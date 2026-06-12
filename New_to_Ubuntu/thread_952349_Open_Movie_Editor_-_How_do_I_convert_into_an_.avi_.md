---
title: "Open Movie Editor - How do I convert into an .avi file or a generic file for playback"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by jsmkbunch2000 on 2008-10-19
I am putting together a simple slideshow presentation for a cousin that passed away last week in a car crash.  (He was 26)  I am new to Ubuntu and Linux.  I have messed around with Windows Movie Maker, and liked how it simplified the process, added music.  I found how to convert the file to an .avi file in Windows. How can I do this in Ubuntu without spending hours?  

The main reason I switched to Ubuntu today was because I was told that Linux works alot like a Mac OS and the Macs are better equipped for this type of thing.  

Please remember, I know absolutely nothing about Linux and comand codes, so I will need someone to guide me through all the steps.  

I downloaded the open Movie Editor, and it appears very similar to the Windows Movie Maker Program.  Just not sure how to get it from a project to a .avi file.  Also, can you add transition effects between each picture slide?  I am using all .jpg for the video portion.  

Thank you in advance for any help you can give.

---

### Post by Irihapeti on 2008-10-19
As far as I know, OpenMovieEditor doesn't work with .avi files. I've had best results with .dv or .mov files. 

You can convert .mpg files to .dv using ffmpeg.

In a terminal (Applications -> Accessories -> Terminal) enter the command:
```
ffmpeg -i filename.mpg filename.dv 
```

Replace "filename" with the name of your movie file.

There's a GUI front-end for ffmpeg here:
[http://code.google.com/p/winff/](http://code.google.com/p/winff/)

jpg picture files can be placed directly in the timeline, but they have to be "stretched" to the time length you want. (Someone on the OME forums wrote a script to do this, if I remember correctly.) I think the only transition available at present is cross-fade, which you do by overlapping the images.

I don't use OME a great deal, so I'm no expert. You might find some more useful information on the OME forums:

[http://www.openmovieeditor.org/board/](http://www.openmovieeditor.org/board/)

Irihapeti

---

### Post by gorgon on 2008-10-19
you can also use Avidemux if you're not happy with the commandline.

To install, go to Applications -> Add/Remove..
search for Avidemux, tick the box next to it and choose apply changes.

(or was that just being really basic :))

There are other video editing programs as well (Kino, Cinelerra, Pitivi), but Avidemux is very handy for conversion

Good luck with it!

---

### Post by sethvath on 2008-10-19
Avidemux is probably the easiest of them all, the rest looks nothing like windows movie maker for that matter so do not expect everything to perform as easily as it is on windows. 

I do not want to disappoint you but linux and mac video editing is not suited for the casual hobbyist, if you do not know what you're doing its more trouble than its worth. Whoever told you "Linux works alot like a Mac OS" is true to a certain extent BUT there are no commericial linux programs that work exactly like WMM on windows or Final Cut Pro on the mac. 

There are many tools to get the same job done but you have to read up on what does what. FFmpeg, avidemux, kino etc

Happy hunting.

---

### Post by chrisod on 2008-10-19
For what it's worth, Windows Movie Maker is the only reason I still have a dual boot system. I simply have not been able to get any of the native Linux video editing programs to work properly.

---

