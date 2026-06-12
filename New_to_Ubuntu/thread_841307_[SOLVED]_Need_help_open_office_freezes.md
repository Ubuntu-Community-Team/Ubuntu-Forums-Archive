---
title: "[SOLVED] Need help open office freezes"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by DarinB on 2008-06-26
Hi i need help i am running a clean install hardy and OO 2.4... this just started happening if i try to open any OO app the window freezes. i can force quit. but must reboot to be able to open a document. it is tied to the launchers and application menu. no help at all an the posts yet

---

### Post by sharks on 2008-06-26
wat is ur sys config?

---

### Post by sharks on 2008-06-26
speed up open office:

[www.theinquirer.net/en/inquirer/news/2005/10/28/how-to-speed-up-open-office](www.theinquirer.net/en/inquirer/news/2005/10/28/how-to-speed-up-open-office)
[www.lifehacker.com/software/optimization/speed-up-openoffice-270775.php](www.lifehacker.com/software/optimization/speed-up-openoffice-270775.php)
[www.ghacks.net/2007/08/18/speed-up-open-office/](www.ghacks.net/2007/08/18/speed-up-open-office/)

---

### Post by Elfy on 2008-06-26
I had a similar issue when there were updates coming through proposed about a month ago - in the end I had to uninstall all and reinstall to get it to work.

Luckily I had the oo beta3 so I could take some time to wait for a fix, but I did think that it had been done on the repos.

What do you get if you do soffice from the terminal?

---

### Post by DarinB on 2008-06-26
please clarify.

---

### Post by DarinB on 2008-06-26
soffice does nothing

---

### Post by DarinB on 2008-06-26
after reboot soffice in terminal works

---

### Post by dca on 2008-06-26
Wait a minute, is this caused when you try to open OO through the menu bar 'Applications -> Office -> OO Writer' or is the freeze caused by when you find a file (*.doc, *.odt,) and try double-clicking on it.
 
If you're can't figure out the problem w/ OO you can d/l & install the free vers of IBM's Lotus Symphony 1...  
 
[http://www14.software.ibm.com/webapp/download/symphony/download.htm](http://www14.software.ibm.com/webapp/download/symphony/download.htm)
 
Just make sure you chown the .lotus file in your home directory prior to use...

---

### Post by Elfy on 2008-06-26
or the openoffice beta :)

I had the same deal - running from the menu or from opening an existing file caused it to hang. Running soffice from a terminal ran then I could open whatever I needed.

I had to uninstall all the openoffice packages and reinstall - I used synaptic at the time, then it worked for me again.

But as I said that was when there were some oo updates through the proposed repos and I was under the impression that they were ok now.

---

### Post by DarinB on 2008-06-26
it only works if i click a doc or odt otherwise with the launchers no go

---

### Post by DarinB on 2008-06-26
if i uninstall what will happen to my docs

---

### Post by AlexMono94 on 2008-06-26
Nothing, you just won't be able to open them. You should first try to stop it crashing though by deleting the .openoffice.org2 folder in your home folder (press Ctrl+H and to show hidden folders) and if that doesn't work reinstall it.

---

### Post by Elfy on 2008-06-26
Did you try removing the gtk packkage that was in the other thread you posted in.

Does it work if you make a launcher - is it only the launchers that are in the menus which have a problem.

---

### Post by DarinB on 2008-06-26
removing gtk did nothing...
when i remove the open office.org2 what will happen and how do i reinstall it

---

### Post by DarinB on 2008-06-26
both the in the menus and when i add a launcher to my desktop.

---

### Post by Elfy on 2008-06-26
> when i remove the open office.org2 what will happen and how do i reinstall it

When I do it I use synaptic it seems easier to get all the packages, search for openoffice.org - in the package pane on the right use the S near the top to sort.

Mark all the installed openoffice packages as complete removal, let it do it check there are no residual configs then reinstall them, as long as you get the main packages it should pick up the others that it needs.

If you still get problems try the openoffice 3 beta I use it all the time (nearly) now.

---

### Post by DarinB on 2008-06-26
i unistalled and removed all residual pckgs installed all the OO 2.4 
no change at all?????????

---

### Post by DarinB on 2008-06-26
The adding of the Open Office 3 Beta is a temporary fix.
So if some one can help with the oo2.4 that would be great.

---

### Post by Dr_Bop on 2008-07-06
(Can't believe *I* am trying to help, but...)

I had the same problem.  I was notified on about July 2, 2008 of updates (the usual Ubuntu automatic updates).  I looked at them and there were some OO updates so I accepted all the udpates.  Now things work fine!  They did not before.  The updates were not "version" updates, just the usual stuff.

So, check for updates - if it does not work now, there is probably little to loose!  Mine is fine.

scott

---

### Post by celem on 2008-07-10
In my case, OO 2.4 on Hardy, while editing an opened text document, writer will freeze at random, namely while entering text or while sitting there with nothing being done. It is random. I've never had a problem, even with Hardy until recently, so I suspect the 2.0.01 updates. Nothing else in Hardy freezes - it seems to solely a OpenOffice Writer issue.

---

