---
title: "Allocate multi-dimensional array in run-time, in C?"
date: 2009-01-24
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-24
How? I keep getting segfaults, NULL pointers, and pointless error messages.

```

    unsigned char **tiles;
    int w = 10;
    int h = 10;

    tiles = malloc( sizeof(unsigned char) * h * w);
    
    if ( not tiles )
        return 0;
    
    int y;
    for(y=0; y<h; y++)
    {
        tiles[y] = malloc(sizeof(unsigned char)*w);
        memset( tiles[y], 0, w );
    }

```

---

### Post by nvteighen on 2009-01-24
It's much easier than you think.

```

#include <stdlib.h> /* Or just malloc.h... */

int main(void)
{
    /* We'll allocate a 12x45 array of integers */
    int rows = 12;
    int cols = 45;

    int **array = (int **)malloc(rows * sizeof(int *));

    if(array == NULL)
        return 1;

    int i;
    for(i = 0; i < rows; i++)
    {
        array[i] = (int *)malloc(cols * sizeof(int));
        
        if(array[i] == NULL) 
        {
            /* Ok, this should be changed depending on what you're
             * doing. Usually, here I'd call the deallocation function so we
             * have either errorless arrays or nothing. */

            continue;
        }
            
    }

    /* Do stuff
     * ...
     * ... */


    /* Now, we free the memory... I'll reuse 'i' */
    for(i = 0; i < rows; i++)
    {
        if(array[i] != NULL) /* Otherwise we segfault */
            free(array[i]);
    }

    free(array);

    return 0;
}

```

Anyway, you see I'm never initializing memory... I always use calloc() because it automatically memsets to zero. And usually, the best would be to create separate functions: an allocating one that returns a pointer to the memory and a deallocating one...

---

### Post by crazyfuturamanoob on 2009-02-13
> **nvteighen said:**
> 
```

    /* Now, we free the memory... I'll reuse 'i' */
    for(i = 0; i < rows; i++)
    {
        if(array[i] != NULL) /* Otherwise we segfault */
            free(array[i]);
    }

    free(array);

    return 0;
}

```

That doesn't seem to work. 

