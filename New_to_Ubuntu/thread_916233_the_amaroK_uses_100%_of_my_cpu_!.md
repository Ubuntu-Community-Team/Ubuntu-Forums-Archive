---
title: "the amaroK uses 100% of my cpu !"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by medya on 2008-09-10
hey I have a 64 bit 2.8 core 2 intel ,
since yesterday amaroK uses 100% of cpu on my ubuntu hardy 64bit.
(I used top command to see the percent of cpu usage)
I upgraded it and I reinstalled it and still have the problem.
what should I do ?

---

### Post by tuxxy on 2008-09-10
I never been a fan of KDE apps, had similar issues installing even simple apps too.  

If its just Amarok maybe you could try a replacement like rythembox or banshee

Heres a link to the [64-Bit User-Group]("http://ubuntuforums.org/group.php?groupid=258") as I noticed you run 64-bit :)

---

### Post by kostkon on 2008-09-10
> **medya said:**
> hey I have a 64 bit 2.8 core 2 intel ,
since yesterday amaroK uses 100% of cpu on my ubuntu hardy 64bit.
(I used top command to see the percent of cpu usage)
I upgraded it and I reinstalled it and still have the problem.
what should I do ?
Try, for example, to run it from the terminal to check for any error messages.

---

### Post by medya on 2008-09-11
here is the terminal thing :
> morgan@morgan-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x9e10f0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x9e10f0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)


---

### Post by skippuff54 on 2008-09-11
IMHO cut ur losses and find another media program, there are several more stable ones...amarok looks sweet and has some sleek features but i think it hates me

maybe u like amarok for somethin specific? if so chances r good u can find another program (or couple of programs to work together) to accomplish what u want at a lot less cost to ur CPU

but tryin to force the issue with amarok in my experience is usually more trouble than it's worth

that said if u start usin other programs and notice a pattern....there could be a deeper issue that u will want to fix regardless...like video drivers or somethin

---

### Post by skippuff54 on 2008-09-11
as far as ur error message...looks like whatever KAccel (within kdecore) is, it's trying to assign a value to an object called "play_pause". so maybe amarok is tryin to control the kdecore object play_pause, but somethin else has already assigned a value to it.

do u have any other media players open right now? or anything else that has a play/pause button?

or do u have a keyboard with a play/pause button on it, or some other type of input hardware with play/pause?

another option: try goin into your keyboard settings through the system panel, and disable all the options for hot keys.

---

### Post by Elephantman5 on 2008-09-11
Or that crazy famous option of 
Sudo apt-get --purge remove amarok
sudo apt-get install amarok

And then going through synaptic and getting all the xine you can find related to audio.
Amarok is awesome.
KDE is not.

Go GNOME and find yourself without problems.

---

### Post by medya on 2008-09-11
tuxxy : 
yeah I know , I myself have written a 15 pages article, comparing all linux media players , the reason I am using amaroK is testing it .
(I haven't published my article on my blog yet)

Elephantman5 :  I did that too no help .

---

### Post by Elephantman5 on 2008-09-11
> **medya said:**
> tuxxy : 
yeah I know , I myself have written a 15 pages article, comparing all linux media players , the reason I am using amaroK is testing it .
(I haven't published my article on my blog yet)

Elephantman5 :  I did that too no help .

I'm very sorry to hear that.
Out of all the media players I've used this is the most secure.
Besides the Foobar/AIMP dual for Windows, I'd put Amarok right besides them

In spite of its incompatability with rare formats, I'd say it's still right on the money with audio quality and stability. Try BMPx as well. You'll see what I'm talking about.
Issue with your Pulsesound driver probably.

---

### Post by frankstrudel on 2008-11-26
Any fix yet?

---

