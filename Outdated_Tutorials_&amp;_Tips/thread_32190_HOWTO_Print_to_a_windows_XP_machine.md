---
title: "HOWTO: Print to a windows XP machine"
date: 2005-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by orion_114 on 2005-05-06
_**How to setup your Ubuntu machine so it can print to a Windows XP shared printer**_

It was suggested that I add this from the following thread:
[http://ubuntuforums.org/showthread.php?t=24887&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=24887&page=1&pp=10)

_Step 1: Installing Samba on Ubuntu_
[list]
[*]Click System -> Administration -> Synaptic Package Manager
[*]Enter your password
[*]Now click Search and type Samba in the search box.
[*]You should now see a list of items containing the word Samba.
[*]Right click on the Samba with the little ubuntu icon on it and select mark for installation.
[*]Click apply
[*]The packages will now be downloaded and installed.
[/list]  

_Step 2: Checking if your network is working_
[list]
[*]Find the ip address of your windows xp machine by going ... start -> run
[*]Then type cmd
[*]type ipconfig in this window and you should see your ipaddress there.
[*]Now on your ubuntu machine goto the command line
and type ping <your windows ip address>
[*]see if you get a response.
[/list]
if you get timeouts:  [-X 
  a.) Check if your network cables are all connected
  b.) Check if your network cards are working
  c.) Check the settings of your network interfaces
  d.) Try disabling any firewall software

_Step 3: Sharing the Windows XP printer_
[list]
[*]start -> settings -> control panel
[*]open printer and faxes
[*]find the printer you wish to share with your ubuntu machine
[*]Right Click -> properties on it and goto the sharing tab.
[*]Click on share this printer and type a short name in the share name box.
[/list]

_Step 4: Adding the printer on the Ubuntu machine_
[list]
[*]System -> Administration -> Printing
[*]Click Printer -> Add Printer
[*]Click on network printer.
[*]Select Windows Printer (SMB) from the dropdown.
[*]In the host section type the IP address of your windows machine.
[*]In the printer section type the share name you gave your printer
[*]Now enter your username and password for your ubuntu machine.
[*]Click forward.
[*]Now select the manufacturer and model of your printer.
[*]And finally click on Apply.
[/list]

Hope you get it workin !!  \\:D/

---

### Post by kyroha on 2005-05-06
Works like a charm, 
many thanks

---

### Post by MetalMusicAddict on 2005-05-06
You helped my with **MY** missing piece. ;)

---

### Post by thecrimsonking on 2005-05-06
By default "Print Services for Unix" are not installed on XP.
You must install *and* manually turn on this service from the MMC before you can print to XP.

I have never been able to print to an XP machine (from linux) before turning this on.  

Now I will sit back and wait for all the people telling me they do it all the time  :roll:

---

### Post by davidmigl on 2005-05-07
Well, now that I have the package installed, now I need to get the driver!  Which, from a few searches looks pretty impossible, considering that none of Canon's new printers seem to be supported.

Oh well; to me, priting from ubuntu isn't a big deal anyway, since I have a windows machine that I use exclusively.

Still, if anyone knows where I could find Linux drivers for a Canon Pixma ip300, it would be greatly appreciated.

---

### Post by plewisfdx on 2005-05-07
A lot of drivers are found at:

[www.turboprint.de/english.html](www.turboprint.de/english.html)

I have a Canon i350, and thats the only place I found a driver for it.  It is not free, but they have a free trial, I think.

---

### Post by kvidell on 2005-05-07
Now what's cool is that it prints... but it only uses a quarter of the page's available realestate. Scales it down to a quarter of the page size and squats it in the top left corner.
Why must they not have the driver for my printer? (Canon MultiPass MP390)
Evil.

Essentially works though, so good on ya :) Thanks!
- Kev

---

### Post by benplaut on 2005-05-07
what do you mean by 'user and password', the login you use with Ubuntu?

---

### Post by kvidell on 2005-05-07
[QUOTE=benplaut]what do you mean by 'user and password', the login you use with Ubuntu?[/QUOTE]
 That's what worked for me.

---

### Post by tseliot on 2005-05-08
[QUOTE=thecrimsonking]By default "Print Services for Unix" are not installed on XP.
You must install *and* manually turn on this service from the MMC before you can print to XP.

I have never been able to print to an XP machine (from linux) before turning this on.  

Now I will sit back and wait for all the people telling me they do it all the time  :roll:[/QUOTE]

Hi! I've installed "Print Services for Unix" on my XP, so how can I turn it on (what's the MMC?)?
Even if my windows printer is shared I can't print to my windows machine from Kubuntu. The only way I can do it is by using Win4lin  and running Win98 (where it recognises my hp3420, as it can see it) and printing from there. 

Otherwise when I try to print, my printer just makes some noise without printing.

Please help me

---

### Post by Arthemys on 2005-05-08
[QUOTE=thecrimsonking]By default "Print Services for Unix" are not installed on XP.
You must install *and* manually turn on this service from the MMC before you can print to XP.

I have never been able to print to an XP machine (from linux) before turning this on.  

Now I will sit back and wait for all the people telling me they do it all the time  :roll:[/QUOTE]

To be honest with you, I've never installed that service and it's just worked for me. Because my impression is that those print services for unix are there for if you don't want to use samba to print through, and use CUPS or something similar. Samba does all of the legwork while Windows sits there and just about drools as it dishes out SMB packets for samba.

---

### Post by tseliot on 2005-05-08
[QUOTE=Arthemys]To be honest with you, I've never installed that service and it's just worked for me. Because my impression is that those print services for unix are there for if you don't want to use samba to print through, and use CUPS or something similar. Samba does all of the legwork while Windows sits there and just about drools as it dishes out SMB packets for samba.[/QUOTE]

Thanks for the answer (and for your honesty). I'm a linux newbie and I can't get my network printer work despite having followed this guide and other ones (from other websites).

Can anybody help me? It's quite annoying having to start win4lin everytime I need to print a document.  ](*,)  (and I don't want to go back to wind**s! I hate it!)

---

