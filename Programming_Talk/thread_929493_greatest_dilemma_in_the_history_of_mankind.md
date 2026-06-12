---
title: "greatest dilemma in the history of mankind"
date: 2008-09-25
forum: Programming Talk
---

### Post by nrs on 2008-09-25
camelCaseForMethodsNVariables or underscores_for_methods_n_variables? I've used both extensively (in different projects of course), and it's almost guranteed whichever one I pick I later regret. 

Which do you prefer?

---

### Post by LaRoza on 2008-09-25
A short descriptive name. Camel case for methods, underscores for variables.

---

### Post by lisati on 2008-09-25
Whichever works the best for readability within the project and compatibility with libraries that might be used..... we can always come back later and use the editor's "search and replace" function if there's a need to change variable names.

---

### Post by pp. on 2008-09-25
> **LaRoza said:**
> A short descriptive name. Camel case for methods, underscores for variables.

I agree, especially for method variables. Methods should not be overly long, and a method should not need that many variables.

However, if a method needs a number of 'similar' variables, then I am bound to use CamelCase and a fair amount of explanation of the variables near the beginning of the method.

---

### Post by nrs on 2008-09-25
> **lisati said:**
> Whichever works the best for readability within the project and compatibility with libraries that might be used..... Can you think of a project where it'd make sense to use one over the other? :-P Most often you're using multiple libraries with multiple conventions so adoption isn't always a straightforward issue. 

> **lisati said:**
> 
 we can always come back later and use the editor's "search and replace" function if there's a need to change variable names.
[COLOR=Red] *bursts into a cold sweat.*[/COLOR]
changing the odd variable name is one thing, changing the naming convention in a sufficiently large project...
(Actually, not that completely painful with sed)

---

### Post by ankursethi on 2008-09-25
Camel case for classes and underscores for methods and variables. This a convention in the Ruby world (and a compulsion, too, because class names HAVE to start with a capital letter). My friend had been trying to make me learn Ruby, and I picked up a few habits along the way.

---

### Post by slavik on 2008-09-25
in C and perl, I tend to do underscores, in Java, I tend to do camelcase ...

---

### Post by NovaAesa on 2008-09-25
camelCase for variables and functions, and CamelCase for classes. I don't like to have my names longer than they need to be, and an underscore it just another extra character that conveys no extra information about what is in the variable.

---

### Post by dwhitney67 on 2008-09-25
I don't know if programming standards should be considered the greatest dilemma in the history of mankind, but it sure does ruffle a few feathers when one's coding style differs from another.

Several companies that I dutifully served in the past employed software standards.  Each programmer had two choices... either follow them or hit the road.

I've attached examples of the coding standards (for C, C++, and Java) that were use at one particular (and enjoyable) company that I worked at in the past.  Due to forum limitations pertaining to the size of attachments, I had to place them in a compressed tar-ball.

Some of you may agree or disagree with the s/w standards, but that is normal.

P.S.  For the record... IMO, camel-style for method names and variable names; first character of a class-name should be in uppercase; homemade acronyms/abbreviations should not be used in class, method, or variables names unless widely understood by those on the particular project.

---

### Post by loell on 2008-09-25
I still prefer underscoring especially in dynamic languages.

---

### Post by wolterh on 2008-09-25
underscores. Always.
Why? Well, as the words are separated by a '_' it is easier to determine which is the first word, and which is the second one. In that way, you can group objects by defining a parent name, for example:
login_function();
login_msg_required = "You need to be logged in to do that."

---

### Post by jespdj on 2008-09-25
It depends on the programming language I'm programming in. I use whatever is the (de facto) standard for the language. If you use something different than what almost everybody that is programming in that particular language is using, then your code will look strange to other developers.

In Java, the norm is to use camelCaseForMethodAndVariableNames and CapitalizedNamesForClasses.

In Ruby, you_normally_use_lowecase_names_with_underscores for methods and variables, and CapitalizedNamesForClasses.

---

### Post by kavon89 on 2008-09-25
camelCase for methods and classes. 

I tend to have underscores and all lower case variables... often I strip the vowels to make it shorter, like txt and acct.

---

### Post by pp. on 2008-09-25
On second thought, it depends on the language.

In a previous post within this thread I said I usually preferred CamelCase. 

There are so-called programming languages which ignore the case in identifiers. That automatically precludes the use of CamelCase since you then could accidentially hit on a variant of a name already in use. That kind of thing would be fiendlishly difficult to debug and correct since us poor humans would find it very hard to spot this kind of conflict.

---

### Post by Nemooo on 2008-09-25
Coming from C I prefer underscores, but I generally follow the language "standard" style, so if it's Lisp im using hyphens.

---

### Post by Brain-free on 2008-09-25
Underscores for methods and variables in C.

I type fast and sometimes I forget to make a letter capital and well, the compiler responds accordingly...

---

### Post by DrMega on 2008-09-25
Coming from an old school backround, I voted camelCase.

I think underscores are better suited in constants, purely because in the olden days it was the custom to type constants in all upper case, so if they were two or more words long, it could look a bit unreadable if you didn't use underscores to break them up.

