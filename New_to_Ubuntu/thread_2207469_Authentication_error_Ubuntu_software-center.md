---
title: "Authentication error Ubuntu software-center"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by robartist on 2014-02-23
Ubuntu software-center won't work. When I try to install something I get:

"Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.29'}): org.debian.apt.install-or-remove-packages"

Does anyone know of a solution please.

Many thanks

My spec: Acer c720, crouton, Ubuntu 13.10, unity

---

### Post by Vladlenin5000 on 2014-02-23
The error has been reported/discussed many times. Here's one result among many: [http://askubuntu.com/questions/207503/authentication-service-is-not-available-when-installing-idle-using-python-2-7](http://askubuntu.com/questions/207503/authentication-service-is-not-available-when-installing-idle-using-python-2-7)

I would start by doing ```
sudo dpkg --configure -a
``` just in case there are some incomplete/pending updates.

---

### Post by robartist on 2014-02-24
Many thanks Vladlenin5000. I tried your suggestion but it made no difference.

Do you, or anyone else, have any other suggestions.

Thanks again

Robert

---

### Post by oldos2er on 2014-02-24
Please run the following in a terminal (Ctrl-Alt-t) and copy and paste all the output here: ```
sudo apt-get update
```

---

### Post by robartist on 2014-02-25
oldos2er
Thanks. This is the result you asked for:
```
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release [49.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en                    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [72.3 kB]           
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [66.8 kB]       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [1,358 B]     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main amd64 Packages [204 kB]     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe amd64 Packages [153 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1,572 B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main i386 Packages [203 kB]     
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B] 
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe i386 Packages [154 kB] 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,763 B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en [95.6 kB]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en            
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources [31.1 kB]         
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources [14 B]      
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources [8,397 B]     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources [689 B]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main amd64 Packages [88.3 kB]  
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe amd64 Packages [32.3 kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse amd64 Packages [1,149 B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main i386 Packages [88.0 kB]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe i386 Packages [32.6 kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse i386 Packages [1,388 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en [48.7 kB]  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en_US
Fetched 1,386 kB in 40s (34.6 kB/s)
Reading package lists... Done
```

---

### Post by oldos2er on 2014-02-25
See [http://askubuntu.com/questions/218961/policykit-error-when-trying-to-install-remove-programs-in-the-software-center](http://askubuntu.com/questions/218961/policykit-error-when-trying-to-install-remove-programs-in-the-software-center) for potential solutions.

---

### Post by robartist on 2014-02-27
I am confused. You asked me to 'run the following...' then copy and paste into this post. But then you just point me to another thread rather than looking at what I had posted.

Was there nothing of note in my copy and paste??

---

### Post by Bashing-om on 2014-02-27
robartist; Hi !

Allow me to intercede.
The requested output was to insure there was not an underling problem with the package manager. Your "update" output is all good, Thus rather then repeating what has already been done, oldos2er points you to a probable known solution.

We are here to render aid and assistance
[INDENT][INDENT]in any event
[/INDENT][/INDENT]

---

### Post by oldos2er on 2014-02-27
> **robartist said:**
> I am confused. You asked me to 'run the following...' then copy and paste into this post. But then you just point me to another thread rather than looking at what I had posted.

Was there nothing of note in my copy and paste??

What Bashing-om said. I just wanted to make sure there were no errors shown from running *sudo apt-get update*

---

