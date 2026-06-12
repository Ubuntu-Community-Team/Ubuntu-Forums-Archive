---
title: "Request: Installing Sbagen Manually"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by threecaster on 2012-08-20
Greets to the Geeks:

I've got an Natty Narwhal 11.04 on an old Aspire 2020 ; I'm more or less keeping together, but always have to struggle somewhat in terminal until I get my sea legs again...

Machine likes Natty good enough, runs GUI and latest Firefox jus' fine!

I've got a supported program that has no repository listing: [http://uazu.net/sbagen/sbagen-1.4.5.tgz](http://uazu.net/sbagen/sbagen-1.4.5.tgz)

at [http://uazu.net/sbagen/](http://uazu.net/sbagen/)

This is a cool binaural beat generator, that gives superior fidelity to anything compressed...

I'll extract the files just fine. Goto terminal (with root btw...) and invoke "./mk" as per instructions.

She sits there a good bit, appearing to ponder, then returns empty command line.

Then "sbagen" returns "command not found".

The instructions give lots of specific details, but are tailored to the experienced Linux hacker. I have no idea what kernel or libraries I have....or how to use a shell.

Being keen not to stick my fingers in the gears, I am asking here for some pacific instructions on what to check or some commands to shed light on what is working/malfunctioning.


Tanx!

Here is the relevant exerpt from SBAGEN.txt:
> 
2.3: Installation for Linux and other UNIX users  
------------------------------------------------

Download the TGZ and unpack it somewhere.  On Linux, the executable
can be built using the little 'mk' script:

>> ./mk

This script assumes GCC on Linux.  If you're using something else,
please check the script and adjust it as necessary.  There is also a
script 'mk-ansi' which strips out non-ANSI C stuff before compiling,
which may work if you don't have GCC.  A user has provided 'mk-netbsd'
to build on NetBSD.  The other 'mk-*' scripts cover other
possibilities and other platforms -- see the comments in the files for
more details.

If you want Ogg and/or MP3 support, and the pre-built .a files aren't
any good to you, you'll need to rebuild them yourself.  See
'mk-tremor-linux' and 'mk-libmad-linux', which include some
instructions at the top of those files.  On UNIX in general this
should be fairly straightforward -- just be happy that you're not
trying to build this on Windows!

On UNIX systems the code handles output to a stereo /dev/dsp device
using either 16-bit signed or 8-bit unsigned samples, or to standard
output, or to a WAV or raw file.

Regarding minimum processor requirements, a Pentium-75 can easily
handle 8 channels of 16-bit 44100Hz binaural beat output.  OGG or MP3
decoding obviously requires more processor power, though.  All the
most time-critical parts use integers only (including Ogg and MP3
decoding), so the code should be relatively easily portable to ARM or
whatever, although I haven't tried this.

Note that the 'nice' or 'renice' commands may be used as root to give
sbagen a greater priority if output gets choppy on low-spec machines.
In any case, you may want to permanently install the 'sbagen' binary
by copying it to /usr/local/bin/.  It needs no support files to run.

Once built, you can test the utility quickly by using any of the *.sbg
files as an argument to sbagen.  There are also some shell-scripts
(t-*) that take you through certain sets of tone-sets, and some
perl-scripts (p-*) which generate and run sequences.

---

### Post by threecaster on 2012-08-22
Nothing?

I got this working on my dinosaur windows in like 8 clicks and no typing.

Really?

I guess no one cares.....  :(  *snif*

---

### Post by 25tom on 2012-08-22
In the terminal you need to run the mk script from within the directory that you unpacked the files to. Use the command ```
cd
``` followed by the filepath to the directory containing the files you unpacked from the archive. Then use the mk script. For example, if the aforementioned directory is in your home folder and is called "folder" then the command would be ```
cd /home/"whatever your username is"/folder
```
Then run the mk script.
Hope this works - and be careful using root! :)

---

### Post by threecaster on 2012-08-27
You are right on track sir, however I am saddened to say that this was already done, (and for those who don't know, you can copy a filepath from a gnome file mangler window and RightClick to paste it into the command line in terminal. (assume terminal in gnome, of course...)

so, in invoking ./mk while command line is pointed to folder locating .mk script...This is what has been performed thus far...with "meh" results....

[IMG]http://www.nokioteca.net/home/forum/uploads/av-383078.jpg?_r=0[/IMG]
"works....doesn't work?
what's the difference?"

(And thanks tho! i wus worried it was gonna get kicked out!)

---

### Post by threecaster on 2012-09-18
[IMG]http://imghumour.com/assets/Uploads/Lets-Bump.jpg[/IMG]

---

