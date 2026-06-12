---
title: "Bash script to make .xml files out of raw text files"
date: 2012-03-11
forum: Programming Talk
---

### Post by Noobus on 2012-03-11
I have been stuggeling with this problem for a few hours now and cant find anything that will work. I have 2 large files with data wich looks like this

```
Boliden
ERS
Astra
ORDF
Lenna
OMBUD
Volvo
LED
```
and the 2nd one looks like this
```
Boliden
ERS
2011-01-01
2012-01-10
Astra
ORDF
2009-01-01
2012-12-31
Lenna
OMBUD
2002-06-15
2006-01-01
Volvo
LED
2007-12-31
2010-12-01
```

Now how do I get that data wraped into tags?
like this
```
<COMPANY>Boliden</COMPANY>
<ROLE>ERS</ROLE>
<COMPANY>Astra</COMPANY>
<ROLE>ORDF</ROLE>
<COMPANY>Lenna</COMPANY>
<ROLE>OMBUD</ROLE>
<COMPANY>Volvo</COMPANY>
<ROLE>LED</ROLE>
```
And
```
<COMPANY>Boliden</COMPANY>
<ROLE>ERS</ROLE>
<STARTDATE>2011-01-01</STARTDATE>
<STOPDATE>2012-01-10</STOPDATE>
<COMPANY>Astra</COMPANY>
<ROLE>ORDF</ROLE>
<STARTDATE>2009-01-01</STARTDATE>
<STOPDATE>2012-12-31</STOPDATE>
<COMPANY>Lenna</COMPANY>
<ROLE>OMBUD</ROLE>
<STARTDATE>2002-06-15</STARTDATE>
<STOPDATE>2006-01-01</STOPDATE>
<COMPANY>Volvo</COMPANY>
<ROLE>LED</ROLE>
<STARTDATE>2007-12-31</STARTDATE>
<STOPDATE>2010-12-01</STOPDATE>
```

---

### Post by ofnuts on 2012-03-11
The frst file has no purpose since the same data is available in the second one. Looks like a good job for awk:
```

awk 'NR%4==0 {print "<company>"$0"</company>"}; NR%4==1 {print "<role>"$0"</role>"};NR%4==2 {print "<startdate>"$0"</startdate>"}; NR%4==3 {print "<stopdate>"$0"</stopdate>"}; '

```

---

### Post by codemaniac on 2012-03-11
> **Noobus said:**
> 
```
Boliden
ERS
Astra
ORDF
Lenna
OMBUD
Volvo
LED
```

Now how do I get that data wraped into tags?
like this
```
<COMPANY>Boliden</COMPANY>
<ROLE>ERS</ROLE>
<COMPANY>Astra</COMPANY>
<ROLE>ORDF</ROLE>
<COMPANY>Lenna</COMPANY>
<ROLE>OMBUD</ROLE>
<COMPANY>Volvo</COMPANY>
<ROLE>LED</ROLE>
```


for the first one , redundant though . :)

```
awk '{if(NR%2 == 1){print "<company>"$1"</company>"}else print "<ROLE>"$1"</ROLE>"}' input_file
```

---

### Post by Noobus on 2012-03-11
> **ofnuts said:**
> The frst file has no purpose since the same data is available in the second one. Looks like a good job for awk:
```

awk 'NR%4==0 {print "<company>"$0"</company>"}; NR%4==1 {print "<role>"$0"</role>"};NR%4==2 {print "<startdate>"$0"</startdate>"}; NR%4==3 {print "<stopdate>"$0"</stopdate>"}; '

```
Both files have there purpuse, this is made up data, but it looks like the real data, which is different in the 2 files :)

I have never used awk before, sed have been enough for all my needs so far. I tried your code, but it dosn't work. Also have the same problem with the code codemaniac provided..

