---
title: "[SOLVED] How to Paste?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-07-18
How do you paste something from the terminal (I want to paste a document from my Desktop to /usr/local/bin)?

---

### Post by SuperSonic4 on 2008-07-18
[color=#007fff]In terminal paste is either ```
shift + insert
``` or ```
ctrl + shift +v
``` copying it is ```
ctrl+shift+c
``` although you'll need root access to paste into /usr I believe[/color]

---

### Post by t0p on 2008-07-18
You select what you want to copy by holding down the left mouse button and highlighting the required text.  Then you press the right mouse button and select **Copy** from the menu.  Next you navigate to the destination file and left-click where you want the text to appear. Finally, you right-click, and select **Paste** from the menu.

It's basically the same as you would copy-paste in Windoze.

---

### Post by redfox1160 on 2008-07-18
What I meant was that I have something on my desktop that I want to put into another folder; how do I do this in the terminal?

---

### Post by t0p on 2008-07-18
> **redfox1160 said:**
> What I meant was that I have something on my desktop that I want to put into another folder; how do I do this in the terminal?

To copy a file from your desktop to /usr/local/bin you'll give the command:

```
sudo cp ~/Desktop/file /usr/local/bin/
```

where "file" is the name of the file you want to copy, and you don't want to change its name.

If you want to move the file rather than copy it, you'd substitute the command "mv" instead of "cp".

---

### Post by redfox1160 on 2008-07-18
thanks!

---

