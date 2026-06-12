---
title: "placing text / output"
date: 2011-04-04
forum: Programming Talk
---

### Post by Drenriza on 2011-04-04
Hi all.

If i have one command ```
ls -laht |awk '{print $9 }'
``` that gives me this output
```
test3
test2
test1

```

and another command ```
date | awk '{print $1 " " $2 " " $3 " " $4}'
```
that gives this output
```
Man 4 Apr 2011
```

How can i copy plaste the date behind the test1 - test3? so i would get an output like (from a terminal)
```
test1 Man 4 Apr 2011
test2 Man 4 Apr 2011
test3 Man 4 Apr 2011
```
Thanks all.
Kind regards.

---

### Post by kurum! on 2011-04-04
Do not use ls to parse file names. Use shell expansion
```

for file in *
do
  echo $file $(date ... )
done

```

I like to use Ruby for my scripting
```

$ ruby -rdate -e 'Dir["*"].each{|x| puts "#{x} #{DateTime.now}"}' file


```

---

### Post by Drenriza on 2011-04-04
is says
```
date: invalid date `...'
```
how do i solve this?

---

### Post by Vaphell on 2011-04-04
you want current date or timestamps of listed objects?
date --help will tell you that 'Mon 4 Apr 2011' can be done with
```
date '+%a %d %b %Y'
```

also $9 on my system is -> from the symlink (if exists), otherwise null
if name then it should be $8 but it will fail in case of space in name

name + current date formatted would be
```
d=$( date '+%a %d %b %Y' ); ls -halt | awk -v d="$d" '{print $8, d }'
```

if you want timestamps of objects, ls accepts custom formats compatible with date command, ```
ls -halt --time-style='+%a %d %b %Y'
``` will format dates to the desired format

---

### Post by Drenriza on 2011-04-05
Thanks Vaphell, worked like a charm.

I must say, i get a bit jealous when i see good code. I would like to be better myself to do stuff like so, but where to start is mind boggeling.

---

### Post by Vaphell on 2011-04-05
where to start?

1. **--help** and man
Try --help on every command you use. 95% supports that switch and will respond with a wealth of information. Even well known tools are commonly used in a way that takes advantage of only few core features, but very often these tools offer amazing functionality that is not widely known. If you make an effort to dig a bit deeper, you can take huge shortcuts where you'd have to use dozen of tools to achieve the same result.

2. Read every bash scripting related thread you see on UF (or any other linux related forum you read), even if the problem is way above your head. There is a big chance you will gain wisdom points, especially when bash gurus like sisco311 overpower the thread with their mad skillz :)

3. google + some combination of 'bash', 'linux', <cmd>, <some atomic operation to perform> - quite obvious. You get tutorials, examples, forum threads where people discuss how to solve problems from different angles and why a given solution is better than the others.

---

### Post by Drenriza on 2011-04-06
Vaphell your a knowledged / experienced person. Maybe you know this one to.

In a script i have. I create a baseline file (static file) and a NewFile (dynamic file)
i then use a command
```
diff $path/Baseline $path/NewFile | grep -E '^>|^<' > $path/NewFileResults
```

I do this to see what files are new and what files are old on my system.
This was also where i used your command 
```
d=$( date '+%a %d %b %Y' ); ls -hlt | awk -v d="$d" '{print $8, d }'
``` to give all files a date so i can see when they were received and so on and so forth.

I know date can be seen by other commands like ls -l but when driffent people finger in all files it gets a bit harry. So this was to eliminate confusion. Anyways.

Now i have a new problem. When i create the baseline file it gets an input. 
[Filename][date] If the date in the baseline file for example is 06-07-2011 and then the next day when it is 07-07-2011 it cant no longer diff properly. Since it dosent "understand" the new date. And then it thinks that all files even already existing files are new files. Hope you can see where im going.

Some code.
Creating the baseline file.
```
d=$( date '+%a %d %b %Y' ); ls -lht /file1/ | awk -v d="$d" '{print $8, d }' > $Baseline
        sed '1d' $Baseline > $Baseline.tmp
        mv $Baseline.tmp $Baseline
        sed '/entry1/d' $Baseline > $Baseline.tmp
        mv $Baseline.tmp $Baseline
        sed '/Incoming/d' $Baseline > $Baseline.tmp
        mv $Baseline.tmp $Baseline
        sed '/entry2/d' $Baseline > $Baseline.tmp
        mv $Baseline.tmp $Baseline
```

(i make tmp files because the system dosent understand the sed option to edit the file directly, without creating a temp file)

```
 d=$( date '+%a %d %b %Y' ); ls -lht /file2/ | awk -v d="$d" '{print $8, d }' > $path/NewFiles
        sed '1d' $path/NewFiles > $path/NewFiles.tmp
        mv $path/NewFiles.tmp $path/NewFiles
        sed '/entry1/d' $path/NewFiles > $path/NewFiles.tmp
        mv $path/NewFiles.tmp $path/NewFiles
        sed '/entry2/d' $path/NewFiles > $path/NewFiles.tmp
        mv $path/NewFiles.tmp $path/NewFiles
        sed '/Incoming/d' $path/NewFiles > $path/NewFiles.tmp
        mv $path/NewFiles.tmp $path/NewFiles
```

and then i diff
```
diff $path/Baseline $path/NewFiles | grep -E '^>|^<' > $path/NewFileResults
```

My question is.
When i diff, how do i get the diff command to look in the first colum instead of both colums. To look for driffences, because then (as far as i know) if it dosent look at the date then it wodent run into this problem. Hope it makes sense, to others than me.

I thought about using cut/awk and take the output of the first colum in the baseline file to a tmp file. But if i do that i dont know how to take the output from the temp file back. So i end up with [file][date] rather then just end up with [file]

---

### Post by Vaphell on 2011-04-06
> (i make tmp files because the system dosent understand the sed option to edit the file directly, without creating a temp file)

-i switch that means 'change source file in place' doesn't work?

i have to think a bit about the core problem, you see, i am not that experienced :-)

---