```
$ cat tmp 
Boliden
ERS
2011-01-01
2012-01-10
Astra
ORDF
2009-01-01
2012-12-31
Lenna
OMBUD
2002-06-15
2006-01-01
Volvo
LED
2007-12-31
2010-12-01

```
```
$ awk 'NR%4==0 {print "<company>"$0"</company>"}; NR%4==1 {print "<role>"$0"</role>"};NR%4==2 {print "<startdate>"$0"</startdate>"}; NR%4==3 {print "<stopdate>"$0"</stopdate>"}; ' tmp
</role>oliden
</startdate>RS
</stopdate>011-01-01
</company>012-01-10
</role>stra
</startdate>RDF
</stopdate>009-01-01
</company>012-12-31
</role>enna
</startdate>MBUD
</stopdate>002-06-15
</company>006-01-01
</role>olvo
</startdate>ED
</stopdate>007-12-31
</company>010-12-01

```

---

### Post by codemaniac on 2012-03-11
Both the awklets are giving the desired output on my system .
Try with the --posix option with awk .something like below .
Also i am suspecting if you have edited this tmp file in windows environment , it may contain some undesired line feeds.
If each record in your sample tmp file does not contain spcaes or tabs , you can use $1 , instead of $0 like below


```
/usr/bin/awk --posix 'NR%4==0 {print "<company>"$1"</company>"}; NR%4==1 {print "<role>"$1"</role>"};NR%4==2 {print "<startdate>"$1"</startdate>"}; NR%4==3 {print "<stopdate>"$1"</stopdate>"}; ' tmp
```

---

### Post by Noobus on 2012-03-11
I'v tried it with the --posix option and still have the same problem. Tried in a ubuntu & dabian VM, the text file is generated in the debian environment but changing $0 to $1 gives the same result :(

---

### Post by Vaphell on 2012-03-11
methinks you got carriage returns (\r) there
check this out:
```
$ echo $'Boliden  
ERS  
2011-01-01  
2012-01-10' | awk 'NR%4==0 {print "<company>"$0"</company>"}; NR%4==1 {print "<role>"$0"</role>"};NR%4==2 {print "<startdate>"$0"</startdate>"}; NR%4==3 {print "<stopdate>"$0"</stopdate>"}; '
<role>Boliden</role>
<startdate>ERS</startdate>
<stopdate>2011-01-01</stopdate>
<company>2012-01-10</company>

$ echo $'Boliden\r
ERS\r
2011-01-01\r
2012-01-10\r' | awk 'NR%4==0 {print "<company>"$0"</company>"}; NR%4==1 {print "<role>"$0"</role>"};NR%4==2 {print "<startdate>"$0"</startdate>"}; NR%4==3 {print "<stopdate>"$0"</stopdate>"}; '
</role>oliden
</startdate>RS
</stopdate>011-01-01
</company>012-01-10

```
looks familiar?

to confirm```
 sed 's/\r/*** OMG OMG CARRRIAGE RETURN! ***/' tmp
``` ;-)

---

### Post by Noobus on 2012-03-11
> **Vaphell said:**
> methinks you got carriage returns (\r) thereOHH my god!! there ware loads of them in there. Gone now. Thanx Vaphell, codemaniac & ofnuts!

---

### Post by ofnuts on 2012-03-11
> **Noobus said:**
> I'v tried it with the --posix option and still have the same problem. Tried in a ubuntu & dabian VM, the text file is generated in the debian environment but changing $0 to $1 gives the same result :($0: whole record, $1: first token in record, since you have only one token per record, this is the same (unless you have trailing spaces...)

---

### Post by Arndt on 2012-03-12
Since you ask for a bash script, how about this:

```
while read x; do
    read y
    echo "<company>$x</company>"
    echo "<role>$y</role>"
done

```

---

### Post by Some Penguin on 2012-03-12
...and if a name contains an ampersand or angle bracket?

---

### Post by ofnuts on 2012-03-13
> **Some Penguin said:**
> ...and if a name contains an ampersand or angle bracket?Or a quote or an apostrophe....  Then change them with a SED stage in the pipe before AWK.

---

