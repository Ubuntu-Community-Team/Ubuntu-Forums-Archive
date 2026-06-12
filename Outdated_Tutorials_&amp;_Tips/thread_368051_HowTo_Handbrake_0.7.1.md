---
title: "HowTo: Handbrake 0.7.1"
date: 2007-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by matthewstory on 2007-02-22
I created a thread a year or two ago on here about how to turn your breezy box into a multimedia PC, that thread included a mini-howTo on how to install handbrake 0.7 from source.  Handbrake is a DVD ripping program that allows you to rip directly from an encrypted or non-encryped DVD and encode to the file type of your choosing.  You can alternitively rip down the DVD to .vobs on your PC with vobcopy and then encode using handbrake from the vobs.  Well here we are a few years later with a new Ubuntu and a new HandBrake, so here we go.

If you just want to install it, I've scripted it the script can be found on the [bash.zedzone.com]("http://bash.zedzone.com") website . . . which you can all feel free to join . . . shameless plug . . . here's the direct link: [http://bash.zedzone.com/wiki/view_entry.php?wikiEntryId=18832]("http://bash.zedzone.com/wiki/view_entry.php?wikiEntryId=18832")

Just a word of warning . . . this installation takes a long time, I mean a really LONG time, but most of that time you dont' have to do anything.

You've been warned . . . ok, the build of HandBrake requires a few tools that you'll need to install with aptitude:
```

make
jam
nasm
gcc
g++

```
And if you want you can also install libtool, automake and autoconf, but if you don't they will be  compiled from source by jam during the handbrake make.

Then you'll need to download the source code from [handbrake.m0k.org]("http://handbrake.m0k.org"):

direct link: [http://download.m0k.org/handbrake/HandBrake-0.7.1.tar.gz]("http://download.m0k.org/handbrake/HandBrake-0.7.1.tar.gz")

untar that badboy:
```

tar vzxf HandBrake-0.7.1.tar.gz

```
Then cd to the newly created directory:

```
cd HandBrake-0.7.1
```

Now you'll need to generate the jamfile:

```
./configure
```

and then jam it:

```
jam
```

About a half an hour later or so that should be done compiling and ready to go.  If you'd like you can install the program we mentioned above, vobcopy.

The program that you just installed is in the folder that you untarred and it's called HBTest.  HBTest is the CLI version of HandBrake, and as there is no GUI front end for HandBrake, HBTest is HandBrake for us.

HBTest is a very robust CLI program, and is extremely complex in terms of its options, and as someone else has already done a good HowTo on that ([http://caenim.com/HandBrake.CLI.Guide/encoding.php]("http://caenim.com/HandBrake.CLI.Guide/encoding.php")) I will end my HowTo here.

---

### Post by mattmac24 on 2007-04-06
thanks so much for this. for some reason on the handbrake site i was downloading the wrong archive...only had a hbtest file in it. the link in the guide put an end to about 3 hours of frustration. great howto.

cheers,

matt

---

