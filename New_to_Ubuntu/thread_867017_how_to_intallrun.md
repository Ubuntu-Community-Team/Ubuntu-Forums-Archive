---
title: "how to intall/run"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by bedhed on 2008-07-22
hi,
i am very new to ubuntu so please pardon my ignorance. i have no idea how to run or install anything. i downloaded a free dvd player but its just sitting on my desktop. its called cdvd.exe. i try opening it or running dvds on it but it does nothing. i assumed it will install/run itself as in windows. can anyone help?

---

### Post by tech0007 on 2008-07-22
Use synaptic to install programs.  It's in System->Administration->Synaptic Package Manager.

That cdvd.exe won't run on ubuntu unless you have WINE, it may not work at all. What's this program for?

---

### Post by era86 on 2008-07-22
You cannot download exe's and run them natively in Ubuntu.  You can run it in Wine, though you can never be 100% it will work.  Trying looking for applications in the Synaptic package manager or download the .deb installers for your desired applications.

---

### Post by scragar on 2008-07-22
exe's are windows executable files, so it may or not run under wine, first I'd check for a linux version or alternative, if it's to play DVD's then I'd recomend the default media player after installing the restricted extras package(see [how to install anything in ubuntu](http://monkeyblog.org/ubuntu/installing/), your after **ubuntu-restricted-extras**), or try VLC is which is a nice choice. there's also guides on how to install wine, although it's easy enough.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by 16777216 on 2008-07-22
Well, first off Ubuntu will not run Windows .exe files as it is GNU/Linux.
That being said, A program called wine allows you to run _*some*_ Windows programs in Ubuntu.
It is reversed engendered and that is why it does not always work perfectly. ( Micro Soft are not going to tell us how Windows does things that is why wine has to be reverse engendered. ) 

To install wine go to the add/remove programs in the menu at the top of the screen when it comes up type 'wine' ( without the ' s ) that will filter the list of programs to all that are wine related.
Then just click the check box next to the entry for wine and click apply choose ok/apply on the remaining dialogs.

After it is done you will have a new entry in the applications menu called wine, their will be an entry to configure wine run that.
Many windows programs will work now.


Wow I type slow!

---

### Post by zipperback on 2008-07-22
".exe" file are Windows executable files.

You honestly DO NOT want to install that on your system. There isn't any need for it.

Try this link for a little more information.

[http://ubuntuforums.org/showthread.php?t=828342#2](http://ubuntuforums.org/showthread.php?t=828342#2)


- zipperback
:popcorn:

---

### Post by bedhed on 2008-07-22
i tried getting WINE but when i tried to install it it said 'Can not install 'wine' (E:Unable to correct problems, you have held broken packages.) '

---

### Post by aomlives on 2008-07-22
You really shouldn't be bothering about that "cdvd.exe", there are a lot more and better media players available for Ubuntu. 
Besides, this cdvd.exe seems to be some Windows spyware, or at least it's from a doubtful source (according to Google). Anyway don't try to run it with WINE. 

Just enable the Medibuntu repos ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) and get a decent media player using Add/Remove.

---

### Post by oldos2er on 2008-07-22
> **bedhed said:**
> i tried getting WINE but when i tried to install it it said 'Can not install 'wine' (E:Unable to correct problems, you have held broken packages.) '

 Open Synaptic Package Manager (System, Administration menu), click the Edit menu at the top, then 'Fix Broken Packages.'

---

### Post by bedhed on 2008-07-22
thank you all very much. i shall try all your suggestions. thank you.

---

