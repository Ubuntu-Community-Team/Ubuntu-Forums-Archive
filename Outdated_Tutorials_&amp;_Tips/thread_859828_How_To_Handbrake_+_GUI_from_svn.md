---
title: "How To: Handbrake + GUI from svn"
date: 2008-07-14
forum: Outdated Tutorials &amp; Tips
---

### Post by fenian on 2008-07-14
It is No Longer necessary to use the svn version to get Handbrake with a GUI.There is now a Linux .deb (Intrepid) that will install Handbrake+GUI you can get it [here]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb").

---

### Post by yosemite610 on 2008-07-15
These seem to work ok:
> svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake
cd HandBrake
./configure
make
But then:
xxx@xxxxx:~/downloads/HandBrake$ sudo make install
make: *** No rule to make target `install'.  Stop.

I installed all the dependencies you listed... What am I missing?

---

### Post by fenian on 2008-07-15
Sorry I made a mistake you don't run the sudo make install command there.Thank for pointing this out,I've fixed it in the guide.

---

### Post by xXZeroXx on 2008-08-22
Hi, I have a problem, well, I have followed every step of your tutorial, but when I put make, it gives me something like this:
make:*** There was no object specified and there was no makefile found.
What may I do?

---

### Post by Unicast on 2008-08-23
Same as previous poster, but I noticed the following after the ./autogen.sh command:

```
checking for GHB... configure: error: Package requirements (gtk+-2.0 >= 2.8 gio-2.0 hal hal-storage) were not met:

No package 'hal' found
No package 'hal-storage' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GHB_CFLAGS
and GHB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

HAL is already installed according to Synaptic, but I couldn't see a HAL-STORAGE in there. Any ideas?

Thanks in advance.

---

### Post by Unicast on 2008-08-23
Right.....

Installed missing dependencies using:
```
sudo apt-get install libgtk2.0-dev libglib2.0-dev  libhal-storage1 libhal-storage-dev libhal-dev
```

Then redid **./autogen.sh**, followed by **make** and **sudo make install**

I now have Handbrake with its GUI installed! :cool:

---

