---
title: "HP Compaq nx6125: Cannot get the internet via wired or wireless connection"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by jleb on 2014-04-08
Hello

As support for Windows XP has expired I am trialling using Ubuntu 12.04 on my HP Compaq nx6125 but cannot get either a wired or wireless connection (has inbuilt wireless and both wired and wireless work fine on Windows XP). I have tried manually configuring with a static address as per the instructions on pages 41-42 in the "Getting Started with Ubuntu 12.04 - Second Edition" found online (as found on [http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)) for a wired connection but it's not working.  Entering my SSID and password for the wireless connection yields no results either. I am pretty much computer illiterate so would appreciate having my hand held with any assistance. 

Many thanks

---

### Post by varunendra on 2014-04-10
Welcome to the forums jleb!

Please open a terminal (Ctrl-Alt-T) and post back the output of following commands -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mörgæs on 2014-04-10
An nx6125 is a little to the weak side for Ubuntu. I suggest X/Lubuntu 13.10 or 14.04.

---

### Post by jleb on 2014-04-11
Thank you very much, Varunendra and Mörgæs! I'll see how I go with the Ubuntu trial, Mörgæs, just for the moment to get a feel, as I am absolutely new to the whole process and don't want to confuse things.

Varunendra, I trust that the below is what you need - just getting this information was a great trial for me, as I've just had a crash-course searching online as to how to create a file in Ubuntu, having to transfer it to a USB (as I am undergoing a trial only at this stage with Ubuntu and, of course, can't access the internet) then downloading Notepad++ to make this text presentable! So here goes, and thanks again:

```

Module                  Size  Used by
dm_crypt               22555  0 
snd_atiixp_modem       18785  0 
snd_atiixp             19452  2 
snd_ac97_codec        110295  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                94597  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
b43                   369639  0 
snd_seq_midi           13132  0 
joydev                 17329  0 
snd_rawmidi            25157  1 snd_seq_midi
hp_wmi                 17834  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              534884  1 b43
sparse_keymap          13658  1 hp_wmi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 55837  0 
snd_timer              28930  2 snd_pcm,snd_seq
dm_multipath           22754  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
scsi_dh                14449  1 dm_multipath
tifm_7xx1              13202  0 
cfg80211              416271  2 b43,mac80211
yenta_socket           44614  0 
tifm_core              15040  1 tifm_7xx1
snd                    61270  13 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18495  1 yenta_socket
psmouse                92648  0 
pcmcia_core            22396  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
bcma                   41297  1 b43
serio_raw              13189  0 
i2c_piix4              17843  0 
k8temp                 12912  0 
snd_page_alloc         18398  3 snd_atiixp_modem,snd_atiixp,snd_pcm
shpchp                 32265  0 
mac_hid                13077  0 
parport_pc             32114  1 
rfcomm                 59026  0 
bnep                   19210  2 
ppdev                  17423  0 
bluetooth             341971  10 rfcomm,bnep
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
squashfs               46690  1 
overlayfs              27532  1 
nls_iso8859_1          12617  1 
dm_raid45              76513  0 
dm_mirror              21948  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18164  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 839423  0 
raid6_pq               97455  1 btrfs
xor                    26221  2 dm_raid45,btrfs
zlib_deflate           26622  1 btrfs
pata_acpi              12886  0 
radeon               1344679  3 
usb_storage            48631  1 
firewire_ohci          36064  0 
ttm                    76692  1 radeon
drm_kms_helper         47306  1 radeon
tg3                   155583  0 
firewire_core          62303  1 firewire_ohci
sdhci_pci              18588  0 
drm                   247722  5 radeon,ttm,drm_kms_helper
sdhci                  37958  1 sdhci_pci
ssb                    56410  1 b43
ptp                    18199  1 tg3
crc_itu_t              12627  1 firewire_core
pps_core               18515  1 ptp
i2c_algo_bit           13316  1 radeon
pata_atiixp            13058  0 
ati_agp                13242  0 
wmi                    18744  1 hp_wmi
video                  19046  0

```

---

### Post by varunendra on 2014-04-11
> **jleb said:**
> just getting this information was a great trial for me, as I've just had a crash-course searching online as to how to create a file in Ubuntu, having to transfer it to a USB (as I am undergoing a trial only at this stage with Ubuntu and, of course, can't access the internet) then downloading Notepad++ to make this text presentable!
Sorry, I should have kept that in mind and made it easier for you.

Based partly on the output you posted (not all I asked, but contains a hint), and partly a guess, please try this :

