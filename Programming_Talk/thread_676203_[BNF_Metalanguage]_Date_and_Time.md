---
title: "[BNF Metalanguage] Date and Time"
date: 2008-01-23
forum: Programming Talk
---

### Post by TreeFinger on 2008-01-23
I have a homework assignment to create two 'programs' in BNF metalanguage.

Anyone familiar with this? The problem asks me to display the alphabet, terminals, and the procedures. I haven't been able to meet with my instructor and I was wondering if you guys/gals would check out my answer for the problem.

```

1. Date in BNF metalanguage

a. Alphabet = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, /}
b. Terminals: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, /
c. Production Rules:
<date> ::= <daypart>"/"<month-part>"/"<year-part>
<dec_d> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
<day-part> ::= <dec_d><dec_d>
<month-part> ::= <dec_d><dec_d>
<year-part> ::= <dec_d><dec_d>

2. Clock in BNF metalanguage
a. Alphabet = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, :, AM, PM}
b. Terminals: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, :, AM, PM
c. Production Rules:
<time> ::= <hour-part>":"<min-part>":"<sec-part><night_day>
<dec_d> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
<hour-part> ::= <dec_d><dec_d>
<min-part> ::= <dec_d><dec_d>
<sec-part> ::= <dec_d><dec_d>
<night_day> ::= "AM" | "PM"

```

We only went over this in one class so many questions were left unanswered for me. I am just not sure if I have the correct characters in my alphabets and terminal symbols lists.

Thanks, Sam.

---

### Post by public_void on 2008-01-23
Be careful with your day-part, month-part etc, because the rules allow any number to be combined with any other number. Therefore according to your rules 99/99/99 is a valid date. Split the individual components of the date and time into smaller rules. For example, seconds are in the range 00 - 59. So the first digit it 0 - 5 and the second digit is 0 - 9. Months are a bit trickier because they range from 01 - 12. This can be broken down into 01 - 09 and 10 to 12 which can be expressed easily.

Hopefully this explains it.

```

#Seconds
<sec_part> ::= <first_sec_digit><second_sec_digit>
<first_sec_digit> ::= 0 | 1 | 2 | 3 | 4 | 5
<second_sec_digit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 

#Months
<month_part> ::= <jan_to_sept> | <oct_to_dec>
<jan_to_sept> ::= 0 <jan_to_sept_digits>
<oct_to_dec> ::= 1 <oct_to_dec_digits>
<jan_to_sept_digits> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
<oct_to_dec_digits> ::= 0 | 1 | 2

```

---

### Post by TreeFinger on 2008-01-23
Thanks, I wasn't sure if it was needed to go that deeply into the restrictions.

The way I thought about it was a computer has no idea that in our time system there are only 12 months in a year so what if someone wants to use this program that uses 13 months as a year.

stupid, i know.

===edit

It seems like I can go on forever to cover these 'exceptions'. Like if the first digit in the day is 3, then the second digit can only be a 0 or a 1 but if the first digit in the day is 2, then the second digit can be 0-9.

---

### Post by popch on 2008-01-23
> **TreeFinger said:**
> Thanks, I wasn't sure if it was needed to go that deeply into the restrictions.

Don't feel bad about that. When to go deeper into restrictions and when not to is not all that clear cut. It depends a great deal on what you are going to do with the specifications.

Consider the improvements suggested above.

Your original design allowed dates like 12/34/56 which is not all that useful. After the suggested change, the design still allows 31/02/99 or 31/06/06 which are not really correct. It would be possible to define a syntax which takes all that into account, but the syntax would become rather more involved with each restriction you add. 

Once you become aware of that, you start detecting the value of documenting your code. 'Syntax does not take into account different lengths of months' or 'accounts for different lenghts of months but not for leap years' would be useful comments to add.

---

### Post by TreeFinger on 2008-01-23
Did the days real quick. I guess it is hard to read but what can you expect?

Would this be more acceptable?

