---
title: "I cant hibernate; &quot;Failed to hibernate session&quot; (Xubuntu 12.04LTS )"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Kharlo on 2012-09-12
When i he the "hibernate" option in the session menu (upper right corner of the screen)

i get this message:

failed to hibernate session
not authorized

then the screen locks

i have no problem login in, out restarting, suspending resuming from... but hibernation

---

### Post by anewguy on 2012-09-12
How much memory is in your PC?  When you installed Ubuntu, did you take the default size for swap?  If so, you'll need your swap to be 2 times the size of your physical memory + a small amount of overhead.

---

### Post by Kharlo on 2012-09-12
> **anewguy said:**
> How much memory is in your PC?  When you installed Ubuntu, did you take the default size for swap?  If so, you'll need your swap to be 2 times the size of your physical memory + a small amount of overhead.

mmm... interesting

my pc has 2gb physical ram, and 650mb of swap

its weird, i used to have ubuntu 12.04 and the other distros (10.04, 9.040 and none of them giveme problem with hibernation, and the swap size has been the same...

---

### Post by mips on 2012-09-12
> **Kharlo said:**
> mmm... interesting

my pc has 2gb physical ram, and 650mb of swap

its weird, i used to have ubuntu 12.04 and the other distros (10.04, 9.040 and none of them giveme problem with hibernation, and the swap size has been the same...

When you hibernate the contents of ram gets written to swap so you can't have swap space that is less than physical ram. Your swap has to be 1.5-2x bigger than your physical ram. Are you not maybe confusing hibernate with suspend?

Start by making your swap space 4GB and once you have done that and you still have issues we can take it further. You can resize your partitions from a livecd with gparted.

Form a terminal you can also try,
```
sudo pm-hibernate
```

I see you have moved to Xubuntu, how are you finding it compared to that old release of Ubuntu you were using?

---

### Post by Kharlo on 2012-09-12
> **mips said:**
> When you hibernate the contents of ram gets written  to swap so you can't have swap space that is less than physical ram.  Your swap has to be 1.5-2x bigger than your physical ram. Are you not  maybe confusing hibernate with suspend?

Start by making your swap space 4GB and once you have done that and you  still have issues we can take it further. You can resize your partitions  from a livecd with gparted.

Form a terminal you can also try,
```
sudo pm-hibernate
```I see you have moved to Xubuntu, how are  you finding it compared to that old release of Ubuntu you were  using?


nop i did not confuse it.. because i quit turning off the computer 7 years go, i only turn it off or restar it when necessary...

a  swap file of 4GB... isnt that too much? i mean.. my swap file always  have been 500 - 700mb and i never have had any inconvenience in other  buntus

---

### Post by anewguy on 2012-09-12
It's not a matter of how much swap is used when you're running - it's a matter of what is needed to hibernate.  Make it 2 times the size of your physical memory and a couple of K bytes extra for overhead.

BTW - you do understand that hibernate is for turning your system off (it will do so) but preserving the last active state.  Suspend will keep the power on.

---

### Post by Kharlo on 2012-09-12
> **anewguy said:**
> It's not a matter of how much swap is used when you're running - it's a matter of what is needed to hibernate.  Make it 2 times the size of your physical memory and a couple of K bytes extra for overhead.

BTW - you do understand that hibernate is for turning your system off (it will do so) but preserving the last active state.  Suspend will keep the power on.


Yes i understand the diferences between powering off, suspending and hibernation,and i always use hibernation, only when an installation or any upgrade ask for restart is the only time the computer goes off and on... otherway i always hibernation, in windows, and ubuntu.

you insist in the double of the ram... then how has the hibernation been working before if it always have had 2gb ram and about 600mb of swap file (in this machine)?
and i have gone to hibernation with lot of windows and programs opened and never have had problem with that swap size AT THE MOMENT OF HIBERNATION.


heading to a possible real cause...
today i was about to format an SD card (with Gparted) and i notice that Gparted showed me the swap partition as unknown,  its like if xubuntu was not recognizing the swap

---

### Post by anewguy on 2012-09-13
Done arguing - been there, done that, the reason I dropped my ubuntu member status (you don't just get that, you have to EARN it).  If you already know better, then don't ask.  And btw - hibernation DOES turn off every system I've ever seen.  You should read up on hibernation and the recommendations for that in Linux - you may find you've just been lucky.  But hey, you already know better.

---

### Post by mips on 2012-09-13
> **Kharlo said:**
> Yes i understand the diferences between powering off, suspending and hibernation,and i always use hibernation, only when an installation or any upgrade ask for restart is the only time the computer goes off and on... otherway i always hibernation, in windows, and ubuntu.

Hibernation turns a computer OFF. All it does is save the system state and RAM contents to swap. When you turn the computer on again it reloads that save state from disk.


> **Kharlo said:**
> you insist in the double of the ram... then how has the hibernation been working before if it always have had 2gb ram and about 600mb of swap file (in this machine)?
and i have gone to hibernation with lot of windows and programs opened and never have had problem with that swap size AT THE MOMENT OF HIBERNATION.


Well maybe previously Ubuntu used less RAM, every new release seems to require more system resources and maybe your RAM usage has finally exceeded the size of your swap space.


First lets confirm that hibernate is enabled,
[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)
To do that, use your favorite text editor to create /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla Add the following to the file and save:
```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

Make sure your file contains the above content. You have to edit the file using 'sudo' or be root.


Several things could be wrong with your swap setup so post the output of these commands here:

cat /var/log/pm-suspend.log
cat /etc/fstab
cat /proc/swaps
swapon -s 
cat /etc/initramfs-tools/conf.d/resume
sudo fdisk -l
sudo blkid


EDIT: Do me a favour and download this python script, [ps_mem.py]("http://www.pixelbeat.org/scripts/ps_mem.py") from [http://blog.xfce.org/2012/05/questions-after-the-4-10-release/](http://blog.xfce.org/2012/05/questions-after-the-4-10-release/) Don't worry it's safe, you can inspect it for yourself.

Open a few of your normal every day applications that you use, browser, terminal etc etc and then run that script in a terminal using "sudo python ps_mem.py" and **post the output here**. It will give you a better indication of your actual memory usage comapare to free, top etc.

---

### Post by mips on 2012-09-13
It's been disabled by default because it does not always work.[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

---

### Post by Kharlo on 2012-09-13
Abuut the hibernation..

I was too hasty with my explanation.

i know that it completly turn it off... i just wanted to mention that i always have chose hibernation (putting all the work/ram info int he hiberfil [windows])

but my explanation was preeetty bad
[****]("https://www.google.com.do/search?hl=es-419&client=firefox-a&hs=GAG&rls=org.mozilla:en-US:official&sa=X&ei=DTFSUJHpBoXf0QHx0YHwCg&ved=0CB0QvwUoAQ&q=hiberfil&spell=1")

---

### Post by Kharlo on 2012-09-13
reading about the problem (and before running the commands posted before [and that i barely understand])
i found this;
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

the past version of ubuntu i chose before this (in the past two days) i choose the encryption option wt the moment of the installation.

Could it be that the swap partition remained encrypted after formating the partition where the OS that encrypted the swap was?

what mentioned in the link, under the header:
**"Caveats"**

thats exactly my situation

---

### Post by Kharlo on 2012-09-13
More waisted time and effor...
i deleted everything again (cause i m kind of exhausted... of the shouldn't-be-so-complicated little things).
I created the necessary space and the 4gb for the swap... i installed the xubuntu12.04lts again and voila!  the same, in the first restart the xubuntu doesnt recognize the swap and of course neither the hibernation works....

---

### Post by Toz on 2012-09-13
Can you post back info about your swap file:
```
swapon -s
```

...your kernel command line:
```
cat /proc/cmdline
```

...and the contents of /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla:
```
cat /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```

---

### Post by Kharlo on 2012-09-13
> **Toz said:**
> Can you post back info about your swap file:
```
swapon -s
```...your kernel command line:
```
cat /proc/cmdline
```...and the contents of /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla:
```
cat /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```

i understood almost nothing

first you want the info i get after enterin "swapon -s" on the terminal?
after that i enter "cat /proc/cmdline", then i post the info again and so ?
that's it?

or do i have to write all that one after other in terminal?
(sorry i )

---

### Post by Kharlo on 2012-09-14
> **mips said:**
> 
Well maybe previously Ubuntu used less RAM, every new release seems to require more system resources and maybe your RAM usage has finally exceeded the size of your swap space.


No.
My previous OS was Ubuntu 12.04LTS, with the same system specs (2gb ram and 640mb swap, SHARED with puppy linux) and everything worked perfect., so it did not used less ram, it used MORE than this xubuntu.

---

### Post by mips on 2012-09-14
I'm beginning to think you don't want help and this is more of a gripe thread.

People have asked you questions & things to do which you ignore. We can't help you unless you help us, we can't smell what's wrong with your setup that's why we ask you questions and give you commands to execute and post the output of back here so we can get some sort of idea what's wrong.

Open a terminal, enter one line of commands at a time and whatever output that command returns post the output of that here. My previous post asked for quite a few things and for you to edit a certain file.

---

### Post by Elfy on 2012-09-14
> **Kharlo said:**
> ...
or do i have to write all that one after other in terminal?
...

Yes.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Kharlo on 2012-09-14
> **mips said:**
> I'm beginning to think you don't want help and this is more of a gripe thread.

People have asked you questions & things to do which you ignore. We can't help you unless you help us, we can't smell what's wrong with your setup that's why we ask you questions and give you commands to execute and post the output of back here so we can get some sort of idea what's wrong.

Open a terminal, enter one line of commands at a time and whatever output that command returns post the output of that here. My previous post asked for quite a few things and for you to edit a certain file.

i have got the feedback, the more you write the less user help you, the very little question i didnt answered was because they have turn something like n/a for me. for example the questions you asked me about checking if hibernation is enabled and about the configuration... after that i reinstalled the system 2 times, and even after that i notice the problem with the swap memory... so you are the geeks in this but I THOUGHT focusing to the swap-encryption issue was more relevant since A LOT OF USER are having this issue related to the three called hibernation/swap/encrypt.

And... since i already apologize due my looks-like-aguing-everything attitude... maybe cause by my blown-by-linux status..

haven't you ever think that i could just have forgotten some of the questions.. instead of thinking that i am intentionally ignoring it? (i am still human, so human that i apologize to "anewguy" while many other people would have started a kind of "personal" discussion)

---

### Post by Kharlo on 2012-09-14
> **mips said:**
>  we can't smell what's wrong with your setup....

for the better idea...

now the system is untouched fresh install with the very default setup, i wasnt' even connected to the internet at the moment of the installation

and i reinstalled it four times
with the 4gb swap (didnt worked)
with the 4gb swap and no encryption (didn't worked)
with the 4gb swap of swap (not shared by any other linux on my system) and didnt worked
with the 600mb of swap i always have used with ubuntu 12.04, without encryption, (didnt not worked)

---

### Post by Kharlo on 2012-09-14
> **Elfy said:**
> Yes.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.


the result for 

> swapon -s
userx@userx-HP:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    655356    0    -1
userx@userx-HP:~$

i dont know what is kernel command line but... here is the result after entering:
> cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=2b03d904-9144-4749-a134-dca230964822 ro quiet splash vt.handoff=7
userx@userx-HP:~$

and the result after;
> cat /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla> 
cat: /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla: No such file or directory
userx@userx-HP:~$

---

### Post by Elfy on 2012-09-14
```
cat: /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla: ***_No such file or directory_***
```

12.04 won't hibernate - it is disabled by default, see post #9

---

### Post by Kharlo on 2012-09-14
> **Elfy said:**
> ```
cat: /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla: ***_No such file or directory_***
```12.04 won't hibernate - it is disabled by default, see post #9

yes, i saw it..
and what can i do?

---

### Post by Elfy on 2012-09-14
read this again

> **mips said:**
> Hibernation turns a computer OFF. All it does is save the system state and RAM contents to swap. When you turn the computer on again it reloads that save state from disk.




Well maybe previously Ubuntu used less RAM, every new release seems to require more system resources and maybe your RAM usage has finally exceeded the size of your swap space.


First lets confirm that hibernate is enabled,
[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)
To do that, use your favorite text editor to create /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla Add the following to the file and save:
```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

Make sure your file contains the above content. You have to edit the file using 'sudo' or be root.


Several things could be wrong with your swap setup so post the output of these commands here:

cat /var/log/pm-suspend.log
cat /etc/fstab
cat /proc/swaps
swapon -s 
cat /etc/initramfs-tools/conf.d/resume
sudo fdisk -l
sudo blkid


EDIT: Do me a favour and download this python script, [ps_mem.py]("http://www.pixelbeat.org/scripts/ps_mem.py") from [http://blog.xfce.org/2012/05/questions-after-the-4-10-release/](http://blog.xfce.org/2012/05/questions-after-the-4-10-release/) Don't worry it's safe, you can inspect it for yourself.

Open a few of your normal every day applications that you use, browser, terminal etc etc and then run that script in a terminal using "sudo python ps_mem.py" and **post the output here**. It will give you a better indication of your actual memory usage comapare to free, top etc.

---

### Post by mips on 2012-09-14
> **Kharlo said:**
> for the better idea...

now the system is untouched fresh install with the very default setup, i wasnt' even connected to the internet at the moment of the installation

and i reinstalled it four times
with the 4gb swap (didnt worked)
with the 4gb swap and no encryption (didn't worked)
with the 4gb swap of swap (not shared by any other linux on my system) and didnt worked
with the 600mb of swap i always have used with ubuntu 12.04, without encryption, (didnt not worked)


I told you hibernation was disabled by default earlier on. 
I asked you to change a certain config file to enable it.

> **mips said:**
> 
First lets confirm that hibernate is enabled,
[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)
To do that, use your favorite text editor to create /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla Add the following to the file and save:
```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

Make sure your file contains the above content. You have to edit the file using 'sudo' or be root.

> **mips said:**
> It's been disabled by default because it does not always work.[https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

---

### Post by mips on 2012-09-14
> **Kharlo said:**
> yes, i saw it..
and what can i do?

```
gksu leafpad /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```

Copy and paste into leafpad text editor:
```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```

Save file & close, reboot.

---

### Post by Kharlo on 2012-09-14
thank for your patience
i have to go out and ill take this with me ill be doing that in a hour

---

### Post by Kharlo on 2012-09-14
> **mips said:**
> ```
gksu leafpad /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```***Copy and paste into leafpad text edito***r:
```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```Save file & close, reboot.

Ok !
i had no idea about what to do with that code, i dindt undestood this:>  use your favorite text editor to create....i working on that

---

### Post by Kharlo on 2012-09-14
> [Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yesdo i have to put my user where the asterisk is, or do i have to replace where it says, "user" or where it says "unix-user"

do i have to specify where to save it?

and what name should i put when saving it?

---

### Post by Toz on 2012-09-14
> do i have to put my user where the asterisk is, or do i have to replace where it says, "user" or where it says "unix-user"
No, don't change anything, just copy and paste

> do i have to specify where to save it?
No, the filename is specified with the first command you ran.

> and what name should i put when saving it?
Just save the file and reboot.

---

### Post by mips on 2012-09-18
So did it work?

---

