---
title: "HOWTO: Recompiling MPlayer / MEncoder on (K)Ubuntu Breezy"
date: 2006-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by amarra on 2006-02-25
[COLOR=Red][B][SIZE=4]HOWTO: Recompiling MPlayer / MEncoder on (K)Ubuntu Breezy

[/SIZE][/B][SIZE=4][COLOR=Black][SIZE=2]I've tried installing all the different versions of MPlayer / MEncoder in my Breezy but I feel disappointed by the fact that these versions aren't compiled to use latest processor extensions (despite their name...). So I've googled around and managed to rebuild the MPlayer / MEncoder packages as described below. Furthermore, I've added the H.254 support by installing the open source x.264 codec library from VLC.

[B]
1) Install development tools:[/B]

[/SIZE][/COLOR][/SIZE][/COLOR]```
sudo apt-get install build-essentials
sudo apt-get install devscripts
sudo apt-get install subversion
sudo apt-get install nasm
```

Note that the subversion and nasm packages are needed to download and build x.264 sources from VLC repository. If you don't mind about it, you can skip subversion and nasm installation.
[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

**2) Install x.264 codec (optional)**

Download latest SVN version from VLC repository:

[/SIZE][/COLOR][/SIZE][/COLOR]```
svn co svn://svn.videolan.org/x264/trunk x264
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

Build and install the codec with the following commands:

[/SIZE][/COLOR][/SIZE][/COLOR]```
cd x264
./configure
make
sudo make install
cd ..

```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]


**3) Download MPlayer sources with all needed dependencies**

MPlayer is in the multiverse section of Ubuntu repository, so please enable this section in the sources.list or directly in Synaptic. Then:

[/SIZE][/COLOR][/SIZE][/COLOR]```
sudo apt-get source mplayer
sudo apt-get build-dep mplayer
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]


**4) Hacking debian/rules**

This is a quick-and-dirty tip to enable missing processor extensions in the MPlayer/MEncoder build.

[/SIZE][/COLOR][/SIZE][/COLOR]```
cd mplayer-1.0-pre7cvs20050716/debian/
vi rules
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

Find and remove all the '--disable-xxx' options where xxx is in (mmx|mmx2|sse|sse2|3dnow|3dnow2). Don't mind about what your processor actually support. By removing all the '--disable-xxx' directives you force the MPlayer build to be tailored to your CPU.


**5) Building packages and install**

Now you can rebuild .deb packages of MPlayer and MEncoder by:

[/SIZE][/COLOR][/SIZE][/COLOR]```
cd ..
sudo debuild -us -uc

```

[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]At the end of the build you will find all the .deb packages produced in the parent directory.

[/SIZE][/COLOR][/SIZE][/COLOR]```
cd ..
sudo dpkg -i install mplayer-586*
sudo dpkg -i install mencoder-586*
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

Despite their name, as said before, mplayer and mencoder binaries now support all extensions of your CPU, as you can easily check by launching mplayer or mencoder without any parameter. On my Athlon 64 mencoder said:

[/SIZE][/COLOR][/SIZE][/COLOR]```
MEncoder dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags: Type: 8 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

while on an Athlon XP:
[/SIZE][/COLOR][/SIZE][/COLOR]
```
MEncoder dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

If you installed the x.264 codec before the mplayer building, you can check the codec presence in MEncoder by the following command:

[/SIZE][/COLOR][/SIZE][/COLOR]```
mencoder -ovc help
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

It should display, among others, the following line:

[/SIZE][/COLOR][/SIZE][/COLOR]```
   x264     - H.264 encoding
```[COLOR=Red][SIZE=4][COLOR=Black][SIZE=2]

That's all, folks.... ;)

I hope this can help anyone that is 'optimization-fanatic' as I am.

Bye.

[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by jazzi on 2006-03-05
THAT'S very helpful.Thanks

---

### Post by Ahriman on 2006-03-14
Another satisfied customer!

Cheers, dude, works great \\:D/

---

### Post by TrendyDark on 2006-03-14
Is there an performance increase with this little mod?

---

### Post by DumbNoob on 2006-03-18
I was skeptical that this might break mencoder working in acidrip because until the recent update it didn't work for me.  It's going great though.  On my computer it gave me, at the minimum, 50% faster speeds with Xvid so far on the second pass.  The first pass I got an even better improvement.  I'm a third of the way through the second pass.  I'll edit the post if it doesn't work out but I've already tested a one pass encode so I doubt there's a problem.  Anyhow THANKS!

As you can see by my username, I don't know a lot unless it's spelled out for me.  I got stuck in the how to at deleting all the --disable-xxx with **vi rules** because I didn't know how to save it.  I figured out key combinations to get me backto the prompt but it didn't save it and it got old trying over and over to find the right key combo and google was no help so I just used sudo gedit which turned out to be easier too becuase I could use the search function for --disable and then just make sure it wasn't something other than the entrys I wanted.

Also, I think the H.254 thing was already installed because it's what comes up default in the gui when I use gtranscode.  Maybe not.. I'm not sure.  I got an error on part of the installation of it in this guide though.  I also got a bit of error messages when it came to making the deb packages but  it is still working and my one pass has a little better detail, such as facial expression, than it did in the two pass before I did all the above so it's still worked out.

Once again, thanks.

Also, it took a really, really long time for the final part to do it's work.  I thought perhaps I had edited that file wrong and that it was caught in a loop and almost closed the window.  Maybe it would be a good idea to add that it takes a long time to build and is also building more than just one architecture because seeing the same things fly by a few times also had me scratchin my head during that part of the process.

---

### Post by efreddi on 2006-04-02
Hi All,

I wanted to have Mencoder capable to use the x264 (in my opinion the best free codec at the moment), so I tried to apply the posted procedure. Here my experience:

**x264**: the procedure of Amarra worked without any hickup, everything ok :) 

**mplayer/mencoder**: here things didn't go that easy... :( 

*sudo apt-get source mplayer*
ok, no problems

*sudo apt-get build-dep mplayer*
here I receve the message that some dependency can't be satisfied. I tried to go on.

[I]cd mplayer-1.0-pre7cvs20050716/debian/
vi rules[/I]
made ;) 

[I]cd ..
sudo debuild -us -uc[/I]
first problem, some error message during building, I have been suggested to run debuild with *-d* option. The second trial gave me another error: missin GTK Devel... with Synapthic I installed the *libgtk1.2-dev*. I try againg

*sudo debuild -us -uc -d*
but after several minutes I get another error :mad:
At this point I got nervous. Looking in the forum I found this post on the same topic:

[http://www.ubuntuforums.org/showthread.php?t=85190&highlight=compiling+mplayer](http://www.ubuntuforums.org/showthread.php?t=85190&highlight=compiling+mplayer)

so I decided to give it a trial.

[I]./configure
make[/I]
and again error. I didn't have the permission to open some file. My nervous were like trings of violine... I tried to force the situation in not correct way:

*sudo make*
after several minutes I get an error: some file is missing. I opened the guilty source file and I found that the missing files were connected to some *tremor*, so I made

*./congig --help*
and I found the option to disable this *tremor*.
Again

*sudo make*
finally everything ok :)
and then

*sudo make install*

and everything went fine.
Anyway, I didn't want to spend to much time to understand what was wrong, it was too late in the night. My goal was to get mencoder and x264 working together and I accomplished it.

My 2 cents, bye


Elia

---

