---
title: "installing firefox 3"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-08-31
I am trying to install firefox 3 but I am doing something wrong.  Can someone tell me what I should do?

allan@allanlaptop:~$ cd firefox
allan@allanlaptop:~/firefox$
allan@allanlaptop:~/firefox$ chmod + x firefox-bin
chmod: cannot access `x': No such file or directory
allan@allanlaptop:~/firefox$ chmod firefox-bin
chmod: missing operand after `firefox-bin'
Try `chmod --help' for more information.
allan@allanlaptop:~/firefox$ chmod +x firefox-bin
allan@allanlaptop:~/firefox$ ./firefox-bin
./firefox-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory
allan@allanlaptop:~/firefox$

---

### Post by SuperSonic4 on 2008-08-31
Have you tried opening Adept and then clicking on firefox and clicking update?

---

### Post by BryanMarley on 2008-08-31
> **saskatchewan said:**
> I am trying to install firefox 3 but I am doing something wrong.  Can someone tell me what I should do?

allan@allanlaptop:~$ cd firefox
allan@allanlaptop:~/firefox$
allan@allanlaptop:~/firefox$ chmod + x firefox-bin
chmod: cannot access `x': No such file or directory
allan@allanlaptop:~/firefox$ chmod firefox-bin
chmod: missing operand after `firefox-bin'
Try `chmod --help' for more information.
allan@allanlaptop:~/firefox$ chmod +x firefox-bin
allan@allanlaptop:~/firefox$ ./firefox-bin
./firefox-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory
allan@allanlaptop:~/firefox$
okay im a total n00b with ubuntu, but for what im seeing, you are missing some kind of files. Maybe you should check if you installed your libjemalloc libraries? Becuase he cannot find them.

Im totally new as of today so im just guessing.

---

### Post by halitech on 2008-08-31
check out these instructions

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by halitech on 2008-08-31
> **SuperSonic4 said:**
> Have you tried opening Adept and then clicking on firefox and clicking update?

that will only update to whatever the latest version is in the repos which in my case (using 7.10) is ff2

---

### Post by saskatchewan on 2008-08-31
I don't understand how to "Have you tried opening Adept and then clicking on firefox and clicking update?"

Can you explain more?

---

### Post by oldsoundguy on 2008-08-31
Which version of Ubuntu?
For Hardy:  Go to System> Administration> Synaptic Package Manager> sign in> scroll down to Firefox, check to install and install.
Gutsy .. Firefox 3 can not be installed from the repositories, you have to go here: [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)
Now, once installed this way, the ONLY way you can update same is via their instructions on the page.  NO Gutsy REPOSITORIES will hold the updates.

---

### Post by SuperSonic4 on 2008-08-31
KMenu -> System -> Adept 

if you search for firefox and then look for an upgrade. As halitech said it needs to be in the repos, what version of kubuntu are you running?

---

### Post by saskatchewan on 2008-08-31
I am running Kubuntu on an AMD64

---

### Post by SuperSonic4 on 2008-08-31
Kubuntu Hardy? (8.04)

I believe firefox 3 is in the repos on hardy.

---

### Post by halitech on 2008-08-31
but are you running 7.04, 7.10 or 8.04?

---

### Post by saskatchewan on 2008-08-31
I can not find Firefox 3 in the repos.

---

### Post by saskatchewan on 2008-08-31
I just installed Kubunt a few days ago so it is the latest version.

---

### Post by halitech on 2008-08-31
FF3beta5 should already be installed then

---

