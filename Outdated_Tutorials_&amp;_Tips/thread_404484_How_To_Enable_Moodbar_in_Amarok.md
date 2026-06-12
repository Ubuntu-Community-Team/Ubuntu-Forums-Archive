---
title: "How To: Enable Moodbar in Amarok"
date: 2007-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Ashex on 2007-04-08
**[size=12]This guide is not required for hardy, sudo apt-get install moodbar is all that is needed[/size]**

For the record, I did not write this tutorial, I found it on a broken website [here.](http://69.60.114.106/www.kubuntu-es.org/public_html/?q=aggregator/sources/3)


This requires the installing of compilers and quite a number of libraries, but that&#8217;s what you get for compiling from source. I don&#8217;t know of any packages lying around for it sorry. And I don&#8217;t have the time to make one. You may need to add extra repositories for some steps. All of this is done by the command line but you can use a GUI. CMD line shows that you&#8217;re not too dependant on GUIs tho and it also is dead useful.

Right, first things first, we have to make sure the necessary compilers are installed:

```
sudo apt-get install build-essential
```

Then we have to install the libraries which are needed for the installation:

```
sudo apt-get install fftw3-dev libgstreamer0.10-dev gstreamer0.10-plugins-base
```

Those are the libraries, now for the programs used by moodbar to anylase sound files:

```
sudo apt-get install gstreamer-tools
```

You might want to install &#8220;gstreamer0.10-plugins-ugly&#8221; too. Now we actually install moodbar, first we need to download the source tarball for it, as of writing this the lastest tar is 0.1.2 but there may be another later version here. But anyway we&#8217;ll take that one:

```
wget http://pwsp.net/~qbob/moodbar-0.1.2.tar.gz
```

Now untar:

```
tar -xvvzf moodbar-0.1.2.tar.gz
```

Move into the new directory and compile, it needs to be installed into the same prefix as GStreamer (which should be /usr in Kubuntu).

```
cd moodbar-0.1.2 && ./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10`
```

If there are no errors, it can be made and installed normally:

```
make && sudo make install
```

If that went smoothly, we can now open Amarok and go to &#8220;Settings -> Configure Amarok&#8221; and from &#8220;General&#8220;, select &#8220;Use moods&#8220;. There are three different colour moods to choose from I go with &#8220;Happy as a Rainbow&#8221;, as it&#8217;s the prettiest and most appealing.

**Note**: If you are having trouble with Amarok generating moods, install gstreamer0.10-plugins-ugly

---

### Post by corrin on 2007-04-27
Awesome job Ashex,

Worked perfectly first time.  The only difference I noticed to your tutorial is that gstreamer is now at 0.10 rather than 0.8, but the commands all remain the same.

---

### Post by claypole on 2007-04-27
Works a treat, thanks! :)

---

### Post by wenchmagnet on 2007-04-30
Thanks!

Perfect and to the point... its howtos like these that have made switching to Ubuntu such a breeze... keep them coming. :-)

---

### Post by manishk on 2007-05-09
Found this deb for Feisty...works great!!

[http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/feisty/test/](http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/feisty/test/)

---

### Post by sugarland2k on 2007-06-25
Tried this with Kubuntu 7.04 and Amarok 1.4.6 (KDE 3.5.7) and the coding works prefect!  Wow!  

Ubuntu / Kubuntu is the perfect O/S.  Friends do not let friends run Vista !  

Thanks so much, love the music on last.fm
Billy in Sugar Land 
:popcorn:

---

### Post by briealeida on 2007-07-07
Using Feisty, I only had an issue with this command:
cd moodbar-0.1.2 && ./configure --prefix=`pkg-config --variable=prefix gstreamer-0.10`


Instead I just did these:
cd moodbar-0.1.2
./configure


And now my moods are queued and calculating!

---

### Post by Ashex on 2007-10-29
Hey Guys, just wanted to let you know I have updated the guide for gutsy!

---

### Post by eliasz on 2007-12-14
THanks very much, very helpful :D

---

### Post by money2themax on 2008-01-19
great it worked

EDIT: i can't get it to display <-- got that fixed didn't restart

EDIT II: is there a prog that will make mood files for all my music with out me playing them?

---

### Post by money2themax on 2008-01-19
bump!

---

### Post by Ashex on 2008-04-15
> **money2themax said:**
> great it worked

EDIT: i can't get it to display <-- got that fixed didn't restart

EDIT II: is there a prog that will make mood files for all my music with out me playing them?

You may or may not have noticed, but just load your collection into a blank queue and Amarok should start generating them.


Also, As far as I can tell, this works in Hardy.

---

### Post by tbr281 on 2008-04-21
I tried everything discussed in this thread and nothing works, i got 4 mp3s with moodbars and the rest of my 2000 tunes are blank, can someone explain this to me because i dont know what else to do.

---

### Post by Ashex on 2008-04-23
> **tbr281 said:**
> I tried everything discussed in this thread and nothing works, i got 4 mp3s with moodbars and the rest of my 2000 tunes are blank, can someone explain this to me because i dont know what else to do.

When you queue the tracks it should generate them automatically. Try installing gstreamer0.10-plugins-ugly

---

