---
title: "Mov/Divx/Xvid/Wmv/Etc to DVD (PAL or NTSC)"
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by netyire on 2006-12-17
[FONT=Tahoma][SIZE=3]_A Guide To: Making DVDs from Various Formats (Get the script here: [http://www.ubuntuforums.org/showthread.php?p=1900382](http://www.ubuntuforums.org/showthread.php?p=1900382))_[/SIZE][/FONT]
[SIZE=2]**Tools Requried:**[/SIZE]
[LIST=1]
[*]mencoder
[*]ffmpeg
[*]dvdauthor
[*]genisoimage or mkisofs (pre 8.10 users)
[/LIST]

[FONT=Tahoma][SIZE=2]Please note, following this guide will produce a disc without menus.[/SIZE][/FONT]

[SIZE=2][FONT=Tahoma]**Step 1: Convert Media to .AVI (Go to the next step, if the file you wish to convert is already in the .avi format)**[/FONT][/SIZE]
[FONT=Tahoma][SIZE=2]Okay, the first thing you need to do is to transcode your media into .avi format so that it is accepted by ffmpeg. (I tried using ffmpeg directly to convert a .mov to .mpg. It did not work :-k ) To do so type the following in the terminal:  [/SIZE][/FONT]

**mencoder <inputfile> -ovc xvid -xvidencopts pass=1 -oac mp3lame -lameopts vbr=3 -o /dev/null**

After which type:

**mencoder <inputfile> -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o <outputfile>**

Okay, now we have a xvid .avi file to work with! :D 

[SIZE=3]**Step Two: Convert the .avi file to a .mpg file**[/SIZE]

Right, now that you have a file that ffmpeg will accept, enter the following to transcode the file into a compliant .mpg file.

**ffmpeg -i <outputfile from the above> -target pal-dvd final.mpg**

If you DVD player uses ntsc then replace the 'pal' to 'ntsc'. Or if you want you can type:

**ffmpeg -i <outputfile from above> -target pal-dvd -aspect 16:9 final.mpg**

This will make the aspect ratio 16:9, see if it works for you. 

Now you have your final .mpg file ready. 

**[SIZE=3]Step 3: Create the DVD file structure[/SIZE]**

Enter:
[B]
dvdauthor -o DVD/ -t final.mpg[/B]

and then:
[B]
dvdauthor -o DVD/ -T[/B]

Simple and fast, you now have the your DVD structure! :cool: 

**[SIZE=3]Step 4: Create The .ISO File[/SIZE]**

Type:

**mkisofs -dvd-video -v -o DVD.iso DVD**

And you finally have the .iso file ready for burning! :KS

Merry Christmas!

---

### Post by netyire on 2006-12-18
[SIZE=2]If you find this useful, please drop a comment! I wrote a python program which asks you for the file you want to convert and a few other things like whether you want PAL or NTSC and whether you want the aspect 16:9 or 4:3 and then creates the DVD.iso for you, ready to burn! :D [/SIZE] Please note that you need mencoder ffmpeg dvdauthor and mkisofs (pre 8.10 users, 8.10 includes this in the genisoimage package). You also need python to run the program. To use it just cd to the directory you extracted the file I attached in this post to and type 

```
python program.py
```Oh, and if you do not have any of the required programs installed just type this into the terminal if you are running pre 8.10:

```
sudo apt-get install mkisofs ffmpeg dvdauthor mencoder python
``` or if you are running 8.10 and above: ```
sudo apt-get install genisoimage ffmpeg dvdauthor mencoder python
```  Just make sure you enable their repositories. Oh and please post a comment.

8/12/2008: Updated required packages, thanks smoka! 18/12/2006: Added support for subtitles as requested by Rejser

---

### Post by rejser on 2006-12-18
Great guide, how would I add subtitles to the dvd, from for example an srt file

---

### Post by netyire on 2006-12-18
**[SIZE="2"]Howto: Add Subtitles To Your DVD[/SIZE]**

[SIZE="2"]Ok, this actually just requires you to use the -sub <mysubtitle.srt> switch on pass 2 of encoding of your movie to avi. For example:

```
mencoder <inputfile> -sub <subtitles.srt> -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o <outputfile>
```

In order to change the size add -subfont-text-scale <n> to the output, where n is a number. The smaller the number, the smaller the font. For example:

```
mencoder <inputfile> -sub <subtitles.srt> -subfont-text-scale 3 -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o <outputfile>
```

Cheers! ;) 

Ok, I updated the script to give support for subtitles![/size]

---

### Post by 454redhawk on 2006-12-19
> **netyire said:**
> [FONT="Tahoma"][SIZE="3"][U]A Guide To: 

**[SIZE="3"]Step 4: Create The .ISO File[/SIZE]**

Type:

**mkisofs -dvd-video -v -o DVD.iso DVD**

And you finally have the .iso file ready for burning! :KS

Merry Christmas!

Where is this typed (what dir)?
Where do you input the source into that command?

What is the max size of the first input file to be converted?
What determines the final output size of the DVD and is there any control of it?
How do I know if the file is too big to fit on DVD?

---

### Post by netyire on 2006-12-20
OK, firstly thanks for asking questions!

> Where is this typed (what dir)?
It is typed in the terminal, in the same directory as where you typed the commands shown in step three. (Creating the DVD file structure)

> Where do you input the source into that command?
Since the source is not clearly specified, I shall assume that you mean the directory created in step three. That is specified in the synax in this format:
```
 mkisofs -dvd-video -o <output iso file> <source directory>
```
And in this case the source directory is DVD, supposing you followed the guide exactly.

> What is the max size of the first input file to be converted?
This depends on the capacity of your DVD, please specify if it is a DVD 5 or DVD 9.

> What determines the output size of the DVD and is there any control of it
Simply put, the final output size of the DVD depends on the what file you want on the DVD. There is control over it (you can do what you want with the files...).

> How do I know if the file is too big to fit on DVD?
Hmm... perhaps it is possible to do this by multiplying the amount of seconds of playback time your media (file) has by 1000 (the bitrate of the mencoder conversion, but this may not be exact), which would give you the possible (video) file size - then add this amount to the length of audio by the bitrate you are using. Once you have the size for the final one, perhaps you can multiply it according to what ffmpeg's bitrate is for the specifications you use. Maybe this will give you what you want. But if you do find a better, more accurate method, please share it :)

---

### Post by xyz on 2006-12-20
Fantastic! Thank you...it works, it's simple; it's understandable! Thx!

---

### Post by 454redhawk on 2006-12-21
THANKS!




> **netyire said:**
> OK, firstly thanks for asking questions!


It is typed in the terminal, in the same directory as where you typed the commands shown in step three. (Creating the DVD file structure)


Since the source is not clearly specified, I shall assume that you mean the directory created in step three. That is specified in the synax in this format:
```
 mkisofs -dvd-video -o <output iso file> <source directory>
```
And in this case the source directory is DVD, supposing you followed the guide exactly.


This depends on the capacity of your DVD, please specify if it is a DVD 5 or DVD 9.


Simply put, the final output size of the DVD depends on the what file you want on the DVD. There is control over it (you can do what you want with the files...).


Hmm... perhaps it is possible to do this by multiplying the amount of seconds of playback time your media (file) has by 1000 (the bitrate of the mencoder conversion, but this may not be exact), which would give you the possible (video) file size - then add this amount to the length of audio by the bitrate you are using. Once you have the size for the final one, perhaps you can multiply it according to what ffmpeg's bitrate is for the specifications you use. Maybe this will give you what you want. But if you do find a better, more accurate method, please share it :)

---

### Post by Crube on 2006-12-22
How big is the file supposed to be. I'm trying to converts a 700mb video into an mpeg. Now ot's 1,6gigs big and 20 minutes long O.o The original file is 1.20 hours

---

### Post by gspinnada uhu on 2006-12-23
thanks for the guide.
i just have one problem:
step three when i am trying to create the dvd file structure i get this error message:
"WARN: unknown mpeg2 aspect ratio 1"
but not just once it fills up the whole terminal window and doesn't stop. all i can do is close the terminal.
i do not know much about formats and conversions, so i do need some help with this.
the original file was pal divx mpeg-4 version 4, 25fps, 616x488.
after step two, the mpg was ntsc, 200x150. the difference in aspect ratios is probably it.
now, could i run the ffmpeg line and specify 616x488, like you showed with the 16:9 aspect ratio? and if yes, would a dvd with that aspect ratio work allright in a ntsc dvd player with a regular ntsc tv?

---

### Post by dannyboy79 on 2006-12-23
the script isn't working for me. does it matter that I have spaces in my avi filename? also, your script doesn't allow me to name the output file? all your script does is create an empty file called DVD.iso? also, I was wodering, how come you didn't enable tab completion for your program , is this hard to do? I ask because I want to learn how to progrm with python as well. can you help me possibly?

---

### Post by netyire on 2006-12-23
> How big is the file supposed to be. I'm trying to converts a 700mb video into an mpeg. Now ot's 1,6gigs big and 20 minutes long O.o The original file is 1.20 hours

Well since the original video that you want to convert, may have been encoded in a different format from mpeg2 (I think DVD videos are in mpeg2 format). In order for the movie to play on a normal DVD player, it needs to be converted into a format which the player can understand. So, since there is a change in the format of the video, there can also be a change in size. I think you can safely not worry about this one. :D 

About the reported time of the video, I think I had problems with it too, though I think the whole video still played. Play the .iso file with mplayer, and see if the whole length of the video is there. However if it is not, then you may have a problem with the video.


> thanks for the guide.
i just have one problem:
step three when i am trying to create the dvd file structure i get this error message:
"WARN: unknown mpeg2 aspect ratio 1"
but not just once it fills up the whole terminal window and doesn't stop. all i can do is close the terminal.
i do not know much about formats and conversions, so i do need some help with this.
the original file was pal divx mpeg-4 version 4, 25fps, 616x488.
after step two, the mpg was ntsc, 200x150. the difference in aspect ratios is probably it.
now, could i run the ffmpeg line and specify 616x488, like you showed with the 16:9 aspect ratio? and if yes, would a dvd with that aspect ratio work allright in a ntsc dvd player with a regular ntsc tv?

I am not sure if you can specify something like 616x488 as the aspect ratio for ffmpeg. Did you type:

ffmpeg -i <outputfile from the above> -target pal-dvd final.mpg

or

ffmpeg -i <outputfile from the above> -target pal-dvd -aspect 16:9 final.mpg

when you converted your video to mpg. If you typed the later with the -aspect 16:9, try again without the -aspect switch. Maybe this works for you. :-k If not maybe you can try something like:

ffmpeg -i <outputfile from the above> -target ntsc-dvd -aspect 4:3 final.mpg

See what works!

---

### Post by netyire on 2006-12-23
> **dannyboy79 said:**
> the script isn't working for me. does it matter that I have spaces in my avi filename? also, your script doesn't allow me to name the output file? all your script does is create an empty file called DVD.iso? also, I was wodering, how come you didn't enable tab completion for your program , is this hard to do? I ask because I want to learn how to progrm with python as well. can you help me possibly?

Hmm... maybe spaces can screw it up. ;) Anyway, try it again with quotes, perhaps something like:
"/home/netyire/christmas_at_natalie/2005.mov".

