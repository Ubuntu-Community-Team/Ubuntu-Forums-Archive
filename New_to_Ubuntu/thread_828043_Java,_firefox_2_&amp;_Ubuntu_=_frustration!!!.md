---
title: "Java, firefox 2 &amp; Ubuntu = frustration!!!"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by mzdutchdoll on 2008-06-13
I know there are already threads regarding Java, but I am a complete beginner when it comes to Ubuntu so I need some help put extremely simply. I want to play on Yahoo Games and I am continuously prompted to download Java, which I have done again, and again, and again...and it doesn't work. I went into system, then into administration and there it is, just sitting there looking pretty- the plugin cotrol panel and the policy tool. I have tried going through the add-ons box in mozilla, then through the mozilla plug-in page but the java it prompts me to download won't open once it's finished. Is there a simple way to get Java working that I could understand? Or better yet is there another browser you can use on Ubuntu that doesn't have Java problems?

---

### Post by Bablefish on 2008-06-13
To get Java the easy way just go to Add Remove from your applications menu

---

### Post by wPwLUi3N on 2008-06-13
A screen shot of the not working applet would be very helpfull. What kind of error it is giving?

---

### Post by Nepherte on 2008-06-13
Be sure you have the sun-java6-plugin package installed if you are running 32bit, if you use 64bit I suggest you try icedtea-gcjwebplugin.

---

### Post by gandaran on 2008-06-13
> **mzdutchdoll said:**
> I know there are already threads regarding Java, but I am a complete beginner when it comes to Ubuntu so I need some help put extremely simply. I want to play on Yahoo Games and I am continuously prompted to download Java, which I have done again, and again, and again...and it doesn't work. I went into system, then into administration and there it is, just sitting there looking pretty- the plugin cotrol panel and the policy tool. I have tried going through the add-ons box in mozilla, then through the mozilla plug-in page but the java it prompts me to download won't open once it's finished. Is there a simple way to get Java working that I could understand? Or better yet is there another browser you can use on Ubuntu that doesn't have Java problems?

yes it's very simple to get java working in firefox 2!
1. make sure you have sun-java6 or sun-java6-plugin  and not open java installed.
2. copy the libjavaplugin.so file from the firefox 3 (/usr/lib/xulrunner-1.9/plugins/libjavaplugin.so) and paste the same file to /usr/lib/firefox2/plugins or better still /usr/lib/mozilla/plugins.

---

### Post by alienexplorers on 2008-06-13
You need to sym-link the file to the firefox 2 plugins directory.  Just loading java will not do this.  Without the libjavaplugin_oji.so file linked to your firefox 2 plugins folder, java will not work.

---

### Post by mzdutchdoll on 2008-06-21
How do i sym link? I'm new to Ubuntu and none of this advice is helping me because i don't understand any of it. I don't know where the directories are on this OE.

---

### Post by Pjotr123 on 2008-06-21
This is an easy how-to for full 100 % multimedia support, including Sun Java:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

I play a lot of chess on Yahoo Games. It's fun there!  :-)

---

