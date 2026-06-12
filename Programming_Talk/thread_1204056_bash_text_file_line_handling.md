---
title: "bash text file line handling"
date: 2009-07-04
forum: Programming Talk
---

### Post by kimr on 2009-07-04
Hi there,

I have a text file, with data in it, no separation characters. All lines are of equal length, in this sample 20 chars.

Lines have data in "fields", field length varies between data, in my sample the fields are of equal length..

The lines are "connected" to each other, lines number 1,2 and 3 are "connected", 4,5 and 6 also, 7,8 and 9 also, etc.

What I would like to do is collect data from line 1 starting from position 1 to 5, then 11 to 15, and from line 2 in position 6 to 10 and position 16 to 20, and from line 3 from position 6 to 15.

These data should then be written to a file in a way that the data collected from lines 1, 2 and 3 are written to one line (with some separation character, for ex ";"), the data collected from lines 4, 5 and 6 written to the next line, the data collected from line 7, 8 and 9 to the next line etc.

Original data example, 2 sets (3 lines per set) of data:

11111555558888899999
22222666664444477777
33333000007777744444
aaaaahhhhhtttttuuuuu
kkkkklllllmmmmmttttt
gggggrrrrrdddddxxxxx

Expected output:
11111;88888;66666;77777;0000077777;
aaaaa;ttttt;lllll;ttttt;rrrrrddddd;

I have been playing around in bash, with awk, sed etc., but I don't get anywhere.

The thing is, that in the orginal data file there are also spaces (meaning that in the originating system there was no data to be put in that field, but since the lines must be of equal length something goes in there, and hence the spaces). 

I have managed to get awk to read the data correctly from one line by changing the field separator from being a space to something else (like "#"), but the "connection" between the lines is the difficult thing for me.

Any suggestions?

KiMR

---

### Post by ghostdog74 on 2009-07-04
```


awk 'BEGIN{f=0}
f==0{
    printf substr($0,1,5)";"substr($0,11,5)";"
    f=1
    next
}
f==1{
    printf substr($0,6,4)";"substr($0,16,5)";"
    f=2
    next
}
f==2{
    printf substr($0,6,9)
}
NR%3==0{
    f=0
    print ""
}' file


```

---

### Post by kimr on 2009-07-04
Thank You, that did the trick.

- KiMR

---

