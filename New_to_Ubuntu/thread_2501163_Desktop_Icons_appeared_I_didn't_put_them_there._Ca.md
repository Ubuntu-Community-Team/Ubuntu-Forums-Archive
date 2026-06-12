---
title: "Desktop Icons appeared I didn't put them there. Can't delete"
date: 2024-09-25
forum: New to Ubuntu
---

### Post by ence on 2024-09-25
Hello 

I don't know how this happened I got Four folders on desktop I didn't put them there.
They the same folder from my Home folder.

I can delete from desktop but they deleted from Home folder what I don't want do.
I ask Chat GPT said to load Tweeks but that keeps crashing and will not open, Then Chat said to load dconf-editor but that won't open too after loading.

Just don't want folders on desktop. 
Also did right click on screen but can't see any thing to get rid of folders.

Any help Thanks

Also on update get errors [IMG]https://ibb.co/z4Vdbgx[/IMG][IMG]https://ibb.co/d28NZXM[/IMG]
add images of errors 
[https://ibb.co/z4Vdbgx](https://ibb.co/z4Vdbgx)
[https://ibb.co/d28NZXM](https://ibb.co/d28NZXM)
[IMG]https://ibb.co/z4Vdbgx[/IMG]

---

### Post by 1fallen on 2024-09-25
Please run this:
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```
If that don't remove them, show this then:
```
ls Desktop
```

---

### Post by ence on 2024-09-25
delete
[IMG]https://ibb.co/d28NZXM[/IMG]

---

### Post by ence on 2024-09-25
Hello 1fallen2 

Type that in Terminal - gsettings set org.gnome.desktop.background show-desktop-icons false

Myname:~$ gsettings set org.gnome.desktop.background show-desktop-icons false
Myname:~$ sudo gsettings set org.gnome.desktop.background show-desktop-icons false
[sudo] password for Myname: 


(process:29969): dconf-WARNING **: 17:32:01.785: failed to commit changes to dconf: Failed to execute child process &#8220;dbus-launch&#8221; (No such file or directory)
Myname:~$ ls Desktop
ls: cannot access 'Desktop': No such file or directory

Sorry I don't realy understand all this.

---

### Post by ence on 2024-09-25
Hello 1fallen2 

:~$ gsettings set org.gnome.desktop.background show-desktop-icons false
~$ .gnome.desktop.background show-desktop-icons false
.gnome.desktop.background: command not found
:~$ gsettings set org.gnome.desktop.background show-desktop-icons false
:~$ gnome-extensions list | grep desktop-icons


~$ ls Desktop << Computer doesn't like this 


ls: cannot access 'Desktop': No such file or directory




:~$ gnome-extensions disable desktop-icons@csoriano
Extension &#8220;desktop-icons@csoriano&#8221; does not exist
:~$ gnome-extensions disable ding @ rastersoft.com
:~$ 



They gone now with this - $ gnome-extensions disable ding @ rastersoft.com copy from Chat.

Thanks

---

### Post by 1fallen on 2024-09-25
Your Update errors are due to some bad PPA's
Can you remove those?
2nd your system looks to be in state of Kaos, possible bad upgrade.
3rd I never told you to use "sudo" with gsettings, Please be careful with your use of "sudo"

Lets look at your sources first:
In Code Tags show this please:
```
inxi -r
```

Quick Tip for Code tags>>>[noparse]```
your paste here
```[/noparse]

---

### Post by ence on 2024-09-25
I see lot video on youtube they all type Sudo. Thought I had do that.


```
 Repos:  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/protonvpn-stable.list
    1: deb [signed-by=/usr/share/keyrings/protonvpn-stable-archive-keyring.gpg] https://repo.protonvpn.com/debian stable main
  Active apt repos in: /etc/apt/sources.list.d/embrosyn-ubuntu-xapps-noble.sources
    1: deb https://ppa.launchpadcontent.net/embrosyn/xapps/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/savoury1-ubuntu-xapps-noble.sources
    1: deb https://ppa.launchpadcontent.net/savoury1/xapps/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/teejee2008-ubuntu-timeshift-noble.sources
    1: deb https://ppa.launchpadcontent.net/teejee2008/timeshift/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/ubuntu.sources
    1: deb http://gb.archive.ubuntu.com/ubuntu/ noble noble-updates main restricted universe multiverse
    2: deb http://security.ubuntu.com/ubuntu/ noble-security main restricted multiverse universe

```

---

### Post by deadflowr on 2024-09-25
The 2 xapps ppas need to be removed as they have no archive for noble.

the timeshift ppa probably needs to be reloaded as they should have updated the key requirements to rsa2048.
I think the simple way is to simply remove the ppa and re-add it.
Which should bring in the updated key.

---

### Post by ence on 2024-09-25
I loaded timeshift when first installed as wanted to go back if got problems but was filling up hard drive. I wanted it to backup not and then to exdrive.
Off to Google see about remove ppas.

Thanks

---

### Post by ence on 2024-09-25
```
Reading package lists... DoneE: The repository 'https://ppa.launchpadcontent.net/embrosyn/xapps/ubuntu noble Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://ppa.launchpadcontent.net/savoury1/xapps/ubuntu noble Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: https://ppa.launchpadcontent.net/teejee2008/timeshift/ubuntu/dists/noble/InRelease: Signature by key 1B32B87ABAEE357218F6B48CB5B116B72D0F61F0 uses weak algorithm (rsa1024)

```

Computer showing errors and I don't know what I'm doing! So be quicker in long run copy data off computer and rebuild. 
Thanks both

---

### Post by 1fallen on 2024-09-25
BTW Timeshift is in our stock repos, no PPA needed.
```
apt search timeshift
timeshift/oracular 24.06.2-1 amd64
  System restore utility



```

---

### Post by ence on 2024-10-01
I got look how setup Time shift
Thanks 1fallen2

---

