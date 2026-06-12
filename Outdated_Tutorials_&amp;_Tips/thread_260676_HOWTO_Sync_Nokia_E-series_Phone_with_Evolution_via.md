---
title: "HOWTO: Sync Nokia E-series Phone with Evolution via Bluetooth"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Nailor on 2006-09-19
This is a howto for syncing a Nokia E-series phone (Symbian 9.1, Series60 3rd edition) with Evolution. This has been tested with Nokia E50.

Kubuntu-users, you should check this post too: [http://www.ubuntuforums.org/showpost.php?p=1998822&postcount=62](http://www.ubuntuforums.org/showpost.php?p=1998822&postcount=62)

For Nokia E65 users (and why not other Nokia phones with S60 3rd edition FP1 too), check this [howto](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)

**For most of the systems this works only for contacts. However, as link above states, Calendar syncing seems to work at least for Nokia E65**

**1. Add required repositories**

Add following repositories to /etc/apt/sources.list:
```

deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main

```

To add key for the repo, do the following:
```

gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -

```

**2. Install required software**
```

sudo aptitude install libopensync-plugin-* libopensync0 opensyncutils msynctool mulstisync-qad bluez-passkey-gnome bluez-gnome

```

On Gutsy (7.10) the package names are bit different. Run command below instead.
```
sudo aptitude install opensyncutils opensync-plugin-evolution opensync-plugin-syncml multisync-tools multisync0.90
```

**3. Configure msynctool**
You can configure opensync via a graphical interface using multisync-qad (using similiar settings as below) or you can use command line. Guide below is for commandline. **Note, that the commandline is reported not to work flawlessly on Feisty. You'll bet better results with GUI**

Add a new group of preferred name (I'll be using nokia in this example):
```

msynctool --addgroup nokia

```
Add plugins to group. If you get errors in this face, they are propably due to missing plugins so check you've installed all required plugins.
```

msynctool --addmember nokia evo2-sync
msynctool --addmember nokia syncml-obex-client

```

Next is the 'trickiest' part. Installed plugins need to be configured. First, you have to find your phone's MAC. Use hcitool to do that:
```

hcitool scan

```
It should return something like:
```

xx:xx:xx:xx:xx:xx PhoneName

```
Now, configure the syncml-obex-client:
```

msynctool --configure nokia 2

```
Replace the context of the configuration (should be open in separate editor after running previous command) with the following XML:
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
        <usestringtable>1</usestringtable>
        <onlyreplace>0</onlyreplace>
        <!-- This needs to be set to 10 000, otherwise you'll be sending more data than your phone can handle. -->
        <recvLimit>10000</recvLimit>
        <maxObjSize>0</maxObjSize>
        <contact_db>Contacts</contact_db>
        <calendar_db></calendar_db>
        <note_db></note_db>
</config>

```
Where bluetooth_address is your phone's MAC address you just discovered.

After configuring the syncml-obex-client it's time to configure evo2-sync. Open configuration file with command
```

msynctool --configure nokia 1

```
And modify it to look like:
```
 
<?xml version="1.0"?>
<config>
<address_path>file:///home/USERNAME/.evolution/addressbook/local/system</address_path>
</config>

```
Replace USERNAME with your username.

**Edgy note:** With the latest update from jahn repositories, this works with defaults. You can configure Calendar as calendar_db to syncml-obex-client setup to make calendar syncing work

**4. Sync!**
You should be good to go now, so you should try synchronizing:
```

msynctool --sync nokia

```

**Edit 2007-10-25** Recvlimit (for syncing both, calendar and contacts). Thanks Ghosty.be.
**Edit 2007-09-04** New repos (thanks to Ghosty.be)
**Edit 2007-08-12:** Added note about E65 howto (thanks Ghosty.be)
**Edit 2006-10-02:** Notes can be extracted, but not yet to Evolution. I'm working on this

Please let me know if there's some problems with this!

---

### Post by Belibem on 2006-09-21
Is it possible to transfer evolutions contacts to the nokia smartphone?

And a bit trickier question :)
Is it possible to sync my 5500 nokia smartphone via usb cable?

---

### Post by Nailor on 2006-09-22
> **Belibem said:**
> Is it possible to transfer evolutions contacts to the nokia smartphone?


I managed to transfer the changes I made in evolution to my E50, all except the picture seemd to sync. Evolution though gets the pics from the phone when syncing.

> 
And a bit trickier question :)
Is it possible to sync my 5500 nokia smartphone via usb cable?

Don't know. You have to refer some other sources, my howto is only for syncing E-series phones with Evolution

---

### Post by Belibem on 2006-09-22
Thanx a lot! I will try as soon as I get my hands upon one of those usb bluetooth dongles.

Concerning my second question: I just want to use the included usb cable instead of bluetooth. However, syncml-obex-client only supports obex and http protocols, so my success chances are very slim with this method.

---

### Post by fago on 2006-09-30
I tried it with a nokia 6280, unfortunately the phone crashes as soon I try to sync.

However I still have some questions. Perhaps you could help.

What are the correct names for the Contacts, Calendar and Notes dbs? Can they be configured on the phone? (I'm using the obex syncml plugin too)

In which direction is the syncronisation supposed to work? *confused*

---

### Post by fredux on 2006-10-01
Does not work for me,

Here are resukts from 
> msynctool --sync nokia

> Synchronizing group "nokia"
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error synchronizing: Unable to connect one of the members
Pipe closed! Exiting.
Pipe closed! Exiting.


is there a solution to sync my nokia 6230i ?

---

### Post by Nailor on 2006-10-02
> **fredux said:**
> Does not work for me

Have you added your computer as a trusted device in your cellphone? I'm not familiar with the 6xxx series, so that's the best I can say at this point.

---

### Post by Nailor on 2006-10-02
> **fago said:**
> I tried it with a nokia 6280, unfortunately the phone crashes as soon I try to sync.

However I still have some questions. Perhaps you could help.

What are the correct names for the Contacts, Calendar and Notes dbs? Can they be configured on the phone? (I'm using the obex syncml plugin too)

I don't know can the names be configured, but the only names I can get the phone to respond are Contacts, Calendar and Notes. I actually tried out the Notes-sync (type text/plain) and it worked well. Calendar sync produces a weird error on phone.
> 
In which direction is the syncronisation supposed to work? *confused*
Both ways, at least on my computer. If I edit the contacts in Evolution and rerun the sync, the changes (except pictures) get uploaded to my phone.

---

### Post by patbuntu on 2006-10-02
Are there any 64 bit packages available?  

Thanks

-Pat

---

### Post by patbuntu on 2006-10-05
> **patbuntu said:**
> Are there any 64 bit packages available?

Or how do I install these on AMD64?

-Pat

---

### Post by eduardgrebe on 2006-10-09
My query is similar to that of patubuntu above. I would like to install on powerpc. Only i386 packages are available in the repo above.

Thanks
Eduard

---

### Post by Nailor on 2006-10-11
Seems that OpenSync is available for i386 only. AMD64 users can propably force the package to install with dpkg:
```

dpkg -i --force-architecture packagename.deb

```

**BUT NOTICE THAT THIS CAN SEVERLY DAMAGE YOUR SYSTEM AND RENDER IT UNUSABLE**

---

### Post by kcleong on 2006-10-19
Update: Used '*msynctool --configure nokia 2*' instead of '*synctool --configure nokia syncml-obex-client*', and it worked :D 

I'm trying this howto on Edgy Eft and I'm stuck at '*msynctool --configure nokia syncml-obex-client*' , it spits out a '*Unable to find member with id syncml-obex-client*'. I've added merseburg.de repos for edgy and installed the required packages.
```

kcleong@laptopkc:~$ msynctool --addgroup nokia
kcleong@laptopkc:~$ msynctool --addmember nokia evo2-sync
kcleong@laptopkc:~$ msynctool --addmember nokia syncml-obex-client
kcleong@laptopkc:~$ msynctool --showgroup nokia
Groupname: nokia
Member 1: evo2-sync
        Configuration : <config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

Member 2: syncml-obex-client
        No Configuration found: Member has not been configured
kcleong@laptopkc:~$ msynctool --configure nokia syncml-obex-client
Unable to find member with id syncml-obex-client

```
Does anybody know how to fix this? The --showgroup shows that syncml-obex-client is in member 2, but configuring is not possible.

---

### Post by darkghost on 2006-10-19
Hi,
I've got exactly the same error with dapper drake (kubuntu).

```

andy@kubuntudesk:~$ msynctool --showgroup nokia
Groupname: nokia
Member 1: evo2-sync
        Configuration : <config>
  <address_path>default</address_path>
  <calendar_path>default</calendar_path>
  <tasks_path>default</tasks_path>
</config>

Member 2: syncml-obex-client
        No Configuration found: Member has not been configured
andy@kubuntudesk:~$ msynctool --configure nokia syncml-obex-client
Unable to find member with id syncml-obex-client


```

---

### Post by darkghost on 2006-10-19
Gosh...thanks, this worked...
I'll let you know if I can sync my E61...

Darkghost

---

### Post by wearlan on 2006-10-22
This article is a work of brilliance, I now how full sync between pda/server/workstation/laptop for inbox and contacts. I can't thank you enough after a day wrestling with gnome-bluetoothmanager/multisyn[ck]/blah blah blah

I did it on openSuse 10.1; a useful url for the packages is..

[http://repos.opensuse.org/OpenSync/SL-10.1/](http://repos.opensuse.org/OpenSync/SL-10.1/)

Which I added to smart as a RPM meta data repository. pick all the bits wbxml/opensync/msynctools and plugins hopefully smart should do the deps.

other than that I followed the instructions...

----

For some of the questions. I did have the phone register the dongle as a trusted device (don't have to dig the phone out then to use the modem)

and I also had to use ...

msynctool --configure nokia 2     instead of syncml-obex-client

I did the same for the evo config too...

----------------------
5 beans indeed (I even registered *just* to say thanks for this, so I have no idea)

thankyou


Alan

---

### Post by Nailor on 2006-10-23
Thanks for everyone noting out the bug in my guide, I've now fixed the configuration line to use the number instead of module name (which was incorrect)

---

### Post by qrazi on 2006-10-23
I had to also install the msynctool package (sudo aptitude install msynctool).

```

msynctool -addgroup nokia

```

is supposed to be:
```

msynctool --addgroup nokia

```

somehow it didnt recognise the evo-2sync plugin. Will further into it ofcourse.

Had a look at the website under the repo: [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/). Since I´m using Efgy at the moment, I switched to using the Edgy repo. Also, i used the gpg key from that website.

---

### Post by jamaas on 2006-10-24
Nailor,

Thanks for this.  I've got the contacts to work using this with a N80 on Efty.  Do I understand correctly, are you (or anyone else) getting this to work for calendar as well?  If so would you please post the exact setup for both the phone and the computer syncml file?

thanks

Jim


> **Nailor said:**
> Thanks for everyone noting out the bug in my guide, I've now fixed the configuration line to use the number instead of module name (which was incorrect)

---

### Post by Nailor on 2006-10-25
> **jamaas said:**
> Nailor,

Thanks for this.  I've got the contacts to work using this with a N80 on Efty.  Do I understand correctly, are you (or anyone else) getting this to work for calendar as well?  If so would you please post the exact setup for both the phone and the computer syncml file?

thanks

Jim
I haven't got any luck with calendar. Trying to sync Calendar, the phone produces a system error and nothing happens (my E50 will still resume though).

---

### Post by qrazi on 2006-10-26
I have run through the setup. now i get the following error when i try to sync:

```

Error while synchronizing: Invalid answer from plugin process

```

I have a Nokia 3230 phone, which is a symbian S60 V2 phone.

---

### Post by patbuntu on 2006-10-29
> **jamaas said:**
> 

are you (or anyone else) getting this to work for calendar as well?

Calendar sync also works with the N80 - replace:

```

<calendar_db></calendar_db>

```

with:

```

<calendar_db>Calendar</calendar_db>

```

and see how you get on.  I had a few entries come through at the wrong time, but everything mostly worked.

-Pat

---

### Post by Nailor on 2006-10-29
> **patbuntu said:**
> Calendar sync also works with the N80 - replace:

```

<calendar_db></calendar_db>

```

with:

```

<calendar_db>Calendar</calendar_db>

```

and see how you get on.  I had a few entries come through at the wrong time, but everything mostly worked.

-Pat

What version of software you got in your phone (type *#0000# in phone)?

I'm not able to sync my E50 calendar though.

---

### Post by luxus on 2006-10-29
it is posible to sync with kdepim?

---

### Post by Nailor on 2006-10-29
> **luxus said:**
> it is posible to sync with kdepim?

There is a libopensync-plugin-kdepim in the repo, but haven't used it. Try and see what happens =)

---

### Post by patbuntu on 2006-10-29
> **Nailor said:**
> What version of software you got in your phone (type *#0000# in phone)?

I'm not able to sync my E50 calendar though.

V4.0623.0.42
20-09-2006
RM-92
Nokia N80 (58.01)

I used multisync-qad to set the plugins up using your settings

---

### Post by Nailor on 2006-10-30
> **patbuntu said:**
> V4.0623.0.42
20-09-2006
RM-92
Nokia N80 (58.01)

I used multisync-qad to set the plugins up using your settings

I propably try to update my phone to see if it fixes problems with calendar. I'm running july 2006 software and there is at least one newer software revision.

Thanks for the tip about multisync-qad. It seems to do the same tricks as commandline.

---

### Post by bodhi.zazen on 2006-10-30
Nice How-to Nailo

This thread has been added to the UDSF wiki.

[syncing a Nokia E-series phone (Symbian 9.1, Series60 3rd edition) with Evolution](http://doc.gwos.org/index.php/SyncNokiaE-seriesPhoneEvolutionBluetooth)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by jamaas on 2006-10-31
Nailor,

Thanks, I'm having the same problem and am not able to update my phone firmware, Vodafone in UK is way behind.  Could you tell me how you updated?  Did you debrand your phone.

Thanks

Jim


> **Nailor said:**
> I propably try to update my phone to see if it fixes problems with calendar. I'm running july 2006 software and there is at least one newer software revision.

Thanks for the tip about multisync-qad. It seems to do the same tricks as commandline.

---

### Post by Nailor on 2006-10-31
> **jamaas said:**
> Nailor,

Thanks, I'm having the same problem and am not able to update my phone firmware, Vodafone in UK is way behind.  Could you tell me how you updated?  Did you debrand your phone.

Thanks

Jim

I use the tool provided by Nokia ([http://europe.nokia.com/softwareupdate](http://europe.nokia.com/softwareupdate)) but I'm not sure is it at all possible for you to use it. The difference is, that I got a normal phone with unlocked sim, e.g. it's not bound to any operator here in Finland. Vodaphone uses specially tailored software for the phone in which case the software update may render the phone unusable.

Have you asked your nearest retailer/service point about the software update? At least here they do it free if you want.

---

### Post by piepre on 2006-11-01
wuhuu, 
works great (contacts and calendar) with my nokia e61 and kontact. thanks :)

---

### Post by patbuntu on 2006-11-01
> **patbuntu said:**
> I had a few entries come through at the wrong time

Handy hint - probably best to check if dst changes are happening while you trying this :mrgreen: 

-Pat

---

### Post by jamaas on 2006-11-02
Thanks piepre.

I presume your setup should work for us as well because the phone runs the same version of Symbian ( I think?!) as our n80's.  Could you please post, or put on a pasteboard, your complete setup on both the phone and the plugins for opensync?  It would also help us to get the version of firmware you are running on your phone.

Jim
> **piepre said:**
> wuhuu, 
works great (contacts and calendar) with my nokia e61 and kontact. thanks :)

---

### Post by piepre on 2006-11-02
> **jamaas said:**
> Thanks piepre.

I presume your setup should work for us as well because the phone runs the same version of Symbian ( I think?!) as our n80's.  Could you please post, or put on a pasteboard, your complete setup on both the phone and the plugins for opensync?  It would also help us to get the version of firmware you are running on your phone.

Jim

I'll post the configs after some tests. Today I noticed that there are all calendar entries twice on my phone :(

---

### Post by stuffcorpse on 2006-11-04
Hello, I've followed instructions here and there, messing about with configs and finally now I got my N73 to work (only tried sync calendars) using bluetooth. usb crashes my ubuntu for some reason. just want to share for anyone who cares. Not really sure if I got it all right but it worked.

I synced with evolution, running edgy ubuntu, hmm using the tools at the beginning of this thread.

my symcl-obex-client config:

<config>
  <bluetooth_address>00:18:C5:47:81:CD</bluetooth_address>
  <bluetooth_channel>13</bluetooth_channel>
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
  <note_db>Notes</note_db>
</config>


channel 13 service on my N73:

Service Name: Nokia SyncML Server
Service RecHandle: 0x10010
Service Class ID List:
  UUID 128: 00005601-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 13
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005601-0000-1000-8000-0002ee000001)
    Version: 0x0100


My N73:

V 2.0628.0.0.1
10-07-2006
RM-133
Nokia N73 (90.01)


I was stuck for a while, kept on getting request errors (67 or 68 or something I don't quite recall) when I test with the CLI. Then I sudoed it and it worked... So i setuid syncml-obex-client so i could use multisync-qad. not sure if that's the right thing to do.

some quirks I noted: I had problems syncing over 120 calendar events with the N73. the PC suite sync progress bar on the phone just stuck at 120 out of 400+ forever. So I reduced the number of events on my phone and it worked. Maybe it's some hardcoded thing.

during my head banging i visited [http://libsyncml.sourceforge.net/](http://libsyncml.sourceforge.net/). they said the project is now dead. i think this is one of the libs used for all this to happen? if so, bummer.

maybe this was all cheesecakes but i had to spend some time to figure this out. hopefully someone will find this somewhat useful...

---

### Post by pjain001 on 2006-11-09
I know this isn't the right place but it's the only place i could find with some knowledge of Nokia's E61 and Evolution ...

On Fedora Core 6, I've tried the same steps BUT I get the following error

% msynctool --addgroup nokia
% msynctool --addmember nokia evo2-sync
% msynctool --addmember nokia syncml-obex-client
Unable to instance plugin with name syncml-obex-client: Could not find format "memo"

Anyone know what might be causing this error?  I haven't been able to find anything of value with regards to Bluetooth on Opensync [http://www.opensync.org/wiki/Evo2-File](http://www.opensync.org/wiki/Evo2-File)

Any suggestions would be greatly appreciated.

---

### Post by Footissimo on 2006-11-21
Having just received my N80 in the post - this thread should mean that I can be finally free of MS activebloodysync and I can get rid of my XP partition..woohoo!  TY Nailor :)

---

### Post by Nailor on 2006-11-21
> **Footissimo said:**
> Having just received my N80 in the post - this thread should mean that I can be finally free of MS activebloodysync and I can get rid of my XP partition..woohoo!  TY Nailor :)

You're welcome :)

---

### Post by Footissimo on 2006-11-21
Works on Dapper and a N80 with the latest firmware - well the contacts sync...haven't had any joy with regards to the calendar entries, despite making the changes mentioned by patbuntu.

Going to upgrade to Edgy in the next week anyway, so I'll see how that goes.

---

### Post by stuffcorpse on 2006-11-21
hmmm after an update from the jahn's repo my things don't work anymore... Nothing else has changed with the configs, and even trying to play around with the options I still get bt/link errors. this is after multisync-qad got replaced by multisync-gui. not sure what went wrong here, I can send files from/to my N73 fine. Hopefully some more updates later or somehow i figure out the right things they will sync again~

---

### Post by selbaer on 2006-11-25
> hmmm after an update from the jahn's repo my things don't work anymore... Nothing else has changed with the configs, 

sure? i also installed it and after that i had to configure evo2-sync.conf again, cause it was messed up.

think somebody should make a clean howto on this, cause there are still things not clearly explained here. (what, you pointing at me??? no no , im sorry , got twenty children, two women and a lot og work to do :)  )

One thing is the config of channel in symcl-obex-client config. many thanks to stuffcorpse , your post helped me a lot to get it work. therefore i will post my config also, maybe it can help somebody like stuffcorpse's helped me:

> <?xml version="1.0"?>
<config>
  <!-- (Only for blue) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>00:12:D1:71:B1:2D</bluetooth_address>
  
  <!-- (Only for blue) The bluetooth channel to use (usualy the 11) [x] -->
  <bluetooth_channel>14</bluetooth_channel>
    
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


notice i have to use another channel (Nokia E60).

one thing to ask: what about opensync, multisync? i get a bit confused. Did i need multisync or just your packages? Is it the same?

---

### Post by stuffcorpse on 2006-11-25
selbaer: no worries, glad that it was of some help.

I went back and tried again. It turned out it was some problems with bluetooth pairing. So I just paired it again and it works now :). Yeah I kind of recall that the config file was messed up after the upgrade, I modified it so that it was like before (when it worked).

I guess the next thing I will try is the gcal sync. I don't really use evolution except getting my gcal to sync with it, and then sync the evo calendar with the phone... But now I use it more because of all the gnome integration stuff, like address books and things. Syncing the To Do list is useful as well. Maybe I can get tomboy or something to work with that... I really want to not have to use evolution, not that I have much against it, but I've used thunderbird for ages and I don't want to change it now.

---

### Post by vinceb on 2006-11-28
OK, I've had a reasonable bash at this without success. I suspect there are some areas where I am misunderstanding. I'm using a Nokia E61 with firmware 1.0610.04.04 and a Dell Laptop running Edgy. I've managed to discern the hardware address and query the phone. 

Interested that someone listed the Bluetooth channel for their nokia. How did you find this out. This is one of the things that if I tweak outside of 10. I just get an error. So 10 appears to make some kind of connection...

multisync-qad/multisync-gui....I've used multisync-gui as the qad package doesn't appear to be anything. I'm not able to edit a path from the gui, it doesn't appear to be an option. You just get dropdowns for the setings of the evolution plugin. I've tried via a terminal and can edit, but if you open the gui it overwrites the settings.

SO the actual error/issue I'm getting is this:

From the gui it appears to do something, syncs (with the phone reporting a sync as well) but then says:

8 entries received
All clients connected or error

The buttons are now disabled on the gui and you have to close the application. I assume it has failed to close the connection with the phone? When you do this you get errors in evolution and need to close and reopen evolution.

From the command line I get 8 messages as below:

Received an entry pas-id-4549FD3500000001 with data of size 4 from member 1 (evo2-sync). Changetype ADDED

Then:

Member 1 of type evo2-sync just sent all changes

Then it just hangs there and I have to Ctrl-C to get the prompt back. Post sync nothing appears to have moved between the devices apart from potential electronic good will. Any ideas?

---

### Post by Nailor on 2006-11-28
> **vinceb said:**
> OK, I've had a reasonable bash at this without success. I suspect there are some areas where I am misunderstanding. I'm using a Nokia E61 with firmware 1.0610.04.04 and a Dell Laptop running Edgy. I've managed to discern the hardware address and query the phone. 

Interested that someone listed the Bluetooth channel for their nokia. How did you find this out. This is one of the things that if I tweak outside of 10. I just get an error. So 10 appears to make some kind of connection...


You can dig out the right channel using two tools: hcitool and sdptool.

First, scan your phone mac with "hcitool scan" command

Then, query the phones services with: "sdptool browse XX:XX:XX:XX:XX" where XX:XX:.... is the mac address of your phone.

Now you should see the list, the one you want to use is the channel offering SyncML Server.

> 
multisync-qad/multisync-gui....I've used multisync-gui as the qad package doesn't appear to be anything. I'm not able to edit a path from the gui, it doesn't appear to be an option. You just get dropdowns for the setings of the evolution plugin. I've tried via a terminal and can edit, but if you open the gui it overwrites the settings.

SO the actual error/issue I'm getting is this:

From the gui it appears to do something, syncs (with the phone reporting a sync as well) but then says:

8 entries received
All clients connected or error

The buttons are now disabled on the gui and you have to close the application. I assume it has failed to close the connection with the phone? When you do this you get errors in evolution and need to close and reopen evolution.

From the command line I get 8 messages as below:

Received an entry pas-id-4549FD3500000001 with data of size 4 from member 1 (evo2-sync). Changetype ADDED

Then:

Member 1 of type evo2-sync just sent all changes

Then it just hangs there and I have to Ctrl-C to get the prompt back. Post sync nothing appears to have moved between the devices apart from potential electronic good will. Any ideas?

I run in to this same problem time to time. If you figure something out, please share =)

---

### Post by vinceb on 2006-11-29
All roads seem to lead to edgy not being that good at bluetooth......I've seen a few posts struggling on file transfer as well. I've tried the right click on file and 'send to'. There's no option for the phone in the dropdown for bluetooth.

Been through the OpenSync bugs to see if there are any clues. It appears there is some kind of hanging bug if the msynctool isn't told to explicity not do things it can't do. Other than that I'm struggling to find anything useful.

Of those out there with this happily syncing, are you on edgy? Is there any difference in bluetooth package versions between breezy, dapper and edgy? Would be useful to know who out there has a known good configuration and what is in there. 

Does anyone know whether the syncml-obex-client can be configured over wlan? The Nokia E61 has a wlan card. I'll have a dig myself anyway.

---

### Post by Footissimo on 2006-11-30
Managed to get the calendar to sync as well as the contacts on a Nokia N80 - basically I added the 'Calendar' bit suggested by patbuntu but the command line sync didn't seem do do anything aside from throwing up errors...so I clicked on multisync-gui and pressed 'edit' then changed 'evo2-sync' to sync my personal calendar in the drop down list on the right.  Hey presto, it worked!

Only 2 problems:

1. Multisync will append appointments to the nokia and won't recognise that the appointment already exists - so next time you sync, you'll get appointments doubling up.  Not a huge problem as you can just delete all the appointments on the phone and then sync - no doubling up

2. The calendar software on the phone doesn't seem to understand all day appointments - so it just states it as a meeting between midnight to midnight..a minor irritation and something that I'll look into and see if I can find out a way around.

Edit: This was on Edgy as well

---

### Post by franco66 on 2006-12-03
It did function (contacts, calendar and tasks) on my E61 and Evolution, and then I lost the contacts + tasks sync - an update ? :( 
Syncing to Kde gave me many duplicate entries
I am puzzled...

---

### Post by raydekok on 2006-12-06
i get this when i trie to sync can anyone help me?

```
raymond@de-tempel:~$ msynctool --sync nokia
Synchronizing group "nokia"
Member 2 of type syncml-obex-client had an error while connecting: There are novalid USB interfaces
Member 3 of type evo2-sync just connected
Member 1 of type evo2-sync just connected
Member 1 of type evo2-sync just disconnected
Member 3 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members
```

---

### Post by raydekok on 2006-12-06
i got it so far:

```
raymond@de-tempel:~$ msynctool --sync nokia
Synchronizing group "nokia"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected

(process:14267): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Member 3 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
Member 1 of type evo2-sync just disconnected
Member 3 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members
```

but i have the idea that i can´t change this: msynctool --configure nokia 1

i don't know how.

---

### Post by raydekok on 2006-12-07
ok i can conect, but now i get the error systemerror on my phone (E61)

i think it happens because i can't edit the last configuration in the howto.

---

### Post by raydekok on 2006-12-07
edit work but stil the system error.

why? why?

---

### Post by raydekok on 2006-12-07
ok one step a time.
now i found out that every time en try to sync i get an error on my phone.
the other thing that happens is that i have tot change this:

```
msynctool --configure nokia 1
```

i can save it but it turns back to the old file.

---

### Post by raydekok on 2006-12-08
who can help me?
i want to sync my phone.

---

### Post by Nailor on 2006-12-08
> **raydekok said:**
> ok i can conect, but now i get the error systemerror on my phone (E61)

i think it happens because i can't edit the last configuration in the howto.

I got system error too if I tried to synchronize Calendar.

What you mean you can't edit the last configuration?

---

### Post by raydekok on 2006-12-08
editting worked. i trie to sync only my contacs. maybe that will work.

---

### Post by raydekok on 2006-12-08
syncing my contacts don't work. why i don't know.

---

### Post by teslaw on 2007-01-10
I've  got it working for contacts (partially, some errors pop up), but where can I set content-type for notes? Can't get notes-sync working, phone just hangs when sending first note (actually seems to sent it, but then stops forever).
And some error that show durng sync:

> blah blah blah... syncing 52 previous entries, and then:
Received an entry 53 with data of size 4 from member 2 (syncml-obex-client). Changetype ADDED
Received an entry 54 with data of size 4 from member 2 (syncml-obex-client). Changetype ADDED
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Error writing entry [email]20060818T104950Z-9888-1000-1-2@gray.domain.name[/email] to member 2 (syncml-obex-client): content type was not configured
Mapping Write Error: content type was not configured
Error writing entry [email]20060818T104930Z-9888-1000-1-1@gray.domain.name[/email] to member 2 (syncml-obex-client): content type was not configured
Mapping Write Error: content type was not configured
Error writing entry [email]20060818T105244Z-9888-1000-1-6@gray.domain.name[/email] to member 2 (syncml-obex-client): content type was not configured
Mapping Write Error: content type was not configured
Error writing entry [email]20060818T105355Z-9888-1000-1-8@gray.domain.name[/email] to member 2 (syncml-obex-client): content type was not configured
Mapping Write Error: content type was not configured
Error writing entry [email]20060818T105206Z-9888-1000-1-4@gray.domain.name[/email] to member 2 (syncml-obex-client): content type was not configured
Mapping Write Error: content type was not configured
Error writing entry [email]20060818T104859Z-9888-1000-1-0@gray.domain.name[/email] to member 2 (syncml-obex-client): content type was not configured
Mapping Write Error: content type was not configured
Error writing entry [email]20060818T105219Z-9888-1000-1-5@gray.domain.name[/email] to member 2 (syncml-obex-client): content type was not configured
Mapping Write Error: content type was not configured
Member 1 of type evo2-sync committed all changes.
Received an reply to our sync
Member 2 of type syncml-obex-client committed all changes.
All clients have written
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects

---

### Post by Nailor on 2007-01-10
> **teslaw said:**
> I've  got it working for contacts (partially, some errors pop up), but where can I set content-type for notes? Can't get notes-sync working, phone just hangs when sending first note (actually seems to sent it, but then stops forever).
And some error that show durng sync:

I don't know about notes, maybe you should try text/plain or something similar in config files. I just got my laptop back from repair so I'll be testing the bt more again.

---

### Post by mjfleck2000 on 2007-01-10
> **luxus said:**
> it is posible to sync with kdepim?

I replied to your post but I don't see that it every posted... so I am re-posting

Yes, I can sync both ways from my Nokia E62 to Kontact for Todos, Address Book and Calendar.  I am using Kubuntu Edgy (it also works in dapper).
Mike

---

### Post by raydekok on 2007-01-11
> **mjfleck2000 said:**
> 

Yes, I can sync both ways from my Nokia E62 to Kontact for Todos, Address Book and Calendar.  I am using Kubuntu Edgy (it also works in dapper).
Mike

can you tell how? because i can't get it working. i have the E61 (nokia)

---

### Post by Whoopie on 2007-01-11
Hi,

here's an email from one of the opensync developers:
[http://article.gmane.org/gmane.comp.misc.opensync.user/1593](http://article.gmane.org/gmane.comp.misc.opensync.user/1593)

He successfully synced with an E63.

> 
i successfully synced a Nokia E63 with SyncML version 1.2.
libsyncml SVN 215 + patch and wbxml 0.9.2 is needed for this!
The needed libsyncml patch is attached (at least SVN revision 215 is needed 
for this!).

!!! WBXML 0.9.2 is REQUIRED for this !!!

In libsyncml the notification which got send while connecting get assemble for 
SyncML 1.2 in a slightly different way then 1.0 and 1.1. I am not this 
familiar yet with the differences of SyncML 1.2 and 1.1 and the notification 
which got send wile connecting (will change this ASAP). The attached patch 
use the same notification function as SyncML 1.1 and 1.0 does instead of 
sending the san type for SyncML 1.2.

Feel free to try this patch if your device support SyncML 1.2 by default or 
only 1.2. And let me know if this helped to get your device syncing...



Best regards,
Whoopie

---

### Post by mjfleck2000 on 2007-01-11
> **raydekok said:**
> can you tell how? because i can't get it working. i have the E61 (nokia)

Sure!
I wrote down some notes as I tried to set this all up.  Spent a good part of the weekend working on this.

I already had bluez-utils and kdebluetooth debs installed.

Several times I had to reboot to clear things up.  Also, I had to shut down the Nokia several times if things got messed up.

Kubuntu dapper or edgy, worked for both, I used only dapper repo at ~jahn
[LIST=1]
[*]Add repositories
     deb [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/) dapper main
     deb-src [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/) dapper main
[*]Add repository gpg key to apt-get
     gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
     gpg --export CB210090B029CB84 | sudo apt-key add -
[*]apt-get update
[*]apt-get install libopensync-plugin-kdepim libopensync-plugin-file libopensync-plugin-google-calendar libopensync-plugin-synce libopensync-plugin-syncml libopensync0 opensyncutils msynctool multisync-qad
[*]Plug in Bluetooth/Usb adapter
[*]sudo hcitool dev... this should show the computer's bluetooth mac #
[*]sudo hcitool scan... should show the E62 bluetooth mac #
[*]you can use “sdptool browse “ to get detailed info on phone and what channels it uses.  For syncing you want the channel for “Nokia SyncML Server”
[*]sudo kate /etc/bluetooth/hcid.conf
[*]remove the “#” from in front of 	auth enable;
[*]sudo kate /etc/bluetooth/rfcomm.conf
[*] I'm not sure this is needed, but I did it anyway.
     sudo mknod /dev/rfcomm0 c 216 0
[*]add rfcomm0 {
device 00:18:C5:43:19:2B; (# from #7 above)
channel 14;
comment "NokiaE62";
}
[*]sudo sdptool add --channel=10 OPUSH  //this is to allow file transfer
    You want the channel that is "SyncMLClient"
[*]sudo kate /etc/bluetooth/hcid.conf
      change passkey from 1234 to whatever number you want
[*] just in case, I also did sudo kate /etc/bluetooth/pin
     and changed the default 1234 to my new passkey
[*]sudo /etc/init.d/bluez-utils restart (for dapper) /etc/init.d/bluetooth (edgy)
[*]Enable bluetooth on E62
[*]Menu->Settings->Bluetooth->Bluetooth On
[*]Menu->Settings->Bluetooth->My phone's visibility Shown to all
[*]Menu->Settings->Bluetooth->My phone's name NokiaE62
[*]Menu->Settings->Bluetooth->RemoteSChip mode On or Off, didn't matter
[*]Pair NokiaE62 with computer
[*]Menu->Settings->Bluetooth-> push joystick to the right to change to paired device menu
[*]Select Options
[*]Select New paired device
[*]Found MyComputer-0
[*]Select
[*]Enter passkey that is the same as item as passkey above
[*]Select yes to automatically authorize
[*]Push in joystick
[*]Select Assign short name
[*]Give a name to this computer ( like Linus1 :)  )
[*]Exit
[*]Try to send a file from KDE
[*]Kmenu->Internet,Bluetooth OBEX, drag and drop,send
[*]As  user (**not root!**)
[*]msynctool --addgroup nokia (or whatever name you want)
[*]msynctool --addmember nokia kdepim-sync
[*]msynctool --addmember nokia syncml-obex-client
[*]hcitool scan
[*]msynctool --configure nokia 2
     here is my nokia file
     <?xml version="1.0"?>
<config>
  <!-- (Only for blue) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>00:18:C5:43:19:2B</bluetooth_address>
  
  <!-- (Only for blue) The bluetooth channel to use (usualy the 11) [x] -->
  <bluetooth_channel>14</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (as root!) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>KDE</identifier>
  
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
[*]Should be good to go at this point
     to sync, from terminal mysynctool --sync nokia
[*]Once this is working, you can use Kmenu->Utilities->Multisync-gui to sync
[/LIST]

I hope my notes work for you and that I didn't miss anything.  If nothing else, you know that it can work and pretty much how I did it.

---

### Post by raydekok on 2007-01-12
> **mjfleck2000 said:**
> 
[*]sudo kate /etc/bluetooth/hcid.conf
[*]remove the “#” from in front of 	auth enable;
[*]sudo kate /etc/bluetooth/rfcomm.conf


what do you mean with this? i can't find auth enable.

---

### Post by wahlau on 2007-01-12
> **mjfleck2000 said:**
> Sure!
I hope my notes work for you and that I didn't miss anything.  If nothing else, you know that it can work and pretty much how I did it.

hey thanks! i tried most of your steps (since some i have already done... ) and they worked! now i have got it sync'ed, and perhaps it might be a reason why i should keep the n73... 

wahlau.

---

### Post by mjfleck2000 on 2007-01-12
> **raydekok said:**
> what do you mean with this? i can't find auth enable.

Yes, my notes were a combination of dapper and edgy.  I uncommented the auth enable for dapper.   This option was not in the edgy version of hcid.conf

---

### Post by raydekok on 2007-01-13
ok that's why i use edgy.
but i can't get it. connect worked i think but then i get an error that says: can't connect with user or username is wrong. but there is no username or so.

but i follow the steps again and we sall see.

---

### Post by namaste70 on 2007-01-13
Sorry, but i'm newbie.

i added 
deb [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/) dapper main
deb-src [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/) dapper main 

with edgy instead dapper.

but when i write

msynctool --addmember nokia evo2-sync 
msynctool --addmember nokia syncml-obex-client

:

Unable to instance plugin with name syncml-obex-client: Unable to find the plugin "syncml-obex-client"


i tried to add plugins with synaptic with gui interface but if i search edo2 or obex-client  i don't find anything.


help! :-) 
thanks

---

### Post by raydekok on 2007-01-13
update your sources.list.

in konsole sudo apt-get update

and do it again.

---

### Post by namaste70bis on 2007-01-13
raydekok, tks for your answer.

now, o follow all the instruction of howto ( i have a nokia E61), 
but when i type  msynctool --sync nokia .......
my phone connect with PC , i write a password on my phone, but when i confirm with ok, i have this error :


Synchronizing group "nokia" 
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members

thks again

---

### Post by mjfleck2000 on 2007-01-13
> **namaste70bis said:**
> raydekok, tks for your answer.

now, o follow all the instruction of howto ( i have a nokia E61), 
but when i type  msynctool --sync nokia .......
my phone connect with PC , i write a password on my phone, but when i confirm with ok, i have this error :


Synchronizing group "nokia" 
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members

thks again

You should not be having to enter the passkey.  The default passkey is "1234".  I changed mine to a different number. 

 I changed the passkey in /etc/bluetooth/hcid.conf.

  I also changed /etc/bluetooth/pin to be the same as the passkey.

I then set the passkey on the Nokia to be the same:

# Pair NokiaE62 with computer
# Menu->Settings->Bluetooth-> push joystick to the right to change to paired device menu
# Select Options
# Select New paired device
# Found MyComputer-0
# Select
# Enter passkey that is the same as item as passkey above
# Select yes to automatically authorize
# Push in joystick
# Select Assign short name
# Give a name to this computer 
# Exit

You might want to verify that you have done the above three items.  If you did, you should not need to enter a passkey when you sync.  If you are still having problem after verifying the above, I would suggest that you turn off your computer, turn off the nokia, then start them both up again and then try to sync.  

Mike

---

### Post by Nailor on 2007-01-19
Has anyone encountered problems with duplicates? On my laptop, msynctool keeps asking about calendar notes (comparing them to contacts), which is disturbing.

---

### Post by neveceral on 2007-01-19
in the first post, there is a mistake in config
```
<config>
        <bluetooth_address>**00**:xx:xx:xx:xx:xx</bluetooth_address>
```
should be only
```
<config>
        <bluetooth_address>xx:xx:xx:xx:xx</bluetooth_address>
```
**without "00"** in the bluetooth_address

---

### Post by Nailor on 2007-01-19
Thanks for pointing that out, I'll fix it asap

---

### Post by mjfleck2000 on 2007-01-19
> **neveceral said:**
> in the first post, there is a mistake in config
```
<config>
        <bluetooth_address>**00**:xx:xx:xx:xx:xx</bluetooth_address>
```
should be only
```
<config>
        <bluetooth_address>xx:xx:xx:xx:xx</bluetooth_address>
```
**without "00"** in the bluetooth_address

I am not sure if you are referring to the the VERY FIRST post in this thread, or to my recent post.  
In neither posting did it appear to me that the bluetooth_address was incorrect.  On **my** E62 phone, it does have 6 hexadecimal groups with the first group being 00.

And there is more good news!  Not only can I send/receive files from/to my Nokia phone, and sync my Calendar/Contacts... I just set up my laptop to be able to use my Nokia for an Internet connection.  So, If I am out and about without a wireless connection but within the Cingular network, I can get on the Internet.  

It is not a fast connection... very much like using dialup...but a nice option to have.

---

### Post by raydekok on 2007-01-19
and stil not working on my nokia E61 with kubuntu. when i'm at home i will try again.

---

### Post by chrismine on 2007-01-21
Thank you I got it to work with my Nokia 6234.

---

### Post by raydekok on 2007-01-22
ok, i make progress, it looks like there is a connection.
but after a while it says connection timed out.
in the begining of the connection knotes starts uop but that's it.
who can help me?

---

### Post by Lucha on 2007-01-22
Well, I have a problem unknow until now. I have configured the plugins and I want to execute the connection but... is says:

** ERROR **: file opensync_plugin.c: line 452 (osync_plugin_get_path): assertion failed: (plugin)
aborting...


Anyone kknows how to solve that? Thanks to all.

---

### Post by raydekok on 2007-01-28
question: will this work with the cable?

---

### Post by Nailor on 2007-01-28
> **raydekok said:**
> question: will this work with the cable?

Not a bad question. I haven't tried it.

However, how it should work (or the way I figured it might work):
Use the original setup but instead of <bluetooth_*>-tags use <interface>, which is the USB interface. Correct usb interface can be found when phone is connected via [FONT="Courier New"]sudo syncml-obex-client -u[/FONT]. That should do the trick.

For more info, see [SyncML Guide at opensync.org]("http://www.opensync.org/wiki/syncml-guide")

---

### Post by morgs on 2007-02-02
> **stuffcorpse said:**
> some quirks I noted: I had problems syncing over 120 calendar events with the N73. the PC suite sync progress bar on the phone just stuck at 120 out of 400+ forever. So I reduced the number of events on my phone and it worked. Maybe it's some hardcoded thing.

I'm trying to set this up to sync my Nokia E61 to Edgy evolution, and I've got over 400 contacts. It gets to 200 or 220 and then gets stuck - sounds similar to your calendar event scenario. I'm not in a position to delete half my contacts - anybody got syncing working with a lot of contacts?

---

### Post by ianni67 on 2007-02-02
I could sync about 350 contacts with my 6630 but got some troubles when syncing calendar:
it keeps asking me to choose between couples of identical entries, which I do not have in my phone. I do not understand what's going on.

---

### Post by bodhi.zazen on 2007-02-04
Nice How-to

This thread has been added to the UDSF wiki.

[Sync_Nokia](http://doc.gwos.org/index.php/Sync_Nokia)

---

### Post by titof on 2007-02-05
I try to synchronize my Nokia 3250 with cable. The connection is executing (connecting... on the phone) but it does'nt stop!
```
 sudo msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync had an error while connecting: Unable to open anything
received event dsession
received contact dsession
received note dsession
Member 2 of type syncml-obex-client just connected

```

---

### Post by titof on 2007-02-06
synchronisation not works with the cable on the 3250 (not this option in Pc suite sync on the phone)

---

### Post by BatPenguin on 2007-02-07
Great instructions, excellent to see that something like this is possible! This feature really is a great addition to Evolution. 

Anyway, this might be a dumb question but does anybody know if this is possible with the Nokia 6810 or is it just simply wrong type of a phone for it? I'm not at all familiar with the different phone technologies so I don't even know what feature to start looking for from this phone's information to figure this if it's possible (if it "could be" supported with right settings). I've been trying to get it going by following instructions but it fails at:

Member 2 of type syncml-obex-client had an error while connecting: Link Error

So, I'd really appreciate any help on figuring out whether I'm wasting my time on trying to get it to work on this phone or whether it's just a configuration thing to get it going. Bluetooth connections with Wammu etc. work fine. Thanks!

---

### Post by Nano on 2007-02-08
I can't sync my N73 with ubuntu.
I tried with 2 usb bluetooth cards and no luck at all.
I keep getting:
```

$mariano@marte:/$ msynctool --sync nokia
Synchronizing group "nokia" 
Member 1 of type evo2-sync had an error while connecting: Unable to open anything
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members

```

Can anybody give me hints about this? I'm pretty much frustrated :(

---

### Post by Nano on 2007-02-08
Here some info, in case it might help:
```

sdptool browse 00:19:79:D0:9D:93
Browsing 00:19:79:D0:9D:93 ...
Service Name: AVRCP Target
Service Description: Audio Video Remote Control
Service Provider: Symbian Software Ltd.
Service RecHandle: 0x10000
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
    uint16: 0xf00

Service Name: SyncMLClient
Service RecHandle: 0x10019
Service Class ID List:
  UUID 128: 00000002-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000002-0000-1000-8000-0002ee000002)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x1001a
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 11
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Nokia OBEX PC Suite Services
Service RecHandle: 0x1001b
Service Class ID List:
  UUID 128: 00005005-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 12
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005005-0000-1000-8000-0002ee000001)
    Version: 0x0100

