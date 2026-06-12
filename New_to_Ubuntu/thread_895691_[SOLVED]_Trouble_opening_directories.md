---
title: "[SOLVED] Trouble opening directories"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by kenbob in nashville on 2008-08-20
I'm an absolute beginner and I'm trying to install some software from source .tgz archives.  I'm finding that I am unable to navigate to any directory to which I've saved downloaded files from my firefox browser.  If I execute an ls command in my downloads directory I can see the directory I need to open, but I'm getting a "no such directory" error when I try to cd to that directory.  "sudo cd {directory name]" does not seem to work either.  I can change directories to ones which I've created in my file manager within my downloads directory.  The common thread here seems to be directories I've created when downloading files from my browser. I am further perplexed by the fact that the when I list the properties of the directories I can't open, I am listed as the owner.

Thanks for your kind attention and generous help

---

### Post by Titan8990 on 2008-08-20
To kick things off you should ALWAYS first check the Ubuntu repositories for what you are trying to install before you attempt to compile it from source. For example if you are trying to install vlc media player you would first do:


```
jordan@einstein:~$ apt-cache search vlc
bongo - flexible and usable media player for Emacs
dvd95 - DVD9 to DVD5 converter
hdhomerun-config - Configuration utility for Silicon Dust HD HomeRun
libvcdinfo-dev - library to extract information from VideoCD (development files)
libvcdinfo0 - library to extract information from VideoCD
mythbuntu-lirc-generator - Mythbuntu Lirc Configuration Generator
videolan-doc - documentation for the VideoLAN streaming solution
vls - lightweight MPEG and DVD video streaming server
x264 - video encoder for the H.264/MPEG-4 AVC standard
libvlc0 - multimedia player and streamer library
libvlc0-dev - development files for VLC
mozilla-plugin-vlc - multimedia plugin for web browsers based on VLC
vlc - multimedia player and streamer
vlc-nox - multimedia player and streamer (without X support)
vlc-plugin-alsa - dummy transitional package
vlc-plugin-arts - aRts audio output plugin for VLC
vlc-plugin-esd - Esound audio output plugin for VLC
vlc-plugin-ggi - GGI video output plugin for VLC
vlc-plugin-glide - Glide video output plugin for VLC
vlc-plugin-sdl - SDL video and audio output plugin for VLC
vlc-plugin-svgalib - SVGAlib video output plugin for VLC
wxvlc - dummy transitional package
```

That searches the repositories for vlc media player. Here we can see that the package name is simply "vlc". So to install it we do:

sudo apt-get install vlc

Moving on. The issue you are having most likely has to do with absolute and relative paths. 

Whenever you fire up the terminal you start at ~ which means your home directory. If the downloads folder was located in your home directory you could simply do:

cd downloads

This uses the relative path. It is relative to the directory you are in because it is only going one level down.

**remember that in Linux names are CASE SENSITIVE. This means that the name downloads is different from Downloads.**

Now, another way you could get to the do it is:

cd /home/YOURUSERNAME/downloads

This would be an absolute path.


Let me know if this solves your issue.

---

### Post by phidia on 2008-08-20
The error you listed tells me you are either entering the command wrong or are using the wrong command relative to where you are working from.
Here's an example: to move my view to the grub directory I would "cd /boot/grub".
If I was viewing (in) my home directory and tried "cd grub" I will get the error you listed. Hope that helps.

---

### Post by kenbob in nashville on 2008-08-20
Thank you for your advice, but the problem seems a little more nuanced than I've been able to describe.  Specifically I've downloaded a plugin for Gimp to my home/downloads/gimp plugins directory.  I created the "gimp plugins" directory when I did a "save as" from the firefox download manager.  I can "cd downloads" do a listing and see a folder "gimp plugins" where I've created it.  I then want to change my operating directory to the "gimp plugins" directory where I hope to run my "make" commands and create the plugin from the downloaded source.  I am being very careful to copy the directory name as listed by the ls command (which I understand is also using local paths).  What seems a bit more confounding is that I can cd into other directories within my downloads path-- as long as they were not created from within the firefox download manager.  If it is any help, I am using the Gnome terminal and the "gimp plugins" directory is listed in light blue along with the other directories that I am able to enter.  Attempting cd [gimp downloads] from my [downloads] branch indicates that the directory cannot be found.  ls displays the local directory [gimp downloads] just fine.

---

### Post by Titan8990 on 2008-08-20
Typically you don't want to add spaces to a name in Linux.

When you do the syntax is this:

cd gimp\ downloads

if you type gimp and press "tab" (assuming there is nothing else there starting with gimp) it will autocomplete the name for you.

Typically, dark blue = directory while light blue = symbolic link.

---

### Post by kenbob in nashville on 2008-08-20
The spaces within my directory names was the problem.  Thank you for the [TAB] autocomplete tip. That got me in right away!  As I said, I'm a complete newbie and the spaces within directory names will be a (feature) to remember.

---

### Post by Titan8990 on 2008-08-20
Good to hear you got it worked out. Don't forget to mark your thread as solved (thread tools at the top).

---

