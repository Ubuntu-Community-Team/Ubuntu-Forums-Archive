---
title: "Downloading website using regex in java?"
date: 2008-10-08
forum: Programming Talk
---

### Post by jinxen on 2008-10-08
Hi!

I have a website that i want to get information from (containing information on network usage). I would like to get that information into my java application. I already have the written regex (frined wrote a c# app with the same functionality) but now i wonder how too get this site info into my java app?

I have tried to google, and search the forums without luck. Any site och tip would be helpful!

Cheers!

---

### Post by reality1011 on 2008-10-08
You should look into screen scraping... also

post the link to the website and / or a snip of the informaiton that you want.... we might be able to tell you how to "extract" that information.

---

### Post by tinny on 2008-10-08
What you are trying to do is called screen scraping.

Here are some Java tools that may help...
[http://www.manageability.org/blog/stuff/screen-scraping-tools-written-in-java](http://www.manageability.org/blog/stuff/screen-scraping-tools-written-in-java)

---

### Post by jinxen on 2008-10-08
Thanks for the quick answers and sorry for not posting some more information about the actual info i am trying to extract! :)

The page it self looks like this:

[IMG]http://noshitsherlock.se/sgs.png[/IMG]

Source code is like this:'

[HTML]
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
  <head><title>Personlig statistik</title>
      <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
      <link rel="stylesheet" href="CSS/styles.css" type="text/css"/>
  </head>
  <body bgcolor="#ffffff" text="#003366">
         <table width="560" border="0" cellpadding="0" cellspacing="0">
             <tr>

                <td colspan="3" width="560" valign="top" class="bigHeader"><img src="images/trans.png" width="560" height="30" alt="background"/></td>
             </tr>
             <tr>                      
                <td width="20" valign="top" class="bigHeader"><img src="images/trans.png" width="18" height="66" alt="background" /></td>
                <td width="520" valign="top" class="bigHeader"><img src="images/statistik.png" alt="Statistik"/></td>
                <td width="20" valign="top" class="bigHeader"><img src="images/trans.png" width="18" height="1" alt="background"/></td>
             </tr>
          </table>
         <table width="560" border="0" cellpadding="0" cellspacing="0">


          <table width="560" border=0>
             <tr>
                <td>
                   Var v&auml;nlig v&auml;nta medan statistiken laddas, det tar en stund. <br />
                   Please hold while the statistics is loading, it takes a few moments. <br/>
                   <br />

                </td>
             </tr>
          </table>
<table width="560" border=0><th>Datum</th><th>Trafik in</th><th>Trafik ut</th><th>Total trafik</th><tr><td>2008-10-08</td><td>2.33 GB</td><td>3.05 GB</td><td>5.38 GB</td></tr><tr><td>2008-10-07</td><td>7.11 GB</td><td>3.96 GB</td><td>11.06 GB</td></tr><tr><td>2008-10-06</td><td>2.96 GB</td><td>2.29 GB</td><td>5.25 GB</td></tr><tr><td>2008-10-05</td><td>40.20 MB</td><td>4.04 MB</td><td>44.24 MB</td></tr><tr><td>2008-10-04</td><td>SAKNAS</td><td>SAKNAS</td><td>SAKNAS</td></tr><tr><td>2008-10-03</td><td>SAKNAS</td><td>SAKNAS</td><td>SAKNAS</td></tr></pre></table><table width="560" border=0>

                   <tr>
                    <td>
                       <br/>
                       Kommentar: Ovanst&aring;ende tabell visar din trafik de senaste sju dagarna.
                       Dagens siffra &auml;r det du genererat hittills idag. Statistiken uppdateras 
                       var 8:e minut.
                    </td>
                   </tr></table>         </table>
         <table cellpadding="0" cellspacing="0" border="0" width="560">
         </table>

        </table>
  </body>
</html>
[/HTML]

I can't post the link to the site because i am on a university network, and only ip addresses within that range is allowed to check the site!

It is a very simple page, the thing i would like to do is:

1: The headline that says "Total trafik" is the amount of traffic for me today. I would like to get that nr under the headline and warn me if it gets to close to 15 GB, since that is my limit.

2: Everything in the table should display in a list since that would also be nice to see.

The app will later on be graphical of course and show these in som nifty way, but my problem is how do download the information from the site. Can't figure out how :)

I have almost all of the regexp already done from a friends project that he has written in c#, the same program but i wan't to write it in java.

example:

```

MatchCollection matchs = Regex.Matches(match.Value.Substring("<table width=\"560\" border=0><th>Datum</th><th>Trafik in</th><th>Trafik ut</th><th>Total trafik</th>".Length, (match.Value.Length - "<table width=\"560\" border=0><th>Datum</th><th>Trafik in</th><th>Trafik ut</th><th>Total trafik</th>".Length) - "</pre></table>".Length), @"<tr>(<td>([\.0-9A-Za-z\-\s]*)</td>)+</tr>");

```

I found something on the site poste earlier. A parse that is called Jericho HTML parser. Don't know if that will do my trick, but it seems kind of right if i look at the example bellow?

[http://jerichohtml.sourceforge.net/samples/console/src/FindSpecificTags.java]("http://jerichohtml.sourceforge.net/samples/console/src/FindSpecificTags.java")

I hope this clears some :)

Cheers

---

### Post by Reiger on 2008-10-08
Since it's XHTML, you can dump it to an XML object -- right? Then, all you have to do is run an XPATH query on it.

The XPATH query is really very simple in your case:
```

html/body/table[position() = 2]/table[position() = 2]/tr/td[position() = 4]

```

Or in English: on the html level, selec the body from there select the second table; from that element select the second table (the stats); from there select all tr elements; from those select all cells in the 4th columns. So all you have to do is find a DOM library (JDOM is said to be good), let it parse the XML and run your XPATH search. Of course if you are really concerned about performance, it's perhaps not such a good idea; alternatively you could do multiple filters on top of each other:
Each Matcher.group(1) from:
```

/<td>([\d.-]+(\w+)?)<\/td>/

```
could be stored in an ArrayList, and a simple algorithm would only pick the elements you know you want (1st and 4th elements).
```

int i;
for(i=0;i<the_list.length;i+=4)
    the_result_list.add("Total traffic at: "+the_list.get(i)+" was: "+the_list.get(i+3));

```

---

### Post by CptPicard on 2008-10-08
I do a lot of screen scraping, and the http client component I use is [Jakarta HttpClient]("http://hc.apache.org/httpclient-3.x/").

Essentially, I just extend this as needed at getURL and handleResponse -- the Scanner can be used to parse the response stream, for example by using regular expressions.

```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package vptools.html.pages;

import java.io.IOException;
import java.io.InputStream;
import java.util.Scanner;
import org.apache.commons.httpclient.HostConfiguration;
import org.apache.commons.httpclient.HttpException;
import org.apache.commons.httpclient.HttpState;
import org.apache.commons.httpclient.methods.GetMethod;
import vptools.Engine;

/**
 *
 * @author eneva
 */
public abstract class HTMLBasePage {
    
    public abstract String getURL();
    
    public void fetch() throws IOException {
        fetch(null, null);
    }
    
    
    public void fetch(HttpState state) throws IOException {
        fetch(null, state);
    }
    
    public void fetch(HostConfiguration conf, HttpState state) throws IOException {
        
        GetMethod method = new GetMethod(getURL());
        InputStream stream = null;
        Scanner scan = null;
        
        try {
            if (state != null && conf != null)
                Engine.getInstance().getHTTPClient().executeMethod(conf, method, state);
            else if (state != null && conf == null)
                Engine.getInstance().getHTTPClient().executeMethod(null, method, state);                
            else
                Engine.getInstance().getHTTPClient().executeMethod(method);

            stream = method.getResponseBodyAsStream();
            scan = new Scanner(stream, method.getResponseCharSet());
            
            handleResponse(scan);
            consumeRest(stream);
            
        }
        catch (HttpException ex) {
            
            try {
                
                if (stream != null)
                    consumeRest(stream);
                
            }
            catch (IOException ioe) {
                throw ioe;
            }
            
            throw ex;
        }
        finally {
            
            if (stream != null) {
                    try {
                        stream.close();
                    }
                    catch (IOException ex) {
                        // NOP
                    }
            }
            
            if (scan != null)
                scan.close();
            
            method.releaseConnection();
        }
    }
    
    
    @SuppressWarnings("empty-statement")
    private void consumeRest(InputStream stream) throws IOException {
        byte[] arr = new byte[1024];
        while (stream.read(arr) != -1);
    }
    
    
    public abstract void handleResponse(Scanner scan);
    
}

```

The Engine singleton contains the initialization for the httpclient and allows me to get an instance to use.

---

### Post by Shin_Gouki2501 on 2008-10-08
if you know what you're looking for its very easy to use the XHTML file as Inputstream for XML processing. It's quite simple to navigate then.

---

### Post by jinxen on 2008-10-09
Thank you all for the answers! I have a little to process now then :) I have no xml knowledge at all, but maybe now is the time to get it then! :)

