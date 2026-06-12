---
title: "Software Center"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by kiddcanuk on 2013-05-28
I am running 12.10 and when I click Software Center it does nothing.

Thanks in advance,

Redd

---

### Post by KnownSyntax on 2013-05-29
Are you just clicking on it once or double clicking? Sometimes you may think you clicked on it but you just "tabbed" it to-say.

---

### Post by Locus Kiesselbachi on 2013-05-29
Try opening software center via terminal. Ctrl+T to open terminal.
try typing
```
software-center
```
Does it open? 
If not, copy terminal answer (command response answer) in to this thread.

Uncle Google knows. :)
[**source**]("http://askubuntu.com/questions/231695/how-do-i-open-ubuntu-software-center-via-terminal")

---

### Post by kiddcanuk on 2013-05-29
Nope. Nothing. But here is what came up.

ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 27, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named bauer-puntu
Traceback (most recent call last):
  File "/usr/bin/software-center", line 128, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 53, in <module>
    from softwarecenter.db.application import Application
  File "/usr/share/software-center/softwarecenter/db/application.py", line 27, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named bauer-puntu
shiffty@shiffty-System-Product-Name:~$

---

### Post by Bashing-om on 2013-05-29
[COLOR=#000000]kiddcanuk; Hi !

Appears you may have to (re-)install software-center. But, before doing so let us make sure there are no underling problems.
Thus: ctl+alt+t yields a command line interface
What results from terminal codes:
```
sudo apt-get update
sudo apt-get upgrade
``` this refreshes the package managers' data base and upgrades installed packages ?

If errors, post them back to us completely, using the code (#) tags at top of post.
[/COLOR][INDENT][COLOR=#000000]
so begins a tale in the telling

[/COLOR][/INDENT]

---

### Post by kiddcanuk on 2013-05-29
Did what you asked. Update worked, but when I went to do an up grade this is what I got.

shiffty@shiffty-System-Product-Name:~$ sudo apt-get update
[sudo] password for shiffty: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                           
Hit [http://www.remastersys.com](http://www.remastersys.com) oneiric Release.gpg                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg       
Hit [http://www.remastersys.com](http://www.remastersys.com) oneiric Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                       
Hit [http://www.remastersys.com](http://www.remastersys.com) oneiric/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en         
Ign [http://www.remastersys.com](http://www.remastersys.com) oneiric/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://www.remastersys.com](http://www.remastersys.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Reading package lists... Done
shiffty@shiffty-System-Product-Name:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shiffty@shiffty-System-Product-Name:~$

---

### Post by Bashing-om on 2013-05-30
Hey [COLOR=#000000]kiddcanuk ;[/COLOR]

That all looks good, no problems with the base package management system. Try this and see if it resolves your situation:
```
sudo apt-get install --reinstall software-center
``` Per "apt-get upgrade" you have no pending updates at that time.[INDENT=3]
reboot and be happy

[/INDENT]

---

### Post by Locus Kiesselbachi on 2013-05-30
Bashing-om is good guy, once he helped me too. :D
My recommendations!

---

### Post by kiddcanuk on 2013-05-30
Hi again! Ok here's what I got:


shiffty@shiffty-System-Product-Name:~$ sudo apt-get install --reinstall software-center
[sudo] password for shiffty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 628 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main software-center all 5.4.1.4 [628 kB]
Fetched 628 kB in 1s (319 kB/s)          
(Reading database ... 310728 files and directories currently installed.)
Preparing to replace software-center 5.4.1.4 (using .../software-center_5.4.1.4_all.deb) ...
Unpacking replacement software-center ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up software-center (5.4.1.4) ...
ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 27, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named bauer-puntu
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 38, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 33, in <module>
    from softwarecenter.backend.scagent import SoftwareCenterAgent
  File "/usr/share/software-center/softwarecenter/backend/scagent.py", line 28, in <module>
    from softwarecenter.distro import get_distro, get_current_arch
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named bauer-puntu
shiffty@shiffty-System-Product-Name:~$ 


Hope this helps. Totally lost!

---

### Post by kiddcanuk on 2013-06-02
Hi again! Ok here's what I got:


shiffty@shiffty-System-Product-Name:~$ sudo apt-get install --reinstall software-center
[sudo] password for shiffty:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 628 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main software-center all 5.4.1.4 [628 kB]
Fetched 628 kB in 1s (319 kB/s)
(Reading database ... 310728 files and directories currently installed.)
Preparing to replace software-center 5.4.1.4 (using .../software-center_5.4.1.4_all.deb) ...
Unpacking replacement software-center ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up software-center (5.4.1.4) ...
ERROR:rootebFileApplication import
Traceback (most recent call last):
File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
from debfile import DebFileApplication, DebFileOpenError
File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
from softwarecenter.db.application import Application, AppDetails
File "/usr/share/software-center/softwarecenter/db/application.py", line 27, in <module>
import softwarecenter.distro
File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
distro_instance = _get_distro()
File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named bauer-puntu
Traceback (most recent call last):
File "/usr/sbin/update-software-center", line 38, in <module>
from softwarecenter.db.update import rebuild_database
File "/usr/share/software-center/softwarecenter/db/update.py", line 33, in <module>
from softwarecenter.backend.scagent import SoftwareCenterAgent
File "/usr/share/software-center/softwarecenter/backend/scagent.py", line 28, in <module>
from softwarecenter.distro import get_distro, get_current_arch
File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 197, in <module>
distro_instance = _get_distro()
File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 172, in _get_distro
module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named bauer-puntu
shiffty@shiffty-System-Product-Name:~$


Hope this helps. Totally lost!

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]kiddcanuk; Sorry, I somehow lost track of you in all the shuffle !

The trace back throws me for a loop too.
Presently I have no idea what
[/COLOR]> [COLOR=#000000]ImportError: No module named bauer-puntu[/COLOR][COLOR=#000000]
means. -it sure is a strange name for a "module" - Will need to do some research and looking before I can advise further.

I will return as soon as possible.[/COLOR][INDENT=3][COLOR=#000000]
regards

[/COLOR][/INDENT]

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]kiddcanuk;

Hey, "[/COLOR][COLOR=#000000]bauer-puntu" is a spin off version of 'buntu.. let's take a look at the source get files and see if that sheds any more light on this.
```
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/ 
```
[/COLOR][INDENT=2][COLOR=#000000]
curious is as curious does

[/COLOR][/INDENT]

---

### Post by kiddcanuk on 2013-06-04
Here is what it says:

shiffty@shiffty-System-Product-Name:~$ cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ quantal main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) oneiric main

deb [http://ppa.launchpad.net/ssakar/ppa/ubuntu](http://ppa.launchpad.net/ssakar/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ssakar/ppa/ubuntu](http://ppa.launchpad.net/ssakar/ppa/ubuntu) lucid main
shiffty@shiffty-System-Product-Name:~$ 

Then I got this:

shiffty@shiffty-System-Product-Name:~$ ls -la /etc/apt/sources.list.d/
total 32
drwxr-xr-x 2 root root 4096 Oct 22  2012 .
drwxr-xr-x 6 root root 4096 Apr 27 23:06 ..
-rw-r--r-- 1 root root  134 Oct 22  2012 bitcoin-bitcoin-quantal.list
-rw-r--r-- 1 root root  134 Oct 22  2012 bitcoin-bitcoin-quantal.list.save
-rw-r--r-- 1 root root  176 Oct 22  2012 google-chrome.list
-rw-r--r-- 1 root root  176 Oct 22  2012 google-chrome.list.save
-rw-r--r-- 1 root root  174 Oct 22  2012 gwendal-lebihan-dev-cinnamon-stable-quantal.list
-rw-r--r-- 1 root root  174 Oct 22  2012 gwendal-lebihan-dev-cinnamon-stable-quantal.list.save
shiffty@shiffty-System-Product-Name:~$ 

Hope this helps you.Thanks!

---

### Post by Bashing-om on 2013-06-04
[COLOR=#000000]kiddcanuk; In your sources.list file at the end is:
[/COLOR]> 
[COLOR=#000000]deb [/COLOR][http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu)[COLOR=#000000] oneiric main[/COLOR]

[COLOR=#000000]deb [/COLOR][http://ppa.launchpad.net/ssakar/ppa/ubuntu](http://ppa.launchpad.net/ssakar/ppa/ubuntu)[COLOR=#000000] lucid main[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://ppa.launchpad.net/ssakar/ppa/ubuntu](http://ppa.launchpad.net/ssakar/ppa/ubuntu)[COLOR=#000000] lucid main
[/COLOR][COLOR=#000000]

I bet those archives are no longer maintained, and trying to load "old" version software is generally not a good idea.

What results if you comment out (place a '#' at the start of the line) those 3 offending lines - in your favorite text editor ?
Remember to make a copy of any file one edits, never can tell what might happen ! 

ssakar ppa last supported version was maveric
remastersys is no longer maintained, however if you want to continue to use it ...see the directions avail at:
[http://www.remastersys.com](http://www.remastersys.com)
[/COLOR][INDENT=2][COLOR=#000000]

how bout that ?

[/COLOR][/INDENT]

---

