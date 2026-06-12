---
title: "Cannot unzip Nexus"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by alan19 on 2014-02-14
Hello all, this is my first posting so first I'd like to thank our admin for the upkeep of this forum. 

My problem began when I tried to find a repository manager for my newly installed ubuntu 12.04. I had many troubles finding a manager in the first place, but after hours of searching I found Nexus. It seemed legit to me, but I have only  been using Linux based OS since last week so what do I know? I downloaded the Linux x86 version of Java first, because some youtube video said it would help, then I downloaded the open Nexus package as a zip file.

I have been reading about Terminal and basic ubuntu user guides and I can make my way around this OS now. I was excited to see Minesweeper :P. I followed the basic intructions on how to unzip Nexus and begin using it, but I was stopped cold by an error message: 

$ sudo unzip nexus-2.7.1-01-bundle.zip
[sudo] password for alan: 
unzip:  cannot find or open nexus-2.7.1-01-bundle.zip, nexus-2.7.1-01-bundle.zip.zip or nexus-2.7.1-01-bundle.zip.ZIP.

The thing is, I had the window open for nexus-2.7.1-01-bundle.zip. I restarted my computer, it still didn't work. 

One other thing may help any expert that may chance upon my thread - when I typed in sudo apt-get update some of the updates failed so Terminal went with older versions. I'm not sure if this has anything to do with this problem, but there we go. 

Here is the youtube video I used: [http://www.youtube.com/watch?v=AwRFQdNtlI8](http://www.youtube.com/watch?v=AwRFQdNtlI8)

I can't find the other videos I was looking at. Can anyone help me unzip this package and get me rolling with Nexus? Or maybe I should delete it and go with a better repository manager?

---

### Post by Bucky Ball on 2014-02-14
Welcome. Repository manager? You are a developer? If not and if you just want to manage the installed repositories or add new ones, use 'Software Sources' or open update manager and click 'Settings' in the bottom left hand corner of the GUI.

You can also have a look at what you have in a terminal with:

nano /etc/apt/sources.list

To change that file, same command but start it with 'sudo'. Make a backup of the file first, though, in case your tweaks go pear-shaped.

---

### Post by saurav_kumar2 on 2014-02-14
1.Try to install 7z in your system from the software centre or follow the following command in the terminal:
       sudo apt-get install 7z
2. the for unzipping your file you just need to follow the following syntax:
      sudo 7z <path of your zip file>
# if problem presists please reply back....................
:):)

---

### Post by alan19 on 2014-02-14
I'm trying to piece together what might be a related problem so here is what's not working on my ubuntu thus far:

alan@ubuntu:~$ sudo 7z nexus-2.7.1-01-bundle.zip

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)


Error:
Incorrect command line

I did something wrong here. The problem is quite persistant! 

And to Bucky Ball, I'm not a developer, but I thought having a repository manager like adrepo would have been good, but nothing I could do would get that to work so I tried nexus after some searching. From what I understand, a lot of people use repositories in the linux world and having software to manage it seemed to me like a good idea. Maybe Nexus isn't right for me, but some ubuntu articles I read claimed that repository managers are a good idea for anyone using a repository.

I'm beginning to think something is missing - maybe a driver? I tried to install a game and it wouldn't start. Ubuntu had no application with which to open them. The two files that I thought would have worked are the .sdl and the .glx files. Nothing happened when I double-clicked.

Here are the details from the apt-get update:

```
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise Release.gpg
Get:1 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates Release.gpg [198 B]               
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise Release                                     
Get:2 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates Release [49.6 kB]                 
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/main Sources                                
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/restricted Sources                          
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/universe Sources                            
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/multiverse Sources                          
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/main amd64 Packages                         
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/restricted amd64 Packages                   
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/universe amd64 Packages                     
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/multiverse amd64 Packages                   
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/main i386 Packages                          
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/restricted i386 Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/universe i386 Packages                      
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/multiverse i386 Packages                    
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/main TranslationIndex                       
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/multiverse TranslationIndex                 
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/restricted TranslationIndex                 
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/universe TranslationIndex                   
Get:3 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/main Sources [451 kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Get:4 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/restricted Sources [8,028 B]      
Get:5 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/universe Sources [104 kB]         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner amd64 Packages                  
Get:6 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/multiverse Sources [8,482 B]      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Get:7 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/main amd64 Packages [746 kB]      
Err [http://build.discursive.com](http://build.discursive.com) lucid Release.gpg                              
  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)
Get:8 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/restricted amd64 Packages [12.2 kB]
Get:9 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/universe amd64 Packages [235 kB]  
Get:10 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/multiverse amd64 Packages [14.5 kB]
Get:11 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/main i386 Packages [770 kB]      
Ign [http://build.discursive.com](http://build.discursive.com) lucid Release                                  
Get:12 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/restricted i386 Packages [12.2 kB]
Get:13 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/universe i386 Packages [241 kB]  
Get:14 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/multiverse i386 Packages [14.7 kB]
Get:15 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/main TranslationIndex [3,564 B]  
Get:16 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/multiverse TranslationIndex [2,605 B]
Get:17 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/restricted TranslationIndex [2,461 B]
Get:18 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/main Translation-en                         
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/multiverse Translation-en                   
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/restricted Translation-en                   
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise/universe Translation-en                     
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/main Translation-en                 
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/multiverse Translation-en           
Hit [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/restricted Translation-en           
Get:19 [http://mirror.lstn.net](http://mirror.lstn.net) precise-updates/universe Translation-en [137 kB] 
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en                  
Ign [http://build.discursive.com](http://build.discursive.com) lucid/main TranslationIndex                    
Err [http://build.discursive.com](http://build.discursive.com) lucid/main Sources                             
  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)
Err [http://build.discursive.com](http://build.discursive.com) lucid/main amd64 Packages                      
  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)
Err [http://build.discursive.com](http://build.discursive.com) lucid/main i386 Packages
  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)
Err [http://build.discursive.com](http://build.discursive.com) lucid/main Translation-en_US
  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)
Err [http://build.discursive.com](http://build.discursive.com) lucid/main Translation-en                      
  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]         
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [97.5 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,791 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [358 kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [90.7 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,445 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [378 kB]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [94.9 kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,639 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Fetched 3,935 kB in 2min 5s (31.4 kB/s)
W: Failed to fetch [http://build.discursive.com/apt/dists/lucid/Release.gpg](http://build.discursive.com/apt/dists/lucid/Release.gpg)  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://build.discursive.com/apt/dists/lucid/main/source/Sources](http://build.discursive.com/apt/dists/lucid/main/source/Sources)  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://build.discursive.com/apt/dists/lucid/main/binary-amd64/Packages](http://build.discursive.com/apt/dists/lucid/main/binary-amd64/Packages)  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://build.discursive.com/apt/dists/lucid/main/binary-i386/Packages](http://build.discursive.com/apt/dists/lucid/main/binary-i386/Packages)  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://build.discursive.com/apt/dists/lucid/main/i18n/Translation-en_US](http://build.discursive.com/apt/dists/lucid/main/i18n/Translation-en_US)  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://build.discursive.com/apt/dists/lucid/main/i18n/Translation-en](http://build.discursive.com/apt/dists/lucid/main/i18n/Translation-en)  Something wicked happened resolving 'build.discursive.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used
```

