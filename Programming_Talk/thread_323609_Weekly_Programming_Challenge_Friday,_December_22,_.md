---
title: "Weekly Programming Challenge: Friday, December 22, 2006"
date: 2006-12-22
forum: Programming Talk
---

### Post by jayemef on 2006-12-22
Okay, this weeks problem will be a 2-parter, mostly because I'm worried that the first segment will be overly easy. So feel free to skip part 1 if you want to just jump into part 2, but I would suggest doing both.

**Part 1: The Obligatory Palindrome**
A palindrome is a word, phrase, number or line of verse which reads the same forwards or backwards, as in 'Able was I ere I saw Elba.' Part 1 of this weeks problem is to decide whether a given input is a palindrome or not. Returning a simple Yes/No, True/False, 1/0, etc. should suffice. Whitespace, case, and punctuation may all be ignored when determining whether a phrase is a palindrome or not.

**Part 2: The Next Smallest (integer) Palindrome**
Part 2 is slightly more complex, and is limited to integers. The goal here is, given an integer, determine what the next smallest integer palindrome would be that is greater than the input. For example, if given the integer 812, your program should return 818 (which is the smallest possible palindrome that is greater than the input).


Enjoy!

---

### Post by Tomosaur on 2006-12-22
818 is bigger than 812...

---

### Post by lnostdal on 2006-12-22
> **jayemef said:**
> Okay, this weeks problem will be a 2-parter, mostly because I'm worried that the first segment will be overly easy. So feel free to skip part 1 if you want to just jump into part 2, but I would suggest doing both.

**Part 1: The Obligatory Palindrome**
A palindrome is a word, phrase, number or line of verse which reads the same forwards or backwards, as in 'Able was I ere I saw Elba.' Part 1 of this weeks problem is to decide whether a given input is a palindrome or not. Returning a simple Yes/No, True/False, 1/0, etc. should suffice.


```

(defun palindrome-p (word)
  (string-equal word (reverse word)))

(palindrome-p "Able was I ere I saw Elba") => t
(palindrome-p "abba") => t
(palindrome-p "lars") => nil

```

> **jayemef said:**
> 
**Part 2: The Next Smallest (integer) Palindrome**
Part 2 is slightly more complex, and is limited to integers. The goal here is, given an integer, determine what the next smallest integer palindrome would be. For example, if given the integer 812, your program should return 818.


ok .. after some explaining below .. here:

```

;; We reuse function from part 1.
(defun palindrome-p (word)
  (string-equal word (reverse word)))


(defun next-integer-palindrome (i)
  (loop
     (incf i)
     (when (palindrome-p (princ-to-string i))
       (return i))))


#|
Some examples:
cl-user> (next-integer-palindrome 812)
818
cl-user> (next-integer-palindrome 818)
828
cl-user> (next-integer-palindrome 1)
2
|#

```

---

### Post by meng on 2006-12-22
> **Tomosaur said:**
> 818 is bigger than 812...
The smallest integer that is larger than the input.

Point of clarification, with problem 1, do spaces and punctuation count? Clearly case does not. I vote they should not.

---

### Post by dwblas on 2006-12-22
> Do geese see God?Is this a legitimate one to test for as well, or does that make it too difficult?  Good choice by the way.  It's a Goldilocks, not too hard, not too soft, but just right.

---

### Post by jayemef on 2006-12-22
Meng is correct -- the next smallest integer would be the smallest valid integer-palindrome greater than the input. So for an input of 815, 816 is NOT a palindrome, 817 is NOT a palindrome, 818 IS a palindrome -- display it. If the input were 818 to begin with, you would still need to find the next smallest one that is greater than 818.

As to valid characters, punctuation, whitespace, and case can all be ignored.

---

### Post by Tomosaur on 2006-12-22
Yeah sorry, dunno why I didn't catch that. Not to worry, all done :)

Done in Java:

Part 1:
```

class pal{

	public static void main(String[] args){
		int left = 0;
		int right = (args[0].length() - 1);
		boolean palindrome = true;
		args[0] = args[0].toLowerCase();
		while(palindrome && left < right){
			if(args[0].charAt(left) == args[0].charAt(right)){
				left++;
				right--;
			}
			else{
				palindrome = false;
			}
		}
		if(palindrome){
			System.out.println("Palindrome");
		}
		else{
			System.out.println("Not a palindrome");
		}
	}
}

```

Part 2:
```

import java.util.*;

class palint{
	private static Scanner input = new Scanner(System.in);

	public static void main(String[] args){
		System.out.println("Please input an integer");
		int inp = input.nextInt();
		inp++;
		checkPal(inp);
	}

	private static void checkPal(int i){
		String i_s = Integer.toString(i);
		int left = 0;
		int right = (i_s.length() - 1);
		boolean palindrome = true;
		while(palindrome && left < right){
			if(i_s.charAt(left) == i_s.charAt(right)){
				left++;
				right--;
			}
			else{
				palindrome = false;
			}
		}
		if(palindrome){
			System.out.println("Next palindrome int = " + i + ".");
		}
		else{
			i++;
			checkPal(i);
		}
	}
}

```

:)

---

### Post by Verminox on 2006-12-22
> **meng said:**
> The smallest integer that is larger than the input.

Point of clarification, with problem 1, do spaces and punctuation count? Clearly case does not. I vote they should not.

Won't be fun if it is punctuation/space sensitive.... Palindromes are usually symmetrized by characters, not by spaces, punctuations, or cases.

Of course, the OP has the right to make the rules but it would be better if it was only character symmetry.


Edit: Oops too late... Jaymef already posted above... so cool


Edit 2: Are single digits considered palindromes? eg. is "5" a palindrome as it is read the same forward and backward...

And... what is this competition going to be based on? speed of execution? lines of code? algorithms used? external libraries? because this is really simple and almost everyone will make similar looking codes in different languages....

---

### Post by dwblas on 2006-12-22
Also, if 812 is the input number, then 818 is the next palindrome, but
if 819 is the input, 828 is the next palindrome.

---

### Post by jayemef on 2006-12-22
> **Verminox said:**
> Edit 2: Are single digits considered palindromes? eg. is "5" a palindrome as it is read the same forward and backward...
Think you answered your own question there, but yes, single characters are palindromes.

> **Verminox said:**
> And... what is this competition going to be based on? speed of execution? lines of code? algorithms used? external libraries? because this is really simple and almost everyone will make similar looking codes in different languages....
Same as usual really. I look at these more as problem exercises than competitions, but any "winner" would stand out from the others as a really nice solution. Could be speed, could be elegance, could be any number of things. If you want to include timings of your output, go right ahead. But it's really hard to get anything accurate out of that, particularly when using I/O, as languages vary a lot on speed of I/O.

Because this problem is fairly easy, it lends itself to creative solutions. It could also utilize solutions from previous challenges, namely the text reversing.

> **dwblas said:**
> Also, if 812 is the input number, then 818 is the next palindrome, but
if 819 is the input, 828 is the next palindrome.
Won't fight you there... but what's your point? Are you just clarifying the problem?

---

### Post by maddog39 on 2006-12-22
The original post says:
> Returning a simple Yes/No, True/False, 1/0, etc. should suffice. **Whitespace, case, and punctuation may all be ignored when determining whether a phrase is a palindrome or not.**

I am going to attempt this in PHP (part 1) now and submit it when it works. :P

---

### Post by Verminox on 2006-12-22
Part 1 was very easy in C++.