### Post by xXZeroXx on 2008-08-23
Thanks, it worked, however, my psp doesn't recognize the video, it says unsupported data, Is there anyone that has a good script or program tha isn't extremely slow, and converts video with good quality?:confused:[-o<:cry:

---

### Post by Unicast on 2008-08-23
Which video codec did you use?

FFMPEG, XviD, or x264?

---

### Post by xXZeroXx on 2008-08-23
I just used the psp preset, and the video codec was mpeg-4 I think, however, I found this script:
[http://myweb.cebridge.net/kmc77/article-video-conversion.html](http://myweb.cebridge.net/kmc77/article-video-conversion.html)
And I think it is better for me because I've been converting videos and no error, anyway, thanks for the info:)
EDIT: Why? Why? What did I do wrong? As it seems, all the video converters hate my naruto episodes, Why?
Please someone, someone give me a good and functional script, forget Winff, it's extremely slow, pspvc doesn't converts my naruto episodes, neither does handbrake. Please someone

---

### Post by fenian on 2008-08-23
[QUOTE=Unicast;5647280]Right.....

Installed missing dependencies using:
```
sudo apt-get install libgtk2.0-dev libglib2.0-dev  libhal-storage1 libhal-storage-dev libhal-dev
```


Added to instructions thanks.

---

### Post by radioraheem on 2008-08-27
[COLOR="Red"]UPDATE:[/COLOR]  Disregard the text below.  I realized I had downloaded the yasm deb but hadn't actually installed it :)  Removed everything, installed the deb, reran the install steps from the beginning and everything appears to be working now.

I followed the guide as it exists currently (as of this post) and I receive the following error after running the make before 'sudo make install'

> jallen@optimus:~/HandBrake/gtk$ make
make  all-recursive
make[1]: Entering directory `/home/jallen/HandBrake/gtk'
Making all in src
make[2]: Entering directory `/home/jallen/HandBrake/gtk/src'
make[2]: *** No rule to make target `../../HandBrakeCLI', needed by `HandBrakeCLI'.  Stop.
make[2]: Leaving directory `/home/jallen/HandBrake/gtk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jallen/HandBrake/gtk'
make: *** [all] Error 2
Any idea what's wrong here?  Many thanks in advance for any help.

---

### Post by radioraheem on 2008-11-03
I used these instructions to install handbrake in 8.10 on one of my machines this weekend (worked fine with some slight modifications).  Today I check the thread the instructions have been replaced with a link to a deb file.

That sounds awesome, but the link is giving me a 404 not found error as of when I'm writing this.

Any chance you can restore the original instructions?

Thanks!

---

### Post by 4embrey on 2008-11-03
I looked for a working .deb forever and finally gave up. This is the only no brain solution I found ( cause i have no brain ) 
> 
Howto setup Handbrake including GUI from svn in Ubuntu
 

First get the medibuntu version of ffmpeg (makes more codecs available),but first remove any old ffmpeg,open a terminal and enter.


sudo apt-get remove ffmpeg

then enter.

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
 
-O /etc/apt/sources.list.d/medibuntu.list

then enter.

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

then enter.

sudo apt-get install ffmpeg

Next Install the dependencies for Handbrake and the gtk gui.

sudo apt-get update && sudo apt-get install automake build-essential jam libdvdcss2-dev libtool subversion yasm zlib1g-dev libbz2-dev dvdbackup xmlto texinfo g77 gfortran libgtk2.0-dev nasm doxygen libsdl1.2-dev gfortran-multilib gcc-multilib g++-multilib libesd0-dev libgtk1.2-dev libfftw3-dev electric-fence

Next install and build Handbrake.svn and gtk gui (enter each line seperately,it will take some time to build)...

svn co svn://svn.handbrake.fr/HandBrake/trunk
 
HandBrake

cd HandBrake

./configure

make

sudo make install

cd Handbrake/gtk

./autogen.sh

make

sudo make install

HandBrake should be available from the Applications menu under Sound & Video
AddThis Social Bookmark Button
 

Posted by Admin at 20:20
 
 
 
 

Labels: Handbrake gui ubuntu
 
, Handbrake ubuntu
 
, install Handbrake ubuntu
 
5 comments:

Marty
 
said...

    DOES NOT WORK!!!
    After i try to do: sudo make install
    it gives me an error message.

    no rules to make install
    16 July 2008 14:11
     
     
Kimme Utsi
 
said...

    kimme@ubuntu:~/HandBrake$ make
    ( cd .. ; ./configure ; cd contrib ; cp -f ../config.jam . ; jam )
    System: Linux
    Endian: little

    To build HandBrake, run:
    './jam' on a Mac (or 'make' to try the UB build method),
    'jam' on Linux or Windows.
    ...found 59 target(s)...
    ...updating 1 target(s)...
    LibX264 ./lib/libx264.a
    patching file encoder/slicetype.c
    Hunk #1 succeeded at 370 (offset -9 lines).
    No suitable assembler found. Install 'yasm' to get MMX/SSE optimized code.
    If you really want to compile without asm, configure with --disable-asm.

    cd `dirname ./x264.tar.gz` && CONTRIB=`pwd` &&
    rm -rf x264 && (gzip -dc x264.tar.gz | tar xf - ) &&
    cd x264 && patch -p0 < ../patch-x264-idr.patch &&
    bash ./configure --prefix=$CONTRIB --enable-pthread &&
    make libx264.a && cp libx264.a $CONTRIB/lib/ && cp x264.h $CONTRIB/include/ && strip -S $CONTRIB/lib/libx264.a

    ...failed LibX264 ./lib/libx264.a ...
    ...failed updating 1 target(s)...
    make[1]: *** [.contrib] Error 1
    make: *** [contrib/.contrib] Error 2
    kimme@ubuntu:~/HandBrake$


    Doesn't work here also, this is the output after my first make command before the sudo make install command.
    19 July 2008 21:22
     
     
Richard
 
said...

    The message tells you what's wrong: "no suitable assembler found. Install yasm" But if you check, you already did, so a quick search in the Ubuntu forums results in a post that states the yasm available in the repo is not a good one. Go to [http://www.tortall.net/projects/yasm/wiki/Download](http://www.tortall.net/projects/yasm/wiki/Download)
     
    to grab 0.7.0 or higher (I grabbed 0.7.1).

    Once I did that, HandBrake built just fine. Of course, don't forget to remove the old yasm before installing the newer version.
    24 July 2008 05:56
     
     
Pod
 
said...

    What do I have to do to install the new yasm? I extracted the files, but I still get the "no rules to make install" message. Do I need to enter some kind of command to make yasm install or is extracting the files sufficient? Thanks.
    26 July 2008 19:32
     
     
Gospel
 
said...

    You have to install yasm as well.
    ./configure
    make
    sudo make install

and during the install i found a issue on my system that was solved by 

> sudo apt-get install libgtk2.0-dev libglib2.0-dev libhal-storage1 libhal-storage-dev libhal-dev

fixes the

"for GHB... configure: error: Package requirements (gtk+-2.0 >= 2.8 gio-2.0 hal hal-storage) were not me" error

note: add these to the deps install for apt-get

posted from: ( i hope he doesn't mind )
[http://onlyubuntu.blogspot.com/2008/07/howto-setup-handbrake-including-gui.html](http://onlyubuntu.blogspot.com/2008/07/howto-setup-handbrake-including-gui.html)

---

### Post by radioraheem on 2008-11-04
I managed to pull it out of Google's cached copy:

> 
First get the medibuntu version of ffmpeg (makes more codecs available),but first remove any old ffmpeg,open a terminal and enter...

Quote:
sudo apt-get remove ffmpeg
then enter...

Quote:
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
then enter...

Quote:
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
then enter...

Quote:
sudo apt-get install ffmpeg
Next Install the dependencies for Handbrake and the gtk gui...

Quote:
sudo apt-get install automake build-essential jam libdvdcss2-dev libtool subversion zlib1g-dev libbz2-dev dvdbackup xmlto texinfo g77 gfortran libgtk2.0-dev nasm doxygen libsdl1.2-dev gfortran-multilib gcc-multilib g++-multilib libesd0-dev libgtk1.2-dev libfftw3-dev electric-fence libx264-dev libx264-57 x264 libtheora-dev intltool gettext libgtk2.0-dev libglib2.0-dev libhal-storage1 libhal-storage-dev libhal-dev
You also need yasm however the version in the repos is too old to get a newer version there are 2 methods...
1-(EASIEST)Download a deb for yasm here (install with right click>gdebi Package installer)
2-Download the source and compile it yourself,you can grab the src code here
Next install and build Handbrake.svn and gtk gui (enter each line seperately,it will take some time to build)...

Quote:
svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake
cd HandBrake
./configure
jam
cd $HOME/HandBrake/gtk
./autogen.sh
make
sudo make install
HandBrake should be available from the Applications menu under Sound & Video

UPDATED August 2, 2008-Added missing dependencies,newer HandBrake using later yasm changed some build parameters.
__________________
"They locked up a man who wanted to rule the world. The fools, they locked up the wrong man..."
-Leonard Cohen
Last edited by fenian; August 23rd, 2008 at 04:46 PM. 


---

### Post by 4kfooler on 2008-11-04
deb not found..................

---

### Post by smi402 on 2008-11-09
I am having a problem installing the required libdvdcss2-dev package from the Medibuntu repository. I am running Intrepid 8.10 on a dual core 64-bit machine and seem to have a version conflict for this package.

```
frank@FWS:~$ sudo apt-get update
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_AU                
Ign http://packages.medibuntu.org hardy/non-free Translation-en_AU            
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Hit http://packages.medibuntu.org intrepid/free Translation-en_AU              
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_AU          
Hit http://packages.medibuntu.org hardy Release                                
Hit http://packages.medibuntu.org intrepid Release                                                 
Hit http://packages.medibuntu.org hardy/free Packages                                               
Hit http://packages.medibuntu.org hardy/non-free Packages
....               
(etc)

frank@FWS:~$ sudo apt-get install libdvdcss2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.9-2medibuntu4) but 1.2.10-0.2medibuntu1 is to be installed
E: Broken packages
frank@FWS:~$ 
```

Any assistance would be appreciated.

---

### Post by radioraheem on 2008-11-09
> **smi402 said:**
> I am having a problem installing the required libdvdcss2-dev package from the Medibuntu repository. I am running Intrepid 8.10 on a dual core 64-bit machine and seem to have a version conflict for this package.

```
frank@FWS:~$ sudo apt-get update
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_AU                
Ign http://packages.medibuntu.org hardy/non-free Translation-en_AU            
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Hit http://packages.medibuntu.org intrepid/free Translation-en_AU              
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_AU          
Hit http://packages.medibuntu.org hardy Release                                
Hit http://packages.medibuntu.org intrepid Release                                                 
Hit http://packages.medibuntu.org hardy/free Packages                                               
Hit http://packages.medibuntu.org hardy/non-free Packages
....               
(etc)

frank@FWS:~$ sudo apt-get install libdvdcss2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.9-2medibuntu4) but 1.2.10-0.2medibuntu1 is to be installed
E: Broken packages
frank@FWS:~$ 
```

Any assistance would be appreciated.

Try installing just the regular libdvdcss package.  I got the same error, so I tried removed the -dev from the package name and it still appears to work fine.

---

### Post by smi402 on 2008-11-09
Thanks radioraheem.

I removed reference to the Medibuntu Hardy repository from Synaptic and just kept the Medibuntu Intrepid list, suspecting the conflict may be arising because of differences in the listings for the two releases. This then eliminated reference to libdvdcss2-dev from the packages available for Intrepid. Running apt-get then gave:
```
frank@FWS:~$ sudo apt-get install libdvdcss2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libdvdcss2 libdvdcss-dev
E: Package libdvdcss2-dev has no installation candidate
```

I guess this means that libdvdcss2-dev may have been deprecated and the functions included in libdvdcss2 and libdvdcss-dev. I have installed them so will now proceed to finalise my installation of Handbrake GUI.

---

### Post by smi402 on 2008-11-09
Having compilation problems. The first compile with make proceeded well - I did not use ./configure or jam but went straight to make as instructed by the latest version of the development software. However running the ./autogen.sh shellscript then failed with the message:
```
checking for GHB... configure: error: Package requirements (gtk+-2.0 >= 2.8 gio-2.0 hal hal-storage libgtkhtml-3.14) were not met:

