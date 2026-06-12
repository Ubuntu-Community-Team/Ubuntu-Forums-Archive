---
title: "Python question"
date: 2015-06-27
forum: Programming Talk
---

### Post by Herbon on 2015-06-27
I'm getting the follow error

```

tep@two:~/tutorial/$ scrapy crawl dmoz
Traceback (most recent call last):
  File "/usr/bin/scrapy", line 9, in <module>
    load_entry_point('Scrapy==1.0.0rc3.post2-g2ff9888', 'console_scripts', 'scrapy')()
  File "/usr/lib/pymodules/python2.7/scrapy/cmdline.py", line 142, in execute
    cmd.crawler_process = CrawlerProcess(settings)
  File "/usr/lib/pymodules/python2.7/scrapy/crawler.py", line 209, in __init__
    super(CrawlerProcess, self).__init__(settings)
  File "/usr/lib/pymodules/python2.7/scrapy/crawler.py", line 115, in __init__
    self.spider_loader = _get_spider_loader(settings)
  File "/usr/lib/pymodules/python2.7/scrapy/crawler.py", line 296, in _get_spider_loader
    return loader_cls.from_settings(settings.frozencopy())
  File "/usr/lib/pymodules/python2.7/scrapy/spiderloader.py", line 30, in from_settings
    return cls(settings)
  File "/usr/lib/pymodules/python2.7/scrapy/spiderloader.py", line 21, in __init__
    for module in walk_modules(name):
  File "/usr/lib/pymodules/python2.7/scrapy/utils/misc.py", line 71, in walk_modules
    submod = import_module(fullpath)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/home/imhotep/tutorial/tutorial/spiders/scrapy.py", line 5, in <module>
    class DmozSpider(scrapy.Spider):
AttributeError: 'module' object has no attribute 'Spider'


```

Backstory, Im trying to use "Scrapy" a python base program. The setting up states....

> go to the project’s top level directory and run: **scrapy crawl dmoz**

[http://doc.scrapy.org/en/latest/intro/tutorial.html](http://doc.scrapy.org/en/latest/intro/tutorial.html)

Which Im assuming is the following directory since this is where the file lives.

```

/home/tep/tutorial

```

Any ideas??

---

### Post by steeldriver on 2015-06-28
You appear to have named your file 'scrapy.py', which causes it to conflict with the name of the module 'scrapy'

Try renaming it to something unique (the tutorial you linked seems to use 'dmoz_spider.py')

---

