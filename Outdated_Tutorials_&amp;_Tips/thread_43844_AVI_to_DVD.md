---
title: "AVI to DVD"
date: 2005-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Wandering Wombat on 2005-06-23
After much searching through these forums and installing packages eg. avidemux and having some dependancy problems from some other posts on this subject I could never convert an AVI to DVD (the one .VOB I did make had audio sync problem) one of the last things I needed to do so I could basically get rid of the windose parasite on my PC. I have searched the forums extensively so plz forgive me if this kind of thing is posted elsewhere.

I have been searching google for weeks to find an easier way to convert an AVI to a DVD and I came across some good tutorials for people who had the problems I have had, I hope these can help others and maybe some discussion will follow from you braniacs out there  :grin:   It is from Gentoo forums/wiki but after installing nearly every DVD and AVI related package in my quest, I only had to Install a couple more things for the script to work. Oh and download the script lol. All the Info needed can be found in the links below, Thanx to the people who did these at gentoo.

[Howto author AVI->DVD with menus using Linux only !](http://forums.gentoo.org/viewtopic.php?t=117709) 

[HOWTO Create a DVD](http://gentoo-wiki.com/HOWTO_Create_a_DVD#Create_a_DVD_directory_structure_.28authoring.29_using_dvdauthor) 

Note: I have only made a basic DVD I havent messed with menus and subtitles etc.

If you use the script for this it will advise you if a package is needed, so check synaptic or search on debian. One package that Ubuntu has but doesnt work with the script is gstreamer0.8-a52dec, had to get a52dec from debian.

Go easy on me this is my first ever post actually trying to contribute lol.

If anyone has any questions I will do my best to answer them, though it just worked for me from following the tutorials good luck!

---

### Post by rachii on 2005-06-23
haha, thanks.   deffinately a good place for me to get started

---

### Post by Sionide on 2005-06-23
Damnit, I guess I need a DVD Writer first huh?

---

### Post by RastaMahata on 2005-06-23
great!
When will linux have good tools to do this? :( We cant depend forever on scripts...

I'll look in the gentoo forums for a DVD -> AVI :P

---

### Post by gil-galad on 2005-06-23
Check out tovid.sf.net, I just used it and it works great!  Better than any windows program I have tried. :)

After that I use dvdstyler to make a dvd with menus.

---

### Post by SFN on 2005-06-23
> If you use the script for this it will advise you if a package is needed, so check synaptic or search on debian. One package that Ubuntu has but doesnt work with the script is gstreamer0.8-a52dec, had to get a52dec from debian. 

I try to avoid installing things from source. I'm sure it's just laziness but I justify it as preferring to be able to handle all installed programs using apt.

This did the trick for me. Download [this](ftp://chuck.ucs.indiana.edu/pub/array2/linux/freshrpms/ayo/redhat/9/i386/RPMS.freshrpms/a52dec-0.7.4-fr3.i386.rpm) RPM of a53dec. Then use alien to turn the RPM into a deb, like so:

```
sudo alien --to-deb a52dec-0.7.4-fr3.i386.rpm
``` 

Then, install the deb, like so:
```
sudo dpkg -i a52dec_0.7.4-1_i386.deb
``` 

any2vob still complained to me because I didn't have ecasound or sndfile-convert. If that's the case for you, you'll need to install ecasound and sndfile-programs.

```
sudo apt-get install ecasound sndfile-programs
```

After doing that, it's working for me.

Thanks for the info, Wombat.

---

### Post by Wandering Wombat on 2005-06-24
Thanx SFN was hoping someone would shed a bit more light on it from an Ubuntu perspective Cheers!

---

### Post by aragorn2909 on 2005-06-24
[QUOTE=gil-galad]Check out tovid.sf.net, I just used it and it works great!  Better than any windows program I have tried. :)

After that I use dvdstyler to make a dvd with menus.[/QUOTE]

Have not tried this yet, but will be sure to at first opportunity.  I have used this method with success:
[http://www.videohelp.com/forum/viewtopic.php?t=242455](http://www.videohelp.com/forum/viewtopic.php?t=242455)

Hope it helps

---

### Post by Wandering Wombat on 2005-06-24
[QUOTE=gil-galad]Check out tovid.sf.net, I just used it and it works great!  Better than any windows program I have tried. :)

After that I use dvdstyler to make a dvd with menus.[/QUOTE]

This looks good will give it a whirl found a videohelp link maybe handy for some

[http://www.videohelp.com/tools?tool=743](http://www.videohelp.com/tools?tool=743)

---

