---
title: "How do I get everything working?"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bikewrecker on 2011-09-21
Hi everybody. I'm new to Ubuntu and have been frustrated with trying to install basically anything. I grew up using windows all my life so I never really had to "learn" how to use windows. I just kind of absorbed it and could usually figure out whatever problems windows gave me. Now I'm using ubuntu for my programming related things and windows for... well everything else. I used to run ubuntu 10.10 and really liked it once I figured everything out. 11.10 however is quite a different story. I understand it's the beta version, and as I'm a ubuntu noob I probably should have just gone with 11.04; however, I have a plethora of questions I need answered and I'm going to ask them here. I eventually want to replace windows completely, but I'm not comfortable enough with ubuntu to make the change. 

Here we go:

**1. Where's the restart button?** 
I've never seen an OS without a restart button and was wondering if there was some way I could get one. I'm entirely too lazy to type "$sudo reboot" and my password in the terminal every time I want to switch partitions. 

**2. How do I get the GUI to show 'hidden' folders?**
I noticed that you're supposed to save a lot of stuff under the ~/ directory. (ie. ~/.mozilla/plugins) but if you look at your home directory, there is no such folder. Is there a way to show these folders or do i just need to learn the terminal better? 

**3. Can I change the sidebar?**
I don't like the look of the sidebar in 11.10. it's like they're trying to copy the mac OS which I don't like at all. I can use a mac if I have to but I'd rather customize my ubuntu how I want it. 

[B]4. alias'
[/B]For some reason every time I make an alias, it will work fine until I reboot. Then my alias is gone :'(

[B]5. How do I get games working?
[/B]So I did some research and found out about wine and playonlinux, which i guess are the same thing? So I went to the playonlinux site and tried to download it and it asked me if i wanted to download the Natty, Maverick, lucid, karmic, or hardy version.... huh? I have no idea and the site didn't explain further. Know which one I should grab?

[B]6. How do I get my mic working?
[/B]For some reason when I go to the "sound recorder" or any other program I can't change which I/O devices I would like to use. The only option is 'Master.' 

[B]7. How do I make a terminal shortcut on my desktop?
[/B]I tried typing in terminal in 'dash home' thingy that I don't particularly like, and dragging the icon onto the desktop. It used to give me an error but now it just doesn't say anything... or make the shortcut. Guess Ill have to stick to ctrl-alt-t?

[B]8. Skype?
[/B]Does skype work for ubutnu? I tried typing in sudo apt-get install skype and it printed out some crap and asked me if i would allow the allocation of some memory for the program and I said yes. Then it told me to insert my ubuntu 11.10 OO CD and press enter when i did... I thought that was weird but I did it anyways and then it just kept re printing the insert cd and press enter txt forever so i hit ctrl-z and stopped it. then one of the cores on my CPU started working at %100 non stop so i had to reboot... 

[B]9. Itunes?
[/B]Now I'm not a big fan of mac software, but the ubuntu built in media player freaks out everytime I try to play one of my itunes songs the .m4h or whatever the crap stupid itunes selfishly converts all your songs to... anyways sudo apt-get install itunes didnt work but that might have been because my CPU was freaking out about trying to install skype sill. That command just seems to easy to work. I do like my ipod touch a lot and would like to get it working with my ubuntu; however, that means I have to buy into the stupid mac corporation and get itunes :( 

[B]10. CPU monitor
[/B]I've been using the system monitor tool to monitor how hard my cpu's are working, but the damn thing uses like 4-15% of my cpu power. Now i have a 3.16 GHz intel Dual core processor so it's not a weeny, but either the system monitor isn't coded very well or something because my cpu monitor on my windows partition doesn't use nearly that much processor power. Anyways it doesn't tell me the temperature of my CPU's anyways so I would like to get a program that does, and that runs of waaay less cpu power. Any suggestions?

[B]11. Error at startup
[/B]I get this error with something having to do with my nvidia settings for my monitors. Idk what is going on but it pops up every time I turn on in ubuntu. I must have messed up the settings when I was trying for the 5 hours to get my second monitor to work. Thank you again to whoever helped me with that one. I can't read the title of the error because the error box is too high on the screen, but it says
 'none of the selected modes were compatible with the possible modes:
Trying modes for CRT 345
CRT345 trying mode 3840x1080@50 Hz with output at 1920x1080@50Hz(pass 0)
CRT345 trying mode 3840x1080@50 Hz with output at 1920x1080@50Hz(pass 1)'
My screens seem to work just fine so it hasn't bothered me too much, but I would like it to go away. I'm afraid to mess with my nvidia settings anymore lest i screw up my monitor setup again. 

Thank y'all so much for all the help! If you can't answer ALL my questions that's toootaly fine. I understand I'd just like to get on the ubuntu train sooner rather than later.
peace.

---

### Post by cariboo on 2011-09-22
> **bikewrecker said:**
> Hi everybody. I'm new to Ubuntu and have been frustrated with trying to install basically anything. I grew up using windows all my life so I never really had to "learn" how to use windows. I just kind of absorbed it and could usually figure out whatever problems windows gave me. Now I'm using ubuntu for my programming related things and windows for... well everything else. I used to run ubuntu 10.10 and really liked it once I figured everything out. 11.10 however is quite a different story. I understand it's the beta version, and as I'm a ubuntu noob I probably should have just gone with 11.04; however, I have a plethora of questions I need answered and I'm going to ask them here. I eventually want to replace windows completely, but I'm not comfortable enough with ubuntu to make the change. 

Here we go:

**1. Where's the restart button?** 
I've never seen an OS without a restart button and was wondering if there was some way I could get one. I'm entirely too lazy to type "$sudo reboot" and my password in the terminal every time I want to switch partitions.

If you are using Unity click the power button in the upper left corner, and select shutdown, a window will pop up with restart, shutdown and cancel. 

> 2. How do I get the GUI to show 'hidden' folders?[/B]
I noticed that you're supposed to save a lot of stuff under the ~/ directory. (ie. ~/.mozilla/plugins) but if you look at your home directory, there is no such folder. Is there a way to show these folders or do i just need to learn the terminal better? 

Open nautilus, the file manager and press Ctrl-h, in a terminal use:

```
ls -la
```


> 3. Can I change the sidebar?[/B]
I don't like the look of the sidebar in 11.10. it's like they're trying to copy the mac OS which I don't like at all. I can use a mac if I have to but I'd rather customize my ubuntu how I want it.

Install compizconfig-settings-manager to change icon size, and other parameters, to change icons install gnome-tweak-tool, both are in the repositories. 

> 4. alias'
For some reason every time I make an alias, it will work fine until I reboot. Then my alias is gone :'(


> 5. How do I get games working?
[/B]So I did some research and found out about wine and playonlinux, which i guess are the same thing? So I went to the playonlinux site and tried to download it and it asked me if i wanted to download the Natty, Maverick, lucid, karmic, or hardy version.... huh? I have no idea and the site didn't explain further. Know which one I should grab?

> 6. How do I get my mic working?
]For some reason when I go to the "sound recorder" or any other program I can't change which I/O devices I would like to use. The only option is 'Master.'

Go to sound preferences, and check the input.  

> 7. How do I make a terminal shortcut on my desktop?
[/B]I tried typing in terminal in 'dash home' thingy that I don't particularly like, and dragging the icon onto the desktop. It used to give me an error but now it just doesn't say anything... or make the shortcut. Guess Ill have to stick to ctrl-alt-t?

Put a terminal icon in the Launcher

> 8. Skype?
Does skype work for ubutnu? I tried typing in sudo apt-get install skype and it printed out some crap and asked me if i would allow the allocation of some memory for the program and I said yes. Then it told me to insert my ubuntu 11.10 OO CD and press enter when i did... I thought that was weird but I did it anyways and then it just kept re printing the insert cd and press enter txt forever so i hit ctrl-z and stopped it. then one of the cores on my CPU started working at %100 non stop so i had to reboot... 

Make sure you have the partner repositories enabled and the distribution set for Natty, and use your favourite method of installing it. To enable the partner repository, clcik the power button and select System Settings->Software Sources

> 9. Itunes?
Now I'm not a big fan of mac software, but the ubuntu built in media player freaks out everytime I try to play one of my itunes songs the .m4h or whatever the crap stupid itunes selfishly converts all your songs to... anyways sudo apt-get install itunes didnt work but that might have been because my CPU was freaking out about trying to install skype sill. That command just seems to easy to work. I do like my ipod touch a lot and would like to get it working with my ubuntu; however, that means I have to buy into the stupid mac corporation and get itunes :( 

Can't be done, Mac or Windows only

