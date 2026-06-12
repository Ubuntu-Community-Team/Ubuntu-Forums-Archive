---
title: "Beginner Programming Challenge #9"
date: 2010-02-15
forum: Programming Talk
---

### Post by Sinkingships7 on 2010-02-15
[SIZE="5"]**_Beginner Programming Challenge #9_**[/SIZE]

Welcome to the 9th programming challenge for beginners, sponsored by [The Ubuntu Beginners Team Development Focus Group]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development"). Let's dive right into things.

**_Task:_**

Your program should be able to open a text file and read its contents. The file will consist only of LOWERCASE letters and numbers 0-9. The file will be formatted such that there is only one alphanumeric character per line. Example file:
```

5
a
n
7
4
n
6
1
0
y
w
a

```
Your program must read each line and store the data in a data structure of your choice. Parse through your structure and print out the following information:

1. The sum of all the individual digits.
2. How many times each character appeared in the file.

Example output for the example above would be:
```

Sum = 23
a = 2
n = 2
w = 1
y = 1

```
The data file used for testing will be one of my own, so you don't know what's on it before I test. Conveniently, the way this program should be written makes that fact irrelevant. Your program should work with any size file. The one I use will be hundreds of lines long.

**_Bonus Points:_**

Code this in a programming language you've never used before!

**_Other Information:_**

Please read the bottom portion of Bodsda's post of BPC #8: [http://ubuntuforums.org/showthread.php?t=1386478](http://ubuntuforums.org/showthread.php?t=1386478)

All of those rules apply here as well. No obfuscated code. If you're a non-beginner, please wait until after the competition is judged to post your solution. We'd all love to learn something from the more advanced coders!

Go to this channel for help: irc.freenode.net #ubuntu-beginners-dev

[SIZE="4"]**[COLOR="Sienna"]EDIT:[/COLOR]**[/SIZE] Please provide instructions for how to run your program along with your submission. **[SIZE="4"]ANY LANGUAGE IS ALLOWED![/SIZE]**

---

### Post by JDShu on 2010-02-15
Just curious, what qualifies as a beginner? I have a minor in CS, learning basic concepts and I write games as a hobby. However, I only come to this part of the forum to ask questions, and this particular problem is not one that I could finish just like that (I consider myself a beginner at least).

---

### Post by Richard1979 on 2010-02-15
I'm learning C but am really at the beginner stage - I do know PHP well though.
Might have a go at this (if PHP is allowed).

---

### Post by Richard1979 on 2010-02-15
Was interested so I had a go anyway, I can't upload .php files so I'll paste the code here.

process.php
[PHP]<?php
// Read the file into a string then explode() this into an unformatted array
$data = file_get_contents('./data.txt');
$dataArray = explode(PHP_EOL, $data);

if (strlen($dataArray[(count($dataArray) - 1)]) == 0) {
    unset($dataArray[(count($dataArray) - 1)]); // Remove the last value if empty
}

// Let's make sure our data is formatted nicely
foreach ($dataArray as $key => $value) {
    $trimmedValue = strtolower(trim($value));
    $dataArray[$key] = $trimmedValue[0]; // We want only a single letter char
}

// Now we have a nice array ready for manipulation so lets continue!

// Lets grab all the numbers and sum them
$x = 0;
foreach ($dataArray as $key => $value) {
    if (is_numeric($value)) {
        $x += $value;
    }
}

echo 'Sum = ' . $x . "\n";

// Find out the count of unique values in our array
$uniqueChars = array_count_values($dataArray);

// Sort highest to lowest
arsort($uniqueChars);

foreach($uniqueChars as $key => $value ) {
    echo $key . ' = ' . $value . "\n";
}
[/PHP]My data file, data.txt
```
5
a
n
7
4
N
6
1
0
ye
w
a

```Run it as 
```
php process.php
```Expected output:
```
richard@lara:~/Programming/PHP/UbuntuComp$ php process.php 
Sum = 23
a = 2
n = 2
0 = 1
y = 1
w = 1
1 = 1
4 = 1
7 = 1
5 = 1
6 = 1

```Could probably nest a few functions there and tidy the code up a bit but it does the job.
If anyone else enters using a "proper" language etc then just take my entry as a non-entry, was just interested to try.

EDIT: I might have a go at this in C if I get time over the next couple of days. I would learn a lot from it I think.

---

### Post by lostinxlation on 2010-02-16
After reading #6 post, I thought I wouldn't quailfy. Deleted my code.

---

### Post by Sinkingships7 on 2010-02-16
> **JDShu said:**
> Just curious, what qualifies as a beginner? I have a minor in CS, learning basic concepts and I write games as a hobby. However, I only come to this part of the forum to ask questions, and this particular problem is not one that I could finish just like that (I consider myself a beginner at least).

If you can't immediately envision a solution to this problem, then I'd say you qualify as a beginner. Have at it! Since you're skeptical as to just how good you are, I encourage you to write this in a language you don't know to provide that extra challenge. :)

---

### Post by thedarklaith on 2010-02-16
what's the deadline?

---

### Post by s.fox on 2010-02-16
My attempt in PHP:

[PHP]
<?php
//Set Sum to 0
$sum = 0;
//Specify data file
$myFile = "data.txt";
$file_array = file($myFile);
//Read in the text file line by line
foreach ($file_array as $line){
    //Tidy up $line a bit because txt file
    $line = str_replace("\n", '', "$line");
    $line = str_replace("\r", '', "$line");
    //Sort out numbers and text
    if (is_numeric($line)) {
        //keep running total of numbers
        $sum = $sum + $line;
    }else{
        //Create seperate var containing only letters
        $data.= $line;
    }  
}  
if ($sum != 0){
    //Display running total if numbers present
    echo 'Sum = '.$sum."<br/>";
}
foreach (count_chars($data, 1) as $i => $val) {
    //Display count of each letter
    echo chr($i). ' = '.$val."<br/>";
} 
?>
[/PHP]

-Silver Fox

---

### Post by Marlonsm on 2010-02-16
I'll give it a try... although I still have no idea of how to do it.

---

### Post by sharpdust on 2010-02-16
Here it is in python:

```
#!/usr/bin/env python

def main():
    theFile = open("input_9.txt", "r")

    theSum = 0
    theCharDict = {}
    for theLine in theFile:
        theLine = theLine.strip()
        if theLine.isdigit():
          theSum = theSum + int(theLine)
        else:
          theCharDict[theLine] = theCharDict.get(theLine, 0) + 1

    print "Sum = " + str(theSum)
    for theKey, theValue in sorted(theCharDict.items()):
        print theKey + " = " + str(theValue)

if __name__ == "__main__":
    main()
```

---

### Post by Bodsda on 2010-02-16
Here is my python solution. It expects a file in the cwd called Challenge_9.txt

[php]
#! /usr/bin/env python 

file = "./Challenge9.txt"       # Define the name of the file
fileObj = open(file, "r")       # Open the file for reading
lines = fileObj.readlines()     # Read each line into a list
fileObj.close()                 # Close the file

ints = []                       # A list that will be used to hold the numbers
chars = []                      # A list that will be ised to hold the characters
word = ""                       # Will be used to concatenate our strings for counting

for i in lines:
    i = i.strip()               # Remove newline chars from the strings
    try:                      ###
        temp = int(i)           #   This block checks if the entry
    except ValueError:          #    is an int or a str
        temp = ""             ###

    if temp == "":            ###
        word += i               #    This block puts the value into the char list if its a str
        if i not in chars:      #     or into the ints list if it is an int
            chars.append(i)     #
                                #
    else:                       #
        ints.append(temp)     ###

sum = 0                         
for i in ints:                  # Add up the numbers and print
    sum += i

print "Sum =", sum

counter = -1                    # Counter for printing correct entry in list
for i in chars:
    counter += 1                # Increment counter to be at the beginning of the list (0)
    print "%s = %s" % (chars[counter],  word.count(chars[counter]))     # Refer to http://docs.python.org/library/stdtypes.html#string-methods
[/php]Bodsda

---

### Post by Bachstelze on 2010-02-16
Haskell. I broke it into three functions (plus main) to help readability:

[php]import Data.Char

digitsSum                   :: String -> Int
lettersCount                :: String -> [(Char, Int)]
printLettersCount           :: [(Char, Int)] -> IO ()


digitsSum s         = sum [digitToInt c | c <- s , isDigit c]

lettersCount []     = []
lettersCount (x:xs)
                    | isLower x     = (x, 1+length [c | c <- xs , c == x]):otherLettersCount
                    | otherwise     = otherLettersCount
                    where otherLettersCount = lettersCount [c | c <- xs , c /= x]

printLettersCount []      = putStr ""
printLettersCount (x:xs)  = do putStr [fst x]
                               putStr " = "
                               putStrLn (show (snd x))
                               printLettersCount xs

main = do
        -- Store the contents of the file as a string in the "file" variable.
        file <- readFile "bpc9.txt"

        -- Print the sum
        putStrLn ("Sum = " ++ show(digitsSum file))

        -- Print the letters counts
        printLettersCount (lettersCount file)

[/php]

It expects a file named "bpc9.txt" in the current working dir.

```
firas@iori ~ % cat bpc9.txt 
0                           
i                           
1                           
c                           
a                           
n                           
2                           
h                           
a                           
s                           
3                           
c                           
h                           
e                           
e                           
z                           
b                           
u                           
r                           
g                           
e                           
r                           
5                           
6                           
8                           
firas@iori ~ % ghc -o bpc9 bpc9.hs  
firas@iori ~ % ./bpc9             
Sum = 25                          
i = 1                             
c = 2                             
a = 2                             
n = 1                             
h = 2                             
s = 1                             
e = 3                             
z = 1                             
b = 1                             
u = 1
r = 2
g = 1
```

---

### Post by howlingmadhowie on 2010-02-16
here's a solution in scheme:
```

#! /usr/bin/guile -s
!#
(use-modules (ice-9 rdelim) (ice-9 format))

(define count-stuff
  (lambda (file)
    (let ((letters (cons '() '()) ))
      (define add-to-letters
        (lambda (input l)
          (cond ((null? (car l))
                 (set-car! letters (cons input 1)))
                ((equal? (caar l) input)
                 (set-cdr! (car l) (+ 1 (cdar l))))
                ((null? (cdr l))
                 (set-cdr! l (cons (cons input 1) '())))
                (else (add-to-letters input (cdr l))))))

      (define loop
        (lambda (file sum)
          (let ((input (read-line file)))
            (cond ((eof-object? input)
                   (list sum letters))
                  ((string->number input)
                   (loop file (+ sum (string->number input))))
                  (else
                   (add-to-letters input letters)
                   (loop file sum))))))
      (loop file 0))))

(define display-stuff
  (lambda (stuff)
    (define display-loop
      (lambda (letters)
        (if (not (null? letters))
            (begin
              (format #t "~a = ~d\n" (caar letters) (cdar letters))
              (display-loop (cdr letters))))))

    (format #t "Sum = ~d\n" (car stuff))
    (display-loop (cadr stuff))))

(define stuff (count-stuff (open-file (cadr (command-line)) "r")))
(display-stuff stuff)

```

it expects the name of the file as the second argument:
```

howie-laptop% ./pc09.scm test.data
Sum = 240
a = 4
c = 1
q = 1
d = 4
howie-laptop% 

```

I made it a lot more complicated than it needed to be because i created the dictionary implementation from scratch.

---

### Post by raydeen on 2010-02-16
Well, I'll post my sorry little excuse mainly for the entertainment of others. You all need a laugh sometimes :) 

It works but I couldn't quite get the second part perfect (it prints the letters in the array but does it in a loop and I couldn't figure out how to keep it from printing the valid letters multiple times) 

The text file:
```

5
g
f
6
h
j
n
5
f
2
d
7
8
k
6
h
1
f
3
s
5
v
v
b
d
5
n
9
k

```

The program:

[php]
# file was written in IDLE 3.1

f = open('test.txt', 'r')                   # Opens file for parsing

array = f.readlines()                       # Adds contents of file to a list

numcount = 0                                # Initializes variable to sum
                                            # the digits in the file
                                            
letters = 'abcdefghijklmnopqrstuvwxyz'      # Initializes variable to check for
                                            # letters in file

print ('\n\n')          



for x in range (len(array)):                # Strips out the newline characters
    array[x] = array[x].strip('\n')


for x in range (len(array)):                # Scans the length of the array
    
    if array[x] >= '0' and array[x] <= '9': # Tests if the element is a digit
        numcount = numcount + int(array[x]) # Adds the digit value to numcount

print ('Sum =', numcount)                   # Prints the sum

print ('\n\n')          

for y in range (len(letters)):              # Runs through the alphabet
                                            # checking to see if the current
                                            # letter is in the array

    lettercount = 0                         # Initializes the current letter
                                            # count to 0:
                                            
    for x in range (len(array)):            # Runs through the array to see
        if letters[y] == array[x]:          # if the letter exists in the array.
            
            lettercount = lettercount +1    # If it does, lettercount is
                                            # incremented by one.
                                            
            print (array[x], lettercount)   # Prinst the letter in the array with
                                            # how many times it occurs.

[/php]

And the output:

```

Sum = 62



b 1
d 1
d 2
f 1
f 2
f 3
g 1
h 1
h 2
j 1
k 1
k 2
n 1
n 2
s 1
v 1
v 2

```

I'm a Python newbie. Had to look up an example on the net for how to read a file in to the program. I figured I'd post it and then look at what the other fellows did in Python so's I could learn from my mistakes. :)

---

### Post by Bodsda on 2010-02-16
> **raydeen said:**
> Well, I'll post my sorry little excuse mainly for the entertainment of others. You all need a laugh sometimes :) 

It works but I couldn't quite get the second part perfect (it prints the letters in the array but does it in a loop and I couldn't figure out how to keep it from printing the valid letters multiple times) 

I'm a Python newbie. Had to look up an example on the net for how to read a file in to the program. I figured I'd post it and then look at what the other fellows did in Python so's I could learn from my mistakes. :)

Learning from others is a good move. I ran into the same problem, how do you stop it from printing each instance of the letter. My solution was to have a string containing all of the letters in order and a list of just one instance of the letters. You can use something like 

```

if letter in list:
    dont append to list
else:
    append to list

```

To get the one instance list. Then I used the string.count method on the string in a for loop of the list to get the counts of all the letters. Check my code a few posts before yours. It is heavily commented.

Hope it helps,
Bodsda

---

### Post by ssmithy on 2010-02-16
Here it is in C++ using vectors.  I'm pretty new to the language so feel free to tell me where I can improve the code. :D

```
#include <iostream>
#include <fstream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

void readFile(const string, vector<char>&);
void displaySum(vector<char>&);
void displayLetterCount(vector<char>&);

void readFile(const string filename, vector<char>& myVector)
{
	char ch;
	ifstream inFile(filename.c_str());
	if (!inFile)
	{
		cerr << "File could not be opened" << endl;
		exit(1);
	} // end if
	while(!inFile.eof())
	{
		inFile >> ch;
		myVector.push_back(ch);
	} // end while
	myVector.pop_back(); // while loop adds an extra character at the end
} // end readFile		// pop_back fixes this - there's probably a better way

void displaySum(vector<char>& myVector)
{
	int sum = 0;
	vector<char>::iterator myIterator;
	for (myIterator = myVector.begin(); myIterator != myVector.end(); myIterator++)
	{
		if (isdigit(*myIterator))
			sum += *myIterator - '0';	
	} // end for
	cout << "Sum is " << sum << endl;
} // end displaySum

void displayLetterCount(vector<char>& myVector)
{
	vector<char> usedList;
	vector<char>::iterator myIterator;
	for (myIterator = myVector.begin(); myIterator != myVector.end(); myIterator++)
	{
		if (!isdigit(*myIterator) && count(usedList.begin(), usedList.end(), *myIterator) == 0)
		{
			int letterCount = count(myVector.begin(), myVector.end(), *myIterator);
			cout << *myIterator << " = " << letterCount << endl;
			usedList.push_back(*myIterator);
		} // end if
	} // end for
} // end displayLetterCount

int main()
{
	vector<char> myVector;	
	readFile("test.txt", myVector);	
	displaySum(myVector);
	displayLetterCount(myVector);
	return 0;
} // end main

```

---

### Post by raydeen on 2010-02-16
> **Bodsda said:**
> Learning from others is a good move. I ran into the same problem, how do you stop it from printing each instance of the letter. My solution was to have a string containing all of the letters in order and a list of just one instance of the letters. You can use something like 

```

if letter in list:
    dont append to list
else:
    append to list

```

To get the one instance list. Then I used the string.count method on the string in a for loop of the list to get the counts of all the letters. Check my code a few posts before yours. It is heavily commented.

Hope it helps,
Bodsda

Thanks for the insight. I'm just starting to really tackle Python and I'm really enjoying it but unfortunately I still have some of the ol' BASIC in me (as my code no doubt shows). Any good examples are much appreciated.

Edit: It occurred to me last night I probably could have used a dictionary for the letters bit. Checked to see if the letter was in the dictionary and if not, add it as a key, then add a value of 1, or if it was in the dict, increase the value by 1. Ah well.

---

### Post by baddog144 on 2010-02-16
Here's my python solution:
```

#!/usr/bin/env python

file = open("text.txt", "r")
lines = file.readlines()
file.close()

sum = 0
uniquechars = {}

for line in lines:
    line = line.strip()
    if line.isdigit():
        sum += int(line)

    if uniquechars.get(line):
        uniquechars[line] += 1
    else:
        uniquechars[line] = 1

print sum

for char in uniquechars:
    print char, uniquechars[char]

```
I'm pretty happy with it :)

---

### Post by Marlonsm on 2010-02-16
Here is mine, in Python.
Very archaic, long and possibly slow, but it works!
```
file_data = open("input.txt", 'r')  #import file
number_count = 0        #declare the count for the numbers
a_count = 0             #declare the count for each letter
b_count = 0
c_count = 0
d_count = 0
e_count = 0
f_count = 0
g_count = 0
h_count = 0
i_count = 0
j_count = 0
k_count = 0
l_count = 0
m_count = 0
n_count = 0
o_count = 0
p_count = 0
q_count = 0
r_count = 0
s_count = 0
t_count = 0
u_count = 0
v_count = 0
w_count = 0
x_count = 0
y_count = 0
z_count = 0
for line in file_data:             #test each line individually
	if line.startswith('a'):   #test all possibilities for each line
		a_count += 1       #add one to the count every time a certain letter is found
	elif line.startswith('b'):
		b_count += 1
	elif line.startswith('c'):
		c_count += 1
	elif line.startswith('d'):
		d_count += 1
	elif line.startswith('e'):
		e_count += 1
	elif line.startswith('f'):
		f_count += 1
	elif line.startswith('g'):
		g_count += 1
	elif line.startswith('h'):
		h_count += 1
	elif line.startswith('i'):
		i_count += 1
	elif line.startswith('j'):
		j_count += 1
	elif line.startswith('k'):
		k_count += 1
	elif line.startswith('l'):
		l_count += 1
	elif line.startswith('m'):
		m_count += 1
	elif line.startswith('n'):
		n_count += 1
	elif line.startswith('o'):
		o_count += 1
	elif line.startswith('p'):
		p_count += 1
	elif line.startswith('q'):
		q_count += 1
	elif line.startswith('r'):
		r_count += 1
	elif line.startswith('s'):
		s_count += 1
	elif line.startswith('t'):
		t_count += 1
	elif line.startswith('u'):
		u_count += 1
	elif line.startswith('v'):
		v_count += 1
	elif line.startswith('w'):
		w_count += 1
	elif line.startswith('x'):
		x_count += 1
	elif line.startswith('y'):
		y_count += 1
	elif line.startswith('z'):
		z_count += 1
	elif line.startswith('1'):    #now for the numbers
		number_count += 1
	elif line.startswith('2'):
		number_count += 2
	elif line.startswith('3'):
		number_count += 3
	elif line.startswith('4'):
		number_count += 4
	elif line.startswith('5'):
		number_count += 5
	elif line.startswith('6'):
		number_count += 6
	elif line.startswith('7'):
		number_count += 7
	elif line.startswith('8'):
		number_count += 8
	elif line.startswith('9'):
		number_count += 9
print "Sum =", number_count  #print the sum
if a_count != 0:             #check if the file had this letter
	print "a =", a_count #print the letter and its count
if b_count != 0:
	print "b =", b_count
if c_count != 0:
	print "c =", c_count
if d_count != 0:
	print "d =", d_count
if e_count != 0:
	print "e =", e_count
if f_count != 0:
	print "f =", f_count
if g_count != 0:
	print "g =", g_count
if h_count != 0:
	print "h =", h_count
if i_count != 0:
	print "i =", i_count
if j_count != 0:
	print "j =", j_count
if k_count != 0:
	print "k =", k_count
if l_count != 0:
	print "l =", l_count
if m_count != 0:
	print "m =", m_count
if n_count != 0:
	print "n =", n_count
if o_count != 0:
	print "o =", o_count
if p_count != 0:
	print "p =", p_count
if q_count != 0:
	print "q =", q_count
if r_count != 0:
	print "r =", r_count
if s_count != 0:
	print "s =", s_count
if t_count != 0:
	print "t =", t_count
if u_count != 0:
	print "u =", u_count
if v_count != 0:
	print "v =", v_count
if w_count != 0:
	print "w =", w_count
if x_count != 0:
	print "x =", x_count
if y_count != 0:
	print "y =", y_count
if z_count != 0:
	print "z =", z_count
```

