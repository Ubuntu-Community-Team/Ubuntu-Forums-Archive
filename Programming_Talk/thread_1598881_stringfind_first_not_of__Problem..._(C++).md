---
title: "string::find_first_not_of  Problem... (C++)"
date: 2010-10-17
forum: Programming Talk
---

### Post by PirateMcplunder on 2010-10-17
I am working on a program that involves a lot of string manipulation and after many hours of beating my head against the wall I cannot seem to figure out what is wrong with my use of the string::find_first_not_of function.

I have string::find working fine throughout the program but I cannot seem to get string::find_first_not_of to work properly.

I am attempting to identify whether or not the string before_token contains only digits and/or spaces/tabs.  The input I am using does indeed only contain digits and a tab but I still end up seeing my error message every time.

The input line looks like this:
2 #number of hops
(the space between 2 and # is a tab)

Here is a snippit of the code that is not working. I can provide the rest if there isn't anything visibly wrong with this.

```
size_t found;
string first_input_line;
string before_token;

		**/* WORKS */**[COLOR="Green"]
[INDENT]/* check first line for reference to the number of hops. */		
found=first_input_line.find("number of hops");[/INDENT]
		if (found==string::npos){
		cerr << "No explicit reference to \"number of hops\" found in the comment for first input line." << endl;
		cerr << usage << endl;
		exit(1);
		}	[/COLOR]
		
[INDENT]/* get first input line up to token "#" */
getline(input_buffer, before_token, '#');	[/INDENT]

		**/* DOESN'T WORK */**[COLOR="Red"]
[INDENT]/* check first part of first line for integer type. */		
found=before_token.find_first_not_of("0123456789 \t");[/INDENT]		
		if (found==string::npos){
		cerr << "Integer not found for the number of hops. Please check input:\n" << endl;
		cerr << usage << endl;
		exit (1);
			}[/COLOR]

```

Any help or hints would be greatly appreciated.  I really don't want to keep having to comment out my error checking code because I don't understand it.

I believe I am following correct form (see: [http://www.cplusplus.com/reference/string/string/find_first_not_of/]("http://www.cplusplus.com/reference/string/string/find_first_not_of/")).  What am I missing?
Thank you.

---

### Post by GeneralZod on 2010-10-17
```

before_token.find_first_not_of("0123456789 \t");

```

You don't seem to be doing anything with the return value.

---

### Post by PirateMcplunder on 2010-10-17
> **GeneralZod said:**
> ```

before_token.find_first_not_of("0123456789 \t");

```

You don't seem to be doing anything with the return value.
Sorry, I pasted in the code wrong.  I can't get the code to work even with:

found=before_token.find_first_not_of("0123456789 \t");

I changed the code in the original post to reflect this.  Any thoughts on why it wouldn't be working even when I am assigning the return value correctly?

---

### Post by GeneralZod on 2010-10-17
There's a bunch of other code missing (input_buffer's declaration; first_input_line; etc) but I'm a bit perplexed as to what it's supposed to do.

What is the value of before_token before you call find_first_not_of? I'm *guessing* it's supposed to be 

2<tab>

in which case before_token.find_first_not_of("0123456789 \t") *should* be npos.

Please post a compileable and runnable version :)

Edit: VV

Cool :)

---

### Post by PirateMcplunder on 2010-10-17
you are correct!  == should be !=

Thank you!

---