```
#include <cstdlib>
#include <iostream>
#include <cstring>
using namespace std;

// Check whether an arbitary string is a palingdrome
bool isStringPalindrome(string str){
    int size = str.size();
    // i is the left iterator, j is the right iterator
    for( int i = 0, j = size-1 ; i < size, j > 0; i++, j-- ){        
        // Keep moving left till we find an alphanumeric char
        while( isalnum(str[i]) == 0 ){
            i++;
        }        
        // Keep moving right till we find an alphanumeric char
        while( isalnum(str[j]) == 0 ){
            j--;
        }        
        // If the str[i] is to the right of str[j], it means we have finished the iteration
        if( i > j ){
            return true;
        }        
        // Now check if the two alphanumeric chars are equivalent, break if not
        if( tolower( str[i] ) != tolower( str[j] ) ){
            return false;
        }       
    }
}

int main(int argc, char *argv[])
{
    string str; // Input
    cout << "Enter String: ";
    getline( cin, str );
    if( isStringPalindrome( str ) ){
        cout << "True" << endl;
    } else {
        cout << "False" << endl;
    }    
    return 0;
}
```





As regards Part 2, I think if anyone just takes the input, keeps incrementing the integer in a loop until it is a palindrome, I think that is just sad.

I guess there are more mathematical algorithms for this, but here is mine:

```
~Removed~ (Bad Algorithm)
```


Notice the "Tricky Part" section. Basically I'm using the fact that if your right digit is greater than the left digit, the next palindrome will be obtained by increasing the left digit by one, bringing the right digit to it, and filling up the middle with 0s.

eg for 4235237, since the in the first pair, 4 < 7, so you get: 5000005
or for 851988, in the second pair 5 < 8, so you get: 860068.

EDIT: OK THIS ALGORITHM IS A BIT WRONG... I'll FIX IT LATER

---

### Post by jayemef on 2006-12-22
Here's my own initial stab at this one, written in PHP:
[php]
<?php
function is_palindrome($text) {
    // Strip out any non-alphanumeric characters, and then lowercase.
    $text = strtolower(preg_replace('/[^A-Za-z0-9]/', '', $text));
    
    // Is the text the same in reverse?
    return ($text == strrev($text));
}

function next_palindrome($number) {
    $next_palindrome = $number + 1;
    
    // Increment until a palindrome is found.
    while (!is_palindrome($next_palindrome)) {
        $next_palindrome++;
    }
    
    return $next_palindrome;
}

$phrase_tests = array(
    'Do geese see god?',
    'Doc, note: I dissent. A fast never prevents a fatness. I diet on cod.',
    'Stressed? No Tips? Spit on Desserts.',
    'Borat to go, OK? Oy! Yokoo gotta rob.',
    'Anal sex at noon taxes Lana.',
    'Was it a car or a cat I saw?',
    'Tango, O Gnat!',
    '"Do nine men interpret?" "Nine men," I nod.',
    'Nine kats is taken in.',
    'I, madam, I made radio. So I dared! Am I mad? Am I?',
    'Now, sir, a war is never even -- sir, a war is won!',
    'Not a tub, but a ton.',
    'Butt raft fart tub.',
    'Mr. Owl ate my metal worm.',
    'Kay, a red nude, peeped under a yak.',
    'No evil I did I live on.',
    'Naomi, sex at noon taxes, I moan.',
    'Karma never on, nor even a Mr. Ak.',
    'Not a palindrome!'
);

$numbers = array(23, 456, 812, 34, 2, 555, 123456789);

foreach ($phrase_tests as $test) {
    if (is_palindrome($test)) {
        echo "TRUE  - The phrase '$test' is a palindrome!\n";
    }
    else {
        echo "FALSE - The phrase '$test' is NOT palindrome!\n";
    }
}

foreach ($numbers as $number) {
    echo "The next palindrome after $number is " . next_palindrome($number) . "\n";
}
?>
[/php]

And the output:
> 
TRUE  - The phrase 'Do geese see god?' is a palindrome!
TRUE  - The phrase 'Doc, note: I dissent. A fast never prevents a fatness. I diet on cod.' is a palindrome!
TRUE  - The phrase 'Stressed? No Tips? Spit on Desserts.' is a palindrome!
TRUE  - The phrase 'Borat to go, OK? Oy! Yokoo gotta rob.' is a palindrome!
TRUE  - The phrase 'Anal sex at noon taxes Lana.' is a palindrome!
TRUE  - The phrase 'Was it a car or a cat I saw?' is a palindrome!
TRUE  - The phrase 'Tango, O Gnat!' is a palindrome!
TRUE  - The phrase '"Do nine men interpret?" "Nine men," I nod.' is a palindrome!
TRUE  - The phrase 'Nine kats is taken in.' is a palindrome!
TRUE  - The phrase 'I, madam, I made radio. So I dared! Am I mad? Am I?' is a palindrome!
TRUE  - The phrase 'Now, sir, a war is never even -- sir, a war is won!' is a palindrome!
TRUE  - The phrase 'Not a tub, but a ton.' is a palindrome!
TRUE  - The phrase 'Butt raft fart tub.' is a palindrome!
TRUE  - The phrase 'Mr. Owl ate my metal worm.' is a palindrome!
TRUE  - The phrase 'Kay, a red nude, peeped under a yak.' is a palindrome!
TRUE  - The phrase 'No evil I did I live on.' is a palindrome!
TRUE  - The phrase 'Naomi, sex at noon taxes, I moan.' is a palindrome!
TRUE  - The phrase 'Karma never on, nor even a Mr. Ak.' is a palindrome!
FALSE - The phrase 'Not a palindrome!' is NOT palindrome!
The next palindrome after 23 is 33
The next palindrome after 456 is 464
The next palindrome after 812 is 818
The next palindrome after 34 is 44
The next palindrome after 2 is 3
The next palindrome after 555 is 565
The next palindrome after 123456789 is 123464321


Some comments: I like this solution, as it's really easy to follow. However, I'm guessing that there must be a more efficient solution, as the replace, tolower, and reverse operations are all fairly costly (at least linear). Also, I don't really like the linear search in the next_palindrome function. It's very easy to implement, as well as easy to tell that it is correct. But I'm sure there is a much faster route to finding them.

---

### Post by Verminox on 2006-12-22
JMF: See my solution above to see how to fix the linear search in your next_palindrome function (read the last lines of my post).

The C++ code may look larger, but it's mostly because of comments, whitespace, and using lower level character manipulation rather than string manipulation, which makes it much faster.

Regular expressions will really kill the speed.

---

### Post by jayemef on 2006-12-22
@Verminox: Question - is isalnum() coming from a library, or did you write it?


> **Verminox said:**
> Notice the "Tricky Part" section. Basically I'm using the fact that if your right digit is greater than the left digit, the next palindrome will be obtained by increasing the left digit by one, bringing the right digit to it, and filling up the middle with 0s.

eg for 4235237, since the in the first pair, 4 < 7, so you get: 5000005
or for 851988, in the second pair 5 < 8, so you get: 860068.


Let's see who can find a faster one :p

Good idea... but it's not right. The next smallest palindrome after 4235237 would be 4235324. The strategy is sound though.

---

### Post by dwblas on 2006-12-22
Here is a solution in Python.  The number problem uses brute force.  I'll add a more creative solution later, but the brute force solution should be done by someone.  It has two advantages [1] it will test every number, [2] you can use it to find a solution to compare to a more creative approach to see if it also finds the correct palindrome.```
#!/usr/bin/python
import string

