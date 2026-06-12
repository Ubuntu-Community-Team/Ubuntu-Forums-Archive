---
title: "Display RSS as a new XML file using python"
date: 2008-08-14
forum: Programming Talk
---

### Post by sch0009 on 2008-08-14
Hello there

I need to create a python program which reads an RSS feed ([http://rss.news.yahoo.com/rss/topstories](http://rss.news.yahoo.com/rss/topstories)) and extracts the title, link and description of each item in the feed. 

Although the RSS is in fact in XML, the idea is that the program converts the information in the feed into more generic XML format.
The elements in the XML instance must belong to namespace that is created by me. I am unsure on how to do this. I have some code which i have tried but not sure if it is correct as it only extracts the first title, link and description instance. 

Here is the code i have so far:

from lxml import etree
import cgi

tree = etree.parse( 'http://rss.news.yahoo.com/rss/topstories' )
root = tree.getroot()
channel = root[0]

items = list(channel.iterchildren(tag='item'))

new_root = etree.Element('Yahoo') # create the mylist element, the root element
new_item = etree.Element('News') 
new_title = etree.Element('title')
new_link = etree.Element('link')
new_description = etree.Element('description')


new_title.text = items[0].find('title').text
new_link.text = items[0].find('link').text
new_description.text = items[0].find('description').text

new_item.append(new_title) 
new_item.append(new_link)
new_item.append(new_description)

new_root.append(new_item)
f = open( 'yahoo_min.xml', 'w')
f.write( etree.tostring(new_root, pretty_print=True, encoding='utf-8', xml_declaration=True)  )
f.close()

Any help would be much appreciated. 
Thank you

---

### Post by pmasiar on 2008-08-14
1) when posting code use the [ code] [/ code] tags. You would know it if you read sticky FAQ :-)

2) when asking question, do not post your complete program, but the smallest part which still has the error - including error message or how output is different from expected, and (in your case) also input which fails. Read "how to ask questions" in my sig (also in FAQ).

3) What exactly is wrong? ;-)

---

### Post by Reiger on 2008-08-14
If you don't know how to output 'elements belonging to a namespace' created all by yourself... Then I suggest you read about XML-Schema's. The W3C schools would make excellent reading?

---