...

Service Name: Nokia SyncML Server
Service RecHandle: 0x1001c
Service Class ID List:
  UUID 128: 00005601-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 13
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005601-0000-1000-8000-0002ee000001)
    Version: 0x0100

...

Service Name: OBEX Object Push
Service RecHandle: 0x1001d
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 9
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100
...

```

msynctool --configure nokia 2
```

<config>
        <bluetooth_address>00:19:79:D0:9D:93</bluetooth_address>
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

msynctool --configure nokia 1
```

<?xml version="1.0"?>
<config>
<address_path>file:///home/mariano/.evolution/addressbook/local/system</address_path>
</config>

```

If any of you could help me I'd really appreciate it.
Thanks in advance

---

### Post by wahlau on 2007-03-12
> **Nano said:**
> Here some info, in case it might help:
```

Service Name: Nokia SyncML Server
Service RecHandle: 0x1001c
Service Class ID List:
  UUID 128: 00005601-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 13

```

msynctool --configure nokia 2
```

<config>
        <bluetooth_address>00:19:79:D0:9D:93</bluetooth_address>
        <bluetooth_channel>**13**</bluetooth_channel>
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


see whether bluetooth channel 13 will work for you. When i had my n73 with me, my configuration worked out fine. See my write up [here]("http://www.wahlau.org/series_60_3rd_edition_nokia_n73_synchronization_with_opensync_under_ubuntu_edgy")

---

### Post by Jeroensum on 2007-03-16
> **Nano said:**
> I can't sync my N73 with ubuntu.
I tried with 2 usb bluetooth cards and no luck at all.
I keep getting:
```

$mariano@marte:/$ msynctool --sync nokia
Synchronizing group "nokia" 
Member 1 of type evo2-sync had an error while connecting: Unable to open anything
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members

```

Can anybody give me hints about this? I'm pretty much frustrated :(

Can post your current configurations? 
```
msynctool --configure nokia 1
```
and
```
msynctool --configure nokia 2
```

---

### Post by Tagallo on 2007-03-24
The guide in the first topic is not up to date, somethings seams to have changed in the Repos...

Now the URL's are:
```

deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ edgy main
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ edgy main

```

Keys:
```

gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -

```

**multisync-qad now is multisync-gui**


Cheers
Thiago

---

### Post by naseem on 2007-04-21
works like a charm in a n91 in feisty (channel was 13)
thanks for the guide :lolflag:

---

### Post by TekNullOG on 2007-04-26
I got it all to work on Feisty with my Nokia E70 after 2-3 hours of playing around!

It wouldn't sync from the command line but then i gave the gui a try and it worked right away!

All 600 contact names and 300 calendar entries synced and the few to-do notes.

Some calendar entries seem weird though. Everything past 7pm in my calendar is 1 day off! For example, a friday night entry shows up in my thursday night but when i open the entry to modify it, the date and time are alright! Don't know how to change that! Weird!!! If anyone has any ideas, I would love the help!

Good How To!

---

### Post by TekNullOG on 2007-04-26
Here is some supplementary information concerning my sync.

Half of the calendar entries are using UTC and the other are using my local time? Is there any way around this?

On the bright side,
with more extensive testing, the contacts really work flawlessly! They sync perfectly both ways.

I would also recommend the multi-sync gui. It is really easy to use. I never managed to get the command line to work (after 3 hours of trying) but the GUI did with less than 5 mins of configs.

---

### Post by xdevnull on 2007-05-07
Has anyone tried to calbe sync a E62?  I was thinking about getting one as a need a new smartphone, however my laptop doesn't have bluetooth.  I noticed the E62 has a usb port and am hopeful.  I don't really feel like adding a bluetooth dongle to the rest of the stuff I have to carry.  I'm currently using Feisty Fawn --

Thanks for the help!

---

### Post by xdevnull on 2007-05-15
Hey - is anyone here?  So I got my new E62 and I am trying to see if I can sync it with usb and not bluetooth.  I'm using Feisty and installed the multisync gui.  For the evolution plugin, there are just pull down menus.  For the syncml-obex-client I have the following config:

```
<?xml version="1.0"?>
<config>
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
  <type>5</type>
  
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

To get the usb interface I go:
```
sudo syncml-obex-client -u
Password:
Found 3 USB OBEX interfaces
Interface 0:
        Manufacturer: Nokia
        Product: Nokia E62
        Interface description: SYNCML-SYNC
Interface 1:
        Manufacturer: Nokia
        Product: Nokia E62
        Interface description: PC Suite Services
Interface 2:
        Manufacturer: Nokia
        Product: Nokia E62
        Interface description: SYNCML-DM
Use '-u interface_number' to connect

```

I only want to sync my contacts and calendar.  I'd also like to install some apps - and move files, if anyone can figure that one out.  When I connect, the evolution seems to work, but then I get an error about the phone.  If I run it from the command line I get:
```
 msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Unable to connect to the interface
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error synchronizing: Unable to connect one of the members
Pipe closed! Exiting.
Pipe closed! Exiting.

```

One question I have is: how do I know if I have the latest libraries?  Is there some way to check that.  Does usb just not work with these phones?  Do I have to go and buy a bluetooth dongle?

Also - how do you add programs to the phone?  I noticed there is a disable objtype when setting up the phone:  I disabled todo and notes - I am also playing with disabling data - but I don't know what that is - is that actually transfering data - as in files/images/programs?

Thanks!

---

### Post by JCook21 on 2007-05-15
Hi everyone,

I'm trying to sync my N73 via bluetooth without any joy.  I tried this a few weeks ago and it didn't work so I removed all of the software I installed for this.  I've just tried re-installing it and I get this error message when trying to install msynctool:

