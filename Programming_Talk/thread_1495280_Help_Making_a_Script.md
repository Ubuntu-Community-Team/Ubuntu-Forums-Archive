---
title: "Help Making a Script"
date: 2010-05-27
forum: Programming Talk
---

### Post by Joseph Schwenker on 2010-05-27
Hey, everyone!  I want to make a script for the Ubuntu terminal that will allow me to input a text file, then run this formula on each line:

*-(*-"#")
NEW LINE

I want the script to take whatever is on each line, and subtract all but one of the characters the first time, all but two of the characters the second time, etc.  This is essentially a "spelling pyramid generator".  For instance, if my word was Ubuntu:

U
Ub
Ubu
Ubun
Ubunt
Ubuntu

Can I have some help?  I can't program at all, but would love to learn.

---

### Post by lostinxlation on 2010-05-27
Not sure if I understand what you want correctly.
 
 
The 1st.
 
```

#!/usr/bin/perl
 
while(<>){
   chomp;
   print "\*-\(\*-\"#\"\)\n";
   print "$_\n";
}

```
 
 
The 2nd
```

#!/usr/bin/perl
 
while(<>){
   chomp;
   $x = $_;
   $len = length($_);
   for(1..$len){
      print substr($x, 0, $_),"\n";
   }
}

```
 
Redirect the text file into the scripts.
 
(I didn't test them)

---

### Post by patchwork on 2010-05-27
There we go, that's better...

[PHP]#!/usr/bin/python
text_file = "/home/kevin/Desktop/test.txt"

f = open(text_file, 'r')
for line in f:
    for i in range(len(line)):
        print line[0:i]
f.close()
[/PHP]Output:

```
u
ub
ubu
ubun
ubunt
ubuntu

g
go
gor
gori
goril
gorill
gorilla

m
me
mee
meer
meerk
meerka
meerkat

```

---

### Post by kaibob on 2010-05-28
You can use bash parameter expansion.

```
#!/bin/bash

while read word ; do
   for (( i=1 ; i<=${#word} ; i++ )) ; do
      echo ${word:0:${i}}
   done
done < file
```

Using patchwork's example,

> $ cat file
ubuntu
gorilla

$ testscript
u
ub
ubu
ubun
ubunt
ubuntu
g
go
gor
gori
goril
gorill
gorilla


---

### Post by Joseph Schwenker on 2010-05-28
All of these scripts return errors for me.  Kaibob's returns ```
joseph@joseph:~$ . spellingscript spelling36
bash: file: No such file or directory
joseph@joseph:~$ 
```

Patchwork's returns ```
joseph@joseph:~$ . spellingscript
text_file: command not found
bash: spellingscript: line 4: syntax error near unexpected token `('
bash: spellingscript: line 4: `f = open(text_file, 'r')'
joseph@joseph:~$ 

```

I am using the default Ubuntu terminal.

---

### Post by patchwork on 2010-05-28
In Kaibob's, you need to input the path and filename of the file you want to parse in place of the word 'file'
> All of these scripts return errors for me.  Kaibob's returns  	Code:
 	joseph@joseph:~$ . spellingscript spelling36
bash: file: No such file or directory
joseph@joseph:~$

In my case, it is a python script, and not a bash script. 
> Patchwork's returns  	Code:
 	joseph@joseph:~$ . spellingscript
text_file: command not found
bash: spellingscript: line 4: syntax error near unexpected token `('
bash: spellingscript: line 4: `f = open(text_file, 'r')'
joseph@joseph:~$ 

If you have python installed, you can either open an interactive session by typing ```
python
``` in your terminal, or you can create and execute a script.  I would certainly recommend trying python, as it is flexible like a scripting language, but more powerful.

---

### Post by geirha on 2010-05-29
The . (dot) command sources the file, running each line in you current shell. You can't use that for a python or perl-script as bash neither understands python nor perl code. Make the file executable and run it.
```
chmod +x script
./script

```

EDIT:

A minor modification of kaibob's script. Instead of using a hardcoded filename, you can pass the filename as argument. If you don't pass an argument, it will ask you for it:
```
#!/bin/bash
if [[ -n $1 ]]; then
  file=$1
else
  read -ep "Input filename: " file
fi

while read -r word ; do
   for (( i=1 ; i<=${#word} ; i++ )) ; do
      echo "${word:0:i}"
   done
done < "$file"

```
```
chmod +x script
./script some_file.txt
```

---

### Post by Joseph Schwenker on 2010-05-29
Using the modified version of Kaibob's, I was able to get the script working.  I was unable to do so with Patchwork's.

```
joseph@joseph:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> patchwork
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'patchwork' is not defined
>>> . patchwork
  File "<stdin>", line 1
    . patchwork
    ^
SyntaxError: invalid syntax
>>> patchwork spelling36
  File "<stdin>", line 1
    patchwork spelling36
                       ^
SyntaxError: invalid syntax
>>> 

```

Thanks, geihra, for the modified version, it helped a lot!  I really hope that they make us do spelling pyramids next year; no more writing for half an hour (ridiculously easy words).

```
joseph@joseph:~$ . kaibob
Input filename: spelling36
a
ac
acq
acqu
acqua
acquai
acquain
acquaint
acquainte
acquainted
a
at
atm
atmo
atmos
atmosp
atmosph
atmosphe
atmospher
atmosphere
c
ca
cat
cata
catas
catast
catastr
catastro
catastrop
catastroph
catastrophe
c
co
col
coll
colla
collap
collaps
collapse
c
co
col
colu
colum
column
c
co
con
conq
conqu
conque
conquer
c
co
cor
corr
corre
corres
corresp
correspo
correspon
correspond
corresponde
corresponden
correspondent
d
de
des
desi
desig
design
designe
designer
f
fa
fam
fami
famil
famili
familia
familiar
g
gy
gym
gymn
gymna
gymnas
gymnasi
gymnasiu
gymnasium
i
in
inq
inqu
inqui
inquis
inquisi
inquisit
inquisiti
inquisitiv
inquisitive
i
ir
irr
irre
irres
irresp
irrespo
irrespon
irrespons
irresponsi
irresponsib
irresponsibl
irresponsible
M
Mr
Mrs
Mrs.
Mrs. 
Mrs. S
Mrs. Sp
Mrs. Spe
Mrs. Spec
Mrs. Spech
Mrs. Specht
n
ne
nec
nece
neces
necess
necessa
necessar
necessary
n
ne
nec
nece
neces
necess
necessa
necessar
necessary
p
pa
pam
pamp
pamph
pamphl
pamphle
pamphlet
p
ph
phy
phys
physi
physic
physici
physicia
physician
r
rh
rhy
rhym
rhyme
rhymed
r
ro
roo
room
roomm
roomma
roommat
roommate
s
sp
spa
spag
spagh
spaghe
spaghet
spaghett
spaghetti
joseph@joseph:~$ 

```

---

### Post by geirha on 2010-05-29
> **Joseph Schwenker said:**
> Using the modified version of Kaibob's, I was able to get the script working.  I was unable to do so with Patchwork's.


Well, the dot command is a POSIX shell command, it is not something either python or perl knows. These are completely different languages, don't expect them to just magically understand each other's syntax.

To run a python script, make it executable and run it
```
chmod +x patchwork
./patchwork
```

Or run it specifically with python
```
python patchwork
```

---

