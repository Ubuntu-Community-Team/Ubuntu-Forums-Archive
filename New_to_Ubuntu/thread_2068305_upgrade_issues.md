---
title: "upgrade issues"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by jcka005 on 2012-10-08
the problem i posted last friday is this-- upgrading 11.04 to 11.10 but i shut down the computer because it was taking so much time...the pc won't boot a day after i did that..now yesterday, the pc suddenly boot and the features were changed..it transform to 11.10..

my question which really bothers me is this---can i upgrade it to 12.04 LTS even though i made mistake of shutting it down while on the process of upgrading last week???

and this-- how come the pc turned to 11.10 if i interrupted the upgrading process??

**PLEASE HELP ME!!!!!*** THANK YOU VERY MUCH ...

---

### Post by HunterDX77M on 2012-10-08
A nearly identical thing happened to me when I was upgrading from Oneiric to Precise. From what it looked like, the installation locked up and I had no choice but to do a hard shutdown. When I turned it back on, some things were really weird and messed up (like the resolution, the mouse, etc.), but the version was 12.04. 

After my initial panic attack, I sat down at another computer and began Google'ing stuff about botched upgrades/installations and I remember I found 1 site that helped out a lot (I had to do something from the boot menu, but I don't remember what right now). The point is, it seems like the installation began with the critical core components of the version I was upgrading to and then went on to less important things (like settings on applications). So, like me, you probably turned it off after the critical components of the version you were upgrading to were already installed, which is why it seems to work right now. 

My advice would be to stick to 11.10 for a couple of days, run an update to update your software and then go for an upgrade to 12.04. Before you do anything like that, make sure to back up any important files/data you might have. When this happened to me, I learned two lessons the hard way. (1) Never touch any thing or start any other program while in the middle of a version upgrade and (2) stick with the LTS, because upgrades are serious sources of anxiety and stress. I hope this helps you a little and that you eventually find your way safely to 12.04. Peace and have a nice day.

---

### Post by jcka005 on 2012-10-08
wow.thank you very much sir..
i looked for updates and i found none..

---

### Post by daslinkard on 2012-10-08
> **jcka005 said:**
> the problem i posted last friday is this-- upgrading 11.04 to 11.10 but i shut down the computer because it was taking so much time...the pc won't boot a day after i did that..now yesterday, the pc suddenly boot and the features were changed..it transform to 11.10..

my question which really bothers me is this---can i upgrade it to 12.04 LTS even though i made mistake of shutting it down while on the process of upgrading last week???

and this-- how come the pc turned to 11.10 if i interrupted the upgrading process??

**PLEASE HELP ME!!!!!*** THANK YOU VERY MUCH ...
My question for you would be whether or not it is feasible for you to run a Live CD of 12.04 to put on your PC as opposed to trying to go through the upgrade?  Once you have successfully burned the image to disc, and boot off the Live CD you should be able to wipe any other OS off the machine and solely load 12.04.

Clean installs tend to be the way to go so there is no issues that get lost in transition from upgrading from one version to the next.  My vote is for the clean install and I believe it will fix your issues.

---

### Post by jcka005 on 2012-10-08
somebody already told me to burn an iso of 12.04 LTS but i was not able to do it..i was kind of scared, i don't know..

but thanks anyway for the suggestions..Godbless..thankyou very much.

---

### Post by daslinkard on 2012-10-08
> **jcka005 said:**
> somebody already told me to burn an iso of 12.04 LTS but i was not able to do it..i was kind of scared, i don't know..

but thanks anyway for the suggestions..Godbless..thankyou very much.
First off, when you say you were not able to because you were scared, do you mind elaborating on what scares you?  I know it can seem like a daunting task when you start with Linux but just know you have a great cast of supporters here in the forum.

What can we do to help you get 12.04 on your system?

---

### Post by bra|10n on 2012-10-08
> **jcka005 said:**
> wow.thank you very much sir..
i looked for updates and i found none..

You might also elaborate on how exactly you checked for updates.

---

### Post by DuckHook on 2012-10-09
I vote with *daslinkard* on this one. I have upgraded a number of Linux systems. Some have gone well, others very badly. Over the years, I have come to the conclusion that chances for a successful upgrade increase with:

1. Pristine prior OS. If the system you are upgrading is basically unchanged from the default install, then the chance of a successful upgrade is greatly increased.
2. Generic drivers. I have had either newly installed systems or the upgrade process itself hang because of corrupt or misbehaving video drivers. Sometimes, a proprietary driver will work with OS version X, but not with version X+1.
3. Little to no customization. I've been tripped up by a highly customized xorg.conf and host.conf.

