---
title: "HOWTO: Sync Evolution with Nokia N95 via Bluetooth on Ubuntu Gutsy"
date: 2008-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by HyRax on 2008-02-23
[COLOR="Red"]**** NOTE: 26TH APRIL 2008 - THIS GUIDE ALSO APPLIES TO UBUNTU 8.04 HARDY HERON. TESTED AND WORKING 100% ****[/COLOR]

Hi all,

After much pain, I have finally got my Nokia N95 (non-8GB model) syncing properly with Evolution, so I thought I'd share my experience, in particular to those who are currently suffering from the "Syntax error" issue that arises out of most of the other HowTo's.

This HowTo has the following prerequisites:

[list]
[*]Vanilla Ubuntu Gutsy Gibbon 7.10 with relevant updates to today. [COLOR="Red"]Or vanilla Ubuntu Hardy Heron 8.04 LTS First Release.[/color]
[*]Nokia N95 with firmware 11.0.026 or later.
[*]OpenSync version 0.21 (Gutsy comes with 0.19 which causes the "Syntax error" messages people have been getting - [COLOR="Red"]Hardy Heron comes with 0.22[/color]).
[*]Evolution 2.12.0 (as shipped with Gutsy - [COLOR="Red"] Hardy ships with 2.22.1[/color]).
[*]A successful pairing of your N95 and Ubuntu install. If you can transfer files to/from your N95, you're ready to sync Evolution. If you don't know how to pair your Bluetooth-enabled phone, there is an excellent tutorial for doing that [color="blue"]_[here](http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu)[/color]_.
[/list]

NOTE: OpenSync does NOT have support yet for syncing Notes. Using this guide you will only be able to sync your Contacts, Tasks (ToDo's) and Calendar.


***[color="red"]DISCLAIMER: You try these intructions at your own risk. I will not be responsible if your N95 goes supernova or if the cats and dogs in your neighbourhood call a truce and start living together. Backup all data on your N95 and Evolution installation before doing anything that you might regret later!**[/color]*


There are two lots of instructions here, one for the GUI fans and one for the commando, erm, command-line fans. Take your pick, but before we go anywhere, we do need to get the MAC address and SyncML Client Channel number your N95 uses.

[list=1]
[*]To get your N95's MAC address, open a terminal and type:

```

$ hcitool scan
Scanning ...
        00:AA:11:BB:22:CC       Nokia N95
$

```

[*]My phone is called "Nokia N95" and has a MAC address of 00:AA:11:BB:22:CC - yours will obviously be different. Note it down.
.
[*]Next, determine the Channel your N95 uses to sync with. By default, it should be Channel 10, but if in doubt, issue the command (substitute *your* MAC address):

```

$ sdptool browse 00:AA:11:BB:22:CC

```

...and scroll through until you come to the section referring to "SyncMLClient" (NOT the "Nokia SyncML Server" or "SyncML DM Client"). Note down the Channel shown.
.
[COLOR="Red"]HARDY HERON USERS: SKIP THE NEXT TWO STEPS. You do NOT need to do this. Go to Step 6 NOW.[/color]
[*]Next, we need to update Ubuntu's repository so we can get the latest OpenSync software. Start with getting the GPG keys:

```

$ gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
$ gpg --export CB210090B029CB84 | sudo apt-key add -

```

[*]Now add the following to the end of /etc/apt/sources.list (note, there is no Gutsy repository yet at the time of writing):

```

deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main

```

*GUI fans can use System->Administration->Software Sources->Third-Party Software and use the "Add" button to add each line in turn. When you click close, you will be prompted to reload to get the info from the new repositories you just added. Do so.*
.
[COLOR="Red"]HARDY HERON USERS: Continue instruction from here. The Ubuntu-supplied version of OpenSync is 0.22 and will work for you, hence no need for third-party updates.[/color]
[*]Now update the system with new package lists and download the software we need:

```

$ sudo apt-get update
$ sudo apt-get install multisync-tools multisync0.90 opensync-plugin-evolution opensync-plugin-syncml

```
[/list]


Now we are ready to configure OpenSync. Choose GUI or command line instructions below.



[size="5"][color="blue"]**_COMMAND LINE CONFIGURATION_**[/color][/size]

[list=1]
[*]Let's go commando with OpenSync. First we create a group to refer to our sync session with. I've called mine "evolution-n95", but you can call it whatever you want. We then create the config for the Evolution side as the first member of this group.

```

$ msynctool --addgroup evolution-n95
$ msynctool --addmember evolution-n95 evo2-sync
$ msynctool --configure evolution-n95 1

```

[*]Your text editor will pop up editing member 1 of your evolution-n95 group. Edit the config to look like this:

```

<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

```

[*]Now do to the N95 side, adding its config as the second member of the group:

```

$ msynctool --addmember evolution-n95 syncml-obex-client
$ msynctool --configure evolution-n95 2

```

[*]Your text editor will pop up editing member 2 of your evolution-n95 group. Edit the config to look like this (remember to put *your* N95's MAC address and Channel number in):

```

<config>
	<bluetooth_address>00:AA:11:BB:22:CC</bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel>
	<interface>0</interface>
	<identifier>PC Suite</identifier>
	<version>1</version>
	<wbxml>1</wbxml>
	<username></username>
	<password></password>
	<type>2</type>
	<usestringtable>1</usestringtable>
	<onlyreplace>0</onlyreplace>
	<recvLimit>0</recvLimit>
	<maxObjSize>0</maxObjSize>
	<contact_db>Contacts</contact_db>
	<calendar_db>Calendar</calendar_db>
	<note_db></note_db>
</config>

```

[*]Now you're ready to rock and/or roll. Let's try syncing:

```

$ msynctool --sync evolution-n95

```

...and you should get a whole stream of mumbo-jumbo similar to the following:

```

$ msynctool --sync evolution-n95
Synchronizing group "evolution-n95" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-47AA3D7000000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47AAB03C00000000 with data of size 4 from member 1. Changetype ADDED
...
Received an entry 20080206T205400Z-5332-1000-1-0@lamaar with data of size 4 from member 1. Changetype ADDED
Received an entry 20080212T131911Z-5797-1000-1-0@lamaar with data of size 4 from member 1. Changetype ADDED
...
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Going to receive 27 changes
Received an entry 1 with data of size 4 from member 2. Changetype ADDED
Going to receive 4 changes
Received an entry 2 with data of size 4 from member 2. Changetype ADDED
Received an entry 3 with data of size 4 from member 2. Changetype ADDED
...
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Sent an entry pas-id-47BF9BC100000001 of size 92 to member 1. Changetype ADDED
Sent an entry pas-id-47BF9BC100000002 of size 104 to member 1. Changetype ADDED
Sent an entry pas-id-47BF9BC100000003 of size 113 to member 1. Changetype ADDED
...
Sent an entry 20080223T040625Z-14241-1000-1-0@lamaar of size 426 to member 1. Changetype ADDED
Sent an entry 20080223T040625Z-14241-1000-1-2@lamaar of size 252 to member 1. Changetype ADDED
...
Member 1 of type evo2-sync committed all changes.
Received an reply to our sync
Sent an entry 29 of size 205 to member 2. Changetype ADDED
Sent an entry 30 of size 153 to member 2. Changetype ADDED
...
Received an reply to our sync
Sent an entry 6 of size 362 to member 2. Changetype ADDED
Sent an entry 7 of size 345 to member 2. Changetype ADDED
...
Member 2 of type syncml-obex-client committed all changes.
All clients have written
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync was successful
$

```

Depending on your data to sync, you may see a LOT of info. This may be done quickly or take a minute or two. In any case, you should see "The sync was successful" at the end amd be returned to the prompt.
.
[*]Pat yourself on the back - you're done. Sync again with the same command as much as you want.
[/list]

[size="5"][color="blue"]**_GUI CONFIGURATION_**[/color][/size]
[list=1]
[*]Go to the Accessories menu and choose "Multisync-qad".
[*]Click on the "Add" icon at the top. You will be prompted for a group name. You can use whatever you want. I chose "evolution-n95". Type it in and click "Apply".
[*]Now click on the "Edit" button in the middle of the window.
[*]In the new window that appears, click "Add member" on the middle-left. A new window appears.
[*]Choose "Evolution 2.x" from the list and click "Apply". This is your first member of the group and will appear as "evo2-sync" in the list under the group name.
[*]Click on "evo2-sync" in the list and the window content will change to show its config. All three of the options should read "Personal".
[*]Now click on "Add member" again and this time choose "SyncML over OBEX Client" from the list and click Apply. This will be your second member of the group and will appear as "syncml-obex-client" in the list under the group name.
[*]Click on "syncml-obex-client" in the list and the window content will change to show its config. Ensure that all the text in that window looks like this (substituting *your* N95's MAC address and Channel number of course):

```

<config>
	<bluetooth_address>00:AA:11:BB:22:CC</bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel>
	<interface>0</interface>
	<identifier>PC Suite</identifier>
	<version>1</version>
	<wbxml>1</wbxml>
	<username></username>
	<password></password>
	<type>2</type>
	<usestringtable>1</usestringtable>
	<onlyreplace>0</onlyreplace>
	<recvLimit>0</recvLimit>
	<maxObjSize>0</maxObjSize>
	<contact_db>Contacts</contact_db>
	<calendar_db>Calendar</calendar_db>
	<note_db></note_db>
</config>

```
[*]Now click on the Close button. You are ready to sync. Click on the Refresh button in the middle of the original window and watch was your N95 syncs away. You won't get any feedback other than the status in that window. If all is good, after a few seconds or a minute, you should see "The sync was successful".
.
[*]Pat yourself on the back. If you have a pet, pat him too, because he's been begging for your attention all this time.
[/list]

Note that your N95 will record a successful (or failed) sync in its log too.

That's it! Happy syncing! :)

---

### Post by olavjunior on 2008-02-27
Works perfectly! Thanks :) I have the latest firmware of n95, so that's ok. Any easy way to extend this to synchronizing google calendar at the same time? And is it possible to have n95 start the sync? (That's no biggi though:))

---

### Post by HyRax on 2008-02-27
Hmmm - I don't use the Google calendar, so I haven't tried that, but it shouldn't be difficult. I'll look into it.

As for the sync, I setup a cron job to execute the command-line sync twice a day from the PC, so I don't even have to initiate sync from my N95. I treat the N95 as a "slave" to the PC.

Given that it is OpenSync that facilitates the sync itself, it would have to be listening out for the N95 to work, so this HowTo I did won't facilitate an N95-to-PC sync, only a PC-to-N95 sync. Again, let me look into it. :)

---

### Post by HyRax on 2008-02-27
OK, there's a post in these very forums where someone has dealt with syncing Evolution with Google Calendar using SyncEvolution and scheduleworld.com to facilitate a two-way sync.

[http://ubuntuforums.org/showthread.php?t=282408](http://ubuntuforums.org/showthread.php?t=282408)

But like with the N95, it is a master-slave type arrangement - everything has to be initiated from your PC - your N95 and Google are just "off-site copies" of your contacts and calendars.

As for the N95-to-PC sync, I'll keep looking.

---

### Post by olavjunior on 2008-02-28
Nice :) Having one problem though.. I've used the graphical interface to choose what to be included in the synk. And there I've chosen the private adressbook (I have two, one for emailadresses and one for phone contacts) But it still synks all my email contacts :( So I've ended up with hundreds of duplicate names... :S

EDIT: Never mind, I must have done something wrong, cause all my emails had gotten into my regular contacts. Deleted and everything works fine now :)

---

### Post by paddy1978 on 2008-02-28
Thanks for posting this guide!

 I seem to be able to get tasks, calendar and contacts syncing but can't get notes to work. If there are any notes on the N95, the process just seems to stall. Are notes syncing for you, or do you not use these?

---

### Post by olavjunior on 2008-03-05
Damn! I get duplicated every entry in the calendar, both on phone and pc!! Help!

---

### Post by HyRax on 2008-03-05
> **paddy1978 said:**
> Thanks for posting this guide!

 I seem to be able to get tasks, calendar and contacts syncing but can't get notes to work. If there are any notes on the N95, the process just seems to stall. Are notes syncing for you, or do you not use these?

Hiya,

I was never using Notes before and my instruction does include syncing the Notes.

Just trying it out myself, yes - the sync does indeed hang and some further research indicates that OpenSync does *not* have support for syncing Notes yet.

The problem is fixed by simply not syncing Notes, or deleting your Notes from both sides before trying to sync again.

Go into a terminal window and enter:
```

$ msynctool --configure evolution-n95 2

```

...and edit the second-last line that reads
```

<note_db>Notes</note_db>

```

...to be:
```

<note_db></note_db>

```

Save and exit, then try and re-sync. Your Notes will be ignored and the sync will complete successfully for just the Contacts and Calendar.

*FOR GUI USERS:* Open Applications->Accessories->Multisync-qad, hit the Edit button, then click on "syncml-obex-client" in the list on the left, then edit the above-mentioned line in the panel on the right. Click on the Close button and then click on the Refresh button to sync again.

I've modified my instruction accordingly.

> **olavjunior said:**
> Damn! I get duplicated every entry in the calendar, both on phone and pc!! Help!

As for your doubled contacts, not sure how that happened - mine has worked flawlessly...!

---

### Post by Dooley on 2008-03-15
Hi there I was wondering if you guys could help me.

I can connect to my phone via bluetooth no problem.

My phones mac address from the hcitool scan is 
```

00:1C:9A:1F:38:4C       My phone

```

My evolution configuration file for evolution from msynctool --configure evolution-n95 1 is...
```

<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

```

This is my bluetooth config (msynctool --configure evolution-n95 2)
```

<config>
        <bluetooth_address>00:1C:9A:1F:38:4C</bluetooth_address>
        <bluetooth_channel>10</bluetooth_channel>
        <interface>0</interface>
        <identifier>PC Suite</identifier>
        <version>1</version>
        <wbxml>1</wbxml>
        <username></username>
        <password></password>
        <type>2</type>
        <usestringtable>1</usestringtable>
        <onlyreplace>0</onlyreplace>
        <recvLimit>0</recvLimit>
        <maxObjSize>0</maxObjSize>
        <contact_db>Contacts</contact_db>
        <calendar_db>Calendar</calendar_db>
        <note_db></note_db>
</config>

```

When I run msynctool --sync evolution-n95 I get
```

Synchronizing group "evolution-n95"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
Member 1 of type evo2-sync committed all changes.
Member 1 of type evo2-sync just disconnected

```

During this process on my phone it says connecting,disconnecting and then System Error.

Here is my Sync Connection Settings on my N95
Server Version: 1.1
Data Bearer: Bluetooth
Host Address: PC Suite
Username: none
Password : none
Allow sync requests: Yes
Accept all sync requests: Yes

In my applications I have Contacts, Calendar and Notes enabled. And the settings seem pretty straightforward.

When I view the log profile the Status says Incomplete.

Can anyone spot something wrong with my setup?

Thanks!

---

### Post by HyRax on 2008-03-16
Check the version of OpenSync you are running. The ¨Syntax error¨ issue is directly related to the version supplied with Ubuntu Gutsy 7.10. Upgrade to OpenSync 0.21 or later and I suspect your problem will magically disappear (see the top of my first post).

You can check your version of OpenSync by looking at the version installed via System->Administration->Synaptic Package Manager, then lookup ¨ÖpenSync¨.

---

### Post by sammys on 2008-03-16
For those of you wanting OpenSync 0.22 packages for Ubuntu Gutsy amd64 architecture i've created them and put them into a repository. Add this as a third party repository in Software Sources:
```
deb http://synerger.com/opensync-amd64 gutsy main
```

Please note that i'm **not** providing support or warranty for these packages. They are simply a rebuild for amd64 using the source packages provided at [http://opensync.gforge.punktart.de/repo/opensync-0.21](http://opensync.gforge.punktart.de/repo/opensync-0.21)

**Use these packages at your own risk!** I've tested it using my N82 and the sync gives no errors.

Enjoy!

---

### Post by Dooley on 2008-03-16
Thanks for the reply.
I thought I had the newest version of openSync, however now that I do, I'm getting another error... a seg fault.

