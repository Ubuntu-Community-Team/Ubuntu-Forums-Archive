---
title: "Weekly Programming Challenge: Friday, December 15, 2006"
date: 2006-12-14
forum: Programming Talk
---

### Post by meng on 2006-12-14
Okay, it has fallen to me to set this week's puzzle. I'm not sure I deserved the honor, but since I have it, and will never get it again, here goes:

Write a program that asks the user to input an integer in numeral form (base 10, let's not get too tricky now). The program then returns that number written as a string.

e.g. if the input was: 169
the output would be: one hundred sixty-nine

The program should be able to handle numbers from 0 to one million.
Feel free to include exception handling if that floats your boat.
My goal here was to set a problem only slightly more tricky than the previous 2 problems.

I prefer not to have the responsibilty of choosing the winner, but if I did have that responsibility, I can tell you that I wouldn't be deciding based on the smallest number of lines of code.

Oh yeah, it's not Friday here yet, but it is Friday in some parts of the world.

---

### Post by gummibaerchen on 2006-12-14
> **meng said:**
> 
Oh yeah, it's not Friday here yet, but it is Friday in some parts of the world.

Hehe, me as an UTC-ler has still about 5 hours to wait :)

Sounds really harder than the others :) We'll see how people do.

---

### Post by kthakore on 2006-12-14
here is my entry in C++:
how would I do an long entry from command line (like ./int2num 126)
```
// Kartik Thakore
// DEC 13th 2006
// Lab 5 
// The following program will convert numbers to words
// E.G 234 is two hundred and tirty four


#include <iostream>
#include <string>
using namespace std;

// Global Varaibles 

const int HUNDRED (30), THOUSAND(31), MILLION(32), BILLION(33), neagtive(0);

//Defining SayWord to create the individual words

void SayWord(long number)
{
 switch(number)
 {
  case 0:
  cout << "" ;
  break;
  
  case 1:
  cout << "one" ;
  break;
  
  case 2:
  cout << "two" ;
  break;
  
  case 3:
  cout << "three" ;
  break;
 
  case 4:
  cout << "four" ;
  break;

  case 5:
  cout << "five" ;
  break;

  case 6:
  cout << "six" ;
  break;
  
  case 7:
  cout << "seven" ;
  break;

  case 8:
  cout << "eight" ;
  break;

  case 9:
  cout << "nine" ;
  break;

  case 10:
  cout << "ten" ;
  break;

  case 11:
  cout << "eleven" ;
  break;

  case 12:
  cout << "twelve" ;
  break;
  
  case 13:
  cout << "thirteen" ;
  break;

  case 14:
  cout << "fourteen" ;
  break;

  case 15:
  cout << "fifteen" ;
  break;

  case 16:
  cout << "sixteen" ;
  break;

  case 17:
  cout << "seventeen" ;
  break;

  case 18:
  cout << "eighteen" ;
  break;

  case 19:
  cout << "nineteen" ;
  break;
  
  case 22:
  cout << "twenty" ;
  break;

  case 23:
  cout << "thirty" ;
  break;

  case 24:
  cout << "forty" ;
  break;
  
  case 25:
  cout << "fifty" ;
  break;
  
  case 26:
  cout << "sixty" ;
  break;

  case 27:
  cout << "seventy" ;
  break;

  case 28:
  cout << "eighty" ;
  break;
  
  case 29:
  cout << "ninety" ;
  break;

  case 30:
  cout << "hundred" ;
  break;

  case 31:
  cout << "thousand" ;
  break;

  case 32:
  cout << "million" ;
  break;
  
  case 33:
  cout << "billion" ;
  break;
   }
} // end SayWord function

void SayHundred(long number)
{
int hundreds, tens, ones; //integer division need not a float one
 hundreds = number/100; //E.G 123 will give 123
 tens = (number%100)/10; //E.G 143 will give 43/10 will give 4 + 20 =24 with is forty
 ones = number%10;
// cout << endl << "[DEBUG] hundreds" << hundreds << " tens " << tens << " ones " << ones << endl; 
  if (hundreds) {
    SayWord(hundreds);
    cout << " ";
    SayWord(HUNDRED);
    cout << " ";
  }
  if (tens >= 2) {
    SayWord(20+tens);
    cout << " ";
    SayWord(ones);
    cout << " ";
  }
  else
   SayWord((tens*10)+ones);
  
} // end SayHundred

void Speak(long number)
{
 int billions, millions, thousands, hundreds;
  
 billions = number/1000000000;
 number = number%1000000000;
 millions = number/1000000;
 number = number%1000000;
 thousands = number/1000;
 hundreds = number%1000;

if(billions)
{
SayHundred(billions);

SayWord(BILLION);
cout << " ";
}
if(millions)
{ 
 SayHundred(millions); 
 cout << " ";
 SayWord(MILLION);
 cout << " "; 
}
if (thousands) {
  SayHundred(thousands);
  cout << " ";
  SayWord(THOUSAND);
  cout << " "; 
}
  SayHundred(hundreds);
}



//end Speak

int main (int argc, char argv[])
{
long number(0);
string error;
//Forever Loop
while (0 == 0)
{


cout << "Integer to Number Sentences"
     << endl
     << "Enter a number ";
    cin >> number;
    if (cin.fail())
    { //cout << "Fail!";
      cin.clear();
      char c = cin.get();
      if ('q' == c)
	{
         cout << "Exiting" << endl;
         exit(0);
         }
  
 // cin.ignore(1000,'\n');

     }


if (number > 2000000000 || number < -2000000000)
  { //cout << "NOT FAIL!!!";
    system("clear"); //change to system("cls") for win32
    cout << number << " is either too big or too small" << endl;
    continue;
  }
else
system("clear"); //change to system("cls") for win32
cout << "Got " << number << endl;
if(number < 0)
{
 number = -number;
 cout << "negative ";
}
if(number == 0)
{
cout << "zero" ;
}
else
{Speak(number);}
cout << endl;

}//end forever loop


return 0;
}

```

