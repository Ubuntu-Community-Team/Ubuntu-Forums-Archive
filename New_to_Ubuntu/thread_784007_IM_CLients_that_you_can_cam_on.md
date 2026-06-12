---
title: "IM CLients that you can cam on"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by k3lt01 on 2008-05-06
Hi everyone.

I use pidgin, and sometimes skype for friends who have skype but nothing else,to communicate with friends overseas. Unfortunately Pidgin (as far as I am aware) doesn't have video chat capabilties which I kinda need, so I need to find an IM client that allows video chat. I know skype does but my friend is reluctant to download and install it and considering I am not adverse to trying new things I will, so I am asking is there an IM client that will allow me to video chat with a friend on Yahoo that I can install on Ubuntu.

Thanks in advance

---

### Post by pro003 on 2008-05-06
pidgin has many plug-ins available through synaptic and those ones build in itself... am not sure is there video option but you can try to find out...

---

### Post by joselin on 2008-05-06
> **pro003 said:**
> pidgin has many plug-ins available through synaptic and those ones build in itself... am not sure is there video option but you can try to find out...


As far as I know pidgin hasn't video option. 

For video I use skype.

Regards

---

### Post by pro003 on 2008-05-06
then Skype it is...:popcorn:

---

### Post by glennric on 2008-05-06
You could try Ekiga, although I don't know if that can communicate with yahoo either.

---

### Post by k3lt01 on 2008-05-06
Thanks for the replies so far.

Skype is not an option atm as my friend does not have it. I'm willing to play around with my machine as I have a spare machine to play with, my friend hasn't got that luxury.

I'll keep looking into it, and will check out the pidgin plug-ins to see what they do and also Ekiga to se what it can do.

---

### Post by SunnyRabbiera on 2008-05-06
I thought kopete has a feature like this too...

---

### Post by frodon on 2008-05-06
Ekiga, skype, kopete, amsn, the best for me being skype despites his limited pulseaudio support

---

### Post by skymera on 2008-05-06
Pidgin is very good, i use it for all my IM needs.
But unfortunately it doesn't support webcams yet. Not sure if they have plans.

I used to use aMSN, it has several plugins, a nice theme.
But it ran very sluggish with compiz, used a lot of memory, 150-200MB RAM.
the only way i could get it to run better is to raise its CPU priority.

So you may want to try it, may work better for you.

---

### Post by aktiwers on 2008-05-06
This will soon have video/audio
[http://code.google.com/p/galaxium/](http://code.google.com/p/galaxium/)

To install: (I copy/pasted this from another post here on UbuntuForums)
> Open up your sources list and add the appropriate repository

```
gksudo gedit /etc/apt/sources.list
```

For Gutsy:


```
deb [ppa.launchpad.net/paulburton89/ubuntu]("http://ppa.launchpad.net/paulburton89/ubuntu") [[launchpad.net]]("http://www.stumbleupon.com/url/ppa.launchpad.net/paulburton89/ubuntu")  gutsy main
deb-src [ppa.launchpad.net/paulburton89/ubuntu]("http://ppa.launchpad.net/paulburton89/ubuntu") [[launchpad.net]]("http://www.stumbleupon.com/url/ppa.launchpad.net/paulburton89/ubuntu")  gutsy main
```

For Hardy:

```
deb [ppa.launchpad.net/paulburton89/ubuntu]("http://ppa.launchpad.net/paulburton89/ubuntu") [[launchpad.net]]("http://www.stumbleupon.com/url/ppa.launchpad.net/paulburton89/ubuntu")  hardy main
deb-src [ppa.launchpad.net/paulburton89/ubuntu]("http://ppa.launchpad.net/paulburton89/ubuntu") [[launchpad.net]]("http://www.stumbleupon.com/url/ppa.launchpad.net/paulburton89/ubuntu")  hardy main
```

then update and install:

```

sudo apt-get update
sudo apt-get install galaxium
```

---

### Post by k3lt01 on 2008-05-07
Thanks everyone.

I have installed Kopete and have done a dummy run to see if it works. Will try again tonight probably.

Thanks for the link for galaxium, will have a fiddle with that in a few days.

---

### Post by spiderbatdad on 2008-05-07
For video with kopete, you will need to install jasper.[http://www.ece.uvic.ca/~mdadams/jasper/#download](http://www.ece.uvic.ca/~mdadams/jasper/#download)

Download the current version. Extract it. cd into the directory, then run:
```
sudo apt-get install build-essential
./configure
make
sudo make install
```

I included build-essential because you will need it to make the package. It is not necessary to ever install again. If you have already installed it, ignore that command.


After that is done, kopete will work with video.

---

### Post by k3lt01 on 2008-05-07
Jasper is in the Repos, so all you need to do is selct it and Hardy does the rest.

---

