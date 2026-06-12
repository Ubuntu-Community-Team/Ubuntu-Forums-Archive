---
title: "Parsing time values for video trimming"
date: 2011-07-02
forum: Programming Talk
---

### Post by FakeOutdoorsman on 2011-07-02
I'm capturing video from Hi8 tapes with a Sony GV-D200 to DV files. The video is analog, and the Sony deck records the whole tape including blank sections. These blank sections show up as a neutral, solid gray color in the video. Generally, the videos in this set have an average of 7 seconds blank, 25 minutes of actual footage, and then the rest of the video is blank (up to 95 minutes).

FFmpeg with the *blackframe* filter can output which frames are potentially blank. The two values for this filter are "% of frame which is black:threshold (or how dark it is)":
```
$ ffmpeg -threads 8 -i input.dv -vf blackframe=100:84 -an -f null -
```
A condensed version of this output:
```
[blackframe @ 0x20ad8e0] frame:1 pblack:100 pos:120000 pts:33367 t:0.033367
[blackframe @ 0x20ad8e0] frame:2 pblack:100 pos:240000 pts:66733 t:0.066733
[blackframe @ 0x20ad8e0] frame:3 pblack:100 pos:360000 pts:100100 t:0.100100
[blackframe @ 0x20ad8e0] frame:201 pblack:100 pos:24120000 pts:6706700 t:6.706700
[blackframe @ 0x20ad8e0] frame:202 pblack:100 pos:24240000 pts:6740067 t:6.740067
[blackframe @ 0x20ad8e0] frame:203 pblack:100 pos:24360000 pts:6773433 t:**[color=red]6.773433[/color]**
frame=  451 fps=  0 q=0.0 size=      -0kB time=00:00:14.97 bitrate=  -0.0kbits/s
frame=  878 fps=874 q=0.0 size=      -0kB time=00:00:29.22 bitrate=  -0.0kbits/s
frame= 1292 fps=858 q=0.0 size=      -0kB time=00:00:43.03 bitrate=  -0.0kbits/s
frame=57319 fps=800 q=0.0 size=      -0kB time=00:31:52.38 bitrate=  -0.0kbits/s
frame=57722 fps=800 q=0.0 size=      -0kB time=00:32:05.83 bitrate=  -0.0kbits/s
frame=58130 fps=800 q=0.0 size=      -0kB time=00:32:19.44 bitrate=  -0.0kbits/s
[blackframe @ 0x20ad8e0] frame:58408 pblack:100 pos:7008960000 pts:1948880267 t:**[color=red]1948.880267[/color]**
[blackframe @ 0x20ad8e0] frame:58409 pblack:100 pos:7009080000 pts:1948913633 t:1948.913633
[blackframe @ 0x20ad8e0] frame:58410 pblack:100 pos:7009200000 pts:1948947000 t:1948.947000
[blackframe @ 0x20ad8e0] frame:58411 pblack:100 pos:7009320000 pts:1948980367 t:1948.980367
[blackframe @ 0x20ad8e0] frame:58412 pblack:100 pos:7009440000 pts:1949013733 t:1949.013733
[blackframe @ 0x20ad8e0] frame:58413 pblack:100 pos:7009560000 pts:1949047100 t:1949.047100
[blackframe @ 0x20ad8e0] frame:58414 pblack:100 pos:7009680000 pts:1949080467 t:1949.080467
[blackframe @ 0x20ad8e0] frame:58415 pblack:100 pos:7009800000 pts:1949113833 t:1949.113833
[blackframe @ 0x20ad8e0] frame:58416 pblack:100 pos:7009920000 pts:1949147200 t:1949.147200
[blackframe @ 0x20ad8e0] frame:58417 pblack:100 pos:7010040000 pts:1949180567 t:1949.180567
[blackframe @ 0x20ad8e0] frame:58573 pblack:100 pos:7028760000 pts:1954385767 t:1954.385767
[blackframe @ 0x20ad8e0] frame:58574 pblack:100 pos:7028880000 pts:1954419133 t:1954.419133
frame=58575 fps=801 q=0.0 size=      -0kB time=00:32:34.29 bitrate=  -0.0kbits/s    
[blackframe @ 0x20ad8e0] frame:58575 pblack:100 pos:7029000000 pts:1954452500 t:1954.452500
[blackframe @ 0x20ad8e0] frame:58576 pblack:100 pos:7029120000 pts:1954485867 t:1954.485867
[blackframe @ 0x20ad8e0] frame:58577 pblack:100 pos:7029240000 pts:1954519233 t:1954.519233
[blackframe @ 0x20ad8e0] frame:58578 pblack:100 pos:7029360000 pts:1954552600 t:1954.552600
[blackframe @ 0x20ad8e0] frame:58579 pblack:100 pos:7029480000 pts:1954585967 t:1954.585967
[blackframe @ 0x20ad8e0] frame:59121 pblack:100 pos:7094520000 pts:1972670700 t:1972.670700
[blackframe @ 0x20ad8e0] frame:59122 pblack:100 pos:7094640000 pts:1972704067 t:1972.704067
frame=59123 fps=803 q=0.0 size=      -0kB time=00:32:52.57 bitrate=  -0.0kbits/s    
[blackframe @ 0x20ad8e0] frame:59123 pblack:100 pos:7094760000 pts:1972737433 t:1972.737433
[blackframe @ 0x20ad8e0] frame:59124 pblack:100 pos:7094880000 pts:1972770800 t:1972.770800
[blackframe @ 0x20ad8e0] frame:59125 pblack:100 pos:7095000000 pts:1972804167 t:1972.804167
[blackframe @ 0x20ad8e0] frame:59126 pblack:100 pos:7095120000 pts:1972837533 t:1972.837533
[blackframe @ 0x20ad8e0] frame:59127 pblack:100 pos:7095240000 pts:1972870900 t:1972.870900
[blackframe @ 0x20ad8e0] frame:59128 pblack:100 pos:7095360000 pts:1972904267 t:1972.904267
```
I'd like the values that I marked in bold red.  With these values I can have FFmpeg automatically trim the blank frames by skipping the first 6.773433 seconds and creating an output with a duration of 1948.880267-6.773433=~1942 seconds. I think awk is the tool to use here to get these two values, but that's about as far as I got. Any ideas?

