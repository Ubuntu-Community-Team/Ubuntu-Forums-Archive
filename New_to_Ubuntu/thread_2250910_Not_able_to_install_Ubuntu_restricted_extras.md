---
title: "Not able to install Ubuntu restricted extras"
date: 2014-10-31
forum: New to Ubuntu
---

### Post by flex567 on 2014-10-31
I was unable to install Ubuntu restricted extras from the software center(picture below). Is there another way to install it?

---

### Post by kc1di on 2014-10-31
in a terminal try this

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by flex567 on 2014-10-31
```
Ign http://si.archive.ubuntu.com trusty InRelease
Ign http://si.archive.ubuntu.com trusty-updates InRelease                      
Ign http://si.archive.ubuntu.com trusty-backports InRelease                    
Hit http://si.archive.ubuntu.com trusty Release.gpg                            
Hit http://si.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://si.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://si.archive.ubuntu.com trusty Release                                
Hit http://si.archive.ubuntu.com trusty-updates Release                        
Hit http://si.archive.ubuntu.com trusty-backports Release                      
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease                         
Hit http://si.archive.ubuntu.com trusty/main Sources                  
Hit http://si.archive.ubuntu.com trusty/restricted Sources                     
Hit http://si.archive.ubuntu.com trusty/universe Sources                       
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://si.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://si.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://si.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://si.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://si.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://si.archive.ubuntu.com trusty/main Translation-en                    
Hit http://si.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://si.archive.ubuntu.com trusty/restricted Translation-en
Get:2 http://security.ubuntu.com trusty-security Release [59,7 kB]
Hit http://si.archive.ubuntu.com trusty/universe Translation-en                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://si.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://si.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://si.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://si.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://si.archive.ubuntu.com trusty-updates/main i386 Packages         
Hit http://si.archive.ubuntu.com trusty-updates/restricted i386 Packages   
Hit http://si.archive.ubuntu.com trusty-updates/universe i386 Packages     
Hit http://si.archive.ubuntu.com trusty-updates/multiverse i386 Packages   
Hit http://si.archive.ubuntu.com trusty-updates/main Translation-en        
Hit http://si.archive.ubuntu.com trusty-updates/multiverse Translation-en  
Hit http://si.archive.ubuntu.com trusty-updates/restricted Translation-en  
Hit http://si.archive.ubuntu.com trusty-updates/universe Translation-en    
Hit http://si.archive.ubuntu.com trusty-backports/main Sources             
Hit http://si.archive.ubuntu.com trusty-backports/restricted Sources       
Hit http://extras.ubuntu.com trusty/main Sources                           
Hit http://si.archive.ubuntu.com trusty-backports/universe Sources         
Hit http://si.archive.ubuntu.com trusty-backports/multiverse Sources       
Hit http://si.archive.ubuntu.com trusty-backports/main i386 Packages       
Hit http://si.archive.ubuntu.com trusty-backports/restricted i386 Packages 
Hit http://si.archive.ubuntu.com trusty-backports/universe i386 Packages   
Hit http://si.archive.ubuntu.com trusty-backports/multiverse i386 Packages 
Hit http://si.archive.ubuntu.com trusty-backports/main Translation-en      
Hit http://si.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://si.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://si.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://si.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://si.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://si.archive.ubuntu.com trusty/restricted Translation-en_US
Get:3 http://security.ubuntu.com trusty-security/main Sources [48,6 kB]
Ign http://si.archive.ubuntu.com trusty/universe Translation-en_US             
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [14 B]     
Get:5 http://security.ubuntu.com trusty-security/universe Sources [11,2 kB]    
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [698 B]    
Get:7 http://security.ubuntu.com trusty-security/main i386 Packages [145 kB]   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:8 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:9 http://security.ubuntu.com trusty-security/universe i386 Packages [50,3 kB]
Get:10 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1401 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en  
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Fetched 318 kB in 3s (105 kB/s)
Reading package lists... Done
seba@seba-H81-D3:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
seba@seba-H81-D3:~$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.8-jre-headless
 * openjdk-7-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
```

still don't have Java ?

---

