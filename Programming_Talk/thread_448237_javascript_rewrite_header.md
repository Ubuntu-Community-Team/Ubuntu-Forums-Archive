---
title: "javascript rewrite header"
date: 2007-05-18
forum: Programming Talk
---

### Post by xolot1 on 2007-05-18
im looking for a method to rewrite the <head> tag of an html document via javascript. is this possible/how would you suggest going about this?


background, ive been working on learning mysql, php, and javascript by building my own blogging application/setup. each page is served via php pulling content from the mysql.  i want to test out a javascript image gallery, and want to insert the source of the .js file into the <head> tag.  i can edit the title and body of the page via mysql, but not the header.  

i was thinking something along the lines of
 function rewriteheader {
original = doucment.html.header.innerHTML;
addedJS = "<script  type='javascirpt' src="xxxxx"></script>";
document.html.header.innerHTML = "original" + "addedJS";
}

but im not yet confident on the feasibility of this...(and i realize im making up JS ^^ but thats the idea).


thanks!

willi

---

### Post by xolot1 on 2007-05-18
my appologies, i think i have figured it out:


<p onClick='original = document.documentElement.firstChild.innerHTML; text =  "<script src=scripts/mootools.js type=text/javascript></script><script src=scripts/jd.gallery.js type=text/javascript></script><link rel=stylesheet href=css/jd.gallery.css type=text/css media=screen />"; document.documentElement.firstChild.innerHTML = original + text;'>CLICK HERE</p>

---

