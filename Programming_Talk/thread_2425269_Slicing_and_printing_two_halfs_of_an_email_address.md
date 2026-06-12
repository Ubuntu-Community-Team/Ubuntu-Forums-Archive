---
title: "Slicing and printing two halfs of an email address (Udemy)"
date: 2019-08-22
forum: Programming Talk
---

### Post by Drone4four on 2019-08-22
I&#8217;ve written a script which slices and prints the first half of an email address (before the &#8216;@&#8217; symbol) and then which also slices and prints the domain name (after the &#8216;@&#8217; symbol). Here is my basic script so far:

```

#!/usr/bin/env python3

email_address = "Yoseph.Stalin@hotmail.com"
print(f'Here is your email: {email_address}')
first_half = email_address[0:13]
print(f'Here is your email user name: {first_half}')
second_half = email_address[-11:]
print(f'Here is your email domain name: {second_half}')

```

Here is the output:

```

$ python script1.py
Here is your email: [email]Yoseph.Stalin@hotmail.com[/email]
Here is your email user name: Yoseph.Stalin
Here is your email domain name: hotmail.com

```

It achieves what I set out to accomplish. 

But what if I wanted to make it dynamic - - so that the script prompts the user to enter his or her email address and then dynamically discerns before and after the &#8216;@&#8217; symbol and then prints the user name and domain name (of different lengths) - - how might you people recommend I go about that?

Or to put it another way: how would I tell Python to process an email address so that it will be able to evaluate both sides of the '@' symbol and distinguish domain names of different lengths without the developer having to manually count the length of characters for each set email address?

For my future reference, I got this question from a non-credit Udemy course. This question came up as part of the string module/section. The course is titled "[The Python Bible: Everything You Need to Program in Python](https://www.udemy.com/the-python-bible/)".

---

### Post by norobro on 2019-08-22
I think string.split("@")  will do what you want: [https://docs.python.org/3/library/stdtypes.html?highlight=split#str.split](https://docs.python.org/3/library/stdtypes.html?highlight=split#str.split)

---

### Post by Drone4four on 2019-08-23
Thank you **@norobro** for your suggestion. :D

I found [a guide which shows how to perform this dynamic operation](https://www.fraudlabspro.com/resources/tutorials/how-to-extract-domain-name-from-email-address/) in 5 different programming languages like Java, C#, and Python.

Python is by far the most elegant. Here is how to extract the domain of an email in Python:

```

email = 'user@example.com'
domain = email.split('@')[1]

```

Extracting the username would be:

```

email = 'user@example.com'
username = email.split('@')[0]

```

Here is my script now:

```

#!/usr/bin/env python3

email_address = input("Please enter a fake email address and be sure to include an @ symbol: >>  ")
user_name = email_address.split('@')[0]
domain_name = email_address.split('@')[1]
print(f'Here is your email: {email_address}')
print(f'Here is your email user name: {user_name}')
print(f'Here is your email domain name: {domain_name}')

```

It runs exactly as intended.

---

### Post by SeijiSensei on 2019-08-23
How do you handle Yoseph Stalin <yoseph.stalin@example.com>?  

What about "Yoseph P. Stalin" <yoseph.stalin@example.com>?  
The quotation marks are required because the local part includes a special character.  Either ' or " can be used.

There are other legitimate formats specified in RFC2822, but these are the most common.  The address can also include a plus sign and "tag" before the @ which some clients use to route mail to specific folders.

"Yoseph P. Stalin" <yoseph.stalin+tito@example.com>

---

