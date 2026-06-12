---
title: "Tutorial: Writing conventions."
date: 2008-05-21
forum: Programming Talk
---

### Post by Can+~ on 2008-05-21
[SIZE="5"]Writing conventions for most languages[/SIZE]

[SIZE="4"]Index[/SIZE]
[LIST=1]
[*]**Index**
[*]**Introduction**
[*]**General Naming**

[*][LIST=1]
[*]CamelCase
[*]Class names
[*]Function names
[*]CONSTANTS
[*]Variables
[*]Variable naming
[*]File naming
[*]Indentation
[*]Spacing
[*]Line distribution
[*]Comments
[*]Comment standardization
[/LIST]

[*]**Other resources**
[*]**Changes**
[*]**Conclusion**
[/LIST]

[SIZE="4"]Introduction[/SIZE]

Trying to read foreign code, specially from students or starters is somehow painful if you're looking for support in doing a certain task. Some languages have their own writing conventions, for example, python has the [PEP 08]("http://www.python.org/dev/peps/pep-0008/") about conventions.

The idea, is at least set a common ground for most languages, for better readability.

[SIZE="4"]General Naming[/SIZE]
[LIST=1]

[*]**[CamelCase](http://en.wikipedia.org/wiki/CamelCase#Programming_and_coding_style)** : Is writing words sticked together, separating each word with a capital letter. Others prefer using_underscores. Both are fine, but CamelCase, apparently, is the most popular in this forum.

[*]**MyClassSomething** : Classes should be capitalized, every word inside also capitalized, just like CamelCase.

[*]**myFunction** : Functions start with lowercase, words inside with capitals. Alternatively, you could differentiate classes from functions with underscores ("_"). Again, this is up to you. (Wybrial)

[*]**CONSTANTS** : Having constants on uppercase is pretty common on C where #define statements exisst, other languages doesn't use this as much, but if your language has a way of making a constant, using UPPERCASE help identify them.

[*]**variables** : Ideally, variables should be plain lowercase, and be referred as *(but not limited to)* one word, that indicates what they do. You can also use underscores here. Here's a bad example:

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP]def myFunc(a, b):
	a[b] += (b*a)
	return b[/PHP]

This function does not specify what a or b are, not even the name of the function can give us a clue about it. This specially painful on dynamically typed languages, statically typed can be a bit better, but not that much, it's better to use something like:

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP]def calculateSpeed(distance, time):
	return distance/time[/PHP]

This should be used on every language.

[*]**Variable naming** : Talking about variables, most of them have different purposes, there are important variables, one-time use variables, etc. The level of detail of a variable should be proportional to it's relevance in the code. An example of an iterator on C:

[**[COLOR="#00ccff"]C/C++[/COLOR]**]
[PHP]int serialSum(int *series, int length)
{
	int i, sum=0;
	
	for (i=0; i<length; i++)
	{
		sum += series[i];
	}

	return sum;
}[/PHP]

"i" Will be used inside it just once on the local scope of the function. Everyone who knows C, usually uses the "i" for the iterations, as it is used to access the index of an array, and no one likes to type [FONT="Courier New"]series[mycooliterator][/FONT] ((pmasiar) suggests using double-letter for short iterators, using "ii" "ij", so you can search them later and replace them with a more descriptive name). 

On other languages, iterators have a different meaning, read the following example to grasp the idea.

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP]for cookie in cookies:
	eat(cookie)

for cookie in cookie_jar:
	eat(cookie)

for line in fileHandler:
	print line.strip()[/PHP]

In this cases, is better to give the iterator a name corresponding to the type of object we will be using. Iterating over a file on python returns each line, therefore, the name line.

(pmasiar) Try to keep plural words for collections, and singular words for each element on that collection, or use compound names that imply a collection, like the cookie jar. Also, consistency on function calls is a great practice, the following example is a Bad example:

