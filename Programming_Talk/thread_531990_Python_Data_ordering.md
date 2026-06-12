---
title: "Python Data ordering"
date: 2007-08-22
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2007-08-22
Hi, i want to make a program in Python that will ask  the user for name and height until raw_input = /e, i know how to do it.
But the data, i need the data to be ordered in size, for example>
Been 187cm, Bob 156cm, etc.
What type i can use to store the data and order it, from highest to lowest?


Test run>
               What is your name?  Bob
               How tall are you? 251
               What is your name?  Been
               How tall are you? 124
               What is your name?  /e
               Program ends, do you wish to save the data in a file, y/n?

---

### Post by AZzKikR on 2007-08-22
> **DamjanDimitrioski said:**
> What type i can use to store the data and order it, from highest to lowest?

I'd use a list. Check the following example:
```
#import the regular expression module
import re

coll = ["200cm", "1450cm", "23cm", "101cm", "12cm"]
#  the actual result should be: 12, 23, 101, 200, 1450

def mysort(str1, str2):
    # this part gets every numer from the string in str1 and str2
    # using regular expressions. After that, it takes the first
    # found entry in the list(index 0), converts that to an integer.
    # Then, let the comparison begin.
    num1 = int(re.findall("[0-9]+", str1)[0])
    num2 = int(re.findall("[0-9]+", str2)[0])
    if num1 > num2:
        return 1
    elif num1 == num2:
        return 0
    else:
        return -1

# this is somewhat tricky. Had to look it up myself. You pass a reference
# to the sorting function, in this case 'mysort'. It takes exactly 2 arguments
# because if you add 'str3' to the 'def mysort()', the intepreter will 
# complain about having too many args.
coll.sort(cmp=mysort)

# print our collection, sorted.
print coll
```

---

### Post by DamjanDimitrioski on 2007-08-22
Thanks for the code, but i will try it later, at home, see ya!

---

### Post by cwaldbieser on 2007-08-22
> **DamjanDimitrioski said:**
> Hi, i want to make a program in Python that will ask  the user for name and height until raw_input = /e, i know how to do it.
But the data, i need the data to be ordered in size, for example>
Been 187cm, Bob 156cm, etc.
What type i can use to store the data and order it, from highest to lowest?


Test run>
               What is your name?  Bob
               How tall are you? 251
               What is your name?  Been
               How tall are you? 124
               What is your name?  /e
               Program ends, do you wish to save the data in a file, y/n?

Since you are gathering the user inputs discretely, why not just validate the numbers immediately and store your results in tuples that can be sorted naturally?
```

data = []
while True:
    print "What is your name?"
    name = raw_input()
    if name == "/e":
        break
    while True:
        print "How tall are you (cm)?"
        height = raw_input()
        try:
            height = float(height)
            break
        except:
            pass
    data.append((height, name))
data.sort()
for height, name in data:
    print "%s %fcm" % (name, height)

```

---

### Post by DamjanDimitrioski on 2007-08-22
Right, i was planning that, but I'm new to Python and i don't now the data types, and data arrays, that is my problem, and will use this algorithm>

program starts.
while not /e (with this i mean end :D )
get input name #Know how.
get input value #Know how.
store name,value #Don't know data types.
else
 data(name,value) - sort #Don't know data types
print 'the tallest is' and  the first value of data array.
print the smallest is , the last  of the array. 
ask for file saving #Know how.
program ends.

Like it, or not is mine.

---

### Post by slavik on 2007-08-22
perl is the closest to python language I know, idea should be similar

```

/usr/bin/perl

use strict; #force declaration of variables

my %data = ();
my $name;
my $height;
my $out;

print "What is your name? ";
$name = chomp <>;

while ($name ne "/e") {
  print "How tall are you? ";
  $height = chomp <>;

  $data{$name} = $height;

  print "What is your name? ";
  $name = chomp <>;
}

%data = sort { $data{$a} <=> $data{$b} } keys(%data);

open $out, "data" or die $!;
print $out "$_ - $data{$_}\n" foreach(keys %data);
close $out;
```

---

