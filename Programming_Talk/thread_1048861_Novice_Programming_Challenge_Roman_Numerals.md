---
title: "Novice Programming Challenge: Roman Numerals"
date: 2009-01-23
forum: Programming Talk
---

### Post by JupiterV2 on 2009-01-23
**Intended Audience:**

Novice programmers with little experience.

That being said, anyone is free to post code. It would be a helpful demonstration for novices.

**Prerequisites:**

At the very least, a basic knowledge of your language of choice. The purpose of this task to allow you to experiment with your problem solving skills rather than your expertise with any particular language. That being said, you will likely need more training beyond just "Hello, World!"

**Task:**

1) Create a program which converts *base 10* numbers to its' Roman numeral equivalent. You may design any kind of user interface you choose but a basic command line UI is probably preferable. If you are not familiar with Roman numerals there are plenty of resources on the net. It is part of this task to research how the system works without help from anyone here.

2) You must be able to convert to a minimum number of 3999. Due to restrictions in terminal text output, it is unlikely you will be able to output the result of larger numbers in a meaningful way.

3) Make sure you account for poor user input and provide proper error messages in response.

To make sure your program works, you may use the following control numbers, and their results, to compare against:

```
  24: XXIV
 128: CXXVIII
 572: DLXXII
3999: MMMCMXCIX
```

**Restrictions:**

You may not use, or at least it's highly discouraged, built-in functions of a language that solves the task for you. Lisp's format, for example. The purpose of this task is for YOU to figure out how to do the conversion.

**Scoring:**

None. This is simply to challenge yourself and be reviewed by your peers.

**Language Restrictions:**

None.

[CHANGELOG]
* Added restrictions section.
* Modified Audience section.
[/CHANGELOG]

---

### Post by eightmillion on 2009-01-24
This challenge is pretty easy, so I went for obfuscation. A bit of a harder challenge would be converting Roman numerals to decimal and/or converting fractions to the Roman duodecimal system.

```
#!/usr/bin/env python

romanize = lambda y,x=[],nums={ 1000:"M",900:"CM",500:"D",400:"CD",100:"C",90:"XC",50:"L",40:"XL",10:"X",9:"IX",5:"V",4:"IV",1:"I"}: (lambda
ry=x.__delslice__(0,40),ro=(lambda : map(lambda g,r=lambda b:x.append(y[-1]/b),t=lambda v:y.append(y[-1]%v):map(eval,["r(g)","t(g)"])
,sorted(nums.keys())[::-1]))():"".join(map(lambda fg: map(lambda ht: nums[ht],sorted(nums.keys())[::-1])[fg]
* x[fg],range(len(x)))))()

def main():
    while True:
        number = raw_input("Please enter a number between 1 and 5000 to convert to Roman numerals or the word \"exit\" to leave: ")
        if number.lower() == 'exit': exit()
        try: number = int(number)
        except:
            print "%s is not a valid number. Please try again" % number, "\n"
            continue
        if number > 5000:
            print "%s is too high. Please try again" % number, "\n"
            continue
        if number <= 0:
            print "%s is too low. Please try again" % number, "\n"
            continue
        print "%d  :  %s" % (number,romanize([number])), "\n"

if __name__=='__main__':
    main()

```

Or, here's a one line version that doesn't do any checking, but is still pretty cool:
```
python -c 'while True: print (lambda y,x=[],nums={ 1000:"M",900:"CM",500:"D",400:"CD",100:"C",90:"XC",
50:"L",40:"XL",10:"X",9:"IX",5:"V",4:"IV",1:"I"}: (lambda ro=(lambda : map(lambda g,r=lambda b:x.append(
y[-1]/b),t=lambda v:y.append(y[-1]%v):map(eval,["r(g)","t(g)"]),sorted(nums.keys())[::-1]))():"".join(
map(lambda fg: map(lambda ht: nums[ht],sorted(nums.keys())[::-1])[fg] * x[fg],range(len(x)))))())([int(
raw_input("Please enter a number between 1 and 4000: "))])'

```

---

### Post by maximinus_uk on 2009-01-24
Trivial in Lisp:

```
(format t "~@R" 572)

DLXXII
```

As the previous poster said, going the other way round would be trickier :p

---

### Post by maximinus_uk on 2009-01-24
God is probably killing fluffy bunnies for me right now as I enter this super-duper quick hack. If you have clisp installed, you just need this as a bash file:

```
#!/bin/bash

echo '(if (and (>' $1 '0) (<' $1 '4000)) (format t "~@R"' $1 ') (format t "Out of range"))' > code.lisp
clisp code.lisp
rm code.lisp

```

```
sparky@laptop:~/code$ ./roman 3478
MMMCDLXXVIII

```

I know!! It's late (here at least) and I'm drunk. But it does do the job!

---

