---
title: "HOWTO: Makes apps load faster"
date: 2005-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-04-09
This is a trick I found on the forum to make apps load faster- prelinking. I'm so happy Hoary is here. For those wanting a speed increase, here are two lines that make your apps load faster:

> sudo apt-get install prelink

sudo prelink -amvR 

The second one might take a while, but its worth it when its done!

Go Ubuntu!

---

### Post by Trickyphillips on 2005-04-09
[QUOTE=poofyhairguy]This is a trick I found on the forum to make apps load faster- prelinking. I'm so happy Hoary is here. For those wanting a speed increase, here are two lines that make your apps load faster:

 

The second one might take a while, but its worth it when its done!

Go Ubuntu![/QUOTE]
 Thanks! Does "prelink -amvR" have to be used every time you install a new application?

---

### Post by bored2k on 2005-04-09
I find this prelink tip more elaborate:
[http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink) (thank Jdong for that) .

---

### Post by poofyhairguy on 2005-04-09
[QUOTE=bored2k]I find this prelink tip more elaborate:
[http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink](http://ubuntuforums.org/showthread.php?t=1971&highlight=prelink) (thank Jdong for that) .[/QUOTE]


Good Call. it needs to be in the guide!

---

### Post by kuleali on 2005-04-13
Nice!

---

### Post by PedroCC on 2005-04-13
Ubuntu developers dont recomend Prelinking...  [-X

---

### Post by jdong on 2005-04-13
[QUOTE=PedroCC]Ubuntu developers dont recomend Prelinking...  [-X[/QUOTE]

Well, for fast-moving releases (i.e. development releases), Prelink isn't a good idea because you can end up with catch-22's:

Library foo changed, so applications depending on foo won't work until they're prelinked. However, the prelinker is prelinked against foo, and so is the shell that you need to spawn the prelinker.....


On released versions, like Hoary/Warty, it's relatively safe to prelink, and it makes Firefox/Openoffice so much faster to start. Plus, the -R flag causes library addresses to be randomized, which minimizes the effectiveness of automated buffer overflow attacks.

---

### Post by jiyuu0 on 2005-04-13
added to ubuntuguide.org
[http://ubuntuguide.org/#loadprogramsfaster](http://ubuntuguide.org/#loadprogramsfaster)

---

### Post by mrbass on 2005-04-13
I highly recommend NOT this doing also.  It's been a disaster in a couple of debian distrubutions.  In all my tests of loading apps it didn't seem to make a difference with the noticable exception of openoffice as they can take it's sweet time to load especially on older CPU's. What went haywire?  Just a few things I can remember is firefox no longer worked, many multimedia plug-ins got borked, etc.

To prelink openoffice only (cuts loading time in half)
[b]sudo apt-get install prelink
sudo /usr/sbin/oooprelink -f[/b]

---

### Post by jdong on 2005-04-13
I can't attest to stuff getting borked. The only time stuff would break with Prelink is if:

A) Bug in prelink (Unlikely -- I have the latest version in Backports, which just has some Debian-integration fixes)

B) Major underlying library changes (Frequent if you live on a development branch)


IMO, just the added security advantage is good enough of a reason to prelink.

---

### Post by Sniffer on 2005-04-14
Thks for the usefull info.

Sniff.

---

### Post by ssam on 2005-04-15
so if a library changes then prelinkede birarys can go unstable. is it possible to unprelink a system before a majour upgrade?

i am running hoary, and very tempted to prelink. when breezy comes along (it seems far away now, but we'll be there in no time) i imagine it will be a good idea to unprelink, upgrade and reprelink.

is this possible?

---

### Post by poofyhairguy on 2005-04-15
[QUOTE=ssam]so if a library changes then prelinkede birarys can go unstable. is it possible to unprelink a system before a majour upgrade?

i am running hoary, and very tempted to prelink. when breezy comes along (it seems far away now, but we'll be there in no time) i imagine it will be a good idea to unprelink, upgrade and reprelink.

is this possible?[/QUOTE]

Yeah. Except just reprelink.

---

### Post by maart on 2005-04-15
Nice speed while opening programs but all programs starts in full screen, so that panels is under new opened window.
How to change that window opens/rezise between these two panels not all over the screen?

---

### Post by poofyhairguy on 2005-04-15
[QUOTE=maart]Nice speed while opening programs but all programs starts in full screen, so that panels is under new opened window.
How to change that window opens/rezise between these two panels not all over the screen?[/QUOTE]


when it does that, put this in the terminal:

killall gnome-panel

---

### Post by AndersAA on 2005-04-15
I've had some problems with prelinking on amd64 (read big problems), quite a while ago though, haven't bothered after that (too much work to fix if it really breaks, as it took a considerable amount of system libs with it :/ )

---

### Post by jdong on 2005-04-15
[QUOTE=AndersAA]I've had some problems with prelinking on amd64 (read big problems), quite a while ago though, haven't bothered after that (too much work to fix if it really breaks, as it took a considerable amount of system libs with it :/ )[/QUOTE]

Oh wow, I'll make a warning of that. I've never tried prelinking on non-i386 archs.

---

### Post by James Brown on 2005-04-16
](*,) After doing that I'm having serious problems with Kde (Kubuntu). When I try to execute kcontrol it hangs the Xserver... Damn... :-x

---

### Post by royg1234 on 2005-06-18
[QUOTE=AndersAA]I've had some problems with prelinking on amd64 (read big problems), quite a while ago though, haven't bothered after that (too much work to fix if it really breaks, as it took a considerable amount of system libs with it :/ )[/QUOTE]

Does this problem exist w/ Athlon64 computers running the i386 install?

---

### Post by AndersAA on 2005-06-18
[QUOTE=royg1234]Does this problem exist w/ Athlon64 computers running the i386 install?[/QUOTE]

nope, there's no way those two can be connected really :)

---

### Post by skoal on 2005-06-18
Sounds great! I'll have to try it.  I definitely found a speed increase with this little gem: "startxfce4 -- -nolisten tcp **+bs**"

* That little "bs" is *no* BS.  That backing store setting really makes my windows snap crackle and pop.

from '/var/log/Xorg.0.log':
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(++) NVIDIA(0): *Backing store enabled*

\\//_

---

### Post by i3dmaster on 2005-06-20
I've had a 128MB old box running RHEL3 which has prelink in there, it runs quite slow when prelinking since the prelink is put into the cron.daily job. its gonna run pretty much every day...

---

### Post by RastaMahata on 2005-06-21
[QUOTE=skoal]Sounds great! I'll have to try it.  I definitely found a speed increase with this little gem: "startxfce4 -- -nolisten tcp **+bs**"

* That little "bs" is *no* BS.  That backing store setting really makes my windows snap crackle and pop.

from '/var/log/Xorg.0.log':
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(++) NVIDIA(0): *Backing store enabled*

\\//_[/QUOTE]
 I get backing store disabled... I dont use xfce or any +bs mod... what's "backing store"? :(

---

### Post by AndersAA on 2005-06-21
[QUOTE=RastaMahata]I get backing store disabled... I dont use xfce or any +bs mod... what's "backing store"? :([/QUOTE]

it stores some data of what's in windows, so it doesn't have to be "reloaded", although the current X implementation isn't complete (can be artifacts and some windows might not redraw properly at all, but that's probably "odd" implementations) and this will use more memory.

---

### Post by RastaMahata on 2005-06-21
[QUOTE=AndersAA]it stores some data of what's in windows, so it doesn't have to be "reloaded", although the current X implementation isn't complete (can be artifacts and some windows might not redraw properly at all, but that's probably "odd" implementations) and this will use more memory.[/QUOTE]
 oh, then I better dont mess with my xorg.conf...

Thanks!

---

### Post by LaSSarD on 2005-08-01
Can I prelink games? If so, is it recommended to prelink Enemy Territory? How do I do it? :)

