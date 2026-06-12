---
title: "[SOLVED] copying a file to floppy?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by lwhitney on 2008-10-20
basic question i think...what's the difference, if any, in the following 2 commands:

cat 'some file' >/dev/fd0

and 

cat 'some file' > /dev/fd0

does a space after the '>' affect the outcome?

---

### Post by Dr Small on 2008-10-20
Neither will write the file to the device, although I could be wrong. Why don't you mount the floppy and then add your files to it?

---

### Post by jerome1232 on 2008-10-20
there is no difference between the commands but I believe dr small is correct about it not writing to the floppy.

offtopic

I always got a kick out of cat 'somelargfile' > /dev/dsp

---

### Post by bodhi.zazen on 2008-10-20
Why not copy with the cp command ?

```
cp some_file /media/floppy/some_file
```

Otherwise, no in this example, the space has no effect on the command.

---

### Post by bumanie on 2008-10-20
As far as I know 'cat' will 'print' to stdout, but is not able to copy files. You would be better off using the cp (copy) command. I believe the first entry without the space between > would not work if using a correct command like cp - as far as I know, there needs to be a space.

---

### Post by lwhitney on 2008-10-20
thanks for the input

---

