---
title: "boot order problems, dual boot W7 &amp; Ubuntu 12.04"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by Pizza Power on 2013-04-17
Hello! Please bear with me, I'm a huge noob. Here is my problem:

I installed Ubuntu on a seperate hard drive than my W7 install. I then used easy BCD to add Ubuntu to the windows boot menu. 

When I boot my computer it goes to the Windows Boot Manager. I select the Ubuntu option. That takes me to the Ubuntu boot manager where I can select windows 7. I haven't actually selected windows 7 using that option out of fear of breaking 
something, so I don't know if that option will actually work. I have selected windows 7 from the windows boot manager and it works fine. 

Is there a way to remove the windows 7 option from the Ubuntu menu, so that way when I select Ubuntu from the windows boot manager, it goes straight to Ubuntu?

---

### Post by sandyd on 2013-04-17
> **Pizza Power said:**
> Hello! Please bear with me, I'm a huge noob. Here is my problem:

I installed Ubuntu on a seperate hard drive than my W7 install. I then used easy BCD to add Ubuntu to the windows boot menu. 

When I boot my computer it goes to the Windows Boot Manager. I select the Ubuntu option. That takes me to the Ubuntu boot manager where I can select windows 7. I haven't actually selected windows 7 using that option out of fear of breaking 
something, so I don't know if that option will actually work. I have selected windows 7 from the windows boot manager and it works fine. 

Is there a way to remove the windows 7 option from the Ubuntu menu, so that way when I select Ubuntu from the windows boot manager, it goes straight to Ubuntu?

Windows is there because of OS Prober.
Run this:
```

gksudo gedit /etc/default/grub

```
Set
```
GRUB_DISABLE_OS_PROBER=true
```, save and run
```
 sudo update-grub
```

and the entry should now be gone :)

---

### Post by zrdc28 on 2013-04-17
Grub customizer should do it for you.


        sudo add-apt-repository ppa:danielrichter2007/grub-customizer
        sudo apt-get update
        sudo apt-get install grub-customizer

---

### Post by Pizza Power on 2013-04-17
> **sandyd said:**
> Windows is there because of OS Prober.
Run this:
```

gksudo gedit /etc/default/grub

```
Set
```
GRUB_DISABLE_OS_PROBER=true
```, save and run
```
 sudo update-grub
```

and the entry should now be gone :)

Thanks! Should I add that entry if mine doesn't have it? Here are the contents of my file

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
```

---

### Post by sandyd on 2013-04-17
> **Pizza Power said:**
> Thanks! Should I add that entry if mine doesn't have it? Here are the contents of my file

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
```

yep

---

### Post by fantab on 2013-04-18
Booting Windows from Ubuntu-GRUB will NOT harm your Windows install at all. 
You have another option, since you have two HDDs. You can change the HDD boot order in the BIOS to boot  the 'Ubuntu' HDD first and it will boot Ubuntu-Grub and you can choose your OS, simple. You don't even need EasyBCD. This way you can keep both Windows and Ubuntu pristine.

My two cents...

---

### Post by oldfred on 2013-04-18
+1 on fantab's suggestion to install grub to the Ubuntu drive.

You want each drive to boot without the other in case of issues with drives later. You then can change boot with one time boot key or BIOS boot order to boot other drive.

Just to be sure to choose Ubuntu drive and leave Windows boot loader in Windows drive.
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Also EasyBCD is using grub4dos as the Windows boot loader does not let you dual boot. So you add an entry to BCD to boot grub4dos to chain load to Ubuntu.
Where Ubuntu's grub2 boot loader normally chainloads back to Windows.

---

