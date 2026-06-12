---
title: "Converting a list to X columns of csv (&amp; wrapping a command around it)"
date: 2012-01-16
forum: Programming Talk
---

### Post by craigp84 on 2012-01-16
Hi All,

Random question, how would you convert a data file from a list like so:

```
12345
12346
12347
12348
12349
12350
... <snip 100+ lines> ...
```

to comma separated X columns across:

```
12345,12346,12347
12348,12349,12350
```

Why would you want to do this? The background to this is a business app which loads certain data into memory based on keys supplied via a cli utility. The cli utility’s syntax looks something like:

```
./app_loadkeys –axxx –bxxx –d 12345,12346,12347 –exxx
./app_loadkeys –axxx –bxxx –d 12348,12349,12350 –exxx
```

I need to share a simple way with others to handle this task, but i’m coming up short. Due to a political concern (boo! hiss!) i can’t simply drop a script in the relevant production user’s home dir for other staff to use (which would seem the best way to go to my mind).

So i need to find a solution to hand this over. I have the standard unix toolset available and also a wiki for storing a “How To” page explaining the process (preferably with copy / pasteable commands).

Here’s the way i do it interactively at the shell when necessary:

> 1.	Open the input data file (sample 1 above) in vim
2.	Record a macro “qq$a,[DEL][ESC]q” – which is recording a macro to register q, going to line end, enter append mode, append a “,”, delete the newline bringing the next line up onto this, exit to command mode, finish recording macro
3.	Undo the change made when recording that macro “u”
4.	Record another macro “qa3@qjq” – which is recoring a macro to register a, run macro in register q 3 times (for 3 columns), move cursor to line below, stop recording macro
5.	Undo the change made when recording that macro “u”.
6.	:set number
7.	<shift>g – go to end of file
8.	Quick mental sum, divide the number of lines in the file by 3 (if 3 columns) and add 1 to the result. Go back to the start of the file “1<shift>g”. Run the macro in register a that many times, i.e. “11@a”
9.	Then it’s simply a case of wrapping this csv data with the command line: “:%s/^/.\/app_loadkeys -axxx -bxxx –exxx –d /”

Although that flows perfectly logically at the shell and should be easy to memorise after a few runs through, the description of how to do it reads horribly and is totally confusing if the user is not experienced with vim. It’s also a bit long winded for a task they can expect to repeat semi-frequently.

I was thinking a copy / pastable command line would be an improvement for usability, perhaps:

```
tr '\n' ',' < imnts.list | sed 's#,\?\([0-9]\+\)\(,[0-9]\+\)\?\(,[0-9]\+\)\?#./app_loadkeys -axxx -bxxx -d \1\2\3 -exxx\n#g'
```

However i think that cmd line looks v daunting for an inexperienced user. What happens if the process changes in future? It’s not very maintainable, for example sometimes they will want to submit 4 keys at a time instead of 3, or 10  keys at a time. I could list out on the wiki page a copy / pasteable command for each version and they copy the one for X keys at a time as they need. Like i say, i feel i’m coming up short here.

Wish i could just drop a script in place to handle this, would take 20 mins and be done with for life.

How would you solve this? Any inspiration greatly welcomed!

---

### Post by dethorpe on 2012-01-16
Indeed is awkward not being able to install a script on the target server.
 
If the users have there own PC's or workstations can you provide a script or batch file that runs on those and issues the actual command line to the server using rsh or ssh? 
 
Users would just need to store the script on thier own boxs, then run it and just type in their user/password on the remote UNIX server? Could even host the script in a comon network share maybe so they didn't need thier own copy and would be easier to do upgrades.
 
If the number of keys per line can change then that could be a parameter to the script, maybe with 3 as the default.

---

### Post by Vaphell on 2012-01-16
splitting into columns (using tmp file)

