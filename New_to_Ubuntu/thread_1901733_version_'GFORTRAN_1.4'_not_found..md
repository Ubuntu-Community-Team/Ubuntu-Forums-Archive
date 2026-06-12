---
title: "version 'GFORTRAN_1.4' not found."
date: 2011-12-29
forum: New to Ubuntu
---

### Post by Flimp on 2011-12-29
Hi all,

I've been trying to get a program (jsplit) to run, but kept receiving the following error message:

> [FONT=Courier New]jsplit: usr/lib/i386-linux-gnu/libgfortran.so.3: version 'GFORTRAN_1.4' not found (required by jsplit)[/FONT]I have tried to uninstall and reinstall gfortran using Ubuntu Software Centre as well as through the terminal, but to no avail. Furthermore, when I tried to update gfortran, the message that came back was that it is the latest version, so I am pretty much stuck. Any help is greatly appreciated.

PS. I have done a google search and came across this:
_*[COLOR=DeepSkyBlue][http://www.mailinglistarchive.com/html/fortran@gcc.gnu.org/2011-02/msg00292.html](http://www.mailinglistarchive.com/html/fortran@gcc.gnu.org/2011-02/msg00292.html)[/COLOR]*_
but I'm not sure if the problem is exactly the same as mine, since I am completely new to the Linux environment.

---

### Post by jjex22 on 2011-12-29
Hi there, and welcome to the forums! sorry to hear you're having difficulties.

It occurs to me that the problem may be with jsplit as it must have been ported to linux - did you get it from source or the software centre? sorry I'm on my pad atm so can't check the repos.

I'd personally suggest downloading WINE from the software centre (a package designed to run windows programs on linux) and seeing if a windows jsplit.exe of  jsplit will work with wine - as it's so basic i'd imagine it probably would. I forsee problems getting full functionality out of it without WINE as it uses MS batch files for putting the bits back together again, and linux (well any unix system) doesn't use .bat files.

If this doesn't work, you may be interested in hjsplit - another basic windows 9.x splitter program that can handle large files - this one does work on wine.

You may be interested to know that unix does actually have its own splitter program built in, except you have to run it from the terminal (ctrl+alt+T).

the command to break the file up is
```

split

```
and the command to put them back together is
```

cat

```

there are of course  several options you can stick into these commands. a full list of these commands can be found on the manual page - just type 
```

man split

```
to see them, but for an example - say I have a ridiculously large file, that I have in my wisdom called "ridiculously-large-file"  that I want to send to my friend as an email attachment, but I'm only allowed to attatch files 500m in size! well I could break it down with
```

split -b 500m -d - ridiculously-large-file

```

where -b allows me to set the size of the "bits" in bytes - here I choose 500m for 500mb. and -d means use numeric suffixes (so i'll end up with lots of files ending in .01, .02 etc insteas of .a, .b etc - this one is just personal preference.

Anyway my unix using friend then gets my email, but would really like to put the file back together, they would open up their terminal and type 
```

cat ridiculously-large-file* > ridiculously-large-file

```
notice the * after the file name - this tells cat to put all the bits back together.


there are also of course gui tools which you can find in the software centre, and split files can't be put back together on a windows machine, (mac osx, bsd, linux all fine) but it is useful to know as you could add it to another command; for example (don't try this, this is just an example)
```

sudo dd if=/dev/sdz of=/data/backups/zdrive.img  | tar cvfj /data/backups/zdrive.img | split -b 690m -d - zdrive.img.tar.bz2

```

I have deliberately used paths that most people wont have incase anyone put this into a terminal, but what's happening here, as an example to what Unix can do for the new user, is as follows
1) the "sudo" command gives you administrator privileges
2) the "dd" command in this case copies my hard drive partition "Z" to the folder data>backups and converts it into an image file called "zdrive".
3) the "tar" command then compresses this image down, creating a .tar.bz2 file -a "tarball"
4) the "split" command that we've already seen then breaks it down into CD sized parts to be written to some CD's.

all this from one command! there are much better ways to back-up and more efficient ways to write this command, I include it only as an example - always read the man page of any terminal command you havn't used before, before you use it so you understand how it works :)

Hope you find this information useful, and 
enjoy linux!

---

### Post by Flimp on 2011-12-29
Thank you for your response.

