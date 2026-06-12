---
title: "Rename folders as files inside"
date: 2018-12-06
forum: Programming Talk
---

### Post by ral1s on 2018-12-06
Hi, 
i have a problem with rename a lot of folders. 

There is a structure of my problem and what i need..

I have many folders..
for example:

folder /0512-2018 contains files 78563412.txt and 78563412.rar
         
[COLOR=#ff0000]**./0512-2018**[/COLOR]   -- 78563412.txt
                        -- 78563412.rar

and i need rename this folder as files inside this folder:

[COLOR=#000000]**./78563412**[/COLOR]   -- 78563412.txt
                      -- 78563412.rar

Thanks so much!

---

### Post by TheFu on 2018-12-06
ABSG will help you create a script: [https://www.tldp.org/LDP/abs/html/](https://www.tldp.org/LDP/abs/html/)
Doesn't appear to be too hard.  I would pick one of the files in the subdirectory (folders are a GUI thing), probably the txt file,  and find it, take the basename, then move the directory containing that file {dirname} to {basename}.

A little **find** + **sed** + **dirname** + **basename** + **mv**

Is this a homework problem for a Linux class?

---