---

### Post by Verminox on 2006-12-14
Start Time: 15 Dec 12:30 AM IST
End Time: 15 Dec 1:10 AM IST

So this is my 40 minute program in C++ :p

```
/*
 * Integer to words
 * By Verminox
 */

#include <iostream>
#include <cmath>
#include <cstring>
#include <cassert>

using namespace std;

string digit2word(unsigned int d){
    // Digits
    static const string d2w[] = { "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine" };
    
    assert( d < 10 );
    if( d == 0 ){
        return string();
    } else {
        return d2w[d-1];
    }
}

string tens2word(unsigned int t){
    // Tens
    static const string t2w[] = { "Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen",
      /* 10= */  "Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety" };

    assert( t < 100 );
    
    if( t == 0 ){
        return string();
    } else if ( t < 10 ){
        return digit2word(t);
    } else if ( t < 20 ) {
        return t2w[t-10]; // First 10 elements of t2w[]
    } else {
        int tens_part = (int)(t/10); // Cut the last digit.. will be between 2-9
        int digit_part = t % 10; // The last digit.. will be between 0-9
        return t2w[tens_part+8] + string(" ") + digit2word(digit_part);
    }
}
        
        
string hun2word(unsigned int h){
    assert( h < 1000 );
    int hun_part = (int)(h/100); // Cut the last 2 digits... ans will be between 0-9
    int tens_part = h % 100; // The last 2 digits... ans will be between 0-99
    
    if( hun_part == 0 ){
        return tens2word(tens_part);
    } else {
        return digit2word(hun_part) + string(" Hundred ") + tens2word(tens_part);
    }
}


string num2word(unsigned long int x){
    string word; // The number in words
    
    int millions  = (int)(x/1000000); // Cut the last 6 digits
    int thousands = (int)(x % 1000000/1000); // Cut everything over the million mark then cut the last 3 digits
    int hundreds = x % 1000; // The last 3 digits
    
    if( millions != 0 ){
        word += hun2word( millions ) + string (" Million ");
    }
    
    if( thousands != 0 ){
        word += hun2word( thousands ) + string(" Thousand ");
    }
    
    word += hun2word( hundreds );
    
    return word;
    
}
    
    

int main(int argc, char *argv[]){
    long int x;
    do {
        cout << "Enter an integer: ";
        cin >> x;
        cout << num2word(x) << endl;
    } while ( x != 0 );
    
    return 0;
}

```


This can count from 1 (One) to 999999999 (Nine Hundred Ninety Nine Million Nine Hundred Ninety Nine Thousand Nine Hundred Ninety Nine)

It cannot count "Zero" because that is the input used to terminate the program :p

Negative numbers are not supported but doesn't take a genius to add that. I'm just too sleepy so I'm turning in.... 'nite



PS: Why does the [ code ] block mess up the indents? Shouldn't it be showign fixed width fonts?

---

### Post by duff on 2006-12-14
going with python this week
```
#!/usr/bin/env python

import sys

words = {
       0:'zero',      1:'one',       2:'two',      3:'three',
       4:'four',      5:'five',      6:'six',      7:'seven',
       8:'eight',     9:'nine',     10:'ten',      11:'eleven',
      12:'twelve',   13:'thirteen', 14:'fourteen', 15:'fifteen',
      16:'sixteen',  17:'seventeen',18:'eighteen', 19:'nineteen',
      20:'twenty',   30:'thirty',   40:'forty',    50:'fifty',
      60:'sixty',    70:'seventy',  80:'eighty',   90:'ninty',
     100:'hundred',1000:'thousand',
}

def hundreds(n):
   if n > 99:
      print words[n / 100], words[100],
      n %= 100
   if n > 19:
      print words[(n / 10) * 10],'-',
      n %= 10
   if n > 0:
      print words[n],

n = int(sys.argv[1])
if n == 0:
   print 'zero'
elif 1000 < n < 2000:
   hundreds(n)
else:
   if n >= 1000000:
      hundreds(n / 1000000)
      n %= 1000000
      print 'million',
   if n > 1000:
      hundreds(n / 1000)
      n %= 1000
      print 'thousand',
   hundreds(n)
```

