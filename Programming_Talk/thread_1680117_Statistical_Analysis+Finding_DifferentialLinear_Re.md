---
title: "Statistical Analysis+Finding Differential/Linear Relation among data?"
date: 2011-02-02
forum: Programming Talk
---

### Post by nipunreddevil on 2011-02-02
I have a database consisting of 5 columns let say c1 to c5 and c6 is dependent on the first five columns.I wish to know how to express c6 in terms of c1 through c5.My data set shall be of a evolving nature.What sort of techniques are suggested.For eg. to be used in Octave or Scilab or R.And instead of a linear relation how can i have a differential equation amongst the same data.

---

### Post by schauerlich on 2011-02-02
With no information as to what sort of data you have and how it all relates to each other, what sort of advice are you hoping to receive?

---

### Post by nipunreddevil on 2011-02-02
The data is like
Col1 can take values from {10,25,35,50,60,75,85,100}
Col2 can take values from {0.5,1,2}
Col3 can take values from {0,1}
Col4 can take values from {60,120,180,240...}
Col5 is variable
Col6 is Col5/col4 and is the variable whose function i need

---

### Post by __Frank__ on 2011-02-04
What you want is called regression analysis. You can of course roll your own, but I would recommend using a package like Minitab, SPSS, R etc.

For example Minitab will give you an output resembling:

The regression equation is
Y = 10.9 + 0.831 X

In addition to that it will give you an Analysis of Variance table and some other useful information to build your model.

Cheers,
Frank

---

