---
title: "gcc help"
date: 2008-11-26
forum: Programming Talk
---

### Post by phanipalagummi on 2008-11-26
in a book i saw that (complete reference to gcc)

hello.out(just typing in the terminal)

gives the executable result of hello.out

but it says to me command not found

could any one help me,and please tell me how to get the result of a executable

---

### Post by jimi_hendrix on 2008-11-26
go to the directory where you compiled it and type ls...then post the output (and try ./hello.out)

---

### Post by cmay on 2008-11-26
you need to have installed the build-essential package. then you compile a test program 
gcc -o hello ./hello.c and it should run by ./hello if not there is maybe something wrong. 
if  you do not have build-essential or gcc which is not installed in ubuntu per default it will likely say :gcc command not found.

---

### Post by phanipalagummi on 2008-11-26
[HTML]dheera@dheera-desktop ~ $ ls
Desktop       hanumaan.c  #*mail*#6153uil#  NetBeansProjects  untitled folder
dwhelper      hanumaan.o  #*mail*#6312Dtl#  p                 Videos
Examples      hello.c     movies            phanindra notes   video songs
hanumaan      hello.c~    myc               Photos            wall papers
#hanumaan.c#  hellow      naruto episodes   Pictures
[/HTML]

after ```
gcc hello.c 
```i got this as out put

[HTML]dheera@dheera-desktop ~ $ ls
a.out     #hanumaan.c#  hellow            naruto episodes   Pictures
Desktop   hanumaan.c    #*mail*#6153uil#  NetBeansProjects  untitled folder
dwhelper  hanumaan.o    #*mail*#6312Dtl#  p                 Videos
Examples  hello.c       movies            phanindra notes   video songs
hanumaan  hello.c~      myc               Photos            wall papers
[/HTML]

after ```
a.out 
```i got this as 

[HTML]dheera@dheera-desktop ~ $ a.out
bash: a.out: command not found
[/HTML]

---

### Post by cmay on 2008-11-26
[php]./a.out[/php]

---

### Post by phanipalagummi on 2008-11-26
[PHP]dheera@dheera-desktop ~ $ ./a.out
bash: ./a.out: No such file or directory
[/PHP]

---

### Post by jimi_hendrix on 2008-11-26
for the heck of it try

gcc -o helloworld filename.c 

(filename = your file name)

then ./helloworld

---

### Post by phanipalagummi on 2008-11-26
thank you i got it,

but why this "./" for why not without that directly typing helloworld i m not getting the result

please dont say to type man gcc

---

### Post by cmay on 2008-11-26
linux is case sensitive. i often cant type in the right command in the first try. 
but if this works then i am sure ./a.out will also if you really want it too :)

---

### Post by phanipalagummi on 2008-11-26
yes even ./a.out also worked

but why this "./" why not directly a.out ,please explain me,
bcoz i saw that a.out could also give the out put in a book

---

### Post by cmay on 2008-11-26
> **phanipalagummi said:**
> yes even ./a.out also worked

but why this "./" why not directly a.out ,please explain me,
bcoz i saw that a.out could also give the out put in a book

./ is current directory . so else you can type /home/$username/a.out
or cd /home/$username/ and then type a.out but its more simple to type ./ 
good luck with your programing.

---

### Post by snova on 2008-11-26
Bash searches for programs in a list of directories, contained in the variable PATH. The current directory you reside in is not in this list. So when you run 'a.out', it looks for it, and cannot find it. Thus you have to tell Bash the filename explicitly with './a.out'. It doesn't look like much, but ./ is a path- . is the current directory, / the path separator.

It is possible to add '.' to PATH, but this is discouraged (I'm not sure why).

---