btw, thanks you for the how-to, I used it with OpenOffice and it opens much faster :)

---

### Post by AndersAA on 2005-08-01
[QUOTE=LaSSarD]Can I prelink games? If so, is it recommended to prelink Enemy Territory? How do I do it? :)

btw, thanks you for the how-to, I used it with OpenOffice and it opens much faster :)[/QUOTE]


well... yeah, but prelinking wont make the application go any faster, it'll just help starting it faster.

---

### Post by LaSSarD on 2005-08-02
[QUOTE=AndersAA]well... yeah, but prelinking wont make the application go any faster, it'll just help starting it faster.[/QUOTE]
 Yeah, that's my problem: starting it. Few days ago it was really quick to start, but now it delays a lot and I'm getting nervous with it :P

Thx for your answer, but how can I do the prelink with the game?

---

### Post by engla on 2006-02-11
Hello there. 

I managed to (almost*) bork my entire system, and I'm pretty sure it was because of prelink. Suddenly, most executables just said "can't execute binary file" or similar. 

Possible cause: I installed new things from source, not from packages and prelink never ran before I restarted my computer (it hung on something, and I force-restarted it). If I remember correctly I installed emacs w/ GTK2 and stuff for my wireless card.

*I didn't have to reinstall. I found an amusing way to recover my system; Synaptic worked in failsafe terminal mode, so first I reinstalled every package needed to login to my default gnome session. I selected basically every package named libg* and reinstalled that.

Then I continued to find all the executables that didn't want to run.
Amusing way to check all binaries: I created a non-privileged user and ran a script that in quick succession started and killed /bin/* /sbin/* /usr/bin/* etc.. then I grepped for "cannot execute" on the resulting error logs and reinstalled each file that was corrupted. auto-apt was very helpful to find out exactly where each binary came from.

I'm a learner, and I /assumed/ that the linux user model would protect me... in theory my unprivileged user couln't do any harm at all to my system, even if I used every binary on the system. In hindsight, it worked perfectly.

---

