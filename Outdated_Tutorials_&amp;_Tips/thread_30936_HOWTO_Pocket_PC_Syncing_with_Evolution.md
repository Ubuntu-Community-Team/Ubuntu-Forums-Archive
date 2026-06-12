---
title: "HOWTO: Pocket PC Syncing with Evolution"
date: 2005-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by tUrtleAE86 on 2005-05-01
At first glance, [SynCE](http://synce.sf.net)  and [Multisync](http://multisync.sf.net)  can seem a bit daunting. But, it really is not nearly as bad as it seems. I got a little help from this [thread](http://www.ubuntuforums.org/showthread.php?t=24805&highlight=ipaq+evolution)  as well.

This HOWTO is based on syncing my Dell Axim X3i with Evolution, but it should carry over to IPAQs and other Pocket PCs.

**[SIZE=3]Does Linux like your PDA?[/SIZE]**

1) Connect your Pocket PC and type "dmesg" in a shell to see if the ipaq kernel module is loaded. The output might look like the following. Take note of the tty used for the connection.
```
usb 4-2: new full speed USB device using uhci_hcd and address 3
ipaq 4-2:1.0: PocketPC PDA converter detected
usb 4-2: PocketPC PDA converter now attached to ttyUSB0
```
2) Optionally, you can use "cat /proc/bus/usb/devices" to check for a USB device that's using the ipaq kernel module.
```
T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=413c ProdID=4002 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

**[SIZE=3]SynCE Setup and Configuration[/SIZE]**

1) Install the required packages for SynCE:
```
sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
```
2) synce-serial setup will be invoked by apt, follow this through using the default settings, unless you have reason to do otherwise. 
```
/dev/ttyUSB0
local address: 192.168.131.102
remote address: 192.168.131.201
no dns entry needed
```
3) Perform the following the following command to tell SynCE where to look. This seems redundant, but doesn't hurt.
```
sudo synce-serial-config ttyUSB0
```
4) Start the SynCE connection daemon by typing "dccm" in a shell. Use "dccm -p password" if your Pocket PC is password protected.
5) Initiate a serial connection by typing "sudo synce-serial-start" in a shell. You should be greeted with "synce-serial-start is now waiting for your device to connect".
6) "synce-pstatus" shows a LOT of information about your Pocket PC, such as current mode of operation, battery charge level, memory usage as well as backup battery status. If you want to see some other synce commands, type "dpkg -L librapi2-tools". You can use these commands to do things such as installing Pocket PC programs, etc.
7) Create the partnership between the Pocket PC and your computer. There are 2 slots on the device, so the INDEX can be 1 or 2.
```
synce-matchmaker create INDEX
```
You should be greeted with:
```
Partnership creation succeeded. Using partnership index INDEX.
```

**[SIZE=3]Multisync Setup and Configuration[/SIZE]**

1) Install the required packages for Multisync:
```
sudo apt-get install libmultisync-plugin-all multisync
```
Or, alternatively if you want to skimp on the packages:
```
sudo apt-get install libmultisync-plugin-evolution libmultisync-plugin-backup multisync
```
2) Start Multisync by typing "multisync" in a shell. You can also do via Applications > Accessories > Multisync, but the shell gives you a lot of feedback which can be helpful the first time you use it.
3) Create a new synchronization pair where one of the plugins is "SynCE Plugin" and the other is "Ximian Evolution 2", the order doesn't matter. You may need to create a new Contact List, Task List and Calendar, so that the default ones aren't used. I'm not sure if this is needed, but it was mentioned in the other thread.
4) Press the "Sync" button.
Initially, I had no entries in Evolution so for some reason, I had to modify all of the entries on my Pocket PC so that the timestamp would register each entry as a 'change', otherwise no entries were sync'd. There must be a simple workaround for this, but I'm not sure at this time.

**[SIZE=3]Disconnecting Your Pocket PC[/SIZE]**

1) Shutdown Multisync
2) "killall -HUP dccm" to kill the serial connection.
3) AS A LAST RESORT, run "synce-serial-abort", if the above command doesn't work.

Please let me know if you have any problems or suggestions.

Have fun!  :)

---

### Post by jrohde on 2005-05-01
> Initially, I had no entries in Evolution so for some reason, I had to modify all of the entries on my Pocket PC so that the timestamp would register each entry as a 'change', otherwise no entries were sync'd. There must be a simple workaround for this, but I'm not sure at this time. 

In Multisync, click "Options" and "Show resync button". Then click "Resync".

---

### Post by derrick1985 on 2005-05-01
Ok, I've been able to make the connection through synce, and can check status, even list my installed programs.

Now, when I try to use Multisync, i get confused. Do i actually need to have synce running everytime I want to use Multisync?

Also, I can't seem to be able to sync my information. I want to synce my personal information from my pocket pc (ex: contacts) to Evolution, but everytime I hit sync, it doesn't work.

HELP! And yes, I have my firewall disable for this.

---

### Post by lynng on 2005-05-02
This is an efficient howto, thanks.

I have found that the Multisync connection only seems to work one-way, however.  Changes made on my PPC show up in Evolution, but changes & new entries in Evolution do not get transferred to my Pocket PC.

This makes it practically useless to use Evo at all, since I have to add/modify my entries from the PPC.

Also, the appointment times & dates do not transfer properly to Evo.  The year on some of my appointsments was 1646!  Nearly all of the appointment times were changed to 8am.  I have way too many entries to change them one by one in Evo.  Why are only some of the times/dates correct & some wrong?  Shouldn't Multisync read the info the same way each time it syncs?

Until these issues can be fixed, there is really no point to going through the slightly tedious process of starting synce.

Also, I never had success with the hotplug script provided on the synce website, and always have to start it manually.

---

### Post by tUrtleAE86 on 2005-05-03
[QUOTE=derrick1985]Ok, I've been able to make the connection through synce, and can check status, even list my installed programs.

Now, when I try to use Multisync, i get confused. Do i actually need to have synce running everytime I want to use Multisync?

Also, I can't seem to be able to sync my information. I want to synce my personal information from my pocket pc (ex: contacts) to Evolution, but everytime I hit sync, it doesn't work.

HELP! And yes, I have my firewall disable for this.[/QUOTE]

Yup, you ALWAYS have to do the following to sync:

```

dccm
sudo synce-serial-start
multisync (or start multisync using the menu)

```

Try doing a resync, that should sync all your contacts from your Pocket PC -> Evolution.

---

### Post by tUrtleAE86 on 2005-05-03
[QUOTE=lynng]This is an efficient howto, thanks.

I have found that the Multisync connection only seems to work one-way, however.  Changes made on my PPC show up in Evolution, but changes & new entries in Evolution do not get transferred to my Pocket PC.

This makes it practically useless to use Evo at all, since I have to add/modify my entries from the PPC.

Also, the appointment times & dates do not transfer properly to Evo.  The year on some of my appointsments was 1646!  Nearly all of the appointment times were changed to 8am.  I have way too many entries to change them one by one in Evo.  Why are only some of the times/dates correct & some wrong?  Shouldn't Multisync read the info the same way each time it syncs?

Until these issues can be fixed, there is really no point to going through the slightly tedious process of starting synce.

Also, I never had success with the hotplug script provided on the synce website, and always have to start it manually.[/QUOTE]

Multisync for Evolution is quite buggy. :(
It seems to work decently well for contacts and tasks, but still has a long way to go for calendar synchronization. It has issues with non-recurring appointments, let alone recurring appointments. One thing that bugs me is that the notes field for tasks in my Pocket PC doesn't map to the description field in my Evolution tasks.

---

### Post by derrick1985 on 2005-05-03
[QUOTE=tUrtleAE86]Yup, you ALWAYS have to do the following to sync:

```

dccm
sudo synce-serial-start
multisync (or start multisync using the menu)

```

Try doing a resync, that should sync all your contacts from your Pocket PC -> Evolution.[/QUOTE]

Nope, still a no go.

---

### Post by webwalker on 2005-05-13
So basically, what I'm hearing is that multi-sync / synce is BROKEN for evolution and broken for Ubuntu.

For Pete's sake, I'm willing to PAY someone to make this bloody thing work. I seems like the synce people are spending all of their time trying to make the software work with KDE. Do I need to just give up and change desktops to get one silly application working?

Pardon the rant, I've just been waiting for the last two years for them to get it together on this package. PPC is now outpacing Palm sales almost 2:1; how long is it going to be before the Microsoft press notices that "Linux can't Sync" and points out the fitful progress of hardware integration. I know MSFT isn't making this easier, but the community has attacked bigger problems than this and licked it. What is so tough about syncing a silly PDA?

RMW

---

### Post by lynng on 2005-05-13
Well, you don't necessarily have to switch to KDE completely.  You could apt-get only kontact.  The KDE libraries would have to be installed.  I have thought about trying this myself to see if the kitchensync app is any better at getting the correct times/dates of appointments.  I've already got synce working, so it *should* be trivial to test it w/ kontact/korganizer.  I will try it over the weekend and post results.

---

### Post by derrick1985 on 2005-05-13
[QUOTE=lynng]Well, you don't necessarily have to switch to KDE completely.  You could apt-get only kontact.  The KDE libraries would have to be installed.  I have thought about trying this myself to see if the kitchensync app is any better at getting the correct times/dates of appointments.  I've already got synce working, so it *should* be trivial to test it w/ kontact/korganizer.  I will try it over the weekend and post results.[/QUOTE]

Please do, I would love to finally get my PPC syncing, preferring gui though.

---

### Post by maltje on 2005-05-15
I trying to follow the things above to let my LOOX sync with my laptop,but you're speaking about sudo synce-serial-config ttyUSB0

but my pocket pc is connected with usb,is that a problem?

---

### Post by lynng on 2005-05-16
Well, I didn't have any luck.  It seems for kitchensync to work w/ synce, you need syncekonnector.  There is no debian package for it (it's been requested), and I could not get it to compile.

---

### Post by cowabunga on 2005-05-18
[QUOTE=webwalker]So basically, what I'm hearing is that multi-sync / synce is BROKEN for evolution and broken for Ubuntu.

For Pete's sake, I'm willing to PAY someone to make this bloody thing work. I seems like the synce people are spending all of their time trying to make the software work with KDE. Do I need to just give up and change desktops to get one silly application working?

Pardon the rant, I've just been waiting for the last two years for them to get it together on this package. PPC is now outpacing Palm sales almost 2:1; how long is it going to be before the Microsoft press notices that "Linux can't Sync" and points out the fitful progress of hardware integration. I know MSFT isn't making this easier, but the community has attacked bigger problems than this and licked it. What is so tough about syncing a silly PDA?

RMW[/QUOTE]
 I fully subscribe to this comment. I have a Dell Axim device and spent several hours last night trying to make it talk to my Evolution (on Fedora Core 3) calendar and tasks. 
I went through the step-by-step guides in the synce web page, and everything seemed to work well: I could see the Axim, and move files from and to it using the Synce tools (pstatus, pcp, pls...). However, when I then tried multisync for syncing with evolution, the result was quite discouraging: the first time i tried to sync, the calendar in the Pocket PC got plenty of entries from my Evolution calendar... but all of them duplicated! I tried to clean the mess and re-try a sencond sync, but from then on nothing happens... it seems that now Multisync has decided that there is nothing to syncronise anymore. Bad luck.
I am also willing to pay some software that makes my evolution (or any organizer that runs on linux) syncronise tasks and calendar with a PocketPC. I wonder if the Novell guys are selling something like this?
Why is it so difficult to use linux on the desktop? Is discouraging for us working everyday with hundreds of linux boxes offering high level services, that we can not use the same OS in our laptops  for the everyday work...

---

### Post by leviathon on 2005-05-18
I've had marginal success with synce and my toshiba 755. I have managed to sync using the same steps as posted in the how to, although it is **very** quirky. Appointments created on the ppc show up 4 hours early in evo, tasks marked as complete in evo do not reflect the change on the ppc, etc. Contacts seem to work ok. It is definately a kludgy solution. I would also be willing to donate to a bounty to get solid gui based ppc synchronization in  ubuntu.

---

### Post by Heliix on 2005-05-28
hello,
I followed your advices step by step but without success.
when I performed sudo synce-serial-config ttyUSB0
there was the first error: cannot find a character device ttyUSB0
(but previously was my cradle detected at  ttyUSB0!). so I read synce-serial-config --help and tried replacing ttyUSB0 with tty0. so far, OK, waiting for connect.
then i run synce-pstatus and there was a second error:
unable to initialize RAPI: unsuspected failure
rapi_context_connect: DCCM PID entry not found
well, I have no idea what to do.

previously, I tried to connect my palm with pilot-link, but also unsuccessfully- I just followed the advices I found on web, try to modify it when it didn't work, read the help... 
I have Palm Zire 71 and the newest version of Ubuntu 

I would appreciate any help
Heliix

---

### Post by timczer on 2005-05-28
I am at the same place as helix.  I get to the partnership step and I get  the following:
tim@ubuntu:~$ synce-matchmaker create INDEX
[synce_info_new:31] unable to open file: /home/tim/.synce/active_connection
[rapi_context_connect:88] Failed to get connection info
[main:23] Failed to initialize RAPI
 I am not sure where to go next.  Any help would be appreciated.

---

### Post by Heliix on 2005-06-05
:smile: 
just synchronized my palm!
look at 
[http://www.ubuntulinux.org/wiki/PalmZire31HOWTO](http://www.ubuntulinux.org/wiki/PalmZire31HOWTO)
if you have another palm than Zire 31, there is a list of vendor/product IDs on
[http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
instead of gnome-evolution I used system>preferences>palm OS devices (from the main Ubuntu menu). 
maybe you'll need first to reboot+ in bios allow USB devices (or sth like that, i don t remember the exact name...)
well, then i pressed the hotsync button and it works
 \\:D/ 
hope it helps you as well
heliix (with double i; not "helix")

---

### Post by maltje on 2005-06-10
root@amilo:/home/maltje # sudo synce-serial-start
/usr/sbin/pppd: In file /etc/ppp/peers/synce-device: unrecognized option '/dev/ttyUSB0'

synce-serial-start was unable to start the PPP daemon!


this error I get

---

### Post by maltje on 2005-06-10
the second time I tried it,I have to use ttyUSB1!!!!!!!!!!!!!!!
He has tried connecting but I got an error
Cannot start communication with the desktop computer,reconnect your device
this is the error I get on my Ipaq

---

### Post by maltje on 2005-06-10
Now I want to put some mp3's on my usbstick,and now the computer is doing this very slowly!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Before trying to fix the ipaq I had no problems with the usbstick!!!!!!!
Help me please

---

### Post by maltje on 2005-06-10
After a restart from ubuntu the problem with usbstick is ok.
Now my IPAQ!!!!

How can I start over again?
I would like to clear everything and try again.

---

### Post by roboguy on 2005-06-12
If your running gnome and you want some nice graphical tools head over to this site [http://sourceforge.net/project/showfiles.php?group_id=30550&package_id=92164](http://sourceforge.net/project/showfiles.php?group_id=30550&package_id=92164) and download the source for gnome-vfs software-manager and the trayicon. You should be able to build these from source without a problem, although you may need to install a couple of the *-dev packages such as synce-dev to get the appropriate header files installed. 

NOTE: amd64 guys will need to edit the make file to get the gnome-vfs software to build. You will need to remove the -Werror flag otherwise a couple of pointer size warnings will cause the build to fail

Now you have all that installed you need to do a couple more steps to get hotplugging and file browsing working.

Follow the directions on this page [http://sourceforge.net/tracker/?func=detail&atid=399601&aid=1204938&group_id=30550](http://sourceforge.net/tracker/?func=detail&atid=399601&aid=1204938&group_id=30550) to get hotplugging working. Then you won't have to do "sudo synce-serial-start" manually anymore!

Then do ```
sudo cp /usr/etc/gnome-vfs-2.0/modules/synce-module.conf /etc/gnome-vfs-2.0/modules/
``` to get gnome-vfs for synce working.

Now if you plug you pocketpc into it's cradle and start the trayicon ```
synce-trayicon
``` you should see a nice little pocketpc icon appear in your gnome tray. Right click it and you can browse your devices file system, install programs etc.

HTH,
Roboguy

---

### Post by maltje on 2005-06-14
I'm not understanding a lot of it:
I download gnome vfs,software manager and trayicon
Then i did tar xzvf synce-gnomevfs-0.9.0.tar.gz
 and a lot happend,just at the end I got an error
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

What now?

---

### Post by mxsteini on 2005-06-17
Hello to all,
does anyone had the follwing problems and solved them?
1. sync ppc->evolution calendar doesn't work
2. sync evolution->ppc doesn't work at all

Maybe point 1. is a mis-setting in my system. I'm new to ppc.

Greetings and special thanx to **tUrtleAE86** for starting this thread

mxsteini

---

### Post by webwalker on 2005-06-27
Argh. So exactly how does one go about rattling the tin cup to encourage someone to fix this? Or should I just give up at go back to a piece of paper and pencil?

---

### Post by Magneto on 2005-06-29
so what can you sync with an IPAQ? mail, tasks, calendar ?
seems like some people can sync some things but not all

if I cant sync appts, email and contacts then its worthless to me- i had to migrate back to outlook just to do this not fun with alot of contacts

---

### Post by timczer on 2005-06-30
I am still looking for help with the "can't initialize RAPI" error I mentioned earlier in this thread.  I tried running this in another linux distro (Mepis) and got to the same point with the same error.  What do I need to do now?  (I would like to get this working as it is pretty much the only reason I keep my XP OS loaded, so I can sync my PDA).

---

### Post by roboguy on 2005-06-30
[QUOTE=Magneto]so what can you sync with an IPAQ? mail, tasks, calendar ?
seems like some people can sync some things but not all

if I cant sync appts, email and contacts then its worthless to me- i had to migrate back to outlook just to do this not fun with alot of contacts[/QUOTE]


With multisync you can sync your appointments, tasks, and contacts, but no email at the moment. This may or may not be a problem dependant on what type of email you have. I.e if you use IMAP then you don't have a problem anyway...

HTH,
Roboguy

---

### Post by Magneto on 2005-07-02
[QUOTE=roboguy]With multisync you can sync your appointments, tasks, and contacts, but no email at the moment. This may or may not be a problem dependant on what type of email you have. I.e if you use IMAP then you don't have a problem anyway...

HTH,
Roboguy[/QUOTE]
 thanks roboguy- is there an imap app or something?

---

### Post by roboguy on 2005-07-03
[QUOTE=Magneto]thanks roboguy- is there an imap app or something?[/QUOTE]

The mail application on your pocketpc will let you set up an IMAP account. It just depends if your mail provider lets you work that way. Gmail for example is POP3 only.

HTH,
Roboguy

---

### Post by roboguy on 2005-07-03
[QUOTE=timczer]I am at the same place as helix.  I get to the partnership step and I get  the following:
tim@ubuntu:~$ synce-matchmaker create INDEX
[synce_info_new:31] unable to open file: /home/tim/.synce/active_connection
[rapi_context_connect:88] Failed to get connection info
[main:23] Failed to initialize RAPI
 I am not sure where to go next.  Any help would be appreciated.[/QUOTE]
 
If your problem is the same as Helix's then it looks like you don't have dccm running. DCCM is (if I recall correctly) the application that synce uses to establish a serial connnection between your pocketpc and the desktop. If this is not running, there is essentially no connection and you won't be able to make a partnership.

Read this page for more info:
[http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php) 

I think you are up to point 5. 

HTH,
Roboguy

---

### Post by lorenzo on 2005-07-13
Hi,
I succeded in synchronizing my ipaq with evolution......once per reboot....

Ok, If I boot my Ubuntu. I connect my iPaq and follow the steps dccm+synce-serial-start+multisync: Perfect.

IF I disconnect my iPaq and plug it again: no way!!!! I can't use synce anymore.

I think the problem is in usb, since with dmesg y get:

usb 2-1: PocketPC PDA converter now attached to ttyUSB0
usb 2-1: USB disconnect, address 80
ipaq 2-1:1.0: device disconnected
usb 2-1: new full speed USB device using uhci_hcd and address 81
ipaq 2-1:1.0: PocketPC PDA converter detected
usb 2-1: PocketPC PDA converter now attached to ttyUSB1
usb 2-1: USB disconnect, address 81
PocketPC PDA ttyUSB1: PocketPC PDA converter now disconnected from ttyUSB1
ipaq 2-1:1.0: device disconnected
usb 2-1: new full speed USB device using uhci_hcd and address 82
ipaq 2-1:1.0: PocketPC PDA converter detected
usb 2-1: PocketPC PDA converter now attached to ttyUSB1
PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
usb 2-1: USB disconnect, address 82
PocketPC PDA ttyUSB1: PocketPC PDA converter now disconnected from ttyUSB1
ipaq 2-1:1.0: device disconnected

and so on about 80 times!!!!!!!!!!

Looks like usb is continuously connected and disconnected... and sometimes switching from usb0 and usb1....

Any suggestion?

Thanks,
Lorenzo

---

### Post by easy_target on 2005-07-13
Hi to all!

I didn't have to download the sources and compile all the gnome-vfs stuff. I just downloaded the i386 rpms from the sourceforge page and alien'd everything. The only adjustment I had to do was to create a link named "libgtop-2.0.so.2" in the /usr/lib directory pointing to  "libgtop-2.0.so.5.0.0" and the tray icon worked like a charm.

By the way does anyone know how to get the hotplug working for Synce or maybe put all the information together to make it work?

Thanks!!!

---

### Post by roboguy on 2005-07-13
[QUOTE=lorenzo]Hi,
I succeded in synchronizing my ipaq with evolution......once per reboot....

Ok, If I boot my Ubuntu. I connect my iPaq and follow the steps dccm+synce-serial-start+multisync: Perfect.

IF I disconnect my iPaq and plug it again: no way!!!! I can't use synce anymore.

I think the problem is in usb, since with dmesg  get:
...
[/QUOTE]

 Not too sure if this is going to help you or not but it may. I set my system up so that the PocketPC connection is created by hotplug each time I plug the device in, and removed when I unplug it. You problem may be that you are not closing the connection. Anyway I followed the directions here [http://synce.sourceforge.net/synce/hotplug.php](http://synce.sourceforge.net/synce/hotplug.php)

My /etc/hotplug/usb/synce looks like this:

```
#!/bin/bash

exec >>/var/log/synce

export time=`date +"%b %d %X"`
export uname=`uname -n`

echo "$time $uname $0: iPAQ added" >> /var/log/synce
synce-serial-abort > /dev/null
(
for x in 'seq 1 20'; do
[-c /dev/ttyUSB0] && break
sleep 1
done
if ![-c /dev/ttyUSB0]; then
echo "$time $uname $0 [$$]: device node /dev/ttyUSB0 not created!"
exit 1
fi
synce-serial-start
)&

cat > $REMOVER <<END
exec >>/var/log/synce
export time=`date +"%b %d %X"`
export uname=`uname -n`
echo "$time $uname $0 [$$]: iPAQ removed"
sleep 15
synce-serial-abort 2>&1
END
chmod +x $REMOVER

