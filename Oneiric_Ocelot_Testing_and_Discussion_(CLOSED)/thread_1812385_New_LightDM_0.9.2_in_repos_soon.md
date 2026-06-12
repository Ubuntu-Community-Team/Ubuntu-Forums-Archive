---
title: "New LightDM 0.9.2 in repos soon"
date: 2011-07-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-26
The new version of LightDM has arrived.
It is in Launchpad now, the status is new, so it is not uploaded into repos yet, but may of course be manually downloaded already.

I installed these packages with dpkg
(lightdm-greeter-example-gtk and liblightdm-gobject-0-0 must be uninstalled first):
- lightdm
- lightdm-gtk-greeter
- liblightdm-gobject-1-0

Here
[https://launchpad.net/ubuntu/oneiric/+source/lightdm/0.9.2-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/lightdm/0.9.2-0ubuntu1)

For example background settings have changed.
LightDM now uses (by default) the path /usr/share/backgrounds/warty-final-ubuntu.png
So if you copy any png image with the same name there, it is automatically picked up by the greeter.

---

### Post by Harry33 on 2011-07-26
This is in repos right now.
Just rememeber to install all these three (gnome):
-lightdm
-liblightdm-gobject-1-0
-lighdm-gtk-greeter

and to uninstall old lightdm packages, like
-liblightdm-gobject-0-0
-lightdm-greeter-example-gtk

---

### Post by bash on 2011-07-26
With this update, unity-greeter was also updated since the theme format changed and quite a few file locations were moved around. If you still want to play with the unity-greeter test mode, the new location is:

```
/usr/sbin/unity-greeter --test-mode
```

Also if you want to keep unity-greeter as your default you have to change some config entries in **/etc/lightdm/lightdm.conf** as the format has changed. Unless you changed other things in the config, all you really need now to run unity-greeter as default is:

```
[SeatDefaults]
greeter-session=unity-greeter
```

If you still have **greeter-theme=unity** in there, remove it.

---

### Post by MacUntu on 2011-07-26
My installation now no longer starts X, but the update was too extensive to pinpoint it on lightdm yet, so watch out if you are using Oneiric on your productive systems (which you shouldn't, let me tell you :D).

---

### Post by mc4man on 2011-07-26
lightdm upgraded here (thru synaptic), but didn't install 
lightdm-gtk-greeter
liblightdm-gobject-1-0
So then a reboot would fail (after battery check

Installing those and removing the 2 old ones resolved

---

### Post by MacUntu on 2011-07-26
Ditto, lightdm-gtk-greeter was missing.

---

### Post by mc4man on 2011-07-26
maybe this wasn't the fault of synaptic, maybe it was, doesn't really matter in this case, future iso's will be correct

Have noticed that every once and a while synaptic is unable to install/upgrade something properly

One ex. would be a case where Pkg A depends on B, depends on C
Marking A fails because synaptic won't install B, if marking B it fails because won't install C
If marking in the dep order then all is well, C-B-A

I believe whenever these oddities have occurred that reloading the sources in synaptic itself have resolved
(So have tried to get in the habit of doing that, but forget because it's only needed occasionally

---

### Post by MacUntu on 2011-07-27
I don't use Synaptic, but maybe this is just a packaging issue? I can't quite follow why lightdm only recommends <lightdm-greeter> - what use does it have without a greeter?

---

### Post by Harry33 on 2011-07-27
> **mc4man said:**
> maybe this wasn't the fault of synaptic, maybe it was, doesn't really matter in this case, future iso's will be correct

Have noticed that every once and a while synaptic is unable to install/upgrade something properly

One ex. would be a case where Pkg A depends on B, depends on C
Marking A fails because synaptic won't install B, if marking B it fails because won't install C
If marking in the dep order then all is well, C-B-A

I believe whenever these oddities have occurred that reloading the sources in synaptic itself have resolved
(So have tried to get in the habit of doing that, but forget because it's only needed occasionally

No it was not Synaptic.
That is because lightdm does not have correct dependencies.
Lighdm-gtk-greeter and liblightdm-gobject-1-0 must be installed manually, they are in the repos.

Some issues are fixed in the latest update (0.9.2-0ubuntu3).
The old greeter is removed now.

> lightdm (0.9.2-0ubuntu3) oneiric; urgency=low
  * Fix lightdm to conflict liblightdm-gobject-0-0 and liblightdm-qt-0-0,
    so that old greeters are removed on upgrade
    - update debian/control
 -- Chris Coulson <email address hidden>   Tue, 26 Jul 2011 23:26:49 +0100

---

### Post by mc4man on 2011-07-27
> No it was not Synaptic
Definitely not, though as mentioned have seen it miss once and a while on some things

even with the new lightdm, no greeter is installed, I gather recommends don't apply to upgrades.

---

### Post by Harry33 on 2011-07-27
> **mc4man said:**
> Definitely not, though as mentioned have seen it miss once and a while on some things

even with the new lightdm, no greeter is installed, I gather recommends don't apply to upgrades.

Do you have this checked?
Preferences - General - Marking Changes (Consider recommended packages as dependencies)

---

### Post by EgoGratis on 2011-07-27
I tried first new Unity greeter and i liked it but then after a while i could not login any more. So i will not test it anymore like this but i would like to know, when it is expected to become default in OO.

---

### Post by dino99 on 2011-07-27
> **EgoGratis said:**
> I tried first new Unity greeter and i liked it but then after a while i could not login any more. So i will not test it anymore like this but i would like to know, when it is expected to become default in OO.

it is already

---

### Post by EgoGratis on 2011-07-27
Yes LightDM is defoult but not jet the greeter? This is was i was wondering about (The Greeter).

---

### Post by dino99 on 2011-07-27
need to report about that missing dependency to get it.

---

### Post by mc4man on 2011-07-27
> **Harry33 said:**
> Do you have this checked?
Preferences - General - Marking Changes (Consider recommended packages as dependencies)

Yeah - it would  like you mentioned 1st. post  -  when the old greeter was installed, then synaptic would not install the recommend. 
With todays upgrade of lightdm if _no greeter is installed_ then the upgrade will install lightdm-gtk-greeter

(with the new lightdm - if the old one was installed then it's removed, but the new one is not installed

---

### Post by seeker5528 on 2011-07-27
> **bash said:**
> Also if you want to keep unity-greeter as your default you have to change some config entries in **/etc/lightdm/lightdm.conf** as the format has changed. Unless you changed other things in the config, all you really need now to run unity-greeter as default is:

```
[SeatDefaults]
greeter-session=unity-greeter
```

Apparently if you purge lightdm and install it, no lightdm.conf is created so you have to create it, then add the lines.

Later, Seeker

---

### Post by Harry33 on 2011-07-27
> **mc4man said:**
> Yeah - it would  like you mentioned 1st. post  -  when the old greeter was installed, then synaptic would not install the recommend. 
With todays upgrade of lightdm if _no greeter is installed_ then the upgrade will install lightdm-gtk-greeter

(with the new lightdm - if the old one was installed then it's removed, but the new one is not installed

The dependency is now fixed in the version (0.9.2-0ubuntu4).
This is now in the repos.

> lightdm (0.9.2-0ubuntu4) oneiric; urgency=low

  * debian/control: depends on the greeters rather than recommends, seems some
    users still get no greeter after upgrade otherwise


---

### Post by Starks on 2011-07-28
Here's a nice glaring bug.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/815271](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/815271)
"Cannot login if user account does not have a password"

---

### Post by dino99 on 2011-07-28
> **Starks said:**
> Here's a nice glaring bug.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/815271](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/815271)
"Cannot login if user account does not have a password"

no password, you brakes the rules. Not a bug, its Linux spirit.

---

### Post by lucazade on 2011-07-28
> **dino99 said:**
> no password, you brakes the rules. Not a bug, its Linux spirit.

hahaha! true :)
Do we need RMS action again?

"When MIT's Laboratory for Computer Science (LCS) installed a password control system in 1977, Stallman found a way to decrypt the passwords and sent users messages containing their decoded password, with a suggestion to change it to the empty string (that is, no password) instead, to re-enable anonymous access to the systems. Around 20% of the users followed his advice at the time, although passwords ultimately prevailed. Stallman boasted of the success of his campaign for many years afterward."

---

### Post by dino99 on 2011-07-28
the opinions of Richard M. Stallman and the Debian project
have diverged :)

---

### Post by MacUntu on 2011-07-28
Also check /var/crash for this [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/816980](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/816980)

Using GDM instead seems to work for Ted Gould, doesn't for me as that crashes too (I'm now using XDM :D).

---

### Post by EgoGratis on 2011-07-28
Today LightDM did upgrade normally yes. But now i see that yesterday i was probably asking different thing. I tested this a while back:

[http://ubuntuforums.org/showthread.php?t=1803709](http://ubuntuforums.org/showthread.php?t=1803709)

And at some point it didn't let me log in anymore so i didn't use it anymore.

I was wondering when this "new theme" will become default.

---

### Post by dino99 on 2011-07-28
latest ligtdm 0.9.2-0ubuntu4 have greeter now installed by deault

---

### Post by EgoGratis on 2011-07-28
This one?

[http://www.webupd8.org/2011/07/first-ubuntu-1110-lightdm-greeter-theme.html](http://www.webupd8.org/2011/07/first-ubuntu-1110-lightdm-greeter-theme.html)

---

### Post by cecilpierce on 2011-07-28
How do I get the greeter to come up when I login or out?
I have unity-greeter and lightdm-greeter in here and I still get the old login thing.
I guess I'll ask in case some one knows, what happen to auto login ? Getting tired of typing password :P

---

### Post by Bowmore on 2011-07-28
First of all you should update your lightdm.conf to the new format
```
sudo cp /usr/share/doc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf
```and lightdm will run with its defaults. But do a backup first just in case.

Then edit the file /etc/lightdm/lightdm.conf and configure **greeter-session** manually in the [SeatDefaults] section:
[B]
greeter-session[/B]=lightdm-gtk-greeter (for the current default greeter)
**greeter-session**=unity-greeter (for the unity-greeter if installed)

In the same section, to activate autologin for user <user-name>:

**autologin-user**=<user_name>
**autologin-user-timeout**=0

And of course, those lines shall be uncommented too.

---

### Post by cecilpierce on 2011-07-28
@Bowmore
Thanks alot, I willto try it out, let you know how it goes, I haven't had much luck lately.

---

### Post by MacUntu on 2011-07-28
Don't forget pam-service=lightdm-autologin.

---

### Post by cecilpierce on 2011-07-28
@Bowmore
Well it all went great, autologin then I had to logout and back in to see the greeter, I used unity-greeter, I guess the lightdm would work but I tried it in a terminal and it had some errors and didn't show up like unity did,
Thanks a million

@MacUntu
I saw that somewhere in my stumbling around trying  this and that, where is it and what does it do ?
Thanks for the info

---

### Post by MacUntu on 2011-07-28
I have no idea, but that's what's set when installing with auto-login enabled, so it's probably needed for something. :D

---

### Post by lucazade on 2011-07-28
> **MacUntu said:**
> I have no idea, but that's what's set when installing with auto-login enabled, so it's probably needed for something. :D

pam module should auto unlock gnome keyring when doing autologin.

---

### Post by MacUntu on 2011-07-28
Ah right, to get rid of that annoying keyring prompt. !:****-)

Right now I have auto-login disabled to be able to actually spot any bugs. :P

---

### Post by EgoGratis on 2011-07-28
> pam module should auto unlock gnome keyring when doing autologin.

Before Ubuntu 11.10 this was not possible? Is this correct or am i wrong and it was?

---

### Post by MacUntu on 2011-07-28
AFAIK only with an empty keyring password.

---

### Post by EgoGratis on 2011-07-28
I see.

---

### Post by ratcheer on 2011-07-28
> **Harry33 said:**
> This is in repos right now.
Just rememeber to install all these three (gnome):
-lightdm
-liblightdm-gobject-1-0
-lighdm-gtk-greeter

and to uninstall old lightdm packages, like
-liblightdm-gobject-0-0
-lightdm-greeter-example-gtk

Are these still the correct installation instructions? Do you also uninstall the old lightdm, first?

Tim

---

### Post by ratcheer on 2011-07-28
> **ratcheer said:**
> Are these still the correct installation instructions? Do you also uninstall the old lightdm, first?

Tim

Never mind. I removed the two packages the instructions said to uninstall, installed the two it said to install in addition to lightdm, then upgraded lightdm. It worked, perfectly.

Thanks,
Tim

---

### Post by Harry33 on 2011-07-29
> **ratcheer said:**
> Are these still the correct installation instructions? Do you also uninstall the old lightdm, first?

Tim

It is important to uninstall the old greeter package and the old liblightdm package.
Package lightdm is updated automatically.
After instalation you can change settings (font, theme) of the greeter here:
/etc/lightdm/lightdm-gtk-greeter.conf

---

