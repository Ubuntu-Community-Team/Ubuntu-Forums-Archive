---
title: "Can't get Chrome installed"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by 8H3LnBH on 2014-09-30
I am about to go crazy trying to do something that is so simple on Windows...install Chrome.  I am running 14.04 and have read several threads here about performing different steps but in the end...I don't think it is installed.  I have run apt-get update and apt-get upgrade.  I opened a browser (Firefox) and went to the download for Chrome.  I downloaded Chrome, right-clicked on it and selected "Open with Software Center".  When the Software Center opens, I click on Install and then the next thing that comes up is a window that says "To install Chrome, these apps need to be removed: Application Indicators, Panel indicator applet - shared library".  If I then click on "Install anyway" it looks like it is installing but it eventually just comes back to the initial Install screen and does not appear to install.

I am really excited about learning Linux but this task that seems like it should be a simple one is proving to not be so simple for me.

---

### Post by Bucky Ball on 2014-09-30
Not quite the same, but have you given Chromium Browser a shot? Is in the repos and should install easily. Pepperflash-installer will allow you to install the version of flash used in Chrome. 

Just a thought. Any how, have a look [HERE]("http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/") and down the page to the headng, 'To add PPA in Ubuntu 14.04 / 13.10 / 13.04 / 12.10 / 12.04'. The PPA will keep Chrome up-to-date. Good luck. ;)

---

### Post by QIII on 2014-09-30
Something to bear in mind is that many things are "easy in Windows" because developers make them that way.  Google makes it easy to install Chrome in Windows (not Microsoft).  If they didn't they'd not get their product used.

Linux?  Meh.  <2% of the computer market.  How much effort do you think they are going to make to make it easy?

(Ironically, Google issues many of its standard workstations to its employees with, of all things, Ubuntu)

---

### Post by craig10x on 2014-09-30
Seems strange that you would have a problem with installing chrome when you right click and open it in ubuntu software center...I've NEVER had a problem with it myself....
You could try this...go to ubuntu software center and install gdebi   Once installed, right click the Chrome deb file and hit where it says "install with gdebi" and use that tool instead...
gdebi is a VERY RELIABLE tool so if that doesn't work, then there must be something else on your system that is causing the problem...

---

### Post by Bucky Ball on 2014-09-30
> **craig10x said:**
> 
You could try this...go to ubuntu software center and install gdebi   Once installed, right click the Chrome deb file and hit where it says "install with gdebi" and use that tool instead...
gdebi is a VERY RELIABLE tool so if that doesn't work, then there must be something else on your system that is causing the problem...

Good idea which might just work. Odd that Gdebi might not be installed with a regular 14.04 install though. :-k Curious.

---

### Post by deadflowr on 2014-09-30
> **Bucky Ball said:**
> Good idea which might just work. Odd that Gdebi might not be installed with a regular 14.04 install though. :-k Curious.

gdebi hasn't been installed by default since 10 or 11(pick a month).

That said it is odd it would want to remove anything.
It would be of most help for the actual and exact package names that were named as being the problem.
I would also run the software updater for a full update, instead apt-get upgrade, which can hold packages back.
Chrome, which I am using now and have for quite sometime, has never asked to remove anything( in Ubuntu)but has needed me to update or install other packages.

---

### Post by Bucky Ball on 2014-10-01
Thanks dflower. Learn something everyday. I only run mini.iso s with xfce4 so what would I know ... ;)

---

### Post by 23senick on 2014-10-01
Don't think anyone's mentioned the easy answer.  Surely the point is that you don't generaly install things in the same way in Ubuntu as you do in windows.  Ubuntu generally installs from a PPA, Chrome isn't in the ubuntu ppa so you need to add the chrome PPA.  You could search this forum for "add chrome ppa" or try the link I found

[http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/) 

Hope it works!

---

### Post by QIII on 2014-10-01
Or just install it from google.com with the click of a button...

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

---

### Post by deadflowr on 2014-10-01
> **23senick said:**
> Don't think anyone's mentioned the easy answer.  Surely the point is that you don't generaly install things in the same way in Ubuntu as you do in windows.  Ubuntu generally installs from a PPA, Chrome isn't in the ubuntu ppa so you need to add the chrome PPA.  You could search this forum for "add chrome ppa" or try the link I found

[http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/) 

Hope it works!

I think you mean the repositories.
Ubuntu generally installs packages from the repositories.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Ubuntu can install packages specifically from ppa's.
But you add those, much like you would for chrome.
[http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)
fwiw

---

