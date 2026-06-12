---
title: "x264 realtime stderr output parsing"
date: 2010-09-06
forum: Programming Talk
---

### Post by lucipacurar on 2010-09-06
Hi guys,

I'm trying to parse the stderr output of x264 and send it to a web browser using php, mysql and ajax.

My command line looks like this:
```
./x264 --bitrate 300 --preset veryfast -o video.mp4 video.f4v 2>log.txt | ./test.sh
```

and test.sh:

```
#!/bin/bash
while sleep 1; do
	line="$(awk '/frames/' log.txt)";
	echo $line;
	echo ${line:1:5};
done
```

...and the output is:
```
[1.2%] 108/9105 frames, 118.63 fps, 350.51 kb/s, eta 0:01:15 
0.1%]
[4.3%] 396/9105 frames, 202.98 fps, 312.68 kb/s, eta 0:00:42 
0.1%]
[7.5%] 684/9105 frames, 231.92 fps, 316.98 kb/s, eta 0:00:36 
0.1%]
[10.8%] 981/9105 frames, 245.92 fps, 313.49 kb/s, eta 0:00:33 
0.1%]
[14.0%] 1278/9105 frames, 254.81 fps, 308.53 kb/s, eta 0:00:30 
0.1%]
[16.9%] 1539/9105 frames, 256.31 fps, 308.50 kb/s, eta 0:00:29 
0.1%]
[19.6%] 1782/9105 frames, 251.07 fps, 312.16 kb/s, eta 0:00:29 
0.1%]
```

I'm just wondering why does the substring always output 0.1%? I just want to use parts of that output and insert them in a database using a PHP script.

Thank you!

---

### Post by Bachstelze on 2010-09-06
Apparently ${line:1:5} does not do what you think. Why not just use cut? It would also make your script portable.

---

### Post by lucipacurar on 2010-09-06
Thank you for your quick reply!

"cut" behaves the same:
```
#!/bin/bash
while sleep 1; do
	line="$(awk '/frames/' log.txt)";
	echo $line;
	echo $line|cut -d"[" -f2;
	unset line;
done
```

and the output is:
```
[1.1%] 99/9105 frames, 247.28 fps, 314.94 kb/s, eta 0:00:36 
0.1%] 9/9105 frames, 111.75 fps, 317.10 kb/s, eta 0:01:21 
[4.3%] 396/9105 frames, 271.41 fps, 312.68 kb/s, eta 0:00:32 
0.1%] 9/9105 frames, 111.75 fps, 317.10 kb/s, eta 0:01:21 
[7.4%] 675/9105 frames, 273.72 fps, 308.76 kb/s, eta 0:00:30 
0.1%] 9/9105 frames, 111.75 fps, 317.10 kb/s, eta 0:01:21 
[10.5%] 954/9105 frames, 272.13 fps, 316.12 kb/s, eta 0:00:29 
0.1%] 9/9105 frames, 111.75 fps, 317.10 kb/s, eta 0:01:21 
[13.6%] 1242/9105 frames, 272.57 fps, 306.13 kb/s, eta 0:00:28 
0.1%] 9/9105 frames, 111.75 fps, 317.10 kb/s, eta 0:01:21 
[17.0%] 1548/9105 frames, 275.69 fps, 310.82 kb/s, eta 0:00:27 
0.1%] 9/9105 frames, 111.75 fps, 317.10 kb/s, eta 0:01:21 
[20.3%] 1845/9105 frames, 276.65 fps, 313.50 kb/s, eta 0:00:26 
0.1%] 9/9105 frames, 111.75 fps, 317.10 kb/s, eta 0:01:21 

```

LE: It seems that everytime I try to echo out that line the process starts again.

---

### Post by Bachstelze on 2010-09-06
What are you trying to output, exactly?

---

### Post by lucipacurar on 2010-09-06
I don't know if it matters that much, but I just need the progress and ETA.

I tried to use grep on that but there was no output at all. After googling a bit I found out that there is no EOL at the end of that line and grep can't parse it.

