---
title: "Slow booting of Ubuntu?"
date: 2019-04-23
forum: New to Ubuntu
---

### Post by swangnation on 2019-04-23
Hi guys, I'm new to Ubuntu so my experience is limited I'm afraid. I've got an asus x550ep latptop amd quadcore 4gb ram and rather unfortunatley 1.5 ghz processor.....its not the best lol but it functions well for basic things as I'm not doing anything major on it.
I just went down from 4 static work spaces down to 1 which has made a difference from the time i log in to graphical interface which is great.....however from the time i power on TO the login in window seems like forever. ( when i say forever i mean it actually feels like more than a minute ) I don't believe it should take that long so when i systemd-analyze blame i get the following :

                        ```
20.747s systemd-journal-flush.service
          19.003s dev-sda2.device
          13.385s systemd-sysctl.service
          12.162s snap-gnome\x2dcalculator-352.mount
          11.758s plymouth-quit-wait.service
          11.162s snap-core-6673.mount
          11.098s snap-gnome\x2d3\x2d28\x2d1804-23.mount
          11.089s snap-gnome\x2d3\x2d26\x2d1604-82.mount
          11.087s snap-gnome\x2dcalculator-260.mount
          11.052s snap-gnome\x2dlogs-45.mount
          11.048s snap-gtk\x2dcommon\x2dthemes-818.mount
          11.029s snap-gnome\x2dsystem\x2dmonitor-57.mount
          11.015s snap-gnome\x2dlogs-61.mount
          10.969s systemd-udevd.service
          10.926s snap-core18-941.mount
          10.874s snap-gnome\x2d3\x2d26\x2d1604-74.mount
          10.847s snap-gnome\x2dsystem\x2dmonitor-70.mount
          10.829s snap-gnome\x2dcalculator-406.mount

          10.805s snap-gnome\x2dsystem\x2dmonitor-77.mount
```

I also just ran systemd-analyze ciritical chain and i got the following:

```
graphical.target @48.614s
&#9492;&#9472;multi-user.target @48.613s
  &#9492;&#9472;systemd-user-sessions.service @36.824s +9ms
    &#9492;&#9472;network.target @29.559s
      &#9492;&#9472;NetworkManager.service @26.147s +3.411s
        &#9492;&#9472;dbus.service @26.119s
          &#9492;&#9472;basic.target @26.072s
            &#9492;&#9472;sockets.target @26.072s
              &#9492;&#9472;snapd.socket @26.027s +44ms
                &#9492;&#9472;sysinit.target @26.026s
                  &#9492;&#9472;systemd-update-utmp.service @25.950s +75ms
                    &#9492;&#9472;systemd-tmpfiles-setup.service @25.704s +243ms
                      &#9492;&#9472;systemd-journal-flush.service @4.954s +20.747s
                        &#9492;&#9472;systemd-remount-fs.service @3.982s +968ms
                          &#9492;&#9472;systemd-journald.socket @3.870s
                            &#9492;&#9472;system.slice @3.870s
```

I can't tell from that if anything is out of the ordinary. Can you guys help?

Can i make the boot up quicker? If so how?

Thanks in advance for your patience and help

---

### Post by jeremy31 on 2019-04-23
Post moved to it's own thread

---

### Post by Autodave on 2019-04-23
What version of 'buntu are you running?

---

### Post by oldfred on 2019-04-23
You may need UEFI/BIOS update (Which you should do anyway) or boot parameter.

       Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221)

---

