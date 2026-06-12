---
title: "Ubuntu setup acting strange"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by penguinbreath on 2008-06-06
This morning while using Ubuntu, GNOME froze on me; all the toolbars stopped responding and I had to ctrl+alt+backspace. I tried to re-login, but nothing would happen (blank screen). I believe I had the -17 linux kernel at this time.
   I rebooted my computer, and everything seemed to work. After I rebooted I wondered if maybe it was some bug that was already fixed. I ran an update and the update included the -18 linux kernel. ( it was 100mb in updates)
    When I started up with the new kernel (-18 ), everything seemed fine for awhile, but later I realized my sound was not working. It appeared the driver wasn't working. I tried to open the terminal, but it wouldn't load. I tried to open Firefox, but it would not load. I tried opening Epiphany and nothing happened. I tried to reboot, but It wouldn't respond. I hit ctrl+alt+ backspace, then Ubuntu then decided to reboot.
    This time I started Ubuntu with the -16 kernel. It *seems* everything is working properly (including sound).

Does anyone have any ideas whats going on?  Could it have possibly been a corrupt kernel?  If so what do I need to reinstall including the -18 linux kernel. Also I would prefer to install it from the command line, but I do not know the command, or the package name. I cannot seem to find the linux kernel in synaptic.

I really do not know what to do or whats going on, so any help would be greatly appreciated! :)

---

### Post by ardvark71 on 2008-06-06
Hi...

I don't know the answer in solving your upgrade but if everything is working correctly with the -16 kernel, I would definitely keep it where it's at. ;)

Best Regards...

---

### Post by penguinbreath on 2008-06-06
Is there a way to set (-16) as the default kernel on startup? Or will I need to uninstall the other two kernels (-17) (-18 )?

---

### Post by Miljet on 2008-06-06
You can edit your /boot/grub/menu.lst file. Near the top of the file is a place to specify which entry boots by default.

Set default and the number of the kernel you want to boot. Remember the numbers start with 0.

---

### Post by penguinbreath on 2008-06-07
I just started up with the -18 kernel, and there is no problems as of yet. :confused:

I am confused as to what happened yesterday. Any ideas?

---

### Post by balachandarlinks on 2008-06-07
I too come across a similar problem after upgrade.....After upgrade it may ask u for a reboot.....A small blue circle will appear in ur taskbar for reboot..after reboot it wirks fine for me....May it the same case for u also......

---

### Post by penguinbreath on 2008-06-09
Did an update, rebooted, and I got some problem with my graphics driver. The system is stuck at 800x600.
I am also having problems with my file manager. For some reason it freezes when I try to run a search.

I believe my problems with Ubuntu started when I made a virtual drive for virtualbox. 
My graphics driver broke right after I made a new virtualbox virtual drive that was 2gb. Is it possible that the creation of the virtual drive somehow corrupted my Ubuntu installation?

Does anyone have an idea as to what is going wrong?
 
Is there a system restore on a Ubuntu CD I can use? Otherwise I may just do a fresh reinstall. I do not want to stay with this current installation in the way it is, as it is to unstable/buggy.


Any ideas? I really need help here. :(

edit:
It appears my sound driver is not working or is missing.

---

### Post by ukripper on 2008-06-09
> **penguinbreath said:**
> This morning while using Ubuntu, GNOME froze on me; all the toolbars stopped responding and I had to ctrl+alt+backspace. I tried to re-login, but nothing would happen (blank screen). I believe I had the -17 linux kernel at this time.
   I rebooted my computer, and everything seemed to work. After I rebooted I wondered if maybe it was some bug that was already fixed. I ran an update and the update included the -18 linux kernel. ( it was 100mb in updates)
    When I started up with the new kernel (-18 ), everything seemed fine for awhile, but later I realized my sound was not working. It appeared the driver wasn't working. I tried to open the terminal, but it wouldn't load. I tried to open Firefox, but it would not load. I tried opening Epiphany and nothing happened. I tried to reboot, but It wouldn't respond. I hit ctrl+alt+ backspace, then Ubuntu then decided to reboot.
    This time I started Ubuntu with the -16 kernel. It *seems* everything is working properly (including sound).

Does anyone have any ideas whats going on?  Could it have possibly been a corrupt kernel?  If so what do I need to reinstall including the -18 linux kernel. Also I would prefer to install it from the command line, but I do not know the command, or the package name. I cannot seem to find the linux kernel in synaptic.

I really do not know what to do or whats going on, so any help would be greatly appreciated! :)

Try using latest update from update-manager kernel -19 as everyone's hardware is different. For me i had some issues with -17 but in -16 and -18 everything is working flawlessly.

---

### Post by penguinbreath on 2008-06-09
> 
Try using latest update from update-manager kernel -19 as everyone's hardware is different. For me i had some issues with -17 but in -16 and -18 everything is working flawlessly.

Do you mean a pre-released update?

My system is fully up to date.

---

### Post by ukripper on 2008-06-09
> **penguinbreath said:**
> Do you mean a pre-released update?

My system is fully up to date.

Not sure if it is pre-release or stable but if it works for you then there is no harm.

---

### Post by penguinbreath on 2008-06-09
> Not sure if it is pre-release or stable but if it works for you then there is no harm. 

Do I download the newer kernel from synaptic?

---

### Post by ukripper on 2008-06-09
if your repos are enabled it should be available to you through update-manager. Check your repos first

---

### Post by penguinbreath on 2008-06-09
I was installing some things for virtualbox. One of the things was a linux kernel for servers.


I do uname -a and I get "-18 server"

Is this normal?

---

### Post by penguinbreath on 2008-06-09
I restarted Ubuntu and used the -16 kernel. All seems to be well. :)


edit:
I just looked at what I installed. I had installed a virtual box module linux kernel -18 server this morning.
How did a -18 server kernel end up on the top of my grub boot list? I thought virtual box module installations only affected virtualbox. :confused:

---

### Post by ukripper on 2008-06-09
> **penguinbreath said:**
> I restarted Ubuntu and used the -16 kernel. All seems to be well. :)


edit:
I just looked at what I installed. I had installed a virtual box module linux kernel -18 server this morning.
How did that end up on the top of my grub boot list? I thought virtual box things were just used inside virtualbox. :confused:

It doesn't mean virtual box. Kernels are always in virtual image when they are loaded in grub menu.lst

---

### Post by penguinbreath on 2008-06-09
Was it virtualbox that messed up my computer as result of myself not knowing how to use it properly?

Should I just format and reinstall, and just stay away from using virtualbox?

---

### Post by ukripper on 2008-06-09
> **penguinbreath said:**
> Was it virtualbox that messed up my computer as result of myself not knowing how to use it properly?

Should I just format and reinstall, and just stay away from using virtualbox?

There is nothing wrong with virtualbox. if it is running fine in -16 then i see no problem with virtualbox. It is more likely the kernel updates. If -16 is stable for you then use it until the next latest stable kernel release. don't reinstall your system if it is working fine under -16

---

### Post by penguinbreath on 2008-06-09
> There is nothing wrong with virtualbox. if it is running fine in -16 then i see no problem with virtualbox. It is more likely the kernel updates. If -16 is stable for you then use it until the next latest stable kernel release. don't reinstall your system if it is working fine under -16


I was planning to switch to Kubuntu in a few months. Perhaps I will begin the installation of it today or tomorrow. (Since I made backups of my system this morning.)
  I will try to stick with the -16 kernel.

Thanks for your help! :)

---

