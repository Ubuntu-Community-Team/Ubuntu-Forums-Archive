---
title: "Photo Slide show software"
date: 2006-07-08
forum: Programming Talk
---

### Post by greenwom on 2006-07-08
Hey Programmers,
I do not have the know-how to work on this but there's a script in the repos called "dvd-slideshow" it creates nice slideshows of still images with music that you can burn to dvd.  there are two GUI's on sourceforge for it. Both have no development.  The projects are called 

"slcreator" and "photo dvd slideshow"

I can get slcreator running but it stinks
"photo dvd slideshow" looks promising but I (or anyone else I know) can get it running.

a smart GUI for the dvd-slideshow script would be a great marketing tool for Ubuntu.  I want to gain some more programming skills but this seemd a bit to large for a learning project.  
Any takes on building something like this for Ubunutu?  just a thought. [-o<

---

### Post by Max Luebbe on 2006-07-09
I could do this. I'm looking for a project right now anyway.
Even if you don't know much programming, you could help out with the interface design.

What do you find lacking in the other interfaces that needs improvement?

---

### Post by greenwom on 2006-07-09
Well I find that the "slcreator" gui is hard to use and ugly.
the "photo dvd slideshow" screen shots look nice but I haven't been able to run the gui

This is how I think it should go
photos and music should run in a time-line
     * ability to drag and drop photos and have previews native in the gui  
       while browsing
     * some form of icon / graphical display to represent that a transition 
       was selected
     * the preview should also be an interface for the transition effects 
       "select crop and zoom points"
  
Not that I want a clone but proshow is the best I've seen. (brother uses extensivly)  [proshow]("http://www.photodex.com/products/proshowgold/features.html")

I think looking at what's already there and seeing what the proshow folks do can give a good idea of what would make a great Linux alternative.

---

### Post by greenwom on 2006-07-09
in the spirit of community.....

If there's something really basic that you think an newbe could do, let me know.  Or if you need Artwork I can try my hand at it...

edit:  If I was to start helping in this area what would I need to learn C++?  I'm a programming novice (one class in basic like 13 years ago.)  and some machine code stuff with micro processors last year.

---

### Post by Max Luebbe on 2006-07-09
I'm still in the research phase.
Reading up on what the script can do, and figuring out what is feasible.

If you haven't done any serious programming I wouldn't dive into C++, I'd give Python or Java a shot. Both are languages you can accomplish just about anything in, but won't have the headaches of memory allocation in your first serious programming adventures.

Art could help. Once things get going, testing would also be really useful.

Give me 24 hours to mess around with the script.

---

### Post by greenwom on 2006-07-10
Max Luebbe, hey since where both Chicago folk; are you planning on going to the Chicago meeting???

I'm sure the team could take on a testing role.

---

### Post by Max Luebbe on 2006-07-10
I'm going to do my best.
It's a bit of a hike from my neck of the woods, and I need to move my work schedule around.

---

### Post by vwj on 2006-07-26
hey, just came a cross this thread.
So I got a look for dvd-slideshow in the repos and came a cross
qdvdauthor. This seems to be a frontend to dvd authouring tools
(dvd-slideshow is one of them).

So meaby get a look at it.

grts
jan

---

### Post by SpectralDesign on 2006-07-28
I'm not sure where you folks have gotten with this....

I noticed that dvs-slideshow 7.2 was in the standard distribution-ring (universe, maybe?)  Not sure how to tell what branch it is, but anyway:

I noticed first that it doesn't cope with paths that include folders with white-space:

```
cbrown@SpectralDesign:~/digikam/New Album/2006_BISHOP_JARDIN$ dvd-slideshow -n 'test verysimple' -f verysimple.txt
[dvd-slideshow]            dvd-slideshow 0.7.2
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2005 by Scott Dylewski
[dvd-slideshow]
/usr/bin/dvd-slideshow: line 1942: [: /home/cbrown/digikam/New: binary operator expected
ERROR: Output directory not specified.
```

but I changed the folder name, and after a long wait I got to:

```
[dvd-slideshow] 93/94 DSCN2833.JPG 0:0:3.0
[dvd-slideshow] Subtitle= Picture X
[dvd-slideshow]########################################
subtitle=Picture X
[dvd-slideshow] 94/94 DSCN2834.JPG 0:0:3.0
[dvd-slideshow] Subtitle= Picture X
[dvd-slideshow]########################################
subtitle=Picture X
<subpictures>
        <stream>
                <spu start="" end="" transparent="ff0000" image="/home/cbrown/digikam/New_Album/2006_BISHOP_JARDIN/dvd-slideshow_temp_21010/subtitle_1.png">
                </spu>

[dvd-slideshow] waiting for mpeg2enc to finish...

```

From which it went nowhere... for hours... and hours....

Maybe the issue is related to these weird messages when I fire it up:


```
cbrown@SpectralDesign:~/digikam/New_Album/2006_BISHOP_JARDIN$ dvd-slideshow -n 'test verysimple' -f verysimple.txt
[dvd-slideshow]            dvd-slideshow 0.7.2
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2005 by Scott Dylewski
[dvd-slideshow]
[dvd-slideshow] Output directory not specified.
[dvd-slideshow] Using /home/cbrown/digikam/New_Album/2006_BISHOP_JARDIN
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Name index using db3 - No such file or directory (2)
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Name index using db3 - No such file or directory (2)
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Name index using db3 - No such file or directory (2)
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Name index using db3 - No such file or directory (2)
[dvd-slideshow] Parsing input .txt file verysimple.txt
[dvd-slideshow] ########################################
[dvd-slideshow] Found 3 images and 0 audio files.
[dvd-slideshow] Video: NTSC  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] Total video length = 0:0:14.0
[dvd-slideshow] Output filename is test_verysimple
[dvd-slideshow] Temporary directory is /home/cbrown/digikam/New_Album/2006_BISHOP_JARDIN/dvd-slideshow_temp_6394
[dvd-slideshow] Creating black background
[dvd-slideshow]########################################
[dvd-slideshow] Title 0:0:5.0
[dvd-slideshow]         Title1=This is my title sample
[dvd-slideshow]         Title2=
[dvd-slideshow]########################################
[dvd-slideshow] 1/3 DSCN2272.JPG 0:0:3.0
[dvd-slideshow] Subtitle= Picture X
[dvd-slideshow]########################################
subtitle=Picture X
subtitles different i=Picture X i-1=
[dvd-slideshow] 2/3 DSCN2273.JPG 0:0:3.0
[dvd-slideshow] Subtitle= Picture X
[dvd-slideshow]########################################
subtitle=Picture X
[dvd-slideshow] 3/3 DSCN2274.JPG 0:0:3.0
[dvd-slideshow] Subtitle= Picture X
[dvd-slideshow]########################################
subtitle=Picture X
<subpictures>
        <stream>
                <spu start="" end="" transparent="ff0000" image="/home/cbrown/digikam/New_Album/2006_BISHOP_JARDIN/dvd-slideshow_temp_6394/subtitle_1.png">
                </spu>

[dvd-slideshow] waiting for mpeg2enc to finish...

```

I feel a bit stuck... even limiting my slides to three, and it seems to hang at the "waiting for mpeg2enc" part....

Maybe it's my `verysimple.txt` config file, but I tried to follow the directions on the sourceforge site:

```
title:5:This is my title
DSCN2272.JPG:3:Picture X
DSCN2273.JPG:3:Picture X
DSCN2274.JPG:3:Picture X
```

Has anyone got this working at all?  I've got the 3 recommended packages installed along with it, which I did via apt-get

```
sudo apt-get install dvd-slideshow jh ead
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  dvdauthor
The following NEW packages will be installed:
  dvd-slideshow dvdauthor jhead

```

So I'm not sure why it's not working out for me :(

I do notice it creates a folder `dvd-slideshow_temp_7470/` with `video_0.mpg`, but it's just black-screen....

I don't think there's anything else I can add!

^Curtis

---

### Post by SpectralDesign on 2006-07-28
PS - I've tried qdvdauthor too, and it shows the same "waiting for mpeg2enc" line in the progress window, and stalls, saying 4% complete, under the "processing images" progress-bar.

---

### Post by vwj on 2006-07-28
You can't use the version in the repos.
Because this version hangs (like you noticed) with bash >3.1.

> 
0.7.4

dvd-slideshow

Bug fixes:

Changed mpeg2enc process file descriptor from 55 to 3 for compatibility with bash >= 3.1 (fixes hang at wait for mpeg2enc to finish)



So I downloaded the laste version (7.5) as a deb package frome source and instaled it. 
It works fine but I didn't use qdvdauthor. I did not like the interface, so I did everything in plain text and from the cli 
(some gentoo left overs, cli ruels ;-)  ).

Grts
jan

---

### Post by Wiki_Poster on 2006-11-12
Thx vwj, i had the same problem that is solved, now.

---

### Post by 5mattyb5 on 2006-11-19
Hey guys, 

Great idea to make a gui for DVD-slideshow. My hat's off to you.

I can't help in any way but I will ask very politely if you will share it with me when you're done.:D 

I refuse to use windows but I have been having trouble trying to find a user friendly photo slideshow program for linux.

____________________

you can't soar with the Linux geeks,
when you're waddling with the Windows freaks.

---

### Post by ]Nbx*cmD[ on 2007-07-10
Hey!

Here you are a simple yet very useful one:

[http://sourceforge.net/projects/jslideshow/](http://sourceforge.net/projects/jslideshow/)

I'm trying it right now and it looks like it's working... don't expect a professional software, but it does the trick and it's fast and goddamn easy to use ;)

Hope it helped!

---

### Post by irwand on 2010-05-14
I've created yet another gui for dvd-slideshow:

[http://code.google.com/p/dvd-slideshow-editor/](http://code.google.com/p/dvd-slideshow-editor/)

It's aim is to assist you in making the script, so it's pretty basic, but it gets the job done. Feedback is appreciated.

---

### Post by greenwom on 2010-05-14
Awesome, great work, 
I'll have to try it out, I am currently using an apple TV as a kiosk.  
I hope this GUI helps me move my Kiosks over to a linux based platform.

I'll have to spend some time re-investing my research for these linux video apps.  Great work, keep it up.

---