The input file should be in the same folder and be called input.txt .
EDIT: Rewritten mine, it's on post #33.

---

### Post by gtr32 on 2010-02-16
Don't include me in the challenge judging, I just wanted to give it a quick try. Does not include any kind of error handling or parameter checks!

[PHP]
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Text.RegularExpressions;

namespace CodingChallenge
{
    class Program
    {

        static void Main(string[] args)
        {
            // use dictionary to store character appearance counts
            Dictionary<string, int> dict = new Dictionary<string, int>();
            
            // regular expressions for the types in question
            Regex digit = new Regex("^[0-9]+", RegexOptions.Multiline);
            Regex character = new Regex("^[a-z]", RegexOptions.Multiline);

            // read file into buffer
            StreamReader reader = new StreamReader(args[0]);
            string data = reader.ReadToEnd();

            // get sum
            long sum = (from Match h in digit.Matches(data) select long.Parse(h.Value)).Sum();

            // get characters
            Match[] matches = (from Match h in character.Matches(data) select h).ToArray();
            foreach (Match match in matches)
            {
                if (dict.ContainsKey(match.Value) == false)
                {
                    // find character count
                    int count = matches.Count(a => a.Value == match.Value);
                    // add pairing to dictionary
                    dict.Add(match.Value, count);
                }
            }

            // write sum
            Console.WriteLine(string.Format("Sum is {0}", sum));

            // write character appearances
            foreach (KeyValuePair<string, int> pair in dict)
            {
                Console.WriteLine(string.Format("Character {0} count is {1}",
                    pair.Key, pair.Value));
            }
        }
    }
}

[/PHP]

---

### Post by GregBrannon on 2010-02-16
I'm impressed by those with the talent and the time to post submissions so quickly.  Please give those of us who are a little slower enough time to program an entry.  Say through the end of the weekend at least?

Thanks.

---

### Post by myrtle1908 on 2010-02-16
There is no Perl implementation thus far.  This made me sad.  Perl is good at this stuff.

```
use strict;
use warnings;

my @nums;
my %chars;

while(<DATA>) {
  chomp && /\d/ ? push(@nums, $_) : $chars{$_}++;
}
print "Sum = " . eval(join '+', @nums) . "\n"; # cheating here :)
for my $c (sort keys %chars) {
  print "$c = $chars{$c}\n";
}

__DATA__
5
a
n
7
4
n
6
1
0
y
w
a
```

```

Sum = 23
a = 2
n = 2
w = 1
y = 1
```

I was too lazy to read from a file.  Disqualify me.

---

### Post by sharpdust on 2010-02-16
> **Marlonsm said:**
> Here is mine, in Python.
Very archaic, long and possibly slow, but it works!
```
file_data = open("input.txt", 'r')  #import file
number_count = 0        #declare the count for the numbers
a_count = 0             #declare the count for each letter
b_count = 0
c_count = 0
d_count = 0
e_count = 0
f_count = 0
g_count = 0
h_count = 0
i_count = 0
j_count = 0
k_count = 0
l_count = 0
m_count = 0
n_count = 0
o_count = 0
p_count = 0
q_count = 0
r_count = 0
s_count = 0
t_count = 0
u_count = 0
v_count = 0
w_count = 0
x_count = 0
y_count = 0
z_count = 0
for line in file_data:             #test each line individually
	if line.startswith('a'):   #test all possibilities for each line
		a_count += 1       #add one to the count every time a certain letter is found
	elif line.startswith('b'):
		b_count += 1
	elif line.startswith('c'):
		c_count += 1
	elif line.startswith('d'):
		d_count += 1
	elif line.startswith('e'):
		e_count += 1
	elif line.startswith('f'):
		f_count += 1
	elif line.startswith('g'):
		g_count += 1
	elif line.startswith('h'):
		h_count += 1
	elif line.startswith('i'):
		i_count += 1
	elif line.startswith('j'):
		j_count += 1
	elif line.startswith('k'):
		k_count += 1
	elif line.startswith('l'):
		l_count += 1
	elif line.startswith('m'):
		m_count += 1
	elif line.startswith('n'):
		n_count += 1
	elif line.startswith('o'):
		o_count += 1
	elif line.startswith('p'):
		p_count += 1
	elif line.startswith('q'):
		q_count += 1
	elif line.startswith('r'):
		r_count += 1
	elif line.startswith('s'):
		s_count += 1
	elif line.startswith('t'):
		t_count += 1
	elif line.startswith('u'):
		u_count += 1
	elif line.startswith('v'):
		v_count += 1
	elif line.startswith('w'):
		w_count += 1
	elif line.startswith('x'):
		x_count += 1
	elif line.startswith('y'):
		y_count += 1
	elif line.startswith('z'):
		z_count += 1
	elif line.startswith('1'):    #now for the numbers
		number_count += 1
	elif line.startswith('2'):
		number_count += 2
	elif line.startswith('3'):
		number_count += 3
	elif line.startswith('4'):
		number_count += 4
	elif line.startswith('5'):
		number_count += 5
	elif line.startswith('6'):
		number_count += 6
	elif line.startswith('7'):
		number_count += 7
	elif line.startswith('8'):
		number_count += 8
	elif line.startswith('9'):
		number_count += 9
print "Sum =", number_count  #print the sum
if a_count != 0:             #check if the file had this letter
	print "a =", a_count #print the letter and its count
if b_count != 0:
	print "b =", b_count
if c_count != 0:
	print "c =", c_count
if d_count != 0:
	print "d =", d_count
if e_count != 0:
	print "e =", e_count
if f_count != 0:
	print "f =", f_count
if g_count != 0:
	print "g =", g_count
if h_count != 0:
	print "h =", h_count
if i_count != 0:
	print "i =", i_count
if j_count != 0:
	print "j =", j_count
if k_count != 0:
	print "k =", k_count
if l_count != 0:
	print "l =", l_count
if m_count != 0:
	print "m =", m_count
if n_count != 0:
	print "n =", n_count
if o_count != 0:
	print "o =", o_count
if p_count != 0:
	print "p =", p_count
if q_count != 0:
	print "q =", q_count
if r_count != 0:
	print "r =", r_count
if s_count != 0:
	print "s =", s_count
if t_count != 0:
	print "t =", t_count
if u_count != 0:
	print "u =", u_count
if v_count != 0:
	print "v =", v_count
if w_count != 0:
	print "w =", w_count
if x_count != 0:
	print "x =", x_count
if y_count != 0:
	print "y =", y_count
if z_count != 0:
	print "z =", z_count
```

The input file should be in the same folder and be called input.txt .


I'm glad to see another python solution, but oh my! What will happen if the input was changed to use uppercase letters as well? You may want to investigate python's other data structures out there to see if you can condense your solution.

---

### Post by Sinkingships7 on 2010-02-16
> **thedarklaith said:**
> what's the deadline?

[quote=GregBrannon]Please give those of us who are a little slower enough time to program an entry. Say through the end of the weekend at least?[/quote]

No worries. There's no real deadline for this challenge. In about a week I'll post a quick warning, and anyone who is still attempting the challenge can message me privately and the "deadline" will be extended.

---

### Post by Rocket2DMn on 2010-02-16
Well I ended up doing a bit more than I originally intended, so it's not nearly as short and straightforward as it could be. This validates inputs, checks for exceptions, and even has a reusable logger to go with it. To use, just feed it a filename or path to file as the first parameter. :popcorn: Enjoy:

```
java Challenge9 /path/to/input/file
```

Challenge9.java
```

/*
 * Available under Creative Commons - Attribution Non-Commercial Share Alike
 * http://creativecommons.org/about/licenses/
 * cc by-nc-sa
 */
import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

/**
 * Beginner Programming Challenge #9 -
 * http://ubuntuforums.org/showthread.php?t=1407897
 * 
 * @author Connor Imes
 */
public class Challenge9 {
  private static final SimpleLogger LOG = new SimpleLogger(Challenge9.class);
  private int sum = 0;
  private final Map<Character, Integer> existingLettersCount = new HashMap<Character, Integer>();

  /**
   * The first and only argument should be the path to the input file.
   * 
   * @param args
   */
  public static void main(String[] args) {
    if (args.length > 0) {
      try {
        new Challenge9().doWork(args[0]);
      } catch (IOException e) {
        LOG.error(e);
      }
    } else {
      LOG.error("No filename given.");
    }
  }

  private void doWork(String fileName) throws IOException {
    for (final String s : readFile(fileName)) {
      if (s.length() == 1) {
        final char ourChar = s.charAt(0);
        if (Character.isDigit(ourChar)) {
          sum += Integer.parseInt(String.valueOf(ourChar));
        } else if (Character.isLowerCase(ourChar)) {
          Integer curValue = existingLettersCount.get(ourChar);
          existingLettersCount.put(ourChar, curValue == null ? 1 : ++curValue);
        } else {
          LOG.error("Not a digit or lowercase alphabetic char: \"" + ourChar
              + "\"");
        }
      } else {
        LOG.error("Not a single character, ignoring line: \"" + s + "\"");
      }
    }
    LOG.info("Sum = " + sum);
    for (Character c : existingLettersCount.keySet()) {
      LOG.info(c + " = " + existingLettersCount.get(c));
    }
  }

  private static List<String> readFile(String fileName) throws IOException {
    final List<String> fileContents = new ArrayList<String>();
    if (new File(fileName).exists()) {
      final BufferedReader bReader = new BufferedReader(
          new FileReader(fileName));
      for (String line; (line = bReader.readLine()) != null;) {
        fileContents.add(line);
      }
    } else {
      throw new FileNotFoundException(fileName);
    }
    return fileContents;
  }
}

```

SimpleLogger.java
```

/*
 * Available under Creative Commons - Attribution Non-Commercial Share Alike
 * http://creativecommons.org/about/licenses/
 * cc by-nc-sa
 */

/**
 * A simple logger with no concept of logging levels or other configuration.
 * 
 * @author Connor Imes
 */
public class SimpleLogger {
  private Class<? extends Object> ownerClass;

  public SimpleLogger(Class<? extends Object> c) {
    ownerClass = c;
  }

  public void error(String s) {
    error(s, null);
  }

  public void error(Throwable t) {
    error(null, t);
  }

  public void error(String s, Throwable t) {
    printError(s, t);
  }

  public void info(String s) {
    print(s);
  }

  protected void printError(String s, Throwable t) {
    final String prefix = "ERROR: [" + ownerClass.getSimpleName() + "] ";
    if (s != null) {
      System.err.println(prefix + s);
    }
    if (t != null) {
      System.err.println(prefix + t.getClass().getSimpleName() + ": "
          + t.getMessage());
      boolean isFirst = true;
      for (StackTraceElement ste : t.getStackTrace()) {
        if (isFirst) {
          System.err.println(prefix + ste.toString());
          isFirst = false;
        } else {
          System.err.println(prefix + "\t" + ste.toString());
        }
      }
    }
  }

  protected void print(String s) {
    System.out.println("INFO : [" + ownerClass.getSimpleName() + "] " + s);
  }
}

```

---

### Post by Richard1979 on 2010-02-16
I had a go in C as well tonight but I'm such a novice I couldn't even figure out how to sum the numbers in my file.
Don't think I'll be attempting this one in C so will just leave my PHP one on page 1. :P

Interesting language though, it has to handle strings as arrays of chars and a char is really an int (ASCII).
Pointers are confusing me too but there's tons of tutorials out there and I love getting back to basics with computing. :)

---

### Post by BenAshton24 on 2010-02-17
<snip> sorry, i didn't read the rules, I'll post my code again once the competition is over :) </snip>

---

### Post by jasperyate on 2010-02-17
im trying to learn c but im at the very beginning so im tryin just to read code where i can so id love to see a solution of this in c if anyone has one, or if an admin can post one when the contest is over.

---

### Post by howlingmadhowie on 2010-02-17
Here's a solution in C. not very good, but it works (my C-foo is pretty weak atm).

```

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

typedef struct {
  char letter;
  int frequency;
  struct letterfreq *next;
} letterfreq;

letterfreq *list;

int freeall() {
  return 1;
}

int add_letter(char letter) {
  letterfreq *current, *new;

  if(list==NULL) {
    list=malloc(sizeof(letterfreq));
    list->letter=letter;
    list->frequency=1;
    list->next=NULL;
    return 1;
  }
  
  current=list;
  
  while(1) {
    if(current->letter==letter) {
      current->frequency++;
      return 1;
    }
    if (current->next != NULL)
      current=current->next;
    else
      break;
  }

  new=malloc(sizeof(letterfreq));
  new->letter=letter;
  new->frequency=1;
  new->next=NULL;
  current->next=new;
  return 1;
} 
void printall() {
  letterfreq *current;
  current=list;
  while(1) {
    printf("%c = %d\n", current->letter, current->frequency);
    if(current->next != NULL)
      current=current->next;
    else
      break;
  }
}

int is_numeric(char *str) {
  char c;
  if(str==NULL) return 0;
  if(!*str) return 0;
  while((c=str[0])) {
    if(!isdigit(c))
      return 0;
    str=&str[1];
  }
  return 1;
}

int main(int argc, char **argv) {
  FILE *fp;
  char line[20];
  int sum=0;
  
  if(argc!=2) return EXIT_FAILURE;
  
  fp=fopen(argv[1], "r");
  while(!feof(fp)) {
    fscanf(fp, "%s", line);
    if(is_numeric(line)) {
      sum+=atoi(line);
    } else {
      add_letter(line[0]);
    }
  }
  
  printf("Sum = %d\n", sum);
  printall();
  
  freeall();

  return EXIT_SUCCESS;
}

```

I didn't get around to writing the freeall function, but it would just mean running along the list freeing the individual members.

--edit--

i thought i'd add some words of explanation to it because it may not be clear what's going on.

much of the program is concerned with creating a data structure to store the letters and their frequency.  this is the letterfreq structure defined at the top of the code.  each instance of letterfreq contains the letter, the frequency and a pointer which may point to the next instance of letterfreq.  let's say you have parsed the following input:

```

a
c
b

```

then list would look like this:

```

---------     ---------     ---------
| a | 1 | --> | c | 1 | --> | b | 1 |
---------     ---------     ---------

```

let's say the next line contains the letter 'c'.  now the program will start checking each letterfreq in turn to see if the letter field contains a 'c'. in this case, it will check the first letterfreq and then, finding an 'a', move on to the second.  here it is successful and increments the value stored in the frequency field of the letterfreq and then returns.

let's say the next line contains the letter 'd'.  now the program will start checking each letterfreq in turn to see if the letter field contains a 'd'.  but it won't be successful. instead it will get to the last letterfreq in the chain (which it will recognise because the pointer of the last letterfreq isn't set) and then add a new letterfreq on to the end.

the one case not yet considered is how the whole thing starts off.  if the chain is empty, just create a new letterfreq with the value of the first letter and the frequency set to 1.

so just as in the scheme example i posted i've designed my own data structure to store the information needed. the problem with the data structure i've used is that it's slower for long lists than a standard implementation of a hashmap or a dictionary in php, python and the like. in general, the amount of time needed to perform an operation on the chain is proportional to the length of the chain.  with hashmaps or dictionaries this is not the case. 

an interesting programming challenge would be to implement hashmaps or dictionaries as [AVL trees]("http://en.wikipedia.org/wiki/AVL_tree") in a programming language of your choice :)

---

### Post by Marlonsm on 2010-02-17
> **sharpdust said:**
> I'm glad to see another python solution, but oh my! What will happen if the input was changed to use uppercase letters as well? You may want to investigate python's other data structures out there to see if you can condense your solution.
The idea itself is very simple, the problem is that the code has to be repeated lots of times.
I'll try to make it shorter, but first I'll read something about lists, I think it should help.

---

### Post by Phoenixie on 2010-02-17
My python solution:

[PHP]#!/usr/bin/env python

sum = 0
chars = {}

with open("data.txt", "r") as file:
    for line in file:
        line = line.strip()
        if line.isdigit():
            sum += int(line)
        else:
            if chars.get(line):
                chars[line] += 1
            else:
                chars[line] = 1

print 'Sum = {0}'.format(sum)
for key, val in chars.iteritems():
    print '{0} = {1}'.format(key, val)[/PHP]

Output:
```
Sum = 23
a = 2
y = 1
w = 1
n = 2

```

---

### Post by schauerlich on 2010-02-17
In C, expects one command line argument, the name of the data file.

```
 gcc -o countfreq.out countfreq.c && ./countfreq.out data.txt
```

[php]#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>


int main(int argc, char * argv[]) {
  FILE *inf;
  int counts[26]; // counts for each letter of the alphabet
  int sum = 0;
  char c;
  int i;
  
  if (argc == 2) { // if file specified
    inf = fopen(argv[1], "r"); // open file
  } 
  else { // else didn't use it right
    puts("usage: countfreq.out filename");
    exit(1);
  } 
  
  for (i = 0; i < 26; i++) { // initialize all of the counts to 0
    counts[i] = 0;
  } // for i
  
  while(fscanf(inf, "%c", &c)) { // read in one character
    if (isdigit(c)) {
      sum += atoi(&c); // we have to convert the character to an int before we add it to the sum
    }
    else if (isalpha(c)) {
      counts[c - 'a'] += 1; // increment the correct count; beginners, see footnote below
    }
    else { // else non-alphanumeric
      break;
    } 
    
    fscanf(inf, "%c", &c); // eat newline
  } // while there's something to be read
  
  printf("Sum = %d\n", sum);
  
  for (i = 0; i < 26; i++) {
    if (counts[i]) { // if the count for that letter does NOT equal zero
      printf("%c = %d\n", i + 'a', counts[i]); // print it; see second footnote
    }
  } // for i
  

  return 0;
} // main()[/php]

