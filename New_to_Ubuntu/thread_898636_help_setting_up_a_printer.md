---
title: "help setting up a printer"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by DFord425 on 2008-08-23
I have never set up a printer to my linux computer but i just got a new printer that has wireless. I went into system settings->printers and im using the add a printer wizard. I got to a list of HP models but i dont see the model i have. Is there anyway to update the list or is there another way to set it up? I have an HP Photosmart C7280

---

### Post by echo314 on 2008-08-23
A quick search on google shows that one person solved this issue be installing the 'hpijs-ppds' package. Give that a try.

---

### Post by tuxulin on 2008-08-23
i think hp does support the c7200 series
the site is quite helpful too.
[http://hplip.sourceforge.net/models/photosmart/photosmart_c7200_series.html](http://hplip.sourceforge.net/models/photosmart/photosmart_c7200_series.html)

good luck
Tuxulin

---

### Post by DFord425 on 2008-08-23
Thanks for your help, im gonna go try it now

---

### Post by DFord425 on 2008-08-24
I downloaded hplip-2.8.7.run to install the derivers and i run it in command line. When i do that, i get this error ```
Running 'sudo apt-get install --yes --force-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 100

```. Does anyone know what that error is? I looked around the website [http://hplip.sourceforge.net/models/...00_series.html](http://hplip.sourceforge.net/models/...00_series.html) which is where i got the file to install it. Has anyone else had this problem?

---

### Post by alienexplorers on 2008-08-24
Run:

sudo apt-get install libsnmp-dev

Then re-run the installer..and it should work.

---

### Post by DFord425 on 2008-08-25
I ran that and got this error:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
What does that error mean?

---

### Post by panhandle on 2008-08-25
What happens with CUPS?

---

### Post by teeleef on 2008-12-16
I think it means you already have another synaptic package manager running?


Teeleef

---

### Post by bumanie on 2008-12-16
> **DFord425 said:**
> I ran that and got this error:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
What does that error mean?

You have two administrative tools open together.

---

### Post by starcannon on 2008-12-16
Doh, just realised someone resurrected this post, well, I'll leave my solution up anyway.

Heres how I get my HP printers going on gnome, your using Kubuntu I just notices, so menu locations may be different, process should be the same; its actually pretty easy once you know how, so hang in there :)
```

sudo apt-get install hplip hplip-gui

```**If your printer is detected**:

[LIST=1]
[*]Go to System>Administration>Printing
[*]Click New (delete a failed printer install if it is present)
[*]My HP printers generally show up in the next window at the top of the list
[*]Select your printer from the list
[*]Click Forward
[*]Choose HP from the menu
[*]Click Forward
[*]Scroll down the list of drivers till you get to C7200
[*]Select Photosmart C7200
[*]Click Forward
[*]Click Apply
[*]Go to System>Preferences>HPLIP Toolbox
[*]Your printer should show up in the left window pane
[*]Choose the Actions tab
[*]Click Print Test Page, click Print Test Page again in the pop-up window
[*]If things are working correctly you have a test page printed, and are all set up.
[/LIST]
going out for cigarette will post the not detected portion when I get back.

**If your printer is not detected**:

[LIST=1]
[*]Go to System>Administration>Printing
[*]Click New (delete a failed printer install if it is present)
[*]Select your AppSocket/HP JetDirect from the list
[*]Click Forward
[*]Choose HP from the menu
[*]Click Forward
[*]Scroll down the list of drivers till you get to C7200
[*]Select Photosmart C7200
[*]Click Forward
[*]Click Apply
[*]Go to System>Preferences>HPLIP Toolbox
[*]Your printer should show up in the left window pane
[*]Choose the Actions tab
[*]Click Print Test Page, click Print Test Page again in the pop-up window
[*]If things are working correctly you have a test page printed, and are all set up.
[/LIST]
That should do it, post back if you run into problems.

---

### Post by Captain_tux on 2008-12-16
Check out this thread... it was the perfect solution for me:

[http://ubuntuforums.org/showthread.php?t=813149&highlight=5180](http://ubuntuforums.org/showthread.php?t=813149&highlight=5180)

Good luck!

---

