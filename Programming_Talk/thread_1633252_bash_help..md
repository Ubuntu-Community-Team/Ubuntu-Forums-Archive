---
title: "bash help."
date: 2010-11-29
forum: Programming Talk
---

### Post by Drenriza on 2010-11-29
Hi all.

I have made a script, that helps me keep track of some movies i have on an external server. So far i get information such as follows
> DeletedRotation - FILM 9 /path/movie1[FONT=Verdana]
[/FONT]NewRotation - FILM 11 /path/movie1My "problem" is as you might notice, that if a movie just changes it's slot number (equal to it is moved, in the order it is presented) the script thinks that the movie has been deleted, and then it thinks that the same movie is a new movie.

How can i make the script output that the movie just has been moved?

The way it works now is that.
I have a baseline file (that only gets updated once a year)
and i have a "new movie file" which gets updated once a month.
These to files then gets compared (diff) to see what is new and what is old.

Hope it makes sense.
Kind Regards.

---

### Post by debsankha on 2010-11-29
I am not sure what you meant by 'rotation', but if all you want is  a list of new movies then why don't you simply save the output of ls in that directory periodically and see the diff between them?

---

### Post by Drenriza on 2010-11-29
> **debsankha said:**
> I am not sure what you meant by 'rotation', but if all you want is  a list of new movies then why don't you simply save the output of ls in that directory periodically and see the diff between them?

I already do that.

I have a baseline file (that only gets updated once a year)
 and i have a "new movie file" which gets updated once a month.
 These to files then gets compared (diff) to see what is new and what is old.
The problem is, that if i changes the order in the way the movies are presented. The script things that 

#1 is has been deleted
#2 is has been uploaded again.

And i end up with information like

> 
DeletedRotation - FILM 10 /path/movie #1
DeletedRotation - FILM 11 /path/movie #2
DeletedRotation - FILM 12 /path/movie #3
DeletedRotation - FILM 13 /path/movie #4
DeletedRotation - FILM 14 /path/movie #5
DeletedRotation - FILM 15 /path/movie #6
NewRotation - FILM 9 /path/movie #7
NewRotation - FILM 10 /path/movie #8
NewRotation - FILM 11 /path/movie #9
NewRotation - FILM 12 /path/movie #1
NewRotation - FILM 13 /path/movie #2
NewRotation - FILM 14 /path/movie #3
NewRotation - FILM 15 /path/movie #4
NewRotation - FILM 16 /path/movie #5
NewRotation - FILM 17 /path/movie #6So im wondering, how i can make it so the script can see that it has just been moved (got a new order value)

You can see that movies 1-6 is seen as both new and deleted. Because it just got moved in, in what order it is presented.
And only movies 7-9 is actually new movies.

---

### Post by debsankha on 2010-11-29
The solution depends on your actual code. 
You can try this for each line in the output of diff:
   if test "$(ls | grep $line)"; then echo $line>new_file;else echo 0; fi

---

### Post by Drenriza on 2010-11-30
> **debsankha said:**
> The solution depends on your actual code. 
You can try this for each line in the output of diff:
   if test "$(ls | grep $line)"; then echo $line>new_file;else echo 0; fi

What would that look like, if the part of the the script that contains the diff looks like this

```
if [ -s /path/Baseline ]; then
        echo "Baseline already exist, proceding with the rest of the script"
else
       cat /path/file |grep ^FILM* > /path/Baseline    
fi

##Step #2
cat /path |grep ^FILM* > /path/NewRotations

##Step #3
diff /path/Baseline /path/NewRotations | grep -E '^>|^<' > /path/NewRotationsResult
```

Edit.
I posted a part of the wrong script, my bad and i'm terribly sorry for those who have used time on this thread.
I hope you accept my apology.
And now it is the right script posted..
Kind regards

---

### Post by debsankha on 2010-11-30
So far as I can understand, the order of the files are changing because ls is sorting the output according to modification time (due to the -t). Just pipe the output of ls -lh to your NewMovies and Baseline files, then do plain diff.

Because the files are now sorted alphabetically, you shouldn't have any problem.

---

### Post by Vaphell on 2010-11-30
can't you use **grep -c <file>** ? it prints out how many times a given pattern occurs
if the result is 2 then obviously the file in question appears in both 'deleted' and 'new' => it's moved.

---

