---
title: "xml feed in C++"
date: 2008-07-16
forum: Programming Talk
---

### Post by Elisei on 2008-07-16
Hi there!

Can anyone suggest a way to open a connection to an XML using c++ where the address of the feed is [http://....?offset=1000](http://....?offset=1000).

Would i need to use sockets to establish the connection or is there another way of doing it?

thanks!

---

### Post by ceclauson on 2008-07-16
I'm not sure what you mean by opening a connection and "feed". I'm guessing you're just talking about http'ing an XML document from the site.  When you do this, you send a request to the server for a resource, and the server sends the resource back.  Once you have it, then you manipulate/do whatever with it programmatically.

If you just want to fetch a resource from a server using http, you can use libCURL.  The site is here:
[http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/)
There are some tutorials on the internet on how to use it.

If the resource is XML, you'll probably need to parse it once it comes back.  There are a few libraries to help you do this.  One is Apache Xerces:
[http://xerces.apache.org/xerces-c/](http://xerces.apache.org/xerces-c/)
and another is libxml++:
[http://libxmlplusplus.sourceforge.net/](http://libxmlplusplus.sourceforge.net/)
XML parsing libraries can use a few different standard methods to parse XML.  In my opinion, DOM is the easiest to work with, but depending on the XML document, you may have to write recursive algorithms.

All of these libraries can be downloaded and installed on Ubuntu with the package manager.

---

