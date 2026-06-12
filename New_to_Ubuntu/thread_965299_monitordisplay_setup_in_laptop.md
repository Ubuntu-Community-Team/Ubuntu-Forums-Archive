---
title: "monitor/display setup in laptop"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by jpease on 2008-10-31
I connected my 2nd display to my laptop did the regular function key + f7 I can not get my display to show up.  Is there additional setup that I need to do?

Total newbie here......

---

### Post by jpease on 2008-10-31
shouldn't it recognize the display automatic?

---

### Post by ethoxyethaan on 2008-10-31
don't double post,

If you have installed the Restricted Extras to run your Nvidia Graphics card it should also have installed the Nvidia X server setting. (you can find this in system>admin>nvidia X settings.)
here you can configure your Second monitor. 

if you can't find it run this from the terminal:

gksudo /usr/bin/nvidia-settings

---

### Post by jpease on 2008-10-31
> **ethoxyethaan said:**
> don't double post,

sorry, I didn't know I double posted.

> **ethoxyethaan said:**
> If you have installed the Restricted Extras to run your Nvidia Graphics card it should also have installed the Nvidia X server setting. (you can find this in system>admin>nvidia X settings.
don't have it
> **ethoxyethaan said:**
> if you can't find it run this from the terminal:

gksudo /usr/bin/nvidia-settings
I didn't get any action out this.  I did get a password request, but that was it.

to be honest I don't even know how to check what kind video card I have.  How do you do that?

---

### Post by wgrant on 2008-10-31
Lots of laptops have Intel video cards, which have excellent multi-monitor support. Your first call for setting it up should always be System->Preferences->Screen Resolution. Only if that fails should one try the more obscure methods.

---

### Post by jpease on 2008-11-01
> **wgrant said:**
> Lots of laptops have Intel video cards, which have excellent multi-monitor support. Your first call for setting it up should always be System->Preferences->Screen Resolution. Only if that fails should one try the more obscure methods.
I have been there but I could not find anything related to adding second display.

Said that, I installed ubuntu on a old dell inspiron 7000.  It installed flawlessly and works perfect.  I tried the function + f7 keys and it worked perfect without going into sys>pref>screen res.

It makes me believe there is something wrong specific to the IBM t23 laptop function + f7 keys

---

