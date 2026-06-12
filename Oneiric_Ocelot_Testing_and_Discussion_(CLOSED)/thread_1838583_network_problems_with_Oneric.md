---
title: "network problems with Oneric"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by richlyn9 on 2011-09-03
I had installed Oneric Alpha 1 which has been updated after the Beta release. I was able to connect to my mobile gprs tethering my phone but now am unable to(no error though) . I am able to connect using the same phone from Lucid through which i am posting this.

Looks like the update has broke some package. But now that i cannot connect its a kinda catch 22 situation....

Any ideas? whats wrong what package needs be fixed?

---

### Post by cariboo on 2011-09-04
Could you post the output of:

```
dmesg | tail -n15
```

When you try to connect to your cell phone?

---

### Post by vpharry on 2011-09-04
> **cariboo907 said:**
> Could you post the output of:

```
dmesg | tail -n15
```When you try to connect to your cell phone?
Same problem here. When I try 2 connect it says disconnected. I typed the code in terminal. Heres the output:-
varun@Varun:~$ dmesg | tail -n15
[   43.786352] init: plymouth-stop pre-start process (1566) terminated with status 1
[   61.552294] r8169 0000:02:00.0: eth0: link up
[   61.552545] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   67.431204] r8169 0000:02:00.0: eth0: link down
[   69.081129] r8169 0000:02:00.0: eth0: link up
[   72.210016] eth0: no IPv6 routers present
[   95.800006] eth0: no IPv6 routers present
[  255.820028] usb 1-5: new high speed USB device number 2 using ehci_hcd
[  255.880306] hub 1-0:1.0: unable to enumerate USB device on port 5
[  258.270025] usb 1-5: new high speed USB device number 3 using ehci_hcd
[  258.703060] cdc_acm 1-5:3.1: ttyACM0: USB ACM device
[  258.706160] usbcore: registered new interface driver cdc_acm
[  258.706163] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[  440.820013] eth0: no IPv6 routers present
[  513.770008] eth0: no IPv6 routers present

---

### Post by richlyn9 on 2011-09-04
Yeah...just says disconnected....

heres the output

richlyn@richlyn-oneric:~$ dmesg | tail -n15
[   65.670727] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[   65.693197] usb 3-1: bad CDC descriptors
[   65.698111] usbcore: registered new interface driver rndis_host
[   65.702707] NET: Registered protocol family 35
[   65.710517] usbcore: registered new interface driver cdc_phonet
[   65.712980] cfg80211: Calling CRDA to update world regulatory domain
[   65.731685] usb 3-1: bad CDC descriptors
[   65.735748] usbcore: registered new interface driver rndis_wlan
[   65.743416] cfg80211: World regulatory domain updated:
[   65.743422] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   65.743425] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.743428] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.743430] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.743433] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.743436] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


I deleted the connection and created a new one...still same issue....


@cariboo97: If you mean at what stage i connect my cell phone? After i have booted in to the system and my desktop shows up thats when i tether my phone.

---

### Post by karmila on 2011-09-04
I have the same problem.

At fresh OO beta install  it works great. But latest update, which is include network-manager broke something. 
My modem is still detected but it just won't connect.

I'm using a usb cdma mobile broadband.

Now i'm using wvdial to connect to internet.

---

### Post by richlyn9 on 2011-09-04
Looks like a bug to me ...

---

### Post by tajreed on 2011-09-04
Same here. I did a clean reinstall-problem solved, then when I did updates I didn't allow those four network updates to update. There must be a bug in them.

---

### Post by vpharry on 2011-09-04
But my problem is not solved...... Guys plz help me.... Wvdial not workin for me.... I dont think its a problem with ubuntu but with gnome 3. I tried the gnome shell without unity but in that too there was the same problem.

---

### Post by cariboo on 2011-09-04
According to richlyn9's dmesg output the device driver is loaded, and it is working, so I'd assume the problem is with network-manager. If you have the previous version of network-manager in /var/cache/apt/archives, you can remove the current version and re-install the previous version.

**Edit:** It looks like the previous version is: network-manager_0.9.0-0ubuntu**1**_amd64.deb, whereas the new version is network-manager_0.9.0-0ubuntu**2**_amd64.deb

---

### Post by walt.smith1960 on 2011-09-04
If it works with fresh install and network manager update appears to be the culprit, could you do a fresh install and make sure you can connect.  If you can connect, then go to synaptic and  mark network manager to not be upgraded?  The other thought would be to roll network manager back to the version that works but I don't know how to do that.  Possibly add the CD to software sources, delete network manager then reinstall the CD version.  I'm just guessing here, maybe somebody more knowledgeable can chip in.

