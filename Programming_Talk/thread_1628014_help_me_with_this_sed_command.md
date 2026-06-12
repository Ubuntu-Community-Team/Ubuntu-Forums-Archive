---
title: "help me with this sed command"
date: 2010-11-22
forum: Programming Talk
---

### Post by tisungho on 2010-11-22
Hi,

I want to extract the numeric value(s) in this text (HTML tag): <TD ALIGN=right>81</TD>

This is working:
```

echo "<TD ALIGN=right>81</TD>" | sed 's/.*\([0-9][0-9]\).*/\1/g'
81
```

However, the above line is not optimal because there's a hard coded number of digits. Then I write:

```

echo "<TD ALIGN=right>81</TD>" | sed 's/.*\([0-9]*\).*/\1/g'

```

It returns empty :(

Anyone knows how to make general 'rule' to extract whatever value  in that string please help!

Thanks!

---

### Post by Arndt on 2010-11-22
> **tisungho said:**
> Hi,

I want to extract the numeric value(s) in this text (HTML tag): <TD ALIGN=right>81</TD>

This is working:
```

echo "<TD ALIGN=right>81</TD>" | sed 's/.*\([0-9][0-9]\).*/\1/g'
81
```

However, the above line is not optimal because there's a hard coded number of digits. Then I write:

```

echo "<TD ALIGN=right>81</TD>" | sed 's/.*\([0-9]*\).*/\1/g'

```

It returns empty :(

Anyone knows how to make general 'rule' to extract whatever value  in that string please help!

Thanks!

If you use [0-9]+ or [0-9][0-9]* it ought to work. [0-9]* can match the empty string, so it does so at the first opportunity and doesn't see your digits.

---

### Post by bzhao on 2010-11-22
> **Arndt said:**
> If you use [0-9]+ or [0-9][0-9]* it ought to work. [0-9]* can match the empty string, so it does so at the first opportunity and doesn't see your digits.

I did test the below line as workable:

  echo "<TD ALIGN=right>812</TD>" | sed 's#[^0-9]*\([0-9]\+\).*#\1#g

---

### Post by ziekfiguur on 2010-11-22
> **tisungho said:**
> 
```

echo "<TD ALIGN=right>81</TD>" | sed 's/.*\([0-9]*\).*/\1/g'

```

It returns empty :(

Anyone knows how to make general 'rule' to extract whatever value  in that string please help!


The problem is that [0-9]* also matches an empty string, so the complete input would be matched by the first .*
By using a + instead of a * it matches at least one number, but than it could also put the 8 in the first .* and only the 1 in [0-9]+
A solution would be to make sure the .* only includes html tags, something like this:
```
echo "<TD ALIGN=right>81</TD>" | sed 's/<.*>\([0-9]*\)<.*>/\1/g'
```
This would also work if there were numbers inside the html tags.

---

### Post by Arndt on 2010-11-22
> **ziekfiguur said:**
> The problem is that [0-9]* also matches an empty string, so the complete input would be matched by the first .*
By using a + instead of a * it matches at least one number, but than it could also put the 8 in the first .* and only the 1 in [0-9]+


No, it has no such choice; the matches are as long as possible.

---

### Post by ziekfiguur on 2010-11-22
> **Arndt said:**
> No, it has no such choice; the matches are as long as possible.

Wouldn't it make the first match as long as possible?
If no, any idea why not?

---

### Post by Arndt on 2010-11-22
> **ziekfiguur said:**
> Wouldn't it make the first match as long as possible?
If no, any idea why not?

Which first match? I think there are too many different expressions mentioned now.

---

### Post by tisungho on 2010-11-22
Hi,

All of your suggestions do the trick :) 
thanks a lot!

I found the command from bzhao is more general, event with this string: 
<TD ALIGN=right><FONT color="red">1</FONT></TD>

> **bzhao said:**
> I did test the below line as workable:

  echo "<TD ALIGN=right>812</TD>" | sed 's#[^0-9]*\([0-9]\+\).*#\1#g

Can you explain a little bit about [^0-9]* in sed?

---

### Post by ziekfiguur on 2010-11-22
> **tisungho said:**
> 
Can you explain a little bit about [^0-9]* in sed?

[^something]

matches everything except `something', so [^0-9] would match all letters, punctuation and whitespace, only no numbers.

@ Arndt
if you use `.*([0-9]+).*' the first match would be .*, the second [0-9]+ and the third .* again. So, if the input is `<TD ALIGN=right>81</TD>' the longest possibility for the first match would be `<TD ALIGN=right>8' while still having a match for all three parts.

---

### Post by Arndt on 2010-11-22
> **ziekfiguur said:**
> [^something]

matches everything except `something', so [^0-9] would match all letters, punctuation and whitespace, only no numbers.

@ Arndt
if you use `.*([0-9]+).*' the first match would be .*, the second [0-9]+ and the third .* again. So, if the input is `<TD ALIGN=right>81</TD>' the longest possibility for the first match would be `<TD ALIGN=right>8' while still having a match for all three parts.

Yes, you are right. I was the one who was confused.

Right now I am wondering why these two give different results:

```
$ echo "foo812bar" | sed 's/\([0-9][0-9]*\)/x/g'
fooxbar
$ echo "foo812bar" | sed 's/\([0-9]+\)/x/g'
foo812bar
```

---

### Post by ziekfiguur on 2010-11-22
> **Arndt said:**
> 
Right now I am wondering why these two give different results:

```
$ echo "foo812bar" | sed 's/\([0-9][0-9]*\)/x/g'
fooxbar
$ echo "foo812bar" | sed 's/\([0-9]+\)/x/g'
foo812bar
```

I'm not really sure, personally I didn't even know you could use sed like that. According to the man page you should use -e before the commands you want to execute, and use -r if you want to use extended regex options. Also, i used to think that \( and \) would mean actual brackets to be found in the input. 
My version:
```
echo "foo812bar" | sed -re 's/([0-9]+)/x/g'
fooxbar
```
work right.

---

### Post by Arndt on 2010-11-22
> **ziekfiguur said:**
> I'm not really sure, personally I didn't even know you could use sed like that. According to the man page you should use -e before the commands you want to execute, and use -r if you want to use extended regex options. Also, i used to think that \( and \) would mean actual brackets to be found in the input. 
My version:
```
echo "foo812bar" | sed -re 's/([0-9]+)/x/g'
fooxbar
```
work right.

The -r is a new thing to me, and I have the feeling something backwards-incompatible has happened compared to how 'sed' worked the last 20 years. I suppose that means I have to be very careful when trying to help..

-e is not needed if the expression is the only argument.

---

