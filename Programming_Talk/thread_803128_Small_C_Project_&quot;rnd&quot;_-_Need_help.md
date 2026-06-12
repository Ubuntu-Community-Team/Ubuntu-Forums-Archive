---
title: "Small C Project &quot;rnd&quot; - Need help"
date: 2008-05-22
forum: Programming Talk
---

### Post by sq377 on 2008-05-22
EDIT: Updated to a new version, made a few changes, renamed to lsrnd, also added patch from panayk.

Edit: Fixed small bug in code

My media center doesn't have a gui, I use ssh + mplayer so that I can use my laptop as a remote.  Now I wanted a way to shuffle media, so I created a c program to do this.

The basic concept is I want to go to do this:
```
quee@squee-laptop:~/Projects/rnd$ mplayer -fs `lsrnd ~/Videos`
```

lsrnd output: 
```
squee@squee-laptop:~/Projects/lsrnd$ lsrnd ~/Videos
/home/squee/Videos/AMV\ Hell\ 4\ \-\ The\ Last\ One.mp4 /home/squee/Videos/AMV\ Hell\ 3\ \-\ The\ Motion\ Picture.avi 
```

lsrnd --help
```
Usage: lsrnd [OPTIONS]... <directories> ...
A program to randomly pick files in the directories specified or in your current working directory
  -d,	--delimiter	enter a custom delimiter [space]
  -m,	--max-list-size	set a maximum number of files to print
  -r,	--recursive	traverse directories
  -w,	--with-hidden	uinclude hidden files and folders
        --help		display this help and exit
        --version	displays version information and exit

```

It works fine with normal files, but here is my issue.  I can't figure out how to escape spaces correctly.  When I give mplayer the string above, I get this: 
```
squee@squee-laptop:~/Projects/rnd$ mplayer -fs `lsrnd ~/Videos`
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/squee/Videos/AMV\.
File not found: '/home/squee/Videos/AMV\'
Failed to open /home/squee/Videos/AMV\.


Playing Hell\.
File not found: 'Hell\'
Failed to open Hell\.


Playing 3\.
File not found: '3\'
Failed to open 3\.


Playing \-\.
File not found: '\-\'
Failed to open \-\.


Playing The\.
File not found: 'The\'
Failed to open The\.


Playing Motion\.
File not found: 'Motion\'
Failed to open Motion\.


Playing Picture.avi.
File not found: 'Picture.avi'
Failed to open Picture.avi.


Playing /home/squee/Videos/AMV\.
File not found: '/home/squee/Videos/AMV\'
Failed to open /home/squee/Videos/AMV\.


Playing Hell\.
File not found: 'Hell\'
Failed to open Hell\.


Playing 4\.
File not found: '4\'
Failed to open 4\.


Playing \-\.
File not found: '\-\'
Failed to open \-\.


Playing The\.
File not found: 'The\'
Failed to open The\.


Playing Last\.
File not found: 'Last\'
Failed to open Last\.


Playing One.mp4.
File not found: 'One.mp4'
Failed to open One.mp4.


Exiting... (End of file)

```

I've tried quoting the entire string, it makes mplayer not recognize any of the files (including ones without spaces).  I'm currently using '\ ' in place of spaces, and mplayer still receives it as separate file names.  Does anyone have any idea how to resolve this issue?  I can't belive there isn't a way to escape this correctly.

Thank you everyone for your help.

also,

---

### Post by geirha on 2008-05-22
Quote the output of your command
```

mplayer -fs "`rnd -r -d /multimedia`"
            ^                       ^

```

EDIT: Oh, wait, rnd may return more than one file?
Try with xargs then:
```

rnd -r -d /multimedia | xargs -d$'\n' -- mplayer -fs

```

This is still not 100% safe, since filenames may contain '\n'. The safest is to append a \0 behind each file, and then use xargs -0 mplayer ...

---

### Post by panayk on 2008-05-22
Try this patch. In short:

I changed how replace_str gets called:

```
for(i = 0; i < file_list.size; i++)
{
    /* The original pointer may be invalid, due to the call to realloc */
    file_list.filename[i] = replace_str(file_list.filename[i], " ", "\\ ");
    printf("%s\n", file_list.filename[i]);
    free(file_list.filename[i]);
}

```

Then:

```
char *replace_str(char *string, char *original, char *replace)
{
    /* some useful constants */
    const int original_length = strlen(original),
              replace_length = strlen(replace),
              diff = replace_length - original_length;

    /* The first character we haven't processed yet. 
     * This is where we start searching for matches
     */
    char *ptr = string;

    while ((ptr = strstr(ptr, original)) != NULL)
    {
            /* split the string into:
             * prefix : 0 ... ptr-1
             * the match : ptr ... ptr+original_length-1
             * suffix : ptr+original_length ... <end-of-string>
             */
            char *suffix = NULL;
            suffix = malloc(sizeof(char) * (strlen(ptr) - original_length + 1));
            strcpy(suffix, ptr + original_length);

            /* make/free space */
			int new_size = 0;
            new_size = strlen(string) + 1 + diff;

            /* ptr may have been invalidated, so we have to update it */
            /* TODO: Is this kind of cast good practise? Is there a better way? */
            int pos = ptr - string;
            string = realloc(string, new_size);
            ptr = string + pos;

            /* do the replacement */
            strcpy(ptr, replace);

            /* we will continue searching from here */
            ptr += replace_length;

            /* add the suffix */
            strcpy(ptr, suffix);
            free(suffix);            
    }

    /* IMPORTANT: This may or may not be the original pointer, because of realloc */
    return string;
}

```

Strange that quoting doesn't work though.

EDIT:
OOPS, this doesn't work after all, better go with xargs.

---

### Post by sq377 on 2008-05-23
Thanks for the patch panak.  I applied it and made a few changes.

geirha: Thanks, that was exactly what I needed to get it to work, but I still can't believe that there isn't a way to escape it correctly through code.

---

