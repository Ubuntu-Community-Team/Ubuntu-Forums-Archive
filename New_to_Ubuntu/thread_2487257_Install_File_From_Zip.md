---
title: "Install File From Zip"
date: 2023-05-29
forum: New to Ubuntu
---

### Post by zulrifiansyah on 2023-05-29
Hi there! I am new on Ubuntu 23.04

There is an application that says " Open terminal and choose this file directory and follow the instruction ./install.sh"

I try to drag the folder from file to terminal and it says "no file directory selected", or something like that. However, any suggestion? If there is a right way to install a program from Zip file, i really want to know. Thank you.

---

### Post by mIk3_08 on 2023-05-29
I think you should do the unzip command via terminal.
Open terminal and type the command below:
```
unzip source_filename.zip
```
when you already unzip the file be sure you make it an executable. To make it executable, run the command below:
```
chmod +x install.sh
``` 
If it needs permissions, you'll need the root access. 
```
sudo chmod +x install.sh
```
Then execute the install.sh script. To do this with root access, type the command below:
```
sudo ./install.sh
```
Reminder: You should know the parent directory of the file. Regards and cheers

---

