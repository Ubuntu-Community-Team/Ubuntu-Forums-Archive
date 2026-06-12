---
title: "HOWTO: Compile Blender 2.5 SVN"
date: 2009-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by skkeeper on 2009-08-18
Blender is THE free 3D graphics application and the version 2.5 his expected to introduce some outstanding changes to its workflow. For all of you, like me, who dont like to wait months for a stable release, I'll present you a way of downloading the source code and compiling it yourselves.

**This guide was tested in Ubuntu 9.04 Jaunty Jackalope. **

**[SIZE="5"]Installing Dependencies[/SIZE]**
```
sudo apt-get install build-essential scons g++ libx11-dev libgl1-mesa-dev libxi-dev zlib1g-dev libpng12-dev libglu1-mesa-dev libjpeg62-dev libfreetype6-dev libtiff4-dev libopenexr-dev libsdl1.2-dev libopenal-dev python2.6-dev libfftw3-dev libsamplerate0-dev libjack-dev libavformat-dev libxvidcore4-dev libogg-dev libfaac-dev libfaad-dev libx264-dev libmp3lame-dev libvorbis-dev libtheora-dev libswscale-dev libavdevice-dev subversion

```
If youre going to follow this guide, ALL THIS PACKAGES must be installed sucessfully.
**[SIZE="5"]Getting and Compiling Python 3.1.1[/SIZE]**
[LIST]
[*]Get the Source Code tarball here: [http://www.python.org/download/](http://www.python.org/download/)
[*]Extract it and cd into it
[*]Configure before compiling:
```
./configure --prefix=/usr --enable-shared
```
[*]Now compile
```
make
```
[*]Finally lets install
```
sudo make install
```
[/LIST]

**[SIZE="5"]Getting and Compiling Blender 2.5 SVN[/SIZE]**
[LIST]
[*]Create a new folder where you're gonna save the source code
[*]Now let's get our hands on the source code:
```
svn checkout https://svn.blender.org/svnroot/bf-blender/branches/blender2.5
```
[*]Enter the folder you just checked out
```
cd blender
```
[*]Let's define some settings for the compilation
```
nano user-config.py
```
Paste and save the following:
```
WITH_BF_FFMPEG = 'true'
BF_FFMPEG_LIB = 'avformat avcodec avutil xvidcore ogg faac faad x264 mp3lame vorbis theora vorbisenc swscale avdevice'
WITH_BF_OPENAL = 'true'
WITH_BF_GAMEENGINE='true'
WITH_BF_FFTW3 = 'true'
WITH_BF_PLAYER='false'
WITH_BF_VERSE='false'
WITH_BF_YAFRAY='false'
BF_PYTHON_VERSION = '3.1'
WITH_BF_JACK = 'true'
```
[*]Finally lets compile
```
scons
```
[*]Now lets clean
```
scons clean
```
[*]The binaries should be created so lets go to the right folder
```
cd ../install/linux2
```
[*]And finnaly run blender
```
./blender
```
[/LIST]

This is my first tutorial for Ubuntu Forums, so any question or feedback please post here:). Namaste

---

### Post by -Zeus- on 2009-09-03
Great post, but actually, the proper svn for 2.5 is:

```
svn checkout https://svn.blender.org/svnroot/bf-blender/branches/blender2.5
```

The svn you provided is just the current branch, currently 2.49b.

---

### Post by skkeeper on 2009-09-03
> **-Zeus- said:**
> Great post, but actually, the proper svn for 2.5 is:

```
svn checkout https://svn.blender.org/svnroot/bf-blender/branches/blender2.5
```

The svn you provided is just the current branch, currently 2.49b.

Thank you, my mistake. I compiled both versions for personal use and confused the svn url when i did the tutorial.

Sorry for the mistake and I'll correct it in the main post

---

### Post by caddict on 2009-09-07
i am trying to install blender 2.5 on 8.10. first problem is

```
Couldn't find package python2.6-dev

```

i guess it is not in the 8.10 repositories

am i wasting my time to try installing on 8.10?

---

### Post by kevdog on 2009-09-08
try python2.4-dev -- I know that's in the intrepid repositories

---

