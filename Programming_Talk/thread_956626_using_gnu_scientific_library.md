---
title: "using gnu scientific library"
date: 2008-10-23
forum: Programming Talk
---

### Post by diamantis13 on 2008-10-23
Hi everybody,
I would like to use gsl in a C++ program, but I am not sure how to do it. Initially I thought of downloading the source from GNU and compile it etc. But I see in synaptic that libgsl is already installed, so I was considering linking my code with these libraries. The problem is that I do not know which is better and how to do it.
Thank you very much

---

### Post by galileon on 2008-10-23
something like this:

install libgsl0-dev or something in synaptic, then in your source.cpp file,

#include <gsl_fft.h>

int main()
{
// use the functions for fft here
}

and remember to link with g++ source.cpp -lgsl, or something like this...

sorry this is vague. i havent used it yet, but will do soon, will figure it out and explain if you can't do it...

---

### Post by StOoZ on 2008-10-23
all you need to know (and much more..) is in here :
[http://www.gnu.org/software/gsl/manual/html_node/]("http://www.gnu.org/software/gsl/manual/html_node/")

---

### Post by santhust on 2010-06-15
> **StOoZ said:**
> all you need to know (and much more..) is in here :
[http://www.gnu.org/software/gsl/manual/html_node/]("http://www.gnu.org/software/gsl/manual/html_node/")

thanks :smile:

---

