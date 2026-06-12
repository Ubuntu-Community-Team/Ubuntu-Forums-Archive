---
title: "Perplexing issue with Java and decimals"
date: 2012-09-30
forum: Programming Talk
---

### Post by Litost on 2012-09-30
Hi everyone! I am fairly new to Ubuntu, very new to programming, and am dumbfounded by this and am sure you lovely folk can help:

public class Change {

    public static void main(String[] args) {
        double purchase = 19.93;
        double payment = 20.00;
        double change = (payment) - (purchase);
        System.out.println(change);
    }

}
which outputs 0.07000000000000028 ?!?!!? In what universe does 20.00 - 19.93 equal anything besides 0.07? I know there are ways I can adjust how many decimal places it rounds to but what disturbs me more is that there are additional decimal places to begin with! Why is this happening? Is there a way to fix it besides changing the amount of decimal places it outputs? Thanks so much for your time.

---

### Post by Vaphell on 2012-09-30
precision is not infinite and there are rounding errors introduced if the binary representation of the numbers doesn't fit the amount of memory given to store them. That's how floating point numbers behave in general, it's not only java.

If you operate on fixed precision numbers you can move to the realm of integers: count cents and print out cents/100 to get value on screen.

---

### Post by Litost on 2012-09-30
Sorry, I still don't understand. I get that there is not enough memory to be precise, but is that because I used double? Should I be using another declaration besides double to get a more accurate answer? I tried float and the answer was even more bizarre. I'm really confused because this isn't the first time I've done basic arithmetic operations in Java but the first time I got such an inaccurate answer and I can't see what I did differently. This one prints everything correctly:  
        double x = 2.5;
        double y = -1.5;
        int m = 18;
        int n = 4;
        System.out.println(x + n * y - (x + n) * y);
        System.out.println(m/n + m % n);
        System.out.println(1 - (1 - (1 - (1 - (1 - n)))));
        System.out.println(Math.sqrt(Math.sqrt(n)));
and it is seemingly much more complicated?

---

### Post by Vaphell on 2012-09-30
these numbers and the results of operations on them are rather easy to write in powers of 2
2.5 = 1*2^1 + 0*2^0 + 1*2^-1


numbers you get in your program are not as pretty, they expand to infinite sequence (or a sequence longer than the length of double) which gets truncated to fit the size of double - rounding error is born.

---

### Post by Litost on 2012-09-30
Right, so is there a different declaration I can use besides double that will allow me to do simple arithmetic with numbers like in the change  program? I'm also not sure how 20.00 can expand infinitely as it's 4 characters long but I think that's over my head as I'm only in my first year of programming.

---

### Post by Vaphell on 2012-09-30
20 is pretty, but apparently 0.07 is not.
As i said, you can internally operate on integers where 100 is an equivalent of $1.00
200-193 will give you 7 with no loss of precision. When you need to show the numbers, you just print number/100 to the screen and maybe force number of decimals to make the output pretty.

---

### Post by Litost on 2012-09-30
Thank you so much! I'll use /100 for the change as you suggested. I was convinced the question was wanting me to change to a different declaration so the values would give a clean answer, so it's good you steered me away from that as otherwise I'd be reading all night looking for a solution that doesn't exist.

---

### Post by Tony Flury on 2012-09-30
> **Litost said:**
> Right, so is there a different declaration I can use besides double that will allow me to do simple arithmetic with numbers like in the change  program? I'm also not sure how 20.00 can expand infinitely as it's 4 characters long but I think that's over my head as I'm only in my first year of programming.

It is nothing to do with the number of characters. all numbers have to be represented in binary (base 2) so 20 is actually 1010 (base 2) (16+4).

All integers can be accurately represented so long as you have enough memory.

All non-integers are a problem though - think about what 0.77 means in base 10 : it means 7/10 + 7/100.

Similarly fractions in binary have to be represented by the closest value made from sums of 1/2, 1/4, 1/8 etc.

so 0.77 is something like 0.11000101 (base 2) ... (which is actually 0.7695315) - i suspect that 0.77 is one of those values that can never be accurately represented as a finite length binary fraction (just like 1/3 can not be accurately represented as a finite length decimal fraction).

---

### Post by ofnuts on 2012-09-30
> **Litost said:**
> Right, so is there a different declaration I can use besides double that will allow me to do simple arithmetic with numbers like in the change  program? I'm also not sure how 20.00 can expand infinitely as it's 4 characters long but I think that's over my head as I'm only in my first year of programming.

When you write 1/3 as a decimal, you write it as ".333333" with some fixed numbers of decimals. If you multiply by 3, you get ".999999" and not "1". Numbers in computers are stored using powers of 2 instead of powers of 10, and exactly like 1/3 cannot be expressed as a finite number of powers of 10, there are numbers that cannot be expressed with the fixed number of powers of 2 allowed in their binary representation, even if these same numbers can be written with a small number of power of 10. 

In the financial world they don't use floating point to express monetary values. Java has a [BigDecimal]("http://docs.oracle.com/javase/1.5.0/docs/api/java/math/BigDecimal.html") type for this.

---

### Post by Litost on 2012-09-30
Thank you ofnuts! You explained it very well to my newbie brain.

---

### Post by Unterseeboot_234 on 2012-09-30
If you want precision units, use type long. Currency is units of pennys. Double will trunicate decimal math starting with 10^9. The underlying binary math trunicates into decimal results.

Currency is also a String. The format specifiers round up at .49 and do a better rounding than Math.round( x );

System.out.printf( "$%f.2", sumTotal * (1+salesTaxRate) );

But if you get serious about financial programming you will learn to reduce to the smallest unit ...

long totalPenny = (long) price / 100;
totalPenny += (long) price % 100;

---