### Post by gunnyman on 2005-05-08
I could never get samba printing to work either  so I turned on Unix Print services on my XP box.
THAT worked like a charm.
For any wondering how to do it, go to Control Panel in XP, click on  Add Remove programs, click on Add Windows components.
Click on Other Network file and print services.
This turns on Unix print services.
Now when adding the printer choose Unix LPD printer
The host is the ip address of the XP computer and the queue name is the name of the printer in Window (the share name)

Samba works great for sharing my files between machines, but not so good for printing at least for me.

---

### Post by tseliot on 2005-05-08
[QUOTE=gunnyman]I could never get samba printing to work either  so I turned on Unix Print services on my XP box.
THAT worked like a charm.
For any wondering how to do it, go to Control Panel in XP, click on  Add Remove programs, click on Add Windows components.
Click on Other Network file and print services.
This turns on Unix print services.
Now when adding the printer choose Unix LPD printer
The host is the ip address of the XP computer and the queue name is the name of the printer in Window (the share name)

Samba works great for sharing my files between machines, but not so good for printing at least for me.[/QUOTE]

I've done as you've told me but  the printer won't even print a test page (during the configuration on XP) on my XP machine. Any ideas?

---

### Post by gunnyman on 2005-05-08
Make sure the Printer itself is shared.

---

### Post by tseliot on 2005-05-08
Ok, I've shared it on XP.

Now, back to kubuntu, what kind of printer shall I choose? (just to make sure I'm doing the right thing)

LPD server or what?

---

### Post by gunnyman on 2005-05-08
[QUOTE=tseliot]Ok, I've shared it on XP.

Now, back to kubuntu, what kind of printer shall I choose? (just to make sure I'm doing the right thing)

LPD server or what?[/QUOTE]

Yes LPD

---

### Post by tseliot on 2005-05-08
Ok I've selected RLPR Environment (Remote LPD servers) 
(no plugin information available)

When I try to print a test page here's the error:

A print error occurred. Error message received from system:

/usr/bin/rlpr -H '192.168.0.2' -P 'unix' -\#1 '/usr/share/apps/kdeprint/testprint.ps' : execution failed with message:
/usr/bin/rlpr: error: connect to 192.168.0.2:51 : Connection refused /usr/bin/rlpr: fatal error: client_open(): cannot connect to lpd 


(192.168.0.2 is the Ip of  the XP machine, and "unix" is the name of its printer)

What's wrong?

Thanks in advance (I'm sorry for being such a noob)

---

### Post by gunnyman on 2005-05-08
Is Window's XP firewall on?

---

### Post by tseliot on 2005-05-08
Windows firewall is not active. But Norton Internet Security 2005 is active. On top of that  Ubuntu and XP are linked through a Router (netgear) and a switch (netgear).
Shall I do anything in particular?

---

### Post by gunnyman on 2005-05-08
Make sure the Ubuntu box has permission to use resources on the XP machine.
Make sure the router and the nortons stuff aren't blocking anything.

---

### Post by benplaut on 2005-05-08
OK... the firewalls are off

i installed print services for Unix, and set the printer to share (with the name, Printer)

i went back to the laptop (connected via wifi and a Planet router), and was able to ping the desktop, 192.168.0.3

i set up the printer with Unix LPD, using 192.168.0.3 as the host, and Printer as the Queue.

Didn't work.

tried with Windows (SMB) using my Ubuntu login, 192.168.0.3 as the host, and Printer [as the printer].

the printer makes all its warm-up noises, but doesn't actually print. the windows machine says that it is an invalid print type...

it keeps trying a few times, and i turn it off

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

BTW, HP PSC 1210v

---

### Post by tseliot on 2005-05-08
[QUOTE=benplaut]OK... the firewalls are off

i installed print services for Unix, and set the printer to share (with the name, Printer)

i went back to the laptop (connected via wifi and a Planet router), and was able to ping the desktop, 192.168.0.3

i set up the printer with Unix LPD, using 192.168.0.3 as the host, and Printer as the Queue.

Didn't work.

tried with Windows (SMB) using my Ubuntu login, 192.168.0.3 as the host, and Printer [as the printer].

the printer makes all its warm-up noises, but doesn't actually print. the windows machine says that it is an invalid print type...

it keeps trying a few times, and i turn it off

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

BTW, HP PSC 1210v[/QUOTE]

We have the same problem... I've got to sleep now (it's night in Italy). 
See (ehm... write) you all tomorrow.

---

### Post by dewey on 2005-05-08
I had to use LPD and enable Unix Printing services to print from Hoary to XP SP2, using a Hewlett Packard P1115

---

### Post by tseliot on 2005-05-09
I've disabled windows firewall, norton internet security firewall, and my router netgear doesn't seem to prevent communication between Kubuntu and Xp (as I can print from the Win4lin emulator which makes me run Win98 under kubuntu).
It doesn't work, I can't print (without the emulator) neither using samba nor with LPD.

Any ideas? Please... ](*,)

---

### Post by RastaMahata on 2005-05-09
woah, worked like a charm. ;)

Thanks for the HOWTO

---

### Post by jrobcet on 2005-05-09
[QUOTE=tseliot]I've disabled windows firewall, norton internet security firewall, and my router netgear doesn't seem to prevent communication between Kubuntu and Xp (as I can print from the Win4lin emulator which makes me run Win98 under kubuntu).
It doesn't work, I can't print (without the emulator) neither using samba nor with LPD.

Any ideas? Please... ](*,)[/QUOTE]

I'm not sure if it will help you, but I finally managed to print to an XP machine by finding the appropriate PPD file for my printer. 

You are trying to print to a HP 3420, correct? If so, you can get the the PPD file here:
[http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-DeskJet_3420&show=0](http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-DeskJet_3420&show=0)

Once you get the PPD file, open a terminal and and cd to the directory containing the file you just downloaded and copy it to the following location like this:
```
sudo cp HP-DeskJet_3420-hpijs.ppd /usr/share/cups/model
```Or if you would rather not a use a terminal, you can install the printer driver by clicking on the "Install Driver" button in Step 2 of the printer configuration utility and then navigating to the PPD file. 

Like I said, I'm not sure if it will help you out, but it certainly won't hurt to try.

---

### Post by wormeyman on 2005-05-09
Printing: Network host '192.168.0.2' is busy, down, or unreachable; will retry in 30 seconds...

I get that error?

---

