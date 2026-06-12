---
title: "Installation improvement"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by manofskill on 2008-06-23
Not sure where to post this.

I was just playing around with ubuntu on my parents computer and it is just tearing this thing up.  I have a bit of experience with ubuntu.  Its been my main os for about six months.  Lately ive been running 64 bit hardy and trying to get SLI to work but i consider myself a beginner.  

I was testing downloading and running a few random programs while on the live cd and i went to install a bunch of them.  As i waited for all of the chosen programs to download i thought of an improvement to the system.  You have to wait for all the packages to download and then they start installing.  Why wait?  I dont think it would be that difficult to have the packages start installing immediately and in the background the rest of them would continue downloading.  I dont have anywhere near the knowledge to pull that off but i thought i would through it out there to the people who can.

Tell me what you think?


manofskill

---

### Post by N.N. on 2008-06-23
Perhaps this suggestion is better suited for the [Ubuntu brainstorm]("http://brainstorm.ubuntu.com/").

On topic: I disagree with the idea. Some packages require you to review their licenses before they can be installed. With the current approach you can wait until all packages have been downloaded and then review all possible licensing terms in one go. With the proposed approach, however, I'd imagine you'd be forced to review the licensing terms as the packages get downloaded, thus necessitating constant user presence during the installation. It sounds like the technique used in "Ubuntu Ultimate Edition", which, according to a [review on Linux.com]("http://www.linux.com/feature/137106"), is highly inconvenient: > About 10 minutes into the upgrade I ran into another usability issue. Those who have worked with Debian-based systems know that when doing an upgrade, all the packages are downloaded at one time and then installed in the proper order. That is not how UE's update worked. Instead, it downloaded and installed each application one at a time. Because of this, at several times through the upgrade process I was asked to address different license agreements, installation confirmations, and setup questions. In a regular Debian upgrade, all of these questions are asked at once. The confirmation is done before you start, and the setup questions are asked during the installation at the end. This allows the user to do something else while the upgrade is taking place. Instead, I was forced to stay at the computer and answer questions as they popped up at unpredictable intervals. This, coupled with the new windows popping up over other application I tried to use, made the update a very painful process, which lasted about 45 minutes.

Of course, if you never install packages which require you to review licensing terms, this issue won't present itself. Principally, however, it's a usability issue.

---

### Post by Nepherte on 2008-06-23
Some packages require other packages to be installed. If they both have to be installed and the  package, requiring the other packages, is downloaded first, it still has to wait before the other packages are installed. These are all exceptions on your concept that are fairly complex. I think we are better off with the current install system.

---

