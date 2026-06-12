---
title: "Tricky ownership"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by grtwhiterhyno on 2008-08-05
I am trying desperately to edit my home and usr folders, more correctly my Mozilla folder, which is buried in there.  :rolleyes:
I just want to drag and drop the flash installer file.  The trouble is that I keep getting an error indicating that I don't have the permission to do that because I'm not the owner. :mad:
I know this not good because I just installed this OS and set it up and I am the ONLY user and the admin.  What the heck is going on! ](*,)  :confused:

---

### Post by Rumel on 2008-08-05
I think you have to perform the actions as root.

---

### Post by grtwhiterhyno on 2008-08-05
<noob>  How do I do that my good Sir?

---

### Post by iaculallad on 2008-08-05
On your terminal, you could just do the command below to get administrative privilege w/c is needed to drag and drop your files to restricted folders.

```
gksudo nautilus
```

---

### Post by grtwhiterhyno on 2008-08-05
Initializing nautilus-share extension

** (nautilus:5929): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

I dont suppose this is right is it?  And this is where it sits. Has not returned to the prompt.

---

### Post by SunnyRabbiera on 2008-08-06
You really dont need to install flash by doing all that.
You can install flash via the repositories, you typically dont install things in ubuntu like you do in windows...
Here is a guide to get you started:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
After that I can teach you how to install flash the ubuntu way.

---

### Post by grtwhiterhyno on 2008-08-06
It appears to have worked. It returned to prompt, I could changs ownership and all, file has been dragged. Thanks

---

### Post by aimpau on 2008-08-06
Careful, .exe files don't work with Linux unless you have wine and Flash itself can be installed from the adobe.com website.

---

### Post by SunnyRabbiera on 2008-08-06
As for why your system is set up, thats how ubuntu is.
The core files are locked out if you dont acess them as sudo, its how the system works to protect itself.
Its not like windows where the first user is root all the time no matter what (this is why there are so many issues for windows)
In ubuntu the core files are locked for a reason.

---

### Post by grtwhiterhyno on 2008-08-06
Well I am definately going to bookmark that page, thank you.  Now, please do enlighten to hapless noob now before you.

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> Well I am definately going to bookmark that page, thank you.  Now, please do enlighten to hapless noob now before you.

Well what do you need to learn?
Where do you need help in?
Just ask and you shall learn.

---

### Post by grtwhiterhyno on 2008-08-06
Alrighty then, I know nothing about Linux and ofcourse ubuntu.  I can't, watch youtube, I can't play shrakrunners on Discovery.com <I think for the same reason>, and now I can't open the screen saver utility without an instantaneous crash <lovely>, my computer also will not recover if it goes into idle mode.  As you can see, I've been frustrated for some time as I have tried numerous fixes.

---

### Post by SunnyRabbiera on 2008-08-06
Hmm, well lets see.
For me it seems sharkrunners on discovery.com works but I think its because I have all my media repositories working and I installed flash the normal ubuntu way by using syanaptic.
If you need more multimedia though, look no farther then medibuntu.
Medibuntu is a third party repository to add on to the others you have already, it provides packages that cant be put out by default in ubuntu due to proprietary crap.
Go here to learn more:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

As for your other issues can you give us a list of your specs?
Processor info?
Video card?
Memory?
Stuff like that will help us help you.

---

### Post by grtwhiterhyno on 2008-08-06
Very old Emachine

Celeron <Copermine>
Cirrus Logic CS4281 Sound Card <onboard>
Video is onboar too: 82810 (CGC) Chipset Graphics Controller <dont know how to get more on it>
Is there a command for the terminal to get the specs on the ram?  I could get it on the reboot, but that will take a minute, this thing doesnt boot very fast now either.

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> Very old Emachine

Celeron <Copermine>
Cirrus Logic CS4281 Sound Card <onboard>
Video is onboar too: 82810 (CGC) Chipset Graphics Controller <dont know how to get more on it>
Is there a command for the terminal to get the specs on the ram?  I could get it on the reboot, but that will take a minute, this thing doesnt boot very fast now either.

For ram it should be listed in the system monitor app, located under system > administration > system monitor and check the "system tab" for ram info.

---

### Post by grtwhiterhyno on 2008-08-06
It says 248.7 MiB, kinda odd.  I forgot about the monitor tool.

---