### Post by caddict on 2009-09-08
thanks kevdog, i may give that a try. i think blender 2.5 needs python 2.6 and 3.1 but really not sure. 

i am building up the strength to do a fresh install of jaunty, so i may just hold off until then.

but i am keen to have a play with the new blender!

---

### Post by caddict on 2009-09-15
thanks skkeeper

i have upgraded to 9.04 and your instructions worked perfectly. 

now to explore blender 2.5!

---

### Post by lubosz on 2009-09-23
great news. the proper blender 2.5 svn is trunk:
[https://svn.blender.org/svnroot/bf-blender/trunk/blender](https://svn.blender.org/svnroot/bf-blender/trunk/blender)

---

### Post by Labello on 2009-10-03
Well it did actually work but performance is soooo bad. about 1FPS. the blender from karmic repos works without such an issue.

---

### Post by caddict on 2009-10-03
also some good builds at

[http://www.graphicall.org/builds/](http://www.graphicall.org/builds/)

---

### Post by mo0nykit on 2009-10-12
Hello!

Before attempting to follow this HOWTO, I asked around at **#python** about upgrading to Python 3.1.1 in Jaunty.
These things I only learned from there:
An important thing to note is that Jaunty uses Python 2.6 as a system default. According to their advice, this command could cause problems ```
sudo make install      # may cause problems
``` So instead of that, it should be ```
sudo make altinstall
```

---

### Post by infinitybrain on 2009-10-13
hey thanks for all skseeker but it doesn't work.its still causing Segmentation fault's .When i try to start it from terminal by writing ./blender from /install/linux2 is says no such file or directory . I've done every thing .is it causing because my displaycard is on board ?.
.i'm 3ds max creator but ive changed my OS to linux and im trying to learn blender . 
So Please Help Me !! my OS is Ubuntu 9.04 jaunty

---

### Post by vinutux on 2009-10-13
> **Labello said:**
> Well it did actually work but performance is soooo bad. about 1FPS. the blender from karmic repos works without such an issue.

Blender from karmic repos is **[COLOR="YellowGreen"]version 2.49a[/COLOR]** v.2.5 still under active development...

---

### Post by caddict on 2009-10-14
i have been downloading "latest blender builds" from graphicall.org - look for builds by Fish, they are compiled on 9.04 - after installing python as above, i just unpack those builds and run blender direct from that directory. no problems.

---

### Post by infinitybrain on 2009-10-14
srry man but its still causing segmentation fault .Guess i've done something wrong back there . i'll try to fix it

---

### Post by caddict on 2009-10-14
just an idea to keep you going. if you are wanting to learn blender, you could run v2.49 (which i think is in the jaunty repos)...until you can get 2.5 working.  2.5 is pretty different but the basic priciples are still the same. also, there are a lot of features in 2.5 which are not working yet, so that could be frustrating.

---

### Post by infinitybrain on 2009-10-14
yeah but i'm still don't know how to work blender 2.49a or 2.49b in Ubuntu 9.04 any suggestions

---

### Post by infinitybrain on 2009-10-14
i found it how stuped i m i skiped this error
see 
[php]
/usr/bin/ld: cannot find -lgettextlib
collect2: ld returned 1 exit status
scons: *** [/home/bagi/build/linux2/bin/blender] Error 1
scons: building terminated because of errors.
[/php]
it caused while scons
and what is -gettextlib

help pls
im bit new in linux

---

### Post by mo0nykit on 2009-10-15
[COLOR=Orange]**[SIZE=4]EDIT: I figured out my mistakes relating to this post. Look here [post #20]("http://ubuntuforums.org/showpost.php?p=8107501&postcount=20")[/SIZE]**[/COLOR]

I have Python 3.1.1 installed in
```
$HOME/python/Python-3.1.1-install
```I copied the *linux2-config.py* to the top of the source tree as *user-config.py*
```
cp ~/blender-source/blender/config/linux2-config.py ~/blender-source/blender/user-config.py
```In my *user-config.py*, I edited **BF_PYTHON=** to match my Python3.1.1 installation. Included here are also the other unedited variables relating to Python
```
# user-config.py
<--cut-->
BF_PYTHON = '$HOME/python/Python-3.1.1-install'
BF_PYTHON_LIBPATH = '${BF_PYTHON}/lib'
BF_PYTHON_VERSION = '3.1'
WITH_BF_STATICPYTHON = False
BF_PYTHON_INC = '${BF_PYTHON}/include/python${BF_PYTHON_VERSION}'
BF_PYTHON_BINARY = '${BF_PYTHON}/bin/python${BF_PYTHON_VERSION}'
BF_PYTHON_LIB = BF_PYTHON+'/lib/python'+BF_PYTHON_VERSION+'/config/libpython'+BF_PYTHON_VERSION+'.a' #'python${BF_PYTHON_VERSION}' 
BF_PYTHON_LINKFLAGS = ['-Xlinker', '-export-dynamic']
BF_PYTHON_LIB_STATIC = '${BF_PYTHON}/lib/libpython${BF_PYTHON_VERSION}.a'
<--cut-->
```However I cannot finish compiling. It complains that it cannot find Python.h. Is there something wrong in my *user-config.py*? Here is the tail end of the output
```
Compiling ==> 'nla.c'
Compiling ==> 'node.c'
source/blender/blenkernel/intern/node.c:31:20: error: Python.h: No such file or directory
scons: *** [/home/kit/blender-source/build/linux2/source/blender/blenkernel/intern/node.o] Error 1
scons: building terminated because of errors.
$
```I tried to locate Python.h and here is the output
```
$ locate -e Python.h
/home/kit/blender-source/blender/source/gameengine/Expressions/KX_Python.h
/home/kit/blender-source/blender/source/gameengine/Expressions/.svn/prop-base/KX_Python.h.svn-base
/home/kit/blender-source/blender/source/gameengine/Expressions/.svn/text-base/KX_Python.h.svn-base
/home/kit/python/Python-3.1.1/Include/Python.h
/usr/include/python2.6/Python.h
$ 
```Is there something that I'm missing?

Thanks in advance!

---

### Post by mo0nykit on 2009-10-15
I figured out my mistakes
> **mo0nykit said:**
> 
```
# user-config.py
<--cut-->
BF_PYTHON = '$HOME/python/Python-3.1.1-install'
BF_PYTHON_LIBPATH = '${BF_PYTHON}/lib'
BF_PYTHON_VERSION = '3.1'
WITH_BF_STATICPYTHON = False
BF_PYTHON_INC = '${BF_PYTHON}/include/python${BF_PYTHON_VERSION}'
BF_PYTHON_BINARY = '${BF_PYTHON}/bin/python${BF_PYTHON_VERSION}'
BF_PYTHON_LIB = BF_PYTHON+'/lib/python'+BF_PYTHON_VERSION+'/config/libpython'+BF_PYTHON_VERSION+'.a' #'python${BF_PYTHON_VERSION}' 
<--cut-->
```
Here is the correct one. Note **BF_PYTHON** and **BF_PYTHON_LIB**
```
# user-config.py
<--cut-->
BF_PYTHON = '/home/kit/python/Python-3.1.1-install'
BF_PYTHON_LIBPATH = '${BF_PYTHON}/lib'
BF_PYTHON_VERSION = '3.1'
WITH_BF_STATICPYTHON = False
BF_PYTHON_INC = '${BF_PYTHON}/include/python${BF_PYTHON_VERSION}'
BF_PYTHON_BINARY = '${BF_PYTHON}/bin/python${BF_PYTHON_VERSION}'
BF_PYTHON_LIB = 'python${BF_PYTHON_VERSION}'  #BF_PYTHON+'/lib/python'+BF_PYTHON_VERSION+'/config/libpython'+BF_PYTHON_VERSION+'.a'
<--cut-->
```

---

### Post by caddict on 2009-10-15
@infinitybrain, you could try downloading 2.49 from this site:

[http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

just unpack to /usr/local/blender and run the binary from that directory.

---

### Post by Dread Knight on 2009-10-16
> **caddict said:**
> @infinitybrain, you could try downloading 2.49 from this site:

[http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

just unpack to /usr/local/blender and run the binary from that directory.

Yo, news flash! Blender.org provides 32 and 64 bit binaries (.deb) for months now.

---

### Post by Labello on 2009-10-17
> **vinutux said:**
> Blender from karmic repos is **[COLOR="YellowGreen"]version 2.49a[/COLOR]** v.2.5 still under active development...

well... thanks for that... i must have misunderstood something while downloading blender 2.5.. -.-*

---

### Post by coCoKNIght on 2009-11-13
In Karmic, Python doesn't need to be compiled. Just install it from the repository:
```
sudo apt-get install python3 python3-dev
```

---

### Post by a2z on 2010-04-25
> **skkeeper said:**
> Blender 
Paste and save the following:
```
WITH_BF_FFMPEG = 'true'
BF_FFMPEG_LIB = 'avformat avcodec avutil xvidcore ogg faac faad x264 mp3lame vorbis theora vorbisenc swscale avdevice'
WITH_BF_OPENAL = 'true'
WITH_BF_GAMEENGINE='true'
WITH_BF_FFTW3 = 'true'
WITH_BF_PLAYER='false'
WITH_BF_VERSE='false'
WITH_BF_YAFRAY='false'
BF_PYTHON_VERSION = '3.1'
WITH_BF_JACK = 'true'
```
 Namaste

I do not have any option I can find to save this code. 
I have went back and checked that I have all python installed and dependencies. 
When running scons, it terminates because of errors.  
[/home/a2z/blenderSource/build/linux2/bin/blender] Error 1
help please.

a2z

---

### Post by nnelsotn55 on 2010-04-25
Good post, thanks for sharing......:lolflag:

________________________
[HDMI Cable](http://www.lindy.co.uk/cables/audio-video/hdmi/)
[USB Cable](http://www.lindy.co.uk/cables/usb/)

---

### Post by freesparks on 2010-05-16
OK,

    I am a little confused and have some questions.  For the sake of staying on top of new trends but still learning where it all came from, I want to install both Blender 2.49b, and Blender 2.5 Alpha 2 on Ubuntu 10.04 Lucid Lynx.  With that said, I believe I have done so successfully and installed both.  For Blender 2.49b, I installed that using the Synaptic Package Manager, and basically runs by me going to the Terminal and, typing:

```
blender
```:)Blender 2.49b then launches successfully confirming that it was compiled using Python 2.6.5.

Now, for Blender 2.5 Alpha 2, which I learned that I downloaded the binary for and not the source,I untarred the binary to it into a > source file in my home directory.  I go to the Terminal and have to type:

```
source ~/.bash_profile
```then I type:

```
echo $PATH
```and then the result of that is as I anticipated:

> home/myhomefolder/source/blender-2.5-alpha2-linux-glibc27-i686:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/gamesAnd finally, I just type:

```
blender
```and then I get:

> found bundled python: /home/myhomefolder/source/blender-2.5-alpha2-linux-glibc27-i686/.blender/python
Blender 2.5 Alpha2 launches, confirming that it compiled with a bundled Python.,,which in actuality is Python3.1.

In detail to do this,
Basically, I created a .bash_profile file which consists of the path to the binary of Blender 2.5 Alpha2 and placed it in my home directory.  And, within that file, I simply typed:

> export PATH="/home/myhomefolder/source/blender-2.5-alpha2-linux-glibc27-i686:${PATH}"
My questions are as follow:
1) Do I have to type:

```
source ~/.bash_profile
echo $PATH
```then

```
blender
```each time I want to launch Blender 2.5 Alpha2 from the Terminal instead of Blender 2.49b?
Or is there a better alternative to running both Blender 2.5 Alpha2 and Blender 2.49b?


Any insights and help on this would be greatly appreciated.  I am confident there is more than one way to get this done.

Best Regards,

freesparks

---

### Post by Jonah Bron on 2010-09-24
Works great!  I installed Blender 2.54 on Ubuntu 10.10 beta without a hitch.  One note, one of the packages is wrong.  It's not libxvidcore4-dev, it's libxvidcore-dev.  That can be confusing because the one without -dev has the 4.

Thanks!

---

### Post by chandni on 2010-12-15
i get errors while compiling blender.
The main problem i face is 'pthread.h not found'

How do i resolve this.

---

