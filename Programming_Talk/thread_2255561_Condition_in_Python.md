---
title: "Condition in Python"
date: 2014-12-05
forum: Programming Talk
---

### Post by eight.coffee.beans on 2014-12-05
So, I started using Python because we've started coding in it at university and now we have second homework to do.
I did the bigger piece of the code, however I'm stuck in making a condition.

The full task is this:
```

Create a calculator which will add up, multiply, divide or subtract the two numbers that user enters.
When calculator finishes the process it must ask user if he/she wants to repeat the program, also if user wants to divide the number by 0 make the program give error message.

```

Here's what I've got:

```

#LINE TO REPEAT THE PROGRAM
restart = "Y"

while restart == "Y":

    #PRINTING OUT THE MAIN MENU
    print("Select one option please:")
    print("----------------------------")
    print("1 for adding up")
    print("2 for subtracting")
    print("3 for multiplying")
    print("4 for dividing")
    print("5 for exponenting")
    print("---------------------------")

    #REQUEST FOR USER TO CHOOSE
    choice_raw = input("Your choice is? \n")

    #CONVERTING INPUT INTO INTEGER
    choice = int(choice_raw)
    #IF INPUT IS GREATER THAN 5 ERROR APPEARS
    if choice > 5:
        print("No function found for the number:", choice)
        
    #IF NUMBER ONE IS CHOSEN 
    elif choice == 1:
        print("Adding up")
        first_number = input("Enter first number: \n")
        second_number = input("Enter second number: \n")
        result_one = int(first_number) + int(second_number)
        print("Rezultat:", result_one)
        
    #IF NUMBER TWO IS CHOSEN
    elif choice == 2:
        print("Subtracting")
        first_number = input("Enter first number: \n")
        second_number = input("Enter second number: \n")
        result_two = int(first_number) - int(second_number)
        print("Rezultat:", result_two)

    #IF NUMBER THREE IS CHOSEN
    elif choice == 3:
        print("Multiplying")
       first_number = input("Enter first number: \n")
        second_number = input("Enter second number: \n")
        result_three = int(first_number) * int(second_number)
        print("Rezultat:", result_three)

    #IF NUMBER FOUR IS CHOSEN
    elif choice == 4: 
        print("Dividing")
        first_number = input("Enter first number: \n")
        second_number = input("Enter second number: \n")
        result_four = float(first_number) / float(second_number)
        print("Rezultat:", result_four)

    #IF NUMBER FIVE IS CHOSEN
    else:
        print("Odabrali ste potenciranje")
       first_number = input("Enter base number: \n")
        second_number = input("Enter exponent number: \n")
        result_five = int(first_number) ** int(second_number)
        print("Rezultat:", result_five)

        #ASKING USER TO RESTART THE CODE
    restart = input("Restar (Y/n)? \n") 


```

I've tried using if or elif inside if, but I got some errors.
Please remember that this has to be done in 'newbie' way and please if possible explain what you did. 

In advance thanks to all.

---

### Post by spjackson on 2014-12-06
The only errors I get from running the above code are:
```

$ python3 calc.py
  File "calc.py", line 44
    first_number = input("Enter first number: \n")
                                                 ^
IndentationError: unindent does not match any outer indentation level

```
and the same for line 60. In each case you need an extra space before first_number so that it lines up with the adjacent lines.

Beyond that, there are other errors that can arise depending on input, but those are more advanced issues.

---

### Post by eight.coffee.beans on 2014-12-06
> **spjackson said:**
> The only errors I get from running the above code are:
```

$ python3 calc.py
  File "calc.py", line 44
    first_number = input("Enter first number: \n")
                                                 ^
IndentationError: unindent does not match any outer indentation level

```
and the same for line 60. In each case you need an extra space before first_number so that it lines up with the adjacent lines.

Beyond that, there are other errors that can arise depending on input, but those are more advanced issues.

Sorry, I probably deleted it when translating in English. 
The code above works, but it doesn't give error when dividing by 0, I have no clue how to do that. :(

---

### Post by ofnuts on 2014-12-06
> **eight.coffee.beans said:**
> So, I started using Python because we've started coding in it at university and now we have second homework to do.
I did the bigger piece of the code, however I'm stuck in making a condition.

The full task is this:
```

Create a calculator which will add up, multiply, divide or subtract the two numbers that user enters.
When calculator finishes the process it must ask user if he/she wants to repeat the program, also if user wants to divide the number by 0 make the program give error message.

```

Here's what I've got:

[...]

I've tried using if or elif inside if, but I got some errors.
Please remember that this has to be done in 'newbie' way and please if possible explain what you did. 

In advance thanks to all.

Can you show us what you tried?

---

### Post by eight.coffee.beans on 2014-12-06
> **ofnuts said:**
> Can you show us what you tried?

```

#IF NUMBER FOUR IS CHOSEN
    elif choice == 4: 
        print("Dividing")
        first_number = input("Enter first number: \n")
        second_number = input("Enter second number: \n")
        if second_number = 0:
           print("Dividing by 0 is not supported")
        else:
           result_four = float(first_number) / float(second_number)
           print("Rezultat:", result_four)


```

I get some error and I assume you can't put *if *inside of *elif*, but I don't know how else would I check if the number entered is 0.

---