Unpacking msynctool (from .../msynctool_0.22-feisty1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/msynctool_0.22-feisty1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/convcard.1.gz', which is also in package multisync-tools
Errors were encountered while processing:
 /var/cache/apt/archives/msynctool_0.22-feisty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

If I try to sync I get an error message saying error connecting next to syncml-obex-client saying error while connecting and unable to connect to one of the members.  Does anyone have any ideas on this as I'd love to get my N73 synchronised with Ubuntu?

---

### Post by xdevnull on 2007-05-15
OK - managed to answer my own question - I think:  
Can you use the usb cable to sync your phone:

Apparently - it is mentioned here:
[http://www.opensync.org/wiki/syncml-guide](http://www.opensync.org/wiki/syncml-guide)
Quote: if you use the syncml-obex-client, you can just use the normal --sync option. *Note that you have to run the msynctool as root to access the usb devices (normally).*

This sucks - is there any way around it on Feisty?  

I got this to work by
1. running evolution as root and creating an appointment and a contact
2. running multisync-gui as root
3. running the following configuration:
```
<?xml version="1.0"?>
<config>
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
  <type>5</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>
  
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
Anyone know of a way around the usb using root problem?  I guess I could point root to my own .evolution folders in my home directory - but I don't want those to suddenly be owned by root - and that is quite the kluge.

Any bright ideas?

---

### Post by xdevnull on 2007-05-16
Jcook

Are you having trouble installing the files?  It looks like there is a problem with a man file - you might try removing it and reinstally - not sure if you need that man file anyway to run the program.  I also notice you are installing from a feisty depository - but your profile says edgy.  Not sure which you are using...

---

### Post by JCook21 on 2007-05-16
> **xdevnull said:**
> Jcook

Are you having trouble installing the files?  It looks like there is a problem with a man file - you might try removing it and reinstally - not sure if you need that man file anyway to run the program.  I also notice you are installing from a feisty depository - but your profile says edgy.  Not sure which you are using...

Thanks for that-I'll try that later.  I am running Feisty but had forgotten to update my profile.  Sorry for the confusion!

---

### Post by JCook21 on 2007-05-16
Hi xdevnull,

Thanks for the suggestion but it didn't work.  I deleted the file /usr/share/man/man1/convcard.1.gz but msynctool still wouldn't install and gives exactly the same error.  Do you have any other ideas?

Thanks for the help and any other suggestions.

---

### Post by xdevnull on 2007-05-16
Hey - figured out how to use the cable from this post here:

[http://ubuntuforums.org/showthread.php?t=211810&highlight=mobile+phone+mount+usb](http://ubuntuforums.org/showthread.php?t=211810&highlight=mobile+phone+mount+usb)

I edited the 40-permissions file in /etc/udev and I can use obexftp to move files to the phone.  However, I am still having problems with sync.  When I run from the gui, it stalls, when I run from the command prompt I get:

```
msynctool --sync nokiaSynchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-464B35D600000007 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-464B354D00000005 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD00000020 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD0000001E with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD0000000F with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD00000006 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-464B36B500000008 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AF00000052 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AE00000046 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AE0000003C with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD00000018 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-464B36FC0000000A with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-464B36D500000009 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-464B31CC00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD0000001C with data of size 4 from member 1. Changetype ADDED
.......................................................
Received an entry pas-id-4638B5AE0000002F with data of size 4 from member 1. Changetype ADDED
Received an reply to our Alert
Received an reply to our Alert
Going to receive 0 changes
Going to receive 0 changes
Received an entry pas-id-4638B5AE00000026 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD00000023 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4638B5AD0000001F with data of size
............................
Received an entry 20070502T160051Z-13174-1000-1-181@tiny with data of size 4 from member 1. Changetype ADDED
Received an entry 20070502T160054Z-13174-1000-1-270@tiny with data of size 4 from member 1. Changetype ADDED
Received an entry 20070502T160050Z-13174-1000-1-110@tiny with data of size 4 from member 1. Changetype ADDED
Received an entry 20070502T160052Z-13174-1000-1-209@tiny with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.


```
The elipses are mine - let me know if I should include all the items.

It stops there and I never get a changes committed from obex.  The phone has a sync screen that just kind of sits there and says "synchronizing" but it stops there.  I also noticed that the sync seemed to hang when there was a conflict.  The phone reported the conflict, as did the multisync-gui.  I made the selection and it went away, but not on the phone.  Hmmmmm...

any ideas?

---

### Post by xdevnull on 2007-05-23
This should be my final post.  The reason I was having problems syncing is because the cursed E62 will not take monthly recurring events by the day of the week: eg. 2nd Tuesday of the month.  It vomits those back.  When I got rid of those the phone syncs, though I am using blue-tooth now becaue it is a bit easier.  I do think, however that the USB stuff should work.  Now my phone syncs, though I wish I could set up monthly meetings more easily.

---

### Post by nekr0z on 2007-05-23
Nice to see at least someone happy. My E50 still doesn't sync calendar, whatever I do.

---

### Post by JCook21 on 2007-05-24
Does anyone have any suggestions as to how I can get around the problems I'm having with msynctool?  I posted about this earlier and would be very grateful for any help.  One of things I really miss is being able to sync my phone with my computer.

---

### Post by jackirby on 2007-05-24
I tried installing with my N73 and got the following message:
Synchronizing group "nokia" 
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Request not successfull: 79
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error synchronizing: Unable to connect one of the members
Pipe closed! Exiting.
Pipe closed! Exiting.

I have already set my divice as trusted... so I don't know why it won't work... Please help!

Thanks,

Jason

---

### Post by bdogg64 on 2007-05-28
Thanks for the kubuntu guide. I was able to get this working with a Nokia E61i. I got the contacts to sync correctly, and the calendar synced up, but it synced the wrong time for my appointment, but I'll live with that for now.

B

---

### Post by jackirby on 2007-05-29
Thanks Heaps!!! the guide was great, I never would have found the tools necessary to do it without you... but you can update it now, I'm running 64bit Kubuntu and all the files needed are in the repositories, so no need to add the non-standard ones. I successfully synced my N73, but I had to remove all my thumbnails in order to do it (no biggy, only had a few) but it stops dead if there are any! keep up the great work!!!

---

### Post by TekNullOG on 2007-05-30
> **bdogg64 said:**
> Thanks for the kubuntu guide. I was able to get this working with a Nokia E61i. I got the contacts to sync correctly, and the calendar synced up, but it synced the wrong time for my appointment, but I'll live with that for now.

B

Did you ever manage to get the right times to sync? If you did, i would love to know!

Cheers

---

### Post by Todas on 2007-06-05
1. Add required repositories

Add following repositories to /etc/apt/sources.list:
Code:

deb [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main
deb-src [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) feisty main

Replace the 'feisty' with whatever distribution version you are using (edgy, dapper).

To add key for the repository, do the following:
Code:

gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -

apt-get update and apt-get upgrade

2. Install required software
Code:
"sudo aptitude install  libopensync0 opensyncutils msynctool mulstisync-qad bluez-passkey-gnome bluez-gnome libopensync-plugin-palm libopensync-plugin-moto libopensync-plugin-opie libopensync-plugin-kdepim libopensync-plugin-gpe libopensync-plugin-sunbird libopensync-plugin-evolution2-dev libopensync-plugin-file libopensync-plugin-google-calendar libopensync-plugin-synce libopensync-plugin-ldap libopensync-plugin-irmc libopensync-plugin-python libopensync-plugin-gnokii libopensync-plugin-evolution2 libopensync-plugin-syncml libopensync-plugin-jescs mulstisync-gui mulstisync-qad multisync"

do not install:
// "sudo aptitude install libopensync-plugin-* libopensync0 opensyncutils msynctool mulstisync-qad //bluez-passkey-gnome bluez-gnome"

3. Configure msynctool
You can configure opensync via a graphical interface using multisync-gui/multisync-qad (using similiar settings as below) or you can use command line. Guide below is for commandline. Note, that the commandline worked flawlessly on Feisty. You'll get even better results with GUI

Add a new group of preferred name (I'll be using nokia in this example):
Code:

start multisync-gui and add group nokia
click on _E_dit add members Evolution 2.x, and SyncML over OBEX Client

or commandline:

msynctool --addgroup nokia

Add plugins to group. If you get errors in this face, they are propably due to missing plugins so check you've installed all required plugins.
Code:

msynctool --addmember nokia evo2-sync
msynctool --addmember nokia syncml-obex-client

Next is the 'trickiest' part. Installed plugins need to be configured. First, you have to find your phone's MAC. Use hcitool to do that:
Code:

hcitool scan

It should return something like:
Code:

xx:xx:xx:xx:xx:xx PhoneName

Now, configure the syncml-obex-client:
Code:
multisync-gui:Double click on evo2sync make sure Addressbook/Calendar/Tasks all have "Personal" Selected. Next: Double click on syncml-obex-client  see Figure 10A below.

or  Command line:
msynctool --configure nokia 2

Replace the context of the configuration (should be open in separate editor after running previous command) with the following XML:
Figure 10A:

<config>
        <bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
        <bluetooth_channel>11</bluetooth_channel>
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
        <note_db>Notes</note_db>
</config>

Where bluetooth_address is your phone's MAC address you just discovered.

After configuring the syncml-obex-client it's time to configure evo2-sync. Open configuration file with command
Code:

skip:
/msynctool --configure nokia 1
/
/And modify it to look like:
/Code:
/
 /
/<?xml version="1.0"?>
/<config>
/<address_path>file:///home/USERNAME/.evolution/addressbook/local/system</address_path>
/</config>

/Replace USERNAME with your username.

Feisty note: With the latest update from jahn repositories, this works with defaults. You can configure Calendar as calendar_db to syncml-obex-client setup to make calendar syncing work

4. Sync!
You should be good to go now, so you should try synchronizing:
Code:
multisync-gui return to opening menu and make sure evolution is not running, next click on _R_efresh wait it make take some time but it should sync all contacts 

I also used the Bluetooth obex client to create a bond prior to syncing.

or Command line:
msynctool --sync nokia

Edit 2006-10-02: Notes can be extracted, but not yet to Evolution. I'm working on this

---

### Post by bdogg64 on 2007-06-13
> **eightinches said:**
> Did you ever manage to get the right times to sync? If you did, i would love to know!

Cheers

I synced my nokia e61i and it added my calendar entries with the correct time! I can't remember if the updates fixed something or what but its working correctly at the moment.

---

### Post by nekr0z on 2007-06-20
It all works with E50, there's only one problem: telephone doesn't accept any changes from Evo. It works in other direction, though. Any ideas on what the matter can be?

---

### Post by Stoff on 2007-06-26
I managed to sync Evolutions' calendar with my Nokia N 73. But one thing is strange: If I create an appointment in Evolution, sync it with the mobile and then try to delete it again, then this works only where I created the appointment. That is, I cannot delete the item in my mobile's calendar and thereby delete it in Evolution as well. I mean, it is not a big deal but it is strange nevertheless.

---

### Post by gravastar on 2007-07-29
Has anyone managed to sync Notes with evolution? 

Or is this still not working?

---

### Post by diehorsti on 2007-08-03
> **Todas said:**
> 

2. Install required software
Code:
"sudo aptitude install  libopensync0 opensyncutils msynctool mulstisync-qad bluez-passkey-gnome bluez-gnome libopensync-plugin-palm libopensync-plugin-moto libopensync-plugin-opie libopensync-plugin-kdepim libopensync-plugin-gpe libopensync-plugin-sunbird libopensync-plugin-evolution2-dev libopensync-plugin-file libopensync-plugin-google-calendar libopensync-plugin-synce libopensync-plugin-ldap libopensync-plugin-irmc libopensync-plugin-python libopensync-plugin-gnokii libopensync-plugin-evolution2 libopensync-plugin-syncml libopensync-plugin-jescs mulstisync-gui mulstisync-qad multisync"


Hi Todas,

I have noted, that you have a small typing mistake. You typed mulstisync-gui and mulstisync-qad instead of multisync-gui and multisync-qad.

This makes copy paste a little bit hard. :)

Cheers.

---

### Post by Ghosty.be on 2007-08-22
Just to report that i synced my contacts with evolution using ubuntu feisty and a nokia E65 with the above method, however i can not seem to get calendar entries nor notes synced with evolution (i added the Calendar entry in the calendar_db for the phone, but it seems this shows an error on the screen of the phone.)

---

### Post by Artanicus on 2007-08-24
The repos are down and probably will stay that way. Most of the packages are included anyways, but sync doesn't work:
'Error while initializing syncengine: Wrong obex type specified'

Im attempting this with the Nokia E90 via bluetooth.

Any ideas? Any chances on an updated howto?

edit: found the problem, my phone uses bluetooth channel 14, not 10.

But ran into some more serious trouble, heres the output:
> 
$ msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-4680C82000000000 with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.



And the phone shows an error roughly translatable as "System Error"

---

### Post by Ghosty.be on 2007-08-26
I added a some things i already found to work for my Nokia E65 to our LUG-wiki:
[http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)
(the site itself is dutch but i wrote the howto in english )

---

### Post by Nailor on 2007-08-27
> **Ghosty.be said:**
> I added a some things i already found to work for my Nokia E65 to our LUG-wiki:
[http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)
(the site itself is dutch but i wrote the howto in english )
I added the link to E65 howto on the first post, thanks.

---

### Post by Nailor on 2007-08-27
For the future: If you have howtos or something else you'd like to be in the first post, just post the thoughts here. I'm scanning this thread every now and then but I really don't have to test everything by myself.

---

### Post by lospo on 2007-08-27
About 7710 ?
I've got one of these, but i can't sync due this error:
> Error synchronizing: unable to connect one of the member.
 and after
> Evo2Sync -> Disconnected
syncml-obex-client -> Error while connecting

The sync failed: unable to connect one of the member.


These are the settings for my syncml-obex-client
> <?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>00:02:EE:97:F7:A7</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>Pc Suite</identifier>
  
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


And these are the services on my phone.
> ~$ sdptool browse 00:02:EE:97:F7:A7
Browsing 00:02:EE:97:F7:A7 ...
Service Name: Dial-Up Networking
Service RecHandle: 0x10000
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: Hands-Free Audio Gateway
Service RecHandle: 0x10001
Service Class ID List:
  "Handfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handfree Audio Gateway" (0x111f)
    Version: 0x0101

Service Name: SyncMLClient
Service RecHandle: 0x10002
Service Class ID List:
  UUID 128: 00000002-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000002-0000-1000-8000-0002ee000002)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x10003
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 11
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Nokia OBEX PC Suite Services
Service RecHandle: 0x10004
Service Class ID List:
  UUID 128: 00005005-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 12
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005005-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: NokiaSyncMLServer
Service RecHandle: 0x10005
Service Class ID List:
  UUID 128: 00005601-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 13
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005601-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: OBEX Object Push
Service RecHandle: 0x10006
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 9
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

In addiction :
phone and PC are pairedthrought the baloon question of gnome and the correct pin;
i can send file throught obex and gnome ;
i can receive files from phone throught the systray bluetooth server;


If someone can help me... i will appreciate! ;)

Thank you and sorry my english...

---

### Post by Ghosty.be on 2007-08-28
try to remove these 2:
<!-- The name of the calendar db. Must be the same as the phones sends -->
<calendar_db>Calendar</calendar_db>

<!-- The name of the note db. Must be the same as the phones sends -->
<note_db>Notes</note_db>

and on the evo config try to remove the paths for notes and calendar also, then try again (when i added these lines on my e65 it gave errors ...)

---

### Post by Dark Star on 2007-08-28
Thanks for the guide :)

---

### Post by lospo on 2007-08-28
> **Ghosty.be said:**
> try to remove these 2:
<!-- The name of the calendar db. Must be the same as the phones sends -->
<calendar_db>Calendar</calendar_db>

<!-- The name of the note db. Must be the same as the phones sends -->
<note_db>Notes</note_db>

and on the evo config try to remove the paths for notes and calendar also, then try again (when i added these lines on my e65 it gave errors ...)

No way, same error as bove... something like a bt connection error? the icon on my phone change to green for a a while, and after 2 seconds it return white...

Argh!

---

### Post by lospo on 2007-08-29
New step:
i try using 
> :~$ syncml-obex-client -b 00:02:EE:97:F7:A7 10 --slow-sync text/x-vcard Contacts --wbxml --identifier "PC Suite"


with this output:
> Received an transport error: Bluetooth connect error
Received an transport error: Link Error


BUT i have these two logs:
[PHP][1188404239.456379]	>>>>>>>  smlThreadStartCallback(0x60aa10)
[1188404239.456483]		+++++++++ This is the worker thread of thread 0x60aa10 for context 0x60a630 +++++++++
[1188404239.471046]		>>>>>>>  smlTransportWorkerHandler(0x60d200, 0x60a4b0)
[1188404239.471089]			>>>>>>>  smlTransportObexClientConnect(0x60b570)
[1188404239.471126]				connecting to bluetooth device 00:02:EE:97:F7:A7 channel 10
[1188404239.864157]				>>>>>>>  smlTransportReceiveEvent(0x60a4b0, (nil), 2, (nil), 0x60a830)
[1188404239.864360]					>>>>>>>  _smlManagerDataHandler(0x60a4b0, (nil), 2, (nil), 0x60a830, 0x60a5a0)
[1188404239.864419]						>>>>>>>  _smlManagerSendEvent(0x60a5a0, 2, (nil), (nil), (nil), 0x60e8d0)
[1188404239.864465]						<<<<<<<  _smlManagerSendEvent
[1188404239.864505]					<--- ERROR --- _smlManagerDataHandler: Bluetooth connect error
[1188404239.864553]				<<<<<<<  smlTransportReceiveEvent: 0
[1188404239.864591]			<--- ERROR --- smlTransportObexClientConnect: Bluetooth connect error
[1188404239.864629]		<<<<<<<  smlTransportWorkerHandler
[1188404239.864670]		>>>>>>>  smlTransportWorkerHandler(0x60d0b0, 0x60a4b0)
[1188404239.864708]			>>>>>>>  smlTransportObexClientSend(0x60b570, (nil), 0x60d3a0, (nil))
[1188404239.864750]				Adding connection id 0
[1188404239.864792]				Target application/vnd.syncml+wbxml
[1188404239.864862]				>>>>>>>  _smlObexEvent(0x60b720, 0x60f030, 0, 4, 2, 0)
[1188404239.864903]					Link Error: 0
[1188404239.864943]					>>>>>>>  smlTransportReceiveEvent(0x60a4b0, (nil), 2, (nil), 0x60a830)
[1188404239.864981]						>>>>>>>  _smlManagerDataHandler(0x60a4b0, (nil), 2, (nil), 0x60a830, 0x60a5a0)
[1188404239.865034]							>>>>>>>  _smlManagerSendEvent(0x60a5a0, 2, (nil), (nil), (nil), 0x60f6d0)
[1188404239.865072]							<<<<<<<  _smlManagerSendEvent
[1188404239.865109]						<--- ERROR --- _smlManagerDataHandler: Link Error
[1188404239.865146]					<<<<<<<  smlTransportReceiveEvent: 0
[1188404239.865182]				<--- ERROR --- _smlObexEvent: Link Error
[1188404239.865222]			<--- ERROR --- smlTransportObexClientSend: Unable to send put request. Bailing out
[1188404239.865263]			>>>>>>>  smlTransportDataDeref(0x60d3a0)
[1188404239.865299]			<<<<<<<  smlTransportDataDeref: refCount > 0
[1188404239.865335]		<<<<<<<  smlTransportWorkerHandler
[1188404239.885548]		>>>>>>>  smlTransportWorkerHandler(0x60d0b0, 0x60a4b0)
[1188404239.885592]			>>>>>>>  smlTransportObexClientDisconnect(0x60b570, (nil))
[1188404239.885645]				>>>>>>>  _smlObexEvent(0x60b720, 0x60dd60, 0, 4, 1, 0)
[1188404239.885683]					Link Error: 0
[1188404239.885724]					>>>>>>>  smlTransportReceiveEvent(0x60a4b0, (nil), 2, (nil), 0x60dde0)
[1188404239.885763]						>>>>>>>  _smlManagerDataHandler(0x60a4b0, (nil), 2, (nil), 0x60dde0, 0x60a5a0)
[1188404239.885806]							>>>>>>>  _smlManagerSendEvent(0x60a5a0, 2, (nil), (nil), (nil), 0x60e8d0)
[1188404239.885844]							<<<<<<<  _smlManagerSendEvent
[1188404239.885882]						<--- ERROR --- _smlManagerDataHandler: Link Error
[1188404239.885919]					<<<<<<<  smlTransportReceiveEvent: 0
[1188404239.885956]				<--- ERROR --- _smlObexEvent: Link Error
[1188404239.885996]			<--- ERROR --- smlTransportObexClientDisconnect: Unable to send disconnect request. Bailing out
[1188404239.886036]		<<<<<<<  smlTransportWorkerHandler
[1188404239.886079]		>>>>>>>  smlThreadStopCallback(0x60aa10)
[1188404239.886115]			+++++++++ Quitting worker thread +++++++++
[1188404239.886156]		<<<<<<<  smlThreadStopCallback
[1188404239.886196]	<<<<<<<  smlThreadStartCallback[/PHP]

and

[PHP][1188404239.456379]	>>>>>>>  smlThreadStartCallback(0x60aa10)
[1188404239.456483]		+++++++++ This is the worker thread of thread 0x60aa10 for context 0x60a630 +++++++++
[1188404239.471046]		>>>>>>>  smlTransportWorkerHandler(0x60d200, 0x60a4b0)
[1188404239.471089]			>>>>>>>  smlTransportObexClientConnect(0x60b570)
[1188404239.471126]				connecting to bluetooth device 00:02:EE:97:F7:A7 channel 10
[1188404239.864157]				>>>>>>>  smlTransportReceiveEvent(0x60a4b0, (nil), 2, (nil), 0x60a830)
[1188404239.864360]					>>>>>>>  _smlManagerDataHandler(0x60a4b0, (nil), 2, (nil), 0x60a830, 0x60a5a0)
[1188404239.864419]						>>>>>>>  _smlManagerSendEvent(0x60a5a0, 2, (nil), (nil), (nil), 0x60e8d0)
[1188404239.864465]						<<<<<<<  _smlManagerSendEvent
[1188404239.864505]					<--- ERROR --- _smlManagerDataHandler: Bluetooth connect error
[1188404239.864553]				<<<<<<<  smlTransportReceiveEvent: 0
[1188404239.864591]			<--- ERROR --- smlTransportObexClientConnect: Bluetooth connect error
[1188404239.864629]		<<<<<<<  smlTransportWorkerHandler
[1188404239.864670]		>>>>>>>  smlTransportWorkerHandler(0x60d0b0, 0x60a4b0)
[1188404239.864708]			>>>>>>>  smlTransportObexClientSend(0x60b570, (nil), 0x60d3a0, (nil))
[1188404239.864750]				Adding connection id 0
[1188404239.864792]				Target application/vnd.syncml+wbxml
[1188404239.864862]				>>>>>>>  _smlObexEvent(0x60b720, 0x60f030, 0, 4, 2, 0)
[1188404239.864903]					Link Error: 0
[1188404239.864943]					>>>>>>>  smlTransportReceiveEvent(0x60a4b0, (nil), 2, (nil), 0x60a830)
[1188404239.864981]						>>>>>>>  _smlManagerDataHandler(0x60a4b0, (nil), 2, (nil), 0x60a830, 0x60a5a0)
[1188404239.865034]							>>>>>>>  _smlManagerSendEvent(0x60a5a0, 2, (nil), (nil), (nil), 0x60f6d0)
[1188404239.865072]							<<<<<<<  _smlManagerSendEvent
[1188404239.865109]						<--- ERROR --- _smlManagerDataHandler: Link Error
[1188404239.865146]					<<<<<<<  smlTransportReceiveEvent: 0
[1188404239.865182]				<--- ERROR --- _smlObexEvent: Link Error
[1188404239.865222]			<--- ERROR --- smlTransportObexClientSend: Unable to send put request. Bailing out
[1188404239.865263]			>>>>>>>  smlTransportDataDeref(0x60d3a0)
[1188404239.865299]			<<<<<<<  smlTransportDataDeref: refCount > 0
[1188404239.865335]		<<<<<<<  smlTransportWorkerHandler
[1188404239.885548]		>>>>>>>  smlTransportWorkerHandler(0x60d0b0, 0x60a4b0)
[1188404239.885592]			>>>>>>>  smlTransportObexClientDisconnect(0x60b570, (nil))
[1188404239.885645]				>>>>>>>  _smlObexEvent(0x60b720, 0x60dd60, 0, 4, 1, 0)
[1188404239.885683]					Link Error: 0
[1188404239.885724]					>>>>>>>  smlTransportReceiveEvent(0x60a4b0, (nil), 2, (nil), 0x60dde0)
[1188404239.885763]						>>>>>>>  _smlManagerDataHandler(0x60a4b0, (nil), 2, (nil), 0x60dde0, 0x60a5a0)
[1188404239.885806]							>>>>>>>  _smlManagerSendEvent(0x60a5a0, 2, (nil), (nil), (nil), 0x60e8d0)
[1188404239.885844]							<<<<<<<  _smlManagerSendEvent
[1188404239.885882]						<--- ERROR --- _smlManagerDataHandler: Link Error
[1188404239.885919]					<<<<<<<  smlTransportReceiveEvent: 0
[1188404239.885956]				<--- ERROR --- _smlObexEvent: Link Error
[1188404239.885996]			<--- ERROR --- smlTransportObexClientDisconnect: Unable to send disconnect request. Bailing out
[1188404239.886036]		<<<<<<<  smlTransportWorkerHandler
[1188404239.886079]		>>>>>>>  smlThreadStopCallback(0x60aa10)
[1188404239.886115]			+++++++++ Quitting worker thread +++++++++
[1188404239.886156]		<<<<<<<  smlThreadStopCallback
[1188404239.886196]	<<<<<<<  smlThreadStartCallback[/PHP]

If someone know something..... please help me!

---

### Post by Ghosty.be on 2007-08-30
Kristian Bäckström sent me a mail reporting this: 

The former jahn
ubuntu repo ([http://www.in.fh-merseburg.de/~jahn/opensync/](http://www.in.fh-merseburg.de/~jahn/opensync/)) seem to
have moved: at least opensync.org points to

[http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/)

so the sources list can be updated to:


deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main
deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main

gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -


So i changed this on my wiki page.

---

### Post by neetu on 2007-09-03
The repos are down and probably will stay that way. Most of the packages are included anyways, but sync doesn't work:
'Error while initializing syncengine: Wrong obex type specified'

Im attempting this with the Nokia E90 via bluetooth.

Any ideas? Any chances on an updated howto?

edit: found the problem, my phone uses bluetooth channel 14, not 10.

But ran into some more serious trouble, heres the output:
Quote:
$ msynctool --sync nokia
Synchronizing group "nokia"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-4680C82000000000 with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.
And the phone shows an error roughly translatable as "System Error"

[url=http://www.homephoneline.co.uk%5dhome phone line[/url]

---

### Post by neetu on 2007-09-03
try to remove these 2:
<!-- The name of the calendar db. Must be the same as the phones sends -->
<calendar_db>Calendar</calendar_db>

<!-- The name of the note db. Must be the same as the phones sends -->
<note_db>Notes</note_db>

and on the evo config try to remove the paths for notes and calendar also, then try again (when i added these lines on my e65 it gave errors ...)

 [home phone line](http://www.homephoneline.co.uk)

---

### Post by Nailor on 2007-09-04
> **Ghosty.be said:**
> Kristian Bäckström sent me a mail reporting this: 

The former jahn
ubuntu repo ([http://www.in.fh-merseburg.de/~jahn/opensync/](http://www.in.fh-merseburg.de/~jahn/opensync/)) seem to
have moved: at least opensync.org points to

[http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/)

so the sources list can be updated to:


deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main
deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main

gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -


So i changed this on my wiki page.

I updated those on the front page too.

---

### Post by Ghosty.be on 2007-09-04
And again an update to the wiki page:

I got the calendar sync working!

see: 
[http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)

i think this should also work for other similar phones based on symbian 6 v3, please send me feedback about other phones so i can add them to the page.

/edit: also added some channel information this night, stuff i just found out from someone on IRC.

---

### Post by rahaydenuk on 2007-09-04
> **Ghosty.be said:**
> And again an update to the wiki page:

I got the calendar sync working!

see: 
[http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)

i think this should also work for other similar phones based on symbian 6 v3, please send me feedback about other phones so i can add them to the page.

Hi,

I am trying to get calendar sync to work with the google calendar plugin on an E65.

My syncml-obex-client config is:
```

<config>
<bluetooth_address>00:17:E5:B5:A0:E9</bluetooth_address>
<bluetooth_channel>14</bluetooth_channel>
<identifier>PC Suite</identifier>
<version>1</version>
<wbxml>1</wbxml>
<username></username>
<password></password>
<type>2</type>
<usestringtable>1</usestringtable>
<onlyreplace>0</onlyreplace>
<!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
<onlyLocaltime>0</onlyLocaltime>
<!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
<recvLimit>0</recvLimit>
<maxObjSize>0</maxObjSize>
<contact_db></contact_db>
<calendar_db>Calendar</calendar_db>
<note_db></note_db>
</config>

```
and my Google config is obviously correct (just requires username and password).

msynctool --sync e65 gives:
```

Synchronizing group "e65"
The previous synchronization was unclean. Slow-syncing
Member 1 of type google-calendar just connected
received event dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an reply to our Alert
Member 2 of type syncml-obex-client just sent all changes
xs to osync: 2007-09-11T09:00:00.000+01:00 => 20070911T090000
xs to osync: 2007-09-11T10:00:00.000+01:00 => 20070911T100000
Received an entry http%3a%2f%2fwww%2egoogle%2ecom%2fcalendar%2ffeeds%2fr%2ehayden%2540gmail%2ecom%2fprivate%2ffull%2fl9ubqn9jf0iagrmi3k41qhm5og with data of size 8 from member 1. Changetype ADDED
Member 1 of type google-calendar just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type google-calendar committed all changes.

```
So it seems like it's doing something. msynctool never exits though and the phone displays a really useful "System error". No appointments have been copied in either direction.

Any ideas?

Thanks,

Richard.

---

### Post by Ghosty.be on 2007-09-05
Probably you did something wrong, I just tested it with my google calendar and it works like a charm :) 

Thanks btw for pointing me to the google calendar plugin, didn't look at that one yet ;)

description follows in a few hours when I'm at home

/edit: description added

---

### Post by eflux2007 on 2007-09-06
Hi,

I just sync my new e65 with evolution. everything fine following the howto.

then I sync my e65 with Outlook to retrieve my old contact from my old Qtek. ok using USB cable and PC suite.

after that, when triyng to sync with Ubuntu with bluetooht never end.
I get this message : 
"....
Conflict not ignored: Ignore is not supported for this mapping
Conflict for Mapping 0x83720d0: Conflict ignored
Conflict not ignored: Ignore is not supported for this mapping
All conflicts have been reported
"
but nothing happen more, then the sync is cancelled by time out (I can see it in report menu on my phone)

thanks for your help,
Benoit.

edit : so I gave up trying to sync my old Qtek with my new e65... i'll do it later, see my post down now about google calendar and evolution sync

---

### Post by Ghosty.be on 2007-09-06
have you tried "rebooting" your phone in between? (turning it off and then back on again?) 
cant really help with this because I don't use outlook at home (and hope I will never need to ...)

---

### Post by Ghosty.be on 2007-09-10
And another update to the wiki: now it is possible to sync calendar and contacts in 1 profile.

---

### Post by nekr0z on 2007-09-11
Ghosty.be, you're doing a great job and I think we all appreciate it!

I just wonder if a repo for Gutsy can be made already...

---

### Post by eflux2007 on 2007-09-11
Hi gave up trying to sync my old contacts from Qtek to e65.
but seems that the "time out" come from another reason.

I now try to sync : 

evolution & nokia e65
AND
google calendar & nokia e65

I put my script here to help, not sure it's full running, I'm still in testing mode. any comments welcome :

script launch with crontab :

code : 
#!/bin/sh
if test -f $HOME/.opensync/group1/lock
then 	rm $HOME/.opensync/group1/lock
fi
if test -f $HOME/.opensync/group2/lock
then 	rm $HOME/.opensync/group2/lock
fi
# conflit 1 ->  sync gmail' advantage over nokia
msynctool --conflict 1 --sync gmail
# conflit 1 -> sync nokia has advantage over evolution
msynctool --conflict 2 --sync nokia

if test -f $HOME/.opensync/group1/lock
then 	rm $HOME/.opensync/group1/lock
fi
if test -f $HOME/.opensync/group2/lock
then 	rm $HOME/.opensync/group2/lock
fi
# conflit 1 ->  sync gmail' advantage over nokia
msynctool --conflict 1 --sync gmail
# conflit 1 -> sync nokia has advantage over evolution
msynctool --conflict 2 --sync nokia

the result is that adding new appointment in google calenda is ok
but then deleting an entry made with nokia, is not deleted in google calendar...

I'm still trying doing a full duplex synchro, I'll post my results here,

best regards to all and thanks for your good tutorials !
Benoit.

---

### Post by Ghosty.be on 2007-09-12
nekr0z: i'm still looking for a way to rebuild the packages for Feisty 64 bit (since i run 64 bit on my desktop at home ...)
If anyone knows how to rebuild packages from the source repoistory...?

eflux2007: right you are, indeed when you delete an appointment on your phone it does not remove it on the google calendar, did not notice this yet. Will have a talk with some developers to see if they can adapt the google calendar plugin perhaps ...

---

### Post by Ghosty.be on 2007-10-04
added a small detail: seems the phone is localized: some people need to use the localized name for contacts ... :confused:

---

### Post by wallygator.uk on 2007-10-04
i everyone and thanks for this genius howto, after a few hrs i managed to do it, i'm new to linux.

 i just managed to work it out with a nokia n95 but calendars are not sync and contacts look very very messed up, as they only show the first number under mobile, ignoring other mobile numbers (home (business) etc as well as some other number (contact showin only the name)

i guess that this is because the detail label on the phone contact does not match the evolution header

is there any way to get around it? i tried to change the header on evolution but it does not seem to me there is a way to do it (at least in a graphical way, not really into coding, sorry for my ignorance)

many thanks

---

### Post by kiddyfurby on 2007-10-07
is anyone using gutsy?

gutsy have its own libopensync, which is at 0.19.*
the repos have 0.21.*
the latest version is 0.31.*

I don't care whether i m using latest version
anyone got gutsy syncing with symbian?

---

### Post by hfdragon on 2007-10-21
I just upgraded to gutsy and sync isn't working anymore.

With feisty, I synced my Nokia 6110 Navigator with Evolution Contacts & Calendar without any problem... now the sync fails :-(

Am I the only one ?

---

### Post by kiddyfurby on 2007-10-22
The packages have new name / version in gutsy

Install the packages:
```
sudo aptitude install opensyncutils opensync-plugin-evolution opensync-plugin-syncml multisync-tools multisync0.90
```then follow the guide on first page from step 3, or use the gui multisync-qad

---

### Post by nekr0z on 2007-10-22
Wrong. The packages kiddyfurby listed are old, version 0.19, while the packages we need are v. 0.22. The proper packages are not yet available for Gutsy.

---

### Post by xdevnull on 2007-10-22
I'm having trouble with my E62/evolution now that I'm on Gutsy.  I had some trouble, then copied over my old config file.  The contacts will sync, but having trouble with the calendar.  It shows the records transfering, completes and disconnects, but it won't show up.  I also notice that if you set the evolution setting for tasks to No Tasks, it errors out.  It used to not do that. Do I need to upgrade something.  I basically went to synaptic and installed the packages there - multisync-qac, tools, evol plugin and syncml plugin.  Hmmm...Should I try and compile 0.22 plugins?

Here's my config:

<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>xxxxxxxxxx</bluetooth_address>
  
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

---

### Post by kiddyfurby on 2007-10-23
> **nekr0z said:**
> Wrong. The packages kiddyfurby listed are old, version 0.19, while the packages we need are v. 0.22. The proper packages are not yet available for Gutsy.
yes they are 0.19
but I have contacts and calendar syncing w/o problem

---

### Post by chrismine on 2007-10-23
I got sync to work with my Nokia 6234 with the default repositories and file versions in Gutsy.

I can sync my contacts, Calendars but not my notes. I had to edit the syncml-obex-client configuration file to look like this:   <calendar_db>Calendar</calendar_db>
What I did is to input the word Calendar in between >< because it were empty.

This did not work for notes.

Any ideas will be welcome.

Thanks.

---

### Post by hfdragon on 2007-10-23
Ok, I put the good repos and installed the good packages.

Contacts & Calendar are syncing OK

Has anyone managed to sync notes with Evolution ?

---

### Post by kiddyfurby on 2007-10-24
i guess evolution just doesn't support vNotes
calendar and contacts are vCal and vCard...

btw, what do u mean by good repos and good packages?

---

### Post by davidme on 2007-10-24
Has anyone been able to sync Nokia (N73) with Evolution and Ubuntu Gutsy ? I followed all the guides and still get messages like this one:

"Received an entry pas-id-47157ADF00000003 with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
"


Help. Please post your exact configs and actions.

---

### Post by hfdragon on 2007-10-24
> **kiddyfurby said:**
> 
btw, what do u mean by good repos and good packages?

I mean those in the howto in page 1 of this thread ;)

---

### Post by hfdragon on 2007-10-24
> **kiddyfurby said:**
> i guess evolution just doesn't support vNotes
calendar and contacts are vCal and vCard...

Yes, It seems that evolution uses the VJOURNAL standard to store notes, and the nokia phones (and Opensync)  the VNOTES standard.

I'll try to fill a ticket about that in the OpenSync trac [http://www.opensync.org/]("http://www.opensync.org/")

---

### Post by xdevnull on 2007-10-24
I tried using those repositories - still not able to get it to sync, especially on the calendar.  I wonder if I should install the feisty program names instead of the gutsy.  This is a real pain - to be able to do something in feisty and then have it break in gutsy.  What's the deal?

---

### Post by Ghosty.be on 2007-10-25
have added some notes to my manual, no news on gutsy yet (just installed it myself, did not make time to install the opensync from the custom repository, tomorrow maybe...) 
From what i have seen the versions in gutsy are 0.19 but the latest packaged ones are 0.22 (yet it is still a feisty repository, but the packages are newer then the existing gutsy packages, will see if i can reach a developer to help fix new packages - and hopefully also 64 bit  versions? )  

[http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)

---

### Post by xdevnull on 2007-10-28
Any luck?  I tried using all old feisty lib at the "good" feisty repos and still no calendar sync.  It's really iritating to have it work in feisty and then broken in gutsy.  What is the deal?

---

### Post by xdevnull on 2007-10-30
I'm still not getting any love.  The problem is, I'm not getting any errors and the thing isn't hanging.  It looks like the information is getting sent.  The phone sends it and the msync tool shows them being copied.  There's the changes committed and the disconection, but NO calendar stuff shows up in Evolution.  

I've got a feeling that there is something going on in with the sync modules - maybe something with the updated version of evolution - that is breaking.

---

### Post by Bjerrum on 2007-10-31
I also try to get my N73 phone synced with Evolution. I managed to get contacts from the phone, but now it stall. The phone tells me it's syncing, but nothing happen.

Get this in terminal:

Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-4727A76600000027 with data of size 4 from member 1. Changetype ADDED
...
xmlEscapeEntities : char out of range
...
Received an reply to our Alert
Received an reply to our Alert
Received an entry pas-id-4727A76600000049 with data of size 4 from member 1. Changetype ADDED
Going to receive 0 changes
...
Received an entry 20071031T112735Z-6480-1000-1-6@sb-ubuntu with data of size 4 from member 1. Changetype ADDED
...
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
xmlEscapeEntities : char out of range
xmlEscapeEntities : char out of range
xmlEscapeEntities : char out of range
xmlEscapeEntities : char out of range
Member 1 of type evo2-sync committed all changes.

Any ideas :confused:

---

### Post by jmesquita on 2007-11-02
Hello guys, I am a little bit confused on how to sync my Nokia E61 Calendar and Contacts since I am using Ubuntu Gutsy (7.10). Here is what I tried and what went wrong:

Installing the packages from gutsy's repo:
Result: No sync at all. Got a "System Error!" message on the phone and msynctool hung.

Installing the packages from custom repo (on the 1 post) with gutsys names:
Result:

I could sync my phones contacts into Evolution and the way back too. But that was not enough for me so I edited this file:
```
msynctool --configure nokiacon 2
```

to replace this line:

```
<calendar_db>Calendar</calendar_db>
```

Well, there's where things started getting messy. I got this message back after lots of added an entry and all:

```

Received an entry 154 with data of size 4 from member 2. Changetype ADDED
Received an entry 155 with data of size 4 from member 2. Changetype ADDED
Member 2 of type syncml-obex-client had an error while getting changes: Link Error
Member 1 of type evo2-sync just disconnected

```

Well. msynctool gets hung forever there.

Is Calendar syncing supported for E61 or any other Nokia S60 phones?


Other then that, how do I transfer files to my phone using bluetooth on Gutsy?

Mesquita

---

### Post by jmesquita on 2007-11-02
Ok, figured some things out. First of all I realized that OpenSync is on the early stages of development and in desperate need of work to be useful. Second is that the sources found on the website are not working on Ubuntu Gutsy Gibbons since the evolution plugin is for evolution-data-server version 2 (Gutsy has 1.12).

Syncing contacts work sometimes and sometimes it doesn't. My experience tells me that we are no quite there yet. Shouldn't Ubuntu have a GUI developed to sync different phones and PDAs? Isn't that something we all use and need on an OS? I digress...

Anyway, I guess until Gutsy deploys evolution-data-server 2 or someone package opensync for Gutsy, we are out of luck. :(

Did anyone get a different feeling or better result?

Thanks

Mesquita

---

### Post by orbister on 2007-11-03
Has anyone any idea about syncing a Nokia 6120 Classic (also Symbian 60)?

I've got the bluetooth side of things working fine, and I can transfer file in both directions. When I try and syncronize contacts I get a very very brief progress bar on the phone, then "System Error".

I've used sdptool to check that SyncML Server is on channel 13, and my syncml-obex setup is

```
<config>
        <bluetooth_address>00:1B:AF:58:EB:4E</bluetooth_address>
        <bluetooth_channel>13</bluetooth_channel>
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
```

If I change <contact_db>Contacts</contact_db> to anything else there is no error, but nothing happens either, so as far as I can see the phone is attempting to send the contacts and is then encountering a problem.

---

### Post by otto67 on 2007-11-06
Strange to see so many problems:
In my case it is well working in Gutsy with my Nokia E70 (3rd edition)

** NB! **
In my following exemple/history I presume that you can make bluetooth connection between your laptop and Nokia-phone. Your laptop must be in the phone's BT devices list and connections from there are allowed.
On the phone in "Sync profile settings" the protocol is "Bluetooth", server version is "1.1" no username, no password, Sync calls is "Yes", Authorization is "Yes"
In the following I describe only computer-side syncing configuration (not BT pairing, not phone sync settings, for this look other howtos)

To make it work on my laptop i followed many howtos and advises of my friend but shortly it works like this:

1. Remove all previous .multisync and .opensync folders in your Home-directory

2. Install needed packages for multisync and openync. I didnt mess with special repos because packages in standard repos are working well (0.19-family)
First I messed a little bit with packages because in some howtos they were different than in others or some cases not present in repositories.
At the moment I have following "sync" packages installed (all from standard gutsy repositories)
------------
libmultisync-plugin-irmc
libmultisync-plugin-irmc-bluetooth
libopensync0
libpisync0
libsyncml0
multisync
multisync0.90
multisync-tools
opensync-plugin-evolution
opensync-plugin-file
opensync-plugin-google-calendar
opensync-plugin-irmc
opensync-plugin-syncml
opensyncutils
python-opensync
rsync
----------
I dont know exactly what is doing every package but as whole the solution is working
The crucial package is "**multisync0.90**" which in other distros/ubuntus was "multisync-qad". This is the necessary graphical frontend. It was confusing because all howtos indicated "multisync-qad" which not exist anymore in gutsy repos.

3) Now when packages installed you have to open "Applications - Accessories - Multisync-qad"
It will open graphical small nice program to do all the rest.

4) Click on "Add"
5) Enter a group name: nokia  
Then click Apply
6) Click on the button "Edit"
7) Then "Add Member"
 a) choose "Evolution 2.x"
 b) choose "SyncML over OBEX Client"
 Then OK
Click on "evo2-sync"
Check that Addressbook, Calendar, Todos are marked "Personal"
9) Click on "syncml-obex-client"
delete the existing content and paste the following text:
--------------- 
[I] <config> 
<bluetooth_address>xxxxxxxxxxxxxxx</bluetooth_address> 
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
<recvLimit>10000</recvLimit> 
<maxObjSize>0</maxObjSize> 
<contact_db>Contacts</contact_db> 
<calendar_db>Calendar</calendar_db> 
<note_db>Notes</note_db> 
</config>[/I]
------------------
replace xxxxxxxxxxxxxxx with the bluetooth address of your phone (hcitool scan)

Then close and you are 99% done.

9) Remarque NB!: First sync I had hangup but after discovered that "Notes" on the phone are causing this. So I deleted all notes from my phone (I dont use them very much)

10) Now click "Refresh" and this start syncing.

** NB! Confusing but important part:**
Very first syncing is extremely long and you can have even timeout message from phone. But dont be afraid. Actually the thing is working. If you look your "gnome-system-monitor" then you see that multisync is not working but a plugin is taking up to 50% of your CPU. It means that syncing is going on and plugin compares and analyses all huge data from phone and evolution. If you get timeout or other error message from he phone then simply restart syncing from Multisync-qad. 
The main goal now is to get first "Healthy sync" ie. your phone says "Sync complete" and computer says: "Sync OK. All clients have written. The sync was successful." 
If multisync asks which conflicting entry in database you prefer, I always answer evo2-sync

Now it can happen that phone says: "Sync complete" but on your laptop you get message "Cannot write one or more objects". And this can happen many times.
My solution to this is that you open "Multisync-qad" and edit the "syncml-obex-client" conf. In last 4 rows i just removed some entries (Calendar and Notes) like this:
-------
...
[I] <contact_db>Contacts</contact_db> 
<calendar_db></calendar_db> 
<note_db></note_db> 
</config>[/I]
...
----------
and then start Sync again. You can combine which entry to remove in "syncml-obex-client" conf- for ex. remove Contacts and let the Calendar. The goal is to get "Healthy sync" ie. your phone says "Sync complete" and computer says: "Sync OK. All clients have written.The sync was successful." If it happens you simply add now again Calendar- entry and Notes- entry in "syncml-obex-client" conf and sync again.
And finally you get your 1st "Healthy Sync". Afterwards the syncing is very fast - only changes are compared and written vice-versa.
I hope this can help someone and avoid messing with this commandline text editors for "syncml-obex-client" editing. 

** Double entries.**
If you have a occasional syncing error (f.ex. you forgot to swhitch on your laptop bluetooth or similar) then multisync always does "slow sync". With "slow sync" it can happen that you will have double / triple similar entries in your phones calendar.
My solution: I open phones calendar - then "Select all" and "Delete" i.e. I erase all events in phone calendar and then sync and all events come correctly from Evolution to phone again.
Thats because I try to keep Evolution Contacts-Calendar always in good shape.

---

### Post by jmesquita on 2007-11-06
On my nokia E61 I only get "System Error" on the phone with this opensync version. If upgraded to version .22 using custom repos, I get a better picture but still no Notes or Calendar syncing.


Mesquita

---

### Post by rimoth on 2007-11-07
Thanks Otto67 - great explanation. I now have n73 synchronizing with Evolution on Gutsy Gibbon.

---

### Post by Capix on 2007-11-13
Hi,

I have an N73 and Gutsy and i'm not able to sync with Evolution.

I've tried to sync them on my home PC and on my office Pc too without success. I've tried Otto's configuration changing the blueetooth channels to:

09 (OBEX Object Push)
10(Sync MLClient)
11 (OBEX File Transfer)
12 (OBEX PC Suite Services)
and 13 (SyncML Server)

I think that in N73 it should work with the last one but no way. I always get the same error on the command line (with msynctool --sync N73):

```

Synchronizing group "N73" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-4732E3A300000003 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4732E8CA00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4733195E00000002 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47387D9600000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-473953F000000002 with data of size 4 from member 1. Changetype ADDED
(a lot of these lines....)
Received an reply to our Alert
Received an entry pas-id-4732EA8600000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-4733195E00000004 with data of size 4 from member 1. Changetype ADDED
(more and more lines like these)
Received an entry pas-id-473953F00000004C with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.

```

N73 throws a "System Error" message and msynctool it just hangs until I press CTRL+C and 

Blueetooth is working because i can send files to my N73 with gnome-obex-server but i'm still unable to sync with Evolution.

Any ideas?

Many thanks!

---

### Post by otto67 on 2007-11-13
As i explained in my howto, the first sync is extremely slow and can take up so 10 minutes. Usually you will have timeout from phone. But then simply sync again and again. I recommend to delete all Notes from phone and Evolution.
Dont be afraid if the sync is long - look at gnome-system-monitor and look if some plugin is working. If yes , then the sync is going on. Dont interrupt it with Ctrl+C.
The channel 10 is correct because it has been working always. 

As far as i understand your terminal message your sync is going on and some plugin is working (look gnome-system-monitor) because you have been informed that conflicts reported
To compare i simply add my /usr/bin/multisync0.90 messages on terminal after a successful sync:
mina@Ott-ML:~$ /usr/bin/multisync0.90
[I]Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
received note dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Received an reply to our Alert
Going to receive 0 changes
Going to receive 0 changes
Going to receive 0 changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
Member 1 of type evo2-sync committed all changes.
Member 1 of type evo2-sync just disconnected
Received an reply to our sync
Received an reply to our sync
Received an reply to our sync
Member 2 of type syncml-obex-client committed all changes.
All clients have written
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync was successful[/I]

As you see your clients sent changes but are not writing (yet) the differences.
Pls try again my howto - i am almost sure that the BT channel is 10 it should not be different from one Nokia to another (my phone is E70).
Pls simplify also your Evolutions calendar or phonebook or Notes. F.ex. i discovered that in my phone i had lot of Notes created occasionally, /simply if keys are unlocked and your phone is in your pocket/ with text like "W" or "arddfs" or "sdfgert" etc, etc, Check once more and delete all these unclean entries in your phone. In my case i had always timeouts because entries like this take huge ressource from the syncing software and it is not able to "digest" these. When i deleted Notes from my phone the things went better immediately. It didnt "hang" anymore and started display messages. Actually hanging means (in my opinion) that some plugin is trying to sync the data received from clients and put it into a logical form for both clients to write it back.
You can try to play also with syncml-obex-client conf as described in my howto i.e. delete Calendar, Notes and try to get first "clean sync" and then add Calendar and Notes step-by-step back in the conf file.
I hope you can understand what i am trying to say.

---

### Post by Capix on 2007-11-13
Many thanks for your reply Otto but I forgotted to say that I got an "System error" message on my phone. 

Althought I will retry with a "clean sync" and i will wait more for the sync to stop.

PS: Having tried for a while and process msynctool, osplugin... in gnome-system-monitor as shown as "Sleeping"

---

### Post by otto67 on 2007-11-13
me too - if i remember correctly i got the same message "System error" (i called it "timeout" in my posts). The osplugin says like it would be "Sleeping" but look at the CPU % , in my case it has shown 40-50 % when first syncing ie. it was actually working (hardly).
As i remember i got these messages from phone until i deleted all Notes from phone (and also from Evolution)
Pls try once more and keep us in touch...

---

### Post by Capix on 2007-11-13
CPU is at 0% on each process :( 

I've been waiting for 10 minutes, do you think that I've to wait much more?

BTW what do you think about the "pairing process" that i found in this website:

[http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)

It's necessary for the sync?

---

### Post by rimoth on 2007-11-13
For the first sync I just sync'd contacts and then added calendar in for the next sync.

---

### Post by rimoth on 2007-11-13
Also I think the Bluetooth channel for the N73 is 13 which I picked up from page 4 of this thread.

---

### Post by arvind_cse on 2007-11-13
I just now got my N70 synced with evolution contacts, To do list, Calendar with Ubuntu 7.04

Make sure you have paired the phone before proceeding.

Once successfully paired you should see your phone when you browse for 

**obex://** from nautilus (explorer window)

I ran into trouble trying to pair bluetooth from command prompt as the phone couldn't identify my ubuntu. 

To fix this i used **System -> preferences -> Bluetooth Preferences** 
and selected the option **Visible and connectable for other devices**
and **Make adapter invisible after:** to never.

My LAPTOP - COMPAQ V3425 AU with Broadcom wireless

This should fix the pairing issue

Try the following configuration for **syncml-obex-client**
using the command ** msynctool --configure nokia 2**

<?xml version="1.0"?>
<config>
<bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
<bluetooth_channel>11</bluetooth_channel>
<interface>0</interface>
<identifier>PC Suite</identifier>

<!-- **Changed to version 0 from 1 ** -->
<version>**0**</version>
<wbxml>1</wbxml>
<username></username>
<password></password>
<type>2</type>
<usestringtable>0</usestringtable>
<onlyreplace>0</onlyreplace>
<onlyLocaltime>0</onlyLocaltime>
<!--** set the limit to 10000** -->
<recvLimit>**10000**</recvLimit>
<maxObjSize>0</maxObjSize>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<!-- **Remove the notes db as its not working** -->
<note_db></note_db>
</config>

Got this working after lots of trial and errors. 

As said by otto67 it takes a lot of time for the first time.

You can give this a try.

---

### Post by otto67 on 2007-11-13
Correctly paired devices is a must for syncing. You should be able to transfer files from your phone to laptop and vice-versa. If it does work OK then you can try syncing. In laptop I have bluetooth-services running all the time and in phone BT menu i have my computer included in "Allowed BT devices". 
When i sync the BT connection starts automatically without error or any special authorization

---

### Post by Bjerrum on 2007-11-13
I got the adress sync to work with my N73. But not the calender. After a lot of lines it gives me this:

```

** (process:6734): WARNING **: invalid escape, passing it through. escaped char was 115

** (process:6734): WARNING **: invalid escape, passing it through. escaped char was 83

** (process:6734): WARNING **: invalid escape, passing it through. escaped char was 97
Pipe closed! Exiting.
Pipe closed! Exiting.
Segmentation fault (core dumped

```

There is many of this escape lines with tree different char. 115, 97 and 83. Could it be the silly danish special character æ,ø,å?

---

### Post by gatman3 on 2007-11-14
If it helps anyone, I have just today successfully synced Contacts, Calendar and Notes (in KDE Kontact) with my new Nokia N75 and 7.10 (Gutsy).  Perhaps it syncs in similar fashion to the N70 and/or N73, don't know, but I found very little info on the web specifically about the syncing the N75.

The key for me was installing the libopensync-plugin-kdepim package instead of opensync-plugin-kdepim.  I could not find any info as to why the Gutsy repositories include these two conflicting packages with slightly different names.  Note that the opensync-plugin-* packages are at revision 0.19-2 while the libopensync-plugin-* packages are at revision 0.22-feisty1.  My Nokia N75 synced the Contacts (address book) properly with the 0.19-2 version of the libraries but wouldn't sync the Calendar.  It gave similar errors to some of the ones that have been listed in this thread.  After switching to the 0.22-feisty1 libraries (libopensync-plugin-*) now everything works.  Perhaps the same is true for the other libraries associated with plugins for evolution, google-calendar, etc., don't know for sure.

Here is my syncml-obex-client.conf file, if it is helpful to anyone:

<config>
<username></username>
<password></password>
<type>2</type>
<bluetooth_address>00:19:79:32:27:6A</bluetooth_address>
<bluetooth_channel>10</bluetooth_channel>
<interface>0</interface>
<version>0</version>
<identifier>PC Suite</identifier>
<wbxml>1</wbxml>
<recvLimit>10000</recvLimit>
<maxObjSize>1</maxObjSize>
<usestringtable>0</usestringtable>
<onlyreplace>0</onlyreplace>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<note_db></note_db>
</config>

And the command I use to sync is:

msynctool --sync N75-KDE --conflict n

(my group name is N75-KDE, and I have it configured to always use the newest entry from either the phone or the Kontact database, which seems to work great).

Note that I just noticed that I don't even have the proper name for the Notes (note_db) entry in my config file, and yet I'm quite certain that syncing the Notes database is working properly.  Weird.  I'll have to experiment more with that.

Following arvind_cse's suggestions earlier in this thread, I have version 0 selected in the config file, yet the phone can only select version 1.1 or version 1.2, and I have the phone in version 1.1 mode.  Not sure if it's significant or not, it was just left over from some of my shotgun fix attempts based on someone's suggestion.

Good luck to all.  I am now madly in love with my new Symbian phone and its ability to sync with Kubuntu.  I just switched from Verizon to AT&T so that I could get a phone with more open capabilities (to hell with Verizon and their incessant need to lock out useful phone capabilities!)  This made my day, and it'll hold me off until the neo1973 is ready for prime time.

EDIT:  I just realized that the libopensync* packages came from Matthias Jahn.  I had added them to my repository and some point and forgotten about it.  Here is the repo info that I added to my /etc/apt/sources.list:

deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main
deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main

This actually provides version 0.22-feisty2 libraries which seem to be required to get the N75 calendar and notes working.  I think that the N75 address book works with the 0.19 libraries included in Gutsy.

---

### Post by Capix on 2007-11-14
mmmm... I think that my problem is pairing because I can send and receive files but i can't see "obex://" folder in Nautilus or Konqueror :(

I'm googling because i've tried:

```
System -> preferences -> Bluetooth Preferences
and selected the option Visible and connectable for other devices
and Make adapter invisible after: to never.

```

But nothing...

---

### Post by Junge on 2007-11-15
After spending some time getting the syncing to work with a Nokia N70 on feisty it finally works, but.......

After the phone is done sending the contacts and agenda items to the computer the computer automatically starts sending the same agenda items back to my phone, but this time as contacts! 

Since I don't want over 600 agenda items in my contact list I was wondering if someone knew how to prevent this?

---

### Post by Junge on 2007-11-16
> **Junge said:**
> After spending some time getting the syncing to work with a Nokia N70 on feisty it finally works, but.......

After the phone is done sending the contacts and agenda items to the computer the computer automatically starts sending the same agenda items back to my phone, but this time as contacts! 

Since I don't want over 600 agenda items in my contact list I was wondering if someone knew how to prevent this?


Never mind... It now suddenly works?

---

### Post by SyncAddict on 2007-11-17
OMFG I just synced my contacts between my Ubuntu Gutsy AMD/32bit box and my Nokia N73 phone. Unable to use to GUI for now, but a happy camper using the CLI :-)

There were some initial problems where my phone would stop sending or would report an error. There were also errors in my terminal about unknown BASE64 encoding. So I ended up removing all the JPEG images for my contacts using my iBook / iSync. After that the syncing with Ubuntu started working. Slow sync at first, but things look good for now. Only tried contacts though, so nu data on events/calendar from here.

I think this is one of the last pieces of functionality that required me to keep Mac OS X around. Too bad that Ubuntu dropped PPC support ;)

---

### Post by Capix on 2007-11-18
> **SyncAddict said:**
> OMFG I just synced my contacts between my Ubuntu Gutsy AMD/32bit box and my Nokia N73 phone. Unable to use to GUI for now, but a happy camper using the CLI :-)

There were some initial problems where my phone would stop sending or would report an error. There were also errors in my terminal about unknown BASE64 encoding. So I ended up removing all the JPEG images for my contacts using my iBook / iSync. After that the syncing with Ubuntu started working. Slow sync at first, but things look good for now. Only tried contacts though, so nu data on events/calendar from here.

I think this is one of the last pieces of functionality that required me to keep Mac OS X around. Too bad that Ubuntu dropped PPC support ;)

How do you pair your phone with Ubuntu? I've been trying many ways but i can't see "obex://" folder in Nautilus or Konqueror.

Can anyone explain it to me like if i was a 4-years-old-ubuntu-newbie? Many thanks

---

### Post by SyncAddict on 2007-11-18
> **Capix said:**
> How do you pair your phone with Ubuntu? I've been trying many ways but i can't see "obex://" folder in Nautilus or Konqueror.

Can anyone explain it to me like if i was a 4-years-old-ubuntu-newbie? Many thanks

I already had paring worked out for Ubuntu -> UMTS Internet access. A small snippit from the UMTS / GPRS / EDGE HOWTO: 

Pairing

You can skip this section if you've already paired your phone with your computer. However, consider the final optional step, as your phone might otherwise nag you every time you use if for dialup.

    *  Run the following, replacing your-phone-mac-address with the proper data

sudo hcitool cc your-phone-mac-address

    *Run the following, replacing your-phone-mac-address with the proper data

sudo hcitool auth your-phone-mac-address

    *  Enter a numeric code into the dialog box that pops up. If no dialog box pops up, run the following in another window

sudo passkey-agent --default /usr/bin/bluez-pin

Hope this helps

Reference : [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

---

### Post by Capix on 2007-11-20
When I follow your steps I get the following message:

>sudo passkey-agent --default /usr/bin/bluez-pin
Can't register passkey agent
Passkey agent already exists


It's very extrange because i can send and receive files throught bluetooth without asking any confirmation (so are they paired?) but still can't sync with evolution :( 

It's very frustating.

---

### Post by rents1977 on 2007-11-20
Newbie here, though I've managed to get everything else I want to work so far, I have a problem with an E65, Evolution and Gutsy. 

Contacts worked 'straight out the box' following the guide on page 1, but when I try to sync the Calendar I get the "system error" message on the phone screen. 

The following is from the console - with most of the contact syncing lines taken out:

```
x@x-desktop:~$ msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-4742C5F500000005 with data of size 4 from member 1. Changetype ADDED
.
.
.
Received an entry pas-id-4742C5F60000000E with data of size 4 from member 1. Changetype ADDED
xmlEscapeEntities : char out of range
.
.
.
Received an entry pas-id-4742C5F600000029 with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
xmlEscapeEntities : char out of range
xmlEscapeEntities : char out of range
Member 1 of type evo2-sync committed all changes.

```

Pretty similiar to **[Bjerrum]("http://ubuntuforums.org/showpost.php?p=3676904&postcount=157")**

I deleted all notes as per suggestions in this thread, but to no avail.

I've tried to replicate the data on
[http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65](http://www.ugov.be/wiki/index.php/Ubuntu_with_Nokia_E65)
exactly, since they got an E65 and Calendar to work, but on Feisty rather than Gutsy.

I tried to install all the packages mentioned in **[this post]("http://ubuntuforums.org/showpost.php?p=3716125&postcount=161")**. But still no dice. Unlike **otto67** I have nothing using any % of CPU.

I'm wondering if I should revert to Feisty? I don't think there is much I would miss from Gutsy, and if I understand correctly, because I have a separate mount point for my home directory, I wont lose any of my Evolution or other personal files if I just run the Feisty installer and point it to /?

---

### Post by llnk on 2007-11-22
Thanks!

---

### Post by truthwork on 2007-11-25
Does anyone know how to sync gutsy with the nokia e51?

---

### Post by ubermenschx on 2007-11-28
Followed your directions in 7.10 on a Dell 1420 syncing to my E62 and it worked perfectly.

Thanks,

G

---

### Post by Spanarn on 2007-11-29
Thanks Nailo, the HOWTO you posted on October 25th, 2007 works for Ubuntu 7.10 and my Nokia N73, using firmware V4.0763.3.2.1, using the built in Bluetooth in my nx9420 laptop.

He's a tip for setting up sync with both Windows and Evolution, or syncing with more then one computer.

In the phone open up the Sync application and create a new sync profile.
Use the PC Sync values, change the following:
Sync profile name: Evolution
And in Connection settings use:
Server version: 1.1
Data berarer: Blutooth
Host addres: Evolution
User name: 
Password
Alow sync requsets: Yes
Accept all...: Yes

And use this syncml config
```

<?xml version="1.0"?>
<config>
	<bluetooth_address>INSERT BT ADDRESS</bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel> 
	<identifier>Evolution</identifier>
  
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

  <onlyLocaltime>0</onlyLocaltime>
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

This solved my problems with not getting all calendar data from my phone:)

I started getting duplicates in my calendar, but i think i hav solved that with my new config...

/Daniel

---

### Post by apalacheno on 2007-12-03
Exactly the same issue with a Nokia 6110 Navigator (which is a Symbian Series 60 rev. 3 too) - reading contacts, calendar and notes to the file system using file-sync works fine, but as soon as I want to write calendar entries using sunbird-sync, I get the infamous 'system error' message and nothing gets sync'ed.

I get the following output:
```

ro@thinkpad:~$ msynctool --sync Calendar
Synchronizing group "Calendar" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type sunbird-sync just connected
received event dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
   *[snip...]*
Received an entry  with data of size 4 from member 1 (sunbird-sync). Changetype ADDED
Received an entry  with data of size 4 from member 1 (sunbird-sync). Changetype ADDED
Received an entry  with data of size 4 from member 1 (sunbird-sync). Changetype ADDED
   *[snip...]*
Received an entry eb2ef720-1040-11d9-a3d7-818b5a56c2aa with data of size 4 from member 1 (sunbird-sync). Changetype ADDED
Received an entry 7579b200-154e-11d9-bcf1-e3e2645a8143 with data of size 4 from member 1 (sunbird-sync). Changetype ADDED
Received an entry 949915a0-154e-11d9-9e76-d63252860658 with data of size 4 from member 1 (sunbird-sync). Changetype ADDED
   *[snip...]*
Member 1 of type sunbird-sync just sent all changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type sunbird-sync committed all changes.

```

Seems to me to be an error with opensync... However, a working solution would be nice anyway :)

---

### Post by tion on 2007-12-03
> **Bjerrum said:**
> I got the adress sync to work with my N73. But not the calender. After a lot of lines it gives me this:

```

** (process:6734): WARNING **: invalid escape, passing it through. escaped char was 115

** (process:6734): WARNING **: invalid escape, passing it through. escaped char was 83

** (process:6734): WARNING **: invalid escape, passing it through. escaped char was 97
Pipe closed! Exiting.
Pipe closed! Exiting.
Segmentation fault (core dumped

```

There is many of this escape lines with tree different char. 115, 97 and 83. Could it be the silly danish special character æ,ø,å?

I have the same problem with my N70. Did you find a solution to this problem Bjerrum? I have searched all over the place, but couln't find any solution.. My contacts transfer just fine, and I have norwegian letters Æ Ø Å in them. Anyone else having this problem?

---

### Post by adrianmak on 2007-12-05
dell insprison 1420 notebook.
bluetooth is work properly as I can browse the file system of the phone.
Then I followed the 1st post instruction and made ubuntu 7.10 work with my sonyericsson t610 phone

Since t61 only support irMC syncronization so irmc-sync should be should used instead of syncml-obex-client


mysynctool --configure SonyEricsson 1
```

<?xml version="1.0"?>
<config>

<address_path>file:///home/grace/.evolution/addressbook/local/system</address_path>

</config>

```

msynctool --configure SonyEricsson 2
```

<config>
  <donttellsync>false</donttellsync>
  <connectmedium>bluetooth</connectmedium>
  <btunit>00:0A:D9:91:1D:4D</btunit>
  <btchannel>11</btchannel>
</config>

```



```

msynctool  --sync SonyEricsson
Synchronizing group "SonyEricsson" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected


```
the phone shown up a message "Synchronizing". But after a long long time, more than half an hour, the synchronization didn't stop

What's going wrong ?

---

### Post by subs on 2007-12-06
would u have a similar mod for gutsy??

---

### Post by promoove on 2007-12-11
I'll throw my tuppence in then.

Please forgive me for any inaccuracies but I still consider myself a newbie.

I've read through this extremely clear thread and I managed to get to the point 
where my two devices (Nokia E61 and an old Dell Dimension L733r with GG) were 
bluetooth paired.

Using Multisync-qad I've even managed to sync my E61 with Evolution at least 3 times but:
- I never managed to get a clean total sync
- I now have duplicate and triplicate entries that I'll need to delete one by one
- I get some sort of lost connection/can't write anymore records kind of error (I won't try to sync again as it'll take me ages to go through some 1200 entries to 
check for duplicates...)

