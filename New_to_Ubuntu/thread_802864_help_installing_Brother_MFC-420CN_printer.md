---
title: "help installing Brother MFC-420CN printer"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-05-21
I am trying to install a printer following [this]("http://ubuntuforums.org/showthread.php?t=434731") guide (the guide is about 5 posts down). However, when I type sudo dpkg -i ./mfc420cnlpr-1.0.2-1.i386.deb in the Install LPR Driver step, I get this message:

dpkg: error processing ./mfc420cnlpr-1.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./mfc420cnlpr-1.0.2-1.i386.deb

what's wrong? I downloaded the drivers and saved them to my desktop. Should I unpack them from the desktop also? I was under the impression that I would unpack them using the terminal in a later step. Thanks.

---

### Post by garyed on 2008-05-21
Are you sure you're in your Desktop directory when you type that command in the terminal?

---

### Post by HotShotDJ on 2008-05-21
The drivers are in the repository.  Please delete the downloaded file.  Then use System --> Administration --> Synaptic Package Manager to install.  To determine which driver package you need, please refer to [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

It really couldn't be easier. :)   Have fun and be amazed. ;)

---

### Post by Watchtow3r on 2008-05-21
Are you sure they're in the repository? i searched brother and couldn't find the specific ones. Which ones are they in there? I couldn't find the same ones. I think that's why the guide said he downloaded from the website. Should I just unpack the ones I downloaded from the internet?

Edit: oh nvm I see it now I'll try it and get back to you.

Edit: Yeah thx it worked.

---

### Post by HotShotDJ on 2008-05-21
> **Watchtow3r said:**
> Are you sure they're in the repository? i searched brother and couldn't find the specific ones. Which ones are they in there? I couldn't find the same ones. I think that's why the guide said he downloaded from the website. Should I just unpack the ones I downloaded from the internet?Yes, I am quite sure.  Your printer is contained in the brother "extra" packages. This information is also provided at the web site to which I referred you earlier. To get everything you need, simply install "brother-cups-wrapper-extra" which will pull in all the packages and drivers needed to get your printer printing.  Once installed and you have configured your printer using System --> Administration --> Printing, you may have to reboot before your printer works properly.

Keep in mind, since you did not specify which version of Ubuntu you are running, I am assuming you are using the most recent stable release which would be Hardy Heron (8.04).

EDIT:  Just saw your edit.  I'm glad you found it.  I'll leave the entirety of my post intact for future reference.

---

### Post by koolkev on 2008-05-30
Synopses.
Go to the website;

[https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

Find the category your printer falls into (use a search). Example MFC-420cn falls under the category "EXTRA"  

Go to your toolbar,  System, Administration, Synaptic Package Manager

In Synaptic Package Manager(SPM) search for "Brother" 
In the result of the SPM search look for the file that contains the name of the category your printer falls under. In this case "brother-cups-wrapper-extra"

Mark "brother-cups-wrapper-extra" for installation and install.

Go to System, Administration, Printing, New Printer

Select the printer you want to add;

(In this case) MFC-420cn USB #1

Click Forward
Select from data base radial button should already be chosen marked 
If Brother is not highlighted click to highlight 
Click Forward
Select your printer model form the list that should appear

Name the printer if the default does not appear or is not sufficiently appealing or accurate.

Click Apply

Print a test page

That is how I understand the process. 
Thank you for your help.

---

### Post by okaloosajohn on 2008-06-04
I have both a Brother MFC-420CN and an HP960C connected via USB to my computer.  I have successfully installed the HP960C as my default printer. 

I would like to be able to also use the Brother, but I have followed the instructions above and the Brother does not appear as a choice when I select new printer.

Help!

---

### Post by avtolle on 2008-06-04
> **okaloosajohn said:**
> I have both a Brother MFC-420CN and an HP960C connected via USB to my computer.  I have successfully installed the HP960C as my default printer. 

I would like to be able to also use the Brother, but I have followed the instructions above and the Brother does not appear as a choice when I select new printer.

Help!
Clarification, please; the Brother does not appear when you select "new printer" or "add new printer"?

---

### Post by okaloosajohn on 2008-06-04
> **avtolle said:**
> Clarification, please; the Brother does not appear when you select "new printer" or "add new printer"?

I followed these instructions:

In Synaptic Package Manager(SPM) search for "Brother"
In the result of the SPM search look for the file that contains the name of the category your printer falls under. In this case "brother-cups-wrapper-extra"

Mark "brother-cups-wrapper-extra" for installation and install.

Go to System, Administration, Printing, New Printer

Select the printer you want to add;

I presumed I would see MFC-430cn USB #1 as a choice per the example, but I don't.

---

### Post by avtolle on 2008-06-04
OK, understand. My first thought is to have you restart your system, and see if the Brother shows up when, after restart, you go to System>>Administration>>Printing, New Printer. EDIT: instead of just a restart, totally shut down, turn everything (including printers) off. Wait a minute or so; power up the Brother, then power up the Computer, then go to System>>Administration>>Printing, New Printer, and see if it shows. If it does, add it, then power up the HP and see if that causes any problems.

Second thought, open Firefox, in address bar type in localhost:631 to see if the Brother shows up in the CUPS database. If it does, then you might try adding it from there. 

Just two random thoughts.

---

### Post by okaloosajohn on 2008-06-04
> **avtolle said:**
> OK, understand. My first thought is to have you restart your system, and see if the Brother shows up when, after restart, you go to System>>Administration>>Printing, New Printer. EDIT: instead of just a restart, totally shut down, turn everything (including printers) off. Wait a minute or so; power up the Brother, then power up the Computer, then go to System>>Administration>>Printing, New Printer, and see if it shows. If it does, add it, then power up the HP and see if that causes any problems.

Second thought, open Firefox, in address bar type in localhost:631 to see if the Brother shows up in the CUPS database. If it does, then you might try adding it from there. 

Just two random thoughts.

I had tried all of your suggestions before posting the first time. I even completely disconnected the HP and just left the Brother connected when I rebooted.  No joy.

The Brother does NOT appear in the CUPS database when viewed thru Firefox.

---

### Post by avtolle on 2008-06-04
(Scratching head): Are the two printers connected in different USB ports on the main system, or are they both on a USB hub? Just thinking about conflicts with the USB port on a hub, but that's really a wild supposition on my part.

---

### Post by okaloosajohn on 2008-06-04
> **avtolle said:**
> (Scratching head): Are the two printers connected in different USB ports on the main system, or are they both on a USB hub? Just thinking about conflicts with the USB port on a hub, but that's really a wild supposition on my part.

They are both on a USB hub.  I will connect one to a main port and reboot and see if that makes a diff.

---

### Post by okaloosajohn on 2008-06-04
> **okaloosajohn said:**
> They are both on a USB hub.  I will connect one to a main port and reboot and see if that makes a diff.

Didn't make any difference.  Still not recognizing the Brother...

---

