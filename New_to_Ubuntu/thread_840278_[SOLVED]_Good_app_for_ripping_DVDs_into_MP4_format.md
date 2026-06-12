---
title: "[SOLVED] Good app for ripping DVDs into MP4 format?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by AOZ on 2008-06-25
Anyone know a good app, preferably from the repos that can rip DVDs into MP4 format?

---

### Post by HalPomeranz on 2008-06-25
It's not in the repos, but I've used HandBrake ([http://handbrake.fr/](http://handbrake.fr/)) and it works well.

---

### Post by AOZ on 2008-06-25
i got the tarball but now what? could you write a quick howto? thanks in advance

---

### Post by 3rdalbum on 2008-06-25
I use [Acidrip]("apt://acidrip"), but the interface is a bit eccentric. It does everything I want of it though.

---

### Post by bluepowder7 on 2008-06-25
i use a two-step process, and both of these are run from the terminal.

1 - **vobcopy** to extract the info from the DVD and stuff it on my hard drive as a VOB file (the rip portion)
2 - **h264enc** script to encode the VOB file using whatever quality setting i want and make an MP4 file

vobcopy is in the repos ("sudo aptitude install vobcopy")
h264enc is just a script that you download and install manually (google it), but it does require mencoder and a few other apps to work.  read the FAQ and run "h264enc -sc" once you have it installed to see which other apps are missing

i use the 1-pass / fixed-quality (CRF = 22) approach to encoding

---

### Post by aeiah on 2008-06-25
+1 for acidrip, although i dont think you get amazing control if using the x264 codec. this might have changed now though

---

### Post by bluepowder7 on 2008-06-25
> **aeiah said:**
> +1 for acidrip, although i dont think you get amazing control if using the x264 codec. this might have changed now though

last time i used it (a month ago on 7.10), you got NO control over any aspect of it.  flat out, it sucked, which is why i ended up going the vobcopy / h264enc script way.

---

### Post by AOZ on 2008-06-25
But acidrip only converts it to .avi or .mpg? unless im missing somethign?

---

### Post by bluepowder7 on 2008-06-25
oh wait - what kind of video codec do you want to use?  if you want to use the mp4v codec and make an mp4 file, you can do that using VLC (not the best, but quite simple).  if you want to use the wonderful h264 video codec and make an mp4 file, i personally love the script.

---

### Post by AOZ on 2008-06-25
I can rip a DVD to MP4 in VLC? and how would i do it using your suggestion? I dont need any advanced controls really i just want to get DVDs onto my ipod the fastest easiest way possible

---

### Post by bluepowder7 on 2008-06-25
> **AOZ said:**
> I can rip a DVD to MP4 in VLC? and how would i do it using your suggestion? I dont need any advanced controls really i just want to get DVDs onto my ipod the fastest easiest way possible

from VLC, go File - Open Disc

on the top, where is says title / chapter, select title "1" and chapter "0" (that means encode title 1 (usually the main movie), starting at chapter 0 (the very beginning) - if that doesn't work right, set chapter to "1")

on the bottom, check "Stream/Save" and click the "settings" box to take you to the next setup window

there, check "File" box, and enter the file name "like maybe /home/john/Videos/Movie1.mp4"

below that, encapsulation "MP4"

below that, check the "audio" and "video" boxes and select mp4a and mp4v.  you can leave the default bitrates, or lower them to make smaller files.

---

### Post by AOZ on 2008-06-25
K so i did all that and once i hit ok, the scroller thing shot across the screen and VLC closed. thanks for the help btw

---

### Post by bluepowder7 on 2008-06-25
really?  and you do have a DVD inserted?  if you're on the main VLC window, and you hit the play button, the movie plays normally?

---

### Post by AOZ on 2008-06-25
Wow i feel really stupid i had the special features disc instead of the actual movie.... I started the converison il let you know how it goes, should take around 20 minutes. thakns alot for your help i was getting pretty frustrated

---

### Post by bluepowder7 on 2008-06-25
no problem.  you might have to tweak things here and there to get it how you like it, and maybe there's a setting here and there i've forgotten about, but it SHOULD work - i personally haven't used the VLC approach in a while since i'm doing the script stuff.

---

### Post by AOZ on 2008-06-25
Hmm it finished the hour and 45 minute part and then strated doing all these 1 minute 35 second things and is just doing those over and over again. is this normal? and when i goto where i saved the file and clcik properties the file is onyl 18 kb.

---

### Post by AOZ on 2008-06-25
Ya that didnt work.... could you give me a guide on how to use the script way?

---

### Post by bluepowder7 on 2008-06-25
gimme a few mins to double-check the whole process on my machine with a DVD...

---

### Post by bluepowder7 on 2008-06-25
but you are able to play the dvd using vlc normally, so you have the libdvdcss2 stuff installed, right?

ok, here's what i'm doing now for American Beauty

load the cd, open vlc, click "file" - "open disc" - on the disc tab, i have "dvd menus" selected, device is "/dev/scd0" (here yours might be different), title=1, chapter=0, check the "stream/save" button, hit the "settings" button, and there i have "file" checked, entered my file path (/home/greg/Desktop/test1.mp4), in the middle encapsulation is "mp4", in the transcoding section i have both "audio" and "video" checked, and using mp4v and mp4a in the pull-down menus there.  for fun, i knocked down the bitrates to 512 video / 128 audio.

after 3-4 mins, i stopped it and it encoded around 21 minutes worth of the movie. file size at this point is 85 megs.

---

### Post by AOZ on 2008-06-25
Man i have no idea what happened but i did the *exact* same thing before but i just did it again and it worked.....really wierd but the good news is i finally have the grindhouse in mp4. YAY! ur a lifesaver bluepowder

---

### Post by bluepowder7 on 2008-06-25
the script method that i use encodes stuff using the h264 codec.  does your iPod support decoding that file type?  it'll still be an mp4 file, but the encoder would be h264 instead of mp4v.  the quality is great, but it's quite slow (a 1hr movie would take 2hrs to encode).

if you want to do it that way, though, and your iPod supports h264, then:

* install vobcopy (in terminal, write "sudo aptitude install vobcopy")
* download the .tar.gz of the h264enc script from here ([http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/))
* if you'd rather use Xvid instead of h264, there's a separate script for that as well
* place the .tar.gz file in your home directory
* right-click it and select "extract here"
* go into the folder and find the "install" file, and double-click it (run in terminal if it asks - if that doesn't happen, rename it to "install264", open terminal, and type "install264" and that SHOULD do the trick)
* in terminal, type "h264enc -sc" and see how many OK's you get and what "errors" you get, and post them up here

to rip the dvd, in terminal just type
"vobcopy -l -n 1 -o /path/to/folder" where the pathtofolder is the path to a folder where you have enough space (over 5gigs) to store the entire ripped dvd

---

### Post by bluepowder7 on 2008-06-25
but, now that you got VLC to work (quite easy, and quick), you don't need to worry about the script stuff in terminal.

yay!

---

### Post by socngill on 2008-06-27
Out of interest (and I'm sorry if this question is a bit of a no, no) but how did you get around the encryption on the DVD?  In Windows I always used SlySoft and Nero Recode but as far as I am aware there is nothing which does this in Linux?

Or am I missing something...?

Again sorry if this sort of talk is not permitted.

---

### Post by bluepowder7 on 2008-06-29
> **socngill said:**
> Out of interest (and I'm sorry if this question is a bit of a no, no) but how did you get around the encryption on the DVD?  In Windows I always used SlySoft and Nero Recode but as far as I am aware there is nothing which does this in Linux?

Or am I missing something...?

Again sorry if this sort of talk is not permitted.


sudo aptitide install libdvdcss2

---

### Post by leemajors on 2008-06-29
what is this "DVD" of which you speak?

---

### Post by uclalinux on 2008-06-29
k9copy

---

### Post by bluepowder7 on 2008-06-29
> **leemajors said:**
> what is this "DVD" of which you speak?

it's like vinyl, but with flashlights.

---

### Post by graveson on 2008-07-01
thanks for heads on the h264enc script. is there a way to automate it somehow to encode files for the ps3 without having answer all those questions. honestly i do understand most of what the script asks.

---

### Post by bluepowder7 on 2008-07-01
> **graveson said:**
> thanks for heads on the h264enc script. is there a way to automate it somehow to encode files for the ps3 without having answer all those questions. honestly i do understand most of what the script asks.

near the end of the questions, it asks if you'd like to view the mencoder options, and right after that it asks you if you'd like to save them.  hit 'y' or 'Y' to save, and accept the default (just hit enter).  btw - you don't ever need to type 'n' for no, just hit enter.

now, if all your input files are pretty well the same and you want to use the same settings for each, just open up the '/home/graveson/batchfile' in a text editor, and copy-paste the block of code as many times as needed.  you'll then obviously need to edit the input and output file name in each block (i think there's 11 or 12 instances per block), but you can leave the same temporary file name (it gets deleted at the end of each block), save the batchfile, and use it with the script (check the 'man h264enc' page for exact details, i can't recall it offhand right now)

if you want to change one or two settings, you can likely find out where they are in the slew of commands.  if you're not 100% sure, go through the whole script again, answering questions for the other type of setup you want, and at the end again say yes to saving the options.  it'll append it to your current file, so the previous entries are safe.

---

### Post by LazyEngineer on 2008-08-05
Thanks for this thread - this is exactly what I was looking for!  Google searches were just getting frustrating - lots of false hits or sites trying to sell you stuff.

I'll be trying VLC tonight to do a conversion and then try that on the iPod.  The H264 codec route sounds interesting - but cumbersome.  Is it that much clearer?  Can anyone confirm that it works on an iPod?

---

### Post by LazyEngineer on 2008-08-06
Alas, this was not successful.  VLC did rip the DVD and make the .mp4 file, but for some reason I can't import this into iTunes.  FYI, I'm using Ubuntu to run VLC and to the rip, and then I transfer the file to my NTFS partition where I have iTunes in XP.  

Is there a setting I missed?

---

### Post by ogromano on 2008-08-13
> **bluepowder7 said:**
> but you are able to play the dvd using vlc normally, so you have the libdvdcss2 stuff installed, right?

ok, here's what i'm doing now for American Beauty

load the cd, open vlc, click "file" - "open disc" - on the disc tab, i have "dvd menus" selected, device is "/dev/scd0" (here yours might be different), title=1, chapter=0, check the "stream/save" button, hit the "settings" button, and there i have "file" checked, entered my file path (/home/greg/Desktop/test1.mp4), in the middle encapsulation is "mp4", in the transcoding section i have both "audio" and "video" checked, and using mp4v and mp4a in the pull-down menus there.  for fun, i knocked down the bitrates to 512 video / 128 audio.

after 3-4 mins, i stopped it and it encoded around 21 minutes worth of the movie. file size at this point is 85 megs.
Thanks a lot for this post, I had no idea VLC could do this... Everything worked exactly as you said. Though I actually had it convert an avi to an mp4 by going on the open file option instead of open disc. Now if I could just get my PSP to play the mp4 file I would be set.
It is supposed to be able to play mp4s, but for some reason it says the data type is not accepted. 

Any suggestions would be greatly appreciated.

---

### Post by hanexar on 2008-08-17
Ogromano: Check for the resolution: the max the slim PSP is accepting is 320x240 for full screen or 368x208 (unless you have custum firmware...)

I'm using ffmpeg to convert my video to PSP, here are my setting for 16:9:

```
ffmpeg -i INPUT -f psp -r 23.5 -s 368x208 -b 768k -ar 24000 -ab 128k OUTPUT.MP4 
``` 

This give my ~270meg/hr of video.

---

### Post by ogromano on 2008-08-18
Thanks very much Hanexar... it worked and it finally played the mp4. I do have custom firmware on my psp, does that make any difference on the resolutions it can play??

One more question, is there a GUI for ffmpeg... being an ubuntu beginner I prefer GUIs. Kmediafactory was mentioned on another thread, but wouldn't that be for KDE?

Thanx again.

---

### Post by hanexar on 2008-08-18
There's no GUI for ffmpeg. I've been looking for a long time for something with a GUI but I always come back with ffmpeg because it's the only tricks that always work.

If you want to play with the different option, here's what I've found that work:

you can change the frame rate (r) to 14.935, you can reduce the video bitrate (b) to anything below 768k, you can upgrade audio to 48000 khz (-ar), or change the audio bit rate (ab). You can probably reduce the resolution (s) to anything lower than those I gave you. 

If you want smaller file, I'll suggest to drop the video bitrate and the audio bitrate to something smaller.

I tried like a dozen different setting, and those I gave you are my favorite (Quality/file size). I went upgrading the quality until I couldn't notice a significant difference between the file.


With a custum firmware, you can install PSPlayerMT (I don't recall were I found it, but it was a version for the 3.71M33 firmware) and with this program, you can play video with a resolution up to 480x282. You can encode your video with this line:

```

ffmpeg -i INPUT -f psp -r 23.5 -s 480x282 -b 768k -ar 24000 -ab 128k OUTPUT.MP4
```

I personally don't use it because I rather the XMB video player and this programs overclock your PSP. But the higher resolution is quite nice.

---

### Post by vgrisham on 2008-08-18
> **uclalinux said:**
> k9copy

amen. 

k9copy is a great app.

---

### Post by ogromano on 2008-08-19
It's great to find some PSP lovers around here, now I don't have to boot back to windows everytime I want to create my mp4s.

Thanx for the help, gotta go ffmpeg some vids!! :)

---

### Post by dmsymr on 2008-08-25
> **bluepowder7 said:**
> from VLC, go File - Open Disc

on the top, where is says title / chapter, select title "1" and chapter "0" (that means encode title 1 (usually the main movie), starting at chapter 0 (the very beginning) - if that doesn't work right, set chapter to "1")

on the bottom, check "Stream/Save" and click the "settings" box to take you to the next setup window

there, check "File" box, and enter the file name "like maybe /home/john/Videos/Movie1.mp4"

below that, encapsulation "MP4"

below that, check the "audio" and "video" boxes and select mp4a and mp4v.  you can leave the default bitrates, or lower them to make smaller files.

Great instructions (for me, anyway!) thankyou. Now that I have the file in mp4 format on my desktop, how do i get it onto my ipod? I have gtkipod, songbird, rythmbox, amarok, banshee and vlc installed on ubuntu 8.04....any suggestions?
Ta

---

### Post by Milesio on 2008-10-13
Ok, I'm officially confused with **k9copy**.

I can copy dvds right, then I burn them with k3b and it all works but... **mpeg4**? :confused: 
When I click on mpeg4 it "seems" to work. It takes its while to process it, I can see the progress bar and all and then... nothing!! After a good while waiting and seeing it "work" there's no output file to be found, anywhere. Even after having specified exactly how the file should be named and where it should be saved to.
Is it working at all?
And *everything else* works, so as far as I know I have all the required libs, etc... Where's my *.mp4 file gone I wonder?? (if there is any!) :P

Am I maybe missing some very silly/obvious point maybe? :D

Any help would be greatly appreciated.

---

