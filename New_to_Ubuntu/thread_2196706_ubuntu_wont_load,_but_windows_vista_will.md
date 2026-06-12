---
title: "ubuntu wont load, but windows vista will"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by albost58 on 2013-12-30
[FONT=arial]i installed ubuntu alongside windows vista. when i boot up i get a menu with vista and EaseUs but no ubuntu.  i downloaded boot repair and booted from it. i chose repair option but still only vista.  i found this file while using boot repair, hope it helps.

# If you change this file, run 'update-grub' afterwards to update[/FONT]
[FONT=arial]# /boot/grub/grub.cfg.[/FONT]
[FONT=arial]# For full documentation of the options in this file, see:[/FONT]
[FONT=arial]#   info -f grub -n 'Simple configuration'[/FONT]

[FONT=arial]GRUB_DEFAULT="Windows Vista (loader) (on /dev/sda1)"[/FONT]
[FONT=arial]#GRUB_HIDDEN_TIMEOUT=0[/FONT]
[FONT=arial]GRUB_HIDDEN_TIMEOUT_QUIET=true[/FONT]
[FONT=arial]GRUB_TIMEOUT=10[/FONT]
[FONT=arial]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX_DEFAULT="[/FONT][FONT=arial]qu[/FONT][FONT=arial]iet splash"[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX=""[/FONT]

[FONT=arial]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT]
[FONT=arial]# This works with Linux (no patch required) and with any kernel that obtains[/FONT]
[FONT=arial]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT]
[FONT=arial]#GRUB_BADRAM="0x01234567,[/FONT][FONT=arial]0xfef[/FONT][FONT=arial]efefe,0x89abcdef,[/FONT][FONT=arial]0xefefefef"[/FONT]

[FONT=arial]# Uncomment to disable graphical terminal (grub-pc only)[/FONT]
[FONT=arial]#GRUB_TERMINAL=console[/FONT]

[FONT=arial]# The resolution used on graphical terminal[/FONT]
[FONT=arial]# note that you can use only modes which your graphic card supports via VBE[/FONT]
[FONT=arial]# you can see them in real GRUB with the command `vbeinfo'[/FONT]
[FONT=arial]#GRUB_GFXMODE=640x480[/FONT]

[FONT=arial]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT]
[FONT=arial]#GRUB_DISABLE_LINUX_UUID=true[/FONT]

[FONT=arial]# Uncomment to disable generation of recovery mode menu entries[/FONT]
[FONT=arial]#GRUB_DISABLE_RECOVERY="true"[/FONT]

[FONT=arial]# Uncomment to get a beep at grub start[/FONT]
[FONT=arial]#GRUB_INIT_TUNE="480 440 1"[/FONT]

---

### Post by Bucky Ball on 2013-12-30
Welcome. Not a lot, but BootRepair will create a boot.info file. Could you do that and post the link to it here so we can have a closer look at what you have setup, please?

I'd be guessing, but there could be some conflict with EaseUS.

When you boot up it sounds like you are getting the Win boot loader and grub has nothing to do with it.

---

### Post by albost58 on 2013-12-31
paste.ubuntu.com/6666909 here you go. EaseUs came long after the issue. ive been trying for awhile. ive installed ubuntu twice. first time it would only boot to ubuntu, i found in the forum a command involving grub and updating. then when i rebooted i only got vista. so i formatted ext4 partition and installed ubuntu again and this time in boot repair there was an option where to place boot and i chose windows. now for the first time i got the menu to load the OS but only vista showed up and boots to vista now but not ubuntu. now is when i installed the EaseUs and backed up my vista partition just precautionary. if any thing else i can get just say so and thanks so much for the help. im new with all this but i really like the feel of ubuntu and would like to explore it some more.:P

---

### Post by oldfred on 2013-12-31
Do not know EasUS and what it may have done.
Better link.
[http://paste.ubuntu.com/6666909/](http://paste.ubuntu.com/6666909/)

Does Vista still boot ok? It only shows two of the three normal Windows boot files.

Your grub configuration has a setting to boot Vista as default which is ok, but you should get menu and be able to choose Ubuntu.

Never install grub to Windows as Windows always has to have its boot code in its partitions. But you do not show that you actually did that. Grub is in MBR and you should get grub menu first, after 10 seconds it will boot Vista by default.

---

### Post by Cowboy84 on 2013-12-31
I had similar problems, I just started over (got rid of the Ubuntu partition) then re downloaded the Ubuntu, used UltraIso to burn to a usb and then restarted the computer to install Ubuntu, didn't have that problem again. The only diffrence is the program I used to burn the USB.

---

### Post by albost58 on 2013-12-31
i power on and it goes to a screen offering vista i can wait or click on it and vista boots fine and works fine.  cant that file be edited and a menu item added so it will know ubuntu is there and boot it?  my last install of ubuntu the partition for it was already there from original install. i just formatted it and re-installed ubuntu. i may do as you say and delete the partition and start over if no resolution is found. thanks everyone, any advice before i delete and re-install?

---

### Post by oldfred on 2013-12-31
You should be seeing entries like this, Boot-Repair shows you have Ubuntu.

menuentry 'Ubuntu, with Linux 3.8.0-29-generic'

---

### Post by albost58 on 2014-01-01
ive been using 12.04.3 so i attempted using 13.10. i formatted and installed. i have boot options to windows and ubuntu. problem solved:p:p:p.

---

### Post by Bucky Ball on 2014-01-01
Good news. Please mark thread as solved by following the instructions in my signature.

Also good news is that 13.10 is directly upgradeable to 14.04 LTS when it comes out next April. That has five years support (13.10 has nine months).

---

