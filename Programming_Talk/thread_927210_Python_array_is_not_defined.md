---
title: "Python: array is not defined?"
date: 2008-09-22
forum: Programming Talk
---

### Post by densha on 2008-09-22
Hi. I'm having a bit of trouble with a python script that I know works as others have tried it. When I run the following script, This error is returned:

Traceback (most recent call last):
  File "cluster.py", line 39, in <module>
    y = array(p,'d')
NameError: name 'array' is not defined

I'm not a python coder, but isn't that saying there is no array function? The below script utilizes the pycluster and numpy modules, but I think this issue is just something simple. This is a brand new box, and I may be missing dependencies. Any help would be appreciated as I have no clue what's up.

Thanks!

```

#!/usr/bin/python

from Pycluster import *
import sys

## pull in command line arguments
#file_path = sys.argv[1]
distance_threshold = 0.6

## Open file and read into string
#f = open(file_path)
#string = f.read()

string = '|| 0.728532777993, 0.844502317749, 0.161366189324, 0.942832583858, 0.76247427825, 0.844112241427, 0.233933001139, 0.842335957819, 0.236405614725, 0.824350752799,  || 0.822256613139, 0.897450261494, 0.86854557703, 0.968129801707, 0.694691521622, 0.944345590249, 0.820035612328, 0.822658477994, 0.366231767381, 0.877665464664,  || 0.929803701707, 0.722045073101, 0.754211220424, 0.980246101532, 0.782040718376, 0.981295746226, 0.84680008879, 0.84343287039, 0.844799864436, 0.37588860197,  || 0.663220463378, 0.73582377828, 0.121742078872, 0.948071774622, 0.780300606948, 0.929535326467, 0.88967743081, 0.827158160696, 0.896464998731, 0.33808964583,  || 0.745132272087, 0.766033691087, 0.879415730774, 0.773621328069, 0.793645370056, 1, 0.822609917514, 0.0249302687645, 0.277257304319, 0.853266812163,  || 0.659805056767, 0.765204130015, 0.87069169998, 0.697740904651, 0.974399175746, 0.944382853386, 0.262031649892, 0.844421431874, 0.916102263117, 0.889625251044,  || 0.733835094278, 0.235191106376, 0.923421762697, 0.841759167693, 0.992945589865, 0.886933060537, 0.235179111027, 0.946652611152, 0.325312738382, 0.378436868977,  || 0.6260569298, 0.74657473342, 0.82461698749, 0.73448683465, 0.956679057586, 0.766980289533, 0.355096444049, 0.945231043441, 0.326798424332, 0.779269689475,  || 0.879455801443, 0.746918007202, 0.774199938178, 0.793049594189, 0.178958153731, 0.835546962865, 0.964418854529, 0.865340223448, 0.182025571146, 0.328021039883,  || 0.194891864622, 0.749420774612, 0.776808698969, 0.798650098292, 0.849289661317, 0.811458462507, 0.918717714416, 0.901702240251, 0.0859780715517, 0.373932781087,  || 0.894906316949, 0.739391918767, 0.694510826174, 0.254823520918, 0.951960087505, 0.766177262999, 0.945714600755, 0.903181638985, 0.812765231631, 0.896858497865,'
#print string

# Clean string
string = string.strip(',| ')

# parse data into list
cleanlist = []
list = string.split(' ||')

for sublist in list:
#  print sublist
  sublist = sublist.strip(',| ')

  sublist = sublist.split(',')

  for x in range(len(sublist)):
    sublist[x] = float(sublist[x])
  cleanlist.append(sublist)

  
distance = []
for x in range(len(cleanlist)):
#  print x
  p = cleanlist[x][0:x]
  y = array(p,'d')
  distance.append(y)
    

# Do cluster analysis
tree = treecluster(method='a',distancematrix=distance)

# Prepare string to return to PHP
return_string = ""
for node in tree:
  if node.distance < distance_threshold:
    return_string += str(node.left) + "," + str(node.right) + "," + str(node.distance) + ";"

print "Cluster output:"
print return_string


```

---

### Post by days_of_ruin on 2008-09-22
```
import array
```
Then replace "array" with "array.array".

---

### Post by chidorex on 2008-09-22
You may be missing the numeric package. I hope these links help you out.

[http://projects.scipy.org/pipermail/scipy-user/2006-August/008849.html](http://projects.scipy.org/pipermail/scipy-user/2006-August/008849.html)
[http://www.dalkescientific.com/writings/NBN/clustering.html](http://www.dalkescientific.com/writings/NBN/clustering.html)

Best of luck.

---

### Post by densha on 2008-09-22
Well, that was my first guess. Pycluster now utilizes numpy instead of numeric. I installed the python-numpy package through apt-get and everything went well. However, it still doesn't seem to work. It doesn't make sense.

To make sure python saw that numpy was installed, I tried to import Pycluster before and after installing numpy.

**Before:**
xorsyst@ubuntu:~/public_html$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52)
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from Pycluster import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/Pycluster/__init__.py", line 1, in <module>
    import numpy
ImportError: No module named numpy

**After:**
xorsyst@ubuntu:~/public_html$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52)
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from Pycluster import *
>>>

No error, so I assume it's installed right.

---

### Post by pmasiar on 2008-09-22
Quite often I see beginners struggle with errors resulting from laziness, like yours "from Pycluster import *". Using this lazy import, you reject any help what Python would tell you if you importe names one by one, as you should.

"import *" means you are begging for problems, and you got what you deserved.

---

### Post by densha on 2008-09-22
Actually I am not the author of this script, but that's besides the point. *Thanks* though pmasiar.

---

### Post by densha on 2008-09-22
After digging around the Pycluster module directory, I discovered that the array line should be:

```

y = Numeric.array(p,'d')

```

---

### Post by vinayras on 2008-10-09
Changing
y = array(p,'d')
to
y = numpy.array(p,'d')

Should work if you have numpy & pycluster installed properly

Regards
Vinay
[http://www.vinayras.com](http://www.vinayras.com)

---