### Post by spjackson on 2014-12-06
In your first post you said "I got some errors" and here you say:
> **eight.coffee.beans said:**
> 
I get some error and I assume you can't put *if *inside of *elif*, but I don't know how else would I check if the number entered is 0.

It is not a good idea to tell us that you got an error without specifying what error you got. In my previous post, I corrected errors which were perhaps due to pasting the code. You didn't show us the code that you were really getting errors with. We are not clairvoyant.

With your new code I get:
```

$ python3 calc.py
  File "calc.py", line 54
    if second_number = 0:
                     ^
SyntaxError: invalid syntax

```
That is nothing to do with the context of being with elif. That line on its own is a syntax error. If you compare '=' with all the other lines where you test for equality, you should get a good idea of one thing that is wrong. Also, second_number is not an int.

Maybe this isn't your problem, but I don't know because I don't know what error you get. However, there is nothing that prevents putting "*if *inside of *elif".*

---

### Post by flaymond on 2014-12-06
Have you check spaces in your code? Spaces is also a critical in Python.

---

### Post by eight.coffee.beans on 2014-12-06
> **spjackson said:**
> In your first post you said "I got some errors" and here you say:


It is not a good idea to tell us that you got an error without specifying what error you got. In my previous post, I corrected errors which were perhaps due to pasting the code. You didn't show us the code that you were really getting errors with. We are not clairvoyant.

With your new code I get:
```

$ python3 calc.py
  File "calc.py", line 54
    if second_number = 0:
                     ^
SyntaxError: invalid syntax

```
That is nothing to do with the context of being with elif. That line on its own is a syntax error. If you compare '=' with all the other lines where you test for equality, you should get a good idea of one thing that is wrong. Also, second_number is not an int.

Maybe this isn't your problem, but I don't know because I don't know what error you get. However, there is nothing that prevents putting "*if *inside of *elif".*
[I]
SyntaxError: inconsistent use of tabs and spaces in indentation[/I]

^Is the error I'm getting.
Here's the code that I have originally written in Croatian, so I apologize if you don't understand some things here, because it seems that I've made some mistakes while translating into English.

```

# Varijabla za ponavljanje
restart = "Y"

while restart == "Y":

    #Ispisivanje izbornika kalkulatora
    print("Izaberite jednu od operacija")
    print("----------------------------")
    print("Unesite 1 za zbrajanje")
    print("Unesite 2 za oduzimanje")
    print("Unesite 3 za mno&#382;enje")
    print("Unesite 4 za dijeljenje")
    print("Unesite 5 za potenciranje")
    print("---------------------------")

    #Zahtjev da korisnik odabere &#382;eljenu operaciju
    choice_raw = input("Va&#353; izbor je? \n")
    #Konvertiranje inputa u integer
    choice = int(choice_raw)
    #Ukoliko je uneseni broj ve&#263;i od broja 5 pojavljuje se pogre&#353;ka
    if choice > 5:
        print("Nije prona&#273;ena matemati&#269;ka operacija za:", choice)
        
    #Ukoliko je unesen broj jedan pokre&#263;e se zbrajanje    
    elif choice == 1:
        print("Odabrali ste zbrajanje")
        broj = input("Unesite broj: \n")
        zbroj = zbroj + broj
        print("Rezultat:", result_one)
        
    #Ukoliko je unesen broj dva pokre&#263;e se oduzimanje
    elif choice == 2:
        print("Odabrali ste oduzimanje")
        first_number = input("Unesite prvi broj: \n")
        second_number = input("Unesite drugi broj: \n")
        result_two = int(first_number) - int(second_number)
        print("Rezultat:", result_two)

    #Ukoliko je unesen broj tri pokre&#263;e se mno&#382;enje
    elif choice == 3:
        print("Odabrali ste mno&#382;enje")
        first_number = input("Unesite prvi broj: \n")
        second_number = input("Unesite drugi broj: \n")
        result_three = int(first_number) * int(second_number)
        print("Rezultat:", result_three)

    [B]#Ukoliko je unesen broj &#269;etiri pokre&#263;e se dijeljenje
    elif choice == 4: 
        print("Odabrali ste dijeljenje")
        first_number = input("Unesite prvi broj: \n")
        second_number = input("Unesite drugi broj: \n")
        if second_number == int(0):
                        print("Dijeljenje nulom nije podr&#382;ano:")  #This is error message 
                else:
                        result_four = float(first_number) / float(second_number)
                        print("Rezultat:", result_four)
[/B]
    #Ukoliko je unesen broj pet pokre&#263;e se potenciranje
    else:
        print("Odabrali ste potenciranje")
        first_number = input("Unesite bazu: \n")
        second_number = input("Unesite potenciju: \n")
        result_five = int(first_number) ** int(second_number)
        print("Rezultat:", result_five)

        #Ispitujemo korisnika da li ho&#263;e ponovno pokrenuti program
    restart = input("Ponoviti program (Y/n)? \n") 


```

---

### Post by ofnuts on 2014-12-06
The problem is that the "else:" should be indented exactly to the same level as the matching "if" (and indented the same way: same combination of spaces and/or tabs for both) like your last "else" that is matching your "elif"s.

---

### Post by zacktu on 2014-12-07
Read about

try:
[INDENT]do your arithmetic[/INDENT]
except: 
[INDENT]handle the error in a graceful way so that you don't get error messages from the Python interpreter[/INDENT]

---

