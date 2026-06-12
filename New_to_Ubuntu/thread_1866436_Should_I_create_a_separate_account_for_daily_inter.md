---
title: "Should I create a separate account for daily internet use?"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by NattyLight on 2011-10-21
Hey guys new here, I actually signed up a couple days ago but have just been lurking and researching until now. One of the threads I found (the Linux vs XP thread) and most people said that you shouldnt do everyday internet browsing on your admin account. I'm not completely new to Ubuntu (coming from 10.04 and LOVED it!) and I always did my day to day such on my admin account and never had a problem. (I also do my day to day stuff on my admin account on my windows 7 side as well and no problems so far either.

Ok so I feel like I'm just rambling on now, back to the question; **Should I create another user account for my day to day internet browsing or am I fine**?This forum is great btw! Helped me to get wireless working flawlessly as well as getting flash to work on my Ubuntu side as well!

---

### Post by muteXe on 2011-10-21
Are you sure you used your admin account??

---

### Post by satanselbow on 2011-10-21
If you really spend that much time browsing prawn sites - and really don't want you mum/wife/family pet to find out... then yeah maybe... otherwise I wouldn't bother ;)

Both FX and Chrom(ium) have private browsing these days anyway :popcorn:

---

### Post by shadytv on 2011-10-21
Ubuntu is a lot different than Windows, by default you are automatically put in a lower level account on the computer the "admin" account in Ubuntu is called root or "/" the password is automatically scrambled in Ubuntu (not the same for debian/fedora/opensuse or any other linux distribution) the only way to gain root (or admin)access is to run a command called sudo in your terminal so there really is no need just DONT run programs as root avoid if at all possible (obviously stuff like update-manager needs root access)

---

### Post by NattyLight on 2011-10-21
> **muteXe said:**
> Are you sure you used your admin account??

Not really I guess, right now I'm the only user on the Ubuntu side and it's the adminstrator

---

### Post by NattyLight on 2011-10-21
> **shadytv said:**
> Ubuntu is a lot different than Windows, by default you are automatically put in a lower level account on the computer the "admin" account in Ubuntu is called root or "/" the password is automatically scrambled in Ubuntu (not the same for debian/fedora/opensuse or any other linux distribution) the only way to gain root (or admin)access is to run a command called sudo in your terminal so there really is no need just DONT run programs as root avoid if at all possible (obviously stuff like update-manager needs root access)

So if I am understanding you right, even though my account is administrator, I still am not root(admin)?

---

### Post by cryptotheslow on 2011-10-21
Your account will be in the admin group, but when you login and open up e.g. Firefox (or anything else) it runs with just your basic user permissions.

If something asks for your Admin password as it starts does it run with any admin rights. Or if you prefix a command in a Terminal session with su or gksu (which will ask for your Admin password).

Note - your "admin" password is the same as your "user" password by default.

Read up on what sudo is and how Ubuntu uses it. There's undoubtably some good info in the Security forum here.


Edit add - and no you are not the user "root". Ever. That account exists but is disabled on an Ubuntu installation.

---

### Post by NattyLight on 2011-10-21
> **satanselbow said:**
> If you really spend that much time browsing prawn sites - and really don't want you mum/wife/family pet to find out... then yeah maybe... otherwise I wouldn't bother ;)

Both FX and Chrom(ium) have private browsing these days anyway :popcorn:

Lol, no wife to worry about, my mom is not too tech savy, plus its PWP anyways, that would be the coolest pet in the world if it found out. 

So it sounds like I'm fine then, just gotta use some common sense (You learn to use common sense a lot as far as windows goes lol)

---

### Post by shadytv on 2011-10-21
> **NattyLight said:**
> So if I am understanding you right, even though my account is administrator, I still am not root(admin)?
the first created account on the computer IS NOT and administrator account, the first account has basic privileges just like the rest of the accounts on the computer (except for root)
so no you are not the administrator

---

### Post by NattyLight on 2011-10-21
> **cryptotheslow said:**
> Your account will be in the admin group, but when you login and open up e.g. Firefox (or anything else) it runs with just your basic user permissions.

If something asks for your Admin password as it starts does it run with any admin rights. Or if you prefix a command in a Terminal session with su or gksu (which will ask for your Admin password).

Note - your "admin" password is the same as your "user" password by default.

Read up on what sudo is and how Ubuntu uses it. There's undoubtably some good info in the Security forum here.


Edit add - and no you are not the user "root". Ever. That account exists but is disabled on an Ubuntu installation.


Oh ok, that is really cool, I never knew that. Yea there is definitely a lot to learn about Linux as a whole but I am up for the challenge :) My first win was finally getting that wireless button to turn blue lol

---

