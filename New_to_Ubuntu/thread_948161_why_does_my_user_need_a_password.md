---
title: "why does my user need a password?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by DetroitLibertyPenguin on 2008-10-14
Why am I not able to have a user that doesn't require a password?

I am the only individual who uses this machine, though in theory I suppose some random person in my house could jump on. When I set up the initial install of Xubuntu would not let me one user "jim" have no password. 

I would like to have the one user not need a password, so that I could turn the computer on and then go about my business, make coffee etc., and then come back and everything would be up and running. Now if I do that the process only gets about half way done because I need to enter my user name and password.

That being said, why in the world is the user password and the super user password the same? This makes no sense to me. Shouldn't the su have to be different? 

So, what do I need to configure, and how do I need to configure it, so that my user has no password, and there is a separate password for root access. I know ubuntu is still Linux, so there has to be a way to do it.

---

### Post by JoshuaRL on 2008-10-14
Debian does that, has a separate root password.  But Ubuntu was set up to have a password for sudo access, and not have a separate login password.  It's just a security decision Ubuntu made.

---

### Post by cardinals_fan on 2008-10-14
You can set up autologin to alleviate the password-entering.

As for the root password, Ubuntu doesn't set it by default.  I personally think this is stupid, but that's how they chose to do it.  If you want a root password, for su or anything else, Google it.  I will respect the wishes of the forum admins by not explaining it here.

---

### Post by Victormd on 2008-10-14
You can set it to auto login. I'm not sure what the proper shortcut would be in xubuntu but in ubuntu, it's under SYSTEM>ADMINISTRATION>LOGIN WINDOW
or open a terminal and type:
```
gksu /usr/sbin/gdmsetup
```

Then, open the SECURITY tab and mark "Enable Automatic Login"

You can setup the different passwords with:
```
users-admin
```

I know these are the commands for Ubuntu and I think they would be the same for Xubuntu, but I'm not sure...

**[COLOR="Red"]Note: Changing these settings may make your computer vulnerable and you should exercise care when doing this.[/COLOR]**

---

### Post by patrickballeux on 2008-10-14
Go in System - Administration - (Connection Login Parameter?).

In there you can select to auto-login your session with the user you selected, without having to enter your password...
(See Security Tab)

