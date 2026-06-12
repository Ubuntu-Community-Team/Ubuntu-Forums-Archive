---
title: "html/css - unwanted background appears (sometimes)"
date: 2009-12-12
forum: Programming Talk
---

### Post by mpgarate on 2009-12-12
I have a website that uses html and css, and I my knowledge of web coding and design is intermediate at best. I have this website together, which I am fairly happy with, but I have been having a problem.

Sometimes, when you access the page, there appears on the bottom an unwanted white box, beginning exactly at the bottom of the sidebar images. Occasionally, I can not reproduce this problem just by clicking to the page. I can, however, almost always reproduce it by clicking on a link on the main page, and hitting the back button. 

Here is the main page, and other affected pages are About Us, Music, and More.  
[http://power-pirate.com/index.html](http://power-pirate.com/index.html)

Please let me know what you think might be causing this issue, and if you have any suggestions for the code in general.

On a side note: I know that using a table as I did on these pages may not be the best way to do it, and I am currently working on a div only version. I still have the problem with the white background on that version. 

Thanks!
m

---

### Post by myrtle1908 on 2009-12-12
Site looks nice.  Cannot reproduce the "white box" you speak of with Firefox 3.5.3.  What browser fails?

---

### Post by myrtle1908 on 2009-12-12
Furthermore, there is nothing wrong with your use of tables for basic layout.  Sure it will annoy the CSS police but who really cares.  Browsers aren't about to drop table support.  Use what works for you.

---

### Post by User3k on 2009-12-12
> **myrtle1908 said:**
> furthermore, there is nothing wrong with your use of tables for basic layout.  Sure it will annoy the css police but who really cares.  Browsers aren't about to drop table support.  Use what works for you.

+1

---

### Post by User3k on 2009-12-12
Also it looks fine to me as well. I am not seeing a white box at all.

---

### Post by Hellkeepa on 2009-12-12
HELLO!

First step to making a site bug-free, is to make sure that it [validates](http://validator.w3.org/check?uri=http%3A%2F%2Fpower-pirate.com%2Findex.html&charset=%28detect+automatically%29&doctype=Inline&group=0). Both the HTML and CSS should validate, and you should be using a strict (or XHTML 1.0 transitional) doctype. Anything else will cause the browsers to go into "quirks" mode, and then it's anybodys guess how your site is presented.

As for those who say "tables are OK for layout", do you feel that Writer/Word is OK for budgets as well? We're talking about using the correct tool for the job here, a tool which'll minimize the problem and work you have to put into a project. Be it websites, or your finances.

Happy syncin'!

---

### Post by mpgarate on 2009-12-13
Thanks for all of the replies!

@hellkeepa - That makes sense. I would like to redo it with divs, so that I can more easily shape the containers to fit the content, rather than the other way around. 

@everyone - I mainly experience this problem in google chrome. See attachment.

---

### Post by jtuchscherer on 2009-12-13
I just saw the white box you were talking about. It took me about 10 attempts to get it (clicking wildly around on the top level nav links).

I didn't quite find yet why it is doing it. It seems like your body is not extending to the bottom edge in those rare cases. But here are two suggestions: 

1) On your body element you specify bgcolor and you set it to white (FFF). Don't do that. It is overwritten by your css anyways, but it may lead to incompatibility with older browsers. 

2)Why did you set the bottom attribute on your body to 5000px? That could cause some weird issues. If you don't need it (and I don't think you do) take it out.

---

### Post by User3k on 2009-12-13
I just reloaded the page around 30 times and saw the white on the bottom twice. I am using Google Chrome as well. I am really not sure why you are getting that white box when you do, everything looks ok at first glance. 

Also, I looked at the page source. Did you ever think about encrypting your emails there so bots can't get a hold of them? Might save on a lot of spam. There are also places on the internet that you can encrypt whole web pages, very simple to use if you ever wanted to check that out.

---

### Post by -grubby on 2009-12-13
It seems to work for me in Chrome. What version are you using?

---

### Post by abhilashm86 on 2009-12-13
it works in firefox, pls tell which version are you using?
```
firefox -v

```

---