```

and my /etc/hotplug/usb/synce.usermap looks like this

```
synce   0x0003  0x0bb4  0x0a06  0x00    0x00    0x00    0x00    0x00    0x00    0x00    0x00    0x00


```

My device is an O2 XdaIIi so if you have one of those the usermap will work for you otherwise you will need to follow the directions on the url I gave you above to use usbview to find out the details for your device.

Cheers,
Roboguy

---

### Post by roboguy on 2005-07-13
[QUOTE=easy_target]
By the way does anyone know how to get the hotplug working for Synce or maybe put all the information together to make it work?
[/QUOTE]

See my last post  ;-) 

Cheers,
Roboguy

---

### Post by jeff on 2005-07-26
This works fine for me.

I have a XDA2 with win2003se (for them who dont know, it is a "smart" phone)

The only issue is the calendar,
the time and date is always off

if i make a calendar event in evolution then sync i have to open the event on the pda then close it again for it to get the correct times.

but syncing an event from my pda to evolution has the same effect but i cant fix it by opening it and closing it..

for anyone interested i have Synce as the first plugin on multisync, and obviously evolution on the second. 

Now i jsut want to work on getting it to work over bluetooth and also getting the internet on my pda.

Thanks

---

### Post by MikeyXX on 2005-07-26
I'm getting this:

mreid@ubuntu:~$ synce-matchmaker create 1
[rra_matchmaker_create_partnership:351] Partnership file not found for ID 5e585e03
[rra_matchmaker_create_partnership:351] Partnership file not found for ID 37334f9e
[rra_matchmaker_create_partnership:380] Partnership not found and there are no empty partner slots on device.
Partnership creation failed. Maybe there is no empty partnership slot?

Does it overright my partnerships? I've previously hooked to two seperate machines so I'd assume the partnership is full, but activesync gives you an option to delete a partnership in Windows.

---

### Post by axman1971 on 2005-08-02
I'm sure I'm missing someting and this is probably a really really dumb question...
I've and Dell axim x5 and after reading this I think I'm ready to try syncing it with Ubuntu...BUT  I'm running off my laptop that has an Ir port... I'm going to take a guess here and say that all the above is for a desk top computer with a wired connecton to the Handheld... right?
So has anyone tried syncing via Ir or should I just not even consider opening this can of worms?

M

---

### Post by tristure on 2005-08-18
Well, if I try dccm / sudo synce-serial-start / multisync, I get the following console output, even after a fresh reboot :

tristan@dhcp-296-4694:~$ multisync
plugin_API_version
short_name
long_name
plugin_init
[plugin_init:915] here
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/tristan/.multisync/3/localsettings
[evo2-sync] DEBUG: end: load_palm_state
[sync_connect:48] ----->
[rapi_context_connect:112] failed to connect to 192.168.131.201
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/tristan/.multisync/4/remotesettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----
sync_disconnect
[evo2-sync] INFORMATION: start: disconnect
[evo2-sync] DEBUG: end: sync_connect
[sync_connect:48] ----->
[rapi_context_connect:112] failed to connect to 192.168.131.201
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
sync_disconnect
[evo2-sync] INFORMATION: start: disconnect
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----


Can't figure out what's going wrong.
Any help on this?

---

### Post by kzinti on 2005-08-20
[QUOTE=MikeyXX]I'm getting this:

mreid@ubuntu:~$ synce-matchmaker create 1
[rra_matchmaker_create_partnership:351] Partnership file not found for ID 5e585e03
[rra_matchmaker_create_partnership:351] Partnership file not found for ID 37334f9e
[rra_matchmaker_create_partnership:380] Partnership not found and there are no empty partner slots on device.
Partnership creation failed. Maybe there is no empty partnership slot?

Does it overright my partnerships? I've previously hooked to two seperate machines so I'd assume the partnership is full, but activesync gives you an option to delete a partnership in Windows.[/QUOTE]

I am having the same problem does anyone know how to fix this?
Thanks

---

### Post by kzinti on 2005-08-21
[QUOTE=kzinti]I am having the same problem does anyone know how to fix this?
Thanks[/QUOTE]

I figured it out it is:
synce-matchmaker replace 1  (or 2)

---

### Post by maltje on 2005-08-30
It won't work here.
the first time I try to connect it connect but it can't synchronize.
The I stop the connection and try to start it again and then I got this error
synce-serial-start was unable to start the PPP daemon!
Please help,it is the only thing that doesn't work here.
I don't won't to go back to Bill's nightmare

---

### Post by taxus on 2005-09-14
After hours of work and lots of sleep lost, I finally managed to make it work.

I have Ubuntu 5.04 (actually, I originally installed Kubuntu but prefered the ubuntu-desktop), and an iPAQ h2210 plugged through a USB hub. I've only had it set up for half an hour, but so far everything seems to synchronize fine with Evolution, both ways. And the appointments show the correct time zone.

So I may keep Linux yet!

I got the source files for the last version of SynCE, 0.9.1 since it was reported in its forum that it might fix the timezone bug, and compiled the binaries from scratch since no packages were available yet (rpm or deb). Had a lot of trouble doing it too: debian installs the binaries elsewhere than the original source and there can be a problem with MultiSync if we don't install the binaries in the same place where the debian packages do. 

Here is what I did. Note that I prefer using Synaptic and Nautilus in superuser mode than apt-get, tar etc. ;)  TrayIcon, the MultiSync plugin and GnomeVFS are only available in versions 0.9.0.

[list=1]
[*]I uninstalled all SynCE packages. I figured this was necessary to avoid conflicts with the debian packages. 
[list][*]libsynce0
[*]libsynce0-dev
[*]synce-dccm
[*]synce-serial
[*]synce-multisync-plugin
[*]librapi2
[*]librapi2-dev
[*]librapi2-tools
[*]librra0
[*]librra0-dev
[*]librra0-tools
[/list]
[*]I [downloaded](http://sourceforge.net/project/showfiles.php?group_id=30550) the "tarballs". For Ubuntu/GNOME you need:
[list][*]synce-0.9.1.tar.gz (contains all SynCE main modules)
[*]synce-multisync_plugin-0.9.0.tar.gz (I know there's a package for it, but you can't install it without installing the 0.9.0 librapi2 and librra0)
[*]synce-trayicon-0.9.0.tar.gz
[*]synce-gnomevfs-0.9.0.tar.gz
[/list]
[*]I compiled! ([compiling instructions](http://synce.sourceforge.net/synce/tarballs.php)) This is a pain because a lot of libraries are needed. Unfortunately I didn't write them down; you'll have to try compiling to see from the error messages which ones you need. You have to at least install automake1.9, make and maybe makedev. DO NOT follow the instructions exactly though. Here is what I did for each module:
[list][*]```
./configure --prefix=/usr --exec-prefix=/usr --with-multisync-include=/usr/include/multisync
```
[*]```
make
```
[*]```
make install
```
[/list]
the prefix options are needed to install the binaries in the same directories as the debian packages; the multisync include might only be useful to the plugin, but it doesn't hurt.
[*]the file tools (from librapi2-tools) don't have the same names: they don't have the synce- prefix (so it's pstatus, pcp, pls, pmkdir, prm, prmdir, pmv, prun)
[*]I haven't fully explored SynCE; I can't browse the PocketPC with the file manager, but I'll try what's written above.
[/list]

Hope this will be useful.

---

### Post by maltje on 2005-09-28
./configure --prefix=/usr --exec-prefix=/usr --with-multisync-include=/usr/include/multisync

sorry but i'm a newbie:what do I need to type?
./configure --/my username --.....????
my username is maltje can you let me see how it works?

---

### Post by chiefofthejojos on 2005-10-13
> ./configure --prefix=/usr --exec-prefix=/usr --with-multisync-include=/usr/include/multisync

I didn't actually run this, but from looking at it I think it should be verbatim.  Just copy and paste it.
OR, just download the rpm files for those package and use those to install instead of compiling.  That's what I did and it's a bit simpler.  For example, to install synce-trayicon (and this is verbatim):
sudo alien synce-trayicon-0.9.0-1.i386.rpm
sudo dpkg -i synce-trayicon_0.9.0-2_i386.deb

---

### Post by hanzj on 2005-10-13
I'm just about to upgrade my ubuntu from Hoary to Breezy. I wonder if snycing my Pocket PC will be easier with the upgrade. I hope so anyway.

---

### Post by gcraenen on 2005-10-13
[QUOTE=hanzj]I'm just about to upgrade my ubuntu from Hoary to Breezy. I wonder if snycing my Pocket PC will be easier with the upgrade. I hope so anyway.[/QUOTE]

No, unfortunately it hasn't improved. I can get my hx 4700 partly synchronised with Evolution. Contacts work fine, Calender doesn't do anything and task are only updated oneway from the pda to Evolution. :( 

For a typical business-user that's not acceptable, so for the real stuff I still use a Windows-system as main OS. For me, there's to much that doesn't work like it should.

---

### Post by GrinRoth on 2005-10-21
Well, I just followed the instructions as was told in the opening post and everything seems to work fine with my Pocket Loox 600!
I'm using Ubuntu Breezy Badger.

Just make sure you select the right calendar and adressbook in MultiSync at Ximian plugin options.

Thanks :D :D

---

### Post by MadPriest on 2005-10-24
**GrinRoth**, does your PocketPC and Evolution have the same times for appointments?
Cause although i have IDT (Israeli Day Time) on the laptop and in Evolution, all appointments are syncing with UTC.

---

### Post by talljimbo on 2005-10-29
Maybe this is a crazy idea, but I was wondering if there might be some correspondence between the people having appointment-time problems and what their hardware clock is set to.  I haven't had any troubles with that, but my hardware clock is set to local (rather non-standard for linux - but what Windows prefers).

So far I've got most things working nicely with Breezy, but I had to hard reset my Axim and erase my old partnerships to make it work.  Still working on the tray icon and gnome-vfs.

One detail I would like to fix, however, is whether you can synchronize multiple evolution calendars - I'm guessing the answer is no, because Pocket Outlook wouldn't be able to distinguish between them - but if anybody knows of a way, I'd love to hear it.

---

### Post by Stormx on 2005-11-01
barney@ubuntu:~$ sudo synce-serial-start
/usr/share/synce/synce-serial-common: line 58: kill: (6640) - No such process

synce-serial-start is now waiting for your device to connect

barney@ubuntu:~$ synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

I get this.

I have a Orange SPV e200... any pointers?

Thanks in advance

---

### Post by schwermie on 2005-11-02
After a lot of troubles and compiling my own kernel ipaq driver etc. i managed to get my pda working with synce. 

When i create a sync pair in multisync: PDA -> Evo, it works fine. 

Now i want to get the appointments created in evo into my pda. When i create a second sync pair (Evo -> PDA), i receive duplicate entries. Please advise.

Thanks, Marco

---

### Post by Stormx on 2005-11-02
**One step closer! I patched the kernal module and now i can connect.... slightly! Look:**

barney@ubuntu:~$ synce-pstatus
Version
=======
Version:    4.20.0 (Unknown)
Platform:   3 (Windows CE)
Details:    ""

System
======
Processor architecture: 5 (ARM)
Processor type:         2577 (StrongARM)
Page size:              0x10000

Power
=====
ACLineStatus: 01 (Online)

Status for main battery
=========================
Flag:          8 (Charging)
LifePercent:   100%
LifeTime:      Unknown
FullLifeTime:  Unknown

Status for backup battery
=========================
Flag:          255 (Unknown)
LifePercent:   Unknown
LifeTime:      Unknown
FullLifeTime:  Unknown

Store
=====
Store size: 31807488 bytes (30 megabytes)
Free space: 18446336 bytes (17 megabytes)

Memory for storage: 819200 bytes (0 megabytes)
Memory for RAM:     18628608 bytes (17 megabytes)

**But Then i try this...**

barney@ubuntu:~$ synce-matchmaker create 1
[rra_matchmaker_create_partnership:351] Partnership file not found for ID 4769328c
Partnership creation succeeded. Using partnership index 2.

**OK, I think this worked. But then multisync finds no new changes?**

**EDIT: OK, it synced =D**

---

### Post by oswald-p on 2005-11-10
I tried to install synce 0.9.1 from sources on an ubuntu Breezy distro as described in this post.
I was able to compile and install all the sources except synce-rra-0.9.1.
The ./configure step was fine but the make step return this error:

patrick@astarte:~/download/synce-0.9.1/synce-rra-0.9.1$ make
make  all-recursive
make[1]: entrant dans le répertoire « /home/patrick/download/synce-0.9.1/synce-rra-0.9.1 »
Making all in lib
make[2]: entrant dans le répertoire « /home/patrick/download/synce-0.9.1/synce-rra-0.9.1/lib »
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -g -Wall -Wsign-compare -Wno-long-long -Werror -ansi -g -O2 -I.. -g -O2 -MT common_handlers.lo -MD -MP -MF ".deps/common_handlers.Tpo" \
  -c -o common_handlers.lo `test -f 'common_handlers.c' || echo './'`common_handlers.c; \
then mv -f ".deps/common_handlers.Tpo" ".deps/common_handlers.Plo"; \
else rm -f ".deps/common_handlers.Tpo"; exit 1; \
fi
gcc -DHAVE_CONFIG_H -I. -I. -I.. -g -Wall -Wsign-compare -Wno-long-long -Werror -ansi -g -O2 -I.. -g -O2 -MT common_handlers.lo -MD -MP -MF .deps/common_handlers.Tpo -c common_handlers.c  -fPIC -DPIC -o .libs/common_handlers.o
cc1: warnings being treated as errors
common_handlers.c: In function 'on_mdir_line_description':
common_handlers.c:206: warning: pointer targets in passing argument 3 of 'parser_add_blob' differ in signedness
make[2]: *** [common_handlers.lo] Erreur 1
make[2]: quittant le répertoire « /home/patrick/download/synce-0.9.1/synce-rra-0.9.1/lib »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/patrick/download/synce-0.9.1/synce-rra-0.9.1 »
make: *** [all] Erreur 2


just to help: "quittant le repertoire" means " leaving directory"
"erreur 2"/"error2";) 

Is there anybody having ideas to solve this problem?

---

### Post by splot on 2005-11-19
[QUOTE=schwermie]After a lot of troubles and compiling my own kernel ipaq driver etc. i managed to get my pda working with synce. 

When i create a sync pair in multisync: PDA -> Evo, it works fine. 

Now i want to get the appointments created in evo into my pda. When i create a second sync pair (Evo -> PDA), i receive duplicate entries. Please advise.

Thanks, Marco[/QUOTE]

Just one sync pair.
Edit it, click Synchronization Options, and click Always have on Both Sides (that's not the exact wording, it's the last one on the list).
Now everything on one should appear on the other. :)

---

### Post by splot on 2005-11-19
**My Own Problems:**

Synce works and multisync doesn't. :/
Or evolution doesn't.
Or something.
Cuz I can connect just great with Synce, can see my files and manipulate stuff at the command line.  But once I fire up Multisync, it says there's no changes, and nothing ever shows up in Evolution, regardless of resyncing and new or old items.

Are there any multisync alternatives?  Is there any other way to back up my pocketPC without copying individual files to my HD?

Is this easier with a PalmOS device?  I'd been considering switching back...

---

### Post by action09 on 2005-11-19
Hi all !

I've got a Dell Axim X30 and it 'll be great to sync it at job and at whome with my computers :)

I connect the base to the pc and ot in /var/log/messages:
Nov 20 02:03:53 localhost kernel: [4464292.968000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Nov 20 02:03:53 localhost kernel: [4464293.077000] ipaq 2-2:1.0: PocketPC PDA converter detected
Nov 20 02:03:53 localhost kernel: [4464293.079000] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
Nov 20 02:03:54 localhost usb.agent[10889]:      ipaq: already loaded


Like said above :)

After doing the Installation of the required packages for SynCE:, i did a :
 "synce-serial-config ttyUSB0"   (or with /dev/ttyUSB0 same error below)

ERROR:

synce-serial-config was unable to find a character device named "ttyUSB0"

Run "synce-serial-config --help" to get help.




   I saw that no entry was found for ttyUSB0 in  /dev/  ....
so do i need to create it  ?

Any clue please :)

T.I.A

Regards

---

### Post by splot on 2005-11-20
[QUOTE=action09]
ERROR:

synce-serial-config was unable to find a character device named "ttyUSB0"

Run "synce-serial-config --help" to get help.
[/QUOTE]

Is your pocketpc in the cradle and turned on?
Did you start dccm first?
And create the partnership as directed at the beginning of this thread?
(In that order?)

---

### Post by action09 on 2005-11-20
>Is your pocketpc in the cradle and turned on?
Yes

>Did you start dccm first?
No. ON the post i follow the order:

1) Connect your Pocket PC and type "dmesg"  --> OK i see

2) Optionally, you can use "cat /proc/bus/usb/devices" to check for a USB device -->  OK

3) sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial --> OK
DUring the config i hit enter because the parameters are the same as described in the post.

4) Perform the following the following command to tell SynCE where to look. This seems redundant, but doesn't hurt.
" sudo synce-serial-config ttyUSB0" --> NOK

But i continued to see if something happen:

5) i did:  "dccm" --> OK

6) i did a "sudo synce-serial-start" and see something on the pocketpc quickly: " ..user authenticated..." but can't see all. so the communication is good i think ?

on the PC isee: 
" Warning!  You have firewall rules that may prevent SynCE from working properly!
synce-serial-start is now waiting for your device to connect"

So i searched for tcp ports used by Activesync or SynCE and found:
dccm            5679/tcp   Direct Cable Connect Manager
rrac              5678/tcp   Remote Replication Agent Connection


I decided to open these ports on my PC firewall, killed activesync on my pocketpc which isn't responding and restart all.

So i did again 5) - 6) 
On 6) i can't see this time the quick message "..user authenticated..."


After doing a ' synce-pstatus' give:
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred




> And create the partnership as directed at the beginning of this thread?
   (In that order?)
Yes i tried but got an error, something went wrong above .


I'm trying to FIND !

Thanks for your answer i'll post it my other questions..

Now i can't have the pocketpc in the dmesg or tail -f /var/log/messages :(

So i'm going to search :)

Thanks anyway :)

---

### Post by rune on 2005-11-25
[QUOTE=splot]**My Own Problems:**

Synce works and multisync doesn't. :/
Or evolution doesn't.
Or something.
Cuz I can connect just great with Synce, can see my files and manipulate stuff at the command line.  But once I fire up Multisync, it says there's no changes, and nothing ever shows up in Evolution, regardless of resyncing and new or old items.

[/QUOTE]

I've had the trouble with appointments not showing up on the PDA. Those have been solved in my setup (Breezy, HP 1710) with Synce 0.9.1.

Instead of compiling synce and all yourself, add the debian unstable repository and install libraa0 librra0-tools synce-dccm synce-multisync-plugin and synce-serial from Debian unstable.

That is follow the first post howto, but before anything else, add the debian repository.

SynCE Setup and Configuration
0) Add debian unstable repository, either in Synaptic: Settings > Repositories > Add > Type: Binary - URL: [http://ftp.dk.debian.org/debian/](http://ftp.dk.debian.org/debian/) - Distribution: unstable - Sections: main

You can change the "dk" to in the url to your local country.

1) Install the required packages for SynCE:

```

sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial

```

1.5) Remove the unstable repository

Follow the Howto from here.

---

### Post by rune on 2005-11-26
I'm succesfully using the following hotplug script that fixes the following problem I've encountered:

1) Waits until (forever=problem) dccm is startet, especially usefull with KDE and Gnome trayicon that starts dccm.
2) A good log format to /var/log/synce (some problems still with a non running dccm.
3) Autoconfigs USB, doesn't matter what ttyUSB1-9 ipaq connects to.
4) Just works for me.

The script should be placed instead of /etc/hotplug/usb/ipaq
I renamed ipaq to ipaq2 and called my /etc/hotplug/usb/synce and made a symlink from /etc/hotplug/usb/ipaq > /etc/hotplug/usb/synce

```

sudo mv /etc/hotplug/usb/ipaq /etc/hotplug/usb/ipaq2
sudo gedit /etc/hotplug/usb/synce
sudo ln -s /etc/hotplug/usb/synce /etc/hotplug/usb/ipaq

```

```
 
#!/bin/bash

# This is a strongly modified hotplug script for ipaq and synce on Linux. 
# It relies on the original hotplug script that came with synce 0.90 and
# some alterations to that found on the synce sourgeforge mailist
# If you have found any improvements please mail me at 
# rune@maagensen.com - TIA Rune Maagensen
# Of cause you may do what you want with this script, copy, modify, 
# use, distribute, whatever.
 
# Put everything in one function to make load in background
# If not the hotplug init process will stall waiting for dccm to 
# get running, but dccm will most likely be loaded after X has loaded
# and either the KDE or Gnome trayicon has loaded.

function all {

# Variables
export LOG=/var/log/synce
export time=`date +"%b %d %X"`
export uname=`uname -n`
export logmes=$time connect

# Get correct ttyUSB at once, so that other messages don't clog up dmesg.
tty=`dmesg|tail|tac|grep -m1 ": PocketPC PDA converter now attached to"|awk '{ print $NF }'`
if [ "x$tty" = "x" ]
    then
    echo $logmes No tty detected, using ttyUSB0 >> $LOG
    tty=ttyUSB0
fi
count=0
echo -n "$logmes DCCM check..." >> $LOG
while ! (pgrep dccm >> $LOG || let "$count>11")
  do   echo "$logmes No DCCM running waiting 10 seconds, count is $count" >> $LOG
  sleep 10
  count=$[$count+1]
done

#Use the correct ttyUSB by changing it with sed.
sed -i s/"ttyUSB[0123]"/"$tty"/ /etc/ppp/peers/synce-device
echo -n "$logmes $0: iPAQ added at $tty" >> $LOG
echo -n -e "\n$logmes ">>$LOG
/usr/bin/synce-serial-abort |tr -d "\n" >> $LOG
echo -n -e "\n$logmes ">> $LOG

# My prior Hoary setup needed little delay before connect 
#(sleep 3 && /usr/bin/synce-serial-start) |tr -d "\n">> $LOG &

/usr/bin/synce-serial-start |tr -d "\n">> $LOG &

cat <<EOF> $REMOVER
echo >> $LOG
export time=\`date +"%b %d %X"\`
export uname=\`uname -n\`
export logmes=\$time REMOVAL
echo -n "\$logmes $0: iPAQ removed" >> $LOG
kill \`head -n 1 /var/run/ppp-synce-device.pid\`
sleep 3
echo -n -e "\\\n\$logmes " >> $LOG
/usr/bin/synce-serial-abort |tr -d "\\n">> $LOG
echo >> $LOG
rmmod ipaq >> $LOG
EOF
chmod +x $REMOVER
}


# Now run the big function in background and carry on 
all &

```

Gnome integration:
I've succesfully gotten synce-gnomevfs and synce-trayicon installed.
I grabbed the rpms from the sourgeforge page [http://sourceforge.net/project/showfiles.php?group_id=30550&package_id=92164](http://sourceforge.net/project/showfiles.php?group_id=30550&package_id=92164), and installed them with alien nad made a symlink to libgtop

1) grab the rpms from the sourceforge page: synce-gnomevfs and synce-trayicon
2) install the packages with alien, you might have to install alien first ```
 apt-get install alien 
``` or with synaptic.
either
```

alien synce-gnomevfsxx.rpm
dpkg -i synce-gnomevfs_xx.deb
alien synce-trayicon-xx.rpm
dpkg -i synce-trayicon_xx.deb

```
or this should work too
```

alien -i synce-gnomevfsxx.rpm
alien -i synce-trayicon-xx.rpm

```

