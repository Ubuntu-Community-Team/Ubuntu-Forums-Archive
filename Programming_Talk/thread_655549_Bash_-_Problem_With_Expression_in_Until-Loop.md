---
title: "Bash - Problem With Expression in Until-Loop"
date: 2008-01-01
forum: Programming Talk
---

### Post by Greasyfingers on 2008-01-01
I am writing my first bash script, and my brain is approaching meltdown. The script creates a config file with the following data in it:

PathCount=3
FilePath1=/path/to/bish
FilePath2=/path/to/bash
FilePath3=/path/to/bosh
...

There can be any number of FilePaths, and PathCount increases by one every time a new FilePath is added

If I do this:```
source /home/$USER/config.file
echo $FilePath1
```I get the expected result of /path/to/bish. But I want to find a way of referencing the FilePaths in a loop, eg:```
source /home/$USER/config.file
N=1
	until [ $N -gt $PathCount ] ; do
		echo $FilePathN
		let N+=1
	done
```where the desired result will be an output of the actual file paths, one for each iteration of the loop. Ie. $FilePathN is referencing the source file as if it was $FilePath1, then $FilePath2, $FilePath3, etc.

I tried all sorts of variations, but can't seem to get a working expression for $FilePathN which will reference the data in the config file. Is this possible? Am I approaching it the wrong way? Right now, my brain has gone gaga, so any help or nursing care would be greatly appreciated.

---

### Post by dwhitney67 on 2008-01-01
Define your list of files in an array, then access the array using your index N.  Note that the index for an array begins with 0, not 1.

---

### Post by ghostdog74 on 2008-01-01
you are writing your first bash script? Have you read any references or books regarding shell scripting?See [here]("http://www.ssuet.edu.pk/~amkhan/Linuxbooks/(ebook%20pdf)%20Teach%20Yourself%20Shell%20Programming%20in%2024%20Hours.pdf") for a start. After that [here ]("http://www.unix.org.ua/orelly/unix/sedawk/index.htm")and [here]("http://tldp.org/LDP/abs/html/") before you attempt anything else

---

### Post by stroyan on 2008-01-01
You can get the *FilePath$N* effect that you want using indirect expansion.
That uses a notation like ${!V} to access the shell variable named by the value of variable V.  (You will also need to use either typeset -i N or an explicit arithmetic evaluation when incrementing N.)```
source /home/$USER/config.file
N=1
until [ $N -gt $PathCount ]
do 
        fp=FilePath$N
        echo ${!fp}
        N=$((N+1))
done
```Another alternative is to use the eval keyword to reevaluate a line a second time after normal expansions complete.```
source /home/$USER/config.file
N=1
until [ $N -gt $PathCount ]
do 
        eval echo \$FilePath$N
        N=$((N+1))
done
```

---

### Post by stroyan on 2008-01-01
You can compress the loop code by using a bash ${!prefix@} construct that matches all variable
names that start with a particular prefix.  But it will be in alphabetic collation order instead of a
numeric sort by N.```
for v in ${!FilePath@};do echo ${!v};done
```

---

### Post by Greasyfingers on 2008-01-02
This is great; thanks all for your help.

It's 5:50am and I finally have it working as desired. I used the array method, as it seemed obvious once it was pointed out, but it was interesting to see so many alternatives.

Must sleep.
Thanks.

---