### Post by mpgarate on 2009-12-13
I am using Chrome v 4.0.249.30. The problem can be rare.. but when it occurs it's really bothersome. Additionally, I think your browser window needs to be open to greater than the height of the web body (~1000px I think) I can not reproduce it on my laptop screen, with a height of 800. 

My Firefox is v 3.5.5

@jtuchscherer - Both very good points. Thanks for pointing those out, I will see what I can do with those. The bottom set to 5,000 was very likely me testing how the value would affect the page, and it's possible that at first glance it did nothing and I forgot about it, but then it could be causing this problem. I will see what happens if I get rid of it, or set a realistic value. 

@User3k - Encrypting the emails sounds like a great idea.. I will get on that.

---

### Post by v8YKxgHe on 2009-12-13
> **Hellkeepa said:**
> First step to making a site bug-free, is to make sure that it [validates](http://validator.w3.org/check?uri=http%3A%2F%2Fpower-pirate.com%2Findex.html&charset=%28detect+automatically%29&doctype=Inline&group=0). Both the HTML and CSS should validate, and you should be using a strict (or XHTML 1.0 transitional) doctype. Anything else will cause the browsers to go into "quirks" mode, and then it's anybodys guess how your site is presented.

While it should validate against W3C standards, XHTML 1.0 Transitional is 100% not required for a browser to run in non-quirks mode. Besides, why suggest transitional for **new** projects? That makes no sense.

Ideally, you want to be running HTML 4.01 strict, 100% not XHTML 1.0 Transitional.

---

### Post by mpgarate on 2009-12-13
I believe my header is set to strict. Is there anything there I need to change in my current header? I will go through and validate.. I am sure there are plenty of problems there.

edit: MANY of my validation errors are like

> Line 98, Column 17: element "CENTER" undefined. Did you mean "center"?
<HR><div><center><b><a href="vote.html">Thank you for voting for Power Pirate!

In the code, center is lower case. I tried going over and retyping it, in case something funny was making it appear upper case (I can't think what). No luck. These are the vast majority of the errors, along with a few missing alt="" for some images.

---

### Post by Hellkeepa on 2009-12-13
HELLo!

**AlexC**:
I recommended XHTML 1.0 trans as an alternative to either HTML 4.01 strict or XHTML 1.0 strict, which is why I put the parenthesis around it and after recommending using "strict doctypes".
In short: We are in agreement.

Those are the only three doctypes that will ensure that all browser stay in standard compliant mode, which is what I was trying to explain in that quoted part. Apologies if that intent was a bit unclear.

**mpgarate**:
Add a strict doctype first, and *then* fix the errors as they crop up. As mentioned above, a site without the proper Doctype is always rendered in quirks mode. Errors in the strict types, can also cause the browser to go into quirks mode, and thus should the site validate. (Not to mention, it becomes quite a lot easier to read the source afterwards.)
Also, what you've done is to mix markup with style, and it's always a sure fire way create a major headache for you. Let the CSS deal with the style of the site, and only the CSS.

Happy codin'!

---

### Post by mpgarate on 2009-12-14
**Update:** I recently uploaded a mailing list registration page ([http://power-pirate.com/registration.html]("http://power-pirate.com/registration.html")) completely generated by Mail Chimp, save for the Google Analytics code I added to the header. I just observed the white-background-box error on the bottom of this page as well. My conclusion is that the error is somehow related to the analytics code, which I have included below. Any ideas on what in the code might be causing this, and if it is fixable?
```
<script type="text/javascript"> 
var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
</script> 
<script type="text/javascript"> 
try {
var pageTracker = _gat._getTracker("UA-2515841-3");
pageTracker._trackPageview();
} catch(err) {}</script> 
```

---

### Post by Hellkeepa on 2009-12-15
HELLo!

Sounds more like a browser bug to me, than a page bug. Though you could try to change the JS bit to this:
```
<script type="text/javascript"> 
<!--

var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));

try {
var pageTracker = _gat._getTracker("UA-2515841-3");
pageTracker._trackPageview();
} catch(err) {}
// -->
</script>
```
Not sure whether or not that try-catch block should be in the header, or in the body, though.

There are also two errors in the HTML-page, which prevents validation. Could be that too, that triggers the browser bug.

Happy codin'!

---

