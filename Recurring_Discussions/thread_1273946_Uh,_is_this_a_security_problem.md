---
title: "Uh, is this a security problem?"
date: 2009-09-24
forum: Recurring Discussions
---

### Post by chessnerd on 2009-09-24
In Ubuntu you can edit the Applications and System menus without being root using the menu editor. This doesn't seem like much of a problem, but I was thinking about it and noticed that you can edit anything about the menus without having root privileges. In fact, you can even change the commands that the menu icons link to without giving your password. I think this could be a major security problem...

Let's say that I am trying to create a piece of malware for Linux that runs a dangerous command. The main problem with that is that, for almost all devastating commands, you need to be root. It's one of the great things about Linux and is probably its greatest security strength. However, let's say I wrote a program that went into the configuration file for the menus and changed something--let's say Synaptic's link--to instead run a dangerous command proceeded with "gksu." If the person clicked on it it would prompt them for their admin password, nothing unusual for Synaptic, and when they typed it in the command would execute with root privileges. Depending on the command it could unblock their firewall, delete all their files, send all their files to someone over the Internet, cause memory usage to skyrocket until the system crashed, etc.

Is this a legitimate security concern or would it be impossible for someone to implement this?

---

### Post by Sean Moran on 2009-09-24
Interesting concept.  It strikes me as a rather naive thing for someone to do to install legitimate Linux on a system, and then install a third-party application on their system that then asks for an admin password, but the chances are that if there could ever be reason for such an operation. someobody out there willl eventually fall for it and do it.

Regarding the menus and  panel, please don't take me as an expert on Ubuntu desktops at this stage, but I believe that the menus and panel settings can be found in the ~/.gconf 'folder' inside the user's home 'folder', so a user may change the configuration of his or her own menus and panels, and it has no effect on the system at large.

As for such things as writing a little script to sudo rm -rf the system, well that would be a case of buyer beware if it wasn't free to begin with.

These sorts of concerns are most interesting to discuss, although I have a bit of faith that there are many developers with much more expertise than myself taking care of things like security.  There I go being naive.  

Two different concerns mentioned really, if I read right.  
1. Changing your menus doesn't change anyone else's on the same machine, as far as I am aware.
2. Installing unrecommended malware onto your pride and joy is not a very wise idea either.

Still an interesting subject to consider, and I maybe totally wrong.

---

### Post by FuturePilot on 2009-09-24
This exact scenario has been discussed many many times. Check Recurring Discussions. There's at least 5 threads on this.

---

### Post by p_quarles on 2009-09-24
It's easier than all that, actually. You can easily change what common commands like "cp" or "rm" do by writing a few lines to .bashrc and symlinking the command to a malicious script. 

Normal user privileges in Linux allow attackers to do a great deal of very harmful things. A lot of people underestimate this.

---

### Post by inobe on 2009-09-24
not a security issue at all, for example' can you change your screensaver or background or log onto an unsecured network, what about creating a personalized launcher..........


it's a user account without privileges that correspond to root.

---

### Post by chessnerd on 2009-09-24
> **FuturePilot said:**
> This exact scenario has been discussed many many times. Check Recurring Discussions. There's at least 5 threads on this.

Really? I did a check before I posted just for that. I tried things like "menu edit virus" and "menu edit security" and then looked through several pages and didn't find anything like this. Just now I searched specifically in Recurring Discussions and those types of searches brought up nothing like this. Could you give me a link to them and tell me what I'd need to search to find them? I try not to make repeat threads if I can avoid it.

---

### Post by chessnerd on 2009-09-24
> **inobe said:**
> not a security issue at all, for example' can you change your screensaver or background or log onto an unsecured network, what about creating a personalized launcher..........


it's a user account without privileges that correspond to root.

Changing the screensaver or background can't break your system. As for logging onto an unsecured network, that is a user risk kind of thing. If something goes wrong its not the OSs fault, is the user's. A personalized launcher does nothing unless it is used, which, if there was suddenly a new launcher on your panel that needed admin privileges to run, would you give it to the program or even click it in the first place?

