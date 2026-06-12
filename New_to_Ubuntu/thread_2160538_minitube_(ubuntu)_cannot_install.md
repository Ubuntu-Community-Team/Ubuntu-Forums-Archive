---
title: "minitube (ubuntu) cannot install"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by leilton on 2013-07-07
Have tried now for three days to find a way to install minitube (ubuntu).

On each occasion get as far as giving my eamail address, only to be told I cannot use it.

Seems to be accepted here, and where ever it is required, so why does Ubuntu One refuse it?

Whilst at it, why am I asked for it anyway, it says no charge on Software centre, and it is recommened over the normal minitube (which by the way does not work in Ubuntu 12.04)?

---

### Post by howefield on 2013-07-07
I just installed version 2.1 to take a look.

Do you have an UbuntuOne account ?

---

### Post by BrunoLotse on 2013-07-07
Hi,here [http://www.noobslab.com/2013/07/minitube-21-available-for-ubuntu.html](http://www.noobslab.com/2013/07/minitube-21-available-for-ubuntu.html) you will find instructions how to install minitube. I did it and it works just fine.Cheers, Bruno

---

### Post by leilton on 2013-07-07
> **howefield said:**
> I just installed version 2.1 to take a look.

Do you have an UbuntuOne account ?

Hi,

Thanks, yes loaded when I installed.

See reply to BrunoLotse

Again thanks for your hrlp

---

### Post by leilton on 2013-07-07
> **BrunoLotse said:**
> Hi,here [http://www.noobslab.com/2013/07/minitube-21-available-for-ubuntu.html](http://www.noobslab.com/2013/07/minitube-21-available-for-ubuntu.html) you will find instructions how to install minitube. I did it and it works just fine.Cheers, Bruno

Hi,

Worked a treat.

Wish I´d known about this earlier, kept wondering why could not use my email just to get it.

Many thanks for help.

---

### Post by BrunoLotse on 2013-07-07
> **leilton said:**
> kept wondering why could not use my email just to get it.The Lord works in miraculous ways....  You're most welcome. Cheers, Bruno

---

### Post by mc4man on 2013-07-07
The ppa (or any current minitube ppa) is at best using the 2.0 version, irregardless of what the package name says, simply open minitube > help to see.
While it may not directly affect you the 2.0 version & so-called 2.1 version from the ppa is flawed in several ways.
So for general user info - 

1. - 2.0 is  broken on playback of VEVO videos - only fixed in 2.1
2.  The ppa version depends on phonon-backend-gstreamer only. Some effort was applied to get the Ubuntu packager to configure to allow either the gstreamer or vlc backends to work, the ppa has not done so.
(the vlc backend is generally superior, less possible issues. The minitube author has decided that for "minitube-ubuntu" to depend on the vlc backend

minitube-ubuntu is only available for intial install  thru software-center, to install you must have a ubuntu sso (single sign on ) account. You create one if enabling ubuntuone or setting up a launchpad account.

screens show some of installing minitube-ubuntu here thru software-center
screen1 - package in S-c, click buy
screen 2  - sign in page,  If one already has an Ubuntuone account or launchpad account then  sign in using account email & account password, Not your email password. Otherwise set up a new account
screen 3 - install starting
screen 4 - minitube-ubuntu version window

Now while minitube-ubuntu deps on phonon-backend-vlc it will use phonon-backend-gstreamer if installed. Sometimes the gstreamer backend is ok, sometimes not. To use the vlc backend the gstreamer backend must not be installed

---

