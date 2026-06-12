---
title: "[SOLVED] How to run a boot script after everything is loaded"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by victorbrca on 2008-08-11
Hi all,


  I'm trying to make my servers play a sound when they are up. I'll be using a little utility called beep2.

  My questions are (if someone has the time to answer them):

1- Which of the two methods should I use?
2- Does my script needs to point to dash instead of bash?
3- How do I set the script to load after everything else?


**=> Method 1**
- Copy my script into /etc/init.d/[script_name]
- Make it executable
- Create link into /etc/rc3.d/S{xx}[myscript_name]
*Note: what should I set the {xx} to?*

**=> Method 2**
- Write a script and put it in the /etc/init.d/ directory
- Make it executable
- Run "sudo update-rc.d [script_name] defaults 90"


Thanks!!


Vic

---

### Post by Vivaldi Gloria on 2008-08-11
Last thing to get executed is /etc/rc.local. Call your script from it:

```
/path_to_your_script/script
exit 0
```

Don't forget to make your script executable.

---

### Post by sdennie on 2008-08-11
If it's just a simple command, it may be sufficient to just add it to /etc/rc.local.  It's already integrated into the init system and runs as a 99 process so, should run after everything else.

---

### Post by victorbrca on 2008-08-11
> **Vivaldi Gloria said:**
> Last thing to get executed is /etc/rc.local. Call your script from it:

```
/path_to_your_script/script
exit 0
```

Don't forget to make your script executable.

> **vor said:**
> If it's just a simple command, it may be sufficient to just add it to /etc/rc.local.  It's already integrated into the init system and runs as a 99 process so, should run after everything else.


Thanks a lot guys!!  :)


Vic.

---

