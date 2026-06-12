---
title: "[SOLVED] burning cd using flac/cue"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Praxicoide on 2008-10-29
Hello,

I've tried to burn an audio CD that was ripped into one long .flac with a .cue file. Using Brasero I get the error "could not find name_of_file.**wav**." I can't find the way to make Brasero use the .flac file available. Is this an error in the .cue file or does Brasero not support flac/cue burning? Is there another program that can perform this?

---

### Post by Bölvaður on 2008-10-29
I wrote a cd with flac songs and it worked. But... I couldnt find out which program I used :(

---

### Post by Praxicoide on 2008-10-30
Yeah, I'm more inclined to think it has to do with Brasero. I'll try alternatives. Thanks.

---

### Post by Praxicoide on 2008-11-02
OK, after a rather hellish upgrade to Intrepid (wanted to try this out instead of a clean install for a change - not doing it again), I decided to take another stab at this and found [this blog](http://onubuntu.blogspot.com/2007/06/splitting-cueflac-files.html) which shows the tools needed to split the flac file (which can then be burned by any burning program).

Anyways, I tried it and it works fine.

All you need to do is to open up a terminal and type:

```
sudo apt-get install cuetools shntool
```

afterwards, you cd into the appropriate directory and type:

```
shntool split -f filename.cue -o flac filename.flac
```

replacing "filename" with the name of the cue and flac files.

And there you go. 

Addendum: on a vaguely related topic, after the upgrade to Intrepid, I can't drag and drop on Brasero any more. It's silly, but I got used to doing that instead of hitting "add." Does anyone know what happened?

---

### Post by kahlil88 on 2008-11-03
I'm having problems burning an audio CD from a single FLAC and CUE sheet. Brasero keeps reporting that it's an invalid cue sheet.

---

### Post by Praxicoide on 2008-11-03
Weird, I got it to open it just fine; the error I got was on the missing .flac file, which is expected.

Maybe you can cut the .flac with shntool as shown above?

---

### Post by kahlil88 on 2008-11-06
> **Praxicoide said:**
> Weird, I got it to open it just fine; the error I got was on the missing .flac file, which is expected.

Maybe you can cut the .flac with shntool as shown above?
I noticed that when the files are anywhere but the home directory, it won't find the FLAC. Does shntool update the cue sheet? I'd like to burn with the cue sheet so that when I pop the disc in a computer, any CD-ripping software will know the CDDB code and provide me with metadata.

---

### Post by @B6Mwu8fN9M on 2009-07-19
Here's a good tutorial which shows how to split a flac file into multiple files based on the cue file. It also shows how to transfer metadata from the cuesheet to the split files.

[http://webupd8.blogspot.com/2009/04/split-ape-and-flac-files-in-ubuntu-and.html](http://webupd8.blogspot.com/2009/04/split-ape-and-flac-files-in-ubuntu-and.html)

---

### Post by pprjack on 2010-02-27
I dispute the SOLVED status of this thread as the original Brasero bug still exists for me.
Brasero error claims it cannot find the .cue sheet after I have opened the .cue sheet with Brasero, ie; right click on the .cue sheet and select "Open with Brasero" context menu option. 
I still cannot recreate the original CD from the RubyRipper created .cue sheet and associated .flac file with Brasero.
Is this issue being worked on? A workaround is not a resolution.
Also not sure if this is a RubyRipper bug or a Brasero bug.
I noticed that the RubyRipper created .flac file is slightly strange in that it does not seem to name the .flac file correctly unless naming them all "- .flac" is the intended behavior
Is there another CD ripper that creates .cue sheets I can test with?
I would hate to have to go back to EAC running in WINE.

Following EAC WINE test;
Brasero still complains it is unable to find the .cue sheet created with EAC so it is a Brasero bug, not solved for me.

---

### Post by pmooney78 on 2010-07-10
But "solved" on this forum just means that the original poster has had their issue resolved; it's not some indication that the software works perfectly for all users on all configurations in all circumstances.

Ubuntuforums is not a bug-tracking site, but one in which people ask for help for their individual problems. In that sense, the "solved" tag is non-disputable. The OP has had their issue resolved. If your problem, which is different from the OP's, is not solved, you are welcome to file a bug report with the software developer, or start a new thread in which you ask for help for your particular situation. Latching on to someone else's thread with your own (somewhat different, somewhat similar) problem and complaining that the advice given to others don't help you is juvenile.

---

### Post by idiosynthetic on 2010-11-28
This works for me with a .cue and .wav from EAC:

```
cdrdao write <filename>.cue
```

---

### Post by kipjones on 2011-01-26
cue sheet, .flac file, Brasero, etc - shntool does the trick here.

Thank you, Praxicoide, for saving me from hours of investigation and nail-biting.

---

### Post by etherspin on 2011-08-28
I didn't care for Brasero, so I installed Wine and then installed [Burrrn]("http://www.burrrn.net/?page_id=4").  

It's a great little piece of software!

---

### Post by Michael Schmidt on 2011-11-26
I also fiddled with this problem for quite some time and then found a simple solution.  For my cue/flac file, I found Brasero wouldn't burn it, shntool wouldn't extract the tracks, but VLC would play it just fine.  I opened the cue file with a text editor.  Here are the first few lines:

REM GENRE "Progressive Rock"

REM DATE 1970

PERFORMER "King Crimson"

TITLE "In The Wake of Poseidon"

FILE "King Crimson - In The Wake Of Poseidon.flac" WAVE

Notice the data FILE is .flac (it is, indeed, a .flac file) but the format is listed as WAVE.  I installed Sound Converter and converted the .flac data file to .wav.  Then, in the .cue file I changed the FILE extension to .wav, so it matched the newly converted file.  Opened the .cue file in Brasero and it burned without incident.

---

### Post by LexRoss on 2011-12-01
That is kinda weird, as most CD rips I had downloaded lately came in FLAC format. Yet, the CUE specification only allows BINARY, WAVE and MP3 to be used in CUE FILE command. Either specification needs to be fixed or Brasero should be able to handle this common situation (.flac file with the WAVE command option). Any bugs reported to Brasero project yet?

---

### Post by seragx99 on 2012-06-28
Here's how to burn flac/cue with K3B, no wav converting, i really don't remember if i had to install flac codecs, but i'm positive i got every K3B plugins i could get. 
In short: You only have to choose the "burn image" option on K3B, when the prompt opens, pick the .cue file, burn your cd and voila! 
More detailed instructions here:
[http://ubuntuforums.org/showthread.php?t=209547](http://ubuntuforums.org/showthread.php?t=209547)
i have ubuntu 12.04 pangolin. K3B and its plugins, dependencies etc. are easyly found in Synaptic (i really can't tell if it's availiable in Ubuntu Software center since i really seldom use it, i'm oldschool u know! i like many letters running wild on my screen :guitar:).

---

### Post by oldos2er on 2012-06-28
Old thread closed; please don't bump old threads.

---

