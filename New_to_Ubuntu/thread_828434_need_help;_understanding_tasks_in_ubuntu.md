---
title: "need help; understanding tasks in ubuntu"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by hovzio on 2008-06-13
hi,

  I have a few questions concerning tasks in Ubuntu. I started out with investigating (reading about) runlevels with sysVinit and the move towards the upstart event based daemon, init etc. In general just trying get a grasp on unix based os's, how they work and further my knowledge concerning computers. I'm new to linux so I apologize in advance if any questions are "far off", please bare with me.

  Is there a website that list standard tasks running under ubuntu with detailed descriptions? (example; /usr/bin/X, scsi_eh_1 ..) Sure I know what X is but why and what are all these options appending?  I have googled quite a few of them (tasks) and sometimes find some answers but more often than not I end up getting complex forum threads showing the output of ps -aux or so. Would be really cool to have it all in one place for reference. Wouldn't mind buying a book either so any suggestions are welcome. :)

  I just installed htop and the output *seems different than that of top. Im not talking about the side scrolling etc but the content. I assume that in all actuality they are the same but I guess I have a lot to learn. Any ideas as to how to go about figuring this out? 

  Any suggestions as to "where to start off" concerning the subject are more than appreciated. I'm starting to feel comfortable with bash and understand the the very basics of bash scripting so I'd like to start getting a grasp on Linux and how it works. I figured learning about tasks and daemons would be a good place to start.

---

### Post by HalPomeranz on 2008-06-13
This is what the system manual pages are for.  Anytime you see a process in the ps output, you can do "man <processname>" (e.g., "man X", "man dbus-daemon", etc) to pull up the manual page about that process.  The manual page should describe the various command-line options, configuration files, etc.  At the end of each manual page are a list of other programs that are somehow related to the program you're reading about.

That's the "perfect world" scenario, anyway.  The truth is that some of the Linux manual pages are pretty scanty.  They're getting better slowly, but I'm sometimes frustrated by the lack of information in some manual pages.

Other sources of information include the GNU "info" command for detailed information about various software packages from the FSF.  For example, try "info emacs" (assuming you have emacs installed).  The start-up scripts in /etc/init.d may also have comments in them that provide information about the services they start.

---

### Post by hovzio on 2008-06-14
The info command has been of little help to me although I see the potential. Theres abount 5 installed programs that have info pages on my pc. There is an info page for wget and some others but like I said it amounts to about 5 to 7 programs. The rest of the time I get redirected to the man pages. How can I get info to work? Where can get more information on info.  The man pages.. sure I look at these (spend lots of time with them) but thats not I'm looking for. I like man pages and use them frequently but I'm looking for somthing else.

---

### Post by HalPomeranz on 2008-06-14
Well the info command is part of the GNU texinfo package.  So I guess the place to start looking is the package documentation.

I'm repeating myself a bit here, but I just want to be specific about the places that I go to look for documentation about specific processes:

-- man pages
-- boot scripts in /etc/init.d
-- config files under /etc and /etc/default
-- files under /usr/share/doc/*
-- Google/various Internet sites
-- GNU info pages

It sounds like you're already using most or all of the above.  Beyond that, you may want to pick up a good general Sys Admin book like Limoncelli/Hogan/Chalup's "The Practice of System and Network Administration" or Nemeth et al's "Linux Administration Handbook".

---

### Post by hovzio on 2008-06-14
> **HalPomeranz said:**
> Well the info command is part of the GNU texinfo package.  So I guess the place to start looking is the package documentation.

I'm repeating myself a bit here, but I just want to be specific about the places that I go to look for documentation about specific processes:

-- man pages
-- boot scripts in /etc/init.d
-- config files under /etc and /etc/default
-- files under /usr/share/doc/*
-- Google/various Internet sites
-- GNU info pages

It sounds like you're already using most or all of the above.  Beyond that, you may want to pick up a good general Sys Admin book like Limoncelli/Hogan/Chalup's "The Practice of System and Network Administration" or Nemeth et al's "Linux Administration Handbook".


Thanks, thats kinda what I'm looking for.Being specific is what I'm looking for :)  I found these very usefull:

-- boot scripts in /etc/init.d
-- config files under /etc and /etc/default

So I looked up System administration and those seem to be "key words" to a lot of the questions I ask myself (and the forums) latley. Thanks again. I will for sure look into a good book on sys. administration.

---

