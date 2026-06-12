---
title: "Hardy using lots of system resources"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Tagri on 2008-05-07
Hi all,

I very recently installed Hardy Heron on my old laptop, as it's not exactly fit to run Vista, and I didn't want to go dig up my old XP key.  I'm normally a Windows-man, and this is my first time using any sort of non-MS made OS, so please bear with me.  I am, however, plenty experienced with computers in general, and absolutely love to learn stuff, so if you can explain why some things are, rather than just say "Go to terminal and type blah", it'd be appreciated.

After getting the system up and running, I quickly noticed that it was very sluggish.  Watching videos (something I did all the time under XP) is virtually impossible, and even simple games like Solitaire and Tetris are extremely choppy.  I google'd around a bit, and found that typing "top" into the terminal would launch a handy little system monitor.  According to it, Xorg is continuously eating up around 50% of my CPU time.  I should mention that this is a Pentium M 1.6GHz processor.  Old, yes, but from my experience under Windows on this machine, I know it is quite a capable little chip.

Additionally, it reports that 87% of my (admittedly meager) 512 megs of RAM are in use.  While this would certainly explain all the harddrive thrashing going on when I try to run any programs, I can't quite figure out where that space is all going.  Adding up all my running processes falls quite a bit short of that figure.

So, to the point, does Ubuntu typically use up such a large amount of memory and CPU time?  Are there simple ways of reducing the load on my poor old laptop?  My needs for it are pretty simple -- the most demanding stuff I ask of it are chatting on VoIP and watching streamed videos.  All the real heavy lifting, I do on my work-laptop or my desktop.

In case it's relevant: the only software I have installed since setting up the system are Mumble, ndiswrapper, and Wine.  I have tested it under both compiz and metacity -- no noticeable difference in performance.  EDIT: Actually there is a difference -- metacity becomes choppier when I move windows around, compiz does not.  Presumably because the latter is hardware accelerated?

TIA for the help! :D

---

### Post by hyper_ch on 2008-05-07
Install htop
```

sudo apt-get install htop

```

run it in the terminal
```

htop

```

make a screenshot and post it here.

---

### Post by Tagri on 2008-05-07
As requested:
[IMG]http://i287.photobucket.com/albums/ll148/Tagri_123/Screenshot-richrich-laptop.png[/IMG]

I picked one with tetris running as well, because I noticed it was also eating way more CPU time than such a simple game ought to.

---

### Post by hyper_ch on 2008-05-07
do you run compiz with adanced desktop effects?

---

### Post by kpkeerthi on 2008-05-07
The RAM usage reported by System Monitor includes **buffers and caches**. [Read on...]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management")

---

### Post by tjwoosta on 2008-05-07
to answer your question,  no ubuntu is not supposed to eat up that much resources!

my sister has ubuntu running on her computer with 256mb ram and all works fine (some minor lag while multitasking but thats expected with only 256mb ram) still better than xp

---

### Post by kesman on 2008-05-07
You should make sure you have extra desktop effects turned off from system -> preferences -> appearance -> visual effects. After this, make sure you have your graphic card drivers installed. Is your's an ATI or Nvidia or intel or what? If it's one of the two first mentioned, check out system -> administration -> hardware drivers and install the proprietary drivers if needed. This should boost things up a bit.

512MB of RAM isn't very much for the normal Ubuntu which uses GNOME as the window manager, I'd suggest you to try Xubuntu out, it uses the lightweight XFCE which still has almost the same amount of graphical configuration tools and usability than GNOME, and it looks much cooler too :P

---

### Post by Tagri on 2008-05-07
Wow, fast responses.  I like :)

In response to hyper_ch: Yes, I use advance desktop effects under compiz, but as I said, this problem is still present under metacity.  I am assuming that when I switch to metacity, all the desktop effects are turned off.  I certainly don't see them, but I suppose that doesn't necessarily mean they aren't eating up resources in the background.

In response to kpkeerthi: I'll assume those are similar to Vista's pre-caching for the time being, and read the article you linked after this post.  If my assumption is correct, then the memory usage shouldn't be a problem, as it should get cleared up as more memory is needed.

In response to kesman: My graphics are run by a Mobility Radeon 9000.  I am reluctant to mess with its drivers.  My first run at using linux was an ill-fated excursion into Gutsy, which did not get along to well with my chipset.  I was quite happy to see that Hardy not only recognized it immediately, but even allowed me to turn on compiz (which runs beautifully, I might add)!  The drivers for this card do not appear in the Hardware Drivers window, which leads me to believe that, like last time, I'd end up digging through *.conf files and downloading package after package tinkering with it.  Now, if the default drivers are the reason why Xorg is so slow, then I don't really have any choice.  But I'd like independent confirmation that this is the issue before I go and do something that I cannot easily undo.

I will look into this Xubuntu thing you mentioned.  Perhaps I'll toss it in VPC on my desktop, give it a tiny bit of ram, and see how it behaves :)

