---
title: "Segmentation error: core dumped"
date: 2015-01-27
forum: Programming Talk
---

### Post by Zach_Bresser on 2015-01-27
I understand that the error message is usually due to a faulty pointer but I cannot figure it out, I have narrowed it done to a block of code though.  Can anyone see a problem with my code.


```
void classSchedule::upGPA(classSchedule schedule[], int& numElems){
    int i = 0;
    while (schedule[i].classNumber != -1)
    {
        if (schedule[i].currentGPA > schedule[i + 1].currentGPA)
        {
            classSchedule temp;
            temp.Schedule();


            temp.classDepartment = schedule[i].classDepartment;
            schedule[i].classDepartment = schedule[i + 1].classDepartment;
            schedule[i + 1].classDepartment = temp.classDepartment;


            temp.classNumber = schedule[i].classNumber;
            schedule[i].classNumber = schedule[i + 1].classNumber;
            schedule[i + 1].classNumber = temp.classNumber;


            temp.creditHours = schedule[i].creditHours;
            schedule[i].creditHours = schedule[i+1].creditHours;
            schedule[i + 1].creditHours = temp.creditHours;


            temp.teacherLastName = schedule[i].teacherLastName;
            schedule[i].teacherLastName = schedule[i + 1].teacherLastName;
            schedule[i + 1].teacherLastName = temp.teacherLastName;


            temp.teacherFirstName = schedule[i].teacherFirstName;
            schedule[i].teacherFirstName = schedule[i + 1].teacherFirstName;
            schedule[i + 1].teacherFirstName = temp.teacherFirstName;


            temp.roomWingAndNumber = schedule[i].roomWingAndNumber;
            schedule[i].roomWingAndNumber = schedule[i + 1].roomWingAndNumber;
            schedule[i + 1].roomWingAndNumber = temp.roomWingAndNumber;


            temp.currentGPA = schedule[i].currentGPA;
            schedule[i].currentGPA = schedule[i + 1].currentGPA;
            schedule[i + 1].currentGPA = temp.currentGPA;


            temp.displayOrNot = schedule[i].displayOrNot;
            schedule[i].displayOrNot = schedule[i + 1].displayOrNot;
            schedule[i + 1].displayOrNot = temp.displayOrNot;
        }
        i++;
    }


}
```

I have instances of a class each hold information about a class(the educational type not c++ class) I needed to sort it by gpa so i created a temp instance of that then transferred it as I would for an array value.

---

### Post by 3246251196 on 2015-01-27
You do not initialise your ```
int i;
```

If you do not initialise it then the value it contains is garbage. For example it may be the value 247. Then, you try and access the 248th element of schedule which may not exist.

Try ```
int i = 0;
```

I believe you can get away with not initialising things in global splace as they are implicitly set to zero, but not stack variables.

---

### Post by Zach_Bresser on 2015-01-27
Ah well that was a stupid mistake on my part, but it did not fix the problem.

---

### Post by lisati on 2015-01-27
A couple of thoughts:

[LIST]
[*]Is there an entry in the passed data where schedule[i].classNumber == -1? 
[*]Is numElems usable in the condition for the while loop?
[/LIST]

---

### Post by steeldriver on 2015-01-27
... also you test for [FONT=courier new]schedule[i].classNumber == -1[/FONT] (presumably to indicate the last element of [FONT=courier new]schedule[/FONT]) but you then attempt to access [FONT=courier new]schedule[i+1][/FONT] in several places

---

### Post by Zach_Bresser on 2015-01-28
Alright so i changed the while loop to 

```
while(i < numElems)
``` and it got rid of the segmentation error but my code does not sort it now? it just displays it like it regularly would.

---

### Post by spjackson on 2015-01-28
I'm guessing that this is homework and you are not allowed to use things like std::vector and std::sort or a copy assignment operator for class classSchedule.

I think you need to do some debugging of your own, e.g. how many times do you expect the while loop to be executed, and how many times is it actually executed?

What sorting algorithm are you trying to use? Whatever it is, your implementation doesn't do it. It's a single pass through the array.

---

### Post by Zach_Bresser on 2015-01-28
> I'm guessing that this is homework and you are not allowed to use things like std::vector and std::sort or a copy assignment operator for class classSchedule.
It is homework, but we are allowed to use anything in the c++ language, we just can't leave the language such as putting this information in sql is not allowed. 

> I think you need to do some debugging of your own, e.g. how many times do you expect the while loop to be executed, and how many times is it actually executed?

I guess I only expected it to run once but that wouldn't make sense because schedule[0] might be < than schedule[1] but schedule[2] might be less than schedule[0] and it wouldn't compare it. 

How would you suggest I take this situation. The code even looks messy and I can't seem to figure it out.

---

### Post by Zach_Bresser on 2015-01-28
I was thinking something like this might be better:
```

void sortArray(classSchedule schedule[], int numElems) 
{ 
    classSchedule temp;
    temp.Schedule();
    int end, counter; 
   for (end = numElems - 1; end >= 0; end--) 
   { 
       for (int counter = 0; counter < end; counter++) 
       { 
          if (schedule[counter].currentGPA < schedule[counter + 1]) 
          { 
             
            temp.classDepartment = schedule[i].classDepartment;
            schedule[i].classDepartment = schedule[i + 1].classDepartment;
            schedule[i + 1].classDepartment = temp.classDepartment;

            temp.classNumber = schedule[i].classNumber;
            schedule[i].classNumber = schedule[i + 1].classNumber;
            schedule[i + 1].classNumber = temp.classNumber;

            temp.creditHours = schedule[i].creditHours;
            schedule[i].creditHours = schedule[i+1].creditHours;
            schedule[i + 1].creditHours = temp.creditHours;

            temp.teacherLastName = schedule[i].teacherLastName;
            schedule[i].teacherLastName = schedule[i + 1].teacherLastName;
            schedule[i + 1].teacherLastName = temp.teacherLastName;

            temp.teacherFirstName = schedule[i].teacherFirstName;
            schedule[i].teacherFirstName = schedule[i + 1].teacherFirstName;
            schedule[i + 1].teacherFirstName = temp.teacherFirstName;

            temp.roomWingAndNumber = schedule[i].roomWingAndNumber;
            schedule[i].roomWingAndNumber = schedule[i + 1].roomWingAndNumber;
            schedule[i + 1].roomWingAndNumber = temp.roomWingAndNumber;

            temp.currentGPA = schedule[i].currentGPA;
            schedule[i].currentGPA = schedule[i + 1].currentGPA;
            schedule[i + 1].currentGPA = temp.currentGPA;

            temp.displayOrNot = schedule[i].displayOrNot;
            schedule[i].displayOrNot = schedule[i + 1].displayOrNot;
            schedule[i + 1].displayOrNot = temp.displayOrNot;

          } 
       } 
   } 
} 
```

I will try it when I get home since I'm in class right now, but does that seem like it would work?

---

