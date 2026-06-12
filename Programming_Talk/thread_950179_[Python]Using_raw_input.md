---
title: "[Python]Using raw_input"
date: 2008-10-16
forum: Programming Talk
---

### Post by Slayeragb2 on 2008-10-16
Hello. I am new to Programming, and decided to make a calculator for something to do. How would I turn using input into raw_input.
I want to be able to make it survive someone inputting a string.

Here is the part of my code I am talking about:

[PHP]
loop=1

while loop==1:
    menu()
    choice=raw_input("What Option would you like to select?")
    if choice=="1":
        add1=input("What is the first number?")
        add2=input("What is the 2nd number?")
        print add1+add2
        print
    elif choice=="2":
        sub1=input("What is the first number?")
        sub2=input("What is the 2nd number?")
        print sub1-sub2
        print
    elif choice=="3":
        mult1=input("What is the first number?")
        mult2=input("What is the 2nd number?")
        print mult1*mult2*1.0
        print
    elif choice=="4":
        div1=input("What is the first number?")
        div2=input("What is the 2nd number?")
        print div1/div2*1.0
        print
    elif choice=="5":
        base=input("What is the base?")
        exp=input("What is the Exponet?")
        print base**exp
        print
    elif choice=="6":
        sqr=input("What number do you want to take the square root off?")
        print sqr**.5
        print
    elif choice=="7":
        print "Goodbye!"
        loop==0
    else:
        print "This is not a option"[/PHP]

I don't know if this is very "Python like" or not...
Any help would be nice (and help on making my code more "Python like" would be nice to).
Thanks!

---

### Post by mssever on 2008-10-16
> **Slayeragb2 said:**
> Hello. I am new to Programming, and decided to make a calculator for something to do. How would I turn using input into raw_input.
I want to be able to make it survive someone inputting a string.
[php]
loop=1

while loop==1:
    menu()
    choice=raw_input("What Option would you like to select?")
    if choice=="1":
        add1=input("What is the first number?")
        add2=input("What is the 2nd number?")
        print add1+add2
        print
# snip[/php]I don't know if this is very "Python like" or not...
Any help would be nice (and help on making my code more "Python like" would be nice to).
Thanks!
Some basic hints on your code: [php]while True:  # You don't need the loop variable
    menu()
    choice = int(raw_input("Prompt goes here"))
    if choice == 1:
        add1 = float(raw_input("First number?"))
        add2 = float(raw_input("Second number?"))
        print "%d\n" % add1 + add2[/php]
As a whole, your code shows that you're new to programming. Making a proper calculator would involve parsing mathematical expressions in standard form, which is probably beyond your skill level. So, while your approach isn't the best, I can't make any concrete big-picture suggestions at your skill level without thinking about it for a while. So, forge ahead!

---

### Post by Slayeragb2 on 2008-10-17
Thanks...
I have only been learning Python for a little while. I didn't know that you could turn a string into a integer like that.
This code was so that I could make something with what little I knew about Python, to keep me more motivated.

---

### Post by LaRoza on 2008-10-17
> **Slayeragb2 said:**
> Thanks...
I have only been learning Python for a little while. I didn't know that you could turn a string into a integer like that.
This code was so that I could make something with what little I knew about Python, to keep me more motivated.

Read this: [http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

You might find the challenges informative: [http://ubuntuforums.org/showthread.php?p=5499486](http://ubuntuforums.org/showthread.php?p=5499486)

---

### Post by Slayeragb2 on 2008-10-17
Thanks..
I have actually started on the challenges recently.
Okay.. I will read that.
Thanks.

---

