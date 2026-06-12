---
title: "compare two large text files"
date: 2014-01-23
forum: Programming Talk
---

### Post by peter_brickles on 2014-01-23
Hello all 

I have two large text files one contains car registration numbers on each line the other details of makes of card colours and registrations. 

I would like to display only the cars in the second file where the registration is not found to match and exissting one in the first file is there any way to do this ?

thanks

---

### Post by steeldriver on 2014-01-23
Is this homework? You can use grep with the -F and -f options to read + test fixed strings from a file

```

       -f FILE, --file=FILE
              Obtain  patterns  from  FILE,  one  per  line.   The  empty file
              contains zero patterns, and therefore matches nothing.

```

With the -v (match inversion) switch that should do what you need.

---

