---
title: "bash coding"
date: 2011-04-07
forum: Programming Talk
---

### Post by Drenriza on 2011-04-07
Ive got alot of help and i learn alot of the examples people give me og bash code.
Now yet again im stuck with a script ive been working on for a while.

I have a script where i create a baseline file (static file) and a NewFile (dynamic file)
i then use a command
```
diff $path/Baseline $path/NewFile | grep -E '^>|^<' > $path/NewFileResults
```

I do this to see what files are new and what files are old on my system.
Now i have a new problem. When i create the baseline file it gets an input. 
[Filename][date] If the date in the baseline file for example is 06-07-2011 one day and then the next day when it is 07-07-2011 it cant no longer diff properly. Since it dosent "understand" the new date. And then it thinks that all files even already existing files are new files. Hope you can see where im going.

It does this because i cant get it to diff only the first colum but still keeping the data in the second colum.

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

Please ask if any questions, i find this hard to explain.

---

### Post by geirha on 2011-04-07
```
diff <(cut -d' ' -f1 "$path/Baseline") <(cut -d' ' -f1 "$path/NewFile")
``` Though it sounds like you rather want comm. See [http://mywiki.wooledge.org/BashFAQ/036](http://mywiki.wooledge.org/BashFAQ/036)

You are doing this in an odd way though. You really shouldn't use ls in a script, and you should use more quotes.

What do you use this diffing for?

---

### Post by Drenriza on 2011-04-07
> **geirha said:**
> ```
diff <(cut -d' ' -f1 "$path/Baseline") <(cut -d' ' -f1 "$path/NewFile")
``` Though it sounds like you rather want comm. See [http://mywiki.wooledge.org/BashFAQ/036](http://mywiki.wooledge.org/BashFAQ/036)

You are doing this in an odd way though. You really shouldn't use ls in a script, and you should use more quotes.

What do you use this diffing for?

Hey Geirha.
Basically i use the script to "monitor" from a cronjob, new and old files.
So when new files are uploaded to surten directories, the script will detect it. And give them a comment, newfile
and if anyone remove files from surten directories the script note it and give it a comment old/removed file.

Newfile
Oldfile. and such.

From what i can see from your suggestion, does the command still do the 
grep -E '^>|^<' > $path/NewFileResults
part?

---

### Post by geirha on 2011-04-07
> **Drenriza said:**
> Hey Geirha.
Basically i use the script to "monitor" from a cronjob, new and old files.
So when new files are uploaded to surten directories, the script will detect it. And give them a comment, newfile
and if anyone remove files from surten directories the script note it and give it a comment old/removed file.

Newfile
Oldfile. and such.

In that case, you should look at incron


> **Drenriza said:**
> 
From what i can see from your suggestion, does the command still do the 
grep -E '^>|^<' > $path/NewFileResults
part?
It does not. Try it (in an interactive shell) and see.

---

### Post by Drenriza on 2011-04-08
So as i understand incron is just a daemon running on the system and monitors specific files / directories.

---

