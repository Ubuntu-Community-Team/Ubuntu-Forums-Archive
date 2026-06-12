---
title: "Python formating question."
date: 2009-07-26
forum: Programming Talk
---

### Post by swoll1980 on 2009-07-26
{python]

In the print statement at the end of this program I would like to change the format of all the outputs to $0000.00 How would I go about doing this? Thanks in advance.

---

### Post by Can+~ on 2009-07-26
[PHP]print "The purchase amount is $%04.2f. The discount is $%04.2f The total is $%04.2f" % (sub, discount, total)[/PHP]

%f : float
%04f : float padded with 4 zeroes
%04.2f : float padded with 4 zeroes and 2 zeroes after the decimal separator.

Read more about here:
[http://docs.python.org/library/stdtypes.html#string-formatting](http://docs.python.org/library/stdtypes.html#string-formatting)

---

### Post by swoll1980 on 2009-07-26
Thank you very much kind sir/madam.

---

### Post by Can+~ on 2009-07-26
> **swoll1980 said:**
> Thank you very much kind sir/madam.

Sir, actually.

Btw, if you're working with money, is better to stay clear from floating point calculation because of the rounding errors, and use the [decimal module]("http://docs.python.org/library/decimal.html").

You could even code your own Money class to handle money and print it in a nice formatting like "$1,200.30".

---

### Post by swoll1980 on 2009-07-27
Thanks again.

---

