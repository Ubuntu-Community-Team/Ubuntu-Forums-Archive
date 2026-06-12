---
title: "OpenCV with codeblocks"
date: 2010-07-01
forum: Programming Talk
---

### Post by shababhsiddique on 2010-07-01
Hi
I am a learner of C++. I am doing some work with OpenCV now..

I managed to compile my OpenCV programs with the following command from terminal

g++ `pkg-config opencv --cflags --libs` myprogram.c

it serves something like

g++ -I/usr/local/include/opencv -L/usr/local/lib -lcxcore -lcv -lhighgui -lcvaux -lml myprogram.c

it works.. but i am not used to write in the notepad.....


can any one help me out on how i can link these libraries to my IDE so that i dont have to worry about terminal commands..



I am using CODEBLOCKS on Jaunty

---

### Post by tuxmanic on 2010-07-18
If you are looking for a Simple way to compilation with OpenCV flags i have a solution

with the help of community i got simple script to compile with OpenCV Flags

To Use This script copy and paste it into a new file named build.sh in your working directory or download the attachment.

```
#!/bin/sh

for file; do
  base=${file%.*}
  case $file in 
    *.c)
      echo "Compiling $base"
      gcc -ggdb $(pkg-config --cflags --libs opencv) -o "$base" "$file"
      ;;
    *.cpp)
      echo "Compiling $base"
      g++ -ggdb $(pkg-config --cflags --libs opencv) -o "$base" "$file"
      ;;
    *)
      echo "Don't know what to do with $file"
      ;;
  esac
done
```To compile a c/c++ programme with opencv flags just execute this script along with the name of the input file

```
./build.sh <input file>
```Then output will generated in the same directory with same name of input file (without extension).to execute the programme, Just enter 

```
./<filename> <arguments>
```_**Exmaple**_
if your input filename is test.c ,then just enter

```
./build.sh test.c
```It will do the compilation . to execute programme enter

```
./test 
```Am not a shell script/opencv expert, i made this because i dont know cmake or make utility .its better to use a make file.if you find any errors please correct it.

---

### Post by shababhsiddique on 2010-08-23
> **tuxmanic said:**
> If you are looking for a Simple way to compilation with OpenCV flags i have a solution

with the help of community i got simple script to compile with OpenCV Flags

To Use This script copy and paste it into a new file named build.sh in your working directory or download the attachment.

```
#!/bin/sh

for file; do
  base=${file%.*}
  case $file in 
    *.c)
      echo "Compiling $base"
      gcc -ggdb $(pkg-config --cflags --libs opencv) -o "$base" "$file"
      ;;
    *.cpp)
      echo "Compiling $base"
      g++ -ggdb $(pkg-config --cflags --libs opencv) -o "$base" "$file"
      ;;
    *)
      echo "Don't know what to do with $file"
      ;;
  esac
done
```To compile a c/c++ programme with opencv flags just execute this script along with the name of the input file

```
./build.sh <input file>
```Then output will generated in the same directory with same name of input file (without extension).to execute the programme, Just enter 

```
./<filename> <arguments>
```_**Exmaple**_
if your input filename is test.c ,then just enter

```
./build.sh test.c
```It will do the compilation . to execute programme enter

```
./test 
```Am not a shell script/opencv expert, i made this because i dont know cmake or make utility .its better to use a make file.if you find any errors please correct it.


Thanks very very much for your help. Sorry for late response. i wanted a way to compile OPenCV codes with a IDE like codeblocks and solved it.

---

