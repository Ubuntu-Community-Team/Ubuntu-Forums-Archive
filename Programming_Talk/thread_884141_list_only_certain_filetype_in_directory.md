---
title: "list only certain filetype in directory"
date: 2008-08-08
forum: Programming Talk
---

### Post by Neon612 on 2008-08-08
I've read up somewhat on boostfilesystem and the normal scandir way of listing files in a directory. The example programs I have tried worked great, but I'd like to limit the list feature to only look for a certain filetype, mp3.

What would be the best way of doing this? Boost or scandir? This does not have to work on multiple platforms, and I'm also just learning C++ at the moment (only a month of writing code behind me) so I'd like a simpler way of doing this for the time being.

Thank you.

---

### Post by Reiger on 2008-08-08
Well you could use a regular expression; if supported?

For instance, in bash:

```
ls *.mp3
```

---

### Post by Neon612 on 2008-08-08
I have some C++ sample code that I'd like to change to let it search only for mp3 files.
[php]#include <stdio.h>
#include <dirent.h>
     
static int one (const struct dirent *unused)
{
  	return 1;
}
     
int main (void)
{
       	struct dirent **eps;
       	int n;
     
       	n = scandir ("./", &eps, one, alphasort);
       	if (n >= 0)
        {
           	int cnt;
           	for (cnt = 0; cnt < n; ++cnt)
             		puts (eps[cnt]->d_name);
        }
   	else
     		perror ("Couldn't open the directory");
     
   	return 0;
}[/php]

---

### Post by thegom on 2008-08-08
The third argument scandir takes is "filter", which is a pointer to a function you write yourself to filter out entries - one way is to do it like this:

[PHP]#include <stdio.h>
#include <dirent.h>
#include <string>
int mp3filter(const struct dirent *dir)
// post: returns 1/true if name of dir ends in .mp3    
{
  const char *s = dir->d_name;
  int len = strlen(s) - 4;	// index of start of . in .mp3
  if(len >= 0)
    {
      if (strncmp(s + len, ".mp3", 4) == 0)
	{
	  return 1;
	}
    }
  return 0;
}

static int one (const struct dirent *unused)
{
  return 1;
}

int main (void)
{
  struct dirent **eps;
  int n;

  n = scandir ("./", &eps, mp3filter, alphasort);
  if (n >= 0)
    {
      int cnt;
      for (cnt = 0; cnt < n; ++cnt)
	puts (eps[cnt]->d_name);
    }
  else
    perror ("Couldn't open the directory");

  return 0;
}[/PHP]

---

### Post by Neon612 on 2008-08-09
Thank you that works like a charm.

Now with the output, the puts command is what outputs each filename, right?
What does the (eps[cnt]->d_name) command mean or do?

---

### Post by thegom on 2008-08-09
Yeah, according to [this]("http://www.cplusplus.com/reference/clibrary/cstdio/puts.html") puts("something") behaves like printf("something); or cout << "something";, except it automatically includes a newline at the end - I've never used it before tho.

As for the (eps[cnt]->d_name, you have an array of pointers to dirent's called eps. the -> operator lets you access an attribute from a pointer to an object/struct, where normally you would use structname.attributename to access the attribute if it wasn't a pointer.

---