Edit: Cariboo907 appears to have the solution.

---

### Post by vpharry on 2011-09-04
Well for me the problem was from the beginning..... From when i installed beta 1. So obviously I wont be having the previous version in cache. From where can I download the older version?

---

### Post by richlyn9 on 2011-09-04
> **cariboo907 said:**
>  If you have the previous version of network-manager in /var/cache/apt/archives, you can remove the current version and re-install the previous version.

**Edit:** It looks like the previous version is: network-manager_0.9.0-0ubuntu**1**_amd64.deb, whereas the new version is network-manager_0.9.0-0ubuntu**2**_amd64.deb

I dont have any previous versions in the archives.
But can i get the deb from [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)  or possibly [http://packages.ubuntu.com/oneiric/comm/](http://packages.ubuntu.com/oneiric/comm/) and install it from there?

any ideas?

---

### Post by richlyn9 on 2011-09-04
I have found the mentioned .deb file  in [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/) (hoping i am looking in the right place...if not someone please direct me) which is updated 02-Sep-2011.
need to know when any of you ran the update which caused this issue.
So that we can decide if this update is bugged or not.....

---

### Post by richlyn9 on 2011-09-04
BTY i remember that the update included "gir1.2-networkmanager" whse package gir1.2-networkmanager-1.0_0.9.0-0ubuntu2_amd64.deb was updated 02-Sep-2011 16:04 at [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/)  i wonder if thats the culprit rather than the one mentioned earlier.

I tried to manually report a bug but wasn't able to at [https://bugs.launchpad.net](https://bugs.launchpad.net) however Bug no:841059 and 841790 look like the ones we are facing here. so far its not fixed so keep tracking the bugs mentioned above meanwhile if someone can find the earlier versions of the package mentioned above kindly share

---

### Post by cariboo on 2011-09-04
Just for your information, you can't manually create bugs on Launchpad. to report bugs use:

```
ubuntu-bug <package-name>
```

either from a terminal, or use alt-F2

---

### Post by richlyn9 on 2011-09-04
> **richlyn9 said:**
> I have found the mentioned .deb file  in [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/) (hoping i am looking in the right place...if not someone please direct me) which is updated 02-Sep-2011.
need to know when any of you ran the update which caused this issue.
So that we can decide if this update is bugged or not.....

I got this .deb from the ubuntu archive and installed it from synaptic..
Its a no go..
problem still persists. guess we need to wait till a fix is in place

---

### Post by CaymanPirate on 2011-09-05
Greetings,

I've encountered this as well... here is a temporary fix... from the last comment on my bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/840082/comments/10](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/840082/comments/10)

I rolled back network-manager to network-manager_0.9.0-0ubuntu1_amd64.deb; and internet connectivity via Huawei Broadband Modem is restored!

$ sudo dpkg -i network-manager_0.9.0-0ubuntu1_amd64.deb


 dpkg: warning: downgrading network-manager from 0.9.0-0ubuntu2 to 0.9.0-0ubuntu1.
(Reading database ... 144119 files and directories currently installed.)
Preparing to replace network-manager 0.9.0-0ubuntu2 (using network-manager_0.9.0-0ubuntu1_amd64.deb) ...
Unpacking replacement network-manager ...
Setting up network-manager (0.9.0-0ubuntu1) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db .

Regards,

CaymanPirate

---

### Post by Nordicruler on 2011-09-06
Anyone find a solution for this that actually work?

---

### Post by Larkspur on 2011-09-06
> **Nordicruler said:**
> Anyone find a solution for this that actually work?

Apart from CaymanPirate's method or reinstalling and not upgrading Network-Manager, I'm afraid not.  

Someone's opened a [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/841874") for this though, so if everyone who has this bug clicks "affects me too," it'll help it get noticed quicker.

---

### Post by karmila on 2011-09-06
> **Larkspur said:**
> Apart from CaymanPirate's method or reinstalling and not upgrading Network-Manager, I'm afraid not.  

Someone's opened a [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/841874") for this though, so if everyone who has this bug clicks "affects me too," it'll help it get noticed quicker.

I clicked it.

---

### Post by richlyn9 on 2011-09-07
I tried CaymanPirate's solution but that did not work for me.

---

### Post by Nordicruler on 2011-09-07
Okay, how do i update everything except network manager?

---

### Post by Larkspur on 2011-09-07
> **Nordicruler said:**
> Okay, how do i update everything except network manager?

In Update Manager, deselect the network-manager updates before you install the rest.  I'm sure there's a CLI method, but I don't know it.

Does anyone know what will happen if a fix is released?  Will I be able to choose that update, or will I have to install the bugged one beforehand?

---

### Post by cariboo on 2011-09-07
Probably the easiest way to lock the version is in synaptic, go to Package, then select lock version. The only problem then is that you have to use synaptic to do your updates.

---

### Post by CaymanPirate on 2011-09-08
Hi,

I was able to apply this temporary fix on both architectures, after a Partial Upgrade in Alpha 3(i386) and an update in Beta. 1 (amd64). The complete process to the discovery of the temporary fix has been documented here...[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/840082](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/840082) (as I originally thought it had something to do with the Broadband modem).

The "Force Version" in Synaptic on Alpha proved unsuccessful as there were no other versions listed for network-manager; and it seems that Beta no longer carries Synaptic. It's all Software Center now (and that didn't work either, install option not available).

