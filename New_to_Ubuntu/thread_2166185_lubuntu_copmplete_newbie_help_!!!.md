---
title: "lubuntu copmplete newbie help !!!"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by ian5 on 2013-08-08
Hi
I have just installed lubuntu 13.04 .
I have several points I need help with.
1/ I noticed flashplayer was not installed , I found one instuction which said "sudo apt-get install adobe-flashplayer £ I did this but it said this was not possible.
So I went to adobe's website and I thought I would download it, now there were several choices , I assumed at first it would be the ubuntu version so I tried that , I got the message no apt available for this so I thought I would try to the tar version. I know a litlle about linux and I beleive I have to put this in the folder . ( I have installed firfox as I prefer this browswer to chromium ). I could not find the firefox folder or I am looking in the wrong place.
Can someone help me with tihs as I do use youtube and other sites that need flash.

2/ I need my printer installed when I clicked on the set up printer it does not show that my printer is connected . it is  and it is on. It just says connect . I did a trouble shoot and I got the instuctions to go to System - admininstrator - Servies and look for cups services.
I do not have this on my menu. I have looked through the system tools menu and everything else.
I need help.

I will be very grateful for any help.

Thanks 


Ian

---

### Post by Gone fishing on 2013-08-08
If you open a terminal and run sudo apt-get install lubuntu-restricted-extras this should install all the restricted formats you need including flash. For the printer we will need a little more information such as the name and model of the printer

---

### Post by Sockerdrickan on 2013-08-08
As for the flash installer, try this command:

```
sudo apt-get install flashplugin-downloader
```

---

### Post by fantab on 2013-08-08
Flash player is available in 'Partner Repositories'. So you have to enable 'Partner Repositories'... you can enable them using either 'Software Center' or 'Synaptic Package manager'. Also If you install Lubuntu-restricted-extras package you will get flash as well as other restricted formats, like support for mp3 etc. This package also install some Microsoft fonts. If you don't want the fonts then don't accept the EULA.

What Printer brand do you have?

---

### Post by ian5 on 2013-08-08
Thank you just saw the replies. I will try them when I get home.
My printer is an Hp Deskjet 720 C, itso lf but it is brilliant

---

### Post by Rex Bouwense on 2013-08-08
HP is very Linux friendly.  Go the HP web site
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
That should solve your problem.

---