The idea is that you trick the user into giving the program root access. The same way that you give root access to things like samba and gufw, you as a user with admin privileges can grant a program root access to the system. The program running with just user privileges can't do much, so it would need root access to really do damage. If you fooled someone into thinking that they were granting that access to the Update Manager or Add/Remove Programs then the program could have privileges to everything on the system and, if part of the program opened up the program it was "replacing," the user might not even realize that anything was wrong until it was too late.

---

### Post by FuturePilot on 2009-09-24
> **chessnerd said:**
> Really? I did a check before I posted just for that. I tried things like "menu edit virus" and "menu edit security" and then looked through several pages and didn't find anything like this. Just now I searched specifically in Recurring Discussions and those types of searches brought up nothing like this. Could you give me a link to them and tell me what I'd need to search to find them? I try not to make repeat threads if I can avoid it.

Here is 2

[http://ubuntuforums.org/showthread.php?t=1120670]("http://ubuntuforums.org/showthread.php?t=1120670")

[http://ubuntuforums.org/showthread.php?t=1215136]("http://ubuntuforums.org/showthread.php?t=1215136")

---

### Post by p_quarles on 2009-09-24
> **chessnerd said:**
> The program running with just user privileges can't do much

This is one of the most persevering and pernicious myths within the Linux community. Yes, you usually need root permissions to access the root filesystem, as well as change low-level hardware settings like video and networking.

But user level permissions provide virtually everything a semi-intelligent attacker would ever need to take over your computer without your knowing it.

---

### Post by inobe on 2009-09-24
> **chessnerd said:**
> Changing the screensaver or background can't break your system. As for logging onto an unsecured network, that is a user risk kind of thing. If something goes wrong its not the OSs fault, is the user's. A personalized launcher does nothing unless it is used, which, if there was suddenly a new launcher on your panel that needed admin privileges to run, would you give it to the program or even click it in the first place?

The idea is that you trick the user into giving the program root access. The same way that you give root access to things like samba and gufw, you as a user with admin privileges can grant a program root access to the system. The program running with just user privileges can't do much, so it would need root access to really do damage. If you fooled someone into thinking that they were granting that access to the Update Manager or Add/Remove Programs then the program could have privileges to everything on the system and, if part of the program opened up the program it was "replacing," the user might not even realize that anything was wrong until it was too late.

in theory if your assumptions were correct' how long do you think it'll progress ?

seriously' we are talking open, hundreds of thousands are improving said software on a daily basis.

the only risk i see are newbies trying to run poorly configured servers and script kiddies cracking weak passwords on ssh boxes.

i guess what i'm trying to say is the desktop is a waste of time for the crackers thirty seconds of fame.

---

### Post by tjwoosta on 2009-09-24
> In Ubuntu you can edit the Applications and System menus without being root using the menu editor. This doesn't seem like much of a problem, but I was thinking about it and noticed that you can edit anything about the menus without having root privileges. In fact, you can even change the commands that the menu icons link to without giving your password. I think this could be a major security problem...

Let's say that I am trying to create a piece of malware for Linux that runs a dangerous command. The main problem with that is that, for almost all devastating commands, you need to be root. It's one of the great things about Linux and is probably its greatest security strength. However, let's say I wrote a program that went into the configuration file for the menus and changed something--let's say Synaptic's link--to instead run a dangerous command proceeded with "gksu." If the person clicked on it it would prompt them for their admin password, nothing unusual for Synaptic, and when they typed it in the command would execute with root privileges. Depending on the command it could unblock their firewall, delete all their files, send all their files to someone over the Internet, cause memory usage to skyrocket until the system crashed, etc.

Is this a legitimate security concern or would it be impossible for someone to implement this?

I don't know the exact link, but this was a big thing a few months back. There were even a couple youtube videos made explaining the concept, and personal blogs showing how to do it.

The original idea was to email somebody a .desktop file disguised as a picture. When the attachment was received in an email client it would prompt the user to save to Desktop (in the email would be a social engineering scheme to convince the recipient to go ahead and save "the picture" to the desktop, and many users are dumb enough to do this without reading the filename which would clearly say filename.desktop or more likely filename.png.desktop). 

When a .desktop is saved to the desktop it becomes a launcher and automatically hides the .desktop extension, so it would look like filename.png. At this point the recipient of the email has saved a malicious launcher to their desktop disguised as an image. The launcher itself would not require root because it only downloads the malicious content to an obscure location in the home directory and changes the users menu entries. Now when the user double clicks the image(expecting to see the image open in an image viewer) it actually install malicious software and change menu entries to launch it.

The user at some point uses the menus to open something that rightfully requires root, but instead it launches the malicious content as root. Game over.

---

### Post by inobe on 2009-09-24
> **tjwoosta said:**
> I don't know the exact link, but this was a big thing a few months back. There were even a couple youtube videos made explaining the concept, and personal blogs showing how to do it.

The original idea was to email somebody a .desktop file disguised as a picture. When the attachment was received in an email client it would prompt the user to save to Desktop (in the email would be a social engineering scheme to convince the recipient to go ahead and save "the picture" to the desktop, and many users are dumb enough to do this without reading the filename which would clearly say filename.desktop). 

When a .desktop is saved to the desktop it becomes a launcher and automatically hides the .desktop extension, so at this point the recipient of the email has saved a malicious launcher to their desktop disguised as an image. The launcher itself would not require root because it only downloads the malicious content to an obscure location in the home directory and changes the users menu entries. Now when the user double clicks the image(expecting to see the image open in an image viewer) it actually install malicious software and change menu entries to launch it.

The user at some point uses the menus to open something that rightfully requires root, but instead it launches the malicious content as root. Game over.

come on man, linkage needed for verification' otherwise non-factual  ?

---

### Post by chessnerd on 2009-09-24
> **FuturePilot said:**
> Here is 2

[http://ubuntuforums.org/showthread.php?t=1120670]("http://ubuntuforums.org/showthread.php?t=1120670")

[http://ubuntuforums.org/showthread.php?t=1215136]("http://ubuntuforums.org/showthread.php?t=1215136")

Fair enough. 

Interesting video for the first one. That's pretty much exactly what I was talking about (in the second half) and it gives evidence to a point in an earlier post that I made about Linux: it's about users making errors and being ignorant about what they are doing, not just about the OS being more secure. It seems like 99% of malware infections are caused, not by OS flaws, but by PEBCAK errors.

As for the second one, everything in the OP was removed because it contained "malicious code," probably because the guy actually told how he would do it.

I honestly did try to find posts like these to make sure I wasn't beating a dead horse, but neither the video one nor the deleted one came up in my searches (probably because I didn't search the right thing).

> **p_quarles said:**
> This is one of the most persevering and pernicious myths within the Linux community. Yes, you usually need root permissions to access the root filesystem, as well as change low-level hardware settings like video and networking.

But user level permissions provide virtually everything a semi-intelligent attacker would ever need to take over your computer without your knowing it.

True. I doubt anyone here is storing all of their important files in a folder that needs root access, and a program running with user level privileges can get at anything in your home folder. That would give an attacker quite a bit of stuff depending on what you have...

---

### Post by chessnerd on 2009-09-24
> **tjwoosta said:**
> I don't know the exact link, but this was a big thing a few months back. There were even a couple youtube videos made explaining the concept

Like this one? [http://www.youtube.com/watch?v=9HxFGQ8OpYw]("http://www.youtube.com/watch?v=9HxFGQ8OpYw")

---

### Post by tjwoosta on 2009-09-24
> come on man, linkage needed for verification' otherwise non-factual ?

Well it was a while back, but just doing a google search I did find a similar idea.

[http://www.geekzone.co.nz/foobar/6229]("http://www.geekzone.co.nz/foobar/6229")

Remember this is not actually a linux virus, its social engineering. And this same type of thing is even easier in windows and happens all the time.

> Like this one? [http://www.youtube.com/watch?v=9HxFGQ8OpYw](http://www.youtube.com/watch?v=9HxFGQ8OpYw)

yea, like that one :)

---

### Post by p_quarles on 2009-09-24
> **chessnerd said:**
> True. I doubt anyone here is storing all of their important files in a folder that needs root access, and a program running with user level privileges can get at anything in your home folder. That would give an attacker quite a bit of stuff depending on what you have...

Sure, if you have sensitive data, the attacker could get at that.

But my real point is that if the attacker found a good exploit, he/she could run any program (with user privileges) without your knowing it or being able to easily detect it (because it's aliased to a common system process name) that could do all manner of nasty things: steal passwords, e-mail viruses to other people, DDOS servers, host kiddie porn/warez in a hidden directory, etc., etc. 

Yeah, this depends on the existence of an unpatched exploit, but that is true of any system. My point is that a lot of people *far* overestimate the actual protective value of root-user privilege separation. It's not really that great.

---

### Post by inobe on 2009-09-24
keep it up guys, in fact why don't you head over to launchpad and report your findings.

it does nothing here but create mass hysteria and madness mixed with mayhem.

surely no one will click a .desktop file after seeing this but why not help improve the product rather than posting here ?

i see a few users saying what can be done however nothing said what they've done to help !

---

### Post by pastalavista on 2009-09-24
A Linux system is as vulnerable to "social engineering" attack as any other OS. The biggest boost to its claim of security superioriy comes from its dismally low percentage of the desktop market. The Linux-server market security is a slightly different story.

---

### Post by MaxIBoy on 2009-09-24
> **p_quarles said:**
> It's easier than all that, actually. You can easily change what common commands like "cp" or "rm" do by writing a few lines to .bashrc and symlinking the command to a malicious script. 

Normal user privileges in Linux allow attackers to do a great deal of very harmful things. A lot of people underestimate this.Which is why I made these bash functions for my ~/.bashrc:
```
function chx {
chmod -w $1
chmod +x $1
}

function chw {
chmod -x $1
chmod +w $1
}
```Now, if I need to modify, say, my ~/.bash_profile:
```

chw ~/.bash_profile
gedit ~/.bash_profile
chx ~/.bash_profile

```At no point in time can I write to *and* execute the file at the same time.

I think this is good security policy and I would encourage everyone else to do the same.

---

### Post by inobe on 2009-09-24
> **MaxIBoy said:**
> Which is why I made these bash functions for my ~/.bashrc:
```
function chx {
chmod +x $1
chmod -w $1
}

function chw {
chmod -x $1
chmod +w $1
}
```Now, if I need to modify, say, my ~/.bash_profile:
```

chw ~/.bash_profile
gedit ~/.bash_profile
chx ~/.bash_profile

```At no point in time can I write to *and* execute the file at the same time.

I think this is good security policy and I would encourage everyone else to do the same.

if this issue was known by the devs' how will you suppose it being fixed ?

---

### Post by tjwoosta on 2009-09-24
> **inobe said:**
> keep it up guys, in fact why don't you head over to launchpad and report your findings.

it does nothing here but create mass hysteria and madness mixed with mayhem.

surely no one will click a .desktop file after seeing this but why not help improve the product rather than posting here ?

i see a few users saying what can be done however nothing said what they've done to help !

Actually all this is already well known. Like I said before this was a big thing a few months back. (it was actually probably about 4 months ago)

Last I heard the gnome team was working on it. As these things go people were discouraged from bringing it up and somehow it was buried again. I only hope the people that were working on it are still working on it.

---

### Post by FuturePilot on 2009-09-24
> **inobe said:**
> keep it up guys, in fact why don't you head over to launchpad and report your findings.

it does nothing here but create mass hysteria and madness mixed with mayhem.

surely no one will click a .desktop file after seeing this but why not help improve the product rather than posting here ?

i see a few users saying what can be done however nothing said what they've done to help !

Gnome already has added a dialogue that pops up and asks you if you want to execute the .desktop file if you click on one.

---

### Post by tjwoosta on 2009-09-24
> Gnome already has added a dialogue that pops up and asks you if you want to execute the .desktop file if you click on one.

I haven't used gnome or kde for a long time, so I cant test it out, but wouldn't that get kind of annoying if you keep all your launchers on your desktop? Or does it just ask you to make it executable for all future uses?

---

### Post by FuturePilot on 2009-09-24
> **tjwoosta said:**
> I haven't used gnome or kde for a long time, so I cant test it out, but wouldn't that get kind of annoying if you keep all your launchers on your desktop? Or does it just ask you to make it executable for all future uses?

It doesn't ask on normal launchers that are on the desktop. Somehow it marks known programs as "trusted". So if you try to launch a random .desktop file you get a dialogue. See screenshot

---

### Post by tjwoosta on 2009-09-24
ahh, i see. 
Well thats one security risk solved, now they just need to change the write permissions for the menu and .bashrc and whatever other config files that could change commands.

---

### Post by Exodist on 2009-09-24
> **p_quarles said:**
> It's easier than all that, actually. You can easily change what common commands like "cp" or "rm" do by writing a few lines to .bashrc and symlinking the command to a malicious script. 

Normal user privileges in Linux allow attackers to do a great deal of very harmful things. A lot of people underestimate this.

I agree, alot of users are in denial here. A web script can easily rake havoc on a users system. 

Currently I believe there is around 860+ viruses/maleware for linux. So if linux is so safe. Why do many?

REF = [http://en.wikipedia.org/wiki/Linux_malware]("http://en.wikipedia.org/wiki/Linux_malware")

---

### Post by bodhi.zazen on 2009-09-24
> **p_quarles said:**
> This is one of the most persevering and pernicious myths within the Linux community. Yes, you usually need root permissions to access the root filesystem, as well as change low-level hardware settings like video and networking.

But user level permissions provide virtually everything a semi-intelligent attacker would ever need to take over your computer without your knowing it.

+1 Shell access is almost as bad as physical access.

> **Exodist said:**
> I agree, alot of users are in denial here. A web script can easily rake havoc on a users system. 

I think that is a bit of an over statement. 

The statement does, however, have a kernel of truth and there have been web browser ecxploits. IMO, one should be using tools such as NoScript and Apparmor.

Starting with 9.10 there is (finally) an apparmor profile for Firefox.

---

### Post by Mornedhel on 2009-09-25
> **tjwoosta said:**
> ahh, i see. 
Well thats one security risk solved, now they just need to change the write permissions for the menu and .bashrc and whatever other config files that could change commands.

No.

As a non-sudoer on a multiuser system, I should not need to ask my sysadmin for permission to customize my environment. It is not his business if I want to add or remove a shortcut in the main menu, or if I want to enable color by default on grep through bashrc. I also cannot execute anything that is harmful system-wide, only something that can act on my own data.

---

### Post by bodhi.zazen on 2009-09-25
> **Mornedhel said:**
> No.

As a non-sudoer on a multiuser system, I should not need to ask my sysadmin for permission to customize my environment. It is not his business if I want to add or remove a shortcut in the main menu, or if I want to enable color by default on grep through bashrc.

+1. Things such as .bashrc are not the PRIMARY vulnerability.

>  I also cannot execute anything that is harmful system-wide, only something that can act on my own data.In theory yes this is true, in practice it is not true. In essence this is what a root kit is, a program or series of programs that runs with user privileges but escalates to root privileges.

There are numerous potential vulnerabilities discovered over time. Many are patched as they are found, but still there are vulnerabilities, both known and unknown, that allow user privilege escalation. Unknown vulnerabilities are know as Zero Day exploits and at this time the only options you might have would be SELinux or Apparmor (or similar).

for example : [http://www.ubuntu.com/usn/usn-821-1](http://www.ubuntu.com/usn/usn-821-1)

Although that example is not shell access, it demonstrates how applications running without root privileges can be leveraged to gain root access. When they say arbitrary code, sure they could edit .bashrc, but that is sloppy.

Thus it is a circular argument, if a cracker can alter .bashrc they already have either shell or root access and either way you are in deep trouble.

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

---