I forgot to mention that jsplit is a scientific (physics to be precise) program used to reorder configuration states by angular momentum and parity, and unfortunately only works on Linux machines, hence the reason why I started using Ubuntu.

Regardless, your response taught me something else that may come useful one day :)

---

### Post by audiomick on 2011-12-29
I suspect, and it is a guess, that the version of gfortran in the repos ( I looked for it on this install, which is 11.04) might be actually newer than the one that jsplit is looking for. This sort of thing can happen, and is a bit of a Catch 22.

Perhaps you could post a link to where you got jsplit from.

You might also like to look for the home page of gfortran and see if you can get the required version from there.


Just incidently, I would consider it a bonus that jsplit only works on Linux. But that is just my opinion. ;)

---

### Post by jjex22 on 2011-12-29
Sorry for getting the program in question confused!

Unfortunately I can't find any info on jsplit by searching google, did you get it from source files, or the software centre? as I say, I'm travelling home at the mo, so don't have access to Ubuntu!

---

### Post by Flimp on 2011-12-30
> **audiomick said:**
> I suspect, and it is a guess, that the version  of gfortran in the repos ( I looked for it on this install, which is  11.04) might be actually newer than the one that jsplit is looking for.  This sort of thing can happen, and is a bit of a Catch 22.

Perhaps you could post a link to where you got jsplit from.

You might also like to look for the home page of gfortran and see if you can get the required version from there.


Just incidently, I would consider it a bonus that jsplit only works on Linux. But that is just my opinion. :wink:
I think you are right. Now that you mention it, I just realised that this hiccup is only occurring on this particular machine, which is running the latest Ubuntu. It runs fine on all the other ones, including on my Macbook Pro, which is running Ubuntu 10.04. In this case, is there a way to fix it other than to install Ubuntu 10.04? I never thought that gfortran would be affected by the operating system it runs on.

