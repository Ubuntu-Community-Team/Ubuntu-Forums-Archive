---
title: "PyTube - A small python script for the use with YouTube"
date: 2007-09-24
forum: Programming Talk
---

### Post by marcos.linux on 2007-09-24
Hi, I made a small python script with uses certain programs to downlod, convert,extract audio out of youtube videos. I called it PyTube, If anyone has any tips, any suggestions, and would like to help me out(im a heavy noob) and would like to help me out making a GUI then talk to me :-)

[http://www.bashterritory.com/pytube]("http://www.bashterritory.com/pytube")

---

### Post by pmasiar on 2007-09-25
1)Nice blog :-)
2) Not bad code for a beginner. I didn't try to run it, just read it a little :-)

Couple of comments:
- Licence: GPLv3 is nice, but even better is "or any later version" - make it future-proof
- consider reading PEP8 about coding standards. Also google for "python idioms" and "python best practices". Wiki in my sig **might** have some links too :-)
- Coding standards suggest 4-space tabs, and some readability hints, like space after comma in import, spaces around = and ==, better function names,  download() instead of op1() etc.
- use method chaining, accomplish more in one line
[php]

change_dir=raw_input("change directory? Yes/No: ").lower()
# is in 1 line instead of 2 line as in:
changedirq=raw_input("change directory? Yes/No: ")
changedirq=changedirq.lower()

[/php]
- It is matter of taste, but consider using string interpolation when building complex commands:

[php]
# string interpolation is more readable that string concatenation from expressions
os.system("mplayer -dumpaudio %s -dumpfile %s.mp3 > /dev/null 2>&1" % (finalfile, finalfile) 
os.system("mplayer -dumpaudio " + finalfile + " -dumpfile " + finalfile + ".mp3 > /dev/null 2>&1")

[/php]
- You may want to try EsayGUI to add a GUI
- Wiki in my sig has many more training tasks. I recommend to look ar PythonChallenge too.

---

### Post by LaRoza on 2007-09-25
For the download links, you might want to archive them, so you don't get code in the browser.

---

### Post by marcos.linux on 2007-10-04
I wrote a GUI :-).

[http://www.bashterritory.com/pytube]("http://www.bashterritory.com/pytube")

---

### Post by Anzan on 2007-10-04
Congratulations!

---

### Post by Ramses de Norre on 2007-10-04
DRY! (don't repeat yourself)

example:

Instead of this:
```
if os.path.isfile("/usr/bin/youtube-dl"):
	print "/usr/bin/youtube-dl present :-)"
else:
	os.system("zenity --error --text=Youtube-DL\ was\ not\ found.")
	sys.exit(1)
if os.path.isfile("/usr/bin/mencoder"):
   	print "/usr/bin/mencoder present :-)"
else:
        os.system("zenity --error --text=Mencoder\ was\ not\ found.")            
	sys.exit(1)
if os.path.isfile("/usr/bin/mplayer"):
        print "/usr/bin/mplayer present :-)"
else:
	os.system("zenity --error --text=MPlayer\ was\ not\ found.")               
	sys.exit(1)
if os.path.isfile("/usr/bin/ffmpeg2theora"):
	print "/usr/bin/ffmpeg2theora present :-)"
else:
	os.system("zenity --error --text=FFMPEG2Theora\ was\ not\ found.")
	sys.exit(1)
if os.path.isfile("/usr/bin/oggenc"):
        print "/usr/bin/oggenc present :-)"
else:
        os.system("zenity --error --text=OGGEnc\ was\ not\ found.")
        sys.exit(1)
```

You can write this clean, adaptable, short like this:
```
for i in ["/usr/bin/youtube-dl","/usr/bin/mencoder","/usr/bin/mplayer","/usr/bin/ffmpeg2theora","/usr/bin/oggenc"]:
    if os.path.isfile(i):
        print i+" present :-)"
    else:
        os.system("zenity --error --text="+i+"\ was\ not\ found.")
        sys.exit(1)
```

---

### Post by markp1989 on 2007-10-04
a good idea,  i used PyTube - Version 0.0.3 and it worked well, i will keep looking , to see how well this project develops, congratulations

---

### Post by marcos.linux on 2007-10-04
I just released version 0.0.6 it has several new things :-) and also that code clean up suggested by Ramses de Norre  	 (thanks).

Does anyone knows how to make a deb out of this type of files? I only know how to make a .deb if a ./configure && make is avaible at the top of the source directory.


Thnx

---

### Post by macaholic on 2008-11-07
Hey does anyone have either a deb,rpm just the fodlers for the latest version? The website seems to have expired. I ahve version 0.0.11.4 and it says there is a newer version. Any help would be appreciated.

---

### Post by LaRoza on 2008-11-07
> **macaholic said:**
> Hey does anyone have either a deb,rpm just the fodlers for the latest version? The website seems to have expired. I ahve version 0.0.11.4 and it says there is a newer version. Any help would be appreciated.
I can find no hints of a later version, only: [http://www.getdeb.net/release/3057](http://www.getdeb.net/release/3057)

---

### Post by macaholic on 2008-11-07
Oh, well thanks very much for that, couldn't find a deb anywhere (not sure how I forgot to check getdeb). I was using a i586 rpm package I foudn and had to unarchive and run the script through that (I run 64-bit). Weird why it says there is a new version, guess if one were so inclined one could rummage through the script and see why...

---

### Post by macaholic on 2008-11-07
So the code for the latest version is as follows:```
latestversion = str(urllib.urlopen("http://www.bashterritory.com/pytube/latestrelease").read()).replace("\n","")
			print "Latest version: " + latestversion
			print "Current version: " + self.pytubeversion
			if latestversion > self.pytubeversion:
				self.wTree.get_widget("versionlabel").show()
			else:
				self.wTree.get_widget("versionlabel").hide()
```
For anyone that knows basic prgramming/scripting principles it's pretty self-explanatory, basically the reason it's claiming there is a new version is because the site is not longer there, and is returning a false version value.

---

### Post by wildman4god on 2008-11-08
It would seem the dude that was behind this has fallen of the face of the planet, if this is the case, would anyone else be willing to pick up this project to one fix the bugs and two make it even better, i would do it my self but I have yet to learn how to program, too busy getting my A+, Linux+ and MCSE certifications.

---