Footnote 1:
This line 'cheats' by using ASCII arithmetic. ASCII represents each character as it would any other number. In this case, a = 97, b = 98, c = 99, ... z = 122 (see [here](http://www.asciitable.com/asciifull.gif) for a full list). I'm converting a letter, c, into some index value for the counts array by subtracting the value of 'a' from it. For instance, if the character I have is 'g' (which is 103) and I subtract 'a' (which is 97), I get 6. counts[6] is the 7th element in the counts array, which corresponds to how many of the 7th letter, 'g', there are.

Footnote 2:
I'm doing something similar to footnote 1, but in reverse. In this case, i is some index in the counts array. I add the value 'a' = 97 to this index, which gives me some number. I then print out that number as if it were an ASCII value. For instance, if i == 6, then by adding 'a' = 97 to it, I get 103. If you interpret 103 as an ASCII value, you get 'g', which is the letter I wanted to print out.

---

### Post by Marlonsm on 2010-02-17
I have another one, also in Python, now using lists:
[php]file_data = open("input.txt", 'r')  #import file
number_count = 0 #declare the sum
letters = ["a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"] #make a list with all letters
count = [] #prepare the list to get the count for each letter
for item in letters:
	count.append(0) #add one item for each letter
letter = 0 #declare the variable that will tell Python which letter in the alphabet it is working with
chars = []
for line in file_data: #create a list with the contents from the imported file
	char = line.strip()
	chars.append(char)
for item in chars: #test each imported item
	test_item = item
	if test_item.isdigit():       #if it's a number, add to the sum
		number_count += int(item)
	else:                         #if it's a letter:
		for item in letters:            #compare imported items to alphabet
			if item == test_item:           #if a letter is found:
				count[letter] += 1          #add it to the count
				letter = 0                  #set the letter back to "a"
				break                       #go to next item
			elif letter + 1 < len(letters): #if a letter is not found, but it has not reached "z" yet,
				letter += 1                 #go to the next letter
			else:                           #if it has already reached "z"
				letter = 0                  #go back to "a"
				break
print "Sum =", number_count
for item in count:
	if item != 0:     #if the was any of the letter in the list, print it and the amount
		print letters[letter],"=", item
	letter += 1       #go to the next letter[/php]
Again, the input should be in the same folder and be called input.txt .

---

### Post by gtr32 on 2010-02-17
> **Marlonsm said:**
> I have another one, also in Python, now using lists:

You might find this useful:

[http://docs.python.org/tutorial/datastructures.html#dictionaries](http://docs.python.org/tutorial/datastructures.html#dictionaries)

---

### Post by Marlonsm on 2010-02-17
> **gtr32 said:**
> You might find this useful:

[http://docs.python.org/tutorial/datastructures.html#dictionaries](http://docs.python.org/tutorial/datastructures.html#dictionaries)

Thanks, it's certainly another way to do it. I might try to add it to mine later...

---

### Post by sharpdust on 2010-02-17
> **Marlonsm said:**
> I have another one, also in Python, now using lists:
[php]file_data = open("input.txt", 'r')  #import file
number_count = 0 #declare the sum
letters = ["a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x",&quot;y","z"] #make a list with all letters
count = [] #prepare the list to get the count for each letter
for item in letters:
	count.append(0) #add one item for each letter
letter = 0 #declare the variable that will tell Python which letter in the alphabet it is working with
chars = []
for line in file_data: #create a list with the contents from the imported file
	char = line.strip()
	chars.append(char)
for item in chars: #test each imported item
	test_item = item
	if test_item.isdigit():       #if it's a number, add to the sum
		number_count += int(item)
	else:                         #if it's a letter:
		for item in letters:            #compare imported items to alphabet
			if item == test_item:           #if a letter is found:
				count[letter] += 1          #add it to the count
				letter = 0                  #set the letter back to "a"
				break                       #go to next item
			elif letter + 1 < len(letters): #if a letter is not found, but it has not reached "z" yet,
				letter += 1                 #go to the next letter
			else:                           #if it has already reached "z"
				letter = 0                  #go back to "a"
				break
print number_count
for item in count:
	if item != 0:     #if the was any of the letter in the list, print it and the amount
		print letters[letter],"=", item
	letter += 1       #go to the next letter[/php]
Again, the input should be in the same folder and be called input.txt .

Good job, you are getting the idea, but you should never have to have a list with the entire alphabet in it.

Try this:

```

if theChar in string.ascii_lowercase:

```

---

### Post by munky99999 on 2010-02-17
**Bash Script:**
```

#!/bin/bash
clear
arrayletter=(a b c d e f g h i j k l m n o p q r s t u v w x y z)
#first thing to do is setup an array for the letters to allow easy incrementation.
array=(`cat $HOME/text.file`)
#This will filter all the text.file into an array to mess with.
len=${#array[*]}
#len here just tells you how many are in the array giving the limit to the loop.
i=0
addnumb=0
for (( k = 0 ; k < 26 ; k++ ))
do
let "op$k"=0
done
#this initializes the op$k variables that I use below.
while [ $i -lt $len ]; do
case ${array[$i]} in
1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 ) addnumb=${array[$i]}+$addnumb
;;
a ) let op0++ ;;
b ) let op1++ ;;
c ) let op2++ ;;
d ) let op3++ ;;
e ) let op4++ ;;
f ) let op5++ ;;
g ) let op6++ ;;
h ) let op7++ ;;
i ) let op8++ ;;
j ) let op9++ ;;
k ) let op10++ ;;
l ) let op11++ ;;
m ) let op12++ ;;
n ) let op13++ ;;
o ) let op14++ ;;
p ) let op15++ ;;
q ) let op16++ ;;
r ) let op17++ ;;
s ) let op18++ ;;
t ) let op19++ ;;
u ) let op20++ ;;
v ) let op21++ ;;
w ) let op22++ ;;
x ) let op23++ ;;
y ) let op24++ ;;
z ) let op25++ ;;
esac
let i++
done
echo "Sum = $(($addnumb))"
num=0
while [ $num -lt 26 ]; do
eval hello=\$op$num
#I use eval here so I can make the nested variable work.
if [ $hello != 0 ]; then
eval echo "${arrayletter[$num]} \$op$num"
fi
let num++
done

```

The applicable file with alphanumeric contents should be in $HOME/text.file

Then run the script with "bash script"

Any comments? Please be as destructive as possible.


Side note: It'd be very interesting to see each one get benchmarked against a large list.

---

### Post by Richard1979 on 2010-02-17
> **munky99999 said:**
> 
Side note: It'd be very interesting to see each one get benchmarked against a large list.

I agree, that would be very neat.

---

### Post by schauerlich on 2010-02-17
> **munky99999 said:**
> Any comments? Please be as destructive as possible.

I think any approach that requires manually specifying the entire alphabet into an array and a 27 case switch statement is probably the wrong one.

---

### Post by falconindy on 2010-02-17
I've been on a C kick since my C++ class has been booooooring.

```
#include <stdio.h>

void main() {
    int freq[26] = {0};
    int sum = 0;

    char c;
    FILE* input = fopen("input.txt", "r");
    while (! feof(input)) {
        c = fgetc(input);
        if (c < 97)
            sum += (c - 48);
        else
            freq[c - 97]++;
        fgetc(input);
    }

    printf("Sum = %d\n", sum);
    for (int i = 0; i < 26; i++)
        if (freq[i] > 0)
            printf("%c = %d\n", i + 97, freq[i]);
}
```

---

### Post by falconindy on 2010-02-17
Bash entry!
```
#!/bin/bash

sum=0
freq=()

freqadd() {
    freq=(${freq[@]} $1)
}

for line in $(cat input.txt); do
    [[ $line == [[:digit:]] ]] && sum=$(( $sum + $line )) || freqadd $line
done

echo sum = $sum
IFS=$'\n'
echo "${freq[*]}" | sort | uniq -c
```

---

### Post by howlingmadhowie on 2010-02-18
> **munky99999 said:**
> 
Side note: It'd be very interesting to see each one get benchmarked against a large list.

i imagine the C methods with the 26 * sizeof(int) large array for storing the results will be comfortably faster than any other methods. they have the obvious advantage that the time to increment an existing letter-value is very small, probably just a handful of ticks.

btw, you could probably make these array-based C methods even faster on intel architecture by changing the array from 26 elements to 32 elements in length and ANDing the character read with 0x3F (which is probably faster than subtraction on intel architecture, if not on a risc machine), or even better, just making the array 128 elements long.  calling atoi is also a big performance hit and should be avoided for the fastest possible solution. 

the hashmap or dictionary methods are going to be a lot slower. finding an element in a hashmap is proportional to the logarithm of the number of elements already there (which doesn't really concern us, because we have an upper bound for the number of elements), but it also contains a lot of calculating and looking up each time (unless the virtual machine is bombastically clever).  also, they've only been submitted in interpreted languages, which means that they're probably going to be a factor of 10 slower than C anyway. 

i imagine my C method (using a linked list to store the values found) will be somewhere between the two. the same method in scheme will be a fair bit slower than the hashmap methods.

---

### Post by s.fox on 2010-02-18
> **munky99999 said:**
> 
Side note: It'd be very interesting to see each one get benchmarked against a large list.

I too am looking forward to having the scripts compared against one another :D  I wonder exactly how they will be compared.

> **howlingmadhowie said:**
> i imagine the C methods with the 26 * sizeof(int) large array for storing the results will be comfortably faster than any other methods. they have the obvious advantage that the time to increment an existing letter-value is very small, probably just a handful of ticks.

Maybe it will be faster but I do not think we were trying to be quick in execution,  nothing in [post#1]("http://ubuntuforums.org/showpost.php?p=8832406&postcount=1") about being quick at any rate.   :D

-Silver Fox

---

### Post by howlingmadhowie on 2010-02-18
here are some benchmarks for an input file of one million letters or numbers:

```

name;data length;results;notes
baddog144.py;1000000;2,35s user 0,25s system 100% cpu 2,599 total;
Bodsda.py;1000000;6,05s user 0,35s system 98% cpu 6,507 total;
falconindy;1000000;0,10s user 0,01s system 87% cpu 0,125 total;WRONG ANSWER!
falconindy.sh;1000000;more than 5 minutes;
howlingmadhowie;1000000;0,27s user 0,00s system 97% cpu 0,277 total;
howlingmadhowie.scm;1000000;15,52s user 0,03s system 99% cpu 15,593 total;
Marlonsm\(1\).py;1000000;9,76s user 0,31s system 99% cpu 10,119 total;
Marlonsm\(2\).py;1000000;9,21s user 0,35s system 99% cpu 9,593 total
munky99999.sh;1000000;more than 5 minutes;
Phoenixie.py;1000000;1,83s user 0,13s system 98% cpu 1,988 total;
raydeen.py;1000000;17,82s user 2,19s system 92% cpu 21,680 total;too much output!
Richard1979.php;1000000;failed;memory error
Richard1979.php;1000000;4,46s user 0,85s system 99% cpu 5,346 total;ini_set('memory_limit', '512M') added
schauerlich;1000000;0,29s user 0,02s system 92% cpu 0,335 total;
sharpdust.py;1000000;1,45s user 0,07s system 98% cpu 1,544 total;
Silver_fox_.php;1000000;failed;memory error
Silver_fox_.php;1000000;4,14s user 0,56s system 99% cpu 4,722 total;ini_set('memory_limit', '512M') added
ssmithy;1000000;0,23s user 0,01s system 84% cpu 0,285 total;
Rocket2DMn;1000000;1,57s user 0,21s system 90% cpu 1,959 total;
Bachstelze;1000000;5,08s user 0,35s system 99% cpu 5,460 total;memory error, had to increase stack size

```

Computer is an athlon64X2 dual core. all C and C++ programs compiled with -O2. gcc version 4.4.1. 64bit operating system. python version 2.6.4. php version 5.2.10-2ubuntu6.4. ghc version 6.10.4.

Here's the code used to generate the list used:
```

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

int main(int argc, char **argv) {
  int num, i, tofind;

  if(argc!=2) return EXIT_FAILURE;
  tofind=atoi(argv[1]);
  srand( ((unsigned int)time(NULL))/2);

  for(i=0; i<tofind; i++) {
    num=rand() & 0x7F;
    if(num<0x30) {
      i--;
      continue;
    }
    if(num<0x3a) {
      printf("%d\n", (num-0x30));
      continue;
    }
    if(num<0x61) {
      i--;
      continue;
    }
    if(num<0x7b) {
      printf("%c\n", num);
    }
    else {
      i--;
      continue;
    }
  }

  return EXIT_SUCCESS;
}

```

---

### Post by s.fox on 2010-02-18
Hello,

Slightly confused by some of the output.  Can you break down what the different columns are.

```
baddog144.py;1000000;2,35s user 0,25s system 100% cpu 2,599 total;
```

Thank you very much,

-Silver Fox

---

### Post by howlingmadhowie on 2010-02-18
you can save the file as filename.csv and open in a spreadsheet program, if you want.

each line is made of 4 fields separated by semicolons. they are:
1/ name of the file
2/ length of the input (always one million, so slightly redundant)
3/ result of running 'time ./$filename $args'
4/ anything else of relevance

---

### Post by lisati on 2010-02-18
> **falconindy said:**
> I've been on a C kick since my C++ class has been booooooring.

```
#include <stdio.h>

void main() {
    int freq[26] = {0};
    int sum = 0;

    char c;
    FILE* input = fopen("input.txt", "r");
    while (! feof(input)) {
        c = fgetc(input);
        if (c < 97)
            sum += (c - 48);
        else
            freq[c - 97]++;
        fgetc(input);
    }

    printf("Sum = %d\n", sum);
    for (int i = 0; i < 26; i++)
        if (freq[i] > 0)
            printf("%c = %d\n", i + 97, freq[i]);
}
```

Nice, but what if some rascal tampers with your data file and puts in a character that isn't 0-9 or a-z?

---

### Post by s.fox on 2010-02-18
Ah I see,

Thank you. :D

-Silver Fox

---

### Post by howlingmadhowie on 2010-02-18
Okay. here's an openoffice spreadsheet file with some more exhaustive results.

i can't work out how to add titles and stuff to the diagram, so i'll just explain that the x-axis is the input length and the y-axis is the logarithm of the time taken.

---

### Post by Rocket2DMn on 2010-02-18
I definitely wasn't shooting for speed by writing a non-minimal java program.  Maybe I'll try something in C (it's been years since I've used it).  Thanks for the benchmarks though.

---

### Post by s.fox on 2010-02-18
Speed was not my goal.  If it is now seen as important I'll see how much time I can shave off my original scripts time.   I will not however jump ship from PHP to C,   should be interesting to see what I can do for the time.:D

---

### Post by howlingmadhowie on 2010-02-18
this is a pretty fast single-threaded C program:

```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv) {
  FILE *fp;
  int sum=0, i=0;
  char ch;
  int values[128];

  if(argc!=2) return EXIT_FAILURE;
  fp=fopen(argv[1], "r");

  for(i=0; i<128; i++) {
    values[i]=0;
  }

  while(!feof(fp)) {
    ch=fgetc(fp);
    if(ch>0x2f && ch<0x3a) {
      sum+=(ch-0x30);
    } else {
      values[ch]++;
    }
    fgetc(fp);
  }

  printf("sum = %d\n", sum);
  
  for(i=0x61; i<0x7b; i++) {
    printf("%c = %d\n", i, values[i]);
  }
  
  return EXIT_SUCCESS;
}

```

It assumes a lot about the input, but is rather fast:

```

datalength  100 1000 10000 100000 1000000 10000000
time         0s   0s    0s  0.01s   0.10s    0.51s

```

---

### Post by howlingmadhowie on 2010-02-18
> **Silver_fox_ said:**
> Speed was not my goal.  If it is now seen as important I'll see how much time I can shave off my original scripts time.   I will not however jump ship from PHP to C,   should be interesting to see what I can do for the time.:D

one thing you could try to do is keep memory size down. 512MB weren't enough to run the php programs for 10 million lines of input, while other approaches didn't exceed a couple of hundred kB for the same task.

---

### Post by s.fox on 2010-02-18
> **howlingmadhowie said:**
> one thing you could try to do is keep memory size down. 512MB weren't enough to run the php programs for 10 million lines of input, while other approaches didn't exceed a couple of hundred kB for the same task.

Yes,  I noticed that.  A little embarrassing,  though this is an extreme test in my opinion ;)

I have one or two ideas that should help get it down.   Should also improve speed too.  Double win :)

-Silver Fox

---

### Post by Marlonsm on 2010-02-18
> **howlingmadhowie said:**
> Okay. here's an openoffice spreadsheet file with some more exhaustive results.

i can't work out how to add titles and stuff to the diagram, so i'll just explain that the x-axis is the input length and the y-axis is the logarithm of the time taken.

Thanks for the results.
I was not aiming for speed in mine, I just wanted it to work. Also interesting to see that both my programs, despite the big difference in size, take about the same time to run.

---

### Post by falconindy on 2010-02-18
> **lisati said:**
> Nice, but what if some rascal tampers with your data file and puts in a character that isn't 0-9 or a-z?
Yeah, it's a little lean (probably too lean) but I was only going by the preconditions given in the initial challenge. I assume I had the 'wrong' answer because of a stray newline character that wasn't consumed correctly. Rearranging the comparison block fixes this (slightly).

```
#include <stdio.h>

void main() {
    int freq[26] = {0};
    int sum = 0;

    char c; FILE* input = fopen("input.txt", "r");
    while (! feof(input)) {
        c = fgetc(input);
        if (c > 96)
            freq[c - 97]++;
        else if (c > 47)
            sum += (c - 48);
    }

    printf("Sum = %d\n", sum);
    for (int i = 0; i < 26; i++)
        if (freq[i]) printf("%c = %d\n", i + 97, freq[i]);
}
```

---

### Post by howlingmadhowie on 2010-02-18
okay, just to really put the cat among the pidgeons, here's a multithreaded method which on a 4-core phenom can complete the task for 10 million values in 0.08 seconds.

```

#include <stdlib.h>

#define NUM_THREADS  12
#define NUM_LETTERS 128

int filelength;
char *data;
int sums[NUM_THREADS];
int letterss[NUM_THREADS][NUM_LETTERS];


void* printHello(void *threadid) {
  long place=0;
  long tid;
  char c;
  tid=(long)threadid;
  place=tid;
  while(place<filelength) {
    c=data[place];
    if(c&0x80) {
      place+=NUM_THREADS;
      continue;
    }
    if(c&0x30 && c<0x3a) {
      sums[tid]+=c-0x30;
    } else {
      letterss[tid][c]++;
    }
    place+=NUM_THREADS;
  }
  pthread_exit(NULL);
}

int main(int argc, char *argv[]) {
  pthread_t threads[NUM_THREADS];
  FILE *file;
  int rc, i, j, sum;
  int letters[NUM_LETTERS];
  long t;
  void *status;

  if(argc!=2) return EXIT_FAILURE;

  sum=0;
  for(i=0; i < NUM_THREADS; i++) {
    sums[i]=0;
  }
  for(j=0; j< NUM_LETTERS; j++) {
    for(i=0; i< NUM_THREADS; i++) {
      letterss[i][j]=0;
    }
    letters[j]=0;
  }

  file=fopen(argv[1], "r");
  fseek(file, 0, SEEK_END);
  filelength=ftell(file);
  fseek(file, 0, SEEK_SET);
  data=malloc(filelength+1);
  fread(data, sizeof(char), filelength, file);

  for(t=0; t<NUM_THREADS; t++) {
    rc = pthread_create(&threads[t], NULL, printHello, (void *)t);
    if (rc) {
      printf("ERROR: return code from pthread_create is %d\n", rc);
      return EXIT_FAILURE;
    }
  }

  for(i=0; i<NUM_THREADS; i++) {
    rc = pthread_join(threads[i], &status);
    if (rc) {
      printf("ERROR: return code from pthread_join() is %d\n", rc);
      return EXIT_FAILURE;
    }
    sum+=sums[i];
    for(j=0; j<NUM_LETTERS; j++) {
      letters[j]+=letterss[i][j];
    }
  }
  printf("sum = %d\n", sum);
  for(j=0x61; j<0x7b; j++) {
    printf("%c = %d\n", j, letters[j]);
  }

  pthread_exit(NULL);
}

```

strangely i've just found that it's faster if i turn the number of threads down to 1! i presume this is because of cache misses when the threads get out of sync.  the performance gain must therefore come from reading the entire file into memory first, rather than checking for feof and asking the operating system for a new batch of letters every now and then.

---

### Post by s.fox on 2010-02-18
Hello,

Don't think either of these will see much (if any) improvement in speed but yes... I have been having a little play.

Version 2 difference is getting rid of the two string replaces and using a single rtrim.  Might help a little,  though not positive.

[PHP]<?php
//Set Sum to 0
$sum = 0;
//Specify data file
$myFile = "data.txt";
$file_array = file($myFile);
//Read in the text file line by line
foreach ($file_array as $line){
    //A little house keeping
    $line = rtrim($line, "\r\n");
    //Sort out numbers and text
    if (is_numeric($line)) {
        //keep running total of numbers
        $sum = $sum + $line;
    }else{
        //Create seperate var containing only letters
        $data.= $line;
    }  
}  
if ($sum != 0){
    //Display running total if numbers present
    echo 'Sum = '.$sum."<br/>";
}
foreach (count_chars($data, 1) as $i => $val) {
    //Display count of each letter
    echo chr($i). ' = '.$val."<br/>";
} 
?> [/PHP]Version 3 uses a different method to read in the file.  Again I am not sure if will see improved speed.

[PHP]<?php 
//Set Sum to 0
$sum = 0;
//Specify data file
$myFile = "data.txt";

//Trying a new method of reading in the file
if($fh = fopen("$myFile","r")){
    while (!feof($fh)){
        //A little house keeping
        $line = rtrim(fgets($fh,9999), "\r\n");
        //Sort out numbers and text
        if (is_numeric($line)) {
            //keep running total of numbers
            $sum = $sum + $line;
        }else{
            //Create seperate var containing only letters
            $data.= $line;
        }  
    }
    fclose($fh);
} 

if ($sum != 0){
    //Display running total if numbers present
    echo 'Sum = '.$sum."<br/>";
}
foreach (count_chars($data, 1) as $i => $val) {
    //Display count of each letter
    echo chr($i). ' = '.$val."<br/>";
}  
?>[/PHP]I think the only way I am going to improve this at the minute is to get the string replace (or rtrim) out of the loop.  Suggestions welcomed :)

-Silver Fox

---

### Post by howlingmadhowie on 2010-02-18
> **Silver_fox_ said:**
> 
[PHP]<?php 
//Set Sum to 0
$sum = 0;
//Specify data file
$myFile = "data.txt";
$file_array = file($myFile);

//Trying a new method of reading in the file
if($fh = fopen("$myFile","r")){
    while (!feof($fh)){
        //A little house keeping
        $line = rtrim(fgets($fh,9999), "\r\n");
        //Sort out numbers and text
        if (is_numeric($line)) {
            //keep running total of numbers
            $sum = $sum + $line;
        }else{
            //Create seperate var containing only letters
            $data.= $line;
        }  
    }
    fclose($fh);
} 

if ($sum != 0){
    //Display running total if numbers present
    echo 'Sum = '.$sum."<br/>";
}
foreach (count_chars($data, 1) as $i => $val) {
    //Display count of each letter
    echo chr($i). ' = '.$val."<br/>";
}  
?>[/PHP]I think the only way I am going to improve this at the minute is to get the string replace (or rtrim) out of the loop.  Suggestions welcomed :)

-Silver Fox

delete the line '$file_array=file($myFile);'! that should improve memory usage greatly :)

---

### Post by pokebirdd on 2010-02-18
I've only ever programmed in C so here's my stab at the challenge:
[PHP]#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[])
{
    /*basic checking and then file loading*/
    if (argc != 2){
        printf("Usage: %s [file]\n", argv[0]);
        return 1;
    }
    FILE *fp = fopen(argv[1], "r");
    if (fp == NULL){
        fprintf(stderr, "Unable to open file %s\n", argv[1]);
        return 1;
    }

    int chars[256] = {0};
    int ch, ii;
    int sum = 0;

    while((ch = getc(fp)) != EOF){
         chars[ch]++;
    }

    for (ii = 0; ii < 10; ii++){
        sum += chars['0'+ii]*ii;
    }
    printf("Sum = %d\n", sum);

    for (ii = 0; ii < 256; ii++){
        if (chars[ii]  && ii != '\n')
            printf("%c = %d\n", ii, chars[ii]);
    }

    return 0;
}[/PHP]

I assumed that the values wouldn't just be alphanumerical. By the way, how do you check the speed of program like what howlingmadhowlie did?

---

### Post by s.fox on 2010-02-18
> **howlingmadhowie said:**
> delete the line '$file_array=file($myFile);'! that should improve memory usage greatly :)

Oh my,  how did I leave that in?  Laugh out loud!  Thank you for pointing that out :D

I was just seeing if the different methods of reading in the file compare against one another.   Any time saving would be highlighted in such a large file.

Version 3a with the silly mistake removed ;)

