---
title: "Help on python"
date: 2012-05-29
forum: Programming Talk
---

### Post by learner py on 2012-05-29
Hello im new to this forum and i have a question about python. Could you please point to the syntax errors in this code? I attached the original problem in case you were wondering what was i trying to do.

####Problem 1 
####Write a program to calculate the credit card balance after one year if a person only pays the 
####minimum monthly payment required by the credit card company each month. 
####Use raw_input() to ask for the following three floating point numbers: 
####1.  the outstanding balance on the credit card 
####2.  annual interest rate 
####3.  minimum monthly payment rate 
####For each month, print the minimum monthly payment, remaining balance, principle paid in the 
####format shown in the test cases below. All numbers should be rounded to the nearest penny. 
####Finally, print the result, which should include the total amount paid that year and the remaining 
####balance. 
####
##
##x = float(raw_input('Enter the outstanding amount on your credit card'))
##y = float(raw_input('Enter the annual interest rate'))
##z = float(raw_input('Minimum monthly payment rate'))
##i = 0;
##while (i < 13):
##    print(i,end= '')
##    i = i + 1
##    x*y = ans
##    print 'Minimum monthly payment', ans
##    (y/12)*x = ans1
##    print 'Interest paid', ans1
##    ans - ans1 = PP
##    print 'Principal paid', PP

---

### Post by lukeiamyourfather on 2012-05-29
First thing, post your code using the code tags.

```

# Like this
print 'So we can tell what the hell it says'

```

I can see a few issues, like this.

```
i = 0;
```

Python doesn't use semicolons to terminate statements. Also this.

```
print 'Minimum monthly payment', ans
```

Should probably be this.

```
print 'Minimum monthly payment, %s' % (ans)
```

In general start with what the interpreter tells you, like what line and column is causing the problem. Those error messages tell you exactly what the problem is most of the time.

---

### Post by The Cog on 2012-05-29
This is a syntax error:
```
print (i,end= '')
```
You can't put an assignment like "end = ''" inside a tuple, you need two separate statements:
```
end = ''
print (i, end)
```

Also, this is a syntax error (you make this same mistake 3 times):
```
x*y = ans
```
An assignment like this always has the variable you are assigning to on the left hand side of the equals, and the formula for the value you want to give it on the right hand side, like this:
```
ans = x * y
```

Please put your code inside code tags when posting, otherwise it's very difficult to read. You can add code tags by pressing the button for advanced editing, and using the # button above the edit box

---

### Post by learner py on 2012-05-29
Thank you both very much for you help. I was finally able to make the program run although it doesn't do what i want it to do would you mind taking a look at to see what can i improve it in? I already corrected the various syntax errors it had but i can't seem to make the process use the information from the month before, it keeps doing the same calculations for each month
Again, thanks for the help!

```
x = float(raw_input('Enter the outstanding amount on your credit card'))
y = float(raw_input('Enter the annual interest rate'))
z = float(raw_input('Minimum monthly payment rate'))
i = 1
while (i < 13):
    print('Month'), i
    i = i + 1
    ans =  x * z
    print('Minimum monthly payment'), ans
    ans1 =  (y/12) * x
    print('Interest paid'), ans1
    PP = ans - ans1
    print('Principal paid'), PP
    RB = x - PP
    print('Remaining Balance'), RB
```

---

### Post by ofnuts on 2012-05-29
> **learner py said:**
> Thank you both very much for you help. I was finally able to make the program run although it doesn't do what i want it to do would you mind taking a look at to see what can i improve it in? I already corrected the various syntax errors it had but i can't seem to make the process use the information from the month before, it keeps doing the same calculations for each month
Again, thanks for the help!



Not very surprising given that no computation seems to involve  the variable "i"

A more pythonic way to write the same loop is to use:
```

for i in range(1,13):

```

Also, do yourself a favor and use descriptive names for your variables, like interest_rate, payment_rate, month...

---

### Post by learner py on 2012-05-29
ofnuts thank for the suggestions, This is the most recent version of the code:
```
outstanding_amt = float(raw_input('Enter the outstanding amount on your credit card'))
interest_rate = float(raw_input('Enter the annual interest rate'))
monthly_pay_rate = float(raw_input('Minimum monthly payment rate'))
i = 0 # the variable i represents the months passed

for i in range(0,13):
    i = i + 1
    print('Month'), i
    ans =  outstanding_amt * monthly_pay_rate
    print('Minimum monthly payment'), ans
    ans1 =  (interest_rate/12) * outstanding_amt
    PP = ans - ans1
    print('Principal paid'), PP
    RB = outstanding_amt - PP
    print('Remaining Balance'), RB
```
 
