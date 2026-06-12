---
title: "Howto: Install Flock (a web browser)"
date: 2006-03-11
forum: Outdated Tutorials &amp; Tips
---

### Post by danhm on 2006-03-11
I switched from Firefox to Flock a few days ago and I love it. It's based on Firefox's code, so all of the plugins (Flash, Java, etc) that work for Firefox also work in Flock, as do many of the extensions. If you have any questions about Flock, [its community](http://www.flock.com/community/) can probably answer any questions you have better than I can, so I suggest asking there first, though I am willing to take a stab at any questions you may have, so don't be scared to ask!


Now, here is the howto!

Step 1) Make sure libstdc++5 is installed -- it's the only dependency you need. Enter the following command in a console:
```
sudo apt-get install libstdc++5
```

Step 2) Download Flock from [http://www.flock.com/developer/linux.php](http://www.flock.com/developer/linux.php)

Step 3) Extract the tarball.
```
tar xzvf flock-0.5.12.gz #Note: You have to be in the directory you downloaded Flock in
```

Step 4) See if it works.
```
cd flock
./flock
```

Optional Step 5) Add it to your Gnome Panel.
Right-click the Panel --> Add to Panel
Select Custom Application Launcher.
Enter the following information:
```

Name: Flock
Generic Name: Web Browser
Comment: Browse the web
Command: Click "Browse..." and browse to the executeable you ran in Step 4. Mine is /home/dan/flock/flock
Type: Application
Icon: Click the icon and browse to the same spot you did for "Command". Enter the "icons" directory, and then select the one you'd like to use. 
```

Any questions? This is my first howto, so be nice! ;p

I'll make a debian package for Flock once I learn how to make them.

---

### Post by kyoushu on 2006-03-12
Thanks alot for that.  I too switched from Firefox to Flock and once I install Ubuntu on my laptop Ill be sure to refer to this when installing Flock.

---

### Post by mstlyevil on 2006-03-12
The link you provided kept giving me a Linux executable file not a tar file. I had to go to the main download page to get the tar file to install it. You might want to check on this. Otherwise the guide worked great.

---

### Post by danhm on 2006-03-12
[QUOTE=mstlyevil]The link you provided kept giving me a Linux executable file not a tar file. I had to go to the main download page to get the tar file to install it. You might want to check on this. Otherwise the guide worked great.[/QUOTE]

Fixed!

---

### Post by mstlyevil on 2006-03-12
You might want to add how to migrate your Firefox pluggins to Flock. I will go ahead and post it here and you can just add it to your original post.

 First rename your flock folder to just flock. Then assuming you are logged into your home directory migrate to your plugin folder by typing into the terminal.

```
cd flock/plugins
```

Then use this command to migrate all your Firefox pluggins.

```
sudo ln -s /usr/lib/mozilla-firefox/plugins/* . 
```

That should do it.

---

### Post by LoclynGrey on 2006-05-05
Thanks it, installed with no problems.
:)
Cheers

---

### Post by Lopsicle on 2006-05-08
I got up to stage 3 but wasnt sure how to get into the directory that flock was downloaded to? So I just double clicked it, then went to stage 4 but says its not there? Obviously Im doing something wrong...can someone help Please :)

---

### Post by Lopsicle on 2006-05-09
Dont worry about it. I wont ask again.

---

### Post by IgnacioMiller on 2007-04-20
I just verified, this also works with Feisty. Be sure to replace the file you are untarring with the version of Flock that you downloaded though.:)

---

### Post by JimS on 2007-05-06
...
I'm having trouble installing Flock.
I have downloaded flock-0.7.13.1.en-US.linux-i686.tar.gz to my desktop.
When I run in my Edgy box

-desktop:~$ tar xzvf flock-0.7.13.1.en-US.linux-i686.tar.gz
tar: flock-0.7.13.1.en-US.linux-i686.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Don't understand why it doesn't find the directory and file.

JimS
...

---

### Post by kaede on 2007-05-07
is there any deb file package for flock? :D

---

### Post by motang on 2007-05-13
Nice thanks for sharing the information.  It worked very well.

---

### Post by compiledkernel on 2007-05-14
> **kaede said:**
> is there any deb file package for flock? :D

[http://www.getdeb.net/app.php?name=Flock](http://www.getdeb.net/app.php?name=Flock)

Provided working Ubuntu Deb for Flock. 

Getdeb.net also provides a number of other deb alternatives to applications out there.

---

### Post by nebhead on 2007-05-15
Or you can just get it off getdeb.net  

[http://www.getdeb.net/category.php?id=7]("http://www.getdeb.net/category.php?id=7")

---

