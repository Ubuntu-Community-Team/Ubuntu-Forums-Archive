---
title: "Partition problem"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Dave Houghton on 2008-10-26
Hello Everyone
I've just installed from a "Live CD" Ubuntu 8.04/EMC2 onto a computer with an older verion of Sherline's BDI EMC, nothing else is on the computer. When the computer boots up it only shows me Ubuntu 8.04 to run. It did partition the hard drive and I moved the "slider" to aprox 25% old EMC, 75% new EMC2 the drive is 40GB. Any ideas how I can make  the computer find the old EMC

Dave

---

### Post by phidia on 2008-10-26
Post the output of "fdisk -l" please.

---

### Post by Dave Houghton on 2008-10-26
Hi
"fdisk -l"  = no output, nothing
regards
Dave

---

### Post by baddnady23 on 2008-10-26
do "sudo fdisk -l"

and enter your password when prompted

---

### Post by Dave Houghton on 2008-10-26
Hi 
What a pain!
I don't have a printer conected to that computer. I tried to copy it to a floppy and print it on this computer, didn't want to copy. I'm tired it's past 4 in the morning here I've been at this since 9'0 clock this morning - thats 19 hours I've had enough.
Thanks for your help so far, I'll get up in the morning refreshed and ready to go. I do appreciate your time and effort, but it's time for me to go to bed.
Best wishes until tomorrow.
Dave

---

### Post by utnubuuser on 2008-10-26
having the same problem with a fresh Xubuntu install.

During install, the other partitions were recognized as per the usual "would you like to import settings from any other sytems...", but afterwards the other disks/partitions aren't listed in the file browser or desktop.
Been looking for the full command to mount the other partitions/disks, because I can find them through sudo fdisk -l.

---

### Post by phidia on 2008-10-26
If you know the designation of the partitions you can mount with "sudo mount /dev/sda1 /mnt/sda1"
You need to create the mount point with "sudo mkdir /mnt/sad1" and of course use the correct partition designation the above is just an example.

---

### Post by starcannon on 2008-10-26
When you need to transport output of a command line command, do so like this:
```
sudo fdisk -l > ~/Desktop/fdisklist.txt
```You will now find a nice little text file named fdisklist.txt on your Desktop, transport it and use it how you wish with any text editor you wish.

GL and have fun.

p.s. there are other ways, you could copy paste output into a newly created text document for instance, or even dump the output into an html document just use .html file extension instead of .txt, experiment and have fun.

---

### Post by Dave Houghton on 2008-10-27
Hi
I'm back. Hope you understand it!
dave@dave-desktop:~$ sudo fdisk -l > ~/desktop/fdisklist.txt
bash: /home/dave/desktop/fdisklist.txt: No such file or directory
dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab07ab07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        1166     9261472+  83  Linux
/dev/sda3            4736        4865     1044225   82  Linux swap / Solaris
/dev/sda4            1167        4735    28667992+   5  Extended
/dev/sda5            1167        4582    27438988+  83  Linux
/dev/sda6            4583        4735     1228941   82  Linux swap / Solaris

Partition table entries are not in disk order
dave@dave-desktop:~$

---

