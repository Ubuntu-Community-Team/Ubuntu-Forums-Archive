---
title: "how to remove all passwords"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by wilbur46 on 2011-10-29
hi linux users.
I recently installed ubuntu 11 on my dell laptop.
after some screwing around with the wireless install i got it working.
i hate passwords. no one else has access to my computer and i would not care if they did.
i would like to be able to update software, and at least log on without this pain in the butt.
please point me to a tutorial (preferably a visual one) which explains how to totally eliminate the need for any passwords. especially administrator passwords.
thanks  W

---

### Post by haqking on 2011-10-29
> **wilbur46 said:**
> hi linux users.
I recently installed ubuntu 11 on my dell laptop.
after some screwing around with the wireless install i got it working.
i hate passwords. no one else has access to my computer and i would not care if they did.
i would like to be able to update software, and at least log on without this pain in the butt.
please point me to a tutorial (preferably a visual one) which explains how to totally eliminate the need for any passwords. especially administrator passwords.
thanks  W

it is not recommened nor supported here.

It is not just about logging on locally, it is about services and scripts (in web browsers) having admin privelege.

If you do what you request you are likely to trash your machine, get 0wN3d very quickly.

Read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") and the security stickies in my signature

---

### Post by Paqman on 2011-10-29
> **wilbur46 said:**
> no one else has access to my computer

If you connect to the internet, billions of people and machines have access to your computer. Lowering your defences will just make you an easy target.

---

### Post by wilbur46 on 2011-10-29
thanks for the reply. i checked your bio. you obviously know what you are doing, but i do not.
I really just want to boot straight to my desktop without having to enter a user password.
I would also like to check for updates or download the newer versions
I keep getting the no privilege box.
I guess this is why i originally built a custom version of puppy, but i thought i might try a complete distro.
i understand the security concerns.
there are so many requests for this info in the forums that i think it need a more complete sticky.
thanks again   W

---

### Post by Paqman on 2011-10-29
> **wilbur46 said:**
> 
I really just want to boot straight to my desktop without having to enter a user password.

You can set the system to log you in automatically, but if you need to connect to wifi you would still have to enter your password. What version are you running?

> 
I would also like to check for updates or download the newer versions


You can have it install the security update automatically, go to Software Sources to enable this. For all the rest of the updates, you'll just have to enter your password.

---

### Post by RedRat on 2011-10-29
I think you are embarking on very dangerous grounds, especially if you are using a wireless router that is not secured. You may well find your computer becoming a zombie and contributing to the overall problems our our Internet. You may find that someone else has found your network and is using either your computer or wireless to download tons of material. Some IPs do not tolerate this and will send you a notice. 

What you are describing is the old days of Windows and Mac. This is just not a safe practice either for you or others.

---

### Post by tartalo on 2011-10-29
Autologin in 11.10:
[http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/](http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/)

I don't think it's such a security breach, anyone with physical access to the computer has access to anything unless you encrypted the file system, which I doubt. I'd appreciate a correction if I'm wrong.

---

### Post by haqking on 2011-10-29
> **tartalo said:**
> Autologin in 11.10:
[http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/](http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/)

I don't think it's such a security breach, anyone with physical access to the computer has access to anything unless you encrypted the file system, which I doubt. I'd appreciate a correction if I'm wrong.

autologin is not the issue so much as physical access is root access.

The OP is asking to remove the need for any admin passwords and this is not receommended for many reasons as pointed out above

You can configure autologin and configure your keyring to have a blank password if you so wish though not recommended but eliminates some of your issues.

However admin passwords for admin tasks should remain in place at all times.

---

### Post by haqking on 2011-10-29
Edit: Double Post

---

### Post by nothingspecial on 2011-10-29
Hi wilbur46,

This has been discussed many, many, many, times.

If you would like to disable your password completely you will have to go elsewhere.

You have been shown how to login without a password.

Think of it this way.......

Your computer is your house.

If you are connected to the internet then your house is in the roughest, toughest area of the town full of countless thieves, swindlers, robbers, fraudsters etc

Your password is the key to your frontdoor.


Do you want to go to bed or out with your frontdoor wide open?

---

### Post by wilbur46 on 2011-10-30
thanks for all replies.
this is always the problem with changing to a new os.
i haven't figured it out yet, which is why i'm asking in  absolute beginner talk.

