---
title: "Help with c++"
date: 2008-03-22
forum: Programming Talk
---

### Post by nickoli on 2008-03-22
Hello Everyone. I'm new to c++ programming and I'm writing a program to convert roman numerals into decimal form and doing the math that is presented within the data file. I'm having a problem parsing the string into char. I will show you the function i'm have the problem with. I'm trying to use .at within a for loop I'm not sure I'm using the correct logic. I've been stuck here for over 24 hours so any help will be appreciated. Thanks for your time.


The function

int convert_from_roman(string& word)
{	int counter, i = 0;
	char letter;
	counter = word.length();
	for(i = 0; i <= word.length(); i++)
	{
	
		switch(word.at(i))
		{
			case 'M': return(1000); break;
			case 'D': return(500); break;
			case 'C': return(100); break;
			case 'L': return(50); break;
			case 'X': return(10); break;
			case 'V': return(5); break;
			case 'I': return(1); break;
			default : return(0);
		}
	}	
}

an example of the string that is in the data file " MCCXXVI"

it will only output the first character which is " 1000"
Thanks for your time.

---

### Post by keratos on 2008-03-22
Erm, you're passing the reference (&) to the string. Try passing by VALUE and use iterator member function !

e.g.

```

int convert_from_roman(string word)
{
...
int total = 0;
string::iterator my_iter;
for(my_iter = word.begin(); my_iter != word.end(); my_iter++)
{
    switch *my_iter 
    {
    <<your switch statements that will add to the "int total" object>>
    }
}
...
return (total);
}

```

---

### Post by lloyd_b on 2008-03-22
It's all those "return..." statements within the switch.  Basically, what's happening is that it hits the proper case for the first letter, and then exits the function (because of the "return").

What you need to do is have a "total" variable, initialized to zero, and for each case add the appropriate amount:
```
switch (word.at(i)) {
     case 'M': total += 1000;
                  break;
     case 'D': total += 500;
                  break;
```
and so on.  Then, at the end of the function, return the value of "total".

BTW: There's a serious problem with your conversion routine.  An example of a valid Roman numeral is "MCMLXIV", which is "1964".  Note the "CM" and "IV" parts - when a smaller value appears to the left of a larger value, the smaller value is *subtracted* from the larger value.  Hence "CM" = 1000 (M) - 100 (C) = 900, and "IV" = 5 (V) - 1 (I) = 4.

Your logic does not take this quirk of Roman numerals into account...

Lloyd B.

---

### Post by keratos on 2008-03-22
> **lloyd_b said:**
> It's all those "return..." statements within the switch.  Basically, what's happening is that it hits the proper case for the first letter, and then exits the function (because of the "return").

What you need to do is have a "total" variable, initialized to zero, and for each case add the appropriate amount:
```
switch (word.at(i)) {
     case 'M': total += 1000;
                  break;
     case 'D': total += 500;
                  break;
```
and so on.  Then, at the end of the function, return the value of "total".

BTW: There's a serious problem with your conversion routine.  An example of a valid Roman numeral is "MCMLXIV", which is "1964".  Note the "CM" and "IV" parts - when a smaller value appears to the left of a larger value, the smaller value is *subtracted* from the larger value.  Hence "CM" = 1000 (M) - 100 (C) = 900, and "IV" = 5 (V) - 1 (I) = 4.

Your logic does not take this quirk of Roman numerals into account...

Lloyd B.

ditto for this more complete answer than my post above which purely focused on the syntax and not the overall progmatic logic.

---

### Post by nickoli on 2008-03-22
Gentleman I  can't say enough to show my appreciation for the assistance you have given me. What appears simple to you was hard for me to grasp. Hopefully the more time I spend studying c++ the more proficient I will become in programming with it. Thanks. Have a great day!:)

---

### Post by keratos on 2008-03-22
no prob.

how about closing this thread as SOLVED (see thread tools)?? :-)

---

