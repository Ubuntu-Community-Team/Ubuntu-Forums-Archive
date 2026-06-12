---
title: "Debian-unofficial under Ubuntu?"
date: 2005-12-13
forum: Repositories &amp; Backports
---

### Post by NotJustANewbie on 2005-12-13
Does anyone know if the debian-unofficial repositories work with Ubuntu?
They're useful for JRE and Skype etc... or is there an Ubuntu repository that has these packages too? (I've tried universe and multiverse)

---

### Post by earobinson on 2005-12-13
This is risky It may work but debian and ubuntu are not 100% compatiable they just work most of the time. Its a risk and it could break something. But if your up for the chalange go for it.

I would recomend just takeing the debs and installing the one by one.

---

### Post by NotJustANewbie on 2005-12-13
Thanks, I think I'll give that a miss.  I like having my system up-to-date automatically (an old windows habit I know). I'll live without JRE for the moment. :rolleyes:

---

### Post by canadianwriterman on 2005-12-13
[QUOTE=NotJustANewbie]Thanks, I think I'll give that a miss.  I like having my system up-to-date automatically (an old windows habit I know). I'll live without JRE for the moment. :rolleyes:[/QUOTE]

I believe JRE is available by installing Automatix first, then running Automatix and selecting JRE for installation.

---

### Post by earobinson on 2005-12-13
Automatix will not keep your system up to date either :(

---

### Post by canadianwriterman on 2005-12-13
True, earobinson. I was just thinking in terms of getting him set up with a JRE install that has been packaged for Ubuntu and installs easily.

---

### Post by NotJustANewbie on 2005-12-13
Thanks for your replies. Maybe I will set up my own Ubuntu-unofficial repsository... ubuntu-unofficial.org - I can see it already ;)

---

### Post by earobinson on 2005-12-13
lol is that not how the backports started? Now they are offical lol.

---

### Post by curuxz on 2005-12-14
when you say automatix wont keep the system upto date, do you mean it installs old packages, or that it locks the packages so they wont update via apt?

As far as i was aware you could use it and then your apt system would auto update the packages from then on as normal?

---

### Post by earobinson on 2005-12-14
you would have to make a post in the automatrix section, but as I understand It installs some deb files that arnt linked up in the repos

---

### Post by DrBair on 2005-12-14
[QUOTE=NotJustANewbie]Thanks for your replies. Maybe I will set up my own Ubuntu-unofficial repsository... ubuntu-unofficial.org - I can see it already ;)[/QUOTE]

And it will have all the dev libraries I could ever want, hot off the presses... 

Man, I miss Gentoo sometimes. I <3 ebuilds.

---

### Post by NotJustANewbie on 2005-12-14
I've added the debian-unofficial repositories and it works fine. Just to let other people know.

---

### Post by earobinson on 2005-12-14
[QUOTE=NotJustANewbie]I've added the debian-unofficial repositories and it works fine. Just to let other people know.[/QUOTE]
_**[COLOR="Red"]Warning:[/COLOR]** Just because it works fine now dont mean that debian wont change something and it will mess up your computer._

I know I have said this before but I feal it is only fair to put a warning close to text claiming it works.

NotJustANewbie Thanks for letting us know, Im going to try it out :) But then I break my computer all the time

---

### Post by NotJustANewbie on 2005-12-14
Thank you for your wise announcement. All I have installed from the debian-unofficial repositories are skype and jre anyway. The dependencies for both of these packages were all from the official ubuntu repositories I noticed, so this seems to be safe ;)

---

