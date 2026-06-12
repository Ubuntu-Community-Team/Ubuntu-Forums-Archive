---
title: "Terminal; ctrl-alt-t"
date: 2011-08-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by douham on 2011-08-29
Hi, is there a new key combo to launch the terminal; Ctrl-Alt_T does not work.

I&#7743; also used to my os remembering the last status of num-lock (either on or off)

These are´nt major issues, just annoyances

---

### Post by godhika on 2011-08-29
You change atleast ctrl-alt-t as a terminal shortcut in ccsm under gnome compatibility.

---

### Post by lucazade on 2011-08-29
In unity-2d ctrl-alt-t works correctly, I use it often.
It looks like this shortcut is disabled in ccsm under key bindings (for unity-3d)

edit: godhika beated me :)

---

### Post by VinDSL on 2011-08-29
You need to go into:
[LIST]
[*]CCSM -> General -> Gnome Compatibility -> Commands
[*]Enable "Open a terminal"
[*]Then "Grab key combination"
[/LIST]

Aren't alphas fun?!?!?

edit: godhika beated me too   :D

---

### Post by coffeecat on 2011-08-29
Rhetorical question: why, oh why, oh why, did they disable ctrl-alt-T by default? When you boot into a new Oneiric install and are confronted by just wallpaper and a cursor (sounds like it's happened to others too by what I've read), it's the first thing you need! :p

---

### Post by VinDSL on 2011-08-29
> **coffeecat said:**
> Rhetorical question: why, oh why, oh why, did they disable ctrl-alt-T by default?
Beats me!

I *guess* they're trying to keep us on our ctrl-alt-Toes...  ;)

---

### Post by lucazade on 2011-08-29
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/820266](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/820266)

---

### Post by rbrick49 on 2011-08-29
ctrl-alt-t is no big deal except you have to do, files /usr/sshare/applications if you want it to work or recovery mode

---

### Post by VinDSL on 2011-08-30
> **rbrick49 said:**
> ctrl-alt-t is no big deal except you have to do, files /usr/sshare/applications if you want it to work or recovery mode
Huh?

---

### Post by jerrylamos on 2011-08-30
> **VinDSL said:**
> You need to go into:
[LIST]
[*]CCSM -> General -> Gnome Compatibility -> Commands
[*]Enable "Open a terminal"
[*]Then "Grab key combination"
[/LIST]

Aren't alphas fun?!?!?

edit: godhika beated me too   :D

Tried ccsm.  Got bug 832458:

ccsm crashed with KeyError in compizconfig.Plugin.ApplyStringExtensions (src/compizconfig.c:6780)(): '\xd0\t\x9b\n\x01' 

When ccsm does run, after crashing, doesn't display anything I can see like "Open a terminal" since all the choices are blank.

So I select Dash then open a terminl and save it on the launcher.  Kind of slow and unhandy but works.  Come to think of it, that's my general comment on Unity-3D.

Jerry

---

### Post by sgage on 2011-08-30
What's the matter with system settings/keyboard/shortcuts?

Works fine here.

---

### Post by VinDSL on 2011-08-31
> **jerrylamos said:**
> I select Dash then open a terminl and save it on the launcher.  Kind of slow and unhandy but works.  Come to think of it, that's my general comment on Unity-3D.
Heh!  I hear ya!

Oh, well, they're getting there.

I don't *think* they disabled Ctrl-Alt-T on purpose...  ;)

---

### Post by mc4man on 2011-08-31
> **VinDSL said:**
> 

I don't *think* they disabled Ctrl-Alt-T on purpose...  ;)
Maybe it's an oversight, (not enabling in gnomecompat) or just following the gnome3 default which is not to have 'Launch Terminal' set

If one was to open GS > SS > keyboard > launchers it's listed but not bound.
If set to Crtl+Alt+T in GS then it will then automatically be set in Unity > compiz  > gnomecompat if not already

---

### Post by CaptainMark on 2011-09-01
the ops other question about the num lock, its getting on my nerves, is everyone having this problem? i have my bios set to 'num lock state on' but ubuntu 11.10 overides this, natty doesnt, nor does any other distro on a live session

---

### Post by douham on 2011-09-01
> **CaptainMark said:**
> the ops other question about the num lock, its getting on my nerves, is everyone having this problem? i have my bios set to 'num lock state on' but ubuntu 11.10 overides this, natty doesnt, nor does any other distro on a live session

Thanks for reminding me about this CaptainMark. 
edit: I don´t have a user password with numbers, but I&#7743; just used to having num lock on all the time.

---

