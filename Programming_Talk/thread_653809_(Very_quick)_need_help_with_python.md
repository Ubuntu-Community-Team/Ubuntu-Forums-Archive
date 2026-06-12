---
title: "(Very quick) need help with python"
date: 2007-12-30
forum: Programming Talk
---

### Post by sammydee on 2007-12-30
Hi all

I'm currently teaching myself python.

I only started a couple of days ago and it's my first programming language (haven't even used basic before) so this is a very basic question.

I want to write a little program that asks for input and outputs "hooray" if it matches the integer, '7', "try again" if input is a number and "invalid input" if the input is not a number.

I've tried lots of different ways using int(input) to try and convert raw_input into an integer. This works but if the input is anything other than a number, if outputs a nasty messy error. Are there other ways of checking to see if raw_input is an integer or not?

Note: I also tried types.IntType but raw_input treats all input as a string by default so it doesn't work.

thanks
Sam

---

### Post by luisromangz on 2007-12-30
The nasty error is actually an exception. You can use the try ... except mechanism to act in case the input is not a number, which will raise the ValueError exception.

---

### Post by MicahCarrick on 2007-12-30
You can use raw_input to get user intput as a string. Then, python's exception handling try: and except: will help you determine if they entered a number or not.

```
    # use raw_input to ensure what the user entered is a string
    
    strval = raw_input('Enter a number: ')
    
    # try to convert the string the user entered into an int
    
    try:
        number = int(strval)
    except:
    
        # if conversion failed, we assume they did not enter a number
        
        print "You did not enter a number!"
        sys.exit(0)
    
    if number == 7:
        print "Yay! You entered 7!"             # user entered '7'
    else:
        print "Sorry,", number, "is incorrect." # user entered different number
```

---

### Post by ghostdog74 on 2007-12-30
> **sammydee said:**
> Hi all

I'm currently teaching myself python.

I only started a couple of days ago and it's my first programming language (haven't even used basic before) so this is a very basic question.

I want to write a little program that asks for input and outputs "hooray" if it matches the integer, '7', "try again" if input is a number and "invalid input" if the input is not a number.

I've tried lots of different ways using int(input) to try and convert raw_input into an integer. This works but if the input is anything other than a number, if outputs a nasty messy error. Are there other ways of checking to see if raw_input is an integer or not?

Note: I also tried types.IntType but raw_input treats all input as a string by default so it doesn't work.

thanks
Sam

I suggest you go through all of [this]("http://docs.python.org/tut/") first.

---

### Post by sammydee on 2007-12-31
Thanks.

I'm going through a few tutorials at the moment but I'll take a look at that one too.

Sam

---

### Post by LaRoza on 2007-12-31
> **ghostdog74 said:**
> I suggest you go through all of [this]("http://docs.python.org/tut/") first.

[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html) would be better for the OP's issue.

Very good article.

---

### Post by ghostdog74 on 2007-12-31
> **LaRoza said:**
> [http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html) would be better for the OP's issue.

Very good article.

Yes, its a good read. However if OP has gone through the tut, from beginning to the end, he should have come across this [page]("http://docs.python.org/tut/node10.html"). Section 8.3 shows him how to do what he wants.

---

### Post by LaRoza on 2007-12-31
> **ghostdog74 said:**
> Yes, its a good read. However if OP has gone through the tut, from beginning to the end, he should have come across this [page]("http://docs.python.org/tut/node10.html"). Section 8.3 shows him how to do what he wants.

The method isdigit() be much more suitable for this.

[php]
    # use raw_input to ensure what the user entered is a string
    
    strval = raw_input('Enter a number: ')
    
    # see if the input is a number:
    if strval.isdigit():
        if strval == 7:
            print "Yay! You entered 7!"             # user entered '7'
        else:
                print "Sorry,", number, "is incorrect." # user entered different n
    else:
        print "You didn't enter a number"
[/php]

Is much better than the first code example.

---

### Post by ghostdog74 on 2007-12-31
> **LaRoza said:**
> The method isdigit() be much more suitable for this.

It doesn't matter,  I am only saying that the tutorial shows him a way to do what he wants, if he reads it. Whether he finds a better way to do what he wants in future, that's up to him to find out. 

> 
Is much better than the first code example.
I did not write that code.

---

### Post by LaRoza on 2007-12-31
> **ghostdog74 said:**
> It doesn't matter,  I am only saying that the tutorial shows him a way to do what he wants, if he reads it. Whether he finds a better way to do what he wants in future, that's up to him to find out. 


I did not write that code.

The Python docs are the best for almost anything I have seen. I always recommend that they get downloaded and used.

The code that was posted used exceptions to achieve the OP's goal, your link and direct reference to part of it, was about exceptions.

---

