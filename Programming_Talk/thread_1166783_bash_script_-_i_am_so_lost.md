---
title: "bash script - i am so lost"
date: 2009-05-22
forum: Programming Talk
---

### Post by abraxas334 on 2009-05-22
Hi, I have quite a complex(or at least to me it seems complex) bash script problem. the script is used for submitting to a cluster (but serial job).
so i use something like this to submit my job:
qsub -N name script.sh

My script looks like this at the moment:
script.sh:
```

echo "Running on 'hostname'"
cd workDir
./executablefile fileX
sleep 20

```
Now the problem: I need to run the executable 200 times but each time a different file needs to be read in. so obviously i don't want to do this manually.
to be more precise the commandline takes one file argument but the program reads another file in: fileX and fileY
what i want my bash script to do in some kind of pseudo code is this:

```

for int i=0; i<NumFiles; i++
cp fileX.i fileX
cp fileY.i fileY
./executable fileX
//wait till executable has finished running (takes a couple of minutes but changes depending on the files read)then copy next file.i

```

any help would be greatly appreciated as i have no clue about bash scripting and i can barely understand the very simple submission script i am using at the moment.
Thanks

---

### Post by k2t0f12d on 2009-05-22
```
echo "Running on 'hostname'"
cd workDir
./executablefile fileX
sleep 20

for int i=0; i<NumFiles; i++
cp fileX.i fileX
cp fileY.i fileY
./executable fileX
//wait till executable has finished running (takes a couple of minutes but changes depending on the files read)then copy next file.i
```

```
index=0
while test "$index" -le "$numFiles"; do

  cp -v fileX.${index} fileX
  cp -v fileY.${index} fileY
  ./executable fileX
  sleep $n      # where $n is replaced by the number of seconds to sleep
  (( index+=1 ))

done
```

**see also [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

