---
title: "Help with Maple 11"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-05-18
Hey guys, I was wondering if I could get some help with maple 11 in Linux.  I've looked at other threads and non of them are of any help.

First and perhaps most important, typing "maple" or "xmaple" into the terminal does nothing - which doesn't surprise me at all because I have no idea how to set it up to do that.

Secondly, I am getting the blank screen problem like some others have had.  The methods on the other thread haven't worked, but that's mainly because of my first problem.

Thirdly, suppose I want to uninstall it and reinstall it in a new directory, how would I go about doing that as it does not appear in the "add/remove..." lists.  My main problem is that the maple 11 folder in in my home directory, which was put their by accident.  So, if I reinstall it, where should it go.  Or can I just cut and paste the folder into a new location?

---

### Post by urgnom on 2008-05-18
To start using maple or xmaple commands, you need to have the executables in your path. Make symbolic links to the maple executables in your /usr/local/bin directory. This should be stated in the Maple documentation too.

Maple is using a java-based GUI. That doesn't work too well with Compiz. Either turn off desktop effects, or change the Java version in Maple to use Java-6 instead of the version that comes with Maple 11, whatever that is. 

Where the folder containing your Maple files is located is not really important. You would like to put it under /usr/local if you want to let other users of the computer use Maple too. Enjoy.

---

### Post by shifty_powers on 2008-05-18
[https://help.ubuntu.com/community/Maple](https://help.ubuntu.com/community/Maple)

;)

---

### Post by roe_polak on 2008-05-18
Edit the /PATH/TO/maple11/bin/xmaple file by adding this line at the top of the file:

```

export AWT_TOOLKIT=MToolkit
```

You can run maple with this file with

```
./PATH/TO/maple11/bin/xmaple
```

---

### Post by SalsaShark on 2008-05-18
> **urgnom said:**
> Maple is using a java-based GUI. That doesn't work too well with Compiz. Either turn off desktop effects, or change the Java version in Maple to use Java-6 instead of the version that comes with Maple 11, whatever that is. 

Alright, I'm going to try changing the Java version that maple is using.  How do I do that?

---

### Post by SalsaShark on 2008-05-18
> **roe_polak said:**
> Edit the /PATH/TO/maple11/bin/xmaple file by adding this line at the top of the file:

```

export AWT_TOOLKIT=MToolkit
```

You can run maple with this file with

```
./PATH/TO/maple11/bin/xmaple
```


I tried this but it won't let me save the file.

---

### Post by SalsaShark on 2008-05-18
Actually, I've been fiddling around and I've gotten to the point where I can run maple from the terminal by typing "xmaple", but I can't get the launcher on my desktop to run maple.  The same problem that the guy in another thread had that went unresolved.

---

### Post by roe_polak on 2008-05-18
> **SalsaShark said:**
> I tried this but it won't let me save the file.

If the path to maple11 is not in your home directory (or simply not owned by you) will need to have root privileges. Use
```
sudo nano /PATH/TO/maple11/bin/xmaple
```
or whatever editor you might prefer. This should solve the problem.

---

