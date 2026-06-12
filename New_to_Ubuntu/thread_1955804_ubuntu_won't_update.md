---
title: "ubuntu won't update"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by JoeyB88 on 2012-04-10
Hello everyone, I'll post my problem, then a bit about me (as I want to learn, but have next to ZERO knowledge about ubuntu / linux). 

PROBLEM: ubuntu won't update. 

Whenever synaptic tries to update, it says there's an issue of somesort with my "br scan" package. I've gone into synaptic and found it, and it is permanently marked for removal. But when I try to remove it, the error "E: brscan: subprocess installed post-removal script returned error exit status 1"

Because of this, no new software can be installed!

I have no idea what this means; I've tried to find solutions to this on the internet, but have really struggled to understand what anyone's talking about. A lot of forum posters presume a lot of knowledge, which I don't have. However, I'm willing to learn, and I want to learn.

Please help me with my problem. 
Please tell me where I can go to learn about ubuntu.

Thank you!!

Joe Burrows

---

### Post by plucky on 2012-04-10
> **JoeyB88 said:**
> Hello everyone, I'll post my problem, then a bit about me (as I want to learn, but have next to ZERO knowledge about ubuntu / linux). 

PROBLEM: ubuntu won't update. 

Whenever synaptic tries to update, it says there's an issue of somesort with my "br scan" package. I've gone into synaptic and found it, and it is permanently marked for removal. But when I try to remove it, the error "E: brscan: subprocess installed post-removal script returned error exit status 1"

Because of this, no new software can be installed!

I have no idea what this means; I've tried to find solutions to this on the internet, but have really struggled to understand what anyone's talking about. A lot of forum posters presume a lot of knowledge, which I don't have. However, I'm willing to learn, and I want to learn.

Please help me with my problem. 
Please tell me where I can go to learn about ubuntu.

Thank you!!

Joe Burrows

Did you try to install the scanner driver for your Brother Printer?

What is the model of the printer?

Open a terminal and post the output for this command ```
sudo apt-get update
```

---

### Post by oklokl on 2012-04-10
Please replace the server.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by JoeyB88 on 2012-04-10
Thanks for the quick reply. Here's what happened:

