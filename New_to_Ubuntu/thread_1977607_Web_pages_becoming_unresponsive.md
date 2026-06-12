---
title: "Web pages becoming unresponsive"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by meduser on 2012-05-10
I am having a slew of issues with the Ubuntu 12,04 LTS release. I have been having flash and shockwave crashes since the install started. I have a thread going on it here:

[http://ubuntuforums.org/showthread.php?p=11911593#post11911593](http://ubuntuforums.org/showthread.php?p=11911593#post11911593)

Now, I am getting the web pages becoming unresponsive. They just freeze and stop then I get a pop up saying this page hase become unresponsive. Wait or kill the page. 

I am having this issue with:

Chrominum, Chrome, and Firefox. I have not tried other browsers, as it would seem a wasted experience.

I thought the problem was related to jdk -7, but that is not the case.

I have tried to turn off hardware acceleration in flash, but I can't uncheck the box.

Please help, as my internet experience sucks right now.

---

### Post by meduser on 2012-05-13
Anybody have any suggestions? I can't even surf the internet without becoming unresponsive..

---

### Post by idoitprone on 2012-05-13
> **meduser said:**
> Anybody have any suggestions? I can't even surf the internet without becoming unresponsive..

Did you update your graphic drivers?

---

### Post by meduser on 2012-05-13
Yes, I have tried both newest nvidia drivers, and have rolled it back one, as I read that the newest drivers have issues with 12.04

---

### Post by idoitprone on 2012-05-13
Open firefox in the terminal

search for terminal

Open it

enter ```
firefox 
```and hit enter
there the terminal will display all the problems with the program

Reproduce the crash and it will tell you

If you want it to log while you browser and still see the error

```
 firefox 2>&1 | tee  firefoxError.txt 
```run this command

---

### Post by meduser on 2012-05-13
when running chromium I get the following when running a video on yahoo...


(exe:20057): Gdk-WARNING **: XID collision, trouble ahead


any ideas what that means?

---

### Post by meduser on 2012-05-13
and shortly after this:

(exe:20057): Gdk-CRITICAL **: IA__gdk_drawable_set_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

---

### Post by Frogs Hair on 2012-05-13
The warning is an Xsession error and there are bug reports going back to 9.10 . I found nothing applicable to Gnome 3 so far.

---

### Post by meduser on 2012-05-13
I am running Ubuntu with Unity..don't know if that changes anything

---

### Post by flemur13013 on 2012-05-13
FF 12, Ubuntu 12.04, flash 11.2 r202 and/or r102

**I stopped FF from hanging by disabling the flash plugin.** "Flashblock" didn't cut it. 
I don't use chromium enough to comment on it.

The sites it hung on didn't necessarily have videos or any obvious reason for using flash; most youtube videos play without flash, and the websites work fine.

With the "all-in-one-sidebar" addon in FF you can enable/disable flash in one or two clicks when you occasionally need it - which is a **lot** less often than I thought.

---

### Post by idoitprone on 2012-05-13
> **meduser said:**
> I am running Ubuntu with Unity..don't know if that changes anything


apperently removing your settings might fix the problem

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823)

rename these files
.gconf .local .gnome2


If you want to test it without making changes

just make a new account, it is simpler to see if your old setting are wreaking havoc
if that does not work then the problem might be something else

---

### Post by meduser on 2012-05-13
I'll just make a new account and try that. Thanks.

> **idoitprone said:**
> apperently removing your settings might fix the problem

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823)

rename these files
.gconf .local .gnome2


If you want to test it without making changes

just make a new account, it is simpler to see if your old setting are wreaking havoc
if that does not work then the problem might be something else

---

### Post by meduser on 2012-05-14
Nope..same issues with a new user.

---

### Post by meduser on 2012-05-19
appears that having cairo dock installed plays havoc on the system...I purged the system of Cairo dock, and it seems to be running like a champ. I wasn't using Cairo dock, I had downloaded it, tried it once, found it annoying, and stopped using it..changed my login back to just Ubuntu.

seems fine now.

---

### Post by meduser on 2012-06-05
after multiple days of good surfing back to the crashes....

Happening on Chrome, Chromium, and Firefox.

past the point of being patient with this.

I did finally get shockwave figured out as now it does not crash. To adjust hardware acceleration, I had to go to Ubuntu 2d, and turn it off there.

---

### Post by meduser on 2012-06-17
anyone? can't figure out what is wrong

---

### Post by idoitprone on 2012-06-17
> **meduser said:**
> anyone? can't figure out what is wrong


nvdia drivers?

---

### Post by meduser on 2012-06-18
I had tried the newest ones, then rolled back to the ones I was using for 11.10. Same issue, and this has stretched on since 12.04 was released.

---

### Post by idoitprone on 2012-06-18
> **meduser said:**
> I had tried the newest ones, then rolled back to the ones I was using for 11.10. Same issue, and this has stretched on since 12.04 was released.

its well known that nvidia binary blobs does not play well with flash

---

### Post by meduser on 2012-06-20
So there is no way around this? Unless I get a different video card?

That seems like an issue that needs to be addressed.

---

### Post by idoitprone on 2012-06-20
> **meduser said:**
> So there is no way around this? Unless I get a different video card?

That seems like an issue that needs to be addressed.


theyre both proprietary we can do nothing about it

other than begging

there one thing

perhaps find a way to downgrade flash to a version that do not have video accel turned on

or

reinstall flash and remove hardware acceleration

---

### Post by meduser on 2012-06-21
I was able to turn video acceleration off...I logged out , and logged back into Ubuntu 2d. 

The webpages just stop loading, video or no.

I can be surfing the internet, and suddenly the pages stop loading, then I get the oops page. I don't think it is flash related.

---