I was able to download the previous version and use dpkg to which:

dpkg: warning:** downgrading** network-manager from 0.9.0-0ubuntu2 to 0.9.0-0ubuntu1.

I restarted and I was Golden.

after this however, I decided on a clean install of Beta (AMD64), however neglecting to update the following packages (until a fix is released):

network-manager (0.9.0-0ubuntu2)
network-manager-gnome

Hope this helps...

---

### Post by cariboo on 2011-09-08
Synaptic is no longer installed by default, but I personally prefer it over the Software Center. When running a testing version synaptic is one of the tools, that should be in your toolbox.

---

### Post by CaymanPirate on 2011-09-08
> **cariboo907 said:**
> Synaptic is no longer installed by default, but I personally prefer it over the Software Center. When running a testing version synaptic is one of the tools, that should be in your toolbox.
Thanks. Duly noted.

---

### Post by richlyn9 on 2011-09-08
> **CaymanPirate said:**
> Hi,

I was able to apply this temporary fix on both architectures, after a Partial Upgrade in Alpha 3(i386) and an update in Beta. 1 (amd64). The complete process to the discovery of the temporary fix has been documented here...[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/840082](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/840082) (as I originally thought it had something to do with the Broadband modem).

The "Force Version" in Synaptic on Alpha proved unsuccessful as there were no other versions listed for network-manager; and it seems that Beta no longer carries Synaptic. It's all Software Center now (and that didn't work either, install option not available).

I was able to download the previous version and use dpkg to which:

dpkg: warning:** downgrading** network-manager from 0.9.0-0ubuntu2 to 0.9.0-0ubuntu1.

I restarted and I was Golden.

after this however, I decided on a clean install of Beta (AMD64), however neglecting to update the following packages (until a fix is released):

network-manager (0.9.0-0ubuntu2)
network-manager-gnome

Hope this helps...


I am trying to download the previous version(0.9.0-0ubuntu1.)from [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/) but seems that old version is not there. 

may i know from where to download the previous version.

---

### Post by tekstr1der on 2011-09-08
> **richlyn9 said:**
> ...may i know from where to download the previous version.

Here's all the trunk builds for Oneiric thus far including the version you seek. Take your pick.

