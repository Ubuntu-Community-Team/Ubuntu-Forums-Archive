---
title: "compare two file (please help me it's deadly urgent)"
date: 2010-11-16
forum: Programming Talk
---

### Post by wanna_try on 2010-11-16
I have many files with info about soft, installed on remote machines.
I need to compare this file with template (soft than must be installed) and output file must content info about software that's not installed.
```
template.txt
software_name1
software_name2
software_name3.1

```

```
workstation1_info.txt
software_name3.2
Lantronix
..any other software
software_name1

```

output must be software_name2, becouse it is not installed, but software_name3.2 is good enough becouse version is more than we need.
So, the task is to show lines that is in template and not in source, using simple regular expressions

I use grep
```
grep -vxf template source >out
```
or
```
grep -Fvf template source >out
```

But it shows me only lines that is in source and not in template etc...

I need so fast to solve this problem, becouse it is deadly urgent case.
Please help me.

---

### Post by ziekfiguur on 2010-11-17
It seems to me diff would do what you need. ```
$diff orig changed_file | grep -r '^>*.'
``` would show only the lines that are in changed_file but not in orig

---

### Post by wanna_try on 2010-11-17
that does not work properly

I show you what I have and what I need

template
[SIZE="2"]```
McAfee AntiSpyware Enterprise Module;8.7.0.130
MySQL ODBC 3.51 Driver;03.51.05 - Gamma
Windows XP Service Pack 3
```[/SIZE]

source
```
[SIZE="2"]McAfee AntiSpyware Enterprise Module;8.7.0.129
Windows XP Service Pack 3;20080414.175805
McAfee VirusScan Enterprise
Altiris Version: 6.9.430.0
[/SIZE]
```

output must be
```
McAfee AntiSpyware Enterprise Module;8.7.0.130
MySQL ODBC 3.51 Driver;03.51.05 - Gamma
```


McAfee AntiSpyware Enterprise Module;8.7.0.130 - becouse version in source is older
MySQL ODBC 3.51 Driver;03.51.05 - Gamma - becouse it is not in  source.
Or any other way, I need just point on mismatch

The way pravin27 supposed is pretty good

```
 awk -F"." 'NR==FNR{a[$1]++;next} !a[$1]' source template.txt
```

But it is not show me mismatch in version, only lines that are not in source

---

### Post by ziekfiguur on 2010-11-17
Both my pravin27's version and mine also print
```
Windows XP Service Pack 3
```since it's followed by a different version number.

If you pipe my command through sed to remove the leadin `> ' I think you get the right output.

```
diff source template | grep -r '^>.*' | sed -e 's/^> //'
```gives 
```
McAfee AntiSpyware Enterprise Module;8.7.0.130
MySQL ODBC 3.51 Driver;03.51.05 - Gamma
Windows XP Service Pack 3
```

---

### Post by wanna_try on 2010-11-17
Thanks, I use it but pravin wrote another solution 
awk -F";" 'NR==FNR{a[$1]=$2;next} !a[$1] ||a[$1] < $2 ' source template.txt

It's totally what I need.
Another question how to write program file with this script??

---