### Post by jonny on 2005-05-09
I've successfully set up several printers in the manner described by this how-to (not directly, though - the how-to came too late for me).  Here are a few things that helped me:

1. Set up the printer as a Windows Printer (SMB).  You'd use LPD if you were connecting through a print server.
2. Ubuntu expects you to specify a user name and password: if you're attaching to an XP Home Edition PC, this is ignored; if you're attaching to an XP Professional machine, you must specify a user name and passsword that's valid on the target Windows machine
3. Do check out linuxprinting.org; Ubuntu doesn't always default to the best printer driver.  HP printers are generally well supported, but I had to google to get a ppd file for the office HP Color Laserjet.
4. I always switch off all firewalls before I start.  I'm much too stupid to configure firewalls correctly the first time around.

One final tip that makes my home network much more productive: I dual boot the target machine, so I've also installed samba server and shared the printer through linux using samba.  By giving the printer the same name in both operating systems, I'm able to print without first running up the stairs to find out which operating system is currently running.

---

### Post by jonny on 2005-05-09
[QUOTE=jrobcet]Once you get the PPD file, open a terminal and and cd to the directory containing the file you just downloaded and copy it to the following location like this:
```
sudo cp HP-DeskJet_3420-hpijs.ppd /usr/share/cups/model
```[/QUOTE]I'm sure that works, but if, you prefer to opoint and click, Step 2 of the Gnome New Printer wizard gives you the option to install the driver from a file.

---

### Post by jrobcet on 2005-05-09
[QUOTE=jonny]I'm sure that works, but if, you prefer to opoint and click, Step 2 of the Gnome New Printer wizard gives you the option to install the driver from a file.[/QUOTE]

Thanks for pointing that out.  I just never noticed that option. When it comes to *nix, I generally feel more comfortable using a terminal to accomplish many things - especially when it comes to moving files around.

---

### Post by tseliot on 2005-05-10
I've tried both using the new driver and using the username and password of an XP user (I use XP Pro) It doesn't work.  In the print manager (on XP) it says:
"remote document with low priority" (this is the translation into English, as my XP is in Italian), and the user who sent the document (according to XP) is "Guest  even if I use another user and password.

What's the problem?

---

### Post by gdel on 2005-05-10
I too am a newby.  Here is how I got my printer on XP to work.

Even though I am using Gnome, I used Synaptic to also d/l KDE (OK, start flameing, but it was the only way I could get my printer to work!)  [-X 
Once I had KDE, I rebooted into Ubuntu using KDE.

- Log into the Printer wizard as Administrator.

- When you launch the Add printer wizard, choose SMB shared printer.

- In the next screen(user identification), choose Anonymous(no login/no password)

- Proceed to the next screen, and SCAN your network.(This is where you will get the NT_ACCESS_DENIED message if you try to access your Windows network)

- Now Don't touch anything, and go BACK one step to the previous screen (User identification).

- In the user identification screen, choose guest(login = "guest").

- Proceed to the next screen. DO NOT repeat a scan. Just try to access your Windows network in the displayed tree. You should magically see your Windows printer appear without any whining about access.

I have a Canon i550 and have found that BJC-8200 works OK.

Once you have your printer set up, you can log out and log back in under Gnome if you wish.

KDE seems to be a lot easier to use for setting up a Windows printer than Gnome.  At least it worked for me. :)

---

### Post by tseliot on 2005-05-11
[QUOTE=gdel]I too am a newby.  Here is how I got my printer on XP to work.

Even though I am using Gnome, I used Synaptic to also d/l KDE (OK, start flameing, but it was the only way I could get my printer to work!)  [-X 
Once I had KDE, I rebooted into Ubuntu using KDE.

- Log into the Printer wizard as Administrator.

- When you launch the Add printer wizard, choose SMB shared printer.

- In the next screen(user identification), choose Anonymous(no login/no password)

- Proceed to the next screen, and SCAN your network.(This is where you will get the NT_ACCESS_DENIED message if you try to access your Windows network)

- Now Don't touch anything, and go BACK one step to the previous screen (User identification).

- In the user identification screen, choose guest(login = "guest").

- Proceed to the next screen. DO NOT repeat a scan. Just try to access your Windows network in the displayed tree. You should magically see your Windows printer appear without any whining about access.

I have a Canon i550 and have found that BJC-8200 works OK.

Once you have your printer set up, you can log out and log back in under Gnome if you wish.

KDE seems to be a lot easier to use for setting up a Windows printer than Gnome.  At least it worked for me. :)[/QUOTE]
Sorry but it didn't work for me. And I didn't get "NT_ACCESS_DENIED" error

Perhaps my case is impossible to solve... Any ideas?

---

### Post by jrobcet on 2005-05-11
[QUOTE=tseliot]Sorry but it didn't work for me. And I didn't get "NT_ACCESS_DENIED" error

Perhaps my case is impossible to solve... Any ideas?[/QUOTE]

Can you post your printer config file ( /etc/cups/printers.conf )? Just make sure to change the password contained in the file before you post it.

---

### Post by tseliot on 2005-05-12
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Thu May 12 11:11:06 2005
<DefaultPrinter hpsamba>
Info HP HP DeskJet 3420 hpijs
Location 
DeviceURI smb://guest@192.168.0.2/hpdeskjet
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
<Printer hpunix>
Info HP HP DeskJet 3420 hpijs
Location 
DeviceURI lpd://192.168.0.2/unix
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

I've used "guest" user ( but I've also tried with user and password). 
P.S. Guest is enabled in my XP machine

---

### Post by jrobcet on 2005-05-12
Hmmm....There are a couple of things in that file that seem to differ from the norm. Just to satisfy my own curiosity, would you be willing paste the following over what you currently have in your config file?

```
<DefaultPrinter DeskJet-3420>
Info DeskJet-3420
DeviceURI smb://XP_username:XP_password@192.168.0.2/hpdeskjet
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
```**NOTE:** Make the appropriate changes to "XP_username:XP_password" before saving the file.

Then restart CUPS:```
sudo /etc/init.d/cupsys restart
```Try it out and see if you can print. If it still won't work, I think we will need to completely start over and walk through the entire process step-by-step.

