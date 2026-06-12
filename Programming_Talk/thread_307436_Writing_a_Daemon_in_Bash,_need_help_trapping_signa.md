---
title: "Writing a Daemon in Bash, need help trapping signals in background"
date: 2006-11-26
forum: Programming Talk
---

### Post by skelooth on 2006-11-26
This is driving me pretty nuts :)

The Daemon and client modes of the program are all in one self referencing script file. The Daemon creates a pid file with it's process id. I'm trapping SIGINT...

Here's the problem.

If I use

$0 --force /home/foo

(--force makes it run as a daemon) Then it runs in the foreground, and from another terminal running the client, I can end it with the call

kill -SIGINT $(cat $0.pid)

and it gets handled properly.

HOWEVER, when I run

$0 --force /home/foo &

to put it in the background from the script, it STOPS TRAPPING SIGNALS!, AHHHHHHH!!! So frustrating :) Can anyone please help me see the light of what's going on and why it's not trapping? When I push it into the background like that the only thing I can do is call SIGKILL on it and manually delete all the config files it makes.

I'm setting the trap by calling
trap myfunction SIGINT

but as mentioned, it works fine when in the foreground

---

### Post by skelooth on 2006-11-26
anyone? :(

---

### Post by daniminas on 2006-11-27
Hello.

I don't know exaclty what you want, but...:

```

USER_INTERRUPT=13

trap 'rm -f $TEMPFILE; exit $USER_INTERRUPT' TERM INT
# Cleans up the TEMPFILE if script interrupted by control-c.

```

Maybe that can help you?.

Daniel =)

---

### Post by daniminas on 2006-11-27
Checkout: [http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/debugging.html](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/debugging.html)

---

### Post by stair314 on 2009-09-09
I'm having a similar issue, see [http://ubuntuforums.org/showthread.php?p=7923441#post7923441](http://ubuntuforums.org/showthread.php?p=7923441#post7923441)

---

