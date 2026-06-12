---
title: "Fullscreen for .sh script?"
date: 2009-04-20
forum: Programming Talk
---

### Post by naja74 on 2009-04-20
I've been googling for a command that will start a .sh script in full screen. I have a .sh script that runs a backup of my laptop then shuts it down, and I run it from a launcher on my gnome panel. The launcher is set as "application in terminal". I've tried adding a --full-screen option in the launcher and the script and neither have given me the desired result.

I'm wanting the script to start in full screen, as if I had used the F11 button or something similar, so that while the backup is running no other person, such as my wife or child, will try to use the laptop while the backup is running. It's not such a big deal when it's running an incremental backup, but a full backup of my /home directory can take several minutes.

Any ideas? I know I could just open a terminal, hit F11 and manually run the script but I'm sure that there's a way to get the script to start in full screen and it's bugging me that I can't find the answer.

---

### Post by leandromartinez98 on 2009-04-20
I don't know how to do that, but I have a different suggestion. You can create an
image saying: Doing backup! Don't use the computer now!

Then, launch "eog" in fullscreen with that figure, before the backup script:

eog -f warning.jpg &
yourbackupscript

---