Also, I just read through this thread again and noticed that the XP machine you are trying to print to is running Norton Internet Security. I have seen this particular program cause strange problems - it sometimes blocks incoming requests even when it has been disabled. Would you be willing to uninstall it temporarily for troubleshooting purposes if needed?

---

### Post by tseliot on 2005-05-12
I've done:
sudo /etc/init.d/cupsd restart
That's what I get:
sudo: /etc/init.d/cupsd: command not found

What's wrong?

---

### Post by jrobcet on 2005-05-12
Try this instead:```
sudo /etc/init.d/cupsys restart
```Sorry about that  :-?

---

### Post by tseliot on 2005-05-12
Ok maybe you meant
 /etc/init.d/cupsys restart

I'll try again

---

### Post by tseliot on 2005-05-12
Ok, I've done as you said.

Here's what my XP machine says if I go to the "printers"  menu (to check the queue)
Low priority document (as before)       Print Error (this is new)

Now my printer doesn't make any noise.

P.S.
One thing I had noticed before (with my old printers.conf)
My Xp machine reported "Low priority document" but the size of the document was wrong, (i.e. 14k/3,44MB but the real dimension was 14kb)  and it seemed XP was still waiting for the rest of the document but the process never ended and I had to turn the printer off in order to get rid of the document in the queue.

Now I can abort the printing process (without turning the printer off) and the size of the document is reported correctly (14kb).

I hope my English (and my description) is clear enough.

About uninstalling Norton: the problem is that the XP machine is my father's (and he uses almost 24/7, and he's always connected; I don't know if I can persuade him to uninstall it...

---

### Post by jrobcet on 2005-05-12
Post the output, if any, from the following:```
lpr -P DeskJet-3420 /usr/share/apps/kdeprint/testprint.ps
```

---

### Post by tseliot on 2005-05-13
Ok I've done as you said.

If you want to see the image

[ftp://tseliot.95mb.com/linux/](ftp://tseliot.95mb.com/linux/)

username: tseliot.95mb.com
password: alb0704

there's only one screenshot. It's in Italian but you will understand as it matches what I've translated before

Reply ASAP and tell me what you think, please

---

### Post by jrobcet on 2005-05-13
Ok....I have good news and bad news. I was looking for something at work yesterday and happened to come across an HP Deskjet 3420 - maybe I should have bought a lottery ticket yesterday   :smile: 

The bad news is that I connected the printer to an XP machine and never could print to it from my ubuntu machine. I finally gave up and decided to connect it directly to the ubuntu machine. It would print fine sometimes but at other times it either refused to print or printed blank pages.

Of course the good news.......it would appear this problem is not isolated to you. I haven't had time to take a look at it yet, but my suggestion is to take a look here:
[http://hpinkjet.sourceforge.net/](http://hpinkjet.sourceforge.net/) 
Maybe you can find some info that would help.

---

### Post by tseliot on 2005-05-13
Thanks for the link.

If I find a way to make my printer work I'll post it.

Thanks for your time

---

### Post by tseliot on 2005-05-16
If I tipe  "smbclient -L 192.168.0.2 -N" in the terminal (if I use the XP name it doesn't work) her's what I get


Domain=[IO] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      Condivisione predefinita
        IPC$            IPC       IPC remoto
        D$              Disk      Condivisione predefinita
        SharedDocs      Disk
        print$          Disk      Driver della stampante
        D               Disk
        C               Disk
        hpdeskjet       Printer   hp deskjet 3420 series
        G$              Disk      Condivisione predefinita
        F$              Disk      Condivisione predefinita
        E               Disk
        F               Disk
        G               Disk
        ADMIN$          Disk      Amministrazione remota
        C$              Disk      Condivisione predefinita
        J               Disk
        unix            Printer   unix
session request to 192.168.0.2 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[IO] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

The name of my XP machine is "IO" but Ubuntu thinks "IO" is the Domain name. Could this be the real problem?

---

### Post by jrobcet on 2005-05-17
[QUOTE=tseliot]The name of my XP machine is "IO" but Ubuntu thinks "IO" is the Domain name. Could this be the real problem?[/QUOTE]

That looks normal - it shouldn't be a problem.

I had another thought yesterday. I'm not sure where I saw it now, but I remember someone solving a problem similiar to this by disabling bidirectional support for the printer. It certainly won't hurt to give it a try. 

To disable it, go to printer properties on the XP machine (right click the printer and choose Properties). Click the Ports tab and uncheck "Enable bidirectional support".

---

### Post by penvzila on 2005-05-17
I've been exporting/printing to .pdf, copying it to a network drive, and walking over to my windows box to print.  I will try some of the things in this thread when I get home.

---

### Post by tseliot on 2005-05-18
[QUOTE=jrobcet]

To disable it, go to printer properties on the XP machine (right click the printer and choose Properties). Click the Ports tab and uncheck "Enable bidirectional support".[/QUOTE]

You're great, man! This solved my problem  \\:D/ . Thanks. 

Perhaps this should be added to the "HOWTO".

Thanks again.

---

### Post by jrobcet on 2005-05-18
Great! I'm glad you finally got it working  :)

---

### Post by Julius on 2005-05-18
Finally this has worked for me. THe only thing I was missing was the username and password. Who'd have thought that it was, in fact, your ubuntu username? I would have never guessed it!  NOw it works

THANKS!

---

### Post by Oblivious Hazard on 2005-05-19
ok, Ive tryed everything is this thread.... And I get this error...
Paused: Can't load /etc/samba/smb.conf - run testparm to debug it

> testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Global parameter wins support found in service section!
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services.

? I'm lost

---

### Post by Oblivious Hazard on 2005-05-19
I found out what was wrong... I forgot I had setup this computer to be the server in that cfg. so i whent back and edtied it, and now it works fine...

---

### Post by Dex on 2005-05-28
jrobcet - you ARE due many six packs, man. Disable bi-directional printing what did it for me, too. Thank you for being such help. Works like a champ \\:D/

---

### Post by allforcarrie on 2005-05-28
[QUOTE=gunnyman]I could never get samba printing to work either  so I turned on Unix Print services on my XP box.
THAT worked like a charm.
For any wondering how to do it, go to Control Panel in XP, click on  Add Remove programs, click on Add Windows components.
Click on Other Network file and print services.
This turns on Unix print services.
Now when adding the printer choose Unix LPD printer
The host is the ip address of the XP computer and the queue name is the name of the printer in Window (the share name)

Samba works great for sharing my files between machines, but not so good for printing at least for me.[/QUOTE]


I spent about an hour trying to get my printer set up, I can't belive i didn't think of this. My problem is that i have a C66, and there are no drivers for it. I loaded the c64 but that doesnt seem to work.  ](*,)

UPDATE*   I connected to the printer, when i tell it to print it just cycles all my paper threw and doesnt print.... any ideas?

---

### Post by drew_t on 2005-06-05
Thanks to Orion_114 for the How-To.  I would suggest adding, in Step 3, after "find the printer you wish to share with your ubuntu machine," something like the following:  **Verify that the printer's status is indicated as "ready."**  

I wasted quite a bit of time tinkering with the Ubuntu machine ](*,) before I finally noticed that the XP machine showed the printer to be "off-line."  The USB cable had simply gotten yanked out of the port on the back of the XP machine.   :oops:   Once the printer was actually connected to the XP machine, printing from the Ubuntu machine worked just fine.  \\:D/

---

### Post by FesterHead on 2005-06-22
Enabling bi-directional printing on the Windows XP Professional SP1 shared printer, installing 'other network file and print services' and selecting a network printer with LPD specifying the host (192.168.2.4 in my case) and the Windows shared name (hp psc 2400 series) with the appropriate hp psc 2400 drivers did it for me.

Drove me nuts for awhile until I tried a few things from this thread.

---

### Post by DarkManX4lf on 2005-07-09
hi, i have two computers(one windows xp and the other ubuntu linux), along with a xbox, the winodws local machine ip is 192.168.0.103, i followed this guide to its word and it doesnt work, the printer is a HP OfficeJet G55, i made sure that i selected that printer in the setup....also this printer is connected to the winodws machine via usb, i cant seem to print from it.

---

### Post by antilog on 2005-07-11
works great.  finally got my hplj1000 working.

i was unable to get it working connected directly to my ubuntu box, so i thought i would try connecting it my windows pc and sharing to my ubuntu box.

apparently windows is still needed....

ugh.

---

### Post by Sionide on 2005-07-11
What if it's a Windows 98 machine? :(

---

### Post by slade_slater on 2005-07-12
One thing I like to do with it is to make a dummy account on my XP box called "printer" and then remove it from all groups so it has no privileges.  Then I go to my printer share on my XP box and put in the "printer" account under the share permissions.  Then I just specifically give "printer" the ability to print.  You could have "printer" manage documents/jobs etc. too...  I don' t know if it matters much anymore, but when you used to print to a windows box using samba, the linux box would usually send the password in cleartext.  Like I said, this may no longer be necessary?  If it is not, please correct me...   :)  Great guide, BTW...

---

### Post by Blob on 2005-07-24
Wow, you guys just blow me away! I thought it would be an ordeal to print from my Ubuntu laptop. I just followed the many directions--and I'm printing wirelessly and flawlessly. All in about 30 minutes. Unreal! Linux rocks and Linux geeks rock even more! Thank you all so much!!!!!!

BTW, when you change your IP address, it does not keep it. you have to start over and install a new printer with the correct IP address. That is why it took me 30 minutes to get it to work-I put down the wrong IP address and when I corrected it, it would not retain it. I just started from scratch and it worked instantly. As such, it would have only  taken 5 minutes to be up and printing .... :-)  :-)  :-)

