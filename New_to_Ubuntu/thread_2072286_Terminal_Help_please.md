---
title: "Terminal Help please"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by jumbobombo on 2012-10-17
Heyyy guys i am new here and i need help  with some terminal commands
I am completely new to the linux world and want to learn 
This is what my sir in college told me to do

1. Find all files in a recursively in a directory whose name starts with the letter A or B and which were modified 3 days ago.
so in my current directory i wrote in terminal :

find . \(-name 'A*' -o -name 'B*' \) -print

So this gave me all the files starting with A or B. and the 3 days ago part i used 

mtime 3

but it gives error

2. Find all directories in a file system which contain html or pdf files and create a list of such directories in a file 
so same as previous :

find . \(-name '*.pdf' -o -name '*.html' \) -print

But i couldnt figure out how to save all the directories in a file 

3. Find all image files in your file system with a size greater than 10kb and whose name contains any vowels

find . \-name '*.iso' -size +10k

So in this how should i go about with vowels?

4. And the directories which i find on the terminal i need to copy them in the same hierarchy to another location in the file system
How should i do  that?
 
Please help me with these problems.
I am completely new to ubuntu 

Thanks in advance :)

---

### Post by Vaphell on 2012-10-17
1. it's **-mtime 3** not **mtime 3**

2. your command finds files not directories
you have to get the directory part of the path (probably something with **-exec**) and probably ignore duplicates (read about pipes and look at **sort** command)
you can redirect output to file with **> file.txt** at the end
also, use **-iname** (case insensitive -name) instead of **-name**, unless you don't mind not getting .PDF in results

3. globs (patterns matching files/directories) support [abc] syntax which means a or b or c. It's easy to figure out how to describe a vowel using that feature.
**-iname** again

4. most likely **find -exec <recursive copy>** but what should happen when matching folders are in parent-child relation? should the child be copied twice (once as subfolder, once as a match?)

---

### Post by jumbobombo on 2012-10-18
> **Vaphell said:**
> 1. it's **-mtime 3** not **mtime 3**

2. your command finds files not directories
you have to get the directory part of the path (probably something with **-exec**) and probably ignore duplicates (read about pipes and look at **sort** command)
you can redirect output to file with **> file.txt** at the end
also, use **-iname** (case insensitive -name) instead of **-name**, unless you don't mind not getting .PDF in results

3. globs (patterns matching files/directories) support [abc] syntax which means a or b or c. It's easy to figure out how to describe a vowel using that feature.
**-iname** again

4. most likely **find -exec <recursive copy>** but what should happen when matching folders are in parent-child relation? should the child be copied twice (once as subfolder, once as a match?)


Heyy thanks a lot for your reply 

1. Solved :D

2. Solved :D the command which i mentioned also gives me the directories so its ok :)

3. What is globs? I did not get this part :confused:

4. I did not understand this either, Earlier you mentioned the **file.txt** if that writes the output in a file i think that it should do

Thanks a lot for your reply sir :)

---

### Post by Vaphell on 2012-10-18
2. you are not pushing yourself ;-)
/some/dir1/file1.pdf
/some/dir1/file2.pdf
/some/dir1/file3.pdf
/some/dir2/file1.html
/some/dir2/file2.html
/some/dir2/file3.html
doesn't look like a directory list to me.
I'd imagine that to pass this exercise you need to get
/some/dir1/
/some/dir2/
any other option is lame ;-)

3. globs are these things that match file/dir names, you know, ***.txt**, ***.pdf**, **something*.html**, ***something***... They support [] which lists a fixed list of allowed characters, eg. **[abc]*** will match everything that starts with a or b or c.

4. if i understand correctly, you have to find dirs and copy them to another location, not dump to file, am i right? That's not the same thing.

---

