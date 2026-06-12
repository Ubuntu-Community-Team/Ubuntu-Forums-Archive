---
title: "You may find this hard to believe"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2008-05-08
I have been using Ubuntu for several years, several versions, several different distros, and I have still not figured out what to do with tarballs.
Example:
I downloaded a linux game. It sits on my desktop as a package labled 20080330.tar.bz2
I have Archive Manager installed, I employ it and end up with a folder containing the various files that make up the program. I have experimented with opening or extraction the various files and still can not come up with the game. I have searched and found tons of suggestions and info but none of it make any sense  to me. In all these years I have been unable to do anything with tar files. I find that unbelievable. Will someone please help me end this aspect of my ignorance?

---

### Post by spiderbatdad on 2008-05-08
Usually, there is a 'read me' and 'install' file containing instructions, as packages can be run or installed in different ways. As you noted the 'tar' is just an archive.

---

### Post by kindafunnylookin on 2008-05-08
I'll give it a shot. Thanks

---

### Post by ericartman on 2008-05-08
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

 I refer to this a lot hope it helps

---

### Post by kindafunnylookin on 2008-05-08
No luck there, I open it with Archive Manager and get this folder but no _read or instruction files_

---

### Post by kindafunnylookin on 2008-05-08
> **ericartman said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

 I refer to this a lot hope it helps

Thanks. I have not come across this before, it will keep me busy for a while.

---

### Post by wdaniels on 2008-05-08
If it's a tarball containing source code, the most typical process is to run the following commands:

```
./configure
make
sudo make install
```

...but of course not everything is the same, and the INSTALL/README files already mentioned are your best bet.

You have to run these commands from the terminal, in the extracted folder.  I find the easiest way to do this is install the nautilus-open-terminal package:

```
sudo apt-get install nautilus-open-terminal
```

You can then right-click the folder (I seem to remember Gnome/nautilus will need a restart first) and select "Open in Terminal" to get a terminal with the path set to the right place.  (Not essential to do that of course, but if you're not too comfortable with the terminal it saves you trying to remember those long folder names.)

---

### Post by spiderbatdad on 2008-05-08
sometimes the instructions are in a DOC folder.

If there is an binary program (big blue diamond) you can usually run that with a ./program_name (like ./installer for example) command, but often the program has to be made executable first with the command sudo chmod a+x program_name, sudo chmod a+x installer (for the above example.)

You need to be in the folder to work with it. So first cd into the folder. If it is on your desktop, ```
cd Desktop/foldername
```

If there is no binary program, look for file like configure...make etc.
This package is installable in the following way.```
./configure
make
sudo make install
```

You will need a compiler already installed. So the first thing to do is make sure you have build-essential.```
sudo apt-get install build-essential
```

---

### Post by bodhi.zazen on 2008-05-08
[http://ubuntuforums.org/showpost.php?p=4473168&postcount=5](http://ubuntuforums.org/showpost.php?p=4473168&postcount=5)

---

### Post by kindafunnylookin on 2008-05-09
OK. Thank you all. You have given me enough information to study an open another whole phase of my Ubuntu abilities. It will take me a while to beat through all of this, but I will. And for now I will use the Linux games available on the repos.

---

### Post by girishv on 2008-05-09
Hi,

if you do not have problem, can you please post the contents of the directory created by un-tarring the archive. That will surely help us to figure out what to do ...

Girish

---

### Post by forumache on 2008-05-09
As girishv said, it would be interesting to see the content of the directory. As I don't expect anyone to copy the content of Archive Manager windows by hand, please run the following command in a terminal:

tar tvfj 20080330.tar.bz2

You *must* be in the directory where the file you downloaded is.

Also, there must be some instructions on the website from where you downloaded the tar file. Usually the developers put some information regarding how to install

Good luck,
Dan

---

