---
title: "environment variables"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by jiangchongyi on 2012-03-04
Hello all&#65292;
 
I deal with cd-hit, a software special for bioinformatics, and meet obstacles.
I download the software and follow the instruction to unpack the file, as followed:
 
tar xvf cd-hit-2006-0215.tar.gz
 
But when I typed in the command, it said that " command not found".
I guess that it may be something wrong with the environment variables, but I donot know what to do.
 
Any help will be grateful!
 
Daniel

---

### Post by mikewhatever on 2012-03-04
What command wasn't found? Can you post the actual output as is instead.

---

### Post by codemaniac on 2012-03-04
Can you post exactly what error the shell is throwing up .

tar command is generally available on almost all UNIX flavors .To check out your version do a below

```
which tar
```

Best regards

---

### Post by codemaniac on 2012-03-04
> **jiangchongyi said:**
> 
tar xvf cd-hit-2006-0215.tar.gz


One thing i noticed ,the downloaded package is gzipped , you need to include 'z' option also with tar , like below

```
tar xzvf cd-hit-2006-0215.tar.gz
```

---

### Post by jiangchongyi on 2012-03-04
> **mikewhatever said:**
> What command wasn't found? Can you post the actual output as is instead.
 
a command within the software
 
cd-hit-est[ATTACH]213663[/ATTACH]

---

### Post by MG&amp;TL on 2012-03-04
In *nix-like systems, you have to specify the directory if you're running it locally. So you want, in that directory:

```
./cd-hit-est -i allseq -o allseqclear
```

---

### Post by nothingspecial on 2012-03-04
Unless that executable is in your $PATH your terminal will not find it.

You need to either, specify the full path, put it in a directory that is in your $PATH or add the directory it is in to your $PATH.

---

### Post by jiangchongyi on 2012-03-04
> **codemaniac said:**
> Can you post exactly what error the shell is throwing up .
 
tar command is generally available on almost all UNIX flavors .To check out your version do a below
 
```
which tar
```
 
Best regards
 
/bin/tar
 
actually, I can get into the file and see the command I want to apply
but when I try to run it 
the ubuntu throwed out that cmmand not found

---

### Post by jiangchongyi on 2012-03-04
> **nothingspecial said:**
> Unless that executable is in your $PATH your terminal will not find it.
 
You need to either, specify the full path, put it in a directory that is in your $PATH or add the directory it is in to your $PATH.
 
 
so can you show me the exact steps how to do it 
I am fresh to ubuntu...
 
Thanks a lot!

---

### Post by codemaniac on 2012-03-04
Hello jiangchongyi

I assume you are having the source package **cd-hit-2006-0215.tar.gz** .
Do you have it unzipped , untarred and installed accordingly in your system ?

I guess the mentioned packaged has not been installed properly in your system .

---

### Post by MG&amp;TL on 2012-03-04
> **jiangchongyi said:**
> so can you show me the exact steps how to do it 
I am fresh to ubuntu...
 
Thanks a lot!

You can either tell bash (the shell) to look in the directories specified in $PATH, by just typing the name of the program, or you can specify the location of it yourself. For instance:

```
/usr/bin/firefox
```

is the same as just:

```
firefox
```

as /usr/bin/ is in your $PATH.

Anyway, in your particular case, I am assuming the unpacked directory is in your homefolder, and called "program"-you'll have to replace that with whatever your directory is called and where it is located.

```
cd program
./cd-hit-est -i allseq -o allseqclear
```

Explanation: cd changes the directory to program/, then you tell bash to look in ./ (the current folder) for an executable called cd-hit-est.

---

### Post by nothingspecial on 2012-03-04
Well, for example you could make a folder in your home directory named bin and put your program in it.

Then put this line at the end of your .bashrc

```
export PATH=${PATH}:/home/$USER/bin
```

So ```
gedit .bashrc
```

Put that line at the very end. Then get bash to read that file again

```
. .bashrc
```

Then test it by typing

```
echo $PATH
```

The final entry should be /home/what_ever_your_username_is/bin

---

### Post by mikewhatever on 2012-03-04
> **jiangchongyi said:**
> a command within the software
 
cd-hit-est[ATTACH]213663[/ATTACH]

You need to cd into the folder first, then run it like this: ./cd-hit-est .

Alternatively, you can provide the full path to the executable: /home/jiangchongyi/parent_folder/cd-hit-est

---

### Post by jiangchongyi on 2012-03-23
> **mikewhatever said:**
> You need to cd into the folder first, then run it like this: ./cd-hit-est .
 
Alternatively, you can provide the full path to the executable: /home/jiangchongyi/parent_folder/cd-hit-est
 
 
I do exactly the way you suggested and the problem solved!
Thanks a lot!

---

