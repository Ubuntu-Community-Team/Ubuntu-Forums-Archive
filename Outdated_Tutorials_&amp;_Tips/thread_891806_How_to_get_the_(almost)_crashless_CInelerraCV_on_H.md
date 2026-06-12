---
title: "How to get the (almost) crashless CInelerraCV on Hardy"
date: 2008-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by artir on 2008-08-16
(From  [http://www.g-raffa.eu/Cinelerra/CinHOWTOs/packages.html]("http://www.g-raffa.eu/Cinelerra/CinHOWTOs/packages.html") )

1.[INDENT]Go to Settings -> Repositories to open the Software Sources window.
Select the Third Party Software tab.
Hit Add.[/INDENT]

In the APT line field copy and paste the following line:
> deb [http://repository.akirad.net](http://repository.akirad.net) akirad-hardy main

Hit Add Source.
Hit the Reload button to update the package information.

 Now you have the akirad repos..

2. There are many cinelerras:
[INDENT]
 [cinelerra]("apt://cinelerra") (x86 and x86_64 without opengl 2.0 video card)
 [cinelerra-generic]("apt://cinelerra-generic") (all x86 and x86_64 with opengl 2.0 video card)
 [cinelerra-k7]("apt://cinelerra-k7") (amd32 without opengl 2.0 video card)
 [cinelerra-k7gl]("apt://cinelerra-k7gl") (amd32 with opengl 2.0 video card)
 [cinelerra-k8]("apt://cinelerra-k8") (amd k8 optimized with opengl 2.0 video card)[/INDENT]

Choose the one that suits your computer. (Usually cinelerra-generic)
Clicking on the above links will download the package right into your PC from the repos :)

Congrats, you have Cinelerra installed!

3. BUT you need to do a little tweak after using it:
[INDENT]
Go to Applications>Sound&Video>Cinelerra
Once it's opened, go to  Settings->Preferences->Playback->Audio Driver.
Choose ESound. Leave the "Server" field in blank and type 7007"(no quotation marks) in the "Port" field.
That will make Cinelerra play nicely with PulseAudio.[/INDENT]


Enjoy!


I tried the cinelerra-common version on a Q6600, NVIDIA 8600GT, Asus P5KSE computer and 0 crashes. I've rendered 2 videos and no problem :)
Now you will have to learn how to use it :mad:

---

### Post by jpeddicord on 2008-08-16
Actually used Cinelerra a few nights ago with this repo. Once you learn it it is once of the most powerful editors out there. :)

---

### Post by mike1212 on 2008-08-18
Should you be able to hear the sound of the video in cinelerra while editing and previewing or compositing?  I can load my videos into cinelerra but there is no sound.  That seems a little odd to me.  I've tried my .mov files (which do give me an error when loaded 

"virtual int FileMOV::read_frame(VFrame*): quicktime_read_frame/quicktime_decode_video failed, result:")

and also some .avi files.  No sound on either.

Thanks for the help.  I've set the audio driver to esound/blank/7007 and read every post I can find on the subject.

---

