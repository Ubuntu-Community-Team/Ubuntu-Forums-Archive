---
title: "Update Download Problem"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by 7Starphy on 2012-11-14
Ok everytime , Ubuntu prompts me for downloading updates , I also accept it and download the updates ,but everytime I get a message telling some of the updates could not be installed . I dont know why..Can anyone please explain why and how to deal with the problem?
This is the error message ,I am getting - 
"**Data files for some packages could not be downloaded **

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer, flashplugin-installer

This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem."

---

### Post by drmrgd on 2012-11-14
If your internet connection is OK, you could just try reinstalling those packages as suggested by the error.  Open a terminal and issue the following:

```
sudo apt-get update && sudo apt-get install --reinstall ttf-mscorefonts-installer flashplugin-installer
```

Report back any errors you get.

---

### Post by 7Starphy on 2012-11-14
I am getting an error , 
```


Ign http://dl.google.com stable InRelease
Ign http://in.archive.ubuntu.com precise InRelease                             
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://dl.google.com stable Release.gpg                                    
Hit http://in.archive.ubuntu.com precise Release.gpg                           
Get:2 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Get:4 http://in.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://in.archive.ubuntu.com precise Release                               
Get:5 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:6 http://security.ubuntu.com precise-security/main Sources [54.6 kB]       
Hit http://dl.google.com stable/main amd64 Packages                            
Get:7 http://in.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                              
Get:8 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:9 http://security.ubuntu.com precise-security/universe Sources [15.8 kB]   
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [196 kB]
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://in.archive.ubuntu.com precise/main Sources                          
Hit http://in.archive.ubuntu.com precise/restricted Sources                    
Hit http://in.archive.ubuntu.com precise/universe Sources                      
Hit http://in.archive.ubuntu.com precise/multiverse Sources                    
Hit http://in.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://in.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://in.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://in.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://in.archive.ubuntu.com precise/main i386 Packages                    
Get:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:13 http://security.ubuntu.com precise-security/universe amd64 Packages [54.7 kB]
Get:14 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:15 http://security.ubuntu.com precise-security/main i386 Packages [201 kB] 
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://in.archive.ubuntu.com precise/universe i386 Packages                
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex           
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [54.9 kB]
Get:18 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex             
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://dl.google.com stable/main Translation-en                            
Get:19 http://in.archive.ubuntu.com precise-updates/main Sources [187 kB]      
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://archive.canonical.com precise/partner Translation-en_IN             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:20 http://in.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:21 http://in.archive.ubuntu.com precise-updates/universe Sources [61.6 kB] 
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:22 http://in.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:23 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [426 kB]
Get:24 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:25 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [153 kB]
Get:26 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:27 http://in.archive.ubuntu.com precise-updates/main i386 Packages [433 kB]
Get:28 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:29 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [153 kB]
Get:30 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Get:31 http://in.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:32 http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:33 http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:34 http://in.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:35 http://in.archive.ubuntu.com precise-backports/main Sources [2,422 B]
Get:36 http://in.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:37 http://in.archive.ubuntu.com precise-backports/universe Sources [17.7 kB]
Get:38 http://in.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:39 http://in.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:40 http://in.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:41 http://in.archive.ubuntu.com precise-backports/universe amd64 Packages [16.2 kB]
Get:42 http://in.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:43 http://in.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:44 http://in.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:45 http://in.archive.ubuntu.com precise-backports/universe i386 Packages [16.2 kB]
Get:46 http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://in.archive.ubuntu.com precise/main Translation-en
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise/restricted Translation-en
Hit http://in.archive.ubuntu.com precise/universe Translation-en
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,275 kB in 4s (517 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 27.4 kB/35.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise/multiverse ttf-mscorefonts-installer all 3.4ubuntu3 [27.4 kB]
Fetched 27.4 kB in 0s (1,056 kB/s)                   
Preconfiguring packages ...
(Reading database ... 185887 files and directories currently installed.)
Preparing to replace ttf-mscorefonts-installer 3.4ubuntu3 (using .../ttf-mscorefonts-installer_3.4ubuntu3_all.deb) ...
mscorefonts-eula license has already been accepted
Unpacking replacement ttf-mscorefonts-installer ...
Preparing to replace flashplugin-installer 11.2.202.251ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.251ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement flashplugin-installer ...
Processing triggers for fontconfig ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.251.orig.tar.gz
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
Setting up ttf-mscorefonts-installer (3.4ubuntu3) ...
Setting up flashplugin-installer (11.2.202.251ubuntu0.12.04.1) ...

```

