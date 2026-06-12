---
title: "Is anyone interested in using my locate frontend?"
date: 2011-02-13
forum: Programming Talk
---

### Post by sashoalm on 2011-02-13
I have created a small front-end for locate for personal use. I mostly started it because none of the programs I tried to use had all the features I wanted:

* Use locate instead of find
* Have a tray icon
* Only search for filenames and be simple [that's why I didn't quite like Google Desktop]

I think catfish came closest but it always defaulted to using 'find' so I had to change it to use locate every time it started which was annoying. 

Well I now use it quite a lot and it's fine with me even if I remain the only user, but in case someone else might want to use it, I'll share it with the community.

The project is hosted on [http://sourceforge.net/projects/qlocate/](http://sourceforge.net/projects/qlocate/)

It's a Qt Creator project so you need Qt Creator to build it.
Here's a screenshot of the main window:
[IMG]http://img51.imageshack.us/img51/8536/screenshotxii.png[/IMG]

To build the project, paste this in the terminal:

sudo updatedb
sudo apt-get install qtcreator subversion
svn co [https://qlocate.svn.sourceforge.net/svnroot/qlocate/trunk](https://qlocate.svn.sourceforge.net/svnroot/qlocate/trunk) qlocate
cd qlocate
qtcreator qlocate.pro

For those who have not used Qt Creator, this will install qtcreator and svn (if you don't have them), download the source, and open the project in qtcreator. It might pop up a dialog asking where to place the build directory, if so, just click the Finish button of the dialog. After you have opened the project from the menu choose Build->Run. The project's icon should appear on the tray. When you click on the tray icon the dialog will appear.

If you have questions about how to build and run it I'll try to help. Any advice or suggestions are welcome. Also if there is more appropriate place to post this please tell me.

---

### Post by gsker on 2011-10-14
Unfortunately your instructions will not install [FONT="Courier New"]qxt[/FONT] which was also required.
For someone who has never compiled, they also have to install [FONT="Courier New"]build-essential[/FONT].

I was unable to use qcreator's interface to change the includes that made qxt work, 
but I edited the [FONT="Courier New"]Makefile[/FONT] 
and appended 
[FONT="Courier New"]-I/usr/include/qxt/QxtGui -I/usr/include/qxt/QxtCore[/FONT] to INCPATH
and appended
[FONT="Courier New"]-lQxtGui -lQxtCore[/FONT] to LIBS

And ran make.

The tool ran fine.

**Feature request:**
I'd rather it had the option to NOT be a tray app, but rather called from a launcher.
But that's just me.

The interface is plenty clean.

---

