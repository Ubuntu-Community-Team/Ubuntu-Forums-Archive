---
title: "Flash Demonstration Tool?"
date: 2010-12-02
forum: Programming Talk
---

### Post by Hodge_1974 on 2010-12-02
Hi Everyone; i have a Java/MySql application that I've written. I need to make a flash demonstration of its use and I was wondering if folks had a preferred tool in Ubuntu to do this. Iv'e seen flash demos done before, but never have delved very far into creation of them.

Thanks :p

---

### Post by lykeion on 2010-12-02
Do you mean a screencast flash embedded video?

You can use gtk-recordMyDesktop. 
Installation and usage info here: [http://www.howtoforge.com/creating-screencasts-with-recordmydesktop-on-ubuntu-9.04](http://www.howtoforge.com/creating-screencasts-with-recordmydesktop-on-ubuntu-9.04)
(it's for 9.04 but should be the same for later Ubuntu versions as well)

It saves video as OGV, if you need to convert to FLV look at this page: [http://techies-r-us.com.au/blog/?p=350](http://techies-r-us.com.au/blog/?p=350)

---

### Post by Hodge_1974 on 2010-12-02
Cool. Thanks lykeion. :)

---

### Post by lykeion on 2010-12-02
Hope it works for fine you. If it does please tag this thread as SOLVED ([http://ubuntuforums.org/showpost.php...51&postcount=6](http://ubuntuforums.org/showpost.php...51&postcount=6)) to let others find solutions easily.

---

### Post by Hodge_1974 on 2010-12-02
Will do.

---

### Post by Hodge_1974 on 2010-12-03
Well I was able to make a video after some experimentation with gtk-recordMyDesktop. That was fairly straight forward. The only trip up I had was finding and then understanding the red bulb in the upper right corner on the screen was my 'Stop' control; once I figured that out, I was able to create an .ogv file.

I haven't tried converting to Flash yet, but I did try and convert to .wmv as the majority of the viewers will be using windows and I wanted the most accessible format so there was as little  technical overhead as possible for them to go straight into viewing it. 
This is where things got sticky. Tried using Winfmm, and a variety of other video editing tools from the repository, all with the same result. They played the .ogv file back as a distorted block junk pile; this was just playing the .ogv file. Once converted to .avi it was the same deal. However, movie player played the .ogv files just fine. Finally I stumbled onto a[ post ]("http://www.pclinuxos.com/forum/index.php?topic=67816.0")about a guy with a similar issue; not a lot of solutions there other than he was using mencoder for a workaround. 
I installed the mencoder from the repositroy and went to the [mencoder website ]("http://www.mplayerhq.hu/design7/news.html") to try and figure out what the command syntax was to accomplish conversion from .ogv to .avi. I skimmed through the manual to no avail. I'm sure its there somewhere, but mencoder does so much other stuff, I wasn't a fan of trying to sift through all of that jazz to find what i was looking for. So I cheated and googled it and found this [page]("http://ubuntuswitch.wordpress.com/2007/10/05/howto-convert-ogg-to-avi-with-mencoder/"). Didn't see a name to give credit to, but thanks to you anonymous blogger).
I thieved the line of code in his post and substituted my filenames and it worked like a champ; I took the resulting .avi file and converted it to .WMV with WinFF. The quality is a little soupy but its sufficient for now. I intend to try review an work through the 2nd link that lykeion posted for conversion to a Flash format and report back.
Hopefully this is helpful to people.

---

### Post by lykeion on 2010-12-05
Nice to follow your progress. Some questions:
How are you going to distribute the video (offline, online, own server, youtube)?
What viewers are you talking about (Windows Media Player, Flash player, Browser plugin)?

Some considerations:
I personally would prefer using ffmpeg instead of mencoder for this kind of video conversions. See [this]("http://en.linuxreviews.org/HOWTO_Convert_video_files")
WMV is a crappy format, and I'm not just saying this because it's Microsoft. I agree with what this man says [here]("http://warp.povusers.org/grrr/proprietaryvideoformats.html")

---