**How To Run:**  This PHP script is looking for a file in the same directory.  The file should be called data.txt

[PHP]<?php 
//Set Sum to 0
$sum = 0;
//Specify data file
$myFile = "data.txt";

//Trying a new method of reading in the file
if($fh = fopen("$myFile","r")){
    while (!feof($fh)){
        //A little house keeping
        $line = rtrim(fgets($fh,9999), "\r\n");
        //Sort out numbers and text
        if (is_numeric($line)) {
            //keep running total of numbers
            $sum = $sum + $line;
        }else{
            //Create seperate var containing only letters
            $data.= $line;
        }  
    }
    fclose($fh);
} 

if ($sum != 0){
    //Display running total if numbers present
    echo 'Sum = '.$sum."<br/>";
}
foreach (count_chars($data, 1) as $i => $val) {
    //Display count of each letter
    echo chr($i). ' = '.$val."<br/>";
}  
?>[/PHP]

---

### Post by howlingmadhowie on 2010-02-18
here's an updated openoffice spreadsheet.  i'd say don't worry about values less that 0.1 seconds.  the difference between C/C++ and the interpreted languages is clear.  i've also added a column for 100 million data points for the fast methods.

---

### Post by munky99999 on 2010-02-18
I tried to write a program in c++. Sadly I got nowhere. I was able to read the file Then be able to do things with it. I couldnt manage to do anything with it. I'm too beginner for that I guess. I might try again later. Though probably should just go back to learning c++

On the otherhand I managed to find that bash wont manage anything over 60bit integers; I'm wondering where the other 4 bits went.

---

### Post by Marlonsm on 2010-02-18
Well... Another one, a rewritten version of the second one using dictionaries, it was run about 5 times faster here: 3.6seconds instead of 19.5s for 1.9 million lines. The only problem is that it will only work if the input is right.

[php]file_data = open("input.txt", "r")  #import file
alphabet = ["Sum","a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"]
count = {} #Make a list with the items in the order they will be in the output
for item in alphabet: #Add those items to a dictionary
	count[item] = 0
chars = []
for line in file_data: #create a list with the contents from the imported file
	char = line.strip()
	chars.append(char)
for item in chars:     #test each imported item
	test_item = item
	if test_item.isdigit():       #if it's a number, add to the sum
		count["Sum"] += int(test_item)
	else:                         #if it's a letter, add to the count
		count[test_item] += 1
for item in alphabet:    #print them in order
	if count[item] != 0:
		print item, "=", count[item]
[/php]

This one has a small change and is somewhat slower, but works even if the input has errors:
[php]file_data = open("input2.txt", "r")  #import file
alphabet = ["Sum","a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"]
count = {} #Make a list with the items in the order they will be in the output
for item in alphabet: #Add those items to a dictionary
    count[item] = 0
chars = []
for line in file_data: #create a list with the contents from the imported file
    char = line.strip()
    chars.append(char)
for item in chars:     #test each imported item
    test_item = item
    if test_item.isdigit():       #if it's a number, add to the sum
        count["Sum"] += int(test_item)
    elif test_item in alphabet:    #check if the input is right
        count[test_item] += 1      #if it's a letter, add to the count
for item in alphabet:    #print them in order
    if count[item] != 0:
        print item, "=", count[item]  [/php]

> **gtr32 said:**
> You might find this useful:

[http://docs.python.org/tutorial/datastructures.html#dictionaries](http://docs.python.org/tutorial/datastructures.html#dictionaries)
Thanks, it helped a lot.

> **sharpdust said:**
> Good job, you are getting the idea, but you should never have to have a list with the entire alphabet in it.

Try this:

```

if theChar in string.ascii_lowercase:

```
Thanks, but using this I can't find a way to make the output be in alphabetical order, like in the first post.

---

### Post by Bachstelze on 2010-02-18
@howlingmadhowie: can you test this one please?

```
import Data.Char

results                     :: String -> ([(Char, Int)], Int)
printLettersCount           :: [(Char, Int)] -> IO ()


results []                  = ([], 0)
results (x:xs)
            | isLower x     = ((x, 1+length [c | c <- xs, c == x]):otherLettersCount, otherNumbersSum)
            | isDigit x     = (sameLettersCount, digitToInt x + otherNumbersSum)
            | otherwise     = nextWithoutThisChar
            where otherLettersCount = fst nextWithoutThisChar
                  otherNumbersSum   = snd next
                  sameLettersCount  = fst next
                  next = results xs
                  nextWithoutThisChar = results [c | c <- xs, c /= x]


printLettersCount []      = putStr ""
printLettersCount [a]     = do putStr [fst a]
                               putStr " = "
                               putStrLn (show (snd a))
printLettersCount (x:xs)  = do putStr [fst x]
                               putStr " = "
                               putStrLn (show (snd x))
                               printLettersCount xs


main = do
        -- Store the contents of the file as a string in the "file" variable.
        file <- readFile "bpc9.txt"

        -- Store the results in the "res" variable.
        let res = results file

        -- Print the sum
        putStrLn ("Sum = " ++ show(snd res))

        -- Print the letters counts
        printLettersCount (fst res)
```

---

### Post by howlingmadhowie on 2010-02-18
> **Bachstelze said:**
> @howlingmadhowie: can you test this one please?

```
import Data.Char

results                     :: String -> ([(Char, Int)], Int)
printLettersCount           :: [(Char, Int)] -> IO ()


results []                  = ([], 0)
results (x:xs)
            | isLower x     = ((x, 1+length [c | c <- xs, c == x]):otherLettersCount, otherNumbersSum)
            | isDigit x     = (sameLettersCount, digitToInt x + otherNumbersSum)
            | otherwise     = nextWithoutThisChar
            where otherLettersCount = fst nextWithoutThisChar
                  otherNumbersSum   = snd next
                  sameLettersCount  = fst next
                  next = results xs
                  nextWithoutThisChar = results [c | c <- xs, c /= x]


printLettersCount []      = putStr ""
printLettersCount [a]     = do putStr [fst a]
                               putStr " = "
                               putStrLn (show (snd a))
printLettersCount (x:xs)  = do putStr [fst x]
                               putStr " = "
                               putStrLn (show (snd x))
                               printLettersCount xs


main = do
        -- Store the contents of the file as a string in the "file" variable.
        file <- readFile "bpc9.txt"

        -- Store the results in the "res" variable.
        let res = results file

        -- Print the sum
        putStrLn ("Sum = " ++ show(snd res))

        -- Print the letters counts
        printLettersCount (fst res)
```

Bachstelze2.hs

compiled with
ghc6 -O2 Bachstelze2.hs -o Bachstelze

number of datapoints: time in seconds
10^2: 0.00
10^3: 0.01
10^4: 0.07
10^5: 0.51
10^6: 10.03
10^7: too long

sorry, but it seems to be getting slower :( 

maybe i did something wrong. i've never done anything with haskell before.

---

### Post by schauerlich on 2010-02-18
> **howlingmadhowie said:**
> calling atoi is also a big performance hit and should be avoided for the fastest possible solution. 

My original, with atoi:
```

10^5:
real 0m0.025s
user 0m0.019s
sys 0m0.003s

10^6: 
real 0m0.181s
user 0m0.172s
sys 0m0.005s

10^7:
real 0m1.733s
user 0m1.697s
sys 0m0.025s

10^8:
real 0m17.176s
user 0m16.950s
sys 0m0.213s

```

Changing atoi to c - '0':
```

10^5:
real 0m0.020s
user 0m0.016s
sys 0m0.003s

10^6:
real 0m0.167s
user 0m0.158s
sys 0m0.005s

10^7:
real 0m1.576s
user 0m1.548s
sys 0m0.023s

10^8:
real 0m15.743s
user 0m15.481s
sys 0m0.215s
```

Not much of a difference until it gets up to 10^7 characters.

---

### Post by s.fox on 2010-02-18
@howlingmadhowie:  

Would you mind testing out [this]("http://ubuntuforums.org/showpost.php?p=8845496&postcount=61") version of my script please?  It would be interesting to see how the different file read method altered the execution time.

Thanks if you can :)

-Silver Fox

---

### Post by falconindy on 2010-02-18
Wrote a threaded version in Java only to find out that I suck at threads. Maybe someone can figure out why this terminating early (results are about 5% off) when there's more than 1 thread.
```
import java.io.*;
import java.util.concurrent.*;
import java.util.*;

public class ThreadedSumFreq implements Runnable {
    private byte[] work;
    private final int w_start, w_end;
    public static int sum = 0;
    public static int[] freq = new int[26];

    public ThreadedSumFreq(byte[] work, int w_start, int w_end) {
        this.work = work;
        this.w_start = w_start;
        this.w_end = w_end;
    }

    public void run() {
        int c = 0;
        for (int i = w_start; i < w_end; i++) {
            c = 0;
            c |= work[i] & 0xFF;
            if (c > 96)
                ThreadedSumFreq.freq[c - 97]++;
            else if (c > 47)
                ThreadedSumFreq.sum += c - 48;
        }
    }

    public static final byte[] getFileAsBytes(final File file) throws IOException {
        final BufferedInputStream bis = new BufferedInputStream(new FileInputStream(file));
        final byte [] bytes = new byte[(int)file.length()];
        bis.read(bytes);
        bis.close();
        return bytes;
    }

    public static void main(String[] args) throws InterruptedException, IOException {
        final int NUM_THREADS = 1;
        byte[] fileContents = getFileAsBytes(new File("input.txt"));
        List threads = new ArrayList(NUM_THREADS);

        int start = 0, end = -1;

        for (int i = 0; i < NUM_THREADS; i++) {
            start = end + 1;
            end = start + (fileContents.length / NUM_THREADS) - 1;
            Thread t = new Thread(new ThreadedSumFreq(fileContents, start, end));
            t.start();
            threads.add(t);
        }

        for (int i = 0; i < NUM_THREADS; i++)
            ((Thread) threads.get(i)).join();

        System.out.printf("Sum = %d\n", ThreadedSumFreq.sum);
        for (int i = 0; i < freq.length; i++)
            if (freq[i] > 0)
                System.out.printf("%c = %d\n", i + 97, freq[i]);
    }

}
```

And here's the unthreaded version that reads from a byte array:
```
import java.io.*;

public class SumFreqFromMemory {
    public static final byte[] getFileAsBytes(final File file) throws IOException {
        final BufferedInputStream bis = new BufferedInputStream(new FileInputStream(file));
        final byte [] bytes = new byte[(int)file.length()];
        bis.read(bytes);
        bis.close();
        return bytes;
    }

    public static void main(String[] args) throws IOException {
        byte[] fileContents = getFileAsBytes(new File("input.txt"));
        int sum = 0;
        int[] freq = new int[26];
        int c;

        for (int i = 0; i < fileContents.length; i++) {
            c = 0;
            c |= fileContents[i] & 0xFF;
            if (c > 96)
                freq[c - 97]++;
            else if (c > 47)
                sum += c - 48;
        }

        System.out.printf("Sum = %d\n", sum);
        for (int i = 0; i < freq.length; i++)
            if (freq[i] > 0)
                System.out.printf("%c = %d\n", i + 97, freq[i]);
    }

}
```

---

### Post by Sinkingships7 on 2010-02-18
Just putting this out there: speed is certainly not a requirement for the challenge. The test file I'm using will only be a few hundred lines long. Of course, you're free to mess around and optimize your code. ;)

---

### Post by s.fox on 2010-02-18
> **Sinkingships7 said:**
> Just putting this out there: speed is certainly not a requirement for the challenge. The test file I'm using will only be a few hundred lines long. Of course, you're free to mess around and optimize your code. ;)

Good to know speed is not going to be the deciding factor in picking a winner, though it doesn't stop us having fun trying to speed things up :D

---

### Post by eeperson on 2010-02-18
Here's my Clojure version.  Its my first Lisp program beyond "Hello World" and my first time using Slime.

```

(ns file-reader
  (:import (java.io LineNumberReader FileReader)))

(defn read-file 
  "returns the lines in a file as a list"
  [file]
  (with-open [reader (LineNumberReader. (FileReader. file))]
	(loop [read-list '()]
	  (let [line (. reader (readLine))]
		(if line
		  (recur (conj read-list line))
		  read-list)))))

(defn sum-of-nums 
  "takes a seq of character numbers and sums them"
  [numbers]
  (reduce + (map #(Integer/parseInt %) numbers)))

(defn count-of-letters 
  "takes a seq of letters and returns a map containing counts for each letter"
  [letters]
  (loop [letter-counts {} letters-left letters]
	(if (empty? letters-left)
	  letter-counts
	  (recur (merge-with + letter-counts {(first letters-left) 1})
			 (rest letters-left)))))
	

(defn process-file 
  "top level function to processes the input file"
  [file]
  (let [file-contents (read-file file)
	numbers (filter #(re-matches #"[0-9]" %) file-contents)
	letters (filter #(re-matches #"[a-zA-Z]" %) file-contents)] 
	(println "Sum = " (sum-of-nums numbers))
	(dorun (map #(println (get % 0) "=" (get % 1)) 
		 (count-of-letters letters)))))

(process-file "input.txt")

```

---

### Post by howlingmadhowie on 2010-02-18
> **Silver_fox_ said:**
> @howlingmadhowie:  

Would you mind testing out [this]("http://ubuntuforums.org/showpost.php?p=8845496&postcount=61") version of my script please?  It would be interesting to see how the different file read method altered the execution time.

Thanks if you can :)

-Silver Fox

i forgot to say i added that to my second openoffice spreadsheet file. you can find it [here]("http://ubuntuforums.org/attachment.php?attachmentid=147461&d=1266513687"). It was about 30% faster and also stayed quite small :)

---

### Post by Marlonsm on 2010-02-18
> **Silver_fox_ said:**
> Good to know speed is not going to be the deciding factor in picking a winner, though it doesn't stop us having fun trying to speed things up :D
Agreed. We are here to learn, and knowing how to speed up things is certainly important.

---

### Post by howlingmadhowie on 2010-02-18
eeperson's entry in clojure:

run with "clojure eeperson.clj"

