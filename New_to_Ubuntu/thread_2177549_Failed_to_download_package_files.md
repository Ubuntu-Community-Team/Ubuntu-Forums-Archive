---
title: "Failed to download package files"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by bekirs on 2013-09-29
Hi all,

the automatic installation gives me the following output:

Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.7~beta2ubuntu9_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.7~beta2ubuntu9_amd64.deb) 404  Not Found [IP: 141.30.13.10 80]

What would you suggest?

---

### Post by heir4c on 2013-09-29
That page don't existed no more.
Have you updated your repo's?
Use this in terminal (or use the Update Manager):
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bekirs on 2013-10-03
here is the output:

```

sudo apt-get update && sudo apt-get upgrade
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://archive.canonical.com precise Release.gpg                           
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release                               
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://de.archive.ubuntu.com precise Release.gpg                           
Get:4 http://de.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:5 http://de.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Hit http://de.archive.ubuntu.com precise Release                               
Get:6 http://de.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://de.archive.ubuntu.com precise-proposed Release [49.6 kB]          
Get:9 http://linux.dropbox.com precise Release.gpg [489 B]                     
Get:10 http://security.ubuntu.com precise-security/main Sources [89.6 kB]      
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [1,804 B]
Ign http://tgcm.info precise Release.gpg                                       
Get:12 http://security.ubuntu.com precise-security/universe Sources [28.1 kB]  
Hit http://de.archive.ubuntu.com precise/restricted Sources                    
Hit http://de.archive.ubuntu.com precise/main Sources                          
Hit http://de.archive.ubuntu.com precise/multiverse Sources                    
Hit http://de.archive.ubuntu.com precise/universe Sources                      
Hit http://de.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://de.archive.ubuntu.com precise/restricted amd64 Packages             
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [324 kB]
Hit http://de.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://de.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://de.archive.ubuntu.com precise/main i386 Packages                    
Hit http://de.archive.ubuntu.com precise/restricted i386 Packages              
Ign http://tgcm.info precise Release                                           
Hit http://de.archive.ubuntu.com precise/universe i386 Packages                
Hit http://de.archive.ubuntu.com precise/multiverse i386 Packages              
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:14 http://linux.dropbox.com precise Release [2,603 B]                      
Ign http://archive.canonical.com precise/partner Translation-en                
Get:15 http://de.archive.ubuntu.com precise/main TranslationIndex [3,706 B]    
Hit http://de.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://de.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://de.archive.ubuntu.com precise/universe TranslationIndex             
Get:16 http://de.archive.ubuntu.com precise-updates/restricted Sources [7,006 B]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:17 http://de.archive.ubuntu.com precise-updates/main Sources [419 kB]      
Get:18 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:19 http://security.ubuntu.com precise-security/universe amd64 Packages [82.8 kB]
Ign http://tgcm.info precise/main TranslationIndex                             
Get:20 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,449 B]
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [343 kB] 
Get:22 http://linux.dropbox.com precise/main amd64 Packages [1,148 B]          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:23 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:24 http://security.ubuntu.com precise-security/universe i386 Packages [86.3 kB]
Get:25 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,640 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:26 http://linux.dropbox.com precise/main i386 Packages [1,148 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:27 http://de.archive.ubuntu.com precise-updates/multiverse Sources [8,343 B]
Get:28 http://de.archive.ubuntu.com precise-updates/universe Sources [96.2 kB] 
Get:29 http://de.archive.ubuntu.com precise-updates/restricted amd64 Packages [11.5 kB]
Get:30 http://de.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.9 kB]
Get:31 http://de.archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]
Get:32 http://de.archive.ubuntu.com precise-updates/universe i386 Packages [221 kB]
Err http://tgcm.info precise/main amd64 Packages                               
  404  Not Found
Err http://tgcm.info precise/main i386 Packages                                
  404  Not Found
Get:33 http://de.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.0 kB]
Hit http://de.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://de.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://de.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://de.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:34 http://de.archive.ubuntu.com precise-proposed/restricted amd64 Packages [14 B]
Get:35 http://de.archive.ubuntu.com precise-proposed/main amd64 Packages [92.9 kB]
Get:36 http://de.archive.ubuntu.com precise-proposed/multiverse amd64 Packages [1,442 B]
Get:37 http://de.archive.ubuntu.com precise-proposed/universe amd64 Packages [23.0 kB]
Get:38 http://de.archive.ubuntu.com precise-proposed/multiverse i386 Packages [1,449 B]
Get:39 http://de.archive.ubuntu.com precise-proposed/universe i386 Packages [26.3 kB]
Get:40 http://de.archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]
Get:41 http://de.archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]
Get:42 http://de.archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]
Ign http://tgcm.info precise/main Translation-en_US                            
Get:43 http://de.archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]
Hit http://de.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://de.archive.ubuntu.com precise/restricted Translation-en             
Hit http://de.archive.ubuntu.com precise/universe Translation-en               
Hit http://de.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://de.archive.ubuntu.com precise-updates/multiverse Translation-en     
Ign http://tgcm.info precise/main Translation-en                               
Hit http://de.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://de.archive.ubuntu.com precise-updates/universe Translation-en
Get:44 http://de.archive.ubuntu.com precise-proposed/main Translation-en [34.8 kB]
Hit http://de.archive.ubuntu.com precise-proposed/multiverse Translation-en    
Hit http://de.archive.ubuntu.com precise-proposed/restricted Translation-en
Err http://de.archive.ubuntu.com precise-updates/main amd64 Packages    
  406  Not Acceptable [IP: 141.30.13.10 80]
Err http://de.archive.ubuntu.com precise-updates/universe amd64 Packages
  406  Not Acceptable [IP: 141.30.13.10 80]
Err http://de.archive.ubuntu.com precise-updates/main i386 Packages     
  406  Not Acceptable [IP: 141.30.13.10 80]
Err http://de.archive.ubuntu.com precise-proposed/restricted i386 Packages
  406  Not Acceptable [IP: 141.30.13.10 80]
Err http://de.archive.ubuntu.com precise-proposed/main i386 Packages    
  406  Not Acceptable [IP: 141.30.13.10 80]
Ign http://de.archive.ubuntu.com precise-proposed/universe Translation-en
Ign http://linux.dropbox.com precise/main Translation-en_US            
Ign http://linux.dropbox.com precise/main Translation-en
Fetched 2,122 kB in 2s (815 kB/s)
W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/de.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index


W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages  406  Not Acceptable [IP: 141.30.13.10 80]


W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages  406  Not Acceptable [IP: 141.30.13.10 80]


W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  406  Not Acceptable [IP: 141.30.13.10 80]


W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages  406  Not Acceptable [IP: 141.30.13.10 80]


W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise-proposed/main/binary-i386/Packages  406  Not Acceptable [IP: 141.30.13.10 80]


W: Failed to fetch http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by heir4c on 2013-10-03
Change the server from where you update via "Software&Update"and try it again.

---

### Post by bekirs on 2013-10-03
Sorry but I don't know how to do that.

---

### Post by heir4c on 2013-10-03
Edit: Sorry it is Xubuntu, ThanX Elfy for let me know.


Via the "Dash" (UbuntuLogo in the left of the desktop) 
Type in the searchbar: Software and you will see the program 'Software & Updates' Click on it. (it take a wile for opening, so be patient)
Than on the first tab you see some button in the middle. (there something on like: http:// ....) Click on that and choose for the main server.
You can also choose the last option (I don't now what it is in English, here is in Dutch) and then the computer can search for the best server.
Than close the window and use the terminal again with the same command.

---

### Post by Elfy on 2013-10-03
> **heir4c said:**
> Via the "Dash" (UbuntuLogo in the left of the desktop) ...

Thread is tagged Xubuntu - there is no such thing as Dash in it.

@ bekirs

Software and Updates can be found in the Settings Manager from the menu. 

Then you can follow the rest of heir4c's post :)

---

### Post by heir4c on 2013-10-03
ThanX Elfy. I'll keep an eye on that the next time.

---

### Post by bekirs on 2013-10-03
> **heir4c said:**
> Edit: Sorry it is Xubuntu, ThanX Elfy for let me know.


Via the "Dash" (UbuntuLogo in the left of the desktop) 
Type in the searchbar: Software and you will see the program 'Software & Updates' Click on it. (it take a wile for opening, so be patient)
Than on the first tab you see some button in the middle. (there something on like: http:// ....) Click on that and choose for the main server.
You can also choose the last option (I don't now what it is in English, here is in Dutch) and then the computer can search for the best server.
Than close the window and use the terminal again with the same command.

There is no searchbat when I click on the "Dash" but there is Ubuntu Software Center. Is it the same?

---

### Post by bekirs on 2013-10-03
Edit:
... is no search bar when...

---

### Post by heir4c on 2013-10-03
No, there is no searchbar because you use Xubuntu but I thought you use Ubuntu. See the post of Elfy: [http://ubuntuforums.org/showthread.php?t=2177549&p=12806128#post12806128](http://ubuntuforums.org/showthread.php?t=2177549&p=12806128#post12806128)

(Sorry for my bad English)

---

### Post by bekirs on 2013-10-03
> **heir4c said:**
> No, there is no searchbar because you use Xubuntu but I thought you use Ubuntu. See the post of Elfy: [http://ubuntuforums.org/showthread.php?t=2177549&p=12806128#post12806128](http://ubuntuforums.org/showthread.php?t=2177549&p=12806128#post12806128)

(Sorry for my bad English)

Under Menu, there is Ubuntu Software Center...

alternative: Menu>System>Update Manager

I couldn't find anything called "Software&Updates"?

---

### Post by Elfy on 2013-10-03
> **Elfy said:**
> Thread is tagged Xubuntu - there is no such thing as Dash in it.

@ bekirs

Software and Updates can be found in the Settings Manager from the menu. 

Then you can follow the rest of heir4c's post :)

Please read replies people have made.

If you are not seeing Software and Updates in Setting Manager - what are you seeing? What version of Xubuntu are you using?

---

### Post by bekirs on 2013-10-03
> **Elfy said:**
> Please read replies people have made.

If you are not seeing Software and Updates in Setting Manager - what are you seeing? What version of Xubuntu are you using?

I am using: Ubuntu 12.04.3 LTS \n \l (this is what I get after I type ```
cat /etc/issue
```

after I select Menu>Settings>Settings Manager, I have followings:

Accessibility
Appearance
Calendar
Desktop
Display
File Manager
Keyboard
Mouse and Touchpad
Notifications
Panel
Power Manager
Preferred Applications
Removable Drives and Media
Screensaver
Session and Startup
Window Manager
Window Manager tweaks
Workspaces

---

### Post by Elfy on 2013-10-03
can't remember what 12.04 looks like :)

If it's not in Settings Manager then it should be an entry in Menu > System

have a look, in the meantime I'll boot a vm

---

### Post by Elfy on 2013-10-03
I do apologise - doesn't appear to be a menu item for it in the default 12.04 I just booted.

You can get to it via the Ubuntu software centre - settings.

But you can run it from a terminal, probably quicker

```
software-properties-gtk
```

once you've got it open - change the server in the first tab

---

### Post by bekirs on 2013-10-03
I have replaced "server from US2 with "Main server"

> **Elfy said:**
> I do apologise - doesn't appear to be a menu item for it in the default 12.04 I just booted.

You can get to it via the Ubuntu software centre - settings.

But you can run it from a terminal, probably quicker

```
software-properties-gtk
```

once you've got it open - change the server in the first tab

---

### Post by Elfy on 2013-10-03
Did an update deal with the problem? 

```
sudo apt-get update
```

---

### Post by bekirs on 2013-10-03
> **Elfy said:**
> Did an update deal with the problem? 

```
sudo apt-get update
```

here is the output: ```
sudo apt-get updateHit http://archive.canonical.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:3 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Get:4 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]           
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:5 http://archive.ubuntu.com precise Release [49.6 kB]                      
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en                
Get:6 http://linux.dropbox.com precise Release.gpg [489 B]                     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://tgcm.info precise Release.gpg                                       
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://tgcm.info precise Release                                           
Ign http://dl.google.com stable/main Translation-en                            
Get:7 http://linux.dropbox.com precise Release [2,603 B]                       
Ign http://tgcm.info precise/main TranslationIndex                             
Get:8 http://archive.ubuntu.com precise-updates Release [49.6 kB]        
Get:9 http://linux.dropbox.com precise/main amd64 Packages [1,148 B]           
Get:10 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Get:11 http://linux.dropbox.com precise/main i386 Packages [1,148 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:12 http://archive.ubuntu.com precise-proposed Release [49.6 kB]            
Get:13 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:14 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Err http://tgcm.info precise/main amd64 Packages                               
  404  Not Found
