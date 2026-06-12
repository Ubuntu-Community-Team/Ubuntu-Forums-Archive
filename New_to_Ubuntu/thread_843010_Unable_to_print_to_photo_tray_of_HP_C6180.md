---
title: "Unable to print to photo tray of HP C6180"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by raccoonone on 2008-06-27
I can't get my printer, an HP Photosmart C6180, to print to the 4x6 photo tray. Whenever I select a photo in F-Spot, go to Photo > Print and select Paper source: Photo tray, I get an error on my printer saying: "Paper size of type is incorrect" and a blank piece of photo paper is ejected. Can anyone help me fix this? I print out photos fairly often, and would like to be able to print them to the special photo paper tray.

---

### Post by raccoonone on 2008-07-08
I still haven't figured out how to fix this. I tried printing via Gimp, and setting up a custom paper size, but that didn't help anything. Any suggestions?

---

### Post by bogert2217 on 2008-07-08
I have the exact same problem (C6180, Ubuntu 8.04, printing from F-spot).  The "paper type" selector in the print dialog is greyed out, this is where you would normally select the size of the paper.  This problem started after upgrading to 8.04.

I am able to print to photo paper from the gnome image viewer, after doing "Page Setup" to select paper size, but then the margins are too large.  And this method does not work for F-spot because F-spot does not have a page setup outside of the print dialog.

Any clues?

---

### Post by LowSky on 2008-07-08
May I suggest that you install HPLIP
[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

It is HP source drivers for their printers and uses a different version of CUPS

---

### Post by raccoonone on 2008-07-10
I have the hplip package installed from the Ubuntu repos, is that enough, or should I try to update from the latest source code?

---

### Post by bogert2217 on 2008-07-11
Source should not be necessary, Sourceforce has the latest version of HPLIP in an automatic installer.

I first tried using Applications->Add/Remove, this did not change anything.  Then downloaded the automatic installer from Sourceforce and ran it.  This installer a new printer name, and I can print to it, but with even fewer options :-(.  On the "Page Setup" tab in the F-Spot print dialog, all three options are now "Not Available" (Paper Type, Paper Source, and Output Tray).  Before installing HPLIP, I could select "Photo Tray" in Paper Source.

So the problem persists.

---

### Post by hansdown on 2008-07-12
> **raccoonone said:**
> I have the hplip package installed from the Ubuntu repos, is that enough, or should I try to update from the latest source code?

Hi raccoonone. You probably also need python-qt3 from the synaptic package manager.

---

### Post by raccoonone on 2008-07-12
> **hansdown said:**
> Hi raccoonone. You probably also need python-qt3 from the synaptic package manager.

I just tried installing that, and still no luck. The "paper type" field remains grayed out, and it still gives an error message if I try to print to the photo tray.

---

### Post by hansdown on 2008-07-12
> **raccoonone said:**
> I just tried installing that, and still no luck. The "paper type" field remains grayed out, and it still gives an error message if I try to print to the photo tray.

Hi again raccoonone. I found an hp site that hopefully will help. [http://www.linuxprinting.org/](http://www.linuxprinting.org/) )

---

### Post by raccoonone on 2008-07-12
> **hansdown said:**
> Hi again raccoonone. I found an hp site that hopefully will help. [http://www.linuxprinting.org/](http://www.linuxprinting.org/) )

Thanks. I looked at that site, and it linked to a guide that suggested I use "sudo hp-setup" instead of going through the Administration -> Printing panel, however that didn't help; I still can't print to the photo tray. Any other suggestions?

---

### Post by raccoonone on 2008-07-16
Any other suggestions? I still haven't been able to get printing to work. Should I file a bug report?

---

### Post by raccoonone on 2008-08-19
I found a work around for this. use HP toolbox (hp-toolbox at a terminal), then go to print settings and change the Media Source to Photo Tray, the Media Size to 4x6, and the Printout Mode to Photo. Then use the Print function that HP Toolbox provides :)

---

### Post by David Valentine on 2008-09-28
Thanks, raccoonone, your suggestion worked for me on my HP Photosmart C7280.  I confess I'm a bit disappointed that photo printing is this inconvenient on HP printers, which are supposed to be linux-friendly.

---

