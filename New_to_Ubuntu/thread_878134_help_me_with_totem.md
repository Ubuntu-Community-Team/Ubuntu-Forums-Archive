---
title: "help me with totem"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by nhovan on 2008-08-02
Alright. so i posted here yesterday and still cannot get my dvd player to work on this. i have 8.04 running on a r61 thinkpad. 
i tried running a dvd in totem and was getting the error that libdvdcss2 needed to be loaded because the dvd is encrypted (it is just a standard dvd from netflix). so someone suggested to install VLC. i tried to do that but it wouldnt work either. can anyone help me get my dvd player working?????

i did install the libdvdcss2 stuff and did that stuff from medibuntu

and when i run totem from terminal this is the new error i get:


demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

---

### Post by silkstone on 2008-08-02
Make sure you have all the codecs for totem and gstreamer...

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll w32codecs libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot

That should cover just about everything! Let's know how you get on.

---

### Post by nhovan on 2008-08-02
installed all that and still getting the error: 

demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

---

### Post by eightmillion on 2008-08-02
This is not a 64bit system? If it is, you need to install w64codecs. Otherwise, you probably have to set the region on your DVD drive. Install 'regionset'.
> sudo apt-get install regionset
Then run it with the command '**regionset**'.

---

### Post by silkstone on 2008-08-02
Also try...

sudo /usr/share/doc/libdvdread3/install-css.sh

or if you get an error with that command:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

If that doesn't work, are you getting a problem with all DVDs or just one?

Also, what problems have you had with VLC?

---

### Post by nhovan on 2008-08-02
getting this error now.. always something different.

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:yes
Enter the new region number for your drive [1..8]:ERROR: Illegal region code!

---

### Post by eightmillion on 2008-08-02
What region are you entering? These are the valid options:
```

1 North America (USA and Canada)
2 Europe, Middle East, South Africa and Japan
3 Southeast Asia, Taiwan, Korea
4 Latin America, Australia, New Zealand
5 Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
6 China

```

---

### Post by billgoldberg on 2008-08-02
I installed all my media codecs with one command.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by nhovan on 2008-08-02
alright so i got it to work. but now the picture is alll messed up. i tried it with 2 different dvds too. screenshot is attached

---

### Post by polybius on 2008-08-02
I am having a similar problem.  After following all the instructions for installing packages from medibuntu, I cannot play my DVD.  I am attempting to play it under gxine or else kaffeine, which I believe are the same.  The audio works fine, but the screen is blank (solid black).  I get the error message:
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

This DVD played fine under Ubuntu 7.10, and I haven't changed the region code of my DVD drive or played any other DVDs since upgrading to hardy. So I don't understand why I would have to change my region code now.  If there are only 5 changes allowed, I don't want to change them unnecessarily.

But I'll do it if necessary.  I installed regionset, and when I run it, it says:
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:n

I answered "no" because I don't understand the info it has given me.  When it says "drive plays discs from region(s):, mask=0xff", what does that mean?  It plays discs from all regions?  None?  If none, why did it work under Gutsy?  I looked in the regionset documentation supplied (under /usr/share/doc) and it did not help answer this question.

Any help would be greatly appreciated.

---

### Post by silkstone on 2008-08-03
If you Google the error message it seems that many people are having a similar problem.

It looks as if it can be solved in most cases by selecting ALSA as the default under System > Preferences > Sound - change all the options to ALSA.

Also of course, if you have 64-bit Hardy you need w64codecs.

---

### Post by polybius on 2008-08-03
Thanks, silkstone.  I tried converting all the sound preferences to ASLA, but nothing changes, still get the same error message.

I also googled that error message.  It's happening across distros, Red Hat, Suse etc, but I couldn't see that anyone had solved it.  Some people were saying that DVDs that give this problem are playing fine under LinDVD.  I researched this, too, it's a proprietary DVD player that was nevertheless distributed by Mandriva for a while, but it seems they have dropped it.  There is some discussion about how to get it working under Ubuntu, but I'm not sure I want to go that route.  

I'm also confused about region coding.  I had the impression from reading the wikipedia article that when libdvdcss uses brute force to crack the encryption, then the region coding is irrelevant.  But now everyone is saying that I have to set the region code of my DVD player to play a DVD under gxine+libdvdcss.  This is especially confusing since this particular DVD *did* play fine under gxine+libdvdcss under dapper (I'm now running feisty). 

I'm not sure what region my DVD is coded to, if any.  It was produced in Europe but distributed in the US.  Also, it's not a movie, but a promotional/educational DVD, and I'm not sure there is any advantage for the producers to impose any region coding.  But that's just guessing.  

So I'm wondering how you find out the region code of a particular DVD.  I didn't see anywhere in the output produced by regionset the region of the DVD (the one in the drive when I ran regionset). 

Something else worries me.  The medibuntu web site says that in addition to the libraries and codecs they offer, you also need to use their version of gxine if you want to play DVDs, that is, instead of the version on the regular (unrestricted) Ubuntu repositories. So how do I know if I got the right version of gxine?  Also, the Ubuntu howto says that after installing the medibuntu packages you have to remove medibuntu from the source list to avoid nagging notices for updates.  Do these nagging notices come from some version incompatibility between the unrestricted and the medibuntu repositories?  This worries me because I did do some software updates in response to those messages.  Is it possible I replaced the medibuntu gxine with the unrestricted one, or somehow screwed up the versions of the packages on my machine?

---