> 10. CPU monitor
[/B]I've been using the system monitor tool to monitor how hard my cpu's are working, but the damn thing uses like 4-15% of my cpu power. Now i have a 3.16 GHz intel Dual core processor so it's not a weeny, but either the system monitor isn't coded very well or something because my cpu monitor on my windows partition doesn't use nearly that much processor power. Anyways it doesn't tell me the temperature of my CPU's anyways so I would like to get a program that does, and that runs of waaay less cpu power. Any suggestions?

Check vindsl's posts in almost any thread in this sub-forum, he uses [conky]("http://conky.sourceforge.net/")

> 11. Error at startup
[/B]I get this error with something having to do with my nvidia settings for my monitors. Idk what is going on but it pops up every time I turn on in ubuntu. I must have messed up the settings when I was trying for the 5 hours to get my second monitor to work. Thank you again to whoever helped me with that one. I can't read the title of the error because the error box is too high on the screen, but it says
 'none of the selected modes were compatible with the possible modes:
Trying modes for CRT 345
CRT345 trying mode 3840x1080@50 Hz with output at 1920x1080@50Hz(pass 0)
CRT345 trying mode 3840x1080@50 Hz with output at 1920x1080@50Hz(pass 1)'
My screens seem to work just fine so it hasn't bothered me too much, but I would like it to go away. I'm afraid to mess with my nvidia settings anymore lest i screw up my monitor setup again. 

> Thank y'all so much for all the help! If you can't answer ALL my questions that's toootaly fine. I understand I'd just like to get on the ubuntu train sooner rather than later.
peace.

---

### Post by jocko on 2011-09-22
> **bikewrecker said:**
> [B]4. alias'
[/B]For some reason every time I make an alias, it will work fine until I reboot. Then my alias is gone :'(
To make an alias permanent you'll have to add it to your ~/.bashrc (hidden in your home directory, so press Ctrl+h to see it....).
You can probably add your aliases anywhere in the file, but there are already some aliases  close to the end of the file, so it may be a good idea to add yours there too. You'll figure out the correct syntax once you see the aliases that are already there...

---

### Post by bikewrecker on 2011-09-22
@cariboo907

1. ... Oh jeeze duh. I sure feel like a *******. Thank you.

2. Ok ctrl-h worked just peachy thanks a ton!

3. Allright I tried to install gnome-tweak-tool but this happened:


daniel@daniel-EP45-UD3L:~$ sudo apt-get install gnome-tweak-tool
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
daniel@daniel-EP45-UD3L:~$ 


"you have held broken packages"... that can't be good. Did I already destroy my ubuntu partion?

6. I tried that before but under the input tab the only device is my webcam. Does this mean I'll have to find a driver for my specific mic? 

7. Lol, ok good plan.