def TestString( string_in ) :
   found = 0
   test_string = string.lower( string.strip(string_in) )
   test_string = test_string.replace( " ", "" )                ## remove spaces
   test_len = len(test_string) /2
   reverse_chars = list(test_string[-test_len:])
   reverse_chars.reverse()
   string_end = "".join(reverse_chars)
   if test_string.startswith( string_end ) :
      found = 1
   return found

def BruteForce( number_in ) :
   found = 0
   num = int(number_in)
   stop_len = len(str(num)) + 1
   while len(str(num)) < stop_len :
      num += 1
      found = TestString( str(num) )
      if found :
         return found, num
   return found

##=========================================================================
if __name__ == "__main__" :
   test_this = "Do geese see God"
   found = TestString( test_this )
   if found :
      print "Palindrome Found for", test_this                     

   test_this = 819
   found, num = BruteForce( test_this )
   if found :
      print "Palindrome Found for", test_this, "is", num

```

---

### Post by Verminox on 2006-12-22
> **jayemef said:**
> @Verminox: Question - is isalnum() coming from a library, or did you write it?




Good idea... but it's not right. The next smallest palindrome after 4235237 would be 4235324. The strategy is sound though.


Damn... a fundamental flaw in my algorithm... well I must have miscalculated what I was trying.... ermm.... I'll try fixing it tomorow, really late here.

Bwt: isalnum() is in the standard C library, nothing great.

Edit:
Oh, and I just realized the flaw in my algorithm.

If str[i] < str[j], then str[j] should be shifted down to the same as str[i] and str[j-1] should be moved up by one, not str[i]....

I'll fix it tomorow very sleepy... I have till next Friday right? :p

---

### Post by Tomosaur on 2006-12-22
> **Verminox said:**
> Part 1 was very easy in C++.
Notice the "Tricky Part" section. Basically I'm using the fact that if your right digit is greater than the left digit, the next palindrome will be obtained by increasing the left digit by one, bringing the right digit to it, and filling up the middle with 0s.

eg for 4235237, since the in the first pair, 4 < 7, so you get: 5000005
or for 851988, in the second pair 5 < 8, so you get: 860068.


Let's see who can find a faster one :p

That's all well and good, but the next smallest integer which is a palindrome after 4235237 is 4235324.

I also don't see how it's 'sad' to just increase the integer in a loop. It's both the fastest way to code the program, and is also the fastest in terms of execution, unless you know of an actual mathematical formula to solve the problem.

---

### Post by Verminox on 2006-12-22
As posted above, the algorithm was posted a bit wrong... I'll fix it and repost again later....


And no a loop is not the fastest way of doing it.... iterating through hundreds or thousands of numbers, converting to a string each time and checking to see if is a palindrome is much slower, than just checking pair by pair and editing accordingly.

---

### Post by Tomosaur on 2006-12-22
Good point, hadn't thought of that :P

EDIT: Actually...
Forgive me if I'm wrong, but surely that's all you're doing behind the scenes anyway? You can't have 'pairs' from a single integer - it's not stored in memory like that - so in essence, the only way to extract two digits from an integer is to convert the integer to a string, extract whichever digits you want, convert each back to integers, then compare them, which is actually slower than just converting the whole thing into a string and then comparing the characters?

Unless I'm misunderstanding what you meant by pairs, I can't remember what your code looked like :S

---

### Post by Wybiral on 2006-12-22
Ok, in C++, the first part...

```

#include <string>
#include <iostream>

using namespace std;

string isPalindrome(string input){
	for(int i=0; i<input.length()/2; i++)
		{if(input[i] != input[input.length()-i]){return "false\n";}}
	return "true\n";
}

int main(int argc, char* argv[]){
	cout << isPalindrome(argv[1]);
	return 0;
}

```

And the second part...

```

#include <string>
#include <iostream>
#include <sstream>

using namespace std;

bool isPalindrome(string input){
	for(int i=0; i<input.length()/2; i++)
		{if(input[i] != input[input.length()-i]){return false;}}
	return true;
}

string intToStr(int nVal){
	ostringstream out;
	out << nVal;
	return out.str();
}

int nextPalInteger(int nVal){
	bool isPal = false;
	for (nVal=nVal; isPal == false; nVal++)
		{isPal = isPalindrome(intToStr(nVal));}
	return nVal-1;
}

int main(int argc, char* argv[]){
	int nVal = atoi(argv[1]);
	cout << nextPalInteger(nVal);
	return 0;
}

```

Either of these can be compiled using "g++ myProgram.cpp" and then executed using "./a.out argument".

The first one takes in any string as an argument and returns true/false whether or not it is a palindrome.

The second one takes in an integer value and returns the next valid palindrome.

This also shows how one can transfer a integer into a string with the "intToStr" function.

---

### Post by dwblas on 2006-12-22
> And no a loop is not the fastest way of doing itThose of us who have the paranoid view point that comes from real world failures (no slam intended to anyone, just an explanation), start out with a way to prove whether we are getting the correct results or not.  Incrementing by one produces reliable output that can be used to check other solutions.  Perhaps it is overkill in this situation, and perhaps the computer will find something that you wouldn't.  My personal preference is to let the computer do the checking.

---

### Post by slash2314 on 2006-12-22
```

def palindrome(word):
        word =''.join([x.lower() for x in word if x.isalnum()])
        reverse_word = ''.join([a for a in word[::-1]])
        if word == reverse_word:
                return True
        return False
def small_integer_palindrome(number):
        origional_number = number
        number+=1
        while True:
                if palindrome(str(number))==True:
                        return 'The next number that is a palindrome after '+str(origional_number)+' is '+str(number)
                number+=1
choice = input("Test palindrome 1 or Test small integer palindrome 2: ")
if choice == 1:
        word_string = str(raw_input("Enter a sentence to test: "))
        print palindrome(word_string)
elif choice == 2:
        number = input("Enter a number to test: ")
        print small_integer_palindrome(number)

```

---

### Post by maddog39 on 2006-12-22
Okay I finally finished my submissions:
 
My contribution in PHP CLI:
[php]
#!/usr/bin/php

<?php
function get_time() {
    $current_time = microtime();
    $current_time = explode(" ", $current_time);
    $current_time = $current_time[1] + $current_time[0];
    return $current_time;
}

$start_time = get_time();

if (($argc >= 1) && (isset($argv[1]))) {
    if ($argv[1] == "-h") {
        echo "usage: " . $argv[0] . " <string>\n";
    } elseif (count(explode(" ", $argv[1])) > 1) {
        if ($argv[1] == strrev($argv[1])) {
            echo "True\n";
        } else {
            echo "False\n";
        }
    } else {
        echo "Use " . $argv[0] . " -h for more information.\n";
    }
} else {
    echo "Use " . $argv[0] . " -h for more information.\n";
}

$stop_time = get_time();
$total_time = round($stop_time-$start_time, 5);
echo "Execution Time: " . $total_time . "s\n\n";
?>
[/php]Then my attempt in C++, you may need to tinker with it to work, im not that good yet with C++:
```

#include <ctype.h>
#include <iostream>

int main() {
    int left = 0;
    int right = length - 1;
    int length = 0;
    char phrase[512], tempchar;
    
    std::cout<<"Enter a phrase: ";
    
    while (std::cin.get(phrase)) {
        if (length > 510) {
            std::cout<<"Your phrase was too long."<<std::endl;
            return -1;
        }
        phrase[length++] = tempchar;
    }
    
    while (left < right) {
        if (!isalpha(phrase[left])) {
            left += 1;
        } else if (!isalpha(phrase[right])) {
            right -= 1;
        } else if ((tolower(phrase[left++])) == (tolower(phrase[right--]))) {
            if (true) {
                std::cout<<"True"<<std::endl;
            } else {
                std::cout<<"False"<<std::endl;
            }
        }
    }
    
    return 0;
}

