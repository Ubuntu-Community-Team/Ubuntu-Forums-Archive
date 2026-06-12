---
title: "Having trouble playing video or even installing new video player"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by joedirt313 on 2008-05-22
When I try to play a video it give me this error code :

Video codec 'DivX 5' is not handled. You might need to install additional plugins to be able to play some types of movies

When I got install and remove program it give me this message:
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

What did I do wrong or better yet how do I fix it?
all I was trying to do was play a video I dl off the net?

---

### Post by anystupidname on 2008-05-22
-Run the command it suggests (apt-get install -f) and make sure it completes.
-Add repo [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
-Then "aptitude update && aptitude install vlc w32codecs mplayer mozilla-plugin-vlc"

---

### Post by MaindotC on 2008-05-22
Why not just have him install the ubuntu-restricted-extras?

---

### Post by joedirt313 on 2008-05-22
Ran the command code it suggested and fixed the installation problem it the process of following tutorial in installing codecs. 
I dont know why all of a sudden it did this though I was watching the videos then all of a sudden it started working funky and giving me all kinds of cant and wont do's?

and thank you for the swift response much appreciated.

---

### Post by MaindotC on 2008-05-22
In VLC, go to Settings -> Preferences -> Video -> Output Modules.  Select "X11 Video Output".

---

### Post by joedirt313 on 2008-05-22
I am sorry you lost me on the vlc?

---

### Post by MaindotC on 2008-05-22
VLC is the media player that you installed by following anystupidname's directions.  Go to Applications -> Sound & Video and you should see VLC in there.  Then follow my directions.

---

### Post by sayakb on 2008-05-22
I don't think that changing the output module will alter codecs. Just fix broken packages and install ubuntu-restricted-extras which would install all necessary gstreamer plugins.

---

### Post by anystupidname on 2008-05-22
> **strAlan said:**
> Why not just have him install the ubuntu-restricted-extras?

@strAlan: Why not? :) Just habbit I guess.

@joe: You're welcome. Instead of adding the medibuntu repo, you could enable restricted extras (take your pick).
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
For your last post, Alan has explained further.

---

### Post by MaindotC on 2008-05-24
dirt what's the status on this - I want to know if I can unsubscribe or not.

---

### Post by Nemo_bis on 2009-11-27
Ubuntu 9.10 Karmic gives some problems, see [Karmic killed my codecs]("http://ubuntuforums.org/showthread.php?t=1317236") for help; you may need to [reinstall some packages]("http://ubuntuforums.org/showpost.php?p=8281817&postcount=18").

---

