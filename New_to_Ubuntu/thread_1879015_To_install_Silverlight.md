---
title: "To install Silverlight"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by arno48 on 2011-11-10
[FONT=Verdana][SIZE=2][I]In order to view videos, Rugby Word Cup site  requires to install Microsoft Silverlight. Can I do with Ubuntu  11.10? Does it work?
[/I][/SIZE][/FONT]

---

### Post by westie457 on 2011-11-10
Hello. Silverlight probably will not work. Suggest you try Moonlight which is in the repositories.

---

### Post by An Sanct on 2011-11-10
Its called "[MoonLight]("http://samiux.blogspot.com/2011/05/howto-moonlight-on-ubuntu-1104.html")", but IMHO SilverLight is saying goodbye ...

(The link contains a how-to for 11.10)

---

### Post by Rodney9 on 2011-11-10
Go to this site [http://go-mono.com/moonlight/](http://go-mono.com/moonlight/)

download 32 or 64 bit version let it install

Then when you go to a site with a silverlight video, moonlight will ask to install the correct codec.

Just tried it on Lubuntu 11.10 64bit and it worked.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Rodney

---

### Post by beew on 2011-11-10
Should boycott sites that use silverlight. 

The Moonlight Firefox plugin is not compaible with firefox 4 and above so you have to install an add on to stop compatibility check, can't remember what it is called, hope someone else who knows will tell you.

Moonlight doesn't work for many silverlight sites from what I read.

---

### Post by oldsoundguy on 2011-11-10
And "Moonlight" is always a build or two behind.  Silverlight is as good as gone as IE usage has OFFICIALLY fallen to below 50% (actually been below 40% on some reports for some period of time!)

---

### Post by Frogs Hair on 2011-11-10
If this is the site it works with the Moonlight version at the posted at the links above .[http://www.rugbyworldcup.com/](http://www.rugbyworldcup.com/)

---

### Post by Rodney9 on 2011-11-10
> **Frogs Hair said:**
> If this is the site it works with the Moonlight version at the posted at the links above .[http://www.rugbyworldcup.com/](http://www.rugbyworldcup.com/)

Curious, fails for me.

Rodney

---

### Post by beew on 2011-11-10
To install the moonlight addon for FF you need to install the add-on compatibility reporter first (it is a Firefox add-on itself, install it the usual way, go to Tools > Add-ons abd search for it then install) It will disable compatibility check as moonlight is not compatible with FF4 and higher.

The bad news is it doesn't work (It seems that Froghair's screenshot is just the home screen of the site, not the actual video)

Having tested that I have uninstalled moonlight.

---

### Post by Frogs Hair on 2011-11-10
> **Rodney9 said:**
> Curious, fails for me.

Rodney

:confused:

I'm using nightly alpha 10 and had to use the compatible reporter to get Moonlight installed .  Here are the plug-ins in use .

---

### Post by inobe on 2011-11-10
i wouldn't, but if you must, it's best to use a platform that silverlight was created for, which would be mac or windows.

if watching such content is that important rather.

---

### Post by Frogs Hair on 2011-11-10
> **beew said:**
> To install the moonlight addon for FF you need to install the add-on compatibility reporter first (it is a Firefox add-on itself, install it the usual way, go to Tools > Add-ons abd search for it then install) It will disable compatibility check as moonlight is not compatible with FF4 and higher.

The bad news is it doesn't work (It seems that Froghair's screenshot is just the home screen of the site, not the actual video)

Having tested that I have uninstalled moonlight.

You are correct , it will work for the home page media but not the video .:(

---

### Post by SeijiSensei on 2011-11-11
Most media sites use Silverlight because it enables them to enforce proprietary "digital rights management" schemes which Moonlight cannot support.  If the video doesn't play, you'll need to use native Silverlight on Windows or OS X.

---

### Post by An Sanct on 2011-11-11
Another hint, use VirtualBox with (an official version of) Windows XP or, download the Microsoft's official [browser emulator images]("http://noscope.com/journal/2010/12/use-microsofts-official-internet-explorer-virtual-pc-testing-images-in-virtualbox-on-osx") (note, that they are huge downloads, that cannot take interrupts in download!)

---

### Post by arno48 on 2011-11-11
> **westie457 said:**
> Hello. Silverlight probably will not work. Suggest you try Moonlight which is in the repositories.
Thank you.
Ubuntu Software Center does not offer Moonlight. Where do you suggest to download Moonlight from?

---

### Post by Frogs Hair on 2011-11-11
It is posted on this thread . Two of us have tested Moonlight on the official world cup web site and Moonlight will work with the media on the main page but not with the video . As suggested in an earlier post it may be digital rights management issue or Moonlight is outdated .

---

### Post by Frogs Hair on 2011-11-11
I tried the site posted below and had no problems with the live Flash streams but the archived videos did not play . When you click on the events a drop down menu with links will appear indicating the plug-in needed .

[http://www.vipbox.tv/sports/rugby.html](http://www.vipbox.tv/sports/rugby.html)

---

### Post by Redsandro on 2012-01-04
> **arno48 said:**
> Ubuntu Software Center does not offer Moonlight. 


Yes, why is that? The package used to be supported. Google is still paved with instructions to download [moonlight-plugin-mozilla]("https://launchpad.net/ubuntu/oneiric/amd64/moonlight-plugin-mozilla"). But it has been removed since 11.04.

---

