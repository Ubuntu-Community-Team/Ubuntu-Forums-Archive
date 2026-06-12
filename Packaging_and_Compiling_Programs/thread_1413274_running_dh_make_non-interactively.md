---
title: "running dh_make non-interactively"
date: 2010-02-22
forum: Packaging and Compiling Programs
---

### Post by donkyhotay on 2010-02-22
I recently wrote a bash script that can take my source code and automatically create a .deb package out of it. My script is designed to run without any debian files and uses dh_make to create some of them for me. In it I have the line:
```

dh_make -s -e myemail@myhost.com -c gpl3 -f myproject.tar.gz

```
This works well except for the fact dh_make stops my entire script to confirm the settings are correct before creating the default files forcing me to press enter to allow my script to continue. I want my script to run automatically without requiring any input from me. I've read through the dh_make man pages and am unable to find any way of running dh_make non-interactively, Does anyone know of a way to do this or possibly a workaround to this issue?

---

### Post by donkyhotay on 2010-03-02
No one here knows how or even if this can be done?

---

### Post by SevenMachines on 2010-03-03
i dont know how it can be done elegantly but if you're sure that all the options are fine and it only stops for you to confirm at the end (and wont stop to ask you questions, otherwise this will end in a loop!) 

$echo "garbage or enter or something" | dh_make <options>

you get the idea anyway, i imagine theres a better way to do this than piping stdin input but i cant think of it off hand

---

### Post by donkyhotay on 2010-03-08
I don't need elegance, and I know my commands are right since every time I run it I always have to wait a few minutes for my script to reach that point then press enter so it can continue going for a few more minutes. I'd rather just start it and let it go without any necessary input from me. I'll try this out and see if it works.

---

### Post by donkyhotay on 2010-03-09
Yep, thats what I needed. It's an ugly hack but it lets me start my script and then let it run for an hour or so without having to do anything else which is the reason for the script in the first place.

---

