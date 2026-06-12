---
title: "Confused as to what this means"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by rossjohn07 on 2013-05-19
I recently installed Ubuntu 12.04 as my new OS on my MacBook Pro. It's been a little rough getting used to the method of installing things in what not running commands. I'm not sure why it's so beneficial to frequently enter "sudo apt-get update" after I've tried to install something. I don't quite get the nature this. I'm still trying to understand why certain things must be done before installing something, and even after installing something it seems like something else has then been affected by this new installation. Still trying to learn, I suppose I will purchase a book on Unix to get a deeper understanding.

Aside I recently had a problem when using "sudo apt-get update" when it gave me these errors in the E. So looking at one forum it told me to change something within it adding something. After that I ran the command again. It works and I get a whole bunch of code until I get to the bottom of the sudo apt-get install code and it says:

```
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,214 kB in 52s (41.9 kB/s)                                            
W: Failed to fetch http://archive.canonical.com/dists/precise/Release  Unable to find expected entry 'precise/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead

```

Any suggestions/moral sympathy?

---

### Post by ibjsb4 on 2013-05-19
Looks like a malformed line in your sources list.  Please post the output of:

```
cat -n /etc/apt/sources.list
```

---

### Post by Albury_Boy on 2013-05-20
[FONT=courier new]sudo apt-get update[/FONT] - This command gets a new list of software packages from (in your specific case) Ubuntu's US mirror, as opposed to (in my case) Ubuntu's Australian mirror.

When you run [FONT=courier new]sudo apt-get install some_software_package[/FONT] Ubuntu looks at the list of packages supplied by your etc/apt/sources.list to find the package that you want to install. 

When you run [FONT=courier new]sudo apt-get upgrade[/FONT] Ubuntu will look for more recent versions of software packages that you have, and try to install the new versions of them.

So, to run updates on your system, you can combine both into ```
sudo apt-get update && sudo apt-get upgrade
```