### Post by QIII on 2014-10-01
The installer from google.com takes care of adding the ppa (Google's ppa), which means Chrome stays updated as Google updates it.

---

### Post by bhaskar4 on 2014-10-01
Use Chromium instead as it is the Linux alternative of Chrome. :P

---

### Post by Bucky Ball on 2014-10-01
Didn't I mention the Chrome PPA [in post #2?]("http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/") Anyway, good luck with it. ;)

---

### Post by craig10x on 2014-10-01
@Bucky Ball: yeah, gdebi use to be installed by default but they probably stopped doing that because they felt that the ubuntu software center was reliable enough to do the same function...I would say it is, most of the time, but occasionally  some run into snags with it like the op here has...

---

### Post by Bucky Ball on 2014-10-01
> **craig10x said:**
> @Bucky Ball: yeah, gdebi used to be installed by default but they probably stopped doing that because they felt that the ubuntu software center was reliable enough to do the same function...I would say it is, most of the time, but occasionally  some run into snags with it like the op here has...

Cheers. I should run a straight Ubuntu install one of these days so I can keep up with the shifting sands and am qualified to comment on these things! I continue to learn in this wonderful virtual environment. :-k ;)

I've been running minimal installs and manually installing gdebi and synaptics for what seems like years now.

---

### Post by 8H3LnBH on 2014-10-01
> **23senick said:**
> Don't think anyone's mentioned the easy answer.  Surely the point is that you don't generaly install things in the same way in Ubuntu as you do in windows.  Ubuntu generally installs from a PPA, Chrome isn't in the ubuntu ppa so you need to add the chrome PPA.  You could search this forum for "add chrome ppa" or try the link I found

[http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/) 

Hope it works!

Tried this BEFORE posting to the forum.  I try hard to not duplicate posts and there is a lot of info out there on this topic but so far none of it has worked for me.

When I run the first command on the linked web page to get the signing key, I get an error that says:

 "gpg: no valid OpenPGP data found"

---

### Post by 8H3LnBH on 2014-10-01
> **QIII said:**
> Or just install it from google.com with the click of a button...

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

I also tried this BEFORE posting because being a Windows guy, that was the logical thing for me to try :).  The outcome of trying this is what I put in the original post.

---

### Post by deadflowr on 2014-10-01
So something else to try is a total cli way.
I assume the deb is in the Downloads folder so from a terminal run these
```
cd Downloads
```
(Please note the capital D)
this will move you into the downloads folder, which make it quicker to run the next command
```
sudo dpkg -i google-chrome-stable-version.deb
```
Quick Tip: when entering the name, if you press the tab button, probably after hitting the first g, the rest will autofill.(Tab completion, ftw)
Please copy the output and paste it.
It should tell us exactly what went wrong, and why.

---

### Post by 8H3LnBH on 2014-10-01
I went back to [http://www.howopensource.com/2011/10...4-10-10-10-04/]("http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/")[COLOR=#000000]* *[/COLOR] to try it again and it appears I was entering a lower case "o" when I should have been entering an upper case "O".  It looks like it should have worked but I can't figure out how to actually start the Chrome browser now.  I don't see an icon for it like there is for Firefox.

---

### Post by deadflowr on 2014-10-01
No icon in the dash?(the menu, not the launcher; you can access the dash by pressing the windows-looking button on the keyboard, ftr)
Try running
```
google-chrome
```
from a terminal.
Does it launch chrome or output something like no such thing?

If it does launch chrome then an icon should appear in the launcher bar, you can add it by right clicking on it and selecting lock to launcher.

---

### Post by 8H3LnBH on 2014-10-01
> **deadflowr said:**
> No icon in the dash?(the menu, not the launcher; you can access the dash by pressing the windows-looking button on the keyboard, ftr)
Try running
```
google-chrome
```
from a terminal.
Does it launch chrome or output something like no such thing?

If it does launch chrome then an icon should appear in the launcher bar, you can add it by right clicking on it and selecting lock to launcher.

Thanks for the tip on the dash...did not know that.  Nothing listed under applications.  When I run it from a terminal window...it does open Chrome and locking it seemed to work.  Weird...Linux will take some getting used to.  Been spoiled by Windows I guess.  Thanks for your help.

---

### Post by craig10x on 2014-10-01
I was just going to mention that too....when apps are installed directly from the ubuntu software center from something actually in the center, it automatically adds it to the unity dock...but when you install deb files from other websites (like Chrome for example) it doesn't...so you just enter the name in dash search and click it, it opens and appears on the dock and then you lock it in yourself...

Things are different here then windows...but you will quickly get use to it ;)

---

### Post by snowmobiler on 2014-10-01
I found its very easy to click the Unity (?) button on the dash (the top icon) and then click on applications. Then you can drag and drop icons to the side dash, I think right clicking didn't work for me.

---

