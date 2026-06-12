---
title: "Need help opening .LVF files"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by xJ3CzNb on 2013-08-09
I have cctv which has recorded an interaction with the police....I downloaded off the cctv recorder to memory stick but cannot open the .lvf files....my computer does not have any suggestions, AND IREALLY NEED THIS FOOTAGE, please can anyone tell me how to do this????

---

### Post by xtremesupremacy3 on 2013-08-09
According to a Google search, your best bet is to convert this to another format using ffmpeg.
The command you would need to use is (in the terminal):

ffmpeg -i file.lvf out.wmv

This is the source for the answer: [http://ffmpeg.org/pipermail/ffmpeg-user/2012-August/008966.html](http://ffmpeg.org/pipermail/ffmpeg-user/2012-August/008966.html)

---

### Post by xJ3CzNb on 2013-08-09
Thanks Xtreme...I just tried that and got this..
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
file.lvf: No such file or directory
I then tried to do the sudo ap thing for the avconv and that said....
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package avconv

---

### Post by xtremesupremacy3 on 2013-08-09
I'm sorry, I should have explained a little more, my fault.

The first thing we want to do is locate the file using the terminal.
So let's assume your lvf file is located in the Downloads folder. Open a terminal and type in:
'cd ~/Downloads'

The cd will change directory, and the ~ means your home directory (please note it's case-sensitive).
If the file is on the Desktop you would put 'cd ~/Desktop' that kind of thing.
Once you are in the directory it is located, you would enter the command I gave but replacing 'file.lvf' with the name of the file. For instance, if the file is called abc.lvf then you would type 'ffmpeg -i abc.lvf out.wmv'.
Once that completes, you should have a file called out.wmv too.
I think the deprecated is just information to inform you it will be replaced soon, but should still work.

Good luck, and let me know if it worked

---

### Post by xJ3CzNb on 2013-08-09
Don't be sorry...I thank you for your time and effort for a newb like myself (an OLD newb at that), things don't come easy at my age and though what you have written all seems 'perfect' sense ...this is what I got....
indy@indy-F5RL:~$ cd~Kingston
cd~Kingston: command not found
indy@indy-F5RL:~$ cd~desktop
cd~desktop: command not found
indy@indy-F5RL:~$ cd/desktop
bash: cd/desktop: No such file or directory
indy@indy-F5RL:~$ cd~/Desktop
bash: cd~/Desktop: No such file or directory
indy@indy-F5RL:~$ cd~/home
bash: cd~/home: No such file or directory
indy@indy-F5RL:~$ cd~
No command 'cd~' found, did you mean:
 Command 'cde' from package 'cde' (universe)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdi' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
 Command 'cd5' from package 'cd5' (universe)
cd~: command not found

My files are still on a memory stick...the Kingston mentioned above...I did transfer (copied one) to the desktop to try using your 'quoted' command line but as you can see...(shrugs shoulders and shakes head in resignation to the inevitable)...I then tried to get a file into the home folder...with similar results...

 I am running Ubuntu 12.10 (perforated penguin or something like that) if that helps you at all?

---

### Post by xJ3CzNb on 2013-08-09
Update....
tried putting the file title in and ....(shock horror) MY TERMINAL 'spoke' to me!!!!...lol

ndy@indy-F5RL:~$ ffmpeg -i 0220130718190018.lvf out wmv
ffmpeg version 0.8.6-6:0.8.6-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:07:34 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[h264 @ 0x8dc80e0] max_analyze_duration reached
[h264 @ 0x8dc80e0] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 2400000.00 (2400000/1) -> 25.00 (25/1)
Input #0, h264, from '0220130718190018.lvf':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: h264 (Baseline), yuv420p, 352x288, 25 fps, 25 tbr, 1200k tbn, 2400k tbc
Unable to find a suitable output format for 'out'

Que?????

---

### Post by xtremesupremacy3 on 2013-08-09
Ah, It's on a USB stick.
That makes sense, could you try this:

'cd /media/' (that's a space after the cd)

Once there, type the command 'ls'
This should show you what's in the directory, if it's empty then the USB is not located there, but my thoughts is that you should see something like KINGSTON.
If that is the case then type 'cd KINGSTON' (replacing KINGSTON with whatever it lists there and remember that it is case sensitive).
Once that is done, typing 'ls' should list all the files on the USB stick.

Please note that if the files are in a subdirectory, you can type 'cd <SUBDIRECTORY>' replacing <SUBDIRECTORY> with the name of the subdirectory.
Once inside the directory where all the lvf files are located you can try the command again.

Just an additional note, if there are multiple lvf files, then you may be better of with the following command that will convert ALL the lvf files:

'for f in *.lvf; do ffmpeg -i $f $f.wmv; done' (without quotes in the directory of the lvf files)

The 'for f in *.lvf' part of this command tells bash to run through all files that end in .lvf
Then the command I gave earlier is carried out, replacing $f with the lvf file it is currently working with, and keeps looping through each file that ends in lvf.
Then 'done' will be carried out once all .lvf files have been converted.

This will copy the names of each of the lvf file, but converted and ending in .wmv

But that will only work in the directory where the lvf files are located.

Also, the reason why the terminal said it wouldn't work is due to the space between out and wmv. It should be 'out.wmv' (with a dot)

---

### Post by xJ3CzNb on 2013-08-09
Errrrmm..I think it is the 'empty' option you mentioned...;)

dy@indy-F5RL:~$ cd /media/
indy@indy-F5RL:/media$ ls
indy
indy@indy-F5RL:/media$ cd <indy>
bash: syntax error near unexpected token `newline'
indy@indy-F5RL:/media$ cd<indy>
bash: syntax error near unexpected token `newline'
indy@indy-F5RL:/media$ indy ls
No command 'indy' found, did you mean:
 Command 'xindy' from package 'xindy' (universe)
indy: command not found
indy@indy-F5RL:/media$ cd /Desktop/
bash: cd: /Desktop/: No such file or directory
indy@indy-F5RL:/media$ cd KINGSTON
bash: cd: KINGSTON: No such file or directory
indy@indy-F5RL:/media$ 

I AM trying.....honest...

---

### Post by xtremesupremacy3 on 2013-08-09
It's fine, don't worry, it took me some time to get used to it too.

Let's make things a little easier.

lets install a little addon that makes things simpler.

in the terminal, type 'sudo apt-get install nautilus-open-terminal'
After that's finished installing, log out, and back in again for the changes to take effect.

Once you have logged back in, open the file manager and just go to the directory where the files are located.
Once there, right-click on some empty space and there should be an option called 'Open in Terminal', hit that and the terminal should be opened in the directory we need to be in.

Once there, if you only have a single file to convert, just type: 'ffmpeg -i <INPUT FILE>.lvf out.wmv' replacing <INPUT FILE> with the name of the file.
Or for multiple files, type: 'for f in *.lvf; do ffmpeg -i $f $f.wmv; done' (you can also copy and paste this one, just make sure you don't copy the single-quotes.

That might just make it a little easier ;)

---

### Post by xJ3CzNb on 2013-08-09
I am wetting myself laughing here....ok I shall do as you direct....as wossisname said to Captain Scott of the Antarctic as he left the tent..."I may be some time".....

---

### Post by xtremesupremacy3 on 2013-08-09
Lol, let me know how you get on, I will keep my fingers and toes crossed for you

---

### Post by xJ3CzNb on 2013-08-09
Well that was ..errrm.interesting...
Nautilus worked fine thanks...and the command for 'all'files also worked fine...

Yes, there is still a problem...though I doubt that you can help with it...however just in case you can here is a short selection of what the terminal threw up at me (interesting watching ones computer actually working though)[h264 @ 0x9c1dfc0] deblocking_filter_idc 7 out of range
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaecc54] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaec884] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] illegal reordering_of_pic_nums_idc
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] mmco: unref short failure
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 [h264 @ 0x9c1dfc0] sps_id out of range
    Last message repeated 1 times