Upshot is: upgrade success is highly dependent on starting out with a well-behaved system. Since yours is already in a questionable state, it would be inviting trouble to upgrade it. A clean install will not inherit anything from the previous version and will be free of any files or configurations that may have been corrupted by a dirty shutdown.

1. Since 11.10 seems to work, I suggest the following: back up all of your important data. For those new to Linux who cannot differentiate what is important from what is not, this means your entire /home directory. If you have the space (say, a big external drive) back up everything from / (i.e. root) on down.
2. Install 12.04 with the option of deleting and replacing any previous version.
3. Reinstall newest versions of all programs you want.
4. Copy your important data from your backup back to your new install.

You should now be good to go.

PS: do not start either an upgrade process or a fresh install unless you have lots of time to let the process complete. With the installation of any OS, you cannot turn the machine off in the middle of the install process. Leave it on all night if necessary.

PPS: sometimes, the install process gets bogged down at the update stage. This may have been why you were forced to abort the process. If you have a slow internet connection, make sure that you answer "no" at the point where you are asked if you want to make updating a part of the installation. This way, only the CD contents will be installed, and you can update later when you have more time or a faster or more reliable connection.

---

### Post by audiomick on 2012-10-09
Lots of good advice in DuckHook's post. That is pretty much exactly what I would do.

I would like to add the following:

Firstly, to reiterate what has already been said, I would not advise trying to simply upgrade from a suspect system. If there really are issues in there, the chances are that they will by carried over to the newer version. A fresh install will give you a solid basis to go on with.

If you don't already have an external drive or something along those lines, think seriously about getting one. Backups are important, and should be on a medium external to the computer that is being backed up.

When you do your fresh install, think about putting the /home folder on a separate partition. You need to go into the "something else" option of the installer when it gets to the point where you can choose between "install beside" and "use the whole drive". This is not absolutely necessary, but gives you the option of retaining an existing /home folder in a new install.

If you, as DuckHook suggested and backup the entire file system or even just the whole /home folder, you should just copy back the files you want, not the whole thing. The reason for this is that your configuration files are in the /home/user folder as hidden files. You can see them by activating the "view hidden files" option in the view menu of the file manager. If any of them are corrupted, simply copying them back will bring the corruption across.

If you have backed up the whole thing, and want to revive a configuration from the old install, you can. Locate the config file for the program in question in the fresh install and make a copy of it under a different name. Copy across the old file from your backup, making sure that it gets saved in the /home/user folder with exactly the right name, and then check to make sure it is all working properly. If anything has gone wrong, you can put back the copy of the fresh file that you made.

---

### Post by jcka005 on 2012-10-10
> **daslinkard said:**
> First off, when you say you were not able to because you were scared, do you mind elaborating on what scares you?  I know it can seem like a daunting task when you start with Linux but just know you have a great cast of supporters here in the forum.

What can we do to help you get 12.04 on your system?
uuhhmmm..i've never tried burning a cd..whew..i'm sorry..

---

### Post by jcka005 on 2012-10-10
> **bra|10n said:**
> You might also elaborate on how exactly you checked for updates.
oh i'm sorry i forgot where i saw that one..i'll check it out later, the pc is in use right now..

---

### Post by jcka005 on 2012-10-10
> **jcka005 said:**
> oh i'm sorry i forgot where i saw that one..i'll check it out later, the pc is in use right now..
okay,system info under system settings.

---

### Post by daslinkard on 2012-10-10
> **jcka005 said:**
> uuhhmmm..i've never tried burning a cd..whew..i'm sorry..
There is no reason to be sorry....I have personally never went sky diving but it's no reason to apologize.  If there is anything that we can do to help you when you get stuck just let us know.  That's what we're here for!

Here is a [link]("https://help.ubuntu.com/community/BurningIsoHowto") that might shed a little light on burning the Live CD.

---

### Post by jcka005 on 2012-10-10
> **daslinkard said:**
> There is no reason to be sorry....I have personally never went sky diving but it's no reason to apologize.  If there is anything that we can do to help you when you get stuck just let us know.  That's what we're here for!

Here is a [link]("https://help.ubuntu.com/community/BurningIsoHowto") that might shed a little light on burning the Live CD.
thanks very much..can i replace the cd by using a flashdrive?? if yes, what size do i need?

---

### Post by Wim Sturkenboom on 2012-10-10
Yes, you can use a flash drive. See [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu) (using your existing Ubuntu install) or [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) (using a Windows PC).

---

### Post by jcka005 on 2012-10-10
> **audiomick said:**
> Lots of good advice in DuckHook's post. That is pretty much exactly what I would do.

