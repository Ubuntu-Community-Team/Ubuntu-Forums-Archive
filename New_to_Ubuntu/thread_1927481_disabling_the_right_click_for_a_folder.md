---
title: "disabling the right click for a folder"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-02-18
i wish to disable the right click for any particular folder in ubuntu. okay i just want to do this to prevent accidental renaming of any files within that folder. like i have pdf files directly saved in the folder (say folder named 'downloads') via a browser where the filename is automatically provided or saved. so next time if i happen to download the same file i would be informed that the folder already contained the particular file. that would prevent me from downloading the same file again and again if in case i changed the filename of earlier existing filename as it's not possible to remember what's on so many files!
help!

---

### Post by tojonukokhadush on 2012-02-18
was it something i should not have asked?

---

### Post by androssofer on 2012-02-18
> **tojonukokhadush said:**
> i wish to disable the right click for any particular folder in ubuntu. okay i just want to do this to prevent accidental renaming of any files within that folder. like i have pdf files directly saved in the folder (say folder named 'downloads') via a browser where the filename is automatically provided or saved. so next time if i happen to download the same file i would be informed that the folder already contained the particular file. that would prevent me from downloading the same file again and again if in case i changed the filename of earlier existing filename as it's not possible to remember what's on so many files!
help!

seem a perfectly fine question to ask...


so what you want to achieve is:

you can add new files to a folder, but they cannot overwrite existing files with the same name, they must use a new name. eg:

file.txr

file(1).txt

---

### Post by tojonukokhadush on 2012-02-19
thankyou very much for your help!
but what i actually wish is to simply disable right clicking to prevent further activities that right click would allow us to do. is that possible in ubuntu operating system?
i am sorry if i elaborated unnecessarily at first hand!

---

### Post by tojonukokhadush on 2012-02-21
can not anybody say, how can we disable renaming a filename within a particular folder inubuntu?

---

### Post by tojonukokhadush on 2013-01-25
okay! just say me how can i disable right click on my system?

---

### Post by slickymaster on 2013-01-25
```
xmodmap -e "pointer = 1 2 99"
```
This will cause a right-click to produce a "Button 99" instead of a "Button 3" click event.

To make it permanent, you'll have to edit the last line of the **.bashrc** file in your home directory, adding that code to it:
```
xmodmap -e "pointer = 1 2 99"
exit
```

If you .bashrc doesn't exist in your home folder, just create it and insert the mentioned code.

---

