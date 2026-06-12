---
title: "SCM scripts"
date: 2009-01-08
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-01-08
I want to write a Scheme script using the scm compiler, similar to a bash script or python script

---

### Post by jpkotta on 2009-01-09
Get scm.
```
sudo aptitude install scm
```

Create a script file.
```
#!/usr/bin/env scm

(print "Hello world.")
(quit)
```

Make it executable and run it.
```
chmod +x hello.scm
./hello.scm
```

---

### Post by Mr.Macdonald on 2009-01-09
Thank you,  I didn't know you needed the (quit)

---

### Post by nvteighen on 2009-01-09
Just a note: scm is a bit non-standard in a lot of stuff... take for example the 'print' procedure... But all Scheme implementations are rather that way, so, if you happen to deploy that code, you better state what implementation you used to write it...

(My FreeTruco is not Standard Scheme just because of MIT/GNU Scheme specific read-eval-print procedure... :()

---

