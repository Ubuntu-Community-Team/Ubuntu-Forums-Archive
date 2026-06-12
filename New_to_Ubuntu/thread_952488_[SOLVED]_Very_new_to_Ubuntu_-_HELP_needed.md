---
title: "[SOLVED] Very new to Ubuntu - HELP needed"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Martin40 on 2008-10-19
I have just recently installed Ubuntu OS on my pc, after using windows for eons.

So far my experience with Ubuntu has been a bit of a nightmare to be honest.

My problems are

When I go to apply the latest updates an error message comes up and will not allow me to apply these changes.

When I enter a audio cd in to my drive no sound comes out, yet I have checked all the pcs sound levels and they are set to an audible level.

I can not access flash content either.

Any assistance on these issues would be very much appreciated. 

Before you ask I´m using Mozilla Firefox Browser.

Martin

---

### Post by jamaas on 2008-10-19
What do you mean apply latest updates?  What error message are you getting ?

Jim

---

### Post by eragon100 on 2008-10-19
> **Martin40 said:**
> I have just recently installed Ubuntu OS on my pc, after using windows for eons.

So far my experience with Ubuntu has been a bit of a nightmare to be honest.

My problems are

When I go to apply the latest updates an error message comes up and will not allow me to apply these changes.

When I enter a audio cd in to my drive no sound comes out, yet I have checked all the pcs sound levels and they are set to an audible level.

I can not access flash content either.

Any assistance on these issues would be very much appreciated. 

Before you ask I´m using Mozilla Firefox Browser.

Martin

to solve the flash problem (and likely the sound as well) go to applications -> add/remove, select show "All available applications, and then search for and install "Ubuntu restricted extras". This will install flash and all kinds of video / audio codecs (mp3, wav etc.) Flash will work after you restart firefox, you might have to restart the computer for the audio codecs (cd in this case) to get working, not sure if that's necessary.

---

### Post by Martin40 on 2008-10-19
Jim,

To explain more in the bottom right hand side on my tool bar I have a red arrow pointing downwards, once I click it then the update manager comes up.

I then press install - but the following message comes up.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I´m slightly confused, any help would be appreciated.

---

### Post by laurielegit on 2008-10-19
go into terminal (in the accessories tool bar) and type in ```
sudo dpkg --configure -a
```

you will need to enter your password for this. :)

---

### Post by jamaas on 2008-10-19
I'm no tech wizzard but usually these messages give good info, do you know how to open a terminal window?  If so, open one and type exactly what it says 

You will likely need super used authorization so use sudo as

$ sudo 'dpkg --configure -a'

minus the single quotes and it will likely check things over and fix it up, or at worst, tell you where the problem is.  Make sense?  If you need more help with terminal window let me know.

J


> **Martin40 said:**
> Jim,

To explain more in the bottom right hand side on my tool bar I have a red arrow pointing downwards, once I click it then the update manager comes up.

I then press install - but the following message comes up.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I´m slightly confused, any help would be appreciated.

---

### Post by eragon100 on 2008-10-19
> **Martin40 said:**
> Jim,

To explain more in the bottom right hand side on my tool bar I have a red arrow pointing downwards, once I click it then the update manager comes up.

I then press install - but the following message comes up.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I´m slightly confused, any help would be appreciated.

Do what it says:

- open a terminal: applications -> accesoires -> terminal:

type sudo dpkg --configure -a and hit enter.

type in your password (no asterisks will show up on the screen) and press enter. close the terminal and it should work now.

Then, go to add/remove to install ubuntu restricted extras to solve flash and audio problems and you should be all set :wink:

---

### Post by Martin40 on 2008-10-19
> **eragon100 said:**
> to solve the flash problem (and likely the sound as well) go to applications -> add/remove, select show "All available applications, and then search for and install "Ubuntu restricted extras". This will install flash and all kinds of video / audio codecs (mp3, wav etc.) Flash will work after you restart firefox, you might have to restart the computer for the audio codecs (cd in this case) to get working, not sure if that's necessary.

I followed your instruction but when I tried to apply the change this error message came up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is becoming very frustrating.

---

### Post by billgoldberg on 2008-10-19
> **Martin40 said:**
> I have just recently installed Ubuntu OS on my pc, after using windows for eons.

So far my experience with Ubuntu has been a bit of a nightmare to be honest.

My problems are

When I go to apply the latest updates an error message comes up and will not allow me to apply these changes.

When I enter a audio cd in to my drive no sound comes out, yet I have checked all the pcs sound levels and they are set to an audible level.

I can not access flash content either.

Any assistance on these issues would be very much appreciated. 

Before you ask I´m using Mozilla Firefox Browser.

Martin

Problem one.

in a terminal (applications -> accessories)

You will get the command you will need to enter in the terminal. Just put "sudo" in front of it.

2. Go to system -> preferences -> sound. Change everything to ALSA.

3. Go to this website: 

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

and download the .deb package.
Double click to install. Restart firefox.

---

### Post by billgoldberg on 2008-10-19
> **Martin40 said:**
> I followed your instruction but when I tried to apply the change this error message came up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is becoming very frustrating.

the command in the terminal is

```
sudo dpkg --configure -a
```

---

### Post by eragon100 on 2008-10-19
> **Martin40 said:**
> I followed your instruction but when I tried to apply the change this error message came up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is becoming very frustrating.

Do it in order!:

1: sudo dpkg --configure -a

2: go to add/remove and install ubuntu restricted extras.

This is also the order in which I posted it.

---

### Post by Martin40 on 2008-10-19
Many thanks to all of you that assisted me. Not a nightmare now.

---

### Post by eragon100 on 2008-10-19
> **Martin40 said:**
> Many thanks to all of you that assisted me. Not a nightmare now.

You're welcome. Please go to "thread tools" and mark the thread as "solved" :)

---

