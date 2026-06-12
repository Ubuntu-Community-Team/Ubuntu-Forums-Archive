---
title: "HOWTO: Converting videos for Creative Zen without using a command line"
date: 2009-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Redundant Username on 2009-04-05
[CENTER]-Zen Coder-[/CENTER]
Before you start, make sure you have mecoder installed. If not, install it from your Package Manager, or you can use the termial:
```
sudo apt-get install mencoder
```

1. Download zencoder.exe from the Google Code page ([http://code.google.com/p/zencoder/](http://code.google.com/p/zencoder/)).

2. Right-click on the file and select Properties. On the Permissions tab tick the box for &#8220;Allow executing file as program&#8221;.

3. Right-click on your desktop and select &#8220;Create Launcher&#8230;&#8221;, Browse and select the file as the Command.

4. Double-click the launcher.

5. Click on "Enable audio encoding"

6.Set the video bit-rate at around 550 and set the audio bit-rate at  110. (lower these values if the video or audio becomes out of sync)

7.Drag and drop the files into the program to start the conversion.
-------------------------------------------------------------------
[CENTER]-Iriverter-[/CENTER]
[Click to install Iriverter]("apt:iriverter")


1.Go to options-device-_1_Creative-_1_Zen Vision:M (Don't worry it still works on the Creative Zen)


2.Go to options-video size-_1_ 320x240


3.Click on the folder icon.

4.Go to options-bitrate(or Shift+Ctrl+B) and change to video bitrate to 560kbps, and change to audio bitrate to 112kbps

5. Click Select and chose a video file in the input field.


6. Click Select on the output field to select an output file.

---

### Post by Paqman on 2009-04-28
There are native Linux solutions for this, too. I've been using [Iriverter (click to install)](apt:iriverter).

My only real beef with Iriverter is that it's single-threaded. You can work around that by opening multiple instances of it, but i'd prefer a proper multithreaded app. I've tried Handbrake, but can't get the settings right to encode reliably. Videos tend to play then stop after a few minutes.

---

### Post by Redundant Username on 2009-05-04
I'll add a guide for that too.
Edit: Zen coder is native. You don't need Wine to run it.
Just because it has an .exe extension doesn't mean it is a windows program.

---