I'm building my tile-based game engine, and map freeing function causes this:
```

*** glibc detected *** ./output: malloc(): memory corruption (fast): 0x0000000000ec2f70 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fd960c7ba58]
/lib/libc.so.6[0x7fd960c7f181]
/lib/libc.so.6(__libc_malloc+0x98)[0x7fd960c80658]
/usr/lib/libxcb.so.1[0x7fd95cbf1011]
/usr/lib/libxcb.so.1[0x7fd95cbef3ba]
/usr/lib/libxcb.so.1(xcb_wait_for_reply+0x15d)[0x7fd95cbf0bdd]
/usr/lib/libX11.so.6(_XReply+0x15e)[0x7fd95e4bf58e]
/usr/lib/libX11.so.6(XQueryPointer+0x8f)[0x7fd95e4acb4f]
/usr/lib/libSDL-1.2.so.0[0x7fd961d40e5b]
/usr/lib/libSDL-1.2.so.0[0x7fd961d41817]
/usr/lib/libSDL-1.2.so.0[0x7fd961d420fb]
/usr/lib/libSDL-1.2.so.0(SDL_PumpEvents+0x30)[0x7fd961d15f90]
/usr/lib/libSDL-1.2.so.0(SDL_PollEvent+0x9)[0x7fd961d163d9]
./output[0x401baf]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fd960c20466]
./output[0x4017e9]
======= Memory map: ========
00400000-00405000 r-xp 00000000 08:01 3369172                            /home/arho/Projects/C/tds3d/output
00604000-00605000 rw-p 00004000 08:01 3369172                            /home/arho/Projects/C/tds3d/output
00c9b000-00ee4000 rw-p 00c9b000 00:00 0                                  [heap]
40cdc000-40cde000 rwxp 00000000 00:0e 694                                /dev/zero
41e7a000-41edd000 rw-p 00000000 00:0e 694                                /dev/zero
7fd950000000-7fd950021000 rw-p 7fd950000000 00:00 0 
7fd950021000-7fd954000000 ---p 7fd950021000 00:00 0 
7fd955f3d000-7fd95613d000 rw-s bb1a5000 00:0e 16955                      /dev/nvidia0
7fd95613d000-7fd95623d000 rw-s bf951000 00:0e 16955                      /dev/nvidia0
7fd95623d000-7fd95627d000 rw-s be0d8000 00:0e 16955                      /dev/nvidia0
7fd95627d000-7fd95629d000 rw-s be446000 00:0e 16955                      /dev/nvidia0
7fd95629d000-7fd9562dd000 rw-p 7fd95629d000 00:00 0 
7fd9562dd000-7fd9562fe000 rw-s 00000000 00:09 0                          /SYSV00000000 (deleted)
7fd9562fe000-7fd9578ce000 rw-p 7fd9562fe000 00:00 0 
7fd9578cf000-7fd957e1f000 rw-p 7fd9578cf000 00:00 0 
7fd957e20000-7fd957f40000 rw-p 7fd957e20000 00:00 0 
7fd957f40000-7fd957f45000 r-xp 00000000 08:01 14019177                   /usr/lib/libXfixes.so.3.1.0
7fd957f45000-7fd958144000 ---p 00005000 08:01 14019177                   /usr/lib/libXfixes.so.3.1.0
7fd958144000-7fd958145000 rw-p 00004000 08:01 14019177                   /usr/lib/libXfixes.so.3.1.0
7fd958145000-7fd95814e000 r-xp 00000000 08:01 14019167                   /usr/lib/libXcursor.so.1.0.2
7fd95814e000-7fd95834e000 ---p 00009000 08:01 14019167                   /usr/lib/libXcursor.so.1.0.2
7fd95834e000-7fd95834f000 rw-p 00009000 08:01 14019167                   /usr/lib/libXcursor.so.1.0.2
7fd95835a000-7fd95837a000 rw-p 7fd95835a000 00:00 0 
7fd95837a000-7fd9583c7000 rw-p 7fd9583f7000 00:00 0 
7fd9583c7000-7fd9583f7000 rw-p 7fd9583c7000 00:00 0 
7fd9583fb000-7fd9592eb000 rw-p 7fd9583fb000 00:00 0 
7fd9592ec000-7fd959307000 rw-p 7fd9592ec000 00:00 0 
7fd959311000-7fd95a291000 rw-p 7fd959311000 00:00 0 
7fd95a292000-7fd95a2b2000 rw-p 7fd95a292000 00:00 0 
7fd95a2b3000-7fd95a303000 rw-p 7fd95a2b3000 00:00 0 
7fd95a303000-7fd95a342000 r--p 00000000 08:01 14050734                   /usr/lib/locale/en_US.utf8/LC_CTYPE
7fd95a342000-7fd95a343000 r--p 00000000 08:01 14050739                   /usr/lib/locale/en_US.utf8/LC_NUMERIC
7fd95a343000-7fd95a344000 r--p 00000000 08:01 14050742                   /usr/lib/locale/en_US.utf8/LC_TIME
7fd95a344000-7fd95a425000 r--p 00000000 08:01 14050733                   /usr/lib/locale/en_US.utf8/LC_COLLATE
7fd95a425000-7fd95a426000 r--p 00000000 08:01 14050737                   /usr/lib/locale/en_US.utf8/LC_MONETARY
7fd95a426000-7fd95a427000 r--p 00000000 08:01 14050743                   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
7fd95a427000-7fd95a428000 r--p 00000000 08:01 14050740                   /usr/lib/locale/en_US.utf8/LC_PAPER
7fd95a428000-7fd95a429000 r--p 00000000 08:01 14050738                   /usr/lib/locale/en_US.utf8/LC_NAME
7fd95a429000-7fd95a42a000 r--p 00000000 08:01 14050732                   /usr/lib/locale/en_US.utf8/LC_ADDRESS
7fd95a42a000-7fd95a42b000 r--p 00000000 08:01 14050741                   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
7fd95a42b000-7fd95a42c000 r--p 00000000 08:01 14050736                   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
7fd95a42c000-7fd95a433000 r--s 00000000 08:01 14033526                   /usr/lib/gconv/gconv-modules.cache
7fd95a433000-7fd95a434000 r--p 00000000 08:01 14050735                   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
7fd95a434000-7fd95a804000 rw-p 7fd95a434000 00:00 0 
7fd95a805000-7fd95ae25000 rw-p 7fd95a805000 00:00 0 
7fd95ae26000-7fd95ae56000 rw-p 7fd95ae26000 00:00 0 
7fd95ae57000-7fd95c2b7000 rw-p 7fd95ae57000 00:00 0 
7fd95c2b7000-7fd95c2be000 r-xp 00000000 08:01 14019195                   /usr/lib/libXrandr.so.2.1.0
7fd95c2be000-7fd95c4bd000 ---p 00007000 08:01 14019195                   /usr/lib/libXrandr.so.2.1.0
7fd95c4bd000-7fd95c4be000 r--p 00006000 08:01 14019195                   /usr/lib/libXrandr.so.2.1.0
7fd95c4be000-7fd95c4bf000 rw-p 00007000 08:01 14019195                   /usr/lib/libXrandr.so.2.1.0
7fd95c4bf000-7fd95c5cf000 rw-p 7fd95c4bf000 00:00 0 
7fd95c5d8000-7fd95c5dc000 rw-s bf485000 00:0e 16955                      /dev/nvidia0
7fd95c5dc000-7fd95c7bc000 rw-p 7fd95c5dc000 00:00 0 
7fd95c7bc000-7fd95c7c5000 r-xp 00000000 08:01 14019197                   /usr/lib/libXrender.so.1.3.0
7fd95c7c5000-7fd95c9c4000 ---p 00009000 08:01 14019197                   /usr/lib/libXrender.so.1.3.0
7fd95c9c4000-7fd95c9c5000 r--p 00008000 08:01 14019197                   /usr/lib/libXrender.so.1.3.0
7fd95c9c5000-7fd95c9c6000 rw-p 00009000 08:01 14019197                   /usr/lib/libXrender.so.1.3.0
7fd95c9c7000-7fd95c9cb000 rw-s bf93e000 00:0e 16955                      /dev/nvidia0
7fd95c9cb000-7fd95c9cc000 rw-s c0e20000 00:0e 16955                      /dev/nvidia0
7fd95c9cc000-7fd95c9cd000 rw-s ad5ca000 00:0e 16955                      /dev/nvidia0
7fd95c9cd000-7fd95c9ce000 rw-s bb065000 00:0e 16955                      /dev/nvidia0
7fd95c9ce000-7fd95c9cf000 rw-s d1c06000 00:0e 16955                      /dev/nvidia0
7fd95c9cf000-7fd95c9d0000 rw-s d1641000 00:0e 16955                      /dev/nvidia0
7fd95c9d0000-7fd95c9d1000 rw-s 109f5d000 00:0e 16955                     /dev/nvidia0
7fd95c9d1000-7fd95c9e1000 rw-p 7fd95c9d1000 00:00 0 
7fd95c9e1000-7fd95c9e6000 r-xp 00000000 08:01 14019171                   /usr/lib/libXdmcp.so.6.0.0
7fd95c9e6000-7fd95cbe5000 ---p 00005000 08:01 14019171                   /usr/lib/libXdmcp.so.6.0.0
7fd95cbe5000-7fd95cbe6000 rw-p 00004000 08:01 14019171                   /usr/lib/libXdmcp.so.6.0.0
7fd95cbe6000-7fd95cc01000 r-xp 00000000 08:01 14020104                   /usr/lib/libxcb.so.1.0.0
7fd95cc01000-7fd95ce00000 ---p 0001b000 08:01 14020104                   /usr/lib/libxcb.so.1.0.0
7fd95ce00000-7fd95ce01000 r--p 0001a000 08:01 14020104                   /usr/lib/libxcb.so.1.0.0
7fd95ce01000-7fd95ce02000 rw-p 0001b000 08:01 14020104                   /usr/lib/libxcb.so.1.0.0
7fd95ce02000-7fd95ce03000 r-xp 00000000 08:01 14020102                   /usr/lib/libxcb-xlib.so.0.0.0
7fd95ce03000-7fd95d002000 ---p 00001000 08:01 14020102                   /usr/lib/libxcb-xlib.so.0.0.0
7fd95d002000-7fd95d003000 r--p 00000000 08:01 14020102                   /usr/lib/libxcb-xlib.so.0.0.0
7fd95d003000-7fd95d004000 rw-p 00001000 08:01 14020102                   /usr/lib/libxcb-xlib.so.0.0.0
7fd95d004000-7fd95d006000 r-xp 00000000 08:01 14019160                   /usr/lib/libXau.so.6.0.0
7fd95d006000-7fd95d205000 ---p 00002000 08:01 14019160                   /usr/lib/libXau.so.6.0.0
7fd95d205000-7fd95d206000 rw-p 00001000 08:01 14019160                   /usr/lib/libXau.so.6.0.0
7fd95d206000-7fd95d20e000 r-xp 00000000 08:01 17211523                   /lib/librt-2.8.90.so
7fd95d20e000-7fd95d40d000 ---p 00008000 08:01 17211523                   /lib/librt-2.8.90.so
7fd95d40d000-7fd95d40e000 r--p 00007000 08:01 17211523                   /lib/librt-2.8.90.so
7fd95d40e000-7fd95d40f000 rw-p 00008000 08:01 17211523                   /lib/librt-2.8.90.so
7fd95d40f000-7fd95d48d000 r-xp 00000000 08:01 14019431                   /usr/lib/libfreetype.so.6.3.18
7fd95d48d000-7fd95d68d000 ---p 0007e000 08:01 14019431                   /usr/lib/libfreetype.so.6.3.18
7fd95d68d000-7fd95d692000 r--p 0007e000 08:01 14019431                   /usr/lib/libfreetype.so.6.3.18
7fd95d692000-7fd95d693000 rw-p 00083000 08:01 14019431                   /usr/lib/libfreetype.so.6.3.18
7fd95d693000-7fd95d6aa000 r-xp 00000000 08:01 14020116                   /usr/lib/libz.so.1.2.3.3
7fd95d6aa000-7fd95d8a9000 ---p 00017000 08:01 14020116                   /usr/lib/libz.so.1.2.3.3
7fd95d8a9000-7fd95d8ab000 rw-p 00016000 08:01 14020116                   /usr/lib/libz.so.1.2.3.3
7fd95d8ab000-7fd95d903000 r-xp 00000000 08:01 14020039                   /usr/Aborted

```

