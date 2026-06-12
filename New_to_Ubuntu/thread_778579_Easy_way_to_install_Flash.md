---
title: "Easy way to install Flash"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Kymeia on 2008-05-02
I tried installing Flash using Synaptic (the non free addons package with fonts etc too) and it seemed to install OK but Flash is still not working on sites like BBC. The problem is the version on the Adobe site seems to require manual installation inputting code and stuff and there's no installer as such.

---

### Post by encompass on 2008-05-02
The adobe flash player is not THAT hard to install...
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)
And the instructions are here...
[http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)
and I think the location they ask for is /usr/lib/mozilla
Good luck!

---

### Post by iSplicer on 2008-05-02
Even easier way; In a terminal:

sudo apt-get install flashplugin-nonfree

---

### Post by gandaran on 2008-05-02
> **Kymeia said:**
> I tried installing Flash using Synaptic (the non free addons package with fonts etc too) and it seemed to install OK but Flash is still not working on sites like BBC. The problem is the version on the Adobe site seems to require manual installation inputting code and stuff and there's no installer as such.

the flashplugin-nonfree in synaptic is exactly the same as the one in the adobe web site.
now which flash packages did you install in synaptic? there are three to choose from!

---

### Post by iSplicer on 2008-05-02
> **gandaran said:**
> the flashplugin-nonfree in synaptic is exactly the same as the one in the adobe web site.


But synaptic is easier =)

---

### Post by linux phreak on 2008-05-02
I got it via the "Add/Remove" and is running without a problem till date.

---

### Post by piratesmack on 2008-05-02
> **Kymeia said:**
> I tried installing Flash using Synaptic (the non free addons package with fonts etc too) and it seemed to install OK but Flash is still not working on sites like BBC. The problem is the version on the Adobe site seems to require manual installation inputting code and stuff and there's no installer as such.

I usually just install the ubuntu-restricted-extras package from synaptic

---

### Post by Sef on 2008-05-02
> I tried installing Flash using Synaptic (the non free addons package with fonts etc too) and it seemed to install OK but Flash is still not working on sites like BBC

There was a problem with one of the flash versions in the Gutsy repo.

---

### Post by spiderbatdad on 2008-05-02
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://www.instructables.com/id/S3IUTBCFEEMAMSW/](http://www.instructables.com/id/S3IUTBCFEEMAMSW/)

[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

[http://screencasts.ubuntu.com/Installing_Flash_on_Ubuntu_i386](http://screencasts.ubuntu.com/Installing_Flash_on_Ubuntu_i386)

---

### Post by t0p on 2008-05-02
If you really can't(???) install **flashplayer-nonfree** through Synaptic, then getting it direct from Adobe's web site is your best bet.  The fact that there's no wizard to hold your hand during install may be intimidating, but using the terminal isn't anything to worry about.  

Very likely, all you'll need to do is use Archive Manager to unzip the files you've downloaded, then change directory so you're inside the downloaded folder, and run a script that does the actual installation.  If you have a look in the folder you downloaded, you'll probably find a README file.  Open it and read it.  It'll tell you what to do.

Tell you what though, I find it curious that you couldn't get flashplayer-nonfree through Synaptic.  Why exactly couldn't you get it?  What kind of error message was displayed?

In case you want to try Synaptic again: the app you want is called **flashplayer-nonfree**.  There's also a Free flash player available through Synaptic, called **gnash**.  The plugin for Firefox is **mozilla-plugin-gnash**.  The standalone Free flash player is called **gnash**.

---

### Post by Victormd on 2008-05-02
I guess the easy way to install is simply by installing the restricted extras... this will install everything you'd need, from mp3 codecs, java, flash, to fonts...

> sudo apt-get install ubuntu-restricted-extras
where ubuntu can be replaced by kubuntu or xubuntu...

---

### Post by piratesmack on 2008-05-02
If you can't get flash to install from the repos, I'll write a quick howto:
-Open Applications>Accessories>Terminal
-Paste and run the following commands one line at a time
```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xzvf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo su
./flashplayer-installer

```
-Close any open browsers when it asks and press "enter"
-When it asks you where you want to install it, type:
```

/usr/lib/mozilla

```

---

### Post by Kymeia on 2008-05-02
What I installed through Synaptic was the Ubuntu-restricted-extras which says it has the Flash plugin. However when I go to sites like BBC.com/news I still get a message saying I need to install the Flash plugin - that's the problem.

---

### Post by encompass on 2008-05-02
I played some audio that was in flash there and it all worked just fine for me... what browser are you using?
Also...
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507)
that will check your latest version and see if it at least 9 or even the same as the linux version listed at the end of the page.
Hope this helps.

---

### Post by kansasnoob on 2008-05-02
This may or may not apply, but when I upgraded two of my computers from Gutsy to Hardy I failed to upgrade my Medibuntu repository which resulted in erratic flash and java performance.

---

### Post by gandaran on 2008-05-02
> **Kymeia said:**
> What I installed through Synaptic was the Ubuntu-restricted-extras which says it has the Flash plugin. However when I go to sites like BBC.com/news I still get a message saying I need to install the Flash plugin - that's the problem.

what about youtube? can you see the videos?

maybe I can help you, but I need more information, what version of ubuntu you using gutsy 7.10 or hardy 8.04? system 32-bit or 64-bit?

---

### Post by c4v3m4n on 2008-05-02
I use 64 bit and just install Automatix2.  Works great for me!

---

### Post by Kymeia on 2008-05-03
It's working now - don't know why when it wasn't before - maybe it just needed a reboot or something.

---