3) Attach pda and see if the following command works:
```

synce-in-computer-folder install
synce-in-computer-folder connect

```
it should give you a Places > Mobile device option

4) Then try:
```

synce-trayicon

```

if you get a libgtop error try the following
```

sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2

```
the first libgtop-2.0 should be on your system, the second is the one trayicon might complain about

---

### Post by jrattner on 2005-12-01
I currently have a pocket PC and have followed this tutorial to set it up.  Its connected and pstatus shows alot of information.  Is it easier to SYNC this pocket pc with evolution or Kontact or whatever?  What is the simpliest and easiet way to do this?

---

### Post by ubuntuthinking on 2005-12-02
OK I'm not a bash programmer of any sort - but this mostly works for me:

Using gedit created a file called "sync"

It contains:

sudo synce-serial-start
dccm
synce-matchmaker INDEX
multisync

Save normally and chmod to make it executable.

Ruinning in a terminal window or dbblclick, put in the root password and I'm up on Multisync. 

Synchronization tests on my machine seem to show no problems - adding items on the PC and on the PPC work as best as I can tell.

I don't remember what the command is but Ill have to look it up regarding how to kill off the script and/or keep the connection persistent when I'm through syncing.

SOMEONE WHO KNOWS WHAT THEIR DOING WITH BASH - PLEASE UPDATE CHANGE ETC.

Good Luck!!   p.s. I'm on Breezy:razz:

---

### Post by ubuntuthinking on 2005-12-09
Spoke too soon - a couple of days of use has shown many problems:

- pda/evo changes on either side are erratic, not always showing up
- i have changed the sync pair in multisync to no avail
- i have re-created the matchmaker index, no luck
- i have re-installed it all and still no luck.

as mentioned above, this is critical to business users and i may have to return to the beast (M$) once again :(

---

### Post by foxiness on 2005-12-19
first thank you and it look it work on synce-pstatus 

but i have problem it use the same ppp my modem use ppp0 how can i change this to let the pocket pc use ppp1 or so

thank you for nice how to

---

### Post by foxiness on 2005-12-20
now i do full sync , but i find two thing

1- must unload or stop /etc/ini.d/sl-modem-daemon stop
2- show resync from options like one here on this topic said

---

### Post by rune on 2005-12-20
[QUOTE=ubuntuthinking]OK I'm not a bash programmer of any sort - but this mostly works for me:

Using gedit created a file called "sync"

It contains:

sudo synce-serial-start
dccm
synce-matchmaker INDEX
multisync

Save normally and chmod to make it executable.

Ruinning in a terminal window or dbblclick, put in the root password and I'm up on Multisync. 

Synchronization tests on my machine seem to show no problems - adding items on the PC and on the PPC work as best as I can tell.

I don't remember what the command is but Ill have to look it up regarding how to kill off the script and/or keep the connection persistent when I'm through syncing.

SOMEONE WHO KNOWS WHAT THEIR DOING WITH BASH - PLEASE UPDATE CHANGE ETC.

Good Luck!!   p.s. I'm on Breezy:razz:[/QUOTE]

Did you follow only the initial howto, or did you apply my modifications? I'm plugging  and unplugging my pda daily and it just works.

There are problems with the breezy versions of synce, but either the debian unstable deb's or the aliened rpm's are quite good.

---

### Post by foxiness on 2005-12-22
rune , thank you :) , how can i write about my feel $%$#$ 

it work with me, and the problem of sl-modem-daemon ,it will not need any more to do stop - start ,but i need to get the dail-up deactive.

---

### Post by MHD on 2006-01-04
[QUOTE=lynng]Well, you don't necessarily have to switch to KDE completely.  You could apt-get only kontact.  The KDE libraries would have to be installed.  I have thought about trying this myself to see if the kitchensync app is any better at getting the correct times/dates of appointments.  I've already got synce working, so it *should* be trivial to test it w/ kontact/korganizer.  I will try it over the weekend and post results.[/QUOTE]

But how do you get Kitchensync working without syncekonnector??? and if you have syncekonnector how did you get it?

---

### Post by André on 2006-01-15
@action09: It's been quite some time since you post about your Axim X30. Did you finally get it to sync??

I am thinking about buying this one but syncing is somehow essential for me so i am really looking forward for your experience with it.

Greetings
André

---

### Post by action09 on 2006-01-15
Not at the moment  :(  I MUST fo it too.. i think it's a default coming from me.. because i here people doing it well...
If these people can paste infos here... it'd be great :)

---

### Post by André on 2006-01-15
Do you mean people get the Axim X30 to work?? ... i would be sold :-)

Or do you mean syncing PDAs in general like with this howto?

Greetings
André

P.S.: I hope you meant the first so i can put this nice one on my list :-)

---

### Post by LandyMan on 2006-02-08
[quote=lorenzo]
usb 2-1: USB disconnect, address 82
PocketPC PDA ttyUSB1: PocketPC PDA converter now disconnected from ttyUSB1
ipaq 2-1:1.0: device disconnected

and so on about 80 times!!!!!!!!!!

Looks like usb is continuously connected and disconnected... and sometimes switching from usb0 and usb1....

Any suggestion?

Thanks,
Lorenzo[/quote]
Lorenzo, I see this is quite some time ago, and I don't know if you got it sorted, but this will hopefully help for the other people with the same problem.

I had the same issues as described above. Going home last night, I started thinking about the whole IP setup for synce. If I leave my Wireless connection enabled on the iPAQ, it receives an IP from the office DHCP, which in my mind will conflict with the setup for synce. So I disabled the wireless unit on my iPAQ (hx4700 btw), and what do you know, it works! \\:D/

Hope this helps someone!

---

### Post by peter rus on 2006-02-09
alright, since no one on the dutch forums was able to help me i am here just like " maltje" to solve my pocketpc problem. i got a Cassiopeia em-500 (casio). i am gonna write every step of the tutorial i take down here so someone correct me if i am wrong ok?

well there we go O.o :

first i removed all that was left from my previous attempts, at least, i hope its all gone: 

sudo apt-get remove librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial

1) Connect your Pocket PC and type "dmesg" in a shell to see if the ipaq kernel module is loaded. The output might look like the following. Take note of the tty used for the connection.

output: 
> 
A ttyUSB0: ipaq_read_bulk_callback - length = 26, data = 7e ff 7d 23 c0 21 7d 2a 7d 24 7d 20 7d 28 7d 20 7d 20 7d 20 7d 20 7d 3d 8b 7e
[4300891.829000] drivers/usb/serial/usb-serial.c: serial_write - port 0, 15 byte(s)
[4300891.829000] drivers/usb/serial/ipaq.c: ipaq_write - port 0
[4300891.829000] PocketPC PDA ttyUSB0: ipaq_write_bulk - length = 15, data = 7e c0 21 09 05 00 08 eb 20 cc ec 7d 5d 15 7e
[4300891.830000] drivers/usb/serial/ipaq.c: ipaq_write_bulk_callback - port 0
[4300891.830000] drivers/usb/serial/usb-serial.c: usb_serial_port_softint - port 0
[4300891.831000] drivers/usb/serial/ipaq.c: ipaq_read_bulk_callback - port 0
[4300891.831000] PocketPC PDA ttyUSB0: ipaq_read_bulk_callback - length = 26, data = 7e ff 7d 23 c0 21 7d 2a 7d 25 7d 20 7d 28 7d 20 7d 20 7d 20 7d 20 c8 7d 34 7e
[4300921.834000] drivers/usb/serial/usb-serial.c: serial_write - port 0, 14 byte(s)
[4300921.834000] drivers/usb/serial/ipaq.c: ipaq_write - port 0
[4300921.834000] PocketPC PDA ttyUSB0: ipaq_write_bulk - length = 14, data = 7e c0 21 09 06 00 08 eb 20 cc ec 13 bd 7e
[4300921.835000] drivers/usb/serial/ipaq.c: ipaq_write_bulk_callback - port 0
[4300921.835000] drivers/usb/serial/usb-serial.c: usb_serial_port_softint - port 0
[4300921.836000] drivers/usb/serial/ipaq.c: ipaq_read_bulk_callback - port 0
[4300921.836000] PocketPC PDA ttyUSB0: ipaq_read_bulk_callback - length = 25, data = 7e ff 7d 23 c0 21 7d 2a 7d 26 7d 20 7d 28 7d 20 7d 20 7d 20 7d 20 a6 bc 7e
[4300935.943000] Unknown OutputIN= OUT=ppp0 SRC=192.168.131.102 DST=192.168.131.201 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=28188 DF PROTO=TCP SPT=5679 DPT=1049 WINDOW=5840 RES=0x00 ACK PSH FIN URGP=0
[4300936.042000] drivers/usb/serial/ipaq.c: ipaq_read_bulk_callback - port 0
[4300936.042000] PocketPC PDA ttyUSB0: ipaq_read_bulk_callback - length = 17, data = 7e ff 7d 23 c0 21 7d 25 7d 21 7d 20 7d 24 3d c7 7e
[4300936.047000] drivers/usb/serial/usb-serial.c: serial_write - port 0, 17 byte(s)
[4300936.047000] drivers/usb/serial/ipaq.c: ipaq_write - port 0
[4300936.047000] PocketPC PDA ttyUSB0: ipaq_write_bulk - length = 17, data = 7e ff 7d 23 c0 21 7d 26 7d 21 7d 20 7d 24 f0 e2 7e
[4300936.047000] drivers/usb/serial/ipaq.c: ipaq_write_bulk_callback - port 0
[4300936.047000] drivers/usb/serial/usb-serial.c: usb_serial_port_softint - port 0
[4300936.278000] drivers/usb/serial/ipaq.c: ipaq_read_bulk_callback - port 0
[4300936.278000] drivers/usb/serial/ipaq.c: ipaq_read_bulk_callback - nonzero read bulk status received: -84
[4300936.412000] usb 1-2: USB disconnect, address 10
[4300936.412000] drivers/usb/serial/usb-serial.c: usb_serial_disconnect
[4300936.412000] ipaq 1-2:1.0: device disconnected
[4300936.422000] drivers/usb/serial/usb-serial.c: serial_close - port 0
[4300936.422000] drivers/usb/serial/ipaq.c: ipaq_close - port 0
[4300936.422000] drivers/usb/serial/usb-serial.c: destroy_serial - PocketPC PDA
[4300936.422000] drivers/usb/serial/ipaq.c: ipaq_shutdown
[4300936.422000] drivers/usb/serial/usb-serial.c: return_serial
[4300936.428000] PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[4300936.432000] drivers/usb/serial/usb-serial.c: port_release - ttyUSB0
[4300937.223000] usb 1-2: new full speed USB device using uhci_hcd and address 11
[4300937.307000] drivers/usb/serial/usb-serial.c: descriptor matches
[4300937.307000] drivers/usb/serial/usb-serial.c: found bulk in on endpoint 0
[4300937.307000] drivers/usb/serial/usb-serial.c: found bulk out on endpoint 1
[4300937.307000] drivers/usb/serial/usb-serial.c: found interrupt in on endpoint 2
[4300937.307000] ipaq 1-2:1.0: PocketPC PDA converter detected
[4300937.307000] drivers/usb/serial/usb-serial.c: get_free_serial 1
[4300937.307000] drivers/usb/serial/usb-serial.c: get_free_serial - minor base = 0
[4300937.307000] drivers/usb/serial/usb-serial.c: usb_serial_probe - setting up 1 port structures for this device
[4300937.307000] drivers/usb/serial/usb-serial.c: the device claims to support interrupt in transfers, but read_int_callback is not defined
[4300937.307000] drivers/usb/serial/ipaq.c: ipaq_startup
[4300937.308000] drivers/usb/serial/usb-serial.c: usb_serial_probe - registering ttyUSB0
[4300937.317000] usb 1-2: PocketPC PDA converter now attached to ttyUSB0
[4301107.837000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4301107.882000] ISO 9660 Extensions: RRIP_1991A
[4301919.238000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4301919.239000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4301979.250000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4301979.251000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302039.262000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302039.263000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302039.454000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302040.528000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302040.528000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302040.528000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302040.528000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302040.528000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302040.528000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302079.365000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302079.579000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302079.579000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302079.579000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302079.579000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302079.579000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302079.579000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4302099.275000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302099.275000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302159.286000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302159.287000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302219.298000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302219.299000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302279.311000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302279.312000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302339.323000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302339.324000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302399.335000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302399.336000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302459.347000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302459.348000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302519.361000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302519.361000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302579.372000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302579.373000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302639.384000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302639.385000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302699.397000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302699.397000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302759.408000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302759.409000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302819.420000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302819.421000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302879.432000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302879.433000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302939.444000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302939.445000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302999.456000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4302999.457000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303059.468000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303059.470000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303119.481000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303119.482000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303179.494000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303179.494000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303239.505000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303239.506000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303299.517000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303299.518000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303359.529000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303359.530000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.101 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109
[4303453.409000] usb 1-2: USB disconnect, address 11
[4303453.409000] drivers/usb/serial/usb-serial.c: usb_serial_disconnect
[4303453.409000] drivers/usb/serial/usb-serial.c: destroy_serial - PocketPC PDA
[4303453.409000] drivers/usb/serial/ipaq.c: ipaq_shutdown
[4303453.409000] drivers/usb/serial/usb-serial.c: return_serial
[4303453.439000] PocketPC PDA ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[4303453.444000] drivers/usb/serial/usb-serial.c: port_release - ttyUSB0
[4303453.444000] ipaq 1-2:1.0: device disconnected
[4303456.223000] usb 1-2: new full speed USB device using uhci_hcd and address 12
[4303456.311000] drivers/usb/serial/usb-serial.c: descriptor matches
[4303456.311000] drivers/usb/serial/usb-serial.c: found bulk in on endpoint 0
[4303456.311000] drivers/usb/serial/usb-serial.c: found bulk out on endpoint 1
[4303456.311000] drivers/usb/serial/usb-serial.c: found interrupt in on endpoint 2
[4303456.311000] ipaq 1-2:1.0: PocketPC PDA converter detected
[4303456.311000] drivers/usb/serial/usb-serial.c: get_free_serial 1
[4303456.311000] drivers/usb/serial/usb-serial.c: get_free_serial - minor base = 0
[4303456.311000] drivers/usb/serial/usb-serial.c: usb_serial_probe - setting up 1 port structures for this device
[4303456.311000] drivers/usb/serial/usb-serial.c: the device claims to support interrupt in transfers, but read_int_callback is not defined
[4303456.311000] drivers/usb/serial/ipaq.c: ipaq_startup
[4303456.312000] drivers/usb/serial/usb-serial.c: usb_serial_probe - registering ttyUSB0
[4303456.318000] usb 1-2: PocketPC PDA converter now attached to ttyUSB0


2) Optionally, you can use "cat /proc/bus/usb/devices" to check for a USB device that's using the ipaq kernel module.
output:
> 
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 12 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=07cf ProdID=2002 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=1ms


1) Install the required packages for SynCE:

done that, but here comes the trouble, there should be a setup be invoked, well, that doesn't happen. watch:
> 
bla bla bla...
Selecteren van voorheen niet geselecteerd pakket synce-serial.
Uitpakken van synce-serial (uit .../synce-serial_0.9.0+cvs051204-2_i386.deb) ...Instellen van libsynce0 (0.9.0-3) ...

Instellen van librapi2 (0.9.1-2ubuntu1) ...

Instellen van librapi2-tools (0.9.1-2ubuntu1) ...
Instellen van librra0 (0.9.0-2) ...

Instellen van librra0-tools (0.9.0-2) ...
Instellen van synce-dccm (0.9.0-1) ...
Instellen van synce-multisync-plugin (0.9.0-3) ...
Instellen van synce-serial (0.9.0+cvs051204-2) ...

peterrus@RUSMAIN:~$


well, its in dutch, but as you can see, there is no setup where i can config any ip adresses.  so i think ik have to solve this first! someone can help me?

---

### Post by tyr1973 on 2006-02-18
I am one of the AMD64 guys, and I have looked through my Makefile and can't work out which part of it I have to modify in order to get rid of the -Werror?

cheers
andreas

---

### Post by roboguy on 2006-02-18
Hi tyr1973,

If you are trying to build synce-gnome-vfs and are following my instructions then the files you want to modify are in the src subdirectory. They are the Makefile.am and Makefile.in files. Remove the -Werror from both of these files and rerun ./configure. Once you have done this it should build ok.

HTH,
Roboguy

---

### Post by blue cube on 2006-03-13
i seem to be able to connect just fine with ActiveSync

but after a little while, I get the error msg on my phone screen that reads:

> ERROR: Cannot connect to PC due to an unexpected error in Winsock services.

is this a firewall problem?

---

### Post by kseise on 2006-04-05
How about this oddball problem, I can browse the entire contents of the PocketPC (Dell Axim X5) using a file manager but multisync with the plugin doesn't transport anything to Evolution.  Anyone have suggestions for this?

---

### Post by Shanachie on 2006-06-03
[QUOTE=lorenzo]Hi,
I succeded in synchronizing my ipaq with evolution......once per reboot....

Ok, If I boot my Ubuntu. I connect my iPaq and follow the steps dccm+synce-serial-start+multisync: Perfect.

IF I disconnect my iPaq and plug it again: no way!!!! I can't use synce anymore.

I think the problem is in usb, since with dmesg y get:

usb 2-1: PocketPC PDA converter now attached to ttyUSB0
usb 2-1: USB disconnect, address 80
ipaq 2-1:1.0: device disconnected
usb 2-1: new full speed USB device using uhci_hcd and address 81
ipaq 2-1:1.0: PocketPC PDA converter detected
usb 2-1: PocketPC PDA converter now attached to ttyUSB1
usb 2-1: USB disconnect, address 81
PocketPC PDA ttyUSB1: PocketPC PDA converter now disconnected from ttyUSB1
ipaq 2-1:1.0: device disconnected
//SNIP//
Any suggestion?

Thanks,
Lorenzo[/QUOTE]

I had a similar problem as you Lorenzo, I tried changing the connection in the ActiveSync settings. The device stayed connected but the PPP connection failed.

