---
title: "ISO:Feedback [Python]"
date: 2009-12-27
forum: Programming Talk
---

### Post by YourMomsASmurph on 2009-12-27
Well let's start this by saying that I am a beginner programmer. this is my first real attempt at learning programming, and I only started a few days ago.

That said I would like some constructive criticism on the first 2 programs I wrote 

(Was looking back to some of your old threads and found the "Beginners challenges" and started to work on them.)

(I would like to know areas of my code that can be improved -- If there are better ways to do some of the things I have tried.)

**Bottles of Beer Code.**

[php]###Program to write the lyrics to the song 99 bottles of beer on the wall.

btls_br=99

while btls_br<=1:#Creates infinite loop as long as btls_br is greater than 1.
    
    print btls_br,"bottles of beer on the wall,",btls_br,"bottles of beer."

    btls_br=btls_br-1#Reduce the number of bottles on the next section of the loop by 1.

    print "Take one down pass it around;",btls_br,"bottles of beer on the wall."
    print " "
    
#when btls_br>1 this section will take over.
    
print btls_br,"bottle of beer on the wall,",btls_br,"bottle of beer."
print "Take one down pass it around; no more bottles of beer on the wall."
print " "

print "No more bottles of beer on the wall, no more bottles of beer."
print "Go to the store and buy some more; 99 bottles of beer on the wall."[/php][B]
Input Code.[/B]

[php]
#Beginner test 2

#Code must ask for first and last name as well as ID number.
#Name cannot start with a space OR be left blank.
#Age must be a positive number between 1-200
#ID number must be 7 !!numbers!!\
#Code must then say the persons first name, last name, age and id number. In that order.

#Code used for testing purposes.
##usrf_name='Andrew'
##usrl_name='Lawrence'
##usr_age=21
##usr_id=1605978

#--------------------------------------------------Code starts here-----------------------------------------------------

print "Type 'quit' to quit at anytime."
print " "

#Need to have a value to avoid "undefined" error.

quit_test='frggr'

#[if quit_test!='quit'] tests if the term quit was entered. If it was,
#everything after that point will not pass the test :. the program will end.

usrf_name_test='frggr'

while usrf_name_test=='frggr':

    quit_test=usrf_name=raw_input("Please enter your first name:")

#Using ' ' character because it comes before ' ' in the ordering.
#a better way to do this would be appreciated.

    if usrf_name<='?':

        print "Name cannot start with a space, or be left blank."
        print " "
    else:
        usrf_name_test='bwah'

if quit_test!='quit':
        
    usrl_name_test='frggr'

    while usrl_name_test=='frggr':

        quit_test=usrl_name=raw_input("Please enter your last name:")

        if usrl_name<='?':
            print "Name cannot start with a space, or be left blank."
            print " "
        else:
            usrl_name_test='bwah'

if quit_test!='quit':

    usr_age_test='frggr'

    while usr_age_test=='frggr':
        try:    
            quit_test=usr_age=raw_input("Please enter your age:")

            if int(usr_age)<=0:
                print "... That is not your real age."
                print " "

            else:
                if int(usr_age)>=200:
                    print "... Your not serious are you?"
                    print " "

                else:
                    usr_age_test='bwah'
                    
        except ValueError:
            if quit_test!='quit':
            
                print "Try again. Use whole numbers please."
                print " "

            else:
                usr_age_test='bwah'

if quit_test!='quit':

    usr_id_test='frggr'

    while usr_id_test=='frggr':
        try:
            quit_test=usr_id=raw_input("Please enter your ID number.(7 numbers from 1000000-9999999):")

            if int(usr_id)<=1000000:
                print "That is not a valid ID number."
                print " "
                
            else:
                if int(usr_id)>=9999999:
                    print "That is not a valid ID number."
                    print " "
                    
                else:
                    usr_id_test='bwah'
                    
        except ValueError:
            if quit_test!='quit':
            
                print "Your ID number Should be 7 NUMBERS long. Try again."
                print " "

            else:
                usr_id_test='bwah'

#This is to ensure that name / age / id number do not come out as 'quit'

if quit_test!='quit':
    print "Your name is,",usrf_name,usrl_name,". You are",usr_age,"years old and your ID number is",usr_id,"." #This code could be replaced later to make a list or something.
[/php]

---

### Post by BenAshton24 on 2009-12-27
Looks pretty good :)

I would change the method that you use to decrease your variable by 1. You can do it this way: **btls_br-=1**

Instead of using "while" you could use a for loop:
```

countdown = range(1,100)
countdown.reverse()
for i in countdown:
    print i, "Bottles"

```

Also If you are using a version of python before 3 then your print statements are fine, however, if you are using python then print is now a function and should be changed to something like "print ('Hello')"

Good luck, hope this helps you.
Ben

---

### Post by YourMomsASmurph on 2009-12-27
Thx for the help -- am curious though

what does btls_br-=1 say exactly (Its nice knowing smaller codes to do a task, but it is nicer to know why I am going to use it)

---

### Post by BenAshton24 on 2009-12-27
> **YourMomsASmurph said:**
> Thx for the help -- am curious though

what does btls_br-=1 say exactly (Its nice knowing smaller codes to do a task, but it is nicer to know why I am going to use it)

-= Basically just says, subtract the following number from the variable. There is also += for addition.

Ben.

---

### Post by jollysnowman on 2009-12-27
```
###Program to write the lyrics to the song 99 bottles of beer on the wall.

btls_br=99

while btls_br<=1:#Creates infinite loop as long as btls_br is greater than 1.
    
    print btls_br,"bottles of beer on the wall,",btls_br,"bottles of beer."

    btls_br=btls_br-1#Reduce the number of bottles on the next section of the loop by 1.

    print "Take one down pass it around;",btls_br,"bottles of beer on the wall."
    print " "
    
#when btls_br>1 this section will take over.
    
print btls_br,"bottle of beer on the wall,",btls_br,"bottle of beer."
print "Take one down pass it around; no more bottles of beer on the wall."
print " "

print "No more bottles of beer on the wall, no more bottles of beer."
print "Go to the store and buy some more; 99 bottles of beer on the wall."
```

I would check the guard clause on your while loop.

For iterating over a series of numbers (as you're doing), I prefer to use a while loop. But when accessing objects in a list, words in a dictionary for example, I use the for-in loop. IMO it makes more sense this way. For example, when reading code, I would say to myself, "While i is less than 5, do this, and increment i" or, "For each string in dict, print its definition."

It's a little different now in Python with xrange() and range() (You can now say, "for each i in the range 1 to 100, do this"), but I first learned C and Java, so it just stuck.

---

### Post by BenAshton24 on 2009-12-27
Also, have a look at the second example here: [http://en.literateprograms.org/99_Bottles_of_Beer_%28Python%29](http://en.literateprograms.org/99_Bottles_of_Beer_%28Python%29)

Ben.

---

