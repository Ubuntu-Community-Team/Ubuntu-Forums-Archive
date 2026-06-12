---
title: "[SOLVED] Installing a Brother DCP-110C printer"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Mr. Svinlesha on 2008-05-20
Hi.

I have a Brother DCP-110 printer, which I had a hell of time installing under Gutsy Gibbon.  When I upgraded to Hardy Heron it stopped working again.  Can anyone help me get it running again, or point me to a how-to?

Thanks in advance.

---

### Post by forestpixie on 2008-05-20
Might help - there are apparently drivers from brother available - your model is on the page

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

this is the installation page

[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html)

---

### Post by Mr. Svinlesha on 2008-05-20
Thanks, **forestpixie**.  You've been a really great help.

---

### Post by avtolle on 2008-05-20
Also, see this; I believe the driver you need is in the repositories, no need to download from the Brother site.
[https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(Brother](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(Brother))

---

### Post by Mr. Svinlesha on 2008-05-20
Well, what do you know.

I found a lot of drivers and what not through synaptic.  Should I just install all of them?

---

### Post by avtolle on 2008-05-20
> **Mr. Svinlesha said:**
> Well, what do you know.

I found a lot of drivers and what not through synaptic.  Should I just install all of them?
No, just the one for your printer (the "extra" ones, if I recall correctly).

---

### Post by Mr. Svinlesha on 2008-05-20
Error message in synaptic:

> E: kio-umountwrapper: subprocess post-removal script returned error exit status 2


Of course.  And the printer doesn't work.  I get a que and an icon, but when I try to print, the job is stopped after a few seconds.

---

### Post by avtolle on 2008-05-20
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793) was my guide to installing a Brother MFC-240-C on Hardy before the drivers were added to the repositories. What I'd suggest is uninstalling the drivers you installed from Synaptic, and using this get the drivers and install. As you are running 8.04, please see the information posted on the FAQ page of the Brother site about the need to create a file which 8.04 apparently doesn't create automatically, which is needed for the driver to correctly install.

---

### Post by Mr. Svinlesha on 2008-05-20
Okay.  Thanks again.

---

### Post by Mr. Svinlesha on 2008-05-21
Well, I've made a real hash of things.

It was late last night and I was tired while posting and working with the printer install, and did a few things I probably shouldn't have done.  To start with, when I found the brother-cups-wrapper-extra and the brother-lpr-driver-extra in Synaptic I just went ahead and tried to install them directly.  Synaptic told me it needed to remove some files and install some files, and I told it to go ahead.  Shortly afterwards I got the error message I posted above:

> E: kio-umountwrapper: subprocess post-removal script returned error exit status 2 

That was in synaptic.

Synaptic is a bit of a mystery to me anyway, I don't really understand it or how/why it removes/installs/reinstalls all of these files with strange names and so forth all the time, so I tend to avoid it.  Anyway, I'm not completely sure about what I've done, but I think I partially installed both the lpr-extra and the cups-extra.

**avtolle** says I should start by uninstalling the drivers I've already installed and then following the instructions at the Brother's FAQ.  Problem is I don't know what I've installed, how much has been installed, or how to uninstall the stuff that's there.  I don't know how to locate these drivers on my computer with Synaptic -- I don't find them in the list of installed packages.

When I start synaptic it tells me that I have  "1570 installed, 0 broken, 0 to install or uppgrade, 1 to remove," and I have no idea why it wants to remove one package; but when I try to apply the changes, I get the following error message:

> E: kio-umountwrapper: subprocess post-removal script returned error exit status 2

Let us turn the next problem.  When I attempted to install last night, a printer icon showed up (for the first time) in one of my toolbars.  So, being a bear of rather little brains, I decided to go ahead and try to print something despite the previous error messages.  No dice.  As wrote earlier, the document queues up but then stops with the following error message: 
> Printer 'DCP-110C': 'cups-missing-filter' 
When I try to cancel the item, I get the following "CUPS server error":
> There was an error during the CUPS operation: 'client-error-not-possible'. 

I suspect that the reason Synaptic can't successfully remove "kio-unmount wrapper" is because there's a document queued in the printer that I can't remove.

Oh, woe is me.  Can anyone help the widow's son?

---

