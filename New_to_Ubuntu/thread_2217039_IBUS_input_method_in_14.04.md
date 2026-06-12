---
title: "IBUS input method in 14.04"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by nns2006 on 2014-04-15
Hello,
I have been recently trying ubuntu 14.04, previously I was using 12.04 on my dell vostro 1500. What I am finding difficult is- using IBUS to write hindi. There is no option to select "intrans" which gives easy method to writing on US english keyboard. has it been discontinued or is it just a matter of time until April 17 after which these options will become available? 

Any idea how to get it working back? 

thanks and regards

Nitya

---

### Post by grahammechanical on 2014-04-15
What have you tried. In 14.04 we go to System Settings and with the Keyboard utility we can install a Hindi keyboard layout. There is Bolnagri, KaGaPa phonetic and Wx Hindi layouts. At the first Keyboard screen click Text Entry. We can also click the keyboard layout icon that is now in the top panel by default and select Text Entry Settings and that will take us to where we can add another keyboard layout.

We also have System Settings>Language Support. You will see that the default keyboard input method is Ibus. If you add language support for Hindi you may find that there may be other input method options available.

Ubuntu 14.04 development reached feature freeze as far back as 21 February. If a looked-for feature is not yet in 14.04, then it will not now be in it.

[https://help.ubuntu.com/community/ibus](https://help.ubuntu.com/community/ibus)


The 14.04 software centre does have ibus-m17n which should give you the itrans layout.
Regards.

---

### Post by nns2006 on 2014-04-16
Thank you for replying grahammechanical. 
I have tried already what you have suggested. You can see it in the screenshot attached. Besides this I don't find any option to add "itrans" which was availble in 12.04 LTS.  I find it really disappointing as I translated office using ibus-itrans into hindi so that I can use it with it with ease and now the writing options itself has vanished. Seems like I prepare the food and went to bring plate and in meantime ubuntu ate it. 
[ATTACH=CONFIG]252111[/ATTACH]

---

### Post by su:bhatta on 2014-04-16
Looking at this link : [http://iso.qa.ubuntu.com/qatracker/milestones/314/builds](http://iso.qa.ubuntu.com/qatracker/milestones/314/builds) given by sudodus in another thread it lists 
'ibus does not support certain keyboard layouts' under Xubuntu Bugs.

Can this be the issue?

---

### Post by nns2006 on 2014-04-20
I apologise for making it here. I dig in into text entry option and found that I has been under a different option. Infact all "itrans" option is under one place written in their respective language.

Thank you.

---

### Post by Murukesh on 2014-06-08
> **nns2006 said:**
> I apologise for making it here. I dig in into text entry option and found that I has been under a different option. Infact all "itrans" option is under one place written in their respective language.

Thank you.

I'd just like to add that, for the same issue, I had to restart X to get the languages to show up in ibus-setup. Then, after adding the language in ibus-setup, I had to do so again in the *Input Sources* section of *Region and Languages* before I could actually use it. I was using gnome-shell, and the Arch Wiki helped out: [https://wiki.archlinux.org/index.php/IBus#GNOME](https://wiki.archlinux.org/index.php/IBus#GNOME)

---

### Post by S._Venkataraman on 2014-10-13
I have installed hindi language support and 
I have tried to enable itrans, but input method is not there. 
 It show only KAGA phonetic,
Bolnagari and Wx.  
Can somebody give more detailed instructions?
Can you tell me where you found all the options for itrans 
together?
**Update:**
I typed ibus-setup in terminal and in the `input-method' tab
I set hindi input method to itrans.  But this has no effect.
In the text entry setting in the task bar itrans is not shown.
What can be the problem?

---

### Post by vvasuki on 2014-11-27
You need to install ibus-m17n

---

