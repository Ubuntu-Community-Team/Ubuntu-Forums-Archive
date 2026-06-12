---
title: "Build essential keeps giving dependency issues"
date: 2017-06-03
forum: New to Ubuntu
---

### Post by dunique on 2017-06-03
I am running Ubuntu 14.04 on my virtualbox after installing flex and bison, I needed to install build-essential but I keep getting this error

Build-essential: Depends: g++(>=4:4.3.3)

I then did

sudo apt-get update 
Sudo apt-get install build-essential

Yet it's not installing. 

What do I do? 

Thanks

---

### Post by KillerKelvUK on 2017-06-03
Try a fix of your current package tree with

```

sudo apt-get install -f

```

if that drops in more packages then try installing build-essentials afterwards.

---

### Post by dunique on 2017-06-03
I have tried that but still didn't fix it.

---

### Post by mc4man on 2017-06-03
build-essential is just a meta (dependency) package so look at the dep that won't install, g++ (another meta package..
```
apt-cache policy g++
```
You could try to install g++ with apt-get to see why it's not installing, if not informative then install aptitude & try with it.

---

### Post by dunique on 2017-06-03
on typing apt-cache policy g++

i got error message: invalid operation policy

i tried installing g++ 

g++ : depends: g++-4.8 (>= 4.8.2-5~)

i also tried with aptitude.. still didn't fix it

---

### Post by howefield on 2017-06-03
> **dunique said:**
> on typing apt-cache policy g++ i got error message: invalid operation policy

Sure you didn't make a typo ?

Better to copy/paste the actual terminal input and output into your forum posts.

---

