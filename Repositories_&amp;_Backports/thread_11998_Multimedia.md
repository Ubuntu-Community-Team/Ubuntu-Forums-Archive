---
title: "Multimedia ?"
date: 2005-01-21
forum: Repositories &amp; Backports
---

### Post by ThePainter on 2005-01-21
Hi,
I did a lot of multimedia editing etc. back in XP and Im trying to set up Ubuntu to do similar jobs.
I first tried to rip a cd with Juicer and it wouldnt allow MP3, missing encoder or something.
I went into synaptic and did some searches and found a few Lame entries so I installed them but I still cant get MP3, what do I have to install to get them.

Also I use to take .avi's from my digi camera and edit them with titles etc. in movie maker then in TMPgenc I would convert them into SVCD to play on my DVD player, what equivilant programs are there in the repositary to do these jobs ?

I installed a few found with searches for DVD and MPG but they dont have entries in the app's menu and when I try to run them directly in the /usr/bin as root I just get a list of options, are they just ran from the prompt or are there some gui editors and convertors ?

Thanks if anyone can help.  :confused:

---

### Post by mmuller on 2005-01-21
mp3 is a sticky subject under linux due to various patent issues, an mpeg layer II 'toolame' library is in ubuntu i think and states that it should work with all mp3 players...

for the avi editing there are a couple of options that i have come across in linux - unfortunately none of them are as good yet as their windows counterparts. If you want completely OS software you could try kino to edit and add the titles etc. the maybe avidemux to convert to mpeg2 and then finally varsha to edit the mpeg2 stuff into a dvd format. or you could try cinelerra (not tried it so cannot comment). Another prgram which is not OS and therefore requires purchasing was/is being developed by ([mainconcept](http://www.mainconcept.com) a while ago, not sure whats going on with it though.

Hope this helps a bit...

---

### Post by mpie on 2005-01-21
[QUOTE=mmuller]mp3 is a sticky subject under linux due to various patent issues, an mpeg layer II 'toolame' library is in ubuntu i think and states that it should work with all mp3 players...

for the avi editing there are a couple of options that i have come across in linux - unfortunately none of them are as good yet as their windows counterparts. If you want completely OS software you could try kino to edit and add the titles etc. the maybe avidemux to convert to mpeg2 and then finally varsha to edit the mpeg2 stuff into a dvd format. or you could try cinelerra (not tried it so cannot comment). Another prgram which is not OS and therefore requires purchasing was/is being developed by ([mainconcept](http://www.mainconcept.com) a while ago, not sure whats going on with it though.

Hope this helps a bit...[/QUOTE]
 also avifile and  konverter although this would require kde

---

### Post by Marquis_de_Carabas on 2005-01-21
I think the gstreamer plugins are what you need for mp3. Check out the [Multimedia HowTo](http://www.ubuntuforums.org/showthread.php?t=94)  and the [Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/)  (specifically no. 15 - How to install multimedia codecs) for more info.

Depending on what you're ripping the CDs for, it might be worth giving Ogg a try (Ogg support should be enabled by default). It seems at least as good as mp3 to me, with the only disadvantage being the lack of support in certain hardware players etc. (so if you're looking to transfer to an iPod then you probably do need mp3).

---

### Post by ThePainter on 2005-01-21
Hi,
I tried Kino and it doesnt support the .avi's from my camera, ive got all the avi lib's installed.
Funny thing is Ive got all them installed and all the other codecs I could find including divx and I still had to install Videolan to veiw .avi's, I got the sound in totem but no video.
I tried to install avidemux,transcode and dvdrip and none of them would install because of unavailable dependencies.
I did the add repositries as shown in ubuntuguides.org so it looks like Ill have to keep my XP dual book a bit longer for these few jobs.

My old Mp3's play Ok so Ill just put new stuff to ogg it sounds ok, I dont use a mp3 player its just that I use to use wma till I found mp3 sounded better and I have used it  for a while now, but a cange is as good as a holiday  8)

---

### Post by ThePainter on 2005-01-21
Hi,
Ok Ive solved the mp3 prob. Ive installed "Grip" it does mp3's  =D> 
Still stuck on the video's though  :cry:

---

### Post by cheleb on 2005-01-22
[QUOTE=ThePainter]... I got the sound in totem but no video.[/QUOTE]
For DivX to work in Totem you have to install **gstreamer0.8-ffmpeg** from the resukka unstable resource.
Add this to your /etc/apt/sources.list
```
deb http://debian.ressukka.net/ unstable/
```
Cheers,
cheleb

---

### Post by ThePainter on 2005-01-22
Hi,
Thanks that worked great.

Heres another prob concerning multimedia for you to think over.

I went to this page [Here](http://www.satlug.org/~bigjnsa/vcd-linux.htm) 
And installed the programs advised:
MJPEG Tools
GNU VCD Imager
CDRDAO burner

I then tried to run the advised commands on this page:

For audio use:
 lav2wav stream.avi | mp2enc -V -o sound.mpg

For the video use:
 lav2yuv stream.avi | yuvscaler -O VCD | mpeg2enc -s -r 16 -o video.mpg

I tried them as they are printed, then adding the filename of my .avi and then I cd to the folder holding the file and then as root.
Wont work ?
It just keeps saying no file or folder by this name ?
What am I doing wrong ?

Arent there any video convertors that have a gui ? 
Im new to all this and am having trouble finding the right text commands.
I tried a couple but they cant recognise the .avi

---

### Post by ThePainter on 2005-01-22
Hi,
Totem is now playing avi's,ogg but it only plays some of my mp3's ?
The ones I ripped in XP work but the ones I ripped with grip dont play, totem just freezes
They play OK in Rythmbox although when I import the folder it shows up as unknown instead of the folder name as the rest of my music folders do ?

---

### Post by cotcot on 2005-07-08
Try GooBox to rip CD to MP3. It is described in the ubuntu guide

---

