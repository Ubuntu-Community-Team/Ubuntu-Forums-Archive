---
title: "Lexmark linux driver kit"
date: 2007-11-07
forum: Packaging and Compiling Programs
---

### Post by MikeSz on 2007-11-07
Has anyone had a play with the Lexmark Linux Driver kit to make a driver for their Ubuntu box?

The link is here [http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html)

Ive been trying to get a Lexmark X4550 all-in-one working in 7.10 but so far, no joy.  Be grateful if anyone has any ideas - I dont know much about Ubuntu but I'm happy to try things out!!

---

### Post by MikeSz on 2007-11-19
Bump....

anyone had a go at this?  I like the printer and it works on my windows machine so didnt want to take it back - has anyone managed to get a driver working yet?  Mine is an all in one 4550 and just will not work in Ubuntu :(

---

### Post by dholbach on 2007-11-20
I'd probably try to file a needs-packaging bug to get it packaged for Ubuntu: [http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by MikeSz on 2007-11-20
Done - many thanks!

---

### Post by Izek on 2008-02-09
> **dholbach said:**
> I'd probably try to file a needs-packaging bug to get it packaged for Ubuntu: [http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](http://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

And how long do you think it'll take? It's almost been 4 months since it was reported...

[https://bugs.launchpad.net/ubuntu/+bug/164054](https://bugs.launchpad.net/ubuntu/+bug/164054)

---

### Post by MikeSz on 2008-02-10
I have no idea - I don't know what a lot of the stuff on the bug site means.  All I know is 'they' have it and it has  been confirmed.  So fingers crossed for Hardy!

---

### Post by Izek on 2008-02-12
> **MikeSz said:**
> I have no idea - I don't know what a lot of the stuff on the bug site means.  All I know is 'they' have it and it has  been confirmed.  So fingers crossed for Hardy!

I made some deb files for you, you may want to check them out.

<<snipped URL>>

Although after installing these packages, you won't be able to run a 4550 Lexmark Wireless Printer (Like I have) since you need to search for the ppd file (Driver File), which there is none when you install these deb files.

After installing the deb files, the installation said it installed to includes/lexmark. **It's a lie, that folder doesn't exist after installation finishes.**

***WARNING: YOU CAN ONLY INSTALL ONE OF THESE DEB FILES AT A TIME! Terminal Will complain if you try to install another over the other.***

Keep in mind... Gutsy can detect that the printer exists on the wireles network. Also, after installing the **z55** version in that deb list, The printer Control Panel in ubuntu will no longer give the error "Could not print to printer." However, it will just hang the printer on "Processing Job..." I think there's a problem with Ubuntu being able to "Wake up" devices.

---

### Post by MikeSz on 2008-02-13
Hi Izek - many thanks for the reply!

Pardon me for being a little slow here but what to these Debs do?  Will they allow my laptop to detect the printer via USB connection?  If so is it easy to set up?

On the Wi-Fi element, are you saying there is a way to get ubuntu to detect the wireless element of the printer?

---

### Post by Izek on 2008-02-13
> **MikeSz said:**
> Hi Izek - many thanks for the reply!

Pardon me for being a little slow here but what to these Debs do?  Will they allow my laptop to detect the printer via USB connection?  If so is it easy to set up?

On the Wi-Fi element, are you saying there is a way to get ubuntu to detect the wireless element of the printer?

Uh, ANY OS can already "detect" printers on a network (Since the network assigns a printer to a specific port, therefore no kit, drivers, etc. are needed to detect a network printer.) The problem is printing to the printer on the network, this requires the drivers, which we don't have.

So no, this won't help you detect a USB printer. Even if you have a z55 printer and installed the LDK for z55.

---

### Post by Izek on 2008-10-20
debs are now gone, and so is the lexmark driver kit by the way.

Sorry for the bump on this.

---

### Post by RealG187 on 2008-10-21
Anything on the x3350 yet?

---

### Post by Izek on 2008-10-27
> **RealG187 said:**
> Anything on the x3350 yet?

Still a paperweight, sorry.

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X3350](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X3350)

---

### Post by RealG187 on 2008-10-31
That reminds me. I have two x3350's.

One was for my comptuer and the other is for the "family PC" (I recently installed Ubuntu on it, but [have been having resolution problems]("http://ubuntuforums.org/showthread.php?t=929963")).

The one I had broke, I haven't bothered to contact Lexmark. I need to buy a new printer/scanner. Are there any good ones that work with Linux?

---

### Post by thelamer on 2008-11-04
I know this is a bad solution and probably not what you are looking for, but I figured I would share my success story. 

Get virtualbox and install a Windows XP virtual machine. 

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I had already configured the printer to connect to my router and have a SMB share setup on an XP machine for the Driver push so it was as easy as using XPs add printer wizard. I have a leaned out version of XP so it boots in about 20 seconds and does what I need it to do. 

After scouring the internet this was the only solution I could come up with and I am now printing from my Linux desktop(albeit in a rigged propriety manner) 

Figured I would share this idea with others that are roadblocked.

---

### Post by Izek on 2008-11-04
I was going to do that too, but then I would have to install OpenOffice within the virtual box, and firefox, and gimp. Though, I don't know how to connect my x4550 printer to a samba connection.

---

### Post by Nuetouch on 2008-12-03
I too have a lexmark X4550, i've been reading the forums and just want to confirm...there are currently no drivers available for this printer? Anyone?...should  I stop looking...?

---

### Post by Izek on 2008-12-03
> **Nuetouch said:**
> I too have a lexmark X4550, i've been reading the forums and just want to confirm...there are currently no drivers available for this printer? Anyone?...should  I stop looking...?

Yes, there are no drivers, and I'm sure there won't be any for linux. Might as well wait for ReactOS or go back to Windows. Or, go to goodwill or something and find a printer that works.

---

### Post by Nuetouch on 2008-12-04
I currently sell used computers, and repair from home. All windows platforms, but soon will sell Linux boxes. So, for me I use both Ubuntu and Windows, both have good and bad points. So,I don't just use windows, both have a lot to offer. But when I sell Linux boxes I need to know what works and what doesn't. I'll just transfer files via samba to windows network and print from there. Thanks all!!

---

### Post by pdoma on 2009-03-21
> **RealG187 said:**
> I need to buy a new printer/scanner. Are there any good ones that work with Linux?

HP is probably one of the most Linux friendly companies so most of their printers should work although this is not a guarantee. I recommend doing some research before you go and buy anything, unless you wonna end up with yet another paperweight. Mean while I urge people to send nasty grams to Lexmark to at least release PPD file for those all in one printers.

---

### Post by rabinnh on 2009-03-30
If anyone is interested in this, please let me know.

I have the same issue with a X6570.  Since I always have a Windows box running (a server), I wrote a little service that sits on the Windows box and monitors a directory.  Any file that gets dropped in that directory gets printed and then (optionally) deleted.

It uses the equivalent of ShellExec, so the program that prints it must be installed, but in practice, all you need is Adobe Acrobat Reader.  

All OpenOffice programs can Export to PDF.  Firefox can "Print to File" in PDF format, etc.  So basically, you mount the Windows directory, and when you print drop the file in the designated directory.  That's what I've been doing.

rabinnh

---

### Post by RealG187 on 2009-03-30
I have been thinking about this:

[http://ubuntuforums.org/showthread.php?t=1099927](http://ubuntuforums.org/showthread.php?t=1099927)

---

### Post by dannyboy79 on 2009-04-14
> **rabinnh said:**
> If anyone is interested in this, please let me know.

I have the same issue with a X6570.  Since I always have a Windows box running (a server), I wrote a little service that sits on the Windows box and monitors a directory.  Any file that gets dropped in that directory gets printed and then (optionally) deleted.

It uses the equivalent of ShellExec, so the program that prints it must be installed, but in practice, all you need is Adobe Acrobat Reader.  

All OpenOffice programs can Export to PDF.  Firefox can "Print to File" in PDF format, etc.  So basically, you mount the Windows directory, and when you print drop the file in the designated directory.  That's what I've been doing.

rabinnh
i am interested in this as I have a Lexmark X5495. I have Ubuntu Feisty Fawn and can't get my SMB shared printer to print from Ubuntu. SO what I do is print to pdf, then manually transfer it to my windows box and then I print it. Can you provide me the script you wrote for windows so that anything that gets put into a folder on my windows box gets auto printed? I would appreciate that. I don't know any programming at all, not on the windows side or the linux side so make the instruction on what I should do as dumb as possible, I would really really appreciate that. I would forever be in your debt. Thank you. Ias there a way to have the print to pdf on the ubuntu machine automatically put the file into the smb shared folder automatically also? thanks for any help here.

---

### Post by rabinnh on 2009-04-14
Here you go, DannyBoy.  There are 4 files in this zip;

sendtoprinter,exe is a Windows binary that is a service.
sendtoprinter.xml is the config file.
intstallutil.exe and installutillib.dll is a command line utility to install and uninstall any service, i.e.

installutil sendtoprinter.exe

So just copy them to a directory, modify the sendtoprinter.xml for the folder you want to monitor, and there you go.

rabinnh

---

### Post by RealG187 on 2009-04-14
> **rabinnh said:**
> If anyone is interested in this, please let me know.

I have the same issue with a X6570.  Since I always have a Windows box running (a server), I wrote a little service that sits on the Windows box and monitors a directory.  Any file that gets dropped in that directory gets printed and then (optionally) deleted.

It uses the equivalent of ShellExec, so the program that prints it must be installed, but in practice, all you need is Adobe Acrobat Reader.  

All OpenOffice programs can Export to PDF.  Firefox can "Print to File" in PDF format, etc.  So basically, you mount the Windows directory, and when you print drop the file in the designated directory.  That's what I've been doing.

rabinnh

Could I do that in a virtual machine?

---

### Post by rabinnh on 2009-04-15
Sure.

---

### Post by rabinnh on 2009-04-15
In fact, if you could use a subdirectory off of the shared folders.

---

### Post by dannyboy79 on 2009-04-15
> **rabinnh said:**
> Here you go, DannyBoy.  There are 4 files in this zip;

sendtoprinter,exe is a Windows binary that is a service.
sendtoprinter.xml is the config file.
intstallutil.exe and installutillib.dll is a command line utility to install and uninstall any service, i.e.

installutil sendtoprinter.exe

So just copy them to a directory, modify the sendtoprinter.xml for the folder you want to monitor, and there you go.

rabinnh
thanks, I'll give it a try and post back if i get it to work.

---

### Post by chrisdglong on 2009-04-16
Let me know if this works as well. I also have a x4550 and would like to get it to work in linux. I have a network of 5 windows OS and one linux. 

This is my first go with ubuntu and it is like learning windows all over again. I do like the increased performance, less worry about viruses and 4 desktops with only two screens :)

---

### Post by RealG187 on 2009-04-22
> **rabinnh said:**
> Here you go, DannyBoy.  There are 4 files in this zip;

sendtoprinter,exe is a Windows binary that is a service.
sendtoprinter.xml is the config file.
intstallutil.exe and installutillib.dll is a command line utility to install and uninstall any service, i.e.

installutil sendtoprinter.exe

So just copy them to a directory, modify the sendtoprinter.xml for the folder you want to monitor, and there you go.

rabinnh

I wonder if I install this can I print when a user is logged on that is not an administrator?

---

### Post by rabinnh on 2009-04-22
No one needs to be logged into the Windows machine.  It is a service.  Just drop files into the Windows folder (share).

---

### Post by RealG187 on 2009-04-22
> **rabinnh said:**
> No one needs to be logged into the Windows machine.  It is a service.  Just drop files into the Windows folder (share).

Wow quick reply, what are the chances you were on...

What type of file formats does it support?

---

### Post by rabinnh on 2009-04-23
Anything that you have a file association for.  For example, if you have Acrobat Reader associated with PDF files, it will print them.  If you have Word associated with DOC files, the same.

What it does is monitor the directory and then use the Windows shell's file associations with the shell "print" verb.  So if you want it to support a specific file type, just make sure there is an associated program.

What I have found is that since Linux supports "Print to file" in PDF format, I pretty much always use that for everything.

---

### Post by RealG187 on 2009-04-23
So I would need to have Acrobat reader or similar on that computer?

If I would print would is disrupt the user on that computer if word or acrobae just randomly comes up?

---

### Post by rabinnh on 2009-04-23
No it won't.  My suggestion is to just try it.  You can always use the included utility to uninstall the service.  No big deal.

---

### Post by dannyboy79 on 2009-06-03
i tried this and I can't get it to work. I was in linux, I printed mapquest.com directions to a pdf file and saved it in the shared windows folder that is being monitored by the service. the printer did nothing?  does the windows share need to have any special security setup on it? I ran installutil.exe sendtoprinter.exe and it said it installed the service and everything. i even have log files, they don't have any errors in them?

Here is what my .xml file looks like.

<?xml version="1.0" encoding="utf-8" ?>

<Configuration>

  <directory>C:\Documents and Settings\All Users\Documents\printer</directory>

  <deleteafterprint>true</deleteafterprint>

</Configuration>


can someone please help?

---

### Post by rabinnh on 2009-06-03
Did you change the Log On settings for the service to use a profile that has your printer set as the default printer?

If not, the service is logged on as "Local System", which has no default printer set.

---

### Post by dannyboy79 on 2009-06-04
ok. could you explian how I can solve this then? thank you.

---

### Post by rabinnh on 2009-06-04
I thought I just did in the previous post.  As an example; 

1) log into Windows as Administrator
2) make sure you have chosen a default printer (the Lexmark).
3) Open the Services applet, select SendToPrinter, right click on Properties.
4) Click the "Log On" tab.
5) Click the "This account" radio button
6) Enter the Administrator name and password

