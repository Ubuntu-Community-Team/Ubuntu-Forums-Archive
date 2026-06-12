---
title: "VLC not loading"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Hadaka on 2012-05-15
Hi, My VLC player stopped working,all tests to my cd rom/dvd are fine. I thought
perhaps the vlc file might be corrupted. The vlc player would show and also show the
file name of the dvd i had inserted,then it would delete the file name and just sit there
doing nothing. Hence my reason for thinking the vlc player files may be corrupted. I went
to the software center,VLC..it indicated i already had it installed, i then clicked remove.
i then entered in terminal

[CODE][sudo apt-get install vlc
]
it failed
i then entered in terminal

[CODE][sudo apt-get update]
and it uploaded quite a few updates,which surprised me since i always run update
manager when the window pops up.
so once again i entered ....sudo apt-get install vlc......and once again it failed
here is the output from the get-install command

[CODE]$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1.1.11-2build2) but 1.1.12-2~oneiric1 is to be installed
       Recommends: vlc-plugin-notify (= 1.1.11-2build2) but 1.1.12-2~oneiric1 is to be installed
       Recommends: vlc-plugin-pulse (= 1.1.11-2build2) but 1.1.12-2~oneiric1 is to be installed
E: Unable to correct problems, you have held broken packages.
[]
any suggestions?

---

### Post by codingman on 2012-05-15
urk...
please edit your code tags.
can't read it easily.

---

### Post by Face-Ache on 2012-05-15
"sudo apt-get update" won't update your system, just the software sources in the repository.

You could try *installing  *VLC from the Software Center rather than the Terminal. Make sure that the various add-on boxes are ticked, and you should get whatever dependencies it requires in order to run.

---

### Post by Hadaka on 2012-05-15
That was my first choice..the software center load..it failed with the 
same error. 

where EXACTLY between [code][\code] am i suppose to paste ?
as you can see..my attempt to do so didnt work...no wonder my VLC
isnt working,maybe ive gotten to stupid to use a computer :P

---

### Post by Face-Ache on 2012-05-15
Could you please explain a little bit more about what you mean by the Software Center install attempt "failing" with the same error?

The reason i ask, is because you don't see any of that "Reading package lists... Done, Building dependency tree, Reading state information..." stuff when you download via the Software Centre, just a progress bar, which changes to "Remove" once it's been installed.

So yeah, i'm a little bit confused as to what's actually happening :)

Don't worry about the [CODE] stuff; _***I ***_certainly understand what you're entering  ;)

---

### Post by Hadaka on 2012-05-15
vlc: Depends: vlc-nox (= 1.1.11-2build2) but 1.1.12-2~oneiric1 is to be installed
     Depends: libaa1 (>= 1.4p5) but 1.4p5-38build1 is to be installed

this is the error i get with the software center load. under Details: as to why it failed.

pretty much the same error with a manual terminal command. I have a twin laptop
to the one that is not loading vlc...both computers were loaded from the same Ubuntu
11.10 install disc, and its twin runs vlc just like this one used to.i dont know what or why
or how vlc became unusable...its not a hardware failure. and its not a dvd disc failure
as i just tested it on the other laptop.

---

### Post by Face-Ache on 2012-05-15
Do you have Synaptic Package Manager? Both of those dependencies, libaa1 and vlc-nox, appear to be available, so you could try downloading and installing them via Synaptic?

---

### Post by Hadaka on 2012-05-15
Thanks..i took a look at that package..it looks like a nice tool, but for a one time
use..ide prefer to avoid the bloat of yet another app. and update the dependant
files via cli, i dont however know the commands and i want to make sure it overwrites
or replaces the lesser files, im still curious as to why those wernt updated,as i stated
the twin laptop gets updated within a day or so as  this one does...yet vlc runs as its
suppose to on it. somehow i must have done something to cause this and am at a loss
to figure it out. any help on cli commands to add the updated files would be great.
thanks .

---

### Post by Face-Ache on 2012-05-15
Sorry mate, i'm still learning the CLI commands myself, so can't really offer any advice on that unfortunately.

With Synaptic, you could download it via the Software Centre, find the missing dependencies, install/download them, and then 'Remove' Synaptic once finished, with the Software Centre?

It's not like Windows, it *will* actually remove all of the program!  :)

Might be an option if there's no other timely CLI command suggestions from the other helpful folks round here.

---

### Post by Curtis6767 on 2012-05-15
Can you download anything from the Software Center or is it just VLC?

And have you restarted your computer between removing VLC and then installing via the CLI?

---

### Post by Hadaka on 2012-05-15
Im going to mark this SOLVED..only because the thread header says..vlc not loading
and now i have managed to get it to load. but it still brings up the player along with
the dvd file name..and then the file name clears and the player sits there..doing nothing.
so its a different problem as vlc player now does indeed load. To avoid loading the
suggested package.i took a look in software center for the 2 files that seemed to be
causing vlc not to load...and both were there and both had green checks on them which
indicates they were loaded on my machine. one file libaa1.bla bla bla was dated installed
in 2011..so i know i had played a dvd since then. the other file VLC-NOX was dated installed
04-18-2012...hmmmm. so i clicked remove...what the heck...i knew the file name..its broken
anyway..nothing to lose..remove brought up vlc-nox and another file 'forgot the name'
and i chose "blow them all away" and then vlc player loaded..still not working...but loaded.
at no time do i recall ever requesting a load of vlc-nox. I have a very simple machine here
and just do basic script and net browsing,mail,dvd now and then...nothing complex...
anyway..thanks to all who suggested something to help..great bunch...i shall continue on
and find why vlc is not working properly...thanks again all.
p.s.
ok..you'd think after 40 years of messing about with computers..i should be able
to find the "SOLVED" marker....not a clue.

---

### Post by Hadaka on 2012-05-15
found it

---

### Post by Face-Ache on 2012-05-15
"at no time do i recall ever requesting a load of vlc-nox" - it probably loaded as an Add On when you initially installed VLC.

I'm pleased you managed to get it to load, but it's a shame you've not been able to get it working properly. Seems strange.

As you've marked this thread Solved, i'd suggest that you start another thread about this new issue, and then link it to this thread so that anyone helping you out from  here knows the history  :)

---

