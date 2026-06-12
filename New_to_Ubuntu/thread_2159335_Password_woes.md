---
title: "Password woes"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by sal55 on 2013-07-02
My new installation needed a password so I gave it 'abc'.

However even that is a nuisance so, on one of the GUI screens, it gave me the option to change the login password, and to have no password (shown as 'none') for logging in. Great!

However, next time I used sudo, it still asked for a password, and neither pressing Enter, nor the old abc, (nor even 'none') worked! And I can't change it to anything else (it also insists on a 'strong' password, but I want the simplest possible because this is a toy installation for messing about with writing programs, and I don't need that amount of hassle. However I can't even get that far).

What do I do now? And if I can get out of this mess (well, short of reinstalling), is it possible to run Linux so that it doesn't ask for a password every five minutes (and ideally, never)?

---

### Post by deadflowr on 2013-07-02
It seems you disabled your password, never a good idea.
Look over this on resetting it
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by sal55 on 2013-07-02
> **deadflowr said:**
> It seems you disabled your password, never a good idea.
Look over this on resetting it
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

That worked fine, thanks. (But I was installing a second virtual Ubuntu in the background just in case!)

Since I can't dispense with a password, at least it is now just a single letter.

---

### Post by ajgreeny on 2013-07-02
That is not really a good idea either!

You do not have to have a single letter password or remove the password just to set up autologin; you can edit a configuration file to do that, but we need to know what version of what OS you're running to give you more details.

You will still need to give your password when installing applications or carrying out activities that need root permissions, but that is one of the major strengths of linux that should be retained on any system, and has now been followed even by Windows, I am told, though I don't run Windows any more to know that for certain.

---

### Post by sal55 on 2013-07-02
> **ajgreeny said:**
> ...but we need to know what version of what OS you're running to give you more details.
 It's 12.04 LTS (of Ubuntu; on x86/32-bit) > You will still need to give your password when installing applications or carrying out activities that need root permissions, but that is one of the major strengths of linux that should be retained on any system, and has now been followed even by Windows, I am told, though I don't run Windows any more to know that for certain.

Some of my Windows machines have asked for a password on startup (even if it's blank, which it always is in my case!), but then it never asks again. Moreover, when is necessary to do something requiring privileges (very rare), then you need to start a program in 'administrator' mode (a right-click option), but even then no password is needed.

In Ubuntu every other command seems to involve 'sudo', and usually (not always) that needs the password.

---

### Post by BBQdave on 2013-07-02
> **sal55 said:**
> In Ubuntu every other command seems to involve 'sudo', and usually (not always) that needs the password.

Wow :)

You should understand that part of what hardens a Linux Distro - protects it from attack and keeps your system healthy - is a **STRONG PASSWORD**.

This is the complete opposite of what you wish; but I would set your admin user, SUDO, with at least 12 characters of lower and upper case letters and numbers too - no words.

Example of remembering a random PASSWORD: [COLOR=#ff0000]**m**[/COLOR]y [COLOR=#ff0000]**S**[/COLOR]uper [COLOR=#ff0000]**c**[/COLOR]amero [COLOR=#ff0000]**f**[/COLOR]rom [COLOR=#ff0000]**78**[/COLOR] [COLOR=#ff0000]**R**[/COLOR]umbles [COLOR=#ff0000]**L**[/COLOR]oud = [COLOR=#ff0000]**mScf78RL**[/COLOR]

---

### Post by Kopkins on 2013-07-02
Without a password or with a simple password your computer could become extremely vulnerable. If you went to a public network someone could easily browse computers on the network and when they try to gain access to yours they face little resistance. Then they have all your files or ruin your install. 

Good Luck,

Kopkins

---

### Post by deadflowr on 2013-07-03
> [COLOR=#000000]Some of my Windows machines have asked for a password on startup (even if it's blank, which it always is in my case!), but then it never asks again. Moreover, when is necessary to do something requiring privileges (very rare), then you need to start a program in 'administrator' mode (a right-click option), but even then no password is needed.[/COLOR]

This is why there is a thriving anti-virus industry.:P

---

### Post by Vormeph on 2013-07-03
Having a password is a must on Linux, imo. You need it to perform adminstrative tasks, from installing software to using sudo. If you are part of a server, then you should set a strong password. If you are just a home user then any password would do so long as you don't give it away. Change your password to something more rememberable and acronymic. Remember, one of the things that make Linux secure is the fact you need to supply a password for every change in the system.

---

### Post by mastablasta on 2013-07-03
> **deadflowr said:**
> This is why there is a thriving anti-virus industry.:P

exactly. malware knows how to "right click" to run as admin. but they will have a hard time guessing your linux password in order to be able to do system changes. it is yet another security layer that makes linux by default more secure than windows.

---

### Post by Zill on 2013-07-03
> **sal55 said:**
> My new installation needed a password so I gave it 'abc'...
... and 'abc' on its own is actually "off the scale" on the [Scary Logins]("http://www.prweb.com/releases/2012/10/prweb10046001.htm") list. ;-)

---

### Post by sal55 on 2013-07-03
> **Kopkins said:**
> Without a password or with a simple password your computer could become extremely vulnerable. If you went to a public network someone could easily browse computers on the network and when they try to gain access to yours they face little resistance. Then they have all your files or ruin your install. 


OK, I'll keep these points in mind.

However my Linux runs on a virtual PC, and is only for experimenting and learning (specifically, programming stuff). It could probably be completely wiped out and it wouldn't really matter (source code is kept on the host).

It does have links to the host computer, and internet access, so there are some risks; so I will probably restrict access to the host to just a few directories, and possibly make those read-only, and I can disable the internet too (it's only really needed for 'apt-get install', but the system seems stable at the moment).

---

### Post by sal55 on 2013-07-03
> **Zill said:**
> ... and 'abc' on its own is actually "off the scale" on the [Scary Logins]("http://www.prweb.com/releases/2012/10/prweb10046001.htm") list. ;-)

How about just 'a' ? BTW that list gave me some good ideas...

---

### Post by SimTech68 on 2013-07-03
The idea is to at least have a password on you admin acct or since I have worked with Unix, the root account. The idea of a password is to protect your stuff. The same reason we lock our doors for our house, or to out cars, or our desk or locker. Your get the point.

Maybe if you would have stated you last post as your first people would have understood what you are trying to do. You stated that you have this as a learning tool, well why don't you see if you can fine the code and disable the password protect or change it so it's not required. Then report what you have done, there are probably others that are just as interested as you to work with Linux based software but get annoyed with silly password. But understand that the basis of this software structure is to keep separate the  kernel(core) from from the userland and that is done with passwords/passcodes......It just the nature of the software, what you are asking is similar to asking a songbird not to sing, or the sun not to shine and so on.

---

### Post by newb85 on 2013-07-03
Reminds me of when I was managing apartments in college, and one of the tenants had opened the deadbolt in his apartment and dumped it all the pounds and tumblers so that any key would unlock it.

---