As for tab completion... I am not really sure as to how to implement it. Well if you have any ideas, please share! Hope this works for you. :-D

---

### Post by rbgCODE on 2007-01-09
Are there any applications just for converting DVD to xvid?

---

### Post by netyire on 2007-01-10
Well, there may be some program out there dedicated to converting DVDs to Xvid AVI files. Though using the command line is fairly easy. Forgive me if I'm going off topic here. ;) 

Anyway to dump the DVD as a .mpg file type
```
mplayer dvd:// -dumpstream -dumpfiles /home/bob/title.mpg
```

You can then type the following for encoding a 1 pass xvid file:
```
mencoder /home/bob/title.mpg -ovc xvid -oac lavc -lavcopts acodec=mp3:abitrate=128 -xvidencopts bitrate=1000 -o /home/bob/encode.avi
```

Or you can go through a two pass encoding:
```
mencoder /home/bob/title.mpg -ovc xvid -oac lavc -lavcopts acodec=mp3:abitrate=128 -xvidencopts pass=1:bitrate=1000 -o /dev/null
```

Then:
```
mencoder /home/bob/title.mpg -ovc xvid -oac lavc -lavcopts acodec=mp3:abitrate=128 -xvidencopts pass=2:bitrate=1000 -o /home/bob/encode.avi
```

