---
title: "how to install files from tar.gz archives on linux ubuntu"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by gagansinghjarry on 2008-09-27
hey guys i am new to the ubuntu concept and i was wondering if someone could help on how to install files from tar.gz archives on ubuntu any help would be appericiated

---

### Post by mikewhatever on 2008-09-27
It depends what's inside tar.gz, can be source code or binaries.
Here are some good guides:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

---

### Post by talsemgeest on 2008-09-27
First you need to see what is inside the archive. It could be a binary, in which case all you have to do is execute it, or it might be a shell script (.sh extension), where you should also be able to execute it. However, the most likely thing to be in it would be the source code for a program. You can usually tell from files like "configure", and other stuff like that.

---

### Post by gagansinghjarry on 2008-09-27
yup it contains an .sh file what am i supposed to do extract it or how do i install it i am sorry for the inconvineince i might be causing you guys but i am not much good when it comes to pc's

---

### Post by talsemgeest on 2008-09-27
Right click the file, then go properties. Go to permissions, then tick the box that says "Allow executing this file as a program". If it is already ticked, leave it. Close that now open the file, and a box should pop up giving you some options, and you should click "Run in terminal".

Hope this helps :)

---

### Post by phanipalagummi on 2008-09-27
this may help you,
                [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

---

### Post by gagansinghjarry on 2008-09-27
> **talsemgeest said:**
> Right click the file, then go properties. Go to permissions, then tick the box that says "Allow executing this file as a program". If it is already ticked, leave it. Close that now open the file, and a box should pop up giving you some options, and you should click "Run in terminal".

Hope this helps :)
all right thanks man will try it right now

---

### Post by gagansinghjarry on 2008-09-27
> **talsemgeest said:**
> Right click the file, then go properties. Go to permissions, then tick the box that says "Allow executing this file as a program". If it is already ticked, leave it. Close that now open the file, and a box should pop up giving you some options, and you should click "Run in terminal".

Hope this helps :)
i did just like you said a terminal window opened and closed itself and nothing mor pleas i really need your help if any one could help me i would be highly obliged

---

### Post by talsemgeest on 2008-09-27
Ok, it looks like the shell script ran, and then encountered an error. You can see what error it encountered by running it from a terminal. In a terminal, type ```
cd <directory that conatains the file>
``` changing it to put in the file pathway. Then type ```
sudo sh <filename>.sh
```, putting in the filename, and see what you get.

---

### Post by lswb on 2008-09-27
There is no standard method for installing from a .tar.gz file, though the sequence of

./configure
make
make install

is pretty common for tarfiles that contain source code.

Untar the file and cd to the new directory. Before you run any commands, look for a README file, DOCS folder, etc. Usually (not always) there will be some info in a text file to get you started. If not check the site where you originally obtained the tar file or even do a google search for info on the program you are trying to install. I would advise not just blindly running shell scripts without having some idea of what they do. Sometimes you can examine the scripts themselves to determine what they do.

---

### Post by gagansinghjarry on 2008-09-28
alright guys thanks for your support i think i got it

---

### Post by steveneddy on 2008-09-28
What does the Read Me file say to do?

---

### Post by gagansinghjarry on 2008-09-28
> **steveneddy said:**
> What does the Read Me file say to do?
would i be here if it had one no offense

---

### Post by steveneddy on 2008-09-28
> **gagansinghjarry said:**
> would i be here if it had one no offense

I don't know. Would you? Do you know to look for a Read Me file?

I don't know anything about you, I just am trying to answer your question.

Most applications come with a Read me file to tell you how to install and what to expect.

Even the dependencies will be listed is a better written Read Me file.

What are you trying to install?

Did you check to see if it was in the repos first?

Installing an application from the Ubuntu repositories would make a more stable system.

---

