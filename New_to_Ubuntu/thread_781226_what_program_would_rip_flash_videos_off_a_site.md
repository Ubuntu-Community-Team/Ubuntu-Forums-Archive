---
title: "what program would rip flash videos off a site?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by love2learn on 2008-05-04
I am not talking about youtube only, I would like to be able to rip any flash video off of any site. such as windows has here:

 [I]Flash Rip Or Play (tm) is a tool to Rip (download) any Flash game or movie files or their links from IE pages viewed containing embedded Flash (.swf) file links. Features include Previewing Flash Links, Ripping Flash files to your hard drive to open and play at will, or saving Favorite Links for later preview or download.

[/I]is there anything like this?
Thanks for your help


sorry: i am using ubuntu gutsy

---

### Post by NightwishFan on 2008-05-04
There is a command line application that rips youtube videos called "youtube-dl". I have tried it and it works fine. For other flash videos I have no idea, however there is a firefox extension that can rip them I believe.

---

### Post by metalf8801 on 2008-05-04
there are lots of Firefox add ons that will let you do that heres a link to one of them 
[https://addons.mozilla.org/en-US/firefox/addon/3590](https://addons.mozilla.org/en-US/firefox/addon/3590)

---

### Post by love2learn on 2008-05-04
I downloaded 
**Fast Video Download 1.5**


and tried to get the video but came up with this:

---

### Post by NightwishFan on 2008-05-04
```
sudo apt-get install ubuntu-restricted-extras
```
That should fix your problem.

---

### Post by love2learn on 2008-05-04
> **NightwishFan said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```That should fix your problem.


got this:

lucana@laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lucana@laptop:~$

---

### Post by stinger30au on 2008-05-04
this should help

[https://addons.mozilla.org/en-US/firefox/addon/2390](https://addons.mozilla.org/en-US/firefox/addon/2390)

---

### Post by imT on 2008-05-04
go to "/tmp" after the flash video is loaded and you'll get it there :)

---

### Post by HunterThomson on 2008-05-04
I just go to keepvid.com ....

You just cut and past the url into the like and select googlevideo or utube or whatever it is and then hit enter then it will give you a like to the download. :)

---

### Post by HunterThomson on 2008-05-04
> **imT said:**
> go to "/tmp" after the flash video is loaded and you'll get it there :)

Now that is a cool way! I love Linux:)

---

### Post by love2learn on 2008-05-04
> **imT said:**
> go to "/tmp" after the flash video is loaded and you'll get it there :)

nice! thanks

---

### Post by iheartubuntu on 2008-05-08
> **imT said:**
> go to "/tmp" after the flash video is loaded and you'll get it there :)

Didnt work for me. I tried it with youtube and a video on joox.net. Theres a bunch of junk in my temp but nothing that looks like a vid file or labeled youtube or anything.

---

### Post by imT on 2008-05-08
> **shirteesdotnet said:**
> Didnt work for me. I tried it with youtube and a video on joox.net. Theres a bunch of junk in my temp but nothing that looks like a vid file or labeled youtube or anything.

it suppose to be called something like "FlashC1yT4U" and you should be able to open it with vlc.

---

### Post by Uruz2012 on 2009-03-24
I second youtube-dl. It's simple and easy to use.

---

### Post by Agent.Logic_ on 2009-03-24
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006) is a good option. This add-on works with virtually any video embedded website. It also has the ability to convert flash videos into other formats.

---

### Post by NCLI on 2009-05-19
Just take it from the /tmp directory, way easier.

---

### Post by Mornedhel on 2009-05-19
miro ?

It's in the repositories.

---

### Post by ssdt on 2009-05-19
There is a lot of firefox plugins to do that job.

---

### Post by cvp on 2010-01-06
> **imT said:**
> go to "/tmp" after the flash video is loaded and you'll get it there :)
:shock:
I realize this is a bit less than two years old, but this deserves any bump it gets. I just tested this out, and my jaw just hit the floor. This is so stupidly useful. I can't believe I went through the pain of add-ons and sketchy third-party apps to do this in Winblows.

---

### Post by ThePinkWitch on 2010-01-06
I use Video Download Helper a firefox addon 
[http://www.downloadhelper.net/](http://www.downloadhelper.net/) :)

---

