---
title: "How do I know if I loaded Ubuntu inside Windows"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by tuusharp on 2013-03-24
A newbie to Ubuntu and I am injoying the experience. 
The process I used was I loaded Ubuntu onto a DVD, then from Windows I executed.

Now .........when the computer boots up, it goes to a black screen and asks which OS I want to use,
Windows XP or Ubuntu.

I'm assuming I have loaded Ubuntu into Windows, I did not use Wubi.

Moving forward I would now like to delete windows and only have Ubuntu as my default OS.

Can someone help by giving a real easy to understand step by step guide to doing this.

Your help is much appreciated.

---

### Post by deadflowr on 2013-03-24
If you executed the Ubuntu disk while using Windows, and from there Ubuntu installed on your system, then you are in fact using a Wubi install.

To do a clean install of Ubuntu, simply keep the disk in the disk drive restart.
You might need to change the boot order status of the Computer.

You'll need to make the system boot to the cd/dvd player before the hard drive, otherwise if the hard drive is listed to boot before the cd player then the hard drive will boot first.

Once you've figure that out then simple run the disk from start up (when you turn on the computer) and either run a live session off the disk or choose to install.

---

### Post by tuusharp on 2013-03-24
Cool thanks.........deadflowr

Not really a computer literate person........... how do i change the boot order status of the Computer  ?

---

### Post by Moose on 2013-03-25
Open your start menu, then type msconfig.exe and press enter. There is a tab for the boot options.

Regards.

---

### Post by Impavidus on 2013-03-25
Never heard of msconfig.exe, but then again, I haven't used windows in ages.

The alternative (most standard because it always works) way is pressing escape, F2, F10, F12 or delete as soon as your computer boots. Which one you need depends on your hardware and is typically shown in the splash screen you get the moment you switch on your computer. You'll get a menu where you can choose your boot order.

---

