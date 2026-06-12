---
title: "firefox and IE"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by dineshs on 2008-10-15
I am using hardy. I have a problem with firefox not opening a secure site which explorer does.I tried user agent switcher which opens this site but cant click the links in it. It shows an error -event is not defined...........Line: 144 .IE is installed but Wine makes my machine slow.I am not an expert.Please help.

---

### Post by trikster_x on 2008-10-15
Could you give the name of the site, or is it a security issue?

---

### Post by dineshs on 2008-10-15
It is a private IP [https://10.240.32.197](https://10.240.32.197) .Before installing user agent switcher it was showing ``It is required to use Internet Explorer 4.0 or later, and enable JavaScript. Please make sure that your browser meets the requirements"

---

### Post by Cl0ud9 on 2008-10-15
The fact that you are getting an error when trying to access a secure site leads me to believe that the website is using an encryption algorithm that Firefox doesn't support. Try finding out what encryption algorithm the website is using and then changing the appropriate settings by typing "about:config" in the url bar.
If you don't want to do that, then try a different web browser like [Opera]("http://www.opera.com/")

---

### Post by dineshs on 2008-10-15
I tried opera but gets the same error

---

### Post by pak33m on 2008-10-16
dineshs,

I had a similiar thing happen but I knew that I couldn't get to a web site with Firefox but I could with IE.  The web site belonged to a customer that I was working on.  The reason I could get in with IE but not Firefox or Opera even is because the customer only allowed 1024-bit encryption.

In order to prove to a coworker that I could get to the customer web site with Firefox was to (like Cl0ud9 mentioned) go to about:config in the address bar and enable the parameters following:

```
security.ssl3.rsa_1024_rc4_56_sha
```

```
security.ssl3.rsa_1024_des_cbc_sha
```

While in about:config you can easily search for **1024** and double-click the aforementioned parameters to toggle both to **true**.

You can try it to at least see if this is what is required of the web site in question.

Hope this helps.

---

### Post by dineshs on 2008-10-16
I tried but it didnt help

---

### Post by linux6994 on 2008-10-16
It sounds like you do not have java installed. Look for sun-java6-jre in synaptic and make sure its installed.

sudo apt-get install sun-java6-jre

---

### Post by dineshs on 2008-10-16
Still the same error

---

### Post by pak33m on 2008-10-16
One other thing I forgot to mention about using Opera.  Not because I'm a big fan but I have had to use a feature in Opera that allows you to mask Opera as IE or Firefox.  I have to do this at work when I know that a web site requires IE.

If you try it you should go to the web site.  Go to Tools -> Quick Preferences -> Edit Site Preferences, click on the Network tab and set the Browser Identification to Mask as Internet Explorer or Identify as Internet Explorer.  You can try both settings if you like.

Hope that helps.

---

### Post by dineshs on 2008-10-16
Now I am getting the login page but when i login the next page goes blank

---

### Post by Bucky Ball on 2008-10-16
Have you got:

ubuntu-restricted-extras

installed? Java could be your problem and that will install it (among other good bits). You can find it in Synaptic Package Manager (System->Administration).

---

### Post by dineshs on 2008-10-16
To confirm I used the command  sudo apt-get install sun-java6-jre
It said sun-java6-jre is already the newest version

---

### Post by TeaSwigger on 2008-10-16
Mind that I defer to any others here who may have better technical knowledge to get Firefox, Opera or something working for you first.

But if you absolutely must use IE for this, perhaps running IE on WINE will work. IEs4Linux is a site that has, or at least had, an easy to install version. Ubuntu has WINE in the repositories for your convenience and IEs4Linux should be readily found by a web search. That may not work in this case and you'll probably want to try anything else first; if you do go that route, use it with caution, only as needed.

Good luck. :)

---

### Post by dineshs on 2008-10-16
I have IE and wine but the machine becomes slow,and sometimes Explorer is not opening,and I need to restart.Also I always need that site for my work

---

### Post by Bucky Ball on 2008-10-16
For your work? Talk to you system admin about this issue and see if they can help. They could have it somehow tweaked to only expect IE and reject all else for security reasons. You may be able to do something with your ip for security instead ... or something.

---

### Post by alphacrucis2 on 2008-10-16
> **Bucky Ball said:**
> For your work? Talk to you system admin about this issue and see if they can help. They could have it somehow tweaked to only expect IE and reject all else for security reasons. You may be able to do something with your ip for security instead ... or something.

As a matter of interest I tried connecting to this site using both Firefox and IE running under Windows. Both timed out so maybe the site is down at the moment, so I can't say whether or not Firefox has the same problem under Windows. I have heard of web sites that are deliberately set up to block browsers other than specific ones they want. Apparently the browsers identify themselves to the web server (I guess that's how web stats can tell you such things as which browsers, OS etc are connecting). I believe it is possible to fudge Firefox so that it identifies itself as Internet Explorer to fool such web servers to bypass such blockage (I haven't looked into how to do that though). I guess you would still have trouble if the site required active X objects of course.



Edit: another reason I didn't get a response is that maybe a firewall is only allowing certain source ip addresses or address ranges to connect to that server.

---

### Post by Bucky Ball on 2008-10-16
> **alphacrucis2 said:**
> Apparently the browsers identify themselves to the web server (I guess that's how web stats can tell you such things as which browsers, OS etc are connecting). 
Edit: another reason I didn't get a response is that maybe a firewall is only allowing certain source ip addresses or address ranges to connect to that server.

Both reasons it needs to be tweaked at their end I would think.

---

### Post by t0p on 2008-10-16
> **Bucky Ball said:**
> Both reasons it needs to be tweaked at their end I would think.

It seems a bit crazy for the OP to use 2 browsers and god-knows what configuration tricks if he knows the site admins and could get them to tweak the site.

---

### Post by pak33m on 2008-10-16
dineshs,

When you said the following:

> Now I am getting the login page but when i login the next page goes blank

Did this happen after I suggested in Opera to Mask as Internet Explorer?

If so, the second page that you're referring to that comes up blank may need to me masked as well.

Another two cents there :)

---

### Post by dineshs on 2008-10-16
I tried opera to mask as IE and identify as IE.Both gave the same result.(Our system admn asks me to use ie!!)

---

### Post by Bucky Ball on 2008-10-16
One more time, talk to your systems admin at work.

---

### Post by oldsoundguy on 2008-10-16
Explain in language a 3 year old could understand to that systems administrator that IE no longer holds 50% of the browser market and is losing ground at the rate of 2 - 3 % per month.  Firefox ALONE will surpass IE (all iterations combined) by the end of the year .. yet alone adding in chrome or safari or opera.

---

### Post by dineshs on 2008-10-17
I shall do that.Thanks to all for the valuable guidance

---

### Post by Bucky Ball on 2008-10-17
> **oldsoundguy said:**
> Explain in language a 3 year old could understand to that systems administrator that IE no longer holds 50% of the browser market and is losing ground at the rate of 2 - 3 % per month.  Firefox ALONE will surpass IE (all iterations combined) by the end of the year .. yet alone adding in chrome or safari or opera.

lol, like what he said and no probs. Don't forget to repost with any other problems. :)

---

