---
title: "[SOLVED] On Windows i could get open office 3 but now i've switched to ubuntu, i can'"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jonobe on 2008-11-02
Even as a Windows user, i had preferred the Open Office to MS.  I switched to Ubuntu about a month ago, and have had to downgrade to version 2.4.
This seems sad to me, especially as Open Office is open source.

Both Applications>Add/Remove    *and *  Synaptic Package Manager 

only offer version 2.4.



So I went to the website to download version 3, and they don't have any installation instructions for Ubuntu.  Great.  Now I'm not techy, so i download it anyway, then Extract it from Archive Manager, read the read me files - it tells me nothing about installing but says i should read my distro instructions (though Ubuntu help instructions have said to look to the package read me files - so both are looking tot he other one to help me, and neither helping) and when i push 'Set up' icon i get an error regarding some Java plugin I didn't know i needed.  So nothing doing.

I have abandoned trying to download 3 now, because I don't have any more time to experiment - i have work deadlines to meet.  I shouldn't even be typing up this.

So while many declare how Ubuntu is so much better than Windows - i'm left thinking, can't there even be clear instructions for some fool like me (who has been to Cambridge Uni) who wants to support Open Source,etc., but is constantly frustrated by simple things not being clear unless you've studied programming for x years?

Anyway, that's enough moaning.  I am a big supporter of the philosophy and I'll stick with Linux, i just get so frustrated when things like not getting OOo 3 is ironically out of my reach now, when it was so easy when I was on Windows (even when 3 was only beta). It just doesn't seem right!  

