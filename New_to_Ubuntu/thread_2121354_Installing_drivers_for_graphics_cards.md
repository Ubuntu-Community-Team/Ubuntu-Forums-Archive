---
title: "Installing drivers for graphics cards"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by WesternRyno on 2013-03-01
Hi, I read in the forums that using the OEM driver should be the last option for Ubuntu users.  Curious why this is so?  I have a new Lenovo with an Nvidia GE 610M card and Ubuntu 12.04 is not recognizing it.  I have seen the options in the forum and I will try them, just curious why I can't use the one offered from Nvidia and if anyone has any current advice?  Thanks!

---

### Post by Mr. Shannon on 2013-03-01
Looking that card up on NVIDA's site it says it supports optimus, thus it is designed to work in tandem with the integrated graphics on your processor.  If your computer is setup in this way (as mine is) then that is why Ubuntu does not recognize it.  Last time I heard NVIDIA had not released OEM drivers for optimus support on linux.  This leaves you with three options.

1. Go into the BIOS and turn the video card off and use the integrated graphics.

2. Go into the BIOS and set the computer to always use the NVIDIA card (uses more power).  Ubuntu might recognize the card after this and offer to install drivers.  I have not tested this.

3. Use [http://bumblebee-project.org](http://bumblebee-project.org).  This will allow you to launch an application and tell it to use the NVIDIA card.  NOTE: this in not system wide, it is a command line program that allows you to launch a program and have it use the dedicated graphics.  This is what I use.  However, unless you game or use other graphics heavy applications you will probably find that you hardly ever use it.

---

### Post by Bashing-om on 2013-03-01
WesternRyno;
In response to why not use OEM drivers...They have no direct support from linux and when kerenel and or Xserver, GUI updates are performed it breaks the initilaizations to the driver, requiring each time to (re)install the driver.
Now the case at hand is a bit different, somewhat old info, but most likely still apt:
> Your 610M is an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See this link here for installing the drivers: Switchable laptop graphics issues on Ubuntu 12.04?
This link for howto to get the driver:
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)

Hope this helps

[RIGHT]
[/RIGHT]

---

### Post by WesternRyno on 2013-03-01
Sweet!  Thanks a lot for this info man, I'm going to go now and try to set this up.  Will post results.

---

### Post by WesternRyno on 2013-03-01
@ Mr Shannon  Question regarding option 1.  In my configuration it lists Graphic Device [Optimus] with an option to change it to UMA only.  Is this the equivalent to turning the video card off?

Thanks for your help by the way!

---

### Post by WesternRyno on 2013-03-01
@Mr Shannon
 Which option do you use?  

edit:  never mind, just re-read what you wrote.

---

### Post by Paqman on 2013-03-01
> **WesternRyno said:**
>  just curious why I can't use the one offered from Nvidia!

On Linux you generally get all your software straight from your distro. You don't have to go and collect it from fifty different places. You get it all straight from the repositories. That means it's been tested with the distro, and you can use a single package manager to do all your installs, updates and removals. It's much cleaner, simpler and easier than the messy Windows way.

---

### Post by WesternRyno on 2013-03-01
@paqman
I see, this makes perfect sense.  Thanks for that.....continuing to ride the learning curve here.

---

