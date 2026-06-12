---
title: "Why must we compile everything?"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by Nixarter on 2012-07-19
For forever, I thought it was because Linux has no equivalent of an installer (which seemed odd, but ohh, well)... but there are apparently *.DEB files that are just that.  Do many people not know about these?  Why aren't they used a lot?  From what I've read it seems like they've been around for a while.

---

### Post by Bucky Ball on 2012-07-19
Ah, yea. Long time. Use them all the time and they are used a lot. You are saying you've never used a .deb file and have compiled everything ever?

---

### Post by idoitprone on 2012-07-19
> **Nixarter said:**
> For forever, I thought it was because Linux has no equivalent of an installer (which seemed odd, but ohh, well)... but there are apparently *.DEB files that are just that.  Do many people not know about these?  Why aren't they used a lot?  From what I've read it seems like they've been around for a while.

everyone here use deb file alot. Do you ever wonder how the ubuntu package manager works. It uses an apt backend, a tool that manges deb packages.

When you download something from repo; in reality, you are just downloading deb packages

---

### Post by richpri on 2012-07-19
I load all my software with Synaptic, I never compile anything that I didn't write myself.

You can find Synaptic under Applications, System Tools, Administration in Gnome under 12.04.  Or in Search Applications, Installed in Unity.

---

### Post by Nixarter on 2012-07-19
Except synaptic, of course.  Less popular, or developmental versions of programs are released... but almost never in deb format.  To date, despite numerous attempts, I have yet to successfully compile anything.  :(  It is just annoying.

What I mean is, why are there lots of tar.gz files in sourceforge, but I debs are rare if they exist at all.  I understand sourceforge is for source, of course.  But that is how places release code (bandwidth issues, I'm assuming).  So is bandwidth the reason?  No easy way to release it?

---

### Post by thatguruguy on 2012-07-19
> **Nixarter said:**
> For forever, I thought it was because Linux has no equivalent of an installer (which seemed odd, but ohh, well)... 
Have you not noticed the Ubuntu Software Center? It's that thing that looks like a magic shopping bag. It's right there in the launcher. It's been there since 11.04.

> **Nixarter said:**
> but there are apparently *.DEB files that are just that.  

Ever since Debian started, I think.

> **Nixarter said:**
> Do many people not know about these?  
I think everyone who uses Debian or a derivative (which includes Ubuntu), knows about .deb files.

> **Nixarter said:**
> Why aren't they used a lot?  
They are. A whole lot. In fact, even when programs offered on Linux aren't available in the Ubuntu Software Center or through a ppa, you can usually find a .deb file for it.


> **Nixarter said:**
> From what I've read it seems like they've been around for a while.
Yep.

Seriously, is this thread meant as some kind of joke? Are you trolling the forums?

---

### Post by thatguruguy on 2012-07-19
> **Nixarter said:**
> Less popular, or developmental versions of programs are released... but almost never in deb format.

It would be neat if you gave an example or two.

---

### Post by Paqman on 2012-07-19
> **Nixarter said:**
> there are apparently *.DEB files that are just that.  Do many people not know about these?  Why aren't they used a lot?

Almost everything on your system will have been installed through a .deb. They're the default package that APT uses (ie: what it downloads from the repos).

You shouldn't ever need to compile anything on an Ubuntu system unless you're installing some *really* oddball or totally bleeding edge stuff. Compiling from source (particularly if you have to manually resolve dependencies) upsets the balance of dependencies in your package manager and can lead to an unstable system. You also won't automatically get updates, which can leave you at risk from malware. I haven't compiled anything in years. It's a horrible, clunky, messy way to get software.

You should always stick to the official repos, a trusted third party repo or PPA, or a .deb file.

---

### Post by idoitprone on 2012-07-19
> **Nixarter said:**
> Except synaptic, of course.  Less popular, or developmental versions of programs are released... but almost never in deb format.  To date, despite numerous attempts, I have yet to successfully compile anything.  :(  It is just annoying.

What I mean is, why are there lots of tar.gz files in sourceforge, but I debs are rare if they exist at all.  I understand sourceforge is for source, of course.  But that is how places release code (bandwidth issues, I'm assuming).  So is bandwidth the reason?  No easy way to release it?

most people here do not use sourceforge because it already been packaged by the distro

you might want to check this site out for developmental version

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

getting development version is easier. In fact it is easier than windows

---

### Post by NikTh on 2012-07-19
> **thatguruguy said:**
> 

I think everyone who uses Debian or a derivative (which includes Ubuntu), knows about .deb files.

And of course name helps , so you cannot forget .deb packages.
[SIZE=3]**Deb**ian[/SIZE]

:P

---

### Post by Rsjc741 on 2012-07-19
Yeah, I'm kinda confused too...

By compile, do you mean just running scripts? or actually using a compiler to compile C/C++/Java/Python files into usable formats?

If all your doing is downloading tar.gz files and sh-ing the file on a terminal, that's not compiling.. that's script.
also if they're a ~\.run files (e.g. Nvidia's Geforce driver), thats just a script that moves files from inside the .run file.

---

### Post by Nixarter on 2012-07-19
OK, then just ignore my questions completely and just ramble on aimlessly.

---

### Post by papibe on 2012-07-19
Hi Nixarter.

> **Nixarter said:**
> OK, then just ignore my questions completely and just ramble on aimlessly.

Answers in posts #3, #6 and #8 are correct and well explained.

If you consider your question was answered, please mark this thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")).

If not, I would suggest you to read again the posts I mentioned, and ask more questions if you still have any doubts.

Kind Regards.

---

### Post by Vaphell on 2012-07-19
you didn't answer why you need bleeding edge and what programs are missing from convenient sources of software. Do you google for '<program_name> ppa' to see if there is a shiny repo just waiting to be added to the sources list on your system? Since Ubuntu 8.04 i compiled stuff maybe twice and installed .deb maybe twice.

ways of installation, from best to worst (average user's pov)
- official repos
- PPA
- .deb
- source

---

### Post by cariboo on 2012-07-20
THe op has requested this thread be closed. Before doing so, though I'd suggest he install synaptic package manager and check the bottom liner of the window. Running Quantal here, there are 40,703 packages listed, that seems to be quite a few .debs.

---

