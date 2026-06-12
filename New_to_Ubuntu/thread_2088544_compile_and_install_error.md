---
title: "compile and install error"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by nycap on 2012-11-14
trying to compile and install a program and getting error messages i cant figure out:

make[3]: *** [abstract_data_unit.lo] Error 1
make[3]: Leaving directory `/home/matt/op25/blocks/src/lib'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/matt/op25/blocks/src/lib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/matt/op25/blocks/src'
make: *** [install-recursive] Error 1

just started using the ubuntu yesterday.  please excuse if this is easily fixed. thank you very much in advance.

---

### Post by drmrgd on 2012-11-14
I think you're going to need to post more of the output.  There is likely some more error messages above that will tell us what commands actually failed.  The summary error you posted (usually show up at the bottom of the run) aren't enough to debug this.

---

### Post by nycap on 2012-11-14
make[4]: Entering directory `/home/matt/op25/blocks/src/lib'
/bin/bash ../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..  -I/usr/local/include/gnuradio -I/usr/local/include    -I/usr/include/python2.7    -g -O2 -Wall -Woverloaded-virtual -pthread -MT abstract_data_unit.lo -MD -MP -MF .deps/abstract_data_unit.Tpo -c -o abstract_data_unit.lo abstract_data_unit.cc
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -I/usr/local/include/gnuradio -I/usr/local/include -I/usr/include/python2.7 -g -O2 -Wall -Woverloaded-virtual -pthread -MT abstract_data_unit.lo -MD -MP -MF .deps/abstract_data_unit.Tpo -c abstract_data_unit.cc  -fPIC -DPIC -o .libs/abstract_data_unit.o
In file included from abstract_data_unit.cc:24:0:
./abstract_data_unit.h:32:27: fatal error: itpp/base/vec.h: No such file or directory
compilation terminated.
make[4]: *** [abstract_data_unit.lo] Error 1
make[4]: Leaving directory `/home/matt/op25/blocks/src/lib'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/matt/op25/blocks/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matt/op25/blocks/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matt/op25/blocks'
make: *** [all] Error 2

these lines come up two times i think.  thanks a bunch.

---

### Post by nycap on 2012-11-14
here is more lines from a what is, i think, a failed command within main compile command:

matt@matt-Inspiron-1525:~/op25/blocks$ make check
Making check in config
make[1]: Entering directory `/home/matt/op25/blocks/config'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/matt/op25/blocks/config'
Making check in src
make[1]: Entering directory `/home/matt/op25/blocks/src'
Making check in lib
make[2]: Entering directory `/home/matt/op25/blocks/src/lib'
make  check-am
make[3]: Entering directory `/home/matt/op25/blocks/src/lib'
/bin/bash ../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../..  -I/usr/local/include/gnuradio -I/usr/local/include    -I/usr/include/python2.7    -g -O2 -Wall -Woverloaded-virtual -pthread -MT abstract_data_unit.lo -MD -MP -MF .deps/abstract_data_unit.Tpo -c -o abstract_data_unit.lo abstract_data_unit.cc
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../.. -I/usr/local/include/gnuradio -I/usr/local/include -I/usr/include/python2.7 -g -O2 -Wall -Woverloaded-virtual -pthread -MT abstract_data_unit.lo -MD -MP -MF .deps/abstract_data_unit.Tpo -c abstract_data_unit.cc  -fPIC -DPIC -o .libs/abstract_data_unit.o
In file included from abstract_data_unit.cc:24:0:
./abstract_data_unit.h:32:27: fatal error: itpp/base/vec.h: No such file or directory
compilation terminated.
make[3]: *** [abstract_data_unit.lo] Error 1
make[3]: Leaving directory `/home/matt/op25/blocks/src/lib'
make[2]: *** [check] Error 2
make[2]: Leaving directory `/home/matt/op25/blocks/src/lib'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/matt/op25/blocks/src'
make: *** [check-recursive] Error 1

thanks so much for help.

---

### Post by drmrgd on 2012-11-14
Based on that (still seems incomplete as you're just showing the 4 iteration (not sure if that's the right word) of make within the build), it looks like you might be missing some dependencies.  Have a look at this documentation and make sure you've installed all the requisite packages (in this case 'libitpp-dev'?):

[http://op25.osmocom.org/wiki/wiki/BuildInstructionsPage](http://op25.osmocom.org/wiki/wiki/BuildInstructionsPage)

Once you've installed all of them, try building again.

---

### Post by nycap on 2012-11-14
> **drmrgd said:**
> Based on that (still seems incomplete as you're just showing the 4 iteration (not sure if that's the right word) of make within the build), it looks like you might be missing some dependencies.  Have a look at this documentation and make sure you've installed all the requisite packages (in this case 'libitpp-dev'?):

[http://op25.osmocom.org/wiki/wiki/BuildInstructionsPage](http://op25.osmocom.org/wiki/wiki/BuildInstructionsPage)

Once you've installed all of them, try building again.


THANK YOU SO MUCH!  i installed the above mentioned package and it installed without error.  yes on build page the one source for the perquisites (i++) is down.  

should i be seeing an executable in the op25/blocks dir or?  i tried to run from alt F2 but it didnt work.  Thanks again.

---

### Post by drmrgd on 2012-11-14
To be honest, I don't know that package at all, or how it works.  If there is an executable in there that needs to be run, the most likely reason you can't find it with alt-F2 (or using the Dash) is because the path /home/matt/op25/ is not part of your system $PATH variable, which is where the system will look for executable programs by default.

So, you have a couple options:

1.  You can launch the program from the terminal every time you want to use it.  I don't know what the executable is called.  But, assuming it's just called 'op25', you would navigate to the folder where the program is and type:

```
./op25
```

That's assuming a pretty simple case, and again, without knowing how the program exactly works, it's hard to know if that will work correctly.

2.  You can add the executable file to your $PATH.  $PATH usually consists of /bin, /usr/bin, /usr/local/bin, etc.  (you can find out all of the locations by running:

```
echo $PATH
```

In order to get the program to be part of the $PATH (and therefore executable from anywhere), you can make a symbolic link to the executable program in a location in your path.  This is sort of like creating a 'shortcut' in windows.  Most people use /usr/local/bin for this (depending on how they prefer to configure their system and what kind of system it is...very broad statement there!).  So, again, assuming the executable is called op25, you can create a symbolic link like this:

```
sudo ln -s /home/matt/op25/op25 /usr/local/bin/op25
```

You might have to change that command a bit to match your conditions (i.e. if op25 is not where I think it is).  

I think that should get you set up.  Let us know how that goes.

---

### Post by nycap on 2012-11-14
i put all the op25 files (which consists of 7 folders) in a folder named i named op25.  i can not find an executable although i might not know what to look for or where to look.  using Alt F2 there is an icon (icon is gears or cogs) named op25 but when i click on it it doesnt do anything. thanks

---

### Post by drmrgd on 2012-11-14
So, I had a quick second glance at that wiki page I sent you, and noticed the following at the bottom of the Beginners Build section:

[http://op25.osmocom.org/wiki/wiki/BeginnersBuildDeprecated](http://op25.osmocom.org/wiki/wiki/BeginnersBuildDeprecated)

> 7.  You should be done ready to run the app. Plug your scanner into the mic input. Launch the sound mixer (under System -> Preferences -> Sound) and make sure you can see the signal coming in from the discriminator tap of the scanner.
```
cd ~/src/op25/python
./audio_p25_rx.py -a
```
This last bit is up to you. Poke around the interface, read the rest of the wiki and mailing list, and, well, good luck!

So, it looks like you need to execute a python script within the package.  Take a moment to read through the wiki page as it seems  like a really nice guide on how to use the package.  I think you'll get more mileage out of that page than me at this point as I don't know much about that software at all ;)

---

### Post by nycap on 2012-11-14
thanks.  i ran the command on the file although i had to change the file path because i didnt install using the instructions from this page (somehow i managed not to find this page).  do you think i should reinstall using the commands given on the beginnersbuild page?  oh and my terminal has not returned to the command prompt. what does this mean and how to get the command promt back?  

please excuse if i am annoying im learning as i go here. Thanks so much.

---

### Post by drmrgd on 2012-11-15
> **nycap said:**
> thanks.  i ran the command on the file although i had to change the file path because i didnt install using the instructions from this page (somehow i managed not to find this page).  do you think i should reinstall using the commands given on the beginnersbuild page?  oh and my terminal has not returned to the command prompt. what does this mean and how to get the command promt back?  

please excuse if i am annoying im learning as i go here. Thanks so much.

Absolutely no annoyance at all!  We all start from somewhere and this is the best way to learn in my opinion!

I don't know much about this kind of thing.  My interpretation of the build instructions suggest that you should (once you've plugged in a mic and scanner and whatnot) be hearing some kind of broadcast.  I guess if you're not hearing anything then there's still a configuration that needs to be made.  Your terminal prompt has probably not returned because (although you can't hear anything I gather) the program's still happily chugging along. 

I will kill the program for now (I think "Ctrl + c" should do it), and then as they mention in that doc, I would "Launch the sound mixer (under System -> Preferences -> Sound) and make sure you can see the signal coming in from the discriminator tap of the scanner."  

If you're still not getting anything, you might have to contact someone on the mailing list to get more troubleshooting help. Since no one else has posted to this thread, I'm guessing this is one of those very specific and niche sort of applications that not a lot know about or how to troubleshoot. 

This looks quite complex, but quite cool.  Wish I had more time to play around with something like this.  Could be fun :)

---

### Post by nycap on 2012-11-19
when trying to compile some code i get this error:

> make[3]: Entering directory `/home/matt/gr-fsk4/src/lib'
/usr/bin/swig -c++ -fvirtual -python -modern -I/usr/local/include/gnuradio/swig -I/usr/local/include/gnuradio   -module fsk4 -o fsk4.cc ../../src/lib/fsk4.i    
/usr/local/include/gnuradio/swig/gnuradio.i:31: Error: Unable to find 'gruel_common.i'

