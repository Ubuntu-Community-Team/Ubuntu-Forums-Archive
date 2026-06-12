---
title: "Conventions for file placement"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-04
Hi,
What are the conventions for where to put different types of files on a Linus system? And how to access them?

For example I'm installing java and a bunch of utilities such as a hex editor and an IDE. 

Should there be separate user ids for these to keep them out of my personal userid space? 

Then to access these programs, I'll need to create links and place them in a global location such as one of the paths in the PATH environment variable.

Thanks,

Norm

---

### Post by glennric on 2008-05-04
First you should check to see if the programs are in the repositories.  If so install them from the repositories, and all that you are asking about will be taken care of for you.  If the java you are referring to is sun's java then install that from the repositories.  Check the repositories for the hex editor and IDE as well.

---

### Post by NormR2 on 2008-05-04
If the repositories requires being connected to the internet, then I have a problem as I'm not able to connect. My winmodem is not found by the PPP GNOME program. So I'm doing everything manually via a MS Windows machine.

If the programs are not in the repositories, where should they go?


Norm

---

### Post by Grishka on 2008-05-04
> **NormR2 said:**
> If the repositories requires being connected to the internet, then I have a problem as I'm not able to connect. My winmodem is not found by the PPP GNOME program. So I'm doing everything manually via a MS Windows machine.

If the programs are not in the repositories, where should they go?


Norm

they can go wherever you want them to. if you prefer simple solutions, however, first look for the packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by NormR2 on 2008-05-05
Thanks for the link - looks like a good site.

Instead of 'reinventing the wheel', I'd think that Linux users would have agreed on conventions on where to store programs and utilities and how to connect to them. 
It would save me a lot of trial and error to use an existing system instead of trying to figure it out myself. Although that's how you learn a new system.

Norm

---

### Post by hyper_ch on 2008-05-05
there is a convention:  [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by NormR2 on 2008-05-05
That site seems to define where Linux puts its stuff.
Where do I put things that aren't a part of Linux?
For example a Hex Editor or a SlideShow program. Do I create a new userid to hold general usage programs?

And how do I access them? Create a Launcher on a Desktop or
create a link and put it in some folder that is on the PATH or
do I create a new folder for my stuff and add it to the PATH? Or?

---

### Post by hyper_ch on 2008-05-05
if you install it it is part of linux :) and then it belongs to the according dirs.

---

### Post by Monicker on 2008-05-05
> **NormR2 said:**
> That site seems to define where Linux puts its stuff.
Where do I put things that aren't a part of Linux?
For example a Hex Editor or a SlideShow program. Do I create a new userid to hold general usage programs?

And how do I access them? Create a Launcher on a Desktop or
create a link and put it in some folder that is on the PATH or
do I create a new folder for my stuff and add it to the PATH? Or?

The heirarchy mentions files which are not a part of the installed OS.

/usr/local or /opt

---

### Post by graben3 on 2008-05-05
I think usually only services and server programs as apache, mysql & php will run with a different user Id, but for a photo gallery software, there is no need to run it with it's own user ID 

I just don't see the point in doing this.

Usually, having a different user ID to run a program is usefull if this program is exposed to the internet so if someone manage to hack this program somehow, he don't get far after because he just got control over 1 userID and he will need to hack another to gain more control after that.

---