[**[COLOR="#00ccff"]C/C++[/COLOR]**]:
[PHP]int serialSum(int *series, int length)
{
	... (defined before)
}
...
int main(int argc, char **argv)
{
	...
	x = serialSum(progression, L);
	...
	return 0;
}[/PHP]

Our minds have a hard time with this, specially when the distance between this two C functions is big. We will travel with the idea "progression, L" looking for the function serialSum, to find other names in the arguments, ideally, keeping a consistent name across the functions is a great idea, specially if functions operate always on the same type of arguments.


[*]**File naming** : Naming your files is something rarely seen as crucial. But there's a general rule that's not only important for readability and usability; create **ALL FILLES WITH LOWERCASE**. Why? Windows doesn't recognize uppercase from lowercase, so using "SomEthIng" is equal to "something" as it is to "SOMETHING", and linux does care about this. So if you're either on windows or linux, use lowercase, even if you know your code won't go outside of your computer, your code will be safer at a long term.

And for compatibility, try to also keep the ".extension" for windows, even if the user won't ever see the actual file, keep the extension. Linux doesn't care about file extensions, only file headers, but use the extension anyway, it will make it clearer for non-linux programmers and users.

Other than that, files can be named as you please, always being descriptive. Rather than "data.bin" "database.txt" "file", use names like "user_account_metadata", "db_user_profile", "sample_content.txt", etc...

[*]**Indentation** : Tabs or spaces, any of them, use them to express the start of something, and the end of another thing. This applies for almost every language that uses more than one line (MUMPS being one the one-liners, ugh). Compare this two:

[**[COLOR="#cc0000"]pseudocode[/COLOR]**]
[PHP]
start_something
start_another_thing
	doSomething
	end_another_thing
	
	start_yet_another_thing
		...
		end_yet_another_thing
end_something[/PHP]

Where do functions start, or end? Which one is which? Here is a far better example:

[**[COLOR="#cc0000"]pseudocode[/COLOR]**]
[PHP]
start_something
	start_another_thing
		doSomething
	end_another_thing
	
	start_yet_another_thing
		...
	end_yet_another_thing
end_something[/PHP]

Python is the obvious exception, where indentation is part of the syntax of the language and not just a readability decision. In this cases, filling tabulation with spaces is preferred, because spaces are always the same size, whilst tabulations vary. (Tony Flury)

[*]**Spacing** : Spacing is something that give some relief to our eyes, makes code clearer sometimes, others it screws it up. Generally speaking, the most wide convention on spaces, is using a single space after a comma.

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP]toomuch = [ 1 , 2 , 3 , 4 , 5 , 6 , 7 ]
fine = [1, 2, 3, 4, 5, 6, 7]
ugh = [1,2,3,4,5,6,7][/PHP]

This probably should be used with the spaces between semicolons inside for's in C, or any other "separative" (?) character. There's various mixes you can do with spacing between operators, examples:

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP]1) if (a < b) and ((c > d) or (d > e))
2) if a<b and (c>d or d>e)
3) if a < b and ( c > d or d > e )[/PHP]

In this example, 1 is better than 2 and 3. Adding spaces between operators and variables, may be hard to read, distinguishing the < > operators from the logical (and, or) ones. On the other hand, sticking them closer solves that issue, but makes it less readable. Using spaces with parenthesis add priority to the < > operators, both for the compiler and for the reader, plus having the extra spacing looking fine.

This last example may be subjective (specially because the PHP tags paint the code in color), depends on the context, and it's up to you to decide, personally, I would choose between 1 and 2. There are other cases, for example:

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP](1)def myFunction(z, x="hello", y="world"):
(2)	print x, y
(3)	z = 2
[/PHP]

When assigning variables on a line (3), there's a lot of space to spare, but inside the argument definition you may need to save some space, and having the variable=value tight looks clearer when having multiple assignments separated by commas (similar to what happened before). As you leave spaces for the commas, for the mental idea of "an argument", and no other space that can confuse the reader.