i am stuck trying to make the code use the information from the previous month each time it does the calculations, any hints? thanks in advance

---

### Post by ofnuts on 2012-05-30
```

i = 0 # the variable i represents the months passed 

```
This is exactly the kind of thing to avoid. Why not:
```

month=0

```
For the rest, I think your problem is that even the math involved aren't clear in your mind, so don't expect to produce proper code until this part is done. Express your solution in plain english, or use comments to put a short sentence next to each important instruction explaining why it is useful.

---

### Post by Barrucadu on 2012-05-30
> **learner py said:**
> 
for i in range(0,13):
    i = i + 1

Don't do that, you don't need to increment `i` in the loop body, `range` takes care of that for you.

---

### Post by learner py on 2012-05-30
Thanks for your feedback everyone ive made more corrections on my code and i think i figured out how to do the recurring effect.

```
outstanding_amt = float(raw_input('Enter the outstanding amount on your credit card'))
interest_rate = float(raw_input('Enter the annual interest rate'))
monthly_pay_rate = float(raw_input('Minimum monthly payment rate'))
month = 0

for month in range(1,13):
    print('Month'), month
    ans =  outstanding_amt * monthly_pay_rate
    print('Minimum monthly payment'), ans
    ans1 =  (interest_rate/12) * outstanding_amt
    PP = ans - ans1
    print('Principle paid'), PP
    RB = outstanding_amt - PP
    print('Remaining Balance'), RB
    if month in range (1,13) :
        outstanding_amt = RB
Total_amount_paid = (ans+ans+ans+ans+ans+ans+ans+ans+ans+ans+ans+ans)
# this is supposed to add up all of the Minimumm monthly payments done
print 'Result'
print 'Total amount paid', Total_amount_paid
print 'Remaining balance', RB
```

However i still can't make the program tell me the correct total amount paid. As a related question, is there any way i can make the program round the numbers to 2 decimal places? I'm sorry but this is the second program i try to write, with the first one asking me my name and date of birth. :lolflag:

---

### Post by Vaphell on 2012-05-30
Total_amount_paid = (ans+ans+ans+ans+ans+ans+ans+ans+ans+ans+ans+ans)

this is an equivalent of 12*ans_calculated_for_month_12 (when the loop ends, ans holds 12th value and you use it 12 times to calculate Total_amount_paid)

you need something like 
```
Total_amount_paid = 0
for month in range(...)
  ans = ...
  Total_amount_paid = Total_amount_paid+ans
```
edit: ok, i didn't notice that ans =  outstanding_amt * monthly_pay_rate is constant - if so you don't have to calculate the same value 12 times. Run it outside the loop.


also this if doesn't make much sense and can be skipped, you iterate over 1-12 so the condition will be always true
```
**if month in range(1,13):**
        outstanding_amt = RB
```

[http://stackoverflow.com/questions/455612/python-limiting-floats-to-two-decimal-points](http://stackoverflow.com/questions/455612/python-limiting-floats-to-two-decimal-points)

---

### Post by learner py on 2012-06-01
Thank you all for your help, i finally made it work. The end version was this:
```
outstanding_amt = float(raw_input('Enter the outstanding amount on your credit card'))
interest_rate = float(raw_input('Enter the annual interest rate'))
monthly_pay_rate = float(raw_input('Minimum monthly payment rate'))
month = 0
Total_amount_paid = 0
for month in range(1,13):
    print('Month'), month
    ans =  outstanding_amt * monthly_pay_rate
    print('Minimum monthly payment'), ('%.2f' % ans)
    ans1 =  (interest_rate/12) * outstanding_amt
    PP = ans - ans1
    print('Principle paid'), ('%.2f' % PP)
    RB = outstanding_amt - PP
    print('Remaining Balance'), ('%.2f' % RB)
    outstanding_amt = RB
    Total_amount_paid = Total_amount_paid + ans
# this is supposed to add up all of the Minimumm monthly payments done
print 'Result'
print 'Total amount paid', ('%.2f' % Total_amount_paid)
print 'Remaining balance', ('%.2f' % RB)
```

---

### Post by David Andersson on 2012-06-06
> **The Cog said:**
> This is a syntax error:
```
print (i,end= '')
```
You can't put an assignment like "end = ''" inside a tuple, you need two separate statements:
```
end = ''
print (i, end)
```

In python3 this is valid syntax, and means "do not add newline, so output from the next print will continue on the same line".
```
print (i,end='')
```
In python version 2.x one puts a comma at the end.
```
print i,
```
The output from the next print will output will continue on the same line with a space inbetween.

---

