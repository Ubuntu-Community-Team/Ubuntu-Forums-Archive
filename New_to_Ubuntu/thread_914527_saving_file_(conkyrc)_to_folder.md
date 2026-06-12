---
title: "saving file (conkyrc) to folder"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by madshad on 2008-09-08
permission denied, I thinkit was the home folder i was to save this too. I didnt write the conky code i downloaded one, i copied the text and named a text file on my desktop, but i just cant figure out how or where i am to save it. if it was home folder permission denied.

thanks!

---

### Post by iaculallad on 2008-09-08
> **madshad said:**
> permission denied, I thinkit was the home folder i was to save this too. I didnt write the conky code i downloaded one, i copied the text and named a text file on my desktop, but i just cant figure out how or where i am to save it. if it was home folder permission denied.

thanks!

Try it with sudo:

```
sudo cp /source/file_to_copy /destination
```

---

### Post by madshad on 2008-09-08
hmm , do i have to change the directory that i am in, in terminal, i cant seem to get the terminal to the desktop folder or any other one that i can save to.

im completely new to all this, sorry

sudo cp /home/-user-/Desktop/.conkyrc /home

i tried that and also just 
/desktop/ .file /home

/gedit/ .file /home

---

### Post by iaculallad on 2008-09-08
> **madshad said:**
> hmm , do i have to change the directory that i am in, in terminal, i cant seem to get the terminal to the desktop folder or any other one that i can save to.

im completely new to all this, sorry

sudo cp /home/-user-/Desktop/.conkyrc /home

i tried that and also just 
/desktop/ .file /home

You could just do this (you're copying from your home directory so there's no need of using sudo):

```
cp ~/Desktop/.conkyrc ~
```

The tilde (~) sign represents your home user directory.

EDIT: Or it might be the other way around:

```
cp ~/.conkyrc ~/Destkop
```

---

### Post by madshad on 2008-09-08
no im copying too the home folder

---

### Post by madshad on 2008-09-08
ahhh yah that worked!!
 thank you so much

---

