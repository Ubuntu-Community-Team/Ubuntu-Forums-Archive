---
title: "Possible extra data in script?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by starstreams on 2012-12-26
Just wanted to verify something. I know this is really basic to most of you. I just don't want to get too far ahead of myself
I highlighted two parts of concern in *red*. (This script was taken right from my book and it works).

Do I actually need to specify a value for firstname and lastname variable when using a read statement? I noticed that I'm able to leave the values blank and it still works. I guess what I'm asking is: why is the book telling me to put a name in (john smith) if the user interacting with the script is changing the value of the variable with a read statement by what he/she types anyway?

And notice the echo after the second [COLOR=Blue]*read lastname*[/COLOR]. Why is the book telling me to add that? I removed it and the script still worked as expected. Could these be typos in the book?
The book by the way is: *Essential Linux Administration - Chuck Easttom and Serge Palladino*

> 
[B]#!/bin/bash

lastname=[/B][COLOR=#ff0000]**smith**[/COLOR][B]
firstname=[/B][COLOR=#ff0000]**john**[/COLOR][B]
echo Please type in your first name
read firstname
echo Please type in your last name
[COLOR=Blue]read lastname[/COLOR]
[/B][COLOR=#ff0000]**echo **[/COLOR](<--why do I need this?)[B]
echo Hello $firstname $lastname it is good to meet you

exit 0[/B]


---

### Post by fdrake on 2012-12-26
> **starstreams said:**
> Just wanted to verify something. I know this is really basic to most of you. I just don't want to get too far ahead of myself
I highlighted two parts of concern in *red*. (This script was taken right from my book and it works).

Do I actually need to specify a variable for firstname and lastname when using a read statement? I noticed that I'm able to leave the variable blank and it still works. I guess what I'm asking is: why is the book telling me to put a name in (john smith) if the user interacting with the script is changing the variable by what he/she types anyway?

And notice the echo after the second [COLOR=Blue]*read lastname*[/COLOR]. Why is the book telling me to add that? I removed it and the script still worked as expected. Could these be typos in the book?
The book by the way is: *Essential Linux Administration - Chuck Easttom and Serge Palladino*

i see a lot of useless code in it. Also the echo statment should have the "" ! are you sure it' s no t an exrcise. I haven't find that many revies about the book. That's not a good sign!

i suggest you this [http://shop.oreilly.com/product/9780596005283.do](http://shop.oreilly.com/product/9780596005283.do)

---

### Post by steeldriver on 2012-12-26
The extra 'echo' just outputs a newline I think - to format the output a bit more nicely. 

The [FONT=Courier New]lastname=smith[/FONT] and [FONT=Courier New]firstname=john[/FONT] assignments just supply default values - if you wanted to be fancier you could use a construct like [FONT=Courier New]${firstname:-john}[/FONT] in the 'echo Hello ... ' line instead

```
echo Hello ${firstname:-john} ${lastname:-smith} it is good to meet you
```See [http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

EDIT: pretty much agree with fdrake though - although there's nothing actually 'wrong' with it, the style is pretty basic - there are nicer ways of prompting for user input (at least in bash 4+) e.g. something like

```

#!/bin/bash

read -p "Please type in your first name: " firstname

read -p "Please type in your last name: " lastname

echo "Hello ${firstname:-john} ${lastname:-smith} it is good to meet you"

exit 0

```

---

### Post by Hadaka on 2012-12-26
Hi, it looks like this simple script is teaching an example
of how to change a defined field or var.  In this excersize,
Lastname is defined as smith  and first name as john.
The read statement changes the $firstname and $lastname
to the new input. The blank echo is just that...a blank line for
easier reading of the script and a newline on the output.
so...yes....if you enter nothing for firstname and lastname it
will forever be john smith....hence. Its called learning about
defined variables,and how to change them.It is good that you question, but...it is not
a type O.

---

### Post by starstreams on 2012-12-26
**@fdrake:** I'll order that book right now if you say it's good.
The book I mentioned only has a small section of scripting, though I have learned a lot of different topics from it in the few chapters I've read It's sometimes vague on somethings. 

I'm not sure what you mean by [B]"" !
[/B]This was an an exercise but all the other exercise examples don't use [B]"" !
[/B]I thought you only needed to add double machine quotes between values with spaces? I'm not sure, what do you do with this --> [B]"" !

@steeldriver:[/B]
what you said about the output statement outputting a new like makes sense. Sort of like how a P tag can be used to add a new line in HTML rather then just starting a new paragraph. I'll have to read up on constructs. But why would you add something that is longer to type such as ${firstname:-john} when adding $firstname makes a call to the variable using less characters. I don't understand the construct I think.


**@Hadaka**
> Hi, it looks like this simple script is teaching an example
of how to change a defined field or var.  In this excersize,
Lastname is defined as smith  and first name as john.
The read statement changes the $firstname and $lastname
to the new input.[B]

EDIT:[/B] Ok, this makes sense now. 
Yes you are correct, the book was demonstrating how to change a defined field var using the *read statement*.
That is correct.
And what you explained makes sense now, Thanks for verifying. I just wasn't sure why they added the extra echo.
And I guess they added the names for values just to show that the read statement would override them anyway. They were using it to make a point I guess.

Thank you
Ordering the LPI Linux Certification in a Nutshell, 2nd Edition book right NOW... :p

---

### Post by fdrake on 2012-12-26
> **Hadaka said:**
> .
so...yes....if you enter nothing for firstname and lastname it
will forever be john smith....

are you sure. If you just press ente you will get an empty string> You have to escape in order not to assaign the value

---

### Post by Hadaka on 2012-12-26
@fdrake...you are correct...you get a blank field....my error ;)
thanks for pointing that out..

---

### Post by starstreams on 2012-12-26
By the way, what would happen if you left the **exit 0** out? hehe
I was afraid to try it last night .. for my computer might go running off on me in an endless loop to never return. 
On a side note, it looks as though you have to terminate the *if* statements also with fi, sometimes after the exit 0 which seems kind of odd, and un nested. Some of this stuff reminds me so much of HTML, XHTML.. CSS.. ect.

> **fdrake said:**
> .. If you just press enter you will get  an empty string> You have to escape in order not to assign the  value
For me, as long as there is a read statement with user input, I get what ever value the user (myself) enters on the keyboard. Or as you mentioned, if the user doesn't enter anything, it's just blank. Just confirming I understand. But why would you escape if leaving the value blank was intended? Unless maybe there are other complex situations like databases where a value can't be left blank possibly?

---

### Post by fdrake on 2012-12-26
> **starstreams said:**
> [B]@fdrake:

I'm not sure what you mean by [B]"" !

It's a good use to use "" when you print a message . it's like using brackets with operations .(it's a coding style that most books push you to follow) It' s easier to read and if you use a good editor it will use a different colour, so oit makes it more intuitive to.

---

### Post by fdrake on 2012-12-26
> **starstreams said:**
> By the way, what would happen if you left the **exit 0** out? hehe
I was afraid to try it last night .. for my computer might go running off on me in an endless loop to never return. 
On a side note, it looks as though you have to terminate the *if* statements also with fi, sometimes after the exit 0 which seems kind of odd, and un nested. Some of this stuff reminds me so much of HTML, XHTML.. CSS.. ect.
you can leave it out. but it is good use to get used writing it, especcially when you will have to use conditions for error megs, or warnings.

---

### Post by Hadaka on 2012-12-26
If you leave exit 0 out, you will be hauled off by the scripting
police,banned from using any form of unix and forced to use
windows for life. ;) and what fdrake said. Its a good habit to
use exit 0 with scripting to define..end of script and also to keep
out of trouble when scripting at the root level. exit 0 at root prompt
drops you back to user level in terminal.

---

### Post by starstreams on 2012-12-26
**@fdrake**
Thanks again on them last two points above fdrake!


> **Hadaka said:**
> If you leave exit 0 out, you will be hauled off by the scripting
police,banned from using any form of unix and forced to use
windows for life. ;) 
Well we can't have any of that now. Microsoft has already put 90% of the world in rooms with bars on windows. 
It's just we've happened to slip through them thank goodness. :D
> **Hadaka said:**
> 
and what fdrake said. Its a good habit to
use exit 0 with scripting to define..end of script and also to keep
out of trouble when scripting at the root level. exit 0 at root prompt
drops you back to user level in terminal.

Yep, makes perfect sense. Good habits and universal structure is imperative.  I agree Hadaka!

Thank you .. to everyone who responded.
It was very helpful and very much appreciated.  Thumbs up!

---

