---
title: "Need help with Bash script to parse text file"
date: 2010-03-10
forum: Programming Talk
---

### Post by jamefarm on 2010-03-10
I'm writing a bash file that pulls an html file off the web then converts it to a text file, collects the information I need and puts it in a csv.  I need to pull certain elements off of most of the lines in the text file.  As an example, here are a few lines from the text file:

   ABC.L   ABCAM  Interim 2009/2010 ABCAM Earnings Release  n/a  n/a  n/a  9-Mar
   ACAD   ACADIA PHARMACEUTICALS INC  Q4 2009 ACADIA PHARMACEUTICALS INC Earnings Release  -$ 0.19  n/a  -$ 0.38  9-Mar AMC
   A036550.KS   ACE DIGITECH CO LTD  Q4 2009 ACE DIGITECH CO LTD Earnings Release  n/a  n/a  n/a  9-Mar 1:40 AM
   AMS.L   ADVANCED MEDICAL SOLUTIONS GROUP  Preliminary 2009 ADVANCED MEDICAL SOLUTIONS GROUP Earnings Release  n/a  n/a  n/a  9-Mar BMO


What I need are the symbol, the company name, estimate, actual, previous year, and date.  using the first line as an example, what I need is:
ABC.L,ABCAM,n/a,n/a,n/a,9-Mar
ACAD,ACADIA PHARMACEUTICALS INC,-0.19,n/a,-0.38,9-Mar
etc...

Any thoughts?

---

### Post by DaithiF on 2010-03-10
Hi,
is there a delimiter (e.g. tab character) between the fields?  its not clear from the text posted if there is or isn't.  If there is then its fairly straightforward -- e.g. use awk or cut to get the fields you want.

If there isn't a delimiter then I would suggest you go back to the process that converts from html to text and change it so that there is enough information left after the process to distinguish the fields from one another.  Otherwise it becomes guesswork as to where a particular field may start or end.

---

### Post by jamefarm on 2010-03-10
The fields are separated with 2 spaces, would that be enough for awk or cut?

---

### Post by DaithiF on 2010-03-10
> The fields are separated with 2 spaces, would that be enough for awk or cut? 
awk, yes,  cut, no.

```
$ awk -F'  ' '{ printf "%s,%s,%s,%s,%s,%s", $1, $2, $4, $5, $6, $7; }'  testfile
ABC.L,ABCAM,n/a,n/a,n/a,9-Mar

```

---

### Post by jamefarm on 2010-03-10
Thanks for the help.  I just noticed in the converted text file that there is a tab between the stock symbol and the company name.

ABC.L<tab>ABCAM

all other fields are separated by double spaces.  How would the command change to account for this?

---

### Post by DaithiF on 2010-03-10
you can't have 2 separate delimiters, but you could do something like this:
```
$ awk -F'  ' '{ sub("\t", ",", $1); printf "%s,%s,%s,%s", $1, $2, $4, $5; }'  testfile
ABC.L,ABCAM,Interim 2009/2010 ABCAM Earnings Release,n/a,n/a

```

---

### Post by geirha on 2010-03-10
> **DaithiF said:**
> you can't have 2 separate delimiters, but you could do something like this:
```
$ awk -F'  ' '{ sub("\t", ",", $1); printf "%s,%s,%s,%s", $1, $2, $4, $5; }'  testfile
ABC.L,ABCAM,Interim 2009/2010 ABCAM Earnings Release,n/a,n/a

```

Yes you can. The -F argument takes a regular expression.

```
awk -F '  |\t' ...
```

---

### Post by DaithiF on 2010-03-10
> **geirha said:**
> Yes you can. The -F argument takes a regular expression.

```
awk -F '  |\t' ...
```
nice, thanks.

---

### Post by jamefarm on 2010-03-10
Here's what ended up working:

awk -F '\\t|  +' -vOFS=, '{gsub(/\$ /,"");print$2,$3,$5,$6,$7,$8}'

Thanks for the help guys!!!

---

