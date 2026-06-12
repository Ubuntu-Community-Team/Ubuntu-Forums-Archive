---
title: "Beginners programming challenge #25"
date: 2012-01-29
forum: Programming Talk
---

### Post by Bodsda on 2012-01-29
_[SIZE=4][COLOR=Red]Welcome to the 25th Beginners programming challenge.[/COLOR][/SIZE]_

This challenge is known by many different names. It is a logic puzzle that (according to some resources (unverified)) only est. 2% of the worlds population will be able to solve. Well, that assumption was made before computers were doing all the heavy lifting. I would now say that only 2% of programmers would be unable to brute force this puzzle :)

[U][B]Background
[/B][/U]
The challenge, should you choose to except it, is to write a solver for the Zebra Puzzle (aka, Einstein's Puzzle, Einstein's Riddle). The program, when run, should print the answer to the 2 questions at the end of the below quoted text. 

Note:  You are not expected to parse the text and computationally map out the issue before solving, I assume that you have read the rules and designed a program that, following those rules, and given facts, produces an answer to 2 questions. 

> [INDENT] 
[LIST=1]
[*]There are five houses.
[*]The Englishman lives in the red house.
[*]The Spaniard owns the dog.
[*]Coffee is drunk in the green house.
[*]The Ukrainian drinks tea.
[*]The green house is immediately to the right of the ivory house.
[*]The Old Gold smoker owns snails.
[*]Kools are smoked in the yellow house.
[*]Milk is drunk in the middle house.
[*]The Norwegian lives in the first house.
[*]The man who smokes Chesterfields lives in the house next to the man with the fox.
[*]Kools are smoked in the house next to the house where the horse is kept. [should be "... a house ...", see discussion below]
[*]The Lucky Strike smoker drinks orange juice.
[*]The Japanese smokes Parliaments.
[*]The Norwegian lives next to the blue house.
[/LIST]
 Now, who drinks water? Who owns the zebra? In the interest of clarity,  it must be added that each of the five houses is painted a different  color, and their inhabitants are of different national extractions, own  different pets, drink different beverages and smoke different brands of  American cigarets [sic]. One other thing: in statement 6, *right* means *your* right. [RIGHT]— Life International, *December 17, 1962*
[/RIGHT]
[/INDENT]

 _**Task**_

Write a program that solve the zebra puzzle. 
The program should output the answer to the questions:

[LIST=1]
[*]Who drinks water?
[*]Who owns the Zebra?
[/LIST]
 
[LIST=1]
[/LIST]
_**Cookie points**_

Cookie points will be awarded for the following extras