The answer seems to be doing `sudo synce-serial-start` the exact moment the the "connecting..." window is shown on the PDA (there is no manual connect that I'm aware off).

Use the udev rule and script in this thread for automaticly running synce-serial-start when connecting the device: [http://ubuntuforums.org/showthread.php?t=149183](http://ubuntuforums.org/showthread.php?t=149183)

---

### Post by dilidon on 2006-06-10
Hi,
Just wanted to share, as it might encourage someone, that using that guide from 2005 I finally managed to solve one of the biggest problems keeping me double-booting (I still am, because of a  few other issues, but that sync thing should be the decisive push): I never got my Axim x30 to sync or even communicate with Breezy. With dapper and this guide, following it exactly *step-by-step*, all seems to work so far.:cool:       So, thank you, tUrtleAE86!

However, what I could not get to work was connecting to an exchange server and then marking it local and then trying to sync it to my pda. Had no success, and the exchange plugin crashed most of the time. But well, decided to migrate the data found in my PDA to my local calendar and currently looking for alternative ways for publishing the data somewhere for those times when I wont have my PDA with me (can't run a server in my own pc). Google seems to support only one-way traffick, but the search continues. Any recommendations would of course be highly appreciated.

---

### Post by aky on 2006-06-11
Hi! I have followed the instructions, but i ended up with this error message, in the end. I've copied the last 3 commands i have given.  I saw many people had the same problem, but i could not find the solution.
I use Dapper Drake, and i try to connect a Pocket Loox 720.

Please help. Thanks! 

aky@aky-desktop:~$ sudo synce-serial-config ttyUSB0
Password:

You can now run synce-serial-start to start a serial connection.

aky@aky-desktop:~$ dccm
aky@aky-desktop:~$ sudo synce-serial-start

Warning!

You have firewall rules that may prevent SynCE from working properly!


synce-serial-start is now waiting for your device to connect

aky@aky-desktop:~$ synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

---

### Post by bof on 2006-06-12
I am trying to connect iPAQ 4700 to ubuntu and have followed all the instructions (several times) in this thread. At present I am not bothered about syncing anything, I just want to browse my iPAQ from ubuntu.
One thing I did notice that I was not offered the opportunity to check the following stuff as suggested:-

2) synce-serial setup will be invoked by apt, follow this through using the default settings, unless you have reason to do otherwise.
Code:
/dev/ttyUSB0 local address: 192.168.131.102 remote address: 192.168.131.201 no dns entry needed 


The last entries from my consloe are as follows:
tony@tony-laptop:~$ sudo synce-serial-config ttyUSB0

You can now run synce-serial-start to start a serial connection.

tony@tony-laptop:~$ sudo synce-serial-start

synce-serial-start is now waiting for your device to connect

tony@tony-laptop:~$

Well, the iPAQ is connected , the iPAQ "USB connecting to host" when I plugged it into its cradle. Should I see something in Places?

---

### Post by dilidon on 2006-06-13
[QUOTE=bof]
One thing I did notice that I was not offered the opportunity to check the following stuff as suggested:-
2) synce-serial setup will be invoked by apt, follow this through using the default settings, unless you have reason to do otherwise.
Code: /dev/ttyUSB0 local address: 192.168.131.102 remote address: 192.168.131.201 no dns entry needed [/QUOTE]
I got it all to work, solely based on this guide, wrote a little script to do the connecting, and all I need now is to get the hotplugging function to work (not sure how to accomplish that, as the guidelines do not match the file locations in Dapper, and I don't quite yet feel like becoming creative with these things, as I just got my USB devices to automount in a user writable mode, which surprisingly was not the default in Ubuntu).
Now, I can confirm that I wasn't offered this option either, so I read the manuals for the synce-serial-config command and simply did that manually after the install. I actually kept doing it every time in the beginning, as otherwise it didn't seem to work, but I've stopped that practice as it seemed redundant.
> sudo synce-serial-config ttyUSB0 192.168.131.102:192.168.131.201
So, you can just use the command above and it does the same trick.
Now, below, I think you skipped one step, namely, running dccm.
> The last entries from my consloe are as follows: tony@tony-laptop:~$ sudo synce-serial-config ttyUSB0
You can now run synce-serial-start to start a serial connection.
tony@tony-laptop:~$ sudo synce-serial-start
synce-serial-start is now waiting for your device to connect
You also need to run *dccm -p 1234* (the latter being your password/pin, in case you have one set) or simply *dccm* before the *synce-serial-start* command.
> Well, the iPAQ is connected , the iPAQ "USB connecting to host" when I plugged it into its cradle. Should I see something in Places?

Not sure if that answers your question, but I have the synce-trayicon running, which was also discussed in this thread I think, and I also have an entry under the Places, and one on my desktop, and I didn't do much besides following the guide word by word (and thinking along).
Oh, and I'm using an Axim x30. I still have a few minor problems but I won't throw them all out here right now to keep it shorter.
Maybe that helps a bit...:-$

---

### Post by bof on 2006-06-13
[QUOTE  wrote a little script to do the connecting,[/QUOTE]

Can you tell me how to write a script and perhaps paste your own script in for me to use? 
TIA

---

### Post by kblood on 2006-06-14
Hello,

I am having the same problem with RAPI. I have tried following several guides around this forum, and also in the Wiki. I have also checked the Synce HOWTO, and the only suggestions for solving this are rebooting, unplugging the PDA and plugging it back... I have tried both options several times.

My specs:
Ubuntu Dapper 6.06 (loving it!), Sony Vaio VGN-FS315M laptop.
Acer n10 PDA, Windows Mobile 2003, USB connection. Device gets correctly detected with Ipaq driver.
I am running Firestarter, but I have a rule to allow all connections from 192.168.131.201, in case that could cause a problem.

Does anybody have any other suggestion to solve the RAPI error?
```
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
```

I am going crazy here, banging my head against the wall...
I have even installed Windows 2000 under VMWare, but the connection is very unstable, and I haven't been able to get it to work except for once, and only for a couple of seconds. Suggestions to help me get it running under VMWare would also be welcome, but I would definitely prefer to have it running under Ubuntu natively...

---

### Post by bof on 2006-06-14
[QUOTE=kblood]
I am going crazy here, banging my head against the wall....[/QUOTE]
Me too.
I am really getting to like ubuntu. I have found replacements for MS Word, Excel, Access, Photoshop Elements and may even have found a replacement for Quicken.
I am resigned to sticking with Dreamweaver on XP for my web work but the one thing that is really holding me back now is not being able to link to my iPAQ.
This one item may tip the balance and keep me on Windows. :-x
I have read ALL the posts on this problem except for the one post which will really sort the problem out once and for all- where is it :-(

---

### Post by frank_ on 2006-06-15
hi there,

i still have trouble with syncing in both directions. changes made in evo are synced perfectly, but changes made on my PDA aren't synced at all. i.e. if i delete a contact on my PDA it's not deleted in evo.

as i read some people were able to get around this problem?!

---

### Post by dilidon on 2006-06-15
[QUOTE=bof]Can you tell me how to write a script and perhaps paste your own script in for me to use? 
TIA[/QUOTE]
Hi. Sorry for the late reply. Was busy for a few days. Here's the story. I can't really write any complex scripts but with my limited understanding of linux I simply created *a random* file with the necessary commands inside and made it executable and I access it from a dropdown drawer from my upper desktop panel. This getting connectid via this script is sometimes unsuccessful on my Axim for the reasons I will explain in the end, but that accounts for only some 10% of the cases, and so far, even though my solution is probably somewhat stupid when judged by someone who could actually write a proper hotpluggin script, it works for me. Before I post it, be it noted that someone had written a hotplugger and had kindly posted it here as well (in 2005, I think) but as the directories and files indicated in the directions do not exist in Dapper I have no clue how to change it to make it work. And I don't unfortunately have the time to learn writing a new one right now either.
Here's the deal. I can take no responsibility about the possible side effects, as I have pretty much no clue as to why it works on my case and not in other cases. [-X  But as said earlier, I use the tutorial 1 to 1 and it just worked.:-({|=  
You can run the script by either clicking on the executable file (asks me whether I want to display it in an editor, execute it, or execute it in a terminal). Ecexute it in a terminal. Alternatively, I think you can type *sh your_file* on the command line to achieve the same effect. Or you could add an icon pointing to that file to your panel or smth.
The script I use:
```
sleep 1
echo Enne jätkamist veendu, et PDA on pesasse asetatud.
echo Ootan 5 sekundit...
echo .....
sleep 1
echo ....
sleep 1
echo ...
sleep 1
echo ..
sleep 1
echo .
sleep 1
sudo synce-serial-config ttyUSB0
sleep 1
dccm -p 9483
sleep 1
sudo synce-serial-start
sleep 3
synce-trayicon
sleep 2
echo Ühendus loodud!
sleep 4

```
As you can see, its pretty much all the same commands as in the manual. However, now, the obstacle I was talking about, which makes my efforts fail in some cases, and might, possibly, be connected to your problems as well. If I plug in my Axim earlier and run the script a few seconds too early, or a few seconds too late, without the waiting in the beginning, it won't connect. In my case, I adjusted the countdown seconds as to achieve an optimal result. Why? Well - when I plug in my Axim it keeps trying to connect to the other side but can't unless these commands welcome it or smth. I've seen numerous posts on the web on how people have 80 or so connects and disconnects on the USB port of their PDA, and I think I'm getting a similar effect, so if the commands are sent to the PDA while it is taking a break from trying for a few secons, the effort will be futile. This is all highly non-computer-talk, but in human language, that's how it seems to be.
So, if I run the script, it tells me it's gonna wait for 5 seconds for me to plug the toy in. Then I plug it in. Then it initiates the commands and simultaneously I can see on the sceen of the PDA that if is trying to connect. And in case the "welcoming commands" have been issued at the right moment , the pda tells you it has successfully been authorized and connected. If the commands don't get sent at the right moment, it fails. This *must* sound slightly funny, but honestly, I have no idea how to write a proper script or modify the modules or smth as to stop this connecting/disconnecting pain. I just found a loophole, and thats where I jump through.

In my case, if I see the popup window on my PDA saying trying to connect and the *dccp* command and the s*ynce-serial-start* commands don't get issued before the window dissappears then the connection fails, as explained above. Weird? Yes. Useless? Totally. Annoying? Oh god, yes. Tolerable? So far, yes. But that will be the last thing for some time now on the testing of which I'm willing to spend long night-hours while having to work during the day. But as it works, I'm sticking with Ubuntu.:)
I hope this is of assistance to someone, as the thread itself in general has been. And if someone who can actually write a more intelligent script is reading this, please revise the hotplugger and update it for Dapper, if you can.
A revised hotplugger, which would not depend on the human pressing the button at the right time, would be much appreciated, indeed! :idea:

PS. If I disconnect my PDA as instructed earlier in this thread, I sometimes have to soft-reset my device for it to be able to connect to the PC again.

---

### Post by bof on 2006-06-15
Thanks for taking so much trouble with this. At the very least I have learnt how to write and execute a "script"
I have been trying out your version and making as many modifications as I can think of. It is not working yet - I still end up with that RAPI nonsense.
However I will keep trying - thanks again.

---

### Post by spiral out on 2006-07-08
> **kblood said:**
> Hello,

I am having the same problem with RAPI. I have tried following several guides around this forum, and also in the Wiki. I have also checked the Synce HOWTO, and the only suggestions for solving this are rebooting, unplugging the PDA and plugging it back... I have tried both options several times.

```
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
```

I am going crazy here, banging my head against the wall...


Having also the same problem, searched almost the whole internet ](*,) 

The 'funny' thing about it is that i had it working a couple of times...

Esspeccialy after a hard reset of my PDA (Toshiba E700), but it's not working anymore... :(

[edit]
Ok, i found out that if i turn on my pda (automaticly starts authentication with a "connect to" windows) and i give on that moment the command
```
synce-serial-start
```it connects!

looks like "synce-serial-start" command dies after some secondes??

---

### Post by soapytheclown on 2006-07-30
Hey ive been trying to get my ipaq 4150 to sync with ubuntu but obviously no success :( i looked at the sourceforge page about it, i see that i have to apply a patch but im not entirely sure how im meant to do it, 

can someone give me an idiots guide on how to do this please, as i have no idea what to do.

the link to the page is 

[http://synce.sourceforge.net/synce/usb_linux.php#many](http://synce.sourceforge.net/synce/usb_linux.php#many) 

under the title "Special information for HP iPAQ 5550 owners"

any help will be appreciated

---

### Post by TasKiNG on 2006-08-01
This may help some people who are having problems getting their PPC to connect  when using kubuntu dapper:-

I followed the instructions in the 1st part of this thread then did the following:-

sudo apt-get install synce-kde kcemirror

get the file: **synce-kde_0.9.1-1_i386.deb** i got it from:- [http://packages.debian.org/unstable/utils/synce-kde](http://packages.debian.org/unstable/utils/synce-kde)

install using:  sudo dpkg -i synce-kde_0.9.1-1_i386.deb
this fixes the problem with raki crashing.

reboot 

now run **raki** and issue the command: **sudo synce-serial-start** and you should be able to browse you ppc files and remote view the screen by clicking on the raki symbol on your taskbar and selecting the relevent options.

hope this helps

---

### Post by smtelegadis on 2006-08-06
DUDE YOUR A GEM!  (It connected once on My Loox 720 and never again.)  Once I followed your advice it worked.

THANK YOU!!:razz:

> **spiral out said:**
> Having also the same problem, searched almost the whole internet ](*,) 

The 'funny' thing about it is that i had it working a couple of times...

Esspeccialy after a hard reset of my PDA (Toshiba E700), but it's not working anymore... :(

[edit]
Ok, i found out that if i turn on my pda (automaticly starts authentication with a "connect to" windows) and i give on that moment the command
```
synce-serial-start
```it connects!

looks like "synce-serial-start" command dies after some secondes??

---

### Post by bof on 2006-08-08
> **TasKiNG said:**
> This may help some people who are having problems getting their PPC to connect  when using kubuntu dapper:-

I followed the instructions in the 1st part of this thread then did the following:-

sudo apt-get install synce-kde kcemirror

get the file: **synce-kde_0.9.1-1_i386.deb** i got it from:- [http://packages.debian.org/unstable/utils/synce-kde](http://packages.debian.org/unstable/utils/synce-kde)

install using:  sudo dpkg -i synce-kde_0.9.1-1_i386.deb
this fixes the problem with raki crashing.

reboot 

now run **raki** and issue the command: **sudo synce-serial-start** and you should be able to browse you ppc files and remote view the screen by clicking on the raki symbol on your taskbar and selecting the relevent options.

hope this helps


Well I followed your instructions and downloaded the file, started to install it and then watched in horror as 239 items were removed from my ubuntu :mad: 
I then found that when I turned on my computer it wouldn't boot into anything!. 
Fortunately my data partition is intact and I have now loaded a fresh copy of ubuntu.

Specifically I need to connect my iPAQ hx4700 so I can at least back up the data on it even If I can't synchronise anything. I am considering copying my Pocket Informant and other files to the SD card and then using that to transfer to the laptop. I am also wondering if I can do a bit of file sharing via the wireless network.
Does anyone out there have a strategy for doing this sort of thing?

---

### Post by rlundeen on 2006-08-08
I'm using an Axim X5.  I ran the dmesg and it showed it just like in the directions.  However, when I run "*sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial*" I get an error that it can not find librra0.  What do I do now?

- Robert

---

### Post by Flavian on 2006-08-13
synce-pstatus does not work for me, even though I got it to work at some point in the past.
I managed to establish a connection between my Pocket PC and Synce, but was NOT able to sync!

But now, when I use "synce-pstatus" it gives me the following error message:

```

synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

```

From that on I can not continue!
Can someone help me, please?

Btw: Is there an option to sync my PDA with Thunderbird?
Thanks in advance
Flo

---

### Post by kelleychambers on 2006-08-14
Hey everyone...

This absolutely baffles me.  Why is this so colossally difficult! I mean this technology has been around for years.  Why can't the supposed solutions actually work for all... consistently?  It's crazy.

Anyway, I have a Dell Axim X30 also.  And I followed the inital directions and yes, I'm able to make a connection with Multisync with no problem.  Click on sync... and nothing transfers into Evolution.  Absolutely nothing!  Where in hell is this stuff going?  I look in the logs and everything seems fine... but NOTHING IS IN MY EVO!!!

Damn, this is frustrating.  Can anyone help me NOT pull out my hair?

---

### Post by raven65az on 2006-08-14
umm....no go.  Here is my shell output.
root@raven-laptop:/home/raven# synce-serial-start

Warning!

You have firewall rules that may prevent SynCE from working properly!


Warning!

synce-serial-start cannot find the dccm process.
Without dccm your PPP connection will soon terminate!


synce-serial-start is now waiting for your device to connect

root@raven-laptop:/home/raven# synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

I am running Dapper, and am using an Ipaq 3630

---

### Post by kseise on 2006-08-14
This really is an aweful situation.  I have tried Red Hat, Xandros, Linspire, Ubuntu Warty, SuSE, and Ubuntu Dapper, Synce just does not work.  I am willing to pay for help setting it up.  The problem is that the $250.00 support plan from Canonical seems a little steep for a single problem.  Is there another support option available?

---

### Post by igsimon on 2006-08-26
I am trying to sync a pocket pc and evolution. I have used the guides here to get sync to connect to pocket pc, pstatus works, multisync using sync and backup lets me backup the pocket pc to a folder. sync to evolution does not work! i tried multisync and backup and all i get is a blank file. any ideas what may be wrong or not configured correctly? this is on latest dapper drake with all updates.:confused:

---

### Post by kseise on 2006-08-29
OK, I got it working.  Everything works fine except for Avantgo, I just don't have the time at the moment to follow the tutorial to change the iptables settings, but it looks pretty simple.

From the synCE sourceforge page, I got tripped up on the following section
> **The Driver entry**

Second you look at the Driver entry. Read more in the apropriate section below.

    [COLOR="Red"]Driver=ipaq or Driver=usbserial Your kernel driver recognized your device, good![/COLOR]

    Driver=(none) Your kernel driver did not recognize your device. You need to perform some special configuration:

       1.

          Only if your Linux kernel is 2.6.10 or later: please send a mail to [email]synce-devel@lists.sourceforge.net[/email] and tell us...
             1. your kernel version
             2. brand and model of your device
             3. vendor/product USB IDs for your device (see Vendor= and ProdID=)
       2.

          Follow the instructions in Appendix A to add options like this, but replace the red digits with the corresponding ones from the output from the command you ran earlier:

              vendor=0x049f product=0x0003

       3.

          If you have the file /etc/rc.local, open it with a text editor and add this line in order to have things working directly next time you restart your computer:

              /sbin/modprobe ipaq

       4.

          Now run these commands to reload the ipaq module:

              rmmod ipaq
              modprobe ipaq

I misunderstood the red section (it is not highlighted on their page) and it really confused me ](*,) 

After re-reading it a few times, I realized that you do NOT need to configure the vendor and product settings if the driver is showing Driver=ipaq.

I undid the changes that followed for setting the vendor ID etc. and re-tried the setup.

I ran synce-kde and got a message that dccm was already running.  I killed all dccm and vdccm and then went on with their instructions.  It failed to work.

I then changed over to gnome and ran the connection process from the command line and it worked like a charm :cool: 

Big thumbs up and thank you to the SynCE team for a great feature,=D>  but a little thumbs down for the slightly confusing setup tutorial:idea: .  I recommend highlighting the fact that if the driver is detected correctly, the rest of the steps in that section should be skipped.

I really hope this post helps somebody.  This had been driving me nuts.\\:D/

---

### Post by chellie on 2006-09-03
hi
Completely new to linux trying to "synce" with ipaq 3950. I think my problem is IP adresses I need to set the local one as I am on a domain How do I do step 2 in SynCE Setup and Configuration? what does apt mean? Thanks

---

### Post by chellie on 2006-09-04
hi again so new not posted before still learning found aload more messages no help.
running latest ubuntu trying to sync ipaq3950 
followed all the steps until. tried changing ip address 
 run synce-pstatus  error:
unable to initialize RAPI: unsuspected failure
complete newby any help welcome

Ta l8r

---

### Post by chellie on 2006-09-04
hi again progress!! do  sudo synce-serial-start just after put in cradle get a connection for a second then it drops well will try another night feel as tho made progress complete newby now knows about terminal and synce!!

---

### Post by chellie on 2006-09-04
hi again YEAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH  changed ip adress in IPAQ 192.168.131.201   manually .  any this might help someone else. Now have it connected everything else can wait good night!

---

### Post by funchords on 2006-09-07
> **kelleychambers said:**
> Click on sync... and nothing transfers into Evolution.  Absolutely nothing!  Where in hell is this stuff going?  I look in the logs and everything seems fine... but NOTHING IS IN MY EVO!!!

I ran into this too.

Edit your Multisync pair, and of the Evolution side, choose options.  You'll see that by default, the options are not to sync anything: Calendar, Contacts, nor Tasks.  Turn on the choices you want to sync.

---

### Post by kseise on 2006-09-07
> **funchords said:**
> I ran into this too.

Edit your Multisync pair, and of the Evolution side, choose options.  You'll see that by default, the options are not to sync anything: Calendar, Contacts, nor Tasks.  Turn on the choices you want to sync.

No just that, but I think you have to tell it to sync with your "Personal" calendar etc.  I don't know if that is true for everyone, but Mine appeared to be syncing, but not with my personal calendar.  Since I ONLY have a personal calendar on this machine, I don't know where else it could have been trying to sync.

---

### Post by bof on 2006-09-09
> **chellie said:**
> hi again YEAHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH  changed ip adress in IPAQ 192.168.131.201   manually .  any this might help someone else. Now have it connected everything else can wait good night!

I,ve been trying for a long time to connect my iPAQ hx4700 to Ubuntu and came up with all the problems ever listed on these forums.

Can you write a step-by-step guide as to how you managed to get your device connected?

---

### Post by balki2005 on 2006-09-09
hello when  i follow  youre  howto i recieve this as output:

jonay@thunderdragon:~$ "multisync"
[plugin_init:915] here
plugin_API_version
short_name
long_name
plugin_init
object_types
plugin_info
[sync_connect:48] ----->
[synce_info_from_file:51] unable to open file: /home/jonay/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/jonay/.multisync/1/remotesettings
[evo2-sync] WARNING: File /home/jonay/.multisync/1/remotesettings does not exist
[evo2-sync] DEBUG: end: sync_connect
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----
sync_disconnect
[evo2-sync] INFORMATION: start: disconnect
object_types
object_types
plugin_info
[sync_connect:48] ----->
[synce_info_from_file:51] unable to open file: /home/jonay/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/jonay/.multisync/1/remotesettings
[evo2-sync] WARNING: File /home/jonay/.multisync/1/remotesettings does not exist
[evo2-sync] DEBUG: end: sync_connect
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----
sync_disconnect
[evo2-sync] INFORMATION: start: disconnect

did I something  wrong  ?

who  can help  me  ?

kind regards,

balki2005

---

### Post by k_smolka on 2006-09-12
> **timczer said:**
> I am still looking for help with the "can't initialize RAPI" error I mentioned earlier in this thread.  I tried running this in another linux distro (Mepis) and got to the same point with the same error.  What do I need to do now?  (I would like to get this working as it is pretty much the only reason I keep my XP OS loaded, so I can sync my PDA).


Did you ever manage to fix this problem i am running a dell axim x50 and i am getting the same error. 

Regards

Karl

---

### Post by Georges on 2006-09-13
Here is my script. It uses Xdialog (sudo apt-get install xdialog)
Usage: plug in ipaq, start the script.
If it ends with OK, all fine, if not, start script again.
If still error: unplug ipaq. WAIT a minute, then start again.
(the waining is what makes the RAPI error go away, don't ask, it must be a microsoft thing)

The script may not be usable for people using dialup as there is a kill -9 pppd somewhere in the script...

I made a button on my gnome panel to start the script.

This does nothing for evolution etc, it's only for creating a working synce connection.

```

#!/bin/bash
echo=myecho
String="test"
function myecho()
{
  echo XXX
  String="$String
$1"
echo "$String" > /tmp/ppc
  echo "$1"
  echo XXX
}
if [ 1 -eq 1 ]
then
(for i in 2 5 7 9 12 15; do echo $i; sleep 1;done;killall -9 synce-pstatus) &
synce-pstatus >/dev/null
ret=$?
kill -9 $!
if [ $ret -eq 0 ]
then
  $echo "The connection is already established"
  echo 50
  sleep 1
  echo 100
  sleep 1
  rm /tmp/ppc
  exit
fi
if ps -edf|grep -q ppp[d]
then
  $echo "killing old connection"
  echo 1
  sudo killall -9 pppd
fi
$echo "gathering device"
echo 20
dev=$(dmesg | tail |awk '/PocketPC PDA converter now attached/ {print $NF}'|tail -1)
echo 25
$echo "setting device: $dev"
r=$(sudo synce-serial-config $dev)
ret=$?
$echo "$r"
if [ $ret -ne 0 ]
then
  $echo "problem starting, you should wait 10s before starting"
  exit
fi
echo 30
$echo "device is set."
killall -9 dccm
if ! ps -edf|grep -q [d]ccm
then
  echo 40
  $echo "no dccm, starting it"
  dccm &
  echo 50
  $echo "done"
fi
echo 60
killall -9 synce-pstatus
if ! ps -edf|grep -q [s]ynce
then
  $echo "no connection, starting one"
  r=$(sudo synce-serial-start)
  ret=$?
  $echo "$r"
  $echo "ret=$ret"
  echo 70
  $echo "done"
fi
echo 80
$echo "starting activesync on pocket PC..."
wait=10
while [ $wait -gt 0 ]
do
  synce-pstatus >/dev/null
  if [ $? -eq 0 ]
  then
    break
  fi
  wait=$((wait-1))
  sleep 1
  echo $((100-$wait*2))
done
if [ $wait -le 0 ]
then
  $echo "cannot start activesync, connection problem."
  echo "cannot connect" >&2
else
  rm /tmp/ppc
  echo "connect OK" >&2
fi
echo 100
sleep 1
fi | Xdialog --allow-close --title "Pocket PC connection" --gauge "connecting to pocket PC" 6 80
if [ -f /tmp/ppc ]
then
  String=$(cat /tmp/ppc)
  rm /tmp/ppc
  echo "$String"
  Xdialog --title "ERROR" --left --msgbox "$String" 0 0
else
  Xdialog --title "Success" --msgbox "DONE, happy syncing" 0 0
fi


```

---

### Post by bof on 2006-09-13
Thanks for trying, Georges, but it didn't work for me. I think I followed your instructions accurately. (as an aside, how do you put a button on the Gnome panel to run the script?)
Here is what I'm getting:-

synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
/home/tony/connect_iPAQ: line 95: 14925 Killed                  ( for i in 2 5 7 9 12 15;
do
    echo $i; sleep 1;
done; killall -9 synce-pstatus )
synce-pstatus: no process killed
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
cannot connect
test
gathering device
setting device: ttyUSB0

You can now run synce-serial-start to start a serial connection.
device is set.
no dccm, starting it
done
starting activesync on pocket PC...
cannot start activesync, connection problem.

---

### Post by sv8bur on 2006-09-15
> **tUrtleAE86 said:**
> At first glance, [SynCE](http://synce.sf.net)  and [Multisync](http://multisync.sf.net)  can seem a bit daunting. But, it really is not nearly as bad as it seems. I got a little help from this [thread](http://www.ubuntuforums.org/showthread.php?t=24805&highlight=ipaq+evolution)  as well.

This HOWTO is based on syncing my Dell Axim X3i with Evolution, but it should carry over to IPAQs and other Pocket PCs.

**[SIZE=3]Does Linux like your PDA?[/SIZE]**

1) Connect your Pocket PC and type "dmesg" in a shell to see if the ipaq kernel module is loaded. The output might look like the following. Take note of the tty used for the connection.
```
usb 4-2: new full speed USB device using uhci_hcd and address 3
ipaq 4-2:1.0: PocketPC PDA converter detected
usb 4-2: PocketPC PDA converter now attached to ttyUSB0
```
2) Optionally, you can use "cat /proc/bus/usb/devices" to check for a USB device that's using the ipaq kernel module.
```
T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=413c ProdID=4002 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

**[SIZE=3]SynCE Setup and Configuration[/SIZE]**

1) Install the required packages for SynCE:
```
sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
```
2) synce-serial setup will be invoked by apt, follow this through using the default settings, unless you have reason to do otherwise. 
```
/dev/ttyUSB0
local address: 192.168.131.102
remote address: 192.168.131.201
no dns entry needed
```
3) Perform the following the following command to tell SynCE where to look. This seems redundant, but doesn't hurt.
```
sudo synce-serial-config ttyUSB0
```
4) Start the SynCE connection daemon by typing "dccm" in a shell. Use "dccm -p password" if your Pocket PC is password protected.
5) Initiate a serial connection by typing "sudo synce-serial-start" in a shell. You should be greeted with "synce-serial-start is now waiting for your device to connect".
6) "synce-pstatus" shows a LOT of information about your Pocket PC, such as current mode of operation, battery charge level, memory usage as well as backup battery status. If you want to see some other synce commands, type "dpkg -L librapi2-tools". You can use these commands to do things such as installing Pocket PC programs, etc.
7) Create the partnership between the Pocket PC and your computer. There are 2 slots on the device, so the INDEX can be 1 or 2.
```
synce-matchmaker create INDEX
```
You should be greeted with:
```
Partnership creation succeeded. Using partnership index INDEX.
```

**[SIZE=3]Multisync Setup and Configuration[/SIZE]**

1) Install the required packages for Multisync:
```
sudo apt-get install libmultisync-plugin-all multisync
```
Or, alternatively if you want to skimp on the packages:
```
sudo apt-get install libmultisync-plugin-evolution libmultisync-plugin-backup multisync
```
2) Start Multisync by typing "multisync" in a shell. You can also do via Applications > Accessories > Multisync, but the shell gives you a lot of feedback which can be helpful the first time you use it.
3) Create a new synchronization pair where one of the plugins is "SynCE Plugin" and the other is "Ximian Evolution 2", the order doesn't matter. You may need to create a new Contact List, Task List and Calendar, so that the default ones aren't used. I'm not sure if this is needed, but it was mentioned in the other thread.
4) Press the "Sync" button.
Initially, I had no entries in Evolution so for some reason, I had to modify all of the entries on my Pocket PC so that the timestamp would register each entry as a 'change', otherwise no entries were sync'd. There must be a simple workaround for this, but I'm not sure at this time.

**[SIZE=3]Disconnecting Your Pocket PC[/SIZE]**

1) Shutdown Multisync
2) "killall -HUP dccm" to kill the serial connection.
3) AS A LAST RESORT, run "synce-serial-abort", if the above command doesn't work.

Please let me know if you have any problems or suggestions.

Have fun!  :)

I have done all this but after giving the command "synce-pstatus" I am getting the following message "synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred" what this means
Thank you

---

### Post by Old Pink on 2006-09-24
All is good until I enter > synce-matchmaker create INDEX 

Then I'm told there's a RAPI error.

---

### Post by dave37 on 2006-10-03
I'm getting the same error:

root@davepc:/home/dave# synce-matchmaker create INDEX
[synce_info_from_file:51] unable to open file: /root/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[main:62] Failed to initialize RAPI
root@davepc:/home/dave#

---

### Post by teejcee on 2006-10-03
> **Matt.H said:**
> 

Then I'm told there's a RAPI error.


Try this...

synce-matchmaker status

This should return details of which system/s your device is matched with.

If the system you're trying to sync with isn't there...

synce-matchmaker replace INDEX    where INDEX is generally either 1 or 2

Now disconnect your device & delete your .synce directory - rename it if you're not comfortable with deleting it.

I would now re-boot your system just to make sure everything is re-set.

Plug your device back in and go from there.

dave37 - this may help you too but I'm a bit puzzled as to why you're doing this as root.   The .synce dir should be in the user's home dir.

---

### Post by dave37 on 2006-10-04
I uninstalled everything then started again as normal user, ran the script and here is the output:

dave@davepc:~$ #!/bin/bash
dave@davepc:~$ echo=myecho
dave@davepc:~$ String="test"
dave@davepc:~$ function myecho()
> {
>   echo XXX
>   String="$String
> $1"
> echo "$String" > /tmp/ppc
>   echo "$1"
>   echo XXX
> }
dave@davepc:~$ if [ 1 -eq 1 ]
> then
> (for i in 2 5 7 9 12 15; do echo $i; sleep 1;done;killall -9 synce-pstatus) &
> synce-pstatus >/dev/null
> ret=$?
> kill -9 $!
> if [ $ret -eq 0 ]
> then
>   $echo "The connection is already established"
>   echo 50
>   sleep 1
>   echo 100
>   sleep 1
>   rm /tmp/ppc
>   exit
> fi
> if ps -edf|grep -q ppp[d]
> then
>   $echo "killing old connection"
>   echo 1
>   sudo killall -9 pppd
> fi
> $echo "gathering device"
> echo 20
> dev=$(dmesg | tail |awk '/PocketPC PDA converter now attached/ {print $NF}'|tail -1)
> echo 25
> $echo "setting device: $dev"
> r=$(sudo synce-serial-config $dev)
> ret=$?
> $echo "$r"
> if [ $ret -ne 0 ]
> then
>   $echo "problem starting, you should wait 10s before starting"
>   exit
> fi
> echo 30
> $echo "device is set."
> killall -9 dccm
> if ! ps -edf|grep -q [d]ccm
> then
>   echo 40
>   $echo "no dccm, starting it"
>   dccm &
>   echo 50
>   $echo "done"
> fi
> echo 60
> killall -9 synce-pstatus
> if ! ps -edf|grep -q [s]ynce
> then
>   $echo "no connection, starting one"
>   r=$(sudo synce-serial-start)
>   ret=$?
>   $echo "$r"
>   $echo "ret=$ret"
>   echo 70
>   $echo "done"
> fi
> echo 80
> $echo "starting activesync on pocket PC..."
> wait=10
> while [ $wait -gt 0 ]
> do
>   synce-pstatus >/dev/null
>   if [ $? -eq 0 ]
>   then
>     break
>   fi
>   wait=$((wait-1))
>   sleep 1
>   echo $((100-$wait*2))
> done
> if [ $wait -le 0 ]
> then
>   $echo "cannot start activesync, connection problem."
>   echo "cannot connect" >&2
> else
>   rm /tmp/ppc
>   echo "connect OK" >&2
> fi
> echo 100
> sleep 1
> fi | Xdialog --allow-close --title "Pocket PC connection" --gauge "connecting to pocket PC" 6 80
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: no process killed
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
cannot connect
dave@davepc:~$ if [ -f /tmp/ppc ]
> then
>   String=$(cat /tmp/ppc)
>   rm /tmp/ppc
>   echo "$String"
>   Xdialog --title "ERROR" --left --msgbox "$String" 0 0
> else
>   Xdialog --title "Success" --msgbox "DONE, happy syncing" 0 0
> fi
test
gathering device
setting device: ttyUSB0

You can now run synce-serial-start to start a serial connection.
device is set.
no dccm, starting it
done
no connection, starting one

synce-serial-start is now waiting for your device to connect
ret=0
done
starting activesync on pocket PC...
cannot start activesync, connection problem.
dave@davepc:~$

Thanks for your help!

---

### Post by teejcee on 2006-10-05
> **dave37 said:**
> I uninstalled everything then started again as normal user, ran the script and here is the output:.........
Thanks for your help!

Looking at your profile, you're running Dapper.  If you've been following only the steps for Hoary, chances are it won't work.

There are many threads relating to this subject and unfortunately all the info you need to get this going is spread across the threads/posts for different platforms.

I've had it in mind to put together a how-to but I'm a bit handicapped with a bunged-up wrist at the moment so even this short amount of typing is a chore.

For the time being...hang in there.

---

### Post by dave37 on 2006-10-07
Thanks very much for your help, by finding info across other posts, I managed to get a Mobile Device icon, using dmesg it shows the unit connected, but I still get the rapi error, or if I click on the mobile device icon, i get :

Could not open location 'synce:///'

Details: Unknown error code: 30

Please drop me a note if you put together a howto

Thanks!

---

### Post by dave37 on 2006-10-07
OK, got it working, how I don't really know.  If i issue the command synce-serial-start as soon as the handheld shows the popup for connecting to network, it connects and I can explore and sync multisync.  But it doesn't hotplug detect it, or if I don't issue the command while the connecting popup is up on the handheld it won't connect.  Better than nothing, but hotplug or connecting more easily would be nice.

---

### Post by bof on 2006-10-07
> **dave37 said:**
> OK, got it working, how I don't really know.

Well if you find out, can you let me know please? :-?

---

### Post by dave37 on 2006-10-07
I followed the HOWTO instructions, in my case I think it's just that I have to issue synce-serial-start when the handheld is placed in the cradle and shows the "connecting to network" popup for a few seconds.  Try it, maybe it'll work

---

### Post by dave37 on 2006-10-08
After a system reboot it's no longer working, if I issue synce-serial-start when the "connecting to network" popup is up on the handheld, it connects for a moment, then the handheld displays "cannot start communications with the desktop computer.  Reconnect your device. If the problem persists see Microsoft ActiveSync Help".

Ooops. was forgetting to start DCCM before issuing synce-serial-start, working now.

---

### Post by bof on 2006-10-08
Lucky you :) 
Can you remind me what handheld you are using?
I'm not sure exactly what script you ended up with. Can you post it again please as the last time I ran the original script it wrecked my installation.

---

### Post by dave37 on 2006-10-08
I'm using a Dell axim x50 (wm2003se)  I installed the following packages here [http://ubuntuforums.org/showthread.php?t=30936](http://ubuntuforums.org/showthread.php?t=30936)

Then started dccm by typing dccm in terminal window, then synce-serial-start as soon as the popup for the "connecting to network" came up on the handheld and voila

---

### Post by bof on 2006-10-08
Well what do you know?
I reinstalled again as you suggested (most files already present but a few new ones were added) and hit the enter button to run Synce just as the handheld dropped into its cradle and presto, I've got a connection.
synce-pls lists the files on the iPAQ and I'm sitting here not daring to switch it off in case it never starts again ](*,) 

I don't seem to have any icon showing in my gnome tray and I can't seem to find the ipaq in Nautillus. Should I be able to see my iPAQ files in a GUI or is it just a terminal job?

---

### Post by teejcee on 2006-10-09
> **dave37 said:**
> OK, got it working, how I don't really know. .........  Better than nothing, but hotplug or connecting more easily would be nice.

Ahaaa - nice to see you've done some leg work for yourself and found some of the bits & pieces - good work, you're getting closer.

Take a look at this thread...

[http://ubuntuforums.org/showthread.php?t=149183](http://ubuntuforums.org/showthread.php?t=149183)

rune lists two scripts.  I've had success with the second one....the one following his statement...
"OR my modified script that waits for dccm to start with X"

---

### Post by bof on 2006-10-09
> **dave37 said:**
> 
Then started dccm by typing dccm in terminal window, then synce-serial-start as soon as the popup for the "connecting to network" came up on the handheld and voila

I have found that you have to enter sudo synce-serial-start as soon as the popup starts. If you're using sudo for the first time  then by the time you've entered your password it's too late and you get the dreaded RAPI error. Unplug and repeat and it seems to work ok.

Now then, typing Multisync gets the Multisync to start and I even get the tray icon now though nothing wants to synchronise yet - more research needed :( 

But first of all I'd like to browse my iPAQ. I don't have anything showing in my Places list. Can someone shed some light on this for me?

---

### Post by dave37 on 2006-10-10
Teejcee, I tried both scripts, no connection.  The only way I get a connection is if I issue synce-serial-start as soon as the "connecting to network" popup appears on the handheld.

Thanks!

---

### Post by IvanB on 2006-10-11
dear friend,I am instaling a ipaq 1940. i follow this guide complete and all seem good, but when i write 
synce-serial-matchmaker command, doesn't works. 
this error message
[synce_info_from_file:51] unable to open file: /root/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[main:62] Failed to initialize RAPI

pstatus this error:
 Unable to initialize RAPI: An unspecified failure has occurred

could you help me.

Ivan 

Sorry for my bad english

---

### Post by kseise on 2006-10-11
> **IvanB said:**
> dear friend,I am instaling a ipaq 1940. i follow this guide complete and all seem good, but when i write 
synce-serial-matchmaker command, doesn't works. 
this error message
[synce_info_from_file:51] unable to open file: /root/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[main:62] Failed to initialize RAPI

pstatus this error:
 Unable to initialize RAPI: An unspecified failure has occurred

could you help me.

Ivan 

Sorry for my bad english


Try running synce-serial-matchmaker as yourself, not as root (do not use sudo).  That should work.  Let us know how you make out.

---

### Post by blakegrover on 2006-10-13
Just so everyone knows in Edgy Eft you can get this working.  I followed the instructions on the first page.  I have made my own little script and it is working with my ipaq 6315 but I'm not sure if it would work for others.  Its not very complicated but I'm sure it doesn't work everytime

```
#/bin/bash

killall -HUP dccm
dccm -p 5373
sleep 2
gksu synce-serial-start
sleep 2
#synce-pstatus
multisync &

```


Someone asked how someone could browse the device through a gui interface and I would like to know also.  

Thanks
Blake

---

### Post by harryharry on 2006-10-17
@blake

try this, works for me (ubuntu dapper)
supposing you have synce installed and working.

download; [http://prdownloads.sourceforge.net/synce/synce-gnomevfs-0.9.0-1.i386.rpm?download](http://prdownloads.sourceforge.net/synce/synce-gnomevfs-0.9.0-1.i386.rpm?download)

sudo apt-get install alien
sudo alien -i synce-gnomevfs-0.9.0-1.i386.rpm

synce-in-computer-folder install
synce-in-computer-folder connect

And it will appear in your filebrowser.

---

### Post by harryharry on 2006-10-17
and for all those that get that d*rn:
Unable to initialize RAPI: An unspecified failure has occurred 
message:

Try this:

in terminal:
# lsusb

this must give a line about your pocketpc like this:

Bus 002 Device 013: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC

type:

# sudo gedit /etc/modprobe.d/synce

and paste this in there: (read the codes form ID above for your device)
(not the << and >>)
>>>
options ipaq vendor=03f0 product=1016
<<<

Save

Reconnect the pocketpc

type:

# dccm
# sudo synce-serial-config ttyUSB0
# sudo synce-serial-start

Test connection:
# synce-pstatus

if it works:

# sudo gedit /etc/udev/rules.d/10-ipaq.rules
and paste this:

>>>
# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
LABEL="synce_rules_end"
<<<<
Save

Restart device:

# sudo /etc/init.d/udev restart

connecten the thing:
# synce-matchmaker

And now my pocketpc is talking to multisync, it sees the changes on the fly when i change something in my pocketpc. (start multisync from console to read the messages)
Still nothing happens in Evolution :( , but still figuring that out.

Anyone?

---

### Post by GooglieS on 2006-10-20
Thank you! The main part of your message is 

[i]>>>
# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
LABEL="synce_rules_end"
<<<<[/i]


And i think that the bold text is unnecessary

[I]Test connection:
# synce-pstatus

**if it works:**

# sudo gedit /etc/udev/rules.d/10-ipaq.rules
and paste this:[/I]

---

### Post by cime on 2006-10-20
I have done everything the tutorial on first page says. When i run "sudo synce-serial-start" my iPaq connects (it's shows the dialog on ipaq that it's connecting and that the user is authenticated) to Ubuntu (edgy) but after few seconds the icon showing that the ipaq (right-bottom of the screen on ipaq) is syncronized with pc dissappears. What's wrong?

---

### Post by jogogets on 2006-10-21
I get the following message when I type:

synce-matchmaker create INDEX

I get: 

[rapi_context_connect:97] Failed to get connection info
[main:62] Failed to initialize RAPI

Any ideas what step I've missed?

---

### Post by jogogets on 2006-10-21
I am attemptint to sync a ipaq pocket pc to ubuntu 2.6.15.27.368. I have followed the suggestions in SynCE webpage. I have this problem:

synce-serial-start was unable to find the file /etc/ppp/peers/synce-device:

Please run the synce-serial-config tool to create this file before running this
script again.


Then I type:

synce-serial-config 

and I get this:

Syntax for synce-serial-config:

  synce-serial-config serial-device [local-ip-address:remote-ip_address [DNS-server-name]]

  The serial-device specifies the name of your serial port device.

  These are the port names on Linux:

    ttyS0  The first serial port
    ttyS1  The second serial port
    ...

  You can also connect via an infrared connection (IrDA). This requires
  that you already have irattach running.

    ircomm0  The first IrDA communication port

  Please send corrections and updates to the above information to the
  SynCE development mailing list: [email]synce-devel@lists.sourceforge.net[/email]

  If you do not provide the local_ip_address:remote_ip_address parameter,
  synce-serial-config will use 192.168.131.102:192.168.131.201.

  If you want to specify these addresses yourself, you may want to read
  about the same option on the man page for pppd.


Any suggestions where I go from here?

---

### Post by Voyageur on 2006-10-26
Here we go

kingy@SagraT23:/usr/src$ ls -l
total 8
drwxr-xr-x 19 root root 4096 2006-10-26 23:05 linux-headers-2.6.15-27
drwxr-xr-x  4 root root 4096 2006-10-26 23:05 linux-headers-2.6.15-27-686

---

### Post by pmilin@ptt.yu on 2006-10-29
First, I have managed to synce my iPAQ1940 with Dapper, having some problems with RAPI-failure, but solved them. Later, I did bluetooth, and everything is working perfectly, but lost synce-serial commands. Does anyone knows why? Is it the case that you cannot use both of them: USB and bluetooth?

Sincerely,
Petar Milin

---

### Post by kseise on 2006-10-31
I have found that Firestarter does not open the correct ports for some reason. When Firestarter is running, I get the RAPI errors that everyone seems to complain about. By clicking "Stop Firewall", the ports get opened up and all syncing is possible. 

If it helps anybody, try turning off the firewall to get Synce to connect.

If anyone can tell me how to correctly open the ports with Firestarter, I would really appreciate it.

---

### Post by Jorge Alfaiate on 2006-12-15
> **tUrtleAE86 said:**
> At first glance, [SynCE](http://synce.sf.net)  and [Multisync](http://multisync.sf.net)  can seem a bit daunting. But, it really is not nearly as bad as it seems. I got a little help from this [thread](http://www.ubuntuforums.org/showthread.php?t=24805&highlight=ipaq+evolution)  as well.

This HOWTO is based on syncing my Dell Axim X3i with Evolution, but it should carry over to IPAQs and other Pocket PCs.

**[SIZE=3]Does Linux like your PDA?[/SIZE]**

1) Connect your Pocket PC and type "dmesg" in a shell to see if the ipaq kernel module is loaded. The output might look like the following. Take note of the tty used for the connection.
```
usb 4-2: new full speed USB device using uhci_hcd and address 3
ipaq 4-2:1.0: PocketPC PDA converter detected
usb 4-2: PocketPC PDA converter now attached to ttyUSB0
```
2) Optionally, you can use "cat /proc/bus/usb/devices" to check for a USB device that's using the ipaq kernel module.
```
T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=413c ProdID=4002 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

**[SIZE=3]SynCE Setup and Configuration[/SIZE]**

1) Install the required packages for SynCE:
```
sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
```
2) synce-serial setup will be invoked by apt, follow this through using the default settings, unless you have reason to do otherwise. 
```
/dev/ttyUSB0
local address: 192.168.131.102
remote address: 192.168.131.201
no dns entry needed
```
3) Perform the following the following command to tell SynCE where to look. This seems redundant, but doesn't hurt.
```
sudo synce-serial-config ttyUSB0
```
4) Start the SynCE connection daemon by typing "dccm" in a shell. Use "dccm -p password" if your Pocket PC is password protected.
5) Initiate a serial connection by typing "sudo synce-serial-start" in a shell. You should be greeted with "synce-serial-start is now waiting for your device to connect".
6) "synce-pstatus" shows a LOT of information about your Pocket PC, such as current mode of operation, battery charge level, memory usage as well as backup battery status. If you want to see some other synce commands, type "dpkg -L librapi2-tools". You can use these commands to do things such as installing Pocket PC programs, etc.
7) Create the partnership between the Pocket PC and your computer. There are 2 slots on the device, so the INDEX can be 1 or 2.
```
synce-matchmaker create INDEX
```
You should be greeted with:
```
Partnership creation succeeded. Using partnership index INDEX.
```

