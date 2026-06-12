---
title: "Just how secure is Linux?"
date: 2009-09-30
forum: Recurring Discussions
---

### Post by JohneG on 2009-09-30
And what should i be aware of?

---

### Post by taseedorf on 2009-09-30
One big thing, we careful doing routines or commands as root.  You can actually do some damage.  Make sure your firewall is set up properly.  If you are new to Linux, Firestarter is a good firewall gui.  For the average user, you won't have to worry about a lot.  Virus and spyware of the like are not very common on a Linux box.  Also, on normal day to day use it is nice to login as a user who does not have root privileges.

---

### Post by BQAggie2006 on 2009-09-30
What Linux distribution will you be using and what will you be using your computer for (personal computing, server, etc)? 

In general, Linux distributions are stable and secure; however, there are things that users do (web, email, P2P) or configure their distribution to do (web hosting, file sharing) that can increase  risk to the machine's security. Because of this, we need to know what you will be using your computer for to better help you understand what precautions you should take and what you should be aware of.

---

### Post by JohneG on 2009-09-30
I am using Ubuntu Jaunty. I use it for Internet (very little past researching and email accounts. No facebook or any of that crap), listening to music, Photo editing, Audio production, General office apps, Watching dvds etc

---

### Post by credobyte on 2009-09-30
Enough secure to not to worry about it. If you are too concerned about viruses and such, install Avast ( home editions, as always, for free ).

---

### Post by fela on 2009-09-30
> **taseedorf said:**
> Also, on normal day to day use it is nice to login as a user who does not have root privileges.

Not nice - essential. You should never login as root unless it's temporary and just for a certain task such as installing some software - and even then you can use sudo instead if you have it installed.

I think the best security policy with Linux and computers in general is just to use your common sense. You can get the best £1000 lock for your bike but it only works if you lock it up right.

---

### Post by BQAggie2006 on 2009-09-30
Since you will only be doing basic home computing you probably won't have to worry too much about your OS security. General web vulnerabilities (XSS, Java, etc) can still be a problem, but just practice safe browsing and you should be fine. There aren't many Linux viruses in the wild, but if you are still worried about them, you can install a virus scanner such as ClamAV or AVG Free for Linux.
 
ClamAV is located in the software repositories, along with a GUI frontend for it (ClamTK). AVG Free for Linux will have to be downloaded from the website and installed with the .deb installer.
 
Hope this helps.

---

### Post by sydbat on 2009-10-01
> **BQAggie2006 said:**
> Since you will only be doing basic home computing you probably won't have to worry too much about your OS security. General web vulnerabilities (XSS, Java, etc) can still be a problem, but just practice safe browsing and you should be fine. There aren't many Linux viruses in the wild, but if you are still worried about them, you can install a virus scanner such as ClamAV or AVG Free for Linux.
 
ClamAV is located in the software repositories, along with a GUI frontend for it (ClamTK). AVG Free for Linux will have to be downloaded from the website and installed with the .deb installer.
 
Hope this helps.All those only search for Windows malware. They may run on Linux, but have no Linux definitions and are useless resource hogs.

Some may say that running a scanner like these is good for keeping Windows users safe from potential Windows malware forwarding from your Linux box, but that is BS. If the person/people you send things to are too lazy to have some type of security software on their Windows boxes, it is NOT your problem.

Want to make sure your Linux box is secure? Read this sticky that no one else thought about directing you to - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by cguy on 2009-10-03
So I shouldn't use the user created during install for casual computing, right?
Having unlimited sudo is almost as bad as being logged in as root, am I correct?

Should I add another user? What type? Desktop user or Unprivileged?

---

### Post by DrMelon on 2009-10-03
I love this little joke that explains why there are no viruses on Linux :D
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by Boom!!! on 2009-10-03
As far back as I can remember Linux has always been secure from viruses and not just because it's not as mainstream as MS windows but because of how it's built.

---

### Post by gordintoronto on 2009-10-03
> **cguy said:**
> So I shouldn't use the user created during install for casual computing, right?
Having unlimited sudo is almost as bad as being logged in as root, am I correct?

Should I add another user? What type? Desktop user or Unprivileged?

The user created during Ubuntu installation is safe to use.  Only when you type:

sudo (progname)

does it become (briefly) unsafe, and that can be done by any user.

---

### Post by aysiu on 2009-10-03
> **gordintoronto said:**
> The user created during Ubuntu installation is safe to use.  Only when you type:

sudo (progname)

does it become (briefly) unsafe, and that can be done by any user. Actually, no.

A user has to be part of the *admin* group in order to have *sudo* privileges.

And *sudo* requires password authentication. There is a 15-minute timeout period after the first *sudo* in which you can issue other *sudo* commands without re-authenticating, but that timeout doesn't carry across multiple terminal sessions.

You can also change the timeout to 0.

---

### Post by Frak on 2009-10-03
> **aysiu said:**
> A user has to be part of the *admin* group in order to have *sudo* privileges.

I thought it was the *wheel* group, they had to be  a part of.

---

### Post by aysiu on 2009-10-03
> **Frak said:**
> I thought it was the *wheel* group, they had to be  a part of.
Maybe I'm reading the /etc/sudoers file incorrectly, but I believe it's saying it's the *admin* group: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

[b]# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/b]

``` Maybe the *wheel* group is for Mac OS X?

---

### Post by Frak on 2009-10-03
> **aysiu said:**
> Maybe I'm reading the /etc/sudoers file incorrectly, but I believe it's saying it's the *admin* group: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

[b]# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/b]

``` Maybe the *wheel* group is for Mac OS X?
Correction from me: Everybody else still uses the Wheel group, except Ubuntu, which uses the Admin group.

---

### Post by fela on 2009-10-03
> **Frak said:**
> I thought it was the *wheel* group, they had to be  a part of.

It can be any group as long as that group is in the /etc/sudoers file.

It can even be a particular user that's in the /etc/sudoers file. In fact sudo is extremely flexible.

<snip>

---

### Post by fela on 2009-10-03
> **Frak said:**
> Correction from me: Everybody else still uses the Wheel group, except Ubuntu, which uses the Admin group.

I use the sudo group. Makes things less complicated :)

---