### Post by fuzzyk.k on 2008-08-06
if you are still interested in changing permissions try 
reading the man pages of chmod and chown from terminal / console

e.g.
man chmod

careful they are powerful

---

### Post by Methuselah on 2008-08-06
I second the recommendation to follow the instructions at the medibuntu link to enable the software stored there.

Then search in applications->add/remove menu for flash then select the Macromedia plugin for installation.

---

### Post by grtwhiterhyno on 2008-08-06
Are you stumped Sunny?

---

### Post by grtwhiterhyno on 2008-08-06
Uh ohh. 
Failed to check for installed and available applications
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I am quite certain something is very wrong now. I followed the adding source list directions at the medi site for my version 8.04 Hardy and tried to open the Add/Remove utility and bam, trouble.

---

### Post by grtwhiterhyno on 2008-08-06
Adding the GPG thing failed.  I also cannot open the synaptic package manager

E: Type '--00:10:26--' is not known on line 1 in source list /etc/apt/sources.list.d/mdibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> Are you stumped Sunny?

Nono, i was just looking stuff over.
As for your issue, are you sure you followed the instructions on medibuntu and such?

---

### Post by grtwhiterhyno on 2008-08-06
Yes sir

Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution.

    * Ubuntu 8.04 "Hardy Heron":

      sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Is that a o as in open or 0 as in 007?

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> Yes sir

Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution.

    * Ubuntu 8.04 "Hardy Heron":

      sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Is that a o as in open or 0 as in 007?

O as in open.
Did you try a restart or something like that, sometimes the repositories hang and its best to restart things.

---

### Post by grtwhiterhyno on 2008-08-06
I will try that, I shall return, dear God I hope I do anyways.

---

### Post by SunnyRabbiera on 2008-08-06
Dont worry so much, sometimes errors come up but usually a reboot will help.
Also in a terminal try sudo apt-get update to see if anything pops up.
its possible you may have to manually edit a few things here and there, but dont worry it wont be too terrible.

---

### Post by grtwhiterhyno on 2008-08-06
Did the restart, in fact shut all the way down and rebooted, and still get error opening the Add/Remove utility.

---

### Post by grtwhiterhyno on 2008-08-06
tom@-****:~$ sudo apt-get update
[sudo] password for tom: 
E: Type '--00:10:26--' is not known on line 1 in source list /etc/apt/sources.list.d/mdibuntu.list
tom@****:~$ 

Life just keeps getting better lol

---

### Post by SunnyRabbiera on 2008-08-06
Hey you are just beginning so expect to make mistakes.
I suggest opening up a terminal and putting in this command:
sudo gedit /etc/apt/sources.list
and see if you have duplicated lines and such and give us a readout of it.
But that does look wrong by you having that extra sources list file, you may have to delete it.
But first things first and do what I suggested above so we can take a peek at your sources list.

---

### Post by grtwhiterhyno on 2008-08-06
Readout is huge, what is best way to get to you?  Just paste here?

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> Readout is huge, what is best way to get to you?  Just paste here?

yeh just copy the list and paste it, if you feel like it you can add a quote or a code tag to your post.

---

### Post by grtwhiterhyno on 2008-08-06
I don't know how to add the tag, sorry.


#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by SunnyRabbiera on 2008-08-06
Well it looks good to me, I feel your issue is generated by that medibuntu list... it looks misspelled so that alone might be alone, I suggest opening up nautilus in sudo mode (sudo nautilus)
make your way to the /etc/apt/sources.list.d and change the name of the mdibuntu.list to medibuntu.list.
remember you dont have to manually type out your commands, you can just copy and paste them from posts people make.
So say I tell you to put in sudo apt-get update you dont have to manually type it in, just copy the command from my post and paste it into the terminal.

---

### Post by grtwhiterhyno on 2008-08-06
2 files there, one by the name of mdibuntu.list the other medibuntu.list, so I cannot change the name of the first because a file already has that name. Now what?

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> 2 files there, one by the name of mdibuntu.list the other medibuntu.list, so I cannot change the name of the first because a file already has that name. Now what?

then just delete the misspelled one.
If its something that happened by mistake somewhere then just delete it and do a sudo apt-get update and see if new errors pop up.

---

### Post by grtwhiterhyno on 2008-08-06
tom@****:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
tom@****:~$ 

WOOHOO, Utilities back online.  Now that we fixed that, we can work on the original problems. Yay lol

