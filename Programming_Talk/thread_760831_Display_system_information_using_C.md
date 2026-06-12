---
title: "Display system information using C"
date: 2008-04-20
forum: Programming Talk
---

### Post by Woody1987 on 2008-04-20
I am currently writing a little program, its use doesnt matter right now, but i would like to be able to display information about the current system within the app, i.e. linux distro, kernel version, graphics card, graphics driver, cpu and memory. How would i go about doing this in c? I dont know where to start on this.

---

### Post by nfm on 2008-04-20
We can use int system(const char*s) function from stdlib.h
```
#include <stdlib.h>
 
int main(void)
{
    system("uname -a && lspci | grep 'VGA'");
    return 0;
}
```
outputs:
> Linux phenon 2.6.25 #1 SMP Thu Apr 17 23:34:07 CDT 2008 x86_64 GNU/Linux
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

Other way I can think of is to open a file from /proc e.g /proc/version and print it and then close it.

______________________________
A second try:
```
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE *file1;
    
    file1 = fopen("//proc//version", "r");
    if (file1 == NULL)
    {
        perror("file1");
        exit(1);
    }
    
    char buffer[100];
    while (fgets(buffer, sizeof(buffer), file1) != NULL)
        fputs(buffer, stdout);
    
    fclose(file1);
    return 0;
}
```

---

### Post by Woody1987 on 2008-04-20
Thanks for the reply, i will try this.

I dont know if you use a nvidia graphics card but if you do open up nvidia-settings and look at the X Server Information tab and you will see something similar to what i want.

---

### Post by kaivalagi on 2008-04-20
It might be worth taking a look at the conky source code. Conky displays system information such as cpu usage, disk io etc, on the desktop. It is written in C.

The main website is [http://conky.sourceforge.net/]("http://conky.sourceforge.net/"). 

The source can be downloaded from [http://sourceforge.net/project/showfiles.php?group_id=143975]("http://sourceforge.net/project/showfiles.php?group_id=143975")

Hope that helps

---

