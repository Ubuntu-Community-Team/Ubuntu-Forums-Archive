---
title: "HOWTO: Lirc in Edgy"
date: 2006-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by hexion on 2006-10-29
[I]**Edited:**
[/I]
Hi all! :)
I've been out of these forums much time, so this Howto hasn't been mantained by myself at all. I couldn't imagine this "Howto" would be seen so much, so I'm really sorry for keeping this outdated.

This thread has grown so much, that I think it's time to put our efforts in mantaining another kind of system that allows everybody to fix, edit, or add new info.. I reffer on a wiki, of course :)
                                          
**Bodhi.zazen **already ported this howto to a wiki (thank you very much), so we can use it from now on. Please, it would be great if anyone who have followed this thread and sent fixes or completed it, visit that wiki and complete/mantain it. Here it is: [http://doc.gwos.org/index.php/Lirc](http://doc.gwos.org/index.php/Lirc)

I'd like to add that you've got a wiki mantained by **Superm1** with much more info than this thread. So please, read it in order to fix your problems. I'd like to thank **Superm1** his unvaluable help for mantaining this thread and helping people with their lirc problems.
Here it is: [http://help.ubuntu.com/community/Install_Lirc_Edgy](http://help.ubuntu.com/community/Install_Lirc_Edgy)

Regards
hexion                  

*P.S.: Of course, you can still post here your doubts. And remember, now everybody can edit this howto (in the wiki created by ***Bodhi.zazen**) so if you find a solution for someone's problem feel free to complete/fix that wiki so you'll help the comunity :)

[I] 
[SIZE=3][B]---------------------------
Old thread follows:
---------------------------[/B][/SIZE]
Advertisement: this howto is provided as is. It may contain errors and have no support. If you find any problem, post it and I'll try to solve it. But sorry if I can't ;)[/I]

*To simplify the howto, we become root at the beginning. If you don't want it, you must put "sudo" in almost all the sentences.*


[SIZE=4]**1) Download lirc (you'll need at least  version 0.8.1pre2)**[/SIZE]

> sudo -s
cd /usr/src
wget [http://lirc.sourceforge.net/software/snapshots/lirc-0.8.1pre2.tar.bz2](http://lirc.sourceforge.net/software/snapshots/lirc-0.8.1pre2.tar.bz2)
tar xvfj lirc-0.8.1pre2.tar.bz2[SIZE=4]**2) Install linux sources and other utils**[/SIZE]

> aptitude install linux-source-2.6.17 build-essential gcc-3.4
tar xvfj linux-source-2.6.17.tar.bz2
unlink linux
ln -s linux-source-2.6.17 linux
cd linux
cp /boot/config-2.6.17-10-generic .config[SIZE=4]**3) Install lirc from repos (to make some config issues in your system, we wont use edgy binaries)**[/SIZE]

> aptitude install lirc lirc-x[SIZE=4]**4) Lirc setup**[/SIZE]

> cd /usr/src/lirc-0.8.1pre2/drivers
ln -s /usr/src/linux/drivers drivers
cd ..
./setupChoose option 1. Driver configuration

You have to choose your card. In example, for avermedia capture 98, you must choose 1)driver configuration  2) TV Card 6)Avermedia TV Card (TV Capture 98 )

At the end, choose option "Save configuration & run configure"


[SIZE=4]**5) Build and install lirc from source**[/SIZE]
[I]
(note we are in /usr/src/lirc-0.8.1pre2 directory and we are root)[/I]

> make
make install[SIZE=4]**6) Load module and test lirc**[/SIZE]

When "make install" finishes, it will tell you which module to load. In my case it's lirc_gpio. Change first line if yours is different.

> modprobe lirc_gpio
lircd
irwAt this point, press your remote control keys to test if it works.

***EDIT:*** Acording to a user (elchupakabra), if your module is "lirc_serial", prior to modprobe line you'll have to do this:

>  aptitude install setserial
setserial /dev/ttyS0 uart none[SIZE=4]**7) Autoload lirc at boot-time**[/SIZE]

> killall lircd>  echo "alias char-major-61-* lirc_gpio" | sudo tee /etc/modprobe.d/lircThis command works with lirc_gpio. I think if your module is another, you'll have to change "lirc_gpio" for it, but I'm not sure if it will work. Report if it doesn't.

>  gedit /etc/rc.localIn that file, add these 2 lines before "exit 0" line:
mknod /dev/lirc c 61 0
lircd


[SIZE=4]**8 ) Disable ir_common (NEW IN EDGY!!!). Explanation and test**[/SIZE]

Since kernel 2.6.17, there's a new "feature" that manages remote control keys of certain TV Cards. This cannot be disabled nor configured, and will interfeer with normal behaviour of LIRC.

To work well with our LIRC configuration, we must disable this module. It cannot be unloaded because bttv module needs it to work. I've made a "kernel hack" (explained at the end of this howto) to build an "ir_common" module with such management disabled.

At this point you need to test if that module is by default doing something in your system, and if so, disable it.


a) Open a terminal
b) With lirc unloaded (killall lircd), press a number key of your remote control.

_If that number appears in the terminal, you must continue with step 9)._

_If there's anything in the terminal window, continue with step 10_


[SIZE=4]**9) Disable ir_common (NEW IN EDGY!!!). Doing the trick**[/SIZE]

You've got 2 options. Loading my "hacked" ir_common module (THIS IS ONLY FOR KERNEL 2.6.17-10-generic),or building your own "hacked" ir_common module.

**9.a) Loading my module (easier but only valid for edgy's default kernel)**

Download attached ir_common.ko (uncompress tar.gz file) and move it to /lib/modules/2.6.17-10-generic/kernel/drivers/media/common
(note, you'll need root privileges to do so)

**9.b) Building your own module**

> gedit /usr/src/linux-source-2.6.17/drivers/media/common/ir-keymaps.cIn this file, there are definitions of the remote control keys of certain TV cards. We need to delete such definitions to avoid ir_common module to manage our card.

Go to the definition of "ir_codes_empty" copy what's between the symbols {} and paste it in ALL other definitions.

In example, "ir_codes_avermedia_dvbt" definition should look like this:

> /* Matt Jesson <dvb@jesson.eclipse.co.uk */
IR_KEYTAB_TYPE ir_codes_avermedia_dvbt[IR_KEYTAB_SIZE] = {
    [ 0x2a ] = KEY_COFFEE,
};When you finish, save changes. Then, compile modules of your kernel

> cd /usr/src/linux-source-2.6.17/drivers/media/common/
rm *.o
rm *.ko
cd /usr/src/linux-source-2.6.17/drivers/media/video/bt8xx/
rm *.o
rm *.ko
cd /usr/src/linux-source-2.6.17
make modulesOk, now you've got your own ir_common module build. Copy it to /lib/modules...

> cp /usr/src/linux-source-2.6.17/drivers/media/common/ir_common.ko /lib/modules/2.6.17-10-generic/kernel/drivers/media/common[SIZE=4]**10) Reboot and enjoy ;)**[/SIZE]


At this point, this HOWTO finishes :P


[I]*) I'll make one of these days a HOWTO to configure lirc keys to do many things. When I've got time, I promise :)

Mine is configured to manage:
amarok, totem, mplayer, vlc player, xdtv, shutdown computer, change between desktops (emerald & compiz), volume control, put on and off the screen, (...)


[B]EDIT: Added my ir-keymaps.c file ("hacked" one)
[/B]
[/I]***EDIT2: Changed ir-keymaps.c file. The earlier was the normal one, not my hacked file. Sorry for the error...***

---

### Post by elchupakabra on 2006-10-29
Hello, I have error on step 6
I'we tried to reboot but i still have this error
root@zz-desktop:~# modprobe lirc_serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.17-10-generic/misc/lirc_serial.ko): Device or resource busy

update:
is solved this problem:
checking serial ports i'we found something:
dmesg | grep tty
[17179570.572000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.576000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179709.196000] lirc_serial: use 'setserial /dev/ttySX uart none'
[17179858.384000] lirc_serial: use 'setserial /dev/ttySX uart none'
and then :
apt-get install setserial
setserial /dev/ttyS0 uart none

---

### Post by superm1 on 2006-10-30
I've actually put together a howto already on the wiki that doesn't install anything from source.  It includes a section to cover issues with I2C and GPIO ( I assembed a debian package already for lirc that has 2.6.17 support for these two modules ).  It's a lot more manageable since it uses debian init scripts and module-assistant for module building rather then spewing binaries across the system that aren't easily uninstallable unless you wrote down every single one installed.

