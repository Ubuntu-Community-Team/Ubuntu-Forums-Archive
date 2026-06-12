---
title: "some kind of proxy program"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by patchido on 2008-08-27
well... this post is to ask if there is some kind of program that makes internet think i am in another site... i know there is one for windows but i cant remember the name.... its because at school i cant get into some pages such as youtub i have to go through vtunnel.com... so is there any program that makes this?

---

### Post by kaivalagi on 2008-08-27
> **patchido said:**
> well... this post is to ask if there is some kind of program that makes internet think i am in another site... i know there is one for windows but i cant remember the name.... its because at school i cant get into some pages such as youtub i have to go through vtunnel.com... so is there any program that makes this?

I host cgiproxy on my home pc via apache, I can then access anything from work...

[http://www.jmarshall.com/tools/cgiproxy/](http://www.jmarshall.com/tools/cgiproxy/)

Hope that helps

---

### Post by patchido on 2008-08-27
what i want is that i dont have to enter any other page... that i only have to type the adress where i want to be masked

---

### Post by kaivalagi on 2008-08-28
> **patchido said:**
> what i want is that i dont have to enter any other page... that i only have to type the adress where i want to be masked

It does just that! It is a "web proxy", it's what they do :) As long as you can reach the site where it is setup you're away.

Check out the screenshots of a session on my localhost, where the url stays at the localhost but I am viewing flickr.com. For it to work for you it would need to run on a website outside of your school which your school doesn't block.

If you need something to directly run on your school computer then sorry, I can't help you there....I really shouldn't helping anyway ;)

Cheers

---

### Post by dioltas on 2008-08-28
I set up a proxy on an old computer I had at home. I installed debian on the computer because it was a bit old for ubuntu. I used squid, a web proxy program for linux. Then you have to set up a ssh server on the box. You'll probably have to forward the port that the ssh server is listening on in your router settings.
Then set up a no-ip.com account, so that if your home ip address changes, you'll still be able to connect to your server.

Then from your computer at school/work or whatever, you have to set up a ssh tunnel to your server. You then set some proxy settings in your internet browser and your good to go. You just browse the web normally.


It might be a bit complicated for a beginner, but there's some good guides on the net.
Google "squid ssh tunnel" etc and you'll find loads of stuff.
Once you have it set up it works fine.

Only reason I did it was because at work they've blocked those cgi proxies aswell somehow. If they work for you, I'd recommend using them as their alot easier and you don't have to set up anything.

Both of these links should find you lots of cgi proxies:
[URL="http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22start+using+cgiproxy%22&btnG=Google+Search"]
http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22start+using+cgiproxy%22&btnG=Google+Search[/URL]
[URL="http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22Start+browsing+through+this+CGI-based+proxy%22&btnG=Google+Search"]
http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22Start+browsing+through+this+CGI-based+proxy%22&btnG=Google+Search[/URL]
(I stole those from an article called 7 google tricks or something).

If you do try the ssh tunnel thing I'm sure you'll get plenty of help on here.

---

### Post by kaivalagi on 2008-08-28
> **dioltas said:**
> I set up a proxy on an old computer I had at home. I installed debian on the computer because it was a bit old for ubuntu. I used squid, a web proxy program for linux. Then you have to set up a ssh server on the box. You'll probably have to forward the port that the ssh server is listening on in your router settings.
Then set up a no-ip.com account, so that if your home ip address changes, you'll still be able to connect to your server.

Then from your computer at school/work or whatever, you have to set up a ssh tunnel to your server. You then set some proxy settings in your internet browser and your good to go. You just browse the web normally.


It might be a bit complicated for a beginner, but there's some good guides on the net.
Google "squid ssh tunnel" etc and you'll find loads of stuff.
Once you have it set up it works fine.

Only reason I did it was because at work they've blocked those cgi proxies aswell somehow. If they work for you, I'd recommend using them as their alot easier and you don't have to set up anything.

Both of these links should find you lots of cgi proxies:
[URL="http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22start+using+cgiproxy%22&btnG=Google+Search"]
http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22start+using+cgiproxy%22&btnG=Google+Search[/URL]
[URL="http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22Start+browsing+through+this+CGI-based+proxy%22&btnG=Google+Search"]
http://www.google.com/search?hl=en&q=inurl%3A%22nph-proxy.cgi%22+%22Start+browsing+through+this+CGI-based+proxy%22&btnG=Google+Search[/URL]
(I stole those from an article called 7 google tricks or something).

If you do try the ssh tunnel thing I'm sure you'll get plenty of help on here.

That's good to know, thanks

When they block my cgiproxy I'll have something else to try ;)

---

### Post by Separ on 2008-08-28
You could use the FoxyProxy addon for Firefox 3 and just search google for a list of working proxies.

---

### Post by patchido on 2008-08-28
ive added it and dont know what to do.... im talking foxyproxy btw

---

