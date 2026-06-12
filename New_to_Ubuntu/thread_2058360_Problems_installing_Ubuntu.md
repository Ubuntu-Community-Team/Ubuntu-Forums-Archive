---
title: "Problems installing Ubuntu"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by Mike Myers on 2012-09-15
I used UNIX a lifetime ago, and then tried to get involved in Red Hat Linux.  It's now many years later, and I'm trying to install Ubuntu - on two laptops.  Both are running Windows 8.

I have a problem on the first laptop which I think I figured out - I ran Windows 8, then loaded the ISO file using Daemon Tools - worked fine until the re-boot, and I assume it died because it was looking for the CD, which had been un-mounted during the re-boot.  I'm now downloading the file again, and will burn to CD.

On the other laptop, I tried to install direct from the website, to run it under Windows.  In the mistaken idea that I should have a whole partition for it, I "reduced" the size of a partition, and in the 30 gigs of free disk space I had, I created a new partition specifically for Ubuntu.  I then used the download method, but noticed that at that point I would select the size for Ubuntu - I picked 14 gigs, half of the available space on that newly created partition.

The download goes fine, then I get an error message ending with:

>>stderr=An error has occurred setting the element data.  The request is not supported.

>stdout

I saved it in a file which I can attempt to post here.  I need to upload it first....


My gut feeling is that the partition I created is now suitable for booting, but that's just a wild guess.  If that's not the problem, I have no idea what else it might be.

---

### Post by Mike Myers on 2012-09-15
I gave up on the laptop with the partition problem - for now.


The laptop that seemed to be closest to working was my Compaq Presario C740EM.  I went back to the web, and clicked on the option to install Ubuntu to run under Windows.   

It downloaded the installer program.

I selected a 24gig area on drive D.


I have no idea where it is finding all the installation files, as instead of a 2 hour download, it did "something" in one minute and was ready for the re-boot.

FIRST QUESTION, WHEN I USE CONTROL PANEL TO UNINSTALL UBUNTU, WHY DIDN'T IT GET RID OF WHEREVER THESE FILES ARE NOW COMING FROM??

Knowing it would crash on the re-boot (as it did before) I inserted the CD for Ubuntu I had just created.  Sure enough, the computer did the re-boot, and I'm now at the "Install WELCOME screen.   

The screen reads "Or if you're ready, you can install Ubuntu alongside (or instead of) your current operating system."    

WHERE IS THE WORDING THAT SAYS IT WILL INSTALL TO RUN UNDER WINDOWS, WHICH IS WHAT I WANTED TO DO????

I will try "Install Ubuntu"   ..........hopefully I don't wreck this laptop.




............naw, I clicked QUIT.   There is nothing here that confirms it is doing what I want, 

Bummer - "quit" doesn't do that - I am now at the Ubuntu Desktop.  



Finally found shutdown.  The computer shut down, then told me to remove the CD and close the tray. 

I rebooted and Ubuntu tried to come up, giving the error message because the CD was no longer in place.

I turned the computer off, and it rebooted, giving me the selection boxes for Windows 8 or Ubuntu.   I picked Windows 8.  Went back to control panel and removed Ubuntu again.

Did <restart>.


Laptop now boots back into Windows 8, like it did many hours ago.

------------------------------------------------

I guess my question now is that somewhere, someplace, somehow, there is the Ubuntu installation stuff on this laptop, such that when I download and run "wubi.exe" it finds the existing files, rather than doing the download from the internet like it's supposed to do.

I am completely lost.  I do have the "iso file" on my computer, but it's not open or anything.  




...........and I should add, if the computer is going to download this two-hour long file, why doesn't it give a name to it, and tell me where it is being stored?????

---

### Post by newb85 on 2012-09-15
I don't think you're taking the right installation approach.

There three (that I know) to install Ubuntu:

1.  Boot from a Live CD or USB and run the installer.  This will place Ubuntu on its own partition.  You will have the choice to run either Windows or Ubuntu when you power up your machine, assuming you install alongside Windows.

2.  Run the Wubi installer in Windows.  This will place Ubuntu on the same partition as Windows.  Again, you will have the choice to run either Windows or Ubuntu when you power up your machine.  WARNING: the Wubi installer is NOT recommended.  Its lead developer has stated that it was designed for experimental installs, not long-term installs.

3.  Install on a Virtual Machine (VM) using a client like VirtualBox ([www.virtualbox.org]("www.virtualbox.org")).  A Live CD or USB will work, or you can simply point to the ISO.  It will be installed on a virtual HD within Windows.  You will have to run Windows and your VM client in order to Boot Ubuntu.

It sounds like option 3 is what you're looking for.

---

### Post by critin on 2012-09-15
It looks like you've started and quit installation more than once.  The install may be corrupted.  If you can get into win8 and it still works, leave it alone for awhile and decide exactly what you want to do before proceeding.

Wubi is easy but it may not work on Win8 yet.  Win8 is not officially 'released', so wait on that.

