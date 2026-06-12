---
title: "Software/General Recommendations for a new user"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by FCS627 on 2012-02-08
I first started using Ubuntu last year through the Wubi as a replacement for my Windows Vista which I had become fed up with due to how slow it would run.  When I purchased a new laptop over the summer with Windows 7 I remembered how much I had enjoyed my "sneakpeak" while using Wubi and had been going back and forth about actually partitioning Linux instead of running through Windows.

Yesterday I decided to make the jump and did so partitioning a bit under half of my space to Ubuntu 11.10.  My point with the preamble was to explain that while I would consider myself still new to Ubuntu, I have at least played around with it for several months to know some of the basics.

My question is simply: What recommendations would some of the experienced users on here suggest to someone like myself, be it general or software.  So far about all I have done is install Google Chrome, use some of the open office programs for classes, and add my music files to Banshee.  I feel like I am really missing out on the full potential of Ubuntu and feel a bit overwhelmed with so many options out there.

I realize that this is quite a vague question to ask but so far I absolutely love the Ubuntu 11.10 as compared to just using the Wubi, and I am very interested in using it the majority of the time.

---

### Post by sanderd17 on 2012-02-08
if you want to learn about Linux, one of the most useful things is the command line. It's very easy to automate dull tasks.

The best (most to the point) tutorial I know is [http://linuxcommand.org](http://linuxcommand.org). 

Apart from that, when searching for a program, keep the file format in mind. E.g. can a graphical program work with my favourite bitmap or vector format, can I use the output of some program for further processing ...

As in Linux, there are much more tool-chains (instead of big software suites), file formats are kmportant, but generally there are a lot of well-suported file formats.

---

### Post by Adam Jensen on 2012-02-08
You're right; this question is very vague:P. Tell us the types of programs that you like so we can narrow down the search for you.

---

### Post by FCS627 on 2012-02-08
Ha yea I kind of figured it was.

First I guess is music since I spend quite a bit of time listening to it while doing work.

I am using Banshee as of now because it came by default with 11.10 and its worked pretty decently.  Is it the most commonly used media player?  What are some other mp's that are comparable if not better?

Are there any "gadget" (as they are called in Windows), type of applications to add to the desktop/top tray?  I tried playing around with the Broadcast thing at the top of the screen and got it to sync with my Twitter account but not Facebook, but was wondering if its possible to sync with Gmail?  

Those are essentially what I can think of at the top of my head but any suggestions to other useful things would certainly be welcomed.

---

### Post by GraeW on 2012-02-08
I believe you can sync the Broadcast thing with your email as well (anything that allows a POP3 access I'm pretty sure). For desktop "widgets" you can check out *screenlets* or *gdesklets* for little clocks, weather apps, etc. There is also *gkrellm* and *conky* as options, but they (especially conky) need a fair amount of work to get running with the information you want.
 
(I use XFCE as my desktop environment, so am not as familiar with Gnome/Unity as others.. just know some basics)

---

### Post by Adam Jensen on 2012-02-08
For music I would recommend Rhythmbox Music Player. The interface is very similar to iTunes and its easy to use.

---

### Post by ajgreeny on 2012-02-08
I also like rhythmbox.  It was the default music player until 10.10, or 11.04, I think then was replaced by banshee, but is now back as the default, I believe.

However, there are almost too many music apps to give you a simple answer;  try as many as you can find to see what you don't like.  It is very easy to remove the surplus ones that you don't need, they use only space and will not slow down your system simply by being installed like they might in Windows.

---

### Post by FCS627 on 2012-02-08
I appreciate all of the replies from everyone.

I'll give Rhythmbox a try and see how I like it compared to Banshee.  

I'm also trying to read up on the link that sanderd17 posted.  It'll be a bit of a learning curve for me as I'm used to the Windows method of only learning the minimum of what you need to preform tasks instead of trying to understand how they work.

I remember one of the older versions of Ubuntu (which I was running off of the wubi) had in the bottom right of the screen like Windows 7 to go right to the desktop, but it appears that 11.10 has removed that unless I just can't find it.  Is there a way to add it back?

---

### Post by HiImTye on 2012-02-08
some of the programs I use all the time:

GNOME-Shell:
to be fair, this isn't a program, but a desktop environment. a lot of people prefer it to Unity3D for various reasons (mine is performance). it is also a scriptable desktop environment which makes extensions very easy to add/remove

WINE/VirtualBox:
for when you just can't live without that windows program

Mangler:
a ventrilo client for Linux

SMPlayer/XBMC:
video players for Linux.
XBMC is more of a 'media experience' than a player. you would have to use it to understand.
SMPlayer is a nice, good looking GUI on top of MPlayer (which is one of the two most recommended video players for Linux, the other being VLC)

FFMPEG:
for screen capturing, media conversion, media streaming, etc. it is entirely a command line tool, but that is most of the beauty of it (it has a very low footprint)

KTorrent:
a torrent client for Linux. there really isn't another torrent client that is as feature-rich and easy to use, sadly (because if there were I could drop the KDE libs lol)

GIMP:
a pretty full featured image manipulation program/editor. it might not be equal to Photoshop, but it is equal to Photoshop in areas that most people think are important

Synaptic Package Manager/Aptitude:
package managers.
Aptitude is great for command line searching for packages (it also has an ncurses interface, if you wish to use it). all I generally use it for is 'aptitude search <package>' but it saves me plenty of time loading a gui to search for and install one package.
Synaptic is a full featured GUI to manage your packages, not just 'applications' like the Ubuntu Software Center does. it also is a powerful package search utility if you are doing lots of package management at one time.

Configuration Editor/dconf-editor/Ubuntu Tweak:
for finding/using all those hidden options that various things have.

Medibuntu:
Medibuntu is a repository that has packages that are restricted in ways that prevent Ubuntu from shipping them in the default repos. a more feature rich FFMPEG and codecs to play restricted formats are included in Medibuntu

PulseAudio Volume Control (pavucontrol):
a utility for configuring recording and playback streams. useful for redirecting your audio output to a monitor (so you can record your desktop sounds)

that's all that comes to mind right now but Im positive there are much more

---

### Post by Adam Jensen on 2012-02-08
I also recommend the Synaptic Package Manager. It makes downloading and installing programs that are not found in the Ubuntu Software center easy. There will be times when you  come across a program online and are only able to get the source files which you have to compile and install yourself (which can be a pain sometimes). Synaptic does all of that for you. To get synaptic, simply type in "synaptic" in the search bar in the Ubuntu software center. You'll thank me later :D

---

### Post by Adam Jensen on 2012-02-08
Opps! Just realized that Hilm Tye already mentioned Synaptic. My bad.

---

### Post by winh8r on 2012-02-09
This thread:


[http://ubuntuforums.org/showthread.php?t=782307&highlight=favourite]("http://ubuntuforums.org/showthread.php?t=782307&highlight=favourite")


might give you some ideas for what you are looking for.

Just have a play around with different things until you find the one you are most comfortable with.


Hope this helps you.

---

### Post by Paqman on 2012-02-09
Open up Ubuntu Software Centre and have a browse. It's been designed to make it easy to discover all the software that's in the repos.

Things like Synaptic are good tools if you want to get things done with package management, but they're not good for browsing and discovering new stuff. USC shines at that, so get stuck in and see what catches your eye!

---