When I run
msynctool --sync evolution-n95
```

Synchronizing group "evolution-n95"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Going to receive 126 changes
Going to receive 12 changes
Received an entry 1 with data of size 4 from member 2. Changetype ADDED
Received an entry 2 with data of size 4 from member 2. Changetype ADDED
Received an entry 3 with data of size 4 from member 2. Changetype ADDED
Received an entry 4 with data of size 4 from member 2. Changetype ADDED
Received an entry 5 with data of size 4 from member 2. Changetype ADDED
Received an entry 6 with data of size 4 from member 2. Changetype ADDED
Received an entry 7 with data of size 4 from member 2. Changetype ADDED
Received an entry 8 with data of size 4 from member 2. Changetype ADDED
Received an entry 9 with data of size 4 from member 2. Changetype ADDED
Received an entry 10 with data of size 4 from member 2. Changetype ADDED
Received an entry 11 with data of size 4 from member 2. Changetype ADDED
Received an entry 12 with data of size 4 from member 2. Changetype ADDED
Received an entry 13 with data of size 4 from member 2. Changetype ADDED
Received an entry 14 with data of size 4 from member 2. Changetype ADDED
Received an entry 15 with data of size 4 from member 2. Changetype ADDED
Received an entry 16 with data of size 4 from member 2. Changetype ADDED
Received an entry 17 with data of size 4 from member 2. Changetype ADDED
Received an entry 18 with data of size 4 from member 2. Changetype ADDED
Received an entry 19 with data of size 4 from member 2. Changetype ADDED
Received an entry 20 with data of size 4 from member 2. Changetype ADDED
Received an entry 21 with data of size 4 from member 2. Changetype ADDED
Received an entry 22 with data of size 4 from member 2. Changetype ADDED
Received an entry 23 with data of size 4 from member 2. Changetype ADDED
Received an entry 24 with data of size 4 from member 2. Changetype ADDED
Received an entry 25 with data of size 4 from member 2. Changetype ADDED
Received an entry 26 with data of size 4 from member 2. Changetype ADDED
Received an entry 27 with data of size 4 from member 2. Changetype ADDED
Received an entry 28 with data of size 4 from member 2. Changetype ADDED
Received an entry 29 with data of size 4 from member 2. Changetype ADDED
Received an entry 30 with data of size 4 from member 2. Changetype ADDED
Received an entry 31 with data of size 4 from member 2. Changetype ADDED
Received an entry 32 with data of size 4 from member 2. Changetype ADDED
Received an entry 33 with data of size 4 from member 2. Changetype ADDED
Received an entry 34 with data of size 4 from member 2. Changetype ADDED
Received an entry 35 with data of size 4 from member 2. Changetype ADDED
Received an entry 36 with data of size 4 from member 2. Changetype ADDED
Received an entry 37 with data of size 4 from member 2. Changetype ADDED
Received an entry 38 with data of size 4 from member 2. Changetype ADDED
Received an entry 39 with data of size 4 from member 2. Changetype ADDED
Received an entry 40 with data of size 4 from member 2. Changetype ADDED
Received an entry 41 with data of size 4 from member 2. Changetype ADDED
Received an entry 42 with data of size 4 from member 2. Changetype ADDED
Received an entry 43 with data of size 4 from member 2. Changetype ADDED
Received an entry 44 with data of size 4 from member 2. Changetype ADDED
Received an entry 45 with data of size 4 from member 2. Changetype ADDED
Received an entry 46 with data of size 4 from member 2. Changetype ADDED
Received an entry 47 with data of size 4 from member 2. Changetype ADDED
Received an entry 48 with data of size 4 from member 2. Changetype ADDED
Received an entry 49 with data of size 4 from member 2. Changetype ADDED
Received an entry 50 with data of size 4 from member 2. Changetype ADDED
Received an entry 51 with data of size 4 from member 2. Changetype ADDED
Received an entry 52 with data of size 4 from member 2. Changetype ADDED
Received an entry 53 with data of size 4 from member 2. Changetype ADDED
Received an entry 54 with data of size 4 from member 2. Changetype ADDED
Received an entry 55 with data of size 4 from member 2. Changetype ADDED
Received an entry 56 with data of size 4 from member 2. Changetype ADDED
Received an entry 57 with data of size 4 from member 2. Changetype ADDED
Received an entry 58 with data of size 4 from member 2. Changetype ADDED
Received an entry 59 with data of size 4 from member 2. Changetype ADDED
Received an entry 60 with data of size 4 from member 2. Changetype ADDED
Received an entry 61 with data of size 4 from member 2. Changetype ADDED
Received an entry 62 with data of size 4 from member 2. Changetype ADDED
Received an entry 63 with data of size 4 from member 2. Changetype ADDED
Received an entry 64 with data of size 4 from member 2. Changetype ADDED
Received an entry 65 with data of size 4 from member 2. Changetype ADDED
Received an entry 66 with data of size 4 from member 2. Changetype ADDED
Received an entry 67 with data of size 4 from member 2. Changetype ADDED
Received an entry 68 with data of size 4 from member 2. Changetype ADDED
Received an entry 69 with data of size 4 from member 2. Changetype ADDED
Received an entry 70 with data of size 4 from member 2. Changetype ADDED
Received an entry 71 with data of size 4 from member 2. Changetype ADDED
Received an entry 72 with data of size 4 from member 2. Changetype ADDED
Received an entry 73 with data of size 4 from member 2. Changetype ADDED
Received an entry 74 with data of size 4 from member 2. Changetype ADDED
Received an entry 75 with data of size 4 from member 2. Changetype ADDED
Received an entry 76 with data of size 4 from member 2. Changetype ADDED
Received an entry 77 with data of size 4 from member 2. Changetype ADDED
Received an entry 78 with data of size 4 from member 2. Changetype ADDED
Received an entry 79 with data of size 4 from member 2. Changetype ADDED
Received an entry 80 with data of size 4 from member 2. Changetype ADDED
Received an entry 81 with data of size 4 from member 2. Changetype ADDED
Received an entry 82 with data of size 4 from member 2. Changetype ADDED
Received an entry 83 with data of size 4 from member 2. Changetype ADDED
Received an entry 84 with data of size 4 from member 2. Changetype ADDED
Received an entry 85 with data of size 4 from member 2. Changetype ADDED
Received an entry 86 with data of size 4 from member 2. Changetype ADDED
Received an entry 87 with data of size 4 from member 2. Changetype ADDED
Received an entry 88 with data of size 4 from member 2. Changetype ADDED
Received an entry 89 with data of size 4 from member 2. Changetype ADDED
Received an entry 90 with data of size 4 from member 2. Changetype ADDED
Received an entry 91 with data of size 4 from member 2. Changetype ADDED
Received an entry 92 with data of size 4 from member 2. Changetype ADDED
Received an entry 93 with data of size 4 from member 2. Changetype ADDED
Received an entry 94 with data of size 4 from member 2. Changetype ADDED
Received an entry 95 with data of size 4 from member 2. Changetype ADDED
Received an entry 96 with data of size 4 from member 2. Changetype ADDED
Received an entry 97 with data of size 4 from member 2. Changetype ADDED
Received an entry 98 with data of size 4 from member 2. Changetype ADDED
Received an entry 99 with data of size 4 from member 2. Changetype ADDED
Received an entry 100 with data of size 4 from member 2. Changetype ADDED
Received an entry 101 with data of size 4 from member 2. Changetype ADDED
Received an entry 102 with data of size 4 from member 2. Changetype ADDED
Received an entry 103 with data of size 4 from member 2. Changetype ADDED
Received an entry 104 with data of size 4 from member 2. Changetype ADDED
Received an entry 105 with data of size 4 from member 2. Changetype ADDED
Received an entry 106 with data of size 4 from member 2. Changetype ADDED
Received an entry 107 with data of size 4 from member 2. Changetype ADDED
Received an entry 108 with data of size 4 from member 2. Changetype ADDED
Received an entry 109 with data of size 4 from member 2. Changetype ADDED
Received an entry 110 with data of size 4 from member 2. Changetype ADDED
Received an entry 111 with data of size 4 from member 2. Changetype ADDED
Received an entry 112 with data of size 4 from member 2. Changetype ADDED
Received an entry 113 with data of size 4 from member 2. Changetype ADDED
Received an entry 114 with data of size 4 from member 2. Changetype ADDED
Received an entry 115 with data of size 4 from member 2. Changetype ADDED
Received an entry 116 with data of size 4 from member 2. Changetype ADDED
Received an entry 117 with data of size 4 from member 2. Changetype ADDED
Received an entry 118 with data of size 4 from member 2. Changetype ADDED
Received an entry 119 with data of size 4 from member 2. Changetype ADDED
Received an entry 120 with data of size 4 from member 2. Changetype ADDED
Received an entry 121 with data of size 4 from member 2. Changetype ADDED
Received an entry 122 with data of size 4 from member 2. Changetype ADDED
Received an entry 123 with data of size 4 from member 2. Changetype ADDED
Received an entry 125 with data of size 4 from member 2. Changetype ADDED
Received an entry 126 with data of size 4 from member 2. Changetype ADDED
Received an entry 127 with data of size 4 from member 2. Changetype ADDED
Received an entry 168 with data of size 4 from member 2. Changetype ADDED
Received an entry 171 with data of size 4 from member 2. Changetype ADDED
Received an entry 172 with data of size 4 from member 2. Changetype ADDED
Received an entry 173 with data of size 4 from member 2. Changetype ADDED
Received an entry 174 with data of size 4 from member 2. Changetype ADDED
Received an entry 175 with data of size 4 from member 2. Changetype ADDED
Received an entry 176 with data of size 4 from member 2. Changetype ADDED
Received an entry 177 with data of size 4 from member 2. Changetype ADDED
Received an entry 178 with data of size 4 from member 2. Changetype ADDED
Received an entry 179 with data of size 4 from member 2. Changetype ADDED
Received an entry 180 with data of size 4 from member 2. Changetype ADDED
Received an entry 181 with data of size 4 from member 2. Changetype ADDED
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
Pipe closed! Exiting.
Pipe closed! Exiting.
Segmentation fault (core dumped)

```

My phone doesn't throw up an error. And when I view the PC Suite sync log is says "Cancelled".

---

### Post by HyRax on 2008-03-17
Well, that&#347; a better result than what you had before - at least the sync is actually starting, and what we have here appears to be a runtime issue.

Your configuration that you posted before is fine - there´s nothing wrong with it, and proof of that is that the sync does start.

Does it bomb out at the same place each time?

I´m inclined to believe that the issue might be some bad data might have been passed, which causes OpenSync to crash. Your output suggests the phone is happily passing data to the PC, but the PC cannot pass data back to the phone.

The easiest troubleshooting method would be to start with a fresh mailbox - nothing, nada, zip. Sync that and see if everything on your phone comes down and populates your contacts and so forth in Evolution. If that works, make some changes on the Evolution side and sync again. If the changes pass back to the phone without any problem, then it´s a good bet that you´ve got some weird data in your actual Evolution mailbox that OpenSync can´t deal with for whatever reason. Then you can try disabling Contacts sync to see if the crash occurs again. If not, disable Calendar and try again, etc. Once you narrow it down to one container of data, then you can go through and find anything that might be classed as ¨unusual¨ in there, temporarily delete it, sync again. Lather, rinse, repeat until you have a clean sync.

Outside of that, you could have a look at the dumped core for clues. Install ¨pstack¨ if you haven´t already got it (type ¨sudo apt-get install pstack¨ at the terminal) and then after the crash, enter ¨pstack core¨ to have a look at what was dumped in the crash and post it here to see if we can get any clues (the core doesn´t usually give many clues, though).

---

### Post by christianxxx on 2008-03-17
I simply can't make my Gutsy-installation install OpenSync 0.21. It insists on installing the 0.19 version.
What I've done is to update the sources.list and sudo apt-get update. Then install. No change. Also tried to uninstall Opensync libraries and then install but still installs 0.19.
Any ideas?

Edit: I forgot to uninstall ALL the Opensync packages.. Now I've got that sorted out, but it still ends with a "System error" when syncing with my N95.

---

### Post by HyRax on 2008-03-17
Post your sync output - let´s have a look.

---

### Post by christianxxx on 2008-03-17
Here's the output from "msynctool --sync nokia"

```

Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-46DDAE6900000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000008 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000013 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000026 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000031 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000039 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000044 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000057 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4743176900000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47825CD200000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47AAFBAB00000003 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000003 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000010 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000018 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000025 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000032 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000047 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000054 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-474D723D00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000002 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000006 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000011 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000015 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000019 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000020 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000024 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000028 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000033 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000042 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000046 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47A9B63C00000002 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000051 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000055 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46EBE66E00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-474D734200000002 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-478281FB00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000037 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000005 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000009 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000012 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000016 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000023 with data of size 4 from member 1. Changetype ADDED
Received an reply to our Alert
Received an reply to our Alert
Received an entry pas-id-46DDAE6900000027 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000030 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000034 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000038 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000041 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000045 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000049 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000052 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000056 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-471C59B900000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47382E3B00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-473ED23B00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4785E8BE00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47A71A7600000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47ACA00B00000004 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47B69CF700000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000004 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000017 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000022 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000035 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000040 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000048 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000053 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-470BB5DE00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-475F19BE00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000007 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000014 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000021 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000029 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000036 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000043 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000050 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46EBE66E00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-474D6CA500000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47A8E45E00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-10@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-11@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T162729Z-5779-1000-1-1@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-0@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-1@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-2@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-3@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-6@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-13@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-14@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-15@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-16@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-17@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-18@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-20@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-22@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-23@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-24@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-25@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-30@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-8@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-26@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-28@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-29@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-31@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-32@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-33@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-35@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-36@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-37@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-12@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 8365871.1544561199450799996.JavaMail.adm-moff@moffice10.nsc.no with data of size 4 from member 1. Changetype ADDED
Received an entry 2E72A31AD95CF440932D44720C7CA69C02EE6B42@RHCL6020.ad.rikshospitalet.no with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-4@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 4C48242B7F82EE419F9B5B4BF88D310C3AEF1F1F0A@srv-win-exch-01.nokc.no with data of size 4 from member 1. Changetype ADDED
Received an entry 4C48242B7F82EE419F9B5B4BF88D310C3AEF1EACB7@srv-win-exch-01.nokc.no with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-21@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T162533Z-5779-1000-1-0@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 85720508.11021191229196722.JavaMail.adm-moff@moffice9.nsc.no with data of size 4 from member 1. Changetype ADDED
Received an entry !151351819-718456-V2@ejournal.mistral.mistralnett.com with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-27@silversurfer with data of size 4 from member 1. Changetype ADDED
Received an entry 20070904T191345Z-5729-1000-1-38@silversurfer with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.


```

It just sits there, wating for something, but since it results in a system error on the phone, I ctrl-c suspended it.

---

### Post by HyRax on 2008-03-17
Hmmm - OK, that was the exact behaviour the plagued OpenSync 0.19, and the upgrade to 0.21 fixed that.

I notice that the repository has now been updated to 0.22 and that´s the version you now get if my instructions are followed.

Under the assumption that 0.22 has broken something, I upgraded my own 0.21 installation to 0.22 and low and behold, my sync has borked itself. I´m not getting the Syntax Error like you are, however I am getting a broken pipe on the Ubuntu side -  half a sync and it bombs out - the output seems to suggest an issue with connecting to Evolution, however.

I´ll have to play with it for a bit and come back to you.

---

### Post by HyRax on 2008-03-17
Okies, something has changed with the Calendar and ToDo list syncs. I _cannot_ sync either of them, however I can sync just my Contacts without a problem. Test this for yourself by entering the following at a terminal:
```

$ msynctool --sync evolution-n95 --filter-objtype todo --filter-objtype event --filter-objtype note --slow-sync contact

```
The above line will filter everything except for data of type ¨Contact¨ and will force a slow sync of it.

If that works OK, test your Calendar only (nothing else) as follows:
```

$ msynctool --sync evolution-n95 --filter-objtype todo --filter-objtype contact --filter-objtype note --slow-sync event

```
If that works OK, finally test your ToDo list only as follows:
```

$ msynctool --sync evolution-n95 --filter-objtype contact --filter-objtype event --filter-objtype note --slow-sync todo

```
This way you can narrow down where your sync is having issues. I have yet to determine if I have some alien data in my ToDo´s or Calendar that is causing 0.22 to bork out, but that´s the next troubleshooting stage. :)

---

### Post by christianxxx on 2008-03-17
Ok, that was actually very helpful, although I don't fully understand the mechanics of the error.

It is the contacts that cause the error, output shown below. Tasks did produce an error on the Ubuntu-side, but the sync did complete without error on the phone.

```
Synchronizing group "nokia" [slow sync]
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-46DDAE6900000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000008 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000013 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000026 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000031 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000039 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000044 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000057 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4743176900000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47825CD200000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47AAFBAB00000003 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000003 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000010 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000018 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000025 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000032 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000047 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000054 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-474D723D00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000002 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000006 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000011 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000015 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000019 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000020 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000024 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000028 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000033 with data of size 4 from member 1. Changetype ADDED
Received an reply to our Alert
Received an entry pas-id-46DDAE690000003C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000042 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000046 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47A9B63C00000002 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000051 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000055 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46EBE66E00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-474D734200000002 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-478281FB00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000037 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000005 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000009 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000012 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000016 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000023 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000027 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000030 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000034 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000038 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000041 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000045 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000049 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000052 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000056 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-471C59B900000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47382E3B00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-473ED23B00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4785E8BE00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47A71A7600000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47ACA00B00000004 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47B69CF700000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000004 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000000D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000017 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000022 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002B with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000035 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000040 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000048 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000053 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-470BB5DE00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-475F19BE00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000007 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000014 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000001D with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000021 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000029 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000002A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000036 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000003F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000043 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE690000004C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46DDAE6900000050 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-46EBE66E00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-474D6CA500000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47A8E45E00000001 with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.

```

My untrained eye cannot see what causes the error. It manages to send a whole lot of data before it ends in error. From what I can see, the entries in both address books seems to be ok.
If I scratch my head any more now, I'll bleed...

---

### Post by HyRax on 2008-03-17
OK, this is confusing me a bit too - on one hand, I had a perfectly working sync that now does not work because of an upgrade from 0.21 to 0.22 of OpenSync where I determine that something has broken in Calendar and ToDos, however on the other hand you have your case where it is only the Contacts that do not sync! As the lesser of two evils, I´d prefer your situation!

I will simply have to play with this some more...

There are a number of major updates to OpenSync and the associated plugins that unfortunately require too many dependencies to be updated that currently do not have official Ubuntu versions (and I not prepared to butcher my system with manual installs of the Debian versions). With any luck, this will be made easier with the next release of Ubuntu which will probably carry these updates, and conversely, may fix many of our sync problems in the process!

---

### Post by christianxxx on 2008-03-18
Fortunately, that's just a month or so, and my problem is not critical or anything, it's just that I want my calendar and contacts to be replicated all over (work, n95 and home).

I never really got it working under Gutsy, so waiting for Hardy doesn't seem like an impossible thing to do. Still it's rather anoying, and I had a few glimpse of hope reading your post. :)

---

### Post by PryGuy on 2008-03-18
Nice! Will try it at home and report pack to you! Will it work with my Nokia N70 I wonder.

---

### Post by HyRax on 2008-03-18
> **PryGuy said:**
> Nice! Will try it at home and report pack to you! Will it work with my Nokia N70 I wonder.

Should do - any of the N-series Nokia´s should be able to use my guide here with about the only real differences being channel number, really. Please let us know how you go.

[quote=christianxxx]Fortunately, that's just a month or so, and my problem is not critical or anything, it's just that I want my calendar and contacts to be replicated all over (work, n95 and home).
[/quote]
Same here! Hopefully I can resolve it soon as I more or less live and die by my evolution calendar!
[quote=christianxxx]
I never really got it working under Gutsy, so waiting for Hardy doesn't seem like an impossible thing to do. Still it's rather anoying, and I had a few glimpse of hope reading your post.[/quote]
Well, thatt is indeed right - Hardy´s not too far away, but with any luck I can find some answers sooner.

---

### Post by atentik on 2008-03-26
I got mine working but it is only capable of synching Contacts ONLY. No Calendar or to-do list... Has anybody figured out how to work around it?

---

### Post by HyRax on 2008-03-26
That's the situation in my case too, and only happened when I ugpraded to OpenSync 0.22. The 0.21 version worked fine for me before.

I have not yet found a solution and am waiting for Hardy Heron before I do any more work on it again as newer versions of OpenSync require many new libraries that Gutsy presently does not have official support for.

---

### Post by atentik on 2008-03-27
I have been able to transfer Contact, Calendar, and To-Do to and from the N95 and Ubuntu. Here are the steps:
-On your N95, go to Tool->Sync->PC Suite->Edit sync profile->Connection settings. To note the version of PC suite you are using. Mine is version 1.1
-On your computer: Application->Accessaries->multisync0.90. Now click on edit to edit and select syncml-obex-client and make the settings to reflect the following: change "VV:VV:VV:VV:VV:VV" to reflect your phone's mac address
----------------------------------------------------------------
<config>
	<bluetooth_address>VV:VV:VV:VV:VV:VV </bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel>
	<interface>0</interface>
	<identifier>PC Suite</identifier>
	<version>[COLOR="Blue"]1.1[/COLOR]</version>
	<wbxml>[COLOR="Blue"]1.1[/COLOR]</wbxml>
	<username></username>
	<password></password>
	<type>2</type>
	<usestringtable>[COLOR="Lime"]2[/COLOR]</usestringtable>
	<onlyreplace>0</onlyreplace>
	<recvLimit>0</recvLimit>
	<maxObjSize>0</maxObjSize>
	<contact_db>Contacts</contact_db>
	<calendar_db>Calendar</calendar_db>
	<note_db></note_db>
</config>
The highlighted "blue" reflects the version 1.1 of my PC-Suit. The "lime" 2 retrieves calendar. You can change to 3 to get the to-do list as well.

---

### Post by HyRax on 2008-03-27
This is interesting. I tried it myself, but I'm still only successfully able to sync Contacts. On the other hand, however, my Calendar sync seems to proceed much further than before, before ultimately bombing out with the same "broken pipe" error. That's SOME progress, compared to before.

I noticed I also had the option for "Bluetooth 1.2", so I changed my settings to use that, but unfortunately I had the same error. Didn't fix anything for me.

Still, a nice find in trying to troubleshoot. I'll explore this one further when I have more time.

I am currently still of the belief that I might have a corrupt or unsupported data in my calendar that for whatever reason OpenSync doesn't like, but it will be too painstaking to sift through all my entries to figure out which one it might be (and that's assuming it IS a busted entry causing the problem). I might back up my calendar and then blank it out to see what happens.

---

### Post by atentik on 2008-03-27
Don't forget to install OBEX-FTP: "sudo apt-get install gnome-vfs-obexftp" I encountered few errors when until I install OBEX. Let us know if it works for you.

---

### Post by HyRax on 2008-03-27
FTP is for direct file transfers, which is not what a sync is. I've already got the OBEX FTP client installed for general Bluetooth file transfers.

In my case the error is saying
```

Member 2 of type syncml-obex-client had an error while getting changes: Broken Pipe

```
...which suggests that there is a transfer error occurring, not a connection error. This in itself suggests corrupted or unreadable/processable data. It only applies to the Calendar and ToDo list (in my case) because Contacts sync just fine by themselves.

Even though the error suggests the phone is at fault, I just now tried deleting my Evolution addressbook and allowed it to be recreated again from scratch. I tried to sync again but the same error popped up. I may have to move my calendar off my phone and start clean from both sides to really pinpoint where the cause of the problem is, and if after blanking both sides and I still get the error, then that suggests a problem with the 0.22 version of the software, but then why do Contacts work and nothing else?

