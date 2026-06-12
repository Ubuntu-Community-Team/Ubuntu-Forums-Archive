---
title: "Parse HTML with python"
date: 2010-12-09
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-12-09
Any modules I use can sort of like this (meaning really simply ;))
```
import urllib, htmlparser
f = urllib.urlopen("http://url.com/")
html = f.read()
htmldict = htmlparser.parse(html)
print htmldict['title'] # Should output the title of url.com's index
print htmldict['h1'][2] # get the second heading # should output "Url.com! Blah Blah!"
```
Thanks for your time!

---

### Post by Simian Man on 2010-12-09
If you restrict yourself to xhtml, than you can use any XML parser to do just what you want.  Otherwise...it will be more difficult I think.

---

### Post by Crazedpsyc on 2010-12-09
Hmm, I don't use xhtml, and this is for parsing an html file on my modem, so I can't change it.

I have found several html parsers for python, but I just couldn't figure out how to use them!
here's the code for one which I got out of a tutorial at [http://www.boddie.org.uk/python/HTML.html](http://www.boddie.org.uk/python/HTML.html)

```
import sgmllib

class MyParser(sgmllib.SGMLParser):
    "A simple parser class."

    def parse(self, s):
        "Parse the given string 's'."
        self.feed(s)
        self.close()

    def __init__(self, verbose=0):
        "Initialise an object, passing 'verbose' to the superclass."

        sgmllib.SGMLParser.__init__(self, verbose)
        self.hyperlinks = []
        self.descriptions = []
        self.inside_a_element = 0
    def start_a(self, attributes):
        "Process a hyperlink and its 'attributes'."

        for name, value in attributes:
            if name == "href":
                self.hyperlinks.append(value)
                self.inside_a_element = 1

    def end_a(self):
        "Record the end of a hyperlink."

        self.inside_a_element = 0

    def get_hyperlinks(self):
        "Return the list of hyperlinks."

        return self.hyperlinks
    def handle_data(self, data):
        "Handle the textual 'data'."

        if self.inside_a_element:
            self.descriptions.append(data)

    def get_descriptions(self):
        "Return a list of descriptions."

        return self.descriptions
import urllib, sgmllib

# Get something to work with.
f = urllib.urlopen("http://localhost/menu.html") # I am just trying it on my own server for speed
s = f.read()

# Try and process the page.
# The class should have been defined first, remember.
myparser = MyParser()
myparser.parse(s)

# Get the hyperlinks.
print myparser.get_hyperlinks()
print myparser.get_descriptions()
```That returns all the link targets and link values in list form, but when I change
```
            if name == "href":
```to
```
            if name == "style":
```or some similar thing, it just returns [][] (two empty lists)

(I do have lots of things like "<button style="Style">Text</button>", and I though it would return Style and Text, which would be good)


IDEA:: Isn't there a way to use a "for something in html: html.replace(something, :" or "for something in html: dict(something)"  to make it into a dictionary without a module?

---

### Post by Crazedpsyc on 2010-12-09
I did this, but what next?
```
>>> from sgmllib import SGMLParser
>>> parser = SGMLParser()
>>> import urllib
>>> f = urllib.urlopen('http://localhost/menu.html')
>>> parser.feed(f.read())
>>> parser.close()
>>> parser
<sgmllib.SGMLParser instance at 0x7f836084e050>
```

Maybe this will help:
```
>>> dir(parser)
['_SGMLParser__starttag_text', '__doc__', '__init__', '__module__', '_convert_ref', '_decl_otherchars', '_parse_doctype_attlist', '_parse_doctype_element', '_parse_doctype_entity', '_parse_doctype_notation', '_parse_doctype_subset', '_scan_name', 'close', 'convert_charref', 'convert_codepoint', 'convert_entityref', 'entity_or_charref', 'entitydefs', 'error', 'feed', 'finish_endtag', 'finish_shorttag', 'finish_starttag', 'get_starttag_text', 'getpos', 'goahead', 'handle_charref', 'handle_comment', 'handle_data', 'handle_decl', 'handle_endtag', 'handle_entityref', 'handle_pi', 'handle_starttag', 'lasttag', 'lineno', 'literal', 'nomoretags', 'offset', 'parse_comment', 'parse_declaration', 'parse_endtag', 'parse_marked_section', 'parse_pi', 'parse_starttag', 'rawdata', 'report_unbalanced', 'reset', 'setliteral', 'setnomoretags', 'stack', 'unknown_charref', 'unknown_decl', 'unknown_endtag', 'unknown_entityref', 'unknown_starttag', 'updatepos', 'verbose']

```

