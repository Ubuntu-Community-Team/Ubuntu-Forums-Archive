---
title: "unable to install any software from terminal"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by giridhar2 on 2013-09-07
I tried to install youtrube-dl, clipgrab etc. These are the messages i keep getting. 

1. **Command typed:**
 
  sudo apt-add-repository ppa:clipgrab-team/ppa

[B]Messages:
[/B]
```
You are about to add the following PPA to your system:
 This PPA contains the latest stable version of ClipGrab
 More info: [https://launchpad.net/~clipgrab-team/+archive/ppa](https://launchpad.net/~clipgrab-team/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp1v7b_m/secring.gpg' created
gpg: keyring `/tmp/tmp1v7b_m/pubring.gpg' created
gpg: requesting key 8EEBB0CA from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp1v7b_m/trustdb.gpg: trustdb created
gpg: key 8EEBB0CA: public key "Launchpad ClipGrab PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```

2. Command typed: 

** sudo apt-get update**

**Messages:**

```
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring Release.gpg
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates Release.gpg                                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                                                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                         
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports Release.gpg                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                                                         
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security Release.gpg                                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                                       
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring Release                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                                                                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                      
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [489 B]                                                           
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates Release                                                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                                       
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports Release                                                               
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [2,603 B]                                                                              
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security Release                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                           
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/main Sources                                                                                         
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages [1,148 B]                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                           
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/restricted Sources                                                                    
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/universe Sources                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                            
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/multiverse Sources                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                           
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/main i386 Packages                                                                                   
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/restricted i386 Packages                                                                             
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/universe i386 Packages                                                                               
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/multiverse i386 Packages                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_IN                          
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/main Translation-en                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                             
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/multiverse Translation-en                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_IN                                                           
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/restricted Translation-en           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                                                              
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/universe Translation-en                                                             
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/main Sources                                          
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/restricted Sources
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                   
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/universe Sources                
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/multiverse Sources
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/main i386 Packages              
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/restricted i386 Packages        
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/universe i386 Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/multiverse i386 Packages
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/main Translation-en
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/multiverse Translation-en
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/restricted Translation-en
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/universe Translation-en
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/main Sources                                                                               
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/restricted Sources                                                                         
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/universe Sources                                                                           
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/multiverse Sources                                                                         
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/main i386 Packages                                                                         
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/restricted i386 Packages                                                                   
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/universe i386 Packages                                                                     
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/multiverse i386 Packages                                                                   
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/main Translation-en                                                                        
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/multiverse Translation-en                                                                  
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/restricted Translation-en                                                                  
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/universe Translation-en                                                                    
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/main Sources                                                                                
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/restricted Sources                                                                          
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/universe Sources                                                                            
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/multiverse Sources                                                                          
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/main i386 Packages                                                                          
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/restricted i386 Packages                                                                    
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/universe i386 Packages                                                                      
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/multiverse i386 Packages                                                                    
[B]Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                
  404  Not Found
[/B]Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/main Translation-en                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_IN                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                                                                               
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/multiverse Translation-en                                                                   
[B]Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages
  404  Not Found
[/B]Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_IN
Hit [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
[B]Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages
  404  Not Found
[/B]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_IN               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/main Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/multiverse Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/restricted Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring/universe Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/main Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/multiverse Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/restricted Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-updates/universe Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/main Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/multiverse Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/restricted Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-backports/universe Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/main Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/multiverse Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/restricted Translation-en_IN
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) raring-security/universe Translation-en_IN
Fetched 4,240 B in 23s (179 B/s)
[B]W: Failed to fetch [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/damnvid/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/damnvid/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

3. Command typed: 

 [/B] sudo apt-get install clipgrab

**Messages: **

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package clipgrab

Everytime i try installing any software from terminal, i get the same type of message. ( i have installed few softwares from the Ubuntu software center, but unable to install from terminal)

[B] Dear Members, I am a windows user who has shifted to Ubuntu 13.04 just few days ago. I do not know anything about .deb files, repositories etc - tried reading but did not understand anything of it. 

Please help me out with simple instructions - Thank you in advance !! 

Regards

[/B]System: Intel Core 2 Duo , 2GB RAM, Windows 7 PC.

---

### Post by grahammechanical on 2013-09-07
In Ubuntu software is stored in respositories (on computer servers). These are also known as Software Sources as they are the sources of software. Each version of Ubuntu has its own software repositories that are indentified by the code name that the version had while it was under development.

Have you noticed that the word "raring" appears in the list of software sources. That is because Ubuntu 13.04 is code named Raring Ringtail.

Now, here is something that you can do. Click the link in the message that says "You are about to add the following PPA to your system ... more info.

Here it is

[https://launchpad.net/~clipgrab-team/+archive/ppa](https://launchpad.net/~clipgrab-team/+archive/ppa)

Notice the line that says, "Technical Details about this PPA?" Click the arrow to the right of the line. The page will expand and you will see "Display sources list entries for" and alongside there is a drop down menu labeled "Choose your Ubuntu version." If you open the drop down menu you will notice that Raring is not in the list. The last version of Ubuntu listed is Quantal (12.10).

All this means that the developer of clipgrab has not provided a Raring repository for clickgrab. That is why you are getting the message "Unable to locate package clipgrab."

You cannot install this software in 13.04. Some will tell you that you can but as you say you do not know anything about all this stuff (and you say it quite loudly) I would not recommend messing with this stuff. There may be a reason why the developer has not provided a Raring repository for his software. May be the software does not work in Raring. May be clipgrab is no longer being developed. Who knows?

I suggest that you remove that PPA. The easy way to do it is to open System Settings>Software and Updates>Other Software tab and untick the PPA. You can even Remove the PPA from this page.

Regards.

---

### Post by giridhar2 on 2013-09-07
Thank you Graham !! That was such a wonderful reply. I did what you said. Tx a ton !! 

So, does that mean i can not download any youtube downloader for Raring Ringtail version of Ubuntu? 

Tx again !

Regards

---

### Post by buzzingrobot on 2013-09-07
Search for "youtube-dl Ubuntu 13.04".  It seems to be availabe in a PPA.

You saw those "404 Not Found" messages this time because the server didn't actually have the folder/file you targeted.  That's the same thing that happens when you try to load a nonexistent web page in a browser.   For future reference, you can also get 404's if a server is offline or too slow in responding.

---

### Post by ibjsb4 on 2013-09-07
You can also shorten the address to ../dists/ and see whats supported.  By leaving off "raring/main/binary-i386/Packages" in the address bar of your browser you will be able to see all supported versions.  Compare the two addresses.

 example:

[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages)

[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/)

---

### Post by giridhar2 on 2013-09-07
tx for your replies. I should confess that the reply of ibjsb4 could not be understood by me. ( i am not well versed with the way net works)..(By the way,The first link shows 404 error). Buzzingrobot, tx for your reply.

---

### Post by ibjsb4 on 2013-09-07
I did an edit on the above post.  Sorry about that, if I am still not doing a good job of explaining it, let me know.

---

### Post by giridhar2 on 2013-09-07
I got it ibjsb4 ! I got what you meant by shortening the address.. Sorry, it is my fault. I did not read properly. I am a bit dumb. 

 i am slightly desperate to get things working on Ubuntu. I am facing problems with my printer & the erratic internet connection. I have posted those problems as two threads - hope i get the answer. It is affecting me as i am tired of Windows 7...

---

### Post by oldos2er on 2013-09-08
Moved to Absolute Beginners.

---

