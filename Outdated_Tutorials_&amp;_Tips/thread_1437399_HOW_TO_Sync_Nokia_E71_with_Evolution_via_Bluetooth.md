---
title: "HOW TO: Sync Nokia E71 with Evolution via Bluetooth - Ubuntu 9.10"
date: 2010-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by engellion on 2010-03-23
Hi guys.

After many hours over the last 2 weeks trying to Sync my Nokia E71 with Evolution via Bluetooth on Ubuntu 9.10 (Karmic), I finally have it working.  I thought to add this post, as I did not find anything recent with a complete step by step breakdown on Ubuntu 9.10.

I want to thank the blogger at OnAgendaTech for his very useful [COLOR="Blue"][instructions]("http://tech.onagenda.com/en/linux/ubuntu/sincronizacion-nokia-e71-evolution-i/")[/COLOR] under Ubuntu 9.04. I found I only had to make a couple of minor changes to get things up and running.  

[SIZE="3"]**[COLOR="Teal"]Getting Started[/COLOR]**[/SIZE]

To get started, you'll need to install these packages (plus any dependencies they call for): 
[LIST]
[*]OpenSync-plugin-evolution 
[*]OpenSync-plugin-syncml 
[*]OpenSync-plugin-file 
[*]opensyncutils
[*]multisync0.90
[*]multisync-tools 
[*]libsyncml-utils
[/LIST]

[COLOR="Teal"]NOTE:All of the OpenSync set of packages need to be of the same version. On Ubuntu 9.10 these version numbers all began with 0.22-2
The Multisync packages were 0.92.0 [/COLOR]

You can use Ubuntu's Synaptic Package Manager to install these (System=>Administration=>Synaptic Package Manager) or from a Terminal screen you can:
[INDENT][INDENT][INDENT]
[COLOR="Sienna"]~$  sudo apt-get install OpenSync-plugin-evolution OpenSync-plugin-syncml OpenSync-plugin-file opensyncutils multisync0.90 multisync-tools libsyncml-utils [/COLOR][/INDENT][/INDENT]
[/INDENT]
		
You also need a working Bluetooth connection.  (I used GNOME Bluetooth v. 2.28.1 to set this up with a little help from BlueProximity v.1.2.5, but that's another story.) 


[SIZE="3"]**[COLOR="Teal"]E71 Phone Setup[/COLOR]**[/SIZE]

Next we are going to set up a new Sync profile on your E71.  
a) From your E71 Menu choose Tools=>Sync. 
b) Scroll to the "PC Suite" sync profile and then  choose "Options=>New Sync Profile". 

[INDENT][INDENT][IMG]http://ubuntuforums.org/attachment.php?attachmentid=151370&d=1269490511[/IMG][/INDENT][/INDENT]

You'll be prompted to copy settings from your PC Suite profile. We want to do this.  The new profile should open up to its settings screen.  Change the [COLOR="Teal"]"Sync profile name"[/COLOR] to **Evolution**

