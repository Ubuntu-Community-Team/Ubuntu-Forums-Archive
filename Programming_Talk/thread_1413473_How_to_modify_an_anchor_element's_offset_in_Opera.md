---
title: "How to modify an anchor element's offset in Opera?"
date: 2010-02-22
forum: Programming Talk
---

### Post by meastwood on 2010-02-22
I have a javascript function (using jquery) that modifies the offset of anchor elements that are 'ajaxed' into a div on the main page.

As always with web development this works first time for Firefox, then after some changes for IE6,7 and 8.  Now it's Opera's turn.  Am using version 10.10.

In the DOM on Opera 'offsetLeft' and 'offsetTop' for **ALL** anchors on the page is reported as 0.  Clearly Opera must be using some other object's attribute when it follows a link to an anchor on the same page.  It must know the 'position' of the target element and they all cannot be (0,0)???  

I have no idea how to get round this one!

###
Well I have got round it - not fixed it.

Opera seems to be very flakey on ubuntu/linux64. It runs browser.js and user js stuff that seems to play havoc with any javascript I've written.  Functions in these files even have problems parsing a script file.  The browser's dom inspector does'nt inspect if javascript is disabled, can't handle ajax, it does'nt seem to clear it's cache ... have had a lot of problems with it - not just html rendering. All in all thank god for FireFox.  I thought I'ld never say this but ... I've had less problems with IE6 ... there I've said it.  What's more I could get things to work in IE6 - not Opera.


My workaround - not such an issue as am implementing unobtrusive javascript - default behaviour for Opera and untested browsers is no javascript even if the client has javascript enabled.  Tested browsers with javascript enabled get Ajax, animation and a couple of other goodies.

---