### Post by TheFu on 2019-04-23
Snaps are known to be slow on boot. [https://askubuntu.com/questions/1051965/ubuntu-18-04-slow-boot-due-to-snapd](https://askubuntu.com/questions/1051965/ubuntu-18-04-slow-boot-due-to-snapd)  I think they solved it, but don't know which version of the snap subsystem has the fix. Don't know if it made it into 19.04.

I know you don't need snaps to have a working system. The same programs are available with out snaps. Just install them using the normal package management and remove the snap package.  I've removed all snaps off my 16.04 desktops.  I don't use Gnome, so removing those will bring a drastic change if you don't get the non-snap version installed. You could be looking at a text screen, no graphics, no mouse, afterwards.  Someone new to Linux might prefer to live with the issue for a few more months until the fix makes it out.

On low-end systems with limited RAM, removing the snapd subsystem is probably the best solution anyway due to the way snaps are designed to work.

The best way to speed up a system like this is to use SSD storage, if you haven't done that already.

I've had boots take over 5 minutes on a UEFI system, before going after some startup fixes. Got it down to 25s now on that machine.

It would be helpful to see the output wrapped in code tags. The indentation conveys some information which is lost.

---

### Post by oldfred on 2019-04-23
Some info on your large time:
       systemd-journal-flush.service @4.954s +[COLOR=#ff0000]20.747s[/COLOR] 

    [https://askubuntu.com/questions/1094389/what-is-the-use-of-systemd-journal-flush-service](https://askubuntu.com/questions/1094389/what-is-the-use-of-systemd-journal-flush-service)

---

### Post by swangnation on 2019-04-24
sorry guys. I'm running ubuntu 18.04.2 Lts, I'm pretty sure it's bionic beaver. I recently flashed a new bios a few weeks ago by the way so my bios is current too.

I just ran sudo apt purge snapd and re installed. I'll reboot and see whats what. Who knows.....it might have done the trick

> **TheFu said:**
> Snaps are known to be slow on boot. [https://askubuntu.com/questions/1051965/ubuntu-18-04-slow-boot-due-to-snapd](https://askubuntu.com/questions/1051965/ubuntu-18-04-slow-boot-due-to-snapd)  I think they solved it, but don't know which version of the snap subsystem has the fix. Don't know if it made it into 19.04.

I know you don't need snaps to have a working system. The same programs are available with out snaps. Just install them using the normal package management and remove the snap package.  I've removed all snaps off my 16.04 desktops.  I don't use Gnome, so removing those will bring a drastic change if you don't get the non-snap version installed. You could be looking at a text screen, no graphics, no mouse, afterwards.  Someone new to Linux might prefer to live with the issue for a few more months until the fix makes it out.

On low-end systems with limited RAM, this is probably the best solution anyway do to the way snaps are designed to work.

The best way to speed up a system like this is to use SSD storage. If you haven't done that already.

I've had boots take over 5 minutes on a UEFI system, before going after some startup fixes. Got it down to 25s now on that machine.

It would be helpful to see the output wrapped in code tags. The indentation conveys some information which is lost.

Your not the first person to suggest that my friend, unless i get more ram on this thing, i might have to seriously consider your suggestion.

Hi again. I just followed the advice in [https://askubuntu.com/questions/1051...t-due-to-snapd]("https://askubuntu.com/questions/1051965/ubuntu-18-04-slow-boot-due-to-snapd") Although i didn't get the proposed repo option in developer options like the advice in the link suggested, i updated anyway and there is a difference. Now i'd like to ask you guys, Is what I've done i.e, systemd-analyze blame and systemd-analyze critical chain the best way to check for boot up time? Or is there another way of looking at boot times? Sorry....Thank you very much for reading and replying by the way. I appreciate it!
In any case, I'm still thinking of editing grub configuration because i do believe that somewhere in there is a unnecessary long timeout of some kind or a delay of some kind. I still think i can get a slightly more quicker boot up time than what i have. 

Beyond that I'll have to throw some more ram on this thing or do as TheFu suggested and run Ubuntu from text instead of graphical interface

---

### Post by TheFu on 2019-04-24
> **swangnation said:**
>  

Beyond that I'll have to throw some more ram on this thing or do as TheFu suggested and run Ubuntu from text instead of graphical interface

Did that "proposed" snapd solution work or not? It isn't clear.

I didn't suggest running in text-only mode, at least that wasn't my intention.  If you are new to Linux, that would probably turn your computer into a doorstop.  Most people need a GUI to do 99% of what they want a desktop.

I suggested installing gnome-desktop using the normal package manager, then removing the gnome parts inside snaps with *snap remove*. The order matters.  I don't know if this works or not.  It could leave the system in a bad situation where reloading is the only option.   Don't do it without having good backups for anything you cannot lose.

I would expect that removing each of the installed snaps BEFORE removing the snapd subsystem would be necessary. Before that, installing the non-snap version of the packages using apt or synaptic or apt-get or aptitude is probably what you want.  This is all guessing.

Be certain you have backups.

---

### Post by Autodave on 2019-04-24
Personally, I do not believe that any more RAM is going to quicken your boot times: 4 gigs should be fine.  You *may* want to consider trying Xubuntu which is a much lighter desktop and will boot quicker than Ubuntu.

---

### Post by Rubi1200 on 2019-04-24
I'm running 18.04 on a fairly old laptop (bought about 7 years ago) with 4GB of RAM. Booting and startup to get to the desktop is pretty slow, but I was expecting that. This is a laptop I use for test purposes, so I don't mind the extra seconds (maybe minute or two) until I am at the desktop.

But if you need something for work or general purposes then go with something lighter and more suited for low end equipment.

Autodave made a good suggestion.

Here are some more options: [https://fossbytes.com/best-lightweight-linux-distros/](https://fossbytes.com/best-lightweight-linux-distros/)

I suggest giving Ubuntu MATE a try.

---

### Post by swangnation on 2019-04-24
> **TheFu said:**
> Did that "proposed" snapd solution work or not? It isn't clear.

I didn't suggest running in text-only mode, at least that wasn't my intention.  If you are new to Linux, that would probably turn your computer into a doorstop.  Most people need a GUI to do 99% of what they want a desktop.

I suggested installing gnome-desktop using the normal package manager, then removing the gnome parts inside snaps with *snap remove*. The order matters.  I don't know if this works or not.  It could leave the system in a bad situation where reloading is the only option.   Don't do it without having good backups for anything you cannot lose.

I would expect that removing each of the installed snaps BEFORE removing the snapd subsystem would be necessary. Before that, installing the non-snap version of the packages using apt or synaptic or apt-get or aptitude is probably what you want.  This is all guessing.

Be certain you have backups.

It has helped however I'm now more adamant that its the grub configuration that needs to be edited also because i think i've done all i can WITHOUT editing the grub configuration manually.

---

### Post by swangnation on 2019-04-24
> **TheFu said:**
> Did that "proposed" snapd solution work or not? It isn't clear.

I didn't suggest running in text-only mode, at least that wasn't my intention.  If you are new to Linux, that would probably turn your computer into a doorstop.  Most people need a GUI to do 99% of what they want a desktop.

I suggested installing gnome-desktop using the normal package manager, then removing the gnome parts inside snaps with *snap remove*. The order matters.  I don't know if this works or not.  It could leave the system in a bad situation where reloading is the only option.   Don't do it without having good backups for anything you cannot lose.

I would expect that removing each of the installed snaps BEFORE removing the snapd subsystem would be necessary. Before that, installing the non-snap version of the packages using apt or synaptic or apt-get or aptitude is probably what you want.  This is all guessing.

Be certain you have backups.


Just wondering if this is normal??

BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,0002,0003,0004
Boot0001* ubuntu
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
grub-install: info: executing efibootmgr -b 0001 -B.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0002,0003,0004
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
grub-install: info: executing efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\shimx64.efi.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0002,0003,0004
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
Boot0000* ubuntu
Installation finished. No error reported.

from the above i get the impression it's trying to boot up 3 times?? I'm confused

---

### Post by oldfred on 2019-04-24
It looks like it listed your UEFI entries with ubuntu as 0001, then deleted 0001 and showed entries.
Then did a new install of ubuntu as 0000 and showed entries again.
Does ubuntu entry work?

---

### Post by swangnation on 2019-04-25
> **oldfred said:**
> It looks like it listed your UEFI entries with ubuntu as 0001, then deleted 0001 and showed entries.
Then did a new install of ubuntu as 0000 and showed entries again.
Does ubuntu entry work?

Silly question but what do you mean by ubuntu entry??

Just so you can get an idea of how long its been since I've used any linux, the last time was back in the dial up days of the mid nineties when i had red hat version 4 along with the manual which is almost as thick as me lol....which i still have by the way.

I've also been forgetting to turn off my automatic updates which has not helped at all! Just turned them off a minute ago and as of now...i will not updating anything for quite a while unless absolutely necessary.

---

### Post by swangnation on 2019-04-25
Hi guys, I'm determined to get to the bottom of this slow boot time. In the previous posts I've explained that i have run a purge on snapd applications/programs and then reinstalled as per instructions in the link suggested and it has definitely helped. So prior to purge, my boot up time ( boot up time meaning from power on to login screen ) was 1 minute 18 seconds. Now my boot up time is is 59 seconds. In the last hour i have turned off all of my auto updates wherever i have found them because the auto updates have not helped at all! Dumb mistake on my part there.

Now I'll explain what happens when i power on : Blank purple screen for between 20 - 30 seconds, then screen goes black for about 3 seconds, then purple screen again with "ubuntu" and the 4 dots progress right beneath for about 10 seconds and then the login screen.

Late last night i did a grub install -v and the following came up : Note that this is before i turned off my auto updates, not sure if that means anything in this context.

BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,0002,0003,0004
Boot0001* ubuntu
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
grub-install: info: executing efibootmgr -b 0001 -B.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0002,0003,0004
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
grub-install: info: executing efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\shimx64.efi.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0002,0003,0004
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
Boot0000* ubuntu
Installation finished. No error reported.

Now in the last hour i have turned off my auto updates and have solemnly vowed ( to myself ) to never upgrade unless absolutely necessary and ran grub install -v again and this is what came up :

BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0002,0003,0004
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
grub-install: info: executing efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu -l \EFI\ubuntu\shimx64.efi.
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0002,0003,0004
Boot0002* UEFI:CD/DVD Drive
Boot0003* UEFI:Removable Device
Boot0004* UEFI:Network Device
Boot0000* ubuntu
Installation finished. No error reported.

Not sure whats happened there or why.

Now I'm going to list what comes up in my grub customizer in order of appearance, sorry by the way but i unable to post screenshots at this point in time.

***List Configuration:***
ubuntu
 menu entry / script linux
[LIST]
[*]advaced menu for ubuntu
[/LIST]
          submenu
          ubunutu, with linux 4.18.0-18 generic 
          menu entry / script linux
          ubunutu, with linux 4.18.0-18 generic (recovery mode)
          menu entry / script linux
          ubunutu, with linux 4.18.0-17 generic [COLOR=#ff0000]I have unchecked this box myself. If it's wrong to do this please correct me
          [/COLOR]menu entry / script linux
          ubunutu, with linux 4.18.0-17 generic (recovery mode) [COLOR=#ff0000]I have unchecked this box myself. If it's wrong to do this please correct me
[/COLOR]          menu entry / script linux
sytem setup
menu entry / script : uefi-firmware

*******General Settings:***
Default Entry : has predefined box checked and (first entry) option selected in dropdown menu. Note in dropdown menu there are the following options Ubuntu, ubunutu, with linux 4.18.0-18 generic, ubunutu, with linux 4.18.0-18 generic (recovery mode) and sytem setup

Visibility : Show menu box is checked, i have unchecked "look for other operating systems" as i only have ubuntu and the boot default entry box is checked at 0 seconds.

Kernel Parameters :
Quiet splash
generate recovery entires box is checked


I hope this helps you guys in pointing me in the right direction becuase i do believe the boot time can be quicker. As mentioned above, it's the blank purple screen that just hangs for 20-30 seconds that takes up the longest time and i do believe it can be reduced. By how much i'm not sure

Again.......i will thank you guys for your patience.

---

### Post by oldfred on 2019-04-25
Do not know grub customizer as the minor changes I do to grub, I just edit the files.

You may  need a boot parameter. Did you review post  #6.

What brand/model system?

---

### Post by swangnation on 2019-04-25
> **oldfred said:**
> Do not know grub customizer as the minor changes I do to grub, I just edit the files.

You may  need a boot parameter. Did you review post  #6.

What brand/model system?


I just ran these

journalctl --disk-usage
Archived and active journals take up 680.0M in the file system.


journalctl -b --unit systemd-journald
-- Logs begin at Fri 2019-03-29 10:41:38 AEDT, end at Thu 2019-04-25 23:20:12 AEST. --
Apr 25 20:06:56 praetorian systemd-journald[270]: Journal started
Apr 25 20:06:56 praetorian systemd-journald[270]: Runtime journal (/run/log/journal/bc694bc40adf4926b81c2dc0b5371e5f) is 4.2M, max 33.8M, 29.5M free.
Apr 25 20:06:57 praetorian systemd-journald[270]: Time spent on flushing to /var is 11.579874s for 771 entries.
Apr 25 20:06:57 praetorian systemd-journald[270]: System journal (/var/log/journal/bc694bc40adf4926b81c2dc0b5371e5f) is 656.0M, max 4.0G, 3.3G free.

system is asus x055e amd quadcore 4gb ram
Brand meaning ubuntu version? 18.04.2 Lts?

---

### Post by TheFu on 2019-04-25
Things that can slow down booting:
* BIOS boot order that doesn't have the Ubuntu Grub disk listed first.  If the BIOS has to check all USB devices first or some optical media, going through all of those can take time.
* Lots of devices connected, especially USB.

Built a new system a few months ago.  Installed one of those 37-in-5 media panels on the front. It provided 4 USB2 ports, 2 USB3 ports and slots for SDHC, MicroSC, CF, SONY MS, MS2 and a few other slot formats.  All the slots go into 1 USB2 header on the MB.  The 4xUSB2 ports go into another header and the USB3 ports yet another header.  I tested them all and they all worked. Great.  But reboots where taking 3-5 minutes.   Because each of those slots might have storage to boot, so the OS decided to check each one.  Checking normal USB ports is relatively fast but checking each of those slots seems to take 20+ seconds.  I don't reboot that system much, so I ignored it for a month.  Then I was doing some work that required multiple reboots and that was driving nuts, so I unplugged all the USB2 connections, leaving just the USB3 and eSATA connection.  Boots were fast again.

If you think the logs are taking too much space, why don't you reduce the allowed size?  There's a journald.conf file for that.  You can also tweak the logrotate.d/ config files as you like.  And if you really don't want much storage used, consider using a RAMdisk for logs like imbedded systems do.

OTOH, if you only reboot once a month, does a slow boot matter?
```
$ uptime 
 11:59:58 up 19 days,  3:44,  3 users,
```
or
```
$ uptime
 11:59:44 up 7 days,  4:50,  6 users,  
``` 
If you reboot daily, would a slight change in habit make this a non-issue?  Boot the computer, then get some coffee, by the time you return, it is ready. Visit most enterprise companies and this happens 50K times every morning.

---

### Post by oldfred on 2019-04-25
Did you update UEFI & SSD firmware?
You may need boot parameter as many models of Asus ahve needed pci=nomsi.
Try by editing grub when you boot and remove quiet splash parameters, so you see boot process. It will go by quickly but may give some clues.
If parameter works we can make it permanent by simple edit to /etc/default/grub.

       Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221)

---

### Post by swangnation on 2019-04-26
Sorry oldfred. Been busy and until now, I've been quite reluctant to open the grub. I have now. I hope this gives you and anyone else a better idea of whats going on with this laptop, I'm going to have a look at the links you posted shortly. AMD have never been all that good. I might have to consider adding a permanent boot parameter because a friend of mine suggested looking into it at the very least as AMD structure is different to Intel.

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-green/black"
GRUB_DISABLE_OS_PROBER="true"

---

### Post by swangnation on 2019-04-26
My apologies oldfred, this laptop doesn't have uefi however i do have the current bios version and as for upgrading ssd firmware? i wouldn't have the faintest idea of how to upgrade if indeed there is an upgrade available. I will have a look shortly and also look at the links you posted previously as well.

I just tried "quiet splash pci=nomsi" and it doesn't work, all it did was add a blank black screen for 2 seconds right before the blank purple screen which just hangs there for forever.

---

### Post by oldfred on 2019-04-26
You posted UEFI boot entries before, so system must be UEFI.
This only shows UEFI boot entries:
sudo efibootmgr -v

I did not think you set colors in /etc/default/grub but in /etc/grub.d/05-debian_theme?
[https://help.ubuntu.com/community/Grub2/Displays#Setting_Menu_Font_Colors](https://help.ubuntu.com/community/Grub2/Displays#Setting_Menu_Font_Colors)

Does your sudo update-grub work or does it give an error or did it create grub.cfg.new as error file     ?

---

### Post by TheFu on 2019-04-26
I've been lost on a few of these posts because the command used with the options used isn't included.  Please
a) show the command, options AND output.
b) use code tags, so it looks the same here, as it does on a terminal.  Spacing/indentation helps. We are used to seeing that stuff.  ANYTHING you are looking at inside a terminal should be shown here with code tags.


Please.

---

### Post by oldfred on 2019-04-26
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then I use quote tag (right most icon) & edit quote to code.

---

### Post by swangnation on 2019-04-26
Sorry guys, your right i haven't been showing input and output. I will do so and will use code tags as well where necessary. 

Oldfred, the answer to your questions is yes.. when i sudo gedit /default/grub yesterday and changed "quiet splash" to "quiet splash pci=nomsi" i got the following output
WARNING **: 08:05:12.386: Set document metadata failed: Setting attribute metadata::gedit-position not supported

However....it did save because i checked it again before rebooting and as i explained before, all it did was add another blank black screen for 2 seconds before going to the purple screen again. I did not actually update grub because i assume in saving, it did that automatically hence the warning message above.

As for setting the colours, i did not get any option at all for setting colours originally when starting up ubuntu for the first time.

When i run ls /sys/firmware/efi/ i get the following : config_table  efivars  fw_platform_size  fw_vendor  runtime  runtime-map  systab  vars, apparently according to what ISN'T there, my system is bios. It's all getting a bit confusing now.


Another thing i saw before i began using Ubuntu, when getting my bios update zip from AMD was that for my laptop X552E, there were 2 variants. X552EA and X552EP. I can't tell which one mine is because at the bottom of the laptop it just says X552E. At the time when i looked at both update zips, they looked identical so i simply chose the slightly bigger file, downloaded it and followed the install instructions. I suppose i shouldn't say they ARE identical because one zip was bigger than the other but in the window where it shows you what changes there are......they were exactly the same. Now I'm really starting to wonder if i actually have the right bios but i simply cannot tell which variant i actually have.

Out of curiosity, will it help to have a look at my bios and post what options are switched on and off? if so...what areas of the bios should i be looking at? To hell with it, I'll do it anyway as it's not going to hurt.

I've taken pictures of my bios screens so if you guys want to look at anything let me know and i will post it. I've got a total of 8 pictures and i don't think i can post them all.

---

### Post by oldfred on 2019-04-26
There are multiple grub files that you can edit. So you have to run this to update your grub menu.
sudo update-grub

So not sure if you included your boot parameter in a boot or not. Best just to manually add it when booting as a test. Then if it works, you know you can permanently add it to grub's configuration file.

Almost all systems since 2012 are UEFI as Microsoft has required them to install Windows in UEFI mode. But many vendors still call it BIOS as they assume users might be confused with the change to UEFI. 

It looks like your system X552E has two different motherboards and that is the difference with which UEFI/BIOS you need.
Does this show motherboard? or change 10 to a few more lines if needed.
sudo lshw | grep -m 1 -A 10 "product"

---

### Post by swangnation on 2019-04-26
> **oldfred said:**
> There are multiple grub files that you can edit. So you have to run this to update your grub menu.
sudo update-grub

So not sure if you included your boot parameter in a boot or not. Best just to manually add it when booting as a test. Then if it works, you know you can permanently add it to grub's configuration file.

Almost all systems since 2012 are UEFI as Microsoft has required them to install Windows in UEFI mode. But many vendors still call it BIOS as they assume users might be confused with the change to UEFI. 

It looks like your system X552E has two different motherboards and that is the difference with which UEFI/BIOS you need.
Does this show motherboard? or change 10 to a few more lines if needed.
sudo lshw | grep -m 1 -A 10 "product"

Ok. when i run sudo lshw | grep -m 1 -A 10 "product" i get the following output :

```
product: X550EP (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: DBN0CV13723645B
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=X sku=ASUS-NotebookSKU uuid=700B4F03-CE7B-F581-3268-BCEE7B0A9C14
  *-core
       description: Motherboard
       product: X550EP
       vendor: ASUSTeK COMPUTER INC.

```
and when i run sudo dmidecode -t 0 i get the following output :

```
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: X550EP.303
    Release Date: 03/13/2014
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 4096 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6
```

Hope that helps.

---

### Post by oldfred on 2019-04-26
This shows you have the EP version:
product: X550EP (ASUS-NotebookSKU)
description: Motherboard
       product: X550EP

And BIOS version:
BIOS Revision: 4.6

---

### Post by swangnation on 2019-04-26
> **oldfred said:**
> This shows you have the EP version:
product: X550EP (ASUS-NotebookSKU)
description: Motherboard
       product: X550EP

And BIOS version:
BIOS Revision: 4.6

As it turns out I've got the correct bios after all. Just wondering if efi boot manager will help get this thing booted up quicker?

---

### Post by swangnation on 2019-04-27
> **oldfred said:**
> There are multiple grub files that you can edit. So you have to run this to update your grub menu.
sudo update-grub

So not sure if you included your boot parameter in a boot or not. Best just to manually add it when booting as a test. Then if it works, you know you can permanently add it to grub's configuration file.

Almost all systems since 2012 are UEFI as Microsoft has required them to install Windows in UEFI mode. But many vendors still call it BIOS as they assume users might be confused with the change to UEFI. 

It looks like your system X552E has two different motherboards and that is the difference with which UEFI/BIOS you need.
Does this show motherboard? or change 10 to a few more lines if needed.
sudo lshw | grep -m 1 -A 10 "product"


"quiet splash pci=nomsi" is not a boot parameter?

Which grub files can i edit? how do i edit them?

---

### Post by TheFu on 2019-04-27
To edit system files, please use **sudoedit**, not sudo gedit.  There are reasons NOT to use GUI editors for system files.  If you must use gedit as the editor, add this to your .bashrc - **export EDITOR=gedit**   , logout, login, but know this will only work from GUI sessions, not ssh or the console. I don&#8217;t know if it fails gracefully or not. Regardless, might want to fix the gedit config file ownership in your HOME, which can cause issues.

Certain system files should be edited using specific tools.  **visudo** is the main one.  crontabs should use **crontab -e**.  All the others should use sudoedit to avoid some issues.  It **is** almost always safe to use sudo nano or sudo vim to edit system files, except those above. They aren't GUI tools and don't write configs owned by root.

grub startup controls are in /etc/grub.d/10_linux
After modifying, sudo update-grub is the minimal required step before rebooting.  Depending on what is modified, mkinitramfs with some options might be needed.  Things like changing the boot file system or adding/removing encryption or LVM or adding 2FA for boot validation. would require the mkinitramfs.

I have 2 Asus boards - a laptop and a Ryzen system. Haven't touched grub to make either boot faster.

---

### Post by oldfred on 2019-04-27
I still do not think you have colors correct in /etc/default/grub and may be the issue.
You should always experiment with manually editing grub when booting with boot parameters as if a setting prevents booting, it is a lot more difficult to change.

Comment these out.
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-green/black"

Then run 
sudo update-grub

Then reboot and manually replace quiet splash  with pci=nomsi.

---

### Post by oldfred on 2019-04-27
I still do not think you have colors correct in /etc/default/grub and may be the issue.
You should always experiment with manually editing grub when booting with boot parameters as if a setting prevents booting, it is a lot more difficult to change.

Comment these out.
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-green/black"

Then run 
sudo update-grub

Then reboot and manually replace quiet splash  with pci=nomsi.

Did you ever do the fixes in post #6? That was 20 seconds of your boot time.

---

### Post by swangnation on 2019-04-28
Thank you TheFu, I will revert back to your answer in the above post should i forget

Oldfred, the answer is yes, I tried it before, i just forgot to mention it is all so i just ran this as well ```
journalctl -b --unit systemd-journald
``` and my output was this ```
-- Logs begin at Fri 2019-03-29 10:41:38 AEDT, end at Sun 2019-04-28 15:32:42 AEST. --
Apr 28 14:47:53 praetorian systemd-journald[267]: Journal started
Apr 28 14:47:53 praetorian systemd-journald[267]: Runtime journal (/run/log/journal/bc694bc40adf4926b81c2dc0b5371e5f) is 4.2M, max 33.8M, 29
Apr 28 14:47:54 praetorian systemd-journald[267]: Time spent on flushing to /var is 15.845256s for 772 entries.
Apr 28 14:47:54 praetorian systemd-journald[267]: System journal (/var/log/journal/bc694bc40adf4926b81c2dc0b5371e5f) is 832.0M, max 4.0G, 3.
```

Also i got my grub menu off hidden. I took a photo of what came up and maybe there is something there that can be tinkered with. By the way i will try what you suggested regarding the colours in the grub config,

---

### Post by swangnation on 2019-04-28
Ok Oldfred, i commented out

 export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="light-green/black"

i saved and rebooted. Negative on any results. Purple screen just hangs there after i click on ubuntu in grub menu.

As for post 6 regarding the link which provided info on flush service etc, i still need to go over a bit it more carefully so i can understand it.

Regarding replacing "quiet splash" with "pci=nomsi" i did that, i got page after page of text with "ok" in green on the left side of screen and i think i saw 2 "failed" in red however the pages went by so quick that i didn't get a chance to read them. In the end it still took the same time to load up. I must say i didn't time it but it felt the same.

After that i tried "quiet splash pci=nomsi", obviously i didn't get page after page of text but i did get the exact same purple screen which just hangs there for 30 seconds. ( i actually timed how long the purple screen stays up and it's actually 30 seconds ).

---

### Post by oldfred on 2019-04-28
Rerun these just to see if any actual change.
        systemd-analyze
systemd-analyze critical-chain 
systemd-analyze blame


Do you use snaps? They have made some fixes so not as slow as they used to be.
      
 boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)

---

### Post by swangnation on 2019-04-29
> **oldfred said:**
> Rerun these just to see if any actual change.
        systemd-analyze
systemd-analyze critical-chain 
systemd-analyze blame


Do you use snaps? They have made some fixes so not as slow as they used to be.
      
 boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)

I think i am, although in the snap directory all i have is gnome system monitor, unless there are more snap packages that i can't see.

in my software, other software section I've got 2 unchecked boxes for canonical as the screenshot shows, silly question maybe but do i have to check those boxes to get the snap improvements or do i get those snap improvements automatically when i upgrade packages?

as for the systemd-analyze etc, I'll be doing that shortly and then having a look at post 6 regarding the links about the vacuum command/instructions shorty and i will let you know. I will thank you again for your time and patience oldfred and everyone else too! Once something is in my head, i will never let it go until I'm satisfied that nothing else can be done.

---

### Post by oldfred on 2019-04-29
This removes all of snap. But if you want any of its applications, do not use Software Center to install as it does not say if you are getting snap or the .deb version.
sudo apt autoremove --purge snapd

I installed 19.04 and it was slow. Removing snap helped some, but there are a lot of messages in log files on some of the issues. It still is taking about 40 sec to boot from my HDD. My main working install of 18.04 on SSD is only somewhat faster at 27 sec. Several versions ago 16.04 when system was new boot was under 10 sec from SSD. And my old laptop with 5400rpm HDD was only 40 sec.
Or a lot of issues and most of us are living with them. Some seem to have fixes which I am trying to accumulate into one long list.

---

### Post by mrdc76 on 2019-04-29
18.04 is just slow to boot on the three different computers I have it installed on. On a Thinkpad T450 with a SSD:

Startup finished in 6.051s (firmware) + 3.978s (loader) + 22.695s (kernel) + 10.320s (userspace) = 43.046s
graphical.target reached after 9.971s in userspace

16.04 was much faster.

I'd recommend to stop tinkering and report a bug.

---

### Post by oldfred on 2019-04-29
I think the problem is not one issue, but a variety of issues. And developers are not good about fixing something generic like slow boot.
Some is system, some is UEFI settings and only the Ubuntu software can possible be fixed. They already know snaps are slower, and are making changes to speed them up.

These types of issues are not bugs.
Found user with DVD installed & for whatever reason system was trying to do a fsck on it.
Some dual booters had second install reformat swap and new UUID did not then match in first install in fstab or this:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1763611](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1763611)
/etc/initramfs-tools/conf.d/resume
Some just need UEFI and SSD firmware updates.
Or need specific boot parameters to avoid system issue.

If we can separate issues & post specific bugs that would be a good start.

---

### Post by swangnation on 2019-04-30
I'm starting to believe it's this version of Ubuntu that is slow in booting up in general. Thanks for the feedback and help guys. Oldfred I'm going to try sudo apt autoremove --purge snapd and that's going to be it. I went over the link in post 6, thank you by the way, regarding the vacuum option / instructions and i really don't think that it's the right solution for this computer at this point in time. I just know it's going to lead to other issues down the track.

I just ran sudo apt autoremove --purge snapd and this was the output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'snapd' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


Thanks for the tip about software centre. Come to think of it i don't believe i need software centre for the time being so i might as well remove it. I suppose i can always re install it later.

I think I'll just put this slow boot up aside for the time being and just live with it.

I don't know about you guys, but i think there should be another label other than solved because i don't believe for a second that I'm the only one experiencing slow boot up. Having said that if you guys are in agreement i will change the post to solved if there's no other label to use.

Thanks guys for your time and patience and advice. I appreciate it.

---

### Post by swangnation on 2019-05-01
I think i may have discovered the problem guys. Bare with me on this.

when i run sudo blkid i get the following output :
```

/dev/sda1: UUID="5DC3-6837" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="e000da08-a5a8-4be8-8daf-7cd675391fb6"
/dev/sda2: UUID="9de9c2ba-62f7-432d-80a6-d71aed4140c8" TYPE="ext4" PARTUUID="f8c6f955-f15a-4264-ae44-b0b2cc49360b"
```

Then when i run cat /etc/fstab i get the following output :

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=9de9c2ba-62f7-432d-80a6-d71aed4140c8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=5DC3-6837  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/swapfile non swap sw 0 0
```


I created an 8gb swap file. Why isn't it showing up here and is it possible that the system is trying to find it but can't, gives up on trying to find it and THEN boots up?

---

### Post by oldfred on 2019-05-01
Ubuntu default install now uses a swap file, which you show.
You do not show a swap partition nor the system trying to mount a swap partition.

Does this show swap file?
ls -lh /swapfile
sudo swapon --show

---

### Post by swangnation on 2019-05-01
> **oldfred said:**
> Ubuntu default install now uses a swap file, which you show.
You do not show a swap partition nor the system trying to mount a swap partition.

Does this show swap file?
ls -lh /swapfile
sudo swapon --show

sudo swapon --show :


```
NAME      TYPE SIZE USED PRIO
/swapfile file   8G   0B   -2
```

hmmm

---

### Post by oldfred on 2019-05-02
How much RAM do you have if not 16GB or more swap is too large.

---

### Post by kellykate on 2019-05-03
I'm not experiencing any slow boot on my site. I only have 8gb ram mind you.

---

### Post by oldfred on 2019-05-03
Slow boot should not be related to RAM unless you have less than 2GB.

---

### Post by oldfred on 2019-05-04
I just made the following changes, did not test all at once so not sure which made real difference

turned off NetworkManager-wait
Changed systemctl daily timer for 
housecleaned systemctl logs
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting

fred@Bionic-Z170N:~$ systemd-analyze
Startup finished in 2.794s (kernel) + 8.918s (userspace) = 11.712s
graphical.target reached after 8.899s in userspace

Was over 30 sec, then after some changes, mid 20 sec. Now about 12 sec.

I can post details if desired, of how I changed settings, but late now, so signing off.

---

### Post by swangnation on 2019-05-05
i have 4gb ram Oldfred. with ```
systemd-analyze blame
``` i get the following :

 ```
18.589s systemd-journal-flush.service
         17.987s plymouth-quit-wait.service
         15.099s dev-sda2.device
         13.453s systemd-tmpfiles-setup-dev.service
         11.443s apt-daily-upgrade.service
          4.709s grub-common.service
          4.523s udisks2.service
          4.473s networkd-dispatcher.service
          3.468s preload.service
          3.418s ModemManager.service
          3.005s systemd-sysctl.service
          2.871s NetworkManager.service
          2.612s accounts-daemon.service
          2.526s motd-news.service
          2.217s apt-daily.service
          1.844s [EMAIL="user@121.servic"]user@121.servic[/EMAIL]e
          1.560s apport.service
          1.492s keyboard-setup.service
          1.425s systemd-resolved.service
```

Why can't i just disable the top 5 services so they don't boot up? AM I able to disable them without running into any issues?

---

### Post by oldfred on 2019-05-05
I cleared systemd journal, saved several GB as now MB. May be slow reading/writing on boot if large.
Added this command to a script I run weekly on housecleaning.

[https://ma.ttias.be/clear-systemd-journal/](https://ma.ttias.be/clear-systemd-journal/)
[https://unix.stackexchange.com/questions/139513/how-to-clear-journalctl](https://unix.stackexchange.com/questions/139513/how-to-clear-journalctl)
du -hs /var/log/journal/
ls -lath /var/log/journal/*/ | tail -n 2
Clear logs over 10 days
sudo journalctl --vacuum-time=10d

Changed grub parameters to add noplymounth & remove quiet splash (fastboot only for skylake and newer or it may make issues):
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth i915.fastboot=1"
sudo nano /etc/default/grub
sudo update-grub

[https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297](https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297)
This is Debian bug #844453. apt-daily.service shouldn't be run during boot
in /etc/systemd/system/apt-daily.timer.d/override.conf
/etc/systemd/system

[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)
sudo systemctl edit apt-daily.timer
> # apt-daily timer configuration override
[Timer]
OnBootSec=15min
OnUnitActiveSec=1d
AccuracySec=1h
RandomizedDelaySec=30min

systemctl status plymouth-quit-wait.service
[https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297](https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297)
sudo systemctl edit apt-daily.timer
file:///etc/systemd/system/apt-daily.timer.d
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1667769](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1667769)

---

### Post by TheFu on 2019-05-05
> **swangnation said:**
> i have 4gb ram Oldfred. with ```
systemd-analyze blame
``` i get the following :

 ```
18.589s systemd-journal-flush.service
         17.987s plymouth-quit-wait.service
         15.099s dev-sda2.device
         13.453s systemd-tmpfiles-setup-dev.service
         11.443s apt-daily-upgrade.service
...
```

Why can't i just disable the top 5 services so they don't boot up? AM I able to disable them without running into any issues?

You can do whatever you like, but expect bad things to happen if important services are disabled.

sda2 is probably where the OS is loaded. Do you want to boot?
tmpfiles are absolutely critical to a running Unix system. If you prevent those, nothing will work. No processes will start.
The apt-daily thing, you can disable, but then you'll need to manually handle all patching. I do it that way. Every Saturday morning.

Flushing the journal can be sped up by doing it more often so the files aren't too large.  There's a way to limit how long or how large the files can be.  I think mine are limited to 100MB - I changed it when you opened this thread and haven't seen any negative impacts on my minimal Ubuntu 16.04.6 box.

You don't need these either, but some convenience things will stop working
 ```

          4.523s udisks2.service
          3.418s ModemManager.service
          2.871s NetworkManager.service
```
If network-manager is disabled and that is how the networking is configured, then the system won't have networking.  I haven't used it ... er ... ever.
udisks is for mounting non-core file systems like remote Samba, USB and other GUI configured storage.  If you used it previously and the storage isn't available anymore, perhaps it is still looking for it? 
If you only mount storage through the /etc/fstab and never use gvfs or a GUI to mount it, then udisks isn't needed. From the manpage: ```

 udisks is only indirectly involved in what devices and objects are shown in the user interface.
``` It is part of gnome, so GUI-centric.
/lib/systemd/system/udisks2.service has this:
```
[Install]
WantedBy=graphical.target
```
So, it is only used by a graphical boot, not a console only boot.  That means the system doesn't absolutely need it.

Many of the services on your system seem to be convenience for full desktops and expected for desktop users. [https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

### Post by drvshrm on 2019-05-05
Which version of ubuntu you are using...did you install any new software just before the problem???

---

### Post by swangnation on 2019-05-06
> **drvshrm said:**
> Which version of ubuntu you are using...did you install any new software just before the problem???

This is my first install of ubuntu 18.04lts. Unfortunately its the only linux that will run on this machine. Mint won't load, fedora was negative along with centOS and puppy. I gave up but i was determined to get some form of linux on this machine as it should be pretty good for basic stuff so I got a friend of mine to put the image on one of his hard drives at his workplace because this machine won't even boot up from a CD or a flash drive. Then i removed my hard drive which has windows 8 and replaced it with the hard drive that had ubuntu on it. I did the rest through apt-get.

Based on this : sudo journalctl -b --unit systemd-journald
```

-- Logs begin at Fri 2019-03-29 10:41:38 AEDT, end at Mon 2019-05-06 20:25:03 AEST. --
May 06 17:38:04 praetorian systemd-journald[262]: Journal started
May 06 17:38:04 praetorian systemd-journald[262]: Runtime journal (/run/log/journal/bc694bc40adf4926b81c2dc0b5371e5f) is 4.2M, max 33.8M, 29
May 06 17:38:04 praetorian systemd-journald[262]: Time spent on flushing to /var is 18.624968s for 770 entries.
May 06 17:38:04 praetorian systemd-journald[262]: System journal (/var/log/journal/bc694bc40adf4926b81c2dc0b5371e5f) is 1.2G, max 4.0G, 2.7G
```

would this command be correct or work? : sudo journalctl --vacuum-size=1G --vacuum-time=5d --vacuum-files=5

Also, how can i determine if i can replace grub2 with systemd-boot?

---

### Post by oldfred on 2019-05-06
Have not used nor know about systemd-boot. I think with every kernel update you will have to copy updated files into ESP.
You may want to look at old gummiboot info:
Gummiboot is dead, of course, because it was spun into systemd 2015
[https://www.freedesktop.org/wiki/Software/systemd/systemd-boot/](https://www.freedesktop.org/wiki/Software/systemd/systemd-boot/)

---

### Post by swangnation on 2019-05-09
I've got another idea....i think.

When i replaced "quiet splash" with "pci=nomsi" in grub config, obviously all i got was page after page of scrolling text with everything that was booting up in text instead of the purple screen. Is there a way i can redirect that boot up process or verbose i think its called into a text file? or somehow copy all of that text that comes up into a text file?

when all that text comes up, on the left of the screen there is "ok" in green but from memory there were two "failed" in red. I think it might help to see what those things are but also, just to see whats booting up in more detailed form i suppose.

---

### Post by danieledei on 2019-05-09
Not only slow booting but 
1)   freezing within minutes -   Again same problem after the last update :   it has been fine for a while and now thy have done it again !!!
2)  whitin minutes  looses wi-fi  completely -  not seeing any SSID


lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
00:13.0 SATA controller: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 0e)
00:1c.1 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 2 (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 0e)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Intel Corporation Wireless 3160 (rev 93)
 
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 5986:0671 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
dmesg
 
[    0.000000] Linux version 4.15.0-48-generic (buildd@lgw01-amd64-036) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #51-Ubuntu SMP Wed Apr 3 08:28:49 UTC 2019 (Ubuntu 4.15.0-48.51-generic 4.15.18)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-48-generic root=UUID=79b80baf-dd32-44b0-a27e-308f2cf3f723 ro quiet splash vt.handoff=1
[    0.000000] KERNEL supported cpus:

---

### Post by VMC on 2019-05-09
> **swangnation said:**
> ...
Also, how can i determine if i can replace grub2 with systemd-boot?
I like systemd-boot, but the problem is your kernels need to reside inside $esp. That makes for a large partition if you have several OS's.
My $esp is 100mb therefore I will use grub.

---

### Post by swangnation on 2019-05-10
> **VMC said:**
> I like systemd-boot, but the problem is your kernels need to reside inside $esp. That makes for a large partition if you have several OS's.
My $esp is 100mb therefore I will use grub.

I have 500gb HD and only ubuntu. If i move my kernel to esp and use systemd-boot, will that speed things up a little bit?

---

### Post by VMC on 2019-05-10
efiboot shouldn't have anything to do with slow booting. How did you compare "slow booting" Did it boot faster at one time. If so, what OS was installed?

---

### Post by oldfred on 2019-05-10
Just installed Mate to 64GB flash drive, yesterday. 
Install was very slow as writing to flash drives is very slow.

First boot of flash drive was 3 min & 55 sec which seems about right.
But it turns out the systemd-analyze firmware number is from first boot, so on my warm reboots that kept getting much larger.

But after making the changes I posted in #48 & #50 boot time dropped a lot.
I had printer on which slowed it a lot. But when I turned printed off, it crashed?

Not sure if some of improvement was internal optimization as you reboot.
but udsisk when from 35s to 11s to 5 sec.
network entry went from 12.5s to 6.8 sec to 4 sec.

I did add noatime to mount of /  and added entry to mount tmpfs in RAM to reduce writes.

Last test reboot was about 21s to login. and it reported 8.2s to graphical screen which seems about right. 
Firmware was up to 23minutes, but that was 3 reboots and editing.

Boot time of Mate from slower flash drive now seems pretty quick.

---

### Post by swangnation on 2019-05-10
> **oldfred said:**
> Just installed Mate to 64GB flash drive, yesterday. 
Install was very slow as writing to flash drives is very slow.

First boot of flash drive was 3 min & 55 sec which seems about right.
But it turns out the systemd-analyze firmware number is from first boot, so on my warm reboots that kept getting much larger.

But after making the changes I posted in #48 & #50 boot time dropped a lot.
I had printer on which slowed it a lot. But when I turned printed off, it crashed?

Not sure if some of improvement was internal optimization as you reboot.
but udsisk when from 35s to 11s to 5 sec.
network entry went from 12.5s to 6.8 sec to 4 sec.

I did add noatime to mount of /  and added entry to mount tmpfs in RAM to reduce writes.

Last test reboot was about 21s to login. and it reported 8.2s to graphical screen which seems about right. 
Firmware was up to 23minutes, but that was 3 reboots and editing.

Boot time of Mate from slower flash drive now seems pretty quick.


can you post more details about #48 please.

---

### Post by oldfred on 2019-05-10
Details were in #50.

---

### Post by swangnation on 2019-05-10
guys, i just ran 
**p```
arted /dev/sda print**
```

i got the following output

```
Model: ATA SAMSUNG HM251HI (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   250GB  250GB  ext4

```

does that look right to you guys? Anything worth changing?

---

### Post by oldfred on 2019-05-11
That is a standard UEFI install.
A bit more advanced is to separate system from your data or have a separate /home partition.

And many of us go one step further and use data partition(s). But then you need to understand, mounting, editing fstab, ownership & permissions.
Having /home as a partition does all that automatically if you set it up during install.

You can create a new /home partition with step by step instructions which cover the details.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I like to keep / at 25 or 30GB but have all data in my data partition so / only actually uses about 7 GB.
QUOTE
Excluding all the tmpfs entries, sdc is flash drive:
```
fred@Bionic-Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
/dev/sda4        25G  7.4G   17G  32% /
/dev/sda1        50G   79M   50G   1% /boot/efi
/dev/sdb6       298G   64G  220G  23% /mnt/data
/dev/sdc4        36G   25G  9.5G  72% /media/fred/data
/dev/sdc3        21G  6.0G   14G  31% /media/fred/mateUSB

```

---

### Post by swangnation on 2019-05-26
> **oldfred said:**
> That is a standard UEFI install.
A bit more advanced is to separate system from your data or have a separate /home partition.

And many of us go one step further and use data partition(s). But then you need to understand, mounting, editing fstab, ownership & permissions.
Having /home as a partition does all that automatically if you set it up during install.

You can create a new /home partition with step by step instructions which cover the details.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I like to keep / at 25 or 30GB but have all data in my data partition so / only actually uses about 7 GB.
QUOTE
Excluding all the tmpfs entries, sdc is flash drive:
```
fred@Bionic-Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
/dev/sda4        25G  7.4G   17G  32% /
/dev/sda1        50G   79M   50G   1% /boot/efi
/dev/sdb6       298G   64G  220G  23% /mnt/data
/dev/sdc4        36G   25G  9.5G  72% /media/fred/data
/dev/sdc3        21G  6.0G   14G  31% /media/fred/mateUSB

```

don't know how to say this but i just back tracked on some of the things I've looked at done to try and make my boot up a little faster and i realized i made some basic errors. In the fstab file, instead of having/swapfile none swap sw 0 0

it was /swapfile non swap sw 0 0. Maybe this makes a difference, better to assume it does.

but also i didn't edit /etc/initramfs-tools/conf.d/resume, and now i remember why. It's because that file is empty. So what file is being used instead? or where is the file i need to edit?

I'm actually beginning to think that all these problems are being caused by the initial installation of ubuntu which i didn't do and that maybe it might be a good idea to reinstall, however i cannot boot off a usb or cd on this laptop.

---

### Post by oldfred on 2019-05-26
If you cannot boot USB, you may need to turn on in UEFI allow USB boot or full USB access type setting.
Or if UEFI Secure Boot is on, that may also prevent USB boot as not secure unless you specifically allow it.
And they USB flash drive has to be correctly configured so UEFI will see it as a boot option in the one time boot menu, often f12 or f10.

---

### Post by Dennis N on 2019-05-26
The drive that is listed in the display in post #63 is a 5400 rpm drive. Have you considered an SSD? You could vastly improve boot time just by changing to SSD.

---

### Post by swangnation on 2019-05-27
your right dennis n, an ssd drive will be quicker but then if I'm going to start spending money i might as well put together a pc. In any case i think i'll give this bios a tickle and see what happens. Is there a thread on here that is best for asking questions about bios and uefi?

---

### Post by oldfred on 2019-05-27
You can start a new thread with that in title.
Lots of info on UEFI in link in my signature below and further links in it.
UEFI/BIOS  varies by vendor, best to check what your manual and vendor's site say for your specific model.

---

### Post by oldrocker99 on 2019-05-27
If you have problems with UEFI, try Legacy. It's been my own experience that using UEFI, which has kept grub from installing, leaving an unbootable computer, for me.

---

### Post by swangnation on 2019-05-27
in my bios i have legacy enabled. Unless I'm misunderstanding something. Just spoke to asus on the phone, the "IT professional" couldn't help as he wasn't confident that my laptop would restart. He advised that i take it to a service centre. Which i will not do. Oldfred, i think i will start a thread once i start making some headway into this, that way i can post as much information that will be helpful as possible.

---

### Post by swangnation on 2019-05-31
Hi guys, back again...

I've sort of solved the problem in a round about way...by creating a bootable usb and re installing ubuntu. Ubuntu runs a lot more smoothly now compared to before, and now, i have a 1gb swap partition in stead of a swapfile. I also have full encryption as well so from powering on this laptop to logging in (i also have to input a 10 word encryption password at the beginning) only takes 1 minutes 09 seconds. I can't really complain about that if I'm honest because its only about 11 seconds slower than before with the difference of full encryption.

I can't exactly say how because my terminology isn't the best as i am new to ubuntu but i knew something went wrong with the original install but i wasn't there to see it as a friend of mine put ubuntu on the hard drive. Either way, i think I'll leave the boot process alone for now and see how this goes for a while.

---

### Post by oldfred on 2020-07-23
Some other slow boot threads.
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

I do not use snaps. Just install .deb if I want that app. But there are some that you may need to use snap.
sudo apt autoremove --purge snapd

My motherboard does not support fwupd Most newer systems from Dell & Lenovo are supported.
sudo apt-get purge fwupd
No bluetooth, so uninstall
sudo apt-get autoremove blueman bluez-utils bluez bluetooth
No thunderbolt
systemctl status bolt 
boltctl list
sudo systemctl disable bolt.service

changed grub from quiet splash to noplymouth, will see boot process rather than Ubuntu logo

---

### Post by &amp;wP*!) on 2020-07-23
Another reason of slow boot is that UUID of any partition might be different than the ones in /etc/fstab. The system boots despite that, but UUID mismatch causes slow boot. I had observed that at Arch Linux-Lubuntu dual-boot. By accident I had formatted swap partition on Arch which updated UUID which did not match the one in /etc/stab of Ubuntu.

---