Oh, and jsplit is a program that comes from a package called grasp2K. It's obtainable from the CPC Program Library, Queen's University, Belfast ([http://cpc.cs.qub.ac.uk/](http://cpc.cs.qub.ac.uk/)) but I think you need a licence or something.

> **jjex22 said:**
> Sorry for getting the program in question confused!

Unfortunately I can't find any info on jsplit by searching google, did you get it from source files, or the software centre? as I say, I'm travelling home at the mo, so don't have access to Ubuntu!
It's okay. I appreciate your help though. The program is part of a package called grasp2K, obtained from the link above ([http://cpc.cs.qub.ac.uk/](http://cpc.cs.qub.ac.uk/))

---

### Post by audiomick on 2011-12-30
> **Flimp said:**
> ... is there a way to fix it other than to install Ubuntu 10.04? I never thought that gfortran would be affected by the operating system it runs on.

Yes, you can lock a version of a package, but I am a bit shaky on how to do that. I will try and look into this in the next couple of days. It being the weekend and new years eve, I don't know how my time will work out. Best thing would be if someone else has a bright idea.

Just for the record, it is not Fortran that is being affected by the OS, but rather the version of the compiler, which is a different can of worms altogether.

---

### Post by lkraemer on 2011-12-30
FLIMP,
The problem is that you don't have your PATHS set correctly so the 
Compiler or Linker finds the correct LIBS (Libraries).

To proceed we need more information on your *nix system.

1.  What shell are you running?
2.  Have you set any PATHS?
3.  What Versions of gcc, g++, gfortran?
4.  What Version of *nix and what Distro
5.  What is contained in your env
6.  Where is the software URL, what are the requirements or dependencies to install it?
7.  Is the Software a .deb or .rpm or do you have the source and you are trying to compile the source?
Is it some other Alien package? .. Hopefully not?

So, dig up the above information and post it.  If you don't know we'll go slow, a couple of steps at a time.

To find the versions of the compilers use:
```

gcc --version
g++ --version
gfortran --version
gcc --version > gcc.txt

```

If you can't locate gcc.txt use:
```

sudo updatedb
locate gcc.txt

```
It should be at /home/loggedinuser/


Here is the first part of my TIP sheet/document for you to read/study.

HOWTO: Set up your environment for Compiles in *nix

1.  Learn to use the Terminal along with the "man" (without " " 's) command to find the information you need.
    Let's update the database so we have the current information for the locate command.
2.  man updatedb  --  Read about the command
3.  sudo updatedb  --  Do the database update, .........then search for grep and information on grep
4.  man grep  --  Read about the command grep
5.  which grep  -- Locate the subdirectory where grep is located
6.  man locate  --  Read about the command locate

As an example: for Step #2 the Terminal command you would use is:
```

man updatedb

```
ie, no quotes, no trailing comments like.....   --  Read about the command

Now, I'm running Debian 6.0 "Squeeze" and my results of locate are:
> 
larry@debian:~$ sudo updatedb
[sudo] password for larry: 
larry@debian:~$ locate libgfortran
/usr/lib/libgfortran.so.3
/usr/lib/libgfortran.so.3.0.0
/usr/share/doc/libgfortran3
/var/lib/dpkg/info/libgfortran3.list
/var/lib/dpkg/info/libgfortran3.md5sums
/var/lib/dpkg/info/libgfortran3.postinst
/var/lib/dpkg/info/libgfortran3.postrm
/var/lib/dpkg/info/libgfortran3.shlibs
/var/lib/dpkg/info/libgfortran3.symbols
larry@debian:~$


So, if you do the same you should find the fortran LIB's your compiler/linker is looking for......but not finding.


The next step you need to do is to find the "SHELL" and "env" you are using.

8.  env  --  Display the current environment, find what Shell is being used with the following command.....
```

    env | grep SHELL=

```
    You can also type:
```

    env > envorig.txt

```
    to create a file of the results to attach. In fact go ahead and do this
    and attach the file so we can view it.  Later you can do a comparison for future reference.

9.  locate .*rc  -- Find the current logged in user's home shell Configuration file (*rc)... use:
```

locate .*rc

```
 	REF: [http://en.wikipedia.org/wiki/Unix_shell](http://en.wikipedia.org/wiki/Unix_shell)
	Bourne shell (sh)
	Almquist shell (ash)
	Bourne-Again shell (bash)
	Debian Almquist shell (dash)
	Korn shell (ksh)
	Z shell (zsh)
	C shell (csh)
	TENEX C shell (tcsh)
        other shells..............

     There may be a .bash_profile file in /home/user along with .bashrc.  You can put configurations in either file, and you
     can create either if it doesn&#8217;t exist. But, why two different files?  What is the difference?  According to the bash man page,
     .bash_profile is executed for login shells, while .bashrc is executed for interactive non-login shells.

     If .bash_profile exists in /home/user with the following information already inserted:
        ```

	PATH=$PATH:$HOME/bin
	export PATH
        
```
     just append your path modifications here instead of the .bashrc file in Step #10.  (ie. CentOS 6)

 
At this point you are about 50% there....but you're most likely 100% over your head.  But READ SLOW, Execute the commands
in a Terminal Window (Console or xterm) and post results and questions.

Just don't give up.


Now, install MELD via Synaptics (SYSTEM -> APPLICATIONS -> SYNAPTICS PACKAGE MANAGER), which will be used for compares later.

WHEW!  Hope you have a grasp on where we have been..........

lk

---

### Post by anewguy on 2011-12-30
With 11.x I believe you first have to install synaptic package manager (I don't believe it is installed by default) via the command line - sudo apt-get install synaptic   

After that you should be able to find the package manager - in 11.x with the Unity desktop, move your mouse to the left until the menu pops in, then go up to the top button in the menu - "Dash Home" and click it.  Put syna in the search string then click on the synaptic package manager icon.

Then continue on with what lkraemer is telling you above.

It's also possible, I suppose that maybe all you need to do is create links for the .3 versions to their .4 counterparts.

Dave ;)

---

### Post by lkraemer on 2011-12-30
Dave,
Thanks, The symbolic link may indeed be another problem.  That is why
I had him do a > locate libgfortran  so we know what
exactly is on his sytem.  But the software may require a later verson,
or a symbolic link to the previous version.  I guess time will tell.

Thanks for the assist!  It's appreciated.  Hope you are doing well!
Happy New Year!

lk

---

### Post by lkraemer on 2011-12-31
Flimp,
If you are compiling from source, you will need to extract the source,
then cd to the source subdirectory.  Once there you need to look for
a readme file or document describing how to compile the source.
You also need to look for a makefile and a configure file.  They may or
may not exist.  Same for any/some documentation.............
That's your responsibility.


**INSTALL REQUIRED SOFTWARE FOR COMPILE:**
Typically you need to install build-essential and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


**TYPICAL COMPILE STEPS:** (from within your source directory)
assumes you have searched for the configure & makefiles, and Documentation on compiling....
```

./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up on a successive compile.
It also removes the Bin file from the source subdirectory.  It should be obvious to you that if make
doesn't work, there is no need to execute the "sudo make install" command because nothing was built
that could be installed.  And after your software is installed, you can do a "make clean" to remove
all the un-necessary files that were generated.


**COMPILE xxxxx FROM SOURCE:**

1. Use Synaptics to install the required Library Files required/needed for the Compile:
Assume you get an error code stating sdl1 is missing.......EXAMPLE:
```

libsdl1.2-dev
somerequiredlibxext-dev
somerequiredlibreadline-dev

```
Typically you will need a -dev lib file.  And there may be several others.....

2. Compile & Install (no configure file exists, and no errors from compile assumed......):
```

make clean
make
sudo make install

```
But, you may have to edit the configure file, to suit your compile, or
set different FLAGS, according to the README or Documentation.  That's
your job!

Also you may have to compile the lib's needed before linking to them.
You may have a libxy.a or libyx.so.  For more information on what they
are and how to generate them use "GOOGLE".  I'm assuming you either know
what to do to compile & link the code or the Makefile sets it up for you.
If you compile the libs, built from the source, typically they are written
to the source directory located at ~/source.....where ~ is your /home/loginuser 
These may need to be moved to your /usr/lib subdirectory before compiling your code,
the makefile may copy them where they are needed, or you may be able to leave them
in the source directory.    More on that later...............



SO, back to the last half of the TIP Sheet......


You need to list the *rc file to verify the contents and set the PATHS.  I'm ASSUMING a Bash shell......Your may be different!

10. cat .bashrc  -- List the configuration file, then append the proper search paths for the users shell with edit.
> 
	export LD_LIBRARY_PATH=????????????????????????????????
	export LIBRARY_PATH=???????????????????????????????????
	export C_INCLUDE_PATH=?????????????????????????????????
	export CPATH=??????????????????????????????????????????

Mine happens to now be:
> 
	export LD_LIBRARY_PATH=/usr/lib:/usr/local/lib
	export LIBRARY_PATH=/usr/lib:/usr/local/lib
	export C_INCLUDE_PATH=.:/usr/include:/usr/local/include
	export CPATH=.:/usr/include:/usr/local/include

But your may vary accordingly.  You won't be able to cut & paste mine,
unless your system is built exactly like mine.  It's up to you to locate
exactly where all the libs and includes are located.  That is what all the
previous commands should have helped you do.  Just because you have 
/usr/lib & /usr/local/lib included....doesn't mean your needed lib is in that path.
That is where your detective work comes to play.  SEARCH and use grep to locate the libs.

Once you have the env set either reboot or reset the env.  Once again,
your system command for this can/may be different.

11. source .bashrc  -- Reset the environment to what we need for Compiles, assuming the SHELL is bash.
    This may not be available on your system.....

VERIFY the env is correct:
12. env  --  Display the new environment to verify the paths.............PARTIAL DISPLAY of SPECIFIC's I NEEDED...
        > 
	LIBRARY_PATH=/usr/lib:/usr/local/lib
	LD_LIBRARY_PATH=/usr/lib:/usr/local/lib
        CPATH=.:/usr/include:/usr/local/include
	C_INCLUDE_PATH=.:/usr/include:/usr/local/include
        

Since your env is now set as you need, save env contents to another file named envnew.txt.  Later,
you can use Meld to compare the two files.

Now, all you have to do is Compile & Link - with/without makefile.  Correct any errors, and 
recompile.  That info will follow tomorrow.

Maybe by then, you will have posted some info......


lk

---

### Post by lkraemer on 2011-12-31
Flimp,
Now you need to do a lot of reading on the tutorials for "makefile".
That is another complete study area, but one you need to know a bit about.
The best thing I can tell you is to use GOOGLE and search for "makefile tutorial".
That will give you some good insight to using modifying your makefile.
REF:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

So, with that under your belt, I've attached a typical Makefile that is located in
the source directory.  This makefile generates a lib.a file, along with some test
programs.  (You need to GOOGLE lib.a & lib.so files for information on what they are
and how you can find the functions contained within the lib.  ie.  ar & nm commands,
as that's your homework!)

Take a look at the attached typical Makefile.  You should notice you can
do  the following commands to compile all, compile only one source file, clean, etc..:
```

make TurboCChars
make TestGraphics
make TestCscanf
make GraphicsTest
make hex2h
make Test
make libTurboC.a
make libTurboCu.a
make clean
make

```


**REF ATTACHED:** Makefile.txt

Obviously I've renamed Makefile to Makefile.txt to meet the upload requirements of this forum.  You will
need to make sure your Makefile is named properly......

Don't forget to set your makefile permissions to 755 so you can execute it.......That is often forgotten!


SO, back to the last tidbit of the TIP Sheet......

I'm assuming you know a bit of the typical compile/link commands.  If not, man gcc or man gfortran will
guide you along with GOOGLE searches of how to compile C/Fortran programs in *nix.


Here is an example of one I used to build the TurboC-source library.  It what I used to locate my makefile problem.
Notice we are tying up all the loose ends now, so you should be sitting pretty.........
If you get a Compile ERROR or make ERROR....GOOGLE Search is your friend!

13.  ```
gcc -g -Wall testbgi.c -o testbgi.exe -L/home/larry/bgi -lbgi.a
```
	Compile testbgi.c with debug information (-g) with Warnings (all) to Object testbgi.exe (-o) and .....
        link libbgi.a which is library archive, located at /home/larry/bgi.  Use ar -t libbgi.a and nm -s libbgi.a
        along with man ar and man nm to get more information on the archive's contents.
     ```

     gcc -c testbgi.c -o testbgi.o
     gcc -o testbgi.exe testbgi.o -L. -lbgi.a
     
```
        ONLY Compile testbgi.c to object testbgi.o and then create the exe, by linking to library libbgi.a located at /home/larry/bgi

14.  ./testbgi.exe  --  will execute the Binary file in *nix.  Check your permissions and set as required to allow execution by you.
     ```

     ./testbgi.exe
     
```
     If your source was compiled with the -g switch, you can use gdb or ddd to debug your source code.  NICE!


Now, since you are finished you can use Meld to compare your env Original file, with the modified env file.  It's WONDERFUL!


ZIT ZOT!!!  ... SLICKER than SNOT!  Wasn't that easy?
 
I hope I haven't forgotten anything, but it's possible..... Time will tell.


What is your status?  I sure hope I haven't spent hours typing, and creating something you will ignore, because
that seems to be a major trent on this Forum nowdays.
 

lk

---

### Post by anewguy on 2011-12-31
I'm going to leave the OP in your more than capable hands as I'm really not familiar with this end of things at all.

Things going ok on this end - I hope the same for you!  Wishing you a happy new year as well!

Dave ;)

---

### Post by Flimp on 2012-01-02
> **lkraemer said:**
> 
What is your status?  I sure hope I haven't spent hours typing, and creating something you will ignore, because that seems to be a major trent on this Forum nowdays.
 
Sorry I couldn't reply earlier. There's been some issues at home over the last couple of days so I've only just sat down to properly read all your replies right now.

I will work on them from the top and keep you guys updated.

A big thank you to everyone who tried to help. 

All the best wishes for the new year, guys :)

PS. lkraemer, I'm very, very new to Linux, so it's probably going to be a slow progress. I can predict some follow-up questions soon enough, so many apologies in advance if I'm going to annoy the hell out of you. Everything is pretty clear so far, so here's hoping it'll continue to move along smoothly. ;)

EDIT: It's almost 2.30am here, so I'll be heading off to bed. I'll let you guys know how it all went within the next 24 hours. Cheers, and thanks again.

---

### Post by Flimp on 2012-01-03
IT WORKS!!!!!!!!!!!!!! :D

I tried reinstalling the package but this time, instead of 'make', I used 'sudo make' and weirdly enough it installed properly.

Thank you again, guys. Especially to lkraemer for all the effort he'd put into this. I'd hug you if I could. 

This is an excellent start to the year.

---