I would like to add the following:

Firstly, to reiterate what has already been said, I would not advise trying to simply upgrade from a suspect system. If there really are issues in there, the chances are that they will by carried over to the newer version. A fresh install will give you a solid basis to go on with.

If you don't already have an external drive or something along those lines, think seriously about getting one. Backups are important, and should be on a medium external to the computer that is being backed up.

When you do your fresh install, think about putting the /home folder on a separate partition. You need to go into the "something else" option of the installer when it gets to the point where you can choose between "install beside" and "use the whole drive". This is not absolutely necessary, but gives you the option of retaining an existing /home folder in a new install.

If you, as DuckHook suggested and backup the entire file system or even just the whole /home folder, you should just copy back the files you want, not the whole thing. The reason for this is that your configuration files are in the /home/user folder as hidden files. You can see them by activating the "view hidden files" option in the view menu of the file manager. If any of them are corrupted, simply copying them back will bring the corruption across.

If you have backed up the whole thing, and want to revive a configuration from the old install, you can. Locate the config file for the program in question in the fresh install and make a copy of it under a different name. Copy across the old file from your backup, making sure that it gets saved in the /home/user folder with exactly the right name, and then check to make sure it is all working properly. If anything has gone wrong, you can put back the copy of the fresh file that you made.
thanks for the info sir..

---

### Post by jcka005 on 2012-10-10
> **Wim Sturkenboom said:**
> Yes, you can use a flash drive. See [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu) (using your existing Ubuntu install) or [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) (using a Windows PC).
thankyou very much..i have seen the link..very helpful for me..

---

### Post by bart.a on 2012-10-10
**Sorry.. missed the second page completely.. my bad..**

download the ubuntu 12.04 iso file from the ubuntu website.
Find the download on your disk (Downloads directory).
Pop in an empty CD in your drive.
Right click on the file.
Select write to disc from the menu.
The image burner pops up.
Left click Burn.

For installation:
Leave the disc in the drive.
Reboot.

Make sure that the BIOS settings for boot order starts the CD-drive first.
Install Ubuntu..

Have fun with your system again..

---

### Post by jcka005 on 2012-10-10
> **bart.a said:**
> **Sorry.. missed the second page completely.. my bad..**

download the ubuntu 12.04 iso file from the ubuntu website.
Find the download on your disk (Downloads directory).
Pop in an empty CD in your drive.
Right click on the file.
Select write to disc from the menu.
The image burner pops up.
Left click Burn.

For installation:
Leave the disc in the drive.
Reboot.

Make sure that the BIOS settings for boot order starts the CD-drive first.
Install Ubuntu..

Have fun with your system again..
thanks for the reply.

---

### Post by jcka005 on 2012-10-10
> **bart.a said:**
> **Sorry.. missed the second page completely.. my bad..**

download the ubuntu 12.04 iso file from the ubuntu website.
Find the download on your disk (Downloads directory).
Pop in an empty CD in your drive.
Right click on the file.
Select write to disc from the menu.
The image burner pops up.
Left click Burn.

For installation:
Leave the disc in the drive.
Reboot.

Make sure that the BIOS settings for boot order starts the CD-drive first.
Install Ubuntu..

Have fun with your system again..
thanks for the reply.

---

### Post by daslinkard on 2012-10-10
I wanted to follow up with you to see how the USB installer is working for you?  Do you have any questions that we might be able to clear up for you?

---

### Post by jcka005 on 2012-10-11
> **daslinkard said:**
> I wanted to follow up with you to see how the USB installer is working for you?  Do you have any questions that we might be able to clear up for you?
i haven't tried installing with flash drive..i'm sorry i have no time to do it since i was very busy finishing my accomplishment report..i am an OJT student here..tomorrow's our last day..so i might not be able to visit this forum everyday..but if i have the chance to install ubuntu12.04 in the pc here, i will let you know..i will let you know if it works..thankyou very much for your time and Godbless you all..

-jessica C:

---

### Post by daslinkard on 2012-10-11
> **jcka005 said:**
> i haven't tried installing with flash drive..i'm sorry i have no time to do it since i was very busy finishing my accomplishment report..i am an OJT student here..tomorrow's our last day..so i might not be able to visit this forum everyday..but if i have the chance to install ubuntu12.04 in the pc here, i will let you know..i will let you know if it works..thankyou very much for your time and Godbless you all..

-jessica C:
No worries at all but I think you should visit the forums everyday!! ;)

---

### Post by jcka005 on 2012-10-11
> **daslinkard said:**
> No worries at all but I think you should visit the forums everyday!! ;)
i will find time sir C: thankyou

---

