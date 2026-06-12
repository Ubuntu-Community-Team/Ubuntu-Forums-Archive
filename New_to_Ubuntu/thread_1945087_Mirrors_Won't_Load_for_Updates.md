---
title: "Mirrors Won't Load for Updates"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-03-22
I've tried unsuccessfuly to run the update manager on my install of Ubuntu 10.10 in the last several days. It starts to download the packages, then says "failed to access mirrors at Ubuntu.com" (or something like that) and then says to check my internet connection which is working just fine. This problem is new as I have run the update manager successfuly many times in the past. I know we're getting close to the time for official support to stop on 10.10, but it hasn't happened yet - has it? Any other suggestions? Thanks.
 
Ubuntu 10.10 (Ppc) running on eMac G4.

---

### Post by 2F4U on 2012-03-22
Maybe it is just one repository. Can you run the following from a terminal and post the output here:

```
sudo apt-get update
```

This gives a chance to look at what particular repositories are not accessible.

---

### Post by Javelin Dan on 2012-03-22
2F4U- I'll have to wait till tonight after I get home, but will post output later. Thanks.

---

### Post by Javelin Dan on 2012-03-22
Sorry, but I don't exactly know how to post code - but here it is anyway...

Ign cdrom://Xubuntu 10.04 LTS _Lucid Lynx_ - Release powerpc (20100428) lucid Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]            
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick Release.gpg                         
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/main Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/main Translation-en_US
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]            
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                       
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/multiverse Translation-en   
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/multiverse Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/restricted Translation-en   
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/restricted Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/universe Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick/universe Translation-en_US
Get:3 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-updates Release.gpg [198B]    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/main Translation-en 
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/main Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/multiverse Translation-en
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [39.8kB]    
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/multiverse Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/restricted Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/restricted Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/universe Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-updates/universe Translation-en_US
Get:5 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-security Release.gpg [198B]           
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/main Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/main Translation-en_US
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/multiverse Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/multiverse Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                           
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/restricted Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/restricted Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main powerpc Packages                  
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/universe Translation-en
Ign [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) maverick-security/universe Translation-en_US
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick Release   
Get:6 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-updates Release [39.8kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources                    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources [178kB]
Get:8 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-security Release [39.8kB]             
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/main powerpc Packages                     
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/restricted powerpc Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/universe powerpc Packages                
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick/multiverse powerpc Packages
Get:9 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-updates/main powerpc Packages [449kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources [778B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources [65.2kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources [2,513B]  
Get:13 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-updates/restricted powerpc Packages [14B]
Get:14 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-updates/universe powerpc Packages [190kB]
Get:15 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-updates/multiverse powerpc Packages [4,367B]
Get:16 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-security/main Sources [105kB]          
Get:17 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-security/restricted Sources [14B]      
Get:18 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-security/universe Sources [34.1kB]     
Get:19 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-security/multiverse Sources [1,755B]   
Get:20 [http://ports.ubuntu.com](http://ports.ubuntu.com) maverick-security/main powerpc Packages [317kB] 
Media change: please insert the disc labeled                                   
 'Xubuntu 10.04 LTS _Lucid Lynx_ - Release powerpc (20100428)'
in the drive '/cdrom/' and press enter

---

### Post by jerrrys on 2012-03-22
[open a terminal and enter:]("https://help.ubuntu.com/community/UsingTheTerminal")

gksudo software-properties-gtk

And uncheck CDrom entries.

[ATTACH]214794[/ATTACH]

then do another update

---

### Post by Javelin Dan on 2012-03-23
Thanks jerrys - I'll try it tonight and let you know. For my continuing education, mind telling me what you think the problem is? Also, if anyone would be kind enough to fill me in on how to post code properly, I'd appreciate it. Thanks again.

---

### Post by jerrrys on 2012-03-23
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+post+code&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+post+code&sa=Search&cof=FORID:9)

..:D

---

### Post by Javelin Dan on 2012-03-25
-[IMG]http://ubuntuforums.org/images/attach/png.gif[/IMG]

Jerrys- Attached (hopefully) is a screenshot of the command you asked me to execute. As you can see, the CD ROM box is not checked. Please advise what to do next.

---

### Post by jerrrys on 2012-03-26
Hi Javelin Dan

Please post the output of this terminal command:

cat -n /etc/apt/sources.list

Thankyou

---

### Post by Javelin Dan on 2012-03-26
Will do after work this evening. Thanks for hanging in there with me...

---

### Post by Javelin Dan on 2012-03-26
Here ya' go...

[CODE 1    # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release powerpc (20101008)]/ maverick main
     2    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb cdrom:[Xubuntu 10.04 LTS _Lucid Lynx_ - Release powerpc (20100428)]/ lucid main universe
     6    deb http://ports.ubuntu.com/ubuntu-ports/ maverick main restricted
     7    deb-src http://archive.ubuntu.com/ubuntu maverick main restricted
     8    
     9    ## Major bug fix updates produced after the final release of the
    10    ## distribution.
    11    deb http://ports.ubuntu.com/ubuntu-ports/ maverick-updates main restricted
    12    deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted
    13    
    14    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15    ## team. Also, please note that software in universe WILL NOT receive any
    16    ## review or updates from the Ubuntu security team.
    17    deb-src http://archive.ubuntu.com/ubuntu maverick universe
    18    deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    21    ## team, and may not be under a free licence. Please satisfy yourself as to
    22    ## your rights to use the software. Also, please note that software in
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb http://ports.ubuntu.com/ubuntu-ports/ maverick multiverse
    26    deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
    27    deb http://ports.ubuntu.com/ubuntu-ports/ maverick-updates multiverse
    28    deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse
    29    
    30    ## Uncomment the following two lines to add software from the 'backports'
    31    ## repository.
    32    ## N.B. software from this repository may not have been tested as
    33    ## extensively as that contained in the main release, although it includes
    34    ## newer versions of some applications which may provide useful features.
    35    ## Also, please note that software in backports WILL NOT receive any review
    36    ## or updates from the Ubuntu security team.
    37    # deb http://ports.ubuntu.com/ubuntu-ports/ maverick-backports main restricted universe multiverse
    38    # deb-src http://archive.ubuntu.com/ubuntu maverick-backports main restricted universe multiverse
    39    
    40    ## Uncomment the following two lines to add software from Canonical's
    41    ## 'partner' repository.
    42    ## This software is not part of Ubuntu, but is offered by Canonical and the
    43    ## respective vendors as a service to Ubuntu users.
    44    # deb http://archive.canonical.com/ubuntu maverick partner
    45    # deb-src http://archive.canonical.com/ubuntu maverick partner
    46    
    47    ## This software is not part of Ubuntu, but is offered by third-party
    48    ## developers who want to ship their latest software.
    49    deb http://extras.ubuntu.com/ubuntu maverick main
    50    deb-src http://extras.ubuntu.com/ubuntu maverick main
    51    
    52    deb http://ports.ubuntu.com/ubuntu-ports/ maverick-security main restricted
    53    deb-src http://ports.ubuntu.com/ubuntu-ports/ maverick-security main restricted
    54    deb http://ports.ubuntu.com/ubuntu-ports/ maverick-security multiverse
    55    deb-src http://ports.ubuntu.com/ubuntu-ports/ maverick-security multiverse
    56    
]

---

### Post by jerrrys on 2012-03-26
BINGO

Line #5 needs to be commented out (#); make it read:
#    deb cdrom:[Xubuntu 10.04 LTS _Lucid Lynx_ - Release powerpc (2010042:cool:]/ lucid main universe

followed with a:

sudo apt-get update

and you should be good to go.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+sources+list&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+sources+list&sa=Search&cof=FORID:9)

---

### Post by Javelin Dan on 2012-03-27
I'll certainly try that. Please explain what happened and how as I have obviously never tweaked any of this. How did the updates manager go from working to not? Thanks again for all your help.

---

### Post by jerrrys on 2012-03-27
I can only guess at what happen.  With few exceptions your sources.list should only contain 10.10 sources.
Maybe you recently upgraded to 10.10 and it was carried over, really don't know for sure.

I myself do not use update-manager, but instead use synaptic-package-manager.  SPM will will do the job of both  update-manager
and the software-center plus much more.  You should check it out.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)

To install it:  sudo apt-get install synaptic
and it will appear in your main menu.

---

### Post by Javelin Dan on 2012-03-27
jerrys - 

I thought I understood what you meant by "comment out" but it turns out I didn't...I couldn't figure out how to amend line 5 in the code. I did however take your advice and am currently downloading the upgrade files through Synaptic (didn't need to download it though, it was already installed). So I guess I'll call this "solved". I would like to learn about the "comment out" thing. Thanks for all your help.

---

### Post by jerrrys on 2012-03-27
> **Javelin Dan said:**
> jerrys - 

I thought I understood what you meant by "comment out" but it turns out I didn't...I couldn't figure out how to amend line 5 in the code. I did however take your advice and am currently downloading the upgrade files through Synaptic (didn't need to download it though, it was already installed). So I guess I'll call this "solved". I would like to learn about the "comment out" thing. Thanks for all your help.

By commenting ([COLOR=Red]#[COLOR=Black]) that line out, it cannot be read by your system.  To do it, maybe a GUI would make more sense.  You would open a terminal and enter:

gksudo nautilus

then navigate to:

[/COLOR][/COLOR]/etc/apt/sources.list
[ATTACH]215036[/ATTACH]

double click on sources.list
then change line five from and to:

deb cdrom:[Xubuntu 10.04 LTS _Lucid Lynx_ - Release powerpc (2010042:cool:]/ lucid main universe

[COLOR=Red]#[/COLOR]deb cdrom:[Xubuntu 10.04 LTS _Lucid Lynx_ - Release powerpc (2010042:cool:]/ lucid main universe
[COLOR=Red][COLOR=Black]
those faces are just an posting error.

[/COLOR][/COLOR]

---

### Post by Javelin Dan on 2012-03-28
OK jerrys, thanks again. The Synaptic trick worked fine. In fact, while I was watching the installation of the files I noticed something about "update manager". So when it was done I clicked on "update manager" and it told me I was up to date and there was nothing to download, so I guess it repaired that problem as well. I remember when I first attempted to learn something about computers, a wise man once told me that there are always at least three different ways to accomplish the same thing on a computer. So far, it seems to be true. I have absolutely no pride about taking the easy way out, but I will admit that if it wasn't for people like you, I'd still be running away from the command line screaming like a girl. Thanks one more time for your time and effort.

---

