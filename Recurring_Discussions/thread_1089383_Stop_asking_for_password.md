---
title: "Stop asking for password"
date: 2009-03-07
forum: Recurring Discussions
---

### Post by neon100 on 2009-03-07
I just want ubuntu to stop asking for my password for enabling LAN connection and for all other places

Why do i have to type password again and again when i've already typed it at login. 

How can i push ubuntu to NEVER ask my password ANYWHERE in ANY option.

I m sick.

---

### Post by underage on 2009-03-07
For security reasons, administrative tasks in Ubuntu can only be performed by users with special administrative privileges.

Administrative access can be given to individual users, who can use the sudo command to perform administrative tasks. The first user account you created on your system during installation will, by default, be able to perform administrative tasks.

When you run an application that requires administrative privileges, you will be asked to enter your user password. This ensures that rogue applications cannot damage your system, and serves as a reminder that you are about to perform administrative actions which require you to be careful!

All of the default graphical configuration tools in Ubuntu already use sudo, so they will prompt you for your password if needed.

Each time you type your password, the system remembers it for 15 minutes so that you do not have to type it again.
For more information on the sudo program and the absence of a root user in Ubuntu, read the sudo - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) page on the Ubuntu wiki. You will find how to remove password prompt for sudo.

**But, i suggest you don't enable root user nor disable password prompt for sudo.**

Your case depends on how you've created the user you have used to login and what privileges they have! If they are a part of the administrator group they can perform administrator task or administer the system.

Holla!

Underage

---

### Post by DeMus on 2009-03-07
> **neon100 said:**
> I just want ubuntu to stop asking for my password for enabling LAN connection and for all other places

Why do i have to type password again and again when i've already typed it at login. 

How can i push ubuntu to NEVER ask my password ANYWHERE in ANY option.

I m sick.

This is the benefit of having a secure operating system. In Windows XP you never had to do it, in Vista you only click the left mouse button in a simple attempt to pretend any safety. In Linux you have to let the system know it is you, acting as administrator or better as Root, doing something to (or with) the system that could inflict danger to the system. This way nobody else, local or using a network connection, can do these things to your system. And that my friend is called safety.

---

### Post by phpadik on 2009-03-07
The persistent password-checking is very helpful. It will hinder automated scripts to change settings that requires administrative privilleges. It will keep your system secure.

COOL.

If you don't really like it, then learn to love it. HAhaha.

---

### Post by 3rdalbum on 2009-03-07
Don't disable all passwords. Please. Very bad idea.

Is the dialog asking for the key/passphrase for your wireless network, or is it asking for a password to unlock your keyring? If it's asking for your wireless network's passphrase, you should create a keyring; this will ensure that your wireless password gets saved and automatically used once your keyring is unlocked every session.

Then use the option to "Unlock keyring at login", and disable automatic logins, and you will never be prompted for your password to unlock your keyring.

Unfortunately I can't give any more specific information than that - I use KDE.

---

### Post by neon100 on 2009-03-07
I've disabled the keyring and it has removed the most annoying part of this problem.

But here's my case... i am on network where i am absolutely not likely to get any threats. Also there aren't much linux virii known yet. And there's no one else who uses my PC. 

So this is why i wanted to kick the whole password thing away. and 

> If you don't really like it, then learn to love it. HAhaha.
I find it very inconsiderate. Ubuntu has philosophy that people should be able to use the software the they want to.

 But anyways. Thank you all. You people rock like always. Ubuntu rocks.:guitar:

---

### Post by chriskin on 2009-03-07
in case you still want to stop it
run sudo visudo and move the big paragraph to the end , remove the # in front of sudo and add yourself to a sudo group 
BUT
this is, the way everyone said, NOT a good idea

yet it will not make you entirely like root, it will just make the passwords less

---

### Post by danmarycap on 2009-03-11
> **3rdalbum said:**
> Don't disable all passwords. Please. Very bad idea.

Is the dialog asking for the key/passphrase for your wireless network, or is it asking for a password to unlock your keyring? If it's asking for your wireless network's passphrase, you should create a keyring; this will ensure that your wireless password gets saved and automatically used once your keyring is unlocked every session.

Then use the option to "Unlock keyring at login", and disable automatic logins, and you will never be prompted for your password to unlock your keyring.

Unfortunately I can't give any more specific information than that - I use KDE.


Thanks for the info!  I, too, want to stop some of the password pop-ups.  I'm all for entering a password to do administrative stuff, but want my wife and daughter to be able to use the netbook without having to enter a password at boot up, another one to connect to wifi, etc.

---

### Post by MaxIBoy on 2009-03-11
There's a difference between automatically remembering passwords and running around as root all the time.

You can have it remember your passwords using keyrings.


Running around as root all the time is also possible, but I could be banned from this forum for telling you how.

---

### Post by mikewhatever on 2009-03-11
> **neon100 said:**
> 

I find it very inconsiderate. Ubuntu has philosophy that people should be able to use the software the they want to.


Well, use it the way you want to, what's stopping you?
I suggest you cook it for lunch and eat it. I've eaten mine the other day, it was delicious.
Feel better now?

---

### Post by chriskin on 2009-03-11
> **mikewhatever said:**
> Well, use it the way you want to, what's stopping you?

lack of knowledge obviously

@ o.p. search the google for more , forum rules don't allow to go into further detail on this subject, sorry.

---

### Post by 3j3x on 2009-09-04
I have to say that this is by far the most obnoxious feature I've ever seen in any OS.... and I thought Vista's constant prompts to enter your password were annoying... At least the UAC feature there is easy to turn off with a few clicks of the mouse. 

Seriously, what is the worst that could possibly happen? 

In my experience not a damn thing. 

This thread is full of dire warnings of inevitable doom due to..... something....... maybe.... 

