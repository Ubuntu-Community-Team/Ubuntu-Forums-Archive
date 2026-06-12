---
title: "Oneric 10.11 screen goes black while working only way out is a power-down."
date: 2011-12-23
forum: New to Ubuntu
---

### Post by earthead on 2011-12-23
[SIZE=1]Good evening.

I am a newbie with Linux. I have been using Oneric 11.10 for about six weeks now. On the odd occasion, about 10 times now, my Laptop (toshiba U400) screen goes black while I am busy working. All I can see is the mouse arrow moving around the screen as I move the mouse. The system seems to freeze and there is no way of retrieving any usable GUI. The only way out is a hard power down which any machine does not enjoy.

google search only finds the default screen setting issue which I have altered in the screen settings in system tools>screen>lock to off so this is not the problem.

If anyone has encountered this problem please enlighten me. If it is solved please forward any links, (I have searched and not found anything helpful yet.)
[/SIZE][SIZE=1]
[/SIZE][SIZE=1]Thank-you.[/SIZE]

---

### Post by Mahkoe on 2011-12-24
Type the following command:
sudo gedit /etc/acpi/lid.sh
Comment out the line that says
if [ `CheckPolicy` = 0 ]; then exit; fi (By adding a "#" at the beginning of the line)
And add 
vbetool dpms on
right underneath.

---

### Post by lolpenguin on 2011-12-24
> **earthead said:**
> [SIZE=1]Good evening.

I am a newbie with Linux. I have been using Oneric 11.10 for about six weeks now. On the odd occasion, about 10 times now, my Laptop (toshiba U400) screen goes black while I am busy working. All I can see is the mouse arrow moving around the screen as I move the mouse. The system seems to freeze and there is no way of retrieving any usable GUI. The only way out is a hard power down which any machine does not enjoy.

google search only finds the default screen setting issue which I have altered in the screen settings in system tools>screen>lock to off so this is not the problem.

If anyone has encountered this problem please enlighten me. If it is solved please forward any links, (I have searched and not found anything helpful yet.)
[/SIZE][SIZE=1]
[/SIZE][SIZE=1]Thank-you.[/SIZE]

There is no need to be so formal...
Welcome to the Ubuntu Community Forums:)

---

### Post by earthead on 2012-01-06
Thank-you for your time, much appreciated.

---

### Post by earthead on 2012-01-06
Thank-you, understood.

---

### Post by earthead on 2012-01-07
[Mahkoe]("http://ubuntuforums.org/member.php?u=1328097")

Thank you for your reply.

I have inserted as you suggested, but the problem still exists.

Can I send you any data?

Thank-you.

---

### Post by silleknarf on 2012-01-08
I'd like to report that I am having the exact same problem. 

I've tried changed all manner of power saving options and nothing has worked. The screen goes black and the cursor remains on screen, the only method of resolution I have found so far is to do a hard restart of my laptop. 

It is a Toshiba Satellite Pro L300 and I'm running Ubuntu 11.10. 

Let me know if there is anything I can do to help.

---

### Post by cmcanulty on 2012-01-08
upgrade to the latest kernel it has a patch for screen going black 3.0.0-15 if that doesn't do it email me as I have lots of things to try very irritating problem that started with 11.10 upgrade

---

