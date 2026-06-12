---
title: "PHP Preg Match"
date: 2008-03-01
forum: Programming Talk
---

### Post by DanielJackins on 2008-03-01
Hi, I'm currently trying to create a registration script, and its all going well except that you can enter invalid values in all of the fields. I can't seem to find a tutorial on preg match, or anything else explaining it very well. I need usernames to be restricted to a-z, A-Z, 0-9, and underscores, and 5 characters minimum, same with passwords. I also need it so they must enter a valid email address (eg [email]goof@goof.net[/email], cause right now they can enter anything, such as just goof)

Thanks

---

### Post by jpeddicord on 2008-03-01
I've never really found a really good tutorial all in one; I've learned by examples. So I'll show you some PCREs for what you might be looking for, like a username::

```
/^\w{5,}$/
```
The /'s at the beginning and end are the boundaries of the actual expression. The ^ matches from the beginning, and the $ does from the end. If you leave these out, it might only match a part of the input.

The \w is equivalent to [a-zA-Z0-9_], and the {5,} modifies the \w to require at least 5 characters. To add a limit on characters, just add another value to the right of the comma. For example, {5,20} means it must be between 5 and 20 characters.

Emails get more complicated; there are a lot of email regexes out there and everyone seems to like a different one. A quick google search for "email regular expression" should bring up some decent results.

---

### Post by DanielJackins on 2008-03-02
Thanks, that cleared up what all that means, but what else would I put?

---

### Post by moselekm on 2009-03-16
Okay, I just started doing PREG MATCH about six hours ago and I have been pretty pumped on how awesome regex is and how dumb I have been for ignoring it for all these years.  I have googled regex and found this thread and thought I'd register and see if I could help.

I am currently reading OReilly's publishing of "Mastering REGEX 3rd edition"

