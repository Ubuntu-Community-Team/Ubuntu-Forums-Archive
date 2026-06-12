---
title: "DESKTOP LOADING SLOW ON LOGIN UBUNTU 14.04lts"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by rael2 on 2016-01-12
Hi, i am using ubuntu 14.04 with unity and  after i tried to change the login screen picture using this tutorial below, now i have to wait 10-12 seconds for desktop to load.Before this it took like 3 seconds.

I've tried to undo this by running  xhost -SI:localuser:lightdm and sudo restart lightdm but there is no difference.
I do not know what more details to provide  


**1.** Press Ctrl+Alt+T on keyboard to open the terminal. When it opens, run the command below to install dconf-editor:

 sudo apt-get install dconf-editor **2.** Run command to get the root user privilege:
 sudo -i **3.** Allow user **lightdm** to create a connection to the X server:
 xhost +SI:localuser:lightdm **4.** Switch to user **lightdm** in this terminal window.
 su lightdm -s /bin/bash **5.** Now you can start the dconf-editor via this user by running:
 dconf-editor When the tool opens, navigate to **com –> canonical –> unity-greeter**. Then change the background value to your custom image and disable both **draw-grid** and **draw-user-backgrounds**
 

 After all, restart your computer and enjoy!


I would be grateful if i could get some help with this.

Thank you

---

### Post by DuckHook on 2016-01-13
Hi rael2 and welcome to the 'buntu forums,

Firstly, I think it is very commendable that you tried a solution first before asking for help. Well done.

After you executed the tutorial, did your desired logon screen load? If not, then did you encrypt your /home directory when you installed? Where is the desired login picture that you wanted to load? Please give the full path and file name. Then open a terminal and do:```
ls -la <path_to_picture>/<name_of_file>
```...replacing my <place_markers> with the actual path and name of your file. Post results back to this thread.

---