### Post by cryptotheslow on 2011-10-21
Let's not get too confusing shadytv. The first user account created is a basic user account but **is** in the admin wheel group so **can** perform administrative tasks (by using sudo / gksu etc.).

Subsequent accounts created by that first account will not be in the admin wheel group unless specifically set up to be.

---

### Post by NattyLight on 2011-10-21
> **cryptotheslow said:**
> Let's not get too confusing shadytv. The first user account created is a basic user account but **is** in the admin wheel group so **can** perform administrative tasks (by using sudo / gksu etc.).

Subsequent accounts created by that first account will not be in the admin wheel group unless specifically set up to be.

So this explains why my account does say admin, its just the group I'm in. Ok I understand now.

---

### Post by nothingspecial on 2011-10-21
> **shadytv said:**
> the first created account on the computer IS NOT and administrator account, the first account has basic privileges just like the rest of the accounts on the computer (except for root)
so no you are not the administrator

The first account created during install is an admin account.

It goes into the admin group and can therefore use sudo to administer the system.

The root account is disabled by default in Ubuntu. You do not need it.

---

### Post by NattyLight on 2011-10-21
> **nothingspecial said:**
> The first account created during install is an admin account.

It goes into the admin group and can therefore use sudo to administer the system.

The root account is disabled by default in Ubuntu. You do not need it.


So on my windows side I should create a separate account though huh?

---

### Post by cryptotheslow on 2011-10-21
> **NattyLight said:**
> So this explains why my account does say admin, its just the group I'm in. Ok I understand now.

It is one of the groups your account is in. 

If you open a Terminal session and type the command
```
 groups 
```

you will get back a list of the groups you are in.

---

### Post by nothingspecial on 2011-10-21
> **NattyLight said:**
> So on my windows side I should create a separate account though huh?

I have absolutely no idea.

You are fine using your admin account in Ubuntu for everyday use. If you need to do something that requires root privileges use sudo for terminal commands and terminal applications. Use gksudo if you need to launch a graphical application with root privileges.

---

### Post by NattyLight on 2011-10-21
> **cryptotheslow said:**
> It is one of the groups your account is in. 

If you open a Terminal session and type the command
```
 groups 
```you will get back a list of the groups you are in.

I just did this, I assume it's pretty normal to be in a lot of groups right? (By a lot I mean the defaults I suppose)

---

### Post by cryptotheslow on 2011-10-21
> **NattyLight said:**
> So on my windows side I should create a separate account though huh?

Probably a good idea if you are careless with your browsing / clicking on links in emails etc.

Personally I have been using an admin user account on XP for years without any problem. But then I am careful what I do and use NoScript and AdBlock plugins on Firefox.

Up to you really at the end of the day.

---

### Post by cryptotheslow on 2011-10-21
> **NattyLight said:**
> I just did this, I assume it's pretty normal to be in a lot of groups right? (By a lot I mean the defaults I suppose)


Yes quite normal to be in a number of groups. Can't remember the default list but it includes stuff like audio. I'm sure if you post up the list someone will be able to confirm if it is "normal" or not.

---

### Post by NattyLight on 2011-10-21
> **nothingspecial said:**
> I have absolutely no idea.

You are fine using your admin account in Ubuntu for everyday use. If you need to do something that requires root privileges use sudo for terminal commands and terminal applications. Use gksudo if you need to launch a graphical application with root privileges.

I will probably just stick with the same account on my Windows 7 side as well, ok thanks everyone!

---

### Post by nothingspecial on 2011-10-21
```
$USER adm dialout cdrom plugdev lpadmin admin sambashare
```

Where $USER is your user.

---

### Post by NattyLight on 2011-10-21
> **cryptotheslow said:**
> Probably a good idea if you are careless with your browsing / clicking on links in emails etc.

Personally I have been using an admin user account on XP for years without any problem. But then I am careful what I do and use NoScript and AdBlock plugins on Firefox.

Up to you really at the end of the day.


Definitely not careless, before I upgraded to Windows 7 I also ran on my admin account for years and no troubles, just gotta have some common sense, don't click on suspicious links etc... you know :) 

Thats definitely one of the things I love about using Ubuntu even over 7 is I don't have to worry about is this link gonna be the one that gets me?

---

### Post by NattyLight on 2011-10-21
```
adm dialout cdrom plugdev lpadmin admin sambashare

```

---

### Post by nothingspecial on 2011-10-21
You should be in your own group.

Did you remove it from your post?

---

### Post by cryptotheslow on 2011-10-21
> **NattyLight said:**
> Definitely not careless, before I upgraded to Windows 7 I also ran on my admin account for years and no troubles, just gotta have some common sense, don't click on suspicious links etc... you know :) 

Thats definitely one of the things I love about using Ubuntu even over 7 is I don't have to worry about is this link gonna be the one that gets me?

