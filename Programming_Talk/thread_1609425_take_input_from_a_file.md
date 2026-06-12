---
title: "take input from a file"
date: 2010-10-30
forum: Programming Talk
---

### Post by c2tarun on 2010-10-30
hi friends
i have certain predefined test cases for my program in a file..
i want my program to take input from that file..
how can i do that with gcc compiler..???

---

### Post by dwhitney67 on 2010-10-30
If you are programming in C, read the man-pages for fopen() and fgets().

If you are programming in C++, read this:
[http://www.cplusplus.com/reference/iostream/ifstream/](http://www.cplusplus.com/reference/iostream/ifstream/)

For other programming languages, you are on your own.

---

### Post by Vox754 on 2010-10-30
> **c2tarun said:**
> hi friends
i have certain predefined test cases for my program in a file..
i want my program to take input from that file..
how can i do that with gcc compiler..???
As is common with you, your question is undecipherable. It is not clear what you want.

Do you want to compile the file, and then run it with different options?
```

./my_program option_1
./my_program option_2
./my_program option_3

```

Or do you want to use input redirection?
```

./my_program < file_1
./my_program < file_2
./my_program < file_3

```

Or do you want to do compile different pieces of code, and test each resulting executable?
```

gcc source_1.c -o my_program_1
gcc source_2.c -o my_program_2
gcc source_3.c -o my_program_3

```
Or a combination of all?

Please, try to take a good hour to write a complete, informative post.

---

### Post by c2tarun on 2010-10-30
> **Vox754 said:**
> As is common with you, your question is undecipherable. It is not clear what you want.

Do you want to compile the file, and then run it with different options?
```

./my_program option_1
./my_program option_2
./my_program option_3

```Or do you want to use input redirection?
```

./my_program < file_1
./my_program < file_2
./my_program < file_3

```Or do you want to do compile different pieces of code, and test each resulting executable?
```

gcc source_1.c -o my_program_1
gcc source_2.c -o my_program_2
gcc source_3.c -o my_program_3

```Or a combination of all?

Please, try to take a good hour to write a complete, informative post.


i m extremely for not explaining my problem in detail.

actually i was trying to solve this problem:
[http://www.codechef.com/problems/SUMTRIAN/](http://www.codechef.com/problems/SUMTRIAN/)

as you can see on the questions page 2 test cases are given.
i made the program, it contains some error. each time i remove a error to check the program i have to enter whole data manually.
here there are only two test cases. but in many other programs i want to design my own test cases. the problem is entering data manually is very tiresome job, and then after entering that amount of data, if program gives wrong output its quite frustrating. somehow i managed to solve this question. but my problem of entering the test cases still persists.
i want a way such that i save certain of my test cases in a file and my program automatically takes input from that file. 
hope now you got what i was trying to explain.
thanx

---

### Post by cgroza on 2010-10-30
Read the file, assign its contents as a string to a variable, pass that variable to your function.

---

### Post by c2tarun on 2010-10-30
well somehow
./myfile < file 
worked for me as i wanted
thanx a lot vox754

---

### Post by worksofcraft on 2010-10-30
> **c2tarun said:**
> well somehow
./myfile < file 
worked for me as i wanted
thanx a lot vox754

Yes you can redirect standard input and you can also pipe the output from one program to another on the command line using the pipe symbol.

If you make a program with graphical user interface you can use [xnee]("http://en.wikipedia.org/wiki/Xnee"), a macro recorder to record and play back test sequences of events.

---

