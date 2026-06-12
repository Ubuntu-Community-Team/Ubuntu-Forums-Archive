---
title: "Input data into a website and get the output using Selenium in Python"
date: 2014-11-11
forum: Programming Talk
---

### Post by amy8 on 2014-11-11
I'm trying to input some text into Bioportal Annotator [http://bioportal.bioontology.org/annotator](http://bioportal.bioontology.org/annotator) using selenium and extract the resulting table into a csv file. I wrote the code below to do that.


```
from selenium import webdriver
import os
import time
import sys
from selenium.webdriver.common.keys import Keys
from urllib2 import Request
import urllib2


fp = webdriver.FirefoxProfile()
fp.set_preference("browser.download.folderList",2)
fp.set_preference("browser.download.manager.showWhenStarting",False)
fp.set_preference("browser.download.dir", "path")
fp.set_preference("browser.download.manager.closeWhenDone", True)
fp.set_preference("browser.helperApps.neverAsk.saveToDisk", "application/x-gzip gz")
browser = webdriver.Firefox(firefox_profile=fp)
browser.get("http://bioportal.bioontology.org/annotator")
popup= browser.find_element_by_class_name("close").click()
sinput = browser.find_element_by_id("annotation_text")
sinput.send_keys("cancer")
ontology = browser.find_element_by_class_name("default")
ontology.click()
ontology.send_keys("National Cancer Institute Thesaurus")
ontology.send_keys(Keys.RETURN);
submit = browser.find_element_by_id('annotator_button')
submit.click()
time.sleep(30)
```
This gets the annotations I need. Now I'd like to do two things. 1. Download the resulting table to a csv file (not JSON or XML), if possible with a name that I specify. 2. Close the popped up firefox window. It is more than fine if there'd be no popup in the first place. Please suggest me how to proceed.
3. If I have a CSV file that should go as an input into the annotator, column wise and if we should mention different ontologies, like "National Cancer Institute Thesaurus" here, how can I do that?

---

### Post by slickymaster on 2014-11-12
Hi amy8, welcome to the forums.

I've edit your post, adding code tags to it. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