---

### Post by Bachstelze on 2010-09-06
In that case, you'll need to first get only the last "line":

```
firas@aoba ~ % cat x264.txt 
[1.2%] 108/9105 frames, 118.63 fps, 350.51 kb/s, eta 0:01:15 [4.3%] 396/9105 frames, 202.98 fps, 312.68 kb/s, eta 0:00:42 [7.5%] 684/9105 frames, 231.92 fps, 316.98 kb/s, eta 0:00:36 [10.8%] 981/9105 frames, 245.92 fps, 313.49 kb/s, eta 0:00:33 [14.0%] 1278/9105 frames, 254.81 fps, 308.53 kb/s, eta 0:00:30 [16.9%] 1539/9105 frames, 256.31 fps, 308.50 kb/s, eta 0:00:29 [19.6%] 1782/9105 frames, 251.07 fps, 312.16 kb/s, eta 0:00:29 
firas@aoba ~ % cat x264.txt | egrep -o "\[[0-9.%]*\] [0-9/]* frames, [0-9.]* fps, [0-9.]* kb/s, eta [0-9:]*" | tail -n 1
[19.6%] 1782/9105 frames, 251.07 fps, 312.16 kb/s, eta 0:00:29

```

---

### Post by soltanis on 2010-09-06
> **Bachstelze said:**
> Why not just use cut? It would also make your script portable.

I'm no expert on portability, but I'm pretty sure awk, along with sh, are the only two interpreters that POSIX mandates a compliant platform to have.

---

### Post by Bachstelze on 2010-09-07
> **soltanis said:**
> I'm no expert on portability, but I'm pretty sure awk, along with sh, are the only two interpreters that POSIX mandates a compliant platform to have.

Nope, cut is standard too :

