---
title: "How to understand error message regarding dependency trees?"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-01
I was following instructions on ubuntu.com regarding how to uncompress and install tarfiles. I attempted to download a file named 'autogen.sh' which the instructions said MIGHT be necessary to help install a tarball. 

The command I issued, along with the response are listed below:

sudo apt-get install autogen.sh

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package autogen.sh
E: Couldn't find any package by regex 'autogen.sh'

I'm wondering how package lists can be read, and dependency trees built when (so it seems) the file doesn't exist. 

Regardless of whether there's a logical explanation, _is there a way to retrieve a file _from a different source (if the download, per the command above, fails)? 

The website that recommended the download is here: 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Many thanks.

---

### Post by dniMretsaM on 2012-04-01
I don't really know the answer to your first question, but the answer to your second question is that autogen.sh is not a file to be downloaded (from APT or anywhere else). It relies on [FONT=Courier New]autoconf[/FONT] and [FONT=Courier New]automake[FONT=Verdana] (according to the Wiki page you linked to, anyway).[/FONT]
[/FONT]

---

### Post by oldos2er on 2012-04-01
autogen.sh is a script that may or may not be included in a given source code tarball. What program are you trying to compile and where did you download it from (git, svn, etc.)?

---

### Post by jps2012 on 2012-04-02
Thanks for the reply, dni and oldnos. I found a downloadable "autogen.sh" file at [http://buildconf.brlcad.org](http://buildconf.brlcad.org). 

The ReadMe file says, in part, "The autogen.sh script provides automatic build system preparation for projects that use the GNU Autotools build system.  In brief, the script is a drop-in replacement for running 'autoreconf' while detecting and cleanly reporting on a variety of common configuration issues." 

As I try to build a functional Ubuntu system (bring back functions that my upgrade to 11.04 seems to have destroyed), I'm working blindly--mostly just trying to follow advice I find on various websites. 

I'm not sure how autogen.sh works, or why it's necessary (but it's certainly downloadable). It's sitting in my home directory, and I'm going to now try to figure out where it should go, and in what order I should run it, in the series of commands I'll issue while trying to get GIMP to once again (after the upgrade) be able to process RAW files. 

Oldos, you asked what I was trying to accomplish; not only did I lose the ability to process RAW files, but it seems I don't have the necessary files to install the UFRaw plugin into GIMP; I'm trying to get the dependencies, and install the plugin.

---

### Post by jps2012 on 2012-04-02
Just in case anyone needs (or wants) to download autogen.sh and has trouble downloading it from bricad.org, it's also available at [http://sourceforge.net/directory/os:linux/freshness:recently-updated/?q=autogen.sh](http://sourceforge.net/directory/os:linux/freshness:recently-updated/?q=autogen.sh)

---

### Post by oldos2er on 2012-04-02
ufraw is in the repositories, have you tried installing it from there? ```
sudo apt-get update && sudo apt-get install ufraw
```

---

### Post by jps2012 on 2012-04-02
Oldos2er: UFRaw is already installed. But ... are you saying that I might be able to overcome the problem with RAW files crashing UFRaw by reinstalling UFRaw? 

If that's the case, I won't be able to do the reinstallation until I fix a permissions problem (I'm learning a lot, but I think for every two things I 'fix' I break two things). See here: 
[http://ubuntuforums.org/showthread.php?t=1951399](http://ubuntuforums.org/showthread.php?t=1951399)

When I upgraded to 11.04, the GUI changed, of course. I can't figure out where the Update Manager went. If I can eventually fix my permissions issue and get back to working as root, I WILL want to do the updates from the manger. _Could you (or anyone) tell me how to find the UM on the new GUI in 11.04? _

---

### Post by oldos2er on 2012-04-02
I answered in your other thread, you're going to need to reinstall your OS.

Here's some info on Unity (I don't use it myself): [http://askubuntu.com/questions/tagged/unity?sort=faq](http://askubuntu.com/questions/tagged/unity?sort=faq)

---

### Post by jps2012 on 2012-04-03
Thanks for the link for the Unity overview, oldos2er. I'm reinstalling 11.04 now. Looks like it's going to be fine. A week ago or so, I read someone's advice about running commands (not necessarily on this forum), saying "Go ahead, break it! Then break it again!" 

I followed that advice to the letter. It might take me a little longer to break it this time.

---