You can't sleep walk with Ubuntu either. You can still be "got" by malicious cross-site scripts, social engineering techniques, network traffic sniffing on public networks etc. The only difference is unless you deliberately make it otherwise such things can only affect the things your user account can access (e.g. your home directory, write stuff to /tmp etc.) but not completely trash your system (easily).

---

### Post by NattyLight on 2011-10-21
> **nothingspecial said:**
> You should be in your own group.

Did you remove it from your post?

Oh yea I did I guess lol, I am in my own group, sorry about that

---

### Post by NattyLight on 2011-10-21
> **cryptotheslow said:**
> You can't sleep walk with Ubuntu either. You can still be "got" by malicious cross-site scripts, social engineering techniques, network traffic sniffing on public networks etc. The only difference is unless you deliberately make it otherwise such things can only affect the things your user account can access (e.g. your home directory, write stuff to /tmp etc.) but not completely trash your system (easily).

Oh yea definitely, I am still just as vigilant on Ubuntu as I am on any Windows OS, my last post made it seem like I'm invincible as long as I'm in Ubuntu, I don't mean that at all.

---

### Post by nothingspecial on 2011-10-21
Everything is fine. Do not worry.

---

### Post by Ms. Daisy on 2011-10-21
> **nothingspecial said:**
> The first account created during install is an admin account.
It goes into the admin group and can therefore use sudo to administer the system.
The root account is disabled by default in Ubuntu. You do not need it.  I suppose I'm beating a dead horse, but I would really like to clarify this point. I've been reading [http://ubuntupocketguide.com/index_main.html](http://ubuntupocketguide.com/index_main.html) which was published in 2009.  This document indicates that "In fact, on most Linux systems two login accounts are created during installation- a standard user, and the root user.  The root user is a special user account gifted with the ability to do anything... Its username is always root.  Normally when Linux is used on a PC, a standard user logs into the root account whenever he has to administer the system, and then logs out when he's finished.  However, he will spend most of her time logged into her ordinary user account, doing day-to-day stuff...
"Ubuntu differs slightly from most Linuxes.  Although the root account is there in the background, the user is discouraged from directly logging in as root.  Instead the user "borrows" root powers to administer the system when necessary.  Usually this is done by simply entering your login password when prompted."
 
So help me (and the OP) out here- is that no longer accurate?

And to shed a bit of light on the OP's question about Windows, the same document goes on to say "The fact that Windows fails to make the distinction, and effectively merges the standard and administrator types of user account, is one reason it's so insecure.  If a virus infects the system, it operates with adminstrator powers, so it can really cause trouble."  Perhaps knowing this tid-bit of information can help you determine how you want to approach internet browsing on Windows systems.

---

### Post by cryptotheslow on 2011-10-21
That information is still correct.

i.e.
the account "root" is disabled on Ubuntu
your user account is in the Admin group, so can carry out Admin tasks by using sudo or gksudo - at which point you are prompted for your password.

---

### Post by Paqman on 2011-10-21
> **Ms. Daisy said:**
> 
So help me (and the OP) out here- is that no longer accurate?


No, it's completely right. Ubuntu does not use a separate root account, and instead allows any user with admin rights to temporarily elevate themselves to root's privileges when they need to.

---

### Post by NattyLight on 2011-10-21
> **Paqman said:**
> No, it's completely right. Ubuntu does not use a separate root account, and instead allows any user with admin rights to temporarily elevate themselves to root's privileges when they need to.

So say you just did something in a terminal that required root, after you are done is there a command in the terminal to "log off" of the root or does it automatically do this as soon as whatever you had to do that required the root password is finished?

---

### Post by NattyLight on 2011-10-21
> **Ms. Daisy said:**
> 

And to shed a bit of light on the OP's question about Windows, the same document goes on to say "The fact that Windows fails to make the distinction, and effectively merges the standard and administrator types of user account, is one reason it's so insecure.  If a virus infects the system, it operates with adminstrator powers, so it can really cause trouble."  Perhaps knowing this tid-bit of information can help you determine how you want to approach internet browsing on Windows systems.

So even if you do create another account for day to day stuff, and you got the virus on that other account, your admin will still be compromised? That's what it sounds like to me anyways. That sucks.

---

### Post by cryptotheslow on 2011-10-21
If you keep the Terminal window open after executing a command with sudo (for example) then for a time the Terminal will retain admin privileges. I think it is around 5 or 10 minutes.


If you prefer you could enter:
```
sudo -s
```
 then enter your command that requires admin privilege.

then enter:
```
exit
```

to definitively exit the elevated privilege.

---

### Post by nothingspecial on 2011-10-21
@NattyLight

Install stuff through the Ubuntu repos (software centre)

Don't open anything you download from an untrusted source as root (with sudo).

You will be fine.

---

### Post by satanselbow on 2011-10-21
> **NattyLight said:**
> is there a command in the terminal to "log off" of the root or does it automatically do this as soon as whatever you had to do that required the root password is finished?

closing the terminal that you used will effectively log you out of the "root" status.

You can try it by opening a terminal and opening a trivial app such as gedit:

```
sudo gedit
```

you will be asked for your password. 

If you then close gedit AND the terminal and lose your evelated status. If you immediately repeated the process you would again be asked for your password.


There is a minor gotcha (more of a watch out!) in that WITHIN THE SAME TERMINAL you will only be asked for your password ONCE. So you could do the example above but before closing the terminal "sudo" another app without having to re-enter your password.

** timeout clarified above ***

Not a too confusing explanation I hope ;)

