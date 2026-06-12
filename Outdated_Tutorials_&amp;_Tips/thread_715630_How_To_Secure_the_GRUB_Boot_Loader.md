---
title: "How To: Secure the GRUB Boot Loader"
date: 2008-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by munkyeetr on 2008-03-05
**NOTE: This is an older tutorial and is focused towards GRUB 0.97, not Grub2**

After you have installed Ubuntu (or some other distributions that use Grub as their boot loader*), there are a few extra steps that you can take to ensure that your Linux installation is more secure.

The first section explains the insecurities of the boot menu and the second section explains how to secure it.

[SIZE="1"]* ArchLinux reportedly doesn't have this issue.[/SIZE]

[SIZE="3"]**1. The Problem**[/SIZE]
[COLOR="Red"]**By default, anyone with physical access to your system has the ability to reboot the machine and gain administrative (root) access to your file system. No authentication is needed.**[/COLOR] :shock:

The GRUB boot menu you see after a clean Ubuntu install looks like this:

[IMG]http://i28.tinypic.com/308llcy.jpg[/IMG]

**NOTE:** *You may see additional entries if you are dual-booting another operating system.*

This menu acts as follows, if you select:
[LIST]
[*]the first entry (default), you will boot to your Ubuntu login screen
[*]the second entry (recovery mode) you will boot into a root shell, which allows you full administrative access to your system
[*]the third entry (memtest32+), you will boot into a memory testing application. (*this entry will be ignored for the remainder of this tutorial, as I am not aware of any security issues this may pose*)
[/LIST]

There are two issues with this menu that make it insecure:
[LIST]
[*]the recovery mode entry [COLOR="Red"]**boots into an administrative (root) shell with full access to your system. It does this with no authentication**[/COLOR]. (in the wrong hands, this could lead to stolen or deleted data, or the entire operating system could be destroyed)
[*]the default entry [COLOR="Red"]**can be made as insecure as recovery mode**[/COLOR] simply by passing the word **single** as a kernel parameter. Again, no authentication is needed to perform this action.
[/LIST]

