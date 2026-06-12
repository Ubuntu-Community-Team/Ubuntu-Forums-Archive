---
title: "Package-Manager error?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by angelsneverdie on 2008-09-10
So when I boot my desktop it loads with a red circle  ith a line in it in the upper right hand area.  when i put the mouse over it i get this message:

An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'error: opening the cache (E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.)'This usally means that your installed packages have unmet dependencies

If i open a terminal and type "sudo apt-get install Package-Manager"  i get the same as above (well, the part that is in the paranthases)
 

I don't know if it is related or not, but every thirty or so times i restart it does its normal hard drive check thing and every time it goes to a terminal screen and wants me to run fsck manually.  i do, and answer yes to all the weird inode errors and other things and then it boots.  This last time, after it started giving me this package manager thing i restarted and it wouldn't even boot, saying something about gdm and x (sorry, i didn't write it down) until i did a manual fsck and said yes to everything


anyone have any idea what is going on?   i just want it to work . . . im running hardy btw.

---

### Post by akiratheoni on 2008-09-10
What do you get when you go to Applications -> Accessories -> Terminal and type in:

```
sudo apt-get update
```

Post the output here.

---

### Post by angelsneverdie on 2008-09-10
this is what i get for sudo apt-get update:

[INDENT]Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [311kB]         
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6636B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [88.4kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [908B]     
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [90.8kB]    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [22.7kB]     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [20.1kB]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [2795B]   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [57.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [29.6kB]    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [4919B]      
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [8222B]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]      
Fetched 653kB in 6s (93.4kB/s)                                                 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
[/INDENT][/INDENT]

---

### Post by iaculallad on 2008-09-10
In your terminal, solve your problem with:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by Malac on 2008-09-10
It takes a while but you could try ```
sudo dpkg-reconfigure -a
```

---

### Post by jemate18 on 2008-09-10
try```
sudo dpkg --configure -a 
```

---

### Post by angelsneverdie on 2008-09-10
> **iaculallad said:**
> In your terminal, solve your problem with:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

seems to have done the trick.

Thanks everyone for your help!

i'll monitor the problem and see if it crops back up. . . 

Does anyone know what may have caused this so I can avoid it in the future?

---

### Post by iaculallad on 2008-09-10
That problem may probably been caused by a disrupted update.

---

