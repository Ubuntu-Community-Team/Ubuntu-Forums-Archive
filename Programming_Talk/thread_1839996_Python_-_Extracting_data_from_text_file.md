---
title: "Python - Extracting data from text file"
date: 2011-09-06
forum: Programming Talk
---

### Post by madtowneast on 2011-09-06
Hi all,


I am trying to extract numbers from a very long text file (>50000 lines) and cant seem to be able to to get the python to do what i would like:

For example the file has lines like this:

```
ERROR [2011-08-29 17:20:02.934] snRate: 2.0918304
ERROR [2011-08-29 17:20:02.936] snRate: 2.03178464
ERROR [2011-08-29 17:20:02.936] scaler:7
ERROR [2011-08-29 17:20:02.938] scaler:5
ERROR [2011-08-29 17:20:02.939] snRate: 2.03178464
```

What I would like to extract are the numbers that come after the "snRate:" string. I have tried using the split command, but the varying sizes of the numbers is giving me trouble. What I have so far is:


```
#!/usr/bin/env python
import sys, os
import numpy as np
import pylab as py


f=open(sys.argv[1],'rU').readlines()
print type(f)
buffer=''
if f:
    for line in f:
        buffer += line

print buffer, type(buffer)

print buffer.split('snRate: ')
```

The buffer is now split into a list of strings, but I have having trouble getting the numbers out because it keeps adding the next like:

```
[...., 'ERROR [2011-08-29 17:20:02.934] snRate: ', '2.0918304\n ERROR [2011-08-29 17:20:02.936] snRate:', ....]
```

I would just like to have a list that goes something like 

```
[...,'2.0918304',...]
```
Thanks for any help in advance.

---

### Post by gardnan on 2011-09-06
Well, I don't have much experience in Python, but it looks like you need a regular expression here. This is pretty much what I would do:
[PHP]import re
...
my_list = []
for line in f:
    my_list += re.findall('snRate (\d.?\d+)', line)[/PHP]And then the variable my_list contains a list of all of the error numbers. Now, keep in mind, while I did test this code, I still am foreign enough to Python to recommend you do some tests of your own.
