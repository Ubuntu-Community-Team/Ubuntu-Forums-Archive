---
title: "Open Folder from Terminal"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by Quarkrad on 2013-08-09
I can open my Documents folders with the command:

**nautilus /home/dad/Documents**

but I cannot open the Ubuntu One folder with:

**nautilus /home/dad/Ubuntu One**  

I'm told there is no file or directory.  I am trying to do this becasue I have created in my **Ubuntu One** folder another folder called **Passwards** that I want to put on the Unity Launcher.  I'm OK making .desktop commands to do this but I need to create a command to open this folder i.e. nautilus /home/dad/Ubuntu One/Passwords

For some reason I cannot open my **/home/dad/Ubuntu One/Passwords** folder via the terminal.  Any help appreciated.

---

### Post by prodigy_ on 2013-08-09
> **Quarkrad said:**
> I cannot open the Ubuntu One folder with:

**nautilus /home/dad/Ubuntu One**
Add double quotes: ```
nautilus "/home/dad/Ubuntu One"
nautilus "/home/dad/Ubuntu One/Passwords"
```

---

### Post by SlugSlug on 2013-08-09
It's due to the space you can use quotes or slash it out. The easiest way is to type
[B]nautilus /home/dad/Ubuntu[hit tab key]

[/B]

---

### Post by Quarkrad on 2013-08-09
Thank you - great.  For my own info; I note that both **nautilus /home/dad/Documents** and **nautilus "/home/dad/Documents"** both open but **nautilus /home/dad/Ubuntu One** does not work but, as you kindly pointed out, **nautilus "/home/dad/Ubuntu One"** does work.  What is special about the Ubuntu One folder that needs the quotes?  Are there any other folders in Ubuntu that also need these quotes?

---

### Post by Deuce1912 on 2013-08-09
> **Quarkrad said:**
> Thank you - great.  For my own info; I note that both **nautilus /home/dad/Documents** and **nautilus "/home/dad/Documents"** both open but **nautilus /home/dad/Ubuntu One** does not work but, as you kindly pointed out, **nautilus "/home/dad/Ubuntu One"** does work.  What is special about the Ubuntu One folder that needs the quotes?  Are there any other folders in Ubuntu that also need these quotes?

Any directory or file with a name that has a space will need the quotes.

Deuce1912

---

### Post by SlugSlug on 2013-08-09
or a slash

**nautilus /home/dad/Ubuntu\ One**


But as above it's a lot easier to use the tab key

---

### Post by prodigy_ on 2013-08-09
Unescaped whitespaces are normally treated as delimiters between arguments. In case of **nautilus /home/dad/Ubuntu One** nautilus actually tries to open two folders: **/home/dad/Ubuntu** and **./One**. Since none of them exists, you get an error message. To prevent this behavior you need to either prepend (escape) every literal whitespace with a backslash (**nautilus /home/dad/Ubuntu\ One**) or use double quotes to separate the path from the rest of the command line (**nautilus "/home/dad/Ubuntu One"**).

---

### Post by Quarkrad on 2013-08-09
Thanks for that explanation.

---

