---
title: "Unable to install Cadence"
date: 2017-07-27
forum: New to Ubuntu
---

### Post by yungguanyu on 2017-07-27
Good Morning Friends

As a disclaimer, I am still pretty green in the Linux world, having only used it full time for a couple of months. I played around with KXStudio and was hoping to be able to use [Cadence]("http://kxstudio.linuxaudio.org/Applications:Cadence") on my Xubuntu install to manage JACK and audio routing.

However, I am at a loss of how to install it. I can't find it in the software store, nor can I find it using a package manager. I followed the instructions  to add the KXStudio repositories, but I still can't seem to find Cadence anywhere. I also downloaded the compiled binaries on the Cadence page, but the readme has no instructions on how to install Cadence.

Any help is greatly appreciated :KS:KS

---

### Post by Frogs Hair on 2017-07-27
Hello:

I enabled the repository from the .deb on the page below and ran the update manager and see all KXStudio applications & plugins in the repository ,  Cadance is whole set of apps and plugings. KXstudio repository includes an entire desktop environment. **_Edit:_** 
> The KXStudio repositories support all Debian versions since Jessie and Ubuntu 14.04 or above.


[http://kxstudio.linuxaudio.org/Repositories#Debian](http://kxstudio.linuxaudio.org/Repositories#Debian)

Cadence did show up after running the software updater which should be done after adding a repository.

---

### Post by Bucky Ball on 2017-07-28
Welcome. Depending on what you want to do, might be simpler to use [Patchage]("http://drobilla.net/software/patchage"). You are having problems with the Jack 'Connections' dialogue? That should do the basic things, but might need a bit of time to understand how it works (and once you do you probably won't need Cadence or Patchage unless you have a VERY complex set up with a lot of real and virtual devices which are easier to work with as individual visual entities in a GUI). 

Patchage IS in the official repositories and is probably lighter than Cadence. 

Finally getting serious with Linux audio myself at the moment and have avoided the KXStudio repo. Not needed in my instance and quite possibly in yours. As this is an AV machine I'm working on, don't want anything I don't need. ;)

PS: Are you using qjackctl for launching jack? If not, you probably should be. If it's anything like Ubuntu Studio, KXStudio may give you a LOT of jack related stuff which, frankly, is not required. If you find you do need something 'jack', you can install it later. 

Essentially, qjackctl is about all you should need to start connecting stuff and get playing.

(PS: Depending on what you're doing, you may also need 'aj2midid' for connecting USB MIDI devices and things, which I think is installed by default in KX but NOT in Ubuntu or Xubuntu. You'll find it in the repos. Simpy install. This should be launched after jack launches and I can give you a command to do that so when you launch qjackctl it also launches aj2midid at same time, if helpful.)

---

### Post by yungguanyu on 2017-07-28
Thanks for the replies.

Bucky, Cadence probably is overkill but it worked nicely with everything. I'm trying to run all my sound through a USB interface (Behringer UM2), for everyday use, as well as recording guitar (via Guitarix). This is "plug and play" with Cadence on a live boot of KX, but i can't get it to work on Xubuntu with just qjackctl. When i run it, it just kills all running audio and nothing else happens.

I am sure there is something simple im missing? Despite bulk googling i can't work it out.

---

### Post by Bucky Ball on 2017-07-28
Are you sure you have Guitarix set to use Jack and not ALSA? Make sure you start jack first, then start the other apps you're going to use. If you start jack after the app, yea, it could lock up. 

BTW, I meant to say a2jmidid. KXstudio, I think, installs that by default. In Xubuntu, you'll need to install it and you should have it installed, just in case. After you've launched jack, launch a terminal and, from memory, run

```
a2jmidid -jack
```
a2jmidid should appear in your jack> 'Connections' window . Do you have a device you are looking for in there?

---

