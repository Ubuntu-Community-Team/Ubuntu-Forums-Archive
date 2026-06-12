---
title: "Software Center not working in Ubuntu 12.04"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by MarkoF on 2012-09-16
Hi all! I'm a new Ubuntu user, recently installed it as my job demanded it. I have no previos experience with any OS apart from various Windows editions.

Two weeks ago or so, I noticed that software center stopped responding. It would start, but just show blank screen with the circle loading thingy going on and on. Tried to load it from terminal as I've read that that is the way to see if some error is occuring, and this is what I've got.

```
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,025 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,025 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,282 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,282 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,565 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,565 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,816 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,816 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
```


That is repeating and repeating without end. These are the things I tried (see also this thread [http://ubuntuforums.org/showthread.php?p=12236380](http://ubuntuforums.org/showthread.php?p=12236380) ):

- updating system (apt-get update, if that's what it is)
- uninstalling and reinstalling software center from terminal
- and one day, I even had to erase the whole Linux partition and install everything again (bad sectors in MRB area); so after completely new Ubuntu installation, this same problem appeared three or four days ago

My current version of software center is:
software-center 5.2.5 install ok installed
software-center 5.2.5 precise de.archive.ubuntu.com
software-center/precise uptodate 5.2.5

I've found a workaround for installing programs without using SC, so I don't have problems with that. But it is irritating that an important part of the system is not working, and those 'system error' messages everytime I boot Ubuntu (they appeared just after SC stopped working). Also, I cannot update the system via Update manager, but have to go through terminal.

Any suggestions?

---

### Post by linuxorunix on 2012-09-16
> **MarkoF said:**
> Hi all! I'm a new Ubuntu user, recently installed it as my job demanded it. I have no previos experience with any OS apart from various Windows editions.

Two weeks ago or so, I noticed that software center stopped responding. It would start, but just show blank screen with the circle loading thingy going on and on. Tried to load it from terminal as I've read that that is the way to see if some error is occuring, and this is what I've got.



DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,025 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,025 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,282 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,282 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,565 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,565 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-16 11:50:03,816 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-16 11:50:03,816 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)


That is repeating and repeating without end. These are the things I tried (see also this thread [http://ubuntuforums.org/showthread.php?p=12236380](http://ubuntuforums.org/showthread.php?p=12236380) ):

- updating system (apt-get update, if that's what it is)
- uninstalling and reinstalling software center from terminal
- and one day, I even had to erase the whole Linux partition and install everything again (bad sectors in MRB area); so after completely new Ubuntu installation, this same problem appeared three or four days ago

My current version of software center is:
software-center 5.2.5 install ok installed
software-center 5.2.5 precise de.archive.ubuntu.com
software-center/precise uptodate 5.2.5

I've found a workaround for installing programs without using SC, so I don't have problems with that. But it is irritating that an important part of the system is not working, and those 'system error' messages everytime I boot Ubuntu (they appeared just after SC stopped working). Also, I cannot update the system via Update manager, but have to go through terminal.

Any suggestions?
Dear MarkoF,

Maybe you could try Synaptic Package Manager: [http://www.nongnu.org/synaptic/action.html]("http://www.nongnu.org/synaptic/action.html") Description and features copied from their website:

Synaptic is a graphical package management program for apt. It provides the same features as the apt-get command line utility with a GUI front-end based on Gtk+.

Features

(as of version 0.62)

Install, remove, upgrade and downgrade single and multiple packages.
Upgrade your whole system.
Manage package repositories (sources.list).
Find packages by name, description and several other attributes.
Select packages by status, section, name or a custom filter.
Sort packages by name, status, size or version.
Browse all available online documentation related to a package.
Download the latest changelog of a package.
Lock packages to the current version.
Force the installation of a specifc package version.
Undo/Redo of selections.
Built-in terminal emulator for the package manager.
Debian/Ubuntu only: Configure packages through the debconf system.
Debian/Ubuntu only: Xapain based fast search (thanks to Enrico Zini)
Debian/Ubuntu only: Get screenshots from screenshots.debian.net


If you need the PPA you can probably find it on [https://launchpad.net/]("https://launchpad.net/")
If not, you could add synaptic using this code in a terminal:

```
sudo apt-get install synaptic
```
And then you press enter and you will need to enter your root password. After this proccess is completed, just type ```
sudo synaptic
``` to open (after entering your password) Synaptic Package Manager with root privileges.

Hopefully this will help you a bit further. :)

Yours faithfully,
linuxorunix

---

### Post by itolf on 2012-09-16
Hi, I am not really sure what has gone wrong with the Software Center as I new to Linux myself, but  you could try un-installing it and re-installing it using the Terminal.

To remove it use this code...

```
sudo apt-get --purge remove Software-Center
```Then to re-install it...

```
sudo apt-get install Software-Center
```Another popular way to install is using the Synaptic manager...

```
sudo apt-get install synaptic
```I hope this is helpful. 

itolf.

---

### Post by mörgæs on 2012-09-16
The command *apt-get update* does not update the system, in spite of the name.

Please boot the computer, close all windows which might open and run

```
sudo apt-get update
sudo apt-get upgrade
```

Please post the output here.

If you (like me) find that Software Centre is in general too buggy, there are alternatives as described in the other posts in the thread.

---

### Post by MarkoF on 2012-09-16
@[linuxorunix]("http://ubuntuforums.org/member.php?u=1709388")
Thank you for your sugestions. I am already using Synaptic Manager, it is a great program.

@[itolf]("http://ubuntuforums.org/member.php?u=1731875")
I have already done that (as described in the initial post), and it didn't help.

@[[COLOR=#DD4814]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075")
I have done as you asked, and the report is below. Unfortunately, it seems that it was too long as terminal allowed me to scroll up only so much.

Thank you all for your comments and suggestions. I use Synaptic Manager, but even when I can't use it to install programs I can always employ dpkg (I think, found it somewhere on the Net) command in terminal. So it's not the matter of being unable to install things, it's the matter of comfort of working in Ubuntu and irritation that an integral part of it stops working a few days after clean installations.

That, and those pesky error messages after the boot.


```
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Get:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise InRelease                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [489 B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Sources                          
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Sources                      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:5 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [2,603 B]                       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main amd64 Packages           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted amd64 Packages     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe amd64 Packages       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse amd64 Packages     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Get:6 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main Sources [2,422 B]    
Get:7 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted Sources [14 B] 
Get:8 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe Sources [14.5 kB]
Get:9 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse Sources [2,230 B]
Get:10 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Get:11 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages [1,029 B]          
Get:12 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:13 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe amd64 Packages [12.9 kB]
Get:14 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,046 B]
Get:15 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:16 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:17 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe i386 Packages [13.0 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:18 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,059 B]
Get:19 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:20 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:21 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:22 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe TranslationIndex [72 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise/universe Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:23 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages [1,029 B]           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/main Translation-en         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:24 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/multiverse Translation-en [1,118 B]
Hit [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/restricted Translation-en   
Get:25 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) precise-backports/universe Translation-en [9,472 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_US                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Fetched 126 kB in 10s (12.3 kB/s)                                              
Reading package lists... Done
```


```
**marko@Marko-laptop:~$ sudo apt-get install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

```
**marko@Marko-laptop:~$ sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ginn libgrip0
The following packages will be upgraded:
  eog wine1.5 wine1.5-amd64 wine1.5-i386:i386 winetricks
5 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 45.3 MB of archives.
After this operation, 14.3 kB of additional disk space will be used.
**Do you want to continue [Y/n]? y**
Get:1 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) precise-updates/main eog amd64 3.4.2-0ubuntu1.1 [768 kB]
Get:2 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main wine1.5-amd64 amd64 1.5.13-0ubuntu1 [22.5 MB]
Get:3 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main wine1.5 amd64 1.5.13-0ubuntu1 [1,140 kB]
Get:4 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main wine1.5-i386 i386 1.5.13-0ubuntu1 [20.7 MB]
Get:5 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main winetricks amd64 0.0+20120912~precise1~ppa1 [149 kB]
Fetched 45.3 MB in 29s (1,516 kB/s)                                            
(Reading database ... 192432 files and directories currently installed.)
Preparing to replace wine1.5-amd64 1.5.12-0ubuntu1 (using .../wine1.5-amd64_1.5.13-0ubuntu1_amd64.deb) ...
Unpacking replacement wine1.5-amd64 ...
Preparing to replace wine1.5 1.5.12-0ubuntu1 (using .../wine1.5_1.5.13-0ubuntu1_amd64.deb) ...
Unpacking replacement wine1.5 ...
Preparing to replace wine1.5-i386:i386 1.5.12-0ubuntu1 (using .../wine1.5-i386_1.5.13-0ubuntu1_i386.deb) ...
Unpacking replacement wine1.5-i386:i386 ...
Preparing to replace winetricks 0.0+20120819~precise1~ppa1 (using .../winetricks_0.0+20120912~precise1~ppa1_amd64.deb) ...
Unpacking replacement winetricks ...
Preparing to replace eog 3.4.2-0ubuntu1 (using .../eog_3.4.2-0ubuntu1.1_amd64.deb) ...
Unpacking replacement eog ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:i386 ...
warning: Schema 'com.canonical.notify-osd' has path '/apps/notify-osd/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.ApplicationsLens' has path '/desktop/unity/lenses/applications/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Runner' has path '/desktop/unity/runner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.FilesLens' has path '/desktop/unity/lenses/files/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity' has path '/desktop/unity/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Launcher' has path '/desktop/unity/launcher/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Panel' has path '/desktop/unity/panel/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Devices' has path '/desktop/unity/devices/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Dash' has path '/desktop/unity/dash/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.indicator.session' has path '/apps/indicator-session/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu-tweak.tweak' has path '/apps/ubuntu-tweak/tweak/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu-tweak.apps' has path '/apps/ubuntu-tweak/apps/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu-tweak.janitor' has path '/apps/ubuntu-tweak/janitor/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu.update-manager' has path '/apps/update-manager/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard' has path '/apps/onboard/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.auto-show' has path '/apps/onboard/auto-show/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.keyboard' has path '/apps/onboard/keyboard/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window' has path '/apps/onboard/window/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window.landscape' has path '/apps/onboard/window/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window.portrait' has path '/apps/onboard/window/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette' has path '/apps/onboard/icon-palette/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.landscape' has path '/apps/onboard/icon-palette/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.portrait' has path '/apps/onboard/icon-palette/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.universal-access' has path '/apps/onboard/universal-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.theme-settings' has path '/apps/onboard/theme-settings/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.lockdown' has path '/apps/onboard/lockdown/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.scanner' has path '/apps/onboard/scanner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.Telepathy.Logger' has path '/apps/telepathy-logger/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.gstreamer-0.10.default-elements' has path '/desktop/gstreamer/0.10/default-elements/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.Vino' has path '/desktop/gnome/remote-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.cache' has path '/desktop/gnome/crypto/cache/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.pgp' has path '/desktop/gnome/crypto/pgp/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse' has path '/apps/seahorse/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse.manager' has path '/apps/seahorse/listing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.dns_sd' has path '/system/dns-sd/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.locale' has path '/system/locale/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy' has path '/system/proxy/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.http' has path '/system/proxy/http/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.https' has path '/system/proxy/https/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.ftp' has path '/system/proxy/ftp/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.socks' has path '/system/proxy/socks/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.smb' has path '/system/smb/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-piwigo' has path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-piwigo/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-yandex-fotki' has path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-yandex-fotki/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell' has path '/apps/shotwell/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences' has path '/apps/shotwell/preferences/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.ui' has path '/apps/shotwell/preferences/ui/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.slideshow' has path '/apps/shotwell/preferences/slideshow/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.window' has path '/apps/shotwell/preferences/window/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.files' has path '/apps/shotwell/preferences/files/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.crop-settings' has path '/apps/shotwell/crop-settings/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.editing' has path '/apps/shotwell/preferences/editing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing' has path '/apps/shotwell/sharing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.facebook' has path '/apps/shotwell/sharing/facebook/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.flickr' has path '/apps/shotwell/sharing/flickr/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.picasa' has path '/apps/shotwell/sharing/picasa/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.youtube' has path '/apps/shotwell/sharing/youtube/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.dataimports' has path '/apps/shotwell/dataimports/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.video' has path '/apps/shotwell/video/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.printing' has path '/apps/shotwell/printing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.plugins' has path '/apps/shotwell/plugins/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.plugins.enable-state' has path '/apps/shotwell/plugins/enable-state/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
Processing triggers for libglib2.0-0 ...
warning: Schema 'com.canonical.notify-osd' has path '/apps/notify-osd/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.ApplicationsLens' has path '/desktop/unity/lenses/applications/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Runner' has path '/desktop/unity/runner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.FilesLens' has path '/desktop/unity/lenses/files/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity' has path '/desktop/unity/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Launcher' has path '/desktop/unity/launcher/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Panel' has path '/desktop/unity/panel/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Devices' has path '/desktop/unity/devices/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.Unity.Dash' has path '/desktop/unity/dash/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.canonical.indicator.session' has path '/apps/indicator-session/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu-tweak.tweak' has path '/apps/ubuntu-tweak/tweak/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu-tweak.apps' has path '/apps/ubuntu-tweak/apps/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu-tweak.janitor' has path '/apps/ubuntu-tweak/janitor/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'com.ubuntu.update-manager' has path '/apps/update-manager/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard' has path '/apps/onboard/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.auto-show' has path '/apps/onboard/auto-show/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.keyboard' has path '/apps/onboard/keyboard/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window' has path '/apps/onboard/window/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window.landscape' has path '/apps/onboard/window/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window.portrait' has path '/apps/onboard/window/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette' has path '/apps/onboard/icon-palette/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.landscape' has path '/apps/onboard/icon-palette/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.portrait' has path '/apps/onboard/icon-palette/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.universal-access' has path '/apps/onboard/universal-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.theme-settings' has path '/apps/onboard/theme-settings/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.lockdown' has path '/apps/onboard/lockdown/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.scanner' has path '/apps/onboard/scanner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.Telepathy.Logger' has path '/apps/telepathy-logger/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.gstreamer-0.10.default-elements' has path '/desktop/gstreamer/0.10/default-elements/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.Vino' has path '/desktop/gnome/remote-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.cache' has path '/desktop/gnome/crypto/cache/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.pgp' has path '/desktop/gnome/crypto/pgp/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse' has path '/apps/seahorse/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse.manager' has path '/apps/seahorse/listing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.dns_sd' has path '/system/dns-sd/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.locale' has path '/system/locale/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy' has path '/system/proxy/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.http' has path '/system/proxy/http/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.https' has path '/system/proxy/https/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.ftp' has path '/system/proxy/ftp/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.socks' has path '/system/proxy/socks/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.smb' has path '/system/smb/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-piwigo' has path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-piwigo/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.org-yorba-shotwell-publishing-yandex-fotki' has path '/apps/shotwell/sharing/org-yorba-shotwell-publishing-yandex-fotki/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell' has path '/apps/shotwell/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences' has path '/apps/shotwell/preferences/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.ui' has path '/apps/shotwell/preferences/ui/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.slideshow' has path '/apps/shotwell/preferences/slideshow/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.window' has path '/apps/shotwell/preferences/window/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.files' has path '/apps/shotwell/preferences/files/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.crop-settings' has path '/apps/shotwell/crop-settings/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.preferences.editing' has path '/apps/shotwell/preferences/editing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing' has path '/apps/shotwell/sharing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.facebook' has path '/apps/shotwell/sharing/facebook/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.flickr' has path '/apps/shotwell/sharing/flickr/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.picasa' has path '/apps/shotwell/sharing/picasa/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.sharing.youtube' has path '/apps/shotwell/sharing/youtube/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.dataimports' has path '/apps/shotwell/dataimports/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.video' has path '/apps/shotwell/video/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.printing' has path '/apps/shotwell/printing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.plugins' has path '/apps/shotwell/plugins/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.yorba.shotwell.plugins.enable-state' has path '/apps/shotwell/plugins/enable-state/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
Processing triggers for gconf2 ...
Setting up winetricks (0.0+20120912~precise1~ppa1) ...
Setting up eog (3.4.2-0ubuntu1.1) ...
Setting up wine1.5 (1.5.13-0ubuntu1) ...
Setting up wine1.5-i386:i386 (1.5.13-0ubuntu1) ...
Setting up wine1.5-amd64 (1.5.13-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

### Post by NikTh on 2012-09-16
Hi , 
Please edit your post and put the results between [noparse]```
 brackets. 
```[/noparse]

[SIZE=3]**[noparse]```
The Results Here
```[/noparse] , **[SIZE=2]so can be readable.

Is this an upgrade from 10.04 ? Or a fresh install of 12.04 ? 

I can see a lot of warnings with schemas . 

Thanks
[/SIZE][/SIZE]

---

### Post by MarkoF on 2012-09-17
I've modified both posts with data with code fields, I hope it's more clear now.

It's completely fresh install. I downloaded .iso of 12.04 from ubuntu.com and burned it onto a DVD.

I also see those warnings, but I have no idea what they mean.

---

### Post by newb85 on 2012-09-17
And your Software Center still isn't working?

The warnings you're seeing seem to be associated with [this bug]("https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/1039722").

Is your version 12.04.1?

---

### Post by MarkoF on 2012-09-17
Still not working, still the same DBusException error. My Ubuntu version is 12.04.1 LTS.

I see, but it doesn't seem to affect Software center, as far as I understand...

---

### Post by NikTh on 2012-09-17
Hi , 
lets try 

  Please apply bellow commands with order and post here any errors. 
```
sudo apt-get purge software-center 
sudo apt-get --purge autoremove 
sudo apt-get install -f 
sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install --reinstall gsettings-desktop-schemas
sudo dpkg-reconfigure gsettings-desktop-schemas
sudo update-gconf-defaults
sudo apt-get install software-center
sudo dpkg-reconfigure software-center --force
```Thanks

---

### Post by commanderwil on 2012-09-18
I am new to Ubuntu and I had the same problem. Now, did you select to install updates and were you connected to the INTERNET when you installed Ubuntu? If you were not then you are going to need to reinstall Ubuntu :( or you can do what I did and search the entire Internet and put a lot of stuff in the terminal and not have you problem solved. If YOUR SURE you did choose to install updates AND you were connected to the Internet then I'm sorry but I can't help you.

And sense I'm saying what a Noob I am at Ubuntu I have a problem. I want to install stuff like Google chrome and adobe flash player. What do I use to open them on the open or run screen(I use Firefox). It says I should use archive manger but that doesn't work? please help!

hooray  for Noobs :lolflag:
You can email me at my school email ( I check it more than my normal email) [email]willschool105@gmail.com[/email]

---

### Post by newb85 on 2012-09-18
> **commanderwil said:**
> I want to install stuff like Google chrome and adobe flash player. What do I use to open them on the open or run screen(I use Firefox). It says I should use archive manger but that doesn't work? please help!

hooray  for Noobs :lolflag:
You can email me at my school email ( I check it more than my normal email) [email]willschool105@gmail.com[/email]

Your question is unrelated to the purpose of this thread.  You should have started a new thread (once you had searched to make sure an appropriate thread didn't already exist).

Chrome comes with flash support built-in, so you shouldn't need to install Adobe flash player.  (The Adobe flash plugin for Firefox can be installed through the Software Center--it's in the repos.)

Unless you have a specific reason for wanting Chrome over Chromium, it would be much easier to simply install Chromium through the Software Center (again, it's in the repos.)  They're virtually the same thing, except that Chromium is open-source and doesn't have Google's name all over it.

In the future, if you want help installing something you've downloaded from a website, you need to provide more information.  What kind of file is it?  Where did you download it?  That sort of info.

---

### Post by MarkoF on 2012-09-24
@NikTh

Sorry I haven't responded sooner, didn't have the Net this past week.
Anyway, tried what you told me. Didn't see any errors during the procedure, but still can't get SC to work. This time I've captured the very beginning of the process of application starting, I hope it will help.

```

marko@Marko-laptop:~$ software-center
2012-09-24 11:50:16,764 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-09-24 11:50:16,768 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-09-24 11:50:16,999 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-09-24 11:50:17,108 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-09-24 11:50:17,376 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 607, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 69, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-24 11:50:18,000 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-24 11:50:18,000 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-24 11:50:18,192 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-24 11:50:18,192 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-24 11:50:18,377 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'
2012-09-24 11:50:18,377 - dbus.connection - ERROR - Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 65, in signal_cb
    callback(new_owner)
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 156, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2012-09-24 11:50:18,574 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/connection.py', 234, 'maybe_handle_message')'

```



@commanderwil
I was connected to the Net at the moment of installation, and downloaded all the updates and third-party software.

---

