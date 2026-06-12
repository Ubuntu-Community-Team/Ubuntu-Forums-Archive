---
title: "Trying to set up a virtualbox shared folder"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-11-21
Hi there. I searched for other help places on this, but didn't find anything that worked, as far as I could tell.

I set up a virtualbox running xubuntu 11.10, and I want to be able to share files across my desktop (xubuntu 11.10) and the virtualbox.

How do I do this?

---

### Post by haqking on 2011-11-21
> **DaimyoKirby said:**
> Hi there. I searched for other help places on this, but didn't find anything that worked, as far as I could tell.

I set up a virtualbox running xubuntu 11.10, and I want to be able to share files across my desktop (xubuntu 11.10) and the virtualbox.

How do I do this?

make sure you have the extensions pack installed.

Then choose shared folders option, browse to folder you want to share.

the first step in doing anything is to read the documentation [http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by DaimyoKirby on 2011-11-21
:oops:*feeling kinda sheepish about forgetting about the manual*

Does my guest OS have to have the guest-extension-thing installed to be able to share the folder, or just my host OS?

Because the folder doesn't seem to be appearing in /media in the vbox, and there isn't a group called vboxsf...

---

### Post by F.G. on 2011-11-21
hmm, i think normally 'guest additions' is something you have to install to the guest OS, you can usually do that via the virtualbox menus while the guest os is running. 

then i think that you have to shut down the guest os, go to settings, 'shared folders' (at the bottom) and then you can add a path to whatever folder you want to be the shared folder (it can be some local folder you've made for the job).

something else good to be aware of is that if you want to use USB devices etc i think you need the PUEL licenced version, rather than the OSE one that comes in the repos.

---

### Post by DaimyoKirby on 2011-11-21
Well, I did, and I set up the folder, but it still isn't showing up in the media folder like the manual said it should.

---

### Post by F.G. on 2011-11-21
sorry, i can't help. i don't have VB etc at my disposal to play with. 
the folder might be elsewhere, as far as i recall they are mounted in the /home directory (or maybe the desktop), not /media (if that's where you'r looking) on the guest os.

---

### Post by andrew.46 on 2011-11-22
> **DaimyoKirby said:**
> Well, I did, and I set up the folder, but it still isn't showing up in the media folder like the manual said it should.

The key is to set the shared folder to mount *automatically*, this is done from the host system and I attach a screenshot to show this setting. This mounts my own shared folder automatically as /media/sf_samba and although the manual suggests that my username would be added to the group vboxsf I had to do this manually, by editing /etc/group, from within the guest system, to allowed to access the shared files. I finished off with a symlink on the Desktop for easy access to /media/sf_samba.

Hopefully this guides you through?

---

### Post by I_can_see_the_light on 2011-11-22
You could try mounting the share manually as well:

[FONT="Courier New"]mount -t vboxsf [-o OPTIONS] sharename mountpoint[/FONT]

---

### Post by DaimyoKirby on 2011-11-22
I made sure it was checked as *auto-mount*. When I loaded my vm, the folder didn't show up as I expected. When I looked for /etc/group though, there was no such directory or file...
And when I went into *System > Users and Groups*, there was no *vboxsf* group when I clicked "manage groups", just a *vboxusers* group.

Also, is a symlink basically just a link to another location on the computer, such as a folder or program?

---

### Post by Morbius1 on 2011-11-22
Post the output of the following command from the VBox guest:
```
ls -al /media
```

---

### Post by Morbius1 on 2011-11-22
Also, I finally understood another part of your last post:
>  And when I went into *System > Users and Groups*, there was no *vboxsf* group when I clicked "manage groups", just a *vboxusers* group.You're looking at the wrong OS. You will find the vboxsf group in the guest not the host.
> When I looked for /etc/group though, there was no such directory or file...Can't answer that one. Since you have Linux on both guest and host both have an /etc/group.

You did install VBox Guest Additions right. That is something you do after you boot into the guest from the guest. Not from the host.

---

### Post by DaimyoKirby on 2011-11-22
Ok, the output of that command from the guestOS is:
```

xubuntu@xubuntu-VirtualBox:~$ ls -al /media
total 8
drwxr-xr-x  2 root root 4096 2011-10-12 17:46 [COLOR="rgb(72, 61, 139)"].[/COLOR]
drwxr-xr-x 23 root root 4096 2011-11-23 01:06 [COLOR="DarkSlateBlue"]..[/COLOR]

```

Now, that was when I was checking in my GuestOS. In both my guest and host OS I have "Guest additions iso image for VirtualBox (virtualbox-guest-additions-iso)" installed, underneath the package "x86 virtualization solution - base binaries" in the Ubuntu Software Center, (as I assume that is the guest additions package everyone talks about) although since vboxsf isn't showing up, I'm guessing that isn't what I'm looking for.

Also, if it makes any difference, I set up my vm using the premade Xubuntu 11.10 vdi [here]("http://virtualboxes.org/images/xubuntu/#xu1110").

---

### Post by andrew.46 on 2011-11-22
> **DaimyoKirby said:**
> I made sure it was checked as *auto-mount*. When I loaded my vm, the folder didn't show up as I expected.

Odd, which version of VirtualBox are you using?


> When I looked for /etc/group though, there was no such directory or file...
And when I went into *System > Users and Groups*, there was no *vboxsf* group when I clicked "manage groups", just a *vboxusers* group.

In your *[COLOR="Red"]**guest**[/COLOR]* system try the following command:

```

andrew@corinth:~$ **[COLOR="Red"]grep -i 'vbox*' /etc/group[/COLOR]**
vboxsf:x:1001:andrew


```

> Also, is a symlink basically just a link to another location on the computer, such as a folder or program?

Exactly!

```

andrew@corinth:~/Desktop$ **[COLOR="Red"]ls -l sf_samba[/COLOR]**
lrwxrwxrwx 1 andrew andrew 16 2011-11-22 18:44 sf_samba -> /media/sf_samba/

```

---

### Post by DaimyoKirby on 2011-11-22
I'm using VirtualBox 4.1.2_Ubuntu r38459.

```

xubuntu@xubuntu-VirtualBox:~$ grep -i 'vbox*' /etc/group
[COLOR="Red"]vbox[/COLOR]users:x:125:xubuntu

```

---

### Post by andrew.46 on 2011-11-22
I have no experience with those 'pre-packed' VM's, my own have always been installed by myself. And I install VirtualBox directly from the Oracle site rather than from the Ubuntu repository:

[http://download.virtualbox.org/virtualbox/4.1.6/](http://download.virtualbox.org/virtualbox/4.1.6/)

If you cannot resolve this issue this presents an alternative path perhaps?

---

### Post by haqking on 2011-11-22
> **andrew.46 said:**
> I have no experience with those 'pre-packed' VM's, my own have always been installed by myself. And I install VirtualBox directly from the Oracle site rather than from the Ubuntu repository:

[http://download.virtualbox.org/virtualbox/4.1.6/](http://download.virtualbox.org/virtualbox/4.1.6/)

If you cannot resolve this issue this presents an alternative path perhaps?

+1

Install the .deb or add the PPA, install extension pack and be done with it.

---

### Post by DaimyoKirby on 2011-11-22
Ok, I guess I try restarting. I'll also try building a vm from scratch.
If I download *Oracle_VM_VirtualBox_Extension_Pack-4.1.6-74713.vbox-extpack* and *virtualbox-4.1_4.1.6-74713~Ubuntu~oneiric_i386.deb*, do I also need *VBoxGuestAdditions_4.1.6.iso*?

---

### Post by andrew.46 on 2011-11-22
These are for 32bit OS so I assume this is what you are running? As well as the 3 files you mentioned (and yes you will need the Guest Additions iso) might not be a bad idea to download the manual as well. Good luck with this :)

---

### Post by DaimyoKirby on 2011-11-23
Yeah, I believe that's what I'm running. I tried looking up about it [here]("https://help.ubuntu.com/community/32bit_and_64bit"), and it returned *lm*, so I'm not exactly sure, but as far as I know I've always been using 32-bit stuff. Would it be good for me to [enable PAE]("https://help.ubuntu.com/community/EnablingPAE"), or switch to 64 bit, or something?
Well, when I downloaded the deb file, and opened it in Ubuntu Software Center, it opened me to a file called *virtualbox-4.1*, and the description reads "Breaks existing package 'virtualbox-guest-additions-iso' conflict: virtualbox-4.1 ()", and whenever I click install, it just hangs there, and nothing happens.

---

