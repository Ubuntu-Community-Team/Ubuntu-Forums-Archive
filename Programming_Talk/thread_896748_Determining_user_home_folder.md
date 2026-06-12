---
title: "Determining user home folder"
date: 2008-08-21
forum: Programming Talk
---

### Post by alxlabs on 2008-08-21
For the console app I used something like this
```

if ((lgn = getlogin()) == NULL || (pw = getpwnam(lgn)) == NULL) 
    	ALog->append("Get of user information failed."); 
else
{
	sprintf (tempbuf, "Working folder: %s", pw->pw_dir);
	ALog->append(tempbuf);
}

```

For some reason it does not work for graphic application if started from the shortcut on the desktop (or any other way without a console) - getlogin returns NULL... Any idea how to make it work or do it any other way?

---

### Post by LaRoza on 2008-08-21
Try getenv()

```

#include <stdio.h>
#include <stdlib.h>
int main(int argc, char ** argv)
{
    printf("%s is your $HOME\n",getenv("HOME"));
    return 0;
}

```

---

### Post by Jessehk on 2008-08-21
```

#include <stdlib.h>

int main( void ) {
    char *hd = NULL;

    if ( (hd = getenv( "HOME" )) == NULL ) {
        /* $HOME environmental variable not set */
    }

    /* hd contains the path to the user's home directory.
    return 0;
}

```

---

### Post by alxlabs on 2008-08-21
Is it possible that 'HOME' variable is not set? Do all the linux distributions have it set in all cases?

---

### Post by LaRoza on 2008-08-21
> **alxlabs said:**
> Is it possible that 'HOME' variable is not set? Do all the linux distributions have it set?

To log in, you need to have some sort of home. 

I never heard of it, but programming for the possibility wouldn't be a bad idea (if a home dir exists, the variable is set, so it shouldn't be a problem)

---

