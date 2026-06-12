---
title: "CImg: jpg file unknown format."
date: 2009-10-03
forum: Programming Talk
---

### Post by lcym on 2009-10-03
[SIZE=2]Hi,
I wrote a small program using CImg library and g++ compiler and I installed imagemagick v6.5.6.

The code is as follows

[/SIZE]```

[SIZE=3]#include "CImg.h"
using namespace cimg_library;

int main(){
     CImg <unsigned char> img("train.jpg");
     img.display("Train");

     return 0;
}
[/SIZE]

```[SIZE=2] 

The program passes compliation but when I run the program, an error message 

"CImg <unsigned char>:: load() "train.jpg", format not recognized" prompts me.

What could be cause? Thanks.
[/SIZE]

---

### Post by Raskol Nikov on 2011-07-13
Hi,
I have a similar problem for the format .tiff
The error displayed is the following:

> sh: convert: not found
sh: gm: not found
sh: convert: not found
sh: gm: not found
sh: convert: not found
sh: gm: not found
terminate called after throwing an instance of 'cimg_library::CImgIOException'
  what():  [instance(0,0,0,0,(nil),non-shared)] CImg<float>::load() : Failed to recognize format of file './Train/8008_024.tiff'.


I'm going crazy searching a solution at this error. :(

Please help!

---

### Post by Raskol Nikov on 2011-07-14
Hey,
there is someone who can help me?
I can't understand this problem:(

---

### Post by ravizombie on 2013-04-13
I have also faced the same problem, but found a solution, after few tries.

Download CImg.h from the website - [http://cimg.sourceforge.net/download.shtml](http://cimg.sourceforge.net/download.shtml)
and place it in the same folder as the cpp file.


 if the below errors are still found
------------
sh: 1: convert: not found
sh: 1: gm: not found
sh: 1: convert: not found
sh: 1: gm: not found
sh: 1: convert: not found
sh: 1: gm: not found
--------------
Run the command in ubuntu, or install imagemagick
>sudo apt-get install imagemagick libmagickcore-dev

Hopefully, this should solve the prob

---

### Post by lisati on 2013-04-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

