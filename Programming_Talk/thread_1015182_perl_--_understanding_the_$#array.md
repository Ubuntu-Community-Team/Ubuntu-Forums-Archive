---
title: "perl -- understanding the $#array"
date: 2008-12-18
forum: Programming Talk
---

### Post by badperson on 2008-12-18
Hi,
I'm working through the intermediate perl book, and one of the examples has this code:

```

my @input_numbers = (1, 2, 4, 8, 16, 32, 64);
my @indices_of_odd_digit_sums = grep {
  my $number = $input_numbers[$_];
  my $sum;
  $sum += $_ for split //, $number;
  $sum % 2;
} 0..$#input_numbers;
```

what is the $# array, and how does it work? 
if I change
```
0..$#input_numbers;[/
```

to ```
@input_numbers 
```
the output changes.
thanks,
bp

---

### Post by Martin Witte on 2008-12-18
see [this ]("http://docstore.mik.ua/orelly/perl/prog3/ch02_08.htm#INDEX-699") for the answer (it is the number of elements)

---

### Post by badperson on 2008-12-18
k, I think I may have figured it out...The $# array is an array of the indices from the array being checked that match the expression in the grep block...is that right? 
btw...didn't see the post above when I posted this
bp

---

### Post by nvteighen on 2008-12-18
Perl is far more logical than some think.

$ means it's a scalar, so there's no way that is an array. It can't be the number of elements because for that you use @array in scalar context (e.g. **if (@array < 9)** in Perl is equivalent to **if len(array) < 9** in Python). So, what is it?

$#array returns the last used index at @array. So, if your @array is 4 elements long, $#array will be 3 (0, 1, 2, 3).

That's it. In summary: $#array = @array - 1

---

### Post by badperson on 2008-12-18
gotcha..., that makes sense. another comparison is arrayname.length in java, right? 

bp

---

### Post by slavik on 2008-12-19
> **nvteighen said:**
> Perl is far more logical than some think.

$ means it's a scalar, so there's no way that is an array. It can't be the number of elements because for that you use @array in scalar context (e.g. **if (@array < 9)** in Perl is equivalent to **if len(array) < 9** in Python). So, what is it?

$#array returns the last used index at @array. So, if your @array is 4 elements long, $#array will be 3 (0, 1, 2, 3).

That's it. In summary: $#array = @array - 1
You have seen the light!!!

Perl6 = @array.length :)

---

### Post by ZuLuuuuuu on 2008-12-19
> **slavik said:**
> Perl6 = @array.length :)

Is that true or should it be:
```

Perl 5 = $#array
Perl 6 = @array.length - 1
```

Everything can be expected from Larry that's why I asked :D

---

### Post by pmasiar on 2008-12-19
> **slavik said:**
> You have seen the light!!!

Yes, I've seen the light: Perl6 changes rather substantial assumptions:

in Perl5, $anything is **always** scalar, @something is **always** array (even slice from %hash: @slice = @hash{@list} )

in Perl6, @array.length is scalar, so the logic nvteighen mentioned goes out of the window.

So I do not see why any sane person would switch to Perl6 - but then, after using Perl5 for couple years, would they be able to keep their sanity? :twisted:

---

### Post by nvteighen on 2008-12-19
> **slavik said:**
> You have seen the light!!!

Perl6 = @array.length :)
Hmmm... I don't like that, unless the whole Perl semantic system is also changed...

I'd actually prefer $array.length, if Larry asked me :)

---

