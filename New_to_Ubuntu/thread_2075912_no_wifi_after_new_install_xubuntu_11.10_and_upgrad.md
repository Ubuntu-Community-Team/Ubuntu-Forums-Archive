---
title: "no wifi after new install xubuntu 11.10 and upgrade to 12.04"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by pjstock on 2012-10-24
I have installed Xubuntu on an oldish laptop with a fresh install of 11.10 (12.04 wouldn't install because of some kernel PAE conflict) and then upgrading immediately to 12.04.

But the wifi is not working. (and I wasn't' smart enough to check whether it was working after the 11.10 as I had a wired ethernet connection running.)

Oddly, pulling down the Networking icon (the up/down arrows) it shows Enable Wireless checked and enabled. 
but futher down I see a greyed out "wireless disabled"

the firewall test shows "inactive".
I looked for other similar posts but haven't found a fix.

full ubuntu has worked so seamlessly for me that I guess I have become lazy.

can anyone advise?

---

### Post by Tamlynmac on 2012-10-25
> pjstock

A quick thought.

Assuming it's a laptop:

You may have a wifi hardware switch. Check to see if you have both  an Fn key and a wifi key on your keyboard. The wifi key is probably located under one of the F/number keys (should look like an antenna giving off signals) at the top of your keyboard. Press the Fn key holding it down and then press the F/wifi key, then release both. Wait a few seconds and see if your wifi comes on.

If this works, some BIOS's I've seen, have a setting to turn on wifi at boot. You may wish to check and see if yours does and if it's turned on.

Also, it might help to post your system specs including what type of wifi card your using, should this not work.

Hope this helps.

---

### Post by NikTh on 2012-10-25
Hi , 

plug your ethernet cable , so you have wired conneciton up and running and then open a terminal and copy-paste bellow commands, one by one. 

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/netinfo
chmod +x netinfo
./netinfo 

```with the last command a txt file named [SIZE=3]**netinfo.txt**[/SIZE] will be created to your home directory. **Please attach this file here **on a reply , by clicking on "New Reply" and then click the paperclip icon at the message toolbar to attach the file. 

Thank you.

---

### Post by Herby Pepper on 2012-10-25
1. plug your Ethernet cable for wired connection. 
2. go to Additional Drivers (it is in Preference) - that will look for missing drivers that you need for your computer to work properly . 
3. if there is wireless driver just "activate" it.

---

### Post by pjstock on 2012-10-25
i should have been clearer.
Yes, it is a laptop.
I checked the Bios and the wireless adapter is Enabled.
and the Fn+F2 does toggle wireless on and off and is also enabled in the Bios and seems to be working.

I'll now run those commands and post the results.

Thank you.

> **Tamlynmac said:**
> A quick thought.

Assuming it's a laptop:

You may have a wifi hardware switch. Check to see if you have both  an Fn key and a wifi key on your keyboard. The wifi key is probably located under one of the F/number keys (should look like an antenna giving off signals) at the top of your keyboard. Press the Fn key holding it down and then press the F/wifi key, then release both. Wait a few seconds and see if your wifi comes on.

If this works, some BIOS's I've seen, have a setting to turn on wifi at boot. You may wish to check and see if yours does and if it's turned on.

Also, it might help to post your system specs including what type of wifi card your using, should this not work.

Hope this helps.

"wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/netinfo
chmod +x netinfo
./netinfo"

thank you 
that procedure seems to create a file called "Netinfo" but the resulting text file, "Netinfo.txt" is size = 0, appears to be empty and fails to upload when I try to attach it as a file.

what am I doing wrong?

Peter

---

### Post by NikTh on 2012-10-25
> **pjstock said:**
> 
thank you 
that procedure seems to create a file called "Netinfo" but the resulting text file, "Netinfo.txt" is size = 0, appears to be empty and fails to upload when I try to attach it as a file.

what am I doing wrong?

Peter

Run again the last command with sudo prefix
```
sudo ./netinfo
``` 

it will ask for your password. Make sure you write the password correctly , cuz nothing appears when you write your password(this is normal). 

Thanks.

---

### Post by westie457 on 2012-10-25
If you go to your /Home folder in 'Nautilus' and double-click on the wireless.script file you downloaded you should get a window with these options 'Run in Terminal', 'Display', 'Cancel' and 'Run'.
Selecting either the first or the last options you will be asked for your password. When that has been entered the 'Network.txt' file will be created and filled. Attach that file to a new reply as 'NikTh' has already requested.


Edit. Beaten by 'NikTh'

---

### Post by pjstock on 2012-10-25
Now I am feeling really dumb.

Nautilus I read is the basic Ubuntu (and maybe all Linux?) file manager. Is this just what shows me the various files, as in on my desktop etc?

(Somewhere I've read that Thunar is the degault FM for Xubuntu and that Nautilus should not be installed or used. True? false?)

in any event, if what I am supposed to do is just "get to" my home folder and then 2xClick on Netinfo, when I do that I get this error message:

"Failed to run iwlist 'scan' as user root.

Unable to copy the user's Xauthorization file."

Am I doing something wrong here? 

Thanks for your patience.

Tada!

thanks for that sudo tip.

There's my Netinfo.txt file

---

### Post by NikTh on 2012-10-25
Hi , 

try this and tell me if wireless working . 

```
sudo modprobe -rvf b43legacy
``` 

and then 

```
sudo modprobe b43
``` 

wait 5-10 secs and tell me if wireless arisen 

Thanks

---

### Post by kimberlite on 2012-10-25
> **pjstock said:**
> Now I am feeling really dumb.

Do not feel so. ...
> 
Nautilus I read is the basic Ubuntu (and maybe all Linux?) file manager. 

It is default for Gnome based environments (AFAIK)

> 
(Somewhere I've read that Thunar is the degault FM for Xubuntu and that Nautilus should not be installed or used. True? false?)


If you are using Ubuntu (unity/gnome based desktop environment - DE) - instead of Kubuntu/Lubuntu/Xubuntu/etc, than you should stick to Nautilus, which is the most integrated file manager into gnome/unity DE.

---

### Post by pjstock on 2012-10-25
Hmmm, very strange.

I tried those two commands.

No joy as yet.

Initially the items in the Networking pull down did change. "Wireless" was there (and was not before) but there was a message about Firmware (the pulldown list has changed and I could not get a screenshot.)

Next it changed to:
Wireless
Wireless disabled (even though below there was a checkmark next to wireless)

Now, 5 minutes later, after I tried those two modprobe commands again, the Wireless section has disappeared again completely.

---

### Post by NikTh on 2012-10-25
OK , 

try something else. 

Give these command in terminal 

```
echo 'blacklist b43legacy' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'b43' | sudo tee -a /etc/modules
``` 

Reboot your PC and see if wireless working. 

If not , give the results of 

```
lsmod 
dmesg | grep -ie firm -ie net -ie b43
``` 

Thanks

---

### Post by pjstock on 2012-10-25
after lsmod:

peter@peter-Latitude-D505:~$ lsmod
Module                  Size  Used by
pcmcia                 39791  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
rfcomm                 38139  16 
bnep                   17830  2 
dell_laptop            17767  0 
snd_timer              28931  2 snd_pcm,snd_seq
dcdbas                 14098  1 dell_laptop
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  17912  2 
soundcore              14635  1 snd
bluetooth             158438  23 rfcomm,bnep,btusb
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32325  0 
psmouse                96684  0 
mac_hid                13077  0 
i915                  414979  2 
serio_raw              13027  0 
parport_pc             32114  1 
drm_kms_helper         45466  1 i915
drm                   197599  3 i915,drm_kms_helper
b43                   342643  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          40180  0 
ssb                    50691  1 b43
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e100                   36289  0

after

dmesg | grep -ie firm -ie net -ie b43

peter@peter-Latitude-D505:~$ dmesg | grep -ie firm -ie net -ie b43
[    0.000000]   Transmeta GenuineTMx86
[    0.042221] NET: Registered protocol family 16
[    0.131661] NetLabel: Initializing
[    0.131664] NetLabel:  domain hash size = 128
[    0.131667] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.131685] NetLabel:  unlabeled traffic allowed by default
[    0.205418] NET: Registered protocol family 2
[    0.208573] NET: Registered protocol family 1
[    0.209292] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    0.209892] audit: initializing netlink socket (disabled)
[    0.626738] NET: Registered protocol family 10
[    0.628518] NET: Registered protocol family 17
[    1.562034] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.641750] b43-pci-bridge 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   16.354091] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.710558] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   17.273393] NET: Registered protocol family 31
[   17.952870] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.353531] type=1400 audit(1351196674.583:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[   19.093600] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.094749] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.096755] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.055553] type=1400 audit(1351196678.283:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=882 comm="apparmor_parser"
[   90.085660] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   90.089104] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

---

### Post by NikTh on 2012-10-26
Check in Network-Manager if **Enable Wireless** is checked. 

and try ```
sudo apt-get install firmware-b43-installer
``` 

reboot and check again if wireless works. 

Give the results 
```
nmcli nm status 
dmesg | grep -ie firm -ie b43
``` 

Please put the results between the brackets **[noparse]```
the results here
```[/noparse]** so can be easy to read.

Thanks

---

### Post by pjstock on 2012-10-29
Thanks for sticking with me on this. I appreciate it.

I am not sure the first command completed successfully. The ABORTING line at the end (see below) seems ominous.

But I'll reboot anyway and report

peter@peter-Latitude-D505:~$ sudo apt-get install firmware-b43-installer
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 26 not upgraded.
Need to get 22.4 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/main b43-fwcutter i386 1:015-9 [18.9 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/multiverse firmware-b43-installer all 1:015-9 [3,524 B]
Fetched 22.4 kB in 0s (41.1 kB/s)            
Selecting previously unselected package b43-fwcutter.
(Reading database ... 158232 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
An unsupported BCM4301, BCM4306 or BCM4306/2 device was found.
Use b43legacy firmware (firmware-b43legacy-installer package) instead.
Aborting.

---

### Post by pedro.nariyoshi on 2012-10-29
Try:

sudo apt-get install firmware-b43legacy-installer

This should do it for you. (;

---

### Post by pjstock on 2012-10-29
no luck after this step.

Wireless is not even listed as an option in the Connections (Up/Down Arrows Icon?) dropdown 

I'll now run those additional commands and report.

peter@peter-Latitude-D505:~$ nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         enabled   


peter@peter-Latitude-D505:~$ dmesg | grep -ie firm -ie b43
[    0.201269] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    1.643420] b43-pci-bridge 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   16.836973] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.

---

### Post by NikTh on 2012-10-29
> **pjstock said:**
> 
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
An unsupported BCM4301, BCM4306 or BCM4306/2 device was found.
Use b43legacy firmware (firmware-b43legacy-installer package) instead.
Aborting.

Yes , you will need the b43legacy firmware. 

```
sudo apt-get install firmware-b43legacy-installer
``` 

Thanks

---

### Post by pjstock on 2012-10-29
might xubuntu just be incompatible with this laptop?
if so, and if I were to start from scratch (though I won't give up until you experts tell me this is a lost cause), is there another small-footprint version of Linux (this laptop only has a 20Gb HDD and 7xxMb of RAM) that is kinder to wifi adaptors?

---

### Post by pedro.nariyoshi on 2012-10-29
Have you tried:
sudo apt-get install firmware-b43legacy-installer
?

Your wifi card is not supported by b43, it is supported only by b43-legacy, that's why you need the different package.

Xubuntu, Lubuntu, etc will support your wireless card the same, since the drivers are on the kernel. Lubuntu and Xubuntu should run fine on 768MB RAM (Lubuntu will probably be better though)

You could consider Bodhi Linux, but I think Lubuntu is probably more than enough.

---

### Post by pjstock on 2012-10-29
b43legacy seems to already be installed.
no wifi though.

Peter

peter@peter-Latitude-D505:~$ sudo apt-get install firmware-b43legacy-installer
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43legacy-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.

---

### Post by pedro.nariyoshi on 2012-10-29
Hmm, sorry for not being able to solve your problem yet. See if this helps:
```
sudo rmmod b43
sudo modprobe b43legacy
```If it doesn't work, try this:
```
export FIRMWARE_INSTALL_DIR="/lib/firmware" 
wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta-3.130.20.0.o
```

If continues not to work, try restarting. If it still doesn't work, run the first commands and please copy a copy of:
```
dmesg | tail
```and:
```
lsmod | grep b43
```

Don't lose hope! (:
We will work out something.

---

### Post by NikTh on 2012-10-30
[B][pedro.nariyoshi]("http://ubuntuforums.org/member.php?u=1088182")

We blacklisted b43legacy and force-load b43 , see post #14. [/B]

[pjstock]("http://ubuntuforums.org/member.php?u=782742")

To undo this , follow these steps 

give this command first 
```
sudo sed 's/blacklist b43legacy//' -i /etc/modprobe.d/blacklist.conf
```and then 

```
sudo sed 's/b43//' -i  /etc/modules
```Then reboot.

---

### Post by pjstock on 2012-10-30
Hmmm, I (maybe foolishly) re-ran the command:

sudo apt-get install firmware-b43legacy-installer

and (maybe unfortunately) afterwards I did the updates/upgrades proposed by Update Manager.

and now it seems completely fouled up.
On reboot, Xubuntu starts but then after the "Xubuntu" screen shows it jumps into some code and then ends on a "Will Halt" and dies.

Is there anyway to recover from this?
Or should I restart by reinstalling 11.10?

sorry if I messed things up.

---

### Post by pedro.nariyoshi on 2012-10-30
> **NikTh said:**
> [B][pedro.nariyoshi]("http://ubuntuforums.org/member.php?u=1088182")
We blacklisted b43legacy and force-load b43 , see post #14. [/B]

Hey man, no need for caps here. I'm sorry I didn't see #14.

> Is there anyway to recover from this?
Or should I restart by reinstalling 11.10?
Try booting in recovery mode and checking for more updates. Do you have "proposed" updates enabled on your system?

---

### Post by NikTh on 2012-10-30
> **pedro.nariyoshi said:**
> Hey man, no need for caps here.


No caps. I'm not yelling. 
Is just bold so others can see as well what we've done in #14th post. 
:)

@pjstock you can try again the procedure described in #3rd post and attach the new netinfo.txt , so we will see if anything changed. 

Thanks

---

### Post by pjstock on 2012-10-30
I'll do these steps tonight on my return home from work.

But I really must commend you all on your diligence, persistence and patience. The support here is extraordinary.
Thank you all.

Peter

when I choose (recovery mode) and the Grub Update, it eventually fails again "Will Now Halt."

Hmmm, when I boot I get messages like

could not write bytes: Broken Pipe
Stoping aave kernel mesasges

and then finally.

Will now Halt


when I try Safe Mode I get the choices of:
Ubuntu, with linux 3.2.0-32-generic 
Ubuntu, with linux 3.2.0-32-generic (recovery mode)
Previous LInux Versions
Memory Test (memtest86+)
Memory Test (memtest86+. serial console 115200)

which do I choose?
Both the recovery modes take me to another list of choices:

Resume
clean
dpkg
fsck
grub
metwork
root
system-summary

which do I choose at this point?

---

### Post by NikTh on 2012-10-31
Hi ,
try to choose the option "Dpkg - Repair Broken Packages" . This option listed at Recovery Mode menu. 
It will run the update-upgrade process too. 

This message > could not write bytes: Broken Pipe may mean a lot of things. 

Broken filesystem , hardware problem , kernel problem ... etc. I don't know how many problems have been solved with this message "inside them". 
Thanks

---

### Post by pedro.nariyoshi on 2012-10-31
> **NikTh said:**
> No caps. I'm not yelling. 
Thanks
No hard feelings (:
Peace :)

[QUOTE=pjstock]which do I choose?[/QUOTE]
I would say that if DPKG doesn't work, try fsck.

I'll try to explain what each option does: (experts, correct me if i'm wrong)

[LIST]
[*]Resume: does nothing, tries to "resume boot"
[*] Clean: cleans some old packages files (tries to make space in the hdd)
[*] dpkg: configures any packages that haven't been configured, updates and upgrades
[*] fsck: stands for filesystem check, similar to MS's "scandisk", tries to fix any errors in your harddrive
[*] grub: tries to update your grub (if you uninstalled a kernel and installed another one, but restarted before updating grub)
[*] network: similar to "safe mode with networking", will give you root access with dhcp-configured net
[*] root: similar to previous, but without configuring the network (you may configure it yourself - only for the brave :P)
[*] system-summary: gives a summary of your system (CPU, RAM, HDD etc)
[/LIST]

---

### Post by pjstock on 2012-11-06
> **NikTh said:**
> Hi ,
try to choose the option "Dpkg - Repair Broken Packages" . This option listed at Recovery Mode menu. 
It will run the update-upgrade process too. 


Excellent. I am back up and running. Thank you.

Now, back to our problem at hand - wifi.
what are the next steps? (I kind of lost the thread there while it was crashing.)

---

### Post by cmcanulty on 2012-11-06
I really like this link and works for a lot of people all copy and paste
[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure]("https://help.ubuntu.com/community/WirelessTroubleshootingProcedure")

---

### Post by pjstock on 2012-11-06
> **NikTh said:**
> [B][pedro.nariyoshi]("http://ubuntuforums.org/member.php?u=1088182")

We blacklisted b43legacy and force-load b43 , see post #14. [/B]

[pjstock]("http://ubuntuforums.org/member.php?u=782742")

To undo this , follow these steps 

give this command first 
```
sudo sed 's/blacklist b43legacy//' -i /etc/modprobe.d/blacklist.conf
```and then 

```
sudo sed 's/b43//' -i  /etc/modules
```Then reboot.

WOAH! Wifi's working on reboot!
I won't claim to understand what you all had me do, but I tip my hat to you for your excellent assistance.
Thank you!

Peter

Sigh,

I should probably open a new thread as this is likely a new problem, but how can I be out of disk space on a fresh install?

I thought Xubuntu was a small footprint version of Linux and this laptop only has a 20Gb HDD, so I hoped it would be a good choice.

Now, at the end of this wifi exercise, I find myself with 0 Free Space and the 18.4Gb used up.

For simplicity I did not dual partition this thing (as that has left me struggling for space in the past too.)

This is a fresh install of 11.10 first, then upgraded to 12.04. Nothing else has been installed and there is no data (music, etc.) on this at all.

What have I done wrong?

Peter

---

### Post by NikTh on 2012-11-06
Yes , you said well . Open a new thread about your new problem. 
Mark this thread as solved ==> [look here if you don't know how](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) 
and open a new thread. 

I hope we can solve your new problem easier and faster. Do not forget to give the results of bellow commands (to the new opened Thread , not here)
```
df -Th
sudo parted -l 
sudo fdisk -l
mount
sudo du -h --max-depth=1 / | grep '[0-9]G\>'
sudo find / -name '*' -size +1G
```
above commands will provide usefull info for your problem to be solved faster.

Also do not forget to put the results between the brackets ==>[noparse]```
the results here
```[/noparse]<== to be easier for someone to read them.

Thanks

---

### Post by pjstock on 2012-11-06
> **NikTh said:**
> Yes , you said well . Open a new thread about your new problem. 
Mark this thread as solved ==> [look here if you don't know how](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) 
and open a new thread. 

I hope we can solve your new problem easier and faster. Do not forget to give the results of bellow commands (to the new opened Thread , not here)
```
df -Th
sudo parted -l 
sudo fdisk -l
mount
sudo du -h --max-depth=1 / | grep '[0-9]G\>'
sudo find / -name '*' -size +1G
```
above commands will provide usefull info for your problem to be solved faster.

Also do not forget to put the results between the brackets ==>[noparse]```
the results here
```[/noparse]<== to be easier for someone to read them.

Thanks

Thank you.
I'd looked around for an obvious SOLVED marker, but didn't see one.
now I know how.
cheers'
Peter

---

