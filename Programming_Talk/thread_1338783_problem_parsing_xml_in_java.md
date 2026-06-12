---
title: "problem parsing xml in java"
date: 2009-11-26
forum: Programming Talk
---

### Post by shadylookin on 2009-11-26
I'm trying to parse an xmlString with java, but I'm having some problems

```

import java.io.StringReader;

import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;

import org.w3c.dom.Document;
import org.xml.sax.InputSource;

public class XMLTest {

	public static void main(String args[]) {

		String dummyString = "<?xml version=\"1.0\"?><test><possibleCheating numberOfTimesDeactive=\"3\" numberOfSecondsDeactive=\"15\" /></test>";
		try {
			DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
			DocumentBuilder db = dbf.newDocumentBuilder();

			Document answeredTest = db.parse(new InputSource(new StringReader(
					dummyString)));
			System.out.println(answeredTest.toString());

			String numberOfDeactives = answeredTest.getElementById(
					"possibleCheating").getAttribute("numberOfTimesDeactive");
			String numberOfSecondsDeactive = answeredTest.getElementById(
					"possibleCheating").getAttribute("numberOfSecondsDeactive");
			System.out.println("student left the test " + numberOfDeactives
					+ " times for a total of " + numberOfSecondsDeactive
					+ " seconds");
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

}

```

It outputs 
> 
[#document: null]
java.lang.NullPointerException
	at XMLTest.main(XMLTest.java:23)


It looks like when I try and parse it nothing is happening then I get the null pointer. Anyone know what's wrong or an alternative way to do this?

---

### Post by myrtle1908 on 2009-11-26
Personally I don't care for those parsers.  I prefer dom4j

```
import org.dom4j.DocumentHelper;
import org.dom4j.Document;
import org.dom4j.Element;

public class Test {
	public static void main(String args[]) {
		try {
			String s = "<?xml version=\"1.0\"?><test><possibleCheating numberOfTimesDeactive=\"3\" numberOfSecondsDeactive=\"15\" /></test>";
			Document d = DocumentHelper.parseText(s);
			Element r = d.getRootElement();
			Element pc = (Element)r.selectSingleNode("possibleCheating");
			System.out.println(pc.attributeValue("numberOfTimesDeactive"));
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```

The above loads an XML Document from a string.  You can use a SAXReader to load from a file eg.

```
org.dom4j.io.SAXReader sr = new org.dom4j.io.SAXReader();
org.dom4j.Document d = sr.read(yourFile);
```

dom4j: [http://dom4j.org](http://dom4j.org)

Download here: [http://sourceforge.net/projects/dom4j/files/](http://sourceforge.net/projects/dom4j/files/) (get dom4j-1.6.1.tar.gz)

You will want the following JARs in your build/run path: 'dom4j-1.6.1.jar', 'jaxen-1.1-beta-6.jar' and 'jaxme-api-0.3.jar' ... these are in the ZIP available above.

---

### Post by Axos on 2009-11-27
You need to use getElementsByTagName rather than getElementById...

```

NodeList nl = answeredTest.getElementsByTagName("possibleCheating");
Element possibleCheating = (Element) nl.item(0);

String numberOfDeactives = possibleCheating.getAttribute("numberOfTimesDeactive");
String numberOfSecondsDeactive = possibleCheating.getAttribute("numberOfSecondsDeactive");

```

---

### Post by myrtle1908 on 2009-11-27
> **Axos said:**
> You need to use getElementsByTagName rather than getElementById...

```

NodeList nl = answeredTest.getElementsByTagName("possibleCheating");
Element possibleCheating = (Element) nl.item(0);

String numberOfDeactives = possibleCheating.getAttribute("numberOfTimesDeactive");
String numberOfSecondsDeactive = possibleCheating.getAttribute("numberOfSecondsDeactive");

```

This is why I prefer dom4j's selectSingleNode and general XPath queries.  XML is structured.  You generally know what you want.  No good having to select a list of common elements and assume zeroeth element.  I prefer to "dive right in" and get what I need.  Still, you answered the OPs question better than I did :)

---

### Post by shadylookin on 2009-11-27
> **Axos said:**
> You need to use getElementsByTagName rather than getElementById...

```

NodeList nl = answeredTest.getElementsByTagName("possibleCheating");
Element possibleCheating = (Element) nl.item(0);

String numberOfDeactives = possibleCheating.getAttribute("numberOfTimesDeactive");
String numberOfSecondsDeactive = possibleCheating.getAttribute("numberOfSecondsDeactive");

```

Thanks a bunch.

And while the dom4j looks nicer and can directly parse strings I want to avoid adding adding more third party libraries if possible.

---

### Post by alexlfe on 2011-03-10
I have a problem in Ubuntu...
with special character, because i have developer a program in windows and work fine but in ubuntu no, why? 

In this code...

	DocumentBuilder db;
	db = dbf.newDocumentBuilder();
	Document document;
	document = db.parse(pathFileXML);
        document.getDocumentElement().normalize();
	System.out.println("Result:" + this.getAsString(document));

I have the output with fine special chacter, for example:
èàéò

while the same program in ubuntu don't work...
like ƒÂ¨ÃƒÂ¨ÃƒÂ¨ ÃƒÂ

why...
the code is the same...

---

### Post by s.fox on 2011-03-10
Thread Necromancy.  Please create a new thread.

Thread Closed.

---

