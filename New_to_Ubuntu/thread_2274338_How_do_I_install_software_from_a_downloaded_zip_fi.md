---
title: "How do I install software from a downloaded zip file?"
date: 2015-04-19
forum: New to Ubuntu
---

### Post by Tom_Carr on 2015-04-19
I usually install from the software center.  If something in not in the software center and I download it from a web site, how do I install it.  I did a google and all the instructions I saw seemed very complex.  I know I did this years ago and it was not that complicated but now I can't remember what I did or find simple instructions.

---

### Post by roger_1960 on 2015-04-19
Hi

Normally if you download a package for ubuntu it is a .deb file.  Open it with gdebi package installer. (If you dont have that, install gdebi with synaptic or from the ubuntu software centre)

Roger

---

### Post by Impavidus on 2015-04-19
A .deb file can also be installed from command line using dpkg.

If the software comes in some kind of archive format, there are no standard instructions. Unpack the archive and look for a README or INSTALL file and read that. Then, use all the Linux knowledge you have and install it.

---

### Post by Holger_Gehrke on 2015-04-19
A zip file is just about the worst container for a Linux program possible because zip can't store the attributes of a Linux file (and that includes the bit to mark a program as executable). If somebody uses that, he should have included some documentation. Without knowing what program you're trying to install it's hard to give you any help. It might be some binary that just needs it's attributes set or there might be a script in there you can execute to get the rest of the program set up or it might be source code that needs building and installing; I can't be more precise without more information.

---

### Post by cariboo on 2015-04-19
It would probably help if you let use know what the name of the file is.

---

### Post by monkeybrain20122 on 2015-04-20
Depends on what is inside the .zip file, can be source codes, an install script or a binary. What is it?

---

### Post by conner_bradley on 2015-04-20
If it is a zip file, you would first want to navigate to the folder where it got placed using cd


>  cd ~/Downloads 

This navigates to the download folder of the current user;

Then extract the file using unzip, if needed install unzip using

>  sudo apt-get install unzip
>  sudo unzip file 

then in order to install the file, say its called installer.deb

>  sudo dpkg -i installer

---

### Post by HermanAB on 2015-04-20
In general, you unzip or untar it, then you read the INSTALL file and the README file and then you cross your fingers and do what they say...

---

### Post by Misterio7 on 2015-04-20
Mostly, software included in zips contain a readme file somewhere (Or in the site you downloaded them). If it's a deb file you can just open it up using sofware center.

**~[COLOR=#4b0082]Misterio[/COLOR]**[COLOR=#4b0082][/COLOR]

---

### Post by newb85 on 2015-04-20
The replies so far have been right on the money.  Keep in mind, the more you deviate from software in the repos (adding PPAs or especially installing from .zips or tarballs), the more likely you are to bork your system.

Packages installed without using apt (either through the command line or SC or Synaptic) will not have their dependencies automatically handled.  Just because things work fine today doesn't mean they will in the future.  

There aren't viruses for Linux in the wild, but that doesn't mean there aren't malicious scripts you could download and execute thinking they were something else.  Consider the source and why you trust them.

---

### Post by oldos2er on 2015-04-20
> ```
sudo unzip file
```

No need for "sudo" when one's working in one's own home folder.

---

### Post by monkeybrain20122 on 2015-04-21
To open the zip file just right click it and choose extract here. Not sure why everyone goes on command line. This is the "New to Ubuntu" section.

---

### Post by newb85 on 2015-04-21
Yes, there's no need to overcomplicate the process.  And unzip should be installed by default, assuming this is Ubuntu.

---