Err http://tgcm.info precise/main i386 Packages                               
  404  Not Found
Ign http://tgcm.info precise/main Translation-en_US                           
Ign http://tgcm.info precise/main Translation-en                              
Get:15 http://archive.ubuntu.com precise/multiverse Sources [155 kB]
Get:16 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:17 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get:18 http://archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:19 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]
Get:20 http://archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]    
Get:21 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:22 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:23 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:24 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:25 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:26 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B] 
Get:27 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B] 
Get:28 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]   
Get:29 http://archive.ubuntu.com precise-updates/restricted Sources [7,006 B]  
Get:30 http://archive.ubuntu.com precise-updates/main Sources [419 kB]         
Get:31 http://archive.ubuntu.com precise-updates/multiverse Sources [8,343 B]  
Get:32 http://archive.ubuntu.com precise-updates/universe Sources [96.2 kB]    
Get:33 http://archive.ubuntu.com precise-updates/main amd64 Packages [694 kB]  
Get:34 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [11.5 kB]
Get:35 http://archive.ubuntu.com precise-updates/universe amd64 Packages [217 kB]
Get:36 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.9 kB]
Get:37 http://archive.ubuntu.com precise-updates/main i386 Packages [715 kB]   
Get:38 http://archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]
Get:39 http://archive.ubuntu.com precise-updates/universe i386 Packages [221 kB]
Get:40 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14.0 kB]
Get:41 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:42 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:43 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:44 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:45 http://archive.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:46 http://archive.ubuntu.com precise-security/main Sources [89.6 kB]       
Get:47 http://archive.ubuntu.com precise-security/multiverse Sources [1,804 B] 
Get:48 http://archive.ubuntu.com precise-security/universe Sources [28.1 kB]   
Get:49 http://archive.ubuntu.com precise-security/main amd64 Packages [324 kB] 
Get:50 http://archive.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:51 http://archive.ubuntu.com precise-security/universe amd64 Packages [82.8 kB]
Get:52 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [2,449 B]
Get:53 http://archive.ubuntu.com precise-security/main i386 Packages [343 kB]  
Get:54 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:55 http://archive.ubuntu.com precise-security/universe i386 Packages [86.3 kB]
Get:56 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,640 B]
Get:57 http://archive.ubuntu.com precise-security/main TranslationIndex [74 B] 
Get:58 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:59 http://archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:60 http://archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:61 http://archive.ubuntu.com precise-proposed/restricted amd64 Packages [14 B]
Get:62 http://archive.ubuntu.com precise-proposed/main amd64 Packages [92.9 kB]
Get:63 http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages [1,442 B]
Get:64 http://archive.ubuntu.com precise-proposed/universe amd64 Packages [23.0 kB]
Get:65 http://archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]
Get:66 http://archive.ubuntu.com precise-proposed/main i386 Packages [106 kB]  
Get:67 http://archive.ubuntu.com precise-proposed/multiverse i386 Packages [1,449 B]
Get:68 http://archive.ubuntu.com precise-proposed/universe i386 Packages [26.3 kB]
Get:69 http://archive.ubuntu.com precise-proposed/main TranslationIndex [3,564 B]
Get:70 http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex [2,605 B]
Get:71 http://archive.ubuntu.com precise-proposed/restricted TranslationIndex [2,461 B]
Get:72 http://archive.ubuntu.com precise-proposed/universe TranslationIndex [2,850 B]
Get:73 http://archive.ubuntu.com precise/main Translation-en [726 kB]          
Get:74 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]   
Get:75 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]   
Get:76 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]
Get:77 http://archive.ubuntu.com precise-updates/main Translation-en [313 kB]  
Get:78 http://archive.ubuntu.com precise-updates/multiverse Translation-en [8,064 B]
Get:79 http://archive.ubuntu.com precise-updates/restricted Translation-en [2,637 B]
Get:80 http://archive.ubuntu.com precise-updates/universe Translation-en [127 kB]
Get:81 http://archive.ubuntu.com precise-security/main Translation-en [156 kB] 
Get:82 http://archive.ubuntu.com precise-security/multiverse Translation-en [1,299 B]
Get:83 http://archive.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:84 http://archive.ubuntu.com precise-security/universe Translation-en [52.6 kB]
Get:85 http://archive.ubuntu.com precise-proposed/main Translation-en [34.8 kB]
Get:86 http://archive.ubuntu.com precise-proposed/multiverse Translation-en [787 B]
Get:87 http://archive.ubuntu.com precise-proposed/restricted Translation-en [14 B]
Get:88 http://archive.ubuntu.com precise-proposed/universe Translation-en [14.5 kB]
Fetched 27.3 MB in 23s (1,173 kB/s)                                            
W: Failed to fetch http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by heir4c on 2013-10-03
The link below don't exist:
[http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-i386/Packages](http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-i386/Packages)
If you go to the directory above you will see there is no precise packages:
[http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/](http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/)
So, remove it from the Software sources.

---

### Post by bekirs on 2013-10-03
> **heir4c said:**
> The link below don't exist:
[http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-i386/Packages](http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/precise/main/binary-i386/Packages)
If you go to the directory above you will see there is no precise packages:
[http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/](http://tgcm.info/publicacion/repo_linux/tgcm8.8rc2/ubuntu/dists/)

it means all updates other than the ones related with those two work fine... did I understand correctly?

Is there anything I can do to remove these errors?

---

### Post by heir4c on 2013-10-03
Yes, the rest works fine, but there are some Ignored but I have the same here. That are the language packages, so don't worry about that.

Just remove the packagas sources from tgcm.info than you get no more errors when you update.
And don't just update but also upgrade.
'update' in the command is that you update the list of packages. 
'upgrade' in the commando is that you effective change the packages on your system.

---

