---
title: "HTML DOM Java"
date: 2011-07-04
forum: Programming Talk
---

### Post by RobikShrestha on 2011-07-04
Can anyone suggest me with some tutorial on how to parse an html file using java? I googled a lot but the examples were very complex. I need something to start from the basics of DOM.

---

### Post by W3N4 on 2011-07-04
Have a look at these websites:
[http://tutorials.jenkov.com/java-xml/dom.html](http://tutorials.jenkov.com/java-xml/dom.html)
[http://www.genedavis.com/library/xml/java_dom_xml_creation.jsp](http://www.genedavis.com/library/xml/java_dom_xml_creation.jsp)
It's very easy, read java api for more information, this is just a start.

---

### Post by myrtle1908 on 2011-07-04
I use HTMLTidy + a parser when I need to do this.  Observe the following fragment ...

```
public static org.w3c.dom.Document getResourceHTML(java.net.URL url) throws Exception {
	java.io.InputStream urlStream = url.openStream();
	org.w3c.tidy.Tidy tidy = new org.w3c.tidy.Tidy();
	tidy.setQuiet(true);
	tidy.setShowWarnings(false);
	return tidy.parseDOM(urlStream, null);
}
```

Basically it takes a URL and grabs the page.  Runs it through Tidy and returns a W3C DOM Document.

---

### Post by RobikShrestha on 2011-07-06
Thanks for the reply. I used the HTMLEditor of java.

---