**[SIZE=3]Multisync Setup and Configuration[/SIZE]**

1) Install the required packages for Multisync:
```
sudo apt-get install libmultisync-plugin-all multisync
```
Or, alternatively if you want to skimp on the packages:
```
sudo apt-get install libmultisync-plugin-evolution libmultisync-plugin-backup multisync
```
2) Start Multisync by typing "multisync" in a shell. You can also do via Applications > Accessories > Multisync, but the shell gives you a lot of feedback which can be helpful the first time you use it.
3) Create a new synchronization pair where one of the plugins is "SynCE Plugin" and the other is "Ximian Evolution 2", the order doesn't matter. You may need to create a new Contact List, Task List and Calendar, so that the default ones aren't used. I'm not sure if this is needed, but it was mentioned in the other thread.
4) Press the "Sync" button.
Initially, I had no entries in Evolution so for some reason, I had to modify all of the entries on my Pocket PC so that the timestamp would register each entry as a 'change', otherwise no entries were sync'd. There must be a simple workaround for this, but I'm not sure at this time.

**[SIZE=3]Disconnecting Your Pocket PC[/SIZE]**

1) Shutdown Multisync
2) "killall -HUP dccm" to kill the serial connection.
3) AS A LAST RESORT, run "synce-serial-abort", if the above command doesn't work.

Please let me know if you have any problems or suggestions.

Have fun!  :)
Dear tUrtleAE86,
I just synchronized perfectly with my iPAQ, according to your instructions. However, I do not see any options to sync the emails - I suspect I can not sync these; is it so?
Thanks.

---

