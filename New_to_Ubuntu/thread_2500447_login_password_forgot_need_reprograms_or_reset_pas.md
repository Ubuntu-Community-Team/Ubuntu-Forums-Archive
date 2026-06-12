---
title: "login password forgot need reprograms or reset password new to xubuntu"
date: 2024-09-02
forum: New to Ubuntu
---

### Post by chris2007 on 2024-09-02
One of my friends give me this laptop that she forgot ther password its something new to me with the command on xubuntu i search around and I found this forum and I have to ask here for help.

I attach some of the image that I takes its may help to my questions

I need to reprograms that may override to start with new acc that my last option

May I ask its can be reset the password? 

Please I need help on this its new to me to work on xubuntu


thanks[IMG]https://ibb.co/GTtJVwC [https://ibb.co/yfX0b4P](https://ibb.co/yfX0b4P) https://ibb.co/0BFmMgQ[/IMG]

---

### Post by TheFu on 2024-09-02
Probably best to just perform a fresh install.  That takes about 10-15 minutes and you will know that the system is clean.

---

### Post by Rex Bouwense on 2024-09-02
TheFu's suggestion of a re-install is probably the easiest and most efficient.  However, you can reset the password if you have physical possession of the computer.  First you must boot into the recovery mode.  If more than one OS is installed you should automatically see the GRUB menu.  If the OS was installed in the legacy mode you must hold down the shift key during boot.  If the OS was installed in EFI mode, you must tap the Esc key during boot.
Once you have the Grub menu, select the recovery mode (usually the second entry) and press enter.  On the next screen scroll down using the down arrow on your keyboard to "drop to root shell prompt" and press enter.  You will see the root prompt at the bottom of the window.
Type *passwd username*  replacing username with your user name.  You will be prompted for a new password.  Just type your new password.  You will receive no indication that the password is being acknowledged.  When you are finished hit enter.  You will be prompted to re-enter the password.  Do so and hit enter again.
Type*exit* and hit enter and you will return to the previous menu.  Select "resume normal boot" and now you know your password.

---

### Post by chris2007 on 2024-09-02
thanks has been download and install fresh Xubuntu

---

### Post by chris2007 on 2024-09-02
> **Rex Bouwense said:**
> TheFu's suggestion of a re-install is probably the easiest and most efficient.  However, you can reset the password if you have physical possession of the computer.  First you must boot into the recovery mode.  If more than one OS is installed you should automatically see the GRUB menu.  If the OS was installed in the legacy mode you must hold down the shift key during boot.  If the OS was installed in EFI mode, you must tap the Esc key during boot.
Once you have the Grub menu, select the recovery mode (usually the second entry) and press enter.  On the next screen scroll down using the down arrow on your keyboard to "drop to root shell prompt" and press enter.  You will see the root prompt at the bottom of the window.
Type *passwd username*  replacing username with your user name.  You will be prompted for a new password.  Just type your new password.  You will receive no indication that the password is being acknowledged.  When you are finished hit enter.  You will be prompted to re-enter the password.  Do so and hit enter again.
Type*exit* and hit enter and you will return to the previous menu.  Select "resume normal boot" and now you know your password.


thanks will noted

---

### Post by TheFu on 2024-09-02
> **chris2007 said:**
> thanks will noted

Beware.  If the system uses full drive encryption, resetting passwords using either a "maintenance shell" or "booting from an ISO" and doing a chroot won't work.  Laptops should be encrypted most of the time, if you care about security.  But if you use encryption, having excellent backups are needed, since a little hardware error on the disk can make access to all the data impossible.  This is good for security. Bad for lots of other reasons.  Just something to consider.

BTW, whenever posting questions, please remember to say the specific release used (22.04?) and the DE used with every question.  Sometimes it matters.  

To help the community be more efficient, it also helps if you'll use the _Thread Tools button_ and mark this thread as **SOLVED**. Only the originator can do this - that's you chris2007.  It helps people with similar problems find only those threads that are solved and it prevents people wanting to help from bothering with already SOLVED threads. Saves everyone time.

No issues at all with this thread. I'm not complaining.  Getting multiple answers is good and letting us know which one you decided to use really helps as well.  I really thought you'd use the maintenance shell method since it is about 30 seconds to do and most of the time, that method would be best.  After you create a flash drive with the fresh ISO to install, be certain to keep that around, since most boot issues cannot be solved without it. The maintenance shell isn't available sometimes.  

Anyway, hopefully, you'll find these forums helpful.  Searching for similar issues to yours would likely have found 20+ others just like this and saved you a little time.  But definitely ask your question in a new thread if the answers you find don't work or aren't clear.  All our systems are just a little different, so sometimes exact help just for your needs is best.

---