Sometimes, the sources.list can get broken and you may need to edit the list to correct it. As [SIZE=2][FONT=arial]**[COLOR=#000000][ibjsb4]("http://ubuntuforums.org/member.php?u=1729120") [/COLOR]**[/FONT][/SIZE]said, in your case you have a bad line in your sources.list. The command he mentioned shows the output of the list. You can (very carefully) edit the sources.list to remove the offending line by typing ```
sudo gedit /etc/apt/sources.list
``` Put a ## in front of the bad line to 'comment' it out. This a temporary fix, and you should try to find out what is wrong with the source. 

Hope this helps you understand apt-get a bit better. I think it's the best way to manage packages in the Linux world.

---

### Post by MoebusNet on 2013-05-20
I hope I'm not being too basic, but many times new users are unaware of the documentation available for Ubuntu. For example, are you aware that you don't always need to use the command-line to install software?

[https://help.ubuntu.com/12.04/ubuntu-help/addremove-install.html](https://help.ubuntu.com/12.04/ubuntu-help/addremove-install.html)

Ifyou haven't looked at it yet, the official documentation is a good foundation for Ubuntu knowledge:

[https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html)

---

### Post by grahammechanical on 2013-05-20
Ubuntu has Graphical User Interface Utilities that can do all these things. Software updater/Update Manager; Software Centre. It is often better to use these utilities. Software Centre will install applications with just one click and then give you an option to remove that application.

These utilities run the commands to update the system and install software. We can set Update Manager to automatically check for updates Daily, Every Two Days, Weekly, Every Fortnight or Never. There is no need to run the command to update so frequently unless we are using commands to modify the system.

Regards.

---

### Post by richierich1986 on 2013-05-20
As a sidenote: 

A book on UNIX isn't gonna help as much as you might think. If you'd rather read a book than the free documentation available online,
there are loads of books on Linux in general, or on Ubuntu specific. That'll get you further than a UNIX book. Those can be awesome
reading material, but probably later on, after you've been using Linux for a while and got used to some basic knowledge.

---

### Post by houseworkshy on 2013-05-20
The built in documentation is very useful.  Just typing "man" in front of any command will give you a lot of info so "man apt-get" is worth a look.  
If you like a more detailed view of what is going on but want it graphically "synaptic-package-manager" is really nice.  It used to be part of a default Ubuntu install, though it isn't anymore it is still available and I recomend it highly.  Here's some info on it [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
It shows you what is going on with apt-get better than any amount of text.  Also, in the begining, it may be easier to see it all rather than remember a lot of switches.

---

### Post by rossjohn07 on 2013-05-21
I came into Ubuntu thinking that it wouldn't be so difficult since I know quite a few programming languages and all. I thought migrating from Mac would be an easy transition and there would be much difference/difficulty. It's definitely much different than I expected, hopefully as the months pass I will become more comfortable with it.

When I enter the command:
```
cat -n /etc/apt/sources.list
```

It then returns the following:

```
1    # deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     9    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    14    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    20    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    21    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    22    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    30    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    31    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    32    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    40    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41    
    42    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    43    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    44    deb http://security.ubuntu.com/ubuntu precise-security universe
    45    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    46    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    47    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb http://archive.canonical.com/ubuntu precise partner
    54    # deb-src http://archive.canonical.com/ubuntu precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb http://extras.ubuntu.com/ubuntu precise main
    59    deb-src http://extras.ubuntu.com/ubuntu precise main
    60    deb http://archive.canonical.com/ precise precise partner
    61    deb-src http://archive.canonical.com/ precise partner
    62    deb http://archive.canonical.com/ precise partner
    63    deb-src http://archive.canonical.com/ precise partner
```

I'm still used to installing things the Mac way where I just easily download a dmg file for any program and it adds it to my application page easily. I think I need to do some more browsing on the internet to really understand the nature of this. I'm sure it's not too difficult. 

But ever since I tried adding Google Chrome (successfully), Adobe Reader (unsuccessfully) - my laptop has been functioning much differently. Now my screen won't even dim and when I close my laptop down, the laptop won't even sleep. The brightness keys seem to not even dim my laptop anymore. And when I start my laptop up it's not as fast as when I had Mac OSX [I guess since it's making the transition to Linux].

It also seems like Software Center is hit or miss; if there's an unknown app on there this is foreign, or that is not listed like Adobe Reader, I usually have to use Terminal. Also when I try to install anything foreign via the Software Center I tend to get errors. It seems like I always migrate back to Terminal even though I should be going through other areas.

I will keep doing research on the forums/internet, when I finally get time. Thank you.

---

### Post by sandyd on 2013-05-21
Your missing the /ubuntu at the end of archive.canonical.com.
Should look like
```

deb http://archive.canonical.com/ubuntu/ precise partner
deb-src http://archive.canonical.com/ubuntu/ precise partner

```

You can just run
```

sudo sed -i 's@archive.canonical.com/ @archive.canonical.com/ubuntu/ @' /etc/apt/sources.list
```
or
```

sudo nano /etc/apt/sources.list
```
and manually adding the /ubuntu to fix it

---

### Post by mastablasta on 2013-05-21
> **Albury_Boy said:**
> .... to remove the offending line by typing ```
sudo gedit /etc/apt/sources.list
``` .

It should be

```
gksudo gedit /etc/apt/sources.list
``` 

as gedit is graphical application. read more on sudo for graphical applicaitons here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

sudo nano ...is ok though as nano is an applicaiton that runs in terminal.

---

### Post by Ratscallion on 2013-05-21
> **rossjohn07 said:**
> I'm still used to installing things the Mac way where I just easily download a dmg file for any program and it adds it to my application page easily. I think I need to do some more browsing on the internet to really understand the nature of this. I'm sure it's not too difficult.
There are three main ways of installing applications in Ubuntu.
1. Use the Ubuntu Software Centre
Consider the Mac App Store in this instance. Whereas with OS X, you will have most of the applications you require available here, and others are available online, the Ubuntu Software Centre (USC) can have its database of applications updated. To do so, the database - the sources.list file you've been editing - needs to be modified. The application called 'apt' sorts all the application installation (and removal) business. The USC is just a good looking (and uncomplicated) way of using it.
2. Use a .deb package file. 
These are much like the dmg files you'll find in OS X and work in much the same way. They open with USC but can also be installed with a Terminal ```
sudo dpkg -i [package].deb
```.
3. Use the Terminal. 
By adding the application to sources.list (as others have already alluded to), running the update and then running an install procedure. It's one of the more efficient, but if you don't know what you're doing, can lead to more problems.

> **rossjohn07 said:**
> But ever since I tried adding Google Chrome (successfully), Adobe Reader (unsuccessfully) - my laptop has been functioning much differently. Now my screen won't even dim and when I close my laptop down, the laptop won't even sleep. The brightness keys seem to not even dim my laptop anymore. And when I start my laptop up it's not as fast as when I had Mac OSX [I guess since it's making the transition to Linux].
I'm not sure if you knew, but Ubuntu comes with its own PDF reader. If you press the Command key (I think) or the big button at the top of the panel on the left and type 'Document Viewer', that brings it up. Or, launch it from a Terminal using 'evince' (without quotes). Often, the big-name applications such as Adobe Reader and Photoshop have counterparts for Ubuntu: evince and GIMP, respectively.
I'm unsure why your hardware would be acting strange, but there may be some updates available or additional drivers required. Try removing some other applications that may be the source (but make sure you know what you're removing before you remove it!)

> **rossjohn07 said:**
> It also seems like Software Center is hit or miss; if there's an unknown app on there this is foreign, or that is not listed like Adobe Reader, I usually have to use Terminal. Also when I try to install anything foreign via the Software Center I tend to get errors. It seems like I always migrate back to Terminal even though I should be going through other areas.
As I mentioned earlier, the database (sources.list) might need updating to make other applications show up. When you need to do this, run one of the commands others have mentioned to edit it, then run ```
sudo apt-get update
``` to let Ubuntu know the database has been updated.
Errors may be in the form of dependencies, in other words, some applications require other applications to be installed before they can be installed. Often, you'll be recommended to install all of them at once, which is a good idea.

---

### Post by rossjohn07 on 2013-05-21
After running
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo nano /etc/apt/sources.list[/FONT][/COLOR]
```

I found this in the code. So, I assume that I must uncomment it and leave it there in the code. Or must I put this with all the Canonical stuff?

```
## Uncomment the following two lines to add software from Canonical's## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb http://archive.canonical.com/ubuntu precise partner
 deb-src http://archive.canonical.com/ubuntu precise partner

```

After uncommenting the lines above and leaving them where they were originally in the code, then running ```
 sudo apt-get update
```
I receive this message at the end of the page stating:

```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release  Unable to find expected entry 'precise/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Why is it that after each deb-src../ubuntu I need a '/' does every deb need a '/' after ubuntu?

Thank you for the help. I'm a EE, I should know these kinds of things. Slowly but surely the light bulb will go off.

---

