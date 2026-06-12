---
title: "how to execute a program?"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by sense12 on 2013-03-23
actually,  i found this program in this web site  [http://web.eecs.utk.edu/~plank/plank/gflib/]("http://web.eecs.utk.edu/%7Eplank/plank/gflib/") ,but because i'm beginner in ubuntu Linux  i can not execute it,  thus any one can help me how i can make this program work .
i have problem particularly in execute ```
  rs_encode_file filename n m stem
```
and ```
 rs_decode_file stem 
```

---

### Post by Virtuality314 on 2013-03-23
Make sure that the binary is executable. To do this, right click rs_encode_file and click on Properties. Then go to the Permissions tab and make sure that ''Allow executing file as program" is checked.

---

### Post by r-senior on 2013-03-23
If you ran make to build it, the programs should be executable. Did you run make? Do you have files called rs_decode_file, etc.?

To execute an executable file in your current directory, you need to do it like this:

```
./rs_decode_file stem
```

---