[h264 @ 0x9c1dfc0] deblocking_filter_idc 7 out of range
[h264 @ 0x9c1dfc0] decode_slice_header error
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 [h264 @ 0x9c1dfc0] non-existing PPS 2 referenced
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaecc54] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaec884] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] non-existing PPS 2 referenced
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] mmco: unref short failure
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 [h264 @ 0x9c1dfc0] sps_id out of range
    Last message repeated 1 times
[h264 @ 0x9c1dfc0] non-existing PPS 2 referenced
[h264 @ 0x9c1dfc0] decode_slice_header error
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 [h264 @ 0x9c1dfc0] non-existing PPS 2 referenced
[h264 @ 0x9c1dfc0] decode_slice_header error
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 [h264 @ 0x9c1dfc0] deblocking_filter_idc 7 out of range
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaecc54] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaec884] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] out of range intra chroma pred mode at 1 0
[h264 @ 0x9c1dfc0] error while decoding MB 1 0
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] sps_id out of range
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 1 times
[h264 @ 0x9c1dfc0] illegal memory management control operation 32
[h264 @ 0x9c1dfc0] cabac_init_idc overflow
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
    Last message repeated 1 times
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 408 times
[h264 @ 0x9c1dfc0] illegal memory management control operation 32
[h264 @ 0x9c1dfc0] cabac_init_idc overflow
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
    Last message repeated 1 times
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
[h264 @ 0x9c1dfc0] number of reference frames (0+3) exceeds max (1; probably corrupt input), discarding one
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
    Last message repeated 21 times
