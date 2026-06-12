---
title: "Need help with flash! URGENT! SYSTEM MELTDOWN!"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by shleyman on 2008-06-24
ok, now i have your attention, youtube is just not working, ive tried everything and it still says i am lacking the required plugins.
i NEED to find a noob friendly topic that goes through step by step how to overcome this problem so is anone willing to show me or spare the time to help me?

---

### Post by Methuselah on 2008-06-24
I always recommend people install Macromedia flash from Add/Remove rather than messing with the tar.gz from adobe's site. You might have to enable the medibuntu repositories first.

---

### Post by webofunni on 2008-06-24
You need to download the "libflashplayer.so" from adobe and put that in firefox plugins directory. 

[http://plugindoc.mozdev.org/linux.html#Flash](http://plugindoc.mozdev.org/linux.html#Flash)

Run following command in command prompt and get back with the result if you are not sure about the FF plugin directory location. 

```
whereis firefox
```

  Usually FF plugin directory will be in "/usr/lib/firefox-ver/plugins"

---

### Post by t0p on 2008-06-24
Use Synaptic to install **flashplugin-nonfree**

---

### Post by Yuki_Nagato on 2008-06-24
I actually recommend that people install the tar.gz straight from Adobe.

_[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")_

You will notice there is a link to installation instructions on the same page.  I have never had any trouble with Linux Flash using this method.

---

### Post by shleyman on 2008-06-24
oive progressed further now i have a white box where the video...
at least its not telling me i need the plugins

---

### Post by shleyman on 2008-06-24
```
----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/ash/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `./libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/ash/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete.


Perform another installation? (y/n): 

```

this is the result i get from going through the abdobe instructions

---

### Post by Methuselah on 2008-06-24
That installation directory doesn't look right to me and you usually have to sudo the script. Then again, I rarely use this installation method.

---

### Post by RomeReactor on 2008-06-24
Hi. What version of Ubuntu do you have?

As Methuselah and t0p said, the easiest way to install Flash is to install it from the repositories. You might have it already installed, but you need to make sure that Gnash isn't installed also, as it conflicts with Flash (Gnash is an open source implementation of Flash, but it still has a ways to go before it reaches the same level of compatibility). To make sure Gnash isn't installed, close Firefox, go to Synaptic (System->Administration->Synaptic) and search for **gnash**; a few results should show up. The one you don't want installed is **mozilla-plugin-gnash**, so if it *is* installed, mark it for removal and press 'Apply'. Open Firefox again, go to YouTube and see if it works now.

---

### Post by webofunni on 2008-06-24
try 

```

#sudo apt-get remove gnash
#sudo apt-get autoremove
#sudo apt-get install flashplugin-nonfree
```

---