I agree that virtual is the easiest way to go at this point.  You already have the iso, get vmware (my choice) or virtual box and follow its directions.

With virtuals you can have both open at the same time, that's kinda fun.  ;)

Don't worry, you'll get there.

---

### Post by Mike Myers on 2012-09-15
What I would like to do, is option #2 above, installing it under Windows.  This is just an experiment, to see if I like it.


When I run wubi.exe     it is supposed to download all the files and then do the installation.   Downloading takes hours.   On my machine it is finding the files somewhere, so the "downloading" takes less than a minute.

Any idea where these files are coming from?  If I could remove them, the process would probably continue the way it's supposed to run.


I need to get to the installation screen where it says it will install under Windows, and let me select the settings - and then download the appropriate files.

Thanks.....   me confused, but will keep trying.

---

### Post by critin on 2012-09-15
> **Mike Myers said:**
> What I would like to do, is option #2 above, installing it under Windows.  This is just an experiment, to see if I like it.


When I run wubi.exe     it is supposed to download all the files and then do the installation.   Downloading takes hours.   On my machine it is finding the files somewhere, so the "downloading" takes less than a minute.

Any idea where these files are coming from?  If I could remove them, the process would probably continue the way it's supposed to run.


I need to get to the installation screen where it says it will install under Windows, and let me select the settings - and then download the appropriate files.

Thanks.....   me confused, but will keep trying.

I don't know where they are in win8, but where ever the Program files are.  Search for 'Ubuntu' and 'wubi'.  There is a folder named ubuntu

VMware is a virtual machine too, but sets up easier than wubi.  You don't have to dual boot, which is a plus for some.  If you already have the iso and know where it is,  (it may be in the folder, but I don't know),  I strongly suggest going that route..

---

### Post by critin on 2012-09-15
From reading again your first two posts, I suspect the iso was never downloaded.  The first stopped with an error and the second ended way too quickly.

If you find you must download again, just download and save it to downloads so you'll have it safe.
Use a torrent or 'down them all' through firefox.  Depending on your internet speed it could be pretty quick or two hours.

---

### Post by newb85 on 2012-09-15
You specifically said in your second post that you wanted to install it to run under Windows.  The Wubi installer will not get you there.

---

### Post by Mike Myers on 2012-09-16
> **critin said:**
> From reading again your first two posts, I suspect the iso was never downloaded.  The first stopped with an error and the second ended way too quickly.

If you find you must download again, just download and save it to downloads so you'll have it safe.
Use a torrent or 'down them all' through firefox.  Depending on your internet speed it could be pretty quick or two hours.


