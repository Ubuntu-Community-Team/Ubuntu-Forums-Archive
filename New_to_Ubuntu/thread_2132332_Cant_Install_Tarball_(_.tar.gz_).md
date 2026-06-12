---
title: "Cant Install Tarball ( .tar.gz )"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by Ashfaqur Rahman on 2013-04-04
Hello!
I am new to ubuntu.
I have installed ubuntu just today.
I am trying to install a tar.gz file for my wireless flash modem.
First I Extract that PCL_BGTLK.tar.gz with archive manager into Desktop.
It contains install.sh, Teletalk_3G.tar.gz and zr .

Now I Open Terminal and open extracted PCL_BGTLK.
After that I give ./configure command but it says " Bash: ./configure: No Such file or directory ".

Now what can i do to install that program?

---

### Post by slickymaster on 2013-04-04
Hi, welcome to the forum.

Now that you already extracted into a folder, all you have to do is:
```
cd /path/to/folder
./configure
make
sudo make install
```

---

### Post by schragge on 2013-04-04
As the archive contains *install.sh*, try it:
```
./install.sh
```

---

### Post by Ashfaqur Rahman on 2013-04-04
I Have Tried With ./install.sh code but now its saying
"...............start install............
****check for root - failed
****please retry as root user.
press any key to exit......."

I am giving u link to download that file.
If you can please download it and check.If you can install let me how to.

[http://www.mediafire.com/download.php?gc31l292g776e61](http://www.mediafire.com/download.php?gc31l292g776e61)

---

### Post by Impavidus on 2013-04-04
In that case use```
sudo ./install
```
It will prompt you for your password. When typing it no characters will show up in the terminal, but the password will be accepted. Just hit enter when you're done.

But I understand you're trying to install a driver for something. I presume it didn't show up under additional hardware? (It's OK, this may happen. Just checking.)

---

### Post by Ashfaqur Rahman on 2013-04-04
Yahooo!!
Problem Solved!!

This ```
sudo ./install.sh
``` code worked!

But Before That I Have To Install about 10 Debian Pakages!! ](*,)

Thanks. =D>

---

### Post by Hasan221 on 2013-04-22
which debian pakage you install and how??????:confused::confused::confused::confused::confused::confused::confused:

---

### Post by albaniaguard on 2014-04-01
i have the same problem,what i nead to do ?

---

### Post by slickymaster on 2014-04-01
> **albaniaguard said:**
> i have the same problem,what i nead to do ?

I would advise you to start a new thread on your issue in particular, providing some more details on what is specifically your problem.

---

### Post by albaniaguard on 2014-04-01
i try to install PCL_EMALB.tar.gz  i do extraxt in desktop and i try to install with terminal the install.sh but i take a eror
  ..................start install.................*** Check for root - failed
*** Please retry as root user.
press any key to exit.... 
what i can do ?

---

### Post by albaniaguard on 2014-04-01
[COLOR=#000000]i try to install PCL_EMALB.tar.gz i do extraxt in desktop and i try to install with terminal the install.sh but i take a eror[/COLOR]
[COLOR=#000000]..................start install.................*** Check for root - failed[/COLOR]
[COLOR=#000000]*** Please retry as root user.[/COLOR]
[COLOR=#000000]press any key to exit.... [/COLOR]
[COLOR=#000000]what i can do ?[/COLOR]

---

### Post by Impavidus on 2014-04-01
As this is exactly the same error as in post #4, it may be a good idea to try the solution mentioned in post #5.

Edit: Oops, didn't see you already started another thread.

---

### Post by coffeecat on 2014-04-01
Thread closed.

---

