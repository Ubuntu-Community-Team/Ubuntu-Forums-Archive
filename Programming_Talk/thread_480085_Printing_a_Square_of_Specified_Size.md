---
title: "Printing a Square of Specified Size"
date: 2007-06-21
forum: Programming Talk
---

### Post by TreeFinger on 2007-06-21
I am working with C++. I am reading a book and right now the second chapter has to do with control structures. I am finished reading the chapter and I am now working on some of the review exercises. I have a question about a program in which the user inputs a specified integer length and the program prints a square of that size. So if user inputs 5 the program will print:
```

*****
*    *
*    *
*    *
*****

```

The problem specifies that the program should work with integers between 1-20. I understand this would be easily done with 20 if statements. I would like to make a more efficient program though and would like someone to explain how.

---

### Post by Smygis on 2007-06-21
Something like:
```

for(int i=1; i <= NumberFromUser; i++) // A loop who will run one time per line.
{
   if (i==1 || i == NumberFromUser) // If it is the top or bottom line:
   {
      for(int i=1; i <= NumberFromUser; i++) // print a line of "*"
         cout << "*";
      cout << endl;
   }
   else // Else
   {
      for(int i=1; i <= NumberFromUser; i++) // step thru each char in the line
         if (i==1 || i == NumberFromUser) // If it is the first ot the last.
            cout << "*"; // print a "*"
         else
            cout << " "; // otherwise print a space.
      cout << endl;
   }
}

```

---

### Post by TreeFinger on 2007-06-21
Hah, well I will test out your code and get back to you. 

I am learning C++ because in the fall one of my classes is going to be C++. I have a heavy course load coming up and I would like to get an easy A in C++ :p .

Little off topic here but another class I am taking is going to be dealing with database. How could I prepare for that class?

--edit

It sure does work! I just wish I understood it!

---

### Post by Smygis on 2007-06-21
I added comments to it.

Well, Database. My only experience with those is for 4 hours ago. When i made the 20 minute wiki with turbogears. What i lie, 20 minutes. I am 3 hours in to the project and still not done. 

But considering i dont know anything about (X)HTML, CSS, JS and all the other stuff. I think its quite good.

---

