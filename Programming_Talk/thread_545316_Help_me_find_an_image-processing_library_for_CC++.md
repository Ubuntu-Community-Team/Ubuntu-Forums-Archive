---
title: "Help me find an image-processing library for C/C++"
date: 2007-09-07
forum: Programming Talk
---

### Post by Zdravko on 2007-09-07
Hi!
I am a C/C++ programmer. I really do need a simple yet powerful and flexible image manipulating library.
The purpose is:
I have an image (jpeg, jpg, gif, png, bmp etc.) with certain dimension. I also want to resize the image to a given dimensions. That is:
Image: 100x100
We want: 80x90.

Or:
Image: 100x100
We want 100:120

Etc...
A universal approach with a free library (console-driven maybe?) is what I need.
Thanks in advance!

---

### Post by CptPicard on 2007-09-07
[Imagemagick]("http://www.imagemagick.org/script/index.php")

---

### Post by loell on 2007-09-07
libmagick++9-dev

---

### Post by asmoore82 on 2007-09-07
> **Zdravko said:**
> Hi!
I am a C/C++ programmer. I really do need a simple yet powerful and flexible image manipulating library.
The purpose is:
I have an image (jpeg, jpg, gif, png, bmp etc.) with certain dimension. I also want to resize the image to a given dimensions. That is:
Image: 100x100
We want: 80x90.

Or:
Image: 100x100
We want 100:120

Etc...
A universal approach with a free library (console-driven maybe?) is what I need.
Thanks in advance!

unless you really want to do the coding yourself, you could probably just do some scripting with the netpbm package ...
[http://netpbm.sourceforge.net/](http://netpbm.sourceforge.net/)
I've used just BASH scripts and netpbm to synthesize video myself.

netpbm is designed with UNIX pipes in mind and converts all images to pnm/pbm format for manipulation and then back again
(much like GIMPs internal XCF format), so you could do somthing like ...

```
#!/bin/bash

output=`date`
mkdir "$output"

for pic in *.jpg
do
     cat "$pic" | jpegtopnm | pamscale -xyfill 100 120 | pnmtojpeg > "${output}/${pic}"
done
```

---

### Post by daveshields on 2007-09-07
Though I haven't used it, I have heard good things about Intel's OpenCV. See [http://www.intel.com/technology/computing/opencv/]("http://www.intel.com/technology/computing/opencv/")

---

### Post by dempl_dempl on 2007-09-07
Ok, I don't wanna advertize my site ( well, not to much ) , 
but if you go to my site [www.stosha.net](www.stosha.net) , you'll find couple of Linux libraries for that.

Just go to Libraries/   C++  (Multiplatform) /  2d & 3d Graphics .

You'll find couple of good libraries there.

---

### Post by Zdravko on 2007-09-09
That would be difficult....

---

### Post by dempl_dempl on 2007-09-22
You call my site difficult!?

If I see you I'll punch you in a face. 
I don't live far from you , you know ...

Off-Topic, but you have Slavic name, and you live in Bulgaria. What's up with that?

---

### Post by loell on 2007-09-22
:lolflag: i hope that post is suppose to be funny, if it is indeed serious, i'm not sure , that he meant your site.

---

### Post by dempl_dempl on 2007-09-23
Ofcourse I was joking...
:D

But, Punching people in the face is funy sometimes ( when you're not the one being punched ofcourse :) )

---

### Post by k_pax on 2008-04-05
Can any one tell me the basic steps involved in gabor pyramidal decomposition of image   or explain me the difference between guassian, laplacian and gabir pyramidal decomposition of image.
                            i need it badly and urgently. please help me out!!

---

### Post by smartbei on 2008-04-05
@OP:
I have ued OpenCV for such things and it has been very simple to learn and use.

@k_pax:
There is this site named Google... [[link]]("http://www.google.com")

---

### Post by risu_vk on 2008-10-10
A simple and easy to learn (all in a single header) for basic stuffs [http://cimg.sourceforge.net]("http://cimg.sourceforge.net")

If you want to do more go for ITK + VTK

---

### Post by in_rainbow on 2009-03-05
openCV all the way. There are even python wrappers, so you don't have to worry about memory allocation and pointers.

---