If it can be of any help, I also installed these packages:

libopensync0 Feisty 0.22
libopensync-plugin-evolution2 Feisty 0.22
libopensync-plugin-evolution2-dev Feistty 0.22
libopensync-plugin-file Feisty 0.22
multisync0.90 0.91.0.4
multisync-tools 0.91.0.4
opensync-plugin-syncml 0.19.1
opensyncutils 0.22

I will try to give it a shot through USB cable and keep you posted.
The sync process as it is now its useless, unreliable. That is, for me :lolflag:

---

### Post by apalacheno on 2007-12-11
you have to make sure that opensync and all plugins have the same versions (in your case 0.22), otherwise you surely get some problems. maybe that's the reason for your experience?

---

### Post by tictactatic on 2007-12-11
Hi, I've been trying to sync my Nokia E65 with Kontact on Gutsy, following several HOWTOs. My laptop and my phone are paired correctly, so it seems, but when I run msynctool --sync nokia I get the following problem:


```
libkcal: ERROR: Can't read uid map file '/home/voce/.kde/share/apps/kcal/uidmaps/remote_DddPSVRszN'
Member 1 of type kdepim-sync just connected
received event dsession
received contact dsession
received note dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry 3jPqFPa9gJ with data of size 4 from member 1. Changetype ADDED
Received an entry 6ijp7k0pLK with data of size 4 from member 1. Changetype ADDED
Received an entry 7N1JKn5D7r with data of size 4 from member 1. Changetype ADDED
Received an entry AcmY3QM4fD with data of size 4 from member 1. Changetype ADDED
Received an entry E7iN119EiT with data of size 4 from member 1. Changetype ADDED
Received an entry ETsUCg8NcP with data of size 4 from member 1. Changetype ADDED
Received an entry HNQVWPXy73 with data of size 4 from member 1. Changetype ADDED
Received an entry Ke6WNkKEMF with data of size 4 from member 1. Changetype ADDED
Received an entry KhXtmOuCeg with data of size 4 from member 1. Changetype ADDED
Received an entry LfraMI7dhk with data of size 4 from member 1. Changetype ADDED
Received an entry OaVfIPqjHh with data of size 4 from member 1. Changetype ADDED
Received an entry UGs3qBFEU2 with data of size 4 from member 1. Changetype ADDED
Received an entry ZYZgBGYhGH with data of size 4 from member 1. Changetype ADDED
Received an entry bNx2sNuYZH with data of size 4 from member 1. Changetype ADDED
Received an entry iHM3zLpR25 with data of size 4 from member 1. Changetype ADDED
Received an entry iUbG7ufqee with data of size 4 from member 1. Changetype ADDED
Received an entry jll2WdnIqK with data of size 4 from member 1. Changetype ADDED
Received an entry kaKBj3Ztxr with data of size 4 from member 1. Changetype ADDED
Received an entry ku6q52jl33 with data of size 4 from member 1. Changetype ADDED
KCrash: Application 'libopensync-kdepim-plugin' crashing...
Received an entry lqvRRL5Zrn with data of size 4 from member 1. Changetype ADDED
Received an entry mWxQIuz2aT with data of size 4 from member 1. Changetype ADDED
Received an entry pTFZJvQIoK with data of size 4 from member 1. Changetype ADDED
Received an entry pvrisfLos3 with data of size 4 from member 1. Changetype ADDED
Member 1 of type kdepim-sync had an error while getting changes: Broken Pipe
Member 1 of type kdepim-sync had an error while disconnecting: Broken Pipe

``` 