(couldn't get clojurec to work :D )
```

input size | time
  10^2       1.7s
  10^3       1.73s
  10^4       2.53s
  10^5       4.80s
  10^6       13.45s
  10^7       OutOfMemoryError

```

by the way, it doesn't print out the list of letters on my computer :(

---

### Post by howlingmadhowie on 2010-02-18
> **falconindy said:**
> Wrote a threaded version in Java only to find out that I suck at threads. Maybe someone can figure out why this terminating early (results are about 5% off) when there's more than 1 thread.
```
import java.io.*;
import java.util.concurrent.*;
import java.util.*;

public class ThreadedSumFreq implements Runnable {
    private byte[] work;
    private final int w_start, w_end;
    public static int sum = 0;
    public static int[] freq = new int[26];

    public ThreadedSumFreq(byte[] work, int w_start, int w_end) {
        this.work = work;
        this.w_start = w_start;
        this.w_end = w_end;
    }

    public void run() {
        int c = 0;
        for (int i = w_start; i < w_end; i++) {
            c = 0;
            c |= work[i] & 0xFF;
            if (c > 96)
                ThreadedSumFreq.freq[c - 97]++;
            else if (c > 47)
                ThreadedSumFreq.sum += c - 48;
        }
    }

    public static final byte[] getFileAsBytes(final File file) throws IOException {
        final BufferedInputStream bis = new BufferedInputStream(new FileInputStream(file));
        final byte [] bytes = new byte[(int)file.length()];
        bis.read(bytes);
        bis.close();
        return bytes;
    }

    public static void main(String[] args) throws InterruptedException, IOException {
        final int NUM_THREADS = 1;
        byte[] fileContents = getFileAsBytes(new File("input.txt"));
        List threads = new ArrayList(NUM_THREADS);

        int start = 0, end = -1;

        for (int i = 0; i < NUM_THREADS; i++) {
            start = end + 1;
            end = start + (fileContents.length / NUM_THREADS) - 1;
            Thread t = new Thread(new ThreadedSumFreq(fileContents, start, end));
            t.start();
            threads.add(t);
        }

        for (int i = 0; i < NUM_THREADS; i++)
            ((Thread) threads.get(i)).join();

        System.out.printf("Sum = %d\n", ThreadedSumFreq.sum);
        for (int i = 0; i < freq.length; i++)
            if (freq[i] > 0)
                System.out.printf("%c = %d\n", i + 97, freq[i]);
    }

}
```

And here's the unthreaded version that reads from a byte array:
```
import java.io.*;

public class SumFreqFromMemory {
    public static final byte[] getFileAsBytes(final File file) throws IOException {
        final BufferedInputStream bis = new BufferedInputStream(new FileInputStream(file));
        final byte [] bytes = new byte[(int)file.length()];
        bis.read(bytes);
        bis.close();
        return bytes;
    }

    public static void main(String[] args) throws IOException {
        byte[] fileContents = getFileAsBytes(new File("input.txt"));
        int sum = 0;
        int[] freq = new int[26];
        int c;

        for (int i = 0; i < fileContents.length; i++) {
            c = 0;
            c |= fileContents[i] & 0xFF;
            if (c > 96)
                freq[c - 97]++;
            else if (c > 47)
                sum += c - 48;
        }

        System.out.printf("Sum = %d\n", sum);
        for (int i = 0; i < freq.length; i++)
            if (freq[i] > 0)
                System.out.printf("%c = %d\n", i + 97, freq[i]);
    }

}
```

You have to synchronise entry to shared data structures, otherwise things can go badly wrong. I solved this in my threaded example by giving each thread its own sum and frequency array and then adding them together at the end.

your second file:

compiled with "javac falconindy3.java" (i changed the name)

```

input size | time
  10^2       0.17s
  10^3       0.21s
  10^4       0.15s
  10^5       0.22s
  10^6       0.21s
  10^7       0.36s
  10^8       1.41s

```

copying the entire file into memory seems to be the fastest way of doing this.

---

### Post by Some Penguin on 2010-02-18
> **falconindy said:**
> Wrote a threaded version in Java only to find out that I suck at threads. Maybe someone can figure out why this terminating early (results are about 5% off) when there's more than 1 thread.
```
import java.io.*;
import java.util.concurrent.*;
import java.util.*;

public class ThreadedSumFreq implements Runnable {
    private byte[] work;
    private final int w_start, w_end;
    public static int sum = 0;
    public static int[] freq = new int[26];

    public ThreadedSumFreq(byte[] work, int w_start, int w_end) {
        this.work = work;
        this.w_start = w_start;
        this.w_end = w_end;
    }

    public void run() {
        int c = 0;
        for (int i = w_start; i < w_end; i++) {
            c = 0;
            c |= work[i] & 0xFF;
            if (c > 96)
                ThreadedSumFreq.freq[c - 97]++;
            else if (c > 47)
                ThreadedSumFreq.sum += c - 48;
        }
    }

```

++ and += are not atomic operations; they consist of an arithmetic operation plus an assignment.   Now, given that, what happens if two threads happen to see the same character at the same time, and both do their arithmetic based on the unmodified value and then store it?

And how does the JVM know that other threads might want to read and write the same value, and therefore to be more careful with optimizations?

In the general case, you should probably read up on synchronization, locks and volatiles.  For this, because you're just doing counts, I suggest looking at AtomicIntegerArray (in the java.util.concurrent.atomic package.  The concurrency framework is generally pretty decent, although IIRC there are some mal-design features between the thread-pool executors and the priority blocking queue) and a plain AtomicInteger for the sum.

> ```

    public static final byte[] getFileAsBytes(final File file) throws IOException {
        final BufferedInputStream bis = new BufferedInputStream(new FileInputStream(file));
        final byte [] bytes = new byte[(int)file.length()];
        bis.read(bytes);
        bis.close();
        return bytes;
    }

    public static void main(String[] args) throws InterruptedException, IOException {
        final int NUM_THREADS = 1;
        byte[] fileContents = getFileAsBytes(new File("input.txt"));
        List threads = new ArrayList(NUM_THREADS);

        int start = 0, end = -1;

        for (int i = 0; i < NUM_THREADS; i++) {
            start = end + 1;
            end = start + (fileContents.length / NUM_THREADS) - 1;
            Thread t = new Thread(new ThreadedSumFreq(fileContents, start, end));
            t.start();
            threads.add(t);
        }

        for (int i = 0; i < NUM_THREADS; i++)
            ((Thread) threads.get(i)).join();

        System.out.printf("Sum = %d\n", ThreadedSumFreq.sum);
        for (int i = 0; i < freq.length; i++)
            if (freq[i] > 0)
                System.out.printf("%c = %d\n", i + 97, freq[i]);
    }
}


```

The AtomicIntegerArray's volatility-of-elements property will also be helpful when you're reading them.

---

### Post by djurny on 2010-02-18
```

/^[0-9]$/ {
        Sum+=$1
}

/^[a-z]$/ {
        alpha[$1]+=1
}

END {
        print "Sum = " Sum
        for (i in alpha) {
                print i " = " alpha[i] | "sort"
        }
}

```

maybe a bit cheating here, as this is awk (== programming language ;)) and gnu userland tooling at the same time :)

pretty straightforward though..!

```

cat programmingchallenge.txt | awk -f programmingchallenge
Sum = 23
a = 2
n = 2
w = 1
y = 1

```

oh, as for the bonus points, i am a daily awk (ab)user..

---

### Post by Some Penguin on 2010-02-18
> **djurny said:**
> [code]
]maybe a bit cheating here, as this is awk (== programming language ;)) and gnu userland tooling at the same time :)

pretty straightforward though..!


Personally, I'm a favor of using appropriate tools for the job, and straightforward tends to be good.  

Of course, there are limits -- you should probably think twice if you're building an extremely heterogeneous system.  For instance, you would probably not amuse your fellow programmers if you built vitally important, fundamental Java classes that relied on JNI calls to Fortran and Eiffel, because such a bizarre combination is likely going to be difficult to maintain, test or use, even if the Fortran bits and Eiffel bits individually seemed to be useful for their particular tasks.

---

### Post by eeperson on 2010-02-18
> **howlingmadhowie said:**
> 
by the way, it doesn't print out the list of letters on my computer :(

I got a little confused about the output in Slime.  I edited my code so it should print out properly.

---

### Post by GregBrannon on 2010-02-18
GregBrannon entry, written in Java.

To run:

1.Copy the source file, FileAlphaNumRead.java to a directory that contains the text file that will be used to test the function of the program.
In a terminal in the directory where the file was copied:
2.Type >javac FileAlphaNumRead.java
3.Type >java FileAlphaNumRead
4.Then respond appropriately to the program's prompts.

```
import java.util.NoSuchElementException;
import java.util.Scanner;
import java.io.*;

/*  FileAlphaNumRead.java
 *  
 *  Description: Ubuntu Forums Programming Challenge #9. The program opens a text
 *               file and reads its contents. The file contains only one alpha-
 *               numeric character per line, consisting of the alpha characters
 *               a - z, lower case only, and the numbers 0 - 9.  The file is read
 *               a line at a time, and the data read is stored in a 36-element
 *               array that then is used to tally the number of times each of the
 *               possible characters appears in the file. The program then uses
 *               the resulting tallies to print the sum of all numeric characters
 *               and report the number of times each lower case alpha character
 *               appeared in the file.
 *               
 *               For extra credit, the file will, at the user's option, create
 *               the target text file with a single random character on each line
 *               as described above. The user will be asked for the desired file
 *               name and the number of characters (or lines) desired.
 *
 *  References: "JavaNotes 5.1.1," D. J. Eck, Chapters 7 (arrays) and 11 (File I/O)
 *              "Java for Programmers," Deitel, Chapters 7 (arrays) and 14 (Files
 *              and Streams)
 *
 *  Version 0.1: Started 17 Feb 2010, completed 18 Feb 2010.
 *  
 *  OS/Environment: Written using Eclipse 3.4.0 in OpenSUSE 11.2/KDE 4.3.4 on a
 *                  Gateway GT5678 (Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.40 GHz
 *                  and java-1.6.0-openjdk-1.6.0.
 */

/**
 * @author GregBrannon
 *
 */
public class FileAlphaNumRead
{

    /**
     * @param args
     */
    public static void main( String[] args )
    {
        // Explain the program
        System.out.println();
        System.out.println( "This program is written in response to Ubuntu forums" );
        System.out.println( "Programming Challenge #9. The program reads characters" );
        System.out.println( "from a text file that are arranged one character per line." );
        System.out.println( "The possible characters are the letters a - z, lower case" );
        System.out.println( "only, and the numbers 0 - 9. The characters are read into" );
        System.out.println( "an array which tallies the number of times each of the" );
        System.out.println( "possible characters appears in the file and then reports" );
        System.out.println( "the sum of the numeric characters and the number of times" );
        System.out.println( "each alpha character appears in the file. (Zero occurrences" );
        System.out.println( "are not reported.)" );
        System.out.println();
        System.out.println( "Optionally, the program begins by offering to create the text" );
        System.out.println( "file that will be used to test the operation of the program." );
        System.out.println();
        
        // Offer to create the text file that will be used to test the program
        System.out.println();
        System.out.println( "Would you like this program to create the text file" );
        System.out.println( "that will be used to test the operation of the program? (Y/n): ");
        
        // Create a String variable and a scanner to get user's answers from the
        // default input
        String userChoice;
        String fileName = null;
        Scanner input = new Scanner( System.in );
        userChoice = input.next();
        
        if ( userChoice.equals( "n" ) )  // The file will not be created 
        {
            System.out.println();
            System.out.print( "What is the name of the input file? ");
            fileName = input.next();
        }
        else  // By default, the test file will be created to the user's
        {               // specifications
            int numChars = 0;  // To store the number of characters in the file
            System.out.println();
            System.out.print( "What would you like the file to be named? ");
            fileName = input.next();
            System.out.println();
            System.out.print( "How many characters would you like the file to have? " );
            numChars = input.nextInt();
            System.out.println();
            
            // Create the output stream for writing to a file
            PrintWriter outputData = null;
            
            try
            {
                outputData = new PrintWriter( new FileWriter( fileName ) );
            }
            catch ( IOException e )
            {
                System.out.println( "That file cannot be created.");
                System.out.println( "Error: " + e );
                System.out.println( "Exiting the program.");
                return;
            }
            
            // Write to the file the number of characters specified by numChars.
            // Characters written randomly are a - z and 0 - 9 with the alpha
            // characters favored roughly 3:1.
            
            int numericOut = 0;     // The numeric output variable
            char alphaOut = '\0';    // The alpha output variable
            
            for ( int i = 1; i <= numChars; i++ )
            {
                // Generate a random number 1 through 4 to decide if a number or letter
                // will be written to the file. ~3 letters are written for each number
                int j = (int)( Math.random() * 3 + 1 );
                if ( j == 1 ) //  If 1, write a number to the file.
                {
                    numericOut = (int)( Math.random() * 10 );
                    outputData.println( numericOut );
                }
                else  // Write an alpha character to the file
                {
                    numericOut = (int)( Math.random() * 26 + 97 );
                    alphaOut = (char)( numericOut );   // convert number to ascii character
                    outputData.println( alphaOut );
                }
            }

            outputData.close();
        }
        
        int[] inputChars = new int[ 36 ]; // Declare and create a 36-element
                                              // array of type character.
        
        // The 36-element array will be used to store the count of numeric
        // characters 0 - 9 and alpha character a - z, in that order.  The array
        // index will be based on the character's ascii value.
        // E.g. inputChars[0] = the number of '0' characters read from the
        // file. '0' is ascii 48, so the index will be determined by subtracting
        // 48 from the ascii value.  The same will be done for the alpha characters
        // starting at index 10 and the ascii value of 'a' = 97.

        // Open the file for reading
        
        Scanner inputData = null;
        String inputChar = null;
        int tallyIndex = 0;
        
        if ( fileName == null )  // If the input file was not generated by this
        {                         // program, get the file name from the user.
            System.out.println();
            System.out.println( "Name of input file (in same directory as program)?: " );
            fileName = input.next();
            System.out.println();
        }
        
        try     // Create the input stream to read data from the file
        {
            inputData = new Scanner( new File( fileName ) );
        }
        catch ( FileNotFoundException e )
        {
            System.out.println( "The file " + fileName + " does not exist." );
            System.out.println( "Exiting the program.");
            return;
        }
        
        try     // Read characters from the input file, tallying them in the
        {       //  character array according to their ascii value
            while ( inputData.hasNext() == true )    // read data from the file
            {                                       // until there is no more
                inputChar = inputData.next();       // Get the next character
                tallyIndex = (int)(inputChar.charAt(0) ); // get ascii value

                if ( tallyIndex < 97 )  // character is a numeral
                {
                    tallyIndex -= 48;   // index numeral '0'/ascii 48 to zero 
                }
                else                    // character is a letter
                {
                    tallyIndex -= 87;   // index alpha 'a'/ascii 97 to 10
                }
                
                inputChars[ tallyIndex ]++;  // increase resulting index by 1
            }
        }
        catch ( NoSuchElementException e )
        {
            System.err.println( "The specified file is not legal." );
            inputData.close();
            return;
        }
        catch ( IllegalStateException e )
        {
            System.err.println( "Error reading from file." );
            return;
        }
        
        // Calculate the sum of all numbers in the file by multiplying each number
        // by the number of occurrences and then summing the results, excluding 0
        
        int charSum = 0;
        
        for ( int i = 1; i < 10; i++ )
        {
            charSum += ( inputChars[ i ] * i ); // Sum of the multiple values
        }
        
        System.out.println();
        System.out.println( "The sum of the numbers in the file is: " + charSum  );
        
        // Print out the tally for each of the alpha characters
        
        for ( int i = 10; i < 36; i++ )
        {
            if ( inputChars[ i ] > 0 )  // Only display the non-zero totals
            {
                // Print index converted to ascii character, followed by tally
                System.out.println( (char)( i + 87 ) + "      " + inputChars[ i ] );
            }
        }

    } // end method main()

} // end class FileAlphaNumRead
```

---

### Post by s.fox on 2010-02-18
> **howlingmadhowie said:**
> i forgot to say i added that to my second openoffice spreadsheet file. you can find it [here]("http://ubuntuforums.org/attachment.php?attachmentid=147461&d=1266513687"). It was about 30% faster and also stayed quite small :)

Thank you for testing it for me :)

It looks like this method of reading the file is much faster :)

30% quicker is a nice result, especially given it stayed small. I do not think I can improve much more on this solution without a complete rewrite,  though ideas from people would be nice.

Once again thank you for testing my script out :D

- Silver Fox

---

### Post by kalaharix on 2010-02-19
So are these code examples for the VIC20 or the TRS80? C'mon guys, even phones have got GUIs now!

I also can't understand how a beginners challenge turned into a speed race. Modern computers are plenty fast enough to run even sloppy code (otherwise Microsoft wouldn't be here:)).

Here is a Gambas example.


```
' Gambas class file
'----------------------------------------------------
PUBLIC SUB Form_Open()
    ME.center                                 'centre form on screen
END
'----------------------------------------------------
PUBLIC SUB btnRun_Click()
  DIM iTotl AS Integer = 0                    'for total of numbers
  DIM iArraySize AS Integer = 1000            'initial size of input array
  DIM hFileIn AS File                         'input file handle
  DIM sChar AS String                         'variable to hold the line character
  DIM iCount AS Integer = 0                   'general loop counter for input
  DIM iCountOut AS Integer = 0                'general loop counter for output
  DIM myArray AS String[]                     'array to hold input
  DIM letterCount AS Integer[26]              'array to hold count of individual letters
  
  IF Exist(FileChooser1.value) THEN           'check if a file has been chosen
    myArray = NEW String[iArraySize]          'instantiate the array at default size
    hFileIn = OPEN FileChooser1.value FOR INPUT 'open the text file
    WHILE NOT Eof(hFileIn)                    'for each line in the text file
      LINE INPUT #hFileIn, sChar
        IF sChar = "" THEN                    'trap an empty line
          sChar = "_"
        ENDIF 
        sChar = Left(sChar, 1)                'limit to first digit of line in case there is more than one digit
        myArray[iCount] = sChar               'put into the array
        INC iCount                            'increment the counter by 1
        IF iCount = iArraySize - 1 THEN      'if the array has nearly reached its limits then expand
          iArraySize += 1000
          myArray.Resize(iArraySize)
        ENDIF
    WEND  
    FOR iCountOut = 0 TO icount - 1           'for each valid element in the array 
      IF IsNumber(Val(myArray[iCountOut])) THEN 'check if it is a number
        iTotl += myArray[iCountOut]           'add to the number total if it is
      ELSE 
        IF myArray[iCountOut] >= "a" AND myArray[iCountOut] <= "z" THEN     'check if it is a valid letter as defined in spec
          INC letterCount[Asc(myArray[iCountOut]) - 97]                     'add 1 to the count of that letter
        ELSE 
          ListBox1.Add("'" & myArray[iCountOut] & "' is not within specification and is ignored")     'add an error message to listbox
        ENDIF 
      ENDIF 
    NEXT 
    ListBox1.Add("The sum of numbers is " & iTotl)
    FOR iCount = 0 TO 25
      IF letterCount[icount] > 0 THEN 
        ListBox1.Add("Total number of letter '" & Chr(icount + 97) & "' is " & letterCount[icount])
      ENDIF 
    NEXT 
  ELSE 
    Message.Error("please select a file to analyse")
  ENDIF 
END
'----------------------------------------------------
PUBLIC SUB btnExit_Click()
  ME.close
END
'----------------------------------------------------
```
I don't particularly like the need to define and expand the input array. It's a bit clumsy compared to some of the other solutions in the thread. I suspect the logic might also have a problem if a-z don't have the same ascii values in other languages/keyboards (?).

It just needs a few standard objects on the form: a filechooser (default name filechooser1), a listbox (listbox1), a button named btnExit and a button named btnRun.

rgds

---

### Post by howlingmadhowie on 2010-02-19
hi :)

i've just created an intermediate programming challenge. It can be found [here]("http://ubuntuforums.org/showthread.php?p=8850170").

Have fun and happy hacking!

---

