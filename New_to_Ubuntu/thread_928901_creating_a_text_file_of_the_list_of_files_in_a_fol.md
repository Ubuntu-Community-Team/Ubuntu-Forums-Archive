---
title: "creating a text file of the list of files in a folder"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by crazy3rdyear on 2008-09-24
Hi,

I'm very new to ubuntu. I did find one post giving the idea of how to do this, but as I am not at all comfortable with using command line I'm looking for more specific help.

I have a folder called "piano scores" in my documents folder. What I want to do is generate a list of the names of the files in the folder and save it as a text file.

The post I was speaking about said to do the following 

find -type f -print > filename 

I tried it but I'm so unfamiliar with the terms I can't get anything to happen! Like do you do one word then enter then the next or type the lot in together?!

Please help :KS

---

### Post by Idefix82 on 2008-09-24
You can simply type
```

ls ~/Documents/piano\ scores > filename
```
and hit enter. Then you will have a file in your current directory called filename which will contain the content of your piano scores folder as a list.
Tip: Under Linux it's better not to use space in folder names and file names.

---

### Post by Titan8990 on 2008-09-24
This is fairly simple. Commands should all be done in the same line (there are exceptions but you don't need to concern yourself with then starting out).

What you will want to do is first change directories to the one you would like to list the contents of.

When you open your terminal you always start in your home directory. This is where your Documents folder is also located. So to change to your piano scores directory:

```
cd /Documents/piano\ scores/
```

Now, you notice that I used a \ in the piano scores name. This is how spaces are done in file and directory names. It is good practice to avoid spaces in file and folder names.

Now to list:

```
ls
```

This will list all the files in your current directory which should be piano scores. You had the right idea on how to append it to a file:

```
ls > filename.txt
```

The file will be placed in the same directory you are in.

Hope this helps.

---

