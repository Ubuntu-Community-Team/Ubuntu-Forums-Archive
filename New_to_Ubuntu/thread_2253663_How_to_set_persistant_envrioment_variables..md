---
title: "How to set persistant envrioment variables."
date: 2014-11-21
forum: New to Ubuntu
---

### Post by khan3 on 2014-11-21
I want to append the Path and set a new environment variable and make it persist how can i do this.

e.g With the above 2 after entering in my location.

export ANDROID_HOME=/<installation location>/android-sdk-macosx
export PATH=${PATH}:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools

---

### Post by nerdtron on 2014-11-21
Add those two lines on you .bashrc file on your home folder. It's a hidden file so you may need to show hidden files from the files browser. And remove the word "export" when you add the lines.

---

### Post by slickymaster on 2014-11-21
You can add it to the file **.profile** or **.bashrc** or your current shell profile file (located in your home directory). Then, each time you open your shell it will be loaded.

If you want to make it permanent for all users, you can edit **/etc/profile** or **/etc/environment**.

---

### Post by khan3 on 2014-11-21
So i did this

sudo su
nano /home/.bashrc

My bashrc file is completely empty added them in without the export. saved and closed. 

It still didint save them. When i echo $ANDROID_HOME it returns nothing.

Right its because i was using su, i best go back and delete that

---

### Post by nerdtron on 2014-11-21
> **khan3 said:**
> So i did this

sudo su
nano /home/.bashrc



 Nope and nope. Don't have to be root, just your normal user. Open a terminal and just type the following (since you are already on your home directory):
```
nano .bashrc
```

The file should already have contents. Just put your custom lines on the bottom of the file.

And you can do this in GUI too. Just open your home folder and show hidden files and you should see the .bashrc file.

---

### Post by khan3 on 2014-11-21
yep i realised that after, ty

---

### Post by bilkay on 2014-11-21
Keep in mind that your .bashrc changes won't take effect until you open a new terminal.

---