I dont see anything wrong with my internet connection ..I mean I am able to browse websites ,install apps from Software center .. :(

---

### Post by grahammechanical on 2012-11-14
The listing ends with this:

> Setting up ttf-mscorefonts-installer (3.4ubuntu3) ...
Setting up flashplugin-installer (11.2.202.251ubuntu0.12.04.1) ...

What happens next? Did it succeeed?

In relation to those two packages you also get this error:

> IOError: [Errno socket error] [Errno 110] Connection timed out

I may be wrong but to be that says there may be a problem at the other end of the line.


The MS core fonts are downloaded and installed one at time from a site called sourceforge.net

> downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)

The connection to that site may be timing out because that site is not responding to the request to send data.

Regards.

---

### Post by drmrgd on 2012-11-14
Hmmm...yes, for sure your internet connection is OK, and it looks like the main package manager is OK.  The problem seems to lie with the update-notification package.  

I did a quick search and it looks like this is a bug with an older version of update-notifier-common.  You might try following the thread to see if you can update it and fix the problem:

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1003100](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1003100)

---

### Post by 7Starphy on 2012-11-14
Sorry ,I dont follow , what am i supposed to do now ? I couldnt understand anything in that link ..can you tell me what I should do .

---

### Post by raja.genupula on 2012-11-14
Ok ,this is what i have got from the link . open your terminal and type this
```
  sudo apt-get install --reinstall update-notifier
```

---

### Post by drmrgd on 2012-11-14
I think what they're basically saying is to reinstall update-notifier-common as that seems to be what's messing things up.  Looking at the stuff that the reverse depends for the package (those packages that depend on update-notifier-common), I'm not sure about removing the package and reinstalling.  So, maybe we'll just try to reinstall that package first before we get to more drastic measures:

```
sudo apt-get update && sudo apt-get install --reinstall update-notifier-common
``` 

Please post back any errors you get with that. It may be that this will work the first time; it may be that we'll have to purge the package and reinstall.

---

