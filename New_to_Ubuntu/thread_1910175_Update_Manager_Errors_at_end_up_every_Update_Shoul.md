---
title: "Update Manager Errors at end up every Update: Should I change a repository?"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by djpurity on 2012-01-16
Hello*, *I have an **Acer Aspire 5251-1805** laptop that I took out the [COLOR=RoyalBlue]**Windows 7**[/COLOR] hard drive and bought a new **Western Digital** hard drive with **500 GB** and installed **Ubuntu 64-bit** after using an **Ubuntu live CD disc**, when it was verion 10.10 I believe. _Stats are the same_: [FONT=System][COLOR=Navy]**AMD (*2.21 GHz*) processor, 3 GB DDR3 memory, DVD-Super Multi DL drive, Acer Nplify 802.11b/g/n, and ATI Mobility Radeon HD 4250 graphics card**[/COLOR][/FONT]. Okay, now that all that's aside, now I get to my problem when I run Update Manager

*Please help *[-o<:
[I][B]
This is a copy of the error that I get after every time I run CHECK on Update Manager:[/B][/I]
> 
W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG D715961D27B81625 Launchpad Experimental Packages PPA, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG 5A9BF3BB4E5E17B5 Launchpad PPA for chromium-daily, W:GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.So, to make it very short: What do I need to do to **fix my list of usable repositories for Update Manager**, ***which** **leads to get this error***, **fixed?** 

Now for some thoughts which cancel the "very short" of it: ;)
I think I understand the part about "[FONT=Fixedsys][SIZE=3][COLOR=RoyalBlue]**cannot be used to add new CD-ROMS**[FONT=Verdana][SIZE=2][COLOR=Black]," but why am I getting that? Is it because I have the CD for Natty checked as a repository?[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][COLOR=Black] Because [/COLOR]unless there is something I could do in order to keep the repositories aware of the fact that **I did *not* ever use a _*CD-ROM*_** when I upgraded my version of software, but rather, **I used a *_mounted_ *iso image* of Ubuntu 64-bit*** to begin with and always have (**Ubuntu 10.10 64-bit** was first, then I have *always* downloaded any iso images of any of the new *"Versions"/"Releases" *that have new names, like Natty, etc, and stored them on my hard drive), so I have always have a copy of a mountable version of the current original iso release (which I download from the Ubuntu website) stored on my hard drive... **but how **would I** _*tell*_ the repositories that instead of a *real* CD-ROM _disc_, that I have an _*iso*_ **which is** on the computer, **and** ready to _mount_ *if needed***? 

I guess the main problem is **that it isn't always mounted**, which is because I want to _**save room**_ on my computer .... Actually -- **IS a mountable iso image the same size as a CD-ROM when it is mounted**? 8-[

And then could things "*[FONT=Lucida Console][SIZE=3][COLOR=DeepSkyBlue]**be added to it**[/COLOR][/SIZE][/FONT]*[FONT=Lucida Console][SIZE=3][COLOR=DeepSkyBlue][FONT=Verdana][SIZE=2][COLOR=Black],[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]" like the **error messages** imply needs to happen? Could I have the **iso** then even **have things _*BE*_ added**? I am just confused here a little bit. 

So any help or advice would be absolutely appreciated! As you can see, I am just a wee little lass and a wee little confused :confused:. So despite me being here about a year or whatever, I still am learning tricks and new things to keep those :twisted: [FONT=Impact][SIZE=4][COLOR=DarkRed]**evil[COLOR=Red] Erro[COLOR=Orange]r [/COLOR]Mes[/COLOR]sages**[/COLOR][/SIZE][/FONT] :evil: at bay=;! [B][I]

Ya'nah'wanna'me'[/I][/B]? :-({|=

---

### Post by spacecheck on 2012-01-16
You might want to read this:

[http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3](http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3)

Might help with the bad signatures. For help removing or commenting  out various sources, you would need to post the contents of your /etc/apt/sources.list

If it works, please use the thread tools to mark this thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Good luck!

PS The weird text formatting you used made your post very uncomfortable to read.

---

