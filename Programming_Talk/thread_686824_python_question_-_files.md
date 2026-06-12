---
title: "python question - files"
date: 2008-02-03
forum: Programming Talk
---

### Post by Mr.popo on 2008-02-03
If I had:

[PHP]
inp = open("text.txt", "w")
inp.write("Hello")
inp.close()
inp = open("text.txt", "r")
for line in inp:
    print line
inp.close()
[/PHP]

If the user then inputted where they would want the file to be saved to then what function would I use?

I was thinking of using the os.system() command to move the file to the location the user specified.

Thanks.

---

### Post by LaRoza on 2008-02-03
Look at the os module. When you open the file for write access, you are saving it. So, have user specify the file to open.

---

### Post by Martin Witte on 2008-02-03
Why not asking for a full path, and then if it is valid then use that?
[PHP]
import os.path
filename = raw_input('give filename\n')
if os.path.lexists(os.path.dirname(filename)):        
    inp = open(filename, "w")
    inp.write("Hello")
    inp.close()
    inp = open(filename, "r")
    for line in inp:
        print line
    inp.close()
else:
    print '%s not a valid directory' % os.path.dirname(filename)
[/PHP]

---

### Post by Mr.popo on 2008-02-04
Thanks,

---

