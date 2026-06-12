---
title: "&quot;Check the Number is Prime&quot; in every Programming Language"
date: 2008-10-07
forum: Programming Talk
---

### Post by Canis familiaris on 2008-10-07
First of all my apologies for literally stealing the idea from [this thread]("http://ubuntuforums.org/showthread.php?t=497579") which I found very interesting. However a "Hello Ubuntu" program will lack the concept of conditions and iterations, so I wondered it would be great to have a thread which would showcase these concepts in every programming language. So This is the thread for program which will:
(1) Get a number as User Input.
(2) Determine whether the number is Prime or Not and hence display the output.
I guess it would be interesting to see :), particularly how iterations are implmented in programming languages which do not have loops.
Also Rules:
(1) Do Not Use a Built in Function for determining a prime.
(2) The code should be clean.
(3) Use [this site]("http://www.challenge-you.com/bbcode") so that you can use the [noparse][CODE][/noparse] tags to have syntax highlighting. Unfortunately I don't think [noparse][PHP][/noparse] tag would really suffice IMO except for PHP of course.
(4) You can post in languages already posted, but a different algorithm would be appreciated.
(5) Please specify the programming language.

Thanks.

---

### Post by Canis familiaris on 2008-10-07
My Entries:
[SIZE="6"]Python[/SIZE]

```
[color=#408080]*#!/usr/bin/python*[/color]
num [color=#666666]=[/color] [color=#008000]input[/color]([color=#BA2121]'Enter the number which you wish to determine it is prime: '[/color])

[color=#008000]**if**[/color] num [color=#666666]<[/color] [color=#666666]2[/color]:
	[color=#008000]**print**[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number"[/color], num, [color=#BA2121]" is not a prime!"[/color]
[color=#008000]**else**[/color]:
	[color=#008000]**for**[/color] div [color=#AA22FF]**in**[/color] [color=#008000]range[/color]([color=#666666]2[/color], (num[color=#666666]/[/color][color=#666666]2[/color])[color=#666666]+[/color][color=#666666]1[/color]):
		[color=#008000]**if**[/color] num[color=#666666]%[/color]div[color=#666666]==[/color][color=#666666]0[/color]:
			[color=#008000]**print**[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number"[/color], num, [color=#BA2121]" is not a prime!"[/color]
			[color=#008000]**break**[/color]
	[color=#008000]**else**[/color]:
		[color=#008000]**print**[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number"[/color], num, [color=#BA2121]" is a prime!"[/color]

```

[SIZE="6"]C[/SIZE]
```
[color=#BC7A00]#include<stdio.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color]()
{
	[color=#B00040]int[/color] div;
	[color=#B00040]int[/color] num;
	
	printf([color=#BA2121]"Enter a number: "[/color]);
	scanf([color=#BA2121]"%d"[/color], [color=#666666]&[/color]num);
	
	[color=#008000]**if**[/color](num[color=#666666]>=[/color][color=#666666]2[/color])
		[color=#008000]**for**[/color](div[color=#666666]=[/color][color=#666666]2[/color]; div [color=#666666]<=[/color] num[color=#666666]/[/color][color=#666666]2[/color]; div[color=#666666]++[/color])
			[color=#008000]**if**[/color]((num[color=#666666]%[/color]div)[color=#666666]==[/color][color=#666666]0[/color])
				[color=#008000]**break**[/color];
				
	[color=#008000]**if**[/color](num[color=#666666]>[/color][color=#666666]1[/color] [color=#666666]&&[/color] ([color=#666666]![/color](div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color])))
		printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The number %d is a prime."[/color], num);
	[color=#008000]**else**[/color]	
		printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The number %d is not a prime"[/color], num);
		
	[color=#008000]**return**[/color] [color=#666666]0[/color];			
}
	

```

[SIZE="6"]C++[/SIZE]
```
[color=#BC7A00]#include<iostream>
[/color][color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

[color=#B00040]int[/color] main()
{
	[color=#B00040]int[/color] div;
	[color=#B00040]int[/color] num;
	
	cout[color=#666666]<<[/color][color=#BA2121]"Enter a number: "[/color];
	cin[color=#666666]>>[/color]num;
	
	[color=#008000]**if**[/color](num[color=#666666]>=[/color][color=#666666]2[/color])
		[color=#008000]**for**[/color](div[color=#666666]=[/color][color=#666666]2[/color]; div [color=#666666]<=[/color] num[color=#666666]/[/color][color=#666666]2[/color]; div[color=#666666]++[/color])
			[color=#008000]**if**[/color]((num[color=#666666]%[/color]div)[color=#666666]==[/color][color=#666666]0[/color])
				[color=#008000]**break**[/color];
				
	[color=#008000]**if**[/color](num[color=#666666]>[/color][color=#666666]1[/color] [color=#666666]&&[/color] ([color=#666666]![/color](div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color])))
		cout[color=#666666]<<[/color][color=#BA2121]"The number "[/color][color=#666666]<<[/color]num[color=#666666]<<[/color][color=#BA2121]" is a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
	[color=#008000]**else**[/color]	
		cout[color=#666666]<<[/color][color=#BA2121]"The number "[/color][color=#666666]<<[/color]num[color=#666666]<<[/color][color=#BA2121]" is not a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
	
		
	[color=#008000]**return**[/color] [color=#666666]0[/color];			
}

```
[SIZE=4]Special Thanks to Reiger for correcting the Code in C and C++[/SIZE]


I am a newbie in programming, particularly Python, so please highlight my mistakes and give tips.

---

### Post by Borusa on 2008-10-07
Just a note - you only need to go up to the square root of the number, not above (well, for the sake of your code, one above the square root will make better sense).

Ideally, you would only need to do the division for prime numbers below the square root of the number, but I can't work out a way of doing that that's actually less expensive than doing it your way.

---

### Post by Canis familiaris on 2008-10-07
> **Borusa said:**
> Just a note - you only need to go up to the square root of the number, not above (well, for the sake of your code, one above the square root will make better sense).

Ideally, you would only need to do the division for prime numbers below the square root of the number, but I can't work out a way of doing that that's actually less expensive than doing it your way.

Thanks but I don't think it will make much difference since the loop will terminate when it finds the lowest factor.
Good Idea, neverthless.

Though I think the best implementation would be the loop to list prime number and check the divisibility. This would result in a much more efficient cycle. But I am not sure how to implement it.

> [SIZE="6"]Python[/SIZE]
```
[color=#408080]*#!/usr/bin/python*[/color]
num [color=#666666]=[/color] [color=#008000]input[/color]([color=#BA2121]'Enter the number which you wish to determine it is prime: '[/color])

[color=#008000]**for**[/color] div [color=#AA22FF]**in**[/color] [color=#008000]range[/color]([color=#666666]2[/color], (num[color=#666666]/[/color][color=#666666]2[/color])[color=#666666]+[/color][color=#666666]1[/color]):
	[color=#008000]**if**[/color] num[color=#666666]%[/color]div[color=#666666]==[/color][color=#666666]0[/color]:
		[color=#008000]**print**[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number"[/color], num, [color=#BA2121]" is not a prime!"[/color]
		[color=#008000]**break**[/color]
[color=#008000]**else**[/color]:
	[color=#008000]**print**[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number"[/color], num, [color=#BA2121]" is a prime!"[/color]
	

```
Also I was wondering is there a way to have the last number in the range() to be inclusive rather than exclusive in Python. I am not really liking  the statement (num/2)+1.

---

### Post by Reiger on 2008-10-07
A quick [SIZE="3"]**Haskell**[/SIZE] version:
```
[color=#008000]**module**[/color] [color=#0000FF]**Test**[/color] [color=#008000]**where**[/color]
[color=#008000]**import**[/color] [color=#0000FF]**Char**[/color]

[color=#0000FF]getInput[/color] i [color=#AA22FF]**=**[/color] (putStrLn i) [color=#666666]>>[/color] getLine

[color=#0000FF]run[/color] i [color=#AA22FF]**=**[/color] [color=#008000]**do**[/color]
        s [color=#AA22FF]**<-**[/color] getInput i
        [color=#008000]**if**[/color] (all isDigit s)
          [color=#008000]**then**[/color] (return (read s [color=#AA22FF]**::**[/color] [color=#B00040]Integer[/color]))
          [color=#008000]**else**[/color] (run [color=#BA2121]"That's not a Positive Integer, and therefore it cannot possibly be prime! Please try again:"[/color])

[color=#0000FF]primes[/color] (x[color=#B00040]:[/color]xs) [color=#AA22FF]**=**[/color] x [color=#B00040]:[/color] ( primes [color=#666666]$[/color] filter (`isRelativePrimeTo` x) xs )
[color=#0000FF]primes[/color]  x         [color=#AA22FF]**=**[/color] x

[color=#0000FF]isRelativePrimeTo[/color] [color=#AA22FF]**=**[/color] [color=#0000FF]\[/color]x y [color=#AA22FF]**->**[/color] x `mod` y [color=#666666]/=[/color] [color=#666666]0[/color]


[color=#0000FF]isPrime[/color] q [color=#AA22FF]**=**[/color] and [color=#666666]$[/color] map (q `isRelativePrimeTo`) [color=#666666]$[/color] primes [color=#666666]$[/color] [[color=#666666]2[/color][color=#666666]..[/color](floor [color=#666666]$[/color] sqrt [color=#666666]$[/color] fromInteger q)]

[color=#0000FF]main[/color] [color=#AA22FF]**=**[/color]  [color=#008000]**do**[/color]
        q [color=#AA22FF]**<-**[/color] (run [color=#BA2121]"Please enter the number which might be prime:"[/color])
        [color=#008000]**if**[/color] ((q[color=#666666]>[/color][color=#666666]1[/color]) [color=#666666]&&[/color] (isPrime q))
          [color=#008000]**then**[/color] (putStrLn [color=#666666]$[/color] [color=#BA2121]"Indeed, "[/color][color=#666666]++[/color](show q)[color=#666666]++[/color][color=#BA2121]" is prime!"[/color])
          [color=#008000]**else**[/color] (putStrLn [color=#666666]$[/color] [color=#BA2121]"No, "[/color][color=#666666]++[/color](show q)[color=#666666]++[/color][color=#BA2121]" is not prime!"[/color])

```
Optimised a little. ;)

---

### Post by Idefix82 on 2008-10-07
In the C and C++ versions you are only checking whether the number is even. You want to replace num%2 by num%dev.

---

### Post by Canis familiaris on 2008-10-07
> **Idefix82 said:**
> In the C and C++ versions you are only checking whether the number is even. You want to replace num%2 by num%dev.

Oops! My mistake. I think I posted the wrong Code. 
I guess this is some indication I'm out of practice.
:P

---

### Post by geirha on 2008-10-07
```

#!/bin/bash

# Simple way of approximating the square root using integer arithmetics
sqrt() # $1 - number
{
    local i=1 j=1 n=$1
    while (( i*i <= n )); do
        ((j=i, i++))
    done
    echo "$j"
}

isprime() # $1 - number
{
    local i=3 n=$1 h=0

    # Only considering 2 or greater
    (( n >= 2 )) || return

    # Trivial cases
    (( n == 2 || n == 3 )) && return

    (( n % 2 == 0 )) && return 1
    h=$(( $(sqrt "$n") + 1 ))
    while (( i < h )); do
        (( n % i == 0 )) && return 1
        (( i += 2 ))
    done
    return 0
}


# If no arguments are given, prompt for an integer
if (( $# == 0 )); then 
    read -p "Enter integer number: " n || exit
else
    n=$1
fi

if isprime "$n"; then
    echo "$n is prime"
else
    echo "$n is not prime"
fi

```

---

### Post by slavik on 2008-10-07
Perl. :)

```

#!/usr/bin/perl
use strict;
use warnings;

sub isprime {
  my $num = shift;
  if ($num < 2) return false;
  if ($num == 2) return true;
  else for (my $i = 2; $i < sqrt($num); $i++) { if ($num % $i == 0) return false; }
  return true;
}

while (<>) {
  if (isprime($_)) {
    print $_ . " is prime\n";
  }
  else print $_ . " is not prime\n";
}

```

---

### Post by kknd on 2008-10-07
**Lua**

```
[color=#008000]**local**[/color] number [color=#666666]=[/color] [color=#008000]io.read[/color]([color=#BA2121]"[/color][color=#BA2121]*n"[/color])
[color=#008000]**local**[/color] isPrime [color=#666666]=[/color] [color=#008000]**true**[/color]

[color=#008000]**for**[/color] i [color=#666666]=[/color] [color=#666666]2[/color], [color=#008000]math.sqrt[/color](number) [color=#008000]**do**[/color]
	[color=#008000]**if**[/color] number [color=#666666]%[/color] i [color=#666666]==[/color] [color=#666666]0[/color] [color=#008000]**then**[/color]
		isPrime [color=#666666]=[/color] [color=#008000]**false**[/color]
		[color=#008000]**break**[/color]
	[color=#008000]**end**[/color]
[color=#008000]**end**[/color]

[color=#008000]**if**[/color] isPrime [color=#008000]**then**[/color] [color=#008000]print[/color]([color=#BA2121]"[/color][color=#BA2121]Is prime!"[/color]) [color=#008000]**else**[/color] [color=#008000]print[/color]([color=#BA2121]"[/color][color=#BA2121]Isn't prime!"[/color]) [color=#008000]**end**[/color]

```

---

