---
title: "Bash script: compare dirs/remove duplicates"
date: 2008-12-17
forum: Programming Talk
---

### Post by eraker on 2008-12-17
Someone asked in a ["General Help" thread](http://ubuntuforums.org/showthread.php?t=1013691") how to compare two directories (including their subdirectories) in order to remove duplicate files from the thousands there. I figured I could put this together relatively quickly, but then I got stuck puzzling out a particular part and I realized it was more difficult than I had realized.

Here's what I've got so far (and I'll probably immediately be told to do this in perl, but I started it in bash and now I'm not sure how to finish):

```

#!/bin/bash
# script name: diffdupedump
# compare output of two directories and remove duplicates
# supply full path of 2 directories to be compared

duplicates=( $(diff -u <(ls -R $1) <(ls -R $2) | grep ^[^-+@] ) )
rm -iv $1/${duplicates[@]:0}
```

I was trying to pull all duplicate filenames (which have no "+" "-" or "@" in them from diff output) and load them into an array, then append the directory name onto those file names in order to pass them to remove, but when I put ```
echo $1/${duplicates[@]:0}
``` into the script, I noticed that the full path was only being appended to the *first* element in the array.

Why does that happen?

After that, there are many other problems with this script as a solution, so I was just using it to try to puzzle something out. I also quickly realized that [many people have already answered this question]("http://www.google.com/search?q=script+to+remove+duplicate+files&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a"), so I mostly wanted to know how I was using the bash array incorrectly as a learning exercise.

Thanks.

---

### Post by chrisamiller on 2008-12-17
I'd use rsync.  Assuming that you're just trying to remove duplicates, and want all the other files combined, just rsync dir1 into dir2. It'll ignore any duplicate files and copy all the rest of the files from dir1 into dir2.  dir2 then contains what you're looking for.

---

### Post by eraker on 2008-12-17
Thanks for the response. I guess the thing that puzzles me is this. When I run this script:

```
#!/bin/bash
# compare output of two directories

dir1="./test1"
dir2="./test2"

duplicates=( $(diff -u <(ls -R $dir1) <(ls -R $dir2) | grep ^[^-+@] ) )
echo $dir1/${duplicates[@]:0};
```

It outputs the following (ignoring uniq files/folders and outputting duplicate files/folders):
```
./test1/butter fee gee nee ozz pee squirrel tee
```

But it only puts the path I wanted onto the first element in the array. Why does that happen?

---

### Post by mssever on 2008-12-17
> **eraker said:**
> But it only puts the path I wanted onto the first element in the array. Why does that happen?
Because that's what you told it to do. Keep in mind how expansion works. First, Bash expands variables. So, $dir1 becomes ./test1/butter and ${duplicates[@]:0} becomes fee gee nee ozz pee squirrel tee. After that, echo combines what's on the command line, and the / gets included. You didn't include any code to add $test1 to the beginning of every element in the array.

---

### Post by eraker on 2008-12-17
Ah. That makes sense. Thanks for explaining that.

---

### Post by Bakerconspiracy on 2008-12-17
Does he only want to remove directories on the same level of hierarchy? Also, I think it would be easier to use something like c++ and 'system("command")" recursively to do this.

---

### Post by mssever on 2008-12-17
> **Bakerconspiracy said:**
> Does he only want to remove directories on the same level of hierarchy? Also, I think it would be easier to use something like c++ and 'system("command")" recursively to do this.
C++ is way overkill for such a project. Python, Ruby, Perl, etc. would be understandable. But C++? Plus, since you're advocating the use of system(), you're suggesting that the OP should try to turn C++ into a shell script. Bash is much better at shell scripting than C++. And, of course a recursive approach would work in Bash.

Use the right tool for the job, and all that.

---