```
# ./numstr.py 169
one hundred sixty - nine
#  ./numstr.py 0
zero
# ./numstr.py 2013
two thousand thirteen
#  ./numstr.py 1234
twelve hundred thirty - four
#  ./numstr.py 987654
nine hundred eighty - seven thousand six hundred fifty - four
```

---

### Post by meng on 2006-12-14
twelve hundred thirty-four? Yuk!
But good effort everyone so far!

---

### Post by utab on 2006-12-14
I liked this programming quiz, this a brain train for us.

Hope never ends

---

### Post by gummibaerchen on 2006-12-14
Mine first quick-test in python. I thought of dicts for that as "duff" did, but had nothing serious started yet :)

```
#!/usr/bin/python
#
#      This program is free software; you can redistribute it and/or modify
#      it under the terms of the GNU General Public License as published by
#      the Free Software Foundation; either version 2 of the License, or
#      (at your option) any later version.
#
#      This program is distributed in the hope that it will be useful,
#      but WITHOUT ANY WARRANTY; without even the implied warranty of
#      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#      GNU General Public License for more details.
#
#      You should have received a copy of the GNU General Public License
#      along with this program; if not, write to the Free Software
#      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
#
import sys
number = 1234
print "the number is", sys.argv[1]

number = sys.argv[1]
enumber = str(number)

# Fourth last thing
if enumber[-4] == "1":
    print "one thousand",
elif enumber[-4] == "2":
    print "two thousand",
elif enumber[-4] == "3":
    print "three thousand",
elif enumber[-4] == "4":
    print "four thousand",
elif enumber[-4] == "5":
    print "five thousand",
elif enumber[-4] == "6":
    print "six thousand",
elif enumber[-4] == "7":
    print "seven thousand",
elif enumber[-4] == "7":
    print "eight thousand",
elif enumber[-4] == "9":
    print "nine thousand",
elif enumber[-4] == "0":
    print "zero thousand",
else:
    print "somethings wrong"

# Third last thing
if enumber[-3] == "1":
    print "one hundred",
elif enumber[-3] == "2":
    print "two hundred",
elif enumber[-3] == "3":
    print "three hundred",
elif enumber[-3] == "4":
    print "four hundred",
elif enumber[-3] == "5":
    print "five hundred",
elif enumber[-3] == "6":
    print "six hundred",
elif enumber[-3] == "7":
    print "seven hundred",
elif enumber[-3] == "7":
    print "eight hundred",
elif enumber[-3] == "9":
    print "nine hundred",
elif enumber[-3] == "0":
    print "and"
else:
    print "somethings wrong - fourth last"


if (enumber[-2] + enumber[-1]) == "11":
    print "eleven",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "12":
    print "twelve",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "13":
    print "thirteen",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "14":
    print "fourteen",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "15":
    print "fiveteen",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "16":
    print "sixteen",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "17":
    print "seventeen",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "18":
    print "eighteen",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "19":
    print "nineteen",
    sys.exit()
elif (enumber[-2] + enumber[-1]) == "10":
    print "ten",
    sys.exit()
#else:
    #print "somethings wrong - third last"
# ^ ^ ^ caused problems, of course!

# Second last thing
if enumber[-2] == "1":
    print "ten",
elif enumber[-2] == "2":
    print "twenty -",
elif enumber[-2] == "3":
    print "thirty -",
elif enumber[-2] == "4":
    print "fourty -",
elif enumber[-2] == "5":
    print "fifty -",
elif enumber[-2] == "6":
    print "sixty -",
elif enumber[-2] == "7":
    print "seventy -",
elif enumber[-2] == "7":
    print "eighty -",
elif enumber[-2] == "9":
    print "ninety -",
elif enumber[-2] == "0":
    print "and",
else:
    print "somethings wrong - second last"

# Last Thing
if enumber[-1] == "1":
    print "one"
elif enumber[-1] == "2":
    print "two"
elif enumber[-1] == "3":
    print "three"
elif enumber[-1] == "4":
    print "four"
elif enumber[-1] == "5":
    print "five"
elif enumber[-1] == "6":
    print "six"
elif enumber[-1] == "7":
    print "seven"
elif enumber[-1] == "7":
    print "eight"
elif enumber[-1] == "9":
    print "nine"
elif enumber[-1] == "0":
    print "zero"
else:
    print "somethings wrong - last"

```

That's crazy, isn't it? only goes till 9999 (at the moment).

---

### Post by duff on 2006-12-14
> **meng said:**
> twelve hundred thirty-four? Yuk!
guess that's american

---

### Post by gummibaerchen on 2006-12-14
> **Verminox said:**
> 
PS: Why does the [ code ] block mess up the indents? Shouldn't it be showign fixed width fonts?

Yes, the code-blocks suck indeed, maybe transfer all the recent **results** (working programs) into the Wiki?

---

### Post by pmasiar on 2006-12-14
> **meng said:**
> I prefer not to have the responsibilty of choosing the winner, but if I did have that responsibility, I can tell you that I wouldn't be deciding based on the smallest number of lines of code.

It would be unfair to decide based on line number: python will be the readable solution, and perl the shortest! :-)

---