[h264 @ 0x9c1dfc0] illegal POC type 32
    Last message repeated 1 times
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
    Last message repeated 190 times
[h264 @ 0x9c1dfc0] cabac_init_idc overflow
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 7346 times
[h264 @ 0x9c1dfc0] Changing field mode (3 -> 3) between slices is not allowed
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 864 times
[h264 @ 0x9c1dfc0] FMO not supported
[h264 @ 0x9c1dfc0] reference overflow (pps)
[h264 @ 0x9c1dfc0] FMO not supported
[h264 @ 0x9c1dfc0] reference overflow (pps)
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
    Last message repeated 158 times
[h264 @ 0x9c1dfc0] deblocking_filter_idc 16 out of range
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 448 times
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaecc54] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] [IMGUTILS @ 0xbfaec884] Picture size 0x0 is invalid
[h264 @ 0x9c1dfc0] mb_width/height overflow
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 7153 times
[h264 @ 0x9c1dfc0] reference overflow
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] mmco: unref short failure
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 224 times
[h264 @ 0x9c1dfc0] FMO not supported
    Last message repeated 1 times
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
    Last message repeated 158 times
[h264 @ 0x9c1dfc0] deblocking_filter_idc 16 out of range
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 415 times
[h264 @ 0x9c1dfc0] deblocking_filter_idc 16 out of range
[h264 @ 0x9c1dfc0] decode_slice_header error
[h264 @ 0x9c1dfc0] concealing 396 DC, 396 AC, 396 MV errors
frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0 frame=    2 fps=  0 q=2.0 size=      32kB time=0.08 bitrate=3252.7kbits/s dup=0     Last message repeated 1079 times
frame=    2 fps=  0 q=2.0 Lsize=      35kB time=0.08 bitrate=3572.7kbits/s dup=0 drop=89984    
video:33kB audio:0kB global headers:0kB muxing overhead 6.476128%


A LOT of it was in RED...I presume that is the fault of the cctv recorder and not this computer...all I get is the first frame of the video...

I would really like to say Danke ye val...you have been a star, and very patient with me.

I suppose I have lost the footage now or it will only play through the recorder itself, and as that is a looping 'record' on the disk I would have to switch the cctv off to keep it...every option but a good one eh!

---

### Post by xtremesupremacy3 on 2013-08-09
Geen dank ;)

Well I'm not really an expert at ffmpeg error messages, but I do see mentioning of picture being incorrect which has to do I believe with a VOD header.
Either way, I think this is where my knowledge ends. I'm afraid I don't know what else to do.

You shouldn't have lost the footage altogether since it shouldn't have overwritten the existing file just made a copy.

Perhaps someone else may know the answer to it, sorry :(

---

### Post by xJ3CzNb on 2013-08-09
You have done marvelously for me extreme!..I honestly do thank you, the problem I asked for help with you have SOLVED, of that there is no doubt! Excellent job!!!

That I have a useless cctv recorder is perhaps the fault of my wallet (should have saved more pennies up in the first place) I have just re-recorded it by camera, it isn't the same but at least it is a recording of a recording and may do the job I need it to...whatever!

PROBLEM SOLVED (is this where I put this?, or is there somewhere else to mark it done?)

---

### Post by xtremesupremacy3 on 2013-08-09
You are more than welcome!

If you have any other issues, please feel free to ask, theres always someone here to help.
If you go to the top of the page and click on 'Thread Tools' you should have the option to mark it as solved (if I remember right).

---

### Post by xJ3CzNb on 2013-08-09
...and that is two problems you have solved in one night for me..duly marked 'SOLVED' .
Thanks once again

---

