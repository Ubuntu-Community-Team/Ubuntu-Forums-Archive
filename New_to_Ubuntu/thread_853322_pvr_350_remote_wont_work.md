---
title: "pvr 350 remote wont work"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by jayg1169 on 2008-07-08
hi,
having serious trouble getting this remote to work.
i can see all the remote buttons through ```
irw
``` but nothing on myth.
any help would be great as the little hair i have is disappearing fast

---

### Post by jayg1169 on 2008-07-09
Bump

---

### Post by wolfen69 on 2008-07-09
you need to go into the mythtv settings and make sure you have selected the correct remote. is it the media center edition remote? i believe there are 3 or 4 choices that are similar.

---

### Post by jayg1169 on 2008-07-09
front or backend?

---

### Post by OffAxis on 2008-07-09
what does 
```
irsend LIST "" ""
```

give you?
(it should list your remote from the lircd.conf file)

---

### Post by jayg1169 on 2008-07-09
```
jay@jay-htpc:~$ irsend LIST "" ""
irsend: Hauppauge
irsend: hauppauge_pvr
irsend: Hauppauge_350
irsend: Hauppauge_WinTV_Nexus-S
irsend: HVR-1100

```

---

### Post by OffAxis on 2008-07-09
I forget (and I'm away from my machine right now):
does irw return just a button's code to stdout or does it list remote:code?

---

### Post by OffAxis on 2008-07-09
Your .lircrc file may not be mapped to the appropriate remote as defined by lircd.conf.

Incidentally, since you're only using the 350's remote you may want to disable the other ones. I think you can do that in mythbuntu's remote control configuration utility, otherwise you can comment them (or their links) out in the /etc/lirc/lircd.conf file.

Check out your ~/.lircrc file and make sure that the button configuration lines match those of irw and your lircd.conf.

If they don't you've got two options; edit it by hand or run
```
mythbuntu-lircrc-generator
```
(you'll need the mythbuntu-lirc-generator package installed for that function)

---

### Post by jayg1169 on 2008-07-09
my input from```
irw

``````
jay@jay-htpc:~$ irw
0000000000001794 00 Up Hauppauge_350
0000000000001794 01 Up Hauppauge_350
0000000000001795 00 Down Hauppauge_350
0000000000001795 01 Down Hauppauge_350
0000000000001797 00 Right Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 01 Vol+ Hauppauge_350
0000000000001791 00 Vol- Hauppauge_350
0000000000001791 01 Vol- Hauppauge_350
00000000000017a0 00 Ch+ Hauppauge_350
00000000000017a1 00 Ch- Hauppauge_350
00000000000017a1 01 Ch- Hauppauge_350

```

---

### Post by jayg1169 on 2008-07-09
sorry forgot to tell ya im not actually running mythbuntu! got 8.04 with mythtv running from synaptic

---

### Post by OffAxis on 2008-07-09
okay, so it does list the Hauppauge_350.
So you'll want to check the .lircrc (which is actually a link to ~/.lirc/mythtv - at least in mythbuntu) and make sure that the buttons are mapped to those keys and haven't been over-written by one of the other remotes. I think they can peacefully co-exist but there may be some crossover; best to limit the available options.
If that all checks out then move on to the the channel-change script and the mythtv setting that points to it (it's in the backend I think, but don't hold me to that).
There used to be a script **change-channel-lirc.pl** or **change-channel-lirc.sh** that would handle the channel changing, but you had to specify the remote (from lircd.conf) within the script.
I'm not sure how it's currently done (the change channel setting in myth should point to a script or a function that does it) but I'd start with that setting and make sure it's getting the correct remote.

---

### Post by jayg1169 on 2008-07-09
offaxis
i know your trying to help but i really dont understand what you wrote! real new to mythtv having real trouble with it!

---

### Post by OffAxis on 2008-07-09
ah. I'll elaborate.
First, if this is a clean or relatively clean install the easiest thing is to do an install with mythbuntu; it was developed to streamline the installation of mythtv and automates a lot of things (remote control setup, for instance). [http://mythbuntu.org](http://mythbuntu.org)

back to the problem at hand:
lirc is a standalone program, mythtv is a standalone program.

lirc can perform two main functions (assuming you have the hardware); receive infrared signals or send infrared signals.

The lirc program consists of these parts:
the main program
a hardware.conf file
a lircd.conf file
a .lircrc file (it's a configuration file as well)

The hardware.conf file is in /etc/lirc/hardware.conf
The lircd.conf is in /etc/lirc/lircd.conf
The .lircrc file is a hidden file in your home directory. It's a user specific configuration file, so whatever user your using to run mythtv is the home folder you'll want to have this in. To make things slightly more confusing, this file has been moved around and reconfigured a few times in recent years; it used to be here ~/.lircrc then it was ~/.mythtv/lircrc and now (in mythbuntu) it's here ~/.lirc/mythtv. To keep packages from breaking links have been placed at these various points so that they end up pointing to the same configuration file.

The hardware.conf file specifies the hardware setup.
The lircd.conf file maps the infrared codes to specific remote controls and puts them in human readable terms (Vol+ for instance)
The lircrc file provides the bridge between the lirc program and other programs; it maps the remote control keys to other programs.
So if you want to increase the volume in mythtv you press a button on your remote, it is received by your computer's infrared sensor, translated to Vol+ by lirc (using your remote's specifications in lircd.conf) and then the lircrc file is read and the Vol+ button is run for mythtv.

As standalone programs the exchange between the two is a little clunky. If you're using a Set Top Box for your TV signal, then you probably want to use the other main function of lirc; sending infrared signals. In this case, the hardware you use is called an IR Blaster or IR Transmitter. mythtv has no way of changing the channel if this is the case, so it runs a script (change-channel-lirc.sh) that runs the irsend command. In this script you have to specify the name of the remote control that you're using (Hauppauge_350). Like I said, a little clunky.

So, when you're troubleshooting lirc/mythtv problems you want to get your lirc configured (**irw **and **irsend LIST "" ""** will give you good feedback), then mess with the .lircrc file (you can use a number of different media players for testing, it doesn't have to be myth), -and if you're using an external set top box- the channel change script and the call from mythtv to the script.

---