---edit
finished up what I think is correct for the date. looking for a double check if possible! Thanks
```

<date> ::= <day-part>"/"<month-part>"/"<year-part>

#START OF DATE PART-DAY#
<day-part> ::= <day-lessthan-ten> | <day-greaterthan-nine> | <day-greaterthan-twentynine>

<day-lessthan-ten> ::= 0 <day-lessthan-ten-digits>
<day-lessthan-ten-digits> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<day-greaterthan-nine> ::= <day-greaterthan-nine-firstdigit><day-greaterthan-nine-seconddigit>
<day-greaterthan-nine-firstdigit> ::= 1 | 2 
<day-greaterthan-nine-seconddigit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<day-greaterthan-twentynine> ::= <day-greaterthan-twentynine-firstdigit> <day-greaterthan-twentynine-seconddigit>
<day-greaterthan-twentynine-firstdigit> ::= 3
<day-greaterthan-twentynine-seconddigit> ::= 0 | 1
#END OF DATE PART-DAY#


#START OF DATE MONTH-PART#
<month-part> ::= <month-jan-sept> | <month-oct-dec>

<month-jan-sept> ::= 0 <month-jan-sept-seconddigit>
<month-jan-sept-seconddigit> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<month-oct-dec> ::= 1 <month-oct-dec-seconddigit>
<month-oct-dec-seconddigit> ::= 0 | 1 | 2
#END OF DATE PART-MONTH#

#START OF DATE PART-YEAR#
<year-part> ::= <year-firstdigit><year-seconddigit>
<year-firstdigit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
<year-seconddigit> ::= 0 | 2 | 3 | 3 | 4 | 5 | 6 | 7 | 8 | 9
#END OF DATE PART-YEAR#

```

I believe I will make a rule called <dec_d> which will include the digits 0-9 because I noticed I used that same rule a few times.

---

### Post by TreeFinger on 2008-01-23
Sorry, for such a boring topic. Anyways, I finished both 'date' and 'time' in BNF metalanguage. Well, I think it is done.. and correct. Please look over and see if there are any problems!  I double checked and I haven't caught anything...

```

1. Date in BNF metalanguage
a. Alphabet = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, /}
b. Terminals: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, /
c. Production Rules:

<date> ::= <day-part>"/"<month-part>"/"<year-part>
#START OF DATE PART-DAY#
<day-part> ::= <day-lessthan-ten> | <day-greaterthan-nine> | <day-greaterthan-twentynine>

<day-lessthan-ten> ::= 0 <day-lessthan-ten-seconddigit>
<day-lessthan-ten-seconddigit> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<day-greaterthan-nine> ::= <day-greaterthan-nine-firstdigit><day-greaterthan-nine-seconddigit>
<day-greaterthan-nine-firstdigit> ::= 1 | 2 
<day-greaterthan-nine-seconddigit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<day-greaterthan-twentynine> ::= <day-greaterthan-twentynine-firstdigit> <day-greaterthan-twentynine-seconddigit>
<day-greaterthan-twentynine-firstdigit> ::= 3
<day-greaterthan-twentynine-seconddigit> ::= 0 | 1
#END OF DATE PART-DAY#

#START OF DATE MONTH-PART#
<month-part> ::= <month-jan-sept> | <month-oct-dec>

<month-jan-sept> ::= 0 <month-jan-sept-seconddigit>
<month-jan-sept-seconddigit> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<month-oct-dec> ::= 1 <month-oct-dec-seconddigit>
<month-oct-dec-seconddigit> ::= 0 | 1 | 2
#END OF DATE PART-MONTH#

#START OF DATE PART-YEAR#
<year-part> ::= <year-firstdigit><year-seconddigit>
<year-firstdigit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
<year-seconddigit> ::= 0 | 2 | 3 | 3 | 4 | 5 | 6 | 7 | 8 | 9
#END OF DATE PART-YEAR#



2. Clock in BNF metalanguage
a. Alphabet = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, :, A, P, M}
b. Terminals: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, :, A, P, M
c. Production Rules:

<time> ::= <hour-part>":"<min-part>":"<sec-part><night_day>"M"
#START OF TIME PART-HOUR#
<hour-part> ::= <hour-lessten> | <hour-greaternine>

<hour-lessten> ::= 0 <hour-lessten-digits>
<hour-lessten-digits> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9

<hour-greaternine> ::= 1 <hour-greaternine-seconddigit>
<hour-greaternine-seconddigit> ::= 0 | 1 | 2
#END OF TIME PART-HOUR#

#START OF TIME PART-MINUTE#
<min-part> ::= <min-part-firstdigit> <min-part-seconddigit>
<min-part-firstdigit> ::= 0 | 1 | 2 | 3 | 4 | 5 
<min-part-seconddigit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
#END OF TIME PART-MINUTE#

#START OF TIME PART-SECOND#
<sec-part> ::= <sec-firstdigit> <sec-seconddigit>
<sec-firstdigit> ::= 0 | 1 | 2 | 3 | 4 | 5
<sec-seconddigit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
#END OF TIME PART-SECOND#

#START OF TIME PART-NIGHT_DAY#
<night_day> ::= <night> | <day>
<night> ::= "P"
<day> ::= "A"
#END OF TIME PART-NIGHT_DAY#

```

---

