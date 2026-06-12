---
title: "Problem with scanf---&gt;SemiBeginner"
date: 2010-02-12
forum: Programming Talk
---

### Post by hakermania on 2010-02-12
Hi, I'm quite a beginner in C++.I am working in QtCreator.I have made a program which co-operates with some .sh executable files. I have a problem when the scanf command takes a character and not a number.Well, to make you understand better, this is my program:

```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int a;
    while (1){
    printf("If you are not root, please become...\n\n 1 = What's my mac?               7 = Start aircrack-ng and hack them all\n 2 = Change my mac                8 = Send DeAth to broadcast\n 3 = Start capturing IVS          9 = See available modems\n 4 = Start Reading files         10 = What's my interface? \n 5 = Stop interface              11 = About this prog \n 6 = Start interface             12 = Exit \n");
    scanf("%d",&a);
    if (a==1) system("/etc/macchanger1.sh");
    else if (a==2) system("/etc/macchanger2.sh");
    else if (a==3) system("/etc/dumpcapt.sh");
    else if (a==4) system("/etc/aireplayread.sh");
    else if (a==5) system("/etc/airmonstop.sh");
    else if (a==6) system("/etc/airmonstart.sh");
    else if (a==7) system("/etc/aircrack.sh");
    else if (a==8) system("/etc/aireplaysenddeath.sh");
    else if (a==9) system("/etc/airodump-ng.sh");
    else if (a==10) system("/etc/airmon-ng.sh");
    else if (a==11) printf(" This prog was written on February 2010 with purpose to make your life easier\n in hacking yours WEP modems...Cheers!!!\n Note that you must have installed macchanger and aircrack-ng \n");
    else if (a==12) break;
    else if (a<=1 || a>=12) printf("Please type a number from 1 to 12\n");
    else {printf("ERROR\n"); break;}
    }
        return 0;

}
```
Well, as you can see the program when being run, shows a menu which allows you to choose what you want to do.The problem is that when somebody gives a character (for example "a" or "b" or "school" or anything else) and no a number the program goes mad and starts the menu again and again till I push Ctrl+C
I have put the last "else" in order to avoid this problem with the thought that this "else" would include all the characters (because I have already included all the numbers on what to do so the thing that remains are the characters) and so, if somebody gave a character the the ERROR message would be shown and then the program would exit (because of the break; after the printf) something that never happens....
Can you please help me solve this problem? Thanks :)

---

### Post by Pelgar on 2010-02-12
Hi hakermania, It's been a very long time since I did any console keyboard input but I think I can help a little. Your main problem is in the way scanf handles errors. Since you are asking it to get a number from the keyboard then give it a character or character string scanf returns an error. The endless loop of repeated messages that you have to ctrl-c to get out of is because scanf does not clear the keyboard buffer on error. The next time your loop runs scanf it sees the same char or string in the keyboard buffer over and over and over.... So if an unwanted string is read in you are going to have to clear the keyboard buffer before you run scanf again.
I don't think testing for numbers less than 1 and greater than 12 is going to work either, not if a char is input. You will need to do something like int tst = scanf("%d",&a); then if tst is zero there was an error.

---

### Post by hakermania on 2010-02-12
> **Pelgar said:**
> Hi hakermania, It's been a very long time since I did any console keyboard input but I think I can help a little. Your main problem is in the way scanf handles errors. Since you are asking it to get a number from the keyboard then give it a character or character string scanf returns an error. The endless loop of repeated messages that you have to ctrl-c to get out of is because scanf does not clear the keyboard buffer on error. The next time your loop runs scanf it sees the same char or string in the keyboard buffer over and over and over.... So if an unwanted string is read in you are going to have to clear the keyboard buffer before you run scanf again.
I don't think testing for numbers less than 1 and greater than 12 is going to work either, not if a char is input. You will need to do something like int tst = scanf("%d",&a); then if tst is zero there was an error.

Am...So....Because I did'nt really get it,  if it is not difficult for you, could you please rewrite my hole program (ctrl+c easier) with this inside in the place you think it will work?:   int tst = scanf("%d",&a);

---

