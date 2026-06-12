---
title: "[SOLVED] Python isdigit() method question"
date: 2007-11-04
forum: Programming Talk
---

### Post by Siph0n on 2007-11-04
I have my script read in lines, and than split it with ' ' as the delimiter (if that's the right word), to make each line a list. The lines in the file are like the following:
"012345 111222333 Shawn M. McCarthy 1234"
without the quotes. So I end up with:
lineSplit[0] = 012345
lineSplit[1] = 111222333
lineSplit[2] = Shawn
lineSplit[3] = M.
lineSplit[4] = McCarthy
lineSplit[5] = 1234

However when I do lineSplit[5].isdigit() , it returns false... Any ideas? I found out that if the lines in my file were like this:
"012345 111222333 Shawn M. McCarthy 1234 "
It would work. Any idea why I need a space at the end of the line? Could it be a special \n character or something at the end of the line? Thanks for any help! :)

---

### Post by ghostdog74 on 2007-11-04
you have given an empty separator '', if you want to split by space, do " ", or just leave it by default.
eg
```

>>> s="012345 111222333 Shawn M. McCarthy 1234"
>>> s.split()
['012345', '111222333', 'Shawn', 'M.', 'McCarthy', '1234']
>>> s.split()[5]
'1234'
>>> s.split()[5].isdigit()
True

```

---

### Post by Siph0n on 2007-11-04
Thanks! I tried it out and it works now!!! :)

---