Also, the second value is most important. I can live without the first if that makes things more realistic to achieve.

---

### Post by Arndt on 2011-07-02
> **FakeOutdoorsman said:**
> I'm capturing video from Hi8 tapes with a Sony GV-D200 to DV files. The video is analog, and the Sony deck records the whole tape including blank sections. These blank sections show up as a neutral, solid gray color in the video. Generally, the videos in this set have an average of 7 seconds blank, 25 minutes of actual footage, and then the rest of the video is blank (up to 95 minutes).

FFmpeg with the *blackframe* filter can output which frames are potentially blank. The two values for this filter are "% of frame which is black:threshold (or how dark it is)":
```
$ ffmpeg -threads 8 -i input.dv -vf blackframe=100:84 -an -f null -
```
A condensed version of this output:
```
[blackframe @ 0x20ad8e0] frame:1 pblack:100 pos:120000 pts:33367 t:0.033367
[blackframe @ 0x20ad8e0] frame:2 pblack:100 pos:240000 pts:66733 t:0.066733
[blackframe @ 0x20ad8e0] frame:3 pblack:100 pos:360000 pts:100100 t:0.100100
[blackframe @ 0x20ad8e0] frame:201 pblack:100 pos:24120000 pts:6706700 t:6.706700
[blackframe @ 0x20ad8e0] frame:202 pblack:100 pos:24240000 pts:6740067 t:6.740067
[blackframe @ 0x20ad8e0] frame:203 pblack:100 pos:24360000 pts:6773433 t:**[color=red]6.773433[/color]**
frame=  451 fps=  0 q=0.0 size=      -0kB time=00:00:14.97 bitrate=  -0.0kbits/s
frame=  878 fps=874 q=0.0 size=      -0kB time=00:00:29.22 bitrate=  -0.0kbits/s
frame= 1292 fps=858 q=0.0 size=      -0kB time=00:00:43.03 bitrate=  -0.0kbits/s
frame=57319 fps=800 q=0.0 size=      -0kB time=00:31:52.38 bitrate=  -0.0kbits/s
frame=57722 fps=800 q=0.0 size=      -0kB time=00:32:05.83 bitrate=  -0.0kbits/s
frame=58130 fps=800 q=0.0 size=      -0kB time=00:32:19.44 bitrate=  -0.0kbits/s
[blackframe @ 0x20ad8e0] frame:58408 pblack:100 pos:7008960000 pts:1948880267 t:**[color=red]1948.880267[/color]**
[blackframe @ 0x20ad8e0] frame:58409 pblack:100 pos:7009080000 pts:1948913633 t:1948.913633
[blackframe @ 0x20ad8e0] frame:58410 pblack:100 pos:7009200000 pts:1948947000 t:1948.947000
[blackframe @ 0x20ad8e0] frame:58411 pblack:100 pos:7009320000 pts:1948980367 t:1948.980367
[blackframe @ 0x20ad8e0] frame:58412 pblack:100 pos:7009440000 pts:1949013733 t:1949.013733
[blackframe @ 0x20ad8e0] frame:58413 pblack:100 pos:7009560000 pts:1949047100 t:1949.047100
[blackframe @ 0x20ad8e0] frame:58414 pblack:100 pos:7009680000 pts:1949080467 t:1949.080467
[blackframe @ 0x20ad8e0] frame:58415 pblack:100 pos:7009800000 pts:1949113833 t:1949.113833
[blackframe @ 0x20ad8e0] frame:58416 pblack:100 pos:7009920000 pts:1949147200 t:1949.147200
[blackframe @ 0x20ad8e0] frame:58417 pblack:100 pos:7010040000 pts:1949180567 t:1949.180567
[blackframe @ 0x20ad8e0] frame:58573 pblack:100 pos:7028760000 pts:1954385767 t:1954.385767
[blackframe @ 0x20ad8e0] frame:58574 pblack:100 pos:7028880000 pts:1954419133 t:1954.419133
frame=58575 fps=801 q=0.0 size=      -0kB time=00:32:34.29 bitrate=  -0.0kbits/s    
[blackframe @ 0x20ad8e0] frame:58575 pblack:100 pos:7029000000 pts:1954452500 t:1954.452500
[blackframe @ 0x20ad8e0] frame:58576 pblack:100 pos:7029120000 pts:1954485867 t:1954.485867
[blackframe @ 0x20ad8e0] frame:58577 pblack:100 pos:7029240000 pts:1954519233 t:1954.519233
[blackframe @ 0x20ad8e0] frame:58578 pblack:100 pos:7029360000 pts:1954552600 t:1954.552600
[blackframe @ 0x20ad8e0] frame:58579 pblack:100 pos:7029480000 pts:1954585967 t:1954.585967
[blackframe @ 0x20ad8e0] frame:59121 pblack:100 pos:7094520000 pts:1972670700 t:1972.670700
[blackframe @ 0x20ad8e0] frame:59122 pblack:100 pos:7094640000 pts:1972704067 t:1972.704067
frame=59123 fps=803 q=0.0 size=      -0kB time=00:32:52.57 bitrate=  -0.0kbits/s    
[blackframe @ 0x20ad8e0] frame:59123 pblack:100 pos:7094760000 pts:1972737433 t:1972.737433
[blackframe @ 0x20ad8e0] frame:59124 pblack:100 pos:7094880000 pts:1972770800 t:1972.770800
[blackframe @ 0x20ad8e0] frame:59125 pblack:100 pos:7095000000 pts:1972804167 t:1972.804167
[blackframe @ 0x20ad8e0] frame:59126 pblack:100 pos:7095120000 pts:1972837533 t:1972.837533
[blackframe @ 0x20ad8e0] frame:59127 pblack:100 pos:7095240000 pts:1972870900 t:1972.870900
[blackframe @ 0x20ad8e0] frame:59128 pblack:100 pos:7095360000 pts:1972904267 t:1972.904267
```
I'd like the values that I marked in bold red.  With these values I can have FFmpeg automatically trim the blank frames by skipping the first 6.773433 seconds and creating an output with a duration of 1948.880267-6.773433=~1942 seconds. I think awk is the tool to use here to get these two values, but that's about as far as I got. Any ideas?

