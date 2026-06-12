---
title: "Lucid Lynx: Software Sources does not open."
date: 2013-03-29
forum: New to Ubuntu
---

### Post by Dragyn on 2013-03-29
So this is a multi-tiered problem.

I was trying to play a game via Wine. Series of errors. Okay. Working through them with my rudimentary understanding of script thanks to these forums. Trying to completely uninstall extant Wine in order to install current stable launch (1.4). This seemed to prescribe updating to a newer version of Ubuntu, currently using 10.04 Lucid Lynx. According to official Ubuntu site I need upgrade to 11.10 Oneiric Ocelot. Site indicates opening "Software Sources."

When I open Software Sources either via System> Administration... or via Ubuntu Software Center> Edit the pointer changes to "clock" and the task bar adds appropriate tab but after about 30 seconds both change back and nothing happens.

More forum questing. Similar problems found for Karmic Koala (the version I started with) but inspection of Ubuntu.info file did not seem to confirm bug. Which is just as well because I can't edit the file anyway.

Problems:
1. How do I fix Software Sources so as to upgrade to 12.04?
2. If I need to edit Ubuntu.info how do I edit the file?
3. Is it possible to fix questviewer.exe error in Wine?

Game still doesn't work but that is lesser problem.

---

### Post by ibjsb4 on 2013-03-29
Do you really want to upgrade to 11.10?  11.10 reaches end of life next month just like 10o4.

I would suggest 12.04

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=upgrade+10.04+to+12.04&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=upgrade+10.04+to+12.04&sa=Search&cof=FORID:9)

---

### Post by Dragyn on 2013-03-29
I was aware of that and your reasoning makes sense. The Ubuntu site seems to imply that I have to upgrade a step at a time. This didn't make sense but given my naivety I'm obliged to follow advice. If I can skip ahead to 12.04 then that will be my next step.

---

### Post by Dragyn on 2013-03-29
Ok. Followed your link. Thank you for the info. I'll try that next.

---

### Post by Dragyn on 2013-03-29
Ok, so now...

I open Update Manager and click "Settings" as per the instructions found in ibjsb4's link and the same nothing happens as with the other methods of accessing Software Sources.

I'm going to try just selecting the "Upgrade to 12.04" button on the Update Manager window...

---

### Post by Dragyn on 2013-03-29
Same problem.

The method described above (attempting to avoid manually opening Software Sources) still resulted in the system attempting to open Software Sources on it's own which still resulted in nothing. Thus the upgrade to 12.04 is a bust until I can fix the Software Sources error.

---

### Post by ibjsb4 on 2013-03-29
Lets have a look.

In terminal:

```
sudo apt-get update
```

And please post.

---

### Post by Dragyn on 2013-03-29
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [481kB]          
Hit [http://dl.google.com](http://dl.google.com) stable/main Packages                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [58.3kB]              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [669kB]      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,829B]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [135kB]           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [171kB]     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [44.5kB]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,381B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,351B]   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,624B] 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [234kB]         
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [321kB]    
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [108kB]     
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,819B]  
Fetched 2,315kB in 12s (180kB/s)                                               
Reading package lists... Done

---

### Post by ibjsb4 on 2013-03-29
That looks good.  Next do a dist-upgrade.

```
sudo apt-get dist-upgrade
```

Get any errors?

---

### Post by Dragyn on 2013-03-29
Don't see any obvious errors. I can post if that would help. It definitely downloaded a lot of info, so the dist-upgrade was necessary. Problem persists.

---

### Post by mörgæs on 2013-03-29
Go for a clean install of 12.04.2 or 12.10. Upgrades are a pain.

---

### Post by ibjsb4 on 2013-03-29
Yes, version upgrades can be a pain.  What happens if you try:

```
sudo do-release-upgrade -d
```

---

### Post by Dragyn on 2013-03-29
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Translation-en                 
                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Translation-en                 
Fetched 1970 kB in 6s (81.3 kB/s)                                              
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
WARNING: Failed to read mirror file

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

To continue please press [ENTER]
        
(I'm willing to do a clean install if that will work. I'm assuming that means I have to back up my info again...)

---

### Post by ibjsb4 on 2013-03-29
Check your sources list to see if been upgraded to precise.

```
cat /etc/apt/sources.list
```

---

### Post by Dragyn on 2013-03-29
It's upgrading now. Might take a couple hours. Will report back then. Thank you for your help thus far.

---

### Post by Dragyn on 2013-03-30
12.04 installed successfully. I am now able to access Software Sources which was the primary concern. Guess we can call this one solved. 
Unity was a bit of a shocker but found the gnome desktop and added that so all is well.
Thanks for your help.


...Now onto the questviewer.exe issue...

---

### Post by ibjsb4 on 2013-03-30
Congratulations :)

Some tweaks for the classic desktop

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

