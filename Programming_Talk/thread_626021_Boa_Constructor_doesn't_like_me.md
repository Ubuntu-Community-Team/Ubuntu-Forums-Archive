---
title: "Boa Constructor doesn't like me"
date: 2007-11-28
forum: Programming Talk
---

### Post by Majorix on 2007-11-28
I have weird windows with Boa Constructor. I am trying to follow the tutorial that comes with it, and I came to a point where it says to click the 3 dots next to the property called Fields. I go to the Properties window to do so, but when I click on Fields to show the dots, I get a blank line. I have attached a screenshot for you to see.

I thought maybe it could be Compiz interfering, so I went ahead and disabled it but to no avail. I also tried reverting back to the original Human theme for Ubuntu but that didn't solve the problem either.

What do you think is the cause? I so much want to be able to get to use this program :(

---

### Post by Majorix on 2007-11-30
Anybody?

---

### Post by JohnSGruber on 2007-12-14
Is this happening when you are supposed to see a plus +++ button to bring up the Collection Editor to adjust the status bar? If so I have the same problem.

I skipped the changes to the status bar (couldn't get it to remember that I moved it to the bottom of Frame1 either), and proceeded with the rest of the instructions. I got as far as inserting the text control but got a crash when I tried to post those changes to the code.

Have you learned anything elsewhere in the meantime?

John

---

### Post by Majorix on 2007-12-14
Yes, we have the same problem.

In the meantime, I learned to use wxGlade, which does pretty much the same (except that it doesn't have an editor).

---

### Post by Majorix on 2008-01-05
I have switched from Ubuntu to Xubuntu, however this same problem is still there.

I have done some work to get Boa Constructor to run with python2.4 instead of 2.5 under wxpython2.4 instead of 2.6; yet there is no luck.

If anybody has any fresh ideas, I would be glad to test them out. Thanks.

---

### Post by s57nev on 2008-02-15
Yeah same problem here....don't know how to get around this point in help...I'll just start some other example ??? Maybe ...

---

### Post by Steveway on 2008-02-15
If you use wxglade and code in Python then I would advise you to use the most recent version of SPE.
The new version of Stanis Python Editor includes wxglade to easily make your gui.
Ohh, version 0.8.4c has been released yesterday! [http://pythonide.blogspot.com/](http://pythonide.blogspot.com/)

---

### Post by misanthropist on 2008-12-28
Same problem on Hardy 8.04. Although the three dots don't show if I click on the right hand side of the empty box the collection editor pops up and seems to function correctly.

---

### Post by Electrice on 2009-07-08
I'm currently in the process of using Boa to develop a cross platform app, and ran into the above mentioned issue in both Ubuntu and on the mac, and may have found a odd partial solution. As far as I can tell part of this problem may be either related to the larger font size that the Ubuntu uses, or to a missing ForcedRefresh() in the inspector. The reason I think this is because I've managed to get some of the +++ buttons to show up in Ubuntu by dragging the inspector window out into the editor area a bit.  This dragging causes the inspector to repaint, and so long as I've got the element I want the +++ shown for selected in the inspector, like magic, some times the buttons mysteriously appear.

So another quick step by step to try:


[LIST]
[*] 1. switch to the Dialog Editor.
[/LIST]

[LIST]
[*] 2. select the element you wish to edit the properties of. (I find selecting via the objects list is often the easiest)
[/LIST]

[LIST]
[*] 3. Select the TAB of the inspector with the item type you want the +++ for.
[/LIST]

[LIST]
[*] 4. Select the ITEM in the inspector you want the +++ for.
[/LIST]

[LIST]
[*] 5. Left-Click-Drag the bottom right corner of the inspector, and drag it out into the editor area.
[/LIST]

[LIST]
[*] 6. If this works the same as it has for me, the +++ some times magically appear for the selected item at this point. Basically it's a repaint issue.
[/LIST]

[LIST]
[*] 7. If 6 didn't work, try dragging the inspector a bit wider as the Ubuntu version of boa has larger fonts base fonts than in the other two OS's. Basically a repaint and font size issue.
[/LIST]

[LIST]
[*] 8. If you still don't see the +++, then that element is probably not working, and you have to code it by hand.
[/LIST]

[LIST]
[*] (Ctrl+Space, Ctrl+Shift+Space, Alt+t and F1 will all quickly become you're friends)
[/LIST]
  I Hope this helps.

---

### Post by gdimike on 2009-09-09
I have the same problem in Jaunty amd64.

Has anyone submitted this to the bug tracking system? I can't seem to find this bug listed there.

---

### Post by stefanlsd on 2009-11-04
Same issue for me under Karmic. Also tried Boa from CVS and still the same.  Will open a bug report.

Reported as [https://bugs.edge.launchpad.net/ubuntu/+source/boa-constructor/+bug/473786](https://bugs.edge.launchpad.net/ubuntu/+source/boa-constructor/+bug/473786)

---

### Post by Lordthoron on 2010-12-28
Having same problem, on my main box and on a fresh install of ubuntu 10.10. with only the OS and boa constructor installed, both boxes are amd 64, main is using ati vid card (pcie) and new box is using generic onboard vid. 
Main pc is ubuntu 10.10 32 desktop ed. using sata HD with PCIE ATI RAdion 
second is ubuntu 10.10 64 desktop ed. using ata HD with Generic OB Vid
both use amd 64 ath 2.4 with 2 gigs ram (pny).

I have only tried it on my Gnome desktop so far im about to try on my KDE to see if that works ill edit in the results..

ok same on KDE, but now Simon is working (unrelated but woot)

---

### Post by oxmox on 2011-08-23
Hello,

I had the same error in boa constructor. The detailed error message 
points to line 410 in this file:

/usr/share/boa-constructor/Explorers/FileExplorer.py

Line 410: files.sort()
That's the place, where the error occurs.

You find the reason therefor in the previous lines:
           
            # A hack for locally-encoded filesystems:
            # We need to convert filesystem names
            # from local encoding to unicode
            if type(self.resourcepath) is str:
           if type(self.resourcepath) is str:
                files = os.listdir(self.resourcepath.decode(
                      sys.getfilesystemencoding()))
            else: # unicode or other 
                files = os.listdir(self.resourcepath)
            #---------------------------------------- 
        except Exception, err:
            raise ExplorerNodes.TransportError(err)
        files.sort()

You must remove the hack:

replace:
  files = os.listdir(self.resourcepath.decode(
              sys.getfilesystemencoding()))
with:
  files = os.listdir(self.resourcepath)

(you must edit the file as as root - e.g. 
sudo gvim /usr/share/boa-constructor/Explorers/FileExplorer.py)

But before you begin, check the error message to be sure it is the same error!

---

