---
title: "[C] Why does stat() not recognize the tilde (~)?"
date: 2009-01-23
forum: Programming Talk
---

### Post by Jesdisciple on 2009-01-23
I finally finished debugging a problem right before posting it here.  It was mostly my fault, because I was passing "$HOME" to getenv() when it should just be "HOME".  But I had a backup solution, in case the environment variable wasn't defined:```
        home = getenv("$HOME");
        if(home == (char *)NULL)
            home = "~";
```When I passed such a path through stat(), it consistently claimed the directory didn't exist, but then my system() call to mkdir would correctly translate the tilde.  In case anyone wants to verify this, my test for a directory's existence follows:```
short dir_exists(char *filename){/* Modified from http://codelupus.wordpress.com/2008/04/16/how-to-check-if-a-file-exists-in-c/ */
    struct stat buf;
    return stat(filename, &buf) >= 0 && S_ISDIR(buf.st_mode) != 0;
}
```That always returned (-1 >= 0 && 0 != 0) when the tilde was used.  So I wonder why stat() doesn't recognize the tilde?

---

### Post by johnl on 2009-01-23
Your system call works because the "mkdir" executable translates the tilde into the $HOME environmental variable.  

stat, on the other hand, is a low level function with a specific purpose;  it's purpose does not include looking for a tilde in the string you pass in, looking up the current user's $HOME directory, and substituting it.  Imagine if every low level filesystem function had to do that.

I guess the short answer is if you want your program to support tilde expansion you'll need to do it manually before calling stat().

Hope this helps!

---

### Post by Jesdisciple on 2009-01-23
Then I guess the tilde wouldn't work anyway if HOME were undefined.  But the Open Group don't specify that HOME must be defined, and in fact [they imply that it might not be]("http://www.opengroup.org/onlinepubs/009695399/utilities/cd.html").  So if (getenv("HOME") == (char *)NULL), is there any other reliable source for the path to the user's home directory?

Sorry to veer off the stated topic a bit...

---

### Post by johnl on 2009-01-23
I actually was just looking at this :)

```

#include <pwd.h>
#include <sys/types.h>
#include <unistd.h>

struct passwd* pwd = getpwuid(geteuid());

if (pwd) {
    printf("user's home directory is %s\n", pwd->pw_dir);
}

```

Will grab the user's home directory out of the /etc/passwd file.
You can use getpwname(username) if you have a username to lookup instead of the current effective user.


Edit:  [this page](http://www.gnu.org/software/libtool/manual/libc/Tilde-Expansion.html) is where i tracked this information down from.

It sounds like the process is this:

If you just want to expand '~' (eg, "~" or "~/foo/bar") use $HOME, if that doesn't work, use the process I mentioned above.

If you want to expand '~user' (eg "~user" or "~user/foo/bar") use the getpwnam() method.

---

### Post by Jesdisciple on 2009-01-23
Well, I don't like the language "if the value of HOME is not really your home directory" on that page very much, so I'll just go with getpwuid() for all *nix systems.  (Or would that likely indicate that the user wants his files stored there instead?) Thanks!

---

### Post by wmcbrine on 2009-01-23
> **johnl said:**
> Your system call works because the "mkdir" executable translates the tilde into the $HOME environmental variable.Actually it's the shell that expands it (system() calls via the shell).

---

### Post by JupiterV2 on 2009-01-23
> **wmcbrine said:**
> Actually it's the shell that expands it (system() calls via the shell).

This is correct.

---

