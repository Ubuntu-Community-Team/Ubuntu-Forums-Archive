---
title: "URGENT::How do I get data into a dojo border container using Ajax?"
date: 2011-05-22
forum: Programming Talk
---

### Post by cutexxbaby on 2011-05-22
I am doing a project and I have a problem. I have retrieved data from a json file using ajax and the xmlhttprequest, but I am not able to put the content I retrieve into the dojo content pane. The content pane is inside a border container. 
 
I have tried the following, but it does not work. The HTMLPage4.html has the json data inside.
 
 
```

function getInfoContent(graphic) 
{
function ajaxRequests() 
{
var activexmodes = ["Msxml2.XMLHTTP", "Microsoft.XMLHTTP"] //activeX versions to check for in IE
if (window.ActiveXObject) { //Test for support for ActiveXObject in IE first (as XMLHttpRequest in IE7 is broken)
for (var i = 0; i < activexmodes.length; i++) {
try {
return new ActiveXObject(activexmodes[i])
}
catch (e) {
//suppress error
}
}
}
else if (window.XMLHttpRequest) // if Mozilla, Safari etc
return new XMLHttpRequest()
else
return false
}
 
var mygetrequests = new ajaxRequests()
mygetrequests.onreadystatechange = function() {
if (mygetrequests.readyState == 4) {
if (mygetrequests.status == 200 || window.location.href.indexOf("http") == -1) {
var bookss = eval("(" + mygetrequests.responseText + ")") //retrieve result as an JavaScript object
var rssent = bookss.infos.info
for (var i = 0; i < rssent.length; i++) {
 
// alert(mygetrequests.responseText);
var placeImg = ""
var txt = ""
// placeImg += rssent[i].descImg
txt += rssent[i].desc
var shorttxt = ""
shorttxt += txt.substring(0, 30);
var bc = new dijit.layout.BorderContainer({ style: "font-size: 11pt; height: 574px; width:739px; border:0px;" });
var c1 = new dijit.layout.ContentPane({
 
region: "top",
style: "height: 11.5%; width: 100%; color: black; background-color: transparent; border:0px;",
content: "<table><div id = \"mydiv\">" + shorttxt + "<font color = '#0000FF' size = '1'><a onclick='showmore();'><u> More...</u></a></div></td></table>"
});
bc.addChild(c1);
}
 
}
else {
alert("An error has occured making the request")
}
}
return bc.domNode;
}
mygetrequests.open("GET", "HTMLPage4.htm", true)
mygetrequests.send(null)
}
 
 
 
 

```

---

### Post by r-senior on 2011-05-22
Could you change the QUOTE tag to a CODE tag so that the indentation appears? It's a bit hard to read as it is.

---

### Post by cutexxbaby on 2011-05-22
> **r-senior said:**
> Could you change the QUOTE tag to a CODE tag so that the indentation appears? It's a bit hard to read as it is.
done...do you know how ?

---

### Post by cutexxbaby on 2011-05-22
> **r-senior said:**
> Could you change the QUOTE tag to a CODE tag so that the indentation appears? It's a bit hard to read as it is.
do you know how should i do to implement the ajax with the dojo border container??

---

