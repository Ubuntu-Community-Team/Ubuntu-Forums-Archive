---
title: "Numpy/Python: converting a string to float"
date: 2009-09-14
forum: Programming Talk
---

### Post by filifunk on 2009-09-14
so I'm making a recarray for historical stock data.  The data from yahoo! comes in a csv that is automatically read as a string.  When I put them into a recarray and specify dtypes most of which are floats, the data is no longer readable.  For instance:

my opening prices are:

```


r = np.rec.fromrecords(values, names ='date, open, hi, lo, close, volume, adj_close')

In [42]: r.open
Out[42]: 
chararray(['3.84', '4.00', '4.35', '3.89', '4.04', '4.15', '4.00', '3.80',
       '4.10', '4.00', '4.15', '3.77', '3.89', '3.77', '3.75', '3.75',
       '3.51', '3.62', '3.17', '3.30', '3.09', '3.24', '3.20', '3.32',
       '3.60', '3.64', '4.00', '3.93', '4.02', '4.19', '3.71', '4.01',
       '3.91', '3.58', '3.39', '3.20', '3.18', '3.22', '3.19', '3.38',
       '3.18', '3.00', '2.91', '2.98', '3.01', '2.95', '3.24', '3.94',
       '3.45', '3.64', '3.61', '3.75', '3.61', '3.87', '3.88', '3.61',
       '3.65', '3.90', '3.90', '3.94', '3.88', '3.79', '3.84', '3.77',
       '3.55', '3.66', '3.56', '3.70', '3.56', '3.56', '3.60', '3.51',
       '3.50', '3.69', '3.74', '3.65', '3.69', '3.75', '3.71', '3.65',
       '3.53', '3.48', '3.62', '3.62', '3.74', '3.62', '3.65', '3.79',
       '3.65', '3.63', '3.77', '3.74', '3.71', '3.95', '4.20', '4.50',
       '4.46', '4.36', '4.33', '4.48', '4.13', '4.31', '4.17', '4.39',
       '4.44', '4.48', '4.50', '4.49', '3.96', '4.30', '4.36', '4.35',
       '4.57', '4.53', '4.39', '4.58', '4.44', '4.26', '4.32', '4.48',
       '4.43', '4.58', '4.76', '4.63', '4.80', '4.83', '4.75', '5.00',
       '5.78', '6.08', '6.19', '6.08', '6.10', '6.08', '6.14', '6.86',
       '6.60', '6.63', '5.76', '5.94', '6.10', '6.16', '5.84', '6.06',
       '5.86', '5.50', '6.75', '6.76', '7.00', '7.12', '6.72', '6.66',
       '6.75', '6.37', '7.05', '7.14', '6.87', '7.04', '7.10', '7.14',
       '7.00', '7.30', '7.46', '7.57', '7.68', '7.78', '7.42', '6.66',
       '5.66', '5.54', '5.68', '6.22', '6.11'], 
      dtype='|S4')

```then when I try to turn these into floats by doing this:

```


r = np.rec.fromrecords(values, names =('date, open, hi, lo, close, volume, adj_close'), dtype = [('date', str), ('open', float), ('hi', float), ('lo', float), ('close', float), ('volume', int), ('adj_close', float)])

I get this for opening prices:


In [45]: print r.open
-------> print(r.open)
[[  5.27365197e-091   4.32849467e-315   4.49459938e-315 ...,
    4.49459938e-315   2.61773480e-310   2.16694178e-313]
 [  5.27365197e-091   3.99434251e-315   4.65843756e-315 ...,
    4.40976618e-315   2.61773812e-310   2.16609345e-313]
 [  5.27365197e-091   4.40976618e-315   3.99628525e-315 ...,
    4.74035665e-315   2.61773395e-310   2.16939936e-313]
 ..., 
 [  7.72819870e-091   4.65940894e-315   4.74068045e-315 ...,
    4.57748985e-315   2.61773976e-310   2.16777069e-313]
 [  7.72819870e-091   4.16077102e-315   3.99563768e-315 ...,
    4.65746620e-315   2.61774143e-310   2.16857045e-313]
 [  7.72819870e-091   4.07755677e-315   4.32622815e-315 ...,
    3.99693284e-315   2.61773895e-310   2.16196512e-313]]


```1.  Is this normal?  Or did I do something that throws the data off kilter?
2.  Is there any way to make these prices floats without changing the look of the data?


Thanks everyone for any 2 cents!

---

### Post by unutbu on 2009-09-14
When you write
```

r = np.rec.fromrecords(values, names ='date, open, hi, lo, close, volume, adj_close')
```

you are asking np.rec.fromrecords to guess the type of each column, since you do not state it explicitly. np.rec.fromrecords guesses that each column is a column of strings.
That is because of what you've put in the variable "values". "values" is probably a list of lists, with each element being a string, not a float. There lies the source of your problem.

When you write 
```

r = np.rec.fromrecords(values, names =('date, open, hi, lo, close, volume, adj_close'), dtype = [('date', str), ('open', float), ('hi', float), ('lo', float), ('close', float), ('volume', int), ('adj_close', float)])
```

you now tell np.rec.fromrecords that you want certain columns from the "values" variable to be *interpreted* as floats. Note this is not a matter of conversion -- here, np.rec.fromrecords does not try to guess that the data in "values" are strings and then parse those strings as floats. That's what python's float() built-in function does, but not np.rec.fromrecords().

Take for instance the string '3.84'. 3 is an ASCII character represented by some number between 0 and 255 (1 byte). So is '.', '8' and '4'. Those numbers are represented by some 4-byte sequence of 0's and 1's. It is this 4-byte sequence that np.rec.fromrecords is interpreting as a 4-byte float. 

So to fix your code, you may want to try something like this:
```

new_values=[]
for row in values:
    date,open,hi,lo,close,volume,adj_close=row
    new_values.append([str(date),float(open),float(hi),float(lo),
                       float(close),float(volume),float(adj_close)])
values=new_values
```

Better yet, you could do the float() conversions as you parse the csv file and build the "values" list.

---

### Post by filifunk on 2009-09-15
just want to say thanks!  Answered my question completely and it works perfectly.

---

