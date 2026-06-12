---
title: "New to Ubuntu and having some troubles"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by anthony53 on 2015-01-24
This computer was gifted to me awhile back and is currently running Linux Mint 15, unfortunately the guy passed away without telling me the password, after finally bypassing that i tried giving the computer an update, but whenever I use "sudo apt-get update" I keep getting these errors


```
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                         
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia Release.gpg [198 B]                 
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia Release [18.5 kB]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages/DiffIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages/DiffIndex
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main Sources [21.2 kB]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages/DiffIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner Sources                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages/DiffIndex
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream Sources [4,862 B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages/DiffIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner amd64 Packages                 
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import Sources [485 B]              
Get:6 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main amd64 Packages [23.5 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring Release.gpg                                     
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream amd64 Packages [9,249 B]   
Get:8 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import amd64 Packages [39.2 kB]     
Get:9 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main i386 Packages [23.5 kB]        
Get:10 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream i386 Packages [9,237 B]   
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates Release.gpg                             
Get:11 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import i386 Packages [40.1 kB]     
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US              
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring Release                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en        
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates Release                                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources           
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources     
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources
  404  Not Found [IP: 91.189.91.23 80]
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import Translation-en                 
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US          
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main Translation-en                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.23 80]
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/main Sources                                    
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/restricted Sources
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/universe Sources
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/multiverse Sources
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/main amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/restricted amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/universe amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/multiverse amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/main i386 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/restricted i386 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/universe i386 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/multiverse i386 Packages
  404  Not Found
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/main Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/main Translation-en
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/multiverse Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/multiverse Translation-en
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/restricted Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/restricted Translation-en
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/universe Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring/universe Translation-en
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/main Sources
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/restricted Sources
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/universe Sources
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/multiverse Sources
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/main amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/restricted amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/universe amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/multiverse amd64 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/main i386 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/restricted i386 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/universe i386 Packages
  404  Not Found
Err [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/multiverse i386 Packages
  404  Not Found
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/main Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/main Translation-en
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/multiverse Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/multiverse Translation-en
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/restricted Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/restricted Translation-en
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/universe Translation-en_US
Ign [http://ftp.wa.co.za](http://ftp.wa.co.za) raring-updates/universe Translation-en
Fetched 190 kB in 1min 45s (1,803 B/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/main/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/restricted/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/universe/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/multiverse/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/main/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/universe/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/multiverse/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/main/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/restricted/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/universe/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/main/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/restricted/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/universe/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/multiverse/source/Sources](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/main/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/universe/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/universe/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages](http://ftp.wa.co.za/pub/ubuntu/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Ive tried changing the repositories ie; [Http://packages.linuxmint.com](Http://packages.linuxmint.com) etc.. but that doesnt seem to help either. Is there any other way to fix this, Thanks in Advance

---

### Post by sammiev on 2015-01-24
Raring is from 13.04 which has reached end of life and I see you also have some 14.04 in there as well ( That's a mess you got there ). You are better off to download the 14.04 ISO and start fresh.

---

### Post by Bucky Ball on 2015-01-25
Welcome. Just a note: Linux Mint is not supported in the main support areas here. There is a sub-forum for Mint here, but there is also a vibrant and active Mint community which has its own forum. Do a search for Mint forum and you will find it.

Having said that, as mentioned, you do have a mess, and without a password, that is a brick wall. Running an unsupported release doesn't help. You would be better downloading the [Ubuntu 14.04 LTS ISO]("http://www.ubuntu.com/download/desktop") (with five years support til April 2019) and installing that. Good luck. ;) 

PS: Please use [code] tags for your terminal output. Neater, easier to read and space-saving. See the last link in my signature for how. I have added them to your first post.

---

