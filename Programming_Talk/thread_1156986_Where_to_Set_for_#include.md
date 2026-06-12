---
title: "Where to Set for #include"
date: 2009-05-12
forum: Programming Talk
---

### Post by huangyingw on 2009-05-12
hello, 
    When I use dirent * ptr in my *.c file,the gcc return me error:‘dirent’ undeclared. I have use #include <dirent.h> statement.
    I wonder to where the gcc compilor search for the #include file, and how could I update info for GCC, so, it could find the right thing?
    I have found the dirent.h located at /usr/include/dirent.h. So I manually add following two lines in /etc/profile, and reboot.
    ```

PATH=/usr/include:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
INCLUDE=/usr/include:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games   
    
```
After rebooting,it seems that my efforts do not take effect, for I still got error: ‘dirent’ undeclared.

---

### Post by Zugzwang on 2009-05-12
Please, never change the environment variables for the include files! *Always* add the correct path to your command when compiling.

If the compiler cannot find "dirent.h", check that you have the package "build-essential" compiled and that you include it the following way: "#include <dirent.h>". You should never get some "dirent" undeclared error. If you have build-essential installed, please copy&paste your code here and - important - copy and paste the compiler error along with the command you used for compiling.

---

### Post by huangyingw on 2009-05-12
yes, I have installed the build-essential. Thank you first for reviewing my codes. If these codes are two long, I will hurry a shortest code to demo my trouble.
It is time for bed now. See you tomorrow.
dir.c:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <dirent.h>
#include <sys/types.h>
#include <sys/stat.h>

void FindAllFile(char * pFilePath)
{
	DIR * dir;
	dirent * ptr;
	struct stat stStatBuf;
	chdir(pFilePath);
	dir = opendir(pFilePath);
	while ((ptr = readdir(dir)) != NULL)
	{
		if (stat(ptr->d_name, &stStatBuf) == -1)
		{
			printf("Get the stat error on file:%s\n", ptr->d_name);
			continue;
		}
		if ((stStatBuf.st_mode & S_IFDIR) && strcmp(ptr->d_name, ".") != 0
			&& strcmp(ptr->d_name, "..") != 0)
		{
			char Path[MAX_PATH];
			strcpy(Path, pFilePath);
			strncat(Path, "/", 1);
			strcat(Path, ptr->d_name);
			findAllFile(Path);
		}
		if (stStatBuf.st_mode & S_IFREG)
		{
			printf("  %s\n", ptr->d_name);
		}
		//this must change the directory , for maybe changed in the recured function
		chdir(pFilePath);
	}
	closedir(dir);
}

int main(void)
{
	FindAllFile("/root/myproject/linux/shell/folder/");
	return   0;
}

```
makefile:
```

run : dir.o
	gcc -o run dir.o
dir.o : dir.c
	gcc -c dir.c
clean :
	rm run dir.o

```
output of make command:
```

gcc -c dir.c
dir.c: In function ‘FindAllFile’:
dir.c:11: error: ‘dirent’ undeclared (first use in this function)
dir.c:11: error: (Each undeclared identifier is reported only once
dir.c:11: error: for each function it appears in.)
dir.c:11: error: ‘ptr’ undeclared (first use in this function)
dir.c:25: error: ‘MAX_PATH’ undeclared (first use in this function)
dir.c:26: warning: incompatible implicit declaration of built-in function ‘strcpy’
dir.c:27: warning: incompatible implicit declaration of built-in function ‘strncat’
dir.c:28: warning: incompatible implicit declaration of built-in function ‘strcat’
make: *** [dir.o] Error 1

```

---

### Post by Zugzwang on 2009-05-12
> **huangyingw said:**
> 
dir.c:11: error: ‘dirent’ undeclared (first use in this function)
[/code]

The problem is that it has to be "struct dirent *" and not "dirent *" in the respective line (11) in your code. If the compiler had problems reading dirent.h, the line number of the compiler error would correspond to the line in which you include dirent.h.

---

### Post by huangyingw on 2009-05-12
> **Zugzwang said:**
> The problem is that it has to be "struct dirent *" and not "dirent *" in the respective line (11) in your code. If the compiler had problems reading dirent.h, the line number of the compiler error would correspond to the line in which you include dirent.h.
hmmmm.:),thank you.
I have experimented to add #include <mybad.h>, and the compilor reports the same as you describe...

---

