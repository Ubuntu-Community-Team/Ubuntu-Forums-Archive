---
title: "Black screen after login in Ubuntu 13.04 (terminal and mouse work)"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by alexander8 on 2013-09-11
Hi,
I turned on my computer at the morning it and after login black screen with mouse's cursor. I can run terminal (ctr+alt+T) and can some programms through it. For example when I started Firefox from terminal - it works but in terminal there is :
```
(process:2480): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
```.
I am not sure but I think this problem appeared after upgrading (yesterday evening).

Please help me I have no idea what to do.

P.S. May it can also help:
```
Get:3 http://security.ubuntu.com raring-security Release [40.8 kB]             
Hit http://dl.google.com stable Release.gpg                                    
Get:4 http://dl.google.com stable Release [1,347 B]                            
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://ca.archive.ubuntu.com raring Release.gpg                            
Get:5 http://dl.google.com stable/main i386 Packages [1,211 B]                 
Get:6 http://security.ubuntu.com raring-security/main Sources [38.0 kB]        
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://extras.ubuntu.com raring Release                                    
Get:7 http://ca.archive.ubuntu.com raring-updates Release.gpg [933 B]          
Get:8 http://security.ubuntu.com raring-security/restricted Sources [14 B]     
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://dl.google.com stable/main i386 Packages                             
Get:9 http://security.ubuntu.com raring-security/universe Sources [8,842 B]    
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://ca.archive.ubuntu.com raring-backports Release.gpg                  
Get:10 http://security.ubuntu.com raring-security/multiverse Sources [2,266 B] 
Hit http://ppa.launchpad.net raring Release.gpg                                
Get:11 http://security.ubuntu.com raring-security/main i386 Packages [99.5 kB] 
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Hit http://ca.archive.ubuntu.com raring Release                                
Hit http://ppa.launchpad.net raring Release.gpg                                
Get:12 http://ca.archive.ubuntu.com raring-updates Release [40.8 kB]           
Hit http://ppa.launchpad.net raring Release                                    
Get:13 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]
Get:14 http://security.ubuntu.com raring-security/universe i386 Packages [34.3 kB]
Hit http://ppa.launchpad.net raring Release                                    
Get:15 http://security.ubuntu.com raring-security/multiverse i386 Packages [3,864 B]
Hit http://ppa.launchpad.net raring Release                                    
Hit http://security.ubuntu.com raring-security/main Translation-en             
Hit http://ppa.launchpad.net raring Release                                    
Hit http://security.ubuntu.com raring-security/multiverse Translation-en       
Hit http://ppa.launchpad.net raring Release                                    
Hit http://security.ubuntu.com raring-security/restricted Translation-en       
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ca.archive.ubuntu.com raring-backports Release                      
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com raring-security/universe Translation-en         
Hit http://ca.archive.ubuntu.com raring/main Sources                           
Hit http://ca.archive.ubuntu.com raring/restricted Sources            
Ign http://extras.ubuntu.com raring/main Translation-en_CA                     
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://ca.archive.ubuntu.com raring/universe Sources              
Ign http://extras.ubuntu.com raring/main Translation-en               
Hit http://ca.archive.ubuntu.com raring/multiverse Sources            
Hit http://ca.archive.ubuntu.com raring/main i386 Packages            
Ign http://security.ubuntu.com raring-security/main Translation-en_CA
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com raring/restricted i386 Packages
Ign http://security.ubuntu.com raring-security/restricted Translation-en_CA
Ign http://security.ubuntu.com raring-security/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com raring/universe i386 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ca.archive.ubuntu.com raring/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com raring/main Translation-en_CA
Hit http://ca.archive.ubuntu.com raring/main Translation-en
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ca.archive.ubuntu.com raring/multiverse Translation-en
Hit http://ca.archive.ubuntu.com raring/restricted Translation-en
Hit http://ca.archive.ubuntu.com raring/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com raring/universe Translation-en
Get:16 http://ca.archive.ubuntu.com raring-updates/main Sources [65.1 kB]
Get:17 http://ca.archive.ubuntu.com raring-updates/restricted Sources [14 B]
Get:18 http://ca.archive.ubuntu.com raring-updates/universe Sources [71.9 kB]
Get:19 http://ca.archive.ubuntu.com raring-updates/multiverse Sources [2,266 B]
Get:20 http://ca.archive.ubuntu.com raring-updates/main i386 Packages [166 kB]
Get:21 http://ca.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:22 http://ca.archive.ubuntu.com raring-updates/universe i386 Packages [144 kB]
Get:23 http://ca.archive.ubuntu.com raring-updates/multiverse i386 Packages [3,864 B]
Hit http://ca.archive.ubuntu.com raring-updates/main Translation-en     
Hit http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/restricted Translation-en      
Hit http://ca.archive.ubuntu.com raring-updates/universe Translation-en        
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com raring-backports/main Sources                 
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/restricted Sources           
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com raring-backports/universe Sources             
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/multiverse Sources           
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com raring-backports/main i386 Packages           
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/restricted i386 Packages     
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com raring-backports/universe i386 Packages       
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/multiverse i386 Packages     
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/main Translation-en          
Hit http://ca.archive.ubuntu.com raring-backports/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com raring-backports/restricted Translation-en    
Hit http://ca.archive.ubuntu.com raring-backports/universe Translation-en      
Ign http://ca.archive.ubuntu.com raring/multiverse Translation-en_CA           
Ign http://ca.archive.ubuntu.com raring/restricted Translation-en_CA           
Ign http://ca.archive.ubuntu.com raring-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/universe Translation-en_CA
Fetched 726 kB in 13s (53.6 kB/s)
Reading package lists... Done
deyneko@Big-comp:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata tzdata-java
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 634 kB of archives.
After this operation, 29.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring-updates/main tzdata-java all 2013d-0ubuntu0.13.04 [141 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ raring-updates/main tzdata all 2013d-0ubuntu0.13.04 [494 kB]
Fetched 634 kB in 1s (342 kB/s) 
Preconfiguring packages ...
(Reading database ... 335300 files and directories currently installed.)
Preparing to replace tzdata-java 2013b-1ubuntu1 (using .../tzdata-java_2013d-0ubuntu0.13.04_all.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2013b-1ubuntu1 (using .../tzdata_2013d-0ubuntu0.13.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2013d-0ubuntu0.13.04) ...

Current default time zone: 'America/Montreal'
Local time is now:      Wed Sep 11 10:41:04 EDT 2013.
Universal Time is now:  Wed Sep 11 14:41:04 UTC 2013.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

Setting up tzdata-java (2013d-0ubuntu0.13.04) ...
deyneko@Big-comp:~$ sudo apt-get update
Hit http://dl.google.com stable Release.gpg
Hit http://security.ubuntu.com raring-security Release.gpg                     
Hit http://dl.google.com stable Release.gpg                                    
Hit http://security.ubuntu.com raring-security Release                         
Hit http://dl.google.com stable Release                                        
Hit http://security.ubuntu.com raring-security/main Sources                    
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://ca.archive.ubuntu.com raring Release.gpg                            
Hit http://security.ubuntu.com raring-security/restricted Sources              
Hit http://dl.google.com stable Release                                        
Hit http://security.ubuntu.com raring-security/universe Sources                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com raring-security/multiverse Sources              
Hit http://extras.ubuntu.com raring Release                                    
Hit http://ppa.launchpad.net raring Release.gpg                                
Get:1 http://ca.archive.ubuntu.com raring-updates Release.gpg [933 B]          
Hit http://security.ubuntu.com raring-security/main i386 Packages              
Hit http://security.ubuntu.com raring-security/restricted i386 Packages        
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com raring-security/universe i386 Packages          
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://ca.archive.ubuntu.com raring-backports Release.gpg                  
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Hit http://ca.archive.ubuntu.com raring Release                                
Hit http://security.ubuntu.com raring-security/main Translation-en             
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://security.ubuntu.com raring-security/multiverse Translation-en       
Get:2 http://ca.archive.ubuntu.com raring-updates Release [40.8 kB]            
Hit http://security.ubuntu.com raring-security/restricted Translation-en       
Hit http://ppa.launchpad.net raring Release                                    
Hit http://ppa.launchpad.net raring Release                                    
Hit http://security.ubuntu.com raring-security/universe Translation-en         
Hit http://ppa.launchpad.net raring Release                                    
Hit http://ppa.launchpad.net raring Release                                    
Hit http://ca.archive.ubuntu.com raring-backports Release                      
Ign http://dl.google.com stable/main Translation-en_CA                         
Hit http://ppa.launchpad.net raring Release                                    
Hit http://ca.archive.ubuntu.com raring/main Sources                           
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_CA                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://ca.archive.ubuntu.com raring/restricted Sources                     
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ca.archive.ubuntu.com raring/universe Sources                       
Ign http://security.ubuntu.com raring-security/main Translation-en_CA          
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com raring/multiverse Sources            
Ign http://extras.ubuntu.com raring/main Translation-en_CA            
Ign http://security.ubuntu.com raring-security/restricted Translation-en_CA
Ign http://security.ubuntu.com raring-security/universe Translation-en_CA
Hit http://ppa.launchpad.net raring/main i386 Packages                
Ign http://extras.ubuntu.com raring/main Translation-en               
Hit http://ca.archive.ubuntu.com raring/main i386 Packages
Hit http://ca.archive.ubuntu.com raring/restricted i386 Packages
Hit http://ca.archive.ubuntu.com raring/universe i386 Packages
Hit http://ca.archive.ubuntu.com raring/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com raring/main Translation-en_CA
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ca.archive.ubuntu.com raring/main Translation-en
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ca.archive.ubuntu.com raring/multiverse Translation-en
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ca.archive.ubuntu.com raring/restricted Translation-en
Hit http://ca.archive.ubuntu.com raring/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com raring/universe Translation-en
Get:3 http://ca.archive.ubuntu.com raring-updates/main Sources [65.1 kB]
Get:4 http://ca.archive.ubuntu.com raring-updates/restricted Sources [14 B]
Get:5 http://ca.archive.ubuntu.com raring-updates/universe Sources [71.9 kB]
Get:6 http://ca.archive.ubuntu.com raring-updates/multiverse Sources [2,266 B]
Get:7 http://ca.archive.ubuntu.com raring-updates/main i386 Packages [166 kB]
Get:8 http://ca.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:9 http://ca.archive.ubuntu.com raring-updates/universe i386 Packages [144 kB]
Get:10 http://ca.archive.ubuntu.com raring-updates/multiverse i386 Packages [3,864 B]
Hit http://ca.archive.ubuntu.com raring-updates/main Translation-en     
Hit http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/restricted Translation-en      
Hit http://ca.archive.ubuntu.com raring-updates/universe Translation-en        
Hit http://ca.archive.ubuntu.com raring-backports/main Sources                 
Hit http://ca.archive.ubuntu.com raring-backports/restricted Sources           
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com raring-backports/universe Sources             
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/multiverse Sources           
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com raring-backports/main i386 Packages           
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/restricted i386 Packages     
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Hit http://ca.archive.ubuntu.com raring-backports/universe i386 Packages       
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/multiverse i386 Packages     
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/main Translation-en          
Ign http://ppa.launchpad.net raring/main Translation-en_CA                     
Ign http://ppa.launchpad.net raring/main Translation-en                        
Hit http://ca.archive.ubuntu.com raring-backports/multiverse Translation-en    
Hit http://ca.archive.ubuntu.com raring-backports/restricted Translation-en    
Hit http://ca.archive.ubuntu.com raring-backports/universe Translation-en      
Ign http://ca.archive.ubuntu.com raring/multiverse Translation-en_CA           
Ign http://ca.archive.ubuntu.com raring/restricted Translation-en_CA           
Ign http://ca.archive.ubuntu.com raring-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com raring-backports/universe Translation-en_CA
Fetched 495 kB in 13s (37.2 kB/s)
Reading package lists... Done
deyneko@Big-comp:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
deyneko@Big-comp:~$ 
```

