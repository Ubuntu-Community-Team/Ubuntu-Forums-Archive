---
title: "C++ file I/O issues"
date: 2009-12-20
forum: Programming Talk
---

### Post by Muscovy on 2009-12-20
I'm having problems reading.writing files in C++. The function ifstream() can take an absolute location like /var/file, but the rest gets a bit weird. Trying ifstream(".test") should produce a hidden file in my ~/, by all logic, but it is instead placed in whatever directory my program is. I'm *sure* I've not had this happen before. ~/ seems to be an invalid file prefix here.

---

### Post by john newbuntu on 2009-12-20
If you do not supply the full path to a filename, the C++ ifstream object always places the file in the directory where the program is located.  ~/ is more of a unix concept and not C++.  If you need to place a file specifically in the home dir, one non-portable way to do this is to query the $HOME variable by using, say getenv() function and prepend that to the filename.

---

### Post by Muscovy on 2009-12-21
I've got a slightly similar problem that just cropped up. I autostarted a program by means of /etc/xdg/autostart, only to find that suddenly the program, run by root, maxes out the CPU. Is there a way to autostart programs for just... not root?

---

### Post by john newbuntu on 2009-12-21
I am surprised because generally the program under autostart gets run under the login id and not as root.  I am not sure on which program it is that you are talking about.  But you could define it as a job under system->preferences->startup applications.

---

### Post by pbrane on 2009-12-21
> **Muscovy said:**
> I'm having problems reading.writing files in C++. The function ifstream() can take an absolute location like /var/file, but the rest gets a bit weird. Trying ifstream(".test") should produce a hidden file in my ~/, by all logic, but it is instead placed in whatever directory my program is. I'm *sure* I've not had this happen before. ~/ seems to be an invalid file prefix here.

The ~ (tilde) is expanded by the shell. C++ has no concept of that. If you want to programatically open/create files you should use the full path.

---

### Post by not_a_phd on 2009-12-22
My experience with C/C++ file IO in Linux is that they are created in the 'current working directory'. You could run your program from the directory that you want your files to be created:

```
~/myprogrammpath/myprogram  
```

You can change your current working directory from inside your program using the chdir() function. Better yet, you can pass your desired output path to your program as an argument.

```

#include<unistd.h>

int main(int argc, char *arg[]) {
char mypath[MAXPATH];
.
.
strcpy(path,arg[1]); // copy output path from argument list

   if(chdir(mypath) < 0) {
      printf("Failed to Change Working Director to %s\n",mypath);
   }


```

---

### Post by nvteighen on 2009-12-23
It works using the CWD. If you access the program from somewhere else (i.e. not cd'ing into its folder), you'll see how the test file will be created at your current location.

---

