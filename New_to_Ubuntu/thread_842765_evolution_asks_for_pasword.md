---
title: "evolution asks for pasword"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by azery on 2008-06-27
I recently installed the new ubuntu (8.04) but I'm having a number of problems. Being new to Linux, I'm looking here for some help. I'll post different problems in different topics, in order improve the readability of the answers.

The third problem is evolution:

Ubuntu is set to login automatically the default user (so not login during boot). As a result, evolution asks for the admin password to unlock the default keyring.

No, I used auto login in order to avoid typing my password and it results in typing my password every time I check my email (well ,the first time after booting)

Can evolution not remember the password?

---

### Post by Nxion on 2008-06-27
You can set evolution to remember it. It sounds like in this case it is asking you for your EMAIL password and not the local admin password. Are you using IMAP or POP? And vy default the security is set to ask for a password when accessing a keyring. I dont belive there is anyway to shut that off, That would be unsecure if you do that. To be honest I dont belive therre is a way to turn it off to not ask for a password any more. Some applications require a password. For example if you run "apt-get upgrade" It will always ask you because it is changing a systme variable. If you turn that abily off, your system is unsecure.

---

### Post by azery on 2008-06-28
it is not asking my email password, it has to be the admin password.

I have no problem in providing the root password when installing software, updates, etc. But for checking email, I find that unacceptable. That would mean that all users, root or not, need to know the root password for something simple as checking email! Not even Microsoft is that stupid.

Looking on the internet, it seems that you are right. I even found a thread ([https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264)) with users and programmers discussing whether this is a bug or not. The users stated it should be a bug, but apparently, they are not willing to consider it a such.

Anyhow, thanks for the reply.

Seems there is no solution...

---

### Post by Troll_the_Great on 2008-06-28
Hy.I was wondering if you have a yahoo plus acount in order to work with evolution.

---

### Post by lisati on 2008-06-28
> **Troll_the_Great said:**
> Hy.I was wondering if you have a yahoo plus acount in order to work with evolution.
Sometimes you do, sometimes you don't - it depends on where you live. I have several free "yahoo.co.nz" email accounts, and all I needed to do was to enable POP access from within yahoo mail. I think this might not work if you have a free yahoo.com account.

EDIT: And don't forget to tell Evolution/Thunderbird/whatever to remember your (email) password if your choice of client provides that option....

---

### Post by mcduck on 2008-06-28
> **azery said:**
> it is not asking my email password, it has to be the admin password.

I have no problem in providing the root password when installing software, updates, etc. But for checking email, I find that unacceptable. That would mean that all users, root or not, need to know the root password for something simple as checking email! Not even Microsoft is that stupid.


It's not asking for admin password. There isn't any in Ubuntu. It's asking the current user's password to unlock that user's keyring.

So the password isn't the same for alll users, there's no need to give your password to other users. They unlock their own keyrings with their own passwords.

(Sure, it can be confusing that you use the same password for 3 things, as your own user password, as the password to gain admin privileges (still not root password but user's own password!) and the password to your keyring.)

Even if you had another user on your machine and you gave him admin rights he wouldn't be using same password for asdmin tasks as you are, but his own password instead.

---

### Post by Elfy on 2008-06-28
I was looking at this issue a few months ago and I think that the only way is to not login automatically.

There was some tlak about a bug - but it's not  abug but a security measure :)
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/236264)

This thread details one way of dealing with it, with only some degree of success

[http://ohioloco.ubuntuforums.org/showthread.php?t=814271](http://ohioloco.ubuntuforums.org/showthread.php?t=814271)

---

### Post by azery on 2008-06-30
seems I will have to live with it.

Giving different users different passwords is not a solution. I would have to disable autologin so that each user can login.

Switching from windows XP to linux, this is unfortunately the first big issue I find. I can understand why the behavior is the way it is, but I nevertheless find it unacceptable: autologin is there to avoid typing passwords and now evolution is forcing me to do so... One way or the other, the autologin should tell the OS the password.


Well, nothing is perfect. Thanks for the advice. (and I'm still not switching back to windows :-)

---

### Post by The Cog on 2008-06-30
It's not the only bug they've introduced into Evolution recently. Every time I try to compose a mail, my CPU rockets and so does my LAN usage - pestering the daylights out of the exchange server. I have to stop and restart Evolution after every mail I send. I'm in the process of loading KDE to see if Evolution is as badly broken there - at least there won't be a gnome keyring.

---

### Post by Gorlist on 2008-07-02
I assumed it was just a bug in Evo. or Ubuntu, but reinstalled yesterday and Evolution is still asking for the password to unlock the keyring. 

The only thing that's a bit bizarre is if it is really for security why ask when you want to send & receive? it should be as the program loads, because at the moment anyone can still read what you already have downloaded...

If its not a bug, then it should be an optional extra for the user, and not an imposed requirement.

Regards,

---

### Post by luke16 on 2008-07-02
How is this a security feature? The user has already elected to be logged in automatically for the exact reason to avoid being nagged at for a password. Whoever has access to the computer already has access to everything else in the user directory, so what exactly does nagging the user for yet another password to simply check his email make the machine more secure?
I just can't see this as anything more than a bug.

---

### Post by abgemacht on 2008-07-02
Why don't you try something different, like Thunderbird?  Not the best solution, but if Evolution isn't doing what you want...

---

### Post by gandaran on 2008-07-02
this evolution keyring thing has been around a long time in other distros, like mandriva and opensuse, ubuntu was an exception, dunno why they introduced this feature now!
but you can easily setup the keyring with no password at all, this way evolution or any other app won't ask you for the keyring password

---