[*]**Line distribution** : Leaving some empty lines between your code, will make it look way, way clearer, specially if you're following a convention invented by yourself, for example, I leave a space between variable definitions and other statements/loops, and other spaces for return blocks when using C, and most languages as well:

[**[COLOR="#00ccff"]C/C++[/COLOR]**]
```
void aFunction()
{
	int aninteger;          /*
	char achar;             * Variables definition.
	mytype *sometype;       * (This comments are not part of the example)*/
	
	if (condition)       /* Statements/loops... working code mostly. */
	{
		int insideInt;            /* Inside variable definition */ 

		while (other condition)   /* 
		{                          * Another statement/loop block 
			do stuff;          * */ 
		}                 
	}

	return aThing.
}
```

This types of conventions are mostly of your own, it doesn't matter how do you like it, the only thing that matters is that you stick to one convention of your own, throughout all your code.

Don't fear to split code for the sake of readability, but if you're gonna do it, do it well:

[**[COLOR="#00ccff"]C/C++[/COLOR]**]
[PHP]
void someFunction(unsigned const int something, unsigned const another
                  signed int x, unsigned char z)
{
	...
}[/PHP]

This way, the arguments look just like a block, mentally, everything after that parenthesis is the argument, so having it on two lines without that spacing, may be rather difficult to read.

[*]**Comments** : Comments can be placed anywhere, multi-lined comments, one line comments. Depends mostly on the context. My personal take on placing comments, is creating a little description of what the function does, what does it expect, and what it returns. Differs from language, python has it's own __doc__ string. On other languages (Quikee) suggests using the JavaDoc syntax:

[**[COLOR="#00ccff"]C/C++[/COLOR]**]
[PHP]
/**
* Here is the place where to describe the class MyClass. 
* The description should not discuss how the class is implemented
* (unless there is anything special about it) but should describe the
* class as a "black box" - generally how the programmer should use 
* it for, its responsibilities, behavior,...
* 
* If possible the description can also include some examples of the
* class usage and also any links to information related to this class. 
* 
* Remember that anything written in the comment should add additional 
* value to the class being described. Do not write obvious things
* like "This is a class named MyClass".
*
*/
class MyClass {

  /**
  * Here is the place to describe how the programmer should use the
  * function/method named myFunctionOrMethod().
  * 
  * Additionally the description should include the description of
  * input parameters, return value and any possible exceptions that can
  * occur.
  * 
  * Do not describe obvious functions / methods like getters and setters
  * unless it brings additional value.
  *
  * @param value - this is a description of the input parameter value.
  *   If the name itself is a good description then the description 
  *   is not needed.
  *
  * @return - this is the description of the return value.
  *
  * @throws MyException - here belongs a description of the situation 
  *   when the exception is thrown. Because this is not always visible
  *   in the method signature, it is more important to mention it here.
  *
  * @see MyClass (guidelines for the class also apply here)
  */
  int myFunctionOrMethod(int value) {
    ...
    /* In the function / method implementation it sometimes is good
       to comment how or why something is implemented in such a way. 
       Avoid comments like: 

         int i; // this is a counter used in the following for statement

         for (...)  { // this is a for statement
         }

         i++; // O my god, I am incrementing i by one
    */
    ...
  }

}[/PHP]
One lined comments are better suited for explaining what are you doing. Now, there's a typical error from newbies here. Most of them do a single comment like:

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP]#Here I assign a the value 2.
a = 2[/PHP]

NO S**T SHERLOCK! I couldn't have figured that out by myself. Here's a better one:

[**[COLOR="#00ee22"]python[/COLOR]**]:
[PHP]#Conversion from degrees to radians.
anglerad = math.pi*angle/180[/PHP]

It's still a bit simple, but it's way better. If someone is looking where does the conversion occurs, and he searches for the string on your code, then this will probably show up.

The most crucial thing about comments, is that it should read as a consistent documentation, either if you use inline comments (being the ones placed on the same line as a block of code) or comments on separate lines. Here's a good example:

