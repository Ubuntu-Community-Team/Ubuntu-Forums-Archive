---
title: "Bash and X and Window Managers."
date: 2010-09-14
forum: Programming Talk
---

### Post by carlsmith on 2010-09-14
I have matchbox and fluxbox installed, but when I boot my system, fluxbox runs automatically.

Can someone please give me a few pointers? I just want to be able to start and quit my window managers at will using bash commands.

---

### Post by sharpdust on 2010-09-15
I don't think you can switch window managers without logging out of X first.

You can define what window manager runs first (as well as starting other apps) in your .xinitrc file ```
# .xinitrc
fluxbox & wmpid=$!

# Start other apps
# firefox &
# xterm &
# xterm &

# HANG POINT - wait for window manager to exit
wait $wmpid

```

---

### Post by conundrumx on 2010-09-15
You can indeed change window managers after starting X.  Are you looking to boot into bash, and then choose a WM/DE or change from one to the other while in X on the fly?

---

### Post by carlsmith on 2010-09-18
Yes, I'm looking to boot into Bash, then be able to tell X what to do. My aim isn't so much to switch between window managers, but I would like to understand how to, what I need to figure out is what to do to display graphical output from Python scripts in a full-screen without a window manager.
I'd like to be able to write a little script with Nano, save it, then run it from the command line and have the graphics open up and take over the screen until I quit the process.
Thank you for getting back to me too.

---

### Post by carlsmith on 2010-09-18
> **sharpdust said:**
> I don't think you can switch window managers without logging out of X first.

You can define what window manager runs first (as well as starting other apps) in your .xinitrc file ```
# .xinitrc
fluxbox & wmpid=$!

# Start other apps
# firefox &
# xterm &
# xterm &

# HANG POINT - wait for window manager to exit
wait $wmpid

```

Nice one chap, thank you, this certainly helps with the window manager problem.  :)

---

