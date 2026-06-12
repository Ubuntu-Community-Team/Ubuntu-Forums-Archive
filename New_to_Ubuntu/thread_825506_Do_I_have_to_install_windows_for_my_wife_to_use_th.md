---
title: "Do I have to install windows for my wife to use this webpage !!?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-11
HI,

I tried Windows Visualization(too slow)...I really dont want to duel boot...or want windows...

My wife is Korean and needs to pay the rent online at this address:

[http://www.wooribank.com/](http://www.wooribank.com/)

Installed swif-firefox...

What options do i have...? nothing happens when i click the first link....

Thanks..

---

### Post by Xiong Chiamiov on 2008-06-11
Considering that I don't read Korean, it's a bit difficult for me to tell what I'm doing, so I'm not sure if it works for me or not.  If it's just a matter of the site telling you that IE is required, you can
a) Use the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") to trick it into thinking you're using IE or
b) Install IE inside Linux using [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").

---

### Post by Ryadt on 2008-06-11
Hi try using this add-on 'agent switcher'

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

hope it helps

---

### Post by exile on 2008-06-11
I can't really help you because I can't read Korean but going there myself and clicking around it does seem to used the words XP SP2 a lot and all the examples are in vista.

Check out [http://www.mydigitallife.info/2007/07/13/changing-user-agent-for-firefox-web-browser/]("http://www.mydigitallife.info/2007/07/13/changing-user-agent-for-firefox-web-browser/")

You might be able to spoof the user agent strings.

Do so at your own risk though.

---

### Post by hopelessone on 2008-06-11
Ahhh Crap !! Active X after i spoofed it...

---

### Post by fenian on 2008-06-11
user agent switcher seems to work,the page looks different(see screenshot attached).

edit - Sorry after clicking a few links it does not appear to work.

---

### Post by irrdev on 2008-06-11
I might be wrong, but this website seems to use ActiveX. In that case, yes, you will have to use Internet Explorer on Windows. Be careful, though! I am always suspicous of websites that use ActiveX, as these objects have full access to your computer. In today's world of Flash, Java Applets, and Silverlight, there is no good reason for legit websites to be using ActiveX for visual presentation. Unless your wife really knows this website well, I would quite frankly stay away!

---

### Post by Xiong Chiamiov on 2008-06-11
[ActiveX works]("http://www.tatanka.com.br/ies4linux/page/Known_issues") (generally) on IEs4Linux, which I linked to in my first post.  Just make sure to get IE6, not 7.

---

### Post by bumanie on 2008-06-11
Depends what type of virtualisation you used, some programs have advantages for some situations, but aren't necessarily fast. If you use something like virtualbox or vmware, you should not find any reduction in speed. I run virtualbox and it runs as quick, if not quicker than off the hard drive installation. Here is a 'how to' setup virtualbox with usb support - you need the binary 'free for home use' to get usb support. [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---

