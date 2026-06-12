---
title: "looking to see if there are programs in ubuntu software"
date: 2019-04-13
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2019-04-13
i just ripped every windows operating system out of every computer except one, that one will wait until i get the rest up and running.  currently i am looking for two programs that are for linux.  the comodo firewall which i've seen that they have a linux downloadable for but i can't seem to get it to work.   i am also looking for the bfg miner program since it looks like a gpu miner.  i saw that they change the titles on some of the programs and was hoping they did for these two.  i am not 100% familiar with the terminal, since i've only been working this operating system about a week

thanks for the help folks.

---

### Post by Dennis N on 2019-04-13
Comodo: I would be sure that they still support Ubuntu. The download page I found said "Supported Operating Systems: Ubuntu 12.04". A lot has changed since 2012 in Ubuntu's core system.

bfgminer is in the Ubuntu repository. **sudo apt install bfgminer** should work.

---

### Post by cryofreeze666 on 2019-04-13
ok, quick introduction, i am terrible with people because i try to stick to facts.  this one "quirk" of mine makes folks think i'm a "bit disagreeable" or too direct.  i will apologize for that in advance.  i have installed ubuntu in the past and asked questions, then found the turn around for answers to be quite long.  this frustrated me and sent me, with my tail between my legs, back to windows.  i don't intend to do that this time.  i have paid for questions that weren't answered properly, or incorrectly, for the last time. i am hoping, with a little patience, i will get through my orientation period better this time.  the first book i purchased is "linux for dummies" for introductory purposes.  i hope, for now, that that will be enough to help me understand what those with more experience explain.  plus i only use one book at a time, so i can apply what i learn.
   now, to my question.  i have been digging through ubuntu software trying to find two programs, the comodo firewall, and bfgminer.  i found while looking for other programs, that sometimes they had changed the name.  obviously, making those particular programs hard to find.  i was wondering, if there was a listing in the net somewhere of the programs listed by the source and the listings in ubuntu software (.something like green (ubunto software) = comodo firewall (internet download) would be handy for me currently).  i could download comodo from the net.  i just can't seem to do the manual activation properly. bfgminer i just can't find in ubuntu software and i liked it in windows.  it's also listed as one of the top 8 crypto miners for linux, so i thought i'd keep using it. 

thank you for tolerating my long wind.



thanks dennis, first time i've had a reply in such a short time.  but i think my reply trying to word things better might be more what i'm looking for.  i assume i have to enter that in the terminal window so i will try that and see what happens for bfg, was hoping to find it in the ubuntu software for now while learning.



oh hey, by the way is there anything i have to type, like end, after it finishes and throws green lettering at me?

ok i'm back it's not showing up in the programs list or any searches.

---

### Post by Dennis N on 2019-04-13
In the terminal, just type:
```
sudo apt install bfgminer
```
press enter key; enter password when requested (nothing shows when you type password); press enter again. You may need to confirm proceeding (y/n) when requested. install will finish up.

---

### Post by maglin2 on 2019-04-13
I don't use ubuntu software, but last time I did it was far from a comprehensive list of what was available in the repositories.
You would probably do better with a gui package manager such as synaptic for finding packages and applications.
```
sudo apt install synaptic
```

The terminal also works fine though using apt-cache search to give everything matching your search term. The one you want is usually at or close to the top.
```
[FONT=monospace][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ apt-cache search bfg[/COLOR]
bfgminer - multi-threaded multi-pool ASIC, FPGA and GPU bitcoin miner
libalgorithm-lbfgs-perl - Perl interface to an L-BFGS non-linear optimization algorithm
libfgetdata6 - library to read/write dirfile data - Fortran 77 bindings
liblbfgs-dev - L-BFGS solver for unconstrained nonlinear optimization problems
liblbfgs0 - L-BFGS solver for unconstrained nonlinear optimization problems
liblbfgs0-dbg - L-BFGS solver for unconstrained nonlinear optimization problems
liblbfgsb-dev - Limited-memory quasi-Newton bound-constrained optimization (static library)
liblbfgsb-doc - Limited-memory quasi-Newton bound-constrained optimization (documentation)
liblbfgsb-examples - Limited-memory quasi-Newton bound-constrained optimization (examples)
liblbfgsb0 - Limited-memory quasi-Newton bound-constrained optimization
lua-torch-optim - Numeric Optimization Package for Torch Framework
python-bumps - data fitting and Bayesian uncertainty modeling for inverse problems (Python 2)
python-bumps-doc - data fitting and Bayesian uncertainty modeling for inverse problems (docs)
python-pyramid - Pyramid web application framework, a Pylons project
python3-bumps - data fitting and Bayesian uncertainty modeling for inverse problems (Python 3)
python3-pyramid - Pyramid web application framework, a Pylons project
rbdoom3bfg - Doom3 BFG edition game engine
yorick-optimpack - optimization of large scale problems for the Yorick language
game-data-packager - Installer for game data files
[/FONT]
```