Download the "linux-firmware-nonfree" package from this link : [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Copy the downloaded file onto you Ubuntu Desktop > Open a terminal (Ctrl-Alt-T) > Run the following command :
```
[s]sudo apt-get install Desktop/linux-firmware*.deb[/s]
sudo dpkg -i Desktop/linux-firmware*.deb
```
*[COLOR="#FF0000"](EDIT: Corrected the command)[/COLOR]*

Then run the following set of commands to reload the driver -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```

Does this make your wifi active?

Please remember that if you are using a "Live Session" (Ubuntu running directly from a CD/DVD), then any changes you make during a running session will be lost on next boot. In that case, you will have to install the above firmware file everytime you boot. However, if it is a "Live Persistent USB" that you are booting from, the change will be saved and you won't have to install the firmware again.

If installing the above firmware package doesn't help, we'll need to see another output asked before. Here is how you can redirect the outputs directly to a simple text file -
```
lspci -nnk | grep -iA2 net **[COLOR="#FF0000"]>[/COLOR] Desktop/lspci.txt**
```

As you can notice, I have added a "Greater than" sign (>) after the main command. It redirects the output to a file mentioned after it. Here, it is **Desktop/lspci.txt**, means a file named "lspci.txt" on the Desktop.

You can simply attach this file in your next post.

---

### Post by jleb on 2014-04-11
Again, thank you for all your assistance, Varunendra.

Unfortunately, it didn't work. I did notice that after running the first command the result was "E: Unable to locate package Desktop" even though I had definitely copied the file to the Ubuntu desktop as per your instructions.

You wishing to see another output that was asked before  - I am sorry I did not supply this in the first place, in my naivete I thought the final output was the only one required -  strangely did not produce the desired "lspci.txt" file. I have instead taken the liberty of producing the full output as I should have initially supplied.

Thanks once more for all your help.

```

ubuntu@ubuntu:~$ uname -mr
3.11.0-15-generic i686
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
    Subsystem: Hewlett-Packard Company MX6125 [103c:308b]
    Kernel driver in use: tg3
--
02:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1356]
    Kernel driver in use: b43-pci-bridge
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
b43                   369639  0 
mac80211              534884  1 b43
cfg80211              416271  2 b43,mac80211
ssb                    56410  1 b43
bcma                   41297  1 b43
dm_crypt               22555  0 
snd_atiixp             19452  2 
snd_atiixp_modem       18785  0 
snd_ac97_codec        110295  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                94597  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
joydev                 17329  0 
snd_seq_midi           13132  0 
hp_wmi                 17834  0 
snd_rawmidi            25157  1 snd_seq_midi
sparse_keymap          13658  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 55837  0 
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
dm_multipath           22754  0 
scsi_dh                14449  1 dm_multipath
snd_timer              28930  2 snd_pcm,snd_seq
tifm_7xx1              13202  0 
yenta_socket           44614  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                92648  0 
tifm_core              15040  1 tifm_7xx1
serio_raw              13189  0 
pcmcia_rsrc            18495  1 yenta_socket
k8temp                 12912  0 
snd                    61270  13 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            22396  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         18398  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4              17843  0 
mac_hid                13077  0 
shpchp                 32265  0 
bnep                   19210  2 
rfcomm                 59026  0 
parport_pc             32114  1 
bluetooth             341971  10 bnep,rfcomm
ppdev                  17423  0 
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
squashfs               46690  1 
overlayfs              27532  1 
nls_iso8859_1          12617  1 
dm_raid45              76513  0 
dm_mirror              21948  0 
dm_region_hash         16100  1 dm_mirror
dm_log                 18164  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 839423  0 
raid6_pq               97455  1 btrfs
xor                    26221  2 dm_raid45,btrfs
zlib_deflate           26622  1 btrfs
pata_acpi              12886  0 
radeon               1344679  3 
usb_storage            48631  1 
ttm                    76692  1 radeon
firewire_ohci          36064  0 
drm_kms_helper         47306  1 radeon
tg3                   155583  0 
firewire_core          62303  1 firewire_ohci
drm                   247722  5 radeon,ttm,drm_kms_helper
ptp                    18199  1 tg3
sdhci_pci              18588  0 
i2c_algo_bit           13316  1 radeon
pps_core               18515  1 ptp
sdhci                  37958  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_atiixp            13058  1 
wmi                    18744  1 hp_wmi
ati_agp                13242  0 
video                  19046  0

```

---

### Post by varunendra on 2014-04-11
> **jleb said:**
> I did notice that after running the first command the result was "E: Unable to locate package Desktop"....

Oops! Another mistake on my part!

The command had to be 'dpkg -i', not 'apt-get install' :redface:

Please use the corrected command after copying the file on the desktop -
```
sudo dpkg -i Desktop/linux-firmware*.deb
```

---

### Post by jleb on 2014-04-12
Varunendra, for the first time when I click on the Network Manager icon at the top of the screen 'Enable Wireless' is listed with a tick next to it - but I still am unable to connect. Which means I am not entering the correct details?

Clicking on Edit Connections brings up the Network Connections page. I then I click on the Wireless Tab, which is empty. I then click on 'Add', which brings up a 'Editing Wireless connection 1' page, which is defaulted to show the Wireless Tab. I enter our SSID (which we had renamed) and leave the Mode as 'Infrastructure'. I then click on the Wireless Security tab, choose for Security 'WPA & WPA2 Personal" from the drop-down menu (on the basis that this is what we do on Windows), enter our Password, then click on Save. Still no wireless connection.

I have also tried the suggestion by Rickford Grant on page 54 in his "Ubuntu for Non-Geeks" I found online, which is to go through the process for setting up an Ethernet connection for Providers not Utilizing DHCP to manually input our connection settings but clicking on Wireless Connection instead of Wired Connection i.e. I follow the process under the "Manual Configuration with Static Address" found on page 41-42 in the "Working with Ubuntu" guide also found online, which is to click on the IPV4 Settings tab in the Editing Wired connection 1 tab (but here it is the Wireless connection 1 tab), changing the method to "Manual", and in turn entering our IP address, our Network Mask, our DNS server address then clicking save. Doesn't work for either a wired or wireless connection.

In case it's of any use here's the output after following your amended instructions:

```