```

---

### Post by jayemef on 2006-12-22
Don't forget that whitespace, punctuation, and character case can be ignored.

---

### Post by cgrebeld on 2006-12-22
Notice the lazy evaluation of the infinite list... Haskell is cool! =)

```


import Char (toLower,isAlphaNum)
checkPalin = do
    userIn <- getLine 
    putStr $ show $ checkPalin (map toLower $ filter (isAlphaNum) userIn)
    where 
          checkPalin cand = cand == (reverse cand)

nextPalin = do
    userIn <- getLine 
    putStr $ show $ head $ dropWhile (not.isPal) [((read userIn :: Int) + 1)..]
    where
        isPal num = (show num) == (reverse (show num))

```

---

### Post by sphinx on 2006-12-22
To those of you who beleive the choice of language is more important to speed than the algorithmn itself, who wants to pit their speedy non-java implementation against mine in slow 'ol java?

Stay tuned for my implementation, I'll do some benchmarks but you'll probably have to benchmark my entry yourself if I dont know how to compile/run your implementation.

This is a chalenge in raw speed. I think I've come up with a great idea for the second part.;)

---

### Post by sphinx on 2006-12-22
First up here is my implementation of the problems:
```

public class PalindromeTool {
    private static String acceptableChars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";

    public static boolean isPalindrome(String string) {
        if(string==null) return false;

        String str = cleanString(string.toLowerCase());
        int strlen = str.length();

        if(strlen==0) return false; // is a empty string a Palindrome or not?

        String firstHalf, secondHalf;
        if(strlen%2==0) { //if even string length
            firstHalf = str.substring(0,strlen/2);
        } else { // if odd string length
            firstHalf = str.substring(0,(strlen/2)+1);
        }
        StringBuffer temp = new StringBuffer(str.substring(strlen/2,strlen));
        secondHalf = temp.reverse().toString();

        return (firstHalf.equals(secondHalf));
    }

    /**
     * This cleans all non a-z|A-Z chars out of the string.
     * @param str
     * @return a string containing only characters between a-z or A-Z
     */
    public static String cleanString(String str) {
        StringBuffer buf = new StringBuffer(str.length());
        char[] chars = str.toCharArray();
        for(int i=0;i<chars.length;i++) {
            if(acceptableChars.indexOf(chars[i])>=0) {
                buf.append(chars[i]);
            }
        }
        return buf.toString();
    }

    public static int getNextPalindromeInt(int seed) {
        int num = seed;
        while(true) {
            String i_s = Integer.toString(num);
            int left = 0;
            int right = (i_s.length() - 1);
            boolean palindrome = true;
            while(palindrome && left < right){
                if(i_s.charAt(left) == i_s.charAt(right)){
                    left++;
                    right--;
                }
                else{
                    palindrome = false;
                }
            }
            if(palindrome){
                return num;
            }
            else{
                num++;
            }
        }
    }

    public static int getNextPalindromeIntFast(int seed) {
        int num = seed+1;
        //split the number
        String numStr = Integer.toString(num);
        int strlen = numStr.length();
        StringBuffer leftStrBuf, rightStrBuf;
        int leftNum, rightNum;
        int midpoint;
        if(strlen%2==0) {
            midpoint = strlen/2;
        } else {
            midpoint = (strlen/2)+1;
        }
        leftStrBuf = new StringBuffer(numStr.substring(0,midpoint));
        rightStrBuf = new StringBuffer(numStr.substring(midpoint,strlen));
        leftNum = Integer.parseInt(leftStrBuf.toString());
        rightNum = Integer.parseInt(rightStrBuf.toString());
        if(rightNum>reverseNum(leftNum)) {
            leftNum++;
            leftStrBuf = new StringBuffer(Integer.toString(leftNum));
        }
        StringBuffer retNum = new StringBuffer();
        retNum.append(leftStrBuf);
        retNum.append(leftStrBuf.reverse());
        return Integer.parseInt(retNum.toString());
    }

    public static int reverseNum(int num) {
        return Integer.parseInt(new StringBuffer(Integer.toString(num)).reverse().toString());
    }
}

```

Credit given to Tomosaur for the implementation of getNextPalindromeInt I stole it almost vertabatim (changed only a little to remove recursion).

My version getNextPalindromeIntFast has next to no looping involved, it should make it a hell of a lot faster the larger the number as its better then 0(n) in performance, actually its not far off 0(1). I've yet to benchmark it though as somethings come up and I can't spend any more time on it right now. Oh, and to help out below is the Main class I used to develop/test.

```

public class Main {
    static String tests[] = {"Able was I ere I saw Elba.",
                             "Hello world.",
                             "Do geese see God?",
                             "abcdefghijklmnopqrstuvwxyz",
                             "123454321",
                             "a"};

    public static void main(String[] args) {
        for(int i=0;i<tests.length;i++) {
            System.out.print(tests[i]);
            System.out.print(": ");
            System.out.println(PalindromeTool.isPalindrome(tests[i].toLowerCase()));
        }
        int num = 1231562349;
        System.out.println(num);
        System.out.println("next in is       : "+PalindromeTool.getNextPalindromeInt(num));
        System.out.println("next in is (fast): "+PalindromeTool.getNextPalindromeIntFast(num));
        System.out.println(PalindromeTool.reverseNum(12345));
    }
}

```

---

### Post by jayemef on 2006-12-22
@sphinx: Nice job -- I've got a couple of quick comments though. Firstly, since integers can be palindromes as well, shouldn't 0-9 be included in your list of acceptable characters? Then secondly, you don't need to check whether your phrase has an odd or even number of characters. Simple integer division should suffice, as anytime you have an odd number of characters, the middle character is guaranteed to be the same as the middle character of the reversed string. So for example, given strings of length 4 and 5, in both cases you only need to compare substrings of length 2.

---

### Post by Wybiral on 2006-12-22
> Then secondly, you don't need to check whether your phrase has an odd or even number of characters. Simple integer division should suffice, as anytime you have an odd number of characters, the middle character is guaranteed to be the same as the middle character of the reversed string. So for example, given strings of length 4 and 5, in both cases you only need to compare substrings of length 2.

That's how my C++ one works, it just iterates over half of the string, completely ignoring the middle character. If (character[i] = character[string/2 - i]) for characters (1 to string/2) then it has to be a palindrome.

I guess another way would be to reverse half of the string and compare that with the other half (excluding the middle man)... kind of like this:

```

#include <string>
#include <iostream>
#include <algorithm>

using namespace std;

string isPalindrome(string input){
	string a = input.substr(0, input.length()/2);
	string b = input.substr(input.length()-input.length()/2, input.length()-1);
	reverse(b.begin(), b.end());
	if (a == b) {return "true\n";}
	else {return "false\n";}
}

int main(int argc, char* argv[]){
	cout << isPalindrome(argv[1]);
	return 0;
}

```

It could be compressed a bit more, and it may not even be more efficient than my other one, but none-the-less... It's another way to do it.

As a matter of fact, you can just reverse the entire string and compare that with the normal one... Why didn't I think of that before?

```

#include <string>
#include <iostream>
#include <algorithm>

using namespace std;

string isPalindrome(string input){
	string b = input;
	reverse(b.begin(), b.end());
	if (input == b) {return "true\n";}
	else {return "false\n";}
}

