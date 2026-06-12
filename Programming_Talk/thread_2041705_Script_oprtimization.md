---
title: "Script oprtimization"
date: 2012-08-13
forum: Programming Talk
---

### Post by Srdjan01 on 2012-08-13
Hi guys,
I have this script that works, but sometimes I am experiencing performance issues due to this script.

```
#!/bin/sh
find /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/ -name '*lif' | xargs cp -t /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d/
sleep 60
find /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/ -name '*lif' | xargs cp -t /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_pdf/
sleep 60
find /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/ -name '*lif' | xargs rm
```

The reason find | xargs is used is the nubmer of files. Usually it is around 100 000 files, and cp cannot be used.

It is my belief that find puts pressure on the system. Could you somehow use 

```

for file in /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/*lif
do
...
```

or something else?

Thanks,
Srdjan

---

### Post by steeldriver on 2012-08-13
well it depends whether the .lif files are all in the top level  of the output_d_p7.4_perf directory, or whether you need to descend into any subdirs - unless the subdir structure is simple enough that you can just explictly loop over output_d_p7.4_perf/dir1/*.lif , output_d_p7.4_perf/dir2/*.lif etc.

If you need the 'find', you could try something like this which at least does not duplicate it

```
while read -d $'\0' file ; do

  cp "$file" /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d/

  cp "$file" /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_pdf/

done < <(find /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/ -name '*lif' -print0)
```

---

### Post by sisco311 on 2012-08-13
Inseatd of the second cp command and rm, you could simply mv the files. I'd try something like:
```
find /path -name '*lif' -exec sh -c 'cp -- "$@" /traget1 && mv -- "$@" /target2' _ {} +
```

---

### Post by spjackson on 2012-08-13
"find" can be a performance hit, but if the directory does not contain subdirectories , then it isn't significantly more expensive than simply globbing. However, you call "find" 3 times with the same parameters; it would be more efficient to call it once, storing the results in a temporary file which is then used as input to the 3 commands. (steeldriver's suggestion is better here.)

Your 2nd and 3rd commands copy then remove the files. If the source and target are on the same partition, it is more efficient to use 'mv', although there is a difference. As it stands, the files get a new timestamp, whereas mv preserves timestamps. So whether that is an option depends on your needs. If you need new timestamps, then mv & touch may be better than cp & rm.

There is a kernel limit in the total length of all the arguments that can be passed to a program. However, "for" isn't a program, and it is possible that bash may be able to cope with the globbing. If you can use "for", then that is an alternative to calling find 3 times.

It certainly used to be the case that processing very many files in a single directory was less efficient than processing the same number of files in smaller directories. I'm not sure to what extent this is still the case, but if it is possible to change how the files are created so that they are split into several directories, then this may also be worth considering.

As with all cases of performance optimisation, be sure to collect performance statistics, and base your changes on those statistics.

---

### Post by ofnuts on 2012-08-13
> **spjackson said:**
> Your 2nd and 3rd commands copy then remove the files. If the source and target are on the same partition, it is more efficient to use 'mv', although there is a difference. As it stands, the files get a new timestamp, whereas mv preserves timestamps. So whether that is an option depends on your needs. If you need new timestamps, then mv & touch may be better than cp & rm.
"cp -p" preserves timestamps.

---

### Post by spjackson on 2012-08-13
> **ofnuts said:**
> "cp -p" preserves timestamps.
True, but irrelevant. The OP is currently not using "cp -p".

---

### Post by ofnuts on 2012-08-13
> **Srdjan01 said:**
> Hi guys,
I have this script that works, but sometimes I am experiencing performance issues due to this script.

```
#!/bin/sh
find /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/ -name '*lif' | xargs cp -t /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d/
sleep 60
find /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/ -name '*lif' | xargs cp -t /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_pdf/
sleep 60
find /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/ -name '*lif' | xargs rm
```The reason find | xargs is used is the nubmer of files. Usually it is around 100 000 files, and cp cannot be used.

It is my belief that find puts pressure on the system. Could you somehow use 

```

for file in /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/*lif
do
...
```or something else?

Thanks,
Srdjan
If we get back to basics and I get it correctly:

for each '*.lif' file under /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_p7.4_perf/:

[LIST]
[*]create a copy in /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d/
[*]create a copy in /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_pdf/
[*]remove the file from the original location
[/LIST]
First, this code has a huge problem, worsened by the "sleep 60" between each call: if a file appears in the subdirectory while the script runs, it may be missed by the 1st, or 1st and 2nd, "find", and be removed without being copied (if you have control over what puts files there then you should make it put the files in the right place...). 

So for correctness reasons alone you have better run "find" only once. After that you can either store the results in a list file and process the list file once with each operation, or write a side script that does all three ops on each file and use that script directly in the find.

Like others I don't think the cp+rm is so efficient, if the files are in the same filesystem (and they look like), then one of the  "cp" can be replaced by an "mv", and if you replace the second copy by a link to the first one (ie, /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_pdf/ contains links to the files in /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d/), you will save disk space and execution time. In fact, if /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d_pdf/ always happen to contain the same files as /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d/, it could be made a link to /appl/virtuo/gways/spool/ericsson/UTRAN/p7/output_d/ and you would only have to deal with one move.

---

### Post by Srdjan01 on 2012-08-15
Thanks guys, you have been very helpful.

---

