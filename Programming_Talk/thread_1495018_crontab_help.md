---
title: "crontab help"
date: 2010-05-27
forum: Programming Talk
---

### Post by COKEDUDE on 2010-05-27
I set up a simple echo script so I know its actually doing its job.
* * * * * echo hi >> /home/bob/Desktop/come
I have 3 video's I'm trying to play as a playlist at 8 am. I've checked in the terminal and as a regular script that this works fine. Right now I'm just trying to get it working so I'm using wildcards for the time and day. I tried it with sourcing and without sourcing in the crontab. Then I tried to run it as a regular script with no luck. I've checked that my script runs fine in the terminal. I also did this with sourcing and without sourcing. I really don't understand what I'm doing wrong so any help would be appreciated. Do I need to use shell scripts or is there something else I am doing wrong?
* * * * * . vlc -L /home/vids/vid1 /home/vids/vid2 /home/vids/vid3
* * * * * vlc -L /home/vids/vid1 /home/vids/vid2 /home/vids/vid3
* * * * * /home/bob/Desktop/yo
* * * * * . /home/bob/Desktop/yo

I have also checked the /etc/cron.deny and /etc/cron.allow and there are no problems in those files.

---

### Post by kalasoka on 2010-05-27
I guess in crontab you need to specify atleast one field. So, to run 'hello.sh' at 8 AM everyday, you'd write

```
#min hour day month dow
0 8 * * * hello.sh > ~user/out
```

---

### Post by rnerwein on 2010-05-28
> **kalasoka said:**
> I guess in crontab you need to specify atleast one field. So, to run 'hello.sh' at 8 AM everyday, you'd write

```
#min hour day month dow
0 8 * * * hello.sh > ~user/out
```

that's right.
on the other side the only environment you got when running a cron script is:

HOME=/home/gonzo
LOGNAME=gonzo
PATH=/usr/bin:/bin
SHELL=/bin/sh
PWD=/home/gonzo

this means you have to set the PATH by yourself in your script ( where is VLC ? ).
if you need a display you have to set your DISPLAY=0:0 too. and so on.
ciao

---

### Post by COKEDUDE on 2010-05-30
> **rnerwein said:**
> that's right.
on the other side the only environment you got when running a cron script is:

HOME=/home/gonzo
LOGNAME=gonzo
PATH=/usr/bin:/bin
SHELL=/bin/sh
PWD=/home/gonzo

this means you have to set the PATH by yourself in your script ( where is VLC ? ).
if you need a display you have to set your DISPLAY=0:0 too. and so on.
ciao

```
/usr/bin/vlc
```

I changed it to full directory and that didn't work :(. 
```
* * * * * /usr/bin/vlc -L /home/vids/vid1 /home/vids/vid2 /home/vids/vid3
* * * * * /home/bob/Desktop/yo
* * * * * . /home/bob/Desktop/yo
```

---

### Post by geirha on 2010-05-30
Put
```
>>/tmp/vlc-output.tmp 2>&1
```
at the end, to capture all output of vlc to a temporary file. Let it run at least once, then see what it output. I'm guessing it's unable to find a display.

---

### Post by COKEDUDE on 2010-06-03
> **geirha said:**
> Put
```
>>/tmp/vlc-output.tmp 2>&1
```
at the end, to capture all output of vlc to a temporary file. Let it run at least once, then see what it output. I'm guessing it's unable to find a display.