### Post by Alireza_Zamani on 2014-10-31
> **flex567 said:**
> ```
Ign http://si.archive.ubuntu.com trusty InRelease
Ign http://si.archive.ubuntu.com trusty-updates InRelease                      
Ign http://si.archive.ubuntu.com trusty-backports InRelease                    
Hit http://si.archive.ubuntu.com trusty Release.gpg                            
Hit http://si.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://si.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://si.archive.ubuntu.com trusty Release                                
Hit http://si.archive.ubuntu.com trusty-updates Release                        
Hit http://si.archive.ubuntu.com trusty-backports Release                      
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease                         
Hit http://si.archive.ubuntu.com trusty/main Sources                  
Hit http://si.archive.ubuntu.com trusty/restricted Sources                     
Hit http://si.archive.ubuntu.com trusty/universe Sources                       
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://si.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://si.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://si.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://si.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://si.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://si.archive.ubuntu.com trusty/main Translation-en                    
Hit http://si.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://si.archive.ubuntu.com trusty/restricted Translation-en
Get:2 http://security.ubuntu.com trusty-security Release [59,7 kB]
Hit http://si.archive.ubuntu.com trusty/universe Translation-en                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://si.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://si.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://si.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://si.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://si.archive.ubuntu.com trusty-updates/main i386 Packages         
Hit http://si.archive.ubuntu.com trusty-updates/restricted i386 Packages   
Hit http://si.archive.ubuntu.com trusty-updates/universe i386 Packages     
Hit http://si.archive.ubuntu.com trusty-updates/multiverse i386 Packages   
Hit http://si.archive.ubuntu.com trusty-updates/main Translation-en        
Hit http://si.archive.ubuntu.com trusty-updates/multiverse Translation-en  
Hit http://si.archive.ubuntu.com trusty-updates/restricted Translation-en  
Hit http://si.archive.ubuntu.com trusty-updates/universe Translation-en    
Hit http://si.archive.ubuntu.com trusty-backports/main Sources             
Hit http://si.archive.ubuntu.com trusty-backports/restricted Sources       
Hit http://extras.ubuntu.com trusty/main Sources                           
Hit http://si.archive.ubuntu.com trusty-backports/universe Sources         
Hit http://si.archive.ubuntu.com trusty-backports/multiverse Sources       
Hit http://si.archive.ubuntu.com trusty-backports/main i386 Packages       
Hit http://si.archive.ubuntu.com trusty-backports/restricted i386 Packages 
Hit http://si.archive.ubuntu.com trusty-backports/universe i386 Packages   
Hit http://si.archive.ubuntu.com trusty-backports/multiverse i386 Packages 
Hit http://si.archive.ubuntu.com trusty-backports/main Translation-en      
Hit http://si.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://si.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://si.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://si.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://si.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://si.archive.ubuntu.com trusty/restricted Translation-en_US
Get:3 http://security.ubuntu.com trusty-security/main Sources [48,6 kB]
Ign http://si.archive.ubuntu.com trusty/universe Translation-en_US             
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [14 B]     
Get:5 http://security.ubuntu.com trusty-security/universe Sources [11,2 kB]    
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [698 B]    
Get:7 http://security.ubuntu.com trusty-security/main i386 Packages [145 kB]   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:8 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:9 http://security.ubuntu.com trusty-security/universe i386 Packages [50,3 kB]
Get:10 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1401 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en  
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Fetched 318 kB in 3s (105 kB/s)
Reading package lists... Done
seba@seba-H81-D3:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
seba@seba-H81-D3:~$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.8-jre-headless
 * openjdk-7-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
```

still don't have Java ?

it is not related to java,
you want Java ? for what ? which edition and version ?

---

### Post by QIII on 2014-10-31
Do you want OpenJDK, which is olen source, or Oracle Java, which is not?

The first is in the repo, the second is not.

---

### Post by kc1di on 2014-11-01
[Here is a page]("http://www.enqlu.com/2014/03/how-to-install-oracle-java-78-jdk-and-jre-in-ubuntu-14-04-13-10-12-10-12-04-and-10-04-via-ppa-or-linux-mint17.html") that tells you how to install Oracle java.  in Ubuntu.
 Or as mentioned above you can install the open source java solution from the repositories. 
If you want java for the web browser you'll need to install icedtea-7-plugin as well.

---

### Post by flex567 on 2014-11-01
```
it is not related to java,
``` It description of Ubuntu restricted extras is Java?

```
Do you want OpenJDK, which is olen source, or Oracle Java, which is not?
```
Which one is better for home non profesional use? 

where can I get OpenJDK ? 

I would need one to play some games in a browser?

---

### Post by slickymaster on 2014-11-01
> **flex567 said:**
> ```
Do you want OpenJDK, which is olen source, or Oracle Java, which is not?
```
Which one is better for home non profesional use? 

where can I get OpenJDK ? 

I would need one to play some games in a browser?

Being for a non professional use, I would go with OpenJDK. It's in the Ubuntu Software Center so all you have to do is to open the software center and enter the term 'OpenJDK' in the search box, in the top right. Once the search is performed just select it and hit 'Install'.

Please be aware that installing OpenJDK is not enough for enabling Java in browsers. You'll also need to install the icedtea-7-plugin package

---

### Post by flex567 on 2014-11-01
I decided to install java this way, Should i manually update it or will update automaticly ?

```
[B][I]sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer [/I][/B]
```

---

### Post by craig10x on 2014-11-01
@flex567: I have used that ppa before...that will update automatically...it will come in the software updater with your normal updates...

---

### Post by QIII on 2014-11-04
That's how I install it.

Andrew is very diligent in keeping the PPAs scripts up to date so that the latest Oracle Java will be downloaded from Oracle and installed.

The actual binaries are not maintained in the PPA, since Oracle no longer authorizes third parties to do that.  The PPA just scripts the download/install process.

---

