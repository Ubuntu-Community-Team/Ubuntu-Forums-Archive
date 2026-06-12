---
title: "Json and Gson?"
date: 2013-11-05
forum: Programming Talk
---

### Post by arnavkumartechno on 2013-11-05
For which language Gson and Json were created? Is there any other way to make a web page faster?

---

### Post by Lars Noodén on 2013-11-05
GSON and JSON were for Java and Javascript.  

You can make a page faster by removing all client-side scripting and using CSS for formatting and layout.  If you have images, icons or similar objects, you can make the page render faster by using the actual HEIGHT and WIDTH attributes for those objects.  Rendering faster makes it appear to load faster.

---

### Post by edouardtavinor on 2013-11-06
To speed up webpages the most important thing is to reduce the number of round trips to the server. This is particularly true for pages loaded over 3g or 4g, where a round trip can take upwards of a second. 

The best way to reduce round trips is to load less files. There are a number of tricks for this. A pretty standard one is to use the basic inline css you need to position elements on the page and then use javascript to create a new css-node to download any additional css you need. Another thing is to try not to use too many different css files and javascript files. 

Another way to reduce load times and improve web page performance is to get the server to deliver static files and then perform any logic you need on the page over javascript. 

One more thing you can look at is using images of various qualities. You can embed data urls in the inline css for small images. this will speed up rendering of those images. explicitly setting width and height of images in the css file is also useful here.

---

### Post by ofnuts on 2013-11-06
JSON=JavaScript Object Notation

GSON is a Java lib from Google to handle JSON.

---

### Post by Lars Noodén on 2013-11-06
> **edouardtavinor said:**
> To speed up webpages the most important thing is to reduce the number of round trips to the server. This is particularly true for pages loaded over 3g or 4g, where a round trip can take upwards of a second. 

The best way to reduce round trips is to load less files. There are a number of tricks for this. A pretty standard one is to use the basic inline css you need to position elements on the page and then use javascript to create a new css-node to download any additional css you need. Another thing is to try not to use too many different css files and javascript files. 

Another way to reduce load times and improve web page performance is to get the server to deliver static files and then perform any logic you need on the page over javascript. 

One more thing you can look at is using images of various qualities. You can embed data urls in the inline css for small images. this will speed up rendering of those images. explicitly setting width and height of images in the css file is also useful here.
 
Yes.  Load fewer files.  I kind of thought that went without saying but just today I saw a page with what looked like dozens of included files pulled from all over.  

However, javascript should still be avoided.  Consolidate on the server side and use static pages, or cache dynamic pages with a reverse proxy/accelerator, but for accessibility and security avoid relying on js.  The page can included it as an extra but should be designed in a way that it still works adequately when in a safe browsing mode with javascript turned off.

---

### Post by edouardtavinor on 2013-11-07
> **Lars Noodén said:**
> Yes.  Load fewer files.  I kind of thought that went without saying but just today I saw a page with what looked like dozens of included files pulled from all over.  

However, javascript should still be avoided.  Consolidate on the server side and use static pages, or cache dynamic pages with a reverse proxy/accelerator, but for accessibility and security avoid relying on js.  The page can included it as an extra but should be designed in a way that it still works adequately when in a safe browsing mode with javascript turned off.

There may be reasons to avoid javascript, but as you say yourself, unless you're using it to create the ui of the page, speed is not one of them. Analysing and running javascript code rarely takes apreciable time.

Javascript can be excellent for security. It allows things like rsa sums to be calculated in the browser which can be used to increase security in a number of instances. It can also reduce page load time immensely by making page loads superfluous. Instead information can be fetched from the server using ajax and displayed when needed.

---

### Post by Lars Noodén on 2013-11-07
On pages that force javascript to be turned on to use them, I all too often run into scripts that slow down and lock up.  Overall, I find that javascript reduces speed.  As to security, recommended practice is to keep it off.  You can't have XSS without javascript.  But that's neither here nor there.

JSON is a data format and there are more languages than just javascript which have modules to read or write it.

---

### Post by edouardtavinor on 2013-11-10
> **Lars Noodén said:**
> On pages that force javascript to be turned on to use them, I all too often run into scripts that slow down and lock up.  Overall, I find that javascript reduces speed.  As to security, recommended practice is to keep it off.  You can't have XSS without javascript.  But that's neither here nor there.

JSON is a data format and there are more languages than just javascript which have modules to read or write it.

Well there's a difference between JavaScript and badly written JavaScript. Your comment is rather like saying "I find looking at pictures of people playing computer games is quicker than loading and playing the game myself". That may well be the case, but the possibilities are very different. Things you can do in JavaScript are just impossible with static content. It allows you to have real applications in the browser. Of course that means that you have security issues which you don't have when looking at static content, and it's also possible to write scripts which misbehave, but I doubt the OP was intending to do this.

Most of the problems of JavaScript can be side-stepped by regarding it as the target for a proper programming language.

---