OMG, NOT ROGUE SCRIPTS!! ANYTHING BUT THAT! 

Go ahead. Disable it, log in as root. You're fine. I can honestly say that I have NEVER had a problem by disabling this "helpful" feature.

---

### Post by chriskin on 2009-09-04
> **3j3x said:**
> I have to say that this is by far the most obnoxious feature I've ever seen in any OS.... and I thought Vista's constant prompts to enter your password were annoying... At least the UAC feature there is easy to turn off with a few clicks of the mouse. 

Seriously, what is the worst that could possibly happen? 

In my experience not a damn thing. 

This thread is full of dire warnings of inevitable doom due to..... something....... maybe.... 

OMG, NOT ROGUE SCRIPTS!! ANYTHING BUT THAT! 

Go ahead. Disable it, log in as root. You're fine. I can honestly say that I have NEVER had a problem by disabling this "helpful" feature.

excuse me for grounding your attempt to sound clever, but the feature here is way cleverer AND way easier to disable than the UAC :) 

logging in as root and disabling the prompts is NOT the same thing, by the way :)

while the second shows that you don't care about extra security, the first one shows that you want to get problems :)

---

### Post by Ms_Angel_D on 2009-09-04
> **3j3x said:**
> Seriously, what is the worst that could possibly happen? 

The worst that could happen is the user deletes required system files and breaks his OS, if the user doesn't mind having to fix breaks than by all means enable root, but if your sharing your computer with others I definitely wouldn't recommend this.

> **3j3x said:**
> I have to say that this is by far the most obnoxious feature I've ever seen in any OS.... and I thought Vista's constant prompts to enter your password were annoying... At least the UAC feature there is easy to turn off with a few clicks of the mouse.

Vista's Implementation of this kind of feature was horrible. In ubuntu I'm only asked for my password for administrative features. 

sudo remembers your password for 15 minutes meaning if your performing a series of administrative tasks you don't need to constantly type in your password.

Vista's uac does not have this feature. I have been using ubuntu for about a year now, prior to this I used vista. Ubuntu's implementation of sudo is by far less annoying than uac.

When I'm not setting up a fresh install I rarely have to type my password in, unless the system is updating, or I'm installing some new software other than that I can do everything on my system without being root.

---

### Post by 3rdalbum on 2009-09-04
> **3j3x said:**
> Go ahead. Disable it, log in as root. You're fine. I can honestly say that I have NEVER had a problem by disabling this "helpful" feature.

Says the user who has only been with UF for 4 days, and this is his first post.

A lot of programs don't expect to be running as root, and don't work properly if they are. Your system becomes dramatically more vulnerable. As programs now run as root, they are more likely to get corrupted, causing you to need to reinstall the program. Programs can go out-of-control and write to every last sector on your hard disk, whereas they can't get to the last 5% if they are running as user.

No. Just don't do it.

---

### Post by t0p on 2009-09-04
**3j3x**: as has already been alluded to in this thread, it is possible to deactivate the password prompts in sudo.  This is done by editing the file /etc/sudoers with the command **visudo**.  Basically, you will need to add option ALL=NOPASSWD to your username and a list of commands.  Whether you need to list every command or there's an option that means "all commands", I don't know.  And even if I did know, I wouldn't tell you because of this site's policy on root/sudo issues.  But this information is not Top Secret Eyes Only Double-oh Seven... Google is Your Friend!

There is also a way to change your password to <nothing> (just press Return).  I'm not going to tell you how. But here's a clue: search my previous threads in these forums...

---

### Post by Commander_Keen on 2009-09-04
You know.. the Mac Os's have a very simular feature as well.
Also, if you dont' like this feature, there are other OS out there, that will allow you to have more freedom.

---

### Post by snowpine on 2009-09-04
> **3j3x said:**
> I have to say that this is by far the most obnoxious feature I've ever seen in any OS.... and I thought Vista's constant prompts to enter your password were annoying... At least the UAC feature there is easy to turn off with a few clicks of the mouse. 

Seriously, what is the worst that could possibly happen? 

In my experience not a damn thing. 

This thread is full of dire warnings of inevitable doom due to..... something....... maybe.... 

OMG, NOT ROGUE SCRIPTS!! ANYTHING BUT THAT! 

Go ahead. Disable it, log in as root. You're fine. I can honestly say that I have NEVER had a problem by disabling this "helpful" feature.

Hi there, thanks for joining the forums specifically to make this insightful posting. ;) Please understand that these are support forums... if the user doesn't care about security and doesn't follow the recommended procedures (for example enabling the locked root account), then it is much more difficult to provide support to that user. You can do whatever you want with your computer (Linux is all about freedom), but we try to provide good advice here on the official forums. :)

---

### Post by hockeytux on 2009-09-04
If you really hate typing passwords then instead of deleting the security feature altogether - why not pick a simple password like a sequence of the same number/letter? I dont recommend it but that would make it faster to type.

---

### Post by scrooge_74 on 2009-09-04
> **3j3x said:**
> I have to say that this is by far the most obnoxious feature I've ever seen in any OS.... and I thought Vista's constant prompts to enter your password were annoying... At least the UAC feature there is easy to turn off with a few clicks of the mouse. 

Seriously, what is the worst that could possibly happen? 

In my experience not a damn thing. 

This thread is full of dire warnings of inevitable doom due to..... something....... maybe.... 

OMG, NOT ROGUE SCRIPTS!! ANYTHING BUT THAT! 

Go ahead. Disable it, log in as root. You're fine. I can honestly say that I have NEVER had a problem by disabling this "helpful" feature.

humm...

Do you fit any of [these categories?]("http://ubuntuforums.org/showthread.php?t=179139&highlight=troll+definition")

---

### Post by aysiu on 2009-09-04
Read this:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