### Post by duff on 2006-12-14
tad shorter and with higher numbers.
```
#!/usr/bin/env python

import sys

words = {
       0:'zero',      1:'one',       2:'two',      3:'three',
       4:'four',      5:'five',      6:'six',      7:'seven',
       8:'eight',     9:'nine',     10:'ten',      11:'eleven',
      12:'twelve',   13:'thirteen', 14:'fourteen', 15:'fifteen',
      16:'sixteen',  17:'seventeen',18:'eighteen', 19:'nineteen',
      20:'twenty',   30:'thirty',   40:'forty',    50:'fifty',
      60:'sixty',    70:'seventy',  80:'eighty',   90:'ninty',
}

illions = 'quintillion', 'quadrillion', 'trillion', 'billion', 'million', 'thousand', ''

def hundreds(n):
   if 99 < n < 1000:
      print words[n / 100], 'hundred',
      n %= 100
   if 19 < n < 100:
      print words[(n / 10) * 10],'-',
      n %= 10
   if 0 < n < 20:
      print words[n],

n = int(sys.argv[1])

if n == 0:
   print 'zero'
else:
   for i, label in enumerate(illions):
      mag = 10 ** (3 * (6-i))
      if n >= mag:
         hundreds(n / mag)
         n %= mag
         print label,

```

running with the US national debt:```
./numstr.py 8665352067907
eight trillion six hundred sixty - five billion three hundred fifty - two million sixty - seven thousand nine hundred seven
```:(

---

### Post by Wybiral on 2006-12-14
lol, I vote duff for using the national debt as an example! Brilliant...

---

### Post by Biggus on 2006-12-15
Hi guys, sorry if theres a sticky all of the forum with the rules posted in it, but I was just wondering if the competition is restricted to certain languages on certain platforms?

ie would I be able to submit code in Sinclair BASIC, for example?

---

### Post by Verminox on 2006-12-15
Biggus: I believe any language is accepted, so give it a go ;)

---

### Post by lnostdal on 2006-12-15
> **meng said:**
> Okay, it has fallen to me to set this week's puzzle. I'm not sure I deserved the honor, but since I have it, and will never get it again, here goes:

