---
title: "Hmmm, CSS printing help"
date: 2005-06-26
forum: Programming Talk
---

### Post by Jujimufu on 2005-06-26
Yeah, this is more along the lines of web language help - hope it's okay.  :-# 

Anyway, my question is simple.  I've implemented an alternative CSS style sheet for non-screen media (IE - print preview) for a website I'm working on.  I'm wondering if there is javascript or some type of HTML command that I can use as a link in a web page that will display the print preview mode for the browser?

Thanks guys!

---

### Post by fierarul on 2005-06-29
You probably want something like styleSwitch no ?

I do something like this on my site (code from the net):
```

var s=document.cookie.split(":");
var v=s[0],f=(s[1])?s[1]:"style.css";

var em='./.';
em=em+"/"+f;

//alert("Style is"+em);

document.write('<link rel="stylesheet" type="text/css" href="'
	+em+'" />');

if(document.createElement){
	document.getElementsByTagName("link")[0].setAttribute("href",em);
}

function switchStyle(n,s){
	var x=new Date();x.setTime(x.getTime()+(60*60*24*365));
	document.cookie=s+':'+n+':'+';expires='+x.toGMTString()+';path=/';
	location.reload();
}

```

and use ```
a href='#' onclick='switchStyle("style4.css",3
```.

I guess there are other methods but you got the ideea. If you have some server-side things (php?) then I guess some simple parameter &print=1 could make you write some other CSS link.

This ([http://toponcefamily.com/blogs/aaron/archive/2005/04/13/474.aspx](http://toponcefamily.com/blogs/aaron/archive/2005/04/13/474.aspx) ) also looks promising...

---

