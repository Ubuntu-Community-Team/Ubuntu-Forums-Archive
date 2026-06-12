---
title: "Installing applications of tar.gz and bzip2 in ubuntu"
date: 2009-06-20
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-06-20
Hello poh...

paano po ba mag install ng tar.gz anf bzip2 applications sa ubuntu???
please help poh

---

### Post by loell on 2009-06-20
depende kasi yan, kung ang archive ay binary or source.

first upack the archive, 

if it's a source then it's most likely

[B]./configure
make
make install
[/B]

if it's a binary archive then there's likely a

**./install.sh**


either way, a readme file should indicate what you should do.

---

### Post by wersdaluv on 2009-06-20
Each compressed folder (like tar.gz) has a unique way of being installed. The most common ways to install them are mentioned by loell. 

What specific tar.gz or bzip2 file do you want to install? =)

---

### Post by badrra on 2009-06-20
First thing you do after extracting it is to look for the readme file. It will give you specific instructions on how to install it and tell you what the dependencies are.

---

### Post by Lila_IT_CMU on 2009-06-20
ok poh...try ko po mag install...

marami akong file na tar.gz pero hindi ko alam kung paano mag install...

---

### Post by killer_d76 on 2009-06-21
what i usually do is..

1. extract the tar.gz files to desktop

2. open up terminal
 - type [PHP]sudo -s[/PHP] 
 - it will be asking for your password
 - this will give you and access as an admin

3. then open up the extracted tar.gz files on your desktop and look for a file that says: **install.sh**

4. drag and drop this file to the terminal that you have opened up earlier then hit enter on your keyboard.. this will automatically install everything for you.

;)

---