### Post by HotShotDJ on 2008-05-21
> **Mr. Svinlesha said:**
> Oh, woe is me.  Can anyone help the widow's son?I can't resist melodrama! :)  Lets try the catch-all fix-er-up command (it may or may not work)```
sudo dpkg --configure -a

```

---

### Post by Mr. Svinlesha on 2008-05-21
Groovy.  If you like melodrama, you've come to the right place.  My wife tells me that I' *very* melodramatic.

:)

Anyway, I ran your command and it started update manager, which preceeded with a "partial upgrade;" reinstalled this kio-unmountwrapper and removed 89 obsolete packages. (It was very dramatic.)

Now my queued printing job is gone, but the printer icon is still there along with the "cups-missing-filter" error.

I have to go to work in a few minutes so I'll be out of the loop for a few hours...but I'm guessing the "cups-missing-filter" error is related to problem **avtolle** referred to earlier: that you have to manually create a folder for the cups files.  I saw that reference somewhere but have lost it again.

Anyway, Synaptic is clean again as well.  Next step, anyone?

PS: Thanks, HotShot.

---

### Post by plucky on 2008-05-21
> Synaptic is clean again as well. Next step, anyone?


Open Synaptic and search for **DCP110** and you should find > cupswrapperdcp110c
DCP110clpr
with green boxes next to them if the previous install went ok.Select the boxes and mark for complete deinstallation and **APPLY**

IF THAT WORKS -and the two drivers are deinstalled,then again in Synaptic search for **Brother**. You should find a list of Packages all starting with Brother. 

Select the packages **brother-cups-wrapper-extra** and **brother-lpr-drivers-extra** and mark for installation and **APPLY**.

Again it that works then go to System > Administration > Printing and with printer powered on,Cups should find and install it.

Good Luck

---

### Post by avtolle on 2008-05-21
Clarification on something I posted to this thread yesterday. The missing file problem (hopefully) only exists if one is installing the drivers from the Brother website. If the drivers are installed from the repositories (not tried this myself, as I did the installation of drivers from the Brother site), it would be logical to think that the file needed would be created as part of the installation from Synaptic. However, it is something to keep in mind if problems persist after following plucky's post.

---

### Post by avtolle on 2008-05-21
> **plucky said:**
> Open Synaptic and search for **DCP110** and you should find 
with green boxes next to them if the previous install went ok.Select the boxes and mark for complete deinstallation and **APPLY**

IF THAT WORKS -and the two drivers are deinstalled,then again in Synaptic search for **Brother**. You should find a list of Packages all starting with Brother. 

Select the packages **brother-cups-wrapper-extra** and **brother-lpr-drivers-extra** and mark for installation and **APPLY**.

Again it that works then go to System > Administration > Printing and with printer powered on,Cups should find and install it.

Good Luck

I think he needs to mark brother-cups-wrapper-extra and brother-lpr-drivers-extra, together with brother-common at least for complete removal. If he searches for the specific drivers you indicate, I don't think he will find them. Then he should mark the appropriate packages for installation as you point out.

@ Mr. Svinlesha: I just used the appropriate packages from the repositories to install the drivers for my MFC-240C on a new install of Linux Mint 5 Beta, which I am testing for use (potentially) by our younger daughter. No attempt had been made to install this printer previously, so I was working with a clean slate. Installed from Synaptic, and all is well; no need to add the "missing file", as the Synaptic install apparently took care of it. So, my current recommendation is to follow plucky's advice, as indicated previously, and let us know how it goes.

---

### Post by Mr. Svinlesha on 2008-05-21
First off, I just want to say  you guys aren't just great -- you're really great.  Thanks for all the help and suggestions.

Secondly, I must sadly report that your suggests haven't worked.

I followed **plucky's** instructions, and they *seemed* to work, but of course the printer didn't.  Then I did something really stupid (probably): I figured I probably needed to remove the printer entirely, so I deleted it from System > Administration > Printing.  Then I redid the whole process from scratch. Then I reselected the printer.  Again, no dice.

Can I have missed a step?  The last time I tried to install this printer, I was forced to reinstall Ubuntu from scratch before I got it to work.  Please tell I'm not going to have to go through that again.

---

### Post by plucky on 2008-05-21
Mr. Svinlesha,

Open a terminal and input ```
lsusb
lpstat -v
lpq
```

Copy and paste to forum.What errors do you get when you try to print?