[**[COLOR="#00ee22"]python[/COLOR]**]
[PHP]
#Open the file containing the data in the form "a|b|c|d \n e|f|g|h...".
f = open("tabular_data.txt", "r")

#Loop over the lines
for line in f:
	#and separate each line in an array, extract the last one with [-1].
	last = line.split("|")[-1]

	if last == "x":
		#If the last letter is x, display to user, and set the flag that will be used in...
		print "Found an x-terminated line"
		found = true

f.close()[/PHP]

If we paste every comment.

> Open the file containing the data in the form "a|b|c|d \n e|f|g|h...". Loop over the lines and separate each line in an array, extract the last one with [-1].If the last letter is x, display to user, and set the flag that will be used in...

Sounds almost Algorithmic.

[*]**Comment standardization** : (Suggested by pmasiar) As a way to make a more coherent programming, try writing always constant structures across all your comments. For example:

[**[COLOR="#00ccff"]C/C++[/COLOR]**]
[PHP]// TODO: <task> : <description>
// FIXME: <task> : <description>[/PHP]

Some IDEs provide this functionality and makes them automatic with other fancy features.

And try including ending comments to make clearer when functions start and end (used in conjunction with the indentation rule), this is not really that necessary for short snippets, but when working with long sections, it might be helpful.

[**[COLOR="#00ccff"]C/C++[/COLOR]**]
[PHP]  if (x>0){
     ...
  } // if (x>0)
  private ArrayList getGenes(...){
     ...
  } // getGenes()[/PHP]

[SIZE="4"]More reading..[/SIZE]

[LIST]
[*][Wikipedia: Programming Style]("http://en.wikipedia.org/wiki/Programming_style")
[*][Wikipedia: CamelCase]("http://en.wikipedia.org/wiki/CamelCase")
[*][Writing conventions for python ( PEP08 )]("http://www.python.org/dev/peps/pep-0008/")
[*](If anyone has a link to an specific language convention, post it)
[/LIST]

[/LIST]

[SIZE="4"]Changes[/SIZE]

Sorted from newest to oldest
[LIST]
[*]Added colors for languages syntax [**[COLOR="#00ee22"]python[/COLOR]**] [**[COLOR="#00ccff"]C/C++[/COLOR]**] [**[COLOR="#cc0000"]pseudocode[/COLOR]**]
[*]Added consistency with comments.
[*]Added CONSTANTS
[*]Added File Naming
[*]Added "more reading" links.
[*]Index created.
[*]Post corrected, according to suggestions.
[*]Post created.
[/LIST]




[SIZE="4"]Conclusion[/SIZE]

You're free to write as you want. The most important thing, is that you avoid cryptic names like "xRsazwA3" for elements inside your code. And at least, if you're willing to do it your own way, be consistent, do the same thing on all your code, if you like doing a double space after a comma, do it, but keep it throughout all your code, so we can read it, get used to it, and keep on.

This guide is incomplete, there's error in this guide, some persons will disagree and say "But I use Something_something_Something for classes!", it's ok, this is not intended for everyone, and you may not like it, no one is forcing you to do it.

[/LIST]

---

### Post by nvteighen on 2008-05-21
Great guide!

What about post-line comments like in this silly C code?
[PHP]
int squareArea(int Side)
{
 int Area = Side * Side; /*Avoid linking to math library for simple math*/

 return Area;
}
[/PHP]

I'd really recommend not to use that and place comments before or after the commented code (I like it before):
[PHP]
int squareArea(int Side)
{
 /*Avoid linking to math library for simple math*/
 int Area = Side * Side;

 return Area;
}
[/PHP]

Thoughts?

---

### Post by sonofusion82 on 2008-05-21
There are all good coding conventions.
However, there are already many similar coding standards out there.
I follow different coding standards depending on what project and what framework I am using. For example, if I am using C++ and KDE, I will generally follow KDE style naming conventions and if I am using Java, I'll follow Java's convention.