---

### Post by alexander8 on 2013-09-11
I still trying to resolve this problem... When I tried to started Unity I received this:

```
:~$ unity
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2013-09-11 12:27:52 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2013-09-11 12:27:52 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported

compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x2000005
  Serial number of failed request:  8427
  Current serial number in output stream:  8431
```

My video card is Radeon EAH5750

Any ideas?

---

### Post by whitesmith on 2013-09-11
> **alexander8 said:**
> I still trying to resolve this problem... When I tried to started Unity I received this [snip]
Any ideas?
I don't follow. Unity should start automatically. You should not have to start it. It simply appears on a screen as the last step of a successful boot. Explain fully what you did to your computer last night, and then maybe we can help.

---

### Post by Panderz on 2013-09-11
Post output of "echo $DISPLAY"

---

### Post by alexander8 on 2013-09-11
> **whitesmith said:**
> Explain fully what you did to your computer last night, and then maybe we can help.
Actually nothing to explain. Last night I worked with pdf financial document and turned my comp off after this. When I tried to start the computer at morning I saw black screen. Just all.
But I remember that there was an updating trough updating program. I allowed for updating but not remember details.

Also I tried to reset compiz. After this background image appeared and conky (it in autostart) and now right button of mouse started work. Actually Ubuntu works but there is not Unity(?). For example I can start Nautilus, thunderbird, firefox from terminal etc. 

> **Panderz said:**
> Post output of "echo $DISPLAY"
```
~$ echo $DISPLAY
:0.0
:~$ 

```

---

### Post by alexander8 on 2013-09-12
May be I need to reinstall unity? If yes - how can I do it?

---

### Post by Jonathan Precise on 2013-09-12
Looks like you have the proprietary drivers installed.

Re-install ubuntu, and do not choose the proprietary drivers.

---