Done.

---

### Post by dannyboy79 on 2009-06-04
thank you. i tried it and it still does not work. I am sorry but I am not familar with stuff like this in windows. are there log files I can look at somewhere? I was in ubuntu, I printed to a .pdf file and saved it in the shared folder on the windows machine but nothing printed. I did what you said in post #38 and restarted the sendtoprinter service but still no go. anymore help would be appreicated.

---

### Post by rabinnh on 2009-06-04
I'm going to go out on a limb and say that you haven't manually printed using Adobe.  I'll bet that if you double click on the PDF in Windows, you'll get their license agreement.

---

### Post by dannyboy79 on 2009-06-05
i am not sure what you mean. I am printing using linux CUPS/PDF Printer, I click on print to file and I save it straight to the shared folder. it turns out the files aren't even being saved into that shared folder. I don't where they are going? even in windows when I print to pdf (i have a full version of acrobat so it does have the distiller) it's not even being saved in the folder. If I print to pdf in windows and save it to the desktop, it does get saved. WEIRD!!!

---

### Post by rabinnh on 2009-06-05
I am talking about on the Windows machines.  I mean no offense, but I can't help if you aren't familiar with Windows at all.

SendToPrinter is calling Reader and then deleting the file (as specified in the config).

Once again, go to your Windows machine, log in as Administrator, and print a PDF.  Open the Services applet on Windows, go to the Log On tab, and ensure that the User and Password use the Administrator account. 

