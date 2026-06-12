---
title: "Quick question about .txt files"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by primky on 2008-06-08
When i open file with .txt extension, menu pops up, where i can select "Display", "Run in terminal", "Run"...

 I am wondering if i can set somewhere with what program i am opening specific filetypes. For example .txt with Text Editor. Then it would open it automatically, without selecting "Display".

---

### Post by balachandarlinks on 2008-06-08
press Alt+F2 .....type gconf-editor..then
  Go to **apps-->nautilus--->preference**
        in that you will find a **row as executable text activation**....just click on its value and erase its value and leave it blank....
        Thats all your problem solved....:popcorn:

---

### Post by bruce89 on 2008-06-08
> **balachandarlinks said:**
> press Alt+F2 .....type gconf-editor..then
  Go to **apps-->nautilus--->preference**
        in that you will find a **row as executable text activation**....just click on its value and erase its value and leave it blank....
        Thats all your problem solved....:popcorn:

Or slightly less strange:

[LIST=1]
[*]Open file manager (Nautilus)
[*]Edit>Preferences
[*]Behaviour tab
[*]Executable text file section
[/LIST]

Why are these text files marked as executable?

---

### Post by primky on 2008-06-08
Thanks, it worked. But at "executable_text_activation" i had to type "display", not leave it empty, otherwise when you click on any file, nothing shows up.

---

### Post by balachandarlinks on 2008-06-08
For me it works fine and opened in gedit .....:)

---

### Post by bruce89 on 2008-06-08
> **balachandarlinks said:**
> **But You thanked bruce89?????**


I'm too charming I think. I've thanked you then.

---

### Post by balachandarlinks on 2008-06-08
Its ok....I shouldnt write like that ...sorry....
  anyway cheers...one problem solved....:guitar:

---

