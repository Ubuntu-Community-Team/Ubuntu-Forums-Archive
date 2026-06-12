---
title: "Newbie Problem - Error in package installation - help, I think I broke my system"
date: 2005-12-31
forum: Repositories &amp; Backports
---

### Post by faithman2k on 2005-12-31
I tried installing this music package through my Applications menu but something went very wrong.

I have scoured the internet trying to find a fix for it, but I don't understand what the problem is so it makes it harder to fix.

This is the what bash tells me after I try ```
apt-get -f upgrade
```

```
Preconfiguring packages ...
(Reading database ... 84241 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I usually don't try to ask for help, but try to work it out on my own... you learn more about your system that way, but I have spent the last day or two trying to figure this out and am getting nowhere.

hope someone can help

Paul.

PS Hi to the Ubuntu community. I just switched from having used Mepis/Kanotix/Suse 10. Ubuntu has been a revelation. Such a nice OS. It doesn't fight you like others I have tried.

---

### Post by faithman2k on 2006-01-01
The problem was the "program" kpsewhich was not present. It seems I found a dependancy issue.

I installed the package that contains kpsewhich (a perl lib of some description) and then I was able to apt-get install correctly.

For all other newbies out there... it helps to carefully read what your package manager is telling you.

Paul.

---

### Post by dragonfyre13 on 2006-01-06
Oh thank you! I couldn't figure out what was wrong (the command line is gibberish to me) and I was afraid I'd have to do a recovery.

[edit]

CRAP!

I get an error when trying to reconnect. It says "run dpkg --configure -a" and when I do, it seems ok. Runs without errors, etc. Then, when I try to remove lilypond-data, it says that dpkg is already being used.

CRAP!

[2nd edit]

YAY! (again)

I got it to work by reinstalling lilypond-data, and then removing it.

YAY!(again)

---

### Post by faithman2k on 2006-01-09
Good to see posting the info helped someone out. 

My system wouldn't let me re-install lilypond-data. It was stuck so I had to install the package that contained kpsewhich so that it could be reinstalled then removed.

Paul.

---

### Post by dragonfyre13 on 2006-01-25
[QUOTE=faithman2k]Good to see posting the info helped someone out. 

My system wouldn't let me re-install lilypond-data. It was stuck so I had to install the package that contained kpsewhich so that it could be reinstalled then removed.

Paul.[/QUOTE]


I shoudl probably clarify. I installed kpeswitch, then closed synaptic, then reinstalled lilypond-data.

The way that I got syanptic to open without crapping out on me was by running the command it tells you to.

---

### Post by jeremy on 2006-02-08
Does anyone know the name of the package that contains kpeswitch?
Thanks

---

### Post by jeremy on 2006-02-08
I found it, it is tetex-bin.

I follwed the instructions in [http://ubuntuforums.org/showthread.php?t=103013&highlight=lilypond](http://ubuntuforums.org/showthread.php?t=103013&highlight=lilypond)
and sorted it ok.

---

### Post by jezjones on 2006-02-09
> 
Does anyone know the name of the package that contains kpeswitch?


I use synaptic, but also from the command line you could 
```

sudo apt-cache search kpeswitch

```

or to find other packages, if you dont find it at first add a backports repository to your system and update and search again.

---