[LIST=1]
[*]The implementation of more than 1 algorithm for solving this (e.g. One brute force algorithm and 1 logic algorithm.)
[*]Solve these as well - [http://en.wikipedia.org/wiki/Zebra_Puzzle#Other_versions](http://en.wikipedia.org/wiki/Zebra_Puzzle#Other_versions)
[/LIST]

_***Disqualified Entries:***_

Any overly obfuscated code will be immediately disqualified without   account for programmers skill. Please remember that these challenges are   for beginners and therefore the code should be easily readable and  well  commented.

Any non-beginner entries will not be judged. Please use common sense   when posting code examples. Please do not give beginners a copy paste   solution before they have had a chance to try this for themselves.


_***Assistance:***_

If you require any help with this challenge please do not hesitate to   come and chat to the development focus group. We have a channel on   irc.freenode.net #ubuntu-beginners-dev
Or you can pm me

Have fun,
Happy coding

Bodsda
Ubuntu Beginners Team

---

### Post by schauerlich on 2012-01-29
I don't think anyone will be surprised to see prolog in here.

```
solve(WaterDrinker, ZebraOwner) :-
    %% There are five houses.
    Street = [[ C1,  N1,  P1,  D1,  S1 ],
              [ C2,  N2,  P2,  D2,  S2 ],
              [ C3,  N3,  P3,  D3,  S3 ],
              [ C4,  N4,  P4,  D4,  S4 ],
              [ C5,  N5,  P5,  D5,  S5 ]],

    %% The Englishman lives in the red house.
    member([red, english, _, _, _], Street),

    %% The Spaniard owns the dog.
    member([_, spaniard, dog, _, _], Street),

    %% Coffee is drunk in the green house.
    member([green, _, _, coffee, _], Street),

    %% The Ukrainian drinks tea.
    member([_, ukranian, _, tea, _], Street),

    %% The green house is immediately to the right of the ivory house.
    right_of([green, _, _, _, _], [ivory, _, _, _, _], Street),
    
    %% The Old Gold smoker owns snails.
    member([_, _, snails, _, old_gold], Street),
    
    %% Kools are smoked in the yellow house.
    member([yellow, _, _, _, kools], Street),
    
    %% Milk is drunk in the middle house.
    D3 = milk,

    %% The Norwegian lives in the first house.
    N1 = norwegian,
    
    %% The man who smokes Chesterfields lives in the house next to the man with the fox.
    next_to([_, _, _, _, chesterfields], [_, _, fox, _, _], Street),
    
    %% Kools are smoked in the house next to the house where the horse is kept.
    next_to([_, _, _, _, kools], [_, _, horse, _, _], Street),
    
    %% The Lucky Strike smoker drinks orange juice.
    member([_, _, _, orange_juice, lucky_strike], Street),
    
    %% The Japanese smokes Parliaments.
    member([_, japanese, _, _, parliaments], Street),

    %% The Norwegian lives next to the blue house.
    next_to([blue, _, _, _, _], [_, norwegian, _, _, _], Street),

    %% now, solutions:
    member([_, WaterDrinker, _, water, _], Street),
    member([_, ZebraOwner, zebra, _, _], Street).



right_of(E1, E2, [E2, E1 | _]).
right_of(E1, E2, [_|T]) :-
    right_of(E1, E2, T).

next_to(E1, E2, L) :-
    right_of(E1, E2, L);
    right_of(E2, E1, L).

```

```
?- solve(Water, Zebra).
Water = norwegian,
Zebra = japanese ;
false.

```

---

### Post by DreVanHenke on 2012-03-02
My 'brute force' solution in Python (my first programme in this language) with many if and loops. Poor performance but at least it produces the right answers.

Code in Python:
[PHP]
#!/usr/bin/python 
'''
        There are five houses.
        The Englishman lives in the red house.
        The Spaniard owns the dog.
        Coffee is drunk in the green house.
        The Ukrainian drinks tea.
        The green house is immediately to the right of the ivory house.
        The Old Gold smoker owns snails.
        Kools are smoked in the yellow house.
        Milk is drunk in the middle house.
        The Norwegian lives in the first house.
        The man who smokes Chesterfields lives in the house next to the man with the fox.
        Kools are smoked in the house next to the house where the horse is kept. [should be "... a house ...", see discussion below]
        The Lucky Strike smoker drinks orange juice.
        The Japanese smokes Parliaments.
        The Norwegian lives next to the blue house.
'''
numbers = [ "one", "two", "three", "four", "five"]
nationalities = [ "Englishman", "Spaniard", "Ukrainian", "Norwegian", "Japanese"]
colours = ["red", "green", "ivory", "yellow", "blue"]
drinks = ["coffee", "tea", "milk", "orange juice", "water"]
pets = ["dog", "snails", "fox", "horse", "zebra"]
smokes = ["Old Gold", "Kools", "Chesterfields", "Lucky Strike", "Parliaments"]

# breaking up the algorithm in two parts:
# - first part on row level
#   these constraints only apply to the fields in a particular house
class House:
    def __init__(self, number = None, nationality = None, colour = None, drink = None, pet = None, smoke = None):
        self.number = number
        self.nationality = nationality
        self.colour = colour
        self.drink = drink
        self.pet = pet
        self.smoke = smoke
        
    def check_constraints(self):
        # Englishman lives in red house
        if nationalities[0] == self.nationality:
            if colours[0] != self.colour:
                return False
        # red house is owned by Englishman
        if colours[0] == self.colour:
            if nationalities[0] != self.nationality:
                return False
            
        # Spaniard owns the dog
        if nationalities[1] == self.nationality:
            if pets[0] != self.pet:
                return False
        # dog is owned by Spaniard
        if pets[0] == self.pet:
            if nationalities[1] != self.nationality:
                return False
            
        # coffee is drunk in the green house
        if drinks[0] == self.drink:
            if colours[1] != self.colour:
                return False
        # in the green house the owner drinks coffee
        if colours[1] == self.colour:
            if drinks[0] != self.drink:
                return False
            
        # Ukrainian drinks tea
        if nationalities[2] == self.nationality:
            if drinks[1] != self.drink:
                return False
        # tea is drank by Ukrainian
        if drinks[1] == self.drink:
            if nationalities[2] != self.nationality:
                return False
            
        # Old Gold smoker owns a snail
        if smokes[0] == self.smoke:
            if pets[1] != self.pet:
                return False
        # snail owner smokes Old Gold
        if pets[1] == self.pet:
            if smokes[0] != self.smoke:
                return False
            
        # Kools are smoke in the yellow house
        if smokes[1] == self.smoke:
            if colours[3] != self.colour:
                return False
        # yellow house owner smokes Kools
        if colours[3] == self.colour:
            if smokes[1] != self.smoke:
                return False
            
        # milk is drunk in the middle house
        if drinks[2] == self.drink:
            if numbers[2] != self.number:
                return False
        # middle house owner drinks milk
        if numbers[2] == self.number:
            if drinks[2] != self.drink:
                return False
            
        # Norwegian lives in the first house
        if nationalities[3] == self.nationality:
            if numbers[0] != self.number:
                return False
        # first house in owned by Norwegian
        if numbers[0] == self.number:
            if nationalities[3] != self.nationality:
                return False
        
        # Lucky Strike smoker drinks orange juice
        if smokes[3] == self.smoke:
            if drinks[3] != self.drink:
                return False 
        # orange juice is drunk by Lucky Strike smoker
        if drinks[3] == self.drink:
            if smokes[3] != self.smoke:
                return False
            
        # Japanese smokes Parliaments
        if nationalities[4] == self.nationality:
            if smokes[4] != self.smoke:
                return False
        # Parliaments is smoked by Japanese
        if smokes[4] == self.smoke:
            if nationalities[4] != self.nationality:
                return False
            
        return True

#= second part on the sort order level
#  these constraints only apply to the sorting order of a list of houses numbered from 1 to 5
class HouseList:
    def __init__(self, houses):
        self.houses = []
        for house in houses:
            self.houses.append(house)
            
    def check_constraints(self):
        # there have to be 5 houses
        if len(self.houses) != 5:
            return False
        else:
            # no double values in the list of houses
            for i in range(len(self.houses)):
                for j in range(len(self.houses)):
                    if i != j:
                        if self.houses[i].colour == self.houses[j].colour:
                            return False
                        if self.houses[i].number == self.houses[j].number:
                            return False
                        if self.houses[i].nationality == self.houses[j].nationality:
                            return False
                        if self.houses[i].drink == self.houses[j].drink:
                            return False
                        if self.houses[i].pet == self.houses[j].pet:
                            return False
                        if self.houses[i].smoke == self.houses[j].smoke:
                            return False

                # The green house is immediately to the right of the ivory house.
                # checking iterator to prevent index out of range errors
                # colours = ["red", "green", "ivory", "yellow", "blue"]
                if i < 4:
                    if self.houses[i].colour == colours[2]:
                        if self.houses[i+1].colour != colours[1]:
                            return False
                if i == 4 and self.houses[i].colour == colours[2]:
                    return False
                if i == 0 and self.houses[i].colour == colours[1]:
                    return False
                
                # The man who smokes Chesterfields lives in the house next to the man with the fox.
                # checking iterator to prevent index out of range errors
                # pets = ["dog", "snails", "fox", "horse", "zebra"]
                # smokes = ["Old Gold", "Kools", "Chesterfields", "Lucky Strike", "Parliaments"]
                if i == 0:
                    if self.houses[i].smoke == smokes[2]:
                        if self.houses[i+1].pet != pets[2]:
                            return False
                    if self.houses[i].pet == pets[2]:
                        if self.houses[i+1].smoke != smokes[2]:
                            return False
                if i == 4:
                    if self.houses[i].smoke == smokes[2]:
                        if self.houses[i-1].pet != pets[2]:
                            return False
                    if self.houses[i].pet == pets[2]:
                        if self.houses[i-1].smoke != smokes[2]:
                            return False
                if 0 < i < 4:
                    if self.houses[i].smoke == smokes[2]:
                        if self.houses[i-1].pet != pets[2] and \
                           self.houses[i+1].pet != pets[2]:
                            return False
                    if self.houses[i].pet == pets[2]:
                        if self.houses[i-1].smoke != smokes[2] and \
                           self.houses[i+1].smoke != smokes[2]:
                            return False
                
                # Kools are smoked in the house next to the house where the horse is kept. 
                # checking iterator to prevent index out of range errors
                # pets = ["dog", "snails", "fox", "horse", "zebra"]
                # smokes = ["Old Gold", "Kools", "Chesterfields", "Lucky Strike", "Parliaments"]
                if i == 0:
                    if self.houses[i].smoke == smokes[1]:
                        if self.houses[i+1].pet != pets[3]:
                            return False
                    if self.houses[i].pet == pets[3]:
                        if self.houses[i+1].smoke != smokes[1]:
                            return False
                if i == 4:
                    if self.houses[i].smoke == smokes[1]:
                        if self.houses[i-1].pet != pets[3]:
                            return False
                    if self.houses[i].pet == pets[3]:
                        if self.houses[i-1].smoke != smokes[1]:
                            return False
                if 0 < i < 4:
                    if self.houses[i].smoke == smokes[1]:
                        if self.houses[i-1].pet != pets[3] and \
                           self.houses[i+1].pet != pets[3]:
                            return False
                    if self.houses[i].pet == pets[3]:
                        if self.houses[i-1].smoke != smokes[1] and \
                           self.houses[i+1].smoke != smokes[1]:
                            return False
                
                # The Norwegian lives next to the blue house.
                # checking iterator to prevent index out of range errors
                # nationalities = [ "Englishman", "Spaniard", "Ukrainian", "Norwegian", "Japanese"]
                # colours = ["red", "green", "ivory", "yellow", "blue"]
                # since the Norwegian can only live in the first house
                # the second house has to be blue
                # this constraint could be simply written as:
                # if i == 1:
                #     if self.houses[i].colour != colours[4]:
                #        return false
                # long method:
                if i == 0:
                    if self.houses[i].nationality == nationalities[3]:
                        if self.houses[i+1].colour != colours[4]:
                            return False
                    if self.houses[i].colour == colours[4]:
                        if self.houses[i+1].nationality != nationalities[3]:
                            return False
                if i == 4:
                    if self.houses[i].nationality == nationalities[3]:
                        if self.houses[i-1].colour != colours[4]:
                            return False
                    if self.houses[i].colour == colours[4]:
                        if self.houses[i-1].nationality != nationalities[3]:
                            return False
                if 0 < i < 4:
                    if self.houses[i].nationality == nationalities[3]:
                        if self.houses[i-1].colour != colours[4] and \
                           self.houses[i+1].colour != colours[4]:
                            return False
                    if self.houses[i].colour == colours[4]:
                        if self.houses[i-1].nationality != nationalities[3] and \
                           self.houses[i+1].nationality != nationalities[3]:
                            return False  
        return True
                        
if __name__ == '__main__':

    houses = []
    houseLists = []
    print('Generating a list of legal houses according to the constraints...')
    for number in numbers:
        for colour in colours:
            for nationality in nationalities:
                for pet in pets:
                    for drink in drinks:
                        for smoke in smokes:
                            house = House(number, nationality, colour, drink, pet, smoke)
                            if house.check_constraints():
                                houses.append(house)
    print(" - number of combinations: " + str(len(houses)))
    print("\nGenerating a list of all legal lists of sorted houses according to the contraints...")
    # Generate a list of sorted lists. Sorted on the only thing known: house number (1-5)
    # but only add it to the lists if it doesn't fail the constraints in the class HouseList
    for house0 in houses:
        if house0.number == numbers[0]:
            for house1 in houses:
                if house1.number == numbers[1]:
                    for house2 in houses:
                        if house2.number == numbers[2]:
                            for house3 in houses:
                                if house3.number == numbers[3]:
                                    for house4 in houses:
                                        if house4.number == numbers[4]:
                                            houseList = HouseList([house0, house1, house2, house3, house4])
                                            if houseList.check_constraints():
                                                print("\n - legal sorted list of houses:")
                                                for house in houseList.houses:
                                                    print('   - ' +house.number + ', ' + house.nationality + ', ' + house.colour + ', ' + house.drink + ', ' + house.pet + ', ' + house.smoke)
                                                houseLists.append(houseList)
                                                # We could break the for loops here, there is only one solution
    for houseList in houseLists:
        for house in houseList.houses:
            if house.drink == drinks[4]:
                print('\nWho drinks water?')
                print(' - The ' + house.nationality + ' drinks water')
            if house.pet == pets[4]:
                print('\nWho owns a zebra?')
                print(' - The ' + house.nationality + ' owns a zebra')
[/PHP]
Ouput:
```

Generating a list of legal houses according to the constraints...
 - number of combinations: 133

Generating a list of all legal lists of sorted houses according to the contraints...

 - legal sorted list of houses:
   - one, Norwegian, yellow, water, fox, Kools
   - two, Ukrainian, blue, tea, horse, Chesterfields
   - three, Englishman, red, milk, snails, Old Gold
   - four, Spaniard, ivory, orange juice, dog, Lucky Strike
   - five, Japanese, green, coffee, zebra, Parliaments

Who drinks water?
 - The Norwegian drinks water

Who owns a zebra?
 - The Japanese owns a zebra

```

---

### Post by Bodsda on 2012-03-03
Hi guys - sorry for the lack of input from me on this challenge, I've only just had the internet connected at my new place.

2 entries... maybe this challenge was a bit tricky, I will be judging the entries in the next few days.

Thanks,
Bodsda
Ubuntu Beginners Team

---

### Post by alexfish on 2012-03-03
> **Bodsda said:**
> Hi guys - sorry for the lack of input from me on this challenge, I've only just had the internet connected at my new place.

2 entries... maybe this challenge was a bit tricky, I will be judging the entries in the next few days.

Thanks,
Bodsda
Ubuntu Beginners Team

Just spotted this thread . so working on it

Any one else ?

---

### Post by alexfish on 2012-03-14
tclsh it prolog style

a bit tougher than prolog : needed to sort some of what prolog does
```
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"

 proc solver {} {
    # from the facts:
    set milk 3      ;#  Milk is drunk in the middle house
    set Norwegian 1 ;#  The Norwegian lives in the first house
    set blue 2      ;#  The Norwegian lives next to the blue house
    # test the statement line by line
    test {Englishman Spaniard Ukrainian Japanese} {2 3 4 5} {
        test {red ivory yellow green} {1 3 4 5} {
            if {$Englishman != $red}      continue        ;#  The Englishman lives in the red house
            test {dog snails fox horse Zebra} {1 2 3 4 5} {
                if {$Spaniard != $dog} continue        ;#  the Spaniard owns the dog
                test {tea Coffee orange_juice water} {1 2 4 5} {
                    if {$Ukrainian != $tea}     continue ;#  The Ukrainian drinks tea
                    if {$green != $Coffee} continue ;#  Coffee is drunk in the green house
                    test {Old_Gold Kools "Lucky_Strike" Parliaments Chesterfields} \
                        {1 2 3 4 5} {
                          # rest of statement == and next to
                          if {
                            [next $green $ivory] &&
                            $Old_Gold == $snails && 
                            $yellow == $Kools &&
                            [next $Chesterfields $fox] &&
                            [next $horse $Kools] &&
                            $Lucky_Strike == $orange_juice &&
                            $Japanese == $Parliaments
                          } solve_it
                    }
                }
            }
        }
    }
 }

# control structure

 proc test {atts values body} {
    foreach perm [permute $values] {
        uplevel 1 "assign {$atts} {$perm}; $body"
    }
 }

# set a 1; set b 2; set c 3 , and so on

 proc assign {atts values} {
    foreach att $atts value $values {uplevel 1 set $att $value}
 }

# Permutate as said just permutate

 proc permute {list {prefix ""}} {
    if {![llength $list]} {return 
[list $prefix]}
    set res 
[list]
    set n 0
    foreach e $list {
        eval 
[list lappend res]\
          [permute [lreplace $list $n $n] [linsert $prefix end $e]]
        incr n
    }
    return $res
 }

#########################
# sort next to

 proc next {x y} {expr {abs($x-$y)==1}}
########################################
# query the results here

 proc solve_it {} {
    set res {}
    foreach var [lsort [uplevel 1 info locals]] {
        set val [uplevel 1 set $var]
        if {[string is integer -strict $val]} {
            lappend res 
[list $var $val]
        }
    }

#################################################################################
# set query solve here : this challenge required "water" + "zebra" note the lower case

 set solve {water zebra}

#################################################################################
 set owns {english spaniard ukrainian norwegian japanese} ;# nationalities taken from statement note lower cases
 set groups {}
 set indexing {1 2 3 4 5}
 set a [lsort -index 1 $res]
 set all [string tolower $a]
## un hash next lin to see partly sorted list
# puts $all
 foreach index $indexing {
    set sort [lsearch -all -inline  $all *$index]
    foreach solves $solve {
        set get [string first $solves $sort]
        if {$get > -1} {
            foreach owner $owns {
                set ck [string first $owner $sort]
                if {$ck > -1} {puts "nationality of  $solves = $owner"}
            }
        }
    }
 }
exit
##### there could be more than one solution : try remove EXIT !!!!
 }
#################
# MAIN
#################
set t [solver]
```results:

nationality of  water = norwegian
nationality of  zebra = japanese

---

### Post by Bodsda on 2012-03-19
This was a tough one to judge. But my decision was swayed by the logical and concise code written by....


......
......
......

schauerlich

Congratulations. Your entry almost made me go and start learning prolog :)
We hope to see the next challenge from you soon!

