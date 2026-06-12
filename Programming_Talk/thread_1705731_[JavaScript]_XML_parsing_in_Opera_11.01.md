---
title: "[JavaScript] XML parsing in Opera 11.01"
date: 2011-03-12
forum: Programming Talk
---

### Post by aytech on 2011-03-12
Hi all, 
I'm having problems making Opera read value from an external xml file. I did the following test xml: 
```
<?xml version="1.0"?>

<collect>

 <node>
 </node>
 
 <node>
 </node>

</collect> 
```

Now, I want to make Opera confirm how many "node" elements it sees, so the html, including javascript code is as follows:
<html>

```
<head>
 <title></title>

 <script type="text/javascript">
[B] function createDoc() 
{
	var xmlDoc = document.implementation.createDocument("","",null);
	return xmlDoc;
}
xmlDoc = createDoc();
xmlDoc.load("test.xml");

function test()
{
	var xmlNodes = xmlDoc.getElementsByTagName("node");
	alert(xmlNodes.length);
}[/B]
 </script>
 </head>
 
 <body>
 <input type="button" value="Check XML" onclick="test()" />
 </body>
 
 </html>
```

Result is 0. Firefox sees it allright, reporting 2 elements. 

Does anyone have any advise on this? 
Thanks

---