int main(int argc, char* argv[]){
	cout << isPalindrome(argv[1]);
	return 0;
}

```

---

### Post by jayemef on 2006-12-23
Just for fun: Return all palindromes in dictionary (note: only tested this in Solaris):
```

$ perl -lne 'print if $_ eq reverse' /usr/dict/words

```

---

### Post by Get_Ya_Wicked_On on 2006-12-23
Let's not forget about C!

```

#include <stdio.h>
#include <string.h>

#define TRUE 1
#define FALSE 0

main () {
  
  char string[30];
  int ispalindrome = TRUE; 
  int a,z;

  printf("Enter a word: ");
  scanf( "%s", &string);
  z = strlen(string) - 1;
  a = 0;

  /*Moves 'inward', checking each letter.*/
  
  while(a <= z && ispalindrome) {
    
  /*   if ( string[a] = '\n')   /*Puts spaces into consideration.
      { a++;
      continue; }

    if ( string[z] = '\n')      /*Nevermind... */

      { z--;
      continue; } */


     if(string[a] != string[z]) {
      ispalindrome = FALSE;
    } 
    a++;
    z--;
  }

  
  if(ispalindrome) {
    printf("%s is a palindrome!\n", string);
  }
  else {
    printf("Sorry, %s is not a palindrome.\n", string);
  } 
} 

```

edit: No regard for spaces...

---

### Post by dwblas on 2006-12-23
> perl -lne 'print if $_ eq reverse' /usr/dict/wordsYou have my vote for best solution (so far), even though it's for words only.

---

### Post by slavik on 2006-12-23
the string must be enclosed with double (or single) quotes to prevent the shell from breaking it up. This code does both in a single file.

```

#!/usr/bin/perl

#part 1
$string = $original = shift; #get the first argument
$string =~ s/\W//g; #replace all non alphanumeric chars with blanks/NULL
$string = lc $string; #make the string lower case for comparison
if ($string eq reverse $string) { print "$original is a palindrome.\n"; } #compare the string with it's reverse
else { print "$original is NOT a palindrome.\n"; }

#part 2
$tmp = $number = shift; $tmp++;
while ($tmp ne reverse $tmp) { $tmp++; } #'!=' for comparison would've worked, too
print "$tmp is the next lowest number after $number that is a palindrome\n";

```

The reason it works for numbers is because of reverse, which treats it's argument (if it's a single thing) as a string.

---

### Post by Verminox on 2006-12-23
> **Tomosaur said:**
> Good point, hadn't thought of that :P

EDIT: Actually...
Forgive me if I'm wrong, but surely that's all you're doing behind the scenes anyway? You can't have 'pairs' from a single integer - it's not stored in memory like that - so in essence, the only way to extract two digits from an integer is to convert the integer to a string, extract whichever digits you want, convert each back to integers, then compare them, which is actually slower than just converting the whole thing into a string and then comparing the characters?

Unless I'm misunderstanding what you meant by pairs, I can't remember what your code looked like :S


Consider a 6 digit number like "999000". Your script will iterate through 999 numbers (till "999999", each time converting an integer to string, doing a linear search for all 6 characters to check whether it is a palindrome, return a boolean, and then accordingly go to the next iteration or return the number if it is a palindrome.

On the other hand, my script will convert this to an integer just once. Check the 1st and 6th digit for equality, and adjust the 6th char to '9' (Note: I don't convert back to integer for checking, I merely compare the two ASCII characters, because they are just one byte and still in the same integral order). I do this 3 times and I'm done... convert back to integer for the return and that's it.

_________________________-



Alright, I fixed my algorithm, here we go:

```
#include <cstdlib>
#include <iostream>
#include <cstring>
using namespace std;

// Find the smallest palindrome integer greater than the given input
int NextPalindrome(unsigned int num){
    // Covnert integer to string
    char buffer[12];
    sprintf( buffer, "%d", num );    
    string str(buffer);
    int size = str.size();    
    
    // i is the left iterator and j is the right iterator
    for( int i = 0, j = size-1, k ; i < size, j > 0; i++, j-- ){
        // If the str[i] is to the right of str[j], it means we have finished the iteration
        if( i >= j ){
            break;
        }   
        // Now to do the changing
        if( str[i] == str[j] ){ 
            // Left and right chars are same, move on
            continue;
        } else if ( str[i] > str[j] ){
            // Left char is greater than right char, so increase the right char
            str[j] = str[i];
        } else {
            // Right char is greater than left char
            // This is the tricky part
            // Bring the right char down the left char,
            // and then change the next left char to the right one
            str[j] = str[i];
            k = j-1; // Next left char to the right one
            while( k != i ){
                if( str[k]!='9' ){                    
                    // Increase it
                    str[k]++; 
                    break;
                } else {
                    // Make it zero and continue with next left char
                    str[k] = '0';
                    k--;
                }
                if( k == i ){
                    // If we reached the left char, that means we need to go one power up
                    str[i]++;
                    str[j]++;
                }
            }
        }
    }            
    // Make it an integer and return
    int Palindrome = atoi( str.c_str() );
    return Palindrome;    
}

int main(int argc, char *argv[]){
    int num; // Input
    cout << "Enter Integer: ";
    cin >> num;
    cout << NextPalindrome( num ) << endl;
    return 0;
}
```


Once again, this code looks a lot longer and more messy than those quick PHP, Python, etc. ones but since this handles the integer characterwise, it will save a LOT of unncessary resources.

Hopefully non-C programmers too can understand the algorithm by looking at the code. Tell me if I made any mistakes again.

Tests:
```
5 => 5
112 => 121
68417 => 68486
456567 => 456654
999000 => 999999
123456789 => 123464321
```




Edit: For those of you who are still trying to make one, I got another algorithm but I'm too lazy to implement in my own code now.

Just convert the integer to a string, divide it into two strings by cutting it at the center (if it has odd number of chars, ignore the center one). Now, just make the right string the reversed version of the left one. Then if the new right one is lower than the original right one, increment the rightmost of the left string by one, and the leftmost of the right string. 

(eg.1) split "68417" to "68" and "17". Ignore the "4" for now, convert "17" to reverse of left string, that is "86". as 86 > 17, continue. Your answer is "68486".

(eg.2) split "123456" to "123" and "456", convert the right string to "321", but as 321 < 456, change both the "3"s to "4"s so you get "124421".

---

### Post by slavik on 2006-12-23
to justify the linear algorithm, it takes 1 secodns to come up with and for a purpose like a contest it is considered good enough.

At ACM contests, your program has at most 5 minutes to run. If your solution works, it should not take more than a minute to run. :)

---

### Post by Wybiral on 2006-12-23
> The goal here is, given an integer, determine what the next smallest integer palindrome would be that is greater than the input

Verminox, I tried your's with "123456" and got "123321" instead of "124421". It seems it's checking down instead of up. I don't mean to be a stick-in-the-mud, just thought maybe it's a bug or something.

---

### Post by slavik on 2006-12-23
I found Verminox' explanations to be a little unclear. I think my explanation is a bit clearer. :)

for '123456' (any even digit amount number), you split it into 2 parts, a and b:
```
$a_temp = $a = 123; $b = 456;
```

then, if the reverse of a is greater than b you assign b to be reverse of a.
```
if (reverse $a > $b) { $b = reverse $a; }
```

if not, increment a until its reverse is greater than b. and assign.
```
while (reverse $a_temp < $b) { $a_temp++; }
$b = reverse $a_temp;
```

append the two together and print the number out
```
print $a.$b."\n";
```

for odd digit amount numbers, you have to repeat the middle digit twice and remove a copy in the end, but the idea is the same. :)

---

### Post by Verminox on 2006-12-23
Slavik: That's the same thing what I said, but more clearer :D

Oh, and "if not, increment a until its reverse is greater than b. and assign." can be avoided by just incrementing the middle parts (that is the rightmost of $a and leftmost of $b).


Wybiral: Yes I think that loop I made was too confusing even for myself... let me catch the bug...

---

### Post by Verminox on 2006-12-23
Ahh the bug was indeed in the while() loop. Revised version:

```
#include <cstdlib>
#include <iostream>
#include <cstring>
using namespace std;

