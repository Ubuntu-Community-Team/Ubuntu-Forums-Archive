---
title: "How Samba printing worked for me"
date: 2005-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by jmeadows111 on 2005-04-17
After hours of frustration (and reading various posts here), I finally got Samba printing to a Windows 98 printer share working, and I don't recall if I saw the solution posted, so I thought I would post it in case it helps anyone else. (I am seeing a lot of posting regarding printing issues...)

When I set up the SMB printer using the System -> Administration -> Printing GUI, it set up the deviceURL in /etc/cups/printers.conf as follows (with slight user id and password changes)

DeviceURI smb://ubuntuUID:ubuntupassword@192.168.1.77/SAMSUNG

This never worked for me.

On the same network, I have a Fedora Core 2 box that can print to this printer share. It has the following as its DeviceURI entry in /etc/cups/printers.conf

DeviceURI smb://ATHOME/LAURA/SAMSUNG 

I commented out the existing line and put this line in, and restarted cups:

 /etc/init.d/cupsys restart

and voila, I ws happily killing trees  :) 

When I opened the printer config gui again, it lists ATHOME (my Windows network) in the host field, which doesn't make sense, but it does seem to work.

Hope this helps others aviod the frustration!

---

### Post by TravisNewman on 2005-04-18
Moving this to the tips&tricks section! Very valuable info!

---

### Post by us3rQUE on 2005-04-29
Im still unable to print on a win98 PC Printer Share on my ubunutu.

Status: 
Printing: Unable to connect to SAMBA host, will retry in 60 seconds...foomatic-rip version $Revision: 3.43.2.6 $ running..

(How can I get a full view of the error.)

---

### Post by Fab on 2005-04-29
what i did was:

in the printer config, select networked printer, smb
hostname was the name of the windows (WinMe in this case) box
printer name was "PRINTER"

worked perfectly fine
im not sure about the names atm, since im not at my home machine atm

---

### Post by supermarchino on 2005-05-11
[QUOTE=jmeadows111]After hours of frustration (and reading various posts here), I finally got Samba printing to a Windows 98 printer share working, and I don't recall if I saw the solution posted, so I thought I would post it in case it helps anyone else. (I am seeing a lot of posting regarding printing issues...)

When I set up the SMB printer using the System -> Administration -> Printing GUI, it set up the deviceURL in /etc/cups/printers.conf as follows (with slight user id and password changes)

DeviceURI smb://ubuntuUID:ubuntupassword@192.168.1.77/SAMSUNG

This never worked for me.

On the same network, I have a Fedora Core 2 box that can print to this printer share. It has the following as its DeviceURI entry in /etc/cups/printers.conf

DeviceURI smb://ATHOME/LAURA/SAMSUNG 

I commented out the existing line and put this line in, and restarted cups:

 /etc/init.d/cupsys restart

and voila, I ws happily killing trees  :) 

When I opened the printer config gui again, it lists ATHOME (my Windows network) in the host field, which doesn't make sense, but it does seem to work.

Hope this helps others aviod the frustration![/QUOTE]

I think you should have tried ;)


DeviceURI smb://**windows**UID:**windows**password@192.168.1.77/SAMSUNG

---

### Post by Behel on 2005-05-16
Hello,

it finally worked for me like this. When editing /etc/cups/printers.conf, I modified it as follows:

DeviceURI smb://WorkgroupName/WindowsUsername:Windowspassword@ServerName/PrinterShareName

It was for me important to specify the Workgroup name in addition to my username. Also the name of the printer is the Share Name, not the Printer Name (as stated in Windows) and it can be obtained on a XP box in: Start->Printers And Faxes then select the printer you want to access (assuming it is already installed), then Properties, then Sharing tab. The name is next to "share name".

And since I had an error after restarting CUPS ( /etc/init.d/cupsys restart) , I just restarted my computer :-). (I can hear you laughing...)

[ FYI: the error was"cupsd: Child exited with status 13!" which means nothing for a newbie like me, any hint?]

And finally it was possible to print!! Thank you to everbody who posted before and I hope this will be helpful to someone...

Loic

---

### Post by MonkeyWrench32 on 2005-05-16
EDIT:  Nevermind, I'm using the Unix Print Services for Windows method instead.

---

### Post by punkefke on 2005-05-31
Hey guys!
I've got an old windows Me computer, which is connected over LAN with my Ubuntu computer. When i wanted to print over network (my printer is a HP840C connected to the WinME box), it failed! After a lot of searching I came to this solution:

Go to gnome-panel -> system-> managment-> printing

Choose for network printer -> smd

Fill in host (the share-name of your windows me box)

Fill in Printer (share-name of your printer)

The other fields empty!

