---
title: "HowTo install KDE 3 into Intrepid (repost)"
date: 2008-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2008-10-30
**5-12-2008**
**Very imortant!**
Thanks (again) to **Madscientist159** the "official" and compatible KDE3 repository is online and ready.
Here the steps to install KDE3 into Intrepid.

[B](A) If you never installed KDE3 into Intrepid
[/B]
Open your apt sources.list
```
kdesu kate /etc/apt/sources.list
```
And add the following lines at the end of the file:
```
#KDE3 Intrepid PPA
deb http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main

```
Save and exit the file. Then do:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop-kde3
```
You'll get a bunch of packages to install, choose y (there is not verification on PPA repositories). When the installation finish, reboot your machine, at the kdm logon choose KDE3 as session.
Done!

**(B) If you had installed KDE3 previously following the guide below, do this**
Copy your configs:
```
sudo cp -R ~/.kde ~/.kde3
```
Reboot your machine and login into Gnome
Open your apt sources.list 
```
gksudo gedit /etc/apt/sources.list
```
Remove (if exists) these lines:
```
deb http://apt.pearsoncomputing.net/ intrepid main
deb-src http://apt.pearsoncomputing.net/ intrepid main

```
and add these lines at the end of the file:
```
#KDE3 Intrepid PPA
deb http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main

```
Save and exit the file. Then do:
```
sudo apt-get update
sudo apt-get remove kdelibs4c2a gdebi gdebi-core kdebase-data
sudo apt-get install kubuntu-desktop-kde3
```
You'll get a bunch of packages to remove/install, choose y (there is not verification on PPA repositories). When the installation finish, reboot your machine, at the kdm logon choose KDE3 as session.
Done!


**19-11-2008**
**Important!**
The [COLOR="Red"]KDE3 repositories are offline[/COLOR] now.
Madscientist159 and Kubuntu Team are working to provide official KDE3 packages/repo for Kubuntu Intrepid.
Please be patient.
Thanks to everyone.
[http://ubuntuforums.org/showpost.php?p=6210362&postcount=107](http://ubuntuforums.org/showpost.php?p=6210362&postcount=107)
[COLOR="Red"]**[http://ubuntuforums.org/showpost.php?p=6211540&postcount=111](http://ubuntuforums.org/showpost.php?p=6211540&postcount=111)**[/COLOR]
[COLOR="Red"]**[http://ubuntuforums.org/showpost.php?p=6213079&postcount=114](http://ubuntuforums.org/showpost.php?p=6213079&postcount=114)**[/COLOR]


**Prologue**
I switched to Kubuntu Intrepid from Hardy and I kept KDE 3 because, in my opinion, KDE 4 is not ready to day-by-day pc operations.

This is not a post against KDE 4, so please do not start flame war about KDE.

I understand at large the reasons why Kubuntu team make the decision to switch the WM into KDE 4 and to do not include KDE 3 anymore; in my view this is a simply wrong decision, but it's ok.
Anyway, because I like very much *ubuntu philosophy and KDE, I found a way to continue to use my distribution at the ultimate release (Intrepid) with my favorite (at the moment) WM, KDE 3.

First of all I must say a big thanks to **Madscientist159 ** that, without his precious works, the solution to use KDE 3 into Intrepid was not possible. Again, Madscientis159, in the full sense of *ubuntu community, invest his time and knowledge into this possibility.

I did the following steps personally, but I do not guarantee that this will work for you, but if I can I'll try to help you.
Please follow the steps indicated if you are a quite experienced user of the system.

**The upgrade from Hardy to Intrepid**
When you are still in Hardy install Gnome environment
```
sudo aptitude install ubuntu-desktop

```
Reboot your machine and log into Gnome
Open a terminal window and do:
```
sudo apt-get update
sudo apt-get dist upgrade

```
Accept the updates if any.
Download on your desktop my source list file sources.txt (available at the end of the post); the repositories in the sources.txt are the official one from Ubuntu; then do:
```
sudo cp ~/Desktop/sources.txt /etc/apt/sources.list

```

> Then upgrade the system from Hardy to Intrepid:
To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions.
(I did not make the command above to upgrade, but I used apt-get, the comand above is the official one anyway)

At the end of installation reboot your machine and log into Gnome. Now you are in Intrepid

**Install KDE 3 into Intrepid**
Attention! Install KDE 3 will REMOVE official Kubuntu KDE 4
Open the sources.list file

```
gksudo gedit /etc/apt/sources.list

```
And add the following lines (the Madscientist159 repository) at the end and save/close the file:
```
###KDE3 on Intrepid
deb [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/) intrepid main
deb-src [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/) intrepid main

```
Add GPG to the repository:
```
wget [http://apt.pearsoncomputing.net/public.gpg](http://apt.pearsoncomputing.net/public.gpg)
sudo apt-key add public.gpg

```
Then do:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kde3


```
Reboot your machine and log into KDE; now you are in KDE 3 in Intrepid

**Annoyances**
Fix KDM login window
```

sudo ln -s /usr/share/apps/kdm/themes/Krystal/ /usr/share/apps/kdm/themes/kubuntu

```
Remove kde applet for network-manager (is not working)
```
sudo apt-get remove knetworkmanager network-manager-kde

```
Add nm-applet of Gnome into KDE
```
sudo ln -s /usr/bin/nm-applet ~/.kde/Autostart/nm-applet

```
Probably you must reconfigure kicker (KDE app bar and some stuff in kcontrol like fonts and style), if you had previously (in Hardy) installed compiz+emerald the configuration will be kept intact.

Reboot to get your networking works under KDE
Basically now you have finished, just add Medibutu repositories
```
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get dist-upgrade

```
Accept the updates if any.

**Do you still want KDE 4?**
You can use the Nightly Neon ppa repositories (no GPG for authenticated packages)
Open sources.list
```
kdesu kate /etc/apt/sources.list

```
And add the following lines at the end of the file, then save/close the file:
```

###Amarok2 & KDE4 Nightly Neon!!
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main

```
Then do:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kde-nightly


```Reboot the machine. Now you can choose 3 WM at the login window:

    * KDE 3
    * KDE 4 (Nightly)
    * Gnome


That's it. Good luck!

---

### Post by madscientist159 on 2008-10-30
As the originator of the KDE3.5 repository, I'd like to say thank you to Dentaku for posting an excellent howto! :popcorn:

Also, if you find any bugs (broken packages, packages that won't upgrade, KDE3.5 programs that are broken or don't work), please report them to my bugtracker at [http://bugs.pearsoncomputing.net/](http://bugs.pearsoncomputing.net/)

Thanks! :)

Tim

---

### Post by madscientist159 on 2008-10-30
To the poster who wanted to know how to "downgrade" back to KDE4:
You will need to run this command before attempting to install the KDE4 master meta-package (kubuntu-desktop, IIRC):
sudo apt-get remove '.*kde.*'
Basically, because KDE3 is treated as an upgrade to KDE4, you need to completely remove it, meaning **all** of its packages, before you can install KDE4.

NOTE: I have not tried this as I am away from my main test machine.  If there is an error, post it here and I'll try to assist.

---

### Post by blackbelt_jones on 2008-10-31
Oh God how could they?

---

### Post by madscientist159 on 2008-10-31
> **blackbelt_jones said:**
> Oh God how could they?

Looks like a lot of people still wanted KDE3...in two days, my repository has transferred 12Gb of data to 200+ unique addresses and still climbing! :)

Have you tried KDE3 under Intrepid yet?  It is even faster in some respects than it was under Hardy, mainly due to the Xorg update I think.

---

### Post by curuxz on 2008-11-01
not that I wish to make this thread into a flame, but I am so $%^&ed off with the Kubuntu team right now its unbelievable. 

What were they thinking retiring KDE 3.5 without asking anyone?!?!? Better still what the hell were they thinking when they decided that KDE 4 was ready?! 90% of the functionality of kde 3.5 is missing and almost 100% of the stability.

As a user of linux for 10 years this has to be the worst move by ANY dev team I have ever seen and now I have to waste my valuable time re-installing because valiant as your post is it simply leaves half my system broken.

---

### Post by madscientist159 on 2008-11-01
Before you re-install, can you please post the error output of whatever upgrade command you were using?  Otherwise I have no chance to fix whatever went wrong.  Also, a reinstall may not be necessary at all...there are ways to force the packaging system back into a working state.

Thanks!

---

### Post by Paul S on 2008-11-01
Yes, there is a need / desire / wish for a stable kde on intrepid, and for some, it's not met by kde 4.  But, I think kubuntu dev's made it clear that they can't do both.

Would madscientist159 consider joining kubuntu team and posting them on kubuntu ppa, like some the original 3.5.10 were done for hardy?  Then he could get free bandwidth too!

regards,

---

### Post by curuxz on 2008-11-02
OK here are my main list of faults with your KDE 3.5 for 8.10 fix :)

- The taskbar and panel over lap in corners (i have one down the right side and one along the bottom, VERY annoying)

- Like the taskbars, desktop icons refuse to see the panel too so they go under it, again annoying.

- Networking is FUBAR, i had to manually override the config even with your suggestion above.

- sound is DEAD :(

- WiFi is DEAD :( :( :(

- System performance is now very very low, even after I disabled all fancy effects mem usage for Xorg is just under 1 gig!!!!! This may just be the new version but stupid memory requirements seem very very vista'ish

Sorry no specific errors since they all just 'dont work' and as much as I would like to route around and fix them I have a major web site launch this weekend and really did not need this mamoth waste of time.

KDE & Kubuntu devs have really sold out the hard working power user with this update. I am really sad.

---

### Post by madscientist159 on 2008-11-02
> **curuxz said:**
> OK here are my main list of faults with your KDE 3.5 for 8.10 fix :)

- The taskbar and panel over lap in corners (i have one down the right side and one along the bottom, VERY annoying)

- Like the taskbars, desktop icons refuse to see the panel too so they go under it, again annoying.

- Networking is FUBAR, i had to manually override the config even with your suggestion above.

- sound is DEAD :(

- WiFi is DEAD :( :( :(

- System performance is now very very low, even after I disabled all fancy effects mem usage for Xorg is just under 1 gig!!!!! This may just be the new version but stupid memory requirements seem very very vista'ish

Sorry no specific errors since they all just 'dont work' and as much as I would like to route around and fix them I have a major web site launch this weekend and really did not need this mamoth waste of time.

KDE & Kubuntu devs have really sold out the hard working power user with this update. I am really sad.

OK, can you try something for me?  Go to your home directory from the command line (do not have KDE active at this point--just switch to a virtual terminal and log in).  Execute ```
mv .kde .kde-old
``` and switch back to KDM or GDM and try to log in again.  KDE4 will really crud up the .kde settings folder causing all kinds of weird issues like the ones you describe.

WiFi and networking in general are known problems, and the fault does not lie with me.  Try complaining to the KNetworkManager people who broke WiFi support in Intrepid (technically, KNetworkManager was not properly updated to handle the new 0.7 networkmanager backend, so nm-applet is the only networkmanager frontend that will work).

Regarding memory usage, did you have Firefox open at the time (or at all since you started the computer)?  There was a bug with Firefox, Flash and the new Xorg that sounds similar to your description--not sure if it is fixed now or not.

Hope this helps,

Tim

---

### Post by red_team316 on 2008-11-02
Why must one install GNOME? I don't want GNOME and am considering trying something similar to the how-to states but with reconstructor.


Couldn't I just:
* replace the sources list in a Kubuntu Hardy 8.04.1 Disc/ISO with the one provided above.
* add the KDE3 repo to the sources list
* add the GPG key
* apt-get update from the chroot environment
* apt-get upgrade or dist-upgrade

...Leaving me with a GNOME free KDE3 Intrepid?

---

### Post by red_team316 on 2008-11-02
Why must one install GNOME? I don't want GNOME and am considering trying something similar to the how-to states but with reconstructor.


Couldn't I just:
* replace the sources list in a Kubuntu Hardy 8.04.1 Disc/ISO with the one provided above.
* add the KDE3 repo to the sources list
* add the GPG key
* apt-get update from the chroot environment
* apt-get upgrade or dist-upgrade

...Leaving me with a GNOME free KDE3 Intrepid?

---

### Post by madscientist159 on 2008-11-02
> **red_team316 said:**
> Why must one install GNOME? I don't want GNOME and am considering trying something similar to the how-to states but with reconstructor.


Couldn't I just:
* replace the sources list in a Kubuntu Hardy 8.04.1 Disc/ISO with the one provided above.
* add the KDE3 repo to the sources list
* add the GPG key
* apt-get update from the chroot environment
* apt-get upgrade or dist-upgrade

...Leaving me with a GNOME free KDE3 Intrepid?

Yes.  You don't even need to log out of KDE when you perform the upgrade.

---

### Post by madscientist159 on 2008-11-02
> **madscientist159 said:**
> OK, can you try something for me?  Go to your home directory from the command line (do not have KDE active at this point--just switch to a virtual terminal and log in).  Execute ```
mv .kde .kde-old
``` and switch back to KDM or GDM and try to log in again.  KDE4 will really crud up the .kde settings folder causing all kinds of weird issues like the ones you describe.

WiFi and networking in general are known problems, and the fault does not lie with me.  Try complaining to the KNetworkManager people who broke WiFi support in Intrepid (technically, KNetworkManager was not properly updated to handle the new 0.7 networkmanager backend, so nm-applet is the only networkmanager frontend that will work).

Regarding memory usage, did you have Firefox open at the time (or at all since you started the computer)?  There was a bug with Firefox, Flash and the new Xorg that sounds similar to your description--not sure if it is fixed now or not.

Hope this helps,

Tim

Just realized I forgot to address the sound issue.  This is a rather well-known problem with the extremely buggy ARTS sound system.  What I always do, and what those who are going to keep KDE3.5 should do, is to bypass ARTS.  To do this, disable the sound system in Kcontrol-->Sound System and uncheck "Enable sound system", then click Apply.  Then go to Kcontrol-->System Notifications and click "Player Settings" and select "Use an external player".  In the "Player" textbox type mplayer

If you don't already have mplayer installed, be sure to install it.  Sound should then work, and you will find it to be far more stable and less of a pain overall than the old ARTS system.

---

### Post by dentaku65 on 2008-11-02
> **curuxz said:**
> OK here are my main list of faults with your KDE 3.5 for 8.10 fix :)

- The taskbar and panel over lap in corners (i have one down the right side and one along the bottom, VERY annoying)

- Like the taskbars, desktop icons refuse to see the panel too so they go under it, again annoying.

- Networking is FUBAR, i had to manually override the config even with your suggestion above.

- sound is DEAD :(

- WiFi is DEAD :( :( :(

- System performance is now very very low, even after I disabled all fancy effects mem usage for Xorg is just under 1 gig!!!!! This may just be the new version but stupid memory requirements seem very very vista'ish

Sorry no specific errors since they all just 'dont work' and as much as I would like to route around and fix them I have a major web site launch this weekend and really did not need this mamoth waste of time.

KDE & Kubuntu devs have really sold out the hard working power user with this update. I am really sad.

For the taskbar you must recreate or at least in my case I did in this way.

For the sound and wifi does not depend by the kde 3 but is general problem, try to install:
```
sudo apt-get install linux-firmware
```
ah, pls for networking in kde you must nm-applet of gnome as indicated on post 1

---

### Post by curuxz on 2008-11-02
This weekend this shoddy upgrade has cost me over 10 working hours, backing up and reinstalling. 

I am sorry I am no longer in 8.10 and I wont be going back any time soon. Much as I would love to route around fixing things there is no real benefit at all to me!

It is broken all over the place, why they chose to ruin kubuntu I simply do not know.

I am grateful for what you are trying to do but I simply do not have time to clean up after the mess of the kubuntu devs, I need my machine to work. I spend a lot of time being active for the open source community and I preach stability to non-linux users every day. If just one of the many many people I have gotten to switch to linux uses this upgrade I will be made to look stupid.

The kubuntu devs have done us a GREAT dis-service.

---

### Post by red_team316 on 2008-11-02
I know it sucks curuxz, I will definitely keeping Hardy as my main OS. 

I am however trying this and will post a separate tutorial on how to do it with reconstructor if I am successful.


BTW, how will this affect installing other programs. I know krusader isn't complete yet for KDE4 but I want it installed also. How do I know that if I install another program it is going to be the KDE3 version and not KDE4?

---

### Post by madscientist159 on 2008-11-02
> **red_team316 said:**
> I know it sucks curuxz, I will definitely keeping Hardy as my main OS. 

I am however trying this and will post a separate tutorial on how to do it with reconstructor if I am successful.


BTW, how will this affect installing other programs. I know krusader isn't complete yet for KDE4 but I want it installed also. How do I know that if I install another program it is going to be the KDE3 version and not KDE4?

The KDE3 versions all have a 7 in front of their version number.  If you go into Synaptic and search for krusader you will probably see two packages--simply select the version you would like and deselect the one you don't.

---

### Post by red_team316 on 2008-11-02
Okay, I made an ISO with reconstructor. After doing a bazillion apt-get updates upgrades dist-upgrades dpkg --configure -a apt-get -f installs, I finally got it to say that everything is up to date(other than dolphin and kde-powermanager which I don't care about)



I fired up my ISO with kvm/qemu and everything seems to go fine until it logs in. I have no mouse/keyboard. Same problem I'd had with starting a chrooted X in intrepid(both vanilla ubuntu and kubuntu).

Any ideas whats wrong? If I can't get it working in kvm, I'm not going to burn a disc.

---

### Post by madscientist159 on 2008-11-02
> **red_team316 said:**
> Okay, I made an ISO with reconstructor. After doing a bazillion apt-get updates upgrades dist-upgrades dpkg --configure -a apt-get -f installs, I finally got it to say that everything is up to date(other than dolphin and kde-powermanager which I don't care about)



I fired up my ISO with kvm/qemu and everything seems to go fine until it logs in. I have no mouse/keyboard. Same problem I'd had with starting a chrooted X in intrepid(both vanilla ubuntu and kubuntu).

Any ideas whats wrong? If I can't get it working in kvm, I'm not going to burn a disc.

I have a fuzzy idea...blackbelt_jones found the same problem with his install.  I have yet to run across it myself, so I can't fix it at this point. :(

From what he has told me, KDM is the only problem.  I am wondering if it has anything to do with the new Xorg and/or possibly a missing extension in the new Intrepid system.  What I would suggest is to use GDM for  now--it works perfectly with KDE and, honestly, it looks a lot nicer when themed properly.

Let me know if this works or not.

Can you install Intrepid with KDE3.5 from your new LiveCD?  If so, that is excellent work!  I would be willing to host it if you don't have the bandwidth to do so...

Tim

EDIT: Oh wait, I missed where you said it was not restricted to KDE3.5  It's *way* too late to be posting I guess!

Try it in VirtualBox (my favorite) or VMWare.  Intrepid's kernel may have problems with anything else.

---

### Post by red_team316 on 2008-11-02
You truely are a mad scientist! I popped back into the chroot, apt-get install gdm, remade the iso and now it works! Thats insane, how could kdm possibly have something to do with it?

I'll need to do some other tweaking to it as the login splash is the generic one.
Also, I'll install it on one of my separate partitions just to make sure it's working properly.

EDIT: Do you know of any kubuntu themed GDM themes?
EDIT2: Can't find any on gnome-look.org...maybe someone could make one while I pound out any other issues with it.

---

### Post by madscientist159 on 2008-11-02
> **red_team316 said:**
> You truely are a mad scientist! I popped back into the chroot, apt-get install gdm, remade the iso and now it works! Thats insane, how could kdm possibly have something to do with it?
 Thanks!:)  
I don't know why or how KDM is broken this point--why don't you file a bug report on it so that everyone affected can add information.  Eventually there should be enough info to actually solve the bug...

> **red_team316 said:**
> 
I'll need to do some other tweaking to it as the login splash is the generic one.
Also, I'll install it on one of my separate partitions just to make sure it's working properly.

EDIT: Do you know of any kubuntu themed GDM themes?

No, and I don't think there are any in existence, but here's a GDM theme I like.  Nice and clean:
[http://www.gnome-look.org/content/show.php/Crisp+Clear+Morning?content=48994](http://www.gnome-look.org/content/show.php/Crisp+Clear+Morning?content=48994)

Just a thought.:)

---

### Post by red_team316 on 2008-11-02
lol no. It's gotta be a kubuntu one. After all this work, it's gotta look professional, not like some hacked up remaster(I give enough support over at the reconstructor forums) :P We might be KDE3 heroes if we can pull this off. Someone step up to the plate, I could do it but it will just lengthen the time it takes to make since I've got to test other stuff.

64-bit version will be next after 32-bit is completed. 

Sure you can host it, but I'll also try to see if I can upload it here too: [http://www.filehosting.org/](http://www.filehosting.org/) supposedly no upload limit. I don't have a website of my own :P I'm a free floater. Hopefully, if enough people get it, someone can start a torrent.


Where do I file it, on launchpad?


EDIT:
Sound also doesn't appear to be working for some reason in kvm. Wait a minute, I just tested standard hardy.sio and sound doesn't work there either.
Other than that, almost every kde3 package is installed, games and a ton of extra stuff. Should I remove some of it? The ISO is 988MB. Kubuntu doesn't typically ship with all of it. I'm just wondering what your thoughts on this are.

EDIT2: There are a bazillion KDE tweaks that need to be done since they are defaulting to KDE standard settings. Luckily I can grab hardy's kubuntu-default-settings and that should clear it up.

---

### Post by madscientist159 on 2008-11-02
> **red_team316 said:**
> lol no. It's gotta be a kubuntu one. After all this work, it's gotta look professional, not like some hacked up remaster(I give enough support over at the reconstructor forums) :P We might be KDE3 heroes if we can pull this off. Someone step up to the plate, I could do it but it will just lengthen the time it takes to make since I've got to test other stuff.

64-bit version will be next after 32-bit is completed. 

Sure you can host it, but I'll also try to see if I can upload it here too: [http://www.filehosting.org/](http://www.filehosting.org/) supposedly no upload limit. I don't have a website of my own :P I'm a free floater. Hopefully, if enough people get it, someone can start a torrent.


Where do I file it, on launchpad?


EDIT:
Sound also doesn't appear to be working for some reason in kvm. Wait a minute, I just tested standard hardy.sio and sound doesn't work there either.
Other than that, almost every kde3 package is installed, games and a ton of extra stuff. Should I remove some of it? The ISO is 988MB. Kubuntu doesn't typically ship with all of it. I'm just wondering what your thoughts on this are.

EDIT2: There are a bazillion KDE tweaks that need to be done since they are defaulting to KDE standard settings. Luckily I can grab hardy's kubuntu-default-settings and that should clear it up.

I understand--why don't you just use the default Ubuntu Human theme for now?  My expertise is not in graphical design or theming so I have no clue where to start on making a Kubuntu version...

I have a bugtracker here: [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net)  I think the Kubuntu devs would hate having it filed on Launchpad, seeing as they have no control over my repository.:)

My thoughts would be to make a DVD version with everything, and then strip out some to make a CD version, sort of like what Ubuntu does.

I'll throw kubuntu-default-settings up on my repository; apparently I missed it.

---

### Post by red_team316 on 2008-11-02
You know, I understand your reasoning on why not to post it on launchpad, but I did experience the same problem in a chrooted X on Intrepid. The odd thing is that the vanilla ubuntu intrepid iso HAS gdm. The problem may be related but I think it may be deeper than just kdm or gdm alone.


You are apparently missing the package that contains kubuntu-wallpaper too(if there is a package, that may be something they just customize before finalizing a new release)
EDIT: yep, the wallpaper is in kubuntu default-settings.

Okay, how do I strip ~300MB without removing OpenOffice lol. I've seen many people ask that one :P

---

### Post by red_team316 on 2008-11-03
Let me know when you've added it to your repo.

There is something odd going on. adept_manager wont fire up from the menu but it will under the terminal. Give me a list of all the packages in your repo. There is a ton of KDE4 crap cluttering up all the directories. If I can do an apt-get remove/purge on all the packages and then reinstall them, hopefully it will remove a ton of the KDE4 stuff. If not, I'll have to go back and rebuild the original ISO(like the original tutorial said), remove those packages, add your repo, and then reinstall them.

EDIT:
in fact, I think your repo needs more work. 

kdelibs5
kdelibs5-data

are KDE4 packages. I'm sure there are more, but thats what I've noticed left floating around so far.

---

### Post by madscientist159 on 2008-11-03
> **red_team316 said:**
> Let me know when you've added it to your repo.

There is something odd going on. adept_manager wont fire up from the menu but it will under the terminal. Give me a list of all the packages in your repo. There is a ton of KDE4 crap cluttering up all the directories. If I can do an apt-get remove/purge on all the packages and then reinstall them, hopefully it will remove a ton of the KDE4 stuff. If not, I'll have to go back and rebuild the original ISO(like the original tutorial said), remove those packages, add your repo, and then reinstall them.

EDIT:
in fact, I think your repo needs more work. 

kdelibs5
kdelibs5-data

are KDE4 packages. I'm sure there are more, but thats what I've noticed left floating around so far.

I kept those around for KDE4 application compatibility--they don't harm KDE3.5 in any way.

The list of packages is here:
[http://apt.pearsoncomputing.net/dists/intrepid/main/binary-i386/Packages](http://apt.pearsoncomputing.net/dists/intrepid/main/binary-i386/Packages)

kubuntu-default-settings is now available in the repository.

If a bug is reproducible in the stock KDE4 or Gnome environments, then by all means file it on Launchpad, as it will need to be fixed by the Ubuntu developers.

I wonder if you can start with the Hardy ISO and upgrade it to Intrepid with my repository added before the upgrade process.  That way, KDE4 will never touch the system...

One other item: see if kdesu exists anywhere on your system.  I have run across a system where the kdesu binary was not installed/installable for some reason, and I had to manually move kdesu.dist to kdesu  That might be why the shortcut for Aptitude was not working.

KDE3.5 is amazingly complex, and it is very possible that my repository needs more work; that's why I'm on this forum! :)

---

### Post by red_team316 on 2008-11-03
Thanks for the list.

BTW, I noticed alot of the package maintainer lines had not been changed. Is there a specific reason you did this? It doesn't make sense that you have packages with the 7 on them that say they are maintained by others. It's easy to spot out what packages are coming from your repo that have your name on them. Are you going to update them? I think you should that way it is obvious where it came from.


Okay, I'll take your word for it that kdelibs5 packages dont conflict. It just seems kind of leery leaving them in there considering it's possible they might point to .kde


GNOME itself is a bug lol. I suppose I can file a bug under chroot for intrepid as filing something against kdm might not be a good idea considering it was their intention for intrepid to be KDE4 only. There may be a package that you need to add to your repo to get kdm/mouse/keyboard working...
 

where do I find the kdesu file(s) and where does the file(s) need to go? I'd rather not go on a wild goose chase :P 
Here is the actual output from the terminal when testing in kvm/qemu:
```

kubuntu@ubuntu:~$ sudo adept_manager
kapture::PkgSystem::PkgSystem()
Error: "/var/tmp/kdecache-kubuntu" is owned by uid 999 instead of uid 0.
debconf
adduser
sysklogd
snort-mysql
oinkmaster
debconf
adduser
sysklogd
snort-mysql
oinkmaster
kdecore (KProcess): WARNING: _attachPty() 43

```
It kind of looks like I need to chown them but the only package I can find in your list you posted is debconf...
hmm..it's adding packages to the terminal output as I look through adept. oinkmaster isn't installed, neither is snort-mysql, etc...
Is this normal behavior?
EDIT: nvm, I fired up adept_manager on my Hardy box and get similar output. I'm not worried about it now.

Installed kubuntu-default-settings. Looks like you added kubuntu-artwork-usplash also(makes me happy:D)

---

### Post by slakkie on 2008-11-03
Some errors during the installation of the kde3 package:

[http://pb.opperschaap.net/3](http://pb.opperschaap.net/3)

And it is not possible to create shortcuts for applications listed in KMenu, I'm unable to bind ksnapshot to print screen and other shortcuts I use (FF, Terminal). See screenshot: [http://www.euronet.nl/users/wesleys/no-shortcut-menu.png](http://www.euronet.nl/users/wesleys/no-shortcut-menu.png)

---

### Post by madscientist159 on 2008-11-03
> **slakkie said:**
> Some errors during the installation of the kde3 package:

[http://pb.opperschaap.net/3](http://pb.opperschaap.net/3)

And it is not possible to create shortcuts for applications listed in KMenu, I'm unable to bind ksnapshot to print screen and other shortcuts I use (FF, Terminal). See screenshot: [http://www.euronet.nl/users/wesleys/no-shortcut-menu.png](http://www.euronet.nl/users/wesleys/no-shortcut-menu.png)

Those are harmless--just ignore them.  Basically they cropped up because I had to manually edit one or two of the packages in order to fix critical bugs fast enough; they will disappear once I recompile those packages.

I will look into the keybinding issue.  Can you delete your /home/<username>/.kde directory (or back it up somewhere and then delete it) and see if that fixes the problem?  This will clear your KDE settings entirely, but most of the time it will also clear up odd issues like that one.

---

### Post by madscientist159 on 2008-11-03
> **red_team316 said:**
> Thanks for the list.

BTW, I noticed alot of the package maintainer lines had not been changed. Is there a specific reason you did this? It doesn't make sense that you have packages with the 7 on them that say they are maintained by others. It's easy to spot out what packages are coming from your repo that have your name on them. Are you going to update them? I think you should that way it is obvious where it came from.
Yes, it's on my to-do list.  When I first started this project I was a complete newbie to the packaging system and didn't even know about the Maintainer line until I had compiled all of the i386 packages.  If you go to the amd64 packages you will see that this bug was fixed there, but I've been waiting on the rest of the i386 packages to see if any more serious bugs will crop up first.

> **red_team316 said:**
> Okay, I'll take your word for it that kdelibs5 packages dont conflict. It just seems kind of leery leaving them in there considering it's possible they might point to .kde


GNOME itself is a bug lol. I suppose I can file a bug under chroot for intrepid as filing something against kdm might not be a good idea considering it was their intention for intrepid to be KDE4 only. There may be a package that you need to add to your repo to get kdm/mouse/keyboard working...
 

where do I find the kdesu file(s) and where does the file(s) need to go? I'd rather not go on a wild goose chase :P 
Here is the actual output from the terminal when testing in kvm/qemu:
```

kubuntu@ubuntu:~$ sudo adept_manager
kapture::PkgSystem::PkgSystem()
Error: "/var/tmp/kdecache-kubuntu" is owned by uid 999 instead of uid 0.
debconf
adduser
sysklogd
snort-mysql
oinkmaster
debconf
adduser
sysklogd
snort-mysql
oinkmaster
kdecore (KProcess): WARNING: _attachPty() 43

```
It kind of looks like I need to chown them but the only package I can find in your list you posted is debconf...
hmm..it's adding packages to the terminal output as I look through adept. oinkmaster isn't installed, neither is snort-mysql, etc...
Is this normal behavior?
EDIT: nvm, I fired up adept_manager on my Hardy box and get similar output. I'm not worried about it now.

Installed kubuntu-default-settings. Looks like you added kubuntu-artwork-usplash also(makes me happy:D)

Let's see if kdesu is actually the problem.  From within a KDE session, go to Konsole and type ```
kdesu adept_manager
```
If that works, then you're OK.  If not, I'll post further instructions.

---

### Post by hans.voss on 2008-11-03
> **dentaku65 said:**
> 
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kde3 jockey-kde


```

I had trouble performing the upgrade. (It bummed out at the dist-upgrade with trying to removing some file (flag.png of all things) that was also available in another package.

Eventually requiring me to select all KDE* packages in Synaptic for Complete removal in order to get the package dead-lock solved

---

### Post by slakkie on 2008-11-03
> **madscientist159 said:**
> Those are harmless--just ignore them.  Basically they cropped up because I had to manually edit one or two of the packages in order to fix critical bugs fast enough; they will disappear once I recompile those packages.


I ignored them, just saying :)


> 
I will look into the keybinding issue.  Can you delete your /home/<username>/.kde directory (or back it up somewhere and then delete it) and see if that fixes the problem?  This will clear your KDE settings entirely, but most of the time it will also clear up odd issues like that one.

I did, no improvement, see [http://www.euronet.nl/users/wesleys/no-shortcut-menu_default.png](http://www.euronet.nl/users/wesleys/no-shortcut-menu_default.png)

I reported the bug on your bugzilla btw (guess you saw that already).

Nah, puzzled, now I can add shortcuts (I have my old .kde dir). Applied some updates from your repo, maybe that fixed it.... weird.

---

### Post by red_team316 on 2008-11-03
kdesu is not installed in the ISO I built. It must not be in your repos... I tried firing it up with kdesudo and that worked but I still get the output. I'm not really worried about the output, I'm considering it normal as I saw the same thing happening on my hardy box when I tested last night.

Even on my hardy box, in the kmenu, the command adept manager does not use kdesu
```

Name: Adept Manager
Description: Manage Packages
Comment: Manage installed and available software
Command: adept_manager
checked: Enable launch feedback
checked: Run as a different user
Username: (It is left blank)

```
This is exactly the same when I test the ISO in kvm/qemu but the menu launcher doesn't work...

---

### Post by madscientist159 on 2008-11-03
> **red_team316 said:**
> kdesu is not installed in the ISO I built. It must not be in your repos... I tried firing it up with kdesudo and that worked but I still get the output. I'm not really worried about the output, I'm considering it normal as I saw the same thing happening on my hardy box when I tested last night.

Even on my hardy box, in the kmenu, the command adept manager does not use kdesu
```

Name: Adept Manager
Description: Manage Packages
Comment: Manage installed and available software
Command: adept_manager
checked: Enable launch feedback
checked: Run as a different user
Username: (It is left blank)

```
This is exactly the same when I test the ISO in kvm/qemu but the menu launcher doesn't work...

OK...I would hazard a guess that the problem is in the .kde settings directory then.  Normally I'd delete it and let KDE recreate the correct settings, but that won't work on an ISO obviously.  I'll have to think about that one...;)

---

### Post by Futurian on 2008-11-03
Thank you for posting these directions.

I got as far as

sudo apt-get dist-upgrade

but while this is running, the terminal is taken over by a screen that tries to get me to select mailserver options. That would be fine, but that screen won't take any input from me; the process hangs there.

To hedge my bets, I'm backing up my home directory preparatory to writing Hardy Heron over my Ibex installation.  I would like to stay with the newer distro, but I really want KDE 3. I tried KDE 4 for several hours, and experienced too many anomalies. Maybe I don't know what I'm doing with 4, but I can't spend more time on it now.

Thanks!

---

### Post by red_team316 on 2008-11-03
> **madscientist159 said:**
> OK...I would hazard a guess that the problem is in the .kde settings directory then.  Normally I'd delete it and let KDE recreate the correct settings, but that won't work on an ISO obviously.  I'll have to think about that one...;)

How about adding kdesudo to your repo. I find it odd that the kdesudo that is present on my ISO is for KDE4 but it's not in your repo list :P I bet that will clear it up.
Let me know when you've added it.

---

### Post by dentaku65 on 2008-11-03
> **Futurian said:**
> Thank you for posting these directions.

I got as far as

sudo apt-get dist-upgrade

but while this is running, the terminal is taken over by a screen that tries to get me to select mailserver options. That would be fine, but that screen won't take any input from me; the process hangs there.

To hedge my bets, I'm backing up my home directory preparatory to writing Hardy Heron over my Ibex installation.  I would like to stay with the newer distro, but I really want KDE 3. I tried KDE 4 for several hours, and experienced too many anomalies. Maybe I don't know what I'm doing with 4, but I can't spend more time on it now.

Thanks!

Try to load the dist-upgrade command in pure console; do CTRL-ALT-F1 and log to the console, then do the dist-upgrade you described above.

---

### Post by red_team316 on 2008-11-03
Here is a list of packages I found that are still needing to be added for the KDE3 versions to the repo or other packages that need removed from IntrepidKDE3. Why you are keeping some KDE4 stuff for compatibility still eludes me, supposedly you can add the nightly neon repo for KDE4, I would think those packages are there. My Installed Hardy works fine and I have no KDE4 packages, even kdelibs5 :/ Keeping KDE4 stuff for compatibility doesn't make sense to me, as if someone really wants KDE4, then they can use the standard Intrepid ISO(or nightly neon) 
```

ktorrent
ksystemlog
khelpcenter4 (still exists on ISO)
kdelibs5
kdelibs5-data
kdelibs-bin
libkdecorations4
libkwineffects1
python-kde4
gwenview

```

Someone please comment on this(dentaku65, you made the tut. Does nightly neon satisfy the urge for KDE4) Not to mention, there are KDE4 apps in the KDE3 repo, then if an update comes along, you wont get it as KDE3 is like an upgrade.


Also, I'm pretty sure without removing all the KDE4 packages, it is unlikely anyone will be able to strip enough without removing oOo from it to get it under 700MB.

---

### Post by slakkie on 2008-11-04
> **madscientist159 said:**
> To the poster who wanted to know how to "downgrade" back to KDE4:
You will need to run this command before attempting to install the KDE4 master meta-package (kubuntu-desktop, IIRC):
sudo apt-get remove '.*kde.*'


This is the correct line, either use remove or purge, the -s is to simulate, so you can see what it will do, remove it if you are happy about the actions it will take to actually perform the removal.

aptitude -s <purge|remove> "~n kde"

---

### Post by dzsabor on 2008-11-04
First of all thank you for this repository, you saved my life :)

Is there a way to include KDE3 version of krusader and gwenview?
These two were installed from intrepid together with some KDE4 libs and I have some problems with them.

---

### Post by dentaku65 on 2008-11-04
> **red_team316 said:**
> Here is a list of packages I found that are still needing to be added for the KDE3 versions to the repo or other packages that need removed from IntrepidKDE3. Why you are keeping some KDE4 stuff for compatibility still eludes me, supposedly you can add the nightly neon repo for KDE4, I would think those packages are there. My Installed Hardy works fine and I have no KDE4 packages, even kdelibs5 :/ Keeping KDE4 stuff for compatibility doesn't make sense to me, as if someone really wants KDE4, then they can use the standard Intrepid ISO(or nightly neon) 
```

ktorrent
ksystemlog
khelpcenter4 (still exists on ISO)
kdelibs5
kdelibs5-data
kdelibs-bin
libkdecorations4
libkwineffects1
python-kde4
gwenview

```

Someone please comment on this(dentaku65, you made the tut. Does nightly neon satisfy the urge for KDE4) Not to mention, there are KDE4 apps in the KDE3 repo, then if an update comes along, you wont get it as KDE3 is like an upgrade.


Also, I'm pretty sure without removing all the KDE4 packages, it is unlikely anyone will be able to strip enough without removing oOo from it to get it under 700MB.

Sorry red_team for the delay, I'm quite busy at the moment... but I can confirm that the list you provide is all under KDE4 and not KDE3 and, as far as I checked are all working, but I don't know if these apps/libs are kept from Kubuntu Intrepid origin (before the install of kde3) or comes from KDE4 Nightly (which I have installed after the KDE3 installation).

---

### Post by madscientist159 on 2008-11-04
> **red_team316 said:**
> Here is a list of packages I found that are still needing to be added for the KDE3 versions to the repo or other packages that need removed from IntrepidKDE3. Why you are keeping some KDE4 stuff for compatibility still eludes me, supposedly you can add the nightly neon repo for KDE4, I would think those packages are there. My Installed Hardy works fine and I have no KDE4 packages, even kdelibs5 :/ Keeping KDE4 stuff for compatibility doesn't make sense to me, as if someone really wants KDE4, then they can use the standard Intrepid ISO(or nightly neon) 
```

ktorrent
ksystemlog
khelpcenter4 (still exists on ISO)
kdelibs5
kdelibs5-data
kdelibs-bin
libkdecorations4
libkwineffects1
python-kde4
gwenview

```

Someone please comment on this(dentaku65, you made the tut. Does nightly neon satisfy the urge for KDE4) Not to mention, there are KDE4 apps in the KDE3 repo, then if an update comes along, you wont get it as KDE3 is like an upgrade.


Also, I'm pretty sure without removing all the KDE4 packages, it is unlikely anyone will be able to strip enough without removing oOo from it to get it under 700MB.

OK, kdesudo and ktorrent are finally built and uploaded.  I am currently building the rest of the packages in that list and hope to have them uploaded sometime soon.  kdesudo was a real pain; I had to modify the packaging more that usual to get it to "upgrade" successfully.

Can't you just apt-get remove the KDE4 packages that you don't want?:confused:

I have **no** KDE4 apps in my repository.  Period.:smile:  What did you come across that made you think that?

I keep some KDE4 stuff (not hosted locally, just that I don't conflict KDE3 with those Ubuntu packages) to maintain the most compatibility possible with the rest of Intrepid.

A question for those on this forum: do you want me to include the new Intrepid wallpapers into the KDE3.5 kubuntu-artwork package?

---

### Post by madscientist159 on 2008-11-04
> **dzsabor said:**
> First of all thank you for this repository, you saved my life :)

Is there a way to include KDE3 version of krusader and gwenview?
These two were installed from intrepid together with some KDE4 libs and I have some problems with them.

You're welcome!  I know the feeling...

I'll add those to the list of packages to compile.

BTW, I read somewhere that there is some concern this repository might disappear in the future.  This is **not true**; I will have this repository up until after Intrepid is no longer supported; hopefully far longer than that.  The hosting I mention in my signature is just for the high-bandwidth site; I have a lower bandwidth server that I don't pay as much for and if worse came to worse I'd just silently redirect to the lower bandwidth server--the repository would stay online.

---

### Post by red_team316 on 2008-11-04
> **madscientist159 said:**
> OK, kdesudo and ktorrent are finally built and uploaded.  I am currently building the rest of the packages in that list and hope to have them uploaded sometime soon.  kdesudo was a real pain; I had to modify the packaging more that usual to get it to "upgrade" successfully.

Can't you just apt-get remove the KDE4 packages that you don't want?:confused:

I have **no** KDE4 apps in my repository.  Period.:smile:  What did you come across that made you think that?

I keep some KDE4 stuff (not hosted locally, just that I don't conflict KDE3 with those Ubuntu packages) to maintain the most compatibility possible with the rest of Intrepid.

A question for those on this forum: do you want me to include the new Intrepid wallpapers into the KDE3.5 kubuntu-artwork package?

I can apt-get remove them, but why not create a no-kde4 package that removes all KDE4 stuff. I think it's a good idea.

And as far as that list some of them are lingering KDE4 packages while others(like ksystemlog) need to be added to your repo as an upgrade. I'm using ksystemlog as an example because I know the package name is the same between hardy and intrepid, but my ISO has the KDE4 version right now. I'm sure you're noticing each package in there is a slightly different case.

Yes, do include the intrepid wallpaper in the kubuntu-artwork package or add it to the kubuntu-default-settings package(make sure it is the right package, I'm going from memory right now lol). I was going to do that manually or suggest that you do it for your repo but you beat me to the punch.


I have another question. Why must this be built from Hardy doing an upgrade? I would think that one would be able to start with an Intrepid Disc or ISO.


EDIT: adding kdesudo to your repo cleared the problem up :D

```

gdebi-core
gdebi-kde

```
also need added to your repos. The gdebi lingering around in the ISO is looking for python-kde4, and on my hardy box the gdebi looks for python-kde3.

```

jockey-kde
jockey-common

```
also need added to your repos. The jockey-kde lingering around in the ISO is looking for python-kde4.

Tim your doing a great job. keep pounding away at the repo and I'll keep pounding away at finding problems.

---

### Post by madscientist159 on 2008-11-05
> **red_team316 said:**
> I can apt-get remove them, but why not create a no-kde4 package that removes all KDE4 stuff. I think it's a good idea.
Can you create a list of KDE4 software that can safely be removed?  I would then put the metapackage together.

> **red_team316 said:**
> And as far as that list some of them are lingering KDE4 packages while others(like ksystemlog) need to be added to your repo as an upgrade. I'm using ksystemlog as an example because I know the package name is the same between hardy and intrepid, but my ISO has the KDE4 version right now. I'm sure you're noticing each package in there is a slightly different case.

Yes, do include the intrepid wallpaper in the kubuntu-artwork package or add it to the kubuntu-default-settings package(make sure it is the right package, I'm going from memory right now lol). I was going to do that manually or suggest that you do it for your repo but you beat me to the punch.
That might be a bit more difficult than I first thought--the wallpaper does not seem to be part of any Intrepid package!  I am trying to figure out where it comes from right now.  Any Ubuntu devs want to shed some light on this?  I thought every file on the system was part of a package (excepting user-added files of course ;-))

> **red_team316 said:**
> 
I have another question. Why must this be built from Hardy doing an upgrade? I would think that one would be able to start with an Intrepid Disc or ISO. You don't have to--feel free to use an Intrepid ISO.

> **red_team316 said:**
> 
EDIT: adding kdesudo to your repo cleared the problem up :D

```

gdebi-core
gdebi-kde

```
also need added to your repos. The gdebi lingering around in the ISO is looking for python-kde4, and on my hardy box the gdebi looks for python-kde3.

Added

> **red_team316 said:**
> 
```

jockey-kde
jockey-common

```
also need added to your repos. The jockey-kde lingering around in the ISO is looking for python-kde4.
That is most likely not a good idea.  I don't know all the details of how Jockey works, but from what I can tell it goes out to a Hardy or Intrepid specific website and downloads drivers.  Mixing and matching Ubuntu versions might not work so well...

Besides, jockey-kde in Intrepid is broken anyway.  Just use jockey-gtk; it works much better.

> **red_team316 said:**
> 
Tim your doing a great job. keep pounding away at the repo and I'll keep pounding away at finding problems.
Thanks!  Keep finding those problems and I'll keep fixing 'em...:)

---

### Post by red_team316 on 2008-11-06
> **madscientist159 said:**
> Can you create a list of KDE4 software that can safely be removed?  I would then put the metapackage together.

Yea, I can come up with a list. Most of what I have found so far is comparing hardy packages to intrepid, and then looking at the package details through adept. Alot of them I'm sure are packages you've added the kde3 version to your repo. It will take a little while to compose the list...
I think QT4 packages are safe to keep as thats the only thing I've noticed on my hardy that would even be related to KDE4.
> **madscientist159 said:**
> 
That might be a bit more difficult than I first thought--the wallpaper does not seem to be part of any Intrepid package!  I am trying to figure out where it comes from right now.  Any Ubuntu devs want to shed some light on this?  I thought every file on the system was part of a package (excepting user-added files of course ;-))

Upon extraction of the intrepid ISO, the wallpaper can be found here:
usr/share/wallpapers/Blue_Curl/contents/images. 
All you need to do is rename it to kubuntu-wallpaper.jpg and then slipstream it into the KDE3 kubuntu-default-settings package. Thats where the default wallpaper resides. Then just edit the kubuntu-wallpaper.jpg.desktop file to be:
```

[Wallpaper]
Encoding=UTF-8
File=kubuntu-wallpaper.jpg
Name=Blue Curl by Nuno Pinheiro
ImageType=pixmap

```
I could not find it in the KDE4 kubuntu-default-settings package so maybe they just haven't done a package for it yet. I would suggest using the 1920X1200 or the 1600X1200 image for slipstreaming.

> **madscientist159 said:**
> 
That is most likely not a good idea.  I don't know all the details of how Jockey works, but from what I can tell it goes out to a Hardy or Intrepid specific website and downloads drivers.  Mixing and matching Ubuntu versions might not work so well...

Besides, jockey-kde in Intrepid is broken anyway.  Just use jockey-gtk; it works much better.

hmm, good point. I never use it anyway. I always install mine by hand(kill x, compile kernel module restart x). I borked my vanilla intrepid install doing it by hand so maybe intrepid needs an updated driver for my card. 

Having a working jockey would really be nice for people who use it to install drivers, but if either one will cause problems or not then it may not be a good idea. jockey is pretty low on my priority list though.

> **madscientist159 said:**
> 
Thanks!  Keep finding those problems and I'll keep fixing 'em...:)
Yea, you've added several packages since we've started this, maybe one of those cleared up the kdm problem too...I'll test again later by removing gdm and doing a "dpkg-reconfigure kdm". I did try copying over the kubuntu kdm theme to gdm folder as seeing the it's still a gdmgreetertheme file, but I do know kdm does have some technical differences from gdm. It gave me some funny error on my hardy box then defaulted to the circles theme lol. I'm sure it's something in the .xml file thats different from gdm to kdm :P

---

### Post by Spaceman9 on 2008-11-08
I've been using Ubuntu since last year and with version 8.10 I've decided to stop using Ubuntu. The reason is KDE4. It's not really ready for every day use yet and won't be finished until 2010. I should say by way of explanation, that I've always installed Gnome and KDE into every distro I've have installed on my computer. I like both desktops and the idea of open source is choice. With Ubuntu there isn't any choice anymore. Linux Mint 5 KDE, Sidux 3 and Debian 4 still use KDE 3.x. Debian 5 will also use KDE 3.x. 

This quote is from the Kubuntu home page:

"8.10 will only include KDE 4 as its desktop. KDE 3 will not be available. As the code-name suggests, Intrepid is intended as a deliberately cutting edge release, if you would rather stay with what you know 8.04 continues to be fully supported. The development team decided that time and manpower considerations as well as the probable(possible) lack of further 3.5x releases prevent them from maintaining 2 separate versions, and KDE 4 was chosen as the version to move forward with." 

I believe the 3 distros I listed above have looked at KDE 4.x and understand it's not really ready for everyday use and understand it's more important to provide their users with a fully functional desktop  then it is to be on a cutting edge that's still just a dull blade. I'm switching to Sidux.

---

### Post by woko on 2008-11-09
First of all I want to thank dentaku65 for creating this thread and the sources.list, madscientist159 for his repository and red_team316 for the shortcut. With your help I managed to successfully upgrade to Intrepid without KDE4! The only thing I had to fix was to set the kdm startscipts behind the hal startscripts (S13kdm -> S25kdm). Otherwise I had no mouse and keyboard at the login window [http://bugs.launchpad.net/ubuntu/intrepid/+source/xorg/+bug/271138]("http://bugs.launchpad.net/ubuntu/intrepid/+source/xorg/+bug/271138").
I was yust about switching to Gnome, when I found this thread. In my opinion KDE3 is better than Gnome, but KDE4 is still not usable for productive work and I can't understand the decision of leaving it in Intrepid. I am doing my daily work as a programmer with KDE3 for over five years now and was happy with it, until KDE4. My colleagues already crossed the divide to Gnome. Maybe I can bring them back with your help.

---

### Post by dentaku65 on 2008-11-09
> **Spaceman9 said:**
> I've been using Ubuntu since last year and with version 8.10 I've decided to stop using Ubuntu. The reason is KDE4. It's not really ready for every day use yet and won't be finished until 2010. I should say by way of explanation, that I've always installed Gnome and KDE into every distro I've have installed on my computer. I like both desktops and the idea of open source is choice. With Ubuntu there isn't any choice anymore. Linux Mint 5 KDE, Sidux 3 and Debian 4 still use KDE 3.x. Debian 5 will also use KDE 3.x. 

This quote is from the Kubuntu home page:

"8.10 will only include KDE 4 as its desktop. KDE 3 will not be available. As the code-name suggests, Intrepid is intended as a deliberately cutting edge release, if you would rather stay with what you know 8.04 continues to be fully supported. The development team decided that time and manpower considerations as well as the probable(possible) lack of further 3.5x releases prevent them from maintaining 2 separate versions, and KDE 4 was chosen as the version to move forward with." 

I believe the 3 distros I listed above have looked at KDE 4.x and understand it's not really ready for everyday use and understand it's more important to provide their users with a fully functional desktop  then it is to be on a cutting edge that's still just a dull blade. I'm switching to Sidux.

Spaceman,
I really understand your complain about Kubuntu 8.10 but, as I said on the post #1, this is not a tread against kde4.
Many people here have this problem on production/personal machines involved in Kubuntu and the decision to dismiss kde3 put (at least me) in a very difficult position.
I've decided to stay in *ubuntu for many reasons, first of all for the community and for the project itself and that's why I start this tread :-)

---

### Post by dentaku65 on 2008-11-09
> **woko said:**
> First of all I want to thank dentaku65 for creating this thread and the sources.list, madscientist159 for his repository and red_team316 for the shortcut. With your help I managed to successfully upgrade to Intrepid without KDE4! The only thing I had to fix was to set the kdm startscipts behind the hal startscripts (S13kdm -> S25kdm). Otherwise I had no mouse and keyboard at the login window [http://bugs.launchpad.net/ubuntu/intrepid/+source/xorg/+bug/271138]("http://bugs.launchpad.net/ubuntu/intrepid/+source/xorg/+bug/271138").
I was yust about switching to Gnome, when I found this thread. In my opinion KDE3 is better than Gnome, but KDE4 is still not usable for productive work and I can't understand the decision of leaving it in Intrepid. I am doing my daily work as a programmer with KDE3 for over five years now and was happy with it, until KDE4. My colleagues already crossed the divide to Gnome. Maybe I can bring them back with your help.

Welcome here woko and thanks for you support
:guitar:

---

### Post by rohandhruva on 2008-11-09
Hi,

Thank you very much for the repository and this guide. I had only one question though - why ask people to first install GNOME (ubuntu-desktop) and then KDE3? I am currently using Hardy KDE3 and I want to upgrade to Intrepid using pearsoncomputing packages. Those KDE3 packages are not independent? Is gnome a compulsory requirement for those packages?

I am thinking of upgrading this way, is it fine:

1. Replace all instances of "hardy" with "intrepid" in sources.list
2. Add the pearsoncomputing.net lines at the very bottom
3. sudo apt-get update; sudo apt-get dist-upgrade (how many ever times it takes)
4. sudo apt-get install kde3

Is that enough to get a stable KDE3 system with Intrepid? Also, will upgrading to these packages change my look and feel in any way?

Thanks.

---

### Post by dentaku65 on 2008-11-09
> **rohandhruva said:**
> Hi,

Thank you very much for the repository and this guide. I had only one question though - why ask people to first install GNOME (ubuntu-desktop) and then KDE3? I am currently using Hardy KDE3 and I want to upgrade to Intrepid using pearsoncomputing packages. Those KDE3 packages are not independent? Is gnome a compulsory requirement for those packages?

I am thinking of upgrading this way, is it fine:

1. Replace all instances of "hardy" with "intrepid" in sources.list
2. Add the pearsoncomputing.net lines at the very bottom
3. sudo apt-get update; sudo apt-get dist-upgrade (how many ever times it takes)
4. sudo apt-get install kde3

Is that enough to get a stable KDE3 system with Intrepid? Also, will upgrading to these packages change my look and feel in any way?

Thanks.

I think that there is no problem in your way, but because it is a version upgrade I suggest to install ubuntu-desktop just to have a complete upgraded system in any case.
Btw installing with aptitude command you can remove completely ubuntu-desktop with aptitude as well.

---

### Post by rohandhruva on 2008-11-09
> **dentaku65 said:**
> I think that there is no problem in your way, but because it is a version upgrade I suggest to install ubuntu-desktop just to have a complete upgraded system in any case.
Btw installing with aptitude command you can remove completely ubuntu-desktop with aptitude as well.

I had installed kde4 on Hardy using aptitude. I later tried to do "sudo aptitude remove kubuntu-kde4-desktop", and that did *not* clear out all the packages, it offered to just remove the meta package. I had to manually weed out KDE4 (installed from the ppa) on my system. I just don't want a similar experience with gnome - having to manually remove each and every gnome related package.

---

### Post by ChiaGod on 2008-11-09
First, to dentaku and madscientist, thank you *very* much.  I was resigned to using gnome with ibex until I came across your thread.

Everythings running great, and I'm back to a usable system but with one caveat.  Occasionally clicking (left/middle/right) ceases to function.  I am able to use the keyboard, I can move the cursor, but with either mouse (I have a PS/2 and  USB connected) clicking in any shape or form is not registering.

The only fix I've found is to restart X (Cntrl + Alt + Backspace).  I noted this issue after the upgrade and changing back to KDE 3.5.  Is there any direction you can point me to for troubleshooting this?  

I've noted that everytime this has happened I've had a Konqueror window open (though I typically keep one Konq window up at all times).

---

### Post by dentaku65 on 2008-11-10
> **rohandhruva said:**
> I had installed kde4 on Hardy using aptitude. I later tried to do "sudo aptitude remove kubuntu-kde4-desktop", and that did *not* clear out all the packages, it offered to just remove the meta package. I had to manually weed out KDE4 (installed from the ppa) on my system. I just don't want a similar experience with gnome - having to manually remove each and every gnome related package.

For Intrepid you should find interesting this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
:)

---

### Post by rohandhruva on 2008-11-10
> **dentaku65 said:**
> For Intrepid you should find interesting this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
:)

Thanks a lot, that was certainly helpful. I will first try to upgrade to KDE3 on intrepid without having GNOME installed.

Two questions:

1. If I install 'kubuntu-desktop' after enabling the pearsoncomputing repository, will it install KDE4? Or is the metapackage pointing to KDE3?

2. If I do an in-place upgrade, will I lose my KDE3 settings and look-n-feel?

---

### Post by dentaku65 on 2008-11-10
> **rohandhruva said:**
> Thanks a lot, that was certainly helpful. I will first try to upgrade to KDE3 on intrepid without having GNOME installed.

Two questions:

1. If I install 'kubuntu-desktop' after enabling the pearsoncomputing repository, will it install KDE4? Or is the metapackage pointing to KDE3?

2. If I do an in-place upgrade, will I lose my KDE3 settings and look-n-feel?

1) No. Metapackage of Kubuntu replace kde3 (as well as kde3 replace kubuntu kde4); as I wrote you can use Nightly for kde4
2) I think partially you loose something (I loose something in look'n'feel in the way I did the upgrade)

---

### Post by rohandhruva on 2008-11-10
Ok one question - do the laptop extra keys work? I mean the keys for increasing the volume, muting, brightness etc.

And one doubt - I current have Hardy installed, and it has the metapackage "kubuntu-desktop" installed. If I follow my method, won't this package be upgraded, and give me KDE4?

---

### Post by rohandhruva on 2008-11-10
I tried upgrading the way I had told - I replaced hardy with intrepid, and added the pearsoncomputing repository at the end. I did aptitude update, and aptitude dist-upgrade. It was giving me quite a few problems, I am attaching the log file. I feel that it is a waste of bandwidth to first upgrade KDE3 (hardy) -> KDE4 (intrepid) -> KDE3 (intrepid, pearsoncomputing), especially since I am on a 256kbps connection.

Please help me figure out what is going wrong.

---

### Post by madscientist159 on 2008-11-10
> **rohandhruva said:**
> I tried upgrading the way I had told - I replaced hardy with intrepid, and added the pearsoncomputing repository at the end. I did aptitude update, and aptitude dist-upgrade. It was giving me quite a few problems, I am attaching the log file. I feel that it is a waste of bandwidth to first upgrade KDE3 (hardy) -> KDE4 (intrepid) -> KDE3 (intrepid, pearsoncomputing), especially since I am on a 256kbps connection.

Please help me figure out what is going wrong.

Sorry I was away for so long; I had some other business to tend to.

The upgrade path between KDE3(Hardy) and KDE3(Intrepid) is much easier at the moment.  To go from KDE4(Intrepid) to KDE3(Intrepid) will require you to remove as much of KDE4 as you can before installing KDE3, or you will probably have to force overwrite some KDE4 packages.

I will look over the debug log you attached and see if I can find the broken package that is preventing a proper upgrade to KDE3...

---

### Post by rohandhruva on 2008-11-10
> **madscientist159 said:**
> 
The upgrade path between KDE3(Hardy) and KDE3(Intrepid) is much easier at the moment.  

Can you please tell me what is the procedure you recommend? Do I install gnome (i.e. ubuntu-desktop)?

---

### Post by madscientist159 on 2008-11-10
> **rohandhruva said:**
> Can you please tell me what is the procedure you recommend? Do I install gnome (i.e. ubuntu-desktop)?

What I do is this:
1. Start with Ubuntu Hardy with KDE3.5 installed on it.
2. Modify your /etc/apt/sources.list to contain only the Ubuntu Intrepid repositories (main, universe, etc.) **and** the pearsoncomputing KDE3.5 repository.
3. sudo apt-get dist-upgrade :)

You may want to apt-get install kde3 when the dist-upgrade completes.  Also make sure that kubuntu-desktop is installed (it should be if it was already installed in Hardy).

---

### Post by madscientist159 on 2008-11-10
> **red_team316 said:**
> Yea, I can come up with a list. Most of what I have found so far is comparing hardy packages to intrepid, and then looking at the package details through adept. Alot of them I'm sure are packages you've added the kde3 version to your repo. It will take a little while to compose the list...
I think QT4 packages are safe to keep as thats the only thing I've noticed on my hardy that would even be related to KDE4.

Upon extraction of the intrepid ISO, the wallpaper can be found here:
usr/share/wallpapers/Blue_Curl/contents/images. 
All you need to do is rename it to kubuntu-wallpaper.jpg and then slipstream it into the KDE3 kubuntu-default-settings package. Thats where the default wallpaper resides. Then just edit the kubuntu-wallpaper.jpg.desktop file to be:
```

[Wallpaper]
Encoding=UTF-8
File=kubuntu-wallpaper.jpg
Name=Blue Curl by Nuno Pinheiro
ImageType=pixmap

```
I could not find it in the KDE4 kubuntu-default-settings package so maybe they just haven't done a package for it yet. I would suggest using the 1920X1200 or the 1600X1200 image for slipstreaming.


hmm, good point. I never use it anyway. I always install mine by hand(kill x, compile kernel module restart x). I borked my vanilla intrepid install doing it by hand so maybe intrepid needs an updated driver for my card. 

Having a working jockey would really be nice for people who use it to install drivers, but if either one will cause problems or not then it may not be a good idea. jockey is pretty low on my priority list though.


Yea, you've added several packages since we've started this, maybe one of those cleared up the kdm problem too...I'll test again later by removing gdm and doing a "dpkg-reconfigure kdm". I did try copying over the kubuntu kdm theme to gdm folder as seeing the it's still a gdmgreetertheme file, but I do know kdm does have some technical differences from gdm. It gave me some funny error on my hardy box then defaulted to the circles theme lol. I'm sure it's something in the .xml file thats different from gdm to kdm :P

So...how's the CD coming along?:)  I would like to install Intrepid on some new computers with KDE3.5 installed from the start...

---

### Post by IgorG on 2008-11-10
Hi,

I have tried to upgrade from hardy with no luck.

sudo  apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
.....
Need to get 296kB/2081MB of archives.
After this operation, 758MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main kspy 7:3.5.10-0ubuntu1~intrepid1 [58.3kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted linux-restricted-modules-common 2.6.27-8.13 [10.2kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main update-manager-core 1:0.93.35 [228kB]
Fetched 238kB in 5min55s (670B/s)
Failed to fetch [http://apt.pearsoncomputing.net/pool/main/k/kdesdk/kspy_3.5.10-0ubuntu1~intrepid1_amd64.deb](http://apt.pearsoncomputing.net/pool/main/k/kdesdk/kspy_3.5.10-0ubuntu1~intrepid1_amd64.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Can this be fixed somehow? I've tried -m, but then apt-get complains about some deb files being not a valid DEB.

---

### Post by madscientist159 on 2008-11-10
> **IgorG said:**
> Hi,

I have tried to upgrade from hardy with no luck.

sudo  apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
.....
Need to get 296kB/2081MB of archives.
After this operation, 758MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main kspy 7:3.5.10-0ubuntu1~intrepid1 [58.3kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/restricted linux-restricted-modules-common 2.6.27-8.13 [10.2kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-proposed/main update-manager-core 1:0.93.35 [228kB]
Fetched 238kB in 5min55s (670B/s)
Failed to fetch [http://apt.pearsoncomputing.net/pool/main/k/kdesdk/kspy_3.5.10-0ubuntu1~intrepid1_amd64.deb](http://apt.pearsoncomputing.net/pool/main/k/kdesdk/kspy_3.5.10-0ubuntu1~intrepid1_amd64.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Can this be fixed somehow? I've tried -m, but then apt-get complains about some deb files being not a valid DEB.

Grr...looks like Servage truncated the kspy package files when I uploaded them.  I will have to re-upload that file; expect it fixed in a few hours.

Ignore the invalid deb warning.  It is only there because I manually edited a couple packages to quickly fix packaging problems, and is perfectly safe.

---

### Post by rohandhruva on 2008-11-10
> **madscientist159 said:**
> What I do is this:
1. Start with Ubuntu Hardy with KDE3.5 installed on it.
2. Modify your /etc/apt/sources.list to contain only the Ubuntu Intrepid repositories (main, universe, etc.) **and** the pearsoncomputing KDE3.5 repository.
3. sudo apt-get dist-upgrade :)

You may want to apt-get install kde3 when the dist-upgrade completes.  Also make sure that kubuntu-desktop is installed (it should be if it was already installed in Hardy).

That's *exactly* what I did, and I got the problems as mentioned in my earlier post - [http://ubuntuforums.org/showpost.php?p=6143049&postcount=60](http://ubuntuforums.org/showpost.php?p=6143049&postcount=60)

In an earlier post it is mentioned that installing "kubuntu-desktop" package will overwrite KDE3 with KDE4 from ubuntu repos. Is that true? Have you made a "kubuntu-desktop" package in the pearsoncomputing repo to override the official ubuntu repo package?

---

### Post by dentaku65 on 2008-11-10
> **rohandhruva said:**
> That's *exactly* what I did, and I got the problems as mentioned in my earlier post - [http://ubuntuforums.org/showpost.php?p=6143049&postcount=60](http://ubuntuforums.org/showpost.php?p=6143049&postcount=60)

In an earlier post it is mentioned that installing "kubuntu-desktop" package will overwrite KDE3 with KDE4 from ubuntu repos. Is that true? Have you made a "kubuntu-desktop" package in the pearsoncomputing repo to override the official ubuntu repo package?

No, not the metapackage, but kde3 (from Madscientist) and kde4 (from Kubuntu official) for the system means: KDE
As I wrote in the #1 I suggest to make the upgrading operations inside Gnome and, at the very last, enter in kde3 under Intrepid.
Then when you have tested your upgrade, you can easly remove Gnome if you wish.
Consider also that kdenetworkmanager plug-in does not work (or at least a week ago did not).

---

### Post by Digger78 on 2008-11-10
> **madscientist159 said:**
> So...how's the CD coming along?:)  I would like to install Intrepid on some new computers with KDE3.5 installed from the start...

When a working ISO is available, I will gladly seed it.

I'm installing ubuntu intrepid on my laptop and gonna install KDE3 from your repo.

madscientist159 Thank you for making it available, and thanks to red_team316 for working on an ISO.

You guys **will be** intrepid heroes :)

---

### Post by rohandhruva on 2008-11-10
> **dentaku65 said:**
> As I wrote in the #1 I suggest to make the upgrading operations inside Gnome and, at the very last, enter in kde3 under Intrepid.
Then when you have tested your upgrade, you can easly remove Gnome if you wish.
Consider also that kdenetworkmanager plug-in does not work (or at least a week ago did not).

That's going to be my final option if direct upgrade to KDE3 (pearson) doesn't work out. But madscientist himself says "The upgrade path between KDE3(Hardy) and KDE3(Intrepid) is much easier at the moment." so I am wondering why such a direct upgrade is not working for me.

I will definitely be replacing kdenetworkmanager with nm-applet as you suggest. Thanks once again :)

---

### Post by madscientist159 on 2008-11-10
> **rohandhruva said:**
> That's going to be my final option if direct upgrade to KDE3 (pearson) doesn't work out. But madscientist himself says "The upgrade path between KDE3(Hardy) and KDE3(Intrepid) is much easier at the moment." so I am wondering why such a direct upgrade is not working for me.

I will definitely be replacing kdenetworkmanager with nm-applet as you suggest. Thanks once again :)

Looking through your log output, it looks like kubuntu-desktop is the main problem at the moment.  It is possible that I need to update dependencies for that package, as it looks like Aptitude cannot directly upgrade it (hence the "kept back")

Can you try this:
1. Remove kubuntu-desktop
2. Try the upgrade process again
3. If it works, then try to install kubuntu-desktop after the upgrade is complete

---

### Post by rohandhruva on 2008-11-10
> **madscientist159 said:**
> Looking through your log output, it looks like kubuntu-desktop is the main problem at the moment.  It is possible that I need to update dependencies for that package, as it looks like Aptitude cannot directly upgrade it (hence the "kept back")

Can you try this:
1. Remove kubuntu-desktop
2. Try the upgrade process again
3. If it works, then try to install kubuntu-desktop after the upgrade is complete

I tried it, still I am getting certain errors. I am attaching the log file. Please pardon some improper formatting, *script* seems to have mangled the file.

---

### Post by dentaku65 on 2008-11-10
> **rohandhruva said:**
> I tried it, still I am getting certain errors. I am attaching the log file. Please pardon some improper formatting, *script* seems to have mangled the file.

Well... I think that this happens because you trying to dist-upgrade inside kde... what happens with apt instead of aptitude?

---

### Post by rohandhruva on 2008-11-10
> **dentaku65 said:**
> Well... I think that this happens because you trying to dist-upgrade inside kde... what happens with apt instead of aptitude?

Thank you, that works. However, apt-get says

The following packages have been kept back:
  dolphin kde-guidance-powermanager

Should that cause any problems? Why is apt-get working, but not aptitude? Is there any conflict on my system? Should I rather upgrade from CLI than KDE?

---

### Post by madscientist159 on 2008-11-10
> **rohandhruva said:**
> Thank you, that works. However, apt-get says

The following packages have been kept back:
  dolphin kde-guidance-powermanager

Should that cause any problems? Why is apt-get working, but not aptitude? Is there any conflict on my system? Should I rather upgrade from CLI than KDE?

No, that will not cause any problems.  In fact, you could just remove those two packages, unless you want to keep Dolphin around for some reason.

I didn't think your use of aptitude instead of apt-get would cause a problem...good catch Dentaku!

---

### Post by rohandhruva on 2008-11-10
> **madscientist159 said:**
> I didn't think your use of aptitude instead of apt-get would cause a problem...good catch Dentaku!

But I fail to understand *why* should aptitude cause a problem?

---

### Post by dentaku65 on 2008-11-10
> **rohandhruva said:**
> But I fail to understand *why* should aptitude cause a problem?

I think because aptitude trying to manage all the complexity of the dependencies.
apt is a little bit straightforward.

---

### Post by rohandhruva on 2008-11-10
> **dentaku65 said:**
> I think because aptitude trying to manage all the complexity of the dependencies.
apt is a little bit straightforward.

Ah, ok. Thanks a lot for your help madscientist159 and dentaku65! I will be upgrading to intrepid with kde3 shortly.

---

### Post by red_team316 on 2008-11-11
certain packages are held back for many different reasons. There may be a bug in a package that does not allow it to upgrade properly or it could be something completely else.

To find out how to put packages on hold and take them off, look here:
[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto)

---

### Post by red_team316 on 2008-11-11
> **Digger78 said:**
> 
[quote="madscientist159"]
So...how's the CD coming along? I would like to install Intrepid on some new computers with KDE3.5 installed from the start...

When a working ISO is available, I will gladly seed it.

I'm installing ubuntu intrepid on my laptop and gonna install KDE3 from your repo.

madscientist159 Thank you for making it available, and thanks to red_team316 for working on an ISO.

You guys **will be** intrepid heroes :)[/QUOTE]

madscientist: I have been testing things a bit more a bit more. It would appear that the link that dentaku posted is pretty darn close to the list of packages I am seeing.
[quote="dentaku65"]
For Intrepid you should find interesting this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[/quote]
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Look at the Pure Gnome and it will give you KDE packages. Could you make a package that removes all of those in the list, so it can be tested. I know it has jockey and some other packages we talked about but since it removes all, it should be a good indication of what isn't installed by a package. I've noticed apt-get removing/purging kubuntu-default-settings still leaves kde4-profile directory(stuff like that).

It will be next week at the very earliest for an ISO. I did take a look at the fix for kdm(thanks woko), although have not had time to integrate and test it yet, it appears it has worked for several others, and it's not just limited to kdm, gdm supposedly had the problem too(the link to the fix is posted earlier in this thread). This weekend I plan to go hunting.

[quote="woko"]
First of all I want to thank dentaku65 for creating this thread and the sources.list, madscientist159 for his repository and red_team316 for the shortcut. With your help I managed to successfully upgrade to Intrepid without KDE4! The only thing I had to fix was to set the kdm startscipts behind the hal startscripts (S13kdm -> S25kdm). Otherwise I had no mouse and keyboard at the login window [http://bugs.launchpad.net/ubuntu/int...rg/+bug/271138](http://bugs.launchpad.net/ubuntu/int...rg/+bug/271138).
I was yust about switching to Gnome, when I found this thread. In my opinion KDE3 is better than Gnome, but KDE4 is still not usable for productive work and I can't understand the decision of leaving it in Intrepid. I am doing my daily work as a programmer with KDE3 for over five years now and was happy with it, until KDE4. My colleagues already crossed the divide to Gnome. Maybe I can bring them back with your help.
[/quote]

---

### Post by Miguellint on 2008-11-11
Just adding my thanks for the work you guys are doing. Totally appreciated. Intrepid remains usable.

I am fortunate in that I run Ubuntu with KDM, not Kubuntu, so my upgrade from KDE 4.1 to KDE 3.5 was painless.

You guys deserve medals.

Regards
Miguel

---

### Post by dentaku65 on 2008-11-11
> **Miguellint said:**
> Just adding my thanks for the work you guys are doing. Totally appreciated. Intrepid remains usable.

I am fortunate in that I run Ubuntu with KDM, not Kubuntu, so my upgrade from KDE 4.1 to KDE 3.5 was painless.

You guys deserve medals.

Regards
Miguel

Welcome aboard Miguellinit
:)

---

### Post by iX9 on 2008-11-11
**Hi!**

Great work, this guide, thanx a lot :) !

Maybe someone will be interest *my* way:
I dont like to install Hardy, and dont like to install Gnome...
So, :
1.) I have downloaded Kubuntu 8.10 *ALTERNATE* CD.
2.) Boot from this LiveCD and right after language selection, press F4 and select *"Install Command-line system only"*.
3.) Setup other things and install system.
4.) After install, log in and add madscientist159's repository in sources.list.
5.) sudo apt-get update.
6.) **sudo apt-get install kde3.**

Now you have pure Intrepid KDE3. ):P


Note: Some apps/packages are missing in compare to my older Hardy instalation: Adept, Dolpfin, Krusader, Firefox..., Usplash, QtCuve...etc. Install manually.
Note2: Sorry for my very bad English...:confused:
iX9

---

### Post by dentaku65 on 2008-11-11
> **iX9 said:**
> **Hi!**

Great work, this guide, thanx a lot :) !

Maybe someone will be interest *my* way:
I dont like to install Hardy, and dont like to install Gnome...
So, :
1.) I have downloaded Kubuntu 8.10 *ALTERNATE* CD.
2.) Boot from this LiveCD and right after language selection, press F4 and select *"Install Command-line system only"*.
3.) Setup other things and install system.
4.) After install, log in and add madscientist159's repository in sources.list.
5.) sudo apt-get update.
6.) **sudo apt-get install kde3.**

Now you have pure Intrepid KDE3. ):P


Note: Some apps/packages are missing in compare to my older Hardy instalation: Adept, Dolpfin, Krusader, Firefox..., Usplash, QtCuve...etc. Install manually.
Note2: Sorry for my very bad English...:confused:
iX9

Please, be aware that some packages you mentioned above are not from KDE, like firefox or usplash, so it is correct that they don't exist :-)
That's why I suggest to install ubuntu (Gnome) by side as described on post #1

---

### Post by red_team316 on 2008-11-11
I dont think madscientist has added Krusader to the repo yet. 

Usplash should be installed regardless of KDE3.

And yes, Kubuntu does not ship with firefox, it comes with Konqueror.

---

### Post by madscientist159 on 2008-11-11
> **red_team316 said:**
> I dont think madscientist has added Krusader to the repo yet. 

Usplash should be installed regardless of KDE3.

And yes, Kubuntu does not ship with firefox, it comes with Konqueror.

I have indeed uploaded Krusader--in fact, the only package that I still need to work on is kubuntu-desktop and the nokde4 package.:)
[B]
For those getting 404 errors:[/B] I am extremely angry at Servage right now.  I logged in this morning only to find out that the entire repository was deleted!!!:mad:  I will change the DNS to point at my low bandwidth in-house server for now, but with the traffic I am getting (>8Gb a **day**) I have no idea how well that will work.

Can anyone recommend a better (i.e. more reliable) inexpensive hosting service?

---

### Post by dentaku65 on 2008-11-11
> **madscientist159 said:**
> I have indeed uploaded Krusader--in fact, the only package that I still need to work on is kubuntu-desktop and the nokde4 package.:)
[B]
For those getting 404 errors:[/B] I am extremely angry at Servage right now.  I logged in this morning only to find out that the entire repository was deleted!!!:mad:  I will change the DNS to point at my low bandwidth in-house server for now, but with the traffic I am getting (>8Gb a **day**) I have no idea how well that will work.

Can anyone recommend a better (i.e. more reliable) inexpensive hosting service?

What about ppa?
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)
Somehow can be, if not official, at least connected with ubuntu.

---

### Post by madscientist159 on 2008-11-11
OK, DNS is switched.  The repository is now back online.

> **dentaku65 said:**
> What about ppa?
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)
Somehow can be, if not official, at least connected with ubuntu.

Yeah, there is a little problem there.  From [https://help.launchpad.net/Packaging/PPA:](https://help.launchpad.net/Packaging/PPA:)
> An APT repository of up to 1 gigabyte for free software
Trouble is, the repo is 1.5Gb in size and growing.
Also
> build and publish binary Ubuntu packages for multiple architectures simply by uploading an Ubuntu source package to Launchpad.
I've had to do so much fiddling with the build environment that I doubt this will work.  I want a place to upload the binaries (and source) that I have already built, tested, in some cases modified, and verified.:)

---

### Post by Robbyx on 2008-11-12
I upgraded from Hardy to intrepid and then decided to try out kde4. My machine is crashing. In case it is kde, as I am not using it, I would like to remove kde completely and still be left with a working Ubuntu. Is that possible?

---

### Post by dentaku65 on 2008-11-13
> **Robbyx said:**
> I upgraded from Hardy to intrepid and then decided to try out kde4. My machine is crashing. In case it is kde, as I am not using it, I would like to remove kde completely and still be left with a working Ubuntu. Is that possible?

I you intend Ubuntu = Gnome look here:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by rohandhruva on 2008-11-13
Any news on how the LiveCD preparation of Intrepid-KDE3 is going on?

---

### Post by red_team316 on 2008-11-13
I've been trying to do this with an Intrepid ISO as the base. It isn't going as well as the upgraded hardy to intrepid ISO. Have patience. Once I get the process for doing this figured out, I will definitely post a tut on how to do so yourself. The ISO is a small part of this project, the repo is the big part. Once we get most of the kinks pounded out for intrepid, there should be no reason why it wouldn't work with Jaunty or Jaunty+1 fairly easy.

madscientist: I have done:
Intrepid extraction...
apt-get purge kde4*
then I try to install kubuntu-desktop, it gives me a bunch of garbage. I do not want to install all of these insane packages. I cannot afford to download such a massive payload each time I need to test your repo. The kubuntu-desktop package should require the same dependancies/reccommends/suggests/conflicts/etc as the hardy version of the package. Do not include the kde3 package in this. The kde3 package is your insane install-everything I'll ever need package. Any packages that are standard packages, (specifically excluding your kde3 or nokde4) packages should exactly resemble the hardy packages. I really hope you haven't been modifiying the dependancies in a ton of different packages :( 

There will never be a LiveCD ISO from me if this isn't addressed. There is no way I can possibly strip the krud from it to create an image that will fit on a CD(less than 700MB). Think of it this way, your wife/gf/husband whatever goes to an auction and buys a huge box and brings it home. The box contains 97 KDE4 packages and 3 KDE packages. Since KDE4 is a forbidden word in your house, you throw all the KDE4 packages in your trash. This takes time as well as energy. It is not efficient. And the worst of all is that it takes forever because your garbage man wont pick up more than 2 KDE4 packages a week.

kdegames, kde3, kde3-amusements are obvious givaways. See the output from my chroot terminal below.
```

root@kubuntu-hardy-64-box:/# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  akregator amor ark arts artsbuilder atlantik atlantikdesigner blinken
  cervisia cryptsetup cvs dcoprss dirmngr docbook-defguide dvipdfmx edict
  enscript eyesapplet festival festlex-cmu festlex-poslex festvox-kallpc16k
  fifteenapplet flac gconf2 gconf2-common gettext gnome-keyring gnuift
  gnuift-perl gnupg2 gpgsm gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-x gvfs gvfs-backends indi
  jockey-common jockey-kde juk kaboodle kaddressbook kaddressbook-plugins
  kalarm kalzium kalzium-data kamera kanagram kandy kanjidic kappfinder karm
  kasteroids kate kate-plugins katomic kaudiocreator kbackgammon kbattleship
  kblackbox kbounce kbruch kbstate kcalc kcharselect kcoloredit kcontrol kcron
  kdat kde-icons-mono kde-kdm-themes kde3 kde3-amusements kde3-core
  kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin
  kdeadmin-kfile-plugins kdeartwork kdeartwork-emoticons kdeartwork-misc
  kdeartwork-style kdeartwork-theme-icon kdeartwork-theme-window kdebase
  kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins
  kdebase-runtime kdeedu kdeedu-data kdegames kdegames-card-data kdegraphics
  kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs-data kdelibs4c2a
  kdelibs5 kdelibs5-data kdelirc kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdesktop kdessh kdetoys kdeutils kdewallpapers kdewebdev kdf kdict
  kdm kdnssd kdvi kedit keduca kenolaba kfax kfaxview kfilereplace kfind
  kfloppy kfouleggs kgamma kgeography kgeography-data kget kghostview
  kgoldrunner kgpg khangman khelpcenter khexedit kicker kicker-applets
  kiconedit kig kimagemapeditor kitchensync kiten kjots kjumpingcube
  klaptopdaemon klatin kleopatra klettres klettres-data klickety klines
  klinkstatus klipper kmag kmahjongg kmail kmailcvt kmenuedit kmid kmilo
  kmines kmix kmoon kmousetool kmouth kmplot kmrml knetwalk knetworkconf
  knewsticker knode knotes kodo kolf kolourpaint kommander kompare
  konq-plugins konqueror konqueror-nsplugins konquest konsole konsolekalendar
  kontact kooka kopete korganizer korn kpackage kpager kpat kpdf kpercentage
  kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor
  kreversi krfb kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers
  kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot
  ksokoban kspaceduel ksplash kstars kstars-data ksvg ksysguard ksysguardd
  ksysv ktalkd kteatime ktimer ktip ktnef ktouch ktron kttsd ktuberling
  kturtle ktux kuser kverbos kview kviewshell kvoctrain kwalletmanager
  kweather kwifimanager kwin kwin4 kwordquiz kworldclock kxsldbg libakode2
  libarts1-akode libarts1-audiofile libarts1-mpeglib libarts1-xine libarts1c2a
  libartsc0 libavahi-glib1 libavc1394-0 libbeecrypt6 libbluetooth2
  libboost-python1.34.1 libcdio-cdda0 libcdio-paranoia0 libcdio7
  libcvsservice0 libdate-manip-perl libdb4.6++ libdv4 libestools1.2
  libgconf2-4 libglade2-0 libgnome-keyring0 libgnuift0c2a libgp11-0
  libgvfscommon0 libidl0 libiec61883-0 libindex0 libio-socket-ssl-perl
  libjpeg-progs libkcal2b libkcddb1 libkdeedu3 libkdegames1 libkdepim1a
  libkgantt0 libkiten1 libkleopatra1 libkmime2 libkonq4 libkpathsea4
  libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1
  liblockdev1 libmad0 libmeanwhile1 libmimelib1c2a libmrml1c2a
  libnet-ssleay-perl liboil0.3 libopenobex1 libopensync0 liborbit2
  libpam-gnome-keyring libparse-yapp-perl libpisock9 libpoppler-qt2 librpm4.4
  librss1 libshout3 libsoup2.4-1 libtidy-0.99-0 libtiff-tools libv4l-0
  libxml-dom-perl libxml-handler-trees-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-perl libxml-regexp-perl libxml-writer-perl
  libxml-xql-perl lilo-config lisa lmodern lskat mpeglib ncompress
  networkstatus noatun noatun-plugins obex-data-server ocrad p7zip-full
  perl-suid phonon phonon-backend-gstreamer pmount poster postfix procmail
  psutils python-kde4 qca-tls quanta quanta-data rpm superkaramba talk
  tex-common texlive-base texlive-base-bin texlive-base-bin-doc texlive-common
  texlive-doc-base texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-latex-base texlive-latex-base-doc tidy tipa ttf-sjfonts vorbis-tools
  xbase-clients xscreensaver xscreensaver-data xscreensaver-gl ytalk zoo
Suggested packages:
  rar unrar unrar-free monopd kdeedu-doc-html kdesdk-doc-html docbook
  docbook-xml lookup xjdic sdic-edict festival-freebsoft-utils festival-gaim
  pidgin-festival gettext-doc gnuift-doc gnupg-doc xloadimage
  kdeaddons-doc-html lame gnubg kde-i18n x-window-system-core
  kttsd-contrib-plugins kdeaccessibility-doc-html kdeadmin-doc-html
  kdebase-doc-html mtools kdegames-doc-html kdegraphics-doc-html fam
  kdemultimedia-doc-html kdenetwork-doc-html kdepim-doc-html egroupware efax
  hylafax-client mgetty-fax kdetoys-doc-html kdeutils-doc-html kommander-dev
  kdewebdev-doc-html menu htdig xmms-kde clamav f-prot-installer
  knewsticker-scripts gij-4.1 libgcj7-awt libjessie-java gnokii gnomemeeting
  povray kscreensaver-xsavers-webcollage libdv-bin libgnuift0-dev libmrml1-dev
  jpilot pilot-link gnome-pilot evolution claws-mail sylpheed libtiff-opengl
  p7zip-rar phonon-backend-xine phonon-backend-vlc phonon-backend-mplayer
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf
  postfix-cdb mail-reader python-kde4-dbg gubed php-doc alien talkd debhelper
  perl-tk xpdf-reader pdf-viewer tidy-doc xfishtank qcam streamer
The following packages will be REMOVED:
  libkonq5-templates
The following NEW packages will be installed:
  akregator amor ark arts artsbuilder atlantik atlantikdesigner blinken
  cervisia cryptsetup cvs dcoprss dirmngr docbook-defguide dvipdfmx edict
  enscript eyesapplet festival festlex-cmu festlex-poslex festvox-kallpc16k
  fifteenapplet flac gconf2 gconf2-common gettext gnome-keyring gnuift
  gnuift-perl gnupg2 gpgsm gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-x gvfs gvfs-backends indi
  jockey-kde juk kaboodle kaddressbook kaddressbook-plugins kalarm kalzium
  kalzium-data kamera kanagram kandy kanjidic kappfinder karm kasteroids kate
  kate-plugins katomic kaudiocreator kbackgammon kbattleship kblackbox kbounce
  kbruch kbstate kcalc kcharselect kcoloredit kcontrol kcron kdat
  kde-icons-mono kde-kdm-themes kde3 kde3-amusements kde3-core
  kdeaccessibility kdeaddons kdeaddons-kfile-plugins kdeadmin
  kdeadmin-kfile-plugins kdeartwork kdeartwork-emoticons kdeartwork-misc
  kdeartwork-style kdeartwork-theme-icon kdeartwork-theme-window kdebase
  kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins
  kdebase-runtime kdeedu kdeedu-data kdegames kdegames-card-data kdegraphics
  kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs-data kdelibs4c2a
  kdelibs5 kdelibs5-data kdelirc kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdesktop kdessh kdetoys kdeutils kdewallpapers kdewebdev kdf kdict
  kdm kdnssd kdvi kedit keduca kenolaba kfax kfaxview kfilereplace kfind
  kfloppy kfouleggs kgamma kgeography kgeography-data kget kghostview
  kgoldrunner kgpg khangman khelpcenter khexedit kicker kicker-applets
  kiconedit kig kimagemapeditor kitchensync kiten kjots kjumpingcube
  klaptopdaemon klatin kleopatra klettres klettres-data klickety klines
  klinkstatus klipper kmag kmahjongg kmail kmailcvt kmenuedit kmid kmilo
  kmines kmix kmoon kmousetool kmouth kmplot kmrml knetwalk knetworkconf
  knewsticker knode knotes kodo kolf kolourpaint kommander kompare
  konq-plugins konqueror konqueror-nsplugins konquest konsole konsolekalendar
  kontact kooka kopete korganizer korn kpackage kpager kpat kpdf kpercentage
  kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor
  kreversi krfb kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers
  kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot
  ksokoban kspaceduel ksplash kstars kstars-data ksvg ksysguard ksysv ktalkd
  kteatime ktimer ktip ktnef ktouch ktron kttsd ktuberling kturtle ktux
  kubuntu-desktop kuser kverbos kview kviewshell kvoctrain kwalletmanager
  kweather kwifimanager kwin kwin4 kwordquiz kworldclock kxsldbg libakode2
  libarts1-akode libarts1-audiofile libarts1-mpeglib libarts1-xine
  libavahi-glib1 libavc1394-0 libbeecrypt6 libbluetooth2 libboost-python1.34.1
  libcdio-cdda0 libcdio-paranoia0 libcdio7 libcvsservice0 libdate-manip-perl
  libdb4.6++ libdv4 libestools1.2 libgconf2-4 libglade2-0 libgnome-keyring0
  libgnuift0c2a libgp11-0 libgvfscommon0 libidl0 libiec61883-0 libindex0
  libio-socket-ssl-perl libjpeg-progs libkcal2b libkcddb1 libkdeedu3
  libkdegames1 libkdepim1a libkgantt0 libkiten1 libkleopatra1 libkmime2
  libkonq4 libkpathsea4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1
  libksieve0 libktnef1 liblockdev1 libmad0 libmeanwhile1 libmimelib1c2a
  libmrml1c2a libnet-ssleay-perl liboil0.3 libopenobex1 libopensync0 liborbit2
  libpam-gnome-keyring libparse-yapp-perl libpisock9 libpoppler-qt2 librpm4.4
  librss1 libshout3 libsoup2.4-1 libtidy-0.99-0 libtiff-tools libv4l-0
  libxml-dom-perl libxml-handler-trees-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-perl libxml-regexp-perl libxml-writer-perl
  libxml-xql-perl lilo-config lisa lmodern lskat mpeglib ncompress
  networkstatus noatun noatun-plugins obex-data-server ocrad p7zip-full
  perl-suid phonon phonon-backend-gstreamer pmount poster postfix procmail
  psutils python-kde4 qca-tls quanta quanta-data rpm superkaramba talk
  tex-common texlive-base texlive-base-bin texlive-base-bin-doc texlive-common
  texlive-doc-base texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-latex-base texlive-latex-base-doc tidy tipa ttf-sjfonts vorbis-tools
  xbase-clients xscreensaver xscreensaver-data xscreensaver-gl ytalk zoo
The following packages will be upgraded:
  jockey-common ksysguardd libarts1c2a libartsc0
4 upgraded, 387 newly installed, 1 to remove and 61 not upgraded.
Need to get 321MB of archives.
After this operation, 880MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by madscientist159 on 2008-11-14
> **red_team316 said:**
> 
madscientist: I have done:
Intrepid extraction...
apt-get purge kde4*
then I try to install kubuntu-desktop, it gives me a bunch of garbage. I do not want to install all of these insane packages. I cannot afford to download such a massive payload each time I need to test your repo. The kubuntu-desktop package should require the same dependancies/reccommends/suggests/conflicts/etc as the hardy version of the package. Do not include the kde3 package in this. The kde3 package is your insane install-everything I'll ever need package. Any packages that are standard packages, (specifically excluding your kde3 or nokde4) packages should exactly resemble the hardy packages. I really hope you haven't been modifiying the dependancies in a ton of different packages :( 

There will never be a LiveCD ISO from me if this isn't addressed. There is no way I can possibly strip the krud from it to create an image that will fit on a CD(less than 700MB). Think of it this way, your wife/gf/husband whatever goes to an auction and buys a huge box and brings it home. The box contains 97 KDE4 packages and 3 KDE packages. Since KDE4 is a forbidden word in your house, you throw all the KDE4 packages in your trash. This takes time as well as energy. It is not efficient. And the worst of all is that it takes forever because your garbage man wont pick up more than 2 KDE4 packages a week.

I will fix that problem.  I have only changed dependencies in the top-level metapackages; this was originally to force APT to actually do the "upgrade" from KDE4.  Now I don't think it is needed any more so I can restore the metapackage dependencies to as close to Hardy as I can get to work. :)

While I'm editing metapackages, do you have a list of KDE4 krud so that I can create the nokde4 metapackage?

---

### Post by madscientist159 on 2008-11-14
The new kubuntu-desktop metapackage is now up.  See if that fixes the problem...

---

### Post by astrophoenix on 2008-11-17
thanks to all, I have my spiffy old kde3 running on intrepid.

but now I'm missing kdiff3. madscientist, any chance of adding a kdiff3 package to your oh-so-handy repo?

thanks

---

### Post by madscientist159 on 2008-11-17
> **astrophoenix said:**
> thanks to all, I have my spiffy old kde3 running on intrepid.

but now I'm missing kdiff3. madscientist, any chance of adding a kdiff3 package to your oh-so-handy repo?

thanks

Uploaded.

Enjoy!:)

---

### Post by red_team316 on 2008-11-17
madscientist. It's down ~300MB but it could still be better. khelpcenter4 and python-kde4 are still in there. Can't you just extract a kubuntu-desktop.deb from hardy and use that for the dependancies then modify the maintainer and architecture? Here is the control file for Hardy's kubuntu-desktop package (version 1.75)
```

Package: kubuntu-desktop
Source: kubuntu-meta
Version: 1.75
Architecture: amd64
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Installed-Size: 44
Depends: acpi, acpi-support, acpid, alsa-base, alsa-utils, anacron, ark, arts, avahi-daemon, bc, ca-certificates, cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gutenprint, dbus, dc, foomatic-db, foomatic-db-engine, foomatic-filters, genisoimage, ghostscript-x, hal, hotkey-setup, kcontrol, kcron, kde-guidance, kde-style-qtcurve, kde-systemsettings, kdeadmin-kfile-plugins, kdebase-kio-plugins, kdegraphics-kfile-plugins, kdemultimedia-kfile-plugins, kdemultimedia-kio-plugins, kdenetwork-filesharing, kdenetwork-kfile-plugins, kdepasswd, kdeprint, kdesktop, kdm, kdnssd, kghostview, khelpcenter, kicker, kio-apt, kio-locate, kmenuedit, kmix, knetworkconf, konq-plugins, konsole, kpdf, ksmserver, ksnapshot, ksvg, ksystemlog, kubuntu-artwork-usplash, kwin, kwin-style-crystal, language-selector-qt, lftp, libarts1-akode, libgl1-mesa-glx, libglut3, libqt-perl, libsasl2-modules, libxp6, openprinting-ppds, pnm2ppa, powermanagement-interface, qca-tls, readahead, screen, smbclient, software-properties-kde, ttf-bitstream-vera, ttf-dejavu-core, ttf-freefont, unzip, usplash, vorbis-tools, x-ttcidfont-conf, xdg-user-dirs, xkb-data, xorg, zip
Recommends: adept, akregator, amarok, apport-qt, avahi-autoipd, bluez-cups, bluez-utils, bogofilter, brltty, cdparanoia, cdrdao, cups-pdf, desktop-effects-kde, digikam, dmz-cursor-theme, dolphin, dvd+rw-tools, foo2zjs, foomatic-db-gutenprint, foomatic-db-hpijs, fortune-mod, gcc, gdebi-kde, gtk-qt-engine, gwenview, hpijs-ppds, hplip, hplip-gui, ijsgutenprint, jockey-kde, k3b, kaddressbook, kaffeine, kamera, karm, katapult, kate, kbstate, kde-guidance-powermanager, kdebluetooth, kdepim-kio-plugins, kdepim-wizards, kdesudo, keep, kfind, kio-umountwrapper, kipi-plugins, klipper, kmag, kmail, kmailcvt, kmilo, kmousetool, kmplayer-konq-plugins, knotes, konqueror, konqueror-nsplugins, kontact, konversation, kooka, kopete, korganizer, kpf, kppp, krdc, krfb, kscreensaver, ksysguard, ktorrent, kubuntu-default-settings, kubuntu-docs, kubuntu-konqueror-shortcuts, kvkbd, kwalletmanager, landscape-client, laptop-detect, libgl1-mesa-dri, libnss-mdns, linux-headers-generic, make, min12xxw, network-manager-kde, networkstatus, openoffice.org-calc, openoffice.org-impress, openoffice.org-kde, openoffice.org-writer, pinentry-qt, powernowd, pxljr, rdesktop, scim-bridge-agent, scim-bridge-client-qt, scim-qtimm, skim, speedcrunch, splix, strigi-applet, strigi-daemon, system-config-printer-kde, ttf-arabeyes, ttf-arphic-ukai, ttf-arphic-uming, ttf-indic-fonts-core, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-thai-tlwg, ttf-unfonts-core, wodim, wvdial, xcursor-themes, xdg-utils
Section: metapackages
Priority: optional
Description: Kubuntu desktop system
 This package depends on all of the packages in the Kubuntu desktop system
 .
 It is safe to remove this package if some of the desktop system packages are
 not desired.

```

---

### Post by claydoh on 2008-11-18
> **Paul S said:**
> Would madscientist159 consider joining kubuntu team and posting them on kubuntu ppa, like some the original 3.5.10 were done for hardy?  Then he could get free bandwidth too!

regards,

Not only free space and bandwidth, but also hint, tips, knowledge, and general advice from the Kubuntu devs. :grin: I'd venture that nearly 100% of the issues seen here could be avoided by joining the community and dipping into that knowledge pool. Remember, one of the factors in not providing KDE3 in 8.10 was *manpower*, i.e,  no one stepped up to help maintain KDE3.

I sincerely recommend (as I have before) making your efforts part of the community

---

### Post by dentaku65 on 2008-11-18
> **claydoh said:**
> Not only free space and bandwidth, but also hint, tips, knowledge, and general advice from the Kubuntu devs. :grin: I'd venture that nearly 100% of the issues seen here could be avoided by joining the community and dipping into that knowledge pool. Remember, one of the factors in not providing KDE3 in 8.10 was *manpower*, i.e,  no one stepped up to help maintain KDE3.

I sincerely recommend (as I have before) making your efforts part of the community

I supposed that, in some way, the Kubuntu Team should contact Madscientist159 to organize the fusion of KDE3 in Kubuntu Intrepid, maybe in backports mode or in ppa.
I've read around that many Kubuntu users will appreciate the possibility to have both KDE at the moment.

---

### Post by claydoh on 2008-11-18
> **dentaku65 said:**
> I supposed that, in some way, the Kubuntu Team should contact Madscientist159

Back when Madscientist159 first started his work, I suggested contacting the kubuntu devs. He declined to do so. :( So maybe that is why no one has contacted him? :confused:


there just happens to be a [Kubuntu meeting](http://fridge.ubuntu.com/node/1738) today @ 20:00 GMT.....................:KS

---

### Post by TekkieFreak on 2008-11-18
This works absolutely beautifully for me Thank You, thank you, thank you!!

My hubby has been using Linux for years...and I just recently decided to switch over from my Mac to Ubuntu.  Anyway, I followed your instructions (with some help from hubby) and now I'm happily running 3.5 and it is absolutely *AMAZING*....so again...THANK YOU!!! THANK YOU!!! THANK YOU!!! :)

---

### Post by Arby on 2008-11-18
Hi folks,

The existence of this repository is causing some concern among the Kubuntu
developers. We know there are people who still want KDE3,  but recommend they
stick with 8.04 (Hardy) rather than use an untested and unsupported third party
archive. We are continuing to support Hardy for those users. In particular
there are some things about the way in which version numbers of the packages are
handled. Including a 7 at the start of the version number means that those
packages will always be newer than any package in the official Kubuntu repos
which all use an epoch of 4. This is probably the desired effect in the short
term for people using this KDE3 repository. However it is likely to cause
serious problems in the future as none of the official upgrade tools will be
unable to calculate a workable upgrade when the time comes for the transition
8.10 to 9.04 and future versions. If the upgrade does manage to proceed then the
end result is likely to be a badly broken system.

In addition, as future releases of KDE3 become less and less common the amount
of work required to maintain a usable KDE3 desktop will increase
dramatically. The interfaces presented by the underlying OS (kernel, X.org,
networking etc) will evolve but KDE3 software is unlikely to evolve to work with
those interfaces. At present the differences are small but they will grow. That
means this project extends from being a packaging effort into a coding and
patching project as well.

One of the main reasons that we decided not to keep KDE3 in Intrepid is that we
simply do not have the manpower to maintain both. If there are other people
prepared to do the work then we are open to discussion. If you want to contact
us on our mailing list at [email]kubuntu-devel@lists.ubuntu.com[/email] then we can try to work
out if there is a way for these packages to co-exist without breaking the
package management system.

regards,
Arby (on behalf of the Kubuntu development team)

---

### Post by madscientist159 on 2008-11-18
> **claydoh said:**
> Back when Madscientist159 first started his work, I suggested contacting the kubuntu devs. He declined to do so. :( So maybe that is why no one has contacted him? :confused:


there just happens to be a [Kubuntu meeting](http://fridge.ubuntu.com/node/1738) today @ 20:00 GMT.....................:KS

It's not that I don't want to join, I've just been snowed under at work for the past few weeks.  Any spare "ubuntu time" has gone into fixing various bugs and packaging problems, or updating one of the many Hardy machines I still have around the house.  That plus having to learn new tools (believe it or not I have never used IRC!) probably made it look like I declined.  Sorry!:-|

If you are willing to let me in anyway, then I do have something that I could use some help with.  There is a user who is trying to use his bluetooth mouse with KDE on Intrepid ([http://bugs.pearsoncomputing.net/show_bug.cgi?id=4](http://bugs.pearsoncomputing.net/show_bug.cgi?id=4)) and it won't work.  I do not have any Bluetooth peripherals to test with (yet) so I am at a loss as to what might be the problem.  Maybe someone has (a lot) more Bluetooth knowledge than I do and could help? ;)

I would be willing to compile/maintain KDE3.5 for Jaunty as well, now that I know the process and what to expect.

Just read the post right above this one.  First, I apologize for any problems I am (or will be) causing.  I would be happy to alter the packaging system to be more compatible--when I compiled this my first and foremost goal was to get KDE3 back onto Intrepid as fast as possible.  

I do understand that the underlying interfaces will change--in fact, I ran into this several times already, but was able to patch around the problems in all cases (except Bluetooth, as I do not know what is wrong).  I will do the work in what ways I can, but my time is limited, so there should be at least one other person who can help with this undertaking.

Ideally, KDE3 would be able to coexist with KDE4.  If I attempt this, would others on the kubuntu-devel list be able to assist if needed?  There are a lot of packages to change before this is possible, and I do not know if I will be able to alter all of them before Jaunty is released.

If anyone is still wondering why I (and others) didn't stay with Hardy, consider that:
1. A network printer spooler hang (requiring a restart to clear) was fixed in Intrepid
2. The new Xorg is faster
3. The Samba domain browser finally works in Intrepid
4. wxMaxima can finally generate plots in Intrepid
I have more, and I am sure others can add to this list, but you get the idea.  Sticking with Hardy is never going to fix those, or other, problems that users have.

---

### Post by dualscreenman on 2008-11-18
Kdebluetooth would have to be ported to the bluez 0.4 api. This is the same problem causing kdebluetooth4's failure in Intrepid.

As for package co-existance, the proper method would be to make the kde3 packages like the kde4 packages in Hardy were (except in reverse): add -kde3 extensions to the end of each package, install the binaries at /usr/lib/kde3 and patch the packages to use ~/.kde3 to save configuration data. This way they can live in peace with KDE4 and dist-upgrades to Jaunty and onward should still go OK. The method is not perfect-- like with the Hardy KDE4 packages sudo will not work with binaries installed to a non-default location-- but the method is much better than adding an epoch of 7 to the package versioning. :P

Unfortunately, it will be very hard for existing users of your current packaging to transition to the -kde3 packages, due to the epoch of 7.

---

### Post by madscientist159 on 2008-11-18
> **dualscreenman said:**
> Kdebluetooth would have to be ported to the bluez 0.4 api. This is the same problem causing kdebluetooth4's failure in Intrepid.

As for package co-existance, the proper method would be to make the kde3 packages like the kde4 packages in Hardy were (except in reverse): add -kde3 extensions to the end of each package, install the binaries at /usr/lib/kde3 and patch the packages to use ~/.kde3 to save configuration data. This way they can live in peace with KDE4 and dist-upgrades to Jaunty and onward should still go OK. The method is not perfect-- like with the Hardy KDE4 packages sudo will not work with binaries installed to a non-default location-- but the method is much better than adding an epoch of 7 to the package versioning. :P

Unfortunately, it will be very hard for existing users of your current packaging to transition to the -kde3 packages, due to the epoch of 7.

There is one way--I will generate an apt-get remove command that contains all of the epoch 7 packages.  Then they can immediately reinstall the -kde3 packages they want.  Am I thinking correctly there?

---

### Post by dentaku65 on 2008-11-19
> **Arby said:**
> Hi folks,

The existence of this repository is causing some concern among the Kubuntu
developers. We know there are people who still want KDE3,  but recommend they
stick with 8.04 (Hardy) rather than use an untested and unsupported third party
archive. We are continuing to support Hardy for those users. In particular
there are some things about the way in which version numbers of the packages are
handled. Including a 7 at the start of the version number means that those
packages will always be newer than any package in the official Kubuntu repos
which all use an epoch of 4. This is probably the desired effect in the short
term for people using this KDE3 repository. However it is likely to cause
serious problems in the future as none of the official upgrade tools will be
unable to calculate a workable upgrade when the time comes for the transition
8.10 to 9.04 and future versions. If the upgrade does manage to proceed then the
end result is likely to be a badly broken system.

In addition, as future releases of KDE3 become less and less common the amount
of work required to maintain a usable KDE3 desktop will increase
dramatically. The interfaces presented by the underlying OS (kernel, X.org,
networking etc) will evolve but KDE3 software is unlikely to evolve to work with
those interfaces. At present the differences are small but they will grow. That
means this project extends from being a packaging effort into a coding and
patching project as well.

One of the main reasons that we decided not to keep KDE3 in Intrepid is that we
simply do not have the manpower to maintain both. If there are other people
prepared to do the work then we are open to discussion. If you want to contact
us on our mailing list at [email]kubuntu-devel@lists.ubuntu.com[/email] then we can try to work
out if there is a way for these packages to co-exist without breaking the
package management system.

regards,
Arby (on behalf of the Kubuntu development team)

Thank you Arby for your post and proposal.
I hope Madscientist159 among others here can contact the Kubuntu devel Team in order to realize officially the kde3 package for Kubuntu Intrepid. I personally not so brilliant in repository/packaging stuff, but I can give my full support as tester without problems.
Pls, let's doing possible this!
Because staying with Hardy is not an option at all, sorry.
:guitar:

---

### Post by madscientist159 on 2008-11-19
I have been personally contacted by the Kubuntu developers and asked to take the repository offline.  At this point, to avoid further problems, that is what I will do.

Don't worry, we will be working on a proper way to get KDE3 onto Intrepid.:)  Most of those who really, really wanted KDE3 probably already have it at this point, and those who do not can wait for the fixed packages.

Tim

---

### Post by minneyar on 2008-11-19
> **Arby said:**
> Hi folks,

The existence of this repository is causing some concern among the Kubuntu
developers. We know there are people who still want KDE3,  but recommend they
stick with 8.04 (Hardy) rather than use an untested and unsupported third party
archive.

Unfortunately, it wasn't until after I had upgraded to Intrepid and spent some time actually working in KDE4 that I decided that I really did prefer KDE3 and it wasn't just the fact that I was unfamiliar with something new.

So my options were to either wipe my system and go back to Hardy or install some unofficial KDE3 packages... I'm glad I got them while the mirror was still up.

---

### Post by dentaku65 on 2008-11-19
> **madscientist159 said:**
> I have been personally contacted by the Kubuntu developers and asked to take the repository offline.  At this point, to avoid further problems, that is what I will do.

Don't worry, we will be working on a proper way to get KDE3 onto Intrepid.:)  Most of those who really, really wanted KDE3 probably already have it at this point, and those who do not can wait for the fixed packages.

Tim

Posted on #1

---

### Post by TekkieFreak on 2008-11-19
Hey guys, I'm willing to help if at all possible.  Just let me know what you need.  I used to be a programmer (mostly java).

Jill 

BTW,  I'd LOVE to see KDE4 get up to speed....so would be more than willing to help with that also.

I too really like the idea of getting kde3 and kde4 able to coexist.  I really love all the *bling* (what can I 
say, I'm a girl :) --- and it's such a nice change going from osX (where you can't configure anything except your wallpaper)....to kde where you can configure most everything.

---

### Post by madscientist159 on 2008-11-19
TekkieFreak,

Know anything about Bluetooth?  Apparently the current bluez is completely incompatible with KDE3.5, and there is some heavy recoding to do on the KDE3.5 end of things.:)

All,

I spoke with the Kubuntu developers this morning.  Basically, I will provide a script to migrate from the current "epoch 7" repository to the new -kde3 repository, and I will start the patch & rebuild process ASAP.

The good side of this is that the official KDE4 and KDE3.5 will finally be able to coexist, and I see no reason why I can't also package KDE3.5 for Jaunty.  There is even the possibility of this going semi-official, but don't hold your breath.:)

The downside is that I have no idea how long this is going to take.  I have to learn the PPA system and a few other tools...

Long term, I might be able to help KDE4 include some missing KDE3.5 options.  We'll see if the KDE devs get there first though. ;)  KDE4.2 added a "standard desktop" option, so that will make a lot of people (myself included) very happy.

Status updates will be posted here as I make progress.

Tim

---

### Post by TekkieFreak on 2008-11-19
ooOOO....heavy coding...as I said it's been a while.  And unfortunately I know nothing about bluetooth...but again I'm willing to take a look and see what I can figure out.  And if you have something a little less er *involved* to start with that would be fabulous. Like I said (at least I think I said it)...I've been out of the programming world for a while.

---

### Post by dentaku65 on 2008-11-19
> **madscientist159 said:**
> TekkieFreak,

Know anything about Bluetooth?  Apparently the current bluez is completely incompatible with KDE3.5, and there is some heavy recoding to do on the KDE3.5 end of things.:)

All,

I spoke with the Kubuntu developers this morning.  Basically, I will provide a script to migrate from the current "epoch 7" repository to the new -kde3 repository, and I will start the patch & rebuild process ASAP.

The good side of this is that the official KDE4 and KDE3.5 will finally be able to coexist, and I see no reason why I can't also package KDE3.5 for Jaunty.  There is even the possibility of this going semi-official, but don't hold your breath.:)

The downside is that I have no idea how long this is going to take.  I have to learn the PPA system and a few other tools...

Long term, I might be able to help KDE4 include some missing KDE3.5 options.  We'll see if the KDE devs get there first though. ;)  KDE4.2 added a "standard desktop" option, so that will make a lot of people (myself included) very happy.

Status updates will be posted here as I make progress.

Tim
I think there is a general problem with bluetooth in Intrepid:
[http://ubuntuforums.org/showthread.php?t=964139](http://ubuntuforums.org/showthread.php?t=964139)
Even if my USB donkey works out of the box (in Gnome, I did not installed kbluetooth, sorry I miss that because I rarely use bluetooth devices)

To do a workaround, you should install anyway:
```
sudo apt-get install bluez-compact bluez-tools
```

Then you can try these commands from terminal:
```
hcitool scan
```
```
hidd -s
```

The strange thing is that there is no more hcid command (from bluez packages), that was useful to start the bluez connector:
```
hcid -s
```
:confused:

---

### Post by Arby on 2008-11-19
Credit to madscientist159 for doing the right thing and coming to talk to us. Suddenly there are people appearing saying they want to help with Kubuntu all over the place. We've been looking for you lot for months :)

Anybody who wants to get involved is more than welcome. We can always use more pairs of hands. If you think you don't know how to do it, we can show you how. Contrary to popular myth you don't need to know how to code, although more of that is good too. For the people who want to start small, I'm sure we can find you something smaller than the bluetooth stack to fix. C++ and python are what we use most.

Testers are always welcome. In fact Jaunty alpha1 is out this week. Anybody who is prepared to donate a bit of bandwidth and some free time to download and test would be great. It's a pretty straight forward way to get involved. Once you get used to it you too can sit up until the wee small hours running tests because we had to re-build the images at 11pm the day before release :)

We could really use some bug triagers. Just some extra pairs of eyes to help us gather information and identify issues, trying to reproduce crashes etc. Good triage makes a really big difference to getting stuff fixed. It can be a bit daunting at first but there are plenty of folks around who can guide you in how to handle a new bug. The wiki has more info [https://wiki.kubuntu.org/Bugs/HowToTriage](https://wiki.kubuntu.org/Bugs/HowToTriage)

If anybody wants to join in the fun jump into #kubuntu-devel on IRC or introduce yourself on the mailing list [email]kubuntu-devel@lists.ubuntu.com[/email]. We can always find things for people to do.

I'll stop hijacking the thread now. Looks like this is all going to work out positively then :)

Arby

---

### Post by SagaciousKJB on 2008-11-19
Could this thread possibly be brought back on track to how to install KDE3 in Kubuntu 8.10?

I've just installed ubuntu-desktop because I can't stand it anymore.  And no, I'm not just whining about not liking the new stuff ( although it is mostly annoying ), my video configuration is no longer working correctly.  I watch videos in a dual xscreen; now all I get is the X server cursor on my second screen.


Someone at least make kde3 installable in 8.10 for the love of God!

---

### Post by dentaku65 on 2008-11-20
> **SagaciousKJB said:**
> Could this thread possibly be brought back on track to how to install KDE3 in Kubuntu 8.10?

I've just installed ubuntu-desktop because I can't stand it anymore.  And no, I'm not just whining about not liking the new stuff ( although it is mostly annoying ), my video configuration is no longer working correctly.  I watch videos in a dual xscreen; now all I get is the X server cursor on my second screen.


Someone at least make kde3 installable in 8.10 for the love of God!

No possible at the moment, but for a very good reason: see post #1

---

### Post by TekkieFreak on 2008-11-20
Quite Frankly, I don't really think he did anything wrong in the first place.  After all, open-source is open-source...No?  The idea being that anyone can use/modify/redistribute at will. So technically, he could come up with his own version and call it "Madbuntu" or whatever.  

I'm not sure whether or not it's possible to "back out" of his 3.5 install...but I guess I've installed it now, it works great and I'll have to cross that bridge when I come to it.  

Heck, look how Apple just based their OS on all the open-source stuff and how they take pieces and parts and modify them to their liking, package it up and it's a multi-billion dollar business.  We should all be so lucky. Ever heard of keyring?  Of course, you have!!! 

Anyway, this is in no way meant to be a flame.  I think there's many folks out there just like me who want to use Ubuntu all the time and run a nice KDE desktop...and bottom line is that for that to happen it has to work.  And yep, I'm more than willing to help!!! 

I'll hop on irc and see what's going on.  


> **Arby said:**
> Credit to madscientist159 for doing the right thing and coming to talk to us. Suddenly there are people appearing saying they want to help with Kubuntu all over the place. We've been looking for you lot for months :)

Anybody who wants to get involved is more than welcome. We can always use more pairs of hands. If you think you don't know how to do it, we can show you how. Contrary to popular myth you don't need to know how to code, although more of that is good too. For the people who want to start small, I'm sure we can find you something smaller than the bluetooth stack to fix. C++ and python are what we use most.

Testers are always welcome. In fact Jaunty alpha1 is out this week. Anybody who is prepared to donate a bit of bandwidth and some free time to download and test would be great. It's a pretty straight forward way to get involved. Once you get used to it you too can sit up until the wee small hours running tests because we had to re-build the images at 11pm the day before release :)

We could really use some bug triagers. Just some extra pairs of eyes to help us gather information and identify issues, trying to reproduce crashes etc. Good triage makes a really big difference to getting stuff fixed. It can be a bit daunting at first but there are plenty of folks around who can guide you in how to handle a new bug. The wiki has more info [https://wiki.kubuntu.org/Bugs/HowToTriage](https://wiki.kubuntu.org/Bugs/HowToTriage)

If anybody wants to join in the fun jump into #kubuntu-devel on IRC or introduce yourself on the mailing list [email]kubuntu-devel@lists.ubuntu.com[/email]. We can always find things for people to do.

I'll stop hijacking the thread now. Looks like this is all going to work out positively then :)

Arby

---

### Post by TekkieFreak on 2008-11-20
So what do we need to do to begin getting the kde3 packages separate from the kde4 packages so that they can co-exist on the same system?

Just let me know where to start. :)

---

### Post by freelsjd on 2008-11-22
:confused:The main problem I had with kde4 was that it does not have hiding panels as of intrepid.  This issue alone was enough to revert back to kde3.  Now am I going to have to revert back to Hardy ?  And for how long ?  Am I now going to give up Ubuntu (or kubuntu) altogether because of this issue.  This absolutely makes no sense to me at all !  You have a set of packages which are open source, and you force the guy to back down and not make them available to people that want them ?  

Now that I have blown a little steam, how can the average user help out ?  Can you at least tell us what the plan is ?

---

### Post by Lars Noodén on 2008-11-22
Thank you!  I'm following KDE4, but in no way shape or form is it ready for daily use or, more importantly work.  I very much need KDE3 to get work done in Intrepid.

---

### Post by dentaku65 on 2008-11-22
Freelrjd and Lars,
I do not have idea when the kde3 packages will be ready, I supposed soon and I think Madscientist159 is working hardly on it; please be patient... if you stay in Intrepid and if you have (too much) trouble to work in kde4 just switch into Gnome in the meantime since kde3 will be ready.

---

### Post by red_team316 on 2008-11-22
How does this affect the creation of an ISO? Will there be an official one compiled from the KDE3 repo or will I still have to create a non-official one? 

With it pointing to kde3, it will be much cleaner. I like it.

---

### Post by madscientist159 on 2008-11-22
> **freelsjd said:**
> :confused:The main problem I had with kde4 was that it does not have hiding panels as of intrepid.  This issue alone was enough to revert back to kde3.  Now am I going to have to revert back to Hardy ?  And for how long ?  Am I now going to give up Ubuntu (or kubuntu) altogether because of this issue.  This absolutely makes no sense to me at all !  You have a set of packages which are open source, and you force the guy to back down and not make them available to people that want them ?  

Now that I have blown a little steam, how can the average user help out ?  Can you at least tell us what the plan is ?

Yes.:)

I am currently porting kdebase to the -kde prefix.  While I am close, do not expect that set of packages uploaded to the PPA and to my apt.pearsoncomputing.net repository for a couple of days yet.  Once that group of packages is up, kdm and the base system will be available for use, but will not be very useful without the other packages for network, admin, etc.

I am currently placing the binaries in /usr/kde3, and modifying everything else to have a -kde3 suffix.  For example, /etc/init.d/kdm becomes /etc/init.d/kdm-kde3, but the executable is /usr/kde3/bin/kdm.  This should allow the system shared files to operate properly, providing the same tight integration with the rest of the system that Hardy and earlier always had.  The only downside to this is that it is taking even longer to get the work done.

Redteam,

No, I do not think there will not be an "official" ISO, so please work on it when the new packages are up. :)

I will post more when I have time.

---

### Post by madscientist159 on 2008-11-24
The first of many KDE3 packages are now up at [https://launchpad.net/~kb9vqf/+archive](https://launchpad.net/~kb9vqf/+archive)

Please note that this is [COLOR="Red"]**for developers only**[/COLOR] at the moment.

The KDE base components are up as of 11/24/08, and KDM3 is (mostly) operational.  There are a few glitches to work out, but this will allow others to start porting other KDE3 packages as well.

My to-do list, in order, is:
arts [provided by Intrepid]
libs [provided by Intrepid]
base [operational, alpha status]
graphics
artwork
multimedia
accessibility
games
admin
toys
utils
pim
sdk
addons
edu
network
webdev
others (kubuntu-desktop, etc.)

As you can see, I have a long way to go.  The good news is that kdebase is the largest and most complex group of packages (it has the most system "hooks"), so the others will go faster.

Alpha testers, wait for kdebase....~intrepid6 (uploading now), then have at it! :)  KDM will display an invalid theme warning, that will not go away until kubuntu-desktop-kde3 is available.  Just ignore it for now

Tim

---

### Post by dentaku65 on 2008-11-24
> **madscientist159 said:**
> The first of many KDE3 packages are now up at [https://launchpad.net/~kb9vqf/+archive](https://launchpad.net/~kb9vqf/+archive)

Please note that this is [COLOR="Red"]**for developers only**[/COLOR] at the moment.

The KDE base components are up as of 11/24/08, and KDM3 is (mostly) operational.  There are a few glitches to work out, but this will allow others to start porting other KDE3 packages as well.

My to-do list, in order, is:
arts [provided by Intrepid]
libs [provided by Intrepid]
base [operational, alpha status]
graphics
artwork
multimedia
accessibility
games
admin
toys
utils
pim
sdk
addons
edu
network
webdev
others (kubuntu-desktop, etc.)

As you can see, I have a long way to go.  The good news is that kdebase is the largest and most complex group of packages (it has the most system "hooks"), so the others will go faster.

Alpha testers, wait for kdebase....~intrepid6 (uploading now), then have at it! :)  KDM will display an invalid theme warning, that will not go away until kubuntu-desktop-kde3 is available.  Just ignore it for now

Tim

Hi Tim,
but what is the apt-get install <namepackage>?

Great!

---

### Post by dentaku65 on 2008-11-24
> **dentaku65 said:**
> Hi Tim,
but what is the apt-get install <namepackage>?

Great!

ops... I see now... kubuntu-desktop-kde3 I supposed :-)
I'm waiting for that...
Maybe can be useful for the users that did your repository before to do something like:
```
cp -R ~/.kde ~/.kde3
```
right before to do the install....

---

### Post by madscientist159 on 2008-11-24
> **dentaku65 said:**
> ops... I see now... kubuntu-desktop-kde3 I supposed :-)
I'm waiting for that...
Maybe can be useful for the users that did your repository before to do something like:
```
cp -R ~/.kde ~/.kde3
```
right before to do the install....

YES!:)  As of right now that is critical.

There are not enough packages compiled to actually *use* KDE3 yet, so I have not uploaded the metapackages--this for developers only at this point, and they should already know which packages to install ;)

I expect there to be many bugs, especially in kdebase, so please report them as you find them to [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net)  Any deviation whatsoever from the behaviour of KDE3 under Hardy should be considered a bug and filed.

---

### Post by inwo on 2008-11-24
Just to add to the Choir:  Madscientist, you are a hero!

---

### Post by blackbelt_jones on 2008-11-25
> **curuxz said:**
> not that I wish to make this thread into a flame, but I am so $%^&ed off with the Kubuntu team right now its unbelievable. 

What were they thinking retiring KDE 3.5 without asking anyone?!?!? Better still what the hell were they thinking when they decided that KDE 4 was ready?! 90% of the functionality of kde 3.5 is missing and almost 100% of the stability.

As a user of linux for 10 years this has to be the worst move by ANY dev team I have ever seen and now I have to waste my valuable time re-installing because valiant as your post is it simply leaves half my system broken.

Well, now it's the second worst move.  Just went to madscientist's kde3 repository for Intrepid

[http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/)
> 
I have been personally contacted by the Kubuntu developers and asked to take the repository offline. At this point, to avoid further problems, that is what I have done.

I've actually started using KDE 4.1... I'm into it now!  But this is incomprehensible to me.  I'm boycotting Kubuntu until someone gives me a good reason for what looks like an attempt to control how people use free software that for me smacks of Microsoft at it's worst.  I've already installed Opensuse 11.0.

On the plus side, KDE 4 is really shaping up.  I'm not sure it's destined to be all things to all people, but I like it a lot!  And I'm sure I hated it as much as anyone.

---

### Post by esdaniel on 2008-11-26
> **blackbelt_jones said:**
>  I'm boycotting Kubuntu until someone gives me a good reason for what looks like an attempt to control how people use free software that for me smacks of Microsoft at it's worst.

Baby and bath water come to mind.  

I also feel your 'pain' in being stuck with Hardy while the KDE3/4 thing resolves itself - it's great to see people like MadScientist take initiative and shows us the benefit of free software in being able to adjust this yourself providing you have or can gain the expertise.  

Running a stable and reliable repo system is what I believe is the crux of the issue, especially in terms of things like security updates and earlier in the thread explanation was given by Arby that there were not sufficient resources to do both - KDE team are keen to evolve their work and have made a decision to move resources to KDE4 - it's not sinister, opaque or underhand - it was a decision, a tough one which had to be made and time will tell if they got it right. 

Yet to go further, as you have in your remarks, and start making comparisons to Microsoft is not fair thus I felt compelled to share my feeling of your comment.  Yes, there are quite a few 'casualties' invovled, such as you and I, however I do not think it justifies us to be so harsh in our assessment of the KDE team and what they are able to provide today.

That's my 2c.

---

### Post by madscientist159 on 2008-11-27
To whoever left me a post on my profile (I cannot respond there because I "do not have enough posts" :(
You will not have to wait that much longer...take a look at [http://launchpad.net/~kb9vqf](http://launchpad.net/~kb9vqf) and go to my PPA.  There you can monitor my progress, and see that I have quite a few packages (1Gb worth!) up already.  I am over halfway done, and this is fully KDE4 compatible at the moment.:)

---

### Post by dentaku65 on 2008-11-28
> **madscientist159 said:**
> To whoever left me a post on my profile (I cannot respond there because I "do not have enough posts" :(
You will not have to wait that much longer...take a look at [http://launchpad.net/~kb9vqf](http://launchpad.net/~kb9vqf) and go to my PPA.  There you can monitor my progress, and see that I have quite a few packages (1Gb worth!) up already.  I am over halfway done, and this is fully KDE4 compatible at the moment.:)

Mad,
it is sufficient to install kdebase-kde3 to test it? And is the session name will be kde3?

---

### Post by madscientist159 on 2008-11-28
> **dentaku65 said:**
> Mad,
it is sufficient to install kdebase-kde3 to test it? And is the session name will be kde3?

Yes, the session name will be KDE3.:)

You need to install quite a few more packages than just that.  For starters, do this (after adding the PPA to your /etc/apt/sources.list file):
```
sudo apt-get install kdebase-kde3 kwin-kde3 kpersonalizer-kde3 ksplash-kde3 kicker-kde3 kcontrol-kde3 konqueror-kde3 ktip-kde3 klipper-kde3 kfind-kde3 kdeprint-kde3 kdebase-kio-plugins-kde3
```

This will give you the base KDE3 system.  **[COLOR="Red"]DO NOT[/COLOR]** install **anything** from my PPA if you have already installed packages from my old KDE3 repository on your system--I will be creating an upgrade script of some kind to handle the transition between the repositories.

There are several bugs that I am aware of and will be fixing:
1. When right-clicking on the Desktop, the "Create New" menu option is empty
2. The KDE3 control center icons are all messed up (but it is still quite usable)
3. KDM3 brings up an error saying that it can't parse a theme file--this will be fixed as soon as I publish the kubuntu-kde3-default-desktop package.
4. If you have KDE4 installed alongside KDE3, Plasma likes to launch the entire KDE4 desktop inside of your KDE3 session.  For some reason that I am still investigating, KDE4 puts a Plasma shortcut in the system autostart folder (/usr/share/autostart).  If you move plasma.desktop from that folder to a safe location elsewhere, the problem seems to be fixed, but I don't know if that breaks KDE4 yet.

---

### Post by red_team316 on 2008-11-28
> **madscientist159 said:**
> 
```
sudo apt-get install kdebase-kde3 kwin-kde3 kpersonalizer-kde3 ksplash-kde3 kicker-kde3 kcontrol-kde3 konqueror-kde3 ktip-kde3 klipper-kde3 kfind-kde3 kdeprint-kde3 kdebase-kio-plugins-kde3
```

This will give you the base KDE3 system.  **[COLOR="Red"]DO NOT[/COLOR]** install **anything** from my PPA if you have already installed packages from my old KDE3 repository on your system--I will be creating an upgrade script of some kind to handle the transition between the repositories.


Hehe thats awesome for me as I'm still running hardy and just chroot to the ISO :D I'll try to find some time this weekend to do some testing.

---

### Post by iX9 on 2008-12-02
Hi!
One question: For what hardware platform is *__lpia.deb ??
Thanx...

---

### Post by madscientist159 on 2008-12-02
iX9,

I had the same question when I first saw it.  It is "Low Power Intel x86".

All,

The repository is nearly complete, as you can probably see by the number of packages in the PPA.  Most of the bugs (including Plasma) have been fixed, and I am repairing the kubuntu-desktop package as I write this.

So, if any brave souls would like to try this new repository out, install the kubuntu-desktop-kde3 package under Intrepid with KDE4! :D  They coexist very well now.

There are some missing packages (such as Amarok) that will be uploaded in the next few days.  Compiz support is also well under way, and should be completed soon.

---

### Post by dentaku65 on 2008-12-03
> **madscientist159 said:**
> iX9,

I had the same question when I first saw it.  It is "Low Power Intel x86".

All,

The repository is nearly complete, as you can probably see by the number of packages in the PPA.  Most of the bugs (including Plasma) have been fixed, and I am repairing the kubuntu-desktop package as I write this.

So, if any brave souls would like to try this new repository out, install the kubuntu-desktop-kde3 package under Intrepid with KDE4! :D  They coexist very well now.

There are some missing packages (such as Amarok) that will be uploaded in the next few days.  Compiz support is also well under way, and should be completed soon.

Hi Tim,
is it included the script that you mentioned few posts ago?
I can try your new packages if so.
And, of course, starts a renewed HowTo for the KDE 3 into Intrepid if needed.

---

### Post by johndouberro on 2008-12-04
> **madscientist159 said:**
> iX9,
and I am repairing the kubuntu-desktop package as I write this.

So, if any brave souls would like to try this new repository out, install the kubuntu-desktop-kde3 package under Intrepid with KDE4! :D  They coexist very well now.


Hi. Good work. I tried kde3 with clean ubuntu 8.10 and it works! :) but some problems occured:
First, I tried to install all your repository, and synaptic reported dependency problems:

```

adept-kde3:
 Depends: adept-notifier-kde3 but it is not going to be installed
  Conflicts: adept  but 3.0~beta4ubuntu5 is to be installed

adept-notifier-kde3:
 Depends: adept-updater  but it is not installable

atlantik-kde3-dev:

kbabel-kde3-dev:

kdebase-kde3-dev:

kdebase-runtime-data-common-kde3:
  Conflicts: kdebase-runtime-data-common  but 4:4.1.2-0ubuntu6 is to be installed

kdegraphics-kde3:
 Depends: libkscan1 (>=4:3.5.10-0ubuntu1~intrepid3) but it is not installable

kdegraphics-kde3-dev:

kdemultimedia-kde3-dev:

kdepim-kde3-dev:

kdesdk-kde3:
 Depends: kdesdk-scripts-kde3 but it is not going to be installed

kdesdk-kde3-dbg:
 Depends: kbabel-kde3-dev but it is not going to be installed

kdesdk-scripts-kde3:
  Conflicts: kdesdk-scripts  but 4:4.1.2-0ubuntu1.1 is to be installed

kio-apt-kde3:
 Depends: kdelibs4c2a but it is not going to be installed

ksystemlog-kde3:
 Depends: kdelibs4c2a but it is not going to be installed

kubuntu-desktop-kde3:
 Depends: kde-style-qtcurve-kde3  but it is not installable
 Depends: kio-apt-kde3 but it is not going to be installed
 Depends: kio-locate-kde3  but it is not installable
 Depends: ksystemlog-kde3 but it is not going to be installed
 Recommends: kde-guidance-kde3  but it is not installable
 Recommends: adept-kde3 but it is not going to be installed
 Recommends: digikamdesktop-effects-kde-kde3  but it is not installable
 Recommends: gdebi-kde-kde3  but it is not installable
 Recommends: gtk-qt-engine-kde3  but it is not installable
 Recommends: gwenview but it is not going to be installed
 Recommends: k3b-kde3  but it is not installable
 Recommends: kaffeine-kde3  but it is not installable
 Recommends: katapult-kde3  but it is not installable
 Recommends: kde-guidance-powermanager-kde3  but it is not installable
 Recommends: kdebluetooth-kde3  but it is not installable
 Recommends: keep-kde3  but it is not installable
 Recommends: kio-umountwrapper-kde3  but it is not installable
 Recommends: kipi-plugins-kde3  but it is not installable
 Recommends: kmplayer-konq-plugins-kde3  but it is not installable
 Recommends: konversation-kde3  but it is not installable
 Recommends: ktorrent-kde3  but it is not installable
 Recommends: kubuntu-docs-kde3  but it is not installable
 Recommends: kubuntu-konqueror-shortcuts-kde3  but it is not installable
 Recommends: kvkbd-kde3  but it is not installable
 Recommends: networkstatus  but it is not installable
 Recommends: openoffice.org-kde-kde3  but it is not installable
 Recommends: skim but it is not going to be installed
 Recommends: strigi-applet  but it is not installable
 Recommends: system-config-printer-kde-kde3  but it is not installable

```

I don't know how severe this problems are, I tried only basic desktop and it worked (thanks again). But I don't know what to do if I would like to install e.g. K3B, kaffeine...

Also, I tried to install KDE3 at my working computer with KDE4, and it tried to uninstall some existing software (like amarok etc.) and install it from your package. If you are interested, I can post these messages.

---

### Post by madscientist159 on 2008-12-04
> **johndouberro said:**
> Hi. Good work. I tried kde3 with clean ubuntu 8.10 and it works! :) but some problems occured:
First, I tried to install all your repository, and synaptic reported dependency problems:

```

adept-kde3:
 Depends: adept-notifier-kde3 but it is not going to be installed
  Conflicts: adept  but 3.0~beta4ubuntu5 is to be installed

adept-notifier-kde3:
 Depends: adept-updater  but it is not installable

atlantik-kde3-dev:

kbabel-kde3-dev:

kdebase-kde3-dev:

kdebase-runtime-data-common-kde3:
  Conflicts: kdebase-runtime-data-common  but 4:4.1.2-0ubuntu6 is to be installed

kdegraphics-kde3:
 Depends: libkscan1 (>=4:3.5.10-0ubuntu1~intrepid3) but it is not installable

kdegraphics-kde3-dev:

kdemultimedia-kde3-dev:

kdepim-kde3-dev:

kdesdk-kde3:
 Depends: kdesdk-scripts-kde3 but it is not going to be installed

kdesdk-kde3-dbg:
 Depends: kbabel-kde3-dev but it is not going to be installed

kdesdk-scripts-kde3:
  Conflicts: kdesdk-scripts  but 4:4.1.2-0ubuntu1.1 is to be installed

kio-apt-kde3:
 Depends: kdelibs4c2a but it is not going to be installed

ksystemlog-kde3:
 Depends: kdelibs4c2a but it is not going to be installed

kubuntu-desktop-kde3:
 Depends: kde-style-qtcurve-kde3  but it is not installable
 Depends: kio-apt-kde3 but it is not going to be installed
 Depends: kio-locate-kde3  but it is not installable
 Depends: ksystemlog-kde3 but it is not going to be installed
 Recommends: kde-guidance-kde3  but it is not installable
 Recommends: adept-kde3 but it is not going to be installed
 Recommends: digikamdesktop-effects-kde-kde3  but it is not installable
 Recommends: gdebi-kde-kde3  but it is not installable
 Recommends: gtk-qt-engine-kde3  but it is not installable
 Recommends: gwenview but it is not going to be installed
 Recommends: k3b-kde3  but it is not installable
 Recommends: kaffeine-kde3  but it is not installable
 Recommends: katapult-kde3  but it is not installable
 Recommends: kde-guidance-powermanager-kde3  but it is not installable
 Recommends: kdebluetooth-kde3  but it is not installable
 Recommends: keep-kde3  but it is not installable
 Recommends: kio-umountwrapper-kde3  but it is not installable
 Recommends: kipi-plugins-kde3  but it is not installable
 Recommends: kmplayer-konq-plugins-kde3  but it is not installable
 Recommends: konversation-kde3  but it is not installable
 Recommends: ktorrent-kde3  but it is not installable
 Recommends: kubuntu-docs-kde3  but it is not installable
 Recommends: kubuntu-konqueror-shortcuts-kde3  but it is not installable
 Recommends: kvkbd-kde3  but it is not installable
 Recommends: networkstatus  but it is not installable
 Recommends: openoffice.org-kde-kde3  but it is not installable
 Recommends: skim but it is not going to be installed
 Recommends: strigi-applet  but it is not installable
 Recommends: system-config-printer-kde-kde3  but it is not installable

```

I don't know how severe this problems are, I tried only basic desktop and it worked (thanks again). But I don't know what to do if I would like to install e.g. K3B, kaffeine...

Also, I tried to install KDE3 at my working computer with KDE4, and it tried to uninstall some existing software (like amarok etc.) and install it from your package. If you are interested, I can post these messages.

Yes, that is to be expected.  I had to completely replace the Intrepid KDE3 subsystem, so any package that depends on KDE3 has to be installed from my repository.  This shouldn't be too severe of a problem; if I am missing something just yell at me until I upload it. ;)

I just finished fixing and uploading the last few kubuntu-desktop-kde3 dependencies, so you should now be able to install that package.

Please let me know what other packages are still needed.

I am still working on the "epoch 7 to -kde3" package transition issue--for now, you can add the new repository to your /etc/apt/sources.list file, remove the old one from that file, drop to a terminal and:
sudo apt-get update
sudo apt-get remove kdelibs4c2a gdebi gdebi-core kdebase-data
sudo apt-get install kubuntu-desktop-kde3
Then reinstall whatever KDE3 programs you are now missing.

[B][COLOR="Blue"]Dentaku,

Can you please edit that first post to reflect the fact that the new repository is now online and ready for use?

Thanks![/COLOR][/B]

Tim

---

### Post by johndouberro on 2008-12-05
You make changes every hour :)
Currently, synaptic announced at clean ubuntu:
```

adept-kde3:
 Depends: adept-notifier-kde3 but it is not going to be installed
  Conflicts: adept  but 3.0~beta4ubuntu5 is to be installed

adept-notifier-kde3:
 Depends: adept-updater  but it is not installable

atlantik-kde3-dev:

kaffeine-gstreamer-kde3:
 Depends: kdelibs4c2a but it is not going to be installed
 Depends: kaffeine-kde3 but it is not going to be installed

kaffeine-kde3:
 Depends: kdelibs4c2a but it is not going to be installed
 Recommends: gdebi-kde-kde3  but it is not installable

kaffeine-kde3-dbg:
 Depends: kaffeine-kde3 but it is not going to be installed
 Recommends: gdebi-kde-kde3  but it is not installable

kbabel-kde3-dev:

kdebase-kde3-dev:

kdebase-runtime-data-common-kde3:
  Conflicts: kdebase-runtime-data-common  but 4:4.1.2-0ubuntu6 is to be installed

kdegraphics-kde3:
 Depends: libkscan1 (>=4:3.5.10-0ubuntu1~intrepid3) but it is not installable

kdegraphics-kde3-dev:

kdemultimedia-kde3-dev:

kdepim-kde3-dev:

kdesdk-kde3:
 Depends: kdesdk-scripts-kde3 but it is not going to be installed

kdesdk-kde3-dbg:
 Depends: kbabel-kde3-dev but it is not going to be installed

kdesdk-scripts-kde3:
  Conflicts: kdesdk-scripts  but 4:4.1.2-0ubuntu1.1 is to be installed


```

mostly -dbg and -dev unimportant stuff (no developement to KDE3 as I know), but Kaffeine will be missing...
Also, synaptic tried to uninstall 

compiz, compiz-gnome, compizconfig-backend-gconf and libcompizconfig0

Not necessary for me, but someone could use both gnome and kde (hotseat).
In the evening, I will try KDE4 and KDE3 together.

---

### Post by johndouberro on 2008-12-05
Sorry, in the last post, I didn't tried to uninstall gdebi and gdebi-core - so I tried now, but whole ubuntu-desktop depeds on them :( is it correct? (kdelibs4c2a  and kdebase-data was not installed in the system).

Hmm, I've got clean ubuntu, installed kubuntu-desktop, tried to install kubuntu-dekstop-kde3, and the system tried to remove kubuntu-desktop (because of e.g. konsole, amarok etc.).
So both desktops, Kde3 and Kde4 can not be together at one machine?

---

### Post by madscientist159 on 2008-12-05
> **johndouberro said:**
> Sorry, in the last post, I didn't tried to uninstall gdebi and gdebi-core - so I tried now, but whole ubuntu-desktop depeds on them :( is it correct? (kdelibs4c2a  and kdebase-data was not installed in the system).

Hmm, I've got clean ubuntu, installed kubuntu-desktop, tried to install kubuntu-dekstop-kde3, and the system tried to remove kubuntu-desktop (because of e.g. konsole, amarok etc.).
So both desktops, Kde3 and Kde4 can not be together at one machine?

kubuntu-desktop installs the KDE4 versions of several programs, such as konsole.  The way I have this set up, the user selects which version of those programs they want (KDE3 or KDE4), but you can have both desktop environments installed side by side.  If I were to try to separate out the application data files from KDE4 would become an absolute nightmare to both compile and use KDE3 (which version of konsole does the system launch when I type 'konsole' into the run dialog?)

I personally don't see any harm in this; you can mix-n-match KDE3 and KDE4 apps until you find a configuration you like, and the KDE4 desktop is quite usable and untouched. :)

Tim

---

### Post by maanus on 2008-12-05
Tim, are you an angel? It seems to me you are.

I just bought a DVB dongle, and hardy is not able to play MPEG4 stream (the one form Estonia's TV broadcasting) from it. How to solve the problem "to not leave KDE3 and to use intrepid's capability to play MPEG4 stream"? And there comes the angel and solves it for thousands!

---

### Post by johndouberro on 2008-12-05
> **madscientist159 said:**
> kubuntu-desktop installs the KDE4 versions of several programs, such as konsole.  The way I have this set up, the user selects which version of those programs they want (KDE3 or KDE4), but you can have both desktop environments installed side by side.  If I were to try to separate out the application data files from KDE4 would become an absolute nightmare to both compile and use KDE3 (which version of konsole does the system launch when I type 'konsole' into the run dialog?)

I personally don't see any harm in this; you can mix-n-match KDE3 and KDE4 apps until you find a configuration you like, and the KDE4 desktop is quite usable and untouched. :)

Tim

I am a bit slow for this - How can I install both KDE3 and KDE4 desktop? When I try 
sudo apt-get install kubuntu-desktop-kde3
the system tries to uninstall all kde4 related. I am not insisting on KDE4, but I fear possible problems with kde3 and both KDEs will be missing on my working computer. Maybe I will wait and try it at some virtual machine.

---

### Post by madscientist159 on 2008-12-05
> **johndouberro said:**
> I am a bit slow for this - How can I install both KDE3 and KDE4 desktop? When I try 
sudo apt-get install kubuntu-desktop-kde3
the system tries to uninstall all kde4 related. I am not insisting on KDE4, but I fear possible problems with kde3 and both KDEs will be missing on my working computer. Maybe I will wait and try it at some virtual machine.

By all means, try it in a virtual machine first.  This is always a good practice when dealing with software you have not tried before. ;)

It will remove kubuntu-desktop and some KDE4 apps (in order to replace them with KDE3 apps), but **it will not remove the KDE4 window manager/plasma/desktop etc.**  kubuntu-desktop is just a metapackage that allows easy installation of the entire KDE4 system, including some KDE4 apps, and KDE4 will not be damaged if you remove it.

Hope this helps some!

---

### Post by dentaku65 on 2008-12-05
Post [#1]("http://ubuntuforums.org/showthread.php?t=963695") updated! :p

---

### Post by sandyd on 2008-12-05
Hi. When i try running
sudo apt-get install kubuntu-desktop-kde3

i get an error code
The following packages have unmet dependencies:
  kcontrol-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                 Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kdm-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
            Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kicker-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
               Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kpersonalizer-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                      Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed

When i try to fix it, it says theirs overlapping files (even though the files do not exist). It gives

Unpacking kdebase-data-kde3 (from .../kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid1_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/kde-information.menu', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by madscientist159 on 2008-12-05
> **carlee said:**
> Hi. When i try running
sudo apt-get install kubuntu-desktop-kde3

i get an error code
The following packages have unmet dependencies:
  kcontrol-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                 Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kdm-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
            Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kicker-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
               Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kpersonalizer-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                      Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed

When i try to fix it, it says theirs overlapping files (even though the files do not exist). It gives

Unpacking kdebase-data-kde3 (from .../kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid1_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/kde-information.menu', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Did you have my original KDE3 repository installed at any point?

---

### Post by sandyd on 2008-12-05
Nope
This was done on a completely brand new Ubuntu Intrepid Ibex 8.10
the only thing that got installed was envyng

---

### Post by ramaswamyps on 2008-12-05
you can try removing both kde s and start from installing kde3 and then kde4
you will have less problems.
eventhough complete kde3 and kde4 are not possible to run in ubuntu-8.10.
so i had to go back to 8.04 and i have kde3 full and kde-4.1.2 almost full.

---

### Post by madscientist159 on 2008-12-05
> **carlee said:**
> Nope
This was done on a completely brand new Ubuntu Intrepid Ibex 8.10
the only thing that got installed was envyng

Kubuntu or Ubuntu?

I will load this up in a new VM and see if I can replicate and fix the issue.

---

### Post by sandyd on 2008-12-05
> **ramaswamyps said:**
> you can try removing both kde s and start from installing kde3 and then kde4
you will have less problems.
eventhough complete kde3 and kde4 are not possible to run in ubuntu-8.10.
so i had to go back to 8.04 and i have kde3 full and kde-4.1.2 almost full.

its a new install, so only kde 3 installation was attempted

---

### Post by sandyd on 2008-12-05
> **madscientist159 said:**
> Kubuntu or Ubuntu?

I will load this up in a new VM and see if I can replicate and fix the issue.

its on a ubuntu install

---

### Post by sandyd on 2008-12-05
apparently, somehow, kde 3 depends on kde 4 packages and requires for them to be installed. When i try removing kdebase-runtime-data, some of the kde3 apps are required to be removed as well. weird...

EDIT:
In fact, the entire kubuntu-desktop-kde3 package depends on it

---

### Post by madscientist159 on 2008-12-05
> **carlee said:**
> apparently, somehow, kde 3 depends on kde 4 packages and requires for them to be installed. When i try removing kdebase-runtime-data, some of the kde3 apps are required to be removed as well. weird...

EDIT:
In fact, the entire kubuntu-desktop-kde3 package depends on it

Thanks for the info; I will look into the problem.

KDE3 and KDE4 do share some application data, but I was hoping that the KDE3 apps would not end up dependent on the KDE4 runtime data package.

I do know that this works very well if you start with a Kubuntu Intrepid (KDE4) install... ;)

---

### Post by beastrace91 on 2008-12-06
Everything was going smoothly I just added the gpg key and then upon running sudo apt-get update I get this error output: [quote="My Terminal"]jeff@linuxKDE:~$ sudo apt-key add public.gpg
OK
jeff@linuxKDE:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid Release.gpg
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release           
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Err [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Err [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Sources
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
W: Failed to fetch [http://apt.pearsoncomputing.net/dists/intrepid/main/binary-i386/Packages.gz](http://apt.pearsoncomputing.net/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://apt.pearsoncomputing.net/dists/intrepid/main/source/Sources.gz](http://apt.pearsoncomputing.net/dists/intrepid/main/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
[/quote]

Did I enter something wrong or are the files missing from the repository?...

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Everything was going smoothly I just added the gpg key and then upon running sudo apt-get update I get this error output: 

Did I enter something wrong or are the files missing from the repository?...

~Jeff

You're using the old repository lines in your /etc/apt/sources.list file--jstu grab the new lines from [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net), replace the old ones, and run sudo apt-get update :)

---

### Post by iX9 on 2008-12-06
Hi, madscientist159!:p
What happens, if appears some updated kde3-related package (for example in official hardy repo)? Must You manually convert it to this repository, or there is an automated script, keeping as updated?:D

---

### Post by madscientist159 on 2008-12-06
> **iX9 said:**
> Hi, madscientist159!:p
What happens, if appears some updated kde3-related package (for example in official hardy repo)? Must You manually convert it to this repository, or there is an automated script, keeping as updated?:D

Copy & paste the new patch file(s) from official to mine and recompile.  Pretty simple. :p

But then again look at the last modified dates for these packages...most of them have not been touched by the Kubuntu devs since September 2008, and many are even older than that.  It's one of the benefits of having a mature desktop environment. ;)

---

### Post by madscientist159 on 2008-12-06
Carlee,

Try this command (all one line):
sudo apt-get install kubuntu-desktop-kde3 ark-kde3 ksystemlog-kde3 kmix-kde3 konq-plugins-kde3 ksnapshot-kde3 konqueror-kde3

apt-get seems to need a little "push" to overwrite the entire existing KDE3 system.

---

### Post by iX9 on 2008-12-06
I will try this:

- Install command line system only by Kubuntu 8.10 Alternate CD.
- Add KDE3 repo to the sources list.
- Apt-get update.
- Apt-get install kubuntu-desktop-kde3.

If this success, it should result in a clear pure KDE3 system...:D


Another question: ;)
What metapackage install to get full KDE3 with all packages from new repo,  and,
What metapackage install to get system with the same apps as is default after installation Hardy Desktop CD?

---

### Post by dentaku65 on 2008-12-06
> **ramaswamyps said:**
> you can try removing both kde s and start from installing kde3 and then kde4
you will have less problems.
eventhough complete kde3 and kde4 are not possible to run in ubuntu-8.10.
so i had to go back to 8.04 and i have kde3 full and kde-4.1.2 almost full.

I suggest the opposite indeed.
First install KDE4 (kubuntu-desktop)
then install KDE3 (kubuntu-dektop-kde3)

I discovered on my own machine that having KDE3 installed is it not possible to install KDE4 official Intrepid repository; no problems with KDE4 from Nightly.

Mad, some hints?

---

### Post by beastrace91 on 2008-12-06
Ok so updating to the correct repositories worked like a charm how ever after running sudo apt-get install kubuntu-desktop-kde3 I get this message after it has downloaded everything and begin unpacking: > Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                                                                                                         [ OK ] 
Processing triggers for ufw ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid1_all.deb
 /var/cache/apt/archives/kubuntu-default-settings-kde3_1%3a8.10-20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Is this something I should worry about or is it a normal error message?

~Jeff

---

### Post by bobe84 on 2008-12-06
Ok, i tried new repos from launchpad on fresh Ubuntu 8.10 install, so far there is problem with right click/create new; no menu at all appears

---

### Post by bobe84 on 2008-12-06
I see now that madscientist said that kubuntu 8.10 works nice with those repos, so i will try his suggestion...

---

### Post by sandyd on 2008-12-06
hmm..... says that all packages are the newest version
the commands didn't work

---

### Post by sandyd on 2008-12-06
> **beastrace91 said:**
> Ok so updating to the correct repositories worked like a charm how ever after running sudo apt-get install kubuntu-desktop-kde3 I get this message after it has downloaded everything and begin unpacking: 

Is this something I should worry about or is it a normal error message?

~Jeff
i had the same problem.... look at the verry bottom of the page before this one and see if that fixes it

---

### Post by sandyd on 2008-12-06
hmm.... i found a little trick
it seems that kde 3 hates the kde 4 stuff... so why not install kde 3 stuff first so it can't complain?

I tried it and amazingly, it worked!

this is what i did.....

sudo apt-get remove kubuntu-desktop-kde3 kubuntu-artwork-usplash kdebase-runtime-data kdebase-kde3-data kdebase-workspace-data-kde3 kdebase-kde4 kdebase-kde3

sudo apt-get autoremove
sudo apt-get install kubuntu-default-settings-kde3 kdebase-data-kde3
sudo apt-get install kubuntu-desktop-kde3
sudo apt-get install kdebase-runtime-data kdebase-kde3
sudo apt-get remove kubuntu-desktop-kde3

oh, and kubuntu-artwork-usplash can't be installed so you might get broken packages,

if it doesn't work, try manually removing the kde packages, and i mean ALL of them before running this, because there might be other conflicting packages

---

### Post by sandyd on 2008-12-06
i got a question.... when i right click on the kde 3.5 desktop then go to "Create New" it only gives me an option of making a link to a device. How can i add the appropriate stuff there? like new text file, document, create new link, etc.

---

### Post by madscientist159 on 2008-12-06
> **carlee said:**
> i got a question.... when i right click on the kde 3.5 desktop then go to "Create New" it only gives me an option of making a link to a device. How can i add the appropriate stuff there? like new text file, document, create new link, etc.

I am working on this--KDE3 as of right now needs some KDE4 shared data, but I am putting together a package that will divert the KDE4 shared data elsewhere and install KDE3 shared data instead.  Look for it later on today or tomorrow.

The kubuntu-artwork-usplash bug should also be fixed now.

Tim

---

### Post by __david on 2008-12-06
Hi madscientist159,

first of all, I'd like to thank you for your efforts. Great!

Your bugzilla installation doesn't work at the moment, so I'll post here:

[LIST=1]
[*] Bug: kaffeine-kde3 is compiled against kdelibs4c2a, not against kdelibs4c2a-kde3. Both versions are conflicting and cannot be installed at the same time. At least on my installation.
[*] Feature request: Will you provide i18n-packages?
[*] Last thing: When using kde3-apps from your repo in Gnome, they use ~/.kde as conf directory rather than ~/.kde3. Is it possible to prevent that behaviour?
[/LIST]

Thanks again!

David

---

### Post by beastrace91 on 2008-12-06
Ok so running this:

sudo apt-get install kubuntu-desktop-kde3 ark-kde3 ksystemlog-kde3 kmix-kde3 konq-plugins-kde3 ksnapshot-kde3 konqueror-kde3

Gets me this:

[quote="My Terminal"]jeff@linuxKDE:~$ sudo apt-get install kubuntu-desktop-kde3 ark-kde3 ksystemlog-kde3 kmix-kde3 konq-plugins-kde3 ksnapshot-kde3 konqueror-kde3
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kubuntu-desktop-kde3 is already the newest version.
ark-kde3 is already the newest version.
ksystemlog-kde3 is already the newest version.
kmix-kde3 is already the newest version.
konq-plugins-kde3 is already the newest version.
ksnapshot-kde3 is already the newest version.
konqueror-kde3 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kcontrol-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                 Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kdm-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
            Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kicker-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
               Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kpersonalizer-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                      Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/quote]

Should I use -f to force it? (Will this work?)

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Ok so running this:

sudo apt-get install kubuntu-desktop-kde3 ark-kde3 ksystemlog-kde3 kmix-kde3 konq-plugins-kde3 ksnapshot-kde3 konqueror-kde3

Gets me this:



Should I use -f to force it? (Will this work?)

~Jeff

Yes, force it.  Something interrupted the installation of all the kde3 packages and left your system missing quite a few important packages.  apt-get -f will try to download and install any missing dependencies you might have.

---

### Post by madscientist159 on 2008-12-06
> **__david said:**
> Hi madscientist159,

first of all, I'd like to thank you for your efforts. Great!

Your bugzilla installation doesn't work at the moment, so I'll post here:

[LIST=1]
[*] Bug: kaffeine-kde3 is compiled against kdelibs4c2a, not against kdelibs4c2a-kde3. Both versions are conflicting and cannot be installed at the same time. At least on my installation.
[*] Feature request: Will you provide i18n-packages?
[*] Last thing: When using kde3-apps from your repo in Gnome, they use ~/.kde as conf directory rather than ~/.kde3. Is it possible to prevent that behaviour?
[/LIST]

Thanks again!

David

David,

1. I'll look in to the kaffeine problem--maybe I goofed and compiled it against kdelibs4c2a.
2. Not sure.  Those are quite nasty due to the sheer number of them--I'll ask the Kubuntu devs for advice on how to handle them
3. Yes.  Before you run KDE applications, open a terminal and run ```
export KDEHOME=~/.kde3
```  You may want to add this to a login or autorun on login script somewhere--I am not familiar with Gnome, so I can't tell you where.:)

---

### Post by beastrace91 on 2008-12-06
Hey just wanted to say I have KDE3 up and running! Thanks guys, I'll you know if I run into any other issues.

~Jeff

---

### Post by beastrace91 on 2008-12-06
Hey upon running:

sudo apt-get install kate (This is the KDE text editor)

I get this:

> Removing `diversion of /usr/share/templates/Directory.desktop to /usr/share/templates.kde4/Directory.desktop by kdebase-runtime-data-common-kde3'
dpkg-divert: error checking `/usr/share/templates/Directory.desktop': No such file or directory
dpkg: error processing kdebase-runtime-data-common-kde3 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:

Any ideas how I can get this working? I can use gedit for now but I prefer Kate

~Jeff

EDIT: When I try to apt-get install wine this happens as well, how ever when I installed envyng-qt it worked fine.

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Hey upon running:

sudo apt-get install kate (This is the KDE text editor)

I get this:



Any ideas how I can get this working? I can use gedit for now but I prefer Kate

~Jeff

EDIT: When I try to apt-get install wine this happens as well, how ever when I installed envyng-qt it worked fine.

Tack a -kde3 suffix onto any KDE3 package you want to install.  For example, apt-get install kate becomes apt-get install kate-kde3.

Also, kaffeine-kde3 and bugzilla are now fixed.

---

### Post by beastrace91 on 2008-12-06
Running sudo apt-get install kate-kde3 yields the following:

[quote="My Terminal"]Removing `diversion of /usr/share/templates/Directory.desktop to /usr/share/templates.kde4/Directory.desktop by kdebase-runtime-data-common-kde3'
dpkg-divert: error checking `/usr/share/templates/Directory.desktop': No such file or directory
dpkg: error processing kdebase-runtime-data-common-kde3 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kdebase-runtime-data-common-kde3
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/quote]

Also just as an FYI before all these errors there are a whole ton of these errors: [quote="My Terminal"]No diversion `any diversion of /usr/share/icons/hicolor/64x64/apps/knetattach.png', none removed
No diversion `any diversion of /usr/share/icons/hicolor/128x128/apps/knetattach.png', none removed
No diversion `any diversion of /usr/share/icons/hicolor/scalable/apps/knetattach.svgz', none removed
No diversion `any diversion of /usr/share/autostart/khotkeys.desktop', none removed
No diversion `any diversion of /usr/share/icons/hicolor/16x16/apps/khotkeys.png', none removed
No diversion `any diversion of /usr/share/icons/hicolor/32x32/apps/khotkeys.png', none removed
[/quote]

Hope that helps resolve what ever the issue may be! 

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Running sudo apt-get install kate-kde3 yields the following:



Also just as an FYI before all these errors there are a whole ton of these errors: 

Hope that helps resolve what ever the issue may be! 

~Jeff

I'm trying to figure out why your system wants to remove kdebase-runtime-data-common-kde3.  Can you post your package list?  Here is a command to do that:
```
dpkg -l > packagelist && gzip packagelist
```
then attach packagelist.gz to your post.

---

### Post by beastrace91 on 2008-12-06
There you go hope that helps and thanks for the quick responses :)

Also if you need to know this was installed on a Ubuntu 8.10 fresh install the only apps I have added are Eric's IDE for Python and envyng-qt

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> There you go hope that helps and thanks for the quick responses :)

Also if you need to know this was installed on a Ubuntu 8.10 fresh install the only apps I have added are Eric's IDE for Python and envyng-qt

~Jeff

Yes, it did help.  For some reason you are missing a bunch of KDE3 core packages.  At the very least you need to ```
sudo apt-get install ksmserver-kde3
``` before trying to install any more KDE3 apps, preferably you would do a ```
sudo apt-get install kubuntu-desktop-kde3
``` instead. ;)

If the previous errors get in your way, just do a ```
sudo dpkg -r --force-all kdebase-runtime-data-common-kde3
```.  It looks like I didn't write the kdebase-runtime-data-common-kde3 removal script well enough to handle a graceful removal of **all** KDE shared runtime data (KDE3 and KDE4)--I need to fix that.

Hope this helps some!

---

### Post by beastrace91 on 2008-12-06
Alas... another wall.

Upon running sudo apt-get install kubuntu-desktop-kde3 I get this mess:

[quote="My Terminal"]jeff@linuxKDE:~$ sudo apt-get install kubuntu-desktop-kde3
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop-kde3: Depends: ksmserver-kde3 but it is not going to be installed
                        Recommends: kde-guidance-kde3 but it is not installable
                        Recommends: adept-kde3 but it is not going to be installed
                        Recommends: digikamdesktop-effects-kde-kde3 but it is not installable
                        Recommends: gdebi-kde-kde3 but it is not installable
                        Recommends: kaffeine-kde3 but it is not going to be installed
                        Recommends: katapult-kde3 but it is not installable
                        Recommends: kde-guidance-powermanager-kde3 but it is not installable
                        Recommends: kdebluetooth-kde3 but it is not installable
                        Recommends: keep-kde3 but it is not installable
                        Recommends: kio-umountwrapper-kde3 but it is not installable
                        Recommends: kipi-plugins-kde3 but it is not installable
                        Recommends: kmplayer-konq-plugins-kde3 but it is not installable
                        Recommends: konversation-kde3 but it is not installable
                        Recommends: ktorrent-kde3 but it is not installable
                        Recommends: kubuntu-docs-kde3 but it is not installable
                        Recommends: kubuntu-konqueror-shortcuts-kde3 but it is not installable
                        Recommends: kvkbd-kde3 but it is not installable
                        Recommends: networkstatus but it is not installable
                        Recommends: openoffice.org-kde-kde3 but it is not installable
                        Recommends: skim but it is not going to be installed
                        Recommends: strigi-applet but it is not installable
                        Recommends: system-config-printer-kde-kde3 but it is not installable
E: Broken packages
[/quote]

:( Any ideas?

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Alas... another wall.

Upon running sudo apt-get install kubuntu-desktop-kde3 I get this mess:



:( Any ideas?

~Jeff

```
sudo apt-get install kubuntu-desktop-kde3 ksmserver-kde3
```

apt-get just really has a hard time with this for some reason. :(

---

### Post by beastrace91 on 2008-12-06
Swing and a miss...

That last command gets me:

[quote="My Terminal"]jeff@linuxKDE:~$ sudo apt-get install kubuntu-desktop-kde3 ksmserver-kde3
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ksmserver-kde3: Depends: kdebase-runtime-data-common-kde3 but it is not going to be installed
E: Broken packages
[/quote]

Ideas?

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Swing and a miss...

That last command gets me:



Ideas?

~Jeff

I'm just as puzzled as you are on this...try this command
```
sudo apt-get install kubuntu-desktop-kde3 ksmserver-kde3 kdebase-runtime-data-common-kde3
```

You can probably see what I'm doing--just take the output of the previous apt-get run, and where it says "Depends: <packagename> but it is not going to be installed", take the package name and tack it onto the end of the prior apt-get command.

I'm setting up a virtual machine with straight Ubuntu Intrepid on it to see if I can make this process any easier.

BTW have you run a sudo apt-get update recently?  You might be running on old package lists which would explain a lot.

---

### Post by beastrace91 on 2008-12-06
I am fully update to date (as far as runing apt-get update/upgrade goes) That last command got it going though... it is downloading now. Will let you know what happens when it finishes, thanks for all of your help thus far.

~Jeff

---

### Post by beastrace91 on 2008-12-06
Ok here is the error it finished with

[quote="My Terminal"]jeff@linuxKDE:~$ sudo apt-get install kubuntu-desktop-kde3 ksmserver-kde3 kdebase-runtime-data-common-kde3
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdebase-runtime-data-common-kde3 is already the newest version.
The following extra packages will be installed:
  kate-kde3 kdebase-kde3 kubuntu-default-settings-kde3
Suggested packages:
  kate-plugins-kde3 kdebase-doc-html
Recommended packages:
  kdebase-runtime-data-common-kde3 kde-guidance-kde3 adept-kde3 digikamdesktop-effects-kde-kde3 gdebi-kde-kde3 kaffeine-kde3 katapult-kde3
  kde-guidance-powermanager-kde3 kdebluetooth-kde3 keep-kde3 kio-umountwrapper-kde3 kipi-plugins-kde3 kmplayer-konq-plugins-kde3 konversation-kde3
  ktorrent-kde3 kubuntu-docs-kde3 kubuntu-konqueror-shortcuts-kde3 kvkbd-kde3 networkstatus openoffice.org-kde-kde3 skim strigi-applet
  system-config-printer-kde-kde3
The following packages will be REMOVED:
  adept
The following NEW packages will be installed:
  kate-kde3 kdebase-kde3 ksmserver-kde3 kubuntu-default-settings-kde3 kubuntu-desktop-kde3
0 upgraded, 5 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 78.6MB/80.1MB of archives.
After this operation, 86.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  kate-kde3 ksmserver-kde3 kdebase-kde3 kdebase-runtime-data-common-kde3 kubuntu-default-settings-kde3 kubuntu-desktop-kde3
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main kubuntu-default-settings-kde3 1:8.12-2 [78.6MB]
Fetched 78.6MB in 8min47s (149kB/s)                                                                                                                        
Selecting previously deselected package kate-kde3.
(Reading database ... 147948 files and directories currently installed.)
Unpacking kate-kde3 (from .../kate-kde3_4%3a3.5.10-0ubuntu3~intrepid2_i386.deb) ...
Selecting previously deselected package ksmserver-kde3.
Unpacking ksmserver-kde3 (from .../ksmserver-kde3_4%3a3.5.10-0ubuntu3~intrepid2_i386.deb) ...
Adding `local diversion of /usr/share/autostart/plasma.desktop to /usr/share/autostart.bkp/plasma.desktop'
Selecting previously deselected package kdebase-kde3.
Unpacking kdebase-kde3 (from .../kdebase-kde3_4%3a3.5.10-0ubuntu3~intrepid2_all.deb) ...
Selecting previously deselected package kdebase-runtime-data-common-kde3.
Preparing to replace kdebase-runtime-data-common-kde3 4:3.5.10-0ubuntu3~intrepid2 (using .../kdebase-runtime-data-common-kde3_4%3a3.5.10-0ubuntu3~intrepid2_all.deb) ...
Unpacking replacement kdebase-runtime-data-common-kde3 ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data-common-kde3_4%3a3.5.10-0ubuntu3~intrepid2_all.deb (--unpack):
 trying to overwrite `/usr/share/desktop-directories/kde-utilities-file.directory', which is also in package kdebase-runtime-data-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-runtime-data-common-kde3_4%3a3.5.10-0ubuntu3~intrepid2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/quote]

What next boss?

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Ok here is the error it finished with



What next boss?

~Jeff

```
sudo dpkg -r --force-all kdebase-runtime-data-common-kde3
```

Then re-run the apt-get command you ran earlier.

Somehow kdebase-runtime-data-common-kde3 got into an inconsistent state, which is probably why you were having so many problems earlier.

I apologize for all the problems, but at least I now know they exist and can try to fix them... :cool:

---

### Post by beastrace91 on 2008-12-06
Erp! Back to this one:

[quote="My Terminal"]No diversion `any diversion of /usr/share/icons/hicolor/32x32/apps/khotkeys.png', none removed
Removing `diversion of /usr/share/templates/Directory.desktop to /usr/share/templates.kde4/Directory.desktop by kdebase-runtime-data-common-kde3'
dpkg-divert: error checking `/usr/share/templates/Directory.desktop': No such file or directory
dpkg: error processing kdebase-runtime-data-common-kde3 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kdebase-runtime-data-common-kde3
[/quote]

And again there is a whole pile of "No diversion" with different file names before this.

~Jeff

---

### Post by madscientist159 on 2008-12-06
> **beastrace91 said:**
> Erp! Back to this one:



And again there is a whole pile of "No diversion" with different file names before this.

~Jeff

And that is with the --force-all option??

I may need to put  my machine in a similar state and see what works.  I'll try to get back to you tomorrow.

---

### Post by beastrace91 on 2008-12-07
Yep that is with the force all, I copy and pasted your code to my terminal.

~Jeff

---

### Post by __david on 2008-12-07
> **madscientist159 said:**
> David,

1. I'll look in to the kaffeine problem--maybe I goofed and compiled it against kdelibs4c2a.
It seems you've already fixed this? Did apt-get source yesterday and today, today's version seems ok.

> **madscientist159 said:**
> 2. Not sure.  Those are quite nasty due to the sheer number of them--I'll ask the Kubuntu devs for advice on how to handle them
I understand. Maybe there is a smart way to find/sed through the control and rules files? They should be very similar for all those packages.

Maybe I'll have a look into this later.

> **madscientist159 said:**
> 3. Yes.  Before you run KDE applications, open a terminal and run ```
export KDEHOME=~/.kde3
```  You may want to add this to a login or autorun on login script somewhere--I am not familiar with Gnome, so I can't tell you where.:)

I don't know where you put /usr/kde3/bin into $PATH for a pure KDE3 install. 

I've switched to Gnome for now, and everything runs nicely, so my next look into KDE will be after installing Jaunty. Nevertheless.  I just love some KDE-Apps and want to be able to control their look and feel via kcontrol. This is where your repo comes in.

Long story short: I've created a file (kde3.sh) in /etc/profile.d/, where I add /usr/kde3/bin to $PATH. I don't know whether it would be worthwhile to create some compatibility package for non-KDE-users (kde3-compat? kde3-gnome-compat?). 

I guess $KDEHOME also affects KDE 4 applications, so I'm not sure if it is really useful to chance that variable (concerning the separation of KDE3 and KDE4 configuration). If it was possible to control KDE3 and KDE4 config variables separately, one would be able to set that variable in the same /etc/profile.d/ script.

---

### Post by __david on 2008-12-07
The official language-pack-kde-* packages are working with your repository, at least under gnome.

COULD SOMEONE CHECK THIS UNDER KDE 3? 
Just try out amarok (from the kde3-repo). If all menu entries are translated, the packages are working.

Packages not working with Tims repository are:
kde-i18n-* (71 packages)
gwenview-i18n
k3b-i18n

As I said, I will have a look whether there is a smart solution to port all of the kde-i18n-* packages.

---

### Post by rohrfrei on 2008-12-07
Hi,

thank you for this excellent kde3-repository, you safed my day!

One question:
What about those KDE3-applications from the main repository (kvirc, kphotoalbum, kbiff,..) that have those unresolvable KDE4-dependencies: Is there any chance to use them under the current KDE3-build (maybe due some wrapper-magic or something)?

---

### Post by madscientist159 on 2008-12-07
> **rohrfrei said:**
> Hi,

thank you for this excellent kde3-repository, you safed my day!

One question:
What about those KDE3-applications from the main repository (kvirc, kphotoalbum, kbiff,..) that have those unresolvable KDE4-dependencies: Is there any chance to use them under the current KDE3-build (maybe due some wrapper-magic or something)?

rohrfrei,

Report missing packages to [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net)  There is no way to wrap around--the KDE3 libraries are in a different location than the Kubuntu apps expect them to be, this is to maintain compatibility with KDE4.  It is a rather trivial matter to upload the missing packages to my repository, I just don't know what all of them are.:D

Jeff,

I have updated the kdebase-runtime-data-common-kde3 package so that it will not fail on removal, but I have no idea how to get the new package on your system with the package manager ignoring the --force-all option.  If you can somehow force the new version onto your system, then its removal should finally succeed.  Maybe you could manually download the .deb file from the repository and install it with --force-all?  With any luck dpkg will treat this as an upgrade and therefore never call the offending script.

Otherwise, since you mentioned this was a clean installation anyway, now might be a good time to reinstall and just try again.;)

---

### Post by beastrace91 on 2008-12-07
So Mad you think formatting and trying from scratch should make this work? Should I use Ubuntu 8.10 or is there something better to use to get KDE3 working?

~Jeff

---

### Post by madscientist159 on 2008-12-07
> **beastrace91 said:**
> So Mad you think formatting and trying from scratch should make this work? Should I use Ubuntu 8.10 or is there something better to use to get KDE3 working?

~Jeff

It's pretty much guaranteed to work under Kubuntu 8.10 (this is what all my testing has been on), but with the script fix in place there is no reason why Ubuntu 8.10 shouldn't work.

---

### Post by beastrace91 on 2008-12-07
Formatting back to Ubuntu 8.10 now, I'll post later tonight when I get home from work/after it does done downloading everything if it worked.

~Jeff

---

### Post by beastrace91 on 2008-12-07
I have not yet tried loading into KDE3/Installing anything in it yet but at the end of installing it I get this message after running sudo apt-get install kubuntu-desktop-kde3 [quote="My Terminal"]Processing triggers for ufw ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/quote]

This is on a fresh Ubuntu 8.10 install with nothing else run aside from sudo apt-get update/upgrade

~Jeff

---

### Post by madscientist159 on 2008-12-07
> **beastrace91 said:**
> I have not yet tried loading into KDE3/Installing anything in it yet but at the end of installing it I get this message after running sudo apt-get install kubuntu-desktop-kde3 

This is on a fresh Ubuntu 8.10 install with nothing else run aside from sudo apt-get update/upgrade

~Jeff

Hi Jeff,

I don't think you'll have problems like you did last time, but all the same I'd like to fix that error.  Can you re-run sudo apt-get install kubuntu-desktop-kde3 and post all of that command's output here?

Thanks!

---

### Post by dentaku65 on 2008-12-07
> **beastrace91 said:**
> I have not yet tried loading into KDE3/Installing anything in it yet but at the end of installing it I get this message after running sudo apt-get install kubuntu-desktop-kde3 

This is on a fresh Ubuntu 8.10 install with nothing else run aside from sudo apt-get update/upgrade

~Jeff

Try
```
sudo apt-get -f install
```
then again:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by beastrace91 on 2008-12-07
Sorry about the delay went out this afternoon... here is the out put from running that command again (sudo apt-get install kubuntu-desktop-kde3):

[quote="My Terminal"]jeff@kubuntu:~$ sudo apt-get install kubuntu-desktop-kde3
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-desktop-kde3 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kcontrol-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                 Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kdebase-kde3: Depends: kdebase-data-kde3 (>= 4:3.5.10-0ubuntu3~intrepid3) but it is not going to be installed
  kdm-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
            Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kicker-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
               Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kpersonalizer-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                      Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  ksplash-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/quote]

What can I do? And for some reason running sudo apt-get -f install kubuntu-desktop-kde3 Yields the same thing.

~Jeff

---

### Post by beastrace91 on 2008-12-07
Running sudo apt-get -f install Yields this output:

[quote="My Terminal"]jeff@kubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdebase-data-kde3
The following NEW packages will be installed:
  kdebase-data-kde3
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
264 not fully installed or removed.
Need to get 0B/9073kB of archives.
After this operation, 13.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  kdebase-data-kde3
Install these packages without verification [y/N]? y
(Reading database ... 146627 files and directories currently installed.)
Unpacking kdebase-data-kde3 (from .../kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/kde-information.menu', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/quote]

Any ideas?

~Jeff

---

### Post by madscientist159 on 2008-12-07
> **beastrace91 said:**
> Running sudo apt-get -f install Yields this output:



Any ideas?

~Jeff

That's something I have to fix on this end.  Don't worry, you won't have to reinstall over such a minor issue. ;)

If you want, try removing kdebase-runtime-data manually, then do the apt-get -f install.  In the terminal, that would be:
```
sudo dpkg -r --force-all kdebase-runtime-data
sudo apt-get -f install
```

I'll post back when that problem is fixed.

---

### Post by beastrace91 on 2008-12-07
Ok so... it says it removes but then forcing the install still throws this error:

[quote="My Terminal"]jeff@kubuntu:~$ sudo dpkg -r --force-all kdebase-runtime-data
(Reading database ... 
146626 files and directories currently installed.)
Removing kdebase-runtime-data ...
jeff@kubuntu:~$ 
jeff@kubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdebase-data-kde3 kdebase-runtime-data
The following NEW packages will be installed:
  kdebase-data-kde3 kdebase-runtime-data
0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
263 not fully installed or removed.
Need to get 0B/12.2MB of archives.
After this operation, 19.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  kdebase-data-kde3
Install these packages without verification [y/N]? y
Selecting previously deselected package kdebase-runtime-data.
(Reading database ... 146110 files and directories currently installed.)
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a4.1.2-0ubuntu6_all.deb) ...
Unpacking kdebase-data-kde3 (from .../kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/kde-information.menu', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/quote]

I am hoping we can get this resolved in the next day or so I kinda need to install apps and atm this is preventing me from installing wine among other things.

~Jeff

---

### Post by hikaricore on 2008-12-07
Out of curiosity, has anyone else had trouble with kwallet?

---

### Post by madscientist159 on 2008-12-07
> **beastrace91 said:**
> Ok so... it says it removes but then forcing the install still throws this error:



I am hoping we can get this resolved in the next day or so I kinda need to install apps and atm this is preventing me from installing wine among other things.

~Jeff

I just tried it here on a brand new install with no errors. :confused:

Did you update your system *before* attempting to install kubuntu-desktop-kde3?  If you didn't then the older version of kdebase-runtime-data is a problem.  

You **must** update to the latest Kubuntu/Ubuntu/Xubuntu before attempting to install KDE3 :p

For now, to get you around that error, you can do this:
```
sudo dpkg -i --force-all /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb
```

hikaricore,

What's going on with KWallet?

---

### Post by beastrace91 on 2008-12-07
> **madscientist159 said:**
> 
For now, to get you around that error, you can do this:
```
sudo dpkg -i --force-all /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb
```

That command there let it work for me. Just as an FYI though my Ubuntu was fully up to date before I tried installing this. But hey it appears to be working now I will let you know if it gives me any other issues.

~Jeff

---

### Post by madscientist159 on 2008-12-07
> **beastrace91 said:**
> That command there let it work for me. Just as an FYI though my Ubuntu was fully up to date before I tried installing this. But hey it appears to be working now I will let you know if it gives me any other issues.

~Jeff

OK, glad it is now working!  The information you provided me allowed me to notice that my Kubuntu install has a bug in it--the /etc/xdg/menus/kde-information.menu was not properly "owned" by kdebase-runtime-data and therefore did not thrown an error.  On your system, it *was* owned by kdebase-runtime-data and therefore correctly threw an error.

Sorry for all the trouble! :KS

---

### Post by iX9 on 2008-12-07
Hi!
What about language packs? Will they work correctly? Or I should install it from hardy repo? Somehow..¿

---

### Post by madscientist159 on 2008-12-07
> **iX9 said:**
> Hi!
What about language packs? Will they work correctly? Or I should install it from hardy repo? Somehow..¿

I don't know yet.  It's on my to-do list, behind several other major issues (one of which is proper OpenOffice integration...)  I have not yet had a chance to ask the Kubuntu devs about it; been too busy pasting the base system back together.:p

---

### Post by beastrace91 on 2008-12-08
Ok just a small annoyance I am looking to fix, I have two add remove programs options on my KMenu, one the Adept installer (this works fine) and the other I believe is from my Gnome install maybe? Any idea how I can remove it from this menu? 

~Jeff

---

### Post by madscientist159 on 2008-12-08
> **beastrace91 said:**
> Ok just a small annoyance I am looking to fix, I have two add remove programs options on my KMenu, one the Adept installer (this works fine) and the other I believe is from my Gnome install maybe? Any idea how I can remove it from this menu? 

~Jeff

Are you referring to Synaptic?  This is Gnome's package manager, and getting rid of it is as simple as:
```
sudo apt-get remove synaptic
```

It would have been installed because you overlaid KDE3 onto an Ubuntu installation.

---

### Post by beastrace91 on 2008-12-08
hmmm Amarok does not want to load any of my MP3s any ideas? Says it is fully up to date, when I first tried to load one it said it need to update to run MP3s properly how ever it did not work properly, tells me media is "not playable". Ideas?

~Jeff

---

### Post by dentaku65 on 2008-12-08
> **beastrace91 said:**
> hmmm Amarok does not want to load any of my MP3s any ideas? Says it is fully up to date, when I first tried to load one it said it need to update to run MP3s properly how ever it did not work properly, tells me media is "not playable". Ideas?

~Jeff

Are you sure that is an Amarok problem?
Seems to me a problem of some missing codec or restricted driver.
Try to use:
```
aplay <file_mp3>
```
if is a system problem.

Btw, Amarox here is perfect

---

### Post by dqp on 2008-12-08
> **beastrace91 said:**
> hmmm Amarok does not want to load any of my MP3s any ideas? Says it is fully up to date, when I first tried to load one it said it need to update to run MP3s properly how ever it did not work properly, tells me media is "not playable". Ideas?

~Jeff

there is a problem...

when I pressed the button "Install MP3 Codec" I get this in the console:

```
/bin/sh: /usr/lib/amarok/install-mp3: No such file or directory

```

this file is located in /usr/kde3/lib/amarok/install-mp3.

something wrong with the paths, you should add /usr/kde3/bin:/usr/kde3/lib:/usr/kde3/share to your $PATH variable..

---

### Post by beastrace91 on 2008-12-08
forgive me but where can I find this $PATH var at to edit?

~Jeff

---

### Post by nicksanders on 2008-12-08
Just as a warning in case its not just my weird config but this morning after I did an update I lost all the window borders, title bars etc and couldn't type. I was still able to log in normally to the KDE session as opposed to the KDE3 session.

I tracked it down to desktop-effects-kde-kde3. I fixed it with the following:

 sudo dpkg -i /var/cache/apt/archives/desktop-effects-kde-kde3_0.4_all.deb

---

### Post by johndouberro on 2008-12-09
I am not sure if it was reported, but an error happened during installation kde3 into the ubuntu with kde4:

E: /var/cache/apt/archives/kdeartwork-misc-kde3_4%3a3.5.10-0ubuntu1~intrepid2_all.deb: trying to overwrite `/usr/share/sounds/KDE_Startup_new.wav', which is also in package kdeartwork-misc

---

### Post by of_darkness on 2008-12-09
[ anomander-rake: ~ ]$ apt-cache rdepends kdelibs4c2-kde3
<kdelibs4c2-kde3>
[ anomander-rake: ~ 

Plz fix so that i can decide wich apps that are missing in the new repo, abakus is missing atleast.

Dunno if it has been reported as a bug on your bug tracker but i cant get along whit those ******* whitout getting aggrevated to hell so i cant check so if it isthen newermind this post:P

---

### Post by KubuntuKilledMe on 2008-12-10
Hey madscientist159, can you add bluetooth support and Katapult to your kde3 build? Thanks a lot!

---

### Post by beastrace91 on 2008-12-10
Hey everything has been running great, but I was just wondering if I might request getting the battery icon added to tray for laptops? I just noticed this afternoon it was not there... do I need to install it or is it not in your KDE3 build yet?

~Jeff

---

### Post by madscientist159 on 2008-12-10
> **beastrace91 said:**
> Hey everything has been running great, but I was just wondering if I might request getting the battery icon added to tray for laptops? I just noticed this afternoon it was not there... do I need to install it or is it not in your KDE3 build yet?

~Jeff

Glad to hear that! :)

I'll add the KDE power manager to my to-do list.

KubuntuKilledMe,

Katapult, yes...Bluetooth, no.  Bluetooth requires a rewrite of the entire KDE Bluetooth stack from what I am told, and I have neither the time nor the resources (no Bluetooth peripherals at all!) to do so.  If someone would like to take this on as a challenge, then please contact me ASAP! :p

---

### Post by nicksanders on 2008-12-11
Hi, everything is running great for me to. Thanks for all your hard work.

If it will save you some work I have guidance-power-manager, kde-guidance-powermanager both 4:4.1.2-0ubuntu5 installed and it works perfectly and looks really nice too.

The application I'm missing is krename would it be possible to add that to your list?

---

### Post by johndouberro on 2008-12-11
Big issue for me - I found basket is missing in your repository. I am almost completely depending on this note tool. Please could you add it to your repository? (also the katapult would be good). Thanks!

(Probably I will try to compile basket myself, but I know almost nothing about how to tell it where kde is)

---

### Post by madscientist159 on 2008-12-12
> **johndouberro said:**
> Big issue for me - I found basket is missing in your repository. I am almost completely depending on this note tool. Please could you add it to your repository? (also the katapult would be good). Thanks!

(Probably I will try to compile basket myself, but I know almost nothing about how to tell it where kde is)

Can you test both basket and katapult for me?  I uploaded them earlier today and they built, but my test system is currently down so I have no idea if they work or not.  Just apt-get update then install. :)

---

### Post by johndouberro on 2008-12-12
tested. both work fine. thanks very much!

---

### Post by of_darkness on 2008-12-13
I have now check the reverse dependency on kdelibs4c2 and kdelibs4c2-kde3 and you nead to package alot of stuff like digikam that has a dependency of the original kdelibs4c2

heres the reverse depndencys for kdelibs4c2

```
  abakus
  adept-batch
  adept-installer
  adept-manager
  adept-notifier
  adept-updater
  akregator
  amarok
  amarok-engine-xine
  amarok-engine-yauap
  amor
  anymeal
  apollon
  ark
  artsbuilder
  atlantik
  atlantikdesigner
  basket
  bibletime
  celestia-kde
  cervisia
  compizconfig-backend-kconfig
  creox
  datakiosk
  dcoprss
  digikam
  dolphin
  eqonomize
  eva
  filelight
  gambas2-gb-qt-kde
  gambas2-gb-qt-kde-html
  ggz-kde-client
  ggz-kde-games
  guarddog
  guidedog
  gwenrename
  gwenview
  hotswap-gui
  icecc-monitor
  ipodslave
  juk
  k3b
  kaboodle
  kaddressbook
  kaddressbook-plugins
  kadu-kde-modules
  kaffeine
  kaffeine
  kaffeine-gstreamer
  kaffeine-gstreamer
  kalarm
  kalcul
  kallery
  kalzium
  kamefu
  kamera
  kanagram
  kandy
  kanjisaver
  kannasaver
  kappfinder
  karbon
  karbon
  karchiver
  karm
  kasablanca
  kasteroids
  kat
  katalog
  katapult
  kate
  kate-plugins
  katomic
  kautoclick
  kbackgammon
  kbarcode
  kbattleship
  kbfx
  kbib
  kbibtex
  kbiff
  kblackbox
  kboincspy
  kbounce
  kbruch
  kbstate
  kbugbuster
  kcalc
  kcemirror
  kchart
  kchart
  kcheckgmail
  kchmviewer
  kcmnvview
  kcmpureftpd
  kcoloredit
  kcontrol
  kcontrol-autostart
  kcpuload
  kcron
  kdbg
  kdbus
  kdeaddons-kfile-plugins
  kdeadmin-kfile-plugins
  kdeartwork-style
  kdeartwork-theme-window
  kdebase-bin
  kdebase-bin-kde3
  kdebase-kio-plugins
 kdebluetooth
  kdegraphics-kfile-plugins
  kde-guidance
  kde-i18n-af
  kde-i18n-ar
  kde-i18n-az
  kde-i18n-be
  kde-i18n-bg
  kde-i18n-bn
  kde-i18n-br
  kde-i18n-bs
  kde-i18n-ca
  kde-i18n-cs
  kde-i18n-csb
  kde-i18n-cy
  kde-i18n-da
  kde-i18n-de
  kde-i18n-el
  kde-i18n-engb
  kde-i18n-eo
  kde-i18n-es
  kde-i18n-et
  kde-i18n-eu
  kde-i18n-fa
  kde-i18n-fi
  kde-i18n-fr
  kde-i18n-fy
  kde-i18n-ga
  kde-i18n-gl
  kde-i18n-he
  kde-i18n-hi
  kde-i18n-hr
  kde-i18n-hsb
  kde-i18n-hu
  kde-i18n-is
  kde-i18n-it
  kde-i18n-ja
  kde-i18n-kk
  kde-i18n-km
  kde-i18n-ko
  kde-i18n-lt
  kde-i18n-lv
  kde-i18n-mk
  kde-i18n-mn
  kde-i18n-ms
  kde-i18n-nb
  kde-i18n-nds
  kde-i18n-nl
  kde-i18n-nn
  kde-i18n-pa
  kde-i18n-pl
  kde-i18n-pt
  kde-i18n-ptbr
  kde-i18n-ro
  kde-i18n-ru
  kde-i18n-rw
  kde-i18n-se
  kde-i18n-sk
  kde-i18n-sl
  kde-i18n-sr
  kde-i18n-srlatn
  kde-i18n-ss
  kde-i18n-sv
  kde-i18n-ta
  kde-i18n-te
  kde-i18n-tg
  kde-i18n-th
  kde-i18n-tr
  kde-i18n-uk
  kde-i18n-uz
  kde-i18n-wa
  kde-i18n-vi
  kde-i18n-zhcn
  kde-i18n-zhtw
  kdelibs
  kdelibs
  kdelibs4c2a-kde3
  kdelibs4-dev
  kdelibs4-dev
  kdelibs4-dev
  kdelibs4-dev
  kdelibs-dbg
  kdelibs-dbg
  kdelirc
  kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins
  kdenetwork-filesharing
  kdenetwork-kfile-plugins
  kdenlive
  kdepasswd
  kdepim-kio-plugins
  kdepim-kresources
  kdepim-wizards
  kdeprint
  kde-pwmanager
  kdescreensaver-aasaver
  kdesktop
  kde-style-comix
  kde-style-domino
  kde-style-klearlook
  kde-style-lipstik
  kde-style-polyester
  kde-style-qtcurve
  kde-style-serenity
  kdesudo
  kde-systemsettings
  kdetv
  kde-tweak
  kdevelop
  kdf
  kdiff3
  kdirstat
  kdissert
  kdm
  kdmtheme
  kdnssd
  kdvi
  kedit
  keep
  kenolaba
  kexi
  kexi
  kexi-mdb-plugin
  keybled
  kfilereplace
  kfilereplace
  kfind
  kfish
  kflickr
  kfocus
  kfolding
  kfouleggs
  kftpgrabber
  kgamma
  kgeography
  kget
  kghostview
  kgmailnotifier
  kgoldrunner
  kgpg
  kguitar
  khangman
  khelpcenter
  khexedit
  kicker
  kicker-applets
  kiconedit
  kid3
  kig
  kile
  kile
  kima
  kimagemapeditor
  kinstaller
  kio-apt
  kio-beagle
  kio-locate
  kiosktool
  kio-umountwrapper
  kipi-plugins
  kiso
  kitchensync
  kitty
  kjots
  kjscmd
  kjumpingcube
  kkbswitch
  klamav
  klaptopdaemon
  klavier
  kleansweep
  klear
  klettres
  klibido
  klickety
  klineakconfig
  klines
  klinkstatus
  klinkstatus
  klipper
  klipsi
  klog
  klogic
  kmag
  kmahjongg
  kmail
  kmailcvt
  kmediafactory
  kmenuedit
  kmess
  kmhtconvert
  kmidimon
  kmilo
  kmines
  kmix
  kmobiletools
  kmoon
  kmousetool
  kmouth
  kmplayer
  kmplayer-base
  kmplot
  kmtrace
  kmyfirewall
  kmymoney2
  kmymoney2-plugin-aqbanking
  kmysqladmin
  knet
  knetdockapp
  knetfilter
  knetload
  knetstats
  knetwalk
  knetworkconf
  knewsticker
  knights
  knmap
  knoda
  knode
  knotes
  knowit
  knutclient
  koffice-libs
  koffice-libs
  kolf
  kolourpaint
  komba2
  kommander
  kommander
  kommando
  komparator
  kompare
  kompile
  kompose
  konq-plugins
  konqueror
  konqueror-nsplugins
  konquest
  konsole
  konsolekalendar
  kontact
  konversation
  konversation
  kooka
  kooldock
  kopete
  kopete-plugin-desklist
  kopete-plugin-thinklight
  kopete-silc-plugin
  korganizer
  kover
  koverartist
  kpackage
  kpager
  kpar2
  kpat
  kpdf
  kpercentage
  kpersonalizer
  kpf
  kphotoalbum
  kpicosim
  kplato
  kplato
  kpoker
  kpowersave
  kppp
  kpreg
  kpresenter
  kpresenter
  kprof
  kpsion
  kpsk
  kptc
  kradio
  kraft
  krdc
  krecipes
  krecordmydesktop
  kredentials
  kreetingkard
  kregexpeditor
  krename
  kreversi
  krfb
  krita
  krita
  kruler
  krusader
  ksame
  ksayit
  kscope
  kscreensaver
  kscreensaver-xsavers
  ksensors
  kshisen
  kshowmail
  kshutdown
  ksig
  ksim
  ksimus
  ksirtet
  kslovar
  ksmiletris
  ksmserver
  ksnake
  ksnapshot
  ksniffer
  ksociograma
  ksocrat
  ksokoban
  kspaceduel
  ksplash
  ksplash-engine-moodin
  kspread
  kspread
  kssh
  ksshaskpass
  kstars
  kst-bin
  kst-plugins
  kstreamripper
  ksubtile
  ksubtitleripper
  ksvg
  ksysguard
  ksystemlog
  ksysv
  kteatime
  ktechlab
  ktemperature
  kthesaurus
  kthesaurus
  kthinkbat
  ktimer
  ktimetrace
  ktip
  ktorrent
  ktouch
  ktrack
  ktranslator
  ktron
  kttsd
  ktuberling
  kturtle
  ktux
  kugar
  kugar
  kuickshow
  kuser
  kwalletmanager
  kwavecontrol
  kvdr
  kweather
  kview
  kwin
  kwin4
  kwin-baghira
  kwin-style-alphacube
  kwin-style-blended
  kwin-style-dekorator
  kwin-style-knifty
  kwin-style-powder
  kwin-style-serenity
  kwin-style-suse2
  kvirc
  kwirelessmonitor
  kwlan
  kword
  kword
  kwordquiz
  kworldclock
  kvpnc
  kxgenerator
  kxmame
  kxneur
  kxsldbg
  kxstitch
  kyamo
  kzenexplorer
  labplot
  libarts1c2a
  libarts1-mpeglib
  libcvsservice0
  libdcop3-jni
  libeduwidgetclock0
  libhk-kdeclasses7
  libk3b3
  libk3b3-extracodecs
  libkamefu0
  libkbluetooth0
  libkcal2b
  libkcddb1
  libkdcraw3
  libkde3-jni
  libkdeedu3
  libkdegames1
  libkdepim1a
  libkexiv2-3
  libkipi0
  libkjsembed1
  libkleopatra1
  libkmime2
  libkonq4
  libkorundum0-ruby1.8
  libkpimexchange1
  libkpimidentities1
  libkscan1
  libksieve0
  libkst1c2
  libktnef1
  libmcs-backend-kconfig
  libmlt0.2.5
  librss1
  libskim0
  libsmokekde1
  licq-plugin-kde
  lineak-kdeplugins
  lisa
  lskat
  mailody
  mateedit
  maxemumtvguide
  mediamanager
  mpeglib
  mythbrowser
  nateon
  network-manager-kde
  networkstatus
  noatun
  noatun-plugins
  noteedit
  oooqs2-kde
  openoffice.org-kde
  opensync-plugin-kdepim
  picwiz
  piklab
  plptools-kde
  potracegui
  python-dcop
  python-kde3
  python-kde3-dbg
  qalculate-kde
  quanta
  regina-normal
  rosegarden
  rosegarden
  score-reading-trainer
  showfoto
  sim
  skim
  skim-scim-pinyin
  smb4k
  soundkonverter
  strigi-applet
  styleclock
  superkaramba
  swscanner
  taskjuggler
  tastymenu
  tellico
  tora
  tork
  tripod
  twinkle
  uim-applet-kde
  wordtrans-kde
  xdg-utils

```

and of kdelibs4c2-kde3

```
  adept-batch-kde3
  adept-installer-kde3
  adept-manager-kde3
  adept-notifier-kde3
  adept-updater-kde3
  akregator-kde3
  amarok-engine-xine-kde3
  amarok-engine-yauap-kde3
  amarok-kde3
  amor-kde3
  ark-kde3
  artsbuilder-kde3
  atlantikdesigner-kde3
  atlantik-kde3
  basket-kde3
  blinken-kde3
  cervisia-kde3
  compizconfig-backend-kconfig-kde3
  compiz-kde-kde3
  dcoprss-kde3
  eyesapplet-kde3
  fifteenapplet-kde3
  gwenview-kde3
  juk-kde3
  k3b-kde3
  kaboodle-kde3
  kaddressbook-kde3
  kaddressbook-plugins-kde3
  kaffeine-gstreamer-kde3
  kaffeine-kde3
  kalarm-kde3
  kalzium-kde3
  kamera-kde3
  kanagram-kde3
  kandy-kde3
  kappfinder-kde3
  karm-kde3
  kasteroids-kde3
  katapult-kde3
  kate-kde3
  kate-plugins-kde3
  katomic-kde3
  kaudiocreator-kde3
  kbabel-kde3
  kbackgammon-kde3
  kbattleship-kde3
  kblackbox-kde3
  kbounce-kde3
  kbruch-kde3
  kbstate-kde3
  kbugbuster-kde3
  kcachegrind-kde3
  kcalc-kde3
  kcharselect-kde3
  kcoloredit-kde3
  kcontrol-kde3
  kcron-kde3
  kdat-kde3
  kdeaddons-kfile-plugins-kde3
  kdeadmin-kfile-plugins-kde3
  kdeartwork-style-kde3
  kdeartwork-theme-window-kde3
  kdebase-kde3-bin
  kdebase-kio-plugins-kde3
  kdegraphics-kfile-plugins-kde3
  kdelibs4-kde3-dev
  kdelibs4-kde3-dev
  kdelibs-kde3
  kdelibs-kde3-dbg
  kdelirc-kde3
  kdemultimedia-kfile-plugins-kde3
  kdemultimedia-kio-plugins-kde3
  kdenetwork-filesharing-kde3
  kdenetwork-kfile-plugins-kde3
  kdepasswd-kde3
  kdepim-kfile-plugins-kde3
  kdepim-kio-plugins-kde3
  kdepim-kresources-kde3
  kdepim-wizards-kde3
  kdeprint-kde3
  kdesdk-kfile-plugins-kde3
  kdesdk-kio-plugins-kde3
  kdesdk-misc-kde3
  kdesktop-kde3
  kdessh-kde3
  kde-style-lipstik-kde3
  kde-style-qtcurve-kde3
  kdesudo-kde3
  kde-systemsettings-kde3
  kdevelop-kde3
  kdf-kde3
  kdict-kde3
  kdiff3-kde3
  kdm-kde3
  kdnssd-kde3
  kdvi-kde3
  kedit-kde3
  keduca-kde3
  keep-kde3
  kenolaba-kde3
  kfax-kde3
  kfaxview-kde3
  kfilereplace-kde3
  kfind-kde3
  kfloppy-kde3
  kfouleggs-kde3
  kgamma-kde3
  kgeography-kde3
  kget-kde3
  kghostview-kde3
  kgoldrunner-kde3
  kgpg-kde3
  khangman-kde3
  khelpcenter-kde3
  khexedit-kde3
  kicker-applets-kde3
  kicker-kde3
  kiconedit-kde3
  kig-kde3
  kimagemapeditor-kde3
  kio-apt-kde3
  kio-locate-kde3
  kitchensync-kde3
  kiten-kde3
  kjots-kde3
  kjscmd-kde3
  kjumpingcube-kde3
  klaptopdaemon-kde3
  klatin-kde3
  kleopatra-kde3
  klettres-kde3
  klickety-kde3
  klines-kde3
  klinkstatus-kde3
  klipper-kde3
  kmag-kde3
  kmahjongg-kde3
  kmailcvt-kde3
  kmail-kde3
  kmenuedit-kde3
  kmid-kde3
  kmilo-kde3
  kmilo-legacy-kde3
  kmines-kde3
  kmix-kde3
  kmoon-kde3
  kmousetool-kde3
  kmouth-kde3
  kmplot-kde3
  kmrml-kde3
  kmtrace-kde3
  knemo-kde3
  knetwalk-kde3
  knetworkconf-kde3
  knewsticker-kde3
  knode-kde3
  knotes-kde3
  kode-kde3
  kodo-kde3
  kolf-kde3
  kolourpaint-kde3
  kommander-kde3
  kompare-kde3
  konq-plugins-kde3
  konqueror-kde3
  konqueror-nsplugins-kde3
  konquest-kde3
  konsolekalendar-kde3
  konsole-kde3
  kontact-kde3
  kooka-kde3
  kopete-kde3
  korganizer-kde3
  korn-kde3
  kpackage-kde3
  kpager-kde3
  kpat-kde3
  kpdf-kde3
  kpercentage-kde3
  kpersonalizer-kde3
  kpf-kde3
  kpicosim-kde3
  kpilot-kde3
  kpoker-kde3
  kpovmodeler-kde3
  kppp-kde3
  krdc-kde3
  krec-kde3
  kregexpeditor-kde3
  krename-kde3
  kreversi-kde3
  krfb-kde3
  kruler-kde3
  krusader-kde3
  ksame-kde3
  ksayit-kde3
  kscd-kde3
  kscreensaver-kde3
  kscreensaver-xsavers-kde3
  kshisen-kde3
  ksig-kde3
  ksim-kde3
  ksirc-kde3
  ksirtet-kde3
  ksmiletris-kde3
  ksmserver-kde3
  ksnake-kde3
  ksnapshot-kde3
  ksokoban-kde3
  kspaceduel-kde3
  ksplash-engine-moodin-kde3
  ksplash-kde3
  kspy-kde3
  kstars-kde3
  ksvg-kde3
  ksysguard-kde3
  ksystemlog-kde3
  ksysv-kde3
  ktalkd-kde3
  kteatime-kde3
  ktimer-kde3
  ktip-kde3
  ktnef-kde3
  ktouch-kde3
  ktron-kde3
  kttsd-contrib-plugins-kde3
  kttsd-kde3
  ktuberling-kde3
  kturtle-kde3
  ktux-kde3
  kuickshow-kde3
  kuiviewer-kde3
  kunittest-kde3
  kuser-kde3
  kwalletmanager-kde3
  kweather-kde3
  kverbos-kde3
  kview-kde3
  kviewshell-kde3
  kwifimanager-kde3
  kwin4-kde3
  kwin-kde3
  kwin-style-crystal-kde3
  kvoctrain-kde3
  kwordquiz-kde3
kworldclock-kde3
  kxsldbg-kde3
  libarts1c2a-kde3
  libarts1-mpeglib-kde3
  libarts1-xine-kde3
  libcvsservice0-kde3
  libdcop3-jni-kde3
  libk3b3-extracodecs-kde3
  libk3b3-kde3
  libkcal2b-kde3
  libkcddb1-kde3
  libkde3-jni-kde3
  libkdeedu3-kde3
  libkdegames1-kde3
  libkdepim1a-kde3
  libkgantt0-kde3
  libkipi0-kde3
  libkiten1-kde3
  libkjsembed1-kde3
  libkleopatra1-kde3
  libkmime2-kde3
  libkonq4-kde3
  libkorundum0-ruby1.8-kde3
  libkpimexchange1-kde3
  libkpimidentities1-kde3
  libkscan1-kde3
  libksieve0-kde3
  libktnef1-kde3
  librss1-kde3
  libsmokekde1-kde3
  lilo-config-kde3
  lisa-kde3
  lskat-kde3
  mpeglib-kde3
  networkstatus-kde3
  noatun-kde3
  noatun-plugins-kde3
  python-dcop-kde3
  python-kde3-kde3
  python-kde3-kde3-dbg
  quanta-kde3
  superkaramba-kde3
  umbrello-kde3
  yakuake-kde3

```

and a diff -y kdelibs4c2 kdelibs4c2-kde3

```
  abakus                              |      adept-batch-kde3
  adept-batch                              |      adept-installer-kde3
  adept-installer                          |      adept-manager-kde3
  adept-manager                              |      adept-notifier-kde3
  adept-notifier                          |      adept-updater-kde3
  adept-updater                              |      akregator-kde3
  akregator                              |      amarok-engine-xine-kde3
  amarok                              |      amarok-engine-yauap-kde3
  amarok-engine-xine                          |      amarok-kde3
  amarok-engine-yauap                          |      amor-kde3
  amor                                  |      ark-kde3
  anymeal                              |      artsbuilder-kde3
  apollon                              |      atlantikdesigner-kde3
  ark                                  |      atlantik-kde3
  artsbuilder                              |      basket-kde3
  atlantik                              |      blinken-kde3
  atlantikdesigner                          |      cervisia-kde3
  basket                              |      compizconfig-backend-kconfig-kde3
  bibletime                              |      compiz-kde-kde3
  celestia-kde                              |      dcoprss-kde3
  cervisia                              |      eyesapplet-kde3
  compizconfig-backend-kconfig                      |      fifteenapplet-kde3
  creox                                  |      gwenview-kde3
  datakiosk                              |      juk-kde3
  dcoprss                              |      k3b-kde3
  digikam                              |      kaboodle-kde3
  dolphin                              |      kaddressbook-kde3
  eqonomize                              |      kaddressbook-plugins-kde3
  eva                                  |      kaffeine-gstreamer-kde3
  filelight                              |      kaffeine-kde3
  gambas2-gb-qt-kde                          |      kalarm-kde3
  gambas2-gb-qt-kde-html                      |      kalzium-kde3
  ggz-kde-client                          |      kamera-kde3
  ggz-kde-games                              |      kanagram-kde3
  guarddog                              |      kandy-kde3
  guidedog                              |      kappfinder-kde3
  gwenrename                              |      karm-kde3
  gwenview                              |      kasteroids-kde3
  hotswap-gui                              |      katapult-kde3
  icecc-monitor                              |      kate-kde3
  ipodslave                              |      kate-plugins-kde3
  juk                                  |      katomic-kde3
  k3b                                  |      kaudiocreator-kde3
  kaboodle                              |      kbabel-kde3
  kaddressbook                              |      kbackgammon-kde3
  kaddressbook-plugins                          |      kbattleship-kde3
  kadu-kde-modules                          |      kblackbox-kde3
  kaffeine                              |      kbounce-kde3
  kaffeine                              |      kbruch-kde3
  kaffeine-gstreamer                          |      kbstate-kde3
  kaffeine-gstreamer                          |      kbugbuster-kde3
  kalarm                              |      kcachegrind-kde3
  kalcul                              |      kcalc-kde3
  kallery                              |      kcharselect-kde3
  kalzium                              |      kcoloredit-kde3
  kamefu                              |      kcontrol-kde3
  kamera                              |      kcron-kde3
  kanagram                              |      kdat-kde3
  kandy                                  |      kdeaddons-kfile-plugins-kde3
  kanjisaver                              |      kdeadmin-kfile-plugins-kde3
  kannasaver                              |      kdeartwork-style-kde3
  kappfinder                              |      kdeartwork-theme-window-kde3
  karbon                              |      kdebase-kde3-bin
  karbon                              |      kdebase-kio-plugins-kde3
  karchiver                              |      kdegraphics-kfile-plugins-kde3
  karm                                  |      kdelibs4-kde3-dev
  kasablanca                              |      kdelibs4-kde3-dev
  kasteroids                              |      kdelibs-kde3
  kat                                  |      kdelibs-kde3-dbg
  katalog                              |      kdelirc-kde3
  katapult                              |      kdemultimedia-kfile-plugins-kde3
  kate                                  |      kdemultimedia-kio-plugins-kde3
  kate-plugins                              |      kdenetwork-filesharing-kde3
  katomic                              |      kdenetwork-kfile-plugins-kde3
  kautoclick                              |      kdepasswd-kde3
  kbackgammon                              |      kdepim-kfile-plugins-kde3
  kbarcode                              |      kdepim-kio-plugins-kde3
  kbattleship                              |      kdepim-kresources-kde3
  kbfx                                  |      kdepim-wizards-kde3
  kbib                                  |      kdeprint-kde3
  kbibtex                              |      kdesdk-kfile-plugins-kde3
  kbiff                                  |      kdesdk-kio-plugins-kde3
  kblackbox                              |      kdesdk-misc-kde3
  kboincspy                              |      kdesktop-kde3
  kbounce                              |      kdessh-kde3
  kbruch                              |      kde-style-lipstik-kde3
  kbstate                              |      kde-style-qtcurve-kde3
  kbugbuster                              |      kdesudo-kde3
  kcalc                                  |      kde-systemsettings-kde3
  kcemirror                              |      kdevelop-kde3
  kchart                              |      kdf-kde3
  kchart                              |      kdict-kde3
  kcheckgmail                              |      kdiff3-kde3
  kchmviewer                              |      kdm-kde3
  kcmnvview                              |      kdnssd-kde3
  kcmpureftpd                              |      kdvi-kde3
  kcoloredit                              |      kedit-kde3
  kcontrol                              |      keduca-kde3
  kcontrol-autostart                          |      keep-kde3
  kcpuload                              |      kenolaba-kde3
  kcron                                  |      kfax-kde3
  kdbg                                  |      kfaxview-kde3
  kdbus                                  |      kfilereplace-kde3
  kdeaddons-kfile-plugins                      |      kfind-kde3
  kdeadmin-kfile-plugins                      |      kfloppy-kde3
  kdeartwork-style                          |      kfouleggs-kde3
  kdeartwork-theme-window                      |      kgamma-kde3
  kdebase-bin                              |      kgeography-kde3
  kdebase-bin-kde3                          |      kget-kde3
  kdebase-kio-plugins                          |      kghostview-kde3
 kdebluetooth                              |      kgoldrunner-kde3
  kdegraphics-kfile-plugins                      |      kgpg-kde3
  kde-guidance                              |      khangman-kde3
  kde-i18n-af                              |      khelpcenter-kde3
  kde-i18n-ar                              |      khexedit-kde3
  kde-i18n-az                              |      kicker-applets-kde3
  kde-i18n-be                              |      kicker-kde3
  kde-i18n-bg                              |      kiconedit-kde3
  kde-i18n-bn                              |      kig-kde3
  kde-i18n-br                              |      kimagemapeditor-kde3
  kde-i18n-bs                              |      kio-apt-kde3
  kde-i18n-ca                              |      kio-locate-kde3
  kde-i18n-cs                              |      kitchensync-kde3
  kde-i18n-csb                              |      kiten-kde3
  kde-i18n-cy                              |      kjots-kde3
  kde-i18n-da                              |      kjscmd-kde3
  kde-i18n-de                              |      kjumpingcube-kde3
  kde-i18n-el                              |      klaptopdaemon-kde3
  kde-i18n-engb                              |      klatin-kde3
  kde-i18n-eo                              |      kleopatra-kde3
  kde-i18n-es                              |      klettres-kde3
  kde-i18n-et                              |      klickety-kde3
  kde-i18n-eu                              |      klines-kde3
  kde-i18n-fa                              |      klinkstatus-kde3
  kde-i18n-fi                              |      klipper-kde3
  kde-i18n-fr                              |      kmag-kde3
  kde-i18n-fy                              |      kmahjongg-kde3
  kde-i18n-ga                              |      kmailcvt-kde3
  kde-i18n-gl                              |      kmail-kde3
  kde-i18n-he                              |      kmenuedit-kde3
  kde-i18n-hi                              |      kmid-kde3
  kde-i18n-hr                              |      kmilo-kde3
  kde-i18n-hsb                              |      kmilo-legacy-kde3
  kde-i18n-hu                              |      kmines-kde3
  kde-i18n-is                              |      kmix-kde3
  kde-i18n-it                              |      kmoon-kde3
  kde-i18n-ja                              |      kmousetool-kde3
  kde-i18n-kk                              |      kmouth-kde3
  kde-i18n-km                              |      kmplot-kde3
  kde-i18n-ko                              |      kmrml-kde3
  kde-i18n-lt                              |      kmtrace-kde3
  kde-i18n-lv                              |      knemo-kde3
  kde-i18n-mk                              |      knetwalk-kde3
  kde-i18n-mn                              |      knetworkconf-kde3
  kde-i18n-ms                              |      knewsticker-kde3
  kde-i18n-nb                              |      knode-kde3
  kde-i18n-nds                              |      knotes-kde3
  kde-i18n-nl                              |      kode-kde3
  kde-i18n-nn                              |      kodo-kde3
  kde-i18n-pa                              |      kolf-kde3
  kde-i18n-pl                              |      kolourpaint-kde3
  kde-i18n-pt                              |      kommander-kde3
  kde-i18n-ptbr                              |      kompare-kde3
  kde-i18n-ro                              |      konq-plugins-kde3
  kde-i18n-ru                              |      konqueror-kde3
  kde-i18n-rw                              |      konqueror-nsplugins-kde3
  kde-i18n-se                              |      konquest-kde3
  kde-i18n-sk                              |      konsolekalendar-kde3
  kde-i18n-sl                              |      konsole-kde3
  kde-i18n-sr                              |      kontact-kde3
  kde-i18n-srlatn                          |      kooka-kde3
  kde-i18n-ss                              |      kopete-kde3
  kde-i18n-sv                              |      korganizer-kde3
  kde-i18n-ta                              |      korn-kde3
  kde-i18n-te                              |      kpackage-kde3
  kde-i18n-tg                              |      kpager-kde3
  kde-i18n-th                              |      kpat-kde3
  kde-i18n-tr                              |      kpdf-kde3
  kde-i18n-uk                              |      kpercentage-kde3
  kde-i18n-uz                              |      kpersonalizer-kde3
  kde-i18n-wa                              |      kpf-kde3
  kde-i18n-vi                              |      kpicosim-kde3
  kde-i18n-zhcn                              |      kpilot-kde3
  kde-i18n-zhtw                              |      kpoker-kde3
  kdelibs                              |      kpovmodeler-kde3
  kdelibs                              |      kppp-kde3
  kdelibs4c2a-kde3                          |      krdc-kde3
  kdelibs4-dev                              |      krec-kde3
  kdelibs4-dev                              |      kregexpeditor-kde3
  kdelibs4-dev                              |      krename-kde3
  kdelibs4-dev                              |      kreversi-kde3
  kdelibs-dbg                              |      krfb-kde3
  kdelibs-dbg                              |      kruler-kde3
  kdelirc                              |      krusader-kde3
  kdemultimedia-kfile-plugins                      |      ksame-kde3
  kdemultimedia-kio-plugins                      |      ksayit-kde3
  kdenetwork-filesharing                      |      kscd-kde3
  kdenetwork-kfile-plugins                      |      kscreensaver-kde3
  kdenlive                              |      kscreensaver-xsavers-kde3
  kdepasswd                              |      kshisen-kde3
  kdepim-kio-plugins                          |      ksig-kde3
  kdepim-kresources                          |      ksim-kde3
  kdepim-wizards                          |      ksirc-kde3
  kdeprint                              |      ksirtet-kde3
  kde-pwmanager                              |      ksmiletris-kde3
  kdescreensaver-aasaver                      |      ksmserver-kde3
  kdesktop                              |      ksnake-kde3
  kde-style-comix                          |      ksnapshot-kde3
  kde-style-domino                          |      ksokoban-kde3
  kde-style-klearlook                          |      kspaceduel-kde3
  kde-style-lipstik                          |      ksplash-engine-moodin-kde3
  kde-style-polyester                          |      ksplash-kde3
  kde-style-qtcurve                          |      kspy-kde3
  kde-style-serenity                          |      kstars-kde3
  kdesudo                              |      ksvg-kde3
  kde-systemsettings                          |      ksysguard-kde3
  kdetv                                  |      ksystemlog-kde3
  kde-tweak                              |      ksysv-kde3
  kdevelop                              |      ktalkd-kde3
  kdf                                  |      kteatime-kde3
  kdiff3                              |      ktimer-kde3
  kdirstat                              |      ktip-kde3
  kdissert                              |      ktnef-kde3
  kdm                                  |      ktouch-kde3
  kdmtheme                              |      ktron-kde3
  kdnssd                              |      kttsd-contrib-plugins-kde3
  kdvi                                  |      kttsd-kde3
  kedit                                  |      ktuberling-kde3
  keep                                  |      kturtle-kde3
  kenolaba                              |      ktux-kde3
  kexi                                  |      kuickshow-kde3
  kexi                                  |      kuiviewer-kde3
  kexi-mdb-plugin                          |      kunittest-kde3
  keybled                              |      kuser-kde3
  kfilereplace                              |      kwalletmanager-kde3
  kfilereplace                              |      kweather-kde3
  kfind                                  |      kverbos-kde3
  kfish                                  |      kview-kde3
  kflickr                              |      kviewshell-kde3
  kfocus                              |      kwifimanager-kde3
  kfolding                              |      kwin4-kde3
  kfouleggs                              |      kwin-kde3
  kftpgrabber                              |      kwin-style-crystal-kde3
  kgamma                              |      kvoctrain-kde3
  kgeography                              |      kwordquiz-kde3
  kget                                  |    kworldclock-kde3
  kghostview                              |      kxsldbg-kde3
  kgmailnotifier                          |      libarts1c2a-kde3
  kgoldrunner                              |      libarts1-mpeglib-kde3
  kgpg                                  |      libarts1-xine-kde3
  kguitar                              |      libcvsservice0-kde3
  khangman                              |      libdcop3-jni-kde3
  khelpcenter                              |      libk3b3-extracodecs-kde3
  khexedit                              |      libk3b3-kde3
  kicker                              |      libkcal2b-kde3
  kicker-applets                          |      libkcddb1-kde3
  kiconedit                              |      libkde3-jni-kde3
  kid3                                  |      libkdeedu3-kde3
  kig                                  |      libkdegames1-kde3
  kile                                  |      libkdepim1a-kde3
  kile                                  |      libkgantt0-kde3
  kima                                  |      libkipi0-kde3
  kimagemapeditor                          |      libkiten1-kde3
  kinstaller                              |      libkjsembed1-kde3
  kio-apt                              |      libkleopatra1-kde3
  kio-beagle                              |      libkmime2-kde3
  kio-locate                              |      libkonq4-kde3
  kiosktool                              |      libkorundum0-ruby1.8-kde3
  kio-umountwrapper                          |      libkpimexchange1-kde3
  kipi-plugins                              |      libkpimidentities1-kde3
  kiso                                  |      libkscan1-kde3
  kitchensync                              |      libksieve0-kde3
  kitty                                  |      libktnef1-kde3
  kjots                                  |      librss1-kde3
  kjscmd                              |      libsmokekde1-kde3
  kjumpingcube                              |      lilo-config-kde3
  kkbswitch                              |      lisa-kde3
  klamav                              |      lskat-kde3
  klaptopdaemon                              |      mpeglib-kde3
  klavier                              |      networkstatus-kde3
  kleansweep                              |      noatun-kde3
  klear                                  |      noatun-plugins-kde3
  klettres                              |      python-dcop-kde3
  klibido                              |      python-kde3-kde3
  klickety                              |      python-kde3-kde3-dbg
  klineakconfig                              |      quanta-kde3
  klines                              |      superkaramba-kde3
  klinkstatus                              |      umbrello-kde3
  klinkstatus                              |      yakuake-kde3
  klipper                              <
  klipsi                              <
  klog                                  <
  klogic                              <
  kmag                                  <
  kmahjongg                              <
  kmail                                  <
  kmailcvt                              <
  kmediafactory                              <
  kmenuedit                              <
  kmess                                  <
  kmhtconvert                              <
  kmidimon                              <
  kmilo                                  <
  kmines                              <
  kmix                                  <
  kmobiletools                              <
  kmoon                                  <
  kmousetool                              <
  kmouth                              <
  kmplayer                              <
  kmplayer-base                              <
  kmplot                              <
  kmtrace                              <
  kmyfirewall                              <
  kmymoney2                              <
  kmymoney2-plugin-aqbanking                      <
  kmysqladmin                              <
  knet                                  <
  knetdockapp                              <
  knetfilter                              <
  knetload                              <
  knetstats                              <
  knetwalk                              <
  knetworkconf                              <
  knewsticker                              <
  knights                              <
  knmap                                  <
  knoda                                  <
  knode                                  <
  knotes                              <
  knowit                              <
  knutclient                              <
  koffice-libs                              <
  koffice-libs                              <
  kolf                                  <
  kolourpaint                              <
  komba2                              <
  kommander                              <
  kommander                              <
  kommando                              <
  komparator                              <
  kompare                              <
  kompile                              <
  kompose                              <
  konq-plugins                              <
  konqueror                              <
  konqueror-nsplugins                          <
  konquest                              <
  konsole                              <
  konsolekalendar                          <
  kontact                              <
  konversation                              <
  konversation                              <
  kooka                                  <
  kooldock                              <
  kopete                              <
  kopete-plugin-desklist                      <
  kopete-plugin-thinklight                      <
  kopete-silc-plugin                          <
  korganizer                              <
  kover                                  <
  koverartist                              <
  kpackage                              <
  kpager                              <
  kpar2                                  <
  kpat                                  <
  kpdf                                  <
  kpercentage                              <
  kpersonalizer                              <
  kpf                                  <
  kphotoalbum                              <
  kpicosim                              <
  kplato                              <
  kplato                              <
  kpoker                              <
  kpowersave                              <
  kppp                                  <
  kpreg                                  <
  kpresenter                              <
  kpresenter                              <
  kprof                                  <
  kpsion                              <
  kpsk                                  <
  kptc                                  <
  kradio                              <
  kraft                                  <
  krdc                                  <
  krecipes                              <
  krecordmydesktop                          <
  kredentials                              <
  kreetingkard                              <
  kregexpeditor                              <
  krename                              <
  kreversi                              <
  krfb                                  <
  krita                                  <
  krita                                  <
  kruler                              <
  krusader                              <
  ksame                                  <
  ksayit                              <
  kscope                              <
  kscreensaver                              <
  kscreensaver-xsavers                          <
  ksensors                              <
  kshisen                              <
  kshowmail                              <
  kshutdown                              <
  ksig                                  <
  ksim                                  <
  ksimus                              <
  ksirtet                              <
  kslovar                              <
  ksmiletris                              <
  ksmserver                              <
  ksnake                              <
  ksnapshot                              <
  ksniffer                              <
  ksociograma                              <
  ksocrat                              <
  ksokoban                              <
  kspaceduel                              <
  ksplash                              <
  ksplash-engine-moodin                          <
  kspread                              <
  kspread                              <
  kssh                                  <
  ksshaskpass                              <
  kstars                              <
  kst-bin                              <
  kst-plugins                              <
  kstreamripper                              <
  ksubtile                              <
  ksubtitleripper                          <
  ksvg                                  <
  ksysguard                              <
  ksystemlog                              <
  ksysv                                  <
  kteatime                              <
  ktechlab                              <
  ktemperature                              <
  kthesaurus                              <
  kthesaurus                              <
  kthinkbat                              <
  ktimer                              <
  ktimetrace                              <
  ktip                                  <
  ktorrent                              <
  ktouch                              <
  ktrack                              <
  ktranslator                              <
  ktron                                  <
  kttsd                                  <
  ktuberling                              <
  kturtle                              <
  ktux                                  <
  kugar                                  <
  kugar                                  <
  kuickshow                              <
  kuser                                  <
  kwalletmanager                          <
  kwavecontrol                              <
  kvdr                                  <
  kweather                              <
  kview                                  <
  kwin                                  <
  kwin4                                  <
  kwin-baghira                              <
  kwin-style-alphacube                          <
  kwin-style-blended                          <
  kwin-style-dekorator                          <
  kwin-style-knifty                          <
  kwin-style-powder                          <
  kwin-style-serenity                          <
  kwin-style-suse2                          <
  kvirc                                  <
  kwirelessmonitor                          <
  kwlan                                  <
  kword                                  <
  kword                                  <
  kwordquiz                              <
  kworldclock                              <
  kvpnc                                  <
  kxgenerator                              <
  kxmame                              <
  kxneur                              <
  kxsldbg                              <
  kxstitch                              <
  kyamo                                  <
  kzenexplorer                              <
  labplot                              <
  libarts1c2a                              <
  libarts1-mpeglib                          <
  libcvsservice0                          <
  libdcop3-jni                              <
  libeduwidgetclock0                          <
  libhk-kdeclasses7                          <
  libk3b3                              <
  libk3b3-extracodecs                          <
  libkamefu0                              <
  libkbluetooth0                          <
  libkcal2b                              <
  libkcddb1                              <
  libkdcraw3                              <
  libkde3-jni                              <
  libkdeedu3                              <
  libkdegames1                              <
  libkdepim1a                              <
  libkexiv2-3                              <
  libkipi0                              <
  libkjsembed1                              <
  libkleopatra1                              <
  libkmime2                              <
  libkonq4                              <
  libkorundum0-ruby1.8                          <
  libkpimexchange1                          <
  libkpimidentities1                          <
  libkscan1                              <
  libksieve0                              <
  libkst1c2                              <
  libktnef1                              <
  libmcs-backend-kconfig                      <
  libmlt0.2.5                              <
  librss1                              <
  libskim0                              <
  libsmokekde1                              <
  licq-plugin-kde                          <
  lineak-kdeplugins                          <
  lisa                                  <
  lskat                                  <
  mailody                              <
  mateedit                              <
  maxemumtvguide                          <
  mediamanager                              <
  mpeglib                              <
  mythbrowser                              <
  nateon                              <
  network-manager-kde                          <
  networkstatus                              <
  noatun                              <
  noatun-plugins                          <
  noteedit                              <
  oooqs2-kde                              <
  openoffice.org-kde                          <
  opensync-plugin-kdepim                      <
  picwiz                              <
  piklab                              <
  plptools-kde                              <
  potracegui                              <
  python-dcop                              <
  python-kde3                              <
  python-kde3-dbg                          <
  qalculate-kde                              <
  quanta                              <
  regina-normal                              <
  rosegarden                              <
  rosegarden                              <
  score-reading-trainer                          <
  showfoto                              <
  sim                                  <
  skim                                  <
  skim-scim-pinyin                          <
  smb4k                                  <
  soundkonverter                          <
  strigi-applet                              <
  styleclock                              <
  superkaramba                              <
  swscanner                              <
  taskjuggler                              <
  tastymenu                              <
  tellico                              <
  tora                                  <
  tork                                  <
  tripod                              <
  twinkle                              <
  uim-applet-kde                          <
  wordtrans-kde                              <
  xdg-utils                              <

```

hope it helps you package the missing stuff that has dependencys:)

---

### Post by madscientist159 on 2008-12-13
> **of_darkness said:**
> I have now check the reverse dependency on ...hope it helps you package the missing stuff that has dependencys:)

Yes, it will help a lot!  Thanks!

---

### Post by of_darkness on 2008-12-13
> **madscientist159 said:**
> Yes, it will help a lot!  Thanks!
Good if you nead any other help thats in m,y scope of knowladge just say it:)

---

### Post by iX9 on 2008-12-13
Hi! :p
I have tryed this:

- Install command-line system only with Kubuntu Intrepid Alternate CD (This installs only about 150 basic packages).
- Add -KDE3 repo to sources.list.
- Sudo apt-get update.
- Sudo apt-get upgrade (40 packages updated).
- Restart.
- Sudo apt-get install kubuntu-desktop-kde3.

This downloads 761 packages, but dependency errors occurs while installing - just the same as beatrace91 wrotte.
> 
....
Errors were encountered while processing:
/var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dentaku65 on 2008-12-13
> **of_darkness said:**
> Good if you nead any other help thats in m,y scope of knowladge just say it:)

Thanks!

---

### Post by red_team316 on 2008-12-14
madscientist/dentaku65: I saw in a previous post about no GPG for the new PPA. Is this correct? Is it possible to get a new one? Or are we out of luck? It would be really nice to have one. I'm just wondering as personcomputing still has the GPG listed but the new repo and I'm thinking it may be the old key.

Sorry for not posting much in awhile. I've been rather busy. I'm updating an Intrepid ISO and going to install KDE3 from the new repo for further testing :)



EDIT:

Check this out this problem. From the chroot. Says it has broken packages. Before adding the PPA repo, I did completely upgrade the system so Ibex was up to date.
```

root@kubuntu-hardy-64-box:/# apt-get update
Hit http://security.ubuntu.com intrepid-security Release.gpg                                                              
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US                                                   
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://ppa.launchpad.net intrepid Release.gpg                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Hit http://archive.ubuntu.com intrepid Release.gpg                   
Ign http://archive.ubuntu.com intrepid/main Translation-en_US        
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US  
Hit http://security.ubuntu.com intrepid-security Release             
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com intrepid Release                       
Hit http://security.ubuntu.com intrepid-security/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Packages                  
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://security.ubuntu.com intrepid-security/restricted Packages                      
Hit http://security.ubuntu.com intrepid-security/main Sources        
Hit http://security.ubuntu.com intrepid-security/restricted Sources  
Ign http://ppa.launchpad.net intrepid/main Sources                   
Hit http://archive.ubuntu.com intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/restricted Packages
Hit http://archive.ubuntu.com intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://ppa.launchpad.net intrepid/main Sources
Fetched 1B in 1s (1B/s)  
Reading package lists... Done
root@kubuntu-hardy-64-box:/# apt-get install kubuntu-desktop-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop-kde3: Depends: kdeprint-kde3 but it is not going to be installed
                        Depends: kio-apt-kde3 but it is not going to be installed
                        Depends: ksmserver-kde3 but it is not going to be installed
                        Depends: kwin-style-crystal but it is not installable
                        Depends: libarts1-akode-kde3 but it is not going to be installed
                        Depends: qca-tls but it is not installable
                        Recommends: kde-guidance-kde3 but it is not installable
                        Recommends: adept-kde3 but it is not going to be installed
                        Recommends: cups-pdf but it is not installable
                        Recommends: digikamdesktop-effects-kde-kde3 but it is not installable
                        Recommends: gdebi-kde-kde3 but it is not installable
                        Recommends: k3b-kde3 but it is not going to be installed
                        Recommends: kde-guidance-powermanager-kde3 but it is not installable
                        Recommends: kdebluetooth-kde3 but it is not installable
                        Recommends: keep-kde3 but it is not going to be installed
                        Recommends: kio-umountwrapper-kde3 but it is not installable
                        Recommends: kipi-plugins-kde3 but it is not installable
                        Recommends: kmplayer-konq-plugins-kde3 but it is not installable
                        Recommends: konversation-kde3 but it is not installable
                        Recommends: ktorrent-kde3 but it is not installable
                        Recommends: kubuntu-docs-kde3 but it is not installable
                        Recommends: kubuntu-konqueror-shortcuts-kde3 but it is not installable
                        Recommends: kvkbd-kde3 but it is not installable
                        Recommends: networkstatus but it is not installable
                        Recommends: openoffice.org-kde-kde3 but it is not installable
                        Recommends: scim-bridge-client-qt but it is not installable
                        Recommends: scim-qtimm but it is not installable
                        Recommends: skim but it is not going to be installed
                        Recommends: strigi-applet but it is not installable
                        Recommends: system-config-printer-kde-kde3 but it is not installable
E: Broken packages
root@kubuntu-hardy-64-box:/# 

```

EDIT2: It's qca-tls. A Vanilla Intrepid ISO(and even my updated one as of today) does not include a qca-tls package in the official ubuntu intrepid repos. Whatever it is, Intrepid doesn't need it or provide it. Your kubuntu-desktop-kde3 package depends on it though. I can confirm that on my hardy-box that kubuntu-desktop does also require this package and it is installed on my hardy system. It appears that you will need to add qca-tls to your repo and/or update the kubuntu-desktop-kde3 packages as neccessary. :)

EDIT3: Upon looking further at the chroot output, apparently kwin-style-crystal is also required.


EDIT4: I can't install jack! LOL! Everything is giving me dependancy errors left and right. Am I missing something or are there a bazillion packages broken?
**K3B and Adept Package Errors:**
(seems to boil down to libdvdread3 for K3B and debtags for Adept)
```

root@kubuntu-hardy-64-box:/# apt-get install k3b-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b-kde3: Depends: libdvdread3 (>= 0.9.7) but it is not installable
            Depends: libk3b3-kde3 but it is not going to be installed
E: Broken packages
root@kubuntu-hardy-64-box:/# apt-get install adept-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.


Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  adept-kde3: Depends: adept-manager-kde3 but it is not going to be installed
              Depends: adept-installer-kde3 but it is not going to be installed
              Depends: adept-updater-kde3 but it is not going to be installed
              Depends: adept-notifier-kde3 but it is not going to be installed
              Depends: adept-batch-kde3 but it is not going to be installed
E: Broken packages
root@kubuntu-hardy-64-box:/# apt-get install adept-batch-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  adept-batch-kde3: Depends: adept-manager-kde3 but it is not going to be installed
E: Broken packages
root@kubuntu-hardy-64-box:/# apt-get install adept-manager-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  adept-manager-kde3: Depends: adept-common-kde3 but it is not going to be installed
E: Broken packages
root@kubuntu-hardy-64-box:/# apt-get install adept-common-kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  adept-common-kde3: Depends: debtags (>= 1.6.1) but it is not installable
E: Broken packages
root@kubuntu-hardy-64-box:/# apt-get install debtags
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package debtags is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debtags has no installation candidate
root@kubuntu-hardy-64-box:/# 

```

EDIT5: Apparently debtags is in the universe repo. Dentaku65, can you update the first post to reflect that universe and multiverse repos need to be active in sources.list BEFORE adding the PPA repo.

---

### Post by Jeepston on 2008-12-14
madscientist159, thanks a lot for your work to bring nice and stable DE to Ubuntu 8.10. I almost gave up on KDE after upgrading from 8.04, but your repo saved me :mrgreen:

But currently I am missing two important packages - kpowersave (quite useful for laptops) and dolphin. As I have understood from the earlier posts, they depend on kdelibs4c2a which conflicts with the lib from your repo. Are those two packages on your to-do list for re-compilation in the nearest future? ;)

---

### Post by red_team316 on 2008-12-14
Okay, after adding universe and multiverse, the installation of kubuntu-desktop-kde3 in the chroot terminal went pretty smoothly. When I fire up the ISO in KVM everything appears to go fine up until the point when the ksplash is supposed to switch to the desktop. It appears to load something(as some bouncy icon) for a short moment, but then the screen just stays white! It doesn't load the background/icons/taskbar...NOTHING! But I do have a mouse. It doesn't quite make sense.

There were 2 packages needing configured when they installed, kdm and if I remember correctly kmail or something to do with mail. Do these need to be configured a certain way? I told it to use kdm-kde3 as the default login manager and to use SMTP for the mail thingy.

I'm getting the White screen of death LOL(actually it's somewhat gray almost like it's a big blank window or something)


EDIT: I just re-extracted a Vanilla Intrepid ISO and did not apt-get upgrade it. Copied the /var/cache/apt/archives/*.deb packages to the newly extracted directory structure(No way I am redownloading them again), added universe and multiverse, and the PPA, apt-get updated and apt-get installed kubuntu-desktop-kde3....and still get the white screen of death.


I did notice it was wanting to remove certain KDE4 packages. This doesn't make sense either...if KDE4 and KDE3 play nice together now, there's no reason for it to remove them. I'm wondering if it removed something essential.

---

### Post by madscientist159 on 2008-12-14
> **red_team316 said:**
> Okay, after adding universe and multiverse, the installation of kubuntu-desktop-kde3 in the chroot terminal went pretty smoothly. When I fire up the ISO in KVM everything appears to go fine up until the point when the ksplash is supposed to switch to the desktop. It appears to load something(as some bouncy icon) for a short moment, but then the screen just stays white! It doesn't load the background/icons/taskbar...NOTHING! But I do have a mouse. It doesn't quite make sense.

There were 2 packages needing configured when they installed, kdm and if I remember correctly kmail or something to do with mail. Do these need to be configured a certain way? I told it to use kdm-kde3 as the default login manager and to use SMTP for the mail thingy.

I'm getting the White screen of death LOL(actually it's somewhat gray almost like it's a big blank window or something)


EDIT: I just re-extracted a Vanilla Intrepid ISO and did not apt-get upgrade it. Copied the /var/cache/apt/archives/*.deb packages to the newly extracted directory structure(No way I am redownloading them again), added universe and multiverse, and the PPA, apt-get updated and apt-get installed kubuntu-desktop-kde3....and still get the white screen of death.


I did notice it was wanting to remove certain KDE4 packages. This doesn't make sense either...if KDE4 and KDE3 play nice together now, there's no reason for it to remove them. I'm wondering if it removed something essential.

Hey, sorry for the delay in getting back to you :p

You are getting the white screen of death when you try to log in, correct?  That is, KDM comes up OK?  Did kpersonalizer come up?

KDE3 does play nice with KDE3, but you can't have the KDE4 and KDE3 version of, say, Konsole installed at the same time.  You get into all kinds of trouble (e.g. which version of Konsole should be loaded when I type "konsole" at the command line?) trying to make individual programs coexist.  This does allow the user to install the KDE4 version of any program instead of the KDE3 version, though, and the two window managers are fully functional.

I assume that adding the universe and multiverse repositories fixed the other problems you were having?

Those mail options are not critical.  I'm not sure why they come up at all; I think Hardy must have installed some kind of default configuration behind the scenes when the user installed from a CD.

I'm going to need to replicate that white screen of death and poke around in it a bit.  Can you write a brief outline of the complete procedure you used to install KDE3 into the ISO and then "run" the ISO?

Thanks!

Jeepston,

kpowersave is up; dolphin is coming shortly.

---

### Post by red_team316 on 2008-12-15
Yea, adding universe and multiverse cleared up the dependancy problem. They typically arent active by default but I think Hardy for some reason had them set that way as default.

When Firing up the LiveCD, you do not see KDM when first logging in. It auto-logins as ubuntu. If you can actually get logged in, then log back out you can get to the KDM screen. The problem is that I can't get anywhere near that. I see the ksplash(I'm guessing it's still called that for KDE4), which has the hard drive icon, then the world icon and several other icons load until it fades in the KDE4 large icon. After that it's the white screen of death.

Here is the procedure.
Download Reconstructor 2.8.1 and install it's dependancies on your system.
```

sudo apt-get install squashfs-tools make gcc mkisofs rsync libbogl-dev libusplash-dev dpkg-dev fakeroot apt-utils python python-gtk2 python-glade2

```
[Reconstructor 2.8.1 Download](http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=44&func=view&id=1043&catid=5)
[Dependancies/Using Reconstructor](http://reconstructor.wiki.sourceforge.net/UsingReconstructor)

Fire up reconstructor by:
```

sudo python reconstructor.py

```
Use reconstructor to Extract a Vanilla Intrepid ISO.
Once it has extracted it, click on the APT Tab and check all the main restricted universe multiverse checkboxes. Also add the PPA lines to the textbox. Click Apply. Then click on the terminal button at the bottom of the reconstructor window. This will fire up a chroot terminal. From there, do an apt-get update and then apt-get install kubuntu-desktop-kde3. Once all of the packages have installed, close the chroot window and click Next. Name your ISO however you like and have it create the ISO somewhere on your hard drive. Regardless of if you are building an x86 or x86_64 ISO, tell it to use the standard x86 option(Trust me on this. There is a bug that if you try to build an x86_64 ISO it wont work right. I have already fixed this in an upcoming release, so just make sure you tell it x86 for now, because there is no difference in the mkisofs command nowadays). Once you have the ISO, then just open a terminal in that directory and do:
```

sudo kvm -cdrom kde3test.iso -boot d -m 1024

``` 
the -m switch is for memory so adjust that as neccessary for your system.

Let me know if you have any other questions or get stuck somewhere. You're pretty keen on things so my instructions aren't lined out 100% but you should be able to fill in the gaps. If not, just let me know and I'll help you get it up and running.

---

### Post by rohandhruva on 2008-12-15
Now that the repository is official, and exists side-by-side with KDE4, how can I upgrade from 8.04 to 8.10? I do not want KDE4 on my system at all. I want to upgrade from KDE3 8.04 to KDE3 8.10 - is it possible? What is the correct procedure for that now?

Consider one more case, I want to have a clean fresh installed system. Can I use the alternate CD-ROM to install a "text only" system, and then add the ppa repo, and then "sudo aptitude install kubuntu-kde3-desktop", is that reasonable enough?

---

### Post by iX9 on 2008-12-16
Yes, this seems to be best way to get fresh and cleen KDE3 Intrepid. I have tryed. Dependency errors just the same as beatrace91 had. But I dont give up. When I will have more time, I will try again... Maybe madscientist should try this way too..?

---

### Post by madscientist159 on 2008-12-17
> **iX9 said:**
> Yes, this seems to be best way to get fresh and cleen KDE3 Intrepid. I have tryed. Dependency errors just the same as beatrace91 had. But I dont give up. When I will have more time, I will try again... Maybe madscientist should try this way too..?

iX9, beatrace91,

If you are getting errors, please file a bug at [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net)  Be sure to include:
1. A detailed description of what you are trying to do (are you using the Ubuntu CD, the Kubuntu CD, Synaptic, aptitude, apt-get, etc?)
2. The entire log from the terminal (from the apt-get install command onwards)  You may need to increase the history of your terminal program to be able to capture all this information.

Thanks!

Redteam,

I am currently working on the LiveCD issue.  Looks like KDE4 was trying to start up instead of KDE3; what I can do is get the CD into a working state and then put it up on my Website so you can download it and remaster it properly. :)

---

### Post by red_team316 on 2008-12-17
> **madscientist159 said:**
> 

Redteam,

I am currently working on the LiveCD issue.  Looks like KDE4 was trying to start up instead of KDE3; what I can do is get the CD into a working state and then put it up on my Website so you can download it and remaster it properly. :)
Was it a package issue of some sort? I replied to your PM btw.

---

### Post by iX9 on 2008-12-18
Hi!:p
   I know how to get command line history (.BashHistory file in profile), but how to get the output from entered command ?
   After typing sudo apt-get install kubuntu-desktop-kde3, there is a lot of screens of messages that just scrolls out and I can't see all of errors...

---

### Post by madscientist159 on 2008-12-18
> **red_team316 said:**
> Was it a package issue of some sort? I replied to your PM btw.

More of an interaction between the LiveCD environment (which seems to be quite different from a standard desktop) and KDE3.  I had to remove the KDE4 window manager and customize the /usr/kde3/bin/startkde script to work around these issues.

Yes, I got your PM.  Rebooting did indeed solve the problem!  I am working out a couple minor bugs right now and will probably post the result tomorrow, after verifying installation works as expected.

iX9,

What are you running the apt-get command from (a standard console, xterm, konsole, etc)?  In konsole I know you can extend the history to "unlimited" and copy-paste that into a bug report...

---

### Post by iX9 on 2008-12-18
There is no graphic environment after installation of basic system - no KDE or Gnome. Just command prompt only. I dont know if it is console, terminal or what. I dont think that copy & paste is working.. I need some command to redirect output from screen to file :confused:

---

### Post by madscientist159 on 2008-12-18
> **iX9 said:**
> There is no graphic environment after installation of basic system - no KDE or Gnome. Just command prompt only. I dont know if it is console, terminal or what. I dont think that copy & paste is working.. I need some command to redirect output from screen to file :confused:

OK, I understand what you are doing now.  Use this command:
```
sudo apt-get install kubuntu-desktop-kde3 > aptlog.txt
```
then attach the aptlog.txt to your bug report.

---

### Post by iX9 on 2008-12-19
Thankx, this I need..;)

Little request:  kcpuload, kmyfirewall..:)

---

### Post by red_team316 on 2008-12-19
> **madscientist159 said:**
> More of an interaction between the LiveCD environment (which seems to be quite different from a standard desktop) and KDE3.  I had to remove the KDE4 window manager and customize the /usr/kde3/bin/startkde script to work around these issues.

Yes, I got your PM.  Rebooting did indeed solve the problem!  I am working out a couple minor bugs right now and will probably post the result tomorrow, after verifying installation works as expected.

I'll check out the link in your PM. I can't DL it tonight, but will try over the weekend. Hopefully it will work fine for me too, although once you can confirm it's working 100%, post the steps involved as the same issue will most likely arise on jaunty. I'd just like to be able to reproduce the fix manually also as I still have the /var/cache/apt/archives downloaded from earlier. Also, then if need be, someone can refer back to it later for archival/instructional purposes. 

I'm guessing eventually it can be wrapped into a separate package or modify one of the existing packages to use the workaround/fix in the actual package install process. I'm betting you probably already have something in the works to streamline this.

Liking reconstructor? :D

---

### Post by dentaku65 on 2008-12-19
I got this error today for kdesudo-kde3 package
```
Get:1 http://ppa.launchpad.net intrepid/main kdesudo-kde3 4:2.5.1-3ubuntu5 [38.9kB]
Fetched 38.9kB in 0s (80.6kB/s)
(Reading database ... 264227 files and directories currently installed.)
Preparing to replace kdesudo-kde3 4:2.5.1-3ubuntu2 (using .../kdesudo-kde3_4%3a2.5.1-3ubuntu5_i386.deb) ...
Leaving `diversion of /usr/kde3/bin/kdesu to /usr/kde3/bin/kdesu.distrib by kdesudo-kde3'
Unpacking replacement kdesudo-kde3 ...
dpkg: error processing /var/cache/apt/archives/kdesudo-kde3_4%3a2.5.1-3ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/kdesu-kde3.1.gz', which is also in package kdebase-kde3-bin
/var/lib/dpkg/tmp.ci/postrm: didn't understand being called with `abort-upgrade'
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdesudo-kde3_4%3a2.5.1-3ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Anyone?

---

### Post by madscientist159 on 2008-12-19
> **dentaku65 said:**
> I got this error today for kdesudo-kde3 package
```
Get:1 http://ppa.launchpad.net intrepid/main kdesudo-kde3 4:2.5.1-3ubuntu5 [38.9kB]
Fetched 38.9kB in 0s (80.6kB/s)
(Reading database ... 264227 files and directories currently installed.)
Preparing to replace kdesudo-kde3 4:2.5.1-3ubuntu2 (using .../kdesudo-kde3_4%3a2.5.1-3ubuntu5_i386.deb) ...
Leaving `diversion of /usr/kde3/bin/kdesu to /usr/kde3/bin/kdesu.distrib by kdesudo-kde3'
Unpacking replacement kdesudo-kde3 ...
dpkg: error processing /var/cache/apt/archives/kdesudo-kde3_4%3a2.5.1-3ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/kdesu-kde3.1.gz', which is also in package kdebase-kde3-bin
/var/lib/dpkg/tmp.ci/postrm: didn't understand being called with `abort-upgrade'
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdesudo-kde3_4%3a2.5.1-3ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Anyone?

I'm on it....sorry! (trying to fix a different problem, broke it for everyone... :rolleyes: )

---

### Post by madscientist159 on 2008-12-19
> **red_team316 said:**
> I'll check out the link in your PM. I can't DL it tonight, but will try over the weekend. Hopefully it will work fine for me too, although once you can confirm it's working 100%, post the steps involved as the same issue will most likely arise on jaunty. I'd just like to be able to reproduce the fix manually also as I still have the /var/cache/apt/archives downloaded from earlier. Also, then if need be, someone can refer back to it later for archival/instructional purposes. 

I'm guessing eventually it can be wrapped into a separate package or modify one of the existing packages to use the workaround/fix in the actual package install process. I'm betting you probably already have something in the works to streamline this.

Liking reconstructor? :D

Yes, reconstructor is very nice! :p  A lot easier than the old method...

My changes were:
1. Get rid of the KDE4 window manager (remove the package that contains /usr/share/xsessions/kde.desktop).  This gets you past the white screen of death.  The KDE4-based Ubiquity installer should stay, of course.
2. Modify the /usr/kde3/bin/startkde script to hard code /usr/kde3/bin into the path and also bypass kstartupconfig & friends in that script--it doesn't work properly in the LiveCD for some reason.  This will get you past the "can't start kstartupconfig" message.
3. Update everything to the latest version (not required, just thought I might as well--I have a mirror of Ubuntu/Kubuntu locally so it took all of 15 minutes ;) )

Because the change was so trivial I don't have plans to create a package--besides, if I added a package that did the above change to startkde, then it would be replicated onto the installed system with unknown consequences.

---

### Post by red_team316 on 2008-12-21
> **madscientist159 said:**
> 
Because the change was so trivial I don't have plans to create a package--besides, if I added a package that did the above change to startkde, then it would be replicated onto the installed system with unknown consequences.
I do not think you are necessarily correct about the replication part. Take a look at the reconstructor/remaster/casper directory. It contains 2 manifest files. They are lists of packages to use on the LiveCD and the other is the packages that actually get installed to the desktop/system. I'm sure this could be used in some way, and or with a script that removes the package afterwards.

Well, at the very least it would be nice to be able to create a reconstructor module/bash script that handles this. Maybe this would be a better option than a package. Unless I am missing something, the script would be something like this:
(Please forgive me if the package names or something else is amiss here as I am typing this off the top of my head. Please feel free to clean it up proper if you wish. I figure you should be given author credit due to all the work you've done so far)
```

#!/bin/sh
#
# Reconstructor Module - KDE3 Installation
#	Copyright (c) 2008  Timothy Pearson
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

RMOD_ENGINE=1.0
RMOD_CATEGORY='Software'
RMOD_SUBCATEGORY='Administration'
RMOD_NAME='KDE3'
RMOD_AUTHOR='Timothy Pearson'
RMOD_VERSION=0.1
RMOD_DESCRIPTION='Installs KDE3 in Intrepid Ibex or later which only have KDE4'
RMOD_RUN_IN_CHROOT=True
RMOD_UPDATE_URL='http://reconstructor.aperantis.com/update/modules/'

echo '#KDE3 Intrepid PPA
deb http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main' >> /etc/apt/sources.list.d/kde3.list
apt-get update
apt-get upgrade
apt-get remove kwin #KDE4 version
apt-get install -y kubuntu-desktop-kde3 #-y because no GPG key, --allow-unauthenticated may also be needed
replace lines in startkde script(are you sure this shouldn't be /usr/bin/startkde?)
apt-get clean
apt-get autoclean
apt-get autoremove

```

BTW, Can you do an install of your ISO image on a virtual partition(or real partition) to confirm that your KDE3 repository DOES NOT show up in the sources.list upon install.
See this thread for further information. I'm working to squash yet another bug in implementation and I think your ISO may suffer from this. Which is why the code above is structured with the repo lines being put into sources.list.d directory rather than the actual sources.list file.
[http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&func=view&id=1202&catid=3#1202](http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&func=view&id=1202&catid=3#1202)

Sorry, I haven't gotten to download it yet. I've got multiple things to do before the 25th and still haven't gotten time.

---

### Post by madscientist159 on 2008-12-22
Redteam,

Thank you for the information and script.:)

> **red_team316 said:**
> ...I've got multiple things to do before the 25th and still haven't gotten time.

I definitely know the feeling...I probably won't be able to do anything major until after the 25th myself.

At least new packaging requests and bug reports have died down! :P

---

### Post by Paul S on 2008-12-23
Great job!

I just did a gnome 8.10 install and installed kde3 without ever installing kde4 first.

> **madscientist159 said:**
> 
sudo apt-get -d -y install kubuntu-desktop-kde3 ark-kde3 ksystemlog-kde3 kmix-kde3 konq-plugins-kde3 ksnapshot-kde3 konqueror-kde3



works, but still leaves a lot of kde3 uninstalled.  And that's where I ran into dependency hell.  I still have some stuff that I can't get to install.  It seems to involve kde-style-qtcurve and kdelibs4c2a.  See attached bug info.

---

### Post by cmreigrut on 2008-12-27
First off, brilliant work!  KDE4 on my Thinkpad A31p was a disaster.

But something seems amiss with my install.  When I attempt to do 

```
kdesu kate
```

I get a command not found.  And 

```
kdesu env
```

shows 
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
```

What am I missing here?

---

### Post by red_team316 on 2008-12-27
> **cmreigrut said:**
> First off, brilliant work!  KDE4 on my Thinkpad A31p was a disaster.

But something seems amiss with my install.  When I attempt to do 

```
kdesu kate
```

I get a command not found.  And 

```
kdesu env
```

shows 
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
```

What am I missing here?
Apparently kate is not installed for some reason. Works fine on my hardy-box.

Try apt-get install kate (KDE4 version)
or apt-get install kate-kde3 (preferably since it is KDE3 we are looking for)

kdesu env has nothing to do with kate. You paths seem fine to me...but I'm not on a KDE Intrepid-box right now. There is alot going on behind the scenes as far as KDE3 packages so maybe there is an appended path, I'm not sure...

---

### Post by tpdi on 2008-12-27
I installed a freah copy of Ubuntu 8.10 (Intrepid Ibex), using the Eeebuntu Base iso.

This is a Ubuntu install. I then installed KDE, which gav me KDE 4.1, hich horrified me. Googling led me to this thread.

I added the sources to my sources.list, and ran 
sudo apt-get install kubuntu-desktop-kde3

This worked but left my menus in poor shape.

So I did a clean re-install of the iso, and ran 
sudo apt-get install kubuntu-desktop-kde3

This failed:
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a4.1.3-0ubuntu1~intrepid1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.1.3-0ubuntu1~intrepid1_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/kde-information.menu', which is also in package kdebase-data-kde3

I've since been in a cycle of: installing, getting broken packages, removing the broken packages, repeat.

I also notice that installing kubuntu-desktop-kde3 brings in kde4 packages:

root@mybox:~# sudo apt-get install kubuntu-desktop-kde3
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  gdebi-kde gwenview install-package kdebase-runtime **kdebase-runtime-bin-kde4** kdebase-runtime-data kdesudo kwin-style-crystal language-selector-qt libkdecorations4
  libkipi5 python-kde4 software-properties-kde

What am I doing wrong? Can I get KDE3 on Ubuntu 8.10? If I do, will I be in a continuing dependency hell? Should I just install Hardy?

(Parenthetically, if OSS is all about choice, why doesn't KDE make it possible to choose KDE 3.5 or 4.1? In theory, I can chose from any number of window managers, why should my choice of a core limit my choices in window managers? This is all very frustrating.)

Thanks for any help.

---

### Post by cmreigrut on 2008-12-27
> **red_team316 said:**
> Apparently kate is not installed for some reason. Works fine on my hardy-box.

Try apt-get install kate (KDE4 version)
or apt-get install kate-kde3 (preferably since it is KDE3 we are looking for)

kdesu env has nothing to do with kate. You paths seem fine to me...but I'm not on a KDE Intrepid-box right now. There is alot going on behind the scenes as far as KDE3 packages so maybe there is an appended path, I'm not sure...

No, kate itself works just fine--just not via sudo.  The problem is that all of the KDE tools are in /usr/kde3/bin/, and yet kdesudo doesn't have that in its path (which, I believe, is hardcoded at compile time) as you can see from the results of kdesu env above.

So either there's been a change recently (I only installed it yesterday), or it's always been broken that way, or I'm missing something.

---

### Post by taisao on 2008-12-28
> **cmreigrut said:**
> No, kate itself works just fine--just not via sudo.  The problem is that all of the KDE tools are in /usr/kde3/bin/, and yet kdesudo doesn't have that in its path (which, I believe, is hardcoded at compile time) as you can see from the results of kdesu env above.

So either there's been a change recently (I only installed it yesterday), or it's always been broken that way, or I'm missing something.

I'm having the same problem. When I want to start kate with superuser access I have to give the path of kate. That's ```
kdesu /usr/kde3/bin/kate

```

---

### Post by madscientist159 on 2008-12-28
Hey, sorry for my absence, I was busy with the holidays.  I will try to answer your questions in turn below.:)

> **Paul S said:**
> Great job!

I just did a gnome 8.10 install and installed kde3 without ever installing kde4 first.




works, but still leaves a lot of kde3 uninstalled.  And that's where I ran into dependency hell.  I still have some stuff that I can't get to install.  It seems to involve kde-style-qtcurve and kdelibs4c2a.  See attached bug info.

You will need to append a -kde3 suffix onto any KDE3 package that you want to install.  For example, kde-style-qtcurve becomes kde-style-qtcurve-kde3

> **tpdi said:**
> I installed a freah copy of Ubuntu 8.10 (Intrepid Ibex), using the Eeebuntu Base iso.

This is a Ubuntu install. I then installed KDE, which gav me KDE 4.1, hich horrified me. Googling led me to this thread.

I added the sources to my sources.list, and ran 
sudo apt-get install kubuntu-desktop-kde3

This worked but left my menus in poor shape.

So I did a clean re-install of the iso, and ran 
sudo apt-get install kubuntu-desktop-kde3

This failed:
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a4.1.3-0ubuntu1~intrepid1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.1.3-0ubuntu1~intrepid1_all.deb (--unpack):
 trying to overwrite `/etc/xdg/menus/kde-information.menu', which is also in package kdebase-data-kde3

I've since been in a cycle of: installing, getting broken packages, removing the broken packages, repeat.

I also notice that installing kubuntu-desktop-kde3 brings in kde4 packages:

root@mybox:~# sudo apt-get install kubuntu-desktop-kde3
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  gdebi-kde gwenview install-package kdebase-runtime **kdebase-runtime-bin-kde4** kdebase-runtime-data kdesudo kwin-style-crystal language-selector-qt libkdecorations4
  libkipi5 python-kde4 software-properties-kde

What am I doing wrong? Can I get KDE3 on Ubuntu 8.10? If I do, will I be in a continuing dependency hell? Should I just install Hardy?

(Parenthetically, if OSS is all about choice, why doesn't KDE make it possible to choose KDE 3.5 or 4.1? In theory, I can chose from any number of window managers, why should my choice of a core limit my choices in window managers? This is all very frustrating.)

Thanks for any help.

You are not doing anything wrong; this is a problem on my end.  Theoretically kdebase-data-kde3 shuld be diverting all of the conflicting files of kdebase-runtime-data, but apparently it is not.  Try it with a Kubuntu instead of an Ubuntu install; I bet it will work for you while I fix the issue.  Incidentally, KDE3 does bring in a few data files from KDE4, but it's nothing to worry about.

> **taisao said:**
> I'm having the same problem. When I want to start kate with superuser access I have to give the path of kate. That's ```
kdesu /usr/kde3/bin/kate

```

This is unfortunately a known issue.  Can you (or anyone) suggest a proper way to add /usr/kde3/bin to the system-wide path when kdelibs4c2a-kde3 is installed?  I don't know how to do that... :(

---

### Post by cmreigrut on 2008-12-28
> **madscientist159 said:**
> 
This is unfortunately a known issue.  Can you (or anyone) suggest a proper way to add /usr/kde3/bin to the system-wide path when kdelibs4c2a-kde3 is installed?  I don't know how to do that... :(

From what I've read, kdesudo (like regular sudo) has its path defined at compile time--they don't even read the system path.  This is said to be a "security measure" to keep someone from being able to prepend stuff to the path and preempt existing applications (imagine if you could add /home/hackers/mystuff to the beginning of the path, and put an executable in that directory called kate that was malware).

So it sounds like you have to modify it prior to the compile.  Either that, or we need to symlink all of the stuff in /usr/kde3/bin into /usr/bin.

P.S. Sounds like there was/is an issue with KDE4 doing exactly the same thing:  [https://bugs.launchpad.net/ubuntu/+source/kdesudo-kde4/+bug/191264](https://bugs.launchpad.net/ubuntu/+source/kdesudo-kde4/+bug/191264)

---

### Post by taisao on 2008-12-28
> **cmreigrut said:**
> From what I've read, kdesudo (like regular sudo) has its path defined at compile time--they don't even read the system path.  This is said to be a "security measure" to keep someone from being able to prepend stuff to the path and preempt existing applications (imagine if you could add /home/hackers/mystuff to the beginning of the path, and put an executable in that directory called kate that was malware).

So it sounds like you have to modify it prior to the compile.  Either that, or we need to symlink all of the stuff in /usr/kde3/bin into /usr/bin.

P.S. Sounds like there was/is an issue with KDE4 doing exactly the same thing:  [https://bugs.launchpad.net/ubuntu/+source/kdesudo-kde4/+bug/191264](https://bugs.launchpad.net/ubuntu/+source/kdesudo-kde4/+bug/191264)

Thanks.
The workaround works for me, [https://bugs.launchpad.net/ubuntu/+source/kdesudo-kde4/+bug/191264/comments/25](https://bugs.launchpad.net/ubuntu/+source/kdesudo-kde4/+bug/191264/comments/25)

---

### Post by tkornel on 2008-12-28
Hi all! I have installed the packages and running now kde3, but I need also kbarcode(-kde3). At the moment it's not in the repo. Could you make it please?

Thanks

Kornel

---

### Post by madscientist159 on 2008-12-29
I have made two changes to the repository that should make things easier:

1. If you install sudo-kde3, ```
sudo <kde3 program name>
``` will now work.  If you want to make sure I didn't insert any backdoors into sudo at the same time, just run a diff against the sudo source code from the PPA and the sudo source code from Ubuntu official--the only difference is the secure_path compile flag :D

2. If the -kde3 package for a program is not available, you can get around this by installing kdelibs4c2a.  This is a metapackage that will override the official kdelibs4c2a, allowing installation of programs such as openoffice.org-kde.  Please heed the warning that is in the description of that metapackage, however:
```
Virtual package to provide kdelibs4c2a to those applications that still need it
Please use the -kde3 variants where they exist instead; [B]there is no gaurantee that
the non -kde3 packages will continue to exist in new releases of Kubuntu[/B]
```

Enjoy!

---

### Post by tkornel on 2008-12-30
Thanks a lot!
I have installed now the kdelibs4c2a package than kbarcode and it works.

Happy New Year!

---

### Post by bimaljr on 2008-12-30
> I understand at large the reasons why Kubuntu team make the decision to switch the WM into KDE 4 and to do not include KDE 3 anymore; in my view this is a simply wrong decision, but it's ok.

I am fully Agree. I think it's too early to remove KDE3.

btw... thanks to all of you.. I am downloading KDE3 in my Ubuntu 8.10 system and will report bug if any.

---

### Post by cacycleworks on 2008-12-30
I, too, do not like hardy ... nor do I like gnome. 

I tried the below steps (note that you want sudo apt-get install kubuntu-desktop-kde3) but it broke. I'm currently in the middle of updating hardy ubuntu so that I can next get kubuntu-desktop (8.04, so is kde3)

I am using x86_64 / AMD64 versions, so perhaps that is the issue?? I don't know, but I wish there was a way to choose to permanently store packages downloaded with each of my installs, because even with a good 300~800 kB/sec download, there is a LOT of waiting as well as wasting someone's bandwidth when I install kubuntu 8.10, try the kde3, then reinstall ubuntu 8.04 and reinstall apt-get install kubuntu-desktop

I did log in again to the 8.10 cli system I was stuck with to get /var/log/apt/term.log...

On the first BIG go everything was ok ... it looked like it was going to work. Then died at:
```
Unpacking kwin-style-crystal (from .../kwin-style-crystal_2.0.1-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid5_all.deb
```

I then tried aptitude with its recommended uninstall something then reinstall something else... which gave the exact same results as simply trying to run apt-get -f install :
```
(Reading database ... 68598 files and directories currently installed.)

Unpacking kdebase-data-kde3 (from .../kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid5_all.deb) ...

Leaving `diversion of /etc/xdg/menus/kde-information.menu to /etc/xdg/menus.kde4/kde-information.menu by kdebase-runtime-data-common-kde3'

dpkg: error processing /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid5_all.deb (--unpack):

 trying to overwrite `/etc/xdg/menus/kde-information.menu', which is also in package kdebase-runtime-data

dpkg-deb: subprocess paste killed by signal (Broken pipe)

Errors were encountered while processing:

 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid5_all.deb
```

I even tried renaming that file (didn't do anything).

I believe that until kubuntu officially offers KDE3 as an alternative to KDE4, I'm stuck with Hardy / 8.04 or finding a new distro. I have too many work processes tied to KDE3 using khotkeys, which is absolutely broken in KDE4. 

That KDE4 was coming didn't seem like a problem until I actually tried it. It's NOTHING like KDE3. I don't get the plasma thing and they broke khotkeys, scrolling the mouse on desktop (why bother with different desktops?), and menus and options I am used to are all missing. And there's nothing as amazing as being trapped in the launcher menu because you didn't pick something.

I'll keep an eye out here and hope for the best.

Thanks for the KDE3 work ... I wish that kubuntu would embrace it.

:) Chris

> **iX9 said:**
> **Hi!**
Maybe someone will be interest *my* way:
I dont like to install Hardy, and dont like to install Gnome...
So, :
1.) I have downloaded Kubuntu 8.10 *ALTERNATE* CD.
2.) Boot from this LiveCD and right after language selection, press F4 and select *"Install Command-line system only"*.
3.) Setup other things and install system.
4.) After install, log in and add madscientist159's repository in sources.list.
5.) sudo apt-get update.
6.) **sudo apt-get install kde3.**

Now you have pure Intrepid KDE3. ):P

---

### Post by sandyd on 2008-12-30
for some reason, when installing kde3, kwin-style-crystal needs to be installed. However, kwin-style-crystal removes the kde3 runtime data (kdebase-data-kde3) which is an impossibility. 
language-selector-qt and software-properties-kde are also broken. Help please?

EDIT: It should be kwin-style-crystal-kde3 that is installed, not kwin-style-crystal

Thanks!

---

### Post by iX9 on 2008-12-31
**Hi!** :p

Here is my trying *step-by-step*:

1. Download & Burn **kubuntu-8.10-alternate-i386.iso**.
2. Boot from this LiveCD, select language, press **F4**, change to "Install command line system only", install the system.
3. Edit /etc/sources.list to enable other repozitories and KDE3 repo:
[[**sources.list**]("http://ident.kvalitne.cz/sources.list")]

4. Sudo apt-get update.
5. Sudo apt-get upgrade | tee upgrade.log   (this downloads and uptates about 40 packages):
[[**upgrade.log**]("http://ident.kvalitne.cz/upgrade.log")]

5. Restart system.
6. Sudo apt-get install kubuntu-desktop-kde3 | tee kde.log

Last command downloads 781 packages including many KDE4 files and fails:
[[**kde.log**]("http://ident.kvalitne.cz/kde.log")]

After that, trying this:  sudo apt-get -f install | tee install-f.log
[[**install-f.log**]("http://ident.kvalitne.cz/install-f.log")]

And again:  sudo apt-get install kubuntu-desktop-kde3 | tee kde2.log
[[**kde2.log**]("http://ident.kvalitne.cz/kde2.log")]

Then I have tryed many things and get this:
[[**111.log**]("http://ident.kvalitne.cz/111.log")]
Packages listed on the end of this logfile, I must forced by **dpkg -i --force-all** one by one.. and then - finally  ....  KDE is UP!
Please check my packagelist if something basic or important is missing:
[[**packagelist0.gz**]("http://ident.kvalitne.cz/packagelist0.gz")]

***So this way is working, you could have just KDE3 from begining on Intrepid! No KDE4, no GNOME!***

Something about  kubuntu-desktop-kde3:  It depends on:
kdelibs5-data
kdelibs-bin
kdelibs5
kdebase-runtime-bin-kde4
kdebase-runtime-data-common
kdebase-runtime-data
kde-icons-oxygen
kdebase-runtime
python-kde4
kdesudo
gdebi-kde
install-package
khelpcenter4_
libkdecorations4
kwin-style-crystal
language-selector-qt
software-properties-kde
libkipi-common
libkipi5
gwenview

Are this packages necessary? I dont have installed them or have -kde3 versions. It also want to remove digikam-kde3 and lipkipi0-kde3.


**Last thing:**
Two most important packages I miss, Tim:
[B]language-pack-kde-cs
language-pack-kde-cs-base[/B]
I can't normaly use this KDE if I can't switch to my language :(:(:(

---

### Post by iX9 on 2008-12-31
Hi:D, one more package needed:  gtk-chtheme*-kde3*  (utility to change bad-looks of apps like synaptic).

---

### Post by Paul S on 2008-12-31
> **cacycleworks said:**
> 
I am using x86_64 / AMD64 versions, so perhaps that is the issue?? I don't know, but I wish there was a way to choose to permanently store packages downloaded with each of my installs, because even with a good 300~800 

I'm running on 64 bit with no problem so far, but I did a clean install rather than upgrade.

You can copy your downloaded debs from /var/cache/apt/archives onto a usb stick, then copy them back into the new installation's /var/cache/apt/archives directory.  Keep in mind, it's huge files to move and move back, so it's still not all that quick.

regards,
27

---

### Post by pmocek on 2008-12-31
After upgrading a Gnome desktop system from Hardy to Intrepid, I found the one KDE application I use, Akregator, to be unusable.  It started, but ran extremely slowly and eventually reported errors about not being able to write to a file (one that existed and had permissions set correctly).  On a similar machine, Akregator now crashes with SIGABRT.

I added the KDE3 repository Madscientist159 created to my APT sources and installed akregator-kde3 using aptitude.  Running /usr/kde3/bin/akregator then resulted in an error being reported and the app failed to start.  I then installed kubuntu-kde3-desktop and dependencies.

Now, when I run Akregator, it prints:

```
/usr/kde3/bin/akregator: error while loading shared libraries:
libqui.so.1: cannot open shared object file: No such file or directory
```

No libqui exists on this machine and I can find no reference to any such library in the Ubuntu repositories.

---

### Post by pmocek on 2008-12-31
Update:

libqui.so.1 is provided by package [libqt3-mt]("http://packages.ubuntu.com/intrepid/i386/libqt3-mt/filelist").  My installation of that package has only the following files:

```
$ dlocate libqt3-mt
libqt3-mt: /.
libqt3-mt: /etc
libqt3-mt: /etc/qt3
libqt3-mt: /etc/qt3/qtrc
libqt3-mt: /etc/qt3/qt_plugins_3.3rc
libqt3-mt: /usr
libqt3-mt: /usr/lib
libqt3-mt: /usr/lib/libqt-mt.so.3.3.8
```

I used [debsums]("http://packages.ubuntu.com/intrepid/debsums") to verify integrity of installed files and found lots of problems.  **I suspect that the problem is related to a corrupted installation, not to the KDE3 packages themselves.**

For more on using debsums to recover from similar trouble, see [Arthur de Jong's "crash recovery using debsums" page]("http://ch.tudelft.nl/~arthur/recovery.html").

---

### Post by red_team316 on 2009-01-03
madscientist:
I am finally getting around to downloading your ISO. I will test it, but it would be really beneficial if we can get the bash script finished. I (as well as others) would really benefit from being able to know create one from scratch, especially the kdm/kwin/startkde parts (as would be needed for jaunty too). Have you had any time to look into it further? I know everyone is still squashing bugs, but that shouldn't matter if it is stable enough to get a working ISO from.

---

### Post by cmreigrut on 2009-01-05
madscientist:

Can you add wlassistant to the repository?  It doesn't exist in the Intrepid repositories any more (perhaps because it claims a dependence on KDE 3.5), and knetworkmanager sucks for wifi, IMHO.

---

### Post by madscientist159 on 2009-01-05
> **red_team316 said:**
> madscientist:
I am finally getting around to downloading your ISO. I will test it, but it would be really beneficial if we can get the bash script finished. I (as well as others) would really benefit from being able to know create one from scratch, especially the kdm/kwin/startkde parts (as would be needed for jaunty too). Have you had any time to look into it further? I know everyone is still squashing bugs, but that shouldn't matter if it is stable enough to get a working ISO from.

Sorry I hadn't gotten this to you sooner...I have not thoroughly tested it yet, would you mind testing it for me? :)

Thanks,

Tim

```

#!/bin/sh
#
# Reconstructor Module - KDE3 Installation
#	Copyright (c) 2008  Timothy Pearson
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

RMOD_ENGINE=1.0
RMOD_CATEGORY='Software'
RMOD_SUBCATEGORY='Administration'
RMOD_NAME='KDE3'
RMOD_AUTHOR='Timothy Pearson'
RMOD_VERSION=0.1
RMOD_DESCRIPTION='Installs KDE3 in Intrepid Ibex or later which only have KDE4'
RMOD_RUN_IN_CHROOT=True
RMOD_UPDATE_URL='http://reconstructor.aperantis.com/update/modules/'

# Create the pach file for startkde
echo '--- /usr/kde3/bin/startkde
+++ /usr/kde3/bin/startkde
@@ -1,8 +1,11 @@
 #!/bin/sh
 #
 #  DEFAULT KDE STARTUP SCRIPT ( KDE-3.5.10 )
+#  MODIFIED FOR LIVECD ENVIRONMENT
 #

+export PATH=/usr/kde3/bin:${PATH}
+
 # When the X server dies we get a HUP signal from xinit. We must ignore it
 # because we still need to do some cleanup.
 trap 'echo GOT SIGHUP' HUP
@@ -81,11 +84,7 @@
 kcmrandrrc [Screen3]
 kcmfonts General forceFontDPI 0
 EOF
-kstartupconfig
-if test $? -ne 0; then
-    xmessage -geometry 500x100 "Could not start kstartupconfig. Check your installation."
-fi
-. $kdehome/share/config/startupconfig
+/usr/kde/bin/kstartupconfig

 # XCursor mouse theme needs to be applied here to work even for kded or ksmserver
 if test -n "$kcminputrc_mouse_cursortheme" -o -n "$kcminputrc_mouse_cursorsize" ; then' >> /startkde.patch

echo '#KDE3 Intrepid PPA
deb http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main' >> /etc/apt/sources.list.d/kde3.list
apt-get update
apt-get upgrade
apt-get remove -y kwin kdebase-workspace-data 	# KDE4 window manager and friends
apt-get install -y kubuntu-desktop-kde3 patch 	#-y because no GPG key, --allow-unauthenticated may also be needed, patch needed for below
patch -p0 < /startkde.patch
rm /startkde.patch
apt-get clean
apt-get autoclean
apt-get autoremove

```

---

### Post by Aenea on 2009-01-07
Hi there all!

I'm a Kubuntu user for a while now and was, like most of us, horrified with the 8.10 release 'cos of kde4. Mind you, I like the way things are going with it, but it was indeed a bit premature to drop kde3 support completely for it.

So I never upgraded to 8.10 'cos of it and I found this thread a few days ago. And love it! 

I installed gnome and did the upgrade from there, took a while but worked nicely. Then I followed the rest of the instructions of the 1st post and all seemed to work. 

System feeled snappier than before, allthough there were still a few minor problems. 1) Whenever I started an application and you get the mouse pointer with the app's icon jumping up & down thingy I saw 2 icons jumping up and down, both the kde3 & the kde4 version of it if the app had different versions for it! 2) Switching between virtual desktops became sluggish after using the system for a while 3) It sometimes took a while before the kde menu opened and some other minor details.

Well, if people have the same problems as I did, I think I managed to solve them.

- I removed some redundant/left-over files from /etc/X11/Xsession.d, namely 80ubuntu-kde3-xmodmap, 80ubuntu-xmodmap and kept 80kubuntu-xmodmap (the previous one I presume). Also removed: 70pulseaudio & 40guidance-displayconfig_restore
- Did an apt-get remove kwin kdebase-workspace-data
- And an apt-get remove kdebase-runtime-bin-kde4

And now it all seems to work even better, switching to virt. desktops is better, no more double app icons jumping, etc. And less .xsession-errors...

Hope this helps someone!

And Tim & all the others: BIG THANKS!

Aenea

---

### Post by red_team316 on 2009-01-07
> **madscientist159 said:**
> Sorry I hadn't gotten this to you sooner...I have not thoroughly tested it yet, would you mind testing it for me? :)

Thanks,

Tim

```

#!/bin/sh
#
# Reconstructor Module - KDE3 Installation
#	Copyright (c) 2008  Timothy Pearson
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

RMOD_ENGINE=1.0
RMOD_CATEGORY='Software'
RMOD_SUBCATEGORY='Administration'
RMOD_NAME='KDE3'
RMOD_AUTHOR='Timothy Pearson'
RMOD_VERSION=0.1
RMOD_DESCRIPTION='Installs KDE3 in Intrepid Ibex or later which only have KDE4'
RMOD_RUN_IN_CHROOT=True
RMOD_UPDATE_URL='http://reconstructor.aperantis.com/update/modules/'

# Create the pach file for startkde
echo '--- /usr/kde3/bin/startkde
+++ /usr/kde3/bin/startkde
@@ -1,8 +1,11 @@
 #!/bin/sh
 #
 #  DEFAULT KDE STARTUP SCRIPT ( KDE-3.5.10 )
+#  MODIFIED FOR LIVECD ENVIRONMENT
 #

+export PATH=/usr/kde3/bin:${PATH}
+
 # When the X server dies we get a HUP signal from xinit. We must ignore it
 # because we still need to do some cleanup.
 trap 'echo GOT SIGHUP' HUP
@@ -81,11 +84,7 @@
 kcmrandrrc [Screen3]
 kcmfonts General forceFontDPI 0
 EOF
-kstartupconfig
-if test $? -ne 0; then
-    xmessage -geometry 500x100 "Could not start kstartupconfig. Check your installation."
-fi
-. $kdehome/share/config/startupconfig
+/usr/kde/bin/kstartupconfig

 # XCursor mouse theme needs to be applied here to work even for kded or ksmserver
 if test -n "$kcminputrc_mouse_cursortheme" -o -n "$kcminputrc_mouse_cursorsize" ; then' >> /startkde.patch

echo '#KDE3 Intrepid PPA
deb http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main' >> /etc/apt/sources.list.d/kde3.list
apt-get update
apt-get upgrade
apt-get remove -y kwin kdebase-workspace-data 	# KDE4 window manager and friends
apt-get install -y kubuntu-desktop-kde3 patch 	#-y because no GPG key, --allow-unauthenticated may also be needed, patch needed for below
patch -p0 < /startkde.patch
rm /startkde.patch
apt-get clean
apt-get autoclean
apt-get autoremove

```

I most certainly will :D As far as thourghally tested, I hope it's to a point that it I can get a testable ISO like the one you made. Doing a diff on the modified files should confirm that they match your ISO or not. I'm not real amazing at bash but wouldn't the echo include the diff lines in the file?  



My thoughts on your ISO...
It worked. I tested in KVM/QEMU and one of the first things I noticed that brought tears to my eyes was the fact that when you right click on the taskbar>configure panel>menu, that the optional menus list does not have duplicates of each entry. This is something that has irked me about ubuntu's implementation for quite some time, and it only occurs when running the liveCD. Hardy and previous releases all had it. I'm guessing that since Intrepid got rid of all of the kde3 stuff, that something is gone now that was causing the bug or either you fixed it yourself.

I cannot logout when using the LiveCD. When I try to, it just freezes. I tested a vanilla intrepid ISO too so it seems that it is an Intrepid bug. On a Hardy ISO, you can logout and relogin just fine.

The fact that you have the Intrepid artwork and mouse scheme going is pleasing. Since it didn't whitescreen, I finally got to see the fruits of your labor rather than my chroot terminal all the time :)

I like that konqueror defaults as the file manager. One less inode to customize.

There are several items in the lost and found in kmenu. I'm guessing you just haven't gotten around to properly locating them in a corresponding package?

When going into the window decoration kcontrol module, KDE 2 is listed as the default window decoration, but in fact it is Plastik. A small but possibly annoying bug.

When moving the mouse from the desktop to a window, it changes back to a standard mouse scheme, but then move it off of the window back to the desktop and you get the kde4 mouse scheme again. Thats odd.

The ISO/CDROM description is Ubuntu Custom and the live CD user is called ubuntu. There is nothing wrong with this but I always found it funny that kubuntu CD's you always log in as ubuntu. These are obviously items that reconstructor can customize easily but in a final release, these need to be tweaked.

The home and media folder icons when viewed in the / directory are the kde4 icons. It seems odd that everything else is crystal-svg like it should be but maybe kde4 is overriding them somehow. When Changing the icon them to oxygen, it seems that the desktop folder holds the kde3 icon. When changing back to crystal-svg, the media and home folders are still defaulting to kde4 ones. So that needs to be fixed so the kde3 icons show. The system menu icon shows the proper home and media icons but konqueror broser doesn't...

The Show Desktop applet doesn't appear to be in the taskbar by default. Another cosmetic thing. It appears that the kubuntu-default-settings are not anywhere near what they should be. kickerrc isn't even in
/usr/share/kubuntu-default-settings/kde-profile/default/share/config/
I think more work needs done on that package. I would definitely check to see if the double settings come back from the reinclusion of them. If so, then we'll need to figure out what configuration it is as I'd not like to deliberately introduce a regression :P albeit minor. Also, you'll notice alot of the lesser-visual-impairment, etc... folders are not in /usr/share/kubuntu-default-settings/kde-profile/
So the package still needs some work.

/etc/apt/sources.list.d - where the KDE3 PPA sources list should reside. I mentioned this earlier, but the bash script will properly take care of that.

There's alot of stuff I couldn't test yet, such as sound or burning through KVM but overall, I feel that even your ISO is almost close enough for me to switch to intrepid full time :D I'll definitely install it on a separate partition later for further testing.

---

### Post by gafy on 2009-01-07
Hello and thank you for allowing 8.10 to run kde3, I share your feeling that it is very important...
I'd like to use digikam with kipi-plugins. there's no -kde3 version of the package kipi-plugins (which requires uninstallation of 
digikam-kde3
libkipi0-kde3
libkipi0-kde3-dev

Maybe I messed up by my probably unclean installation of kde3 over 8.10, or maybe this package is missing. In this case, may I ask you to see if somthing can be done?
Thanks again, 
Gafy

---

### Post by elliottm on 2009-01-08
I tried following the "alternate install cdrom" steps on a virtualbox VM, and run into an error.

Here are the steps I took:

1. insert a kubuntu intrepid amd64 alternate CD
2. press f4 to install command line system
3. when it comes up, apt-get update and apt-get upgrade, then reboot
4. add the kde3 repositories, then apt-get get update
5. install kubuntu-desktop-kde3 (warning: when following this method, you download about 750mb of packages, so if you're doing it more than once, try to save the package caches when reinstalling.)
6. select "kdm-kde3 and "no configuration for display manager and mail
7. reboot

Here, the login screen shows up. I enter my name and password, and an error comes up saying "could not start kstartupconfig, check your installation." when you click OK, the x server restarts. I selected "console login", attempted to run kstartupconfig from the console, and was told that it was a part of a package that was not installed (kdelibs4c2a). I tried installing both kdelibs4c2a and kdelibs4c2a-kde3, and i get the same error. I'm not sure what to do now.

---

### Post by cacycleworks on 2009-01-08
I have been watching this thread and as soon as I see a post like the one above -- only successful, I will immediately try it on my laptop. 

btw - I would appreciate a link to instructions on how to copy the cache to my /home (that partition doesn't get formatted ever) and then how to point apt to it...  :) And if the time comes, I will google to find said instructions and reply with the link. 

Thanks for your great work! I hope kubuntu will officially support KDE3! If not, I am prepared to stay with 8.04 until 2011.

:) Chris

---

### Post by elliottm on 2009-01-09
> **cacycleworks said:**
> btw - I would appreciate a link to instructions on how to copy the cache to my /home (that partition doesn't get formatted ever) and then how to point apt to it...

cp /var/cache/apt /home/myname/mydirectory -R

I wouldn't bother trying to point your package manager at that directory. Instead, copy it back once you reinstall. Just remember/write down the way the files are laid out inside of /var/cache/apt and make sure you copy everything back the same way.

---

### Post by cacycleworks on 2009-01-09
Oooo sweet! I read up on rsync and added a script to /etc/cron.weekly:

rsync -ricv --exclude "lock" /var/cache/apt /home/chris/linux_tricks

:)

---

### Post by dentaku65 on 2009-01-11
> **taisao said:**
> I'm having the same problem. When I want to start kate with superuser access I have to give the path of kate. That's ```
kdesu /usr/kde3/bin/kate

```

Yes, but you can add to the env the PATH
```
sudo nano /etc/environment
```
In something like this:
```
PATH="[COLOR="Red"]/usr/kde3/bin[/COLOR]:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

This is also really necessary to use kde3 apps into Gnome env.

---

### Post by Jack Harkness on 2009-01-13
Are there any known issues with the KDE games?  I installed kdegames-kde3 from Adept.  They appeared to install correctly, but they don't work.  Literally, you click them in the menu and nothing happens... Not even the bouncing icon.  I've uninstalled and reinstalled them three times.  They refuse to work.  The gnome games which are still on my system do work fine.

---

### Post by Jack Harkness on 2009-01-14
A new issue I just ran into.  Adept Manager launches okay, but if I click on "Manage Repositories", nothing happens.  Any ideas?

---

### Post by astrophoenix on 2009-01-15
I have the new kde3 packages installed. but now I want to try out the kde 4.2 beta 2 the kubuntu devs have made available. what should I do? I think I need to remove all of kde3, then install the 4.2 packages, but I'm not sure how to.

---

### Post by dentaku65 on 2009-01-17
> **astrophoenix said:**
> I have the new kde3 packages installed. but now I want to try out the kde 4.2 beta 2 the kubuntu devs have made available. what should I do? I think I need to remove all of kde3, then install the 4.2 packages, but I'm not sure how to.

You have to add the repos of ppa neon as indicated on post #1
look for the part:
> **Do you still want KDE 4?**
then when you are in the login window you can choose which kde use :-)

---

### Post by jeromio on 2009-01-19
What should I do about the knetworkconf-kde3 dependency?

```
The following packages have unmet dependencies:
  kubuntu-desktop-kde3: Depends: knetworkconf-kde3 but it is not going to be installed
                        Recommends: kdebluetooth-kde3 but it is not installable
                        Recommends: kipi-plugins-kde3 but it is not installable
                        Recommends: kubuntu-docs-kde3 but it is not installable
                        Recommends: strigi-applet but it is not installable
                        Recommends: system-config-printer-kde-kde3 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by cacycleworks on 2009-01-19
When I run into issues like this, I use aptitude. You evoke it with 'sudo aptitude' at the command line. It will highlight problems in red and then you can press 'e' to examine -- and it will offer recommendations and/or show if it breaks other things.

imho, this is going to big and complicated enough that efforts really need to be spent getting kubuntu developers to help "the rest of us". KDE4 is wholly different from 3 and is absolutely NOT an "upgrade", "new version", or any other term implying we didn't get the rug pulled out from under us.

-Chris

---

### Post by jeromio on 2009-01-19
Yeah - both aptitude and adept suggest the same "solution": remove kubuntu-desktop-kde3. This rather defeats the whole purpose though ;)

I'm having lots of random issues with my system. Wine stopped working. I have to launch K9copy from cmd prompt for some reason (or else it crashes). For some reason Shift-Enter is mapped to "Logout no Prompt" and I keep inadvertently hitting that combo and getting immediately logged out. That sucks.

I really, really wanted the updated core stuff of 8.10. Particularly Compiz. With 8.0.4 I was having huge issues with Compiz consuming CPU to the point that I had to reboot every other day. Now that is totally resolved. Except KDE 4 is total garbage. I realize they are sort of starting over, but it's just no good right now. IMO, KDE3.5 is better than any other system: I have XP, Vista, Gnome and OS X 10.5. KDE 3.5 is so much better at everything. KDE 4 is on par with Gnome - which is to say, not very user friendly.

It would be awesome if the Kubuntu folks would add KDE3.5 support.

---

### Post by cacycleworks on 2009-01-19
> **jeromio said:**
> Yeah - both aptitude and adept suggest the same "solution": remove kubuntu-desktop-kde3. This rather defeats the whole purpose though ;)

Is kubuntu-desktop-kde3 simply a shell package? If so, you can remove it and everything will be the same. Same as when you remove "kubuntu-desktop" because you don't want kontact, etc.

> **jeromio said:**
> It would be awesome if the Kubuntu folks would add KDE3.5 support.

OMG, yes. I would open my paypal and give $100 to whoever they designate if they promised to let us keep 3.5.x. My current environment is very consistent (if not actually reliable) and I refuse to update or ANYthing to change it. I hope that by the time FF3 quits working in kubuntu 8.04, that KDE4 will be robust or that OpenSuSE, etc, still maintain KDE3 for professionals.

In my case, I have lots of khotkeys mapped...
meta+k = konsole
meta+shift+k = kate
meta+shift+ctrl+k = kdevelop
meta+h = khotkeys
meta+f = system fonts applet
... and those are just my launchers... I've got a slew of text macros for my emails.

Get this...

I type in this:
```
jeromio
```

Then press meta+t and this automagically happens:
```

Hi jeromio,

Thanks for writing!

|   <-- cursor is here blinking...

Thanks,
Chris

```

I've got about 20 of those macros for my emails. Tripled my email handling load. Sometimes in FF with gmail, I can simply do this:
(type their name), meta+t, meta+s, TAB (moves focus to Send), enter, y (to archive the email)

:) Chris

---

### Post by astrophoenix on 2009-01-20
can we get kdiff3 added into this kde 3.5 repo? or is it already there, with a strange name? thanks

---

### Post by iX9 on 2009-01-24
Is madscientist dead?¿

---

### Post by madscientist159 on 2009-01-24
> **iX9 said:**
> Is madscientist dead?¿

Nope, I'm not dead.  I was snowed completely under at work until today, actually. :(

I did (and will in the future) post a status update on the main page here: [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/)

I don't have a lot of time to read through forum threads at the moment, so I was focusing on the bugs that people have been steadily entering into the bugtracker at [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net)

Sorry for giving everyone a scare! :D

Tim

---

### Post by madscientist159 on 2009-01-24
> **astrophoenix said:**
> can we get kdiff3 added into this kde 3.5 repo? or is it already there, with a strange name? thanks

It's there, under kdiff3-kde3  Remember to always add a -kde3 suffix to all KDE3 programs you want to install from my repository.

Also, Synaptic would have found it if you had searched for kdiff3...;)

---

### Post by madscientist159 on 2009-01-24
> **Jack Harkness said:**
> Are there any known issues with the KDE games?  I installed kdegames-kde3 from Adept.  They appeared to install correctly, but they don't work.  Literally, you click them in the menu and nothing happens... Not even the bouncing icon.  I've uninstalled and reinstalled them three times.  They refuse to work.  The gnome games which are still on my system do work fine.

Yes, there is an issue with the default path.  I am correcting it now, and when you can upgrade to kdebase-kde3 4:3.5.10-0ubuntu3~intrepid**10**, do it and the games should work again.

---

### Post by madscientist159 on 2009-01-24
> **jeromio said:**
> What should I do about the knetworkconf-kde3 dependency?

```
The following packages have unmet dependencies:
  kubuntu-desktop-kde3: Depends: knetworkconf-kde3 but it is not going to be installed
                        Recommends: kdebluetooth-kde3 but it is not installable
                        Recommends: kipi-plugins-kde3 but it is not installable
                        Recommends: kubuntu-docs-kde3 but it is not installable
                        Recommends: strigi-applet but it is not installable
                        Recommends: system-config-printer-kde-kde3 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

That's odd.  Looks like it is barfing on ```
Depends: knetworkconf-kde3 but it is not going to be installed
```.  You can safely ignore the ```
Recommends: foo but it is not installable
``` lines; they will not cause a problem once the depends problem is fixed.

Can you post the output of ```
aptitude why-not knetworkconf-kde3
```

Thanks!

---

### Post by Allen0 on 2009-01-24
I'm trying to reinstall kde3 in ubuntu Intrepid install. I keep getting "broken pipe" error.
The following packages have unmet dependencies:
  kcontrol-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                 Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kdebase-kde3: Depends: kdebase-data-kde3 (>= 4:3.5.10-0ubuntu3~intrepid9) but it is not going to be installed
  kdm-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
            Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kicker-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
               Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  kpersonalizer-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                      Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
  ksplash-kde3: Depends: kdebase-data-kde3 (> 4:3.5.10) but it is not going to be installed
                Depends: kdebase-data-kde3 (< 4:3.5.11) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
allen@allen-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdebase-data-kde3
The following NEW packages will be installed:
  kdebase-data-kde3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0B/9070kB of archives.
After this operation, 13.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kdebase-data-kde3
Install these packages without verification [y/N]? y
(Reading database ... 301101 files and directories currently installed.)
Unpacking kdebase-data-kde3 (from .../kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid9_all.deb) ...
Leaving `diversion of /etc/xdg/menus/kde-information.menu to /etc/xdg/menus.kde4/kde-information.menu by kdebase-data-kde3'
dpkg: error processing /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid9_all.deb (--unpack):
 trying to overwrite `/usr/share/wallpapers/default_blue.jpg', which is also in package kdebase-workspace-wallpapers
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-data-kde3_4%3a3.5.10-0ubuntu3~intrepid9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
allen@allen-desktop:~$ sudo apt-get list
E: Invalid operation list
allen@allen-desktop:~$ 


can someone tell me how to fix it?

Thanks in advance.
Allen0

---

### Post by madscientist159 on 2009-01-24
> **Allen0 said:**
> I'm trying to reinstall kde3 in ubuntu Intrepid install. I keep getting "broken pipe" error.

can someone tell me how to fix it?

Thanks in advance.
Allen0

Try removing the kdebase-workspace-wallpapers package and see if the installation completes successfully.

---

### Post by Allen0 on 2009-01-25
Many thanks to madscientist159, you gave me the right stuff. Kde3 now works. The reinstall of Kde3 went on without any problems.

---

### Post by gjoellee on 2009-01-25
I remember sometime I noticed that there exists an ISO of Intrepid with KDE 3

---

### Post by Freebirth One on 2009-01-25
Does anyone know how to install the last stable build of Krusader for KDE3.5 on Ubuntu?

Using the deb of Version 1.90 leads to the error message, that I don't have a kdelibs4. Compiling it from source says that kde-config is missing; apt-file search kde-config says that this file is in kdelibs4c2a. And this one is installed. Both versions, normal and with an "-kde3"-postfix. 

The 'kde-config' isn't there till now. but usually has to be.

Any ideas?



Following some output; debsearch is short form for 'dpkg -l | grep $*'

```

root@smu-extensa:/home/smu/eigene_dateien/sources/krusader-1.90.0# apt-file search kde-config
kdelibs-dbg: /usr/lib/debug/usr/bin/kde-config
kdelibs4c2a: /usr/bin/kde-config
kdelibs4c2a: /usr/share/man/man1/kde-config.1.gz
kdevelop-data: /usr/share/apps/kdevappwizard/template-common/kde-configure.in.in
root@smu-extensa:/home/smu/eigene_dateien/sources/krusader-1.90.0# debsearch kdelibs
ii  kdelibs-bin                                4:4.1.3-0ubuntu1~intrepid4                           executables for all KDE 4 core applications
rc  kdelibs-data                               4:3.5.10-0ubuntu6                                    core shared data for all KDE applications
ii  kdelibs-data-kde3                          4:3.5.10-0ubuntu2~intrepid5                          core shared data for all KDE applications
ii  kdelibs4c2a                                4:3.5.100~0ubuntu1                                   KDE3 libs virtual package
ii  kdelibs4c2a-kde3                           4:3.5.10-0ubuntu2~intrepid5                          core libraries and binaries for all KDE applications
ii  kdelibs5                                   4:4.1.3-0ubuntu1~intrepid4                           core libraries for all KDE 4 applications
ii  kdelibs5-data                              4:4.1.3-0ubuntu1~intrepid4                           core shared data for all KDE 4 applications
root@smu-extensa:/home/smu/eigene_dateien/sources/krusader-1.90.0# which kde-config
root@smu-extensa:/home/smu/eigene_dateien/sources/krusader-1.90.0#

```

---

### Post by Freebirth One on 2009-01-27
Okay, either Krusader was added or I just missed that this one was in the KDE3-Packages. Anyway, I've got a running Krusader 1.90, and that is very, very cool.

Thanks for that.

---

### Post by Allen0 on 2009-01-27
I'm trying to clean up my gdm login screen. I have kde3.5 (that works) - 
kde (that dosn't work) - and kde neon (that works). How can I get the kde off of my login screen. I want to keep kde3.5 and kde neon on it. I can't figure out what text file controls the login screen so I can edit it to fix my problem. 

Thanks Allen0

---

### Post by Allen0 on 2009-01-28
I fixed my problem. I edited
/etc/apt/sources.list
and took out the "KDE" line. It was the only way I could find to get rid of the login window problem.

Allen0

---

### Post by jeromio on 2009-01-29
I neglected to come back to this thread to follow-up on the knetworkconf-kde3 issue. I did enter an issue in bugzilla and it's fixed now and I can install the package.

For k9copy, I uninstalled the kde4 version (since it really wasn't working correctly) and downloaded a debian ("test") version of k9copy 1.2.4. This installed and is running fine. Maybe add it to the repo?

I still need help with my "log out no prompt" issue. There are *several* key combinations that invoke this. In fact, as I typed that "test" above, I inadvertently logged myself out. I think I did shift+backspace or shift+spacebar. I know that shift+Enter also invokes this. I have edited every file I can find that has a key mapping in it to remove any shortcut sequences. But it's still happening. I also have the double bouncing program icons when starting up any app. I saw a post on that in this thread, but the suggested fix didn't fix this for me.

I'm also having some strange-ness with web browsing. In Firefox, cookies are not behaving correctly. They seem to get deleted. And there are several web pages that don't load - I get a redirect loop error. These pages load on *all* my other systems (a kubuntu hardy box, mac osx, windows). I also have trouble with using konqueror for web browsing. Many, many pages (such as .asp) are not recognized as web pages and I get a prompt asking what I want to do with the file (eg, download, open in Kate). 

I suspect that all of these problems are somehow related and that there's just one magic spot where I can go to fix everything in one file ;)

I do appreciate all the work that's been done by madscientist et al. For the most part, this is working well. But these little issues (actually, the "random" forced log-outs due to various shift key sequences is seriously debilitating) are annoying.

---

### Post by jeromio on 2009-01-29
Also, the log-out window (for the prompted logout, where I actually *mean* to log out ;) ) is scrogged. So if I go to the "start menu"  and select Logout, instead of a window with all the options: logout, shutdown, restart, I just have one button for Logout. So to restart, I have to use shutdown from the commandline.

---

### Post by minneyar on 2009-01-30
When I go to [http://bugs.pearsoncomputing.net/](http://bugs.pearsoncomputing.net/), it says "You don't have permission to access / on this server."  Is anybody else seeing this?

Also, when I run "sudo apt-get update" with the KDE3 repository in my sources.list, I get this error:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB2F6C86F77B1CA9

I've got the key linked to from [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/) in my key ring, and everything was working fine until a couple of days ago.  Not to be paranoid or anything, but the bug tracker going down and the repository being signed with a different key make me a little nervous.

---

### Post by maybeway36 on 2009-01-30
gtk-qt-engine-kde3 doesn't seem to work right for me. GTK apps look plain and gray when I choose to use my KDE theme.

---

### Post by Jack Harkness on 2009-02-01
> **minneyar said:**
> When I go to [http://bugs.pearsoncomputing.net/](http://bugs.pearsoncomputing.net/), it says "You don't have permission to access / on this server."  Is anybody else seeing this?

Also, when I run "sudo apt-get update" with the KDE3 repository in my sources.list, I get this error:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB2F6C86F77B1CA9

I've got the key linked to from [http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/) in my key ring, and everything was working fine until a couple of days ago.  Not to be paranoid or anything, but the bug tracker going down and the repository being signed with a different key make me a little nervous.

I just got a bunch of *-kde3 updates a couple of days ago.  Looks like work is continuning.

---

### Post by tehmini on 2009-02-03
I get the following when trying to install:

```

[~]|19> sudo apt-get install kubuntu-desktop-kde3       
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop-kde3: Depends: kdenetwork-filesharing-kde3 but it is not going to be installed
                        Recommends: kdebluetooth-kde3 but it is not installable
                        Recommends: kipi-plugins-kde3 but it is not installable
                        Recommends: kubuntu-docs-kde3 but it is not installable
                        Recommends: strigi-applet but it is not installable
                        Recommends: system-config-printer-kde-kde3 but it is not installable
E: Broken packages

```

Any ideas? (if it matters, I have both KDE 4.2 and KDE nightly/neon installed)

---

### Post by madscientist159 on 2009-02-12
> **tehmini said:**
> I get the following when trying to install:

```

[~]|19> sudo apt-get install kubuntu-desktop-kde3       
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop-kde3: Depends: kdenetwork-filesharing-kde3 but it is not going to be installed
                        Recommends: kdebluetooth-kde3 but it is not installable
                        Recommends: kipi-plugins-kde3 but it is not installable
                        Recommends: kubuntu-docs-kde3 but it is not installable
                        Recommends: strigi-applet but it is not installable
                        Recommends: system-config-printer-kde-kde3 but it is not installable
E: Broken packages

```

Any ideas? (if it matters, I have both KDE 4.2 and KDE nightly/neon installed)

Can you post the output of
```
aptitude why-not kdenetwork-filesharing-kde3
```

To those who noticed the bugtracker problem and the signing key issue: that was a really bad coincidence.  I migrated my main webserver to Apache 2.2, which temporarily killed the bugtracker due to some mod_proxy issues, and at nearly the same time Launchpad decided to change my signing key.  It probably looked like I was hacked or something went terribly wrong, but rest assured that was not the case. :P

BTW all those issues have now been resolved, thanks to the bug reports that were filed.  If you still have the old GPG signing keys, please go to [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) and follow the GPG key instructions again.

Tim

---

### Post by uboot on 2009-02-27
Hi folks, 

I also got exited when I discovered this thread and tried to install kde3 on Intrepid. Having had KDE4 on it before, I ran into big trouble :( In my second life I'm a Gentoo user who's not so familiar with Debian's package management...

kubuntu-desktop-kde3 installed without errors, but there are certain glitches like kinfomanager showing nothing and I am unable to change monitor resolution - the according dialog simply does not exist under system settings :(

I discovered that /usr/kde3/bin does not reside in the path, so I added it to /etc/environment.

Also, I added universe and multiverse to sources.list

But still no luck, so I tried to uninstall every kde package I could find. I had some trouble removing kio-umountwrapper-kde3 but got it solved via [http://ubuntuforums.org/showthread.php?p=4786808](http://ubuntuforums.org/showthread.php?p=4786808)

Then I tried to reinstall kubuntu-desktop-kde3. Worked without errors, but what is strange to me is: this will install kdebase-runtime*, kdelibs-bin kdelibs5* for KDE 4.1.4 as well as kdm from KDE4. 

This seems somehow related to the fact, that kubuntu-desktop-kde3 depends on kwin-style-crystal, language-selector-qt and software-properties-kde

Finally: I still cannot change resolution. KDE Control Center is empty.


...maybe I should add that my Ubuntu is AMD64...

----
Allright, did a fresh textmode install of kubuntu 8.10 and the error isn't gone. KControl is not empty anymore, but lacks the ability to setup monitor resolution.

I filed a bugreport here: [http://bugs.pearsoncomputing.net/show_bug.cgi?id=45](http://bugs.pearsoncomputing.net/show_bug.cgi?id=45)

---

### Post by madscientist159 on 2009-03-02
> **uboot said:**
> Hi folks, 

I also got exited when I discovered this thread and tried to install kde3 on Intrepid. Having had KDE4 on it before, I ran into big trouble :( In my second life I'm a Gentoo user who's not so familiar with Debian's package management...

kubuntu-desktop-kde3 installed without errors, but there are certain glitches like kinfomanager showing nothing and I am unable to change monitor resolution - the according dialog simply does not exist under system settings :(

I discovered that /usr/kde3/bin does not reside in the path, so I added it to /etc/environment.

Also, I added universe and multiverse to sources.list

But still no luck, so I tried to uninstall every kde package I could find. I had some trouble removing kio-umountwrapper-kde3 but got it solved via [http://ubuntuforums.org/showthread.php?p=4786808](http://ubuntuforums.org/showthread.php?p=4786808)

Then I tried to reinstall kubuntu-desktop-kde3. Worked without errors, but what is strange to me is: this will install kdebase-runtime*, kdelibs-bin kdelibs5* for KDE 4.1.4 as well as kdm from KDE4. 

This seems somehow related to the fact, that kubuntu-desktop-kde3 depends on kwin-style-crystal, language-selector-qt and software-properties-kde

Finally: I still cannot change resolution. KDE Control Center is empty.


...maybe I should add that my Ubuntu is AMD64...

----
Allright, did a fresh textmode install of kubuntu 8.10 and the error isn't gone. KControl is not empty anymore, but lacks the ability to setup monitor resolution.

I filed a bugreport here: [http://bugs.pearsoncomputing.net/show_bug.cgi?id=45](http://bugs.pearsoncomputing.net/show_bug.cgi?id=45)

First, thanks for the bugreport, I appreciate you taking the time to file it. :KS

You caught me at a really bad time.  Right now, the entire repository is in an inconsistent state, as I am in the middle of a massive update that moves the KDE3.5 files to a standard directory [/opt/kde3] instead of the nonstandard directory they were in earlier.  I am also pulling most of the KDE3.5 config files out of /etc, and trying to get everything to compile in preparation for Jaunty, which will be here before we know it.

Why don't you (and anyone else who reads this) **_*hold off on updating or installing anything from the repository for a week or so*_** while I finish the update.  Once that is done, I will post here and update the open bugreports, asking that those who reported them re-test and see if the bug has been fixed or not.

Hopefully this update is a one-time deal; I see no reason to shift the directories around any more after this.

Thanks! :P

Tim

---

### Post by cmreigrut on 2009-03-02
Well, I did an auto update this morning, and bad things have apparently occurred.  When I attempt to start up and log on, I now get a window stating 
```
Could not start kstartupconfig.  Check your installation.
```

my only option is an "okay" button, at which point I get
```
Call to lnusertemp failed (temporary directories full?). Check your installation
```

again, all I get is "okay" at which point it looks like X restarts and I'm back at the graphical login.

When I looked, it appeared that kubuntu-desktop-kde3 was no longer there, so I attempted to reinstall it, but still to no avail.  I've now uninstalled and reinstalled it several times (trying various permutations of clean, autoclean, remove, etc.) but still nothing.  

Any help would be greatly appreciated!

---

### Post by zevans on 2009-03-02
> **madscientist159 said:**
> 
Why don't you (and anyone else who reads this) **_*hold off on updating or installing anything from the repository for a week or so*_** while I finish the update.


If you're halfway through moving to /opt I think you should disable the repository or this thread is going to get very busy! Appreciate it's a complicated thing to do.

I figured that might be what you were doing, my system broke the same way after the updates this morning and I noticed some libs and config had moved. I've half-fixed it by copying some stuff back to /usr, but kicker is properly broken. 

Keep it up though :D

---

### Post by cmreigrut on 2009-03-02
> **zevans said:**
> If you're halfway through moving to /opt I think you should disable the repository or this thread is going to get very busy! Appreciate it's a complicated thing to do.

I second this thought.  I'm still hosed--and apparently MadScientist and I were posting at the same time, so I didn't see his post!

Zevans, can you post what you changed?  I'm trying to work through the problem right now and any advice would be great!

---

### Post by madscientist159 on 2009-03-02
> **zevans said:**
> If you're halfway through moving to /opt I think you should disable the repository or this thread is going to get very busy! Appreciate it's a complicated thing to do.

I wish I could.  To make matters worse, my PPA overran its assigned space late last night and I only recently got the limit increased again (re-allowing package uploads).  I was planning to perform the update of the base system (arts, libs, base, artwork, multimedia, games) overnight to minimize the impact on the users, but due to the PPA problem I obviously could not.

I just noticed that the new kdebase compiled, so those who were unlucky enough to already update their systems try an update in about 30 minutes or so--the new kdebase will restore quite a bit of functionality.

Sorry for the inconvenience!

Tim

---

### Post by cmreigrut on 2009-03-02
I'm back to semi-functional as well (after copying /usr/kde3 from last night's backup).  It generated a bunch of missing mime type problems when starting up, but aside from missing icons I seem ok.

Hey, Tim--can you post here when you get kdebase up?  I'll be happy to update and test it for you (but I don't want to get half an update again).  Thanks!

---

### Post by cmreigrut on 2009-03-02
Well, I tried upgrading, figuring that it couldn't hurt as I could just go back to my existing /usr/kde3.  I now get dropped directly into a shell (no X, no KDM).

When I run startx, I get:
```
Xsession: unable to start X session --- no "/home/chris/.xsession" file, no "/home/chris/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.
```

Reverting back to my old /usr/kde3 I can run kdm from the command prompt and then everything is pretty peachy.

---

### Post by madscientist159 on 2009-03-02
> **cmreigrut said:**
> Well, I tried upgrading, figuring that it couldn't hurt as I could just go back to my existing /usr/kde3.  I now get dropped directly into a shell (no X, no KDM).

When I run startx, I get:
```
Xsession: unable to start X session --- no "/home/chris/.xsession" file, no "/home/chris/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.
```

Reverting back to my old /usr/kde3 I can run kdm from the command prompt and then everything is pretty peachy.

Hmmm...I was afraid something like that might happen.  What happens if you do a ```
sudo dpkg-reconfigure kdm-kde3
``` and select kdm-kde3 again?

If that doesn't work, try temporarily installing and using regular kdm or gdm as the login screen and select kde3 as the session type.

---

### Post by bennywhere on 2009-03-02
Ok,
so I didn't read the post before updating today and I totally hosed my system...

madscientist: First of all, thanks a lot for your work providing kde 3.5 on intrepid!!  It's very much appreciated.
Now, when do you think things are back to normal? I don't want to rush you, but I'm at the point where I need to install and use gnome for the time being :-(

Thanks a lot!

Ben

---

### Post by cmreigrut on 2009-03-02
OK, so I did the the dpkg-reconfigure.  Still get dropped into the shell at startup, but sudo /opt/kde3/bin/kdm now brings up kdm and everything's peachy.  So we're almost there!

Thanks for all the hard work, Tim!

---

### Post by cmreigrut on 2009-03-02
> **bennywhere said:**
> Ok,
so I didn't read the post before updating today and I totally hosed my system...
<snip>
...I'm at the point where I need to install and use gnome for the time being :-(

Ben,

You should be able to get back to a functional KDE3 with the following:
```

sudo apt-get update
sudo apt-get clean
sudo apt-get update
sudo dpkg-reconfigure kdm-kde3

```

If you DO get dropped to the shell when you start up,
```

sudo /opt/kde3/bin/kdm

```
should get you going.

---

### Post by bennywhere on 2009-03-02
cmreigrut,
thanks a lot for your help! I'll try it right away!

Thanks again!

Ben

---

### Post by madscientist159 on 2009-03-02
Here's how to fix the kdm-kde3 problem--I don't know why the upgrade did not automatically do this:
Edit /etc/X11/default-display-manager as root, and change /**usr**/kde3/bin/kdm to /**opt**/kde3/bin/kdm

If the file contained /usr/kde3/bin/kdm at the time of the upgrade, no amount of dpkg-reconfigure attempts will fix it--it seems to get stuck, with a manual edit being the only way to restore it to proper functionality.

For those who accidentally hosed their systems, I can confirm that upgrading to the latest will bring back most system functionality.  The only major problem that I can see at the moment is that kde-gtk themes do not work, but this will be fixed as I run through the remaining updates.

On a side note, I had no idea so many people were still using KDE3.5! :P  I'm going to set up a poll on the KDE3.5 maintainers project page to get some idea of exactly how many--I'll post a link when I have it up.

Tim

---

### Post by bennywhere on 2009-03-02
Thanks Tim!! Looks like most is back to normal!
However, now I need to compile a kde program (kthinkbat) and I get an error saying that "in the prefix you've chosen are no KDE headers installed..." 
Does anyone know what to do?

Thanks!

---

### Post by moparisthebest on 2009-03-02
I hosed my system earlier by upgrading, it fixes most things by copying everything from /usr/kde3/ to /opt/kde3/, then deleting /usr/kde3 and linking it to /opt/kde3/.

Basically:
```

mv -r /usr/kde3/* /opt/kde3/
rm -r /usr/kde3
ln -s /opt/kde3 /usr/kde3

```

Yakuake still crashes, and not all icons are back but it's not that bad.

By the way, thanks madscientist159 for doing all of this for us, KDE4 is so unusable right now and I love 3.5, I appreciate all the hard work you put into this. :)

---

### Post by madscientist159 on 2009-03-02
> **bennywhere said:**
> Thanks Tim!! Looks like most is back to normal!
However, now I need to compile a kde program (kthinkbat) and I get an error saying that "in the prefix you've chosen are no KDE headers installed..." 
Does anyone know what to do?

Thanks!

Use this compile option:
--prefix=/opt/kde3

Don't use --exec-prefix or anything like that.  If that doesn't work let me know and I'll look a bit closer into the problem.

Status update:
kdepim is giving me major grief ("libtool: install: `conduit_doc.la' is not a valid libtool archive"), so I may have to skip over the KDE PIM applications for now and come back to them later.

---

### Post by bennywhere on 2009-03-02
Tim,
nope that doesn't seem to work... same error.
Now, what about the comment above yours regarding moving everything from /usr/kde3 to /opt/kde3?  Would you suggest doing that?

Thanks!

---

### Post by madscientist159 on 2009-03-02
> **bennywhere said:**
> Tim,
nope that doesn't seem to work... same error.
Now, what about the comment above yours regarding moving everything from /usr/kde3 to /opt/kde3?  Would you suggest doing that?

Thanks!

You could, but back up both directories first.  The problem is that as I continue to release fixed packages over the next few days, they will end up conflicting with the files you just coped over and this will give your package manager (and you!) a monumental headache. ;)

Try these compile options: --prefix=/opt/kde3 --with-extra-includes=/opt/kde3/include/kde --with-extra-libs=/opt/kde3/lib

Also, why don't you submit a bug report (a.k.a package request) for the package you are trying to compile?  I'd be happy to add it to the repository...

Once again, I apologize for all the problems this has caused.  I was originally going to do this all overnight, but the PPA size problem really messed that up.

---

### Post by bennywhere on 2009-03-02
Tim, no need to apologize, we all appreciate your work on this!

As for the bug report: I'm modifying the source to enhance the program, which does not even come as a .deb package (as far as I know).  It's really only the compilation that doesn't work anymore since today's update.  ./configure actually recognizes /opt/kde3 when it's checking for kde-config

Regarding the copying over: I guess I'd rather wait... ;-) nobody likes headaches!

Thanks for your help.

---

### Post by mdhirsch on 2009-03-03
> **madscientist159 said:**
> 
I just noticed that the new kdebase compiled, so those who were unlucky enough to already update their systems try an update in about 30 minutes or so--the new kdebase will restore quite a bit of functionality.

Sorry for the inconvenience!

Tim

Tim, sorry for all the trouble you're having.  I wish I had read this earlier.  I figured out how to get KDM working on my own, and then read this thread.

I find going to the end of a long web conversation very inconvenient.  Is there an email gateway for this forum?  Or is there a mailing list you monitor to discuss your wonderful PPA repository?  I bet there are a lot of folks using it and it would be nice to have a mailing list.

If you're looking for suggestions, I think the kubuntu users mailing list would be the appropriate place, but anywhere would be great.

Thanks for all your hard work,

Michael

---

### Post by kekc on 2009-03-03
Hi Tim,

Thanks for repository, first of all! ;)

Secondly - I had the same problem with kdm, but fixed /etc/X11/default-display-manager. It's OK now.

But I have also lost some progs, that are left disconnected in /usr/kde3/bin/. Can you suggest temporary solution, how to use them? I mean PATH and libraries link.

Path is simple - I have just add
```
PATH=$PATH:/usr/kde3/bin
export PATH

```
to my .bash_profile.

But what about libs in /usr/kde3/lib/? Should I add them to /etc/ld.so.conf.d/kde3libs.conf?

Thanks again!

---

### Post by madscientist159 on 2009-03-04
> **mdhirsch said:**
> Tim, sorry for all the trouble you're having.  I wish I had read this earlier.  I figured out how to get KDM working on my own, and then read this thread.

I find going to the end of a long web conversation very inconvenient.  Is there an email gateway for this forum?  Or is there a mailing list you monitor to discuss your wonderful PPA repository?  I bet there are a lot of folks using it and it would be nice to have a mailing list.

If you're looking for suggestions, I think the kubuntu users mailing list would be the appropriate place, but anywhere would be great.

Thanks for all your hard work,

Michael

I agree.  I am thinking of starting a kubuntu-kde3.5-users mailing list--would anyone else like this as well?  I would also start a kubuntu-kde3.5-announce list so that I can warn people when I am rolling out a major update like this one... ;)

> **kekc said:**
> Hi Tim,

Thanks for repository, first of all! ;)

Secondly - I had the same problem with kdm, but fixed /etc/X11/default-display-manager. It's OK now.

But I have also lost some progs, that are left disconnected in /usr/kde3/bin/. Can you suggest temporary solution, how to use them? I mean PATH and libraries link.

Path is simple - I have just add
```
PATH=$PATH:/usr/kde3/bin
export PATH

```
to my .bash_profile.

But what about libs in /usr/kde3/lib/? Should I add them to /etc/ld.so.conf.d/kde3libs.conf?

Thanks again!

Yes, for now you can safely add /usr/kde3/lib to /etc/ld.so.conf.d/kde3libs.conf .  Be sure to run ldconfig afterwards.

Status update: The core system has been updated and tested working; I am now uploading the zillions of smaller packages.  Can those who already upgraded update again and let me know if anything major is still broken?

By the way, I know my bugtracker is down.  The server it is hosted on has a magically-shrinking free disk space problem; I have only see it once or twice before, and only on this particular server.  I haven't had time to track the root cause down, so Bugzilla remains offline for now. :(

Tim

---

### Post by FlevoMartin on 2009-03-04
> **madscientist159 said:**
> Can those who already upgraded update again and let me know if anything major is still broken?

I've just updated again. The Knetworkmanager works if started from /usr/kde3, only the icons are missing here and there. But somewhat worse: Kaffeine tells me "Loading of player part 'xine_part' failed." on startup and therefore is unable to play any media files. 
Otherwise I didn't find any bigger issues for now.

Thank you and keep up the good work!
Martin

---

### Post by xylometazolin on 2009-03-04
> **madscientist159 said:**
> Can those who already upgraded update again and let me know if anything major is still broken?

Today I completely removed my kde3, made a "aptitude clean" and installed it again. During the installation I had chosen kdm-kde3 as my default display manager, but the package still writes "/usr/kde3/bin/kdm" to /etc/X11/default-display-manager. Yakuake is currently not usable. It crashes after the start.

Thanks for your work, Tim!

---

### Post by managementboy on 2009-03-05
> **xylometazolin said:**
> Today I completely removed my kde3, made a "aptitude clean" and installed it again. During the installation I had chosen kdm-kde3 as my default display manager, but the package still writes "/usr/kde3/bin/kdm" to /etc/X11/default-display-manager. Yakuake is currently not usable. It crashes after the start.

Thanks for your work, Tim!

yes, same happens to me yakuake is broken

---

### Post by tonyelewis on 2009-03-05
Thanks very much for your work which allows me to continue using KDE3.  Continuing the messages about problems arising from this week's changes, I have had problems with compiz after this morning's updates.  Compiz was working for me yesterday.  Here are some of the errors and my attempted temporary fixes :

> compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/opt/kde3/bin/compiz: 406: /usr/kde3/bin/compiz.real: not found

> sudo ln -s /opt/kde3/bin/compiz* /usr/kde3/bin/

> compiz --replace
Checking for Xgl: not present.
...
Checking for Xgl: not present.
/usr/kde3/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

> sudo ln -s /usr/kde3/lib/compiz/lib*.so /opt/kde3/lib/compiz/

> compiz --replace
Checking for Xgl: not present.
...
Checking for Xgl: not present.
/usr/kde3/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"

ln -s /usr/share/compiz/* /opt/kde3/share/compiz/

> compiz-decorator --replace
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start

> sudo ln -s /opt/kde3/lib/libdecoration.so* /usr/kde3/lib/

At this point, it still wasn't working so I gave up because I need to get on with some work.  Any help on these issues much appreciated.

---

### Post by xylometazolin on 2009-03-05
The kile packages seems to be currently not available.

But kaffeine works again. :) Thanks, Tim.

---

### Post by mdhirsch on 2009-03-05
> **madscientist159 said:**
> I agree.  I am thinking of starting a kubuntu-kde3.5-users mailing list--would anyone else like this as well?  I would also start a kubuntu-kde3.5-announce list so that I can warn people when I am rolling out a major update like this one... ;)

Yes, please let us know when the mailing lists are setup.  I'll join both.

> 
Status update: The core system has been updated and tested working; I am now uploading the zillions of smaller packages.  Can those who already upgraded update again and let me know if anything major is still broken?


Amarok won't play anything for me.  I get an error I've not seen before:
Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

Thanks,

Michael

---

### Post by mdhirsch on 2009-03-05
> **mdhirsch said:**
> 
Amarok won't play anything for me.  I get an error I've not seen before:

I take it back.  I did another update.  Strangely, though only one package was shown as updateable, but I selected "Mark all upgrades" in synaptic, I got about 20 new kde3 packages.  Now amarok is quite happy, as am I.

---

### Post by manij on 2009-03-05
The big update did me in couple of days ago!

but I was able to edit the display manager to

/opt/kde3/bin/kdm

get KDE 3 running.

but I'm not able to run adept to fire up. it says it is not installed or something like that also knetworkmanager is not available???

Can I get around this by using Gnome and doing an update?

BTW, Thanks for all your effort for getting KDE 3 in II MAdscientist.

---

### Post by madscientist159 on 2009-03-06
> **manij said:**
> The big update did me in couple of days ago!

but I was able to edit the display manager to

/opt/kde3/bin/kdm

get KDE 3 running.

but I'm not able to run adept to fire up. it says it is not installed or something like that also knetworkmanager is not available???

Can I get around this by using Gnome and doing an update?

BTW, Thanks for all your effort for getting KDE 3 in II MAdscientist.

You can go to a terminal and type ```
sudo apt-get update && sudo apt-get upgrade
``` to install the updates.

Quick status update: I have just finished another batch of updates.  This one cures the aptitude problems, as well as the oh-so-annoying default-display-manager problem.  I am about 80% done now; expect the entire update to be finished in the next couple of days.

The mailing lists are online now.  There is a link with subscription information on my homepage at [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) -- just scroll down a bit; it is near the bottom.  I will announce when the update is complete and when my bugtracker is fixed on the -announce list. :)

Thank you one and all for your patience during this--I really appreciate how friendly the Kubuntu community seems to be! :D

Tim

---

### Post by tonyelewis on 2009-03-06
Hello.  Many thanks for your continued work on this.  I'm now noticing three problems...

1.  Compiz not working.  Details as for yesterday.

2.  Firefox not working:

> /usr/bin/firefox
Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.
> /usr/bin/firefox-3.0
Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.

3.  Failure to update kio-umountwrapper-kde3 :

> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  kio-umountwrapper-kde3
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
70 not fully installed or removed.
Need to get 0B/12.7kB of archives.
After this operation, 8192B of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 301860 files and directories currently installed.)
Preparing to replace kio-umountwrapper-kde3 0.2-0ubuntu3 (using .../kio-umountwrapper-kde3_0.2-1ubuntu0_i386.deb) ...
Leaving `diversion of /opt/kde3/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /opt/kde3/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper-kde3'
Unpacking replacement kio-umountwrapper-kde3 ...
dpkg: error processing /var/cache/apt/archives/kio-umountwrapper-kde3_0.2-1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/opt/kde3/share/apps/konqueror/servicemenus/media_safelyremove.desktop', which is also in package konqueror-kde3
/var/lib/dpkg/tmp.ci/postrm: didn't understand being called with `abort-upgrade'
Errors were encountered while processing:
 /var/cache/apt/archives/kio-umountwrapper-kde3_0.2-1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I presume that these issues are all related to the KDE3 changes - please accept my apologies if not.  Thanks again.

---

### Post by tonyelewis on 2009-03-06
Apologies.  Please ignore my mention of Firefox - I think that issue is unrelated.  I seem to have got Firefox up and running with:

> sudo ln -s /etc/gre.d/1.9.0.7.system.conf.dpkg-new /etc/gre.d/1.9.0.7.system.conf
> firefox &

---

### Post by madscientist159 on 2009-03-06
> **tonyelewis said:**
> Apologies.  Please ignore my mention of Firefox - I think that issue is unrelated.  I seem to have got Firefox up and running with:

> sudo ln -s /etc/gre.d/1.9.0.7.system.conf.dpkg-new /etc/gre.d/1.9.0.7.system.conf
> firefox &

You are correct. ;)

Thank you for letting me know about the umountwrapper problem--I have uploaded a fix; as soon as the PPA compiles it you should be rid of that error.

Compiz is a pain.  I will probably have to work on it for a few more days to get it working 100% again, so just be patient and the Compiz problems will probably resolve themselves. :)

---

### Post by bobe84 on 2009-03-06
This is bad, i did update hour ago and it broke everything, i mean everything. This is so sad, nautilis starts as default file manager... :(
No icon anywhere...

Help please!

---

### Post by jeromio on 2009-03-06
My system was very dead - managed to get it back up by following the recent posts here. 

I'm back up now, although w/ no compiz. However, KDE is really clunky. Not sure what package would be responsible for this. If I switch windows or launch a new app, I can see the app getting drawn on screen. Slowly. Each control gets rendered, almost a pixel at a time. Moving the active window is fine, but the windows underneath get the same pixel by pixel refresh deal.

---

### Post by bennywhere on 2009-03-06
I can confirm the above issue.  Also, there are no icons, and not all apps are shown in k menu.

Thanks!

---

### Post by madscientist159 on 2009-03-06
> **bennywhere said:**
> I can confirm the above issue.  Also, there are no icons, and not all apps are shown in k menu.

Thanks!

That is odd--I am running an updated version of KDE3 with no problems. :confused:

Did you have Compiz enabled at the time of the upgrade?  If so, what happens if you deactivate Compiz?

Which icons are missing?

EDIT: Please, please make sure you reboot your systems after applying these updates.  Also, make sure you have all of the updates installed using a terminal and ```
sudo apt-get update && sudo apt-get dist-upgrade
``` as it is possible that your package manager only applied some of them and silently failed.

---

### Post by zekica on 2009-03-07
It looks like your new packages are installing files in /opt/kde3, while previous version installed them in /usr/kde3.

And also in new packages, KDE applications aren't looking in /opt/kde3 nor in /usr/kde3 for .desktop files or any other configuration (icons, sounds, etc...).

I hope that this will help you fix updated packages, so that we can use KDE3 again.

---

### Post by zekica on 2009-03-07
Update: It looks that adding following lines at the beginning of 'startkde' script fixes almost all problems:

```
export KDEDIRS=/opt/kde3/:/usr/
export XDG_DATA_DIRS=/opt/kde3/share/:/usr/share/
```

However, there is one major problem with configuration of some applications:
For example konqueror has duplicated buttons on toolbar: [http://i40.tinypic.com/2la671f.png](http://i40.tinypic.com/2la671f.png)

And also some applications have duplicated menu items or some menu items have "No text" as their title.

I believe that the problem is with some compile time configuration options not applied.

---

### Post by madscientist159 on 2009-03-07
> **zekica said:**
> Update: It looks that adding following lines at the beginning of 'startkde' script fixes almost all problems:

```
export KDEDIRS=/opt/kde3/:/usr/
export XDG_DATA_DIRS=/opt/kde3/share/:/usr/share/
```

However, there is one major problem with configuration of some applications:
For example konqueror has duplicated buttons on toolbar: [http://i40.tinypic.com/2la671f.png](http://i40.tinypic.com/2la671f.png)

And also some applications have duplicated menu items or some menu items have "No text" as their title.

I believe that the problem is with some compile time configuration options not applied.

Thank you for the fix!  I have uploaded a new version of kdebase that includes it.

With regard to the duplicated Konqueror menu bar, I wonder if there are some old konqueror files floating around in /usr/kde3.  Can you try moving /usr/kde3 to /usr/kde3.bkp (it should no longer be needed) and see if that fixes the problem?

I am setting up a clean install of Intrepid right now to see if I can find any other problems--apparently when I simply upgraded my system it was not enough to expose these issues.

Thanks! :D

Tim

---

### Post by zekica on 2009-03-07
I have no configuration files in /usr/kde3. There is only a kdesu binary file in /usr/kde3/bin.

I have also noticed that some standard options in kde applications like 'About KDE' in Help menu are not available in:
- Konqueror
- Systemsettings

And are available in:
- Konsole
- Kate


If I do a 'Configure toolbar' and move one of the buttons up or down, double buttons dissapear, but menu stays without those basic options: [http://i43.tinypic.com/153xiyp.png](http://i43.tinypic.com/153xiyp.png)

---

### Post by zekica on 2009-03-07
I have attached a list of all files on my test installation (ls -R /).

There was a /debian folder which I have renamed to 'debianx2'.

I hope this helps a little. ;)

---

### Post by madscientist159 on 2009-03-08
Here's a copy of the message I just sent to the kubuntu-kde3.5-announce list:
> The update is finally complete!  You may now update and then file bugs on the bug tracker at [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net) as needed.

Before filing a bug, please check the following:
1. Make sure *all* of the available updates are actually installed.  KDE3.5 is made up of many small packages, and some of them can "slip though the cracks" and not get updated by your package manager.  The simple way to test this is to open a terminal and type "sudo apt-get update && sudo apt-get dist-upgrade" (without the quotes).

2. Does the bug still exist when you log in as a brand new user?  If not, then one of your profile's configuration files (located in ~/.kde3) is most likely out of date, and you will need to find and update it manually.

This repository is finally Debian directory structure compliant, and also compatible with any new version of KDE4 due to the prefix change.  I hope this will make the transition to Jaunty quite smooth.

As always, I welcome your comments and suggestions!

Timothy Pearson
KDE3.5 Maintainer
[http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net)

Something I forgot to mention in that message, but seems quite obvious, is that you **must** log out and log back in after the update is complete to allow the programs to reload from the new prefix.

---

### Post by jeromio on 2009-03-08
Still having the slowness issues in KDE. I upgraded from a console login and rebooted. My system settings manager is missing several plugins (has since I moved to 8.10 w/ KDE3.5). One of those is the user admin one. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=105767&stc=1&d=1236539493[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=105768&stc=1&d=1236539493[/IMG]
I can add a user from commandline, but then I can't log that user into KDE due to missing .xsession stuff. How do I add a user such that it can login to KDE? Ideally, how do I get that user management plugin back?

Also, the logout dialog is still broken. it only shows the "Logout" button - no option to switch user, shutdown or restart.

And I cannot enable compiz - at least not the "right" way. The dialog shows an install button and all options greyed out.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=105766&stc=1&d=1236539493[/IMG]
When I click "Install", I get an error:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=105765&stc=1&d=1236539493[/IMG]

---

### Post by madscientist159 on 2009-03-08
Thank you for all that detailed information--it is much appreciated.

I just tested Compiz (and the installation of it from the screen that you showed) on my clean-slate Intrepid test machine--it worked perfectly.  Do you have adept-kde3 installed?

There is definitely a problem with the KDE control center.  I did not realize kde-guidance was required when I originally created this repository, so now I have to go back and compile it.  Expect it up in the next couple of days if everything goes well.  You should have filed a bug report when you first noticed it... ;)

You can, from KDM-kde3, select KDE3 from the "Session type" menu.

Thanks again!

Tim

---

### Post by bobe84 on 2009-03-08
It appears that almost everything is ok now, no more dead apps, icons are ok.
Only thing is double toolbar in konqueror, help menu konqueror, double bookmarks menu konqueror.

---

### Post by tonyelewis on 2009-03-09
Hi Tim.  My compiz is working now and things seem to be pretty much back to normal.  Thanks very much.

---

### Post by uboot on 2009-03-09
it's still the same - unable to change monitor resolution... :(

---

### Post by madscientist159 on 2009-03-09
> **uboot said:**
> it's still the same - unable to change monitor resolution... :(

A couple of days (and way too many libs/base updates) later...it works for me! :D

Can you try it again?  You will need to have the kde-guidance-kde3 package installed on your system, if it isn't already.

If it doesn't work, it is very possible that it doesn't "like" your Xorg configuration--there are a lot of bugs on Launchpad related to that particular control module.

---

### Post by kekc on 2009-03-10
Hi Tim!

Thanks for your great job!
I see, that almost all programs in /opt/kde3 now.

The only one I have in /usr/kde3 is kdesvn-kde3 and it's libs.

---

### Post by uboot on 2009-03-10
> **madscientist159 said:**
> A couple of days (and way too many libs/base updates) later...it works for me! :D

Can you try it again?  You will need to have the kde-guidance-kde3 package installed on your system, if it isn't already.

If it doesn't work, it is very possible that it doesn't "like" your Xorg configuration--there are a lot of bugs on Launchpad related to that particular control module.

That's what I did yesterday - installed a fresh kubuntu-desktop-kde3 :(

Today there were several updates and following your hint regarding guidance manager, I discovered that the kde3-version wasn't installed but the kde4 version!!

I then installed guidance-power-manager-kde3. This triggered a de-install of the kde4 guidance manager that got installed with kubuntu-desktop-kde3 before.

Now I can change resolution but somehow X-Server is running with VESA drivers. My xorg.conf the default one (pretty empty, so to say...) and with Gnome it manages to load the correct intel driver for my 965 chipset.

Also, I should note that there is no KDE3-splash Screen when logging in.

And there are still kde4 packages installed like kde-base, kdm, kdehelpcenter,...

Regarding /usr/kde3/bin - there is only a broken link named kdesu in it (pointing to kdesudo)


So, what's next? I purged every kde-stuff I could find and then created the attached log files from 'apt-get install kubuntu-desktop-kde3'. The first one is without backports in sources.list, the second one includes backports.

Do these logs look ok for you?

Again, I'd like to mention that I am running Ubuntu Intrepid AMD64...


Note: when purging kde3, I always got the following error:
```
Removing kio-umountwrapper-kde3 ...
dpkg-divert: mismatch on package
  when removing `diversion of /opt/kde3/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper'
  found `diversion of /opt/kde3/share/apps/konqueror/servicemenus/media_safelyremove.desktop to /opt/kde3/share/apps/konqueror/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper-kde3'
dpkg: error processing kio-umountwrapper-kde3 (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper-kde3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.
```
...my workaround is 'rm /var/lib/dpkg/info/kio*'

---

### Post by jeromio on 2009-03-10
This will be a long post. I did install the kde-guidance-kde3 and now have the user manager plugin to system settings. However, it was broken. I figured it would come back after a reboot. I think I went too far. I tried installing compiz-kde3. This seemed to work, no major errors. But compiz didn't actually work. I could set the various options from the desktop-effects dialog, but nothing changed. So quit X and I did another update/upgrade-dist. That resulted in not being able to boot X. I gave up last night and did another update/upgrade this morning. Now I can boot into X, but everything is grey or white except the mouse pointer. As in, I have a grey screen, one or two whit boxes and a white strip where the panel should be. So if I click where the "K" should be (the start-menu), a white box (the K-menu) pops up. But it's all just whiteness.

I noticed that emerald-kde3 was not installed. However, when I try to install it, it has deps to the "normal", non kde3 packages and so it won't install:

```
jeromio@blirp:~$ sudo apt-get install emerald-kde3
[sudo] password for jeromio:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  compiz-core compiz-plugins
Suggested packages:
  nvidia-glx
Recommended packages:
  emerald-themes-kde3
The following NEW packages will be installed:
  compiz-core compiz-plugins emerald-kde3
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/746kB of archives.
After this operation, 3531kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  emerald-kde3
Install these packages without verification [y/N]? y
(Reading database ... 297786 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_1%3a0.7.8-0ubuntu4.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_1%3a0.7.8-0ubuntu4.1_amd64.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/compiz.1.gz', which is also in package compiz-core-kde3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.7.8-0ubuntu4.1_amd64.deb) ...
Selecting previously deselected package emerald-kde3.
Unpacking emerald-kde3 (from .../emerald-kde3_0.7.2-0ubuntu7_amd64.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_1%3a0.7.8-0ubuntu4.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried removing compiz (I'm doing everything via ssh from another box), but I still get the grey/white desktop. Also, I can't test w/ another user b/c I never got to a point where user manager was working.

---

### Post by jeromio on 2009-03-10
Fixed my weird white/grey screen issue by dropping back to an old xorg.conf backup file. Still no compiz, but I do have my system up again. BTW, the user manager plugin *does* work now.

---

### Post by chemist109 on 2009-03-10
First of all, thanks to the MadScientist for helping out all of us KDE 3 types until KDE 4 is complete enough to use.

I've been experimenting with setting up a KDE 3 only system using the alternate install disk for intrepid.

First, boot up the alternate disk and hit F4 and choose "install a command line system".

Then go through the standard debian/ubuntu text based installer.

When you get to the command line, log in and update the system to get all the newest packages:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Then, edit the /etc/apt/sources.list to add the KDE 3 ppa (see the first post on this thread).  

```
sudo nano /etc/apt/sources.list
```

```
#KDE3 Intrepid PPA
deb http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kb9vqf/ubuntu intrepid main
```

Next, install the KDE 3 desktop as suggested in the first post.

```
sudo apt-get update && sudo apt-get install kubuntu-desktop-kde3
```

The only problem I had was that /etc/network/interfaces had set up eth0 to start at boot.  This prevents network manager from managing that interface.  It also caused the system to hang for about 30 sec. at boot while it looked for a network connection.  This is easily fixed-- just comment out the lines involving the interface (eth0), in /etc/network/interfaces like this:

```
sudo nano /etc/network/interfaces
```

```
#auto eth0
#iface eth0 inet dhcp
```

I had to start jockey-kde to get proprietary video drivers.  I also had to start knetworkmanager.  I've only been using the system for a little while, but it seems to work just fine.

---

### Post by jeromio on 2009-03-12
Everything pretty much works on my system, but KDE is still really slow. And it appears to be only KDE (QT) apps such as konqueror (very, very slow), K9copy, K3b. Gnome apps (such as firefox) don't suffer the painfully slow redraw issues - at least that's my impression.

I tried creating a new user (via the KDE settings manager) so I could see if the problem is related to my specific config. However, I can't log that user into to X. After the login screen, I get an error dialog: "Xsession: unable to start X session --- no "/home/gempuser/.xsession" file, no "/home/tempuser/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.

I also can't switch users from an X windows session. I don't have that option from the login or logout dialog and while in a session (with my pre-exising user account), if I press Ctrl-Alt+F6, I get a console login, not an X login. Oddly, F8 gives me a console with the tail end of some kind of failed boot up sequence (can't copy paste it and can't find any logs in /var/log that have this in there, so this is me transcribing):

```

Starting K Display Manager: kdm-kde3                                  [OK]
 * Starting anac(h)ronisitic cron anacron                             [OK]
 * Starting deferred execution scheduler atd                          [OK]
 * Starting periodic command scheduler crond                          [OK]
 * Enabling additional executable binary formats binfmt-support       [OK]
 * Checking battery   state...                                        [OK]
grep: /usr/lib/kde4/etc/kde4/kdm/kdmrc: No such file or directory
Not starting K Display Manager (kdm-kde4); it is not the default display manager.

```I get that every time in that session (across reboots).

BTW, I had the white screen issue again. Something is overwriting my xorg.conf with bad data.

Very weird. I apparently have multiple issues in parallel. I think I may just need to re-install....:(

---

### Post by jeromio on 2009-03-12
More strangeness. I had 2 other existing user accounts on system. I tried one and was able to log in to X/KDE and everything was fine - no white screen. The other one had the same problem as my tempuser: no .xsession found. So I tried comparing the .kde3 files between this working user account and my main (white screen) account. I found a few minor differences in some files and decided to copy the startupconfig and startupconfigfiles over from the working account to the white screen account. Then I rebooted. Didn't help. Then logged into the working account. White screen!

I thought perhaps trying to reconfigure kdm would help. So I tried

```
sudo dpkg-reconfigure kdm-kde3
```

and I got

```
cat: /etc/X11/default-display-manager: No such file or directory
[: 19: /usr/kde3/bin/kdm: unexpected operator
```

So, that's odd b/c the kdm binary is in /opt/kde3/bin/. And my default-display-manager (which does exist) has 
```
/opt/kde3/bin/kdm
```

I'm mired in a pit of dispair....:(

---

### Post by madscientist159 on 2009-03-12
> **jeromio said:**
> More strangeness. I had 2 other existing user accounts on system. I tried one and was able to log in to X/KDE and everything was fine - no white screen. The other one had the same problem as my tempuser: no .xsession found. So I tried comparing the .kde3 files between this working user account and my main (white screen) account. I found a few minor differences in some files and decided to copy the startupconfig and startupconfigfiles over from the working account to the white screen account. Then I rebooted. Didn't help. Then logged into the working account. White screen!

I thought perhaps trying to reconfigure kdm would help. So I tried

```
sudo dpkg-reconfigure kdm-kde3
```

and I got

```
cat: /etc/X11/default-display-manager: No such file or directory
[: 19: /usr/kde3/bin/kdm: unexpected operator
```

So, that's odd b/c the kdm binary is in /opt/kde3/bin/. And my default-display-manager (which does exist) has 
```
/opt/kde3/bin/kdm
```

I'm mired in a pit of dispair....:(

Hi jeromio,

Hate to say this, but it seems that your system is hosed.  It sounds like the core system itself is messed up (X, your video drivers, maybe even the default home directory).  It might be easier for you just to re-install. :)

The : 19: /usr/kde3/bin/kdm: unexpected operator is normal--just the upgrade script reacting harmlessly to having not found /usr/kde3/bin/kdm as your default display manager (which is a good thing).

---

### Post by forestwraith on 2009-03-17
I have a note for others of the kde naive among us regarding kde packages.



Following the instructions, installing kubuntu-desktop-kde3, I did not realize right away that this meta-package will NOT install the entire kde3 repository.  Not that it should, but then there will be more kde3 packages to install.  There is no kde-kde3 metapackage in the repository, and maybe that is a bug.  So for instance, things like kdeedu-kde3, kdetoys-kde3 and kweather-kde3 will have to be installed explicitly.



May I suggest, something like "apt-cache -- search '-kde3'|sort|less".  There you can look through all the available packages.



And "dpkg-query -l '*-kde3'|less" or even "dpkg-query -l '*-kde3'|sort|less" will let you see what packages are already installed, and which are not installed.



Similarly, using the Synaptic Package Manager, and doing a custom search on "-kde3", will show the available, installed, and not installed kde3 packages.



And, Tim, maybe you would add a reminder about installing additional kde3 packages to the instructions at [http://apt.pearsoncomputing.net/?](http://apt.pearsoncomputing.net/?)



James

---

### Post by maniaq on 2009-03-19
just want to add my voice to the obvious TORRENT of disappointment with the Ubuntu team over their choice to ditch KDE 3.5

KDE4 is a nice *idea * but until it gets itself stabilised, you have no business forcing it down people's throats as Kubuntu of choice

irresponsible barely covers it

---

### Post by madscientist159 on 2009-03-20
> **maniaq said:**
> just want to add my voice to the obvious TORRENT of disappointment with the Ubuntu team over their choice to ditch KDE 3.5

KDE4 is a nice *idea * but until it gets itself stabilised, you have no business forcing it down people's throats as Kubuntu of choice

irresponsible barely covers it

Hey, as a Kubuntu team member I might take offense at that! ;)

I made this announcement to the mailing list, but figured I should post it here as well:
> The KDE3.5 repository has been migrated to a new team PPA, and in the next month or so I will be heavily modifying the PPA that you are currently using.  

I have updated the instructions on [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) to reflect the new team PPA, so please update your system with the new repository information as soon as possible.  Be sure to update the GPG key as well, by following the instructions under "Add the GPG signing key".

This will not affect your current software installation--the binaries have been copied directly from the existing PPA with no modifications.  I am only requesting that you update the repository locations in an effort to prevent future problems, as the old PPA will become a development/testing PPA in the future.

Thank you, and I hope you enjoy your KDE3.5 installation!

Timothy Pearson
KDE3.5 Maintainer

---

### Post by chemist109 on 2009-03-24
I've install freenx on my KDE3 (only) Intrepid box, but when I attempt to connect, it tries to start a KDE4 session (and fails).  I end up with a black screen after the KDE4 splash disappears.

---

### Post by chemist109 on 2009-03-25
> **chemist109 said:**
> I've install freenx on my KDE3 (only) Intrepid box, but when I attempt to connect, it tries to start a KDE4 session (and fails).  I end up with a black screen after the KDE4 splash disappears.
Answering my own question: In the nx client go to configure and under desktop choose custom.  In the custom settings, check the "Run the following command" radio box and in the space below put: 

```
/opt/kde3/bin/startkde
```

---

### Post by azag on 2009-04-02
i have installed the kde3 from the ppa repo and kde4 neon.
i was very happy with the kde3 in ibex but now using kde4 neon i think kde4.2 is stable enough
so now i want to uninstall kde3 and kde4 neon to have a clean upgrade to kubuntu 9.04 
how can i do this?

---

### Post by madscientist159 on 2009-04-02
> **azag said:**
> i have installed the kde3 from the ppa repo and kde4 neon.
i was very happy with the kde3 in ibex but now using kde4 neon i think kde4.2 is stable enough
so now i want to uninstall kde3 and kde4 neon to have a clean upgrade to kubuntu 9.04 
how can i do this?

The easiest way I can think of off the top of my head is to execute this from a terminal:
sudo apt-get remove kde3*

Please read the package removal list carefully before entering "Y" to make sure that it is not removing something you wanted to keep installed.

As an aside, in Jaunty KDE3.5 and KDE4.x coexist peacefully, so you don't *have* to remove KDE3.5 unless you need disk space or just don't want it around anymore...

Tim

---

### Post by azag on 2009-04-02
> **madscientist159 said:**
> The easiest way I can think of off the top of my head is to execute this from a terminal:
sudo apt-get remove kde3*

Please read the package removal list carefully before entering "Y" to make sure that it is not removing something you wanted to keep installed.

As an aside, in Jaunty KDE3.5 and KDE4.x coexist peacefully, so you don't *have* to remove KDE3.5 unless you need disk space or just don't want it around anymore...

Tim


thanks for your fast reply.

this is the result:
The following packages will be REMOVED:
  akregator amarok-nightly amarok-nightly-kdebase amarok-nightly-kdelibs amarok-nightly-kdesupport
  gdebi-kde gtk-qt-engine-kde4 guidance-power-manager hwdb-client-kde install-package kaffeine
  kde-guidance-powermanager kde-icons-crystal kde-icons-crystalclear kde-icons-crystalproject
  kde-icons-mono kde-icons-noia kde-icons-nuovext kde-icons-oxygen kde-nightly
  kde-nightly-google-gadgets kde-nightly-kdebase kde-nightly-kdeedu kde-nightly-kdegraphics
  kde-nightly-kdelibs kde-nightly-kdemultimedia kde-nightly-kdenetwork kde-nightly-kdepim
  kde-nightly-kdepimlibs kde-nightly-kdeplasma-addons kde-nightly-kdesupport kde-nightly-kdeutils
  kdeaddons-doc-html kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdebase-workspace-libs4+5 kdegraphics-strigi-plugins kdelibs-bin
  kdelibs-data-kde3 kdelibs4c2a kdelibs4c2a-kde3 kdelibs5 kdelibs5-data kdenetwork-doc-html
  kdepimlibs-data kdepimlibs5 kdesudo kdm khelpcenter4 kwin-style-crystal language-pack-kde-en
  language-pack-kde-en-base language-selector-qt libarts1c2a-kde3 libartsc0-kde3 libkdecorations4
  libkdepim4 liblockdev1 libplasma3 pykdeextensions python-kde4 software-properties-kde
  system-config-printer-kde
0 upgraded, 0 newly installed, 65 to remove and 0 not upgraded.
After this operation, 926MB disk space will be freed.
Do you want to continue [Y/n]?


so there is  something wrong with the command line or apt-get?

i see packages from your repo, from kde4neon and i think these -kde4 are from an old kde4 from the ppa repos

---

### Post by madscientist159 on 2009-04-03
> **azag said:**
> so there is  something wrong with the command line or apt-get?

There was something wrong with my memory. ;)

Try this instead:
sudo aptitude remove ~nkde3

Tim

---

### Post by docanime on 2009-04-06
So I was able to get KDE 3.5 installed on top of KDE 4.2 / Jaunty. For a time, I did have gdm, kdm4, and kmd3.5 all running but I got that straighten out by changing things in the rc5.d directory.

Also, Jaunty now uses the KDE 3.5 login instead of KDE 4's. 

But, there are still remenants of KDE4 running along side their KDE3.5 clones on the computer. 

Something is causing kded4 and knotify4 to run. 
Anyone know what scripts start these programs up? I can't find it.

Also, a few KDE programs will be trying to use kdeinit4 or its klauncher to use but it can't find it (i renamed them). 
Anyone know if this default value for which launcher to use (kdeinit4 instead of kdeinit) is stored somewhere?

Thanks in advanced.

---

### Post by mikerobinson on 2009-04-07
I am having problems with the python-kde3-kde3 package, see below:

> $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kde-guidance-kde3: Depends: python-kde3-kde3 but it is not installed
  kde-guidance-powermanager-kde3: Depends: python-kde3-kde3 but it is not installed
E: Unmet dependencies. Try using -f.

$ sudo apt-get install python-kde3-kde3
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  k3b-data libcaptury0 python-kde4-dev libemeraldengine0 libcapseo0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  python-kde3-kde3
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/12.5MB of archives.
After this operation, 54.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  python-kde3-kde3
Install these packages without verification [y/N]? y
(Reading database ... 233014 files and directories currently installed.)
Unpacking python-kde3-kde3 (from .../python-kde3-kde3_3.16.0-0ubuntu4_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/python-kde3-kde3_3.16.0-0ubuntu4_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/kresources.so', which is also in package python-kde3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python-kde3-kde3_3.16.0-0ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is this package a misnomer? Should these packages actually be referring to "python-kde3" instead?

Thanks

---

### Post by red_team316 on 2009-04-07
On a fresh install of Jaunty 9.04 Beta, I installed KDE3. Under Adept, when clicking on the manage repositories in the menu pulldown, it does nothing...

Edit: Also, something is wrong with the /etc/init.d/kdm-kde3 script. When I open vt6 and type:
```

sudo /etc/init.d/kdm-kde3 stop

```
It tells me that
```

kdm-kde3 not running (/var/run/kdm.pid not found)

```
so it is looking for the wrong pid apparently. I found this out when trying to install the NVIDIA Blob 180.44 manually(as I always do. It requires that X is not running.)

---

### Post by Polaris96 on 2009-04-22
That didn't work for me.  

The new repositories came on just fine, although there was an "unknown source" reminder that flashed on the terminal every time I invoked the new repositories.

I followed the install directions exactly using apt in the terminal.  kde3 did come on- sort of.  What I actually wound up with was a mashup of incomplete kde3 and kde4 (I can't tell if kde4 was altered because I haven't really been able to use it from the initial upload)

After apt-get -f 'ing a whole bunch of stuff, I was left with a dependency "python-kde3" that WOULD NOT RESOLVE no matter what I did.

It took an hour of tearing my hair out just to remove kde3 because apt didn't want to budge until the unresolvable dependency was resolved.  I was eventually able to remove everything by playing with aptitude (I apologize I don't remember exactly how I finally got it to work).

I did a clean install of Intrepid onto a brand new AMD athlon 64 machine hoping to tweak it out and leave it for my girlfriend (who is still on windows).  I NOW BELIEVE THAT INTREPID IS NOT AT ALL SUITABLE FOR NON GEEKS.  I will remove the current OS and retrofit Hardy, which, I think, is a lot more robust - at least you can adjust the bloody system settings.

---

### Post by maybeway36 on 2009-04-22
If I were you, I might install Jaunty right now. It's almost done anyways. But if Hardy works, there's no problem sticking with that.

---

### Post by cacycleworks on 2009-04-23
> **maybeway36 said:**
> If I were you, I might install Jaunty right now. It's almost done anyways. But if Hardy works, there's no problem sticking with that.

Does Jaunty support KDE3? Or is KDE4 finally usable? I specifically care about khotkeys. I'm in another cruch with work, so it might be a while before I get to try upgrading from Hardy...

Thanks!
Chris

---

### Post by maybeway36 on 2009-04-23
The instructions on [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) work for Jaunty. The only problem is with a few packages like amarok-kde3 and gwenview-kde3 which refer to packages that have been renamed.

---

### Post by jtgd on 2009-05-09
I installed Intrepid back in January, could not stand the KDE4.2 beta, installed the KDE3.5.10 from pearsoncomputing and used it happily for a while.  I upgraded to Jaunty last week and it continued running KDE3.  I seem to be missing out on some of the newest packages, so I decided to give KDE4 a try again.

I tried installing kde (apt-get install kubuntu-desktop) and rebooted.

It does not go into kdm automatically.  I have to log in as root and run kdm manually.

I log in and I get to the desktop and all I see is my mouse pointer and gkrellm.  Black screen.  Does not respond to mouse buttons (no right-click menu).  I have to hit Ctrl-Alt-Delete to log out.  I can run Gnome but I want KDE.

Does anyone know what I have to do to get the regular KDE4 back again?  Thanks for your help.

---

### Post by blackbelt_jones on 2009-06-15
> I see on the homepage that the repo is "fully compatible with KDE4" and I was wondering if that means I can use it to install KDE3 and KDE4 on the same Kubuntu system.

I was about to reply to this post, [I]when I noticed that it was ME!
[/I]:lolflag:

Well, Mr. Jones, your mileage may vary, but when I tried it, I had problems with it.  After installing both on the same system, if I tried to open KDE3. both desktops would open at once!  I had a KDE3 panel, a KDE4 panel, a KDE3 menu, a KDE4 menu!  Needless to say, it didn't work.

---

### Post by xylometazolin on 2009-06-15
> **blackbelt_jones said:**
> I see on the homepage that the repo is "fully compatible with KDE4" and I was wondering if that means I can use it to install KDE3 and KDE4 on the same Kubuntu system.

You can install KDE3 and KDE4 on the same system. But there are some conflicts when installing both KDE versions of a package, e.g. yakuake-kde3 and yakuake, since they use the same location for the manual pages. So you have to tell aptitude to ignore those conflicts in order to get both application versions installed.

---

### Post by blackbelt_jones on 2009-07-06
I don't know if this is a bug, but my biggest problem with Mad Scientist's generally excellent KDE3-kubuntu is with finding commands to open KDE3 applications, most significantly konqueror.  in Kubuntu, the command "konqueror" opens The KDE4 version of konqueror, or it would if I had it installed.  An apt-get search predictably reveals that the kde3 version of konqueror is named konqueror-kde3, but typing konqueror-kde3 in konsole or in the run-application window doesn't open konqueror-kde3, or anything else.  Is there an applicable command?

I like to use fluxbox sometimes, and customizing fluxbox uses direct text editing of files, so this is a big problem for me.

---

### Post by madscientist159 on 2009-07-06
> **blackbelt_jones said:**
> I don't know if this is a bug, but my biggest problem with Mad Scientist's generally excellent KDE3-kubuntu is with finding commands to open KDE3 applications, most significantly konqueror.  in Kubuntu, the command "konqueror" opens The KDE4 version of konqueror, or it would if I had it installed.  An apt-get search predictably reveals that the kde3 version of konqueror is named konqueror-kde3, but typing konqueror-kde3 in konsole or in the run-application window doesn't open konqueror-kde3, or anything else.  Is there an applicable command?

I like to use fluxbox sometimes, and customizing fluxbox uses direct text editing of files, so this is a big problem for me.

Take a quick look at the "Executing KDE3.5 applications from another DE" section here: [https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty#Executing%20KDE3.5%20applications%20from%20another%20DE](https://wiki.kubuntu.org/Kubuntu/Kde3/Jaunty#Executing%20KDE3.5%20applications%20from%20another%20DE)

It should answer any questions you have.

Tim

---

### Post by Nxx on 2009-07-09
Hi!

I wonder why I cannot install kde3 from Jaunty. I've added your repo, but there is no kubuntu-desktop-kde3, kdebase-kde3 and kde-kde3 packages as well as core libraries. If to install from Intrepid repo, there multiple problems emerge. 

- It is incompatible with nvidia-190 drivers (simply tries to remove them).
- Compiz-kde3 conflicts with existing compiz breaking the system.
- No Kvirc package and the old Qt3 Kvirc package from old Ubuntu does not woirk either (it asks for libarts1c2a, while in the system already exists libarts1c2a-kde3).
- Installing KDE4 in parallel breaks the system.
- Compiz-kde3 has an older version than that available for KDE3 in OpenSuse.
- Gnome applications and Wine do not have icons in the main menu
- When uninstalling kde3, all Qt3 applications uninstalled as well (such as Gambas2 and HBasic). They should be reinstalled manually after this.

Thanks.

---

### Post by maybeway36 on 2009-07-09
On Jaunty, you have to add both the Jaunty and Intrepid KDE3 repositories.

---

### Post by manij on 2009-08-17
I ave installed KDE3.5 in Jaunty. I have trouble with Knetworkmanager. It simply does not connect.

Starting nm-applet from terminal works. unfortunately, I'm not able to close the terminal. It kills the nm-applet. Is there a way to get around this?

---

### Post by madscientist159 on 2009-08-17
> **manij said:**
> I ave installed KDE3.5 in Jaunty. I have trouble with Knetworkmanager. It simply does not connect.

Starting nm-applet from terminal works. unfortunately, I'm not able to close the terminal. It kills the nm-applet. Is there a way to get around this?

Yes.  Run nm-applet from the KDE run dialog, which can be accessed from the Start menu or by pressing Alt+F2.

I know about knetworkmanager's shortcomings and I might be willing to try fixing them, but it isn't a high priority because nm-applet works just fine.

Tim

---

### Post by manij on 2009-08-17
> **madscientist159 said:**
> Yes.  Run nm-applet from the KDE run dialog, which can be accessed from the Start menu or by pressing Alt+F2.

I know about knetworkmanager's shortcomings and I might be willing to try fixing them, but it isn't a high priority because nm-applet works just fine.

Tim

Thanks Tim. I just don't want have to keep the terminal on all the time. I'll try the route you suggested.

---

### Post by Stevie-C on 2009-08-24
I followed the instructions here to the letter and ran into the following issue which is REALLY impacting the usability of the installation for me.

When I try to change the screensaver, X dies and kicks me back to the KDM login screen.

though one piece of GOOD news: I was able to use knetworkmanager without a hitch to connect to a WPA-encrypted wi-fi network

---

### Post by uboot on 2009-08-26
As for [http://bugs.pearsoncomputing.net/](http://bugs.pearsoncomputing.net/) didn't work (Bugzilla has suffered an internal error...), I post it here:


On Jaunty AMD64, kdebase-kde3 recommends kdm (kde4), thus lots of KDE4-packages would get installed. I need to manually deselect them and resolve conflicts by selecting kdm-kde3.

---

### Post by manij on 2009-09-03
Pearsoncomputing appears to be down. 

Could someone post the links to repos for jaunty

DO I simply substitute Jaunty instead of intrepid in the address below?

deb [http://ppa.launchpad.net/kb9vqf/ubuntu](http://ppa.launchpad.net/kb9vqf/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/kb9vqf/ubuntu](http://ppa.launchpad.net/kb9vqf/ubuntu) intrepid main

?????

---

### Post by red_team316 on 2009-09-04
> **manij said:**
> Pearsoncomputing appears to be down. 

Could someone post the links to repos for jaunty

DO I simply substitute Jaunty instead of intrepid in the address below?

deb [http://ppa.launchpad.net/kb9vqf/ubuntu](http://ppa.launchpad.net/kb9vqf/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/kb9vqf/ubuntu](http://ppa.launchpad.net/kb9vqf/ubuntu) intrepid main

?????

you must have those as well as jaunty lines (4 lines total).

---

### Post by sandyd on 2009-09-10
The repository currently conflicts with the KDE 4 backports causing some apps (such as k3b) to be non-installable.

help!!!

the conflicts are mainly with kdelibs4c2a

---

### Post by manij on 2009-09-19
Dell vostro 1000
AMD tk-57
2G ram

Intrepid IBEX

KDE3.5 remix

Everything works and then it just doesn't

I use nm-applet to manage my network connection. Sometimes it disconnects from the network and will not reconnect unless I restart the machine.

This is new behavior in the past couple of weeks. Any suggestions?

---

### Post by nekron29 on 2009-10-25
Just installed kde 3.5 in karmik.

Everything went well ( i am using the gnome version of karmic, no kde4) yet i have a problem with the process "kdesktop" it;s taking high load on my cpu - 70-80%. Do you have any idea why ? and what can i do to stop behaving like this.

Also it seems i am not able to do a restart or a shutdown as these options are missing from the start menu.

Using ubuntu 9.10 rc.

thanks

---

### Post by madscientist159 on 2009-10-25
> **nekron29 said:**
> Just installed kde 3.5 in karmik.

Everything went well ( i am using the gnome version of karmic, no kde4) yet i have a problem with the process "kdesktop" it;s taking high load on my cpu - 70-80%. Do you have any idea why ? and what can i do to stop behaving like this.

Also it seems i am not able to do a restart or a shutdown as these options are missing from the start menu.

Using ubuntu 9.10 rc.

thanks

What happens if you log out and log back in (without restarting the computer)?  Does the problem disappear?

Also, what graphics hardware are you using?  If you don't know, go to a terminal and run lspci , then post the output here.

---

### Post by manij on 2009-10-29
> **nekron29 said:**
> Just installed kde 3.5 in karmik.

Everything went well ( i am using the gnome version of karmic, no kde4) yet i have a problem with the process "kdesktop" it;s taking high load on my cpu - 70-80%. Do you have any idea why ? and what can i do to stop behaving like this.

Also it seems i am not able to do a restart or a shutdown as these options are missing from the start menu.

Using ubuntu 9.10 rc.

thanks

Could you help me with the repo addresses for KDE 3 install in KARMIC? Thanks

Mani

---

### Post by djobbito on 2009-10-29
> **manij said:**
> Could you help me with the repo addresses for KDE 3 install in KARMIC? Thanks

Mani

Hi,

You shall the details in this page:
[http://apt.pearsoncomputing.net/install.html](http://apt.pearsoncomputing.net/install.html)

```
1. Add these lines to your /etc/apt/sources.list file:
For Karmic [STABLE] (2 lines):
deb [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main


2. Add the GPG signing key:
wget [http://apt.pearsoncomputing.net/public.gpg](http://apt.pearsoncomputing.net/public.gpg)
sudo apt-key add public.gpg

3. Install KDE 3.5:
sudo apt-get update
sudo apt-get install kubuntu-desktop-kde3
```


Enjoy

---

### Post by leorolla on 2009-10-30
For green users like me, it works smooth and fine!!!

What I did:

1. Install Ubuntu 9.10

2. Follow the simple instructions from [http://apt.pearsoncomputing.net/install.html](http://apt.pearsoncomputing.net/install.html) except for "sudo apt-get install kubuntu-desktop-kde3"

3. Follow the not-so-simple instructions from [https://wiki.kubuntu.org/Kubuntu/Kde3/Karmic#Executing%20KDE3.5%20applications%20from%20another%20DE]("https://wiki.kubuntu.org/Kubuntu/Kde3/Karmic#Executing%20KDE3.5%20applications%20from%20another%20DE")


Result: You can install KDE 3.5 applications inside Gnome.

Drawback: I still couldn't find a way to get it done in an automated way: associating filenames, creating icons, and setting the environment variables.

Question: How should I fix the above missing features (menu icons, environment variables, filename associations) ?

---

### Post by leorolla on 2009-10-31
[apt.pearsoncomputing.net/]("http://apt.pearsoncomputing.net/public.gpg")

is offline!

Anyone knows what happened?

---

### Post by madscientist159 on 2009-10-31
> **leorolla said:**
> [apt.pearsoncomputing.net/]("http://apt.pearsoncomputing.net/public.gpg")

is offline!

Anyone knows what happened?

Yup; I upgraded the server to Karmic and the new Apache installation gave me quite a bit of grief (SSL virtual hosts are apparently broken under 2.2.12).  Downgrading Apache has fixed the issue and the site is now back online.

Sorry for the inconvenience!

Tim

---

### Post by moparisthebest on 2009-11-25
So what is the recommended way to upgrade from Jaunty using KDE 3.5 to Karmic?  If none of the package names changed I suppose using the Ubuntu server upgrade tool would work after disabling the 3.5 jaunty repos and then adding the 3.5 karmic repos and doing an apt-get update and apt-get upgrade.  Does anyone know why this plan would not succeed?

---

### Post by rpeters on 2009-12-07
Persistent problem with KDE3 repository updates ](*,)

For a few months now, after doing sudo apt-get update, everything updates, with this exception: ```
Failed to fetch http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.bz2  Hash Sum mismatch
```

In early November installed Kubuntu Karmic from the CD. The problem persisted.

Just tried the KDE3.5 Repository Installation Instructions on [http://apt.pearsoncomputing.net/install.html](http://apt.pearsoncomputing.net/install.html). Same problem.

Maybe I'll have to go to ppa.launchpad.net/kde3-maintainers/ppa/ubuntu/ and download their dists/karmic/main/binary-i386/Packages.bz2 file to update from, or go to their /pool/main/ and look for updated .deb files.  But it would be nice to solve this problem.  Any ideas?

---

### Post by madscientist159 on 2009-12-07
> **rpeters said:**
> Persistent problem with KDE3 repository updates ](*,)

For a few months now, after doing sudo apt-get update, everything updates, with this exception: ```
Failed to fetch http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.bz2  Hash Sum mismatch
```

In early November installed Kubuntu Karmic from the CD. The problem persisted.

Just tried the KDE3.5 Repository Installation Instructions on [http://apt.pearsoncomputing.net/install.html](http://apt.pearsoncomputing.net/install.html). Same problem.

Maybe I'll have to go to ppa.launchpad.net/kde3-maintainers/ppa/ubuntu/ and download their dists/karmic/main/binary-i386/Packages.bz2 file to update from, or go to their /pool/main/ and look for updated .deb files.  But it would be nice to solve this problem.  Any ideas?

Are you located behind a transparent Internet proxy system?

---

### Post by rpeters on 2009-12-07
> Are you located behind a transparent Internet proxy system?

I'm currently behind what is probably the biggest content filter of all, aka The Great Firewall.  But as far as I remember, the problem existed before I came here in August.  However - it could be a factor.  I can take the laptop along on my next trip outside the proxy area and see if it makes a difference.

---

### Post by eb53 on 2009-12-13
> **nekron29 said:**
> Just installed kde 3.5 in karmik.

Everything went well ( i am using the gnome version of karmic, no kde4) yet i have a problem with the process "kdesktop" it;s taking high load on my cpu - 70-80%. Do you have any idea why ? and what can i do to stop behaving like this.

Also it seems i am not able to do a restart or a shutdown as these options are missing from the start menu.

Using ubuntu 9.10 rc.

thanks
-----------------------------------------------------------------------

I have the same problem, on two different machines with Karmic/kde3 installed two different ways.  I run 6 or 8 desktops and only Desktop 1 soaks up massive cpu, with gkrellm reporting 'kdesktop-kde3' as the culprit.  The other Desktops are fine, but Desktop 1 exhibits the syndrome any time I visit it.

When I boot with Desktop1 as default, there's a "Monitoring file progress.." pop-up that stays up until I change desktops for the first time, and then it's gone.  If I boot into any other desktop but Desktop 1, everything is fine - except when visiting Desktop 1, which again eats up massive CPU time until I go to another desktop.

This happens on exactly the same way on two different machines (and I have several others that are similarly configured but don't exhibit the syndrome at all).  Both are up-to-date with the latest upgrades and kernel 2.6.31-16:

1. A Dell Precision 390 desktop with an NVidia GeForce (regardless of which drivers I enable).  This was a plain-vanilla Ubuntu install, with KDE-3 installed on top per the usual kde3-maintainers PPA (Pearson method...).  The kernel is plain generic.

2. A brand-new Dell Lattitude Z laptop with an Intel GMA X4500 HD adapter.  Installed Pearson's Karmic/KDE3 remix from scratch.  This one runs the "pae" version of the kernel.

The problem is only manifest when Desktop 1 is active, so the workaround is obvious.  But it would be nice to be able to use Desktop 1 as well.

---

### Post by madscientist159 on 2009-12-13
> **eb53 said:**
> -----------------------------------------------------------------------

I have the same problem, on two different machines with Karmic/kde3 installed two different ways.  I run 6 or 8 desktops and only Desktop 1 soaks up massive cpu, with gkrellm reporting 'kdesktop-kde3' as the culprit.  The other Desktops are fine, but Desktop 1 exhibits the syndrome any time I visit it.

When I boot with Desktop1 as default, there's a "Monitoring file progress.." pop-up that stays up until I change desktops for the first time, and then it's gone.  If I boot into any other desktop but Desktop 1, everything is fine - except when visiting Desktop 1, which again eats up massive CPU time until I go to another desktop.

This happens on exactly the same way on two different machines (and I have several others that are similarly configured but don't exhibit the syndrome at all).  Both are up-to-date with the latest upgrades and kernel 2.6.31-16:

1. A Dell Precision 390 desktop with an NVidia GeForce (regardless of which drivers I enable).  This was a plain-vanilla Ubuntu install, with KDE-3 installed on top per the usual kde3-maintainers PPA (Pearson method...).  The kernel is plain generic.

2. A brand-new Dell Lattitude Z laptop with an Intel GMA X4500 HD adapter.  Installed Pearson's Karmic/KDE3 remix from scratch.  This one runs the "pae" version of the kernel.

The problem is only manifest when Desktop 1 is active, so the workaround is obvious.  But it would be nice to be able to use Desktop 1 as well.

Hmmm...very odd.  I run over 20 machines with Karmic and KDE3 and have yet to see this bug (not that it doesn't exist; just makes troubleshooting more difficult).

Can you try creating a brand new user, log in under that user with KDE3, and then see if the problem exists there?  This is to see if any of the configuration files in ~/.kde3 are the problem.

Beyond that, troubleshooting becomes more arcane--let's see of the config files are the problem first. :D

Tim

---

### Post by eb53 on 2009-12-13
Tim - that was fast, thanks.  But I've resolved the issue, sort of, while encountering a new mystery.  And your suspicion was on the mark.

Short story: the kdesktop-kde3 CPU-hogging problem was caused by setting Pager Options | Background to Desktop Wallpaper.  Changing it to Elegant or Transparent eliminates the problem.

... After which I can't get the Desktop Wallpaper setting to stick anymore - it won't checkmark - and that's the new mystery.

My old machine had Pager Options | Background set to Desktop Wallpaper for a long time, but the problem only appeared after an an-upgrade about a month or so ago, IIRC.  My new laptop initially wouldn't let me set the Pager Options to Desktop Wallpaper but after several random tries it took, and that's probably when the problem started on that machine.  My brand-new install on a new desktop has not yet allowed me to set that option, and it's fine otherwise.

I hope there's a clue there somewhere...

---

### Post by madscientist159 on 2009-12-13
> **eb53 said:**
> Tim - that was fast, thanks.  But I've resolved the issue, sort of, while encountering a new mystery.  And your suspicion was on the mark.

Short story: the kdesktop-kde3 CPU-hogging problem was caused by setting Pager Options | Background to Desktop Wallpaper.  Changing it to Elegant or Transparent eliminates the problem.

... After which I can't get the Desktop Wallpaper setting to stick anymore - it won't checkmark - and that's the new mystery.

My old machine had Pager Options | Background set to Desktop Wallpaper for a long time, but the problem only appeared after an an-upgrade about a month or so ago, IIRC.  My new laptop initially wouldn't let me set the Pager Options to Desktop Wallpaper but after several random tries it took, and that's probably when the problem started on that machine.  My brand-new install on a new desktop has not yet allowed me to set that option, and it's fine otherwise.

I hope there's a clue there somewhere...

Yes, there is a clue there.  About that time I was heavily reworking the desktop and pager to fully support Compiz (multiple viewport wallpapers and all) and I ran into the same problem with the Desktop Wallpaper option that you did.  Apparently it is still broken; would you mind filing a bug at [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net) (on or after 12/15/2009; server is down due to disk failure at the moment)?  Otherwise I tend to forget about users' bugs. ;)

Thanks!

Tim

---

### Post by eb53 on 2009-12-13
> **madscientist159 said:**
> Yes, there is a clue there.  About that time I was heavily reworking the desktop and pager to fully support Compiz (multiple viewport wallpapers and all) and I ran into the same problem with the Desktop Wallpaper option that you did.  Apparently it is still broken; would you mind filing a bug at [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net) (on or after 12/15/2009; server is down due to disk failure at the moment)?  Otherwise I tend to forget about users' bugs. ;)

Thanks!

Tim
No problem.  And now that I realize which Tim you are, thank you for keeping kde3.5 alive!  It must be quite the effort, for which I'd bet I'm not the only one who's vastly appreciative.

---

### Post by d3matt on 2009-12-16
so I love the kde3.5 remix :D

I'm just having trouble with sound when I integrated kde3.5 into my existing ubuntu install.  Any suggestions?

Edit:  Found the PulseAudio Volume Control... Somehow, my output device got muted.  Wierd!

---

### Post by Sanne on 2009-12-17
Hi all,

I installed Karmic 64Bit yesterday as a command line system, then xorg, kdebase-kde3, and now I'm working my way up to a minimal system with my beloved Kde3 :). So far it works very well, and I want to express my thanks to you Tim for your work!

I used to measure my cpu temperatures and fan speed with ksensors but couldn't find it in the Kde3 repository as ksensors-kde3. Would you consider adding this package to the archive, by any chance?

Thanks again,
Sanne

**Edit:** For anybody with the same problem, I found a nice replacement for Ksensors named [Kima]("http://kima.sourceforge.net/") which is available as package kima-kde3.

---

### Post by Bladeforger on 2010-06-07
KGoldRunner

THANKS!!!!!

I used this information, and the corresponding wiki, to install KDE3.5 and then to install the older version of KGoldRunner.  It works!!!!  

I love the older version because (guess it's a difference with the KDE 4 not processing keystrokes as fast) the version for KDE4 isn't as fast at processing the keystrokes.  Digging is a hassle.  

NOW, I have the KDE3 version of KGoldRunner back on my Karmic box.  Yea!!!

Many grateful thanks to MadScientist and everyone else who has helped with the project!!!!!!!!!!!!! 
:P

Keith

---

### Post by manij on 2010-07-18
Hi,

I'm not able mount the other partitions on my hard drive with "write"
permission in KDE 3.5 Trinity. Only way I can even mount them is thro' editing
fstab. Even then It does not let modify the contents. I don't have this problem
when I run Gnome Help!

Lucid Lynx
Gnome and KDE 3.5 Trinity

---

### Post by DemonSharkKisame on 2010-08-31
Hello, I stumbled upon the Trinity project out of boredom one day and it seemed to catch my attention, as I've never used KDE 3.5 and I want to see what the differences between this and KDE 4 are. I've got the correct repositories set up, but when I try to install the package kubuntu-desktop-kde3, it fails because of an error involving sudo (I use Ubuntu 10.04). Is it normal for this package to try and remove sudo, or is this a bug?

---

### Post by manij on 2010-09-09
> **DemonSharkKisame said:**
> Hello, I stumbled upon the Trinity project out of boredom one day and it seemed to catch my attention, as I've never used KDE 3.5 and I want to see what the differences between this and KDE 4 are. I've got the correct repositories set up, but when I try to install the package kubuntu-desktop-kde3, it fails because of an error involving sudo (I use Ubuntu 10.04). Is it normal for this package to try and remove sudo, or is this a bug?

Do the following

The workaround is to temporarily set a root password, install sudo-kde3, then
unset the root password.  The following commands should do that:
1. sudo passwd
2. Enter a new (temporary) root password at the prompt
3. sudo apt-get install sudo-kde3
4. sudo passwd -l root


I had the same issue. this fixes it. courtesy of Tim pearson

---

### Post by DemonSharkKisame on 2010-11-02
Finally decided to install KDE3/Trinity after upgrading to 10.10, and so far, TDE works magnificently... though GNOME seems to be FUBAR'd. Any clue as to why this is or how I can fix it?

---

### Post by Sanne on 2010-11-03
DemonSharkKisame, this thread doesn't seem to be very active anymore. You might want to post to the [Kubuntu KDE3/Trinity user mailing list]("http://apt.pearsoncomputing.net/mailinglist.html"), you should get more help there.

---

### Post by DemonSharkKisame on 2010-11-03
lol, that's okay, I managed to fix GNOME anyway... just needed to get into IceWM and switch out the theme GNOME was using from Qt to a native GTK theme :)

---

### Post by Sanne on 2010-11-03
Glad you got it working. :)

---

### Post by samwyse on 2010-11-15
Any chance getting the three viewmode buttons back in Konqueror? The patch in comment #15 [https://launchpad.net/ubuntu/+source/kdebase/+bug/43949](https://launchpad.net/ubuntu/+source/kdebase/+bug/43949) doesn't work anymore.

---

### Post by samwyse on 2010-12-12
> **samwyse said:**
> Any chance getting the three viewmode buttons back in Konqueror? The patch in comment #15 [https://launchpad.net/ubuntu/+source/kdebase/+bug/43949](https://launchpad.net/ubuntu/+source/kdebase/+bug/43949) doesn't work anymore.

Applying the patch in /opt/kde3/share/services/ 
instead of /usr/share/services/ works.

---