// Find the smallest palindrome integer greater than the given input
int NextPalindrome(unsigned int num){
    // Covnert integer to string
    char buffer[12];
    sprintf( buffer, "%d", num );
    
    string str(buffer);
    int size = str.size();
    
    
    // i is the left iterator and j is the right iterator
    for( int i = 0, j = size-1, k ; i < size, j > 0; i++, j-- ){
        // If the str[i] is to the right of str[j], it means we have finished the iteration
        if( i >= j ){
            break;
        }   
        // Now to do the changing
        if( str[i] == str[j] ){ 
            // Left and right chars are same, move on
            continue;
        } else if ( str[i] > str[j] ){
            // Left char is greater than right char, so increase the right char
            str[j] = str[i];
        } else {
            // Right char is greater than left char
            // This is the tricky part
            // Bring the right char down the left char,
            // and then change the next left char to the right one
            str[j] = str[i];
            k = j-1; // Next left char to the right one
            
            while( 1 ){
                if( k == i ){
                    // If we reached the left char, that means we need to go one power up
                    str[i]++;
                    str[j]++;
                    break;
                }
                if( str[k]!='9' ){                    
                    // Increase it
                    str[k]++; 
                    break;
                } else {
                    // Make it zero and continue with next left char
                    str[k] = '0';
                    k--;
                }
            }
        }
    }            
    // Make it an integer and return
    int Palindrome = atoi( str.c_str() );
    return Palindrome;    
}

int main(int argc, char *argv[])
{
    int num; // Input
    cout << "Enter Integer: ";
    cin >> num;
    cout << NextPalindrome( num ) << endl;
    return 0;
}

```



Now it "just works". The algorithm is still very ugly though... If i get some time tomorow I'll try the other idea (what Slavik posted)

---

### Post by ghostdog74 on 2006-12-23
```

#!/usr/bin/python
"""
Assumuption:
a) No punctuations
b) Conversion to lowercases.
"""
import re
def is_it_palindrome(a_string, anumber=None):
        a_string = re.sub("[^A-Za-z0-9]+", "", a_string).lower()
        if anumber is not None:
		while True:
			if a_string == a_string[::-1]:
				return a_string
			else:
				a_string = str(long(a_string) - 1)				
	else:
		return a_string == a_string[::-1]
	
palindrome = raw_input("Enter a palindrome:")
if (is_it_palindrome(palindrome)):
	print "%s is Palindrome. " % palindrome
else:
	print "%s is not Palindrome. " %palindrome
palindrome = raw_input("Enter a number palindrome:")
out = is_it_palindrome(palindrome,1)
print "Nearest palindrome: " , out


```

outpuT:
```

>python test.py
Enter a palindrome:sdfws
sdfws is not Palindrome.
Enter a number palindrome:1234
Nearest palindrome:  1221

```

---

### Post by dwblas on 2006-12-23
> Enter a number palindrome:1234
Nearest palindrome:  1221Not correct, it should be 1234 --> 1331 = greater than original number.  It seems we have all come to the same solution.  Divide the length by 2 (doesn't matter if the length is even or odd) and strip off the rightmost len/2
1234 --> 12
reverse and append 12-->1221
if less than original, add one to left most
12 --> 13
repeat and rinse 
1331
HTH

---

### Post by Note360 on 2006-12-23
The first and second part where equally easy (in ruby)

First part
```

#!/usr/bin/env ruby

def main
  
  puts "Insert a word so I can test for a Palindrome"
  
  phrase = gets.chomp.downcase
  phrase = phrase.gsub /||,||'||"/, ""
  phrase_reverse = phrase.reverse
   
  if phrase == phrase_reverse
    puts "True"
  else
    puts "False"
  end
  
end

while 1
  main
end

```


Here is the second part
```

#!/usr/bin/env ruby

class NumPalindrome
  
  def initialize( a_number )
    @a_number = a_number.to_i
  end
  
  def reverse_number( any_number=@a_number )
    # This sets the reverse of any_number so you can see if it is a palindrome.
    # Takes a_number makes it a string so it can be reversed and makes it into a int 
    
    @r_number = any_number.to_s.reverse.to_i 
  end
  
  # Will find the next palindrome even if it already is one
  def find_next_palindrome
    @r_number = 0
    
    until @a_number == @r_number
      @a_number += 1
      reverse_number @a_number 
    end
    
    return @a_number
  end
  
  def find_last_palindrome
    @r_number = 0
    
    until @a_number == @r_number
      @a_number -= 1
      reverse_number @a_number
    end
    
    return @a_number
  end
  
end

def main  

  print "Insert any number: "
  
  pal_number = NumPalindrome.new( gets.chomp.to_i )
  
  next_pal = pal_number.find_next_palindrome
  last_pal = pal_number.find_last_palindrome
  
  puts "Next Palindrome: #{next_pal}"
  puts "Last Palindrome: #{last_pal}"
end

while 1
  main
end
  

```

Unfortuantly this gets slow at higher numbers. ](*,)

Edit: I revised the code and made it better

---

### Post by ghostdog74 on 2006-12-23
> **dwblas said:**
> Not correct, it should be 1234 --> 1331 = greater than original number.  It seems we have all come to the same solution.  Divide the length by 2 (doesn't matter if the length is even or odd) and strip off the rightmost len/2
1234 --> 12
reverse and append 12-->1221
if less than original, add one to left most
12 --> 13
repeat and rinse 
1331
HTH

Misinterpreted the requirements. The correct one should be 
```

...
a_string = str(long(a_string) + 1)	
...

```

output:
```

>python test.py
Enter a palindrome:sfs
sfs is Palindrome.
Enter a number palindrome:1234
Nearest palindrome:  1331

```

---

### Post by rockz on 2006-12-23
A clean and short solution written in ruby:

```