No package 'libgtkhtml-3.14' found
```

The suggested packages for fixing hal and hal-storage are installed:
```
frank@FWS:~/svn/HandBrake/gtk$ sudo apt-get install libgtk2.0-dev libglib2.0-dev libhal-storage1 libhal-storage-dev libhal-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manually installed.
libhal-storage1 is already the newest version.
libhal-storage-dev is already the newest version.
libhal-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Synaptic indicates that libgtkhtml2-0 and libgtkhtml3.14-19 are installed.

Any help would be appreciated.

---

### Post by smi402 on 2008-11-09
Got it to compile. Read through a few more Blog spots and discovered there is a new dependency that needs to be included in the apt-get list.

libgtkhtml3.14-dev

Installing this will also install another whole batch of dependencies (26 on my Intrepid 8.10 amd64). Ran the ./autogen.sh script again and it gave no errors. make followed by sudo make install completed the installation. The Handbrake GUI is then in the Applications -> Sound and Video menu.

The yasm-0.7.1-0ubuntu1 package that is in the Intrepid list also works as is - no need to get special versions of yasm or compile it when installing on Intrepid 8.10 amd64.

Now to see if HandBrake lives up to its reputation for mp4 and x264 encoding. :):)

---

### Post by 081103jk on 2008-11-10
&#36890;&#30693;&#35201;&#27714;&#65292;&#25937;&#28798;&#24080;&#31735;&#12289;&#36807;&#28193;&#23433;&#32622;&#25151;&#21450;&#30456;&#20851;&#21407;&#26448;&#26009;&#29983;&#20135;&#20225;&#19994;&#35201;&#21162;&#21147;&#38477;&#20302;&#25104;&#26412;&#65292;[&#38050;&#31649;](http://www.cnlcxb.com/)&#20445;&#25345;&#20215;&#26684;&#31283;&#23450;&#12290;&#21508;&#30465;(&#33258;&#27835;&#21306;&#12289;&#30452;&#36758;&#24066;)&#20215;&#26684;&#20027;&#31649;&#37096;&#38376;&#21487;&#32467;&#21512;&#26412;&#22320;&#21306;&#23454;&#38469;&#24773;&#20917;&#65292;&#20381;&#25454;&#12298;&#20215;&#26684;&#27861;&#12299;&#26377;&#20851;&#35268;&#23450;&#65292;&#25253;&#32463;&#24403;&#22320;&#25919;&#24220;&#25209;&#20934;&#21518;&#65292;&#23545;&#25937;&#28798;&#24080;&#31735;&#29983;&#20135;&#29992;&#24067;&#12289;&#38050;&#31649;&#20197;&#21450;&#36807;&#28193;&#23433;&#32622;&#25151;&#29983;&#20135;&#29992;&#38050;&#26495;&#12289;&#38050;&#24102;&#12289;[&#38050;&#31649;](http://www.cnlcxb.com/)&#32858;&#33519;&#20057;&#28911;&#31561;&#20027;&#35201;&#21407;&#26448;&#26009;&#65292;&#37319;&#21462;&#20020;&#26102;&#20215;&#26684;&#24178;&#39044;&#25514;&#26045;&#31561;&#21150;&#27861;&#65292;[&#38050;&#31649;](http://www.cnlcxb.com/)&#31283;&#23450;&#20215;&#26684;&#12290;&#36164;&#28304;&#35843;&#20986;&#30465;&#24066;&#35201;&#20999;&#23454;&#25215;&#25285;&#36215;&#31283;&#23450;&#24080;&#31735;&#21644;&#36807;&#28193;&#23433;&#32622;&#25151;&#21407;&#26448;&#26009;&#20215;&#26684;&#30340;&#36131;&#20219;&#65292;&#21327;&#21516;&#36164;&#28304;&#35843;&#20837;&#30465;&#24066;&#20849;&#21516;&#25226;&#25239;&#38663;&#25937;&#28798;&#24080;&#31735;&#21644;&#36807;&#28193;&#23433;&#32622;&#25151;&#29983;&#20135;&#29992;&#21407;&#26448;&#26009;&#20215;&#26684;&#31283;&#23450;&#22312;&#28798;&#21069;&#27700;&#24179;&#12290;&#23545;&#24080;&#31735;&#12289;[&#26080;&#32541;&#38050;&#31649;](http://www.cnlcxb.com/wfgg.htm)&#36807;&#28193;&#23433;&#32622;&#25151;&#31561;&#29289;&#36164;&#30340;&#36816;&#36755;&#65292;&#20813;&#25910;&#36710;&#36742;&#36890;&#34892;&#36153;&#12290;    &#36890;&#30693;&#37096;&#32626;&#21508;&#22320;&#20215;&#26684;&#20027;&#31649;&#37096;&#38376;&#21152;&#24378;&#23545;&#25239;&#38663;&#25937;&#28798;&#24080;&#31735;&#21644;&#36807;&#28193;&#23433;&#32622;&#25151;&#29983;&#20135;&#21450;&#30456;&#20851;&#21407;&#26448;&#26009;&#20215;&#26684;&#30340;&#24033;&#26597;&#65292;&#20005;&#32899;&#26597;&#22788;&#21033;&#29992;&#25937;&#28798;&#20043;&#26426;&#35851;&#21462;&#26292;&#21033;&#30340;&#34892;&#20026;&#65292;[&#38050;&#31649;](http://www.cnlcxb.com/)&#23545;&#20018;&#36890;&#28072;&#20215;&#20197;&#21450;&#19981;&#25191;&#34892;&#20020;&#26102;&#20215;&#26684;&#24178;&#39044;&#25514;&#26045;&#12289;&#25910;&#36153;&#20943;&#20813;&#25919;&#31574;&#31561;&#36829;&#27861;&#34892;&#20026;&#65292;&#35201;&#20381;&#27861;&#20174;&#20005;&#20174;&#37325;&#26597;&#22788;&#65292;&#23545;&#20856;&#22411;&#26696;&#20214;&#35201;&#20104;&#20197;&#20844;&#24320;&#26333;&#20809;&#12290;&#21508;&#32423;&#20215;&#26684;&#20027;&#31649;&#37096;&#38376;&#35201;&#23494;&#20999;&#36319;&#36394;&#25937;&#28798;&#24080;&#31735;&#21644;&#36807;&#28193;&#23433;&#32622;&#25151;&#29983;&#20135;&#20379;&#24212;&#36807;&#31243;&#20215;&#26684;&#25191;&#34892;&#24773;&#20917;&#65292;&#21152;&#24378;&#20027;&#35201;&#21407;&#26448;&#26009;&#20215;&#26684;&#30417;&#27979;&#65292;&#21457;&#29616;&#20215;&#26684;&#24322;&#24120;&#21464;&#21270;&#35201;&#21450;&#26102;&#25253;&#21578;&#12290;(&#22269;&#23478;&#21457;&#23637;&#25913;&#38761;&#22996;&#35759;) [IMG]http://www.cnlcxb.com/images/09144420311.jpg[/IMG]