---

### Post by jinxen on 2008-10-13
Hi!

I have choosen to go with dom4j. I have managed to get a application almost right i think. But when i try to parse the site i get the following error.

```

Exception in thread "main" org.dom4j.DocumentException: Error on line 21 of document http://web.sgsnet.se/tvbstats/ip.php : Open quote is expected for attribute "border" associated with an  element type  "table". Nested exception: Open quote is expected for attribute "border" associated with an  element type  "table".
        at org.dom4j.io.SAXReader.read(SAXReader.java:482)
        at org.dom4j.io.SAXReader.read(SAXReader.java:321)
        at sgsmem.Main.parse(Main.java:25)
        at sgsmem.Main.main(Main.java:33)
Nested exception: 
org.xml.sax.SAXParseException: Open quote is expected for attribute "border" associated with an  element type  "table".
        at com.sun.org.apache.xerces.internal.util.ErrorHandlerWrapper.createSAXParseException(ErrorHandlerWrapper.java:236)
        at com.sun.org.apache.xerces.internal.util.ErrorHandlerWrapper.fatalError(ErrorHandlerWrapper.java:215)
        at com.sun.org.apache.xerces.internal.impl.XMLErrorReporter.reportError(XMLErrorReporter.java:386)
        at com.sun.org.apache.xerces.internal.impl.XMLErrorReporter.reportError(XMLErrorReporter.java:316)
        at com.sun.org.apache.xerces.internal.impl.XMLScanner.reportFatalError(XMLScanner.java:1438)
        at com.sun.org.apache.xerces.internal.impl.XMLScanner.scanAttributeValue(XMLScanner.java:802)
        at com.sun.org.apache.xerces.internal.impl.XMLNSDocumentScannerImpl.scanAttribute(XMLNSDocumentScannerImpl.java:578)
        at com.sun.org.apache.xerces.internal.impl.XMLNSDocumentScannerImpl.scanStartElement(XMLNSDocumentScannerImpl.java:222)
        at com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl$FragmentContentDispatcher.dispatch(XMLDocumentFragmentScannerImpl.java:1693)
        at com.sun.org.apache.xerces.internal.impl.XMLDocumentFragmentScannerImpl.scanDocument(XMLDocumentFragmentScannerImpl.java:368)
        at com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:834)
        at com.sun.org.apache.xerces.internal.parsers.XML11Configuration.parse(XML11Configuration.java:764)
        at com.sun.org.apache.xerces.internal.parsers.XMLParser.parse(XMLParser.java:148)
        at com.sun.org.apache.xerces.internal.parsers.AbstractSAXParser.parse(AbstractSAXParser.java:1242)
        at org.dom4j.io.SAXReader.read(SAXReader.java:465)
        at org.dom4j.io.SAXReader.read(SAXReader.java:321)
        at sgsmem.Main.parse(Main.java:25)
        at sgsmem.Main.main(Main.java:33)

```

