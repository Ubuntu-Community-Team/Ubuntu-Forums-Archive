---
title: "HOWTO: Install ZPoC"
date: 2006-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by tonyr1988 on 2006-08-03
ZPoC, a P2P program exclusively for Christian music, doesn't have an equivalent program and doesn't work at all under Wine. Here's how to get it under Ubuntu Dapper Drake (note: my first tutorial, so bear with me):

Go to [http://rullz.lv/zpoc/download/](http://rullz.lv/zpoc/download/)

Download the dclibzpoc-0.3.7.tar.bz2 package

Unzip it to your /tmp folder

Open up a Terminal and type:

> sudo apt-get install libbz2-dev libxml2-dev xlibs-dev qt3-apps-dev
cd /tmp/dclibzpoc-0.3.7
./configure
sudo make
sudo make install

Then download the valknutzpoc-0.3.7.tar.gz package

Unzip it to your /tmp folder as well

Go back to your Terminal and type:

> cd /tmp/valknutzpoc-0.3.7
./configure
sudo make
sudo make install

To get the program to run, use the command:

> valknut-zpoc

It will not automatically be added to your menu, but you can use Alacarte to do that (instructions for that are in other threads).

The interface is different, and it takes some getting used to, but for many people, it's well worth it.

Make sure you bring up the Hub List and Refresh it! (the refresh button is at the bottom-left of the window) to see the rooms.

If you have any problems, I'd be glad to try and help you out!

---

### Post by oddabe19 on 2006-08-06
Thank you so much! I haven't tried it yet, but i'm sure it will work great!

I needed this! :-p

---

### Post by mabulco on 2007-09-15
Maybe I am a little bit late with my reaction... Just installed the newest version of ubuntu (7.04 ?) and when I follow the instructions then I can't get it to work. So could somebody please help me with this one

---

### Post by Callmestupid on 2009-02-05
I too followed the instuctions and did not succeed in installation. I think I may be missing so program as when I got to the make and Make install steps I got

*** No targets specfified and no makefile found. Stop.

*** No rule to make target 'install'. Stop.

If I need something to make this please let me know. Stumped.

---

### Post by myrddinemrys on 2009-02-17
I had a successful install (On two different Kubuntu Intrepid machines) by changing the first line to install a couple different dependencies.  My revised instructions are below.

1.  Unpack the two files into /tmp.
2.  Install dependencies:> sudo aptitude install g++ libbz2-dev libxml2-dev libxcb-xlib0-dev qt3-apps-dev
3.  Compile/install the contents of both files:> cd /tmp/dclibzpoc-0.3.7
./configure
make
sudo make install
and> cd /tmp/valknutzpoc-0.3.7
./configure
make
sudo make install
4.  Run Zpoc with the command:> valknut-zpoc

---

### Post by 32809randy on 2010-12-21
I successfully got the installation done however on program launch I get: Cannot connect to Xserver :0.0

I am using a laptop with a wifi connection.

Thanks.

randy

---

### Post by SpotHT on 2010-12-21
I compiled and installed it, but I cannot run ZPoC.

---

