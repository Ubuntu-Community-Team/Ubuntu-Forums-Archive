---
title: "compiz upgrade issue"
date: 2011-07-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-07-19
latest 0.9.5.0-0ubuntu1 upgrade wants to install a bunch of kde packages on gnome system

bug #812762

---

### Post by VinDSL on 2011-07-19
That would set off "red flags" for me.

Obviously, something would be amiss, in my situation.

Are you asking for "our" permission to click the "Apply" button?!?!?

If so, I give that idea two thumbs down...  ;)

Okay... missed that on the first reading:  bug #812762

Looks like we're in concordance!

---

### Post by dino99 on 2011-07-19
hey i'm only reporting because of your nice conky settings :) :) :)

---

### Post by VinDSL on 2011-07-19
> **dino99 said:**
> hey i'm only reporting because of your nice conky settings :) :) :)
LoL!  :D

---

### Post by jppr on 2011-07-19
Just did latest upgrades, there is now new Compiz, Unity and Xorg and system run fine now :popcorn:

---

### Post by dino99 on 2011-07-19
cant install unity (4.2.0-0ubuntu5) as it depends on libunity-misc4 >=0.2.1
but only have 0.2-0ubuntu1 into the repo actually.

---

### Post by jppr on 2011-07-19
> **dino99 said:**
> cant install unity (4.2.0-0ubuntu5) as it depends on libunity-misc4 >=0.2.1
but only have 0.2-0ubuntu1 into the repo actually.

  Comes your updates mainserver? i have and i don´t have any problems update system.

---

### Post by dino99 on 2011-07-19
yes i use main server, which version of the above unity package dependency have you ?

note that unity have been removed due to compiz upgrading issue, and now i have that dependency issue.

---

### Post by Bowmore on 2011-07-19
The oneriric repos has libunity-misc4 version 4.0.2-0ubuntu1.

---

### Post by dino99 on 2011-07-19
yeah thats why unity fails to install (#6 above)

#812810

---

### Post by sgage on 2011-07-19
I just did the full bunch of updates (compiz, unity, xorg, etc.) and everything seems to be fine. No KDE packages installed or missed dependencies or anything like that.

---

### Post by Bowmore on 2011-07-19
As far as I can see there has never been a libunity-misc4 version 0.2-0ubuntu1 in the repos. The first libunity-misc4 to be released was 4.0.2-0ubuntu1 a month ago, also acc to my apt log from a natty upgrade.

Here the Oneiric releases
[https://launchpad.net/ubuntu/oneiric/+source/libunity-misc](https://launchpad.net/ubuntu/oneiric/+source/libunity-misc)

Is it a missing 4. in front of the version or a corrupt apt data base? 

But I guess you see that 0.2-0ubuntu1 version in synaptic :confused:

---

### Post by ratcheer on 2011-07-19
> **jppr said:**
> Just did latest upgrades, there is now new Compiz, Unity and Xorg and system run fine now :popcorn:

Really? Mine cannot display the desktop, now. Just a few rectangular patches of it.

Tim

---

### Post by dino99 on 2011-07-19
> **Bowmore said:**
> As far as I can see there has never been a libunity-misc4 version 0.2-0ubuntu1 in the repos. The first libunity-misc4 to be released was 4.0.2-0ubuntu1 a month ago, also acc to my apt log from a natty upgrade.

Here the Oneiric releases
[https://launchpad.net/ubuntu/oneiric/+source/libunity-misc](https://launchpad.net/ubuntu/oneiric/+source/libunity-misc)

Is it a missing 4. in front of the version or a corrupt apt data base? 

But I guess you see that 0.2-0ubuntu1 version in synaptic :confused:


of course there is 4 ahead (watch unity dependency about libunity-misc4 into synaptic, then you will understand :))

---

### Post by Bowmore on 2011-07-19
> **dino99 said:**
> of course there is 4 ahead (watch unity dependency about libunity-misc4 into synaptic, then you will understand :))Nope, I don't see your point. I says (>=0.2.1) which is ok. You wrote
> cant install unity (4.2.0-0ubuntu5) as it depends on libunity-misc4 >=0.2.1 but only have **0.2-0ubuntu1** into the repo actually.but meant libunity-misc4 **4.**0.2-0ubuntu1? If so, then there is something else that struggles.

---

### Post by dino99 on 2011-07-19
better explanation:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/812810/comments/2](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/812810/comments/2)

---

### Post by Bowmore on 2011-07-19
Good news that apt-get made it!