I chose camelCase as the preferred one because I think that it should be clear when scanning through the code that you are looking at a discreet item. Imagine if there is a mathematical formula and you are scanning down quickly, which of the following is more readable (in a very short time):

```

//camelCase

netPayThisMonth = (grossAnnualSalary - (incomeTax + nationalInsurance)) / 12;

```

or

```

//camelCase

net_pay_this_month = (gross_annual_salary - (income_tax + national_insurance)) / 12;

```

(incidentally, the formula is rubbish but it serves to highlight the point).

---

### Post by gomputor on 2008-09-25
CamelCase for classes and methods and underscore for the rest.
But a lot of times I just forget to do it! :)

---

### Post by jimi_hendrix on 2008-09-25
i use camelCase becuase my classes methods and variables tend to be one or two words

---

### Post by SeanHodges on 2008-09-25
Personally I really honestly don't mind. Picking the one that is standard in the core language API makes the decision easy and keeps things consistent, but just like the tabs vs. spaces debate I have better things to do than get religious about it...

One thing I would say though is STICK WITH YOURS OR OTHER PEOPLES ORIGINAL DECISIONS on these things. I really hate sifting through code that interleaves different coding standards :(


Oh, and off the record, Vim beats Emacs hands down ;)

---

### Post by Wybiral on 2008-09-25
I prefer the-lisp-way :)

---

### Post by henchman on 2008-09-25
An underscore is only a lost byte :P (or even 4 with utf32)

---

### Post by henchman on 2008-09-25
doh! Ò_ó

---

### Post by loell on 2008-09-25
> **henchman said:**
> An underscore is only a lost byte :P (or even 4 with utf32)

and the second word that has the same first letter with the first word's last letter causes **dementia** 8-[ Letter**[COLOR="Blue"]s[/COLOR]****[COLOR="Blue"]S[/COLOR]**ame. :lolflag:

---

### Post by DrMega on 2008-09-26
> **loell said:**
> and the second word that has the same first letter with the first word's last letter causes **dementia** 8-[ Letter**[COLOR="Blue"]s[/COLOR]****[COLOR="Blue"]S[/COLOR]**ame. :lolflag:

You can avoid that specific example by avoiding plurals in your names. We tend to only handle single items at a time anyone, so use the singular.

Before anyone meantions arrays, an array is just a collection of singular items and you tend to reference (either explicitly or implicitly) the items individually, so no need for plural names (usually).

---

### Post by lisati on 2008-09-26
> **DrMega said:**
> You can avoid that specific example by void plurals in your names. We tend to only handle single items at a time anyone, so use the singular.

Before anyone meantions arrays, an array is just a collection of singular items and you tend to reference (either explicitly or implicitly) the items individually, so no need for plural names (usually).

I sometimes use "List" as part of an array name e.g. NameList (or alternatively ListOfNames) - NameList[n] is sometimes more natural than Names[n]

---

### Post by fballem on 2008-09-26
> **nrs said:**
> camelCaseForMethodsNVariables or underscores_for_methods_n_variables? I've used both extensively (in different projects of course), and it's almost guranteed whichever one I pick I later regret. 

Which do you prefer?

There should be a third choice that's often used - PascalCase.

This starts with an upper-case character, which differs from camelCase, which starts with a lower-case character.

Generally, I will use PascalCase for public methods and parameters, and camelCase for non-public methods and attributes. I don't use public attributes - preferring to use getters and setters instead.

---

### Post by loell on 2008-09-26
> **DrMega said:**
> You can avoid that specific example by void plurals in your names. 

yeah the above example is rather weak. :D

---

### Post by DrMega on 2008-09-26
> **DrMega said:**
> You can avoid that specific example by void plurals in your names. We tend to only handle single items at a time anyone, so use the singular.

I've re-read what I wrote. It makes no sense. I meant "avoiding" not "void" (my typo makes the whole sentence senseless).[/QUOTE]

> **lisati said:**
> I sometimes use "List" as part of an array name e.g. NameList (or alternatively ListOfNames) - NameList[n] is sometimes more natural than Names[n]

I might go with NameList but not ListOfNames. You highlight the reason why, in that ListOfNames[n] implies that in the array at element n there is a list of names, whereas I think you meant that the array is the list and at index n there is a single name.

> **fballem said:**
> There should be a third choice that's often used - PascalCase.

This starts with an upper-case character, which differs from camelCase, which starts with a lower-case character.

Generally, I will use PascalCase for public methods and parameters, and camelCase for non-public methods and attributes. I don't use public attributes - preferring to use getters and setters instead.

I like this one too. A further variation is a notation that now seems to be becoming obsolete. You would prefix the variable name with a single lowercase letter to denote the general data type (eg nIndex, cName being a numeric index and a character string respectively). It is kind of obsolete in modern code editors with strongly typed languages as intellisense (or whatever name it goes by) gives you the info you need.

---

### Post by SeanHodges on 2008-09-26
> **fballem said:**
> There should be a third choice that's often used - PascalCase.

PascalCase is a form of CamelCase.

---

### Post by lukjad on 2008-09-26
Underscores.

---

### Post by Reiger on 2008-09-26
I use underscores for variables like size_x, but tend to use camel case for variables like downloadDir (as well as methods/functions).

---

