---
title: "Python questoin"
date: 2009-07-25
forum: Programming Talk
---

### Post by ice_qube on 2009-07-25
i keep getting 

UnboundLocalError: local variable 'end' referenced before assignment

but im really not understanding this error.... the module is called just like all the other ones above it but ono that one im getting an error. somebody help me please

```
from random import randrange

def MENU():
    dead = 0
    fuel = 200.0
    enemy = randrange(40, 350)
    ammo = 5
    travel = 0
    answ = 'n'
    obs = randrange(0,200)
     
    if dead !=1:
        while dead != 1:
            print'_________________________________________'
            print 'obs',obs
            print 'nme',enemy
            print
            print '!   Inventory      !'
            print 
            print 'Travel  =',travel
            print 'Fuel    =' ,fuel
            print 'Ammo    =',ammo
            print
            print '***MENU****'
            print '1 Fire'
            print '2 Move Forward'
            print '3 Move Backward'
            print '4 Exit'
            print'________________________________________'
            choice = raw_input ('Enter Selection number')
            try:
                choice = int(choice)
                if choice == 1:
                    dead, ammo = fireWeapon(ammo, enemy, travel)
                elif choice == 2:
                    fuel, travel = moveFwd(fuel, travel, obs)
                elif choice == 3:
                    fuel, travel = moveBkwd(fuel, travel)
##ERROR##ERROR##ERROR##
                elif choice == 4:
                    dead, ans = end()                                       #error sumhhow????
                else:
                    print
                    print 'invalid opton'
                    print
            except str(choice):
                print
                print 'You entered a letter rather than a number'
                print ' please try again'
                print


        
        
def fireWeapon(ammo, enemy, travel):
    while ammo>0:
        if ammo > 0:
            firedstnc = input ('How far would you like to fire your weapon? ')
            print
            nmepos = enemy
            mypos = travel + firedstnc
            target = nmepos - mypos
            if target >40:
                print ' You left your enemy unharmed'
                print
                ammo = ammo - 1
                dead = 0
                return dead, ammo
            elif 20 < target <= 40:
                print ' You damaged the enemy'
                print
                ammo = ammo - 1
                dead = 0
                return dead, ammo
            elif 0<= target <= 20:
                print ' You destroyed the enemy'
                print ' You won the game'
                print
                joe = raw_input ('press enter to close')
                ammo = ammo - 1
                dead = 1
                return dead, ammo
            else:
                print' You left your enemy unharmed'
                print
                ammo = ammo - 1
                dead = 0
                return dead, ammo
    while ammo<=0:
        print 'your out of ammo'
        print ' You LOSE'
        print
        print 'press enter to close'
        ammo = 0
        dead = 1
        return dead, ammo
    
    

def moveFwd(fuel, travel, obs):
    choice = 0
    while fuel >= 0 and choice != 1:
        if fuel >= 0:
            mvfwd = input ('how far would you like to go Forward?')
            k = travel + mvfwd
            if mvfwd >= obs or k >=obs:
                distance = obs-travel-1
                print ' thers an obstruction in your way'
                print 'you can only move foreward', distance
                return fuel, travel
            elif mvfwd<obs:
                print 'You are able to move forward ',mvfwd,' feet'
                if fuel ==0:
                    print ' Your fuel is depleted'
                    print
                    return fuel, travel
                elif mvfwd > fuel:
                    print 'Your destination exceeds available gas'
                    print 'Try again'
                    print
                    return fuel, travel
                elif mvfwd <= fuel:
                    fuel = fuel - mvfwd
                    travel = travel + mvfwd
                    return fuel, travel

                


def moveBkwd(fuel, travel):
    choice = 0
    
    while fuel >= 0 and choice != 1:
        if fuel >= 0:
            mvbkwd = input ('how far would you like to go Backward?')
            if fuel ==0:
                print 'Your fuel is depleted'
                print
                return fuel, travel
            if mvbkwd > fuel:
                print ' Your destination exceeds whats possible'
                print
                return fuel, travel
            elif mvbkwd <= fuel:
                fuel = fuel - mvbkwd
                travel = travel - mvbkwd
                return fuel, travel
                


def end(): 
    ans = raw_input(' Are you sure you want to end?')
    if ans == 'yes' or ans == 'y':
        print 'Thank you for playing'
        nd = raw_input ('Press Enter to close')        
        dead = 1
        return dead, ans
        
    elif ans == 'no' or ans == 'n':
        dead = 0
        return dead, ans
                        

MENU()


```

---

### Post by smartbei on 2009-07-25
That is odd - it works for me. Could you try running the exact code you pasted in the forum to see if the bug still exists? (Perhaps you accidentally ran an older version)

---

### Post by matmatmat on 2009-07-25
Seen above post

---

### Post by ice_qube on 2009-07-25
i apologise i posted the wrong one... its this code (this one has a lil  password verification thingy in it)  but its the same problem