class Palindrome

	def initialize(phrase)
		@phrase = phrase.gsub(/\s|,|'|\./,'').downcase
	end
	
	def is_it_palindrome?
		@phrase == @phrase.reverse
	end
	
	def next_palindrome_integer
		integer = @phrase.to_i
		
		until integer.to_s == integer.to_s.reverse
			integer+=1
		end
		
		return integer
	end
	
end

print "Enter a phrase: "
my_phrase = Palindrome.new(gets.chomp)
puts "Is it palindrome? #{my_phrase.is_it_palindrome?}"

print "Enter a number: "
my_number = Palindrome.new(gets.chomp)
puts "The next integer palindrome is: #{my_number.next_palindrome_integer}"

```

---

### Post by Note360 on 2006-12-23
> **rockz said:**
> A clean and short solution written in ruby:

```

class Palindrome

	def initialize(phrase)
		@phrase = phrase.gsub(/\s|,|'|\./,'').downcase
	end
	
	def is_it_palindrome?
		@phrase == @phrase.reverse
	end
	
	def next_palindrome_integer
		integer = @phrase.to_i
		
		until integer.to_s == integer.to_s.reverse
			integer+=1
		end
		
		return integer
	end
	
end

print "Enter a phrase: "
my_phrase = Palindrome.new(gets.chomp)
puts "Is it palindrome? #{my_phrase.is_it_palindrome?}"

print "Enter a number: "
my_number = Palindrome.new(gets.chomp)
puts "The next integer palindrome is: #{my_number.next_palindrome_integer}"

```


Your version just killed my version.

---

### Post by Third Thoughts on 2006-12-24
I think I have another solution for part 2 that doesn't just use brute force. I explain it in the code. I haven't proved the algorithm I came up with, but I've given it some testing. Tell me if you see a way to break it. I've done it in ruby. 

Here's the breakdown of the algorithm

After playing around with palindromes for awhile, I figured out there were some rules concerning how you got from one palindrome to the next largest one. Generally, the difference between a palindrome "a" and the next largest "b" was a function of the number of digits of "a". However this did not hold true when the middle number (or middle two numbers) of "a" was a 9. In this case, it was a little more complicated. Here "a" - "b" was a function of a number "n." To get n, you start from the middle 9's (if there are two 9's then start from the first) and move back toward the start of the number until you encounter a number other than 9. The place of the last nine you encounter is "n". So for 191 and 1991 n = 2. For 35953 n = 3. For 99999, 9999, 999, and 99 n=1. I've tested all of my functions somewhat rigoursly, but I haven't proved them, so let me know if you find numbers that don't work. Here are the rules I've come up with

When the middle number is not 9
---Let n be the number of digits in a palindrome a
------If n is even then the difference between a and the next palindrome b is
----------11 * 10^(n-1)
------If n is odd
----------10^round_down(n/2) 

When the middle number is 9
--Let n be as described in the above paragraph (The place of the final nine reading from right to left)
------If n = 1 then the difference between a and the next palindrome b is
----------2
------If n != 1
-----------11 * 10^round_down(n/2)

Once I had these rules, I simply took the given number, made it a palindrome by dropping the last half and then reversing the first half (or in the case of an odd digited number, the last half rounded down, so 12345 became 12321). I called this palindrome, the natural palindrome. I haven't proved, but I'm fairly certainly that there are no palindromes between a number and its natural palindrome. If this conjecture is true, then if the natural palindrome is less than the original number, the next palindrome up must be the closest one greater than the given number. So I just used my rules to get it.

One final note. I considered all single digit numbers (1,2,3 ...9) to be palindromes.

~Andrew S.

```


# Get the user input
number = gets.to_i


######################
#Figuring out the difference between my natural palindrome and the next one up 
#when the middle digit of my number is nine. 
#Its based on the number of consecutive nines from the middle digit
def next_palindrome_finder_with_nines (palindrome_digits, num_length)
	i=0
	k=0
	until (palindrome_digits.reverse[k..k] != "9")
		i += 1	
		k += 1	
	end
		
	
	
	n = palindrome_digits.length - i
	
	if n == 0
		difference_btw_current_pdrome_and_next = 2
	else		
		difference_btw_current_pdrome_and_next = 11 * 10 ** (n.to_f/2).floor
	end

	return difference_btw_current_pdrome_and_next
end	
############################

#The number of digits in the given number
length_of_number = number.to_s.length

#The palindrome part is the portion of the number 
#that will be repeated. In a number with an even number of digits 
#it is the first half of those digits, in one with an odd number, 
#its the first half rounded up (i.e. with a 7 digit number we take the first four)
length_of_palindrome_part = (length_of_number.to_f./(2) + 0.5).floor

palindrome_part = number.to_s[0..length_of_palindrome_part-1]

#In an number with an odd number of digits, the middle number is obvious,
#in an even number, it's the digit that is repeated twice in the middle (i.e in 8338, its 3)
middle_number = number.to_s[length_of_palindrome_part-1..length_of_palindrome_part-1]

#The numbers that will be repeated in the palindrome)
repeated_numbers = number.to_s[0..length_of_palindrome_part-2]



#Here we come up with what I call the natural palidrome for our given number. 
#That's the palindrome you make by dropping the last half of the number 
#and reversing the first half. 
#(ie the natural palindrome of 12345 is 12321. 
#The natural palindrome of 123456 is 123321)
if (length_of_number == 1)
	natural_palindrome = number
elsif (length_of_number == 2)
	natural_palindrome = number.to_s[0..0]*2
elsif (length_of_number % 2 != 0)	
	natural_palindrome = repeated_numbers + middle_number + repeated_numbers.reverse
else
	natural_palindrome = repeated_numbers + middle_number + middle_number + repeated_numbers.reverse
end


#Now that we have our natural palindrome, 
#we check to see if its bigger than the number we were given. 
#If it is, we're done, if not then we do some fancy mathematical footwork 
#to get the next biggest palindrome. 
#Basically there are two different cases, with one divided into sub cases. 
#If the middle number is a nine, then one formula applies. 
#If the middle number isn't a nine, then we check and see if the number 
#has an odd or even number of digits. In each of these three cases, 
#we add a different number to our natural palindrome and 
#get the next palindrome. The mathematical stuff is more fully explained at the beginning.

if (natural_palindrome.to_i > number)
	next_palindrome = natural_palindrome
else
	if (middle_number == "9")
		number_to_add = next_palindrome_finder_with_nines(palindrome_part, length_of_palindrome_part)
	else
		if (length_of_number % 2 != 0)
			number_to_add = 10 ** (length_of_number.to_f/2).floor
		else
			number_to_add = 11 * 10 ** (length_of_number/2 - 1)
		end
	end
	
	next_palindrome = natural_palindrome.to_i + number_to_add
end			

puts next_palindrome

```

---

### Post by Tomosaur on 2006-12-24
> **Third Thoughts said:**
> I think I have another solution for part 2 that doesn't just use brute force. I explain it in the code. I haven't proved the algorithm I came up with, but I've given it some testing. Tell me if you see a way to break it. I've done it in ruby. 


Clever stuff, I'll write it in something else and see if it carries.

EDIT: Actually I won't, got stuff to do :P

---

### Post by cocteau on 2006-12-24
My answer. I don't know if any of the previous attempts in c or c++ did it like this. I'm not very good at sightreading code yet.

Anyway. First part is simple enough, so I'll explain my algorithm for the second before I post the code.

1. Split number into a vector, with an entry for each digit.
2. Define two indeces, to seach through the vector comparing elements.
    set the right one (lower value digits) to size of vector / 2.
    set the left (higher value digits to) size of vector / 2 - 1 if size of vector is even. Otherwise set it to the same as the right one.
3. Do a loop while the left index is higher or equal to index 0. Quoted from the code, this part of the algorithm looks like this:
    //while end has not been reached, set digits like this:
    //l and r must be even.
    //if r < l, set r to l.
    //if r > l, incremt l by one and set r to l
    //also if l is incremented, set r to l for the rest.

Please note, that I consider myself a novice programmer and therefor I prefer code which is more verbose, as it is easier for me to read.

Here's the complete code:

```

#include <iostream>
#include <vector>

using std::cin;               using std::cout;
using std::endl;              using std::vector;

//math function. power.
int pow(const int& x, const int& y)
{
    int ret = 1;
    
    for (int i = y; i != 0; i--) {
           ret *= x;
    }
    
    return ret;
}

//return a vector with each digit from the number seperately.
vector<int> iterateNum(const int& x)
{
    int size = 0;
    vector<int> ret;
    
    int temp = x;
    
    //find number of digits in number
    while ( temp > 0 ) {
        temp /= 10;
        size++;
    }
    
    //split digits into vector
    temp = x;
    
    for (int i = size; i != 0; --i) {
        ret.push_back(temp / pow(10, i - 1));
        temp -= (temp / pow(10, i - 1)) * pow(10, i - 1);
    }
        
    return ret;
}

//join iterated digits as single number.
int joinNum(const vector<int>& vec)
{
    int ret = 0;
    
    for (vector<int>::size_type i = 0; i != vec.size(); ++i)
        ret += vec[i] * pow(10, vec.size() - i - 1);
        
    return ret;
}

//test to see if number is even
bool isEven(const int& x) {
    return (x / 2) * 2 == x;
}

//looks for the next larger palindrome.
int findPal(vector<int> vec)
{
    int ret = 0;
    int l = 0, r = 0;
    
    //if vector has an even size, set indeces one place apart
    //else set to the same spot.
    r = vec.size() / 2;
    
    if (isEven(vec.size())) {
        l = vec.size() / 2 - 1; 
    } else {
        l = vec.size() / 2;
    }
    
    //while end has not been reached, set digits like this:
    //l and r must be even.
    //if r < l, set r to l.
    //if r > l, incremt l by one and set r to l
    //also if l is incremented, set r to l for the rest.
    bool lIncremented = false;
    while ( l >= 0 ) {
        if ( !lIncremented ) {
            if ( vec[l] > vec[r] ) {
                vec[r] = vec[l];
            } else if ( vec[l] < vec[r] ) {
                vec[r] = ++vec[l];
                lIncremented = true;
            }
        } else {
            vec[r] = vec[l];
        }
        
        r++;
        l--;
    }
    
    return joinNum(vec);
}

int main()
{
    int x = 0;
    
    cout << "Enter a number: ";
    cin >> x;
    
    cout << findPal(iterateNum(x)) << endl;

    system("PAUSE");
    return 0;
}
```

... and just for completeness, here's my solution for the first puzzle.

```

#include <iostream>
#include <vector>
#include <string>
#include <cctype>

using std::cin;               using std::cout;
using std::endl;              using std::string;
using std::vector;            using std::isalpha;
using std::isupper;           using std::tolower;

//Fills a vector with some known palindromes and one false.
void populateVector(vector<string>& vec)
{
     vec.push_back("Do geese see god?");
     vec.push_back("Doc, note: I dissent. A fast never prevents a fatness. I diet on cod.");
     vec.push_back("Was it a car or a cat I saw?");
     vec.push_back("I, madam, I made radio. So I dared! Am I mad? Am I?");     
     vec.push_back("Now, sir, a war is never even -- sir, a war is won!");
     vec.push_back("This is not a palindrome!");
     
     return;
}

//copy only alpha chars into a return vector and convert all chars to
//lowercase.
void stripNonAlpha(vector<string>& vec, vector<string>& retVec)
{
     string buffer;
     retVec.clear();
     
     for (vector<string>::size_type i = 0; i != vec.size(); ++i) {
     buffer.clear();
            
         for (string::size_type j = 0; j != vec[i].size(); ++j) {
             if (isalpha(vec[i][j]))        //if alpha char
                if (isupper(vec[i][j]))     //if upper case
                    buffer += tolower(vec[i][j]);
                else
                    buffer += vec[i][j];
         }
     
     retVec.push_back(buffer);
     }
     
     return;
}       


//check to see if string is a palindrome.
bool isPal(const string& s)
{
    string::const_iterator iter = s.begin();
    string::const_reverse_iterator rIter = s.rbegin();
    bool isPal = true;
    
    while (isPal && iter != s.end()) {
          if (*iter != *rIter)
             isPal = false;
          else {
               iter++;
               rIter++;
          }
    }
    
    return isPal;
}
     


int main()
{
    vector<string> szVec;
    vector<string> tVec;
    
    populateVector(szVec);
    stripNonAlpha(szVec, tVec);
    
    for (vector<string>::size_type i = 0; i != szVec.size(); ++i) {
        cout << "'" << szVec[i] << "'";
        
        if (isPal(tVec[i])) {
            cout << " is a palindrom.";
        } else {
            cout << " is NOT a palindrom.";
        }
        
        cout << endl;
    }
    
    system("PAUSE");
    return 0;
}
```

EDIT1: Oh yes... I borrowed some palindromes from a previous solution and forgot to give credit for it. Sorry about that.

---

### Post by otaviocc on 2006-12-26
My contribution with Wolfram's Mathematica:

```
Palindrome[word_] := Module[{},If[word == StringReverse[word], Return["True"], Return["False"]]];
```

or just:

```
Palindrome[word_] := If[word == StringReverse[word], "True", "False"];
```

```
In[8]:=
Palindrome["OCC"]
Out[8]=
False
```

```
In[9]:=
Palindrome["ABBABABBA"]
Out[9]=
True
```

And a classical palindrome phrase in Portuguese: "Socorram me subi no ônibus em Marrocos" (Help me I went in a bus in Morocco.)

```
In[10]:=
Palindrome["SOCORRAMMESUBINONIBUSEMMARROCOS"]
Out[10]=
True
```

---

### Post by JupiterV2 on 2008-05-10
Strictly speaking, the code which makes the lowest palindrome from a number without going under doesn't do so. It will produce a result that is only slightly higher but doesn't COMPLETELY fit the bill.

For example: if the number 1436 was entered, 2442 would be returned. If the challenge was strictly followed the correct output would be 2002. However, I decided not to do so as who wants to look at a whack-load of zeros between two numbers. (ie: 134504 outputs to 235532 whereas 200002 would be a smaller number without going under)

[PHP]#include <stdio.h>
#include <string.h>

int is_palindrome(const char* str)
{
	// test whether or not the given string is a palindrome 
	int len = strlen(str);
	
	int x, y;
	char cx, cy;
	
	for(x = 0, y = (len - 1); x < y;)
	{
		cx = str[x], cy = str[y];
		
		// switch from upper case to lower case
		if( cx > 64 && cx < 90 ) cx += 32;
		if( cy > 64 && cy < 90 ) cy += 32;
		
		// non-lowercase non-alpha-numerics are ignored
		if( (cx < 97 || cx > 122) && (cx < 48 || cx > 57) )
		{
			x++;
			continue;
		}
		
		if( (cy < 97 || cy > 122) && (cy < 48 || cy > 57) )
		{
			y--;
			continue;
		}
		
		if( cx != cy ) return 0;
		
		x++;
		y--;
	}
		
	return 1;
}

int make_palindrome(char* str)
{
	int len = strlen(str);
	int x = 0, y = len - 1;
	
	while( !is_palindrome(str) && x <= y)
	{		
		if( str[x] == str[y] ) continue;
		
		if( str[x] > str[y] ) str[y] = str[x];
		else str[y] = ++str[x];
		
		x++, y--;
	}
}

int is_number(const char* str)
{
	// tests whether the given string represents a number
	int len = strlen(str), x = 0;
	
	while( x < len )
	{
		if( str[x] < 48 || str[x] > 57 ) return 0;
		x++;
	}
	
	return 1;
}

int main(int argc, char** argv)
{
	if( argc != 2 )
	{
		printf("Usage: %c <value>\n", argv[0]);
		return 1;
	}
	
	if( is_number(argv[1]) ) make_palindrome(argv[1]);
	
	printf("Is %s a palindrome? %s\n", argv[1], 
		(is_palindrome(argv[1]) ? "yes" : "no"));
		
}[/PHP]

---

### Post by LaRoza on 2008-05-10
[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

---

