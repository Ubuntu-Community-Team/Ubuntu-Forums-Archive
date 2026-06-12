---
title: "Ubuntu Bash Script changing file names chronologicaly"
date: 2012-11-30
forum: Programming Talk
---

### Post by Strahd on 2012-11-30
I have this bash script where I am trying to change all *.txt files in a directory to their date of last modification. This is the script:

> #!/bin/bash
# Renames the .txt files to the date modified
# FROM: foo.txt  Created on: 2012-04-18 18:51:44
# TO:    20120418_185144.txt
for i in *.txt
do
mod_date=$(stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g')
mv "$i" "$mod_date".txt
done
The error I am getting is:

renamer.sh: 6: renamer.sh: Syntax error: word unexpected (expecting "do")
Any help would be greatly appreciated. Thank you for your time.

---

### Post by gnusci on 2012-11-30
your last part is wrong:

sed 's/[: -$

---

### Post by Strahd on 2012-11-30
> **gnusci said:**
> your last part is wrong:

sed 's/[: -$Sorry about that. Fixed.

---

### Post by papibe on 2012-12-01
Hi Strahd. Welcome to the forums ):P

I think it would be much simpler if you get the timestamp format, and past it on to 'date'. 'date' can handle many time and date formats.

For instance:
```
$ stat --format %Y  exclude.txt
1331017133

$ date -d @$(stat --format %Y  exclude.txt) +%F
2012-03-06

$ date -d @$(stat --format %Y  exclude.txt) +%Y%m%d_%H%M%S
20120306_005853

```
Regards.

---

### Post by gnusci on 2012-12-01
or try

mod_date=`stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g'`

---

### Post by Strahd on 2012-12-01
> **papibe said:**
> Hi Strahd. Welcome to the forums ):P

I think it would be much simpler if you get the timestamp format, and past it on to 'date'. 'date' can handle many time and date formats.

For instance:
```
$ stat --format %Y  exclude.txt
1331017133

$ date -d @$(stat --format %Y  exclude.txt) +%F
2012-03-06

$ date -d @$(stat --format %Y  exclude.txt) +%Y%m%d_%H%M%S
20120306_005853

```
Regards.I am new at this, I would appreciate it if you could you show me how that code would go in the bash file.

---

### Post by Strahd on 2012-12-01
> **gnusci said:**
> or try

mod_date=`stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g'`I tried it, but still get the same error.

---

### Post by gnusci on 2012-12-01
Run the following command and post the output

$ ls -lrt renamer.sh

---

### Post by Strahd on 2012-12-01
> **gnusci said:**
> Run the following command and post the output

$ ls -lrt renamer.sh
> -rwxr-xr-x 1 root root 564 Dec  1 05:19 renamer.sh
Done.

---

### Post by papibe on 2012-12-01
> **Strahd said:**
> I am new at this, I would appreciate it if you could you show me how that code would go in the bash file.

Sure thing:
```
#!/bin/bash
for file in *.txt; do
    mod_date=$(date -d @$(stat --format %Y  "$file") +%Y%m%d_%H%M%S)
    mv -iv "$file" "$mod_date".txt
done
```
Let us know how it goes.
Regards.

---

### Post by Strahd on 2012-12-01
> **papibe said:**
> Sure thing:
```
#!/bin/bash
for file in *.txt; do
    mod_date=$(date -d @$(stat --format %Y  "$file") +%Y%m%d_%H%M%S)
    mv -iv "$file" "$mod_date".txt
done
```
Let us know how it goes.
Regards.Thank you. I get the same error as before:

> renamer.sh: 5: renamer.sh: Syntax error: word unexpected (expecting "do")

---

### Post by papibe on 2012-12-01
That is strange. That code works on my machine.

It could be a dirty character on the file? Try copying and pasting this code on a new file (different name).

Let us know how it goes.
Regards.

---

### Post by Strahd on 2012-12-01
> **papibe said:**
> That is strange. That code works on my machine.

It could be a dirty character on the file? Try copying and pasting this code on a new file (different name).

Let us know how it goes.
Regards.Still no luck.
>  sudo sh Namer.sh
Namer.sh: 2: Namer.sh: Syntax error: word unexpected (expecting "do")

---

### Post by Vaphell on 2012-12-01
are you sure you have **do** there, in next line or after ;?

```
**$ cat mr.sh**
#!/bin/bash
[COLOR="Red"]for i in *.txt[/COLOR]
  mod_date=$(stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g')
  echo mv "$i" "$mod_date".txt
done 
**$ sh ./mr.sh **
./mr.sh: 3: Syntax error: word unexpected (expecting "do")


**$ cat mr.sh**
#!/bin/bash
[COLOR="Red"]for i in *.txt do[/COLOR]
  mod_date=$(stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g')
  echo mv "$i" "$mod_date".txt
done 
**$ sh ./mr.sh **
./mr.sh: 3: Syntax error: word unexpected (expecting "do")


**$ cat mr.sh**
#!/bin/bash
[COLOR="Blue"]for i in *.txt
do[/COLOR]
  mod_date=$(stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g')
  echo mv "$i" "$mod_date".txt
done 
**$ sh ./mr.sh** 
mv 20121201_084804.txt 20121201_084804.txt
mv 20121201_084809.txt 20121201_084809.txt


**$ cat mr.sh**
#!/bin/bash
[COLOR="Blue"]for i in *.txt; do[/COLOR]
  mod_date=$(stat --format %y "$i"|awk '{print $1"_"$2}'|cut -f1 -d'.'|sed 's/[: -]//g')
  echo mv "$i" "$mod_date".txt
done 
**$ sh ./mr.sh**
mv 20121201_084804.txt 20121201_084804.txt
mv 20121201_084809.txt 20121201_084809.txt
```

besides, when you write bash script, run it with bash, not sh. Or make the script executable
```
chmod +x script.sh
```
and run it with
```
./script.sh
```

---

### Post by Lars Noodén on 2012-12-01
> **papibe said:**
> Sure thing:
```
#!/bin/bash
for file in *.txt; do
    mod_date=$(date -d @$(stat --format %Y  "$file") +%Y%m%d_%H%M%S)
    mv -iv "$file" "$mod_date".txt
done
```
Let us know how it goes.
Regards.

I've not seen the @$( ) before.  What does it mean?

---

### Post by Vaphell on 2012-12-01
> I've not seen the @$( ) before. What does it mean? 
nothing
it's @ + $()

```
$ LANG=C date -d 111111111
Sat Nov 11 00:00:00 CET 11111
$ LANG=C date -d @111111111
Tue Jul 10 01:11:51 CET 1973

```
apparently @ means seconds from 1970-01-01

---

### Post by Lars Noodén on 2012-12-01
> **Vaphell said:**
> nothing
it's @ + $()

```
$ LANG=C date -d 111111111
Sat Nov 11 00:00:00 CET 11111
$ LANG=C date -d @111111111
Tue Jul 10 01:11:51 CET 1973

```
apparently @ means seconds from 1970-01-01

Thanks.  I see the @ now in [date(1)](http://manpages.ubuntu.com/manpages/precise/en/man1/date.1.html) examples.

---

