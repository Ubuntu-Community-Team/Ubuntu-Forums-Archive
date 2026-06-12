---
title: "smart way of reading file in Python ?"
date: 2006-02-26
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-26
I have the folowing input file. The first number is the value of the variable on the right hand side after the "#" sign.
```

1024	#max_number_of_nodes
1024	#total_stream_packets
256	#packet_size
4	#play_time_of_one_packet
5	#max_concurrent_upoads
5	#max_concurrent_downloads
3072	#max_upload_speed_of_server
256	#dedicated_speed_per_connection
8	#max_nodes_in_alliance
4	#max_number_of_alliance
30	#temporal_time

```

I wrote a functions as follows, and I thought it was really raw (I am newbie to python so bear with me). Could you suggest me some smart way of reading file with lot of variables. Thanks.
```

def read_input_file(filename):        
    f = open(filename, "r")
    while True:
        line = f.readline()
        if (not line): break
        var = line.split()
        max_number_of_nodes = int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        total_stream_packets = int(var[0])
        ine = f.readline()
        if (not line): break
        var = line.split()
        packet_size = int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        play_time_of_one_packet = int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        max_concurrent_upoads = int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        max_concurrent_downloads= int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        max_upload_speed_of_server= int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        dedicated_speed_per_connection= int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        max_nodes_in_alliance= int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        max_number_of_alliance= int(var[0])
        line = f.readline()
        if (not line): break
        var = line.split()
        temporal_time= int(var[0])

```

---

### Post by psychicdragon on 2006-02-27
Here's a slightly simpler solution:
```
import re

FILE = "bo.txt"
f = open(FILE, 'r')
string = f.read()
f.close()

string = string.rstrip('\n')
lines = re.split('\n', string)
		
var = {}
for line in lines:
    (value, key) = re.split('\t+?\#', line)
    var[key] = value

print var

```

There are probably even better ways to do this though.

---

### Post by Ozitraveller on 2006-02-27
Or you could do the read on a set size, say read 1000 chars at a time, and adds the string to some type of data structure (stack) or even an array. And on another thread have a small process to monitor the stack, and if there is something there, do the the splitting. It might even be worth giving the statck a bit of a head start, by say don't start processing anything on the stack until there are 5, 10, 20 items waiting there, just so the file reading doesn't catch up with the splitting. Anyway just an idea. :-) 

Tip: if you want to process really large files the buffered approach is a more efficient way.

---

### Post by LordHunter317 on 2006-02-27
The best idea, unless the file is much to large to hold into memory is to read the file line by line, then parse it into records and values.  As for how to do that in Python, beats me.

---

### Post by Virak on 2006-02-27
```
def read_input_file(filename):
    file = open(filename, "r")
    vars = {}

    for line in file:
        value, name = line.split()
        if name[0] == "#":
            vars[name[1:]] = value

    file.close()

    return vars
```
^ That's how I'd do it.

---

### Post by krypto_wizard on 2006-02-27
thanks for all the responses

---

### Post by krypto_wizard on 2006-02-27
I like your approach. A quick question since all the variables and their values are in as a dictionary, how to get them as an actual variable.

For ex when I say
```

print max_upload_speed

```

It gives me error.

How to fix this.


[QUOTE=psychicdragon]Here's a slightly simpler solution:
```
import re

FILE = "bo.txt"
f = open(FILE, 'r')
string = f.read()
f.close()

string = string.rstrip('\n')
lines = re.split('\n', string)
		
var = {}
for line in lines:
    (value, key) = re.split('\t+?\#', line)
    var[key] = value

print var

```

There are probably even better ways to do this though.[/QUOTE]

---

### Post by thumper on 2006-02-27
how about this one liner?

```
dict([(x[1][1:], int(x[0])) for x in [x.split() for x in open('input.txt')]])
```

:)

---

### Post by krypto_wizard on 2006-02-27
awesome!!!

How to get the variable names which are dictionary keys to be as variable names of the python program ?



[QUOTE=thumper]how about this one liner?

```
dict([(x[1][1:], int(x[0])) for x in [x.split() for x in open('input.txt')]])
```

:)[/QUOTE]

---

### Post by Van_Gogh on 2006-02-27
I like Virak's solution the best, it's the most readable and the way I'd do it too. It'll run into difficulties if there's ever an empty line though, but that's nothing a try/except clause won't fix.

Thumper's solution is very cool though, but too dense for my taste: I have to struggle to completely understand it all.

> How to get the variable names which are dictionary keys to be as variable names of the python program ?

That'd be a bad idea even if it's possible. You'd not know what your variable names would be, so how could you ever know what to do with them after you get them in your program? I'd suggest using dictionaries and just reading its values when you need them. It's easier too.

---

### Post by krypto_wizard on 2006-02-27
I am still looking solution for 

" How to get the variable names which are dictionary keys to be as variable names of the python program ?"

Could somebody explain it



[QUOTE=Van_Gogh]I like Virak's solution the best, it's the most readable and the way I'd do it too. It'll run into difficulties if there's ever an empty line though, but that's nothing a try/except clause won't fix.

Thumper's solution is very cool though, but too dense for my taste: I have to struggle to completely understand it all.



That'd be a bad idea even if it's possible. You'd not know what your variable names would be, so how could you ever know what to do with them after you get them in your program? I'd suggest using dictionaries and just reading its values when you need them. It's easier too.[/QUOTE]

---

### Post by thumper on 2006-02-27
How about this... Values is a class that initialises member variables defined by the named parameters of the constructor.  Using the ** operator we can expand a dictionary into named parameters.

```
class Values(object):
    def __init__(self, **kwds):
        self.__dict__.update(kwds)

```
The __dict__ member is a dictionary that contains the member variables for the object.  

If you don't like complex list comprehension then do it in two steps.  It is more readable that way.  I was just being a smart arse.

```
>>> fileinfo = [x.split() for x in open(filename)]
>>> fileinfo
[['1024', '#max_number_of_nodes'], ['1024', '#total_stream_packets'], ['256', '#packet_size'], ['4', '#play_time_of_one_packet'], ['5', '#max_concurrent_upoads'], ['5', '#max_concurrent_downloads'], ['3072', '#max_upload_speed_of_server'], ['256', '#dedicated_speed_per_connection'], ['8', '#max_nodes_in_alliance'], ['4', '#max_number_of_alliance'], ['30', '#temporal_time']]
>>> mapinfo = dict([(x[1][1:], int(x[0])) for x in fileinfo])
>>> info = Values(**mapinfo)
>>> print info.dedicated_speed_per_connection
256
>>> print info.max_concurrent_downloads
5

```

The first list comprehension statement reads each line from the input file and creates a list of the split lines.  split by default splits on whitespace which is what we want in this case.

The second statement builds a dictionary from a list of key value pairs.  x[1][1:] says to take the second item of x (which is our text "#variable_name") and slice that from the first item, which removes the #.  The second part of the tuple is the integer representation of the first part of the split line.

---

