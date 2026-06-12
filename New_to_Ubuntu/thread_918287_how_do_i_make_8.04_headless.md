---
title: "how do i make 8.04 headless"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by deembee on 2008-09-12
Hi I want to make a computer headless with no mouse or keyboard or screen. I have set up remote desktop and can access it across my network from my xp machine but when i pull out the screen, mouse and keyboard ubuntu doesn't load. I plugged the screen in and it seemed to have stalled at some could not detect monitor and graphics screen. could someone please tell me how I go about making this work.
thanks

---

### Post by wolterh on 2008-09-12
I think that you are looking for ubuntu-server

---

### Post by jemate18 on 2008-09-12
> **deembee said:**
> Hi I want to make a computer headless with no mouse or keyboard or screen. I have set up remote desktop and can access it across my network from my xp machine but when i pull out the screen, mouse and keyboard ubuntu doesn't load. I plugged the screen in and it seemed to have stalled at some could not detect monitor and graphics screen. could someone please tell me how I go about making this work.
thanks

I think you should download the Ubuntu Server Edition.. It doesn't have a GUI installed by default...

After installing it, you can setup your BIOS so that even without a keyboard, your system will not halt on POST (Power On Self Test)

---

### Post by deembee on 2008-09-12
I don't want to use the server edition as i know nothing about servers and minimal knowledge of command line stuff. I would like to use the desktop edition as i have it set up how i want it. Surely this can be done ...can in xp ;)

---

### Post by adult swim on 2008-09-12
seems like you need server edition, cli is not that scary.  if you are trying to use vncviewer to control the box, then why not just boot it up with all of the peripherals attached, unplug them and then you are set.

---

### Post by Mysphyt on 2008-09-19
I'm a little frustrated here--I'm facing the same dilemma, and I feel like the question raised hasn't been seriously responded to.

I'm not a CLI guru, but I'm transitioning my fileserver from a hand-built Gentoo system, driven primarily by bash scripts I wrote myself, so I'm not at all afraid of the CLI.  But a lot of the tools I want to use--Azureus, for one--aren't functional (or at least aren't as functional) from a CLI only perspective.  More importantly, this server's primary function is processing/transcoding/archiving video, and so I want to maintain the possibility of setting up MythTV/XBMC/something in the future.  I'm not afraid of the CLI, but I want to have access to GUI driven tools.

A good example is Bittorrent--in a CLI world, I had to use a hodgepodge of cron jobs to process downloads, dtach to manage persistent sessions, and rtorrent (a proficient, but not particularly full-featured, NCURSES bt client) to do the actual downloading.  I still missed functionality that was native to Azureus, not least RSS feed parsing and a web interface.  It seems absurd to say that a headless system can't have a graphical component available via VNC--especially when I have everything working as desired when KVM are plugged in.  For a headless box--one that I generally keep tucked behind a very large TV--leaving a display and keyboard plugged in, or connecting and disconnecting it at reboot, are neither practical nor feasible.

I really don't mean to be combative here, and everybody on the forum is always very helpful.  I just feel like a valid question was asked, and then passed over.  So I'm going to ask the question of the OP again: is there a way to bypass/workaround the "failsafe" mode that Ubuntu boots X into when no display is detected?

Thanks, all.

---

### Post by ayenack on 2008-09-19
This seems strange to me it should work no probs as far as I know.

Have you enabled remote login on the ubuntu box?

**Systems>Administration>Login Window**

In security you need to un-tick the **Deny TCP connections to Xserver**
In Remote you need to set it to **Same as Local**

I've got a Feisty box running headless and had no problems whatever. Not sure if there's a bug in Hardy. Is Hardy using the pre-release of Xorg?

BTW. There's a great little app called xnest (it's in the repo's) that you can use with Terminal Server Client to connect to your remote desktop.

---

### Post by Mysphyt on 2008-09-20
Thanks for the reply--in fact, I have remote login via XDMCP as well as via VNC working now, thanks to you and to the extensive conversation in [this thread]("http://ubuntuforums.org/showthread.php?t=122402").  The problem I'm still having, though, is that what I'm aiming to do is to have an X session start automatically, and the connect to it via VNC, rather than being able to log in remotely.  I'm not worried about the security factor, because the box is behind a router and a firewall, and I'll be tunneling via SSH.  But I do want all this stuff to be able to happen automatically--isn't there a way to force the X server to use specific screen geometry?

---

### Post by deembee on 2008-09-20
Hmm I wasn't happy with the answers my CLI knowledge is very poor and i don't feel like spending the day working on something that should be easy.

what i did find is that it works perfect with a vga terminator, just 3 75ohm resistors across pins
1 and 6
2 and 7
3 and 8

$2 plug
16c for resistors

---

### Post by cariboo on 2008-09-20
You can use gui programs on the server without having to install a desktop. Just use X forwarding with ssh, once you are on your server, just type the name of the program you want to run. To enable X forwarding in a teminal type:

```
ssh -X username@server
```

then at the prompt on the server just type the name of the application you want to run eg:

```
sudo synaptic
```

Of course you have to have the application installed to use it.

Jim

---

### Post by ayenack on 2008-09-20
Not sure this will work but you could use automatic login on the headless box.

[B]System>Administration>Login Window
Security
Enable Automatic Login[/B]

This will make the box login with no user input. Then it's down to you to configure your VNC tunneling. Should be able to do it with Remote Desktop Viewer.

---

### Post by Mysphyt on 2008-09-22
Cariboo--what I'm hoping is to get a system working where I can start a program (via X forwarding, VNC, XDMCP, whatever), disconnect, and leave it running in my absence, then reconnect later and resume working with it.  Even better, I'd like to be able to turn my computer on, have it start some of those processes, and then be able to connect and see what's going on.  There are a lot of tutorials on the forums for VNC with resumable sessions, but none of them seem to want to automatically log you in, and none of them have worked for me, for some reason.  My understanding of X forwarding is that essentially it'll just use your local X to display the program, meaning that when you disconnect/quit, the process would terminate.

Ayenack: that's what I have now, and that's where I'm getting the low graphics/failsafe mode with X.  

It seems like there should be a more elegant way to deal with this than deembee's solution, but I can't seem to figure out what it is.  Thanks for all your help.  :)

---

