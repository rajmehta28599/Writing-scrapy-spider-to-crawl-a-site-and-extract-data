# Writing-scrapy-spider-to-crawl-a-site-and-extract-data

Software : Anaconda prompt 

1)Creating a new Scrapy project

2)Writing a spider to crawl a site and extract data

3)Exporting the scraped data using the command line

4)store in json file

##lets start

**create scrapy file for our project**

>  scrapy startproject file_name

**in file_name run command**

> scrapy shell url_link

**in that you inspect html tag from website and get the data **

>response.css('title').getall()
>response.css('title::text').getall()

**make spider >quotes_spider file to extract your data**

>import scrapy


>class QuotesSpider(scrapy.Spider):
>    name = "quotes"
>    start_urls = [
>        'http://quotes.toscrape.com/page/1/',
>        'http://quotes.toscrape.com/page/2/',
>    ]

>   def parse(self, response):
>       for quote in response.css('div.quote'):
>            yield {
>                'text': quote.css('span.text::text').get(),
>                'author': quote.css('small.author::text').get(),
>                'tags': quote.css('div.tags a.tag::text').getall(),
>            }

**run your file with your given in name (name="quotes")**

>scrapy crawl quotes -o quotes.json

**or**

>scrapy crawl quotes -o quotes.jl

**or**

>scrapy crawl quotes -o quotes.csv
