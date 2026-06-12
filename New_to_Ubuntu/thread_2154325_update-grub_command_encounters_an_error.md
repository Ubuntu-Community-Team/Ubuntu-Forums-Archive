---
title: "update-grub command encounters an error"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by asadderandawiserman on 2013-06-14
I'm new to Ubuntu, only installed it yesterday, and I'm running it alongside Windows 7. The version I have installed is Ubuntu 13.04. I've been trying to edit the grub settings, so that it has a 5 second hidden timer in which I can press any key to open the grub menu, after which it will automatically boot Windows 7 if no key is pressed. I'm fairly sure that I've set the file /etc/default/grub correctly for these settings, but I'll post it here anyway, in case it's part of the problem.

> &#65279;# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=4
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


I then tried to run update-grub in the terminal, but every time I try, I get the same result:

> asadderandawiserman@joseph-AMILO-Li3910:~$ sudo update-grub
[sudo] password for asadderandawiserman: 
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found




It seems that this has not updated the grub effectively, because when I restart, it works exactly like it always has. I've had a look, but couldn't find any relavent threads, so I was wondering if anyone knew how to fix this?

---

### Post by Cheesemill on 2013-06-14
Have you somehow changed the name of the /etc/default/grub file or changed its permissions?

What's the output of...
```
ls -lha /etc/default/grub
```

---

### Post by asadderandawiserman on 2013-06-14
> **Cheesemill said:**
> Have you somehow changed the name of the /etc/default/grub file or changed its permissions?

What's the output of...
```
ls -lha /etc/default/grub
```

I haven't changed the name, but I did make myself the owner so that I could edit the file, before changing the ownership back to root. The output is:

```
-rw-r--r-- 1 root root 1.3K Jun 14 09:16 /etc/default/grub
```

---

### Post by oldfred on 2013-06-14
If it is back to root it should then work.

Better just to edit this way:
       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub

---

### Post by asadderandawiserman on 2013-06-14
> **oldfred said:**
> If it is back to root it should then work.

Better just to edit this way:
       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub

In future, I'll use that method to edit files, but although I've changed the ownership to root, update-grub still reacts the exact same way I mentioned in the first post. Is there any other reason it could be acting like this?

---

### Post by NikTh on 2013-06-14
Show the results again 

```
sudo grub-mkconfig -o /boot/grub/grub.cfg.new
```

---

### Post by asadderandawiserman on 2013-06-14
> **NikTh said:**
> Show the results again 

```
sudo grub-mkconfig -o /boot/grub/grub.cfg.new
```

```
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found
```

This is what I got.

---

### Post by sum1nil on 2013-06-14
As a last resort I believe you can reinstall grub on the had drive that you boot from although you may lose any changes you made.
For me it was 'grub-install /dev/sdb' since I boot from the 2nd sata drive. 
Please read 'man grub-install' before trying this. 
I would follow oldfred's advice in the future when changing important files. 

Take care.

---

### Post by oldfred on 2013-06-14
I do not see what is wrong, but sometimes the only fix is a reinstall. You only need to totally uninstall grub2 and reinstall it.

I might delete that file also before reinstalling if the uninstall does not work. 

If you can boot, you can skip the chroot part.

 chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Boot-Repair also has a helper to chroot & uninstall and reinstall.
While grub is uninstalled you will not be able to reboot, so make sure you have reinstalled before rebooting.


 # uninstall both grub legacy & grub2 reinstall grub2 and to sda
sudo -i
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub

---

### Post by asadderandawiserman on 2013-06-16
Thanks very much all of you, I got the update-grub to work, but it still doesn't seem to work properly. I set up the grub file in the same way I showed in the first post, then ran update-grub and restarted the computer, but it didn't work quite as I intended. As I explained in the original post, I wanted a 5 second hidden timer, then to load the default OS, Windows 7. What has actually happened, is when I turn on the computer, it flashes up 'Loading GRUB' for a fraction of a second, then there is a flash of GRUB-purple, before the computer boots Windows 7 normally. There doesn't seem to be a way to get to the GRUB menu, or to access the Ubuntu OS at all. So I have two problems:

1. What did I do wrong in the settings for grub which caused it to behave in this way and how can I fix it?

2. Is there any way I can access Ubuntu, because at the moment, my computer will only boot as described above, so I can only access windows 7.

Thanks!

---

### Post by Impavidus on 2013-06-16
1: You wrote:
> /usr/sbin/grub-mkconfig: 1: /etc/default/grub: &#65279;#: not found
Was this a direct copy-paste from your terminal? Because the third semicolon suggests that the problem is not that /etc/default/grub cannot be found, but that the # gives a problem. The # just starts a comment, but on closer inspection it appears to be U+ffef#, in other words, there is a zero width no-break space/byte order mark from [this]("http://en.wikipedia.org/wiki/Arabic_Presentation_Forms-B") Unicode section just before the #. This invisible character caused your problem. Any idea how it could have come up there? It appears you deleted it coincidentally.

2: You can boot from a live disk. I think you have to modify the file, chroot and update-grub, but as I never tried myself I can't be specific.
Edit: I'm not sure, but maybe boot repair can fix this kind of problem. Also see [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by oldfred on 2013-06-17
This setting says you never want to see the menu. Better to have some positive entry just to give time to use shift and get menu to appear.
 GRUB_TIMEOUT=0

      
 Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)


>  GRUB_HIDDEN_TIMEOUT - Hides the menu (but not splash) for the given time. To display the menu immediately, place a # symbol at the start of this line.
GRUB_HIDDEN_TIMEOUT_QUIET - False is supposed to present a countdown timer in the upper left corner of a blank (or splash image bg) screen. True leaves a blank screen (or splash) with no countdown timer visible.
GRUB_TIMEOUT= Starts the timer once the menu is displayed, if it is ever called up. Whether or not the menu is displayed is decided by the "GRUB_HIIDEN_TIMEOUT" line. 



---

### Post by asadderandawiserman on 2013-06-17
> **oldfred said:**
> This setting says you never want to see the menu. Better to have some positive entry just to give time to use shift and get menu to appear.
 GRUB_TIMEOUT=0

      
 Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

Thanks, I think I know what to do to fix the GRUB settings now, but I can't edit them until I can re-access the installed Ubuntu system. I've tried booting up from a Live CD, but it will only let me re-install, or use a trial version, not access the version I already have installed. Any ideas?

---

### Post by oldfred on 2013-06-17
We never edit this file. But there are exceptions.

 #Normally we do not directly edit grub.cfg. Edit from live-CD/DVD/USB. change sda5 to your install's partition.
mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

I think this is what you want to edit, find this section and change the set timeout to 10 like mine below:
> terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  [COLOR=#ff0000]set timeout=10[/COLOR]
fi
### END /etc/grub.d/00_header ###


---

