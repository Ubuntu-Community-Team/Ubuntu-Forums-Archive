---
title: "I turned my computer into a paper weight."
date: 2013-03-08
forum: New to Ubuntu
---

### Post by parker4 on 2013-03-08
I have a Vista based laptop that. I created a separate partition and loaded linux into the empty partition. Now that I have installed ubuntu my hardware does not have installed drivers. I have no idea what the root password is so I cannot even begin to 'start' and 'try' installing drivers. I tried my password, I ran the terminal > sudo bash, but it only told me my user was not on some list and the shits getting reported.
So I restarted my laptop holding zero which normally brings up the vista utility. Now it just brings up a linux screen asking if I want to boot linux or an old deleted windows xp. I cannot find anything in bios letting me boot from the other partition containing vista. Because I cannot connect the computer to the internet I cannot load any programs that would allow me to switch from linux to windows. I just wanted to take more advantage with the RA  I have but I guess I turned my laptop into a paper weight...
Help me please!

---

### Post by tgalati4 on 2013-03-08
When you installed Ubuntu, you gave a user name and password.  That user is also the administrator and root user of the machine.  Use *sudo* with commands to operate with root privilege.

What version of Ubuntu did you install?  Was there ever a version of WinXP on the machine?  Always have a working network cable when installing, because wireless frequently will not work out-of-the-box.  But then you already knew that.

Open a terminal and post the output of:

```
sudo fdisk -l
```  (That's an "L" not a 1).

---

### Post by BlindSoothsayer on 2013-03-08
I would try loading Windows XP just to see what happens.  That could be your Vista partition.  I am dual booting Windows Vista and Ubuntu 12.10, for some reason Vista shows up as Windows 7 on my boot menu, even though I've never had Windows 7.

---

### Post by Mark Phelps on 2013-03-09
Ubuntu is not like Windows -- you don't follow an installation by hunting around for drivers.  Your hardware is scanned during the Ubuntu install and the correct drivers are installed automatically.

How did you shrink Vista to make room for Ubuntu? If you used the Ubuntu installer and shrank Vista using the slider, that can corrupting the Windows boot loader, rendering it unbootable?

If you're willing to pay a bit of money, there is a site where you can download an ISO of Win7 repair CD (which will work with Vista) and you can use that to get Vista working again.

---

### Post by schragge on 2013-03-09
> **parker4 said:**
> I tried my password, I ran the terminal > sudo bash, but it only told me my user was not on some list and the shits getting reported.If you're sure you entered your password right then this usually means you are not in the *sudo* (administrative) group. Open a terminal (**Ctrl**+**Alt**+**t**) and enter:
```
pkexec adduser $USER sudo
``` Then reboot.

[SIZE=-1]Sorry, just can't resist. An obligatory [xkcd reference]("http://xkcd.com/838/").[/SIZE] :)

---

### Post by justincarter on 2013-03-13
As you have already checked BIOS setting but it didn't work. I think There are some other system issues. You should go for it-support or hire a computer service. They will assist you well and you can get rid of your installing problems.[IT Support Austin]("http://tristarcc.com/it-support/")

---

