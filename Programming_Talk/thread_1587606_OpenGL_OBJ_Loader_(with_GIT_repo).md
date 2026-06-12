---
title: "OpenGL: OBJ Loader (with GIT repo)"
date: 2010-10-03
forum: Programming Talk
---

### Post by nfm on 2010-10-03
Hey guys,
So I'm tired of searching for OBJ Loader and decided to code my own. I found some obj loader while ago and it have been sitting on my hdd, I'm in process of resurrecting it and I'm looking for help.

I would like community to help me so I could **update** the repo with changes so all of us could **benefit** from this. If you decide to write a patch PM or e-mail me, or simply reply to the thread.

**Repository:** it will down during night since it's where I sleep
```
git clone git://git.kkaminsk.com/OBJLoader.git
```

**File:** initial version - OBJLoader_rev0.tar.bz2
[https://docs.google.com/leaf?id=0B9OPEm2FC7s9N2RmOTgyNzgtZmY0MC00YTJlLWI2NTItMmY3Njc1MmQ4Y2Iw&hl=en](https://docs.google.com/leaf?id=0B9OPEm2FC7s9N2RmOTgyNzgtZmY0MC00YTJlLWI2NTItMmY3Njc1MmQ4Y2Iw&hl=en)

**Includes:** Makefile, SDL window, function for reading .TGA (targa) files, and processes keys. So far this is what we got:
[IMG]http://img651.imageshack.us/img651/5099/objloader.png[/IMG]

**So what needs to be implemented?**
Very little, I would do it myself but I forgot how to exactly load textures, I'm slowly rereading my GL book.
**objloader.c: line 194: **At this spot everything is done for us, we need to traverse the arrays and call functions such glTexImage2D() etc. to setup the textures.

Thanks :KS

---

### Post by Sockerdrickan on 2010-10-04
Loading OBJ models to data structures isn't even related to OpenGL.

Check this out for more information on the format [http://en.wikipedia.org/wiki/Obj](http://en.wikipedia.org/wiki/Obj)

Load OBJ to a data structure as your first step. Then get to the rendering.

---

### Post by nfm on 2010-10-16
I made some progress.

[IMG]http://img521.imageshack.us/img521/5099/objloader.png[/IMG]

Not the real issue is that the loader is restricted to only loading a quad, for example, it only accepts following format for a face/polygon:
```
f 16/8/6 15/6/6 47/5/6 43/7/6 
```
If anything else is in the .obj file, funky or bad stuff will happen

```
        /* quad */
        else if (memcmp(p, "f", 1) == 0) /* or *p == 'f' */
        {
            nread = sscanf(p, "f %d/%d/%d %d/%d/%d %d/%d/%d %d/%d/%d",
                &ret->FaceArray[nF].Vertex[0],
                &ret->FaceArray[nF].TexCoord[0],
                &ret->FaceArray[nF].Normal[0],
                &ret->FaceArray[nF].Vertex[1],
                &ret->FaceArray[nF].TexCoord[1],
                &ret->FaceArray[nF].Normal[1],
                &ret->FaceArray[nF].Vertex[2],
                &ret->FaceArray[nF].TexCoord[2],
                &ret->FaceArray[nF].Normal[2],
                &ret->FaceArray[nF].Vertex[3],
                &ret->FaceArray[nF].TexCoord[3],
                &ret->FaceArray[nF].Normal[3]);
            if (nread != 12)
                printf("f: read only %d instead of 12\n", nread);                                                            
            nF++;
        }
```

I could make sscanf to try to read like 10 "%d"'s and based on the return value of sscanf allocate required size and then read. Also another thing is that format such as "f 1//1 2//2 3//3 5//2" is allowed where middle number is omitted, it only complicates thing further...

---

### Post by Wybiral on 2010-10-16
I'd use something like [strtok]("http://www.cplusplus.com/reference/clibrary/cstring/strtok/") to split it into tokens and work with it from there instead of using an overly specific ssanf.

---