### Post by mc4man on 2017-06-03
Well then run
```
apt-cache policy g++-4.8
```
eventually you'll find what's blocking it though generally aptitude will tell you ("still didn't fix it" isn't very helpful here.

---

### Post by dunique on 2017-06-03
Thank you!

```
ayobami@ayobami-VirtualBox:~$ apt-cache policy g++
g++:
  Installed: (none)
  Candidate: 4:4.8.2-1ubuntu6
  Version table:
     4:4.8.2-1ubuntu6 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
ayobami@ayobami-VirtualBox:~$ 
```


I ran : apt-cache policy g++-4.8

I got this:

```
g++-4.8:
  Installed: (none)
  Candidate: 4.8.2-19ubuntu1
  Version table:
     4.8.2-19ubuntu1 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
```

---

### Post by mc4man on 2017-06-03
You should open up Software & Updates (software-properties-gtk from cli) & make sure both trusty-security & trusty-updates are enabled under the Updates tab.
Then reload your sources & see where you stand. The current package for g++-4.8 is as below - 
> $ apt-cache policy g++-4.8
g++-4.8:
  Installed: 4.8.4-2ubuntu1~14.04.3
  Candidate: 4.8.4-2ubuntu1~14.04.3
  Version table:
 *** 4.8.4-2ubuntu1~14.04.3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     4.8.2-19ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

---

### Post by dunique on 2017-06-03
Both trusty security and trusty updates are enabled

```
ayobami@ayobami-VirtualBox:~$ apt-cache policy g++-4.8
g++-4.8:
  Installed: (none)
  Candidate: 4.8.2-19ubuntu1
  Version table:
     4.8.2-19ubuntu1 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
ayobami@ayobami-VirtualBox:~$ 
```

still getting errors

---

### Post by deadflowr on 2017-06-03
> **dunique said:**
> Both trusty security and trusty updates are enabled

ayobami@ayobami-VirtualBox:~$ apt-cache policy g++-4.8
g++-4.8:
  Installed: (none)
  Candidate: 4.8.2-19ubuntu1
  Version table:
     4.8.2-19ubuntu1 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
ayobami@ayobami-VirtualBox:~$ 

still getting errors

Did you run the apt-cache policy command after you enabled the sec and update sources?
if so, you might need to reload the sources ala sudo apt-get update.
That will allow you to see what mc4man's post shows.

As it is, you're still showing only the main packages and nothing for the security or updates repos.

---

### Post by dunique on 2017-06-03
```
ayobami@ayobami-VirtualBox:~$ sudo aptitude why-not build-essential
p   flex:i386            Provides  flex                
p   flex:i386            Suggests  build-essential:i386
p   build-essential:i386 Conflicts build-essential     
ayobami@ayobami-VirtualBox:~$
```

> **deadflowr said:**
> Did you run the apt-cache policy command after you enabled the sec and update sources?
if so, you might need to reload the sources ala sudo apt-get update.
That will allow you to see what mc4man's post shows.

As it is, you're still showing only the main packages and nothing for the security or updates repos.


It wasn't disabled. i didnt make any changes.

```
ayobami@ayobami-VirtualBox:~$ sudo aptitude install build-essential
The following NEW packages will be installed:
  build-essential g++{a} g++-4.8{ab} libstdc++-4.8-dev{ab} 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,095 kB of archives. After unpacking 29.7 MB will be used.
The following packages have unmet dependencies:
 libstdc++-4.8-dev : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.3 is installed.
                     Depends: libgcc-4.8-dev (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.3 is installed.
 g++-4.8 : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.3 is installed.
           Depends: gcc-4.8 (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.3 is installed.
open: 37; closed: 109; defer: 14; conflict: 13                                                                                                .The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     build-essential [Not Installed]                    
2)     g++ [Not Installed]                                
3)     g++-4.8 [Not Installed]                            
4)     libstdc++-4.8-dev [Not Installed]                  



Accept this solution? [Y/n/q/?] 
```


Someone help.. i'm running out of options

---

### Post by steeldriver on 2017-06-03
The issue seems to be that you have installed 32-bit versions of flex and bison - doing so seems to have pulled in the 32-bit version of build-essential which conflicts with installing the 64-bit version

Perhaps it would be a good time to back up and tell us **how **you installed flex and bison?

---

### Post by dunique on 2017-06-03
I installed flex and bison using

sudo apt-get install flex bison

---

### Post by steeldriver on 2017-06-03
OK please show us 

```

cat /etc/lsb-release

dpkg --print-architecture

dpkg --print-foreign-architectures

apt-cache policy flex flex:i386 bison bison:i386

```

---

### Post by dunique on 2017-06-03
Here are they

```
ayobami@ayobami-VirtualBox:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
```

```
ayobami@ayobami-VirtualBox:~$ dpkg --print-architecture
amd64
```

```
ayobami@ayobami-VirtualBox:~$ dpkg --print-foreign-architectures
i386
```

```
ayobami@ayobami-VirtualBox:~$ apt-cache policy flex flex:i386 bison bison:i386
flex:
  Installed: 2.5.35-10.1ubuntu2
  Candidate: 2.5.35-10.1ubuntu2
  Version table:
     2.5.39-8~ubuntu14.04.1 0
        100 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty-backports/main amd64 Packages
 *** 2.5.35-10.1ubuntu2 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
flex:i386:
  Installed: (none)
  Candidate: 2.5.35-10.1ubuntu2
  Version table:
     2.5.39-8~ubuntu14.04.1 0
        100 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty-backports/main i386 Packages
     2.5.35-10.1ubuntu2 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
bison:
  Installed: 2:3.0.2.dfsg-2
  Candidate: 2:3.0.2.dfsg-2
  Version table:
 *** 2:3.0.2.dfsg-2 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
bison:i386:
  Installed: (none)
  Candidate: 2:3.0.2.dfsg-2
  Version table:
     2:3.0.2.dfsg-2 0
        500 [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
ayobami@ayobami-VirtualBox:~$
```

---

### Post by deadflowr on 2017-06-03
Please use code tags when posting the output from the terminal:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by steeldriver on 2017-06-03
OK I must be mistaken then - sorry bout that

---

### Post by dunique on 2017-06-03
How can I resolve the issue? 

Or a complete reinstall of the Ubuntu??

---

### Post by mc4man on 2017-06-03
open up Software & Updates > switch 'Download from:' to the Main server, reload the sources & try again.

---

### Post by dunique on 2017-06-04
> **mc4man said:**
> open up Software & Updates > switch 'Download from:' to the Main server, reload the sources & try again.

I changed update from to 'main server'.. However some couldnt download. I still have these

```
ayobami@ayobami-VirtualBox:~$ sudo apt-get install build-essential
[sudo] password for ayobami: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages
```

```

ayobami@ayobami-VirtualBox:~$ sudo apt-get update
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.ubuntu.com trusty InRelease                            
Hit http://extras.ubuntu.com trusty Release.gpg                             
Get:1 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]         
Hit http://extras.ubuntu.com trusty Release                                    
Get:2 http://extras.ubuntu.com trusty/main Sources [1,064 kB]
Get:3 http://archive.ubuntu.com trusty-backports InRelease [65.9 kB]
Get:4 http://extras.ubuntu.com trusty/main amd64 Packages [1,350 kB]           
Hit http://archive.ubuntu.com trusty-security InRelease                        
Get:5 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Get:6 http://archive.ubuntu.com trusty-updates/main Sources [399 kB]           
Get:7 http://archive.ubuntu.com trusty-updates/restricted Sources [6,331 B]    
Get:8 http://archive.ubuntu.com trusty-updates/universe Sources [179 kB]       
Get:9 http://extras.ubuntu.com trusty/main i386 Packages [1,348 kB]            
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources                
Get:10 http://archive.ubuntu.com trusty-updates/main amd64 Packages [984 kB]   
Get:11 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [17.1 kB]
Get:12 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [407 kB]
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages         
Get:13 http://archive.ubuntu.com trusty-updates/main i386 Packages [941 kB]    
Get:14 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [16.9 kB]
Get:15 http://archive.ubuntu.com trusty-updates/universe i386 Packages [408 kB]
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Get:16 http://archive.ubuntu.com trusty-updates/main Translation-en [486 kB]   
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Get:17 http://archive.ubuntu.com trusty-updates/universe Translation-en [216 kB]
Hit http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://archive.ubuntu.com trusty-backports/restricted Sources              
Hit http://archive.ubuntu.com trusty-backports/universe Sources      
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources       
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages  
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Get:18 http://archive.ubuntu.com trusty-security/main Sources [131 kB]         
Get:19 http://archive.ubuntu.com trusty-security/restricted Sources [4,955 B]  
Get:20 http://archive.ubuntu.com trusty-security/universe Sources [53.7 kB]    
Hit http://archive.ubuntu.com trusty-security/multiverse Sources               
Get:21 http://archive.ubuntu.com trusty-security/main amd64 Packages [618 kB]  
Get:22 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [14.0 kB]
Get:23 http://archive.ubuntu.com trusty-security/universe amd64 Packages [159 kB]
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages         
Get:24 http://archive.ubuntu.com trusty-security/universe i386 Packages [159 kB]
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages         
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Get:25 http://archive.ubuntu.com trusty-security/universe Translation-en [92.4 kB]
Get:26 http://archive.ubuntu.com trusty Release [58.5 kB]                      
Hit http://archive.ubuntu.com trusty-backports/main Sources                    
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages        
Hit http://archive.ubuntu.com trusty/main Sources                              
Get:27 http://archive.ubuntu.com trusty/restricted Sources [5,433 B]      
Hit http://archive.ubuntu.com trusty/universe Sources   
Hit http://archive.ubuntu.com trusty/multiverse Sources                  
Hit http://archive.ubuntu.com trusty/main amd64 Packages                 
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages           
Hit http://archive.ubuntu.com trusty/universe amd64 Packages             
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages           
Hit http://archive.ubuntu.com trusty/main i386 Packages                  
Hit http://archive.ubuntu.com trusty/restricted i386 Packages            
Hit http://archive.ubuntu.com trusty/universe i386 Packages              
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages            
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://archive.ubuntu.com trusty-backports/main Translation-en             
Err http://archive.ubuntu.com trusty-security/main i386 Packages               
  404  Not Found [IP: 91.189.88.161 80]
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 8,845 kB in 12min 45s (11.6 kB/s)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-amd64/Packages  Hash Sum mismatch

W:  Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages   404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/universe/i18n/Translation-en  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```


```
ayobami@ayobami-VirtualBox:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by mc4man on 2017-06-04
show
```
apt-cache policy g++:* gcc:* binutils:* libstdc++-4.8-dev:*
```

---

### Post by dunique on 2017-06-04
> **mc4man said:**
> show
```
apt-cache policy g++:* gcc:* binutils:* libstdc++-4.8-dev:*
```

```
ayobami@ayobami-VirtualBox:~$ apt-cache policy g++:* gcc:* binutils:* libstdc++-4.8-dev:*
g++:
  Installed: (none)
  Candidate: 4:4.8.2-1ubuntu6
  Version table:
     4:4.8.2-1ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
g++:i386:
  Installed: (none)
  Candidate: 4:4.8.2-1ubuntu6
  Version table:
     4:4.8.2-1ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
gcc:
  Installed: 4:4.8.2-1ubuntu6
  Candidate: 4:4.8.2-1ubuntu6
  Version table:
 *** 4:4.8.2-1ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
gcc:i386:
  Installed: (none)
  Candidate: 4:4.8.2-1ubuntu6
  Version table:
     4:4.8.2-1ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
binutils:
  Installed: 2.24-5ubuntu14.1
  Candidate: 2.24-5ubuntu14.1
  Version table:
 *** 2.24-5ubuntu14.1 0
        100 /var/lib/dpkg/status
     2.24-5ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
binutils:i386:
  Installed: (none)
  Candidate: 2.24-5ubuntu3
  Version table:
     2.24-5ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
libstdc++-4.8-dev:
  Installed: (none)
  Candidate: 4.8.2-19ubuntu1
  Version table:
     4.8.2-19ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libstdc++-4.8-dev:i386:
  Installed: (none)
  Candidate: 4.8.2-19ubuntu1
  Version table:
     4.8.2-19ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
ayobami@ayobami-VirtualBox:~$ 

```

---

### Post by mc4man on 2017-06-04
For whatever reason you're still not getting proper updates from security & updates.
Run this
```
apt-cache madison  libstdc++-4.8-dev:*
```

Ex. here, 
> $ apt-cache madison  libstdc++-4.8-dev:*
libstdc++-4.8-dev | 4.8.4-2ubuntu1~14.04.3 | [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
libstdc++-4.8-dev | 4.8.4-2ubuntu1~14.04.3 | [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
libstdc++-4.8-dev | 4.8.2-19ubuntu1 | [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
libstdc++-4.8-dev:i386 | 4.8.4-2ubuntu1~14.04.3 | [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
libstdc++-4.8-dev:i386 | 4.8.4-2ubuntu1~14.04.3 | [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages
libstdc++-4.8-dev:i386 | 4.8.2-19ubuntu1 | [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
Are you using a proxy or something?

---

### Post by dunique on 2017-06-04
> **mc4man said:**
> For whatever reason you're still not getting proper updates from security & updates.
Run this
```
apt-cache madison  libstdc++-4.8-dev:*
```

Ex. here, 

Are you using a proxy or something?

I am not using proxy. 

```
ayobami@ayobami-VirtualBox:~$ apt-cache madison libstdc++-4.8-dev:*
libstdc++-4.8-dev | 4.8.2-19ubuntu1 | http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libstdc++-4.8-dev:i386 | 4.8.2-19ubuntu1 | http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

```

Thanks all for the help.

I changed by browsing connection and then did a fresh update.

Build-essential has installed now.

---

