---
title: "Kylix 3 on Ubuntu 5.04?"
date: 2005-09-07
forum: Programming Talk
---

### Post by ubuntu_kevin on 2005-09-07
Has anyone gotten Kylix 3 to install on ubuntu?  I saw one instance
of someone getting it to work in this forum it but no one ever
explains completely how they did it. Here is the link to the one thread I found...

[http://ubuntuforums.org/showthread.php?t=36084](http://ubuntuforums.org/showthread.php?t=36084)

I'm using the most current version Ubuntu 5.04 "The Hoary Hedgehog".  I
really like this distro and would like to be able to use it with Kylix 3.    :-P 

When I try to install I get the following...

Checking dependencies...
Kernel version >= 2.2.0....OK
Glibc version >= 2.1.2....FAILED
X11 Server....OK
Libjpeg version >= 6.2.0....OK
setup.sh: line 350: [: x11-2: integer expression expected
setup.sh: line 352: [: x11-2: integer expression expected
setup.sh: line 354: [: x11-2: integer expression expected
setup.sh: line 350: [: x11-2: integer expression expected
setup.sh: line 352: [: x11-2: integer expression expected
setup.sh: line 354: [: x11-2: integer expression expected
Libgtk version >= 1.2.0....FAILED

Any help would be greatly appreciated.

Thanks!!

Kevin

---

### Post by ubuntu_kevin on 2005-09-07
I was able to install Kylix with the help of someone on the borland Kylix forum.  I can run Kylix but I cannot seem to run a program from the debugger.  

For those that are interested here is what I did...

1. Opened a root terminal window

2. First, install following packages:

    apt-get install gcc libgtk1.2 libxaw6

3. ln -s /usr/X11R6/lib/libx11.so.6 /usr/X11R6/lib/libx11.so

4.  set default to /CDROM and
 
    sh setup.sh

    and follow installation instructions.

5.  After instalation, you will also need to do the following to get the
menus and toolbars to work (and pretty much everything else in kylix).
In the startdelphi script, add this:

LANG=en_US.ISO8859-1
export LD_ASSUME_KERNEL=2.4.1

6) On the last line of the startdelphi script, add to the beginning of the last line LANG=$KYDEF_LOCALE so the last line looks like...

LANG=$KYDEF_LOCALE /home/josir/kylix3/bin/delphi $*

So now I am able to start Kylix, but I am still not able to run a program from within Kylix.  **When I try to run the debugger, the whole system freezes and I have to reboot.  Does anyone have the fix for this????????**


Thanks,

Kevin

---

### Post by metavoid on 2005-10-01
so it might not work at all. ? 
I have been using knoppix but saw that this linux would install on precision m70 so i had to try it. Im so impressed with its quality and structure.

---

### Post by ubuntu_kevin on 2005-10-01
I still have not found a way to run the debugger in Kylix on Ubuntu.

Kevin

---

### Post by alred on 2005-10-01
kylix tends to have problems when we click on that "Run" menuitem , freezing and hang , in redhat9 , ubuntu , lycoris and maybe other distros , delphi also sometimes gives the same problems in Microsoft Windows but much much less frequent ... 

i usually use the ide to generate a gui by populating the form with necessary gui components with empty events and just compile and build them without "running" them inside the ide , infact i always compile and build from the command line with " dcc -B xxx.dpr " or  " dcc -B xxx.dpk " after saving the project to disk , you can use the ide to set the compile options if you wanted to ...

just want to  mention some other thing , i also managed to compile and build kylix applications in FreeBSD and run them with the help of bsd "linux compat" , all from the command line ...


enjoy ...

---

### Post by metavoid on 2005-10-01
Im using Kylix 3 on knoppix 3.3 with only small issues.
Never hangs or crashes. 

Need to have linux on my laptop and found a review saying Ubuntu would work out of the box. And it did ! 

Im so impressed with its quality and usability.

However, getting Kylix to run is frankly beyond my skills

First 
Link libx11 then
 ln -s /usr/lib/libstdc++.so.6.0.5 /usr/lib/libstdc++-libc6.1-1.so.2

then startbcb gave me

wine:
chdir to /home/private/.borland/wineserver-laptopm70:0.0 : Permission denied

sudo startbcb got rid of this but the splash sceren opens and nothing more happens. Just stays there.
:(

So do you think its possible to get Kylix 3 working?


I think it will break my heart giving up this new found love just because of
a #&¤%#&¤% product from borland, but I Must have kylix.

---

### Post by alred on 2005-10-01
[QUOTE=metavoid]Im using Kylix 3 on knoppix 3.3 with only small issues.
Never hangs or crashes. 
Need to have linux on my laptop and found a review saying Ubuntu would work out of the box. And it did ! 
Im so impressed with its quality and usability.
However, getting Kylix to run is frankly beyond my skills
First 
Link libx11 then
ln -s /usr/lib/libstdc++.so.6.0.5 /usr/lib/libstdc++-libc6.1-1.so.2
then startbcb gave me
wine:
chdir to /home/private/.borland/wineserver-laptopm70:0.0 : Permission denied
sudo startbcb got rid of this but the splash sceren opens and nothing more happens. Just stays there.
:(
So do you think its possible to get Kylix 3 working?
I think it will break my heart giving up this new found love just because of
a #&¤%#&¤% product from borland, but I Must have kylix.[/QUOTE]

i'm able to startup that c++ ide without problem , but cant even compile a project , it report "  Fatal F1003 Project1.bpr 1: Error directive:  " , it also report the same error when i run bc++ from the command line , not sure why is that happening cause i donno much about bc++ ...

do you know what is that error ??

if i can get rid of that compile error , maybe i could just compile the project from the command line after building the gui and events stuffs from the ide ...

---

### Post by metavoid on 2005-10-03
Hmm. I have not seen that error. However, on knoppix distro (debian also)
I had to install a compability glibc to compile anything.

But, it seems like the compiler itself is unhappy about something.

I really wish we could get it to work.

Ubuntu is by far the nicest linux I have ever seen.

It even warned me about low on batteri. :)

---

### Post by alred on 2005-10-03
luckily kylix pascal still works perfectly(without the ide) for me in ubuntu
will look into kylix c++ some other days

have to admit that without a gui kylix debugger could be very troublesome at times
i think kylix is using that an executable in the kylix bin directory for it debugger(i'm using the open kylix edition)
not sure how to call it from the commandline , had tried but empty xterm only ...
now i'm looking or try to learn using gdb with kylix compiled executables , the first time iim using gdb actually,because of this thread  , hope it works and compatible with kylix executables ...


enjoy ...

---

### Post by SkySpeedr on 2006-11-06
Has anyone got the compile/run button to work without locking the machine up? I recently intalled ubuntu and just installed Kylix3 including the startdelphi mods to get the IDE to work. The IDE works just fine but hitting that run button send the CPU to 100% and it's almost impossible to get control of the machine again!

I would really appreciate some help with this one!

---

### Post by jdtiede on 2008-01-21
> **ubuntu_kevin said:**
> I was able to install Kylix with the help of someone on the borland Kylix forum.  I can run Kylix but I cannot seem to run a program from the debugger.  

For those that are interested here is what I did...

1. Opened a root terminal window

2. First, install following packages:

    apt-get install gcc libgtk1.2 libxaw6

3. ln -s /usr/X11R6/lib/libx11.so.6 /usr/X11R6/lib/libx11.so

4.  set default to /CDROM and
 
    sh setup.sh

    and follow installation instructions.

5.  After instalation, you will also need to do the following to get the
menus and toolbars to work (and pretty much everything else in kylix).
In the startdelphi script, add this:

LANG=en_US.ISO8859-1
export LD_ASSUME_KERNEL=2.4.1

6) On the last line of the startdelphi script, add to the beginning of the last line LANG=$KYDEF_LOCALE so the last line looks like...

LANG=$KYDEF_LOCALE /home/josir/kylix3/bin/delphi $*

So now I am able to start Kylix, but I am still not able to run a program from within Kylix.  **When I try to run the debugger, the whole system freezes and I have to reboot.  Does anyone have the fix for this????????**


Thanks,

Kevin

I followed the steps as far as I could, but whei I got to

     sh setup.sh

I still got

    setup.sh: 92: Syntak errer: "(" unexpected

just as I did before. The line in question is the first function call"

     Function FindLibrary()  {

and my C skills are too limited to figure out why Kubuntu 7.04 doesn't like it. Of course that's the end of installation for now. I had Kylix runnuni on RH or Fedora 3-4 years ago but was never able to get it to connect with PostgreSQL.

---

### Post by Kimm on 2008-01-21
You might wana try [Lazarus](http://www.lazarus.freepascal.org/). It is essentially the same thing (VERY similar), but it is OSS and more actively worked on :)

---

