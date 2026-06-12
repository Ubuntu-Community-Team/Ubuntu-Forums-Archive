---
title: "[PYTHON] How do you do this?"
date: 2008-05-22
forum: Programming Talk
---

### Post by blaq145 on 2008-05-22
this is what the code should do

i got a list of responses

so when i type in

respond('The cat is on the tree', 4)

it would return the 4th response from the list

however, the list has only 12 responses, so if the number is 20
it would loop back after the 12

eg, it would go 1,2,3,4,5,6,7,8,9,10,11,12,1,2,3,4,5,6,7,8 

so the 8th would be return

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> 

eg, it would go 1,2,3,4,5,6,7,8,9,10,11,12,1,2,3,4,5,6,7,8 

so the 8th would be return

Use the modulus (%) operator. Try this

[PHP]
for x in range(0, 20):
    print (x % 8) + 1
[/PHP]

So extend that principle to your code:

[PHP]
print reponses[(user_input % (len(reponses) - 1)) + 1]
[/PHP]

If user_input is an integer that the user has entered, you will print the correct index, looping at the number of entries (len) in the array. (-1 for zero-based index)

/Lau

---

### Post by blaq145 on 2008-05-22
hi Lau

thanks for the reply

this is how it suppose to work

i got a list here called responses, and there are a total of 18 responses

so when i type in the function
respond('user_input', 19)

it should return the 1st response from the list

this is the definition

def respond(userinput, number)

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> 

i got a list here called responses, and there are a total of 18 responses

so when i type in the function
respond('user_input', 19)

it should return the 1st response from the list

this is the definition

def respond(userinput, number)

Yea, I think I understood that bit. Then this should work

[PHP]
def respond(unserinput, number):
    return responses[(number % (len(responses) - 1) + 1)]
[/PHP]

This will loop back to 1 when the *number *exceeds the length of the array.

/Lau

---

### Post by blaq145 on 2008-05-22
thanks again
i think i wasn't clear on the loop thing lol
this code returns the 1 response for all of them
(note the first response is 0 on the list) 

the list has 10 different responses ( 0 - 9 )
the code has to work for like
 
if number is 12
it would return the 2 response 

if number is 20
it would return the 9 response

i hope it makes more sense now

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> thanks again
i think i wasn't clear on the loop thing lol
this code returns the 1 response for all of them
(note the first response is 0 on the list) 

the list has 10 different responses ( 0 - 9 )
the code has to work for like
 
if number is 12
it would return the 2 response 

if number is 20
it would return the 9 response

i hope it makes more sense now

:)

Im not sure if we're completely missing each other. Please try the first code I posted:

[PHP]
for x in range(0, 20):
    print (x % 5)
[/PHP]

This will show you how to use modulus in the way youre thinking. I tried the code I posted above and it works fine. Try this:

[php]
responses = [1, 2, 3, 4, 5, 6, 7, 8, 9]

def respond(unserinput, number): 
     return responses[(number % len(responses)) - 1] 

>>> respond("bla", 12)
2
>>> respond("bla", 19)
9
[/php]

Wasn't that exactly what you were looking for?

/Lau

---

### Post by Lau_of_DK on 2008-05-22
... or maybe this is easier:

[PHP]
responses = [1, 2, 3, 4, 5, 6, 7, 8, 9] 

def respond(number):  
     return responses[(number % len(responses)) - 1] 
 
if __name__ == '__main__':
    for x in range(1, 20):
        print x,":",respond(x)
[/PHP]

If Im just confusing you, just let me know, I'll step back and let somebody else answer.

/Lau

---

### Post by blaq145 on 2008-05-22
sorry for the late reply
you've been a great help so far!

i got that working now,

but there are more.. so bear with me if you would

this where the userinput part put to use

some responses have the asterisk '*' in them, so if the response do have that, the code has to replace the * with the userinput

so im guessing something like if * found in result, replace the * with userinput, only *, but keep the ' '

i hope that's clear

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> sorry for the late reply
you've been a great help so far!

i got that working now,

but there are more.. so bear with me if you would

