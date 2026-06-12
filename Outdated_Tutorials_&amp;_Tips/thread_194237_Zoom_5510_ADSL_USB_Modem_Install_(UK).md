---
title: "Zoom 5510 ADSL USB Modem Install (UK)"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Malac on 2006-06-11
[B]_[SIZE=5]Zoom [COLOR=black]5510[/COLOR]A ADSL USB Modem Install[/SIZE]_  [SIZE=2]
(This is for the slim dark grey one issued in the UK by alot of providers [pictured below]. [COLOR=black]5510[/COLOR]-72 Mine says.
May work with other Connexant Chip Modems, just compile and run cxacru-fw [/SIZE][/B][SIZE=2][see post #23 page 3][/SIZE][B][SIZE=2] and put extracted file in the cxacru folder).
[/SIZE][/B][B][IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=11219&d=1150317617[/IMG]
If you have this model below you want the other howto at the link provided.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=11257&stc=1&thumb=1&d=1150366330[/IMG]
[/B] [B][SIZE=2] 
[ https://wiki.ubuntu.com/UsbAdslModem/EagleUsb?highlight=%28eagle-usb%29]("https://wiki.ubuntu.com/UsbAdslModem/EagleUsb?highlight=%28eagle-usb%29")
This has been tested by zxc and works fine for this one.

_Please Note_:
[COLOR=DarkGreen]youruserlogin[/COLOR][/SIZE][/B]**[SIZE=2][COLOR=DarkGreen][COLOR=Black] is what you use to login to the actual connection, it[/COLOR][/COLOR][/SIZE]**[B][SIZE=2][COLOR=DarkGreen][COLOR=Black] can be in the form of your full e-mail address not just the username[/COLOR][/COLOR]
[/SIZE][/B] 
 This was done on a Fresh Install of Ubuntu 6.06 "Dapper" and Ubuntu 6.10 "Edgy".
 [B][U][SIZE=5]Okay to start

[/SIZE][/U][/B]  On an Internet Enabled OS or Machine
 
 Get the following file from the internet.
**CXACRU Extraction Utility**
 [http://homepage.ntlworld.com/malacandra/cxacru.zip](http://homepage.ntlworld.com/malacandra/cxacru.zip)
[SIZE=-2]I can't remember where I got this one from so I have put a copy here.[/SIZE]
 [SIZE=-2]This is the one with a pre-extracted **(Windows)** Zoom [COLOR=black]5510A[/COLOR] firmware file.
If you have a Mac you will have to run the cxacru-fw program on the Mac driver file.
I do not know if this will work as I do not own a Mac.
If someone wants to attach the Mac file to this post I will include it in the zip file.
[/SIZE]  
 Put it in a folder called "adslusb"(without the quotes) in the root of your machine.
 Also save this page to that folder as a ".complete" file

 If you are *not* dual booting you will have to burn the folder onto a CD-R or floppy.
 If you *are* dual booting with (I assume) Windows, when Back in Ubuntu mount your Windows Drive using "mount" in the root Terminal(described later).
Get the DNS numbers for your ISP.
These can be found in windows by typing ```
ipconfig /all
``` in a Dos Box and scrolling to the section for the connected modem or phone ISP and ask them.
 
 Back in Ubuntu
 Login as normal user.
 I found this made life easier, saving having to type sudo in the terminal all the time.
 Run nautilus as root and gnome-terminal as root.
 Choose [Applications->Accessories->Alacarte Menu Editor], scroll down to [System Tools] and activate [Root Terminal] and [Run as Different User], Close.
 Choose [Applications->System Tools->Root Terminal], then Enter Password.
 Choose [Applications->System Tools->Run as different user], type "nautilus"(without the quotes) in the box.
  DO NOT CLOSE THESE UNTIL THE END.

 ------ Dual-Boot Hard Disk Section, if folder is on a CD-R or floppy miss this section out -----
 In Nautilus
 Go to Filesystem:/mnt/, right-click on space, choose "Create Folder" and call it "win".
 In Terminal
 If Windows drive is the first partition (1) on C: (hda) then this should be sufficient:
[LEFT]```
mount /dev/hda1 /mnt/win
```[/LEFT]
                                      ----- End Section -----

 In Nautilus
 Go to FileSystem:/mnt/win/ or to the CD or to floppy.
Right-click the folder "adslusb" and choose copy.
Go to Filesystem:/usr/src/, right-click on space, choose "Paste".
Choose "Bookmarks" in the top menu and "Add to Bookmarks", (This will aid with navigation later).
 Go to Filesystem: /usr/src/adslusb folder.
Open cxacru-fw.zip
Extract "cxacru-fw" folder to Filesystem: /usr/src
 [SIZE=-2](Using [Extract] choose "Other" in "Extract in Folder" pulldown
Browse to Filesystem:/usr/src, Click [Open] then [Extract])[/SIZE]
 
 In Terminal

```

 cd /usr/src/cxacru-fw
 cp /usr/src/cxacru-fw/cxacru-fw.bin /lib/firmware/2.6.15-23-386/cxacru-fw.bin
``` In Nautilus
Go to folder Filesystem: /etc/network.
           Open file "interfaces".
And insert the following at the bottom:
```
[LEFT]# The ADSL connection
iface ppp0 inet ppp
    provider [COLOR=DarkGreen]yourprovidername[/COLOR]
    # enables ip forwarding (this is a gateway)
    pre-up echo 1 > /proc/sys/net/ipv4/ip_forward
    pre-up iptables-restore < /etc/iptables.up.rules

auto ppp0[/LEFT]
    
```-----------------------------------------------------------------------------------------------------------------------------------
[B]At this stage Reboot and when the boot messages get to "Configuring Network Interfaces......" start watching the green link light.
It should flash repeatedly then eventually stay on.(This can take what seems like forever but persevere.)[/B]
-----------------------------------------------------------------------------------------------------------------------------------
Okay congratulations, you've gotten this far, hurrah. \\:D/ =D>

Run nautilus as root and gnome-terminal as root.
Choose [Applications->System Tools->Root Terminal], then Enter Password.
 Choose [Applications->System Tools->Run as different user], type "nautilus"(without the quotes) in the box.
  DO NOT CLOSE THESE UNTIL THE END.

In Nautilus
 Go to Filesystem: /etc/ppp/peers folder.
Create file [COLOR=green]yourprovidername[/COLOR] (Right-Click: Create Document->Empty File).
**The only things in this file should be.**
```

 user "[COLOR=DarkGreen]youruserlogin[COLOR=Black]" *(with the quotes this time)*[/COLOR][/COLOR]
 plugin pppoatm.so
[LEFT]  noipdefault
 usepeerdns
 defaultroute
 persist
 noauth
 nopcomp
 noccp
 novj[/LEFT]
    
```[LEFT]
Save and Exit
[/LEFT]
                                      Go to Filesystem: /etc/ppp folder
Open the file "chap-secrets"
Add a line
```
 "[COLOR=DarkGreen]youruserlogin[/COLOR] * [COLOR=DarkGreen]yourpassword[/COLOR]"(without the quotes)
``` Open the file "pap-secrets"
And do the same.
Rename the file "options" to "options.orig"(right-click choose "Rename").
Create new file "options" and enter these values:
```

 asyncmap 0
[LEFT]  auth
 crtscts
 lock
 hide-password
 modem
 proxyarp
 lcp-echo-interval 60
 lcp-echo-failure 4
 noipx
 replacedefaultroute
 noipdefault
 #noauth
 persist
 lcp-max-configure 50
 -pap
 name any
 user [COLOR=DarkGreen]"youruserlogin" [/COLOR](with the quotes this time) 
 defaultroute
 plugin /usr/lib/pppd/2.4.4b1/pppoatm.so 0.38[/LEFT]
    
```[LEFT]
Create file "resolv.conf"(right-click on space, choose "Create Document"--->"Empty File")
[/LEFT]
                      Open this file and add this:
```

 nameserver xxx.xxx.xxx.xxx
 nameserver xxx.xxx.xxx.xxx
```[LEFT]Where xxx.xxx.xxx.xxx is replaced by your ISP DNS Servers.
[/LEFT]
                                      Go to /etc folder.
Open the file "modules"
Add a line:
[LEFT]```
 "pppoatm"(without the quotes).
```[/LEFT]
                                      Save and Exit.
 Create file "cxacru"(right-click on space, choose "Create Document"--->"Empty File")
Open "/etc/cxacru" file and cut/paste this in to read like this.  
 ```

#
[LEFT]# Config file for Conexant AccessRunner 
# 

# Driver mode 
DRIVER_MODE=1 # 1 = normal, 2 = debug, 3 = normal+max speed (without ask adsl status), 4 = debug+max speed (without ask adsl status) 

# Protocol 
PROTOCOL_MODE=2 # 1 = RFC1483/2684 routed, 2 = PPP over ATM (pppoa), 3 = RFC1483/2684 bridged, 4 = PPP over Ethernet (pppoe) 

# Paths 
BINARY_PATH="/usr/sbin" 
ATM_PATH="" 

# ADSL 
# if OPEN_MODE is blank then cxload uses default mode acoording VID & PID 
# Values for OPEN_MODE are: 
# 0 = auto selection, G.Handshake 
# 1 = auto selection, T1.413 
# 2 = G.Handshake 
# 3 = ANSI T1.413 
# 4 = ITU-T G.992.1 (G.DMT) 
# 5 = ITU-T G.992.2 (G.LITE) 
OPEN_MODE= 

# ATM 
VPI=0
VCI=38

# Specific for RFC1483/2684 routed/bridged
#  if IP_ADDRESS is blank in bridged mode then it uses DHCP to get IP
IP_ADDRESS=
NETMASK=255.255.255.0
GATEWAY=[/LEFT]
    
```[LEFT]
Save and Exit.
[/LEFT]
                        
 I would also get rid of the ntpdate check on boot as you aren't connected anyway.
 To do this choose System->Administration->Services and uncheck (ntpdate)

 REBOOT (Do not try dialing yet.)

 When you reboot and login type:
 In Terminal
  [LEFT]```
pppd call [COLOR=DarkGreen]yourprovidername[/COLOR]
```[/LEFT]
                                      And I hope it works for you as it did for me. Good Luck.

------------------------------------------------------------------------------------------------------------------------------------------
[B]Slight Addendum:
Don't use kppp, gnome-ppp or System->Administration->Networking to change the PPP settings as it screws up the files for this connection.[/B]

This is adapted from my original 5.10 "Breezy" HowTo and the process is much easier for "Dapper". One reason to upgrade. :-D
I re-did my entire install from scratch several times during doing this walkthrough to make sure it worked. Hopefully I didn't forget anything.

It should work on a fresh install of "Dapper" and "Edgy", I can't vouch for anything else or if you have already altered your system from the default.

This is for a UK broadband ISP so I don't know if it will work in other countries.

Have Fun.

P.S. If you want to let me know here if this worked for you or not it would be much appreciated

---

### Post by zxc on 2006-06-11
I wasn't sure what you meant by "yourusernamename"

For example my username comes in the form:

[email]Myusername@tiscali.co.uk[/email]

Do I include the whole thing or just myusername?...I included the whole thing throughout and it didn't seem to effect it (or turn up any errors).

---

Anyway to my problem, I followed the tutorial and everything seemed fine except when the run:
```
sudo pppd call yourprovidername
Plugin /usr/lib/pppd/2.4.4bl/pppoatk.so
Plugin pppoatm.so loaded.
pppd: In file /etc/ppp/peers/yourprovidername : unrecognised option '8.35'
```

That option comes from the following line within yourprovidername:

(Hash - I can't find it on this stupid Mac) VP.VC pair used by your ISP.
8.35

I tried changing it to 0.38 (which I think is the UK's VP/VC but I just got the same error except with 0.38. I also tried commenting this line out and I just got:

```
Plugin /usr/lib/pppd/2.4.4bl/pppoatk.so
Plugin pppoatm.so loaded.
```

Any my internet didn't work.

After issuing the pppd call command should my internet work as my modem doesn't have the "Link" L.E.D shining?

Thanks for all your hard work, it's greatly appreciated (and by the way this was done on a fresh Dapper Install).

---

### Post by Malac on 2006-06-12
Firstly:
My Bad, I put the wrong folder in the copy command to load the firmware.
I'm Really, Really Sorry.
The section should read;(corrected section in **bold**).
```
[LEFT] cd /usr/src/cxacru-fw
 cp /usr/src/cxacru-fw/cxacru-fw.bin **/lib/firmware/2.6.15-23-386/cxacru-fw.bin**[/LEFT]
   
``` 
If you do not have the green link light shining constantly at any point then the modem is not loading the firmware.
If the firmware isn't loaded then with the corrected steps then try the following as your machine is a Mac.
--------
I am running a PC so I used the cnxetu.sys file for windows to create the cxacru-fw.bin file so it will probably be a different driver file for a Mac.
In which case you will have to run the cxacru-fw program with the Mac version driver file for the modem and use that created file.
Get the file from the modem installation CD and put it in the cxacru-fw folder in /usr/src.
Go to the cxacru-fw folder in terminal:
```
cd /usr/src/cxacru-fw
``` And type in:
```
./cxacru-fw [NameofMacDriverFile] cxacru-fw.bin
``` This will create a new cxacru-fw.bin file.
Then put the created file in **/lib/firmware/2.6.15-23-386** and /lib/hotplug/firmware.
Then Reboot.
Until you get the green light constantly lit there is no point doing any of the other steps.
I have altered the howto to reflect this.

Secondly:

Note This section from the howto:
Go to Filesystem: /etc/ppp/peers folder.
Open the file [COLOR=green]yourprovidername[/COLOR] by double clicking on it.
Change the "user=you@yourrealm" field to:
     

     [LEFT]```
"user=yourusername@yourprovidername"(without the quotes)
```   [/LEFT]
              
**  The only other things in this file should be**.

```

[LEFT][LEFT] plugin pppoatm.so
 noipdefault
 usepeerdns
 defaultroute
 persist
 noauth
 nopcomp
 noccp
 novj[/LEFT]
 [/LEFT]
 
```[LEFT]
[/LEFT]
              Save and Exit

Delete anything else or put a # infront of it to comment it out.
The 8.35 should be 0.38 for the UK but you don't need this either so delete or # it out.

If a line ```
connect "/usr/sbin/chat -v -f /etc/chatscripts/[COLOR=DarkGreen]yourprovidername[/COLOR]"
```  or
```
/dev/modem
115200
```  is at the bottom, delete or  # those as well.

Sorry should have made this clearer in the howto.

Once again **do not** use kppp, gnome-ppp or [System->Administration->Networking ]
or you will get these sorts of errors as they change the /etc/ppp/peers/yourprovidername file.

If still not working; double check all files listed in the howto are the same on your system, if that does not throw up any mistakes post the files here (minus sensitive info i.e. password/username) and I will give them a scan.

Hope this helps and all is working with these changes.

---

### Post by zxc on 2006-06-13
I'm only using a borrowed Mac laptop to access the internet while my Ubuntus internet isn't set up (Ubuntu is running on a PC).

I'm doing a fresh install and trying this tonight. Thanks again for your patience.

**Edit:**Failed again, modem wouldn't initialise (the Link L.E.D doesn't light up at all). I'm assuming this is driver side and not much can be done to rectify it.

Thanks for all your help but I think I'm going to surrender to Windows. :-(

---

### Post by Malac on 2006-06-14
Okay I am going to do a full install again from scratch just to get the green link light on.
Then post a "walkthrough" of just that process to see if that helps.
If the modem is actually working then there should be no reason this howto shouldn't work. If you can try it in windows to check that would be cool.

Is the modem detected in Ubuntu, [System->Administration->Device Manager], if not then I would suspect a dodgy USB cable even if the power light is on.

I've attached a screenshot of how my device manager looks, in case you don't know what to look for.

If not, try plugging it into a different USB port.
Or if it is plugged into a USB add-in PCI Card try the ones usually built on to the motherboard.
It could be the PCI card is the problem.

If you type ```
dmesg
``` into terminal after unplugging and re-plugging the modem you should see something similar to this:
```
[4295553.943000] usb 2-2: USB disconnect, address 3
[4295555.399000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[4295557.769000] cxacru 2-2:1.0: found firmware cxacru-fw.bin
``` 
Stick with it don't surrender to the lure of Windows. :)
The feeling of triumph when it finally works is worth it. \\:D/

---

### Post by Malac on 2006-06-14
Okay just changed the howto order so you aren't doing extra stuff before checking the link light is working.

I did a fresh install and followed these steps and the link light worked first time.
Give this a try then resume howto after the Reboot Section if all is well. 
Before commencing check the Red "Pwr" light is on if not then modem not working, check your USB connection, otherwise, carry on.

--------------------------------------------------------------------------------------------------
Login as normal user.
Run nautilus as root and gnome-terminal as root.
Choose [Applications->Accessories->Alacarte Menu Editor], scroll down to [System Tools] and activate [Root Terminal] and [Run as Different User], Close.
 Choose [Applications->System Tools->Root Terminal], then Enter Password.
 Choose [Applications->System Tools->Run as different user], type "nautilus"(without the quotes) in the box.
  DO NOT CLOSE THESE UNTIL THE END.

 ------ Dual-Boot Hard Disk Section, if folder is on a CD-R or floppy miss this section out -----
 In Nautilus
 Go to Filesystem:/mnt/, right-click on space, choose "Create Folder" and call it "win".
 In Terminal
 If Windows drive is the first partition (1) on C: (hda) then this should be sufficient:
[LEFT]```
mount /dev/hda1 /mnt/win
``` [/LEFT]
                           ----- End Section -----

 In Nautilus
 Go to FileSystem:/mnt/win/ or to the CD or to floppy.
Right-click the folder "adslusb" and choose copy.
Go to Filesystem:/usr/src/, right-click on space, choose "Paste".
Go to Filesystem: /usr/src/adslusb folder.
Open cxacru-fw.zip
Extract "cxacru-fw" folder to Filesystem: /usr/src
 [SIZE=-2](Using [Extract] choose "Other" in "Extract in Folder" pulldown
Browse to Filesystem:/usr/src, Click [Open] then [Extract])[/SIZE]
 
 In Terminal
    ```

 cd /usr/src/cxacru-fw
 cp /usr/src/cxacru-fw/cxacru-fw.bin /lib/firmware/2.6.15-23-386/cxacru-fw.bin
```[LEFT][LEFT]In Nautilus
[/LEFT]
  [/LEFT]
   Go to folder Filesystem: /etc/network.
           Open file "interfaces".
And insert the following at the bottom:
  ```
[LEFT][LEFT]# The ADSL connection
iface ppp0 inet ppp
    provider [COLOR=DarkGreen]yourprovidername[/COLOR]
    # enables ip forwarding (this is a gateway)
    pre-up echo 1 > /proc/sys/net/ipv4/ip_forward
    pre-up iptables-restore < /etc/iptables.up.rules

auto ppp0
```[/LEFT]
 

[LEFT]Reboot
[/LEFT]
           [/LEFT]
       -----------------------------------------------------------------------------------------------------------------------------------

Let me know what happens.

---

### Post by zxc on 2006-06-14
Ok still not working (the link light) but before and after your latest process I did dmesg and instead of showing info about cxacru it seemed to mention lots about eagle-usb (both before and after) and I think it was loading eagle-usb firmware :S.

---

### Post by Malac on 2006-06-14
That's weird as eagle-usb stuff isn't installed by default when I do a fresh install.
The eagle stuff definitely does not work with this modem that is one of the ones I tried with no success.
 Check in Synaptic and uninstall, it if it is listed.
 Did you note the corrected location for the cxacru-fw.bin file in folder /lib/firmware/2.6.15-23-386 not just /lib/firmware ?

I can't see why this would not be working from a fresh install for you but it does for me every time.
It is only two steps after the fresh install when all you get is the red "PWR" light.
1/. Put 'cxacru-fw.bin' in folder.
2/. Change 'interfaces' file and the green light comes on after rebooting.

I can only assume something else is interfering with the process on your system which is not on mine.
Either another usb device or I have read on one of the forums a sound module, "dabusb", can interfer with some usb modems.
Perhaps your system uses this.

Just to double check this is the slim dark grey Zoom 5510 you have not the white squarish one. For that one you need the eciadsl package.

---

### Post by zxc on 2006-06-14
Yup, it's the dark *cursed* grey 5510. (looks like [http://images.amazon.com/images/P/B0007LZGGU.01-A2R0FX412W1BDT.LZZZZZZZ.jpg](http://images.amazon.com/images/P/B0007LZGGU.01-A2R0FX412W1BDT.LZZZZZZZ.jpg))

And in Synaptic Eagle-usb isn't even installed. :-x 

And I've copied and pasted the commands so I don't think there's going to be an  error there (I did the corrected one for sure).

I pulled out all my Printers USBs so it's just my modem and my Flash Memory stick.

I'm not giving up quite yet...I'll probably try the reinstall a couple of times and hope for a miracle :) .

---

### Post by Malac on 2006-06-14
Okay the picture you linked to is not the same as my modem.
My modem is modem1.png
I think yours may be a moderner version of the modem2.png 
in which case the eciadsl drivers may work for you here is the URL
[http://eciadsl.flashtux.org/]("http://eciadsl.flashtux.org/")

Give that a try.
If not you will almost definitely have to run the cxacru-fw program on the driver file from your install CD that came with that modem.

If it is trying to install the eagle drivers by default it may be that they are the right drivers for your modem.
The latest version is available through sourceforge.net or try the synaptic ones.
Keep at it. :D

Please let me know _when_, not if,:D you succeed.
And good luck any help I can offer, I will.


For others reading this:
**modem3.png should work with latest eagle drivers from sourceforge.net**

---

### Post by srtck on 2006-07-04
I am using zoom 5510a modem and installed ubuntu-dapper.  I applied this walkthrough  today. Green light stayed on but when i run "pppd call myprovidername" command i am having following error. 
```
root@xxx:/home/yyy# pppd call myprovidername
Plugin /usr/lib/pppd/2.4.4b1/pppoatm.so loaded.
pppd: In file /etc/ppp/peers/myprovidername: unrecognized option 'user=myuserlogin'
```
Because of my isp, only thing i changed in your walkhrough is vpi and vci parameters.
I checked all of the settings but i am still having same error.

---

### Post by Malac on 2006-07-04
[quote=srtck]I am using zoom 5510a modem and installed ubuntu-dapper.  I applied this walkthrough  today. Green light stayed on but when i run "pppd call myprovidername" command i am having following error. 
```
root@xxx:/home/yyy# pppd call myprovidername
Plugin /usr/lib/pppd/2.4.4b1/pppoatm.so loaded.
pppd: In file /etc/ppp/peers/myprovidername: unrecognized option 'user=myuserlogin'
``` Because of my isp, only thing i changed in your walkhrough is vpi and vci parameters.
I checked all of the settings but i am still having same error.[/quote] 

Sorry the /etc/ppp/peers/[COLOR=DarkGreen]yourprovidername[/COLOR] file should read ```
user "[COLOR=DarkGreen]youruserlogin[/COLOR]"
``` there is no **=** sign and the quotes should be there this time.
I will amend the walkthrough.

Let me know if this works.

---

### Post by srtck on 2006-07-06
i corrected the file as you said and reboot.

```
root@xxx:/home/yyy# pppd call myprovidername
Plugin /usr/lib/pppd/2.4.4b1/pppoatm.so loaded.
Plugin pppoatm.so loaded.
```
So no there are no errors anymore.Then i opened the firefox but i could not connect anywhere.
It's weird. There must be something wrong.

---

### Post by Malac on 2006-07-06
That is strange, if all your files are now correct and no errors are being given when you dial it should work.
Sorry for the next bit but just to confirm you have got the 5510A modem pictured at the beginning of this thread and not one of the other ones.

Have you tried pinging an IP address from terminal (66.102.9.99 should be google)
if that connects but a ping to [www.google.com]("http://www.google.com") doesn't then it's a DNS problem, see other threads for problems with this.

The only other thing I can suggest is to redo the steps making sure all is as it should be or attach your files to this post and I will have a look at them.

---

### Post by srtck on 2006-07-06
OK. I fixed the problem i am online right now.
 In the options file least line must be same as my vpi and vci parameters.
Like this, 
```
plugin /usr/lib/pppd/2.4.4b1/pppoatm.so myvpi.myvci
```
I missed that point.

Thank you for all of support.

---

### Post by Malac on 2006-07-08
You're very welcome.
Happy Ubuntu-ing

---

### Post by gritpype on 2006-08-21
Apologies if this has been answered elsewhere, but:

I have followed this procedure, and it works fine - up until the point I want to use the internet. dmesg after completing all the steps produces a message telling me the line is up, and giving me the speeds. But the Internet still won't launch. 

Under Windows, the connection is over a routed RFC1483 connection to a static IP, not a dynamically assigned one. I assume this is the problem, as I have changed all the other parameters that need changing (VIP/VCP, etc.). What do I need to change?

All help gratefully received.

---

### Post by Malac on 2006-08-21
> **gritpype said:**
> Apologies if this has been answered elsewhere, but:

I have followed this procedure, and it works fine - up until the point I want to use the internet. dmesg after completing all the steps produces a message telling me the line is up, and giving me the speeds. But the Internet still won't launch. 

Under Windows, the connection is over a routed RFC1483 connection to a static IP, not a dynamically assigned one. I assume this is the problem, as I have changed all the other parameters that need changing (VIP/VCP, etc.). What do I need to change?

All help gratefully received.
You will need to change the /etc/network/interfaces file entry for the ppp0 connection to read:
```
 auto ppp0
     iface ppp0 inet static
     address 192.168.1.1
     network 192.168.1.0
     netmask 255.255.255.0
     gateway 192.168.1.254
     broadcast 192.168.1.255
```
replacing the values for your network: plus in /etc/cxacru file DEFAULT IP ADDRESS.
I think, you may have to do a search for assigning static IP to dialup modems.
Let me know if this works.

---

### Post by gritpype on 2006-08-22
Not yet, I'm afraid.

I'm not entirely sure what I should be putting for broadcast or network in /etc/network/interfaces

Can't ping anything either. Gah.

](*,)

---

### Post by gritpype on 2006-08-25
Done it! Only took me 10 days ...

Anyway, I should confess at this point that I'm using a different modem, and using your How-To as a jumping off point, combined with some other sources.

I will write my own How-To now for this modem and my provider.

---

### Post by Malac on 2006-08-25
=D>\\:D/Glad to hear you solved the problems and that my guide at least pointed you in the right direction. :)\\:D/=D>

---

### Post by zeus123 on 2006-10-28
Thanks for the Install guide! There is no way I would have got anything done without this!

Ive got a problem though im afraid.

First off, my modem doesnt use the eagle-usb chipset. If im right its just the 5510b which uses that.
[http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport](http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport)

I have the plain old 5510...
[http://www.zoom.com/techsupport/adsl/adsl_usb.shtml](http://www.zoom.com/techsupport/adsl/adsl_usb.shtml)

[http://www.zoom.com/datasheets/dsl-5510.shtml](http://www.zoom.com/datasheets/dsl-5510.shtml)

Ive followed the walkthrough but my modem never connects to the exchange, ie the flashing link (data on mine) always flashes.

I have been through the walkthrough three times and the only bit which confuses me is right at the beginning when it says.....
"just compile and run cxacru-fw and put extracted file in the cxacru folder)."

I cant compile it because doesnt seem to be a configure file in the download... 

Ive tried setting VCI=0.38 because in windows the phone number is 0,38! Also when I ran lpconfig /all in windows it said netmask was 255.255.255.255 so I tried that to instead of 255.255.255.0
Still no joy.

Ive also typed in my ip address because its always the same.

I should add that I have left it for over hours trying to connect!
Any help would be great!
Many Thanks

---

### Post by Malac on 2006-10-28
Hi zeus123,
Okay, just to clarify this is for the 5510A modem that you gave me in the first link:
[http://www.zoom.com/techsupport/adsl/adsl_usb.shtml](http://www.zoom.com/techsupport/adsl/adsl_usb.shtml)

If it looks like the one here:
[http://www.zoom.com/datasheets/dsl-5510.shtml](http://www.zoom.com/datasheets/dsl-5510.shtml)
Then this walkthrough probably won't work (as is) as I have no idea which driver that one uses, but if you have the driver disk for it you may be able to get it working by extracting the firmware from that file. It may not be called CnxEtU.sys though.

Sorry for having to check that but you never know. :)

To compile the cxacru-fw program open a terminal and cd to the folder you put the files and run the following command:```
gcc -o cxacru cxacru-fw.c
```Then rename the cxacru-fw.bin file in case you need to revert to it and run:```
./cxacru CnxEtU.sys cxacru-fw.bin
``` to extract the driver file.
If successful it should say something like:```
found firmware in `CnxEtU.sys' at offset 0x3e80
```This cxacru-fw.bin file can then placed in "/lib/firmware/<kernel-flavour>"
In my case I'm running Edgy generic so it goes in "/lib/firmware/2.6.17-10-generic".
I also put a copy in /lib/firmware so I can copy it quickly into any kernel upgrade folders. And finally one in /lib/hotplug/firmware for good measure. :)
Here is a paired down copy of /etc/network/interfaces file if you want to try this one. Remember to rename or backup your original one.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.1
    netmask 255.255.0.0
    network 192.168.1.0
    broadcast 192.168.1.255
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.1.1
    gateway 192.168.1.1

auto ppp0
iface ppp0 inet ppp
    provider supanet
    # enables ip forwarding (this is a gateway)
    pre-up echo 1 > /proc/sys/net/ipv4/ip_forward
    pre-up iptables-restore < /etc/iptables.up.rules
```Post #18 on page 2 is from someone with a fixed I.P. Address.
Check that post out for a possible solution.
But it sounds to me like the firmware isn't loading.

These two steps should be enough to get the light to come on.
If not then try removing all cxacru-fw.bin files in /lib/firmware/<kernel-flavour>, /lib/firmware and /lib/hotplug/firmware and rebooting then run:
```
dmesg tail | grep cxacru
``````
dmesg tail | grep ATM
``````
dmesg tail | grep ppp0
```and for good measure ```
ifconfig ppp0
```And post the output of each.

---

### Post by zeus123 on 2006-10-28
Thanks for your reply.

I had a look on my driver cd and there isnt a file called CnxEtU.sys included.... does this mean I need to extract from a different .sys?

I found in /usb/WAN Driver/dsldrv two .sys files.
gwausb.sys (windows says this is a "usb dsl driver" and...
gafwload.sys (windows says this is a "usb adsl firmware loader"

Itried running cxacru-fw using the gcc -o cxacru cxacru-fw.c command but it says I haven't got gcc! Its a fresh install.
If I leave the CnxEU.sys file in the extracted folder I still cant extract the .bin file.

Im using the "different user" and root terminal but if I dont right click on all the files and tick all the permissions boxes I get "permissions denied" messages.


I tried 
dmesg tail | grep cxacru
dmesg tail | grep ATM
dmesg tail | grep ppp0
and all just return the cursor to the next line; no text

ifconfig ppp0 said something about not finding firmware.

I'm sorry I couldn't quote any of the messages, Im swapping from windows to linux and forgot to write them down!

Am I right in thinking I need either the gwausb.sys or gafwload.sys files?

---

### Post by Malac on 2006-10-29
```
sudo apt-get install build-essential
```will install gcc, make, etc.
Frankly I don't know why these aren't installed by default as most people I know have had to do some compiling at some point.

Once cxacru is compiled, I'd run it on the gafwload.sys file as that is stated as the firmware file.
If that doesn't work try the other file, gwausb.sys, and see what happens. :)
But I don't recognise the names, they aren't on my Zoom driver CD.
A google search found they are associated with some SpeedTouch, D-Link, Ericsson and Zoom modems too.
They are distributed by GlobeSpan Inc. not Connexant, as my modem is, so your modem chipset may be different.
Because of this it may not work as the program may only work on Cnx.....sys files. I'm afraid I don't know as I didn't write the program.

As nothing was returned from dmesg try ```
dmesg tail | grep usb
```This should show any usb messages received.
If still nothing about your modem shows try unplugging the modem then re-plugging it in and run that command again. If nothing is showing up then your device isn't connecting with the usbcore stuff (whole other set of problems).
If you're green light is flashing though I think you will see something.
Try ```
ifconfig -a
``` too.
To save writing the output of the commands, re-direct it to a file by using```
dmesg tail | grep usb **> dmesg_out.txt**
```and ```
ifconfig -a **> ifc_out.txt**
```Then copy/move them somewhere you can get at them to post here (floppy or windows accessible folder).

I found this link for debian  GlobeSpan chipset drivers:
[http://dsl.linux.it/ChipsetGlobespan](http://dsl.linux.it/ChipsetGlobespan)
which says they work with eciadsl drivers
There are some in the repositories:```
sudo apt-get install eciadsl
```or can be downloaded here:[http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/)
In which case try ```
dmesg tail | grep eciadsl > dmesg_out.txt
``` to see if any eciadsl drivers are loading.

This may be another route to try.

Good luck.

---

### Post by zeus123 on 2006-11-05
Malac, 
    Many Thanks for your help and time in trying to get my modem to work.

Its up and running and im typing this from Ubuntu, my first proper Linux ditro (other than Linux From Scratch, believe it or not!)

I ended up having to use the link you posted as my Zoom 5510 is the version with the globespan chipset. The steps I took were....

Source code from...
[http://eciadsl.flashtux.org/download/nortek-2021/](http://eciadsl.flashtux.org/download/nortek-2021/)

./configure --prefix=/usr
make
make install

eciadsl-config-tk

Then set the settings, ie choose Modem and IP, login details. I also added my IP address and changed the VCI and VPI to 38 and 0 respectively.

Then as root I ran eciadsl-start and voila!

Strangely the compilation of source code only worked if I ran all three commands in the root terminal, I also have to run eciadsl-start as root. It might make sense to everyone else but I thought the only one id have to run as root would be "make install"

The drivers have to be the ones ive added a link to above. I did try the latest drivers but they didnt work. Synchronization errors were the problem.

Just to clarify which modem I have.... its the Globespan GS7070 5510. (thats 5510 with nothing else, not 5510b for example)
Here is a link....
[http://eciadsl.flashtux.org/modems.php?modem=21](http://eciadsl.flashtux.org/modems.php?modem=21)
Note that I just used the synchfile which was in the configuration setting by default. I think it was the GS7470 01 file where the eci website says something about file 09, and its abviously the GS7070. It worked fine so.....

Once again many thanks! Im sure if I couldnt have got the net working I would have gone straight back to windows even when all my work can be done in Linux!

---

### Post by Malac on 2006-11-05
Congratulations zeus123, glad I could help. :)

---

### Post by dolaksiz on 2007-04-08
Thank you very much for this walkthrough! I am surfing through the net with Ubuntu at last :) But I have aslight problem that I should ask.

I have two OS's installed on my computer. Windows XP Pro and Ubuntu. I made all the things on the walkthrough to install my modem on Ubuntu and it was OK. But now when I go back to Windows, I cannot connect to Internet. The "link" light flashes and then it stays on as usual, but I cannot access to any website. Why has this happened? How can I solve it ? Thanks..

---

### Post by Malac on 2007-04-08
> **dolaksiz said:**
> Thank you very much for this walkthrough! I am surfing through the net with Ubuntu at last :) But I have aslight problem that I should ask.

I have two OS's installed on my computer. Windows XP Pro and Ubuntu. I made all the things on the walkthrough to install my modem on Ubuntu and it was OK. But now when I go back to Windows, I cannot connect to Internet. The "link" light flashes and then it stays on as usual, but I cannot access to any website. Why has this happened? How can I solve it ? Thanks..
None of the steps to make the modem work in Ubuntu will have any effect on the modem when it is booted up using Windows XP.
The firmware should still be loaded from the normal Windows .sys files.
Have you changed your firewall settings or done any internet related updates in Windows?
I suspect this will be completely unrelated to the Ubuntu install for the modem.

---

### Post by dolaksiz on 2007-04-08
No I haven't made a change at all in Windows. But now I looked at the settings in the Windows' device manager and saw that "Zoom USB Network Adapter" is deactivated. I activated it and now I can access Internet. So how did it disable itself?

And now when I try to start up Ubuntu, it does not log in! It locks up at the start of Ubuntu (the screen where we see the progress bar). I plugged out the modem and restarted and there is no problem, I can login to Ubuntu :) What can be the problem, it is strange that when it works for one OS it does not work for the other :)

---

### Post by Malac on 2007-04-08
> **dolaksiz said:**
> No I haven't made a change at all in Windows. But now I looked at the settings in the Windows' device manager and saw that "Zoom USB Network Adapter" is deactivated. I activated it and now I can access Internet. So how did it disable itself?

And now when I try to start up Ubuntu, it does not log in! It locks up at the start of Ubuntu (the screen where we see the progress bar). I plugged out the modem and restarted and there is no problem, I can login to Ubuntu :) What can be the problem, it is strange that when it works for one OS it does not work for the other :)
I can only think that if you reboot from one OS to another it isn't clearing the firmware. If you are switching from one OS to the other you may be better shutting down then restarting so the modem firmware is reset for each OS.
The firmware maybe you are using for Ubuntu may be a different version try copying the CnxEtU.sys one from the Windows install, running the cxacru program on it and use the extracted one in Ubuntu to make sure they are the same versions.

---

### Post by dolaksiz on 2007-04-11
Yes reseting the modem at each startup fixes the problem, thanks!

But now i have this problem. In the "System Log" view on Ubuntu, I can see an error message every 5 seconds and it is annoying

... kernel [some numbers]: ATM dev 0: poll status: error -5

it is posting repeatedly every 5 seconds! I know this is because of cxacru driver because in the source code of this driver there is a function that puts this error.

What can be the cause and how can I fix it? Thanks..

---

### Post by Malac on 2007-04-12
> **dolaksiz said:**
> Yes reseting the modem at each startup fixes the problem, thanks!

But now i have this problem. In the "System Log" view on Ubuntu, I can see an error message every 5 seconds and it is annoying

... kernel [some numbers]: ATM dev 0: poll status: error -5

it is posting repeatedly every 5 seconds! I know this is because of cxacru driver because in the source code of this driver there is a function that puts this error.

What can be the cause and how can I fix it? Thanks..
I have that too, I have never bothered to fix it as it hasn't bothered me since I did the first install on Breezy. I will look into it if I can get the time. :)

---

### Post by lenzino on 2007-06-16
Hii, I got a ADSL USB Modem UTStarcom UT-300U the chip set is conexant v2. I tried to follow your How-To. The modem lights up continually. the modem shows up in the hardware list but . when i run 

pppd call myprovidername
Plugin /usr/lib/pppd/**2.4.4**/pppoatm.so loaded.
Plugin pppoatm.so loaded.

Note the bold area is 2.4.4 it is different from what u have said in the how to which is 2.4.4b1. I did this because there is no folder called 2.4.4b1.Is this ok?

I tried to ping the IP address you u gave but it says no connection to network.

I'm running Ubuntu 7.04 (Feisty Fawn)  I have attached screen shots with the details of my modem. Can you please tell me how to get this modem working.

[IMG]http://farm2.static.flickr.com/1092/555141308_4aa9e7a2f8.jpg?v=0[/IMG]
[IMG]http://farm2.static.flickr.com/1389/555141302_4ab1d499b1.jpg?v=0[/IMG]

Good Luck
Julian Leoanrdo

---

### Post by Malac on 2007-06-16
@Lenzino
Have you tried the eagle-atm drivers or the eciadsl drivers?

---

### Post by CalonDdraig on 2008-01-14
Hi Guys,

I've followed the above steps as directed, but all I get is this when I try to connect:

[FONT="Fixedsys"]dafydd@Tyr:/etc/network$ pppd call Orange
Plugin /usr/lib/pppd/2.4.4/pppoatm.so loaded.
Plugin pppoatm.so loaded.
dafydd@Tyr:/etc/network$ [/FONT]

Any ideas what I've done wrong? Its a 7.10 system btw..

No idea what I'm doing with this so please help...

~Calon

---

### Post by katsolimon on 2008-02-24
thanks a lot for the tutorial, i have 6.06 lts and it took me 10 minutes to get online.

---

### Post by Malac on 2008-02-25
> **katsolimon said:**
> thanks a lot for the tutorial, i have 6.06 lts and it took me 10 minutes to get online.I'm glad it worked for you. Happy Ubuntu-ing :).

To ~Calon, if you still need help I can try and help you through it.
I've been moving house so have been offline for weeks so didn't notice your post.

---

