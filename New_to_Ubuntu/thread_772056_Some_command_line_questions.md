---
title: "Some command line questions"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by jacatone on 2008-04-28
How would I specify Console to download a program but not automatically install it? Just save it somewhere as a .deb file. Also, what command would I use to tell Console to update a particular program that I already have installed like say Firefox? Thanks.

---

### Post by skymera on 2008-04-28
in the terminal type

```
 sudo apt-get --help 
```

That should bring up all the possible parameters.
One of them is download only =)

I would test but im in college and stuck on Windows *sob*

---

### Post by Google Spider on 2008-04-28
When you run sudo apt-get install package_name it downloads and stores the deb file in **/var/cache/apt/archive** but also installs it.

You can go to the repos through your browser to download deb files.

---

### Post by southernman on 2008-04-28
> **jacatone said:**
> How would I specify Console to download a program but not automatically install it? Just save it somewhere as a .deb file. Also, what command would I use to tell Console to update a particular program that I already have installed like say Firefox? Thanks.

Question one- One way is to use "wget" by doing a:
```
wget http://somedomain.tld/path_to_file.extension
```

Question two- Well, if there is an update available for a ubuntu supported program ( like firefox ) then the notification icon will pop up and ask if you want to install it. 

To install something in Ubuntu via the terminal or console just do:
```
sudo apt-get update
sudo apt-get install <program name>
```

---

### Post by hyper_ch on 2008-04-28
```

sudo apt-get install -d PACKAGE

```

---

### Post by Tatty on 2008-04-28
> **jacatone said:**
> Also, what command would I use to tell Console to update a particular program that I already have installed like say Firefox? Thanks.

You can check for changes in the repos and install any updates with
```
sudo apt-get update
sudo apt-get upgrade
```

**Edit:** lol sorry southernman, i didnt see you had already replied when i typed this :)

---

### Post by gunbladeiv on 2008-04-28
the easiest way to get a source package is by doing this:
```
sudo apt-get source <package name>
```
This command will download the source to current location without installing em. 
Hope this will help

---

