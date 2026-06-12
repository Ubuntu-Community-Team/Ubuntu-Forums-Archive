---
title: "Recursion confusion help requested"
date: 2013-04-13
forum: Programming Talk
---

### Post by ToFue on 2013-04-13
Hi guys,
I'm absolutely stumped!
I have an assignment to recursively multiply multi-digit numbers digit by digit in java.  I'm not allowed to use "*", and must conform to the "elementary school algorithm" with NO iterations.. 
 
example: 

```
  
  1234   = x
x    52   = y
-------
  2468    (first pass of sending to multiplySingleDigit( x%10, y%10 ), reducing x by x/10 to get each digit.)
6170(0)  ( sequential passes must add a "0" at the end of the result)
-------
64168   = result of adding each 'pass'
```


So far my code goes through a single pass of either x or y if either has multiple digits, but if both have multiple digits my test fails.

my implement:
```

//testcase: 
    assertFalse( !(this.hw.multiply(this.i6, this.i6) == 576) );
// where i5 == 13 && i6 == 24


// meat of: int multiply(int x, int y)
  if (x < 10 && y < 10)
    result = multiplySingleDigit(x, y)
  else
    result = result + multiplySingleDigit( x%10,y%10 )
      + multiplyTens( multiply(x%10, y/10) + multiply( x/10, y%10 ) )
      + multiplyTens( multiplySingleDigit(x/10, y/10) );

// meat of: int multiplyTens(int i)
int result = 0;
if (x > 0) {
     result = Integer.parseInt( new String(x+"0") );
   }
return result;

```

I left out other trivial code for the sake of biting into the meat of the logic.. and my fallacies..

Can an experienced guru please show me where I'm going wrong? I'm going in circles trying to figure out where x or y should reduce a digit in the recursive step.

---

### Post by shawnhcorey on 2013-04-14
There are four steps to all recursion. They are:
[LIST=1]
[*]Handle the degenerate case, process it, and return the result.
[*]Break the problem into smaller parts.
[*]Apply recursion to each part.
[*]Combine the results of the parts to form the whole result.
[/LIST]
I have written [an article in Perl]("http://lookatperl.blogspot.ca/2012/11/a-look-at-recursion.html") on how to do this.

For this problem I would use two subroutines: one to split up the multiplier into single digits and call the second. The second one only works with single digit multipliers and splits the multiplicand into single digits.

---

### Post by ofnuts on 2013-04-14
I don't know what makes you so sure that "multiplySingleDigit(x/10, y/10) );" is only going to handle single-digit numbers...

Your basic problem is that you wrote code that yourself can't read or debug. You devised something that could work, but there are still some ideas that aren't completely clear, and nothing in your code to help you make them clearer. Don't try to be too clever. So:
[LIST]
[*]replace this humongous one-liner "result" computation by the same in "slow motion"
[LIST]
[*]all intermediate computations in their own variables (makes it so much easier to debug)(*) 
[*]gives them meaningful names, for instance: "[FONT=fixedsys]int lowTopByHighBottom= multiply(x % 10, y / 10);[/FONT]" 
[/LIST]
  
[*]add useful print statements (that you will remove before returning the assignment of course). 
[*]it is even better if they help you track where you are in the recursion.
[LIST]
[*]Add to all the multiply*() methods an indent parameter for the trace 
[*]Add some indent when calling recursive methods, ie: 
[/LIST]
   
[/LIST]
```

    static int multiplySingleDigit(String indent,int x, int y) {
        System.out.printf("%s multiplySingleDigits(%d,%d)\n", indent, x, y);
        [...]
    }

    static int multiply(String indent, int x, int y) {
        System.out.printf("%s multiply(%d,%d)\n", indent, x, y);
        [...]
            int lowTopByLowBottom=multiplySingleDigit("--"+indent,x % 10, y % 10);
            int lowTopByHighBottom= multiply("--"+indent,x % 10, y / 10);
        [...]

```

Eventually things will sort themselves out that way.

(*) Beginning coders are often ashamed to use variables for intermediate results, thinking one-liners are the hallmark of the seasoned programmer. Nothing is farther from the truth. Good programmers don't write much comments, but they do write very self-explanatory code.

---

