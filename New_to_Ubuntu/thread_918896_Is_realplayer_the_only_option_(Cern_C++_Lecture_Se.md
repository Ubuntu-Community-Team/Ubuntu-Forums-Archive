---
title: "Is realplayer the only option? (Cern C++ Lecture Series)"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Jonas thomas on 2008-09-13
I hope you can lend some advice/options....

I'm trying  watch this beyond cool lecture series on C++ my computer....
Hear's the link.. [http://www.wlap.org/cern/lectures/tech/c/00/]("http://www.wlap.org/cern/lectures/tech/c/00/")


```

Edit:2008-09-13
There is a more up to date version of the lecture and was told to run it  detached in linux. Here it is:

[http://esmane.physics.lsa.umich.edu/wlap-cwis/SPT--BrowseResources.php?ParentId=215]("http://esmane.physics.lsa.umich.edu/wlap-cwis/SPT--BrowseResources.php?ParentId=215")

Also a more up to date link to the lecture archive is at [http://atlascollab.umich.edu/archive]("http://atlascollab.umich.edu/archive")
```

I'm running, Hardy, Firefox Browser 3.0.1 ,Totem-plugin-viewer 2.22.1
Hear's my problem.  On my linux machine, the only way I can watch the lecture is to start from the beginning and manually advance the slides.

On my wifes, Win 2k machine running Firefox, the slides automatically advance but I can only what it by starting from the beginning.

I sent this lecture link to a geek friend of mind and he had nothing but harsh criticism for Realplayer (on his windows machine anyway)...

I found that there is a download on [realplayer for Linux]("http://www.real.com/linux")    If this program was downloaded through synaptic, I'd try it.  But I'm a little reluctant to download from a website..

So.... I guest the questions are....
Is RealPayer the only option to get this lecture working on firefox?

Are there any negatives to running RealPlayer in Linux?

What is the proper way to install RealPlayer in case I want to blow it away. (I saw some one else was having difficulties deleting this.[http://ubuntuforums.org/showthread.php?t=914455&highlight=realplayer]("http://ubuntuforums.org/showthread.php?t=914455&highlight=realplayer") )

It's been somewhat frustrating since these lectures are over a 1 hour long and trying to block out that much time with a five year old is next to impossible and I haven't been able to get the lecture to start midstream.. :confused:

---

### Post by Jonas thomas on 2008-09-13
Well....
I just found some ubuntu instructions on how to do this;
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin")

---

### Post by Mornedhel on 2008-09-13
You can use mplayer (you may need to install the w32codecs package from Medibuntu) to play RealMedia files. Mplayer also has a Firefox plugin, but I usually just use it from the console.

The URL you provided also has a link for downloading an archive which apparently has slides and videos inside. Those work with mplayer (just tested).

---

### Post by whitethorn on 2008-09-13
I downloaded it, unpacked and it worked with mplayer. So no need to install Realplayer, I also had a hard time uninstalling it.

---

### Post by Jonas thomas on 2008-09-13
> **whitethorn said:**
> I downloaded it, unpacked and it worked with mplayer. So no need to install Realplayer, I also had a hard time uninstalling it.

I think if you download you only get the lecture and not the slides... I think you need to use the plugin through the browser.....

---

### Post by oldos2er on 2008-09-13
Tried to run it in Realplayer and received this error: The content you are trying to play uses an audio codec (DNET) that is obsolete and no longer supported. Please contact the content provider about using a supported codec.

---

### Post by Mornedhel on 2008-09-13
There is a folder called "slides" with what appear to be a dozen GIF slides in the archive.

---

### Post by Jonas thomas on 2008-09-13
> **Mornedhel said:**
> You can use mplayer (you may need to install the w32codecs package from Medibuntu) to play RealMedia files. Mplayer also has a Firefox plugin, but I usually just use it from the console.

The URL you provided also has a link for downloading an archive which apparently has slides and videos inside. Those work with mplayer (just tested).

Are you able to advance to a midpoint in the lecture??

---

### Post by SunnyRabbiera on 2008-09-13
hmm, the way this behaves seems very unusual.
I have realplayer insalled but it doesnt seem to plug in for this page.
I think this is a firefox 3 issue.

---

### Post by ronnielsen1 on 2008-09-13
>  So no need to install Realplayer, I also had a hard time uninstalling it.]
It's not worth it. I've never used it in linux

---

### Post by Mornedhel on 2008-09-13
I can use the standard mplayer controls, including Play/Pause, seek ahead for 10s, 1m or 10m, etc. So basically, yup.

---

### Post by Jonas thomas on 2008-09-13
> **oldos2er said:**
> Tried to run it in Realplayer and received this error: The content you are trying to play uses an audio codec (DNET) that is obsolete and no longer supported. Please contact the content provider about using a supported codec.

Bummer, perhaps mplayer route is the way to go...
On my wife's Win 2000 computer, somehow the video sends a signal to advance the slide.....
If I could just get the lecture to advance mid-point, I could advance the slides manually.

---

### Post by Jonas thomas on 2008-09-13
> **Mornedhel said:**
> I can use the standard mplayer controls, including Play/Pause, seek ahead for 10s, 1m or 10m, etc. So basically, yup.

Huh... Are you using Firefox??  
I haven't been able to do that.....
(Are the slides advancing??)

---

### Post by Mornedhel on 2008-09-13
No, I basically got the archive from the Download link, tar xvzf'ed it into a folder, and from there I use mplayer 001.rm from the console to watch the video. The mplayer plugin for Firefox *might* work, I never really tried it.

This also means the slides are not advancing, but you can use your favorite image viewer to display them alongside the mplayer window.

---

### Post by Jonas thomas on 2008-09-13
> **Mornedhel said:**
> No, I basically got the archive from the Download link, tar xvzf'ed it into a folder, and from there I use mplayer 001.rm from the console to watch the video. The mplayer plugin for Firefox *might* work, I never really tried it.

This also means the slides are not advancing, but you can use your favorite image viewer to display them alongside the mplayer window.

The way they have it set up is pretty cool (If I could get it to work).
I think the way it's supposed to work is that you click on the lecture index and it'll take you to that point in the lecture.
I think I'm going go through and make sure I have the appropriate codecs setup for mplayer.  I found a pretty interesting link on how to do that.


[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html")

---

### Post by Jonas thomas on 2008-09-13
> **Jonas thomas said:**
> The way they have it set up is pretty cool (If I could get it to work).
I think the way it's supposed to work is that you click on the lecture index and it'll take you to that point in the lecture.
I think I'm going go through and make sure I have the appropriate codecs setup for mplayer.  I found a pretty interesting link on how to do that.


[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html")

@#$@# I went through the instructions on the above link.... I think I was missing a codec.  I managed to get the video to advance but I lost my sound...  Time to dive into the sound settings.....

---

### Post by Jonas thomas on 2008-09-13
> **Jonas thomas said:**
> @#$@# I went through the instructions on the above link.... I think I was missing a codec.  I managed to get the video to advance but I lost my sound...  Time to dive into the sound settings.....

I'm getting darn close to getting this thing to work.....
I loaded the [website]("http://wlap.physics.lsa.umich.edu/cern/lectures/tech/c/00/real/f001.htm")

Just below the video window there is a speaker icon.  I right clicked on it and selected "Configure".  My Video Output and Audio Output was blank.  I selected gl and alsa (which got the sound working).

I got the video advance working which was the major goal :)

Now, if I can get the slide advance working that would be the cake topper..
In the configure everything is check off(by default) excepts for the following:
[LIST]
[*]Enable MIDI Support
[*]Enable DivX Support
[*]Play media directly from site (No Caching)
[*]Connect to RTSP media of TCP
[*]Use HTTP instead of RTSP
[/LIST]

Any chance anyone knows if one of these is the  magic option that will get the slides to advance automatically??

---

### Post by SunnyRabbiera on 2008-09-13
For Midi, you will need timidty, and possibly kmid.
For divix, you may want to consider installing more restricted packages or using medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Jonas thomas on 2008-09-13
> **SunnyRabbiera said:**
> For Midi, you will need timidty, and possibly kmid.
For divix, you may want to consider installing more restricted packages or using medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I brought forced through the options and couldn't get the slide advance to work. What you say would explain that.  The only thing it's a shot in the dark that that's my problem. I'm am so close to getting this thing to work in ubuntu... I'm think I'm going to contact the site.. and see If I can get someone to offer help.  The disturbing thing is I don't know if this site has been updated for a while.. For Academic site, you'd think there would be all kind of advise on how to get this running in Linux... 

Any here the link to the [FAQ's ]("http://www.wlap.org/help.html")
I guess the next logical step is to see if I got javascripting enabled....  I 80% sure I do.. I need to figure out how check that within the browser...

So... [this]("http://support.mozilla.com/en-US/kb/JavaScript#_Enabling_and_disabling_JavaScript") answers that.

Yep.... It's enabled....  I guess it's time to email the site...

Ok.. I'm going to try the realtime route.  I just finished the installation per instructions I links about.
I guess know I need to get it hooked up.
I used this link as a guide
[http://ubuntuforums.org/showthread.php?t=118946]("http://ubuntuforums.org/showthread.php?t=118946")

I downloaded the lecture and tried to fire it up with realplayer and I got the same message someone else had earlier:
"The content you are trying to play uses an audio codec (DNET) that is obsolete and no longer supported. Please contact the content provider about using a supported codec"

I googled and found out what the deal is:
[http://www.hitsquad.com/smm/programs/RealPlayer_linux/wwwboard/messages/89.html]("http://www.hitsquad.com/smm/programs/RealPlayer_linux/wwwboard/messages/89.html")

---

### Post by Jonas thomas on 2008-09-13
I'm starting to regret that I loaded up realplayer.
I just found a way to load it up via synaptic.
[http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml]("http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml")

I wish I would have have known about that first... I wonder if I load up and mark for removal if it will get rid of all the stuff.

---

### Post by Jonas thomas on 2008-09-14
> **Jonas thomas said:**
> I'm starting to regret that I loaded up realplayer.
I just found a way to load it up via synaptic.
[http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml]("http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml")

I wish I would have have known about that first... I wonder if I load up and mark for removal if it will get rid of all the stuff.

I found the uninstaller script (last entry on the Faq)for the bin file(which I used).
They have a use at your own risk disclaimer......
:(
[https://player.helixcommunity.org/2005/help/playerfaq.html]("https://player.helixcommunity.org/2005/help/playerfaq.html")

---

### Post by Jonas thomas on 2008-09-16
> **Mornedhel said:**
> No, I basically got the archive from the Download link, tar xvzf'ed it into a folder, and from there I use mplayer 001.rm from the console to watch the video. The mplayer plugin for Firefox *might* work, I never really tried it.

This also means the slides are not advancing, but you can use your favorite image viewer to display them alongside the mplayer window.

 I emailed university of michigan.  They said that the lecture is meant to run as detached in linux.

There is a newer recording of Paul Kunz’s C++ course:

 [http://esmane.physics.lsa.umich.edu/wlap-cwis/SPT--BrowseResources.php?ParentId=215]("http://esmane.physics.lsa.umich.edu/wlap-cwis/SPT--BrowseResources.php?ParentId=215")

 There is also a more up-to-date link to their archive:
[http://atlascollab.umich.edu/archive]("http://atlascollab.umich.edu/archive")

I'm a little fuzzy as to whether or not these links are supposed to run better in linux..

---