---

### Post by webbie180 on 2005-07-24
[QUOTE=Blob]Wow, you guys just blow me away! I thought it would be an ordeal to print from my Ubuntu laptop. I just followed the many directions--and I'm printing wirelessly and flawlessly. All in about 30 minutes. Unreal! Linux rocks and Linux geeks rock even more! Thank you all so much!!!!!!

BTW, when you change your IP address, it does not keep it. you have to start over and install a new printer with the correct IP address. That is why it took me 30 minutes to get it to work-I put down the wrong IP address and when I corrected it, it would not retain it. I just started from scratch and it worked instantly. As such, it would have only  taken 5 minutes to be up and printing .... :-)  :-)  :-)[/QUOTE]
 I followed the steps in the 1st post and got the required results.  Trying to print a test page but got this error message, NT_STATUS_LOGON_FAILURE, wat's does that mean and how to correct it?

---

### Post by bertros on 2005-07-26
I too am a newbie who is trying to get my Ubuntu box to print to a printer on my XP box.  I have TurboPrint installed because I have a Canon MP750 printer, and I haven't seen the driver anywhere else. 

My problem is:  when I go to Printers>>Properties>>Connections, there is a password in the field that I don't think I put there.  It is 5 characters long (which I don't use), and when I delete it, it comes right back.  There is no password in the connections section of TurboPrint setup.

In the past, when I was using a different Ubuntu box, I was able to print to an Epson printer on my XP box as long as the username and password fields were blank, and guest access was allowed on my XP printer.  In that case I had not installed TurboPrint.

Any ideas where that password is coming from and how I can get rid of it?
When I try to print currently, I get the "NT access denied" error message.

Thanks

---

### Post by jasplund on 2005-07-26
I can´t get it to work. I have the same ip on both my computers. Maybe that´s why?

---

### Post by Imgonna on 2005-07-27
Spot on - worked first time for my XP Pro Box and Samsung ML-1210 printer, without modifying XP in anyway other than the share.

Now I can print across my WLAN  \\:D/

---

### Post by sbclifton on 2005-07-30
Thanks. Unfortunately, my Ubuntu system thinks it is printing and the XP system sees nothing. I will try re-booting both and see if that helps.

---

### Post by Jeltje on 2005-08-05
Perfect! I finally got it working...
Did exactly the things described in the HOWTO.

However, that did not entirely work as the printer did come "alive" but produced no test page. I tested if the printer (HP PSC 1350) worked if I connected it straight to my box and it worked perfectly (with the HPIJS driver and HP PSC 1300 selected).

Disableing bidirectional support in win xp made the printer work in the network.

 :)

---

### Post by sbclifton on 2005-08-23
Well I am very happy that this thread has helped solve a lot of people's problems.