[http://www.opengroup.org/onlinepubs/9699919799/utilities/cut.html](http://www.opengroup.org/onlinepubs/9699919799/utilities/cut.html)

---

### Post by lucipacurar on 2010-09-20
Thanks for your help. I managed to parse everything I needed except patterns like this:
```
Importing AVC-H264: |===========         | (56/100)
Importing AVC-H264: |===========         | (57/100)
Importing AVC-H264: |===========         | (58/100)
Importing AVC-H264: |===========         | (59/100)
Importing AVC-H264: |============        | (60/100)
Importing AVC-H264: |============        | (61/100)
```

---

### Post by Bachstelze on 2010-09-20
What do you want to "extract" here?

---

### Post by lucipacurar on 2010-09-20
"Importing AVC-H264:" and the progress "(xx/100)"

Thank you!

---

### Post by Bachstelze on 2010-09-20
Then you can use sed to remove the "progress bar":

```
firas@aoba ~ % echo "Importing AVC-H264: |============        | (61/100)" | sed 's/|=*\ *|\ //'
Importing AVC-H264: (61/100)

```

---

### Post by lucipacurar on 2010-09-21
```
AVC-H264 import - frame size 640 x 474 at 29.970 FPS
Importing AVC-H264: |                    | (01/100)
Importing AVC-H264: |                    | (02/100)
Importing AVC-H264: |                    | (03/100)
Importing AVC-H264: |                    | (04/100)
Importing AVC-H264: |=                   | (05/100)
Importing AVC-H264: |=                   | (06/100)
Importing AVC-H264: |=                   | (07/100)
Importing AVC-H264: |=                   | (08/100)
Importing AVC-H264: |=                   | (09/100)
Importing AVC-H264: |==                  | (10/100)
Importing AVC-H264: |==                  | (11/100)
Importing AVC-H264: |==                  | (12/100)
Importing AVC-H264: |==                  | (13/100)
Importing AVC-H264: |==                  | (14/100)
Importing AVC-H264: |===                 | (15/100)
Importing AVC-H264: |===                 | (16/100)
Importing AVC-H264: |===                 | (17/100)
Importing AVC-H264: |===                 | (18/100)
Importing AVC-H264: |===                 | (19/100)
Importing AVC-H264: |====                | (20/100)
Importing AVC-H264: |====                | (21/100)
Importing AVC-H264: |====                | (22/100)
Importing AVC-H264: |====                | (23/100)
Importing AVC-H264: |====                | (24/100)
Importing AVC-H264: |=====               | (25/100)
Importing AVC-H264: |=====               | (26/100)
Importing AVC-H264: |=====               | (27/100)
Importing AVC-H264: |=====               | (28/100)
Importing AVC-H264: |=====               | (29/100)
Importing AVC-H264: |======              | (30/100)
Importing AVC-H264: |======              | (31/100)
Importing AVC-H264: |======              | (32/100)
Importing AVC-H264: |======              | (33/100)
Importing AVC-H264: |======              | (34/100)
Importing AVC-H264: |=======             | (35/100)
Importing AVC-H264: |=======             | (36/100)
Importing AVC-H264: |=======             | (37/100)
Importing AVC-H264: |=======             | (38/100)
Importing AVC-H264: |=======             | (39/100)
Importing AVC-H264: |========            | (40/100)
Importing AVC-H264: |========            | (41/100)
Importing AVC-H264: |========            | (42/100)
Importing AVC-H264: |========            | (43/100)
Importing AVC-H264: |========            | (44/100)
Importing AVC-H264: |=========           | (45/100)
Importing AVC-H264: |=========           | (46/100)
Importing AVC-H264: |=========           | (47/100)
Importing AVC-H264: |=========           | (48/100)
Importing AVC-H264: |=========           | (49/100)
Importing AVC-H264: |==========          | (50/100)
Importing AVC-H264: |==========          | (51/100)
Importing AVC-H264: |==========          | (52/100)
Importing AVC-H264: |==========          | (53/100)
Importing AVC-H264: |==========          | (54/100)
Importing AVC-H264: |===========         | (55/100)
Importing AVC-H264: |===========         | (56/100)
Importing AVC-H264: |===========         | (57/100)
Importing AVC-H264: |===========         | (58/100)
Importing AVC-H264: |===========         | (59/100)
Importing AVC-H264: |============        | (60/100)
Importing AVC-H264: |============        | (61/100)
Importing AVC-H264: |============        | (62/100)
Importing AVC-H264: |============        | (63/100)
Importing AVC-H264: |============        | (64/100)
Importing AVC-H264: |=============       | (65/100)
Importing AVC-H264: |=============       | (66/100)
Importing AVC-H264: |=============       | (67/100)
Importing AVC-H264: |=============       | (68/100)
Importing AVC-H264: |=============       | (69/100)
Importing AVC-H264: |==============      | (70/100)
Importing AVC-H264: |==============      | (71/100)
Importing AVC-H264: |==============      | (72/100)
Importing AVC-H264: |==============      | (73/100)
Importing AVC-H264: |==============      | (74/100)
Importing AVC-H264: |===============     | (75/100)
Importing AVC-H264: |===============     | (76/100)
Importing AVC-H264: |===============     | (77/100)
Importing AVC-H264: |===============     | (78/100)
Importing AVC-H264: |===============     | (79/100)
Importing AVC-H264: |================    | (80/100)
Importing AVC-H264: |================    | (81/100)
Importing AVC-H264: |================    | (82/100)
Importing AVC-H264: |================    | (83/100)
Importing AVC-H264: |================    | (84/100)
Importing AVC-H264: |=================   | (85/100)
Importing AVC-H264: |=================   | (86/100)
Importing AVC-H264: |=================   | (87/100)
Importing AVC-H264: |=================   | (88/100)
Importing AVC-H264: |=================   | (89/100)
Importing AVC-H264: |==================  | (90/100)
Importing AVC-H264: |==================  | (91/100)
Importing AVC-H264: |==================  | (92/100)
Importing AVC-H264: |==================  | (93/100)
Importing AVC-H264: |==================  | (94/100)
Importing AVC-H264: |=================== | (95/100)
Importing AVC-H264: |=================== | (96/100)
Importing AVC-H264: |=================== | (97/100)
Importing AVC-H264: |=================== | (98/100)
Importing AVC-H264: |=================== | (99/100)
                                                          
                                                          
Importing AVC-H264: |=================== | (99/100)
                                                          
Import results: 9105 samples - Slices: 37 I 2904 P 6164 B - 1 SEI - 37 IDR
	Stream uses B-slice references - max frame delay 2
AAC import - sample rate 44100 - MPEG-4 audio - 2 channels
Importing AAC: |                    | (01/100)
Importing AAC: |                    | (02/100)
Importing AAC: |                    | (03/100)
Importing AAC: |                    | (04/100)
Importing AAC: |=                   | (05/100)
Importing AAC: |=                   | (06/100)
Importing AAC: |=                   | (07/100)
Importing AAC: |=                   | (08/100)
Importing AAC: |=                   | (09/100)
Importing AAC: |==                  | (10/100)
Importing AAC: |==                  | (11/100)
Importing AAC: |==                  | (12/100)
Importing AAC: |==                  | (13/100)
Importing AAC: |==                  | (14/100)
Importing AAC: |===                 | (15/100)
Importing AAC: |===                 | (16/100)
Importing AAC: |===                 | (17/100)
Importing AAC: |===                 | (18/100)
Importing AAC: |===                 | (19/100)
Importing AAC: |====                | (20/100)
Importing AAC: |====                | (21/100)
Importing AAC: |====                | (22/100)
Importing AAC: |====                | (23/100)
Importing AAC: |====                | (24/100)
Importing AAC: |=====               | (25/100)
Importing AAC: |=====               | (26/100)
Importing AAC: |=====               | (27/100)
Importing AAC: |=====               | (28/100)
Importing AAC: |=====               | (29/100)
Importing AAC: |======              | (30/100)
Importing AAC: |======              | (31/100)
Importing AAC: |======              | (32/100)
Importing AAC: |======              | (33/100)
Importing AAC: |======              | (34/100)
Importing AAC: |=======             | (35/100)
Importing AAC: |=======             | (36/100)
Importing AAC: |=======             | (37/100)
Importing AAC: |=======             | (38/100)
Importing AAC: |=======             | (39/100)
Importing AAC: |========            | (40/100)
Importing AAC: |========            | (41/100)
Importing AAC: |========            | (42/100)
Importing AAC: |========            | (43/100)
Importing AAC: |========            | (44/100)
Importing AAC: |=========           | (45/100)
Importing AAC: |=========           | (46/100)
Importing AAC: |=========           | (47/100)
Importing AAC: |=========           | (48/100)
Importing AAC: |=========           | (49/100)
Importing AAC: |==========          | (50/100)
Importing AAC: |==========          | (51/100)
Importing AAC: |==========          | (52/100)
Importing AAC: |==========          | (53/100)
Importing AAC: |==========          | (54/100)
Importing AAC: |===========         | (55/100)
Importing AAC: |===========         | (56/100)
Importing AAC: |===========         | (57/100)
Importing AAC: |===========         | (58/100)
Importing AAC: |===========         | (59/100)
Importing AAC: |============        | (60/100)
Importing AAC: |============        | (61/100)
Importing AAC: |============        | (62/100)
Importing AAC: |============        | (63/100)
Importing AAC: |============        | (64/100)
Importing AAC: |=============       | (65/100)
Importing AAC: |=============       | (66/100)
Importing AAC: |=============       | (67/100)
Importing AAC: |=============       | (68/100)
Importing AAC: |=============       | (69/100)
Importing AAC: |==============      | (70/100)
Importing AAC: |==============      | (71/100)
Importing AAC: |==============      | (72/100)
Importing AAC: |==============      | (73/100)
Importing AAC: |==============      | (74/100)
Importing AAC: |===============     | (75/100)
Importing AAC: |===============     | (76/100)
Importing AAC: |===============     | (77/100)
Importing AAC: |===============     | (78/100)
Importing AAC: |===============     | (79/100)
Importing AAC: |================    | (80/100)
Importing AAC: |================    | (81/100)
Importing AAC: |================    | (82/100)
Importing AAC: |================    | (83/100)
Importing AAC: |================    | (84/100)
Importing AAC: |=================   | (85/100)
Importing AAC: |=================   | (86/100)
Importing AAC: |=================   | (87/100)
Importing AAC: |=================   | (88/100)
Importing AAC: |=================   | (89/100)
Importing AAC: |==================  | (90/100)
Importing AAC: |==================  | (91/100)
Importing AAC: |==================  | (92/100)
Importing AAC: |==================  | (93/100)
Importing AAC: |==================  | (94/100)
Importing AAC: |=================== | (95/100)
Importing AAC: |=================== | (96/100)
Importing AAC: |=================== | (97/100)
                                                     
Saving video.mp4: 0.500 secs Interleaving
ISO File Writing: |                    | (01/100)
ISO File Writing: |                    | (02/100)
ISO File Writing: |                    | (03/100)
ISO File Writing: |                    | (04/100)
ISO File Writing: |=                   | (05/100)
ISO File Writing: |=                   | (06/100)
ISO File Writing: |=                   | (07/100)
ISO File Writing: |=                   | (08/100)
ISO File Writing: |=                   | (09/100)
ISO File Writing: |==                  | (10/100)
ISO File Writing: |==                  | (11/100)
ISO File Writing: |==                  | (12/100)
ISO File Writing: |==                  | (13/100)
ISO File Writing: |==                  | (14/100)
ISO File Writing: |===                 | (15/100)
ISO File Writing: |===                 | (16/100)
ISO File Writing: |===                 | (17/100)
ISO File Writing: |===                 | (18/100)
ISO File Writing: |===                 | (19/100)
ISO File Writing: |====                | (20/100)
ISO File Writing: |====                | (21/100)
ISO File Writing: |====                | (22/100)
ISO File Writing: |====                | (23/100)
ISO File Writing: |====                | (24/100)
ISO File Writing: |=====               | (25/100)
ISO File Writing: |=====               | (26/100)
ISO File Writing: |=====               | (27/100)
ISO File Writing: |=====               | (28/100)
ISO File Writing: |=====               | (29/100)
ISO File Writing: |======              | (30/100)
ISO File Writing: |======              | (31/100)
ISO File Writing: |======              | (32/100)
ISO File Writing: |======              | (33/100)
ISO File Writing: |======              | (34/100)
ISO File Writing: |=======             | (35/100)
ISO File Writing: |=======             | (36/100)
ISO File Writing: |=======             | (37/100)
ISO File Writing: |=======             | (38/100)
ISO File Writing: |=======             | (39/100)
ISO File Writing: |========            | (40/100)
ISO File Writing: |========            | (41/100)
ISO File Writing: |========            | (42/100)
ISO File Writing: |========            | (43/100)
ISO File Writing: |========            | (44/100)
ISO File Writing: |=========           | (45/100)
ISO File Writing: |=========           | (46/100)
ISO File Writing: |=========           | (47/100)
ISO File Writing: |=========           | (48/100)
ISO File Writing: |=========           | (49/100)
ISO File Writing: |==========          | (50/100)
ISO File Writing: |==========          | (51/100)
ISO File Writing: |==========          | (52/100)
ISO File Writing: |==========          | (53/100)
ISO File Writing: |==========          | (54/100)
ISO File Writing: |===========         | (55/100)
ISO File Writing: |===========         | (56/100)
ISO File Writing: |===========         | (57/100)
ISO File Writing: |===========         | (58/100)
ISO File Writing: |===========         | (59/100)
ISO File Writing: |============        | (60/100)
ISO File Writing: |============        | (61/100)
ISO File Writing: |============        | (62/100)
ISO File Writing: |============        | (63/100)
ISO File Writing: |============        | (64/100)
ISO File Writing: |=============       | (65/100)
ISO File Writing: |=============       | (66/100)
ISO File Writing: |=============       | (67/100)
ISO File Writing: |=============       | (68/100)
ISO File Writing: |=============       | (69/100)
ISO File Writing: |==============      | (70/100)
ISO File Writing: |==============      | (71/100)
ISO File Writing: |==============      | (72/100)
ISO File Writing: |==============      | (73/100)
ISO File Writing: |==============      | (74/100)
ISO File Writing: |===============     | (75/100)
ISO File Writing: |===============     | (76/100)
ISO File Writing: |===============     | (77/100)
ISO File Writing: |===============     | (78/100)
ISO File Writing: |===============     | (79/100)
ISO File Writing: |================    | (80/100)
ISO File Writing: |================    | (81/100)
ISO File Writing: |================    | (82/100)
ISO File Writing: |================    | (83/100)
ISO File Writing: |================    | (84/100)
ISO File Writing: |=================   | (85/100)
ISO File Writing: |=================   | (86/100)
ISO File Writing: |=================   | (87/100)
ISO File Writing: |=================   | (88/100)
ISO File Writing: |=================   | (89/100)
ISO File Writing: |==================  | (90/100)
ISO File Writing: |==================  | (91/100)
ISO File Writing: |==================  | (92/100)
ISO File Writing: |==================  | (93/100)
ISO File Writing: |==================  | (94/100)
ISO File Writing: |=================== | (95/100)
ISO File Writing: |=================== | (96/100)
ISO File Writing: |=================== | (97/100)
ISO File Writing: |=================== | (98/100)
ISO File Writing: |=================== | (99/100)                                                        

```

This is the output of MP4Box I need to parse in realtime. This is also a text file coming out the same way as the other log of x264 in this thread.

The output of the sed command running in the script from the first post is this one:
```
AVC-H264 import - frame size 640 x 474 at 29.970 FPS Importing AVC-H264: (01/100Import results: 9105 samples - Slices: 37 I 2904 P 6164 B - 1 SEI - 37 IDR Stream uses B-slice references - max frame delay 2 AAC import - sample rate 44100 - M SO File Writing: |=================== | (99/100)e Writing: (01/100)
AVC-H264 import - frame size 640 x 474 at 29.970 FPS Importing AVC-H264: (01/100Import results: 9105 samples - Slices: 37 I 2904 P 6164 B - 1 SEI - 37 IDR Stream uses B-slice references - max frame delay 2 AAC import - sample rate 44100 - M SO File Writing: |=================== | (99/100)e Writing: (01/100)
AVC-H264 import - frame size 640 x 474 at 29.970 FPS Importing AVC-H264: (01/100Import results: 9105 samples - Slices: 37 I 2904 P 6164 B - 1 SEI - 37 IDR Stream uses B-slice references - max frame delay 2 AAC import - sample rate 44100 - M SO File Writing: |=================== | (99/100)e Writing: (01/100)
AVC-H264 import - frame size 640 x 474 at 29.970 FPS Importing AVC-H264: (01/100Import results: 9105 samples - Slices: 37 I 2904 P 6164 B - 1 SEI - 37 IDR Stream uses B-slice references - max frame delay 2 AAC import - sample rate 44100 - M SO File Writing: |=================== | (99/100)e Writing: (01/100)
AVC-H264 import - frame size 640 x 474 at 29.970 FPS Importing AVC-H264: (01/100Import results: 9105 samples - Slices: 37 I 2904 P 6164 B - 1 SEI - 37 IDR Stream uses B-slice references - max frame delay 2 AAC import - sample rate 44100 - M SO File Writing: |=================== | (99/100)e Writing: (01/100)
AVC-H264 import - frame size 640 x 474 at 29.970 FPS Importing AVC-H264: (01/100Import results: 9105 samples - Slices: 37 I 2904 P 6164 B - 1 SEI - 37 IDR Stream uses B-slice references - max frame delay 2 AAC import - sample rate 44100 - M SO File Writing: |=================== | (99/100)e Writing: (01/100)
```

Thank you again for your quick reply.

---

