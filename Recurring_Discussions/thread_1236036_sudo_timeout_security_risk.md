---
title: "sudo timeout: security risk?"
date: 2009-08-09
forum: Recurring Discussions
---

### Post by fela on 2009-08-09
I'm talking about the 15 minute 'remembrance' - or whatever you call it - of course. Don't you think that the fact that after you run, say, sudo vim /etc/fstab to add your NFS share on your NAS to the fstab, you (or anyone else) could then just run any old command and brick your whole system or anything root has read/write access to (including remote filesystems), within a 15 minute window?

Also, I might have forgotten this, but can anyone enlighten me on how to turn this 'feature' off? Sorry to sound like a n00b, I ain't.

---

### Post by kerry_s on 2009-08-09
is it 15 minutes now? the default is 5.

anyways, i change mine to 1 minute.

---

### Post by movieman on 2009-08-09
Anyway, to completely disable it, set the timestamp_timeout in /etc/sudoers to 0 (see 'man sudoers' for more details).

---

### Post by Crunchy the Headcrab on 2009-08-09
> **fela said:**
> I'm talking about the 15 minute 'remembrance' - or whatever you call it - of course. Don't you think that the fact that after you run, say, sudo vim /etc/fstab to add your NFS share on your NAS to the fstab, you (or anyone else) could then just run any old command and brick your whole system or anything root has read/write access to (including remote filesystems), within a 15 minute window?

Also, I might have forgotten this, but can anyone enlighten me on how to turn this 'feature' off? Sorry to sound like a n00b, I ain't.
I think they'd have to have access to your pc...how would they open a session?  Nevertheless I usually set my
> Defaults:username timestamp_timeout=2  It says 2 minutes but I usually do 2 or less.  This means Sudo requires my password again after 2 minutes.  As someone else said you can set it to 0 to make it require the password every time.  The sudoers file is in /etc/sudoers.

---

### Post by MikeTheC on 2009-08-10
Well, as another thread so proudly states, "Physical Access *is* Root Access" so...

---

### Post by starcannon on 2009-08-10
I leave mine at the default 5 minutes; generally what ever I'm doing that requires escalated priv's will take 6 minutes to accomplish anyway ;)

---

### Post by Mornedhel on 2009-08-10
As another poster said, physical access is root access, and there's a thread about that already.

If the goal is just to brick the computer, you don't even need root access. The first two possibilities that come to mind are

1. the old bash one-line fork bomb : you only need a terminal and all of ten seconds to remember the command and type it
2. a hammer

---

### Post by insane_alien on 2009-08-10
unless there is physical access to the computer or the account you used to sudo has been compromised already then there is nothing to worry about.

this is basically asking 'if my security has already been compromised, is that a security risk?'

well the answer to this is surprisingly no. its not a risk anymore, it is a certainty as it has already happened.

---

### Post by fela on 2009-08-10
Ok, thanks for the replies guys. I've changed my limit to 1 minute now (apt-get installs usually take more than 1 minute, most other administritive things are the same).

And the reason I thought it was a security risk, is that I thought the point of sudo was to elevate permissions **temporarily**, so that you know when you can brick your computer but most of the time you can't.

But with the 'remembrance' bug (I call it a bug not a feature :P), surely all that goes out of the window? Depending on the limit you've set (or haven't remembered to reset), you can brick your computer for a whole 5 (or 15, I thought) minutes after you've allowed yourself to brick your computer so-called temporarily! Surely that goes against the point of sudo, and you might aswell just su root instead?

---

### Post by Mornedhel on 2009-08-10
> **fela said:**
> But with the 'remembrance' bug (I call it a bug not a feature :P), surely all that goes out of the window? Depending on the limit you've set (or haven't remembered to reset), you can brick your computer for a whole 5 (or 15, I thought) minutes after you've allowed yourself to brick your computer so-called temporarily! Surely that goes against the point of sudo, and you might aswell just su root instead?

You still have to type sudo, which serves as a reminder that you're doing dangerous things. Again, it is possible to brick a computer with non-administrative commands.

