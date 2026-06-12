---
title: "Cups-pdf not printing"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by jesrani on 2008-11-15
I have just installed Xubuntu on an old PC (Overwritten Freespire) and I have installed LXDE desktop. Seems to be running well. I installed Samba and was able to install a Network Printer, but I am having problems with cups-pdf which I need to make pdf's. I have read several forums and installed the printer but there is no output. When I open the Printer configuration tool and see the properties for "CupsPDF" and then click "Pint Test Page" there is a messege besides this "Processing /usr/lib/cups/backend/cups-pdf failed"
I tried to find on net and did few things but nothing works. What to do? When I try "/etc/init.d/cupsys restart" command it does not work but the command "/etc/init.d/cups restart" works.
Please help as I am stuck with this.

---

### Post by Kellemora on 2008-11-15
Hi J

Samba is technically for connecting to a WinDOZE machine! But works fine with other machines too.

Have you SHARED the printer on the Network?

Can you see the printer from your machine if you type smbtree?

Sorry I can't be of more help!

TTUL
Gary

---

### Post by jesrani on 2008-11-15
Any help on this anyone?? What do I do now to get PDF printing working in Xubuntu?

---

### Post by Keen101 on 2008-11-15
You can't share cups-pdf over samba. I've tried, it won't work. I'm not sure if the printer test page feature works with cups-pdf either.

But, it should work fine from within the (x)ubuntu machine. To test it go to a random webpage (or this one) and press "print" from within firefox. Then select your cups-pdf printer. It should work fine. Tell us if you still have problems.

---

### Post by jesrani on 2008-11-15
> **Keen101 said:**
> You can't share cups-pdf over samba. I've tried, it won't work. I'm not sure if the printer test page feature works with cups-pdf either.

But, it should work fine from within the (x)ubuntu machine. To test it go to a random webpage (or this one) and press "print" from within firefox. Then select your cups-pdf printer. It should work fine. Tell us if you still have problems.

My cups-pdf is not working from within Xubuntu itself. I think you must have got confused as I wrote about a SMB printer. Sorry.
Anyways, I seem to have done everything but the cups-pdf doen not give any output. No PDF directory is created in /home/user folder.

---

### Post by Keen101 on 2008-11-15
hmmm... cups-pdf isn't working on this particular machine either. weird. 


Is your system an 8.10 version? Mine is... this might be another 8.10 regression....But, i did notice this message when i went to print...

does yours have the same message? This might be the problem. (at least on my system.) I will go a googling now.............

**edit:**  found this...([http://ubuntuforums.org/showthread.php?t=939689](http://ubuntuforums.org/showthread.php?t=939689))

**edit #2:** we'll i looked in that folder (on my system), and it is actually not there, so the above method will not work. I think i will try reinstalling cups-pdf with synaptic package manager.... i will tell you how it goes....

**edit #3:** Well, what do you know.. the package "cups-pdf" wasn't even installed on my system. I had a PDF printer set up, but the actual files were not installed... go figure... i hope your problem is an easy one too. good luck.

**edit #4:** well, looks like i spoke too soon. Even though cups-pdf is now actually installed, i now get the error "/usr/lib/cups/backend/cups-pdf failed!". This is not good. It is really starting to look like a 8.10 regression, i might have to look on launchpad to see if there is already a bug report. Hopefully i can find an easy fix for this. I also hope your problem is different and/or easier to fix than mine.

---

### Post by jesrani on 2008-11-15
> **Keen101 said:**
> hmmm... cups-pdf isn't working on this particular machine either. weird. 


Is your system an 8.10 version? Mine is... this might be another 8.10 regression....But, i did notice this message when i went to print...

does yours have the same message? This might be the problem. (at least on my system.) I will go a googling now.............

**edit:**  found this...([http://ubuntuforums.org/showthread.php?t=939689](http://ubuntuforums.org/showthread.php?t=939689))

**edit #2:** we'll i looked in that folder (on my system), and it is actually not there, so the above method will not work. I think i will try reinstalling cups-pdf with synaptic package manager.... i will tell you how it goes....

**edit #3:** Well, what do you know.. the package "cups-pdf" wasn't even installed on my system. I had a PDF printer set up, but the actual files were not installed... go figure... i hope your problem is an easy one too. good luck.

Yes my system is 8.10.

I have Cups-pdf installed on my system so now I am still stuck up.

This should be really have been simple like in Windows.

Any more ideas???

---

### Post by handydan918 on 2008-11-16
I really can't be sure what you are trying to accomplish. 
Are you trying to print a pdf? are you trying to print a pdf to a file? 

Other?

---

### Post by Keen101 on 2008-11-16
Well, i guess cups-pdf is obsolete now. I have no idea why nobody mentioned this to me! arghh...

these two threads kept mentioning a thing called "print to file", but i couldn't figure out what they were talking about until now. 

[http://ubuntuforums.org/showthread.php?t=947960](http://ubuntuforums.org/showthread.php?t=947960)
[http://ubuntuforums.org/showthread.php?p=5963209](http://ubuntuforums.org/showthread.php?p=5963209)

[B]..anyway i figured out what is now the equivalent...

Use the "print to file" option instead....[/B]

mark this thread as solved if this fixed your problem.

---

### Post by jesrani on 2008-11-16
Yes. I am able to use the Print to file option. However I am not sure if this will work in everything. I do not get the option in Openoffice but OOo has its own pdf output so thats ok.
For the time being I am ok, however I cant say the problem is solved.
Thanks for the help.

---