ubuntu@ubuntu:~$ sudo dpkg -i Desktop/linux-firmware*.deb
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 150115 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.14ubuntu1_all.deb) ...
Setting up linux-firmware-nonfree (1.14ubuntu1) ...
ubuntu@ubuntu:~$ sudo modprobe -rv b43
rmmod /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/3.11.0-15-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.11.0-15-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/3.11.0-15-generic/kernel/drivers/ssb/ssb.ko
rmmod /lib/modules/3.11.0-15-generic/kernel/drivers/bcma/bcma.ko
ubuntu@ubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/b43/b43.ko 
ubuntu@ubuntu:~$ 

```

---

### Post by varunendra on 2014-04-12
If I remember correctly, there is a known bug with the combination of this driver + the particular card that you have. If it is the same bug due to which you are not able to automatically detect available network (you shouldn't need all those manual steps you tried), the fix/workaround would be a simple one.

To verify if it is what I mentioned above, please run the following command in a terminal *(it is highly recommended to 'Undo' all the additional manual changes beforehand that you mentioned in your post above)* -
```
sudo iwlist scan
```
..while the wireless seems to be enabled. Do you see available network(s) in the output? If yes, can you see them in Network Manager's menu as well and connect to them?

If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by jleb on 2014-04-12
Varunendra, that did it! I can't thank you enough! Now, I am too  exhausted after all this to have a good play on Ubuntu but I will next  time I log on. Thank you again!

---

### Post by varunendra on 2014-04-12
Glad it worked. :)

To make it automatic so that you don't have to run the command manually after each boot, add the command to your **/etc/rc.local** file. A quick and easy way to do that is the following command -
```
sudo sed -i '/^exit 0/i iwlist scan' /etc/rc.local
```

It will insert the command "iwlist scan" just before the line "exit 0" in the file (the last line in that file must be "exit 0", the above command takes care of it).

You can run the above code without the "-i" option to see the result on the terminal without actually modifying the file. Running it with the "-i" option will actually modify the file instead of showing the result on the terminal.

---

### Post by squakie on 2014-04-13
> **jleb said:**
> Varunendra, that did it! I can't thank you enough! Now, I am too  exhausted after all this to have a good play on Ubuntu but I will next  time I log on. Thank you again!

Just remember the thing Varunendra posted earlier about needing to reload this information if your are running off a liveDVD or don't have persistence on a USB flash if that is what you are using.  So if you mean "reboot the live media" when you say "next time I log on" then be sure to re-read that post.

---

### Post by jleb on 2014-04-13
Thanks, Squakie, I've remembered to do that - I am using a USB flash (much smoother than a liveDVD, I've found). Sometimes I have to enter the code a second time for my wireless connection to show, though...Maybe it's a matter of waiting a short while for the connection to be made. 

Varunendra, I take it that I use this code after I install Ubuntu? Right now I'm still playing around with it on live trial.

I have to say, though, that after being on Ubuntu for a couple of hours the cursor has been starting to move erratically and the screen has frozen, requiring me to power-off and re-boot. This no doubt is due to my memory being almost full. I also realise that Ubuntu will work much more smoothly once I have installed it. As support for Windows XP has been withdrawn I will be erasing the disc before installing Ubuntu, which will free up a lot of memory. However, Mörgæs post below has got me thinking as to whether something lighter such as X/Lubuntu (13.10 or 14.04) might be preferable. My concern is that I am brand new to this world and Ubuntu seems to have the most material at hand to assist me - I understand this might best be covered by beginning a new post, which I will commence.

Thanks again for all the help! It's very encouraging for someone not computer-savvy stepping into Linux for the first time.

---

### Post by varunendra on 2014-04-14
> **jleb said:**
> Varunendra, I take it that I use this code after I install Ubuntu? Right now I'm still playing around with it on live trial.

If your Live USB has been created with persistence, you won't need repeat the commands everytime you boot, and the last suggestion about /etc/rc.local file *should* also work just as in installed mode.

To get best suggestions about which version of Ubuntu you should try, posting your hardware details may be a good idea. It can be a full output of "sudo lshw" command, or just these -

* How much memory (RAM) your system has.
* Which CPU model (its frequency, cache, no. of cores if you know them, else we can look it up from the model name)
* How much disk space.
* Which graphics card, if any other than the onboard one (or embedded one in CPU).

---

### Post by jleb on 2014-04-14
Thanks, Varunendra - I've created a new thread asking for suggestions with my laptop model in the heading and with details of its hardware system. FYI so far Lubuntu seems to be the most favoured reply. 

Thanks again for easing my way.

---

