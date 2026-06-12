---
title: "How do find files that are containing an text."
date: 2011-10-26
forum: New to Ubuntu
---

### Post by ryanrio95 on 2011-10-26
Hi.

I would like to know an command where i can search files with.
For example, i have an directory with files AND subdirectories,
and i just want to pick the text file that contains $string.

Can anyone help me?

Thanks in Advance.

---

### Post by nothingspecial on 2011-10-26
If you are in the parent directory you can type

```
grep -r pantomime *
```

to search for the word pantomime in all the files in all the subdirectories of that directory and all the files in the subdirectory itself.

Type ```
man grep
``` to see other options, such as how you would like the results outputted.

---

### Post by KL_72_TR on 2011-10-26
Or maybe you can use these commands:
```
locate
``````
find
```Don't forget to read the
```
man
```and
```
info
```
of each command.

---

### Post by ryanrio95 on 2011-10-26
> **nothingspecial said:**
> If you are in the parent directory you can type

```
grep -r pantomime *
```to search for the word pantomime in all the files in all the subdirectories of that directory and all the files in the subdirectory itself.

Type ```
man grep
``` to see other options, such as how you would like the results outputted.

Thanks, this does what i want :)

---

### Post by ajgreeny on 2011-10-26
The grep command is incredibly handy for a huge number of very useful, but generally unimportant uses, eg 

[LIST=1]
[*]to see the listing of your grub menu without looking all through /boot/grub/grub.cfg use ```
grep menuentry /boot/grub/grub.cfg
```
[*]to see what you have recently installed/removed/upgraded with synaptic or apt-get or update manager use ```
grep -w upgrade /var/log/dpkg.log*
```changing the word "upgrade" to "remove" or "install," for what you wish to see.
[/LIST]
I'm sure there are hundreds (thousands?) more examples other users can offer as well, but I thought it worth drawing your attention to grep for those simple things.

---

