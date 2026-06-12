---
title: "Start something running in workspace 2"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by gladgrind on 2013-01-27
When I boot up, I am in workspace 1, and I run a script to run this and that. I would like one of the programs to start up in workspace 2, rather than workspace 1.

Any way to do that? Automatically I mean; I do not want to lift a finger other than run the script.

I know it is terminally lazy. Thanks for any help.

---

### Post by tgalati4 on 2013-01-27
Laziness is a primary motivator in Linux.  "How can I do the least work possible?"

In a terminal:

```
env
```

You will see something that looks like:

DISPLAY=:0.0


I would think that if you put a stanza in your script that sets DISPLAY to 0.2 or 0.3 then it might show up in a different workspace.  Just a hunch.

Perhaps:

```
setenv DISPLAY :0.2
```

After some searching, there is a tool:

[http://tomas.styblo.name/wmctrl/](http://tomas.styblo.name/wmctrl/)

It's not installed by default:

tgalati4@Dell600m-mint14 ~ $ apt-cache search wmctrl
wmctrl - control an EWMH/NetWM compatible X Window Manager
tgalati4@Dell600m-mint14 ~ $ apt-cache policy wmctrl
wmctrl:
  Installed: (none)
  Candidate: 1.07-7
  Version table:
     1.07-7 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe i386 Package

Perhaps:

```
sudo apt-get install wmctrl
```

Now, how is that for a lazy reply?

---

### Post by mcduck on 2013-01-27
If you are using Unity (or really any desktop session with Compiz as the window manager), you can use "Window Rules" and "Place Windows"-plugins to define various settings (like a specific desktop) for different applications and windows.

Just install CompizConfig Settings Manager if you don't have it already, make sure those plugins are enabled, and then define the window matching rules in their settings... (the best way to specify your application windows depends on application itself, but using the window title works quite well in most cases.)

(be careful with CCSM, though, some settings there might conflict with the default desktop setup so if you get any warnings about conflicts, make sure you are sure what youa re doing before overwrititng any default settings. Although both the plugins I suggested should be perfectly safe, and even if something goes wrong, running "unity --reset" in a terminal should get things back to a sane setup.)

---

