---
title: "problem installing package (SPR 3.3.2)"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by TheSource007 on 2013-05-26
Hi everyone,
I am new to the Ubuntu OS and I've learning how to use it and how to install things and stuff.
I am having troubles installing a package called StatPatternRecognition
[HTML]http://statpatrec.sourceforge.net/[/HTML]
In the terminal I try to install it this way;
./ configure --prefix=$HOME/TRY4      so I can install the package in the folder TRY4.
After it's done doing whatever it's doing, I type make. Then that takes a while and after a long series of words and number it displays errors at the end. Then I type make install and after 3 seconds it finishes with errors. These are the last lines the make install displays

SprAddBaggersApp.cc: In function ‘int main(int, char**)’:
SprAddBaggersApp.cc:47: error: ‘EOF’ was not declared in this scope
make[1]: *** [SprAddBaggersApp.o] Error 1
make[1]: Leaving directory `/home/jesusms/Downloads/SPR-3.3.2/src'
make: *** [install-recursive] Error 1


I have attached the config log file that the program created. I dont know if it's useful or relevant here, 'cause I dont even know what it says. I have no idea what's wrong. I tried installing in different directories, downloading many packages that it seem to need (like gcc or something like that), but nothing seems to work. Plus I am new to this OS so i have no idea what's going on.
The program is (from what I understand) a data analysis software. I will have to use it for an assigment so I need to learn how to use it, but if I cant install it I cant learn how to use it.
I will appreciate any help.
Thank you.

---

### Post by steeldriver on 2013-05-26
Hello and welcome to the forum 

That source package appears to have a bunch of files (SprAddBaggersApp.cc is just the first) which use the EOF symbolic constant without including either <stdio.h> or <cstdio> - it's old code (seems to have been dormant for 5 or 6 years) so maybe that was legal in earlier versions of gcc / g++

I managed to get it to build after fixing those inclusions - you can either run this one-liner in the SPR-3.3.2 directory:

```
while read -r file; do if [ $(grep -c '<stdio.h>' "$file") -eq 0 ]; then sed -i -re '0,/#include <[^>]+>/ s//#include <stdio.h>\n&/' "$file"; fi; done < <(find . -name '*.cc' -exec grep -l 'EOF' {} \;)
```

(basically it searches for any .cc files that use 'EOF', then if they don't contain '<stdio.h>' it inserts '#include <stdio.h>' at the top of the standard inclusions). Or you can apply the attached patch file by placing it in your Downloads directory at the same level as your SPR-3.2.2 directory and then doing

```
patch -p1 < ../patch-SPR-3.3.2.txt
```

from the SPR-3.2.2 directory

Hope this helps

[ATTACH]243106[/ATTACH]

---

### Post by TheSource007 on 2013-05-27
Thanks a lot! It did work and I think it installed correctly.
However I can't open any of the files. Not sure what I'm doing wrong.
For example, I type,
jesusms@jesusms-laptop:~/TRY7/bin$ ./exampleUserCuts
and it shows
Unable to open file gauss2_uniform_2d_train.pat
Unable to read data from file gauss2_uniform_2d_train.pat
Also, I tired the example on the package home page,

jesusms@jesusms-laptop:~/TRY7/bin$ ./SprIOTestApp -a 1 cleveland.data
Unable to open file cleveland.data
Unable to read data from file cleveland.data

all of those files are in the share folder under TRY7 folder. Am I supposed to open them manually first. If so, how?
Thanks a lot.

---

### Post by steeldriver on 2013-05-27
All the data files appear to be in the share subdirectory

```
t61p:~/TRY7$ find ../ -name '*.pat'
../share/gauss4_uniform_2d_valid.pat
../share/triangle_square_00_train.pat
../share/gauss4_uniform_2d_train.pat
../share/gauss_uniform_2d_train.pat
../share/tmva_root.pat
../share/lambda-test.pat
../share/trainRoot.pat
../share/discrete_square.pat
../share/gauss2_uniform_2d_train.pat
../share/gauss2_uniform_2d_train_root.pat
../share/gauss2_uniform_2d_valid.pat
../share/lambda-train.pat
../share/uniform_on_uniform_2d.pat
../share/gausscorr_uniform_2d_train.pat
../share/mlp_root.pat

```

 so instead of cd'ing into the bin directory and trying to run from there, cd into the share directory and give your executable path back to bin:

```
t61p:~/TRY7$ cd share/
t61p:~/TRY7/share$ 
t61p:~/TRY7/share$ ../bin/exampleUserCuts 
Read data from file gauss2_uniform_2d_train.pat for variables "x1_plus_x2"
Total number of points read: 2528
Points in class 0: 2138 1: 390
Output successfully closed.
```

Or to make life easier you can add the bin directory to your PATH and then you can call the executables from anywhere without worrying about the path:

```
t61p:~/TRY7/share$ export PATH=$PATH:$HOME/TRY7/bin
t61p:~/TRY7/share$ 
t61p:~/TRY7/share$ exampleUserCuts 
Read data from file gauss2_uniform_2d_train.pat for variables "x1_plus_x2"
Total number of points read: 2528
Points in class 0: 2138 1: 390
Warning: file filtered.out will be deleted.
Output successfully closed.
t61p:~/TRY7/share$ 
t61p:~/TRY7/share$ SprIOTestApp -a 1 cleveland.data
Read data from file cleveland.data for variables "age" "sex" "cp" "trestbps" "chol" "fbs" "restecg" "thalach" "exang" "oldpeak" "slope" "ca" "thal"
Total number of points read: 303
Found 5 classes in data:
  Class:          0(1)    Points:        164
  Class:          2(1)    Points:         36
  Class:          1(1)    Points:         55
  Class:          3(1)    Points:         35
  Class:          4(1)    Points:         13
No input classes specified in string  Will use 0 and 1 by default.
Training data filtered by class.
Points in class 0(1):   164
Points in class 1(1):   55
t61p:~/TRY7/share$ 

```

Good luck

---

### Post by TheSource007 on 2013-05-27
Wow thank you that really helped.
Now I can begin to learn how to use this thing.
I really appreciate your help. Thank you

---

