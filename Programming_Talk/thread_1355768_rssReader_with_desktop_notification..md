---
title: "rssReader with desktop notification."
date: 2009-12-15
forum: Programming Talk
---

### Post by espen77 on 2009-12-15
Hi all. I am new to python, just passed the hello world stage. I have written a couple of bash scripts earlyer but that is about it, so I got my self my very first e-book and started reading (Hello World! Conputer programming for kids).

So I wanted to make something that showed OSD notification when there was something new at slashdot, but i tried to make it so it can work with other feeds to. There are probably many programs like this out there, but i am still proud i got this to work.
 
```
#! /usr/bin/env python
# My first program beyond the hello world's. It reads RSS feeds and display them
# as desktop notification in ubuntu. I got the inspiration and some code from:
# http://www.learningpython.com/2006/01/14/rss-reader-part-one/
# and pynotify doc's.
try:
 import urllib2, gtk, pygtk, os, os.path, pynotify, time
 from xml.dom import minidom, Node
 pygtk.require('2.0')
except:
 print "Error: need python-notify, python-gtk2 and gtk"

rssLists = {}
rssTimer = 0

def osdNotify(osdTitle,osdString):
 if not pynotify.init("Timekpr notification"):
  sys.exit(1)
 n = pynotify.Notification(osdTitle, osdString)
 n.set_urgency(pynotify.URGENCY_LOW)
 n.set_timeout(10000)
 if not n.show():
  print "Error: Failed to send notification"
  sys.exit(1)

def grabRSS(rssTitle, rssAddress):
 global rssLists, rssTimer
 if not rssLists.has_key(rssTitle):
  rssLists[rssTitle] = []
 url_info = urllib2.urlopen(rssAddress)
 if (url_info):
  rssTimer = 60 # set shorter refresh if RSS is reachable
  xmldoc = minidom.parse(url_info)
  if (xmldoc):
   rootNode = xmldoc.documentElement
   for node in rootNode.childNodes:
    if (node.nodeName == "item"):
     for item_node in node.childNodes:
      if (item_node.nodeName == "title"):
       title = ""
       for text_node in item_node.childNodes:
        if (text_node.nodeType == node.TEXT_NODE):
         title += text_node.nodeValue
       if (len(title)>0):
        if title not in rssLists[rssTitle]:
         if len(rssLists[rssTitle]) < 15:
          rssLists[rssTitle].append(title)
         else:
          rssLists[rssTitle].insert(0, title)
         rssLists[rssTitle] = rssLists[rssTitle][:15]
         osdNotify(rssTitle, title)
         print rssTitle + ": " + title # prints feed to terminal
  else:
   osdNotify("Script Error!", "Error getting XML document!")
 else:
  rssTimer = 600 # set longer refreshtime if RSS not reachable
  osdNotify("Script Error!", "Error! Getting URL")

while True:
 grabRSS("slashdot.org", "http://rss.slashdot.org/Slashdot/slashdot")
 time.sleep(rssTimer)
```

---

### Post by car1 on 2009-12-15
The indentation hurts the brain.

[http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)

---

