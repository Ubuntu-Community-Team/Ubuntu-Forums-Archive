---
title: "[SOLVED] Object Arrays in Java"
date: 2008-04-19
forum: Programming Talk
---

### Post by brennydoogles on 2008-04-19
I am working on some homework for my Java class, and I seem to have hit a few bumps in the road, possibly due to some logical errors. The project involves reading and writing student data to a text file, and storing the student data in an array. I have quite a bit of the code written, but I am having a hard time with one particular part. I need to scan through all of the student records from the text file, and return all of the student objects who are Grad Students. The idea I had for this was to use a for loop to cycle through all of the students (stored in an array), and add every grad student to another array using an if statement such as:

```
 public static Student[] gradStudents(Student[] students)
        {
            Student[] gradStudents = new Student[LIMIT];
            for (int i=0; i < numberOfStudentsInArray(students); i++)
            {
                if (students[i].getMajor() = "G")
                {
                     gradStudents += this;
                }
                
            }
            return gradStudents;
        }
```

The problem is that I am getting errors that I have never seen before, such as:

```
Compiling 1 source file to /home/brendon/Documents/csci 1250/workspace/processStudents/build/classes
/home/brendon/Documents/csci 1250/workspace/processStudents/src/ProcessStudents.java:176: unexpected type
required: variable
found   : value
                if (students[i].getMajor() = 'G')
/home/brendon/Documents/csci 1250/workspace/processStudents/src/ProcessStudents.java:178: non-static variable this cannot be referenced from a static context
                     gradStudents += this;
/home/brendon/Documents/csci 1250/workspace/processStudents/src/ProcessStudents.java:178: operator + cannot be applied to Student[],ProcessStudents
                     gradStudents += this;
3 errors
BUILD FAILED (total time: 1 second)
```

I am not looking for someone to do my homework for me, but rather to give me a gentle nudge in the right direction. We barely covered arrays in class, so I am sure that I could be missing some important piece of information. Thanks so much!!

---

### Post by CptPicard on 2008-04-19
It's the "gradStudents += this" line. It's just simply nonsense. :) You don't add to arrays by doing a +=, and "this" refers to the object the method you're in belongs to; the way you're using "this" simply doesn't carry the meaning I think you think it does.

---

### Post by dwhitney67 on 2008-04-20
> **brennydoogles said:**
> 
```
 public static Student[] gradStudents(Student[] students)
        {
            Student[] gradStudents = new Student[LIMIT];
            for (int i=0; i < numberOfStudentsInArray(students); i++)
            {
                if (students[i].getMajor() = "G")
                {
                     gradStudents += this;
                }
                
            }
            return gradStudents;
        }
```


Why have to limited the number of graduate students using LIMIT?  Perhaps there are more than this limit??

Why do you have a method called numberOfStudentsInArray()??  Each array has a property that indicates the length of the array.

When you are checking if the student is a graduate or not, you are performing an assignment, not a comparison.

The usage of "this" is not applicable to static methods.

Hopefully these hints will put you on the right track.

---

### Post by Tomosaur on 2008-04-20
Ok - first of all, if you don't know for certain the number of gradStudents, you shouldn't use an array, not even if you know that the number of students will never exceed some number. There are exceptions to this obviously, but unless you know exactly the number of spaces you'll need in your array, generally just don't use them.

When you don't know what limit to use, you should use some dynamically expanding data type, such as an ArrayList (check the Java API). They're a bit more clunky to use than an array, but at least you won't be running into NullPointerException all the time.

Secondly, to find the length of an array, just use the following (if your array is called myArray): int length = myArray.length;

To get the length of an ArrayList, use: myArrayList.size();

Thirdly, when you're checking for equality in an if statement, you use ==, not just a single =, like this:
```

if(students[i].getMajor() == "G"){
    //blah blah blah
}
```


Finally, 'this' is a constant used by Java, referring to the instance of the class which this method is in. Not only can you not use += to add things to an array, but you're trying to add an instance of whichever class your code is in to an array. To add something to an array, you use the following format:

array[index] = value;

So let's say you have an array of integers, and you want to add the number 4 to the third space in the array:

myArray[2] = 4;

Arrays count from 0, so the FIRST space is 0, second is 1, third is 2 etc etc.

Hope that helps :)

---

### Post by CptPicard on 2008-04-20
Tomosaur, equality comparison of strings doesn't work that way. If it is a char, 'G', then you can do == 'G'. If it's a String, it's got to be something.equals("G").

Also, the reason why he has a method for counting students in array is of course that he probably has students in it and then the rest is nulls. So there needs to be a way to actually count how many places are in use in the array.

---

### Post by mike_g on 2008-04-20
I would use an array list for it and call its size. It may be a little extra work to get your head around at first, but in the long term it will make life a whole lot easier. 

I have this recurring problem where I keep using static arrays because at the time I think its easier, then it turns into a mess and I have to go back later and change it all to lists.

---

### Post by Tomosaur on 2008-04-20
> **CptPicard said:**
> Tomosaur, equality comparison of strings doesn't work that way. If it is a char, 'G', then you can do == 'G'. If it's a String, it's got to be something.equals("G").
Actually, you can compare strings using ==, but it's a bit confusing.

String literals are fine to compare using ==, but with objects of **type** String, you must use s.equals(p).

If you compare a literal with an object, you have to use s.equals aswell.

It depends on how the string returned by Student.getMajor() was defined.

It's better form to use s.equals, but it's not always necessary.

> 
Also, the reason why he has a method for counting students in array is of course that he probably has students in it and then the rest is nulls. So there needs to be a way to actually count how many places are in use in the array.That was my point - you should never have an array if there are going to be nulls in it. If you need an array but don't know how many values it is going to actually hold, use an ArrayList - that's what it's there for.

---

### Post by brennydoogles on 2008-04-20
Thanks all for the hints, I'm sure they will help me get back on the right track. As for the quirkiness of the methodologies used in this program, part of it is because of specifications laid out by the professor (having us practice certain aspects of Java), and part of it is that we are all first year Java students, and haven't learned some of the things that would make more sense in this particular situation. Thanks all for your help, I will post back in a bit and let you know if I got it working correctly, and how.

---

### Post by brennydoogles on 2008-04-20
Ok, so I made a few changes, and here is what I currently have working:

```
public static Student[] gradStudents(Student[] students)
        {
            Student[] gradStudents = new Student[LIMIT];
            int n = 0;
            for (int i=0; i < numberOfStudentsInArray(students); i++)
            {
                if (students[i].getStudentType() == 'G')
                {
                   gradStudents[n] = students[i];
                   n++;
                }
                
            }
            return gradStudents;
        }
```


Thank you all so much for your help!!

---

### Post by brennydoogles on 2008-04-20
::::EDIT::::

Naturally, after typing up an enormously long question, I find the typo in my code that fixes the functionality of my code. Thanks for all of the help!!!

---