Write a program that asks the user to input an integer in numeral form (base 10, let's not get too tricky now). The program then returns that number written as a string.

e.g. if the input was: 169
the output would be: one hundred sixty-nine

The program should be able to handle numbers from 0 to one million.
Feel free to include exception handling if that floats your boat.
My goal here was to set a problem only slightly more tricky than the previous 2 problems.

I prefer not to have the responsibilty of choosing the winner, but if I did have that responsibility, I can tell you that I wouldn't be deciding based on the smallest number of lines of code.

Oh yeah, it's not Friday here yet, but it is Friday in some parts of the world.

Common Lisp has this built in:

```

cl-user> (dotimes (i 20)
           (format t "~R~%" (expt i i)))
one
one
four
twenty-seven
two hundred fifty-six
three thousand one hundred twenty-five
forty-six thousand six hundred fifty-six
eight hundred twenty-three thousand five hundred forty-three
sixteen million seven hundred seventy-seven thousand two hundred sixteen
three hundred eighty-seven million four hundred twenty thousand four hundred eighty-nine
ten billion
two hundred eighty-five billion three hundred eleven million six hundred seventy thousand six hundred eleven
eight trillion nine hundred sixteen billion one hundred million four hundred forty-eight thousand two hundred fifty-six
three hundred two trillion eight hundred seventy-five billion one hundred six million five hundred ninety-two thousand two hundred fifty-three
eleven quadrillion one hundred twelve trillion six billion eight hundred twenty-five million five hundred fifty-eight thousand sixteen
four hundred thirty-seven quadrillion eight hundred ninety-three trillion eight hundred ninety billion three hundred eighty million eight hundred fifty-nine thousand three hundred seventy-five
eighteen quintillion four hundred forty-six quadrillion seven hundred forty-four trillion seventy-three billion seven hundred nine million five hundred fifty-one thousand six hundred sixteen
eight hundred twenty-seven quintillion two hundred forty quadrillion two hundred sixty-one trillion eight hundred eighty-six billion three hundred thirty-six million seven hundred sixty-four thousand one hundred seventy-seven
thirty-nine sextillion three hundred forty-six quintillion four hundred eight quadrillion seventy-five trillion two hundred ninety-six billion five hundred thirty-seven million five hundred seventy-five thousand four hundred twenty-four
one septillion nine hundred seventy-eight sextillion four hundred nineteen quintillion six hundred fifty-five quadrillion six hundred sixty trillion three hundred thirteen billion five hundred eighty-nine million one hundred twenty-three thousand nine hundred seventy-nine
nil
cl-user> 

```

---

### Post by meng on 2006-12-15
> **lnostdal said:**
> Common Lisp has this built in
I suspected SOME language had such a feature. Interesting it took a while for anyone to mention it. Had I known, I probably would have set a different puzzle, but it's a legitimate solution nonetheless. Thanks for sharing.

---

### Post by rockz on 2006-12-15
My contribution, I made a ruby program to solve this challenge.

```

=begin
  This program convert a number to words

  Yuri Malheiros 
  December, 15th 2006
=end

class Number
   def initialize(x)
    @words = {
       0 => 'zero',     1 => 'one',        2 => 'two',       3 => 'three', 
       4 => 'four',     5 => 'five',       6 => 'six',       7 => 'seven', 
       8 => 'eight',    9 => 'nine',      10 => 'ten',      11 => 'eleven', 
      12 => 'twelve',  13 => 'thirteen',  14 => 'fourteen', 15 => 'fifteen',
      16 => 'sixteen', 17 => 'seventeen', 18 => 'eighteen', 19 => 'nineteen',
      20 => 'twenty',  30 => 'thirty',    40 => 'forty',    50 => 'fifty',
      60 => 'sixty',   70 => 'seventy',   80 => 'eighty',   90 => 'ninety',
    }

    @number = x
  end
  
  def string_hundred(x)
    result = ''
   
    if (x/100) >= 1 && (x/100) <= 9
      result << @words[x/100] << ' hundred '
    end
    
    if (x % 100) >= 1 && (x % 100) <= 20
      result << @words[x%100]
    elsif (x%100/10*10) != 0
      result << @words[x%100/10*10]
      if (x%10) > 0
        result << '-' << @words[x%10]
      end
    end
    
    return result
  end

  def to_s
    result = ''
    thousands = @number % 10**6 / 1000
    millions = @number % 10**9 / 10**6

    if @number == 0
      result << @words[0]
    end

    if millions >= 1 && millions <= 999
      result << string_hundred(millions) << ' million ' 
    end

    if thousands >= 1 && thousands <= 999
      result << string_hundred(thousands) << ' thousand ' 
    end
   
    result << string_hundred(@number % 1000)
  end

end

myNumber = Number.new(873029841)
puts myNumber

```

The result is eight hundred seventy-three million twenty-nine thousand eight hundred forty-one

---

### Post by -J- on 2006-12-15
I'm a scripting hack, just enough to get the job done I guess.

Anyways, here's my ductape version...
```

#!/usr/bin/perl

%words= (1 => 'one', 2 => 'two', 3 => 'three', 4 => 'four', 5 => 'five',
        6 => 'six', 7 => 'seven', 8 => 'eight', 9 => 'nine', 10 => 'ten',
        110 => 'eleven', 120 => 'twelve', 130 => 'thirteen', 140 => 'fourteen', 150 => 'fifteen',
        160 => 'sixteen', 170 => 'seventeen', 180 => 'eighteen', 190 => 'nineteen',
        20 => 'twenty', 30 => 'thirty', 40 => 'forty', 50 => 'fifty', 60 => 'sixty',
        70 => 'seventy', 80 => 'eighty', 90 => 'ninety');

print"Enter an integer in numeral form: ";
chomp($input=<STDIN>);
@numbers = reverse(split(//, $input));

if ( @numbers[1] =~ /^1$/ && @numbers[0] != 0) { @numbers[1] = "@numbers[1]@numbers[0]"; @numbers[0] = 99; }
if ( @numbers[4] =~ /^1$/ && @numbers[3] != 0) { @numbers[4] = "@numbers[4]@numbers[3]"; @numbers[3] = 99; }

print $words{@numbers[6]}," million " if (@numbers[6]);
print $words{@numbers[5]}," hundred " if (@numbers[5]);
print $words{(@numbers[4]*10)} if (@numbers[4]);
print "-" if (@numbers[4] =~ /^[2-9]/ && @numbers[3] != 0);
print $words{@numbers[3]}," thousand " if (@numbers[3]);
print $words{@numbers[2]}," hundred " if (@numbers[2]);
print $words{(@numbers[1]*10)} if (@numbers[1]);
print "-" if (@numbers[1] =~ /^[2-9]/ && @numbers[0] != 0);
print $words{@numbers[0]} if (@numbers[0]);
print "\n";

```

---

### Post by Klipt on 2006-12-15
Delphi code I wrote a long time ago (long, but I tried to make it 'sound natural'):
```
const
   Digit: array[0 .. 9] of string = ('zero', 'one', 'two', 'three',
    'four', 'five', 'six', 'seven', 'eight', 'nine');
   Teen: array[10 .. 19] of string = ('ten', 'eleven', 'twelve',
    'thirteen', 'fourteen', 'fifteen', 'sixteen', 'seventeen', 'eighteen',
    'nineteen');
   Ten: array[2 .. 9] of string = ('twenty', 'thirty', 'forty', 'fifty',
    'sixty', 'seventy', 'eighty', 'ninety');
   Multiplier: array[1..6] of string = ('thousand', 'million', 'billion', 'trillion', 'quadrillion', 'quintillion');

function DoubleDigit(Num: integer): string;
begin
   if Num < 10 then
      Result := Digit[Num]
   else if Num < 20 then
      Result := Teen[Num]
   else
   begin
      Result := Ten[Num div 10];
      if (Num mod 10) <> 0 then
         Result := Result + '-' + Digit[Num mod 10];
   end;
end;

function TripleDigit(Num: integer): string;
begin
   if Num < 100 then
      Result := DoubleDigit(Num)
   else
   begin
      Result := Digit[Num div 100] + ' hundred';
      if (Num mod 100) <> 0 then
         Result := Result + ' and ' + DoubleDigit(Num mod 100);
   end;
end;

function QuadrupleDigit(Num: integer): string;
begin
   if Num < 1000 then
      Result := TripleDigit(Num)
   else
   begin
      Result := Digit[Num div 1000] + ' thousand';
      if (Num mod 1000) <> 0 then
         if (Num mod 1000) < 100 then
            Result := Result + ' and ' + DoubleDigit(Num mod 100)
         else
            Result := Result + ', ' + TripleDigit(Num mod 1000);
   end;
end;

function ButLastThreeDigits(Num: int64): string;
var
   Mul: integer;
begin
   Result := '';
   Num := Num div 1000;
   Mul := 1;
   while Num > 0 do
   begin
      if (Num mod 1000 > 0) then
      begin
         Result := TripleDigit(Num mod 1000) + ' ' + Multiplier[Mul] + Result;
         if Num >= 1000 then
            Result := ', ' + Result;
      end;
      Num := Num div 1000;
      Inc(Mul);
   end;
end;

function AsWord(Num: int64): string;
begin
   if Num < 0 then
      Result := 'minus ' + AsWord(-Num)
   else if Num < 1000 then
      Result := TripleDigit(Num)
   else
   begin
      Result := ButLastThreeDigits(Num);
      if (Num mod 1000) <> 0 then
         if (Num mod 1000) < 100 then
            Result := Result + ' and ' + DoubleDigit(Num mod 100)
         else
            Result := Result + ', ' + TripleDigit(Num mod 1000);
   end;
end;

```

Output of US national debt: "Eight trillion, six hundred and sixty-five billion, three hundred and fifty-two million, sixty-seven thousand, nine hundred and seven."

---

### Post by rockz on 2006-12-15
Update... now the number is read from keyboard:

```

=begin
  This program convert a number to words

  Yuri Malheiros 
  December, 15th 2006
=end

class Number
   def initialize(x)
    @words = {
       0 => 'zero',     1 => 'one',        2 => 'two',       3 => 'three', 
       4 => 'four',     5 => 'five',       6 => 'six',       7 => 'seven', 
       8 => 'eight',    9 => 'nine',      10 => 'ten',      11 => 'eleven', 
      12 => 'twelve',  13 => 'thirteen',  14 => 'fourteen', 15 => 'fifteen',
      16 => 'sixteen', 17 => 'seventeen', 18 => 'eighteen', 19 => 'nineteen',
      20 => 'twenty',  30 => 'thirty',    40 => 'forty',    50 => 'fifty',
      60 => 'sixty',   70 => 'seventy',   80 => 'eighty',   90 => 'ninety',
    }

    @number = x
  end
  
  def string_hundred(x)
    result = ''
   
    if (x/100) >= 1 && (x/100) <= 9
      result << @words[x/100] << ' hundred '
    end
    
    if (x % 100) >= 1 && (x % 100) <= 20
      result << @words[x%100]
    elsif (x%100/10*10) != 0
      result << @words[x%100/10*10]
      if (x%10) > 0
        result << '-' << @words[x%10]
      end
    end
    
    return result
  end

  def to_s
    result = ''
    thousands = @number % 10**6 / 1000
    millions = @number % 10**9 / 10**6

    if @number == 0
      result << @words[0]
    end

    if millions >= 1 && millions <= 999
      result << string_hundred(millions) << ' million ' 
    end

    if thousands >= 1 && thousands <= 999
      result << string_hundred(thousands) << ' thousand ' 
    end
   
    result << string_hundred(@number % 1000)
  end

end

print "Enter a number: "
number = gets.chomp.to_i

myNumber = Number.new(number)
puts myNumber

```

---

### Post by jayemef on 2006-12-16
Fun bash solution that utilizes Google!

```

#!/bin/bash

NUMBER=$1

# Check whether number is more than 3 digits, as Google adds padding.
if [ ${#NUMBER} -gt 3 ]; then
    NUMBER=${NUMBER:(-3):3}
fi


RESULT=$(wget -U "Mozilla Firefox" http://www.google.com/search?q=$1+in+words -O - 2> /dev/null | grep "$NUMBER = " | sed "s/.*$NUMBER = //g" | sed 's/<.*//g')

echo $RESULT


```

Output:
> 
./num_to_text.sh 12455735
twelve million four hundred fifty-five thousand seven hundred thirty-five



Running through the code, I first run a query against Google using wget to pull results. I then grep to find the result line, use sed to filter out everything before the answer, and then use sed again to filter out everything after the answer. I'm sure these utilities could have been used more elegantly, but this was quick and semantically logical.

---

### Post by diggity on 2006-12-16
Here's a PHP/HTML example using a form and php arrays
```

<?php
function num2str($group, $place)
{
    global $numberWords, $placeWords;
    
    $numStr = '';
    $hundreds = '';
    $tens = '';
    $ones = '';
    $groupSize = count($group);
    if($groupSize == 3)
    {
        $hundreds = $group[0];
        $tens = $group[1];
        $ones = $group[2];
    }
    else if($groupSize == 2)
    {
        $tens = $group[0];
        $ones = $group[1];
    }
    else
        $ones = $group[0];
    
    if($hundreds > 0)
    {
        $numStr .= $numberWords[$hundreds].' '.$placeWords[0].' ';
        if($place == 0)
            $numStr .= ' and ';
    }
    if($tens > 1)
        $numStr .= $numberWords[$tens.'0'].'-'.$numberWords[$ones].' ';
    else if($tens == 1)
        $numStr .= $numberWords[$tens.$ones].' ';
    else
        $numStr .= $numberWords[$ones].' ';
        
    return $numStr;
}

if(isset($_POST['submit']))
{
    $number = $_POST['myNumber'];
    $numberWords = array('1' => 'one', '2' => 'two', '3' => 'three', '4' => 'four', '5' => 'five', 
    '6' => 'six', '7' => 'seven', '8' => 'eight', '9' => 'nine', '10' => 'ten', '11' => 'eleven', 
    '12' => 'twelve', '13' => 'thirteen', '14' => 'fourteen', '15' => 'fifteen', '16' => 'sixteen', 
    '17' => 'seventeen', '18' => 'eighteen', '19' => 'nineteen', '20' => 'twenty', '30' => 'thirty', 
    '40' => 'forty', '50' => 'fifty', '60' => 'sixty', '70' => 'seventy', '80' => 'eighty', 
    '90' => 'ninety');
    $placeWords = array('hundred', 'thousand', 'million', 'billion');
    $numberArray = array_chunk(array_reverse(str_split($number)), 3);
    $numGroups = count($numberArray);
    $currPlace = $numGroups-1;
    $str = '';
    for($i=($numGroups-1); $i>=0; $i--)
    {
        $str .= num2str(array_reverse($numberArray[$i]), $currPlace);
        if($currPlace > 0)
            $str .= ' '.$placeWords[$currPlace].', ';
        $currPlace--;
    }
}
?>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0.1//EN">
<html>
<head>
  <title>Number to String</title>
</head>
<body>
<form name="myForm" action="num2str.php" method="post">
Type a number: <input type="text" name="myNumber" size="20" maxlength="12" value="<?php echo @$number ?>" /><br />
<input type="submit" name="submit" value=" Write String " />
</form>
<br /><br />
<?php echo @$str ?>
</body>
</html>

```Using the above number of 873029841, the output is:
eight hundred seventy-three  million, twenty-nine  thousand, eight hundred  and forty-one

---

### Post by hod139 on 2006-12-16
> **jayemef said:**
> Fun bash solution that utilizes Google!

Has my vote for most innovative solution!  I was trying to think of a solution that didn't utilize a lookup table for the names and couldn't think of one.  Great idea!!

---

### Post by dwblas on 2006-12-16
> Fun bash solution that utilizes Google!
Has my vote for most innovative solutionMy vote as well (if I had one).  Excellent solution to use existing resources.  Why re-invent the wheel of numbers to strings.

---

### Post by samjh on 2006-12-16
> **jayemef said:**
> Fun bash solution that utilizes Google!

[SNIPE CODE]

Running through the code, I first run a query against Google using wget to pull results. I then grep to find the result line, use sed to filter out everything before the answer, and then use sed again to filter out everything after the answer. I'm sure these utilities could have been used more elegantly, but this was quick and semantically logical.

Genius!  Gets my vote for best solution too! :)