---

### Post by SunnyRabbiera on 2008-08-06
Good, things worked out then on that end.
Now for your other issues, what one would you like to start off with?

---

### Post by grtwhiterhyno on 2008-08-06
I dont know really.  I suppose getting the flash thing going since I've been working on that for 2 days now.  If that goes quickly, I'm getting awfully tired of coming back to my computer and having to reboot the thing.

---

### Post by SunnyRabbiera on 2008-08-06
Alright lets go onto flash, now that medibuntu is working you can try to install the flashplayer-nonfree packages.
I dont know what else to sa concerning this, by installing flash the windows way you might not get the best of flash.

---

### Post by grtwhiterhyno on 2008-08-06
Lead the way Sunny.

---

### Post by SunnyRabbiera on 2008-08-06
Well as I said installing flash the ubuntu way is very easy.
Go into synaptic now you know where it is and how to use it thanks to the guide i gave you and search for flashplayer in it.
If you have gnash or anything I suggest you remove it.
Once you go through the guide I liked it will become clear, using synaptic is very easy.

---

### Post by grtwhiterhyno on 2008-08-06
Alright, gnash is gone.  When I search for flash it shows flash-plugin and flashplugin-nonfree installed. I probably did it wrong to begin with, so should I uninstall/reinstall?

---

### Post by SunnyRabbiera on 2008-08-06
Its worth a shot, but your biggest mistake was moving all those flash files you got from the adobe flash site.
If you remember where you put them, I suggest you get rid of those files you got from adobe to be on the safe side... then reinstall flashplayer-nonfree

---

### Post by grtwhiterhyno on 2008-08-06
Whats the difference in marking for removal and for complete removal?

---

### Post by abhilashkumar on 2008-08-06
A simple 'removal' doesn't remove the downloaded debs etc. A complete removal removes them and they will have to be downloaded again. If you are running short on disk space then you can do a complete removal.

---

### Post by SunnyRabbiera on 2008-08-06
Yes, either one will do to be honest.

---

### Post by grtwhiterhyno on 2008-08-06
You my long eared and fuzzy rabbity friend are the friggin BOMB!! Youtube works, goin to Discovery really quick.

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> You my long eared and fuzzy rabbity friend are the friggin BOMB!! Youtube works, goin to Discovery really quick.

Well glad it works, hey at one time I wasn't much different then you but by now this is second nature,
We are all beginners at some point.

---

### Post by grtwhiterhyno on 2008-08-06
Discovery works, a little slow though, never the less, you deserve a frosty beverage my friend.  Should I go ahead and try to open my screen saver utility?  If it crashes I will return.

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> Discovery works, a little slow though, never the less, you deserve a frosty beverage my friend.  Should I go ahead and try to open my screen saver utility?  If it crashes I will return.

Well that might be graphics related.
Actually we can check out any errors if you run gnome-screensaver-preferences in a terminal and see if it gives you errors.
There is a chance your issue may be related to your graphics card, but we will see.

---

### Post by grtwhiterhyno on 2008-08-06
Crash.  Screens worth of color bars and pixels before communication is stopped with monitor and then thats it.

---

### Post by SunnyRabbiera on 2008-08-06
alright, then do as I suggested and see what happens if you run it in a terminal, again the command is gnome-screensaver-preferences
and give us its readout.
Now are you using desktop effects?
If so try turning them off and try the application again, I wont be on much logner sorry to say as I got to get some sleep but hopefully someone can pick up where I left off.

---

### Post by grtwhiterhyno on 2008-08-06
Crashed trying to open it, crashed again with the terminal command. Effects have been turned off since installation because I was getting pixellaiton when moving my mouse around.  Is there a way to add you as a friend or something, because I too need rest and even if I get this fixed, I, ofcourse, have other questions.

---

### Post by SunnyRabbiera on 2008-08-06
> **grtwhiterhyno said:**
> Crashed trying to open it, crashed again with the terminal command. Effects have been turned off since installation because I was getting pixellaiton when moving my mouse around.  Is there a way to add you as a friend or something, because I too need rest and even if I get this fixed, I, ofcourse, have other questions.

I will handle that part, I am back up now so I may just start you off with a few private messages.

---

### Post by grtwhiterhyno on 2008-08-06
Bump

---

### Post by grtwhiterhyno on 2008-08-06
and again

---

