---
title: "Rubyripper mp3 doesn't work"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Dimoutlook on 2008-10-06
Has anyone gotten Rubyripper to encode a cd to mp3 I'v been trying since yesterday to get it to work but have very frustrating time to get it to work here is a short clip from the log



Website: [http://code.google.com/p/rubyripper](http://code.google.com/p/rubyripper)

Cdrom player used to rip:
HL-DT-ST RW/DVD GCC-4244N 1.00
Cdrom offset used: 0

Ripper used: cdparanoia -Z
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-mp3	-> -b 320
(LAME 32bits version 3.97 ([http://www.mp3dev.org/](http://www.mp3dev.org/))
-wav

CDDB INFO

Artist	= Various
Album	= Sports Rock
Year	= 1997
Genre	= Rock
Tracks	= 10

01 - We Will Rock You
02 - Get Down Tonight
03 - Mony Mony
04 - Shout Part 1
05 - Tequila
06 - Bang The Drum All Day
07 - Pick Up The Pieces
08 - Green Onions
09 - Land Of 1000 Dances
10 - Na Na Hey Kiss Him Goodbye

STATUS

Starting to rip track 1, trial #1
Starting to rip track 1, trial #2
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: a11cbd0e5858c31c345cf3ae1c052806

Starting to rip track 2, trial #1
WARNING: Encoding to mp3 exited with an error with track 1!
Starting to rip track 2, trial #2
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 76ce892df34e4a372b20cf98b9c63cf2

Starting to rip track 3, trial #1
WARNING: Encoding to mp3 exited with an error with track 2!
Starting to rip track 3, trial #2
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: e4291a087cb1d0e7a0f16ddc19a3c069

Starting to rip track 4, trial #1
WARNING: Encoding to mp3 exited with an error with track 3!
Starting to rip track 4, trial #2
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 052c158536a28e7e3fc7581807706dcc

Please help me out on this Rubyripper is susposed to be the best

Thanks to all

Dimoutlook

---

### Post by mc4man on 2008-10-07
Stick a k on the end,  ex.  -b 320k
Read lame --help or lame --longhelp or lame --preset help  (in terminal

---

### Post by Dimoutlook on 2008-10-07
Thank you for the reply but still exits with errors from encoding

---

### Post by vanadium on 2008-10-07
You should encode in variable bitrate: optimal file quality at minimum file sizes. CBR 320 is overkill. In Rubyripper, I have the following options for mp3: 
```

-V 2 --vbr-new

```
You should test encoding from the commandline to see eventual error messages. Rip an audio file in WAV format using Rubyripper. Then open the terminal in the directory containing the wav file. Try encoding with the command:
```

lame -V 2 --vbr-new filename.wav

```
This will indicate if and what error occurs.

---

### Post by Dimoutlook on 2008-10-07
Lame seems to work from the cl ok heres the output

laptop:~/mp3/temp$ lame -V 2 --vbr-new track2_1.wav
LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding track2_1.wav to track2_1.wav.mp3
Encoding as 44.1 kHz VBR(q=2) j-stereo MPEG-1 Layer III (ca. 7.3x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  1531/7403   (21%)|    0:03/    0:17|    0:03/    0:18|   11.140x|    0:14 
 32 [  10] **
 40 [   0] 
 48 [   0] 
 56 [   0] 
 64 [   0] 
 80 [   0] 
 96 [   0] 
112 [   2] *
128 [   2] *
160 [ 233] %%%%%%%%%%%%%%%************
192 [ 605] %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%***************************
224 [ 309] %%%%%%%%%%%%%%%%%%%%%%%%***********
256 [ 271] %%%%%%%%%%%%%%*****************
320 [  99] %%%%%%******
----------------02:33----------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  212.0       55.8  44.2        91.7   5.0   3.2
Writing LAME Tag...done
ReplayGain: -2.7dB


does this mean that lame is ok and installed correctly?
 I really appreciate you taking the time to help me get ruby up and working

---

### Post by Dimoutlook on 2008-10-07
I seem to have spoke too soon the file is only 39 sec long and garrbled

---

### Post by Dimoutlook on 2008-10-07
I seem to have spoke too soon the file is only 39 sec long and garbled

---

### Post by mc4man on 2008-10-07
Should work fine.
Are you using 8.04 or 8.10?
Do you have liblame0 installed?

Not that it should matter but what version of rubyripper are you using?

---

### Post by Dimoutlook on 2008-10-07
I'm using 804.1 LTS Synaptic shows liblame0 is installed, The rubyripper is 0.53. is 8.10 any better than 804.1 ? maybe thats why it doesn't want to work on my laptop?

---

### Post by mc4man on 2008-10-07
> is 8.10 any better than 804.1 ? No, not at all (I haven't gotten it to work yet properly in 8.10

Does RR work with other codecs?
You could always try going into home folder and delete the .rubyripper folder and then start it up fresh. (will set everything back to default

---

### Post by Dimoutlook on 2008-10-07
Thanks for that tidbit will try that reset on rr some little peice that I'm missing has to be the problem!

---

### Post by Dimoutlook on 2008-10-07
Ok rips flac and ogg with no problems, wonder why lame is not working will look at the .rr file to see if I find something

---

### Post by vanadium on 2008-10-08
Your previous output shows that lame is working correctly. There is another possibility that I am thinking of. lame allows only specific genres to be added to the tags (type "lame --genre-list" to see the list). Possibly, you retrieved a genre from cddb that is not on the lame list. When RR passes that to lame, lame does not accept it and quits. 

I find this annoying behaviour of lame. I think this behaviour is changed in the most recent version of lame. In the mean time, you will need to change the genre to one of the genres on the list.

---

### Post by Dimoutlook on 2008-10-09
Thank you for the reply to genre-list. I gave up and moved to abcde which is a lot easer to configure with its scripts it was intimidating at first but once  I used it, it works flawlessly.

Thanks again for all your help

Dimoutlook

---

