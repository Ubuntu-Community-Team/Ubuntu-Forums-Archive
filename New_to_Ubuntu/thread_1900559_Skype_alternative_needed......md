---
title: "Skype alternative needed....."
date: 2011-12-26
forum: New to Ubuntu
---

### Post by Autodave on 2011-12-26
Need to connect with family who are using Windows and Skype.  Is there a Skpe version for Linux?  Is there an alternative program that will connect w/Skype users?

---

### Post by fractalman on 2011-12-26
You can find skype in the software centre,

---

### Post by Autodave on 2011-12-26
> **fractalman said:**
> You can find skype in the software centre,


Downloaded it, but it will not open at all.  I am running 11.10 and figured it might not be compatible.

---

### Post by BertN45 on 2011-12-26
If you run the 64 bit version of linux, you have to ensure that it can run 32 bit programs like skype.
See: [http://www.ubuntugeek.com/new-features-in-ubuntu-11-10-oneiric.html](http://www.ubuntugeek.com/new-features-in-ubuntu-11-10-oneiric.html)

---

### Post by Autodave on 2011-12-26
> **BertN45 said:**
> If you run the 64 bit version of linux, you have to ensure that it can run 32 bit programs like skype.
See: [http://www.ubuntugeek.com/new-features-in-ubuntu-11-10-oneiric.html](http://www.ubuntugeek.com/new-features-in-ubuntu-11-10-oneiric.html)


Nope: running 32 bit.

---

### Post by nmaster on 2011-12-26
> **Autodave said:**
> Need to connect with family who are using Windows and Skype.  Is there a Skpe version for Linux?  Is there an alternative program that will connect w/Skype users?

the skype protocol is closed and proprietary. it was reverse engineered, but this is not endorsed by microsoft:
[http://www.geek.com/articles/news/the-skype-protocol-has-been-reverse-engineered-2011062/](http://www.geek.com/articles/news/the-skype-protocol-has-been-reverse-engineered-2011062/)

---

### Post by Autodave on 2011-12-26
> **nmaster said:**
> the skype protocol is closed and proprietary. it was reverse engineered, but this is not endorsed by microsoft:
[http://www.geek.com/articles/news/the-skype-protocol-has-been-reverse-engineered-2011062/](http://www.geek.com/articles/news/the-skype-protocol-has-been-reverse-engineered-2011062/)


OK then.  What Linux program should I try?

---

### Post by Lalaith on 2011-12-26
It may help to read this thread:
[http://ubuntuforums.org/showthread.php?t=1888507](http://ubuntuforums.org/showthread.php?t=1888507)

It was me asking about the same... I am now using either skype or the app of gtalk (gmail).

---

### Post by nmaster on 2011-12-29
> **Lalaith said:**
> It may help to read this thread:
[http://ubuntuforums.org/showthread.php?t=1888507](http://ubuntuforums.org/showthread.php?t=1888507)

It was me asking about the same... I am now using either skype or the app of gtalk (gmail).

i would agree that google talk is quite good.  it requires a google account, but if you already use gmail then its nbd.  i imagine most other people you know also have google accounts, no?

---

### Post by mastablasta on 2011-12-29
> **Autodave said:**
> OK then. What Linux program should I try?
 
 
skype for linux should work fine. if oyu are havign porblems or if oyu think nothing happens, then open terminal and type in "skype" it will give any error outputs and also launch it.
 
skype for linux may not have all features as the windows version, but it also doesn't suffer from adds and facebook interface bs.
 
 
i am not  why article on Skype is not opensource has anyhting to do with this topic. Skype IM interface is providing revenue to Skype (now Microsoft) wheather it runs on Windows or on Linux.
 
 
google talk is indeed a good alterantive but is also not a complete alternative. for example i can't make phone calls with it and even if i could they would be more expencive than via Skype. but for webchat it works fine.

---

### Post by HermanAB on 2011-12-29
Howdy,

When all else fails, go to the Skype web site and download the 'static' version of Skype.  It includes most of the required libraries and should work without too much trauma. 

A static version should include ALL the libraries but the Skype developers are a little clueless/careless.  You can see which libraries are needed with a program called ldd and then install any missing ones.

If sound won't work, install all, I really mean ALL, Pulse packages you can find in the repos.

If video won't work, install Cheese from the repos.

That is about it - eventually Skype should work - I use it all the time.

---

### Post by Derek Karpinski on 2011-12-29
Cheese is broken for a lot of people in 11.10........better to install VLC to test webcam functionality.

---

### Post by houseworkshy on 2011-12-29
I use skype in 10.04.3 64 bit and it works bar the video, which does work in cheese.  So if you are ok with text only then you could go back to that.  The video also works in some web based chat applications, like google and yahoo, if one puts in the flash none free package.  So you could downgrade to the 10.04 lts, this would also mean going back to the gnome gui which is for most, according to what I've read and experianced, a major plus.

---

### Post by BertN45 on 2011-12-29
I would seriously consider Google Talk, it is web based so you can use it from phones, windows pcs, macs or linux pcs, everywhere you can find a computer. Besides I saw that the costs for calling mobiles e.g. in Europe is half the price of Skype.

I think Google cannot use it in advertisement, because it is even cheaper then calling from one mobile company to another in the same country.

---

### Post by Lalaith on 2011-12-30
GoogleTalk is simpler to install and use (just my opinion being a newbie), but as nmaster asked, your contacts must have a google account too.
I am running also skype and didn't find major problems neither.

---

### Post by Zill on 2011-12-30
> **Autodave said:**
> Need to connect with family who are using Windows and Skype.  Is there a Skpe version for Linux?  Is there an alternative program that will connect w/Skype users?
Have you tried [Faceflow]("http://www.faceflow.com/")?

No software download required as it uses a standard web-browser (with flash).

---

