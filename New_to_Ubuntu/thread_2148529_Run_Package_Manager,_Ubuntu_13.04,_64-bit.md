---
title: "Run Package Manager, Ubuntu 13.04, 64-bit"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by jackbn on 2013-05-25
I have a problem icon (red circle with horizontal bar, near upper right).
A click on the icon, produces the following message:

```

"An error occured, please run Package Manager from the right-click menu or apt-
get in a terminal to see what is wrong.
The error message was: 'Error Broken Count > 0'
This usually means that your installed packages have unmet dependencies."
```

I can't find Package Manager or the "right-click menu or apt-".
Can someone translate to English, and provide more guidance?

Thanks,
Jack

---

### Post by josephmills on 2013-05-25
run in your terminal (ctrl+alt+t)
```
sudo apt-get -qq upgrade  
```
what is the output ?  please paste it here

---

### Post by sudo san on 2013-05-25
Open the terminal and type:
```
sudo apt-get install -f
```

This should correct the dependencies.

---

### Post by josephmills on 2013-05-25
> [COLOR=#000000]Open the terminal and type:[/COLOR]
[COLOR=#000000]Code:

sudo apt-get install -f[/COLOR]
[COLOR=#000000]This should correct the dependencies.[/COLOR] yeah it will be it can also un-correct other packages that maybe install like forcing downgrades that can cause more headaches then it is worth. This is why I asked to see what was causeing this maybe it is 3rd party maybe it is ..... Hope that this helps.

---

### Post by sudo san on 2013-05-25
Ah, I see......

Apt does have super cow powers, but not all of them have good outputs on the system packages.

Thanks, I will keep that in mind when using that command.

---

### Post by ibjsb4 on 2013-05-25
You got me wondering about this.

>  -q, --quiet
           Quiet; produces output suitable for logging, omitting progress
           indicators. More q's will produce more quiet up to a maximum of 2.
           You can also use -q=# to set the quiet level, overriding the
           configuration file. [COLOR=#ff0000]Note that quiet level 2 implies -y, you should
           never use -qq without a no-action modifier such as -d, --print-uris
           or -s as APT may decided to do something you did not expect.[/COLOR]
           Configuration Item: quiet.


Taken from man apt-get

---

### Post by josephmills on 2013-05-25
> **ibjsb4 said:**
> You got me wondering about this.



Taken from man apt-get

```
apt-get upgrade --help | grep qq
  -qq No output except for errors



```

but yeah[FONT=arial black] -d[/FONT] should be used

---

### Post by ibjsb4 on 2013-05-25
> it can also un-correct other packages that maybe install like forcing downgrades 

And just to be sure everyone is on the same page, "-f install" does not stand for force install.  This is the command for "fix broken packages" and is recommended to fix unmet dependences.

#5
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by jackbn on 2013-05-27
```
bluebeard@bluebeard-desktop:~$ sudo apt-get -qq upgrade
[sudo] password for bluebeard: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bluebeard@bluebeard-desktop:~$
```

---

### Post by jackbn on 2013-05-27
```
bluebeard@bluebeard-desktop:~$ sudo dpkg --configure -a
Setting up linux-image-extra-3.8.0-22-generic (3.8.0-22.33) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Processing triggers for gconf2 ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 3.8.0.22.38); however:
  Version of linux-headers-generic on system is 3.8.0.21.37.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libaccount-plugin-1.0-0 (0.1.6bzr13.04.05-0ubuntu1.1) ...
Processing triggers for libglib2.0-0:amd64 ...
Setting up empathy (3.6.4-0ubuntu4.1) ...
Setting up nautilus-sendto-empathy (3.6.4-0ubuntu4.1) ...
Setting up linux-image-generic (3.8.0.22.38) ...
Setting up mcp-account-manager-uoa (3.6.4-0ubuntu4.1) ...
Setting up account-plugin-aim (3.6.4-0ubuntu4.1) ...
Setting up gnome-control-center-signon (0.1.6bzr13.04.05-0ubuntu1.1) ...
Setting up account-plugin-salut (3.6.4-0ubuntu4.1) ...
Setting up account-plugin-yahoo (3.6.4-0ubuntu4.1) ...
Setting up account-plugin-jabber (3.6.4-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-generic
bluebeard@bluebeard-desktop:~$
```

---

### Post by jackbn on 2013-05-27
So, it looks like there is still a problem.

Jack

---

### Post by matt_symes on 2013-05-27
Hi

It looks like you are missing the generic headers files but before i look for a fix, can we get some information about your system.

Please post the output of

```
cat /etc/lsb-release
```

```
dpkg -l | grep linux-headers
```

```
dpkg -l linux-headers-3.8.0-22{,-generic}
```

```
apt-cache search linux-headers-3.8.0-22{,-generic}
```

```
grep -r "^[^#]" /etc/apt/sources.list{,.d/}
```

Copy and paste the commands into the terminal and copy and paste the results back into your next post (highlught text in terminal->right click->copy).

Please paste the results between code tags to make it easier to read. It use code tags, highlight the text in your next post to put between code tags and hit the # button on the menu bar above where you type your text.

I'll edit your provious posts, to add code tags, for you.

Kind regards

---

### Post by jackbn on 2013-05-28
Thanks guys for all the help. 
I decided it was probably simpler, and more likely to work, just to reinstall Ubuntu. 
So, it's working fine now. 

I believe the problem I had, began when I shut down before a software update was finished.
There was NO indication it was still updating, and I thought it was complete.

I have now installed 13.04 three or four times, on a two different computers, with different motherboards and different CPUs, 
Each time, when the Optical Disk instllation was done, NOTHING happened.
The screen went black but the computer continued to run. This is not good. 
I waited at least 15 minutes before rebooting, to give any processes time to finish.
The installation should give some notice when it is complete.

---

