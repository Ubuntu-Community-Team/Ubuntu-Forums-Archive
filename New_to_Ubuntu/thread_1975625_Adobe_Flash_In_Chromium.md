---
title: "Adobe Flash In Chromium"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by WacoOne on 2012-05-07
I'm working with Lubuntu. How can I get Adobe Flash for it?

---

### Post by PhantomTurtle on 2012-05-07
You either open up synaptic or the software center and search for flash player or just flash and install the browser plug-in. Also I believe that the Restricted (or was it multiverse, try both) repositories need to be enabled in Synaptic.

---

### Post by marko on 2012-05-07
I have had more problems on this than I would have expected..  Got 12.04 running on my kids VERY underpowered laptop. Very excited that it works!

But he wants to go on a Flash site and I have not found documentation that explains how this is supposed to work.

I keep seeing things that help Firefox, that help install Flash..

But fact is: Flash is already installed according to apt and synaptic.  I can't run the addon that helps correct issues because that depends on Firefox. So Flash is in, but sites in Chrome still complain about a missing plug-in.  If Firefox is as light as Chrome, I may just install that..  we'll see..

---

### Post by PhantomTurtle on 2012-05-08
If you want something very lightweight, try Midori, Flash should work in it.

---

### Post by daemoncycler on 2012-05-08
Hi, I am a Chrome user - don't really have much experience with Firefox.  Kept getting "plug-in: shockwave flashplayer crashed" with chromium so I installed Chrome as I would have in windows, by just downloading & installing it.  Seems to be working fine - no more flash crash.

Guess my question is, am I supposed to be installing new applications thru Synaptic?  Just installed Lubuntu today & that Synaptic Package Manager is a bit daunting. Actually did a search in Synaptic for Chrome without much luck.

thanks

---

### Post by IWantFroyo on 2012-05-09
> **daemoncycler said:**
> Hi, I am a Chrome user - don't really have much experience with Firefox.  Kept getting "plug-in: shockwave flashplayer crashed" with chromium so I installed Chrome as I would have in windows, by just downloading & installing it.  Seems to be working fine - no more flash crash.

Guess my question is, am I supposed to be installing new applications thru Synaptic?  Just installed Lubuntu today & that Synaptic Package Manager is a bit daunting. Actually did a search in Synaptic for Chrome without much luck.

thanks

The version of Chrome in the repositories is chromium-browser. Also, there should be a plugin somewhere in the web store that manages flash for you.

---

### Post by daemoncycler on 2012-05-09
OK, I'll go try to find the web store - guess that's not Synaptic?  Will check the Lubuntu FAQ for web store.

thanks

---

### Post by speed32219 on 2012-05-09
I am not sure chromium supports flash, but it is built in the new chrome.  With firefox I just did sudo apt-get install flashplugin-nonfree.

---

### Post by daemoncycler on 2012-05-09
I have Lubuntu 11.10 installed.  Looks like Lubuntu Software Center is installed by default in 12.04. Have to issue the following command to install it in 11.10.


sudo apt-add-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install lubuntu-software-center 

So Linux is like a hands-on kind of OS.  Little afraid I'm gonna jack things up issuing commands directly into the kernel (whatever it's called?).

I really like Google Chrome, but then I don't have any experience with Firefox.

thanks again

---

### Post by oregonbob on 2012-05-09
Well here is a twist. I did a fresh install of 12.04. I must have installed Adobe flash and it made all flesh on youtube blue. So I removed Adobe flash. Now youtube doesn't work at all in Chrome. This is depressing. Google is slowly getting out of anything linux. First Picasa, now Chrome.

I installed "restricted extras" and that fixed nothing. Still no youtube in Chrome.

Edit: OK, now I reinstalled Adobe Flash and also Google Toolbox extension and "Youtube Options" extension and mysteriously IT IS WORKING AGAIN! Ubuntu is becoming an install circus. You install it then work round the clock for several days getting the blue people to go away.

---

### Post by potwash on 2012-05-09
Hi All. 
I had exactly the same issue with flash when upgraded to 12.04. If you put chrome://plugins in chromium address bar. Click details to right hand side of page. I copied the flash version and googled it. I followed instructions to copy and paste a previous version to /usr/lib/flashplugin-installer (i think the last bit is correct) and then restarted Chrome and Youtube & BBC Iplayer worked. Im no guru and if someone has a better way I'll embrace it

---

### Post by WacoOne on 2012-05-09
Here's an update:

I downloaded Firefox through Ubuntu Software Center, but flash didn't work on it. So I did what Speed suggested and put in this into the terminal:

sudo apt-get install flashplugin-nonfree

Now flash works in Firefox, but not Chromium still. I can live with that, but is there something I can punch into the terminal that would allow it to work in Chromium as well?

---

### Post by WacoOne on 2012-05-09
I figured it out by following these directions:

[http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html](http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html)

---

