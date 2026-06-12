---
title: "minimalbuntu?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by hammad1337 on 2008-07-12
can any one give me link to a minimal version of ubuntu, which has only CLI (no gui). and only basic, important packages, like sudo, apt, etc installed... i need it for a server in a virtual machine.
also, please tell me a the packages i would need to install on in to enjoy listening to mp3 music in command line.
thanks. :)

---

### Post by hyper_ch on 2008-07-12
download the server cd.

---

### Post by boblemur on 2008-07-12
i installed this yesterday, i got one download error... but it installed fine without it anyways :)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

i really like it...

---

### Post by Xerp on 2008-07-12
Jailtime has some good images:

[http://jailtime.org/](http://jailtime.org/)

If you don't use Xen, then there are some VMWare image here:

[http://isv-image.ubuntu.com/vmware/](http://isv-image.ubuntu.com/vmware/)

If you use Virtual Box, then take a pop over here:

[http://virtualbox.wordpress.com/](http://virtualbox.wordpress.com/)

---

### Post by VitaLiNux on 2008-07-12
You can try an Alternate install. You can install an Ubuntu CLI with little memory. Follow this link: 
[http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/gutsy/](http://ubuntu.cs.wisc.edu/pub/mirrors/linux/ubuntu/releases/gutsy/)

As a side note, any Alternate image will allow you to install the same Ubuntu CLI. You can download any of the *buntu alternate CDs!

---

### Post by walkerk on 2008-07-12
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


I used this for a minimal install. I installed xorg, openbox, etc on top of it...

---

### Post by VitaLiNux on 2008-07-12
Also these links could be of good help for you:
[Music player Daemon]("http://www.musicpd.org/")
[Manipulate Audio Files Using CLI]("http://vivapinkfloyd.blogspot.com/2008/05/how-to-manipulate-audio-files-using-cli.html")
I hope you will find your answers here!

---

### Post by Hendrixski on 2008-07-12
> **hammad1337 said:**
> can any one give me link to a minimal version of ubuntu, which has only CLI (no gui). and only basic, important packages, like sudo, apt, etc installed... i need it for a server in a virtual machine.
also, please tell me a the packages i would need to install on in to enjoy listening to mp3 music in command line.
thanks. :)

Well, the server version doesn't come with a GUI... but it's got a ton of server stuff installed in it.

There's also a version of Ubuntu server used for virtual appliances which cuts out not only the GUI but also all of the drivers (because if you're running in a VM you don't need those).

I think there's also a way to install just a text-only system.  Not sure of the details on that, it's probably one of the options on the install disk.

---

### Post by Vivaldi Gloria on 2008-07-12
Different command line versions of ubuntu:

(1) The alternative desktop cd with the F4 option (install CLI system) 

(2) Minimal CD available from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

(3) Server CD

(4) Ubuntu Jeos available from [http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)


Comments:

As far as I can see (1) and (2) install exactly the same basic ubuntu CLI version. I really like this version. It has no server stuff. Useful as a base system for a custom system build. For example install openbox. Or just use it as is. Good for old boxes. I use one in an old computer to practice bash and listen to music using moc. The install of (2) takes longer than (1) because it downloads everyting from the net. So use (2) if you have a decent connection.

(3) contains server programs. Don't install this unless you are making a server. Having non-used server programs on a destop computer is bad on 3 accounts: a) Takes space b) Updates take more time & bandwidth c) security: no point in programs which listens to ports.

(4) This version is a very light version which has hardly any drivers on it. Do NOT install it in a computer because it won't recognize your hardware. This version is supposed to be run in a virtual sytem like vmware, virtualbox, etc. "This combination of reduced size and optimised performance ensures that Ubuntu JeOS Edition delivers a highly efficient use of server resources in large virtual deployments."

---

