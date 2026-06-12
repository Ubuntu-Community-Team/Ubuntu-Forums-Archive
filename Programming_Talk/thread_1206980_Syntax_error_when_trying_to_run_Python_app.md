---
title: "Syntax error when trying to run Python app"
date: 2009-07-07
forum: Programming Talk
---

### Post by The Toxic Mite on 2009-07-07
Hi all!

I'm trying to create an application, in where you hold a conversation with the computer (I called the "person" John :P).

Now this is my first Python program (not counting "Hello World"), and when I try to run it, it returns that there is a syntax error.

```

calvinps@InterCity-125:~$ ./John.py
./John.py: line 14: syntax error near unexpected token `('
./John.py: line 14: `name = raw_input("Hello! What is your name?")'

```

Now I did expect an error to come up, but not this kind. :P

Any help will be appreciated :D

I have attached the source file here :)

-TTM-

---

### Post by Can+~ on 2009-07-07
Run it with

[PHP]python John.py[/PHP]

If you want to run it with the "./filename.py" you need to write set the [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)") so bash knows how to execute it, like:

[PHP]#!/usr/bin/env python

the rest of my code[/PHP]

---

### Post by The Toxic Mite on 2009-07-07
Again, it complains there's something wrong with the syntax:
```

calvinps@InterCity-125:~$ python John.py
  File "John.py", line 18
    if response1 = "I'm fine" or "I'm okay" or "I'm alright", print "I'm glad to hear!"
                 ^
SyntaxError: invalid syntax
calvinps@InterCity-125:~$ #!/usr/bin/env python
calvinps@InterCity-125:~$ ./John.py
./John.py: line 14: syntax error near unexpected token `('
./John.py: line 14: `name = raw_input("Hello! What is your name?")'

```

Looking at Line 18, I can tell there's something wrong.

Trust me, I am a complete Python n00b, and I haven't done IF statements on there before! :P

---

### Post by Can+~ on 2009-07-07
[PHP]a = 3 # assigns the value of a to 3.[/PHP]

[PHP]a == 3 # compares if a's value is 3[/PHP]

> **The Toxic Mite said:**
> Again, it complains there's something wrong with the syntax:
```

calvinps@InterCity-125:~$ python John.py
  File "John.py", line 18
    if response1 = "I'm fine" or "I'm okay" or "I'm alright", print "I'm glad to hear!"
                 ^
SyntaxError: invalid syntax
calvinps@InterCity-125:~$ #!/usr/bin/env python
calvinps@InterCity-125:~$ ./John.py
./John.py: line 14: syntax error near unexpected token `('
./John.py: line 14: `name = raw_input("Hello! What is your name?")'

```

Looking at Line 18, I can tell there's something wrong.

Trust me, I am a complete Python n00b, and I haven't done IF statements on there before! :P

The reason why you get different errors is, that the "python something.py" is working properly and detected the error I mentioned above; and the ./John.py don't work because the "#!/usr/bin/env python" must go INSIDE the file on the first line, otherwise, bash will try to execute like another type of script/code and it will throw a completely different error.

---

### Post by ibutho on 2009-07-07
You've made errors in all of your if statements. They should be something like this
```

if response1 == "I'm fine" or "I'm okay" or "I'm alright":
    print "I'm glad to hear!"
if response1 = "I don't feel good" or "Not so good":
    print "Oh dear. Sorry to hear about that :-("

```

---

### Post by days_of_ruin on 2009-07-07
> **ibutho said:**
> You've made errors in all of your if statements. They should be something like this
```

if response1 == "I'm fine" or "I'm okay" or "I'm alright":
    print "I'm glad to hear!"
if response1 **==** "I don't feel good" or "Not so good":
    print "Oh dear. Sorry to hear about that :-("

```

Fixed it for you.

---

### Post by The Toxic Mite on 2009-07-08
Hi.

I edited the source code with the corrections suggested above, along with a few other adjustments, but it still doesn't work properly.

```

calvinps@InterCity-125:~$ python John.py
Hello! What is your name? Calvin
Hey! Nice to meet you, Calvin . My name is John. :D
('How are you today, ', 'Calvin', '? ')I'm alright      
I'm glad to hear!
Oh dear. Sorry to hear about that :-(
Do you think Linux is cool? Yes
That's nice to hear! :-)
Aww! Why don't you like Linux?...
Ok.
I have to go now
Goodbye Calvin !

```

The source will be attached to this post

---

### Post by Tony Flury on 2009-07-08
In your code you have lots of similar to the snippets below
```

if response1 == "I'm fine" or "I'm okay" or "I'm alright":
[CODE]

This wont do what you expect - in fact as you have seen it will ALWAYS generate a True condition so you will ALWAYS generate a response - regardless of what response1 is set to.

What will be better is to use : 

[CODE]
if response1 in ["I'm fine", "I'm okay", "I'm alright"] :

```

if you use something similar in all places you might well find that your code will work better.

also to fix the problem you have :
```

('How are you today, ', 'Calvin', '? ')

```

Try doing :
```

prompt1 = "How are you today, " + name + " ? "

```
this will build a string - which you can print normally (without getting the surrounding brackets). Your previous code was building a tuple - which is why it was printing out with brackets and commas.

One final thing - the normal recommendation is to use spaces (and not tabs) for your indentation.

---

