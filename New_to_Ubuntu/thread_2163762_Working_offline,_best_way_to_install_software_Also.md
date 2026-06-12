---
title: "Working offline, best way to install software? Also, general help with Ubuntu..."
date: 2013-07-19
forum: New to Ubuntu
---

### Post by MackDaddyMcFresh on 2013-07-19
Hi all,

I'm completely new to Ubuntu, and I am working off of a virtual machine at work that has no internet access.  All development must take place on this machine, and I am having a hard time getting the necessary tools and resources installed to it.  I was just curious what the suggested method of installation is if apt-get cannot access the internet.  I have been grabbing the individual .deb packages and using **dpkg --install** to get software on there up to this point, but I'm hoping there is a better method than just trying to install a package, seeing its missing dependencies, then retrieving those dependencies and getting deeper and deeper into a tree of necessary packages.  

I'm going to school for software engineering, but thus far we've only worked in Windows in environments like Visual Studio and Netbeans.  I'm at an internship now, and they've got me working on this virtual machine with Ubuntu 13.04, coding in python, and using a bunch of resources that I'm completely new to (MySQL, Werkzeug, Jinja2, XAMPP, etc.).  I've learned much in the past six weeks, and--until yesterday--I've had all of these resources playing nicely together and I've been coding away on my web application, but when I tried to install Google Chrome on the vm to test browser compatibility, my virtual environment stopped working and is telling me that I don't have mysql installed anymore.  If anyone with more experience can take a second to explain why something like this might occur or point me in the direction of a resource that can deepen my understanding of how this system works, I would greatly appreciate it; I don't want to have to be afraid of modifying anything on my vm and having it inexplicably stop working.  Thank you so much for any help, and let me know if you need more info from me in order to address any of these questions.

---

### Post by lukeiamyourfather on 2013-07-19
When you mean offline do you mean no internet access but you're still on a network or do you mean completely isolated with no network connection at all? The reason I ask is you could setup a local mirror of the Ubuntu repositories and still be able to use "sudo apt-get install build-essential" or whatever you want to install. The machine could be setup to point to the local network repository and off you go. If there's no network connection at all, maybe Debian would be a better option because you can download DVD's that contain every single package in the repositories (it's like 20GB of downloads). I don't think Ubuntu has that, so you're stuck downloading packages one at a time as you need them. If I'm wrong and Ubuntu has this feature, someone please correct me!

---

### Post by MackDaddyMcFresh on 2013-07-19
It's completely isolated; no network access :(

---

### Post by lukeiamyourfather on 2013-07-19
> **MackDaddyMcFresh said:**
> It's completely isolated; no network access :(

Maybe you can do this on another machine and then use a portable USB flash drive or hard drive to get it to the isolated machine?

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by lukeiamyourfather on 2013-07-19
This is interesting too, apt-mirror.

[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher](http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher)

Again, you'd need something to transport the data to the isolated machine.

---

### Post by MackDaddyMcFresh on 2013-07-19
Thanks for the help, I'll definitely look into this in the near future.  I've gotten my web app running again, but I'm going to do an overhaul soon and try to rebuild the environment from the ground up with an understanding of everything that I'm doing.  I'm not a huge fan of the "poke it with a stick until it starts moving again" approach that I've been taking thus far.  I'll revisit this post once I've done some more research and tweaking and let you know how your suggestions panned out.  Thanks again!

---

### Post by scbingham on 2013-07-19
Read this:

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

---

### Post by lukeiamyourfather on 2013-07-19
> **scbingham said:**
> Read this:

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

That's very nice! I haven't seen that one yet. Thanks for posting the link.

---