### Post by dannystaple on 2006-12-16
> **harryharry said:**
> @blake

try this, works for me (ubuntu dapper)
supposing you have synce installed and working.

download; [http://prdownloads.sourceforge.net/synce/synce-gnomevfs-0.9.0-1.i386.rpm?download](http://prdownloads.sourceforge.net/synce/synce-gnomevfs-0.9.0-1.i386.rpm?download)

sudo apt-get install alien
sudo alien -i synce-gnomevfs-0.9.0-1.i386.rpm

synce-in-computer-folder install
synce-in-computer-folder connect

And it will appear in your filebrowser.
Well got most of this working in Edgy. I even have the tray icon and file manager working. The tray icon is available from the same sourceforge site, and can be installed with alien, however, in Edgy, it points to an old version of libgtop, and will complain. You will need to create a symlink for the old lib version (I am sure this is probably evil and wrong  - but it worked for me):

```
sudo ln -s /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2
```

You can then run the tray icon with:
```
synce-trayicon
```


Which gives you convenient right click access to the file manager, and disconnecting form the pocket pc. The file manager is showing me all the files. 

I still cannot get multisync to update my tasks from evolution to the pocket PC, and the only thing in the log which looks vaguely like a problem is this:
```
[synce_join_thread:260] synce_join_thread called when no thread is running
```

Even when I hit resync, it appears to do not a lot. Any ideas?

My general feeling is that this is an area that really, really needs some work- it is a long way behind many other components of the desktop, and while I am comfortable with getting most of it working (apart from the annoying evolution link-up, which seems only one-way), it would be a complete no-go area for someone who is simply a user (interpret as potential windows-convert, non-programmer or otherwise newbie).

---

### Post by dannystaple on 2006-12-16
> **Jorge Alfaiate said:**
> Dear tUrtleAE86,
I just synchronized perfectly with my iPAQ, according to your instructions. However, I do not see any options to sync the emails - I suspect I can not sync these; is it so?
Thanks.

Jorge, this may have been mentioned before, but emails need to be set up using IMAP. As your pocket Pc grabs itself an IP connection also as it links up, you just need normal IMAP settings in there. I do not think the built-in mail client supports POP3 email. 

You may be able to use an IMAP demon on your Linux box, which pumps a feed from a POP3 mailbox and then use that with both evolution and the pocketpc.

---

### Post by arturrenato on 2006-12-27
Hi,

I'm having problems to setup my Ipaq 3115. I'm receiving the message above:

root@artur-desktop:/lib/modules# synce-pstatus -d 3
[synce_info_from_file:51] unable to open file: /root/.synce/active_connection
[synce_info_from_file:51] unable to open file: /root/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

/var/log/message:

Dec 27 14:49:39 localhost kernel: [17180783.772000] usb 2-1: new full speed USB device using uhci_hcd and address 6
Dec 27 14:49:39 localhost kernel: [17180783.908000] ipaq 2-1:2.0: PocketPC PDA converter detected
Dec 27 14:49:39 localhost kernel: [17180783.908000] /home/artur/ipaq/kernel-2.6-driver/ipaq.c: active config #2 != 1 ??
Dec 27 14:49:39 localhost kernel: [17180783.908000] usb 2-1: PocketPC PDA converter now attached to ttyUSB0

DCCM is running:

root@artur-desktop:/lib/modules# ps auxww | grep dccm
artur     5525  0.0  0.1   1916   532 ?        Ss   14:38   0:00 dccm -p X


/proc/bus/usb/devices:

...
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=03f0 ProdID=1016 Rev= 0.00
C:* #Ifs= 1 Cfg#= 2 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
...


Do anybody have an idea? 

Thank you,
Artur

---

### Post by kseise on 2006-12-27
Try running synce as yourself, not root.  Post the results back here.

---

### Post by arturrenato on 2006-12-27
Hi kseise, thank you for your help.

The command outputs:

artur@artur-desktop:~$ synce-serial-config ttyUSB0
Sorry, you need root privileges to run synce-serial-config.
artur@artur-desktop:~$ synce-serial-start
Sorry, you need root privileges to run synce-serial-start.
artur@artur-desktop:~$            

Thanks.
Artur

---

### Post by Georges on 2006-12-27
LOL

he wanted you to start "synce-pstatus" as artur instead of root, not "synce-serial-config"

Your original post was that "synce-pstatus" does give an error. And it probably gives that error because you run it as root.

Georges

---

### Post by arturrenato on 2006-12-28
I'm getting the same error:

-----
artur@artur-desktop:~$ dccm -p 1010
artur@artur-desktop:~$ sudo bash
Password:
root@artur-desktop:~# synce-serial-config ttyUSB0

You can now run synce-serial-start to start a serial connection.

root@artur-desktop:~# synce-serial-start

synce-serial-start is now waiting for your device to connect

root@artur-desktop:~# exit
exit
artur@artur-desktop:~$ synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
artur@artur-desktop:~$
-----

Do you have any idea?
Thank you,
Artur

---

### Post by Georges on 2006-12-28
I use my own script which should do everything.
[http://ubuntuforums.org/showpost.php?p=1493807&postcount=111](http://ubuntuforums.org/showpost.php?p=1493807&postcount=111)

Sometime I also get the error. I then disconnect the ipaq, wait 10 seconds and reconnect.
Then run the script.
Usually then it works.

Georges

---

### Post by mintcoffee on 2007-01-03
Hi all,

I have a Palm Treo 700wx and the 'ipaq' driver is not loading when I plug in the USB cable. Does anyone know if this device is supported?

---

### Post by gadgetgirl on 2007-01-04
I installed enough of synce in edgy with my WM5 PDA (T-Mobile MDA) that I can use pls to see files and pcp to copy. Now I was wondering how I can disable synce temporarily.

The problem is that sometimes I just want to charge the phone and not sync anything. After installing synce, when I plug in the USB cable, it disconnects my wlan connection in NetworkManager in favor of the "wired connection" to the PDA. Ideally, I'd prefer to never lose my WLAN connection, but I would settle for being able to control when the connection occurs to the PDA.

Any ideas other than uninstalling synce?

Edit: It looks like running "sudo ./clean.sh" in my usb-rndis-lite directory will remove the modules and prevent my computer connecting to my PDA. If someone has a better procedure, please do tell. :)

---

### Post by Sjoerd Mulder on 2007-01-05
After wading through this and other forums, I still did not manage to get my synchronization working. So, I decided to find another way. I now sync my evolution with a server, and sync my pda with that server. 1) it works and 2) I can now sync whenever and wherever i want to, which I like. So even with multisync working correctly, I can say that this really is a better way!

