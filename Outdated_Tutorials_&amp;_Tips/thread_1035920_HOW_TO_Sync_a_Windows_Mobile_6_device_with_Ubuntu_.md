---
title: "HOW TO: Sync a Windows Mobile 6 device with Ubuntu 8.10"
date: 2009-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Neon Lemmy Koopa on 2009-01-10
This tutorial is going to show you how to synchronize a Windows Mobile 6/6.1 device with Evolution under Ubuntu 8.10.
[U][B]
NOTE[/B][/U]: This tutorial was actually done using Linux Mint 6, however I gave these exact instructions to a friend using Ubuntu 8.10 and he said it worked perfectly.  Besides, Linux Mint 6 is practically Ubuntu 8.10 anyway with more stuff installed.  Also this is done under gnome, but it shouldnt be too hard for KDE or other desktop users.

Well lets get started.

**First off, uninstall ANY AND ALL packages relating to synce, multisync, and opensync.  They will conflict with this tutorial.**

Next you need to install the needed packages.  The required packages are actually in a different reopsitory, so open up Software Sources and add the following repo:
```
http://ppa.launchpad.net/synce/ubuntu your_ubuntu_version main
replacing your_ubuntu_version with the version you are using (intrepid or hardy)
```and update the repo.

Now open up your terminal and enter the following command:
```
sudo apt-get install synce-kpm synce-sync-engine opensync-plugin-synce opensync-plugin-evolution multisync0.90 multisync-tools
```This will install the required packages.

Once that is finished, with the terminal still open, enter the command ```
synce-kpm
``` and wait for the program to come up.  You may want to add a launcher for this to your menu, so you dont have to call up the terminal every time.
**_NOTE_**: if the program says "Make sure Sync-Engine is running" then open a new tab in the terminal and type ```
synce-sync-engine
``` and then the message should disappear.
Once the program is loaded, check your device.  Open ActiveSync on it and verify that there are less than 2 partnerships on it.  If there are 2 partnerships, delete one.
**WARNING: deleting partnerships in Windows Mobile will erase all the data synchronized with that partnership, so when deleting one, make sure to delete the one that is less used, as to preserve as much data as possible.**

Once you have less than 2 partnerships, plug the device into your preferred USB port.  Synce-KPM should recognize the device and start to load it.  Now go to the "Partnership Manager" tab and click "Add".  A window will come up with a text area and some checkboxes.  Mark the checkboxes for the data types you want to synchronize, and in the text area, name the partnership.  Click OK.

Under the partnership tab, you should see your new partnership appear.  Once it does, close Synce-KPM (it will minimize to the tray cause it needs to stay open), and open Multisync-gui from the accessories menu in GNOME.  If it isnt there, open up another tab in the terminal and type "multisync0.90" and it will open.  You should see a window with a toolbar and empty space come up.  This is the program that will transfer the data to your device.  

From the toolbar, click "Add" and enter a name for the group and click "Apply".  Now you should see your group appear in the empty space.  Click "Edit" and another window will come up.  Select any of the check boxes for data that you _**DON'T**_ want to be synced.  If you want all data synced, leave them unchecked.  Now click the "Add Member" button and select "Plugin to synchronize with Windows CE devices" and click "Apply".  Click "Add Member" again and select "Evolution 2.x" and click "Apply".  Ypu should see the selected plugins appear in the left pane of the edit window.  Select "evo2-sync" and choose what calendars, address books, and todo lists to be synced.
_**NOTE: YOU CAN ONLY SYNC CALENDERS UNDER THE CATEGORY "ON THIS COMPUTER".  YOU CAN'T SYNC GOOGLE CALENDARS WITH IT.  OTHER CALENDAR TYPES HAVE NOT BEEN TESTED.**_ 

Once you have configured what to be synced, close the edit window and click "Refresh".  This will start to synchronize your device.  Don't worry if any windows come up asking you which data to sync.  Just choose one and click apply.  If no windows come up, disregard that last statement.  Once multisync says "Sync was Successful" you can disconnect your device and verify that the info was synced.  If you followed the instructions in this tutorial, everything should have synced correctly.

CONGRATULATIONS, YOU HAVE JUST SYNCED YOUR WINDOWS MOBILE 6/6.1 DeVICE WITH UBUNTU!

Now go break out the tequila and celebrate lol.

Some after notes:

