---
title: "Cant' get permissions to change"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by StephenG on 2008-10-21
Let's start with the understanding that this is my very first foray into Linux.  I've been using Windows for years now and that  was a changeover I resisted for many years as I was very comfortable before that with DOS and it's command lines.  I thought, for whatever reason, that Linux and I would get along since I had a love for an understanding of command lines.
I've had great deal of difficulty getting a Linksys wireless card installed and working.  I have followed all the Ubuntu threads on the WMP54G and virtually all of them include altering the file
/etc/network/interfaces
However, when I find the file and make the required line entries, the system refuses to accept the changes and gives me the error message
"You do not have the permissions necessary to save file."
I have gone into the User area and given all the permissions I can find to the one and only user on the system.  To no avail.
To further complicate matters, I can't even access the internet to download some of the suggested apps, like Network Manager, since I can't get the bloody wireless card to do anything at all.
I'm running out of ideas and need some advisory help.

StephenG

---

### Post by fr.theo on 2008-10-21
have you tried to use the sudo gedit /etc/network/interfaces in terminal, just remember that changing things that have a security feature may cause problems.

make sure you follow the instructions of the manufacturer or the site which issued you the instructions carefully.

---

### Post by handydan918 on 2008-10-21
The problem here is the Unix permissions model. You are attempting to edit a file you don't own. System-wide config files are always owned by root. This is one of the many security layers present in Linux that prevents the pwnage so widespread in the windows world.
Let's assume you are using gedit.
 Do ```
sudo gedit /etc/network/interfaces
```

ought to get it done.

---

### Post by phidia on 2008-10-21
You may also want to look at the wireless docs [here]("https://help.ubuntu.com/community/WifiDocs") and the links therein.

---

### Post by StephenG on 2008-10-21
I understand and appreciate the security aspects.  Will I need to re-command anything after I've made the changes, to get the permissions back to where they started?  Just make the changes and go on?  Reassign the permissions back to root?  Anything else?
Fr.Theo -- all the information I've gotten has been from right here on this forum.  Is there something I should be wary of (other than normal forum paranoia)?

---

### Post by fr.theo on 2008-10-21
As I have been told it is not a good idea to fiddle with the root privileges, so I would say return all that you have done as it was before. 

As soon as you make your changes to your file sudo won't keep the root privileges open but return you to your normal user mode and you will have to use sudo again if you wish to install or edit restricted files. 

Sorry just being cautious.

---

### Post by handydan918 on 2008-10-21
> **StephenG said:**
> I understand and appreciate the security aspects.  Will I need to re-command anything after I've made the changes, to get the permissions back to where they started?  Just make the changes and go on?  Reassign the permissions back to root?  Anything else?
Fr.Theo -- all the information I've gotten has been from right here on this forum.  Is there something I should be wary of (other than normal forum paranoia)?

Editing the file using sudo will not change the permissions/ownership of the file. All sudo does is temporarily elevate your user privileges so you can do admin tasks. Like edit system-wide config files. 
I think the security concern voiced above was in regard to network security and changing the default settings. 
It's your system, however; you can do anything you want, and if you break it, you can keep all the pieces....

---

### Post by StephenG on 2008-10-21
Ha!  Breaking it is exactly waht I'm trying to avoid.  So, I understand that using the "sudo" command will let me make the changes to the interfaces file without taking it out of the root directory or any other such insanity that might render the file unusable, etc?!?

---

### Post by greg@localhost on 2008-10-21
The file won't change - you have two users root and your user. The file is owned by root, therefore you need to be root to make changes to it. sudo will give you these priveliges temporarily.

---

### Post by madsc89 on 2008-10-21
Yes. To change some files, you need to open them using sudo.

The terminal command would then look like this:

```

sudo <your command>
```

Then you have to enter your password.

This doesn't change anything except what you change yourself.

It merely gives you the permission to change important files etc.

---

### Post by StephenG on 2008-10-21
Thank you all kindly.  I appreciate your patience.  I did get the file to change but the wireless card still baffles me.  I'll keep looking for that fix.  Maybe a differrent card and to heck with Linksys WMP54G?

---

### Post by greg@localhost on 2008-10-21
Have you tried using ndiswrapper?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by StephenG on 2008-10-21
Unless there's something written that's less technical and arcane than what I've found, it'll be a while until I can get that done.  As I said, I'm very comfortable with old DOS command line stuff, but Linux is a new world for me and I haven't got the time (as when I was a young unattached man) to sit around playing with things until I figure it out.  It just takes a bit longer, without a tutor.  If you know of some easily-understood directions, I'm game.  Right now, I'm in the process of installing 8.04, in the hopes that it might have some better drivers than did 7.10.  The machine is an old K6-300 and is chugging away as we speak.

---

### Post by handydan918 on 2008-10-23
> **StephenG said:**
> Ha!  Breaking it is exactly waht I'm trying to avoid.  So, I understand that using the "sudo" command will let me make the changes to the interfaces file without taking it out of the root directory or any other such insanity that might render the file unusable, etc?!?

Right. 
But.
Taking a file out of the root directory (or chowning it or whatever...) is less likely to render it unusable than it is to render it TOO usable, i.e., by unauthorized users! On a desktop system this may not be a huge deal, but you still want to be able to control who can make system-wide changes. 
Otherwise, you end up with the Windows security model....

---

