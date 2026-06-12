---
title: "Beginner Question, Copy Command / Scripting?"
date: 2007-05-21
forum: Programming Talk
---

### Post by rscott5 on 2007-05-21
Hi all,

I'm very new to Linux and any scripting language (I do have a good programming background though), so please bare with me, here goes. I have a huge collection of music, all in different file formats, which I need to separate out in order to convert. The thing is that I want to maintain my file structure when I separate out the certain files to be converted. I have my music set up in a /Artist/Album/Number - Song Title format. Here is the code that I tried to use to accomplish my task: ```
cp /home/ryan/music/*/*/*.m4a /home/ryan/tobeconverted/*/*/*.m4a
``` The problem here (I think) is that the cp command doesn't create the new .../*/*/ (.../Artist/Album/) directories when it needs to so when I run this it says directory does not exist. So my first question, is there a way to make the cp command do this for me?

If not, I suppose I will have to write a script to do this. The best way that I can think of to do this would be to loop through the folders, and if a *.m4a file is found, then it should create the appropriate directories (if needed) and then copy the file. Does this sound right? Any pointers as to how I would do this in Perl, or any other language?

Thanks in advance for your help.

Ryan

---

### Post by WW on 2007-05-22
There are probably many ways to do this. Here is one, but I expect someone else will come along any minute with an even clearer and more concise version.

You can use the **rsync** command with filters.  For example, I created a directory called tmp1, that contains a few subdirectories and files:
```

~$ tree tmp1
tmp1
|-- a.dat
|-- b.www
|-- subdir1
|   |-- d.dat
|   `-- e.mmm
`-- subdir2
    |-- f.dat
    `-- subdir3
        |-- junk.xyz
        |-- x.dat
        `-- y.dat

3 directories, 8 files
~$

```
To copy just the *.dat files, but keep the directory structure, I  will use the rsync command like this:
```

~$ rsync -r --filter="+ */" --filter="+ *.dat" --filter="- *" tmp1/ tmp2
~$ tree tmp2
tmp2
|-- a.dat
|-- subdir1
|   `-- d.dat
`-- subdir2
    |-- f.dat
    `-- subdir3
        |-- x.dat
        `-- y.dat

3 directories, 5 files
~$

```
Two notes:
1. The second filter option, **--filter="+ *.dat"**, determines the extension of the files to copy.
2. The trailing / in **tmp1/** is significant.  Without it, there will be an extra directory level in tmp2.

---

### Post by Mr. C. on 2007-05-22
> 
cd /home/ryan/music
find  -name '*.m4a' | tar  -cf - --files-from=- | tar -C /home/ryan/tobeconverted -xpf -
  

MrC

---

### Post by rscott5 on 2007-05-22
> **Mr. C. said:**
> MrC

Awesome! That worked perfect. Now I'm gonna get down to trying to understand why it worked so perfect. Thanks for the help.

WW - Thanks as well, Mr. C's answer just happened to seem quicker for me to try first.

---

