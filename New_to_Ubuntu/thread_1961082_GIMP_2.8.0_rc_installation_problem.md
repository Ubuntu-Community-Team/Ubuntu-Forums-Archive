---
title: "GIMP 2.8.0 rc installation problem"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by Virtuality314 on 2012-04-18
This is my first post so it might be in the wrong place.

I wanted to try out GIMP 2.8.0 rc so I downloaded it, extracted the contents and then followed the instructions in the INSTALL.txt file.

However, when I ran ./config in the terminal (as described) I got the message:
 'No package babl found' followed by lots of messages:
"Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix.

Alternatively, you may set the environment  variables BABL_CFLAGS and BABL_LIBS to avoid the need to call pkg-config. See the pkg-config man page for more details."

However, I have already installed both BABL and GEGL using by entering
'git clone git://git.gnome.org/babl' and
'git clone git://git.gnome.org/gegl' into the terminal

I don't understand the message from ./config as I haven't been using ubuntu that long.

I am using Ubuntu 11.10

Virtuality314

---

### Post by Toz on 2012-04-18
> **Virtuality314 said:**
> However, I have already installed both BABL and GEGL using by entering
'git clone git://git.gnome.org/babl' and
'git clone git://git.gnome.org/gegl' into the terminal

If these are the only commands that you ran, then all you did was clone the source (copy it) to your local drive. You still need to configure, build and install both of those packages. Information on building those packages should be found in the directories created to house the source.

EDIT: This PPA ([https://launchpad.net/~otto-kesselgulasch/+archive/gimp]("https://launchpad.net/~otto-kesselgulasch/+archive/gimp")) seems to have the gimp 2.8 release candidate (along with the required libs) available. It would be __much__ easier than trying to compile it yourself. (Note: I have not tried this PPA).

EDIT2: Here is a related link that might be of interest: [http://www.unixmen.com/install-gimp-2-8-rc1-in-ubuntu-12-04-precise-pangolin-via-ppa/]("http://www.unixmen.com/install-gimp-2-8-rc1-in-ubuntu-12-04-precise-pangolin-via-ppa/"). Note that the PPA seems to have both precise (12.04) and oneiric (11.10) packages available.

---

### Post by Virtuality314 on 2012-04-18
[COLOR=Black]Thank you for the surprisingly quick reply.

I didn't realise that I didn't actually install the packages.
I found this website: [http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html) (before I read your post) and it also tells me to add the ottokesselgulash repository.

Thanks,

Virtuality314
[/COLOR][COLOR=Black] [/COLOR]

---

### Post by Toz on 2012-04-18
And oh, sorry I didn't initially notice, but welcome to the forums.

---

### Post by alphacrucis2 on 2012-04-18
I recall following a step by step web guide for building gimp 2.7.5 which even I was able to follow successfully, although it was a bit tedious. I forgot to bookmark it and I can't now recall where I found it. Hopefully some kind soul will set up a ppa for us on final release of 2.8.

---

### Post by Virtuality314 on 2012-04-19
Marked thread as solved

---

