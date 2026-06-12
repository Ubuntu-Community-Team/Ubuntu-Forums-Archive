---
title: "Javascript onclick doesn't work in IE"
date: 2008-01-23
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-01-23
Hi,

I have been searching on google to find the answer for my question, but I have not succeeded to find the answer for my question, that's why I m trying to find my answer in here.

I have a dynamic page with 10 anchors and 10 div element in it. Each anchor is named like anchor_1, anchor_2, ... and each div is called div_1, div_2, ... .

I have created an oclick event handler for each anchor to change the content of the corresponding div element. For example, if you press on a_23, div_23 contents should be changed. 

[PHP]
<a id="anchor_23" onclick="vote_link(this)">
</a>	
[/PHP]

And I have a javascript function called vote_link(this) which grabs this.id and find the corresponding div element and change it. Everything works in FF, but in IE it even doesn't call my function

I have bunch of onclick event handlers and since they worked on FF I thought everything is alright. Fortunately or Unfortunately I don't have IE on my computer to test everything immediately, so almost non of my javascript simple functions work in IE. 

Any idea how to solve this problem?

---

### Post by LaRoza on 2008-01-24
I never use script the way you are, so I don't know what the problem is. You are much better off abstracting this and placing it in an external file. Much easier to handle.

See my home page, the links in the navigation box are altered using ECMAScript in an external file. [http://laroza.freehostia.com/home/script](http://laroza.freehostia.com/home/script) there is the script for it.

---

### Post by mohtasham1983 on 2008-01-24
Basically, I changed my approach. The reason that I'm trying to place them inline is that I'm using YUI and all my elements are inside a tab. If I go to the second tab, the page won't be loaded so I had trouble locating those elements. I found some event handler for changing tabs, but they were kinda complicated and produced other problems. 

YUI has several useful functions to find the element by class name and tag name, so it kinda does what you did on your script. But as I said earlier since I use the tabview, i'm having a lot of problems.

---

### Post by LaRoza on 2008-01-24
> **mohtasham1983 said:**
> Basically, I changed my approach. The reason that I'm trying to place them inline is that I'm using YUI and all my elements are inside a tab. If I go to the second tab, the page won't be loaded so I had trouble locating those elements. I found some event handler for changing tabs, but they were kinda complicated and produced other problems. 

YUI has several useful functions to find the element by class name and tag name, so it kinda does what you did on your script. But as I said earlier since I use the tabview, i'm having a lot of problems.

Try putting a semicolon in: onclick="function(this);"

Might fix it

---

### Post by Wybiral on 2008-01-24
Try: href = "javascript:function();"

---

### Post by LaRoza on 2008-01-24
> **Wybiral said:**
> Try: href = "javascript:function();"

That won't degrade gracefully, ideally, links should have a normal href attribute that is cancelled **if** the script fails. If that doesn't work, browsers, readers, text browsers, and search engines are lost.

---

### Post by mohtasham1983 on 2008-01-24
Thank you all. I tried all suggestions but neither of them worked.

I think I'm going to take YUI approach. In YUI they have a function to find elements in DOM based on element name and class. But, all my contents are inside a tab view and loaded using AJAX, so I practically I cannot use onload or onDOMContent ready events. However, in YUI they have some event handler for tabview. I used oncontentchange one, but I have a small problem. When I load the entire page for the first time, the anchor element reacts normally and the function assigned to handle it says "hi". Then when I move to the second tab and click on the anchor element in it, the function works fine, but when I go back to first tab and click on the anchor element, it calls the function like two times. Here is the code that I m usingL


[PHP]
YAHOO.util.Event.onContentReady("news_tab", init);  

function init(e)
{
	var rate=YAHOO.util.Dom.getElementsByClassName('btn','a');
	YAHOO.util.Event.addListener(rate, "click", hi);
}

function hi(e)
{
	alert("hi");
}
[/PHP]

[PHP]
var tab1 = tabView.getTab(1);
tab1.addListener('contentChange', init);
[/PHP]

I have tried different combinations, but non of them seems to be working.

---

### Post by clasificado on 2008-01-24
it dont seems to be a "combination" problem, but an approach one. 

keep in mind the anchor functionality, it will redirect the browser window if you dont cancel the redirection.

<a id="anchor_23" onclick="vote_link(this);return false;"> 
</a>

OR

<a id="anchor_23" onclick="return vote_link(this);"> 
</a> 

and do a return false in vote_link

---

### Post by mohtasham1983 on 2008-01-26
I think I know what's the problem now.

I just noticed that I had done exact same thing previously and it is working fine with Internet Explorer.I have something like this in my page:

[PHP] onclick='show_comment(id);'  [/PHP]

I believe the only difference between this page and my current page is in their document type. The page that is working fine with onclick event has the following structure:

[PHP]<!DOCTYPE HTML PUBLIC
                    
                 "-//W3C//DTD HTML 4.01 Transitional//EN"
                 "http://www.w3.org/TR/html401/loose.dtd"
                 "-//W3C//DTD XHTML 1.0 Strict//EN"
                 "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">  [/PHP]

The one that I'm using and not working is the following:

[PHP]<xsl:output method="xml" doctype-system="http://www.w3.org/TR/xhtml1/DTD/xhtml1-
transitional.dtd" doctype-public="-//W3C//DTD XHTML 1.0 Transitional//EN" indent="yes"/>  [/PHP]

Unfortunately, I don't know how to use the equivalent document type for xslt.

---

### Post by mohtasham1983 on 2008-01-29
Alright, after playing around with my code I just realized that it has nothing to do with the document type. I just created an anchor element in a new empty xhtml file and called the function and it worked in FF and Opera. I guess it should be working in IE, too. I don't have IE to test with right now. The other day when I checked IE and Opera, I realized that they have the same behavior to this event.

Then I did exact same thing with my site but it didn't work in it. 

After that instead of calling an external function I wrote something like this:

[PHP]<a onclick="alert('hi'); return false;"> button </a>[/PHP]

and in my surprise it worked both in Opera and FF. So I copied the javascript function from the external file and placed it at the end of my page inside script tag and called my function again. But, it didn't work either. 

Anyone had the same problem before?

---

### Post by AlonA on 2010-06-02
I solved it!
OK, I had this problem for about a week now and just few hours ago some HTML expert in my firm told me to try onmousedown instead of onclick and it worked!

So, just change the event name from onclick=.... to onmousedown=
and it should work great in IE and firefox and chrome :D (so probably also on all others too)

Good luck :):popcorn::P

---

