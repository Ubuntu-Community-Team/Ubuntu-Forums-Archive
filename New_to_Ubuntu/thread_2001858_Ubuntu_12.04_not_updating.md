---
title: "Ubuntu 12.04 not updating"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by joetait on 2012-06-11
Hi

In short, I can't get my Ubuntu to update. The update manager tells me there are no updates, which would be fine, but I am concerned about the odd behaviour from the terminal. When I try 
```

sudo apt-get update

```then it just says [waiting for headers], all the way to the edge of the screen (and off of it). Sometimes it will get up to 18%, and then just stay there indefinitely.

Any ideas as to why it is doing this would be much appreciated :)

When it does get anywhere, many of them have fail messages, such as: 
```

Err http://ubuntu.mirror.cambrium.nl precise Release.gpg                                                                                             
  Connection failed

```

---

### Post by arochester on 2012-06-11
Your details say you are in Southampton and you are using a repository in the Netherlands?

Change your repository. 

Do you have Synaptic Package Manager? Synaptic>Download from (change to Server for the UK) ...or choose Other>Select Best Server. It will run through a series of tests to find the quickest. This can change with the time of day etc.

---

### Post by joetait on 2012-06-12
Okay, I have changed that (Thank you very much for the spot), but it still seems to be having big issues trying to update.

It got to 24%, and is now going back down (currently at 19%), with a large number of errors
```

Err http://gb.archive.ubuntu.com precise Release.gpg                                                             
  Connection failed
Err http://gb.archive.ubuntu.com precise-updates Release.gpg                                                     
  Connection failed
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                       
Err http://gb.archive.ubuntu.com precise-backports Release.gpg                                                   
  Connection failed
Err http://ppa.launchpad.net precise Release.gpg                                                                 
  Connection failed
Err http://gb.archive.ubuntu.com precise-security Release.gpg                                                    
  Connection failed
Ign http://gb.archive.ubuntu.com precise Release                                                                 
Err http://ppa.launchpad.net precise Release.gpg                                                                 
  Connection failed

```for example.

It also has errors like
```

Err http://archive.canonical.com precise Release.gpg                                                            
  Bad header line

```
and it is also still coming up with a lot messages saying [waiting for headers].
Again, any ideas would be much appreciated :)

---

### Post by wilee-nilee on 2012-06-12
Post the sources.list with running.

```
cat /etc/apt/sources.list
```

---

### Post by joetait on 2012-06-12
> **wilee-nilee said:**
> Post the sources.list with running.

```
cat /etc/apt/sources.list
```


Okies, the output from that is:
```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de2.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de2.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de2.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise universe
deb http://de2.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de2.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://de2.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de2.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://de2.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://de2.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://de2.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://de2.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://repository.spotify.com stable non-free # disabled on upgrade to precise

```

---

### Post by wilee-nilee on 2012-06-12
you might try to just save that list and use a new one from this source generator.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

To open the source list as a read and write run.

```
sudo gedit /etc/apt/sources.list
```

Personally I would just open it save all that is there to a gedit store wherever and insert the new one.

---

### Post by joetait on 2012-06-12
Okay, I tried changing the sources.list file as suggested, and it is still doing exactly the same.

Also, I have tried updating with a different Internet connection, and that is not working either, which implies it is the computers fault that there is a connection failure.

Any more suggestions would be greatly appreciated :)

EDIT: I assume that this is related, so extra info - the update manager has managed to come up with two firefox updates, but it refuses to carry out the update since it can't authenticate the packages.

---

### Post by wilee-nilee on 2012-06-12
> **joetait said:**
> Okay, I tried changing the sources.list file as suggested, and it is still doing exactly the same.

Also, I have tried updating with a different Internet connection, and that is not working either, which implies it is the computers fault that there is a connection failure.

Any more suggestions would be greatly appreciated :)

Use the software sources again and run the select best server option, and use the one it finds.

If you are getting gpg errors and a key that looks somewhat like this.```
AED4B06F473041FA
```   Use this key loader command with your own missing key, or keys individually, then run the update again.                               ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AED4B06F473041FA
```Then run a update in the terminal, and post all the text including the update command if you are still having problems.

It may be that the cache needs to be removed as well, on that here is a link.
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/198060](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/198060)

---

### Post by joetait on 2012-06-12
I have selected the suggested server from synaptics.

I am not getting any keys, so I guess that there are no gpg errors (though it is sometimes saying connection failed, where the previous line was a .gpg file).

I followed the instructions for resetting the cache, but then at the command
```

LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824

```

it behaves in a similar manner as when trying to update. The output from that command is:

```

joe@joe-laptop:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
Ign http://extras.ubuntu.com precise InRelease                                                                                        
Ign http://archive.canonical.com oneiric InRelease                                                                                    
Ign https://private-ppa.launchpad.net precise InRelease                                                                               
Err http://extras.ubuntu.com precise Release.gpg                                                                                      
  Connection failed
Ign https://private-ppa.launchpad.net precise Release.gpg                                                                             
Ign https://private-ppa.launchpad.net precise Release                                                                                 
Ign http://packages.medibuntu.org precise InRelease                                                                                    
Err http://packages.medibuntu.org precise Release.gpg                                                                                  
  Connection failed
Ign http://archive.canonical.com precise InRelease                                                                                     
Ign http://repository.spotify.com stable InRelease                                                                                     
Ign http://ubuntu.mirrors.uk2.net precise InRelease                                                                                    
Ign http://ppa.launchpad.net precise InRelease                                                                                         
Ign http://extras.ubuntu.com precise Release                                                                                           
Err http://repository.spotify.com stable Release.gpg                                                                                   
  Connection failed
Ign http://repository.spotify.com stable Release                                                                                       
Ign https://private-ppa.launchpad.net precise/main TranslationIndex                                                                    
Ign http://packages.medibuntu.org precise Release                                                                                      
Err http://archive.canonical.com oneiric Release.gpg                                                                                   
  Connection failed
Ign http://ppa.launchpad.net precise InRelease                                                                                         
Err http://archive.canonical.com precise Release.gpg                                                                                   
  Connection failed
Ign http://ppa.launchpad.net precise InRelease                                                                                         
19% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]


```

EDIT: I have got another, different error too:
```


Err https://private-ppa.launchpad.net precise/main i386 Packages                                                                       
  Received HTTP code 0 from proxy after CONNECT

```

---

### Post by dtohjam on 2012-06-25
I think that you may have a proxy issue.
I solved this problem here... but not an elegant solution and some advice is appreciated;

see...
[http://ubuntuforums.org/showthread.php?t=1844030](http://ubuntuforums.org/showthread.php?t=1844030)

---

### Post by brakensi on 2012-08-21
I ran into the same problem. I could not update after a fresh install. The following worked for me. 

[http://www.upubuntu.com/2012/06/how-to-configure-ubuntu-to-update.html](http://www.upubuntu.com/2012/06/how-to-configure-ubuntu-to-update.html)

---

### Post by marlow59 on 2012-08-21
Did you give a try the Synaptic package manager option?

---

