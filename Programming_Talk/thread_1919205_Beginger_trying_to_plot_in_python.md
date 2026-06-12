---
title: "Beginger trying to plot in python"
date: 2012-02-02
forum: Programming Talk
---

### Post by conradin on 2012-02-02
Hi all I'm trying to plot a sine wave using python, but I get this message:
Im not sure if this error is a library related error, or if my syntax is incorrect. Can someone help me understand where I've gone wrong?
```
./numpz
Traceback (most recent call last):
  File "./numpz", line 31, in <module>
    d=loadtxt('out.csv',dtype=double)
  File "/usr/lib/python2.7/site-packages/numpy/lib/io.py", line 630, in loadtxt
    X.append(tuple([conv(val) for (conv, val) in zip(converters, vals)]))
ValueError: invalid literal for float(): -2.00000e-03w-0.022w-0.022w0w-2.00000e-03w-0.026w-0.026

```

here is the script Im calling ./numpz
```
#!/usr/bin/python
from numpy import *
from numpy.linalg import inv
import matplotlib.pyplot as plt
import csv

cr = csv.reader(open('T0000ALL.CSV','rb'))
try : 
	w = open('out.CSV','wb')
	cw = csv.writer(w, delimiter='w')
except:
	print 'no file found'
	quit()
data = 0 
for row in cr:
	try:    
		if (row[0] == 'TIME'):
			data=1
			continue
	except:         
		continue
	
	if (not data):
		continue

	row[3] = 0
	cw.writerow(row)
w.close()


d=loadtxt('out.csv',dtype=double)
plt.plot(d[:,0]*le3, d[:,1]*le3 )
plt.grid()
plt.title('500Hz SienWave')
plt.xlabel('Time in ms')
plt.ylabel('Voltage, Volts')		
plt.show		

```

---

### Post by ofnuts on 2012-02-02
if you have "w" as separators in the input file you have to specify a delimiter when creating the reader.

---

