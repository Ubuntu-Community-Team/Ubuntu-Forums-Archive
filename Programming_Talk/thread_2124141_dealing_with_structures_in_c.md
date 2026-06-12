---
title: "dealing with structures in c"
date: 2013-03-09
forum: Programming Talk
---

### Post by vera0501 on 2013-03-09
we were asked to code a certain pogram in c that would enable a user to: add a student, view all the students, search for a student and exit, with the use of structures. the program should act like a students' portal. 
i have this 'tentative code' that when compiled, would print an error of Segmentation fault (core dumped). so this how my code goes:

```
#include<stdio.h>

typedef struct tag1{
    int day, year, month;
}Date;

typedef struct tag2{
    int number;
    char name[50];
    char course[30];
    Date birthday;
}Record;
    


main(){
    int choice, n, i=0;
    Record student[200];

    //printing of menu:
    printf("Choose from the menu:\n");
    printf("     [1] Add Student\n");
    printf("     [2] Search Student\n");
    printf("     [3] View All\n");
    printf("     [4] Exit\n");
    scanf("%d", &choice);
    
    
    if((choice>=1)&&(choice<=4)){
        if(choice==1){
            
            printf("Enter student number:\n");
            scanf("%d", &student[n].number);    
    
            printf("Enter the name of the student:\n");        
            scanf("%[^\n]", student[n].name);
        
            printf("Enter month of birth:\n");
            scanf("%d", &student[n].birthday.month);

            printf("Enter day of birth:\n");
            scanf("%d", &student[n].birthday.day);

            printf("Enter year of birth:\n");
            scanf("%d", &student[n].birthday.year);

            printf("Enter course:\n");
            scanf("%[^\n]", student[n].course);
            
            n++;
        }
        if(choice==2){
        while(i<n){
            printf("%d\n", student[n].number);
            printf("%s", student[n].name);
            printf("%d/%d/%d", student[n].birthday.month, student[n].birthday.day,student[n].birthday.year);
            printf("%s", student[n].course);
            i++;
            }
        }
        }
        
        
    }
```


i was just half way through because i have no idea on how i will search for a student. hope you have any suggestions for me to improve my code. thanks :D

---

### Post by Some Penguin on 2013-03-10
1) You never initialize n, but you do read from it.

You're not compiling with -Wall, are you?  You should -- and pay attention to every warning it spews.

2) Whenever you have a loop like

```

while (i < n) {
   ...
   i++
}

```

and you never actually *use* i in your iteration other than through incrementing it, but instead use n as an array index... you're probably doing it wrong.

---

### Post by ofnuts on 2013-03-10
Several things:

  
[LIST]
[*]you only ask things once, and then exit the program...
[*]don't use "n" and "i" as a variable names. Give your variable meaningful names. Then you'll discover that you mean need to have variables named "studentsInArray", "newStudent", "scannedStudent"...
[*]think about which array item receives the input for case 1.
[*]your implementation of choice=2 looks a lot (minus the bugs mentioned above) to what the implementation of choice 3 would be...
[*]Having a first check on the choice "if((choice>=1)&&(choice<=4)){" and then having an "if" condition on each valid choice serves no purpose. Skip the pretest and have a fall-through case.
[*]... which bring us to the next remark: in C there is a "switch" instruction exactly for this kind of thing.
[*]"search for student" is ill-defined: search on what? number? name? birth date?
[*]the order of the fields in the Date structure is weird (and not even the order in which you ask them). In a bigger application it could come back to haunt you.
[*]if you don't use the structure tags just skip them instead of calling them tag1, tag2...
[*]you should really have one function to process each of the menu options, otherwise you code will become an unwieldy mess very quickly. And you can also have one function to display the menu and return the choice (and process invalid answers)
[/LIST]

So your problem isn't really with the structures...

---

### Post by trent.josephsen on 2013-03-10
> **ofnuts said:**
> 
[LIST][*]if you don't use the structure tags just skip them instead of calling them tag1, tag2...[/LIST]

Better idea, don't use typedef to hide the word "struct" and just call them "struct Record" and "struct Date". There are good times and bad times to use typedef. This is one of the bad times.

---