---

### Post by rejekt on 2006-12-17
This idea is very awesome, and I just checked out this area of the forums. Maybe I'll get around to adding something to this challenge, but I look forward to future challenges to come. :)

---

### Post by utab on 2006-12-17
#include "io_preamble.h"


string num2string(const int& num){
        map<int,string> MAP;
        string literal;

        MAP[0]="zero";MAP[1]="one";MAP[2]="two";MAP[3]="three";MAP[4]="four";MAP[5]="five";
        MAP[6]="six";MAP[7]="seven";MAP[8]="eight";MAP[9]="nine";MAP[10]="ten";MAP[11]="eleven";
        MAP[12]="twelfe";MAP[13]="thirteen";MAP[14]="fourteen";MAP[15]="fifteen";MAP[16]="sixteen";
        MAP[17]="seventeen";MAP[18]="eighteen";MAP[19]="nineteen";MAP[20]="twenty";MAP[30]="thirthy";
        MAP[40]="fourty";MAP[50]="fifty";MAP[60]="sixty"; MAP[70]="seventy";MAP[80]="eighty";
        MAP[90]="ninety";

        int first=num/100;
        int rest=num%100;
        //cout << first << " " << rest << endl;
        map<int,string>::const_iterator it;
        if (first!=0){
                it=MAP.find(first);
                literal+=(it->second+" hundred ");
        }
        if (rest <= 20){
                it=MAP.find(rest);
                literal+=(it->second+" ");
        }
        if (rest > 20){
                        if(rest%10!=0){
                                int first=rest/10;
                                int res=rest%10;
                                it=MAP.find(first*10);
                                literal+=(it->second + " ");
                                it=MAP.find(res);
                                literal+=(it->second + " ");
                        }
                        else{
                                it=MAP.find(rest);
                                literal+=(it->second + " ");
                        }
        }

        return literal;
}