### Post by starcannon on 2008-10-27
Looking at your output I see two *nix installs on there, and 2 swap partitions(you only need one btw, it'll handle both *nix operating systems). When you Press Esc at the Grub load screen does your other OS not show up in the lists? If not, then a bit of Grub Wizardry should do the trick as it appears that it is still there.

Starcannon

P.S. Linux is Case Sensitive, so:
```
 dave@dave-desktop:~$ sudo fdisk -l > ~/desktop/fdisklist.txt
```is not the same as:
```
 dave@dave-desktop:~$ sudo fdisk -l > ~/Desktop/fdisklist.txt
```if you look in /home/dave or ~/ you will see a folder in there called Desktop, thats where the command sends the txt file.
GL and have fun

---

### Post by Dave Houghton on 2008-10-27
Hi
Very sorry about that 'D' the older I get the dumber I get.
When the computer boots up I get the following:
Ubuntu 8.04,Kernel 2.6.24-16-rtai
Ubuntu 8.04,Kernel 2.6.24-16-rtai (recovery mode)
Ubuntu 8.04,memtest86+
If I press 'c' I get
grub> pressing Esc takes me back to the screen before I pressed 'c'
The other OS do not show.
Is that what you were asking for, because not sure what a grub load screen is.
Thanks Dave

---

### Post by caljohnsmith on 2008-10-28
Please post the following so we can see your Grub menu configuration, and also which partition Hardy is in:
```
cat /boot/grub/menu.lst
 mount | grep " / " | awk '{print $1}'
```
So is the EMC OS that you refer to this one:

[http://www.linuxcnc.org](http://www.linuxcnc.org)

---

### Post by Dave Houghton on 2008-10-28
Hi
It's seems I am causing a lot of trouble, I am really very sorry, I know it's mainly down to me and my lack of computer knowledge. If you could bear with me I would be gratefull.
First the code: I cannot print on that computer (no printer connected) but I can save it to the Desktop, transfer it to this computer and post it.
I am putting the code in Terminal. Do I put the code in one long line or do I press enter after .../menu.txt  if I do press enter the reply is: no such file or directory. If I put the code in one long line the reply is the same: no such file or directory. I'm doing this wrong arn't I.
The EMC OS is Linux yes, it came from Sherline as BDI (debian version) with the CNC mill.
Sorry I am such a pain in the butt. If you feel I'm a bit of a lost cause I understand, I really do.
Regards Dave

---

### Post by starcannon on 2008-10-29
Run [caljohnsmith]("http://ubuntuforums.org/member.php?u=530779") 's codes in 2 separate lines. 

Don't worry, your questions are fine, thats what the forums are for :) so keep smiling, and so long as you don't make any rash moves, I think you'll find a solution that lets you have your cake and eat it to, be patient with yourself (we will be).

I've been up all night trying to delve into the mysteries of bash scripting and python, so for now just giving you a boost; I'll be back refreshed here in about 5~8 hours, and see if I can help you get on the road to technological nervana.

GL and keep truckin like the do-dah man.

---

### Post by Dave Houghton on 2008-10-29
Hi Starcannon

Thanks for all your support and kind words, really appreciated. I won't do any thing rash, I'll just wait fot the next instructions. Also taking it slowly one step at a time helps me to understand better. I have plently of time and patience, so please don't rush yourself.
Best wishes 
Dave

---

### Post by Dave Houghton on 2008-10-29
Hi
Ran caljohnsmith's codes as below:

dave@dave-desktop:~$ cat /boot/grub/menu.1st > ~/Desktop/menu1st.txt
cat: /boot/grub/menu.1st: No such file or directory
dave@dave-desktop:~$  mount | grep " / " | awk 
dave@dave-desktop:~$ 

It seems I'm doing something wrong.

Regards 
Dave

---

### Post by ajgreeny on 2008-11-03
That's because it is ```
cat /boot/grub/menu.lst
```ie LST, but lower case at the end.  A very common mistake, but one that can be very frustrating for new users.  Try again with the correct code.

---

### Post by Dave Houghton on 2008-11-03
Hello ajgreeny
Well I'll be blowed - Thank so much,and below is what I got:
dave@dave-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1ac72eca-c738-47e0-98ed-ce78db1a42f3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-rtai
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-rtai root=UUID=1ac72eca-c738-47e0-98ed-ce78db1a42f3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-rtai
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-rtai (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-rtai root=UUID=1ac72eca-c738-47e0-98ed-ce78db1a42f3 ro single
initrd		/boot/initrd.img-2.6.24-16-rtai

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
dave@dave-desktop:~$ 

Hope it helps, means zip to me,
Like the hat!
best wishes from South Africa

---

