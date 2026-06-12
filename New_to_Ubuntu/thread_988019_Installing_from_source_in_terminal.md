---
title: "Installing from source in terminal"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-11-20
I downloaded a package called "asfbin command line version 1.7.1" from their website [http://www.radioactivepages.com/index.php?section=software&docid=asfbin](http://www.radioactivepages.com/index.php?section=software&docid=asfbin) since I did not find it in synaptic package manager.

I extracted the package to my home folder and attempted to install the program in terminal unsuccessfully getting the reply "file or directory not found."

I used the cd ~ to navigate to my home directory where it's located.

Then I typed the ./configure command and before I could type make and sudo make install I received the above "file or directory not found error." 

Do I need to type the asfbin-bin" file name after all these commands? Example: ./configure asfbin-bin, make asfbin-bin and sudo make install asfbin-bin?

Is there a good tutorial site on installing packages in this fashion?

Thanks

---

### Post by nothingspecial on 2008-11-20
You need to cd into the actual file. Not just the directory it is located in.

---

### Post by lakersforce on 2008-11-20
A little more descriptive description of your problem would help. Try and post the output of the command...

---

### Post by Brian_Newbie on 2008-11-20
When I attempt to install the package asfbin-bin in terminal that is already unzipped and in my home folder, I get the following text: 


brian@brian-laptop:~$ cd ~ asfbin-bin
brian@brian-laptop:~$ ./configure
bash: ./configure: No such file or directory
brian@brian-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by nothingspecial on 2008-11-20
> **Brian_Newbie said:**
> When I attempt to install the package asfbin-bin in terminal that is already unzipped and in my home folder, I get the following text: 


brian@brian-laptop:~$ cd ~ asfbin-bin
brian@brian-laptop:~$ ./configure
bash: ./configure: No such file or directory
brian@brian-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.

You`ve not cd`d into it, thats why your prompt still says brian@brian-laptop:~

```
cd asfbin-bin
```

---

### Post by Billybob97060 on 2008-11-20
you've got to actually be in the folder itself, not just its directory or it will not find it because it only looks in that one place

UPDATE: you got there just before me :)

---

### Post by Brian_Newbie on 2008-11-20
UGH! When I typed: 

brian@brian-laptop:~$ cd asfbin-bin  ( I received...)
bash: cd: asfbin-bin: Not a directory

I can't seem to get past step one.

---

### Post by hyper_ch on 2008-11-20
where is that folder?

---

### Post by Brian_Newbie on 2008-11-20
The folder is in /home/brian/ the same place as when I use the GUI and go to "places" then click on the first folder in the list "home Folder"

---

### Post by hyper_ch on 2008-11-20
I don't use gnome so I have no clue where "Places" goes and that list is....

try:

```

cd ~/asfbin

```

if that does not work, post the output of:

```

ls ~/

```

---

### Post by Brian_Newbie on 2008-11-20
It did not work. Output of both commands: 

brian@brian-laptop:~$ cd ~/asfbin-bin
bash: cd: /home/brian/asfbin-bin: Not a directory

brian@brian-laptop:~$ ls ~/
asfbin-bin
Copyright American election campaign 
Desktop
Documents
email on linux laptop
YouTube_-_April_Verch_dances_up_a_storm.flv
brian@brian-laptop:~$

---

### Post by nothingspecial on 2008-11-20
What is it you are trying to install and where did you get it?

---

### Post by shifty_powers on 2008-11-20
go into nautilus, rename the bloody folder and then rerun the command :D

eg rneame it temp and go

```
cd ~/temp
```

---

### Post by Brian_Newbie on 2008-11-20
I'm trying to install a package which joins asf and wmv files without any loss of resolution. The package is called asfbin version 1.7.1 which I downloaded from this website:

[http://www.radioactivepages.com/index.php?section=software&docid=asfbin](http://www.radioactivepages.com/index.php?section=software&docid=asfbin)

I clicked on the linux asfbin command line version on that site. It downloaded initially to my desktop. I dragged it into my home folder by opening the folder from the GUI and dragging it off of my desktop.

The asfbin-bin definitely shows up in my home folder.

---

### Post by Brian_Newbie on 2008-11-20
I rename it temp and got the following output:

brian@brian-laptop:~$ cd ~/temp
bash: cd: /home/brian/temp: Not a directory

---

### Post by nothingspecial on 2008-11-20
That`s because it`s not a directory. It is code.
I don`t know what it is and suggest you don`t use it and look for an alternative.

If you must use it you probably need to make it executable.
```

chmod a+x asfbin
```

or if it`s still called temp ```
chmod a+x temp
```

Then ```
./temp
``` or```
./asfbin
```

I repeat, I wouldn`t do it.

---

### Post by Brian_Newbie on 2008-11-20
You're right. This package does need to be made executable. Do I type the chmod a+x temp first, then go through the installation steps second?

---

### Post by lakersforce on 2008-11-20
> **Brian_Newbie said:**
> You're right. This package does need to be made executable. Do I type the chmod a+x temp first, then go through the installation steps second?

yes

---

### Post by Brian_Newbie on 2008-11-20
I found the post where I came upon this program asfbin. It's located here:

[http://ubuntuforums.org/showthread.php?t=804557&highlight=joining+wmv+files&page=2](http://ubuntuforums.org/showthread.php?t=804557&highlight=joining+wmv+files&page=2) (and it's the 13th post in that thread). 

It looked like a good program to try out vs avidemux which I use often. However I found that converting vids to avi from wmv's then joining them with avidemux made the clarity of the movie worse (in most cases but not all). 

I'll play around some more with making asfbin executable. If it doesn't work, no harm done.

Thanks to everyone for all your help.

---