Now here's what I did wrong: you have to think about CASE-SENSITIVITY ](*,)  when filling in host and printer names!!!! (e.g. my box share-name is 'vaste' and not 'VASTE')

Greetz,
Punkefke :grin:

---

### Post by cowlip on 2005-08-05
How frustrating!! I hope some1 will open a bug for this behavior.

---

### Post by asdf on 2005-08-12
[QUOTE=Behel]Hello,

it finally worked for me like this. When editing /etc/cups/printers.conf, I modified it as follows:

DeviceURI smb://WorkgroupName/WindowsUsername:Windowspassword@ServerName/PrinterShareName
[/QUOTE]

Worked beautifully, thanks :) Only it's weird because it used to accept smb://User:Pass@host/computer/share.  All of a sudden it didn't work with that, I don't know if it was because of a change in the cups daemon or in a windows update.

Anyway, thanks for the solution.

---

### Post by jewishj on 2005-08-21
[QUOTE=punkefke]Hey guys!
I've got an old windows Me computer, which is connected over LAN with my Ubuntu computer. When i wanted to print over network (my printer is a HP840C connected to the WinME box), it failed! After a lot of searching I came to this solution:

Go to gnome-panel -> system-> managment-> printing

Choose for network printer -> smd

Fill in host (the share-name of your windows me box)

Fill in Printer (share-name of your printer)

The other fields empty!

Now here's what I did wrong: you have to think about CASE-SENSITIVITY ](*,)  when filling in host and printer names!!!! (e.g. my box share-name is 'vaste' and not 'VASTE')

Greetz,
Punkefke :grin:[/QUOTE]

This did not work for me.  
I noticed I was getting an error "Connection failed with error NT_STATUS_ACCESS_DENIED".

After some searching though, I was able to fix this by typing in "Guest" for username and leaving password blank.

Running a HP Deskjet 5550 via an XP machine on the network.  Guest account does not have to be active.

Just thought this may be helpful to someone.

---

### Post by Franko30 on 2005-08-23
Hi,

for me nothing in this thread worked, except the hint with the guest user (on my German machine 'Gast').

This made the printer (HP Laser Jet 4 P) work.

And fiddling a little bit with the driver and settings made the printouts look nice. :-)

---

### Post by pixxelle on 2005-09-09
> it finally worked for me like this. When editing /etc/cups/printers.conf, I modified it as follows:

DeviceURI smb://WorkgroupName/WindowsUsername:Windowspassword@ServerName/PrinterShareName


I was really frustrated; tried this and it worked the *first* time!   

Thanks so much! :grin: 

(Unbuntu 5.04, dual boot WinXPsp2, Epson C86 (using Linux C84 driver- gimp-print), printer share on a Win2KServ domain member running Win2kPro)

---

### Post by emmo on 2005-10-27
[QUOTE=Behel]Hello,

it finally worked for me like this. When editing /etc/cups/printers.conf, I modified it as follows:

DeviceURI smb://WorkgroupName/WindowsUsername:Windowspassword@ServerName/PrinterShareName

It was for me important to specify the Workgroup name in addition to my username. Also the name of the printer is the Share Name, not the Printer Name (as stated in Windows) and it can be obtained on a XP box in: Start->Printers And Faxes then select the printer you want to access (assuming it is already installed), then Properties, then Sharing tab. The name is next to "share name".

*snip*

And finally it was possible to print!! Thank you to everbody who posted before and I hope this will be helpful to someone...

Loic[/QUOTE]

after trying for (to long) to get a windoze printer to work, with every gui you can find, 30 different uri's, this is the one that works. 

that gui config tool is not workin, i can say that. I got it workin now (just plain XP Pro printersharing) and with that url. What bugs me a bit is that the password is visible in the default print setuptool.

i used the above uri, so for me that is;

[HTML]DeviceURI smb://mshome/emmo:password@amd/hpdeskjet[/HTML]

in the setuptool now, computername shows workgroup, printer shows the rest of the uri, accept for the workgroup name, username is blank, and 15*** in password box to complete the mess. (wonder what can be there, since to complete uri is visible...

Well, i got it working that is what counts, but gnome-cups-manager is gonna be removed here, that is for shure :smile:

ps, i saw to late that this was about a 5.04, but it works with 5.10 (ubuntu) also :)

---

### Post by kjkrum on 2005-10-27
Behel's solution worked for me!  Now I can get back to work after 3 hours of frustration.

Pretty sad that MAJOR bugs like this can go unfixed for > 5 months.  One wonders if Linux will ever see widespread adoption when the best distro around can't even get samba printing right.  If it weren't for my patience with this crap (and bitter contempt for Microsoft), my company would probably not be using Linux at all.

---

### Post by oldgoat on 2006-05-01
Thank you jmeadows111 - this was the piece of information that did the trick for me:D

---

