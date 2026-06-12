---
title: "modem connect through php or command line"
date: 2007-02-14
forum: Programming Talk
---

### Post by tocleora on 2007-02-14
Is there a way either in PHP or from a command line (like exec() call) that I can communicate with a modem?  I don't need audio per-say, we'll be dialing a number and entering dial tones to automate a process one of our programmers has to do manually write now.  So ultimately we'd dial the number, enter a series of dial tones and hang up, that's all.  Is this possible?  TIA...

---

### Post by prensing on 2007-02-19
I would look at minicom. You can specify a script to run on the command line, so if you can write the script, you should be able to call it from PHP. I have not done this myself, though, so no guarantees.

---