Start Firefox and put in address bar ```
http://localhost:631/
```will take you to the CUPS printer page.See what you can do to troubleshoot the printer.


Good Luck

---

### Post by Mr. Svinlesha on 2008-05-21
lsusb:
> Bus 005 Device 003: ID 041e:4055 Creative Technology, Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f9:0169 Brother Industries, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

lpstat -v
> device for DCP-110C: usb://Brother/DCP-110C
device for PDF: cups-pdf:/

lpd:
> DCP-110C is ready
no entries


I'll check the Firefox page and see what I can find out.

---

### Post by Mr. Svinlesha on 2008-05-21
Well, I can't figure out what might be wrong so far.

I do have this to say: I can't go through this every time I upgrade Ubuntu.  This has to be fixed.  It's really frustrating.

---

### Post by Mr. Svinlesha on 2008-05-21
PS: One possible clue: last time I went into Synaptic, and searched under "DCP110," I found the files you referred to ("cupswrapperdcp110c," "DCP110clpr").

Now they're gone.

---

### Post by avtolle on 2008-05-21
> **Mr. Svinlesha said:**
> PS: One possible clue: last time I went into Synaptic, and searched under "DCP110," I found the files you referred to ("cupswrapperdcp110c," "DCP110clpr").

Now they're gone.
When did you remove them? Before or after you reinstalled the drivers packages from Synaptic? The results of checking localhost:631 suggest that the drivers are installed. I've just had a thought, and will return shortly.

---

### Post by avtolle on 2008-05-21
If you would be so kind as to go back to Firefox and type in [http://localhoust:631/](http://localhoust:631/) in the bar and get to CUPS again, please select "Manage Printers" and see if the driver shows for the printer. If it does, then the next thing I suggest is (an old trick from back in the CP/M days) totally close out the computer, power it and the printer down. Wait about a minute or so, turn on the printer and then turn the computer on, and see what happens.

If, instead, the driver does not show under CUPS, then it will need to be installed again. Just a thought.

---

### Post by Mr. Svinlesha on 2008-05-21
Definitely worth a shot.  The page says DCP110 is my default printer, drivers installed (Brother DCP-110C CUPS v1.1).

Back shortly.

---

### Post by plucky on 2008-05-21
> I can't go through this every time I upgrade Ubuntu. This has to be fixed. It's really frustrating. 

It is now a lot easier now the drivers are included in Synaptic.After the next upgrade,just remember to use Synaptic and not the download from the Brother site.

I reinstalled my printer using the Brother site as I didn't know that the drivers had been included in Synaptic.Everything seems to get a little easier with every upgrade.

Good Luck

---

### Post by Mr. Svinlesha on 2008-05-21
You are a genius.  Worked like a charm.  Thank you muchly.

I'll mark the thread as solved.

Once again, many thanks both to you **avtolle**, and everyone else who's helped me out in this thread.

---

### Post by avtolle on 2008-05-21
Outstanding! Sometimes, those things those of us with a bit of age had to do "back then" still work. It has been a pleasure working with you. Best of luck.
That also goes for you, plucky; a real pleasure.

---

### Post by HotShotDJ on 2008-05-21
> **avtolle said:**
> Outstanding! Sometimes, those things those of us with a bit of age had to do "back then" still work.Isn't THAT the truth. :)  Well done with your assistance in this thread.   After looking at what finally worked, I wonder if simply turning off & disconnecting the printer, restarting the cups server (/etc/init.d/cupsys restart), and then reconnecting and turning the printer back on, would have done the same thing.  Another trick from the old days. :)

---

### Post by avtolle on 2008-05-21
> **HotShotDJ said:**
> Isn't THAT the truth. :)  Well done with your assistance in this thread.   After looking at what finally worked, I wonder if simply turning off & disconnecting the printer, restarting the cups server (/etc/init.d/cupsys restart), and then reconnecting and turning the printer back on, would have done the same thing.  Another trick from the old days. :)
I wondered the same thing myself, but thought it simpler to have him just totally shut down and restart the computer after turning the printer on. Memories of those tricks from "back then" do stay with us, don't they? :-)

And, for me, your assistance with this was also appreciated. The use of the all purpose fix it, as you termed it, slipped my mind, and, given what was happening, was the appropriate step to be taken.

---

