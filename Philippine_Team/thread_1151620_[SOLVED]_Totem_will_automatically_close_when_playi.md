---
title: "[SOLVED] Totem will automatically close when playing AVI videos and MP3 audios"
date: 2009-05-07
forum: Philippine Team
---

### Post by SHENGTON on 2009-05-07
Hello guys, good afternoon. :)

Guys, I really need you help. Got a problem here with Totem or Movie Player.

I have AVI videos and MP3 videos here. Just recently installed the following:
1. ubuntu-restricted-extras
2. build-essential
3. Skype
4. Opera Browser
5. PlayOnLinux
5. GYacHI
6. WinFF
7. Crossover Linux
8. Mozilla Thunderbird
9. VLC Media Player

When I tried to play AVI and MP3, the Movie Player will open for awhile and then it will just close. VLC Media Player could play MP3 files but when I tried it with AVI files same with Movie Player. Both Movie Player and VLC Media Player will automatically close when playing AVI videos and MP3 audios.

Is there something I forgot to install?

or

This is a bug?

By the way I'm using Ubuntu Jaunty 9.04 and the Kernel version is 2.6.28-11-generic. Hope you can help me with this.

Take care and God bless. :)

---

### Post by paul.gevers on 2009-05-07
> **SHENGTON said:**
> When I tried to play AVI and MP3, the Movie Player will open for awhile and then it will just close. Same with VLC Media Player as well. Both Movie Player and VLC Media Player will automatically close when playing AVI videos and MP3 audios.

It would help if you start the program from a command line and look at/copy the output. Usually it will help finding the problem.

---

### Post by SHENGTON on 2009-05-07
Hello paul.gevers, good afernoon. :)

Thanks for replying. How will I do that?

Take care and God bless. :)

---

### Post by pro003 on 2009-05-07
why don't you install mplayer and see if that resolves the problem... 

maybe you have some broken packages installed...

---

### Post by wineman on 2009-05-07
ok open gnome-terminal (Applications --> Accessories --> Terminal) and type in "totem", then press enter and watch totem appear. 
Try and play a movie or MP3, and you'll see a list of things coming up the terminal. Try and write some of them down there, and i guarentee you that your problem will be on that lsit.

im going to take a wild guess here, but i think that winff might be the problem.

Hope this helps bru:)

---

### Post by SHENGTON on 2009-05-07
Hello guys, good afternoon. :)

Thanks for helping.

@pro003
Same thing with Movie Player and VLC Media Player

@wineman
Here's the result:
> shengton@shengton:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

What should I do next?

Thanks and God bless. :)

---

### Post by loell on 2009-05-07
this is a video driver bug, are you using intel video?

---

### Post by SHENGTON on 2009-05-07
Hello loell, good afternoon. :)

Yes I'm using Intel video.

Take care and God bless. :)

---

### Post by loell on 2009-05-07
as a work around you can use vesa driver instead of intel driver, or

follow ubuntugeek's work around, [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html")

---

### Post by SHENGTON on 2009-05-07
Hello loell, good afternoon. :)

Everyhting works fine now. I just followed this [post]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/357824/comments/5"). And it's said that All I have to do is go to System => Preferences => Multimedia System Selector and changed the video output to something other than auto detect.

After that I can now play AVI and MP3 files. It is said as well in that topic that just like you said that instead og using the Intel driver I just need to install the VESA driver.

Thanks again guys and God bless. :)

---

### Post by SHENGTON on 2009-05-08
Kindly mark my topic as SOLVED.

Thanks and God bless. :)

---