this where the userinput part put to use

some responses have the asterisk '*' in them, so if the response do have that, the code has to replace the * with the userinput

so im guessing something like if * found in result, replace the * with userinput, only *, but keep the ' '

i hope that's clear

Sure, its pretty clear. Could you just provide me with 1 or 2 examples of how this would be used practically?

/Lau

---

### Post by blaq145 on 2008-05-22
ok

it works like this

respond('I feel confused!', 40)
 
Expected:
    "I don't understand what you mean by 'I feel confused!'."

But instead with the current code i would just get:
    "I don't understand what you mean by '*'."

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> ok

it works like this

respond('I feel confused!', 40)
 
Expected:
    "I don't understand what you mean by 'I feel confused!'."

But instead with the current code i would just get:
    "I don't understand what you mean by '*'."

Im not sure I fully understand, but youre probably looking for something like this

[PHP]
def respond(user_input, number):   
    if user_input.__contains__("*"):
        return "I dont know what you mean by", user_input
    else:
        return responses[(number % len(responses)) - 1] 
[/PHP]

That type of thing?

/Lau

---

### Post by blaq145 on 2008-05-22
Hmm, im not sure what that code does

Basically, it's like this

when I put in

respond('I feel confused!', 10)

let's say the 11th response on the list is 'I don't know what you mean by '*'.

it's going to return 

"I don't know what you mean by 'I feel confused!'."

so it replaced the * in the response with the 'I feel confused!'

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> 
"I don't know what you mean by 'I feel confused!'."

so it replaced the * in the response with the 'I feel confused!'

Ahh, now I get it :)

This should do it 

[PHP]
def respond(user_input, number):    
    str_response = responses[(number % len(responses)) - 1] 
    return str_response.replace("*", user_input)
[/PHP]

/Lau

---

### Post by blaq145 on 2008-05-22
the * is still there :/

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> the * is still there :/

Re-read your code, you've got a bug. I got this

[PHP]

responses = ["you said *", "they said *"] 

def respond(user_input, number):  
    str = responses[(number % len(responses)) - 1] 
    return str.replace("*", user_input)
 
if __name__ == '__main__':    
    print respond("testing", 1)

Output:
you said testing
[/PHP]

---

### Post by blaq145 on 2008-05-22
the * is still there
I might forgot to mention that not all the responses in the list has the '*'
maybe that changes things?

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> the * is still there
I might forgot to mention that not all the responses in the list has the '*'
maybe that changes things?

Should make a difference. The replace function is very simple

t = "hello miss"
t.replace("miss", "sir")
print t
>> hello sir

So basically that last code should just replace any star with whatever the user entered. If it doesn't work you probably have a bug. You can try posting the entire code if you like.

/Lau

---

### Post by blaq145 on 2008-05-22
```
def respond(user_input, number):  
    str = responses[(number % len(responses)) - 1] 
    return str.replace("*", user_input)
```

this is the code i used

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> ```
def respond(user_input, number):  
    str = responses[(number % len(responses)) - 1] 
    return str.replace("*", user_input)
```

this is the code i used

Yea, I meant the ENTIRE code. The only thing that could make the code above malfunction, is if there's some formatting distburing the "*" in your response. is it purely a " * "  (space)(star)(space) ? If so, try that str.replace(" * ", user_input)...


/Lau

---

### Post by blaq145 on 2008-05-22
what do you mean?

that's my entire code, unless i missed something again :/

it's '*'

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> what do you mean?

that's my entire code, unless i missed something again :/

it's '*'

k, then try

return str.replace("'*'", user_input)

Or preferably, change the formatting so your responses only have " * " and no '*' or anything else that can disturb replace.

/Lau

---

### Post by blaq145 on 2008-05-22
the list is fixed, im not supposed to change it

i changed it anyway to test it out, but it's still the same result

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> the list is fixed, im not supposed to change it

i changed it anyway to test it out, but it's still the same result