Whichever choice you make, hope it works for you!:D

---

### Post by Rekr on 2007-01-15
Tried to do a 2 xvid movie the other night, upon completing the .iso I went to burn but the size was too big 4.4gb.   I see there is a -fs switch for ffmpeg that will limit the file size, anyone have any idea what the format is?  I'd like to limit both xvids to 2.1gb each when converting via ffmpeg.

---

### Post by dannyboy79 on 2007-01-16
i am not exactly sure if you are taking 2 xvid files (in .avi container) and then trying to combine them into 1 .mpg file and then use dvdauthor to create your iso from that?? or what but what I suggest you do is use mencoder to make your xvid files a certain size by getting the correct syntax from this website [http://gentoo-wiki.com/TIP_MEncoder_Tips_and_Tricks#Generating_AVIs_with_fixed_output_size_.282-pass_encoding.29](http://gentoo-wiki.com/TIP_MEncoder_Tips_and_Tricks#Generating_AVIs_with_fixed_output_size_.282-pass_encoding.29)

otherwise check out this website [http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC7](http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC7) for ffmpeg info but when I looked thru all the options I didn't see this -fs option you referred to or any place that talked about output file size.

---

### Post by eriqk on 2007-01-17
Works great!
I think it's a good idea to set aspect=n:n every time though, dvdauthor comes up with the warning and when I play the DVD, every player so far (totem, gxine, mplayer) assume widescreen even if it isn't. When I set 4:3 just in case, It Just Works.
Also: I tried the mencoder thing with a somewhat noisy QuickTime-Dv file and it came out horrible. Artefacts all over the place. It converted just fine when I threw it at ffmpeg directly though, so I think it depends on the used codec (what did you use? Sorenson, or mp4 or some such thing?).

Anyway, it worked great with a non-standard file I had laying around- an .avi rendered from iMovie at ~18 fps that used to cause lots of sync problems in various players and converters. I now, finally, have it on DVD. Yay!

Groet, Erik

---

### Post by Gyme on 2007-01-22
To: Gspinnada uhu

As the DVD aspect can only be 4:3 ( 1.333 ) or 16:9 ( 1.78 )  the image can become stretched, to ensure this does not happen you have to correctly set the size (-s) in ffmpeg

This link explains about aspect ratios and sizes:

[http://forum.videohelp.com/viewtopic.php?t=174200](http://forum.videohelp.com/viewtopic.php?t=174200)

So if your original avi video size is 616x488 then the aspect is 616/488 = 1.26

If your intended DVD is 16:9 (ntsc) then the width is 616 x 1.78 = 1096
The height is 1096 / 1.26 = 868  ( closest divisible by 4 )

Therefore your output size should be 1096x868
[COLOR="DarkRed"]
ffmpeg -i foo.avi -target ntsc-dvd -s 1096x868 foo.mpg[/COLOR]

Hope this helps:guitar:

---

### Post by jake3988 on 2007-01-22
Might I suggest tovid.sourceforge.net?  Its the easiest converter to dvd I've ever seen... so easy in fact, its the only one I've ever gotten to work myself.  Ever.

It automates everything.  The only format I've not gotten to work is .bin movie files.


Note: Tovid USES ffmpeg, dvdauthor, etc.  It just automates the process and makes it 10x easier.  As well as huge support for menus and background and whatnot to make your dvd look great!

---

### Post by user1397 on 2007-01-22
Yup, he's talking about _[this]("http://ubuntuforums.org/showthread.php?t=183936")_ guide

---

### Post by odzx on 2007-01-30
maybe someone can help me with this: this is the first time im converting any media sine i used to play video on my my tv by connecting my laptop to it. i dont have my laptop any more and my home dvd player is kind of old. i tried converting avi files with the nautilus script and with tovid, both seemed to work fine and after burnning the iso to a dvd i could watch it on my computer. the problem is that my home dvd player seems unable to load the burned dvd. i know old dvd players have problems with playing burned cd/dvd but i thought by converting the files the problem should be solved!?
forgive me if that seems like stupid question but i have to make sure before i just get rid of this old dvd player.
thanks.

---

### Post by binks on 2007-01-30
please go and check out you dvd player at [www.videohelp.com](www.videohelp.com) in the standalone section to check that the media you are using is compatible with your play i suspect i doesnt support the disc type or maybe just the manufacturer
binks

---

### Post by xyz on 2007-02-14
Sorry for not expressing myself like a video connaisseur; I'm not!

Somehow, using this HowTo, is it possible to reduce my_video.mpg (187MB) to a my_video.mpg (100MB or less)?

I need to upload that video but it can't be over 100MB.
Any help is greatly appreciated.

---

### Post by jake3988 on 2007-02-14
Yeah.  ffmpeg uses a default quality by default.  look at the manpage for specifics.  Simply lower the quality.

---

### Post by xyz on 2007-02-15
> **jake3988 said:**
> Yeah.  ffmpeg uses a default quality by default.  look at the manpage for specifics.  Simply lower the quality.

Thx...appreciate!

---

### Post by pay on 2007-02-15
[This](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html) guide is probably the best that I've seen.

---

### Post by xyz on 2007-02-15
> **pay said:**
> [This](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html) guide is probably the best that I've seen.
Thanks for providing the link. Might be of great help to someone.
Where I stand today in the video world of understanding, the guide is WAY over my head!

---

### Post by sn00ps on 2007-02-28
thank you for the python script

I added the following code to give me more control over the Label and ISO name

```


#ask for iso name and label name
isoname = raw_input("ISO Name:")
labelname = raw_input("Label:")
#make iso file
os.system("mkisofs -dvd-video -v -V " + labelname + " -o " + isoname + ".iso DVD")


```

---

### Post by finite9 on 2007-06-05
this guide wont work for me on Feisty amd64.

the first few steps work great, but creating the ISO fails...

```
andrew@everest:~/movies$ mkisofs -dvd-video -v -o DVD.iso ./DVD
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage 1.1.2 (Linux)
Scanning ./DVD
Scanning ./DVD/AUDIO_TS
Scanning ./DVD/VIDEO_TS
genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
genisoimage: Can't open VMG info for './DVD/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

```

Any ideas?

---

### Post by dannyboy79 on 2007-06-07
and does your VIDEO_TS folder have the .IFO file it's looking for? I would use tovid if you not familar with linux. It's the best video conversion GUI I have used, well it's the only one BUT still, it's GREAT!!! There's a guide here: [http://ubuntuforums.org/showthread.php?t=183936](http://ubuntuforums.org/showthread.php?t=183936)

---

### Post by finite9 on 2007-06-07
> **dannyboy79 said:**
> and does your VIDEO_TS folder have the .IFO file it's looking for?

Nope, because dvdauthor did not create it when it created the DVD structure.  I used the command  as given in the guide.

---

### Post by dannyboy79 on 2007-06-08
well there's your problem, if there's no .IFO file, than it's not going to work, so you should either try out tovid or try to figure out why dvdauthor didn't create the required files.

---

### Post by nami on 2007-06-10
Why not just used DeeVeeDee?

---

### Post by finite9 on 2007-06-11
> **nami said:**
> Why not just used DeeVeeDee?

yeah I tried that and it did create an ISO without issue, but it would not play in Totem, and I haven't had chance to troubleshoot yet.

---

### Post by dannyboy79 on 2007-06-11
may I ask why you're trying to check to see if a DVD plays within totem? Isn't the purpose of converting it to DVD is so that you can play in on a real DVD player? Also, have you installed all neccessary apps and libs for DVD playback to work?

[http://ubuntu-tutorials.com/2006/12/14/how-to-enable-dvd-playback-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/14/how-to-enable-dvd-playback-ubuntu-510-6061-610/)

---

### Post by eZtaR on 2007-06-11
GREAT work on the guide and the python app is simply the cherry on top of the icecream :D

One question though:
You wrote something about subtitleimplementation. Will this hardcode the subs or will you be able to switch them on/off? :)

---

### Post by dannyboy79 on 2007-06-12
> **eZtaR said:**
> GREAT work on the guide and the python app is simply the cherry on top of the icecream :D

One question though:
You wrote something about subtitleimplementation. Will this hardcode the subs or will you be able to switch them on/off? :)

i would think that they would be hard coded into the final mpg since he's applying the sub info before transcoding.

---

### Post by nami on 2007-06-12
> **finite9 said:**
> yeah I tried that and it did create an ISO without issue, but it would not play in Totem, and I haven't had chance to troubleshoot yet.

worked perfectly for me first time, just got an old divx file and ended up with an iso which i burnt to dvd and it played in my standalone dvd player. :KS

---

### Post by finite9 on 2007-06-12
> **nami said:**
> worked perfectly for me first time, just got an old divx file and ended up with an iso which i burnt to dvd and it played in my standalone dvd player. :KS

I have not tried burning the disc, but as all my other DVD ISOs work fine by dragging them into totem, this was the easiest way to check the ISO without wasting a disc.

---

### Post by dannyboy79 on 2007-06-13
great tip!!! what about when you get a folder that contains a VIDEO_TS and AUDIO_TS? what player would you use to verify the dvd structure prior to burning it then?? just curious as I use tovid and that's what tovid creates.

---

### Post by finite9 on 2007-06-13
> **dannyboy79 said:**
> great tip!!! what about when you get a folder that contains a VIDEO_TS and AUDIO_TS? what player would you use to verify the dvd structure prior to burning it then?? just curious as I use tovid and that's what tovid creates.

I think the Open Location command in VLC will let you open a folder that contains a DVD structure, But I would not say that this 'verifies' the entire structure.

---

### Post by dannyboy79 on 2007-06-13
i didn't mean I needed it to verify the structure, my point is that I would like to be able to open it as a dvd structure and see if it plays. I do this in windows after using AutoGK, it's intervideo windvd and it allows me to "open dvd from folder". I simply chose the parent folder that contains the 2 dvd folders (what I meant when I said dvd structure) and then it plays the dvd. So what i am sayign is that I don't want to click on a .vob file and play it using totem or mplayer, I want to be able to use some program that will see the 2 folders, VIDEO_TS and AUDIO_TS and be able to show me the resulting dvd structure playing as a dvd. I'll give VLC a shoot.

---

### Post by finite9 on 2007-06-20
> **liontiger said:**
> 
1)dvdauthor -o moviedirectory -v 720x576+pal+16:9 -a mp2+en  movie.mpg
2)dvdauthor -o moviedirectory -T
3)mkisofs -dvd-video -o movie.iso moviedirectory
4)Put an empty DVD ..... and Burn it with your favorite tool

