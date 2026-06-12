---
title: "ubuntu network setup wizard(an easy gui for samba)"
date: 2006-04-26
forum: Programming Talk
---

### Post by troyDoogle7 on 2006-04-26
Hi all, 

We have noticed in a lot of the help secitions that a lot of newbies and some veterens are having problems setting up and configuring samba in order to share  files and printers with windows computers. 

We all know how simple it is to do in windows and would love for the ubuntu to be just as easy.  Brentoboy said the following:
> 
 Re: Using the samba gui (Shared folders tool)
I think troy is right.
We need to start advocating a better gui for samba. I have yet to have a samba server setup for ubuntu without resorting to hit the config file, not even a basic: "just share this folder" type of setup.

A good samba gui could work like so:

first, select which "windows" you want to model:
Windows 95/98 - totally opened sharing, no user athentication
Windows NT/2000 - users must login
Windows domain server - users own their own files, and some users can access some shares... etc.

then it could ask:
what do you want to call this computer?
What is the workgroup / domain name?

the wizard would ask what folders you want to make available, and then some questions about printers etc.

finally, it would spit out a new smb.conf file, and restart smb

then it could offer to allow you to add/remove/edit samba users (or maybe this should be a different app altogether that gets launched after you create a new smb-conf)

after running the wizard, a windows box should be able to see the server and its shares without any more issues than they would have with a windows 2000 computer that they had selected to share a particular folder.

if it isnt that easy, then it isnt progress.
I really dont see why a clean python script couldnt do all those things with ease, but it would take some time to organize and design a really smooth logical step by step easy setup.
__________________
- Brentoboy
"god is real (unless explicitly declared as int)" 

Can someone tell me if this is feasible?
If so is it easy to achiieve?
Is there anything in the pipeline for ubuntu that would do something like this?

Thanks, on behalf of the newbie commuinty

---

### Post by shof2k on 2006-04-26
I'm not a python programmer, but nothing of the above seems impossible to do.  I agree that this should be done sooner than later.  Working with window's shares is a definite plus when getting people to try linux.

Rock on!!!!

---

### Post by LactosetheIntolerant on 2006-04-26
Having a gui to create a samba conf file would be trivial, but still requires the user to know what they need to do to get it working.  Therein lies the problem.

---

### Post by troyDoogle7 on 2006-04-26
Lacto, can you explain that I don't understand.  

Wouldn't it be easy to just offer drop down menus? to guide the user?

---

### Post by brentoboy on 2006-04-27
a simple "just share this folder" smb file is easy to make, but not very secure, a pyWizard could certanly ask 2 or three questions, and make life easy for the 80% of home users who dont care a hoot about security becuase they are behind a firewall router dsl model or cabel modem.

a smb-users network app, and smb integration into the user-admin app shouldnt be so bad.  create a virtual group smb-users, and if they are in that group, then ussue the smb add user command or smb update user when you make changes to an ubuntu user

there is no need to even have a seperate smb-users list or user manager.  after enabling smb, it should just say "if you want users to be able to login to smb shares, add them to the smb-users group in user-groups-admin, and update thier password."

I-donno, just ranting.
anyway, I'd be happy to help, I am learning wxPython, and I could see it doing that, but I am still just a noob to python

---

### Post by brentoboy on 2006-04-27
would glade files that outline the options help the cause?

---

### Post by mjm115 on 2006-04-27
Or how about something similar to the [KSambaplugin]("http://ksambakdeplugin.sourceforge.net/") in KDE?

[IMG]http://ksambakdeplugin.sourceforge.net/ksambapluginkcontrolcenter.png[/IMG]

---

### Post by troyDoogle7 on 2006-04-29
That is exactly the sort of thing that we need in ubuntu.  Is there a method to port to ubuntu?

---