---

### Post by Ms. Daisy on 2011-10-21
> **NattyLight said:**
> So even if you do create another account for day to day stuff, and you got the virus on that other account, your admin will still be compromised? That's what it sounds like to me anyways. That sucks. That's what it sounds like to me, too, when we're talking about Windows.  You could look into sandboxing (I don't think it's necessary on Linux).  The concept is that you open your browser inside of a box or a walled-off partition in your hard drive and nothing can access the C drive unless you explicitly allow it.  I don't think it offers much protection against cross-site scripting or someone hijacking your sessions, but it would theoretically prevent malicious programs from downloading onto your machine.

---

### Post by nothingspecial on 2011-10-21
> **satanselbow said:**
> closing the terminal that you used will effectively log you out of the "root" status.

You can try it by opening a terminal and opening a trivial app such as gedit:

```
sudo gedit
```

you will be asked for your password. 

If you then close gedit AND the terminal and lose your evelated status. If you immediately repeated the process you would again be asked for your password.


There is a minor gotcha (more of a watch out!) in that WITHIN THE SAME TERMINAL you will only be asked for your password ONCE. So you could do the example above but before closing the terminal "sudo" another app without having to re-enter your password.

** timeout clarified above ***

Not a too confusing explanation I hope ;)


Use gksudo for graphical apps please.

---

### Post by NattyLight on 2011-10-21
> **satanselbow said:**
> closing the terminal that you used will effectively log you out of the "root" status.

You can try it by opening a terminal and opening a trivial app such as gedit:

```
sudo gedit
```you will be asked for your password. 

If you then close gedit AND the terminal and lose your evelated status. If you immediately repeated the process you would again be asked for your password.


There is a minor gotcha (more of a watch out!) in that WITHIN THE SAME TERMINAL you will only be asked for your password ONCE. So you could do the example above but before closing the terminal "sudo" another app without having to re-enter your password.

** timeout clarified above ***

Not a too confusing explanation I hope ;)

No not at all, easier to understand than all the NDISwrapper stuff lol

---

### Post by NattyLight on 2011-10-21
> **Ms. Daisy said:**
> That's what it sounds like to me, too, when we're talking about Windows.  You could look into sandboxing (I don't think it's necessary on Linux).  The concept is that you open your browser inside of a box or a walled-off partition in your hard drive and nothing can access the C drive unless you explicitly allow it.  I don't think it offers much protection against cross-site scripting or SQL injection, but it would theoretically prevent malicious programs from downloading onto your machine.


So almost like setting up a virtual server like Virtual Box right? Or like a 3rd party firewall? When I had XP Comodo Firewall had a kind of sandbox feature, I havent installed in on 7 yet because I'm not sure if the firewall in 7 is good or not yet. But back to what you were saying, if a malicious program did infect the VB, just the VB would be screwed instead of your entire Windows side.

---

### Post by NattyLight on 2011-10-21
> **nothingspecial said:**
> @NattyLight

Install stuff through the Ubuntu repos (software centre)

Don't open anything you download from an untrusted source as root (with sudo).

You will be fine.

Yea, before I was looking to trying to install flash, it took me to the adobe site but, idk I still didnt really trust it, so I was glad that I found it on the software center side. Another thing I love about Ubuntu as well.

---

### Post by Ms. Daisy on 2011-10-21
> **NattyLight said:**
> So almost like setting up a virtual server like Virtual Box right? Or like a 3rd party firewall?  Kinda. A firewall controls network traffic, but a sandbox prevents a program run inside of it from talking to any other part of the same computer.  A sandbox differs from a Virtual Box in that it isn't it's own OS.  A sandbox is just an empty space to run programs separated from everything else on your hard drive.  

The most obvious example is if I would write a program called "deleteAllMyFiles.py".  I want to test it but I don't really want to delete all my files on my computer.  So I run it in a sandbox and see if it deletes the test files I put in there with it.

---

