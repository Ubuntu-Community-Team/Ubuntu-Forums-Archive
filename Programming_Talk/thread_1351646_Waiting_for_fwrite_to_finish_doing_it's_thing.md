---
title: "Waiting for fwrite to finish doing it's thing"
date: 2009-12-10
forum: Programming Talk
---

### Post by bamsanks on 2009-12-10
Hello.
I have written some code to write an image to a file using fwrite.
The image is then sent out through sockets to a browser somewhere far away.
The problem is that fwrite seems not to have finished before the next code gets executed.
Is there any way I can loop until it finishes?

---

### Post by dwhitney67 on 2009-12-10
fwrite() reports back status indicating the number of bytes it successfully wrote.  If this value does not equal the number of bytes you specified, then you should investigate why.

I cannot tell you why your code did not work... because I have not seen it.  For all I know your image is 100 bytes long, and your told fwrite() that it is 50 bytes long.  Please post some code if you want a better answer to why your usage of fwrite() is not behaving as you would have wanted.

---

### Post by Arndt on 2009-12-11
> **bamsanks said:**
> Hello.
I have written some code to write an image to a file using fwrite.
The image is then sent out through sockets to a browser somewhere far away.
The problem is that fwrite seems not to have finished before the next code gets executed.
Is there any way I can loop until it finishes?

The answer from dwhitney is a good one. You can also try using fflush and see if it works better.

---

### Post by bamsanks on 2009-12-11
Main section:
```

    //From here ..
    pixIn = ReadBitmap("/home/sam/Pictures/symbols/char.bmp", &w, &h);
    sx = sy = floor((nh-h)/2);
    Imprint(pixIn, pixOut, sx, sy, w, h, nw, nh);

    DrawBorder(pixOut, nw, nh);
    WriteBitmap(FilePath, pixOut, nw, nh);
    // .. to here just creates and writes the image ^

    fp=fopen(FilePath, "rb");
    if (stat(FilePath, &results) == 0) {
        fs = results.st_size;
        printf("%i\n", fs);
    } else {
        printf ("File could not be located. Exiting.\n");    
        exit(0);
    }
    char *xv=malloc(fs);

    fread(xv, fs, 1, fp);
    send(new_socket, xv, fs, 0);

```WriteBitmap function:

```
void WriteBitmap(char FilePath[], int *pixels, int w, int h) {

    int i;
    int tw = w, th = h;
    int ll = (floor((double)(w*3-1)/4)+1)*4; //Line length
    int sod = h * ll; //Size of image data
    int sof = sod + 54; //Size of file
    char xv[sof];
    int t, p;
    int x, y;
    int col;
    int r, g, b, bw;
    FILE *fp;

    if(remove(FilePath))
        printf("File doesn't exist. Creating anyway.\n");

    fp = fopen(FilePath, "wb");

    //Clear out all the crap
    for (i=0;i<=sof;i++) xv[i]=0;

    //Write "BM"
    xv[0]=66;xv[1]=77;

    //Write file size over 4 bytes:
    for (i=3;i>=0;i--) {
        p = pow(256,i);
        t = (int)floor((double)sof/p);
        xv[i+2]=t;
        sof -= t * p;
    }
    
    //Define length of headers
    xv[10]=54;

    //Define length of info header
    xv[14]=40;

    //Write width and height over 8 bytes:
    for (i=3;i>=0;i--) {
        p = pow(256,i);
        t = (int)floor((double)tw/p);
        xv[i+18]=t;
        tw -= t * p;
        t = (int)floor((double)th/p);
        xv[i+22]=t;
        th -= t * p;
    }

    //Set number of planes
    xv[26]=1;

    //Specify bits per pixel
    xv[28]=24;

    //Write size of data over 4 bytes:
    for (i=3;i>=0;i--) {
        p = pow(256,i);
        t = (int)floor((double)sod/p);
        xv[i+34]=t;
        sod -= t * p;
    }

    // NOTE: Bitmaps are stored upside down
    for (y=0;y<h;y++) {
        for (x=0;x<w;x++) {
            xv[56+(h-(y+1))*ll+x*3] = pixels[y*w*3+x*3+0];
            xv[55+(h-(y+1))*ll+x*3] = pixels[y*w*3+x*3+1];
            xv[54+(h-(y+1))*ll+x*3] = pixels[y*w*3+x*3+2];
        }
    }

    fwrite(xv, sizeof(xv[0]), sizeof(xv)/sizeof(xv[0]), fp);
}
```I'm hoping this gives you an idea of what's going on.

.. Also, I know that the image is saving correctly as it appears as a full bitmap with no errors in my "Pictures" folder.
I can also create the image prior to running the program and just use the socket send part with success.
That's what gave me the impression that fwrite() hasn't finished before it gets sent.

---

### Post by dwhitney67 on 2009-12-11
Before exiting the function WriteBitmap(), fclose() the file.

Then verify that the file is indeed the size you expect by examining it on your HDD, or some other other way.

Your code is way to complicated for me to spend only 5 minutes examining it.  For starters, it is incomplete, and second, your choice of variable names is quite pathetic.  Try defining variable names that convey information; in other words, instead of something like 'n', choose to use 'number' or 'num'.

Another worthwhile piece of advice... next time you are trying to understand the concepts of how something works, write a simple program that exercises the functions you are using.  For example:
```

#include <stdio.h>
#include <assert.h>

int main()
{
   char data[50] = {0};
   char restoredData[50] = {0};

   FILE* file = fopen("./foo", "wb");

   if (file)
   {
      // write to, then close the file
      fwrite(data, 1, sizeof(data), file);
      fclose(file);

      // reopen the file for reading
      file = fopen("./foo", "rb");

      // read the data, and verify that we got the quantity of data expected
      assert(fread(restoredData, 1, sizeof(restoredData), file) == sizeof(restoredData));
   }
   else
   {
      return 1;
   }

   return 0;
}

```

---

### Post by bamsanks on 2009-12-11
The lack of the fclose() function was the issue.
I tried to simplify the code to avoid further complication, however I have no excuse for the variable names.
Thankyou for your help and putting up with my code.

---

### Post by dwhitney67 on 2009-12-11
> **bamsanks said:**
> The lack of the fclose() function was the issue.

Upon further reflection on the problem, I believe an fflush() would also have committed the data to the file, thus allowing for it to be read by another FILE stream.

Either way, as you have found, explicitly closing the file with an fclose() ensures that the written data is committed to the file.

---

