---
title: "Chromium pepperflash detected as Adobe Flash 11.2..."
date: 2014-10-06
forum: New to Ubuntu
---

### Post by Tar_Ni on 2014-10-06
Hi,

This is causing me some issues, my Chromium browser with Google pepperflash-plugin installed is detected as Adobe Flash 11.2 by various websites.. This is a problem for me  since I can't watch videos on a sports website, it ask me to upgrade Flash.. I am on Lubuntu 14.04.1 LTS

I go to Chrome//plugins and indeed it says that I have:

[COLOR=#000000][FONT=Ubuntu]**Adobe Flash Player** - Version : 11.2.999.999Shockwave Flash 11.2 r999
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][TABLE="class: plugin-details-label"]
[TR]
[TD]Description :[/TD]
[TD]Shockwave Flash 11.2 r999[/TD]
[/TR]
[/TABLE]

[TABLE="class: plugin-details-label"]
[TR]
[TD]Emplacement :[/TD]
[TD]/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so[/TD]
[/TR]
[/TABLE]

That's very strange, because I removed Adobe Flash Player 11.2 when I switched to Chromium. And BTW Chromium not longer support NPAPI plugins..

How can I make Chromium show online that I am using the latest Pepper Flash 15.0?

---

### Post by vasa1 on 2014-10-06
Please give links for others to test.

---

### Post by Tar_Ni on 2014-10-06
Hi,

Thanks for you reply

I provided a screenshot ( my Lubuntu install is French BTW), as you can see, it says I have Adobe Flash 11.2 but still it's location is from the pepperflash folder. Which means Chromium is indeed using Pepperflash but it display online that I use Adobe 11.2 because that's what my browser is saying.. Strange because I no longer have Adobe 11.2 installed!

That causes some issues because even though some website know that I have Pepper Flash 15.0 (I right click on the video and it says ''About flash 15.0'') other places detect that I have 11.2 installed.. As a result I can't watch sports video on rds.ca and whatismybrowser.com tell me that my Flash 11.2 is outdated!

---

### Post by vasa1 on 2014-10-06
[https://bugs.launchpad.net/ubuntu/+source/pepperflashplugin-nonfree/+bug/1373271](https://bugs.launchpad.net/ubuntu/+source/pepperflashplugin-nonfree/+bug/1373271)

---

### Post by Tar_Ni on 2014-10-06
If it's a known bug that explains a lot.. Thanks.

I see there is a patch for the moment but I am not sure how it works. I am not an experienced user. Can someone explain me how to do this?

[https://launchpadlibrarian.net/185644749/pepperflashplugin-nonfree-version.diff](https://launchpadlibrarian.net/185644749/pepperflashplugin-nonfree-version.diff)

---

### Post by vasa1 on 2014-10-06
I think you just have to edit the specified file as shown in the patch. ```
--- etc-chromium-default.txt.orig	2014-09-24 10:21:59.885638163 +0300
+++ etc-chromium-default.txt	2014-09-24 10:25:13.585631239 +0300
@@ -5,7 +5,7 @@
 
 if [ -f $flashso ]
 then
-        flashversion=`strings $flashso|grep ^LNX|sed -e "s/^LNX //"|sed -e "s/,/./g"`
+        flashversion=`strings $flashso|sed -n -e '/LNX/ { s/.*LNX //; s/,/./g; p; q}'`
         CHROMIUM_FLAGS="$CHROMIUM_FLAGS --ppapi-flash-path=$flashso --ppapi-flash-version=$flashversion"
 fi
 

```But I hope somebody drops by and confirms it. I'm on Chrome so I don't have that file.

---

### Post by Tar_Ni on 2014-10-06
I did a clean install of my Lubuntu system, and downloaded Chrome instead of Chromium. To me, they are pretty much interchangeable though I like the fact that Chromium is a bit more open-source. That said, there is just less trouble with Chrome for the time being.

Annoying things about Chromium:

- User has to manually update Pepperflash-plugin from the terminal, without any notification of a new Pepper flash release.

- Bug which detect Chromium flash player as being the 11.2 plugin.


Well thanks for your help anyway Vasa.

---

### Post by vasa1 on 2014-10-06
I think that it was just a matter of removing the line marked with "-" and putting in the line with "+" in a file perhaps called /etc/chromium/default.txt and not "etc-chromium-default.txt".

Anyway, since I didn't do it myself I didn't want to suggest you do it. Let's still hope someone competent sees this thread :)

---

### Post by vasa1 on 2014-10-07
Something similar in this comment: [https://code.google.com/p/chromium/issues/detail?id=402850#c7](https://code.google.com/p/chromium/issues/detail?id=402850#c7)> Also to get the Flash version reported correctly I edited /etc/chromium/default to look for ^.*LNX rather than just ^LNX as <strings> finds the only instance of "LNX" has characters in front of it.

---

### Post by mc4man on 2014-10-07
Fairly simple, just edit /etc/*chromium-browser*/default & change that line (note location slightly different then mentioned
ex. here - 
```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS=""

# part for pepperflashplugin-nonfree : begin

flashso="/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so"

if [ -f $flashso ]
then
        flashversion=`strings $flashso|sed -n -e '/LNX/ { s/.*LNX //; s/,/./g; p; q}'`
        CHROMIUM_FLAGS="$CHROMIUM_FLAGS --ppapi-flash-path=$flashso --ppapi-flash-version=$flashversion"
fi

# part for pepperflashplugin-nonfree : end
```

---