i guess there is a patch for this. instructions from a site say:

> Apply the [patch]("http://svn.spench.net/main/gr-baz/patch/op25/r307.diff") in the root of your source directory: 
          patch -p0 < r307.diffim sorry but i am learning as i go and i dont even know what "your source directory" is or how to apply the patch (which is a huge page of xml code i think).   and then what run that command?  im lost here.

---

### Post by alphacrucis2 on 2012-11-19
> **nycap said:**
> when trying to compile some code i get this error:



i guess there is a patch for this. instructions from a site say:

im sorry but i am learning as i go and i dont even know what "your source directory" is or how to apply the patch (which is a huge page of xml code i think).   and then what run that command?  im lost here.

The .diff file contains the changes to be applied to the source. The patch program reads the diff file and makes the corresponding changes to the source. The source directory is where ever you put the source files you are wanting to compile. So cd into that directory. Download the text from your link and store it in the same directory as a file called r307.diff and run the specified patch command.

---

### Post by nycap on 2012-11-26
trying to apply patch to "version 306 of the SVN source" .   what is SVN?   how do i find the source directory?

Thanks in advance.

---

### Post by nycap on 2012-11-26
i run command in the appropriate directory
```
./bootstrap && ./configure && make make check sudo make install
```and i get this error

```
bash: ./bootstrap: No such file or directory
```