### Post by 7Starphy on 2012-11-14
Nope ,I am still getting the same errors :( After I typed the code you guys asked me to
```


Ign http://in.archive.ubuntu.com precise InRelease
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.canonical.com precise InRelease                             
Hit http://in.archive.ubuntu.com precise Release.gpg
Get:1 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:3 http://in.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://in.archive.ubuntu.com precise Release                               
Get:5 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Get:6 http://in.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://in.archive.ubuntu.com precise/main Sources                          
Hit http://in.archive.ubuntu.com precise/restricted Sources                    
Hit http://in.archive.ubuntu.com precise/universe Sources                      
Hit http://in.archive.ubuntu.com precise/multiverse Sources                    
Hit http://in.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://in.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://in.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                              
Get:7 http://security.ubuntu.com precise-security/main Sources [54.6 kB]       
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://in.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://in.archive.ubuntu.com precise/main i386 Packages                    
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://in.archive.ubuntu.com precise/universe i386 Packages                
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex             
Get:8 http://in.archive.ubuntu.com precise-updates/main Sources [187 kB]       
Get:9 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:10 http://security.ubuntu.com precise-security/universe Sources [15.8 kB]  
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [1,392 B]
Get:12 http://security.ubuntu.com precise-security/main amd64 Packages [196 kB]
Get:13 http://in.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
Get:14 http://in.archive.ubuntu.com precise-updates/universe Sources [61.6 kB] 
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://dl.google.com stable/main Translation-en                            
Get:15 http://in.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:16 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [426 kB]
Get:17 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:18 http://security.ubuntu.com precise-security/universe amd64 Packages [54.7 kB]
Get:19 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,189 B]
Get:20 http://security.ubuntu.com precise-security/main i386 Packages [201 kB] 
Ign http://archive.canonical.com precise/partner Translation-en_IN             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:21 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:22 http://security.ubuntu.com precise-security/universe i386 Packages [54.9 kB]
Get:23 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Get:24 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:25 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [153 kB]
Get:26 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:27 http://in.archive.ubuntu.com precise-updates/main i386 Packages [433 kB]
Get:28 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:29 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [153 kB]
Get:30 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:31 http://in.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:32 http://in.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:33 http://in.archive.ubuntu.com precise-backports/universe Sources [17.7 kB]
Get:34 http://in.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:35 http://in.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:36 http://in.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:37 http://in.archive.ubuntu.com precise-backports/universe amd64 Packages [16.2 kB]
Get:38 http://in.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:39 http://in.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:40 http://in.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:41 http://in.archive.ubuntu.com precise-backports/universe i386 Packages [16.2 kB]
Get:42 http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://in.archive.ubuntu.com precise/main Translation-en                   
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://in.archive.ubuntu.com precise/restricted Translation-en             
Hit http://in.archive.ubuntu.com precise/universe Translation-en               
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,264 kB in 11s (198 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 222 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier-common all 0.119ubuntu8.6 [222 kB]
Fetched 222 kB in 0s (4,384 kB/s)              
(Reading database ... 185887 files and directories currently installed.)
Preparing to replace update-notifier-common 0.119ubuntu8.6 (using .../update-notifier-common_0.119ubuntu8.6_all.deb) ...
Unpacking replacement update-notifier-common ...
Setting up update-notifier-common (0.119ubuntu8.6) ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.251.orig.tar.gz
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 234, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 93, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 239, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 344, in open_http
    h.endheaders(data)
  File "/usr/lib/python2.7/httplib.py", line 954, in endheaders
    self._send_output(message_body)
  File "/usr/lib/python2.7/httplib.py", line 814, in _send_output
    self.send(msg)
  File "/usr/lib/python2.7/httplib.py", line 776, in send
    self.connect()
  File "/usr/lib/python2.7/httplib.py", line 757, in connect
    self.timeout, self.source_address)
  File "/usr/lib/python2.7/socket.py", line 571, in create_connection
    raise err
IOError: [Errno socket error] [Errno 110] Connection timed out

```

---

### Post by drmrgd on 2012-11-14
Just noticed something on the tail end of that bug report (which, by the way, you might consider adding a report to just to help get this fixed!): there's update-notifier-common AND update-notifier.  Seems the last user was able to work around this by reinstalling update-notifier.  Try that and see if you can get her workaround to work for you:

```
sudo apt-get install --reinstall update-notifier
```

After that, I'm sort of running out of options, and we may have to wait for a bug fix.

---

### Post by 7Starphy on 2012-11-14
I am able to re-install the Update notifier thing..just that after I do that and re-run the code you gave me intitially , it is still posing the same problems :(

---

### Post by drmrgd on 2012-11-14
There is one other possibility that I came across earlier but didn't see how it fit at first.  Are you by chance connecting to the web through a proxy?  Based on the 'Connection timed out' error, I started thinking that maybe this solution was relevant:

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1005837](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1005837)

Apart from that, I'm officially out of ideas.  Sorry to not have been more help

---

### Post by 7Starphy on 2012-11-14
Yes! I am connected to my Internet via my university proxy . I think the bug you mentioned in that link and mine are similar ,but I dont understand how to solve it . Can you please explain the possible solution discussed in the link you gave ?

---

### Post by drmrgd on 2012-11-14
To be honest, this is outside of my realm of knowledge too and I'm not quite sure what's going on.  What I read here is that the apt system is somehow not using the system wide proxy settings and throwing an error.  It seems that when that poster ran with 'sudo -i', which changes the way the environment is loaded for a sudo shell command, it worked.  It seems that when the user forced the proxy environment settings by modifying the update-notifier script in cron they were able to solve it possibly.  

Before you mess with it, perhaps another user can shed some light.  Otherwise, I would say either make a backup copy of the script that person mentioned, then modify the script and give it a shot, or post to that bug report with your problems and see if it helps resolve the problem from there.  I'm not 100% on how that system actually works enough to know how to fix it myself.

---

### Post by 7Starphy on 2012-11-14
I did change the file from this to this , can you verify whether I have done it as it is requested in that link ?
this is my FINAL upadte-notifier-common ,file
```

#!/bin/sh

set -e

[ -x /usr/lib/update-notifier/package-data-downloader ] || exit 0
./etc/environment
export http_proxy https_proxy
# Try to rerun any package data downloads that failed at package install time.
/usr/lib/update-notifier/package-data-downloader

```

---

### Post by drmrgd on 2012-11-14
I think that looks right to me.  I guess it's no harm to try it, and if it fails just revert back to the original form of the script.  Again, this is a little outside of my knowledge base....

---

