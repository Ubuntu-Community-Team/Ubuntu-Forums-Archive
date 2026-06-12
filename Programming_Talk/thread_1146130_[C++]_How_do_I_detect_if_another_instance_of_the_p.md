---
title: "[C++] How do I detect if another instance of the program is already running?"
date: 2009-05-02
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-05-02
Hello,

How do I detect if another instance of the program is already running?
Also how do I pass data from the new instance to the old one? (eg. a filename passed at the command line)

I don't know if it is relevant but I use gtkmm. Does it have any related functions?

Any docs/tutorials/example code are welcome.

---

### Post by eye208 on 2009-05-02
Most applications use some kind of lockfile for this purpose. For example, Firefox will create a symbolic link "lock" inside a subfolder of "~/.mozilla" on startup. This link doesn't point at another file but contains the process number of the running Firefox instance belonging to this user.

The process number can be used to connect to the running Firefox via [Unix domain sockets](http://en.wikipedia.org/wiki/Unix_domain_socket) and pass information to it, such as command line parameters that were given to the new instance. If the process doesn't exist any more, it's an indicator that the previous instance of Firefox crashed and could not delete the lock. In this case, the lockfile can be removed/replaced by the new instance.

---

### Post by Kareeser on 2009-05-02
ps aux | grep [searchterm]

---

### Post by mmix on 2009-05-02
you can't(progname can be changed), but here is simple hack.

```

#include <stdio.h>
extern const char *__progname;

int main()
{
    if( strncmp("a.out", __progname, 5) ==0)
    {
        printf("a.out is already running\n");
        return 1;
    }
    printf("process name: %s\n", __progname);
    
    return 0;
}

```

---

### Post by Arndt on 2009-05-02
> **Kareeser said:**
> ps aux | grep [searchterm]

There is also 'pgrep'.

---

### Post by Arndt on 2009-05-02
> **mmix said:**
> you can't(progname can be changed), but here is simple hack.

```

#include <stdio.h>
extern const char *__progname;

int main()
{
    if( strncmp("a.out", __progname, 5) ==0)
    {
        printf("a.out is already running\n");
        return 1;
    }
    printf("process name: %s\n", __progname);
    
    return 0;
}

```

I don't think this achieves what the OP asked for. In what way does this test whether some other process is running?

---

### Post by mmix on 2009-05-02
> **Arndt said:**
> I don't think this achieves what the OP asked for. In what way does this test whether some other process is running?

a.out is the progname of above code.
and check instance of a.out.

---

### Post by dwhitney67 on 2009-05-02
> **mmix said:**
> a.out is the progname of above code.
and check instance of a.out.

I agree with Arndt; you might as well have coded:
```

#include <cstdio>

int main(int argc, char** argv)
{
  printf("%s is already running.\n", argv[0]);
}

```

---

### Post by mmix on 2009-05-03
> **dwhitney67 said:**
> I agree with Arndt; you might as well have coded:
```

#include <cstdio>

int main(int argc, char** argv)
{
  printf("%s is already running.\n", argv[0]);
}

```

Correct.
So, i made another example which actually works.

```

#include <stdio.h>
#include <string.h>
#include <dirent.h>
#include <linux/limits.h>
#include <unistd.h>

#define P	"/proc"
#define S	"/status"

#define BUFFER 100

extern const char *__progname;

int main()
{
	DIR *dp;
	struct dirent *dirp;
	
	FILE *fp;
	char path[PATH_MAX]={0}; 
	char file[BUFFER]={0};
	char Name[BUFFER]={0};
	char Pid[BUFFER]={0};
	
	sprintf(Name, "Name:\t%s\n",  __progname);
	sprintf(Pid, "Pid:\t%d\n", getpid());
	
	if( (dp = opendir(P)) == NULL)
	{
		printf("couldn't read directory");
		return 1;
	}
	
	while( (dirp = readdir(dp)) != NULL)
	{
		if( atoi(dirp->d_name) != 0)
		{
			strcat(path,P);
			strcat(path,"/");
			strcat(path,dirp->d_name);
			strcat(path,S);
			fp = fopen(path, "r");
			if( fp == NULL)
			{
				printf("error opening status\n");
				return 1;
			}
			else
			{
				fgets(file,BUFFER, fp);
				if(strcmp(Name, file)==0)
				{	
					memset(file, 0, sizeof(file));
					fgets(file, BUFFER, fp);
					fgets(file, BUFFER, fp);
					fgets(file, BUFFER, fp);
					if( strcmp( Pid, file)!=0)
					{
						printf("processing already running\n");
						return 1;						
					}

				}
				
				memset(file, 0, sizeof(file));
			}
			memset(path, 0, sizeof(path));	
			fclose(fp);
		}
	}
	
	printf("process is starting\n");
	while(1)
	{
		if(getchar())
			break;
	}
	
	closedir(dp);

	
	return 0;
}

```

---

### Post by Arndt on 2009-05-03
> **mmix said:**
> Correct.
So, i made another example which actually works.

```

#include <stdio.h>
#include <string.h>
#include <dirent.h>
#include <linux/limits.h>
#include <unistd.h>

#define P	"/proc"
#define S	"/status"

#define BUFFER 100

extern const char *__progname;

int main()
{
	DIR *dp;
	struct dirent *dirp;
	
	FILE *fp;
	char path[PATH_MAX]={0}; 
	char file[BUFFER]={0};
	char Name[BUFFER]={0};
	char Pid[BUFFER]={0};
	
	sprintf(Name, "Name:\t%s\n",  __progname);
	sprintf(Pid, "Pid:\t%d\n", getpid());
	
	if( (dp = opendir(P)) == NULL)
	{
		printf("couldn't read directory");
		return 1;
	}
	
	while( (dirp = readdir(dp)) != NULL)
	{
		if( atoi(dirp->d_name) != 0)
		{
			strcat(path,P);
			strcat(path,"/");
			strcat(path,dirp->d_name);
			strcat(path,S);
			fp = fopen(path, "r");
			if( fp == NULL)
			{
				printf("error opening status\n");
				return 1;
			}
			else
			{
				fgets(file,BUFFER, fp);
				if(strcmp(Name, file)==0)
				{	
					memset(file, 0, sizeof(file));
					fgets(file, BUFFER, fp);
					fgets(file, BUFFER, fp);
					fgets(file, BUFFER, fp);
					if( strcmp( Pid, file)!=0)
					{
						printf("processing already running\n");
						return 1;						
					}

				}
				
				memset(file, 0, sizeof(file));
			}
			memset(path, 0, sizeof(path));	
			fclose(fp);
		}
	}
	
	printf("process is starting\n");
	while(1)
	{
		if(getchar())
			break;
	}
	
	closedir(dp);

	
	return 0;
}

```

It doesn't work, but almost. For me, it compares a line beginning with "Pid" with a line beginning with "Tgid", and they will never match, so it will report itself as being a different process. Maybe the /proc/*/status format is not reliable across releases. /proc/*/stat probably is - at least it's documented in detail.

Why not compare with the result of getpid()?

---

### Post by SledgeHammer_999 on 2009-05-03
Interesting stuff. I think the lockfile is the simplest and easiest approach. I will look into it more. Thank you all.

---

### Post by mmix on 2009-05-03
> **Arndt said:**
> It doesn't work, but almost. For me, it compares a line beginning with "Pid" with a line beginning with "Tgid", and they will never match, so it will report itself as being a different process. Maybe the /proc/*/status format is not reliable across releases. /proc/*/stat probably is - at least it's documented in detail.

Why not compare with the result of getpid()?

/proc/*/stat version. :)
all code belongs to GPLv3

```

#include <stdio.h>
#include <string.h>
#include <dirent.h>
#include <linux/limits.h>
#include <unistd.h>

#define P    "/proc"
#define S    "/stat"

#define BUFFER 100

extern const char *__progname;

int main()
{
    DIR *dp;
    struct dirent *dirp;
    
    FILE *fp;
    char path[PATH_MAX]={0}; 
    char file[BUFFER]={0};
    char Name[BUFFER]={0};
    char name[BUFFER]={0};
    pid_t Pid;
    pid_t pid = getpid();
    
    sprintf(name,"(%s)", __progname);
    
    if( (dp = opendir(P)) == NULL)
    {
        printf("couldn't read directory");
        return 1;
    }
    
    while( (dirp = readdir(dp)) != NULL)
    {
        if(  atoi(dirp->d_name)  != 0)
        {
            strcat(path,P);
            strcat(path,"/");
            strcat(path,dirp->d_name);
            strcat(path,S);
            fp = fopen(path, "r");
            if( fp == NULL)
            {
                printf("error opening stat\n");
                return 1;
            }
            else
            {
                fscanf(fp, "%d", &Pid);
                fscanf(fp, "%s", Name);
                
                if( (strcmp(name, Name) == 0) && (pid != Pid))
                {
                    printf("process is already running.\n");
                    return 1;
                }
                
                memset(Name, 0, sizeof(Name));
                
            }
            memset(path, 0, sizeof(path));    
            fclose(fp);
        }
    }
    
    printf("process is starting\n");
    while(1)
    {
        if(getchar())
            break;
    }
    
    closedir(dp);

    
    return 0;
}

```

---

### Post by SledgeHammer_999 on 2009-05-26
Sorry to revive it, but in case someone is reading(in the future). Another interesting solution is D-bus.

---