And to all: I have noticed, in writing this on the offending laptop, that it seems to choke on graphically demanding things, but only those that are NOT run through compiz.  For example, scrolling down makes it choke.  Falling tetris blocks make it choke.  Playing videos makes it choke.  But wobbly windows, spinning the desktop-cube, and other such compiz niceties don't cause a performance hit at all.  My guess, therefore, is that the compiz effects are being hardware accelerated, whereas the other graphical effects I've mentioned are being run in software.  Is this possible?  I googled the Xorg process, and it's apparently related to GUIs, which kind of jives with my guess.  Perhaps compiz, handling the desktop, is hardware accelerated, but Xorg, handling individual windows, is running in software and therefore eating my CPU?

In any event, it is late, and sleep takes priority over laptop.  I'll continue to plug away at this tomorrow.

---

### Post by stream303 on 2008-05-07
That htop image is great!  One of my favs...

I see Firefox 3.0b5 - can you run something a little lighter instead such as epiphany-browser?  (in synaptic look specifically for epiphany-browser and not just epiphany)  Currently used the Firefox gecko engine..

Perhaps you could use this until firefox goes stable.  I use Epiphany-browser permanently but that's me. Install and check again with htop.

Be sure to check out the "sticky" in the General Help forum about Hardy bugs which go into some of these things in more detail..

---

### Post by tacutu on 2008-05-07
xorg taking up half of the CPU does not seem normal at all!

---

### Post by kesman on 2008-05-07
For Original Poster:

You should check wheter you are running the open source ATI-drivers, or the closed source FGLRX, which is way more powerful. To do this, run
```
glxinfo | grep vendor
```
in terminal. Glxinfo is quite self-explanatory, but you can get more info on any command with
```

man command

```
man being a short version of manual.
Grep makes a command only print the lines that contain the following word, vendor in this case. This should output the graphic driver used. To install FGLRX, download EnvyNG from synaptic and use it to automatically install the driver for you. You can also find out info about your XORG settings in /etc/X11/xorg.conf which is a configuration file. Edit it with
```

gksudo gedit /etc/X11/xorg.conf

```
be sure to take a backup first.
Its very simple to revert back to your current configuration if you take a backup of the file right now, and in case something goes wrong, just rename your xorg.conf to seomthing else, and your backup of it back to xorg.conf and restart xorg with ctrl+alt+backspace

BTW: I am running ubuntu with mobility radeon x700 with no choppiness with the latest fglrx driver.

---

### Post by hyper_ch on 2008-05-07
I think there are problems with compiz and desktop effects. Hence my question...

With 512 ram it should run ok...

---

### Post by fulgencio on 2008-05-07
I have 512 megas of ram on my laptop too but I think my processor is slightly faster though, before I upgraded to Hardy I was running with lots of Advanced desktop settings, but after the upgrade I had to turn them of because of very similar problems made me uncomfortable. If you don't mind the effects just turn them off; it helped me a lot

---

### Post by Tagri on 2008-05-08
stream303: I've been using Firefox for years on this laptop under Windows, and that was back when it leaked so much memory, you'd have thought the devs were afraid to write to the same bit twice.  However, looking at htop, it does seem to be at least partially to blame for my woes.  I'll check out some lighter browsers like the one you mention as a temporary fix, but I really want to get at the root cause here.

kesman: Thanks!  That's exactly the sort of explanatory post I was hoping for.  I ran glxinfo as you suggested, but I don't see any indication of what driver I'm using.  It says that my server and client glx vendor strings are both SGI, and that the OpenGL vendor string is Tungsten Graphics, Inc.  I'm not really sure how I'm supposed to figure out my drivers from there...  At any rate, I then ran gedit on xorg.conf, and found a bit of weirdness.  The file opened up as completely blank when I ran gedit on it from the command line, but when I used gedit's menu to browse for the file, it opened just fine.  Inside of it, I found a line indicating that my drivers are 'ati', which I imagine means that they aren't the FGLRX ones you mentioned.  I will try installing those and report back on how it goes.

UPDATE: Well, I ran EnvyNG as suggested, and to be honest, the result was the last thing I expected.  It reported that the driver it had selected for me was not supported for my OS, and kicked me back to a command prompt.  Is this unique to Hardy, being so new and all, or does the ATI legacy driver simply not support Ubuntu at all?

To all those mentioning desktop effects -- desktop effects would be disabled when I switch back to metacity, right?  They certainly appear to be.  Metacity performs a bit worse than compiz for me, with Xorg taking up just as much CPU time.  Therefore, I cannot see how this problem could be being caused, or even exacerbated, by desktop effects.  If I am missing something, please point it out.

---

### Post by kesman on 2008-05-08
You could also view the output of XORG log with
```

cat /var/log/Xorg.0.log

```
and grep any lines with EE or WW, they contain error and warning messages. **cat** prints out the contents of a file.

---

