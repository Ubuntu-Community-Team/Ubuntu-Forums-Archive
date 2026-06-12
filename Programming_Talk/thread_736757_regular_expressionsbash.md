---
title: "regular expressions/bash"
date: 2008-03-26
forum: Programming Talk
---

### Post by linuxmaveric on 2008-03-26
Can someone help me with a regEX question :)

How could I write a regular expression using "GREP" that would allow me to search files in this order 

City,  State,  and  Zip Code.  With spaces in between "city" "ST" and "zip"

The city can be any name.  The State can be any two capital letters and the zip can be any number between [0-9]

How can I put that together in a regEX using grep to search??

If anyone can help me a thousand thanks!!
RR. :)

---

### Post by ghostdog74 on 2008-03-26
provide your sample input

---

### Post by linuxmaveric on 2008-03-27
Not sure!! It should start sort of like this in bash:

grep "regEX for city, ST, 12345zip" /usr/addressbook

I need help figuring out how to write an expression to deal with what I stated above.

I'm working on it but Its still not right. im using [0-9] to deal with the zip and [A-Z] to deal with the capital only for ST, and not sure for "city"
regEx's Yuck!!! But a necessary chaos!!

---

### Post by mssever on 2008-03-27
> **linuxmaveric said:**
> Not sure!! It should start sort of like this in bash:

grep "regEX for city, ST, 12345zip" /usr/addressbook

I need help figuring out how to write an expression to deal with what I stated above.

I'm working on it but Its still not right. im using [0-9] to deal with the zip and [A-Z] to deal with the capital only for ST, and not sure for "city"
regEx's Yuck!!! But a necessary chaos!!

Here's a Ruby regex to get you started: ```
^([^,]+)\s+([A-Z]{2})\s+([0-9]{5})
```You'll have to modify it a bit for egrep (use egrep, NOT grep). Also, this assumes the presence of a comma between the city and the state. If there's no comma, do something like 
```
^(.+)\s+([A-Z]{2})\s+([0-9]{5})
``` But this regex might be a bit fragile.

---

### Post by linuxmaveric on 2008-03-27
Your examples did the trick. I don't need commas so I used your second example. Thank you very much. I just tried it using egrep & "voila" it worked.
Cool!
RR.

---

### Post by linuxmaveric on 2008-04-02
I created a simpler and easier solution for my problem that I originally posted. Using grep & regEx to find a address consisting of City, State and zip. City could be anything, state always two capitals "ST", and a  5 digit zip. Here is my basic solution:

 grep ", [A-Z][A-Z] [-0-9][0-9][0-9][0-9][0-9]" /filename

This would do the job nicely. But thanks everyone for the suggestions. They gave me the ideas to figure this out.
RR.

---

### Post by Can+~ on 2008-04-02
> **linuxmaveric said:**
> I created a simpler and easier solution for my problem that I originally posted. Using grep & regEx to find a address consisting of City, State and zip. City could be anything, state always two capitals "ST", and a  5 digit zip. Here is my basic solution:

 grep ", [A-Z][A-Z] [-0-9][0-9][0-9][0-9][0-9]" /filename

This would do the job nicely. But thanks everyone for the suggestions. They gave me the ideas to figure this out.
RR.

It's better to use a special character for "n" repetitions rather than copy pasting. It makes it more easy to update, and more legible rather than start counting. Try to stick with the {}, *, +, .

---

### Post by mssever on 2008-04-02
> **linuxmaveric said:**
> grep ", [A-Z][A-Z] [-0-9][0-9][0-9][0-9][0-9]" /filename
Refinement: ```
egrep ', [A-Z]{2} [0-9]{5}' /filename
```Note that when you use grep for anything beyond trivial, you should use egrep, as it's regex support is better.

---

