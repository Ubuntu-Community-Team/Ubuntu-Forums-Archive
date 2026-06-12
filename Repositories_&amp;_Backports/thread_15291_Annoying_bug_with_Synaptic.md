---
title: "Annoying bug with Synaptic"
date: 2005-02-13
forum: Repositories &amp; Backports
---

### Post by M-Rick on 2005-02-13
Each time you modify something in the prefs of Synaptic you loose the access of the packages !
The lists are empties, but it finds the packages anyway since they are viewed at the bottom. I think there pref file becomes corrupted each time you cahnge a setting and this block the refresh of the packages list in teh window.
I have tried everything, even only changing one color in the color menu, and the same thig happens ...

Really boring ....

Yes I can use the apt-get in the terminal, but if I have a graphical software to do the same thing it is more confortable using it than the terminal !

---

### Post by WW on 2005-02-13
Have you filed a bug at bugzilla.ubuntu.com?

Are you running warty or hoary?

I am running warty, with version 0.53.4 of Synaptic. I just changed the color
of the "upgradeable" files in Settings->Preferences->Color, and I didn't see
any problem with the list of packages.

---

### Post by M-Rick on 2005-02-13
warty look at my signature : 4.10

so try to change expert default archive to stable or in temporary files to change to anything and you will see, it won't work anymore.

it is supposed to have a preferences file in the /apt/get folder but there is nothing even in invible files.

I am not the only one to have this problem, on the French forum there is a complete topic with this problem and both x86/PPC users.

---

### Post by WW on 2005-02-13
This bug sounds like the same one that you reported:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6151](https://bugzilla.ubuntu.com/show_bug.cgi?id=6151)

In the comments in the bug report,  Michael Vogt provides a link to a synaptic package that he says fixes the bug.  Take a look.


P.S. Your entries in this forum don't show a signature.

---

### Post by M-Rick on 2005-02-13
yes thank you the time you reply I was just reading it :)

---