Are you using OpenSync 0.22 with an N95 and a Gutsy install of Evolution? Anything different in your setup from a vanilla install?

---

### Post by atentik on 2008-03-28
I believe I'm using multisync0.90 ( I just followed the instruction you gave at the very first post (#1)). Installed all that was mentioned there and just like yourself, only the calendar was able to sync successfully. Then I went [here]("http://davehall.com.au/blog/dave/2007/11/18/my-new-toy-nokia-n95") and followed the instruction which is very much the same as yours. Then I when and did the modifications to reflect the suggestion I made in my earlier post.

---

### Post by HyRax on 2008-03-28
> **atentik said:**
> I believe I'm using multisync0.90.
Yeah, that's the version of MultiSync that gives you the tools for running the sync. I'm talking about the backend software that actually does the physical sync work, which is OpenSync. When I first wrote this, 0.21 was out. When you follow the same instruction, you'll now get 0.22 because it was updated in the meantime. A vanilla Ubuntu Gutsy install comes with 0.19.

If you followed my instruction in the last couple of weeks, then it is likely that you have 0.22 installed (even though the instruction makes you setup a repository called opensync-0.21 it brings down 0.22 instead).

---

### Post by atentik on 2008-03-28
I guess I'm using OpenSyn then. Did you follow the link I provided? Was it any useful? What version of n95 firmware do you have on your phone? i have the latest version upgraded v21. Maybe you'd have to update the version of the firmware. I'm not quit certain. Best of luck. Let us know how things go. I can't wait for someone to find a way of installing evolution 2.22 on Gutsy 7.10. I tried installing it on but it won't let me. It seems like it needs some packages in Gnome 2.22 to install ( these packages are ( i believe) in the next version of ubuntu (8.04). 
It has more features than the current edition. The current edition won't even allow me to change the color on my calendar. It is very terrible thus far. Let me know if you are able to install evolution 2.22 on your pc. 
Thanks

---

### Post by HyRax on 2008-03-28
> **atentik said:**
> I guess I'm using OpenSyn then. Did you follow the link I provided? Was it any useful?

Sorry, forgot to give you feedback on that - yes, I've seen that site before. When I began my own in-roads into syncing my N95, I came across that site and everything is sound on it. What is missing was the discrepancies between OpenSync 0.19 and 0.21 which once discovered, is what prompted me to do up my own HowTo. :)
> **atentik said:**
> What version of n95 firmware do you have on your phone? i have the latest version upgraded v21. Maybe you'd have to update the version of the firmware. I'm not quit certain.
When I first started, I had the older V11 firmware and everything was fine. I upgraded my N95 to V20.0.015 only 4 weeks ago and didn't have any new sync issues. I only upgraded to OpenSync 0.22 to investigate another poster's issues and bang - borked it. I don't think the firmware has anything to do with the issues at this stage.
> **atentik said:**
>  Best of luck. Let us know how things go. I can't wait for someone to find a way of installing evolution 2.22 on Gutsy 7.10. I tried installing it on but it won't let me. It seems like it needs some packages in Gnome 2.22 to install ( these packages are ( i believe) in the next version of ubuntu (8.04). 
It has more features than the current edition. The current edition won't even allow me to change the color on my calendar. It is very terrible thus far. Let me know if you are able to install evolution 2.22 on your pc. 
Thanks
Well, Hardy Heron is around the corner and that is what I'm presently waiting for as it will have support for the newer libraries that the newer versions of OpenSync require and with any luck, our sync problems disappear as if by magic. Yes, Hardy will also have Gnome 2.22, so you'll also get the new version of Evolution too! :) Can't wait - only about 26 days to go. Shame I don't have a spare N95 to play with (in case I bork my calendar), or I'd be downloading the Hardy Beta and be trying out the newer OpenSync on that.

---

### Post by olavjunior on 2008-03-29
I'm also getting the Broken Pipe error. I seem to have the 0.22 version, and also the latest firmware of n95. Let me know if you work this out! Kind of annoying. Do you think it will be easier with Hardy?

---

### Post by HyRax on 2008-03-29
> **olavjunior said:**
> I'm also getting the Broken Pipe error. I seem to have the 0.22 version, and also the latest firmware of n95. Let me know if you work this out! Kind of annoying. Do you think it will be easier with Hardy?
Well, I'm making some brutal assumptions, but yes - I'm hoping some of these problems are fixed in Hardy. The main issue is that the newer versions of OpenSync need newer supporting libraries which Gutsy does not have official support for (but Debian Etch does). I'm hoping (not expecting) that Hardy will have support for those newer libraries thus allowing us to use newer versions of OpenSync without the need to chop up your system with manually installed 3rd party libraries (too messy and opens the door to other potential problems).

---

### Post by olavjunior on 2008-04-19
Well, it works fine in Hardy.I''m getting an errorthough at the end, "Unable to write to one or more objects". The problem now is that on n95 all calender-entries get duplicated EVERYTIME! :S
The evolution stays fine though...Any ideas on how to avoid this?
I see it "recieving entries" on calender, and then just "syncronizing"...

---

### Post by HyRax on 2008-04-19
Cool stuff - no, I haven't tried Hardy yet. I toyed with the idea of downloading the Release Candidate yesterday, but I figured the Final release is due in just 4 days now, so I may as well wait a bit longer, then I'll have a proper go at it.

Meanwhile, my issues under Gutsy haven't changed - I can only sync Contacts and nothing else, even with a clean N95 and Evolution calendar!

---

### Post by HyRax on 2008-04-25
Well, day two of Hardy Heron being out and right out of the box, I have successfully synchronised my N95 and Evolution Mailbox & Calendar using the exact same configuration I had under Gutsy using the Hardy-supplied version of OpenSync (which is 0.22 - go figure). I'm using the 64-bit version of Hardy, but that shouldn't make any difference.

This was a fresh install of Hardy, not an upgrade. I then manually re-did the config as per my guide (rather than copy stuff across) and it worked first time, with only one doubled entry on the N95 out of about 100 or so updates. Sweet. :)

Tested both the command line msynctool and GUI MultiSync 0.90 tool. Both work just fine.

I also note that Bluetooth connectivity in general under Hardy has been *vaaaaaastly* improved too - simpler, faster and way cooler than the way MS Windows does it.

---

### Post by LonelyTraveler on 2008-04-26
Hi all,

I know this thread is for the Nokia N95, but I was hoping that someone can help me to sync my Nokia E61i.

I've tried KitchenSync that is actually for KDE, but getting the same error I'm getting when trying this guide.

I've tried the GUI and command line method. This is the error I get:

```
~$ msynctool --sync evolution-n95
Synchronizing group "evolution-n95" 
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error synchronizing: Unable to connect one of the members
Pipe closed! Exiting.
```

I'm running Hardy.

---

### Post by HyRax on 2008-04-26
> **LonelyTraveler said:**
> Hi all,

I know this thread is for the Nokia N95, but I was hoping that someone can help me to sync my Nokia E61i.

Hey, that's OK - the N95 is just an example - it should apply to just about any sync-capable Nokia. :)

Anyway, it appears your problem is Bluetooth related, not Sync related.