### Post by pedro3005 on 2010-02-19
Well, I'm learning python and this was helpful. I had to get a bit of help (was that cheating?), but I did lots of it myself. Not my hardest challenge yet :D!
```

import string
save = open("save.text", "a")
read = open("file.text", "r")
totalsum = 0
char_list = read.read().split("\n")
for item in char_list :
    if item.isdigit() :
        totalsum = totalsum + int(item)
for letter in string.ascii_lowercase :
    if letter in char_list :
        print "%s : appeared %s times." % (letter, char_list.count(letter))
print "The total sum was: %s." % (totalsum)
print "All information was saved to file save.text."
save.close()
read.close()

```It reads from the file called file.text
EDIT: Oopsie :P Fixed a bug that basically ruined the save file.

---

### Post by lavinog on 2010-02-19
I loaded the data into a list object because of this rule:
> Your program must read each line and store the data in a data structure of your choice. Parse through your structure and print out the following information:

[php]
#! /usr/bin/env python
DATAFILE = 'data.txt'

def loaddata(file):
    try:
            datafile = open(file)
    except IOError:
        print 'Error opening file: %s' % file
        return []
    data = [ c.strip() for c in datafile ]
    return data
    
def sumdigits(data):
    sum = 0
    for c in data:
        if c.isdigit():
            sum+=int(c)
    return sum

def countchars(data):
    charcount = {}
    for c in data:
        if c in charcount.keys():
            charcount[c]+=1
        else:
            charcount[c]=1
    return charcount

def main():
    data = loaddata(DATAFILE)
    if data:
            
        print 'sum =  %s' % sumdigits(data)
        for c,v in countchars(data).items():
            print '%s = %s'%(c,v)
    
if __name__=='__main__':main()
[/php]

I am wondering if list comprehensions could be used to improve the speed for larger data files.
I am also just learning about using iterators instead, so I might run a test to see what works better.

---

### Post by gtr32 on 2010-02-19
> **howlingmadhowie said:**
> i imagine the C methods with the 26 * sizeof(int) large array for storing the results will be comfortably faster than any other methods. they have the obvious advantage that the time to increment an existing letter-value is very small, probably just a handful of ticks.

Very true. They are simple and taking an advantage of the type of application that was described. The downside to those are that if the requirements change, major recoding is necessary. F.e. what if the requirement was changed from digits to social security numbers instead?

Like with every software project, you would have to pick the tools based on what the goals are. Fast? Flexible? Reusable?

Once the challenge is over I will try to find time to post a few versions that take this problem from multiple angles. The C# code I posted was a quick test on what I could do with LINQ statements that are quite new to me. As you can see, one regular expression and one line of code could solve an even more complex requirement than the one posted. It won't be the fastest solution in regards to processing but it certainly cuts down development time and effort.

---

### Post by howlingmadhowie on 2010-02-19
> **gtr32 said:**
> Very true. They are simple and taking an advantage of the type of application that was described. The downside to those are that if the requirements change, major recoding is necessary. F.e. what if the requirement was changed from digits to social security numbers instead?

Like with every software project, you would have to pick the tools based on what the goals are. Fast? Flexible? Reusable?

Once the challenge is over I will try to find time to post a few versions that take this problem from multiple angles. The C# code I posted was a quick test on what I could do with LINQ statements that are quite new to me. As you can see, one regular expression and one line of code could solve an even more complex requirement than the one posted. It won't be the fastest solution in regards to processing but it certainly cuts down development time and effort.

You may be interested in an advanced programming challenge i was thinking of posting.  Basically it would be "implement hasharrays as AVL trees and compare the performance creating a hasharray and doing some operations on this file #INSERT LARGE FILE HERE# compared with the native implementation in the language of your choice".

basically i'm interested in if AVL trees are faster than most hashing algorithms with hash buckets on most inputs.  i imagine they are, but it would be nice to have some data and getting others to do the footwork sounds like a great idea :)

---

### Post by howlingmadhowie on 2010-02-19
> **lavinog said:**
> I loaded the data into a list object because of this rule:


[php]
#! /usr/bin/env python
DATAFILE = 'data.txt'

def loaddata(file):
    try:
            datafile = open(file)
    except IOError:
        print 'Error opening file: %s' % file
        return []
    data = [ c.strip() for c in datafile ]
    return data
    
def sumdigits(data):
    sum = 0
    for c in data:
        if c.isdigit():
            sum+=int(c)
    return sum

def countchars(data):
    charcount = {}
    for c in data:
        if c in charcount.keys():
            charcount[c]+=1
        else:
            charcount[c]=1
    return charcount

def main():
    data = loaddata(DATAFILE)
    if data:
            
        print 'sum =  %s' % sumdigits(data)
        for c,v in countchars(data).items():
            print '%s = %s'%(c,v)
    
if __name__=='__main__':main()
[/php]

I am wondering if list comprehensions could be used to improve the speed for larger data files.
I am also just learning about using iterators instead, so I might run a test to see what works better.

apart from looping through the entire list twice (once to find the sum and once to find the frequency of the letters) this looks to be a pretty fast implementation. i'll check it on my reference laptop when i get home.

---

### Post by Dmck23 on 2010-02-19
Hi here is my entry written in java

Instructions to run:-
1)Copy the source code to the same directory as the test file save as FileCounter.java
2)Compile the program rom the terminal: javac FileCounter.java
3)Run the program passing in the name of the file as an argument: java FileCounter test.txt

FileCounter.java
```
import java.io.*;
import java.util.*;

public class FileCounter {

    public static void main(String[] args) {
        //Create a file from the args passed in by the user
        File data = new File(args[0]);
        
        //Create an ArrayList to store the letterCount objects
        ArrayList<LetterCount> count = new ArrayList<LetterCount>();
        
        //create fileReader and BufferedReader to read the data from file.
        try{
            FileReader input = new FileReader(data);
            BufferedReader buff = new BufferedReader(input);
            
            //boolean to tell if the end of file has been reached
            boolean eof = false;
            int total = 0;
            
            while(!eof){
                String line = buff.readLine();
                if(line == null){
                    eof = true;
                }else{
                    //create a try-catch to catch any NumberFormatExceptions by trying to convert
                    //a string into a Integer. If the exception is thrown then the line must be a char 
                    //and the catch will deal with counting the char's. If a exception isn't thrown then
                    //the Integer value is added to the total.
                    try{
                        total += Integer.parseInt(line);
                    }catch (NumberFormatException NFE){
                        //Boolean set to true for a new char, it will be set to false if the current
                        //line being read matches a char in the count array.
                        boolean newChar = true;
                        
                        //if the count array is not empty search through it to see if the current line
                        //matches a char already in the array.
                        if(count.size() != 0){
                            for(int i = 0;i<count.size();i++){
                                if(count.get(i).getChar().equals(line)){
                                    //if the line is equal to a character already in the array then the count
                                    //is incremented an newChar boolean set to false.
                                    count.get(i).setCount();
                                    newChar = false;
                                }
                            }
                            //if no char in the array matched the line then a new LetterCount object is
                            //added to the array for that char.
                            if(newChar){
                                count.add(new LetterCount(line));
                            }
                        }else{
                            //if this is the first char read then the a new LetterCount object is added to the array
                            count.add(new LetterCount(line));
                        }
                    }
                }    
            }
            //Close the buffer and print out the totals.
            buff.close();
            System.out.println("Sum = "+total);
            for(int i = 0;i<count.size();i++){
                System.out.println(count.get(i).getChar()+" = "+count.get(i).getCount());
            }
        }catch (IOException e){
            System.out.println(e.getMessage());
        }
    }
}

//Create a LetterCount class that will have two variables.the first is a String to store the char and the
//second is an int to store the amount of times the char has appeared
class LetterCount{
    private String letter;
    private int count;
    
    //the class has one  which reads in a string.  
    LetterCount(String let){
        letter  = let;
        count = 1;
    }
    
    public String getChar(){
        return letter;
    }
    
    public void setCount(){
        count++;
    }
    
    public int getCount(){
        return count;
    }
}
```

Welcome any feedback
Thanks,
Dmck23

---

### Post by falconindy on 2010-02-19
> **Dmck23 said:**
> Welcome any feedback
Thanks,
Dmck23
Definitely a different approach. I like your use of an exception to catch the different data type.

My 2 cents:
- While I applaud your effort to only track the exact number of elements you need, it's working against you because you have to search the entire ArrayList at a cost of O(n) before you do an insert or an update. You also don't declare an initial size or growth, so every insert into the ArrayList is fairly costly. Assuming the worst case scenario (26 elements in a simple array) is actually your best bet, because your cost is then a bounded constant. You're blindly specifying the offset (the letter's ascii value, modified) and incrementing whatever value is there.
- You don't need to actually catch your IOException in main since it's not going to be something you can recover from. Just mention in the function header that main "throws IOException". Exceptions are expensive and, while important, you should choose your battles so to speak.
- Your LetterCount class should declare 'letter' as a 'final char'. This goes towards optimization as you can predict that one and only one character value will ever need to exist in that attribute for the lifetime of the class.

---

### Post by munky99999 on 2010-02-19
I finally got my code working. It's very similar to [http://ubuntuforums.org/showpost.php?p=8837121&postcount=16](http://ubuntuforums.org/showpost.php?p=8837121&postcount=16)

So similar it's practically plagiarism. Except I used lists instead of vectors and changed many things trying to eliminate potential limits because of data types. I also never used algorithm or string headers. Performance wise the post I linked is ever so slightly faster. Quite noticeable with larger input.

It breaks though soon as I get to above 50,000,000 lines in the text.file. It uses about 1 gig of ram; only 1 cpu and takes just a bit over 1 min.

Sum: 64293750
a = 1428750

It doesnt seem like it's a problem with the program but the issue is that I'm running out of system ram when I go larger; then the program just cant manage to do the job.

How do figure out why it's crashing?

---

### Post by MinimalBin on 2010-02-21
[COLOR=Green]**Updated**[/COLOR] :)

data.txt
```
a
c
u
m
2
4
5
#
0
z
i
7

```application.rb
```
#!/usr/bin/env ruby

def numeric?(object)
    true if Float(object) rescue false
end

file = File.new("data.txt", "r")

data = Array.new
hmap = Hash.new(0)
numSum = 0

elementCounter = 0
while (line = file.gets)
    data[elementCounter] = line.gsub(/\n/, "")
    elementCounter = elementCounter + 1
end

for element in data
    if (numeric?(element))
        numSum = numSum + element.to_i
    elsif
        hmap[element] += 1
    end
end

hmap.each do |entry, count|
    puts "#{entry} = #{count}"
end

puts "\nNumber sum: #{numSum}"
```Run:
```
ruby application.rb
```

---

### Post by Sinkingships7 on 2010-02-21
I would like to remind everyone to provide instructions on how to run your programs. I have a lot of these to go through and it would really make my life a bit easier. Thank you. :)

---

### Post by Marlonsm on 2010-02-21
> **munky99999 said:**
> I finally got my code working. It's very similar to [http://ubuntuforums.org/showpost.php?p=8837121&postcount=16](http://ubuntuforums.org/showpost.php?p=8837121&postcount=16)

So similar it's practically plagiarism. Except I used lists instead of vectors and changed many things trying to eliminate potential limits because of data types. I also never used algorithm or string headers. Performance wise the post I linked is ever so slightly faster. Quite noticeable with larger input.

It breaks though soon as I get to above 50,000,000 lines in the text.file. It uses about 1 gig of ram; only 1 cpu and takes just a bit over 1 min.

Sum: 64293750
a = 1428750

It doesnt seem like it's a problem with the program but the issue is that I'm running out of system ram when I go larger; then the program just cant manage to do the job.

How do figure out why it's crashing?

Could you post the source here so we can test in another computer?
But 50 million lines is way over the proposed "hundreds" of lines in the first post, so it's nothing to worry about.

---

### Post by Some Penguin on 2010-02-21
> **munky99999 said:**
> 
It doesnt seem like it's a problem with the program but the issue is that I'm running out of system ram when I go larger; then the program just cant manage to do the job.

For this particular problem, is there a reason why you want to store all the input in memory at once?

---

### Post by falconindy on 2010-02-21
> **Some Penguin said:**
> For this particular problem, is there a reason why you want to store all the input in memory at once?
Why wouldn't you? I/O is expensive. Do it all at once and then read from RAM instead.

---

### Post by Some Penguin on 2010-02-21
> **falconindy said:**
> Why wouldn't you? I/O is expensive. Do it all at once and then read from RAM instead.

Not if there's 50 million rows and the system needs to thrash.  For that matter, even if the system doesn't thrash, reading it all first prevents synchronously reading and processing -- and a modern operating system might be able to notice and cache for sequential reads.

---

### Post by howlingmadhowie on 2010-02-22
> **Some Penguin said:**
> Not if there's 50 million rows and the system needs to thrash.  For that matter, even if the system doesn't thrash, reading it all first prevents synchronously reading and processing -- and a modern operating system might be able to notice and cache for sequential reads.

nevertheless, for large datasets reading the whole thing into memory at once does cut time down to a quarter.

however, one thing to try would be reading in a smaller amount at once, maybe 10MB or something.  That should allow fast processing while also saving time allocating huge amounts of ram on a busy system.

---

### Post by s.fox on 2010-02-22
Hello,

> **Sinkingships7 said:**
> I would like to remind everyone to provide  instructions on how to run your programs. I have a lot of these to go  through and it would really make my life a bit easier. Thank you. :)

Thank you for the reminder,  I edited my submission to include the how to run information.

> **Silver_fox_ said:**
> 
**How To Run:**  This PHP script is looking for a file in the same directory.  The file should be called data.txt

[PHP]<?php 
//Set Sum to 0
$sum = 0;
//Specify data file
$myFile = "data.txt";

//Trying a new method of reading in the file
if($fh = fopen("$myFile","r")){
    while (!feof($fh)){
        //A little house keeping
        $line = rtrim(fgets($fh,9999), "\r\n");
        //Sort out numbers and text
        if (is_numeric($line)) {
            //keep running total of numbers
            $sum = $sum + $line;
        }else{
            //Create seperate var containing only letters
            $data.= $line;
        }  
    }
    fclose($fh);
} 

if ($sum != 0){
    //Display running total if numbers present
    echo 'Sum = '.$sum."<br/>";
}
foreach (count_chars($data, 1) as $i => $val) {
    //Display count of each letter
    echo chr($i). ' = '.$val."<br/>";
}  
?>[/PHP]

-Silver Fox

---

### Post by Lux Perpetua on 2010-02-22
> **howlingmadhowie said:**
> nevertheless, for large datasets reading the whole thing into memory at once does cut time down to a quarter.

however, one thing to try would be reading in a smaller amount at once, maybe 10MB or something.  That should allow fast processing while also saving time allocating huge amounts of ram on a busy system.I wrote a C program to test this using the standard buffered IO capabilities of stdio.h. Actually, I found diminishing returns after about 1 kilobyte of buffer (the default being apparently 8192 bytes on my system). For smaller buffer sizes, however, the performance does suffer greatly. 

I'm not posting my test program here, following the guidelines in the OP. However, I can PM it to anyone who wants to experiment with it, or I can simply post it after the challenge is over.

---

### Post by kemra on 2010-02-23
Im just trying to put the finishing touches to an entry written in C#. Finally cracked a few things that were getting in my way with the code. Hopefully I should have it finished and tested by this evening. I will post back here tonight!

---

### Post by kalaharix on 2010-02-24
Hi

Instructions for the (only!) Gambas contribution:

Gambas does a good job at compiling run-time versions of applications so I have put a deb installer package at [deb Installer]("ftp://ftp.drivehq.com/charlesg628/PublicFolder/progchallenge_0.0-1_all.deb"). I have tested this on Ubuntu 9.04 and 9.10. The program can then be run from the applications menu under education.

For those with Gambas installed there is a source archive at [progChallenge Source]("ftp://ftp.drivehq.com/charlesg628/PublicFolder/progChallenge-0.0.5.tar.gz").

Just load the program from Applications,Education. Choose the file from the filechooser and run.

rgds

---

### Post by kemra on 2010-02-24
A bit later than promised but here is my entry. It is written in C# and takes an input file called **input.txt** in the same working directory as the compile executable.

```
using System;
using System.IO;
using System.Collections;
using System.Collections.Generic;

namespace Challenge9v3
{
	class Challenge9v3
	{
		public static int sum;
		public static Hashtable table = new Hashtable();
		private const string FILE_NAME = "input.txt";
    	public static void Main(String[] args) {
        	if (!File.Exists(FILE_NAME)) {
            	Console.WriteLine("{0} does not exist. Press any button to exit.", FILE_NAME);
            	Console.ReadKey(true);
            	return;
        	}
			using (StreamReader sr = File.OpenText(FILE_NAME)) {
				string s = "";
				while ((s = sr.ReadLine()) != null) {
					if(char.IsDigit(Convert.ToChar(s))) {
						sum = sum + Convert.ToInt32(s);
					} else {
						if(table.ContainsKey(s)) {
							table[s] = (int) table[s] + 1;
						   } else {
						   	table.Add(s, 1);
						   }
					}
				}
				}
				Console.WriteLine("Sum = " + sum);
				foreach(DictionaryEntry de in table) {
					Console.WriteLine("{0} = {1}", de.Key, de.Value);
				}
				Console.ReadKey(true);
		}
			}
	}
```

Definately not the most elegant solution but it works. Although I have one question, my alpha characters are printed out in the order they appear in the input file, is that OK for the purposes of the challenge? As although the example in the first post shows them sorted alphabetically the rules do not mention it.

---

### Post by Cooner on 2010-02-24
Just stumbled across this, and I don't think I qualify, but wanted to give thumbs up to those giving this a go.

To those doing it in python... somehow that just feels like cheating :D

Though the perl submissions are pretty nice too, I just have trouble reading them.

---

### Post by lavinog on 2010-02-24
> **Cooner said:**
> 
To those doing it in python... somehow that just feels like cheating :D

Isn't that the beauty of python though.

---

### Post by lavinog on 2010-02-24
Simplified my python version so that large data files shouldn't be an issue:

Change the DATAFILE to the appropriate file

EDIT:  replaced data.strip() with data[0] for a drastic improvement in speed
[php]
#! /usr/bin/env python
DATAFILE = 'data.txt'


def main():
    # initialize sum and dictionary
    sum = 0
    charcount={}
    
    # iterate through datafile
    for data in open(DATAFILE):
        
        #c = data.strip()    #remove nonprintable chars
        c = data[0]         # faster than stripping
        
        if c.isdigit():
            sum+=int(c)
        
        else:               # assuming only lowercase letters are the only other type
            if c in charcount.keys():
                charcount[c] += 1
            else:
                charcount[c] = 1
                

    # Sort keys
    chars = charcount.keys()
    chars.sort()

    # Output results
    print 'sum =  %s' % sum

    for c in chars:
        print '%s = %s'%(c,charcount[c])

if __name__=='__main__':main()
[/php]

Also wrote a script to create a data file:
[php]
#! /usr/bin/env python
DATAFILE = 'data.txt'

#DATALEN = 100000000  #191Mb file
DATALEN = 10000000  #20Mb file

import random

def makecharlist():
    charlist = range(10)
    charlist += [ chr(c) for c in range(ord('a'),ord('z')+1) ]
    return charlist

def main():
    charlist = makecharlist()
    count = 0
    file = open(DATAFILE,'w')
    
    while count < DATALEN:
        file.write('%s\n' % (random.choice(charlist)) )
        count +=1
    
if __name__=='__main__':main()
[/php]
I am curious if using list comprehensions can speed this up.

---

### Post by lavinog on 2010-02-24
I was able to reduce the processing time to almost half by using python3.1 and list comprehensions and sets.
One of the things that I am finding is that converting str to int is getting expensive.
I have to take a break from this, but the next thing I might try is to put everything into a dictionary, then multiply the count of each digit by the value.

