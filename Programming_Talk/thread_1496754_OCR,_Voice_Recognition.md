---
title: "OCR, Voice Recognition"
date: 2010-05-29
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-05-29
Hello forum,

i am definitely a newbie in the world of programming (i even need the spell-check to tell me it takes double 'm' :) )
Yet one of the things that i find intriguing is how programs like OCRs or Voice Recognition function.
For instance take an OCR, i suppose some archetype of the letter "a" etc. must be stored somewhere first. But how do we point at the program:
[LIST=1]
[*]to find at all a letter on the scanned document,
[*]to make it compare to the archetype,
[*]to allow it to recognise the current letter as (approximately) similar to the archetype?[/LIST]

This is simply amazing to me. I guess one cannot give great details in forum post, but i'd like to get the basics of it. At what level or in which form is the data manipulated? What kinds of processes are used? etc.

I'd appreciate if some could enlighten me on that point.

Thanks. :)

---

### Post by Tony Flury on 2010-05-29
For instance - one possible OCR process would be : 

1) Load the image of the page
2) remove noise - maybe non black pixels - single pixels on its own etc.
3) identify the gaps between the words
4) identify the letters
5) find the base line ...
6) identify the shape of each letter - in terms of lines and relative distances etc.
7) Compare the shapes with the model your program holds.

---

### Post by jesuisbenjamin on 2010-05-29
Hi Tony,
Thanks for your reply. You said:

> 6) identify the shape of each letter - in terms of lines and relative distances etc.

I understand how to ask whether "8" is found in "789". But how do you describe the concept of "line" to a program? or how can we tell a program what is the "noise" to be removed and what a "letter" is?

That's more where i get lost, i stick with human concepts and can't see it from the point of view of programming...

Thanks.
B.

---

### Post by slavik on 2010-05-29
software can do raster to vector ... not as easy as vector to raster, but doable.

Not only that, but you can take a vector of a stored letter and match against the rasterized imaged and see how closely the vector would match the letter. highest consistency wins.

---

### Post by Alcareru on 2010-05-30
Another thing OCR software may take into consideration is dictionaries. "Do a spell check" on it's output and then maybe revise it's guesses of letters. At least [tesseract]("http://code.google.com/p/tesseract-ocr/") does this on some level. I'm not familiar with the details of implementation.

---

### Post by NovaAesa on 2010-05-30
Artificial Neural Networks are also used for OCR.

---

### Post by jesuisbenjamin on 2010-05-31
> **Alcareru said:**
> Another thing OCR software may take into consideration is dictionaries. "Do a spell check" on it's output and then maybe revise it's guesses of letters. At least [tesseract]("http://code.google.com/p/tesseract-ocr/") does this on some level. I'm not familiar with the details of implementation.

Oh yeah, this is cool. Actually it's what we do too when we don't recognise something for sure :)

---

### Post by James78 on 2010-05-31
> **NovaAesa said:**
> Artificial Neural Networks are also used for OCR.And you can see a Javascript example of a neural net [here]("http://userscripts.org/scripts/review/56989"). It's a Javascript that autofills a captcha, if it gets it wrong the first time, it usually gets it right the second time.

---

### Post by jesuisbenjamin on 2010-06-01
Thanks for that James,

I took a look and well as i said i am a newbie in programming, besides my background is languages and history. So i can't even understand the information on ANN on wikipedia. Nevertheless, from the figures i guessed the idea is that an input is processed through several methods with the idea purpose of calculating the output with the highest probability or something like that. Is that right? Is there some information for people that aren't used to mathematical formulas and references to obscure theories?
That would be cool. I have always been attracted to the idea of a program that can converse. I'd like to try to make work on a program that understands grammar once (when i'll have more experience of course), the process also helps understanding grammar better i imagine.

Thanks.

---

### Post by James78 on 2010-06-01
> **jesuisbenjamin said:**
> Nevertheless, from the figures i guessed the idea is that an input is processed through several methods with the idea purpose of calculating the output with the highest probability or something like that. Is that right?That is indeed the basic way of how it works. :)

---

### Post by Some Penguin on 2010-06-01
> **jesuisbenjamin said:**
> Thanks for that James,

I took a look and well as i said i am a newbie in programming, besides my background is languages and history. So i can't even understand the information on ANN on wikipedia. Nevertheless, from the figures i guessed the idea is that an input is processed through several methods with the idea purpose of calculating the output with the highest probability or something like that. Is that right? Is there some information for people that aren't used to mathematical formulas and references to obscure theories?

ANNs *are* mathematical formulas, so you're going to need to understand basic math to understand ANNs.  They're just very simple functions, with marginally less simple training updates (frequently, gradient descent).  The skill is in determining network structure -- in particular, what inputs to use and how to code them.

---

