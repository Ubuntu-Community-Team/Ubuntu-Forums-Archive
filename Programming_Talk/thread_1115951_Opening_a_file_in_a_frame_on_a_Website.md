---
title: "Opening a file in a frame on a Website"
date: 2009-04-04
forum: Programming Talk
---

### Post by linux4life88 on 2009-04-04
I have a website that has three column design and in the right side column I have information that is updated often. To update it I have to change the information on all pages of my website. I was wondering if there would be a way to have an external file that I could open in that frame on each separate page of the website. This would allow me to edit just one document and that would update all of the web pages at once. Is there a way to do this.

---

### Post by scragar on 2009-04-05
Look into server side includes and see if your host supports them, if not you might be forced to use frames(An iFrame is best), they are inefficient and an ugly solution though.

---

### Post by linux4life88 on 2009-04-06
Isn't there just a way to open an html document inside of another html document? I remember doing this before, I just can't remember how. I don't remember using sever side language to do it though. Thanks for the help

---

### Post by linux4life88 on 2009-04-07
Bump

---

### Post by linux4life88 on 2009-04-09
Bump

---

### Post by cpetercarter on 2009-04-09
I guess this may not be practical for your site, but if you use the Smarty templating engine to generate web pages, incorporating sub-templates for specific sections of the web page is a piece of cake.

---

### Post by lemuriaX on 2009-04-09
On a LAMP server, Server Side Includes is probably what you want. You might just need to add some code to your .htaccess file depending on how your server is configured. Check out the reference here:

[http://httpd.apache.org/docs/1.3/howto/htaccess.html#ssi](http://httpd.apache.org/docs/1.3/howto/htaccess.html#ssi)

---

### Post by tturrisi on 2009-04-10
> ...they are inefficient and an ugly solution though.

iFrames work well and can be customized using CSS to look good.  They are NOT inefficient as all rendering is done by the client and it puts no load on the server.

Just add this code to the right column of page and all you have to edit is the one source html page, upload it and it will change on all pages.

```
<iframe src="path/name-of-page.html" name="my-iframe" frameborder="0 or 1" width="pixels or %" height="pixels or %"  scrolling="yes or no or auto" style="text-align:center; vertical-align:top; background-color:some-color; margin:pixels or %; padding:pixels or %;">
```

You can omit the width and height in the above code and use CSS width & height.

You can even use a link to change what's displayed in an iframe!

```
<a href="path/name-of-page.html" target="my-iframe">Click Here</a>
```

---

### Post by linux4life88 on 2009-04-12
iframe that is it, that is what I was trying to think of. Thank you very much tturrisi, this will save me a lot of time.

---