---

### Post by lisati on 2008-05-21
> **nvteighen said:**
> Great guide!

What about post-line comments like in this silly C code?
[PHP]
int squareArea(int Side)
{
 int Area = Side * Side; /*Avoid linking to math library for simple math*/

 return Area;
}
[/PHP]

I'd really recommend not to use that and place comments before or after the commented code (I like it before):
[PHP]
int squareArea(int Side)
{
 /*Avoid linking to math library for simple math*/
 int Area = Side * Side;

 return Area;
}
[/PHP]

Thoughts?

Maybe a comment on its own line at the start of a block of code, supplemented by comments at the end of lines *only if needed for clarification*.

---

### Post by achelis on 2008-05-21
I thought camelCase started with a lower-case letter? And PascalCase is the one where all words start with a capital letter?

I'd recommend using the standard depending on project and language, as has been mentioned before.

---

### Post by pmasiar on 2008-05-21
Good suggestions (including following the project norm). More small bits advice:
- I never use single-letter variable name. For loops, I prefer meaningful variable name, or ii, jj, kk. Easier to search/replace later
- Last letter in name is never letter 'o' or 'l'. Last letter 's' is for collections, which defines loop variable: "for user in users".
- Code is in chunks, separated by empty lines, chunk has full-line comments.
- closing brace } has endline comment - copy of the code before opening brace, like:
[php]
  if (x>0){
     ...
  } // if (x>0)
  private ArrayList getGenes(...){
     ...
  } // getGenes()
[/php]
Yout IDE might have templates which will add these for you.
- Standardize also codetags like //FIXME;  //TODO etc so you can find them later

Re CamelCase: Classes are CamelCase, variables  (instances) are camelCase.

---

