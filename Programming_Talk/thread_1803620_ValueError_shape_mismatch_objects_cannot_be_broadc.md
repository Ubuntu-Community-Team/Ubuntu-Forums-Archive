---
title: "ValueError: shape mismatch: objects cannot be broadcast to a single shape"
date: 2011-07-13
forum: Programming Talk
---

### Post by Saad Bin Ahmed on 2011-07-13
Hey,

I got the following error. If anybody knows about this error then please share the solution.

inputs = ((array(inputs)-inputMeans)/inputStds).tolist()
ValueError: shape mismatch: objects cannot be broadcast to a single shape

---

### Post by Arndt on 2011-07-13
> **Saad Bin Ahmed said:**
> Hey,

I got the following error. If anybody knows about this error then please share the solution.

inputs = ((array(inputs)-inputMeans)/inputStds).tolist()
ValueError: shape mismatch: objects cannot be broadcast to a single shape

What language or program is this?

---

### Post by Saad Bin Ahmed on 2011-07-13
this program is in python.

---

### Post by Saad Bin Ahmed on 2011-07-13
> **Saad Bin Ahmed said:**
> this program is in python.

from numpy import array

inputMeans =array([1, 2, 3])

inputStds =array([4, 5, 6])

inputs = ((array(inputs)-inputMeans)/inputStds).tolist()
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)

/home/saad/<ipython console> in <module>()

ValueError: shape mismatch: objects cannot be broadcast to a single shape

This is the error message which shows to me when I try to execute program. Your timely help would be highly appreciated.

---

### Post by Arndt on 2011-07-13
> **Saad Bin Ahmed said:**
> from numpy import array

inputMeans =array([1, 2, 3])

inputStds =array([4, 5, 6])

inputs = ((array(inputs)-inputMeans)/inputStds).tolist()
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)

/home/saad/<ipython console> in <module>()

ValueError: shape mismatch: objects cannot be broadcast to a single shape

This is the error message which shows to me when I try to execute program. Your timely help would be highly appreciated.

What is 'inputs'? If it is a different length from inputMeans, you will get that error.

---

### Post by Saad Bin Ahmed on 2011-07-14
Hey,
I want to execute the following python program but it terminates with error 
**[SIZE=2]ValueError: shape mismatch: objects cannot be broadcast to a single shape[/SIZE]**

Please have a look on it and suggest me where I made mistake.

from numpy import arange, array, vectorize, newaxis
#from Numeric import *
#from NetCDF import * 
import netcdf_helpers
from scipy import *
from optparse import OptionParser
import sys
import os
from xml.dom.minidom import parse

labels = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', 'a', 'b', 'c', 'd', 'e', 'f', 'g','ga', 'h', 'i', 'j', 'k', 'km', 'l', 'm', 'n', 'o', 'p', 'pt', 'q','r','s','sc','sp','t','u','v','w','x','y','z']
inputMeans =array([511.8343, 102.7592, 0.03199977])
inputStds =array([134.0498, 24.34094, 0.1758981])

#command line options
parser = OptionParser()

#parse command line options
(options, args) = parser.parse_args()
if (len(args)<2):
    print "usage: -options input_filename output_filename"
    print options
    sys.exit(2)

inputFilename = args [0]
ncFilename = args[1]
print options
print "input filename", inputFilename
print "data filename", ncFilename
seqDims = []
seqLengths = []
targetStrings = []
wordTargetStrings = []
seqTags = []
inputs = []
contain=[]
new=[]
print "reading data files"
for l in file(inputFilename).readlines():
    xmlfile = l.strip()
    if len(xmlfile):
        print xmlfile
        seqTags.append(xmlfile)
        upxfile = xmlfile.replace('xml', 'upx')
        if os.path.exists(upxfile):
            word = parse(upxfile).getElementsByTagName('hwData')[0].getElementsByTagName('label')[0].getElementsByTagName('alternate')[0].getAttribute('value').strip().replace(' ','*')
            print word
            wts = word.encode('spell')
            print wts
            wordTargetStrings.append(wts)    
            ts = ""
            for c in word:
                label = c.encode('spell')
                ts += label + ' '
            ts = ts.strip()
            print ts
            targetStrings.append(ts)
        else:
            wordTargetStrings.append(' ')
            targetStrings.append(' ')            
        oldlen = len(inputs)
        for trace in parse(xmlfile).getElementsByTagName('trace'):        
            for coords in trace.firstChild.nodeValue.split(','):
                pt = coords.split()
                inputs.append([float(pt[0]), float(pt[1]), 0.0])
            inputs[-1][-1] = 1
        seqLengths.append(len(inputs) - oldlen)
        seqDims.append([seqLengths[-1]])