Unfortunately  I started this thread and I still can't get mine to print. 

My print driver on the Xp box (HP952c) doesnt let me mess with the parallel bi-directionality. I've tried about everything else. Not a peep out of the XP printer nor any sign on the PC that it is receiving anything. 

I so want to switch over to unbutu full time, but I gotta be able to print!

any other ideas are welcome.

---

### Post by stiivi on 2005-08-24
I have followed instructions on this thread too, however I am still not able to print. I have digged into log files, but no luck so far. More information is in this thread:

[http://www.ubuntuforums.org/showthread.php?t=59205&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=59205&highlight=samba)

---

### Post by TwiceOver on 2005-09-11
Sorry.  I just realized this isn't the place to ask questions.  Found the thread through a search.  I'll repost in the appropriate forum.

---

### Post by keerat on 2005-10-09
[QUOTE=jrobcet]That looks normal - it shouldn't be a problem.

I had another thought yesterday. I'm not sure where I saw it now, but I remember someone solving a problem similiar to this by disabling bidirectional support for the printer. It certainly won't hurt to give it a try. 

To disable it, go to printer properties on the XP machine (right click the printer and choose Properties). Click the Ports tab and uncheck "Enable bidirectional support".[/QUOTE]

A lot of the more recent HP Printers appear to come equipped with bidirectional support. Disabling it on my PSC 1350 helped fix my printing woes. Searching for printer servers also shows that the support for bidirectional ports is limited. 

Thanks for the tip.

---

### Post by maulattu on 2005-10-16
nothing to do 4 me.:( 
i've windows 2003 std edition with an hp laserjet 1000 (usb).
it's shared and with or without the support of bidirectional communication printing from kubuntu 5.10 doesn't work.
when i configure the printer under kde, it find the printer, but when i send a test page on the control panel of the printer under windows i see the job just for 1 second and aftger that it disappear. under the event viewer of windows it reports:

```
The document 1, remote document with low priority belonging to Administrator was deleted on hp laserjet 1000
```

i've tried with or without the bidirectional support enabled and moreover i've installed the unix printer service (and it's started ;) )

what can i do:confused: :confused:

---

### Post by maulattu on 2005-10-16
this is the log of cups:
```
I [16/Oct/2005:20:43:36 +0200] Setting tmpprinter_xf9eDaPd device-uri to "smb://WORKGROUP/server/hp" (was "file:/dev/null".)
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] New printer 'tmpprinter_xf9eDaPd' added by 'root'.
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] Printer 'tmpprinter_xf9eDaPd' modified by 'root'.
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] Printer 'tmpprinter_xf9eDaPd' now accepting jobs ('root').
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] Printer 'tmpprinter_xf9eDaPd' started by 'root'.
I [16/Oct/2005:20:43:36 +0200] Adding start banner page "none" to job 17.
I [16/Oct/2005:20:43:36 +0200] Adding end banner page "none" to job 17.
I [16/Oct/2005:20:43:36 +0200] Job 17 queued on 'tmpprinter_xf9eDaPd' by 'maurizio'.
I [16/Oct/2005:20:43:36 +0200] Started filter /usr/lib/cups/filter/pstops (PID 5513) for job 17.
I [16/Oct/2005:20:43:36 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 5514) for job 17.
I [16/Oct/2005:20:43:36 +0200] Started backend /usr/lib/cups/backend/smb (PID 5515) for job 17.
E [16/Oct/2005:20:43:37 +0200] PID 5514 stopped with status 1!
I [16/Oct/2005:20:43:37 +0200] Hint: Try setting the LogLevel to "debug" to find out more.
```

it seems to be an error of the foomatic-rip driver, right?
where can i set the LogLevel to debug???

every job i tried to start reports this error:???:

---

### Post by dgermann on 2005-10-22
Hi--

Many thanks. 

I just spent a couple hours trying to get my Brother HL-5140 installed, following this thread. 

Eventually what got it to work for me was to use the ip address of the XP machine (192.168.1.101), instead of its network name (fred).

Hope that helps someone else, too.

Thanks, folks! You have been a big help.

---

### Post by w.hill on 2005-10-25
[QUOTE=maulattu]this is the log of cups:
```
I [16/Oct/2005:20:43:36 +0200] Setting tmpprinter_xf9eDaPd device-uri to "smb://WORKGROUP/server/hp" (was "file:/dev/null".)
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] New printer 'tmpprinter_xf9eDaPd' added by 'root'.
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] Printer 'tmpprinter_xf9eDaPd' modified by 'root'.
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] Printer 'tmpprinter_xf9eDaPd' now accepting jobs ('root').
I [16/Oct/2005:20:43:36 +0200] Saving printers.conf...
I [16/Oct/2005:20:43:36 +0200] Printer 'tmpprinter_xf9eDaPd' started by 'root'.
I [16/Oct/2005:20:43:36 +0200] Adding start banner page "none" to job 17.
I [16/Oct/2005:20:43:36 +0200] Adding end banner page "none" to job 17.
I [16/Oct/2005:20:43:36 +0200] Job 17 queued on 'tmpprinter_xf9eDaPd' by 'maurizio'.
I [16/Oct/2005:20:43:36 +0200] Started filter /usr/lib/cups/filter/pstops (PID 5513) for job 17.
I [16/Oct/2005:20:43:36 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 5514) for job 17.
I [16/Oct/2005:20:43:36 +0200] Started backend /usr/lib/cups/backend/smb (PID 5515) for job 17.
E [16/Oct/2005:20:43:37 +0200] PID 5514 stopped with status 1!
I [16/Oct/2005:20:43:37 +0200] Hint: Try setting the LogLevel to "debug" to find out more.
```

it seems to be an error of the foomatic-rip driver, right?
where can i set the LogLevel to debug???

every job i tried to start reports this error:???:[/QUOTE]

I am having the same problem printing from 5.10 to a shared MagiColor2300DL (W2K). I can print to the share from two Gentoo (LINUX) boxes but not 5.10 - Configured to print to the SAMBA share.

I can print to a Lexmark T614 using IPP ok.

You can alter the LogLevel in /etc/cups/cupsd.conf

You will have to restart cupds for the change to take effect.

Is it possible to configure W2K to be a lpd server? I know that it is possible to print TO a lpr from W2K but am confused about emulating one.

---

### Post by w.hill on 2005-10-25
Problem solved. There appears to be a bug with the foomatic driver for the MagiColor printer.

I downloaded the driver directly. Compiled it (After working out how to install a functional compiler), installed it.

Hurrah.

---

### Post by Hranj on 2006-10-20
ok i thought that i did everything right but i guess not. when i print it gets sent to the printer but it just prints a blank page with nothing on it? anyone know how to fix this?

---

### Post by d4n3lu on 2006-10-21
I have a problem im trying to print to a windows machine from ubuntu i did what u did and it didnt work i cand really get the driver for my printer maybe u can help me out i have a Dell 720 photo printer
Thanx a lot pls help me

---

### Post by d4n3lu on 2006-10-22
i got a dell 720 photo printer and i cand find the driver for it can sombody help me pls i got the printer where it make noces but nothing prints.

---

### Post by a.v.l on 2006-12-07
> **orion_114 said:**
> _**How to setup your Ubuntu machine so it can print to a Windows XP shared printer**_

It was suggested that I add this from the following thread:
[http://ubuntuforums.org/showthread.php?t=24887&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=24887&page=1&pp=10)

_Step 1: Installing Samba on Ubuntu_
[list]
[*]Click System -> Administration -> Synaptic Package Manager
[*]Enter your password
[*]Now click Search and type Samba in the search box.
[*]You should now see a list of items containing the word Samba.
[*]Right click on the Samba with the little ubuntu icon on it and select mark for installation.
[*]Click apply
[*]The packages will now be downloaded and installed.
[/list]  

_Step 2: Checking if your network is working_
[list]
[*]Find the ip address of your windows xp machine by going ... start -> run
[*]Then type cmd
[*]type ipconfig in this window and you should see your ipaddress there.
[*]Now on your ubuntu machine goto the command line
and type ping <your windows ip address>
[*]see if you get a response.
[/list]
if you get timeouts:  [-X 
  a.) Check if your network cables are all connected
  b.) Check if your network cards are working
  c.) Check the settings of your network interfaces
  d.) Try disabling any firewall software

_Step 3: Sharing the Windows XP printer_
[list]
[*]start -> settings -> control panel
[*]open printer and faxes
[*]find the printer you wish to share with your ubuntu machine
[*]Right Click -> properties on it and goto the sharing tab.
[*]Click on share this printer and type a short name in the share name box.
[/list]

_Step 4: Adding the printer on the Ubuntu machine_
[list]
[*]System -> Administration -> Printing
[*]Click Printer -> Add Printer
[*]Click on network printer.
[*]Select Windows Printer (SMB) from the dropdown.
[*]In the host section type the IP address of your windows machine.
[*]In the printer section type the share name you gave your printer
[*]Now enter your username and password for your ubuntu machine.
[*]Click forward.
[*]Now select the manufacturer and model of your printer.
[*]And finally click on Apply.
[/list]

Hope you get it workin !!  \\:D/

I'm trying, but failing to network/print from my Ubuntu machine to the printer on my XP machine. I've followed the above instructions and seem able to ping the XP machine, at least I'm assuming the 56 (84) bytes of data result I get confirms this.

When I do a test print from my Ubuntu machine the printer property box says ready and then it tells me that an A4 page has been sent to the printer, but thats all.  The printer neither prints nor makes any sound.

I've enabled printer sharing on my XP machine, but now I need some help please.

---

### Post by Stormx on 2006-12-20
Issues! I can print a test page perfectly, with the CUPS test page or the normal ubuntu one. But I can't print from any apps.

Constantly, the cups error log gives this, over and over again.:

```
E [20/Dec/2006:22:41:34 +0000] cupsdAuthorize: Local authentication certificate not found!
```

Printing a test page works perfectly, but gives these errors:

```
E [20/Dec/2006:22:45:46 +0000] [Job 18] No %%BoundingBox: comment in header!
```

Printing a 1 line text file from gedit gives this:

```
E [20/Dec/2006:22:48:11 +0000] PID 32740 (/usr/lib/cups/filter/pstocanonbj) crashed on signal 11!
```

Now this could be to do with my drivers, I just don't know. if it is, please direct me somewhere else.

Basicly the printer prints nothing on the gedit try. It sits there saying

> Stopped: job-stopped

in the print queue state.

Any ideas? :)