The syncml-obex-client part seems to work well enough (no ugly errors), and the whole process ends with:

```
Member 2 of type syncml-obex-client just sent all changes
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error synchronizing: Unable to read from one of the members
Pipe closed! Exiting.
```

As far as I can decipher this, there is something wrong with the way kdepim-sync is working. Any Kontact users out there who have it configured properly under Gutsy?

---

### Post by oc666 on 2008-01-02
I'm trying to configure my sunbird with nokia e61. I configured it, but I don't sure what I need to put in the config of sunbird-sync.
If I left it empty I get the next error:> Error while initializing syncengine: (null)

---

### Post by mafitzpatrick on 2008-01-05
First up before you sync can I recommend taking a backup of your calendar! I've gone around in circles trying to solve the sync problem and it gets pretty boring deleting manually.

I'm not sure about Evolution but for Kontact (under KDE) you can find the calendar files in /home/****username****/.kde/share/apps/korganizer/ with a filename ending in .ics   - if you make a copy of this you can then copy it back when it all goes wrong.

If you've ended up with duplicates on your mobile device the way to clear them is a bit more complicated: Basically start from an empty calendar in your application and then open up this folder /home/martin/.opensync/group1/ 

This holds the "state" information for opensync. You basically want to delete any files in that folder (and subfolders) with the extension .db   Do this and then sync and all the calendar entries will be copied back into your app.  

They're still duplicated!!! That's true. But the magic thing is that if you now delete them and resync it will wipe them off your mobile device.  In Kontact you can wipe them quickly by going to File -> Archive and selecting a date in the future (2500 for example) and select the checkbox to "Delete only, do not save". Hopefully Evolution has something similar?

