---
title: "[SOLVED] wine will not install"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by steve joe bob on 2008-07-18
ok. so i'm switching to ubuntu coming from windows for as long as i can remember. so having wine to be able to run some of those apps while i transition would be very useful to me. anyways i currently do not have an internet connection with ubuntu (long story but at the moment my only form internet connection is via my blackberry and my tethering plan. you can see my other thread for more info on that. anyways i am getting nowhere fast with that whole thing.... i'm very new to all this so following some of the more advanced steps is momentarily difficult) well any ways i'm surfing on xp and downloading stuff to a 2nd drive and then rebooting to ubuntu on another partition and trying to install the stuff i downloaded (frustrating to say the least :P) so i was at wine hq and after awhile i found a place where i could just download a .deb file instead of just clicking a link that would install it for me if i was connected on ubuntu. well i downloaded what i thought they said was the stable version which was like 1.0 that didn't work so i downloaded 1.0.0 that didnt' work either. i get an error which i can't remember right now but i'll go look at it and come back and write it down for everybody. so there it is i would really appreciate any help. thanks in advance!

---

### Post by JoshuaRL on 2008-07-18
Yeah, we'll need the error you got.  You may have just installed the wrong type for your processor.  What programs are you wanting to install with Wine?

---

### Post by Viper666 on 2008-07-18
well let's see the error first... and also i think Wine needs a few dependency's to install... write those down and download them, install them before the wine package and everything should work ok after

---

### Post by bodhi.zazen on 2008-07-18
In general that is not how you install software in Linux.

You can either use "Add/Remove programs" or synaptic.

Applications -> Add/Remove -> search for wine

System -> administration -> Synaptic Package manager -> search for wine.

You may need to enable your repositories.

You can also use the command line.

```
sudo apt-get install wine
```

[uhelp]community/SoftwareManagement[/uhelp]

[uhelp]community/SynapticHowto[/uhelp]

[uhelp]community/Repositories/Ubuntu[/uhelp]

---

### Post by steve joe bob on 2008-07-18
ok so i got that error. this is what i see when i double click the .deb file i downloaded. (this is the 1.0.0) it says Error: Dependency is not satisfiable: binfmt-support. i think i attached a screenshot i dunno :P i also thought of something while i was rebooting.... i tried to use the add/remove program to add it in. and again no net connection on ubuntu but i believe it said something about it would use older files since it couldn't connect. again i got some error which i failed to record but i don't have anything better to do then watch my computer reboot till i figure this out so i'll go find that error message! :P

---

### Post by Bigtime_Scrub on 2008-07-18
Im just throwing out ideas here...

You can try and create a repository CD by putting programs you want to install on it. It would take some fudging around in Synaptic to get going but its well worth it in the long run. 

Linux users dont normally download something from windows and than try to use that and install it to a linux system because it doesnt make sense. If you have internet access you can just get what you need from the terminal. 

For people without internet access a repository CD is the way to go.

---

### Post by bodhi.zazen on 2008-07-18
Close that window.

Open a terminal

```
sudo apt-get install -f
```

Then re-install the .deb

Again: this is not the way it is normally done ;)

---

### Post by steve joe bob on 2008-07-18
ok so i've tried a bunch of stuff now (thanx for all the tips!) but it's still not working. i'll try to tell you what i've done and i have some screenshots again. ok so when i use that add/remove option it first gives me an error saying that it cannot connect (i assume anyways) then i close that and it gives me an error that says"wine windows emulator cannot be installed on your computer type (i386)". so i proceeded to try the synaptic thing and did a search for wine and it didn't find anything. then i saw the last post by bodhi.zazen so i figured i'd give that a shot. well i copied that command into the the terminal and it asked for my pass and i gave it. then it did something and gave me the opportunity to type another command so i assume that means it finished what it was doing. so i double clicked the .deb file (the 1.0.0) and got the same errors as before so clicked the other one (1.0) and got the exact same error. and these are the errors i'm seeing:  ok 2 of them won't upload? but here's the other three:

---

### Post by shp on 2008-07-18
Youll have to download the dependency and install it first. Normally these dependencies are downloaded automatically

---

### Post by shp on 2008-07-18
Also did you get the right version for your computer

---

### Post by JoshuaRL on 2008-07-18
You'll need to download the .deb for binfmt-support.  If you need .debs for Ubuntu, [check here.](http://packages.ubuntu.com/)

[This is the package you need.](http://packages.ubuntu.com/hardy/binfmt-support)  Just keep going like this until you don't have any more dependencies to be met.

---

### Post by steve joe bob on 2008-07-19
thnx JoshuaRL! that worked perfectly. took awhile but for my unique situation i didn't have much of a choice

---

### Post by JoshuaRL on 2008-07-19
Yeah, thats the issue sometimes.  You could also try APTonCD if you had another Ubuntu/Debian-based machine connected to the internet somewhere.

---

