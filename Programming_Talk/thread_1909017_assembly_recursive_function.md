---
title: "assembly recursive function"
date: 2012-01-14
forum: Programming Talk
---

### Post by fooball on 2012-01-14
Hi people,have  this problem problem probably with (not)understanding  stack or something but its making me crazy slowly because i've been  google-ing it for 2 days
and i only have more questions now.What is not clear to me is once i enter **factorial: **and reach [COLOR=Red]** call factorial  **[/COLOR]how anything between call factorial and end_factorial:  gets executed.As per my understanding (obviously wrong :)) once [COLOR=Red]**call factorial**[/COLOR] is executed it should jump back to [COLOR=Black]**factorial:**[/COLOR] ,start executing again until %eax is 1 and then jump to **[COLOR=Blue]end_factorial:[/COLOR]**?!
I copied this from the book and its AT&T syntax. 
many thanks in advance


.section .data

.section .text

.globl _start

.globl factorial 

_start:
pushl $4
call factorial 
addl $4, %esp

movl %eax, %ebx 
movl $1, %eax
$0x80

.type factorial,@function
**factorial:**

pushl %ebp

movl %esp, %ebp 

movl 8(%ebp), %eax 

cmpl $1, %eax

je end_factorial

decl %eax

pushl %eax

**[COLOR=Red]call factorial  [/COLOR]**                      #this is the one 

movl 8(%ebp), %ebx

[COLOR=Black]imull[/COLOR] %ebx, %eax

**[COLOR=Blue]end_factorial:[/COLOR]**

movl %ebp, %esp

popl %ebp

ret

---

### Post by SGFzc2U= on 2012-01-14
Remember that it has two possible ends. If eax is one,q it ends. If eax isn't one, it continues to call itself until eax is one. It's kind of hard to explain. If you don't understand my explanation at all, follow the flow of that program on paper, marking every register and stack.

Also, remember that each iteration of factorial has its own stack frame.

---

### Post by fooball on 2012-01-14
yes i think thats my problem,not knowing how return actually works .i got a debugger gui  (because im kinda scared of gdb  ) so I will try to see what is going on.
thanks and i let you know (or ask more questions ;))

---

### Post by fooball on 2012-01-16
ok i got it(roughly) but will still need a lot of practice to get used to. key was like *SGFzc2U=* said in separate stack frames :).thanks.

 Now i just wanted to ask is it really so hard to find working gui for gdb or its only me?i guess i tried all which are in repositories(i dont wanna name them because of the risk of offending some zealous fan ;)), everithing goes nice with install no failed dependencies no errors but they just dont work. Irony i guess, me talking about recursion and almost end up trying to debug the debugger (recursively of course)

also tried IDA through wine but for that one i couldn't find debugger plugin.i did found one thats working, edb or evans debugger .it showed me how stack works but even with that one exit value of above program was 18(and not 24 as it should be).edb warns you however that you are running i386 programon x86_64 machine and that that is not  implemented yet.

At the end i found emacs gdb mode and i plan to stick with this one.Emacs is hard but i guess better that than debug the debugger .  
[http://www.gnu.org/software/emacs/manual/html_node/emacs/Debuggers.html#Debuggers](http://www.gnu.org/software/emacs/manual/html_node/emacs/Debuggers.html#Debuggers)
I am writing this if someone sometimes runs in the same gui problems
have a nice day

---

### Post by Arndt on 2012-01-17
> **fooball said:**
> ok i got it(roughly) but will still need a lot of practice to get used to. key was like *SGFzc2U=* said in separate stack frames :).thanks.

 Now i just wanted to ask is it really so hard to find working gui for gdb or its only me?i guess i tried all which are in repositories(i dont wanna name them because of the risk of offending some zealous fan ;)), everithing goes nice with install no failed dependencies no errors but they just dont work. Irony i guess, me talking about recursion and almost end up trying to debug the debugger (recursively of course)

also tried IDA through wine but for that one i couldn't find debugger plugin.i did found one thats working, edb or evans debugger .it showed me how stack works but even with that one exit value of above program was 18(and not 24 as it should be).edb warns you however that you are running i386 programon x86_64 machine and that that is not  implemented yet.


Maybe it was showing you the exit value as hexadecimal.

---

### Post by fooball on 2012-01-17
You are right man .many thanks.never thought of that.looot of practice awaits .
i guess if i had used number > F it would save me some headache :) .And appologies to Evan of course

i realized that i should write 9 instead of F here but  i went to run program with 17 which will give far more than 255 and when i checked exit status with echo $? it gave me 0.but in edb value in %rbx was ok.Did kernel did that or what?

---

