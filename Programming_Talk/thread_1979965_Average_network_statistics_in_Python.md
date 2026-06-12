---
title: "Average network statistics in Python"
date: 2012-05-14
forum: Programming Talk
---

### Post by christianrough on 2012-05-14
I'm newbie to python and I need to calculate the 'average speed' of my network interface(like the tool nload) on a linux machine. The below code is telling me how much bytes have been sent and received. I would appreciate if someone could help me save the average speed of my network interface to a file. I know that the average speed can be calculated if we know when the interface was up. I wish to make this code run in the background continuously and it stores the average speed (upload/download) to a file every 3 seconds. If someone can give a good solution in C, that would be GREAT! :)

```

def main():
    rx_bytes, tx_bytes = get_network_bytes('wlan0')
    print '%i bytes received' % rx_bytes
    print '%i bytes sent' % tx_bytes
      
def get_network_bytes(interface):
    for line in open('/proc/net/dev', 'r'):
        if interface in line:
            data = line.split('%s:' % interface)[1].split()
            rx_bytes, tx_bytes = (data[0], data[8])
            return (int(rx_bytes), int(tx_bytes))

if __name__ == '__main__':
    main()

```

---

### Post by ofnuts on 2012-05-15
> **christianrough said:**
> I'm newbie to python and I need to calculate the 'average speed' of my network interface(like the tool nload) on a linux machine. The below code is telling me how much bytes have been sent and received. I would appreciate if someone could help me save the average speed of my network interface to a file. I know that the average speed can be calculated if we know when the interface was up. I wish to make this code run in the background continuously and it stores the average speed (upload/download) to a file every 3 seconds. If someone can give a good solution in C, that would be GREAT! :)

```

def main():
    rx_bytes, tx_bytes = get_network_bytes('wlan0')
    print '%i bytes received' % rx_bytes
    print '%i bytes sent' % tx_bytes
      
def get_network_bytes(interface):
    for line in open('/proc/net/dev', 'r'):
        if interface in line:
            data = line.split('%s:' % interface)[1].split()
            rx_bytes, tx_bytes = (data[0], data[8])
            return (int(rx_bytes), int(tx_bytes))

if __name__ == '__main__':
    main()

```
Obtain the values at regular time intervals, compute the differences, and divide by the time interval.

The rest looks suspiciously like homework...

---

### Post by psyllex on 2013-01-31
> **ofnuts said:**
> Obtain the values at regular time intervals, compute the differences, and divide by the time interval.

The rest looks suspiciously like homework...

I'm trying to do something from similar(not homework...for work..but I'm python ignorant)  Just essentially grab the rx and tx stats, every .5 s or so from a script to generate some json to use in a realtime graph (or about as real time as I can get it).  

I am curious what imports are you using?

---

### Post by greenpeace on 2013-01-31
Those other posts are from nearly a year ago... 

When I did something similar before, I used:

**commands** - to make a call to the linux ifconfig command and get the bytes sent & received
**time**     - to calculate the time intervals

For writing your data to json, check the **json**[1] library

good luck!

