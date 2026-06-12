---
title: "xvidenc syntax"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Langstracht on 2012-10-24
Apologies for the inanity of this ... but I am not able to figure out the syntax (nor can I find it anywhere) for encoding a file.

xvidenc figures my filename is an option ... or a preset.

Can anyone help.

TIA

---

### Post by andrew.46 on 2013-04-23
The options can all be seen with:

```

xvidenc -help

```

There is an example in there to start with:

```

xvidenc -2p -p ehq

```

which might provide a suitable starting point. The file or dvd is then selected interactively.

---

### Post by Langstracht on 2013-04-24
Thank you for your help.

It now looks like it will work.  But ... the input has me baffled.

If I try to encode a DVD I get the message "No such block device" whatever I input.

And if I try to encode a VIDEO_TS I get the message "Directory not specified or does not exist" regardless of what "path" I type in.

Can you explain what's missing or what's required?

Thanks in anticipation.

---

### Post by andrew.46 on 2013-04-24
Concerning the DVD you should be able to test as follows:

```

andrew@skamandros~$ **[COLOR="#FF0000"]xvidenc -scan [/COLOR]**

Would you like to scan a video file or a DVD? [file/vcd/dvd]: dvd

-> Found device: /dev/sr1
-> Found device: /dev/sr0
-> Found symbolic link to DVD device: /dev/dvd -> sr0
-> Found symbolic link to DVD device: /dev/dvd0 -> sr0
-> Found symbolic link to DVD device: /dev/dvd1 -> sr1
-> Found symbolic link to DVD device: /dev/dvdr -> sr0
-> Found symbolic link to DVD device: /dev/dvdr0 -> sr0
-> Found symbolic link to DVD device: /dev/dvdr1 -> sr1
-> Found symbolic link to DVD device: /dev/dvdrw -> sr0
-> Found symbolic link to DVD device: /dev/dvdrw0 -> sr0
-> Found symbolic link to DVD device: /dev/dvdrw1 -> sr1
-> Found symbolic link to DVD device: /dev/dvdwriter -> sr0
-> Found symbolic link to DVD device: /dev/dvdwriter0 -> sr0
-> Found symbolic link to DVD device: /dev/dvdwriter1 -> sr1

Specify the DVD Device [default is /dev/dvd]: 

```

and on my system the field should be */dev/dvd *, it may be different on yours...

---

### Post by Langstracht on 2013-04-24
Thanks.  

It shows up using "xvidenc -scan *".


However it does NOT show up with "xvidenc -scan" - which is what I had already used.


Thanks again.

---

### Post by andrew.46 on 2013-04-24
So it works for you now?

---

### Post by Langstracht on 2013-04-25
Well ... yes and no.

The first dvd I encoded produced no audio.

I wasn't sure if this was perhaps "my fault" ... chose an incorrect option or whatever.

So I tried again with a different dvd ... and it was fine.

Went back to the first, "carefully" ... and got the same "no audio" result.

What does this mean?  I haven't a clue.

---

### Post by andrew.46 on 2013-04-25
Try the following command and see if you need to add a few libraries:

```

andrew@skamandros~$ [B][COLOR="#FF0000"]xvidenc -sc
[/COLOR][/B]
-> Checking for 'MPlayer'..................... OK
-> Checking for 'MEncoder'.................... OK
-> Xvid video support in MEncoder............. YES
-> AAC (FAAC) audio support in MEncoder....... YES
-> MP3 (LAME) audio support in MEncoder....... YES
-> AC3 (lavc) audio support in MEncoder....... YES
-> PCM audio support in MEncoder.............. YES

-> Checking for 'bc'.......................... OK
-> Checking for 'pv'.......................... FAILED! [no support for DVD ISO dumps]
-> Checking for 'dd'.......................... OK
-> Checking for 'neroAacEnc'.................. OK
-> Checking for 'aacplusenc'.................. FAILED! [no support for AAC+ audio]
-> Checking for 'oggenc'...................... OK
-> Checking for 'flac'........................ OK
-> Checking for 'less'........................ OK
-> Checking for 'lsdvd'....................... OK
-> Checking for 'dvdxchap' (from ogmtools).... FAILED! [no support for DVD chapters export]
-> Checking for 'mkvmerge' (from mkvtoolnix).. OK
-> Checking for 'ogmmerge' (from ogmtools).... FAILED! [no support for the OGM container]
-> Checking for 'MP4Box' (from gpac).......... OK

If you have installed a required program but the script
can't find it, run 'xvidenc -r' to reset the config file.


```

If you have to add a couple of libraries don't forget the *xvidenc -r *command to reset the config file...

---

### Post by Langstracht on 2013-04-25
I'll give that a try.  Thanks!

That sad, I am REALLY surprised to learn that a missing library doesn't result in an error message though.

Or is it possible that something else is amiss - some cunning code on the DVD for instance ...

---

### Post by Langstracht on 2013-04-25
O.k.  Done.

Everything "o.k." except:

-> Checking for 'neroAacEnc'.................. FAILED! [no support for AAC+ audio]
-> Checking for 'aacplusenc'.................. FAILED! [no support for AAC+ audio]

One of which I see you have too.  And one which you don't.

So!  This leads me to 2 questions.  1 - is it possible/likely that it (aacplusenc) is the cause of the no audio problem?  2 - what can/do I do about it.

Thanks in anticipation yet again.

---

### Post by andrew.46 on 2013-04-25
Does seem a little odd. MP3 should be a safe bet then with xvidenc but do you have playback with mp3 files with media players like vlc on your setup? This is often missing by default in Ubuntu.

---

### Post by Langstracht on 2013-04-26
Yes I regularly play mp3 files.  

With vlc.  And with Banshee and Mplayer.

---

### Post by andrew.46 on 2013-04-26
Hmmm.... in that case I am not entirely sure. My last thought is that pehaps you could try the following:

```

xvidenc -r

```

This has the following actions:

```

-r     Reset configuration file. As of version 7.9.5, xvidenc  uses
              a  configuration  file  which contains the paths to the pro-
              grams needed for its correct operation.  This  option  tells
              the  script to remove and recreate the config file using the
              default values. It can be used to restore the original  val-
              ues  of the config file in case the user has modified it and
              wants to get rid of those modifications.  It  is  also  used
              for resetting the config file in case the user has installed
              a required program after xvidenc has  generated  its  config
              file.  If this is the case, the config file will not contain
              the path to the newly installed program so one has to  reset
              the  file  in  order  to find it. This is because the config
              file is generated/updated only once: if it's  not  available
              on the user's system and during config version updates.  The
              configuration  file  is  located   in   /home/username/.xvi-
              denc/config

```

and if that does not work I am afraid that I am out of ideas :(.

---

### Post by Langstracht on 2013-04-26
I knew about the command (thanks to you it has to be said) but since I haven't added or changed anything I didn't think there would be any need to use it.

However I'll give it a try and see how we go.

It's too bad that there's no way of judging/assessing the success of a session without having to wait for it to end and see (hear!) what you've got.

That said, can I assume that the quality levels will not change anything other than the quality.  That is, if I were to run 1 pass very low quality and got sound, would you expect that I would also get sound at "ehq". Or if not then not at the higher level either.  If so then I can get a handle on the outcome a bit quicker.

Thanks again.

---

