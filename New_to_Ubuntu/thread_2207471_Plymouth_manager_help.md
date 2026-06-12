---
title: "Plymouth manager help"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by Project_ICE on 2014-02-23
So yeah. My expeince level with linux and ubuntu is fairly limited. seeing that I have just started using it two days ago. I may be in over me head here trying to do whatever it is that I am doing but oh well.

[TABLE="class: code-table, align: left"]
[TR]
[TD] sudo add-apt-repository ppa:mefrio-g/plymouthmanager
                          >  In this ppa you can find the latest stable release of Plymouth Manager

To add it type in a terminal:

- sudo apt-add-repository ppa:mefrio-g/plymouthmanager
- sudo apt-get update
- sudo apt-get install plymouth-manager


 More info: [https://launchpad.net/~mefrio-g/+archive/plymouthmanager](https://launchpad.net/~mefrio-g/+archive/plymouthmanager)
Press [ENTER] to continue or ctrl-c to cancel adding it

                       > gpg: keyring `/tmp/tmp229zxf/secring.gpg' created
gpg: keyring `/tmp/tmp229zxf/pubring.gpg' created
gpg: requesting key 849919D3 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp229zxf/trustdb.gpg: trustdb created
gpg: key 849919D3: public key "Launchpad PPA for Mario Guerriero" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK




 [/TD]
[/TR]
 [TR]
[TD] sudo apt-get update
                  at the end of the update i get this
                 > W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.





 [/TD]
[/TR]
 [TR]
[TD] sudo apt-get install plymouth-manager
                      > Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package plymouth-manager







Im not sure if I am doing something wrong....or theres just a glitch.
Or maybe this way is outdated. 

All I am trying to do is to change the boot/splash

[/TD]
[/TR]
[/TABLE]

---

### Post by Vladlenin5000 on 2014-02-23
The PPA you added has no packages for your Ubuntu version - no surprise considering it isn't updated since 2011 - so... First of all what is your intended purpose for installing that software?

---

### Post by Dennis N on 2014-02-23
> All I am trying to do is to change the boot/splash

There are some themes (called Plymouth themes) available in the Ubuntu Software Center. As I recall, whatever you install becomes your new theme.

Search for **plymouth-theme** to see what's available.

A fairly nice one among those offered is Solar. Search for **plymouth-theme-solar**

---

### Post by Project_ICE on 2014-02-23
> **Dennis N said:**
> There are some themes (called Plymouth themes) available in the Ubuntu Software Center. As I recall, whatever you install becomes your new theme.

Search for **plymouth-theme** to see what's available.

A fairly nice one among those offered is Solar. Search for **plymouth-theme-solar**

I installed the one you mentioned. plymouth-theme-solar. I rebooted and nothing changed. do I have to activate it somehow?


Also, Since what i previously tried didnt work. how do i remove whatever i did as far as the plymouth manager goes. every time i do sudo apt-get update it keeps saying that

---

### Post by Vladlenin5000 on 2014-02-23
In order to remove a PPA just run the same *apt-add-repository *command with the *--remove* option. There's no need to go further than that since you actually didn't install stuff from that PPA.
```
sudo apt-add-repository --remove ppa:mefrio-g/plymouthmanager
```

Regarding your other question I have no idea, i never messed with those things but I would like to know too.

---

### Post by deadflowr on 2014-02-23
> **Project_ICE said:**
> I installed the one you mentioned. plymouth-theme-solar. I rebooted and nothing changed. do I have to activate it somehow?


Also, Since what i previously tried didnt work. how do i remove whatever i did as far as the plymouth manager goes. every time i do sudo apt-get update it keeps saying that


To change try 
```
sudo update-alternatives --config default.plymouth
``` 				 

and select the new one if in there.

But on another topic, what about sudo apt-get update?
That statement seems to have been cut off.

But if, as I think it does, it  was going to say that apt-get updates keeps saying you have updates to install, then yes it would.
sudo apt-get update doen't update the packages, it only get refreshes the information of what packages can be updated.
To actually update the packages run
```
sudo apt-get upgrade
```

Mind you, I'm only speculating here, as the post seemed to be cut off.

---

### Post by Project_ICE on 2014-02-24
> **Vladlenin5000 said:**
> In order to remove a PPA just run the same *apt-add-repository *command with the *--remove* option. There's no need to go further than that since you actually didn't install stuff from that PPA.
```
sudo apt-add-repository --remove ppa:mefrio-g/plymouthmanager
```

Regarding your other question I have no idea, i never messed with those things but I would like to know too.


Worked like a charm. Thanks!

---

### Post by Project_ICE on 2014-02-24
> **deadflowr said:**
> To change try 
```
sudo update-alternatives --config default.plymouth
```                  

and select the new one if in there.


Also worked perfectly. Thanks

---

### Post by Project_ICE on 2014-02-24
Maybe one of you could figure this out too. I had installed Intel-gpu-tools from 01.org. Its pretty much an update for intel drivers. I since have removed it though and i still get this at the bottom of my update

> W: GPG error: [https://download.01.org](https://download.01.org) saucy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366



---

### Post by Dennis N on 2014-02-24
> I installed the one you mentioned. plymouth-theme-solar. I rebooted and nothing changed. do I have to activate it somehow?
Yes. The command deadflowr gave did it. Thanks deadflowr. I had thought it was part of the install.

The selection in the repository is limited. If you are interested in additional themes, visit **gnome-look.org** and select category "splash screens" on the left. earth-sunrise is one I am using on Ubuntu now. These can require more steps to manually install, but it's not difficult.

Enjoy your new splashscreen.

---

### Post by deadflowr on 2014-02-24
Yeah, the update-alternatives command is probably mentioned somewhere.
Whether that somewhere is in a review in the Ubuntu Software Center or the description of synaptic, or one of those quick lines that come and go doing an apt-get install.
I don't remember, but I know I've used it, so I happened to have it in my history.

> **Project_ICE said:**
> Maybe one of you could figure this out too. I had installed Intel-gpu-tools from 01.org. Its pretty much an update for intel drivers. I since have removed it though and i still get this at the bottom of my update

Perhaps you need to disable the 01.org added repository.
Easiest is to open software sources and go to the section "other software"
It should be listed here, uncheck it if it isn't already.
Once that's done, the key won't matter.
But if want, you can remove the key as well, by going to the next tab authentication and removing the key there.
Be careful, though if removing the key. remove the wrong one and no more updates.

If you need help opening software sources, type this in a terminal
```
software-properties-gtk
```
or open the update manager and go to the button that says settings.
(If on 12.10 or newer you should be able to just launch the program called " Software and Updates")

Hope this makes some sort of sense.

---