[1] [http://docs.python.org/2/library/json.html](http://docs.python.org/2/library/json.html)

---

### Post by psyllex on 2013-02-01
> **greenpeace said:**
> Those other posts are from nearly a year ago... 

When I did something similar before, I used:

**commands** - to make a call to the linux ifconfig command and get the bytes sent & received
**time**     - to calculate the time intervals

For writing your data to json, check the **json**[1] library

good luck!

[1] [http://docs.python.org/2/library/json.html](http://docs.python.org/2/library/json.html)



Alright...this is what I pulled in the end.  The json isn't perfect but it's close:


     ```
 lines = open("/proc/net/dev", "r").readlines()

      columnLine = lines[1]
      _, receiveCols , transmitCols = columnLine.split("|")
      receiveCols = map(lambda a:"recv_"+a, receiveCols.split())
      transmitCols = map(lambda a:"trans_"+a,     transmitCols.split())

      cols = receiveCols+transmitCols

      faces = {}
      for line in lines[2:]:
      if line.find(":") < 0: continue
      face, data = line.split(":")
      faceData = dict(zip(cols, data.split()))
      faces[face] = faceData

      #import pprint                                                                                                                                         
      #pprint.pprint(faces)                                                                                                                                  

      import json
      data_string = json.dumps(faces)
      print 'JSON:', data_string
```

This is the output after jsbeautifer:

{'    lo': {'recv_bytes': '501767',
            'recv_compressed': '0',
            'recv_drop': '0',
            'recv_errs': '0',
            'recv_fifo': '0',
            'recv_frame': '0',
            'recv_multicast': '0',
            'recv_packets': '3888',
            'trans_bytes': '501767',
            'trans_carrier': '0',
            'trans_colls': '0',
            'trans_compressed': '0',
            'trans_drop': '0',
            'trans_errs': '0',
            'trans_fifo': '0',
            'trans_packets': '3888'},
 '  eth0': {'recv_bytes': '0',
            'recv_compressed': '0',
            'recv_drop': '0',
            'recv_errs': '0',
            'recv_fifo': '0',
            'recv_frame': '0',
            'recv_multicast': '0',
            'recv_packets': '0',
            'trans_bytes': '0',
            'trans_carrier': '0',
            'trans_colls': '0',
            'trans_compressed': '0',
            'trans_drop': '0',
            'trans_errs': '0',
            'trans_fifo': '0',
            'trans_packets': '0'},
 ' wlan0': {'recv_bytes': '163141505',
            'recv_compressed': '0',
            'recv_drop': '0',
            'recv_errs': '0',
            'recv_fifo': '0',
            'recv_frame': '0',
            'recv_multicast': '0',
            'recv_packets': '188139',
            'trans_bytes': '16567648',
            'trans_carrier': '0',
            'trans_colls': '0',
            'trans_compressed': '0',
            'trans_drop': '0',
            'trans_errs': '0',
            'trans_fifo': '0',
            'trans_packets': '102498'}}

---

### Post by greenpeace on 2013-02-01
It doesn't seem to work here as it seems to have lost the formatting on the way.  Moving things around, and tidying up a little, I get the following:

```
#!/bin/usr/env python
#
import json

lines = open("/proc/net/dev", "r").readlines()

columnLine   = lines[1]

# here you can use a list slice (the "[1:3]") to 
# capture only the bits you want...
receiveCols, transmitCols = columnLine.split("|")[1:3]  

receiveCols  = map(lambda a:"recv_"+a,  receiveCols.split())
transmitCols = map(lambda a:"trans_"+a, transmitCols.split())

cols = receiveCols+transmitCols

faces = {}
for line in lines[2:]:
      if line.find(":") < 0: 
            continue
      face, data  = line.split(":")
      faceData    = dict(zip(cols, data.split()))
      faces[face] = faceData

print "JSON: ", json.dumps(faces)

#uncomment the following line for a "prettier" output
#print("JSON: "+ json.dumps(faces, indent=4))
```

Note that it's customary to include your "import" statements at the top of the file/script... Also, you can always wrap a **print()** around the json.dumps method to make the output more readable.

There doesn't seem to be any problem with the json?  looks ok to me, and passes validation[1]!

Finally, I'm sure you're already handling it, but how are you marking the time?  Have you considered including a "time" element in the JSON?



[1] [http://jsonlint.com/](http://jsonlint.com/)

---

### Post by psyllex on 2013-02-01
> Note that it's customary to include your "import" statements at the top of the file/script... Also, you can always wrap a **print()** around the json.dumps method to make the output more readable.

There doesn't seem to be any problem with the json?  looks ok to me, and passes validation[1]!

Finally, I'm sure you're already handling it, but how are you marking the time?  Have you considered including a "time" element in the JSON?



[1] [http://jsonlint.com/](http://jsonlint.com/)
Yeah I'm aware of the includes being on top.  I'm just new to python so I've kind of been programming it in such a way as I can follow the logic...I forgot to clean it up before posting. I had pretty print where I had that "import json" which is why I posted it that way.  I learned programming first on C++ so I understand the need for clean code, all my javascript time hasn't help me write super clean code though....yet for scripting it's so small I like that I can be a slob about it sometimes.  But it will eventually bite me in the '****'.

I simply use a python time function to get the time i.e.:

       ```
import datetime
       now = datetime.datetime.now()
```

I use that just to time stamp the stats.  Sorry forgot to include that...(I try and paraphrase or pull any extraneous code so you fine people don't have to read through everything).  I'm only worried about the last 3 hours of any time period so I only keep track of a 24 hour time cycle (not 12 so I don't have to contend with the weird negative time i.e. 1pm - 11am kinda thing). Thanks for the help people!):P

---

### Post by greenpeace on 2013-02-01
> **psyllex said:**
> Yeah I'm aware of the includes being on top.  I'm just new to python so I've kind of been programming it in such a way as I can follow the logic...I forgot to clean it up before posting. I had pretty print where I had that "import json" which is why I posted it that way.  I learned programming first on C++ so I understand the need for clean code, all my javascript time hasn't help me write super clean code though....yet for scripting it's so small I like that I can be a slob about it sometimes.  But it will eventually bite me in the '****'.

I simply use a python time function to get the time i.e.:

```
import datetime
now = datetime.datetime.now()
```

I use that just to time stamp the stats.  Sorry forgot to include that...(I try and paraphrase or pull any extraneous code so you fine people don't have to read through everything).  I'm only worried about the last 3 hours of any time period so I only keep track of a 24 hour time cycle (not 12 so I don't have to contend with the weird negative time i.e. 1pm - 11am kinda thing). Thanks for the help people!):P

Have you checked the **time()** function in the **time** library? [1]

It returns the current time in seconds (and milliseconds) since the epoch... so doing the maths should be nice and easy:

```
gp@mariachi:~$ python
Python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import time
>>> time.time()
1359772391.150641

```



Happy coding!  :)


[1] [http://docs.python.org/2/library/time.html#time.time](http://docs.python.org/2/library/time.html#time.time)

---

