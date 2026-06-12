---
title: "Packaging commercial software"
date: 2015-09-08
forum: Packaging and Compiling Programs
---

### Post by marstrehlow on 2015-09-08
Hi all,

I wrote a little game in OpenGL which I very much like to publish and sell on the Ubuntu Software Center. In general I know what there is to do... but I believe I have small thinking problem.

So basically I created a .deb package by working through some pages of documentation. It'll create a package that resolves the dependencies, and installs the game along with its resources into the /opt directory, as it is instructed for packaging software for Ubuntu. I submitted that package and was told that it wasn't a source package.

And this is where I'm stuck. Eventually I learned that a source package effectively contains the source code so it can be compiled for other platforms. I need help creating said source package.

Is there something I'm missing? Do commercial packages have to have the source code? Or is there a trick to creating such packages pretending to be a source package? Is there a guide that describes how to create these packages?

I'd be very grateful for any help or comment, pointing me in the right direction.


Cheers guys!
Marcus

---

### Post by brian-mccumber on 2015-09-08
Have you checked out the [Ubuntu SDK]("https://developer.ubuntu.com/en/start/")? I just installed it last night but I haven't had the time to mess with it yet other than opening an example project and getting it to run but it does look like it has all the necessary tools to make this task alot easier and it will allow a Dev to target mobile devices too. I also found this link to an article about packaging new software for distribution.

[http://packaging.ubuntu.com/html/packaging-new-software.html](http://packaging.ubuntu.com/html/packaging-new-software.html)

---

### Post by flaymond on 2015-09-10
[QUOTE=brian-mccumber]Have you checked out the [Ubuntu SDK]("https://developer.ubuntu.com/en/start/")? I just installed it last night but I haven't had the time to mess with it yet other than opening an example project and getting it to run but it does look like it has all the necessary tools to make this task alot easier and it will allow a Dev to target mobile devices too. I also found this link to an article about packaging new software for distribution.
[/QUOTE]

I don't think Ubuntu SDK currently support one click .deb packaging right now. Anyway, it's good if you dealing with Qt application development.

---

### Post by brian-mccumber on 2015-09-12
I found this link after a bit of searching maybe this will help you. 

[https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf](https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf)

---