Thats exactly what the VLC forum people said. They never explained how to fix that problem though :(. Any idea how to fix that?

---

### Post by rnerwein on 2010-06-03
hi
vlc via cron is a ticket to hell - but i got it - first some explanation about errors ( may be uninteresting )
# when i trie to run vlc via root crontab i get:
#--------------------------------------------------------------------------------------------------
11021 geteuid()                         = 0
11021 write(2, "VLC is not supposed to be run as"..., 224) = 224
| 00000  56 4c 43 20 69 73 20 6e  6f 74 20 73 75 70 70 6f [COLOR=Blue] VLC is n ot suppo[/COLOR] |
| 00010  73 65 64 20 74 6f 20 62  65 20 72 75 6e 20 61 73  [COLOR=Blue]sed to b e run as[/COLOR] |
| 00020  20 72 6f 6f 74 2e 20 53  6f 72 72 79 2e 0a 49 66  [COLOR=Blue] root[/COLOR]. S orry..If |
| 00030  20 79 6f 75 20 6e 65 65  64 20 74 6f 20 75 73 65   you nee d to use |
| 00040  20 72 65 61 6c 2d 74 69  6d 65 20 70 72 69 6f 72   real-ti me prior |
| 00050  69 74 69 65 73 20 61 6e  64 2f 6f 72 20 70 72 69  ities an d/or pri |
| 00060  76 69 6c 65 67 65 64 20  54 43 50 20 70 6f 72 74  vileged  TCP port |
| 00070  73 0a 79 6f 75 20 63 61  6e 20 75 73 65 20 2f 75  s.you ca n use /u |
| 00080  73 72 2f 62 69 6e 2f 76  6c 63 2d 77 72 61 70 70  sr/bin/v lc-wrapp |
| 00090  65 72 20 28 6d 61 6b 65  20 73 75 72 65 20 69 74  er (make  sure it |
| 000a0  20 69 73 20 53 65 74 2d  55 49 44 20 72 6f 6f 74   is Set- UID root |
| 000b0  20 61 6e 64 0a 63 61 6e  6e 6f 74 20 62 65 20 72   and.can not be r |
| 000c0  75 6e 20 62 79 20 6e 6f  6e 2d 74 72 75 73 74 65  un by no n-truste |
| 000d0  64 20 75 73 65 72 73 20  66 69 72 73 74 29 2e 0a  d users  first).. |
11021 exit_group(1)                     = ?

# when i try to run it as an normal user i get:
#----------------------------------------------------------------------------------------------------
11199 read(5, "\32\1\36\0\7\0\1\0\202\0\10\0unknown|unknown term"..., 4097) = 320
11199 close(5)                          = 0
11199 ioctl(2, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffb35a6680) = -1 EINVAL (Invalid argument)
11199 ioctl(2, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffb35a6620) = -1 EINVAL (Invalid argument)
11199 write(2, "Error opening terminal: unknown."..., 33) = 33
| 00000  45 72 72 6f 72 20 6f 70  65 6e 69 6e 67 20 74 65  [COLOR=Blue]Error op ening te[/COLOR] |
| 00010  72 6d 69 6e 61 6c 3a 20  75 6e 6b 6e 6f 77 6e 2e  [COLOR=Blue]rminal:  unknown.[/COLOR] |
| 00020  0a                                                .                 |
11199 exit_group(1)

but here is the way it works:
my crontab is:
# m h  dom mon dow   command
40 13  *   *    * /home/richi/scripts/cronmusi.sh

my script is ( you have to open a terminal first and type in the terminal: [COLOR=Red]tty ---> results in: /dev/pts/X[/COLOR] ( my is /dev/pts/2 )
#!/bin/sh
/usr/bin/xhost +localhost
DISPLAY=:0.0
export DISPLAY
LANG=de_DE.utf8
export LANG
/usr/bin/vlc -L /home/richi/Musik/special/nights_in_white_satin.wav [COLOR=Red]</dev/pts/2 >/dev/pts/2 2>&1[/COLOR]
exit 0
# you can minimize the tty but don't close it. this will do the trick.  :-)  :-)
ciao
p.s. i will open a thread for vlc too ( i just downloaded it ) because i can't play videos even from command line ( horrible pictures ).

---

### Post by COKEDUDE on 2010-06-09
I got this to work finally. Thanks a lot for the help. I officially hate gedit because of my experience. It didn't save my file properly. It somehow saved my file as 
```
ASCII text, with CRLF line terminators
```

I didn't know that was a problem or how to check it for a LONG LONG time which really stunk. 

This is my functioning script if anyone is curious. I also of course had to change my language since I speak English. 
```
#!/bin/sh
set -x
/usr/bin/xhost +localhost
DISPLAY=:0.0
export DISPLAY
LANG=en_US.utf8
export LANG
/usr/bin/vlc -L "/home/bob/Desktop/The Patriot/The Patriot.avi" </dev/pts/0 >/dev/pts/0 2>&1
exit 0
```

Again Thanks a lot for the help. I would have never of been able to figure this out on my own.

---

### Post by COKEDUDE on 2010-11-09
Um somehow my tty magically changed on its own. So I had to change my script a bit. This is what it looks like now. 

```
#!/bin/sh
set -x
/usr/bin/xhost +localhost
DISPLAY=:0.0
export DISPLAY
LANG=en_US.utf8
export LANG
/usr/bin/vlc -L "/home/bob/Desktop/The Patriot/The Patriot.avi" </dev/pts/1 >/dev/pts/1 2>&1
exit 0
```

Does anyone have any idea why my tty changed? I have no idea how to change it so I am quite surprised it happened.

---

### Post by COKEDUDE on 2010-11-19
If you use a lot of terminals this is a better to do what you see above. It checks what your tty information is so you use the appropriate tty. 

```
#!/bin/bash
mytty=`tty` #note: backticks (grave) not single quotes
echo $mytty
set -x
/usr/bin/xhost +localhost
DISPLAY=:0.0
export DISPLAY
LANG=en_US.utf8
export LANG
/usr/bin/vlc -L "/home/bob/Desktop/The Patriot/The Patriot.avi" <$mytty >$mytty 2>&1
exit 0

```

---

