---
title: "HOWTO: Windows Mobile sync for Intrepid"
date: 2009-02-27
forum: Outdated Tutorials &amp; Tips
---

### Post by HittingSmoke on 2009-02-27
[I]I just managed to get this right after about a year of multiple threads and many different ways of trying. This way took me about four hours and should take you even less with this guide.

This has been tested to work as described on a CDMA HTC Touch Pro from Sprint as well as an HTC Apache with the same radio[/I]

[COLOR="Red"][B]WARNING, BACK UP ALL CONTACTS AND EVENTS BEFORE SYNCING. IT IS HIGHLY LIKELY THAT ON YOUR FIRST SYNC YOU WILL LOSE ALL YOUR CONTACTS ON ONE OR BOTH DEVICES!
On my first sync (with all my contacts on my phone) they were wiped out and I had to manually add them all to Evolution again because I didnt have a compatible backup format and CVS sucks... [PIMBackup]("http://freewareppc.com/database/pimbackup.shtml") for your WM device is a nice free option[/B][/COLOR]

This is a guide to getting your Windows Mobile 5+ smartphone or pocket PC to sync with Evolution. It should also work (using extra opensync plug-ins) with Sunbird, KDE 3.x PIM, Blackberry, Palm, and Open Palm packages and devices. This guide, however will only focus on Windows Mobile to Evolution.

To start off, we need to install a few packages that our GUI sync apps will rely on.

```
sudo apt-get install synce-sync-engine synce-kpm multisync0.90
```
****note*** There is no Gnome native sync option that I can find for Intrepid that's nearly as good as sync-kpm. I recommend it to both KDE and Gnome users. Use synce-kde or synce-gdm for Hardy*

For file browsing under Nautilus in Gnome also install
```
sudo apt-get install synce-gnomevfs
```
****note*** this is not necessary with newer WM 6+ devices as they give you an option to use a mass storage connection when pluged in which works like any other removable storage in Ubuntu.*

Now we need to install our OpenSync plugins for use with MultiSync. For Windows Mobile and Evolution we want to run
```
sudo apt-get install opensync-plugin-synce opensync-plugin-evolution
```

At this point you want to use Alt-F2 to run **synce-sync-engine** then Alt-F2 and run **synce-kpm**

****note***synce-kpm wont create a launcher in your menu, you might want to set a desktop shortcut to it*
****note*** you want to make sure RNDIS is enabled on your phone by going to "Settings > Connections tab > USB to PC" and making sure the "Enable advanced network functionality" box is check, otherwise this wont work. **Many other guides require this to be disabled, so if you've tried other guides to sync your WM device, this might be disabled**.*

At this point you should be able to connect your device and it should be recognised by the already running sync-kpm. This will ask you to create a partnership for your device.[SIZE="1"](*see issues at bottom)[/SIZE] Pick a name and what you'd like synced and you should see a screen that shows you battery info, basic device info and an add/remove programs tab.

If at this point your device isn't detected open up ActiveSync on your device and go to "Menu > Connections" and make sure "Synchronize all PC's using this Connection:" is checked and set to USB

If that still doesn't work, try disabling the Ubuntu firewall by using [COLOR="Red"]**(only if you are behind a router with a firewall, otherwise see bottom of post for ports to open individually)**[/COLOR]
```
sudo ufw disable
```

If you've got a connection with synce-kpm now then you can start up the program that actually makes the sync connection, MultiSync.

Start multisync by running **multisync0.90** via Alt+F2 or from a terminal window. In the top left click the Add button and choose a group name for this sync profile. After choosing your group name you will be presented with a window to set up the actual sync profile.

Click the **"Add Member"** button and select **"Evolution 2.x"**. Click the "Add Member" button once more and select **"Plugin to synchronize with Windows CE device"** and click close.

Now with the KDE PDA Manager (synce-kpm) running, click the refresh button under your newly created group in MultiSync and your contacts and calendar **should** sync.

Like I said, the first time it wiped my contacts from my device but it seems as long as you don't delete anything from your PC that you don't want deleted form your device then it will work fine and sync both ways. I had deleted all the contacts in Evolution to try and to a clean sync to the PC but instead it registered the deletes on my device.

* There seems to be a problem with synce-kpm registering the device as new each time it's pluged in. Each time you plug in your device to sync it you may have to create a new partnership with synce-kpm. I'm not sure how to fix this or why each new one created sticks under *synce-configure-bindings* but the syncing itself works so hopefully someone will be able to work out this lesser problems later.

*The individual ports to open for Windows Mobile syncing are TCP 990, 999, 5678, 5721, 26675. I'm not going into detail on how top open firewall ports, you can find this info many other places with a quick Google search.

---

### Post by noren on 2009-11-16
wow this one really worked thanks a lot.. i was able to sync my win 5 mobile..

cheers

---

### Post by mirchichamu on 2009-11-20
Thanks hitting smoke for your detailed explanation. In fact that was the reason I left linux and switched back to windows when I was not able to connect my PPC to linux.
Now I came back again but the situation has not changed much. I did whatever is mentioned in the following link but partially succeeded.

[http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)

I succeeded to install synce tray icon. It detects my Htc touch viva(opal)
when I connect but It fails to connect through Natalius. So I cannot explore my device. I just want to explore my device and nothing else. 

One respected member suggested to install win5torage but that also could not open all my folders on my SD card.

Can you help me in this regard? Thanks in advance.

---

### Post by HittingSmoke on 2009-11-20
> **mirchichamu said:**
> Thanks hitting smoke for your detailed explanation. In fact that was the reason I left linux and switched back to windows when I was not able to connect my PPC to linux.
Now I came back again but the situation has not changed much. I did whatever is mentioned in the following link but partially succeeded.

[http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)

I succeeded to install synce tray icon. It detects my Htc touch viva(opal)
when I connect but It fails to connect through Natalius. So I cannot explore my device. I just want to explore my device and nothing else. 

One respected member suggested to install win5torage but that also could not open all my folders on my SD card.

Can you help me in this regard? Thanks in advance.

I'm sorry, I wish I could help but I have a Windows 7 PC running right now that I'm using to sync my phone so I haven't kept up with the Linux apps.

Normally I would re-install them and take a shot at recreating your problem but my Touch Pro is having some hardware related issues right now so I can't try and sync it.

If I get a chance to order a new phone soon I'll give it a try and let you know the results.

---

### Post by mirchichamu on 2009-11-21
> **HittingSmoke said:**
> I'm sorry, I wish I could help but I have a Windows 7 PC running right now that I'm using to sync my phone so I haven't kept up with the Linux apps.

Normally I would re-install them and take a shot at recreating your problem but my Touch Pro is having some hardware related issues right now so I can't try and sync it.

If I get a chance to order a new phone soon I'll give it a try and let you know the results.

Thanks HittingSmoke for your sympathetic reply!

I will be waiting for you sir.
Best wishes.

---

### Post by nagaraj on 2010-01-05
guess this thread is quite old and may not b viewed but strill i will put my query here b coz this is the only how to that came close to my requirement. i managed to sync my smartphone (cingular/htc 3100 win5)with my pc (karmic) but nothing happened in evoltion. multisync displayed that 585 contacts were transfered . now where did they all go? thankfully i did not loose any data. any ideas what may b happening?

---