[LIST]
[*]If you do not use evolution, there are a number of opensync plugins in the repository for Sunbird, Thunderbird Lightning and other calendars.
[*]Alot of the info here was grabbed from [this page.]("http://www.synce.org/moin/SynceSetup")
[*]If you use your WinMo device to access the web via Internet Sharing, this will break it.  To fix it, you need to go and remove "libsynce0" to remove all SynCE related packages.  Synce is the one that causes the break.  When you want to sync your device again, just install the synce packages listed above.  A little troublesome, yes, but Im working on a way to fix it.
[*]PLEASE DO NOT HESITATE to report any problems or troubles.  Your problems will help me improve this guide.
[*]Here are the official instructions on the SynCE wiki: [http://www.synce.org/moin/SynceInstallation/Ubuntu](http://www.synce.org/moin/SynceInstallation/Ubuntu)
[/LIST]

---

### Post by PhilCash on 2009-01-22
G'day Neon,

So near yet so far...
I had tried several recommendations to get synce working between my HTC Touch Diamond and Evolution and am still at it. I first tried your method without removing all the synce, multisync, and opensync files, and that came the closest to working I've ever been! Brilliant!
I was able to delete an old and created a new partnership, but after reading the entries from one device it failed to read the other device.
So, I followed your instructions to the letter, doing a complete removal of synce etc to remove any config files, and starting from scratch.
I've deleted my "phil-ubuntu" partnership from my HTC, then connected it to my Laptop with Synce-KPM running. 

The HTC is recognised, but the old "phil-ubuntu" partnership is still listed by Synce-KPM even though it is no longer listed in my HTC. I can't create a new partnership as it Synce-KPM says no empty slots are available, and I can't delete the old partnership. The terminal shows:
-----------------------------------
philcash@phil-laptop:~$ synce-kpm
Running dataserver
running the GUI Part
Initializing DataServer
odccm is NOT running!!
Finished with init
Using new partnership api of sync-engine
checking for active partnerships, querying dataserver
Error happened during deletion of partnership...
org.synce.SyncEngine.Error.SyncRunning: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 696, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.5/site-packages/synceKPM/dataserver/dataserver.py", line 667, in deletePartnership
    dbusSyncEngine.DeletePartnership(id,guid)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.synce.SyncEngine.Error.SyncRunning: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 696, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.5/site-packages/SyncEngine/kernel.py", line 851, in DeletePartnership
    raise errors.SyncRunning
SyncRunning: org.synce.SyncEngine.Error.SyncRunning: 
---------------------
I've also tried:
------------------------------
philcash@phil-laptop:~$ synce-delete-partnership

            AVAILABLE DEVICE PARTNERSHIPS
Index     Name         Device      Host         SyncItems
-----     ----         ------      ----         ---------

0	Windows PC	Touch_Diamond	IOCOMM1	[]
1	phil-ubuntu	Touch_Diamond	phil-laptop	[Files Calendar Tasks Contacts ]
Select index of partnership to delete, or empty to exit -1
Selected  1
Deleting partnership...
error: org.synce.SyncEngine.Error.SyncRunning
philcash@phil-laptop:~$ 
------------------------

Maybe I can get the partnership to delete properly if I can stop the SyncEngine, but how do I do that?
Any suggestions would be appreciated.

Cheers,
Phil

---

### Post by Neon Lemmy Koopa on 2009-01-22
I looked up your problem and managed to find that there has been some issues in syncing Ubuntu with an HTC Touch device.  I looked around and found an article you might be interested in.  Unfortunately, I have no HTC Touch device, so I couldn't test it.

[http://www.edadfutura.com/en/sincronizar-htc-diamond-con-ubuntu-macos/]("http://www.edadfutura.com/en/sincronizar-htc-diamond-con-ubuntu-macos/")

I hope this is of some help.

---

### Post by halovivek on 2009-01-22
Thanks for posting. I will try with my windows mobile 6 and get back to you.

---

### Post by dlovely on 2009-01-22
Thx! I have a Samsung Omnia with windows 6 and I'm going to try this and will get back to you.
That is when and if I decide to install Ubuntu this weekend! Still doing some recearch

---

### Post by PhilCash on 2009-01-23
Closer and closer...must be nearly there...

G'day Again,

I have followed the instructions at 
[http://www.edadfutura.com/en/sincron...-ubuntu-macos/](http://www.edadfutura.com/en/sincron...-ubuntu-macos/)
and am closer than ever before, but still not quite there.
After completing the instructions I am able to browse my HTC and see files and ststus information.
But after attempting to sync, I was greeted with the message "Error Synching. Unable to read from one of the members."
There did not appear to be a partnership. I started synch-kpm to investigate, and found that there was no partnership, so I setup a new partnership in synce-kpm (thats SynCE KDE PDA Manager...I'm using Ubuntu and don't know if running a KDE application is problematic or not)
So with a new partnership setup, I ran multisync and attempted to sync with the following results:

The initial response from Multisync was "The previous sync was unclean. Slow Syncing."
Then it carried on and stopped, indicating:

synche-opensync-plugin  Connected
evo2-sync               Sent all Changes
759 entries received
All clients connected or in error

But it seems to have halted at this point as the 'Remove", "Edit", and "Refresh" buttons remain grayed out and the updates have not been passed between Evolution and HTC.

Reboot.

After rebooting and trying to synch again with multisynch, the sync process counted through the 759 entries as before, but reported:
Error synchronising: Unable to read from one of the members.
and
synche-opensync-plugin  Disconnected
evo2-sync               Disconnected
All conflicts have been reported

    hmmm...suspect partnership has failed in some way...so, start terminal and:

philcash@phil-laptop:~$ synce-kpm
Running dataserver
running the GUI Part
Initialising DataServer
odccm is NOT running!!
Finished with init
Using new partnership api of sync-engine
checking for active partnerships, querying dataserver

The Synce gui starts and lists the partner as before, but the popup stating "No active partnerships found" comes up.

I can still browse the HTC, so I feel its really coming down to these blasted partnerships, but I just don't know how they work or how to diagnose problems with them.

As always, any help would be appreciated.

Cheers,
Phil

---

### Post by isleshocky77 on 2009-01-23
I just wanted to confirm this does work and say THANK YOU!  I've been trying to get my phone to sync with Linux for about a year.  I don't know if it was specifically this guide because I just got an upgraded phone through insurance since my old one died.  

I just wanted to confirm that the Palm Treo 700wx (from Verizon) running Windows Mobile 6 CAN successfully sync with Ubuntu 8.10 and Evolution 2.x.

Side not at first I couldn't get the machine to respond to my phone and I thought it was a problem with drivers or blacklisting ipaq or something like that. But it turned out to be the USB cable. Playing with the positioning of my Treo on the cradle got it to show up through dmesg and then it connected in the synce-kpm.

Also make sure if you're running windows mobile 6 make sure you're using RNDIS USB mode by clicking the UsbSwitch program under the programs menu.

Once again thanks.

---

### Post by isleshocky77 on 2009-01-23
> **PhilCash said:**
> Closer and closer...must be nearly there...

G'day Again,

I have followed the instructions at 
[http://www.edadfutura.com/en/sincron...-ubuntu-macos/](http://www.edadfutura.com/en/sincron...-ubuntu-macos/)
and am closer than ever before, but still not quite there.
After completing the instructions I am able to browse my HTC and see files and ststus information.
But after attempting to sync, I was greeted with the message "Error Synching. Unable to read from one of the members."
There did not appear to be a partnership. I started synch-kpm to investigate, and found that there was no partnership, so I setup a new partnership in synce-kpm (thats SynCE KDE PDA Manager...I'm using Ubuntu and don't know if running a KDE application is problematic or not)
So with a new partnership setup, I ran multisync and attempted to sync with the following results:

The initial response from Multisync was "The previous sync was unclean. Slow Syncing."
Then it carried on and stopped, indicating:

synche-opensync-plugin  Connected
evo2-sync               Sent all Changes
759 entries received
All clients connected or in error

But it seems to have halted at this point as the 'Remove", "Edit", and "Refresh" buttons remain grayed out and the updates have not been passed between Evolution and HTC.

Reboot.

After rebooting and trying to synch again with multisynch, the sync process counted through the 759 entries as before, but reported:
Error synchronising: Unable to read from one of the members.
and
synche-opensync-plugin  Disconnected
evo2-sync               Disconnected
All conflicts have been reported

    hmmm...suspect partnership has failed in some way...so, start terminal and:

philcash@phil-laptop:~$ synce-kpm
Running dataserver
running the GUI Part
Initialising DataServer
odccm is NOT running!!
Finished with init
Using new partnership api of sync-engine
checking for active partnerships, querying dataserver

The Synce gui starts and lists the partner as before, but the popup stating "No active partnerships found" comes up.

I can still browse the HTC, so I feel its really coming down to these blasted partnerships, but I just don't know how they work or how to diagnose problems with them.

As always, any help would be appreciated.

Cheers,
Phil

If you have a lot of contacts and/or appointments this part can take a while.  I wasn't sure what kind of result I was waiting for so I just let it sit.  Originally I had problems where the phone kept disconnecting; it appeared to happen whenever the phone went idle.  I decided to keep pressing the menu button every 30 seconds and touching the screen and mine finally did complete. It took about 5 minutes or so and when done your phone should show as being sync.  Leave active sync open on your phone and you'll see it come to life while syncing with a progress bar.

Hope some of this helps.

---

### Post by gdiepen on 2009-04-15
> **Neon Lemmy Koopa said:**
> Some after notes:

[LIST]
[*]If you do not use evolution, there are a number of opensync plugins in the repository for Sunbird, Thunderbird Lightning and other calendars.
[*]Alot of the info here was grabbed from [this page.]("http://www.synce.org/moin/SynceSetup")
[*]If you use your WinMo device to access the web via Internet Sharing, this will break it.  To fix it, you need to go and remove "libsynce0" to remove all SynCE related packages.  Synce is the one that causes the break.  When you want to sync your device again, just install the synce packages listed above.  A little troublesome, yes, but Im working on a way to fix it.
[*]PLEASE DO NOT HESITATE to report any problems or troubles.  Your problems will help me improve this guide.
[/LIST]

Hi Neon,

I would like to ask whether you can mention the official ubuntu instructions on our wiki somewhere in your post. The reason I am asking this is that currently there are a lot of old and incorrect tutorials present on the web that are not updated to the current versions of SynCE. When people use these old tutorials, they incorrectly get the impression that SynCE is not working.

I have recently updated the Ubuntu instructions at our wiki to make them easier to follow and they can be found at:
[http://www.synce.org/moin/SynceInstallation/Ubuntu](http://www.synce.org/moin/SynceInstallation/Ubuntu)

Kind regards,

Guido Diepen

---

### Post by Neon Lemmy Koopa on 2009-04-15
> **gdiepen said:**
> Hi Neon,

I would like to ask whether you can mention the official ubuntu instructions on our wiki somewhere in your post. The reason I am asking this is that currently there are a lot of old and incorrect tutorials present on the web that are not updated to the current versions of SynCE. When people use these old tutorials, they incorrectly get the impression that SynCE is not working.

I have recently updated the Ubuntu instructions at our wiki to make them easier to follow and they can be found at:
[http://www.synce.org/moin/SynceInstallation/Ubuntu](http://www.synce.org/moin/SynceInstallation/Ubuntu)

Kind regards,

Guido Diepen
I don't understand: If you updated your tutorials already, what do you want me to do?

---

### Post by gdiepen on 2009-04-15
> **Neon Lemmy Koopa said:**
> I don't understand: If you updated your tutorials already, what do you want me to do?
What I mean is whether you can clearly mention in your guide somewhere that we have the Ubuntu instructions on our wiki also.

The reason why I am asking is that if in some time we make a change in SynCE somehow and your guide is not updated, people might follow the instructions they find on your guide. Because these instructions will not up-to-date with the then-current version of SynCE, people run into problems while installing and think that SynCE is not working, while actually the problem was the fact that they were following an outdated guide.

---

### Post by glendavee on 2010-01-04
I'm trying to sync a windows mobile 6 device with evolution and running karmic. I've followed Neon's instructions and all seemed to go well. Multisync sees the device and when I sync, data seems to be exchanged. Problem is that when I edit an entry the change doesn't get synced and if I add a new entry either in evolution or the device then the new entry doesn't get synced to the other device. I've tried to check my settings, but can't find the problem. Obviously I'm doing something wrong. Grateful for any help.

---

### Post by ecuajosh on 2010-01-18
thanks guys for all you help.
im sorry i might be stupid but if don't ask i'll stay stupid. lol
im trying to add the repo to the software source but i don'd get it to work, here is what im doing:
software sources | other software 
then i click add
then i typed [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) karmic main
i'm running ubuntu 9.10 karmic koala
but it doesn't let me click on add(faded).
what am i doing wrong. all help appreciated.
thanks in advance

---