Also, the second value is most important. I can live without the first if that makes things more realistic to achieve.

I find python useful for this kind of thing. Does this do what you want?

With your data (which I put in mpeg.dat):

```
$ python mpeg.py <mpeg.dat 
6.773433 1948.880267 1942.106834
```

mpeg.py:

```
import sys
import re

frameseen = False

for line in sys.stdin:
    m = re.search("^frame=", line)
    if m:
        frameseen = True
        continue

    m = re.search(" t:([0-9.]+)$", line)
    if m:
        if not frameseen:
            t0 = float(m.group(1))
        else:
            t1 = float(m.group(1))
            print "%f %f %f" % (t0, t1, t1-t0)
            sys.exit(0)

```

---

### Post by FakeOutdoorsman on 2011-07-02
Thanks for the reply. Yes, your example does work with the samples I've tested so far:
```
$ python2 mpeg.py <2001_5401_1_A
6.206200 2359.256900 2353.050700
```
Python 3.2 on the Arch Linux machine doesn't like it though:
```
$ python mpeg.py <2001_5400_1_A
  File "mpeg.py", line 18
    print "%f %f %f" % (t0, t1, t1-t0)
                   ^
SyntaxError: invalid syntax
```
No big deal because python 2 is also available. I must admit that I'm fairly python ignorant and I only have a little experience with bash scripting. My simple method of calculating the duration:
```
duration=$(echo "$lastblackframe"-"$offset" | bc)
```

---

### Post by FakeOutdoorsman on 2011-07-02
> **FakeOutdoorsman said:**
> Python 3.2 on the Arch Linux machine doesn't like it though

Allow me to talk to myself. Apparently python 3 has a syntax change for *print*.
```
print ("%f %f %f" % (t0, t1, t1-t0))
```

---

### Post by Arndt on 2011-07-03
> **FakeOutdoorsman said:**
> Allow me to talk to myself. Apparently python 3 has a syntax change for *print*.
```
print ("%f %f %f" % (t0, t1, t1-t0))
```

Yes, that's one of the changes made in python 3 - they are mentioned here now and then. I haven't encountered python 3 myself yet, so I keep forgetting those changes.

---

