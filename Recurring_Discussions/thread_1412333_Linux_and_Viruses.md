---
title: "Linux and Viruses"
date: 2010-02-21
forum: Recurring Discussions
---

### Post by daniell59 on 2010-02-21
Why is Linux more resistant to viruses? Is it because less viruses are written for it being that it has many less users than windows, or is there another reason?

Thanks

---

### Post by MelDJ on 2010-02-21
see: [http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses](http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses)

---

### Post by lisati on 2010-02-21
There are a number of reasons. For example, many examples of [malware]("http://en.wikipedia.org/wiki/Malware") are written specifically for Windows and won't work on *nix.

Have a look here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HPD2 on 2010-02-21
The short lazy answer is beacuse it doesn't have the market share to make it a worth while target. However Linux is also further protected by it's security policy. By default users have limited access and only gain admin access through a seprate account (root) or by privlage escalation (sudo and su.)

---

### Post by J V on 2010-02-21
**Viruses**
If there ever was a serious Linux virus out there, to get it to actually work, you would need to for example:

[LIST]
[*]Log onto your email
[*]Open your email
[*] Download the attachment
[*]Find the attachment
[*]Right-click and go to properties
[*]Go to the permissions tab
[*]Check the box marked execution
[*]Run the application (It can now infect the files in the same directory as it is in)
[*]Input your password (It can now infect files over the entire system)
[/LIST]
  On windows, all you'd have to do is to log onto your email, windows does the rest automatically, this is very insecure and the reason windows users are plagued by virusses.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

---

### Post by JiuJitsu500 on 2010-02-21
well said.... but root is the only user that can modify the entire system.... most users don't even use anything as root, or how to set the password (though a 3 second google will answer it)... "sudo" won't cut it....

just an add on :)

Linux makes is incredibly hard for viruses to even think about your computer, but if it's freakin yoda strong in the force... it has to have root power still to do anything to the core :)

---

### Post by Spiritof76 on 2010-02-21
Another way to think of it is;
Linux was, and still is built by hackers. Therefore security is always has been in mind.  Unix has from the very early days in the 70s was a multi-user operating system. A system multiple users is designed to keep users and processes seperate.

Windows is evolved from DOS a single threaded single user system. Functionality has been added and patched to keep the system up to date. Microsoft programmer's try to patch the system they send out into the world that the hackers will gladly try to find ways to break.  Because the code for linux is public the very folks that find the security breaches are the ones that offer the fixes.

This is why Microsoft programmers are always trying to play catchup. and LINUX seems to always be ontop of the issue.


I also believe that the very act of installing and running a Linux based system makes the users just a little bit more sophisticated.

---

### Post by Paqman on 2010-02-21
Our repositories are also a big reason why malware has a tough time on Linux. If a vulnerability is spotted in an Ubuntu package (for example), a fix  can be uploaded to the repos, and it'll be automatically installed on close to 100% of all systems connected to the internet within 24 hours. OSes that lack centralised repositories (eg: Windows, Mac OS) can't even dream of matching that kind of response.

---

### Post by Elfy on 2010-02-21
moved to recurring discussions

---