Loading all of the data in memory does have a speed benefit too.  This might be a good time for me to figure out how to use yield to get blocks of data.

---

### Post by davidboy on 2010-02-24
Here's my solution written in Vala.  It will ask for the name of the file to process.  I've never used Vala before so I couldn't figure out how to convert a string to an int.  That's why I made the messy little toInt() function.    Also, the letter counts are sorted so that it prints out the count for a first, then b, and so on.  I tested it with the small sample provided and it worked fine.

However, the first post says > Your program must read each line and store the data in a data structure  of your choice. Parse through your structure and print out the following  information but mine goes though the file and at each line figures out if it's a number or letter and processes it before going on to the next line.  So I don't know if it's a valid entry or not.  Anyway, I had fun making it and learned alot about Vala.


[PHP]using GLib;

int sum = 0;
int[] lettercount;
string[] letters;

int main(string[] args) {
    lettercount = {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0};
    letters = {"a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"};
    
    stdout.printf("Enter the name of the file to parse: ");
    string filename = "";
    stdin.scanf("%s", filename);
    
    var file = File.new_for_path(filename);
    if (!file.query_exists(null)) {
        stderr.printf("Error: file %s does not exist\n", file.get_path());
        return 1;
    }
    
    processFile(file);
    printResults();
    
    return 0;
}
    
void processFile(File file) {
    try {
        var in_stream = new DataInputStream (file.read(null));
        string line;
        while ((line = in_stream.read_line(null, null)) != null) {
            processLine(line);
        }
    } catch (Error e) {
        stderr.printf("Error: %s", e.message);
        return;
    }
    
    return;
}    
void processLine(string line) {
    for (int i=0; i<25; i++) {
        if (line == letters[i]) {
            lettercount[i] += 1;
            return;
        }
    }
    sum += (toInt(line));
    return;
}

void printResults() {
    stdout.printf("Sum = %i\n", sum);
    for (int i=0; i<25; i++) {
        if (!(lettercount[i] == 0)) {
            stdout.printf("%s = %i\n", letters[i], lettercount[i]);
        }
    }
    return;
}

int toInt(string str) {
    switch (str) {
    case "0":
        return 0;
    case "1":
        return 1;
    case "2":
        return 2;
    case "3":
        return 3;
    case "4":
        return 4;
    case "5":
        return 5;
    case "6":
        return 6;
    case "7":
        return 7;
    case "8":
        return 8;
    case "9":
        return 9;
    }
    return 0;
}
[/PHP]To compile it:  Install the vala compiler with "sudo apt-get install valac" and then compile with "valac --pkg gio-2.0 programname.vala"

---

### Post by lavinog on 2010-02-24
This reduces my earlier code from 80s to 10s by counting everything first, then getting the sum from the digit count.
Also using the builtin count() made a big improvement.

[php]
#! /usr/bin/env python
DATAFILE = 'data.txt'
import math

def loaddata(file):
    try:
            datafile = open(file)
    except IOError:
        print('Error opening file: %s' % file)
        return []
    data = [ c[0] for c in datafile ]
    return data
    

def countchars(data):
    charlist = [ chr(c) for c in range(ord('a'),ord('z')+1) ]
    charlist += [ str(d) for d in range(10) ]
    
    counts = [ data.count(l) for l in charlist ]

    charcount = dict(zip(charlist,counts))
    
    return charcount

def sumdigits(data):
    sum = 0
    for c in data.keys():
        if c.isdigit():
            sum += data[c] * int(c)
    return sum
        

    
def main():
    data = loaddata(DATAFILE)

    if data:
        chardata = countchars(data)
        charkeys = list(chardata.keys())
        charkeys.sort()
            
            
        print 'sum =  %s' % sumdigits(chardata)
        for c in charkeys:
            if c.isdigit():continue
            print '%s = %s'% (c,chardata[c]) 
    
if __name__=='__main__':main()

[/php]

---

### Post by Barrucadu on 2010-02-24
I'm learning Pascal for my Computing AS level so decided to have a go. Works for files up to a million lines. Expects data file to be in the cwd named "beginner9.txt".

```
program Beginner9;

{ Your program should be able to open a text file and read its contents.
  The file will consist only of LOWERCASE letters and numbers 0-9.
  The file will be formatted such that there is only one alphanumeric character per line.

  Your program must read each line and store the data in a data structure of your choice. Parse through your structure and print out the following information:
    - The sum of all the individual digits.
    - How many times each character appeared in the file

  http://ubuntuforums.org/showthread.php?t=1407897

  Attempt by Barrucadu <mike@barrucadu.co.uk>. }

Uses SysUtils;

const
   FILESIZE = 1000000;         { Works for a file of up to 1,000,000 lines. Todo: figure out a way to dynamically grow the lines arrays. }
   FILENAME = 'beginner9.txt'; { Filename of data file. }

type
   carr	 = Array [0 .. FILESIZE] of Char;
   pcarr =  ^carr;

var
   lines : carr; { Data structure for read file ("read each line and store the data") }

Procedure readfile (fname : String; lines : pcarr); { readfile(fname) - read filename into an array. Pascal doesn't allow returning an array, so pointers. }
var
   fh	 : TextFile; { File handler }
   i   	 : Integer;  { Line counter }
begin
   i := 0;
   
   AssignFile(fh, fname); { Assign the file handler with the file }
   reset(fh);             { Open file in read mode }

   { While we still have stuff to read }
   while not eof(fh) do
   begin
      if i <= FILESIZE then
      begin
	 { Read a line and increment the counter. }
	 readln(fh, lines^[i]);
	 i := i + 1;
      end
      else
      begin
	 { Todo: figure a way around this. }
	 writeln('File too big, ignoring rest of lines.');
	 exit;
      end;
   end;

   CloseFile(fh); { Close the file handler }
end; { readfile }

Function countchar (pfile : carr; ascii : Char) : Integer; { countchar(pfile, ascii) - return the number of occurrences of ascii in pfile. }
var
   count, i : Integer; { Counting variable, and loop counter. }
begin
   count := 0;
   
   for i := 0 to FILESIZE do
   begin
      if pfile[i] = ascii then
      begin
	 count := count + 1;
      end;
   end;

   countchar := count;
end; { countchar }

Function sumtotal (pfile : carr) : Integer; { sumtotal(pfile) - return the total of all integers in pfile. }
var
   sum, i : Integer; { Sum variable, and loop counter. }
begin
   sum := 0;

   { For every line do }
   for i := 0 to FILESIZE do
   begin
      if (pfile[i] >= '0') and (pfile[i] <= '9') then { It's a number :D }
	 sum := sum + ord(pfile[i]) - 48;
   end;

   sumtotal := sum;
end;

Procedure showchars (pfile : carr); { showchars(pfile) - show char counts. }
var
   ascii, count	: Integer; { Current ascii code, and character count. }
begin
   for ascii := 32 to 126 do { The printing characters }
   begin
      count := countchar(pfile, chr(ascii)); { Get the character count. }

      if count > 0 then
	 writeln(chr(ascii), ' (', ascii, '): ', count); { Display character, ASCII code, and count }
   end;
end;

Procedure showsum (pfile : carr); { showsum(pfile) - show the sum of all digits. }
begin
   writeln('Sum total of all digits: ', sumtotal(pfile));
end; { showsum }

begin
   readfile(FILENAME, @lines); { Read/parse the file. }
   showchars(lines);           { Show character counts. }
   showsum(lines);             { Show sum total. }
end.

```

Compile with `fpc beginner-9.pas -Mobjpas`.

---

### Post by gtr32 on 2010-02-24
> **djurny said:**
> maybe a bit cheating here, as this is awk (== programming language ;)) and gnu userland tooling at the same time :)

Not at all, it gets the job done. If you look at the code I posted earlier this is the same approach I took. Instead of awk I used C# and regular expression library. The beauty of it is if the criteria (file format f.e.) changes, you are well prepared and most likely just have to change your regular expression formula.

---

### Post by Lux Perpetua on 2010-02-24
> **Some Penguin said:**
> Personally, I'm a favor of using appropriate tools for the job, and straightforward tends to be good.  

Of course, there are limits -- you should probably think twice if you're building an extremely heterogeneous system.  For instance, you would probably not amuse your fellow programmers if you built vitally important, fundamental Java classes that relied on JNI calls to Fortran and Eiffel, because such a bizarre combination is likely going to be difficult to maintain, test or use, even if the Fortran bits and Eiffel bits individually seemed to be useful for their particular tasks.Once I wrote a program with a display end written in PostScript and a computation back end in Octave. Unfortunately, as far as I know, PostScript code cannot run external programs. Thus, I also had a shell script to spawn the PostScript and Octave parts as processes, which subsequently communicated via named pipes. You're probably wondering: why the hell would I do that? Well, at first, PostScript seemed extremely convenient for the type of graphical output I wanted, so I started coding that part of it. I ran into trouble when I realized I had to use other tools for parts of it and somehow combine it all. In hindsight, it was pretty stupid; I'm probably better off rewriting it from scratch if I ever need that code in the future. (I'd probably try to do the whole thing in Python with Scipy for the computation and possibly Cairo for the output.)

---

### Post by myrtle1908 on 2010-02-24
> **Cooner said:**
> Though the perl submissions are pretty nice too, I just have trouble reading them.

Yes.  Perl is particularly good at this type of task.  After all, it was designed for mundane text munging such as this.  I don't qualify for this challenge as I'm not a beginner but it saddened me that nobody had submitted a Perl implementation ... so I did (page 3).

---

### Post by conehead77 on 2010-02-25
Haskell. It is based on Bachstelze's solution ([link]("http://ubuntuforums.org/showpost.php?p=8836333&postcount=12")). At first i only wanted to remove the explicit recursion in his code (printLettersCount and lettersCount), but when i was finished the program looked totally different.
[PHP]
import Data.Char (isAlpha, isDigit, digitToInt)
import Data.List (nub)

digitsSum :: String -> Int
digitsSum = sum . map digitToInt . filter isDigit 

lettersCount :: String -> [(Char, Int)]
lettersCount s = nub $ map makeTuple letterList                            
  where letterList = filter isAlpha s
        makeTuple x = (x, length $ filter (==x) s)

main = do
  file <- readFile "bpc9.txt"
  putStrLn $ "Sum = " ++ show (digitsSum file)
  mapM_ (putStrLn . tostring) (lettersCount file) 
    where tostring (x,y) = [x] ++ " = " ++ show y
[/PHP]

You rarely need to roll your own recursion with Haskell, there is almost always a variant of map or filter to save your day.

If speed is a matter, do not use String but ByteString. If i have some time today i might provide an example.

---

### Post by patrickaupperle on 2010-02-25
Here is my entry in Java. I am sure it is done horribly, but I am a beginner with java. Comments are appreciated. 
```
import java.util.Scanner;
import java.io.File;
import java.io.FileNotFoundException;
import java.util.ArrayList;
public class Count {
	public static void main(String args[]) throws FileNotFoundException {
		Scanner fileIn = new Scanner(new File("data.txt"));
		int sum = 0;
		ArrayList<String> lList = new ArrayList<String>(); //letterList
		ArrayList<Integer> nOfLList = new ArrayList<Integer>(); //numberOfLetterList
		while (fileIn.hasNext()) {
			if (fileIn.hasNextInt()) {
				sum = sum + fileIn.nextInt();
			} else {
				String n = fileIn.next();
				if (lList.indexOf(n) == -1) {
					lList.add(n);
					nOfLList.add(1);
				} else {
					int i = nOfLList.get(lList.indexOf(n));
					nOfLList.set(lList.indexOf(n), ++i);
				}
			}
		}
		System.out.println("sum = "+sum);
		for (String l : lList) {
			System.out.println(l+": "+nOfLList.get(lList.indexOf(l)));
		}
			
	}
}
```

:D First time I have been able to enter into one of these challenges (I started doing them too late).

Edit: Oops, I didn't include a how to run. Although it is probably unnecessary, as this is an average java program, here it is. Put this code in a file called "Count.java". Put "data.txt" in the same folder. run "javac Count.java" then "java Count".

---

### Post by Sinkingships7 on 2010-02-25
New entries are still coming in frequently enough to postpone the judging. Until things slow down, keep coding!

---

### Post by lavinog on 2010-02-26
This is my final try with python:
It now attempts to determine if it should process the whole file at once or in chunks to conserver memory.  Maybe one day I can figure out a good way to check free memory from within the program, so it can compensate automatically (and not cause the system to swap)

[php]
#! /usr/bin/env python
DATAFILE = 'data.txt'
CHUNKLIMIT  = 20000000  # Determines if parsing will be done in chunks
CHUNKSIZE   = 20000000



DO_CHUNKS = False       # True will force parsing in chunks
SHOW_TIME = True

import time

def loaddata(file):
    file.seek(0)   # in case we are re-reading file
    data = [ c[0] for c in file ]
    return data
    
def load_data_chunk(file,chunksize):
    file.seek(0)   # in case we are re-reading file
    data = []
    for c in file:
        data.append(c[0])
        if len(data) >= chunksize:
            yield data
            data = []
    yield data
    
def gencharlist():
    charlist = [ chr(c) for c in range(ord('a'),ord('z')+1) ]
    charlist += [ str(d) for d in range(10) ]
    return charlist    
    
def countchars(data,charcount=None):
    # This shouldn't be called too many times to make a difference
    charlist = gencharlist()
    
    counts = [ data.count(l) for l in charlist ]
    
    if charcount:
        for c,v in zip(charlist,counts):
            charcount[c] += v
        
    else:
        charcount = dict(zip(charlist,counts))
    
    return charcount

def sumdigits(data):
    sum = 0
    for c in data.keys():
        if c.isdigit():
            sum += data[c] * int(c)
    return sum
        
def get_eof(file):
    while file.read(1024):
        pass # just wanting to get to eof

    return file.tell()
    
def get_chars_from_pos(file):
    pos = file.tell()
    file.seek(0)
    linesize = len(file.readline())
    file.seek(pos)
    charcount = int(pos/linesize)
    return charcount

def parsedata(file):
    data = loaddata(file)
    return countchars(data)

def parsechunks(file,chunksize):
    data = load_data_chunk(file,chunksize)
    chardata=None
    processed_count = 0
    for datapiece in data:
        piecesize = len(datapiece)
        chardata = countchars(datapiece,chardata)
        processed_count += piecesize
        if piecesize:
            print ' Total Processed: %s'%processed_count
        
    return chardata
    
def main():
    try:
        file = open(DATAFILE)
    except IOError:
        print('Error opening file: %s' % DATAFILE)
        return

    eof = get_eof(file)
    totalchars = get_chars_from_pos(file)
    print 'Total characters: %s' % totalchars
    
    do_chunks = DO_CHUNKS
    
    if totalchars > CHUNKLIMIT:
        do_chunks = True

    starttime = time.time()
    if do_chunks:
        chardata = parsechunks(file,CHUNKSIZE)
    else:
        chardata = parsedata(file)
    stoptime = time.time()
    
    charkeys = list(chardata.keys())
    charkeys.sort()
        
    print 'sum =  %s' % sumdigits(chardata)
    for c in charkeys:
        if c.isdigit():continue
        print '%s = %s'% (c,chardata[c]) 
    if do_chunks:
        print 'Completed using data chunks'
        
    if SHOW_TIME:
        print 'Time to complete: %s secs' % (stoptime - starttime)


if __name__=='__main__':
    main()
[/php]

---

### Post by BoGs on 2010-02-26
So I thought I would try my hand out at ruby :D

here is my go at it

```
#!/usr/bin/ruby -v

def is_number?(i)
  true if Float(i) rescue false
end

counter = 0
sum = 0
letters = Array.new

file = File.new("data.txt", "r")

while(line = file.gets)
    if is_number?(line) then
        sum += line.to_i
    else
        letters[counter] = line.rstrip
        counter = counter + 1
    end
end

file.close

letters = letters.inject(Hash.new(0)) {|h,x| h[x]+=1;h}.sort
puts "Sum = #{sum}"

letters.each { |letter|
    puts "#{letter[0]} = #{letter[1]}"
}


```

```

bogdan@x:~/Documents/programming/comp$ ruby ruby.rb
Sum = 23
a = 2
n = 2
w = 1
y = 1

```

This was a blast thank god or i would of never got into ruby :) i like but i don't like :D

---

### Post by cprofitt on 2010-02-26
I made it so the file will be taken in the command line argument. This example is done in Python which I am, sadly, still trying to learn. I also wanted to print out the name of the file analyzed as a verification that the proper file had been used.

[php]
#!/usr/bin/env python
# programming challenge 9
# written by cprofitt 2/26/2010
# version .0.1

import sys
import fileinput

# main will open the file and read line by line
def main():
        # print the name of the file analyzed
        print "file: " + sys.argv[1]

        # define numeric total variable
        iSum = 0

        #define dictionary to count instances of alpha characters
        cDict = {}

        # handle each line
        for line in fileinput.input(sys.argv[1]):
                line = line.strip()

                if line.isdigit(): # handle integers
                        iSum = iSum + int(line)
                else: # handle characters
                        cDict[line] = cDict.get(line, 0) + 1

        # print the total of the numeric lines in the file
        print "Sum = " + str(iSum)

        # print the count for each alpha in the file
        for cKey, iValue in sorted(cDict.items()):
                print cKey + " = " + str(iValue)

main()

[/php]

my sample file is attached.

the output is:
$ python text.py ufpc9.txt
file: ufpc9
Sum = 163
a = 6
b = 5
c = 5
d = 3
e = 5
f = 2
g = 3
h = 1
i = 1
j = 2
n = 1
p = 1
q = 2
r = 3
s = 2
t = 1
u = 2
v = 1
w = 1
y = 4
z = 3

---

### Post by cprofitt on 2010-02-26
> **lavinog said:**
> This is my final try with python:
It now attempts to determine if it should process the whole file at once or in chunks to conserver memory.  Maybe one day I can figure out a good way to check free memory from within the program, so it can compensate automatically (and not cause the system to swap)

Interesting code.

I liked the time to completion code... very nice.

---

### Post by Sinkingships7 on 2010-03-02
Last call for programs. I will begin judging tomorrow. If you need more time, don't hesitate to send me a PM or post here.

---

### Post by Lux Perpetua on 2010-03-03
I'm not a beginner in any reasonable definition, but there's no real possibility of someone copying this and getting away with it. I recently started learning ARM assembly for fun, and I used this as an exercise to help me along. To run this, if you don't run an ARM system, you'll need (1) an ARM assembler, (2) an ARM linker, and (3) an ARM user-space emulator. There are no other dependencies (not even libC). On Arch Linux, you can get (1) and (2) from the package cross-arm-elf-binutils, but there probably isn't a Ubuntu equivalent. It looks like you can get them from here, though: 

[http://www.gnuarm.com/](http://www.gnuarm.com/) 

The qemu emulator, which hopefully has a Ubuntu package, includes ARM support via the program qemu-arm (item (3) in my list).

Some notes about the code:

The integer division instruction isn't standard on ARM processors. Integer division (by 10, specifically) is actually pretty useful if you want to print out integers in base 10. I wrote my own "print_int" function, which requires a "div10" function for division by 10, which I also wrote. 

There's one more cool thing I'd like to point out about the code, something you can only do in assembly language, and can't do without considerable difficulty unless all instructions have the same size in memory. (All ARM instructions are 4 bytes long, and "Thumb"-mode instructions, which I used for the code table (explained in the next sentence), are 2 bytes long.) I made a table of blocks of instructions, and I use the input character as an index into it to select the right behavior. For input characters '0', ..., '9', the corresponding block will update the running digit sum. For inputs 'a', ..., 'z', the corresponding code block will increment the counter (in a table) for that letter. For all other characters, the block does nothing. (Actually, I slightly lied that this can only be done in assembly language: in theory, a switch/case construct in C or C++ could be compiled to a similar structure. However, this is completely at the compiler's discretion, so it doesn't really count, since you can't implement it directly.) 

