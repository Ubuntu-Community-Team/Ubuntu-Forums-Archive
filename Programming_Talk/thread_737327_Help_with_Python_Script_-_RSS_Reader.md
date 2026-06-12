---
title: "Help with Python Script - RSS Reader"
date: 2008-03-27
forum: Programming Talk
---

### Post by WinterWeaver on 2008-03-27
Hi,

I've been following this tutorial: [http://www.learningpython.com/2006/01/30/rss-reader-part-three-generator-class/](http://www.learningpython.com/2006/01/30/rss-reader-part-three-generator-class/)

The script works, but for some reason it only works on the RSS feed he uses in that example ('http://rss.slashdot.org/Slashdot/slashdot')

I am trying to adapt this script to read from any feed link I choose. When I change the feed to another, like for example, : [http://ubuntuforums.org/external.php?type=RSS2](http://ubuntuforums.org/external.php?type=RSS2), then the script doesn't work. :confused:

Here is the complete script:
```
#! /urs/bin/env python

import urllib2
from xml.dom import minidom, Node

class RSSItem:
    """ this is an RSS item, it contains all the RSS info like Title and Description """
    def __init__(self, title="", description=""):
        self.title = title
        self.description = description

class RSSReader:
    """ This is our RSS Reader """
    def __init__(self, RSSUrl):
        self.RSSUrl = RSSUrl
        self.xmldoc = self.GetXMLDocument(RSSUrl)
        if (not self.xmldoc):
            print "Error Getting XML Document!"

    def GetXMLDocument(self, RSSUrl):
        """ This function reads in a RSS URL and then retruns the XML document on success """
        url_info = urllib2.urlopen(RSSUrl)
        xmldoc = None
        if (url_info):
            xmldoc = minidom.parse(url_info)
        else:
            print "Error Getting URL"
        return xmldoc

    def GetItems(self):
        """ Generator to get items """
        for item_node in self.xmldoc.documentElement.childNodes:
            if (item_node.nodeName == "item"):
                """ Great, we have a item """
                rss_item = self.CreateRSSItem(item_node)
                yield rss_item

    def CreateRSSItem(self, item_node):
        """ Create an RSS Item and return it """
        title = self.GetChildText(item_node, "title")
        description = self.GetChildText(item_node, "description")
        return RSSItem(title, description)

    def GetItemText (self, xml_node):
        """ Get the text from an xml item """
        text = ""
        for text_node in xml_node.childNodes:
            if (text_node.nodeType == Node.TEXT_NODE):
                text += text_node.nodeValue
        return text

    def GetChildText(self, xml_node, child_name):
        """ Get a child node from the xml node """
        if (not xml_node):
            print "Error GetChildNode: No xml_node"
            return ""
        for item_node in xml_node.childNodes:
            if (item_node.nodeName == child_name):
                return self.GetItemText(item_node)
        return ""

if __name__ == "__main__":
    rss_reader = RSSReader('http://ubuntuforums.org/external.php?type=RSS2')
    for rss_item in rss_reader.GetItems():
        if (rss_item):
            print rss_item.title
            print ""
            print rss_item.description
            print ""
```

thanks for any assistance :)

WW

---

### Post by Wybiral on 2008-03-27
You should use the [universal feed parser]("http://www.feedparser.org/") for RSS feeds. It's easier than manually parsing and can tolerate messy XML more.

---

### Post by WinterWeaver on 2008-03-27
wow, thanks for the fast reply :)

Will try using that then ^_^

ta,

WW

---

### Post by WinterWeaver on 2008-03-27
Sooo much easier! Thanks a lot!

Now I just need to find a way that I can use it in my websites, which was the end-goal :)

WW

---

### Post by mssever on 2008-03-27
> **Wybiral said:**
> and can tolerate messy XML more.

Isn't the point of XML that parsers should refuse to deal with an XML file that contains even the smallest syntax error? After all, part of the problem with HTML is how lax the browsers are. It seems to me that if a parser can tolerate messy XML files, then the parser is broken by definition.

---