8. Ok I went into software sources and clicked em all. Then I typed my favorite method of installing and It did a bunch of stuff and now in the unity dash thingy there is a skype icon but when I click it nothing happens. :(

9. Pfft. Figures.. I can convert the .m4h (or whatever they're called) files and play them with the ubuntu build in music player though right?

10. Ok I got that but it's freakin out my computer. I'll mess with it some more.

Thank you soo soo much for all your help! I really appreciate it! I'm gonna mess with this stuff some more and see if I can't get it working. 

@ jocko

Ok thanks I tired that, but I didn't get it working. It wanted me to save my aliases in a different file so I did that but they're not workin. I'll mess with it some more though. I'm confidant I'll be able to get it workin. Thank you for the help.

---

### Post by cariboo on 2011-09-22
To fix broken packages, the easiest way for a new users is to install synaptic, and use the broken package filter to remove what's broken.

---

### Post by bikewrecker on 2011-09-22
Ok, I went the the synaptic package manager edit> fix broken packages. then on the bottom it says "Successfully fixed dependency problems" so then I type "sudo apt-get install gnome-tweak-tool" and it gives me the same error. :(

---

### Post by paul_in_london on 2011-09-22
> **bikewrecker said:**
> @cariboo907

...

3. Allright I tried to install gnome-tweak-tool but this happened:


daniel@daniel-EP45-UD3L:~$ sudo apt-get install gnome-tweak-tool
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
daniel@daniel-EP45-UD3L:~$ 


"you have held broken packages"... that can't be good. Did I already destroy my ubuntu partion?

...



You haven't necessarily broken your install. The packages are in a greater state of flux at this stage of the release cycle and can be out of synch. (this might be clearer if you have a look at the sticky about partial upgrades).

Try running these commands and paste the output so we can see what's held back:

```
apt-get update
```

and then:

```
apt-get upgrade
```

---

### Post by bikewrecker on 2011-09-22
> **paul_in_london said:**
> You haven't necessarily broken your install. The packages are in a greater state of flux at this stage of the release cycle and can be out of synch. (this might be clearer if you have a look at the sticky about partial upgrades).

Try running these commands and paste the output so we can see what's held back:

```
apt-get update
```and then:

```
apt-get upgrade
```

```

daniel@daniel-EP45-UD3L:~$ sudo apt-get update
[sudo] password for daniel: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Translation-en
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://archive.canonical.com natty InRelease                               
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:1 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg         
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://archive.canonical.com oneiric Release                               
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://archive.canonical.com natty Release                       
Get:3 http://us.archive.ubuntu.com oneiric Release [39.8 kB]                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Get:4 http://us.archive.ubuntu.com oneiric/main Sources [874 kB]               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Ign http://archive.canonical.com oneiric/partner Translation-en_US          
Ign http://archive.canonical.com oneiric/partner Translation-en              
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                  
Ign http://archive.canonical.com natty/partner Translation-en_US             
Ign http://archive.canonical.com natty/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en                     
Hit http://security.ubuntu.com oneiric-security/restricted Sources           
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex
Ign http://security.ubuntu.com oneiric-security/main Translation-en_US         
Ign http://security.ubuntu.com oneiric-security/main Translation-en            
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_US   
Get:5 http://us.archive.ubuntu.com oneiric/restricted Sources [5,326 B]        
Get:6 http://us.archive.ubuntu.com oneiric/universe Sources [4,683 kB]         
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_US   
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_US     
Ign http://security.ubuntu.com oneiric-security/universe Translation-en        
Get:7 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]         
Get:8 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,225 kB]      
Get:9 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [7,963 B] 
Get:10 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [4,453 kB] 
Get:11 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB] 
Get:12 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,225 kB]      
Get:13 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,009 B] 
Get:14 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,460 kB]  
Get:15 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Ign http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Ign http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Ign http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Ign http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Get:16 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,920 kB] 
Ign http://us.archive.ubuntu.com oneiric/main Translation-en_US                
Ign http://us.archive.ubuntu.com oneiric/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com oneiric/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com oneiric/universe Translation-en_US            
Ign http://us.archive.ubuntu.com oneiric-updates/main Translation-en_US        
Ign http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Ign http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Ign http://us.archive.ubuntu.com oneiric-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US  
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Fetched 21.3 MB in 2min 2s (174 kB/s)                                          
Reading package lists... Done


``````
[U]
daniel@daniel-EP45-UD3L:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The follow[/U]ing packages have been kept back:
  gnome-control-center-data
The following packages will be upgraded:
  apt apt-transport-https apt-utils bamfdaemon banshee
  banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore binutils
  brasero brasero-cdrkit brasero-common compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default compiz-plugins-main
  compiz-plugins-main-default deja-dup eog gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-indicate-0.6 gir1.2-pango-1.0 gir1.2-peas-1.0 gnome-bluetooth
  gnome-desktop3-data gnome-games-common gnome-mahjongg gnome-session
  gnome-session-bin gnome-session-common gnome-settings-daemon gnome-sudoku
  gnomine hpijs hplip-cups language-selector-common language-selector-gnome
  libapt-inst1.3 libapt-pkg4.11 libbamf0 libbamf3-0 libbrasero-media3-1
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdecoration0
  libgail-3-0 libgail-3-common libgnome-bluetooth8 libgnome-desktop-3-2
  libgnomekbd-common libgnomekbd7 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libhpmud0 libindicate-gtk3 libindicate5 libnm-glib-vpn1 libnm-glib4
  libnm-util2 libpango1.0-0 libpango1.0-0:i386 libpeas-1.0-0 libpeas-common
  libsane libsane-hpaio libunity-2d-private0 libyelp0 network-manager oneconf
  python-gobject python-gobject-cairo python-indicate sane-utils shotwell
  ubuntu-desktop ubuntu-minimal ubuntu-standard unity-2d unity-2d-launcher
  unity-2d-panel unity-2d-places unity-2d-spread unity-lens-files
  update-manager update-manager-core yelp zeitgeist-datahub
93 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 29.7 MB of archives.
After this operation, 438 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libbamf3-0 amd64 0.2.100-0ubuntu1 [24.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgail-3-common amd64 3.1.92-0ubuntu1 [131 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libpango1.0-0 i386 1.29.3+git20110916-0ubuntu1 [367 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libpango1.0-0 amd64 1.29.3+git20110916-0ubuntu1 [365 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgail-3-0 amd64 3.1.92-0ubuntu1 [24.2 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgtk-3-common all 3.1.92-0ubuntu1 [134 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgtk-3-0 amd64 3.1.92-0ubuntu1 [2,459 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libbamf0 amd64 0.2.100-0ubuntu1 [24.8 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ oneiric/main bamfdaemon amd64 0.2.100-0ubuntu1 [49.6 kB]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libapt-pkg4.11 amd64 0.8.16~exp5ubuntu11
  404  Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main apt amd64 0.8.16~exp5ubuntu11
  404  Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libapt-inst1.3 amd64 0.8.16~exp5ubuntu11
  404  Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main apt-utils amd64 0.8.16~exp5ubuntu11
  404  Not Found [IP: 91.189.92.171 80]
Get:10 http://us.archive.ubuntu.com/ubuntu/ oneiric/main ubuntu-minimal amd64 1.243 [2,744 B]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main apt-transport-https amd64 0.8.16~exp5ubuntu11
  404  Not Found [IP: 91.189.92.171 80]
Get:11 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-gobject amd64 3.0.0-0svn1 [352 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-pango-1.0 amd64 1.29.3+git20110916-0ubuntu1 [22.8 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-gtk-3.0 amd64 3.1.92-0ubuntu1 [231 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ oneiric/main language-selector-gnome all 0.52 [20.8 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ oneiric/main language-selector-common all 0.52 [253 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-gobject-cairo amd64 3.0.0-0svn1 [8,116 B]
Get:17 http://us.archive.ubuntu.com/ubuntu/ oneiric/main ubuntu-standard amd64 1.243 [2,798 B]
Get:18 http://us.archive.ubuntu.com/ubuntu/ oneiric/main update-manager-core amd64 1:0.152.19 [173 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ oneiric/main update-manager all 1:0.152.19 [609 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgnome-desktop-3-2 amd64 3.1.92-0ubuntu2 [96.1 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-desktop3-data all 3.1.92-0ubuntu2 [27.8 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgnomekbd-common all 3.1.92-0ubuntu1 [8,240 B]
Get:23 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgnomekbd7 amd64 3.1.92-0ubuntu1 [57.1 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-settings-daemon amd64 3.1.92-0ubuntu3 [447 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ oneiric/main banshee amd64 2.2.0-1ubuntu1 [2,085 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ oneiric/main banshee-extension-soundmenu amd64 2.2.0-1ubuntu1 [21.1 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ oneiric/main banshee-extension-ubuntuonemusicstore amd64 2.2.0-1ubuntu1 [17.8 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ oneiric/main binutils amd64 2.21.53.20110810-0ubuntu3 [2,635 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ oneiric/main brasero-common all 3.1.92-0ubuntu1 [300 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ oneiric/main brasero-cdrkit amd64 3.1.92-0ubuntu1 [37.9 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ oneiric/main brasero amd64 3.1.92-0ubuntu1 [190 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libbrasero-media3-1 amd64 3.1.92-0ubuntu1 [471 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ oneiric/main compiz-plugins-main amd64 1:0.9.5.94+bzr20110919-0ubuntu1 [751 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ oneiric/main compiz-plugins-main-default amd64 1:0.9.5.94+bzr20110919-0ubuntu1 [587 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ oneiric/main compiz-gnome amd64 1:0.9.5.94+bzr20110919-0ubuntu1 [353 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ oneiric/main compiz-plugins amd64 1:0.9.5.94+bzr20110919-0ubuntu1 [756 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ oneiric/main compiz-plugins-default amd64 1:0.9.5.94+bzr20110919-0ubuntu1 [598 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdecoration0 amd64 1:0.9.5.94+bzr20110919-0ubuntu1 [24.1 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ oneiric/main compiz-core amd64 1:0.9.5.94+bzr20110919-0ubuntu1 [279 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ oneiric/main compiz all 1:0.9.5.94+bzr20110919-0ubuntu1 [5,954 B]
Get:41 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-dbusmenu-gtk-0.4 amd64 0.4.94-0ubuntu1 [5,474 B]
Get:42 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdbusmenu-gtk4 amd64 0.4.94-0ubuntu1 [29.9 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-dbusmenu-glib-0.4 amd64 0.4.94-0ubuntu1 [7,180 B]
Get:44 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdbusmenu-glib4 amd64 0.4.94-0ubuntu1 [43.9 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdbusmenu-gtk3-4 amd64 0.4.94-0ubuntu1 [30.0 kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ oneiric/main deja-dup amd64 19.92-0ubuntu2 [593 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libpeas-common all 1.1.4-0ubuntu1 [13.4 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libpeas-1.0-0 amd64 1.1.4-0ubuntu1 [65.8 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu/ oneiric/main eog amd64 3.1.92-0ubuntu1 [748 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgnome-bluetooth8 amd64 3.1.92-0ubuntu1 [54.8 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-bluetooth amd64 3.1.92-0ubuntu1 [270 kB]
Get:52 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-gnomebluetooth-1.0 amd64 3.1.92-0ubuntu1 [5,708 B]
Get:53 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libindicate-gtk3 amd64 0.6.1-0ubuntu1 [5,406 B]
Get:54 http://us.archive.ubuntu.com/ubuntu/ oneiric/main python-indicate amd64 0.6.1-0ubuntu1 [15.6 kB]
Get:55 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-indicate-0.6 amd64 0.6.1-0ubuntu1 [7,186 B]
Get:56 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libindicate5 amd64 0.6.1-0ubuntu1 [31.9 kB]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-games-common amd64 1:3.1.92-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-mahjongg amd64 1:3.1.92-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Get:57 http://us.archive.ubuntu.com/ubuntu/ oneiric/main unity-2d-spread amd64 4.10.0-0ubuntu1 [27.2 kB]
Get:58 http://us.archive.ubuntu.com/ubuntu/ oneiric/main unity-2d-places amd64 4.10.0-0ubuntu1 [241 kB]
Get:59 http://us.archive.ubuntu.com/ubuntu/ oneiric/main unity-2d-panel amd64 4.10.0-0ubuntu1 [131 kB]
Get:60 http://us.archive.ubuntu.com/ubuntu/ oneiric/main unity-2d-launcher amd64 4.10.0-0ubuntu1 [64.4 kB]
Get:61 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libunity-2d-private0 amd64 4.10.0-0ubuntu1 [414 kB]
Get:62 http://us.archive.ubuntu.com/ubuntu/ oneiric/main unity-2d all 4.10.0-0ubuntu1 [4,436 B]
Get:63 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-session-bin amd64 3.1.92-0ubuntu1 [165 kB]
Get:64 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-session all 3.1.92-0ubuntu1 [13.7 kB]
Get:65 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-session-common all 3.1.92-0ubuntu1 [40.7 kB]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-sudoku amd64 1:3.1.92-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnomine amd64 1:3.1.92-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Get:66 http://us.archive.ubuntu.com/ubuntu/ oneiric/main hpijs amd64 3.11.7-1ubuntu1 [354 kB]
Get:67 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libhpmud0 amd64 3.11.7-1ubuntu1 [112 kB]
Get:68 http://us.archive.ubuntu.com/ubuntu/ oneiric/main hplip-cups amd64 3.11.7-1ubuntu1 [298 kB]
Get:69 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libgtk-3-bin all 3.1.92-0ubuntu1 [15.9 kB]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libnm-util2 amd64 0.9.1.90-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libnm-glib-vpn1 amd64 0.9.1.90-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libnm-glib4 amd64 0.9.1.90-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Get:70 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libsane amd64 1.0.22-2ubuntu2 [4,098 kB]
Get:71 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libsane-hpaio amd64 3.11.7-1ubuntu1 [125 kB]
Get:72 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libyelp0 amd64 3.1.4-0ubuntu1 [128 kB]
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main network-manager amd64 0.9.1.90-0ubuntu1
  404  Not Found [IP: 91.189.92.171 80]
Get:73 http://us.archive.ubuntu.com/ubuntu/ oneiric/main sane-utils amd64 1.0.22-2ubuntu2 [205 kB]
Get:74 http://us.archive.ubuntu.com/ubuntu/ oneiric/main yelp amd64 3.1.4-0ubuntu1 [55.8 kB]
Get:75 http://us.archive.ubuntu.com/ubuntu/ oneiric/main ubuntu-desktop amd64 1.243 [3,818 B]
Get:76 http://us.archive.ubuntu.com/ubuntu/ oneiric/main unity-lens-files amd64 0.6.8-0ubuntu1 [33.9 kB]
Get:77 http://us.archive.ubuntu.com/ubuntu/ oneiric/main zeitgeist-datahub amd64 0.7.0-0ubuntu4 [25.8 kB]
Get:78 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-peas-1.0 amd64 1.1.4-0ubuntu1 [6,114 B]
Get:79 http://us.archive.ubuntu.com/ubuntu/ oneiric/main oneconf all 0.2.6.5 [31.0 kB]
Get:80 http://us.archive.ubuntu.com/ubuntu/ oneiric/main shotwell amd64 0.11.2-0ubuntu1 [2,353 kB]
Fetched 25.9 MB in 2min 41s (160 kB/s)                                         
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.11_0.8.16~exp5ubuntu11_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp5ubuntu11_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.3_0.8.16~exp5ubuntu11_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.16~exp5ubuntu11_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp5ubuntu11_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-common_3.1.92-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-mahjongg_3.1.92-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-sudoku_3.1.92-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnomine_3.1.92-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util2_0.9.1.90-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib-vpn1_0.9.1.90-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib4_0.9.1.90-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.1.90-0ubuntu1_amd64.deb  404  Not Found [IP: 91.189.92.171 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

---

### Post by paul_in_london on 2011-09-22
[B][Edited slightly to clarify, I hope]
[/B]
Ok. Did the second command produce any other output or did it bomb out at this point:

```
E: [COLOR="Red"]Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/COLOR]
```

If it bombed out, can you try running it again? As a general rule by the way it's best to check for updates and apply them before trying to install something that isn't already installed.

After the first command, you should see stuff like:

```
...
Ign http://archive.ubuntu.com oneiric-proposed/universe Translation-en_GB
Ign http://archive.ubuntu.com oneiric-proposed/universe Translation-en
Fetched 17.4 MB in 16s (1,046 kB/s)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric-updates/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric-updates/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric-security/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric-security/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Current status: 1 update [+1].
paul@oneiric-64:~$Current status: 1 update [+1].

```

The output from the second command will be along these lines - well the bit at the end when it fetches stuff!

```
paul@oneiric-64:~$ sudo aptitude safe-upgrade
The following packages will be upgraded: 
  byobu 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 76.7 kB of archives. After unpacking 4,096 B will be used.
Do you want to continue? [Y/n/?] Y
Err http://archive.ubuntu.com/ubuntu/ oneiric/main byobu all 4.34-0ubuntu1
  404  Not Found [IP: 91.189.88.30 80]
0% [Working]localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/byobu/byobu_4.34-0ubuntu1_all.deb: 404  Not Found [IP: 91.189.88.30 80]
                                         
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/byobu/byobu_4.34-0ubuntu1_all.deb: 404  Not Found [IP: 91.189.88.30 80]
paul@oneiric-64:~$
```

The mirror is playing up. Had to try another couple of times:

```
paul@oneiric-64:~$ sudo aptitude safe-upgrade
The following packages will be upgraded: 
  byobu 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 76.7 kB of archives. After unpacking 4,096 B will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://archive.ubuntu.com/ubuntu/ oneiric/main byobu all 4.34-0ubuntu1 [76.7 kB]
Fetched 76.7 kB in 0s (412 kB/s)
Preconfiguring packages ...
(Reading database ... 208336 files and directories currently installed.)
Preparing to replace byobu 4.33-0ubuntu1 (using .../byobu_4.34-0ubuntu1_all.deb) ...
Unpacking replacement byobu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up byobu (4.34-0ubuntu1) ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
Current status: 0 updates [-1].
paul@oneiric-64:~$
```

---

### Post by madjr on 2011-09-22
Hi bikewrecker,

if you're relative new i would seriously stick with 10.10 or 11.04 for now.

11.10 is a beta and it will break a lot. (is broken for me now, so i will need to fix it, but is something i always do when beta testing)

even the final version in the first month will have bugs till updates fix them.

---

### Post by bikewrecker on 2011-09-22
Ok i ran the second command a bunch more times and on the fourth time it looks like it went through. Here's what it put
```

daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnome-control-center-data
The following packages will be upgraded:
  apt apt-transport-https apt-utils bamfdaemon banshee
  banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore binutils
  brasero brasero-cdrkit brasero-common compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default compiz-plugins-main
  compiz-plugins-main-default deja-dup eog gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-indicate-0.6 gir1.2-pango-1.0 gir1.2-peas-1.0 gnome-bluetooth
  gnome-desktop3-data gnome-games-common gnome-mahjongg gnome-session
  gnome-session-bin gnome-session-common gnome-settings-daemon gnome-sudoku
  gnomine hpijs hplip-cups language-selector-common language-selector-gnome
  libapt-inst1.3 libapt-pkg4.11 libbamf0 libbamf3-0 libbrasero-media3-1
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdecoration0
  libgail-3-0 libgail-3-common libgnome-bluetooth8 libgnome-desktop-3-2
  libgnomekbd-common libgnomekbd7 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libhpmud0 libindicate-gtk3 libindicate5 libnm-glib-vpn1 libnm-glib4
  libnm-util2 libpango1.0-0 libpango1.0-0:i386 libpeas-1.0-0 libpeas-common
  libsane libsane-hpaio libunity-2d-private0 libyelp0 network-manager oneconf
  python-gobject python-gobject-cairo python-indicate sane-utils shotwell
  ubuntu-desktop ubuntu-minimal ubuntu-standard unity-2d unity-2d-launcher
  unity-2d-panel unity-2d-places unity-2d-spread unity-lens-files
  update-manager update-manager-core yelp zeitgeist-datahub
93 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 3,789 kB/29.7 MB of archives.
After this operation, 438 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libapt-pkg4.11 amd64 0.8.16~exp5ubuntu11 [518 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/main apt amd64 0.8.16~exp5ubuntu11 [1,053 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libapt-inst1.3 amd64 0.8.16~exp5ubuntu11 [37.0 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric/main apt-utils amd64 0.8.16~exp5ubuntu11 [189 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric/main apt-transport-https amd64 0.8.16~exp5ubuntu11 [15.8 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-games-common amd64 1:3.1.92-0ubuntu1 [190 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-mahjongg amd64 1:3.1.92-0ubuntu1 [461 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnome-sudoku amd64 1:3.1.92-0ubuntu1 [298 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gnomine amd64 1:3.1.92-0ubuntu1 [329 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libnm-util2 amd64 0.9.1.90-0ubuntu1 [119 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libnm-glib-vpn1 amd64 0.9.1.90-0ubuntu1 [17.7 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libnm-glib4 amd64 0.9.1.90-0ubuntu1 [78.6 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ oneiric/main network-manager amd64 0.9.1.90-0ubuntu1 [483 kB]
Fetched 3,789 kB in 22s (165 kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 192700 files and directories currently installed.)
Preparing to replace libbamf3-0 0.2.98-0ubuntu2 (using .../libbamf3-0_0.2.100-0ubuntu1_amd64.deb) ...
Unpacking replacement libbamf3-0 ...
Preparing to replace libgail-3-common 3.1.90-0ubuntu1 (using .../libgail-3-common_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libgail-3-common ...
Preparing to replace libpango1.0-0:i386 1.29.3-0ubuntu3 (using .../libpango1.0-0_1.29.3+git20110916-0ubuntu1_i386.deb) ...
De-configuring libpango1.0-0 ...
Unpacking replacement libpango1.0-0:i386 ...
Preparing to replace libpango1.0-0 1.29.3-0ubuntu3 (using .../libpango1.0-0_1.29.3+git20110916-0ubuntu1_amd64.deb) ...
Unpacking replacement libpango1.0-0 ...
Preparing to replace libgail-3-0 3.1.90-0ubuntu1 (using .../libgail-3-0_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libgail-3-0 ...
Preparing to replace libgtk-3-common 3.1.90-0ubuntu1 (using .../libgtk-3-common_3.1.92-0ubuntu1_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace libgtk-3-0 3.1.90-0ubuntu1 (using .../libgtk-3-0_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libgtk-3-0 ...
Preparing to replace libbamf0 0.2.98-0ubuntu2 (using .../libbamf0_0.2.100-0ubuntu1_amd64.deb) ...
Unpacking replacement libbamf0 ...
Preparing to replace bamfdaemon 0.2.98-0ubuntu2 (using .../bamfdaemon_0.2.100-0ubuntu1_amd64.deb) ...
Unpacking replacement bamfdaemon ...
Preparing to replace libapt-pkg4.11 0.8.16~exp5ubuntu9 (using .../libapt-pkg4.11_0.8.16~exp5ubuntu11_amd64.deb) ...
Unpacking replacement libapt-pkg4.11 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up libapt-pkg4.11 (0.8.16~exp5ubuntu11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 192700 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp5ubuntu9 (using .../apt_0.8.16~exp5ubuntu11_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp5ubuntu11) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
(Reading database ... 192700 files and directories currently installed.)
Preparing to replace libapt-inst1.3 0.8.16~exp5ubuntu9 (using .../libapt-inst1.3_0.8.16~exp5ubuntu11_amd64.deb) ...
Unpacking replacement libapt-inst1.3 ...
Preparing to replace apt-utils 0.8.16~exp5ubuntu9 (using .../apt-utils_0.8.16~exp5ubuntu11_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace ubuntu-minimal 1.242 (using .../ubuntu-minimal_1.243_amd64.deb) ...
Unpacking replacement ubuntu-minimal ...
Preparing to replace apt-transport-https 0.8.16~exp5ubuntu9 (using .../apt-transport-https_0.8.16~exp5ubuntu11_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace python-gobject 2.90.3-1svn1 (using .../python-gobject_3.0.0-0svn1_amd64.deb) ...
Unpacking replacement python-gobject ...
Preparing to replace gir1.2-pango-1.0 1.29.3-0ubuntu3 (using .../gir1.2-pango-1.0_1.29.3+git20110916-0ubuntu1_amd64.deb) ...
Unpacking replacement gir1.2-pango-1.0 ...
Preparing to replace gir1.2-gtk-3.0 3.1.90-0ubuntu1 (using .../gir1.2-gtk-3.0_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace language-selector-gnome 0.51 (using .../language-selector-gnome_0.52_all.deb) ...
Unpacking replacement language-selector-gnome ...
Preparing to replace language-selector-common 0.51 (using .../language-selector-common_0.52_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace python-gobject-cairo 2.90.3-1svn1 (using .../python-gobject-cairo_3.0.0-0svn1_amd64.deb) ...
Unpacking replacement python-gobject-cairo ...
Preparing to replace ubuntu-standard 1.242 (using .../ubuntu-standard_1.243_amd64.deb) ...
Unpacking replacement ubuntu-standard ...
Preparing to replace update-manager-core 1:0.152.18 (using .../update-manager-core_1%3a0.152.19_amd64.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace update-manager 1:0.152.18 (using .../update-manager_1%3a0.152.19_all.deb) ...
Unpacking replacement update-manager ...
Preparing to replace libgnome-desktop-3-2 3.1.92-0ubuntu1 (using .../libgnome-desktop-3-2_3.1.92-0ubuntu2_amd64.deb) ...
Unpacking replacement libgnome-desktop-3-2 ...
Preparing to replace gnome-desktop3-data 3.1.92-0ubuntu1 (using .../gnome-desktop3-data_3.1.92-0ubuntu2_all.deb) ...
Unpacking replacement gnome-desktop3-data ...
Preparing to replace libgnomekbd-common 3.1.90-1 (using .../libgnomekbd-common_3.1.92-0ubuntu1_all.deb) ...
Unpacking replacement libgnomekbd-common ...
Preparing to replace libgnomekbd7 3.1.90-1 (using .../libgnomekbd7_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libgnomekbd7 ...
Preparing to replace gnome-settings-daemon 3.1.92-0ubuntu2 (using .../gnome-settings-daemon_3.1.92-0ubuntu3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace banshee 2.1.4-1ubuntu1 (using .../banshee_2.2.0-1ubuntu1_amd64.deb) ...
Unpacking replacement banshee ...
Preparing to replace banshee-extension-soundmenu 2.1.4-1ubuntu1 (using .../banshee-extension-soundmenu_2.2.0-1ubuntu1_amd64.deb) ...
Unpacking replacement banshee-extension-soundmenu ...
Preparing to replace banshee-extension-ubuntuonemusicstore 2.1.4-1ubuntu1 (using .../banshee-extension-ubuntuonemusicstore_2.2.0-1ubuntu1_amd64.deb) ...
Unpacking replacement banshee-extension-ubuntuonemusicstore ...
Preparing to replace binutils 2.21.53.20110810-0ubuntu2 (using .../binutils_2.21.53.20110810-0ubuntu3_amd64.deb) ...
Unpacking replacement binutils ...
Preparing to replace brasero-common 3.1.90-0ubuntu1 (using .../brasero-common_3.1.92-0ubuntu1_all.deb) ...
Unpacking replacement brasero-common ...
Preparing to replace brasero-cdrkit 3.1.90-0ubuntu1 (using .../brasero-cdrkit_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement brasero-cdrkit ...
Preparing to replace brasero 3.1.90-0ubuntu1 (using .../brasero_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement brasero ...
Preparing to replace libbrasero-media3-1 3.1.90-0ubuntu1 (using .../libbrasero-media3-1_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libbrasero-media3-1 ...
Preparing to replace compiz-plugins-main 1:0.9.5.94+bzr20110915-0ubuntu1 (using .../compiz-plugins-main_1%3a0.9.5.94+bzr20110919-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins-main ...
Preparing to replace compiz-plugins-main-default 1:0.9.5.94+bzr20110915-0ubuntu1 (using .../compiz-plugins-main-default_1%3a0.9.5.94+bzr20110919-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins-main-default ...
Preparing to replace compiz-gnome 1:0.9.5.94+bzr2803-0ubuntu5 (using .../compiz-gnome_1%3a0.9.5.94+bzr20110919-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-gnome ...
Preparing to replace compiz-plugins 1:0.9.5.94+bzr2803-0ubuntu5 (using .../compiz-plugins_1%3a0.9.5.94+bzr20110919-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins ...
Preparing to replace compiz-plugins-default 1:0.9.5.94+bzr2803-0ubuntu5 (using .../compiz-plugins-default_1%3a0.9.5.94+bzr20110919-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-plugins-default ...
Preparing to replace libdecoration0 1:0.9.5.94+bzr2803-0ubuntu5 (using .../libdecoration0_1%3a0.9.5.94+bzr20110919-0ubuntu1_amd64.deb) ...
Unpacking replacement libdecoration0 ...
Preparing to replace compiz-core 1:0.9.5.94+bzr2803-0ubuntu5 (using .../compiz-core_1%3a0.9.5.94+bzr20110919-0ubuntu1_amd64.deb) ...
Unpacking replacement compiz-core ...
Preparing to replace compiz 1:0.9.5.94+bzr2803-0ubuntu5 (using .../compiz_1%3a0.9.5.94+bzr20110919-0ubuntu1_all.deb) ...
Unpacking replacement compiz ...
Preparing to replace gir1.2-dbusmenu-gtk-0.4 0.4.93-0ubuntu1 (using .../gir1.2-dbusmenu-gtk-0.4_0.4.94-0ubuntu1_amd64.deb) ...
Unpacking replacement gir1.2-dbusmenu-gtk-0.4 ...
Preparing to replace libdbusmenu-gtk4 0.4.93-0ubuntu1 (using .../libdbusmenu-gtk4_0.4.94-0ubuntu1_amd64.deb) ...
Unpacking replacement libdbusmenu-gtk4 ...
Preparing to replace gir1.2-dbusmenu-glib-0.4 0.4.93-0ubuntu1 (using .../gir1.2-dbusmenu-glib-0.4_0.4.94-0ubuntu1_amd64.deb) ...
Unpacking replacement gir1.2-dbusmenu-glib-0.4 ...
Preparing to replace libdbusmenu-glib4 0.4.93-0ubuntu1 (using .../libdbusmenu-glib4_0.4.94-0ubuntu1_amd64.deb) ...
Unpacking replacement libdbusmenu-glib4 ...
Preparing to replace libdbusmenu-gtk3-4 0.4.93-0ubuntu1 (using .../libdbusmenu-gtk3-4_0.4.94-0ubuntu1_amd64.deb) ...
Unpacking replacement libdbusmenu-gtk3-4 ...
Preparing to replace deja-dup 19.92-0ubuntu1 (using .../deja-dup_19.92-0ubuntu2_amd64.deb) ...
Unpacking replacement deja-dup ...
Preparing to replace libpeas-common 1.1.3-0ubuntu1 (using .../libpeas-common_1.1.4-0ubuntu1_all.deb) ...
Unpacking replacement libpeas-common ...
Preparing to replace libpeas-1.0-0 1.1.3-0ubuntu1 (using .../libpeas-1.0-0_1.1.4-0ubuntu1_amd64.deb) ...
Unpacking replacement libpeas-1.0-0 ...
Preparing to replace eog 3.1.91-0ubuntu1 (using .../eog_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement eog ...
Preparing to replace libgnome-bluetooth8 3.1.4-0ubuntu2 (using .../libgnome-bluetooth8_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement libgnome-bluetooth8 ...
Preparing to replace gnome-bluetooth 3.1.4-0ubuntu2 (using .../gnome-bluetooth_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gnome-bluetooth ...
Preparing to replace gir1.2-gnomebluetooth-1.0 3.1.4-0ubuntu2 (using .../gir1.2-gnomebluetooth-1.0_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gir1.2-gnomebluetooth-1.0 ...
Preparing to replace libindicate-gtk3 0.5.91-0ubuntu3 (using .../libindicate-gtk3_0.6.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libindicate-gtk3 ...
Preparing to replace python-indicate 0.5.91-0ubuntu3 (using .../python-indicate_0.6.1-0ubuntu1_amd64.deb) ...
Unpacking replacement python-indicate ...
Preparing to replace gir1.2-indicate-0.6 0.5.91-0ubuntu3 (using .../gir1.2-indicate-0.6_0.6.1-0ubuntu1_amd64.deb) ...
Unpacking replacement gir1.2-indicate-0.6 ...
Preparing to replace libindicate5 0.5.91-0ubuntu3 (using .../libindicate5_0.6.1-0ubuntu1_amd64.deb) ...
Unpacking replacement libindicate5 ...
Preparing to replace gnome-games-common 1:3.1.91-0ubuntu1 (using .../gnome-games-common_1%3a3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gnome-games-common ...
Preparing to replace gnome-mahjongg 1:3.1.91-0ubuntu1 (using .../gnome-mahjongg_1%3a3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gnome-mahjongg ...
Preparing to replace unity-2d-spread 4.8.0-0ubuntu1 (using .../unity-2d-spread_4.10.0-0ubuntu1_amd64.deb) ...
Unpacking replacement unity-2d-spread ...
Preparing to replace unity-2d-places 4.8.0-0ubuntu1 (using .../unity-2d-places_4.10.0-0ubuntu1_amd64.deb) ...
Unpacking replacement unity-2d-places ...
Preparing to replace unity-2d-panel 4.8.0-0ubuntu1 (using .../unity-2d-panel_4.10.0-0ubuntu1_amd64.deb) ...
Unpacking replacement unity-2d-panel ...
Preparing to replace unity-2d-launcher 4.8.0-0ubuntu1 (using .../unity-2d-launcher_4.10.0-0ubuntu1_amd64.deb) ...
Unpacking replacement unity-2d-launcher ...
Preparing to replace libunity-2d-private0 4.8.0-0ubuntu1 (using .../libunity-2d-private0_4.10.0-0ubuntu1_amd64.deb) ...
Unpacking replacement libunity-2d-private0 ...
Preparing to replace unity-2d 4.8.0-0ubuntu1 (using .../unity-2d_4.10.0-0ubuntu1_all.deb) ...
Unpacking replacement unity-2d ...
Preparing to replace gnome-session-bin 3.1.91-0ubuntu2 (using .../gnome-session-bin_3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gnome-session-bin ...
Preparing to replace gnome-session 3.1.91-0ubuntu2 (using .../gnome-session_3.1.92-0ubuntu1_all.deb) ...
Unpacking replacement gnome-session ...
Preparing to replace gnome-session-common 3.1.91-0ubuntu2 (using .../gnome-session-common_3.1.92-0ubuntu1_all.deb) ...
Unpacking replacement gnome-session-common ...
Preparing to replace gnome-sudoku 1:3.1.91-0ubuntu1 (using .../gnome-sudoku_1%3a3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gnome-sudoku ...
Preparing to replace gnomine 1:3.1.91-0ubuntu1 (using .../gnomine_1%3a3.1.92-0ubuntu1_amd64.deb) ...
Unpacking replacement gnomine ...
Preparing to replace hpijs 3.11.7-0ubuntu5 (using .../hpijs_3.11.7-1ubuntu1_amd64.deb) ...
Unpacking replacement hpijs ...
Preparing to replace libhpmud0 3.11.7-0ubuntu5 (using .../libhpmud0_3.11.7-1ubuntu1_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-cups 3.11.7-0ubuntu5 (using .../hplip-cups_3.11.7-1ubuntu1_amd64.deb) ...
Unpacking replacement hplip-cups ...
Preparing to replace libgtk-3-bin 3.1.90-0ubuntu1 (using .../libgtk-3-bin_3.1.92-0ubuntu1_all.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace libnm-util2 0.9.0-0ubuntu3 (using .../libnm-util2_0.9.1.90-0ubuntu1_amd64.deb) ...
Unpacking replacement libnm-util2 ...
Preparing to replace libnm-glib-vpn1 0.9.0-0ubuntu3 (using .../libnm-glib-vpn1_0.9.1.90-0ubuntu1_amd64.deb) ...
Unpacking replacement libnm-glib-vpn1 ...
Preparing to replace libnm-glib4 0.9.0-0ubuntu3 (using .../libnm-glib4_0.9.1.90-0ubuntu1_amd64.deb) ...
Unpacking replacement libnm-glib4 ...
Preparing to replace libsane 1.0.22-2ubuntu1 (using .../libsane_1.0.22-2ubuntu2_amd64.deb) ...
Unpacking replacement libsane ...
Preparing to replace libsane-hpaio 3.11.7-0ubuntu5 (using .../libsane-hpaio_3.11.7-1ubuntu1_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace libyelp0 3.1.3-0ubuntu1 (using .../libyelp0_3.1.4-0ubuntu1_amd64.deb) ...
Unpacking replacement libyelp0 ...
Preparing to replace network-manager 0.9.0-0ubuntu3 (using .../network-manager_0.9.1.90-0ubuntu1_amd64.deb) ...
Unpacking replacement network-manager ...
Preparing to replace sane-utils 1.0.22-2ubuntu1 (using .../sane-utils_1.0.22-2ubuntu2_amd64.deb) ...
invoke-rc.d: policy-rc.d denied execution of stop.
Unpacking replacement sane-utils ...
Preparing to replace yelp 3.1.3-0ubuntu1 (using .../yelp_3.1.4-0ubuntu1_amd64.deb) ...
Unpacking replacement yelp ...
Preparing to replace ubuntu-desktop 1.242 (using .../ubuntu-desktop_1.243_amd64.deb) ...
Unpacking replacement ubuntu-desktop ...
Preparing to replace unity-lens-files 0.6.6-0ubuntu1 (using .../unity-lens-files_0.6.8-0ubuntu1_amd64.deb) ...
Unpacking replacement unity-lens-files ...
Preparing to replace zeitgeist-datahub 0.7.0-0ubuntu3 (using .../zeitgeist-datahub_0.7.0-0ubuntu4_amd64.deb) ...
Unpacking replacement zeitgeist-datahub ...
Preparing to replace gir1.2-peas-1.0 1.1.3-0ubuntu1 (using .../gir1.2-peas-1.0_1.1.4-0ubuntu1_amd64.deb) ...
Unpacking replacement gir1.2-peas-1.0 ...
Preparing to replace oneconf 0.2.6.4 (using .../oneconf_0.2.6.5_all.deb) ...
Unpacking replacement oneconf ...
Preparing to replace shotwell 0.11.1-0ubuntu1 (using .../shotwell_0.11.2-0ubuntu1_amd64.deb) ...
Unpacking replacement shotwell ...
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
Processing triggers for shared-mime-info ...
Processing triggers for cups ...
invoke-rc.d: policy-rc.d denied execution of start.
Updating PPD files for hpijs ...
Updating PPD files for hplip-cups ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libgtk-3-common (3.1.92-0ubuntu1) ...
Setting up libpango1.0-0 (1.29.3+git20110916-0ubuntu1) ...
Setting up libgtk-3-0 (3.1.92-0ubuntu1) ...
Setting up bamfdaemon (0.2.100-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf.index...
Setting up libbamf3-0 (0.2.100-0ubuntu1) ...
Setting up libgail-3-0 (3.1.92-0ubuntu1) ...
Setting up libgail-3-common (3.1.92-0ubuntu1) ...
Setting up libpango1.0-0:i386 (1.29.3+git20110916-0ubuntu1) ...
Setting up libbamf0 (0.2.100-0ubuntu1) ...
Setting up libapt-inst1.3 (0.8.16~exp5ubuntu11) ...
Setting up apt-utils (0.8.16~exp5ubuntu11) ...
Setting up ubuntu-minimal (1.243) ...
Setting up apt-transport-https (0.8.16~exp5ubuntu11) ...
Setting up python-gobject (3.0.0-0svn1) ...
Setting up gir1.2-pango-1.0 (1.29.3+git20110916-0ubuntu1) ...
Setting up gir1.2-gtk-3.0 (3.1.92-0ubuntu1) ...
Setting up language-selector-common (0.52) ...
Setting up language-selector-gnome (0.52) ...
Setting up python-gobject-cairo (3.0.0-0svn1) ...
Setting up ubuntu-standard (1.243) ...
Setting up update-manager-core (1:0.152.19) ...
Setting up update-manager (1:0.152.19) ...
Setting up gnome-desktop3-data (3.1.92-0ubuntu2) ...
Setting up libgnome-desktop-3-2 (3.1.92-0ubuntu2) ...
Setting up libgnomekbd-common (3.1.92-0ubuntu1) ...
Setting up libgnomekbd7 (3.1.92-0ubuntu1) ...
Setting up gnome-settings-daemon (3.1.92-0ubuntu3) ...
Setting up banshee (2.2.0-1ubuntu1) ...
Setting up banshee-extension-soundmenu (2.2.0-1ubuntu1) ...
Setting up banshee-extension-ubuntuonemusicstore (2.2.0-1ubuntu1) ...
Setting up binutils (2.21.53.20110810-0ubuntu3) ...
Setting up brasero-common (3.1.92-0ubuntu1) ...
Setting up libbrasero-media3-1 (3.1.92-0ubuntu1) ...
Setting up brasero-cdrkit (3.1.92-0ubuntu1) ...
Setting up brasero (3.1.92-0ubuntu1) ...
Setting up compiz-core (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up compiz-plugins-main-default (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up compiz-plugins-main (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up libdecoration0 (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up compiz-plugins-default (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up compiz-gnome (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up compiz-plugins (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up compiz (1:0.9.5.94+bzr20110919-0ubuntu1) ...
Setting up libdbusmenu-glib4 (0.4.94-0ubuntu1) ...
Setting up libdbusmenu-gtk4 (0.4.94-0ubuntu1) ...
Setting up gir1.2-dbusmenu-glib-0.4 (0.4.94-0ubuntu1) ...
Setting up gir1.2-dbusmenu-gtk-0.4 (0.4.94-0ubuntu1) ...
Setting up libdbusmenu-gtk3-4 (0.4.94-0ubuntu1) ...
Setting up deja-dup (19.92-0ubuntu2) ...
Setting up libpeas-common (1.1.4-0ubuntu1) ...
Setting up libpeas-1.0-0 (1.1.4-0ubuntu1) ...
Setting up eog (3.1.92-0ubuntu1) ...
Setting up libgnome-bluetooth8 (3.1.92-0ubuntu1) ...
Setting up gir1.2-gnomebluetooth-1.0 (3.1.92-0ubuntu1) ...
Setting up gnome-bluetooth (3.1.92-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/bluetooth-applet.desktop ...
Setting up libindicate5 (0.6.1-0ubuntu1) ...
Setting up libindicate-gtk3 (0.6.1-0ubuntu1) ...
Setting up python-indicate (0.6.1-0ubuntu1) ...
Setting up gir1.2-indicate-0.6 (0.6.1-0ubuntu1) ...
Setting up gnome-games-common (1:3.1.92-0ubuntu1) ...
Setting up gnome-mahjongg (1:3.1.92-0ubuntu1) ...
Setting up libunity-2d-private0 (4.10.0-0ubuntu1) ...
Setting up unity-2d-spread (4.10.0-0ubuntu1) ...
Setting up unity-2d-places (4.10.0-0ubuntu1) ...
Setting up unity-2d-panel (4.10.0-0ubuntu1) ...
Setting up unity-2d-launcher (4.10.0-0ubuntu1) ...
Setting up unity-2d (4.10.0-0ubuntu1) ...
Setting up gnome-session-bin (3.1.92-0ubuntu1) ...
Setting up gnome-session-common (3.1.92-0ubuntu1) ...
Setting up gnome-session (3.1.92-0ubuntu1) ...
Setting up gnome-sudoku (1:3.1.92-0ubuntu1) ...
Setting up gnomine (1:3.1.92-0ubuntu1) ...
Setting up libhpmud0 (3.11.7-1ubuntu1) ...
Setting up hpijs (3.11.7-1ubuntu1) ...
Setting up hplip-cups (3.11.7-1ubuntu1) ...
Setting up libgtk-3-bin (3.1.92-0ubuntu1) ...
Setting up libnm-util2 (0.9.1.90-0ubuntu1) ...
Setting up libnm-glib-vpn1 (0.9.1.90-0ubuntu1) ...
Setting up libnm-glib4 (0.9.1.90-0ubuntu1) ...
Setting up libsane (1.0.22-2ubuntu2) ...
Setting up libsane-hpaio (3.11.7-1ubuntu1) ...
Setting up libyelp0 (3.1.4-0ubuntu1) ...
Setting up network-manager (0.9.1.90-0ubuntu1) ...
Setting up sane-utils (1.0.22-2ubuntu2) ...
invoke-rc.d: policy-rc.d denied execution of start.
Setting up yelp (3.1.4-0ubuntu1) ...
Setting up ubuntu-desktop (1.243) ...
Setting up unity-lens-files (0.6.8-0ubuntu1) ...
Setting up zeitgeist-datahub (0.7.0-0ubuntu4) ...
Installing new version of config file /etc/xdg/autostart/zeitgeist-datahub.desktop ...
Setting up gir1.2-peas-1.0 (1.1.4-0ubuntu1) ...
Setting up oneconf (0.2.6.5) ...
Setting up shotwell (0.11.2-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Yea I used the update manager this morning but it looks like it has more updates now..wait after that last command it looks like there is only one more update left?

---

### Post by paul_in_london on 2011-09-22
Cool. Now repeat those two commands (apt-get update/apt-get upgrade) to see if any other updates come through.

Then you could see if it'll let you install gnome-tweak-tool. Do you have gnome-shell installed?

---

### Post by bikewrecker on 2011-09-22
> **madjr said:**
> Hi bikewrecker,

if you're relative new i would seriously stick with 10.10 or 11.04 for now.

11.10 is a beta and it will break a lot. (is broken for me now, so i will need to fix it, but is something i always do when beta testing)

even the final version in the first month will have bugs till updates fix them.

Haha yea, thanks. I'm learning that lesson the hard way. So do you think it's because the OS is broken or because I'm not doing something right? If it's just the OS's fault I can wait till fixes come out, but I'm thinkin it's probably my fault.

---

### Post by paul_in_london on 2011-09-22
Don't use update manager or if you do and it offers you a partial upgrade, don't do it. If you want to use a GUI to update/upgrade, use synaptic. Be very careful if it wants to remove stuff. You have to know what you're doing. That isn't meant to sound patronising!

---

### Post by philinux on 2011-09-22
If you really wanna wreck your bike to install itunes try some of these solutions. I think version 7 is the one though. And I've never tried any as I don't use itunes.

[itunes]("http://www.google.co.uk/pda?q=linux+itunes")

---

### Post by bikewrecker on 2011-09-22
> **paul_in_london said:**
> Cool. Now repeat those two commands (apt-get update/apt-get upgrade) to see if any other updates come through.

Then you could see if it'll let you install gnome-tweak-tool. Do you have gnome-shell installed? 
Ok, It wouldn't let me install "gnome-control-center-data" this way so i went in the update manager and got it from there

How do I tell if I have gnome-shell or not?

---

### Post by paul_in_london on 2011-09-22
> **bikewrecker said:**
> Haha yea, thanks. I'm learning that lesson the hard way. So do you think it's because the OS is broken or because I'm not doing something right? If it's just the OS's fault I can wait till fixes come out, but I'm thinkin it's probably my fault.

Don't worry, it's a good way to learn. If you have another install to fall back on that would be useful. Or install in a virtual machine to get used to things.

---

### Post by bikewrecker on 2011-09-22
> **philinux said:**
> If you really wanna wreck your bike to install itunes try some of these solutions. I think version 7 is the one though. And I've never tried any as I don't use itunes.

[itunes]("http://www.google.co.uk/pda?q=linux+itunes")
Allright, Cool thanks. It's weird how wine works...

---

### Post by bikewrecker on 2011-09-22
> **paul_in_london said:**
> Don't worry, it's a good way to learn. If you have another install to fall back on that would be useful. Or install in a virtual machine to get used to things.
Yea I have a windows 7 partition and an old ubuntu 10.10 partition as well as this one. My linux buddy said that the kernel in 10.10 was too old (2.6something) and to install this one... he uses arc linux though so idk how skilled he thought I am with ubuntu lol. Ohwell. I'm learning a ton and I'm having fun while doing it! Thank you everybody for your help!

---

### Post by philinux on 2011-09-22
> **bikewrecker said:**
> Allright, Cool thanks. It's weird how wine works...

Mostly wine does not work for me lol. I have a notebook that came with win 7 64 bit premium. ;)

Dual booted of course.

---

### Post by paul_in_london on 2011-09-22
> **bikewrecker said:**
> Ok, It wouldn't let me install "gnome-control-center-data" this way so i went in the update manager and got it from there

How do I tell if I have gnome-shell or not?

gnome-shell isn't installed by default, so you probably don't have it. One way to check is:

```
paul@oneiric-64:~$ sudo apt-cache policy gnome-shell
[sudo] password for paul: 
gnome-shell:
  Installed: 3.1.92-0ubuntu1~11.10~ricotz0
  Candidate: 3.1.92-0ubuntu1~11.10~ricotz0
  Version table:
 *** 3.1.92-0ubuntu1~11.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     3.1.90.1-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages
paul@oneiric-64:~$
```

The apt-get upgrade (or, similarly, aptitude safe=upgrade) is a more conservative way of updating compared with apt-get dist-upgrade/aptitude full-upgrade, but you'll get to know about these things.

I'm not keen on wine by the way - except the kind you drink! :lolflag:

---

### Post by Harry33 on 2011-09-22
> **bikewrecker said:**
> Ok, It wouldn't let me install "gnome-control-center-data" this way so i went in the update manager and got it from there

How do I tell if I have gnome-shell or not?

There is no need to install gnome-control-center-data (3.1.92-0ubuntu2) package now.
The build of the other two related packages (gnome-control-center, libgnome-control-center1) failed for 64-bit setups.
Perhaps they are rebuild tomorrow.

See here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-control-center/1:3.1.92-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/gnome-control-center/1:3.1.92-0ubuntu2)

---

### Post by bikewrecker on 2011-09-22
Ok, I don't have it installed. Is that something I need? just "sudo apt-get install gnome-shell"?

---

### Post by jarpiw on 2011-09-22
FYI I've just tried to install gnome-tweak-tool and aptitude says there is a conflict between libcogl5 and libcogl2 and both are needed.

---

### Post by chlorox on 2011-09-22
You're going to need to wait a little bit. If you're using the official Ubuntu/Oneiric repos. They're waiting on a couple of dependencies before gnome-shell can be rebuilt. Some things are still in transition.

Isn't the Gnome 3.2 release scheduled for next week?

---

### Post by paul_in_london on 2011-09-22
> **bikewrecker said:**
> Ok, I don't have it installed. Is that something I need? just "sudo apt-get install gnome-shell"?

You don't actually need it, but I use it instead of the default Unity interface.

---

### Post by bikewrecker on 2011-09-22
> **paul_in_london said:**
> You don't actually need it, but I use it instead of the default Unity interface.
Ok well I'm not a big fan of the unity interface either, but like these other guys said. It doesn't look like gnome-shell is out yet or somthing.

```

daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ sudo apt-get install gnome-shell[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libcogl2 (>= 1.7.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by RomeReactor on 2011-09-22
HI bikewrecker. In the first page (post number *8*) you got the following output after running apt-get update:

```
daniel@daniel-EP45-UD3L:~$ sudo apt-get update
[sudo] password for daniel: 
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901) dists/oneiric/main/binary-i386/ Translation-en
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://archive.canonical.com natty InRelease                               
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:1 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg         
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://archive.canonical.com oneiric Release                               
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://archive.canonical.com natty Release                       
Get:3 http://us.archive.ubuntu.com oneiric Release [39.8 kB]                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Get:4 http://us.archive.ubuntu.com oneiric/main Sources [874 kB]               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Ign http://archive.canonical.com oneiric/partner Translation-en_US          
Ign http://archive.canonical.com oneiric/partner Translation-en              
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                  
Ign http://archive.canonical.com natty/partner Translation-en_US             
Ign http://archive.canonical.com natty/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en                     
Hit http://security.ubuntu.com oneiric-security/restricted Sources           
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex
Ign http://security.ubuntu.com oneiric-security/main Translation-en_US         
Ign http://security.ubuntu.com oneiric-security/main Translation-en            
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_US   
Get:5 http://us.archive.ubuntu.com oneiric/restricted Sources [5,326 B]        
Get:6 http://us.archive.ubuntu.com oneiric/universe Sources [4,683 kB]         
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_US   
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_US     
Ign http://security.ubuntu.com oneiric-security/universe Translation-en        
Get:7 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]         
Get:8 http://us.archive.ubuntu.com oneiric/main amd64 Packages [1,225 kB]      
Get:9 http://us.archive.ubuntu.com oneiric/restricted amd64 Packages [7,963 B] 
Get:10 http://us.archive.ubuntu.com oneiric/universe amd64 Packages [4,453 kB] 
Get:11 http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB] 
Get:12 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,225 kB]      
Get:13 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,009 B] 
Get:14 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,460 kB]  
Get:15 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Ign http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Ign http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Ign http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Ign http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Get:16 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,920 kB] 
Ign http://us.archive.ubuntu.com oneiric/main Translation-en_US                
Ign http://us.archive.ubuntu.com oneiric/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com oneiric/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com oneiric/universe Translation-en_US            
Ign http://us.archive.ubuntu.com oneiric-updates/main Translation-en_US        
Ign http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Ign http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Ign http://us.archive.ubuntu.com oneiric-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US  
Ign http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Fetched 21.3 MB in 2min 2s (174 kB/s)                                          
Reading package lists... Done
```

It seems you have Natty sources in your system; not only that, but results for i386 and amd64 as well (32-bit and 64-bit). It's been a while since I used Ubuntu 64-bit, so I don't know if they should show up there in newer versions. Look for **software sources** in Dash and open the application; make sure there are no repositories from 11.04 enabled. Or from a terminal:

```
gksu gedit /etc/apt/sources.list
```

and you can comment out the entries for Natty there (adding a **#** at the beginning of the Natty lines). If you *do* make changes to the repositories, either through software-sources or gedit, update and upgrade again:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

If you don't find any Natty repositories on your system, you might want to try to fix the problem with:
```
sudo apt-get install -f
```

---

### Post by paul_in_london on 2011-09-22
> **bikewrecker said:**
> Ok well I'm not a big fan of the unity interface either, but like these other guys said. It doesn't look like gnome-shell is out yet or somthing.

```

daniel@daniel-EP45-UD3L:/etc/conky/conky-1.8.1$ sudo apt-get install gnome-shell[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libcogl2 (>= 1.7.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Gnome shell has been out for quite a while and I'm using it, but sometimes it's not installable or usable or upgradable for a while depending on what's happening with other packages etc. It's possible to enable other repositories (Personal Package Archives or PPAs) to get more bleeding-edge packages, but I'd advise you to stick with the main, offcial packages until you're more experienced.

---

### Post by cariboo on 2011-09-22
Everything is being rebuilt for the beta release, so I'd try not to install anything until after the official release.

As an aside, I updated a system yesterday that hadn't been updated for a couple of weeks, I had well over 400 updates waiting, this afternoon, I'm in the process of updating again, and this time there are over 150 updates. Things are certainly in in a state of flux at the moment.

---

### Post by bikewrecker on 2011-09-22
Allright guys, thanks for all your help! I think ill wait for the actual release like yall are saying. That sounds like the best plan to me.

---

### Post by Harry33 on 2011-09-23
> **jarpiw said:**
> FYI I've just tried to install gnome-tweak-tool and aptitude says there is a conflict between libcogl5 and libcogl2 and both are needed.

This is if you use Gnome-shell from Oneric repos only.

Gnome-tweak-tool does not need libcogl at all, but it needs Gnomo-shell. It is a tool for Gnome-shell, after all.
The working version of Gnome-shell depends on libcogl2 right now. But this is an old version.
The new Gnome-shell (3.1.92) depends on libcogl5, like all the other new related packages, like clutter and mutter. But it is not yet available.

Right now the newest available packages (from Oneirc repos) are kinda broken.
You can install clutter and mutter (with libcogl5), but then again you could only install old gnome-shell (depending on libcogl2).
So, you need to wait until new gnome-shell is around.

Or, if you know what you are doing, you can go to Ricotz Testing PPA, and install the complete, new Gnome-shell from there.

---