Now you can copy back the backup you made earlier (you did, didn't you?), go through the process of deleting the .db files again and then resync. Voila. Nice and clean.

Working on how to avoid the duplicates at the moment...

---

### Post by mafitzpatrick on 2008-01-05
While I'm here: Does anyone have any idea what the "Use String Table" option does? I've looked around and found no documentation at all. Very odd. Tried syncing with it off for a change (originally had it switched on as per this howto) and it worked absolutely fine.

---

### Post by mindhaq on 2008-01-06
I found a solution for always getting duplicate entries on my Nokia 6280.

[http://www.opensync.org/changeset/1482](http://www.opensync.org/changeset/1482)

Add the following line to syncml-obex-client.conf

[HTML]<onlyLocaltime>1</onlyLocaltime> [/HTML]

However, since upgrading to Gutsy it became impossible to sync with Evolution, only between syncml and files. So where are the gutsy-compiled versions, like jmesquita wished for in November?

Error message is "Member 2 of type evo2-sync had an error while connecting: Unable to open anything."

---

### Post by mafitzpatrick on 2008-01-09
I'm no longer getting duplicates on my setup and it's working fine.  Two things to be behind that: I've set "use string table" option to OFF (or 0 in the configfile).  I don't know why/if that has any effect as there is no documentation of what it is for, but, since changing it I have no duplication.

Also make sure (on KDE) to log out of Kontact completely before syncing.  

Again not sure if that was the reason for the dupes either: all I know is they are the two things I've changed and it now works a dream!

---

### Post by frediE on 2008-01-10
I know this post is for the e-series but after three days of blue<in the face>tooth I hope I get a little respect.  :-)

Desktop -> Bluetooth -> Nokia 6133

All bluetooth turned on - good
Search for devices - good
Pairing - good

Browse device - bad
  Bluetooth issue "obex://[xx: xx: xx: xx: xx: xx]" is not a valid location.
  Found solution "sudo aptitude install gnome-vfs-obexftp"

Browse device (round 2) - bad
  Couldn't display "obex://[xx :xx :xx: xx: xx: xx]".
  Found solution - Right-click on the bluetooth applet and select "Preferences", go to the "Services" tab, left-click on "Input service", click the "Add" button, select your input device & connect.

Browse device (round three) - good
  Third time was the charm.  browsing devices and grabbing files.


Oh now we are going to sync....
follow the steps from first post (still don't understand the diff between Multisync and Mulitsync0.90).  

All is installed and no sync.  - bad
Found other posts that state the Nokia does not support irmc but only supports syncml-obex-client.

Removed irmc-bluetooth and installed the syncml-obex

Sync - bad
After much trial and error (random number really) i think i am close.  I click on sync and it just sits there.  no errors yet and its been a while.


Question is any thoughts on how long the first sync should take?  When using Nokia suite to sync (past life), the phone would show "synchronizing" in the screen.  I am not getting that now.  Does that mean nothing is happening or is it stealth with multisync0.90.


Last question.... is there any way to know my settings are correct in the bluetooth configuration.  This is what I am currently trying to use but as I mentioned before most of the numbers (yes besides the bluetooth address) are guesses.

[FONT=Courier New] <config>
    <bluetooth_address>XX:XX:XX:XX:XX:XX</bluetooth_address>
    <bluetooth_channel>13</bluetooth_channel>
    <interface>0</interface>
    <identifier>PC Suite</identifier>
    <version>1</version>
    <wbxml>1</wbxml>
    <username></username>
    <password></password>
    <type>2</type>
    <usestringtable>1</usestringtable>
    <onlyreplace>0</onlyreplace>
    <recvLimit>10000</recvLimit>
    <maxObjSize>0</maxObjSize>
    <contact_db>addressbook</contact_db>
    <calendar_db></calendar_db>
    <note_db></note_db>
</config>
[/FONT] 

Much Please and Thanks for the help! :)

---

### Post by mafitzpatrick on 2008-01-10
fredie: Are you using the updated packages (these are not in the Ubuntu repositories, so you need to add them to your package manager):

deb [http://opensync.gforge.punktart.de/repo/opensync-0.21](http://opensync.gforge.punktart.de/repo/opensync-0.21) fiesty main
deb-src  [http://opensync.gforge.punktart.de/repo/opensync-0.21](http://opensync.gforge.punktart.de/repo/opensync-0.21) fiesty main

You then need to add the keys for security by running the following in a terminal:

```

gpg --keyserver hkp://subkeys.pgp.net/ --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -

```

Once you've done that, open up your package manager and refresh the package list (if it hasn't done it already). You'll see updates for opensync. If you install them you should find that the sync now works correctly.

[More instructions here](http://opensync.gforge.punktart.de/repo/opensync-0.21/)

Hope that helps.

---

### Post by frediE on 2008-01-10
Oh that step #1.  I am running Gutsy 64-bit.
Anyone know of 64-bit OpenSync repositories?

---

### Post by frediE on 2008-01-11
Also looks like there maybe some challenges with the OpenSync url?
I was getting 404 page not found.  I had to remove the trailing "/" and it seem to pull in all the open sycn packages just fine.

```
deb http://opensync.gforge.punktart.de/repo/opensync-0.21 fiesty main

```

---

### Post by selorant on 2008-01-13
My phone is not E-series, but I think that from here I could found answer why I cant't get things work? So my phone is Nokia 6500c and Gutsy is OS.

When I try to sync to my phone, phone says 
```
Initializinc syncronasation
``` and after that 
```
Data transfer not possible. 
```
In the promt I get message 
```

Member 2 of type syncml-obex-client had an error while getting changes: Request not successfull: 68
```

Setting for phone connection is:
```

<config>
        <bluetooth_address>XXXXXXXXXX</bluetooth_address>
        <bluetooth_channel>11</bluetooth_channel>
        <interface>0</interface>
        <identifier>PC Suite</identifier>
        <version>1</version>
        <wbxml>1</wbxml>
        <username></username>
        <password></password>
        <type>2</type>
        <usestringtable>0</usestringtable>
        <onlyreplace>0</onlyreplace>
        <recvLimit>0</recvLimit>
        <maxObjSize>0</maxObjSize>
        <calendar_db>calendar</calendar_db>
</config>

```

I think that problem is in the database names?!? I have tried different variations of names but not get it work...I have also  tried one db at the time or all three (contacts, address and notes). 

Anyone could help me???

---

### Post by nischg on 2008-01-13
I've been trying to set blueZync and blueZync 4 thunderbird extension ([http://bluezync.kaarposoft.dk/](http://bluezync.kaarposoft.dk/))  to sync my Nokia e62 with Thunderbird but I need at least version 0.34 of OpenSync to be installed.
I haven't been able to install it, but blueZync and T'bird extension looks promising to what I want.

Does any one know how to install a newer version of OpenSync without messing everything up?

---

### Post by mafitzpatrick on 2008-01-13
selorant: As far as I know the databases must be with correct capitalisation: Use "Contacts" instead of "contacts" and "Calendar" instead of "calendar" etc.

Not obvious I know. Also you might want to try de-selecting them and syncing one at a time to see which one works. I only sync the calendar and I'm not sure where notes would sync to anyway.

Hope that helps.

---

### Post by selorant on 2008-01-13
> **mafitzpatrick said:**
> selorant: As far as I know the databases must be with correct capitalisation: Use "Contacts" instead of "contacts" and "Calendar" instead of "calendar" etc.

Not obvious I know. Also you might want to try de-selecting them and syncing one at a time to see which one works. I only sync the calendar and I'm not sure where notes would sync to anyway.

Hope that helps.

I have tried different names with different capitalasation... Calendar, calendar, cal, Kalenteri (finnish). Also one at the time. Not succeeded:(

Is there anyway to found out these database names from the phone??? Or could test something else?

---

### Post by nekr0z on 2008-01-13
The phone's databeses names can be figured out from menu Communication -> Sync. You select a profile ("PC Sync"), go to editing it and look for "Applications" section. There's a "Database name" entry for each application (addressbook, calendar, etc.)

---

### Post by selorant on 2008-01-13
> **nekr0z said:**
> The phone's databeses names can be figured out from menu Communication -> Sync. You select a profile ("PC Sync"), go to editing it and look for "Applications" section. There's a "Database name" entry for each application (addressbook, calendar, etc.)

Now I found those names, but in Nokia 6500 PC Sync gives only options to choose name and password. In th chance phone -> sync -> I see those names... If I chance language, names chance. Not get It still work.

I tried also sync N73 (there I can found nicely those database names) in this case phone says "system error". in the promt I get this message:
```

Member 1 of type evo2-sync just connected
received event dsession
received contact dsession
received note dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Received an reply to our Alert
Received an reply to our Alert
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
Member 1 of type evo2-sync committed all changes.
Member 1 of type evo2-sync just disconnected

```
settings was:
```

<config>
<bluetooth_address>XX:XX:XX:XX:XX</bluetooth_address>
<bluetooth_channel>13</bluetooth_channel>
<interface>0</interface>
<identifier>PC Suite</identifier>
<version>1</version>
<wbxml>1</wbxml>
<username></username>
<password></password>
<type>2</type>
<usestringtable>1</usestringtable>
<onlyreplace>0</onlyreplace>
<recvLimit>10000</recvLimit>
<maxObjSize>0</maxObjSize>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<note_db>Notes</note_db>
</config>

```
My plan is not to get this N73 to work with my PC, I only tried if I could get that connected easily. No I start think that there is some problem in my PC and these installation. Problem is that I don't know where? :confused:

---

### Post by Jingo on 2008-02-10
> **truthwork said:**
> Does anyone know how to sync gutsy with the nokia e51?
It does work somehow on E51.

But..

I'm getting duplicate calendar entries while syncronizing with evolution. Anyone know a solution?

Det syncronized meeting entries start and end at the same time.
ex: meeting 12. feb. 2008 from 12:00 to 14:00 in evolution => 12:00 to 12:00 on the phone!?
What would be the problem?

---

### Post by Jingo on 2008-02-10
Edit: Duplicate post... sorry!

---

### Post by ltdunbar on 2008-02-11
> **Jingo said:**
> It does work somehow on E51.

But..

I'm getting duplicate calendar entries while syncronizing with evolution. Anyone know a solution?

Would you post your config file for E51? I cannot get calendar synchronization at all...

Thanks!

---

### Post by Jingo on 2008-02-11
> **ltdunbar said:**
> Would you post your config file for E51? I cannot get calendar synchronization at all...

Thanks!

Sure!

Actually I used channel 10, but channel 14 should be the right one.
Did create a special "Evolution" profile on the phone's sync app.

```
<?xml version="1.0"?>
<config>
	<bluetooth_address>BTADDRESS</bluetooth_address>
	<bluetooth_channel>14</bluetooth_channel> 
	<identifier>Evolution</identifier>
  
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

  <onlyLocaltime>0</onlyLocaltime>
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

---

### Post by ltdunbar on 2008-02-11
Thanks, I copied it, and pasted my MAC, but unfortunately unless I disable Calendar and Notes, I keep getting System Error on my E51. :-(

---

### Post by half_monkey on 2008-02-11
Hi,
I've got a Nokia 5610, and have been tinkering with various versions of everything above. currently i'm on opensync 0.22 (compiled from the release source tarball ([http://opensync.org/download/releases/0.22/]("http://opensync.org/download/releases/0.22/")), and i get the following output:

```
$ /usr/local/bin/msynctool --sync noktest
Synchronizing group "noktest"
Member 2 of type file-sync just connected
received contact dsession
Member 1 of type syncml-obex-client just connected
All clients connected or error
Member 2 of type file-sync just sent all changes
Member 1 of type syncml-obex-client had an error while getting changes: Request not successfull: 68
Member 2 of type file-sync just disconnected
Member 1 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members
```

The configuration for the syncml plugin is as follows:
```
<config>
<bluetooth_address>XX:XX:XX:XX:XX:XX</bluetooth_address>
<bluetooth_channel>11</bluetooth_channel>
<interface>0</interface>
<identifier>PC Suite</identifier>
<version>1</version>
<wbxml>1</wbxml>
<username></username>
<password></password>
<type>2</type>
<usestringtable>1</usestringtable>
<onlyLocaltime>0</onlyLocaltime>
<onlyreplace>0</onlyreplace>
<recvLimit>10000</recvLimit>
<maxObjSize>0</maxObjSize>
<contact_db>Contacts</contact_db>
<calendar_db></calendar_db>
<note_db></note_db>
</config>
```

(where XX:XX... is the bluetooth address of my phone). What does the error number 68 mean? Has anyone else had this problem? Has anyone found a solution?

Cheers

---

### Post by Jingo on 2008-02-12
Something here: [http://opensync.org/wiki/Model_E51](http://opensync.org/wiki/Model_E51)

The libsyncml in the feisty repo is version 0.4.4. The wiki says libsyncml earlier than 0.4.6 did not sync calendar proporly!

Edit: Also se opensync mailinglist: [http://news.gmane.org/group/gmane.comp.misc.opensync.user/last=/force_load=t](http://news.gmane.org/group/gmane.comp.misc.opensync.user/last=/force_load=t)

---

### Post by Jingo on 2008-02-14
I now got it working on my Nokia E51. With libsyncml version 0.4.4.

Some hint on the mailinglist said installing MMSsync via Nokia Pc Suite on windows did some magic! I installed it by accident, don't know if it changed anything. Anyway now it works for me.

On the phone:
[LIST=1]
[*]Create a Sync profile, named "Evolution"
[*]SyncML version 1.1
[*]Connect using bluetooth
[*]I disabled every "program" except "Calendar"
[*]Calendar database "Calendar"
[*]Sync in both directions
[/LIST]

On the PC:
Repo
```
deb http://opensync.gforge.punktart.de/repo/opensync-0.21 fiesty main
```
```
sudo aptitude install opensync libsyncml-utils
```

Try:
```
syncml-obex-client -b $MAC $CHANNEL --slow-sync text/x-vcalendar Calendar --wbxml --identifier "Evolution"
```
Where $MAC = Bluetooth adress, and $CHANNEL = 10

Should give a dump of your phones calendar.

Config - only changes channel to 10:
```
<?xml version="1.0"?>
<config>
	<bluetooth_address>BT MAC</bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel> 
	<identifier>Evolution</identifier>
  
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

  <onlyLocaltime>0</onlyLocaltime>
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

Group consists of evo2-sync and syncml-obex-client.

---

### Post by SwiftNano on 2008-02-24
Hi everyone I have been struggling with this all weekend and have finally cracked it with evolution and my N95 8GB.

I had managed to get the contacts to sync but any calendar events caused a system error on the phone and the sync process to hang. Experienced by many on this forum from what I read.

The main reason it took so long is that I was ignoring part of Nailor's original post assuming that gusty would have the latest versions of OpenSync in its repo's.

Gusty's repo's have version 0.19 of all the opensync stuff. So to make this all work add the feisty repo's and keys and update opensync and all its plugins.

This works for me now with contacts calendar and to-do's. Thanks nailor for a great howto and I will not be assuming that the latest distro release has all the latest versions of everything again.

Please let me know if anyone wants any more info as I would be please to help although I am a relative newbie.

Swift

---

### Post by oh6jih on 2008-03-04
Anyone having success with E90 and Ubuntu 7.10? Tried pritty much all the configs i could find but no success.

```

koivuporras@liisa:~$ msynctool --sync nokiacon
Synchronizing group "nokiacon" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
received event dsession
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

And phone says "System Error" after connection attempt

---

### Post by lospo on 2008-03-06
Hi, i try to sinc my N80 phone with multisync-qad in ubuntu 7.10 feisty but the best result is to write on the phone "System Error".
Anyone can hep me with this?

My syncml-obex-client config:

[PHP]
<config>
<bluetooth_address>XX:XX:D2:2C:XX:XX</bluetooth_address>
<bluetooth_channel>13</bluetooth_channel>
<interface>0</interface>
<identifier>PC Suite</identifier>
<version>1</version>
<wbxml>1</wbxml>
<username></username>
<password></password>
<type>2</type>
<usestringtable>0</usestringtable>
<onlyreplace>0</onlyreplace>
<recvLimit>10000</recvLimit>
<maxObjSize>0</maxObjSize>
<contact_db>Contacts</contact_db>
<calendar_db></calendar_db>
<note_db></note_db>
</config>
[/PHP]

Thanks to anyone!

---

### Post by lospo on 2008-03-07
Update!
I changed this
[PHP]
<contact_db>Contacts</contact_db>
[/PHP]
to this
[PHP]
<contact_db>addressbook</contact_db>
[/PHP]

And now everything seems to be ok, the phone write sync complete but looking the addressbook it is empty.
Where i'm wronG!?!?!?!?

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

### Post by heggenhe on 2008-03-16
Hi Guys,

so far so good. I try also to sync my nokia (3109 classic) with evolution. I am using ubuntu 7.10. Everything looks working good, But when I start the sync I got the following message

```
Synchronizing group "evolution-n3109c" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-47D6DF9500000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47DCFF4F00000001 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47CC43DB00000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47D9612300000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47DA942700000000 with data of size 4 from member 1. Changetype ADDED
Received an entry pas-id-47DCEA9700000000 with data of size 4 from member 1. Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client had an error while getting changes: Request not successfull: 68
Member 1 of type evo2-sync just disconnected
```

Request not successfull: 68 ??? Has anyone an idea how to fix that problem.

Thanks a lot.
Heiko

---

### Post by Bjerrum on 2008-03-20
I got my N73 synced with evolution. Unfortunately I really don't know what i did, but to things that I did and maybe can be helpful for someone.

[LIST=1]
[*]Installed GNOME Bluetooth tool and moved files from phone and back again
[*]No checks in "Disable syncing of objtype" in the graphical application multisync0.90
[/LIST]

---

### Post by dravidan on 2008-03-24
I am at the same place.  Did you figure out what was wrong?

---

### Post by kiddyfurby on 2008-03-31
hi guys i have my n73 syncing contacts
here's a few tips:
opensync 0.22 works, 0.19 in the repos might not
make sure you remove .opensync in your home folder if you've used 0.19 before
the amd64 deb sammys provided works, even in hardy
if the sync is not working... try to separate calendar and contacts into two sync profile

---

### Post by audiomick on 2008-04-16
Hallo.
I seem to have won the battle, and wanted to share the results.

I am using an E61 from the German provider T Mobil, but with the language set to english. The computer is a (2 months old)  desktop with 64 bit  Ubuntu Studio (Gutsy) installed. I have synced the phone via USB Cable, not bluetooth, to Evolution.

 I also had the problem that others here have described, that the phone tried to sync then showed a system error. After reading this thread all the way through ( RTFM ... ) it dawned on me to add the suggested repositories. Funny how things work when you do them right...

I only got this going yesterday, so I can't say much about reliability or stability but:

Contacts syncronise, without doubling up. Changes in the computer go to the phone and vice versa.

Calender syncronises, changes work in both directions, but things that I had in the phone as memos are now meetings. I had gone back and forwards a couple of times before I noticed this. I made an attempt to sync notes which went bad, and at the next attempt ( no notes ) had conflicts ( double entries ). I selected "newest" for each of them, and assume that Evolution took the memos on board as meetings, then wrote them back to the phone as such.

Notes didn't work. As this is not that important for me, I haven't and wont pursue it further.

2 more observations:
The USB plug on the phone is REALLY DODGY. If you're having trouble, check first to see if the phone is really connected. When it has a connection, it shows a little USB symbol under the battery level display, where the lock symbol appears when the phone is locked. Mine loses the connection nearly every time if I move the phone whilst it is polugged in.

I noticed this morning that Evolution isn't going off to get mail. Haven't investigated yet, can't imagine how the sync process could affect this, and my e-mail provider doesn't have that good a track record, but you never know.

Update :Evolution was switched to "work offline". I have no recollection of having switched it mayself, nor any reason for having done so. However, after getting the phone going, I spent the rest of the day messing around getting an online banking connection working. Who knows what happened...

Finally, thanks very much to everyone who has contributed to this thread, in particular Nailor for starting it and Sammys for the 64 bit repo.

Look after yourselves
Michael

---

### Post by xdevnull on 2008-04-16
So - hardy is coming out next week...think there will be any changes?  I wonder if the old punktard repositories will still be there?  Should one still use the feisty repository?  Does hardy have updated libraries etc, that leaves the other site behind?

---

### Post by mathew.chacko on 2008-04-17
> **chrismine said:**
> I got sync to work with my Nokia 6234 with the default repositories and file versions in Gutsy.

I can sync my contacts, Calendars but not my notes. I had to edit the syncml-obex-client configuration file to look like this:   <calendar_db>Calendar</calendar_db>


I too have Nokia 6234. I am trying to sync on Hardy Beta. No success so far. Could you please show your config files. 

Thanks in advance.

---

### Post by audiomick on 2008-04-23
Hallo
After having made such a positive post recently, I thought I'd better spread the bad news as well:

After having the phone (E61) sync happily via USB and apparently all in order, I went on to clean up and consolidate my addresses; things like putting the same person's phone no. and e-mail into the same entry. When I tried to sync it up, it didn't work. 
I did some more cleaning up, including going through in Evolution and putting all the entries in the spots where Evolution wants to have them when you open a new contact. Then I saved the address book in the phone to the card, backed up evolution, disabled the calender sync, then (took a deep deep breath and) deleted all of the addresses in the phone. This resulted in an almost perfect sync.
I went through the phone and compared it to Evolution to figure out what didn't go across. There were only a couple of entries, and rewriting their names in Evolution cleaned it all up so it would sync.
So far so good.
Then I turned on the calender again, expecting it to work as it was unchanged since the original clean sync, but it didn't. Haven't got that sorted yet, because after spending all afternoon trying to sync back and forwards the computer decided it didn't want to boot up.
I really don't know if this is related to the attempts to sync up, but it did follow immediately after that. I've since done a complete re-install, and the box seems to be happy again. I'm going to add things bit by bit, and pull the appropriate configs across from the HOME folder from the previous installation, which I was able to recover with the Ubuntu live CD.
Gotta love that....
Hope to have some more info soon
Michael

PS Rewriting the names in Evolution was inspired by the fact that the entries went across to the phone without the first name.
also; Nicknames don't transfer. Evolution lists them as <nickname>, the phone as <SECONDNAME> or something like that. At any rate, there's no mutual entry for them.

NEW INFO 30 Aug. 2008

Firstly, it turned out to be a bad BIOS on the computer. After it had gotten sulky another 4 times or so I took it back to the shop, where they updated/ re-installed the BIOS. Since then, things are fine.

Secondly, the phone is synchronizing (touch wood ) quite well. As I mentioned in my first post on this thread, I am using USB, not bluetooth, however the behavior of the sync process as such should be the same either way. I am syncing Calender and Contacts. Notes doesn't work, and I still don't intend to pursue that.

As far as getting that first clean sync goes, a tip: After the first attempt, you are likely to be asked which of two entries ( one in the phone, one in the computer) you wish to use. If there are a lot of entries involved, click the button that tells multi-sync to treat all entries the same. Until I did that, I had many failed sync attempts in one sitting. Having done that I got a clean sync immediately. I think clicking through the entries one by one takes too long for multi-sync.

Another tip: When you get things running, observe carefully the way it all behaves. For instance, I lost an entry through a wrong assumption. I had to update a phone number, and thought I could delete the relevant entry from the phone and overwrite it from the computer. What got transferred was not the new number, but rather the deletion. oops...

Anyway, good luck to all who are still trying.
Michael

---

### Post by abh83 on 2008-05-01
Sorry I can't help u there Audiomick. But I want to thank Nailor for this great HowTo! It works flawlessly on Hardy.

---

### Post by Curly Brace on 2008-05-05
Many thanks, all worked for me, exactly in way you wrote it, Otto.

I'm running Ubuntu 8.04 and Nokia 6120 Classic. I've got an errors appearing until I removed the Notes and Calendar from the XML settings.

Thanks again!

---

### Post by sukka69 on 2008-05-07
Hi Curly Brace,

I am having the same phone and Ubuntu 8.04 as you, can you share with me steps that you did to get it sync? I am newbies, appreciate you can share some clear guide to get it done. what do you means *"I've got an errors appearing until I removed the Notes and Calendar from the XML settings."* ? How to remove that?

I tried exactly the same step as post #1, but stuck at the following screen, it just hang there till timeout:

> 
root@sseng-laptop:/home/sseng# msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync had an error while connecting: Unable to open anything
received event dsession
received contact dsession
received note dsession
root@sseng-laptop:/home/sseng# ient just connected
root@sseng-laptop:/home/sseng# msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync had an error while connecting: Unable to open anything
received event dsession
received contact dsession
received note dsession
Member 2 of type syncml-obex-client just connected

Many thanks for help.

---

### Post by sukka69 on 2008-05-07
Hi,

I did it! I just clear every setting, removal opensync and mutisync. Reinstall and do the setting from fresh according to post #161. It sync ok now. Many thanks to otto67.:KS

---

### Post by uhappo on 2008-05-13
> **Jingo said:**
> I now got it working on my Nokia E51. With libsyncml version 0.4.4.

Some hint on the mailinglist said installing MMSsync via Nokia Pc Suite on windows did some magic! I installed it by accident, don't know if it changed anything. Anyway now it works for me.

On the phone:
[LIST=1]
[*]Create a Sync profile, named "Evolution"
[*]SyncML version 1.1
[*]Connect using bluetooth
[*]I disabled every "program" except "Calendar"
[*]Calendar database "Calendar"
[*]Sync in both directions
[/LIST]

On the PC:
Repo
```
deb http://opensync.gforge.punktart.de/repo/opensync-0.21 fiesty main
```
```
sudo aptitude install opensync libsyncml-utils
```

Try:
```
syncml-obex-client -b $MAC $CHANNEL --slow-sync text/x-vcalendar Calendar --wbxml --identifier "Evolution"
```
Where $MAC = Bluetooth adress, and $CHANNEL = 10

Should give a dump of your phones calendar.

Config - only changes channel to 10:
```
<?xml version="1.0"?>
<config>
	<bluetooth_address>BT MAC</bluetooth_address>
	<bluetooth_channel>10</bluetooth_channel> 
	<identifier>Evolution</identifier>
  
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

  <onlyLocaltime>0</onlyLocaltime>
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

Group consists of evo2-sync and syncml-obex-client.

This helped me, I'm on Hardy with Nokia N73.

Sync is now clean. Wuhuu!!

---

### Post by uhappo on 2008-05-16
It's crucial to use the basic "PC Suite"-identifier/class, both in config and in your N73.

Then
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

Plus:
- syncml obex client
- evo2-sync
- multisync0.90
- opensync 0.22

[img]http://stashbox.org/200617/Sync%20profile.jpg[/img]

And you should be golden. I've synced in both directions 100% clean with this configuration.

Ok, time to sync away!

---

### Post by hfdragon on 2008-05-16
> **uhappo said:**
> 
  <contact_db>Contacts</contact_db>
  <calendar_db>Calendar</calendar_db>
  <note_db>Notes</note_db>


You can sync Contacts, Calendat AND Notes ?

I've not tried for quite a long time, but I'v always only manage to sync only Contacts and Calendar...

---

### Post by uhappo on 2008-05-16
> **hfdragon said:**
> You can sync Contacts, Calendat AND Notes ?

I've not tried for quite a long time, but I'v always only manage to sync only Contacts and Calendar...

Haven't tried Notes, and maybe I won't, if it messes my working sync. My point was: I tried various confs and followed many posts, but my long lasting working sync profile is above

---

### Post by zuzuzzzip on 2008-06-07
uhappo: I tried your configs for your N73 on my N80 but it didn't work...

You didn't say what server address to specify on the phone though, I tried using my PC's BT MAC address but with no success...

terminal output:
```
$ syncml-obex-client -b $MAC $CHANNEL --slow-sync text/x-vcalendar Calendar --wbxml --identifier "Evolution"
connection with device succeeded
Received an transport error: Request not successfull: 67
```hmm.. Changing the Server to connect to in the phone settings to "Evolution" gave me:
```
$ syncml-obex-client -b 00:12:D1:A6:EE:8D 10 --slow-sync text/x-vcalendar Calendar --wbxml --identifier "Evolution"
connection with device succeeded
Received an Alert for the DS Server at Calendar: Type: 201, Last , Next 20080607T140226Z
Slowsyncing
Just received a new session with ID 1
Received the DevInf
Session 1 reported final. flushing
Received an reply to our Alert
Session 1 reported final. flushing
Session 1 has ended

```
and a "System Error!" on the phone :)

---

### Post by uhappo on 2008-06-23
Hmmm, let's see:

On phone, check your Sync-preferences, and it should be checked from PC Suite-type, not from e.g. Lifeblog.

It should use server-version 1.1

Transfer type bluetooth

Server address PC Suite

User name none

Password none (I guess)


I use my MAC-address (just in case) with small letters, eg 00:f5...

And again, don't use Evolution-named profiles or others, keep everything PC Suite-named, use that (my) config and you should be able to sync properly. Unless, N80 isn't able to do it, but you never know.



> **zuzuzzzip said:**
> uhappo: I tried your configs for your N73 on my N80 but it didn't work...

You didn't say what server address to specify on the phone though, I tried using my PC's BT MAC address but with no success...

terminal output:
```
$ syncml-obex-client -b $MAC $CHANNEL --slow-sync text/x-vcalendar Calendar --wbxml --identifier "Evolution"
connection with device succeeded
Received an transport error: Request not successfull: 67
```hmm.. Changing the Server to connect to in the phone settings to "Evolution" gave me:
```
$ syncml-obex-client -b 00:12:D1:A6:EE:8D 10 --slow-sync text/x-vcalendar Calendar --wbxml --identifier "Evolution"
connection with device succeeded
Received an Alert for the DS Server at Calendar: Type: 201, Last , Next 20080607T140226Z
Slowsyncing
Just received a new session with ID 1
Received the DevInf
Session 1 reported final. flushing
Received an reply to our Alert
Session 1 reported final. flushing
Session 1 has ended

```
and a "System Error!" on the phone :)

---

### Post by bob1989898 on 2008-07-13
I have Ubuntu 8.04.1 installed on my Asus Laptop and have set up a working Bluetooth Connection between the Computer and my Nokia 6300.
This weekend I wanted to sync my Evolution Contacts and my Calendar to my mobile and vice versa via Bluetooth. I used the following HOWTO:

[http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17)

I used the graphical Method. I only changed the Bluetooth Channel to 11, as it was written in several other Forums.

My Config for the syncml-obex client under Multisync 0.90 is like this (I just deleted the MAC-Adress for this Post):

<config>
<bluetooth_address></bluetooth_address>
<bluetooth_channel>11</bluetooth_channel>
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
<note_db>Notes</note_db>
</config>

But as soon as I try to sync my phone with Evolution via Terminal, I get the following log:

Synchronizing group "Nokia"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
received event dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client had an error while getting changes: Request not successfull: 64
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error synchronizing: Unable to read from one of the members
Pipe closed! Exiting.
bob@bob-laptop:~$ Pipe closed! Exiting.

Does anyone knows a Solution or has a similar problem?

---

### Post by madmtbbibi on 2008-07-18
Yes I have the same problem.
Nokia 6500c.
same log as above, but error 68, not 64!
Do you think opensync 0.36 would help?

Simon

---

### Post by Gromba on 2008-07-22
Maybe this page is helpfull:
[http://www.opensync.org/wiki/syncml-guide#KnownConfigurations](http://www.opensync.org/wiki/syncml-guide#KnownConfigurations)

---

### Post by jeppo on 2008-07-28
Hey guys,

Great guide, extremely helpful.

(Apart from not being able to sync notes) I only have one issue.  How can in sync in one direction only?  Is it possible at all?  I just want to be able to copy my new contacts from my phone over to Evolution without it sending back the old ones.

Thanks,
Chris

---

### Post by apalacheno on 2008-07-29
Hi Chris,
this is not possible with the 0.22 versions, but it has been introduced somewhere in the 0.3x series, which are still very unstable and shouldn't be used in production environment. According to the opensync devs, 0.40 will be the first stable version since the 0.22 version.

However, I have the impression, that the project is stuck a bit. The last unstable release (0.36) is about half a year old.

Cheers,
Robert

---

### Post by jeppo on 2008-07-29
Ah that's a shame.  So do you reakon that feature will be included in 0.4?

Just quickly, any ideas on how to get notes syncing properly with evolution?  As soon as I enable syncing of notes the sync hangs.

Anyway Robert thanks for clearing that up.

Chris

---

### Post by apalacheno on 2008-07-29
It will be in 0.40, but as I said, I don't have any idea when it will be released. According to [http://www.opensync.org/wiki/TODO]("http://www.opensync.org/wiki/TODO") most TODOs are already finished, but progress seems to be slow lately.

---

### Post by MickSulley on 2008-08-08
I cannot get this to work properly.  It connects and looks like it is working but it only transfers diary entries from the phone to the pc, and no contacts either way.

Any ideas?

Thanks
Mick

---

### Post by niceguy123 on 2008-08-10
Glad to find this thread, Can someone help me with my new E71 ? I'd like to be able to sync to this computer Ubuntu 8.04 and manage pictures taken with it's camera.

thanks.

---

### Post by niceguy123 on 2008-08-10
Glad to find this thread, Can someone help me with my new E71 ? I'd like to be able to sync to this computer Ubuntu 8.04 and manage pictures taken with it's camera.

thanks.

---

### Post by midgemiles on 2008-08-27
I have been able to sync my Nokia N95 8GB for contacts and calendar with evolution on Hardy Heron, thanks to this guide.  I am getting some "unclean" syncs so am in troubleshooting mode, but generally it is working adequately.
Is there any way to limit the calendar entries synced to phone to no more than (say) four weeks old?  I don't want to delete old entries on the computer evolution calendar, but I dont want all the old entries on the phone.

---

### Post by audiomick on 2008-08-30
> **MickSulley said:**
> I cannot get this to work properly.  It connects and looks like it is working but it only transfers diary entries from the phone to the pc, and no contacts either way.

Any ideas?

Thanks
Mick

Look at this bit of your config

 <contact_db>Contacts</contact_db>
        <calendar_db></calendar_db>

As shown here, only contacts will sync, not Calender.

 <contact_db></contact_db>
 <calendar_db>Calendar</calendar_db>

In this instance only Calendar, no contacts.

For both, it needs to look like this:

 <contact_db>Contacts</contact_db>
 <calendar_db>Calendar</calendar_db>

taking care that the words "Contacts" and "Calendar" are written exactly as the appear in the sync Profile in the phone.

If it isn't that, I don't know what it is, sorry

michael

---

### Post by MickSulley on 2008-09-13
Hi,
I can now sync contacts thanks to the info in these posts.  However calendar entries sync from the phone to the PC but not the other way.  Any ideas?
Thanks
Mick

---

### Post by audiomick on 2008-09-22
> **MickSulley said:**
> Hi,
I can now sync contacts thanks to the info in these posts.  However [SIZE="4"][COLOR="Blue"]calendar entries sync from the phone to the PC but not the other way[/COLOR][/SIZE].  Any ideas?
Thanks
Mick

Hi Mick.
How are you entering your calender entries? Evolution offers (I'm guessing a bit because I live in Germany and have a german language Evolution ) appointments, all day events, meetings and things to do, much the same as the phone.
My phone is an E61, I'm transferring via usb, but the mechanics are the same as for bluetooth, and I'm using the Evolution 2.22.3.1 that comes with Ubuntu 8.04.

I had meetings and memos in the phone when I first tried to sync, and found that they all landed as the one type of entry in Evolution, and that only that type of entry got back to the phone.

Try making a set of dummy entries in Evolution, one of each type, and see what gets across. I now only use the one type for everything. It's a bit of a waste of the theoretically possible flexibility of the phone and Evolution, but it seems to work quite reliably. I work as a freelancer, so my calender is really important, and I haven't had a problem yet with things getting lost.

good luck,
Michael

---

### Post by MickSulley on 2008-09-22
Thanks for the reply.  Just tried it all again and it seems to work fine.  I can only assume that rebooting both PC and phone has fixed it all, I thought I had tried that before, obviously not.

Thanks

Mick

---

### Post by dgrafix on 2008-09-24
Im not too fussy about syncing my mail stuff. I am interested in file access though if anyone has any ideas.

I have 2 phones, ones a nokia 6210c and a samsung thing.

Both phones connect via bluetooth, are browsable and i can download files from them. However, when i try to send music or other files to the device i get the error:

"operation not supported by backend"

Any ideas what the problem is here? Not being able to load files to it is a pain in my 'backend' :)

---

### Post by MickSulley on 2008-09-24
I managed to get a ring tone to my phone, used Blutooth manager, send file.  It came over to my phone as a text message which I could then save.

I worked for what I wanted but I guess it would be tedious to send albums that way.

Cheers
Mick

---

### Post by PhoenixAndy on 2008-10-07
I've just got a shiny new e71 to replace my tired HTC Wizard, and I can't manage to get it to sync using usb. Bluetooth isn't an option as I don't have a bluetooth dongle on the pc.

If I set up the relevant settings as root, it'll at least connect, but the phone seems to hang with a "Connecting" message.

However if I try it as my standard user, I get the following:

```
Synchronizing group "PC Suite" 
The previous synchronization was unclean. Slow-syncing
Member 2 of type evo2-sync just connected
Member 1 of type syncml-obex-client had an error while connecting: Unable to connect to the interface
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error synchronizing: Unable to connect one of the members
Pipe closed! Exiting.
Pipe closed! Exiting.

```

That **seems** to indicate that the problem is that the normal user can't access the usb system properly. I'm willing to accept that the root connection hasn't hung and is actually doing something due to the fact that the first sync can take a while. I'll see what state my phone is in when I get up in the morning.

Of course, having to run the sync as root is far from optimal, so I'm looking for a solution. I've found the suggestions about changing udev rules, but they haven't worked.

**UPDATE:** So this morning I check how things have progressed. My phone is displaying an "Operation Timed Out" error. The PC hasn't noticed that the phone has given up. So clearly I get further while syncing as root, but still no joy.

---

### Post by audiomick on 2008-10-14
Hallo PhoenixAndy.
That all looks horribly familiar...
I've had my E61 going for a couple of months now via USB (Ubuntu 8.04), so heads up, it can work. It's all a bit dim now after a few months, but what you describe sounds like the business with the udev permissions still isn't right.
If you read German, look here:

[http://blog.netandif.de/2008/02/22/sync-von-nokia-e61-und-evolution-per-usb-unter-linux/]("http://blog.netandif.de/2008/02/22/sync-von-nokia-e61-und-evolution-per-usb-unter-linux/")

that's the description that I followed to get mine going.

In short: if you do this

```
syncml-obex-client -u
```

and get this:

> *Superuser privileges are required to access complete USB information.*


then it's not right yet.

so:

for Ubuntu 8.04, at least,

plug the phone in and

```
lsusb
```

should get something like this:

[FONT="Courier New"]Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 046d:c046 Logitech, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c317 Logitech, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0421:044d Nokia Mobile Phones 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
mick@mick-desktop:~$ [/FONT]

this is what we want:

[FONT="Courier New"]Bus 003 Device 004: ID 0421:044d Nokia Mobile Phones [/FONT]

then:

```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```

and add an entry like this:
```

#to allow access to usb for syncing the phone
BUS=="usb",SYSFS{idVendor}=="0421",SYSFS{idProduct}=="044d",GROUP="plugdev",USER="mick"
```

 whereby your user name probably isn't "mick" :-)

Something else just occurs to me:

In the config for the snycml-obex-client

that looks something like this:

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
        <usestringtable>1</usestringtable>
        <onlyreplace>0</onlyreplace>
        <!-- This needs to be set to 10 000, otherwise you'll be sending more data than your phone can handle. -->
        <recvLimit>10000</recvLimit>
        <maxObjSize>0</maxObjSize>
        <contact_db>Contacts</contact_db>
        <calendar_db></calendar_db>
        <note_db></note_db>
</config>

```
(see post #1 on this thread)

needs to be set to type 5 for USB

```
 <type>5</type>
```

It must be already right if you are having success as root. Did I understand that right i your post, or is there also still a problem as root?


have another go at it,
good luck
Michael

---

### Post by PhoenixAndy on 2008-10-14
ok, so this is what I added to /etc/udev/rules.d/40-permissions.rules:

```
#to allow access to usb for syncing the phone
BUS=="usb",SYSFS{idVendor}=="0421",SYSFS{idProduct}=="00ab",GROUP="plugdev",USER="astanford"
```

based on:
```
astanford@osiris:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0421:00ab Nokia Mobile Phones 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 001: ID 0000:0000  

```

After which I still get "Superuser privileges are required to access complete USB information."

This seems to imply that my changes aren't being adhered to.

Also, it appears I didn't have a plugdev group, as I began to suspect that it could be something as simple as my user account not being a member of the group, and discovered that the group didn't even exist. I attempted to create the group, in an effort to solve that problem, but still no success.

---

### Post by kylea on 2008-10-19
Trick with 6110 and 6233 - Delete ALL entries on the phones and then hey presto it starts working.

Only remaining issue - Lighting does not automatically show updates from the Phone - needed to shutdown and re-start - there may be a setting - anyone know.

---

### Post by audiomick on 2008-10-23
> **PhoenixAndy said:**
> ok, so this is what I added to /etc/udev/rules.d/40-permissions.rules:

```
#to allow access to usb for syncing the phone
BUS=="usb",SYSFS{idVendor}=="0421",SYSFS{idProduct}=="00ab",GROUP="plugdev",USER="astanford"
```

based on:
```
astanford@osiris:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0421:00ab Nokia Mobile Phones 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 001: ID 0000:0000  

```

After which I still get "Superuser privileges are required to access complete USB information."

This seems to imply that my changes aren't being adhered to.

Also, it appears I didn't have a plugdev group, as I began to suspect that it could be something as simple as my user account not being a member of the group, and discovered that the group didn't even exist. I attempted to create the group, in an effort to solve that problem, but still no success.

That all looks right.
Which Linux are you using? Mine is Ubuntu 8.04. If it is a different one, maybe plugdev isn't the right group. That's starting to get out of range of my knowledge...
Also, you may have seen a post from me earlier in the thread about the USB plug on the phone. In the last few days I've had a couple of unsuccessful syncs, and just realised that it is because the phone is losing the connection as I put it down after switching to "PC Suite" mode.
I doubt that this has anything to do with your problems, but it is something to watch.
I'l keep thinking about it anyway. Maybe something will occur to me.
Michael

---

### Post by audiomick on 2008-10-26
Hallo.
I made a "tactical error" a few days ago, and would like to let people know about it.
I had mentioned in a post a week or so ago that I had had a couple of bad syncs. The result was that all my calender entries were in triplicate in the phone. I thought that the quickest way to clean up would be to erase the calender entries in the phone and do a new sync to get them back from the computer. This was a **BIG MISTAKE![B]**[/B]

The sync process remembers the the last changes, which is obvious when you think about it. The result was not the hoped for transfer from the full calender in the computer, but rather the erasure of all the entries in the computer as well. And of course I hadn't backed up Evolution before starting either... :mad::confused::(
As a free-lancer, it's not so good to suddenly lose all your appointments.

I think I've got it all back, and hope that the episode will have been the timely warning about the importance of backups that we all need from time to time.
Michael

---

### Post by AbdulRahiem on 2008-10-29
> **MickSulley said:**
> Hi,
I can now sync contacts thanks to the info in these posts.  However calendar entries sync from the phone to the PC but not the other way.  Any ideas?
Thanks
Mick

My phone is a Nokia E70. I had exactly the same problem. I solved it by creating an additional profile on my phone, called *Evolution*. I had noticed that the built-in *PC Suite* profile was read-only and I could not edit the direction settings.

The name given to the Server ID in the profile should be identical to the name for the group in the Multisync dialog.

In the new profile I initially set the direction to 'To Phone only'. I deleted all contacts and calendar entries from the phone. After initial synchronisation the contacts and calendar entries were reloaded and everything was in order. I then changed the direction settings to 'normal', i.e. two ways, and everything is now working well, in both directions!

AbdulRahiem

---

### Post by audiomick on 2008-10-31
> ... by creating an additional profile on my phone, called *Evolution*. I had noticed that the built-in *PC Suite* profile was read-only and I could not edit the direction settings.

In the new profile I initially set the direction to 'To Phone only'. I deleted all contacts and calendar entries from the phone....

AbdulRahiem

Hi Abdul.
I think your post was the one I needed before trying what I described in my last post, the one previous to yours.
Better late than never! Thanks for the tip
Michael

---

### Post by pianon on 2008-11-06
> **Jingo said:**
> I now got it working on my Nokia E51. With libsyncml version 0.4.4.

Some hint on the mailinglist said installing MMSsync via Nokia Pc Suite on windows did some magic! I installed it by accident, don't know if it changed anything. Anyway now it works for me.



Does everything work? I mean, calendar, contacts, notes... Only slow-syncing or also normal syncing?

---

### Post by Luk_Deisler on 2008-11-06
Hi there, I want to sync(contacts, calendar) my N82 with kubuntu 8.10. Is it possible?

---

### Post by AbdulRahiem on 2008-11-06
> **Luk_Deisler said:**
> Hi there, I want to sync(contacts, calendar) my N82 with kubuntu 8.10. Is it possible?
If it (your N82 that is) supports SyncML, then you can do it. Go to the *Connectivity* tab on the menu. If you find "Sync" there, then you can do it. You will have to create a profile for it. Read this thread and you will find all the information that you need.

---

### Post by gertvdijk on 2008-12-02
I have quite a few serious sync errors for my Nokia E50 device:
[LIST]
[*]Landline numbers are skipped
[*]Work telephone numbers are skipped
[/LIST]
This is happening since gutsy, hardy and still in intrepid... Do more people have these problems? Because it isn't useable without proper syncing. Now I have half of my 280+ contact without a phone number in Evolution, big part with missing phone numbers and god knows what more isn't synced...

---

### Post by Mad_Dud on 2008-12-25
Guys, I think, this thread needs to have serious summarize, because collecting data from over 20 pages is quite hard.

**audiomick** tried to do it 2 pages ago, but maybe we could manage to write serious howto and put it on first post in this thread.

Anyway good job guys!

---

### Post by fsando on 2008-12-25
EDIT: Delete.

---

### Post by max11 on 2009-02-14
I dont have bluetooth device on my laptop ... I only need USB connection (sync)  What do i do on these lines:
```
 <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address></bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel></bluetooth_channel>
  
``` 
???

---

### Post by AbdulRahiem on 2009-02-14
Just leave those lines as they are. They don't interfere.

---

### Post by Tiny_D on 2009-02-16
Hi,

I try to sync my e61i on my Kubuntu 8.4 and 8.10.

I was half successful on 8.4, the calendar entries were pushed to phone, but it stopped with the prior named "System Error". 

I had created a new Sync profile on the phone, only for the calendar. But it doesn't help.

every time I start the syncing a copy of the calendar entries will be created. Maybe the reason for that is the "System Error".

I have read a couple of post here in that threat, but I didnd't got a solution. 
Is there a newer version of the syncml and opensync stuff?

This is msynctool version "0.22"
using OpenSync version "0.22"

s there a solution anywere at the moment for that issue?

```

<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>00:17:E5:EF:59:B5</bluetooth_address>

  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>14</bluetooth_channel>

  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw devic$
  <interface>0</interface>

  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>Sunbird</identifier>

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
  <recvLimit>10000</recvLimit>

  <maxObjSize>1</maxObjSize>

  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <!-- <contact_db>Contacts</contact_db> -->

  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>

  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db></note_db>
</config>

```

The Version of the Phone is

1.0633.22.05

Have anyone made some experiences with a newer firmware?

I had made a couple of test and switched bbetween channel 14 and 10. 

On 8.10 I only use USB couse of some BT issues in the Kubuntu fork.

---

### Post by Tiny_D on 2009-02-17
Hm, error persist. On 8.04 via BT and 8.10 via USB. I upgrade the e61i to 2.0633.65.01 but error also persist.

What is the difference to the working ones?

---

### Post by packoman on 2009-03-02
Hi.
I hope someone here can help me or at least comment:
I am trying to sync a Nokia 6230i to evolution using opensync with the syncml-obex-client and the msynctool. Till now unfortunately only with partial success. The following is happening:
When I tried to sync for the first time(s), the sync started (showing a contacts being synced), but then the mobile stalled and I got an error at the console (don't remember which one).
Now I tried again and it works, however only two of my contacts are actually synced, whereas the rest (138 in total) are being ignored completely.
I tried resetting everything (i.e.: getting evolution back to the state after a fresh install - which I had done before starting), because I suspect, that the first failed/partial(?) sync attempts are still saved somewhere and cause this odd behavior.
However deleting .evolution and the .opensync-0.22 directories in my user-home-directory does not help - Evolution keeps even the contacts and everything. :confused:
So my question is, whether you guys know how to reset Evolution completely (i.e. which directories I need to delete for this) and also for opensync? Or if you have any other suggestions what could be done?
Appart from the above behavior, interestingly the syncing works fine for those two contacts and new contacts that I add inside Evolution or the Nokia 6230i. 
Hope someone can help me, because after almost a year of trying, I feel, I'm so close to finally reaching my goal of syncing my mobile to my PC.
Thanks,
Michael

---

### Post by pixelmuerto on 2009-03-10
> **bob1989898 said:**
> 
Synchronizing group "Nokia"
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
received event dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client had an error while getting changes: Request not successfull: 64
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error synchronizing: Unable to read from one of the members
Pipe closed! Exiting.
bob@bob-laptop:~$ Pipe closed! Exiting.

Does anyone knows a Solution or has a similar problem?
 
I have same problem, You have found the solution?
thanks.

---

### Post by pawebst on 2009-04-24
For those interested, I have a nokia e71 syncing contacts and calendar( recurring events not syncing but hey.) on intrepid 8.10 after following the above How-Tos (Thanks everyone for their efforts). Following little nuiances though - Had problems with sdptool browse command  - often came back with Failed to connect to SDP server on xx:xx:xx:xx:xx:xx: Connection timed out. To get a response you must be already paired which I initiated from the phone. 
Digress -- select paired devices -new paired devices
Select desktop to pair with
Enter pin on first mobile then desktop
 I have BlueProximity 1.2.5 running which shows an icon if devices are paired. Gui didn't help with pairing or channel no. however but Bluetooth applet 1.8 was somewhat useful
(PC suite channel turned out to be 10 as already suggested)--

However to keep the sync I had to answer no to phones question: Authorise device to make connections automatically?
If I answered yes connection was immediately lost.

Not a very technical help I know but thought someone might be grateful.

---

### Post by ajmctaggart on 2009-05-21
Thanks!

I am in the process of trying to sync an E71 and N95 and Evolution...Process is a pain...

I am documenting my progress [here]("http://ubuntuforums.org/showthread.php?t=1160470")

Hope we can perfect this art...it's not easy to get the perfect solution...

---

### Post by fluffman86 on 2009-06-11
> **ajmctaggart said:**
> Thanks!

I am in the process of trying to sync an E71 and N95 and Evolution...Process is a pain...

I am documenting my progress [here]("http://ubuntuforums.org/showthread.php?t=1160470")

Hope we can perfect this art...it's not easy to get the perfect solution...

[http://lumumba.uhasselt.be/frederickgaens/SyncE71Linux.html](http://lumumba.uhasselt.be/frederickgaens/SyncE71Linux.html)

^ that worked perfectly for me on a fresh 9.04 install with my Nokia e71x.  I kinda switched up the directions for USB, though.  Basically, where you config group member 2, use:
> 
<config>
	<interface>0</interface>
	<identifier>PC Suite</identifier>
	<version>1</version>
	<wbxml>1</wbxml>
	<username></username>
	<password></password>
	<type>5</type>
	<usestringtable>1</usestringtable>
	<onlyreplace>0</onlyreplace>
	<recvLimit>0</recvLimit>
	<maxObjSize>0</maxObjSize>
	<contact_db>Contacts</contact_db>
	<calendar_db>Calendar</calendar_db>
	<note_db></note_db>
</config>


...and ignore the stuff at the top about bluetooth scanning and stuff.

---

### Post by ssawin on 2009-06-17
I followed these instructions with Easy Peasy on an Eee 1000 netbook, connecting to a Nokia E62.  Everything went flawlessly, and it began synchronizing, displaying hundreds of lines of the form 
         Received an entry 307 with data of size 4 from member 2 (syncml-obex-client). Changetype ADDED
(and the same for member 1 so it is going both ways, then it says
       Member 2 of type syncml-obex-client just sent all changes
        All clients sent changes or error

and then hangs up

when I run it again it says
     The previous synchronization was unclean. Slow-syncing
 The previous synchronization was unclean. Slow-syncing


Any suggestions what I can do to get it working?

thanks for any help

---

### Post by audiomick on 2009-07-01
Hallo ssawin,
probably not much help but:
I had to hammer away at mine for a while (E61, Ubuntu initally 8.04, then 8.10, 9.04)
I had quite a run of various error messages and "previous unclean, slow syncing", but eventually it worked, without any real changes.

I did go through the contacts in Evolution an try to make the entries there consistent with what the phone wants (compare an entry that has come from the phone with one you have made in Evo yourself, and adjust to match)

What definitely helped was: During the slow sync, the computer asked which version of a number of entries to take ( phone, Evolution ). If I tried going through one by one, something timed out and the sync crashed. When I set the checkmark to remember the choice, it all went through. This was the thing that achieved a running system state for me.

keep at it!
Michael

---

### Post by randrade on 2009-08-22
ssawin,
I'm synchronizing my E63 with evolution using syncml-http-server plugin. Instead of using a bluetooth or USB connection, I do the sync using an internet connection.
I must say I had some problems with msynctool regarding hanging or freezing. What I did to solve it? Well, I think I just needed to configure the syncml-http-server plugin without authentication and with and empty notedb.
After that I just set my phone to sync using SyncML v. 1.1, removed the username and password data from the sync phone profile and activated the sync only for contacts and calendar.
After doing these changes, everything worked fine.
Using msynctool isn't the perfect solution, it's buggy and connection may time-out sometimes, but it can do the job with a little bit of patience and hard work.


   Cheers,


         Ricardo

---

### Post by Dead1nside on 2009-09-01
I'm a Fedora user but we're all trying to achieve the same thing aren't we.

I have one question about opensync to an s60 phone, specifically the calendar. Is the syncing process destructive in that Sunbird has other fields like 'Categories' when an entry is synced to s60 calendar is this field destroyed or is it just unused?

Thank-you in advance for your advice on this matter.

---

### Post by audiomick on 2009-09-22
> **Dead1nside said:**
> I'm a Fedora user but we're all trying to achieve the same thing aren't we.

I have one question about opensync to an s60 phone, specifically the calendar. Is the syncing process destructive in that Sunbird has other fields like 'Categories' when an entry is synced to s60 calendar is this field destroyed or is it just unused?

Thank-you in advance for your advice on this matter.

Hallo.
Can't say for sure, I can only tell you what I have observed.
Calendar in the E61 offers Meetings, memos, anniversary or to do.

In Evolution, which I have in German, I can store a Termin (appointment),
a ganztägige Ereigness(all day event), a Besprechung(meeting) or an Aufgabe(to do).

My experience is, if I put, for instance, a memo in the phone, for which Evolution has no matching category, it turns up there as a Termin(appointment).

Similarly, a Termin(appointment) in Evolution turns up as a meeting in the phone, but so does a Besprechung(meeting).

I have not observed that anything gets destroyed, but rather that the sync process puts it in where it thinks it should be, or leaves it out completely, eg. To Do from the phone doesn't make it to Evolution, but stays in the phone. An Aufgabe(to do) in Evolution has appeared on the phone as a to do, but I think not always. I don't use them much, so can't say much about it.
Hope this helps
Michael

---

### Post by Dead1nside on 2009-09-26
> **audiomick said:**
> 
Hope this helps
Michael

Yes it did, it's a lot more clever than I thought, it's able to cope with a lot of situations.

Thanks for the reply.

---

### Post by eotakos on 2009-10-19
Hello everyone,

Since i've succeeded in syncing my E52 with evolution, i guess it is time i contributed my part in this vast thread (especially after i've extracted so much info out of it...). Note that my mobile device runs on S60 v3.2.3 , Symbian os 9.3 and the ubuntu systems i managed to sync with were hardy 8.04 (desktop) and jaunty 9.04 (laptop) and both worked following the same procedure. Note also that i'm talking about bluetooth connection.

The instructions I followed are these on post #161 by oto. All very accurate and precise. 

Advice: don't trip into guessing your channel!. you might end up hurting your moral. There are other parameters you may be needed to experiment with, and the channel shouldn't be one of them. You will inevitably be needed to find out your bluetooth address ... after you do, use it in this command
```
sdptool browse $MAC
```
to find out all the services your mobile device supports, and the corresponding channels. For my case, it wasn't the "pc suite" service that was needed (nor channel 10) but rather, it was service "SyncMLClient" and channel 8!   (and please don't confuse this with the identifier parameter. it has nothing to do with it, and it remains "pc suite")

Something else that i wanted to say is that somewhere in this thread i read that in order to sync, you need to be browsing the content of the mobile device at the same time (aka to see the contents under  "obex:///". This is highly inaccurate! Using my desktop (8.04), i never could browse my mobile device through obex:/// and even though i managed to sync. So as far as browsing the same time as you sync, the only impact could be the slowing down of the synching. So if you need to check that your bluetooth works with the device just try sending a file to it.

That's it - i wish you best of luck

---

### Post by suyog on 2009-10-21
Chris, You can set direction in sync profile in your phone.




> **jeppo said:**
> Hey guys,

Great guide, extremely helpful.

(Apart from not being able to sync notes) I only have one issue.  How can in sync in one direction only?  Is it possible at all?  I just want to be able to copy my new contacts from my phone over to Evolution without it sending back the old ones.

Thanks,
Chris

---

### Post by suyog on 2009-10-21
> **eotakos said:**
> Hello everyone,

Since i've succeeded in syncing my E52 with evolution, i guess it is time i contributed my part in this vast thread (especially after i've extracted so much info out of it...). Note that my mobile device runs on S60 v3.2.3 , Symbian os 9.3 and the ubuntu systems i managed to sync with were hardy 8.04 (desktop) and jaunty 9.04 (laptop) and both worked following the same procedure. Note also that i'm talking about bluetooth connection.

The instructions I followed are these on post #161 by oto. All very accurate and precise. 

Advice: don't trip into guessing your channel!. you might end up hurting your moral. There are other parameters you may be needed to experiment with, and the channel shouldn't be one of them. You will inevitably be needed to find out your bluetooth address ... after you do, use it in this command
```
sdptool browse $MAC
```
to find out all the services your mobile device supports, and the corresponding channels. For my case, it wasn't the "pc suite" service that was needed (nor channel 10) but rather, it was service "SyncMLClient" and channel 8!   (and please don't confuse this with the identifier parameter. it has nothing to do with it, and it remains "pc suite")

Something else that i wanted to say is that somewhere in this thread i read that in order to sync, you need to be browsing the content of the mobile device at the same time (aka to see the contents under  "obex:///". This is highly inaccurate! Using my desktop (8.04), i never could browse my mobile device through obex:/// and even though i managed to sync. So as far as browsing the same time as you sync, the only impact could be the slowing down of the synching. So if you need to check that your bluetooth works with the device just try sending a file to it.

That's it - i wish you best of luck
Did you manage to sync Notes? If yes, could you please let me know.

---

### Post by eotakos on 2009-11-01
> **suyog said:**
> Did you manage to sync Notes? If yes, could you please let me know.

actually, I read that there is trouble getting to it, so i avoided it. Now that i've added pictures to some contacts on the phone, there is some "pipe error" on the side of the phone that prevents the syncing from working at all.

I know (obviously) this is of no help to you, i'm just saying... anyway - i bothered with this thread because i wanted to pass the contacts from the pc to the phone - the "fine" syncing is not that important to me, although it could be of some use. 

If some time i find the courage to remove the photos off the contacts on the phone and try it again, ill post again :-)

---

### Post by imachine on 2009-11-04
I've tried using the guide on E66 + 9.10.

E66 newest (todate) firmware.

It sorta works.

I deleted the notes like aforementioned, but it only helped a little - it didn't stall on notes, but after I get syncml-obex-client and evo2-sync as "connected" then "sent all changes" then I see a lot of hard disk activity on the computer, then syncml-obex-client gets a status "commited all changes" and evo2-sync "Sent all changes" and the device says "System error!"

Therefore I think it is a problem with evo2-sync. Probably the uploading?

Evolution is off, pidgin is off and Tomboy is off during the process.

After the whole operation my nokia phone is left with bluetooth on, but nonfunctional. Turning it off and on again makes it unable to turn on, and the device needs to be restarted.

Eh, isn't Symbian opensource by now?

Please help because I am so close I can feel it, and using the sync option on the phone would greatly ease my life :)

---

### Post by pingwing on 2009-11-06
I've just discovered [this site]("http://diabo.freehostia.com/symbian/indexhack.htm") which tells you how to mod your Symbian phone so you can cut/copy/paste the Calendar and Contacts files inside! This means you can finally clean everything up after a slow-sync, not only in Evo but also in Symbian, and so remove all those duplicate entries.
Here is a howto that worked for my Nokia E51 (S60 3rd Edition, Feature Pack 1) and Evolution 2.22.3.1, syncing with Multisync 0.90 0.91

***HOW TO GET RID OF THOSE NASTY DUPLICATE ENTRIES***

With your phone:
You will need: The CD and USB cable that came with your phone; a fully-charged battery
1. BACKUP YOUR PHONE! (see the manual for how to do that).
Type *#0000# to see the specs of your phone, then go [here]("http://symbianism.blogspot.com/2008/11/which-nokia-symbian-phones-can-be.html") to see if it's hackable. If it isn't yet, you're out of luck – but keep an eye out for further developments.
2. Go [here]("http://diabo.freehostia.com/symbian/indexhack.htm") and choose the best way to mod your phone (this is quite an adventure, so make sure you have a little time).
;)(tips for travelers:
a - to install X-Plore,  I installed PC Suite on an nLite version of XP running on VirtualBox. You may find a neater way.
b -  if, when you try to install ROMPatcher you get a message saying “certificate expired”, change your phone's date to 11/15/2008 and try again. Don't forget to put back the correct date when you're done)
3. Make a copy of the Calendar file (C:\Private\10003a5b\Calendar) in your phone and put it in a safe place on your computer.
(On some phones the folder name is 1000395b)
4. Delete  the Calendar file in your phone.
5. Repeat steps 3 and 4 with the Contacts file (C:\Private\100012a5\DBS_100065FF_Contacts.cdb).
(On some phones the folder name is 10001295)
;)(tip – X-Plore doesn't have a Paste function in the edit menu. You paste by navigating to the folder you want, and then pressing the main enter button on your phone – the one in the middle)

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

Now connect your phone via Bluetooth and run a sync. Warning! This may take as long as 15 minutes, and Multisync seems to hang at least once. If you interrupt it[-X, you'll cause an unclean sync and you're back to square one. Best thing is to switch to another desktop and go back [here]("http://diabo.freehostia.com/symbian/indexhack.htm") and look at all the other interesting things you can do with your modded phone. Or feed the dog.

That's it. If all went well, everything should be back to normal at both ends.

---

### Post by audiomick on 2009-11-07
Hallo.
First of all, thanks to Pingwing for the tip. The site you mention looks really interesting.

A bit of information, and a question: has anyone else had this problem?
I updated, using the update function,not a new install, from 9.04 to Ubuntu 9.10 the other day.

I use **_USB, NOT BLUETOOTH_** for my transfers.
After the update, I was back to root only access to the USB port. Got around that, then discovered that the transfers aren't working anymore.

The phone and the computer find each other, the transfer starts, and even, as far as I can see, gets most if not all entries across. Right near the end, where normally the friendly confirmation of a successful transfer would pop up, the computer opens an error window complaining the some components could not be read.

My first suspicion is that an update in Evolution has brought a change with it. As far as I can see, all the Open sync and Obex stuff is the same since 8.04. The phone hasn't changed, so it nearly has to be Evolution. Does anyone know, or even suspect, anything useful?

Michael

---

### Post by suyog on 2009-11-10
Any luck with Notes sync? I think notes are not still supported by evo2-sync plugin.

Also anyone of you tried to get syncml-http-client plugin? I am not able to get it anywhere.

---

### Post by audiomick on 2009-11-30
Look at this:
[http://ubuntuforums.org/showthread.php?t=1341792](http://ubuntuforums.org/showthread.php?t=1341792)

If we all go off and vote, maybe life will get easier.

---

### Post by suyog on 2009-11-30
Yes, I am there, fully support the idea, spread the word and get more people to vote.
:)

---

### Post by forest555 on 2009-11-30
Yes it is very nice but I do not understand why they spoilt syncing in Karmic. It worked and still works perfectly in Jaunty, Intrepid and Feisty.

Do you think someone is trying to repair it?

---

### Post by suyog on 2009-12-01
I am not sure why this is happening. I will try to get some Eseries phone from friends to test, but my N82 works. Strange!!!

---

### Post by forest555 on 2009-12-01
> **suyog said:**
> I am not sure why this is happening. I will try to get some Eseries phone from friends to test, but my N82 works. Strange!!!

Only with Karmic.
Yes, very strange. First syncing if Evolution is empty works. After any change of Evolution's contact or calendar you get an error. After that you can do slow syncing but also this ends always with error.

it is so sad.

---

### Post by rewlad on 2009-12-23
I had a problem, how to get SMS out of my E51, while migrating to N900.
I was not able to use PC Suite, because it does not have Linux version.
The solution for me was to use SMS Export symbian utility:
[http://www.nokia.com.hk/get-support-and-software-en/download-software/s60/s60-phone-and-application-download/nokia-n73](http://www.nokia.com.hk/get-support-and-software-en/download-software/s60/s60-phone-and-application-download/nokia-n73)
It exports messages to the memory card as simple text files.

---

### Post by bertschollaert on 2009-12-27
Thank you all so much for the tips and workaround. However syncing my Nokia 6303c with Evolution through USB still doens't work completely. I do it through Ovi.com at the moment, but that's cumbersome and costly.

I already tried all usual alternatives (opensync, syncml, gnokii, wammu...) without succes. Can you point me to a thread for this?

Thank you in advance.

---

### Post by audiomick on 2009-12-27
Hi Bert.
I had my E61 working, but it stopped when I updated to 9.10. I have no idea why. From what I have seen in various posts, there is a problem.

What is yours doing? Does it not work at all, or does it get part of the way and then stop?

Is your system 9.10, and was it updated or a fresh install?

---

### Post by bertschollaert on 2009-12-28
Hi, I'm also working on 9.10. So far I did not succeed in connecting my Nokia 6303c to Ubuntu 9.10 with USB. Syncing my Nokia to Ovi.com and then syncing Ovi.com to Evolution (running a Microsoft Exchange configuration for my work) did work however. The downside here is that it costs me some money to each time connect my Nokia to Ovi.com.
Connecting via bluetooth is possible for me with Wammu, but this laptop doesn't have a bluetooth connection.

---

### Post by audiomick on 2009-12-28
Hallo Bert.
There is something to take into consideration with the USB connection. The normal user doesn't have the right permissions. Have you changed anything there?

Your name suggests you might be German. If you can read German, you could look at this:
[http://blog.netandif.de/2008/02/22/sync-von-nokia-e61-und-evolution-per-usb-unter-linux/](http://blog.netandif.de/2008/02/22/sync-von-nokia-e61-und-evolution-per-usb-unter-linux/)

Bear in mind that this is a couple of years old. I tried it again just last week, and it didn't work exactly as described.

I would prefer you to read it first, then I will let you know what I did differently, as that means a lot less typing for me...:)

If you can't read German, let me know, and I will summarize it.

---

### Post by suyog on 2009-12-28
@Bert, I never got Wammu to work for me. Have you got any success?
About connecting via USB, do you use "PC Suite" option on connection?
Also do other modes like "data transfer" or "Media Transfer" work?
Try to restart both laptop and phone and work again.
For Sync with USB , you will need to change few settings in OpenSync.

Check this thread for details [http://ubuntuforums.org/showthread.php?t=1327147](http://ubuntuforums.org/showthread.php?t=1327147)

---

### Post by bertschollaert on 2009-12-29
Hi Suyog, thank you a lot for the suggestions, I'll try them as soon as possible and let you know.
Audiomick, unfortunately I'm Flemish, so German is not completely my cup of tea:(. Could you shortly summarize this, please?

---

### Post by audiomick on 2009-12-29
Ok Bert, I'll give it a go. Bear in mind that this is broken on my system. When I start the sync, (apart from the fact that I am now getting the message "the last sync was unclean" and it does a slow sync) it gets almost all the way through, even transfers apparently everything from the phone to evolution, then breaks off just before it is finished. I have seen a number of posts describing the same behaviour. I am not sure, but it might only relate to E series phones. Yours is not E series, so it is possibly worth a try.

This is a long explanation, but I don't want to just give you a couple of commands and hope for the best. I want you to have a little bit of background as a basis for working this out.

There is also a purely mechanical issue. The plug on my phone to USB cable on the phone end is absolutely useless. It doesn't sit well, and has caused a bad sync once or twice by losing it's connection in the middle of the process. I have to plug it in and make sure that the phone is lying flat with no strain on the cable.


Now quoting/translating from the German guide I used to set mine up. My comments are preceded with [COLOR="Red"]#[/COLOR]

Accessing USB devices in Gutsy is only possible with root privileges. 
[COLOR="Red"]#[/COLOR] this is still true in Karmic

This is shown by
```
syncml-obex-client -u
```
which yields the message
"superuser privileges are required to access complete USB information"

Plug in the phone and do
```
lsusb
```
you will get something like this
```
mick@ubuntu-desktop:~$ lsusb
[COLOR="Red"]Bus 004 Device 003: ID 0421:044d Nokia Mobile Phones E61 (PC Suite mode)[/COLOR]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c317 Logitech, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
The line in red is the relevant one.

You need to change /etc/udev/rules.d/40-permissions.rules
[COLOR="Red"]#[/COLOR] the problem is, "40-permissions. rules" doesn't exist on my Karmic. Something has changed with udev, which is what regulates USB access, among other things. A look at
```
man udev
```
is a bit confusing, but not a bad idea.

[COLOR="Red"]#[/COLOR]In short, when you add a rule, if the number at the start is bigger than the existing ones, it will have precedence. The attached screenshot shows the current contents of my /etc/udev/rules.d . The "80-permissions.rules" is the one I added for the phone.

To edit the rule, you need the info from "lsusb"
[COLOR="Red"]#[/COLOR]this is the line in red above. Yours may be a bit different. We will be creating a rule, not editing. I will show what I did further down.

After editing,
```
sudo udevadm control --reload-rules
```
will reload the udev rules.
[COLOR="Red"]#[/COLOR]this did not seem to work; I had to log off and back on.
edit: I just looked at the man page for "udevadm". What is there suggests that you might have to unplug the phone to reload the rules

Doing ([COLOR="Red"]#[/COLOR]after adding the new rule and reloading the rules)
```
syncml-obex-client -u
```
will now yield something like this
```
mick@ubuntu-desktop:~$ syncml-obex-client -u
Superuser privileges are required to access complete USB information.
Found 3 USB OBEX interfaces
Interface 0:
	Manufacturer: Nokia
	Product: Nokia E61
	Interface description: SYNCML-SYNC
Interface 1:
	Manufacturer: Nokia
	Product: Nokia E61
	Interface description: PC Suite Services
Interface 2:
	Manufacturer: Nokia
	Product: Nokia E61
	Interface description: SYNCML-DM
Use '-u interface_number' to connect
```

Here is what I did.

I created a new rule in /etc/udev/rules.d called "80-permissions.rules"

to get to the directory```
cd /etc/udev/rules.d
``` 
to open the editor as root```
gksu gedit
``` 
this is the contents of my rule
```
#for the E61

BUS=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="044d", GROUP=="plugdev", USER=="mick"
```
if you look back at the line I highlighted in red from "lsusb",
```
[COLOR="Red"]Bus 004 Device 003: ID 0421:044d Nokia Mobile Phones E61 (PC Suite mode)[/COLOR]
``` you can see where the numbers "0421" and "044d" came from. User name has to be your user name, of course.

As I mentioned, I had to log off and back on to make the rule apply. It is working, because the output of "syncml-obex-client -u", as shown above, changed after adding the rule.

Apart from all of that, in your syncml-obex-client config, there has to be
```
 <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel></bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
```
i.e. bluetooth channel not required and the interface for syncml-sync from the output of "syncml-obex-client -u" that we looked at further up.

I hope this is a help to you. Let me know, please, if you could get it working or if it was all too much. :)

---

### Post by bertschollaert on 2009-12-30
Hi Suyog and audiomick, thank you both for the suggestions. They are closely related to each other I think, in fact the howto audiomick provides is very similar to [https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync]("https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync"), which is referenced in Suyog's post, or are there some major differences? 
I had however already tried this, with a quite unclear outcome. Using the CLI, I can see a lot of activity, but (almost) every event gives a conflict between both devices, so I have to select one of them each time.
Using both CLI and GUI, I see a message firstly appearing that the phone cannot be reached:  "Member 1 of type evo2-sync had an error while connecting: Unable to open anything", so that doesn't look too good, does it?
Anyway I'll try some further with audiomick's howto and the other suggestions. Thank you both and my best wishes for 2010!

---

### Post by bertschollaert on 2009-12-30
Hi audiomick,
I tried your suggestions, but the result is unfortunately the same: Opensync starts with an "Error while connecting" message, the phone says "Sync started", but resides on 0%. Thanks anyway for the suggestion, or do you think I did something wrong?

---

### Post by audiomick on 2009-12-30
> **bertschollaert said:**
> , but (almost) every event gives a conflict between both devices, so I have to select one of them each time.

What helped me with this was using the "remember my choice" option. If I tried to do them all individually, something would always time out and the sync would fail.


> Using both CLI and GUI, I see a message firstly appearing that the phone cannot be reached:  "Member 1 of type evo2-sync had an error while connecting: Unable to open anything", so that doesn't look too good, does it?

You are right, this doesn't look good. All I can offer is a checklist
* is the phone showing that it has a connection?
* can you see the phone with "lsusb"?
* can you see the phone with "syncml-obex-client -u"?
* is the config file right?
If that is all correct, I am at a bit of a loss as to know what to try next.

---

### Post by bertschollaert on 2009-12-30
Hi Michael, thanks again. I'm afraid though I'll have to answer yes to all your checklist questions, but probably I did something wrong in the configuration? Or what could this error specifically be due to? Anyway, after tomorrow I'll try some more, have a great new year's eve.
@ Suyog, concerning Wammu, it connected my phone, but only some basic information was shown, and calendar not supported. I tried this with all available modes on my phone (the ones you mention). Thanks though for your help.

---

### Post by suyog on 2010-01-02
@bertschollaert, Wammu never worked for me with S60 phones. I guess it works for some, doesnt for many. Also I dont think they are developing it further.

Surprising I am not facing much issues with sync. I am now only waiting for Notes sync.

Have a great new year 2010, I hope we can have better solution!!!

---

### Post by bertschollaert on 2010-01-19
@audiomick: I gave it a fresh try, but unfortunately no better results. My lsusb shows my phone, I followed your instructions closely, but when edit the 80-nokia-mobiles.rules with my numbers (being idVendor 0421 and idProduct 01bo and USER schollbe), then unplug the phone, run "sudo udevadm control --reload-rules" and plug the phone back in, I get 3 interfaces when running "sudo syncml-obex-client -u", but all 3 have Interface description: (null). This is the case when choosing the PC suite option on my phone (the other options don't give me any interface). In 80-nokia-mobiles.rules I tried some other things, as mentioned in [https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync]("https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync"), but these also didn't work.

When I try the tool with all 3 interfaces, some synchronization seems to happen, but after a while some errors appear:
...Received an entry 305 with data of size 8 from member 2 (syncml-obex-client). Changetype ADDED
Member 2 of type syncml-obex-client had an error while getting changes: Link Error: 0x0
Member 2 of type syncml-obex-client just disconnected
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members
 
Any suggestions or should I just get myself another phone?;)

---

### Post by audiomick on 2010-01-19
Hi Bert.
Sorry to hear that you had no success. To be honest, I haven't even looked at mine the last couple of weeks, other than trying to find some info in the 'net occasionally.
That "couldn't read to one of the members" looks suspiciously like the fault that has been turning up for other people too.

I really don't know what is to be done at the moment, apart from wait. It's tragic really; it worked so well for a while.

---

### Post by pingwing on 2010-02-16
Hi all
After a lot of headbanging, I've got calendar and sync working again (Nokia E51 and Hardy LTS), and I'd like to share a couple of ideas.
First this “Unable to read from one of the members”. When it happened to me, I ran a sync in terminal and there it said something about a broken pipe. So I looked inside .opensync in my home folder, and (after making a backup copy, of course) deleted all the files in Group 1 except the  ones with the extension .config. I then ran a sync, all the other files came back by magic, but this time it worked. Almost.
The next thing I wanted to discover is why opensync seems to hang, make duplicate entries and generally make a mess of things. A sync in terminal gave me this at the end:

Received an entry 20090310T190422Z-22399-1000-1-35@pingwing-desktop with data of size 0 from member 1 (evo2-sync). Changetype DELETED 
Member 1 of type evo2-sync just sent all changes 
Member 2 of type syncml-obex-client just sent all changes 
All clients sent changes or error 
All conflicts have been reported 

(process:26582): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed 
Member 1 of type evo2-sync committed all changes.

And then it hung.
So I sez to myself: what if syncml is just so primitive it can't handle anything except the basic “who-where-when”, and the frills like “how often”  or “public or private” give it indigestion? To see, I looked back at all my entries in evo and deleted all the multiple entries and anything that contained any more than “who-where-when” info. To my surprise. I found some stuff dating back to 2002 - and I didn't even use Linux back then:confused: I also found one entry that evo didn't let me delete at all, and it corresponded to the one indicated “size 0” in the clip above!
At this point I extracted the calendar.ics file from the evo backup, opened it with gedit, deleted the corresponding VEVENT, then saved the file, put it back in the backup folder, and restored evo with it. The offender had now vanished.
The only thing left to do now was to delete the calendar in my phone. (Mine is now modded, so that was easy, but if you don't want to go through the hassle of modding, a quick and dirty way is to reset your phone.)
The next  command-line sync copied all my stuff back into the phone, and every sync since then has  worked fine.
Could this work for someone else?
BTW I stopped using blueman and went back to the gnome bluetooth applet – it seems to work better on Hardy.

---

### Post by audiomick on 2010-02-16
Thanks for the post Pingwing. I don't know if it will help, but it gives me something to think about at least...;)

---

### Post by imachine on 2010-02-16
I know this maybe is not all on topic but my problems got resolved once I obtained the HTC hero, a telephone device with Linux Android on board. :)

---

### Post by Bharath on 2010-02-18
I have posted a partial solution on ->

[http://ubuntuforums.org/showthread.php?p=8844076#post8844076](http://ubuntuforums.org/showthread.php?p=8844076#post8844076)

Bharath

---

### Post by leoh on 2010-02-21
I've been reading this topic and been unable so far to sync.
The thing is that most guides are old (2007 or even older), and the instructions, screenshots, versions, repositories, etc are no longer valid on Ubuntu 9.10.
Can anybody provide me with an up-to-date tutorial or something?

---

### Post by audiomick on 2010-02-21
Hallo Leoh
I haven't seen anything newer than this thread. Someone, suyog I think, did report success with 9.10, as far as I recall. Look back at the posts from around the end of October and start of November last year. That should be around 30 to 35 posts back from this one, I think.

---

### Post by suyog on 2010-03-06
hey you are still not able to sync? thats really strange.
anyways I have come back to 9.04 after disaster with 10.04 Alpha.
I wasted my 2 days to get back online , up and running.
:) Never ever try alpha software, lesson learned.
I am also trying syncevolution which is being developed as part of Moblin(now MeeGo) :)

Their latest version 1.0 Beta 2 has support for sync with phones over Bluetooth via GUI. Give a try and let me know how it goes.
I posted how-to earlier when this feature of sync with phones was not there.
[http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html](http://mobileyog.blogspot.com/2009/11/how-to-sync-contactscalendar-from.html)
I am planning to post new how-to based on new version soon once i get some free time :)

---

### Post by audiomick on 2010-03-07
Hi suyog, thanks for keeping us up to date!
I haven't made any new attempts for a while, but that syncevolution thing looks promising. Do you happen to know how well it works (if at all??) for syncing the phone to Ubuntu/Evolution via USB? I don't want to use Ovi.com if I can avoid it, and my desktop doesn't have bluetooth.

---

### Post by suyog on 2010-03-07
I tried sync with my N82 via syncevolution 1.0 beta 2 and it failed via Bluetooth. I have sent logs screenshots to developers and hope to get some solution soon.
Regarding Sync via USB, I am not sure if syncevolution can do it now. I will check that too with developers.

---

### Post by engellion on 2010-03-24
> **leoh said:**
> I've been reading this topic and been unable so far to sync.
The thing is that most guides are old (2007 or even older), and the instructions, screenshots, versions, repositories, etc are no longer valid on Ubuntu 9.10.
Can anybody provide me with an up-to-date tutorial or something?

Hi.  I came up against the same problem trying to sync my E71 with Evolution via Bluetooth on Ubuntu 9.10.  I have finally got it to work.  Once you set it up, it is pretty straight forward.  I've been successful using the OpenSync and Multisync tools + Multsyc0.90 gui.  

Here is a **[Step-by-Step Guide]("http://ubuntuforums.org/showthread.php?t=1437399")** to how I got it going on my E71.  Not sure if anything is different for the E51, but if the E51 uses SyncML then it should be the same setup process.  

[http://ubuntuforums.org/showthread.php?t=1437399]("http://ubuntuforums.org/showthread.php?t=1437399")

Cheers.

---

### Post by Jared Norris on 2010-08-10
I have spent hours trawling forums and other blogs for solutions for my Nokia e51 because I have wanted to sync contacts and calendars via bluetooth as well. I had some success back in 2007 with opensync and/or multisync tools but there was always the fear of the apparently random double ups or deletions.

Move forward a few years and it's 2010 and new lucid install and I felt I should have another go at getting this right. Several broken attempts later I found the Sync GUI interface and thought I'd try this. If failed hard to start with by itself. I then stumbled onto the syncevolution website and found these 2 links [http://syncevolution.org/wiki/nokia-e71-ubuntu-1004-lts](http://syncevolution.org/wiki/nokia-e71-ubuntu-1004-lts) and [http://syncevolution.org/wiki/compatibility-nokia-6220-classic](http://syncevolution.org/wiki/compatibility-nokia-6220-classic) and reading over them both I was able to configure my Nokia e51 to work flawlessly every time. No double ups, no broken attempts, no deletions just pure bliss and has worked for the last few months now.

When I have a spare hour or so I was going to document the exact steps I took because it was actually a combination of the 2 posts. It relies on the cli for the vast majority but it's not anything really scary.

I just wanted to put this out there for anyone still having problems syncing because it does work it just takes some setting up (I did it in less than an hour once I actually found those 2 pages).

---

### Post by fsando on 2010-08-10
Thanks, I'll look at it later for my e71 ;)

---

### Post by emorkay on 2010-09-09
Hi all,
I was finally able to sync contacts and calendar entries on my Nokia N73 with Evolution using multisync in Ubuntu Lucid. But Evolution doesn't seem to read the end date of the recurring appointments properly. And it displays the recurring appointments as if they repeat for an indefinite time. It seems to be reading the start date only. How can I correct this?
Any help in this regard is appreciated!
Thanks,
Rajendra

---

### Post by Dead1nside on 2010-09-15
Has anyone managed to sync "Tasks" in Sunbird (or in Evolution if it has an equivalent) with the S60s ToDo list? This'd be the next step for me.. Does S60 store the ToDos in the same database as the calendar entries?

Thanks.

---

### Post by suyog on 2010-10-09
todos are stored in calendar in Nokia phones(S60 also). These get synced with Tasks in Evolution. I could sync that with syncevolution with my various nokia phones. check this link
[http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html](http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html)

I am sure we can find way to sync with Sunbird also.

---

### Post by eotakos on 2010-11-05
Hello everyone!...

So! Here is how I did it for a nokia E52 with syncevolution  		(my syncing includes contacts, calendar, memos)


(-big parenthesis- because I hate getting credit for something I didn't come up with or anything, everything posted below is the outcome of the two posts:

[http://syncevolution.org/wiki/nokia-e71-ubuntu-1004-lts](http://syncevolution.org/wiki/nokia-e71-ubuntu-1004-lts)  and 
[http://syncevolution.org/wiki/compat...a-6220-classic](http://syncevolution.org/wiki/compat...a-6220-classic) 

which are given by "head_victim" on that same page. The first link gives an idea about how things work, the second one gets you -if not there- closer :-)  
-end of big parenthesis-)


The packages needed to be installed for this to work are:
syncevolution
sync-ui

... and their dependances -if any extra- :-)   the installation of these, plants a "sync" icon on your internet menu.

---------------------------------------
step 1) link the two bluetooth devices.

what you need to do is go to "set up a new device" from the bluetooth menu, detect and add your mobile on the list.
Follow the instructions to where they take you in order to do the pairing. Don't worry if the pairing isn't kept alive - mine dies too after 1 or 2 seconds.

On your mobiles side, you need to go to the bluetooth menu, then to "reliable devices", where you should find your pc's bluetooth name, and make it a reliable device.

About the pairing: I've read in many posts that you should be in an "copying files" mode in order to sync. This doesn't apply in my case...

----------------------------------------------------
step 2) "see" the mobile phone through syncevolution

Go ahead and open your new installed "sync" programm on your menu! - If it is the first time you run the programm, you should read "select sync device" (click on it)
... and if your mobile phone is on the bluetooth list (as added in the previous step), it should appear further down on the list, under "direct sync".
From the dropdown list, choose "nokia_7210c" and "use these settings", and then "save and replace current service". 

Don't do any syncing - just close the window

------------------------------------
step 3) get to know the config files

open a terminal, and execute : "nautilus ~/.config/syncevolution" - I guess this makes navigating easier...-

navigate to ->default->peers , and you should see your nokia_7210c. You can rename the folder as you like to call your phone while syncing.

now navigate to ->"your phone"->sources, and you can see folders that correspond to all the services that are supported for syncing by syncevolution (which doesn't mean that all services are
there for syncing with every phone...)

every folder contains a config.ini file that dictates the sync parameters for every service. The parameters, syntax and the structure of the file is the same in every case.

The parameters that we are concerned with are:
"sync="  		//  the way the syncing is meant to be done (two way, one way, etc - look at the commented lines above the field)
this is in the beginning of the files, and 
"uri=" 
at the very end of the files. I don't remember changing "type=" (at the end of the files as well) at any point, but to make sure, I'll give you that setting for every case as well (in a bit).

the "uri" field is (the way I see it) the codename that the mobile phone expects to see in order to sync the corresponding field. To find which are these codenames in your case, navigate to your 
mobile phone's menu (for e52):
> Note: phone menus are not identical, because I'm not using the english menus 
menu -> control panel -> phone -> sync., then...  options -> edit sync profile, and then scroll down to see "sync. setting contacts", "sync. setting calendar", "sync. setting notes " // clicking on these fields, you get the corresponding "codename" under the field "data base contacts", or "data base calendar" or "data base notes". Mine are "Contacts", "Calendar", "Notes" respectively. If yours are different, I would suggest keeping your settings, and adapt the settings of syncevolution further below.

-------------------------
step 4) start syncing...

The idea is that for the first sync, evey field must be synchronized by itself. So, go to every config.ini file - exept for the addressbook - and switch the "sync=" value to "none". At the addressbook folder, the config.ini file should have the following setup:
sync =  two-way 
type = addressbook
uri = Contacts

(I would suggest that you mind the capitals)

save the config.ini files, and go ahead and do your first sync. Open a terminal and type: 
syncevolution "your-phone"   
where your-phone is the name you gave to the directory under "~/.config/syncevolution/default/peers"

You should see some syncing going on / if you don't, among the messages displayed, you should see
"Synchronization failed, see /home/*******..../syncevolution-log.html"   - go ahead and open this file with your browser.

This file, among others, says which channel is used to make the connection. This channel must be the same as the channel the phone uses for SyncML service. So, if it isn't successfully detected automaticaly, we have to check that too:
type at your terminal:
```
hcitool scan
```
this should show you your phones bluetooth hardware address a.k.a. a number like 00:32:45:.....
then, use this number to see the services and the corresponding channels:
```
sdptool browse 00:32:45:.....
```

this will have a quite long output, but as I said, what we are interested in is the "SyncMLClient" service (for e52 channel 8 ). If the channel number stated at this output is not the same as the one displayed at the error messages, you can change the channel syncevolution uses, by editing "~/.config/syncevolution/default/peers/"your phone"/config.ini"
go to the "syncURL=" line, and add at the end "+channel" where channel is the working "SyncMLClient" channel (see the commented instructions just above the field).

save the file and try the sync. again.

if you succeed, it means that you repeat the same procedure with calendar and memo separately (for every other sync-field, "sync = none"). Note that for nokia E52, sync works with the "calendar" configuration folder, and not the "calendar+todo" configuration folder.
their config.ini files should have the following settings:

calendar:
sync = two-way 
type = calendar
uri = Calendar


memo:
sync = two-way  
type = memo
uri = Notes


----------------------------
step 5) complete your setup

after you have done all contacts, calendar and memo syncs separately, you can turn all three sync-fields to "sync = two-way", and enjoy flawless syncing everytime / no duplicates :-), just open a terminal and type:
```
syncevolution "your-phone"
```


that's all -

---

### Post by emorkay on 2010-11-05
Hi,
Thanks for a such a nice post.
I am getting the following error when I try to sync my Nokia N73 with evolution.
"First ERROR encountered: OBEX Request 2 got a failed response Unknown response"
Any Ideas??
Thanks,

---

### Post by eotakos on 2010-11-06
hm... I really can't say. 

The only thing I would suggest is try playing around with the channels. Scan your device for services/channels as I describe above, and maybe for N73 another service does the job.

-sorry-

---

### Post by emorkay on 2010-11-19
> **eotakos said:**
> hm... I really can't say. 

The only thing I would suggest is try playing around with the channels. Scan your device for services/channels as I describe above, and maybe for N73 another service does the job.

-sorry-
I have really been busy...will try it and let you know...
Thanks...

---

### Post by suyog on 2010-11-24
try this instead,

[http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html](http://mobileyog.blogspot.com/2010/06/easiest-way-to-sync-your-mobile-phone.html)

---