### Post by hakermania on 2010-02-12
No, ok, thx the problem is completely solved thx to you! I like when I find so good people! Thx!

 #include <stdio.h>
 #include <stdlib.h>
 
 int main()
 {
     char tst[256];
     int a;
     while (1){
     printf("If you are not root, please become...\n\n 1 = What's my mac?               7 = Start aircrack-ng and hack them all\n 2 = Change my mac                8 = Send DeAth to broadcast\n 3 = Start capturing IVS          9 = See available modems\n 4 = Start Reading files         10 = What's my interface? \n 5 = Stop interface              11 = About this prog \n 6 = Start interface             12 = Exit \n");
     if (scanf("%d",&a)==1){
     if (a==1) system("/etc/macchanger1.sh");
     else if (a==2) system("/etc/macchanger2.sh");
     else if (a==3) system("/etc/dumpcapt.sh");
     else if (a==4) system("/etc/aireplayread.sh");
     else if (a==5) system("/etc/airmonstop.sh");
     else if (a==6) system("/etc/airmonstart.sh");
     else if (a==7) system("/etc/aircrack.sh");
     else if (a==8) system("/etc/aireplaysenddeath.sh");
     else if (a==9) system("/etc/airodump-ng.sh");
     else if (a==10) system("/etc/airmon-ng.sh");
     else if (a==11) printf(" This prog was written on February 2010 by Hakermania\n a 15 years old child with purpose to make your life easier\n [EMAIL="alexsol94@hotmail.com"][/EMAIL]\n");
     else if (a==12) break;
     else if (a<=1 || a>=12) printf("Please type a number from 1 to 12\n");}
     else {printf("ERROR do not type characters, please type a number from 1 to 12\n"); scanf("%s",tst);}
     }
         return 0;
 
 }

---

### Post by Pelgar on 2010-02-12
Try this

```
#include <stdio.h>
#include <stdlib.h>


int main()
{
    int a;
    int tst;
    char chr = 0;
    while (1)
    {
    printf("If you are not root, please become...\n\n 1 = What's my mac?               7 = Start aircrack-ng and hack them all\n 2 = Change my mac                8 = Send DeAth to broadcast\n 3 = Start capturing IVS          9 = See available modems\n 4 = Start Reading files         10 = What's my interface? \n 5 = Stop interface              11 = About this prog \n 6 = Start interface             12 = Exit \n");
    tst = scanf("%d",&a);
    if(!tst) //if scanf error
    {
      printf("Please type a number from 1 to 12\n");
      while (chr != '\n')
      {
        scanf("%c", &chr); //clear keyboard buffer
      }
      chr = 0;             //make sure char != '\n' in case user inputs another char or string
    }
    else if (a==1) system("/etc/macchanger1.sh");
    else if (a==2) system("/etc/macchanger2.sh");
    else if (a==3) system("/etc/dumpcapt.sh");
    else if (a==4) system("/etc/aireplayread.sh");
    else if (a==5) system("/etc/airmonstop.sh");
    else if (a==6) system("/etc/airmonstart.sh");
    else if (a==7) system("/etc/aircrack.sh");
    else if (a==8) system("/etc/aireplaysenddeath.sh");
    else if (a==9) system("/etc/airodump-ng.sh");
    else if (a==10) system("/etc/airmon-ng.sh");
    else if (a==11) printf(" This prog was written on February 2010 with purpose to make your life easier\n in hacking yours WEP modems...Cheers!!!\n Note that you must have installed macchanger and aircrack-ng \n");
    else if (a==12) break;
    else {printf("ERROR\n"); break;}
    }
        return 0;

}
```

---

### Post by hakermania on 2010-02-12
No, ok the problem was solved buddy! But anyway thx for the help

---

### Post by Pelgar on 2010-02-12
Glad you got it worked out! I believe your fix is a bit cleaner than mine, less code anyway. Like I said, it has been a long time.

---

### Post by hakermania on 2010-02-12
> **Pelgar said:**
> Glad you got it worked out! I believe your fix is a bit cleaner than mine, less code anyway. Like I said, it has been a long time.

yeah, ok I asked and in other foroums and the ways they suggested me were completely confusing.This is the best I can say...but thx anyway ;)

---

### Post by FendarilX on 2010-02-12
Isn't there an ISDIGIT function somewhere in the cstring or cstdlib?

---

### Post by nvteighen on 2010-02-13
I wonder why this done in **C**... Yes, this is **not C++**. Anyway, this sort of code should have been written in bash instead... It would have been much easier to deal with input...

---

### Post by Pelgar on 2010-02-13
nvteighen said:
> I wonder why this done in **C**... Yes, this is **not C++**. Anyway, this sort of code should have been written in bash instead... It would have been much easier to deal with input...You are very right this is C and not C++ code. The OP clearly stated that he is a beginner and his problem was with scanf. Instead of confusing him with one of the many other ways this could be done I decided to simply try to answer his question.

---

### Post by hakermania on 2010-02-15
Yeah, you're right!
Although thx everybody!

---