### Post by grahammechanical on 2013-03-01
This post [http://ubuntuforums.org/showthread.php?t=2121367](http://ubuntuforums.org/showthread.php?t=2121367) is an example why I have resisted any temptation to install proprietary video drivers from the OEM web site. Regards.

---

### Post by WesternRyno on 2013-03-01
@bashing om

Thanks for the link you supplied.  I'm going to follow it now and install bumblebee.  I have one last query on this subject.  In the thread from the link, it says:

Then when you need 3D graphics for a program, run it as optirun program. To save power on laptops, it runs only that single program through your nvidia graphics card. To start nvidia-settings, run this optirun nvidia-settings -c :8

How does one run a program, such as Cairodock, as an optirun program?  Is this from the terminal?

---

### Post by Bashing-om on 2013-03-01
WesternRyno;
I do not run with optimus and/or Bumblebee// But, my recolection on the matter is on the command line preceed the program/application name on the command line with the parameter "optirun". As to how it applies to the utility "cairodock" ; I do not know but can not see how optirun applies to a desk top utility.
There is a lot of info on the 'net in respect to "optirun". Might I suggest a quick "Google" search on the term... it returns lots of hits.
[INDENT=2]not much help now, but still here in the event I can

[/INDENT]

---

### Post by WesternRyno on 2013-03-01
Well, I think I am done trying to get Ubuntu to work on my new Ultrabook.  After installing bumblebee to the letter, I cannot reboot into Ubuntu and get either the black screen or the purple screen.  I see how it works well for older computers, but this has been nothing but a week long hassle for me.  I'm out.

---

### Post by Bashing-om on 2013-03-01
WesternRyno;
Sorry to hear that and regretfull that I have not been of sufficient help. Have patience and others may offer better support.
[INDENT=2]hang in there

[/INDENT]

---

### Post by Mr. Shannon on 2013-03-01
> **WesternRyno said:**
> Well, I think I am done trying to get Ubuntu  to work on my new Ultrabook.  After installing bumblebee to the letter,  I cannot reboot into Ubuntu and get either the black screen or the  purple screen.

Sorry to hear that.  Did you use the ppa to install (you should).  Also, did you use the ubuntu-x-swat repository (you should not).  If you could post what commands you used to install bumblebee that would help.

> **WesternRyno said:**
> I see how it works well for older computers, but this  has been nothing but a week long hassle for me.  I'm out.

My less than 6 month old Lenovo ThinkPad works fine with optimus.  I remember having some trouble getting optimus to run correctly at first but I don't remember it causing boot issues.

If all you want your graphics card for is Cairodock then I suggest you let the integrated graphics card handle that.  You can undo the install of bumblebee and the NVIDIA drivers (hopefully fixing your system) by using ctrl+alt+F1 to switch to tty1.  Login and then execute the following commands:

```
sudo apt-get autoremove --purge bumblebee bumblebee-nvidia nvidia-common nvidia-current nvidia-settings
```

then reboot and select your integrated graphics card in the BIOS (mine is an option under display).  My BIOS says integrated graphics not not UMA, but UMA does have something to do with Intel integrated graphics so that might be it.  The option should let you chose between optimus, NVIDIA, and the integrated card.  Some systems may not have all those options however.

If it is a new computer then it will probably have an Intel 3000 or Intel 4000 integrated card in it which is plenty powerful for most users.  I drive two full HD screens off of one and sometimes play video at the same  time (without the NVIDIA card).  Disclaimer: my CPU is a quad core hyperthreaded i7 so that may account for some of that performance.

---

### Post by WesternRyno on 2013-03-01
Mr. Shannon,

SIr, I could really use any assitance.  I took a break, formatted my drives, did a fresh install of 12.04 and have been re-attempting bumblebee, but to no avail.  I've gotten close, but no cigar.  I followed what seemed like solid instructions on the following links,  but was met with an E:  unable to locate package Bumblebee-nvidia and then got you have held broken packages.

[http://bumblebee-project.org/install.html#Ubuntu](http://bumblebee-project.org/install.html#Ubuntu)
[http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work)
[https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu](https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu)

I've purged bumblebee so I can start over but am a bit at a loss.  Will read more but am getting a bit scrambled from all this.  Thanks for any help!

edit:  I should add that I saw threads before hand warning not to download a driver direct from Nvidia so have fortunately avoided that pitfall.  Currently, I have 12.04 running, seemingly stable with a few things I want to overcome before I can consider myself happy with my set-up, the foremost one being the graphics card.  I don't intend to play games, but need it for design.  This is my attempt to use open source on a PC rather than shell out for a Mac.

---

### Post by WesternRyno on 2013-03-01
So this would not be the route to take in the terminal then?


[LIST=1]
[*]Add a PPA containing recent drivers as the one in the repositories is possibly outdated:
  
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
[*]Add the Stable Bumblebee Releases PPA and install Bumblebee using the proprietary NVIDIA driver:
  
sudo add-apt-repository ppa:bumblebee/stable sudo apt-get update sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic 
[/LIST]

---

### Post by WesternRyno on 2013-03-01
Ok, after a bumblebee purge.....here we goooooo


sudo add-apt-repository ppa:bumblebee/stable

sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic

I then get four errors:
E:  Type 'ain' is not known on line 3 in source list etc/apt/source.list.d/bumblebee-stable-precise.list
E:  THe list of sources could not be read
E:  Unable to locate package bumblebee
E:  Unable to locate package bumblebee-nvidia

---

### Post by WesternRyno on 2013-03-02
I now have an additional issue with update manager, despite another purge:

An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/bumblebee-stable-precise.list'

---

### Post by Mr. Shannon on 2013-03-02
> **WesternRyno said:**
> So this would not be the route to take in the terminal then?


[LIST=1]
[*]Add a PPA containing recent drivers as the one in the repositories is possibly outdated:
  
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
[*]Add the Stable Bumblebee Releases PPA and install Bumblebee using the proprietary NVIDIA driver:
  
sudo add-apt-repository ppa:bumblebee/stable sudo apt-get update sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic 
[/LIST]


No, the ubuntu-x-swat/x-ubdates is for older versions of Ubuntu.  This is likely what broke your system.

So now you have to purge that ppa.  So go to the terminal and type:
```
sudo apt-get install ppa-purge
```
then run
```
sudo ppa-purge ppa:bumblebee/stable
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```
that should return your system to the state it was in before installing either repository.  Be sure to note any errors.  If the remove of the bumblebee repository fails then run:
```
cat /etc/apt/sources.list.d/bumblebee-stable-precise.list
```
and post the result back here.  It should be:
```
deb http://ppa.launchpad.net/bumblebee/stable/ubuntu precise main
deb-src http://ppa.launchpad.net/bumblebee/stable/ubuntu precise main

```
next run:
```
dpkg -l | grep nvidia
```
if it lists any packeges then they should probably be removed but post these first so someone on the forum can confirm.

If all the above commands were successful and there were no nvidia packages installed then you can run the commands below to install bumblebee properly (I would try to boot back into the graphical environment first just to make sure it is working now):
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install linux-headers-generic bumblebee bumblebee-nvidia
```

---

### Post by WesternRyno on 2013-03-02
First of all, thanks so much for taking the time to help me out...I'm going a bit batty here. 

I receive errors after this code:

sudo ppa-purge ppa:bumblebee/stable

They are as follows:
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/bumblebee-stable-precise.list'
E: The list of sources could not be read
Warning:  apt-get update failed for some reason

So I run the cat code and it does look like:

deb [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) precise main deb-src [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) precise main

Then I run: 
dpkg -l | grep nvidia

and get this:

ii  nvidia-common                                1:0.2.44.2                                       Find obsolete NVIDIA drivers
ii  nvidia-current-updates                       304.64-0ubuntu0.2                                NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings-updates                      304.43-0ubuntu0.2                                Tool of configuring the NVIDIA graphics driver

PS update manager now won't work and I get this error:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/bumblebee-stable-precise.list'

---

### Post by Mr. Shannon on 2013-03-02
Don't worry about the "Please report this bug" message, that is being caused by the other errors.  I can't tell for sure since you did not put the result of cat in CODE tags, but it looks from the error that the last three characters of main "ain" have somehow ended up on the third line.  You will need to fix this and then continue with the instructions in my previous post.  To do this, first make a backup:
```
sudo cp /etc/apt/sources.list.d/bumblebee-stable-precise.list ~/
```
this will store a copy in your home directory.  Now edit the file and move "ain" from the 3rd line back up to the second so that it spells "main".  You can edit the file with:
```
sudo nano /etc/apt/sources.list.d/bumblebee-stable-precise.list
```
Remember to save the file with ctrl-o and then the Enter key before exiting with ctrl-x.
NOTE: you should probably do:
```
sudo apt-get update
```
after fixing this file before continuing with the instructions in my previous post.

I am realy sorry this is so complicated.
[B]
EDIT: [/B]
> **WesternRyno said:**
> 
ii  nvidia-common                                1:0.2.44.2                                       Find obsolete NVIDIA drivers
ii  nvidia-current-updates                       304.64-0ubuntu0.2                                 NVIDIA binary Xorg driver, kernel module and  VDPAU library
ii  nvidia-settings-updates                      304.43-0ubuntu0.2                                 Tool of configuring the NVIDIA graphics driver

It is safe to remove those packages and since everything is currently messed up I would go ahead and remove those for now.

---

### Post by WesternRyno on 2013-03-02
Mr Shannon, thanks again so much for sticking around and helping me out.  It kinda blows me away that you would do so.  Here is the CODE from the cat:

deb [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) precise main
deb-src [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) precise main
ain

Should I just delete the ain?

I figured how to do so in the edit code you gave me, but I can't figure how to exit?  Shift + 6 to get the symbol?  

I'm sorry I don't get all this as fast as I'd like, I wasn't expecting any of it......frustrating yes, but I am learning an absolute load here...anyways, back to the task at hand.  Will update asap

ahh, it means cntrl ok.

---

### Post by Mr. Shannon on 2013-03-02
> **WesternRyno said:**
> 
deb [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) precise main
deb-src [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) precise main
ain

Should I just delete the ain?


Yes delete the trailing ain, that should allow apt to read from the repository and thus for the ppa-purge to work.

---

### Post by WesternRyno on 2013-03-02
Ok, edited the file....

Ran 

sudo apt-get update

seemed to go well, but at the end got this line:

N: Ignoring file 'bumblebee-stable-precise.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

---

### Post by WesternRyno on 2013-03-02
Dude, if you need/want to bail, I understand....I will just re-install Ubuntu tomorrow and go from there....if you are able and willing, here is where I'm at after running this code from you:

sudo apt-get autoremove --purge bumblebee bumblebee-nvidia nvidia-common nvidia-current nvidia-settings

I get:
The following packages will be REMOVED:
  nvidia-common* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 49 not upgraded.
After this operation, 213 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 167976 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing nvidia-common ...
Purging configuration files for nvidia-common ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
N: Ignoring file 'bumblebee-stable-precise.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'bumblebee-stable-precise.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'bumblebee-stable-precise.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

---

### Post by WesternRyno on 2013-03-02
OH hey!  The Red error sign has disappeared from my top menu bar, that's a good sign!  Crowd cheers!

Update manager works now too!

Thanks man, I'm gonna be re-reading all this to see how you've done this.  But am I purged and ready now for your other instructions?

---

### Post by WesternRyno on 2013-03-02
Ok, I ran your purging instructions and got good and favourable results aside from the N:  ignoring .....

You say now to reboot back into the graphical environment...does that mean go into BIOS and put Optimus back on?

---

### Post by Mr. Shannon on 2013-03-02
Do:
```
sudo mv bumblebee-stable-precise.list.save.1 ~/
```
That file was probably accidentally created when editing the file.  This will move it into your home directory.  You can delete it from there after you are sure it is not necessary.

Next go ahead and remove those nvidia packages with:
```
sudo apt-get autoremove --purge nvidia-common nvidia-current-updates nvidia-settings-updates
```
your packages were a little different than the ones installed on my system so the command I gave you previously was incorrect.

Then do the ppa-purge as I described earlier for both ppa's.

Finally reboot.  You should now be back to a working system without bumblebee.

If you chose to try bumblebee again just remember not to use the ppa:ubuntu-x-swat/x-updates repository.

---

### Post by Mr. Shannon on 2013-03-02
> **WesternRyno said:**
> You say now to reboot back into the graphical environment...does that mean go into BIOS and put Optimus back on?

I would return the settings to the same as they where before.  If that works and you don't wan't to use bumblebee then you can try changing it to the integrated graphics and if that does not work then just change it back.

---

### Post by WesternRyno on 2013-03-02
Running code: sudo mv bumblebee-stable-precise.list.save.1 ~/

Leads to this:

mv: cannot stat `bumblebee-stable-precise.list.save.1': No such file or directory

---

### Post by Mr. Shannon on 2013-03-02
Sorry, in my haste I forgot to add the whole path.  Use:
```
sudo mv /etc/apt/sources.list.d/bumblebee-stable-precise.list.save.1 ~/
```

Also, sory for the confusion, I seem to be giving you instructions just as you already do them.

---

### Post by WesternRyno on 2013-03-02
First of all,
Mr Shannon achievement unlocked:  Legend Statu
Heheh, at least in my books!

I wish there were some way to show my appreciation beyond letting you know that your service has really helped someone out there (me) in digital land!  Unless you are on Vancouver Island and I can get ya a cup of coffee for your efforts!  Heheh

So you say bumblebee works for you?  I would be keen to try it again, but I feel I should read up on it some more first and go back to the forums and post some warnings on the code recommendations.

So yes, thanks again for all your effort offered to a complete stranger!  I will be passing it on, you can be assured of that.

---

### Post by WesternRyno on 2013-03-02
One last thing if you don't mind....

It would be your opinion and experience that these would be the codes to run if and when I go for Bumblebee again:


sudo add-apt-repository ppa:bumblebee/stable sudo apt-get update sudo apt-get install linux-headers-generic bumblebee bumblebee-nvidia

---

### Post by Mr. Shannon on 2013-03-02
So is your sytem working now?

**EDIT:**
> **WesternRyno said:**
> One last thing if you don't mind....

It would be your opinion and experience that these would be the codes to run if and when I go for Bumblebee again:


sudo add-apt-repository ppa:bumblebee/stable sudo apt-get update sudo  apt-get install linux-headers-generic bumblebee bumblebee-nvidia
Yes, that should work.  To be on the safe side I would install the linux-headers-generic first:
```
sudo  apt-get install linux-headers-generic
```
before installing bumblebee.

Glad to be of help.

---

### Post by WesternRyno on 2013-03-02
I have a stable desktop now, can restart and reboot with no problem, update manager loads however I haven't installed them yet and I am no longer receiving error messages.  So yes, for all intensive purposes, I believe my system is working now.  I still want to address the graphics card issue, but as mentioned, I need to read more first to avoid this fiasco or any others like it again.  Thanks again for coming to my rescue!

---

### Post by mörgæs on 2013-03-02
If you consider the problem solved, please mark the thread so.
A temporary solution is described [here]("http://ubuntuforums.org/showthread.php?t=2121377").

---

### Post by WesternRyno on 2013-03-02
I don't think I will consider this closed as I would like to first post here the proper code sequence for installing Bumblebee for a Nvidia GE 610M Optimus graphics card for Ubuntu 12.04.  Am waiting to hear from the Bumblebee team and will move forward from then.

---

### Post by Bashing-om on 2013-03-02
WesternRyno;
Well done ! Welcome to our world, where there is a will there is a way.

We stand-by awaiting a fruitionus outcome.[INDENT=2]

happu ubuntu'n

[/INDENT]

---

### Post by WesternRyno on 2013-03-02
Heheh, thanks for the welcome meng.  Forgive my post drama there, I had reached a point of exhaustion from all the walls I'd hit and was anxious to get on with work.

As for the issue of Nvidia Optimus cards, specifically for me the GE 610M I'm still unresolved as to the best solution and am currently reading and asking questions.  Here's where I'm at with troubleshooting possibilities:

**1**)  Download the Nvidia driver direct from their site.  I know the warnings for this but this link is at least making me consider it:

[http://askubuntu.com/questions/218126/how-to-i-install-my-video-driver-for-nvidia-geforce-610m-on-ubuntu-12-04](http://askubuntu.com/questions/218126/how-to-i-install-my-video-driver-for-nvidia-geforce-610m-on-ubuntu-12-04)
The fella doesn't say if he had luck adjusting his resolution after the fact, so I will have to dig some more.l

**2**)  Download and install Bumblebee.  This appeals to me, however, I have a few concerns based on the seemingly conflicting code suggestions and the long term support from these guys.  I have no reason to doubt the longterm support, but it is something to consider as they are only a few in number.  Anyways, this code sequence from Mr Shannon here will be the one I will likely try: 

i)     sudo  apt-get install linux-headers-generic
ii)   sudo add-apt-repository ppa:bumblebee/stable 
iii)  sudo apt-get update 
iv)  sudo apt-get install linux-headers-generic bumblebee bumblebee-nvidia

 I've also contacted the Bumblebee guys to see what their input is, and have seen this code sequence for this card as well:
i)    sudo apt-get install linux-source
ii)   sudo apt-get install linux
iii)  sudo apt-get autoremove nvidia-current
iv)  sudo apt-get install xserver-xorg xserver-xorg-video-all
v)   sudo apt-add-repository ppa:noobslab/nvidia-quantal
vi)  sudo apt-get update
vii)  sudo apt-get install nvidia-current
viii) sudo reboot

---

### Post by Mr. Shannon on 2013-03-02
As for number 1, that will probably only work if you set the BIOS to dedicated graphics mode.  And I would try letting Ubuntu install it's drivers (also from nvidia, just a little older) while running in dedicated graphics mode before using the drivers downloaded from NVIDIA.  It can be a mess and your system will likely break every time ubuntu installs a new kernel.

As for the second option, the first string of commands lists nothing about Bumblebee so I am unsure why you have that under the Bumblebee section.  Also, those commands are for ubuntu 12.10, not 12.04.

Long term support on a project is always up in the air for open source projects, they come and go (some stay forever).  However, you should remember that the linux kernel was started by one guy.  Also, you can always switch solutions down the road if one no longer works.

---

### Post by WesternRyno on 2013-03-02
Thanks for the input, I edited the post.  What you say about the long term support makes sense as well.

---

