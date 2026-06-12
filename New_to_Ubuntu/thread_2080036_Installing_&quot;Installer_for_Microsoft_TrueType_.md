---
title: "Installing &quot;Installer for Microsoft TrueType core fonts&quot;"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by TerryDixon on 2012-11-02
When installing this software  from "Ubuntu Software Centre" I mistakenly failed to  accept the EULA. The package appeared to install OK  but actually hadn't. Now if I remove and re-install the package I get a failed EULA pop-up with no option to correct this.

How do I recover from this situation?

---

### Post by ibjsb4 on 2012-11-02
It sounds like you haven't installed the restricted-extras package either.  Its a needed package for audio/video and will include the ms fonts EULA agreement.

Search the software center for "ubuntu restricted extras" and install.

Should fix your problem  :)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by newb85 on 2012-11-03
Try this:
```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

I believe that will give you another opportunity to accept the EULA.

---

### Post by TerryDixon on 2012-11-04
Thanks guys but I have tried both suggestions above. Neither worked. In both cases I still get the message that I have not accepted the EULA.

---

### Post by uzumakifahim on 2012-11-04
I'm facing the same problem here. Is there anyway to get rid of this problem?

---

### Post by Linux_junkie on 2012-11-04
Instead of re-configuring ttf-mscorefonts-installer as mentioned above, have you tried to remove (purge) that package then install it later?
```
sudo apt-get purge ttf-mscorefonts-installer
```
then
```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by grahammechanical on 2012-11-04
Have either of you tried scrolling down to the bottom of the licence screen and clicking the Accept button?

---

### Post by mastergunner on 2013-01-21
I am having sort of the same issue though I do not see an accept at the bottom of the EULA. I see the word OK but nothing happens. HELP.

---

### Post by steeldriver on 2013-01-21
try pressing the TAB key until the OK box is highlighted - then press enter or spacebar

---

