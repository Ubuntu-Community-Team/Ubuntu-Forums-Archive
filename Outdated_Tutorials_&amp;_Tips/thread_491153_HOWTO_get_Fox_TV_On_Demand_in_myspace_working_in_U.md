---
title: "HOWTO get Fox TV On Demand in myspace working in Ubuntu"
date: 2007-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by forrestcupp on 2007-07-03
So you want to watch the latest 24 on MySpace, but you have to have Windows to do it, huh?

This will take you step by step to get it working in Ubuntu.  I don't have experience with 64-bit, so I don't know if it will work.  I don't know why it wouldn't, though.

**_1. Make sure you have Wine installed_**
If you want the latest version of wine, go [here](http://www.winehq.org/site/download-deb) and follow their directions to get the Wine repository in your sources list and install.

If you don't care about having the latest version, just open a terminal and type:
```
sudo aptitude install wine
```


**_2. Download and install Firefox for Windows_**
Unfortunately, you have to use the Windows version of Firefox for viewing these videos.  It's a pain to switch back and forth between Firefox's, but if you want to watch these videos, this is the only way. 

So go to [Firefox's download site](http://www.mozilla.com/en-US/firefox/all.html) and download the Windows version for whatever language you want to use.

Then install it using Wine with the command below.  Substitute the actual path that you downloaded the file to.  If you installed it to your home directory, substitute your user name with "username."  If the filename that you downloaded happens to be different, substitute the correct filename.  It is important to put the "\" before spaces in a filename.  That tells the CLI that the space isn't the end, it's part of the name.
```
wine /home/username/downloads/Firefox\ Setup\ 2.0.0.4.exe
```
This will run the setup file using the Wine compatibility layer.  Just go through the installation like normal, and it will install the Windows version of Firefox in the Wine directory.


**_3. Run Firefox for Windows and install Fox TV On Demand's video player_**
If you have a standard Wine setup, Wine put a hidden .wine directory in your home folder.  Within that .wine directory is a directory called "drive_c" which is your C: drive.  Within that directory, you will find another directory called "Program Files"  This is where Wine installs your Windows programs.  To see the .wine directory in Nautilus, Konqueror, or Dolphin, you have to enable the showing of hidden files.  So to run Firefox, type the following command remembering to substitute your username with "username."
```
wine /home/username/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```
If you know how to make menu items, you can make a menu entry for this and put that command in.

Now, in Firefox for Windows, go to [http://www.myspace.com/fox](http://www.myspace.com/fox)
Make sure to *not* use this instance of Firefox if it isn't the Windows version.

In the white box it says, "Click here to download plugin."  Click it, and it will install Flash for Windows.

Now click the link to 24, or whatever show you want to watch (as of this posting 24 doesn't have any videos available).  Click the "Watch Now" button.  Firefox probably won't allow the download of the media player, so you'll have to click the edit box on the bar that comes down, and allow this website.  Then click the "click here to continue" link and choose to install the plugin.  Next time you run Firefox for Windows, it will work.  


**_4. Optional - use Beryl to watch fullscreen_**
If you click the button on the website below the video to make the picture bigger, it gives you better resolution, but it isn't anywhere near fullscreen.  You can use the zoom feature in Beryl, Compiz, or Fusion to zoom in to the video to make it more full screen.  Beryl also smooths the screen out so the zoom doesn't look pixelated.   This actually makes the quality of the video slightly better than original.

In Beryl, to zoom, just put the cursor where you want to zoom and press the Super/Windows key while scrolling your mouse wheel.


The shows that aren't currently playing don't have any videos available, so if all you're seeing is a black box and it never plays, that's probably why.  Just try a different show.

I hope this helps.  It worked for me.  If you have any questions, I probably can't help because I already told you everything I know about this.

---

