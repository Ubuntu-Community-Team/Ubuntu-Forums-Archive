---
title: "No sound on IBM R51"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by tdravin on 2008-05-01
Hi,

I am very new to Ubuntu, so far so good, except the sound.  I am running 8.04 on an IBM R51 laptop with an Intel 715 chipset.  The only place I can get any sound is when I am in the terminal and I scroll to the bottom, I get a beep.  I tried to go through the Comprehensive Sound Problem Solutions Guide, without much luck.  I can not get the system to recognize the sound device.  When I type aplay -l here is the result.

```
todd@todd-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Modem [Intel 82801DB-ICH4 Modem], device 0: Intel ICH - Modem [Intel 82801DB-ICH4 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
todd@todd-ubuntu:~$ 

```

Somehow it is seeing my modem as a sound device.  I get a similar result when I tried to run ALSA mixer.  I was unable to locate drivers for my onboard sound card on this chip set at the ALSA site.

I would appreciate any help or advise.

Thanks,
Todd

---

### Post by spiderbatdad on 2008-05-01
I think the good news is your card is detected. Try this. Run the command: 
```
asoundconf list
```
You should see an identifier similar to that shown by aplay -l.

Next run command: ```
asoundconf set-default-card Parameter
```
Where "Parameter" is the result of the first command, 'asoundconf list.'
Use appropriate case for letters.
Reboot computer.

---

### Post by tdravin on 2008-05-01
Thanks for the response, the only result to asoundconf list is the Modem.

```
todd@todd-ubuntu:~$ asoundconf list
Names of available sound cards:
Modem
todd@todd-ubuntu:~$ 

```

---

### Post by scottmuz on 2008-05-01
Do you have installed linux-ubuntu-modules-2.6.24-16-generic (or whichever module applies to the kernel you are running).

Installing this resolved my sound card problem.

---

### Post by spiderbatdad on 2008-05-01
```
asoundconf set-default-card I82801DBICH4
```

Reboot.

---

### Post by tdravin on 2008-05-01
I reloaded linux-ubuntu-modules-2.6.24-16-generic and tried asoundconf set-default-card I82801DBICH4.  Neither seemed to have an effect.

---

### Post by tdravin on 2008-05-02
I tried a couple of the ideas from the other thread about laptop sound without sucess.  Here is a result of lspci.  It doesn't seem as if my sound card is being recognized at all.

```
todd@todd-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

```

Any other ideas?

---

### Post by tdravin on 2008-05-02
I started to suspect a harware problem, so I pulled the keyboard off, didn't really change anything just made sure all the connectors were good.  When I restarted the sound was fine.  Unreal!!!!

Thanks for all the help.

---

### Post by tdravin on 2008-05-02
OK maybe not.  Next boot, no sound and can't see sound card.  This laptop worked fine with XP, so I really don't think it is hardware.  What could cause an intermittant sound problem like this????

please help!!

---

### Post by spiderbatdad on 2008-05-02
could you copy ```
dmesg
``` into a text file, then right click the file and select 'archive.' Upload the archive here with the manage attachment tool below this reply window.

---

### Post by tdravin on 2008-05-02
Here it is, I wasn't able to copy the entire file as the terminal only allowed a set number of lines.  I am sure there is a simple command to give one page at a time.  HMMMMM :confused:

Todd

---

### Post by spiderbatdad on 2008-05-02
```
dmesg | more
```

---

### Post by tdravin on 2008-05-02
Thank you, I had just figured out how to get the terminal to display more lines.  Here you go.

---

### Post by spiderbatdad on 2008-05-02
lot of errors. I suggest your edit you kernel line to match mine. I, too use a thinkpad. I'm not sure it will solve your sound issue, but maybe. I use the previous kernel. Hardy on 2.6.22-14-generic, so my sound works. Anyway, editing this file should speed up your boot time considerably, and possibly fix some of your hardware issues.