[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

---

### Post by hexion on 2006-10-30
> **superm1 said:**
> I've actually put together a howto already on the wiki that doesn't install anything from source.  It includes a section to cover issues with I2C and GPIO ( I assembed a debian package already for lirc that has 2.6.17 support for these two modules ).  It's a lot more manageable since it uses debian init scripts and module-assistant for module building rather then spewing binaries across the system that aren't easily uninstallable unless you wrote down every single one installed.

[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

You don't mention the ir_common problem since 2.6.17 kernel.  That's precisely my contribution in this howto.   :rolleyes:
I knew about lirc-modules-source packet, but I still preffer building from source. For me nothing except this worked.

---

### Post by superm1 on 2006-10-30
Sorry,
I haven't come across the ir_common problem myself as I don't use i2c.  Could you better explain what functionality ir_common is supposed to include and why it doesn't work correctly with lirc?  

Debian upstream hasn't had any bugs issued about this, and has i2c support fixed since about 20 days ago:
[http://packages.debian.org/changelogs/pool/main/l/lirc/lirc_0.8.0-9/changelog](http://packages.debian.org/changelogs/pool/main/l/lirc/lirc_0.8.0-9/changelog)

---

### Post by hexion on 2006-10-30
> **superm1 said:**
> Sorry,
I haven't come across the ir_common problem myself as I don't use i2c.  Could you better explain what functionality ir_common is supposed to include and why it doesn't work correctly with lirc?  

Debian upstream hasn't had any bugs issued about this, and has i2c support fixed since about 20 days ago:
[http://packages.debian.org/changelogs/pool/main/l/lirc/lirc_0.8.0-9/changelog](http://packages.debian.org/changelogs/pool/main/l/lirc/lirc_0.8.0-9/changelog)

Please, read the bugs I filed in ubuntu and upstream (kernel.org)

[https://launchpad.net/products/linux/+bug/67399](https://launchpad.net/products/linux/+bug/67399)
[http://bugzilla.kernel.org/show_bug.cgi?id=7395](http://bugzilla.kernel.org/show_bug.cgi?id=7395)


Mainly, bttv now supports a IR module in certain TV cards. But cannot be disabled (compiled in kernel and BTTV depends on it) nor configured.

---

### Post by superm1 on 2006-10-30
Hexion, This make a lot more sense now.  Thanks.

---

### Post by lerrup on 2006-11-03
Mario,

I am confused as I want to install lirc for a /dev/eventx type remote that doesn't need a module.

How do I configure lirc to start with using the .debs, as you would if you installed from source?

Thanks,

---

### Post by superm1 on 2006-11-03
Lerrup,

You will need to modify /etc/lirc/hardware.conf.

You will find a line, LIRCD_ARGS=""

Modify this line to include
```
LIRCD_ARGS="-d /dev/eventX"
```

---

### Post by basketcase on 2006-11-03
I followed your wiki..

When I go to start lirc, here is the output

> bdmorrison@ubuntu:/etc/lirc$ sudo /etc/init.d/lirc start
##################################################
## LIRC IS NOT CONFIGURED                       ##
##                                              ##
## read /usr/share/doc/lirc/html/configure.html ##
##################################################
Starting lirc daemon:.


I have /etc/lirc/lircd.conf and /etc/lirc/lircd.conf.hauppauge

I have stopped/started/restarted w/o success.  

I think the remote is one of the last things I need to deal with!!

---

### Post by basketcase on 2006-11-03
> **basketcase said:**
> I followed your wiki..

When I go to start lirc, here is the output



I have /etc/lirc/lircd.conf and /etc/lirc/lircd.conf.hauppauge

I have stopped/started/restarted w/o success.  

I think the remote is one of the last things I need to deal with!!
So I went back and went through the instructions again at the beginning.  Remote did respond when I was testing it.  I killall lircd, restarting now...

And it doesn't work...

I'll wait for a reply and google till then.

---

### Post by superm1 on 2006-11-04
basketcase,

You will need to replace the existing /etc/lirc/lircd.conf with the lircd.conf.hauggpauge.  (the lircd.conf that is there is just a holder file until you replace it or add a remote to it)

---

### Post by loell on 2006-11-04
hi, i'm new to setting infrared devices , my ma-620 infrared now works, and when i push keys from a remote control it is now responding, just a basic question what's the tool for revealing the key codes of a remote control? ;)

---

### Post by superm1 on 2006-11-04
> **loell said:**
> hi, i'm new to setting infrared devices , my ma-620 infrared now works, and when i push keys from a remote control it is now responding, just a basic question what's the tool for revealing the key codes of a remote control? ;)

loell,

If your remote is working natively - then 
```
xev
``` 

will reveal what the buttons are being recognized as.

If you remote is working thanks to lirc, then
```
irw 
```

will reveal the buttons being recognized.

---

### Post by basketcase on 2006-11-04
> **superm1 said:**
> basketcase,

You will need to replace the existing /etc/lirc/lircd.conf with the lircd.conf.hauggpauge.  (the lircd.conf that is there is just a holder file until you replace it or add a remote to it)
Right now, it has the lircd.conf.hauppauge copied into it.  

I'll remove it and see what it does as there is already (I copied over) an lircd.conf.hauppauge there.

---

### Post by superm1 on 2006-11-04
> **basketcase said:**
> Right now, it has the lircd.conf.hauppauge copied into it.  

I'll remove it and see what it does as there is already (I copied over) an lircd.conf.hauppauge there.

I'll add a correction to explain this better in the wiki.  There is a header in the default lircd.conf that needs to be cleared out if you simply add a remote to it.

---

### Post by basketcase on 2006-11-04
> **superm1 said:**
> I'll add a correction to explain this better in the wiki.  There is a header in the default lircd.conf that needs to be cleared out if you simply add a remote to it.
I wondered if that wasn't the case, so I completely deleted everything in the lircd.conf file.

The only thing in there now is what I copied over from the lircd.conf.hauppauge file from the link provided in the wiki.

---

### Post by EspressoNuts on 2006-11-04
Hexion and all,

Sorry for the kind-a-newbie question, but I am trying to set up a TIRA 2.1 and everything goes normal until set 4 (./setup.sh). The result of the configuration is 
"Your hardware does not require a kernel module.

Now enter 'make' and 'make install' to compile and install the package."

Which puzzles me. If I do make and make install, I do not have a module to modprobe. Although I can "lircd" and "irw" (or for other purposes "xev") are executed, nothing happens. By ps -ef I see no lirc or irw process either.

What am I doing worng?

---

### Post by hexion on 2006-11-04
> **EspressoNuts said:**
> Hexion and all,

Sorry for the kind-a-newbie question, but I am trying to set up a TIRA 2.1 and everything goes normal until set 4 (./setup.sh). The result of the configuration is 
"Your hardware does not require a kernel module.

Now enter 'make' and 'make install' to compile and install the package."

Which puzzles me. If I do make and make install, I do not have a module to modprobe. Although I can "lircd" and "irw" (or for other purposes "xev") are executed, nothing happens. By ps -ef I see no lirc or irw process either.

What am I doing worng?

Is your hardware supported by lirc? I mean, is there an option in ./setup.sh script that matches your hardware?
If you're not sure, you can check in [www.lirc.org]("http://www.lirc.org"). In the "Supported Hardware" menu.

If there is, and you're setting it properly, maybe it's a bug of lirc and should be reported to [www.lirc.org]("http://www.lirc.org")
If there isn't you can probe with another card's configuration and if you're lucky maybe there's another one with the same config...

Good luck ;)

---

### Post by EspressoNuts on 2006-11-04
Thanks for the prompt reply. I am not actually using the remote to control a TV card. Just trying to get TIRA from Home-electronics [http://www.home-electro.com/tira2lx.php](http://www.home-electro.com/tira2lx.php)
to work. It is supported by lirc, there is an option for it on setup. Goal is to control XMMS if i get it working.


I am tweaking on hardware.conf and lirc.conf, now. If anyone has better ideas, please let me know.

Thanks,:-k

---

### Post by basketcase on 2006-11-04
Another question...

I started over -- everything has gone smoothly.  Myth is up and running, but remote still does not work.  

> #
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R [www.mythtvportal.com](www.mythtvportal.com)
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg [www.lugv.at](www.lugv.at)
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote





My question, in the above lircd.conf.hauppauge file there are a number of configurations depending on remote and video card.  Up to now I have just copied and pasted that entire conf into lircd.conf.  Do I just want to pull the one that is applicapable to my remote and video card?

---

### Post by basketcase on 2006-11-04
Another question...

Do I need to do this?  All I'm wanting to do is change the channel, and browse through MythTV with the remote control and not need a keyboard.  

> **Create a .lircrc file**

  If you are intending on using lirc for only IR transmitting, you don't need to create a ~/.lircrc file. If you are going to use it for IR receiving, you will need to create a ~/.lircrc file describing what each of the buttons does for each application you will use lirc in. 
 The basic syntax is as follows: 
 [LIST]
[*] begin
    prog = PROGRAM
    button = REMOTE_BUTTON
    config = ACTION
end[/LIST] Where: 
 [LIST]
[*]*PROGRAM* is the program you are recording buttons for.  Some examples for *PROGRAM* are **mythtv**, **mplayer**, **xine**, **vlc**, and **irexec**. 
 *REMOTE_BUTTON* is the name of the button in accordance with what is listed in your /etc/lirc/lircd.conf. 
 *ACTION* is the action that will be performed when this button is pressed. You can find a list of actions in the attached .lircrc example file. 
[/LIST]  **Specific Application Notes**

  Multiple applications can be listed in the .lircrc file, but you will need a seperate *begin* and *end* block for each button in eachapplication.  
 [LIST]
[*] MythTV 
[/LIST] If you are using this for mythtv, you will need to create a symbolic link to this file for mythtv to read it. 
 [LIST]
[*] ln -s ~/.lircrc ~/.mythtv/lircrc[/LIST] [LIST]
[*] IRexec 
[/LIST] irexec is able to interpret keypresses and launch applications when the keys are pressed. The syntax is: 
 [LIST]
[*] begin
    prog = irexec
    button = REMOTE_BUTTON
    config = APPLICATION
end[/LIST] APPLICATION is simply the path and name of a file marked executable. 


---

### Post by basketcase on 2006-11-04
okay it seems that I do

There are a number of .lircrc configs online, but it seems they're just a little off per the lircd.conf that was used...so I guess I'm going to have to map my own :(

---

### Post by loell on 2006-11-04
i'm still finding my config by attemting to map key codes

irrecord --device=/dev/ircomm0 myconfig.conf

but when i open myconfig.conf after pressing several remote keys
the file is empty :(

---

### Post by cheuschober on 2006-11-04
Hi. Thanks for the tutorials. I followed SuperM's wiki spot and tried the ir-common hack here but I still can't get responsiveness from my remote (ATI Remote Wonder (lirc_atiusb)).

irw produces nothing BUT irrecord correctly detects and maps all the button presses.

What might I be doing wrong?

Chad

---

### Post by SlamBam on 2006-11-06
Hi,

excellent guide. Lirc seems to work now. Two thing I found confusing:

Step 4 in your guide says: ./setup
Should´nt this be: ./configure?

And in step you doe:
"echo "alias char-major-61-* lirc_gpio" | sudo tee /etc/modprobe.d/lirc"

Shouldnt this be:
echo "alias char-major-61-* lirc_gpio" | sudo tee /etc/modprobe.d/aliases"?

Thanks!

---

### Post by hexion on 2006-11-06
> **cheuschober said:**
> Hi. Thanks for the tutorials. I followed SuperM's wiki spot and tried the ir-common hack here but I still can't get responsiveness from my remote (ATI Remote Wonder (lirc_atiusb)).

irw produces nothing BUT irrecord correctly detects and maps all the button presses.

What might I be doing wrong?

Chad

My main contribution in this howto is the ir-common stuff ;)  About the rest I can't help cause I don't have that card, surely superm1 can help you better than me :mrgreen:

---

### Post by hexion on 2006-11-06
> **SlamBam said:**
> Hi,

excellent guide. Lirc seems to work now. Two thing I found confusing:

Step 4 in your guide says: ./setup
Should´nt this be: ./configure?

And in step you doe:
"echo "alias char-major-61-* lirc_gpio" | sudo tee /etc/modprobe.d/lirc"

Shouldnt this be:
echo "alias char-major-61-* lirc_gpio" | sudo tee /etc/modprobe.d/aliases"?

Thanks!


No, it's correct as is.
./setup is to select your card
./configure is the previous step before doing a make / make install.

In fact, ./setup calls ./configure in the option "Save configuration & run configure"

About the echo command, it's good as in the howto. It's not my command, I copied it from many lirc howtos. And it works (at least for me :mrgreen: )

---

### Post by kuja on 2006-11-06
superm1, the page on help.ubuntu.com you linked to on the first page was exactly what I was looking for! It would be kind of nice to see it, or a trimmed down version of it anyway, as the page in the ubuntu wiki (lirchowto, or similar). It works like a charm.

On a sidenote, one thing potentially worth mentioning is the kdelirc package. For KDE users anyway, irkick provides a MUCH simpler way of setting up the remote control functions than writing an lircrc file.

---

### Post by superm1 on 2006-11-06
> **kuja said:**
> superm1, the page on help.ubuntu.com you linked to on the first page was exactly what I was looking for! It would be kind of nice to see it, or a trimmed down version of it anyway, as the page in the ubuntu wiki (lirchowto, or similar). It works like a charm.

On a sidenote, one thing potentially worth mentioning is the kdelirc package. For KDE users anyway, irkick provides a MUCH simpler way of setting up the remote control functions than writing an lircrc file.

kuja, glad to hear this worked for you.  I haven't personally used irkick to set up a lircrc file.  Could you possibly add a bit to the wiki page about this, and I'll organize it to fit well with other content?  I have a few other things to yet add, including Hexion's ir_common hack.

---

### Post by superm1 on 2006-11-06
> **cheuschober said:**
> Hi. Thanks for the tutorials. I followed SuperM's wiki spot and tried the ir-common hack here but I still can't get responsiveness from my remote (ATI Remote Wonder (lirc_atiusb)).

irw produces nothing BUT irrecord correctly detects and maps all the button presses.

What might I be doing wrong?

Chad
Chad,
This may be because you have the kernel ati driver loaded as well.  Could you make sure that there are no ATI modules loaded at the same time (other then radeon or fglrx).

---

### Post by kuja on 2006-11-06
> **superm1 said:**
> kuja, glad to hear this worked for you.  I haven't personally used irkick to set up a lircrc file.  Could you possibly add a bit to the wiki page about this, and I'll organize it to fit well with other content?  I have a few other things to yet add, including Hexion's ir_common hack.
Sure, I suppose I can add a bit of info on it to the wiki. irkick doesn't actually use the lircrc file though... It provides dirt simple functionality for setting up use with a handful of kde programs (amarok, kaffeine, noatun, konqueror). It uses DCOP to provide functionality. You can also select dcop functions from running programs, or use klauncher to execute terminal commands.

---

### Post by loell on 2006-11-07
:( after some extensive research, i've come to a conclusion
that my ir usb dongle (MA-620) is not usable with lirc,
other owners that have gone with this path and doesn't  have any luck either,
too bad, i guess i'll have to look for real infrared module for a pc

---

### Post by cheuschober on 2006-11-09
Ahh.

Hexion... about your ir_common bug... Does it only affect the number keys or does it possibly also affect other keys?

I'm finding some odd (undocumented) behaviour with my lirc control of xine using my atiusb remote wonder. A menu navigation remote-down button produces an 'EventDown'+'EventSelect' event as opposed to it simply producing 'EventDown' as indicated in .lircrc.

This behaviour seems similar to your bug report description but before I go around hacking up my ir_common (I have a bttv card) I figured it would be safer to ask whether or not you think it might be related.

Is there a way to test if it's just the remote and / or modules?

Thanks so much,
~Chad

---

### Post by ilias on 2006-11-09
Here's my case.
I'm using dapper drake...although i don't think there's any difference...
I compiled a custom kernel from source. the 2.6.18.
configure goes ok but when I enter make I get the following error
```
/usr/src/lirc-0.8.1pre1/drivers/lirc_dev/lirc_dev.c:54:35: error: linux/devfs_fs_kernel.h: No such file or directory
```
this is the ouput when I enter the locate command
```
$ locate devfs_fs_kernel.h
/usr/include/linux/devfs_fs_kernel.h
/usr/src/linux-source-2.6.15/include/linux/devfs_fs_kernel.h
/usr/src/linux-headers-2.6.15-27-386/include/linux/devfs_fs_kernel.h
/usr/src/linux-headers-2.6.15-27/include/linux/devfs_fs_kernel.h

```
As you can see the specific files exists on the 2.6.15 kernel.
so i do
```
ln -s /usr/src/linux-source-2.6.15 /usr/src/linux
```
and
```
ln -s /usr/src/linux/drivers /usr/src/lirc-0.8.1pre1/drivers/drivers
```
and I still get the same output
what's wrong?

---

### Post by hexion on 2006-11-10
> **cheuschober said:**
> Ahh.

Hexion... about your ir_common bug... Does it only affect the number keys or does it possibly also affect other keys?

I'm finding some odd (undocumented) behaviour with my lirc control of xine using my atiusb remote wonder. A menu navigation remote-down button produces an 'EventDown'+'EventSelect' event as opposed to it simply producing 'EventDown' as indicated in .lircrc.

This behaviour seems similar to your bug report description but before I go around hacking up my ir_common (I have a bttv card) I figured it would be safer to ask whether or not you think it might be related.

Is there a way to test if it's just the remote and / or modules?

Thanks so much,
~Chad

In my case, with edgy, ir_common managed number keys and several other keys...

Freeze button blocked my session...
Power button launched the logoff menu...
I think it managed too the volume keys...

I can't remember anymore and now I have it disabled :mrgreen:
Anyway, through some functions were ok, I didn't like that something chose what some of my remote control keys were for. I preffer setting them by myself.

To test what's your ir_common behaviour I think there's no other way than simply checking its keys one by one... since I couldn't find any .c file in the kernel tree with info about that. It should be here /usr/src/linux/drivers/media/common/ir-functions.c

Don't worry about "hacking" the ir_common module. It's just like making it to not recognize your card... there's no strange code added. In fact I only deleted key definitions as explained in the HOWTO.
And you can always keep your current ir_common module just renaming it before copying the new one for if you don't like it :D

---

### Post by hexion on 2006-11-10
> **ilias said:**
> /usr/src/lirc-0.8.1pre1/drivers/lirc_dev/lirc_dev.c:54:35: error: linux/devfs_fs_kernel.h: No such file or directory[/code]this is the ouput when I enter the locate command


Try using lirc-0.8.1pre**2** as explained in the HOWTO. Since 2.6.17 kernel, some files changed their place in the tree, and it was fixed in the pre2.

---

### Post by EspressoNuts on 2006-11-11
HI,

This is just a quick note on working with Tira 2.1 - I actually managed it to work on receiving mode.:)  Now I'm looking for emmitter (sending IR to my cable box and receiver).:-k 

Thanks for the help.

---

### Post by superm1 on 2006-11-11
> **EspressoNuts said:**
> HI,

This is just a quick note on working with Tira 2.1 - I actually managed it to work on receiving mode.:)  Now I'm looking for emmitter (sending IR to my cable box and receiver).:-k 

Thanks for the help.

The only devices I know that support transmitting are the mceusb2 transceivers and serial.

---

### Post by mazirian on 2006-11-11
It's funny that lirc has, over the past few years, taken more of my time than any other package.  It never works without a fight.

@superm1: Were you able to build a lirc_gpio module against 2.6.17 sources using the normal method (i.e., the method described in your wiki page)?  Make complains that the version of bttv in the sources is too old to build the lirc driver, and then the build fails.

Will the howto at the root of this thread correct that issue?

---

### Post by mazirian on 2006-11-11
The build error might be helpful:

```

/usr/src/modules/lirc/drivers/lirc_gpio/lirc_gpio.c:62:2: error: #error "*******************************************************"
/usr/src/modules/lirc/drivers/lirc_gpio/lirc_gpio.c:63:2: error: #error " Sorry, this driver needs bttv version 0.7.45 or       "
/usr/src/modules/lirc/drivers/lirc_gpio/lirc_gpio.c:64:2: error: #error " higher. If you are using the bttv package, copy it to "
/usr/src/modules/lirc/drivers/lirc_gpio/lirc_gpio.c:65:2: error: #error " the kernel                                            "
/usr/src/modules/lirc/drivers/lirc_gpio/lirc_gpio.c:66:2: error: #error "*******************************************************"

```

---

### Post by mazirian on 2006-11-11
Rather, the build error is that the lirc_gpio.c doesn't know where to look for the drivers:

/usr/src/modules/lirc/drivers/lirc_gpio/lirc_gpio.c:56:41: error: ../drivers/media/video/bttv.h: No such file or directory

And also the same error for bttvp.h

bttv.h and bttvp.h are in drivers/media/video/bt8xx/ however.

So how is anyone getting this to build lirc_gpio out of the box?

---

### Post by mazirian on 2006-11-12
Well, this is silly that anyone would have to do this, but I was able to get the lirc_gpio module to build and to get lirc back up and running after my edgy upgrade by doing the following:

```

cd /usr/src/linux/drivers/media/video
sudo cp bt8xx/bt* .

```

This is in edgy, using the lirc-modules-source-0.8.0-5ubuntu1 package.  The wiki article linked to above indicates that you won't be able to use the current stable packages to build gpio or i2c.  That was true in dapper, but apparently not for edgy (at least as of this date).

Now let's share irexec tricks... I've attached my lircrc, which I am using with a winfast 2000XP card and remote to manage gnomeradio, totem, mplayer, rhythmbox and tvtime.  If you have a different card, you'd have to reference the keys as they are defined in your /etc/lirc/lircd.conf

---

### Post by hexion on 2006-11-12
> **mazirian said:**
> Well, this is silly that anyone would have to do this, but I was able to get the lirc_gpio module to build and to get lirc back up and running after my edgy upgrade by doing the following:

```

cd /usr/src/linux/drivers/media/video
sudo cp bt8xx/bt* .

```This is in edgy, using the lirc-modules-source-0.8.0-5ubuntu1 package.  The wiki article linked to above indicates that you won't be able to use the current stable packages to build gpio or i2c.  That was true in dapper, but apparently not for edgy (at least as of this date).

I repeat what I told to ilias:
>  Try using lirc-0.8.1pre**2** as explained in the HOWTO. Since 2.6.17 kernel, some files changed their place in the tree, and it was fixed in the pre2.That obvious "trick" is what everybody made before lirc.org released the PRE2 snapshot.
Please, when following a howto, do all the steps exactly as they are. If don't, it's normal that people have errors like that.

I need to say more, and please don't consider it as I'm angry or anything like that. This is a thread about my howto, not superm1 one. It could be very confuse for people trying to make their lirc work that comments here talk about another howto (which is wonderful, more complete than this, and which I recommend by the way).

In example, you (mazirian) are writing that you have problems with your lirc config. Ok, then someone may think it's a problem with this howto... but when I read your post, you say you have used lirc-modules-source-0.8.0-5ubuntu1 package, and that's clearly NOT what it's recommended in this howto and it's explained why it's needed to use another with 2.6.17 kernel.

I don't mean you have to write in another place, or not to write at all.... but it would be very considerate to clarify before posting a comment that doesn't reffer on this howto, that it's following another one. Just to not confuse people...

Thanks for understanding ;)

---

### Post by mazirian on 2006-11-12
@Hexion: Yeah, that was a bit thoughtless of me.  Sorry.  To clarify, I wasn't following your howto, but trying to make the current lirc packages work.  I prefer to keep things under package management as much as possible.  That said, you may want to modify your howto to use checkinstall.  It's a slightly safer practice that allows you to remove and/or easily reinstall the built package, without going through the hassle of debuild, etc...

FWIW, I don't seem to have any problems with ir_control...yet.  At least the keys I use most don't trigger any actions in gnome.

---

### Post by hexion on 2006-11-12
> **mazirian said:**
> @Hexion: Yeah, that was a bit thoughtless of me.  Sorry.  To clarify, I wasn't following your howto, but trying to make the current lirc packages work.  I prefer to keep things under package management as much as possible.  That said, you may want to modify your howto to use checkinstall.  It's a slightly safer practice that allows you to remove and/or easily reinstall the built package, without going through the hassle of debuild, etc...

FWIW, I don't seem to have any problems with ir_control...yet.  At least the keys I use most don't trigger any actions in gnome.

Yes, I know that having to rebuild lirc each time a new kernel image appears is boring... but for years I've had problems with lirc and at the end it works with the method I explained... so for me it's ok that way :-D

About the ir_common, it's not a problem for all TV cards. Just a few... exactly the ones defined in ir-keymaps.c
But, I'm convinced that kernel.org people will complete that file to "catch" the more cards... so maybe you'll have problems in newer kernel versions. If so, you know how to fix it ;)

P.S.: I agree with you, it's better to use things under ubuntu's package management, BUT, in this case... maybe it's not so good... Ubuntu's support of lirc is awfull and that doesn't seem to change yet. I have filed bugs against lirc, and against the kernel image... and there's no response at all. I've even sent them my "patch" for the ir_common stuff with same result.
That's why I decided to tell people to forget ubuntu's lirc packages and just build their own... when ubuntu's support of lirc change (if some day it does), I will change my recommendations :)

---

### Post by igb on 2006-11-12
First of all thanks for the HowTo. I have been having my own problems getting lirc to work: [http://www.ubuntuforums.org/showthread.php?t=296855]("http://www.ubuntuforums.org/showthread.php?t=296855")

So, I decided to follow this HowTo on a clean machine to try and get my Microsoft Media Centre remote to work. Following the steps in this thread I compiled and installed lirc with lirc_mceusb2. I can modprobe lirc_mceusb2 and it detects my remote. I can start lircd with no errors. However, as soon as I try to run irw, lircd terminates with no error message. I can see no error message in the logs.

ls -l /dev/lirc shows:

```
crw-r--r-- 1 root root 61, 0 2006-11-12 16:49 /dev/lirc
srw-rw-rw- 1 root root     0 2006-11-12 16:58 /dev/lircd
```

Any ideas on how to find out what's happening?

Ian.

---

### Post by mazirian on 2006-11-12
@Hexion: Agreed, ubuntu let's lirc pretty much slide.  I understand that there a lot of packages to manage, but here the community has stepped up with solutions and they don't seem to get implemented.  I had a bug in dapper for lirc that simply never got attended to at all, and the answer was pretty clear. In any event, I would like to see good lirc packages get into backports or someplace else.  Perhaps we could work on packaging something and getting it into backports.

---

### Post by hexion on 2006-11-13
> **igb said:**
> First of all thanks for the HowTo. I have been having my own problems getting lirc to work: [http://www.ubuntuforums.org/showthread.php?t=296855](http://www.ubuntuforums.org/showthread.php?t=296855)

So, I decided to follow this HowTo on a clean machine to try and get my Microsoft Media Centre remote to work. Following the steps in this thread I compiled and installed lirc with lirc_mceusb2. I can modprobe lirc_mceusb2 and it detects my remote. I can start lircd with no errors. However, as soon as I try to run irw, lircd terminates with no error message. I can see no error message in the logs.

ls -l /dev/lirc shows:

```
crw-r--r-- 1 root root 61, 0 2006-11-12 16:49 /dev/lirc
srw-rw-rw- 1 root root     0 2006-11-12 16:58 /dev/lircd
```Any ideas on how to find out what's happening?

Ian.

Any info with **dmesg** after you modprobe your module?

Try also this before you run lircd (as root):
> sudo rm /dev/lirc
sudo mknod /dev/lirc c 61 0

It's strange, lircd should output something when it dies... maybe you should file a bug in [www.lirc.org](www.lirc.org) if you can't make it work :-k ](*,)

Good luck

---

### Post by hexion on 2006-11-13
> **mazirian said:**
> @Hexion: Agreed, ubuntu let's lirc pretty much slide.  I understand that there a lot of packages to manage, but here the community has stepped up with solutions and they don't seem to get implemented.  I had a bug in dapper for lirc that simply never got attended to at all, and the answer was pretty clear. In any event, I would like to see good lirc packages get into backports or someplace else.  Perhaps we could work on packaging something and getting it into backports.
I fear my knowledge is very limited in package management, so I don't think I'm able to implement a solution nowadays. If someone can and I can be any helpfull in any way, I'll help... but I need to learn a few before I make more things than a simple HOWTO :mrgreen:

---

### Post by igb on 2006-11-13
```
sudo rm /dev/lirc
sudo mknod /dev/lirc c 61 0
```

That seems to have fixed it. However, it doesn't survive a reboot, even though I have it set in rc.local.

At least it's working now! I'll post another comment when I work out what's resetting the permissions on /dev/lirc.

**Edit**
I had a typo in rc.local. Once I had fixed this lirc now works after a reboot.

Ian.

---

### Post by superm1 on 2006-11-13
Hexion,

I would be glad to help add your fix to my unofficial packages.  Once ubuntu syncs the new feisty pacakges from debian unstable, I can them submit it as a debdiff against the official packages.

It will take me some time as I have other things on my plate, but I will let you know when I get it done.

---

### Post by maybeme on 2006-11-13
I get this error when running make:

```
/usr/src/lirc-0.8.1pre2/lirc_dev.c:850: error: unknown field 'open' specified in initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:850: warning: excess elements in struct initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:850: warning: (near initialization for 'fops')
/usr/src/lirc-0.8.1pre2/lirc_dev.c:851: error: unknown field 'release' specified in initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:852: warning: excess elements in struct initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:852: warning: (near initialization for 'fops')
make[5]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_dev.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_dev] Error 2
make[4]: Leaving directory '/usr/src/linux-source-2.6.17'
make[3]: *** [lirc_dev.o] Error 2
make[3]: Leaving directore '/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directore '/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directore '/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2
```

I followed the guide except I did this
```
cp /boot/config-2.6.17-10-server .config
```
In stead of the generic one, because I'm using the server edition.
I installed xserver-xorg, and am now working on openbox, so that couldn't be the problem.

I alse did
./setup.sh
in stead of
./setup

configure didn't gave me any errors.


Anybody can help me?

Thanks in advance

---

### Post by toganet on 2006-11-13
I am getting the following error when trying to compile the module:

```

In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:51:23: error: btcx-risc.h: No such file or directory
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:128: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:129: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:365: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:232:1: warning: this is the location of the previous definition
make[5]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2

```

I've tried following the HOWTO to the letter, and all the suggestions in this thread, to no avail.  I had this system working perfectly by following another howto, but after adding a second tuner to my system lirc starts, but does not allow the module lirc_gpio to be inserted.  Strangely, irw either starts and immediately exits, or responds with 'connection refused'.

Any ideas?

---

### Post by hexion on 2006-11-14
> **toganet said:**
> I am getting the following error when trying to compile the module:

```

In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:51:23: error: btcx-risc.h: No such file or directory
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:128: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:129: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:365: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:232:1: warning: this is the location of the previous definition
make[5]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2

```I've tried following the HOWTO to the letter, and all the suggestions in this thread, to no avail.  I had this system working perfectly by following another howto, but after adding a second tuner to my system lirc starts, but does not allow the module lirc_gpio to be inserted.  Strangely, irw either starts and immediately exits, or responds with 'connection refused'.

Any ideas?

> sudo cp /usr/src/linux-source-2.6.17/drivers/media/video/btcx-risc.h /usr/src/linux-source-2.6.17/drivers/media/video/bt8xx
sudo cp /usr/src/linux-source-2.6.17/drivers/media/video/btcx-risc.c /usr/src/linux-source-2.6.17/drivers/media/video/bt8xx;)

---

### Post by hexion on 2006-11-14
> **superm1 said:**
> Hexion,

I would be glad to help add your fix to my unofficial packages.  Once ubuntu syncs the new feisty pacakges from debian unstable, I can them submit it as a debdiff against the official packages.

It will take me some time as I have other things on my plate, but I will let you know when I get it done.

Cool! :mrgreen:

---

### Post by lerrup on 2006-11-14
> **hexion said:**
> ;)
Quote:
 Originally Posted by toganet View Post 
I am getting the following error when trying to compile the module:
 
 
Code:
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:51:23: error: btcx-risc.h: No such file or directory
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:128: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:129: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:365: error: field â has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:232:1: warning: this is the location of the previous definition
make[5]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2
I've tried following the HOWTO to the letter, and all the suggestions in this thread, to no avail. I had this system working perfectly by following another howto, but after adding a second tuner to my system lirc starts, but does not allow the module lirc_gpio to be inserted. Strangely, irw either starts and immediately exits, or responds with 'connection refused'.
 
 Any ideas?
Quote:
 sudo cp /usr/src/linux-source-2.6.17/drivers/media/video/btcx-risc.h /usr/src/linux-source-2.6.17/drivers/media/video/bt8xx
 sudo cp /usr/src/linux-source-2.6.17/drivers/media/video/btcx-risc.c /usr/src/linux-source-2.6.17/drivers/media/video/bt8xx 


When do I issue this command?

---

### Post by hexion on 2006-11-14
**lerrup**, when you compile lirc it complains about that file in certain location. And you have it in another location...

Simply copy it with those commands I told you and then repeat from #5 step.

---

### Post by toganet on 2006-11-14
Thank you for your help, I am making progress now, I think.  Issuing the two cp commands above did allow me to make the module, and install it.

Now I am running into the same problem I had at the beginning -- when I try to modprobe lirc_gpio, I get this error:

```

FATAL: Error inserting lirc_gpio (/lib/modules/2.6.17-10-generic/misc/lirc_gpio.ko): Invalid request code

```

This error started when I added a second bttv card to my system.  Only one of them uses the lirc_gpio module -- I wonder if it is trying to attach to the wrong instance of bttv?

---

### Post by maybeme on 2006-11-14
> **maybeme said:**
> I get this error when running make:

```
/usr/src/lirc-0.8.1pre2/lirc_dev.c:850: error: unknown field 'open' specified in initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:850: warning: excess elements in struct initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:850: warning: (near initialization for 'fops')
/usr/src/lirc-0.8.1pre2/lirc_dev.c:851: error: unknown field 'release' specified in initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:852: warning: excess elements in struct initializer
/usr/src/lirc-0.8.1pre2/lirc_dev.c:852: warning: (near initialization for 'fops')
make[5]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_dev.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_dev] Error 2
make[4]: Leaving directory '/usr/src/linux-source-2.6.17'
make[3]: *** [lirc_dev.o] Error 2
make[3]: Leaving directore '/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directore '/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directore '/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2
```

I followed the guide except I did this
```
cp /boot/config-2.6.17-10-server .config
```
In stead of the generic one, because I'm using the server edition.
I installed xserver-xorg, and am now working on openbox, so that couldn't be the problem.

I alse did
./setup.sh
in stead of
./setup

configure didn't gave me any errors.


Anybody can help me?

Thanks in advance

Anybody?

---

### Post by hexion on 2006-11-14
**maybeme,** you have to check the log in the first point you get an error message.

This have to be before the beggining of the piece of log you have posted here, and surely it will complain about a missing .h or .c file.

---

### Post by toganet on 2006-11-14
Found my problem:  I needed to pass the lirc_gpio module the correct parameters. Duh!.

Turns out lirc_gpio is smart enough to detect all but two of its parameters via modprobe:  debug and card.  

Of course, since I had added a second card, lirc_gpio didn't know which one to attach to, so it defaulted to the first.  In my case, the Leadtek card is actually /dev/video1, so I issued:

```

sudo modprobe lirc_gpio card=1

```

Then I started lirc, and voila!  It works!

Thanks to all who helped!

---

### Post by RJNFC on 2006-11-15
> **EspressoNuts said:**
> Hexion and all,

Sorry for the kind-a-newbie question, but I am trying to set up a TIRA 2.1 and everything goes normal until set 4 (./setup.sh). The result of the configuration is 
"Your hardware does not require a kernel module.

Now enter 'make' and 'make install' to compile and install the package."

Which puzzles me. If I do make and make install, I do not have a module to modprobe. Although I can "lircd" and "irw" (or for other purposes "xev") are executed, nothing happens. By ps -ef I see no lirc or irw process either.

What am I doing worng?

THIS was exactly the sort of problem I just solved.  The symptoms also include the lirc daemon crashing when you run irw.  This (for me) was for 2 reasons.  One, you need to make sure you set LIRCD_ARGS="-d /dev/ttyS0" or to whatever other device it's supposed to point to, and you need to set DRIVER="(your remote)".  In my case, DRIVER="mp3anywhere".  I also set LOAD_MODULES=false, but I'm not sure if that actually helped.  (those configuration options are all in /etc/lirc/hardware.conf)

Reason two that it wasn't working was that I had done 'setserial /dev/ttyS0 uart none' as many people noted.  Only problem is, that command turns off the serial port, so if you DON'T need it, and you run it, you'll be 100% screwed until you reboot or reset it.

Hope that helps anyone still messing with it.

---

### Post by maybeme on 2006-11-15
> **hexion said:**
> **maybeme,** you have to check the log in the first point you get an error message.

This have to be before the beggining of the piece of log you have posted here, and surely it will complain about a missing .h or .c file.

Thanks a lot, but now I have a real noob question:

Where do I find that log? I only find a config.log, but configure went fine.

Thanks again

---

### Post by Lester_Burnham on 2006-11-15
Hi,

Thanks for a great howto....

I'm using a Dvico USB Remote FusionHDTV.
I was having trouble with other tutorials, because they didn't have the same driver options as your method.
eg: USB Devices > dvico

Anyway, I've got it working and need some help on what to enter into the startup files to get it to start at boot.

```
sudo /usr/sbin/lircd --driver=dvico --device=/dev/hiddev0
```

Thanks,
Lester

---

### Post by lerrup on 2006-11-15
> **toganet said:**
> Found my problem:  I needed to pass the lirc_gpio module the correct parameters. Duh!.

Turns out lirc_gpio is smart enough to detect all but two of its parameters via modprobe:  debug and card.  

Of course, since I had added a second card, lirc_gpio didn't know which one to attach to, so it defaulted to the first.  In my case, the Leadtek card is actually /dev/video1, so I issued:

```

sudo modprobe lirc_gpio card=1

```

Then I started lirc, and voila!  It works!

Thanks to all who helped!

I've managed to get this far to the same error message.  Problem is that no matter which card number I try and define, it will not load.  I have 2 cards, one which is a leadtek dvb card.

Help me before I go and do something drastic like buy a remote and receiver!

---

### Post by nesher13 on 2006-11-16
Hexion and all,

Sorry for the kind-a-newbie question, I am trying to set up a Avermedia TV
Capture98 and everything goes normal until set 5 (make ). The result  is

root@tvmyth:/usr/src/lirc-0.8.1pre2# make
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=config.h \
             /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/usr/src/lirc-0.8.1pre2'
Making all in drivers
make[2]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.17-10-generic/build/ SUBDIRS=/usr/src/lirc-0.8.1pre2/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
mkdir -p /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_versions
rm -f /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.1pre2/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/../.. -I/lib/modules/2.6.17-10-generic/build//include/ -I/lib/modules/2.6.17-10-generic/build//drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.c
  Building modules, stage 2.
make -rR -f /usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.17-10-generic/Module.symvers -I /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/Modules.symvers -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/Modules.symvers /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.o
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.lirc_dev.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -DMODULE -c -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.mod.o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.ko /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.mod.o
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
mv Makefile.automake Makefile
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
Making all in lirc_gpio
make[3]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.17-10-generic/build/ SUBDIRS=/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
mkdir -p /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.tmp_versions
rm -f /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.lirc_gpio.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../.. -I/lib/modules/2.6.17-10-generic/build//include/ -I/lib/modules/2.6.17-10-generic/build//drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_gpio)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_gpio)" -c -o /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.tmp_lirc_gpio.o /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:51:23: error: btcx-risc.h: No such file or directory
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:128: error: field ‘top’ has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:129: error: field ‘bottom’ has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:365: error: field ‘main’ has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:232:1: warning: this is the location of the previous definition
make[5]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2
root@tvmyth:/usr/src/lirc-0.8.1pre2# make install
Making install in drivers
make[1]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers'
Making install in lirc_dev
make[2]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[3]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
test -c /dev/lirc || (/bin/bash ../../mkinstalldirs /dev && /bin/mknod /dev/lirc c 61 0)
/bin/bash ../../mkinstalldirs /lib/modules/2.6.17-10-generic/misc
mkdir /lib/modules/2.6.17-10-generic/misc
 /usr/bin/install -c -m 644 lirc_dev.ko /lib/modules/2.6.17-10-generic/misc/lirc_dev.ko
/sbin/depmod -a
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
Making install in lirc_gpio
make[2]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[2]: *** No rule to make target `install'.  Stop.
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make: *** [install-recursive] Error 1


What am I doing worng?

---

### Post by mazirian on 2006-11-16
```
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:51:23: error: btcx-risc.h: No such file or directory
```

lirc_gpio.c is looking for btcx-risc.h in your kernel source in the drivers/media/video/bt88xx directory and its not there.  Find that file in your kernel source and copy it to the bt8xx directory.  If you build the current edgy source version you;ll get the opposite problem, that is, lirc_gpio.c will look for a bunch of stuff in video that is in fact in the bt8xx dirrectory.  Go figure.

---

### Post by maybeme on 2006-11-17
I found what's missing:

```
WARNING: Symbol version dump /usr/src/linux-source-2.6.17/Module.symvers is missing modules; will have no dependencies and modversions.
```

But why don't I have that file?

I use Edgy server edition.

---

### Post by mazirian on 2006-11-17
Use modules-assistant fakesource to download and prepare a kernel source directory for you that is matched well with your running kernel.  Once m-a has worked its magic, I enter the kernel source directory and issue a "make prepare"

---

### Post by zackr on 2006-11-18
I have maybeme's exact same problem, and I'm not running a 'server' variant.

I also couldn't find a make log... where are they? I'm assuming though that it is the exact same problem as maybeme has. How do you 'use modules-assistant fakesource'? Or aren't you referring to this problem?

I'm using lirc for a serial IR receiver on Com port 1. Would this make any difference? And should I be following your guide?

---

### Post by maybeme on 2006-11-18
> **mazirian said:**
> Use modules-assistant fakesource to download and prepare a kernel source directory for you that is matched well with your running kernel.  Once m-a has worked its magic, I enter the kernel source directory and issue a "make prepare"

Thanks, this fixed my problem!
1000x thanks
btw: it's module-assistant in stead of modules-assistant :-D 

> **zackr said:**
> I have maybeme's exact same problem, and I'm not running a 'server' variant.

I also couldn't find a make log... where are they? I'm assuming though that it is the exact same problem as maybeme has. How do you 'use modules-assistant fakesource'? Or aren't you referring to this problem?

I'm using lirc for a serial IR receiver on Com port 1. Would this make any difference? And should I be following your guide?

just run
```
make > /home/user/makelog.log
```
or something like this, this will make a log of your make, or you could also scroll up (shift + pageup) and see what was the problem.

---

### Post by zackr on 2006-11-18
> **maybeme said:**
> Thanks, this fixed my problem!
1000x thanks
btw: it's module-assistant in stead of modules-assistant :-D 



just run
```
make > /home/user/makelog.log
```
or something like this, this will make a log of your make, or you could also scroll up (shift + pageup) and see what was the problem.

Yes! It is the same as your problem! "WARNING: Symbol version dump /usr/src/linux-source-2.6.17/Module.symvers
           is missing; modules will have no dependencies and modversions."
I'm trying out module-assistant fakesource at the moment... will let you know if I have any further problems in this post...

And yes, there were. 

```
 :~# modprobe lirc_serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.17-10-386/misc/lirc_serial.ko): Device or resource busy

```

What I did was allow the pristine kernel sources to be placed in /usr/src/linux-source-2.6.17-10-386, did a 'make prepare', and then unlinked the other /linux and relinked it to this one. I even did cp /boot/config-2.6.17-10-386 .config . After that I redid lirc config, make worked perfectly, and so did make install.

Now I'm getting that error. I'm assuming it's due to something still not right with either the kernel source or headers?

---------------------------------------------

I fixed it!! All I needed to do was follow the 'setserial' information here: [http://www.ubuntuforums.org/showthread.php?t=163496](http://www.ubuntuforums.org/showthread.php?t=163496)

If you don't have setserial installed, search for the package in synaptic.

---

### Post by maybeme on 2006-11-18
Did you run:
sudo setserial /dev/ttyS0 uart none
sudo setserial /dev/ttyS1 uart none
?

EDIT: added /dev/ before ttySx

---

### Post by thirstycat on 2006-11-19
ok... I've been following this thread and feel I'm just on the verge of getting lirc to work, but not there yet ](*,) 

I have a pvr-150 card, am running Edgy-server and have everything else for mythtv working perfectly.  I've previously used mythtv with a Fedora Core install and remember having to fight every step of the way to get everything to work.  Ubuntu was SO much nicer :-)

so I have tried both the updated deb packages superm1 put together, as well as compiling the latest LIRC myself from source.  In both cases, after doing a modprobe lirc_i2c, I get the following in the logs:

> lirc_dev: IR Remote Control driver registered, at major 61
[17179738.364000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

I can start lircd, but it immediately crashes when I run irw.

do the errors above suggest any kind of a solution to anyone out there?

thanks in advance--

---

### Post by bob31984 on 2006-11-20
I get the same dmesg log as thirstycat when I modprobe lirc_i2c.

When I run lircd -n, then irw in another window, lircd crashes with
```
lircd: lircd(hauppauge) ready
lircd: accepted new client on /dev/lircd
lircd: could not open /dev/lirc
lircd: default_init(): No such device
lircd: caught signal
Terminated
```

The file /dev/lirc exists, and I have set the permissions to 666. I had a similar problem when installing lirc on Dapper, and found a solution using the dev/input driver and /dev/input/event2. I guess this must be a newer version of lirc though because when I do
```
lircd -H dev/input -d /dev/input/event2 -n
```
lircd returns
```
Driver `dev/input' not supported.
Supported drivers:
        default
```
I have also tried
```
rm /dev/lirc
mknod /dev/lirc c 61 0
```

Any ideas anyone?
Cheers

---

### Post by thirstycat on 2006-11-20
interesting... if I try
```
lircd -H dev/input -d /dev/input/event2 -n
```
I can get lircd to start up properly, however, running irw still results in
```
lircd-0.8.0[6825]: lircd(userspace) ready
lircd-0.8.0[6825]: accepted new client on /dev/lircd
lircd-0.8.0[6825]: initializing '/dev/input/event2'
lircd-0.8.0[6825]: unable to open '/dev/input/event2'
lircd-0.8.0[6825]: caught signal

```

so I'm not really any further along...

bob31984: Did you install the regular desktop installation, or the "server" variant?  I used "server" and am wondering if that has anything to do with my troubles.   After all, it seems that others have followed some of the same howto's and gotten everything working.

---

### Post by bob31984 on 2006-11-20
thirstycat: Try looking in /proc/bus/input/devices to find out which event* to use (in my case it's event3), you should see something like
```
I: Bus=0001 Vendor=0070 Product=3401 Version=0001
N: Name="cx88 IR (Hauppauge WinTV 34xxx "
P: Phys=pci-0000:02:0b.0/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 0 0 10000ffc
```
I did the server installation, but I'm using the 386 kernel. uname -r gives 2.6.17-10-386

Weird that your lircd takes dev/input as a driver but not mine :(

---

### Post by thirstycat on 2006-11-20
> **bob31984 said:**
> thirstycat: Try looking in /proc/bus/input/devices to find out which event* to use (in my case it's event3)

yeah... well, one more weird thing... I don't *see* anything in there that relates to my TVCard/IR device.  Only my keyboard and "PC Speaker".   Maybe I'd better pull the PC out of the entertainment center and verify that I actually have the IR sensor plugged into the right place :???: 

Otherwise, my whole mythtv setup works beautifully.

---

### Post by trubblemaker on 2006-11-21
Got a wierd issue.  Installed mythTV (front&backend) on the same box. Installed lirc: First with this howto, then did "make uninstall" because I didn't want to patch my kernel then did superm1's howto just like thirsty cat, and I'm getting the same issue. Although mine doesn't crash, I succesffully can test with irw, and even gets correct keys (listed as hauppauge)
but I also get this in dmesg:
lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

here's the tail of my dmesg

```

[   34.552051] ivtv0-osd warning: ivtvfb_check_var
[   34.552060] ivtv0-osd warning: ivtvfb_set_par
[   36.849802] lirc_dev: IR Remote Control driver registered, at major 61 
[   36.871815] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   37.068402] bttv: driver version 0.9.16 loaded
[   37.068415] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   37.233989] cx2388x v4l2 driver version 0.0.5 loaded
[   37.252140] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[   37.252210] lirc_dev: lirc_register_plugin: sample_rate: 10
[   38.146859] ivtv0-osd warning: ivtvfb_check_var
[   38.250727] ivtv0-osd warning: ivtvfb_check_var
[   38.250738] ivtv0-osd warning: ivtvfb_set_par

```

any ideas?

---

### Post by thirstycat on 2006-11-21
It actually looks like your setup is working then... 
the line: lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted. 
may not be anything to worry about.  The "kernel tainted" part is just a warning that the module contains non-free code.  That's only a concern from a philosophical/legal standpoint.

I'm not getting the "lirc_i2c: chip found..." part.

sounds to me like you're good to go!

---

### Post by trubblemaker on 2006-11-21
yeah I think I forgot to define my buttons in myth, which I just did...

As for helping you out how did you remove the after installing from source and package?

I did the same but used "make uninstall; make clean" to purify my machine, maybe both are trying ot grab the driver?

---

### Post by thirstycat on 2006-11-24
well, I can't say for certain what I did differently, but after rebuilding the machine from scratch (I had an unrelated harddrive problem that forced this solution), everything works now.  Including my remote!

The ONE change I know I made was to download the firmware from the lirc project website (Option 2 from the howto at [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)) as opposed to using the prebuilt .deb provided by wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)  .

I can't say this was the deciding factor though since I tried on the previous system to rebuild the lirc drivers and reinstall everything using that method before with no success.  It's possible that I had some stray library from a past attempt lying around and mucking things up.  who knows... I can say that the step-by-step installation instructions in the Wiki are pretty much spot-on otherwise.

thanks for all the help and suggestions from folks in this forum!

---

### Post by Blixter on 2006-11-26
**[I][B]make install:**

Making install in drivers
make[1]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers'
make[2]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers'
make[3]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers'
test "/dev/ttyS0" = "" || test -L /dev/lirc || (/bin/sh ../mkinstalldirs /dev && cd `dirname /dev/ttyS0` && ln -s `basename /dev/ttyS0` lirc)
ln: creating symbolic link `lirc' to `ttyS0': File exists
make[3]: *** [mklink] Error 1
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make: *** [install-recursive] Error 1

gives me this error. Any idea???[/I][/B]

ohh man...i give up with lirc...2 weeks 0 no results

---

### Post by christooss on 2006-11-29
A have followed the wiki howto and I hope this is the right place to ask

> christooss@ubuntu:~$ sudo /etc/init.d/lirc start
##################################################
## LIRC IS NOT CONFIGURED                       ##
##                                              ##
## read /usr/share/doc/lirc/html/configure.html ##
##################################################
Starting lirc daemon:.


I have copyed lirc.conf for my remote file to /etc/lirc

when I try to run irw it say
> connect: Connection refused

if I run

sudo irrecord -d /dev/lirc0 lircd.conf

the out put is
> 
irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not init hardware (lircd running ? --> close it, check permissions)

And /dev/lirc0 isn't present on my system

And thoughts?

I have pinnacle system remote

---

### Post by srpouyet on 2006-12-04
Hi,

I have a problem regarding Lirc, searched the forums/google but wasn't able to find a solution...

I have installed lirc and it's working properly (irw returns output for my philips mce receiver).

The problem is that after rebooting, my remote isn't detected anymore.
The module, lirc_mseusb2, is loaded according to lsmod.
Lirc is also running according to the KDE process manager (I'm running Kubuntu).

If I restart the lirc daemon with sudo /etc/init.d/lirc restart, irw is able to pickup the mce ir signals, and works fine.

Does anybody know how to get the lirc daemon working properly on boot?

Your help is appreciated!

Cheers,
Sebastiaan (an absolute linux newbie :mrgreen: )

---

### Post by mazirian on 2006-12-04
Must have something to do with the timing of the starting of hotplug and lirc.  I know that's not helpful specifically. I'm just throwing out a theory.

---

### Post by superm1 on 2006-12-04
> **christooss said:**
> A have followed the wiki howto and I hope this is the right place to ask



I have copyed lirc.conf for my remote file to /etc/lirc

when I try to run irw it say


if I run

sudo irrecord -d /dev/lirc0 lircd.conf

the out put is


And /dev/lirc0 isn't present on my system

And thoughts?

I have pinnacle system remote

What driver is the pinacle remote supported by?  Do you know?

>  	Hi,

I have a problem regarding Lirc, searched the forums/google but wasn't able to find a solution...

I have installed lirc and it's working properly (irw returns output for my philips mce receiver).

The problem is that after rebooting, my remote isn't detected anymore.
The module, lirc_mseusb2, is loaded according to lsmod.
Lirc is also running according to the KDE process manager (I'm running Kubuntu).

If I restart the lirc daemon with sudo /etc/init.d/lirc restart, irw is able to pickup the mce ir signals, and works fine.

Does anybody know how to get the lirc daemon working properly on boot?

Your help is appreciated!

Cheers,
Sebastiaan (an absolute linux newbie :mrgreen: )

Can you check dmesg for hardware loading errors?  I have several mceusb2 transceivers, and one of them decides to fail every so often the same way.  My only solution was to hack a script together in my modprobe options (this is on gentoo).  The script forces that module and the lirc-serial module to load/unload exactly twice at which point the device is usually functional.

---

### Post by christooss on 2006-12-04
superm1: [http://lirc.sourceforge.net/remotes/pinnacle_systems/](http://lirc.sourceforge.net/remotes/pinnacle_systems/)

I think it is

---

### Post by superm1 on 2006-12-04
Okay, so if this is the remote you are using, what sort of receiver?  Is this a serial receiver?  Is this a proprietary USB receiver shipped with your remote?

---

### Post by srpouyet on 2006-12-04
> **mazirian said:**
> Must have something to do with the timing of the starting of hotplug and lirc.  I know that's not helpful specifically. I'm just throwing out a theory.

Hmmm, that might be the case. Turned off the computer, went out for a few hours and powered the pc up just now. This time the lirc daemon is running properly from the sart, the remote shows up in irkick! Must be some quirk then? :-k

If the problem persists I'll report back... for the moment I'm keeping my fingers crossed!

---

### Post by christooss on 2006-12-04
Reciever is COM port based it came with remote

---

### Post by superm1 on 2006-12-04
Okay depending on how that comm based receiver is wired, it may or may not be supported by the lirc project.  If it's wired like a standard lirc serial receiver, then you will be able to choose the lirc-serial module from module-assistant, build it, load it, and test it with that.   If its wired like anything else, then you are SOL in this case and need a different receiver.

---

### Post by trubblemaker on 2006-12-04
can't get my control to work in myth, installed lirc, no install issues it tests with irw, reads the correct keys.  dmesg looks good:

```

[   36.257059] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[   36.257140] lirc_dev: lirc_register_plugin: sample_rate: 10
[   37.016965] NET: Registered protocol family 10
[   37.017235] lo: Disabled Privacy Extensions
[   37.017599] IPv6 over IPv4 tunneling driver
[   37.554687] ivtv0-osd warning: ivtvfb_check_var
[   37.598006] ivtv0-osd warning: ivtvfb_check_var
[   37.598018] ivtv0-osd warning: ivtvfb_set_par
[   47.424599] ath0: no IPv6 routers present

```

Don't know what I need/ is left to get it going with myth.

i have setup both ~/.lircrc and  ~/.mythtv/lircrc

---

### Post by trubblemaker on 2006-12-04
turns out the irxevent wasnt' running, I had to change my .xsession to:

```

irxevent -d 
/usr/bin/mythbackend & 
/usr/bin/mythfrontend

```

and know I'm all good.

---

### Post by trubblemaker on 2006-12-04
this may be a solution for
Sebastiaan  :mrgreen: 

as you say everything is running you may need to add the 'irxevent -d' to the method that you use to start mythtvfrontend, here you can see that I start everything from my .xsession, if you have different setup, just add  irxevent -d to the file that you start mythfrontend in.

---

### Post by superm1 on 2006-12-05
> **trubblemaker said:**
> turns out the irxevent wasnt' running, I had to change my .xsession to:

```

irxevent -d 
/usr/bin/mythbackend & 
/usr/bin/mythfrontend

```and know I'm all good.
Trubblemaker, this is off topic for this thread, but don't start the backend that way.  You always want to start the backend via sudo /etc/init.d/mythtv-backend start or sudo /etc/init.d/mythtv-backend restart.

This will make sure that the backend runs with the correct permissions, nice level, and logging into /var/log/mythtv/mythbackend.log.  If you can't get it started by starting it through the init script, look at /var/log/mythtv/mythbackend.log.  It usually points to permissions related problems either on video devices or directories that myth has to write to as a backend.

---

### Post by superm1 on 2006-12-05
> **hexion said:**
> In my case, with edgy, ir_common managed number keys and several other keys...

Freeze button blocked my session...
Power button launched the logoff menu...
I think it managed too the volume keys...

I can't remember anymore and now I have it disabled :mrgreen:
Anyway, through some functions were ok, I didn't like that something chose what some of my remote control keys were for. I preffer setting them by myself.

To test what's your ir_common behaviour I think there's no other way than simply checking its keys one by one... since I couldn't find any .c file in the kernel tree with info about that. It should be here /usr/src/linux/drivers/media/common/ir-functions.c

Don't worry about "hacking" the ir_common module. It's just like making it to not recognize your card... there's no strange code added. In fact I only deleted key definitions as explained in the HOWTO.
And you can always keep your current ir_common module just renaming it before copying the new one for if you don't like it :D

Hexion,
I've chatted  & done some investigating with some other people on the mythtv team about this i2c behavior with lirc and certain remotes, and adding the "hacked" ir_common module that you are listing is not going to make it into a package.  The basic idea as I understand it is that these remotes that make it into the kernel will no longer need to depend on lirc.  Since the kernel recognizes them - they are in the HID layer and won't need a daemon like lircd to access them properly.  Keys can be remapped using xmodmap to the keys that you want them to be if they aren't sane defaults.  This can be done a  user by user basis, similar to .lircrc's  - but instead .Xmodmap's.

Think of this behavior as the exact same result as what irxevent would spit out for you if you used lirc for these remotes, but you willl be able to safely suspend the box without having to restart lircd, mythfrontend, xine, mplayer, vlc, or any other apps that access lircd.  You also won't have to worry about chaining lircd processes if you previously had to control more then one lirc device including a kernel i2c supported remote. 

I'll add a bit on the edgy wiki explaining this behavior.  It would be best if you could add a wiki page about building from source to reflect this workaround and such.  If you can move your content from the first post to the wiki page, and then link to both your wiki page from source and the wiki page on help.ubuntu.com with a brief description explaining what the purpose of each of them is, it would probably make newer users understand whats going on a bit better.  It's generally better that users don't install from CVS sources, unless they need it to use your i2c fix :)  Once you assemble a wiki page with the edgy from source method including your ir_common hacked module, I'll link to it from the main lirc edgy page.

---

### Post by gribelu on 2006-12-05
First of all a big thanks for the guide(s)!
but
I'm having a weird problem.
My remote works with irw (sample output: 0000000000000001 00 VolUp lircd.conf)
Also works with IRKick (the KDE thing).

But it doesn't 'see' the config in /home/myusername/.lircrc ! ](*,) 

My .lircrc looks like this:
```

begin
    button = VolUp
    prog = irexec
    config = vlc
end

```

wth?

---

### Post by christooss on 2006-12-05
smario1 I did choose serial port :(

---

### Post by superm1 on 2006-12-05
> **christooss said:**
> smario1 I did choose serial port :(

This being the case, 

```
sudo apt-get install setserial
sudo setserial /dev/ttyS0 uart none
sudo modprobe lirc-serial
```

Make sure the lirc-serial module is loaded.  If this works, then we can setup setserial to permanently give access to lirc on every boot.

---

### Post by trubblemaker on 2006-12-05
> **superm1 said:**
> sudo /etc/init.d/mythtv-backend start
thanks once again for your knowledge and advice, i've made the correction

---

### Post by christooss on 2006-12-05
superm1

> christooss@ubuntu:~$ sudo modprobe lirc-serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.17-10-386/misc/lirc_serial.ko): Device or resource busy
christooss@ubuntu:~$ sudo rmmod lirc-serial
ERROR: Module lirc_serial does not exist in /proc/modules
christooss@ubuntu:~$ sudo modprobe lirc-serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.17-10-386/misc/lirc_serial.ko): Device or resource busy
christooss@ubuntu:~$ sudo rmmod lirc_serial
ERROR: Module lirc_serial does not exist in /proc/modules
christooss@ubuntu:~$ sudo modprobe lirc_serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.17-10-386/misc/lirc_serial.ko): Device or resource busy


---

### Post by superm1 on 2006-12-05
> **christooss said:**
> superm1
Check ```
dmesg
```, it should tell you why the serial port is busy.

You did do 
```
sudo setserial /dev/ttyS0 uart none
```

right?

---

### Post by christooss on 2006-12-05
this is dmesg

> [17201833.400000] lirc_dev: IR Remote Control driver registered, at major 61 
[17201833.404000] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[17201833.404000] lirc_serial: port 02f8 already in use
[17201833.404000] lirc_serial: use 'setserial /dev/ttySX uart none'
[17201833.404000] lirc_serial: or compile the serial port driver as module and
[17201833.404000] lirc_serial: make sure this module is loaded first
[17201849.568000] lirc_serial: port 02f8 already in use
[17201849.568000] lirc_serial: use 'setserial /dev/ttySX uart none'
[17201849.568000] lirc_serial: or compile the serial port driver as module and
[17201849.568000] lirc_serial: make sure this module is loaded first
[17201967.516000] lirc_serial: port 02f8 already in use
[17201967.516000] lirc_serial: use 'setserial /dev/ttySX uart none'
[17201967.516000] lirc_serial: or compile the serial port driver as module and
[17201967.516000] lirc_serial: make sure this module is loaded first
[17202240.812000] lirc_serial: port 02f8 already in use
[17202240.812000] lirc_serial: use 'setserial /dev/ttySX uart none'
[17202240.812000] lirc_serial: or compile the serial port driver as module and
[17202240.812000] lirc_serial: make sure this module is loaded first


Yes I have done setserial

---

### Post by superm1 on 2006-12-05
Ah but you aren't using /dev/ttyS0.  That IRQ you are using appears to be /dev/ttyS1.  Try setserial on that device

```
sudo setserial /dev/ttyS1 uart none
```

---

### Post by christooss on 2006-12-05
ok no error now. But still when I run irw there is error Conection refused.

Or is there other way to test remote?
Or do I have to do anything first?

---

### Post by bodhi.zazen on 2006-12-05
Nice How-to

This thread has been added to the UDSF wiki.

[Lirc](http://doc.gwos.org/index.php/Lirc)

---

### Post by superm1 on 2006-12-06
> **christooss said:**
> ok no error now. But still when I run irw there is error Conection refused.

Or is there other way to test remote?
Or do I have to do anything first?
Lircd has to be running for irw to work.  so ```
sudo /etc/init.d/lirc start
``` will start lircd.

---

### Post by christooss on 2006-12-06
> christooss@ubuntu:~$ sudo /etc/init.d/lirc start
Password:
##################################################
## LIRC IS NOT CONFIGURED                       ##
##                                              ##
## read /usr/share/doc/lirc/html/configure.html ##
##################################################
Starting lirc daemon:.
christooss@ubuntu:~$ ir
ircat       irman2lirc  irrecord    irw         
irexec      irpty       irsend      
christooss@ubuntu:~$ irw
connect: No such file or directory
christooss@ubuntu:~$ irw /dev/ttyS
ttyS0  ttyS1  ttyS2  ttyS3  
christooss@ubuntu:~$ irw /dev/ttyS1
connect: Connection refused


Here is this output

---

### Post by superm1 on 2006-12-06
> **christooss said:**
> Here is this output
This being the case, you haven't placed a lircd.conf in /etc/lirc to replace the holder file.  If you have a remote (which i recall you did find one) lircd.conf, then remove /etc/lirc/lircd.conf and place this file in its place.  Lirc should then be able to start.

---

### Post by christooss on 2006-12-06
christooss@ubuntu:~$ ls /etc/lirc
hardware.conf  lircd.conf   lirc-modules-source.conf
lirc.conf      lircmd.conf  lirc-modules-source.conf.ucf-old

And lirc.conf is pinacle one :(

---

### Post by superm1 on 2006-12-06
You misread, you should remove the old **lircd.conf** and replace it with the pinnacle lirc**d**.conf

---

### Post by christooss on 2006-12-06
ok thanks for making it clear

Now really no errors. But how to test now?

irw doesn't give me any output

---

### Post by trubblemaker on 2006-12-06
easy way: reboot, then try

```
sudo /etc/init.d/lirc start
irw
```
or
slightly more complex 
```
 sudo modprobe lirc_<your driver> 
sudo /etc/init.d/lirc start
irw
```
(an example of a driver is modprobe lirc_gpio)

then press buttons on your remote you should see key presses them come up on a terminal, when your done, press <crtl> + 'c' to quit.

---

### Post by christooss on 2006-12-06
nope no output from irw :(

---

### Post by superm1 on 2006-12-06
> **christooss said:**
> nope no output from irw :(
Like I was saying, it's pretty unlikely that the serial receiver for this remote is wired the same way that general serial receivers that are used with lirc are wired.  If you've got all this software configured right, you should be getting output from irw.  

If you want to try just the serial receiver to see if that is working like a standard lirc receiver, without lircd running, but with lirc_serial loaded, and setserial ran

sudo cat /dev/lirc0

Point your remote at the receiver and press some buttons.  With any luck you will be getting output when pressing buttons.  If this is the case, but it doesn't work with irw when lircd is running, then you need to record your own remote to use instead.

---

### Post by tfmccull on 2006-12-06
I have a Hauppauge remote, seems to work fine, need to remap some buttons though.

i tried to use irrecord so i could build my own file, but i keep getting this message:

gap not found, can"t continue error from irrecord

The system is seeing the button pushes (it display a period on screen every time i hit a button) if i stop pushing buttons after a few seconds i get that error and it spits me to a prompt without writing anything to the file.

Second question: Being a noob, are there any GUI-based utilites for Gnome that will allow me to build a proper config file for LIRC (al l the while learning about the process?)

---

### Post by superm1 on 2006-12-06
> **tfmccull said:**
> I have a Hauppauge remote, seems to work fine, need to remap some buttons though.

i tried to use irrecord so i could build my own file, but i keep getting this message:

gap not found, can"t continue error from irrecord

The system is seeing the button pushes (it display a period on screen every time i hit a button) if i stop pushing buttons after a few seconds i get that error and it spits me to a prompt without writing anything to the file.

Second question: Being a noob, are there any GUI-based utilites for Gnome that will allow me to build a proper config file for LIRC (al l the while learning about the process?)

Second Question:
Not as of yet.  Either me or someone else on the ubuntu mythtv team will eventually be writing one that is planned to be integrated in the ubuntu mythtv installer that we will be working on.
.

First Question:
when you say *remap,* do you mean some of the buttons just aren't recognized?  Or you just want to change what they are called?

---

### Post by christooss on 2006-12-06
[http://gentoo-wiki.com/HOWTO_LIRC#Pinnacle_PCTV_remote](http://gentoo-wiki.com/HOWTO_LIRC#Pinnacle_PCTV_remote)

I will try to load 8*** module. And we'll se how it goes

I don't know how but I hope I will get a solution

---

### Post by tfmccull on 2006-12-06
Some but not all of the buttons work. But instead of copying someone elses config from somewhere i'd like to understand what it is that i'm doing, if only on a basic level.

Any idea about the error message? Or how to i see the output of the remote buttons so i can build a proper lirc.conf file. (I realize that the acutal mapping of the buttons are in the lirrc file)

---

### Post by superm1 on 2006-12-06
> **tfmccull said:**
> Some but not all of the buttons work. But instead of copying someone elses config from somewhere i'd like to understand what it is that i'm doing, if only on a basic level.

Any idea about the error message? Or how to i see the output of the remote buttons so i can build a proper lirc.conf file. (I realize that the acutal mapping of the buttons are in the lirrc file)
You will have to double check on this, but I have read in the past that recording from i2c, gpio, mceusb, and mceusb2 devices won't be able to consistently produce all of the information necessary for a lircd.conf.  A serial receiver is necessary.  I know personally, i've tried to make several with mceusb2 receivers, and all that they ever produce is junk that works 5 percent of the time for transmitting but works all the time for receiving.

These hauppauge remotes are pretty popular though, you should be able to find a lircd.conf that includes all of your buttons somewhere.  If you eventually produce a more inclusive one, or locate one - post a link to it here and i'll add it to the wiki (or add it yourself).

---

### Post by trubblemaker on 2006-12-06
link for [new hauppage grey remote]("http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt") with arrow keys and coloured keys on the bottom

[lircrc]("http://wilsonet.com/mythtv/lircrc-haupgrey.txt") for older grey controller

both brought to you buy: [Jarod's Guide for lirc]("http://wilsonet.com/mythtv/fcmyth.php#lirc")

---

### Post by beamish on 2006-12-09
> **ilias said:**
> Here's my case.
I'm using dapper drake...although i don't think there's any difference...
I compiled a custom kernel from source. the 2.6.18.
configure goes ok but when I enter make I get the following error
```
/usr/src/lirc-0.8.1pre1/drivers/lirc_dev/lirc_dev.c:54:35: error: linux/devfs_fs_kernel.h: No such file or directory
```
this is the ouput when I enter the locate command
```
$ locate devfs_fs_kernel.h
/usr/include/linux/devfs_fs_kernel.h
/usr/src/linux-source-2.6.15/include/linux/devfs_fs_kernel.h
/usr/src/linux-headers-2.6.15-27-386/include/linux/devfs_fs_kernel.h
/usr/src/linux-headers-2.6.15-27/include/linux/devfs_fs_kernel.h

```
As you can see the specific files exists on the 2.6.15 kernel.
so i do
```
ln -s /usr/src/linux-source-2.6.15 /usr/src/linux
```
and
```
ln -s /usr/src/linux/drivers /usr/src/lirc-0.8.1pre1/drivers/drivers
```
and I still get the same output
what's wrong?

It appears that devfs_fs_kernel.h was removed or moved in later kernels. I got around this compile error by simply commenting it out in the lirc source.

---

### Post by dawson64 on 2006-12-10
I'm trying to get my remote to work with my PVR-350.  I followed superm1's how to and get to the point where I run ```
sudo /etc/init.d/lirc start 
irw
```
but when I push buttons on the remote I do not get anything back.  I've double checked the connection...

```
dmesg | grep lirc
[42949569.890000] lirc_dev: IR Remote Control driver registered, at major 61
[42949569.910000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[42949570.320000] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[42949570.320000] lirc_dev: lirc_register_plugin: sample_rate: 10

```

---

### Post by superm1 on 2006-12-10
> **dawson64 said:**
> I'm trying to get my remote to work with my PVR-350.  I followed superm1's how to and get to the point where I run ```
sudo /etc/init.d/lirc start 
irw
```but when I push buttons on the remote I do not get anything back.  I've double checked the connection...

```
dmesg | grep lirc
[42949569.890000] lirc_dev: IR Remote Control driver registered, at major 61
[42949569.910000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[42949570.320000] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[42949570.320000] lirc_dev: lirc_register_plugin: sample_rate: 10

```

Is the 350 I2C supported directly by the kernel now?  eg, if you press a button, say the 1 button without lirc running or the lirc_i2c modules loaded, do you get a 1 in a terminal?

If so, then you will either have to use hexion's fix or just use xmodmap to remap your keys.

---

### Post by dawson64 on 2006-12-10
I'm pretty new to this, can you give me some cmds that i can run to stop this and where to watch in the terminal?
Thanks!

> **superm1 said:**
> Is the 350 I2C supported directly by the kernel now?  eg, if you press a button, say the 1 button without lirc running or the lirc_i2c modules loaded, do you get a 1 in a terminal?

If so, then you will either have to use hexion's fix or just use xmodmap to remap your keys.

---

### Post by superm1 on 2006-12-11
Well, easiest way to go -

Open up a terminal, and type 

```
xev
```


Xev will listen for keycodes returned by remotes or by mouse keystrokes.  With xev running, if the kernel mode i2c driver has taken priority, you will see it return keystrokes when pressing buttons on the remote.

---

### Post by aissen on 2006-12-11
Hi.

If I hacks the ir-keymaps and recompile the ir-common module. After this and reboot the machine whe I press any of my button I get this message in syslog:

Dec 11 21:28:38 bender kernel: [  121.635621] bttv IR (card=123): unknown key: key=0x1c raw=0x1c down=0
Dec 11 21:28:40 bender kernel: [  122.833820] bttv IR (card=123): unknown key: key=0x21 raw=0x21 down=1
Dec 11 21:28:41 bender kernel: [  123.100086] bttv IR (card=123): unknown key: key=0x21 raw=0x21 down=0
Dec 11 21:28:42 bender kernel: [  123.659246] bttv IR (card=123): unknown key: key=0x2e raw=0x2e down=1
Dec 11 21:28:42 bender kernel: [  123.739124] bttv IR (card=123): unknown key: key=0x2e raw=0x2e down=0
Dec 11 21:28:42 bender kernel: [  123.792377] bttv IR (card=123): unknown key: key=0x1e raw=0x1e down=1
Dec 11 21:28:42 bender kernel: [  123.898885] bttv IR (card=123): unknown key: key=0x1e raw=0x1e down=0


What's wrong?? 

Thx,

.-aissen

---

### Post by dawson64 on 2006-12-11
When I rn xev I get
```

:~$ xev
xev:  unable to open display ''
:~$

```

> **superm1 said:**
> Well, easiest way to go -

Open up a terminal, and type 

```
xev
```


Xev will listen for keycodes returned by remotes or by mouse keystrokes.  With xev running, if the kernel mode i2c driver has taken priority, you will see it return keystrokes when pressing buttons on the remote.

---

### Post by superm1 on 2006-12-11
> **dawson64 said:**
> When I rn xev I get
```

:~$ xev
xev:  unable to open display ''
:~$

```

This requires the place you launch this from has an X server running.  If your on a remote computer, you will need to X forawrd, or if your on a local computer - start from a normal terminal app, eg gnome-terminal instead of switching to a vritual terminal.

---

### Post by dawson64 on 2006-12-11
> **superm1 said:**
> This requires the place you launch this from has an X server running.  If your on a remote computer, you will need to X forawrd, or if your on a local computer - start from a normal terminal app, eg gnome-terminal instead of switching to a vritual terminal.

Ah...  I ran xev and am still not getting anything to show up when i push remote buttons.:(

---

### Post by superm1 on 2006-12-12
> **dawson64 said:**
> Ah...  I ran xev and am still not getting anything to show up when i push remote buttons.:(
Okay, well we at least know that the 350's i2c isn't supported by the kernel as of now.  Going back to lirc, have you placed the correct hauppauge remote in /etc/lirc/lircd.conf?  There are multiple different hauppauge devices each with their own custom remote to place in /etc/lirc/lircd.conf

---

### Post by newcoventry on 2006-12-12
I wanted to chime in here and thank you all for the huge help this forum has been for me.  I was pulling out my hair trying to get lirc running.  I followed all the instructions posted here and in the mythtv install frontend&backend page [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)
I am running the standard install referenced at the site above with a Hauppauge 150 MCE with the new RC6 Phillips remote.
After much trial and error the fix for me was to follow these instructions: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)  after completing the "install one device option" I then went through as though I was installing a second device, then everything kicked on, why it worked, I honestly have no clue.

I just want to give some hope out there for everyone who is ready to throw their lirc_mceusb2 remote out the window.

---

### Post by TechnoPenguin on 2006-12-15
I used the Wiki way to do this with a homebrew serial modules (**lirc_serial**) and I just kept fighting for hours, until I came up with the [Fedora MythTV Link]("http://wilsonet.com/mythtv/fcmyth.php#lirc") (Thanks Trubblemaker!)

There I found out that if I use the serial modules, I have to put the following lines to */etc/modprobe.conf*

```
alias char-major-61 lirc_serial
options lirc_serial irq=4 io=0x3f8
install lirc_serial /bin/setserial /dev/ttyS0 uart none ;\
    /sbin/modprobe --ignore-install lirc_serial 
```

This only applies to COM1. Check the link for COM2.

Anyway after I tried this + reboot, ran lirc and irw and I got codes! Yay!

---

### Post by superm1 on 2006-12-15
> **TechnoPenguin said:**
> I used the Wiki way to do this with a homebrew serial modules (**lirc_serial**) and I just kept fighting for hours, until I came up with the [Fedora MythTV Link]("http://wilsonet.com/mythtv/fcmyth.php#lirc") (Thanks Trubblemaker!)

There I found out that if I use the serial modules, I have to put the following lines to */etc/modprobe.conf*

```
alias char-major-61 lirc_serial
options lirc_serial irq=4 io=0x3f8
install lirc_serial /bin/setserial /dev/ttyS0 uart none ;\
    /sbin/modprobe --ignore-install lirc_serial 
```This only applies to COM1. Check the link for COM2.

Anyway after I tried this + reboot, ran lirc and irw and I got codes! Yay!
Consider yourself eternally mentioned in the wiki :)
[https://help.ubuntu.com/community/Install_Lirc_Edgy#head-6ceb2a6bf65eddb537dd6038798144b163ab4a0a](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-6ceb2a6bf65eddb537dd6038798144b163ab4a0a)

---

### Post by TechnoPenguin on 2006-12-15
o.O My first day with Ubuntu and these forums, and I'm making some rep already :) 

Now I'll have to make totem listen to what I say. I tried to run irexec as daemon and made it to send commands like *totem --play*, but if I press a button on my remote, it takes at least 10 seconds to register it. Not good.

EDIT: Well, it seems that totem is LIRC-friendly and has native support for *.lircrc*, so that solved the problem.

---

### Post by superm1 on 2006-12-15
> **TechnoPenguin said:**
> 
EDIT: Well, it seems that totem is LIRC-friendly and has native support for *.lircrc*, so that solved the problem.

oooh, this is good to know.  I had no idea...

---

### Post by christooss on 2006-12-16
Thanks technopenguin. I will try this with my reciever.

---

### Post by christooss on 2006-12-18
technopenguin did you do this step from wikihowto?

> Modify LOAD_MODULES=false to be LOAD_MODULES=true. Also, add your module to the line that is MODULES="". Your module is the name of the module you chose previously to build prefixed by lirc_. So for the mceusb driver, this would be lirc_mceusb.

Cause editing modprobe.conf doesn't seem to work. Irw stop right after running it. NO "hangiging" mentioned in wiki howto

---

### Post by dsegarra on 2006-12-18
HI all. I hardly write in forums as everytime I have a problem I search and search and find the solutions thanks to all the bright people that write in them. This time I had no choice but to write and see if any other ideas might help me get thru this. I have a PVR-150 (1045) with IR Remote Blaster. I have tried alot ALOT of different options, tutorials, hacks, you name it to get Lirc Working with no success at all. My dmesg output is similar to others:

[17179591.728000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179591.732000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179591.876000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179591.876000] lirc_dev: lirc_register_plugin: sample_rate: 10


When I irw I get no outputs on the terminal. Any different leads? ..THanks, anything will be helpful right now! . I really want to record some programs on premium channels and for that I need my set up box . By the way MythTv works perfectly sound and everything. Is just the Remote. Thanks again.

---

### Post by superm1 on 2006-12-18
> **dsegarra said:**
> HI all. I hardly write in forums as everytime I have a problem I search and search and find the solutions thanks to all the bright people that write in them. This time I had no choice but to write and see if any other ideas might help me get thru this. I have a PVR-150 (1045) with IR Remote Blaster. I have tried alot ALOT of different options, tutorials, hacks, you name it to get Lirc Working with no success at all. My dmesg output is similar to others:

[17179591.728000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179591.732000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179591.876000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179591.876000] lirc_dev: lirc_register_plugin: sample_rate: 10


When I irw I get no outputs on the terminal. Any different leads? ..THanks, anything will be helpful right now! . I really want to record some programs on premium channels and for that I need my set up box . By the way MythTv works perfectly sound and everything. Is just the Remote. Thanks again.

Well at this point, if you have the lirc modules loading fine and detecting your card, but irw won't output any data - the most likely culprit if your /etc/lirc/lircd.conf.  Are you sure you are using the one for the appropriate Hauppauge remote?

---

### Post by dsegarra on 2006-12-19
I dont know. I dont know which lircd.conf I have or which one I need. I have tried a few I found online. I have the grey remote with colored buttons. Any thoughts? thanks a million.

---

### Post by superm1 on 2006-12-19
> **dsegarra said:**
> I dont know. I dont know which lircd.conf I have or which one I need. I have tried a few I found online. I have the grey remote with colored buttons. Any thoughts? thanks a million.

Well at least one of these should work:
[http://lirc.sourceforge.net/remotes/hauppauge/lircd.conf.hauppauge](http://lirc.sourceforge.net/remotes/hauppauge/lircd.conf.hauppauge)

Also, note that you can have multiple remotes in your lircd.conf.  If you have 1 or 53 remotes, it works just the same.

---

### Post by dsegarra on 2006-12-19
superm 1

THanks! I will try that when I get back to my house.

---

### Post by voidmage on 2006-12-22
I'm having zero luck with my PVR-150MCE remote.  I can start lirc but when I run irw it goes straight back to shell. I have tried configuring lirc to use two devices, but no luck there either.

EDIT: Also, when I push buttons on the remote the light on the IR receiver lights up, so I know that works. It's probably something about lircd connecting to it, but I have no idea what it is or how to fix it.

output from lirc after starting irw:
```

lircd-0.8.0[8302]: lircd(userspace) ready
lircd-0.8.0[8302]: accepted new client on /dev/lircd
lircd-0.8.0[8302]: could not get file information for /dev/lirc
lircd-0.8.0[8302]: default_init(): No such file or directory
lircd-0.8.0[8302]: caught signal
Terminated

```

dmesg | grep lirc:
```

[17179597.528000] lirc_dev: IR Remote Control driver registered, at major 61
[17179597.528000] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179597.528000] lirc_mceusb2: USB remote driver for LIRC v0.23
[17179597.528000] lirc_mceusb2: Martin Blatter <martin_a_blatter@yahoo.com>, Daniel Melander <lirc@rajidae.se>
[17179597.532000] usbcore: registered new driver lirc_mceusb2

```

lsmod | grep lirc:
```

lirc_mceusb2           15008  0
lirc_dev               16244  1 lirc_mceusb2
usbcore               134912  5 lirc_mceusb2,usbhid,ehci_hcd,ohci_hcd

```

cat /proc/bus/usb/devices:
```


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=10
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=1784 ProdID=0001 Rev= 0.00
S:  Manufacturer=Topseed
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=TS0006LL
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms

T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0b43 ProdID=0003 Rev=19.12
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=8ms

```

lsusb:
```

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0b43:0003 Play.com, Inc. PS2 Controller Converter
Bus 001 Device 002: ID 1784:0001
Bus 001 Device 001: ID 0000:0000

```

---

### Post by ajm2005 on 2006-12-22
:)

---

### Post by trubblemaker on 2006-12-23
to be honest, building from source is considered the a very good way to create a program for your computer.  It makes the program tailor designed for your specific hardware.  As you are new to linux, I totally get you being afraid of building from source.  I didn't get it either and avoided it like the plague.  Then one day I couldn't find a way to get my wireless working, and I took the plunge and built the module from source.  It did everything for me correctly on the first try.  I could've saved alot of time if I'd done that before I lost 2 days looking for another method.

OK PREACHING IS DONE here's an easy [howto]("https://help.ubuntu.com/community/Install_Lirc_Edgy")  written in Enlish. It doesn't involve "make" much, and uses apt-get for most of the installation.  It's very step by step and should work well for you, if you have more questions post back here.

I should also mention that your chances of getting help are diminished as you insulted the author of this thread, but I'm sure other will still try and help you if you don't post with the same attitude next time.

---

### Post by mariuss on 2006-12-25
> **thirstycat said:**
> well, I can't say for certain what I did differently, but after rebuilding the machine from scratch (I had an unrelated harddrive problem that forced this solution), everything works now.  Including my remote!

The ONE change I know I made was to download the firmware from the lirc project website (Option 2 from the howto at [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)) as opposed to using the prebuilt .deb provided by wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)  .

I am having the exact same problem. I am confused about the ONE change mentioned above. The link points to the ivtv howto, I can't see an option 2 or anything related to lirc there. Are you sure this is the right link?

---

### Post by mariuss on 2006-12-25
> **voidmage said:**
> I'm having zero luck with my PVR-150MCE remote.  I can start lirc but when I run irw it goes straight back to shell. I have tried configuring lirc to use two devices, but no luck there either.

I am having the exact same problems as you.

There is one thing I noticed in your configuration though, you seem to be using the mceusb2 driver, but for your remote, afaik, you should use i2c.

Marius

---

### Post by eclisse on 2006-12-26
> **superm1 said:**
> I've actually put together a howto already on the wiki that doesn't install anything from source. 


Works like a charm. 10 mins and my MCE remote was working perfectly. Thank you, superm1!

Paolo

---

### Post by mariuss on 2006-12-26
> **eclisse said:**
> Works like a charm. 10 mins and my MCE remote was working perfectly. Thank you, superm1!

Could anyone get a hauppauge pvr150 silver remote working using [superm1's howto]("https://help.ubuntu.com/community/Install_Lirc_Edgy") (under Edgy 386)?

---

### Post by trubblemaker on 2006-12-26
I got the pvr-350 working but I did have to manually add irexec to my .xsession file so that it started at boot.  Otherwise I added any info to the howto that I might have done differently.

---

### Post by superm1 on 2006-12-27
> **voidmage said:**
> I'm having zero luck with my PVR-150MCE remote.  I can start lirc but when I run irw it goes straight back to shell. I have tried configuring lirc to use two devices, but no luck there either.

EDIT: Also, when I push buttons on the remote the light on the IR receiver lights up, so I know that works. It's probably something about lircd connecting to it, but I have no idea what it is or how to fix it.

output from lirc after starting irw:
```

lircd-0.8.0[8302]: lircd(userspace) ready
lircd-0.8.0[8302]: accepted new client on /dev/lircd
lircd-0.8.0[8302]: could not get file information for /dev/lirc
lircd-0.8.0[8302]: default_init(): No such file or directory
lircd-0.8.0[8302]: caught signal
Terminated

```dmesg | grep lirc:
```

[17179597.528000] lirc_dev: IR Remote Control driver registered, at major 61
[17179597.528000] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179597.528000] lirc_mceusb2: USB remote driver for LIRC v0.23
[17179597.528000] lirc_mceusb2: Martin Blatter <martin_a_blatter@yahoo.com>, Daniel Melander <lirc@rajidae.se>
[17179597.532000] usbcore: registered new driver lirc_mceusb2

```lsmod | grep lirc:
```

lirc_mceusb2           15008  0
lirc_dev               16244  1 lirc_mceusb2
usbcore               134912  5 lirc_mceusb2,usbhid,ehci_hcd,ohci_hcd

```cat /proc/bus/usb/devices:
```


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=10
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=1784 ProdID=0001 Rev= 0.00
S:  Manufacturer=Topseed
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=TS0006LL
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms

T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0b43 ProdID=0003 Rev=19.12
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=8ms

```lsusb:
```

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0b43:0003 Play.com, Inc. PS2 Controller Converter
Bus 001 Device 002: ID 1784:0001
Bus 001 Device 001: ID 0000:0000

```
Your problem here appears to stem from starting lirc without the init script.  The init script sets a bunch of defaults that are important to its functionality.

```
sudo /etc/init.d/lirc restart
```

Should do it hopefully :)

---

### Post by superm1 on 2006-12-27
> **mariuss said:**
> I am having the exact same problem. I am confused about the ONE change mentioned above. The link points to the ivtv howto, I can't see an option 2 or anything related to lirc there. Are you sure this is the right link?
This is off subject from lirc, but the method of doing the ivtv-firmware has changed.  The new way is the only way listed there because it shows you the license prior to installation which Hauppaugge requires.

---

### Post by superm1 on 2006-12-27
> **mariuss said:**
> I am having the exact same problems as you.

There is one thing I noticed in your configuration though, you seem to be using the mceusb2 driver, but for your remote, afaik, you should use i2c.

Marius
Some pvr150s use the mceusb2 remote, some are i2c.  Depends if you have an external USB receiver with it or not.

---

### Post by zackr on 2006-12-27
I'm having a problem with autoloading LIRC at boot time using the serial interface.

I did the following:

echo "alias char-major-61-* lirc_serial" | sudo tee /etc/modprobe.d/lirc

Then I added the two lines to rc.local following that per the guide.

However, it appears that LIRC fails to even start. After going 'sudo init 1' then 'sudo init 5', I tried 'sudo killall lircd', but it couldn't kill the process because it wasn't even running.

I have also made a lirc conf file, and started it up by putting this in the sessions manager: irexec -d /root/.lircrc

Now, I know this is working fine since all I have to do is start LIRC manually by going 'sudo lircd' and then running the irexec command.

What I want to know is: what's the most elegant way to get LIRC started at boot/end of runmode initialization, and then run irexec?

---

### Post by mariuss on 2006-12-27
> **superm1 said:**
> Some pvr150s use the mceusb2 remote, some are i2c.  Depends if you have an external USB receiver with it or not.

Hm, this could be my problem then. I have an external USB receiver (and it also has an IR blaster). Is this the mceusb2 then?

If yes, how can I safely remove the i2c driver I already installed?

Thanks,
Marius

---

### Post by dsegarra on 2006-12-27
Just for the records and another option.

This is what worked for me:

After installing the lirc-modules and linux source:

cd /usr/src
tar -xvzf lirc-modules.tar.gz
tar -xjvf linux-source-2.6.17.tar.bz2
ln -s /usr/src/linux-source-2.6.17 /usr/src/linux
cd linux
make -kpkg --revision 2.6.17
depmod -ae && update-modules
modprobe lirc_dev
modprobe lirc_i2c
dmesg | grep lirc
irw

and it worked!. Of course I downloaded the correct lircd.conf & lircrc.conf as well.

---

### Post by dsegarra on 2006-12-27
I am now trying to find a tutorial on setting up the transmitter to send signals to my cable box. Any ideas, links, How To's?

---

### Post by mariuss on 2006-12-27
> **dsegarra said:**
> I am now trying to find a tutorial on setting up the transmitter to send signals to my cable box. Any ideas, links, How To's?

Try this:
[https://help.ubuntu.com/community/MythTV_Edgy_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_Edgy_External_Channel_Changer)

---

### Post by dsegarra on 2006-12-27
mariuss

thanks!

---

### Post by Schuenemann on 2006-12-28
Sorry for the newbie question:
I bought a USB Irda device [(here's its link)]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=150055114459&ssPageName=STRK:MEWN:IT&ih=005") on ebay to be able to connect my cellphone (Nokia 6020) to my computer.

Is this tutorial what I need to make that possible?

Thanks

---

### Post by dsegarra on 2006-12-28
Let me get this straight. I have to re-configure my hauppauge remote to control the set up box?. This way it will change the channels in the set up box and not in mythtv?. Kind of confused here.


Thanks

---

### Post by mariuss on 2006-12-28
> **dsegarra said:**
> Let me get this straight. I have to re-configure my hauppauge remote to control the set up box?. This way it will change the channels in the set up box and not in mythtv?. Kind of confused here.

Ideally you want MythTV to control your set-top box. It can be done with an IR blaster (I thought that this is what you meen with "transmitter") or wither serial or firewire cable.

Marius

---

### Post by Analord on 2006-12-29
Card tv2000xp leadtek

When modprobe lirc_gpio

FATAL: Error inserting lirc_gpio (/lib/modules/2.6.17-10-generic/misc/lirc_gpio.ko): Invalid request code

Dmesg says :
[http://paste.ubuntu-nl.org/39295/](http://paste.ubuntu-nl.org/39295/)


Any help would be apreciated.](*,)

---

### Post by mariuss on 2006-12-29
> **mariuss said:**
> Hm, this could be my problem then. I have an external USB receiver (and it also has an IR blaster). Is this the mceusb2 then?

If yes, how can I safely remove the i2c driver I already installed?

So, using the mceusb2 driver helped, but it was not all. I also needed a different lircd.conf file and found the right one on the [Sysop.ca blog]("http://www.sysop.ca/?p=55").

The irw test works now :-D

---

### Post by zackr on 2006-12-30
Hi, can someone please reply to my post 157 pls?

---

### Post by superm1 on 2006-12-30
> **Schuenemann said:**
> Sorry for the newbie question:
I bought a USB Irda device [(here's its link)]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=150055114459&ssPageName=STRK:MEWN:IT&ih=005") on ebay to be able to connect my cellphone (Nokia 6020) to my computer.

Is this tutorial what I need to make that possible?

Thanks
When you plug this device in, see what it shows up in during
```
lsusb
```

It may or may not be supported by the lirc IRDA drivers.  (Most likely not)

What was your intention to use with your cellphone?  Does your cellphone even have an IR port (most don't)

---

### Post by superm1 on 2006-12-30
> **Analord said:**
> Card tv2000xp leadtek

When modprobe lirc_gpio

FATAL: Error inserting lirc_gpio (/lib/modules/2.6.17-10-generic/misc/lirc_gpio.ko): Invalid request code

Dmesg says :
[http://paste.ubuntu-nl.org/39295/](http://paste.ubuntu-nl.org/39295/)


Any help would be apreciated.](*,)
Are you using hexion's hack here?  You may have to do this if you want to use lirc with this device since it may be supported by the kernel.  It would be good if he could comment on this and when its needed.

---

### Post by superm1 on 2006-12-30
> **zackr said:**
> I'm having a problem with autoloading LIRC at boot time using the serial interface.

I did the following:

echo "alias char-major-61-* lirc_serial" | sudo tee /etc/modprobe.d/lirc

Then I added the two lines to rc.local following that per the guide.

However, it appears that LIRC fails to even start. After going 'sudo init 1' then 'sudo init 5', I tried 'sudo killall lircd', but it couldn't kill the process because it wasn't even running.

I have also made a lirc conf file, and started it up by putting this in the sessions manager: irexec -d /root/.lircrc

Now, I know this is working fine since all I have to do is start LIRC manually by going 'sudo lircd' and then running the irexec command.

What I want to know is: what's the most elegant way to get LIRC started at boot/end of runmode initialization, and then run irexec?

Well elegant depends on how you started out here.  Are you using ubuntu packaging, or a general lirc install from source?  Ubuntu packaging provides init scripts to start lirc, and there is a method to guarantee setserial is ran prior to lirc_serial being installed described in [http://help.ubuntu.com/community/Install_Lirc_Edgy](http://help.ubuntu.com/community/Install_Lirc_Edgy)

---

### Post by superm1 on 2006-12-30
> **dsegarra said:**
> Let me get this straight. I have to re-configure my hauppauge remote to control the set up box?. This way it will change the channels in the set up box and not in mythtv?. Kind of confused here.


Thanks
If you've just got your hauppaugge remote, and no serial transmitter, IR transmitter, or firewire cable - you won't be able to change channels on your cable box.

Check your cable box, and see what ports are on the back.  If you've got a IEEE1394 (or Firewire) port, this is the best way to go.  You can even capture video from certain stations (depending on what the cable co. locks down).  If you've got a High Speed Data (or serial) port, then this is second choice.  If you haven't got either, you can request a box from your cable company with either of those ports.  Last choice is an IR transmitter like one that you can either build or order from a site like irblaster.info.  These aren't nearly as reliable, and unfortunately several people (including me) are hit by an IR transmitting bug documented at bugs.debian.org, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=373871](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=373871) .

---

### Post by Schuenemann on 2006-12-30
> **superm1 said:**
> When you plug this device in, see what it shows up in during
```
lsusb
```

It may or may not be supported by the lirc IRDA drivers.  (Most likely not)

What was your intention to use with your cellphone?  Does your cellphone even have an IR port (most don't)

Hi, thanks for answering.
This is the output for lsusb:
```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 07d0:4959 Dazzle
Bus 002 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```
What does this mean?
My motherboard only has 2 USB ports and 1 is used by the keyboard.

My intention is to transfer data (pictures, ringtones, etc). And yes, the cellphone does have IR.

Thanks

---

### Post by devnet on 2007-01-01
I've followed the Install Lirc Edgy at the wiki:  [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

When modprobing for my lirc_mceusb2 remote, I get the following error:
```

FATAL: Module lirc_mceusb2 not found.

```

I'm running Kubuntu Edgy Eft...no one at the Kubuntu forums has ever tried to get mceusb running...

So, I figured that I'd try this how-to.  So I wiped lirc from the system...the followed the how-to.  Instead of using pre2 I used pre5 since it was the latest.  When running modprobe lirc_mceusb I get the EXACT same error. 

In the wiki, it states to do the following:
```

dpkg -i /usr/src/lirc-modules-2.6.*.deb

```

But if we've already sudo rm /usr/src/lirc*.deb before to remove old info, how can we dpkg?

So, I'm at an impasse here...I can't modprobe lirc_mceusb

I'm using 2 Haup cards...a 150 and a 350.  I'm having no problems watching television or recording TV.  This is the last thing I need to do to have a perfect PVR :D

Can anyone point me in the right direction?
dpkg -i /usr/src/lirc-modules-2.6.*.deb

---

### Post by superm1 on 2007-01-01
> **devnet said:**
> I've followed the Install Lirc Edgy at the wiki:  [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

When modprobing for my lirc_mceusb2 remote, I get the following error:
```

FATAL: Module lirc_mceusb2 not found.

```I'm running Kubuntu Edgy Eft...no one at the Kubuntu forums has ever tried to get mceusb running...

So, I figured that I'd try this how-to.  So I wiped lirc from the system...the followed the how-to.  Instead of using pre2 I used pre5 since it was the latest.  When running modprobe lirc_mceusb I get the EXACT same error. 

In the wiki, it states to do the following:
```

dpkg -i /usr/src/lirc-modules-2.6.*.deb

```But if we've already sudo rm /usr/src/lirc*.deb before to remove old info, how can we dpkg?

So, I'm at an impasse here...I can't modprobe lirc_mceusb

I'm using 2 Haup cards...a 150 and a 350.  I'm having no problems watching television or recording TV.  This is the last thing I need to do to have a perfect PVR :D

Can anyone point me in the right direction?
dpkg -i /usr/src/lirc-modules-2.6.*.deb
Hi,
can you post the contents of /etc/lirc/lirc-modules-source.conf?  My best educated guess here would be that the wrong module is listed there or the build process is failing, so we'll start out with checking to make sure this file is looking correct.

---

### Post by superm1 on 2007-01-01
> **Schuenemann said:**
> Hi, thanks for answering.
This is the output for lsusb:
```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 07d0:4959 Dazzle
Bus 002 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```What does this mean?
My motherboard only has 2 USB ports and 1 is used by the keyboard.

My intention is to transfer data (pictures, ringtones, etc). And yes, the cellphone does have IR.

Thanks
Well to my knowledge, the lirc project can't be used for this purpose.  You may have more luck using the USB adapter in SIR mode, but I'm not sure if the SIR drivers will even work for this adapter.  To my knowledge, they only worked for on motherboard IR.  Sorry!

---

### Post by rubrboots on 2007-01-02
I am trying to setup lirc to control a homemade ir transmitter to change channels on my cablebox. I have followed the LIRC Edgy documentation guide, but when I reach the "start and test" step I run into problems

```
boots@mythbox:~$ sudo /etc/init.d/lirc start 
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.
boots@mythbox:~$ irw
connect: No such file or directory
boots@mythbox:~$ 
```

When following the guide I chose "serial" and "sir" as modules to be built. I was just guessing with those, so maybe my problem lies here. Any ideas?

---

### Post by superm1 on 2007-01-02
> **rubrboots said:**
> I am trying to setup lirc to control a homemade ir transmitter to change channels on my cablebox. I have followed the LIRC Edgy documentation guide, but when I reach the "start and test" step I run into problems

```
boots@mythbox:~$ sudo /etc/init.d/lirc start 
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.
boots@mythbox:~$ irw
connect: No such file or directory
boots@mythbox:~$ 
```When following the guide I chose "serial" and "sir" as modules to be built. I was just guessing with those, so maybe my problem lies here. Any ideas?
Check dmesg.  Odds are you need to use setserial to make sure that your serial port is freed up first.

If dmesg gives you errors about loading either your serial or sir drivers, you will need to use the setserial utility.  It's outlined at the bottom of the page:
[https://help.ubuntu.com/community/Install_Lirc_Edgy#head-6ceb2a6bf65eddb537dd6038798144b163ab4a0a](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-6ceb2a6bf65eddb537dd6038798144b163ab4a0a)

---

### Post by Schuenemann on 2007-01-02
> **superm1 said:**
> Well to my knowledge, the lirc project can't be used for this purpose.  You may have more luck using the USB adapter in SIR mode, but I'm not sure if the SIR drivers will even work for this adapter.  To my knowledge, they only worked for on motherboard IR.  Sorry!

You know any tutorial for that?
Thanks

---

### Post by rubrboots on 2007-01-02
Thanks superm1, that was exactly my problem. Now like I said earlier I built "serial" and "sir" modules during setup but starting lirc will return errors if I add "lirc_sir" the my /etc/lirc/hardware.conf. It will start properly if with "lirc-serial" only. Does this mean that I do not need the sir module?

---

### Post by superm1 on 2007-01-02
> **rubrboots said:**
> Thanks superm1, that was exactly my problem. Now like I said earlier I built "serial" and "sir" modules during setup but starting lirc will return errors if I add "lirc_sir" the my /etc/lirc/hardware.conf. It will start properly if with "lirc-serial" only. Does this mean that I do not need the sir module?
Well this depends on what your intentions are.  If you really want to use two separate lirc devices like that (sir and serial), then you will have to follow the section that explains how to set up multiple devices, and you will have to use setserial to open up the serial port for the sir device and the serial port for the serial device.

So if you have an external transmitter that you were going to plug into the serial port, don't bother with the sir module.  If you were going to try to just use the sir port to transmit (which i don't think you would get very good range if this worked ), don't bother with the serial module.

Hope that makes sense :)

---

### Post by superm1 on 2007-01-02
> **Schuenemann said:**
> You know any tutorial for that?
Thanks
sigh..... can't say I do.  I looked for ways to use my laptop's sir port, and the only direction I was pointed was lirc sir stuff.  I know there are other things possible with it though.  Sorry!

---

### Post by shad0w_walker on 2007-01-05
Ok, stepping back a little from the current talk about modules. I followed the guide and managed to get my MCEusb remote working beautifully with the mscusb2 driver.

Iv now got one last issue which is holding me back, i can get the IR blaster to flash, but it appears that there is no acctual data being sent as nothing responds to commands. Any ideas?

---

### Post by superm1 on 2007-01-05
> **shad0w_walker said:**
> Ok, stepping back a little from the current talk about modules. I followed the guide and managed to get my MCEusb remote working beautifully with the mscusb2 driver.

Iv now got one last issue which is holding me back, i can get the IR blaster to flash, but it appears that there is no acctual data being sent as nothing responds to commands. Any ideas?
Your referring to the ir blaster for the mceusb2 right?  This thing is very very finicky.  You need to attach it directly to the device, since it can only get a range of a few cm.

Transmitting works like this (are you doing it this way)
```
irsend SEND_ONCE REMOTE BUTTON
```
where 
REMOTE is your remote name in lircd.conf
BUTTON is the button your sending in lircd.conf from REMOTE

---

### Post by Panhead Bill on 2007-01-05
Hexicon;

  I have a Hauppague remote (i2c).  Here are the problems i've had with this how-to:  (note this is not a complaint, this guide is very helpful)

Step 4:  ./setup   responds with no such file.  ./setup.sh works
 
Step 6 part 1: The following satement  seems to be in the wrong step. 
 
**"When "make install" finishes, it will tell you which module to load. In my case it's lirc_gpio. Change first line if yours is different."**
 
After step 4's save and configure, I reread the output and found this set of statements after the config.status statements:

[B]: config.status: executing default-1 commands

You will have to use the lirc_i2c kernel module.

Now enter 'make' and 'make install' to compile and install the package.[/B]


Step 6 part 2:  When I try testing the remote, it works, but I couldn't stop the remote sensing and return to the command mode until I opened a second terminal, and issued the "killall lircd" command.  Is there a way to do this in the first terminal?  [I](added info: Ctrl +c stops the testing and returns you to the command line)
[/I]
Step 8: 
[B]a) Open a terminal
b) With lirc unloaded (killall lircd), press a number key of your remote control.

If that number appears in the terminal, you must continue with step 9).

If there's anything in the terminal window, continue with step 10[/B]

What do I do when there is no change to the terminal window?  I pressed many keys on the remote, and there was no reaction in the terminal.
I rebooted, and the remote does not affect mythtv.  Any suggestions?

---

### Post by manro on 2007-01-06
I need some help here!

I have an avermedia TV98 card, when I run the irw this is the results

```

0000000040bf807f 00 TV/FM AVerMedia
0000000040bf807f 01 TV/FM AVerMedia
0000000040bf807f 02 TV/FM AVerMedia
0000000040bf807f 03 TV/FM AVerMedia
0000000040bf807f 04 TV/FM AVerMedia
0000000040bf807f 05 TV/FM AVerMedia
0000000040bf807f 06 TV/FM AVerMedia
0000000040bf807f 07 TV/FM AVerMedia
0000000040bf40bf 00 CD AVerMedia
0000000040bf40bf 01 CD AVerMedia
0000000040bf40bf 02 CD AVerMedia
0000000040bf40bf 03 CD AVerMedia
0000000040bf40bf 04 CD AVerMedia
0000000040bf40bf 05 CD AVerMedia
0000000040bf40bf 06 CD AVerMedia
0000000040bf40bf 07 CD AVerMedia
0000000040bfc03f 00 TELETEXT AVerMedia
0000000040bfc03f 01 TELETEXT AVerMedia
0000000040bfc03f 02 TELETEXT AVerMedia
0000000040bfc03f 03 TELETEXT AVerMedia

```

...and this is my dmesg result

> 
[17179616.728000] The bttv_* interface is obsolete and will go away,
[17179616.728000] please use the new, sysfs based interface instead.
[17179616.728000] lirc_gpio (-1): card type 0x29, id 0x31461
[17179616.728000] lirc_dev: lirc_register_plugin: sample_rate: 10
[17179616.732000] lirc_gpio (0): driver registered
[17179617.924000] vmnet1: no IPv6 routers present
[17179618.360000] vmnet8: no IPv6 routers present
[17179620.456000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=1
[17179620.648000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=0
[17179621.416000] bttv IR (card=41): unknown key: key=0x10 raw=0x10 down=1
[17179621.560000] bttv IR (card=41): unknown key: key=0x10 raw=0x10 down=0
[17179622.136000] bttv IR (card=41): unknown key: key=0x30 raw=0x30 down=1
[17179622.328000] bttv IR (card=41): unknown key: key=0x30 raw=0x30 down=0
[17179623.096000] bttv IR (card=41): unknown key: key=0x00 raw=0x00 down=1
[17179623.240000] bttv IR (card=41): unknown key: key=0x00 raw=0x00 down=0
[17179624.728000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=1
[17179624.920000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=0
[17179625.304000] bttv IR (card=41): unknown key: key=0x10 raw=0x10 down=1
[17179625.448000] bttv IR (card=41): unknown key: key=0x10 raw=0x10 down=0
[17179625.736000] bttv IR (card=41): unknown key: key=0x30 raw=0x30 down=1
[17179625.880000] bttv IR (card=41): unknown key: key=0x30 raw=0x30 down=0
[17179626.408000] bttv IR (card=41): unknown key: key=0x00 raw=0x00 down=1
[17179626.504000] bttv IR (card=41): unknown key: key=0x00 raw=0x00 down=0
[17179627.176000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=1
[17179627.320000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=0
[17179627.656000] bttv IR (card=41): unknown key: key=0x10 raw=0x10 down=1
[17179627.800000] bttv IR (card=41): unknown key: key=0x10 raw=0x10 down=0
[17179628.184000] bttv IR (card=41): unknown key: key=0x30 raw=0x30 down=1
[17179628.328000] bttv IR (card=41): unknown key: key=0x30 raw=0x30 down=0
[17179628.664000] bttv IR (card=41): unknown key: key=0x00 raw=0x00 down=1
[17179628.808000] bttv IR (card=41): unknown key: key=0x00 raw=0x00 down=0
[17179639.704000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=1
[17179639.944000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=0
[17179640.328000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=1
[17179640.712000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=0
[17179641.000000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=1
[17179641.384000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=0
[17179641.576000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=1
[17179641.768000] bttv IR (card=41): unknown key: key=0x20 raw=0x20 down=0


... my ~/.lirc look like this

> 
 # MAIN BEGIN - Application Selection Mode
# ———————————————————–

begin
prog = irexec
remote = TVPhone98
button = TV/FM
# Start TVtime
config = tvtime –window &
# Enter tvtime mode
mode = tvtime
end

# —————
# MAIN END

# APP MODES BEGIN
# —————

# tvtime mode
begin tvtime
begin
prog = irexec
button = POWER
config = tvtime-command QUIT
# Exit tvtime mode
flags = mode
end
begin
prog = irexec
button = TELETEXT
config = tvtime-command SHOW_MENU
end
begin
prog = irexec
button = AUTOSCAN
config = tvtime-command CHANNEL_SCAN
end
begin
prog = irexec
button = VIDEO
config = tvtime-command TOGGLE_INPUT
end
begin
prog = irexec
button = AUDIO
config = tvtime-command SET_AUDIO_MODE
end
begin
prog = irexec
button = DISPLAY
config = tvtime-command DISPLAY_INFO
repeat = 0
end
begin
prog = irexec
button = FULLSCREEN
config = tvtime-command TOGGLE_FULLSCREEN
end
begin
prog = irexec
button = MUTE
config = tvtime-command TOGGLE_MUTE
end
begin
prog = irexec
button = VOL_UP
config = tvtime-command RIGHT
repeat = 0
end
begin
prog = irexec
button = VOL_DOWN
config = tvtime-command LEFT
repeat = 0
end
begin
prog = irexec
button = CH_UP
config = tvtime-command UP
repeat = 0
end
begin
prog = irexec
button = CH_DOWN
config = tvtime-command DOWN
repeat = 0
end
begin
prog = irexec
button = 1
config = tvtime-command CHANNEL_1
end
begin
prog = irexec
button = 2
config = tvtime-command CHANNEL_2
end
begin
prog = irexec
button = 3
config = tvtime-command CHANNEL_3
end
begin
prog = irexec
button = 4
config = tvtime-command CHANNEL_4
end
begin
prog = irexec
button = 5
config = tvtime-command CHANNEL_5
end
begin
prog = irexec
button = 6
config = tvtime-command CHANNEL_6
end
begin
prog = irexec
button = 7
config = tvtime-command CHANNEL_7
end
begin
prog = irexec
button = 8
config = tvtime-command CHANNEL_8
end
begin
prog = irexec
button = 9
config = tvtime-command CHANNEL_9
end
begin
prog = irexec
button = 0
config = tvtime-command CHANNEL_0
end
end tvtime

#inicio mplayer

begin
button = VOL_UP
prog = mplayer
config = volume 1
repeat = 1
end

begin
button = VOL_DOWN
prog = mplayer
config = volume -1
repeat = 1
end

begin
button = PLAY
prog = mplayer
config = pause
end

begin
button = STOP
prog = mplayer
config = seek 0 1\npause
end


I think everything is configured and installed as it have to, but I can't control anything nor TVTIME or anythign, can someone please help me? ... almost forgot, when I push the autoscan button it locks my screen!!! thats the only thing that woks :( 

Sorry for my english.

Regards, ;)

---

### Post by superm1 on 2007-01-06
> **manro said:**
> I need some help here!

I have an avermedia TV98 card, when I run the irw this is the results

```

0000000040bf807f 00 TV/FM AVerMedia
0000000040bf807f 01 TV/FM AVerMedia
0000000040bf807f 02 TV/FM AVerMedia
0000000040bf807f 03 TV/FM AVerMedia
0000000040bf807f 04 TV/FM AVerMedia
0000000040bf807f 05 TV/FM AVerMedia
0000000040bf807f 06 TV/FM AVerMedia
0000000040bf807f 07 TV/FM AVerMedia
0000000040bf40bf 00 CD AVerMedia
0000000040bf40bf 01 CD AVerMedia
0000000040bf40bf 02 CD AVerMedia
0000000040bf40bf 03 CD AVerMedia
0000000040bf40bf 04 CD AVerMedia
0000000040bf40bf 05 CD AVerMedia
0000000040bf40bf 06 CD AVerMedia
0000000040bf40bf 07 CD AVerMedia
0000000040bfc03f 00 TELETEXT AVerMedia
0000000040bfc03f 01 TELETEXT AVerMedia
0000000040bfc03f 02 TELETEXT AVerMedia
0000000040bfc03f 03 TELETEXT AVerMedia

```...and this is my dmesg result



... my ~/.lirc look like this



I think everything is configured and installed as it have to, but I can't control anything nor TVTIME or anythign, can someone please help me? ... almost forgot, when I push the autoscan button it locks my screen!!! thats the only thing that woks :( 

Sorry for my english.

Regards, ;)
Your .lirc file needs to be a ~/.lircrc
```
mv ~/.lirc ~/.lircrc
```

Also, make sure you are starting irexec
```
irexec -d
```

---

### Post by dresbo on 2007-01-07
Having just spent the last 3 days straight trying to get mine working I thought I'd share some of what I discovered in the hope it might help others with similar problems

I have a Hauppauge Nova-t PCI with new silver remote A415-HPG-WE (under battery in remote) running edgy/2.6.17. From what I've read this should just work in the Kernel as a keyboard (and appears as a device in /dev/input/eventX). Sure enough numbers etc worked straight out of the box, but the Guide,Tv, Videos etc keys didn't.  

You can map the ones that work by running 'xev' and checking the keycode you get from them when you press the buttons.  You can then create a .Xmodmap file in your home folder which will force x to map those codes to keys you press.  For example:  

I dumped my current map out with

cd ~
xmodmap -pke > .Xmodmap

now edit the map with your favourite editor adding the codes that xev gives.  I wanted my Menu button to give the menu in Mythtv so I mapped it to 'm' with 

...
keycode 158 = m
keycode 159 =
keycode 160 =
...

When you reboot for the first time it will prompt you to load the map.  Allow it to and it won't prompt again.  You should find that when you press the Menu button it prints an m to the console.  


This is great for the keys that xev recognises but what about the others. The mythtv/nova-t wiki ([http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI)) indicates that you might have to add some symbols to a couple of your kernel sources to get these extended keys to work.  My kernel already had these and it still didn't work. For those having the same problem:

These 'extended' keys seem to give codes greater than 256, 'Guide' for example gives 365. If you run xev  from the command line and press the keys you get no reponse from those keys but you do from the ones that work. As far as I can tell this is because X can't cope with codes over 256.  If you find out which Event device the remote is with 

cat /proc/bus/input/devices

and see which Event number it shows up against.  Mine is 

N: Name="cx88 IR (Hauppauge Nova-T DVB-T"
P: Phys=pci-0000:00:06.0/ir0
S: Sysfs=/class/input/input4

Which is Event4.  You can then run evtest (get it with 'sudo apt-get install dvb-utils')

sudo evtest /dev/input/Event4

To see what its giving when you press the buttons.  On mine I get

Event: time 1168173133.655584, type 1 (Key), code 365 (EPG), value 0
Event: time 1168173133.655589, type 0 (Reset), code 0 (Reset), value 0

When I press Guide which is Electronic program guide.  I think this means that the kernel can handle it but x can't.  I thought you might be able to map the scancodes over 256 to keycodes below it using 'setkeycodes'.  See the man page.  You can print out keycodes using showkey (must do this outside of X - press ctrl-alt-F! for a real console ctrl-alt-F7 to get back in).

However I couldn't get it to do anything other than complain when I tried passing the showkey codes into setkeycodes.  I get invalid argument. I gave up with this route.  But since I now understood why it wasn't working I gave lirc a bash (not for the first time)

So to LIRC instead (I said this took a while!). firstly install the ubuntu package

sudo apt-get install lirc

to give you the relevant config settings

Then I installed lirc from source using this guide [http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft).

but this didn't work.  The way to get it work is clear once you realise that the problem is that it doesn't need a driver module at all.  So install the source with (you need the build-essentials packages to build the following stuff - google it)

wget [http://lirc.sourceforge.net/software/snapshots/lirc-0.8.1pre5.tar.bz2](http://lirc.sourceforge.net/software/snapshots/lirc-0.8.1pre5.tar.bz2)
 tar -xjvf lirc-0.8.1pre5.tar.bz2 -C /usr/src
 cd /usr/src/lirc-0.8.1pre5

change the tar for the newest version when you do it.  Now run

sudo ./configure --with-driver=devinput

This will set it up to use the EventX and requires no kernel driver (which it tells you at the end of the output)

Now

sudo make 
sudo make install

to make and install it.

You'll need a lircd.conf file which tells lirc how to translate the events from /dev/input/eventX into Lirc commands, which are then picked up by .lircrc in your home folder (simple huh)

lircd.conf goes in /etc/.  I've attached mine but you can record your own with

sudo irrecord -H dev/input -d /dev/input/event4 lircd.conf

and following the instructions.  You should end up with a lircd.conf file in the current directory with loads of codes in it which you copy to /etc/lircd.conf

now you can test your conf file by running 

sudo lircd -H dev/input -d /dev/input/event4

or whichever event number you got - which tells it to listen to event4 using the devinput driver. It should then translate signals on event4 to the codes in lircd.conf 

Now open another terminal window and run 

irw

Which connects to lirc and listens for keypress signals from the lirc service (which in turn creates a socket at something like /dev/lirc which is actually what irw listens to). If its all working you should get

$ irw
0000000080010069 00 Left Hauppauge_Nova-T-new
000000008001006c 00 Down Hauppauge_Nova-T-new
0000000080010067 00 Up Hauppauge_Nova-T-new
000000008001006a 00 Right Hauppauge_Nova-T-new

as you press buttons.  You're nearly there. Now to set up the service

Very Important: I seemed to get /usr/sbin/lircd from the initial apt-get install of lirc and /usr/local/sbin/lircd from the source install, which means that when you run the service with 'sudo /etc/init.d/lirc start' it doesn't use the one that you just compiled because its hardcoded into the init script as usr/sbin/lircd.  When you run 'lircd' from the command line you get the one you just compiled starting! which is why I think some people are having problems with the service but not with the command line.
Use

sudo cp /usr/local/sbin/lircd /usr/sbin/lircd

to fix it.

You will find that when you reboot your computer the ir remote can move from event4 to event1 or any other event.  This is pain.  You can make it static so that it also appears as /dev/input/irremote using this guide [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php) 

Once you've done that you need to tell lircd to start up with the correct options every time.  You set this in /etc/lirc/hardware.conf. Relevant lines

LIRCD_ARGS="-H dev/input -d /dev/input/irremote"

DRIVER="dev/input"

DEVICE="/dev/input/event4"

LIRCD_CONF="/etc/lircd.conf"

I wasn't sure whether you needed to put DRIVER and DEVICE as well as the command line args but it seems to work for me

Set the service to startup at boot in all runlevels with

update-rc.d lirc defaults

reboot and it should all be started and listening.  I've included my ~/.mythtv/lircrc file for the mythtv commands as well

Good luck

---

### Post by manro on 2007-01-07
> **superm1 said:**
> Your .lirc file needs to be a ~/.lircrc
```
mv ~/.lirc ~/.lircrc
```

Also, make sure you are starting irexec
```
irexec -d
```

Sorry...actually it is ~/.lircrc ;) but it was the irexec -d thing :D 

Thanks a lot superm1!

Best Regards,
:-D

---

### Post by manro on 2007-01-07
Here I am again asking for help ;) 

How can I block or disable the "AUTOSCAN" button to lock my session, that's not specified on my .lircrc file!

Thanks for all the help!

Regards,

---

### Post by superm1 on 2007-01-07
> **manro said:**
> Here I am again asking for help ;) 

How can I block or disable the "AUTOSCAN" button to lock my session, that's not specified on my .lircrc file!

Thanks for all the help!

Regards,
More than likely, the kernel is interpreting the AUTOSCAN event as a real button event.  Go to your gnome shortcut key preferences.  Set your session lock key to something different.

You can also use xsetkeycodes to change the key that is being interpreted by AUTOSCAN similar to a few posts above.

---

### Post by nashira on 2007-01-07
> **superm1 said:**
> I've actually put together a howto already on the wiki that doesn't install anything from source.  It includes a section to cover issues with I2C and GPIO ( I assembed a debian package already for lirc that has 2.6.17 support for these two modules ).  It's a lot more manageable since it uses debian init scripts and module-assistant for module building rather then spewing binaries across the system that aren't easily uninstallable unless you wrote down every single one installed.

[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

Thanks!  this worked well for me using a Haupagge WinTV go-plus after several failed attempts at different methods.  Highly recommended.

---

### Post by manro on 2007-01-08
> **superm1 said:**
> More than likely, the kernel is interpreting the AUTOSCAN event as a real button event.  Go to your gnome shortcut key preferences.  Set your session lock key to something different.

You can also use xsetkeycodes to change the key that is being interpreted by AUTOSCAN similar to a few posts above.

Thanks again ;) 

Regards, :D

---

### Post by Panhead Bill on 2007-01-15
Still no go with the remote.  Hauppague 150 remote.  Step 8 still confusing, as I do not get any change to the terminal when pressing keys - after killall.  I restarted and no action from remote.

Tests so far:
mythtv@ubuntuPVR:~$ ls -l /dev/lirc*
crw-r--r-- 1 root root 61, 0 2007-01-08 10:23 /dev/lirc
crw-rw---- 1 root root 61, 0 2007-01-08 10:23 /dev/lirc0
crw-rw---- 1 root root 61, 1 2007-01-08 10:23 /dev/lirc1
srw-rw-rw- 1 root root     0 2007-01-13 20:26 /dev/lircd

mythtv@ubuntuPVR:~$ sudo lircd -n
lircd: lircd(hauppauge) ready
lircd: accepted new client on /dev/lircd

----------------------------------------------

mythtv@ubuntuPVR:~$ irw

0000000000001781 00 1 Hauppauge_350
0000000000001795 00 Down Hauppauge_350
0000000000001794 00 Up Hauppauge_350
00000000000017a0 00 Ch+ Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
00000000000017b4 00 Forward Hauppauge_350
00000000000017b7 00 Record Hauppauge_350
00000000000017a1 00 Ch- Hauppauge_350
0000000000001781 00 1 Hauppauge_350

etc.

Any hints what to check next?

---

### Post by ptipton on 2007-01-16
I am installing mythth backend on a headless server which has gone smoothly with the exception of getting the pvr 150 irblaster working to change channels on my satellite box.

I have been following the instructions for Edgy Mythtv install in the community documentation including the HOWto: LIRC in Edgy and External Changer documents. At one point the remote was working albeit as a " Hauppauge_350" , however, after trying various different lircd.conf files, now when i run IRW I get " Connection refused".

As a backend server I dont actually need the remote to work just the IR Blaster but have had no luck whatsoever in this respect.

I have found this page on the subject [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) which requires the download of a patched lirc and ir blaster firmware but I am unsure if this is the correct thing to do in edgy.

Any advice on how to set this up would be much appreciated, i'm a realtive newbie and the mythtv install has gone very well excluding this, however without the ir blaster to change channel on the satelite box mythtv is basically useless.

I originally posted in the Multimedia and Video section but thought this thread might be more appropriate

---

### Post by ptipton on 2007-01-18
Was told by superm1 that currently the only option is to avoid the packages and compile from source. I used the instructions fron the link in my original post and now remote and ir blaster working perfectly. Thanks for the help superm1.

---

### Post by dsegarra on 2007-01-19
> **superm1 said:**
> If you've just got your hauppaugge remote, and no serial transmitter, IR transmitter, or firewire cable - you won't be able to change channels on your cable box.

The card came with an IR transmitter. Is this as reliable as getting an external one?. 


Thanks

---

### Post by tfmccull on 2007-01-19
After weeks of trying to get LIRC to work with my mce transceiver, i have finally got it. Not quite sure how, but at this point who cares?

2 questions: since i complied from source, i cant start lirc using /etc/init.d/lirc start. How do i start lirc on boot? I tried editing my rc.local file with the instructions on page 1 of this post, but i still need to start it manually every time i reboot.

Second question: sincei installed it this way, i dont have a /etc/lirc directory. My lircd.conf file is in /etc/ and i have no hardware.conf file. where would hardware.conf be hiding?

If i can get lirc to start on boot i will be a VERY happy person.

Thanks.

---

### Post by mr_git on 2007-01-20
Hi, I've followed this excellent how-to, and am very close to having my avermedia tv98 remote working on Edgy.

Lirc seems to work great when I do

```

./setup.sh
make
make install
modprobe lirc_gpio
lircd
irw
```

... I get results like these (by pressing buttons on the remote, obviously!):

```

0000000000000011 00 5 TVCapture98
0000000000000011 01 5 TVCapture98
0000000000000011 02 5 TVCapture98
0000000000000011 03 5 TVCapture98
0000000000000011 04 5 TVCapture98
0000000000000011 05 5 TVCapture98
0000000000000011 06 5 TVCapture98
0000000000000011 07 5 TVCapture98
0000000000000011 08 5 TVCapture98
0000000000000011 09 5 TVCapture98
0000000000000011 0a 5 TVCapture98
0000000000000011 0b 5 TVCapture98
0000000000000018 00 1 TVCapture98
0000000000000018 01 1 TVCapture98
0000000000000023 00 TV/FM TVCapture98
0000000000000023 01 TV/FM TVCapture98
0000000000000022 00 CD TVCapture98
0000000000000022 01 CD TVCapture98
0000000000000022 02 CD TVCapture98
0000000000000022 03 CD TVCapture98
0000000000000022 04 CD TVCapture98
0000000000000022 05 CD TVCapture98
0000000000000022 06 CD TVCapture98
0000000000000022 07 CD TVCapture98
0000000000000022 08 CD TVCapture98
0000000000000022 09 CD TVCapture98
```

However, this seems to be the only way I can get it working; despite having followed the instructions in the how-to under **7) Autoload lirc at boot-time** and **Disable ir_common**, the lircd which starts up at boot doesn't seem to see my remote. *irw* gives no output at all, unless I *killall lircd* and then start from the beginning running *setup.sh* in the lirc source directory.

Can anyone offer any help? I feel like I must be very close to having this working on boot.

cheers,
mr_git

---

### Post by superm1 on 2007-01-22
> **dsegarra said:**
> The card came with an IR transmitter. Is this as reliable as getting an external one?. 


Thanks
A lot of people have been getting cards like this lately.  I've heard good success with this, but I don't have support for this in the package as of right now.  There is a blog post floating around explaining how to get this going from source.

---

### Post by hexion on 2007-01-28
Hi everybody.

I've been out much time. Sorry to everyone who asked for help in this time, and so sorry for keeping this thread outdated.

Please, read again the first post. I think we better move to a wiki so all of us can complete, fix, and mantain info around this thread (and around things that this thread didn't ever cover)

Thanks to everybody who contributed in this thread, helping people with their problems (specially to **Superm1** ;) ).

And remember, now this "howto" belongs to everybody, so feel free to mantain it in the wiki that **Bodhi.zazen **created for us (thank you ;) )

Regards!

---

### Post by mariuss on 2007-01-28
> **hexion said:**
> And remember, now this "howto" belongs to everybody, so feel free to mantain it in the wiki that **Bodhi.zazen **created for us (thank you ;) )

Link?

---

### Post by hexion on 2007-01-28
> **mariuss said:**
> Link?

This is the link: [http://doc.gwos.org/index.php/Lirc](http://doc.gwos.org/index.php/Lirc)
It's posted in the first post of this thread, anyway..

---

### Post by hexion on 2007-01-29
I received a PM with this error. For those who have the same problem, here it's the solution:

> **Kr152ta said:**
>  Kr152ta

root@kriszta-Ubuntu:/usr/src/lirc-0.8.1# make
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=config.h \
             /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/usr/src/lirc-0.8.1'
Making all in drivers
make[2]: Entering directory `/usr/src/lirc-0.8.1/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/lirc-0.8.1/drivers/lirc_dev'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/lirc-0.8.1/drivers/lirc_dev'
Making all in lirc_gpio
make[3]: Entering directory `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.17-10-generic/build/ SUBDIRS=/usr/src/lirc-0.8.1/drivers/lirc_gpio modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
mkdir -p /usr/src/lirc-0.8.1/drivers/lirc_gpio/.tmp_versions
rm -f /usr/src/lirc-0.8.1/drivers/lirc_gpio/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.1/drivers/lirc_gpio
gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1/drivers/lirc_gpio/.lirc_gpio.o.d -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc-0.8.1/drivers/lirc_gpio/../.. -I/lib/modules/2.6.17-10-generic/build//include/ -I/lib/modules/2.6.17-10-generic/build//drivers/media/video/ -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_gpio)" -D"KBUILD_MODNAME=KBUILD_STR(lirc_gpio)" -c -o /usr/src/lirc-0.8.1/drivers/lirc_gpio/.tmp_lirc_gpio.o /usr/src/lirc-0.8.1/drivers/lirc_gpio/lirc_gpio.c
In file included from /usr/src/lirc-0.8.1/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:51:23: error: btcx-risc.h: Nincs ilyen fájl vagy könyvtár
In file included from /usr/src/lirc-0.8.1/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:128: error: field &#8216;top&#8217; has incomplete type
/usr/src/lirc-0.8.1/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:129: error: field &#8216;bottom&#8217; has incomplete type
/usr/src/lirc-0.8.1/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:365: error: field &#8216;main&#8217; has incomplete type
/usr/src/lirc-0.8.1/drivers/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
/usr/src/lirc-0.8.1/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:232:1: warning: this is the location of the previous definition
make[5]: *** [/usr/src/lirc-0.8.1/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1/drivers/lirc_gpio] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.1/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1'
make: *** [all] Error 2
root@kriszta-Ubuntu:/usr/src/lirc-0.8.1#

All you have to do is this:

> cp /usr/src/linux-source-2.6.17/drivers/media/video/btcx-risc.* /usr/src/linux/drivers/media/video/bt8xx/By the way, I recommend that /usr/src/linux points to /usr/src/linux-source-2.6.17 and not to linux-headers-2.6.17-10-generic as in this case.

To do that:
> cd /usr/src
unlink linux
ln -s /usr/src/linux-source-2.6.17 linux 

;)

---

### Post by Patrick Dixon on 2007-01-29
HEEELLLLP!

I had installed lirc but couldn't figure out why it didn't listen to my key mapping until I found this thread, so I tried to use the hacked ir_common module.

Unfortunately the module seems to be called ir-common.ko so I 'installed' that first before realising that it should be ir_common.ko.  Now my ir remote is not recognised at all!  Removing the ir_common.ko file and re-booting doesn't get me back to where I was either.

So how do I remove the ir_common.ko/ir-common.ko module that didn't work and try to use X-whatever-it-is to map my Hauppauge Nova-T remote for MythTV?

I do SO love linux.

---

### Post by hexion on 2007-01-29
> **Patrick Dixon said:**
> HEEELLLLP!

I had installed lirc but couldn't figure out why it didn't listen to my key mapping until I found this thread, so I tried to use the hacked ir_common module.

Unfortunately the module seems to be called ir-common.ko so I 'installed' that first before realising that it should be ir_common.ko.  Now my ir remote is not recognised at all!  Removing the ir_common.ko file and re-booting doesn't get me back to where I was either.

So how do I remove the ir_common.ko/ir-common.ko module that didn't work and try to use X-whatever-it-is to map my Hauppauge Nova-T remote for MythTV?

I do SO love linux.

I didn't understand what's exactly your problem... but if you want to recover your ir-common.ko file, you just have to download the sources of your kernel version, and run "make modules".

Your module will be created in its location, and you'll have to copy to /lib/modules... (see the paths in the howto).

---

### Post by Patrick Dixon on 2007-01-29
So basically I'm f**ked!

The problem is that your tar.gz file creates ir-common.ko NOT ir_common.ko

I didn't notice this and rebooted - no IR

I corrected it and rebooted - now no IR device!

So I can't go forward and I can't go back.

Is there anywhere I can just get a vanilla ir_common.ko from, rather than re-install the whole f'ing kernel.  I've spent 4 days to get to where I am now ....

---

### Post by Patrick Dixon on 2007-01-29
Even putting your ir_common.ko file back doesn't give me my IR remote back - it was present (event3) and working before I installed your hacked module.

$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0006 Version=003e
N: Name="ImExPS/2 Logitech Explorer Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

---

### Post by Squee22 on 2007-01-31
I need some help!!!!


ok so I followed this guide word for word:
[http://www.develia.org/documents.php?l=2&f=1&p=lirclivedrive](http://www.develia.org/documents.php?l=2&f=1&p=lirclivedrive)


and it works great. but theres one problem. every time I restart I have to re start the program with 
[INDENT]/usr/sbin/lircd -H livedrive_midi -d /dev/snd/midiC0D1[/INDENT]


so I put that line in my startup programs tab in sessions.

doesn't work

so I opened up my permissions on lircd, midicod1, lircmd, lircrc, lircd.conf, and every other lirc file I could find

still doesn't work after reboot, but now when I type in my command it doesn't ask for password

now I have it set up to a icon on my taskbar, I click every time I start the comp'.  now this works, as a band-aid solution, but it would be really nice if it would work as a startup/boot program

---

### Post by ErikTheRed on 2007-02-01
I'm not sure if any of you can help me or not, but we had a power outage today and my mythtv box went offline. Now I can't get lirc to startup even though it had been working previously. Any ideas?

/dev/lirc, /dev/lirc0. and /dev/lircd are all still there (did they get stuck maybe?).

---

### Post by Patrick Dixon on 2007-02-01
run
cat /proc/bus/input/devices
and check that the event number is still the same.

If that's the problem, have a look at 'Make the LIRC Device Static' here [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php)

---

### Post by Patrick Dixon on 2007-02-01
As a follow up to my previous posts, I have found that ir-common is not a problem for lirc with WinTV - at least with a Hauppauge Nova-T card/remote.  lirc seems to take precedence over the ir-common kernel settings, so that when WinTV is running and if you have lircrc in ~/.mythtv you should get the commands you have defined in lircrc.  When/if WinTV isn't running, the ir-common, pre-defined, commands are active.

I followed this guide [http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php) but you should note that you have to edit the /etc/lirc/hardware.conf to reflect the correct device/event number for you machine.  I recommend you try this before embarking on the other complicated solutions recommended here, as you can do the whole thing without doing much more than a sudo apt-get install.  Just ensure that you use the right event# for your machine, as it will change depending on whether you have a keyboard & mouse connected!

---

### Post by hexion on 2007-02-01
> **Squee22 said:**
> I need some help!!!!


ok so I followed this guide word for word:
[http://www.develia.org/documents.php?l=2&f=1&p=lirclivedrive](http://www.develia.org/documents.php?l=2&f=1&p=lirclivedrive)


and it works great. but theres one problem. every time I restart I have to re start the program with [INDENT]/usr/sbin/lircd -H livedrive_midi -d /dev/snd/midiC0D1[/INDENT]
so I put that line in my startup programs tab in sessions.

doesn't work

so I opened up my permissions on lircd, midicod1, lircmd, lircrc, lircd.conf, and every other lirc file I could find

still doesn't work after reboot, but now when I type in my command it doesn't ask for password

now I have it set up to a icon on my taskbar, I click every time I start the comp'.  now this works, as a band-aid solution, but it would be really nice if it would work as a startup/boot program

Have you tried adding that line in /etc/rc.local ?
Note, what are launched there is set with root privileges and for all users.

---

### Post by Squee22 on 2007-02-01
> **hexion said:**
> Have you tried adding that line in /etc/rc.local ?
Note, what are launched there is set with root privileges and for all users.


worked like a charm. thank you sir

---

### Post by bobo1on1 on 2007-02-13
I have a problem, I followed the guide exactly, but the /etc/init.d/lirc script is not installed!

What is going on here?

---

### Post by Patrick Dixon on 2007-02-13
> **bobo1on1 said:**
> I have a problem, I followed the guide exactly, but the /etc/init.d/lirc script is not installed!

What is going on here?

Check your /etc/apt/source.list includes the 'universe' lines (not commented out).

sudo apt-get install lirc

should then install lirc and give you the /etc/init.d/lirc script - like this.

root@mediaserver:/home/dixon# apt-get install lirc
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dialog
Suggested packages:
  lirc-modules-source lirc-x
The following NEW packages will be installed:
  dialog lirc
0 upgraded, 2 newly installed, 0 to remove and 127 not upgraded.
Need to get 524kB of archives.
After unpacking 2798kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe dialog 1.0-20060221-1 [208kB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe lirc 0.8.0-5ubuntu1 [316kB]
Fetched 524kB in 14s (35.2kB/s)
Preconfiguring packages ...
Selecting previously deselected package dialog.
(Reading database ... 97498 files and directories currently installed.)
Unpacking dialog (from .../dialog_1.0-20060221-1_i386.deb) ...
Setting up dialog (1.0-20060221-1) ...
Selecting previously deselected package lirc.
(Reading database ... 97621 files and directories currently installed.)
Unpacking lirc (from .../lirc_0.8.0-5ubuntu1_i386.deb) ...
Setting up lirc (0.8.0-5ubuntu1) ...
Setting up modutils file
##################################################
## LIRC IS NOT CONFIGURED                       ##
##                                              ##
## read /usr/share/doc/lirc/html/configure.html ##
##################################################
Starting lirc daemon:.

root@mediaserver:/home/dixon# ls -ls /etc/init.d/lirc*
4 -rwxr-xr-x 1 root root 3382 2006-07-10 18:50 /etc/init.d/lirc

---

### Post by newcoventry on 2007-02-23
A few months ago I had Lirc up and working like a charm.  I am using the mceusb2 configs and whatnot. I made the mistake of running all the updates on my system and now lirc won't function at all.  Here is what I am getting as output: 
First I run sudo lircd -n
everything is happy.
Then I try running: irw on a second instance of terminal and nothing happens.
When I go back to the first terminal I see:
```
lircd: lircd(mceusb2) ready
lircd: accepted new client on /dev/lircd
lircd: could not open /dev/lirc
lircd: default_init(): No such device
lircd: caught signal
Terminated
```


After running the updates on my system I went through these steps to rebuild my modules:
```
sudo rm /usr/src/lirc*deb
sudo m-a clean lirc
sudo m-a update,prepare
sudo m-a a-i lirc
sudo depmod -a
```

Any ideas what went awry?

---

### Post by pulpinator on 2007-03-24
I have a PVR-150 with the Hauppauge remote. First, I followed the instructions here:
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

Then I found this thread and followed the instructions on the first post. Both give me the same result, not working remote. When I type irw, I get a new prompt.

dmesg | grep lirc gives me:

```

[17179605.876000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179605.876000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.

```

Any ideas?

---

### Post by manro on 2007-04-14
Hello,

I don't know if it's ok to post my question here, but it seems the right place to me!

I already have lirc up and running on Edgy following hexion's howto (thanks a lot hexion), but I have no success installing it on Feisty, basically I can't replace the ir_common module in Feisty's kernel (I own an avermedia tv card), can any of you guys give me some help with this?

Thanks,
Manro

---

### Post by manro on 2007-04-14
Just a little update... it seems to work when I run all the process of installation, but once I reboot the machine the lirc stops working, I try to rebuild the ir-common for the 2.6.20-15-generic kernel but it seems like I don't know what I'm doing! - if someone can help me facilitating me the ir-common for the 2.6.20-15-generic I'll really appreciate!

Thnaks, :D

---

### Post by djjazz on 2007-04-16
I tried installing lirc under Feisty Fawn (updated and running 2.6.20-15-generic kernel)  and when I run ./configure I get the error message:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check



run apt-get says I have installed gcc





The full output from ./configure:

setup.sh written by Karsten Scheibler, 1999-JUN-28

If you have problems or questions please consult the mailing list
<http://lists.sourceforge.net/mailman/listinfo/lirc-list>

Configuration: .setup.config, executable shell script: configure.sh
Starting the generated shell script which will call configure with the right
parameters...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for mknod... /bin/mknod
checking for mkfifo... /usr/bin/mkfifo
checking for depmod... /sbin/depmod
checking for libusb-config... no
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
Please read the documentation!!!




and tail from config.log:
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define STDC_HEADERS 1
#define VERSION "0.8.1"
#endif
#ifdef __cplusplus
void exit (int);

configure: exit 1


Any ideas?

Thanks!

---

### Post by christooss on 2007-04-19
Damn. I cant make my reciever work. Again I foloved instructions in wiki but when I come to irw no output is there.

I have serial connection. I have put 

> alias char-major-61 lirc_serial 
options lirc_serial irq=4 io=0x3f8
install lirc_serial /bin/setserial /dev/ttyS0 uart none ;\
    /sbin/modprobe --ignore-install lirc_serial

in /etc/modporbe.d/lirc and rebooted but no output from irw.

this is my dmesg | grep lirc

[>    72.874848] lirc_dev: IR Remote Control driver registered, at major 61 
[   73.133869] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[   74.142415] lirc_serial: auto-detected active high receiver
[   74.142431] lirc_dev: lirc_register_plugin: sample_rate: 0

Any ideas? I have loaded lircd.con for my remote on the right place and even tried another remote with irrecord. But no output there ither

---

### Post by TheKid965 on 2007-04-19
> **djjazz said:**
> I tried installing lirc under Feisty Fawn (updated and running 2.6.20-15-generic kernel)  and when I run ./configure I get the error message:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check



run apt-get says I have installed gcc


You need to install the "g++" package for C++ compatibility.  Vanilla gcc doesn't have it "out of the box."

---

### Post by superm1 on 2007-04-20
> **christooss said:**
> Damn. I cant make my reciever work. Again I foloved instructions in wiki but when I come to irw no output is there.

I have serial connection. I have put 



in /etc/modporbe.d/lirc and rebooted but no output from irw.

this is my dmesg | grep lirc

[

Any ideas? I have loaded lircd.con for my remote on the right place and even tried another remote with irrecord. But no output there ither
How did you build your serial device?  Home built?

---

### Post by hexion on 2007-04-21
> **manro said:**
> Just a little update... it seems to work when I run all the process of installation, but once I reboot the machine the lirc stops working, I try to rebuild the ir-common for the 2.6.20-15-generic kernel but it seems like I don't know what I'm doing! - if someone can help me facilitating me the ir-common for the 2.6.20-15-generic I'll really appreciate!

Thnaks, :D

Hi manro.
It seems that your sources/headers doesn't match your current kernel. In example, if you try to use a module built with a low-latency .config file using a generic kernel, it will fail to load ir-common, and as a consecuence bttv module won't load, and lirc_gpio won't load too.

How can you know your problem is that? With a "lsmod | grep bttv" If it doesn't show anything, your ir-common module is broken.

What would I do to try?
- Delete your /usr/src/linux-source-2.6.20  directory
- Ensure you have linux-sources installed.
- If it downloads a new file, try again the howto. NOTE: copy the correct .config file matching your kernel (lowlatency or generic and the correct version).

I send here an attachment with my ir-keymaps.c file. But it's made just for me...  I edited it to leave all buttons without any action but the volume control and the mute button (I like the eye-candy of gnome 2.18 and I don't know how to launch that effect from console :))

Hope it helps ;)

---

### Post by christooss on 2007-04-23
superm1 I got it with tv tuner. But i think its some generic one

---

### Post by manro on 2007-04-28
> **hexion said:**
> Hi manro.
It seems that your sources/headers doesn't match your current kernel. In example, if you try to use a module built with a low-latency .config file using a generic kernel, it will fail to load ir-common, and as a consecuence bttv module won't load, and lirc_gpio won't load too.

How can you know your problem is that? With a "lsmod | grep bttv" If it doesn't show anything, your ir-common module is broken.

What would I do to try?
- Delete your /usr/src/linux-source-2.6.20  directory
- Ensure you have linux-sources installed.
- If it downloads a new file, try again the howto. NOTE: copy the correct .config file matching your kernel (lowlatency or generic and the correct version).

I send here an attachment with my ir-keymaps.c file. But it's made just for me...  I edited it to leave all buttons without any action but the volume control and the mute button (I like the eye-candy of gnome 2.18 and I don't know how to launch that effect from console :))

Hope it helps ;)

Thanks Hexion ... it works!!! :) ... but now I found another issue :( ... after I reboot and running the "lsmod | grep bttv" command I recive this:

```
manro@ubuntu-desktop:~$ lsmod | grep bttv
bttv                  173684  2 lirc_gpio,bt878
video_buf              26116  1 bttv
ir_common              31108  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            8712  1 bttv
btcx_risc               5896  1 bttv
tveeprom               15888  1 bttv
i2c_core               22784  7 nvidia,i2c_ec,tuner,tvaudio,bttv,i2c_algo_bit,tveeprom
videodev               28160  1 bttv
v4l2_common            25216  3 tuner,bttv,videodev
manro@ubuntu-desktop:~$ 
```

It seems that everything it's ok ... then I run the irw command and receive responds:

```
manro@ubuntu-desktop:~$ irw
00000000c03fc03f 00 CH_UP TVPhone98_ext
00000000c03fc03f 01 CH_UP TVPhone98_ext
00000000c03fc03f 02 CH_UP TVPhone98_ext
00000000c03fc03f 03 CH_UP TVPhone98_ext
00000000c03fc03f 04 CH_UP TVPhone98_ext
00000000c03fc03f 05 CH_UP TVPhone98_ext
00000000c03fc03f 06 CH_UP TVPhone98_ext
00000000c03fc03f 07 CH_UP TVPhone98_ext
00000000c03fc03f 08 CH_UP TVPhone98_ext
00000000c03fc03f 09 CH_UP TVPhone98_ext
00000000c03fc03f 0a CH_UP TVPhone98_ext
00000000c03fc03f 0b CH_UP TVPhone98_ext
0000000040bf7887 00 VOL_DOWN TVPhone98
0000000040bf7887 01 VOL_DOWN TVPhone98
0000000040bf7887 02 VOL_DOWN TVPhone98
0000000040bf7887 03 VOL_DOWN TVPhone98
```

I already run the irexec -d and configure (copy) the .lircrc and lircd.conf but nothing happens. I also try the irrecord --device=/dev/lircd but when it ask to push buttons it just doesn't shows anything, not a single point!

I'm very close to make it work, please, if someone know what is wrong let me know!

Attached is my .lircrc and lircd.conf if you want to take a look (maybe is something wrong in there :))

Thanks againg fot all the help!

Regards,
MaNRo

---

### Post by medeshago on 2007-04-29
I've tried this with the remote from a flyvideo 2000 card in Feisty Fawn.

The proble is that i get this with "make":

make[5]: *** [/usr/src/lirc-0.8.1/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1/drivers/lirc_gpio] Error 2
make[4]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/usr/src/lirc-0.8.1/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/usr/src/lirc-0.8.1'
make: *** [all] Error 2

and i get this if i try to continue with "make install":

medeshago@nosotros:/usr/src/lirc-0.8.1$ sudo make install
Making install in drivers
make[1]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers'
Making install in lirc_dev
make[2]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
make[3]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
test -c /dev/lirc || (/bin/bash ../../mkinstalldirs /dev && /bin/mknod /dev/lirc c 61 0)
/bin/bash ../../mkinstalldirs /lib/modules/2.6.20-15-generic/misc
 /usr/bin/install -c -m 644 lirc_dev.ko /lib/modules/2.6.20-15-generic/misc/lirc_dev.ko
/sbin/depmod -a
make[3]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
make[2]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_dev'
Making install in lirc_gpio
make[2]: se ingresa al directorio `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
make[2]: *** No hay ninguna regla para construir el objetivo `install'.  Alto.
make[2]: se sale del directorio `/usr/src/lirc-0.8.1/drivers/lirc_gpio'
make[1]: *** [install-recursive] Error 1
make[1]: se sale del directorio `/usr/src/lirc-0.8.1/drivers'
make: *** [install-recursive] Error 1


That's it. I can't get it to work.

---

### Post by manro on 2007-04-29
Hey guys...I don't know why, but after like five restarts, I just run the irexec -d again and everything begins to work just like it should! :) 

Thanks for everything really!

Best Regards,
MaNRo

---

### Post by lonegeek on 2007-05-02
Does anyone know how to get the serial ir blaster from [http://www.irblaster.info/]("http://www.irblaster.info/") to work?

---

### Post by superm1 on 2007-05-03
> **lonegeek said:**
> Does anyone know how to get the serial ir blaster from [http://www.irblaster.info/](http://www.irblaster.info/) to work?
You will need to follow the Lirc_Edgy directions and build the lirc_serial modules.  Be sure to enable the transmitter.  There are also directions at the bottom of the page on how to disable the uart on the serial port.  Add your remote to /etc/lirc/lircd.conf.

Warning: I've got blasters and configurations I know to be functional that don't work anymore on a few of my computers a few releases ago.  They are broken in both debian etch and ubuntu feisty.  Hopefully you don't get hit by this same bug.  I've got a bug filed with debian about it.

---

### Post by hexion on 2007-05-03
> **manro said:**
> Hey guys...I don't know why, but after like five restarts, I just run the irexec -d again and everything begins to work just like it should! :) 

Thanks for everything really!

Best Regards,
MaNRo

It was my black sheep.. 
I sent him to do the trick in your system while you weren't watching :lolflag:

Glad you solved it. I remember the first time it worked for me... that day I decided to switch completelly to Linux :)

---

### Post by t_anjan on 2007-05-10
I compiled the "ir-common.ko" required to disable the in-built IR recognition of Feisty. This file is for the default kernel of Feisty, namely 2.6.20-15

---

### Post by manro on 2007-05-10
> **hexion said:**
> It was my black sheep.. 
I sent him to do the trick in your system while you weren't watching :lolflag:

Glad you solved it. I remember the first time it worked for me... that day I decided to switch completelly to Linux :)

Ha ha ha !!! :lolflag:

Ohh that sheep of yours!... Hexion, thanks a lot really, same case here...  since I get the lirc work on my old Edgy linux is the only OS on my machine...mmmm...well...except for the one on the VMWare ;)  

Thanks again, now I'm a extremely happy Feisty user \\:D/

---

### Post by hexion on 2007-05-10
> **t_anjan said:**
> I compiled the "ir-common.ko" required to disable the in-built IR recognition of Feisty. This file is for the default kernel of Feisty, namely 2.6.20-15

Remember, for those who post/use compiled modules, that a ir-common built with a .config from a generic kernel configuration WONT WORK in a system with a low-latency kernel (and viceversa)

So please, specify wheter it's compiled for generic or low-latency kernels ;)

BTW, thanks t_anjan. It can be usefull for somebody :)

---

### Post by t_anjan on 2007-05-13
I really don't know what low-latency and generic kernels are. I'll tell you what I did, maybe from that you can tell me what I have.

In my /usr/src/linux-headers-2.6.20-15-generic/drivers/media/common folder, I could not find the ir-keymaps.c file at all. So I moved the folder to a temporary location and did a "sudo apt-get linux-source". Then I had a "linux-source-2.6.20.tar.bz2" file in my /usr/src folder. On extracting this, I found the ir-keymaps.c file in the correct folder. Then, I did the normal modification of the file and "sudo make modules". 

First, it said that loading modules capability was not enabled. So I did a "sudo make menuconfig" and activated the option to load modules. Then, doing "sudo make modules" again, it started to compile. The compiling process took about 20 mins. 

Afterward, I copied the ir-common.ko file to the /lib/modules/2.6.20-15-generic/drivers/media/common folder and rebooted. That's it.

---

### Post by hexion on 2007-06-01
> **t_anjan said:**
> I really don't know what low-latency and generic kernels are. I'll tell you what I did, maybe from that you can tell me what I have.

In my /usr/src/linux-headers-2.6.20-15-generic/drivers/media/common folder, I could not find the ir-keymaps.c file at all. So I moved the folder to a temporary location and did a "sudo apt-get linux-source". Then I had a "linux-source-2.6.20.tar.bz2" file in my /usr/src folder. On extracting this, I found the ir-keymaps.c file in the correct folder. Then, I did the normal modification of the file and "sudo make modules". 

First, it said that loading modules capability was not enabled. So I did a "sudo make menuconfig" and activated the option to load modules. Then, doing "sudo make modules" again, it started to compile. The compiling process took about 20 mins. 

Afterward, I copied the ir-common.ko file to the /lib/modules/2.6.20-15-generic/drivers/media/common folder and rebooted. That's it.

Generic and low-latency kernels are 2 "tastes" of kernels provided by Ubuntu in Feisty. By default generic kernel is installed (you can see which one you have installed with "uname -a" command). You can find the difference between them in these forums, but as far as it concerns us for lirc, it's enough to know that a module build for generic is not compatible with a low-latency kernel and viceversa.

By the way, you couldn't find the .c file at first place, because you were looking at the headers folder :)  .c files are in the source folder you installed later.

---

### Post by t_anjan on 2007-06-04
OK, so the file I posted is for the generic kernel. :-)

---

### Post by migranpipa on 2007-06-09
> **manro said:**
> Here I am again asking for help ;) 

How can I block or disable the "AUTOSCAN" button to lock my session, that's not specified on my .lircrc file!

Thanks for all the help!

Regards,

> **superm1 said:**
> More than likely, the kernel is interpreting the AUTOSCAN event as a real button event.  Go to your gnome shortcut key preferences.  Set your session lock key to something different.

You can also use xsetkeycodes to change the key that is being interpreted by AUTOSCAN similar to a few posts above.


Hi people, manro, have you resolved this? I have been searching in the thread but I didn't find nothing cleary about xsetkeys. I have the same problem, when I push the "full screen" button and many others. Can anybody help me?

Thanks a lot.
 
Sorry, my English is so bad, I am Spanish too.

Regards.

---

### Post by migranpipa on 2007-06-16
Hi, anybody can't help me?

Thanks.

---

### Post by mazirian on 2007-06-16
I just hate lirc.  It's always been trouble for me.  After having defeated it for years it hits me again with another problem. I just updated my kernel to 2.6.20-16-lowlatency today and now although I am able to build the lirc modules easily with modules-assistant the resulting deb installs modules that may not be loaded.

```

[   93.145236] lirc_dev: disagrees about version of symbol struct_module
[   93.161347] lirc_dev: disagrees about version of symbol struct_module
[   93.167722] lirc_gpio: Unknown symbol lirc_unregister_plugin
[   93.168247] lirc_gpio: Unknown symbol lirc_register_plugin

```

grr..

---

### Post by mazirian on 2007-06-16
After much dicking around, I ended up going back to the generic kernel image and rebuilding the lirc modules against kernel source created by m-a fakesource.  That worked fine.  I wonder why I can't build loadable modules when I'm running the low latency kernel image.

---

### Post by Elv13 on 2007-07-21
Hi, i made a serial (lirc) IR reciver. When i tryed to use it under linux, it did not work at all. I tryed it on one of my old laptop that still have windows on it, it worked perfectly with winirc (lirc for windows). I was under gentoo, after few week of hard time, i started to see something when i was doing cat /dev/lirc, it was seeing the remote and writing things when i pressed button. But irrecord was not able to corectly configure it...

Now i am using Ubuntu. No more luck, i get all problem one after the other. After few hack, i am able to modprobe lirc_serial, but it end there


dmesg:
[17179714.200000] lirc_dev: IR Remote Control driver registered, at major 61
[17179714.216000] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179714.216000] lirc_serial: port 03f8 already in use
[17179714.216000] lirc_serial: use 'setserial /dev/ttySX uart none'
[17179714.216000] lirc_serial: or compile the serial port driver as module and
[17179714.216000] lirc_serial: make sure this module is loaded first
[17179998.044000] lirc_serial: auto-detected active low receiver
[17179998.044000] lirc_dev: lirc_register_plugin: sample_rate: 0

i did setserial /dev/ttyS1 uart none and setserial /dev/ttyS0 uart none it is how i got the module to load

I tryed to use the cvs version, the ubuntu version, the debian version, i compiled module automatikly, manually, with debian utils, with a new kernel, with de default kernel and some other combinaison and it always do the same **** things.

When i try irrecord i get

Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.

irrecord: could not find gap.
irrecord: gap not found, can't continue

irw do nothing but start (i had to do a symlink (ln -s /dev/lirc0 /dev/lirc) to prevent it from stoping immediatelly)


I really dont know what to do now, please, help me!

---

### Post by hexion on 2007-07-23
I don't have the knowledge to help you...
First try superm1's wiki to look for help. If you can't find the info, send him a PM. If someone can help you, it's him.

Good luck.

---

### Post by jimbo123 on 2007-07-26
> **Elv13 said:**
> 
Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.

irrecord: could not find gap.
irrecord: gap not found, can't continue

I seem to recall that to kick things off you need to **press and HOLD** a button for the gap to get recognised,.. and then cycle through each button and labelling it.

Jim.....

---

### Post by antiram on 2007-07-31
> **mazirian said:**
> I just hate lirc.  It's always been trouble for me.  After having defeated it for years it hits me again with another problem. I just updated my kernel to 2.6.20-16-lowlatency today and now although I am able to build the lirc modules easily with modules-assistant the resulting deb installs modules that may not be loaded.

```

[   93.145236] lirc_dev: disagrees about version of symbol struct_module
[   93.161347] lirc_dev: disagrees about version of symbol struct_module
[   93.167722] lirc_gpio: Unknown symbol lirc_unregister_plugin
[   93.168247] lirc_gpio: Unknown symbol lirc_register_plugin

```

grr..

i am using lirc-0.8.2 and it works for me with lowlateny-kernel if i "make clean" in lirc-0.8.2 directory and then ./setup etc..

---

### Post by cebe11 on 2007-08-13
I've followed this guide and others and have finally "sort of" successfully got my remote to work.  Details:
Ubutnu Edgy 2.6.17.12
Lirc 0.8.2 
Hauuppauge Nova-S DVB card with IR receiver plugged into the card itself.
Using the /dev/input driver so I compiled using the /dev/input.

I can succesfully load lircd, stop lircd, run IRW and irrecord to get my custom config.  Here is where things go wrong. 
  I can successfully get all key functions mapped and can change what they do for Mythtv using the .mythtv/lircrc file, everything works as expected.  I can even map any number to any key EXCEPT a number key.  For example I can map my number 2 to the Green button and it shows up in Myth as the number 2 as expected.  If I then map the number two to 2 key, nothing happens.
 I can run IRW and see the expected output of all the keys EXCEPT the number keys.  These either don't show up at all or show up as if I typed a the number on the keyboard, not as a true Hauppauge command.

  In the end I can get all the keys to function except the number keys of the remote.
For some reason the kernel input layer is not passing these keypresses onto lircd?  Any suggestions appreciated, this is driving me crazy.
Thanks for any input/suggestions of where to look/try next.

---

### Post by cebe11 on 2007-08-23
bump?

---

### Post by Mfvane on 2007-10-20
Hi,  I am new to this forum, but I have some experience in tempering with lirc, but this time either I am blind, or it is an odd bug...
I have a Pixelview MPEG2 and it worked OK with the gpio module. Since I updated the kernel to the 2.6.22, it no longer supported this module. So, I configured my system in a way that it wouldn't need the gpio module, as seen in one forum.
My hardware.conf ended up like this:

LIRCD_ARGS=""
LOAD_MODULES=true
DRIVER="dev/input"
DEVICE="/dev/input/by-path/pci-0000:02:06.0--event-ir"
MODULES="lirc_dev"
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""
(I also tried putting the device with /dev/input/event4 or /dev/input/irdev, none worked"

the command cat /proc/bus/input/devices recognizes my card

I: Bus=0001 Vendor=1554 Product=4011 Version=0001
N: Name="bttv IR (card=72)"
P: Phys=pci-0000:02:06.0/ir0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=100003
B: KEY=1000000 0 0 0 0

lircd.conf is the original supplied by lirc for this card . 

dmesg :lirc_dev: IR Remote Control driver registered, at major 61

Now, when I try evtest at the /dev/input/event4, it doesn't give me no outputs... as well as when at /dev/input/irdev...
 irw doesn't show any of keys I press, 
I know that the RC is working because dmesg shows 

bttv IR (card=72): unknown key: key=0x01 raw=0x01 down=0 when I press a key.

When trying to run lircd -n, it gives me:
lircd: WARNING: invalid code found for PixelView_PlayTV_MPEG2: ch+
lircd: lircd(devinput) ready
lircd: caught signal

And the whole thing doesn't work. If you guys have any ideas, it would be very welcome!! 
Best wishes and ubuntus for everyone!
Matheus
:)

---

### Post by Mfvane on 2007-10-21
I just fiugured out that my ir-common had been edited to disable the IR-COMMON...
I recompiled it from source and now works great!
Thanks

---

### Post by chuck2 on 2007-11-16
superm1 deserves something for this, thank you.

---

### Post by imblack on 2010-04-10
Can you tell me how you did that please?

---

### Post by Azathoth_ on 2010-05-15
I made the ir_common modifications but now, everytime I try to load the new ir_common.ko it gives me the following:

```
FATAL: Error inserting ir_common (/lib/modules/2.6.32-22-generic/kernel/drivers/media/common/ir-common.ko): Invalid module format
```

Now, I cannot use Lirc since I upgraded to Ubuntu 8.10 Lucid Lynx.

Anyone can help me?

---

### Post by Azathoth_ on 2010-05-16
Finally, I am going to use ir_common: [http://ubuntuforums.org/showthread.php?p=9308971](http://ubuntuforums.org/showthread.php?p=9308971)

---

