---
title: "[Bash] Sending the TERM Signal to a Process"
date: 2012-05-03
forum: Programming Talk
---

### Post by dodle on 2012-05-03
My question specifically deals with ffmpeg. What I am trying to do is cleanly shut down an ffmpeg process that was started in the background the same way it would shut down if the "q" key was pressed while the program was running in the foreground. I've figured out that I can kill the process in the background using the "kill" command and the "$!" variable:

```
nohup ffmpeg -y -f x11grab -r 30 -s 1280x800 -i :0.0 -sameq -vcodec libx264 test.avi > nohup$$.out 2>&1 &
P1=$!

sleep 5s
kill $P1
```

> The  default  signal  for  kill is TERM.

Is sending the [color=red]TERM[/color] signal to the ffmpeg process the same as pressing the "q" key to stop encoding, or does it prematurely shut down the program potentially causing problems with the output? So far the output videos seem to work fine. I haven't looked through the ffmpeg source code, but perhaps I should.

---

### Post by Bachstelze on 2012-05-03
Instead of looking through the ffmpeg source code, asking on the mailing-lists what would be a good way to simulate a press on the q key would probably take less time and effort. :p

---

### Post by papibe on 2012-05-03
Hi dodle.

I believe you could send a 'q' if you run the ffmpeg command on 'screen', and then sending input to it using the 'stuff' option.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1843007&highlight=screen+stuff") to get you started (post #2).

Hope that helps, and tell us how it goes.
Regards.

---

### Post by dodle on 2012-05-03
> **Bachstelze said:**
> asking on the mailing-lists...would probably take less time and effort.

That gave me the idea to get on the IRC channel. I was told that hitting the "q" key to end the encoding is the same as pressing Ctrl+C, and if the video is playable afterwards then all headers have been written correctly. So it sounded like using the kill command to send a TERM signal ends the encoding just fine. Thanks for your help guys, and I'm glad I didn't have to go through the source.

---

### Post by Bachstelze on 2012-05-03
Ctrl+C does not send SIGTERM but SIGINT. Just to be sure, you might want to make your script send that instear of SIGTERM.

---

### Post by dodle on 2012-05-03
For this case it doesn't look like there is whole lot of difference between using SIGTERM and SIGINT:

> &#8212; Macro: int SIGTERM

    The SIGTERM signal is a generic signal used to cause program termination. Unlike SIGKILL, this signal can be blocked, handled, and ignored. It is the normal way to politely ask a program to terminate.

    The shell command kill generates SIGTERM by default. 

&#8212; Macro: int SIGINT

    The SIGINT (&#8220;program interrupt&#8221;) signal is sent when the user types the INTR character (normally C-c).

> :~$ man kill
...
INT        2   exit
...
TERM      15   exit
...

It appears that ffmpeg handles them the same. But I think you are right, to be safe I will use SIGINT.

---

