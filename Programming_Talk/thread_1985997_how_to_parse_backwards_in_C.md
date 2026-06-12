---
title: "how to parse backwards in C"
date: 2012-05-24
forum: Programming Talk
---

### Post by anewguy on 2012-05-24
I have a C program using GTK that uses gtk_font_button_new.  That returns a string containing the font name followed by 1 or more possible "attribute" like bold or italic and finally the font size.  An example might be:

Andale Mono 22

where "Andale Mono" is the font name and 22 is the font size

== or ==

Andale Mono Bold 22

== or ==

Andale Mono Bold Italic 22

Obviously, some font names are longer than 2 words as well.

I tried to write a function to look backwards in a string until either the beginning of the string or a space, then copy that portion of the string (without the space).  I thought I could pull out the length that way.  I thought I could use either the same routine to search for trailing "attribute" and pull them out 1 at a time as well, then just copy the rest of the string which would be the font name.

I could not figure out how to do this and make it work.  It would compile clean, I could find the string length, set up the "from" and the "to" for a strncpy, but it always aborted with a segment fault at runtime.

I have since removed all that from my code so I could just start from scratch on that part.

So:

- does anyone know a SIMPLE way (someone a few months ago before I stopped working on this for a while suggested a pango routine, but I don't understand pango at all) to parse out the font name, any attributes and finally the size from such strings?

- does anyone know of a way in GTK to display just the font families?  I really want to just have the font selection be something like:

Arial
Andale Mono
etc.

and let me program separately for inputting the size and attributes?


Thanks in advance!

Dave ;)

---

### Post by roelforg on 2012-05-24
Remember that you have to allocate length_of_result_string+1 to the target buffer.
(the +1 is to take in account the \0 strncopy appends)

---

### Post by ofnuts on 2012-05-24
> **anewguy said:**
> I have a C program using GTK that uses gtk_font_button_new.  That returns a string containing the font name followed by 1 or more possible "attribute" like bold or italic and finally the font size.  An example might be:

Andale Mono 22

where "Andale Mono" is the font name and 22 is the font size

== or ==

Andale Mono Bold 22

== or ==

Andale Mono Bold Italic 22

Obviously, some font names are longer than 2 words as well.

I tried to write a function to look backwards in a string until either the beginning of the string or a space, then copy that portion of the string (without the space).  I thought I could pull out the length that way.  I thought I could use either the same routine to search for trailing "attribute" and pull them out 1 at a time as well, then just copy the rest of the string which would be the font name.

I could not figure out how to do this and make it work.  It would compile clean, I could find the string length, set up the "from" and the "to" for a strncpy, but it always aborted with a segment fault at runtime.

I have since removed all that from my code so I could just start from scratch on that part.

So:

- does anyone know a SIMPLE way (someone a few months ago before I stopped working on this for a while suggested a pango routine, but I don't understand pango at all) to parse out the font name, any attributes and finally the size from such strings?

- does anyone know of a way in GTK to display just the font families?  I really want to just have the font selection be something like:

Arial
Andale Mono
etc.

and let me program separately for inputting the size and attributes?


Thanks in advance!

Dave ;)
- Tokenize the name in individual words
- Concatenate back the words until you hit one which indicates a font characteristic (bold/italic/condensed/semi-bold/extra-bold...(you will need a list of these))
- You can concatenate the rest until you hit a number for the font characteristics ("bold italic") 
- The last one would be the size.

---

### Post by anewguy on 2012-05-25
I *may* have found a way to get the font name list, *if* the Pango fonts are the same as the available fonts on a system without Pango installed:

[http://www.lemoda.net/pango/list-fonts/index.html]("http://www.lemoda.net/pango/list-fonts/index.html")

Do you know if this would work for just getting the font families on a normal Linux system (no Pango)?

---

### Post by anewguy on 2012-05-25
Solved!  The link I posted above contains code which I slightly modified to put the names in a gtk combo box, so all is good now!

Thanks for the input!

Dave ;)

---

