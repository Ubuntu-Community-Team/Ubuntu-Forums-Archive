---
title: "can you make firefox apps work as apps"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by snowguy on 2011-11-09
I prefer sticking with the default ubuntu programs on the theory that my life is easier when I need help (as I often do). But I've had it with firefox and am about to switch to Chrome. Before I do though I thought I'd find out if there is a simple solution to my problem and I am missing it.

I want to be able to use my gmail and pandora as a separate app from the browser. Separate app = proper alt-tab switching and no interference with my browser. At first I thought the "Pin as App tab" would solve my problems, but when I really started working with it I found that it was always getting in the way. Simple example: after browsing around I have 7 or 8 tabs open. I don't need them so I close firefox and my music from pandora stops playing. 

So next I said (after searching around), I'll create a new profile for gmail and pandora. But I find firefox profiles very buggy or very poorly designed. I'm not sure which. Example: I create a profile called "Apps" and start it with firefox -no-remote -P Apps and I get a fresh copy of FF that I can start gmail and pandora from...great. But then I click firefox to do browsing and it opens up for browsing with my "Apps" profile. In order to have a "browsing" default profile and a separate apps profile, I have to remember to always open firefox with the browsing profile before I open up the firefox with the apps profile. Is that a bug or a the expected behavior? I don't know.


Anyway, before I make the switch has anyone gotten firefox apps to work as apps in ubuntu 11.10 with unity?

---

### Post by Alwimo on 2011-11-09
[http://library.gnome.org/misc/release-notes/3.2/#epiphany](http://library.gnome.org/misc/release-notes/3.2/#epiphany)
 
Try out the instructions in the Web Applications section. I haven't tried these.
 
As Unity in Ubuntu 11.10 is based on Gnome 3.2, it should work.

---

### Post by snowguy on 2011-11-09
Ok. From what I have read I see people have been able to make Chrome work. And Alwimo suggests moving to Epiphany. Thanks Alwimo for that suggestion. 

But before I go there, does anyone have a suggestion on how to do this Firefox?

> **Alwimo said:**
> [http://library.gnome.org/misc/release-notes/3.2/#epiphany](http://library.gnome.org/misc/release-notes/3.2/#epiphany)
 
Try out the instructions in the Web Applications section. I haven't tried these.
 
As Unity in Ubuntu 11.10 is based on Gnome 3.2, it should work.

---

### Post by Alwimo on 2011-11-09
It's not from Firefox, but from another Mozilla program called Prism. That's as close as I know.
[http://prism.mozillalabs.com/](http://prism.mozillalabs.com/)

---

### Post by snowguy on 2011-11-11
Looks like Prism has been dropped from the repositories. I think I could still install it from an RPM but that sort of defeats my reasoning for staying with firefox in the first place (wanting to stick with the standard install). Looks like I'm off to Chromium. thanks.

---

### Post by snowguy on 2011-11-22
just want to provide an update.  I was able to get this working (though not perfectly) using chromium. After installing chromium in order for the app to be treated as a separate app (instead of just another browser window), I had to use this workaround [http://askubuntu.com/questions/59014/how-can-i-make-chromium-app-windows-count-as-their-own-application-in-the-unit](http://askubuntu.com/questions/59014/how-can-i-make-chromium-app-windows-count-as-their-own-application-in-the-unit)

Note that the workaround says it doesn't apply to 11.10; however, as already noted by a comment there, the work around is still required.

Also, even after all this it doesn't work perfectly. Here's an example to show that we still aren't at the point where we can use separate "web-apps" as apps in Ubuntu. I have two apps: a default chrome app for browsing and a gmail app for reading e-mail. When an e-mail in my gmail has a link in it and I click in it, it should open up the link in my default browser (now Chromium). Instead it opens up the link as a new window of my gmail web-app.

---

### Post by ankspo71 on 2011-11-22
Hi,
This can sort of be done with separate application shortcuts for firefox... one for Firefox itself, and one for Gmail in Firefox, and one for Pandora in Firefox, and you can still share the same firefox profile. Closing one window will not close the other windows, and you should be able to manage the windows through Alt Tab (I tested this in Xubuntu's Alt Tab). 

Firefox is normally started with the command: 
```
firefox
```

But
```
firefox -new-window http:www.pandora.com/
```
will always open a separate window for Pandora in Firefox. 

And
```
firefox -new-window https:mail.google.com/mail/
```
will do the same for Gmail.

Now use a start menu editor (such as alacarte or maybe lxmed) to create application shortcuts in the start menu using the commands above.

```
Name: Pandora
Icon: any icon you would like to use
Command: firefox -new-window http://www.pandora.com/
```

```
Name: Gmail
Icon: any icon you would like to use
Command: firefox -new-window https://mail.google.com/mail/ 

```

---

### Post by snowguy on 2011-11-22
ankspo71, thanks for the tips and these are interesting. But I don't think I was very clear on what I meant by making "apps work as apps." What I mean is I'd like unity to treat them as though they aren't part of the browser, but rather standalone apps. Using alt-tab as an example, that means when I use alt-tab the gmail window would not be bundled together with the other firefox windows. 

I can explain more clearly if you have questions. If you are using Xubuntu the problem may not be applicable.

---

### Post by ankspo71 on 2011-11-22
Oh I see, I forgot that the Alt Tab in Unity groups the application windows together. I found this recent video about using Alt Tab and Alt ` in Unity.
[http://www.youtube.com/watch?v=XHFNnygpvcM](http://www.youtube.com/watch?v=XHFNnygpvcM)
(the actual key used varies depending on our keyboard layouts).

---

