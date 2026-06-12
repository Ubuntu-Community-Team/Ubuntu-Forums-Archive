---
title: "Brightness keys stop to work after update :( &quot;unknow key code&quot;"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by macmus on 2013-07-05
Hi,

Recently I did load updates for ubuntu to Kernel 
```

Linux HP-EliteBook 3.8.0-26-generic

```
and as a result my Brigtness keys stoped to work :(. Even when reverting back to 
```

Linux HP-EliteBook 3.8.0-25-generic

```
I still have an issue. 
I did even try to install latest 3.10 version but it did not help at all :(

So far I was using following grub parameters to make it work:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"

```

This entry acpi_backlight=vendor seems to help me befofre, but now it does nothing...

When I press Fn+F8 Fn+F9 following entries are generated in dmesg:

```

[ 2141.368837] atkbd serio0: Unknown key pressed (raw set 2, code 0xc3 on isa0060/serio0).
[ 2141.368845] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[ 2141.491530] atkbd serio0: Unknown key released (raw set 2, code 0xc3 on isa0060/serio0).
[ 2141.491538] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[ 2141.564734] atkbd serio0: Unknown key pressed (raw set 2, code 0xc3 on isa0060/serio0).
[ 2141.564742] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[ 2141.672575] atkbd serio0: Unknown key released (raw set 2, code 0xc3 on isa0060/serio0).
[ 2141.672583] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[ 2141.848596] atkbd serio0: Unknown key pressed (raw set 2, code 0xa4 on isa0060/serio0).
[ 2141.848603] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[ 2141.931667] atkbd serio0: Unknown key released (raw set 2, code 0xa4 on isa0060/serio0).
[ 2141.931675] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[ 2141.998911] atkbd serio0: Unknown key pressed (raw set 2, code 0xa4 on isa0060/serio0).
[ 2141.998918] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[ 2142.087927] atkbd serio0: Unknown key released (raw set 2, code 0xa4 on isa0060/serio0).
[ 2142.087935] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.

```


quickly doing calculation

```

lech@HP-EliteBook:~$ xmodmap -pke | grep 195
keycode 195 = XF86Launch8 NoSymbol XF86Launch8
lech@HP-EliteBook:~$ xmodmap -pke | grep 164
keycode 164 = XF86Favorites NoSymbol XF86Favorite

```

and 

```

lech@HP-EliteBook:~$ xmodmap -pke | grep Brig
keycode 232 = XF86MonBrightnessDown NoSymbol XF86MonBrightnessDown
keycode 233 = XF86MonBrightnessUp NoSymbol XF86MonBrightnessUp
keycode 237 = XF86KbdBrightnessDown NoSymbol XF86KbdBrightnessDown
keycode 238 = XF86KbdBrightnessUp NoSymbol XF86KbdBrightnessUp

```

What happend ? 
Could anyone guide me how to fix this issue :(

I would much appreciate that.

Thanks!

---

### Post by macmus on 2013-07-05
As a workaround I'm using now xbacklight, but I want to previous FN keys back :(

but should they even be working with vendor settings?

I'm totaly confused now...

Please help,

---

### Post by Toz on 2013-07-05
What is the model number of your elitebook?

Can you try the acpi_osi=\"!Windows 2012\" kernel parameter? The relevant entries in /etc/default/grub should look like this:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!windows 2012\""
```
...(make sure you get the correct number of quote symbols in that last line).

Don't forget to run:
```

sudo update-grub
```
...and reboot.


Once rebooted, try the brightness keys again as well as posting back:
```

cat /proc/cmdline
```
...and
```

sudo lspci -vnn | grep -A15 VGA
```

---

### Post by macmus on 2013-07-05
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!windows 2012\""
```


before I do that.. May I ask what is a diffrence between GRUB_CMDLINE_LINUX_DEFAULT and GRUB_CMDLINE_LINUX ? my current grub looks like:



```

root@HP-EliteBook:~# cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="1>4"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor i8042.reset acpi_osi=Linux"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_SAVEDEFAULT="false"

```

---

### Post by Toz on 2013-07-05
There is no real difference in that the content from the two lines is combined. Traditionally, the default settings are left in GRUB_CMDLINE_LINUX_DEFAULT and any user-added parameters are put into GRUB_CMDLINE_LINUX.

For your setup, I would suggest:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!windows 2012\" pcie_aspm=force i8042.reset"
```

---

### Post by macmus on 2013-07-05
Hi did that and no change:(

```

BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=6c701ba7-077e-42fe-8b8d-375d78d02a5d ro "acpi_osi=!windows 2012" quiet splash pcie_aspm=force acpi_backlight=vendor i8042.reset i8042.nomux=1 vt.handoff=7

```


```

lech@HP-EliteBook:~$ sudo lspci -vnn | grep -A15 VGA
[sudo] password for lech: 
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device [103c:17df]
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at d4000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
	Subsystem: Hewlett-Packard Company Device [103c:17df]
	Flags: bus master, medium devsel, latency 0, IRQ 44
	Memory at d4720000 (64-bit, non-prefetchable) [size=64K]

```

---

### Post by Toz on 2013-07-05
> **macmus said:**
> Hi did that and no change:(

```

BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=6c701ba7-077e-42fe-8b8d-375d78d02a5d ro "acpi_osi=!windows 2012" quiet splash pcie_aspm=force [COLOR="#FF0000"]acpi_backlight=vendor[/COLOR] i8042.reset i8042.nomux=1 vt.handoff=7

```


You still have acpi_backlight=vendor enabled. Can you remove that one as well and try again? And after reboot, can you also:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by macmus on 2013-07-05
when i add n "acpi_osi=!windows 2012" keys does not work :(
when I remove vendor line even xbacklight -set commands do not work anymore.

```

http://paste.ubuntu.com/5847543/

```


```

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
696
3484

```

---

### Post by Toz on 2013-07-05
Can you try only acpi_osi=?
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi= pcie_aspm=force i8042.reset"
```

On reboot post back:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by macmus on 2013-07-05
so.. with only this.. fn keys do not work and xbacklight do not work ether:(

```

lech@HP-EliteBook:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=6c701ba7-077e-42fe-8b8d-375d78d02a5d ro acpi_osi= pcie_aspm=force i8042.reset quiet splash vt.handoff=7
lech@HP-EliteBook:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
1
10
/sys/class/backlight/intel_backlight
1079
3484
lech@HP-EliteBook:~$ dmesg | tail
[   83.341311] atkbd serio0: Unknown key released (raw set 2, code 0xa4 on isa0060/serio0).
[   83.341316] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[   83.477026] atkbd serio0: Unknown key pressed (raw set 2, code 0xc3 on isa0060/serio0).
[   83.477034] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[   83.579223] atkbd serio0: Unknown key released (raw set 2, code 0xc3 on isa0060/serio0).
[   83.579230] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[   83.665726] atkbd serio0: Unknown key pressed (raw set 2, code 0xc3 on isa0060/serio0).
[   83.665731] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[   83.760212] atkbd serio0: Unknown key released (raw set 2, code 0xc3 on isa0060/serio0).
[   83.760220] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
lech@HP-EliteBook:~$ 

```

could you explain  me why now there is this problem ?
It use to work before and I did not change anything ? 

What does this:

```

Unknown key released 

```

means

Can I somehow restore this binding?

---

### Post by Toz on 2013-07-05
I was hoping that one of these kernel parameters might fix your problem, but since none of these seem to make a difference, lets go back to the defaults you were using:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor i8042.reset acpi_osi=Linux"
GRUB_CMDLINE_LINUX_DEFAULT=""
```
After reboot, this should get xbacklight working again.


> [ 2141.672583] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[ 2141.848596] atkbd serio0: Unknown key pressed (raw set 2, code 0xa4 on isa0060/serio0).
[ 2141.848603] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[ 2141.931667] atkbd serio0: Unknown key released (raw set 2, code 0xa4 on isa0060/serio0).
I'm assuming that the first one is for the brightness up key and the second for the brightness down key. As you've noted in your first post:
> 
keycode 232 = XF86MonBrightnessDown NoSymbol XF86MonBrightnessDown
keycode 233 = XF86MonBrightnessUp NoSymbol XF86MonBrightnessUp

Can you try the following commands:
_Brightness up_
```
sudo setkeycodes e043 233
```
_Brightness Down_
```
sudo setkeycodes e024 232
```

---

### Post by macmus on 2013-07-05
it did not help me much .. well there is no message in dmesg now but this is something I don't care :P

Any idea if installing any recent updates to ubunty may cause it ?

I happend when I installed 3.10 and now it stays :(

---

### Post by Toz on 2013-07-05
It's quite possible at the kernel upgrade introduced a regression. However, can we try a few other things to try to see if we can figure out what happened?

1. You have a number of kernel parameters in use. The acpi_backlight=vendor and acpi_osi=Linux we have verified are required. You have a couple of others:
- **i8042.reset** and **i8042.nomux=1** -> I'm not sure why these are required or what facilitated the need to add them, but perhaps you can try without in case they are now interfering.
- **pcie_aspm=force** -> this one is actually redundant. As you can see from your dmesg log:
> 0.162578] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
...and
> 0.660207]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
...so you can probably stop using it.

I would suggest a try with the following:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
...and see if it works.

2. The setkeycode commands should have worked. Can you try the following:
- in one terminal window, run:
```
tail -f /var/log/dmesg
```
...and in another terminal, hit the Function+Brightness Up combination and note the codes that are displayed in the first terminal window.

Then repeat for Function+Brightness Down. Post them back.

3. And finally, when you boot your computer, hold down the Shift Key and the Grub window should appear. Select "Ubuntu" from this menu and it will offer you the opportunity to boot with the previous kernel (3.8.0-25-generic). Check to see if the brightness keys are functional with this kernel. If so, then a regression has been introduced with the new kernel and a bug report needs to be created.

---

### Post by macmus on 2013-07-05
i reverted back to 3.8.0-25

```

Linux HP-EliteBook 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

I removed all the paremters except vendor one:

```

root@HP-EliteBook:~# cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=6c701ba7-077e-42fe-8b8d-375d78d02a5d ro acpi_backlight=vendor quiet splash pcie_aspm=force i8042.reset vt.handof

```

xbacklight works but same issue with keys

```

[  232.303697] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[  232.701233] atkbd serio0: Unknown key pressed (raw set 2, code 0xa4 on isa0060/serio0).
[  232.701241] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[  232.797435] atkbd serio0: Unknown key released (raw set 2, code 0xa4 on isa0060/serio0).
[  232.797442] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[  233.033426] atkbd serio0: Unknown key pressed (raw set 2, code 0xc3 on isa0060/serio0).
[  233.033434] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[  233.126551] atkbd serio0: Unknown key released (raw set 2, code 0xc3 on isa0060/serio0).
[  233.126559] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[  251.297264] atkbd serio0: Unknown key pressed (raw set 2, code 0xa4 on isa0060/serio0).
[  251.297269] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[  251.451017] atkbd serio0: Unknown key released (raw set 2, code 0xa4 on isa0060/serio0).

```

once i bind the code ..  error stops in dmesg but brigtness does not work..

additionaly:
I just released that togeter with kernel update i downloaded new xorg update.... maybe it be a reason ??

how to debug it from there?

---

### Post by Toz on 2013-07-05
Can you follow the instructions from point #2 in my previous post (you should reboot before trying so that the setkeycode commands are not in effect). I'd like to know exactly which codes are displayed when you press the brightness up combination and exactly which codes are displayed when you press the brightness down combination.

In addition, can you post back your Xorg.0.log file?
```
pastebinit /var/log/Xorg.0.log
```

---

### Post by macmus on 2013-07-05
ok .. brightness up = fn + f10 

```

[ 1890.781031] atkbd serio0: Unknown key pressed (raw set 2, code 0xc3 on isa0060/serio0).
[ 1890.781038] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.
[ 1890.996256] atkbd serio0: Unknown key released (raw set 2, code 0xc3 on isa0060/serio0).
[ 1890.996267] atkbd serio0: Use 'setkeycodes e043 <keycode>' to make it known.

```

brightness down = fn + f9

```

[ 2340.906832] atkbd serio0: Unknown key pressed (raw set 2, code 0xa4 on isa0060/serio0).
[ 2340.906840] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.
[ 2341.010489] atkbd serio0: Unknown key released (raw set 2, code 0xa4 on isa0060/serio0).
[ 2341.010501] atkbd serio0: Use 'setkeycodes e024 <keycode>' to make it known.

```


and xorg

```

lech@HP-EliteBook:~$ pastebinit /var/log/Xorg.0.log
http://paste.ubuntu.com/5848755/


```

---

### Post by Toz on 2013-07-06
Since this used to work and now doesn't, its probably as a result of an upgrade. You've reverted the kernel and the problem persists. 

> [    29.237] 
X.Org X Server 1.13.4
Release Date: 2013-04-17
[    29.237] X Protocol Version 11, Revision 0
[    29.237] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    29.237] Current Operating System: Linux HP-EliteBook 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64
[    29.237] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=6c701ba7-077e-42fe-8b8d-375d78d02a5d ro acpi_backlight=vendor quiet splash pcie_aspm=force i8042.reset vt.handoff=7
[    29.237] Build Date: 08 May 2013  02:34:03PM
[    29.237] xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
How did you upgrade Xorg? Its looking like something changed with the keyboard mappings thats bringing in that message in the dmesg log file.

---

### Post by macmus on 2013-07-06
Yes Correct.

I do only updates when they pop up in the tray. The same way i did update for this new kernel and xorg.

Is there any way how to check previous mapping ?

---

### Post by Toz on 2013-07-06
> [ 29.237] xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Are you using the xorg-edgers PPA? Googling the xorg-server version leads me to that site. If so, it looks like there have been some recent updates there that may have affected the operation of your hotkeys. This command will help identify where the package is coming from:
```
apt-cache policy xserver-xorg
```



> BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=6c701ba7-077e-42fe-8b8d-375d78d02a5d ro acpi_backlight=vendor quiet splash pcie_aspm=force i8042.reset vt.handof
If this is the latest version of your kernel command line, how manu backlight interfaces do you have?
```
ls /sys/class/backlight/interface
```

If you are using xorg-edgers, I'm thinking that something changed there that affected your function keys. I also think those setkeycodes commands are working, but if you have more than one backlight interface, then its writing to the wrong one. Ideally, you want to boot with a kernel command line option that gives you one backlight interface, run the setkeycodes commands again and re-test the function keys.

If that doesn't work, the best we can do is create a workaround to give you keyboard control of your backlight interface.

---

### Post by macmus on 2013-07-06
I'm using standard ubuntu updates. I may have installed something in the past, but I don't know if this come from this PPT

```

lech@HP-EliteBook:~$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.7+1ubuntu4
  Candidate: 1:7.7+1ubuntu4
  Version table:
 *** 1:7.7+1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
        100 /var/lib/dpkg/status
lech@HP-EliteBook:~

```

I do not have this one you asked:

```

lech@HP-EliteBook:~$ ls /sys/class/backlight/interface
ls: cannot access /sys/class/backlight/interface: No such file or directory
lech@HP-EliteBook:~$ $ 
lech@HP-EliteBook:~$ ls /sys/class/backlight/intel_backlight/
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

```

Is there any way to recall this change and use a standard xrog not the one you are mentioning ?

---

### Post by Toz on 2013-07-07
> **macmus said:**
> I'm using standard ubuntu updates. I may have installed something in the past, but I don't know if this come from this PPT

```

lech@HP-EliteBook:~$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.7+1ubuntu4
  Candidate: 1:7.7+1ubuntu4
  Version table:
 *** 1:7.7+1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
        100 /var/lib/dpkg/status
lech@HP-EliteBook:~

```
That is very odd. The xserver-xorg version is the correct one that comes with raring, but the version in your log file (xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring) states something else. I'm not sure how this discrepancy came to be. According to the log file, you are running an xserver from a branch off of git. If you do a google search of that version, it takes you to the xorg-edgers PPA. Can you post back the results of:
```
ls /etc/apt/sources.list.d/
```
...I want to see if xorg-edgers is there.
Note: Another way to check is to open the Software Centre and click the arrow beside "Installed" and it will list all the sources that you have (including PPAs). If xorg-edgers is listed there, select it and it will show which packages from that PPA are currently installed.

> I do not have this one you asked:

```

lech@HP-EliteBook:~$ ls /sys/class/backlight/interface
ls: cannot access /sys/class/backlight/interface: No such file or directory
lech@HP-EliteBook:~$ $ 
lech@HP-EliteBook:~$ ls /sys/class/backlight/intel_backlight/
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

```
Oops, a typo on my part. Do you have any interfaces other intel_backlight?
```
ls /sys/class/backlight/
```
I want to see if we can manually manipulate the backlight. To see if you can, you will be entering a command like:
```
echo XX | sudo tee /sys/class/backlight/YY/brightness
```
...where **XX** is a value between 0 and the contents of */sys/class/backlight/YY/max_brightness*, and **YY **is the interface name. So, for example for the intel_backlight interface:
```
echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 3000 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
If you have more than 1 interface, then try the other interface as well. Post back if you can manually adjust this interface.


> Is there any way to recall this change and use a standard xrog not the one you are mentioning ?
If you are using the xorg-edgers PPA (we can verify from above), according to [the PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa"), it can be reverted via:
```
To revert to official packages, install the ppa-purge package and run "sudo ppa-purge xorg-edgers".
```
But lets verify first whether it is in use.

---

### Post by macmus on 2013-07-08
I found that that with new kernel I had to recompile again modules for vbox.
Do I have to do anything simmilar for x.org and other stuff?

```

root@HP-EliteBook:/home/lech/# ls /etc/apt/sources.list.d/
amith-ubuntutools-raring.list         danielrichter2007-grub-customizer-raring.list          linrunner-tlp-raring.list.save      steam.list.save                      xorg-edgers-ppa-raring.list.save
amith-ubuntutools-raring.list.save    ehoover-compholio-raring.list                          noobslab-mint-raring.list           tiheum-equinox-raring.list           xubuntu-dev-xfce-4_10-raring.list
apt-fast-stable-raring.list           ehoover-compholio-raring.list.save                     noobslab-mint-raring.list.save      tiheum-equinox-raring.list.save      xubuntu-dev-xfce-4_10-raring.list.save
apt-fast-stable-raring.list.save      google-chrome.list                                     noobslab-themes-raring.list         ubuntu-wine-ppa-raring.list          xubuntu-dev-xfce-4_12-raring.list
atareao-atareao-raring.list           google-chrome.list.save                                noobslab-themes-raring.list.save    ubuntu-wine-ppa-raring.list.save     xubuntu-dev-xfce-4_12-raring.list.save
atareao-atareao-raring.list.save      gwendal-lebihan-dev-cinnamon-nightly-raring.list       skype-wrapper-ppa-raring.list       webupd8team-themes-raring.list       zedtux-naturalscrolling-raring.list
cairo-dock-team-ppa-raring.list       gwendal-lebihan-dev-cinnamon-nightly-raring.list.save  skype-wrapper-ppa-raring.list.save  webupd8team-themes-raring.list.save  zedtux-naturalscrolling-raring.list.save
cairo-dock-team-ppa-raring.list.save  linrunner-tlp-raring.list                              steam.list                          xorg-edgers-ppa-raring.list

```


and backlight is intel

```

ls /sys/class/backlight/

```

```

root@HP-EliteBook:/home/lech/# cat /sys/class/backlight/intel_backlight/max_brightness 
3484

```

I just did test:

```

lech@HP-EliteBook:~/$ echo 1000 | sudo tee /sys/class/backlight/intel_backlight/brightness 
1000
lech@HP-EliteBook:~/$ echo 2000 | sudo tee /sys/class/backlight/intel_backlight/brightness 
2000

```

and this is changing my brightness succesfully.

---

### Post by macmus on 2013-07-08
I just see there is again update for X.org display driver for intel..

---

### Post by Toz on 2013-07-08
You do have the xorg-edgers ppa installed (you can see its entry in /etc/apt/sources.d).

I'm not sure what to suggest now. You can try purging that PPA and reverting back to the raring-based version of xserver, or we could create a workaround to give you keyboard control of your function keys (along the lines of: [http://ubuntuforums.org/showthread.php?t=2156192&p=12702299&viewfull=1#post12702299]("http://ubuntuforums.org/showthread.php?t=2156192&p=12702299&viewfull=1#post12702299")).

If you open a terminal window, execute:
```
acpi_listen
```
...then press the brightness function up key combination then the brightness function down key combination, do any codes show up in the terminal window? If not, try executing the setkeycodes commands and trying again.

---

### Post by macmus on 2013-07-08
hmm 2 things 

1. I installed new x.org which poped up and did not bring any improvments.

2. When executing acpi_listen nothing is showing up when I press buttons :(

---

### Post by Toz on 2013-07-09
> **macmus said:**
> 
2. When executing acpi_listen nothing is showing up when I press buttons :(
Even after you ran the setkeycodes
```
sudo setkeycodes e043 233
sudo setkeycodes e024 232
```
...then try "acpi_listen" again.

EDIT: Can you also post back:
```
ls -l /etc/apt/sources.list.d
```
...so that I can see when you enabled some of those PPAs. Do you recall enabling one of the PPAs at around the time the problem started?

---

### Post by macmus on 2013-07-09
that is rlly interesting I added this two lines now and brightness is working again ...

maybe it is because the recent upadte of x.org I downloaded...

```

lech@HP-EliteBook:~$ sudo setkeycodes e043 233
lech@HP-EliteBook:~$ sudo setkeycodes e024 232

```


any way to add it permanently now ?

---

### Post by Toz on 2013-07-09
Yes. 

```
gksu gedit /etc/rc.local
```
...and add _above_ the *exit 0* command:
```
/usr/bin/setkeycodes e043 233
/usr/bin/setkeycodes e024 232
```
...and save the file.

---

### Post by macmus on 2013-07-09
hmm that interesting but on the first login after shutdown this not work.

I have to logout and login, then it works.

---

### Post by Toz on 2013-07-09
> **macmus said:**
> hmm that interesting but on the first login after shutdown this not work.

I have to logout and login, then it works.
That is interesting. Lets try this instead:

1. Remove the codes from the /etc/rc.local file.

2. Create a new file, /usr/local/bin/setcodes, with the following content:
```
#!/bin/bash
/usr/bin/setkeycodes e043 233
/usr/bin/setkeycodes e024 232

```

3. Make /usr/local/bin/setcodes executable.

4. Add to the end of /etc/lightdm/lightdm.conf:
```
session-startup-script = /usr/local/bin/setcodes
```

5. Reboot and try again.

---

### Post by macmus on 2013-07-10
Thanks!
It solve this strange issue! :)

:D

---

### Post by Toz on 2013-07-10
Glad to hear. Can you mark this thread as solved using the instructions from the "How to Mark a Thread SOLVED" link in my signature? Thanks.

---

### Post by macmus on 2013-07-10
I found out also that without this 

```

1 S lech      3740     1  0  80   0 - 66749 futex_ 17:26 ?        00:00:00 xfce4-power-manager --restart --sm-client-id 274af5795-e7fe-4688-8f16-52436a73a3b3
0 S lech      9299     1  0  80   0 - 159047 poll_s 17:28 ?       00:00:02 xfce4-power-manager --no-daemon

```

I could not do brigtness. ACPI did not work at all. 
Sometime it is stack in 
```

xfce4-power-manager --restart --sm-client-id 274af5795-e7fe-4688-8f16-52436a73a3b3

```
its has to be killed and restarted manualy with --no-daemon.

It seems this restat comes from fact that xfce tries to resume process, but without --no-daemon it does not work.
It seems to be a bug of this app.

---

