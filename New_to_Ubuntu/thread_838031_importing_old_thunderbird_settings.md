---
title: "importing old thunderbird settings"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-06-23
Okay, new problem. I used the terminal to get thunderbird. Cool, it worked. I have my old thunderbird, with the randomly generated number named folder in my hard drive. I dragged it to the new hidden thunderbird folder, and deleted the old one. 
Now, when I try to click on the thunderbird icon, it tells me thunderbird is running and to shut it down first or restart the computer. Okay, so I restart, and it is still doing it. 
What do I do now?

---

### Post by dracayr on 2008-06-23
open a terminal and type ```
ps -e|grep thunderbird
```. post the output

dracayr

---

### Post by Nepherte on 2008-06-23
This will most likely solve it:
```
kill $(pidof thunderbird-bin)
```

---

### Post by Andrew79 on 2008-06-23
> **dracayr said:**
> open a terminal and type ```
ps -e|grep thunderbird
```. post the output

dracayr

it did nothing?

---

### Post by Andrew79 on 2008-06-23
> **Nepherte said:**
> This will most likely solve it:
```
kill $(pidof thunderbird-bin)
```

this did nothing also??

---

### Post by Nepherte on 2008-06-23
If it did nothing, it killed the process and you should be able to restart thunderbird. If you got this message:
```
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
```
then the process was already killed. In both cases you should be fine now.

---

### Post by dracayr on 2008-06-23
> **Andrew79 said:**
> this did nothing also??

In that case, your thunderbird installation is most likely screwed up. try a reinstall

```
sudo apt-get --reinstall install tunderbird
```

EDIT: This is only the case if 'did nothing' means that thunderbird still doesn't work

dracayr

---

### Post by tubbygweilo on 2008-06-23
Andrew,
before going any further can you recover the old and working ThunderBird from your deleted items Wastebasket? If so then change the name so as to keep it safe.

Assuming that you have recovered the old ThunderBird folder then please right click on the folder and select the Create Archive option and place this newly created archive on your desktop. Once you have created the archive now again right click on the folder but this time select the Extract option and extract into your home folder. 

I have found that the process of creating and then extracting preserves all file permissions as well as overwriting the target folder and it works rather well for transferring both FireFox and ThunderBird folders between machines.

---

### Post by Andrew79 on 2008-06-23
okay, so I was able to get it to restart, and it imported my emails. This is a fresh install for me, and off my last go, I saved my old folder with the randomly generated number folder name. How do I take that folder, with all the email folder(my contacts) into the new one so it will sort out all my emails? I had quite a few, so going through all my emails again would take a really long time.

---

### Post by dracayr on 2008-06-23
tubbygweilo already answered your question 1 post above yours...

dracayr

---

### Post by Andrew79 on 2008-06-23
okay, tried that, after extracting to the home folder it tells me there is an error, and has a button for the command line error

---

