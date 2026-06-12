---
title: "New to linux, need help installing PIL"
date: 2007-01-25
forum: Programming Talk
---

### Post by Bombdogs on 2007-01-25
Hi all,

didn't know whether to post this in the absolute beginner section, thought I may get a better response here...

I've been using Python on windows for about a month. Switched to linux (ubuntu) about 2 days ago & I'm really groping around in the dark trying to install the python image library that I need. My problem is with the linux part of things rather than the python part.

So I followed the readme, which instructs me to extract the tar & then run a pyhton program which builds the library. I extracted the tar to my user space...

/home/paul/Python/ExtensionLibrary

which I created myself. The readme says that I should extract it to my Python Extension library if I have one... I didn't or didn't know where to look, so created it in my user space. It also says that using your own directory should be fine too. So that's me confused.

Running the build script produces loads of errors, mainly directory not found but a few others thrown in for good measure too.

Any pointers would be great, I've read loads & am still struggling to understand what I'm doing wrong here.

Many thanks,

PMF

---

### Post by runningwithscissors on 2007-01-25
Well there is a very likely chance that the library is in the online repositories.

Don't download tarballs off the net to install them. Search for it in synaptic or using apt.

I could tell you how, but I have never used Debian or any of its derived distributions. :(

---

### Post by Steveire on 2007-01-25
```

sudo aptitude install python-imaging

```

---

### Post by Bombdogs on 2007-01-26
Well thanks very much Steveire, that worked perfectly and was a lot easier than the route I was going down.

If I may pick your brains so I know what I did there...

sudo - run as superuser
aptitude - package manager program
install - i presume thats a command sent to aptitude
python imaging - the thing to install

is that the correct reading? 

Also I need to install ffmpeg - I've scoured the add/remove programs bit of ubuntu & couldn't find it listed. Again I've ended up with a tarball downloaded from the net, which needs to be compiled, which scares me a lot! Can I use aptitude to install this too?

sudo aptitude install ffmpeg

would that be right?

Again many thanks for the help,

PMF

---

### Post by Steveire on 2007-01-26
Sure. Aptitude can also be used to search by the way.

```

stephen@flea:~$ aptitude search ffmpeg
p   ffmpeg                          - multimedia player, server and encoder
p   ffmpeg2theora                   - Theora video encoder using ffmpeg
p   gstreamer0.10-ffmpeg            - FFmpeg plugin for GStreamer
p   gstreamer0.8-ffmpeg             - FFmpeg plugin for GStreamer
p   moc-ffmpeg-plugin               - ncurses based console audio player - ffmpe
stephen@flea:~$

```

also note that you can do this
```

sudo aptitude install ffmp

```
Then press TAB, and it will complete the name for you.

---

### Post by hod139 on 2007-01-26
> **Bombdogs said:**
> 
Also I need to install ffmpeg - I've scoured the add/remove programs bit of ubuntu & couldn't find it listed. Again I've ended up with a tarball downloaded from the net, which needs to be compiled, which scares me a lot! Can I use aptitude to install this too?
If you don't like the command line, you can search using synaptic (System-->Administration-->Synaptic package manager) or online at [packages.ubuntu.com]("http://packages.ubuntu.com").  All results for searching for [ffmpeg from pacakge.ubuntu.com]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ffmpeg&searchon=names&subword=1&version=edgy&release=all").

---