```
#!/bin/bash

if(( $# != 0 ))
then
  cols=$1
else
  cols=3
  echo 'no parameter given, using default value'
fi
echo number of columns: $cols

i=1;
while read ln
do
  if(( i%cols==0 ))
  then
    echo "${ln}"
  else
    echo -n "${ln},"
  fi
  ((i++))
done < in.txt > tmp.csv


while read ln
do
  echo csv row: "${ln}"
done < tmp.csv
```
test on a sample file with rows 1-12:
```
$ ./file2csv.sh
no parameter given, using default value
number of columns: 3
csv row: 1,2,3
csv row: 4,5,6
csv row: 7,8,9
csv row: 10,11,12
$ ./file2csv.sh 4
number of columns: 4
csv row: 1,2,3,4
csv row: 5,6,7,8
csv row: 9,10,11,12

```

---

### Post by ofnuts on 2012-01-16
> **craigp84 said:**
> Hi All,

Random question, how would you convert a data file from a list like so:

```
12345
12346
12347
12348
12349
12350
... <snip 100+ lines> ...
```to comma separated X columns across:

```
12345,12346,12347
12348,12349,12350
```Why would you want to do this? The background to this is a business app which loads certain data into memory based on keys supplied via a cli utility. The cli utility&#8217;s syntax looks something like:

```
./app_loadkeys &#8211;axxx &#8211;bxxx &#8211;d 12345,12346,12347 &#8211;exxx
./app_loadkeys &#8211;axxx &#8211;bxxx &#8211;d 12348,12349,12350 &#8211;exxx
```I need to share a simple way with others to handle this task, but i&#8217;m coming up short. Due to a political concern (boo! hiss!) i can&#8217;t simply drop a script in the relevant production user&#8217;s home dir for other staff to use (which would seem the best way to go to my mind).

So i need to find a solution to hand this over. I have the standard unix toolset available and also a wiki for storing a &#8220;How To&#8221; page explaining the process (preferably with copy / pasteable commands).

How would you solve this? Any inspiration greatly welcomed!

```

numargs=$1
numargs_minus_one=$(($numargs - 1))
tr '\n' ',' < $in | sed -re "s/(([[:digit:]]+,){$numargs_minus_one}[[:digit:]]+),/\1\n/g"

```numargs is the number of elements you want processed per run.

Basically, replace all LFs by commas, and then  replace every Nth comma by a LF

---

### Post by craigp84 on 2012-01-16
Many thanks for the replies.

> **dethorpe said:**
> 
If the users have there own PC's or workstations can you provide a script or batch file that runs on those and issues the actual command line to the server using rsh or ssh? 


Yes, that is a neat solution - nicely gets around the issue of not being able to install a script somewhere in the production user's $PATH, and the idea of a common maintainable script is a nice sweetener.

> **ofnuts said:**
> ```

numargs=$1
numargs_minus_one=$(($numargs - 1))
tr '\n' ',' < $in | sed -re "s/(([[:digit:]]+,){$numargs_minus_one}[[:digit:]]+),/\1\n/g"

```numargs is the number of elements you want processed per run.

Basically, replace all LFs by commas, and then  replace every Nth comma by a LF

I like the idea of improving maintainability here - it's much clearer how to adjust for X columns with this.

I also posted on unix.com and user jayan_jay came up with the below little gem:

```
paste -d',' - - - < infile | awk '{print "./app_loadkeys -axxx -bxxx -d "$0" -exxx"}'
```

Many thanks all!

---

### Post by sisco311 on 2012-01-16
In a POSIX shell you could do something like:
```
while read -r l1; do 
    read -r l2
    read -r l3
    printf '%s\n' "${l1},${l2},$l3"
done < file
```

Obviously, this is inconvenient if you need more columns.

So here is a script in which you can specify the number of columns:
```
#!/bin/sh

col=3
while read -r line; do
     i=1
     while test $((i<col)) = 1 && read -r next; do
         line="${line},$next"
         i=$(($i+1))
     done
     printf '%s\n' "$line"
done < file

```

---