Sometimes you just don't even know how to ask the appropriate question.
authentication password is my problem. i've been scratchin my head but can't get the password right.
can i somehow recover it?

While i appreciate all help, i really don't need to be lectured. i'm not trying to sabotage the internet here

Ask me about the relative aspects of dynamic balancing--reciprocal vs. rotating, and i can either try explaining in terms you can understand, or i can "assume you know what you're doing"

---

### Post by HermanAB on 2011-10-30
Howdy,

You got to boot into single user mode, then reset the password.

At the grub boot menu select the "Recovery" option, this will boot you into single user mode as root where you can reset your password:

Code: passwd username

---

### Post by haqking on 2011-10-30
> **wilbur46 said:**
> thanks for all replies.
this is always the problem with changing to a new os.
i haven't figured it out yet, which is why i'm asking in  absolute beginner talk.

Sometimes you just don't even know how to ask the appropriate question.
authentication password is my problem. i've been scratchin my head but can't get the password right.
can i somehow recover it?

While i appreciate all help, i really don't need to be lectured. i'm not trying to sabotage the internet here

Ask me about the relative aspects of dynamic balancing--reciprocal vs. rotating, and i can either try explaining in terms you can understand, or i can "assume you know what you're doing"

ok as mentioned above yes you can do that.

See here [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by philinux on 2011-10-30
> **wilbur46 said:**
> hi linux users.
I recently installed ubuntu 11 on my dell laptop.
after some screwing around with the wireless install i got it working.
i hate passwords. no one else has access to my computer and i would not care if they did.
i would like to be able to update software, and at least log on without this pain in the butt.
please point me to a tutorial (preferably a visual one) which explains how to totally eliminate the need for any passwords. especially administrator passwords.
thanks  W

For your two needs it is easy. 

1 set your system to auto login.

2 in 11.10 software updates via update manager etc no longer need a password. Only needed to install new software.

---

### Post by Humber on 2012-07-04
> **haqking said:**
> it is not recommened nor supported here.
It is not just about logging on locally, it is about services and scripts (in web browsers) having admin privelege.
If you do what you request you are likely to trash your machine, get 0wN3d very quickly.
Read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") and the security stickies in my signature

I was under the impression Ubuntu (and all distros of Linux) were configurable, so much so that people could tweak them to their tastes. It seems to me you don't understand the basic concept of people assuming responsibilty for their actions and would rather have the entire Ubuntu community act as babysitter for those of us who have decided to assume whatever no-password risk there might be. Looks a little like when the government says it's there to help you. Yeah, right.

I strongly believe this attitude is far WORSE than being prompted for a password every 2 minutes.

---

### Post by Zill on 2012-07-04
> **Humber said:**
> I was under the impression Ubuntu (and all distros of Linux) were configurable, so much so that people could tweak them to their tastes...
And, of course, Linux systems remain configurable - you have the source code to do with it what you will!  Just don't expect too much help in breaking the security model from other, more responsible, users. 
> **Humber said:**
> It seems to me you don't understand the basic concept of people assuming responsibilty for their actions and would rather have the entire Ubuntu community act as babysitter for those of us who have decided to assume whatever no-password risk there might be...
The "Ubuntu community", in general, recognise the great security problems that arise if good passwords are not used.  These problems are not limited to the specific user but are, if the system is connected to the internet, a source of much of the spam that plagues *all* internet users.  Unprotected systems are hijacked by spammers and, while most of these machines probably run Windows, running Linux machines in the same way inevitably leads to these machines being attacked as well.

---

### Post by haqking on 2012-07-04
> **Humber said:**
> I was under the impression Ubuntu (and all distros of Linux) were configurable, so much so that people could tweak them to their tastes. It seems to me you don't understand the basic concept of people assuming responsibilty for their actions and would rather have the entire Ubuntu community act as babysitter for those of us who have decided to assume whatever no-password risk there might be. Looks a little like when the government says it's there to help you. Yeah, right.

I strongly believe this attitude is far WORSE than being prompted for a password every 2 minutes.

and it is still not supported here, regardless of what i think or assume.


Peace

---

### Post by Paqman on 2012-07-04
> **Humber said:**
> It seems to me you don't understand the basic concept of people assuming responsibilty for their actions 

No, the advice was given precisely because it was assumed that the user would have to assume responsibility for their ill-advised actions.

---