I won't say the rest is self-explanatory, since it's still assembly, but hopefully the comments will guide any interested readers. ```
        .section .data
        
        /* For output */
error_msg1:
        .ascii "No file specified\n"
error_msg1_end:
        error_msg1_length = (error_msg1_end - error_msg1)
        
error_msg2:
        .ascii "Couldn't find file\n"
error_msg2_end:
        error_msg2_length = (error_msg2_end - error_msg2)

string1:
        .ascii "Sum = "
string2:
        .skip 1
        .ascii  " = "

        .align 2
        
        .arm
        
        /* This table will count the occurrences of each letter */
count_table:
        .skip   26*4

        .align 2
        .global _start

        /* Program entry point */
_start:
        /* [sp] = argc, [sp+4] = argv[0], [sp+8] = argv[1], etc. */
        ldr     r0, [sp]                
        cmp     r0, #2
        bge     argc_okay

        /* Too few command-line arguments were given */
        mov     r0, #2                  @ 2 for stderr
        adr     r1, error_msg1
        mov     r2, #error_msg1_length
        swi     0x900004                @ `write' syscall
        
        mov     r0, #1
        swimi   0x900001                @ `exit' syscall

argc_okay:      
        ldr     r0, [sp, #8]            @ filename from argv[1]
        mov     r1, #0                  @ 0 = O_RDONLY
        swi     0x900005                @ open syscall
        movs    r8, r0                  @ r8 = file desc. for reading
        bpl     open_okay
        
        /* There was an error opening the file */
        mov     r0, #2                  @ 2 for stderr
        adr     r1, error_msg2
        mov     r2, #error_msg2_length
        swi     0x900004                @ `write' syscall

        mov     r0, #1
        swimi   0x900001                @ `exit' syscall


open_okay:     
        mov     r5, #0                  @ r5 tracks the sum of digits
        adr     r7, count_table
        adr     r6, loop1_begin

        /* We'll put each input character on the stack.
         * Technically, we only need a byte for this, but
         * the APCS stipulates that sp should always be word-aligned.
         */

        sub     sp, sp, #4              @ space for input
        
loop1_begin:   
        mov     r0, r8                  @ file descriptor for reading
        mov     r1, sp                  @ input destination
        mov     r2, #1                  @ input size (1 byte)
        swi     0x900003                @ execute `read' syscall
        subs    r0, r0, #1              @ check return value
        bmi     loop1_end               @ (if we couldn't read anything)
        
        ldrsb   r0, [sp]
        adr     r1, code_table
        movs    r2, r0
        bmi     loop1_begin             @ (if it's outside ASCII range)
        add     r1, r1, r0, LSL #3

        add     r1, r1, #1              @ for thumb mode
        /*  now r1 = code_table + 8*(input byte value) + 1 */

        /* We compute this here to save space in the code table */
        sub     r3, r7, #'a'*4
        add     r3, r3, r2, LSL #2

        bx      r1

        /* This is an array of blocks of executable code,
         * indexed by the input character. Each ASCII character has a
         * block of four thumb instructions (i. e., 8 bytes).
         */

        .thumb

code_table:
        .rept   48                      @ ['\0', '0)
        bx      r6
        .skip   6
        .endr

        .rept   10                      @ ['0', '9']
        sub     r2, #'0'
        add     r5, r2
        bx      r6
        .skip   2
        .endr
        
        .rept   39                      @ ('9', 'a')
        bx      r6
        .skip   6
        .endr

        .rept   26                      @ ['a', 'z']
        ldr     r1, [r3]
        add     r1, #1
        str     r1, [r3]
        bx      r6
        .endr

        .rept   5                       @ ('z', 0x7f]
        bx      r6
        .skip   6
        .endr
        
        .arm
        
loop1_end:
        mov     r0, #1                  @ 1 for stdout
        adrl    r1, string1
        mov     r2, #6
        swi     0x900004                @ `write' syscall

        mov     r0, r5
        bl      print_int
        bl      newline

        /* There's probably a more elegant way to set up
         * this loop...
         */
        mov     r4, #26
        add     r7, r7, #26 * 4
loop2_begin:
        sub     r1, r7, r4, LSL #2
        ldr     r6, [r1]

        /* Don't print anything if the count is zero */
        movs    r6, r6
        beq     loop2_test
        
        rsb     r0, r4, #'z'+1
        adrl    r1, string2
        strb    r0, [r1]

        mov     r0, #1
        mov     r2, #4
        swi     0x900004

        mov     r0, r6
        bl      print_int
        bl      newline
        
loop2_test:     
        subs    r4, r4, #1
        bne     loop2_begin
        
        mov     r0, #0
        swi     0x900001                @ `exit' syscall


        /* Auxiliary functions */

buffer:
        .skip 36
buffer_end:

        .align 2
        /* prints out r0 (in base 10) */
print_int:
        stmfd   r13!, {r4-r8, r10, r11, r14}

        movs    r5, r0
        rsbmi   r0, r0, #0
        
        adr     r4, buffer_end
dec_digits_loop:
        bl      div10
        
        add     r1, r1, #'0'
        strb    r1, [r4, #-1]!
        cmp     r0, #0
        bne     dec_digits_loop

        mov     r1, #'-'
        cmp     r5, #0
        strmib  r1, [r4, #-1]!

        mov     r0, #1
        mov     r1, r4
        adr     r2, buffer_end
        sub     r2, r2, r4
        swi     0x900004

        ldmfd   r13!, {r4-r8, r10, r11, r14}
        mov     pc, lr

        
        /* (r0, r1) = (r0 div 10, r0 mod 10)
         * This is a quick hack to divide an integer by 10.
         */
div10:
        mov     r2, r0
        
        mov     r0, r0, ASR #4
        add     r0, r0, ASR #1
        add     r0, r0, r0, ASR #4
        add     r0, r0, r0, ASR #8
        add     r0, r0, r0, ASR #16
        
        mov     r1, r0, LSL #1
        add     r1, r1, r0, LSL #3

        sub     r1, r2, r1
div10_correct_loop:
        subs    r1, r1, #10
        addpl   r0, r0, #1
        bpl     div10_correct_loop

        add     r1, #10
        mov     pc, lr

        
nl:
        .byte '\n'

        .align 2
        /* prints '\n'. Does not modify registers. */
newline:
        stmfd   r13!, {r0-r4, r14}
        
        mov     r0, #1
        adr     r1, nl
        mov     r2, #1
        swi     0x900004

        ldmfd   r13!, {r0-r4, r14}
        mov     pc, lr
        
```To assemble: ```
arm-elf-as -o beginners_09.o beginners_09.s
arm-elf-ld -s -Ttext-segment 54 -o b09 beginners_09.o
```(The prefix "arm-elf-" might be different for you, and you can omit the arguments **-s -Ttext-segment 54** to the linker if you don't mind a larger executable.) To run: ```
qemu-arm b09 <filename>
```
There may be a few bugs, but it seems to work on the few files I tested it on. Also, it uses unbuffered input (making a separate syscall to read() for each byte), which probably hurts performance a bit. Implementing buffered input directly in ARM assembly would be a good exercise, but I didn't do it for this one.

---

### Post by cprofitt on 2010-03-05
> **Sinkingships7 said:**
> Last call for programs. I will begin judging tomorrow. If you need more time, don't hesitate to send me a PM or post here.


Cool... it will be interesting to see the results... and then have the next challenge.

---

### Post by Sinkingships7 on 2010-03-06
And the winner of the beginner's programming challenge #8 is...

**cprofitt**!

I chose his submission because it was to the point, made good use of built-in tools and, most importantly, was well-commented and therefore easy to read and understand by beginners.


Some honorable mentions:

howlingmadhowie for his Scheme implementation and for bringing stimulating conversation to the thread with talks of multithreading and speed.

Bodsda's Python implementation for EXTREMELY well-commented code.

falconindy for his simple-yet-effective C implementation.


It's up to cprofitt to come up with the next challenge. Thanks to all participants. I hope everyone was able to take something away from this challenge!

---

### Post by s.fox on 2010-03-06
Congratulations cprofitt :D  Nicely done

Also well done to all those who entered, I really enjoyed looking through your submissions :D.  I am already looking forward to the next challenge.

-Silver Fox

---

### Post by Marlonsm on 2010-03-06
Congrats for cprofit, and thanks for everybody here, I'm sure many people learned a lot here.

---

### Post by cprofitt on 2010-03-06
Thanks... I am... ah... Wow.

Now to find a good beginners 'problem' to solve.

I hope to have it up in the next 12-24 hours.

---

### Post by mo.reina on 2010-03-08
i know i'm late to the party but wanted to post my code anyway... it's a bit redundant, i've only started learning python...
```
total = 0
count = 0
final =[]

#open the file and assign its value to the variable "readfile"
readfile = open("file.txt", "r").read()
#loop for every line in "readfile"
for line in readfile:
  #check if line is a digit, if so sums it with the total
  if line.isdigit():
    total = total + int(line)
  #lines that are not digits
  else:
    #deletes if newline is present (avoids the counting of newlines)
    if line == "\n":
      del line
    #places value in temporary var "holder"
    else:
      holder = line
      #checks "readfile" for every instance of the value in the var "holder"
      for item in readfile:
	#increments the number of times the value of "holder" is present
        if item == holder:
          count += 1
      #records the value of "holder" and the number of times it is present
      string = holder, "=", count
      #checks if there is a duplicate in the final list (otherwise the duplicate elements are counted again)
      if string in final:
        del string
      else:
        final.append(string)
      count = 0
print "total = ", total
for line in final:
  print line
```

---

### Post by lavinog on 2010-03-08
> **mo.reina said:**
> i know i'm late to the party but wanted to post my code anyway... it's a bit redundant, i've only started learning python...

Some things to experiment with:

```
    total = total + int(line)
```
can be replaced with:
```
    total += int(line)
```
It doesn't change the behavior (not sure if there would be any speed benefits), but it is less code to type.

```
readfile = open("file.txt", "r").read()
```
can be replaced with:
```
readfile = open("file.txt")
```
same reason as above.

```
    if line == "\n":
      del line

```
```
    if len(line.strip())==0:
      continue

```
strip removes non-printable characters.
continue will skip to the next value in the for loop (eliminates the need for the else statement, and nested if statements)
del line is a wasted step since it will get reassigned anyway.

You also don't need to copy line into a holder,  just continue to use line for your tests:
```

        if item == line:
          count += 1
      #records the value of "line" and the number of times it is present
      string = line, "=", count

```

```

      if string in final:
        del string
      else:
        final.append(string)

```
```

      if string not in final:
        final.append(string)

```
Again, no need to del string...it will be done automatically.

```

      string = holder, "=", count

```
Although your string setup works, you may want to learn how to do it this way:
```

      string = '%s = %s' % (holder, count)

```

You algorithm works, but it is inefficient.  If the input file contains 100 repeated 'a' characters, your algorithm will count all 'a's 100 times.
Instead find a way to count each character once.
Two ways to do this:
make a list of each possible character (a-z) and iterate through the list counting each one.
or
Utilize python's dictionary type and check to see if a character already exists in the dictionary.
You can also just add a list for characters that have already been counted, and check that the character isn't in the list (This will be the easiest to implement in your code without a major rewrite.)

---

### Post by mo.reina on 2010-03-10
> **lavinog said:**
> 
You algorithm works, but it is inefficient.  If the input file contains 100 repeated 'a' characters, your algorithm will count all 'a's 100 times.
Instead find a way to count each character once.
Two ways to do this:
make a list of each possible character (a-z) and iterate through the list counting each one.
or
Utilize python's dictionary type and check to see if a character already exists in the dictionary.
You can also just add a list for characters that have already been counted, and check that the character isn't in the list (This will be the easiest to implement in your code without a major rewrite.)

thanks, i thought about checking each character but thought that it was a bit of a cheat since it really should only look at the characters available.  putting the characters in a list and checking against them was what i thought would be a good method, but i'm not sure what the best method is to record the number of times the character is matched

---

### Post by WillFerrellLuva on 2010-03-24
A little late, as i just got back into programming, but here is my solution in c++

```

#include <fstream>
#include <iostream>
#include <string>
using namespace std;


int main()

{
	fstream in;
	char char_temp = ' ';
	int int_temp = 0;
	int int_count[10] = {0}; 
	int char_count[26] = {0};
	string contents = "";
	
	in.open("test");
	if(in.good())
	{
		while(!in.eof())
		{
			in>>char_temp;
			if(!in.eof())
			{
				contents += char_temp;
			}
		}
	}
	else 
	{
		cout << "Error opening file." << endl;
	}
	in.close();
	
	//0-9 (48 - 57 ascii) and a-z (97 - 122 ascii)lowercase
	for(unsigned int i = 0; i < contents.size(); i++)
	{
		if(static_cast<int>(contents[i]) >= 48 && static_cast<int>(contents[i]) <= 57) //is a number
		{
			int_temp = static_cast<int>(contents[i]) - 48;
			int_count[int_temp]++;
		}
		else if(static_cast<int>(contents[i]) >= 97 && static_cast<int>(contents[i]) <= 122) //is a letter
		{
			int_temp = static_cast<int>(contents[i]) - 97;
			char_count[int_temp]++;
		}
	}
	
	//calculate sum of numbers
	int sum = 0;
	for(int i = 0; i < 10; i++)
	{
		sum += (int_count[i] * i);
	}
	cout << "Sum = " << sum << endl;
	
	//print number of letters
	for(int i = 0; i < 26; i++)
	{
		if(char_count[i] > 0)
		{
			cout << static_cast<char>(i + 97) << " = " << char_count[i] << endl;
		} 
	}
	

	return 0;

}

```

---

### Post by ghostdog74 on 2010-07-23
```

$ cat file
5
a
n
7
4
n
6
1
0
y
w
a

$ awk '!/[0-9]/{_[$1]++}/[0-9]/{s+=$1}END{for(i in _) print i,_[i] ;print s}' file
w 1
y 1
n 2
a 2
23


```

---

### Post by StephenF on 2010-07-24
> **ghostdog74 said:**
> awk:D

challenge9.py
```

#! /usr/bin/env python

import sys
from collections import defaultdict

def main():
    log = defaultdict(int)

    while 1:
        c = sys.stdin.read(1)
        if not c:
            break
        if c.isdigit():
            log["Sum"] += int(c)
        elif c.islower():
            log[c] += 1
        
    print "Sum = %d" % log.pop("Sum", 0)
    for item in sorted(log.items()):
        print "%s = %d" % item
        
if __name__ == "__main__":
    main()

```

Usage (using test data from the OP):
```

$ cat infile | ./challenge9.py
Sum = 23
a = 2
n = 2
w = 1
y = 1

```

---

### Post by ghostdog74 on 2010-07-24
> **StephenF said:**
> :D

challenge9.py
```

#! /usr/bin/env python

import sys
from collections import defaultdict

def main():
    log = defaultdict(int)

    while 1:
        c = sys.stdin.read(1)
        if not c:
            break
        if c.isdigit():
            log["Sum"] += int(c)
        elif c.islower():
            log[c] += 1
        
    print "Sum = %d" % log.pop("Sum", 0)
    for item in sorted(log.items()):
        print "%s = %d" % item
        
if __name__ == "__main__":
    main()

```

Usage (using test data from the OP):
```

$ cat infile | ./challenge9.py
Sum = 23
a = 2
n = 2
w = 1
y = 1

```

ok, so i saw you quoted me. What's the thing you are trying to say to me?

---

### Post by StephenF on 2010-07-24
Just the smiley face. I mean, that's an elegant solution.

---

### Post by Vox754 on 2010-07-24
> **ghostdog74 said:**
> ok, so i saw you quoted me. What's the thing you are trying to say to me?

Yey! ghostdog is back!

Since you left, geirha took your job as the resident bash/sed/awk master.

'Tis gonna be great!

By the way, the Bash Absolute Beginner's Guide (ABS) is not recommended, it's full of errors.

See this thread [Good BASH Tutorial](http://ubuntuforums.org/showthread.php?t=1507547).

---

### Post by ghostdog74 on 2010-07-24
> **StephenF said:**
> Just the smiley face. I mean, that's an elegant solution.
i see. I just saw the word "awk" only and nothing else and was wondering if you have left out something.

---

### Post by ghostdog74 on 2010-07-24
> **Vox754 said:**
> 
By the way, the Bash Absolute Beginner's Guide (ABS) is not recommended, it's full of errors.

yes, been MIA and didn't take the time to change it.

---

### Post by thepopasmurf on 2010-08-04
This is  a bit late but I have only decided to learn Ocaml in the last week.

```
(* If running in interpreter,   #load "str.cma"   must be called first *)

let file = Sys.argv.(1);;
let ic = open_in file;;

exception Insert_error;;

(* itemCounter Data type for keeping track
   of how many times an element is encountered*)
type 'a itemCounter = Null
	|Cons of ( 'a * int ) * 'a itemCounter;;
								
let rec isMember x count =
	match count with
	Null -> false;
	|Cons((a,b), c )-> x=a || isMember x c;;
	
let rec addItemCounter item holder =
	let rec insert x count =
		match count with 
			Null -> raise Insert_error
			| Cons((a,b), c) -> if x=a then Cons((a,b+1),c)
			else Cons((a,b), insert x c)
	in
		if isMember item holder then insert item holder
		else Cons((item, 1), holder);;

let rec print_itemCounter counter =
	match counter with
	Null -> ();
	|Cons((a,b),c) -> Printf.printf "%c -> %d\n" a b;
								print_itemCounter c;;

(* ---------------- *)

let rec counter in_channel intList charCounter =
	try begin
	let word = input_line in_channel in
	let re = Str.regexp "[0-9]" in
	if Str.string_match re word 0 then
		counter in_channel ((int_of_char (String.get word 0)::intList)) charCounter
	else
		counter in_channel intList (addItemCounter (String.get word 0) charCounter)
	end
	with End_of_file ->
		close_in in_channel;
		print_int (List.fold_left (+) 0 intList);
		print_string "\n";
		print_itemCounter charCounter;;
		
counter ic [] Null;;

```

It looks quite long. I decided to make my own datatype to count the characters. Sorry if the code looks messy. The tabs didn't paste well.
My solution uses regular expressions because I though it was a bit inelegant to check the characters using exceptions.

If you want to compile it you need to include the "str.cma" file for the regular expressions.
 To compile follow this form
```
$ ocamlc -o output str.cma challenge9.ml
```
to execute follow this form
```
./output textfile 
```

---

### Post by CuracaoThe on 2011-07-16
Written in Ruby

[PHP]
def read_from_file(path)
  lines = IO.readlines(path) {|l| l.chomp}
end

lines = read_from_file("collector.txt")
numbers_sum = 0
letters = {}

lines.each do |line|
  if line =~ /^[a-z]$/
    key = line.chomp.to_sym
    letters[key] = 0 unless letters.keys.include?(key)
    letters[key] += 1
  end
  numbers_sum += line.to_i
end

puts "Sum = #{numbers_sum}"
letters.each do |k, v|
  puts "#{k} = #{v}"
end

[/PHP]

Source file:
[PHP]
~% cat collector.txt 
a
a
a
c
b
b
3
5
0
d
a
c
d
1
1
0
0
d
c
[/PHP]

Result of executing:
[PHP]
~% ruby collector.rb
Sum = 10
a = 4
c = 3
b = 2
d = 3
[/PHP]

---