Then, as Dennis N says 

```
sudo apt install bfgminer
```

For anything not in the repositories I suspect google may be the best tool, but others may know better. Personally I don't install from outside the repositories.

As Dennis N has said, comodo antivirus for linux hasn't been updated for years. I've not heard of them doing a linux firewall.

Experienced and knowledgeable folks here (I don't include myself) will probably tell you that for a standard desktop install you don't need an av or any firewall other than the preinstalled ufw.
To set it up
```
sudo ufw enable
```

Good luck.

---

### Post by DuckHook on 2019-04-13
> **cryofreeze666 said:**
> …asked questions, then found the turn around for answers to be quite long … i am hoping, with a little patience, i will get through my orientation period better this time…
You won't find a better helper on these forums than Dennis N. I will leave the technical stuff to him. I will chance addressing the more general items:

You will find the community to be a welcoming one. As a technical forum, we like to stick to facts too. However, not all help is available quickly. You will often need to be patient, as this is a forum populated and staffed solely by general users like yourself. Forum members volunteer their time and knowledge and it's up to each of us to decide which questions we want to answer. A respectful attitude and good netiquette will go a long way to earning you forum cred.

> the first book i purchased is "linux for dummies" for introductory purposes.  i hope, for now, that that will be enough to help me understand what those with more experience explain.  plus i only use one book at a time, so i can apply what i learn.

Please read the links in my sig: "Linux is not Windows" & "Resources for Newcomers". These will provide a solid grounding in addition to your "Dummies" book.

> …i could download comodo from the net…

Why Comodo and not GUFW, which is in the repos and is just a GUI front end for UFW, which is already part of a default install?

---

### Post by cryofreeze666 on 2019-04-13
it was the firewall i had experience with, and i saw a link in google.  i didn't read the site thoroughly though, which was obviously my fault.  i went back and read it, after dennis pointed out why i might be having problems.  though i may be willing to completely change my way of doing things, like everyone else, i'd like to maintain some of the old comfort levels which makes a 100% change all at once; difficult at best.  but now i am going to shut up for a while while i go through and try to find bfg since i copied and pasted it into the terminal as dennis typed it but i can't find it.


dennis, i did all that as the program "donloaded" but i can't seem to find a listing.  i am going to try the way maglin2 suggested. hopefully i will find it there since there doesn't appear to be a gui with the instal.

---

### Post by maglin2 on 2019-04-13
If you want to find out if you've actually installed it first type 

apt-cache policy bfgminer 

into a terminal

---

### Post by cryofreeze666 on 2019-04-13
i didn't know that there was a preinstalled firewall in linux.  i made the assumption that there wasn't a firewall, like most of the operationg systems i have used since, oh i don't know, maybe 87- 88.  i have hated windows since xp pro, but couldn't find anything purchasable to replace it that wasn't designed for specific computers (at least that's what i understood about mac's operating system).  so i am researching and learning currently, and i was trying to not completely abandon my comfort zone.  looks like i'm going to have to.

---

### Post by cryofreeze666 on 2019-04-13
it found it with the  apt-cache search bfg  from your first post. now i'm just trying to figure out how to run it, before i run it over to my miners. oh hey, before i forget... wine.  when i was reading through programs the last time i tryed to become a linux devotee, `it seemed to make some windows games playable on linux.  does it still work, and if it does how new can the games be.  or is it something that was just about the popular games?  i am particularly crazy about the original NEED FOR SPEED MOST WANTED, RISE OF NATIONS, and DUNGEON LORDS.  i am kind of curious about steam as well now that i think about it, am i going to have to leave this computer connected to windows?

---

### Post by cryofreeze666 on 2019-04-13
ahhhh "resources for newcomers" sucks printing it out is gonna take forever with the first page being only links.  oh yeah, i hate reading from a monitor it's distracting to me.

---

### Post by cryofreeze666 on 2019-04-13
ok, i've finished reading "linux isn't windows", but already knew most of that information from the other 3 or 4 times i had installed it.  BUT NOW THAT BFG MINER IS INSTALLED AND I'VE FOUND IT, HOW DO I RUN IT.... LOL no guis came with it, it seems.  


could someone please tell me what the terminal command is.

---

### Post by cryofreeze666 on 2019-04-13
ok, went here to try and run the bfgminer :
 [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) 

tryed to do this: **./**[I]filename.extension

but my problem was i had trouble finding the extension part.  i started with ./bfgminer since that is what is showing when i type [/I]
[FONT=monospace][COLOR=#000000]apt-cache search bfg

but i'm having trouble identifying what the extension would be.
[/COLOR][/FONT]

---

### Post by Dennis N on 2019-04-13
If you have Ubuntu, first try the overview screen: press Super Key, then start typing the program name in search box at top. Possible matches appear below it. One click on the program's icon will start it.

When started, it's icon then goes on the launcher/dock at left. You can add it to favorites with right-click > add to favorites. Then it's there permanently.

Extensions: Linux programs don't use an extension like Windows programs. You just use the package name: in this case, bfgminer

---

### Post by maglin2 on 2019-04-13
```
apt-cache search bfg 
```

doesn't actually tell you whether bfgminer is installed. 

```
apt-cache policy bfgminer 
```
would

I know nothing of how it is run though.

```
bfgminer --help
```

is usually a good start for any application.

---

### Post by cryofreeze666 on 2019-04-13
ok, i am guessing an overview is what your calling a window..  so which overview am i opening files, ubuntu software, or show applications?  cause the only place i can actually find it is in synaptic.  i've tried computer/user/shared files/ applications, nothing.  i've typed apt-cache search bfgminer and get the reply of bfgminer - multi-threaded multi- pool ASIC, FPGA and GPU bitcoin miner.  but i still can't run it. i've typed ./bfgminer and gotten nothing as well.


ok well i found the file in computer/user/share/man/man1/bfgminer.1.gz but it seems to be a read me file that i cant run off of.


ok i am trying to find what might be executable gui's in the synaptic/ properties/ installed files section and not getting lucky yet.

ok weird to me, synaptic says there is supposed to be something installed in /user/bin/bfgminer but i can't find anything there. how do i uninstall and reinstall the program so i can start with a fresh copy and start over in my searches for an exe file

alright i just went and searched my computer for bfgminer.exe and it found nothing.  i'm going to have to assume that there is another difference between windows and linux, no executable files.  wow is this becoming tedious.  i had forgotten how frustrating learning new systems can be

thanks to everyone trying to help me so far

wait is there a second program i need to install that equips the gui's?

---

### Post by cryofreeze666 on 2019-04-13
ok, i am guessing an overview is what your calling a window..  so which overview am i opening files, ubuntu software, or show applications?  cause the only place i can actually find it is in synaptic.  i've tried computer/user/shared files/ applications, nothing.  i've typed apt-cache search bfgminer and get the reply of bfgminer - multi-threaded multi- pool ASIC, FPGA and GPU bitcoin miner.  but i still can't run it. i've typed ./bfgminer and gotten nothing as well.

---

### Post by wildmanne39 on 2019-04-13
Please be patient, we are all volunteers here from all over the world in different time zones, if you do not get a reply you can bump your post once every 12 hours with the word bump, please do not create duplicate posts.

Thanks

---

### Post by cryofreeze666 on 2019-04-13
well maglin2 here's a fun fact that i don't seem to be enjoying.  i copied and pasted 
apt-cache policy bfgminer

out of that came this:  

[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

and out of that came a 404 error which has me wondering if i've been chasing a unicorn all day.

---

### Post by cryofreeze666 on 2019-04-13
haven't been trying to create duplicate posts, i've been replying to those helping me and letting them know where i am currently standing.  i've recently been trying to edit my replies to specific people in order to keep them informed of my status..  no sense asking for help if they don't know what their advice has helped me accomplish. editing should slow down my bean count i would think.

---

### Post by yetimon_64 on 2019-04-13
> **cryofreeze666 said:**
> ...[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

and out of that came a 404 error which has me wondering if i've been chasing a unicorn all day.


[ATTACH=CONFIG]283023[/ATTACH]

The link you posted works fine here; definitely not a unicorn.

Regards, yeti.

---

### Post by wildmanne39 on 2019-04-13
> ok, i am guessing an overview is what your calling a window.. so which overview am i opening files, ubuntu software, or show applications? cause the only place i can actually find it is in synaptic. i've tried computer/user/shared files/ applications, nothing. i've typed apt-cache search bfgminer and get the reply of bfgminer - multi-threaded multi- pool ASIC, FPGA and GPU bitcoin miner. but i still can't run it. i've typed ./bfgminer and gotten nothing as well. 
That is what I am referring to, you have it in two posts which is a duplicate and appears that you are getting inpatient waiting for someone to answer that question, no harm done, I just wanted to make you aware.

---

### Post by Geoffrey_Arndt on 2019-04-14
[https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/bfgminer_5.4.2+dfsg-1build2_amd64.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/bfgminer_5.4.2+dfsg-1build2_amd64.deb.html)

I suggest you search in the Package Manager (Synaptic) for the program "gdebi" and install it.   This will allow you to use stand-alone debs (debs which do not come from the official Ubuntu repositories) as referenced in the link above.   It will install the mining program for you.   

IF - repeat IF bfgminer has a built in gui, then using the search window in either Ubuntu Unity DE or Ubuntu Gnome DE will display the program as an icon that you can start by clicking on it.    Or, you can just display all gui programs that are installed by using the apps window (for Gnome DE) or the dash search (for Unity DE).

By the way, much if not all this info can be searched for in youtube that will show how to do those searches, and display the differences in the two main Ubuntu desktop environments.    Did you say what version of Ubuntu you are actually running and what DE?  That would be helpful.

..................................

BTW - - no need to run any other firewall than "GUFW" (graphical uncomplicated fire wall).   If the gui part isn't already installed, just search for gufw in either Synaptic or the Ubuntu "Software" center.   Search youtube for video tutorials on how to set it up and customize it (like port forwarding etc.).

---

### Post by maglin2 on 2019-04-14
> [COLOR=#000000] i copied and pasted [/COLOR]
[COLOR=#000000]apt-cache policy bfgminer[/COLOR]

[COLOR=#000000]out of that came this: [/COLOR]

[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)[COLOR=#000000] bionic/universe amd64 Packages[/COLOR]
[COLOR=#000000]100 /var/lib/dpkg/status[/COLOR]

When I run apt-cache policy for a package that isn't installed I get something like 
```
[FONT=monospace][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ apt-cache policy bfgminer[/COLOR]
bfgminer:
  Installed: (none)
  Candidate: 5.4.2+dfsg-1build2
  Version table:
     5.4.2+dfsg-1build2 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

[/FONT]
```

for something that is installed I get
```
[FONT=monospace][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ apt-cache policy firefox[/COLOR]
firefox:
  Installed: 66.0.2+build1-0ubuntu0.18.04.1
  Candidate: 66.0.2+build1-0ubuntu0.18.04.1
  Version table:
 *** 66.0.2+build1-0ubuntu0.18.04.1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
     59.0.2+build1-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

[/FONT]
```

I can't understand your output, which doesn't seem to say either installed (version) or installed (none).

What does 

```
bfgminer --help
```

yield?

Without trying to install bfgminer myself I doubt I can help you further with this project.

Have you considered a different approach. Why not try another thread asking if anyone on the forum is successfully carrying out cryptocurrency mining with ubuntu, and if so could they please offer guidance as to the approach?
It's possible there is a better way.
Just a thought.
Best of luck.

---

### Post by cryofreeze666 on 2019-04-24
sorry about that wildmanne39, i wasn't aware that i had double tapped thank you, i'll try not to do that in the future.  more than probably i will be getting back on over the weekend, but i think i'm going to look for more books because googling super key after daniel told me about it left me staring at a search result of millions of results.  obviously i didn't get to that, so i'm going to start over again on saturday afternoon (here) and try to figure out what he was talking about.  the first few  links has me understanding that a superkey is a bunch of lesser keys.  more than likely i will be getting on in the evening after i have a better understanding of superkey relation to ubuntu.


oh and daniel if i understand you right about exe. files being windows, i guess i'm looking for a command line(?) to do what an exe. file for windows would do.  

sorry guys, this old dog has a bone and he's chewin madly.  i hate being stupid about things, and i try to learn as quickly as i can.

---

