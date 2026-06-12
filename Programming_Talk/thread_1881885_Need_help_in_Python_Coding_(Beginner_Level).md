---
title: "Need help in Python Coding (Beginner Level)"
date: 2011-11-16
forum: Programming Talk
---

### Post by blackpink on 2011-11-16
I need help my homework about python coding, everybody says its beginner level but i am confused, is there anybody knows about python coding?
Here is homework it has 3 questions.

CSE-101 Assignment 2 / Python Coding

1. You are working on a bacteria that has 10 important chromosomes. These chromosomes are symbolized with the numbers from 0 to 9. We are trying to understand the effects of mutation on the bacteria chromosomes. The mutation function which is below mutates all 10 chromosomes of bacteria in each iteration. Our aim is to reach the first chromosome structure after applying the mutations on bacteria. You should create a Python code that observes the effects of mutation on the bacteria. Your code should print the number of successful trials in 1000 trial. The first chromosome structure of bacteria is:

Bacteria=[1,4,3,7,2,5,3,9,8,0]
The mutation function of the bacteria is:
mutation (chromosome x) = (((Number representation of chromosome x) + 3) * 5) mod 89 Your print-out should be like below:
Genetic match ensured at 659 . trial


2. You should take a 4-digit number from user as a password and create a Python code that encrypts the password. Your code should prevent the user from entering a number smaller or larger than 4 digit. Your code should encrypt the password according to the schema as below:
1->b 5->f 9->j 2->c 6->g 0->a 3->d 7->h
4->e 8->i
Your code should convert every digit of the number to letter and print it in reverse order. After finding the digits of the number, do not use if statements to convert these digits to letters. Instead, you have to put every numbers and letters in a LIST get the numbers to
letters. If you use some oprations like if x=1: print (“b”) on your code you will get zero. Your print-out should be like below:
      Enter your password:4587
      h
      i
      f
      e

3. You are going to examine grade data of a class in a Python code. The name of students and their grades are like below:
name_list = ["john", "jill", "adriana", "bill", "george", "lucas",
"marcus", "chen", "sakis", "eldrine"]
      mt1_list = [30, 70, 10, 40, 100, 90, 30, 50, 5, 40]
      final_list = [20, 10, 30, 40, 60, 100, 60, 35, 20, 60]
The final has %60 and the midterm has %40 effect on overall grades. Your code should have a
menu which should work forever until the user wishes to stop it. You can use sys.exit() function to terminate the program but you have to find out how to use it in Phyton. Your menu should have 3 other elements and seem like below:
Menu:
1. Print the name of the person who get the highest grade in midterm1 
2. Print the name of the person who get the lowest grade in final
3. Print the name of the person who get the highest grade at overall 
4. Exit
Enter your choice:
The user should enter a number from the menu and then the program should print the result according to the menu. For instance, if the user entered 2, the program should print the name of the student who has taken the lowest grade in final exam. If the user enters a number which is out of the menu range, you should warn the user and re-show the menu until the user enters a valid option.

GOOD LUCK! [COLOR="Red"](i don't know if i am lucky?)[/COLOR]
&#65532;&#65532;&#65532;&#65532;&#65532;&#65532;&#65532;&#65532;&#65532;&#65532;You should answer the homework using Python codes. Your python file name should suit the format “studentnumberHW2code2.py”

---

### Post by surfer on 2011-11-16
i don't think, anyone here will solve your homework for you. instead of just posting the whole assignment, ask the questions you have on your way to a solution.

a primer into python is:
[http://www.diveintopython.net/](http://www.diveintopython.net/)

and if you do not know how to write the code into a text file and how to execute that code. well... maybe ask that.

---

### Post by 11jmb on 2011-11-16
[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

Don't ask the forums to do your homework for you. If you have specific questions such as trouble understanding an error message that google doesn't answer sufficiently, go ahead and ask here.

---

### Post by surfer on 2011-11-16
i couldn't resist to do the first one. if i understood correctly, here's a start to the solution.

that should get you started to do the rest.


```
#!/usr/bin/python


generation_0 = [1,4,3,7,2,5,3,9,8,0]

def mutation_function(n):
    '''
    the mutation function for 1 chromosome
    '''
    return ((n + 3) * 5) % 89

def next_generation(generation_n):
    '''
    apply the mutation function to the list of chromosomes
    '''
    return map(mutation_function, generation_n)



```

---

### Post by blackpink on 2011-11-16
> **surfer said:**
> i couldn't resist to do the first one. if i understood correctly, here's a start to the solution.

that should get you started to do the rest.


```
#!/usr/bin/python


generation_0 = [1,4,3,7,2,5,3,9,8,0]

def mutation_function(n):
    '''
    the mutation function for 1 chromosome
    '''
    return ((n + 3) * 5) % 89

def next_generation(generation_n):
    '''
    apply the mutation function to the list of chromosomes
    '''
    return map(mutation_function, generation_n)



```

i know that nobody have to help my homework. You have to be an angel, thnx for your help. =)

---

### Post by karlson on 2011-11-16
> **blackpink said:**
> i know that nobody have to help my homework. You have to be an angel, thnx for your help. =)

By forum rules homework threads are terminated with extreme prejudice.  I'd say we are waiting on a moderator to descend on this.

---

### Post by oldfred on 2011-11-16
The Code of Conduct says:

> While we are happy to serve as a resource for hints and for asking  questions when you get stuck and need a little help, the Ubuntu Forums  is not a homework service. Please do not post your homework assignments  expecting someone else to do it for you. Any such threads will be taken  offline and warnings or infractions may be issued.

Thread Closed.

---

