---
title: "[SOLVED] Gnome terminal text (fonts) spacing mess"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by fourthofjuly on 2008-09-17
[SIZE="2"][COLOR="Blue"]hi...

was trying to tweak my gnome terminal window for colours with help from this link...

[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/]("http://www.ibm.com/developerworks/linux/library/l-tip-prompt/")

but have messed up the text (fonts) as spacing of some letters is too close now to be readable... this is not the case with the default profile...

please see the screenshot...

I tried re-installing gnome-terminal but to no avail...

please help...!!![/COLOR][/SIZE]

---

### Post by fourthofjuly on 2008-09-17
anyone, please?

---

### Post by fourthofjuly on 2008-09-17
awaiting.....

---

### Post by zerhacke on 2008-09-17
You're going to piss a lot of people off by bumping your own thread several times per hour.  You're also screwing yourself out of the unanswered unreplied thread count.  A thread without any answers is often picked to answer a question rather than one with multiple answers as it is assumed those threads have been answered already.

---

### Post by cariboo on 2008-09-17
I don't suppose you made a backup of /etc/bash.bashrc? I suppose you could remove the changes you made to restore it back to the default settings. If you created a .bashrc file in your home directory you could delete it.

Without knowing what and how you changed the settings it is pretty hard to tell you what to do to repair your problem. 

Reinstalling a program because you sdrewed up the config file is not going to change anything as you found out. Reinstalling a program because it doesn't work the way you expected, is the windows way of doing things. Remember Linux is not Windows. What you know about windows does not transfer to Linux.

If you could post the files you changed we might be able you to solve your problem.

Jim

---

### Post by quinnten83 on 2008-09-17
If you've got a live cd you can try copy the .bashrc file back to your home folder.
start from the live cd, look for the .bashrc (find .bashrc) and copy it to your harddisk.

Also i believe if you put in the command export PS1=""\e[0m >" should set the foreground and background color back. Also in Gnome-terminal you can change text in edit, current profile, try with that see if it helps. 

Sorry, I looked this up and couldn't come up with anything better. Perhaps someone else might be able to help you better.

That tutorial is from 2000 BTW, although I think it is still up to date, I would check around first before experimenting in such detail with your bash.

---

### Post by nowshining on 2008-09-17
did you perhaps change fonts?? some fonts make the txt appear closer than others..

---

### Post by fourthofjuly on 2008-09-18
> **cariboo907 said:**
> I don't suppose you made a backup of /etc/bash.bashrc? I suppose you could remove the changes you made to restore it back to the default settings. If you created a .bashrc file in your home directory you could delete it.

Without knowing what and how you changed the settings it is pretty hard to tell you what to do to repair your problem. 

Reinstalling a program because you sdrewed up the config file is not going to change anything as you found out. Reinstalling a program because it doesn't work the way you expected, is the windows way of doing things. Remember Linux is not Windows. What you know about windows does not transfer to Linux.

If you could post the files you changed we might be able you to solve your problem.

Jim
thanks, i did not create it but the .bashrc file was already there in my home directory... i had added / removed a line exactly like below (did this  2-3 times since i was testing to view different colours):
------------------------------------------------------------
export PS1="\[\e[36;1m\]\u@\[\e[32;1m\]\H> \[\e[0m\]"
------------------------------------------------------------


the following are the contents of .bashrc prior to editing & at present:

==============================================
# .bashrc

# User specific aliases and functions

# Source global definitions
if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi
==============================================

please help...

---

### Post by fourthofjuly on 2008-09-18
> If you've got a live cd you can try copy the .bashrc file back to your home folder.
start from the live cd, look for the .bashrc (find .bashrc) and copy it to your harddisk.

thanks, ok i am trying your suggestion of live CD... looks like this will work...!!!

i will backup my ~/.bashrc file as ~./bashrc.old & copy a new version from the live CD...

> Also i believe if you put in the command export PS1=""\e[0m >" should set the foreground and background color back. Also in Gnome-terminal you can change text in edit, current profile, try with that see if it helps.


> did you perhaps change fonts?? some fonts make the txt appear closer than others..

well, the current profile thing is not helpful since if i enable "use the system fixed width font" the text appears ok... its only with the other profiles that this problem appears...

---

### Post by hellion0 on 2008-09-18
Monospaced fonts tend to work best in the Terminal. Try finding a monospace or fixed-width variant of the font you want to use.

---

### Post by fourthofjuly on 2008-09-18
> **hellion0 said:**
> Monospaced fonts tend to work best in the Terminal. Try finding a monospace or fixed-width variant of the font you want to use.
thanks... 

yes, indeed only monospace fonts are working... i guess i will manage with that...!!!

---

### Post by hissyfut on 2008-11-25
> **fourthofjuly said:**
> thanks... 

yes, indeed only monospace fonts are working... i guess i will manage with that...!!!

Where are the monospace aliases? How would monospace be called for use in a different terminal than gnome terminal.
-fn what?

---

### Post by rajendran.bits on 2010-05-27
Thanks for the great help...

I think some one may face this issue when the upgrading from ubuntu 9.10 to 10.04.

---

