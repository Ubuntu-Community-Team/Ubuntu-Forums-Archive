---
title: "Reading a sound file (.wav) into an array."
date: 2008-11-02
forum: Programming Talk
---

### Post by Coder543 on 2008-11-02
Is there anyone who can explain (possible with sample code in C) how I might read the frequency data into a pointer array of ints (or long longs if needed) (from a wav file)? This would be very helpful to me, since I am attempting to analyze different patterns in (a) sound file(s), *not* playback sound files.

---

### Post by WW on 2008-11-03
You can use the C library [libsndfile](http://www.mega-nerd.com/libsndfile/) to read the data. It is not "frequency data"; it is the sample data.  To get the frequencies, you'd have to process the data with something like an FFT.

Here's a C program that gets the sample data from "file.wav", and writes it as integers to "filedata.out":
```

#include <stdio.h>
#include <stdlib.h>
#include <sndfile.h>

int main()
    {
    SNDFILE *sf;
    SF_INFO info;
    int num_channels;
    int num, num_items;
    int *buf;
    int f,sr,c;
    int i,j;
    FILE *out;
    
    /* Open the WAV file. */
    info.format = 0;
    sf = sf_open("file.wav",SFM_READ,&info);
    if (sf == NULL)
        {
        printf("Failed to open the file.\n");
        exit(-1);
        }
    /* Print some of the info, and figure out how much data to read. */
    f = info.frames;
    sr = info.samplerate;
    c = info.channels;
    printf("frames=%d\n",f);
    printf("samplerate=%d\n",sr);
    printf("channels=%d\n",c);
    num_items = f*c;
    printf("num_items=%d\n",num_items);
    /* Allocate space for the data to be read, then read it. */
    buf = (int *) malloc(num_items*sizeof(int));
    num = sf_read_int(sf,buf,num_items);
    sf_close(sf);
    printf("Read %d items\n",num);
    /* Write the data to filedata.out. */
    out = fopen("filedata.out","w");
    for (i = 0; i < num; i += c)
        {
        for (j = 0; j < c; ++j)
            fprintf(out,"%d ",buf[i+j]);
        fprintf(out,"\n");
        }
    fclose(out);
    return 0;
    }

```
I only tested it on one file, and that file had just one channel, so I can't promise anything. :)

libsndfile can automatically give you the data as floats or doubles instead of ints, if you want.  Check out its docs.


P.S. The ubuntu packages to install for libsndfile are **libsndfile1** and **libsndfile1-dev**.

---

### Post by Coder543 on 2008-11-03
Oh, wow... The first reply looks to be exactly what I needed! Thank you, for your prompt assistance, WW! I will look into that code, that should have what I need.

---

### Post by Coder543 on 2008-11-03
Sorry for the double-post, however; when I attempted to compile that code. I received this output:
coder@coder-laptop:~/Desktop$ gcc *.c -o app.bin
/tmp/cc5LYdEV.o: In function `main':
snd_to_int.c:(.text+0x1e): undefined reference to `sf_open'
snd_to_int.c:(.text+0xcb): undefined reference to `sf_read_int'
snd_to_int.c:(.text+0xd7): undefined reference to `sf_close'
collect2: ld returned 1 exit status
coder@coder-laptop:~/Desktop$

This was after installing the libsndfile1 and libsndfile1-dev. What do i need to do?

---

### Post by WW on 2008-11-03
Add the option **-lsndfile** to the gcc command.

---

### Post by Coder543 on 2008-11-03
Thanks, that got it to compile.

---

### Post by Coder543 on 2008-11-06
What *is* this data exactly, if it would need processing with "an FFT"?

---

### Post by senorsunday on 2013-05-04
> **WW said:**
> You can use the C library [libsndfile]("http://www.mega-nerd.com/libsndfile/") to read the data. It is not "frequency data"; it is the sample data.  To get the frequencies, you'd have to process the data with something like an FFT.

Here's a C program that gets the sample data from "file.wav", and writes it as integers to "filedata.out":
```

#include <stdio.h>
#include <stdlib.h>
#include <sndfile.h>

int main()
    {
    SNDFILE *sf;
    SF_INFO info;
    int num_channels;
    int num, num_items;
    int *buf;
    int f,sr,c;
    int i,j;
    FILE *out;
    
    /* Open the WAV file. */
    info.format = 0;
    sf = sf_open("file.wav",SFM_READ,&info);
    if (sf == NULL)
        {
        printf("Failed to open the file.\n");
        exit(-1);
        }
    /* Print some of the info, and figure out how much data to read. */
    f = info.frames;
    sr = info.samplerate;
    c = info.channels;
    printf("frames=%d\n",f);
    printf("samplerate=%d\n",sr);
    printf("channels=%d\n",c);
    num_items = f*c;
    printf("num_items=%d\n",num_items);
    /* Allocate space for the data to be read, then read it. */
    buf = (int *) malloc(num_items*sizeof(int));
    num = sf_read_int(sf,buf,num_items);
    sf_close(sf);
    printf("Read %d items\n",num);
    /* Write the data to filedata.out. */
    out = fopen("filedata.out","w");
    for (i = 0; i < num; i += c)
        {
        for (j = 0; j < c; ++j)
            fprintf(out,"%d ",buf[i+j]);
        fprintf(out,"\n");
        }
    fclose(out);
    return 0;
    }

```


I want you let you know that years later, this code saved me from failing a senior design class days before graduation. I had to recreate a matlab code in C; the matlab to C converters were segfaulting and throwing way more errors than they were worth; and this code helped me recreate that code from scratch on my first time using C++, in less than a day.

Beyond gratitude. Thank you.

---

### Post by kittaddeepa6 on 2013-05-08
Hi.....please help me......

I am Divya. I have implemented the code given by you in C++.

But I am getting the following errors:
  [Linker error] undefined reference to `sf_open' 
  [Linker error] undefined reference to `sf_read_int' 
  [Linker error] undefined reference to `sf_close' 
  ld returned 1 exit status 

Please tell me how to solve this problem

---

### Post by QIII on 2013-05-08
This is a very old thread.  If you have a similar question, please start a new thread.

Closed.

---

