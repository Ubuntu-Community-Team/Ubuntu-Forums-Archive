---
title: "zenity and crontab - can't get them work together"
date: 2009-12-02
forum: Programming Talk
---

### Post by arrange on 2009-12-02
I've been using **zenity** in my **crontab** jobs for a long time, but it stopped working in Karmic for me. I've tested different options, but none of them work, and I've come out of ideas. Could you please help me out?

Options I've tried and which worked in Jaunty
```
arrange@lean:~$ crontab -l
# m h  dom mon dow   command
* * * * *       export DISPLAY=:0.0; /usr/bin/zenity --info --title="Information" --text="Hello World" &> /tmp/dbg; whoami >> /tmp/dbg; date >> /tmp/dbg
* * * * *       export DISPLAY=:0.0 && /usr/bin/zenity --info --title="Information" --text="Hello World" &> /tmp/dbg; whoami >> /tmp/dbg; date >> /tmp/dbg
* * * * *       export DISPLAY=:0; /usr/bin/zenity --info --title="Information" --text="Hello World" &> /tmp/dbg; whoami >> /tmp/dbg; date >> /tmp/dbg
* * * * *       DISPLAY=:0 /usr/bin/zenity --info --title="Information" --text="Hello World" &> /tmp/dbg; whoami >> /tmp/dbg; date >> /tmp/dbg
* * * * *       env DISPLAY=:0.0; /usr/bin/zenity --info --title="Information" --text="Hello World" &> /tmp/dbg; whoami >> /tmp/dbg; date >> /tmp/dbg
* * * * *       env DISPLAY=:0.0 && /usr/bin/zenity --info --title="Information" --text="Hello World" &> /tmp/dbg; whoami >> /tmp/dbg; date >> /tmp/dbg
```

There are no error messages in *stderr* or in system logs (but the command itself is there as a regular cron job - see below) . The command works perfectly from *gnome-terminal*. The output of *whoami* is *arrange*, so it's launched under a regular user.

```
Dec  2 20:12:01 lean CRON[2263]: (arrange) CMD (export DISPLAY=:0.0; /usr/bin/zenity --info --title="Information" --text="Hello World" &> /tmp/dbg; whoami >> /tmp/dbg; date >> /tmp/dbg)
```

Thanks.

---

### Post by dwhitney67 on 2009-12-02
I had a similar issue recently, and not with Karmic (damn I hate these stupid names).... anyhow, I had an issue with 8.10... let's just call it 'Moldy'.

To solve the issue, I inserted an 'xhost +' statement in the .bashrc file of the user's account in which I wanted the Zenity message dialog box displayed.

The only issue I came across, which may be unrelated, is that the screensaver/screenlock would not engage.  Maybe it was a system fluke and nothing related to 'xhost +'.

P.S.  Maybe you have something similar in your ~/.bashrc file:
```

...

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    **xhost + >& /dev/null**
    ;;
*)
    ;;
esac

...

```

---

### Post by arrange on 2009-12-03
GREAT, thanks, seems to be working now! I just used ```
xhost local:arrange > /dev/null
```not really sure what the difference is, but looks safer :)

And the screensaver works OK in my case, so it must be unrelated.

Thanks again.

---

### Post by dwhitney67 on 2009-12-03
> **arrange said:**
> GREAT, thanks, seems to be working now! I just used ```
xhost local:arrange > /dev/null
```not really sure what the difference is, but looks safer :)

And the screensaver works OK in my case, so it must be unrelated.

Thanks again.

Great!  I will try that myself.  I run a cron job that limits the time to one hour in which my 5 y.o. daughter is allowed to surf the internet (via Firefox).  I use zenity to display a warning message that the grace period is about to expire in 5 minutes, and then again when it has expired.

---