Back to work on my 2.4 now (sniff sniff) then 
(oh. by the way. it's not working properly as there's no minimize/close option on the spreadsheet - it's fullscreen or nothing.  Never had that prob with windows...)

disillusioned, though not defeated

---

### Post by jmszr on 2008-11-02
jonobe,
         Give this a try: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by Ryadt on 2008-11-02
Go in Administration > Software Sources. Under the 'third party tab' add this ```
[I]deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
Reload and openoffice 3 should appear in update manager.
[/I]

---

### Post by jonobe on 2008-11-02
i tried this - and indeed it showed up in update manager.  Didn't install though, it says

Not all updates can be installed - so i run the option of 'partial upgrade'.

But this doesn't work either, it starts off ok then tells me

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
openoffice.org-common
openoffice.org-filter-mobiledev
openoffice.org-style-human
ttf-opensymbol


anyway, thanks for the help, much appreciated.  these things are so not straightforward, i know that. right, i've finished my cup of tea, back to work.

---

### Post by 73ckn797 on 2008-11-02
Follow this:
I have installed OO 3.0 on my desk and laptops with Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever.

Extracted files using File Roller (default Gnome compression utility) to the created directory. 

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon.

---

### Post by jonobe on 2008-11-02
WEll, I've tried the tips above.

So far, the first attempt didn't work, then the 2nd attempt didn't work, then the 3rd attempt involved me taking out all of 2.4 with synaptics.  I then tried to find the deb package on Open office site, but only could find JRE as a download - and now 2.4 won't reload because it says there is some conflict or other.

Luckily i have saved my work and can transfer it to Windows tomorrow, where i can complete it.

While I support Ubuntu, if it really wants to compete, these issues have to be resolved.  How many different ways are there to do something and for them not to work?
There needs to be a default 'normal' way of downloading stuff that is accessible to idiots like me who really don't have the time to become experts.  
god knows what i'm going to do now.  I'll get through it, probably next weekend when i've got some spare time.  In the meantime i don't have a wordprocessor or spreadsheet.
Sorry guys - thanks for your help - i'll let you know if i solve it.


more disillusioned but not entirely defeated (yet?)

---

### Post by 73ckn797 on 2008-11-02
> **jonobe said:**
> WEll, I've tried the tips above.

So far, the first attempt didn't work, then the 2nd attempt didn't work, then the 3rd attempt involved me taking out all of 2.4 with synaptics.  I then tried to find the deb package on Open office site, but only could find JRE as a download - and now 2.4 won't reload because it says there is some conflict or other.

Luckily i have saved my work and can transfer it to Windows tomorrow, where i can complete it.

While I support Ubuntu, if it really wants to compete, these issues have to be resolved.  How many different ways are there to do something and for them not to work?
There needs to be a default 'normal' way of downloading stuff that is accessible to idiots like me who really don't have the time to become experts.  
god knows what i'm going to do now.  I'll get through it, probably next weekend when i've got some spare time.  In the meantime i don't have a wordprocessor or spreadsheet.
Sorry guys - thanks for your help - i'll let you know if i solve it.


more disillusioned but not entirely defeated (yet?)

The file to download is listed in my tip. The directory names are for help purposes mainly. Checking what actual directories the Oo extracts to must me confirmed prior to performing the terminal operations. I have only been using Ubuntu/Linux since August 2008, so if I can figure it out I am certain that you can.

Hope it all works out.

---

### Post by NewJack on 2008-11-02
> **jmszr said:**
> jonobe,
         Give this a try: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

I was going to recommend the above instructions also.  Went flawless for me on Hardy.

---

### Post by jonobe on 2008-11-02
> **73ckn797 said:**
> The file to download is listed in my tip. The directory names are for help purposes mainly. Checking what actual directories the Oo extracts to must me confirmed prior to performing the terminal operations. I have only been using Ubuntu/Linux since August 2008, so if I can figure it out I am certain that you can.

Hope it all works out.


how do I find the file on the open office website?  I can only find a 'download' option, which starts pretty much automatically as the JRE option, not the deb, which is what you refer to.  I've tried search there and that gives no results

---

### Post by NewJack on 2008-11-02
Go to this link:

[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

Look for your Language, then just past "Release" you will see Windows, Linux RPM then Linux DEB.  The Linux DEB is the one you download.

Good luck!

---

### Post by jonobe on 2008-11-02
WEll, it's getting late now but i couldn't crash out without having to solve this problem.  I went over what everyone said, found out the main probelm was first
to download the DEB not the JRE (silly me)
by finding it in 'other platforms' on the website,
and then not actually type in what Tombutu suggests but use my brain (Which as an idiot i would prefer not to use, thank you)
which said i should type in to the Terminal 
'sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/*.deb'

which didn't work because i had followed instructions to Extract, but my comp had extracted to my home directory.  Are you noobies following?

So i retyped it several times until it all started working.  It started processing loads of stuff and i sat back happy and flipped open a tin of cheap beer, smile upon my face.

When it had finished, i went to Applications.

Nothing officey was there.

I rebooted (old habits from Windows days) to see if that would help.

No.

So you see.  

The problem is I don't usually mind working through things, but today i've a load of other problems, i've got a hell of a week coming up, and the last thing i need is problems with something like a spreadsheet that won't minimize, so i upgrade it, it doesn't work i try a million different things.  So now i haven't got a spreadsheet at all.  And now i realize that i saved my work in open office format so windows can't read it, so i'm stuffed as i can't read it at work tomorrow.  I'll have to tell my peers about my problems and they'll think i' haven't done my work and i'm talking nonsense about OS and what?  

I think i'm going to have to resort to another beer.  Might aswell by hung for mutton as lamb.

---

### Post by 73ckn797 on 2008-11-02
> **NewJack said:**
> Go to this link:

[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

Look for your Language, then just past "Release" you will see Windows, Linux RPM then Linux DEB.  The Linux DEB is the one you download.

Good luck!


Joe has the answer at [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

### Post by SunnyRabbiera on 2008-11-02
Well for me i really wish Open office would not have a million different installer files just to make open office workable.
I mean why couldnt they just merge the core files into one installer and then make the others easier to install.
There will be third party repositories to be sure though

---

### Post by NewJack on 2008-11-02
[LEFT]Did you follow Tom's instructions on how to add the menu entries :

To do this, make sure you are in the right directory, then type the following into a Terminal-  ```
sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/openoffice.org3.0-debian-menus_3.0-9354_all.deb
```Hope that helped you out!
[/LEFT]

---

### Post by brandoncolorado on 2008-11-02
> **jonobe said:**
> WEll, it's getting late now but i couldn't crash out without having to solve this problem.  I went over what everyone said, found out the main probelm was first
to download the DEB not the JRE (silly me)
by finding it in 'other platforms' on the website,
and then not actually type in what Tombutu suggests but use my brain (Which as an idiot i would prefer not to use, thank you)
which said i should type in to the Terminal 
'sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/*.deb'

which didn't work because i had followed instructions to Extract, but my comp had extracted to my home directory.  Are you noobies following?

So i retyped it several times until it all started working.  It started processing loads of stuff and i sat back happy and flipped open a tin of cheap beer, smile upon my face.

When it had finished, i went to Applications.

Nothing officey was there.

I rebooted (old habits from Windows days) to see if that would help.

No.

So you see.  

The problem is I don't usually mind working through things, but today i've a load of other problems, i've got a hell of a week coming up, and the last thing i need is problems with something like a spreadsheet that won't minimize, so i upgrade it, it doesn't work i try a million different things.  So now i haven't got a spreadsheet at all.  And now i realize that i saved my work in open office format so windows can't read it, so i'm stuffed as i can't read it at work tomorrow.  I'll have to tell my peers about my problems and they'll think i' haven't done my work and i'm talking nonsense about OS and what?  

I think i'm going to have to resort to another beer.  Might aswell by hung for mutton as lamb.

Jonobe,

I have a few comments I would like to make.  I understand your frustration.  This should be simple, and I believe in a way, it is.

1)  Version 3.0 is not worth the upgrade/hassle unless you can look through the new features list and find something that is absolutely essential.  For most people, they believe upgrading is necessary because they want to be able to open .docx (Office 2007) files.  However, this has already been enabled in OO 2.4.  The program essentially looks and feels the same.  Just stick with 2.4, and when 3.0 is supported (when bugs are worked out and the next version of Ubuntu is released), your operating system is going to upgrade your software automatically.  How simple is that?  Windows could not do that for you.

2)  The simplest way to upgrade is the one mentioned early.  Only 2 steps, should take 1 minute.  You shouldn't have to uninstall 2.4, because you are actually updating to version 3.0

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

3)  Don't fret, a lot of this stuff that seems complicated at first, is only complicated because you have never done it before.

Best of luck.

---

### Post by brandoncolorado on 2008-11-02
One other note.  For the purposes of installing .deb files:  Just download the file to your computer, double click on it, and there is an install file.  However, for the purposes of upgrading to OO 3.0, the .deb download is unnecessary because of the instructions I posted in the last post.

---

### Post by ad_267 on 2008-11-02
I think we should get something straight here. Sorry if you've already mentioned this but I've had a read and couldn't find it.

What version of Ubuntu are you using? It is a lot simpler if you're using 8.10. You can just add some software sources under System - Administration - Software Sources.

---

### Post by jonobe on 2008-11-02
if only it was so simple

Hardy 8.04

---

### Post by brandoncolorado on 2008-11-02
> **jonobe said:**
> if only it was so simple

Hardy 8.04

It is.  (see above post)

---

### Post by darolu on 2008-11-02
Take a look at this:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by ad_267 on 2008-11-02
Ok well from your post above you said you installed from the packages but there wasn't anything in the menu. OpenOffice 3.0 should be installed, the problem is that 2.4 is still installed and 3.0 has been installed in the /opt directory. This means you have to make your own launcher in the menu.

Right click on the menu and select "Edit menus". Go to Applications - Office and select New Item. Then for the item command you need to enter "opt/openoffice.org3/program/soffice"

This seems to be a better guide if it's still not working: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by thomas228 on 2008-11-02
> **jonobe said:**
> WEll, it's getting late now but i couldn't crash out without having to solve this problem.  I went over what everyone said, found out the main probelm was first
to download the DEB not the JRE (silly me)
by finding it in 'other platforms' on the website,
and then not actually type in what Tombutu suggests but use my brain (Which as an idiot i would prefer not to use, thank you)
which said i should type in to the Terminal 
'sudo dpkg -i ~/Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/*.deb'

which didn't work because i had followed instructions to Extract, but my comp had extracted to my home directory.  Are you noobies following?

So i retyped it several times until it all started working.  It started processing loads of stuff and i sat back happy and flipped open a tin of cheap beer, smile upon my face.

When it had finished, i went to Applications.

Nothing officey was there.

I rebooted (old habits from Windows days) to see if that would help.

No.

So you see.  

The problem is I don't usually mind working through things, but today i've a load of other problems, i've got a hell of a week coming up, and the last thing i need is problems with something like a spreadsheet that won't minimize, so i upgrade it, it doesn't work i try a million different things.  So now i haven't got a spreadsheet at all.  And now i realize that i saved my work in open office format so windows can't read it, so i'm stuffed as i can't read it at work tomorrow.  I'll have to tell my peers about my problems and they'll think i' haven't done my work and i'm talking nonsense about OS and what?  

I think i'm going to have to resort to another beer.  Might aswell by hung for mutton as lamb.

Try [http://ubuntuforums.org/showthread.php?t=953487](http://ubuntuforums.org/showthread.php?t=953487) (post #3)

You may have to clean out 00o3 if your still having problems. If so See [http://ubuntuforums.org/showthread.php?p=5977796#post5977796](http://ubuntuforums.org/showthread.php?p=5977796#post5977796)  (post #2)

Keep a stiff upper lip as you almost had it except for from the directory DEBS do

cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

That step gives you your application>office menu

By the way 00o3 Windows version can read/write 00o3 files as well as the ubuntu version.

I hope this does not muddy up the water for you and 
Good Luck

Tom

---

### Post by NewJack on 2008-11-02
Like I posted before, if you follow the Tombuntu instructions as laid out by Tom it works flawlessly.  It seems as though the OP forgot to add the menus.  Using Tom's method, I was up and running in about 10 minutes.  OpenOffice 2.4 was gone, 3.0 was installed and every program ran fine and finally all of my menu options were there.

Good luck!

---

### Post by jonobe on 2008-11-04
OK

 
So I thein tried the 

openoffice.org3.0-debian-menus_3.0-9354_all.deb

in Desktop Integration folder






[edit:  i have noticed this is what Thomas228 suggested - thanks!]

 now everything works perfectly.

I'm happy now 


I think what i'll take from this is not to try to do anything drastic if I'm in the middle of important work.  Linux has a steep learning curve at the beginning.  It's not so user-friendly all the time, but in many ways it is more so - adding applications through the menu is usually very simple. Now i've got it all working like a dream, and a Windows user, seeing me working with Ooo3 went ' what?  that's fast?  what speed is your computer?'  It transpired his (Windows) computer has 50% more RAM and GHz, yet my Linux (Dell 6400) leaves it standing.

Of course.

Climbing mountains is hard work but it feels great at the top (-:

---

### Post by BLTicklemonster on 2009-02-03
> **73ckn797 said:**
> Follow this:
I have installed OO 3.0 on my desk and laptops with Intrepid. Everything was effortless and is running great.

~

Thank you, that worked for me. I was lost without my spreadsheet!

---

