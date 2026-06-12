---
title: "Package operation failed message"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by hktrout on 2012-05-25
Hi,
Whenever I install for all the updates from Update Manager, I always get "Package operation failed " message window at the end of update process. It says "The installation or removal of a software package failed ". What should I do not to get this message window ? Thank you

---

### Post by kc1di on 2012-05-25
> **hktrout said:**
> Hi,
Whenever I install for all the updates from Update Manager, I always get "Package operation failed " message window at the end of update process. It says "The installation or removal of a software package failed ". What should I do not to get this message window ? Thank you

There could be a couple reasons for that. 
Here are some things you can try:

In  a Terminal type the following commands:

```
sudo apt-get autoclean
sudo apt-get clean
```

then these :

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 
```

Finally If none of those get rid of it. 
I would do this:
```
sudo apt-get install synaptic
```

when install go to synaptic and click on edit then fix broken packages.
I like synaptic for package management anyway. :) 

Let us know how that works out.

---

### Post by ajgreeny on 2012-05-25
> **kc1di said:**
> 
I would do this:
```
sudo apt-get install synaptic
```when install go to synaptic and click on edit then fix broken packages.
I like synaptic for package management anyway. :) 

Let us know how that works out.
I fully agree with this.

Synaptic, though a bit more complicated than ubuntu-software-centre, is by far the most flexible, all encompasing and wonderful package manager on any of the Linux systems I have ever seen or used.

It is always the first thing I install on new *ubuntu systems now that it has gone from the default install.

---

### Post by Haneef Mubarak on 2012-05-25
I have seen much positive sentiment about Synaptic. I have used it to fix many things, so I can vouch for it too. Perhaps we ought to have a poll...

---

### Post by hktrout on 2012-05-25
[QUOTE=kc1di;11967120]There could be a couple reasons for that. 
Here are some things you can try:

In  a Terminal type the following commands:

```
sudo apt-get autoclean
sudo apt-get clean
```

then these :

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 
```

Thank you so much for help! I don't get the failed massage anymore!

---

### Post by kc1di on 2012-05-25
> **hktrout said:**
> [QUOTE=kc1di;11967120]There could be a couple reasons for that. 
Here are some things you can try:

In  a Terminal type the following commands:

```
sudo apt-get autoclean
sudo apt-get clean
```

then these :

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 
```

Thank you so much for help! I don't get the failed massage anymore!
great :)
please mark the thread as solved

---

### Post by welyjan on 2012-09-04
> **kc1di said:**
> There could be a couple reasons for that. 
Here are some things you can try:

In  a Terminal type the following commands:

```
sudo apt-get autoclean
sudo apt-get clean
```

then these :

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 
```

Finally If none of those get rid of it. 
I would do this:
```
sudo apt-get install synaptic
```

when install go to synaptic and click on edit then fix broken packages.
I like synaptic for package management anyway. :) 

Let us know how that works out.
Hi Dave : 

I also had that error for a while, and I tried the command lines that you posted , still could not be able to fix the problem , 
everytime I tried to update , it gives this message : 

############################################
installArchives() failed:  Extracting templates from packages:  10%% Extracting templates from packages: 21%% Extracting templates from  packages: 32%% Extracting templates from packages: 42%% Extracting  templates from packages: 53%% Extracting templates from packages:  64%% Extracting templates from packages: 75%% Extracting templates from  packages: 85%% Extracting templates from packages: 96%% Extracting  templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 10%% Extracting templates from  packages: 21%% Extracting templates from packages: 32%% Extracting  templates from packages: 42%% Extracting templates from packages:  53%% Extracting templates from packages: 64%% Extracting templates from  packages: 75%% Extracting templates from packages: 85%% Extracting  templates from packages: 96%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 10%% Extracting templates from  packages: 21%% Extracting templates from packages: 32%% Extracting  templates from packages: 42%% Extracting templates from packages:  53%% Extracting templates from packages: 64%% Extracting templates from  packages: 75%% Extracting templates from packages: 85%% Extracting  templates from packages: 96%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 10%% Extracting templates from  packages: 21%% Extracting templates from packages: 32%% Extracting  templates from packages: 42%% Extracting templates from packages:  53%% Extracting templates from packages: 64%% Extracting templates from  packages: 75%% Extracting templates from packages: 85%% Extracting  templates from packages: 96%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ...  10%% (Reading database ... 15%% (Reading database ... 20%% (Reading  database ... 25%% (Reading database ... 30%% (Reading database ...  35%% (Reading database ... 40%% (Reading database ... 45%% (Reading  database ... 50%% (Reading database ... 55%% (Reading database ...  60%% (Reading database ... 65%% (Reading database ... 70%%dpkg:  unrecoverable fatal error, aborting: 
 reading files list for package 'libreoffice-style-human': Input/output error 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

######################################

when I typed the the  command line to download synaptic , it gives me another message : 

#############################

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  synaptic
0 upgraded, 1 newly installed, 0 to remove and 270 not upgraded.
Need to get 0 B/2,405 kB of archives.
After this operation, 7,779 kB of additional disk space will be used.
Selecting previously unselected package synaptic.
(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libreoffice-style-human': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

#########################

what could be the problem , I even tried to uninstall dpkg , and install it ; but it did not fix the problem . 

thank you for your post in advance .

---

