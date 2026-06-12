---
title: "Basic python"
date: 2011-04-05
forum: Programming Talk
---

### Post by antagonist388 on 2011-04-05
I'm supposed to create a program that chargers the user per character typed per word, then adds a space after the word and charge them for that too. The charges are a nickel and a penny respectively. Also, you are supposed to be able to enter either X or x and stop the program and receive your total. If you never break out of the program, it will automatically do so after 80 characters. After it breaks out it is supposed to read you your total charge and your sentence.

For some reason my program doesn't do that. My first problem is that if I enter x or X, it doesn't exit out of the loop.

My next problem is that it doesn't add up the total for some reason!

I think my problem has something to do with local and global variables.. but I really have no idea how to fix it... any tips?

Any tips on how to avoid global variables altogether? I tried to but when I didnt put them in at the start it came up with an error.. specifically...

this one

[PHP]What is the word?word
0.05
0.1
0.15000000000000002
0.2
Traceback (most recent call last):
  File "C:/Python32/hardproblem1.py", line 29, in <module>
    main()
  File "C:/Python32/hardproblem1.py", line 25, in main
    totalcost=totalcost+subtotal
NameError: global name 'subtotal' is not defined
[/PHP]I had it print the subtotal each time so I could make sure that wasn't the problem with the total cost

Here's the program:

[PHP]totalcost=0
subtotal=0
word=' '
value=False
def function(word):
    z=len(word)
    subtotal=0
    for i in range (len(word)):
        y = ord(word[i])
        if word == 'x' or word== 'X':
            value=True
            break
        if ord('a')<=y<=ord('z') or ord('0')<=y<= ord('9') or ord('A')<=y<=ord('Z'):
            cost=.05
            subtotal=subtotal+cost
            print(subtotal)
        else:
            print("Invalid character")
    subtotal=subtotal+.01
    word=word+' '
def main():
    sentence=''
    totalcost=0
    word=input("What is the word?")
    while len(sentence)<=80 and (value==False):
        sentence=sentence+word
        function(word)
        totalcost=totalcost+subtotal
        word=input("What is the word?")
    print(sentence)
    print(totalcost)
main()[/PHP]

---

### Post by unknownPoster on 2011-04-06
The subtotal variable is local to the function named "function." As such, your main function can't "see" subtotal and therefore it is undefined.

I would suggest redesigning your algorithm. Specifically, look into a return value for your "function" function.

As a side note, I would suggest following a better naming convention. Having a function called function is just confusing.

---

### Post by 102jon on 2011-04-06
One word: homework.

---

### Post by unknownPoster on 2011-04-06
> **102jon said:**
> One word: homework.

I fail to see how the OP breaks any of the rules pertaining to this forum. He shows us work he has done and asks for assistance, not how to solve the problem.

No need to cry wolf.

---

### Post by 102jon on 2011-04-07
> **unknownPoster said:**
> I fail to see how the OP breaks any of the rules pertaining to this forum. He shows us work he has done and asks for assistance, not how to solve the problem.

No need to cry wolf.

Yes, but it is a homework question and personally I would like to see students do everything they can to figure out the problem themselves before resorting to forums for help. I don't think the OP's efforts were very exhaustive.

---

### Post by raydeen on 2011-04-13
Does this really need functions at all? I wrote an equivalent to the program with one while loop, 16 lines total. Unless the functions are required by the teacher, it looks like there's a lot of overkill going on here.

---

