---
title: "Submitting an XML form?"
date: 2006-07-19
forum: Programming Talk
---

### Post by hagen00 on 2006-07-19
Hi there

I need to send some XML data to a server and I've been given the following specifications. 

Server: [http://myserver.com/parseXML.jsp](http://myserver.com/parseXML.jsp)
Request method: POST
Form request data name: xmldata

```
<XML>
<RECEIVE_RESPONSE user=12345678>
<SMS_RECEIVE uid=”1” to=”+275550000001” type=”6”/>
<SMS_RECEIVE uid=”2” to=”+275550000002” type=”1”>thanks for the
message</SMS_RECEIVE>
</RECEIVE_RESPONSE>
</XML>
```

I'm assuming that *xmldata *is just the name of the form, but my question is, how do I include XML into a normal HTML form? Or do I submit an XML form? How would I do that?

Help much appreciated

H

---

### Post by yaaarrrgg on 2006-07-19
What they are saying, I think, is that 'xmldata' is the name of the form variable.  As a quick test, you can make an html page with a textarea named this, and paste the XML in it, like (replace myserver):

```

<form action="http://myserver.com/parseXML.jsp" method="post">
<textarea name="xmldata">
<XML>
<RECEIVE_RESPONSE user=12345678>
<SMS_RECEIVE uid="1" to="+275550000001" type="6"/>
<SMS_RECEIVE uid="2" to="+275550000002" type="1">thanks for the
message</SMS_RECEIVE>
</RECEIVE_RESPONSE>
</XML>
</textarea>
<input type="submit">
</form>

```

Posting to a webpage varies from language to language though.... depending on your problem, you may have to: 

1. collect your data from a regular html form 
2. then compile it to xml format
3. programatically post that the data (as the variable 'xmldata') to the the page [http://myserver.com/parseXML.jsp](http://myserver.com/parseXML.jsp)  
4. read and parse the response...

---

### Post by hagen00 on 2006-07-20
Thanks a lot yaaarrrgg, that's exactly what I had to do!

Cheers

---

