---
title: "Help with automatic matlab script"
date: 2008-03-26
forum: Programming Talk
---

### Post by nitro_n2o on 2008-03-26
Hi, 
I want run some matlab function with different arguments many times, but I don't want to do this manually. 
is there something in matlab that is similar to bash loop for i in *.jpg; do ls $i; done that I can use in matlab? 

any help will be really appreciated it 

Thx

---

### Post by WW on 2008-03-26
Matlab  has [for loops](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/matlab_prog/).  Follow the link, and click on Getting Started -> Programming -> Flow Control -> Loop Control.  Or, in Matlab, try **help for** or **doc for**. If those links are not enough to answer your question, give a few more details about what you want to do.

---

### Post by nitro_n2o on 2008-03-26
Yeah I know that matlab has for loops ...  I think i should give more information 

I have a function hello(file_name1, file_name2)  which takes 2 files names and does some processing and I want to run the function on several different files 

if the function hello was a C program, then i'll do this: 

for f in * 
do 
 ./hello.c $f ${f/.jpg}.data
done 

and the shell will take care of the rest 

how can i do the same thing with matlab ? 

Thanks for the reply

---

### Post by WW on 2008-03-26
The **dir** and **fileparts** commands might be useful.  Something like this, perhaps:
```

% Get a list of the files in the current directory with extension .jpg
jpgfiles = dir('*.jpg');
for k = 1:length(jpgfiles)
    % Split the file name into parts.
    [pathstr,name,ext,versn] = fileparts(jpgfiles(k).name);
    % Create the name with extension .data (instead of .jpg)
    newname = [name '.data'];
    % Do something useful with the files...
    hello(jpgfiles(k).name, newname)
end

```

---

### Post by WW on 2008-03-26
Or the brief version:
```

for f = dir('*.jpg')'
    [pathstr,name,ext,versn] = fileparts(f.name);
    hello(f.name, [name '.data'])
end

```

---

### Post by nitro_n2o on 2008-03-26
that looks great, expect that it says too many arguments to fileparts 
do you know how to fix that 

thx

---

### Post by WW on 2008-03-26
That happened to me, too.  In the brief version, don't forget the ' (the Matlab transpose character) after the **dir** function.

---

### Post by nitro_n2o on 2008-03-26
Thanks a lot that works :) 
it is the transpose i'm missing

---

