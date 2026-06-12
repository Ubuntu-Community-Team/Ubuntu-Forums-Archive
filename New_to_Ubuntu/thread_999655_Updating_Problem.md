---
title: "Updating Problem"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-12-02
I'm running Hardy and have started getting the following message during updates.

Not all updates can be installed

Run a partial upgrade, to install as many updates as possible

This can be caused by:
	A previous update which didn't complete
	Problems with some of the installed software
	Unofficial software packages not provided by Ubuntu
	Normal changes of a pre-release version of Ubuntu

After I've run the partial update, it reports that these are the packages causing problems

libbabl-0.0-0
libgegl-0.0-0
libpurple0
pidgin-data

I know pidgin is a chat program and as it's something I never use, I uninstalled it through Synaptic. There was more Pidgin entries on the list before I did that but the last one remains, and I have no idea what the others are. Can anyone please advise?

---

### Post by kansasnoob on 2008-12-02
Let's first try:

```
sudo apt-get -f install
```

To resolve dependencies.

You may get some feedback. remember to preface the suggested 'fix" with sudo.

---

### Post by Kevbert on 2008-12-02
The first two files are graphics library files. The other two are pidgin files.
Try running the following commands in terminal:
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by kansasnoob on 2008-12-02
You should also check Software Sources (in System > Administration).

Make sure proposed and backports are "unticked" under updates and make sure it's not trying to find sources from a CD!

---

### Post by MaxVK on 2008-12-02
There have been a number of similar threads to this, with the same problems (One of them was my own!), and there has yet to be a foolproof answer to this problem.

My own problem was with three other files, but there was no cure as such, I just kept trying to update and finally it worked when there were several other updates as well.

With this in mind, my only advice, as someone who suffered exactly the same error, is to wait and keep trying - eventually it should work (I think my three files took about 4 days before they worked).

Max

---

### Post by Cuttysark on 2008-12-08
Sorry for taking a while to post guys, the flu bug got me. I tried the advice you gave but alas, no joy, and now I get another entry in the no update list, brasero. Maybe it will be simply down to waiting it out.

---

### Post by Cuttysark on 2008-12-15
It's been a few days now and I still have this problem. It hasn't affected anything I've been doing, other than having to acknowledge it every time I switch on. Now however, it is causing a problem. I just Rockboxed my Sansa and I'd like to try some Ogg Vorbis on it. I went to install a convertor but it keeps telling me I already have an installer open. 

I've already tried sudo killall dpkg, sudo killall apt-get, sudo killall synaptic, sudo dpkg --configure -a and sudo apt-get install -f which I got from an earlier post I made about a botch install of a program, and they did the trick that time, but not this time unfortunately.

Can anyone advise me please?

---

### Post by Cuttysark on 2008-12-25
Sorry for laboring this one guys but I'm getting a little worried now. The list of problem files is now two, libbabl-0.0-0 and libgegl-0.0-0 but I have no idea what they are. If it was a program I could uninstall then I would do that. The thing is, it offers a partial update, but that isn't happening. I look at the list of proposed updates, security updates at that, and I approve the partial, but once it's done and I run it again, the same proposed security updates are being offered, so it doesn't seem to be doing any updating?

---

