---
title: "can someone help me compile this small program ?"
date: 2006-04-27
forum: Programming Talk
---

### Post by index_0@ya.com on 2006-04-27
Hi , 
In search of exec command , i 've landed up in misery for last two days !
I am a newbie into gcc, and i couldnt compile this simple program, !

#include <unistd.h>

int main(){
	exec("/bin/ls");
}

on compiling,
an error is generated telling

exec is not refrenced ,

what's wrong?
sorry i dont 've the exact compiler error message .. 

thx in advance

---

### Post by M4av0 on 2006-04-27
i think there is no exec function. you have to call one of the execv functions, try cat unistd.h |grep exec. but there is a small trick involved in using these functions. here is a link i found usefull, hope it helps: [http://yolinux.com/TUTORIALS/ForkExecProcesses.html](http://yolinux.com/TUTORIALS/ForkExecProcesses.html)

have fun with programming

---

### Post by mscman on 2006-04-27
Here is the correct code for that program:
```
#include <unistd.h>

int main()
{
        char *args[] = {"-r", "-t", "-l", (char *) 0 };
        execv("/bin/ls", args);
}

```
Hopefully you visit the link in the above post to learn more about the commands, but if you're simply wanting it to compile, that's how it goes.;)

---

### Post by index_0@ya.com on 2006-04-27
thx  ,,,
it works....

---

### Post by zkissane on 2006-04-28
You should get in the habit of putting "return 0;" at the end of your main function (or, when you learn more about error codes, use them too).  Your particular version of your particular compiler may not complain if you leave off the return value, but some will force you to put one there.

---

