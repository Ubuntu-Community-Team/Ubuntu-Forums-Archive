---
title: "web interface to create config files"
date: 2007-09-19
forum: Programming Talk
---

### Post by zero-9376 on 2007-09-19
hi im looking to create a small web application that will read a config file on the host os which should contain a list of paramaters and options for each of those paramaters, i want to have a web app read the config and create html menus based on the options, i then want the app to read what the user selects and generate a config file based on the selected options. all files are stored on the server in specific locations used by other apps. 

id like to use something that wont require to much in the way of system resources resources. ive just started with python, so i was looking at turbogears/pylons but i was wondering if anyone has a better solution that would allow me to implement this functionality quickly (as in i need it in a couple of days).

thanks

---

### Post by CptPicard on 2007-09-19
Sounds like you should keep on looking at Turbogears/Pylons if you've got your start with Python... other ways of doing things are at least as complex.

Just make sure you keep your application secure if you're altering some important config file, your app sounds like a potential security hole...

---

### Post by zero-9376 on 2007-09-19
the config file im editing should be fixed within the program and it only relates to my other applications. thanks, ill keep looking at turbogears as it is apparently more new-user friendly

---

### Post by danbh on 2007-09-23
Hey there.  I think you should just do the page in javascript and maybe jQuery, and a language that can process the config files, like php (I would think that python can do it too, but I haven't ever used python).  It doesn't sound like you need a whole model/view/controller framework.  Turbogear looks like it is used for a database that needs a variety of views and controller functions.  You only need a single view, and a single action.

---

### Post by zero-9376 on 2007-09-24
i have actually just spent the weekend (the whole weekend! without sleep) creating the system based on turbogears. given that i am new to python and have long forgotten my html im pretty happy with the way it turned out. the big advantage of turbogears is not having to run another server. the code will get a clean up once once i learn more and after my thesis is submitted. thanks for the help.

---