---

### Post by kevdog on 2008-11-10
I completed this entire tutorial (using the comments of others since the original post has been destroyed), also compiled from svn ffmpeg and yast.  All of the tutorials are poorly written, do not list all the dependencies needed, and I would recommend using checkinstall to install everything if possible. 

Just my two cents.

---

### Post by omelette on 2009-01-06
Hi.  Anyone curently using Handbrake 0.9.3 will know that the installation problems have been solved as there is now a Deb installation package - even a newb like me managed it first time!

However this post concerns what happens next, or doesn't as the case might be - this seems to be extrordinarily buggy!

1: If I try converting a video to any format that accepts FAAC audio and don't alter the bitrate from the default value, it instantly returns "Rip done", having done nothing of course.
2: No format or combination of settings that I have tried, encode sound properly  - FAAC loses sync right from the get-go, with a 1h:35m video eventually ending up almost 10m out of sync with the sound, whereas all LAME mp3 encoding results in everyone sounding like munchkins, irrespective of the sampling frequency or bitrate chosen.
3: Some combinations of settings just cause it to close completely, (crash) without returning an error message.

Finally before starting a conversion, it always displays the same annoying error message "Destination filesystem almost full...", even right after booting Ubuntu - anyone know what this is about?

Is anyone else experiencing any/all of these problems, on what is essentially a 'fresh' Ubuntu installation???