Under [COLOR="Teal"]"Applications"[/COLOR] we want to say "Yes" to "Contacts" and "Calendar" and say "No" everything else including "Notes" (the Evolution plugin doesn't support notes at the time of writing. When it does, you can go back in here and change this to "Yes").

[COLOR="Teal"][EDIT: Under "Applications" - for each menu item (Contacts, Calendar, Notes, etc) available, "Include in Sync - Yes/No" will be the first sub-menu.][/COLOR]

Now under [COLOR="Teal"]"Connection settings"[/COLOR] we want the following:  

Server version: 1.1
Data bearer: Bluetooth
Host address: Evolution
User name: none
Password: none
Allow sync requests: Yes
Accept all sync requests: Yes

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=151372&stc=1&d=1269490817[/IMG][/CENTER]

Hit "Back" when your done. 


[SIZE="3"]**[COLOR="Teal"]On Ubuntu 9.10[/COLOR]**[/SIZE]

There are two ways to set things up in Ubuntu.  You can use a Terminal and command line interface, or you can use a nice GUI that you installed with the packages listed - multisync0.90 ("Applications=>Accessories=>Multisync-gui) 

The GUI makes it easy to setup opensync.  For now, I'll list the commands that I typed at the terminal.

  **Step 1.**   Create a sync group called **evo2-e71**

  [INDENT][INDENT][COLOR="Sienna"]~$ msynctool --addgroup evo2-E71[/COLOR] [/INDENT][/INDENT]

This group will add the necessary plugins, one that transfers the formatted data via Bluetooth-OBEX SycnML from the phone (syncml-obex-client), and another which moves this data to the data files of Evolution via the Evolution plugin (evo2-sync). To see a list of plugins available:

[INDENT][INDENT][COLOR="Sienna"]~$ Msynctool --listplugins [/COLOR]
   
   Available plugins:
   evo2-sync
   syncml-http-server
   syncml-obex-client
   file-sync[/INDENT][/INDENT]

If [COLOR="Teal"]evo2-sync[/COLOR] or [COLOR="Teal"]syncml-obex-client[/COLOR] are missing, go back to Synaptic and install them. 
 

**Step 2.**   Add [COLOR="Teal"]evo2-sync[/COLOR] to the group you just created, evo2-E71:

  [INDENT][INDENT][COLOR="Sienna"]~$ msynctool --addmember evo2-E71 evo2-sync[/COLOR] [/INDENT][/INDENT]

And configure the group:

  [INDENT][INDENT][COLOR="Sienna"]~$ msynctool --configure evo2-E71 1 [/COLOR][/INDENT][/INDENT]

This will launch the editor *nano* which should show the content:

[COLOR="Blue"]  [INDENT][INDENT]<?xml version="1.0"?>
<config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>[/INDENT][/INDENT][/COLOR]

This indicates to the group where to route the data. "default" points to Evolution's default paths:

[INDENT][/INDENT]address_path => file: / / / home / USERNAME / .evolution / addressbook / local / system

[INDENT][/INDENT]calendar_path => file: / / / home / USERNAME / .evolution / calendar / local / system

[INDENT][/INDENT]tasks_path => file: / / / home / USERNAME / .evolution / tasks / local / system

Where USERNAME is your username on Ubuntu. These routes should be changed where necessary.

During my quest to get things working, I ended up typing in here the full path to the addressbook:

[COLOR="Blue"][INDENT][INDENT]<?xml version="1.0"?>
<config>
  <address_path>file:///home/paul/.evolution/addressbook/local/system</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>[/INDENT][/INDENT][/COLOR]


**Step 3.**   For the [COLOR="Teal"]syncml-obex-client[/COLOR] plugin need to know the E71's Bluetooth MAC address. To do this we need to configure the E71 to be visible to all. From the phone's menu, "Connectivity => Bluetooth => My phone's visibility: Show to all".

Now at the Ubuntu terminal enter:

[INDENT][INDENT][COLOR="Sienna"]~$ Hcitool scan[/COLOR][/INDENT][/INDENT]
 
[INDENT][INDENT]Scanning ...
	00:25:B2:10:7F:1E	MyNokia E71[/INDENT][/INDENT]

[COLOR="Teal"](NOTE: This is not my phone's actual MAC address, but this is what it will look like.)[/COLOR]

And to see the SyncML channel your phone uses:

[INDENT][INDENT][COLOR="Sienna"]~$ sdptool search SYNCML[/COLOR][/INDENT][/INDENT]

[INDENT][INDENT]Searching for SYNCML on 00:25:B2:10:7F:1E ...
Service Name: SyncMLClient
Service RecHandle: 0x1000b
Service Class ID List:
  UUID 128: 00000002-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008 )
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000002-0000-1000-8000-0002ee000002)
    Version: 0x0100[/INDENT][/INDENT]

Note the Channel number from this search. In my case: 10

[COLOR="Teal"](BTW, while not needed for syncing your E71, you can use BlueProximity to scan the channels on your phone to see which ones are usable and open.  This was helpful for me a couple of times when I was not sure if OpenSync was able to get through to my Nokia E71. BlueProximity is a type of automatic security control for when you leave your Ubuntu machine unattended.  When you walk away from your Ubuntu box, with your phone in your pocket, at a certain distance the Screen Saver comes on and you need your password to unlock it. Cool. 8) )[/COLOR]