Valgrind says it's this line:
```

free(array)

```
Or the equivalent in my program:
```

void map_Free( struct mapData *map )
{
    if ( !map || !map->tiles )
        return;
    
    int i;
    for( i=0; i<map->height; i++ )
    {
        if ( map->tiles[i] != NULL )
            free( map->tiles[i] );
    }
    
    **free( map->tiles );**
}

```
What am I missing?

---

### Post by sujoy on 2009-02-13
i dont know how you allocated the memory, but
free( map->tiles[i] );
already frees the memory map->tiles[0] and map->tiles essentially points to the same thing. so you are trying to free an already freed memory as far as i can tell

---

### Post by nvteighen on 2009-02-13
> **crazyfuturamanoob said:**
> That doesn't seem to work. 

(...)

Valgrind says it's this line:
```

free(array)

```
Or the equivalent in my program:
```

void map_Free( struct mapData *map )
{
    if ( !map || !map->tiles )
        return;
    
    int i;
    for( i=0; i<map->height; i++ )
    {
        if ( map->tiles[i] != NULL )
            free( map->tiles[i] );
    }
    
    **free( map->tiles );**
}

```
What am I missing?

Sorry, I made a fatal mistake there, possibly confusing array with a malloc()'ed struct or who knows what the hell... Yes, sujoy is right, free(array) is not needed, as the for-loop releases all memory.