joe@joe-1005HA:~$ sudo apt-get update
[sudo] password for joe: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [39.8 kB]              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg       
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg [198 B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release           
Get:5 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]              
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release [39.8 kB]             
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [93.8 kB]         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex
Get:8 [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages [7,285 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex               
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources [157 kB]         
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [22.6 kB]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [1,640 B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [283 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources [753 B]   
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources [42.6 kB]   
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources [3,116 B] 
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages [440 kB]  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [78.7 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [3,540 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_GB               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages [141 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages [6,364 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 1,368 kB in 2s (540 kB/s)                
Reading package lists... Done

---

### Post by JoeyB88 on 2012-04-10
Did I install the drivers? - yes, but it was complicated.

The make is:

Brother DCP-195C

---

### Post by plucky on 2012-04-10
> **JoeyB88 said:**
> Did I install the drivers? - yes, but it was complicated.

The make is:

Brother DCP-195C

You need to install the brscan3 driver for your printer.

See [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) 

Can you post the output for ```
sudo apt-get upgrade
```

---

### Post by JoeyB88 on 2012-04-10
I just tried to install the bruscan3, with the deb filetype.

I got this error:


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the brscan package. This might mean you need to manually fix this package.

---

### Post by plucky on 2012-04-10
> **JoeyB88 said:**
> I just tried to install the bruscan3, with the deb filetype.

I got this error:


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the brscan package. This might mean you need to manually fix this package.

Which one did you use 32-bit or AMD64?

Post output for ```
lsb_release -a
```

---

### Post by JoeyB88 on 2012-04-10
I just tried to install the bruscan3, with the deb filetype.

I got this error:


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the brscan package. This might mean you need to manually fix this package.

When I ran the other script, I got this:

Get:34 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe chromium-browser i386 18.0.1025.142~r129054-0ubuntu0.11.04.1 [20.0 MB]
Get:35 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe chromium-browser-inspector all 18.0.1025.142~r129054-0ubuntu0.11.04.1 [120 kB]
Get:36 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libjasper1 i386 1.900.1-7ubuntu2.11.04.1 [141 kB]
Get:37 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-declarative i386 4:4.7.2-0ubuntu6.3 [954 kB]
Get:38 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-script i386 4:4.7.2-0ubuntu6.3 [829 kB]
Get:39 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-xmlpatterns i386 4:4.7.2-0ubuntu6.3 [1,071 kB]
Get:40 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-network i386 4:4.7.2-0ubuntu6.3 [469 kB]
Get:41 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-dbus i386 4:4.7.2-0ubuntu6.3 [193 kB]
Get:42 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-xml i386 4:4.7.2-0ubuntu6.3 [93.7 kB]
Get:43 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libgl1-mesa-dri i386 7.10.2-0ubuntu2.1 [2,506 kB]
Get:44 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libgl1-mesa-glx i386 7.10.2-0ubuntu2.1 [93.7 kB]
Get:45 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-svg i386 4:4.7.2-0ubuntu6.3 [138 kB]
Get:46 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libtiff4 i386 3.9.4-5ubuntu6.1 [131 kB]
Get:47 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-opengl i386 4:4.7.2-0ubuntu6.3 [286 kB]
Get:48 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqtgui4 i386 4:4.7.2-0ubuntu6.3 [3,994 kB]
Get:49 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main mysql-common all 5.1.61-0ubuntu0.11.04.1 [12.3 kB]
Get:50 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libmysqlclient16 i386 5.1.61-0ubuntu0.11.04.1 [1,809 kB]
Get:51 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-sql-sqlite i386 4:4.7.2-0ubuntu6.3 [24.7 kB]
Get:52 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-sql-mysql i386 4:4.7.2-0ubuntu6.3 [31.7 kB]
Get:53 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqt4-sql i386 4:4.7.2-0ubuntu6.3 [98.7 kB]
Get:54 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libqtcore4 i386 4:4.7.2-0ubuntu6.3 [1,827 kB]
Get:55 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main kdelibs5-plugins i386 4:4.6.5-0ubuntu1.1 [890 kB]
Get:56 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkhtml5 i386 4:4.6.5-0ubuntu1.1 [1,881 kB]
Get:57 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkatepartinterfaces4 i386 4:4.6.5-0ubuntu1.1 [684 kB]
Get:58 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libktexteditor4 i386 4:4.6.5-0ubuntu1.1 [83.7 kB]
Get:59 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkmediaplayer4 i386 4:4.6.5-0ubuntu1.1 [37.8 kB]
Get:60 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libplasma3 i386 4:4.6.5-0ubuntu1.1 [818 kB]
Get:61 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkdewebkit5 i386 4:4.6.5-0ubuntu1.1 [59.3 kB]
Get:62 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkparts4 i386 4:4.6.5-0ubuntu1.1 [106 kB]
Get:63 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libknotifyconfig4 i386 4:4.6.5-0ubuntu1.1 [39.8 kB]
Get:64 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libknewstuff3-4 i386 4:4.6.5-0ubuntu1.1 [150 kB]
Get:65 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkfile4 i386 4:4.6.5-0ubuntu1.1 [208 kB]
Get:66 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkemoticons4 i386 4:4.6.5-0ubuntu1.1 [40.9 kB]
Get:67 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main kdoctools i386 4:4.6.5-0ubuntu1.1 [172 kB]
Get:68 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkio5 i386 4:4.6.5-0ubuntu1.1 [762 kB]
Get:69 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libnepomukutils4 i386 4:4.6.5-0ubuntu1.1 [81.4 kB]
Get:70 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libnepomukquery4a i386 4:4.6.5-0ubuntu1.1 [102 kB]
Get:71 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libsolid4 i386 4:4.6.5-0ubuntu1.1 [216 kB]
Get:72 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libxml2 i386 2.7.8.dfsg-2ubuntu0.3 [608 kB]
Get:73 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libnepomuk4 i386 4:4.6.5-0ubuntu1.1 [192 kB]
Get:74 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main kdelibs-bin i386 4:4.6.5-0ubuntu1.1 [186 kB]
Get:75 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkjsembed4 i386 4:4.6.5-0ubuntu1.1 [295 kB]
Get:76 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkjsapi4 i386 4:4.6.5-0ubuntu1.1 [221 kB]
Get:77 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libxml2-utils i386 2.7.8.dfsg-2ubuntu0.3 [78.3 kB]
Get:78 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkrosscore4 i386 4:4.6.5-0ubuntu1.1 [55.9 kB]
Get:79 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkidletime4 i386 4:4.6.5-0ubuntu1.1 [37.1 kB]
Get:80 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkdnssd4 i386 4:4.6.5-0ubuntu1.1 [63.0 kB]
Get:81 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkcmutils4 i386 4:4.6.5-0ubuntu1.1 [89.0 kB]
Get:82 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkdeui5 i386 4:4.6.5-0ubuntu1.1 [1,184 kB]
Get:83 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkntlm4 i386 4:4.6.5-0ubuntu1.1 [29.4 kB]
Get:84 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkdesu5 i386 4:4.6.5-0ubuntu1.1 [52.1 kB]
Get:85 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkpty4 i386 4:4.6.5-0ubuntu1.1 [33.3 kB]
Get:86 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkdecore5 i386 4:4.6.5-0ubuntu1.1 [839 kB]
Get:87 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libthreadweaver4 i386 4:4.6.5-0ubuntu1.1 [49.3 kB]
Get:88 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main kdelibs5-data all 4:4.6.5-0ubuntu1.1 [2,195 kB]
Get:89 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main language-pack-en all 1:11.04+20111206 [93.0 kB]
Get:90 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main language-pack-en-base all 1:11.04+20110719 [745 kB]
Get:91 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main language-pack-gnome-en all 1:11.04+20111206 [131 kB]
Get:92 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main language-pack-gnome-en-base all 1:11.04+20110719 [1,731 kB]
Get:93 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main linux-image-2.6.38-11-generic i386 2.6.38-11.50 [35.8 MB]
Get:94 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main nvidia-common i386 0.2.30.1 [11.2 kB]
Get:95 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ure i386 1.7.0+LibO3.3.4-0ubuntu1 [1,187 kB]
Get:96 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main uno-libs3 i386 1.7.0+LibO3.3.4-0ubuntu1 [1,111 kB]
Get:97 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main apt i386 0.8.13.2ubuntu4.4 [2,103 kB]
Get:98 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libpam-runtime all 1.1.2-2ubuntu8.4 [41.8 kB]
Get:99 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main multiarch-support i386 2.13-0ubuntu13.1 [7,850 B]
Get:100 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main apt-utils i386 0.8.13.2ubuntu4.4 [223 kB]
Get:101 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main isc-dhcp-client i386 4.1.1-P1-15ubuntu9.3 [265 kB]
Get:102 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main isc-dhcp-common i386 4.1.1-P1-15ubuntu9.3 [319 kB]
Get:103 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main sysvinit-utils i386 2.87dsf-4ubuntu23.1 [50.8 kB]
Get:104 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main sysv-rc all 2.87dsf-4ubuntu23.1 [36.4 kB]
Get:105 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main initscripts i386 2.87dsf-4ubuntu23.1 [32.2 kB]
Get:106 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main rsyslog i386 4.6.4-2ubuntu4.2 [214 kB]
Get:107 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main bind9-host i386 1:9.7.3.dfsg-1ubuntu2.3 [53.0 kB]
Get:108 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main dnsutils i386 1:9.7.3.dfsg-1ubuntu2.3 [137 kB]
Get:109 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libisc62 i386 1:9.7.3.dfsg-1ubuntu2.3 [143 kB]
Get:110 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libdns69 i386 1:9.7.3.dfsg-1ubuntu2.3 [634 kB]
Get:111 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libisccc60 i386 1:9.7.3.dfsg-1ubuntu2.3 [17.5 kB]
Get:112 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libisccfg62 i386 1:9.7.3.dfsg-1ubuntu2.3 [36.4 kB]
Get:113 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main liblwres60 i386 1:9.7.3.dfsg-1ubuntu2.3 [35.7 kB]
Get:114 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libbind9-60 i386 1:9.7.3.dfsg-1ubuntu2.3 [24.8 kB]
Get:115 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libldap-2.4-2 i386 2.4.23-6ubuntu6.1 [160 kB]
Get:116 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main acpid i386 1:2.0.7-1ubuntu2.4 [33.6 kB]
Get:117 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main app-install-data-partner all 12.11.04.4 [47.6 kB]
Get:118 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-problem-report all 1.20.1-0ubuntu5.1 [31.5 kB]
Get:119 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-launchpadlib all 1.9.7-0ubuntu2.1 [43.6 kB]
Get:120 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-apport all 1.20.1-0ubuntu5.1 [107 kB]
Get:121 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main apport all 1.20.1-0ubuntu5.1 [59.1 kB]
Get:122 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main apport-gtk all 1.20.1-0ubuntu5.1 [27.6 kB]
Get:123 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libcurl3-gnutls i386 7.21.3-1ubuntu1.5 [212 kB]
Get:124 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main apt-transport-https i386 0.8.13.2ubuntu4.4 [19.1 kB]
Get:125 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main byobu all 3.33-0ubuntu1.1 [62.6 kB]
Get:126 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main icedtea-6-jre-cacao i386 6b22-1.10.6-0ubuntu1 [415 kB]
Get:127 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main icedtea-6-jre-jamvm i386 6b22-1.10.6-0ubuntu1 [526 kB]
Get:128 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main openjdk-6-jre-lib all 6b22-1.10.6-0ubuntu1 [5,883 kB]
Get:129 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main openjdk-6-jre-headless i386 6b22-1.10.6-0ubuntu1 [26.8 MB]
Get:130 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ca-certificates-java all 20100412ubuntu0.11.04.1 [101 kB]
Get:131 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libcupscgi1 i386 1.4.6-5ubuntu1.4 [35.3 kB]
Get:132 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libcupsdriver1 i386 1.4.6-5ubuntu1.4 [24.3 kB]
Get:133 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libcupsimage2 i386 1.4.6-5ubuntu1.4 [54.3 kB]
Get:134 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libcupsmime1 i386 1.4.6-5ubuntu1.4 [18.2 kB]
Get:135 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libcupsppdc1 i386 1.4.6-5ubuntu1.4 [60.4 kB]
Get:136 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main cups-common all 1.4.6-5ubuntu1.4 [1,274 kB]
Get:137 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main cups-bsd i386 1.4.6-5ubuntu1.4 [44.5 kB]
Get:138 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main cups-client i386 1.4.6-5ubuntu1.4 [126 kB]
Get:139 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main cups-ppdc i386 1.4.6-5ubuntu1.4 [34.1 kB]
Get:140 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main cups i386 1.4.6-5ubuntu1.4 [1,963 kB]
Get:141 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libcurl3 i386 7.21.3-1ubuntu1.5 [220 kB]
Get:142 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main curl i386 7.21.3-1ubuntu1.5 [179 kB]
Get:143 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main cvs i386 1:1.12.13-12ubuntu1.11.04.1 [1,251 kB]
Get:144 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main desktopcouch all 1.0.7-0ubuntu2.1 [12.3 kB]
Get:145 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-desktopcouch-application all 1.0.7-0ubuntu2.1 [34.5 kB]
Get:146 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-desktopcouch-records all 1.0.7-0ubuntu2.1 [25.1 kB]
Get:147 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main dpkg-dev all 1.16.0~ubuntu7.1 [476 kB]
Get:148 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libdpkg-perl all 1.16.0~ubuntu7.1 [183 kB]
Get:149 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libecryptfs0 i386 87-0ubuntu1.3 [61.3 kB]
Get:150 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ecryptfs-utils i386 87-0ubuntu1.3 [100 kB]
Get:151 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main gir1.2-dbusmenu-glib-0.4 i386 0.4.3-0ubuntu4 [6,942 B]
Get:152 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libdbusmenu-glib3 i386 0.4.3-0ubuntu4 [38.1 kB]
Get:153 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main nautilus-sendto-empathy i386 2.34.0-0ubuntu3.2 [451 kB]
Get:154 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main empathy i386 2.34.0-0ubuntu3.2 [956 kB]
Get:155 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main empathy-common all 2.34.0-0ubuntu3.2 [389 kB]
Get:156 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libt1-5 i386 5.1.2-3ubuntu0.11.04.2 [139 kB]
Get:157 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libevdocument3 i386 2.32.0-0ubuntu12.4 [431 kB]
Get:158 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libevview3 i386 2.32.0-0ubuntu12.4 [100 kB]
Get:159 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main evince-common all 2.32.0-0ubuntu12.4 [105 kB]
Get:160 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main evince i386 2.32.0-0ubuntu12.4 [182 kB]
Get:161 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ffmpeg i386 4:0.6.4-0ubuntu0.11.04.1 [247 kB]
Get:162 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libavfilter1 i386 4:0.6.4-0ubuntu0.11.04.1 [52.9 kB]
Get:163 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libswscale0 i386 4:0.6.4-0ubuntu0.11.04.1 [212 kB]
Get:164 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libpostproc51 i386 4:0.6.4-0ubuntu0.11.04.1 [132 kB]
Get:165 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libavdevice52 i386 4:0.6.4-0ubuntu0.11.04.1 [44.6 kB]
Get:166 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libavformat52 i386 4:0.6.4-0ubuntu0.11.04.1 [829 kB]
Get:167 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/multiverse libavcodec-extra-52 i386 4:0.6.4-1ubuntu1 [4,488 kB]
Get:168 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe libavutil-extra-50 i386 4:0.6.4-1ubuntu1 [77.9 kB]
Get:169 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libvorbisfile3 i386 1.3.2-1ubuntu1.1 [20.4 kB]
Get:170 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libvorbisenc2 i386 1.3.2-1ubuntu1.1 [117 kB]
Get:171 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libvorbis0a i386 1.3.2-1ubuntu1.1 [93.8 kB]
Get:172 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libdbusmenu-gtk3 i386 0.4.3-0ubuntu4 [26.3 kB]
Get:173 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main firefox-globalmenu i386 11.0+build1-0ubuntu0.11.04.1 [49.4 kB]
Get:174 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main firefox i386 11.0+build1-0ubuntu0.11.04.1 [17.0 MB]
Get:175 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main firefox-branding i386 11.0+build1-0ubuntu0.11.04.1 [16.2 kB]
Get:176 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main firefox-gnome-support i386 11.0+build1-0ubuntu0.11.04.1 [16.6 kB]
Get:177 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main firefox-locale-en all 11.0+build1-0ubuntu0.11.04.1 [420 kB]
Get:178 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main gdm-guest-session all 0.24ubuntu0.1 [7,732 B]
Get:179 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libgvfscommon0 i386 1.8.0-0ubuntu3 [56.8 kB]
Get:180 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main gvfs-fuse i386 1.8.0-0ubuntu3 [13.5 kB]
Get:181 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libarchive1 i386 2.8.4-1ubuntu0.11.04.1 [141 kB]
Get:182 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libusbmuxd1 i386 1.0.7-1ubuntu0.11.04.1 [13.5 kB]
Get:183 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main usbmuxd i386 1.0.7-1ubuntu0.11.04.1 [35.9 kB]
Get:184 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libimobiledevice2 i386 1.1.0-3ubuntu1 [49.9 kB]
Get:185 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main gvfs-backends i386 1.8.0-0ubuntu3 [765 kB]
Get:186 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main gvfs i386 1.8.0-0ubuntu3 [343 kB]
Get:187 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main kdebase-runtime-data all 4:4.6.5-0ubuntu1 [3,870 kB]
Get:188 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main kdebase-runtime i386 4:4.6.5-0ubuntu1 [1,513 kB]
Get:189 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main plasma-scriptengine-javascript i386 4:4.6.5-0ubuntu1 [341 kB]
Get:190 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main plasma-scriptengine-declarative i386 4:4.6.5-0ubuntu1 [298 kB]
Get:191 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main kdemultimedia-kio-plugins i386 4:4.6.5-0ubuntu1 [79.4 kB]
Get:192 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libkcddb4 i386 4:4.6.5-0ubuntu1 [152 kB]
Get:193 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe libdvdread4 i386 4.1.3-10ubuntu3.1 [51.2 kB]
Get:194 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libgksu2-0 i386 2.0.13~pre1-3ubuntu3.1 [44.1 kB]
Get:195 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libicu44 i386 4.4.2-2ubuntu0.11.04.1 [7,057 kB]
Get:196 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libmodplug1 i386 1:0.8.8.1-2ubuntu0.3 [160 kB]
Get:197 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libpurple-bin all 1:2.7.11-1ubuntu2.1 [16.7 kB]
Get:198 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libpurple0 i386 1:2.7.11-1ubuntu2.1 [1,743 kB]
Get:199 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-impress i386 1:3.3.4-0ubuntu1 [501 kB]
Get:200 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-draw i386 1:3.3.4-0ubuntu1 [2,193 kB]
Get:201 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-gtk i386 1:3.3.4-0ubuntu1 [163 kB]
Get:202 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-gnome i386 1:3.3.4-0ubuntu1 [50.7 kB]
Get:203 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-writer i386 1:3.3.4-0ubuntu1 [6,454 kB]
Get:204 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-uno i386 1:3.3.4-0ubuntu1 [98.6 kB]
Get:205 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ttf-opensymbol all 2:2.4.3+LibO3.3.4-0ubuntu1 [109 kB]
Get:206 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-math i386 1:3.3.4-0ubuntu1 [290 kB]
Get:207 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-style-human all 1:3.3.4-0ubuntu1 [2,856 kB]
Get:208 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-common all 1:3.3.4-0ubuntu1 [16.8 MB]
Get:209 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-calc i386 1:3.3.4-0ubuntu1 [4,447 kB]
Get:210 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-base-core i386 1:3.3.4-0ubuntu1 [638 kB]
Get:211 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-core i386 1:3.3.4-0ubuntu1 [27.6 MB]
Get:212 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-emailmerge all 1:3.3.4-0ubuntu1 [5,876 B]
Get:213 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libreoffice-help-en-us all 1:3.3.4-0ubuntu1 [6,006 kB]
Get:214 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main librsvg2-common i386 2.32.1-0ubuntu3.1 [17.6 kB]
Get:215 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main librsvg2-2 i386 2.32.1-0ubuntu3.1 [96.8 kB]
Get:216 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ubuntuone-client-gnome i386 1.6.2-0ubuntu2 [56.0 kB]
Get:217 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libsyncdaemon-1.0-1 i386 1.6.2-0ubuntu2 [42.7 kB]
Get:218 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ubuntuone-client all 1.6.2-0ubuntu2 [45.7 kB]
Get:219 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-ubuntuone-client all 1.6.2-0ubuntu2 [210 kB]
Get:220 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe libwxbase2.8-0 i386 2.8.11.0-0ubuntu8.1 [595 kB]
Get:221 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libglu1-mesa i386 7.10.2-0ubuntu2.1 [161 kB]
Get:222 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe libwxgtk2.8-0 i386 2.8.11.0-0ubuntu8.1 [3,263 kB]
Get:223 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main light-themes all 0.1.8.13.1 [65.8 kB]
Get:224 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main linux-headers-2.6.38-11 all 2.6.38-11.50 [10.9 MB]
Get:225 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main linux-headers-2.6.38-11-generic i386 2.6.38-11.50 [814 kB]
Get:226 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main openjdk-6-jre i386 6b22-1.10.6-0ubuntu1 [209 kB]
Get:227 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-cupshelpers all 1.3.1+20110222-0ubuntu16.5 [35.4 kB]
Get:228 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-libxml2 i386 2.7.8.dfsg-2ubuntu0.3 [287 kB]
Get:229 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-pam i386 0.4.2-12.2ubuntu2.11.04.1 [11.1 kB]
Get:230 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-papyon all 0.5.5-1ubuntu1.4 [182 kB]
Get:231 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-software-properties all 0.80.9.1 [19.3 kB]
Get:232 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main aptdaemon-data all 0.41+bzr661-0ubuntu0.2 [163 kB]
Get:233 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-aptdaemon-gtk all 0.41+bzr661-0ubuntu0.2 [3,648 B]
Get:234 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-aptdaemon.gtk3widgets all 0.41+bzr661-0ubuntu0.2 [16.4 kB]
Get:235 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-aptdaemon.gtkwidgets all 0.41+bzr661-0ubuntu0.2 [16.0 kB]
Get:236 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main aptdaemon all 0.41+bzr661-0ubuntu0.2 [15.9 kB]
Get:237 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main python-aptdaemon all 0.41+bzr661-0ubuntu0.2 [71.6 kB]
Get:238 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main software-center all 4.0.7 [466 kB]
Get:239 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main software-properties-gtk all 0.80.9.1 [35.3 kB]
Get:240 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main system-config-printer-common all 1.3.1+20110222-0ubuntu16.5 [135 kB]
Get:241 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main system-config-printer-gnome all 1.3.1+20110222-0ubuntu16.5 [184 kB]
Get:242 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main system-config-printer-udev i386 1.3.1+20110222-0ubuntu16.5 [18.7 kB]
Get:243 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main tomboy i386 1.6.0-0ubuntu4 [506 kB]
Get:244 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xul-ext-ubufox all 0.9.4-0ubuntu1 [45.7 kB]
Get:245 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main ubufox all 0.9.4-0ubuntu1 [1,192 B]
Get:246 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main udisks i386 1.0.2-4ubuntu2 [214 kB]
Get:247 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main unity i386 3.8.16-0ubuntu1~natty3 [624 kB]
Get:248 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main unity-common all 3.8.16-0ubuntu1~natty3 [17.8 kB]
Get:249 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main update-manager all 1:0.150.5.2 [650 kB]
Get:250 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main update-manager-core i386 1:0.150.5.2 [165 kB]
Get:251 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main update-notifier i386 0.111ubuntu2.1 [57.5 kB]
Get:252 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main update-notifier-common all 0.111ubuntu2.1 [10.9 kB]
Get:253 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main whois i386 5.0.11ubuntu1.1 [29.8 kB]
Get:254 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main x11-common all 1:7.6+4ubuntu3.2 [69.6 kB]
Get:255 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xserver-common all 2:1.10.1-1ubuntu1.3 [31.7 kB]
Get:256 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xserver-xorg-core i386 2:1.10.1-1ubuntu1.3 [1,497 kB]
Get:257 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xserver-xorg-video-intel i386 2:2.14.0-4ubuntu7.3 [224 kB]
Get:258 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xserver-xorg-video-all i386 1:7.6+4ubuntu3.2 [1,138 B]
Get:259 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xserver-xorg-input-all i386 1:7.6+4ubuntu3.2 [1,008 B]
Get:260 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xserver-xorg i386 1:7.6+4ubuntu3.2 [13.4 kB]
Get:261 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main xorg i386 1:7.6+4ubuntu3.2 [1,566 B]
Get:262 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe xulrunner-1.9.2 i386 1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1 [9,190 kB]
Get:263 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe dhcp3-client all 4.1.1-P1-15ubuntu9.3 [4,548 B]
Get:264 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe dhcp3-common all 4.1.1-P1-15ubuntu9.3 [4,112 B]
Get:265 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main icedtea-plugin i386 1.1.1-0ubuntu1~11.04.2 [196 kB]
Get:266 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main icedtea-netx i386 1.1.1-0ubuntu1~11.04.2 [459 kB]
Get:267 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/universe icedtea6-plugin all 6b21.1.1-0ubuntu1~11.04.2 [938 B]
Get:268 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libgweather-common all 2.30.3-1ubuntu1.1 [606 kB]
Get:269 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main libgweather1 i386 2.30.3-1ubuntu1.1 [53.3 kB]
Get:270 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty-updates/main mobile-broadband-provider-info all 20111113-1ubuntu0.11.04 [43.6 kB]
Fetched 304 MB in 5min 38s (898 kB/s)                                          
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 185415 files and directories currently installed.)
Removing brscan ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@joe-1005HA:~$

---

### Post by JoeyB88 on 2012-04-10
> **plucky said:**
> Post output for ```
lsb_release -a
```

I'm 32 bit, I think. It's an eee pc netbook.

joe@joe-1005HA:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty
joe@joe-1005HA:~$

---

### Post by JoeyB88 on 2012-04-10
any help anyone?

---

### Post by jadtech on 2012-04-10
ok  your problem could be just this  your linux needs to be up to date  before you can install programs and drivers upper left corner  of the desk top click the wheel like icon next to your user name on the menu click update software, then when the update manager opens click the check button it will scan for updates to the linux version you have once its done install all the updates listed..

your version of linux must be up to date before the software and drivers can be installed ..

---

