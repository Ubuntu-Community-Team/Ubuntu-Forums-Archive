---
title: "command line"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by harrydee on 2008-06-14
I'm having trouble,'again', in trying to add new items to the system using the terminal.If I download a programme to the desktop and then enter ' sudo apt-get install [?] desktop', I get the response "couldn't find package". I also find that the terminal doesn't accept my password, although it is the only one I use and is accepted elsewhere on the distro.
This happens with all programmes such as google earth, enlightenment etc.

Any comments would be appreciated.

---

### Post by kalesh7 on 2008-06-14
I suppose you are downloading .deb packages, if it is in repository you wouldn't need to download to desktop but just use

sudo apt-get install package_name

so it probably is not in the repository, use this command 

sudo dpkg -i filename.deb

I am not sure about the password, (maybe you have somehow restricted yourself from doing root operations?)

---

### Post by the_doc on 2008-06-14
> **harrydee said:**
> sudo apt-get install [?] desktop', I get the response "couldn't find package".

This command is trying to install a package called desktop.  Using synaptic via the gui is a lot easier.  You can even install .deb packages by right clicking on them and choosing the first option.

If you want to do it via the terminal then the above post is the way to go.

---

### Post by ibuclaw on 2008-06-14
Yes, the command
```
sudo dpkg -i *.deb
```
would be the one that you are looking for.

"**apt-get**" searches the Ubuntu Repositories, as defined in the sources file. Whereas "**dpkg**" searches the current directory you are working in.

Also, double-clicking the .deb file on your desktop should open up the app "**gDebi**", a GUI frontend for dpkg.

Regards
Iain

---

### Post by cariboo on 2008-06-14
Another way to install .deb's, if you have them on your desktop is just to double click on it and gebi will pop up and you can install it from there.

As a matter of fact if firefox knows what kind of file it is it will ask you what you want to do with it.

Jim

---

