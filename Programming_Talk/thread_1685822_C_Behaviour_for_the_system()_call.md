---
title: "C Behaviour for the system() call"
date: 2011-02-11
forum: Programming Talk
---

### Post by CaptainMark on 2011-02-11
Hi, 
Im a bit confused about the behaviour of the system()  call for C programming, watch out, complete beginner here, when I read about the system("clear") function to clear the terminal window i added a few calls for it into my basic number quiz, heres my modest beginners program, ```
// Number Quiz

#include<stdio.h>

main() {
    int    i=            0,
        i_questions=0,
        i_number1=    0,
        i_number2=    0,
        i_answer=    0,
        i_correct=    0,
        i_score    =    0;
        
    srand(time(0));

    system("clear");
    printf("\nWelome to the quiz.\n\nHow many questions would you like to answer\n>>>");
    scanf("%d", &i_questions);
    system("clear");
    
    for(i=0; i<i_questions; i++) {
        i_number1=    rand() %10 + 1;
        i_number2=    rand() %10 + 1;
        i_correct=    i_number1 + i_number2;
        printf("\n\n\nWhat is %d + %d?\n>>>", i_number1, i_number2);
        scanf("%d", &i_answer);

        if(i_answer == i_correct) {
            printf("Correct!");
            i_score++;
        }
        else {
            printf("No sorry the answer was %d", i_correct);
        }// end if else
        system("clear");
    }// end for

    if (i_questions == 0) {
        printf("*****!\n");
    } else {
        printf("Well done on completing the quiz\n");
        printf("Your total score was:\t%d/%d\n",i_score, i_questions);
    }// end if else 
    
}// end main


```What im confused by is the timing of the 'clear' at the end of the for loop, its the last statement in the for loop so i expected that after i type my answer to the question the if/else statement would print a correct/incorrect message, which wouldnt show due to it being immediately cleared and then back to the top of the for loop three new lines and another question. 
However what happens when i type my answer and press enter is the previous question clears then the correct/incorrect message is displayed followed by only two new lines and another question. 
Can anybody explain simply what is happening to make this happen, 

Thanks for your time,
Mark

EDIT: Ive attached shots of what I mean

---

### Post by Arndt on 2011-02-11
> **CaptainMark said:**
> Hi, 
Im a bit confused about the behaviour of the system()  call for C programming, watch out, complete beginner here, when I read about the system("clear") function to clear the terminal window i added a few calls for it into my basic number quiz, heres my modest beginners program, ```
// Number Quiz

#include<stdio.h>

main() {
    int    i=            0,
        i_questions=0,
        i_number1=    0,
        i_number2=    0,
        i_answer=    0,
        i_correct=    0,
        i_score    =    0;
        
    srand(time(0));

    system("clear");
    printf("\nWelome to the quiz.\n\nHow many questions would you like to answer\n>>>");
    scanf("%d", &i_questions);
    system("clear");
    
    for(i=0; i<i_questions; i++) {
        i_number1=    rand() %10 + 1;
        i_number2=    rand() %10 + 1;
        i_correct=    i_number1 + i_number2;
        printf("\n\n\nWhat is %d + %d?\n>>>", i_number1, i_number2);
        scanf("%d", &i_answer);

        if(i_answer == i_correct) {
            printf("Correct!");
            i_score++;
        }
        else {
            printf("No sorry the answer was %d", i_correct);
        }// end if else
        system("clear");
    }// end for

    if (i_questions == 0) {
        printf("*****!\n");
    } else {
        printf("Well done on completing the quiz\n");
        printf("Your total score was:\t%d/%d\n",i_score, i_questions);
    }// end if else 
    
}// end main


```What im confused by is the timing of the 'clear' at the end of the for loop, its the last statement in the for loop so i expected that after i type my answer to the question the if/else statement would print a correct/incorrect message, which wouldnt show due to it being immediately cleared and then back to the top of the for loop three new lines and another question. 
However what happens when i type my answer and press enter is the previous question clears then the correct/incorrect message is displayed followed by only two new lines and another question. 
Can anybody explain simply what is happening to make this happen, 

Thanks for your time,
Mark

EDIT: Ive attached shots of what I mean

The behaviour you see could be because stdout in the program is line-buffered, and you don't print whole lines. Try replacing

 ```
          printf("No sorry the answer was %d", i_correct);
```

with
 ```
          printf("No sorry the answer was %d\n", i_correct);
```

---

### Post by CaptainMark on 2011-02-11
Yes this works, thanks. So nothing is printed until a new line character is detected, i assumed that it was the semi colons that printed whatever was in the buffer

---

### Post by Arndt on 2011-02-11
> **CaptainMark said:**
> Yes this works, thanks. So nothing is printed until a new line character is detected, i assumed that it was the semi colons that printed whatever was in the buffer

No, the semicolons are just for the compiler to know where statements end. They are not there at runtime.

---