I wrote a howto on my new weblog: [http://www.sjoerdmulder.nl/wordpress/?p=4](http://www.sjoerdmulder.nl/wordpress/?p=4)

---

### Post by stephensheppard on 2007-01-06
Your weblog entry cuts off at the beginning of discussion of configuration. Any chance you could post the entire howto? Thanks!

---

### Post by Sjoerd Mulder on 2007-01-06
Ouch you are right, must have done something wrong while editing the text. Glad I made a backup... Thanks for pointing to it.

It's back on now, however: 
[www.sjoerdmulder.nl](www.sjoerdmulder.nl)

---

### Post by IntuitiveNipple on 2007-01-10
Like a few others I've had issues with firestarter's default ruleset blocking connections between Multisync and my PDA, via synce.

Other firewall rulesets will likely cause the same problem.

I've added 3 rules via iptables to the netfilters. Firestarter provides a way for you to give it rules when it starts up by adding them to the /etc/firestarter/user-pre file, which is included by /etc/firestarter/firewall using a 'source' statement.

Here's the contents of my /etc/firestarter/user-pre
```
$IPT -I FORWARD 1 -s 192.168.131.0/24 -d 192.168.131.0/24 -j ACCEPT
$IPT -I OUTPUT 1 -s 192.168.131.0/24 -d 192.168.131.0/24 -j ACCEPT
$IPT -I INPUT 1 -s 192.168.131.0/24 -d 192.168.131.0/24 -j ACCEPT
```

$IPT is translated by firestarter into the appropriate command to execute iptables.

synce issues IPs in the range 192.168.131.0/24 range unless you've changed the defaults. If you have, then adapt the rules above to reflect your IP settings.

---

### Post by IntuitiveNipple on 2007-01-10
Instead of having to manually execute scripts when I want to synchronise, I've added a simple command to Edgy's 

**System > Preferences > Removable Drives and Media**

"PDA" tab.

**PocketPC** - "Sync PocketPC devices when connected" is enabled with the command:
```
sudo synce-serial-start && sleep 4 && multisync
```
This starts synce, gives it 4 seconds to establish the connection, and then starts multisync.

The && separator concatenates the commands but won't execute the 2nd command until the previous has completed.

To prevent the **sudo** command requiring the password i've edited the **sudoers** file:
```
$ sudo visudo
```
And added the following entry:
```
tj ALL=NOPASSWD: /usr/bin/synce-serial-start
```
Replace my username (tj) with your own, of course.

Now, whenever I drop the PDA into the cradle it will connect and then start multisync and do its thing without intervention.

Note: this assumes you've also set things up so that dccm (or vdccm) starts when you login via

**System > Preferences > Sessions** "Startup Programs" - Command=/usr/bin/dccm

---

### Post by kseise on 2007-01-15
> **IntuitiveNipple said:**
> Instead of having to manually execute scripts when I want to synchronise, I've added a simple command to...


Your last two posts are priceless.  They worked perfectly for me.  I plan on nuking my system either tonight or tomorrow and starting from scratch.  I will try and re-confirm all the steps needed, and then present a single HOW-TO.

---

### Post by IntuitiveNipple on 2007-01-21
Some minor improvements based on experience.

[list]
[*]When connecting the PDA, just in case there are problems with sudo (wanting a password), use *gksudo* so at least you get a prompt rather than the command silently failing.
[*]Specify the exact path to *synce-serial-start* otherwise *sudo* seems to get confused and not match it with the entry in *sudoers*
[*]The entry in *sudoers* may need to be slightly amended
[/list]
**Pocket PC hot-plug command**
```
gksudo /usr/bin/synce-serial-start && sleep 4 && multisync
```
**/etc/sudoers**
```
tj      ALL = (ALL) NOPASSWD: /usr/bin/synce-serial-start
```
**Tip:** If you don't seem to be getting a response when plugging the PDA in, but Device Manager shows it connecting/disconnecting, replace the hot-plug command with something simple like *gedit* which doesn't need super-user privileges and is a visual indication that the command is being executed.

---

### Post by snovak on 2007-01-24
Hey folks,
Having troubles with this I have a UTstarcom PPC6700 Sprint smartphone/WindowsCE pocketpc.  

OS: ubuntu dapper

Here's my reply from dmesg:
[17354985.452000] usb 4-1: new full speed USB device using uhci_hcd and address 4
[17354997.056000] usb 4-1: USB disconnect, address 4

I'll plug in the device and read the first line,
after about 5 seconds the second will be added.  

Am I without hope here?  Does Edgy have extended support Or, am I missing a package somewheres?

---

### Post by cookieofdoom on 2007-01-26
Great advice, thanks for this. It worked flawlessly with my x50V... if you have an x50v don't be afraid to try this!

---

### Post by Lapiz on 2007-02-11
Is it any way to connect device(Acer n311) which is seems not support ipaq driver?
```
Feb 11 23:45:59 benito-desktop kernel: [17190534.592000] usb 1-2: USB disconnect, address 4
Feb 11 23:58:41 benito-desktop kernel: [17191296.924000] usb 1-2: new full speed USB device using uhci_hcd and address 5
Feb 11 23:58:41 benito-desktop kernel: [17191297.128000] usb 1-2: configuration #1 chosen from 1 choice
```

---

### Post by andreh on 2007-03-23
> [http://www.synce.org/index.php/Windows_Mobile](http://www.synce.org/index.php/Windows_Mobile)
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
[http://www.synce.org/index.php/Windows_Mobile_2005_Support](http://www.synce.org/index.php/Windows_Mobile_2005_Support)
[http://www.funambol.com/opensource/](http://www.funambol.com/opensource/)
Windows Mobile is a compact operating system combined with a suite of basic applications for mobile devices based on the Microsoft Win32 API. Devices which run Windows Mobile include Pocket PCs, Smartphones, and Portable Media Centers. It is designed to be somewhat similar to desktop versions of Windows.[1]
**SynCE has support for Smartphones and Pocket PCs, using Windows CE, Windows Mobile 2003 and Windows Mobile 2005. **
[http://www.synce.org/index.php/Windows_Mobile](http://www.synce.org/index.php/Windows_Mobile)

[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
Windows Mobile 2005, originally codenamed "Magneto", was released on May 9, 2005. It is powered by Windows CE 5.0 and uses the .NET Compact Framework 1.0 SP2 &#8212; an environment for programs based on .NET to be used.[b]
SynCE has support for Windows Mobile 2005, on its support pages. [/b]

[http://www.synce.org/index.php/Windows_Mobile](http://www.synce.org/index.php/Windows_Mobile)
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
[http://www.synce.org/index.php/Windows_Mobile_2005_Support](http://www.synce.org/index.php/Windows_Mobile_2005_Support)
[http://www.funambol.com/opensource/](http://www.funambol.com/opensource/)
> [http://ubuntuforums.org/showthread.php?p=2271744#post2271744](http://ubuntuforums.org/showthread.php?p=2271744#post2271744)
Yes, under ** Fiesty I can sync my HP Ipaq1930 with Evolution**, the contacts and calendar are perfect . The Howto worked first time with out problems.

 could sync an **eten m600 and a linux box using a vmware virtual machine to sync files and emails (w/ the virtual machine running windows) **.
> ** Bluetooth gsm sony-ericsson Z530 d  of [b] Sony K750i is**
[http://forum.ubuntu-nl.org/topic/8383](http://forum.ubuntu-nl.org/topic/8383)
[https://wiki.ubuntu.com/NlBluetooth?highlight=%28nlbluetooth%29](https://wiki.ubuntu.com/NlBluetooth?highlight=%28nlbluetooth%29)

Ik synchroniseer opie adresboek, calendar en todo met evolution. Dat werkt super. 
Dat schijnt overigens ook te kunnen tussen evo en pocketpc. 
Hier is een heel goed programma voor: multisync. 
[http://multisync.sourceforge.net/index.shtml](http://multisync.sourceforge.net/index.shtml)
[http://forum.nedlinux.nl/viewtopic.php?id=11836](http://forum.nedlinux.nl/viewtopic.php?id=11836)

> [http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
MultiSync is a free modular program to synchronize calendars, addressbooks and other PIM data between programs on your computer and other computers, mobile devices, PDAs or cell phones. MultiSync works on any Gnome platform, such as Linux.

Currently MultiSync has plugins for
Ximian Evolution synchronization, supporting calendar, ToDos and contacts. Multisync also support Evolution 2 
IrMC Mobile Client synchronization (supported by e.g. SonyEricsson T68i/T610/Z600, Siemens S55 phones etc.) via Bluetooth or IR on Linux, or cable connection. [b]
[Windows CE / Pocket PC synchronization](http://www.microsoft.com/windowsmobile/pocketpc/default.mspx). This plugin is part of the SynCE project, and can be downloaded there. 
Opie and Zaurus synchronization. [/b]
SyncML support (supported by e.g. SonyEricsson P800/P900 and many other phones and devices, for example the SyncML server Sync4j). SyncML also allows you to do remote connection of two MultiSync programs via an encrypted connection over the net. 
Palm synchronization. 
LDAP synchronization. 
Backup of your PIM data.
[http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
> [http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
Attention Windows Mobile 2005 device owners!

These devices do not work with SynCE. If you are interested in getting these 
[devices supported by SynCE, please join the SynCE-WindowsMobile5 mailing list](http://sourceforge.net/mailarchive/forum.php?forum=synce-windowsmobile5). Se also bug report 1332550.
[http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
> Voor Pocket PC Windwow Mobile 2005/2003 Moet je ** SyncCE ** gebruiken, CE zal wel voor Windows CE staan.
OpenSync zelf zal in elk geval niet werken. Onderstaande link is van 27 jan 2007
[http://www.synce.org/index.php/Syncing_via_OpenSync](http://www.synce.org/index.php/Syncing_via_OpenSync)


Building SynCE with Windows Mobile 2005 support from Subversion
These instructions build Windows Mobile 5 support for SynCE by using the latest bleeding edge software from SynCE's Subversion repository. 
You must have a Subversion client installed.
Distribution-Specific Build Scripts 

Some linux distribution's package management tools even allow subversion sources to be managed and uninstalled, therefore if you have one of those, it's probably best to use the package tool to install the wm5 branch of SynCE. If your distribution isn't listed, proceed to the manual instructions below.
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_SourceForge_Packages_and_Subversion)
Edgy Eft: Gespannen salamander 6.10
Dapper Drake: Kwieke Woerd 6.06
Breezy Badger: Winderige Das 5.10
Hoary Hedgehog: De aloude egel 5.04
Warty Warthog: Wrattige wrattenzwijn. 4.10

[http://www.ubuntuforums.org/showthread.php?t=30936&page=16&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=16&highlight=pocketpc)
 installed enough of synce in edgy with my**b WM5 PDA (T-Mobile MDA) that I can use pls to see files and pcp to copy. **Now I was wondering how I can disable synce temporarily.
[http://www.ubuntuforums.org/showthread.php?t=30936&page=16&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=16&highlight=pocketpc)

[http://www.ubuntuforums.org/showthread.php?t=30936&page=14&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=14&highlight=pocketpc)
First, I have managed to synce my iPAQ1940 with Dapper, having some problems with RAPI-failure, but solved them. Later, I did bluetooth, and everything is working perfectly, but lost synce-serial commands. Does anyone knows why? Is it the case that you cannot use both of them: USB and bluetooth?
[http://www.ubuntuforums.org/showthread.php?t=30936&page=14&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=14&highlight=pocketpc)

[http://www.ubuntuforums.org/showthread.php?t=30936&page=13&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=13&highlight=pocketpc)
'm using a Dell axim x50 (wm2003se) I installed the following packages here [http://ubuntuforums.org/showthread.php?t=30936](http://ubuntuforums.org/showthread.php?t=30936)
Then started dccm by typing dccm in terminal window, then synce-serial-start as soon as the popup for the "connecting to network" came up on the handheld and voila
[http://www.ubuntuforums.org/showthread.php?t=30936&page=13&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=13&highlight=pocketpc)

[http://www.ubuntuforums.org/showthread.php?t=30936&page=11&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=11&highlight=pocketpc)
running latest ubuntu trying to sync ipaq3950 
followed all the steps until. tried changing ip address run synce-pstatus error:unable to initialize RAPI: unsuspected failure
Changed ip adress in IPAQ 192.168.131.201 manually and now everything works
[http://www.ubuntuforums.org/showthread.php?t=30936&page=11&highlight=pocketpc](http://www.ubuntuforums.org/showthread.php?t=30936&page=11&highlight=pocketpc)

[http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php)
1. Special note for owners **of Microsoft Smartphone devices**
These devices are not guaranteed to work with any released Linux kernel! Read on for the solution!
This note is known or probable to apply to the following devices, but may also apply to others:[b]
HTC Canary/Tanager (also known as i-Mate Smartphone, Orange SPV/SPV e100, Qtek 7070)
HTC Voyager (also known as i-Mate Smartphone 2, Orange SPV e200, Qtek 8080)
HTC Typhoon (also known as Orange c500, Qtek 8010)[/b] -- Dave Jenkins reports that it works with an unpatched 2.6.11-1.1369_FC4 kernel.
Motorola MPx200
Without a fix for this problem, synce-serial-start just hangs, because pppd will not be able to setup a PPP connection.
[http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php)

> **It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)


 

First you must find out what version of Windows your device is running, and visit the corresponding section below: 
For help on finding out what version of Windows your device is running, visit the Discovering your Device's Windows Version page. 
[i]Windows Mobile 2005 
Windows Mobile 2005 support in SynCE is under development. 
For support and Installation Guides, visit the Windows Mobile 2005 Support page[/i]
[http://www.synce.org/index.php/Installation_Guides](http://www.synce.org/index.php/Installation_Guides)
> Volgens mij zou je al veel hulp kunnen bieden door uit te zoeken wat nu standaard wel zou moeten werken en wat niet.
Op internet slagen verscheidene mensen er nl wel in om hun Pocketpc aan de praat te krijgen.
Florian, Je spreekt hopelijk wel een beetje engels ?

Welke versies van Windows PocketPC worden nu wel ondersteunt..en welke niet ?
Welke fabrikanten met Windows PocketPC worden nu wel ondersteunt..en welke niet ?
Welke desktops/window mangers van Windows PocketPC worden nu wel ondersteunt..en welke niet ? Ik krijg de indruk dat er met KDE minder problemen zijn.
Welke mobile phones en PDA's van Windows PocketPC worden nu wel ondersteunt..en welke niet ?
> [http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
MultiSync is a free modular program to synchronize calendars, addressbooks and other PIM data between programs on your computer and other computers, mobile devices, PDAs or cell phones. MultiSync works on any Gnome platform, such as Linux.

Currently MultiSync has plugins for
Ximian Evolution synchronization, supporting calendar, ToDos and contacts. Multisync also support Evolution 2 
IrMC Mobile Client synchronization (supported by e.g. SonyEricsson T68i/T610/Z600, Siemens S55 phones etc.) via Bluetooth or IR on Linux, or cable connection. [b]
[Windows CE / Pocket PC synchronization](http://www.microsoft.com/windowsmobile/pocketpc/default.mspx). This plugin is part of the SynCE project, and can be downloaded there. 
Opie and Zaurus synchronization. [/b]
SyncML support (supported by e.g. SonyEricsson P800/P900 and many other phones and devices, for example the SyncML server Sync4j). SyncML also allows you to do remote connection of two MultiSync programs via an encrypted connection over the net. 
Palm synchronization. 
LDAP synchronization. 
Backup of your PIM data.
[http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
> [http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
MultiSync is a free modular program to synchronize calendars, addressbooks and other PIM data between programs on your computer and other computers, mobile devices, PDAs or cell phones. MultiSync works on any Gnome platform, such as Linux.

Currently MultiSync has plugins for
Ximian Evolution synchronization, supporting calendar, ToDos and contacts. Multisync also support Evolution 2 
IrMC Mobile Client synchronization (supported by e.g. SonyEricsson T68i/T610/Z600, Siemens S55 phones etc.) via Bluetooth or IR on Linux, or cable connection. [b]
[Windows CE / Pocket PC synchronization](http://www.microsoft.com/windowsmobile/pocketpc/default.mspx). This plugin is part of the SynCE project, and can be downloaded there. 
Opie and Zaurus synchronization. [/b]
SyncML support (supported by e.g. SonyEricsson P800/P900 and many other phones and devices, for example the SyncML server Sync4j). SyncML also allows you to do remote connection of two MultiSync programs via an encrypted connection over the net. 
Palm synchronization. 
LDAP synchronization. 
Backup of your PIM data.
[http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
> [http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
**Attention Windows Mobile 2005 device owners!**

These devices do not work with SynCE. If you are interested in getting these 
[devices supported by SynCE, please join the SynCE-WindowsMobile5 mailing list](http://sourceforge.net/mailarchive/forum.php?forum=synce-windowsmobile5). Se also bug report 1332550.
[http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
> **It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
> **It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)


 

First you must find out what version of Windows your device is running, and visit the corresponding section below: 
For help on finding out what version of Windows your device is running, visit the Discovering your Device's Windows Version page. 
[i]Windows Mobile 2005 
**Windows Mobile 2005 support in SynCE is under development. **
For support and Installation Guides, visit the Windows Mobile 2005 Support page[/i]
[http://www.synce.org/index.php/Installation_Guides](http://www.synce.org/index.php/Installation_Guides)
> [b]STAP 1 
building SynCE with WM5 support from SVN[/b]
Install libsync, librapi2, odccm, synce-gnome 
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion)

[b]STAP 2
subversion of usb-rndis-lite and compiled[/b]
[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite))

[b]STAP 3
Starting A Connection[/b]
"sudo odccm" and then "cd synce-gnome/src" and then "python test.py"
[http://www.synce.org/index.php/Starting_A_Connection](http://www.synce.org/index.php/Starting_A_Connection)

---

### Post by andreh on 2007-03-26
Voor het installeren van 'usb-rndis-lite' moet voldaan worden aan twee eisen:
1) Kernel Headers installed:
2)  ** CONFIG_USB_NET_CDCETHER** compiled either into the kernel

Hoe en waar kan ik zien of dit het geval is ?
Moet ik dan in 
> cat /boot/config-2.6.17-11-386   | grep CDCETHER
zijn ?
En hoe kan ik nu zien of dit in de kernel zit..of in een module..of niet ?


Ik gebruik de onderstaande handleiding

[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite))

> Dit is** EIS 1 **

**Compile and Install **
Note: you must have your ** Kernel Headers installed: **
Waar kan ik onderstaande vinden:

> Dit is **EIS 2**

Note: You need to have ** CONFIG_USB_NET_CDCETHER** compiled either into the kernel, or as a module, in your kernel config.
En waar zit ' USB Gadget support -> Ethernet Gadge'  in Ubuntu 06.10 ?
Located in Device Drivers -> USB support -> USB Gadget support -> Ethernet Gadget

> USER @ubuntu:/lib$ [b] uname -a
Linux ubuntu 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
[/b]



[http://www.synce.org/index.php/Kernel_Headers](http://www.synce.org/index.php/Kernel_Headers)
Install the package kernel-headers-VERSION, where VERSION is your output to uname -r. In the previous example, I would have to install the package kernel-headers-2.4.27-2-686. This can be done using a graphical repository browser, or simply on the command line execute, as root:

USER@ubuntu:/lib$ ** sudo apt-get install kernel-headers-2.6.17-11-386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-headers-2.6.17-11-386

[http://www.synce.org/index.php/Kernel_Headers](http://www.synce.org/index.php/Kernel_Headers)
> USER@ubuntu:~/Desktop/PocketPC$** svn co [https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)**
svn: Can't open file 'usb-rndis-lite/.svn/lock'
USER@ubuntu:~/Desktop/PocketPC$** sudo svn co [https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)**
Checked out revision 2774.
USER@ubuntu:~/Desktop/PocketPC$** cd usb-rndis-lite**
USER@ubuntu:~/Desktop/PocketPC/usb-rndis-lite$** sudo make**
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/USER/Desktop/PocketPC/usb-rndis-lite modules
*make: *** /lib/modules/2.6.17-11-386/build: No such file or directory.  Stop.*
make: *** [default] Error 2
USER@ubuntu:~/Desktop/PocketPC/usb-rndis-lite$ uname -a
Linux ubuntu 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
USER@ubuntu:~/Desktop/PocketPC/usb-rndis-lite$ ls -rtl
total 120
> USER@ubuntu:/lib$** ls -rtl mod* **
total 16
drwxr-xr-x 7 root root 4096 2006-10-06 07:28 2.6.15-23-386
drwxr-xr-x 7 root root 4096 2007-03-07 13:43 2.6.15-28-386
drwxr-xr-x 6 root root 4096 2007-03-13 16:21 2.6.17-11-386
drwxr-xr-x 2 root root 4096 2007-03-16 12:27 2.6.17-11-generic
USER@ubuntu:/lib$
> **ls -rtl /lib/modules/2.6.17-11-generic/**
total 0
lrwxrwxrwx 1 root root 40 2007-03-16 12:27 build -> /usr/src/linux-headers-2.6.17-11-generic
> USER@ubuntu:/lib$** ls -rtl  /lib/modules/2.6.17-11-386 **
total 1516
drwxr-xr-x 11 root root   4096 2007-03-11 19:34 kernel
drwxr-xr-x  2 root root   4096 2007-03-11 19:34 initrd
drwxr-xr-x  2 root root   4096 2007-03-11 19:34 madwifi
-rw-r--r--  1 root root 265637 2007-03-13 16:21 modules.pcimap
-rw-r--r--  1 root root 339217 2007-03-13 16:21 modules.dep
-rw-r--r--  1 root root 387348 2007-03-13 16:21 modules.usbmap
-rw-r--r--  1 root root   1135 2007-03-13 16:21 modules.seriomap
-rw-r--r--  1 root root     74 2007-03-13 16:21 modules.ofmap
-rw-r--r--  1 root root  22378 2007-03-13 16:21 modules.isapnpmap
-rw-r--r--  1 root root    806 2007-03-13 16:21 modules.inputmap
-rw-r--r--  1 root root    813 2007-03-13 16:21 modules.ieee1394map
-rw-r--r--  1 root root     69 2007-03-13 16:21 modules.ccwmap
-rw-r--r--  1 root root 144271 2007-03-13 16:21 modules.symbols
-rw-r--r--  1 root root 329850 2007-03-13 16:21 modules.alias
drwxr-xr-x  2 root root    380 2007-03-25 11:42 volatile
USER@ubuntu:/lib$
[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite))

> USER@ubuntu:~$** lsmod  | grep usb **
usb_storage            73408  2 
scsi_mod              141320  3 sg,sd_mod,usb_storage
libusual               15632  1 usb_storage
usbcore               130304  5 usb_storage,libusual,ehci_hcd,uhci_hcd
Betekend onderstaande nu dat CONFIG_USB_NET_CDCETHER in de kernel is opgenomen of als een module aanwezig is ?
> ** /boot       vi /boot/config-2.6.17-11-386  **

/boot$ cat config-2.6.17-11-386 | grep _USB_N
CONFIG_DVB_USB_NOVA_T_USB2=m
CONFIG_USB_NET_AX8817X=m
**CONFIG_USB_NET_CDCETHER=m **
CONFIG_USB_NET_GL620A=m
CONFIG_USB_NET_NET1080=m
CONFIG_USB_NET_PLUSB=m
CONFIG_USB_NET_RNDIS_HOST=m
CONFIG_USB_NET_CDC_SUBSET=m
CONFIG_USB_NET_ZAURUS=m
CONFIG_USB_NET2280=m

---

### Post by andreh on 2007-03-26
Onderstaande zijn al geinstalleerd volgens de grafische Synaptic Manager.., dus dat is het probleem blijkbaar niet..
> Linux kernel headers for version 2.6.17 on x86/x86_64
This package provides kernel header files for version 2.6.17 on
x86/x86_64.
> Header files related to Linux kernel version 2.6.17
This package provides kernel header files for version 2.6.17, for sites
that want the latest kernel headers. Please read
/usr/share/doc/linux-headers-2.6.17-11/debian.README.gz for details
> USER@ubuntu:~/Desktop/PocketPC/usb-rndis-lite$ **sudo ./clean.sh**
Password:
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/USER/Desktop/PocketPC/usb-rndis-lite modules
make: *** /lib/modules/2.6.17-11-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules
USERs@ubuntu:~/Desktop/PocketPC/usb-rndis-lite$
> **ls -rtl /lib/modules/2.6.17-11-generic/**
total 0
lrwxrwxrwx 1 root root 40 2007-03-16 12:27 build -> /usr/src/linux-headers-2.6.17-11-generic
> [b]
 ls -rtl /usr/src/linux-headers-2.6.17-11-generic/    [/b]
total 340
-rw-r--r-- 1 root root 285721 2007-02-01 20:03 Module.symvers
-rw-r--r-- 1 root root  45479 2007-02-01 21:12 Makefile
drwxr-xr-x 8 root root   4096 2007-03-16 12:27 scripts
lrwxrwxrwx 1 root root     30 2007-03-16 12:27 usr -> ../linux-headers-2.6.17-11/usr
lrwxrwxrwx 1 root root     32 2007-03-16 12:27 sound -> ../linux-headers-2.6.17-11/sound
lrwxrwxrwx 1 root root     35 2007-03-16 12:27 security -> ../linux-headers-2.6.17-11/security
lrwxrwxrwx 1 root root     30 2007-03-16 12:27 net -> ../linux-headers-2.6.17-11/net
lrwxrwxrwx 1 root root     34 2007-03-16 12:27 modules -> ../linux-headers-2.6.17-11/modules
lrwxrwxrwx 1 root root     29 2007-03-16 12:27 mm -> ../linux-headers-2.6.17-11/mm
lrwxrwxrwx 1 root root     30 2007-03-16 12:27 lib -> ../linux-headers-2.6.17-11/lib
lrwxrwxrwx 1 root root     33 2007-03-16 12:27 kernel -> ../linux-headers-2.6.17-11/kernel
lrwxrwxrwx 1 root root     30 2007-03-16 12:27 ipc -> ../linux-headers-2.6.17-11/ipc
lrwxrwxrwx 1 root root     31 2007-03-16 12:27 init -> ../linux-headers-2.6.17-11/init
drwxr-xr-x 4 root root   4096 2007-03-16 12:27 include
lrwxrwxrwx 1 root root     29 2007-03-16 12:27 fs -> ../linux-headers-2.6.17-11/fs
lrwxrwxrwx 1 root root     35 2007-03-16 12:27 firmware -> ../linux-headers-2.6.17-11/firmware
lrwxrwxrwx 1 root root     34 2007-03-16 12:27 drivers -> ../linux-headers-2.6.17-11/drivers
lrwxrwxrwx 1 root root     33 2007-03-16 12:27 crypto -> ../linux-headers-2.6.17-11/crypto
lrwxrwxrwx 1 root root     32 2007-03-16 12:27 block -> ../linux-headers-2.6.17-11/block
lrwxrwxrwx 1 root root     31 2007-03-16 12:27 arch -> ../linux-headers-2.6.17-11/arch
direcory BUILD gekopieerd:

**sudo cp -R * ../2.6.17-11-386/**


> ** sudo make **
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/USER/Desktop/PocketPC/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.o
/home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.c: In function &#8216;init_status&#8217;:
/home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.c:191: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.c: In function &#8216;rx_submit&#8217;:
/home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.c:324: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.c: In function &#8216;usbnet_start_xmit&#8217;:
/home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.c:957: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
  CC [M]  /home/USER/Desktop/PocketPC/usb-rndis-lite/cdc_ether.o
  CC [M]  /home/USER/Desktop/PocketPC/usb-rndis-lite/rndis_host.o
  Building modules, stage 2.
  MODPOST
  CC      /home/USER/Desktop/PocketPC/usb-rndis-lite/cdc_ether.mod.o
  LD [M]  /home/USER/Desktop/PocketPC/usb-rndis-lite/cdc_ether.ko
  CC      /home/USER/Desktop/PocketPC/usb-rndis-lite/rndis_host.mod.o
  LD [M]  /home/USER/Desktop/PocketPC/usb-rndis-lite/rndis_host.ko
  CC      /home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.mod.o
  LD [M]  /home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
> **sudo ./clean.sh**
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/USER/Desktop/PocketPC/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules
[http://www.synce.org/index.php/Starting_A_Connection](http://www.synce.org/index.php/Starting_A_Connection)

> **sudo make install **
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/USER/Desktop/PocketPC/usb-rndis-lite modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  INSTALL /home/USER/Desktop/PocketPC/usb-rndis-lite/cdc_ether.ko
  INSTALL /home/USER/Desktop/PocketPC/usb-rndis-lite/rndis_host.ko
  INSTALL /home/USER/Desktop/PocketPC/usb-rndis-lite/usbnet.ko
  DEPMOD  2.6.17-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
depmod -ae
> Controleer of de daemons al runnen
 [b]udev -> hald -> dbus-daemon

ps aux | grep -E "hald|dbus-daemon|udevd"[/b]
root      2165  0.0  0.1   2644   332 ?        S<s  09:46   0:00 /sbin/udevd --daemon
104       4076  0.0  0.3   2304   824 ?        Ss   09:46   0:00 /usr/bin/dbus-daemon --system
108       4091  0.0  0.7   7140  1856 ?        Ss   09:46   0:05 /usr/sbin/hald
root      4092  0.0  0.3   2912   880 ?        S    09:46   0:00 hald-runner
108       4098  0.0  0.2   2024   672 ?        S    09:46   0:00 /usr/lib/hal/hald-addon-acpi
108       4101  0.0  0.2   2020   700 ?        S    09:46   0:00 /usr/lib/hal/hald-addon-keyboard
108       4114  0.0  0.2   2028   712 ?        S    09:46   0:00 /usr/lib/hal/hald-addon-storage
108       4116  0.0  0.2   2028   708 ?        S    09:46   0:00 /usr/lib/hal/hald-addon-storage
108       4119  0.0  0.2   2024   712 ?        D    09:46   0:00 /usr/lib/hal/hald-addon-storage
108       4121  0.0  0.2   2028   708 ?        S    09:46   0:00 /usr/lib/hal/hald-addon-storage
108       4125  0.0  0.2   2024   708 ?        S    09:46   0:00 /usr/lib/hal/hald-addon-storage
108       4133  0.0  0.2   2024   708 ?        S    09:46   0:04 /usr/lib/hal/hald-addon-storage
USER  4888  0.0  0.3   2304   820 ?        Ss   09:47   0:00 /usr/bin/dbus-daemon --fork --print-pid 8 --print-address 6 --session
> ** sudo apt-get install  python-dbus **
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-dbus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
> **pls**

** (process:12320): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'
[http://www.synce.org/index.php/Starting_A_Connection](http://www.synce.org/index.php/Starting_A_Connection)


> [b]cat /proc/bus/usb/devices
[/b]
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0bb4 ProdID=0bce Rev= 0.00 [b]
S:  Manufacturer=HTC
S:  Product=Generic RNDIS[/b]
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

---

### Post by imjustabill on 2007-04-03
One thing I found helps is manually starting the activesync application on my PPC, it makes things run much more smoothly

---

### Post by arijarot on 2007-04-04
Is there a way to sync files and folders?

---

### Post by mayonaise15 on 2007-04-05
Here is the command I have in Removable Drives and Media that auto starts dccm, starts multisync, then kills dccm when multisync exits.

```
dccm && sleep 4 && gksudo /usr/bin/synce-serial-start && sleep 4 && multisync & wait && sudo killall -HUP dccm
```

---

### Post by linuxpimp on 2007-04-08
How do i check if CONFIG_USB_NET_CDCETHER is activated and if not, how do i activate:

I am getting errors when installing the driver from Synce:
 sudo ./clean.sh 
Password:
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/ivor/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules


I assume this is why.

Thanks

lp

---

### Post by My-dial-up on 2007-04-09
ipaq 6365
Ubuntu 6.10 Desktop
No firewall

Having followed the guide I've managed to get the ipaq 6365 to sync, BUT my ipaq runs Journal by Omegaone and needs to have access to the internet over the synce connection. My network is 192.168.1.x yet the ipaq network runs 192.168.131.201/102.

How do I give the ipaq access to the internet through the synce connection?

---

### Post by My-dial-up on 2007-04-10
Someone must be able to help me out here?

---

### Post by linuxpimp on 2007-04-11
> **linuxpimp said:**
> How do i check if CONFIG_USB_NET_CDCETHER is activated and if not, how do i activate:

I am getting errors when installing the driver from Synce:
 sudo ./clean.sh 
Password:
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/ivor/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules


I assume this is why.

Thanks

lp

Ok folks, by using some Google-fu and the command make menuconfig from the linux-headers dir (/usr/src), i chercked and indeed have this module enabled. 

So why the errors? Duing a search withing menuconfig for the terms above returns no results.

What's the problem here?

Many thanks

lp

---

### Post by davedave on 2007-04-16
Hi,

Maybe I've missed something, but I seem to be getting the dreaded "Unable to initialize RAPI: An unspecified failure has occurred"

> **username@hostname:~$ lsusb**
Bus 004 Device 069: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC

Connecting and turning on the pocketPC
> **username@hostname:~$ tail -f /var/log/messages**
Apr 17 11:48:11 hostname kernel: [19694831.884000] usb 4-5.3: new full speed USB device using ehci_hcd and address 70
Apr 17 11:48:11 hostname kernel: [19694831.976000] usb 4-5.3: configuration #1 chosen from 1 choice
Apr 17 11:48:11 hostname kernel: [19694831.976000] ipaq 4-5.3:1.0: PocketPC PDA converter detected
Apr 17 11:48:11 hostname kernel: [19694831.976000] usb 4-5.3: PocketPC PDA converter now attached to ttyUSB0

Running synce-serial-start
> **username@hostname:~$ sudo synce-serial-start**
synce-serial-start is now waiting for your device to connect

**username@hostname:~$ tail -f /var/log/messages**
Apr 17 11:48:33 hostname synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr 17 11:48:33 hostname pppd[9104]: pppd 2.4.4 started by root, uid 0
Apr 17 11:48:35 hostname pppd[9104]: Serial connection established.
Apr 17 11:48:35 hostname pppd[9104]: Using interface ppp0
Apr 17 11:48:35 hostname pppd[9104]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 17 11:48:35 hostname pppd[9104]: local  IP address 192.168.131.102
Apr 17 11:48:35 hostname pppd[9104]: remote IP address 192.168.131.201
Apr 17 11:48:42 hostname pppd[9104]: LCP terminated by peer
Apr 17 11:48:42 hostname pppd[9104]: Connect time 0.2 minutes.
Apr 17 11:48:42 hostname pppd[9104]: Sent 400 bytes, received 986 bytes.
Apr 17 11:48:45 hostname pppd[9104]: Connection terminated.
Apr 17 11:48:45 hostname pppd[9104]: Modem hangup
Apr 17 11:48:45 hostname pppd[9104]: Exit.

Running synce-pstatus
> **username@hostname:~$ synce-pstatus**
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

Running "synce-matchmaker status" (or any synce-matchmaker command for that matter)
> **username@hostname:~$ synce-matchmaker status**
[synce_info_from_file:51] unable to open file: /home/username/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[main:62] Failed to initialize RAPI

Running George's script
> **username@hostname:~$ sync_dave**
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
/home/username/scripts/sync_dave: line 95:  9606 Killed                  ( for i in 2 5 7 9 12 15;
do
    echo $i; sleep 1;
done; killall -9 synce-pstatus )
synce-pstatus: no process killed
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
cannot connect
test
gathering device
setting device: ttyUSB0

You can now run synce-serial-start to start a serial connection.
device is set.
no dccm, starting it
done
no connection, starting one

synce-serial-start is now waiting for your device to connect
ret=0
done
starting activesync on pocket PC...
cannot start activesync, connection problem.

I'm at wits end with this currently, can anyone think of anything obvious that I've missed?
Or should I just wait until Feisty Fawn is released and pray that it solves my problem.

Cheers and many thanks in advance,
Dave

---

### Post by saz on 2007-04-17
anyone managed to install multisync? cuz when it tries do install libmultisync-plugin-palm it fails, there is a dependency "libpisock8" that is not installable, well it is not installable cuz it is old! i have installed libpsock9!

---

### Post by saz on 2007-04-17
forget it, i installed the others packages, except the palm one, and worked  no prob

---

### Post by johnny tutu on 2007-04-20
Good thread.

Thanks for helping me get my PPC connected.  Unfortunately I cannot seem to get Evolution and my PPC to pass my contacts calendar or anything back and forth.  Help?

---

### Post by johnny tutu on 2007-04-20
Nevermind, got it.

---

### Post by CybaCowboy on 2007-04-22
> **tUrtleAE86 said:**
> 7) Create the partnership between the Pocket PC and your computer. There are 2 slots on the device, so the INDEX can be 1 or 2.
```
synce-matchmaker create INDEX
```


This is where I get up to, only to find that it has not worked!


Here's my Terminal screen:

```

cowboy@cowboy-pc:~$ dccm
cowboy@cowboy-pc:~$ sudo synce-serial-start
Password:

synce-serial-start is now waiting for your device to connect

cowboy@cowboy-pc:~$ synce-matchmaker create INDEX
[synce_info_from_file:51] unable to open file: /home/cowboy/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI

```


Am I doing something wrong, or is there some other issue?

How can I get my Pocket PC to sync with Evolution?

---

### Post by My-dial-up on 2007-04-22
Is it possible to synce 2 pdas at the same time?

---

### Post by CybaCowboy on 2007-04-24
> **CybaCowboy said:**
> This is where I get up to, only to find that it has not worked!


Here's my Terminal screen:

```

cowboy@cowboy-pc:~$ dccm
cowboy@cowboy-pc:~$ sudo synce-serial-start
Password:

synce-serial-start is now waiting for your device to connect

cowboy@cowboy-pc:~$ synce-matchmaker create INDEX
[synce_info_from_file:51] unable to open file: /home/cowboy/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI

```


Am I doing something wrong, or is there some other issue?

How can I get my Pocket PC to sync with Evolution?

Anyone?

---

### Post by bheremans on 2007-04-24
it is a problem with dccm and synce-serial-start not running as the same user, I can create the index if I run dccm as root (-r option)but then synce tray icon isn't working properly.

---

### Post by CybaCowboy on 2007-04-24
So, how do I get it going then?

I tried "sudo dccm" (I was trying to run it as the same user as SynCE), but I am told that the command was not found!

---

### Post by bheremans on 2007-04-25
sudo /usr/bin/ddcm -r
shoud work, then create the index, and dccm can be restarted as normal user after that.

---

### Post by CybaCowboy on 2007-04-25
Still no luck...

[i]
cowboy@cowboy-pc:~$ sudo /usr/bin/ddcm -r
sudo: /usr/bin/ddcm: command not found
cowboy@cowboy-pc:~$ synce-matchmaker create INDEX
[synce_info_from_file:51] unable to open file: /home/cowboy/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI
cowboy@cowboy-pc:~$ dccm[/i]

---

### Post by thirupraju on 2007-04-29
After executing 
sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial

I am getting the following error. Please help me to solve.

with thanks & regards
Thiru


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsqldbc75 shtool automake1.4 libdc1394-13 xchat-common libpcre3-dev
  libcommoncpp2-1.4-0 libapr0 libclamav1 libldap2-dev libpcrecpp0 libsvn0
  kdesvn-kio-plugins libdevel-symdump-perl libyate1.0.0 yate libsvnqt2
  libavcodec0d linux-headers-2.6.17-10 libpri1.2 libccrtp1-1.4-0
  linux-headers-2.6.17-10-generic liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmimedir0 librapi2 multisync
Suggested packages:
  synce-kde libmultisync-plugin-irmc-bluetooth
Recommended packages:
  libmultisync-plugin-evolution libmultisync-plugin-backup
  libmultisync-plugin-irmc
The following NEW packages will be installed:
  libmimedir0 librapi2 librapi2-tools librra0 librra0-tools libsynce0
  multisync synce-dccm synce-multisync-plugin synce-serial
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/302kB of archives.
After unpacking 1540kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 40367 package `libselinux1':
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)


After serarching the forum I got the solution and now its working fine. Thanks a lot.
the link : [http://ubuntuforums.org/showthread.php?t=114504](http://ubuntuforums.org/showthread.php?t=114504)

---

### Post by cerealk on 2007-05-01
> **tUrtleAE86 said:**
> 
1) Connect your Pocket PC and type "dmesg" in a shell to see if the ipaq kernel module is loaded. The output might look like the following. Take note of the tty used for the connection.
```
usb 4-2: new full speed USB device using uhci_hcd and address 3
ipaq 4-2:1.0: PocketPC PDA converter detected
usb 4-2: PocketPC PDA converter now attached to ttyUSB0
```

So yea, I don't see that at all.   I'm running 7.04 with a iPAQ 19xx series.  Does any know why I couldn't even get this far?

---

### Post by jorgealfonso on 2007-05-01
One question to the people that has been following this thread : Is the information on the first post still valid? has there been some significant update/shortcut since?

I might sound lazy, but there are 20 pages since more than one year ago and it would take some time to go through it all (while understanding everything...)

Thank you

---

### Post by davedave on 2007-05-10
For Windows Mobile 5 devices, follow these steps
[http://www.synce.org/index.php/Windows_Mobile_2005_Support](http://www.synce.org/index.php/Windows_Mobile_2005_Support)

I was suffering from the following errors
> username@hostname:~$ synce-pstatus
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
> username@hostname:~$ synce-matchmaker status
[synce_info_from_file:51] unable to open file: /home/username/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[main:62] Failed to initialize RAPI

But following that guide and building things from the subversion repository has solved my problems.

---

### Post by codeslicer on 2007-05-11
To avoid having to run:

```

dccm
sudo synce-serial-start
multisync

```

everytime you need to sync, first, you need to find which group you are in. Go to System -> Administration -> Users and Groups. Click on the Advanced tab, and look at what it says in the Main Group selection box. Don't close it yet! If you do open it back up. Go to the Account tab and enter your password at the bottom, otherwise you might be locked out of the computer! Now, you need to run this in a terminal:

```
EDITOR=gedit sudo visudo
```

Next, go to the last line and add:

```
%GROUP ALL = NOPASSWD: /usr/bin/synce-serial-start, /usr/bin/synce-serial-abort
```

Replace GROUP with the group in the Users Settings panel. If my group was codeslicer, I would add this to the end of the file:

```
%codeslicer ALL = NOPASSWD: /usr/bin/synce-serial-start, /usr/bin/synce-serial-abort
```

Now go to System -> Preferences -> Removable Drives and Media -> PDAs, and under Pocket PC check the checkbox and in the box type in

```
killall -HUP dccm;sudo synce-serial-abort;dccm;sudo synce-serial-start;multisync
```

Now, it should work when you connect your Pocket PC/Windows CE Device.

This way, you can disconnect the device without running the killall command - it kills existing zombie connections when the device connects. Have fun :)

P.S. I'm using Ubuntu 7.04 with an HP Jornada 720 and it works perfectly, even the syncing between Evolution. Make sure you are using the right programs for the right devices!!!

---

### Post by codeslicer on 2007-05-12
Sometimes, the dates on evolution may be off. This isn't feature nor a bug. It's a featured bug. The problem is, the timezones don't match. For example, if on your Pocket PC you had Boston as the Timezone but New York on your computer, you have to make sure both of them correspond to Boston, or vise versa. :)

---

### Post by r2d22 on 2007-05-12
lucky you. i can't seem to run multisync anymore (too many install/uninstall?).

i'm getting the following error message:
> ra@big-room-ubuntu:~$ multisync
plugin_API_version
short_name
long_name
plugin_init
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/ra/.multisync/2/localsettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect
Segmentation fault (core dumped)


any guesses?

---

### Post by Ateo on 2007-05-14
If you do not see expected results for IPAQ PDAs (not being assigned a serial port), you need to add to /etc/modprobe.d/options:```
modprobe ipaq vendor=0x???? product=0x????
```

You can get the vendor and product using USBView (available in Synaptic).

If this has already been posted, sorry.

---

### Post by wersdaluv on 2007-05-27
Guys, try this one-> [http://synce.sourceforge.net/synce/howto.php](http://synce.sourceforge.net/synce/howto.php)

---

### Post by jcarrete on 2007-06-19
Hi All,

I have tried just about everything in this thread (twice or more) and I have still not been able to synchronise with Evolution.

The furthest I get is to get multisync running while ActiveSync on the PDA seems to think it is Sync'ing (the rotating arrows keep going). 

Here is the info I get from multysinc on the command prompt: 

> plugin_API_version
short_name
long_name
plugin_init
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/jcarrete/.multisync/4/localsettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect

In case it may help, I am using version 2.6.20-16-generic of the kernel with the latest updates applied.  I am using partnership index 2 on a Pocket PC 2003 (version 4.20.1081). 

Any help would be greatly appreciated.

Cheers.

 Jcarrete

---

### Post by jcarrete on 2007-06-26
Just a quick update.  I managed to make it work.  Apparently I had not defined which items had to be synchronised.  Once I did that, I was able to Resync and now it all works fine.

The only issue now is that every time I connect the device I have to go to the command prompt and type: *sudo synce-serial-start* and then re-start multisync.
Just a small inconvenience though.

Other than that it works great!

Jcarrete

P.S.: It would be nice to be able to synchronise the notes as well.

---

### Post by Argo666 on 2007-07-06
I tryed all the paths but when i reach this point:

synce-matchmaker create INDEX

the answer is always this:

[synce_info_from_file:51] unable to open file: /home/argo/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI

and I'm not able to go on and finish to connect my pc with my pda (I-mate Jamin)
Somebody could help me please?

Thanks

---

### Post by Strelock on 2007-07-07
Folks, does anybody have loox syncing correctly?
I have to issues:
1) A synchronization pair works only ones, on the second sync ximian plug in returns unknown error when looking for changes.

2) Pocket calendar gets totally screwed-up. Default one is slow and sometimes pop us a message that it is corrupted, Pocket Informant totally hangs the PPC...

Any clues anybody?

---

### Post by Strelock on 2007-07-08
Well, OK the issue is:
Everything works fine but only once for synchronization pair. Second time multisync returns: Failed to get first plugin change: Unknown error.

First plugin is Ximian. Do you have any suggestions?

---

### Post by andytof47 on 2007-07-08
Hi All I have followed the howto and just wanted to know if anyone has this problem

I get connected really quickly then diconnected staight away...:confused:

The user authenticated dialogue box shows up briefly then dies on me

My iptables shows me the firewall is completely down however I can still browse so I gather it's not the firewall

Anyhelp?????

---

### Post by Stu284 on 2007-07-08
i sort of got this working, only problem is when i plug in the phone, it comes up new network connection and i can connect to it, but it knocks out my internet connection!

anyone know how i can disable the usb-rndis-lite driver as i have given up with this, as i use the usb to charge my phone most days  :(

---

### Post by edmondt on 2007-07-10
This method doesn't work well for me, I have written a thread on [How to Connect to a WM5/WM6 Device with USB and sync with Evolution or Kontact]("http://ubuntuforums.org/showthread.php?t=345176&highlight=WM5"), let's start from there if you have a newer device.

---

### Post by hughleat on 2007-07-10
Hi,

    I've been through the steps listed.  I'm running Ubuntu 7.04 and I have an Ipaq HW6915.  When I try synce-pstatus, I get 

    synce-pstatus: Could not find configuration at path '(Default)'
   
    Does anyone know how to fix this?  

    Do I have to recompile the kernel?  This seems a bit scary to me (until very recently I've been a windows only user and so compiling the kernel sounds like a terrifying way to loose everything).

    Cheers,

    Hugh.

---

### Post by outphase on 2007-07-23
I am also getting the following message using Feisty with a TMo Dash
```
$ synce-pstatus 
synce-pstatus: Could not find configuration at path '(Default)'
```

---

### Post by lfvsouza on 2007-07-29
I got a MIO DIGIWALKER a701 - it is a windows mobile 5 phone. I am trying to sync it to evolution as well, but when i connect it and try the dmesg command it doesnt show me an ipac kernel or anything like it. the result for a lsusb is this line:
BUS 002 DEVICE 004: ID 3340:a0a1 Yakumo
It doesnt show in the SynCE or multi-sync so i cannot make it work.
Anybody ?

---

### Post by IzeHouze on 2007-08-17
Worked perfect the first time through.  Using 7.04 and a Sprint PPC6600 on Windows Mobile 2003.

The only extra step I had to do was "Resync" to get the contacts from the phone to Evolution on the first Sync.

---

### Post by borris.morris on 2007-09-06
> **outphase said:**
> I am also getting the following message using Feisty with a TMo Dash
```
$ synce-pstatus 
synce-pstatus: Could not find configuration at path '(Default)'
```

do you have a password? if so, try to disable it once.

---

### Post by momist on 2008-02-23
> **codeslicer said:**
> To avoid having to run:

```

dccm
sudo synce-serial-start
multisync

```

everytime you need to sync, !

Thankyou codeslicer!!  I'm using Ubuntu 7.10 and a Medion MDPPC250 and your code here has made it work for me.  I thought I had this fixed last week, but ran into the problems others have had with
```

synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred

```

It synchronised once at the first attempt, and then I never could get it to go again.  This seems to have fixed it, for now.

Thank YOU! :)

Now I need to get multisync to backup and synchronise a file (not Evolution)  for my password vault.  Any ideas on that anyone?

TIA

---

### Post by cyber_bushi on 2008-02-26
Hi,

anyone solved the time problem when syncing Evolution with the pda? I read all through the thread but didn't find anything. In my case every appointment on Evolution is one hour later than I entered it on the pda. Time zone on pda and Evolution are the same, hardware time is local (due to windows dual boot).
Any hints?

cb

---

### Post by djbon2112 on 2008-03-15
Hello everyone. I get to the last step ("synce-matchmaker create INDEX") but I get the error:

```
joshua@joshua-laptop:~$ synce-matchmaker create
[synce_info_from_file:51] unable to open file: /home/joshua/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI
```

Same thing if I type any number after "create". I've got a Motorola Q (WM5) and Ubuntu Gutsy.

---

### Post by brodanmd on 2008-04-13
hi. i have an i-mate jam (windows mobile 2003 se). i followed all the instruction but when it got to the part of making a partnership, i got this message:

dan@Ace:~$ synce-matchmaker create INDEX
[rra_matchmaker_create_partnership:380] Partnership not found and there are no empty partner slots on device.
Partnership creation failed. Maybe there is no empty partnership slot?
dan@Ace:~$

i couldn’t sync.
i’m a nube and i’m lost. :)
thanks!

---

### Post by VeeDubb on 2008-04-13
You'll probably find that syncing is still impossible because Ubuntu has such a bad implementation of synce and opensync that it's a joke.  However.....

I can solve that problem for you.  I'm at my windows box at work, so I can't give you the exact commands, but if you type synce-matchmaker in a terminal with no options, it will read out the various uses of that command.  One of them will allow you to delete partnerships that are already on your device.  

The reason this is necessary is that windows mobile only has support for two sync partnerships.  Once you've created partnerships with two computers, you can't make another even if they are all the same computer with different OS's and sync software installed.  

Just delete the partnerships you have, and you'll be able to make a new one.

Unfortunately, as I said before, you're more likely to win the lottery than get syncing working with Ubuntu.  I recommend you use that command to delete both partnerships, do NOT make a new one, and then install Mandriva linux 2008-Spring.  There is a meta package in their repositories called task-WM5-synce-kde and  another called task-WM5-synce-gnome.  Just install the one for whichever desktop you're running and syncing will be up in about 5 minutes.  works like a champ for WM5 and WM6.  Mandriva isn't quite as polished as ubuntu these days, but it's more than adequate, and if WM sync is important to you, it's the only option that's practical.  That or spend a year or two writing your own software.

---

### Post by AdamWill on 2008-04-14
For the Mandriva option, here's the instructions:

[http://wiki.mandriva.com/en/2008.1_Synchronization](http://wiki.mandriva.com/en/2008.1_Synchronization)

---

### Post by qgfreire on 2008-05-01
It worked easily in Hardy!

---

### Post by claudio.88 on 2008-05-01
> **qgfreire said:**
> It worked easily in Hardy!

I have a WM6 HTC ppc ad with the procedure of the first post i can't connect my ppc to my Hardy!! :(

When i try to do this command: 
```
sudo synce-serial-start
``` the command line don't prompt!

and then:

```
my@my-pc:~$ synce-pstatus
** Message: Hal reports no devices connected

** (process:8732): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pstatus: Could not find configuration at path '(Default)'
```

---

### Post by qgfreire on 2008-05-02
Sory, My HP hx4700 it's in 2003SE <=> Windows CE 4.21.

can you send usbview?

---

### Post by zovcin on 2008-05-05
> **qgfreire said:**
> It worked easily in Hardy!

I managed connecting and syncing, but all done manually.

How did you make the automation?

Can I just plug in the Pocket PC and wait for event to start synchonization?

Zoran

---

### Post by AdamWill on 2008-05-06
claudio: WM5 and later devices do not work the same way, the instructions in this thread won't help you. See this thread:

[http://ubuntuforums.org/showthread.php?t=774110](http://ubuntuforums.org/showthread.php?t=774110)

for some help with WM5+ devices.

---

### Post by spnoe on 2008-05-11
Can anyone help?? I used the script as in this thread and get the error below;

synce-serial-start was unable to find the file /usr/etc/synce-serial.default:

Please run the synce-serial-config tool to create this file before running this
script again.

I am running Mobile 2003 and Ubuntu Hardy Heron

Help appreciated.

Steve

---

### Post by eternalnoob on 2008-06-05
Thanks tUrtleAE86, worked a treat for the following combination
ubuntu 8.04
Dell Axim x50v Windows Mobile 2003 SE

Being a complete noob I used synaptic to install all the packages.

I already had 2 partnership so I had to replace one of them

synce-matchmaker replace 1

apart from that no probs

---

### Post by Mander on 2008-06-05
Has anyone been able to get sync working with a really old pocket PC?  I've got an ancient Cassiopeia (MIPS VR4122, Windows CE 3.3.9348, from 1999) that I've been hanging on to because, well, it still works.  I can still sync it with Outlook 2003 but it won't even communicate with Vista.  Has anyone tried to get an ancient old thing like that working with Linux?

---

### Post by qgfreire on 2008-06-20
I synced with evolution, not only contacts but also calendar.
best regards

---

### Post by hufferd on 2008-08-16
> **tUrtleAE86 said:**
>  HOWTO is based on syncing my Dell Axim X3i with Evolution, but it should carry over to IPAQs and other Pocket PCs.
1) Shutdown Multisync
2) "killall -HUP dccm" to kill the serial connection.
3) AS A LAST RESORT, run "synce-serial-abort", if the above command doesn't work.

Please let me know if you have any problems or suggestions.

I do have 2 questions here I have a Dell Axim 50 and I got everything installed and it sync BUT the only thing it pulled off my PDA were my contact names no addresses or email addresses were pulled from my PDA did I do something wrong? 

#2. is it a must to kill the serial connection everytime you are done? and do you need to restart it every time as well? 

Thanks Dan

---

### Post by hufferd on 2008-08-16
Bump

---

### Post by taps on 2008-08-26
> **spnoe said:**
> synce-serial-start was unable to find the file /usr/etc/synce-serial.default:

Please run the synce-serial-config tool to create this file before running this
script again.

I am running Mobile 2003 and Ubuntu Hardy Heron

I have the exact same problem. Surely someone can help here!

---

### Post by Rhubarb on 2008-09-07
I have managed to get contacts and tasks synchronised with evolution, thanks :)

taps & hufferd, I don't think I'd be able to help you out, as /usr/etc/synce-serial.default does not exist for me either, yet it still works fine.

For your information:  I'm running Mobile 2003 SE, Ubuntu 8.04 64bit, connecting via the USB cradle.

For those that have multisync working, here is a little bash script I created to make it easier to run multisync from the Accessories menu:

```
#!/bin/bash
dccm
sleep 1
gksu synce-serial-start
sleep 3
multisync
sleep 1
killall -HUP dccm
```

If I'm not clear, please post here / send me a private message.

The next phone / PDA I'll buy will be Linux powered, and I'll make sure it's Linux friendly before buying it (Looking at getting an openmoko next) ;)

---

### Post by filipecamargo on 2008-09-12
Hi everyone!
I've used this tutorial to sync my E-TEN (WM6) PPC to Evolution in Ubuntu Hardy: [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) .
The sync takes place but no contacts from my PPC appears at Evolution. 
I didn't erase the windows partnership. I have both now at PPC.
I've tried both metods (OpenSync and SyncEngine) and have the same results for them: It shows "syncronized" at PPC but no contacts at Evolution.
Any hint?
Thanks!
Filipe

---

### Post by Rhubarb on 2008-09-17
filipecamargo:
There's a few things that may help you.
One is to setup multisync as in the screenshot attached.

The other is a bug that I found.
It won't synchronize if it doesn't think your contacts have changed.
Thankfully there is a good workaround to fix this problem.
You can either edit your contacts a tiny bit so they change, and hence get synchronized with evolution, or the approach I took:
I backed up my contacts (I have an app called xbackup on my wince phone), deleted all my contacts, the restored all my contacts.
When they're restored, multisync (synce may be similar) noticed the change, and correctly populated evolution with all my contacts.

---

### Post by okcwby390f on 2008-10-22
tUrtleAE86: I ran through the instructions you got in this thread to synce my HP handheld. I got a connection with the PPC. I can see that on the screen of the PPC. when I run synce-pstatus I get a error of (could not find configuration path at "default"). I was wondering if I might need to remove synCE and multisync to configure them again. Like I said my PPC is showing a connection, but I get the above error. If I try to run multisync from the graphic interface it tells me it is running but nothing is happening. If I run multisync-qad ; in graphic interface, it tells me it could not start synce engine. It is the same with kithensync. Any help from anyone would be great. I posted a thread about my problem also. called synce problem with handheld. again thanks for any help

---

### Post by okcwby390f on 2008-10-22
> **djbon2112 said:**
> Hello everyone. I get to the last step ("synce-matchmaker create INDEX") but I get the error:

```
joshua@joshua-laptop:~$ synce-matchmaker create
[synce_info_from_file:51] unable to open file: /home/joshua/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI
```

Same thing if I type any number after "create". I've got a Motorola Q (WM5) and Ubuntu Gutsy.

I also get the same thing if I run the synce-matchmaker.

---

### Post by VeeDubb on 2008-10-26
> **filipecamargo said:**
> ...I've tried both metods...
Thanks!
Filipe


I actually think that's your problem right there.

I've tried this over and over again with several different versions of several different distributions.  The mandriva solution worked "okay" but not great, and I found the system unstable on my hardware. (which it shouldn't have been since it's mostly new hardware, and Ubuntu is a ROCK)

Anyway, what finally got it working for me, was a CLEAN INSTALL of Ubuntu, and explicitly following the directions that several others have already linked from the opensync wiki.

I believe the problem was in trying to follow all the different how-to's and finding myself with different things running that appeared compatible, but ultimately caused the whole thing to not work.

Right now, I have a fully functional sync for contacts and calendar between my WM6 pda and Evolution.  The to-do list doesn't sync, but I don't use that on my desktop anyway.

---

### Post by impresionist on 2008-12-03
Hello All,
I'm trying to do this issue since when I had Festy, then Hardy, then now with Interpid, no way...
Now, I followed your step one by one, and what I obtain is:

XXX@XXX-interpid:~$ sudo synce-serial-start
[sudo] password for XXX: 
Connect script failed

synce-serial-start was unable to start the PPP daemon!

When I try to:
XXX@XXX-interpid:~$ PPP daemon
bash: PPP: orden no encontrada

Meanwhile when I start from:
sudo synce-serial-start, I get:
samer@samer-interpid:~$ sudo synce-serial-start
Connect script failed

synce-serial-start was unable to start the PPP daemon!


I don't know what bad I'm doing in all this...

I'm trying to connect IPAQ 6915 with WM5

Thanks in advance,

Samer

---

### Post by richardh9936 on 2010-06-24
IMPRESIONIST wrote "IPAQ 6915 with WM5"

Ah, that WM5 would be the problem, then.  Try wikipedia's comments on MS ActiveSync; and in these forums elsewhere, I've seen that anything after WM3 is problematic.

---

### Post by ODECiF on 2010-08-06
Okay, this tutorial has completely screwed me...

I use Lucid and I have tried for about 3 hours to get through this howto, but to no avail. Now, when I decided to don't give a flying ...., I cannot connect anything the way I want it although I could before.

I cannot connect my HTC Touch Pro (Raphael) as a mass storage device as I could before (it wont eve pop up) and I cannot connect to the SSH-server I have managed to make use of while accessing my harddrive with movies on.

Anyone who could help me to restore everything to what it was 4 hours ago? I have removed all packages via apt-get that was described to be installed in this guide.

//ODECiF

---

### Post by maiemi on 2011-03-11
Hi ODECIF,

to connect Your Rafael as mass storage, You have to install the freeware wm5torage on your windows mobile device. 
Link: [http://freewareppc.com/communication/wm5torage.shtml](http://freewareppc.com/communication/wm5torage.shtml)

You can find the HowTo here:
[https://help.ubuntu.com/community/PortableDevices/WindowsMobile](https://help.ubuntu.com/community/PortableDevices/WindowsMobile)

Hope, it helps,

greets,
maiemi

---

### Post by meanymoo on 2011-06-02
is it any other way to explore my windows mobile other than with nautilus?
it appears that nautilus can't handle syncE
i've tried GPE File Manager too but it doesn't work either
my device is imate JAQ WM5
which in [https://help.ubuntu.com/community/PortableDevices/WindowsMobile](https://help.ubuntu.com/community/PortableDevices/WindowsMobile)
is compatible device
and my[FONT=Verdana][SIZE=1] [/SIZE][/FONT][COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][FONT=Verdana][SIZE=1]ubuntu is 11.04 - the [/SIZE][/FONT][I][FONT=Verdana][SIZE=1]Natty[/SIZE][/FONT]
[SIZE=1][FONT=Verdana]can someone help me please[/FONT][/SIZE]
thanx before
[/I][/COLOR][/FONT][/COLOR]

---