So I will provide a few validation things I have made and I'll break it down for anyone.  Quote me if I am wrong or if their is an easier way.  We all know that PHP is heavily supported and provide massive examples and snippets we can use (Such as the famous EMAIL validation:
> preg_match('/^[^@\s]+@([-a-z0-9]+\.)+[a-z]{2,}$/i'

But that doesn't really break down to those of us newbs who wish to know why and how it works.  So I will make my own form validation REGEX's and tell you how they work.

Universal Notes:
[LIST]
[*]Your search regex code should be surrounded by single quotes (').
[*]Your delimeter is a lot like PERL's use, but can become kind of annoying and some what pointless with simple searches with regex/preg.
[*]After the single quote you place your delimeter, in most all examples they are a /.
[*]REGEX reads in english (well mine does), so it goes left to right.  As you type is as it reads.  THIS IS IMPORTANT!
[/LIST]

First, my email validation:
> preg_match('/^[a-z0-9]{4,}+.?([a-z0-9]+)?@([a-z0-9]+\.)+[a-z]{3,4}$/i'


This validation allows many commercial and business emails.  I did this code to match these examples:
[LIST]
[*]robert.masters@gmail.com
[*]kylesbuzz@yahoo.com
[*]kyle.musters@cvn1.navy.mil
[/LIST]

[i]To start, let me rush through and blabber out what I am doing here in the order of the code, for indepth read below.
I start with it using / as my delimiter telling regex to begin, I use the caret(^) to start at the beginning expecting Letters or Numbers only defined by the [] = character class, and for as many characters as printed within the character class of Letters and Numbers Only, and it has to be at least one character or it will return false (as the + sign says, do this as many times as long as their is at least one true value (A-Z and/or 0-9) you'd like for so long as it maintains true.  The {} adjusts the minimum number of characters needed for the search to be thus far TRUE.  {4,} = At least four, maximum being infinite.
Next, Like in math, the parenthesis combines values within itself.  This includes **\. **because as we know the \ slash tells PHP to count it as literal, and the dot is a metacharacter in REGEX that you doesn't mean period AT ALL (well, 1% of it does).  Following that is our friendly and common [] CHARACTER CLASS.  Like the other, it is AlphaNumerical only with the plus sign to tell the search to continue on reading alpha numerical characters.  We close it all off with ) parenthesis.  The question mark is like in math when you multiply the outside number with the inside values.  Here the question mark, like thus said, EFFECTS ALL OF WHAT IS INSIDE the parenthesis.  The question mark means OPTIONAL, meaning, if you find it, great, if not, then keep going as if TRUE.
Now we have our first TRUE SOLID CHARACTER, the AT SIGN @.  Before the @ sign, if everything is true and it finds this, then it will only, as the rest, expect the REGEX supplied after.
Following right after I have another set of what is seemingly identical parenthesis and character class [] brackets, but a bit opposite, with the \. period being at the end.  PLEASE NOTE how after the [] character class the plus sign follows and not after the period.  As emails like [email]mastermo@comcast...email..com[/email] do NOT exist.  By putting a plus sign after that period we are telling the search that multiple periods after one another is alright.  So we simply tell REGEX to allow multiple alphanumerical characters to follow one another, but periods are to be solid lonely objects/values.  We close the parenthesis and follow it with the slave driving PLUS SIGN +.  This tells it that is can do that set of ALPHANUMERICAL periods to be done over and over, but done AT LEAST ONCE.  If we didn't provide that plus sign, you could only do it once leaving business emails in the bane of not being able to submit you information.
Finally for the com's and info's and net's and everything else.  If you wish to add Numerical values then you would simply kick it into the [] CHARACTER CLASS with the ALPHA-code.  And I set the limit to the character class as 3-4 letters/characters.
Finally, I close it with the delimiter, /, and follow it with the command code: i, which means IGNORE CAPS.  More commands exist with PREG because PERL rocks socks.  ALL DONE!  Boy, I bet that probably barely helped, but the below should help you dissect.[/i]

In preg match we start with the opening syntax: *('*.  After that it is safe to just say you wish to begin searching at the front of the line.  If you do, make sure you note to end the search at the end of the line, just for practice.
[i]^ (caret/power-to-the) = Start of the line
$ (Dollar Sign) = End of line[/i]
By doing **('^**, I now eliminate any melicious use of the form by adding anything not stated in the search, ideally: SPACES.

Because REGEX is very literal and simple-yet-complex, do not use spaces to separate your commands, REGEX will read everything to the T.  So right after you tell REGEX to start at the line, tell what it needs to see first.  I want it to see a Letter or Number first. (Emails can JUST BE NUMBERS, I have tested this on my domain emails, fun stuff).  So we use CHARACTER CLASS.  Character Class is basically a single character to search for placed into [] brackets.

So [a-z0-9] actually means find a single digit that is a through z or zero through nine.  The dash - and caret ^ are the only characters that are not always LITERAL.  By beginning your character class with a care ^, you are saying all characters in that character class are everything YOU'RE NOT looking for/avoiding.  So putting [^a-z] will mean your search will find a character that is numeric or symbol. (including spaces).  And the - if used anywhere between characters will generate a metacharacter use and not be literal.  So if used in between characters in the class incorrectly will give you an error.  So [-a-z] means find a character that is a dash or ALPHA.  See, REGEX is smart enough to know that the dash has nothing to relate to before itself, so it counts itself as literal.
SO:
[a-z^-] would mean search for alpha or a caret ^ or a dash -.

If you haven't noticed, character classes mean JUST ONE CHARACTER.  Often you will follow your [] with a + or *.  + and * are repeaters/repetition metacharacters.  Both being different with how they act on the first return value they find or attempt to find.
Think of it like this
+ REQUIRES a value stated and may have more following.
* IS ALWAYS TRUE, and simply means repeat the value preceding me, if there is no value to match, then it won't matter, the code/REGEX will continue as TRUE.
So [a-z]* instead of the code [a-z]+ would be bad for email because a person can type in an email like:
@yahoo.com
Because [a-z]* looked for the alpha code, but found the next step in the code being the @ sign and because * can fail to find it's character(s) over and over, but still continue the code.  So the + sign requires a return at least once.

---