Strange thing is that libunity-misc4 is versioned 4.x.y while libunity-misc0 is versioned 0.x.y so there has never existed a released version 0.x nor 0.x.y for libunity-misc4 to my knowledge.

Sebastien refers to nattys version 0.2.1 which is for libunity-misc0. libunity-misc4 is not part of natty. The (>=0.2.1) dependency is probably just a left over when the source libunity-misc was upgraded and reversioned for oneiric.

So still a mystery how you got a libunity-misc4 version 0.2 but also why apt-get succeeded to install.

---

### Post by VinDSL on 2011-07-20
Oh, my!

I've been dreading this update cycle, but...

Now, you've convinced me to try it - guaranteed breakage, yes?!?!?  Or, not!

The suspense is killing me! Hrm...

Okay!  So it is written, so it is done.  :D

Wish me luck!

```

The following packages have been kept back:
  gstreamer0.10-plugins-bad x11-common
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  compiz-plugins-main compiz-plugins-main-default compizconfig-backend-gconf
  compizconfig-settings-manager friendly-recovery gir1.2-gtk-2.0
  gnome-icon-theme gnome-orca gnome-session gnome-session-bin
  gnome-session-common gnome-settings-daemon gnome-terminal
  gnome-terminal-data gtk2-engines-pixbuf gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  kerneloops-daemon libcompizconfig0 libdecoration0 libegl1-mesa
  libegl1-mesa-drivers libgail-common libgail18 libgbm1 libgl1-mesa-dri
  libgl1-mesa-dri-experimental libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgwibber-gtk2 libgwibber2
  libopenvg1-mesa libplymouth2 libunity-core-4.0-4 plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text python-compizconfig
  python-ubuntuone-storageprotocol ubuntu-system-service unattended-upgrades
  unity unity-common unity-services update-manager update-manager-core
  update-notifier update-notifier-common xorg xserver-xorg
  xserver-xorg-input-all xserver-xorg-video-all
65 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 18.3 MB of archives.
After this operation, 565 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Hopefully, I'll be back in a few...

---

### Post by mc4man on 2011-07-20
I've seen some rather poor behavior since the compiz/uniy upgrades on 2 installs though that doesn't mean a whole lot on O in it's current state (normally if I see stuff on separate installs I  think it's probably valid.

The most obvious is losing window decoration on certain pop up type windows, also over time degraded performance.
Opening certain qt4 app windows seems to accelerate the degrade (opening vlc's playlist and tools > pref's in particular

Might have to do a fresh install tomorrow  after only 2 days
screen show some examples - 1st. in synaptic, 2nd the file deletion confirmation window, 3rd vlc pref's

---

### Post by VinDSL on 2011-07-20
> **mc4man said:**
> I've seen some rather poor behavior since the compiz/uniy upgrades on 2 installs [...]

Might have to do a fresh install tomorrow  after only 2 days [...]
Yep! My UbuOO install is dead in the water now.

Desktop comes up, sans any icons, et cetera.  Can't go anywhere, can't do anything useful.

None of the usual remedies work.

Oh, well, I was overdue for a fresh install anyway...  ;)

---

### Post by ratcheer on 2011-07-20
Mine is no worse than it was, yesterday. But no better, either.

The last time I checked, I could still use it in Unuty2D.

Tim

---

### Post by VinDSL on 2011-07-21
> **VinDSL said:**
> Yep! My UbuOO install is dead in the water now.

Desktop comes up, sans any icons, et cetera.  Can't go anywhere, can't do anything useful.

None of the usual remedies work.

Oh, well, I was overdue for a fresh install anyway...  ;)
w00t!  Back from the dead...  :D

I was just about to do a fresh install - had the Live CD/USB plugged into the port - when I decided to do one last update.

I didn't see anything in the updates that looked like it would patch my install, but it did.

Oneiric lives to fight another day!  LoL!

No packages are being held back either...

---

### Post by ratcheer on 2011-07-21
I updated this morning. No held updates. I can still use Unity2D but not regular Unity. I got a new fglrx driver, yesterday, so it should work with the new Xorg and compiz.

Tim

---

### Post by ratcheer on 2011-07-21
> **ratcheer said:**
> I updated this morning. No held updates. I can still use Unity2D but not regular Unity. I got a new fglrx driver, yesterday, so it should work with the new Xorg and compiz.

Tim

More updates this evening. I am finally able to get a good, working Unity (3D) desktop, again. But after a few minutes, fglrx-amdcccle crashed. I submitted a bug report. My system continued working normally.

Tim

---

