---
title: "HELP! scandir can't read /proc"
date: 2010-04-14
forum: Programming Talk
---

### Post by PanP5 on 2010-04-14
Sorry for the caps, but I'm on a time crunch.

Two bits of code:

scandir:

```
int main (void)
{
   struct dirent **eps;
   int n;
   n = scandir ("/proc", &eps, selector, alphasort);
   if (n >= 0)
   {
     //Do stuff
   }
   else
      perror ("Couldn't open the directory");

   return 0;
}
```


readdir_r:
```
int main (void)
{
  DIR *dp;
  struct dirent *ep, *result;

  dp = opendir ("/proc");

  if (dp != NULL)
  {
     while(!readdir_r (dp, ep, &result) && result)
     puts (ep->d_name);

    (void) closedir (dp);
  }
  else
    perror ("Couldn't open the directory");

  return 0;
}

```

Both programs work perfectly in most directories. However, the first one, using scandir, can't open /proc. It always goes to the else statement. The second one, using readdir_r, can open the /proc "directory" just fine.

What's going on, and how can I debug this? They compile just fine, no warnings. I can't imagine it's a permissions issue, since the readdir_r code has no problem accesing /proc. And the scandir code works perfectly for all other directories I've tested it in.

I can rewrite my code to use readdir, but it would be messier, and I'd rather not backtrack. Any ideas?

---

### Post by PanP5 on 2010-04-14
> **PanP5 said:**
> Both programs work perfectly in most directories.

When I tested it in other directories, I changed the string literal in the code to refer to another directory.

---

### Post by Some Penguin on 2010-04-14
Have you checked what errno is set to?

Incidentally, I could see issues if scandir() is itself changing /proc while it is reading directory entries.

---

### Post by gmargo on 2010-04-14
What kind of error are you getting?  You did not provide code for your selector() function; perhaps that is faulty? 

Here's some scandir(/proc) code that works for me on Hardy (almost verbatim from the scandir(3) man page):

```

#include <stdio.h>
#include <dirent.h>

int
main(void)
{
    struct dirent **namelist;
    int n;

    n = scandir("/proc", &namelist, 0, alphasort);
    if (n < 0)
        perror("scandir");
    else
    {
        while (n--)
        {
            printf("%s\n", namelist[n]->d_name);
            free(namelist[n]);
        }
        free(namelist);
    }
}


```

---

### Post by PanP5 on 2010-04-14
> **Some Penguin said:**
> Have you checked what errno is set to?

> **gmargo said:**
> What kind of error are you getting?  You did not provide code for your selector() function; perhaps that is faulty? 

I checked errno, saw it wasn't set, was baffled, and then realized that the error was occuring in the if statement. I left that stuff out above. Here's my code in full, adding a second check for errno:


```
//I'm making the assumption that only process "directories" in /proc start with a numeral  
static int selector (const struct dirent *entry)
{
//  cout << "In selector, first char of dirent d_name: " << entry->d_name <<endl;
  if(isdigit(entry->d_name[0]))
     return 1;
  else return 0;
}

int main (void)
{
   struct dirent **eps;
   int n;
   ifstream in;
   string process_name, process_dir;
   int process_id;
   Proc p(0,"");
   cout << "Starting: " << endl;
   n = scandir ("/proc", &eps, selector, alphasort);
   if (n >= 0)
   {
      int cnt;
      for (cnt = 0; cnt < n; ++cnt)
      {
         process_dir = eps[cnt]->d_name;
         process_dir += "/stat";

         in.open(process_dir.c_str());

         if(!in){
           cout << "Could not open: " <<errno << endl;
           return -1;
         }
         in >> process_id; //we're only interested in the second word of
         in >> process_name; //this file, which is the process name 

         p.setName(process_name);
         p.setId(process_id);

        in.close();
        cout << p.getId() << " " << p.getName() << endl;
      }

   }
   else
      perror ("Couldn't open the directory");
      cout << ": " << errno;
   cout << "Done!" << endl;
   return 0;
}

```

errno is set to 2

---

### Post by PanP5 on 2010-04-14
The problem is happening on this line:

in.open(process_dir.c_str());

---

### Post by PanP5 on 2010-04-14
> **gmargo said:**
> What kind of error are you getting?  You did not provide code for your selector() function; perhaps that is faulty? 

Here's some scandir(/proc) code that works for me on Hardy (almost verbatim from the scandir(3) man page):

```

#include <stdio.h>
#include <dirent.h>

int
main(void)
{
    struct dirent **namelist;
    int n;

    n = scandir("/proc", &namelist, 0, alphasort);
    if (n < 0)
        perror("scandir");
    else
    {
        while (n--)
        {
            printf("%s\n", namelist[n]->d_name);
            free(namelist[n]);
        }
        free(namelist);
    }
}


```

I tried your code. g++ complained that "free" was not declared in that scope. I commented those lines out though, and the code worked just fine.

Weird. I'm going to try to drop my selector function, see if that has anything to do with it.

---

### Post by PanP5 on 2010-04-14
> **PanP5 said:**
> Weird. I'm going to try to drop my selector function, see if that has anything to do with it.

Geez. I'm over tired. This has nothing to do with scandir. My in stream can't open the stat files.

---

### Post by PanP5 on 2010-04-14
The string process_dir is built in a way that assumes that the process directories are in same directory as the executable, which was the case when I tested the code.

It failed because I was trying to open files in /proc.

I assumed it was an issue with scandir, and the fact that my correct code for readdir_r was working threw me off.

5+ hours on a careless error. Jebus.

---

