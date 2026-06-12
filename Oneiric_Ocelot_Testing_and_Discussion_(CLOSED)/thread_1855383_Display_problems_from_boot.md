---
title: "Display problems from boot"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Jeinhor on 2011-10-06
Hi folks!

I just updated from Ubuntu 11.04 to 11.10, and when booting the display just shows some colored lines (can attach an image tonight) where the Ubuntulogo should have been. It seems the system boots normally otherwise, I can ssh to it from another computer.

11.04 shows the display fine. Can this be a driver issue? Is there any way to install the proprietary drivers from the command line (you think that would help?)?

As I have ssh access I can gather any logs you need, but I'm not sure what's relevant so please let me know.

Any ideas, suggestions or questions are welcome :) 

Thanks in advance!

---

### Post by 23dornot23d on 2011-10-06
ATI Radeon HD 6400M graphics card.

If this is still your graphics card .... 

I believe there have been some problems in the past with some ATI graphics  ... 

I use Nvidia so maybe someone else can help - but confirm your graphics card to start with
( mine is working fine using Nvidia by the way )

---

### Post by Toz on 2011-10-06
> **Jeinhor said:**
> Is there any way to install the proprietary drivers from the command line (you think that would help?)?

Try running **jockey-text**. Here are the command-line options:

```
$ jockey-text --help
Usage: jockey-text [options]

Options:
  -h, --help            show this help message and exit
  -c, --check           Check for newly used or usable drivers and notify the
                        user.
  -u, --update-db       Query driver databases for newly available or updated
                        drivers.
  -l, --list            List available drivers and their status.
  -a, --auto-install    Enable drivers that can be automatically installed.
  --hardware-ids        List hardware identifiers from this system.
  -e DRIVER, --enable=DRIVER
                        Enable a driver
  -d DRIVER, --disable=DRIVER
                        Disable a driver
  --confirm             Ask for confirmation for --enable/--disable
  -C, --check-composite
                        Check if there is a graphics driver available that
                        supports composite and offer to enable it
  -m free|nonfree|any, --mode=free|nonfree|any
                        Only manage free/non-free drivers. By default, all
                        available drivers with any licence are presented.
  --dbus-server         Run as session D-BUS server.
  --no-dbus             Do not use D-BUS for communicating with the backend.
                        Needs root privileges.
  -k KERNEL, --kernel=KERNEL
                        Use a different target kernel version than the
                        currently running one. This is only relevant with
                        --no-dbus.

```

---

### Post by Jeinhor on 2011-10-06
> **Toz said:**
> Try running **jockey-text**. Here are the command-line options:

Thanks. This would be for gathering logs, yes?

> **23dornot23d said:**
> ATI Radeon HD 6400M graphics card.

If this is still your graphics card .... 

I believe there have been some problems in the past with some ATI graphics  ... 

I use Nvidia so maybe someone else can help - but confirm your graphics card to start with
( mine is working fine using Nvidia by the way )

Huh? Where did you find that information, about my graphics card?

This is for a HTPC I'm running, a Zotac-box with an integrated graphics card (nVidia). Ran fine on 11.04.



I installed 11.10 in a bit of a strange way. I thought the problem I'm having with graphics was unrelated to this install, but perhaps not. Check out my issue here (read the last post, that's the most important one where I'm describing my current installation): [http://ubuntuforums.org/showthread.php?t=1854257](http://ubuntuforums.org/showthread.php?t=1854257).

I just installed ubuntu-desktop package using SSH as I don't have access to the console session right now, perhaps ubuntu-desktop installed missing graphics drivers as well? I'll try when I get home and get back to you guys here. 

Thanks for the tips!

---

### Post by Toz on 2011-10-06
> Originally Posted by Toz View Post
Try running jockey-text. Here are the command-line options:> **Jeinhor said:**
> Thanks. This would be for gathering logs, yes?
This is the text interface for installing proprietary drivers - in case you don't have access to the gui.

---

### Post by Jeinhor on 2011-10-06
> **Toz said:**
> This is the text interface for installing proprietary drivers - in case you don't have access to the gui.

Ah, great! Didn't read the quote properly, sorry. Thanks for the tip.

---

### Post by Quackers on 2011-10-06
You could try the nomodeset boot option, see below for details on how to do that in an installed system

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by 23dornot23d on 2011-10-06
Just as regards where I got the graphics card info from was one of your past posts ..... [**LINK**]("http://ubuntuforums.org/showpost.php?p=10986121&postcount=1")

You maybe have more than one computer - but the information was important .... 
I took a stab at it - just shows ..... cannot assume things to be as we sometimes expect them to be .....

But I did ask for clarification ... which we now have ..... Thank You ....

---

### Post by Jeinhor on 2011-10-10
Problem solved after installing proprietary drivers (jockey-text), thanks everyone!

---

### Post by Toz on 2011-10-10
Glad to hear and thanks for posting back. Can you please mark the thread "Solved" from the Thread Tools link above?

---

### Post by Jeinhor on 2011-10-10
> **Toz said:**
> Glad to hear and thanks for posting back. Can you please mark the thread "Solved" from the Thread Tools link above?

Had forgotten I could do that. Done.

---

