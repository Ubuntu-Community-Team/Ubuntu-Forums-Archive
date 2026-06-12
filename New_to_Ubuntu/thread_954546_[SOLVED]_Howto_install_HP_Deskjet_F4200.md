---
title: "[SOLVED] Howto install HP Deskjet F4200"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Chris Edgell on 2008-10-21
Please tell me if you know a place to click to install.  The places I've been don't show Linux installations.  (Or give me a phone number for tech support)

---

### Post by Chris Edgell on 2008-10-21
Now I've gotten as far as the Linux download, the icon landed on my desktop.  When I try to run it in the terminal I get the message command not found.  When I click on the icon an AbiWord screen opens and just stays blank.  Any ideas?

---

### Post by wolfen69 on 2008-10-21
normally, all you have to do is make sure the printer is plugged in and turned on. ubuntu will install it automatically. however, i am not as familiar with xubuntu. check synaptic package manager and search for hplip. install it if you do not have it. you should be done then.

---

### Post by timcredible on 2008-10-21
what are you trying to run?  for hp printers, just plug it in and reboot your pc, the hp drivers are already on the ubuntu livecd, so you already have it.

---

### Post by Chris Edgell on 2008-10-21
Thanks...   Now, I've scanned a document and it was printed but when I press "Print" it doesn't print.  (If the scan prints does that necessarily mean that the driver is in place?)  When I get the print box, the default is "Generic postscript" the other category is "Create a PDF Document" (what's PDF?)  Then another selection box is Location, the default here is Ipr, the other choices are file, or custom

I'm going through the tiny handbook, but haven't yet found the answer to my problem.

---

### Post by wolfen69 on 2008-10-21
you need to go to printing preferences and make your printer the default.

---

### Post by Chris Edgell on 2008-10-21
If I click settings>default printer>PDF is highlighted  I have the choice of Set default or use system default.  I don't find a place that says preferences, where is it?

---

### Post by wolfen69 on 2008-10-21
i'm not sure where it is in xubuntu, but look in the menus for "printing". then just highlight your printer on the left, and then click the button "set as default".

---

### Post by fballem on 2008-10-21
A couple of things that may help:

According to the HPLIP website, you need version 2.8.5 of the hplip utility. If you're running ubuntu 8.04, then the one that is in the repository is 2.8.2, which won't work with your printer.

The download site is here: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

The instructions are here: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html). Please read these first. It is fairly easy, but it will help you to know what to expect.

When you download the file, save it to your desktop - it's one of the options for downloads.

Once you have downloaded, you will need to remove the existing hplip installation. You can do this through Synaptic:

[LIST=1]
[*]Select System > Administration > Synaptic Package Manager
[*]Enter your password
[*]When the list comes up, do a search for 'hplip' (without the quotation marks.
[*]It will show an entry for hplip. If it installed (the box is coloured in), then right-click and select 'Remove All' from the options.
[*]This will give you a list of all of the things that will be removed. Select OK. **These will be replaced when you install the new version.**
[*]Select 'Apply' and hplip will be removed.
[*]Close Synaptic - you are done with this part of it.
[/LIST]

To install the new version:
[LIST=1]
[*]Open a Terminal. This can be done from Applications > Accessories > Terminal.
[*]Type: cd ~/Desktop and press [Enter]. This should change the prompt in your terminal.
[*]Type: sh hplip-2.8.9.run and press [Enter]. This will give you information, which you will already have seen in the installation instructions. Along the way, you will be asked for your password.
[*]When the operations are complete (it can take a while), you will be presented with some screens to actually set up your printer. If all went well, you should have a test page printed out.
[/LIST]

Hope this helps,

p.s. PDF is Portable Document Format - it is an electronic format that can be read using Adobe Acrobat Reader and similar programs like Evince.

---

### Post by Chris Edgell on 2008-10-21
(I may have to talk to the guy who set me up, I don't have a lot of options I recall having with windows.....printing menus, I don't find anything like that.

Now, fballem, In your first sentence you say "If you're running Ubuntu 8.04 then the one that is in the repository is 2.8.2 which won't work with your printer.  But when I go to that first website it says I'd be downloading 2.8.9 which is the one that landed on my desktop, or at least the icon did.

---

### Post by Chris Edgell on 2008-10-21
Now I've gone to the synoptic mgr and it has about 8 lines of 2.8.2 which IS what you said wouldn't work for me.  Even tho as that prev comm states it said it would be .... .9 but it was .2  But still when I go to the two websites you have shown me, I seem to find only downloads of the .9 (which is what has been turning into the .2)

---

### Post by fballem on 2008-10-21
Synaptic is showing you what is currently installed: hplip 2.8.2. If you follow the first set of instructions that I gave you, then that will uninstall 2.8.2. You do not want 2.8.2

What landed on your desktop is 2.8.9, which is the one that you do want. If you follow my second set of instructions, then that's the one that will be installed.

Once version 2.8.9 is installed, your printer should work, in theory. I do know that your printer is not supported in 2.8.2.

Hope this clarifies things for you.

Regards,

---

### Post by fballem on 2008-10-21
How are you doing with your printer?

---

### Post by Chris Edgell on 2008-10-21
I did go through all those many steps and spent quite a few minutes in that terminal step. but then at long last, it told me that it had failed and I must do the set-up manually.  But I did see it go thru and add the parts I needed and fix and make clean, oh so many steps it did correcting errors.  I'm sorry to say I have to go out now for a couple of hours, but will be back at it then, especially if you have any more advise for me.  I thank you so, I've learned a lot from you, you've been so nice and patient.

---

### Post by Chris Edgell on 2008-10-21
I'm sorry, I just wanted to say, I just went to the synoptic mgr and nothing is installed.

---

### Post by fballem on 2008-10-21
When the installation is complete, it won't show in Synaptic. Synaptic will show only the items that are installed through the repository.

Anything that you install externally, such as hplip 2.8.9, will not show up. For your reference, if you have future problems and the instructions include 'sudo apt-get ... ', these will show up in Synaptic once it's done. apt is a command line interface that does the same thing as Synaptic. This installation of hplip does not use apt.

---

### Post by Chris Edgell on 2008-10-22
For the first time I got all the way to the Setup Wizard.  I got to the point where it said "no devices found"   USB bus
Please enter USB ID for the printer

---

### Post by Teamgeist on 2008-10-22
post output of ```
lsusb
``` please

---

### Post by Chris Edgell on 2008-10-22
Thank you all, finally, after understanding that it was all correctly installed, I just had to go over the instructions and I actually just connected it to the port that was there instead of using the adaptor that I had been using with my last computer.  
I learned so many lessons in the last two days, one-from so many of you;and two-from a site called Tutorials on Forum Basics.  I saw all I had been doing wrong, including being in a big hurry-not stopping to see if I could think through something; if I could study something on the tutorials.  Anyway thank you all for your help and patience.

---

### Post by fballem on 2008-10-22
> **Chris Edgell said:**
> Thank you all, finally, after understanding that it was all correctly installed, I just had to go over the instructions and I actually just connected it to the port that was there instead of using the adaptor that I had been using with my last computer.  
I learned so many lessons in the last two days, one-from so many of you;and two-from a site called Tutorials on Forum Basics.  I saw all I had been doing wrong, including being in a big hurry-not stopping to see if I could think through something; if I could study something on the tutorials.  Anyway thank you all for your help and patience.

Glad it worked, and thanks for marking the thread as solved. It will make it much easier for others who are experiencing a similar problem.

Regards,

---