**Step 4.**   With the data you obtained in the previous step, we're now going to add and configure the second plugin, [COLOR="Teal"]syncml-obex-client[/COLOR]:

[COLOR="Sienna"][INDENT][INDENT]~$ Msynctool --addmember evo2-E71 syncml-obex-client 
~$ Msynctool --configure evo2-E71 2 [/INDENT][/INDENT][/COLOR]

[COLOR="Teal"](Note: the 2 tells Msynctool you want to edit the 2nd group member, which is now syncml-obex-client.)[/COLOR]

Nano opens up the [COLOR="Teal"]syncml-obex-client[/COLOR] configuration file. We're going to modify three items with respect to the default configuration: 

[LIST]
[*]bluetooth_address
[*]bluetooth_channel 
[*]identifier
[/LIST]

Here's my configured file using the MAC address, channel number and the SyncML profile identifier I set up earlier in my phone, in this case "Evolution":

[INDENT][INDENT][COLOR="Blue"]<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>[COLOR="Black"]00:25:B2:10:7F:1E[/COLOR]</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>[COLOR="Black"]10[/COLOR]</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>[COLOR="Black"]Evolution[/COLOR]</identifier>
  
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
</config>[/COLOR][/INDENT][/INDENT]

I left everything else at it's default settings.

OK. We're just about there. 

**Step 5.**   Sync your E71 to Evolution

To do this, we can use the command line, or the Multisync-gui.  "Applications=>Accessories=>Multisync-gui"

If you use Multisync-gui, I reccommend you launch it from the command line in a terminal.  That way you can see what is happenning in the background if things go wrong. To bring it up enter:

[COLOR="Sienna"][INDENT][INDENT]~$ multisync0.90[/INDENT][/INDENT][/COLOR]

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=151218&stc=1&d=1269389089[/IMG][/CENTER]

This gui shows the groups you've set up. In my case from the screen shot, I have one for Bluetooth and one for USB syncs.  (Am still trying to get the USB sync to work.)

If you click on the "Edit" button, you will be taken to a screen that lists your group's plugins.  

Select either of the plugin items and you  will be shown their configuration screens on the right.  You shouldn't need to change any thing here. If you followed my steps above, this should all be configured. However, for the evo2-sync plugin, make sure the Addressbook, Calendar, and Tasks are the right ones you want to sync.

[http://ubuntuforums.org/attachment.php?attachmentid=151220&d=1269388718](http://ubuntuforums.org/attachment.php?attachmentid=151220&d=1269388718)

From the edit screen, select the group name - evo2-E71. If they are not checked, check the boxes for "Notes" and "Data" to disable syncing these.  By disabling those objecttypes you don't want to sync, you can also do selective syncs of "Contact", "Todo" or "Event".  This is useful particularly if you hit trouble when syncing all these at once.

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=151219&d=1269388718[/IMG][/CENTER]

Now hit close and your ready to sync! 

On the main screen of the gui, hit the REFRESH button.
 
 
**[SIZE="3"][COLOR="Teal"]Trouble Shooting[/COLOR][/SIZE]**

**i)  Error:** All changes are sent but you get a 'Pipe Closed! Exiting. Segmentation fault (core dumped)' error:

On my first run I got the following error:

[INDENT][INDENT](I've cut the first 455 entries from this screen dump)
Received an entry 456 with data of size 4 from member 2. Changetype ADDED
Received an entry 457 with data of size 4 from member 2. Changetype ADDED
Received an entry 458 with data of size 4 from member 2. Changetype ADDED
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
Pipe closed! Exiting.
Pipe closed! Exiting.
Segmentation fault (core dumped)[/INDENT][/INDENT]

**Solution:** After trolling around from forum to forum, and post to post, some of which were upto 3 years old, I tried the following (thanks to HyRax's post [COLOR="Blue"][COLOR="RoyalBlue"][here]("http://art.ubuntuforums.org/showpost.php?p=4530856&postcount=13")[/COLOR][/COLOR] and some helpful information from pingwing over [COLOR="RoyalBlue"][here]("http://ubuntuforums.org/showpost.php?p=8835702&postcount=314")[/COLOR])

Start with a fresh, empty set of database files for Evolution.  Then hit refresh.  You will probably be doing a "slow sync" now. So be patient.  

Because I had imported .pst files from Outlook into Evolution in my initial setup of Evolution, I possibly had some artifacts that SyncML didn't like.  Anyhow, this fresh start reslulted in a successful sync.

**ii) Error:** Multisunc-gui (Multisync0.90) fails to connect to one or both group members.

I don't know what is the problem here. It happened a couple of times. I got the gui to connect one of the times by a 'Synaptic:Mark for complete removal' of all the opensync and multisync packages listed above and setting everything up again from scratch. Drastic but effective.   

**Workaround:**  close Multisync0.90 and try a command line sync at the terminal:

[COLOR="Sienna"][INDENT][INDENT]~msynctool --sync evo2-E71[/INDENT][/INDENT][/COLOR]

If everything went well, you should see something like this in the terminal screen output:
[INDENT]
Synchronizing group "evo2-E71" 
Member 1 of type evo2-sync just connected
received contact dsession
received event dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry 20100324T004504Z-12580-1000-1-3@Paul-DellD620 with data of size 4 from member 1 (evo2-sync). Changetype ADDED
Received an entry 20100324T004610Z-12580-1000-1-4@Paul-DellD620 with data of size 4 from member 1 (evo2-sync). Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Going to receive 0 changes
Going to receive 0 changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.
Received an reply to our sync
Received an reply to our sync
Sent an entry 904 of size 320 to member 2 (syncml-obex-client). Changetype ADDED
Sent an entry 905 of size 264 to member 2 (syncml-obex-client). Changetype ADDED
Member 2 of type syncml-obex-client committed all changes.
All clients have written
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync was successful[/INDENT]


==============================
This last line looked so good!
==============================

.

---

### Post by chronosoft on 2010-03-26
Hi there! :D thanks for posting this! Been following your guide... and on the E71 when you're creating the new Sync Profile under Applications -> Contacts, data etc there is "Remote database" section in contacts, data etc... What do i put in that field?

---

### Post by audiomick on 2010-03-27
Nice guide. I had my syncing running, but the update to 9.10 broke it (E61 via USB ). I will try to set it up again from scratch when 10.04 is out, after I do the planned fresh install. It is nice to know that it should, in principle, work.

---

### Post by engellion on 2010-03-27
> **chronosoft said:**
> Hi there! :D thanks for posting this! Been following your guide... and on the E71 when you're creating the new Sync Profile under Applications -> Contacts, data etc there is "Remote database" section in contacts, data etc... What do i put in that field?

Hi. You're welcome :) 

The 'Remote database' will be the name that the Opensync SyncML server (on the PC) is expecting for this data type. In our case "Contacts".  

When you chose to create a 'New sync profile', if you had highlighted the 'PC Suite' sync profile before going "Options=>New sync profile", then you should have got the prompt in the screen shot as shown above to "Copy values from profile 'PC Suite'".  These values will all be set up for the SyncML service. 

The only two things we might consider changing under "Applications", is "Include in sync 'Yes/No'", and "Synchronisation type - Both ways/To server only/To phone only'" 

Under "Applications", I just left everything as was in the PC Suite profile and just changed "Notes" to "No".  You might want to change the "Synchronisation type" to send the data from the side that is your primary source. Leaving this as "Both ways" is fine, and will work.  But until you are entirely happy that clean data is being transferred successfully you might just want to set this up initially as a one-way sync.

---

### Post by engellion on 2010-03-27
@audiomick

Thanks Michael. Correction done.  Hope you get things working under 10.04. I don't have access to an E51, but I assume the phone set-up is similar.

Cheers.

---

### Post by leoh on 2010-03-31
I just tried my E51 with your tutorial, it works!!!
It didn't work at the beginning, it couldn't connect via bluetooth to my phone. I had to remove my phone from my bluetooth paired devices and vice versa, then pair them again, and it worked!

This is what I was waiting for to move from Windows to Linux. Thanks!

---

### Post by KC8DNQ on 2010-04-01
Thanks for this great HowTo! It worked out of the box for me.

A few times your command lines do have a capital letter in the beginning, that had to be changed into non-capital for the command to run, but this was really easy beasy!!!

And ofcourse I'm using the E71... ;)

Will be following, when it becomes possible to sync task-lists too...

---

### Post by leoh on 2010-04-01
I noticed that it doesn't sync the contact's picture. Is it possible to do that?

---

### Post by leoh on 2010-04-01
This is not working as it should. I just added a new contact to Evolution, and synced. The sync process took about 5 seconds and finished without errors on both the computer and the phone.

However, the new contact didn't get copied to the phone. Am I missing something?

---

### Post by leoh on 2010-04-04
Bump. Anyone? Did this happen to you too?

---

### Post by Karti on 2010-05-02
Hi all,

Looks like I am almost there.

However I only want to use blue tooth and can't find find OpenSync-plugin-syncml to download in the repositories and therefore don't have the syncml-obex-client 

I have it set up with with the:

Msynctool --configure evo2-E71 1
Msynctool --configure evo2-E71 2

Copying the details from your code but both saved to a temp file. This appears to disappear each time - is there somewhere I should actually save the files in my home drive?

During sync it appears to work fine, transferring items etc but when I view the phone and Evolution there are no changes.

Any help is greatly appreciated and I am running Ubuntu 10.04

Regards

K
;)

