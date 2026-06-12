---
title: "Where to find PPAs?"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by NA3OH on 2014-07-04
Pretty much the title. I hear about people adding repositories but I have no idea where exactly you get them? 

Let's use the example that prompted me to ask this question. I'm looking into how to automount several partitions upon booting, and a guide I'm reading says to get the program pysdm. It says to just run sudo apt-get install pysdm. When I run that in the terminal it says that it couldn't locate the package. In this case I'm assuming I need to add another repository? I know the command to install them, but how do I find them?

---

### Post by bapoumba on 2014-07-04
[http://ubuntuforums.org/showthread.php?t=2076532](http://ubuntuforums.org/showthread.php?t=2076532) :)

Not your question I know : 
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs)

---

### Post by slickymaster on 2014-07-04
See [http://packages.ubuntu.com/search?keywords=pysdm](http://packages.ubuntu.com/search?keywords=pysdm) and [https://launchpad.net/ubuntu/+source/pysdm](https://launchpad.net/ubuntu/+source/pysdm)

It seems that the package pysdm stopped being seeded in Precise.

---

### Post by deadflowr on 2014-07-04
That package is old and was removed from the repos after 12.04.(rightfully, I would say)
[http://askubuntu.com/questions/237066/where-is-the-pysdm-package](http://askubuntu.com/questions/237066/where-is-the-pysdm-package)

As for ppa's
Typically, you'll find them at launchpad.net
Do a search, with google or other search-engine for which ever package you'd like to try.
The ppa's home page like this one
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)
will give you the details of how to add it to your system.

---

### Post by NA3OH on 2014-07-04
> **deadflowr said:**
> That package is old and was removed from the repos after 12.04.(rightfully, I would say)
[http://askubuntu.com/questions/237066/where-is-the-pysdm-package](http://askubuntu.com/questions/237066/where-is-the-pysdm-package)

As for ppa's
Typically, you'll find them at launchpad.net
Do a search, with google or other search-engine for which ever package you'd like to try.
The ppa's home page like this one
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)
will give you the details of how to add it to your system.

Thanks, this was exactly the type of answer I was looking for

---

### Post by grumblebum2 on 2014-07-04
You may want to read this guide about PPAs.
[http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html](http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html)

and this one about [**_[COLOR="#B22222"]Y PPA MANAGER[/COLOR]_**]("http://www.webupd8.org/2011/09/y-ppa-manager-0081-released-with-ubuntu.html")
which among other things allows you to easily purge a PPA should upgraded packages from a PPA cause trouble.

---

