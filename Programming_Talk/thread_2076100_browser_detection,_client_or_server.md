---
title: "browser detection, client or server?"
date: 2012-10-25
forum: Programming Talk
---

### Post by chuchi on 2012-10-25
Hello everyone!
 

 I am developing a website using CSS3 animations, video, canvas etc and the same website for mobile devices.
 

 So, depending on the browser the content varies. For example:
 

 If the user has a mobile browser the content is different.
 If the user is using IE, I can not show animations.
 Etc.....
 

 I know that this must be a stupid question, but I have read a lot on the web. Is it better to do the Browser detection with server side (PHP) or JavaScript??
 

 For what I have read, it seems to me that it is better to do in PHP, including files depending of the browser.  
 

 Thank you very much!!!

---

### Post by myrtle1908 on 2012-10-25
Definitely client-side.  Also best to use a decent feature detection lib rather than sniffing the UA string (which is unreliable).  Try here [http://modernizr.com/](http://modernizr.com/)

---

### Post by chuchi on 2012-10-26
Hi myrtle190! thanks for reply.  I have read your link about modernizr to perform browser detection on the client-side.

This is what I can do with modernizr:

```

if(!Modernizr.cssanimations)  	window.location='nocss3/index.php';

```

can't I? this is very useful for me!

But also I need to do mobile detection. I have been reading 
about modernizr in the web, and it seems to me that I can not perform
a mobile detection.

How can I do that??
Thank you very much!

---

### Post by Lars Noodén on 2012-10-26
I would say the opposite: definitely server side!

That takes out the complexities of trying to run scripting on clients that may or may not support your script and may even have scripting turned off.  More of the security conscious people (or those tired of ads) will browse with javascript off.  With the server side detection you have full control over what is server and how the selection is made.

---

### Post by chuchi on 2012-10-26
Hi Lars Noodén! thanks for reply! I agree with you. But I have read that it is possible to fake the user agent of the client browser... What about that?

---

### Post by spjackson on 2012-10-26
> **chuchi said:**
> But I have read that it is possible to fake the user agent of the client browser... What about that?
Why is that a problem? If a user tells you they are using IE when they are not, by means of faking the user agent, and you deliver content tailored for IE, then the user has got what they asked for.

---

### Post by Lars Noodén on 2012-10-26
> **spjackson said:**
> Why is that a problem? If a user tells you they are using IE when they are not, by means of faking the user agent, and you deliver content tailored for IE, then the user has got what they asked for.

Agreed.  If the user agent is faking the identifications string, it means that the client is prepared to function as that browser and will work if your site treats it as such.  Think of it as one form of customizing the browser.  People really do spend time customizing their browsers to get them working the way they like it, even if not all modify their browser identification strings.

---

### Post by Vaphell on 2012-10-26
+1
respect the user's configuration, don't double guess him, take the data his browser sends at face value.
And one more thing: don't be a control freak with pixel perfect layouts that break when user changes default font size (some people have poor sight etc) in browser prefs or forces his own set of fonts (because he can, that's why ;-) ). Graceful degradation all the way.

---

### Post by chuchi on 2012-10-26
I agree with all of you. Thank you very much for your help, it has been very helpful for me!!!

Now I am using WURFL to browser detection on the server. But once installed, it takes more than 10MB!!! do you know other libraries for browser detection??

---

### Post by Lars Noodén on 2012-10-26
I'm not familiar with WURFL.  Do you have a link?  I also realize that PHP libraries have a reputation for being unfinished and incomplete but maybe there is something there that can be used instead.  

However, there's really only one browser series that is problematic so why not let it detect itself?  

```

**<!--**[if IE]>
      @import url("msie.css");
<![endif]**-->**

```

The above is legitimately a comment so real browsers will just ignore it.  And if you design the XHTML + CSS right, the older browsers will still have something to render even if not as pretty.  The principle is called degrade gracefully or something like that.

---

### Post by chuchi on 2012-10-26
Hi!! take a look at this:

[http://ofps.oreilly.com/titles/9781449316419/appa.html](http://ofps.oreilly.com/titles/9781449316419/appa.html)

I agree with you in that there is only one problematic browser IE...... very problematic indeed!!!

But people can also use older versions of firefox or safari.....

---

### Post by Lars Noodén on 2012-10-26
Thanks for the WURFL link.  I hadn't seen that before.  

The [get_browser](http://php.net/manual/en/function.get-browser.php) function in PHP claims to be able to return an array with data about what a browser supports.  Would that do what you need?

About the older versions of Firefox, Safari, etc. they do fine with CSS, it's just that they ignore the newer features but otherwise work just fine if things are set up to [degrade gracefully](https://www.google.fi/search?q=degrade+gracefully).

---

### Post by chuchi on 2012-10-26
You are welcome!! Yes the get_browser function of PHP seems to do that I want! thanks a lot!!

---

