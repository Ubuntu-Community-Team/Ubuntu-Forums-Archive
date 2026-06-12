---
title: "Creating a GUI for the commands that i enter to terminal"
date: 2009-09-08
forum: Programming Talk
---

### Post by aytacd on 2009-09-08
Hello everyone, 

I'm using a program called freesurfer. I enter several functions through the terminal and get the results. 
such as when i write "[FONT=Nimbus Roman No9 L][SIZE=3]tksurfer SUBJ1 lh inflated[/SIZE][/FONT]" a brain image open on a window and i'm able to select the region that i want to process by mouse. 

or i will enter "[FONT=DejaVu Sans Mono][SIZE=3]sliceview-sess -s SUBJ1 -a  rtopy -c eccen -map h -slice mos[/SIZE][/FONT]" which some parts could be optional (SUBJ1)

i need a create a gui. I have all the functions and can run these on terminal. Any ideas about how can i convert them to a gui. I don't need a complicated tool only buttons that will call the functions will be enough... 

Hope i could explain what i need. Any thoughts?

---

### Post by stevescripts on 2009-09-08
hmm... I *suspected* when I saw "tksurfer", that there might be a tcl/tk
scripting interface to freesurfer.  (I have never used this, FWIW).

Have you looked at this link? [http://surfer.nmr.mgh.harvard.edu/fswiki/TkSurferGuide/TkSurferScripting/TkSurferIntroToScripting](http://surfer.nmr.mgh.harvard.edu/fswiki/TkSurferGuide/TkSurferScripting/TkSurferIntroToScripting)

For help getting started with tcl/tk - look here:

[http://wiki.tcl.tk/](http://wiki.tcl.tk/)

While I (and others here) can provide a bit of assistance with getting started with tcl/tk - I do not currently have the time/energy to learn TkSurfer.

Hope this helps a bit.

Steve

---

### Post by issih on 2009-09-08
Well, most programming languages will let you throw together a gui that just calls native code.... but doing so will depend on the language you choose

Java will certainly do it, I'd bet python too (although I never have used it)

As an alternative that may suffice and will take you ten seconds, you could just create launchers on the desktop that call those commands (unless the SUBJ1 is being manipulated in some clever way) and use those directly.

Hope that helps

---

### Post by aytacd on 2009-09-09
Thanks for your advices. What about writing each function in a script, save them seperately and call them from MATLAB? 
I don't have much programming experience, and much time so matlab or a tool that i don't need to know Java/C/Phyton etc. will be perfect for me.

---

### Post by MrBoxes on 2009-09-09
I'm extremely interested in any advice on this topic. I've been looking for how to do this for a bit now. I want to make a GUI with buttons that when pressed would execute commands and promp for options maybe. I'm fine with coding and I'd actually prefer tk. Thanks in advanced.

---

### Post by aytacd on 2009-09-14
ok here is what i did: 

i have created scripts (.sh) for each command that i have run in terminal. For that i need to add setenv and source codes to each scripts. 

Than i call each script from matlab with system('source myscript.sh) 
for this i save all commands to work folder of the matlab. 
After that i create my gui with matlab. 

That is the easiest way for me to create a gui. Thanks for your help.

---

### Post by stevescripts on 2009-09-14
MrBoxes -

How about you start a new thread, with some specific examples of some of the commands you are talking about?

Just for clarification - you said you would actually prefer tk ... so are we talking about tk from tcl, Python, Ruby, or ... ?

Steve
(I am quite busy right now - so be patient concerning replies, please)

---

