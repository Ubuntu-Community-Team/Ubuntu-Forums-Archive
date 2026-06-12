---
title: "Greek spelling with OOO2.4."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by altkon on 2008-11-02
I am only a new comer who has entered the world of Linux by dual installing Ubuntu 8.4 with WXP.
Everything works fine and I spent most of my time in tryng to learn the ins and outs of Linux OS.
Open Office.Org 2.4. came along with Ubuntu and I am having difficulties in Greek spell checking.
I tried to install the Greek Language Directory thru the Source Wizard but it was not possible because there not exists one.
Therefore I downloaded and saved the el_GR 0.5 version of the Greek dectionary dd 25Aug04 for OpenOffice.Org 2.4.but I dont know how to install it.:confused::(
So please could you explain to me how to do it so that it can give me
the option of Greek language spell check.
Thanks a lot.
Regards,
andre

---

### Post by Pro-reason on 2008-11-02
Did simply installing *myspell-en-gr* in Synaptic not work?

---

### Post by altkon on 2008-11-03
By Synaptic do you mean "Synaptic Package Manager" and if yes how can I process your command "myspell-en-gr" as I am totally ignorant.
Can you guide me please??
Thanks.
AA

---

### Post by gandaran on 2008-11-03
open synaptic and scroll down to myspell, find the Greek one mark for install and click the apply button

---

### Post by kostkon on 2008-11-03
> **altkon said:**
> By Synaptic do you mean "Synaptic Package Manager" and if yes how can I process your command "myspell-en-gr" as I am totally ignorant.
Can you guide me please??
Thanks.
AA
Search for it in *Synaptic*, left-click on it and select it for installation, and then hit the apply button.

---

### Post by altkon on 2008-11-04
A big thanks to Gandaran and Kostkon.
It all worked fine.:D
Now I have Greek language spell chk on my OO 02.4.
By the same token can I activate Thunderbird-local-el from Synaptic.??
and what about evolution mail message writer. Can I add Greek language  spell check?? And how... 
Regards,
andre

---

### Post by gandaran on 2008-11-04
> By the same token can I activate Thunderbird-local-el from Synaptic.??
yes
> and what about evolution mail message writer. Can I add Greek language spell check?? And how... 
thunderbird, firefox and open office use the myspell packages
evolution and all ubuntu gnome apps use something else, used to be ispell packages in hardy 8.04 and older distros, now in intrepid 8.10 I'm not sure, all I can find in synaptic installed are wamerican or wbritish packages, don't see any wgreek package or igreek in synaptic, but search synaptic, your ubuntu installation could be deferent.

---

### Post by simosx on 2008-11-04
The typical process in installing language support (including Greek), is to go to System/Administration/Language Support and make sure that Greek Modern is selected. This will pull in automatically the necessary packages.

You then need to restart (or logout, then re-login again).

In OpenOffice.org 2.x, you need to specify the document language so that the correct spelling language is activated. You can also configure the default document language in the preferences.

---

### Post by altkon on 2008-11-06
Greek spelling works fine in OpenOffice 2.4 now however does not check spelling on Evolution, but when press F7 returns message "spell checking" complete.
Any thoughts on how to activate Greek spelling in Evolution.
I have ispell installed already.
Thanks

---

### Post by altkon on 2008-11-08
> **altkon said:**
> Greek spelling works fine in OpenOffice 2.4 now however does not check spelling on Evolution, but when press F7 returns message "spell checking" complete.
Any thoughts on how to activate Greek spelling in Evolution.
I have ispell installed already.
Thanks

Would like to rephrase my posting above as follows.
Greek spelling checker does not work on Evolution.
Although Greek words exist in Spell checker frame when I type a phrase  in English letters it does not respond when I type a phrase in Greek letters.
Instead a message pops up informing "No misspelled words found".
Spell checker when it opens contains both EN and GR words.:confused:

---

### Post by simosx on 2008-11-21
> **altkon said:**
> Would like to rephrase my posting above as follows.
Greek spelling checker does not work on Evolution.
Although Greek words exist in Spell checker frame when I type a phrase  in English letters it does not respond when I type a phrase in Greek letters.
Instead a message pops up informing "No misspelled words found".
Spell checker when it opens contains both EN and GR words.:confused:

Evolution is a special case. It is a known bug and unfortunately, spelling does not work for the Greek language.

---