### Post by DamjanDimitrioski on 2007-08-23
#########################################################
#           Macedonian Source code                                                                       #
#########################################################
#import sys,os
#people = [ ]
#def do_k(x):
#    odi = x
#    while odi == True:
#            ime = raw_input('Vnesi ime: ')
#            #print odi #Debug check, for me.
#            if ime != '\k':
#                visina = float(raw_input('Vnesi visina: '))
#                print "Toj " +ime +'.\nSo visina: '+str(visina)+' cm.'
#                people.append((ime,visina))
#                pass
#            else:
#            #print odi #Debug check, for me.
#                odi = False#For any case.
#                poredi()
#                pechati()
#                break
#def poredi():
#    print 'Sortiram.'
#    people.sort()
#def kraj():
#    print "Blagodaram shto go koristevte mojot softver!"
#    sys.exit
#
#def snimi():
#    yes = True
#    sho = raw_input("Dali sakasj da ja snimish listata, d/n? - ")
#    while yes == True:
#        if sho == "d":
#            d = os.getenv('HOME')
#            fajl = raw_input("Vnesi ime na fajlot! -  ")
#            fl = open(d + '/Desktop/' + fajl,'w')
#            pass
#            fl.write('\n                            +----------------------------------------------------------------------+\n')
#            fl.write('\n                             !               Lista na iminja, od najvisok!                            !\n')
#            fl.write('\n                            +----------------------------------------------------------------------+\n')
#            fl.write('\n=-----------------------------------------------------------------------------------------------=\n')
#            for i,v in people:
#                fl.write("Ime: "+ i + ",so visina " + str(v)+'.\n')
#            fl.write('=-----------------------------------------------------------------------------------------------=\n')
#            fl.close
#            kraj()
#            break
#        else:
#            kraj() #wont exit
#    else:
#        snimi()
#def pechati():
#    people.sort()
#    print people
#    for i,v in people:
#        #print "%s %fcm% (i , v)"
#        print "Ime: "+ i + ",so visina " + str(v)
#do_k(True)
#if len(people)>0:
#    snimi()

#########################################################
#           English Source code                         #
#########################################################
import sys,os
people = [ ]
def do_it(x):
    go = x
    while go == True:
            name = raw_input('Enter name: ')
            #print odi #Debug check, for me.
            if name != '\e':
                height = float(raw_input('Enter height: '))
                print "That " +name +'.\nWith height: '+str(height)+' cm.'
                people.append((name,height))
                pass
            else:
            #print odi #Debug check, for me.
                go = False#For any case.
                sortthem()
                prints()
                break
def sortthem():
    print 'Sortiram.'
    people.sort()
def end():
    print "Thanks for using my software!"
    sys.exit

def save():
    yes = True
    what = raw_input("Do you want to save the list, y/n? - ")
    while yes == True:
        if what == "y":
            d = os.getenv('HOME') #Get the home path.
            file = raw_input("Vnesi ime na fajlot! -  ")#Name of the file.
            fl = open(d + '/Desktop/' + file,'w')# Finaly our full path.
            pass
#Write heading!
            fl.write('\n                            +----------------------------------------------------------------------+\n')
            fl.write('\n                             !               List of names, from the tallest!                      !\n')
            fl.write('\n                            +----------------------------------------------------------------------+\n')
            fl.write('\n=-----------------------------------------------------------------------------------------------=\n')
            for n,h in people:
                fl.write("Name: "+ n + ",with height " + str(h)+'.\n') #For each name, print name and age.
            fl.write('=-----------------------------------------------------------------------------------------------=\n')
            fl.close
            end()
            break
        else:
            end() #wont exit, it go's forever.
#    else:
 #       save()
def prints():
    people.sort()#I'm trying to use this again, but it is not sorting people[ ].
    print people
    for n,h in people:
        #print "%s %fcm% (n , h)" #I don't know what to do with this!
        print "Name: "+ n + ",with height " + str(h)
do_it(True)
if len(people)>0: #If the file is not empty, no need of this, but any way.
    save()

---

### Post by DamjanDimitrioski on 2007-08-23
Sorry, automaticly my text was formated to the begining of the line.:lolflag:

---

### Post by pmasiar on 2007-08-23
use code tags: [ code] .... program .... [/ code]

---

### Post by DamjanDimitrioski on 2007-08-23
pmasiar> what are code tag's?

---

### Post by pmasiar on 2007-08-23
vB code help (BTW linked in answer form, but because link  is not underlined, you need to find by mousing over it, right from text "Posting Rules: ": [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by DamjanDimitrioski on 2007-08-25
**[COLOR=Blue]Guy's, please look at [COLOR=Red]my code[/COLOR] and find the[COLOR=Red] error[/COLOR] why it don't [COLOR=Red]sort[/COLOR] the [COLOR=Red]data[/COLOR], please, i want to[COLOR=Red] learn[/COLOR] how to [COLOR=Red]manipulate[/COLOR] with [COLOR=Red]data types[/COLOR].[/COLOR]**
 :guitar:

---

### Post by cwaldbieser on 2007-08-25
> **DamjanDimitrioski said:**
> **[COLOR=Blue]Guy's, please look at [COLOR=Red]my code[/COLOR] and find the[COLOR=Red] error[/COLOR] why it don't [COLOR=Red]sort[/COLOR] the [COLOR=Red]data[/COLOR], please, i want to[COLOR=Red] learn[/COLOR] how to [COLOR=Red]manipulate[/COLOR] with [COLOR=Red]data types[/COLOR].[/COLOR]**
 :guitar:

Maybe if you could re-post your code formatted nicely in the CODE tags as pmasiar suggested, it would be easier for others to run and analyze your program.  Also, it might help if you gave examples of what is not working how you expect.

---