### Post by VinDSL on 2011-09-01
> **CaptainMark said:**
> the ops other question about the num lock, its getting on my nerves, is everyone having this problem? i have my bios set to 'num lock state on' but ubuntu 11.10 overides this, natty doesnt, nor does any other distro on a live session
Yes, I've been having this problem too!

I cannot tell you how many problems it has caused for me, when I'm coding.  Makes me want to smash my keyboard with a hammer.

Lubuntu (daily build) has the same problem.

I tried Xubuntu (daily build), and I think it had this problem too - can't remember.

I also tried Mandriva 2011 (final) aka “Hydrogen" the other night.  I *think* it worked in Mandriva, but I wouldn't swear to it.

Anyway, I have a feeling that this "Num Lock" problem is coming from upstream...

---

### Post by douham on 2011-09-01
> **CaptainMark said:**
> the ops other question about the num lock, its getting on my nerves, is everyone having this problem? i have my bios set to 'num lock state on' but ubuntu 11.10 overides this, natty doesnt, nor does any other distro on a live session

I only just noticed that Num Lock turns off each time I log out and then log back in. However it stays on when I resume from standby.

---

### Post by ratcheer on 2011-09-01
I also have the NumLock problem in Oneiric. Is there a bug open on this?
 
Tim

---

### Post by CaptainMark on 2011-09-02
i cant find anything on launchpad, we should make a bug report but which package would this be related to, i would guess it would be lightdm, because gdm used to be in charge of setting numlock on so i guess theyve overlooked it when coding lightdm, any thoughts?

---

### Post by mc4man on 2011-09-02
numlock - lightdm
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/835532](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/835532)

---

### Post by ratcheer on 2011-09-02
Thanks, mc4man. I have added my "me too". There are currently only the originator and I, so more of you need to go add to it.
 
Tim

---

### Post by CaptainMark on 2011-09-03
im in

---

### Post by Hakunka-Matata on 2011-09-04
Running on Stock 11.10 beta

> Linux 1110-b1 3.0.0-10-generic-pae #16-Ubuntu SMP Fri Sep 2 20:09:42 UTC 2011 i686 athlon i386 GNU/Linux

CTRL-ALT-T does not work to bring up Teminal:  What's the Shortcut now?

---

### Post by mc4man on 2011-09-04
In unity if you have compizconfig-settings-manager (ccsm) installed then open it up > gnome compatibility > commands & enable it there.
If you happen to have gnome-shell installed it can be set in System Settings > Keyboard > Launchers (if set in GS it will then automatically be enabled in ccsm > gnomecompat

Or it can be set to another binding if desired in System Settings > Keyboard > Shortcuts > Custom shortcuts

---

### Post by jerrylamos on 2011-09-04
I select "dash home" and type in ter which puts a terminal picture on the launcher.  

With right click you can "keep in launcher".  Even stays there on reboot.

If you already have a terminal you can right click on the launcher icon and open a "new terminal".

A bit clumsier and definitely slower than just Ctrl-Alt-t but it works.

Now the launcher isn't very big, eight plus "dash" and "trash" but in test mode I haven't often filled it up yet.  I do delete icons I don't use like Impress and Software Center and Ubuntu One.  

I use network copy (when its working on Oneiric) between my netbook, notebook, tower, and my wife's two Windoze.  She uses Windoze because she supports a couple websites that use proprietary $$$ software not available on linux.  Yet.  If ever.

Jerry

---

### Post by fjgaude on 2011-09-04
> **Hakunka-Matata said:**
> Running on Stock 11.10 beta



CTRL-ALT-T does not work to bring up Teminal:  What's the Shortcut now?

Just what the doctor ordered... thanks! Now we have the best of all worlds with the Dash, just enter a t, and the Terminal icon shows. You can drag it into the Launcher and then right-click Keep in launcher. Now Ctrl-Alt-t. Two ways.

---

### Post by fjgaude on 2011-09-04
> **mc4man said:**
> In unity if you have compizconfig-settings-manager (ccsm) installed then open it up > gnome compatibility > commands & enable it there.
If you happen to have gnome-shell installed it can be set in System Settings > Keyboard > Launchers (if set in GS it will then automatically be enabled in ccsm > gnomecompat

Or it can be set to another binding if desired in System Settings > Keyboard > Shortcuts > Custom shortcuts

Just what the doctor ordered... thanks! Now we have the best of all worlds with the Dash, just enter a t, and the Terminal icon shows. You can drag it into the Launcher and then right-click Keep in launcher. Now Ctrl-Alt-t. Two ways.

---

### Post by cariboo on 2011-09-04
Merged two threads on the same subject.

---

