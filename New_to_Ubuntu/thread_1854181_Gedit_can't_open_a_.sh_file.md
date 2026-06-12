---
title: "Gedit can't open a .sh file"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by nuubtronic on 2011-10-03
Hi everyone,

My professor wants me to download an old version of the <oXygen/> XML editor, but I can't open the file I've downloaded. The download is named "oxygen-32bit.sh", and this is the error message I get in gedit:

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

Thanks in advance,

nuubtronic

---

### Post by CharlesA on 2011-10-03
You'd have to run it from a terminal instead of opening it in gedit.

---

### Post by nuubtronic on 2011-10-03
Gladly. Can you please coach me through how to do that?

---

### Post by hyper2hottie on 2011-10-03
It would appear that the file is not a text file.  You can check the file type with
```
file /directoryOfFile/File
```If you still want to look at the file in a text editor you can use kate, vi, or vim.  They will all open binary files.  It will just be a mess of stuff you probably can not understand though.

EDIT:
To view the file with vi open a terminal with crtl-alt-t and type
```
vi /directoryOfFile/File
```

---

### Post by Cyjan on 2011-10-03
> **nuubtronic said:**
> Gladly. Can you please coach me through how to do that?

when you double click on the .sh file ubuntu should give you an option either to "run", "display" or "run in terminal"

no?

---

### Post by HermanAB on 2011-10-03
If you really want to look at a binary file, install hexedit.

---

### Post by mcduck on 2011-10-04
That sounds like the download was corrupted (.sh extension on a binary file would make no sense at all).

Did you try opening the file directly from the browser, or did you download it to your computer first?

---

### Post by cavh on 2011-10-04
1. In your file manager, right-click the file and choose 'open in terminal'

2. In the terminal, type this command to make the file executable:

```
chmod u+x oxygen-32bit.sh
```

3. Still in the terminal, type this to run the file:
```

./oxygen-32bit.sh
``` Note - the dot and the slash are important

---

### Post by nuubtronic on 2011-10-04
> **mcduck said:**
> That sounds like the download was corrupted (.sh extension on a binary file would make no sense at all).

Did you try opening the file directly from the browser, or did you download it to your computer first?

I did download the file first. It's presently in my download folder.

---

### Post by nuubtronic on 2011-10-10
> **Cyjan said:**
> when you double click on the .sh file ubuntu should give you an option either to "run", "display" or "run in terminal"

no?

No, I'm not getting those options. It wants to open automatically in gedit.

---

### Post by nuubtronic on 2011-10-10
> **cavh said:**
> 1. In your file manager, right-click the file and choose 'open in terminal'

2. In the terminal, type this command to make the file executable:

```
chmod u+x oxygen-32bit.sh
```3. Still in the terminal, type this to run the file:
```

./oxygen-32bit.sh
``` Note - the dot and the slash are important

I'm still having trouble opening the file in terminal. I don't seem to have that option.

---

### Post by nuubtronic on 2011-10-10
Okay, I've got a fix that worked. You guys may have mentioned this part, but I just didn't get how to open the file in the terminal.

Here's what worked:

user@User-Netbook:~$ cd /home/user/Downloads/
user@User-Netbook:~/Downloads$ chmod u+x oxygen-32bit.sh
user@User-Netbook:~/Downloads$ ./oxygen-32bit.sh

---

