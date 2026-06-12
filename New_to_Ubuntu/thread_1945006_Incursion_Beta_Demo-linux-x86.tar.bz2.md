---
title: "Incursion Beta Demo-linux-x86.tar.bz2"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2012-03-22
I downloaded a file which is a Demo for a new game being release later in the year.

The file is > Incursion Beta Demo-linux-x86.tar.bz2  but now what do i do ?

If i double click it opens in Archive Manager, then that folder just opens to other folders and files ?
I have never tried to do anything like this in the time i have been using Ubuntu.....
Can anyone advise me how i install & run this please [-o<

---

### Post by EzioAuditore on 2012-03-22
there most probably will be a 'read me' or 'install' file containing the instructions on how to install it.

---

### Post by MadMonkey1966 on 2012-03-22
Thanks for the reply :)

There is only one README file, which is a HTML one, and when that opens it only contains the rules of the game.

also contained in the folder with the README file, are 4 other folders (common, game, lib & renpt) a few .png images , a python script & shell script :-k

---

### Post by flurospar on 2012-03-22
Is there any file called "configure"?

Read the readme files, read up online (or contact the dev) for the dependencies and run (if "configure") is there:

```
sudo ./configure && sudo make install
```

Obviously, after extracting the tarball and moving to that folder using ```
cd <foldername>
```

---

### Post by MadMonkey1966 on 2012-03-22
Thanks for the help.

While i as waiting for any replies i downloaded the Windows version on one of my backup PCs. When i extracted them from the .zip file, i compared the files to the ones for Ubuntu.

The shell script in Ubuntu is an .exe one in Windows, so i tried double clicking that in Ubuntu, and 'Hey Presto, it runs lol

I have extracted to a folder on the desktop now, so i can run it from there. i know its not installed, but its only a Demo.

thanks for the advice ):P

---