---

### Post by dgermann on 2006-12-21
Stormx--

When I installed CUPS (months to years ago), I recall having to use the ipaddress for the printer, rather than the name of the computer to which it was attached. I remember playing around in System > Admin > Printers with different combinations and eventually something worked.

Poking around just now I found [this thread]("http://ubuntuforums.org/showthread.php?t=294990") here which refers to problems others had with some Canon printers under CUPS and having to get a different driver. Perhaps that will give you some things to try.

Also, do you know about the localhost:631 web tools for CUPS? Perhaps that will have some extra help.... ;)

---

### Post by Chemist on 2006-12-28
hi I'm trying to print to a brother printer on an xp pro machine. I've installed samba on my ubuntu box and shared the printer on the xp machine as well as installing the other print services on it. The priner makes a noise if its going to print but nothing happens.

---

### Post by Benchrest on 2007-01-01
Moved message to its own thread, can't figure out how to delete, only edit.

---

### Post by lamalex on 2007-02-11
> **thecrimsonking said:**
> By default "Print Services for Unix" are not installed on XP.
You must install *and* manually turn on this service from the MMC before you can print to XP.

I have never been able to print to an XP machine (from linux) before turning this on.  

Now I will sit back and wait for all the people telling me they do it all the time  :roll:

i had no problem at all....  pwnt.

---

### Post by KaroSHiv0n on 2007-02-22
Just wanted to say thankyou! finally i can print again, i dont know how many damn attempts i made over the last few weeks to get printing working and finallyits working again, thank you so much! <3

---

### Post by [Phaedrus] on 2007-03-27
Works like a charm. Thanks.

---

### Post by jordon on 2007-04-01
Works great with Edgy. Thanks so much!

A few observations for those who might be having trouble:

With Windows's ipconfig, your computer's IP address is the one that appears on the "IP Address" line. (Probably obvious, but...) I pinged this IP address from Ubuntu and it seemed to do about a zillion pings. I didn't find out exactly how many because I just closed the terminal after a while. I don't know if that's normal behavior, but entering that IP address in Step 4 worked fine.

Also, when I was going through the printer setup in Ubuntu, I was asked to enter a user name and password for "MSHOME," with "root" already entered as the user name. I clicked "Cancel" and went ahead with the directions, and everything turned out okay. Your mileage may vary.

---

### Post by reality_hunter on 2007-04-10
Hi - I have noticed the last reply to this thread was in January, but i am hoping someone here will assist me because after about 10-15 hours of work..i am ready to give up :[-X 

==================================================
printer: KONICA MINOLTA magicolor 2430DL (using USB)
  *this is setup as a shared printer and can also print from a 3rd box(laptop)

also using a D-LINK wire/wireless router
==================================================

I recently installed UBUNTU edgy 6.10 on my HP and that is the only operating system on that machine. I have learned a lot from this forum and the starter guide since I am not that much familiar with the commands and all that but I will be hopefully soon.

anyways the problem is printing on my windows XP machine from my UBUNTU.  Before I goon further I think its important that I should mention one MAIN problem that I think could be preventing me from printing, but i am not sure if thats what it is. The main problem I think is:
 *  On UBUNTU, when I click on add printers and go through the steps and click apply, I DONOT see a printer added on the printer dialog box that is open. I have tried many time , rebooting and all that, but nothing and cannot find the answer anywhere why this might be.
 *  This was not the case when I had first newly installed UBUNTU because that time going thru the process of adding printer, I was able to add a printer and it would show on the printer section.  BUT now this does not happen. :frown:  PLEASE ADVICE as to what to do.

Also, In the process described , I have one more question. setup procedure:
1) add printer
2)choose network printer   --> chooose "SMB"
3) *after choosing SMB, there is a popup asking me username and password.  Sometimes it asks 2 times and sometimes it asks for three times and sometimes just once.  I will mention what it asks for next:
   (i) please enter the login for the "192.168.xxx.xx1" (this is the IP for the windows 
         computer)
   (ii) please enter the login for the "CHIMPI" (this is the name of the windows computer)
   (iii) please enter the login for the "username-desktop" (name of the UBUNTU desktop)
(I do have a username and password setup on my windows machine)
I have tried with and without the passwords but nothing.  It would be informative to know what and why it is asking. PLEASE also advice whether to leave these fields blank or not.
4) at HOST: I put "192.168.xxx.xx1"
5) printer: I put the shared name for the printer "KONlaser"
6) *this username and password feild is automatically filled up by the LAST Username and Password entered from the popup, BUT either way, this should be the username and password for the UBUNTU......is this correct?
7)clicking NEXT, I can choose the manufacturer and next I can see the exact printer MODEL listed from the list and by selecting that ...clicking next and then apply.

this procedure used to add a printer and now it does not.  PLEASE kindly help.

Also, I should mention that the firewall on the windows doesnot seem to be the problem because I had just setup a network drive between the 2 computers and I have more than 150GB of HD space on that network drive that is installed on UBUNTU but can be accessed as a network drive from the windows.  
Also, just to be sure -- how do i properly find the IP address of my UBUNTU? because I have noticed that from the network config it displays the IPv4 address or somthing, but from my router configuration setting....it is "192.168.xxx.xx0" ("which I am guessing is the correct one")

sorry about making the thread so long (this is my first post), I will learn.
thanks for the taking the time to read this and thanks for helping out :-#

---

### Post by rmadd1 on 2007-08-13
I found your post on this forum to get my windows printer to work as a shared printer on my Ubuntu laptop. I followed your instructions exactly and rechecked twice more, I have the printer supposdly on my machine but when I go to print, it goes through the pop-up boxes sending the info to the printer then nothing happens. I hope you can tell me whats wrong. This is the biggest thing about linux, getting the components to work. I hate windows, but at least the addons work. The downside is all the security programs that has to installed. Hope you can help.  Thanks for your help!

---

### Post by newagelink on 2007-08-14
> **kyroha said:**
> Works like a charm, 
many thanksHa! Thanks so much OP; I feel stupid that I hadn't done this already ...

---

### Post by Nano on 2007-08-14
I wish I knew how to print to a print server.
I've tried for weeks but no luck.
It's a D-Lynk USB print server.

It works correctly for all windows boxes but I can't set it up in my ubuntu boxes.

Any tips?

---

### Post by mrhirsh on 2007-10-12
I am running XP Pro on my Toshiba Laptop (Ubuntu 7.04) under VMWare.  The printer works fine in Ubuntu but does nothing in XPPro.  I've followed all the steps and suggestions (I think) particularly the check list from Orion.  

My printer is an HP 1300 which is a plug and play unit (USB).  When I plug an external mouse into any of the USB's it works fine.  The printer doesn't seem to be recognized in any of them.

When I print in XP Pro, i get the little icon like the document is being sent to the printer.  But nothing happens.

I would greatly appreciate any help.

Michael

---

### Post by tad1073 on 2008-02-09
I have followed the directions for setting up ubuntu to access the printer that is connected to the widows machine but i am still unable to print to it.  Here is the way i set everything up:

```

smb://WORKGROUP/server:port/printername

```
Of coarse with the appropriate entries for workgroup, server, port and printer name.

I click verify and get "Verified    This print share is accessable"

I have even tried setting up LDP or what ever it is called and it doesn't work.

also, I am using gutenprint 5.0.1 drivers.

---

### Post by tad1073 on 2008-02-10
bump...

---

### Post by tad1073 on 2008-02-11
bump...

---

### Post by timjohn7 on 2008-02-21
> **jrobcet said:**
> Great! I'm glad you finally got it working  :)
I've been following this thread to solve exactly the same problem using an HP Deskjet 2460 under WIndoze XP Pro.
I wish I'd jumped straight to this simple cure and I recommend that it is included in Ubuntu documentation.

Thanks

---

### Post by captainzoom on 2008-03-02
Finally got my printer to work. Just shouldn't have skipped that first 'how to part' i'm such an idiot! 

nb. adding the password requirement when using windows xp pro could be helpfull to more idiots :-)

---

