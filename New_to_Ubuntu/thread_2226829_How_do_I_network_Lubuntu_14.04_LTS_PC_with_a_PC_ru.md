---
title: "How do I network Lubuntu 14.04 LTS PC with a PC running Win 7 Pro?"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by Alex_Rodriguez on 2014-05-29
Hi,

I have a computer running Lubuntu 14.04 LTS and I am wanting to network it with a computer running Win 7 Pro Service pack 1. I wish to access the scanner, printer and if possible folders on the Win 7 Pro computer. Both computer are currently sharing the internet connection through a router, so they are connected by a network cable. Could you please provide me with simple steps in order to achieve this.


Cheers,

Alex

---

### Post by TheFu on 2014-05-29
Sharing printers over the network is relatively easy when they are on the same LAN, provided the printer is well supported by Linux.  Scanners will depend on the exact model.  I share a scanner on Linux systems, but not Windows.

If the systems are NOT on the same LAN, security considerations dictate that you only do this over a VPN.

So the first steps for all of this is to setup sharing on the Windows side - do this for the printer and the folders you want to share. After that, open whatever file browser you like (pcmanfm is fine) and select "Go --> Network Drives" ... that should be enough to get you there.

For connecting to the printer, click on the main menu, then Preferences, then Printers and follow the instructions. The exact printer involved might matter, but well supported printers "just work."  [https://www.google.com/search?client=ubuntu&channel=fs&q=lubuntu+network+printer&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=lubuntu+network+printer&ie=utf-8&oe=utf-8) might help.  Network printing is handled by a mix of samba and CUPS. Often the samba part is completely transparent.

Sorry, but I cannot help with the scanner.  I use X/Windows to remote into the machine connected to the scanner and run **gscan2pdf**. Works just like being there, as it should.

You may need to alter the firewall configuration on Windows to allow local LAN access to the file and printer sharing ports.

---

### Post by Alex_Rodriguez on 2014-05-30
(Replying to TheFu)

I followed your instructions with regards to Windows but are stuck when it comes to Lubuntu. When I open system tools->printers a dialog box pops up. I add a printer. Then it gives me options of where the computer is whether it is a local printer or one on a network. I click network but then it gives me a whole load of options that I know nothing about and I need step-by-step instructions to guide me through the process of connecting my Win 7 printer via this option. Hope you can help?

Cheers,

Alex

P.s. I have tried Ubuntu procedures to see whether they are applicable but to no avail. I would love to file share but when you right click in Lubuntu in your home folder on either your documents folder or the public folder there are no options to share...I have installed Samba but have no clue how to use it and have doubts about whether it can be used with Win 7 as it says nothing about it in the manual.

---

### Post by TheFu on 2014-05-30
The stuff I've described works fine with Win7.  
Post some of the exact commands you've tried and which how-to guides you've followed with the exact step that failed.

Did you run **pcmanfm**?

---

### Post by Alex_Rodriguez on 2014-05-31
Hi again,

These are the steps I followed to try and get file sharing going:
[LIST=1]
[*]PCManFM
[*]Go->Network
[*]Double click Windows Network
[*]Double click WORKGROUP-NEW (The name of my Windows Network)
[*]Get the error "Failed to retrieve share list from server: Connection timed out" and the subsequent error, of "The specified location is not mounted."
[*]Then I searched google for the first error message in step 5. above and found this tutorial to fix this problem in Ubuntu and since Lubuntu is based on Ubuntu I guessed it might just work. Here is the tutorial: [www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/")
[*]I did everything it said and have got the same errors as in step 5.
[/LIST]

I have also tried this tutorial to get it going: [www.7tutorials.com/how-change-workgroup-ubuntu-linux-work-windows]("http://www.7tutorials.com/how-change-workgroup-ubuntu-linux-work-windows")
But again this did not work as there was no way to click on the folder to enable file sharing and or installation of Samba.

Samba is installed now though if that helps.

Hope this helps.

Cheers,

Alex

---

### Post by TheFu on 2014-05-31
That how-to is opposite of what you want, right?  It is about sharing files from Linux to Windows.  
Didn't you want to share files from Windows to Linux?

Let's go the direct route.
In pcmanfm's URL bar, enter something like this:
smb://192.168.1.33/

The IP address needs to be the IP address of the Windows machine on your network.  Mind is "smb://172.22.22.14/" then I'm prompted for the userid, workgroup, and password to connect.  I was unable to get WORKGROUP changed in the GUI, to help browsing.

The issue with this method is that on many home networks, IP addresses change all the time. We can try to solve that later, assuming we can't find a way to get browsing by workgroup working shortly.

---

### Post by Alex_Rodriguez on 2014-06-01
Hi,

I followed the method to get access to the windows files and it worked perfectly - once I created a windows password.

Now the next thing is I would like to print and use my scanner which both are connected to my Win 7 PC. These are the steps I tried in Lubuntu to set-up a printer:
[LIST=1]
[*]Start Menu -> System Tools -> Printers
[*]This opens a dialog box with the word "Add" in it.
[*]I clicked "Add" and selected Network Printer
[*]Then I clicked onto "Find Network Printer"
[*]Then a box opens on the right with Host: and I typed in my Win 7 IP address and clicked find.
[*]It asks for my Win 7 username and password and I put it in and it comes back with no printer was found at that address.
[/LIST]

My Win 7 computer is on and the printer attached to it is on also.

What must I do to get the printer working?

Cheers,

Alex

---

### Post by TheFu on 2014-06-01
> **Alex_Rodriguez said:**
> 
My Win 7 computer is on and the printer attached to it is on also.

What must I do to get the printer working?

Glad the file access is working.
For the printer to work, did you enable printer sharing in Windows to "everybody"? [http://windows.microsoft.com/en-us/windows-vista/enable-file-and-printer-sharing](http://windows.microsoft.com/en-us/windows-vista/enable-file-and-printer-sharing)

Did you load the specific printer driver in Ubuntu?  Which printer exactly is it?

---

### Post by Alex_Rodriguez on 2014-06-02
Hi,

After reading your reply I did the following things:

[LIST=1]
[*]Double checked that printer sharing was enabled on my Win 7 machine. Found out that file and printer sharing was enabled but sharing of the actual printer itself was not, fixed that with this link: [http://windows.microsoft.com/en-us/windows/share-printer#1TC=windows-7](http://windows.microsoft.com/en-us/windows/share-printer#1TC=windows-7) (which is a link that branched of from the link you gave me, so thanks)
[*]Went back to the Lubuntu machine and followed my steps that I had added previously and managed to locate my printer that is attached to my Win 7 computer.
[*]Put in my Authentication details clicked "Verify" and the printer was verified.
[*]Then I clicked "Forward" then I waited, and waited for something to happen... I guess it was looking for the driver that I have not installed.
[/LIST]

The printer is a FujiXerox DocuPrint 203A and I have not installed the driver for it in Lubuntu - I do not know how. Could you please help me? I am really forward to printing a test page...

Kind regards,

Alex

---

### Post by TheFu on 2014-06-02
Until you load the drivers, there really isn't much hope besides creating PDF files and manually printing those from Windows.
Google found this: [http://ubuntuforums.org/showthread.php?t=1396366](http://ubuntuforums.org/showthread.php?t=1396366)

---

### Post by Alex_Rodriguez on 2014-06-05
Hi,

I had a look at the link did some further research and got bogged down in a lot detail regarding free drivers on this website:
[http://www.openprinting.org/download/kpfeifle/LinuxKongress2002/Tutorial/II.Foomatic-User/II.tutorial-handout-foomatic-user.html](http://www.openprinting.org/download/kpfeifle/LinuxKongress2002/Tutorial/II.Foomatic-User/II.tutorial-handout-foomatic-user.html)

So, I decided to look for an easier alternative. I went to the FujiXerox website that had the appropriate driver for my printer: 
[http://www.fujixeroxprinters.com.au/en/Downloads.aspx?product=5411&category=5726](http://www.fujixeroxprinters.com.au/en/Downloads.aspx?product=5411&category=5726) and downloaded the linux driver. I uncompressed the zipped folder
and inside it contained a folder called deb and another folder called rpm. After doing further research, I found out that the deb was for debian based distros such as
Lubuntu and Ubuntu etc and the rpm was for Redhat etc. So I double clicked the contents of the deb folder and installed these two files:
[LIST=1]
[*]cupswrapperdocuprint_203_a-1.0.2-2.i386.deb
[*]docuprint_203_a-lpr-1.1.2-4.i386.deb
[/LIST]
I then opened up the printer install dialog box as previously described above and went to add the printer. Except this time it had a little icon of a printer called Docuprint 203 A inside of it.
I double clicked the icon and it opened to the settings tab. I clicked on change the Device URI and selected network printer. I put in my password etc and clicked apply and it comes back with the following error: CUPS Server Error There was error during the CUPS operation: 'client-error-not-possible'. I have done a lot of Googling since and have not been able to solve this problem. Can you help?

Cheers,

Alex

---

### Post by TheFu on 2014-06-05
Every printer is a little different and I don't have this model and I share printers going the other way (connected to Linux, not Windows).

Seems like you are making progress and your description makes perfect sense.
Don't worry, this will be 5-10 minutes next time, not weeks. You are learning much - sorta like learning a new language.

Have you tried sharing the printer from Windows with "everybody"?  No userid/credentials should be required.

---

### Post by Alex_Rodriguez on 2014-06-06
Hi,

I tried sharing the printer with everybody but got the same error. 

Here I will just add a bit more detail that was accidentally left out of my last post. The final steps are as follows:
(After I open the printer dialog box, double click on the printer icon, click change Device URI)
[LIST=1]
[*]I put in my authentication details
[*]Click "Verify"
[*]Get, the response of, "Print Share Verified - This Print Share is accessible." (This makes me think its not an authentication issue)
[*]I click "ok" (On the print share being accessible part)
[*]Then to finish the change of address for the Device URI box from USB to Network Printer, I click Apply
[*]Then I get the error:
[/LIST]
"CUPS Server error, There was an error during the CUPS operation: 'client-error-not-possible'"

Perhaps, my printer can not be used on a network (I did update the driver on the Win 7 computer, but that made no difference). Do you have any further thoughts to overcome this problem? From my researching I have seen that other people have had the same problem but just with a different laser printer. So your further help would be appreciated.

If the network problem can not be solved then I may have to use a USB stick to print documents - though I am not giving up yet.

Kind regards,

Alex

---

### Post by TheFu on 2014-06-06
Why use a USB drive?  That is just crazy talk when there is a network.
Export the files to PDF to the shared storage, remote into the other machine and print the PDF file.

There shouldn't be any need to authenticate anything. Just sayin'

Any printer can be shared over a network if the hostOS handles things correctly.  I've never seen a printer that worked under Linux NOT be able to share it over the network. Have you considered moving which system to which the printer is connected?  Heck, if you can connect the printer to the Linux machine temporarily, get it working that way, you'll know that the driver is working correctly, even if you put the connection back to Windows.

On my netbook, I connect to a remote printer menu-->preferences-->printers (I'm running LXDE), which opens a printer configuration window.  Inside there is an "add" button. Click it - Network Printer - Find Printer - type in the remote hostname (qbe in my case) - it automatically found the printer at ipp://qbe:631/ipp .   Click "next" - searching for drivers ... then a list is provided.... I select the vendor (Samsung), then printer model ... there are 2 drivers, with 1 "recommended", which I choose.  I'm shown a name-the-printer dialog and accept the defaults.  Print Test Page is offered. I do - it worked.   That's it. Done.

By any chance, have you visited the local web interface to CUPS? [http://localhost:631/](http://localhost:631/)  There may be something in there of help.

---

### Post by Alex_Rodriguez on 2014-06-07
Hi,

I just went to the address you gave me [http://localhost:631/](http://localhost:631/) and used the Administration tool to try and set-up my printer. The part I got stuck on and I cannot resolve is choosing my Device URI for my printer/server. I tried just about every combination suggested on this page ([http://localhost:631/help/network.html](http://localhost:631/help/network.html) ) but I could not print a CUPS test page out on my printer. So I am going to try and contact my printer company and see if they can give me the correct URI to use with that printer.

On another issue, my printer is a GDI printer which apparently is designed to be used with Windows OS, more info here: 
[http://www.openprinting.org/printer/Generic/Generic-GDI_Printer](http://www.openprinting.org/printer/Generic/Generic-GDI_Printer) I found out it was a GDI printer by looking at the brochure about the printer from the manufacturers website.

Using the printer, on my linux machine is not convenient even for a short time.

So I think its back to the manufacturer for me. 

I think in the future I will buy an HP printer apparently they are more compatible with Linux.

Thanks for all your help.

Cheers,

Alex

---

### Post by bertan2 on 2014-06-07
I found the manual for your printer by Googling. [http://www.fujixeroxprinters.com.au/downloads/uploaded/dp204a_ug_aa58.pdf](http://www.fujixeroxprinters.com.au/downloads/uploaded/dp204a_ug_aa58.pdf) Follow the instructions on page 4-9 to print the printer settings page. It should give you useful information on the printer's settings and capabilities that will allow you to specify the URI that CUPS needs.

---

### Post by Alex_Rodriguez on 2014-06-08
Hi,

I went to the link that you gave me and could not find the Device URI. However, there is a whole lot of useful info in there about how to maintain my printer - so thanks anyway. I have written to the support people for FujiXerox and hopefully they will get back to me with an answer. I will let you know what it is and whether the printer now works or not via the network.

Thanks and cheers,

Alex

---

### Post by Alex_Rodriguez on 2014-06-11
Hi,

Just a final note to everyone to thank them for their inputs. I contacted Fuji Xerox and one of their support Engineers did some tests and found that it is not possible to network a Win 7 PC with an attached Fuji Xerox DocuPrint 203 A printer via its USB port with a PC running Lubuntu. It is possible to network if all machines are running Windows though. Its also possible to network with a standalone printer which is network capable - it connects directly to the network and has its own IP address. Since I am in none of the two latter positions this problem cannot be solved unless of course there are changes to Lubuntu itself, I guess.

I won't bother trying to connect my scanner via the network. I will just use the good old USB stick or public folder to transfer files between my computers - to print and scan.

The Device URI for my Fuji Xerox is: ipp://ip-address this is only useful if you have a standalone version of that printer with its own IP address.

Thanks again,

Cheers,

Alex

P.s. It is of course possible to directly connect a printer and scanner to a PC running Lubuntu, but that was not my question.

---

### Post by TheFu on 2014-06-11
Xerox is going to provide that answer whether it is possible or not.  I wouldn't believe it.  If it isn't "officially supported", they cannot answer in any other way.

---