### Post by VitalBodies on 2008-06-05
I have a Q6600 quad core with 1GB of ram. Ubuntu seems really fast. 

At least it did. 

Now I am having problems with very slow performance and not sure why. 
I am using Firefox and my desktop effects are off. I am using Gnome and I have the default Mesa drivers loaded for a Ati Radeon X1650 pro card with 512MB. Oddly the system is fine for an hour or so and just gets slower and slower. Firefox (180 mib) taking the most of the memory with Xorg or npviewer.bin (both around 40mib) running second and third. I reboot and I am fine again for a while. I am using only evolution, Firefox and Quanta. I do have the Firestarter firewall on also. Nothing I do maxes any or all of the cpu but the swap gets bigger and my memory hangs at or over 80%.   
I admit it is not uncommon for me to have 20-25 firefox tabs open but shutting them one by one makes the memory go up not down.

---

### Post by hyper_ch on 2008-06-05
vitalbodies:

There's some "bug" that I had a first also with firefox. It used up all the cpu. The solution was to delete the urlclassifier.sqlite file your firefox profile folder.

since then it runs well.

---

### Post by VitalBodies on 2008-06-05
> **hyper_ch said:**
> vitalbodies:

There's some "bug" that I had a first also with firefox. It used up all the cpu. The solution was to delete the urlclassifier.sqlite file your firefox profile folder.

since then it runs well.
What is the urlclassifier.sqlite file? My sense so far was a memory leak in Firefox because doing minor normal things it just takes more and more memory. Even shutting table and clearing all ones privacy data (cache, history etc). 

Also where would the Firefox profile folder be located? 

I have this:
mozilla/firefox/i127m5uy.default/urlclassifier**3**.sqlite

---

### Post by hyper_ch on 2008-06-05
that would be the file... it will not do anything against the memory leak (if that still exists) but if your firefox is using all cpu then deleting that file helps.

---

### Post by VitalBodies on 2008-06-05
> **hyper_ch said:**
> that would be the file... it will not do anything against the memory leak (if that still exists) but if your firefox is using all cpu then deleting that file helps.

My impression is that it is using all the memory. 
Below is a screen shot of the resources. 
[Screenshot.png]("http://www.vitalbodies.com/ws07/images/offsite/Screenshot.png")

---

### Post by hyper_ch on 2008-06-05
Hmmm, that's the flash player that uses so much resources... do you have to open one or the adobe one?

---

### Post by VitalBodies on 2008-06-05
> **hyper_ch said:**
> Hmmm, that's the flash player that uses so much resources... do you have to open one or the adobe one?

I started with Gnash and it did not work for many things so I tried the this:
sudo aptitude install flashplugin-nonfree

If I go to somewhere like the BBC and there is a video on the page I do not have to open a flash player to see the video. Although flash has been intermittent on some sites. 

Currently Installed:  
Macromedia Flash plugin
Gsstreamer Plugin
Vlc Media Player
Movie Player Totem
Gnash swf viewer

---

### Post by VitalBodies on 2008-06-06
Thank you so much for your help. Ultimately un-installed all the flash items and tried out the the shockwave flash 9.0 r 100 pluging that blocks out all the ads unless one wants to see them one by one. The memory problem is mostly gone. 

I had one incident to day with one weird site that much ave laved 40-50 java applets that nearly took out Firefox. My browser window would have been as wide as the room! I shut that down and was ok again. 

The tool you suggest will help for many things...

---

### Post by VitalBodies on 2008-06-07
SOLVED: 
One of my two memory modules had popped part way out of its socket. 
Popping it back in resolved the problem.

---

### Post by hyper_ch on 2008-06-09
notebook or desktop?

---

### Post by adithyu85 on 2008-06-17
Hi all,

So what's the final take on this problem?

My Vostro 1400 is also overburdened with xorg. It is using in the range of 10 to 40% CPU.

Went through the whole thread but didn't find any concrete reason/solution.

Thanks

Cheers

---

### Post by compwiz18 on 2008-06-17
In response to the original poster and the previous post:

I have a Compaq V2000 with an ATI Xpress 200M, which I found very sluggish after install Hardy with the restricted fglrx drivers for my ATI card. I finally learned that this was because the Composite/AIGLX extension for X.org was enabled. Disabling AIGLX made the computer feel much more responsive, even when using Metacity. If you'd like to try this, you need to make a quick edit to /etc/X11/xorg.conf

First, back it up:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d%H%M%S`
```which will make a backup of xorg.conf that will be named something like xorg.conf.20080617061200 (it uses the current time).

Next, edit xorg.conf to disable AIGLX:```
gksudo gedit /etc/X11/xorg.conf
```will open a text editor for you, and then you can add
```
Section "ServerFlags"
        Option "AIGLX" "off"
EndSection
```to the end of that file.

Reboot the computer, and the desktop should seem more responsive. To undo what we just did, just remove the code you pasted at the end, or move the backup of xorg.conf back to xorg.conf.

---

