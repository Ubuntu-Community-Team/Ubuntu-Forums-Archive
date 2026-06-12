---
title: "Bash script for converting video formats"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2014-10-16
I've tried to run this bash script both on Ubuntu Mate and on my Macbook with errors. Could anyone please look at it and help me get it to run? I recently dug out the old xbox and with a friend who does hardware more than I do, we replaced the original 8GB hard drive with a 500GB IDE. The whole kit runs about as well as can be expected. 

Thankfully my expectations are low!  ^_~

What I want to do is have a basic portable party box with music, movies and music videos.  Not really planning to use it for gaming at all but if there's space left I might look into coinops.  The problem is I just went through my music videos and updated to 720p versions from Youtube.  I hate the thought of trying to run down 480p versions when I have nearly 500 music videos already downloaded and organized.  Hence I'm trying to convert them through the magic that is ffmpeg.

I'd really rather do it all on my Macbook (it has a core i5 and 16GB of RAM so it'd be the best really) and to that end I even tried installing Ubuntu Mate to the Macbook's SD Card but that was just seven different installations that didn't boot.  OS X does have its own BASH shell though so if it can be made to run there that'd be awesome too!

Thanks in advance.&#65279;

Link to the script: [http://pastebin.com/aP8hyk5g](http://pastebin.com/aP8hyk5g)

---

### Post by TheFu on 2014-10-17
Perhaps [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) will be helpful?

Looked over the script quickly. Perhaps using HandbrakeCLI would be easier? You can setup profiles using the GUI, then call those with the CLI version.

---

### Post by mc4man on 2014-10-17
Notwithstanding any possible improvements/changes  to encoding parameters - 
# Remove any spaces from filenames
rename s'/ //' *.$inputformat
this seems better, (& actually  works) - 
rename 's/ /_/g' *

Then make sure you have a real ffmpeg installed or change command to avconv (libav-tools package

---

### Post by nerdtron on 2014-10-17
Adding more info,

Does this line even work? (in the for loop) ls *.$inputformat | sed "s/\.$inputformat//"

Also you try running the script like this:
```
bash -x /path/to/script
```

The -x is like a "verbose mode" for running bash script. This will output the lines processed by the script. Let's see how far you script goes.

EDIT: You have a Mac and it has decent specs, why need a bash script if you can use GUI programs. Those are just 500, you can do them by batch.

---

### Post by bornagainpenguin on 2014-10-22
I ended up using Handbrake and following some of the suggestions on the xbmc4xbox forums.  Thanks for the replies.  I dunno why the script didn't work but I got the job done so I'm satisfied.

EDIT: [ATTACH]257444[/ATTACH] I've attached the handbrake preset I used in case anyone from the future comes looking for help in this regard.  You know Google can be.

Hi, future people!  Do you still use Google in your time? ;-)

---

