---
title: "No idea how to to install a tar.gz package"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by Marcus Zion on 2012-05-21
I'm rather fed up with Libre Office and I wanted my old OpenOffice program back so I downloaded the newest version which is 3.4.0 in a tar.gz. Problem is I've no idea how to install it.

---

### Post by Lynceus on 2012-05-21
maybe just a right click on the file, permissions, execute and then allow executing file as program
Just a thought

---

### Post by Frogs Hair on 2012-05-21
If you downloaded from the link and you right click and extract the package the .deb packages that can be installed with software center are inside folder. Check the read me files in the folder before proceeding. 

[http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html)

---

### Post by agillator on 2012-05-21
A '.tar.gz' file is simply an archived group of files (files all put in one file) and then compressed. You uncompress and unarchive the files. What happens then depends upon what the files really are. So, the first step is to get to the actual files. You do that with the tar program. Open a terminal and go to the directory where you wish the files to be. Most of the time that is going to be the directory where the tarred file is, but not always.  Then, 'tar zxvf <path of the tarred file>. Of course if you are in the same directory as the tarred file all you need is the file name. Most of the time a new subdirectory will be created which will contain the original files; depends on how they were archived (i.e. tarred) in the first place. What you do then depends on what you have. In the case of OpenOffice I THINK you will have an installation file. I can't remember for sure. If you do (probably a bin or an sh file) you may have to adjust the permissions so it is executable (sudo chmod +x <filename>) and then run the file, most likely with sudo. There will probably be a README or INSTALL file which will tell you what you need to do.

Now with all that said, is there a reason you are installing that way? Why not just 'sudo apt-get install openoffice'?

---

### Post by critin on 2012-05-21
If you downloaded the deb file from the main site, extract it (it will choose default folder/path-let it) then open and find the DEBS icon. open that and click on "desktop-integration".
There will be choices of how to install when you right click for menu -- allow it to be installed by software center.

---

### Post by Frogs Hair on 2012-05-22
The . debs for OO are inside the tar.gz. as stated in my first post.

---

