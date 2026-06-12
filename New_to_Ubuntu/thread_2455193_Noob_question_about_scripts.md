---
title: "Noob question about scripts"
date: 2020-12-14
forum: New to Ubuntu
---

### Post by lelolelo on 2020-12-14
I'm new to Ubuntu and I noticed I have a delay when I press Caps Locks and I found a script that claims to solve this problem [here]("https://github.com/hexvalid/Linux-CapsLock-Delay-Fixer/"). The problem is that I'm such a noob that I don't know how to run this script.

This is the code:
```
#!/bin/bash
#Linux CapsLock Delay Fixer by ErkanMDR /- HELYX

cd "${BASH_SOURCE%/*}" || exit

xkbcomp -xkb $DISPLAY xkbmap
fixpatchline=$(cat fixpatch)
perl -i~ -0777 -pe "s/key .CAPS[^}]+};/$fixpatchline/" xkbmap
xkbcomp xkbmap $DISPLAY
rm xkbmap*
echo "Problem fixed ;)"

```

Can someone tell me where should I place the .sh file for this to work?

---

### Post by yancek on 2020-12-14
Well, I've never had that problem but according to the site you refer to in your post, running the command shown there is supposed to do that:

```
bash -ic "sh bootstrap.sh" 
```

Good luck,

---

### Post by lelolelo on 2020-12-14
I already tried that, but I get this output: 
sh: 0: Can't open bootstrap.sh

I think I should place this file somewhere

---

### Post by rsteinmetz70112 on 2020-12-14
The permissions on the file are probably wrong. 
In a terminal window run

```
ls -ld dbootstrap.sh
```

Post the results.

---

### Post by lelolelo on 2020-12-14
> **rsteinmetz70112 said:**
> The permissions on the file are probably wrong. 
In a terminal window run

```
ls -ld dbootstrap.sh
```

Post the results.

-rwxrwxr-x 1 user user 273 Dec 14 13:03 bootstrap.sh

---

### Post by lelolelo on 2020-12-14
okay now I figured out how to run this script but it doesn't work. It disables Caps Locks and doesn't fix it.

---

### Post by Impavidus on 2020-12-15
This is the kind of problem-solving that causes problems.

You had an issue with a CapsLock delay. It's not a very common issue. If it were, it would have read about it, as I've been a regular on these forums for years. Then there's a script that claims to magically solve this issue, no matter what caused it. Of course, magical solutions can be very tempting to new users, but we try to avoid them on these forums.

What the script did was that it created a description of your keyboard mapping, replaced a line with the line from the file "fixpatch" (whatever is in there) and set it as the new keyboard mapping. Is doesn't look like there's an undo function, but using your keyboard settings to switch to a different layout and back to the original may restore the default.

---

### Post by lelolelo on 2020-12-15
I found the fix to this problem [here]("https://wiki.archlinux.org/index.php/Xorg/Keyboard_configuration#Switching_state_immediately_when_Caps_Lock_is_pressed"). It's working.

Thanks for all replies.

---

### Post by TheFu on 2020-12-15
Script files need to be either in the PATH somewhere or you need to correctly specify the exact location to the script file.
Also, the Unix permissions on the file need to allow read and execute for the userid trying to run the script.

So, to show some permissions, I created a /tmp/TT directory and quickly created some empty files inside it and made some odd permissions:
```
$ \ls -l
total 0
-rwxrwxr-x 1 tf tf 0 Dec 15 09:25 script-1
-rwx------ 1 tf tf 0 Dec 15 09:25 script-2
-------r-x 1 tf tf 0 Dec 15 09:25 script-3
----r-xr-x 1 tf tf 0 Dec 15 09:25 script-4
```

tf = thefu

To run script-1, I'd need to specify the exact path to that file.  ** /tmp/TT/script-1** is the answer.  Because my PWD/CWD is /tmp/TT/, I could also run it with **./script-1**  Using just script-1 shouldn't and won't work. My PATH environment variable does not include the CWD.
Check your PATH with 
```
echo $PATH
```

Of all those files, which can my 'tf' account run?  Answer: only the first 2.  script-3 and script-4 doesn't allow the file 'owner' either read or execute permissions, which is the same as blocking those even if 'other' permissions do allow it.

So, to run script-3, what do I need to change?  As it is now, anyone except me or userids in the 'tf' group can run it.

Unix permissions have an elegance about them, once they are understood.  You are unlikely to see permissions like script-3 and script-4 have very often, since the file owner can just chmod the permissions.  These permissions work the same for local or remote NFS storage, which is one of the reasons NFS is preferred over CIFS network storage.

---

