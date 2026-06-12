---
title: "[SOLVED] lost pardus admin and user passwords help please"
date: 2008-09-03
forum: Other OS Talk
---

### Post by benjaminjames on 2008-09-03
hi all i recently installed pardus on my lil brothers box but forgot to write down the password and username i set for him grrr, will i have to reinstall or is there a program or script(im not very good with terminal work tho)i can use any help will be appreciated thanks all

---

### Post by pelle.k on 2008-09-03
1. learn from your mistake. bad benjaminjames!
2. add "single" as a parameter in grub (the kernel line with parameters)
3. run passwd <username>

---

### Post by benjaminjames on 2008-09-03
hi thanks for the speedy reply but i have no idea how to do what you suggested im a bit non technical :)

---

### Post by pelle.k on 2008-09-03
2. At the grub boot menu (where you choose operating system), select the option that lets you edit the kernel parameters (i belive you press F6 or something if i remember correctly). Add "single" (without the "" of course) to the end of the kernel parameters, then continue booting up.
3. At the terminal prompt, run "passwd <TheUserNameHere>" (without <>), you will be asked to enter a new password, then reboot. (btw, the "reboot" command does just that, but you may press ctrl-alt-delete as well)

---

### Post by benjaminjames on 2008-09-04
cool thanks but i cant even remember the user name lol

---

### Post by pelle.k on 2008-09-04
ah, ok!
at the command prompt, type
```
cat /etc/passwd | tail -n5
```

That will show the file with users, and the "|" sends that to tail, wich cuts out the last 5 entries in that file (where he probably is).
The output may be a little cryptic, but the username is the first thing on a line, before a ":".

I hope that makes sense :)

---

### Post by benjaminjames on 2008-09-04
ok so here is the output, i take that the username is josh is that correct? btw thank you for being so patient. so now i have to add the line in the grub booter is that correct?
Josh@Josh-pardus ~ $ cat /etc/passwd | tail -n5
ups:x:133:133:UPS:/var/lib/nut:/bin/false
pnp:x:200:200:PnP:/dev/null:/bin/false
teamspeak:x:400:400:Teamspeak:/dev/null:/bin/false
Josh:x:1000:100:josh:/home/Josh:/bin/bash
nobody:x:65534:65534:nobody:/:/bin/false

---

### Post by pelle.k on 2008-09-04
```
Josh:1000:100:josh:/home/Josh:/bin/bash
```
That is correct! Be sure to remember that letters in linux are case sensetive, so it's important that you capitalize the J in Josh.

Now that you know the name of your user, go ahead with the steps i outlined in post #4.
Please, don't hesitate to ask if you get it wrong.

---

