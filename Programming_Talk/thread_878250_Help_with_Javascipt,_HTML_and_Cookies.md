---
title: "Help with Javascipt, HTML and Cookies"
date: 2008-08-02
forum: Programming Talk
---

### Post by painejake on 2008-08-02
Not sure if this is the correct forum, but here goes..

Ok i run a gaming server/website and we have a voting box where members of the website can vote to try and get the website a bit more "out there" on a kind of ranking website.

I have made a javascript popup box and i want it to only show if they dont have a cookie in there browser and after the cookie deletes itself the box shows again. This is my script so far:

```
<script>document.title="WoWfate";</script><SCRIPT language=JavaScript1.2>
var ns4=document.layers
var ie4=document.all
var ns6=document.getElementById&&!document.all

//drag drop function for NS 4////
/////////////////////////////////



var dragswitch=0
var nsx
var nsy
var nstemp

function drag_dropns(name){
if (!ns4)
return
temp=eval(name)
temp.captureEvents(Event.MOUSEDOWN | Event.MOUSEUP)
temp.onmousedown=gons
temp.onmousemove=dragns
temp.onmouseup=stopns
}

function gons(e){
temp.captureEvents(Event.MOUSEMOVE)
nsx=e.x
nsy=e.y
}
function dragns(e){
if (dragswitch==1){
temp.moveBy(e.x-nsx,e.y-nsy)
return false
}
}

function stopns(){
temp.releaseEvents(Event.MOUSEMOVE)
}

//drag drop function for ie4+ and NS6////
/////////////////////////////////


function drag_drop(e){
if (ie4&&dragapproved){
crossobj.style.left=tempx+event.clientX-offsetx
crossobj.style.top=tempy+event.clientY-offsety
return false
}
else if (ns6&&dragapproved){
crossobj.style.left=tempx+e.clientX-offsetx
crossobj.style.top=tempy+e.clientY-offsety
return false
}
}

function initializedrag(e){
crossobj=ns6? document.getElementById("dnwtop_100_showimage") : document.all.dnwtop_100_showimage

var firedobj=ns6? e.target : event.srcElement
var topelement=ns6? "HTML" : "BODY"

while (firedobj.tagName!=topelement&&firedobj.id!="dragbar"){
firedobj=ns6? firedobj.parentNode : firedobj.parentElement
}

if (firedobj.id=="dragbar"){
offsetx=ie4? event.clientX : e.clientX
offsety=ie4? event.clientY : e.clientY

tempx=parseInt(crossobj.style.left)
tempy=parseInt(crossobj.style.top)

dragapproved=true
document.onmousemove=drag_drop
}
}
document.onmousedown=initializedrag
document.onmouseup=new Function("dragapproved=false")

////drag drop functions end here//////

function hidebox(){
if (ie4||ns6)
    crossobj.style.visibility="hidden"
else if (ns4)
    document.dnwtop_100_showimage.visibility="hide"
}

document.write('');

document.write('<div id="dnwtop_100_showimage" style="z-index: 300; position:absolute;width:380px;left:1;top:1"><table border="1" bordercolor="659044" width="380" bgcolor="000000" cellspacing="0" cellpadding="0"><tr><td width="100%"><table border="0" width="100%" cellspacing="0" cellpadding="0" height="36"><tr><td width="100%" id="dragbar" title="Vote For WoWfate" height="25"><ilayer width="100%" onSelectStart="return false"><layer width="100%" onMouseover="dragswitch=1;if (ns4) drag_dropns(dnwtop_100_showimage)" onMouseout="dragswitch=0"><span style="font-weight: bold; font-family: Verdana; font-size: 12px; color: F8F8F8;  padding: 6px; padding-bottom: 4px;"><center>Vote For WoWfate</center></span></layer></ilayer></td></tr><tr><td width="100%" bgcolor="122031" style="padding:10px; border: solid D7DCE9 2px; border-top:0px; font-family:Verdana; font-size:12px; color:D7DCE9;"><IGNORE!><i><BR><center><b><img src="http://wowfate.gotdns.org/images/vote_popup/vote-ani.gif"><br><br><font color="white">Vote For WoWfate So That We Can Grow In Population And Size<br>Only You Can Get Us To #1..</font> <font color="white"></font><font color="white"></b></i><br><br><div align="center"><a href="http://localhost/vote.html" target="_blank" onClick="hidebox()"><img src="http://wowfate.gotdns.org/images/vote_popup/vote.gif" border="0"></a>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#" onClick="hidebox();return false"><img src="http://wowfate.gotdns.org/images/vote_popup/no_thanks.gif" border="0"></a>&nbsp;&nbsp;&nbsp;</div></td></tr></table></td></tr></table></div></center>');

</SCRIPT>
```

and that will forward them to this page

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Re-directing</title>
</head>
<?php
setcookie('wowfate_vote', '1', time() + 43200);
?>
<script language='javascript'>
setTimeout("location.href='http://www.xtremetop100.com/in.php?site=1132238889'",1);
</script>
<body>
<p>Re-directing you to 
<a href="http://www.xtremetop100.com/in.php?site=1132238889">http://www.xtremetop100.com/in.php?site=1132238889</a> in 3 seconds..</p>
<p>Thanks for Voting... </p>

```

The bit im really stuck on is i think this will plant a cookie for a set time

```
setcookie('wowfate_vote', '1', time() + 43200);
```

but how do i make the box only show if that cookie isn't there?

Many Thanks for future replys

Jay :)

---

### Post by drubin on 2008-08-02
GOOGLE.

[http://www.javascripter.net/faq/readinga.htm](http://www.javascripter.net/faq/readinga.htm)
[http://www.w3schools.com/JS/js_cookies.asp](http://www.w3schools.com/JS/js_cookies.asp)

Take a look at 

[www.w3schools.com](www.w3schools.com)

---

