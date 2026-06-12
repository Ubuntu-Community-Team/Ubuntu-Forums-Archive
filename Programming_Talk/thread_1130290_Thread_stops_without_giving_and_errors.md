---
title: "Thread stops without giving and errors"
date: 2009-04-19
forum: Programming Talk
---

### Post by Wug on 2009-04-19
Resolved.

Note to self:

DO NOT try to delete 'this'. IT WILL BLOW UP EVERYTHING.

---

### Post by dwhitney67 on 2009-04-19
Ok, so is this a programming challenge where the task is to guess the contents of your application?  So far the only clues we have been given is that you are developing with Dev-C++ and are using printf().  Hmmm, could you be developing in C or C++?

---

### Post by Wug on 2009-04-19
main looks like this:

> int main(int argc, char *argv[])
{
  double xmin_, xmax_, ymin_, ymax_;
  int width_, height_, depth_;
  xmin_ = -1;
  xmax_ = 1;
  ymin_ = -1;
  ymax_ = 1;
  width_ = 100;
  height_ = 100;
  depth_ = 10000;
  printf("file: %s\ncorners: (%f, %f) and (%f, %f)\nsize: %ix%i\ndepth: %i", name, xmin_, ymax_, xmax_, ymin_, width_, height_, depth_);
  bmp_image mm = RenderMbrot(xmin_, xmax_, ymin_, ymax_, width_, height_, depth_);
  printf("never reaches this line\n");
  mm.bmp_save(name);
  printf("Finished rendering.\n");
  mm.~bmp_image();
  return 0;
}


the function RenderMbrot(...) looks like this
> bmp_image RenderMbrot(double xmin, double xmax, double ymin, double ymax, int wpix, int hpix, int depth)
{
  int w,h,x,y;
  double pct;
  printf("\n");
  bmp_image mandelbrot = bmp_image(wpix, hpix, 24);
  for (h=1; h<=hpix; h++)
  {
    for (w=1; w<=wpix; w++)
    {
      mandelbrot.data[mandelbrot.index(w, h)]=mbrot_red(CheckMandel(xmin+w*(xmax-xmin)/(wpix-1),ymin+h*(ymax-ymin)/(hpix-1),depth));
      mandelbrot.data[mandelbrot.index(w, h)+1]=mbrot_grn(CheckMandel(xmin+w*(xmax-xmin)/(wpix-1),ymin+h*(ymax-ymin)/(hpix-1),depth));
      mandelbrot.data[mandelbrot.index(w, h)+2]=mbrot_blu(CheckMandel(xmin+w*(xmax-xmin)/(wpix-1),ymin+h*(ymax-ymin)/(hpix-1),depth));
    }
    pct = (100.0 * h / hpix);
    printf("\r%.1f%%", pct);
  }
  return mandelbrot;
}

all of the functions are defined.
all of the classes are defined.
the program compiles with no problems, warnings, errors, or otherwise.
the program runs with no visible errors and whatnot.
the only problem is that in main, it never gets past the line > bmp_image mm = RenderMbrot(xmin_, xmax_, ymin_, ymax_, width_, height_, depth_);

---

### Post by dwhitney67 on 2009-04-19
Typically an index starts at 0; is there a particular reason you start your loops at 1?

Also, that big key on your keyboard... the spacebar... you should consider using it sometimes.  Also, when posting code, please post the complete code so that others do not have to put together the framework around it to compile/run it themselves.

---

