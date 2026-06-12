---
title: "HowTo: Installing Jamboree"
date: 2005-05-08
forum: Outdated Tutorials &amp; Tips
---

### Post by wavex on 2005-05-08
**Warning: I am no linux guru. This installs from source. No .deb here. This may not be the best way of installing either. But it worked for me and I wanted to make it easy on others. If you have anything to add like how to add it in the gnome menu or what not. just post and I will try to include it in the top post of this thread.**

Again Warning: **I am a noob at making a howTo. Use this at your own risk.**

First what is Jamboree?
Jamboree is a music player for GNOME.
 
Jamboree manages and plays MP3 and OGG music files through the use of GNOME's multimedia framework GStreamer.

Sceenshot can be viewed here.
[Screenshot](http://www.imendio.com/images/jamboree.png) 

Now for installing.
You need to Download Jamboree first. I suggest downloading to your home directory. Go to the link below and download the latest version of jamboree. Currently it is 0.5 
Grab the bz2
[Jamboree Download](ftp.gnome.org/pub/gnome/sources/jamboree/)

Now that we have it downloaded and hopefully in the home directory. Open a terminal and follow these commands.

Note: you may need to change the version number of jamboree.
cd ~
tar -xvjf jamboree-0.5.tar.bz2  
cd ~/jamboree-0.5

Now if you are using a standard ubuntu installation you will need to get a few files programs first. To get these follow these commands. 

sudo apt-get install libxml-parser-perl
sudo apt-get install libgtk2.0-dev
sudo apt-get install libgnomeui-dev
sudo apt-get install libgstreamer0.8-dev
sudo apt-get install libgdbm-dev

Now that we have these file we can continue with the installation of Jamboree.

make sure you are in ~/jamboree-0.5 directory.
Follow these commands.

sudo ./configure
sudo make 
sudo make install

Jamboree should now be install. Just go to Run application and type in jamboree

---

### Post by bored2k on 2005-05-08
Out of curiosity, why should we give it a try ? I mean, the [screenshot](http://www.imendio.com/images/jamboree.png) is very nice, but it sort of looks like (just a little bit) Rhythmbox. Why is it better ?

---

### Post by wavex on 2005-05-09
I find it more stable than rythmbox. Rythmbox has locked up on me many times. and Jamboree hasn't.

---

### Post by mattgirv on 2005-05-09
[QUOTE=wavex]I find it more stable than rythmbox. Rythmbox has locked up on me many times. and Jamboree hasn't.[/QUOTE]
Hmm, RhythmBox is stable for me. Is this the only advantage Jamboree has?

---

### Post by MrRoboto on 2005-05-09
kinda off-topic but:

why should I use a player (Rhythmbox, Jamboree) that doesn't support equalization?

to me is like playing music with a cheap music tape playesr while I can have access to a super-complete Hi-Fi system (BMP, XMMS).. i like the gui and how manage all my files but I just want to hear good sound not playng with files...

---

### Post by Paulus on 2005-05-09
continuing the "offtopicness", anyone else think that bmp and xmms *sound* better than rhythm and muine players?  Just me?

btw, great that a screenshot was included, gives a good idea what your getting (in this case it deterred me lol)

---

### Post by wavex on 2005-05-09
This is from the FAQ
Q: Why aren't you hacking on Rhythmbox instead? 

A: Jamboree was started as a very simple experiment to see how slow or 
fast the GTK+ treeview really was. Back then, Rhythmbox development 
was pretty much halted. As for today, Jamboree is a nice little hobby 
project with a strong KISS filosophy. It has just about 11000 lines 
of code (according to SLOCCount) and very few features and will 
probably stay that way.

I find it faster then rhythmbox as well. 
Rhythmbox has stability problems for people with huge amount of mp3s because it has trouble with certain id3tags and I believe when it runs upon a wma file too.

Some people have no problems though.

---

### Post by Janux on 2005-10-02
You can also add the next repositories to install Jamboree:

```
deb http://acs.barrapunto.org/debian/jamboree hoary main
deb-src http://acs.barrapunto.org/debian/jamboree hoary main
```

They are provided by Alvaro del Castillo

---

### Post by diegoguillen on 2006-09-03
Hi I know that this forum is for  Hoary but I am interested in Jamboree but I use Dapper and I can't install it my problem is:

checking for gst-inspect... gst-inspect
checking GStreamer element spider... not found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element audioconvert... found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element audioscale... not found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element volume... found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element fakesink... found.
configure: error:
The following GStreamer elements are missing:

     spider audioscale

Make sure you have gstreamer and gstreamer-plugins installed, along with their development packages.

but I have the gstreamer-plugins installed

Jamboree runs on 32 bits or no?

Thanks I hope you can help me

---

### Post by hraposo on 2006-09-04
when I type make It's appears:>         then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.c: Na função &#8216;main&#8217;:
main.c:226: error: &#8216;GNOME_PARAM_POPT_TABLE&#8217; undeclared (first use in this function)
main.c:226: error: (Each undeclared identifier is reported only once
main.c:226: error: for each function it appears in.)
make[2]: ** [main.o] Erro 1
make[2]: Saindo do diretório `/home/helder/Desktop/jamboree-0.5/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/helder/Desktop/jamboree-0.5'
make: ** [all] Erro 2


---

