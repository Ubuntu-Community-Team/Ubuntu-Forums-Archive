---
title: "Opening apps remotely with X11 not working"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by slockton on 2008-06-02
Hello,

I think this problem has an easy solution, but when I search for an answer it never quite fits my problem. The client is running OS X 10.5.3 (with X11 installed!), and the server is ubuntu hardy.

The problem:
- I log in to ubunutu machine via ssh: ssh -X <ipaddress>
- Then I try to launch an application from the command line (e.g. firefox), which SHOULD open X11 on the OS X machine and then open the X application.
- However, the application launches on the ubuntu server and NOT the mac client!

The same goes for any X application (gedit, deluge, for example).

I presume there's something wrong with my DISPLAY settings, but I do not know how to configure it so it opens up the window on the client side - I thought it just did that automatically...

Thanks,
Ste

---

### Post by sdennie on 2008-06-02
I've never used ssh -X but, you are right in that it's likely a problem with your DISPLAY variable.  I would try doing something like this:

```

DISPLAY=the_client:0.0 whatever_program_you_want_to_run

```

It's entirely possible that your login scripts on your OSX machine are explictly setting DISPLAY regardless of how nicely you ask it to not do so.  That could be your problem.

You may also have problems with xhost settings but, that's a whole other thread...

---

### Post by barnex on 2008-06-02
> **slockton said:**
> Hello,
 The client is running OS X 10.5.3 (with X11 installed!), 


Not only should X11 be installed, it should also be running and the DISPLAY variable should be set. The easiest way to is to open X11.app and ssh to your ubuntu server **from within an X11 terminal** (not apple's Terminal.app). In that case, DISPLAY will already be set and X forwarding should work. Also, I recommend connecting with:
```

ssh -YC user@machine

``` 
The -Y (trusted X-forwarding) is necessary for some apps to work well.

This worked perfectly for me when I was running macOSX (which I've ditched now, installed Ubuntu over it. :-) )

---

### Post by slockton on 2008-06-02
> **barnex said:**
> Not only should X11 be installed, it should also be running and the DISPLAY variable should be set. The easiest way to is to open X11.app and ssh to your ubuntu server **from within an X11 terminal** (not apple's Terminal.app). In that case, DISPLAY will already be set and X forwarding should work. Also, I recommend connecting with:
```

ssh -YC user@machine

``` 
The -Y (trusted X-forwarding) is necessary for some apps to work well.

This worked perfectly for me when I was running macOSX (which I've ditched now, installed Ubuntu over it. :-) )

I followed these instructions with no luck - the app still opens on the ubuntu (server), and not on the OS X client.

Something I should have mentioned: This has stopped working since I (clean install) upgraded to Hardy. Before, I could use iTerm in OS X to ssh -Y in to the ubuntu machine. When trying to launch firefox, i would simply type the command ('firefox'), X11 on OS X would start and launch firefox in a new window. No longer.

Thanks,
Ste

---