totally stuck.  thanks in advance.

---

### Post by azmyth on 2012-11-26
chmod +x bootstrap

or

you are in the wrong directory when you run the command

ls | grep bootstrap

will tell you.

---

### Post by squakie on 2012-11-27
What are you trying to install and where did you get it?

---

### Post by gnusci on 2012-11-27
Maybe wrong order,

$ ./configure && make make check sudo make install && ./bootstrap

---

### Post by monkeybrain2012 on 2012-11-27
Which program is this and where do you get the instructions? Maybe there is no bootstrap script?

---

### Post by nycap on 2012-11-27
the program is OP25, it is a module in another program, gnuradio.  OP25 is a module that encapsulates another program, gr-4fsk.  I have been trying for like two weeks to get these modules installed into gnuradio with no luck.  just have been running into error after error. fix one and another pops up.  

my main sources of build and install directions have been:  [http://wiki.spench.net/wiki/OP25;](http://wiki.spench.net/wiki/OP25;)  [http://op25.osmocom.org/wiki/wiki/BeginnersBuildDeprecated;](http://op25.osmocom.org/wiki/wiki/BeginnersBuildDeprecated;)  and [http://op25.osmocom.org/wiki/wiki/BuildInstructionsPage](http://op25.osmocom.org/wiki/wiki/BuildInstructionsPage).

i have at some points seemingly installed gr-fsk4 and op25 couple times without error but they are not showing up in the gnuradio program. so now i made some changes and OP25 wont even compile.

---

### Post by audiomick on 2012-11-27
> **nycap said:**
> ... in another program, gnuradio. ...

Where did you get gnuradio from? On this 10.04 install, that is in the software centre. It is a meta package that pulls in "the complete gnuradio and USRP software collection". Are those modules not in there?

---

### Post by nycap on 2012-11-27
i downloaded the gnu radio from the gnuradio site.  my understanding was that i needed to build it from source in order to be able do what i am trying to do.  the gnuradio site gives the commands for terminal to download and compile and install gnu radio.  but no the latest version of gnu radio 3.6.0 (i think i have) does not come with these blocks, the ones i need, (fsk4, op25, wireshark). 

thanks.

---

### Post by nycap on 2012-11-27
i run these commands to install the gr-fsk4

```
wget http://radiorausch.googlepages.com/gr-fsk4-22Apr08.tar.gz -O gr-fsk4-22Apr08.tar.gz tar zxvf gr-fsk4-22Apr08.tar.gz cd gr-fsk4 ./bootstrap ./configure make -j 4 CC=gcc-4.1 CXX=g++-4.1 sudo make install
```

and i get these errors

```
make[4]: *** [fsk4_apco25_f.lo] Error 1
make[4]: *** Waiting for unfinished jobs....
../../libtool: line 1128: g++-4.1: command not found
make[4]: *** [fsk4_generic_f.lo] Error 1
libtool: compile:  g++-4.1 -DHAVE_CONFIG_H -I. -I../.. -I/usr/local/include/gnuradio -I/usr/local/include -I/usr/include/python2.7 -g -O2 -Wall -Woverloaded-virtual -pthread -MT fsk4_rdlap_f.lo -MD -MP -MF .deps/fsk4_rdlap_f.Tpo -c fsk4_rdlap_f.cc  -fPIC -DPIC -o .libs/fsk4_rdlap_f.o
../../libtool: line 1128: g++-4.1: command not found

```

any idea about how to fix this error?  thanks in advance.

---

### Post by monkeybrain2012 on 2012-11-27
Did you install libtool?

If not, then run 

sudo apt-get install libtool

---

### Post by nycap on 2012-11-27
here is the commands i run to compile and install gr-fsk4:

```
wget http://radiorausch.googlepages.com/gr-fsk4-22Apr08.tar.gz -O gr-fsk4-22Apr08.tar.gz 
tar zxvf gr-fsk4-22Apr08.tar.gz
cd gr-fsk4
./bootstrap
./configure
make -j 4 CC=gcc-4.1 CXX=g++-4.1 
sudo make install
```
here is the error i get:

```

libtool: line 1128: g++-4.1: command not found
```

i do have latest g++ installed.  Thanks in advance for any ideas.

---

### Post by nycap on 2012-11-27
i changed the command to g++4.4 and it compiled and installed without error. however the program module is not found where it is supposed to be

---

### Post by mc4man on 2012-11-27
> Did you install ..
The Op is running 2 threads on basically the same thing, none to useful for those attempting to help...
[http://ubuntuforums.org/showthread.php?t=2088857](http://ubuntuforums.org/showthread.php?t=2088857)

---

### Post by oldos2er on 2012-11-27
Threads merged. Please don't start more than one thread for the same issue, it dilutes community effort.

---

### Post by nycap on 2012-11-27
i got this to compile by changing the command from
```
make -j 4 CC=gcc-4.1 CXX=g++-4.1 
```

to
```
make -j 4 CC=gcc-4.1 CXX=g++-4.4
```

---

### Post by nycap on 2012-11-27
> **oldos2er said:**
> Threads merged. Please don't start more than one thread for the same issue, it dilutes community effort.

this thread was about installing gr-fsk4.  the other thread was an error from installing a different program.

---

### Post by lisati on 2012-11-27
Threads merged

Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

If you think that your thread is in the wrong place, you are welcome to ask the forum staff to move the thread using the "Report Abuse" button.

---

### Post by nycap on 2012-11-27
> **mc4man said:**
> The Op is running 2 threads on basically the same thing, none to useful for those attempting to help...
[http://ubuntuforums.org/showthread.php?t=2088857](http://ubuntuforums.org/showthread.php?t=2088857)

these are two separate issues im talking about here.  and thread in the above link more or less solved.

---

### Post by nycap on 2012-11-27
after running sudo make install in terminal install gets stuck with this:

```
usrp2.cc:73:23: error: expected type-specifier
usrp2.cc:73:23: error: expected &#8216;)&#8217;
usrp2.cc:74:30: error: no matching function for call to &#8216;usrp2::usrp_table_entry::usrp_table_entry(std::string&, usrp2::usrp2::sptr&)&#8217;
usrp2.cc:74:30: note: candidates are:
usrp2.cc:43:5: note: usrp2::usrp_table_entry::usrp_table_entry(const string&, int)
usrp2.cc:43:5: note:   no known conversion for argument 2 from &#8216;usrp2::usrp2::sptr {aka boost::shared_ptr<usrp2::usrp2>}&#8217; to &#8216;int&#8217;
usrp2.cc:38:10: note: usrp2::usrp_table_entry::usrp_table_entry(const usrp2::usrp_table_entry&)
usrp2.cc:38:10: note:   candidate expects 1 argument, 2 provided
In file included from /usr/include/boost/shared_ptr.hpp:17:0,
                 from /home/matt/src/gnuradio-3.2.2/usrp2/host/include/usrp2/usrp2.h:22,
                 from usrp2.cc:23:
/usr/include/boost/smart_ptr/shared_ptr.hpp: In instantiation of &#8216;boost::shared_ptr<T>::shared_ptr(Y*) [with Y = int; T = usrp2::usrp2]&#8217;:
usrp2.cc:73:56:   required from here
/usr/include/boost/smart_ptr/shared_ptr.hpp:183:50: error: cannot convert &#8216;int*&#8217; to &#8216;usrp2::usrp2*&#8217; in initialization
make[3]: *** [usrp2.lo] Error 1
make[3]: Leaving directory `/home/matt/src/gnuradio-3.2.2/usrp2/host/lib'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/matt/src/gnuradio-3.2.2/usrp2/host'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/matt/src/gnuradio-3.2.2/usrp2'
make: *** [install-recursive] Error 1
```
source seemed to configure and compile ok but wont install.  any help will be much appreciated.

---

### Post by steeldriver on 2012-11-27
I've had a play with this and it seems to be a known bug

[https://bugs.launchpad.net/ubuntu/+source/gnuradio/+bug/687464](https://bugs.launchpad.net/ubuntu/+source/gnuradio/+bug/687464)

A patch is provided in the link (look at the 2nd reply) and I did manage to get it to build after that (using plain 'make' with no special arguments - not sure why you need those) - or you may want to try a newer tarball, or installing from the git repo instead

Good luck

---

### Post by nycap on 2012-11-27
output from terminal:

```
usrp2.cc:73:23: error: expected type-specifier
usrp2.cc:73:23: error: expected ‘)’
usrp2.cc:74:30: error: no matching function for call to ‘usrp2::usrp_table_entry
```

i recognize that "usrp2.cc" is the file in which the code needs to be  debugged (please tell if i am wrong).  but i don't know what the numbers (eg. 73:23) after the file  name mean.   can it lead me to exactly where the type-specifier is missing?

---

### Post by steeldriver on 2012-11-27
They are the line and column numbers

Rather than trying to fix it yourself, it would be easier to download the gnuradio_gcc45_fix.patch file in the link I posted, save it in your working directory, then do

```
patch ./usrp2/host/lib/usrp2.cc < gnuradio_gcc45_fix.patch
```

---

### Post by nycap on 2012-11-27
> **steeldriver said:**
> I've had a play with this and it seems to be a known bug

[https://bugs.launchpad.net/ubuntu/+source/gnuradio/+bug/687464](https://bugs.launchpad.net/ubuntu/+source/gnuradio/+bug/687464)

A patch is provided in the link (look at the 2nd reply) and I did manage to get it to build after that (using plain 'make' with no special arguments - not sure why you need those) - or you may want to try a newer tarball, or installing from the git repo instead

Good luck

thank you very much.   i found this guys posts when i was searching for help but i didnt find this exact page.

---

### Post by nycap on 2012-11-27
> **steeldriver said:**
> They are the line and column numbers

Rather than trying to fix it yourself, it would be easier to download the gnuradio_gcc45_fix.patch file in the link I posted, save it in your working directory, then do

```
patch ./usrp2/host/lib/usrp2.cc < gnuradio_gcc45_fix.patch
```

i copied the code from that link and put in a file, named it what you said, put it in the appropriate directory.  i cd into there and run the command here is the output in terminal:

```
matt@matt-Inspiron-1525:~/src/gnuradio-3.2.2/usrp2/host/lib$ patch ./usrp2/host/lib/usrp2.cc < gnuradio_gcc45_fix.patch
patching file ./usrp2/host/lib/usrp2.cc
Hunk #1 FAILED at 38.
Hunk #2 FAILED at 70.
2 out of 2 hunks FAILED -- saving rejects to file ./usrp2/host/lib/usrp2.cc.rej
```

what did i do wrong here?  thanks a bunch.

---

### Post by steeldriver on 2012-11-27
Actually I intended you to put it in / run it from the same directory you are running the 'make' command in i.e. ~/src/gnuradio-3.2.2 (hence the relative path)

However you should be able to run it from where you are, simply as

```
patch usrp2.cc < gnuradio_gcc45_fix.patch
```

---

### Post by nycap on 2012-11-27
> **steeldriver said:**
> Actually I intended you to put it in / run it from the same directory you are running the 'make' command in i.e. ~/src/gnuradio-3.2.2 (hence the relative path)

However you should be able to run it from where you are, simply as

```
patch usrp2.cc < gnuradio_gcc45_fix.patch
```


thanks alot. the sudo make install worked without error.   i was also able to run the install command for gr-fsk4 without error.  but installing the op25 is giving me the following:

```
op25_imbe_vocoder.cc:266:193: error: 'sprintf' was not declared in this scope
op25_imbe_vocoder.cc:267:45: error: 'strlen' was not declared in this scope
op25_imbe_vocoder.cc:267:46: error: 'memcpy' was not declared in this scope
op25_imbe_vocoder.cc: In member function 'void op25_imbe_vocoder::init_sock(char*, int)':
op25_imbe_vocoder.cc:320:61: error: 'memset' was not declared in this scope
op25_imbe_vocoder.cc:323:25: error: 'stderr' was not declared in this scope
op25_imbe_vocoder.cc:323:73: error: 'fprintf' was not declared in this scope
op25_imbe_vocoder.cc:328:25: error: 'stderr' was not declared in this scope
op25_imbe_vocoder.cc:328:70: error: 'fprintf' was not declared in this scope
```im looking for a patch for this but not having luck.  thank you very much.

---

### Post by nycap on 2012-11-27
:i added some headers in some files and finally got it all to compile and install.  now i am trying to run using:

```
cd ~/src/op25/python
./audio_p25_rx.py -a
```and getting:

```
Traceback (most recent call last):
  File "./audio_p25_rx.py", line 34, in <module>
    from gnuradio import audio, eng_notation, fsk4, gr, gru, op25
  File "/usr/local/lib/python2.7/dist-packages/gnuradio/fsk4.py", line 26, in <module>
    _fsk4 = swig_import_helper()
  File "/usr/local/lib/python2.7/dist-packages/gnuradio/fsk4.py", line 22, in swig_import_helper
    _mod = imp.load_module('_fsk4', fp, pathname, description)
ImportError: libgnuradio-core.so.0: cannot open shared object file: No such file or directory
```

have no idea what this means or how to start this program.  i had a previus biuld of this program which was a higher version.  is it possible that Alt F2 calls up the higher version to run?  what im doing depends on running in the older version i think.  thanks in advance for help.

---

### Post by steeldriver on 2012-11-28
Are you sure the gnuradio-core component was successfully built?

```
~/src/gnuradio-3.2.2$ find . -name 'libgnuradio-core\.so\.*' -exec ls -l {} \;
-rwxrwxr-x 1 steeldriver steeldriver 23432072 Nov 27 20:46 ./gnuradio-core/src/lib/.libs/libgnuradio-core.so.0.0.0
lrwxrwxrwx 1 steeldriver steeldriver 25 Nov 27 20:46 ./gnuradio-core/src/lib/.libs/libgnuradio-core.so.0 -> libgnuradio-core.so.0.0.0
```Next you need to know if and where it got installed (/usr/local/lib?) - if it's not somewhere that the linker looks by default you will need to add it to the library search path using ldconfig (or use LD_LIBRARY_PATH - generally deprecated but preferred in certain circumstances)

Since it's a python import error you may need to adjust PYTHONPATH as well

---

### Post by Andrewiski on 2012-12-02
NYCAP,

I am getting the same error message. Were you able to figure out how to add op25 to the python search path I tried using environment variable PYTHONPATH but it didn't seem to work for me.

 

By the way, does CAP stand for Civil Air Patrol?

---

