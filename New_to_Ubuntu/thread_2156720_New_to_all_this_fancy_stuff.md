---
title: "New to all this fancy stuff"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by Michaelocalypse on 2013-06-22
First off, I got this computer from here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883258040](http://www.newegg.com/Product/Product.aspx?Item=N82E16883258040)
Secondly, I've never used, or even seen, any Linux systems before.

So there's your frame of reference.

Now, I'm not a complete idiot.  It's been a while since I've messed with any computer stuff, but I know it's a good skill to have.  That's why I wanted to get into Linux.  As far as my experience, I've pulled a few towers apart and added memory and modems.  I've also taken (and passed) Jave and C programming classes in school, as well as a few other engineering/math related program languages.  Taught myself HTML before that.  So I'm not a complete idiot, just a regular one.  I don't play well with Mac/Apple, and I don't like the new Windows/Microsoft stuff.  My 10 year old Dell laptop was crap when new, and has run its course several times.  This began the search for a new machine.

I know the machine I got is not the greatest.  I don't do any gaming.  Mostly internet surfing, forums, and the occasional video.  So far, it's doing the trick.  I contacted Avatar to get the Administrator/Root passoword so I can create a user account for myself.  I've read enough to know I don't want to go screwing around on the root account.  I tried the LTerm deal, then the CTRL+ALT+F1 thing to no avail... and started hitting buttons until CRTL+ALT+F6 (I think) got me out of it.

All that being said, I'm really liking this stuff.  Hopefully I can learn to use it to it's full potential soon.  I studied Mechanical Engineering, not this black magik voodoo computer stuff.  Bear with me while I figure this it out.  (I've gotten lazy and am still adapting to no spell check features.  Excuse any errors and rest assured that they annoy me more than they annoy you.)

---

### Post by kostkon on 2013-06-22
Welcome, hope you like it. The PC is fine.

You can easily install a spell checker in Firefox, and I assume also in Chrome.

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]Michaelocalypse; Hi ! Welcome to the forum.

This ain't no step for a stepper. Once you get some acclimation to the system ...you will find it is quite intuitive and it only gets as deep as you want it to get . -> you can do anything with it that you can imagine !
What version and distribution are you presently using ?  Be aware that there exist a number of different desk top environments that fit right on top of whatever you have installed, in the event you find you do not like what you have now.

We will work with you to get you productive and happy. Is there something presently that troubling you ? Getting comfortable with a new operating system takes time and as this is your first encounter with linux, there is a learning curve once you are past the point -of point and click. An overabundance of documentation abounds and the sheer weight can be intimitating but time will allow you to sift through it. In the meantime we are here to help in any means we can.

Root access ....not something that is done except in those extreme cases, and then be very sure of what you want it for and what you are doing it for... not discussed on this forum. For activities requiring administrative authority "sudo" is generally used.
From the desk top key combo ctl+alt+t will yield a terminal interface (CLI), in this terminal:
```
man sudo
``` Is a great way to introduce you to the complexities that are linux and to the manual of all commands in general.
Have a read and we are open for discussion and explanation. 
[/COLOR][INDENT=3][COLOR=#000000]
ubuntu, my operating system of choice

[/COLOR][/INDENT]

---

### Post by grahammechanical on 2013-06-22
Hi and welcome to the forums.

There is good news in all of this. Ubuntu is designed for the ordinary user. You really do not need to know terminal commands because there are utilities for doing most stuff. Find your way around the OS before you try out anything adventurous. You may find that you can do the adventurous stuff without any excitement. Or that Ubuntu satisfies your needs as it is.

You have installed a version of Ubuntu that is supported for security fixes and the like until about May next year. By that time a new Long Term Support (5 years) Ubuntu will be released and you will be able to upgrade to it. At the moment a new version of ubuntu is released every six months (in April and October). If you think of upgrading to the next release from 12.10 (13.04 - came out at end of April) then keep in mind that it has only 9 months support and so you will have to upgrade to 13.10 (Oct 2013) to keep using a supported version. You might be content to stick with 12.10 until next April.

Regards.

---

### Post by Michaelocalypse on 2013-06-22
Thanks for the responses.  My biggest grip with this machince so far is that I'm having to use the guest account.  It doesn't let me save any settings.  I breifly played with the sudo stuff, and will have to keep playing with it.  I'd like to have my own user account with a password.  It's something I'm accoustomed to, and the guest account doesn't save any changes I make.  This could just be part of the "me failing to learn anything" learning curve.  I didn't install the OS.  The only reason I want the root password is to make a user account for myself.  Any complaints after that will be blamed solely on the user (me).
Ubuntu is pretty intuitive so far.  A friend recommended this OS to me over other Linux versions, especially for former Windows users like myself.

I'm happy with the machine so far.  This forum seems to have a lot more to it than others I'm on.  Just another learning curve, but I'm becoming comfortable with it.  Thank you for your patience.  Feel free to be blunt with me.  I won't take it poorly.

> **kostkon said:**
> Welcome, hope you like it. The PC is fine.

You can easily install a spell checker in Firefox, and I assume also in Chrome.

Yeah, I had that before when I used to use Firefox.  I've been using Chome on my old Windows machine for a while.  I've been thinking about dowlnloading the TOR Browser on this computer, which I just heard about.

---

### Post by 2F4U on 2013-06-23
You can create as many different user accounts as you like. Here is a small how-to:

[https://help.ubuntu.com/13.04/ubuntu-help/user-add.html](https://help.ubuntu.com/13.04/ubuntu-help/user-add.html)

---

### Post by squakie on 2013-06-23
So let me ask - this guest account - does it ask for a password when you log in?  If so, you should be able to use sudo with that same password UNLESS the guest account isn't in the sudo'rs group, which could well be the case for a guest (it would make sense).  If you can't get access to sudo, you can't follow the other posts for adding a user as you won't have the priviledges to do so.

The root account is normally not recommended in Ubuntu.  Ubuntu is trying to reach an audience that shouldn't really have a need for root, and could screw some things up if they did have root access.  Hence the use of sudo.

However, you may have a special case here.  I doubt there is actually going to be a password coming from the manufacturer - they probably just install an OEM disk.  What's unfortunate is that they apparently didn't give you any instructions that would help you create your own account(s).

I'll take a look on the net for anything sounding similar for this PC and manufacturer.

In the mean time, there is a way to activate the root account.  We are not allowed by the forum rules to discuss that in the public forum for obvious reasons.  If I cannot find something to help you out, I will PM you to see if you REALLY want to activate root (I really wouldn't recommend it unless NOTHING else will work ;) ).

---

### Post by Impavidus on 2013-06-23
There is a way to create a new account from the terminal and give it access to sudo. To do so you root permissions, so the trick is to boot into a recovery console, which will give you root permissions automatically. See [here]("https://wiki.ubuntu.com/RecoveryMode") for instructions on how to get into a recovery console (drop to root shell), then remount the filesystem rw with```
mount -o rw,remount /
``` (watch the spaces)
and add a user using [these]("http://askubuntu.com/questions/70236/create-an-administrator-user-in-command-line") instructions.

---

### Post by newb85 on 2013-06-23
Michael,
I think you're missing an important point about Ubuntu.  It's *designed* for you to safely use the administrator account that was set up on the machine when it was sent to you.  Unless you issue a command with sudo in the CLI or give the your password when asked for authentication, you don't have elevated privileges.  Adding the extra user doesn't really add any security.

---

### Post by Michaelocalypse on 2013-06-23
> **2F4U said:**
> You can create as many different user accounts as you like. Here is a small how-to:

[https://help.ubuntu.com/13.04/ubuntu-help/user-add.html](https://help.ubuntu.com/13.04/ubuntu-help/user-add.html)
Thanks for the link.  As it states on that page, I can't do it without the administrator/root password.  I don't have that.

> **squakie said:**
> So let me ask - this guest account - does it ask for a password when you log in?  If so, you should be able to use sudo with that same password UNLESS the guest account isn't in the sudo'rs group, which could well be the case for a guest (it would make sense).  If you can't get access to sudo, you can't follow the other posts for adding a user as you won't have the priviledges to do so.

The root account is normally not recommended in Ubuntu.  Ubuntu is trying to reach an audience that shouldn't really have a need for root, and could screw some things up if they did have root access.  Hence the use of sudo.

However, you may have a special case here.  I doubt there is actually going to be a password coming from the manufacturer - they probably just install an OEM disk.  What's unfortunate is that they apparently didn't give you any instructions that would help you create your own account(s).

I'll take a look on the net for anything sounding similar for this PC and manufacturer.

In the mean time, there is a way to activate the root account.  We are not allowed by the forum rules to discuss that in the public forum for obvious reasons.  If I cannot find something to help you out, I will PM you to see if you REALLY want to activate root (I really wouldn't recommend it unless NOTHING else will work ;) ).
I'm not trying to gain access to the root account to mess around with it.  I just want to add another user for myself.  I don't think the guest account has sudo privilages as it didn't work that way when I tried it.
A friend has another device from this manufacturer and he's the one who said I may have to contact them if things like this happened.  If they don't respond back soon he's going to give me the email of the guy he's been contacting.  It should work out in the end.  No need to bend some forum rules... yet. ;)

> **Impavidus said:**
> There is a way to create a new account from the terminal and give it access to sudo. To do so you root permissions, so the trick is to boot into a recovery console, which will give you root permissions automatically. See [here]("https://wiki.ubuntu.com/RecoveryMode") for instructions on how to get into a recovery console (drop to root shell), then remount the filesystem rw with```
mount -o rw,remount /
``` (watch the spaces)
and add a user using [these]("http://askubuntu.com/questions/70236/create-an-administrator-user-in-command-line") instructions.
Thanks.  I came accross a page with that information but figured I'd try it with using the password first.  Also, it's my machine and I should have the passwords for it.

> **newb85 said:**
> Michael,
I think you're missing an important point about Ubuntu.  It's *designed* for you to safely use the administrator account that was set up on the machine when it was sent to you.  Unless you issue a command with sudo in the CLI or give the your password when asked for authentication, you don't have elevated privileges.  Adding the extra user doesn't really add any security.
I cannot get into the administrator account.  It has a password on it and I do not know what the password is.  The manufacturer who sold me the machine did not give it to me.

---

### Post by Impavidus on 2013-06-23
From the recovery console you can reset any password, including the password of any users in the sudo group: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you don't have the password, the best way to go is the recovery mode. If there is an account with sudo privileges (aka an admin account) of which they didn't give you the password, reset it using the link in this post. If you can't even find such an account, create one using the links in my previous post.

And indeed, a guest account doesn't let you do anything permanent.

---

### Post by newb85 on 2013-06-24
That's what I was going to suggest.  That's assuming, of course, that they didn't encrypt the /home directory when they set up Ubuntu on the machine.

Really, they *should* have supplied you with the password for the administrator account.  Without being able to elevate to superuser privileges, you can't add or remove programs, you can't update the system, and you can't even add a normal user.

---

### Post by Michaelocalypse on 2013-06-24
Thanks guys.  Looks like there's a few ways to do everything on these machines.
Avatar emailed me with some possible username/password combos and one of them worked.  I should probably change it now.

One more wuick question:  I can either create "standard" new user or an "administrator" new user.  I'm assuming the standard one should have sudo privilages and all that.  Just wanted to double check with you guys, even though I'm sure I could change it or delete and make a new one.

---

### Post by newb85 on 2013-06-24
> **Michaelocalypse said:**
> One more wuick question:  I can either create "standard" new user or an "administrator" new user.  I'm assuming the standard one should have sudo privilages and all that.  Just wanted to double check with you guys, even though I'm sure I could change it or delete and make a new one.

No.  An administrator account has sudo privileges, and a standard account does not.  As you are the one who will be performing administrative tasks, you want to set your account up as administrator.  That way, you can install software and updates, etc. without having to log out and log back in.

---

### Post by Michaelocalypse on 2013-06-25
Gracias mi amigo.

---

### Post by coldraven on 2013-06-25
> am still adapting to no spell check features.
In Firefox right click in any text box that has at least two lines.
Enable "Check spelling" and select your language or add dictionaries.

---