---

### Post by myrtle1908 on 2010-12-09
"Beautiful Soup is a Python HTML/XML parser designed for quick turnaround projects like screen-scraping. Three features make it powerful:

   1. Beautiful Soup won't choke if you give it bad markup. It yields a parse tree that makes approximately as much sense as your original document. This is usually good enough to collect the data you need and run away.
   2. Beautiful Soup provides a few simple methods and Pythonic idioms for navigating, searching, and modifying a parse tree: a toolkit for dissecting a document and extracting what you need. You don't have to create a custom parser for each application.
   3. Beautiful Soup automatically converts incoming documents to Unicode and outgoing documents to UTF-8. You don't have to think about encodings, unless the document doesn't specify an encoding and Beautiful Soup can't autodetect one. Then you just have to specify the original encoding. 

Beautiful Soup parses anything you give it, and does the tree traversal stuff for you. You can tell it "Find all the links", or "Find all the links of class externalLink", or "Find all the links whose urls match "foo.com", or "Find the table heading that's got bold text, then give me that text." 

[http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)

---

### Post by Crazedpsyc on 2010-12-09
Thanks! I'm downloading it right now!

---

### Post by Cheesehead on 2010-12-09
You don't need to parse the whole page (or build a big dict or import a whole framework) if you just want a couple things. Take a look at the page source, and see if you can identify them using a simple search or regex.

That's how I do it for my router.

Just for fun, I'm also throwing in a method to log in to your router.

For Python 2.7:

```
#!/usr/bin/env python

"""This is a python2.7 script that queries a router and does something with the router information.

Step 1 - Login and query the router, and return the router's HTML reply
Step 2 - Extract the data we want from the reply
Step 3 - Do work with the data

Security issue: Username and password sent to the router are in the clear.
"""

import urllib2
import base64
import string

def read_info_from_router( ):
    """
    Connects to the router and reads the HTML page with the Device List.
    Returns a list of raw strings that needs to be parsed.

    Tutorial on authenticating webpages using Python is at 
    http://www.voidspace.org.uk/python/articles/authentication.shtml
    """

    router_username = "YOUR ROUTER USERNAME"
    router_password = "YOUR ROUTER PASSWORD"
    device_list_url = "http://192.168.1.1/router_page.html"

    base_64_string = base64.encodestring('%s:%s' % 
        (router_username, router_password))[:-1]
    authorization_header = "Basic %s" % base_64_string
    request = urllib2.Request(device_list_url)
    request.add_header("Authorization", authorization_header)
    handle = urllib2.urlopen(request)
    router_web_page = handle.readlines()
    return list_of_html_strings


def get_data_from_html(list_of_html_strings):
    """
    Isolate the data from an HTML string.
    """

    title = ''
    h1 = ''
    for row in list_of_html_strings:
        if row.count("<title>") == 1:
            title = string.lstrip(row, " <title>")   # Strip junk off the string
            title = string.rstrip(title, "</title>;\r\n")  # Strip junk off the string
        elif row.count("<h1>") == 1:
            h1 = string.lstrip(row, " <h1>")   # Strip junk off the string
            h1 = string.rstrip(h1, "</h1>;\r\n")  # Strip junk off the string
    return (title, h1)

list_of_html_strings = read_info_from_router( )
(title, h1) = reformat_html(list_of_html_strings)
do_work(title, h1)


```

---

### Post by Crazedpsyc on 2010-12-09
Thanks Cheesehead! That looks great and I will use it for a few other things because of it's speed, but it unfortunately does not work for my modem's download allowance page :(...
Thank you to [myrtle1908]("http://ubuntuforums.org/member.php?u=544720")! That worked perfectly! It is a little slow, and it took a while going through all the levels of .contents (I ended up with "soup.contents[2].contents[1].contents[1].contents[1].contents[1].contents[0].contents[3].contents[2].text")
But at least it gets the numbers to the screen!

---