Also, if you want to read more on regular expressions: [http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

---

### Post by Erdaron on 2011-09-06
Do you need just a list of numbers, or do you need to keep the timestamp associated with each number?

If you only need the numbers, you could do something like this:
```
numbers = []
for line in f:
    a = f.split('snRate: ')
    if len(a) > 1:
        numbers.append(a[-1])

```

Basically, split out the numbers first, and then make them into a list.

---

### Post by kurum! on 2011-09-06
> **gardnan said:**
> Well, I don't have much experience in Python, but it looks like you a regular expression here.

sometimes, the easiest way is without regular expression.

---

### Post by kurum! on 2011-09-06
To OP, you can split on the word "snRate:". This is how i do it in Ruby

```

File.open("file").each do |line|
  puts line.split("snRate:")[1].strip if line[/snRate/]
end


```

Doing it the same in Python shouldn't be too hard, since the syntax is almost similar. It says, split on "snRate" in lines which contain the word "snRate", then while you iterate the lines, get the 2nd element of the split (which is your number) and remove any spaces.

---

### Post by madtowneast on 2011-09-07
Thanks for all the replies.

> **gardnan said:**
> Well, I don't have much experience in Python, but it looks like you need a regular expression here. This is pretty much what I would do:
[PHP]import re
...
my_list = []
for line in f:
    my_list += re.findall('snRate (\d.?\d+)', line)[/PHP]And then the variable my_list contains a list of all of the error numbers. Now, keep in mind, while I did test this code, I still am foreign enough to Python to recommend you do some tests of your own.
Also, if you want to read more on regular expressions: [http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

I tried this one and it worked perfectly. 

I have been trying to adjust to to get ```
depth
``` and ```
records
``` sent from another log file with format like this:

```
snData: 2011-08-29 17:09:54.438864:
	Depth: [0]
	RecordsSent: [61]

stringHit: 2011-08-29 17:09:54.438864:
	Depth: [8]
	RecordsSent: [3026]
```

Any recommendations?

Thanks again

---

### Post by Bodsda on 2011-09-07
> **madtowneast said:**
> Thanks for all the replies.
 
 
 
I tried this one and it worked perfectly. 
 
I have been trying to adjust to to get ```
depth
``` and ```
records
``` sent from another log file with format like this:
 
```
snData: 2011-08-29 17:09:54.438864:
    Depth: [0]
    RecordsSent: [61]
 
stringHit: 2011-08-29 17:09:54.438864:
    Depth: [8]
    RecordsSent: [3026]
```
 
Any recommendations?
 
Thanks again
 
Lets pretend our file looks like this, forget the other lines for now.
 
```

Depth: [0]
RecordsSent: [61]
Depth: [8]
RecordsSent: [3026]

```
 
All we want is the numbers in a list, one after another. So what we want to do is; for each line, extract the number between '[' and ']' - How about this code (untested)
 
```

mylist = []
 
handle = open(file, "r")
contents = handle.readlines()
handle.close()
 
for item in contents:
    mylist.append(item.split("[")[1].split("]")[0])

```
 
See if from that, you can work out how the double split works, and how you could ignore the snrate and stringhit lines. Let us know if your still having problems.
 
Hope this helps,
Bodsda

---

### Post by madtowneast on 2011-09-07
> **Bodsda said:**
> Lets pretend our file looks like this, forget the other lines for now.
 
```

Depth: [0]
RecordsSent: [61]
Depth: [8]
RecordsSent: [3026]

```
 
All we want is the numbers in a list, one after another. So what we want to do is; for each line, extract the number between '[' and ']' - How about this code (untested)
 
```

mylist = []
 
handle = open(file, "r")
contents = handle.readlines()
handle.close()
 
for item in contents:
    mylist.append(item.split("[")[1].split("]")[0])

```
 
See if from that, you can work out how the double split works, and how you could ignore the snrate and stringhit lines. Let us know if your still having problems.
 
Hope this helps,
Bodsda

Thank you very much for this. It worked. What I was wondering is how i can sort numbers i am reading by the labels, i.e. 

```
snData:
stringHit:
```

---

### Post by Bodsda on 2011-09-07
> **madtowneast said:**
> Thank you very much for this. It worked. What I was wondering is how i can sort numbers i am reading by the labels, i.e. 
 
```
snData:
stringHit:
```
 
I'm not entirely sure what you mean. Can you provide a sample file and what output you want the program to produce. Then we can help you get the code right.
 
Cheers,
Bodsda

---

### Post by madtowneast on 2011-09-07
> **Bodsda said:**
> I'm not entirely sure what you mean. Can you provide a sample file and what output you want the program to produce. Then we can help you get the code right.
 
Cheers,
Bodsda

Sample would be:

```
jvm: 2011-08-29 17:09:54.438864:
	MemoryStatistics: [290328680, 381288448]

moniData: 2011-08-29 17:09:54.438864:
	Depth: [0]
	RecordsSent: [1]

rdoutData: 2011-08-29 17:09:54.438864:
	Depth: [0]
	RecordsSent: [0]

rdoutReq: 2011-08-29 17:09:54.438864:
	TotalRecordsReceived: 132
	RecordsReceived: [132]
	BytesReceived: [8184]

sender: 2011-08-29 17:09:54.438864:
	NumReadoutRequestsReceived: 178
	NumHitsReceived: 2663
	NumReadoutsSent: 1
	NumHitsCached: 0
	NumHitsQueued: 310
	NumReadoutRequestsQueued: 0

snData: 2011-08-29 17:09:54.438864:
	Depth: [0]
	RecordsSent: [61]

stringHit: 2011-08-29 17:09:54.438864:
	Depth: [8]
	RecordsSent: [3026]

stringhub: 2011-08-29 17:09:54.438864:
	TimeOfLastHitOutputFromHKN1: 207977962295545677
	NumberOfActiveAndTotalChannels: [60, 60]
	NumberOfActiveChannels: 60
	TimeOfLastHitInputToHKN1: 207977964479700660
	HitRateLC: 0.0
	HitRate: 0.0
	TotalLBMOverflows: 1091

system: 2011-08-29 17:09:54.438864:
	LoadAverage: [0.0, 0.02, 0.35999999999999999]
	NetworkIO: {'lo_tx_errs': 0, 'eth1_rx_fifo': 0, 'eth2_rx_packets': 0, 'eth1_tx_compressed': 0, 'eth2_tx_compressed': 0, 'eth0_tx_fifo': 0, 'eth1_tx_packets': 0, 'lo_tx_compressed': 0, 'eth1_rx_compressed': 0, 'lo_rx_errs': 0, 'eth1_tx_fifo': 0, 'lo_tx_fifo': 0, 'eth0_tx_errs': 0, 'eth0_rx_multicast': 0, 'eth0_tx_carrier': 0, 'eth3_rx_compressed': 0, 'eth3_tx_drop': 0, 'lo_tx_drop': 0, 'eth2_rx_drop': 0, 'eth1_tx_drop': 0, 'eth3_rx_bytes': 0, 'eth3_tx_packets': 0, 'lo_rx_bytes': 8270472, 'eth2_rx_errs': 0, 'eth3_tx_errs': 0, 'eth0_rx_errs': 0, 'eth2_tx_errs': 0, 'lo_rx_packets': 71359, 'eth2_rx_compressed': 0, 'eth3_rx_packets': 0, 'eth0_tx_drop': 0, 'eth0_rx_frame': 0, 'eth1_tx_bytes': 0, 'eth1_rx_multicast': 0, 'eth1_rx_packets': 0, 'eth2_tx_fifo': 0, 'eth1_tx_errs': 0, 'eth2_tx_bytes': 0, 'eth3_rx_frame': 0, 'eth2_rx_frame': 0, 'eth1_rx_bytes': 0, 'eth0_rx_drop': 0, 'eth3_rx_drop': 0, 'eth1_rx_frame': 0, 'eth2_tx_packets': 0, 'eth0_tx_bytes': 389183382674, 'eth3_rx_errs': 0, 'eth0_rx_bytes': 141781372747, 'eth3_tx_compressed': 0, 'eth2_rx_fifo': 0, 'lo_tx_bytes': 8270472, 'eth1_rx_errs': 0, 'eth1_tx_carrier': 0, 'eth0_rx_packets': 478007025, 'lo_rx_drop': 0, 'eth0_tx_compressed': 0, 'eth0_rx_fifo': 0, 'eth3_tx_colls': 0, 'eth0_tx_colls': 0, 'lo_tx_packets': 71359, 'eth2_rx_multicast': 0, 'eth2_tx_colls': 0, 'eth3_tx_fifo': 0, 'eth1_tx_colls': 0, 'lo_tx_carrier': 0, 'lo_rx_frame': 0, 'eth1_rx_drop': 0, 'lo_tx_colls': 0, 'eth3_tx_bytes': 0, 'lo_rx_fifo': 0, 'eth2_tx_drop': 0, 'eth3_tx_carrier': 0, 'eth3_rx_multicast': 0, 'eth0_rx_compressed': 0, 'eth2_rx_bytes': 0, 'eth2_tx_carrier': 0, 'eth0_tx_packets': 1197286889, 'lo_rx_multicast': 0, 'lo_rx_compressed': 0, 'eth3_rx_fifo': 0}
	AvailableDiskSpace: {'/': 43836096, '/dev/shm': 24725760}

tcalData: 2011-08-29 17:09:54.438864:
	Depth: [0]
	RecordsSent: [0]

PyrateBufferManager: 2011-08-29 17:09:57.031479:
	CurrentAquiredBuffers: 0
	ReturnBufferCount: 4285
	CurrentAquiredBytes: 0
```

This pattern repeats every second. 

Output should be a graph, but I will just give a sample array:

```
snDataTime=[..., 17:09:54.438864, ...]
snDataDepth=[..., 0, ...]
snDataRecordsSent=[..., 61,...]
```

---

### Post by Bodsda on 2011-09-08
> **madtowneast said:**
> Sample would be:
 
```
jvm: 2011-08-29 17:09:54.438864:
    MemoryStatistics: [290328680, 381288448]
 
moniData: 2011-08-29 17:09:54.438864:
    Depth: [0]
    RecordsSent: [1]
 
rdoutData: 2011-08-29 17:09:54.438864:
    Depth: [0]
    RecordsSent: [0]
 
rdoutReq: 2011-08-29 17:09:54.438864:
    TotalRecordsReceived: 132
    RecordsReceived: [132]
    BytesReceived: [8184]
 
sender: 2011-08-29 17:09:54.438864:
    NumReadoutRequestsReceived: 178
    NumHitsReceived: 2663
    NumReadoutsSent: 1
    NumHitsCached: 0
    NumHitsQueued: 310
    NumReadoutRequestsQueued: 0
 
snData: 2011-08-29 17:09:54.438864:
    Depth: [0]
    RecordsSent: [61]
 
stringHit: 2011-08-29 17:09:54.438864:
    Depth: [8]
    RecordsSent: [3026]
 
stringhub: 2011-08-29 17:09:54.438864:
    TimeOfLastHitOutputFromHKN1: 207977962295545677
    NumberOfActiveAndTotalChannels: [60, 60]
    NumberOfActiveChannels: 60
    TimeOfLastHitInputToHKN1: 207977964479700660
    HitRateLC: 0.0
    HitRate: 0.0
    TotalLBMOverflows: 1091
 
system: 2011-08-29 17:09:54.438864:
    LoadAverage: [0.0, 0.02, 0.35999999999999999]
    NetworkIO: {'lo_tx_errs': 0, 'eth1_rx_fifo': 0, 'eth2_rx_packets': 0, 'eth1_tx_compressed': 0, 'eth2_tx_compressed': 0, 'eth0_tx_fifo': 0, 'eth1_tx_packets': 0, 'lo_tx_compressed': 0, 'eth1_rx_compressed': 0, 'lo_rx_errs': 0, 'eth1_tx_fifo': 0, 'lo_tx_fifo': 0, 'eth0_tx_errs': 0, 'eth0_rx_multicast': 0, 'eth0_tx_carrier': 0, 'eth3_rx_compressed': 0, 'eth3_tx_drop': 0, 'lo_tx_drop': 0, 'eth2_rx_drop': 0, 'eth1_tx_drop': 0, 'eth3_rx_bytes': 0, 'eth3_tx_packets': 0, 'lo_rx_bytes': 8270472, 'eth2_rx_errs': 0, 'eth3_tx_errs': 0, 'eth0_rx_errs': 0, 'eth2_tx_errs': 0, 'lo_rx_packets': 71359, 'eth2_rx_compressed': 0, 'eth3_rx_packets': 0, 'eth0_tx_drop': 0, 'eth0_rx_frame': 0, 'eth1_tx_bytes': 0, 'eth1_rx_multicast': 0, 'eth1_rx_packets': 0, 'eth2_tx_fifo': 0, 'eth1_tx_errs': 0, 'eth2_tx_bytes': 0, 'eth3_rx_frame': 0, 'eth2_rx_frame': 0, 'eth1_rx_bytes': 0, 'eth0_rx_drop': 0, 'eth3_rx_drop': 0, 'eth1_rx_frame': 0, 'eth2_tx_packets': 0, 'eth0_tx_bytes': 389183382674, 'eth3_rx_errs': 0, 'eth0_rx_bytes': 141781372747, 'eth3_tx_compressed': 0, 'eth2_rx_fifo': 0, 'lo_tx_bytes': 8270472, 'eth1_rx_errs': 0, 'eth1_tx_carrier': 0, 'eth0_rx_packets': 478007025, 'lo_rx_drop': 0, 'eth0_tx_compressed': 0, 'eth0_rx_fifo': 0, 'eth3_tx_colls': 0, 'eth0_tx_colls': 0, 'lo_tx_packets': 71359, 'eth2_rx_multicast': 0, 'eth2_tx_colls': 0, 'eth3_tx_fifo': 0, 'eth1_tx_colls': 0, 'lo_tx_carrier': 0, 'lo_rx_frame': 0, 'eth1_rx_drop': 0, 'lo_tx_colls': 0, 'eth3_tx_bytes': 0, 'lo_rx_fifo': 0, 'eth2_tx_drop': 0, 'eth3_tx_carrier': 0, 'eth3_rx_multicast': 0, 'eth0_rx_compressed': 0, 'eth2_rx_bytes': 0, 'eth2_tx_carrier': 0, 'eth0_tx_packets': 1197286889, 'lo_rx_multicast': 0, 'lo_rx_compressed': 0, 'eth3_rx_fifo': 0}
    AvailableDiskSpace: {'/': 43836096, '/dev/shm': 24725760}
 
tcalData: 2011-08-29 17:09:54.438864:
    Depth: [0]
    RecordsSent: [0]
 
PyrateBufferManager: 2011-08-29 17:09:57.031479:
    CurrentAquiredBuffers: 0
    ReturnBufferCount: 4285
    CurrentAquiredBytes: 0
```
 
This pattern repeats every second. 
 
Output should be a graph, but I will just give a sample array:
 
```
snDataTime=[..., 17:09:54.438864, ...]
snDataDepth=[..., 0, ...]
snDataRecordsSent=[..., 61,...]
```
 
Ok, so you are ignoring every line except for the line beginning with 'snData' and the two lines following it.
 
(Code untested)
```

snDataT = []
snDataD = []
snDataRS = []
 
handle = open(file, "r")
contents = handle.readlines()
handle.close()
 
count = -1
for item in contents:
    count += 1
    if "snData" in item:
        snDataT.append(item.split()[2].strip(":")
        snDataD.append(contents[count + 1].split('[')[1].split(']')[0]
        # Add your entry here

```
 
I've left a comment in the section for the records sent line. See if you can work out from the data depth line how you would go about obtaining the value for records sent. It should be fairly straight forward. 
 
If you get stuck, try breaking the code down line by line and work out exactly what the splits and strips do. Add extra print statements to see current data in the variables.
 
If after that your still having problems, post the code you have and we will help 'you' work out how to do it.
 
Hope this helps,
Bodsda

---

