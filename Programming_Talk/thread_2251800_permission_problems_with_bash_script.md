---
title: "permission problems with bash script??"
date: 2014-11-06
forum: Programming Talk
---

### Post by einstein**-7 on 2014-11-06
Just trying to run this simple bash script from my user\bin folder which basically converts a dng image sequence to exr.  

```
#!/bin/bash
#export TMPDIR=/media/......
for file in *.dng ; do
mkdir './Out/'$file'/'
/raw2dng $file './Out/'$file'/'
mkdir './Out/'$file'/EXR'
   for out in "./Out/$file/*.dng" ; do
      dcraw -c -w -H 1 -o 5 -q 3 -4 $out | convert - -depth 16 "./Out/$file/EXR/%06d.exr"
   done
done
```

here is the problem 

```
crush@crushmob:/$ dng2exr
bash: /usr/bin/dng2exr: Permission denied
crush@crushmob:/$ sudo dng2exr
sudo: dng2exr: command not found
```

any ideas why the command is suddenly not found??

---

### Post by steeldriver on 2014-11-06
Did you actually set the execute permission bits on the script?

```

sudo chmod +x /usr/bin/dng2exr

```

---

### Post by einstein**-7 on 2014-11-06
> **steeldriver said:**
> Did you actually set the execute permission bits on the script?

```

sudo chmod +x /usr/bin/dng2exr

```

Ok this worked! still currios as to why the command cant be found under a sudo command if the script dosn't have root execute permission..  I realize this should probably be in the coding section but its not creating dirrectories correctly. 
Script below and errors.

```
#!/bin/bash
#export TMPDIR=/media/......
for file in *.dng ; do
mkdir './Out/'$file'/'
/dng2exr $file './Out/'$file'/'
mkdir './Out/'$file'/EXR'
   for out in "./Out/$file/*.dng" ; do
      dcraw -c -w -H 1 -o 5 -q 3 -4 $out | convert - -depth 16 "./Out/$file/EXR/%06d.exr"
   done
done
```

```
crush@crushmob:~/Videos$ dng2exr
mkdir: cannot create directory ‘./Out/Camera_1_2014-11-05_1746_C0000_000000.dng/’: No such file or directory
/usr/bin/dng2exr: line 5: /dng2exr: No such file or directory
mkdir: cannot create directory ‘./Out/Camera_1_2014-11-05_1746_C0000_000000.dng/EXR’: No such file or directory

```

Not sure why it cant create the directory as a sudo call is the same.. I understand what the "mkdir" line do but not sure what this line is doing??

 ```
/dng2exr $file './Out/'$file'/' 
```

---

### Post by Bucky Ball on 2014-11-06
*Thread moved to **Programming Talk**.*

... and so it was ...

If your original issue is fixed you are perhaps best to mark this thread as solved and post another with a title _specific_ to your exact issue. You will get more mileage. Good luck.

---

### Post by matt_symes on 2014-11-07
Hi

Mkdir will fail if any intermediate directories do not exist; in this case the directory ./Out maybe ?

Try mkdir with the -p switch.

```
mkdir -p ....
```

Is that the problem ?

Kind regards

---

