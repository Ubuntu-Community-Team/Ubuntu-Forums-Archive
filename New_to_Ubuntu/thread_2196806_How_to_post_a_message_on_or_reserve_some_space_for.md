---
title: "How to post a message on or reserve some space for a guest account"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by aka-John99 on 2013-12-31
I keep thinking about this and half-heartedly try to look up how to do it but have not yet figured it out. I am hoping someone will point me in the correct direction.

The guest account is useful I can let anyone use the computer and not worry they will make changes. I also have other named accounts for other family members to use. It would be great if I could figure out how to
[LIST]
[*]Add a warning message: reminding a user of the guest account, to save everything they wish to keep  to their own memory stick.
That saves me having to say that. Or when I forget to !! #-oI can then point to an on screen message that should have been read. 
[*]Better still. Reserve some small amount of memory, enough for a document, copy of an email or a short video clip. That way some guest may check emails or whatever and save whatever is needed and preserve it at power off until they are able to find removable storage media to use. 
[/LIST]

Maybe this just is not possible, and I will have to simply create yet another account. 
It is probably rather an odd request, but I like the idea of something with no access to my other computer partitions whilst having some very limited storage facility. I doubt I  need fully detailed step by step instructions but if you could point me in the right direction with links to documentation or some similar solution it should help. 

Thanks in advance,
Cheers, John.





I am using Ubuntu 12.04 LTS With a Unity (usually 2d ) environment, on a multi booting Laptop.

---

### Post by Jonathan Precise on 2013-12-31
I think you will have to create a new account (could be another guest account) to be able to even add a start-up program that stays there (they are stored in the account stuff). Sorry. :(

---

### Post by steeldriver on 2013-12-31
Well I've never tried it, but in theory you could modify the guest account setup script (/usr/sbin/guest-account) - it already does a bunch of stuff to *remove* things from the guest's .config/autostart, so I don't see any reason you couldn't *add* stuff there. There also appears to be a 'hook' to an optional /etc/guest-session/prefs.sh script. That's where I'd start.

---

### Post by aka-John99 on 2013-12-31
Thanks both for the quick replies. I will leave this again for a while but at least I now have some solid ideas on where to start, so thanks.
> **Jonathan Precise said:**
> I think you will have to create a new account (could be another guest account) to be able to even add a start-up program that stays there (they are stored in the account stuff). Sorry. :( 
That's what I initially thought I may need to do. In fact I am thinking I may be able to create a custom guest account after all.  

> **steeldriver said:**
> Well I've never tried it, but in theory you could modify the guest account setup script (/usr/sbin/guest-account) - it already does a bunch of stuff to *remove* things from the guest's .config/autostart, so I don't see any reason you couldn't *add* stuff there. There also appears to be a 'hook' to an optional /etc/guest-session/prefs.sh script. That's where I'd start.
That's a great clue. Looking at /usr/sbin/guest-account at least it is only a short script, so I stand a good chance of understanding what it does.

After looking at your posts I also found

[http://askubuntu.com/questions/307087/where-does-the-guest-session-store-its-configuration-files](http://askubuntu.com/questions/307087/where-does-the-guest-session-store-its-configuration-files) > In /tmp/guest-[xxxxxx], where the x's are a string of letters and numbers. That folder contains all the normal home folders for a user.

  The guest account is managed by lightdm through /usr/sbin/guest-account, which is a shell script. After setting up the guest account, the script will run a preferences script if it exists: /etc/guest-session/prefs.sh

  A convenience set of scripts to make this process easier, along with some explanation of how to use them, can be found at [CustomizeGuestSession]("https://help.ubuntu.com/community/CustomizeGuestSession").

  The basic settings you can change are:

  ....Set a Folder for storing files permanently
Show an Info dialog at startup
Set the guest account language and keyboard
  I haven't tested everything, but after using it a few times things seems to work well  .... 

Also
**[Ubuntu 12.04 - Customize the 'Guest Session']("http://ubuntuforums.org/showthread.php?t=2114924")** plus the slightly dated **[Customize guest session]("http://ubuntuforums.org/showthread.php?t=1566078")** tutorial.

I will mark the thread as solved and post back again when I get round to trying to put some of this into practice.

---

