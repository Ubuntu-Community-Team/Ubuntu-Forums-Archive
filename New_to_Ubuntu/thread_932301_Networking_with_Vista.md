---
title: "Networking with Vista"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by wabbit46 on 2008-09-28
I am having trouble networking a Vista computer with one running ubuntu 8.04 via a Cat 5 cable. 

Both computers can ping each other but I cannot see either computer (or its shares) in a network search.

---

### Post by northern lights on 2008-09-28
[https://help.ubuntu.com/community/Samba]("https://help.ubuntu.com/community/Samba")

---

### Post by wabbit46 on 2008-09-28
Thanks for your useless information.

---

### Post by HittingSmoke on 2008-09-28
> **wabbit46 said:**
> Thanks for your useless information.
> 
This tutorial will help you setup reliable and secure sharing between Linux and Windows. It covers the steps to take for both operating systems.

Wow, kind of a rude thing to say to someone who just gave you exactly what you needed.

---

### Post by balagosa on 2008-09-28
It is useless to him in the sense that he does not know what to do with it. Maybe if the suggestor posted a little background of what samba can do.

I had this same experience, it took me weeks to setup up my Samba properly even with a guide-at-hand.

---

### Post by wabbit46 on 2008-09-28
Thanks to both "HittingSmoke" and "Balagosa". I have Samba installed but if I cannot detect the target machine it is useless.

---

### Post by northern lights on 2008-09-28
For more in-depth advice or more adequate info, a detailed description on where you're stuck would be helpful.

Pinging is not reliant on samba and should work without it.
File sharing however is.

What does entering```
smb://
```in the nautilus location entry yield?

As an aside, HittingSmoke adequately expressed the sort of motivation your reply  spawns...

---

### Post by wabbit46 on 2008-09-29
Northern Lights,

I sincerely apoligise if my response was offensive. 

I have no idea how to invoke Nautilus hence I am in this forum.

Attempting to invoke smb;// from a terminal results in the message command not found.

---

### Post by northern lights on 2008-09-29
> **wabbit46 said:**
> I have no idea how to invoke Nautilus hence I am in this forum.

Attempting to invoke smb;// from a terminal results in the message command not found.
Nautilus is your filebrowser. It automatically opens when you select any of the entries in the "Places" menu. Alternatively, running```
nautilus
```from either a terminal or the run-dialog (Alt+F2) would open an instance of it. The location bar can be switched between button view or an entry bar via the very left button.

> **wabbit46 said:**
> I sincerely apoligise if my response was offensive.Sorted.

---

### Post by Kellemora on 2008-09-29
I hate to say this, but I have to agree with Wabbit!

The info about Samba is not only useless, it's totally BOGUS!

I've spent the last THREE WEEKS trying to get a Network up and running, that was working fine upon install.

I FINALLY swapped out the hard drives again to the old small hard drive, same computer, and Networking and file sharing works perfectly, no glitches.

Copied EVERY SINGLE FILE associated with Networking and Samba.

Put the new drive back in and compared.
Every single LINE of configuration in any and all files were IDENTICAL.

Yet No Networking!  Put the old drive back in, ALL Networking to ALL computers works perfectly AND in both directions.  Files are viewable on Windows machines just fine, writable, no problems.

OK, check out other files that could possibly be associated.
Copy them. Plop the new drive back in.
Once again, they are IDENTICAL.  
But, No Network........

I finally managed to get the Linux machine to see the Windows machines by completely uninstalling Samba and all it's associated files, rebooting then reloading everything.  At least NOW it can see the other machines, BUT, no Windows machine can see it.

The ONLY difference is the hard drives, everything else is Identical, including all the files that work on one, but not at all on the other.

Apparently, the trick to getting the network to work has NOTHING to do with Samba at all.  At this point, it appears to me, the issue lies with the hard drives the programs are installed on.  Which I know is ridiculous, but that's how it appears.

I even tried MIRRORING the working system to the new hard drive on a different partition.  That caused more problems!  I didn't bother to try to figure out why though, just deleted that partition.

If Samba is set up right and it still don't work.  Look elsewhere or try a fresh install.  Sometimes then everything works right for no logical reason.

TTUL
Gary

---

### Post by northern lights on 2008-09-29
> **Kellemora said:**
> I hate to say this, but I have to agree with Wabbit!

The info about Samba is not only useless, it's totally BOGUS!

I've spent the last THREE WEEKS trying to get a Network up and running, that was working fine upon install.

I FINALLY swapped out the hard drives again to the old small hard drive, same computer, and Networking and file sharing works perfectly, no glitches.

Copied EVERY SINGLE FILE associated with Networking and Samba.

Put the new drive back in and compared.
Every single LINE of configuration in any and all files were IDENTICAL.

Yet No Networking!  Put the old drive back in, ALL Networking to ALL computers works perfectly AND in both directions.  Files are viewable on Windows machines just fine, writable, no problems.

OK, check out other files that could possibly be associated.
Copy them. Plop the new drive back in.
Once again, they are IDENTICAL.  
But, No Network........

I finally managed to get the Linux machine to see the Windows machines by completely uninstalling Samba and all it's associated files, rebooting then reloading everything.  At least NOW it can see the other machines, BUT, no Windows machine can see it.

The ONLY difference is the hard drives, everything else is Identical, including all the files that work on one, but not at all on the other.

Apparently, the trick to getting the network to work has NOTHING to do with Samba at all.  At this point, it appears to me, the issue lies with the hard drives the programs are installed on.  Which I know is ridiculous, but that's how it appears.

I even tried MIRRORING the working system to the new hard drive on a different partition.  That caused more problems!  I didn't bother to try to figure out why though, just deleted that partition.

If Samba is set up right and it still don't work.  Look elsewhere or try a fresh install.  Sometimes then everything works right for no logical reason.

TTUL
Gary
I'm with you on networking being not the easiest to set up and it having the potential to create frustration.

However, bashing the samba project as you did does not only seem unfair, but really hinders progress.

Undoubtedly, now a recent convert has to think of this issue as fatal, when it isn't.

"Everything working right, for no logical reason" never happens. "Everything working right for a reason that is beyond your or my grasp" might just happen once in a while.

All in all your statement is counter-productive and not helpful at all.

Anyhow, should the point of this thread be the quest for a solution, give an in-depth description on the problem, it might be dealt with.
Should the point of this thread turn out to be simple *nix network bashing, goodbye, take care, and enjoy.
My time's too precious for that.

---

### Post by jonandrews on 2008-10-12
Some of the preceding posts do seem to make the cross-platform networking issue feel more complicated than it is, in my experience. I have put a step-by-step guide to networking between Ubuntu & Windows on a website:

[http://www.europe.eclipse.co.uk/Ubuntu](http://www.europe.eclipse.co.uk/Ubuntu)

See if that helps.....

---

### Post by mothraman on 2008-11-18
I have similar problems...as do many others, evidently.

I've responded to so many "solutions" that I'm not sure what used to work any more.

I have a wired Vista machine, a wireless Ubuntu machine, and a wireless XP machine.

Here's where I am now:

I added client ntlmv2 auth = yes to smb.conf.

That got me partly there. Everybody can see and access everything EXCEPT Ubuntu cannot see shares on the Vista machine (although it can see the machine).

This is a problem because the printer is on the Vista machine.

I ran "secpol.msc" on the Vista machine and changed Lan manager settings to negotiate ntlmv2 when necessary--no change in any of the above.

There was a time when ubuntu could see the vista shares but not access them, and could not print even after setting up the printer. Vista would see "remote guest document" in the queue but not print it..which is the same situation I get if I give the workgroup/computer/printer address in printer setup and try to print a test page now, even though I can't see the printer.

I run smbtree and the vista shares are listed.

With so many people having similar problems there must be a known solution--or a known bug.

Can anyone help?

---

### Post by handydan918 on 2008-11-18
SAMBA is an amazing project. 
However.
Based as it is on attempted interoperability with a proprietary (and obscure!) set of protocols, (Windows) it is almost incomprehensibly complex. 

now, before the inevitable "Oh yeah? Well I just plugged it in and it worked!" posts come, yes, sometimes it works. When it does, great. When it doesn't, there should be an alternative. 

Like SSHFS or freenx.

---

### Post by rampageoberon on 2008-11-18
I personally have found Vista a nightmare for networking/file sharing. Ubuntu and XP machines work brilliantly and yes one has to refer to Samba documentation from various sources which touch on several different aspects.

Regarding getting ti to work on Vista could you try disable windows firewall/other firewalls and net defender and then try it. Hopefully it works and then you can turn things on and identify what breaks.

Hope that helps

---

### Post by billgoldberg on 2008-11-18
> **wabbit46 said:**
> I am having trouble networking a Vista computer with one running ubuntu 8.04 via a Cat 5 cable. 

Both computers can ping each other but I cannot see either computer (or its shares) in a network search.

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

The guide I've written, see if it works (it should).

It is extremely easy.

---

### Post by philinux on 2008-11-18
I've just managed to get printing from ubuntu networked machine to the main xp machin. But when you go places network windows network nothing is discovered even though I've shared the printer and a shared folder. It all has to be set up manually. Same with the printer.

---

### Post by mothraman on 2008-11-18
Thanks.  Between my last post and now I figured out that I could mount the vista shares manually.  I won't get inot whether that's a good thing or not, but I'd say it's less than user-friendly.

I can now access files on the vista machine, and I can also see the printer.  However, once I set up the printer and try to print a test page, all I get is the printer making noise for a few seconds but not printing.  The print job is in the queue on Vista, bit I can't delete without unplugging the printer's power cord.

I tried a ppd file from the HP web site--same result.

There's a linux print product on the hp website that has to be downloaded and compiled. It has several dependencies, at least one of which it can't install.

I have found network printing to be a challenge on several linux versions.

Any thoughts?

---

### Post by txwooley on 2008-12-05
I have a slightly different problem, but didn't think it was different enough for a whole new thread.  I am running Hardy on my laptop, Vista on home desktop, and XP on kids desktop.  Neither of the Windows comps could see the Ubuntu laptop, and the laptop couldn't see the Windows comps.  I have Samba, Samba-Common, and SMBClient all installed on said laptop.  By the way, the laptop doesn't show an icon or list in any way my networked (wireless) printer, but it can print on it.  I have been trying for months to get Ubuntu and Windows to make nice with each other, but to no avail.  Then, all of a sudden, for no known reason, yesterday the laptop showed up in the network places on my Vista!  I right-clicked on a video on the laptop, shared it, and watched it on the Vista!  Yay! They get along!  I shut-down the laptop last night before bed, and when I started it this morning, no networking.  The laptop can still print to the network printer, but the "Windows Network" icon in Network Servers is empty (not showing either the Vista or the XP).  Likewise the Ubuntu doesn't show up in Network Places on either PC.  I really wish I knew what I did to make them play nice yesterday, but I have no idea.  I know I didn't do anything other than re-start the laptop to make them enemies again.  Please help!:confused:

---

### Post by Kellemora on 2008-12-05
Hi Gang

Well I don't have and would never allow Vista anything to pass through our doors.

I DO have 8 computers Networked, 6 are Ubuntu, 2 are Doze XP.

Samba and the LAN work just fine, but Ubuntu is where the problems come in.  Most of the time, shares are NOT FOUND under Places/Network as they should be.  This is NOT a Samba issue!

But the documentation for Samba, is as I said in my earlier post, totally BOGUS.

smb.conf is NOT read by Samba without a special boot up procedure.  The files that run upon boot-up are BINARY (meaning not humanly editable) and found in /var/lib/samba. Where technically you can do nothing about them.

If you install smbtree and type smbtree in a terminal (providing you don't have smbfs installed) it WILL show ALL of your shares, Windows and LINUX and all of the machines on the LAN.  Therefore you KNOW the LAN is up and running properly.

You can PING all the machines, no problem.  And you can go to Places/Networking hit the GO/Location and fill it in as smb://IP number and the shared files on that computer will appear just fine.

But if you use Places/Network they SHOULD APPEAR but often don't.
That's a BUG that has been in Ubuntu for MORE THAN 2 years now and is NOT being addressed or resolved!

Making changes in smb.conf is virtually useless, unless you reboot three times in succession so the smb.conf overwrites the /var/lib/samba configuration file.  And even then it won't take all the time.

On some of our 6 Ubuntu machines here, it's not uncommon to have to reboot 10 to 15 times before the shares will appear under Places/Network on their own.

And, every single time and update comes down the pike, even when not related at all to networking, the entire network comes crashing down like a house of cards, requiring ALL the Ubuntu machines to require rebooting to get things up and running again.

I still cannot use command line controls like rsync to see any hard drive or file on any other computer.  And despite dozens of responses and studying every piece of documentation, not a single suggestion or instruction has worked yet.

I converted my entire office over to Ubuntu and the most simplest of things in Windows is a Major headache wrought with frustration in Ubuntu.  Networking works perfectly in CentOS (RedHat) and in other Distro's I've played with.  The only Distro, which happens to be the one I want to use, networking is a total nightmare.  Works fine for 5 to 6 hours then don't work and takes half a day to get it back up again.  Although over the past three months I'm learning some shortcuts to reload all the files and mount them manually much quicker.  It's still something that should NEVER have to be done.

A BARE BONES smb.conf file works just fine on all Distro's, except Ubuntu.  Identical smb.conf files on 6 machines, except for machine specific lines of course, works one day perfectly, the next day it don't work at all, even though absolutely nothing changed.

My GOAL was to eliminate Doze machines entirely!  But many features of Ubuntu REQUIRE a Doze machine to make them work!
Not all the problems are Ubuntu, I realize 3rd party vendors are who make the hardware drivers.
But how logical is this.  I have a GREAT laser printer driver, has some features the OEM driver don't have.  But they left out one major feature.  The ability to change Empty Toner Cartridges!
The only way to change a toner cartridge is to connect the printer from the Ubuntu machine to a WinDOZE machine!  Not Ubuntu's fault of course, but how can something so logical be overlooked.
Also, you cannot program your scroll mouse button!
Isn't the keyboard and mouse the two most widely used interfaces between the computer and a humanoid?  So why are mouse features ignored?????  Shouldn't the human interface have been JOB ONE?

TTUL
Gary

---

