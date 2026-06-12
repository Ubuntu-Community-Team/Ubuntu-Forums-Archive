---
title: "Necessary Packages"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by leilton on 2012-01-27
Hi.   Have now, with help from Forums members, got rid of Windows, and installed Xubuntu 11.10.

Question is, what, if anything, do I need to install, apart from that which was on the DVD?

Keep reading, on Internet, about Unity, Compitz etc, but everything., with a few exceptions, appears to be working well.

Still a bit confused about what Desktop, if any I have (and why no Wallpaper), and do I really need a Launcher?

Sorry if pain, but want to get most of new system.

---

### Post by Megaptera on 2012-01-27
Hi,
Xubuntu is a "desktop environment" more detail here: [http://lifehacker.com/5762081/wtf-desktop-environments-gnome-kde-and-more-explained](http://lifehacker.com/5762081/wtf-desktop-environments-gnome-kde-and-more-explained)

If your system is running fine then no need to add stuff but if you go to Software Centre through the menu you can choose all sorts of compatible and safe apps to install with a couple of clicks [http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre](http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre) 
As I discovered early on though if you install apps with a captital "K" you might end up with a lot of Kubuntu added to your Xubuntu!

---

### Post by hhh on 2012-01-27
> **leilton said:**
> ... (and why no Wallpaper)... 
??? Open the Run dialog (Alt+F2 or "Run" in the Xfce Menu) and enter "xfce4-settings-manager" without quotes, then go to "Desktop". Can you set one from there?

---

### Post by Double.J on 2012-01-27
> **leilton said:**
> Hi.   Have now, with help from Forums members, got rid of Windows, and installed Xubuntu 11.10.

Question is, what, if anything, do I need to install, apart from that which was on the DVD?

Keep reading, on Internet, about Unity, Compitz etc, but everything., with a few exceptions, appears to be working well.

Still a bit confused about what Desktop, if any I have (and why no Wallpaper), and do I really need a Launcher?

Sorry if pain, but want to get most of new system.

Hi there, as to what you need... well not much really! Ubuntu and it's lightweight sisters Xu and Lu buntu come with most things you'd need.. the rest are optionals :)

A couple of recommendations that are very common to install:
[COLOR="Red"]wine[/COLOR] - this is a "compatibility layer" for windows apps - basically it lets some windows programs run on xubuntu. for a full list of what, check out[ wineHQ]("http://www.winehq.org/")

[COLOR="red"]Ubuntu Restricted Extras[/COLOR] - proprietary codecs for audio/video, MS fonts, and flash.

[COLOR="red"]Compizconfig Settings Manager[/COLOR] - enables several desktop effects (may not be recommended for hardware with limited graphics

Most of the rest is just preference - do you like chromium or firefox? abiword or libre office writer, that sort of thing.. most of the popular software now has user reviews in the software centre :)

All the best :)

---

### Post by wolfen69 on 2012-01-27
> **leilton said:**
> 

Question is, what, if anything, do I need to install, apart from that which was on the DVD?


If you need multimedia codecs, do:
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by leilton on 2012-01-28
> **wolfen69 said:**
> If you need multimedia codecs, do:
```
sudo apt-get install xubuntu-restricted-extras
```

Hi,

Thank you.

Found that in Synaptic, have loaded it?, and will have fun rest of day seeing what I have.

Thanks for help:P

---

### Post by leilton on 2012-01-28
> **Megaptera said:**
> Hi,
Xubuntu is a "desktop environment" more detail here: [http://lifehacker.com/5762081/wtf-desktop-environments-gnome-kde-and-more-explained](http://lifehacker.com/5762081/wtf-desktop-environments-gnome-kde-and-more-explained)

If your system is running fine then no need to add stuff but if you go to Software Centre through the menu you can choose all sorts of compatible and safe apps to install with a couple of clicks [http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre](http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre) 
As I discovered early on though if you install apps with a captital "K" you might end up with a lot of Kubuntu added to your Xubuntu!

Thanks much.

Good idea.  Seeing as it is b..........y cold here in Spain, will spend day going thru everthing I can find, no not downloading, just check what is on offer.

Love the System, dont know why did not do change before.:p

---

### Post by leilton on 2012-01-28
> **hhh said:**
> ??? Open the Run dialog (Alt+F2 or "Run" in the Xfce Menu) and enter "xfce4-settings-manager" without quotes, then go to "Desktop". Can you set one from there?

Thanks for that, more so for the info on the keys.

Yes knew about the desktop, but on my machine that has Ubuntu, I can select a number of different backgrounds, seem a bit limited with Xubuntu, but beggers cant be choosers.

:o

---

### Post by leilton on 2012-01-28
> **gnu/mirow said:**
> Hi there, as to what you need... well not much really! Ubuntu and it's lightweight sisters Xu and Lu buntu come with most things you'd need.. the rest are optionals :)

A couple of recommendations that are very common to install:
[COLOR=Red]wine[/COLOR] - this is a "compatibility layer" for windows apps - basically it lets some windows programs run on xubuntu. for a full list of what, check out[ wineHQ]("http://www.winehq.org/")

[COLOR=red]Ubuntu Restricted Extras[/COLOR] - proprietary codecs for audio/video, MS fonts, and flash.

[COLOR=red]Compizconfig Settings Manager[/COLOR] - enables several desktop effects (may not be recommended for hardware with limited graphics

Most of the rest is just preference - do you like chromium or firefox? abiword or libre office writer, that sort of thing.. most of the popular software now has user reviews in the software centre :)

All the best :)

Thank you.

Am amazed at the amount of support have received to my question.

Have all three of the items you quoted, so now know what I'll be doing for the next few days.

Whilst I am on the air, so to speak, can I ask, if you dont mind, do I need a security pro gramme, on Windows I had four?

Again my thanks

:D

---

### Post by Megaptera on 2012-01-28
> **leilton said:**
>  ... if you dont mind, do I need a security pro gramme, on Windows I had four?... :D

The short answer is "none" but have a read here for why, and what you might want to consider eg passwords etc.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by leilton on 2012-01-28
> **Megaptera said:**
> The short answer is "none" but have a read here for why, and what you might want to consider eg passwords etc.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Again my thanks to you.:D

---

### Post by Megaptera on 2012-01-28
You're welcome!!

---

### Post by hhh on 2012-01-28
> **leilton said:**
> Yes knew about the desktop, but on my machine that has Ubuntu, I can select a number of different backgrounds, seem a bit limited with Xubuntu, but beggers cant be choosers.
Gnome has more default wallpapers than Xfce, but you can use any image on your computer. Just click the plus button underneath the list of default wallpapers and navigate to an image.

---

