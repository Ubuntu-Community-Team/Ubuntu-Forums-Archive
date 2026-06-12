---
title: "Broadcasting program output to connected sessions via wall"
date: 2015-07-24
forum: Programming Talk
---

### Post by cdaringe2 on 2015-07-24
Hi all:

I have a script that I care to run on machine boot, and be running in the background.  This service, however, needs to be vocal and show output to connected sessions.

Here's an example:

```
node ./.webpack-dev-server.js
```

The output of the command is pretty basic:

```
Listening at 0.0.0.0:22222

```

Great.  Now, on every stdout newline, I want to prefix the output.  This isn't mandatory, but figured `xargs` may help me get individual commands to `wall` to work a bit better (thx @Wraithan!).

```
node ./.webpack-dev-server.js | xargs -L 1 echo "wpds - $1"
```

The output is just as expected:

```
wpds -  Listening at 0.0.0.0:22222


```

WooHoo!  OK, now I want to broadcast it to all sessions:

```
node ./.webpack-dev-server.js | xargs -L 1 echo "wpds - $1" | wall
```

However, there is not output.  It is silent :( .  I am running ubuntu 14.x.

```

wall --version
wall from util-linux 2.20.1

```

How can I get each stdout line to be broadcast?  I made a really simple script, test.js, that *just* logs two bits to stdout (via console.log, for node'rs), and

```
node test.js | xargs -L 1 echo "test - $1" | wall
```

actually *does *broadcast the two simple logs.  I don't understand why the output can be shown in both scripts without piping to wall, but why wall honors broadcasting from my simple script by not my webpack script!

I hope that was clear!  Looking forward to LEARNING.

---

### Post by ofnuts on 2015-07-25
If "node" doesn't terminate then there may be some ouput buffering somewhere (4K buffers usually) which prevents the data to be forwarded in the pipes (until a buffer fills up or the process upstreams closes the handle). Typically the output to a terminal/tty is line-buffered (output actually occurs when the stream contains a line-end character, so it appears instantaneously) while output to other types (files/pipes) is fully buffered which is not a problem when programs terminate bit is a problem for long-running code.

---

### Post by cdaringe2 on 2015-07-25
Thanks for the tip, @ofnuts.  Great to know.  Given that my basic script works:

```

node test.js | xargs -L 1 echo "test - $1" | wall
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]Broadcast Message from cdieringer@chrisweb
        (/dev/pts/0) at 13:36 ...


test -  m1
test -  m2

```

I am not confident that the buffering would be the issue at play. Regardless, your note was informative, and lead me to learn a bit about **stdbuff**, and disabling buffering as a test. I modified my test and actual commands to disable buffering, and they look more like:
```

stdbuf -i0 -o0 -e0 node test.js | stdbuf -i0 -o0 -e0 xargs -L 1 echo "test - $1" | wall
// and ...
stdbuf -i0 -o0 -e0 node webpack-dev-server.js | stdbuf -i0 -o0 -e0 xargs -L 1 echo "$1" | wall

```

The test script still works great.  The the webpack cmd still shows me the output _without_ piping to wall, but silent when piping to wall.  I'm wondering if my webpack script spawns a child process, and the output I generally see on screen is from that?  Let me know if you've got any other tricks up your sleeve.  Thanks for the input, again!

---

### Post by tgalati4 on 2015-07-26
It could be a permissions issue.  Look at *top* and while running your script see who the owners are for all of the processes that are running.  If the web-based processes are running as "www-data" or "wheel" or something else, then it's possible *wall* can't see those sessions.  It would seem to be a security vulnerability to allow *wall* to send messages to other processes through a javascript instance.

---

### Post by cdaringe2 on 2015-07-27
@tgalati4, another great idea!  thanks!  i confirmed that my user is the user of all of the processes (node/xargs/wall). i also ran them all sudo prefixed with buffering disabled.  i also tried running my command in a root session just in case there was something else at play.

It's still puzzling to me that without ```
**| wall**&#8203;
``` I can see the output as expected.

---