Enabling a root account is not recommended for security reasons (mostly to double the time necessary to brute-force one's way through your login/password).

---

### Post by Tibuda on 2009-08-10
I add **sudo -k** to my .bashrc file, so it clears the sudo timeout everytime I open a terminal. I like the timeout if I'm using the same terminal.


[quote="man sudo"]The -k (kill) option to sudo invalidates the user’s timestamp by setting the time on it to the Epoch.  The next time sudo is run a password will be required.  This option does not require a password and was added to allow a user to revoke sudo permissions from a .logout file.[/quote]

---

### Post by q.dinar on 2010-09-16
topics etc started about this earlier:
[http://ubuntuforums.org/showthread.php?t=1045209](http://ubuntuforums.org/showthread.php?t=1045209)
[http://ubuntuforums.org/showthread.php?t=1051348](http://ubuntuforums.org/showthread.php?t=1051348)
[http://brainstorm.ubuntu.com/idea/17754/](http://brainstorm.ubuntu.com/idea/17754/)
[https://bugs.launchpad.net/ubuntu/+bug/377244](https://bugs.launchpad.net/ubuntu/+bug/377244)

---

### Post by Calmarius on 2011-03-21
I think sudo timeout is a security risk in Ubuntu.

Because if you have an active sudo session then *any* buggy program with remote arbitrary code execution exploit can execute a sudo in your name and can access your system and can install spyware or so. With this timeout we would be in the same boat as Windows users and we would need 3rd party antivirus and antispyware software as they do.

One of the main reasons of moving to the Linux world and abandon Windows is the better security. Now I'm a bit disappointed. Fortunately I was able to set the sudo timeout to 0.

---

### Post by CharlesA on 2011-03-21
Perhaps that is why you shouldn't normally install stuff that isn't in the repositories?

See [here]("https://help.ubuntu.com/community/RootSudo") for pro/cons of using sudo.

---

### Post by cariboo on 2011-03-21
In Natty the sudo timeout is set to zero by default, much to the chagrin of many of the testers.

---

### Post by jwbrase on 2011-03-21
Here's something I don't understand: Sudo keeps track of timeouts per user and terminal. If you log out of a terminal and log back in, the sudo timestamp remains.

So why doesn't sudo compare the timestamp in /var/run/sudo/[username]/ with the "change" timestamp (last time permissions were changed) on the terminal in question? 

Is there some way I don't know of to change the "changed" timestamp to an arbitrary date (thus making such a mechanism useless)? I know that touch -t can be used to change the "accessed" and "modified" timestamps, but it looks like the "changed" timestamp is only changed when permissions change. Is there some method of doing this that I don't know of? If not, checking to see if the timestamp in /var/run/sudo/[username] is older than the "change" timestamp on the terminal and requiring a password if it is would give some extra security.

---

### Post by jwbrase on 2011-03-21
> **Calmarius said:**
> I think sudo timeout is a security risk in Ubuntu.

Because if you have an active sudo session then *any* buggy program with remote arbitrary code execution exploit can execute a sudo in your name and can access your system and can install spyware or so.

No, only a program running on the same terminal. This is most concerning for graphical programs using gksudo, but there is isolation between programs running on different terminals. (Or could a program on one terminal run an arbitrary program (such as sudo) on another terminal owned by the same user?)

---

### Post by tgm4883 on 2011-03-21
> **jwbrase said:**
> No, only a program running on the same terminal. This is most concerning for graphical programs using gksudo, but there is isolation between programs running on different terminals. (Or could a program on one terminal run an arbitrary program (such as sudo) on another terminal owned by the same user?)

I don't believe that is possible.

As for it being a security risk, It's only a risk if you don't trust the code running on your machine.

---

### Post by jwbrase on 2011-03-21
> **jwbrase said:**
> Here's something I don't understand: Sudo keeps track of timeouts per user and terminal. If you log out of a terminal and log back in, the sudo timestamp remains.

So why doesn't sudo compare the timestamp in /var/run/sudo/[username]/ with the "change" timestamp (last time permissions were changed) on the terminal in question? 

Is there some way I don't know of to change the "changed" timestamp to an arbitrary date (thus making such a mechanism useless)? I know that touch -t can be used to change the "accessed" and "modified" timestamps, but it looks like the "changed" timestamp is only changed when permissions change. Is there some method of doing this that I don't know of? If not, checking to see if the timestamp in /var/run/sudo/[username] is older than the "change" timestamp on the terminal and requiring a password if it is would give some extra security.

Actually, looking through the source, sudo seems to have at least the capability of doing this. There are certainly references to the "changed" timestamp on the tty, but the behavior of sudo on my system suggests that this feature is not compiled in.

---

### Post by Calmarius on 2011-03-22
> **jwbrase said:**
> No, only a program running on the same terminal. This is most concerning for graphical programs using gksudo, but there is isolation between programs running on different terminals. (Or could a program on one terminal run an arbitrary program (such as sudo) on another terminal owned by the same user?)

So does this mean after issuing a sudo command in a terminal then accidentally visiting a hacked website that exploits a code execution vulnerability in Firefox *can not* execute a system("sudo rm -rf /") to wipe out my system?

One timeout per terminal?

---

### Post by tgm4883 on 2011-03-22
> **Calmarius said:**
> So does this mean after issuing a sudo command in a terminal then accidentally visiting a hacked website that exploits a code execution vulnerability in Firefox *can not* execute a system("sudo rm -rf /") to wipe out my system?

One timeout per terminal?

It can, but not for the reason you specified. It would need to run it in the same terminal you run sudo in. Basically, if you got code running as your user, it just has to wait until you run something else with sudo, then it has full access to your machine. I've posted basic bash scripts that would do that in another thread. The key though is that a FF vulnerability would need to be exploited or the code would need some other way to run on your system first.

---

### Post by Shining Arcanine on 2011-03-23
> **MikeTheC said:**
> Well, as another thread so proudly states, "Physical Access *is* Root Access" so...

That is not the case if you are running a remote ssh session. You do not automatically get root access by getting access to a terminal.

---

### Post by tgm4883 on 2011-03-23
> **Shining Arcanine said:**
> That is not the case if you are running a remote ssh session. You do not automatically get root access by getting access to a terminal.

A remote ssh session isn't physical access now is it. :)

---

