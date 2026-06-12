---
title: "Octave / Matlab - scaling axes query"
date: 2010-10-13
forum: Programming Talk
---

### Post by goseph on 2010-10-13
Hi all!

I am plotting some data with Surf in Octave, I want to set each unit in the x and y axes to "Res" instead of just the index of the matrix containing said data.

Does anybody know how? DataAspectRatio sounded good but it literally just stretched the image of the rendered graph!

I need cross compatibility with Matlab and Octave

Thanks!

Luke

---

### Post by renzokuken on 2010-10-13
i might be able to help cos i have a fair bit of experiance with this type of plotting in Matlab, but i'm not sure what you mean by "Res". could you clarify it a bit more.

cheers

---

### Post by goseph on 2010-10-13
> **renzokuken said:**
> i might be able to help cos i have a fair bit of experiance with this type of plotting in Matlab, but i'm not sure what you mean by "Res". could you clarify it a bit more.

cheers

Ah sorry, "Res" is just a variable in my program.

Concrete Example:

I wish to plot how a measurement varies in 2-dimensional space. I have a 2d matrix representing measurements taken every 0.1 metres in the xy-plane, when I plot this, the x and y axes are labelled with 0, 1, 2 etc. (ie. the index of the data in the data matrix) I want to change the unit labelling to 0, 0.1, 0.2 etc. (ie. the real world "indexes" of the measurements.

Is this clear?

Thankyou for your time!

---

### Post by renzokuken on 2010-10-13
it sounds like you are only passing your Z data to the surf function and so it uses the matrix coords as X and Y

i.e. are you simply running (imagine Z is your data)
```
surf(Z)
```

what you need to do is have your X and Y data (the 0.1 steps)in seperate variables of the same dimensions and order as Z. then you can run

```
surf(X,Y,Z)
```

this will use X for the x-axis, Y for the y-axis and Z as your surface data

---

### Post by goseph on 2010-10-13
Yeah that sounds about right, I guess I will just have to fill up x and y with 0:0.1:n

Thanks for help.

---

### Post by renzokuken on 2010-10-13
for example, if you had your data in an excel file that looked like this

```

x     y     z
0     0     5
0.1   0     6
0.2   0     3
0.3   0     8
.......
0.7   0.6   4
0.8   0.6   6
0.9   0.6   3
1     0.6   7
....etc etc

```

in Matlab you would run
```

data = xlsread('filename.xls');
surf(data(1,:),data(2,:),data(3,:));

```

that would use the first column for X, second column for Y and third column for Z

---

### Post by Vox754 on 2010-10-13
> **goseph said:**
> Hi all!

I am plotting some data with Surf in Octave, I want to set each unit in the x and y axes to "Res" instead of just the index of the matrix containing said data.

Does anybody know how? DataAspectRatio sounded good but it literally just stretched the image of the rendered graph!

I need cross compatibility with Matlab and Octave

Thanks!

Luke
It seems like Octave internally uses gnuplot to do the plotting.

While gnuplot is legendary, I never got to learn its syntax. If you have the time you should check out "matplotlib". It's a library for Python that does plotting with a basic Matlab interface. However, once you get the hang of it, you will prefer to use Python's own object oriented interface. And this being Python, matplotlib it's easy to learn and it's cross platform.

Of course, this implies using Matlab/Octave to do the numerical calculations, while using Python solely to do the plotting. Depending on your needs, you may want to do everything in a single program. For me, it works just fine; doing calculation in Octave, exporting the results to a text file, reading it with Python, and plotting. Python also has the "numpy" library, which lets you use matrices just like Octave, so maybe in the future I may not even use Octave.

If you want to take a look at matplotlib, just use any search engine. The project's webpage has a section with examples, in which you can see both the code and the figure produced.

---