Please confirm that you have done that before posting again.

Thanks

---

### Post by Mr Smelly on 2009-09-19
Hi rabbinh,

What versions of Windows does this work on? I'm running XP and can't convince sendtoprinter to run as a service. I have followed the instructions above but when I start it as a service Windows reports that it is starting but it then immediately stops.

__

---

### Post by rabinnh on 2009-09-19
XP should be fine.  I don't know if I have enough information to help you.

Have you:

1) Installed it to its own directory?
2) Created a separate print directory to drop files into?
3) Modified the sendtoprinterconfig.xml to point to the print directory?
4) Logged on as a user who is a member of the Administrator group and printed at least once to make sure you can print manually?
5) Used the same user credentials to modify the "Log on" service properties?

It sounds like the config file can't find the print directory.  That is what I would check first.

rabinnh

---

### Post by Mr Smelly on 2009-09-19
Yes I had done all those things. I think that the problem was that I had set the print directory to a mapped network drive (S:\SendToPrinter).

If I change the print directory to one on the hard drive (C:\SendToPrinter) it works like a charm.

If I change the print directory to \\WD-NetCenter1\Shared Files\SendToPrinter (which is the drive S: is mapped to) I can get sendtoprinter to start as a service but not to print or delete the files dropped into the folder.

Do you know if it is possible to use a network drive as the print directory?

