---
title: "Environment Variable Config Files: The Final Word!"
date: 2007-03-29
forum: Programming Talk
---

### Post by travlr on 2007-03-29
I'd like to get **[COLOR="RoyalBlue"]the final word on environment variable configuration file locations[/COLOR]**. I'm then going to post the final word, in a simple and expressive entry on the wiki.

I want to determine all the locations of files that affect an environment. Also how it affects the certain environments. We're talking about the console (login and non-login) the X windowing system, the desktop manager (gdm/kdm/xdm), AND etc....! 

I also want to specify the hierarchy of the file sourcing (ex. ~/.bash_profile sources ~/.bashrc, or whatever)

I'm going to cross post this on the ubuntu and kubuntu forms. I will cross post informative replies to synch the information. 

The following lists the category of questions I have. As information comes in I will edit this post to localize all the information. 

Any additional information not already covered, will also be greatly appeciated.

[COLOR="RoyalBlue"][LIST=1]
[*]**~/.bash_profile**
[*]**~/.bashrc**
[*]**~/.bash_login**
[*]**/etc/environment**
[*]**/etc/bash.bashrc**
[*]**/etc/profile**
[*]**.xsession** 
[*]**ldconfig -V <libpath> ...for LD_LIBRARY_PATH ???**
[*]**sourcing hierarchy **
[*]**desktop manager config files**
[*]**ANY OTHER VARIABLE LOCATION OF IMPORTANCE, NOT MENTIONED**
[/LIST][/COLOR]

Thanks for your help,
-travlr

---

### Post by Mr. C. on 2007-03-29
Interesting, and ambitiuos idea; I think you will find the task far more complicated than you might expect.

Environment variables can be setup by programs at runtime, can live any an file, and are often configured depending upon how some command is invoked.  There are thousands of them!

Best of luck!
MrC

---

### Post by travlr on 2007-03-29
> **Mr. C. said:**
> Interesting, and ambitiuos idea; I think you will find the task far more complicated than you might expect.

Environment variables can be setup by programs at runtime, can live any an file, and are often configured depending upon how some command is invoked.  There are thousands of them!

Best of luck!
MrC

I'm just talking about env vars that I would need to engage for either my own apps, or apps I install without using the  apt/deb-packaging system. 

For instance here's an example I'm trying to figure out right now:

I want to append "~/programming/projects" to the PYTHONPATH env variable, so I put it in /etc/profile /etc/bash.bashrc and /etc/environment. It show's up from a console 'echo $PYTHONPATH' call. But, it's not in python's path when I start up a python interpreter from the desktop menu. So I guessing that either I need to enter it in /etc/X11/Xsessions.options, or the kdm config file, or create a ~.xsession config file so  that /etc/X11/Xsession will call and source it.

I'm just trying to get the "low down" on the various places for putting env vars, and when and for what they are sourced for.

---

### Post by WW on 2007-03-29
You mean PYTHONPATH, right? (No underscore.)

Edit: Looks like you fixed it while I was typing my response. :)

---

### Post by Mr. C. on 2007-03-29
I'm certainly not trying to burst your bubble - it sounds like a noble task.

As you've seen from just one variable, the tree of possibilities becomes large rather quickly.

Consider also, what happens when a remote command is run (say, via ssh); environment variables set in .bash_login or .bash_logout won't be used; but if the remote command starts a shell, those files are sourced.

It really is a difficult problem.  Get more perspective by reviewing the bash man page, searching for INVOCATION.

And then there's ksh, tcsh, sh, csh, mc, etc.

It can make one's head hurt!

Regards,
MrC

---

### Post by WW on 2007-03-29
There is also ~/.gnomerc.  I set umask there so applications started from the gnome menu use the umask that I want them to, rather than the default.  You could try setting PYTHONPATH there.

---

### Post by travlr on 2007-03-29
> **Mr. C. said:**
> I'm certainly not trying to burst your bubble - it sounds like a noble task.

As you've seen from just one variable, the tree of possibilities becomes large rather quickly.

Consider also, what happens when a remote command is run (say, via ssh); environment variables set in .bash_login or .bash_logout won't be used; but if the remote command starts a shell, those files are sourced.

It really is a difficult problem.  Get more perspective by reviewing the bash man page, searching for INVOCATION.

And then there's ksh, tcsh, sh, csh, mc, etc.

It can make one's head hurt!

Regards,
MrC
Yes, it has made my head hurt on more than one occasion. 

Any input (say on ssh remote login situations) you might be able to provide, would help the effort of my collecting as much possible information ;). 

As I said I want to elucidate it on the wiki for all to in the community to easily access.

-travlr

---

### Post by Mr. C. on 2007-03-29
The man pages provides nice lists of these variables, when they are used, and how.  Time to start scanning!

MrC

---

### Post by travlr on 2007-03-29
> **Mr. C. said:**
> The man pages provides nice lists of these variables, when they are used, and how.  Time to start scanning!

MrC
That's a pretty rude reply bud. I've got plenty of experience scanning. I'm trying to do something helpful for the community and you only care to offer an obvious, and unhelpful reply. No offense taken, really, I understand. 

-travlr

---

### Post by Mr. C. on 2007-03-29
I meant no rudeness at all.  It was my way of saying thanks, but no thanks.

As I said, I think you're undertaking a noble task.
MrC

---

### Post by po0f on 2007-03-30
travlr,

[quote=travlr]That's a pretty rude reply bud. I've got plenty of experience scanning. I'm trying to do something helpful for the community and you only care to offer an obvious, and unhelpful reply. No offense taken, really, I understand.[/quote]

How was Mr. C.'s post rude?  You asked a question, and he gave you a valid answer.  Just because he pointed you to a source instead of spoon-feeding you the answer, his reply was rude?

Also, if his reply was so obvious, why did you not consider it yourself?  (most) man pages contain a wealth of information and you are: a) expecting Mr. C. to have this information memorized so he can post it for you, or b) expecting Mr. C. to look up this information so he can post it for you.  In either case, it obviates any need for you to do the work yourself.  Way to help out the community by being lazy.

If you ask me, *you* are the one being rude by expecting someone to do all the legwork for you, so you can cut and paste someone else's work onto some wiki, under your name.

When asking for help next time, remember that it is freely given, meaning you get what you pay for.  Be just a little bit considerate and appreciative, though, and you will be amazed how much help nothing will get you.

---