Thanks everyone,
Bodsda,
Ubuntu Beginners Team

---

### Post by anewguy on 2012-03-19
I don't Zeeba except from comic pages......

Had Japaneese friends in L.A., but we didn't call them Japaneese - we just called them friends and people....

and.....

you can smoke corned beef
and you can smoke hash
but, you can't smoke corned beef hash!
(thanks Mad Magazine - early 1970's)

Actually, there have been a lot of these types of logic problems around for years.  They used to be standard measure in our computer courses back when I was in college (so you KNOW they've been around a LONG time! ;) ).  

Could I solve one now?  I don't think so.....too many years, too much "fun" have gone by.

---

### Post by schauerlich on 2012-03-19
> **Bodsda said:**
> This was a tough one to judge. But my decision was swayed by the logical and concise code written by....


......
......
......

schauerlich

Congratulations. Your entry almost made me go and start learning prolog :)
We hope to see the next challenge from you soon!

Thanks everyone,
Bodsda,
Ubuntu Beginners Team

Yay!

Good news and bad news. Good news, I have an idea for the next challenge. Bad news, it's finals week for me, so the new challenge will have to wait a few days. But I promise it's coming within a week - feel free to PM me to remind me!

---

### Post by fiatveritas on 2012-04-04
> **Bodsda said:**
> This was a tough one to judge. But my decision was swayed by the logical and concise code written by....


......
......
......

schauerlich

Congratulations. Your entry almost made me go and start learning prolog :)
We hope to see the next challenge from you soon!

