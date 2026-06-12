---
title: "script to convert, delete original, compress and move"
date: 2012-12-26
forum: Programming Talk
---

### Post by tsitras on 2012-12-26
hi. please some help since i am stuck in creating a bash script that has several parameters.

i am looking to create a script to run periodically on my box to:
-convert wav to mp3
-delete the original wav files that has been converted
-compress the files to a new file by data_time
-move the compressed file to a new folder/or NFS mount

up to now i am in the 
#!/bin/sh
# name of this script: wav2mp3.sh
# wav to mp3

for i in *.wav; do
if [ -e "$i" ]; then
file=`basename "$i" .wav`
lame -h -b 192 "$i" "$file.mp3"
fi
done



but it does not seem to do anything.

---

### Post by SuperCamel on 2012-12-26
Is it possible LAME isn't installed?

---

### Post by fdrake on 2012-12-26
probably . the scripts should be ok
```

sudo apt-get install lame

```
also remember that the screept needs to be in the same dir of the wav files!

---

### Post by tsitras on 2012-12-27
i do have lame installed. the script is in the same dir as the files.

---

### Post by r-senior on 2012-12-27
Assuming you are running this on an Ubuntu derivative, you should be aware that you are probably not writing a bash script because you have this line at the top:

> ```
#!/bin/sh
```

Usually /bin/sh is linked to dash, the Debian Almquist Shell. If you are expecting to use bash builtins and idioms, you need /bin/bash at the top of the file. Otherwise make sure you refer to the manual page and resources for dash.

As far as the script goes, it works for me unmodified:

```

$ ls
test.sh  test.wav
$ ./test.sh
LAME 3.99.3 64bits (http://lame.sf.net)
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding test.wav to test.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III (7.3x) 192 kbps qval=2
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  4947/4947  (100%)|    0:11/    0:11|    0:11/    0:11|   11.160x|    0:00 
-----------------------------------------------------------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  192.0       40.4  59.6        96.7   1.7   1.7
Writing LAME Tag...done
ReplayGain: -5.1dB
$ ls
test.mp3  test.sh  test.wav

```

Are you able to run the lame command without the script?

How are you running the script? Is it possible you are confusing it with something else in your path? Make sure you prefix with "./" when you run it to make sure you are running the one in the current directory.

---

### Post by fdrake on 2012-12-27
did you check the permissions to execute the script? What error does it gives you when you run it?

---

### Post by tsitras on 2012-12-27
dear r-senior is it possible to have the script complete with the changes you proposed?

---

### Post by r-senior on 2012-12-27
I didn't change it -- it ran as it was and worked OK.

All I did was paste it into a new file (called test.sh), save it on my desktop, copy a wav file into the same directory, then:

```
$ sudo apt-get install lame
$ chmod +x test.sh
$ ./test.sh
```

---

### Post by ofnuts on 2012-12-27
```

#!/bin/sh
# name of this script: wav2mp3.sh
# wav to mp3

for i in *.wav; do
if [ -e "$i" ]; then
file=`basename "$i" .wav`
lame -h -b 192 "$i" "$file.mp3"
fi
done

```I'm curious to know why you test for the file (if [[ -e ...]]) because the 'for i in *.wav' can only build a list of files that exist.... unless you expect some of these files to be deleted while the first ones are converted?

---