---

### Post by RealG187 on 2009-09-20
I tried to run send to printer and got an error, I can't remember what it was, I'll have to try again and note the error.

---

### Post by rabinnh on 2009-09-21
It will not work on network drives, since it uses a Win32 call to get notifications on directory modifications.  This allows it to use no CPU unless something is dropped into the directory.

rabinnh

---

### Post by Mr Smelly on 2009-09-23
OK. Thanks for your help.

---

### Post by luvr on 2009-09-23
> **pdoma said:**
> Mean while I urge people to send nasty grams to Lexmark to at least release PPD file for those all in one printers.

My dad has a Lexmark X83, which is connected to his computer via USB. Under Windows, the printer works, but I cannot convince Linux to print to it. It does identify the vendor and the product name, as demonstrated by the following line of output from the *"lsusb"* command:
```
Bus 005 Device 003: ID 043d:003d Lexmark International, Inc. X83 Scan/Print/Copy
```
So, the printer is connected OK, but cannot be used.

Now, I was wondering to which extent the PPD file could help in getting the printer to work? What more would be needed to operate the printer?

---

### Post by Cathy B on 2009-11-08
I'm just chiming in as I'm so new at this OS and have the Lexmark x4550.  Plus the Ubuntu 9.10 can't find my wireless router; dell truemobile 2300, so BIG learning curve going on!

