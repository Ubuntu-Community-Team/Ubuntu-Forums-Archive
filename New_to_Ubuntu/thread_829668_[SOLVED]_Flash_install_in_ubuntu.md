---
title: "[SOLVED] Flash install in ubuntu"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-15
now i am trying to install flash player for my firefox.
I am getting this error.
can any one guide me

```

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 
```

---

### Post by Franc88 on 2008-06-15
> **rraj.be said:**
> now i am trying to install flash player for my firefox.
I am getting this error.
can any one guide me

```

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 
```

Hi, I'm new to linux and I just installed flash too for firefox today. Here is what I did:

1.  D/l the tar.gz file to a folder
2.  Extract the file to the same folder
3.  From gnome, I opened the directory then the folder containing the flash file.
4.  I double clicked the flashplayer-installer file, and clicked on the option to run in terminal.
5.  I had to close firefox to continue installation.
6.  I pressed ENTER to continue installation.
7.  I pressed "Y" for continue installation.
8.  After it was done, it gave a message and closed the terminal.
9.  Restart firefox and flash worked.


Hope this helps.

---

### Post by wormser on 2008-06-15
Or

```
sudo apt-get install flashplugin-nonfree
```

Done.

---

### Post by Franc88 on 2008-06-15
> **wormser said:**
> Or

```
sudo apt-get install flashplugin-nonfree
```

Done.

just curious, can you type this command in any directory or do you have to be in the directory where the file is at?

---

### Post by wormser on 2008-06-15
It does not matter which directory you are in.  The command apt-get knows where to install the program.  It downloads the program from the repository then installs it.  You should read [_How to Install Anything in Ubuntu_]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Fingel on 2008-06-15
that command runs a program that will download and automaticaly install the flash plugin. Simple as that. The days of hunting the web for programs to install is over with ubuntu.

---

### Post by cheesypoof on 2008-06-15
You can type that command anywhere, because it gets the package from synaptic.

---

### Post by aysiu on 2008-06-15
> **Franc88 said:**
> just curious, can you type this command in any directory or do you have to be in the directory where the file is at?
Anywhere, since it uses the software repositories instead of the .tar.gz you manually downloaded.

But...

You don't need to type the command. You can copy and paste it into the terminal.

And...

You don't need the terminal at all. Just visit a Flash site and click on *Install Missing Plugins*. More details [here](http://www.psychocats.net/ubuntu/flash)

---

### Post by niket on 2008-08-14
> **Franc88 said:**
> Hi, I'm new to linux and I just installed flash too for firefox today. Here is what I did:

1.  D/l the tar.gz file to a folder
2.  Extract the file to the same folder
3.  From gnome, I opened the directory then the folder containing the flash file.
4.  I double clicked the flashplayer-installer file, and clicked on the option to run in terminal.
5.  I had to close firefox to continue installation.
6.  I pressed ENTER to continue installation.
7.  I pressed "Y" for continue installation.
8.  After it was done, it gave a message and closed the terminal.
9.  Restart firefox and flash worked.


Hope this helps.

:):)Thanks so much. It worked to me too!!!:):):
niket

---