I saw the word 'failed' too many times so I thought I'd ask about this too.
Thanks guys!

---

### Post by Impavidus on 2014-02-14
You were probably just in the wrong directory to unzip this file.

But ++ to Bucky Ball. If you're not developing software but just want to use the repositories (possibly add some, but be careful with that), which I think you are as a beginner, you can use the build-in tools.

Edit: Oops, we posted simultaniously. Hadn't seen your reply yet.

Edit 2: Yes, we use a lot of repositories in the Linux world, but most of us don't use any repository managers or related stuff other than the build-in tools. They should suffice and spare you the trouble of installing something manually and seeking help with something most of us don't use.

Your apt-get update output shows a strange mixture of sources from 10.04 and 12.04. As 10.04 is unsupported (except for the server version), this explains the error messages.

---

### Post by oldos2er on 2014-02-14
Which version of Ubuntu are you using? Also if you're working in your home folder, don't use 'sudo'.

---

### Post by grahammechanical on 2014-02-14
Is this what you are wanting to install?

[http://www.sonatype.org/nexus](http://www.sonatype.org/nexus)

As ordinary user we do not need anything like that. The Ubuntu developers provide repositories and manage them for us. When we install applications whether through the terminal or the Ubuntu Software Centre the application is downloaded from the Ubuntu repositories and installed for us. We also automatically get updates and security fixes. All of this is managed for us.

Regards.

---

### Post by alan19 on 2014-02-14
Ok, thank you everyone. It seems that Nexus would be over my head even if I got it so I'll let this unzipping thing go. However, I want to try to unzip a file I really want and see if I can get Terminal use 7zip to unzip the thing. Thank you to everyone for educating me on repositories, I guess all the reading I did wasn't enough to fully grasp the concept.

Impavidus - is there anything I should do about having 10.04 stuff in my upgrade? 

Oldos2er - I have 12.04 LTS. I suppose most things don't need 'sudo'?

Thanks again!

---

### Post by Bucky Ball on 2014-02-14
If you are running 12.04 you should go to Software Sources (or Update Manager and 'Settings' in the bottom left corner) and untick or remove any PPA that says 'lucid' in the name. You are 12.04, that is Precise. You are going to stumble on the lucid repos as they are   no longer in operation. As mentioned, unless you are running the server version, 10.04 (Lucid) is unsupported.

---

### Post by steeldriver on 2014-02-15
You shouldn't need 7z for .zip files (use unzip), but just for the record, 7z needs a **function letter** to tell it what operation you want to do e.g. to e**x**tract an archive

```
7z **x** *file.7z*
```

See man 7z

```

FUNCTION LETTERS
       a      Add

       d      Delete

       e      Extract

       l      List

       t      Test

       u      Update

       x      eXtract with full paths

```

---

### Post by oldos2er on 2014-02-15
> **alan19 said:**
> Oldos2er - I have 12.04 LTS. I suppose most things don't need 'sudo'?

Ubuntu version doesn't really matter in regards to use of sudo. If you're working inside your home folder (i.e. /home/user/) sudo is not necessary because your user has full read/write permissions there. Any part of the file system outside of your home folder will require admin (or root) permissions, so that's when you'd need sudo. Basically you do not want to use sudo unless you're sure it's required. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by alan19 on 2014-02-16
Thanks Bucky Ball. Looks like everything under my "other sources" tab is from lucid so I unchecked everything. I'll focus on customizing my desktop for now and getting to know the programs that are already on here. I got gnome and I really like the interface now.

---

### Post by alan19 on 2014-02-16
Noted, thanks steeldriver

---