Thanks everyone,
Bodsda,
Ubuntu Beginners Team
This is a cool forum! I remember doing this problem without a computer when I was in middle school (Though, I have some resentment that a computer can easily solve a problem like this.). It's clearly a linear system...

---

### Post by alexfish on 2012-04-04
> **fiatveritas said:**
> This is a cool forum! I remember doing this problem without a computer when I was in middle school (Though, I have some resentment that a computer can easily solve a problem like this.). It's clearly a linear system...

This one interested me for one reason:

> One other thing: in statement 6, right means your right.we have to decide if the first house is on the left or is it on the right

> The green house is immediately to the right of the ivory house.although the solve requested who drank water and who owned the zebra

from tcl script the solves are "if followed the comments remove # and exit"

> {kools 1} {norwegian 1} {fox 1} {water 1} {yellow 1}
 {chesterfields 2} {ukrainian 2} {blue 2} {horse 2} 
{tea 2} {englishman 3} {old_gold 3} {milk 3} {red 3} {snails 3} 
{lucky_strike 4} {spaniard 4} {dog 4} {ivory 4} {orange_juice 4} 
{coffee 5} {japanese 5} {parliaments 5} {zebra 5} {green 5}

nationality of  water = norwegian
nationality of  zebra = japanese> {kools 1} {norwegian 1} {fox 1} {water 1} {yellow 1}
 {chesterfields 2} {ukrainian 2} {blue 2} {horse 2} {tea 2} 
{englishman 3} {old_gold 3} {milk 3} {red 3} {snails 3} 
{coffee 4} {japanese 4} {parliaments 4} {zebra 4} {green 4} 
{lucky_strike 5} {spaniard 5} {dog 5} {ivory 5} {orange_juice 5}

nationality of  water = norwegian
nationality of  zebra = japanese
in rational logic if:

if first house is on the left then first statement is correct
if first house is on the right then second statement is correct

So is the first house on the left or is it on the right

Added:
have not seen the true Solution to the puzzle IE: where is the final bit which indicates or proves the first  or the second solution
for me this puzzle has yet to be solved , suppose I don't belong to the 2% club.. Info tells me as of yet, there are No Members ..any takers

---

### Post by alexfish on 2012-04-11
MM! no takers

Could it be solved using Algebra , think Einstein . what was he good at.

[http://www.mathsisfun.com/puzzles/algebra-puzzles-index.html](http://www.mathsisfun.com/puzzles/algebra-puzzles-index.html)

Have fun

alexfish

---

