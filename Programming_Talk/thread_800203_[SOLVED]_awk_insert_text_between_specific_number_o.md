---
title: "[SOLVED] awk insert text between specific number of records"
date: 2008-05-19
forum: Programming Talk
---

### Post by Claus7 on 2008-05-19
Hello,

what we want to do : I want with awk to add text in a file from NR = 10 till NR = 20. The numbers are not the same every time and I provide them as an example. 
I was able to add text in line 10 or in every other line, yet no more than one line per text. The *for*, *if* or *while* statements with NR as a variable doesn't do the job, yet only if the text is going to be inserted in the beginning of the file.
Does anyone have any idea? Something like : for (NR=10;NR<=20;NR++) would be very nice, YET this doesn't work :(

EDIT: Ok, I found it and I post it, yet it took me the whole day!

```
awk '{
      if (NR>=10 && NR<=20)
      {printf "%6d %5d %5d  %10.5f  %15.2f \n", 4,5,6,7,8}
      else
      {print $0 }
     }' input > output
```
:)
Regards!

---

### Post by ghostdog74 on 2008-05-19
you can save on the if/else , as awk's pattern construct already incorporate "if"
```

awk 'NR>=10 && NR<=20 { 
    printf "%6d %5d %5d  %10.5f  %15.2f \n", 4,5,6,7,8
    next
}1' file

```

---

