---
title: "Anjuta 2.0.2 'The Breeze' Relased! (alpha)"
date: 2006-06-07
forum: Programming Talk
---

### Post by Kimm on 2006-06-07
> 
2006-05-15 21:28

Behold! After a long wait, Anjuta development team proudly announces the 
release of Anjuta DevStudio 2.0.2 -- 'The Breeze'. This is the next in 
alpha series that brings us more closer towards the final storm. 
 
The release sports shiny new GtkSourceview editor plugin and Valgrind 
plugin for your unlimited hacking pleasure. You also get automake 
project configuration fully working and editor tab drag n drop (ala 
firefox) feature for your visual wowness. 
 
All these, and a pile of bug fixes, await a small contribution from your 
generous beta-testing skills. So, guys, get it before your neighbour has 
the chance to boast about it! 


Yes!

Its finaly here, a new developement release of Anjuta has been released (I was almost convinced the project was dead....)

I'm downloading the sources now! ^^

Update:

Heres a screenshot of 2.0.2 editing a soon-to-be maths program (for calculating one thing only)

[img]http://img75.imageshack.us/img75/5537/screenanjuta4am.png[/img]

Ps.
Anjuta needs later versions of libgdl-1-0 and libgbf-1-0 than found in the Dapper Repos.
I have build packages for these programs tuned for Dapper (i386) along with a checkinstall package of Anjuta, but I have no where to host them.

If you have somewhere I can put them... please PM me or reply to this thread so we can work something out :)

---

### Post by Kimm on 2006-06-08
/bump

is realy nobody interested in this? :o

---

### Post by ydong on 2006-06-08
Hi,

please send it to: [email]ydshare@gmail.com[/email]
password: 0106321

i use this email address as a shared net-disk. and its password will NEVER change.

i used to work with C# for about 2 years. as a newbie of Linux programming, i really don't know what to do. if there's free time, would you please teach & discuss with me a little on C/C++ programming? (personal, through gaim or email)

my email addr: [email]ydong.public@gmail.com[/email]

---

### Post by Kimm on 2006-06-08
ydong, wounderfull!

I mailed the packages to that e-mail so they are now open for download!

Since the Anjuta package was only a checkinstall package I did what I could to get the package to resolve dependencies (following the Anjuta website and looking at the repos).

Note that all packages in the mail must be installed to satisfy the package, and get Anjuta to work properly.

PS.
I also droped you an e-mail ydong :)

---

### Post by mattias01 on 2006-06-08
hm... I can't get it to work. Maybe I'm just stupid.

I can't install libgdl-1-common because it needs libgdl-1, and when I install libgdl-1 I can't install libgdl-1-common because something is broken and must be fixed before I can install or uninstall any more packages.

I tried to compile anjuta 2.0.2 and all the depenecies a few weeks ago, but I didn't get it all to compile. It's good that someone have got it to work.

---

### Post by ydong on 2006-06-09
i can't get to work neither. when i tried to install libgdl, my software index was brokened! i had to use sudo apt-get install -f. when i tried to compile from source code, it prompted the version of libgdl(0.6.0) is under 0.6.1.

someone has succeeded to install anjuta-2.0.2?

---

### Post by Kimm on 2006-06-09
Hm... strange.

Could you elaborate a bit on the problem?
Perhaps I did something wrong while packaging, If I knew the problem I'd try to fix it.

---

### Post by ydong on 2006-06-09
i can't remember the process exactly. i install the lib from your package and it didn't work. then i install it from repository again. then the index of softwares was borken. Then i fixed it... the version of the libgdl from repository is 0.6.0. it's doesn't match the requirements of anjuta-2.0.2. so, i can't compile it neither.

---

### Post by Kimm on 2006-06-10
Fixed!

Somehow I had managed to add a file called ".deb" (as an effect, it was hidden..) inside the data directory of each libgdl package, which caused some trubble.

I have removed the file and repackaged the libraries. They are in a separate e-mail in ydongs shared inbox ("Updated libgdl 0.6.1")

---

### Post by kreso on 2006-06-10
what's wrong? I can't execute a program from within anjuta nor do I have any autocompletion whatsoever available :( :(

---

### Post by kreso on 2006-06-10
I've compiled anjuta from source using the abve gdl and gdf packages.

---

### Post by Kimm on 2006-06-10
As far as I know Anjuta 2 is built from the ground up, and its still in Alpha stages so not all features will be available.

I pretty much just posted these packages here for people to try it out. For production you should probably use the old Anjuta... or find another IDE.

---

### Post by kreso on 2006-06-10
I wasn't thinking of using anjuta as a development platform since it's still beta, but I was hoping to test these autocompletion features which I simply can't run :(

Maby I'm doing something wrong?

---

### Post by Kimm on 2006-06-10
Well... I supose some plugins might not have been compiled... perhaps you should try to recompile?

---

### Post by ydong on 2006-06-11
maybe you don't have libtool installed

---

### Post by vasdee on 2006-06-21
Cheers for the debs, i've bundled them into a zip and put them on freefilehoster for anyone else who wants them. Much easier than using a gmail account - interesting idea none-the-less :)

[http://www.freefilehoster.com/uploads/1150862400Anjuta_2.0.2a.zip]("http://www.freefilehoster.com/uploads/1150862400Anjuta_2.0.2a.zip")
Should be wget'able to boot!

---

### Post by azmrb on 2006-08-16
My question is...

Why is the version in synaptic still 1.2.4 ???

Seems like it should have been updated by now.

---

### Post by TRAyres on 2006-10-19
I get an error message when trying to use doinst.sh :

WARNING: failed to install schema `/schemas/apps/anjuta/valgrind/editor' locale `C': Unable to store a value at key '/schemas/apps/anjuta/valgrind/editor', as t he configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't conta in any databases or wasn't found 2) somehow we mistakenly created two gconfd pro cesses 3) your operating system is misconfigured so NFS file locking doesn't wor k in your home directory or 4) your NFS client machine crashed and didn't proper ly notify the server on reboot that file locks should be dropped. If you have tw o gconfd processes (or had two at the time the second was launched), logging out , killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration t hat prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. Ther e can only be one gconfd per home directory, and it must own a lockfile in ~/.gc onfd and also lockfiles in individual storage locations such as ~/.gconf

](*,)  - I am very new to Linux, so I'm quite lost. Thanks!

---

