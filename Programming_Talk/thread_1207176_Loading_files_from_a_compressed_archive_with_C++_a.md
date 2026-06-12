---
title: "Loading files from a compressed archive with C++ and SDL"
date: 2009-07-07
forum: Programming Talk
---

### Post by Nuticulus on 2009-07-07
Hi,

I am writing a SDL game at the moment and I'm looking for a way to load images and sounds from a compressed archive and display / play them using SDL_RWops.
I don't really mind what format the compressed archive is in, just as long as it's easy to edit the contents of the archive.

Does anyone know how to do this?

---

### Post by TheBuzzSaw on 2009-07-07
I think zlib might have what you're looking for... unless I'm way off on what zlib actually does.

---

### Post by JordyD on 2009-07-07
Is this what you're looking for: [http://www.kekkai.org/roger/sdl/rwops/rwops.html]("http://www.kekkai.org/roger/sdl/rwops/rwops.html")?

---

### Post by Nuticulus on 2009-07-08
I'm pretty sure zlib can't do this sort of thing, but I'm not absolutely certain.
I had a look at [http://www.kekkai.org/roger/sdl/rwops/rwops.html](http://www.kekkai.org/roger/sdl/rwops/rwops.html), but unfortunately it only covers .gz archives, which as far as I know can only hold one file...

Edit: I'm an idiot. The solution was on [http://www.kekkai.org/roger/sdl/rwops/rwops.html](http://www.kekkai.org/roger/sdl/rwops/rwops.html), and I didn't see it! :p Grrr...

Anyway, I got it working! Thanks JordyD! ):P

---

### Post by Nuticulus on 2009-07-09
Ok, Now I have a new problem. Here is my code for loading an image from a zip file:

```
#ifndef loadImage
#define loadImage

#include "SDL/SDL.h"
#include "SDL_rwops_zzip.h"
#include "zzip.h"
#include "iostream"
#include "string"

SDL_Surface *loadImage(char* zipFileName, char* imageName, int fileSize);

SDL_Surface *loadImage(char* zipFileName, char* imageName, int fileSize)
{
    SDL_Surface *NewImage;
    SDL_RWops *rw;
    ZZIP_FILE *file;
    Uint8 *buffer;
    buffer = (Uint8*)malloc(fileSize);
    int filesize;

    std::string strZipFile = zipFileName;
    std::string strImgName = imageName;
    std::string strArg = strZipFile + '/' + strImgName;

    file = zzip_open(strArg.c_str(), 0);
    if(file==NULL)
    {
        std::cout << "Unable to load image \'" << imageName << "\' from archive \'" << zipFileName << "\'.\n";
        return NULL;
    }
    filesize = zzip_read(file, buffer, fileSize);
    rw = SDL_RWFromMem(buffer, filesize);
    NewImage = IMG_Load_RW(rw, 0);

    free(buffer);
    SDL_FreeRW(rw);
    zzip_close(file);

    return NewImage;
}

#endif
```

Right now, you have to pass the size of the uncompressed image in order to allocate memory for a buffer.
Is there any way to load the size of the image from the zip file using zZipLib?

---

### Post by JordyD on 2009-07-09
> **Nuticulus said:**
> Ok, Now I have a new problem. Here is my code for loading an image from a zip file:

```
#ifndef loadImage
#define loadImage

#include "SDL/SDL.h"
#include "SDL_rwops_zzip.h"
#include "zzip.h"
#include "iostream"
#include "string"

SDL_Surface *loadImage(char* zipFileName, char* imageName, int fileSize);

SDL_Surface *loadImage(char* zipFileName, char* imageName, int fileSize)
{
    SDL_Surface *NewImage;
    SDL_RWops *rw;
    ZZIP_FILE *file;
    Uint8 *buffer;
    buffer = (Uint8*)malloc(fileSize);
    int filesize;

    std::string strZipFile = zipFileName;
    std::string strImgName = imageName;
    std::string strArg = strZipFile + '/' + strImgName;

    file = zzip_open(strArg.c_str(), 0);
    if(file==NULL)
    {
        std::cout << "Unable to load image \'" << imageName << "\' from archive \'" << zipFileName << "\'.\n";
        return NULL;
    }
    filesize = zzip_read(file, buffer, fileSize);
    rw = SDL_RWFromMem(buffer, filesize);
    NewImage = IMG_Load_RW(rw, 0);

    free(buffer);
    SDL_FreeRW(rw);
    zzip_close(file);

    return NewImage;
}

#endif
```

Right now, you have to pass the size of the uncompressed image in order to allocate memory for a buffer.
Is there any way to load the size of the image from the zip file using zZipLib?
I do not use zZipLib, but these functions may be what you're looking for: [zZipLib Library Functions]("http://zziplib.sourceforge.net/zziplib.html#zzip_dir_stat"). The zzip_file_stat or zzip_fstat functions look like what you may be talking about.

---

### Post by Nuticulus on 2009-07-09
Ok, I seem to have messed up my build options. It now comes out with this error:
```
SDL_rwops_zzip.c|63|error: lvalue required as left operand of assignment
```
Does anyone know what the necessary build options are? I'm using the Code::Blocks IDE.

Here is the code for SDL_rwops_zzip.c:
```
/*
 *      Copyright (c) 2001 Guido Draheim <guidod@gmx.de>
 *      Use freely under the restrictions of the ZLIB License
 */

#include "SDL_rwops_zzip.h"
#include <zziplib.h>

#define SDL_RWOPS_ZZIP_FILE(_context) \
             ((ZZIP_FILE*) (_context)->hidden.unknown.data1)

static int _zzip_seek(SDL_RWops *context, int offset, int whence)
{
    return zzip_seek(SDL_RWOPS_ZZIP_FILE(context), offset, whence);
}

static int _zzip_read(SDL_RWops *context, void *ptr, int size, int maxnum)
{
    return zzip_read(SDL_RWOPS_ZZIP_FILE(context), ptr, size*maxnum);
}

static int _zzip_write(SDL_RWops *context, const void *ptr, int size, int num)
{
    return 0; /* ignored */
}

static int _zzip_close(SDL_RWops *context)
{
    zzip_close (SDL_RWOPS_ZZIP_FILE(context));

    if ( context )
	SDL_FreeRW (context);

    return 0;
}

#ifndef O_BINARY
#define O_BINARY 0
#endif

SDL_RWops *SDL_RWFromZZIP(const char* file, const char* mode)
{
    register int mo = 0;
    register SDL_RWops* rwops;
    register ZZIP_FILE* zzip_file;

    for (; *mode; ++mode)
	switch (*mode)
	{
	case 'r': mo |= O_RDONLY;  break;
	case '+': mo |= ZZIP_CASEINSENSITIVE; break; /* == O_APPEND */
	case 'b': mo |= O_BINARY; break;
	case 'w': /* ouch! */  return 0;
	    /* default, 't', 'a', etc, just ignore */
	}

    zzip_file = zzip_open (file, mo);
    if (! zzip_file) return 0;

    rwops = SDL_AllocRW ();
    if (! rwops) { zzip_close (zzip_file); return 0; }

    SDL_RWOPS_ZZIP_FILE(rwops) = zzip_file;
    rwops->read = _zzip_read;
    rwops->write = _zzip_write;
    rwops->seek = _zzip_seek;
    rwops->close = _zzip_close;
    return rwops;
}
```

---