### Post by LaRoza on 2008-05-21
Good post. Perhaps a wikipedia link to: [http://en.wikipedia.org/wiki/Programming_style](http://en.wikipedia.org/wiki/Programming_style) also.

Added to sticky and anyone with sloppy code infracted.

---

### Post by Wybiral on 2008-05-21
> **pmasiar said:**
> Re CamelCase: Classes are CamelCase, variables  (instances) are camelCase.

In Python, Guido suggest (and all throughout the standard library) that functions and variables be lower_case_underscore, instead of camelCase, while classes are CamelCase. I agree with him, it's much easier to separate them visually like this.

---

### Post by Quikee on 2008-05-21
> **Can+~ said:**
> [PHP]
/* Function MyFunction
* Arguments: integer that is the _______
*            float that is used for ______ inside the main iteration.
*            *char, a pointer to the ______, it changes outside the function!
*
* Returns: A pointer to the allocated memory that does _______.
* 
* TODO: Throws some erratic data when entering inputs of _____ .
* */

node *myFunction(...)
{
	... malloc ...
}[/PHP]

I don't thing this is the best example of how to describe classes and functions/methods. I have created what I believe is a better example how to describe them. It uses the JavaDoc syntax, as JavaDoc is used in many
other languages as well, but generally the syntax itself doesn't really matter (it is however to use a standard one for which the documentation can be compiled).

[PHP]
/**
* Here is the place where to describe the class MyClass. 
* The description should not discuss how the class is implemented
* (unless there is anything special about it) but should describe the
* class as a "black box" - generally how the programmer should use 
* it for, its responsibilities, behavior,...
* 
* If possible the description can also include some examples of the
* class usage and also any links to information related to this class. 
* 
* Remember that anything written in the comment should add additional 
* value to the class being described. Do not write obvious things
* like "This is a class named MyClass".
*
*/
class MyClass {

  /**
  * Here is the place to describe how the programmer should use the
  * function/method named myFunctionOrMethod().
  * 
  * Additionally the description should include the description of
  * input parameters, return value and any possible exceptions that can
  * occur.
  * 
  * Do not describe obvious functions / methods like getters and setters
  * unless it brings additional value.
  *
  * @param value - this is a description of the input parameter value.
  *   If the name itself is a good description then the description 
  *   is not needed.
  *
  * @return - this is the description of the return value.
  *
  * @throws MyException - here belongs a description of the situation 
  *   when the exception is thrown. Because this is not always visible
  *   in the method signature, it is more important to mention it here.
  *
  * @see MyClass (guidelines for the class also apply here)
  */
  int myFunctionOrMethod(int value) {
    ...
    /* In the function / method implementation it sometimes is good
       to comment how or why something is implemented in such a way. 
       Avoid comments like: 

         int i; // this is a counter used in the following for statement

         for (...)  { // this is a for statement
         }

         i++; // O my god, I am incrementing i by one
    */
    ...
  }

}[/PHP]

---

### Post by Can+~ on 2008-05-21
I added almost everything you (as a whole) suggested. Plus an index and some links.

If anyone has some links to a language certain programming convention, post it. :KS

---

### Post by vek on 2010-04-18
Just chiming in here on function comments... probably with an unpopular suggestion...

From working in large projects that have many users, I must say that the whole comment-before-function thing seems to be a recipe for disaster just due to making it easier to mess up.

I highly recommend including the comment inside the function, just after the opening brace, instead of before the function declaration.  I know this isn't as popular and might look a little less neat, but it means that when someone copies the function, they copy the comment too.  Especially when refactoring or moving code around.  At least when its part of the function, it goes along for the ride.

Too often I find comments floating in the middle of nowhere because someone copied the function it belonged to, but not the comment just above it, when they were moving, copying, refactoring...

---

### Post by Tony Flury on 2010-04-19
Just a small comment - under indentation i would have expected to have seen some mention of how identation is a matter of style for most languages, but how for Python it is part of the syntax, and the need to adopted a consistent indentation style will save a lot of grief. Most people go with 4 space tabs i think - and more importantly, don't use Tab characters at all - they set their editors up to insert spaces when Tab is pressed.

---

### Post by Can+~ on 2010-04-19
> **vek said:**
> Just chiming in here on function comments... probably with an unpopular suggestion...

From working in large projects that have many users, I must say that the whole comment-before-function thing seems to be a recipe for disaster just due to making it easier to mess up.

I highly recommend including the comment inside the function, just after the opening brace, instead of before the function declaration.  I know this isn't as popular and might look a little less neat, but it means that when someone copies the function, they copy the comment too.  Especially when refactoring or moving code around.  At least when its part of the function, it goes along for the ride.

Too often I find comments floating in the middle of nowhere because someone copied the function it belonged to, but not the comment just above it, when they were moving, copying, refactoring...

I'm not sure what do you consider copy and pasting inside code; but if you find yourself replicating code frequently, you might be running into the copy and paste antipattern:

[http://en.wikipedia.org/wiki/Copy_and_paste_programming](http://en.wikipedia.org/wiki/Copy_and_paste_programming)

---

### Post by azagaros on 2010-04-19
Naming conventions and other coding ideas... 

m_bError is what I have used for representing a member boolean variable for years, since I worked at IBM in the mid 90's.  It is frustrating looking at new code styles and sorting out the scope level of a variable, especially now when the layer of namespace is present.  Like you see a variable like stringMyString some where in code, is it global, local or namespaced?  Scope of variables play important rolls in certain forms of programming.  I don't use globals in most of my code and I am trying to sort out the use of elaborate class of namespacess, which most older forms of c++ didn't have.

nValue for a numeric value of some form at a local scope level.

strValue for strings...

Some of these taught at the schools I went to in the early 90's..

Comments fit where you are and think about them...  Pre-code or post code.  How detailed were subject of the programmer working the code..  I am not working Asm, which it was preferred to see comments on every line.

Suggesting how people code is a bad idea, as long as you see consistency across a program is all that matters.  But promoting good programming practices is good.

---