[SIZE=2]**inputs = ((array(inputs)- inputMeans)/inputStds).tolist()**[/SIZE][COLOR=Red]** // shows error in this line**[/COLOR]
print len(labels), labels
print labels

#create a new .nc file
file = netcdf_helpers.NetCDFFile(ncFilename, 'w')

#create the dimensions
netcdf_helpers.createNcDim(file,'numSeqs',len(seqLengths))
netcdf_helpers.createNcDim(file,'numTimesteps',len(inputs))
#netcdf_helpers.createNcDim(file,'inputPattSize',len(inputs[0]))
netcdf_helpers.createNcDim(file,'numDims',1)
netcdf_helpers.createNcDim(file,'numLabels',len(labels))



your help would be highly appreciated.

---

### Post by Saad Bin Ahmed on 2011-07-14
> **Arndt said:**
> What is 'inputs'? If it is a different length from inputMeans, you will get that error.


Please have a look on it and suggest me where I made mistake.

from numpy import arange, array, vectorize, newaxis
#from Numeric import *
#from NetCDF import * 
import netcdf_helpers
from scipy import *
from optparse import OptionParser
import sys
import os
from xml.dom.minidom import parse

labels = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', 'a', 'b', 'c', 'd', 'e', 'f', 'g','ga', 'h', 'i', 'j', 'k', 'km', 'l', 'm', 'n', 'o', 'p', 'pt', 'q','r','s','sc','sp','t','u','v','w','x','y','z']
inputMeans =array([511.8343, 102.7592, 0.03199977])
inputStds =array([134.0498, 24.34094, 0.1758981])

#command line options
parser = OptionParser()

#parse command line options
(options, args) = parser.parse_args()
if (len(args)<2):
print "usage: -options input_filename output_filename"
print options
sys.exit(2)

inputFilename = args [0]
ncFilename = args[1]
print options
print "input filename", inputFilename
print "data filename", ncFilename
seqDims = []
seqLengths = []
targetStrings = []
wordTargetStrings = []
seqTags = []
inputs = []
contain=[]
new=[]
print "reading data files"
for l in file(inputFilename).readlines():
xmlfile = l.strip()
if len(xmlfile):
print xmlfile
seqTags.append(xmlfile)
upxfile = xmlfile.replace('xml', 'upx')
if os.path.exists(upxfile):
word = parse(upxfile).getElementsByTagName('hwData')[0].getElementsByTagName('label')[0].getElementsByTagName('alternate')[0].getAttribute('value').strip().replace(' ','*')
print word
wts = word.encode('spell')
print wts
wordTargetStrings.append(wts) 
ts = ""
for c in word:
label = c.encode('spell')
ts += label + ' '
ts = ts.strip()
print ts
targetStrings.append(ts)
else:
wordTargetStrings.append(' ')
targetStrings.append(' ') 
oldlen = len(inputs)
for trace in parse(xmlfile).getElementsByTagName('trace'): 
for coords in trace.firstChild.nodeValue.split(','):
pt = coords.split()
inputs.append([float(pt[0]), float(pt[1]), 0.0])
inputs[-1][-1] = 1
seqLengths.append(len(inputs) - oldlen)
seqDims.append([seqLengths[-1]])

inputs = ((array(inputs)- inputMeans)/inputStds).tolist() // shows error in this line
print len(labels), labels
print labels

#create a new .nc file
file = netcdf_helpers.NetCDFFile(ncFilename, 'w')

#create the dimensions
netcdf_helpers.createNcDim(file,'numSeqs',len(seqL engths))
netcdf_helpers.createNcDim(file,'numTimesteps',len (inputs))
#netcdf_helpers.createNcDim(file,'inputPattSize',l en(inputs[0]))
netcdf_helpers.createNcDim(file,'numDims',1)
netcdf_helpers.createNcDim(file,'numLabels',len(la bels))



your help would be highly appreciated.

---

### Post by drs305 on 2011-07-14
Threads merged.

---

### Post by Tony Flury on 2011-07-15
> **Saad Bin Ahmed said:**
> Please have a look on it and suggest me where I made mistake.

<code cut>


your help would be highly appreciated.

Can you repost your code - using code tags (the # on the toolbar) and that way the indentation (which is so critical to python) is preserved, and we stand a chance of helping you.

It also seems you derive inputs from an XML file - so we wont be able to find the problem unless you attach that file as well.

---