Im still struggling with this ISO thing.

I converted my dv file to .mpeg then I use dvdauthor and mkisofs to create an ISO, as stated above, and this now works great.  But Totem cannot play the ISO like it plays every other DVD rip I have done.  It thinks it is a VCD!!  And it is apparently missing the protocol support.  Why does it think it's a VCD?  Btw, As far as I know, I have all bad and ugly gstreamer plugins from universe and multiverse.
```

 totem DVcaptest.iso 
** Message: Error: A VCD protocol source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1581): gen_source_element (): /play:
No URI handler for vcd

** Message: Missing plugin: gstreamer.net|0.10|totem|VCD protocol source|urisource-vcd (VCD protocol source)
no application found
** Message: No installation candidate for missing plugins found.
** Message: Error: A VCD protocol source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1581): gen_source_element (): /play:
No URI handler for vcd

** Message: Missing plugin: gstreamer.net|0.10|totem|VCD protocol source|urisource-vcd (ignoring)
** Message: All missing plugins are blacklisted, doing nothing
```

---

### Post by kelvin spratt on 2007-06-20
this a great peace of work but their is a much easer way use DEVEDE simply load your file do a 10 second preview if ok set aspect and PAL or NTSC  set sound that's it convert to ISO in one go. if you have problems with distorted sound there is a patch for mencoder as it has a bug in the latest version on the DEVEDE site.its that simple.

