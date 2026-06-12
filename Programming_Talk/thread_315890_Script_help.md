---
title: "Script help"
date: 2006-12-09
forum: Programming Talk
---

### Post by pjman on 2006-12-09
I'd like to run a script that executes the following command:

```
cdrdao read-cd --read-raw --datafile ***<name of CD>***.bin --device ATAPI:0,0,0 --driver generic-mmc-raw ***<name of CD>***.toc
```

I want the ***<name of CD>*** to be automatically pulled from the title of the CD (it's a data cd). I'd probably be able to figure it out but I don't know the command to get the title of the inserted CD. Can anyone help me with this?

Thanks!

---

### Post by po0f on 2006-12-10
pjman,

I can't give you a specific answer, but I can point you in the right direction.  You will want to look into D-BUS, and possibly, HAL.

---

### Post by lnostdal on 2006-12-10
this is probably simple enough to do in a SH-script:

```

lars@ibmr52:~/programming$ volname /dev/cdrom
Ubuntu 6.10 i386   

```
 ..right .. so:

```

lars@ibmr52:~/programming$ emacs -nw getVolName.sh 
lars@ibmr52:~/programming$ cat getVolName.sh
#!/usr/bin/env sh
echo "Volume name is \"`volname /dev/cdrom`\"."
lars@ibmr52:~/programming$ chmod +x getVolName.sh
lars@ibmr52:~/programming$ ./getVolName.sh
Volume name is "Ubuntu 6.10 i386                ".

```

..you probalby get the idea.. :)

---

### Post by po0f on 2006-12-10
lnostdal,

I knew there had to be a simple command as the answer.  I'm sure I'll find this useful.  :)

---

### Post by pjman on 2006-12-10
Cool. I'll give it a try. 

Thanks for the help!

---

### Post by pjman on 2006-12-10
I'm almost there. Does anyone know how to get rid of the blank space before the "."?

```
Volume name is "Ubuntu 6.10 i386                ".
```

Thank you!

**Edit**

I got it working using 'sed' following the FAQ [here]("http://sed.sourceforge.net/grabbag/tutorials/sedfaq.txt") (section 3.2). I just wish I understood how sed works :-)

Here's the code for the script in case anyone is interested.

```

#!/usr/bin/env sh
cdrdao read-cd --read-raw --datafile "`volname /dev/hdc | sed 's/[ ^t]*$//'`".bin --device ATAPI:0,0,0 --driver generic-mmc-raw "`volname /dev/hdc | sed 's/[ ^t]*$//'`".toc

```

I had to use /dev/hdc and not /dev/cdrom, I'm not sure why.

---

