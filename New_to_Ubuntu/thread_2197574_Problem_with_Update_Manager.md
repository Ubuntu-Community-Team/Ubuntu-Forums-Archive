---
title: "Problem with Update Manager"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by gordon33 on 2014-01-04
Hello All

I have been having problems with my HP G60 lap top that runs Ubuntu 10.04.   

What can I do to search for the cause of the problem of the Update Manager?

I thought I could  update to Ubuntu 12.04 or 13.10 through Update Manager to work around all the problems. (see list of problems below.)  When I go to Systems, Administration, then Update Manager the Update Manager flashes on the screen for only a second or two.  Also, there is a red dot with a white horizontal line in the top panel.  When I move the cursor arrow over that red dot a message comes up “A problem occurred when checking for updates.”   

My search for help started with the problems with the Internet.  The first suggestion was to up date the Firefox and 10.04.  So I am wondering what to do to update the system with the following problems.

PROBLEMS 
Connection with Internet crashing. 
Problems accessing open office documents.
Unable to down load Ubuntu 12.04 from a flash drive.  Could not get the computer to boot up from a USB Flash stick.
Unable to make a start up disc from the other computers I have access to.

Gordon33

---

### Post by gordon33 on 2014-01-04
Another problem has been the 4 downloads of ubutu 12.04 and 13.10 keep showing up on my desk top screen.  I have moved them to trash and deleted trash at least 50 times they keep coming back.

---

### Post by Impavidus on 2014-01-04
I'd say clean install.

Check whether your computer can boot from usb. Enter the bios and see whether the option is available. Most computers can.

Burning a live dvd should be fairly straight-forward. Same for live usb. Do you get any errors? Have you checked the disks? Where do you get stuck?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by deadflowr on 2014-01-04
10.04 on the desktop has reached end of life.
Problems such as this are probably par for the course, and will most likely occur more often.
Post the output of this from a terminal
```
sudo apt-get update
```
and then this
```
sudo apt-get upgrade
```
click on no(n)
I feel like the answer will lie within one of those commands.

As far as zombie icons go, don't know can't help.

---

### Post by Bucky Ball on 2014-01-04
> **Impavidus said:**
> I'd say clean install.



^^
This. 

You could try deadflowr's suggstions, but not sure where that will get you.

Boot from an install disk, backup what you need to, then install 12.04 LTS or 13.10, both upgradeable to the next long-term support release 14.04 LTS in April.

As for making an install disk, you want to download the ISO and use either Win or Ubuntu software (Brasero) to 'burn image to disk'. Are you drag and dropping the ISO onto the disk? You need to burn the ISO image to it to make it bootable.

---

### Post by deadflowr on 2014-01-04
I'd also add, of the four iso's of 12.04 and 13.10, do you know if they were fully downloaded or not?
The 12.04 should be somewhere around 700MB and the 13.10 should be sufficiently more
(I forget but I think 13.10 is around 800MB or something) 
Might also want to run a[ checksum]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by gordon33 on 2014-01-04
Hello 

Thank you i will check these out after lunch.

---

### Post by monkeybrain20122 on 2014-01-04
If your computer supports booting from usb (most computers made in the last 10 years do)and you have a flash drive lying around make a live usb. Forget about the CD and fiddling with burning speed. The startup disk creator in your 10.04 should still work, if not get unetbootin.

---

### Post by Bucky Ball on 2014-01-04
> **monkeybrain20122 said:**
> If your computer supports booting from usb (most computers made in the last 10 years do)and you have a flash drive lying around make a live usb. Forget about the CD and fiddling with burning speed. The startup disk creator in your 10.04 should still work, if not get unetbootin.

OP states as a problem in the first post:

> Unable to down load Ubuntu 12.04 from a flash drive. Could not get the computer to boot up from a USB Flash stick.


... which is why I'm wondering if there's a problem with how the USB and/or disk are being created.

---

### Post by monkeybrain20122 on 2014-01-04
Oops missed that. Sorry.

To be able to boot from usb may require setting boot order in BIOS.

---

### Post by gordon33 on 2014-01-04
Hello All

I will reply to the responces in order the best I can.


Hello **Impavidus**

The boot options from Bios are:

CD-Rom Boot   Enabled
Floppy Boot  Enabled
Internal Network Adapter Boot  Disabled
Boot Order

Boot Order
USB Diskette on Key/USB Hard Disk
Internal CD/DVD ROM Drive
Notebook Hard Drive
   Network Adaprer

When I chose "USB Diskette on Key/USB Hard Disk"  It starts diffrent I get what looks simular to a battery and a small figuer at the bottom of the screen, then UBUNTU in the center of the screen,  Next the screen when black, after 10 minutes of the black screen I shut the computer down.  
The computer I have that stays connected to the internet does not have a disk drive I can write to a DVD on.



Hello deadflowr

One of the problems withthe HP is the internet crashes.  Would that be a problem for sudo apt-get update?  The results follow:

```
gordon@gordon-laptop:~$ sudo apt-get update 
[sudo] password for gordon: 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B] 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US 
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) lucid/main Translation-en_US 
Get:4 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [198B]         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty/partner Translation-en_US 
Get:5 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/universe Translation-en_US 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/multiverse Translation-en_US 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg [198B]           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg [198B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [58.3kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [535kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [732kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B] 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [240kB]          
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,347B]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [46.6kB]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [148kB]     
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]  
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [334kB]         
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,366B]  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,817B] 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [110kB] 
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [295kB] 
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Fetched 2,593kB in 3s (650kB/s) 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

E: Some index files failed to download, they have been ignored, or old ones used instead. 
gordon@gordon-laptop:~$ sudo apt-get upgrade 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
gordon@gordon-laptop:~$ 
```



