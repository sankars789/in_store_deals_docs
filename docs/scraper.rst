============
Scraper
============

`The Scraper is the heart of our app. It fetches the data and pumps to the app. So the scraper design is very critical. I have considered several tools and technologies for scraping.`

I have done scraping in node.js and python. **Python** is my choice as it is very simple and follows **sequential programming** approach.

The following explains the scraping browsers and frameworks

1. Scrapy-Python
-----------------
 `Scrapy <http://scrapy.org>`_
 is one of the best framework for scraping. But it can't scrape dynanmic sites where the content is generated on the fly by java script. because it uses headless browser.

2. Selenium-xvfb
------------------
 Selenium uses real browser so it can scrape dynamic sites. But is bit slow. It doesnt matter. it does the job pretty good. XVFB is emulator to run browser in hidden mode.

============================================
`Puma India <http://in.puma.com/>`_ scraping
============================================
It is a dynamic site. But the initial page is static. so for the first page, we used **scrapy**. for products page used **selenium**.



Puma-lev1
---------
its job is to fetch all the unique product pages along with the following fields.
    1. id  
    2. process_lev1  
    3. process_lev2  
    4. sale  
    5. name  
    6. **url**  
    7. image_small  
    8. regular_price  
    9. discounted_price  


command to run ::
  **cd puma-spider/stack/stack/**
   **scrapy crawl puma-lev1**



Program Logic
^^^^^^^^^^^^^
 Fetch the data from the site and while saving it, do the following.
  1. If the item is not present (check using **URL** as key), Then **Insert** it.
  2. If item exists in the DB, then update the following fields.
      - sale
      - regular_price  
      - discounted_price  
      

Puma-lev2
---------
`lev2-sample-link <http://in.puma.com/ferrari-motorsport-men-s-track-jacket-11404.html>`_

command to run ::
  **python puma-lev2.py refresh=N**
  
  **python puma-lev2.py refresh=Y**


The level2 spider reads yields the following fields.
  1. images - original, big, small
  2. style number
  3. availability
  4. size

Keep a refresh flag for this program. if refresh flag is Y, then **process all** else process only those with **process_lev2** flag **N**
  





