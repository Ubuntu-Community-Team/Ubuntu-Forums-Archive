---
title: "Encountered a section with no Package: header"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by fortunsz on 2013-12-25
i tried to *apt-get update* and i got this..


[I]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy-updates_main_i18n_Translation-id
E: The package lists or status file could not be parsed or opened.[/I]

i have tried *sudo rm /var/lib/apt/lists/* -vf*

and the result is the same

Please help me.. :confused:

---

### Post by fantab on 2013-12-25
[COLOR=#000000][FONT=Tahoma]Try these:

sudo -i
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]apt-get clean
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]cd /var/lib/apt
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]mv lists lists.old
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]mkdir -p lists/partial
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]apt-get clean
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]apt-get update
cd
exit[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]


[/FONT][/COLOR]

---

### Post by Castania on 2014-02-04
I know this is a bit old, but it may give some insight, so I'll put it here.  Maybe someone will see it and their frustration level will dissipate.

I work at a US high school.  Since students use computers at school, the server is equipped with a lot of "blocking" capability.

On occasion, for some reason, one of the Ubuntu repository sites gets "blocked."  When it does, I get the message about "no headers", Synaptic won't work, apt-get update fails, etc., etc., etc.  I'm sure you've read this stuff:  type in "sudo rm /vars/ . . . -vf" blah, blah, blah.

I found that I could create a hotspot with my cell phone, connect to the internet with that, and the "header" problem went away.

So . . . I thinking this is could be the issue:  for some reason, and the very moment the system needs it, the repository isn't available, and it throws everything in a mess.  

Perhaps the best thing to do is ignore it for a while . . . then try later.

Ken

---