Are you able to perform any general file copying to/from your phone via Bluetooth? Are they paired correctly with both sides set to "authorised" (so you don't have to manually OK the connection request)? Have you added the *hciconfig hci0 inqmode 0* fix (workaround for a bug in Bluetooth) into your /etc/rc.local as the second-last line?

Once you can successfully transfer physical files to your phone and back, you are ready to do a sync.

---

### Post by LonelyTraveler on 2008-04-27
Hi Hyrax

I just checked if I can send files to my computer from my phone and found I can't. I used to be able to do this with Gutsy. I had a program in my accessories menu that I had to open in order to receive a file but can't find that in Hardy.

I checked the "receive file from remote devices" checkbox in my bluetooth preferences, but it still doesn't work.

Does my /etc/rc.local file have to look like this?:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
hciconfig hci0 inqmode 0
exit 0
```

After posting here last night, I found a website called ScheduleWorld.com Allows you to sync Evolution with the server and then sync your phone with the server too. Works great. But I still want to sort this normal way of syncing out too. Especially sending files to my computer from my phone.

I was wondering if it is possible to sync files too? Like with PDA's. Where it checks what file was last edited and syncs accordingly?

Thanks!

---

### Post by HyRax on 2008-04-27
> **LonelyTraveler said:**
> Hi Hyrax

I just checked if I can send files to my computer from my phone and found I can't. I used to be able to do this with Gutsy. I had a program in my accessories menu that I had to open in order to receive a file but can't find that in Hardy.

I checked the "receive file from remote devices" checkbox in my bluetooth preferences, but it still doesn't work.

Does my /etc/rc.local file have to look like this?:


Yes, that is correct. You might also want to refer to the Bluetooth connectivity guide _[color="Blue"][here](http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu)_[/color] which will guide you through Bluetooth setup again, but in a nutshell:

[list]
[*]Edit /etc/bluetooth/hcid.conf and change "security = user" to "security = auto" and change the PIN number from 1234 to your personal preference. Save and exit.
[*]Restart Bluetooth services with /etc/init.d/bluetooth restart
[*]Do the Bluetooth bug fix in your /etc/rc.local file (already done in your case).
[*]Make sure the Bluz-utils and Bluez-gnome packages are installed.
[*]Restart your PC (mostly for the rc.local fix to take effect).
[*]Initiate Bluetooth connection FROM your phone TO your PC. The phone will ask you for Ubuntu's PIN number. Ubuntu will also ask if you want to allow your phone to access it.
[*]Once done, when prompted, allow full authorisation for both Ubuntu and your phone so the PIN is not prompted for again in future.
[*]Ubuntu Hardy comes with all the OBEX FTP packages already installed, so no need to install anything else like you had to do with Gutsy to enable file transfers. Do a right-click on the Bluetooth icon in your system tray and Browse Device. Connect to your phone and you should be able to navigate the folders on it as per any normal disk device. Once you can do this, you can try syncing again.
[/list]

> **LonelyTraveler said:**
> 
After posting here last night, I found a website called ScheduleWorld.com Allows you to sync Evolution with the server and then sync your phone with the server too. Works great. But I still want to sort this normal way of syncing out too. Especially sending files to my computer from my phone.

Yeah, OpenSync just does the phone contacts and calendar, not files. If you want to sync files, I might suggest using RSync once you have a Bluetooth connection established. It will toss over only the changes in files you specify.
> **LonelyTraveler said:**
> 
I was wondering if it is possible to sync files too? Like with PDA's. Where it checks what file was last edited and syncs accordingly?

Unfortunately I am not really familiar with PDA's having shunned them in favour of a small laptop and my mobile :) however Google around and I'm sure you'll find something. I notice KDA users have KPilot, used for syncing Palm Pilots.

As for my recommendation of RSync, RSync does more than check last edited - it actually merges the physical changes in the file. It's intended for things like archiving, backup and is even used to mirror the Ubuntu archive server all around the world - very reliable app. It can work one way or bi-directionally. Ubuntu has it pre-installed.

---

### Post by LonelyTraveler on 2008-04-27
Thanks Hyrax,

I did what you said, but I still can't send anything to my computer. I am able to browse my phone from my computer though. I get a sending failed message everytime I try to send something to my computer. 

I will look into rsync after this is sorted out too. Thanks.

---

### Post by HyRax on 2008-04-27
> **LonelyTraveler said:**
> Thanks Hyrax,

I did what you said, but I still can't send anything to my computer. I am able to browse my phone from my computer though. I get a sending failed message everytime I try to send something to my computer. 

I will look into rsync after this is sorted out too. Thanks.
Can't send anything - you mean sync or file transfer? Remember that the sync is a function initiated by Ubuntu, NOT the phone. The phone is slave to Ubuntu. If you're referring to files, if you can browse, you most certainly should be able to transfer files. In the case of sending files FROM the phone, Ubuntu should prompt if you want to save it somewhere.

---

### Post by LonelyTraveler on 2008-04-27
I went through your howto again and got it working! Thanks a lot! Made a few duplicates but that fine. I'm not going to use this all the time, as I'm using ScheduleWorld. Going to try rsync just now.

---

### Post by HyRax on 2008-04-27
> **LonelyTraveler said:**
> I went through your howto again and got it working! Thanks a lot! Made a few duplicates but that fine. I'm not going to use this all the time, as I'm using ScheduleWorld. Going to try rsync just now.
Good stuff! Glad to help. :)

---

### Post by LonelyTraveler on 2008-04-27
Do you have any idea where my phone mounts when I browse the device? I'm trying out grsync, the gui version for rsync.

---

### Post by HyRax on 2008-04-27
> **LonelyTraveler said:**
> Do you have any idea where my phone mounts when I browse the device? I'm trying out grsync, the gui version for rsync.
[ObexFS](http://dev.zuckschwerdt.org/openobex/wiki/ObexFs) can probably help you out there. It mounts an ObexFTP device so that you can access it like any regular mounted volume.

Personally, I just use the USB lead for that - automatically mounted as a flash device (and because Bluetooth is too slow for large or numerous file transfers - I just use Bluetooth for small files and contacts/calendar sync).

---

### Post by LonelyTraveler on 2008-04-27
I don't know if I'm missing something on this website, but when I run "sudo mount -t fuse "obexfs#-b00:17:E6:08:B9:CC" /tmp/mnt" nothing happens. Can't find my phone mounted anywhere. But if I use the Browse device fuction it must be mounting somewhere right?

---

### Post by HyRax on 2008-04-27
> **LonelyTraveler said:**
> I don't know if I'm missing something on this website, but when I run "sudo mount -t fuse "obexfs#-b00:17:E6:08:B9:CC" /tmp/mnt" nothing happens. Can't find my phone mounted anywhere. But if I use the Browse device fuction it must be mounting somewhere right?
No, in Gnome, it utilises things like VFS to achieve connectivity which is different from mounted volumes.

Did you create the /tmp/mnt directory before mounting first? Without a directory to latch onto, the mount command can't do its work.

If you don't like the idea of creating empty directories that you might forget about later, consider using the RAM disk instead at /dev/shm, eg:

```

$ mkdir /dev/shm/myphone
$ sudo mount -t fuse "obexfs#-b00:17:E6:08:B9:CC -B6" /dev/shm/myphone

```

...should now make your mobile accessible at /dev/shm/myphone and when you reboot, the /dev/shm directory will be totally empty.

Outside of that, I can't really help you since I don't actually use ObexFS myself and is really going off-topic for this thread.

EDIT: Actually, make sure you are part of the FUSE group too, or you won't have permission to access FUSE-controlled devices.

---

### Post by LonelyTraveler on 2008-04-27
Just tried it but same thing. Thanks for the help. I'm sure I'll get it working.

---

### Post by pjalegria on 2008-04-27
Does it works with N6630???

---

### Post by PhonicLynx on 2008-04-27
Well it seems I am having that similar Calendar problem. One thing I've noticed which may or may not help is the categories section.

I have noticed that the birthdays got transfered.. but none of the calendar items before this date and time got transfered.

I added a few items just to test it to see how it goes and they appeared in evolution fine.

Is there any way to force it to put in the calendar entries before today's date / time?

---

### Post by HyRax on 2008-04-27
> **PhonicLynx said:**
> Is there any way to force it to put in the calendar entries before today's date / time?
That's very odd. I intentionally emptied my Evolution calendar to ensure that everything synced properly the first time, and it took all my entries before "today" that were on my phone and put them into my evolution calendar by default.

Try performing a "slow sync" with the *--slow-sync* parameter. The normal sync theoretically just searches for anything new and ignores existing data. A slow sync checks everything past, present and future.

---

### Post by quantumchicken on 2008-04-30
Hello, i hope someone can help me with this.

I have a Nokia N95, and i am trying to sync my exchange calendar.  Basically it wont.  I can sync contacts but not calendar entries.

I can sync personal calendars in evolution, but just not the exchange one.  I can add entries in evolution and they appear on the exchange server, but i just cant sync them with the N95.  No error appears on the sync program, but no calendar entries go from the N95 to the exchange server.

I tried using the sync program to just sync between calendars in evolution, i.e from personal to exchange, but it encountered an error.

This seems very strange, because i can access the exchange calendar and add events manually, just not sync to it.

Thanks,

Matt

---

### Post by HyRax on 2008-04-30
> **quantumchicken said:**
> 
This seems very strange, because i can access the exchange calendar and add events manually, just not sync to it.

I don't use Exchange myself, but if you have it added as another calendar in your Evolution client, then I would image it doesn't sync because you haven't told OpenSync to use it.

In step 2 of my guide, you have to tell it which books you want to sync:

```

<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

```

I can only assume you'll need to change this to additionally sync your exchange calendar, but I'd be weary syncing two separate calendars to one device - it will probably write back to the Evolution or Exchange calendar all the other calendar's entries!

---

### Post by quantumchicken on 2008-04-30
Hi Thanks for getting back to me so quickly.  I have told OpenSync to look for the exchange stuff, but it still doesn't work.  Could it be because of the security of the exchange server?

the config looks like this:


<?xml version="1.0"?>
<config>
  <address_path>exchange://username;auth=Basic@icex.imperial.ac.uk/;personal/Contacts</address_path>
  <calendar_path>exchange://username;auth=Basic@icex.imperial.ac.uk/;personal/Calendar</calendar_path>
  <tasks_path/>
</config>

it says that auth=Basic, could this be a problem?


Thanks again.

Matt

P.S i have changed the username here for security, but it does have my real username in the file.

---

### Post by HyRax on 2008-04-30
> **quantumchicken said:**
> Hi Thanks for getting back to me so quickly.  I have told OpenSync to look for the exchange stuff, but it still doesn't work.  Could it be because of the security of the exchange server?

I have absolutely no idea. I'm not an Exchange user, and the guide was for syncing with Evolution (I was originally under the impression you were syncing your Exchange data with Evolution and then from there to your phone) - I cannot say whether or not OpenSync will work with Exchange at all, as a quick Google suggests others are having similar issues. It seems to me that OpenSync is built more for Evolution than anything else.

Sorry!

---

### Post by quantumchicken on 2008-05-01
Ah i see.  Ok well thanks for all your help anyway.  I'm sure a solution will come up sooner or later.

I also have another little issue if i may :)

If i just sync my N95 with an evolution calendar on ubuntu hardy (fresh install) then i get duplicates on the phone, but not on evolution.  However if i try and sync it with hardy but this time updated from gusty (or whatever the last one was) then its fine.

I know there was some issues with duplicates, but i couldn't see whether it got resolved.

Thanks

Matt

---

### Post by HyRax on 2008-05-01
> **quantumchicken said:**
> 
If i just sync my N95 with an evolution calendar on ubuntu hardy (fresh install) then i get duplicates on the phone, but not on evolution.  However if i try and sync it with hardy but this time updated from gusty (or whatever the last one was) then its fine.

This seems to be hit or miss, and once synced a few times at the start, appears to settle down with most people. In my case, under Hardy I only every got one duplicate and it's been perfect ever since.

I typically find keeping updates confined to one side (ie: phone or Ubuntu and then sync) pretty much eliminates any chance of duplicates.

---

### Post by olavjunior on 2008-05-04
Well, the sucsess of this seems pretty random. Did a fresh install of Hardy now, and was unable to get this to work again. Now I'm only getting this error: 
> Member 2 of type syncml-obex-client had an error while connecting: Request not successfull: 67


---

### Post by HyRax on 2008-05-05
> **olavjunior said:**
> Well, the sucsess of this seems pretty random. Did a fresh install of Hardy now, and was unable to get this to work again. Now I'm only getting this error:
That error is caused by one of two issues: 1) you have another app running on your phone, so quit it, or 2) your Obex config in OpenSync is not right.

Most likely the latter is affecting you. I noticed that OpenSync in Hardy creates a more "elaborate" config file which doesn't seem to work! If you copy the config as shown from my original Gutsy guide, you should find it works perfectly.

---

### Post by olavjunior on 2008-05-05
Thanks for that. It did it, plus I thought I had to use version 2, but that didn't seem to be the case. But I'm not satisfied with it. I deleted some entries on the phone and told sync to take the phones side in conflicts, but still my phone got filled with 3 dups of every deleted appointment...

What's your experience on this? Do you consistently just create appointments in evolution? Or do you always take one side in conflicts?

EDIT: All these dups drive me crazy! I'm officially giving up on opensync! This is such ********! Sorry.. but I'm so annoied of all those hours I've spent with this unfinished peace of software.. Going to stick with goosync and google calandar, and just use Evolution as a calendar reader :o(

---

### Post by HyRax on 2008-05-05
Bummer, dude. :(

Admittedly during my issues under Gutsy, I did clean out my Evolution calendar and let my phone take control, so when I got Hardy going, there was really only one way to go. Since then, everything after that was been fine. On the initial sync, I only got a single doubled entry and none since.

I *do* do edits on both the phone and Evolution and in those rare times I get a conflict, I always go with "Newer" to resolve it. Seems to work fine. On occasion I get re-prompted for the same entry despite no changes since last sync, but after that second time, I never get prompted again until I actually change it again.

Outside of that, my only real issue is that any alarms I create don't get set as alarms on my phone or vice-versa, eg: there's the entry, there's the time for the appointment, but the alarm to remind you for it is not activated on the opposite side - I have to do that manually. Thankfully the N95 shows your up-coming appointments on the main-screen which I refer to all the time, so this is not majorly disasterous unless I lived and died by the calendar.

All up, yes, the software isn't perfect and still needs a LOT of work before it becomes a real PC Suite beater, but it seems to work reasonably well in my experience now.

You know, the only way you will know for sure is if you backup your calendar somewhere, blank out your phone and/or Evolution and sync from scratch. If you still have issues after that, then yeah - OpenSync isn't for you.

---

### Post by olavjunior on 2008-05-05
But I use a lot of recurring events. I believe I've read that there's a problem with recurring events? Or was that the google calendar integration?...
Maybe I'll try with clean sheets then...

But how do you clean out the evolution calendar? The choice to delete the calendar is greyed out

---

### Post by HyRax on 2008-05-06
> **olavjunior said:**
> But I use a lot of recurring events. I believe I've read that there's a problem with recurring events? Or was that the google calendar integration?...
Maybe I'll try with clean sheets then...

But how do you clean out the evolution calendar? The choice to delete the calendar is greyed out
My recurring events appear to be OK...

When I say "clean it out", I really mean "delete the bugger" and let it recreate it - it's in ~/.evolution/calendar :)

---

### Post by sbrunner on 2008-05-07
Hello !

I use this configuration:
```

<config>
<bluetooth_address>00:1F:00:B0:DB:55</bluetooth_address>
<bluetooth_channel>10</bluetooth_channel>
<interface>1</interface>
<identifier>PC Suite</identifier>
<version>2</version>
<wbxml>1</wbxml>
<username></username>
<password></password>
<type>2</type>
<usestringtable>0</usestringtable>
<onlyreplace>0</onlyreplace>
<recvLimit>0</recvLimit>
<maxObjSize>0</maxObjSize>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<note_db></note_db>
</config>

```
And I have this error message:
```

The previous synchronization was unclean. Slow-syncing
Member 2 of type kdepim-sync just connected
Member 1 of type syncml-obex-client had an error while connecting: Request not successfull: 67
Member 2 of type kdepim-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members

```
I don't understand what's the problem ?

Thanks in advance,
Stéphane Brunner.

---

### Post by HyRax on 2008-05-11
> **sbrunner said:**
> Hello !

I use this configuration:

<snip>

I don't understand what's the problem ?

The 67 error seems to stem from a bad config. Some suggestions to try (make a backup of your config first!):
[list]
[*]Try changing the MAC address of your phone to use lowercase letters (I don't actually know if it is case-sensitive or not, but I use lowercase, so it's a place to start).
[*]Change the Bluetooth version to 1.1 or 1.2 (you've got 2.0 specified) - it must match what your phone is set to.
[*]Try changing WBXML to 1.2 and UseStringTable to 3.
[/list]
This is the one I use with my Nokia N95:
```

<config>
  <bluetooth_address>00:11:22:aa:bb:cc</bluetooth_address>
  <bluetooth_channel>10</bluetooth_channel>
  <interface>0</interface>
  <identifier>PC Suite</identifier>
  <version>1.2</version>
  <wbxml>1.2</wbxml>
  <username></username>
  <password></password>
  <type>2</type>
  <usestringtable>3</usestringtable>
  <onlyreplace>0</onlyreplace>
  <recvLimit>0</recvLimit>
  <maxObjSize>0</maxObjSize>
  <contact_db>Contacts</contact_db>
  <calendar_db>Calendar</calendar_db>
  <note_db>Notes</note_db>
</config>

```

See how you go with that.

---

### Post by olavjunior on 2008-05-13
ok, deleted evolution (both tasks and cal) and nokia calender (and tasks), and got rid of all the old entries.  Wrote new entries (not using google cal entries) and all errors disappeared and no dupes were made. So I think I can live with this after all :)

---

### Post by uhappo on 2008-05-15
Ok, my Nokia N73 works great now. Here is info

```

<config>
  <bluetooth_address>MAC here</bluetooth_address>
  <bluetooth_channel>10</bluetooth_channel>
  <interface>0</interface>
  <identifier>PC Suite</identifier>
  <version>1</version>
  <wbxml>1.2</wbxml>
  <username></username>
  <password></password>
  <type>2</type>
  <usestringtable>3</usestringtable>
  <onlyLocaltime>1</onlyLocaltime>
  <onlyreplace>0</onlyreplace>
  <recvLimit>10000</recvLimit>
  <maxObjSize>50</maxObjSize>
  <contact_db>Contacts</contact_db>
  <calendar_db>Calendar</calendar_db>
  <note_db>Notes</note_db>
</config>

```

I use Hardy Heron, syncml obex client, evo2 sync, multisync0.90 and opensync 0.22

WUHUU!!!

---

### Post by olavjunior on 2008-05-24
Well, I thought it worked fine, but when it's gone a couple of days it all gets duplicated again. Now I've tried every possible settings for multisync, and I just can't get it to work probably. I really don't understand how it can be painless for you! Just gonna give it up I guess... .(

---

### Post by HyRax on 2008-05-24
Really?? Can't explain that one! The longest I've gone without a sync was about three days and when I returned, the sync worked as expected. Normally I sync about once a day - maybe I might leave it for a week and see what happens?

Admittedly I am fairly specific when I enter data into my phone, ie: new calendar entries are primarily done on the phone and new contacts are primarily done on Evolution (via new email contacts more than new phone numbers, really), so the chances of duplicates or version clashes should be virtually nil for me, but what you describe is totally different - you're getting duplicates after not syncing for a few days?? Has there been new data entered in that time? If so, what side?

---

### Post by olavjunior on 2008-05-25
Well, I believe it's the contacts that have f... up my syncs somehow. I struggled with multisync all day yesterday, with restoring backups in evo hundred times and deleting all data on phone. Because what happens is that eighter all contacts didn't get there in first sync, so all calender entries got duplicated on the second or vis versa. 

Really, I don't need to change a calendar entry, it just get duplicated, and not just one here and there, everyone! (not for contacts, that might happen to 10 % or so)

But now I've dropped the contacts sync, and I just synced (with no changes), and everything is fine :) So I really hope it will stay this way. I might live without the contacts...

---

### Post by HyRax on 2008-05-25
Might not have any real bearing on it (I'm plucking at straws here), but is the date & time correct (and in sync) with both your phone and PC? I update my phone via the mobile network and the PC updates via NTP - they are always within a second or two of each other.

I'm also going to leave my syncing for a week and see if I get similar issues.

---

### Post by olavjunior on 2008-05-25
I don't think it's the date that's the issue, since the entries are totally similar. But now I've made one sync entry in multisync for contacts and one for calendar, so I can sync them separately to keep it more simple (less errors). After the first contact sync my contakts went up with 10 %. So I deleted the dups, and re synced. Then everything was fine. So I'm gonna test this and see how it works out. So far so good :)

---

### Post by Kapteeni on 2008-06-05
I got the sync working in Hardy with these instructions, but it worked only once... 

```

Synchronizing group "evolution-n95"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-48400AE200000007 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-48400AE200000014 with data of size 4 from member 1. Changetype ADDED
...
Member 1 of type evo2-sync had an error while getting changes: Broken Pipe
Member 1 of type evo2-sync had an error while disconnecting: Broken Pipe
Received an entry 2 with data of size 4 from member 2. Changetype ADDED
Received an entry 3 with data of size 4 from member 2. Changetype ADDED
...
Member 2 of type syncml-obex-client just sent all changes
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error synchronizing: Unable to read from one of the members
Pipe closed! Exiting.

```

Any ideas?

---

### Post by HyRax on 2008-06-06
> **Kapteeni said:**
> I got the sync working in Hardy with these instructions, but it worked only once... 

Any ideas?
Try syncing only contacts or only calendar and see if the broken pipe still crops up.

---

### Post by cha_ha on 2008-06-08
hi,

i use the N95 with firmware-version V 21.0.016. Opensync-0.22. And msynctool-0.22. I can connect the phone an synchronize calendar and contacts, but i have the same strange effects as other users in this forum.

All my contacs are twice in my phone.I i delete the duplicates the next sync restore this.If i delete all contacts in my N95 and delete the duplicated entries in evolution it works with this command:
```
msynctool --sync N95 --filter-objtype todo --filter-objtype event --filter-objtype note --conflict n --slow-sync contact
```

My Calendar is strange to. Cause every sync adds a new (same) Version of all existing entries. Therefore after 4 sync's i have 4 identical entries. I don't know how this works.
If i delete all entries in my N95 and sync again the entries are correct. But only this time. Therefore i have to delete the hole calendar before i sync with evolution. This command i use to sync contacts:
```
msynctool --sync N95 --filter-objtype todo --filter-objtype event --filter-objtype note --conflict n --slow-sync contact
```

Has anbody an idea?

---

### Post by philidox on 2008-06-11
I was following your Howto and it get stop on the gui instruction on step number 5.  When I click on Add Member, there is a new window that appears but there is no selectable group there.  Please help.  I attach a screenshot to help out with my issue

---

### Post by HyRax on 2008-06-12
> **cha_ha said:**
> i use the N95 with firmware-version V 21.0.016. Opensync-0.22. And msynctool-0.22. I can connect the phone an synchronize calendar and contacts, but i have the same strange effects as other users in this forum.

Post up your OpenSync configuration and let's see if we can suss this out.
> **philidox said:**
> I was following your Howto and it get stop on the gui instruction on step number 5.  When I click on Add Member, there is a new window that appears but there is no selectable group there.  Please help.  I attach a screenshot to help out with my issue
OK, that snapshot is totally wrong - you *should* have some choices there.

Try completely uninstalling just multisync and its configuration files with:
```

$ sudo apt-get --purge remove multisync0.90

```
...then re-install it again with:
```

$ sudo apt-get install multisync0.90

```
...then open the Multisync app again to re-do your configuration and see if you get a list of choices in Step 5 again. You SHOULD see options like "Evolution 2.x" and "SyncML over OBEX client" listed.

If it's STILL blank, then delete the ".opensync-0.22" directory in your Home and try again. You might also want to consider using the terminal instructions to create the config files and then see if you can use the GUI after that.

---

### Post by philidox on 2008-06-12
If fixed my issue all I had to do was install the plugins via synaptic package manager.  I"m not gonna lie I just type in opensync in the search bar and installed anything and everything that had opensync in the name.  A lil excessive but it worked.  Thx alot.  However I have another question.  Everytime I hit refresh it gives me an error however I can see the bt connectivity on my phone and on ubuntu.  Which is far more progress than I've ever seen.  So I feel I'm almost there. I attach a screen shot.  Keep the ideas coming.  I get an "Error while connecting". Any ideas?  Will the channel that the bt is working thru make a huge difference if so how can I be sure that I"m using the right channel?

---

### Post by HyRax on 2008-06-13
You should have just followed the instructions for installing in the first place! ;)

Anyway, post up your configuration files - let's have a look.

---

### Post by Kapteeni on 2008-06-18
> **HyRax said:**
> Try syncing only contacts or only calendar and see if the broken pipe still crops up.

Contact sync works ok, but calendar is the one giving the broken pipe error.

---

### Post by Spyke on 2008-06-22
> **cha_ha said:**
> hi,
My Calendar is strange to. Cause every sync adds a new (same) Version of all existing entries. Therefore after 4 sync's i have 4 identical entries. I don't know how this works.


I had exactly the same problem with my phone. After looking at the configuration file for the syncML-bit, I changed

```
<onlyreplace>0</onlyreplace>
```

to

```
<onlyreplace>1</onlyreplace>
```

That seemed to solve that problem for me.

---

### Post by Styx on 2008-06-23
Hi all

I know it is a bit off topic but it would have helped me a lot so.
I have had a lot trouble getting my nokia 6233 to sync. I tried everything and every set up i could think of with the "SyncML over OBEX Client" plugin. 
Now the "Nokia (gnokii) Mobile Device" plugin did the magic. 
It saved me from going mad i think. 

So if you are encountering this:
```
Member 1 of type syncml-obex-client had an error while getting changes: Request not successfull: 64
```
it would be a good try to go for the gnokii plug in. 

It was easy to set up. 
I put this in the gnokii-sync configuration file used by multisync-qad:
```

<config>
  <connection>bluetooth</connection>
  <port>aa:bb:cc:dd:ee:ff</port>
  <model>6233</model>
</config>

```  

For me it just worked after I configured /home/user/.gnokiirc.
There is a example under/usr/share/doc/gnokii-common/sample/gnokiirc.gz. And you can try it with xgokii to see if it is working.

I am using Hardy and the repository versions of msync and the plugins that came with it.
I hope i save someone from going mad.
And sorry again for being a bit off topic

---

### Post by skyup on 2008-06-23
Could somebody help me?
I cannot sync Evolution with my Nokia N73 because of segmentation fault.

---

### Post by Styx on 2008-06-25
Pleas post the error output from the console and the configuration that you are using at the moment.

---

### Post by skyup on 2008-06-27
> **Styx said:**
> Pleas post the error output from the console and the configuration that you are using at the moment.

**This is my setting:**
```
<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>my MAC Address</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>10000</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>

```

**This is the output:**
```
skyuplam@skyuplam-labtop:~$ msynctool --sync Evolution-N73
Synchronizing group "Evolution-N73" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry 20080627T053725Z-7399-1000-1-0@skyuplam-labtop with data of size 4 from member 1. Changetype ADDED
Received an entry 20080623T042437Z-7213-1000-1-4@skyuplam-labtop with data of size 4 from member 1. Changetype ADDED
Received an entry 20080627T104528Z-7399-1000-1-1@skyuplam-labtop with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Going to receive 38 changes
Received an entry 2 with data of size 4 from member 2. Changetype ADDED
Received an entry 3 with data of size 4 from member 2. Changetype ADDED
Received an entry 4 with data of size 4 from member 2. Changetype ADDED
Received an entry 6 with data of size 4 from member 2. Changetype ADDED
Received an entry 7 with data of size 4 from member 2. Changetype ADDED
Received an entry 9 with data of size 4 from member 2. Changetype ADDED
Received an entry 10 with data of size 4 from member 2. Changetype ADDED
Received an entry 11 with data of size 4 from member 2. Changetype ADDED
Received an entry 12 with data of size 4 from member 2. Changetype ADDED
Received an entry 13 with data of size 4 from member 2. Changetype ADDED
Received an entry 14 with data of size 4 from member 2. Changetype ADDED
Received an entry 15 with data of size 4 from member 2. Changetype ADDED
Received an entry 16 with data of size 4 from member 2. Changetype ADDED
Received an entry 17 with data of size 4 from member 2. Changetype ADDED
Received an entry 18 with data of size 4 from member 2. Changetype ADDED
Received an entry 20 with data of size 4 from member 2. Changetype ADDED
Received an entry 21 with data of size 4 from member 2. Changetype ADDED
Received an entry 22 with data of size 4 from member 2. Changetype ADDED
Received an entry 23 with data of size 4 from member 2. Changetype ADDED
Received an entry 24 with data of size 4 from member 2. Changetype ADDED
Received an entry 25 with data of size 4 from member 2. Changetype ADDED
Received an entry 26 with data of size 4 from member 2. Changetype ADDED
Received an entry 27 with data of size 4 from member 2. Changetype ADDED
Received an entry 28 with data of size 4 from member 2. Changetype ADDED
Received an entry 29 with data of size 4 from member 2. Changetype ADDED
Received an entry 30 with data of size 4 from member 2. Changetype ADDED
Received an entry 31 with data of size 4 from member 2. Changetype ADDED
Received an entry 32 with data of size 4 from member 2. Changetype ADDED
Received an entry 33 with data of size 4 from member 2. Changetype ADDED
Received an entry 34 with data of size 4 from member 2. Changetype ADDED
Received an entry 35 with data of size 4 from member 2. Changetype ADDED
Received an entry 36 with data of size 4 from member 2. Changetype ADDED
Received an entry 37 with data of size 4 from member 2. Changetype ADDED
Received an entry 38 with data of size 4 from member 2. Changetype ADDED
Going to receive 325 changes
Received an entry 1 with data of size 4 from member 2. Changetype ADDED
Received an entry 2 with data of size 4 from member 2. Changetype ADDED
Received an entry 3 with data of size 4 from member 2. Changetype ADDED
Received an entry 4 with data of size 4 from member 2. Changetype ADDED
Received an entry 5 with data of size 4 from member 2. Changetype ADDED
Received an entry 6 with data of size 4 from member 2. Changetype ADDED
Received an entry 7 with data of size 4 from member 2. Changetype ADDED
Received an entry 8 with data of size 4 from member 2. Changetype ADDED
Received an entry 9 with data of size 4 from member 2. Changetype ADDED
Received an entry 10 with data of size 4 from member 2. Changetype ADDED
Received an entry 11 with data of size 4 from member 2. Changetype ADDED
Received an entry 12 with data of size 4 from member 2. Changetype ADDED
Received an entry 13 with data of size 4 from member 2. Changetype ADDED
Received an entry 14 with data of size 4 from member 2. Changetype ADDED
Received an entry 15 with data of size 4 from member 2. Changetype ADDED
Received an entry 16 with data of size 4 from member 2. Changetype ADDED
Received an entry 17 with data of size 4 from member 2. Changetype ADDED
Received an entry 18 with data of size 4 from member 2. Changetype ADDED
Received an entry 19 with data of size 4 from member 2. Changetype ADDED
Received an entry 20 with data of size 4 from member 2. Changetype ADDED
Received an entry 21 with data of size 4 from member 2. Changetype ADDED
Received an entry 22 with data of size 4 from member 2. Changetype ADDED
Received an entry 23 with data of size 4 from member 2. Changetype ADDED
Received an entry 24 with data of size 4 from member 2. Changetype ADDED
Received an entry 25 with data of size 4 from member 2. Changetype ADDED
Received an entry 26 with data of size 4 from member 2. Changetype ADDED
Received an entry 27 with data of size 4 from member 2. Changetype ADDED
Received an entry 28 with data of size 4 from member 2. Changetype ADDED
Received an entry 29 with data of size 4 from member 2. Changetype ADDED
Received an entry 30 with data of size 4 from member 2. Changetype ADDED
Received an entry 31 with data of size 4 from member 2. Changetype ADDED
Received an entry 32 with data of size 4 from member 2. Changetype ADDED
Received an entry 39 with data of size 4 from member 2. Changetype ADDED
Received an entry 40 with data of size 4 from member 2. Changetype ADDED
Received an entry 41 with data of size 4 from member 2. Changetype ADDED
Received an entry 42 with data of size 4 from member 2. Changetype ADDED
Received an entry 33 with data of size 4 from member 2. Changetype ADDED
Received an entry 34 with data of size 4 from member 2. Changetype ADDED
Received an entry 35 with data of size 4 from member 2. Changetype ADDED
Received an entry 36 with data of size 4 from member 2. Changetype ADDED
Received an entry 37 with data of size 4 from member 2. Changetype ADDED
Received an entry 38 with data of size 4 from member 2. Changetype ADDED
Received an entry 39 with data of size 4 from member 2. Changetype ADDED
Received an entry 40 with data of size 4 from member 2. Changetype ADDED
Received an entry 41 with data of size 4 from member 2. Changetype ADDED
Received an entry 42 with data of size 4 from member 2. Changetype ADDED
Received an entry 43 with data of size 4 from member 2. Changetype ADDED
Received an entry 44 with data of size 4 from member 2. Changetype ADDED
Received an entry 45 with data of size 4 from member 2. Changetype ADDED
Received an entry 46 with data of size 4 from member 2. Changetype ADDED
Received an entry 47 with data of size 4 from member 2. Changetype ADDED
Received an entry 48 with data of size 4 from member 2. Changetype ADDED
Received an entry 49 with data of size 4 from member 2. Changetype ADDED
Received an entry 50 with data of size 4 from member 2. Changetype ADDED
Received an entry 51 with data of size 4 from member 2. Changetype ADDED
Received an entry 52 with data of size 4 from member 2. Changetype ADDED
Received an entry 53 with data of size 4 from member 2. Changetype ADDED
Received an entry 54 with data of size 4 from member 2. Changetype ADDED
Received an entry 55 with data of size 4 from member 2. Changetype ADDED
Received an entry 56 with data of size 4 from member 2. Changetype ADDED
Received an entry 57 with data of size 4 from member 2. Changetype ADDED
Received an entry 58 with data of size 4 from member 2. Changetype ADDED
Received an entry 59 with data of size 4 from member 2. Changetype ADDED
Received an entry 60 with data of size 4 from member 2. Changetype ADDED
Received an entry 61 with data of size 4 from member 2. Changetype ADDED
Received an entry 62 with data of size 4 from member 2. Changetype ADDED
Received an entry 63 with data of size 4 from member 2. Changetype ADDED
Received an entry 64 with data of size 4 from member 2. Changetype ADDED
Received an entry 65 with data of size 4 from member 2. Changetype ADDED
Received an entry 66 with data of size 4 from member 2. Changetype ADDED
Received an entry 67 with data of size 4 from member 2. Changetype ADDED
Received an entry 68 with data of size 4 from member 2. Changetype ADDED
Received an entry 69 with data of size 4 from member 2. Changetype ADDED
Received an entry 70 with data of size 4 from member 2. Changetype ADDED
Received an entry 71 with data of size 4 from member 2. Changetype ADDED
Received an entry 72 with data of size 4 from member 2. Changetype ADDED
Received an entry 73 with data of size 4 from member 2. Changetype ADDED
Received an entry 74 with data of size 4 from member 2. Changetype ADDED
Received an entry 75 with data of size 4 from member 2. Changetype ADDED
Received an entry 76 with data of size 4 from member 2. Changetype ADDED
Received an entry 77 with data of size 4 from member 2. Changetype ADDED
Received an entry 78 with data of size 4 from member 2. Changetype ADDED
Received an entry 79 with data of size 4 from member 2. Changetype ADDED
Received an entry 80 with data of size 4 from member 2. Changetype ADDED
Received an entry 81 with data of size 4 from member 2. Changetype ADDED
Received an entry 82 with data of size 4 from member 2. Changetype ADDED
Received an entry 83 with data of size 4 from member 2. Changetype ADDED
Received an entry 84 with data of size 4 from member 2. Changetype ADDED
Received an entry 85 with data of size 4 from member 2. Changetype ADDED
Received an entry 86 with data of size 4 from member 2. Changetype ADDED
Received an entry 87 with data of size 4 from member 2. Changetype ADDED
Received an entry 88 with data of size 4 from member 2. Changetype ADDED
Received an entry 89 with data of size 4 from member 2. Changetype ADDED
Received an entry 90 with data of size 4 from member 2. Changetype ADDED
Received an entry 91 with data of size 4 from member 2. Changetype ADDED
Received an entry 92 with data of size 4 from member 2. Changetype ADDED
Received an entry 93 with data of size 4 from member 2. Changetype ADDED
Received an entry 94 with data of size 4 from member 2. Changetype ADDED
Received an entry 95 with data of size 4 from member 2. Changetype ADDED
Received an entry 96 with data of size 4 from member 2. Changetype ADDED
Received an entry 97 with data of size 4 from member 2. Changetype ADDED
Received an entry 98 with data of size 4 from member 2. Changetype ADDED
Received an entry 99 with data of size 4 from member 2. Changetype ADDED
Received an entry 100 with data of size 4 from member 2. Changetype ADDED
Received an entry 101 with data of size 4 from member 2. Changetype ADDED
Received an entry 102 with data of size 4 from member 2. Changetype ADDED
Received an entry 103 with data of size 4 from member 2. Changetype ADDED
Received an entry 104 with data of size 4 from member 2. Changetype ADDED
Received an entry 105 with data of size 4 from member 2. Changetype ADDED
Received an entry 106 with data of size 4 from member 2. Changetype ADDED
Received an entry 107 with data of size 4 from member 2. Changetype ADDED
Received an entry 108 with data of size 4 from member 2. Changetype ADDED
Received an entry 109 with data of size 4 from member 2. Changetype ADDED
Received an entry 110 with data of size 4 from member 2. Changetype ADDED
Received an entry 111 with data of size 4 from member 2. Changetype ADDED
Received an entry 112 with data of size 4 from member 2. Changetype ADDED
Received an entry 113 with data of size 4 from member 2. Changetype ADDED
Received an entry 114 with data of size 4 from member 2. Changetype ADDED
Received an entry 115 with data of size 4 from member 2. Changetype ADDED
Received an entry 116 with data of size 4 from member 2. Changetype ADDED
Received an entry 117 with data of size 4 from member 2. Changetype ADDED
Received an entry 118 with data of size 4 from member 2. Changetype ADDED
Received an entry 119 with data of size 4 from member 2. Changetype ADDED
Received an entry 120 with data of size 4 from member 2. Changetype ADDED
Received an entry 121 with data of size 4 from member 2. Changetype ADDED
Received an entry 122 with data of size 4 from member 2. Changetype ADDED
Received an entry 123 with data of size 4 from member 2. Changetype ADDED
Received an entry 124 with data of size 4 from member 2. Changetype ADDED
Received an entry 125 with data of size 4 from member 2. Changetype ADDED
Received an entry 126 with data of size 4 from member 2. Changetype ADDED
Received an entry 127 with data of size 4 from member 2. Changetype ADDED
Received an entry 128 with data of size 4 from member 2. Changetype ADDED
Received an entry 129 with data of size 4 from member 2. Changetype ADDED
Received an entry 130 with data of size 4 from member 2. Changetype ADDED
Received an entry 131 with data of size 4 from member 2. Changetype ADDED
Received an entry 132 with data of size 4 from member 2. Changetype ADDED
Received an entry 133 with data of size 4 from member 2. Changetype ADDED
Received an entry 134 with data of size 4 from member 2. Changetype ADDED
Received an entry 135 with data of size 4 from member 2. Changetype ADDED
Received an entry 136 with data of size 4 from member 2. Changetype ADDED
Received an entry 137 with data of size 4 from member 2. Changetype ADDED
Received an entry 138 with data of size 4 from member 2. Changetype ADDED
Received an entry 139 with data of size 4 from member 2. Changetype ADDED
Received an entry 140 with data of size 4 from member 2. Changetype ADDED
Received an entry 141 with data of size 4 from member 2. Changetype ADDED
Received an entry 142 with data of size 4 from member 2. Changetype ADDED
Received an entry 143 with data of size 4 from member 2. Changetype ADDED
Received an entry 144 with data of size 4 from member 2. Changetype ADDED
Received an entry 145 with data of size 4 from member 2. Changetype ADDED
Received an entry 146 with data of size 4 from member 2. Changetype ADDED
Received an entry 147 with data of size 4 from member 2. Changetype ADDED
Received an entry 148 with data of size 4 from member 2. Changetype ADDED
Received an entry 149 with data of size 4 from member 2. Changetype ADDED
Received an entry 150 with data of size 4 from member 2. Changetype ADDED
Received an entry 151 with data of size 4 from member 2. Changetype ADDED
Received an entry 152 with data of size 4 from member 2. Changetype ADDED
Received an entry 153 with data of size 4 from member 2. Changetype ADDED
Received an entry 154 with data of size 4 from member 2. Changetype ADDED
Received an entry 155 with data of size 4 from member 2. Changetype ADDED
Received an entry 156 with data of size 4 from member 2. Changetype ADDED
Received an entry 157 with data of size 4 from member 2. Changetype ADDED
Received an entry 158 with data of size 4 from member 2. Changetype ADDED
Received an entry 159 with data of size 4 from member 2. Changetype ADDED
Received an entry 160 with data of size 4 from member 2. Changetype ADDED
Received an entry 161 with data of size 4 from member 2. Changetype ADDED
Received an entry 162 with data of size 4 from member 2. Changetype ADDED
Received an entry 163 with data of size 4 from member 2. Changetype ADDED
Received an entry 164 with data of size 4 from member 2. Changetype ADDED
Received an entry 165 with data of size 4 from member 2. Changetype ADDED
Received an entry 166 with data of size 4 from member 2. Changetype ADDED
Received an entry 167 with data of size 4 from member 2. Changetype ADDED
Received an entry 168 with data of size 4 from member 2. Changetype ADDED
Received an entry 169 with data of size 4 from member 2. Changetype ADDED
Received an entry 170 with data of size 4 from member 2. Changetype ADDED
Received an entry 171 with data of size 4 from member 2. Changetype ADDED
Received an entry 172 with data of size 4 from member 2. Changetype ADDED
Received an entry 173 with data of size 4 from member 2. Changetype ADDED
Received an entry 174 with data of size 4 from member 2. Changetype ADDED
Received an entry 175 with data of size 4 from member 2. Changetype ADDED
Received an entry 176 with data of size 4 from member 2. Changetype ADDED
Received an entry 177 with data of size 4 from member 2. Changetype ADDED
Received an entry 178 with data of size 4 from member 2. Changetype ADDED
Received an entry 179 with data of size 4 from member 2. Changetype ADDED
Received an entry 180 with data of size 4 from member 2. Changetype ADDED
Received an entry 181 with data of size 4 from member 2. Changetype ADDED
Received an entry 182 with data of size 4 from member 2. Changetype ADDED
Received an entry 183 with data of size 4 from member 2. Changetype ADDED
Received an entry 184 with data of size 4 from member 2. Changetype ADDED
Received an entry 185 with data of size 4 from member 2. Changetype ADDED
Received an entry 186 with data of size 4 from member 2. Changetype ADDED
Received an entry 187 with data of size 4 from member 2. Changetype ADDED
Received an entry 188 with data of size 4 from member 2. Changetype ADDED
Received an entry 189 with data of size 4 from member 2. Changetype ADDED
Received an entry 190 with data of size 4 from member 2. Changetype ADDED
Received an entry 191 with data of size 4 from member 2. Changetype ADDED
Received an entry 192 with data of size 4 from member 2. Changetype ADDED
Received an entry 193 with data of size 4 from member 2. Changetype ADDED
Received an entry 194 with data of size 4 from member 2. Changetype ADDED
Received an entry 195 with data of size 4 from member 2. Changetype ADDED
Received an entry 196 with data of size 4 from member 2. Changetype ADDED
Received an entry 197 with data of size 4 from member 2. Changetype ADDED
Received an entry 198 with data of size 4 from member 2. Changetype ADDED
Received an entry 199 with data of size 4 from member 2. Changetype ADDED
Received an entry 200 with data of size 4 from member 2. Changetype ADDED
Received an entry 201 with data of size 4 from member 2. Changetype ADDED
Received an entry 202 with data of size 4 from member 2. Changetype ADDED
Received an entry 203 with data of size 4 from member 2. Changetype ADDED
Received an entry 204 with data of size 4 from member 2. Changetype ADDED
Received an entry 205 with data of size 4 from member 2. Changetype ADDED
Received an entry 206 with data of size 4 from member 2. Changetype ADDED
Received an entry 207 with data of size 4 from member 2. Changetype ADDED
Received an entry 208 with data of size 4 from member 2. Changetype ADDED
Received an entry 209 with data of size 4 from member 2. Changetype ADDED
Received an entry 210 with data of size 4 from member 2. Changetype ADDED
Received an entry 211 with data of size 4 from member 2. Changetype ADDED
Received an entry 212 with data of size 4 from member 2. Changetype ADDED
Received an entry 213 with data of size 4 from member 2. Changetype ADDED
Received an entry 214 with data of size 4 from member 2. Changetype ADDED
Received an entry 215 with data of size 4 from member 2. Changetype ADDED
Received an entry 216 with data of size 4 from member 2. Changetype ADDED
Received an entry 217 with data of size 4 from member 2. Changetype ADDED
Received an entry 218 with data of size 4 from member 2. Changetype ADDED
Received an entry 219 with data of size 4 from member 2. Changetype ADDED
Received an entry 220 with data of size 4 from member 2. Changetype ADDED
Received an entry 221 with data of size 4 from member 2. Changetype ADDED
Received an entry 222 with data of size 4 from member 2. Changetype ADDED
Received an entry 223 with data of size 4 from member 2. Changetype ADDED
Received an entry 224 with data of size 4 from member 2. Changetype ADDED
Received an entry 225 with data of size 4 from member 2. Changetype ADDED
Received an entry 226 with data of size 4 from member 2. Changetype ADDED
Received an entry 227 with data of size 4 from member 2. Changetype ADDED
Received an entry 228 with data of size 4 from member 2. Changetype ADDED
Received an entry 229 with data of size 4 from member 2. Changetype ADDED
Received an entry 230 with data of size 4 from member 2. Changetype ADDED
Received an entry 231 with data of size 4 from member 2. Changetype ADDED
Received an entry 232 with data of size 4 from member 2. Changetype ADDED
Received an entry 233 with data of size 4 from member 2. Changetype ADDED
Received an entry 234 with data of size 4 from member 2. Changetype ADDED
Received an entry 235 with data of size 4 from member 2. Changetype ADDED
Received an entry 236 with data of size 4 from member 2. Changetype ADDED
Received an entry 237 with data of size 4 from member 2. Changetype ADDED
Received an entry 238 with data of size 4 from member 2. Changetype ADDED
Received an entry 239 with data of size 4 from member 2. Changetype ADDED
Received an entry 240 with data of size 4 from member 2. Changetype ADDED
Received an entry 241 with data of size 4 from member 2. Changetype ADDED
Received an entry 242 with data of size 4 from member 2. Changetype ADDED
Received an entry 243 with data of size 4 from member 2. Changetype ADDED
Received an entry 244 with data of size 4 from member 2. Changetype ADDED
Received an entry 245 with data of size 4 from member 2. Changetype ADDED
Received an entry 246 with data of size 4 from member 2. Changetype ADDED
Received an entry 247 with data of size 4 from member 2. Changetype ADDED
Received an entry 248 with data of size 4 from member 2. Changetype ADDED
Received an entry 249 with data of size 4 from member 2. Changetype ADDED
Received an entry 250 with data of size 4 from member 2. Changetype ADDED
Received an entry 251 with data of size 4 from member 2. Changetype ADDED
Received an entry 252 with data of size 4 from member 2. Changetype ADDED
Received an entry 253 with data of size 4 from member 2. Changetype ADDED
Received an entry 254 with data of size 4 from member 2. Changetype ADDED
Received an entry 255 with data of size 4 from member 2. Changetype ADDED
Received an entry 256 with data of size 4 from member 2. Changetype ADDED
Received an entry 257 with data of size 4 from member 2. Changetype ADDED
Received an entry 258 with data of size 4 from member 2. Changetype ADDED
Received an entry 259 with data of size 4 from member 2. Changetype ADDED
Received an entry 260 with data of size 4 from member 2. Changetype ADDED
Received an entry 261 with data of size 4 from member 2. Changetype ADDED
Received an entry 262 with data of size 4 from member 2. Changetype ADDED
Received an entry 263 with data of size 4 from member 2. Changetype ADDED
Received an entry 264 with data of size 4 from member 2. Changetype ADDED
Received an entry 265 with data of size 4 from member 2. Changetype ADDED
Received an entry 266 with data of size 4 from member 2. Changetype ADDED
Received an entry 267 with data of size 4 from member 2. Changetype ADDED
Received an entry 268 with data of size 4 from member 2. Changetype ADDED
Received an entry 269 with data of size 4 from member 2. Changetype ADDED
Received an entry 270 with data of size 4 from member 2. Changetype ADDED
Received an entry 271 with data of size 4 from member 2. Changetype ADDED
Received an entry 272 with data of size 4 from member 2. Changetype ADDED
Received an entry 273 with data of size 4 from member 2. Changetype ADDED
Received an entry 274 with data of size 4 from member 2. Changetype ADDED
Received an entry 275 with data of size 4 from member 2. Changetype ADDED
Received an entry 276 with data of size 4 from member 2. Changetype ADDED
Received an entry 277 with data of size 4 from member 2. Changetype ADDED
Received an entry 278 with data of size 4 from member 2. Changetype ADDED
Received an entry 279 with data of size 4 from member 2. Changetype ADDED
Received an entry 280 with data of size 4 from member 2. Changetype ADDED
Received an entry 281 with data of size 4 from member 2. Changetype ADDED
Received an entry 282 with data of size 4 from member 2. Changetype ADDED
Received an entry 283 with data of size 4 from member 2. Changetype ADDED
Received an entry 284 with data of size 4 from member 2. Changetype ADDED
Received an entry 285 with data of size 4 from member 2. Changetype ADDED
Received an entry 286 with data of size 4 from member 2. Changetype ADDED
Received an entry 287 with data of size 4 from member 2. Changetype ADDED
Received an entry 289 with data of size 4 from member 2. Changetype ADDED
Received an entry 290 with data of size 4 from member 2. Changetype ADDED
Received an entry 291 with data of size 4 from member 2. Changetype ADDED
Received an entry 292 with data of size 4 from member 2. Changetype ADDED
Received an entry 293 with data of size 4 from member 2. Changetype ADDED
Received an entry 294 with data of size 4 from member 2. Changetype ADDED
Received an entry 295 with data of size 4 from member 2. Changetype ADDED
Received an entry 296 with data of size 4 from member 2. Changetype ADDED
Received an entry 297 with data of size 4 from member 2. Changetype ADDED
Received an entry 298 with data of size 4 from member 2. Changetype ADDED
Received an entry 299 with data of size 4 from member 2. Changetype ADDED
Received an entry 300 with data of size 4 from member 2. Changetype ADDED
Received an entry 301 with data of size 4 from member 2. Changetype ADDED
Received an entry 302 with data of size 4 from member 2. Changetype ADDED
Received an entry 303 with data of size 4 from member 2. Changetype ADDED
Received an entry 304 with data of size 4 from member 2. Changetype ADDED
Received an entry 305 with data of size 4 from member 2. Changetype ADDED
Received an entry 306 with data of size 4 from member 2. Changetype ADDED
Received an entry 307 with data of size 4 from member 2. Changetype ADDED
Received an entry 308 with data of size 4 from member 2. Changetype ADDED
Received an entry 309 with data of size 4 from member 2. Changetype ADDED
Received an entry 310 with data of size 4 from member 2. Changetype ADDED
Received an entry 311 with data of size 4 from member 2. Changetype ADDED
Received an entry 312 with data of size 4 from member 2. Changetype ADDED
Received an entry 313 with data of size 4 from member 2. Changetype ADDED
Received an entry 314 with data of size 4 from member 2. Changetype ADDED
Received an entry 315 with data of size 4 from member 2. Changetype ADDED
Received an entry 316 with data of size 4 from member 2. Changetype ADDED
Received an entry 317 with data of size 4 from member 2. Changetype ADDED
Received an entry 318 with data of size 4 from member 2. Changetype ADDED
Received an entry 319 with data of size 4 from member 2. Changetype ADDED
Received an entry 320 with data of size 4 from member 2. Changetype ADDED
Received an entry 321 with data of size 4 from member 2. Changetype ADDED
Received an entry 322 with data of size 4 from member 2. Changetype ADDED
Received an entry 323 with data of size 4 from member 2. Changetype ADDED
Received an entry 324 with data of size 4 from member 2. Changetype ADDED
Received an entry 325 with data of size 4 from member 2. Changetype ADDED
Received an entry 326 with data of size 4 from member 2. Changetype ADDED
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
Segmentation fault
Pipe closed! Exiting.
Pipe closed! Exiting.

```

---

### Post by texadactyl on 2008-07-07
HyRax and Happo - I noticed that you both are using this setting now:

<note_db>Notes</note_db>

Does that mean that you are both syncing Evolution notes successfully with the N95?

My unit is on the way from an eBay seller.

Thanks...Richard

---

### Post by cszikszoy on 2008-07-08
ToDo notes sync works fine with my N73.  I'm sure it'll work with the N95.

---

### Post by HyRax on 2008-07-08
> **lemon8h8ead said:**
> HyRax and Happo - I noticed that you both are using this setting now:

<note_db>Notes</note_db>

Does that mean that you are both syncing Evolution notes successfully with the N95?

No, I'm not using Notes at all, hence it's safe for me to leave that config option on as there's no notes to sync.

Mind you, I haven't tried syncing Notes in the current release. Previous releases would either hang or bork.

---

### Post by MarcGammon on 2008-07-28
Member 1 of type evo2-sync had an error while getting changes: Broken Pipe


I have managed to get Calendar sync working between Hardy and my Nokia N80 over Bluetooth.  The "Broken Pipe" error, for my setup, was always with "Member 1", which was the Evolution connection, not the phone.  I could not work out what was happening but have worked around it by creating a new calendar in Evolution.  I then made this the default calendar so that my appointments land up in this calendar rather than in the "Personal" calendar.  Then, in multisync0.90, I could specify the new calendar by name, and the "Broken Pipe" error then goes away.  
For completeness (for the N80 phone), my syncml-obex-client config is
[FONT="Courier New"]

<?xml version="1.0"?>
<config>
  <bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
  <bluetooth_channel>10</bluetooth_channel>
  <interface>0</interface>
  <identifier>PC Suite</identifier>
  <version>1</version>
  <wbxml>1</wbxml>
  <username></username>
  <password></password>
  <type>2</type>
  <usestringtable>1</usestringtable>
  <onlyreplace>0</onlyreplace>
  <onlyLocaltime>0</onlyLocaltime>
  <recvLimit>0</recvLimit>
  <maxObjSize>0</maxObjSize>
  <contact_db>Contacts</contact_db>
  <calendar_db>Calendar</calendar_db>
  <note_db>Notes</note_db>
</config>
[/FONT]
I hope this helps others.

---

### Post by leandir on 2008-08-31
Nokia N70, and I am stuck at the "Bluetooth connection problem" :-( I have already followed all the instructions contained in this thread, to no avail. Here is the error message: 

```
luca@luca-laptop:~$ msynctool --sync nokia
Synchronizing group "Nokia" 
The previous synchronization was unclean. Slow-syncing
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
Member 1 of type evo2-sync just connected
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error synchronizing: Unable to connect one of the members
Pipe closed! Exiting.
luca@luca-laptop:~$ Pipe closed! Exiting.
```

Here is instead the configuration in multisync-qad:

```
<config>
  <bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
  <bluetooth_channel>10</bluetooth_channel>
  <interface>0</interface>
  <identifier>PC Suite</identifier>
  <version>1</version>
  <wbxml>1</wbxml>
  <username></username>
  <password></password>
  <type>2</type>
  <usestringtable>3</usestringtable>
  <onlyLocaltime>1</onlyLocaltime>
  <onlyreplace></onlyreplace>
  <recvLimit>10000</recvLimit>
  <maxObjSize>50</maxObjSize>
  <contact_db>Contacts</contact_db>
  <calendar_db>Calendar</calendar_db>
  <note_db>Notes</note_db>
</config>
```

I am unable to browse the phone through bluetooth, but sending/receiving files works like a charm. Using standard opensync and multisync for hardy, clean installation. I already tried to purge and reinstall everything sync-related, though. This is especially buggering since some days ago I succeeded in making it sync ... had a kind of disaster on my box and had to reinstall everything though, so I am stuck here again.

---

### Post by leandir on 2008-08-31
Victory! I was finally able to sync everything but Notes (I DO hope they will implement this in Evolution, considering that KDE does it perfectly fine - albeit it creates doubles every time). In any case, the final code...

```
<config>
<username></username>
<password></password>
<type>2</type>
<bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
<bluetooth_channel>11</bluetooth_channel>
<interface>0</interface>
<version>1</version>
<identifier>PC Suite</identifier>
<wbxml>1</wbxml>
<recvLimit>1</recvLimit>
<maxObjSize>1</maxObjSize>
<usestringtable>1</usestringtable>
<onlyreplace>0</onlyreplace>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<note_db>Notes</note_db>
</config>
```

It was absolutely vital to reboot the phone after the pairing was established, however. Dunno why :-)

Now I am again a happy cellphone user :guitar:

---

### Post by brendo8686 on 2008-09-02
Hey all theres an extreemly new mobile phone out from nokia that costs $3.450!! lol im serious. It can use the camera to read and speak back to you [http://mobilephoneblogaroo.wordpress.com](http://mobilephoneblogaroo.wordpress.com)

---

### Post by olavjunior on 2008-09-08
Well, I've been struggeling with multisync for a long time now. Sometimes it work, and sometimes it doesn't. What buggs me now is that some appointments made in Evolution doesn't get synced over to my Nokia. It just says Sync Successful, without nothing changed. 

My config is:

```

<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>XX:XX:XX:XX:XX</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db></note_db>
</config>

```

---

### Post by martron88 on 2008-09-09
I've been fighting with duplicate calendar and tasks appearing in my n95 all day.  I've got my multisync profile set up like most of you.

For reference:
```
<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1.1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>

```

So, after hours of wrangling, I've figured out that syncML just doesn't like unsuccessful synchronizations.  Whenever an error code 500 would turn up within the sync process, all of my events and tasks would be effectively duplicated on the n95.

So, I managed to eventually find the offending entry.  It was a task.  Evolution seems to be trying to put timezone information into task due dates and syncML/n95 doesn't like it.  So, my solution for now is no due dates on To-do items.

To provide an example:

A malformed (AKA creates duplicates on sync) task looks like:
```
BEGIN:VTODO
SUMMARY:German course website
CLASS:PRIVATE
SEQUENCE:3
LAST-MODIFIED:20080910T030405
PRIORITY:3
UID:20080907T221411Z-10975-1000-1-48@freyja
DTSTAMP:20080910T025300Z
CREATED:20080910T025300
[COLOR="Red"]DUE;TZID=/softwarestudio.org/Tzfile/America/Toronto:20080910T123000[/COLOR]
PERCENT-COMPLETE:0
END:VTODO
```

And a good (synchronization works as expected) task looks like:
```
BEGIN:VTODO
SUMMARY:German course website
CLASS:PRIVATE
SEQUENCE:4
LAST-MODIFIED:20080910T030754
PRIORITY:3
UID:20080907T221411Z-10975-1000-1-48@freyja
DTSTAMP:20080910T025300Z
CREATED:20080910T025300
PERCENT-COMPLETE:0
END:VTODO
```


Note the line: ```
DUE;TZID=/softwarestudio.org/Tzfile/America/Toronto:20080910T123000
```

Accepted "Due" lines look like: ```
DUE:20080910T040000Z
```

The workaround for now is to just assign due dates on the n95 and synchronize afterward.

---

### Post by olavjunior on 2008-09-10
Thank you! Looking forward to try this out! Cause every once in a while the sync breaks as you say, and then my n95 entries gets duped.

EDIT: I'm not sure if this will work though, cause I still got an error without any task-entries. But I'm gonna try. You should file a bug report on this! Anyways of disabling the timezone stamp in evo? THis is really the one thing that bugs me the most with Liux!! I'm so sick of struggling with this :(

---

### Post by martron88 on 2008-09-10
I just found a better workaround to my task problem.  In evolution preferences > Calendar and Tasks > General Tab: Set the timezone to UTC instead of a specific location.  This allows the tasks to be saved without that crazy timezone line.


Of course this is likely not the only quirk that is creating duplicates in the n95.  Here's my suggestion on how we can control this duplication bug.  Whenever the errors occur, paste the full output of the failed synchronization here (make sure you run msync from the terminal).  Within this output, look for an error code (e.g. error 500) and note the UID that created the error (something like 20080910T182432Z-6608-1000-1-14).  Depending whether you think it is a task, calendar or contact item that generated this error, open the respective file in a text editor (I use gedit). The files are found in:

```
Tasks: ~/.evolution/tasks/local/system/tasks.ics
Calendar: ~/.evolution/calendar/local/system/calendar.ics
Contacts: ~/.evolution/addressbook/local/system/addressbook.db
```

I recommend you make a backup of each of these files by making quick copies:

In Terminal:
```
cp ~/.evolution/tasks/local/system/tasks.ics ~/.evolution/tasks/local/system/tasks-backup.ics
cp ~/.evolution/calendar/local/system/calendar.ics ~/.evolution/calendar/local/system/calendar-backup.ics
cp ~/.evolution/addressbook/local/system/addressbook.db ~/.evolution/addressbook/local/system/addressbook-backup.db

```

Now, open the file that you think is suspect (or use the gnome search tool to search ~/.evolution to find the UID within a file e.g. 20080910T182432Z-6608-1000-1-14) and search for the UID string within the file.  If it matches, Cut and paste that entry (strip any private data by replacing with xs) into this forum so we can help you trouble shoot what might be wrong (it's probably about 5 to 10 lines long and between "BEGIN" and "END" tags).  To troubleshoot it yourself, just compare that entry with the other entries and try to figure out what is different.  Likely problems include odd characters (accents) or out of place timezones.  Maybe we'll be able to compile a list of what to stay away from.



As for bug reports, who do you think would be interested in it?  Evolution, evo2sync, multisync, opensync?

---

### Post by martron88 on 2008-09-10
Just an update, switching to UTC fracked up all the times in evolution and my n95 of my calendar entries so I reverted back to Toronto as my timezone.  Interestingly, those weird time zone entries no longer appear when I add due dates to tasks and my n95 syncs fine.

Weird non?

Turns out that adding a "Due time" puts the weird timezone stuff in there.  So just avoid putting times on your due dates for tasks.

---

### Post by olavjunior on 2008-09-11
Multisync perhaps? I don't know.. 

But thanks for the UTC-tip though! Now after a couple of hours, I've managed to change the timezone AND gotten successful syncs with the N95. So far so good, let's just hope it stays that way :) If it breaks again, I'll sure let you know what broke it (I won't use the gui from now)

EDIT: I can already tell you that this works very vell! Using UTC did the trick! Thanks!

---

### Post by microcris on 2008-09-12
Hi there :)

I used that manual to synchronize my N80 and it worked very well :) Thanks :)

Now, I have an LG KU800. There is any chance to synchronize this phone with the same method? 
I tried to change the blue-tooth address and the identifier to LGPCSync but it gave me a error "Error synchronizing: Unable to connect one of the members"

If anyone knows how to do that, I would be very grateful.

---

### Post by teejcee on 2008-09-15
Many thanks for this how-to, HyRax.

All looks good ( so far ) syncing a Nokia E65 with Evolution - Contacts.

---

### Post by culmore on 2008-09-19
The sync is almost working for me, thanks for this post. My contacts which where on my mobile phone now all appear in evolution. But for some reason there are some strange characters like "&#xD;" in the note field of many of my contacts. I would just delete the notes but there are about 80 or so of them and they contain useful info. This cause sync conflicts even though the notes are perfectly readable in both the Nokia and evolution.

Just to be clear this is the note field of my contacts in the Nokia. Not the separate notes application, I disabled the syncing of notes. The easiest way is in the sync configuration on my nokia e70.

I am guessing that this is some kind of character encoding problem with end of line character (LF anf CR)

Thanks for any help anyone can be.

---

### Post by martron88 on 2008-09-22
> **culmore said:**
> 
I am guessing that this is some kind of character encoding problem with end of line character (LF anf CR)

Thanks for any help anyone can be.

You could try manually editing Evolution's addressbook file: ```
~/.evolution/addressbook/local/system/addressbook.db
```

gedit works fine.  Figure out what character it is that's giving trouble, then do a search and replace throughout the file.

Backup your addressbook file before you touch anything!!
```
cp ~/.evolution/addressbook/local/system/addressbook.db ~/.evolution/addressbook/local/system/addressbook-backup.db
```

---

### Post by em4mapson on 2008-09-22
> **martron88 said:**
> You could try manually editing Evolution's addressbook file: ```
~/.evolution/addressbook/local/system/addressbook.db
```

gedit works fine.  Figure out what character it is that's giving trouble, then do a search and replace throughout the file.


Problem is that the db-file is not human readable. One needs a suitable database browser. I do not know is it possible to do "find-and-replace" with those.

Culmore, you could also sync to file first (file-sync plugin), then remove unwanted characters, and then sync to back to evolution. Obviously more usable and elegant way is to make a script, which would do all of that.

---

### Post by culmore on 2008-09-27
> **em4mapson said:**
> Problem is that the db-file is not human readable. One needs a suitable database browser. I do not know is it possible to do "find-and-replace" with those.

Culmore, you could also sync to file first (file-sync plugin), then remove unwanted characters, and then sync to back to evolution. Obviously more usable and elegant way is to make a script, which would do all of that.

Good ideas thanks guys. I did try this one and my Nokia gives the similar symptoms in terms of error message (as expected). My Nokia got into a strange state the loudspeaker stopped working and I had to remove the battery to fix it. Odd. This has slowed me down a bit. Even more backups required in case disaster hits.. ekkk I may have to boot to windows to backup with the Nokia software suite..

I just wanted to reply so you knew I had appreciated the two answers to my question and I will be trying again. Will post the results.

---

### Post by martron88 on 2008-09-28
> **em4mapson said:**
> Problem is that the db-file is not human readable. One needs a suitable database browser. I do not know is it possible to do "find-and-replace" with those.

Culmore, you could also sync to file first (file-sync plugin), then remove unwanted characters, and then sync to back to evolution. Obviously more usable and elegant way is to make a script, which would do all of that.

You're right!

You can save your contacts in evolution in VCard format which is readable enough for search/replace of odd characters.  I think that's what I ended up doing in the summer.  Once 'fixed' you should delete your contacts in evolution and import the fixed vcard file.  A bit laborious but it could work

---

### Post by olavjunior on 2008-10-09
Well, finally! I'm so sick of all these bugs, so I'm soooo glad that Evolution finally work properly with google calendar (Intrepid)! So now I have google calendar as default, and use goosync to syncronize my mobile. All I need multisync for now is tasks, but that didn't work. However, that's no big deal :) Oh, happy day!

---

### Post by Nano on 2008-10-15
I'm getting this error and I really can't figure out what's going wrong :(
```

 msynctool --sync evolution-n95
Synchronizing group "evolution-n95" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-48F5A14100000000 with data of size 8 from member 1 (evo2-sync). Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client had an error while getting changes: Forbidden (0x43)
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members


```

---

### Post by viaciofano on 2008-10-18
hyrax
big thank you i have just sync my n95 to evo via hardy.....will read the post to see how i can get google calender next to work....
Vinny

---

### Post by midgemiles on 2008-10-21
I am having success mostly syncing my Nokia N95 8GB with Evolution using the guide posted here - thanks to Hyrax.
Just a problem with alarms.  Say an appointment has been entered into evolution with a reminder alarm set for 1 hour prior to time of appointment. When I do a sync and it is transferred to the phone, the alarm becomes 9 hours after the appointment - a 10 hour difference.  Perhaps not coincidentally, my timezone is GMT + 10.00 (Brisbane Australia).  
The computer takes the time from a web server (but can be set manually), and the phone can take time from a network server (or be set manually)
In the syncml-obex-client there is a timezone workaround.  When set to '0' the alarm information does not transfer from computer to phone - the phone entry says 'no alarm'.  If set to '1' the alarm setting does transfer, but adds 10 hours.
So in evolution I ask for the alarm to be 11 hours before the appointment, and then the phone alarm (on which I mostly rely) is now correct at 1 hour before appointment.
It makes no difference whether the phone time is set manually or derived from the phone network.
It would appear that multisync or one of its members is adding 10 hours.

So I try setting the time on both my phone and computer manually (turn off taking time from a server) and the alarm time sync problem remains.

When I used to sync evolution with my previous phone sony ericsson z800 (using multisync and irmc), this alarm problem did not exist.

Don't know if anyone has had a similar experience, but maybe its useful to discuss.

Finally, the change in alarm interval in evolution (from 1 hour before to 11 hours before) is not detected or not transferred in subsequent syncs of existing appointments, but reflected only in appointments entered after the setting was changed.

---

### Post by budge31 on 2008-11-10
Fantastic. Puts me one step closer to dumping windows forever. Thank HyRax.

---

### Post by ernstblaauw on 2008-11-15
Great to see Ubuntu and N95 are working quite well together.
At the moment, I'm running Ubuntu 8.10 (Intrepid). As I do not have bluetooth on my desktop, I was wondering if it is possible to use the usb connection for sync. Does anyone know something about this?

---

### Post by Trebaruna on 2008-11-18
It might be interesting to know that using these instructions to the letter I've got my N82 working with ubuntu 8.10.
Everything works like a charm... more or less. Using to-dos with a start date freaks the phone out. Must not support that data field. Other than that, it appears to work quite nicely! Thanks!

---

### Post by cirobr on 2008-12-23
Smoothly working on N76 and Ubuntu Hardy. Thanks.

---

### Post by jonelnz on 2009-01-03
Hi everyone...

My better half just bought an N95 before Xmas so I haven't been following this thread for long.
As she is running XP on her machine I've only installed the software that came with the phone, but have been reluctant to use it.(didn't like the GUI much)

Yesterday I attempted to setup a sync with Evolution using this guide by "HyRax" - Thank you so much...
After a couple of hours of failed attempts I gave up and went to bed.

Today after reading the whole thread in it's entirety I saw a post by "leander" who stated that

Quote:
"It was absolutely vital to reboot the phone after the pairing was established, however. Dunno why"

I am now one happy syncer, Thank you HyRax and everyone who contributed to this thread


**<config file>**

<config>
	<bluetooth_address>00:1E:A4:54:82:5D</bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel>
	<interface>0</interface>
	<identifier>PC Suite</identifier>
	<version>1.2</version>
	<wbxml>1.2</wbxml>
	<username></username>
	<password></password>
	<type>2</type>
	<usestringtable>1</usestringtable>
	<onlyreplace>0</onlyreplace>
	<recvLimit>0</recvLimit>
	<maxObjSize>0</maxObjSize>
	<contact_db>Contacts</contact_db>
	<calendar_db>Calendar</calendar_db>
	<note_db>Notes</note_db>
</config>

---

### Post by seng1978 on 2009-01-14
Hi guys,


just walking through this guide and want to let my self out abit ^^

I used this guide twice already and I noticed after I setup things correctly syncing wont be succesful rite away.

1st Time: Well the first time I tried setting it up it didnt sync. It said syn was succesfull(ya rite!) but my contacts in evo stayed empty and I got more than 400 contacts in my phone.

I gave up! A couple days later I thought about syncing again. I opened the multisync thingy and BANG it synced! WTH! All for 400 contacts poped up in the Evo. I was like KEWL!

2nd time: Well, I did a firmware upgrade on my phone today so all my contacts in my phone were gone rite? So i fired up multisync and it again said sync successful. My cell phone gave its regular confirmation *beep* sound. However, no contacts were in my phone...

So i thought maybe a restart solved my first sync back then. So a restart should solve my problem now too rite?

I went ahead and restarted my machine and synced BANG! all 400 contacts back in to my phone WOOOOOOOOOT


So maybe u just need to restart ur machine. PC's got a rest sometimes too. Who said they are not human:lolflag:

---

### Post by laakkus on 2009-01-21
After I fought for too long. I got the evo-sync working..

**Then I changed to Thunderbird** and am ever more happier. I like it more, UI and functionality.. Everything is syncing just great! 
(after I followed this guide: [http://www.lucagasperini.com/blog/2007-sync-nokia-thunderbird-and-google-calendar/](http://www.lucagasperini.com/blog/2007-sync-nokia-thunderbird-and-google-calendar/) )

---

### Post by mikhmv on 2009-01-26
Hi, I have some problem with synchronization.
If Appointment have reminder (alarm) Alarm time sync incorrectly. It have -5 hours. 
here my config file
> 
<?xml version="1.0"?>
<config>
<username></username>
<password></password>
<type>2</type>
<bluetooth_address>00:24:04:D8:BB:12</bluetooth_address>
<bluetooth_channel>6</bluetooth_channel>
<interface>0</interface>
<version>1.2</version>
<identifier>PC Suite</identifier>
<wbxml>2</wbxml>
<recvLimit>10000</recvLimit>
<maxObjSize>50</maxObjSize>
<usestringtable>3</usestringtable>
<onlyLocaltime>1</onlyLocaltime>
<onlyreplace>0</onlyreplace>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<note_db>Notes</note_db>
</config>


If after sync i change both appointment I have:
here info from Computer
> 
<?xml version="1.0"?>
<vcal>
  <Method>
    <Content>PUBLISH</Content>
  </Method>
  <Event>
    <Summary>
      <Content>Test</Content>
    </Summary>
    <DateStarted>
      <Content>20090126T070000</Content>
    </DateStarted>
    <DateEnd>
      <Content>20090126T071500</Content>
    </DateEnd>
    <Class>
      <Content>PUBLIC</Content>
    </Class>
    <Location>
      <Content>test</Content>
    </Location>
    <Sequence>
      <Content>7</Content>
    </Sequence>
    <LastModified>
      <Content>20090126T053807</Content>
    </LastModified>
    <Priority>
      <Content>0</Content>
    </Priority>
    <DateCalendarCreated>
      <Content>20090126T053425Z</Content>
    </DateCalendarCreated>
    <Transparency>
      <Content>OPAQUE</Content>
    </Transparency>
    <Alarm>
      <AlarmDescription>Test</AlarmDescription>
      <AlarmAction>DISPLAY</AlarmAction>
      <AlarmTrigger>
        <Content>-PT15M</Content>
        <Value>DURATION</Value>
        <Related>START</Related>
      </AlarmTrigger>
    </Alarm>
  </Event>
</vcal>


here from phone:
> 
<?xml version="1.0"?>
<vcal>
  <Event>
    <Summary>
      <Content>Test</Content>
    </Summary>
    <DateStarted>
      <Content>20090126T120000Z</Content>
    </DateStarted>
    <DateEnd>
      <Content>20090126T121500Z</Content>
    </DateEnd>
    <UnknownNode>
      <NodeName>X-EPOCAGENDAENTRYTYPE</NodeName>
      <Content>APPOINTMENT</Content>
    </UnknownNode>
    <Class>
      <Content>PUBLIC</Content>
    </Class>
    <Location>
      <Content>aaa</Content>
    </Location>
    <Sequence>
      <Content>6</Content>
    </Sequence>
    <UnknownNode>
      <NodeName>X-METHOD</NodeName>
      <Content>NONE</Content>
    </UnknownNode>
    <Alarm>
      <AlarmAction>AUDIO</AlarmAction>
      <AlarmTrigger>
        <Content>-PT5H15M</Content>
        <Value>DURATION</Value>
        <Related>START</Related>
      </AlarmTrigger>
      <UnknownParam>X-EPOCSOUND<ParamName>TYPE</ParamName></UnknownParam>
    </Alarm>
    <LastModified>
      <Content>20090126T053644Z</Content>
    </LastModified>
    <Priority>
      <Content>0</Content>
    </Priority>
    <UnknownNode>
      <NodeName>X-SYMBIAN-LUID</NodeName>
      <Content>64</Content>
    </UnknownNode>
  </Event>
</vcal>


phone have <Content>-PT5H15M</Content>. 

If localtime = 0 than alarm on phone switch off. 

Can anybody help me to resolve this problem?

P.s. My area -5 hours. In phone (n85) time settings = local time only.

---

### Post by mikhmv on 2009-01-27
I found that Alarm switch off if i am using localtimeonly = 0. If localtimeonly =0 than alarm Switch on but have -5 additional hours from event alarm in evolution. 

Can anybody help me with this?

---

### Post by danzvash on 2009-03-30
Quick note:

Calendar events only seem to sync from the phone when they are set to "Public", rather than "Private".

Unfortunately events are created as "Private" by default and there seems to be no way of changing this default behaviour. So to get sync working, you have to manually set each Calendar event to "Public" first. 

Thanks, Nokia.

(I hope I'm wrong: please, somebody tell me I am.)

---

### Post by brendanpiater on 2009-03-30
Anyone tested this with Januty?

Cheers
B

---

### Post by stepdown on 2009-04-01
Working perfectly here, just gotta get Thunderbird contacts into Evolution properly now.

Thanks! :D

---

### Post by ukblacknight on 2009-04-06
Does anyone know how to pair a Nokia N96 with evolution?  I had an n95 and this guide worked perfectly first time, however I'm having trouble with the n96!

```
tom@BlacKnight:~$ msynctool --sync evolution-n96
Synchronizing group "evolution-n96" 
The previous synchronization was unclean. Slow-syncing

(process:14677): libecal-WARNING **: e-cal.c:318: Unexpected response
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
Member 1 of type evo2-sync just connected
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members

```

I can pair my phone fine.  I usually have trouble browsing the phone through Intrepid, it works probably 1 in every 10 tries, however I can send/receive files from the phone fine.

This is my config file.  The MAC has been taken out for security:
```
<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>5</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>

```

The N96 seems to use channel 5 by default.  I did spot a different error earlier too, something on the lines of "Unknown SAN Version", whatever that means.

I can provide more info if necessary!

---

### Post by ollapapallo on 2009-05-05
> **ukblacknight said:**
> Does anyone know how to pair a Nokia N96 with evolution?  I had an n95 and this guide worked perfectly first time, however I'm having trouble with the n96!

I also managed to sync my N95 but would be really happy if someone would provide instructions also for **N96**


8-[

---

### Post by lancer14 on 2009-05-30
Thankyou for the info. just sharing some n95 wallpapers [http://mobilephonecellcomputing.wordpress.com/apple-iphone-wallpapers](http://mobilephonecellcomputing.wordpress.com/apple-iphone-wallpapers)

---

### Post by robbie d on 2009-06-30
I got my N95 to sync on Jaunty, but I have a feeling the <notes> refers to the 'todo' tasks rather than the separate notes app that the nokia has. If i'm wrong can someone please tell me where my 500+ notes went in evolution?

---

### Post by texadactyl on 2009-08-13
A lot of people have had troubles with the multisync-based tools.  I found that sync experience to be inconsistent and always fails to process deletions.

I currently do a combination of 2 manual syncs:
[INDENT]1. Sync my N95 with Google Mail Contacts and Calendar using Google Sync.  Go to [**Google Sync**]("http://www.google.com/mobile/products/sync.html") and select Nokia S60.  Follow the instructions there ... it may have changed since I installed 6 months ago.

2. Sync my Google Mail Contacts with Thunderbird + Zindus.  NOTE that this does not include Calendar sync (see below).  I'll assume that you are already using the Mozilla Thunderbird email client and that you have setup the gmail account in Thunderbird.  Install "Zindus" from the Tools Add-ons sequence (similar process to that which is used with Firefox).
[/INDENT]

This gives me access to contacts on the go, on the web, or at my Linux desktop.  It should work for Windows and MacOSX too.

If you want to sync (Sunbird) or view (Lightning) your **Google Calendar** on the desktop, the following URL gave me instructions that worked, albeit a bit quirky for my taste: [**how-to-sync-any-desktop-calendar-with-google-calendar**]("http://lifehacker.com/399407/how-to-sync-any-desktop-calendar-with-google-calendar").  I hope that a simpler procedure will be forthcoming for those folks who have dynamic calendars.  I am not a big calendar-user so I wasn't that interested but that's just me and maybe my interests will change in the future.

Good luck.

---

### Post by argie on 2009-09-30
Just wanted to report that I got this working on an N73 by doing the following:

1. Syncing to an empty address book.
2. Syncing to a new, empty Calendar first. Then syncing to my normal Personal calendar.

---

### Post by benjalien on 2009-10-13
Hi [HyRax]("http://ubuntuforums.org/member.php?u=506955") and everyone else!

I'm having a little problem syncing my N70...

Here's what I get:

The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects

Unable to commit change. Error 500

And the sync only works one way. My phone writes to evolution, but evolution doesn't write to my phone...

Any idea?

---

### Post by Acker on 2009-10-15
Hi!

I got a similar message to > The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects

This is since Karmic. In Jaunty there was no error.

Any help?

Best regards,
Acker

---

### Post by Acker on 2009-10-23
Hmm i did a clean  install of karmic today, reconfigured the sync and everything is working again without an error, so for me thx again and problem solved! :guitar: :guitar: :guitar:

---

### Post by Darce on 2009-10-31
Still works on a clean Karmic install. Thanks guys.....

---

### Post by benjalien on 2009-11-02
Well, actually I'm on Debian :)

Could you please post me your versions so I could see if I use the same...

Benjalien

---

### Post by pingwing on 2009-11-04
I've just discovered [this site]("http://diabo.freehostia.com/symbian/indexhack.htm") which tells you how to mod your Symbian phone so you can cut/copy/paste the Calendar and Contacts files inside! This means you can finally clean everything up after a slow-sync, not only in Evo but also in Symbian, and so remove all those duplicate entries.
Here is a howto that worked for my Nokia E51 (S60 3rd Edition, Feature Pack 1) and Evolution 2.22.3.1, syncing with Multisync 0.90 0.91

***HOW TO GET RID OF THOSE NASTY DUPLICATE ENTRIES***

With your phone:
You will need: The CD and USB cable that came with your phone; a fully-charged battery
1. BACKUP YOUR PHONE! (see the manual for how to do that).
Type *#0000# to see the specs of your phone, then go here to see if it's hackable. If it isn't yet, you're out of luck – but keep an eye out for further developments.
2. Go [here]("http://diabo.freehostia.com/symbian/indexhack.htm") and choose the best way to mod your phone (this is quite an adventure, so make sure you have a little time).
;)(tips for travelers:
a - to install X-Plore,  I installed PC Suite on an nLited version of XP running on VirtualBox. You may find a neater way.
b -  if, when you try to install ROMPatcher you get a message saying “certificate expired”, change your phone's date to 11/15/2008 and try again. Don't forget to put back the correct date when you're done)
3. Make a copy of the Calendar file (C:\Private\10003a5b\Calendar) in your phone and put it in a safe place on your computer.
(On some phones the folder name is 1000395b)
4. Delete  the Calendar file in your phone.
5. Repeat steps 3 and 4 with the Contacts file (C:\Private\100012a5\DBS_100065FF_Contacts.cdb).
(On some phones the folder name is 10001295)
(tip – X-Plore doesn't have a Paste function in the edit menu. You paste by navigating to the folder you want, and then pressing the main enter button on your phone – the one in the middle)

With Evolution:
1. Delete all the duplicates in your calendar and contacts (manually, I'm afraid).
2. Make a backup (File – Backup Settings) and put the resulting .tar.gz file in the usual safe place
3. Create a folder on your desktop (call it what you like), put a copy of your Evolution backup in there, and open it with Archive Manager. Don't extract the files.
4. You'll find a folder called .evolution – open it.
5. Now go to calendar/local/system and delete all the files in there except calendar.ics
6. Then go to .evolution/addressbook/local/system and delete everything except addressbook.db and addressbook.db.summary.
7. Close Archive Manager.
8. Restore Evolution (File – Restore Settings) using the modified .tar.gz file.
Evolution should now look exactly the same as it did before – if it doesn't, restore the original settings (which you saved at the beginning, right?) and try again.

With Multisync-qad (if you haven't already done this)
1. Open Multisync and click on Edit
2. Click on syncml-obex-client
3. Look for the part that looks like <recvlimit>0</recvlimit> and change it to <recvlimit>10000</recvlimit> (this will stop multisync from passing more data than your phone can handle)
4. Click on Close

Now connect your phone via Bluetooth and run a sync. Warning! This may take as long as 15 minutes, and Multisync seems to hang at least once. If you interrupt it, you'll cause an unclean sync and you're back to square one. Best thing is to switch to another desktop and go back [here]("http://diabo.freehostia.com/symbian/indexhack.htm") and look at all the other interesting things you can do with your modded phone. Or feed the dog.

That's it. If all went well, everything should be back to normal at both ends.:D

---

### Post by franjo101 on 2009-11-11
Can anyone tell me is it possible to sync N95 with Sunbird?
Thanks!

---

### Post by otto67 on 2009-11-13
I have the same problem as Benjalien with my E70.
Till Jaunty sync worked perfectly
Since Karmic I get following messages:
"
The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects 
"
and phone writes to evolution, but evolution doesn't write to my phone...
Reinstalled Karmic twice but always the same issue
Maybe Darce could send his configuration files and versions.

---

### Post by forest555 on 2009-11-15
Does anybody know what to do? Sync is not possible anymore in Koala Karmic. 

The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects 

What to do? Please help?

---

### Post by wretched_dutchman on 2009-11-15
I also have the same sync-error with my N95.
Since I couldn't find any answers on google, nor a bug-report, I also posted a bug-report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/opensync/+bug/483224](https://bugs.launchpad.net/ubuntu/+source/opensync/+bug/483224)

I hope that someone comes with a solution to this problem

---

### Post by forest555 on 2009-11-16
What a pitty! It is really a very serious problem. Would not want to go back to Jaunty. Please help who can!

---

### Post by otto67 on 2009-11-18
I guess that problem is leading to libluetooth3. I compared all packages which are working when syncing: all multisync-opensync things are same versions. I also downgraded and tried several multi- or opensync packages with the same "cannot write ....objects" issue always. Biggest version difference is in libbluetooth3 (in jaunty 4.32 in karmic 4.51) I suppose new bluetooth libraries are the reason why plugins cannot write to the phone. Downgrade libbluetooth to 4.32 is not easy because affects lot of system packages including evolution itself.
I post this to launchpad too. Maybe someone can advise forums, mailinglists where to post it.
???

---

### Post by hitman9211 on 2009-11-18
Works perfectly! Thanks  I have the latest firmware of n95, so that's ok


Thanks 
a lot dude :)

---

### Post by stepdown on 2009-11-18
Think I'm having the same problem under Karmic Koala...

Error writing entry 815 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
...
The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects

Seems to work fine from phone to evolution but not from evolution to phone :(

---

### Post by forest555 on 2009-11-22
Same here, since Karmic - from Evolution to phone impossible.

Does anybody know, what to do?

---

### Post by audiomick on 2009-11-25
> **otto67 said:**
> I guess that problem is leading to libluetooth3. 
???

Hallo.
Mine is broken too - E61 to Evolution, but I am not using bluetooth. Mine runs over USB, so it can't be the bluetooth causing the trouble, at least not for me. I rather suspect the new version of Evolution it self which (I believe) came with 9.10.

I would really appreciate a suggestion too, as I have run out of ideas. I have become very dependent on the phone sync for my calendar. :cry:

---

### Post by suyog on 2009-11-25
I am able to do Sync both ways over Bluetooth in 9.10.
I am not sure why you are having issues.

---

### Post by forest555 on 2009-11-25
> **suyog said:**
> I am able to do Sync both ways over Bluetooth in 9.10.
I am not sure why you are having issues.

I supose you are only person in the world who can do that with Kaemic...

---

### Post by audiomick on 2009-11-25
> **forest555 said:**
> I supose you are only person in the world who can do that with Kaemic...

My thoughts exactly...;)

---

### Post by forest555 on 2009-11-25
Does anybody know what did they change in Karmic? In Jaunty everything works perfectly.

---

### Post by audiomick on 2009-11-25
No idea mate, nor has anyone else, as far as I can tell.

I suspect that the evo2-sync module can't deal with the updated Evoution, as that, i.e. Evolution, is the only thing that changed when I updated, but it is only a guess.

---

### Post by stepdown on 2009-11-26
Interesting to know that it might not be to do with bluetooth, just spotted [your other thread](http://ubuntuforums.org/showthread.php?p=8384580) via Google as well!

---

### Post by audiomick on 2009-11-26
> **stepdown said:**
> just spotted [your other thread](http://ubuntuforums.org/showthread.php?p=8384580) via Google as well!

Glad someone did...;-)

---

### Post by suyog on 2009-11-26
I am not sure why its not working for all but I am all latest updates, blueman.

In System->Admin->Software sources->Updates , I have checked all options including pr-released & unsupported.

Give a try again.

---

### Post by audiomick on 2009-11-27
> **suyog said:**
> I am not sure why its not working for all but I am all latest updates, blueman.

In System->Admin->Software sources->Updates , I have checked all options including pr-released & unsupported.

Give a try again.

I have everything enabled, except "karmic-proposed", which I presume is what you mean by pre-release. I am not game to select that, because I don't want to risk updating something important to a possibly buggy pre-release version and have it stop working.

I have decided to use PC Suite to back up the phone until I get an indication that the problem might be solved. 

It is a pain, and only possible because I have to have windows on my laptop to use the programs for Yamaha digital audio stuff that I use at work. I hate to think how people are managing who have really managed to get rid of windows altogether.

---

### Post by suyog on 2009-11-27
I have Ubuntu kernel with version 2.6.31-15.50, it has come via proposed, can you check yours?

---

### Post by audiomick on 2009-11-27
My Kernel is 2.6.31-15-generic

---

### Post by suyog on 2009-11-27
so apart from that I think i don't have anything different. So you can give a try by enabling "proposed" updates.

---

### Post by audiomick on 2009-11-27
Hallo.
First of all, thanks for the suggestion.
I added proposed and re-loaded, but it didn't offer me a new kernel. Don't know why.

edit: that might be because I have an Ubuntu Studio, which, as far as I know, uses a different kernel from the standard Ubuntu.

---

### Post by suyog on 2009-11-27
Thats now very strange !!! I dont have any answer now :(

---

### Post by audiomick on 2009-11-27
> **suyog said:**
> Thats now very strange !!! I dont have any answer now :(

Yeah, no worries.
It seems like I am not completely alone with the problem. Hopefully something will turn up soon that will help... :p
Thanks for thinking about it anyway.

---

### Post by audiomick on 2009-11-30
Look at this:

[http://ubuntuforums.org/showthread.php?t=1341792](http://ubuntuforums.org/showthread.php?t=1341792)

might make life easier

---

### Post by Charles. on 2009-11-30
I am having the same problem between korganizer and a Nokia E65 under 9.10.  I cannot write new events entered or changed in korganizer to the phone:[INDENT]Error writing entry KOrganizer-21992573.428 to member 1 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
[/INDENT]however an event deleted in korganizer is successfully deleted on the phone.  The phone reports  discards for the events that are not entered in it's calendar (so they are almost getting there!)

Synchronisation worked under 8.04 with a slightly different syncml-obex-client config file.  I had to change to[INDENT]<recvLimit>0</recvLimit>
<maxObjSize>100000</maxObjSize>
[/INDENT]both were (oddly) previously 1.

Since this is the same problem seen with Evolution maybe the issue is with syncml-obex-client?  My syncml config file is (except the address):[INDENT]<config>
<username></username>
<password></password>
<type>2</type>
<bluetooth_address>00:00:00:00:00:00</bluetooth_address>
<bluetooth_channel>10</bluetooth_channel>
<interface>0</interface>
<version>1</version>
<identifier>PC Suite</identifier>
<wbxml>1</wbxml>
<recvLimit>0</recvLimit>
<maxObjSize>100000</maxObjSize>
<usestringtable>0</usestringtable>
<onlyreplace>0</onlyreplace>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<note_db>Notes</note_db>
</config>
[/INDENT]Suyog It would be interesting to see what your config file looks like though I cant see too many options for changes.  I am running 2.6.31-15-generic and don't have pre-release or unsupported.

---

### Post by suyog on 2009-11-30
@Charles, I am using Bluetooth connection with following config of syncml-obex-client. I have removed Notes as they are not synced with Evolution(evo2-sync plugin dont support Memo<->Notes.
Also I have created sync profile "Ubuntu" in my phone's sync, here i have just copied PC suite renamed it to "Ubuntu", disabled Notes in Applications, and for contacts and calendar , i set to update "to server" as i dont want to have any updates from Evolution. These setttings i can always change to suite my requirements which I cant do in PC suite sync profile. SYnc Profile name from phone is used in identifier field in following config.

<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>My Phone MAC ID</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>Ubuntu</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>0</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>10000</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
</config>

---

### Post by suyog on 2009-11-30
I just noted that specifying sync direction in sync profile application setting in mobile doesnt make difference. i.e. If I set in Sync->Ubuntu->edit sync profile->apps->contacts->sync type=to server only. This i thought will allow only to add/update/delete to server(evolution). But with this setting also I note that sync is always 2 way. If I add/delete/update in Evolution , it gets synced with Mobile.

---

### Post by audiomick on 2009-12-01
@suyog
Can you try something for me? Can you change the sync direction for the calendar so that evolution is writing to the phone?

The reason for this is that I have an impression that this is what is hanging up. If that is the case, that might give us a workaround for the time being.

---

### Post by wesamly on 2009-12-01
Oh! [HyRax]("http://ubuntuforums.org/member.php?u=506955"),
Really thanks, you can't imagine how much it was helpful, you are the best=D>
Just to give you an idea:
I am running Kubuntu Karmic Koala 9.10, and I was trying to sync just bought Nokia N86 8MP. Let's say: Sync Evolution with Nokia N86 8MP via Bluetooth on Kubuntu Karmic ;)
After following the "GUI fan" part of the HowTo, I successfully synced the contacts between Evolution and the mobile phone.
Linux Rocks \\:D/

---

### Post by suyog on 2009-12-03
> **audiomick said:**
> @suyog
Can you try something for me? Can you change the sync direction for the calendar so that evolution is writing to the phone?

The reason for this is that I have an impression that this is what is hanging up. If that is the case, that might give us a workaround for the time being.

I am able to sync calendar from Evolution to Phone, also as i have noted changing sync direction in phone sync profile just doesnt seem to have any effect. i.e. even if i set it as only phone , it does update in both directions.

---

### Post by audiomick on 2009-12-03
OK, thanks. So much for that theory...:-?

---

### Post by stepdown on 2009-12-08
My kernel is up to 2.6.31-16-generic and the error persists, just so we can get that ruled out!

---

### Post by audiomick on 2009-12-09
this is really starting to *pique* me off!
I went to check to see if anything had changed, as I got a kernel update the other day.
Now I've lost the damn USB permission again!

---

### Post by bob-182 on 2009-12-09
have you tried the newest version of syncevolution?
[http://syncevolution.org/blogs/pohly/2009/syncevolution-10-alpha-1-released](http://syncevolution.org/blogs/pohly/2009/syncevolution-10-alpha-1-released)

---

### Post by audiomick on 2009-12-09
> **bob-182 said:**
> have you tried the newest version of syncevolution?
[http://syncevolution.org/blogs/pohly/2009/syncevolution-10-alpha-1-released](http://syncevolution.org/blogs/pohly/2009/syncevolution-10-alpha-1-released)

Thanks Bob. I thought there was something on the way, but probably wouldn't have noticed myself for weeks...;)

Edit:
I have had a closer look at that. It seems to be geared towards the Nokia Internet Tablets. They seem to have a different OS to the Symbian on my E61.

---

### Post by suyog on 2009-12-11
I have tried SyncEvolution even provided some inputs/testing for syncing Evolution with OVI.com cloud. 
[http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html](http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html)

It works there as well as other services like funambol, scheduleworld.

Recent update I have not tried as it allows to sync with phones also.

@audiomick, @bob-182 did you try it? let me know how was your experience.

---

### Post by audiomick on 2009-12-11
@suyog.
Haven't tried it yet, and I won't be able to for the next ten days or so at least, as I will be away at work.

---

### Post by suyog on 2009-12-14
I also wont be able to do it as its in alpha and install is not easy. We have to compile from source which i am least comfortable with.

---

### Post by audiomick on 2009-12-15
> **suyog said:**
> I also wont be able to do it as its in alpha and install is not easy. **We have to compile from source **which i am least comfortable with.

Hmmm... I have never even tried that.;) Have to wait a bit longer I suppose.

---

### Post by Allochtoon on 2010-01-02
Im able to sync from phone to evo, but from evo to phone i get

"Error synchronizing: unable to write one or more objects"

---

### Post by suyog on 2010-01-02
@Allochtoon, could you please check in your phone->tools->sync->PC Suite and in applications check if sync direction is both ways or not.

This message looks like evo is not able to write in phone.

---

### Post by audiomick on 2010-01-02
> **suyog said:**
> @Allochtoon, could you please check in your phone->tools->sync->PC Suite and in applications check if sync direction is both ways or not.

This message looks like evo is not able to write in phone.

Could be the sync direction, but this is the error message I am getting, and it is not the sync direction in my case. :(

---

### Post by dr_smit on 2010-01-03
:popcorn :=D>=D> :-\"
Works perfectly with Nokia 6630
dr_smit
:guitar:

---

### Post by suyog on 2010-01-03
This is really weird !!! works for some guys not for some. :)

---

### Post by audiomick on 2010-01-03
> **suyog said:**
> This is really weird !!! works for some guys not for some. :)

Yeah, wish I knew why...

---

### Post by Allochtoon on 2010-01-03
sorry trried different settings, i use 3310c though. Thanks for the help though in the mean time i use virtualbox.

---

### Post by suyog on 2010-01-04
@Allochtoon Hey Let me know about how it works in virtualbox?
I am really interested to know whether PC Suite, OVI Player and other Nokia Desktop programs work in Virtual environment.

---

### Post by tincup on 2010-01-13
Any news on this issue?

Having the same exact annoying "Unable to commit change. Error 415" issues here with a Nokia E65 and KOrganizer in single file mode. There seems to be a lot of talk about this problem out there... but no solutions whatsoever.

- t

---

### Post by audiomick on 2010-01-14
hallo.
As far as I can tell, the evo2-sync plugin isn't being developed anymore, or has changed to evolution2 or something. There used to be a reference to evo2-sync in the plugins list at the opensync site
[http://www.opensync.org/wiki/plugins](http://www.opensync.org/wiki/plugins)
and now it says "evolution". This link leads to a message saying "this doesn't work yet".

I don't know what is happening there. It seems that the evo2sync plugin still works for some people, but not for others. Mine doesn't work.:(

---

### Post by Charles. on 2010-01-18
@suyog Thanks for that file sadly (of course:() changing my preferences made no difference.

I am using opensync-plugin-kdepim as the data source and seeing the same problem as with evolution. Isn't the problem likely to be with syncml-obex-client sending a bad update?  My phone log shows a count under Phone: Discarded which reflects the number of items that should have been added.

Anyway I will just keep adding event on my phone, cursing:( and hoping a solution appears

---

### Post by stepdown on 2010-01-27
> **Charles. said:**
> Anyway I will just keep adding event on my phone, cursing:( and hoping a solution appearsThis has been my approach for a while now, Evolution is pretty much just a backup of what's on my phone now.

---

### Post by suyog on 2010-03-06
hey guys check and use syncevolution with its latest beta release
[http://syncevolution.org/blogs/pohly/2010/syncevolution-10beta2-released](http://syncevolution.org/blogs/pohly/2010/syncevolution-10beta2-released)
I have tried older version but that didnt have Bluetooth sync.
I have written how-to on my blog for ovi.com<->evolution sync.
[http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html](http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html)

---

### Post by heryatmadja on 2010-04-07
> **suyog said:**
> @Allochtoon Hey Let me know about how it works in virtualbox?
I am really interested to know whether PC Suite, OVI Player and other Nokia Desktop programs work in Virtual environment.

I run PC-Suite in VirtualBox (non OSE) on top of Karmic and the N95 USB sync works fine (albeit much slower).

---

### Post by stepdown on 2010-04-09
> **suyog said:**
> hey guys check and use syncevolution with its latest beta release
[http://syncevolution.org/blogs/pohly/2010/syncevolution-10beta2-released](http://syncevolution.org/blogs/pohly/2010/syncevolution-10beta2-released)Very interesting, will have a look at this in time...

Thanks! :)

---

### Post by 321on on 2010-04-17
Hi,
almost got it working but have an error at end which shows
Error synchronizing: Unable to read from one of the members.

syncml-obex-client  Error while disconnecting

Any suggestions welcome

---

### Post by bnuytten on 2010-05-07
Using Ubuntu and msynctool, I've been able to succesfully sync both my windows mobile phone contacts/calendar/notes with Evolution and then sync evolution with my Nokia E71 phone. Thus saving a lot of time copying stuff manually. Thank you open source!

Quick instructions for Lucid. Warning this will install some packages from the previous (Karmic) version.

```

wget http://de.archive.ubuntu.com/ubuntu/pool/universe/libo/libopensync-plugin-syncml/opensync-plugin-syncml_0.22-2_amd64.deb
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/libs/libsyncml/libsyncml0_0.4.6-3build1_amd64.deb
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/libs/libsoup/libsoup2.2-8_2.2.105-4ubuntu1_amd64.deb

sudo dpkg -i libsoup2.2-8_2.2.105-4ubuntu1_amd64.deb libsyncml0_0.4.6-3build1_amd64.deb opensync-plugin-syncml_0.22-2_amd64.deb


msynctool --listplugins
Available plugins:
synce-opensync-plugin
syncml-http-server
syncml-obex-client
evo2-sync

```
If you see syncml-obex-client listed, the install has been successful.

Continue with the instructions at the start of this thread to configure your device. My config looks like this.
```

msynctool --showgroup nokia
Groupname: nokia
Member 2: syncml-obex-client
	Configuration : <?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>00:11:22:33:44:55</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>0</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>

Member 1: evo2-sync
	Configuration : <config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

```

Make sure your phone is visible via bluetooth and issue the following command.
```

msynctool --sync nokia

```

If your Nokia phone and Ubuntu computer haven't been "paired" before, the nokia phone will ask for a password, type in any password you like. For instance "1234" and choose ok. Your Ubuntu will show a popup asking for (the same) password. Once the pairing is complete, the synchronisation will start. Note that you have to pair only once.

---

### Post by stepdown on 2010-05-07
Will try this out over the weekend, thanks!

---

### Post by emorkay on 2010-05-11
Hi,
I have followed all the steps. I am trying to sync my Nokia N73 with Evolution in Ubuntu 10.04. I am getting the following error:
Error while initializing syncengine: Model is not in configuration

Any help?
My configuration file for my phone is as follows:
***********************************************************************************
<config>
<bluetooth_address>My Phone's address</bluetooth_address>
<bluetooth_channel>10</bluetooth_channel>
<interface>0</interface>
<identifier>PC Suite</identifier>
<version>1</version>
<wbxml>1</wbxml>
<username></username>
<password></password>
<type>2</type>
<usestringtable>1</usestringtable>
<onlyreplace>0</onlyreplace>
<!-- This needs to be set to 10 000, otherwise you'll be sending more data than your phone can handle. -->
<recvLimit>10000</recvLimit>
<maxObjSize>0</maxObjSize>
<contact_db>Contacts</contact_db>
<calendar_db></calendar_db>
<note_db></note_db>
</config>
**************************************************************************************************

I am using multisync0.90.

Please help me out.

Thanks,

---

### Post by dona.net on 2010-06-15
Hi guys! I've a problem... I googled a lot and tried thousands of things, but I haven't been able to get sync working.

I'm trying to sync Evolution with a Nokia E65 over bluetooth using msynctool. I'm on Ubuntu 10.04 on a 64bit pc. I always get **Error 415 Unable to commit change** for the sync from evolution to nokia.

Packages used (I had to manually install some, as opensync-plugin-syncml isn't in repository now):
[LIST]
[*]opensync-plugin-evolution 0.22-2ubuntu2
[*]opensync-plugin-syncml 0.22-2
[*]multisync-tools 0.92.0~svn355-2
[*]libopensync0 0.22-4
[*]libsoup2.2-8 2.2.105-4ubuntu1
[*]evolution 2.28.3-0ubuntu9
[/LIST]

Here the trace containing the error when trying do sync:

```
$ msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-4C16B82200000002 with data of size 8 from member 1 (evo2-sync). Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Going to receive 0 changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.
Received an reply to our sync
Error writing entry pas-id-4C16B82200000002 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Member 2 of type syncml-obex-client committed all changes.
All clients have written
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects
```


Here my syncml-obex-client configuration:

```
<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>XX:XX:.......</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>1</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>
```


I'm testing with one contact only. And I've disabled calendar and notes sync for isolating the problem. The sync nokia->evolution works, but the sync evolution->nokia gives error 415, and no updates are seen on Nokia.

I'm desperate, please help me! :-) Thank you!

---

### Post by suyog on 2010-06-23
I have been using syncEvolution and Sync becomes very easy with it. Check my blog post about it.
[http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html](http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html)

Please note that I did test with 1.0 Beta 3 version but they have released stable 1.0 version after that so make changes in sources list while downloading.

[http://syncevolution.org/blogs/pohly/2010/syncevolution-10-released](http://syncevolution.org/blogs/pohly/2010/syncevolution-10-released)

Let me know how it works :)

---

### Post by daka on 2010-11-10
Hello Suyog

Thanks for the help... after years bI finally have my Nokia N95 syncing with Ubuntu... BUT I have a double entries problem whenever I sync.... I have to delete all the phone contacts then recopy all the Evolution contacts but then the next time I add one contact it doubles them up and I can't get around it.  Do you have an answer for this by any chance?

Thanks

sean

---

### Post by daka on 2010-11-10
I think I have figured out the problem... I had synced two or three phones over the years and I now have to start from scratch.... hopefully it will be cleaned up this way.....


TASKS.... I am not having success syncing tasks.. any suggestions?

sean

---

### Post by daka on 2010-11-13
Still having problems with the syncing... double entries...

I thought and still think it is related to having tried to sync contacts from 2 nokia phones N95 and old 6234...

When I open the sync configuration panel I get a strange message about the 6234.... it says that " current configuration is more complex than what shown... etc..

I would like to just erase the nokia 6234 but I don't see that option anywhere.. i suspect it has contaminated the whole system for syncing and needs to be purged... I have erased everything four times from the phone and the ubuntu and it still repeats and I have also re-installed the sync software..... any suggestions out there???

sean

---

### Post by daka on 2010-11-16
I have finally sorted the double entry problem with the help of a tekno-guru.. now contacts and calendar are fine.  I still don't see how "Tasks" gets synced... can anyone explain this to me?  On my Nokia N95 I see only 'Notes' in the Office application, and I don't see tasks anywhere.  Do I have to download a task software perhaps?

Thanks


sean

---

### Post by suyog on 2010-11-24
Try this, few thing might have changed but procedure is simple.
Notes in phone sync with Memos in Evolution.

[http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html](http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html)

---

### Post by heviiguy on 2010-12-01
I've spent a week trying to get SyncEvolution to sync between my Nokia N86 8MP and my Ubunto 10.04 box. What a crock! Sometimes certain things sync while during other phases of the moon, they don't. Trying to do it with Multisync doesn't throw the same disturbing error codes in my face but, neither does it result in any meaningful syncs.

It's obvious that I'm not the only guy extremely frustrated and supremely pissed at this abysmal situation. Is there really no solution? Are we all just wasting our time, chasing our tails in a never-ending quest to try to sort this crap out? I don't know about the rest of you but, I've got work to do. I had hoped that being able to sync my "stuff" would help me do my work but, this futile effort has now put me way behind the eight ball.

---

### Post by daka on 2010-12-01
Hello heviguy

I have had this nightmare for 9 years with Linux, starting with laptop modems and continuing with many other obstacles.  In spite of all the suffering I am happy to say I don't have Windows installed on my laptop any more.  I can't use some sophisticated software like Cubase yet but one day soon I will because Linux is advancing slowly but surely.

I DO have my Nokia N95 syncing with my laptop perfectly but it was not straightforward and required patience as I am still a Newbie after 9 years.

The biggest help I got was from this mailing list:

Send SyncEvolution mailing list submissions to
        [email]syncevolution@syncevolution.org[/email]

To subscribe or unsubscribe via the World Wide Web, visit
        [http://lists.syncevolution.org/listinfo/syncevolution](http://lists.syncevolution.org/listinfo/syncevolution)
or, via email, send a message with subject or body 'help' to
        [email]syncevolution-request@syncevolution.org[/email]

You can reach the person managing the list at
        [email]syncevolution-owner@syncevolution.org[/email]

The principal person responding to problems is EXTREMELY helpful but has very little time to hold your hand through simple steps.  He will tell you what to do or what to send him and you will have to possibly get some help from a teknoguru to follow his instructions and forward the requested information.  Through this process you will learn syncevolution.

You need to start with the premise that there are some people who have their phone syncing and patiently find out how it is done.

I am EXTREMELY happy to have my phone syncing but it was a bit problematic, partlu because I tried to sync two different Nokia phones and confused the hell out of the poor program resulting in double entries.

Good Luck

Sean

---

### Post by daka on 2010-12-01
Thanks Suyog!  I also now have notes amd memos syncing and am delighted!!!!

Sean

---

### Post by heviiguy on 2010-12-01
Olá Sean, 

Thank you very much for the encouraging words. It's good to see that somebody who had also been traversing this malodorous dungheap finally emerged. You've given me cause to try again.

I'll join the message board. I've actually been active on the site itself (you'll see my entries under "Nokia N86 8MP"). And indeed, Patrick has responded to some of my comments and questions. Yet, I've not been able to sort it out. Perhaps those on the mailing list might be able to guide me through this mess. In turn, maybe descriptions of my many attempts and variations might shed light on somebody else's issues - and help lead them out of the mire.

Saludos

---

### Post by daka on 2010-12-23
Hi Heviiguy

I just went through another nightmare.  I lost my Linux Mint Debian distro when it crashed.. it is based on Ubuntu 10.10.  I had to re-install everything and Syncevolution wouldn't work.  I even got to the point of sending Patrick Ohly another SOS email.

Then I suspected that the problem had something to do with Bluetooth and not with the sync software.  My philosophy for years has been to download everything that looks like it might relate to Bluetooth because bluetooth has been so problematic for years.  However, once I completely removed all bluetooth apps except for the default basic bluetooth  the sync worked perfectly again.

My suggestion is that maybe you use a live distro and try with minimal bluetooth apps, and see if that solves the problem.

I am once again very happy with my syncing life!

daka

---

### Post by heviiguy on 2010-12-23
Happy Holidays, Daka!

Fortunately I've not had serious issues with Bluetooth in general. The only times that I had experienced bluetooth-related issues were when I was running two competing bt managers. Took me awhile but, I eventually learned that this was a no-no. Nevertheless, this wasn't the source of my problems with SyncEvolution. 

Just last week, I was finally able to get my fone to sync! Well, at  least my contacts and calendars were syncing. However, it seems to be a  very precarious exercise. The slightest misalignment of the stars seems  to confuse the program. Perhaps this is why Patrick recently released a  "test" update.

I also run Conduit Synchronizer between my fone and box so that I can keep a couple of important files in sync via Bluetooth. This works like a charm!

---

