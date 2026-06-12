---
title: "Problem with 'Open' a serial port since 10.10"
date: 2010-12-06
forum: Programming Talk
---

### Post by ritchie-w on 2010-12-06
Hi,

after I updated my system I can not open a serial port on my system anymore.

The following code is used and worked with 9.4 and 10.4 without any problems.

> 
	if ((fd = open(p, O_RDWR | O_NOCTTY | O_SYNC )) == -1)
		{
                ... failure return;
                }


It always run into failure return.

Thanks for help

R.

---

### Post by Zugzwang on 2010-12-06
Perhaps the "name" of the port has changed? What does "p" in your code refer to? After the update, the device might have a different name (e.g., "/dev/ttyUSB0"). Modify your program to put out the name of the device you actually tried to open, "ls" into the "/dev" directory and check that:
[LIST]
[*]The name of the device stayed the same.
[*]You still have sufficient access rights.
[/LIST]

---

### Post by dwhitney67 on 2010-12-06
What is the value of "errno"?

```

#include <errno.h>
#include <string.h>
#include <stdio.h>

...

if ((fd = open(p, O_RDWR | O_NOCTTY | O_SYNC )) == -1)
{
   **printf("%s (%d)\n", strerror(errno), errno);**
}

...

```

---

### Post by ritchie-w on 2010-12-06
Hi,

the code works fine with the software, before I updated the system to 10.10.

The Error code is -1 

> 
const		char	*p;

	p=comPortString.toLocal8Bit();						// Convert QT -> char

	if ((fd = open(p, O_RDWR | O_NOCTTY | O_SYNC )) == -1)
		{
		ErrorText=tr("initPort: Can't open device %1").arg(comPortString);
		ErrorStatus=true;
		return;
		}
}


ls shows
> 
crw-rw-rw- 1 root dialout 4, 64 2010-12-06 18:36 ttyS0


On my second laptop, the same code does not return from function.
I add a print out into the code and it does not shows the printf behind.


What does "root dialout 4 mean" ?

Edit:
I also tried
> 
sudo chmod o+rw /dev/ttyS0 

After that I works once.
Regard

R.

---

### Post by dwhitney67 on 2010-12-06
> **ritchie-w said:**
> 
The Error code is -1 

No it is not; that is the return code from open().  What I was asking for is the value of _errno_.  Don't confuse the two.

> **ritchie-w said:**
> 
What does "root dialout 4 mean" ?

"root" is who owns the file; "dialout" is the group that is assigned to the file.  Thus if you are root, or within the dialout group, then you would have access to the file.  Others would not, unless world permissions were to be altered.

If you are unaware of the basics of file ownership/permissions, I would suggest that you refrain from using "sudo" on anything.  You are risking the state of your system.

---

### Post by ritchie-w on 2010-12-06
Hi,

the user is member of "dialout", so no problems with that.

But I noticed as well, that the convertion from QT String to char * does not work as I thought.

As well, during the update of 9.4 to 10.10, the QT lib changed as well from 4.5 to 4.7. I have to check what everything changed for this reason as well.

Thanks for help so far, will return, if I have more detailed questions.

Regards

R.

---

### Post by ritchie-w on 2010-12-06
So

the first change I get.

The USB converter did not work on '/dev/ttyUSB0' anymore,
but it looks like, that the port '/dev/ttyS0' now works.

Now I have to figure out what flags (tcgetAttr() has been changed,
because my binary transmission did not work up to now.

Sometimes I can open the port, sometimes not.
Failure message: Port not existing.

ls /dev/ttyS0 check, file existing :-(  


Regards

R.

---

### Post by Zugzwang on 2010-12-07
@OP: You still did not incorporate the errno-printf line from dwhitney, right? Which precise error message are you getting with that line? Please copy&paste.

It might simply be the case that the port is already in use by another program.

---

