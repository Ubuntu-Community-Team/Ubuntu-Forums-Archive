---
title: "bash script problem with chroot"
date: 2006-07-26
forum: Programming Talk
---

### Post by kintarooe on 2006-07-26
I'm building a script to make it easier to set up new domains in our ubuntu cluster with a small script. It is set up to take a couple of needed parameters and it does the rest. The problem is i need it to chroot into our webserver and let it create a couple of directories, but i do not know how to send commands in line with chroot so that it does not pause. I also need it to exit without killing the script so that it can finish. Any help is appreciated.. :confused:

---

### Post by simonn on 2006-07-26
Why do you need to chroot?

---

### Post by fluffington on 2006-07-26
You can just put the command after chroot on the commandline.

From *chroot --help*:

> 
Usage: chroot NEWROOT [COMMAND...]
  or:  chroot OPTION
Run COMMAND with root directory set to NEWROOT.

      --help     display this help and exit
      --version  output version information and exit

If no command is given, run ``${SHELL} -i'' (default: /bin/sh).


---

### Post by kintarooe on 2006-07-27
The main part of the webserver that actually holds the content is jailed. thanks fluffington for the tip i didn't think to check the help (used the man instead). Does anyone know about exiting the new root without stopping my script?

---

### Post by kintarooe on 2006-07-27
nevermind about my last question ( i still thought it kept the new root open.

---

