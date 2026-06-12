---
title: "Regex for valid First and Last name"
date: 2011-06-30
forum: Programming Talk
---

### Post by woodson2 on 2011-06-30
I have a regex I'd like to implement  and I believe it should be working and I have tested it on various  websites that have regex testers but it always says the name is invalid.

#!/bin/bash -x

echo Enter the users first and last name.
read name

Code:
```
if [[ "$name" =~ "^((?:[A-Z](?:('|(?:[a-z]{1,3}))[A-Z])?[a-z]+)|(?:[A-Z]\.))(?:([ -])((?:[A-Z](?:('|(?:[a-z]{1,3}))[A-Z])?[a-z]+)|(?:[A-Z]\.)))?$" ]]
```
then
echo name is valid.
else
echo name is invalid.
exit 1
fi


If I enter Jon Doe then is should be valid.

---

### Post by Arndt on 2011-06-30
> **woodson2 said:**
> I have a regex I'd like to implement  and I believe it should be working and I have tested it on various  websites that have regex testers but it always says the name is invalid.

#!/bin/bash -x

echo Enter the users first and last name.
read name

Code:
```
if [[ "$name" =~ "^((?:[A-Z](?:('|(?:[a-z]{1,3}))[A-Z])?[a-z]+)|(?:[A-Z]\.))(?:([ -])((?:[A-Z](?:('|(?:[a-z]{1,3}))[A-Z])?[a-z]+)|(?:[A-Z]\.)))?$" ]]
```
then
echo name is valid.
else
echo name is invalid.
exit 1
fi


If I enter Jon Doe then is should be valid.

I'm not an expert on the regexps that bash supports, and I didn't try to understand this long one, but went from the other direction:

```
#!/bin/bash -x

name="John Doe"

if [[ "$name" =~ "^John Doe" ]]
then
echo name is valid.
else
echo name is invalid.
exit 1
fi
```

Not even that works, so I suggest you put your regexp together piece by piece, from working pieces. I can't say why ^ doesn't work; it is mentioned in the regex(7) man page.

---

### Post by woodson2 on 2011-06-30
I was able to get it working by removing all the references to ?: as bash doesn't support this.

The only problem now is that it won't allow hyphenated last names like

Mary Jones-Smith

The ^ and $ symbols are regex anchors.

---

### Post by Vaphell on 2011-06-30
is there any reason why you do it in bash? Use perl or python to gain access to more powerful regexes
besides that regex looks quite hardcore, care to list name formats you'd like to detect as valid?

---

### Post by diesch on 2011-06-30
What exactly do you want the regex to match?

---

### Post by woodson2 on 2011-06-30
> **Vaphell said:**
> is there any reason why you do it in bash? Use perl or python to gain access to more powerful regexes
besides that regex looks quite hardcore, care to list name formats you'd like to detect as valid?


The rest of the script is in bash. Anyways I was able to get everything working with this:

echo Enter the users first and last name.
read name
if [[ "$name" =~ ^[A-Z][a-z]+" "[A-Z][a-z]+(-[A-Z][a-z]+)*$ ]]
then
echo name is valid.
else
echo name is invalid.
exit 1
fi

It will allow

Mike Smith
Mary  Joe-Smith
Wi Pka

Won't allow

Wi Pk
mary
Mary smith
mary smith
Mary Jones-Smith Barnes

No numbers or characters etc..

---

### Post by sanderj on 2011-06-30
What's your definition of "valid First and Last name"

Are the following names valid:

Pieter van den Hoogenband
René van der Gijp
Boris Veldhuijzen van Zanten
Floris Jan Bovelander
Gert-Jan Bakker
Melanie Henriëtte Schultz van Haegen-Maas Geesteranus

All these names are existing persons and names in the Netherlands. The last name is a minister in the current cabinet.

---

### Post by woodson2 on 2011-06-30
> **sanderj said:**
> What's your definition of "valid First and Last name"

Are the following names valid:

Pieter van den Hoogenband
René van der Gijp
Boris Veldhuijzen van Zanten
Floris Jan Bovelander
Gert-Jan Bakker
Melanie Henriëtte Schultz van Haegen-Maas Geesteranus

All these names are existing persons and names in the Netherlands. The last name is a minister in the current cabinet.


No it doesn't accept any of these names. The definition of valid names for our environment are as follows:

Mike Jones or Mary Smith-Jones

I would suspect it would be very difficult to construct a regex that would cover everything. If you have it I would gladly test it out in my environment.

---

### Post by Vaphell on 2011-06-30
what about Mary D'Arcy-Jones?

---

### Post by woodson2 on 2011-06-30
> **Vaphell said:**
> what about Mary D'Arcy-Jones?


Doesn't accept that either.  I'm open to suggestions....

---

### Post by sanderj on 2011-06-30
> **woodson2 said:**
> Doesn't accept that either.  I'm open to suggestions....

What are you trying to achieve? What are you afraid of?

Even if I fill out Steve Jones, you can't be sure it's (my) valid name ...

If your name is René, and if a website says it's not valid, that's quite annoying and maybe even offensive. So you must be able to handle non-US-ASCII characters, and maybe even Unicode.


And, isn't it the responsibility of the user to fill out the correct, valid name?

---

### Post by trent.josephsen on 2011-06-30
> **woodson2 said:**
> Doesn't accept that either.  I'm open to suggestions....

Let the user enter his or her name as a free-form string, and don't impose any silly rules on it.  Why should you care what the format of your user's name is?

If it's important to you that you know the user's "legal" first and last name, ask for them in separate fields, and let Harry René van der O'Malley-Witherspoon decide which parts are which.  You're fighting a losing battle with this guesswork.

What does your program do with "Kim Jong-Il"?

---

### Post by diesch on 2011-06-30
> **trent.josephsen said:**
>  If it's important to you that you know the user's "legal" first and last name, ask for them in separate fields, and let Harry René van der O'Malley-Witherspoon decide which parts are which.  You're fighting a losing battle with this guesswork.


If you want to do it for international names remember that in some countries the first name part is the family name, and in same they have additional official name parts, like a patronym.

---

### Post by mourt on 2011-06-30
> **woodson2 said:**
> Doesn't accept that either.  I'm open to suggestions....

One suggestion would be to just not impose restrictions on names, as there aren't any reasonably patterns.

---

### Post by nvteighen on 2011-06-30
I would understand you wrote a regexp that tried to ensure that there are no weird characters in the name... let's say numbers.

But in general, given the different conventions used for names in the world, you better ask for a single string for name and allow people to fill it like they want to. If you're concerned about identity, ask for some legal identification number, which usually have some predefined format (and validation digit).

---

### Post by trent.josephsen on 2011-06-30
> **diesch said:**
> If you want to do it for international names remember that in some countries the first name part is the family name, and in same they have additional official name parts, like a patronym.

That's why I added the Kim Jong-Il part (which is admittedly ambiguous, especially if you weren't aware that Kim is in fact his surname).  Thanks for making that clear.

---

