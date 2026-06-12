---
title: "problem with gcc?"
date: 2010-11-18
forum: Packaging and Compiling Programs
---

### Post by bbb777 on 2010-11-18
hi,

i have a simple c program for processing a band-sequential image that i have been using fine on my local ubuntu 8.04 machine for some time now. however, when i ftp this program over onto a debian server and then compile and run it (on the same set of images), i get different results. the main parts of the code goes like:

```

infile_i = fopen(infile_image, "rb");	

outfile_t = fopen(outfile_T, "wb");

unsigned char *n_i = malloc(total * sizeof(unsigned char));
//image values are in unsigned char; total is the number of pixels

fread(n_i, sizeof(unsigned char), total, infile_i);

long j;
for(j=0; j<total; j++){
//some operations
}

fwrite(n_o, sizeof(float), total, outfile_t);

//the above is repeated for all the bands in the image file

```

i use the following command to compile it, both locally and on the server:

gcc -Wall -lm code.c -o a.out

the problem with the results from the server is that, although the operations on each band seem to be done properly, the output bands (which are written chunk by chunk using fwrite) are displaced from one other, so that pixels that are originally vertically aligned are now displaced, along both the x- and y-axis. what's weirder is that, this displacement gets worse with increasing band number, such that the output band2 is displaced by, say, 2 vertical pixels and 2 horizontal pixels from the output band1, output band3 is 4 vertical pixels and 4 horizontal pixels displaced from band1, etc. the displacement is all along the same direction.

does anyone know what this is all about? is there a way to correct this?

thanks.

---

### Post by TiBaal89 on 2010-11-18
Just a random middle of the night possible ill informed long shot... but maybe check the value sizeof(float) and the like.

---

### Post by bbb777 on 2010-11-18
i have tried that before, and i think they are slightly different between my machine and the server. but i dont think that is a problem, because all my outputs are float, so the effect on every band should be the same. or am i missing something?

---