(My setup is in french, So I don't know how "Fenêtre de connexions" is called in english).

---

### Post by Victormd on 2008-10-15
> **cardinals_fan said:**
> If you want a root password, for su or anything else, Google it.  I will respect the wishes of the forum admins by not explaining it here.

We can't explain/teach this?

---

### Post by scragar on 2008-10-15
Well the reason for the password is that it's a big reason for the linux security and stability, not letting any old program start messing with important files because the user needs to enter the password to give it permtition(which is much harder to fake than just boosting your privilages on some other security methods).

According to the forum rules I'm not supposed to show you how to disable this stuff without letting you know how dangerous to security it is, but as long as you understand that removing the password reduces you to a level of securty most windows systems have(where in everyone is using an admin privilaged account so they can install things) then it's all good.


first, open a terminal, that'll make things easy:```
gksudo gdmsetup
```
Go to security, enable automatic login.

[follow this guide](https://help.ubuntu.com/community/RootSudo#Remove Password Prompt For sudo) to turn off the password to get admin rights,

---

### Post by Tatty on 2008-10-15
> **Victormd said:**
> We can't explain/teach this?

Making changes such as enabling a root password or having a machine with no passwords at all are considered to be very dangerous moves.  Generally the admins/mods in these forums hold the view that if a person does not know how to do this (or how to find out how to do this) then they should not be considering it as it will most likely cause things to fall apart.

As such, this sort of information tends to be kept off these forums.

> **DetroitLibertyPenguin said:**
> 
I am the only individual who uses this machine, though in theory I suppose some random person in my house could jump on. When I set up the initial install of Xubuntu would not let me one user "jim" have no password. 

Is your computer connected to the internet / a network?  If so then you are not the only person with access to it.


Making your computer automatically log in to a specified session on boot however is something you can do quite easily.  Go to System->Administration->Login Window, then go to the Security tab.

---

### Post by DetroitLibertyPenguin on 2008-10-15
Thanks a lot to all!

I was amazed how quickly this was responded to, as the other posts I've put on this forum either were not responded to or took days for someone to respond to. (One of the big fall backs Ubunutu had to Mandriva, my previously installed distro). 

You all did a much better job of explaining to me what the Linux password does. Instead of simply "don't be root, its just a bad idea"

The autologin has been changed, which in all honesty was my major concern. I didn't have an ADMINISTRATION under the applications, system, however, as usual the terminal link worked. The more I use Linux the more i learn that the command prompt is the quicker, easies, better way to do most everything! (I love seeing my computer work instead of it being a mystery, hooray for Linux!) 

That being said, with your comment about the root password that does give me an additional question. Mandriva required you to use a root password, is there a difference between the Ubunutu to "sudo" command and the Mandriva "su" command?

---

### Post by DetroitLibertyPenguin on 2008-10-15
how do i delete this second post that I accidentally added?

---

### Post by scragar on 2008-10-15
> **DetroitLibertyPenguin said:**
> Thanks a lot to all!

I was amazed how quickly this was responded to, as the other posts I've put on this forum either were not responded to or took days for someone to respond to. (One of the big fall backs Ubunutu had to Mandriva, my previously installed distro). 

You all did a much better job of explaining to me what the Linux password does. Instead of simply "don't be root, its just a bad idea"

The autologin has been changed, which in all honesty was my major concern. I didn't have an ADMINISTRATION under the applications, system, however, as usual the terminal link worked. The more I use Linux the more i learn that the command prompt is the quicker, easies, better way to do most everything! (I love seeing my computer work instead of it being a mystery, hooray for Linux!) 

That being said, with your comment about the root password that does give me an additional question. Mandriva required you to use a root password, is there a difference between the Ubunutu to "sudo" command and the Mandriva "su" command?

sudo gives admin rights for 1 command
su gives admin rights until you decide to drop back to normal use

both have good and bad points(sudo is annoying for long lines of commands, su is more likely to leave you just staying in root since you never need to drop out of it)

---

### Post by eentonig on 2008-10-15
yes and no.


"su" allows you to become another user (which is possible in Ubuntu as well)

"sudo" allows you to run a program with admin rights, on behalf of you own user account.

The latter has some benefits for which I personnally prefer it. Amongst other things, with sudo it's easier to keep track who performed which admin task.

There's some good explanation regarding the why and how of  "sudo" usage in Ubuntu in the ubuntu Wiki.

---

### Post by SunnyRabbiera on 2008-10-15
> **DetroitLibertyPenguin said:**
> Thanks a lot to all!

I was amazed how quickly this was responded to, as the other posts I've put on this forum either were not responded to or took days for someone to respond to. (One of the big fall backs Ubunutu had to Mandriva, my previously installed distro). 

You all did a much better job of explaining to me what the Linux password does. Instead of simply "don't be root, its just a bad idea"

The autologin has been changed, which in all honesty was my major concern. I didn't have an ADMINISTRATION under the applications, system, however, as usual the terminal link worked. The more I use Linux the more i learn that the command prompt is the quicker, easies, better way to do most everything! (I love seeing my computer work instead of it being a mystery, hooray for Linux!) 

That being said, with your comment about the root password that does give me an additional question. Mandriva required you to use a root password, is there a difference between the Ubunutu to "sudo" command and the Mandriva "su" command?

sudo stands for super user do, basically it gives root access without the need of a root account or password.
Mandriva and ubuntu follow different but similar security approaches, mandriva uses a similar process to sudo by allowing temporary root access but it also disables root at the same time.
Usually though its a good idea not to use auto logins and the like as they dont encourage proper security practices... I guess thats why I dont like Mandriva 2009 other then its now using KDE4.
I know it sounds silly to have to type in your password each time you log in and you are the only user but in the long term its a better idea not to have auto login enabled.

---

### Post by Tatty on 2008-10-15
> **DetroitLibertyPenguin said:**
> That being said, with your comment about the root password that does give me an additional question. Mandriva required you to use a root password, is there a difference between the Ubunutu to "sudo" command and the Mandriva "su" command?

su means SuperUser.  So when you run su, you are elevated to super-user privilages until you decide you no longer want them.

sudo means SuperUser Do [this command].  So it basically gives you superuser privilages for that one command only.

The benefits of "su" vs "sudo" have been hotly debated for years in the linux community, a quick google will find you plenty of pages on them.  sudo is just the method which is favoured by Ubuntu.

---

### Post by scragar on 2008-10-15
> **Tatty said:**
> su means SuperUser.  So when you run su, you are elevated to super-user privilages until you decide you no longer want them.

sudo means SuperUser Do [this command].  So it basically gives you superuser privilages for that one command only.

The benefits of "su" vs "sudo" have been hotly debated for years in the linux community, a quick google will find you plenty of pages on them.  sudo is just the method which is favoured by Ubuntu.

su is switch user, it's just that if you don't specify a user(EG```
su bob
```) it defaults to root.

---

### Post by jerome1232 on 2008-10-15
su - switch user
sudo - super user do


In Mandriva you were actually switching to the root account. Generally only accounts in the group 'wheel' are allowed to do this. You have one root account that can do admin tasks.

(disabled by default in ubuntu for security reasons, we don't want people logging in to x as root and making their system very vulnerable to attack)

In Ubuntu you're temporarily giving you own account the same powers as a root account, sudo can also be used to run as any other user on the system. Only accounts that are in the 'admin' group are allowed to use the sudo command. You can also customize sudo to allow certain groups to be half-admins and such. All and all they are both considered about as secure as the other while sudo allows for customization, and you don't have to give out your one master password to people.

---

### Post by cardinals_fan on 2008-10-15
> **DetroitLibertyPenguin said:**
> 
That being said, with your comment about the root password that does give me an additional question. Mandriva required you to use a root password, is there a difference between the Ubunutu to "sudo" command and the Mandriva "su" command?
Ubuntu has a 15-minute timeout set on (gk)sudo.  I think that this is terrible security.  If you want to set it to zero (I would), read this: [http://ubuntuforums.org/showthread.php?p=116697#post116697](http://ubuntuforums.org/showthread.php?p=116697#post116697)

---

### Post by DetroitLibertyPenguin on 2008-10-29
nope, no desire to do that. 

and just to answer your questions before they come: Yes, I do leave my door unlocked, and the keys in my ignition of my Pickup. Yes, I do live in a large metropolitan area, as you can tell from my user name. I did get my bike stolen last week, but I have no intention on changing my ways.

---

