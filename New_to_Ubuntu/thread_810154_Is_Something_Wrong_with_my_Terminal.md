---
title: "Is Something Wrong with my Terminal?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Andavane on 2008-05-28
I am still struggling with the terminal.
I am following the steps in
[http://linuxcommand.org/lts0020.php#cd]("http://linuxcommand.org/lts0020.php#cd")
In my

/home/andavane

directory, I have made a folder called "Downloads" and put Hardy Heron 8.04 there.
The problem is I seem unable to use "cd" to change the directory to there to perform the md5sum. I get "no such file or directory" As in here:

[http://ubuntuforums.org/album.php?albumid=201&pictureid=607]("http://ubuntuforums.org/album.php?albumid=201&pictureid=607")

What am I doing wrong? Is the terminal working OK?

Am I committing a cardinal blunder in my terminal excercises? Is it possible there is something wrong with my installation?

Regards

John

---

### Post by drkameleon on 2008-05-28
If you type "ls" in your home folder (terminal), does "Downloads" come up? To enter your "Downloads" folder you just have to type

cd Downloads (not cd /Downloads ---> this looks for a directory in your /home folder, not /home/andavane...;))

---

### Post by spiderbatdad on 2008-05-28
The problem appears to be that your pwd (present working directory) in that screenshot is Desktop. From Desktop, there is no path to Downloads. try typing cd by itself, to get you back to home. Then cd Downloads
Remember that filenames and directories are case sensitive, as well

Or from Desktop you can give the full path...cd /home/adavane/Downloads/what_ever_folder

EDIT: I see now you are not pwd Desktop...however the path to downloads needs your user name

---

### Post by 3rdalbum on 2008-05-28
/home contains all the home directories on your computer, so basically you are one folder *above* where you want to be.

If you just type *cd *with nothing afterwards, it goes straight to your user's home directory. From there, *cd Downloads* will work.

---

### Post by lisati on 2008-05-28
> **Andavane said:**
> I am still struggling with the terminal.
I am following the steps in
[http://linuxcommand.org/lts0020.php#cd]("http://linuxcommand.org/lts0020.php#cd")
In my

/home/andavane

directory, I have made a folder called "Downloads" and put Hardy Heron 8.04 there.
The problem is I seem unable to use "cd" to change the directory to there to perform the md5sum. I get "no such file or directory" As in here:

[http://ubuntuforums.org/album.php?albumid=201&pictureid=607]("http://ubuntuforums.org/album.php?albumid=201&pictureid=607")

What am I doing wrong? Is the terminal working OK?

Am I committing a cardinal blunder in my terminal excercises? Is it possible there is something wrong with my installation?

Regards

John

Possibility: Linux recognizes a difference between "Downloads" and "downloads" - make sure you use the same one on the "cd" as you did on the mkdir

cheers!

---

### Post by Andavane on 2008-05-28
> **drkameleon said:**
> If you type "ls" in your home folder (terminal), does "Downloads" come up? To enter your "Downloads" folder you just have to type

cd Downloads (not cd /Downloads ---> this looks for a directory in your /home folder, not /home/andavane...;))
and to spiderbatdad as well.

Yes, when I type ls in home file, Downloads is listed, and when I type "cd Downloads" it does indeed change to that directory. Thanks very much!

I may be getting there slowly. It means that if you are changing the directory to a folder which exists already in your working folder, no forward slash is necessary. Yes?
I don't remember reading it like that in the guides. I must check again.
;)
------
> **spiderbatdad said:**
> The problem appears to be that your pwd (present working directory) in that screenshot is Desktop. From Desktop, there is no path to Downloads. try typing cd by itself, to get you back to home. Then cd Downloads
Remember that filenames and directories are case sensitive, as well

Or from Desktop you can give the full path...cd /home/adavane/Downloads/what_ever_folder

EDIT: I see now you are not pwd Desktop...however the path to downloads needs your user name
Thank you. The point about being case sensitive is understood. I will need to sit down with the other bit, and work through the guides again.

My objective here is to perform the checksum thing on the iso file I download for Hardy, before burning it to a CD.

Hope it goes OK. As I said, my main computer work is letters and articles, not computer software things. But I must admit it is interesting. I'd like to be a bit better at it.

Kind regards

John

PS: When I type what you say (cd../home/adavane/Downloads)
I get:
"No such file or directory"
I always end up getting confused by the terminal....:confused:

---