[https://launchpad.net/ubuntu/oneiric/+source/network-manager](https://launchpad.net/ubuntu/oneiric/+source/network-manager)

---

### Post by tekstr1der on 2011-09-08
> **Nordicruler said:**
> Okay, how do i update everything except network manager?

Cariboo's way is great for synaptic:

> **cariboo907 said:**
> Probably the easiest way to lock the version is in synaptic, go to Package, then select lock version. The only problem then is that you have to use synaptic to do your updates.

To keep a package from updating in synaptic, apt-get, aptitude AND the update manager, you'll additionally need to hold the package with dpkg as well:

```
echo "network-manager hold" | sudo dpkg --set-selections
```

---

### Post by richlyn9 on 2011-09-09
I have downloaded the older ver from [https://launchpad.net/~ricotz/+archive/testing/+sourcepub/1910195/+listing-archive-extra](https://launchpad.net/~ricotz/+archive/testing/+sourcepub/1910195/+listing-archive-extra) and tried to do "upload downloaded script" in Synaptic, but synaptic does not recognise the older version and gives no option to install it. Futhermore i think i may need to have a debian installed forst coz its seems a debian installer is not there by default in Oneric.

---

### Post by richlyn9 on 2011-09-09
> **CaymanPirate said:**
> Hi,

I was able to download the previous version and use dpkg to which:

dpkg: warning:** downgrading** network-manager from 0.9.0-0ubuntu2 to 0.9.0-0ubuntu1.

I restarted and I was Golden.

network-manager (0.9.0-0ubuntu2)
network-manager-gnome



How do you install the downloaded previous version using dpkg and do i also need to download "network-manager-gnome"

---

### Post by cariboo on 2011-09-09
> **richlyn9 said:**
> How do you install the downloaded previous version using dpkg and do i also need to download "network-manager-gnome"

Remove the current version of network-manager:

```
sudo apt-get purge network-manager
```

Then cd into the directory  where the ntwork-manger is stored, then and:

```
sudo dpkg -i network-manager_0.9.0-0ubuntu1*.deb
```

**Note** there was an update to network-manager_0.9.0-0ubuntu3 on Sept 8, so if you have access to a wired connection to install the latest version, you may be ok.

---

### Post by karmila on 2011-09-09
Hi guys, today update solve the problem. My network-manager is working :D

---

### Post by richlyn9 on 2011-09-10
I downloaded the 8th Sept network-manager_0.9.0-0ubuntu3 updated Deb and saved it on my desktop(had it first on my home folder but it gave an error after which i moved it to my desktop).

then ran this....


richlyn@richlyn-oneric:~$ sudo apt-get purge network-manager
[sudo] password for richlyn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil50 libavcodec52
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  network-manager*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3,822 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 181563 files and directories currently installed.)
Removing network-manager ...
network-manager stop/waiting
Purging configuration files for network-manager ...
dpkg: warning: while removing network-manager, directory '/var/lib/NetworkManager' not empty so not removed.
dpkg: warning: while removing network-manager, directory '/etc/NetworkManager/system-connections' not empty so not removed.
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
richlyn@richlyn-oneric:~$ cd ~
richlyn@richlyn-oneric:~$ cd /home
richlyn@richlyn-oneric:/home$ sudo dpkg -i network-manager_0.9.0-0ubuntu3_amd64.deb
dpkg: error processing network-manager_0.9.0-0ubuntu3_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 network-manager_0.9.0-0ubuntu3_amd64.deb  
richlyn@richlyn-oneric:/home$ cd /home/richlyn/Desktop/
richlyn@richlyn-oneric:~/Desktop$ sudo dpkg -i network-manager_0.9.0-0ubuntu3*.deb
Selecting previously deselected package network-manager.
(Reading database ... 181459 files and directories currently installed.)
Unpacking network-manager (from network-manager_0.9.0-0ubuntu3_amd64.deb) ...
Setting up network-manager (0.9.0-0ubuntu3) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
richlyn@richlyn-oneric:~/Desktop$ dmesg | tail -n15
[  468.875227] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[  468.887001] usb 3-1: bad CDC descriptors
[  468.887030] usbcore: registered new interface driver rndis_host
[  468.909238] cfg80211: Calling CRDA to update world regulatory domain
[  468.937185] usb 3-1: bad CDC descriptors
[  468.937280] usbcore: registered new interface driver rndis_wlan
[  469.010721] cfg80211: World regulatory domain updated:
[  469.010726] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  469.010730] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  469.010732] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  469.010735] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  469.010738] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  469.010740] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  525.135860] show_signal_msg: 18 callbacks suppressed
[  525.135866] zeitgeist-daemo[1313]: segfault at 2 ip 00007f8066120bed sp 00007fff660cad30 error 6 in libxapian.so.22.3.0[7f806603e000+1e6000]
richlyn@richlyn-oneric:~/Desktop$ 

Rebooted and  ran dmesg


richlyn@richlyn-oneric:~$ dmesg | tail -n15
[   95.006464] usbcore: registered new interface driver cdc_acm
[   95.006468] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[   95.053612] usbcore: registered new interface driver cdc_ether
[   95.061768] usb 3-1: bad CDC descriptors
[   95.061799] usbcore: registered new interface driver rndis_host
[   95.082484] cfg80211: Calling CRDA to update world regulatory domain
[   95.111126] usb 3-1: bad CDC descriptors
[   95.111186] usbcore: registered new interface driver rndis_wlan
[   95.143877] cfg80211: World regulatory domain updated:
[   95.143880] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   95.143884] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   95.143887] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   95.143889] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   95.143892] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   95.143894] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
richlyn@richlyn-oneric:~$ 



Now my network icon in the toolbar is missing (dosen't come back up after rebooting too), tried setting it up from the system settings.I am still unable to connect.

---

### Post by richlyn9 on 2011-09-11
> **richlyn9 said:**
> 

Removing network-manager ...
network-manager stop/waiting
Purging configuration files for network-manager ...
**dpkg: warning: while removing network-manager, directory '/var/lib/NetworkManager' not empty so not removed.**
dpkg: warning: while removing network-manager, directory '/etc/NetworkManager/system-connections' not empty so not removed.
Processing triggers for ureadahead ...


do you think the network manager was actually not removed...???

---