---

### Post by omelette on 2009-02-18
The above problems I encountered with Handbrake seem to all stem from the fact that I was running it from an 'inside-Windoze' installation - having just moved my installation to a real Linux partition via the most excellent LVPM, I am thrilled to discover that Handbrake now works perfectly, with no out-of-sync sound or anything!!!  I'm also very impressed with its speed.  Excellent application! :)

EDIT:  Ahem, I was premature with my praise - there's actually lots still not working properly!  AVI encoding of sound is wonky, which seems to be caused by Handbrake not allowing/dealing with mono sound.  OGM in an instant-rip wiith a zero-byte file, and you must restart Handbrake to encode anything else.  Whereas encoding with the MKV wrapper just results in it crashing!  Unacceptable bugs...

---

### Post by gordwait on 2009-02-22
Aiyayii - It's Feb 2009, here are a few more steps I had to do to get the gui to install - and run.

After following all the threads up to the point of this last missing dependency:
 sudo apt-get install libgtkhtml3.14-dev

I had the following results:
HandBrakeCLI was built when I ran make.
Handbrake GUI was in my menu but would not run. 

So, after all the instructions threaded thru this topic I added the following steps:

cd gtk
./configure
make
sudo make install

Now I'll see if the gui version works. It runs now!


Notes:
Some mention of a Handbrake/autogen.sh script is mentioned here, can't find it. 

I'm converting files for my PS3 so I am using --preset ps3 option on CLI (haven't tried gui yet) but only some of the files actually play. 
The ones that don't play are Sony Digital 8 camcorder files captured via dvgrab. handbrake converts them without any complaint but the ps3 doesn't like them. 

Where would I find the ps3 preset script? Is this something I can hack on to improve?

Good luck, you need to be stubborn to get this thing to compile!

---

