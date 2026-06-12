---
title: "Simple BASH Script: Need some help."
date: 2009-10-03
forum: Programming Talk
---

### Post by rob86 on 2009-10-03
I'm trying to make a bash script that when run it will start in the current dir, and check every file size and execute commands when it finds one that is smaller than something.

For example: echo 'This file (TestFile111.avi) is smaller than 1.5gb' 

Ofcourse it will do more than echo in the end, but one thing at a time.. I just want it to go through the files right now.

I want it to go through the sub directories too, like if it's run in /MainDIR/ it will go through /MainDIR/Sub1/ and /MainDIR/Sub2/ etc.. 

I've done a bit of reading on it and have some idea how to do the if statements to check the file size and figure I'm supposed to use the stat command in there somewhere but it's kind of hard to get started.. I can make a script to check one file's file size, but I don't know how to make it check every file even in sub dirs. 

Can anyone help me?

---

### Post by diesch on 2009-10-03
```

find . -size -1536M | while read f; do
 echo "This file ($f) is smaller than 1.5GB"
done

```

This doesn't work for files whose name contain a line break - but if you have file names like that I'm sure you are used to have trouble.

---

### Post by bigboy_pdb on 2009-10-03
The method that was posted looks good, but one thing that should be changed is the data should be redirected to "done" instead of "while". I've had problems with piping data to "while" in the past. Unfortunately, I can't remember what issues with it were, otherwise I'd give an example.

With the changes it would be:
```

while read f; do
 echo "This file ($f) is smaller than 1.5GB"
done < <(find . -size -1536M)

```

---

### Post by diesch on 2009-10-03
The difference I see here is that your way is bash-specific (it doesn't work with plain sh) and creates a separate subshell for the find command.

---

