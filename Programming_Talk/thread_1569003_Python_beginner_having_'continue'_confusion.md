---
title: "Python beginner having 'continue' confusion"
date: 2010-09-06
forum: Programming Talk
---

### Post by CaptainMark on 2010-09-06
Im learning python (really early days still so go easy on me) and having trouble figuring out where the continue statement returns to. Heres my code so far, its a training thing so its a really stupid program. ```
#!/usr/bin/python3
# character creation
# a program that lets you edit attribute for a rpg character
# mark skinner 06/09/2010

# variables
stats={'strength':0,'health':0,'wisdom':0,'dexterity':0}
choice=None
freepoints=30

# user choice
while choice!=0:
    print('''You have the following options:
0. Quit
1. Distribute points from scratch
2. Remove points from an attribute
3. Add points to an attribute
4. Veiw current point usage''')
    choice=input('\nPlease enter your choice number. ')

# distribute points
    if choice=='1':
        freepoints=30
        print('\nAll points have been reset.\nYou currently have',freepoints,'free points.\n\
If you use too many points you will start again. ')
        input('Press enter to start. ')
        for element in stats:
            print('\nCurrent attribute:',element.title(),'\nAvailable points:',freepoints)
            change=input('How many points would you like? ')
            change=int(change)
            stats[element]=change
            freepoints-=change
            print('The attribute',element,'is set to:',stats[element])
        if freepoints<0:
            print('\nYou have used too many points.\nAll points have been reset to zero. ')
            for element in stats:
            stats[element]=0
            input('Press enter to continue. ')
            continue

``` The thing im having trouble understanding  is at the bottom i was expecting 'if freepoints<0' to print the message, reset the stats and return the user up to just after the line '# distibute points' ready to start entering points again but instead it returns to the main menu options and prints them again, where am i going wrong and how do i correct my code to do what i intended?

---

### Post by DaithiF on 2010-09-06
Hi, a continue statement takes effect on its enclosing loop.  The only loop that encloses your continue statement is the one that begins with the while choice != 0 line.

and so the continue statement causes execution to jump back to that point.  You mention you wanted to jump back to the line around #distribute points, but you don't have any loop starting there.

---

### Post by Bodsda on 2010-09-06
Try moving your loop down a few lines, start it 'after' you have printed the menu, or nest another loop inside your current one. 
 
Bodsda

---

### Post by CaptainMark on 2010-09-06
i see, i thought that it would 'continue' back to an 'if' statement as well as loops, thanks for clearing that up

---

### Post by GenBattle on 2010-09-06
Continue just skips ahead to the next iteration in the loop, so it jumps from wherever the continue statement is to the start of the loop.

---

