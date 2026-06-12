---
title: "tunneling x11vnc through ssh on a non standard port to ubuntu computer tightvnc"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by ty74 on 2013-06-25
Hi, I have been stuck with setting up my virtual desktop on my ubuntu laptop. I am running ubuntu to ubuntu with x11vnc I start the process on my laptop as follows: " ssh -L5904:localhost:5900 -p Port remoteuser@remoteip." That command works, then I start x11vnc server, "x11vnc -noncache -once -shared -rfbauth ~/.vnc/passwd." This command works and starts connection. Then I open another window on my laptop and type, export VNC_VIA_CMD='/usr/bin/ssh -2 -c aes128-cbc -x -p Port -l User -f -: %L:%H:%R %G sleep 20' (not sure if works). then I type, vncviewer -endcodings Tight -depth 8 -quality 1 -via IPofremotemachine -u remoteuser localhost:port. The first time it work but from now on it just gives me the vncviewer -help screen everytime. I type in the password for my remote machine and then shows -help screen for vncviewer. I think the problem is with Tightvnc viewer but don't know what. Please help. I got some info on [www.vanemery.com/Linux/]("http://www.vanemery.com/Linux/")**VNC**/**vnc**-**over**-ssh.html[COLOR=#666666][FONT=arial]&#8206;.[/FONT][/COLOR]

---

### Post by steeldriver on 2013-06-25
If you want to connect again once the first connection is terminated, but disallow multiple concurrent connections, then you probably want to start x11vnc with '-never-shared -forever' instead of '-once -shared' - see

```

man x11vnc

       -once

              Exit after the first successfully connected viewer  disconnects,
              opposite of -forever. This is the Default.

       -forever

              Keep  listening for more connections rather than exiting as soon
              as the first client(s) disconnect. Same as -many

[B]              To get the standard non-shared VNC behavior where when a new VNC
              client connects the existing VNC client is dropped use:  -never&#8208;
              shared -forever   This method can also be used to guard  against
              hung TCP connections that do not go away.
[/B]
```

I'm not familiar with the VNC_VIA_CMD or the '-via' option but I suspect they are only applicable when you are tunneling via a (3rd) intermediate host - if you are tunneling straight from the x11vnc server to your laptop then once you have set up the SSH tunnel (which looks correct btw) and started the remote x11vnc server, afaik it *should* be sufficient just to do

```
vncviewer -encodings tight -depth 8 -quality 1 localhost::5904
```

(where 5904 is your chosen alternative local port) or equivalently

```
vncviewer -encodings tight -depth 8 -quality 1 localhost:04
```

Or you can use the Remmina VNC client which is standard in Ubuntu I think

---

### Post by ty74 on 2013-06-26
That did the trick the -nevershared -forever options on x11vnc command. Thanks for the tip steeldriver!:)

---

