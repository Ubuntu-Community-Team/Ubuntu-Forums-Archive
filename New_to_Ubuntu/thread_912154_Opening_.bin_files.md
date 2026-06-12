---
title: "Opening .bin files"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Zopiac on 2008-09-06
i want to install DangerDeep from its .bin file, but dont know how, etc.

/home/zopiac/Downloads/dangerdeep-0.3.0-linux-installer.bin

i already tried properties>make executable but there is no program to open it...

what are the commands?

---

### Post by RealPSL on 2008-09-06
From a terminal (Applications > Accessories -> Terminal)
```
$ chmod u+x /home/zopiac/Downloads/dangerdeep-0.3.0-linux-installer.bin
$ /home/zopiac/Downloads/dangerdeep-0.3.0-linux-installer.bin
```

If you do not want to use the terminal you can also do this from Nautilus byt right clicking the file and checking the "Allow executing file as program". You can then double click the file to run it but since I have never installed that program I am not sure what will happen next. Doing it from the command line (terminal) might be a little easier.

The "$" in the above command just signifies the prompt so do not type it. Sorry if I am giving you too much detail.

---

