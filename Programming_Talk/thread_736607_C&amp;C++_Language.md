---
title: "C&amp;C++ Language"
date: 2008-03-26
forum: Programming Talk
---

### Post by mrdosa on 2008-03-26
I have both g++ and gcc, this I know from my synaptic package manager, it shows both are installed. I want to know, how can I open these. I mean, how should I go about using C and C++ 
I am a novice to all this, so can anyone help me out? Please!
Thanks in Advance.

---

### Post by LaRoza on 2008-03-26
See the sticky in the Programming Talk.

(Thread moved)

---

### Post by scragar on 2008-03-26
```
gcc **FILENAME or PATH**
```
to compile a .c file:
```
gcc **FILENAME** -o **PLACE TO STORE COMPILED VERSION**
```
to compile it with a name other than it's default file(I think it's either called **out** or **a.out** or something like that.

---

### Post by mrdosa on 2008-03-26
So, if I just want to write a small program, how should I go about?

---

### Post by LaRoza on 2008-03-26
> **mahender.mandala said:**
> So, if I just want to write a small program, how should I go about?

See the sticky, which has examples and a lot of information.

---

### Post by scragar on 2008-03-26
if your just learning then I have a few tips:

**1:** install binfmtc so you can run your C/C++ files without needing to compile your programs before testing```
sudo apt-get install binfmtc
```then start all your files with the comment:```
/*BINFMTCXX: 
*/
```

**2:** get used to saving files as .c and giving them execute privilages so you can launch them with binfmtc.

**3:** find a good tutorial.

---

### Post by iansane on 2008-03-26
You don't actually open them. You use the right commands in terminal to compile a program like helloworld.cpp. or you install an IDE (integrated development enviroment) that uses them as a backend.

you can go here.
[http://www.cplusplus.com/doc/tutorial/program_structure.html](http://www.cplusplus.com/doc/tutorial/program_structure.html)

put the helloworld code in a file and save it as helloWorld.cpp. 
Then in terminal cd to the dir. where it is and type

```
 g++ -O helloWorld.cpp -o helloWorld 
```

This compiles it into an executable which can be run from terminal with
```
 ./helloWorld 
```

If everything works you should see "hello World" in terminal

That is the most basic way to use g++

---

### Post by mrdosa on 2008-03-26
Thanks. I will do what you have suggested.

---

### Post by iansane on 2008-03-26
I never noticed you guys have this programming forum here. Too bad I can't get someone to do my homework according to the sticky. LOL just kidding.

---

### Post by LaRoza on 2008-03-26
> **iansane said:**
> I never noticed you guys have this c++ forum here. Too bad I can't get someone to do my homework according to the sticky. LOL just kidding.

Well, I am thinking of trying to get a change in the policy, to allow us to help, but on the condition we give the wrong answers.

---

### Post by mrdosa on 2008-03-26
I did what insane told. It worked, but isnt it a bit difficult to keep checking whether the program works? I mean, do we have to compile from terminal each time and run the compile file? is there nothng like Turbo C out here!?

---

### Post by mrdosa on 2008-03-26
Scrager I have installed the program u asked me to, now, should I use the text editor to write the c program and execute it?

---

### Post by LaRoza on 2008-03-26
> **mahender.mandala said:**
> I did what insane told. It worked, but isnt it a bit difficult to keep checking whether the program works? I mean, do we have to compile from terminal each time and run the compile file? is there nothng like Turbo C out here!?

You can use an IDE, and compile and run in one click.

(I don't use IDE's, and have quick compile scripts and aliases, but I have briefly used Geany, and it was nice and light, but usable)

---

### Post by mrdosa on 2008-03-26
Thanks guys!! I used to use turbo c on windows way back in first year of college. And jsut started using linux. I am just starting to learn C and C++ again and wrote my first program now!!:guitar: Now, if someone can post a good sticky here on how to use ubuntu for all C and C++ programming, it would be great. 


Psst. I dont know what an IDE is! I am way to ignorant I guess. If I could get hold of any tutorial on how to use ubuntu for programming c, i will stop asking!!:)

---

### Post by bruce89 on 2008-03-26
> **mahender.mandala said:**
> Thanks guys!! I used to use turbo c on windows way back in first year of college.
[...]
Psst. I dont know what an IDE is!

See your own words. (Integrated Development Environment)

---

### Post by mrdosa on 2008-03-26
Oops sorry!! Told you...am way to ignorant. I will try and learn this time around. Thanks once again. Just starting afresh as a hobby. I am a mechanical engineer BTW!!:lolflag:

---

### Post by LaRoza on 2008-03-26
> **mahender.mandala said:**
>  Now, if someone can post a good sticky here on how to use ubuntu for all C and C++ programming, it would be great. 


The sticky in this forum has two links for C and C++ programming.

---

