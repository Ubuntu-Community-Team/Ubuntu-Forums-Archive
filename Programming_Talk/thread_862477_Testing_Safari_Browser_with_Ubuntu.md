---
title: "Testing Safari Browser with Ubuntu"
date: 2008-07-17
forum: Programming Talk
---

### Post by SuperMike on 2008-07-17
I am a PHP Web Developer. I'd really like to have a way to test my sites with Safari in a virtual machine or somehow natively inside Ubuntu, and know that it's going to validate tests for Mac users who visit my websites.

What's the cheapest solution for pulling that off? I could purchase a used Mac Mini on eBay, of course, but I'd like to see if there are options that are cheaper.

---

### Post by Sinkingships7 on 2008-07-17
> **SuperMike said:**
> I am a PHP Web Developer. I'd really like to have a way to test my sites with Safari in a virtual machine or somehow natively inside Ubuntu, and know that it's going to validate tests for Mac users who visit my websites.

What's the cheapest solution for pulling that off? I could purchase a used Mac Mini on eBay, of course, but I'd like to see if there are options that are cheaper.


Assuming that the web engine wouldn't be different, Apple has a native version of Safari for Windows. So if you can create a virtual machine with windows and install Safari on it, wouldn't that do the trick?

---

### Post by themusicwave on 2008-07-17
I remember hearing/reading somewhere that Sarfari and Konquerer use the same rendering engine.

If that is the case, perhaps you could just install Konquerer from the repos and test with it.

You'll have to research it some to be sure it is true of course, sorry if I am passing on lies...

---

### Post by sq377 on 2008-07-17
The next release of gnome will have "Webkit" as the default rendering engine, which is what safari uses.  You can test this now by installing midori.  It's not perfect, flash and other media applets are absent, but general page rendering should be very similar.  This build is a little bit old, so if you want the latest, go to [http://webkit.org/](http://webkit.org/) grab the latest nightly build and make it yourself.  There is a test browser in the source that you can use.

Your other option is to use the windows version of safari in wine
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11235](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11235)


Good luck.

---

### Post by -grubby on 2008-07-17
> **themusicwave said:**
> I remember hearing/reading somewhere that Sarfari and Konquerer use the same rendering engine.

If that is the case, perhaps you could just install Konquerer from the repos and test with it.

You'll have to research it some to be sure it is true of course, sorry if I am passing on lies...

Konqueror uses KHTML, Safari uses Webkit. I believe that Apple got Webkit by making changes to KHTML, and releasing them back upstream. I know that Konqueror and Safari's rendering engines are at least *similar*

---

### Post by SuperMike on 2008-07-17
> **Sinkingships7 said:**
> Assuming that the web engine wouldn't be different, Apple has a native version of Safari for Windows. So if you can create a virtual machine with windows and install Safari on it, wouldn't that do the trick?

Say, I didn't even know that Safari ships for Windows. What a relief. That will save me a good chunk of change. While I'm on the topic, I just installed Ubuntu 8.04 on a brand new Acer Extensa laptop and then found the trick (from the [bug list reported here]("http://ubuntuforums.org/showthread.php?t=773851")) to get VirtualBox going. So with that going, I need to get IE6, IE7, Opera, and Safari installed into a particular version of Windows. I have a license and media for Windows 2000 Server, and the laptop came with an OEM license for Vista (media is downloadable, I think), but I wanted to know what you recommend. I mean, I *hate* Vista. If I could get a super cheap copy of XP somewhere, and you know of a place, please let me know. I also don't know if IE7 plays nicely inside XP. Then, I guess I need to get IE6 and IE7 in separate VMs because I hear that as a web developer, if you put both on the same system, IE6 will fail to render conditional comments or have other kinds of bugs. If you know a way around that as well, let me know.

---

### Post by LaRoza on 2008-07-17
[http://browsershots.org/](http://browsershots.org/)

---

### Post by Sinkingships7 on 2008-07-17
> **LaRoza said:**
> [http://browsershots.org/](http://browsershots.org/)

Well, that looks like a handy little site...

---

### Post by SuperMike on 2008-07-20
For a limited time, Micro$oft is enabling a free trial install of Winblows Server 2008 that lasts up to 240 days. This comes with Internet Exploder 7. Just visit their site, look for Windows Server 2008, and click Try It Out. So, here's what I did:

* Use VirtualBox on Ubuntu 8.04 (used Sun version because apt-get install VirtualBox is a no-starter right now) and then downloaded the ISO image from Microsoft for Windows Server 2008. From there, for my browser testing, I get IE7, and then I can also install Opera 9.5 and Apple Safari for Windows. The Safari testing on Windows will work just fine on any Mac -- it's the same engine.

* For IE6 testing, I just installed IES4Linux. I don't do IE5.5 testing anymore because it's so old.

* I can install FF2 for the root account profile (so as not to mess up my .mozilla settings folder for my regular profile).

So, what this gives me on a single Ubuntu 8.04 laptop is a test environment for FF2, FF3, the latest Opera, the latest Safari (Mac testing), IE6, and IE7. And I did it all 100% free without breaking any laws.

Now, it would be great for me to figure out how to hook the W2K8S so that it lasts indefinitely, such as clock games, but this will do nicely for now. And when it jams up after 240 days, I can try to reinstall it again to see if it gives me another 240 days.

---

### Post by -grubby on 2008-07-20
> **LaRoza said:**
> [http://browsershots.org/](http://browsershots.org/)

Holy wow. I got 44 different browser screenshots of my website in less than 5 minutes!

---

