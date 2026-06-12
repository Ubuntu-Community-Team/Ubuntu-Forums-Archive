---
title: "Configuring Samba"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by Luc_Lacombe on 2013-11-01
Hello again

I remember few years ago I installed Samba in an old version of Ubuntu and it worked fine.
I guess things have changed since as it was version 7.04 of Ubuntu.
So I want to be sure to avoid polluting this version 12.04 of Ubuntu.
You guess I want to have complete fluent network with other XP and W7 computers.
Now read this...
As soon as this Ubuntu installation was achieved I was able to see and have access to file in my other W$ computers but in only one side.
I understand the communication is not reciprocal and this were I need your help!

Then I first created a folder called  "SF-Ubuntu"  in a separate partition (NTFS) and also created a link from it that I placed in my Ubuntu desktop.
Then I proceeded to make this folder to become sharable, right click of /properties/share and clicking "Share this folder".
I thought this would finalize the functionning of my network as it "dealt" with Samba and installed "few things" using the word Samba.
But I reralized I was wrong.
So this is where I need you here.
The question : What do I have to do get the network job "dancin'" and make perfect bi-directionnal fluidity in this network?
I don't know if this is of importance but I have to warn you that this computer is a dual-boot with a separate disk for Win-XP and everything is perfect here, thanks to Grub.
I know perfectly I need Samba but like I told you...I want to make things right the first time and keep a clean machine.
Thanks!

Luc Lacombe

---

### Post by newb85 on 2013-11-01
The first thing to come to mind is that you need to configure samba.  You at least need to establish the authentication method and what user (s) have access.

---

### Post by Luc_Lacombe on 2013-11-01
Hello newb85

Good start but do you have more that comes to mind? :D
You know...I'm almost new as an Ubuntu user.

Luc

---

### Post by tgalati4 on 2013-11-01
The first lesson:  SAMBA consists of two parts:  A server, which serves up the files and a client, which asks for the files.

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

How can you be a new user?  You have been using Ubuntu since April of 2007.  That is 6 and 1/2 years.  

But I digress.

---

### Post by PeterRJG on 2013-11-01
> **tgalati4 said:**
> 

How can you be a new user?  You have been using Ubuntu since April of 2007.  That is 6 and 1/2 years.  



Easy. The OP used it for a day or a week or so, decided it wasn't for him, went back to whatever he was using and comes back to Linux 6 and a half years later. What a strange assumption to think he's been using it continuously....

@ the OP: this guide *may* help. [http://ulujain.org/random/sambalinux.shtml](http://ulujain.org/random/sambalinux.shtml) The link to Werdna down the bottom of that page has more comprehensive info

---

### Post by bab1 on 2013-11-01
> **Luc_Lacombe said:**
> ...
The question : What do I have to do get the network job "dancin'" and make perfect bi-directionnal fluidity in this network?
...

I know perfectly I need Samba but like I told you...I want to make things right the first time and keep a clean machine.
Thanks!

Luc Lacombe

Be careful of what distro and version the help describes.  Ubuntu is not the same as SUSE or RedHat.  For the latest Ubuntu using Samba I would  follow this:  [http://www.jonathanmoeller.com/screed/?p=4169]("http://www.jonathanmoeller.com/screed/?p=4169")

---

### Post by bab1 on 2013-11-01
> **PeterRJG said:**
> 
@ the OP: this guide *may* help. [http://ulujain.org/random/sambalinux.shtml](http://ulujain.org/random/sambalinux.shtml) The link to Werdna down the bottom of that page has more comprehensive info

This information is misleading for a newbie.  It will cause endless hours of Samba pain since It is based on Redhat and therefore different in many ways to Ubuntu (and Debian) style distros.

---

### Post by Luc_Lacombe on 2013-11-01
> **PeterRJG said:**
> Easy. The OP used it for a day or a week or so, decided it wasn't for him, went back to whatever he was using and comes back to Linux 6 and a half years later. What a strange assumption to think he's been using it continuously....

@ the OP: this guide *may* help. [http://ulujain.org/random/sambalinux.shtml](http://ulujain.org/random/sambalinux.shtml) The link to Werdna down the bottom of that page has more comprehensive info

                                                                                                                                                                                                     [URL="http://ubuntuforums.org/showthread.php?t=2185165&p=12835695#post12835695"]#4

[/URL]                                                                                                                                                                                                                                                           [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar241895_2.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=241895")                                                                                    


 [**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895")

This is the best answer i can give you! Cannot be said better!

Luc

---

### Post by Luc_Lacombe on 2013-11-01
> **bab1 said:**
> This information is misleading for a newbie.  It will cause endless hours of Samba pain since It is based on Redhat and therefore different in many ways to Ubuntu (and Debian) style distros.

Yes you're right.
Different versions can be misleading.
Like I said I want to stay clean...no blur!
My actual version is 12.04.
Any other suggestions?
By the way, thanks for all your answers![IMG]http://ubuntuforums.org/images/icons/icon14.png[/IMG]

Luc

---

### Post by PeterRJG on 2013-11-01
> **bab1 said:**
> This information is misleading for a newbie.  It will cause endless hours of Samba pain since It is based on Redhat and therefore different in many ways to Ubuntu (and Debian) style distros.

Hmm, wasn't aware of that. It's actually a Fuduntu (RIP) tutorial. Well, that's another illusion shattered, that Samba is the same on all distros.

---

### Post by bab1 on 2013-11-01
> **PeterRJG said:**
> Hmm, wasn't aware of that. It's actually a Fuduntu (RIP) tutorial. Well, that's another illusion shattered, that Samba is the same on all distros.
Samba is the same.  That OS uses RPM to install and Ubuntu uses APT.  The file OS's system is laid out differently and  there is no *wheel* group in Ubuntu/Debian.  Even using same distro there will always be version changes.  Early versions of Ubuntu don't start the *smbd* and *nmbd* daemons the same way as the later versions.

---

### Post by tgalati4 on 2013-11-01
To the OP, I apologize for my trolling comment.  Yes, I realize that you have not been using Ubuntu for 6 and 1/2 years.  Otherwise you would not be asking this question.  

Just keep at it.  SAMBA is an extensive framework that has been around a long time.  It is similar across distros, but there are differences and you will see them as you look for tutorials.

Current information can be found at:

```
man samba
man smb.conf
```

But manual pages are tough reading for new people.

---

### Post by Luc_Lacombe on 2013-11-01
> **tgalati4 said:**
> To the OP, I apologize for my trolling comment.  Yes, I realize that you have not been using Ubuntu for 6 and 1/2 years.  Otherwise you would not be asking this question.  

Just keep at it.  SAMBA is an extensive framework that has been around a long time.  It is similar across distros, but there are differences and you will see them as you look for tutorials.

Current information can be found at:

```
man samba
man smb.conf
```

But manual pages are tough reading for new people.

Hello tgalati4

You don't have to apologize as I didn't take it bad!
I know you were jokin'.
PetrRJG had a perfect fit answer that I quoted.
OK.
About this:
"```
man samba
man smb.conf
```"

What do you mean by (code) ?

Luc

---

### Post by newb85 on 2013-11-01
Those are terminal commands.  The easiest way to access the manual pages (man pages) in Ubuntu is through a terminal.  Ctrl+Alt+T will bring it up in any Ubuntu using Unity.  Then type the first line and hit Enter.  You'll see the man page for samba.  Hit "q" to exit the man page and return to the command prompt.  Enter the second line and hit Enter.  You'll see the man page for the file smb.conf (a samba configuration file).  Again "q" will return you to the command prompt.

---