Hello Bucky Ball 

I have been right clicking on the dowload and picking "write to disk" then burn.  The problem has been I can not make a DVD with the computers I have.  The recient start up DVD was made on the questionable computer.

Hello deadflowr
The Icons for the downloads that keep reappearing after being sent to tras/ deleated show nothing or error mesages.  The USB stick has about 1.7 GB of space used it is probably loaded with 12.04.  that USB only has the start up ubuntu on it. 

The DVD I burned (13.10) has 453 items totaling 881.8 MB.  

Results from checksum

```
gordon@gordon-laptop:~$ checksum 
No command 'checksum' found, did you mean: 
 Command 'checksub' from package 'ncbi-tools-bin' (universe) 
checksum: command not found 
gordon@gordon-laptop:~$ checksub 
The program 'checksub' is currently not installed.  You can install it by typing: 
sudo apt-get install ncbi-tools-bin 
gordon@gordon-laptop:~$ 
```

```
gordon@gordon-laptop:~$ sudo apt-get update 
[sudo] password for gordon: 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B] 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US 
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) lucid/main Translation-en_US 
Get:4 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [198B]         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty/partner Translation-en_US 
Get:5 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/universe Translation-en_US 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports/multiverse Translation-en_US 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg [198B]           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg [198B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [58.3kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [535kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [732kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B] 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [240kB]          
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,347B]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [46.6kB]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [148kB]     
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,630B] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]  
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [334kB]         
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,366B]  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,817B] 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [110kB] 
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [295kB] 
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources 
  404  Not Found [IP: 91.189.91.14 80] 
Fetched 2,593kB in 3s (650kB/s) 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80] 

E: Some index files failed to download, they have been ignored, or old ones used instead. 
gordon@gordon-laptop:~$ sudo apt-get upgrade 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
gordon@gordon-laptop:~$
```

---

### Post by deadflowr on 2014-01-04
It seems you would have several ways to go.
I believe in an earlier post, there was a link to getting the usb stick functional.
That would be by far the easiest route.

I also see that your sources.list is mixed-up with some old jaunty entries.
You would need to clear those out if you wanted to upgrade that way.
It's unclear about the connectivity of your network.
So the focus should be on the iso's and the usb stick.

And the checksum I mentioned was a link to Ubuntu's HowTo
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
I don't know if there's an actual "checksum" command, I used it in a generic sense.
Basically, though, you match the output of the hash to the one [here]("https://help.ubuntu.com/community/UbuntuHashes").
It will be exactly the same if right or something entirely different if wrong.

---

### Post by gordon33 on 2014-01-04
Hello Deadflowr

I will work on geting the USB stick to work.

Where is the "sources.list" that is mixed-up with some old jaunty entries?
How would I clear those out in order to upgrade that way?
Are they critical to get the start up USB to boot first?


I will be working on understanding whether to check the downolad of 13.10 on my good computer or the install 13.10 USB flash stick.

Gordon33

---

### Post by gordon33 on 2014-01-04
Hello All

I deleated every thing on my USB stick and then followed:  How to create a bootable USB stick on Ubuntu.....    [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
Pluged in the USB stick and started the Lap Top.  First try, Got through a few new boot up screens then it printed out a bunch of stuff on a black screen:

* Starting
* Stopping cold Plug Devices
* Stopping log inital device creation
* Starting enable remaining boot-time encrypted block devices
* Starting configure network device security
* Starting configure network device
* Starting save undev log update rules
* Stopping save undev log update rules

There was more but the computer shut down.  

Tried again, Each time I try to boot with the USB some thing chages, once I got a live version of 13.10.  I have another live version with an icon on the desk top that says "Install Ubuntu 13.10" .  When I click on that icon nothig happened.

I am thinking there is a problem with the download I used to creat the disk. It might just be a live version.

I will look in to a new down load.

Gordon33

---

### Post by deadflowr on 2014-01-04
> **gordon33 said:**
> Hello Deadflowr

I will work on geting the USB stick to work.

Where is the "sources.list" that is mixed-up with some old jaunty entries?
How would I clear those out in order to upgrade that way?
Are they critical to get the start up USB to boot first?


On the latter point, no the updates to the current system won't matter if you reinstall.
That will wipe the old sources.list out anyway.

On the first point, the sources.list is in the file /etc/apt/sources.list.
To edit you would open a terminal and run
```
gksu gedit /etc/apt/sources.list
```
the file would then be loaded.
You would then look for any line that have jaunty in them
Gedit has a decent search feature, should look like a magnifying glass.
You the search for text feature, which will highlight any words you try.
When you find the line(s) with jaunty, you would then add a # symbol to front of the line.
Or even easier, delete the line(s).
Then save the file and close it.
an example
```
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
```
and the commented out  line
```
**#**deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
```
But all this would be for naught, if going the usb reinstall route.
Which'll be easier when you figure out what's wrong the iso and usb stick.

---

### Post by Bucky Ball on 2014-01-04
Burn the ISO rather than 'Write to disk' is the way to go. Write to disk will not create a bootable image.

Just a note: Could you put code between code tags, please? [code] Compact, neater, easier to read that way. You can type them in manually or 'Go Advanced', mark out the code and click the # icon. Thanks.

(PS: I have done one for you as an example. ;))

---

