---
title: "Bash script that loops through folders and saves PATH outputs into txt file?"
date: 2017-10-06
forum: Programming Talk
---

### Post by michiko.snow on 2017-10-06
[COLOR=#242729][FONT=Arial][FONT=inherit][FONT=arial]I am a newbie who is attempting to write a script that utilizes a text file containing names of different folders (subj1, subj2, subj3... etc), loops through each folder and goes into these folders to extract **full paths** of two files inside (i.e. /Users/desktop/subj1/animals/pig.jpg, /Users/desktop/subj1/animals/cow.jpg), then saves the subject ID and two files in 3 columns in a tab-delimited text file. (E.g. subj1 /Users/desktop/subj1/animals/pig.jpg /Users/desktop/subj1/animals/cow.jpg) so on and so forth. 
[/FONT][/FONT]
[FONT=inherit][FONT=arial]I have tried searching for answers but nothing really came close to answering this query.. I also need to do this for 1000 folders so it would be insane to try to create a file by hand.[/FONT][/FONT]
[FONT=arial]
Would really appreciate any helpful input!!
[/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2017-10-07
Welcome to the forums.

ABSG might be helpful.  google "ABSG linux" to find it.  I'd just use intermediate temporary files as I worked through the steps.  Get a list of the files with 'find' ... then you can selectively remove the parts you don't want for other answers needed.

I wouldn't use bash/sh/ksh for something like this.  I'd use perl, python, ruby.

Are you sure this is an Ubuntu question?

An exact "these are the inputs" and "these are the outputs" is needed.

---

### Post by steeldriver on 2017-10-08
Can you clarify with a complete example? I'm struggling to understand why you need to loop through folders if you already know the two files - can't you just treat it as a simple text processing operation e.g.

```

$ awk '{print $0, "/User/desktop/"$0"/animals/dog.jpg", "/User/desktop/"$0"/animals/pig.jpg"}' OFS='\t' file
subj1   /User/desktop/subj1/animals/dog.jpg     /User/desktop/subj1/animals/pig.jpg
subj2   /User/desktop/subj2/animals/dog.jpg     /User/desktop/subj2/animals/pig.jpg
subj3   /User/desktop/subj3/animals/dog.jpg     /User/desktop/subj3/animals/pig.jpg

```

---