---

### Post by leoh on 2010-05-20
I tried again with Ubuntu 10.04, but it seems some of the packages have changed, and they are no longer available on Synaptic (for example, opensync-plugin-syncml).
What can I do?

---

### Post by leoh on 2010-05-20
> **Karti said:**
> Hi all,

Looks like I am almost there.

However I only want to use blue tooth and can't find find OpenSync-plugin-syncml to download in the repositories and therefore don't have the syncml-obex-client 

I have it set up with with the:

Msynctool --configure evo2-E71 1
Msynctool --configure evo2-E71 2

Copying the details from your code but both saved to a temp file. This appears to disappear each time - is there somewhere I should actually save the files in my home drive?

During sync it appears to work fine, transferring items etc but when I view the phone and Evolution there are no changes.

Any help is greatly appreciated and I am running Ubuntu 10.04

Regards

K
;)
It seems you are syncing twice with evolution, instead of having evolution and your phone. Try deleting one of the evolution sync instances and adding your phone as described on the tutorial.

---

### Post by expatal on 2010-05-27
> **leoh said:**
> I tried again with Ubuntu 10.04, but it seems some of the packages have changed, and they are no longer available on Synaptic (for example, opensync-plugin-syncml).
What can I do?

Take a look here: [http://ubuntuforums.org/showthread.php?p=9263987](http://ubuntuforums.org/showthread.php?p=9263987) post #5.

I have all packages installed now, but have not yet managed an initial sync. Some trouble with passwords it would appear, but that's another topic.

I'm running 10.04 Lucid opposite an E71.

---

### Post by AlexanderDGreat on 2010-12-04
Duh...

Here's a BETTER way to do it.

Install a VirtualBox - WindowsXP or Windows7.

Install Nokia Suite for E71.

Sync Phone Contacts, Calendar, and All your Files in 10 minutes.

No hassles, no worries. :)

---

