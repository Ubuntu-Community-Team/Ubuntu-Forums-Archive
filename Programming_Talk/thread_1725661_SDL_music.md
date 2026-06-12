---
title: "SDL music"
date: 2011-04-10
forum: Programming Talk
---

### Post by qw3rty_rocks on 2011-04-10
I was hoping to be able to make a system in SDL that was able to get the contents of a directory (music) and be able to choose a random file and play it. So far things haven't gone to plan so does anyone have an idea on how i could do this?

---

### Post by slavik on 2011-04-10
use gstreamer instead

---

### Post by qw3rty_rocks on 2011-04-10
Well I had already got music working already and i don't really want to switch to gstreamer but I want to be able to, lets say, allow the user to drop music in a folder and the program will play whatever is in there automatically. I don't know how to do this.
I'm using sdl because i'm making a game.

---

### Post by Phenax on 2011-04-10
What's the problem? Just use SDL_Mixer and something like the gcc-provided dirent.h for going through directories (If you're using C/C++).

---

### Post by qw3rty_rocks on 2011-04-10
Yeah well lets say i was having trouble with dirent.h

---

### Post by Phenax on 2011-04-10
> **qw3rty_rocks said:**
> Yeah well lets say i was having trouble with dirent.h

What's your problem? [Wikipedia]("http://en.wikipedia.org/wiki/Dirent.h#Example") has a good example.

---

### Post by qw3rty_rocks on 2011-04-10
Well i kind of get it but how would i convert the output to work with Mix_LoadMUS();

---

### Post by Phenax on 2011-04-10
Kind of messy, and doesn't handle errors gracefully. Nor does it handle all possible errors. But should give you the general idea. The output of getRandomMusicName(char *path); should be compatible with Mix_LoadMUS. This is C code btw. You'll need to include cstring, cstdlib, ctime instead of what I have if you're using C++.

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <dirent.h>
#include <time.h>

int isMusicFile(char *filename);
char *getRandomMusicName(char *path);

int isMusicFile(char *filename)
{
    char extension[4];
    strncpy(extension, filename + strlen(filename) - 3, 4);
    if(strncmp(extension, "mp3", 3) == 0)
        return 1;
    else if(strncmp(extension, "ogg", 3) == 0)
        return 1;
    else if(strncmp(extension, "lac", 3) == 0) //for flac, because im lazy
        return 1;

    return 0;
}

char *getRandomMusicName(char *path)
{
    int i = 0;
    char file_names[256][256];

    DIR *dp;    
    struct dirent *entry;
    
    dp = opendir(path);
    
    if(dp == NULL)
        perror("opendir");
    
    while((entry = readdir(dp)))
    {
        if(isMusicFile(entry->d_name))
        {
            strncpy(file_names[i], entry->d_name, 256);
            i++;
        }
    }

    closedir(dp);

    if(i == 0)
        exit(EXIT_FAILURE); //add your own error handling

    //strdup duplicates our string.
    //automatic variable are gone from memory
    //after the function ends. We need to free this later.
    return strdup(file_names[rand() % i]);
}

int main(void)
{
    srand(time(NULL));

    char *x = getRandomMusicName(".");
    if(x == NULL) //our strdup didn't work. insufficient memory, etc.
        exit(EXIT_FAILURE);

    printf("%s", x);
    free(x); //you have to free if you strdup.
    return 0;
}

```

---

### Post by qw3rty_rocks on 2011-04-11
Ok it works, but I want to be able to specify a directory other than the current directory. so lets say a directory "/data/music". I can read the contents of that directory fine. The problem is that when I pass it to Mix_LoadMUS it only gets the name of the file not the directory. How would I fix this?

---

### Post by Phenax on 2011-04-11
So make a (char *) that points to a string containing your path (like char *path = "/data/music/"). Pass that to getRandomMusicName function and set the result to a variable like in the example. Then use something like strncat to concatenate your path and your filename to make a new string that is the full path like "/data/music/file.mp3".

---

### Post by qw3rty_rocks on 2011-04-11
Ok thats what I do but it gives me segmentation fault. Here is the modified code:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <dirent.h>
#include <time.h>

int isMusicFile(char *filename);
char *getRandomMusicName(char *path);

int isMusicFile(char *filename)
{
    char extension[4];
    strncpy(extension, filename + strlen(filename) - 3, 4);
    if(strncmp(extension, "mp3", 3) == 0)
        return 1;
    else if(strncmp(extension, "ogg", 3) == 0)
        return 1;
    else if(strncmp(extension, "lac", 3) == 0) //for flac, because im lazy
        return 1;

    return 0;
}

char *getRandomMusicName(char *path)
{
    int i = 0;
    char file_names[256][256];

    DIR *dp;    
    struct dirent *entry;
    
    dp = opendir(path);
    
    if(dp == NULL)
        perror("opendir");
    
    while((entry = readdir(dp)))
    {
        if(isMusicFile(entry->d_name))
        {
            strncpy(file_names[i],path, 256);
            i++;
        }
    }

    closedir(dp);

    if(i == 0)
        exit(EXIT_FAILURE); //add your own error handling

    //strdup duplicates our string.
    //automatic variable are gone from memory
    //after the function ends. We need to free this later.
    return strdup(file_names[rand() % i]);
}

int main(void)
{
    srand(time(NULL));

    char* x = getRandomMusicName("./data/music/");
    if(x == NULL) //our strdup didn't work. insufficient memory, etc.
        exit(EXIT_FAILURE);
    char* path = "./data/music/";
    strncat(path, x, 300);

    printf("%s", x);
    printf("%s", "\n\n");
    free(x); //you have to free if you strdup.
    return 0;
}
```

---

### Post by fct on 2011-04-11
You haven't posted where the segfault happens (use gdb) but it might be this:

```
char* path = "./data/music/";
strncat(path, x, 300);
```

---

### Post by Phenax on 2011-04-11
> **fct said:**
> You haven't posted where the segfault happens (use gdb) but it might be this:

```
char* path = "./data/music/";
strncat(path, x, 300);
```

Indeed.

When you do
```

char *path = "./data/music";

```You cannot actually modify the string that path points to. It allocates a string that contains "./data/music" on the stack, usually it's read-only memory, which is why you get a segmentation fault. Either way, it'd be undefined to do such a thing.
C needs to know the size of things.

Doing
```

char path[] = "./data/music";

```Will give you a modifiable string, meaning you could do something like path[2] = 'b', which would be undefined behavior with the above example, but all this is doing is really becoming
```

char path[13] = "./data/music";

```As "./data/music" is 12 characters long + 1 character for null terminator '\0'
Proof:
```

#include <stdio.h>

int main(void)
{
    char path[] = "./data/music";
    printf("%d", sizeof(path)); //a char is ALWAYS 1 byte in C
    return 0;
}

```Thus you will need to explicitly make path, or a new variable, large enough to hold the path as well as your filename that you will append to it.

---

### Post by qw3rty_rocks on 2011-04-11
IT WORKS!!!!!!!!!!!!!!!!!!!!!!
Yay
Thank you so much you guys.

---