### Post by jespdj on 2008-10-07
[SIZE="6"]Ruby[/SIZE]
```
[color=#408080]*#!/usr/bin/env ruby*[/color]

[color=#008000]**class**[/color] [color=#0000FF]**PrimeGen**[/color]
    [color=#008000]attr_reader[/color] [color=#19177C]:primes[/color]

    [color=#008000]**def**[/color] [color=#0000FF]initialize[/color]
        [color=#19177C]@primes[/color] [color=#666666]=[/color] [color=#666666][[/color][color=#666666]2[/color], [color=#666666]3[/color][color=#666666]][/color]
    [color=#008000]**end**[/color]

    [color=#008000]**def**[/color] [color=#0000FF]generate_next[/color]
        [color=#008000]**def**[/color] [color=#0000FF]check_prime[/color](n)
            limit [color=#666666]=[/color] [color=#880000]Math[/color][color=#666666].[/color]sqrt(n)[color=#666666].[/color]ceil
            [color=#19177C]@primes[/color][color=#666666].[/color]each {[color=#666666]|[/color][color=#008000]p[/color][color=#666666]|[/color] [color=#008000]**break**[/color] [color=#008000]false[/color] [color=#008000]**if**[/color] n [color=#666666]%[/color] [color=#008000]p[/color] [color=#666666]==[/color] [color=#666666]0[/color]; [color=#008000]**break**[/color] [color=#008000]true[/color] [color=#008000]**unless**[/color] [color=#008000]p[/color] [color=#666666]<[/color] limit }
        [color=#008000]**end**[/color]

        n [color=#666666]=[/color] [color=#19177C]@primes[/color][color=#666666][-[/color][color=#666666]1[/color][color=#666666]][/color] [color=#666666]+[/color] [color=#666666]2[/color]
        n [color=#666666]+=[/color] [color=#666666]2[/color] [color=#008000]**until**[/color] check_prime(n)
        [color=#19177C]@primes[/color] [color=#666666]<<[/color] n
        [color=#008000]**return**[/color] n
    [color=#008000]**end**[/color]
[color=#008000]**end**[/color]

[color=#008000]print[/color] [color=#BA2121]"Enter a number: "[/color]
num [color=#666666]=[/color] [color=#008000]gets[/color][color=#666666].[/color]to_i

[color=#008000]p[/color] [color=#666666]=[/color] [color=#880000]PrimeGen[/color][color=#666666].[/color]new
[color=#008000]p[/color][color=#666666].[/color]generate_next [color=#008000]**until**[/color] [color=#008000]p[/color][color=#666666].[/color]primes[color=#666666][-[/color][color=#666666]1[/color][color=#666666]][/color] [color=#666666]>=[/color] num

[color=#008000]**if**[/color] num [color=#666666]==[/color] [color=#666666]2[/color] [color=#AA22FF]**or**[/color] [color=#008000]p[/color][color=#666666].[/color]primes[color=#666666][-[/color][color=#666666]1[/color][color=#666666]][/color] [color=#666666]==[/color] num [color=#008000]**then**[/color] [color=#008000]puts[/color] [color=#BA2121]"[/color][color=#BB6688]**#{**[/color]num[color=#BB6688]**}**[/color][color=#BA2121] is prime"[/color] [color=#008000]**else**[/color] [color=#008000]puts[/color] [color=#BA2121]"[/color][color=#BB6688]**#{**[/color]num[color=#BB6688]**}**[/color][color=#BA2121] is composite"[/color] [color=#008000]**end**[/color]

```
Partly copied and pasted from one of my [Project Euler](http://projecteuler.net/) programs.

---

### Post by NovaAesa on 2008-10-07
[SIZE="7"]Befunge[/SIZE]

```
[color=#666666]25[/color][color=#19177C]v[/color] [color=#19177C]v[/color] [color=#008000]**p**[/color] [color=#666666]05[/color] [color=#666666]+[/color][color=#666666]1[/color][color=#008000]**g**[/color] [color=#666666]05[/color] [color=#19177C]<[/color]
[color=#19177C]v[/color][color=#666666]0[/color][color=#19177C]<[/color]       [color=#19177C]>[/color][color=#008000]:[/color] [color=#666666]50[/color] [color=#008000]**g**[/color][color=#666666]%[/color][color=#008000]**|**[/color]
[color=#19177C]>[/color][color=#008000]**p**[/color][color=#19177C]>[/color][color=#008000]**&**[/color][color=#19177C]>[/color][color=#008000]:[/color][color=#666666]50[/color][color=#008000]**g**[/color][color=#666666]`[/color][color=#008000]**|@**[/color][color=#008000],,[/color][color=#BA2121]"!p"[/color][color=#19177C]<[/color]
[color=#008000]**@**[/color] [color=#008000],[/color] [color=#BA2121]"p"[/color]   [color=#19177C]<[/color]

```

Gotta love those esoteric languages (and yes, I did write this code myself).

---

### Post by Reiger on 2008-10-07
> **Anurag_panda said:**
> My Entries:
[SIZE="6"]C[/SIZE]
```
[color=#BC7A00]#include<stdio.h>
[/color]
[color=#B00040]int[/color] main()
{
	[color=#B00040]int[/color] div;
	[color=#B00040]int[/color] num;
	
	printf([color=#BA2121]"Enter a number: "[/color]);
	scanf([color=#BA2121]"%d"[/color], [color=#666666]&[/color]num);
	
	
	[color=#008000]**for**[/color](div[color=#666666]=[/color][color=#666666]2[/color]; div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color]; div[color=#666666]++[/color])
	{
		[color=#008000]**if**[/color](num[color=#666666]%[/color]div[color=#666666]==[/color][color=#666666]0[/color])
		{
			printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number %d is not a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], num);
			[color=#008000]**break**[/color];
		}
	}
	
	[color=#008000]**if**[/color]([color=#666666]![/color](div[color=#666666]<[/color]num[color=#666666]/[/color][color=#666666]2[/color]))
		printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number %d is a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], num);
		
	[color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

[SIZE="6"]C++[/SIZE]
```

[color=#BC7A00]#include<iostream>
[/color][color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

[color=#B00040]int[/color] main()
{
	[color=#B00040]int[/color] div;
	[color=#B00040]int[/color] num;
	
	cout[color=#666666]<<[/color][color=#BA2121]"Enter a number: "[/color];
	cin[color=#666666]>>[/color]num;
	
	
	[color=#008000]**for**[/color](div[color=#666666]=[/color][color=#666666]2[/color]; div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color]; div[color=#666666]++[/color])
	{
		[color=#008000]**if**[/color](num[color=#666666]%[/color]div[color=#666666]==[/color][color=#666666]0[/color])
		{
			cout[color=#666666]<<[/color][color=#BA2121]"The number "[/color][color=#666666]<<[/color]num[color=#666666]<<[/color][color=#BA2121]" is not a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
			[color=#008000]**break**[/color];
		}
	}
	
	[color=#008000]**if**[/color]([color=#666666]![/color](div[color=#666666]<[/color]num[color=#666666]/[/color][color=#666666]2[/color]))
		cout[color=#666666]<<[/color][color=#BA2121]"The number "[/color][color=#666666]<<[/color]num[color=#666666]<<[/color][color=#BA2121]" is a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
		
	[color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

I am a newbie in programming, particularly Python, so please highlight my mistakes and give tips.

These entries are not 'valid' as they do report incorrect results:
```

prometheus@Bartix:~/Documents$ gcc -o test prime.c
prometheus@Bartix:~/Documents$ chmod +x test
prometheus@Bartix:~/Documents$ ./test
Enter a number: 0

The Number 0 is a prime
prometheus@Bartix:~/Documents$ ./test
Enter a number: 1

The Number 1 is a prime

```

Proved with your C version, but since you apply the same algorith and therefore the same bug to your C++ version; both will not work. The same thing can be shown for negative input. The reason is that you assume all primes will have been filtered out if and only if your for loop has been 'fully' executed, without any forced breaks. But the for loop will never be executed at all if the input is less than 2, yet your if-condition will dutifully ('div' having been set to 2, which is more than the input!) evaluate to true, and hence your program is tricked into believing anything less than 2 is prime.

---

### Post by Canis familiaris on 2008-10-07
> **Reiger said:**
> These entries are not 'valid' as they do report incorrect results:
```

prometheus@Bartix:~/Documents$ gcc -o test prime.c
prometheus@Bartix:~/Documents$ chmod +x test
prometheus@Bartix:~/Documents$ ./test
Enter a number: 0

The Number 0 is a prime
prometheus@Bartix:~/Documents$ ./test
Enter a number: 1

The Number 1 is a prime

```

Proved with your C version, but since you apply the same algorith and therefore the same bug to your C++ version; both will not work. The same thing can be shown for negative input. The reason is that you assume all primes will have been filtered out if and only if your for loop has been 'fully' executed, without any forced breaks. But the for loop will never be executed at all if the input is less than 2, yet your if-condition will dutifully ('div' having been set to 2, which is more than the input!) evaluate to true, and hence your program is tricked into believing anything less than 2 is prime.

Thanks. Noted. Will Correct it.

EDIT: Done. Is it OK Now?

---

### Post by Reiger on 2008-10-07
Ehrm no. As a matter of fact you have now made it explicit that your program should believe everything below 2 is prime:
```

if((!(div<num/2)) || num < 2)

```
Whereas anything below 2 cannot possibly be prime, so I think you meant:
```

if(num>1 && (!(div<num/2)))

```

EDIT: And there's more:
```

prometheus@Bartix:~/Documents$ gcc -o test prime.c
prometheus@Bartix:~/Documents$ chmod +x test
prometheus@Bartix:~/Documents$ ./test
Enter a number: 4

The Number 4 is not a prime

The Number 4 is a prime

```

Previously tested it with 27, which goes OK, but 4 is even so...

```

if(num>1 && (!(div<=num/2)))

```

Should be the condition. Now for a minor touch up:
```
[color=#BC7A00]#include<stdio.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color]()
{
        [color=#B00040]int[/color] div;
        [color=#B00040]int[/color] num;
        
        printf([color=#BA2121]"Enter a number: "[/color]);
        scanf([color=#BA2121]"%d"[/color], [color=#666666]&[/color]num);
        
        [color=#008000]**if**[/color](num[color=#666666]>=[/color][color=#666666]2[/color])
                [color=#008000]**for**[/color](div[color=#666666]=[/color][color=#666666]2[/color]; div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color]; div[color=#666666]++[/color])
                        [color=#008000]**if**[/color](num[color=#666666]%[/color]div[color=#666666]==[/color][color=#666666]0[/color])
                                [color=#008000]**break**[/color];
        
        [color=#008000]**if**[/color](num[color=#666666]>[/color][color=#666666]1[/color] [color=#666666]&&[/color] ([color=#666666]![/color](div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color])))
                printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number %d is a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], num);
        [color=#008000]**else**[/color]
                printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number %d is not a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], num);
        
        [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

EDIT: The touch-up thing is ensuring that the program gives output in the rare (previously broken) cases. For instance, running the programatically-fixed version with input 0 wouldn't yield any output as no printf() call could be reached. So I restructured the code to make all non-primes fall into the else clause.

---

### Post by Canis familiaris on 2008-10-07
> **Reiger said:**
> Ehrm no. As a matter of fact you have now made it explicit that your program should believe everything below 2 is prime:
```

if((!(div<num/2)) || num < 2)

```
Whereas anything below 2 cannot possibly be prime, so I think you meant:
```

if(num>1 && (!(div<num/2)))

```

EDIT: And there's more:
```

prometheus@Bartix:~/Documents$ gcc -o test prime.c
prometheus@Bartix:~/Documents$ chmod +x test
prometheus@Bartix:~/Documents$ ./test
Enter a number: 4

The Number 4 is not a prime

The Number 4 is a prime

```

Previously tested it with 27, which goes OK, but 4 is even so...

```

if(num>1 && (!(div<=num/2)))

```

Should be the condition. Now for a minor touch up:
```
[color=#BC7A00]#include<stdio.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color]()
{
        [color=#B00040]int[/color] div;
        [color=#B00040]int[/color] num;
        
        printf([color=#BA2121]"Enter a number: "[/color]);
        scanf([color=#BA2121]"%d"[/color], [color=#666666]&[/color]num);
        
        [color=#008000]**if**[/color](num[color=#666666]>=[/color][color=#666666]2[/color])
                [color=#008000]**for**[/color](div[color=#666666]=[/color][color=#666666]2[/color]; div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color]; div[color=#666666]++[/color])
                        [color=#008000]**if**[/color](num[color=#666666]%[/color]div[color=#666666]==[/color][color=#666666]0[/color])
                                [color=#008000]**break**[/color];
        
        [color=#008000]**if**[/color](num[color=#666666]>[/color][color=#666666]1[/color] [color=#666666]&&[/color] ([color=#666666]![/color](div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color])))
                printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number %d is a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], num);
        [color=#008000]**else**[/color]
                printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]The Number %d is not a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], num);
        
        [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

EDIT: The touch-up thing is ensuring that the program gives output in the rare (previously broken) cases. For instance, running the programatically-fixed version with input 0 wouldn't yield any output as no printf() call could be reached. So I restructured the code to make all non-primes fall into the else clause.
Thanks. I would also put your algorithm in C++ as well.

---

### Post by Reiger on 2008-10-07
Well your C++ original refuse to compile: gcc spits out more gibberish than I can cope with, given I don't know C++. (I can read some of the code based on my experience with other, similar, languages; but I can't mkae heads or tails from what the GCC says...)
```

/tmp/ccCcmLVO.o: In function `std::__verify_grouping(char const*, unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
prime.cc:(.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
prime.cc:(.text+0x59): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
prime.cc:(.text+0x97): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
prime.cc:(.text+0xdf): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/ccCcmLVO.o: In function `__static_initialization_and_destruction_0(int, int)':
prime.cc:(.text+0x129): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccCcmLVO.o: In function `__tcf_0':
prime.cc:(.text+0x176): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccCcmLVO.o: In function `main':
prime.cc:(.text+0x199): undefined reference to `std::cout'
prime.cc:(.text+0x19e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x1ac): undefined reference to `std::cin'
prime.cc:(.text+0x1b1): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
prime.cc:(.text+0x1e5): undefined reference to `std::cout'
prime.cc:(.text+0x1ea): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x1f6): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
prime.cc:(.text+0x206): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x248): undefined reference to `std::cout'
prime.cc:(.text+0x24d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x259): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
prime.cc:(.text+0x269): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccCcmLVO.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

---

### Post by Canis familiaris on 2008-10-07
> **Reiger said:**
> Well your C++ original refuse to compile: gcc spits out more gibberish than I can cope with, given I don't know C++. (I can read some of the code based on my experience with other, similar, languages; but I can't mkae heads or tails from what the GCC says...)
```

/tmp/ccCcmLVO.o: In function `std::__verify_grouping(char const*, unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
prime.cc:(.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
prime.cc:(.text+0x59): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
prime.cc:(.text+0x97): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
prime.cc:(.text+0xdf): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/ccCcmLVO.o: In function `__static_initialization_and_destruction_0(int, int)':
prime.cc:(.text+0x129): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccCcmLVO.o: In function `__tcf_0':
prime.cc:(.text+0x176): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccCcmLVO.o: In function `main':
prime.cc:(.text+0x199): undefined reference to `std::cout'
prime.cc:(.text+0x19e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x1ac): undefined reference to `std::cin'
prime.cc:(.text+0x1b1): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
prime.cc:(.text+0x1e5): undefined reference to `std::cout'
prime.cc:(.text+0x1ea): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x1f6): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
prime.cc:(.text+0x206): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x248): undefined reference to `std::cout'
prime.cc:(.text+0x24d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
prime.cc:(.text+0x259): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
prime.cc:(.text+0x269): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccCcmLVO.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```
Use **g++** to compile the C++ code. g++ is actually gcc called with special C++ libraries.

```
g++ filename -o program
```

---

### Post by Zugzwang on 2008-10-07
> **Reiger said:**
> Well your C++ original refuse to compile: gcc spits out more gibberish than I can cope with, given I don't know C++. (I can read some of the code based on my experience with other, similar, languages; but I can't mkae heads or tails from what the GCC says...)


That's not surprising! The command to compile C++ code is "g++".

---

### Post by Reiger on 2008-10-07
Here you are:

```
[color=#BC7A00]#include<iostream>
[/color][color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

[color=#B00040]int[/color] main()
{
        [color=#B00040]int[/color] div;
        [color=#B00040]int[/color] num;
        
        cout[color=#666666]<<[/color][color=#BA2121]"Enter a number: "[/color];
        cin[color=#666666]>>[/color]num;
        
        [color=#008000]**if**[/color](num[color=#666666]>=[/color][color=#666666]2[/color])
                [color=#008000]**for**[/color](div[color=#666666]=[/color][color=#666666]2[/color]; div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color]; div[color=#666666]++[/color])
                        [color=#008000]**if**[/color](num[color=#666666]%[/color]div[color=#666666]==[/color][color=#666666]0[/color])
                                [color=#008000]**break**[/color];
        
        [color=#008000]**if**[/color](num[color=#666666]>[/color][color=#666666]1[/color] [color=#666666]&&[/color] ([color=#666666]![/color](div[color=#666666]<=[/color]num[color=#666666]/[/color][color=#666666]2[/color])))
                cout[color=#666666]<<[/color][color=#BA2121]"The number "[/color][color=#666666]<<[/color]num[color=#666666]<<[/color][color=#BA2121]" is a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
        [color=#008000]**else**[/color]
                cout[color=#666666]<<[/color][color=#BA2121]"The number "[/color][color=#666666]<<[/color]num[color=#666666]<<[/color][color=#BA2121]" is not a prime[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
        
        [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

---

### Post by snova on 2008-10-07
Well, it's no Sieve of Atkins, but it'll have to do. Compile and run with the number to test as it's argument. It'll give correct results for everything except 1 and negative numbers (you get segfaults for those). The return value is whether it's a prime or not. Keep in mind it's not shell boolean.

```
main(int c,char**v){unsigned int s=atoll(v[1])+1,p=0,m=3;char*a
=malloc(s);for(;p<s;p++)a[p]=1;while(m*m<s){p=m*m;while(p<s){a[p
]=0;p+=m;}m+=2;while(!a[m]&&m*m<s)m+=2;}return s-1%2?a[s-1]:0;}
```

It's not nearly as good as my last piece. :(

---

### Post by nvteighen on 2008-10-07
**Scheme**

The trick here is that we can create a **truly infinite** stream of primes by just giving the rules for the Sieve of Eratosthenes from an infinite stream of integers generated by the rules of Induction Theory.

And then, we just check whether the input is part of the stream or not. When found, it returns "true" (#t), but when the next prime number is bigger than the test case it's obvious that the number is not prime, so it returns #f. If none of both conditions is met, the program continues by demanding more information from the primes stream.

These are the kind of nice things you can do in this language.

```
[COLOR=#408080]*;; A Primality-checker in Scheme*[/COLOR]

[COLOR=#408080]*;; We create a predicate that checks a number for primality. To use it, start*[/COLOR]
[COLOR=#408080]*;; some Scheme interpreter, load this module and type (prime? <number>). If*[/COLOR]
[COLOR=#408080]*;; true, it returns #t and, if false, #f; so, you can use this in a conditional*[/COLOR]
[COLOR=#408080]*;; as any built-in predicate.*[/COLOR] 
([COLOR=#008000]**define **[/COLOR]([COLOR=#0000ff]prime?[/COLOR] [COLOR=#19177c]number[/COLOR])

  [COLOR=#408080]*;; Creates an infinite stream of integers starting from n*[/COLOR]
  ([COLOR=#008000]**define **[/COLOR]([COLOR=#0000ff]int-stream-from[/COLOR] [COLOR=#19177c]n[/COLOR])
    ([COLOR=#0000ff]cons-stream[/COLOR] [COLOR=#19177c]n[/COLOR]
                 ([COLOR=#0000ff]int-stream-from[/COLOR] ([COLOR=#008000]+ [/COLOR][COLOR=#19177c]n[/COLOR] [COLOR=#666666]1[/COLOR]))))
  
  [COLOR=#408080]*;; Checks if y is a divisor of x.*[/COLOR]
  ([COLOR=#008000]**define **[/COLOR]([COLOR=#0000ff]div?[/COLOR] [COLOR=#19177c]x[/COLOR] [COLOR=#19177c]y[/COLOR])
    ([COLOR=#008000]= [/COLOR][COLOR=#666666]0[/COLOR] ([COLOR=#008000]modulo [/COLOR][COLOR=#19177c]x[/COLOR] [COLOR=#19177c]y[/COLOR])))

  [COLOR=#408080]*;; Creates an infinite stream of primes, using the Sieve of Eratosthenes.*[/COLOR]
  ([COLOR=#008000]**define **[/COLOR]([COLOR=#0000ff]eratosthenes[/COLOR] [COLOR=#19177c]row[/COLOR])
    ([COLOR=#0000ff]cons-stream[/COLOR] ([COLOR=#0000ff]stream-car[/COLOR] [COLOR=#19177c]row[/COLOR])
                 ([COLOR=#0000ff]eratosthenes[/COLOR] 
                  ([COLOR=#0000ff]stream-filter[/COLOR] ([COLOR=#008000]**lambda **[/COLOR]([COLOR=#0000ff]x[/COLOR])
                                   ([COLOR=#008000]not [/COLOR]([COLOR=#0000ff]div?[/COLOR] [COLOR=#19177c]x[/COLOR]
                                              ([COLOR=#0000ff]stream-car[/COLOR] [COLOR=#19177c]row[/COLOR]))))
                                 ([COLOR=#0000ff]stream-cdr[/COLOR] [COLOR=#19177c]row[/COLOR])))))

  [COLOR=#408080]*;; And after having defined the auxiliary local procedures, we now code the*[/COLOR]
  [COLOR=#408080]*;; body. It's just a classic, trivial Scheme-ish tail recursion.*[/COLOR]
  ([COLOR=#008000]**let **[/COLOR][COLOR=#19177c]loop[/COLOR] (([COLOR=#0000ff]primes[/COLOR] ([COLOR=#0000ff]eratosthenes[/COLOR] ([COLOR=#0000ff]int-stream-from[/COLOR] [COLOR=#666666]2[/COLOR]))))
    ([COLOR=#008000]**cond **[/COLOR](([COLOR=#008000]< [/COLOR][COLOR=#19177c]number[/COLOR] ([COLOR=#0000ff]stream-car[/COLOR] [COLOR=#19177c]primes[/COLOR]))
           [COLOR=#880000]#f[/COLOR])
          (([COLOR=#008000]= [/COLOR][COLOR=#19177c]number[/COLOR] ([COLOR=#0000ff]stream-car[/COLOR] [COLOR=#19177c]primes[/COLOR]))
           [COLOR=#880000]#t[/COLOR])
          ([COLOR=#008000]**else **[/COLOR]([COLOR=#0000ff]loop[/COLOR] ([COLOR=#0000ff]stream-cdr[/COLOR] [COLOR=#19177c]primes[/COLOR]))))))

```

---

### Post by dribeas on 2008-10-07
> **Borusa said:**
> Ideally, you would only need to do the division for prime numbers below the square root of the number, but I can't work out a way of doing that that's actually less expensive than doing it your way.

While dividing only by prime numbers is hard you can reduce computation time by half by just checking odd numbers (that is, change the loop iteration from i++ to i+=2). Clearly, if the number were divisible by an even number it would surely be divisible by 2, which is the first test.

---

### Post by jimi_hendrix on 2008-10-07
```
[color=#008000]**using**[/color] [color=#0000FF]**System**[/color];

[color=#008000]**namespace**[/color] [color=#0000FF]**IsPrime**[/color]
[color=#008000]**{**[/color]
    [color=#008000]**class**[/color] [color=#0000FF]**Program**[/color]
    [color=#008000]**{**[/color]
        [color=#008000]**static**[/color] [color=#008000]**void**[/color] [color=#0000FF]Main[/color]()
        [color=#008000]**{**[/color]
            [color=#408080][i]//prompt user for input and read it
[/i][/color]            Console.WriteLine([color=#BA2121]"please enter a number to check:"[/color]); 
            [color=#B00040]int[/color] check = Convert.ToInt32(Console.ReadLine());

            [color=#408080][i]//check for the not possible primes
[/i][/color]            [color=#008000]**if**[/color] (check < [color=#666666]2[/color])
            [color=#008000]**{**[/color]
                Console.WriteLine([color=#BA2121]"the number you entered can not be prime"[/color]);
                Console.WriteLine([color=#BA2121]"press any key to exit"[/color]);
                Console.ReadKey(); [color=#408080][i]//pauses the program for the user to read
[/i][/color]                [color=#008000]**return**[/color]; [color=#408080][i]//exits the program
[/i][/color]            [color=#008000]**}**[/color]

            [color=#408080][i]//begin for loop to check for the prime
[/i][/color]            [color=#008000]**for**[/color] ([color=#B00040]int[/color] i = [color=#666666]2[/color]; i < check; i++)
            [color=#008000]**{**[/color]
                
                [color=#008000]**if**[/color] ((check % i) == [color=#666666]0[/color]) [color=#408080][i]//tells user if number is not prime
[/i][/color]                [color=#008000]**{**[/color]
                    Console.WriteLine([color=#BA2121]"the number is not prime"[/color]);
                    Console.WriteLine([color=#BA2121]"press any key to exit..."[/color]);
                    Console.ReadKey();
                    [color=#008000]**return**[/color];
                [color=#008000]**}**[/color]
            [color=#008000]**}**[/color]

            [color=#408080][i]//tells user number is prime
[/i][/color]            Console.WriteLine([color=#BA2121]"the number is prime"[/color]);
            Console.WriteLine([color=#BA2121]"press any key to exit"[/color]);
            Console.ReadKey();
        [color=#008000]**}**[/color]
    [color=#008000]**}**[/color]
[color=#008000]**}**[/color]

```

---

### Post by Reiger on 2008-10-07
> **nvteighen said:**
> **Scheme**

The trick here is that we can create a **truly infinite** stream of primes by just giving the rules for the Sieve of Eratosthenes from an infinite stream of integers generated by the rules of Induction Theory.

And then, we just check whether the input is part of the stream or not. When found, it returns "true" (#t), but when the next prime number is bigger than the test case it's obvious that the number is not prime, so it returns #f. If none of both conditions is met, the program continues by demanding more information from the primes stream.

These are the kind of nice things you can do in this language.


You do *exactly* the same in Lisp as I did in Haskell before I optimised (to reduce the complexity with a factor O(sqrt(n)) ):
```

isPrime q = (q==) $ last $ primes [2..q] {- Generate a list of integers, remove the non-prime numbers, grab the last item in the result list, return if that item is equal to the input (prime!) or not (not-prime!). -}

```

---

### Post by jimi_hendrix on 2008-10-07
```
[color=#008000]**Module**[/color] Module1
    [color=#008000]**Dim**[/color] prime [color=#AA22FF]**As**[/color] [color=#B00040]Integer[/color]
    [color=#008000]**Dim**[/color] isPrime [color=#AA22FF]**As**[/color] [color=#B00040]Boolean[/color] [color=#666666]=[/color] [color=#008000]**False**[/color]
    [color=#008000]**Sub**[/color] Main()
        Console.WriteLine([color=#BA2121]"enter an integer to check"[/color])
        prime [color=#666666]=[/color] Console.ReadLine()

        [color=#008000]**If**[/color] prime [color=#666666]<[/color] [color=#666666]2[/color] [color=#008000]**Then**[/color]
            Console.WriteLine([color=#BA2121]"the number is not possibly prime"[/color])
            Console.WriteLine([color=#BA2121]"press any key to exit"[/color])
            Console.ReadKey()
            System.Environment.Exit([color=#666666]0[/color])
        [color=#008000]**End**[/color] [color=#008000]**If**[/color]


        [color=#008000]**For**[/color] index [color=#AA22FF]**As**[/color] [color=#B00040]Integer[/color] [color=#666666]=[/color] [color=#666666]2[/color] [color=#008000]**To**[/color] (prime [color=#666666]-[/color] [color=#666666]1[/color])

            [color=#008000]**If**[/color] (prime [color=#AA22FF]**Mod**[/color] index) [color=#666666]=[/color] [color=#666666]0[/color] [color=#008000]**Then**[/color]
                isPrime [color=#666666]=[/color] [color=#008000]**False**[/color]
            [color=#008000]**End**[/color] [color=#008000]**If**[/color]
        [color=#008000]**Next**[/color]


        [color=#008000]**If**[/color] isPrime [color=#666666]<>[/color] [color=#008000]**True**[/color] [color=#008000]**Then**[/color]
            Console.WriteLine([color=#BA2121]"the number is prime"[/color])
            Console.WriteLine([color=#BA2121]"press any key to exit"[/color])
            Console.ReadKey()

        [color=#008000]**Else**[/color]
            Console.WriteLine([color=#BA2121]"the number is not prime"[/color])
            Console.WriteLine([color=#BA2121]"press any key to exit"[/color])
            Console.ReadKey()
        [color=#008000]**End**[/color] [color=#008000]**If**[/color]


    [color=#008000]**End**[/color] [color=#008000]**Sub**[/color]

[color=#008000]**End**[/color] [color=#008000]**Module**[/color]

```

---

### Post by dribeas on 2008-10-08
> **jimi_hendrix said:**
> 
```
            [color=#408080][i]//check for the not possible primes
[/i][/color]            [color=#008000]**if**[/color] (check == [color=#666666]0[/color] | check == [color=#666666]1[/color] | check == [color=#666666]2[/color])
            [color=#008000]**{**[/color]
                Console.WriteLine([color=#BA2121]"the number you entered can not be prime"[/color]);

```

:) Small mistake: 2 is definitely a prime number. The same goes with 1, even if I think mathematicians consider it a non-proper prime... anyone cares to clear this point?

Oh, and you should check for negative values (as you did in your VB version)

---

### Post by pp. on 2008-10-08
> **dribeas said:**
> Small mistake: 2 is definitely a prime number. The same goes with 1, even if I think mathematicians consider it a non-proper prime... anyone cares to clear this point?

In that case, every positive integer is a non-proper prime.

A positive odd integer is prime if it can be divided by 1 and itself only.

A positive even integer is prime if it is equal to 2.

---

### Post by Idefix82 on 2008-10-08
**1 is not a prime!!!**
If it was then there would be no unique factorisation into prime factors since 2= 1*2.
"Prime number" is a mathematical term so what the mathematicians consider it to mean is what it means :)

Edit: just to reiterate, there is no such term as "proper prime" and "improper prime".

---

### Post by jimi_hendrix on 2008-10-08
> **pp. said:**
> In that case, every positive integer is a non-proper prime.

A positive odd integer is prime if it can be divided by 1 and itself only.

A positive even integer is prime if it is equal to 2.

> **dribeas said:**
> :) Small mistake: 2 is definitely a prime number. The same goes with 1, even if I think mathematicians consider it a non-proper prime... anyone cares to clear this point?

Oh, and you should check for negative values (as you did in your VB version)

> **Idefix82 said:**
> **1 is not a prime!!!**
If it was then there would be no unique factorisation into prime factors since 2= 1*2.
"Prime number" is a mathematical term so what the mathematicians consider it to mean is what it means :)

Edit: just to reiterate, there is no such term as "proper prime" and "improper prime".

see what happens when you post late at night...fixing it now

---

### Post by jespdj on 2008-10-08
The number 1 is not a prime number.

See [Prime number](http://en.wikipedia.org/wiki/Prime_number) on Wikipedia, it also has some information on why 1 is not a prime number. Basically, if 1 would be a prime number, the [fundamental theorem of arithmetic](http://en.wikipedia.org/wiki/Fundamental_theorem_of_arithmetic) would not be valid.

---

### Post by mosty friedman on 2008-10-08
done in Java
```
[color=#008000]**import**[/color] [color=#0000FF]**java.util.Scanner**[/color][color=#666666];[/color]
[color=#008000]**public**[/color] [color=#008000]**class**[/color] [color=#0000FF]**PrimeTest**[/color]
[color=#666666]{[/color]
 [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]void[/color] [color=#0000FF]isPrime[/color][color=#666666]([/color] [color=#B00040]int[/color] n [color=#666666])[/color] 
    [color=#666666]{[/color]
      [color=#B00040]boolean[/color] prime [color=#666666]=[/color] [color=#008000]**true**[/color][color=#666666];[/color]
      [color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]<[/color] [color=#666666]2[/color] [color=#666666])[/color]
         prime [color=#666666]=[/color] [color=#008000]**false**[/color][color=#666666];[/color]
         
        [color=#008000]**for**[/color][color=#666666]([/color] [color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]2[/color][color=#666666];[/color] i [color=#666666]<[/color] n[color=#666666];[/color] i[color=#666666]++[/color] [color=#666666])[/color]
         [color=#666666]{[/color]
            [color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]%[/color] i [color=#666666]==[/color] [color=#666666]0[/color] [color=#666666])[/color]
              [color=#666666]{[/color]
                prime [color=#666666]=[/color] [color=#008000]**false**[/color][color=#666666];[/color]
                   [color=#008000]**break**[/color][color=#666666];[/color]
              [color=#666666]}[/color]
         [color=#666666]}[/color]
         [color=#008000]**if**[/color][color=#666666]([/color] prime [color=#666666])[/color]
            System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]printf[/color][color=#666666]([/color] [color=#BA2121]"%d %s\n"[/color][color=#666666],[/color] n[color=#666666],[/color] [color=#BA2121]"is a prime number"[/color] [color=#666666]);[/color]
         [color=#008000]**else**[/color]
            System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]printf[/color][color=#666666]([/color] [color=#BA2121]"%d %s\n"[/color][color=#666666],[/color] n[color=#666666],[/color] [color=#BA2121]"is not a prime number"[/color] [color=#666666]);[/color]
     [color=#666666]}[/color]
 
[color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]void[/color] [color=#0000FF]main[/color][color=#666666]([/color] String[color=#666666][][/color]args [color=#666666])[/color]
 [color=#666666]{[/color]
   Scanner sc [color=#666666]=[/color] [color=#008000]**new**[/color] Scanner[color=#666666]([/color] System[color=#666666].[/color][color=#7D9029]in[/color] [color=#666666]);[/color]
   System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color] [color=#BA2121]"enter a number to check if its prime or not"[/color][color=#666666]);[/color]
   [color=#B00040]int[/color] num [color=#666666]=[/color] sc[color=#666666].[/color][color=#7D9029]nextInt[/color][color=#666666]();[/color]
   isPrime[color=#666666]([/color] num [color=#666666]);[/color]
 [color=#666666]}[/color]

[color=#666666]}[/color]

```
any tips or any feedback are appreciated :)

---

### Post by geirha on 2008-10-08
> **mosty friedman said:**
> 
any tips, hints or any feedback is appreciated :)

Instead of checking for 1 or 0, check for less than 2 instead, that way you'll handle negative numbers as well. The task does not mention what to do with negative numbers, so you can treat them as not primes.

---

### Post by mosty friedman on 2008-10-08
> **geirha said:**
> Instead of checking for 1 or 0, check for less than 2 instead, that way you'll handle negative numbers as well. The task does not mention what to do with negative numbers, so you can treat them as not primes.
thanks for that tip..that was a useful one..never payed attention to that

---

### Post by nvteighen on 2008-10-08
> **Reiger said:**
> You do *exactly* the same in Lisp as I did in Haskell before I optimised (to reduce the complexity with a factor O(sqrt(n)) ):
```

isPrime q = (q==) $ last $ primes [2..q] {- Generate a list of integers, remove the non-prime numbers, grab the last item in the result list, return if that item is equal to the input (prime!) or not (not-prime!). -}

```

Well, I never said Scheme is the only nice way to do it... Actually, using an infinite stream is an advantage you get in functional programming... and it's just so much nicer than imperative solutions...

By the way, my code is not exactly the same as your Haskell (as far as I could understand it...), as you developed an application in Haskell, but I instead wrote a procedure on Scheme that extends the language and therefore, to use it, you start the interpreter (The Lisp Machine of our days...), load the module (but a simple shell script would ease that to the user) and type (prime? ...) when you need it. 

The "classic" development style on Scheme (don't know what about other Lisp dialects) is just that: I extend the language to my needs, load it into the interpreter and then let the user type in the commands he needs... and if he/she needs to extend my extensions, he/she'll do exactly the same, etc. etc. etc. and all extensions will be just Lisp objects, which is the difference why you can do this in Python, Perl or other interpreted languages: yeah, you can extend the language, start the interpreter loading the module (and, e.g. using the -i flag in Python to stay in interactive mode), but those extensions won't be embedded into Python itself, but just implemented in Python.

Yeah, it's a bit weird and probably not "usable" for the end-user, who expects an interface (better if GUI), not a Scheme interpreter with some module loaded and then start playing with it.

---

### Post by jimi_hendrix on 2008-10-08
** FORTRAN 77 **(with goto instead of subprograms (functions in most other languages))

```
      [color=#008000]**program **[/color][color=#19177c]prime[/color]
      [color=#b00040]integer [/color][color=#19177c]tocheck[/color], [color=#19177c]i[/color], [color=#19177c]ret[/color]

      [color=#008000]**write**[/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#ba2121]'what is the number to check?'[/color]
      [color=#008000]**read**[/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#19177c]tocheck[/color]

      [color=#008000]**if**[/color] ([color=#19177c]tocheck[/color] [color=#aa22ff]**.lt.**[/color] [color=#666666]2[/color]) [color=#008000][b]then
        write[/b][/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#ba2121]'the number prime'[/color]
        [color=#008000]**goto **[/color][color=#666666]2[/color]
      [color=#008000][b]endif
       do [/b][/color][color=#666666]1[/color] [color=#19177c]i[/color] [color=#666666]=[/color] [color=#666666]1[/color], ([color=#19177c]tocheck[/color] [color=#666666]-[/color] [color=#666666]1[/color])
        [color=#19177c]ret[/color] [color=#666666]=[/color] [color=#008000]mod[/color]([color=#19177c]tocheck[/color],[color=#19177c]i[/color])
        [color=#008000]**if**[/color] ([color=#19177c]ret[/color] [color=#aa22ff]**.eq.**[/color] [color=#666666]0[/color]) [color=#008000][b]then
          write[/b][/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#ba2121]'the number prime'[/color]
          [color=#008000]**goto **[/color][color=#666666]2[/color]
        [color=#008000][b]endif
 [/b][/color][color=#666666]1[/color]    [color=#008000][b]continue 
      
 [/b][/color][color=#666666]2[/color]    [color=#008000][b]stop
      end[/b][/color]

```
you should retype this code in all caps for tradition

---

### Post by pp. on 2008-10-09
> **jimi_hendrix said:**
> ** FORTRAN 77 **(with goto instead of subprograms (functions in most other languages))

When and where does it tell that a number is prime?
Why does it say that a number is prime whenever it is not?

Oh, and ***goto*** does not do anything resembling a function or a procedure.

---

### Post by jimi_hendrix on 2008-10-09
i really have to stop posting late at night...ill edit it later...and i never said goto was a funtion...i said subprograms were

---

### Post by Reiger on 2008-10-09
> **nvteighen said:**
> Well, I never said Scheme is the only nice way to do it... Actually, using an infinite stream is an advantage you get in functional programming... and it's just so much nicer than imperative solutions...

It's mostly the benefit of lazy evaluation/programming... the inifite stream gets never fully evaluated, only as far as is needed...

> 
By the way, my code is not exactly the same as your Haskell (as far as I could understand it...), as you developed an application in Haskell, but I instead wrote a procedure on Scheme that extends the language and therefore, to use it, you start the interpreter (The Lisp Machine of our days...), load the module (but a simple shell script would ease that to the user) and type (prime? ...) when you need it.

Well no not really, load it in an interpreter and you can use these as 'native' built-in functions. For instance, if you load this module in the GHCI you would be able to filter out all relative primes in the sequence [4,5,6,7,8,9,10] by typing primes [4,5,6,7,8,9,10]. So wheter or not it's the same as Lisp I'm not sure (not familiar with Lisp), but it would appear that the effect to the user is pretty much the same.

---

### Post by lisati on 2008-10-09
> **jimi_hendrix said:**
> ** FORTRAN 77 **(with goto instead of subprograms (functions in most other languages))

```
      [color=#008000]**program **[/color][color=#19177c]prime[/color]
      [color=#b00040]integer [/color][color=#19177c]tocheck[/color], [color=#19177c]i[/color], [color=#19177c]ret[/color]

      [color=#008000]**write**[/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#ba2121]'what is the number to check?'[/color]
      [color=#008000]**read**[/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#19177c]tocheck[/color]

      [color=#008000]**if**[/color] ([color=#19177c]tocheck[/color] [color=#aa22ff]**.lt.**[/color] [color=#666666]2[/color]) [color=#008000][b]then
        write[/b][/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#ba2121]'the number prime'[/color]
        [color=#008000]**goto **[/color][color=#666666]2[/color]
      [color=#008000][b]endif
       do [/b][/color][color=#666666]1[/color] [color=#19177c]i[/color] [color=#666666]=[/color] [color=#666666]1[/color], ([color=#19177c]tocheck[/color] [color=#666666]-[/color] [color=#666666]1[/color])
        [color=#19177c]ret[/color] [color=#666666]=[/color] [color=#008000]mod[/color]([color=#19177c]tocheck[/color],[color=#19177c]i[/color])
        [color=#008000]**if**[/color] ([color=#19177c]ret[/color] [color=#aa22ff]**.eq.**[/color] [color=#666666]0[/color]) [color=#008000][b]then
          write[/b][/color] ([color=#666666]*[/color],[color=#666666]*[/color]) [color=#ba2121]'the number prime'[/color]
          [color=#008000]**goto **[/color][color=#666666]2[/color]
        [color=#008000][b]endif
 [/b][/color][color=#666666]1[/color]    [color=#008000][b]continue 
      
 [/b][/color][color=#666666]2[/color]    [color=#008000][b]stop
      end[/b][/color]

```
you should retype this code in all caps for tradition
I'd suggest starting the DO loop at 2 - unless I'm mistaken, "any positive integer" modulus 1 would equal zero.

---

### Post by nvteighen on 2008-10-09
> **Reiger said:**
> It's mostly the benefit of lazy evaluation/programming... the inifite stream gets never fully evaluated, only as far as is needed...

Yeah, you're right. But are there imperative programming languages with lazy evaluation?

> Well no not really, load it in an interpreter and you can use these as 'native' built-in functions. For instance, if you load this module in the GHCI you would be able to filter out all relative primes in the sequence [4,5,6,7,8,9,10] by typing primes [4,5,6,7,8,9,10]. So wheter or not it's the same as Lisp I'm not sure (not familiar with Lisp), but it would appear that the effect to the user is pretty much the same.

You can do that with any interpreted language that has an interactive shell. The difference in Lisp is that there's absolutely no distinction between built-in procedures and the ones you created... there's no differnce even with syntactic keywords because the syntax is always the same for everything:

```

(*procedure* *datum*)

```

By that, any procedure you create becomes part of the language, not just something implemented in the language. For example, there's no language (as far as I know) that treats your created procedures exactly the same as the + operator, except Lisp, where (+ 2 3) has the same syntax than creating a procedure called 'add' (add 2 3)... So, the boundary between "operators" and "procedures" is destroyed... This, plus, the "code <=> data" (homoiconicity) principle makes Lisp more than a language, but a framework to create languages and therefore so different to anything else (hey, can you take the second element of a procedure...? In Lisp you can, as any procedure is a list, so it has a second element!).

As you already know a functional programming language, I really recommend you learn some sort of Lisp to see it on your own.

---

### Post by pp. on 2008-10-09
> **nvteighen said:**
> ... are there imperative programming languages with lazy evaluation?

Yes, but they call it something else. Classical example: short-circuited compound conditions. In "A and B", "B" will be executed only if "A" evaluates to true.

> **nvteighen said:**
> there's no language (as far as I know) that treats your created procedures exactly the same as the + operator, except Lisp, where (+ 2 3) has the same syntax than creating a procedure called 'add' (add 2 3)

Smalltalk does that, too. Operators are just funny selectors.

---

### Post by Zugzwang on 2008-10-09
If I remember correctly, lately (less than 8 years ago) there was discovered some prime number testing algorithm with a running time polynomial in the length of the prime number given (and without randomisation). That one would be quite nice to see here! Does anyone have more information (Google doesn't reveal much)?

---

### Post by Bichromat on 2008-10-09
> **Zugzwang said:**
> If I remember correctly, lately (less than 8 years ago) there was discovered some prime number testing algorithm with a running time polynomial in the length of the prime number given (and without randomisation). That one would be quite nice to see here! Does anyone have more information (Google doesn't reveal much)?

Is this what you're talking about: [http://mathworld.wolfram.com/AKSPrimalityTest.html](http://mathworld.wolfram.com/AKSPrimalityTest.html) ?
It is asymptotically faster than other methods, but I think it is too slow and cumbersome to be useful on small numbers. The best algorithm available is the Elliptic curve test.
For small enough numbers (less than 15 digits), a probabilistic test like Rabin-Miller is sufficient (if you take enough bases).
Even for larger numbers, the probability of a false positive is very small.

---

### Post by Nemooo on 2008-10-12
My solution in [Arc]("http://arclanguage.com/"):

```
[color=#408080]*; Returns t if the number is a prime and nil otherwise.*[/color]
[color=#408080]*; Run with (is-prime x)*[/color]

([color=#008000]**def **[/color][color=#19177C]is-prime[/color] ([color=#0000FF]x[/color])
  ([color=#008000]**if **[/color]([color=#0000FF]is[/color] [color=#19177C]x[/color] [color=#666666]2[/color]) [color=#19177C]t[/color]
               ([color=#008000]or [/color]([color=#008000]< [/color][color=#19177C]x[/color] [color=#666666]2[/color]) ([color=#0000FF]is[/color] ([color=#0000FF]mod[/color] [color=#19177C]x[/color] [color=#666666]2[/color]) [color=#666666]0[/color])) [color=#19177C]nil[/color]
                                             ([color=#0000FF]check-prime[/color] [color=#19177C]x[/color])))

([color=#008000]**def **[/color][color=#19177C]check-prime[/color] ([color=#0000FF]x[/color])
  ([color=#0000FF]with[/color] ([color=#0000FF]return[/color] [color=#19177C]t[/color] [color=#19177C]i[/color] [color=#666666]3[/color] [color=#19177C]limit[/color] ([color=#0000FF]sqrt[/color] [color=#19177C]x[/color]))
    ([color=#0000FF]while[/color] ([color=#008000]<= [/color][color=#19177C]i[/color] [color=#19177C]limit[/color])
      ([color=#008000]when [/color]([color=#0000FF]is[/color] ([color=#0000FF]mod[/color] [color=#19177C]x[/color] [color=#19177C]i[/color]) [color=#666666]0[/color])
        ([color=#008000]= [/color][color=#19177C]return[/color] [color=#19177C]nil[/color])
        ([color=#008000]= [/color][color=#19177C]limit[/color] [color=#666666]0[/color]))
      ([color=#0000FF]zap[/color] [[color=#19177C]+[/color] [color=#19177C]_[/color] [color=#666666]2[/color]] [color=#19177C]i[/color]))
    [color=#19177C]return[/color]))

```

EDIT: This is in my opinion a lot more elegant and more efficient. Has anyone else given Arc a try?

---

### Post by achelis on 2008-10-12
> **mosty friedman said:**
> done in Java
```
[color=#008000]**import**[/color] [color=#0000FF]**java.util.Scanner**[/color][color=#666666];[/color]
[color=#008000]**public**[/color] [color=#008000]**class**[/color] [color=#0000FF]**PrimeTest**[/color]
[color=#666666]{[/color]
 [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]void[/color] [color=#0000FF]isPrime[/color][color=#666666]([/color] [color=#B00040]int[/color] n [color=#666666])[/color] 
    [color=#666666]{[/color]
      [color=#B00040]boolean[/color] prime [color=#666666]=[/color] [color=#008000]**true**[/color][color=#666666];[/color]
      [color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]<[/color] [color=#666666]2[/color] [color=#666666])[/color]
         prime [color=#666666]=[/color] [color=#008000]**false**[/color][color=#666666];[/color]
         
        [color=#008000]**for**[/color][color=#666666]([/color] [color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]2[/color][color=#666666];[/color] i [color=#666666]<[/color] n[color=#666666];[/color] i[color=#666666]++[/color] [color=#666666])[/color]
         [color=#666666]{[/color]
            [color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]%[/color] i [color=#666666]==[/color] [color=#666666]0[/color] [color=#666666])[/color]
              [color=#666666]{[/color]
                prime [color=#666666]=[/color] [color=#008000]**false**[/color][color=#666666];[/color]
                   [color=#008000]**break**[/color][color=#666666];[/color]
              [color=#666666]}[/color]
         [color=#666666]}[/color]
         [color=#008000]**if**[/color][color=#666666]([/color] prime [color=#666666])[/color]
            System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]printf[/color][color=#666666]([/color] [color=#BA2121]"%d %s\n"[/color][color=#666666],[/color] n[color=#666666],[/color] [color=#BA2121]"is a prime number"[/color] [color=#666666]);[/color]
         [color=#008000]**else**[/color]
            System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]printf[/color][color=#666666]([/color] [color=#BA2121]"%d %s\n"[/color][color=#666666],[/color] n[color=#666666],[/color] [color=#BA2121]"is not a prime number"[/color] [color=#666666]);[/color]
     [color=#666666]}[/color]
 
[color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]void[/color] [color=#0000FF]main[/color][color=#666666]([/color] String[color=#666666][][/color]args [color=#666666])[/color]
 [color=#666666]{[/color]
   Scanner sc [color=#666666]=[/color] [color=#008000]**new**[/color] Scanner[color=#666666]([/color] System[color=#666666].[/color][color=#7D9029]in[/color] [color=#666666]);[/color]
   System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color] [color=#BA2121]"enter a number to check if its prime or not"[/color][color=#666666]);[/color]
   [color=#B00040]int[/color] num [color=#666666]=[/color] sc[color=#666666].[/color][color=#7D9029]nextInt[/color][color=#666666]();[/color]
   isPrime[color=#666666]([/color] num [color=#666666]);[/color]
 [color=#666666]}[/color]

[color=#666666]}[/color]

```
any tips or any feedback are appreciated :)

My 2 cents: I would change the isPrime method to return a boolean indicating whether the number given is a boolean or not. Imo it's not nice to have a function doing both calculation/modelling and output/view. 
The second thing is that, as has been mentioned before, you only need to check all uneven numbers up to the square root of n.
I took the liberty to modify your code to this:
```
[color=#008000]**import**[/color] [color=#0000FF]**java.util.Scanner**[/color][color=#666666];[/color]
[color=#008000]**public**[/color] [color=#008000]**class**[/color] [color=#0000FF]**PrimeTest**[/color]
[color=#666666]{[/color]
    [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]boolean[/color] [color=#0000FF]isPrime[/color][color=#666666]([/color] [color=#B00040]int[/color] n [color=#666666])[/color] [color=#666666]{[/color]
	[color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]<[/color] [color=#666666]2[/color] [color=#666666]||[/color] [color=#666666]([/color][color=#666666]0x01[/color] [color=#666666]&[/color] n[color=#666666])[/color] [color=#666666]==[/color] [color=#666666]0[/color][color=#666666])[/color]
	    [color=#008000]**return**[/color] [color=#008000]**false**[/color][color=#666666];[/color]
	[color=#008000]**if**[/color][color=#666666]([/color]n [color=#666666]==[/color] [color=#666666]2[/color][color=#666666])[/color]
	    [color=#008000]**return**[/color] [color=#008000]**true**[/color][color=#666666];[/color]
         
	[color=#B00040]int[/color] h [color=#666666]=[/color] [color=#666666]([/color][color=#B00040]int[/color][color=#666666])[/color] Math[color=#666666].[/color][color=#7D9029]sqrt[/color][color=#666666]([/color]n[color=#666666]);[/color]
        [color=#008000]**for**[/color][color=#666666]([/color] [color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]3[/color][color=#666666];[/color] i [color=#666666]<=[/color] h[color=#666666];[/color] i [color=#666666]+=[/color] [color=#666666]2[/color] [color=#666666])[/color] [color=#666666]{[/color]
	    [color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]%[/color] i [color=#666666]==[/color] [color=#666666]0[/color] [color=#666666])[/color] [color=#666666]{[/color]
		[color=#008000]**return**[/color] [color=#008000]**false**[/color][color=#666666];[/color]
	    [color=#666666]}[/color]
	[color=#666666]}[/color]
	[color=#008000]**return**[/color] [color=#008000]**true**[/color][color=#666666];[/color]
    [color=#666666]}[/color]
 
    [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]void[/color] [color=#0000FF]main[/color][color=#666666]([/color] String[color=#666666][][/color]args [color=#666666])[/color] [color=#666666]{[/color]
	Scanner sc [color=#666666]=[/color] [color=#008000]**new**[/color] Scanner[color=#666666]([/color] System[color=#666666].[/color][color=#7D9029]in[/color] [color=#666666]);[/color]
	System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color] [color=#BA2121]"enter a number to check if its prime or not"[/color][color=#666666]);[/color]
	[color=#B00040]int[/color] n [color=#666666]=[/color] sc[color=#666666].[/color][color=#7D9029]nextInt[/color][color=#666666]();[/color]
	[color=#008000]**if**[/color] [color=#666666]([/color]isPrime[color=#666666]([/color] n [color=#666666]))[/color]
	    System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color]n [color=#666666]+[/color] [color=#BA2121]" is a prime."[/color][color=#666666]);[/color]
	[color=#008000]**else**[/color]
	    System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color]n [color=#666666]+[/color] [color=#BA2121]" is not a prime."[/color][color=#666666]);[/color]
    [color=#666666]}[/color]
[color=#666666]}[/color]

```
Alternatively the print-out could be written as:
```

System.out.println(n + " is " + (isPrime(n) ? "" : "not ") + "a prime.");

```

---

### Post by Barrucadu on 2008-10-12
Common Lisp:

```
([color=#008000]defun[/color] [color=#19177C]isprime[/color] ([color=#19177C]x[/color])
  ([color=#008000]**if**[/color] ([color=#008000]<[/color] [color=#19177C]x[/color] [color=#666666]2[/color])
	  ([color=#008000]**return-from**[/color] [color=#19177C]isprime[/color] [color=#880000]nil[/color])
	([color=#008000]dotimes[/color] ([color=#19177C]i[/color] ([color=#008000]+[/color] ([color=#008000]ceiling[/color] ([color=#008000]sqrt[/color] [color=#19177C]x[/color])) [color=#666666]1[/color]))
	  ([color=#008000]**if**[/color] ([color=#008000]>[/color] [color=#19177C]i[/color] [color=#666666]1[/color])
		  ([color=#008000]**if**[/color] ([color=#008000]<[/color] [color=#19177C]i[/color] [color=#19177C]x[/color])
			  ([color=#008000]**if**[/color] ([color=#008000]equal[/color] ([color=#008000]mod[/color] [color=#19177C]x[/color] [color=#19177C]i[/color]) [color=#666666]0[/color])
				  ([color=#008000]**return-from**[/color] [color=#19177C]isprime[/color] [color=#880000]nil[/color]))))))
  ([color=#008000]**return-from**[/color] [color=#19177C]isprime[/color] [color=#880000]t[/color]))

```

---

### Post by Lux Perpetua on 2008-10-13
> **Zugzwang said:**
> If I remember correctly, lately (less than 8 years ago) there was discovered some prime number testing algorithm with a running time polynomial in the length of the prime number given (and without randomisation). That one would be quite nice to see here! Does anyone have more information (Google doesn't reveal much)?Here you go. :-) For your amusement: ```
[color=#408080][i]/* AKS Primality Algorithm.
 *
 * Described here:
 *
 *     [http://www.cse.iitk.ac.in/~manindra/algebra/primality_v6.pdf](http://www.cse.iitk.ac.in/~manindra/algebra/primality_v6.pdf)
 * 
 * Actually, the algorithm implemented here is considerably less
 * efficient than the one described in the paper due to my naive
 * polynomial squaring algorithm.  Nevertheless, it is still a
 * polynomial-time primality testing algorithm.
 */[/i][/color]
[color=#BC7A00]   

#include <iostream>
#include <sstream>
[/color]
[color=#408080][i]/* This is the default for integers expected to be of size comparable to
 * the number whose primality is being checked. */[/i][/color]
[color=#008000]**typedef**[/color] uint32_t reg_int;

[color=#408080]*/* This is used as necessary to prevent overflow. */*[/color]
[color=#008000]**typedef**[/color] uint64_t big_int;

[color=#408080]*/* Compute n^b. */*[/color]
reg_int power(reg_int n, [color=#B00040]unsigned[/color] [color=#B00040]int[/color] b) {
    [color=#008000]**if**[/color] (b [color=#666666]==[/color] [color=#666666]0[/color])
        [color=#008000]**return**[/color] [color=#666666]1[/color];

    reg_int m(power(n, b[color=#666666]>>[/color][color=#666666]1[/color]));
    m [color=#666666]*=[/color] m;

    [color=#008000]**if**[/color] (b [color=#666666]&[/color] [color=#666666]1[/color])
        m [color=#666666]*=[/color] n;

    [color=#008000]**return**[/color] m;
}

[color=#408080][i]/* Compute floor(n^(1/b)). This is not the cleverest algorithm, but it's
 * acceptably fast, and it isn't the bottleneck of the program, so
 * there's no reason to optimize it now.
 */[/i][/color]
reg_int root(reg_int n, [color=#B00040]unsigned[/color] [color=#B00040]int[/color] b) {
    [color=#008000]**if**[/color] (n [color=#666666]<[/color] [color=#666666]1[/color])
        [color=#008000]**return**[/color] [color=#666666]0[/color];

    reg_int m(root(n [color=#666666]>>[/color] b, b)[color=#666666]<<[/color][color=#666666]1[/color]);
    reg_int k(m [color=#666666]+[/color] [color=#666666]1[/color]);

    [color=#008000]**if**[/color] (power(k, b) [color=#666666]<=[/color] n)
        [color=#008000]**return**[/color] k;
    [color=#008000]**else**[/color]
        [color=#008000]**return**[/color] m;
}

[color=#408080][i]/* Compute the Euler totient function of n (number of positive integers
 * up to n relatively prime to n).  The running time is exponential in
 * the length of n, but that's okay, since the number it will be used on
 * is small compared to the number whose primality is being
 * checked. It's not the bottleneck, so there's no reason to worry about
 * it.
 */[/i][/color]
[color=#B00040]unsigned[/color] [color=#B00040]int[/color] phi([color=#B00040]unsigned[/color] [color=#B00040]int[/color] n) {
    [color=#008000]**if**[/color] (n [color=#666666]==[/color] [color=#666666]1[/color])
        [color=#008000]**return**[/color] [color=#666666]1[/color];

    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] p([color=#666666]2[/color]);

    [color=#008000]**while**[/color] ([color=#008000]**true**[/color]) {
        [color=#008000]**if**[/color] (n [color=#666666]%[/color] p [color=#666666]==[/color] [color=#666666]0[/color]) {
            n [color=#666666]/=[/color] p;
            [color=#B00040]unsigned[/color] [color=#B00040]int[/color] q([color=#666666]1[/color]);
            [color=#B00040]unsigned[/color] [color=#B00040]int[/color] m(n);

            [color=#008000]**while**[/color] (m [color=#666666]%[/color] p [color=#666666]==[/color] [color=#666666]0[/color]) {
                m [color=#666666]/=[/color] p;
                q [color=#666666]*=[/color] p;
            }
            [color=#008000]**return**[/color] (p [color=#666666]-[/color] [color=#666666]1[/color])[color=#666666]*[/color]q[color=#666666]*[/color]phi(m);
        }
        p [color=#666666]+=[/color] [color=#666666]1[/color];
    }
}

[color=#408080][i]/* Usage: instantiate this class on a positive integer and either cast
 * it to a string (for informative output) or a bool (for a simple
 * true/false determination of the primality of the integer).
 */[/i][/color]
[color=#008000]**class**[/color] [color=#0000FF]**primality_check**[/color] {
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] r;
    reg_int n;
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] lgn; [color=#408080][i]// log_2(n)
[/i][/color]    [color=#B00040]bool[/color] val;

    [color=#408080][i]/* These are work buffers used by the polynomial arithmetic
     * subroutines. They represent polynomials mod x^r - 1.  Note: all
     * polynomial arithmetic is mod (x^r - 1, n). The outines operate on
     * Accum_A (as source and destination) and use Accum_B for scratch
     * work or to store results as needed. 
     */[/i][/color]

    reg_int [color=#666666]*[/color] Accum_A;
    reg_int [color=#666666]*[/color] Accum_B;

    std[color=#666666]::[/color]ostringstream messages;

    [color=#B00040]void[/color] clear(reg_int [color=#666666]*[/color]P) {
        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]0[/color]; k [color=#666666]<[/color] r; [color=#666666]++[/color]k) {
            P[k] [color=#666666]=[/color] [color=#666666]0[/color];
        }
    }

    [color=#B00040]void[/color] swap() {
        reg_int [color=#666666]*[/color]D [color=#666666]=[/color] Accum_A;
        Accum_A [color=#666666]=[/color] Accum_B;
        Accum_B [color=#666666]=[/color] D;
    }

    [color=#408080]*/* Multiply Accum_A by (x + a). */*[/color]
    [color=#B00040]void[/color] mul_a([color=#B00040]unsigned[/color] [color=#B00040]int[/color] a) {
        reg_int last(Accum_A[r[color=#666666]-[/color][color=#666666]1[/color]]);

        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] r[color=#666666]-[/color][color=#666666]1[/color]; k [color=#666666]>[/color] [color=#666666]0[/color]; [color=#666666]--[/color]k) {
            big_int t(Accum_A[k]);
            t [color=#666666]*=[/color] a;
            t [color=#666666]+=[/color] Accum_A[k[color=#666666]-[/color][color=#666666]1[/color]];
            t [color=#666666]%=[/color] n;

            Accum_A[k] [color=#666666]=[/color] t;
        }
        big_int t(Accum_A[[color=#666666]0[/color]]);
        t [color=#666666]*=[/color] a;
        t [color=#666666]+=[/color] last;
        t [color=#666666]%=[/color] n;

        Accum_A[[color=#666666]0[/color]] [color=#666666]=[/color] t;
    }

    [color=#408080][i]/* Square Accum_A.  This is the bottleneck of the program and
     * basically cripples this implementation. :-( There are faster ways
     * to square a polynomial, but they're much more complicated.
     */[/i][/color]
    [color=#B00040]void[/color] sqr() {
        swap();
        clear(Accum_A);

        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]0[/color]; k [color=#666666]<[/color] r; [color=#666666]++[/color]k) {
            [color=#B00040]unsigned[/color] [color=#B00040]int[/color] k2 [color=#666666]=[/color] (k [color=#666666]+[/color] k) [color=#666666]%[/color] r;

            big_int t(Accum_B[k]);
            t [color=#666666]*=[/color] t;
            t [color=#666666]+=[/color] Accum_A[k2];
            t [color=#666666]%=[/color] n;

            Accum_A[k2] [color=#666666]=[/color] t;

            [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] j [color=#666666]=[/color] k [color=#666666]+[/color] [color=#666666]1[/color]; j [color=#666666]<[/color] r; [color=#666666]++[/color]j) {
                [color=#B00040]unsigned[/color] [color=#B00040]int[/color] i [color=#666666]=[/color] (j [color=#666666]+[/color] k) [color=#666666]%[/color] r;

                big_int t(Accum_B[k]);
                t [color=#666666]*=[/color] Accum_B[j];
                t [color=#666666]+=[/color] t;
                t [color=#666666]+=[/color] Accum_A[i];
                t [color=#666666]%=[/color] n;

                Accum_A[i] [color=#666666]=[/color] t;
            }
        }
    }

    [color=#408080]*/* Compute (x + a)^n and put result in Accum_A. */*[/color]
    [color=#B00040]void[/color] pow([color=#B00040]unsigned[/color] [color=#B00040]int[/color] a) {
        clear(Accum_A);
        Accum_A[[color=#666666]0[/color]] [color=#666666]=[/color] a;
        Accum_A[[color=#666666]1[/color]] [color=#666666]=[/color] [color=#666666]1[/color];

        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] lgn [color=#666666]-[/color] [color=#666666]1[/color]; k [color=#666666]>[/color] [color=#666666]0[/color]; [color=#666666]--[/color]k) {
            sqr();

            [color=#008000]**if**[/color] ((n [color=#666666]>>[/color] (k[color=#666666]-[/color][color=#666666]1[/color])) [color=#666666]&[/color] [color=#666666]1[/color] [color=#666666]==[/color] [color=#666666]1[/color]) {
                mul_a(a);
            }
        }
    }

    [color=#408080]*/* Determine if (x + a)^n == x^n + a. */*[/color]
    [color=#B00040]bool[/color] test([color=#B00040]unsigned[/color] [color=#B00040]int[/color] a) {
        pow(a);

        [color=#008000]**if**[/color] (Accum_A[[color=#666666]0[/color]] [color=#666666]!=[/color] a) {
            [color=#008000]**return**[/color] [color=#008000]**false**[/color];
        }

        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]1[/color]; k [color=#666666]<[/color] n [color=#666666]%[/color] r; [color=#666666]++[/color]k) {
            [color=#008000]**if**[/color] (Accum_A[k] [color=#666666]!=[/color] [color=#666666]0[/color]) {
                [color=#008000]**return**[/color] [color=#008000]**false**[/color];
            }
        }

        [color=#008000]**if**[/color] (Accum_A[n [color=#666666]%[/color] r] [color=#666666]!=[/color] [color=#666666]1[/color]) {
            [color=#008000]**return**[/color] [color=#008000]**false**[/color];
        }

        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] (n [color=#666666]%[/color] r) [color=#666666]+[/color] [color=#666666]1[/color]; k [color=#666666]<[/color] r; [color=#666666]++[/color]k) {
            [color=#008000]**if**[/color] (Accum_A[k] [color=#666666]!=[/color] [color=#666666]0[/color]) {
                [color=#008000]**return**[/color] [color=#008000]**false**[/color];
            }
        }

        [color=#008000]**return**[/color] [color=#008000]**true**[/color];
    }

[color=#008000]**public**[/color][color=#666666]:[/color]
    primality_check(reg_int p);

    [color=#008000]**operator**[/color] [color=#B00040]bool[/color] () [color=#008000]**const**[/color] {
        [color=#008000]**return**[/color] val;
    }

    [color=#008000]**operator**[/color] std[color=#666666]::[/color]string () [color=#008000]**const**[/color] {
        [color=#008000]**return**[/color] messages.str();
    }

    [color=#666666]~[/color]primality_check() {
        [color=#008000]**delete**[/color] [] Accum_A;
        [color=#008000]**delete**[/color] [] Accum_B;
    }
};

primality_check[color=#666666]::[/color]primality_check(reg_int p) 
    [color=#666666]:[/color] n(p), Accum_A([color=#666666]0[/color]), Accum_B([color=#666666]0[/color])
{
    lgn [color=#666666]=[/color] [color=#666666]0[/color];

    reg_int m(n);

    [color=#008000]**while**[/color] (m [color=#666666]!=[/color] [color=#666666]0[/color]) {
        m [color=#666666]>>=[/color] [color=#666666]1[/color];
        [color=#666666]++[/color]lgn;
    }

    [color=#408080][i]// 1. Check if n is a perfect power
[/i][/color]    m [color=#666666]=[/color] n;
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] b [color=#666666]=[/color] [color=#666666]1[/color];
    [color=#008000]**while**[/color] (m [color=#666666]>[/color] [color=#666666]1[/color]) {
        [color=#666666]++[/color]b;
        m [color=#666666]=[/color] root(n, b);
        [color=#008000]**if**[/color] (power(m, b) [color=#666666]==[/color] n) {
            val [color=#666666]=[/color] [color=#008000]**false**[/color];
            messages [color=#666666]<<[/color] [color=#BA2121]"Composite! ("[/color] 
                     [color=#666666]<<[/color] n [color=#666666]<<[/color] [color=#BA2121]" = "[/color] [color=#666666]<<[/color] m [color=#666666]<<[/color] [color=#BA2121]"^"[/color] [color=#666666]<<[/color] b [color=#666666]<<[/color] [color=#BA2121]")"[/color];
            [color=#008000]**return**[/color];
        }
    }

    [color=#408080][i]// 2. Determine r
[/i][/color]    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] target(lgn[color=#666666]*[/color]lgn);
    
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] order([color=#666666]0[/color]);
    r [color=#666666]=[/color] [color=#666666]1[/color];

    [color=#008000]**while**[/color] (order [color=#666666]<[/color] target) {
        [color=#666666]++[/color]r;
        order [color=#666666]=[/color] [color=#666666]1[/color];
        [color=#B00040]unsigned[/color] [color=#B00040]int[/color] q(n [color=#666666]%[/color] r);

        [color=#008000]**while**[/color] (q [color=#666666]!=[/color] [color=#666666]1[/color]) {
            [color=#008000]**if**[/color] (order [color=#666666]>=[/color] target) {
                [color=#008000]**break**[/color];
            }

            q [color=#666666]=[/color] (q [color=#666666]*[/color] n) [color=#666666]%[/color] r;
            [color=#666666]++[/color]order;
        }
    }

    Accum_A [color=#666666]=[/color] [color=#008000]**new**[/color] reg_int[r];
    Accum_B [color=#666666]=[/color] [color=#008000]**new**[/color] reg_int[r];

    [color=#408080][i]// 3. Check if n has any proper factors up to r
[/i][/color]    [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]2[/color]; k [color=#666666]<=[/color] r; [color=#666666]++[/color]k) {
        [color=#008000]**if**[/color] (n [color=#666666]%[/color] k [color=#666666]==[/color] [color=#666666]0[/color]) {
            [color=#008000]**if**[/color] (k [color=#666666]==[/color] n) {
                [color=#408080][i]// 4. We actually just proved n is prime
[/i][/color]                val [color=#666666]=[/color] [color=#008000]**true**[/color];
                messages [color=#666666]<<[/color] [color=#BA2121]"Prime! (checked exhaustively)"[/color];
                [color=#008000]**return**[/color];
            } [color=#008000]**else**[/color] {
                val [color=#666666]=[/color] [color=#008000]**false**[/color];
                messages [color=#666666]<<[/color] [color=#BA2121]"Composite! (divisible by "[/color] [color=#666666]<<[/color] k [color=#666666]<<[/color] [color=#BA2121]")"[/color];
                [color=#008000]**return**[/color];
            }
        }
    }

    [color=#408080][i]// 5. Polynomial test (the heart of the algorithm)
[/i][/color]    
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] limit((root(phi(r), [color=#666666]2[/color]) [color=#666666]+[/color] [color=#666666]1[/color])[color=#666666]*[/color]lgn);
    
    [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] a [color=#666666]=[/color] [color=#666666]1[/color]; a [color=#666666]<=[/color] limit; [color=#666666]++[/color]a) {
        [color=#008000]**if**[/color] ([color=#666666]![/color]test(a)) {
            val [color=#666666]=[/color] [color=#008000]**false**[/color];
            messages [color=#666666]<<[/color] [color=#BA2121]"Composite! (failed polynomial test with a = "[/color]
                     [color=#666666]<<[/color] a [color=#666666]<<[/color] [color=#BA2121]", r = "[/color] [color=#666666]<<[/color] r [color=#666666]<<[/color] [color=#BA2121]")"[/color];
            [color=#008000]**return**[/color];
        }
    }

    [color=#408080][i]// 6.
[/i][/color]    val [color=#666666]=[/color] [color=#008000]**true**[/color];
    messages [color=#666666]<<[/color] [color=#BA2121]"Prime! (passed all tests)"[/color];
}

std[color=#666666]::[/color]ostream [color=#666666]&[/color] [color=#008000]**operator**[/color] [color=#666666]<<[/color] (std[color=#666666]::[/color]ostream [color=#666666]&[/color] os, [color=#008000]**const**[/color] primality_check [color=#666666]&[/color] PC) {
    os [color=#666666]<<[/color] [color=#008000]**static_cast**[/color][color=#666666]<[/color]std[color=#666666]::[/color]string[color=#666666]>[/color](PC);
    [color=#008000]**return**[/color] os;
}

[color=#B00040]int[/color] main([color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]**[/color]argv) {
    [color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

    [color=#008000]**if**[/color] (argc [color=#666666]<[/color] [color=#666666]2[/color]) {
        cerr [color=#666666]<<[/color] [color=#BA2121]"Usage: "[/color] [color=#666666]<<[/color] argv[[color=#666666]0[/color]] [color=#666666]<<[/color] [color=#BA2121]" number_to_test"[/color] [color=#666666]<<[/color] endl;
        [color=#008000]**return**[/color] [color=#666666]1[/color];
    }

    istringstream is(argv[[color=#666666]1[/color]]);

    reg_int n;

    [color=#008000]**if**[/color] ([color=#666666]![/color](is [color=#666666]>>[/color] n)) {
        cerr [color=#666666]<<[/color] [color=#BA2121]"Usage: "[/color] [color=#666666]<<[/color] argv[[color=#666666]0[/color]] [color=#666666]<<[/color] [color=#BA2121]" number_to_test"[/color] [color=#666666]<<[/color] endl;
        [color=#008000]**return**[/color] [color=#666666]1[/color];
    }

    primality_check PC(n);

    cout [color=#666666]<<[/color] PC [color=#666666]<<[/color] endl;

    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```To compile: ```
g++ -ansi -Wall -pedantic -O3 aks_uint.cpp
```See the comments for specific details about the implementation. It doesn't achieve the asymptotic running time advertised in the paper because  my polynomial squaring is very suboptimal. However, it's technically still polynomial-time. Typical results on my computer: ```
%>time a.out 1299721
Prime! (passed all tests)

real    1m42.026s
user    1m32.454s
sys     0m0.040s
```This program can be ported painlessly to gmpxx. In fact, I've already done it, but it's probably not very useful, since this version is slow enough already, and the gmpxx version is more than ten times as slow.

---

### Post by jimi_hendrix on 2008-10-13
my first perl script...

[php]
#!/usr/bin/perl

print "what is the number you would like to check?\n";
my $check = <>; #<> is short for <STDIN>, both would work here

#begin checking
for (my $i = 2; $i < $check; $i++)
{
    if ($check % $i == 0)
    {
        print "the number is not prime\n";
        exit;
    }
}

print "the number is prime\n";

[/php]

any comments would be great

---

### Post by Reiger on 2008-10-13
And what would happen if the number entered was smaller than 2? Hint: see the C & C++ entries.

---

### Post by Reiger on 2008-10-13
> **achelis said:**
> 
```
[color=#008000]**import**[/color] [color=#0000FF]**java.util.Scanner**[/color][color=#666666];[/color]
[color=#008000]**public**[/color] [color=#008000]**class**[/color] [color=#0000FF]**PrimeTest**[/color]
[color=#666666]{[/color]
    [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]boolean[/color] [color=#0000FF]isPrime[/color][color=#666666]([/color] [color=#B00040]int[/color] n [color=#666666])[/color] [color=#666666]{[/color]
	[color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]<[/color] [color=#666666]2[/color] [color=#666666]||[/color] [color=#666666]([/color][color=#666666]0x01[/color] [color=#666666]&[/color] n[color=#666666])[/color] [color=#666666]==[/color] [color=#666666]0[/color][color=#666666])[/color]
	    [color=#008000]**return**[/color] [color=#008000]**false**[/color][color=#666666];[/color]
	[color=#008000]**if**[/color][color=#666666]([/color]n [color=#666666]==[/color] [color=#666666]2[/color][color=#666666])[/color]
	    [color=#008000]**return**[/color] [color=#008000]**true**[/color][color=#666666];[/color]
         
	[color=#B00040]int[/color] h [color=#666666]=[/color] [color=#666666]([/color][color=#B00040]int[/color][color=#666666])[/color] Math[color=#666666].[/color][color=#7D9029]sqrt[/color][color=#666666]([/color]n[color=#666666]);[/color]
        [color=#008000]**for**[/color][color=#666666]([/color] [color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]3[/color][color=#666666];[/color] i [color=#666666]<=[/color] h[color=#666666];[/color] i [color=#666666]+=[/color] [color=#666666]2[/color] [color=#666666])[/color] [color=#666666]{[/color]
	    [color=#008000]**if**[/color][color=#666666]([/color] n [color=#666666]%[/color] i [color=#666666]==[/color] [color=#666666]0[/color] [color=#666666])[/color] [color=#666666]{[/color]
		[color=#008000]**return**[/color] [color=#008000]**false**[/color][color=#666666];[/color]
	    [color=#666666]}[/color]
	[color=#666666]}[/color]
	[color=#008000]**return**[/color] [color=#008000]**true**[/color][color=#666666];[/color]
    [color=#666666]}[/color]
 
    [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]void[/color] [color=#0000FF]main[/color][color=#666666]([/color] String[color=#666666][][/color]args [color=#666666])[/color] [color=#666666]{[/color]
	Scanner sc [color=#666666]=[/color] [color=#008000]**new**[/color] Scanner[color=#666666]([/color] System[color=#666666].[/color][color=#7D9029]in[/color] [color=#666666]);[/color]
	System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color] [color=#BA2121]"enter a number to check if its prime or not"[/color][color=#666666]);[/color]
	[color=#B00040]int[/color] n [color=#666666]=[/color] sc[color=#666666].[/color][color=#7D9029]nextInt[/color][color=#666666]();[/color]
	[color=#008000]**if**[/color] [color=#666666]([/color]isPrime[color=#666666]([/color] n [color=#666666]))[/color]
	    System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color]n [color=#666666]+[/color] [color=#BA2121]" is a prime."[/color][color=#666666]);[/color]
	[color=#008000]**else**[/color]
	    System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color]n [color=#666666]+[/color] [color=#BA2121]" is not a prime."[/color][color=#666666]);[/color]
    [color=#666666]}[/color]
[color=#666666]}[/color]

```

This code will fail to recognize 2 as a prime, but that can be solved readily by changing order of a few lines to:
```

if(n == 2)
    return true;
         
if( n < 2 || (0x01 & n) == 0)
    return false

```

---

### Post by Lux Perpetua on 2008-10-15
I've revamped my AKS implementation using gmpxx and the polynomial multiplication hack explained here: 

[http://www.apple.com/acg/pdf/aks3.pdf](http://www.apple.com/acg/pdf/aks3.pdf)

Now it's actually faster than my native integer implementation. To wit: the "hard" operation, polynomial squaring, can piggyback on big integer arithmetic. Ironically, the code is simpler *and* it runs faster, since most of the real work is pushed into the GMP library. ```
[color=#408080][i]/* AKS Primality Algorithm.
 *
 * Described here:
 *
 *     http://www.cse.iitk.ac.in/~manindra/algebra/primality_v6.pdf
 * 
 * The crucial part of the algorithm, which requires verifying a long
 * list of polynomial identities, is implemented using a useful hack
 * explained here:
 *
 *     http://www.apple.com/acg/pdf/aks3.pdf
 */[/i][/color]
[color=#BC7A00]   
#include <iostream>
#include <sstream>
#include <gmpxx.h>
[/color]
[color=#408080]*/* Compute n^b. */*[/color]
mpz_class power([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] n, [color=#B00040]unsigned[/color] [color=#B00040]int[/color] b) {
    [color=#008000]**if**[/color] (b [color=#666666]==[/color] [color=#666666]0[/color])
        [color=#008000]**return**[/color] [color=#666666]1[/color];

    mpz_class m(power(n, b[color=#666666]>>[/color][color=#666666]1[/color]));
    m [color=#666666]*=[/color] m;

    [color=#008000]**if**[/color] (b [color=#666666]&[/color] [color=#666666]1[/color])
        m [color=#666666]*=[/color] n;

    [color=#008000]**return**[/color] m;
}

[color=#408080][i]/* Compute floor(n^(1/b)). This is not the cleverest algorithm, but it's
 * acceptably fast and correct. 
 */[/i][/color]
mpz_class root([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] n, [color=#B00040]unsigned[/color] [color=#B00040]int[/color] b) {
    [color=#008000]**if**[/color] (n [color=#666666]<[/color] [color=#666666]1[/color])
        [color=#008000]**return**[/color] [color=#666666]0[/color];

    mpz_class m(root(n [color=#666666]>>[/color] b, b)[color=#666666]<<[/color][color=#666666]1[/color]);
    mpz_class k(m [color=#666666]+[/color] [color=#666666]1[/color]);

    [color=#008000]**if**[/color] (power(k, b) [color=#666666]<=[/color] n)
        [color=#008000]**return**[/color] k;
    [color=#008000]**else**[/color]
        [color=#008000]**return**[/color] m;
}

[color=#408080][i]/* Compute the Euler totient function of n (number of positive integers
 * up to n relatively prime to n).  The running time is exponential in
 * the length of n, but that's okay, since the number it will be used on
 * is small compared to the number whose primality is being
 * checked. It's not the bottleneck, so there's no reason to worry about
 * it.
 */[/i][/color]
[color=#B00040]unsigned[/color] [color=#B00040]int[/color] phi([color=#B00040]unsigned[/color] [color=#B00040]int[/color] n) {
    [color=#008000]**if**[/color] (n [color=#666666]==[/color] [color=#666666]1[/color])
        [color=#008000]**return**[/color] [color=#666666]1[/color];

    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] p([color=#666666]2[/color]);

    [color=#008000]**while**[/color] ([color=#008000]**true**[/color]) {
        [color=#008000]**if**[/color] (n [color=#666666]%[/color] p [color=#666666]==[/color] [color=#666666]0[/color]) {
            n [color=#666666]/=[/color] p;
            [color=#B00040]unsigned[/color] [color=#B00040]int[/color] q([color=#666666]1[/color]);
            [color=#B00040]unsigned[/color] [color=#B00040]int[/color] m(n);

            [color=#008000]**while**[/color] (m [color=#666666]%[/color] p [color=#666666]==[/color] [color=#666666]0[/color]) {
                m [color=#666666]/=[/color] p;
                q [color=#666666]*=[/color] p;
            }
            [color=#008000]**return**[/color] (p [color=#666666]-[/color] [color=#666666]1[/color])[color=#666666]*[/color]q[color=#666666]*[/color]phi(m);
        }
        p [color=#666666]+=[/color] [color=#666666]1[/color];
    }
}

[color=#408080]*/* Find the number of bits of n ( = floor(log_2(n + 1))). */*[/color]
[color=#B00040]unsigned[/color] [color=#B00040]int[/color] lg([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] n) {
    mpz_class m(n);
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]0[/color];

    [color=#008000]**while**[/color] (m [color=#666666]>[/color] [color=#666666]0[/color]) {
        m [color=#666666]>>=[/color] [color=#666666]1[/color];
        [color=#666666]++[/color]k;
    }

    [color=#008000]**return**[/color] k;
}

[color=#408080][i]/* Usage: instantiate this class on a positive integer and either cast
 * it to a string (for informative output) or a bool (for a simple
 * true/false determination of the primality of the integer).
 */[/i][/color]

[color=#008000]**class**[/color] [color=#0000FF]**primality_check**[/color] {
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] r;
    mpz_class n;
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] lgn; [color=#408080][i]// log_2(n)
[/i][/color]    [color=#B00040]bool[/color] val;

    mpz_class accum;

    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] cell_size;
    mpz_class cell_mask;
    mpz_class full_mask;

    std[color=#666666]::[/color]ostringstream messages;

    [color=#B00040]void[/color] dump([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] P) {
        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]0[/color]; k [color=#666666]<[/color] r; [color=#666666]++[/color]k) {
            mpz_class coeff(P [color=#666666]&[/color] (cell_mask [color=#666666]<<[/color] (cell_size [color=#666666]*[/color] k)));
            coeff [color=#666666]>>=[/color] cell_size [color=#666666]*[/color] k;
            std[color=#666666]::[/color]cout [color=#666666]<<[/color] coeff [color=#666666]<<[/color] [color=#BA2121]' '[/color];
        }
        std[color=#666666]::[/color]cout [color=#666666]<<[/color] std[color=#666666]::[/color]endl;
    }

    [color=#408080]*/* Reduce accum mod (x^r - 1) after a multiplication */*[/color]
    [color=#B00040]void[/color] reduce_poly() {
        accum [color=#666666]+=[/color] (accum [color=#666666]>>[/color] (cell_size [color=#666666]*[/color] r));
        accum [color=#666666]&=[/color] full_mask;
    }

    [color=#408080]*/* Reduce accum mod (n) after arithmetic */*[/color]
    [color=#B00040]void[/color] reduce_coeffs() {
        mpz_class temp([color=#666666]0[/color]);
        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]0[/color]; k [color=#666666]<[/color] r; [color=#666666]++[/color]k) {
            mpz_class coeff(accum [color=#666666]&[/color] (cell_mask [color=#666666]<<[/color] (cell_size [color=#666666]*[/color] k)));
            coeff [color=#666666]>>=[/color] cell_size [color=#666666]*[/color] k;
            coeff [color=#666666]%=[/color] n;

            temp [color=#666666]^=[/color] (coeff [color=#666666]<<[/color] (cell_size [color=#666666]*[/color] k));
        }
        [color=#408080][i]//dump(temp);
[/i][/color]        accum [color=#666666]=[/color] temp;
    }

    [color=#408080]*/* Compute (x + a)^n and put result in accum. */*[/color]
    [color=#B00040]void[/color] pow([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] a) {
        accum [color=#666666]=[/color] [color=#666666]1[/color];
        accum [color=#666666]<<=[/color] cell_size;
        accum [color=#666666]+=[/color] a;

        [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] lgn [color=#666666]-[/color] [color=#666666]1[/color]; k [color=#666666]>[/color] [color=#666666]0[/color]; [color=#666666]--[/color]k) {
            accum [color=#666666]*=[/color] accum;
            reduce_poly();

            [color=#008000]**if**[/color] ((mpz_class((n [color=#666666]>>[/color] (k[color=#666666]-[/color][color=#666666]1[/color]))).get_ui() [color=#666666]&[/color] [color=#666666]1[/color]) [color=#666666]==[/color] [color=#666666]1[/color]) {
                accum [color=#666666]=[/color] (accum [color=#666666]*[/color] a) [color=#666666]+[/color] (accum [color=#666666]<<[/color] cell_size);
                reduce_poly();
            }
            reduce_coeffs();
        }
    }

    [color=#408080]*/* Determine if (x + a)^n == x^n + a. */*[/color]
    [color=#B00040]bool[/color] test([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] a) {
        pow(a);

        [color=#B00040]unsigned[/color] [color=#B00040]int[/color] idx [color=#666666]=[/color] mpz_class(n [color=#666666]%[/color] r).get_ui();
        mpz_class target([color=#666666]1[/color]);
        target [color=#666666]<<=[/color] (cell_size [color=#666666]*[/color] idx);
        target [color=#666666]+=[/color] a;

        [color=#008000]**return**[/color] accum [color=#666666]==[/color] target;
    }

[color=#008000]**public**[/color][color=#666666]:[/color]
    primality_check([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] p);

    [color=#008000]**operator**[/color] [color=#B00040]bool[/color] () [color=#008000]**const**[/color] {
        [color=#008000]**return**[/color] val;
    }

    [color=#008000]**operator**[/color] std[color=#666666]::[/color]string () [color=#008000]**const**[/color] {
        [color=#008000]**return**[/color] messages.str();
    }
};

primality_check[color=#666666]::[/color]primality_check([color=#008000]**const**[/color] mpz_class [color=#666666]&[/color] p) 
    [color=#666666]:[/color] n(p), lgn(lg(n))
{
    [color=#008000]**if**[/color] (n [color=#666666]==[/color] [color=#666666]0[/color]) {
        val [color=#666666]=[/color] [color=#008000]**false**[/color];
        messages [color=#666666]<<[/color] [color=#BA2121]"Zero!"[/color];
        [color=#008000]**return**[/color];
    }

    [color=#008000]**if**[/color] (n [color=#666666]==[/color] [color=#666666]1[/color]) {
        val [color=#666666]=[/color] [color=#008000]**false**[/color];
        messages [color=#666666]<<[/color] [color=#BA2121]"Unit!"[/color];
        [color=#008000]**return**[/color];
    }

    [color=#408080][i]// 1. Check if n is a perfect power
[/i][/color]    mpz_class m(n);
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] b [color=#666666]=[/color] [color=#666666]1[/color];
    [color=#008000]**while**[/color] (m [color=#666666]>[/color] [color=#666666]1[/color]) {
        [color=#666666]++[/color]b;
        m [color=#666666]=[/color] root(n, b);
        [color=#008000]**if**[/color] (power(m, b) [color=#666666]==[/color] n) {
            val [color=#666666]=[/color] [color=#008000]**false**[/color];
            messages [color=#666666]<<[/color] [color=#BA2121]"Composite! ("[/color] 
                     [color=#666666]<<[/color] n [color=#666666]<<[/color] [color=#BA2121]" = "[/color] [color=#666666]<<[/color] m [color=#666666]<<[/color] [color=#BA2121]"^"[/color] [color=#666666]<<[/color] b [color=#666666]<<[/color] [color=#BA2121]")"[/color];
            [color=#008000]**return**[/color];
        }
    }

    [color=#408080][i]// 2. Determine r
[/i][/color]    mpz_class target(lgn[color=#666666]*[/color]lgn);
    
    mpz_class order([color=#666666]0[/color]);
    r [color=#666666]=[/color] [color=#666666]1[/color];

    [color=#008000]**while**[/color] (order [color=#666666]<[/color] target) {
        [color=#666666]++[/color]r;
        order [color=#666666]=[/color] [color=#666666]1[/color];
        [color=#B00040]unsigned[/color] [color=#B00040]int[/color] q [color=#666666]=[/color] mpz_class(n [color=#666666]%[/color] r).get_ui();

        [color=#008000]**while**[/color] (q [color=#666666]!=[/color] [color=#666666]1[/color]) {
            [color=#008000]**if**[/color] (order [color=#666666]>=[/color] target) {
                [color=#008000]**break**[/color];
            }

            q [color=#666666]=[/color] mpz_class((q [color=#666666]*[/color] n) [color=#666666]%[/color] r).get_ui();
            [color=#666666]++[/color]order;
        }
    }

    [color=#408080][i]// 3. Check if n has any proper factors up to r
[/i][/color]    [color=#008000]**for**[/color] ([color=#B00040]unsigned[/color] [color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]2[/color]; k [color=#666666]<=[/color] r; [color=#666666]++[/color]k) {
        [color=#008000]**if**[/color] (n [color=#666666]%[/color] k [color=#666666]==[/color] [color=#666666]0[/color]) {
            [color=#008000]**if**[/color] (k [color=#666666]==[/color] n) {
                [color=#408080][i]// 4. We actually just proved n is prime
[/i][/color]                val [color=#666666]=[/color] [color=#008000]**true**[/color];
                messages [color=#666666]<<[/color] [color=#BA2121]"Prime! (checked exhaustively)"[/color];
                [color=#008000]**return**[/color];
            } [color=#008000]**else**[/color] {
                val [color=#666666]=[/color] [color=#008000]**false**[/color];
                messages [color=#666666]<<[/color] [color=#BA2121]"Composite! (divisible by "[/color] [color=#666666]<<[/color] k [color=#666666]<<[/color] [color=#BA2121]")"[/color];
                [color=#008000]**return**[/color];
            }
        }
    }

    [color=#408080][i]// 5. Polynomial test (the heart of the algorithm)
[/i][/color]    
    mpz_class limit((root(phi(r), [color=#666666]2[/color]) [color=#666666]+[/color] [color=#666666]1[/color])[color=#666666]*[/color]lgn);
    
    [color=#408080][i]/* This should give us enough padding to do an operation of type 
       accum = accum^2*(x + a) without reducing mod n until the end */[/i][/color]
    cell_size [color=#666666]=[/color] lgn [color=#666666]+[/color] lgn [color=#666666]+[/color] lg(r) [color=#666666]+[/color] lg(limit [color=#666666]+[/color] [color=#666666]1[/color]);

    cell_mask [color=#666666]=[/color] [color=#666666]1[/color];
    cell_mask [color=#666666]<<=[/color] cell_size;
    [color=#666666]--[/color]cell_mask;

    full_mask [color=#666666]=[/color] [color=#666666]1[/color];
    full_mask [color=#666666]<<=[/color] r[color=#666666]*[/color]cell_size;
    [color=#666666]--[/color]full_mask;

    [color=#008000]**for**[/color] (mpz_class a [color=#666666]=[/color] [color=#666666]1[/color]; a [color=#666666]<=[/color] limit; [color=#666666]++[/color]a) {
        [color=#008000]**if**[/color] ([color=#666666]![/color]test(a)) {
            val [color=#666666]=[/color] [color=#008000]**false**[/color];
            messages [color=#666666]<<[/color] [color=#BA2121]"Composite! (failed polynomial test with a = "[/color]
                     [color=#666666]<<[/color] a [color=#666666]<<[/color] [color=#BA2121]", r = "[/color] [color=#666666]<<[/color] r [color=#666666]<<[/color] [color=#BA2121]")"[/color];
            [color=#008000]**return**[/color];
        }
    }

    [color=#408080][i]// 6.
[/i][/color]    val [color=#666666]=[/color] [color=#008000]**true**[/color];
    messages [color=#666666]<<[/color] [color=#BA2121]"Prime! (passed all tests)"[/color];
}

std[color=#666666]::[/color]ostream [color=#666666]&[/color] [color=#008000]**operator**[/color] [color=#666666]<<[/color] (std[color=#666666]::[/color]ostream [color=#666666]&[/color] os, [color=#008000]**const**[/color] primality_check [color=#666666]&[/color] PC) {
    os [color=#666666]<<[/color] [color=#008000]**static_cast**[/color][color=#666666]<[/color]std[color=#666666]::[/color]string[color=#666666]>[/color](PC);
    [color=#008000]**return**[/color] os;
}

[color=#B00040]int[/color] main([color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]**[/color]argv) {
    [color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

    [color=#008000]**if**[/color] (argc [color=#666666]<[/color] [color=#666666]2[/color]) {
        cerr [color=#666666]<<[/color] [color=#BA2121]"Usage: "[/color] [color=#666666]<<[/color] argv[[color=#666666]0[/color]] [color=#666666]<<[/color] [color=#BA2121]" number_to_test"[/color] [color=#666666]<<[/color] endl;
        [color=#008000]**return**[/color] [color=#666666]1[/color];
    }

    istringstream is(argv[[color=#666666]1[/color]]);

    mpz_class n;

    [color=#008000]**if**[/color] ([color=#666666]![/color](is [color=#666666]>>[/color] n)) {
        cerr [color=#666666]<<[/color] [color=#BA2121]"Usage: "[/color] [color=#666666]<<[/color] argv[[color=#666666]0[/color]] [color=#666666]<<[/color] [color=#BA2121]" number_to_test"[/color] [color=#666666]<<[/color] endl;
        [color=#008000]**return**[/color] [color=#666666]1[/color];
    }

    primality_check PC(n);
    cout [color=#666666]<<[/color] PC [color=#666666]<<[/color] endl;

    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```To compile: ```
 g++ -ansi -Wall -pedantic -lgmpxx -lgmp -O3 aks_gmp.cpp -o aks_gmp
```You will need libgmpxx. Typical results on my computer: ```
%> time aks_gmp 15485867
Prime! (passed all tests)

real    1m37.072s
user    1m36.570s
sys     0m0.020s
%> time aks_gmp 25775050868797
Composite! (failed polynomial test with a = 1, r = 2027)

real    0m5.405s
user    0m5.376s
sys     0m0.008s

``` (Note that 25775050868797 = 7368791*3497867, a product of two primes.)

---

### Post by uljanow on 2008-10-15
A slightly modified java version which uses miller-rabin-test
[PHP]import java.util.*;

public class PrimeTest {
	private static long modExp(int b, int e, int m) {
		long c = 1;
		for (int i = 0; i < e; i++)
			c = (b*c) % m;
		return c;
	}
	public static boolean isPrime(int p, int k) {
		if (p < 2 || k < 1) return false;
		Random rnd = new Random(System.currentTimeMillis());
		for (int i = 0; i < k; i++) 
			if (modExp(1 + rnd.nextInt(p-1), p-1, p) != 1)
				return false;
		return true;		
	}
	public static void main(String[]args) {
		System.out.println( "enter a number to check if its prime or not");
		if (isPrime(new Scanner(System.in).nextInt(), 100))
			System.out.println("prime");
		else
			System.out.println("not a prime.");
	}
}[/PHP]

---

### Post by mosty friedman on 2008-10-15
```

(0x01 & n) == 0

```
very interesting trick, thanks for the tip..but can you explain to me what does this part do???

---

### Post by unutbu on 2008-10-15
0x01 is hexadecimal notation for the number 1.
& is the bit-and operator.
n is an integer.

Think in binary. If n is even then its binary representation will end in a 0.  0x01 has a binary reprensentation that ends in a 1. If you bit-and 0 and 1, you get 0. So

(0x01 & n) == 0 

is true if  n is even. Similarly, the expression is false if n is odd. So it is a test if n is even or odd.

In the greater context of the previous post, the code is expressing the idea that numbers which are strictly less than 2 or even are not prime.

---

### Post by mosty friedman on 2008-10-15
> **unutbu said:**
> 0x01 is hexadecimal notation for the number 1.
& is the bit-and operator.
n is an integer.

Think in binary. If n is even then its binary representation will end in a 0.  0x01 has a binary reprensentation that ends in a 1. If you bit-and 0 and 1, you get 0. So

(0x01 & n) == 0 

is true if  n is even. Similarly, the expression is false if n is odd. So it is a test if n is even or odd.

In the greater context of the previous post, the code is expressing the idea that numbers which are strictly less than 2 or even are not prime.
to check if a number is even cant we just do this if( n%2 == 0 )...i;m sorry i'm not really familiar with the binary operators, can you please tell me in which situations they could become really helpful

---

### Post by pp. on 2008-10-15
> **mosty friedman said:**
> to check if a number is even cant we just do this if( n%2 == 0 )...i;m sorry i'm not really familiar with the binary operators, can you please tell me in which situations they could become really helpful

A division operation takes more time (uses more CPU cycles) than a bitwise AND. At least, this used to be true for all processors of a few years ago.

---

### Post by unutbu on 2008-10-15
Sure, n%2 == 0 works too. I believe (0x01 & n)==0 may be faster however, since the bit-and operation is extremely easy for computers to do, while taking the modulus of a number is in general more complicated.


For information on what the bit-and operation does, perhaps see this page: [http://en.wikipedia.org/wiki/Binary_and](http://en.wikipedia.org/wiki/Binary_and)

The key idea is that 0 is associated with False, and 1 is associated with True. So 0 & 1 (sort-of) means False and True, which, according to the rules of logic, yields False (i.e. 0).

---

### Post by pp. on 2008-10-27
[SIZE="5"]**APL**[/SIZE]

(&#8764;R&#8712;R°.×R)/R&#8592;1&#8595;&#953;R

No, I don't speak APL. It's from [Wikipedia]("http://en.wikipedia.org/wiki/APL_(programming_language)#APL_Glossary")

---

### Post by tom66 on 2008-10-27
Efficient C version:

```

bool is_prime(int n)
{
	int y = 2;
	int m = (int)ceil(sqrt(n));
	
	if(n == 0 || n == 1) return false;
	if(n == 2) return true;
	
	for(; y < m; y++)
	{
		if(y % n == 0)
			return false;
	}
	
	return true;
}

```

Overly-complex and probably slower version: 

```

bool is_prime(int n)
{
	int y = 2;
	int m = (int)ceil(sqrt(n));
	
	if(n == 0 || n == 1) return false;
	if(n == 2) return true;

	for(; y < m; y++)
	{
		if((log(y) / log(2)) % 1 == 0)
			((x & (y - 1)) == 1) ? (y + 0)
				: return false;
		
		if(y % n == 0)
			return false;
	}
	
	return true;
}

```

---

### Post by jimi_hendrix on 2008-10-27
what does the semi-colen in the for loop do?

---

### Post by Bichromat on 2008-10-27
> **tom66 said:**
> Efficient C version:

```

bool is_prime(int n)
{
	int y = 2;
	int m = (int)ceil(sqrt(n));
	
	for(; y < m; y++)
	{

		if(y % n == 0)
			return false;
	}
	
	return true;
}

```


This version is incorrect and quite inefficient : it gives wrong results for n<2, and it calculates y%n for n even, which is unnecessary.

---

### Post by tom66 on 2008-10-27
Well, it worked for my Ulam spiral script which produced good results, identical to known good spirals. I did make a modification, I removed the second assignment in the loop. Square root is there because it's the HCF of that number, in any case. 

I see what you mean for the dividing <2, I'll try to correct that.

---

### Post by jimi_hendrix on 2008-10-27
@ tom66

what does that ; in the for loop declaration do?

---

### Post by snova on 2008-10-27
> **jimi_hendrix said:**
> @ tom66

what does that ; in the for loop declaration do?
Nothing. Ordinarily a for loop looks like:

[php]for( INITIALIZATION ; CONDITION ; POST-BODY )[/php]

But there is no initialization code in this loop, so he leaves it out. But the semi-colon is still necessary.

---

### Post by jimi_hendrix on 2008-10-27
> **snova said:**
> Nothing. Ordinarily a for loop looks like:

[php]for( INITIALIZATION ; CONDITION ; POST-BODY )[/php]

But there is no initialization code in this loop, so he leaves it out. But the semi-colon is still necessary.

interesting...i thought it was one of those C triks that i never learned...

---

### Post by Bichromat on 2008-10-28
> **tom66 said:**
> Well, it worked for my Ulam spiral script which produced good results, identical to known good spirals. I did make a modification, I removed the second assignment in the loop. Square root is there because it's the HCF of that number, in any case.

Oops, I meant it calculates n % y for every y (it's y % n in your code by the way, that's what confused me). When entering the loop, you should have established that n is not divisible by 2, so there's no use to test n % 4, n % 6 etc.
The loop should start with y = 3 and the increment should be 2, so as to test odd integers only (twice faster).

---

### Post by efittery on 2009-04-05
In J, the easiest to write test would be:

1 p: <some number>

which returns 1 if prime and 0 if not prime

1 p: 3
1

1 p: 5
1

1 p: 2147483658 which is ( 2^31)
1 p: 2147483647 which is ((2^31)-1)

now about bigger numbers, say like ((2^127-1) which is:
170141183460469231731687303715884105727

1 p: 170141183460469231731687303715884105727
1

slower

How about ((2^521) - 1) which is:

6864797660130609714981900799081393217269435300143305
4093944634591855431833976560521225596406614545549772
96311391480858037121987999716643812574028291115057151

1 p: ((2x^521) - 1)
1

Really slow.

A better approach is needed to handle numbers like:

((2x^43112609) -1) which is a number that is 12978189 digits long.

 Electronic Frontier Foundation is offering a $150,000 award to the first person or group to discover a 100 million digit prime number! See how GIMPS will distribute this award if we are lucky enough to find the winning 100 million digit prime.

Good luck

---

### Post by samjh on 2009-04-05
[SIZE="5"]Ada[/SIZE]

Naive algorithm.

```
with Ada.Text_IO, Ada.Integer_Text_IO, Ada.Command_Line;

use Ada.Text_IO, Ada.Integer_Text_IO, Ada.Command_Line;

procedure Prime is
	Target : Integer;
	Result : Boolean := True;
begin
	Target := Integer'Value(Argument(1));

	if Target > 1 then
		for N in Integer range 2..(Target-1) loop
			if Target mod N = 0 then
				Result := False;
				exit;
			end if;
		end loop;
	else
		Result := False;
	end if;

	if Result = True then
		Put_Line("Prime");
	else
		Put_Line("Non-Prime");
	end if;
end Prime;
```

To compile and run:
1. Install GNAT (sudo apt-get install gnat).
2. Save code into file: prime.adb
3. Compile using command: gnat make prime.adb
4. Usage: ./prime [integer]. Example: ./prime 10000

---

### Post by ZuLuuuuuu on 2009-04-06
Here is an algorithm in two languages, I wrote while doing Project Euler problems :)

**Tcl:**

```
proc is_prime {number} {
    set j 2
    
    while {$number % $j != 0} {
        incr j
    }
    
    if {$j == $number} {
        return 1
    } else {
        return 0
    }
}
```

**Smalltalk:**

```
Integer extend [
	isPrime [
		| i |

		i := 2.

		[self \\ i = 0] whileFalse: [
			i := i + 1.
		].

		(i = self) ifTrue: [
			^true
		] ifFalse: [
			^false
		].
	]
]
```

---

### Post by sujoy on 2009-04-06
highly inefficient haskell code, but its uber simple :P

```

factors num      = [x | x <- [1..num], num `mod` x == 0]
prime num        = factors num == [1,num]

```

---

### Post by Wybiral on 2009-04-06
**[SIZE="4"]Python (a bit more pythonic)[/SIZE]**

```

from math import sqrt

def isprime(n):
    highest = int(sqrt(n)) + 1
    if n > 1 and all(n % x > 0 for x in range(2, highest)):
        return True
    else:
        return False

```

This could easily be a one-liner, albeit less explicit and thus not Pythonic at all (true Python code should never look like this!) But just for kicks:
```

isprime = lambda n: n > 1 and all(n % x for x in range(2, int(n ** 0.5) + 1))

```

---

### Post by Simian Man on 2009-04-06
```
[color=#408080]*(* Ocaml *)*[/color]

[color=#0000FF]**Printf**[/color].printf [color=#BA2121]"Enter number: "[/color][color=#666666];[/color]
[color=#008000]**let**[/color] value [color=#666666]=[/color] read_int [color=#008000]()[/color] [color=#008000]**in**[/color]
[color=#008000]**let**[/color] is_prime x [color=#666666]=[/color]
  [color=#008000]**let**[/color] bound [color=#666666]=[/color] int_of_float [color=#666666]([/color]ceil [color=#666666]([/color]sqrt [color=#666666]([/color]float_of_int x[color=#666666])))[/color] [color=#008000]**in**[/color]
  [color=#008000]**let**[/color] [color=#008000]**rec**[/color] ip_aux x n [color=#666666]=[/color]
    [color=#008000]**if**[/color] n [color=#666666]>[/color] bound [color=#008000]**then**[/color] [color=#008000]true[/color]
    [color=#008000]**else**[/color] [color=#008000]**if**[/color] [color=#666666]([/color]x [color=#AA22FF]**mod**[/color] n[color=#666666])[/color] [color=#666666]==[/color] [color=#666666]0[/color] [color=#008000]**then**[/color] [color=#008000]false[/color]
    [color=#008000]**else**[/color] [color=#666666]([/color]ip_aux x [color=#666666]([/color]n [color=#666666]+[/color] [color=#666666]1[/color][color=#666666]))[/color]
  [color=#008000]**in**[/color] [color=#666666]([/color]ip_aux x [color=#666666]2[/color][color=#666666])[/color]
[color=#008000]**in**[/color] [color=#0000FF]**Printf**[/color].printf [color=#BA2121]"%d is %s[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color] value [color=#666666]([/color][color=#008000]**if**[/color] [color=#666666]([/color]is_prime value[color=#666666])[/color] [color=#008000]**then**[/color] [color=#BA2121]"prime"[/color] [color=#008000]**else**[/color] [color=#BA2121]"not prime"[/color][color=#666666])[/color]

```

---

### Post by SirGe on 2010-09-12
This thread is a bit stale, but I could not hold myself back...

A perl/regexp command line hack (with optimizations at that!):

```
$ perl -le 'print+((1x shift)=~/^1?$|^(11+?)\1+$/&&"not "),"prime"' <number>
```

Use it like so:

```
perl -le 'print+((1x shift)=~/^1?$|^(11+?)\1+$/&&"not "),"prime"' 315779
```

By the way, that's about the limit of how far it will work (unless you have extra patience and spare time :))

Enjoy figuring out how it works...

Dis Claimer: not my code, Abigail did it first, I think.

---

### Post by roobie on 2011-05-10
This is my contribution: (D v2)

```
#!/usr/bin/rdmd
import std.stdio;
import std.math;

bool isPrime(long n) {

    int factors;

    real cieling = sqrt(n);

    if (n == 0) {
        return false;
    }    
    
    for (long i = 2; i <= cieling; ++i) {
        if (factors != 0) {
            return false;
        }
        
        if (n % i == 0) {
            factors++;
            while (n % i == 0) {
                n /= i;
                factors++;
            }
        }
    }
    return true;
}

void main() {
    writeln(isPrime(0));
    writeln(isPrime(1));
    writeln(isPrime(2));
    writeln(isPrime(3));
    writeln(isPrime(1111111111111111111));
}
```

If you have the DMD d-compiler v2.x just run it as a script, i.e.
```
./<file name>.d
```

---

### Post by Klaus Viuhka on 2012-01-12
General, easy "sysadmin style" shell one-liner (gnu utils, not exactly programming language, but...)

```
seq 20 | factor | perl -ane 'printf "%s %sprime\n", $F[0], ($#F == 1) ? "" : "not "'
```

---

### Post by KdotJ on 2012-01-12
Just for the laughs... here it is in LOLcode:

```
HAI
CAN HAS STDIO?

GIMMEH VAR
I HAS A NUM
LOL NUM R 2

IM IN YR LOOP
    UP NUM!!1
    IZ NUM BIGGER THAN VAR? GTFO
    
    I HAS A TEMP
    LOL TEMP R VAR % NUM
    
    IZ TEMP LIEK 0?
        YARLY
            VISIBLE Not Prime!
            GTFO
    KTHX
IM OUTTA YR LOOP

IS NUM LIEK VAR? VISIBLE Prime Number!
KTHXBYE

```


PS. It may be wrong lol, I haven't ever attempted to compile and run LOLcode.

---

