---
title: "Custom Shell Command (help)"
date: 2007-04-25
forum: Programming Talk
---

### Post by jlebrech on 2007-04-25
This code compiles but segfaults on run.

Basically this command should return the latest opened file, and with the switch open the next one down the line.



```


#include <sys/stat.h>			
#include <sys/types.h>			
#include <unistd.h>		
#include <stdio.h>			
#include <time.h>
#include <dirent.h>

/*
		Latest From List Command (lfl)
		
		Usage
		-----
		
		lfl       -- will return latest accessed file from a directory
		lfl next  -- will find the lastest accessed file but will return the one after
		
		vi | lfl /etc/      -- Will open the last accessed file in /etc/
		mplayer | lfl next  -- Will play the file after the last opened file		
*/

time_t last_accessed(char * filename);

/************************************************************************/

int main( int argc, char argv[] )
{
    time_t highest_atime;
	char * last_accessed_file_name = malloc(50 * sizeof (char));;
	char * one_after_last_accessed_file_name = malloc(50 * sizeof (char));;
	
	DIR * dir_p;
	struct dirent * dir_entry_p;
	
	if (argc > 0) {
		dir_p = opendir(argv[0]);
	} else {
		dir_p = opendir(".");
	}
	
	time_t itime;
	int iwas_latest;
	iwas_latest = 0;
	
	while( NULL != (dir_entry_p = readdir(dir_p)))
	{
		itime = last_accessed(dir_entry_p->d_name);
		if (itime > highest_atime) {
			highest_atime = itime;
			last_accessed_file_name = (char *)dir_entry_p->d_name;
			iwas_latest = 1;
		} else {
			
			if ( iwas_latest == 1 ){
				one_after_last_accessed_file_name = (char *)dir_entry_p->d_name;
			}
			iwas_latest = 0;
		}
	}
	
	
	if ((argc > 1)&&(strcmp(argv[1],"next") == 1)){
		printf(one_after_last_accessed_file_name);
	} else {
		printf(last_accessed_file_name);
	}
	
	return 0;
	
}

/************************************************************************/

time_t last_accessed(char * filename)
{
   struct stat stat_p;

   if ( -1 ==  stat (filename, &stat_p))	
      {
      printf(" Error occoured attempting to stat %s\n", filename);
      exit(0);
      }

   return stat_p.st_atime;
}


```

---

### Post by rjack on 2007-04-25
Two suggestions and one order:

- always compile with -ansi -pedantic -Wall options
- use -g option of gcc and use gdb to debug
- check for error conditions after each syscall

Fix this:
```
dir_p = opendir(argv[0]);
```
You are passing argv[0] to opendir, but the first of the argv array is the program name; therefore opendir returns NULL, you don't check this error and pass a null pointer to readdir: segfault.

PS: ```
lfl.c:29: warning: second argument of &#8216;main&#8217; should be &#8216;char **&#8217;
```

---