```
#Build 4.3 STEADY!
#Random Enemy coordinates, Random obstacle coordinates
#Must enter pass twice 2 verify and re enter to login
#only prob is when you type the number 4 proggy crashes
from random import randrange

def MENU():
    dead = 0
    fuel = 200.0
    enemy = randrange(40, 350)
    ammo = 5
    travel = 0
    answ = 'n'
    obs = randrange(0,200)
    curpwd = raw_input('Choose PWD')
    print
    pwd = raw_input ('Please RE-Enter pwd')
    print
    if curpwd == pwd:
        password = pwd
    elif curpwd != pwd:
        print ' Sorry you have entered the wrong password'
        MENU()
    pwd2=raw_input('please enter your pwd to login')
    if password == pwd2:
        print ('You have successfully logged in!')
        print
    elif password !=pwd2:
        print
        print ('you have entered the wrong password')
        print ('reload the application to try again')
        print
        end = raw_input('press enter to close')
        dead = 1
   

    if dead !=1:
        while dead != 1:
            print'_________________________________________'
            print 'obs',obs
            print 'nme',enemy
            print
            print '!   Inventory      !'
            print 
            print 'Travel  =',travel
            print 'Fuel    =' ,fuel
            print 'Ammo    =',ammo
            print
            print '***MENU****'
            print '1 Fire'
            print '2 Move Forward'
            print '3 Move Backward'
            print '4 Exit'
            print'________________________________________'
            choice = raw_input ('Enter Selection number')
            try:
                choice = int(choice)
                if choice == 1:
                    dead, ammo = fireWeapon(ammo, enemy, travel)
                elif choice == 2:
                    fuel, travel = moveFwd(fuel, travel, obs)
                elif choice == 3:
                    fuel, travel = moveBkwd(fuel, travel)
                elif choice == 4:                
###########ERROR IS HERE FOR SOME REASON##################
                    dead, ans = end()#error sumhhow????
                else:
                    print
                    print 'invalid opton'
                    print
            except str(choice):
                print
                print 'You entered a letter rather than a number'
                print ' please try again'
                print


        
        
def fireWeapon(ammo, enemy, travel):
    while ammo>0:
        if ammo > 0:
            firedstnc = input ('How far would you like to fire your weapon? ')
            print
            nmepos = enemy
            mypos = travel + firedstnc
            target = nmepos - mypos
            if target >40:
                print ' You left your enemy unharmed'
                print
                ammo = ammo - 1
                dead = 0
                return dead, ammo
            elif 20 < target <= 40:
                print ' You damaged the enemy'
                print
                ammo = ammo - 1
                dead = 0
                return dead, ammo
            elif 0<= target <= 20:
                print ' You destroyed the enemy'
                print ' You won the game'
                print
                joe = raw_input ('press enter to close')
                ammo = ammo - 1
                dead = 1
                return dead, ammo
            else:
                print' You left your enemy unharmed'
                print
                ammo = ammo - 1
                dead = 0
                return dead, ammo
    while ammo<=0:
        print 'your out of ammo'
        print ' You LOSE'
        print
        print 'press enter to close'
        ammo = 0
        dead = 1
        return dead, ammo
    
    

def moveFwd(fuel, travel, obs):
    choice = 0
    while fuel >= 0 and choice != 1:
        if fuel >= 0:
            mvfwd = input ('how far would you like to go Forward?')
            k = travel + mvfwd
            if mvfwd >= obs or k >=obs:
                distance = obs-travel-1
                print ' thers an obstruction in your way'
                print 'you can only move foreward', distance
                return fuel, travel
            elif mvfwd<obs:
                print 'You are able to move forward ',mvfwd,' feet'
                if fuel ==0:
                    print ' Your fuel is depleted'
                    print
                    return fuel, travel
                elif mvfwd > fuel:
                    print 'Your destination exceeds available gas'
                    print 'Try again'
                    print
                    return fuel, travel
                elif mvfwd <= fuel:
                    fuel = fuel - mvfwd
                    travel = travel + mvfwd
                    return fuel, travel

                


def moveBkwd(fuel, travel):
    choice = 0
    
    while fuel >= 0 and choice != 1:
        if fuel >= 0:
            mvbkwd = input ('how far would you like to go Backward?')
            if fuel ==0:
                print 'Your fuel is depleted'
                print
                return fuel, travel
            if mvbkwd > fuel:
                print ' Your destination exceeds whats possible'
                print
                return fuel, travel
            elif mvbkwd <= fuel:
                fuel = fuel - mvbkwd
                travel = travel - mvbkwd
                return fuel, travel
                


def end(): 
    ans = raw_input(' Are you sure you want to end?')
    if ans == 'yes' or ans == 'y':
        print 'Thank you for playing'
        nd = raw_input ('Press Enter to close')        
        dead = 1
        return dead, ans
        
    elif ans == 'no' or ans == 'n':
        dead = 0
        return dead, ans
                        

MENU()

```

---

### Post by MadCow108 on 2009-07-25
the variable
end = raw_input('press enter to close')
has the same name as the function end()
rename one of them

---

### Post by ice_qube on 2009-07-25
sweeet...im mad i didnt notice that tho. but thanks alot :D

---

### Post by ice_qube on 2009-07-25
so is that a rule? that a variable cant have the same name as a funtion?

---