string parse2string(double & num){
        string str;
        map<int,string> map_digits;
        map_digits[0]="";map_digits[1]="thousand";map_digits[2]="million";map_digits[3]="billion";map_digits[4]="trillion";
        vector<string> str_values;
        vector<int> a;
        while(fmod(num,1000.0)){
                a.push_back(int(fmod(num,1000.0)));
                num=(num-fmod(num,1000.0))/1000.0;
        }
        vector<int>::const_iterator iter=a.begin();
        for(int i=0;i!=a.size(),iter!=a.end();++i,++iter)
                str_values.push_back(num2string(*iter)+((map_digits.find(int(i)))->second));
        for(vector<string>::const_reverse_iterator riter=str_values.rbegin();riter!=str_values.rend();++riter)
                str+=*riter;
        return str;
}

int main(){
        double t=788998.0;
        string values=parse2string(t);
        cout << values << endl;
        return EXIT_SUCCESS;
}


Have not tested a lot though. Output of us debt is

eight trillionsix hundred sixty five billionthree hundred fifty two millionsixty seven thousandnine hundred seven

---

### Post by slash2314 on 2006-12-17
```

def get_each_category(number):
    types = {'trillion':0,'billion':0,'million':0,'thousand':0,'hundred':0,'ten':0,'one':0}
    while number>0:
        if number>=1000000000000:
            types['trillion']+= number / 1000000000000
            number-=1000000000000*(number / 1000000000000)
        if number>=1000000000:
            types['billion']+= number / 1000000000
            number-=1000000000*(number /1000000000)
        if number>=1000000:
            types['million']+= number / 1000000
            number-=1000000*(number / 1000000)
        elif number>=1000:
            types['thousand']+= number / 1000
            number-=1000 *(number /1000)
        elif number>=100:
            types['hundred']+= number / 100
            number-=100*(number /100)
        elif number>=10:
            types['ten']+= number / 10
            number-=10 *(number /10)
        elif number>=1:
            types['one']+= number / 1
            number-=1*(number/1)
    return types
def num2word(num):
    word_string = ''
    words = {10:'ten',9:'nine',8:'eight',7:'seven',6:'six',5:'five',4:'four',3:'three',2:'two',1:'one'}
    below_hundred_tens = {9:'ninty',8:'eighty',7:'seventy',6:'sixty',5:'fifty',4:'fourty',3:'thirty',2:'twenty'}
    teens = {11:'eleven',12:'twelve',13:'thirteen',14:'fourteen',15:'fifteen',16:'sixteen',17:'seventeen',18:'eighteen',19:'nineteen'}
    if num>=100:
        word_string+=words[int(str(num)[0])]+'  hundred  '
        num-=int(str(num)[0])*100
    if num>=20:
        word_string+=below_hundred_tens[int(str(num)[0])]
        num-= int(str(num)[0])*10
        if num>0:
            word_string+='-'
    if num>10 and num<20:
        word_string+=teens[num]
        num-= num

    if num<=10 and num>0:
        word_string+= words[num]
    return word_string
while True:
    number = int(input("enter number:"))
    if number>0 and number<=999999999999999:
        break
    elif number==0:
        print 'zero'
        break
    else:
        print 'please enter a number greater than or equal to zero'
categories = get_each_category(number)
if categories['trillion']>=1:
    print num2word(categories['trillion'])+'  trillion',
if categories['billion']>=1:
    print num2word(categories['billion'])+'  billion',
if categories['million']>=1:
    print num2word(categories['million'])+'  million',
if categories['thousand']>=1:
    print num2word(categories['thousand'])+'  thousand',
if categories['hundred']>=1:
    print num2word(categories['hundred'])+'  hundred',
if categories['ten']>0 or categories['one']>0:
    print num2word(int((categories['ten']*10)+categories['one'])),

```

Using 8665352067907 the output was
eight  trillion six  hundred  sixty-five  billion three  hundred  fifty-two  million sixty-seven  thousand nine  hundred seven

---

### Post by maddog39 on 2006-12-17
Hmm.. tomorrow Im going to write me a PHP command line program for this. Using a different approach, and if i really want to get interesting, maybe a GTK+ GUI with that too. :D

---

### Post by meng on 2006-12-22
Thanks to everyone who contributed. I also thought the googling solution was ingenious.

As I said previously, I don't want to pick a "winner", participation is its own reward (yeah yeah), but I'm wondering if there is to be a new challenge this week? Has anyone volunteered to set a problem for us to consider over Christmas/Hanukkah/Kwanzaa/Solstice?

Otherwise, I volunteer jayamef.

---

### Post by studiesrule on 2006-12-22
aww... man, jayamef's entry was just awesome. I can't even think of anything to top that (at least that I can do). I totally vote for him.

---

### Post by jayemef on 2006-12-22
Sure, will do.

Thanks for the nomination. Wasn't sure if Google was considered an "outside library" or not :D.

---

