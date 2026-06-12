---
title: "Batch Converting and Ripping to Ogg useing the aoTuV encoder."
date: 2008-11-24
forum: New to Ubuntu
---

### Post by osc1882 on 2008-11-24
Ok,so I need to start converting flac files and ripping cd's to ogg and I have been informed that I need to use the aoTuV encoder. I'm guessing the newest version is the best but maybe the second newest would work. So the question(s) is does Ubuntu us aoTuV out of the box already? I want to use -q6 or -q7. I have tried "Sound Converter" but they use different bitrates instead of qualities. And I don't know if it is useing aoTuV. Then I tried OggConvert but it seems to only let you load one file at a time, no batch converting.

Any wisdom?

Also in a short while I may need to rip cd's to ogg. 

I want to support and push Ogg because it's free(as in freedom) I just need a little help getting started.

---

### Post by osc1882 on 2008-11-25
Bump. (Thought I would bump it before I went to bed.)

---

### Post by osc1882 on 2008-11-25
lol Double Bump (Before I go to work. lol )

---

### Post by vanadium on 2008-11-25
I guess the standard libvorbis encoder comes with most linux systems, and not the aoTuV optimized version. You can download a pre-compiled aoTuV encoder yourself and eventually replace the standard binary with it.

Once you work at the command prompt, batch conversion is easy. To convert an entire directory of wav files to ogg:

```

for f in *.wav ;  do oggenc -q 6 "$f" ;  done

```

Using find, you can do an entire directory tree

```

find . -name '*.wav' -execdir oggenc -q 6 "{}" \;

```

---

### Post by doug1212 on 2008-11-25
To use oggenc-aotuvb5 your easiest option would be to find a pre compiled binary (Hydrogen audio?) and drop it in /usr/local/bin and point your ripping app to it.

To convert your flacs to oggs do a search for a bash, perl or python script that can mass convert and copy tags / artwork, or there are nautilus extensions to do the same.

My ripper of choise is abcde (command line) I also use the latest cdparanoia 10.2 as pre compiled binary in /usr/local/bin and edit ~/.abcde.conf file to point to it.

Doug.

---

### Post by osc1882 on 2008-11-27
Wow, is there a page with step by step instructions for any of that. Every time I think I am good wih Ubuntu I find out that I am not.

---

### Post by vanadium on 2008-11-28
Make sure you download the linux binary for the aoTuV encoder.

You can move the downloaded binary to a good location using a file manager window with root permissions. You start such an instance with the command "gksu nautilus". Go to /usr/bin, rename the existing oggenc to "oggenc.old". Move the downloaded binary there and rename it to "oggenc". Then close the nautilus window in order to prevent you from doing damage to the system by accident.

---

### Post by doug1212 on 2008-11-28
If you want Aoyumi's aotuv encoder system wide and you don't mind adding repositories from launchpad have look here:

[HTML]https://launchpad.net/~pjssilva/+archive[/HTML]

If you do add the repo do add the PGP Key first.

If you fancy a nautilus right click menu for converting from flac to ogg install "Nautilus-flac-Converter" I am on Hardy and had to build it from source (not difficult).

[HTML]http://nautilus-flac.sourceforge.net/[/HTML]

---