Then Im out of good ideas.
Unless you can post your ENTIRE program, every single line associated to this program, I can do anymore for you :(

/Lau

---

### Post by blaq145 on 2008-05-22
Well good news, it works now. Haha you're great help man. Thanks alot.

But I wonder if you could help me out with some more...

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> Well good news, it works now. Haha you're great help man. Thanks alot.

But I wonder if you could help me out with some more...

Sure, you need help with some laundry? :)


/Lau

---

### Post by blaq145 on 2008-05-22
Haha, no
but it would be great if you can help me with this one

this code works to remove all the punctuations, preceding whitespace and trailing whitespace in a sentence

here's my code
```
def standardise_phrase(string):

    punctuation_list = ['!', '?', ',', '.']

    length = len(punctuation_list)

    for x in range(0, length):
        string = string.replace(punctuation_list[x], '')

    return string
```

here are some examples how it should work

standardise_phrase('I am happy today')
Expecting:
    'I am happy today'

standardise_phrase("  What's going on here ! ! ? ?  ")
Expected:
    "What's going on here"

standardise_phrase('  , , ,,,!!!???   ')
Expected:
     ''

---

### Post by Lau_of_DK on 2008-05-22
How about just filtering out non-alphanumeric characters?


[PHP]
def afilter(str):    
    y = ""
    for x in range(0,len(str)):
        if str[x].isalpha():
            y += str[x]
             
    return y

if __name__ == '__main__':    
     
     print afilter("!#$$@'hi there!!,.,.#")

output: "hi there"
[/PHP]

/Lau

---

### Post by Lau_of_DK on 2008-05-22
Alternatively, if you want more control

[PHP]
def afilter(str):     
    blacklist = [',','!','.','$','#']

    y = "" 
    for x in range(0,len(str)): 
        if not t[x] in blacklist: 
            y += str[x] 
              
    return y 

if __name__ == '__main__':     
      
     print afilter("!#$$@'hi there!!,.,.#") 

output: "hi there" 
[/PHP]

---

### Post by blaq145 on 2008-05-22
yours work the same as mine as some of the preceding whitespace and trailing whitespace in the sentence are still there

eg
standardise_phrase("  What's going on here ! ! ? ?  ")
    
Expected:
    "What's going on here"
Got:
    "__What's going on here_______"

standardise_phrase('  , , ,,,!!!???   ')
    
Expected:
    ''
Got:
    '________'

---

### Post by geirha on 2008-05-22
strip() will return the string with preceeding and trailing whitespace removed, so add that one last. I.e. with the above code:
[php]def afilter(str):     
    blacklist = [',','!','.','$','#']

    y = "" 
    for x in range(0,len(str)): 
        if not t[x] in blacklist: 
            y += str[x] 
              
    return y.strip()
[/php]

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> 
    ''
Got:
    '________'

Youre right, I missed that.
There are a few ways you can solve it, I'd prefer

[PHP]
def afilter(str):    
    blacklist = [',','!','.','$','#','@','\''] 
     
    y = ""
    
    for x in range(0,len(str)):  
        if not str[x] in blacklist:  
            y += str[x]  
               
    return y.split()
[/PHP]

So you get it back as a list, but you could also return y.ljust(0).strip() instead of the split(). Both will work, just in different ways.

/Lau

---

### Post by blaq145 on 2008-05-22
Thanks, that worked great. I know I've been a handful. But I have just one last question.

If you're willing to hear it out.

Ok, so after all those preceeding spacings and punctuations are removed.
I use the string and match every words in it to a list of words.
Here's a part of the list, just to give an idea. So the words found on the left side, will be replaced with the word on the right side.