And i see in the source code i posted above on line 21 the don't close the second argument <table width="560" border=0>. Is there somehow i can skip this or to fix it since i don't host the site?

Cheers


Application looks like this.

```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package sgsmem;


import org.dom4j.*;
import org.dom4j.io.SAXReader;


/**
 *
 * @author skynet
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    
    public static Document parse(String file) throws DocumentException {
        SAXReader reader = new SAXReader();
        Document document = reader.read(file);
        return document;
    }
    
    
    
    public static void main(String[] args) throws DocumentException {        
        
        Document doc = parse("http://web.sgsnet.se/tvbstats/ip.php");
        
        String test = doc.valueOf("//html/body/table[position() = 2]/table[position() = 2]/tr/td[position() = 4]");
        
        System.out.println(test);
        
        // TODO code application logic here
    }

}


```

---

### Post by myrtle1908 on 2008-10-13
Have a look at the org.w3c.tidy package ... this should cleanup the HTML.  You can then parse into a DOM object.

For example:-

```

public static org.w3c.dom.Document getResourceHTML(java.net.URL url) throws Exception {
	java.io.InputStream urlStream = url.openStream();
	org.w3c.tidy.Tidy tidy = new org.w3c.tidy.Tidy();
	tidy.setQuiet(true);
	tidy.setShowWarnings(false);
	return tidy.parseDOM(urlStream, null);
}

```

---