### Post by Drenriza on 2010-11-30
> **debsankha said:**
> So far as I can understand, the order of the  files are changing because ls is sorting the output according to  modification time (due to the -t). Just pipe the output of ls -lh to  your NewMovies and Baseline files, then do plain diff.

Because the files are now sorted alphabetically, you shouldn't have any problem.


i have done the -t in the ls because i want them sorted after how "old" the files are. So i get the newest at the top and oldest at the bottom.

And that makes the most sense in this case.

---

### Post by Drenriza on 2010-11-30
> **Vaphell said:**
> can't you use **grep -c <file>** ? it prints out how many times a given pattern occurs
if the result is 2 then obviously the file in question appears in both 'deleted' and 'new' => it's moved.

What would this look like in the script?

---

### Post by debsankha on 2010-11-30
This is a possible solution:
```

cat baseline | sort -k 8 > tempold
ls -lh path/ > tempnew
diff tempold tempnew | grep -E "^>" | sort -r -k 7,8 > newmovies

```

Modify according to your taste.

---

### Post by Drenriza on 2010-11-30
I dont get it.

---

### Post by Drenriza on 2010-12-06
bump.

Anyone who can help me?

---

### Post by Arndt on 2010-12-06
> **Drenriza said:**
> bump.

Anyone who can help me?

Well, does the suggestion work?

---

### Post by Drenriza on 2010-12-06
post 

#4 I dont understand the suggestion, on how to implement it
#5 An output of the code i use.
#10 I dont understand the ls -lh part of the command, and their fore got stuck on how to implement it into the rest of the script.

I posted an output of the code in the hope that when an suggestion was made, people would use the code example and post their suggestion into it. So i wodent have to edit it or only edit it to a minimum.

I'm not a programmer, and have very very limited knowledge about programming in any regard. So in alot of examples i need to see how people would implement their suggestion, instead of just posting their suggestion or else i cannot "see" it.

Kind Regards

---

### Post by apmcd47 on 2010-12-06
Personally I would create a temporary file from the baseline file, which is made up of file paths of the film files, sorted into alphabetical order. I would then make a second such file of the current "snapshot" of your server. Now you can use comm:
```
comm -1 filea fileb
```will NOT list lines unique to filea;
```
comm -2 filea fileb
```will NOT list lines unique to fileb;
```
comm -3 filea fileb
```will NOT list common lines.

Use the output of *comm -23* to list deleted files and of *comm -13[I]*[/I] to list new files.

Andrew

---

### Post by debsankha on 2010-12-09
I suggest this algorithm:
```

[LIST=1]
[*]save the output of ls -lt in the file baseline once.
[*]after a month or whatever, save the output of ls -lh in the file tempnew.
[*]sort the file baseline alphabetically and save it in tempold
[*]the diff between tempold and tempnew gives you the list of new movies.
[/LIST]

```

And here's the code: 
```

cat baseline | sort -k 8 > tempold
ls -lh path/ > tempnew
diff tempold tempnew | grep -E "^>" | sort -r -k 7,8 > newmovies

```

Hope this helps:p

---

### Post by Drenriza on 2010-12-10
> **debsankha said:**
> I suggest this algorithm:
```

[LIST=1]
[*]save the output of ls -lt in the file baseline once.
[*]after a month or whatever, save the output of ls -lh in the file tempnew.
[*]sort the file baseline alphabetically and save it in tempold
[*]the diff between tempold and tempnew gives you the list of new movies.
[/LIST]

```And here's the code: 
```

cat baseline | sort -k 8 > tempold
ls -lh path/ > tempnew
diff tempold tempnew | grep -E "^>" | sort -r -k 7,8 > newrotations

```Hope this helps:p

I dont get the ls -lh part. Since in the script you dont ls any directories.
You only cat files. That creates baseline and newrotations.

Can you please explaine that part?

---

### Post by apmcd47 on 2010-12-10
Assuming your baseline and snapshot files look like this:
```
FILM 1 /home/drenriza/film1
FILM 2 /home/drenriza/film3
FILM 3 /home/drenriza/film4
FILM 4 /home/drenriza/film5

```
This is tested and works:
[PHP]#!/bin/sh