The file to edit id /boot/grub/menu.lst. Open it with root user privileges like so: ```
gksu gedit /boot/grub/menu.lst
```scroll down to the section that looks like this:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```

change yours to match mine at the end of the line that begins with the word 'kernel.' I have highlighted the changes, above.
Save the file and reboot. Then run the command:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Unless you have made changes to graphics setting that you don't want to alter.

Reboot and upload another dmesg if you like. You may find that you're going to need previous kernel modules to get sound...maybe not, though.

---

### Post by almabeck on 2008-05-02
Spiderbatdad, I've got the same problem on my Dell Inspiron 1420. Have tried a number of things suggested on this forum (I have a list, if that would help), to no avail. I've been trying what you've advised here--no luck so far. [And can't figure out how to get the whole output of dmesg to copy, so I can't send you that yet.] Any suggestions that might help me? As you can probably guess, I know almost nothing about this!

---

### Post by spiderbatdad on 2008-05-02
> **almabeck said:**
> Spiderbatdad, I've got the same problem on my Dell Inspiron 1420. Have tried a number of things suggested on this forum (I have a list, if that would help), to no avail. I've been trying what you've advised here--no luck so far. [And can't figure out how to get the whole output of dmesg to copy, so I can't send you that yet.] Any suggestions that might help me? As you can probably guess, I know almost nothing about this!

I generally use the gnome terminal. Applications>>accessories>>terminal.
Run the command...start at the bottom, holding the left mouse button and drag the mouse to the beginning of the field...thus highlighting all the text. Then right click in the terminal and select 'copy.'  I open the gedit text editor...Accessories>>Text Editor, Right click in the page and select, "Paste." Then save the file. The boot parameters I suggested here are not a solution to sound issues. The OP had many errors, and I suspect hardware problems with other devices,,,like touchpad, as well as a long boot time. 

As I said the only solution I have found to undetected soundcard in Hardy is to use the previous kernel. And unfortunately I don't have a simple solution to downgrading, other than installing an older release. I had Hardy in Alpha1 release. It used the same kernel as Gutsy. As upgrades arrived, I received new kernels, but retained the old. Apparenly the previous kernel isn't even in synaptic, so IDK where to get it. It is 2.6.22-14-generic.

---

### Post by tdravin on 2008-05-02
Here is the new dmesg file, still lots and lots of errors and still no sound.  



Almabeck: go into terminal and right click.  Hit edit current profile.  Click on scrolling and change scrollback to a larger number.  Then type dmesg . Copy the results, open the text editor, paste and save.  Go to the file, right click and hit create archive.  Upload the archive by hitting reply and then go ad advanced.  Below the reply window, is a button that says manage attachments.

Todd

---

### Post by almabeck on 2008-05-02
Well, my son is right--I'm learning a lot just from trying to fix this! Thanks for teaching me how to copy a large file in the terminal.

---

### Post by tdravin on 2008-05-02
I just rebooted using kernel 2.6.22-14-generic.  Still no sound.  Here is the dmesg, file booting with this kernel.

:)Todd

---

### Post by spiderbatdad on 2008-05-02
> **tdravin said:**
> Here is the new dmesg file, still lots and lots of errors and still no sound.  



Almabeck: go into terminal and right click.  Hit edit current profile.  Click on scrolling and change scrollback to a larger number.  Then type dmesg . Copy the results, open the text editor, paste and save.  Go to the file, right click and hit create archive.  Upload the archive by hitting reply and then go ad advanced.  Below the reply window, is a button that says manage attachments.

Todd

Looks better though. You have some usb device plugged in, but hot plugging doesn't seem to be working. Maybe boot once without the device. Alsa modules installed. Just not sure what to suggest at this point. Try selecting Alsa under all the sound settings. In Preferences>>Sound. Maybe removing pulseaudio through synaptic. That would try to remove Ubuntu desktop meta package...probably not a big deal. You could also surf over to 
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)  and post there...in a subsequent post, upload your dmesg. They handle bugs and workarounds. If you can find Hardy Alpha1 anywhere it uses the previous kernel. The when update manager does the upgrade, you have  both kernels in menu.lst and you can boot from the earlier kernel.

---

### Post by spiderbatdad on 2008-05-02
> **tdravin said:**
> I just rebooted using kernel 2.6.22-14-generic.  Still no sound.  Here is the dmesg, file booting with this kernel.

:)Todd

On this kernel, check the sound settings like this:[http://ubuntuforums.org/showthread.php?t=510376](http://ubuntuforums.org/showthread.php?t=510376)
 Or make sure Alsa is selected under preferences>>sound.
If that still fails, run asoundconf set-default-card again.

---

### Post by ihatejoefitz on 2008-05-05
Try muting the external amp through alsamixer.  This is what worked for my Intel 82801DB-ICH4.

---