---

### Post by doojsdad on 2009-02-13
> **crazyfuturamanoob said:**
> How? I keep getting segfaults, NULL pointers, and pointless error messages.

```

    unsigned char **tiles;
    int w = 10;
    int h = 10;

    tiles = malloc( sizeof(unsigned char) * h * w);
    
    if ( not tiles )
        return 0;
    
    int y;
    for(y=0; y<h; y++)
    {
        tiles[y] = malloc(sizeof(unsigned char)*w);
        memset( tiles[y], 0, w );
    }

```

Because tiles is an array of pointers (which I'm assuming are 32 bits for you), you need to malloc in portions of pointers to unsigned chars not unsigned chars themselves. ie

```
tiles = malloc( sizeof(unsigned char) * h * w);
```

should be:

```
tiles = malloc( sizeof(unsigned char *****) * h);
```

When you access tiles[y] further than.. wait I just realized that this might work for you by pure coincidence because you allocate h*w*1byte which I guess might work for you, but it's by accident. Sorry kind of thinking out loud.

---

### Post by geirha on 2009-02-13
I prefer to use 1d arrays for representing matrices.
```

int main(void)
{
    unsigned char *tiles;
    int w= 5, h= 5;
    int i= 0;
    
    tiles= malloc( sizeof(unsigned char)*w*h );
    memset(tiles, 0xff, w*h);
    
    tiles[3*w+0]= 0;  // set row 3, column 0 to 0;
    
    while( i < w*h )
    {
        printf("%02x ", tiles[i]);
        if ( ++i%w == 0)
            putchar('\n');
    }
    free(tiles);
    return 0;
}

```

Not as intuitive to access the values with tiles[row*width+column] instead of tiles[row][column], but less hassle; one malloc, one free.

---

### Post by dwhitney67 on 2009-02-13
> **sujoy said:**
> i dont know how you allocated the memory, but
free( map->tiles[i] );
already frees the memory map->tiles[0] and map->tiles essentially points to the same thing. so you are trying to free an already freed memory as far as i can tell

Nope, not true.  In the little program shown below, tiles and tiles[0] do _not_ point to the same thing.

```

#include <stdlib.h>
#include <stdio.h>

int main()
{
  const int rows = 10;
  const int cols = 20;

  int** tiles = malloc(rows * sizeof(int*));

  for (int i = 0; i < rows; ++i)
  {
    tiles[i] = malloc(cols * sizeof(int));
  }

  for (int i = 0; i < rows; ++i)
  {
    free(tiles[i]);
  }

  // Comment out the line below, and valgrind will correctly
  // report that 40 bytes are not freed by the application.
  // Leave it in, and all is kosher.
  // Btw, 40 bytes = rows * sizeof(int*)
  free(tiles);
}

```

---