Critin, I do have the "main??" version downloaded, and have burnt the ISO file to a CD.  (I have now downloaded it five or six times, in trying to get to the Windows installation, but I never get there....


This is what I am trying to do: 
[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

You will read here that downloading the files should take an hour or so - on this laptop it takes less than a minute - so the files MUST be coming from something I have already done on the laptop.  

I will try again.
I have un-installed Ubunto.
There is no CD in the drive.
The ISO file I had stored on the drive has been deleted.
The computer has been re-started....

---

### Post by Mike Myers on 2012-09-16
Very strange - I am doing the same things now as I did yesterday, and this time the (long) download is starting.  In one hour I'll find out if everything will work this time.

I'm also installing on a different partition, with a newly downloaded copy of wubi.exe  .....maybe before it was finding my old ISO file for Ubuntu, even though it was not mounted....   that's the only reason I can think of - there is no other place on my laptop I know of for where it could find the files....

Thanks!!

---

### Post by critin on 2012-09-16
> **Mike Myers said:**
> Very strange - I am doing the same things now as I did yesterday, and this time the (long) download is starting.  In one hour I'll find out if everything will work this time.

I'm also installing on a different partition, with a newly downloaded copy of wubi.exe  .....[COLOR=Blue]**maybe before it was finding my old ISO file for Ubuntu, even though it was not mounted..**[/COLOR]..   that's the only reason I can think of - there is no other place on my laptop I know of for where it could find the files....

Thanks!!

At one time I tried to install wubi and it messed up.  I deleted it from Add/Remove and tried to install it again.  It wouldn't install because it said there was already wubi on the system.  I had to search for everything ubuntu/wubi and delete it before I could do another install.  I finally found the folder and a couple of loose entries to delete.  It had to be absolutely clean.

I still wonder about using it with win8.  Do you know if others have done it?   Perhaps that error you mentioned was a problem with getting permission from win8.
>                                               If a security message like this appears, click **'Continue'** to proceed.
Did you get this message the first time?  Win8 may be more picky about what they allow.

Be sure too that the version numbers match, 12.04 iso to 12.04 wubi.exe.  I've seen a couple of issues where they didn't.  There is 12.04.1, so be aware.

I hope you're successful.  I used wubi for a year before installing into a permanent partition, and I liked it.

---

### Post by Mike Myers on 2012-09-16
Well, I'm closer.

The download finished, the laptop re-booted, and started up Ubuntu.  I am now at the Ubuntu Desktop.


.............from what I saw earlier on YouTube videos, I expected the software to do lots more set-up work, and re-booting.  Nothing is happening, and there is no message as to what I'm supposed to do to complete the process.


I'm logged on, but my user name is the same as my Windows 8 user name, not the one I typed into the setup program.  The password works, so I must be doing some things right....

---

### Post by Mike Myers on 2012-09-16
Newb85, I'm not sure what you mean - I think that's the objective of the  procedure I posted the link for up above....   I hope.  Now that I'm  into Ubuntu, will it give me the choice of which to run.....

Yes!

I shut the system down from Ubuntu, and rebooted.  I got to the new  "Windows" screen from Win 8, and then to the choice of which operating  system I want to use.  So I think I've done that part right.  I'm guessing I'm somewhat done with the installation - need to see if I should download updates, and then I need to start learning what to do.



Critin, I think you described the problem I was having - once I got rid of all the old stuff, things did seem to go as described.

You're asking me about Win-8....    I'm just learning Win-8, so I don't know what to expect.  So far it seems that anything that works under Win-7 will work under Win-8, and the missing features such as the "start" button can be re-created using add-on software.



Regarding your question, I did get the message several times:
  "If a security message like this appears, click **'Continue'** to proceed. 			 		"


I don't think I got it this last time.  Doing things under Windows was effortless, once I got it to work at all.  This is on my Compaq C740EM Presario.   I've got other issues trying to get it to install on my Toshiba Satellite - will put that in a different thread, so as to not confuse things even more than they already seem to be!   :-)

---

### Post by newb85 on 2012-09-16
Mike,

If the Wubi installer got you to what you wanted, then I just plain misunderstood what you wanted.

Congratulations!  You sound like you're well on your way.  Happy Ubuntuing!  ;)

---

### Post by critin on 2012-09-16
I know how developing releases don't always do things the way they will when finally released. and some things are held back  that will be activated on release. (after payment is received)  Win8 is still in dev stage.  It will do everything win7 does eventually, but...right now, you're experimenting.

What you learn here might very well help a user who tries to install wubi into win8 in the next few months.  Take notes.  lol

> and the missing features such as the "start" button can be re-created using add-on software.Bah!  Who needs an old start button anyway?  'buntu'ers don't.    lol   The word START is in big bold text,  and working off the regular desktop is simple with file manager in the task bar. Just like most buntus.    The metro screen?  Delete the icons you don't want, I don't stay on that screen long enough for it to bother me.
Sorry--went off topic.

---

### Post by Mike Myers on 2012-09-17
> **critin said:**
> I know how developing releases don't always do things the way they will when finally released. and some things are held back  that will be activated on release. (after payment is received)  Win8 is still in dev stage.  It will do everything win7 does eventually, but...right now, you're experimenting.

What you learn here might very well help a user who tries to install wubi into win8 in the next few months.  Take notes.  lol

Bah!  Who needs an old start button anyway?  'buntu'ers don't.    lol   The word START is in big bold text,  and working off the regular desktop is simple with file manager in the task bar. Just like most buntus.    The metro screen?  Delete the icons you don't want, I don't stay on that screen long enough for it to bother me.
Sorry--went off topic.

I wish what you said were true about Microsoft - unfortunately, someone in charge of software design has attempted to ban the "start" button - probably because you don't need it with a touch-screen, but for those few people stuck (!!!!!!) with a mouse and keyboard, the "Metro" interface is quite slow and miserable.  Many companies have developed a replacement "start" button, which in my opinion makes the operating system quite useable again - in fact, better in many, many ways than any Windows OS I've yet tried.  (The ones I recommend are "Start8" which works the way Windows did many years ago, and fits me like an old shoe, and "StartMenu7 version 4.5 which has many nice benefits - that's what I'm using on this laptop.  Back to your question, I have also downloaded Windows 8 RTM, an exact copy of what Microsoft will be releasing in October - it's free to download, but the RTM version will expire in 90 days from installation.  So, if anyone wants a "start button", my advice is to download one as soon as you find you're too frustrated with Microsoft's way - unless of course you have a touchscreen, in which case you might actually enjoy Metro....

I did what you did - wholesale deletion of the Metro apps.  And with the new Start buttons, most of metro can be "hidden" away anyway - I never get to see it unless I specifically try to.


For Windows, i need the "start button".  I don't know enough about Ubuntu to know what to expect...     and my experience with UNIX is back when people actually used a "command shell" type of environment.

I'm guessing that since the Ubuntu I have right now is working under Windows, if I were to put all this on a dual-monitor computer, I could be using both simultaneously.  

I will post another thread here about getting Ubuntu to load under Windows on my Toshiba laptop.  That failed last time....    I'll start out by posting the error message I got.

Thanks for your help - all of you.  

Oh yeah - even for people who think Windows 8 is for the birds, more and more people are going to start using it (getting stuck with it?), so I think it's a good idea for the future to help people start out with Ubuntu under the Win8 shell.

---