---

### Post by yutana on 2010-03-19
Lexmarks aren't total paper weights. You can use them as a copy machine. It's HP for me from now on.

---

### Post by RealG187 on 2010-03-19
> **yutana said:**
> Lexmarks aren't total paper weights. You can use them as a copy machine. It's HP for me from now on.True. You can copy I guess. After my x3350 broke I got an HP.

It works under Linux to scan and print, and even if it didn't it has a cool feature where I can scan and have it save the image on a flash drive or memory card, and I can scan through the web interface it has. And I can Bluetooth print from my phone :P

---

### Post by Dark Jedi on 2010-04-04
I dont know if this issue has been resolved but I was able to download a .sh file from lexmark which was a simple executable which allowed me to see and print to my x4650 via USB. The wifi aspect is still work in progress but all good things in time. My windows boxes use wifi, my ubuntu is tethered... for now.

[http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&userlocale=EN_US&locale=en&oslocale=en_US](http://support.lexmark.com/index?page=downloadFile&actp=CONTENT&productCode=LEXMARK_X4650&id=DR20523&segment=DOWNLOAD&userlocale=EN_US&locale=en&oslocale=en_US)

HTH :guitar:

---

### Post by frogging on 2011-07-20
Lexmark says they don't have drivers for the all in one printers this is a lie I use to have a X74 before it broke.  It worked with Linux.  The X74 is an old all in one printer by Lexmark.  

Anyone here old enough besides me to remember the old dot metric printers.  The manuals had compatible print drivers you could use if the ones listed for your printer didn't work.  It was a all around print driver.  All the fetters didn't work but you could print.

Lexmark do you know that there are a lot of folks moving to Linux.  If they can't print with the Lexmark they have they will get a Epson, Cannon, or HP that will.  Lexmark I see your new all in ones have Linux print drivers, So why will you refuse to make one work with the X4550? 

Why will I buy a printer from a company that has not helped it's customers for 5 years.

I'm forwarding this and all the Lexmark's threads to Lexmark.  If you read this and bought a new printer please let me know what kind you bought   

Right now I don't need to print in color I just need to print. :popcorn:

---