**How Are Kernel Parameters Passed Via The Boot Menu?**
We already know that recovery mode boots into a root shell with no kernel parameters or authentication needed (*if you don't believe it, give it a try*), but how do we make the default entry perform the same action.

As simple as this:

[LIST=1]
[*]Highlight the default entry in the boot menu
[*]Press '**e**' to edit boot commands
[*]Highlight the line that begins "**kernel /boot/vmlinuz...**", and press '**e**' again
[*]Type " **single**" (that is a SPACE and the word **single**, without the quotation marks added to the end of the existing string)
[*]Press **Enter**
[*]Press '**b**' to boot
[/LIST]
We have just booted into an administrative (root) shell, exactly as we would have had we selected the recovery mode entry.

I have just demonstrated that, by default, anyone with physical access to your computer can gain root privileges by simply rebooting and manipulating the Grub boot menu. That's the bad news. The good news is that it is easy to fix!

[SIZE="3"]**2. The Fix**[/SIZE]

(**NOTE:** *I am writing this tutorial from the perspective of an Ubuntu 7.10 user, but the premise is the same on other distributions. Feel free to substitute your favorite Command Line and Text Editor programs as needed or as you see fit.*)

Boot to your desktop as normal, and open a Terminal window (**Applications** -> **Accessories** -> **Terminal**)

The GRUB boot menu configuration file is located at[FONT="Courier New"] /boot/grub/menu.ls[/FONT]t, so let's open that file up in our text editor. In the Terminal window type:
```
gksudo gedit /boot/grub/menu.lst
```
then enter your password when prompted and a file similar to this should open:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM.
Numbering starts from 0, and
# the entry number 0 is the default if the command is
not used.
#
# You can specify 'saved' instead of a number. In this
case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use
'savedefault' or your
# array will desync and will not let you boot your
system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically
booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the
menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable
all interactive editing
# control (menu entry editor and command-line)  and
entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after
AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers
will be modified
## by the debian update-grub script except for the
default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels
use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can
be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e6e6fe4f-6c0f-46e5-8a40-b45225220a85
ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic
boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot
options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot
option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen
boot option
# xenhopt=

## Xen Linux kernel options to use with the default
Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot
options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the
menu.lst
## only counts the first occurence of a kernel, not
the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default
booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default
options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=e6e6fe4f-6c0f-46e5-8a40-b45225220a85 ro
quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery
mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=e6e6fe4f-6c0f-46e5-8a40-b45225220a85 ro
single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
(**NOTE**:*Again, you may see additional entries if you are dual-booting another operating system.*)

We won't need to worry about most of this file, but there are 2 sections that need to be edited to secure the boot loader. We will edit the password section first, but before that we must take one detour and create an encrypted password:

Select the Terminal window and open a new tab (**File** -> **New tab**).

In the new tab type:
```
grub
```
and a grub> prompt will open. At the grub> prompt type:
```
md5crypt
```
then type the password you want to use to secure your boot loader. Grub will display an encrypted string. This is your password in encrypted form.

[IMG]http://i25.tinypic.com/w88f2c.jpg[/IMG]

Highlight the encrypted string, then copy (**SHIFT**+**CRTL**+**C**) it to the clipboard.

Then type:
```

quit

```
to exit the Grub prompt.

Now, let's go back into the menu.lst file that is open in your text editor, and find the password section that looks like this:
```

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

```
and add a new line directly below as follows (Paste the encrypted string from the clipboard (**Edit** -> **Paste**):
```

password --md5 <encrypted password>

```

where <*encrypted password*> is the password you created in the last section.

So, your password section should now look like this:
```

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
**password --md5 $1$xcLiO$4czPGUKIdo5e8Vi3nIpme0**

```

:KS Half of our problems are now fixed (or they will be once the file is saved), as you can no longer pass kernel parameters without supplying your password first.

We still need to deal with the ability to boot into recovery mode without a password because, remember...we don't need to change any kernel parameters to do that, we just select the entry and press Enter.

Here's how we fix that:
In the menu.lst file, find the menu options that looks like this (they should be at the bottom of the file):
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=e6e6fe4f-6c0f-46e5-8a40-b45225220a85 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=e6e6fe4f-6c0f-46e5-8a40-b45225220a85 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
and add the **lock** command to the recovery mode entry so it looks like this:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
**lock**
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=e6e6fe4f-6c0f-46e5-8a40-b45225220a85 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

```

The lock command requires that a password be entered before you can boot to that entry. You can add the lock command to any entry in the Boot menu if you wish to restrict who can boot to it.

Now save the menu.lst file (**File** -> **Save**) and exit (**File** -> **Quit**)

As an added precaution, it's also a good idea to change the permissions of the menu.lst file so that only root (and you through the sudo command) can view the file. By default it is readable and writeable by root (the owner), and readable by everyone else, as demonstrated by typing the following in a terminal window:
```

ls -la /boot/grub/menu.lst*

```
(**NOTE:** *I use the * here because there is also a backup of the file in the same directory*.)

To make the desired change type the following at the terminal window:
```

sudo chmod 600 /boot/grub/menu.lst*

```
Enter your password if prompted, then rerun:
```

ls -la /boot/grub/menu.lst*

```
to verify that the desired changes have been made.

[SIZE="3"]**3. Verifying the Changes**[/SIZE]

:KS Congratulations, we are done securing the GRUB boot loader! Now let's reboot and look at the what a difference our changes have made.

When we reboot, we see the boot menu has changed a little

[IMG]http://i27.tinypic.com/28bb4zm.png[/IMG]

it now advises us to press Enter to boot the selected OS, or press '**p**' to enter a password and unlock the next set of features. We can still boot into the default entry as normal, but we cannot add kernel parameters without first entering our password.

Likewise, if we try to boot into recovery mode without first entering our password we are greeted with an error:

[IMG]http://i27.tinypic.com/jrenab.png[/IMG]

which is exactly what we want to see. Now our Linux box is a *little more secure* (see note below) against threats by people who have physical access to our machine.

**Please Note**: While this procedure makes your system a little more secure it does not prevent someone who has time to physically work at your machine from getting past it. This procedure makes it harder and slows an opportunistic attacker down, but given even ten minutes unattended they can get past this by booting through a Live CD or removing the hard drive and putting it into another computer. This is meant more to prevent someone from doing damage in under 60-seconds. To slow them a even a little further make sure to remove CD from your boot options in the system BIOS. Be aware, that this can also easily be bypassed by someone who is left unattended with your computer.

While I won't cover it in this how-to, you may want to also look into disk encryption to better safeguard your data.

---

### Post by kaiju on 2008-03-10
neat idea! i'm just surprised the issue doesn't get addressed "officially".

this might be an ubuntu (or perhaps debian?) -specific problem though. i just checked on my computer (ubuntu and arch dual boot), and while ubuntu behaves just the way pointed out by you, in arch there doesn't seem to exist a way to get into any account without the appropriate password. even with the 'single' option passed to the kernel, the system will ask for the root password during bootup (it gives the choice between entering the root password or pressing ctrl+d, which makes the switch to runlevel 3, i assume, offering a standard login prompt).

i'm thinking that this is a big enough security issue that it should be corrected in the official release...

---

### Post by munkyeetr on 2008-03-10
I wonder if it is because Ubuntu doesn't actually make you create a root password, though I would think they would prompt for a valid sudo password.

I will add the Arch doesn't have this problem to the HowTo. Thanks.

---

### Post by kaiju on 2008-03-11
> **munkyeetr said:**
> I wonder if it is because Ubuntu doesn't actually make you create a root password, though I would think they would prompt for a valid sudo password.

my thoughts exactly. i'm definitely no expert in this, but it does seem to have to do with not having a regular (secured) root account.
if this really is the case, i don't think it would be that big of a deal to make the user have to add a root password at setup.
(after all, the difficulty of booting ubuntu in single user mode is pretty much the same as getting into the "administrator" account in windows xp...)

edit (one week later):
it seems that a bios password is the only way to secure a computer from people with physical access to it, since a live distro will give anyone booting it on any machine root access to anything on the computer's hard drives once they're mounted.

even with that, a secure root account might be a nice idea.
or, if that is considered unimportant, perhaps it should be made clear to the users that a standard ubuntu setup gives easy access to the root account, and that this can be a security issue in some cases.

---

### Post by lswest on 2008-04-02
Nice workaround for the recovery boot option, didn't know you could lock entries.  Thanks!  (useful for me, since i go to school with a few other linux users, who may very well just want to mess with me ;))

*EDIT* Also used it to secure my recovery partition for Vista ^^ (just for those wannabe hackers that do exist at my school...)

---

### Post by sammydee on 2008-04-09
I actually always viewed being able to boot into single user mode as a feature, not a bug.

Let's face it, if someone has physical access to your pc, you're pretty much already pwned. All they need to do is stick in a boot live cd or floppy and then thery can do whatever they want anyway.

Single user mode has saved me before a couple of times when I've forgotten my password or fubared my system so badly it wouldn't even get to multiuser mode.

Sam

---

### Post by milton1 on 2008-04-09
> **kaiju said:**
> 
it seems that a bios password is the only way to secure a computer from people with physical access to it, since a live distro will give anyone booting it on any machine root access to anything on the computer's hard drives once they're mounted.

even a bios password will not help if someone gets physical access. Simply pulling the CMOS battery will reset bios passwords. The best you can hope for is to slow down someone with physical access, and even then, ten minutes is all a good tech needs to get into your system.

---

### Post by sammydee on 2008-04-10
I can however see how this kind of security would be very useful in something like a library or cyber cafe, where the pcs might be configured not to boot from cd or floppy drive, and nobody is likely to get ten minutes alone to break the case lock.

In this particular case, the last thing you want is to hand the users root access. I can see the point the op is making. Maybe this should be included in the Ubuntu livecd installer, at least as an option for power users?

Sam

---

### Post by ukripper on 2008-04-10
nice one with encryption!

---

### Post by Ptero-4 on 2008-04-15
Wow. good ones.

---

### Post by M.G. on 2008-04-30
Thanks a lot. Nice job. Well explained. :grin:

---

### Post by Patsoe on 2008-04-30
> **kaiju said:**
> 
i'm thinking that this is a big enough security issue that it should be corrected in the official release...

As has been pointed out, anyone with physical access to your pc can boot from a LiveCD, mount your disks, then read all your data anyway. So by locking GRUB you only force them to bring a LiveCD with them...

If you don't want those people to be able to read your data, put it on an encrypted partition. Anyone who then wants to mount your disks will have to know a password, otherwise the partition will just look like random bits to them.

You can set up Ubuntu with strong encryption using the alternate installer. The setup thus created encrypts your data and all system files, except the /boot directory. So nobody can read your documents, nobody can alter binaries, but potentially they could still do something to /boot...

---

### Post by munkyeetr on 2008-04-30
You know, people keep coming and posting about how "if someone has physical access to your system, they can just blah blah blah, so it's a waste of time to secure the boot loader."

While they have a point to *some* degree, the reason I think this how-to is important is because:

1) it seems quite a few people don't know that the boot loader menu leaves their system wide open, and they should have the know-how to close it if they wish.

2) someone could certainly use a live cd (after they bypassed a bios password) to do whatever they wanted, but I think making them perform these steps and slowing them down is better than just saying "it's a waste of time" and allowing them to perform something as bad as rm -rf on root in under 60 seconds.

I've provided a how-to that makes your system a little more secure than the standard out-of-the-box- installation, and some people have found it useful. Other's do not, and that's their perogative.

I mean, we could also say that (while definitly hard and very labour intensive), people *could* crack your password given enough time or opportunity and have full access to your system, so why use a password at all? Because it makes it that much harder, that's why.

---

### Post by Patsoe on 2008-05-01
> **munkyeetr said:**
> 
1) it seems quite a few people don't know that the boot loader menu leaves their system wide open, and they should have the know-how to close it if they wish.

It's absolutely a good thing to provide that know-how. But people should also know how far that extra security goes. 

> 
2) someone could certainly use a live cd (after they bypassed a bios password) to do whatever they wanted, but I think making them perform these steps and slowing them down is better than just saying "it's a waste of time" and allowing them to perform something as bad as rm -rf on root in under 60 seconds.

Also true. But again, people should also know that the BIOS password can be reset by flipping the CMOS battery (opening the case ~ 60 seconds, too?) and getting around GRUB just takes a LiveCD (boot time ~ 200 sec?).

> 
I mean, we could also say that (while definitly hard and very labour intensive), people *could* crack your password given enough time or opportunity and have full access to your system, so why use a password at all? Because it makes it that much harder, that's why.
Well, setting a good user password really makes it *a lot* harder to break in over a network. The CMOS reset and the LiveCD only slow you down by what, a factor of ten at most? A good user password does not get broken in ten minutes. So that's a bit of an unfair comparison.

I didn't mean to ***** on your tutorial - if that's how I came across, please review my post. I just thought I'd add that if you're concerned about this kind of attack on your system, you might want to look into disk encryption. The Ubuntu installer makes that perfectly simple, and that really makes it that much harder to break in.

---

### Post by munkyeetr on 2008-05-01
Hey Patsoe,

Sorry if that seemed directed at you; it wasn't, though it was your post that made me finally say something. It also prompted me to do what I maybe should have done awhile ago, and that was to add a note at the bottom of the how-to about the issues you (and others) point out.

Thanks.

---

### Post by Gripp on 2008-05-01
what about booting from live CD and mounting the real linux partition and chroot to it?

i have two sides to that Q
the other is that i frequently need to do just that to run update-initramfs -u and get my normal system back a working condition... and i'm thinking i'm not the only one. 

so if anything done here DOES restrict this chroot, then how to bypass it?

edit: guess i should have read the other users first eh?!

so, okay then, is there a way to restrict the mount access? mount only if PW supplied kind of thing?
and guys, really he;s right about the time thing.  think about it.  even if you dont have a BIOS PW they still have to boot into the bios to change the boot order, reboot and then wait for the live cd to finish doing its thing.  which seems to me quite some time (my exp has been about 5 minutes)
and really, if you have a duel boot system, they could still use sysinternals little linux viewer program to see everything in your install.. just like we can look at and delete everything in our windows drive!
wow, now that i think about ti, rm-rf could be a two-fer in my case... ouch

---

### Post by Patsoe on 2008-05-01
Hi munkyeetr,

Thanks for that. Actually, now that I read back my first post, I'd like to apologise for that very dry reaction that seems full of implied criticism... in real life I would never stumble into a bar and start telling people I just met for the first time how they should drink their beer :)

Best!

---

### Post by chunlong on 2008-08-11
I really hope that Ubuntu at least explains this to people during install or something that people will be able to easily log on as root on their machine, otherwise have a default root password or grub password or something.

I know it doesn't make it dead secure, but it does make it a little more secure. Say I have my machine in my lounge, some guests come along and go, "Hey! He's running Ubuntu! Check this out!" and proceeds to change all my passwords or something. I mean, if I had a password then it means he needs a live CD or some sort, and though it doesn't mean he can't break into my machine, it's definitely less likely. Even if he does bother, I'd probably be around by then. In this way, it does make the machine more secure, if not completely secure.

I mean, why do people even bother to lock their doors at home? It's arguable that that would help. I mean, most house doors are not unbreakable. And alarms only means the people have less time to do what they want to do.

So arguing that it doesn't make it more secure just doesn't make sense to me. I know we're all entitled to our opinion, but I'm sure this can be a turn off to most people switching to linux/ubuntu. Even XP required people to type a password in recovery mode. Why not Ubuntu?

Typing a password does not make it harder to go into recovery mode. And how often do you forget a password?! If you forget your login password, odds are you hadn't used the machine for a long time, so it really is worth the effort to get a live CD.

I also don't understand why Ubuntu thinks we don't need a firewall, but that's a completely different story. Thanks so much for these kinds of posts! good work!

---

### Post by veNom_bz on 2008-08-26
> **chunlong said:**
> 
I also don't understand why Ubuntu thinks we don't need a firewall, but that's a completely different story. 

iptables is ever present.... and ufw is available as well.

kudos to the op :D

---

### Post by joelgsf on 2009-09-11
munkyeetr, congratulations! I finally meet someone sensible to this problem, which I also raised in another thread and could get almost only answers with that blah, blah, blah you mention.
I fully agree with you, the problem is not that the door exists, but that it is left open by default and an ordinaty desktop user is completely unaware of it. I think that Ubuntu Organization should be concerned with it.
Your tutorial is excelent and should be spread to all Ubuntu users.:D

---

### Post by heyyy on 2009-09-15
if i have the alternative install with encrypted lvm do i need to do this?

---

### Post by MikeJRamsey on 2010-01-03
Munkyeetr,
 Thank you.  Still works with Ubuntu 9.10 even though the screen details are slightly different.

Mike Ramsey

---

