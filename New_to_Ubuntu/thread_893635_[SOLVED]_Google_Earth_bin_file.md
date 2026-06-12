---
title: "[SOLVED] Google Earth bin file?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Darbre on 2008-08-18
Hi

I used Synaptic to get Google Earth. All went well, I got v 4.2. The first time I tried to run it, I was told that there was an update to v4.3, did I want it? I said yes and now have a file on my desktop that called GoogleEarthLinux.bin. Clicking it brings up a box that says "no application installed for this file". Right clicking the file doesn't tell me anything. So.....my question is:  What do I do with a bin file?

Thanks

Darbre

---

### Post by Elfy on 2008-08-18
I think that you need to change to the desktop

```
cd Desktop
chmod a+x name_of_file.bin
sudo ./name_of_file.bin
```

You can use tab to auto fill file name - start with first letter then tab

---

### Post by Darbre on 2008-08-18
> **forestpixie said:**
> I think that you need to change to the desktop

```
cd Desktop
chmod a+x name_of_file.bin
sudo ./name_of_file.bin
```

You can use tab to auto fill file name - start with first letter then tab


That worked, but what did I do? Why was it necessary? Rather than just execute commands, I'd like to know a little bit about what the command does.

Thanks

Darbre

---

### Post by Elfy on 2008-08-18
cd - change directory - change to the Desktop, in linux desktop would be different

chmod - you used to make the file file executable 

sudo *superuser*do - allows commands to be run with root rights

the rest ran the command

Most commands have a manual entry which can be got from terminal eg man chmod

Simplistic descriptions, which might be slightly 'off' but that is the jist of it.

---

### Post by Darbre on 2008-08-18
Thanks again. I appreciate your time

Darbre

---

### Post by junglist313 on 2008-08-18
I have been wondering about this same question for a few days now. The difference between 4.2 and 4.3 is jaw dropping! It now runs faster than ever. Thank you forestpixie! 
=D>=D>=D>=D>=D>

---