myname=${0##*/}

# clean up on exit
cleanup() {
   trap '' 0 1 2 3 15 19   # clear the trap so we don't get called twice
   /bin/rm -f "${myname}*$$"
}
trap 'cleanup' 0 1 2 3 15 19

baseline=$1
latest=$2

oldfiles="${myname}old$$"
newfiles="${myname}new$$"
delfiles="${myname}del$$"
addfiles="${myname}add$$"

sed -e 's%^[^/]*%%' "${baseline}" | sort > ${oldfiles}   # just the paths
sed -e 's%^[^/]*%%' "${latest}"   | sort > ${newfiles}   # ditto


comm -23 ${oldfiles} ${newfiles} > ${delfiles}     # no longer in new
comm -13 ${oldfiles} ${newfiles} > ${addfiles}     # new files

grep -F -f ${delfiles} "${baseline}" | sed -e 's/^/Deleted: /'
grep -F -f ${addfiles} "${latest}"   | sed -e 's/^/Added: /'
[/PHP]

No expectations as to where a column may start, but an expectation that your pathnames all start with /

The sed commands remove the stuff before the pathnames; the comm commands get lines unique to the first file and the second file respectively and the greps list the lines affected.

Andrew

---

### Post by Drenriza on 2010-12-16
> **apmcd47 said:**
> Assuming your baseline and snapshot files look like this:
```
FILM 1 /home/drenriza/film1
FILM 2 /home/drenriza/film3
FILM 3 /home/drenriza/film4
FILM 4 /home/drenriza/film5

```This is tested and works:
[PHP]#!/bin/sh

myname=${0##*/}

# clean up on exit
cleanup() {
   trap '' 0 1 2 3 15 19   # clear the trap so we don't get called twice
   /bin/rm -f "${myname}*$$"
}
trap 'cleanup' 0 1 2 3 15 19

baseline=$1
latest=$2

oldfiles="${myname}old$$"
newfiles="${myname}new$$"
delfiles="${myname}del$$"
addfiles="${myname}add$$"

sed -e 's%^[^/]*%%' "${baseline}" | sort > ${oldfiles}   # just the paths
sed -e 's%^[^/]*%%' "${latest}"   | sort > ${newfiles}   # ditto


comm -23 ${oldfiles} ${newfiles} > ${delfiles}     # no longer in new
comm -13 ${oldfiles} ${newfiles} > ${addfiles}     # new files

grep -F -f ${delfiles} "${baseline}" | sed -e 's/^/Deleted: /'
grep -F -f ${addfiles} "${latest}"   | sed -e 's/^/Added: /'
[/PHP]No expectations as to where a column may start, but an expectation that your pathnames all start with /

The sed commands remove the stuff before the pathnames; the comm commands get lines unique to the first file and the second file respectively and the greps list the lines affected.

Andrew

Can you please explain a little of how the script works?
Thanks on advance,
Kind regards

EDIT
> FILM 1 /home/drenriza/film1
FILM 2 /home/drenriza/film3
FILM 3 /home/drenriza/film4
FILM 4 /home/drenriza/film5The path is /video/FILM1 the video folder lies in the root of the system. The FILM1 is a folder within the video folder that contains an .mpeg file.

at #5 their is an partial output of my script.

---

### Post by apmcd47 on 2010-12-24
> **Drenriza said:**
> Can you please explain a little of how the script works?
Thanks on advance,
Kind regards

EDIT
The path is /video/FILM1 the video folder lies in the root of the system. The FILM1 is a folder within the video folder that contains an .mpeg file.

at #5 their is an partial output of my script.

basically oldfiles, newfiles, addfiles and delfiles are temporary files created by the program and deleted when the cleanup function is called by normal termination or the invocation of kill.

The two sed commands strip the initial "FILM X" from each line of the baseline and latest files and the sort sorts the resulting lines into alphabetical order.

The comm commands take two files and outputs the lines from the files into three columns: Only in the left file; Only in the right file; Common to both files. The switches -1, -2 and -3 turn off one or more of those columns, so that the two commands I use:
[PHP]comm -23 ${oldfiles} ${newfiles} > ${delfiles}  
comm -13 ${oldfiles} ${newfiles} > ${addfiles} [/PHP]
result in two files containing (1) only paths found in the first file, ie those that have been deleted between the creation of the first and second files; and (2) only paths found in the second file: files added since the creation of the first file.

The *grep -F *commands do a literal search rather than a regular expression search, and the *-f file* option is used to pull the search patterns out of the named file.

Andrew

---