---

### Post by pabloisthewolf on 2007-12-24
Hi all:

Just started with Ubuntu and followed the instructions on this thread to a "T" but my DVD could not play on my Samsung DVD-3500 Combo Player?  Did burn with ntsc instead of Pal but I tried both and it still could not play?  Still scratching my head on this?  Any help would be appreciated.

---

### Post by srpkannan on 2008-06-25
I have 4 wmv files. I want to join them and then make a DVD video file. What should I do?

---

### Post by brons2 on 2008-06-26
Here's another one.  I have a European PAL format DVD (non-copywrighted) that I want to rip and re-burn to DVD in the US NTSC format.  Can I use mplayer for that?

The PAL DVD plays fine on my computer but I want something that will play on a normal player like my PS3 for example.  When I put it in the PS3 it says "PAL Format not supported"

---

### Post by smoka on 2008-12-07
Cheers for this howto - worked fine for me converting an .XviD using Hardy Heron (although just followed the steps, haven't tried the script).

Was a bit confused at first as couldn't see mkisofs in the repositories, but it seems to come included with genisoimage which seemed to be already installed by default [http://packages.ubuntu.com/hardy/mkisofs](http://packages.ubuntu.com/hardy/mkisofs) 

All I needed to do was:
sudo apt-get install mencoder ffmpeg dvdauthor

then just ran through the steps 2-4 and burnt the DVD.iso image using Brasero

---

### Post by Fire_Chief on 2009-02-25
> **jake3988 said:**
> Might I suggest tovid.sourceforge.net?  Its the easiest converter to dvd I've ever seen... so easy in fact, its the only one I've ever gotten to work myself.  Ever.

It automates everything.  The only format I've not gotten to work is .bin movie files.


Note: Tovid USES ffmpeg, dvdauthor, etc.  It just automates the process and makes it 10x easier.  As well as huge support for menus and background and whatnot to make your dvd look great!

Outstanding suggestion! I tried this last night with a movie I ripped from DVD and then dumped back onto a DVD+R and it worked like a charm. Very straightforward interface with a help sidebar that was actually helpful. I used Handbrake for the ripping and that was perfect as well.

Thanks!

---

### Post by dannyboy79 on 2009-02-25
> **srpkannan said:**
> I have 4 wmv files. I want to join them and then make a DVD video file. What should I do?

would avidemux work for this? otherwise can't you just merely type in 
```
join file1.wmv file2.wmv file3.wmv file4.wmv
``` I am not sure what the output file would be called though? Don't have any other suggestions sorry. Oh wait, tovid would be awesome for this. You could add ll the videos under one menu or you could create 4 different menus with each video in it's own menu. Good luck.

---

### Post by exosyst on 2009-03-01
Made a few changes to the script as it wasn't working for filenames with spaces.

I've included it in case anyone wants to use it.

Additionally it pops up a notification when done, uses mp3lame instead of lavc and also converts to pal rather than NTSC (as I'm in the UK).

It's so simple. even mum can use it now :P

Thanks to the original author for the know-how.

---

### Post by Sgtblades275 on 2009-04-25
thanks so much bro for this help. For me, all my video files I actually need on dvd are recorded as avi already so all I have to do is convert it and set to iso and I'm done! :D thanks much dude

---

### Post by pcjunkie on 2009-08-23
Thanxs

---

### Post by plgmgua on 2009-11-23
Is it possible to create a batch scrip to covert several videos in one single job?

---

### Post by eshwar_andhavarapu on 2009-11-29
Thank You!

---

### Post by emma00 on 2010-07-04
[QUOTE=netyire;1897671][FONT=Tahoma][SIZE=3]_A Guide To: Making DVDs from Various Formats (Get the script here: [http://www.ubuntuforums.org/showthread.php?p=1900382](http://www.ubuntuforums.org/showthread.php?p=1900382))_[/SIZE][/FONT]

After which type:

**mencoder <inputfile> -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o <outputfile>**


My file was already in .avi format but when i type this:

 mencoder <home/hada/Downloads/tkk/The karate kid> -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o <outputfile>

I got this error and am in doubt that if we have to write the name in output file or this will be generated


bash: syntax error near unexpected token `newline'

---

