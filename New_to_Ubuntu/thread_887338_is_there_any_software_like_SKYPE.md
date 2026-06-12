---
title: "is there any software like SKYPE?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ellankavi on 2008-08-12
I'd like to know if there's any software for video chat that can work with skype.

---

### Post by Riffer on 2008-08-12
There is Skype, it's in the repos.

Also for the latest version go here.

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

### Post by bikeboy on 2008-08-12
Give Skype a go :D

I don't have any experience installing it but there is a version for linux and it supposedly supports video.

---

### Post by Crafty Kisses on 2008-08-12
> **bikeboy said:**
> Give Skype a go :D

I don't have any experience installing it but there is a version for linux and it supposedly supports video.

I'm pretty sure Skype supports video, I just wish Pidgin would support video already. :)

---

### Post by hyper_ch on 2008-08-12
add the medibuntu repos and get skype from there.

---

### Post by Xavieran on 2008-08-12
As Riffer said, skype is available.

I have it working here at home, and it works perfectly; including video.

The only issue I've had is that it doesn't support sending SMS's to mobile phones yet, apparently it's still a beta.

Of course, I simply connect my bluetooth enabled phone with Wammu, and can send messages through the computer that way...

---

### Post by kostkon on 2008-08-12
Also, you can add the official repository and get an update every time there is a new version:
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

---

### Post by ellankavi on 2008-08-12
what's a repository?

---

### Post by Kobalt on 2008-08-12
[Here]("https://help.ubuntu.com/8.04/add-applications/C/extra-repositories.html") you go.

---

### Post by sir_skiner on 2008-08-12
is there any working action handler for skype 2.0?

---

### Post by billgoldberg on 2008-08-12
> **sir_skiner said:**
> is there any working action handler for skype 2.0?

A little suggestion from me here.

Add the medibuntu repo.

Just copy/paste this command to "applications -> accessories -> terminal".

It will add the needed repository, skype and some other stuff like dvd support and some other codecs.
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype
```

You'll be prompted for you password, just type it and press enter. You will not see what you type.

After the command is done running, it will be installed and available in the applications menu.

The skype version installed will be the latest available for linux.

--

Other software.

Ekiga is installed by default as a VOIP client on you computer. I don't know if it supports video. Check it out.

---

### Post by sir_skiner on 2008-08-12
think that repo is ofline.

i'll be trying later...

---

### Post by northern lights on 2008-08-12
> **billgoldberg said:**
> ```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 skype
```
+1

I'd just recommend 'mozilla-mplayer' over 'totem-mozilla' - plays video web content much smoother for me.

Any confirmations?

Bill, what do you think?

> **sir_skiner said:**
> think that repo is ofline.
it's up.

---

### Post by sir_skiner on 2008-08-12
thanks, but it doesn't help - no action-handler included in package...

---

### Post by _Kesler_ on 2008-08-20
forget the repo, it does not have a video supported version.

download skype from [http://skype.com/download/skype/linux/](http://skype.com/download/skype/linux/)

for 32bit install from xterm:
sudo dpkg -i /skype-debian_2.0.0.72-1_i386.deb

for 64 bit install from xterm:
sudo dpkg -i --force-architecture /skype-debian_2.0.0.72-1_i386.deb

Download getlibs from [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
Double click downloaded file to install it.

run "getlibs /usr/bin/skype" from terminal

for both 32bit and x64 (1 and/or 2 may not be necessary)
1) open volume control and click file/change -- choose device/opt 1  (edit/preferences -- check all)

2)from xterm type alsamixer change Digital to "Digital" (where it currently says Analog above Digital)

enjoy skype with video!

---

### Post by sir_skiner on 2008-08-22
thanks, but you don't understand what i need.

it's not about video in skype - it's not a problem.

i need some kind of url-handler to open skype links or skype buttons coded in websites body in skype v. 2.0.

take a look here:
[http://heartbeat.skype.com/2008/08/payments_were_not_working_for.html](http://heartbeat.skype.com/2008/08/payments_were_not_working_for.html)

what you can see is that:

> Payments were not working for a short period on 12th of August.

By [IMG]http://mystatus.skype.com/smallicon/joosep_k[/IMG] Joosep on August 12, 2008.

clicking [IMG]http://mystatus.skype.com/smallicon/joosep_k[/IMG] should open skype chat window with Joosep. but it doesn't. same thing with skype public chats

---