### Post by sujoy on 2009-01-24
wow, first submit in a challenge ever :)

```
#!/usr/bin/env perl

use warnings;
use strict;

my ($key,$value,$num);
my $romanform="";
my %romans = (1000,'M',900,'CM',500,'D',400,'CD',100,'C',90,'XC',50,'L',40,'XL',10,'X',9,'IX',5,'V',4,'IV',1,'I');
print "enter a number between 1 and 4999 :: ";
chomp (my $number = <STDIN>);
$num=$number;
while ($num > 0) {
	foreach $key (sort {$b <=> $a} keys %romans) {
		if ($num >= $key) {
			$romanform .= $romans{$key};
			$num -= $key;
			last;
		}		
	}
}

print "roman form of $number is $romanform\n";
```

---

### Post by JupiterV2 on 2009-01-24
> **eightmillion said:**
> This challenge is pretty easy, so I went for obfuscation. A bit of a harder challenge would be converting Roman numerals to decimal and/or converting fractions to the Roman duodecimal system.

The intention of this task was to be easy. That being said, who says that the next challenge wasn't to do exactly what you suggest? ;)

---

### Post by JupiterV2 on 2009-01-24
> **maximinus_uk said:**
> Trivial in Lisp:

```
(format t "~@R" 572)

DLXXII
```

As the previous poster said, going the other way round would be trickier :p

I probably should have stated that you can't use built-in functions within a language which automatically does the task for you... :) I'll edit the challenge now to reflect that.

---

### Post by pp. on 2009-01-24
> **JupiterV2 said:**
> ..should have stated that you can't use built-in functions ..

That was my first reaction, too. However, seeing how finding the function(s) appropriate to a given task can be quite daunting, too, I'm not so sure any more.

Why not allow built-in functions, too, while manually coding a correct solution gives twice the number of points?

---

### Post by eightmillion on 2009-01-24
Here's a ruby version that I just wrote.

```

#!/usr/bin/env ruby                           

def romanize(input)
    ints = [1000,900,500,400,100,90,50,40,10,9,5,4,1]
    nums = ['M','CM','D','CD','C','XC','L','XL','X','IX','V','IV','I']
    result = []
    for i in 0...ints.length
        count = input / ints[i]
        result << nums[i] * count
        input -= ints[i] * count
    end
    result.join ''
end

while true
    print "Please enter a number between 1 and 4999: "
    input = gets.chomp
    if input == 'exit'
        exit
    end
    begin
        input = Integer(input)
    rescue ArgumentError
        puts "#{input} is not a valid number. Please try again."
        next
    end
    if input < 0 or input > 5000
        puts "#{input} is out of range. Please try again."
        next
    end
    puts romanize(input)
end

```

---

### Post by Caduceus on 2009-01-24
> **eightmillion said:**
> Here's a ruby version that I just wrote.

```

#!/usr/bin/env ruby                           

def romanize(input)
    ints = [1000,900,500,400,100,90,50,40,10,9,5,4,1]
    nums = ['M','CM','D','CD','C','XC','L','XL','X','IX','V','IV','I']
    result = []
    for i in 0...ints.length
        count = input / ints[i]
        result << nums[i] * count
        input -= ints[i] * count
    end
    result.join ''
end

while true
    print "Please enter a number between 1 and 4999: "
    input = gets.chomp
    if input == 'exit'
        exit
    end
    begin
        input = Integer(input)
    rescue ArgumentError
        puts "#{input} is not a valid number. Please try again."
        next
    end
    if input < 0 or input > 5000
        puts "#{input} is out of range. Please try again."
        next
    end
    puts romanize(input)
end

```

+1 Was hoping there would be a Ruby solution I could learn from. Out of curiosity, why did you use two arrays instead of a hash? Was thinking for mine I'd go on the lines of

```


Roman_Numerals =
{ 
  1 => "I",
  2 => "II",
  3 => "III",
  4 => "IV"
}

```

And so on. Any advantages in using arrays?

Cheers

---

### Post by eightmillion on 2009-01-24
> **Caduceus said:**
> +1 Was hoping there would be a Ruby solution I could learn from. Out of curiosity, why did you use two arrays instead of a hash? Was thinking for mine I'd go on the lines of

And so on. Any advantages in using arrays?

Cheers

No real advantage or disadvantage to using arrays, besides that it's easier to type. You could do it many different ways. For instance:

```
def romanize(input)
    nums = { 1000 => "M", 900 => "CM", 500 => "D", 400 => "CD", 100 => "C", 90  => "XC",
      50  => "L", 40  => "XL", 10  => "X", 9 => "IX", 5   => "V", 4   => "IV", 1   => "I" }
    result = []
    nums.keys.sort.reverse.each do
        |i|
        count, input = input.divmod(i)
        result << nums[i] * count
    end
    result.join ''
end
```

---