word_list
[
 [['Hi', "G'day", 'Hey'],                               'Hello'],
 [['Bye', 'Farewell', 'Later', 'Ciao', 'Quit'],         'Goodbye'],
 [["don't"],                                            'do not'],
 [["Don't"],                                            'Do not'],
 [["doesn't"],                                          'does not'],
 [["can't"],                                            'cannot'],
 [["won't"],                                            'will not'],
 [["wouldn't"],                                         'would not'],
 [["shouldn't"],                                        'will not'],
 [['recollect', 'recall'],                              'remember'],
 [['dreamt', 'fantasised', 'imagined'],                 'dreamed'],

eg. 
"I've imagined about this"
 would return
"I have dreamed about this"

```
def search_terms(string):
    
    string = replace_punctuation(string)
```

---

### Post by blaq145 on 2008-05-22
Ops, I guess that's too much.

Lots of thanks to Lau, you're a champ!

---

### Post by Lau_of_DK on 2008-05-22
> **blaq145 said:**
> Ops, I guess that's too much.

Lots of thanks to Lau, you're a champ!

No prob =)

Its not too much, Im just not a my computer anymore, if you can wait somewhere between 1 - 4 hours, I'll be back :)

In the meantime, anybody else with a Python running that can help him out?

/Lau

---

### Post by Lau_of_DK on 2008-05-22
Hi again,

I haven't been able to test this, but I imagine it would work :)

[PHP]
def search_terms(str):
    for item in word_list:
        if str in item[0]:
            return item[1]
[/PHP]

Let me know how it goes - it might require a little tweaking.

/Lau

---

### Post by imdano on 2008-05-22
> **Lau_of_DK said:**
> Youre right, I missed that.
There are a few ways you can solve it, I'd prefer

[PHP]
def afilter(str):    
    blacklist = [',','!','.','$','#','@','\''] 
     
    y = ""
    
    for x in range(0,len(str)):  
        if not str[x] in blacklist:  
            y += str[x]  
               
    return y.split()
[/PHP]

So you get it back as a list, but you could also return y.ljust(0).strip() instead of the split(). Both will work, just in different ways.

/LauA few points about this code:
- You probably shouldn't use the variable "str", since its overwriting the builtin python type 'str'.  It doesn't affect anything here, it's just a bad practice in general.

- Instead of doing this [php]    for x in range(0,len(str)):  
        if not str[x] in blacklist:  
            y += str[x][/php]You can just do
[php]    for x in str:  
        if not x in blacklist:  
            y += x[/php]

- Here's alternative way of implementing the filter as well:
[php]def afilter(val):
    blacklist = [',','!','.','$','#','@','\'']
    for x in blacklist:
        val = val.replace(x, "")
    return val.strip()[/php]

---

### Post by geirha on 2008-05-22
Let's put the whole function on one line while we're at it :)
[php]
>>> standardise_phrase= lambda x: "".join([c.strip(",!.$#@?") for c in x]).strip()
>>> standardise_phrase(" What's going on here ! ! ? ? ")
"What's going on here"
[/php]

---

### Post by Wybiral on 2008-05-22
> **imdano said:**
> [php]def afilter(val):
    blacklist = [',','!','.','$','#','@','\'']
    for x in blacklist:
        val = val.replace(x, "")
    return val.strip()[/php]

The performance of this would be terrible! Not only does it return a new string for each blacklist character, it has to iterate the entire string being filtered for each of them too (implied by "replace").

The best way would be either a generator expression, or actually using "filter" (that's what it's there for).

```

"".join(c for c data if c not in blacklist)

```

```

filter(lambda c: c not in blacklist, val)

```

---

### Post by Can+~ on 2008-05-22
Another method is using a translation, but this requires the string module (which is kinda deprecated).

[PHP]
import string

#Identity translation makes no changes.
identity = string.maketrans('','')

#            the string                 table     deleted chars
print "WHAT THE F...? !?! !?!".translate(identity, ",!.$#@?")[/PHP]

I don't know how the translate works, but I guess it maps each character to another, therefore, making it O(1) as it doesn't have to transverse through a m-list of restricted characters (O(m)), but still has to go through each letter on the original string.

---

### Post by Lau_of_DK on 2008-05-23
> **Wybiral said:**
> 
The best way would be either a generator expression, or actually using "filter" (that's what it's there for).


I have to let you guys know, that when this thread first sprung up and I posted my simplistic noob approaches here, Wybiral was good enough to PM me a full page tutorial on Generator expressions with references to languagues he knew, that I knew! :) What a guy!

:guitar:

---

