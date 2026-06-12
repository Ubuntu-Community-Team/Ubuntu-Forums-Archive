---
title: "[Beginner] Programming Challenge: 2"
date: 2008-08-05
forum: Programming Talk
---

### Post by LaRoza on 2008-08-05
The last challenge was very popular with many entries. Hopefully, the comments and other code was informative. Here is the last challenge: [http://ubuntuforums.org/showthread.php?t=876479](http://ubuntuforums.org/showthread.php?t=876479)

For this one, I ask non beginners to not give solutions that give away too many hints to those trying.


[size=+1]The Challenge:[/size]
The most problematic part of programming is user input. The best program can fall apart because of users. No matter what you ask in a program, expect the user to give random input or nothing at all. One of the entries in the previous challenge was disqualified because as I tested the code (before reading it, to see if it did what it was supposed to do), I was confronted with a vague prompt. It didn't really give an indication of what I was supposed to enter. I entered nothing, and exception was thrown because the program tried to read a part of the string and the program ended.

Another one asked for input, but kept looping, no way to cancel it!

I suggest you all read this article: [Saving Users From Themselves](http://linuxgazette.net/issue83/evans.html)

It is using Python as the language, so entries using Python will have a good guide to follow, but any language is allowed (and somewhat prefered for this challenge)

Write a program to take a person's **forum name**, **age**, **forum user id** (a postive integer equal to or between 1 and 999999). The program should ask for each datum individually, and not go to the next unless the previous was valid. If there is an error, it must prompt again until it is write or the program is halted. The entry "quit" should exit the program at any question.

If all data is entered, it should print a sentence like:
```

You are LaRoza, aged 20 next year you will be 21, with user id 266234, the next user is 266235.

```

In short:
[list]
[*] User name can't begin with spaces, or have no characters in it. It can truncate strings over 20, if needed.
[*] Age has to be positive and not 0. It doesn't need a maximum, but you are free to make your program logical. 
[*] User ID can't be negative or 0. The maximum I require is 999999.
[*] Typing "exit" should exit the program gracefully.
[*] The prompt should be logical.
[*] Most importantly, it **must not crash, segfault, lockup, or enter an infinite loop no matter what is entered**
[/list]


[size=+1]Rules:[/size]
Do not copy code, but you can obviously read it :-)

Try not to comment on other submissions. It will be hard to judge changing entries. If you edit your code, post the new version and make it clear there is a new code.

[size=+1]How it will be judged[/size]
This task is a bit more about programming than the previous, so you'll be judged on how ell the program works.

[list]
[*] If I can segfault it, it is disqualified. (hint, C users have a big challenge, but if it works, you are almost guaranteed to win. Input in C is not trivial. To make this simpler, I will not enter a string bigger than 20 characters for valid data, but larger strings shouldn't cause problems. Truncate them.)
[*] If I can make it throw an exception that is not caught and handled, it is disqualified (Python users, you can test data and catch exceptions, I recommend both)
[*] Unicode is not required, but if there are many entries in the final judging, unicode will be the tie breaker (use the first part of my title before the | to test)
[*] If I can't exit the program without killing it, it will be disqualified. 
[*] Prompts should be logical and tell how to exit.
[/list]

As before, try to follow the following (although I think it won't come down to judging on this, as the challenge will be tricky for beginners):
[list]
[*] Clean code. Readable code is a must for being a programmer who wishes to possibly interact with others. Some languages can be more readable than others, so it will be judged on the effort of writing clean code, not which language is easier to read by design.
[*] Logical code. Be a programmer, not a code monkey :-)
[*] Commented code. If something is possibly unclear (like an obscure use of math), let the readers know. Do not over comment, and let the code speak for itself whenever you can. Have logical variable names and function names. (Excessive commenting is a minus factor)
[*] Working code. It has to work as it is posted. The codw will be read on the forum, so remember to use this guide to paste code if you don't know how: [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)
[/list]

[size=+1]Hints:[/size]
[list]
[*] If you use C, be wary of input functions. I recommend getting everything as a string and testing it. 
[*] Since you will be performing math on the data, you should watch out for illogical answers. All numbers will be integers, so watch out for large numbers! I shouldn't get infinity or 0 anywhere!
[*] Using this challenge to try out a new language brings you bonus points, so please state when you are using the language for the first time if you are.
[/list]

---

### Post by drubin on 2008-08-05
Just want to start it off and say good, Luck to all and Thanks again LaRoza

---

### Post by kpatz on 2008-08-05
> **LaRoza said:**
> Prompts should be logical and tell how to exit.

"To exit, just hold down escape, control, tab, alt, both shifts, num lock and the little squiggly until your screen turns blue. Then, stare at it until your shift ends." ;)

(courtesy of [Strong Bad](http://www.hrwiki.org/index.php/from_work))

But, kidding aside, any plans for programming challenges for the more advanced programmer geeks?

---

### Post by drubin on 2008-08-05
> **kpatz said:**
> "To exit, just hold down escape, control, tab, alt, both shifts, num lock and the little squiggly until your screen turns blue. Then, stare at it until your shift ends." ;)

(courtesy of [Strong Bad](http://www.hrwiki.org/index.php/from_work))

But, kidding aside, any plans for programming challenges for the more advanced programmer geeks?

I don't think it is fair to expect her to do those as well :) Maybe some one else has the time would be willing to take them on.

---

### Post by LaRoza on 2008-08-05
> **kpatz said:**
> 
But, kidding aside, any plans for programming challenges for the more advanced programmer geeks?

[http://ubuntuforums.org/showthread.php?t=783387](http://ubuntuforums.org/showthread.php?t=783387)

[http://ubuntuforums.org/showpost.php?p=5497968&postcount=18](http://ubuntuforums.org/showpost.php?p=5497968&postcount=18)

The older list was more advanced, but the index is now out of date, and no one has continued the challenges. Feel free to pick them up.

---

### Post by bobbocanfly on 2008-08-05
Im almost certain there are cleaner ways to do this. Anyway, here is my attempt in Python:
```
#!/usr/bin/env python

import sys

class User:

    #Sets up variables for the class & prints banner
    def __init__(self):
        self.username = ""
        self.age = 0
        self.uid = 0
        
        #Print a quick set of instructions so people dont get lost 
        print "Please fill in the correct data or type exit to quit"
        
    #Checks to see if the user wants to quit
    def check_quit(self, uinput):
        if uinput== "exit":
            sys.exit(0)


    #Gets the users forum username
    def get_username(self):
        user_input = raw_input("Type your forum username: ")
    
        self.check_quit(user_input)
    
        #Check string is correct length
        if len(user_input) > 20:
            print "Usernames must be less than 20 characters long"
            self.get_username()
        elif len(user_input) < 1:
            print "Usernames must be at least 1 character long"
            self.get_username()
        else:
            #Use exception handling to detect if user is giving invalid data
            try:
                self.username = str(user_input)
            except:
                print "Username must be in string format"
                self.get_username()
           
    #Gets the users age     
    def get_age(self):
        user_input = raw_input("Type your age: ")

        self.check_quit(user_input)
        
        #Convert the output of range() to string so we can convert safely
        #to integer (with error handling) later on
        if user_input not in str(range(1, 999999)):
            print "Please enter a number between 1 and 999999"
            self.get_age()
        else:
            try:
                self.age = int(user_input)
            except:
                print "Please enter a number between 1 and 999999"
                self.get_age()
           
    #Gets the users forum user id     
    def get_uid(self):
        user_input = raw_input("Type your forum user id: ")

        self.check_quit(user_input)

        #Convert the output of range() to string so we can convert safely
        #to integer (with error handling) later on      
        if user_input not in str(range(1, 999999)):
            print "Please enter a number between 1 and 999999"
            self.get_uid()
        else:
            try:
                self.uid = int(user_input)
            except:
                print "Please enter a number between 1 and 999999"
                self.get_uid()
                
    #Shows the final string
    def show_string(self):
        print "You are %s, aged %s next year you will be %s, with user id %s, the next user is %s." % (
              self.username, self.age, self.age + 1, self.uid, self.uid + 1)

if __name__ == "__main__":
    usr = User()
    usr.get_username()
    usr.get_age()
    usr.get_uid()
    usr.show_string()
```

---

### Post by LaRoza on 2008-08-05
Remember: 0 isn't valid as an age or id, and ages have to be realistic. Also, names can be over 20, but they can be truncated (this is for C programmers mainly). Python doesn't have this issue really, so you can accept longer user names.

---

### Post by slavik on 2008-08-05
> **kpatz said:**
> "To exit, just hold down escape, control, tab, alt, both shifts, num lock and the little squiggly until your screen turns blue. Then, stare at it until your shift ends." ;)

(courtesy of [Strong Bad](http://www.hrwiki.org/index.php/from_work))

But, kidding aside, any plans for programming challenges for the more advanced programmer geeks?
heh, I just wrote LaRoza a message regarding advanced challenges.

---

### Post by jimi_hendrix on 2008-08-05
> **kpatz said:**
> "To exit, just hold down escape, control, tab, alt, both shifts, num lock and the little squiggly until your screen turns blue. Then, stare at it until your shift ends." ;)

(courtesy of [Strong Bad](http://www.hrwiki.org/index.php/from_work))


what does this do...

and i have a questions...

if i enter the max id number (99999 i think it was) should it say "the next user will be 100000" or "you are the last user"

---

### Post by LaRoza on 2008-08-05
> **jimi_hendrix said:**
> 
if i enter the max id number (99999 i think it was) should it say "the next user will be 100000" or "you are the last user"

999999 (6 digits).

No, it can go beyond, it just has to accept at least that amount and there will be no penalty for not accepting longer numbers.

---

### Post by lisati on 2008-08-05
> **LaRoza said:**
> I suggest you all read this article: [Saving Users From Themselves](http://linuxgazette.net/issue83/evans.html)

It is using Python as the language, so entries using Python will have a good guide to follow, but any language is allowed (and somewhat prefered for this challenge)



+1: Some good ideas in the article that have their application in other languages besides Python.
One of my early programming efforts (30 years ago, ouch! At school, before computers in school were as common as they are today) would have benefitted from some of the tips presented so far....

I might wander off and contemplate this challenge, it will be good to brush up on my programming skills, which have become a little rusty lately from lack of use.

(Thinks quietly to self: a couple of Pascal books are on the table beside me....might be interesting.....better give the newer programmers a chance first though)

---

### Post by jimi_hendrix on 2008-08-05
o and 1 other question...does it have to say it in the exact format that you wrote up there or can i format it differently as long as it shows the same info

---

### Post by LaRoza on 2008-08-05
> **jimi_hendrix said:**
> o and 1 other question...does it have to say it in the exact format that you wrote up there or can i format it differently as long as it shows the same info

As long as it does what it says, you can follow a different format.

---

### Post by British0zzy on 2008-08-05
I have a quick question. When will this challenge be judged (final day for submissions?)
I can probably whip something up in a couple days, but I'm kinda busy.
So for C programmers, if a user enters a name longer than 20, it should be truncated? Or should there be an error message? And should there be a error message if a user tries to input a ridiculously long name in the input field?
Also, is there a max age?
Cool contest,
Rich

---

### Post by OutOfReach on 2008-08-05
I'm starting to love these challenges.
I'll whip something up and post back here. :D

---

### Post by jimi_hendrix on 2008-08-05
i am oveously not allowed to use a GUI right...

---

### Post by chris200x9 on 2008-08-05
how are we supposed to know if the username is valid? or do you just mean a valid age eg. not 500?

---

### Post by linkmaster03 on 2008-08-05
jimi: Well, there's no point for one. And since it's Visual C, the judge probably wouldn't want it any more anti-Linux with Windows GUI.

---

### Post by OutOfReach on 2008-08-05
One question, a user name can't be a number right? (e.x. 1337).

---

### Post by schauerlich on 2008-08-05
Are there any restrictions as to what characters are allowed in the username?

---

### Post by jimi_hendrix on 2008-08-05
[QUOTE=linkmaster03]jimi: Well, there's no point for one. And since it's Visual C, the judge probably wouldn't want it any more anti-Linux with Windows GUI.[/QUOTE]

curse you microsoft...

EDIT: wrong quote

---

### Post by linkmaster03 on 2008-08-05
I think usernames should be allowed to contain numbers. Considering many usernames contain atleast one number.

---

### Post by chris200x9 on 2008-08-05
```
 #include <iostream>
#include <string>
using namespace std;
int main () {
	int age;
	
	int ID;
	string name;
	cout << "put in your forum name foo!" << endl; 
	cin >> name;
    cout << "how old are you?" << endl;
	cin >> age;
	while ( age > 100 || age < 1) {
		cout << "dude stop lying!" << endl;
		cout << "input your real age" << endl;
	cin >> age;
	
		}
	
	cout << "input your forum I.D" << endl;
	cin >> ID;
	
	
	while ( ID < 1 || ID > 999999)
	{
		cout << "I think you put your I.D in wrong, please input it again?" << endl;
		cin >> ID;
		
		
	}
		
cout << "You are " << name << ", aged " << age << " next year you will be " << age + 1 << ", with user id " << ID << ", the next user is " << ID + 1;
	
	// You are LaRoza, aged 20 next year you will be 21, with user id 266234, the next user is 266235.
	
    return 0;
}

```

---

### Post by LaRoza on 2008-08-05
> **British0zzy said:**
> I have a quick question. When will this challenge be judged (final day for submissions?)

When it is finished. Since you expressed a desire to take part, I would wait for you :-)

> 
So for C programmers, if a user enters a name longer than 20, it should be truncated? Or should there be an error message? And should there be a error message if a user tries to input a ridiculously long name in the input field?

I don't know if the forum has a user name limit, and I chose 20 sort of randomly. This is to prevent paranoia about extremely long buffers for C programmers. It shouldn't crash the program. Basically, a user name is a maximum of 20 characters for it to pass. How it handles it is up to you. I don't care if it truncates it or asks for a shorter name.

If a C version is made that can handle any length, I'd be impressed :-)

> 
Also, is there a max age?
Cool contest,
Rich
If you want there to be.

> **jimi_hendrix said:**
> i am oveously not allowed to use a GUI right...

You can have one made with a GUI. It has to be free, and let me know what I need to compile it though. Packages should be in Ubuntu repos.

> **chris200x9 said:**
> how are we supposed to know if the username is valid? or do you just mean a valid age eg. not 500?

Not blank for a user name (no leading spaces either)

For a valid age, it has to be a possible age. So 0 is out or negative numbers at the very least.

> **OutOfReach said:**
> One question, a user name can't be a number right? (e.x. 1337).

> **EDavidBurg said:**
> Are there any restrictions as to what characters are allowed in the username?
No. As I mentioned, ascii will be used for testing, but if there are highly competitive versions (which I doubt, as it would require 10 to be equal), I will use unicode.

---

### Post by ghostdog74 on 2008-08-05
@laroza, i think it would be good to update these "clarifications" to the first post and then remove those posts that ask questions, to avoid cluttering the thread. ie, only posts of solutions should remain.

---

### Post by LaRoza on 2008-08-05
> **ghostdog74 said:**
> @laroza, i think it would be good to update these "clarifications" to the first post and then remove those posts that ask questions, to avoid cluttering the thread. ie, only posts of solutions should remain.

I updated my post, but I am not going to remove posts unless they go off topic.

---

### Post by arsenic23 on 2008-08-05
Doing this in python seemed very straight forward, so I thought I'd try it out in bash.  Fairly amusing too, since I've only ever used bash scripts to sed and grep through files and string sed, grep, find, and rename commands together..  

Originally I was going to modify the user's input with sed and compare it to the original input.  The idea was to force the input to be correct with sed, and then if it wasn't I could tell by seeing if userinput was equal to modified userinput.  It was a mess.

ANYWAY, I still ended up doing it in bash, since I'd already started into it.  
I had some odd problems with this one.  For instance, could someone explain to me why *[ $userinput -lt 4 ]* works and *[ $userinput < 4 ]* doesn't ?? I thought they'd act exactly the same, but when I used '<' the elif would never run, even when it should have been true.

Anyway, I supose I still took the easy way out, since bash's variables aren't really typed, but I don't have time to mess with a language I'm not familiar with at all right now, and the only ones I've looked into are bash and python.

Entry:
[PHP]#!/usr/bin/env bash
# It's ugly, but it works
# Also, -- formated to have no horizontal scroll on the forums.

promptText(){	# I have no idea why I didn't use the prompt
		# flag read has.  This is a pretty puny function.
echo -n "Input "$currant "('quit' to exit): " 
}		# $currant is set before each function is called.

nameCheck(){
promptText
read userinput
if [ $userinput = 'quit' ]; then echo "I sure hope 'quit' isn't your username." 
	exit; fi
if [ $userinput =  ]; 	# Makes sure that something is input
	then echo "	Input error, please enter your username!"
	echo "	Your username must contain at least 1 character." 
	nameCheck 2> /dev/null
else name=$userinput
fi
}

ageCheck(){
promptText
read userinput
if [ $userinput = 'quit' ]; then exit; fi
if [ ! $(echo "$userinput" | grep -E "^[0-9]+$") ] # test for positive number
	then echo "	Input error."
	echo "	Your age must be a positive number between 3 and 120." 
	ageCheck 2> /dev/null
elif [ $userinput -lt 4 ]	# test to make sure age is > 4
	then echo "	Input error: I think you are more then "$userinput" years old."
	echo "	Your age must be a number between 3 and 120."
	ageCheck 2> /dev/null
elif [ $userinput -gt 120 ]	# test to make sure age is < 120
	then echo "	Input error: I think you are less then "$userinput" years old."
	echo "	Your age must be a number between 3 and 120."
	ageCheck 2> /dev/null
else age=$userinput
fi
}

forumidCheck(){
promptText
read userinput
if [ $userinput = 'quit' ]; then exit; fi
if [ ! $(echo "$userinput" | grep -E "^[0-9]+$") ] # test for positive number
	then echo "	Input error. I doubt "$userinput" is your forum ID."
	echo "	Your forum ID must be a positive number greater then 0." 
	forumidCheck 2> /dev/null
elif [ $userinput -lt 1 ]	# test to make sure forum ID is not 0
	then echo "	Input error. I doubt "$userinput" is your forum ID."
	echo "	Your forum ID must be a positive number greater then 0."
	forumidCheck 2> /dev/null
else forumid=$userinput
fi
}


currant="your name"; clear 
nameCheck 2> /dev/null	# sets $name to entered username
currant="your age"; clear
ageCheck 2> /dev/null	# sets $age to entered age ( 4-120 )
currant="your forum ID"; clear
forumidCheck 2> /dev/null # sets $forumid to entered ID ( > 0 )
# NOTE: The above functions are called with errors redirected to /dev/null
#       They were sometimes giving unimportant errors out that should
#       not effect the script.

clear; echo " "	# formated the variables bold below  ||
		#				     \/
echo -ne "Your name is \033[1m"$name"\033[0m, you are \033[1m"$age"\033[0m years old, and \
you smell bad. \nAlso your forum ID is \033[1m"$forumid"\033[0m.  The next user is \
 \033[1m"$(($forumid+1))"\033[0m."
echo -e " \n"[/PHP]

---

### Post by ghostdog74 on 2008-08-05
> **arsenic23 said:**
> Doing this in python seemed very straight forward, 

explain to me why *[ $userinput -lt 4 ]* works and *[ $userinput < 4 ]* doesn't ?? I thought they'd act exactly the same, but when I used '<' the elif would never run, even when it should have been true.

please see the link in my sig to learn bash. In it, you will come across [this](http://tldp.org/LDP/abs/html/comparison-ops.html). you will understand after reading that. also you might want to implement a while loop
```

while true
do
 #ask for input
 # if user ask for quit, then quit
 # else do something else
 ...
 ..
done

```

---

### Post by arsenic23 on 2008-08-06
> **ghostdog74 said:**
> please see the link in my sig to learn bash. In it, you will come across [this](http://tldp.org/LDP/abs/html/comparison-ops.html). you will understand after reading that. also you might want to implement a while loop


Thanks, the bash help I had been using never explained the need for "(( ))" when comparing ints.  In fact it had a chart that said that -lt and < where the same thing.  I had tried something like [ $((val < 9)) ] thinking it was something like that and having used $(( stuff )) to do simple math is bash before.  heheh

So is there a terribly good reason to use a while loop in this situation?  I really only did it like this because I was interested in seeing if bash would get angry if I had functions call themselves.  I put in incorrect input over and over again to see if it would raise a fuss, but it seemed to work alright.

---

### Post by Wybiral on 2008-08-06
HTML 4.01 Strict

```
[color=#BC7A00]<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN"
   "http://www.w3.org/TR/html4/strict.dtd">[/color]

[color=#008000]**<html>**[/color]
[color=#008000]**<head>**[/color]
[color=#008000]**<title>**[/color][Beginner] Programming Challenge: 2[color=#008000]**</title>**[/color]
[color=#008000]**<script **[/color][color=#7D9029]type=[/color][color=#BA2121]"text/javascript"[/color] [color=#7D9029]src=[/color][color=#BA2121]"http://www.google.com/jsapi"[/color][color=#008000]**></script>**[/color]
[color=#008000]**<script **[/color][color=#7D9029]type=[/color][color=#BA2121]"text/javascript"[/color][color=#008000]**>**[/color]google.load([color=#BA2121]"jquery"[/color][color=#666666],[/color] [color=#BA2121]"1.2.6"[/color]);[color=#008000]**</script>**[/color]
[color=#008000]**<script **[/color][color=#7D9029]type=[/color][color=#BA2121]"text/javascript"[/color][color=#008000]**>**[/color]
[color=#008000]**function**[/color] as_int(x) {
    [color=#008000]**var**[/color] notdigit [color=#666666]=[/color] [color=#008000]**function**[/color](c){ [color=#008000]**return**[/color] ([color=#BA2121]"-0123456789"[/color].indexOf(c) [color=#666666]==[/color] [color=#666666]-[/color][color=#666666]1[/color]); }
    [color=#008000]**if**[/color]([color=#666666]![/color]x.length) [color=#008000]**throw**[/color] [color=#BA2121]"No integer to parse"[/color][color=#666666];[/color]
    [color=#008000]**for**[/color]([color=#008000]**var**[/color] c [color=#008000]**in**[/color] x) [color=#008000]**if**[/color](notdigit(x[c])) [color=#008000]**throw**[/color] [color=#BA2121]"Invalid character"[/color][color=#666666];[/color]
    [color=#008000]**return**[/color] [color=#008000]parseInt[/color](x);
}
$([color=#008000]**function**[/color]() {
    $([color=#BA2121]"#submit_user"[/color]).click([color=#008000]**function**[/color]() {
        [color=#008000]**var**[/color] errors [color=#666666]=[/color] [];
        [color=#008000]**var**[/color] username [color=#666666]=[/color] $([color=#BA2121]"#username"[/color]).val();
        [color=#008000]**if**[/color]([color=#666666]![/color]username.length) errors.push([color=#BA2121]"* No username given!"[/color]);
        [color=#008000]**if**[/color]([color=#BA2121]" \t"[/color].indexOf(username[[color=#666666]0[/color]]) [color=#666666]!=[/color] [color=#666666]-[/color][color=#666666]1[/color])
            errors.push([color=#BA2121]"* Username cannot begin with whitespace!"[/color]);
        [color=#008000]**try**[/color] {
            [color=#008000]**var**[/color] age [color=#666666]=[/color] as_int($([color=#BA2121]"#age"[/color]).val());
            [color=#008000]**if**[/color](age [color=#666666]<[/color] [color=#666666]1[/color]) errors.push([color=#BA2121]"* Age cannot be < 1"[/color]);
        } [color=#008000]**catch**[/color](e) {
            errors.push([color=#BA2121]"* Invalid age!"[/color]);
        }
        [color=#008000]**try**[/color] {
            [color=#008000]**var**[/color] id [color=#666666]=[/color] as_int($([color=#BA2121]"#id"[/color]).val());
            [color=#008000]**if**[/color](id [color=#666666]<[/color] [color=#666666]1[/color] [color=#666666]||[/color] id [color=#666666]>[/color] [color=#666666]999999[/color]) errors.push([color=#BA2121]"* Invalid ID range!"[/color]);
        } [color=#008000]**catch**[/color](e) {
            errors.push([color=#BA2121]"* Invalid ID!"[/color]);
        }
        [color=#008000]**if**[/color](errors.length [color=#666666]>[/color] [color=#666666]0[/color]) {
            alert([color=#BA2121]"The following errors occurred:\n\n"[/color] [color=#666666]+[/color] errors.join([color=#BA2121]"\n"[/color]));
        } [color=#008000]**else**[/color] {
            $([color=#BA2121]"#username"[/color]).val([color=#BA2121]""[/color]);
            $([color=#BA2121]"#age"[/color]).val([color=#BA2121]""[/color]);
            $([color=#BA2121]"#id"[/color]).val([color=#BA2121]""[/color]);
            [color=#008000]**var**[/color] x [color=#666666]=[/color] $([color=#BA2121]"<div/>"[/color]);
            x.text([color=#BA2121]"You are "[/color] [color=#666666]+[/color] username [color=#666666]+[/color] [color=#BA2121]", aged "[/color] [color=#666666]+[/color] age [color=#666666]+[/color]
                   [color=#BA2121]" next year you will be "[/color] [color=#666666]+[/color] (age[color=#666666]+[/color][color=#666666]1[/color]) [color=#666666]+[/color] [color=#BA2121]", with user id "[/color] [color=#666666]+[/color]
                   id [color=#666666]+[/color] [color=#BA2121]", the next user is "[/color] [color=#666666]+[/color] (id[color=#666666]+[/color][color=#666666]1[/color]) [color=#666666]+[/color] [color=#BA2121]"."[/color]);
            x.hide();
            $([color=#BA2121]"#output"[/color]).prepend(x);
            x.show([color=#666666]500[/color]);
        }
    });
});
[color=#008000]**</script>**[/color]
[color=#008000]**</head>**[/color]
[color=#008000]**<body>**[/color]
[color=#008000]**<table**[/color] [color=#7D9029]style=[/color][color=#BA2121]"text-align:center; border: 2px dashed black; padding:8px; margin-bottom:8px;"[/color][color=#008000]**>**[/color]
    [color=#008000]**<tr><td>**[/color]Username:[color=#008000]**</td><td><input**[/color] [color=#7D9029]type=[/color][color=#BA2121]"text"[/color] [color=#7D9029]id=[/color][color=#BA2121]"username"[/color][color=#008000]**></td></tr>**[/color]
    [color=#008000]**<tr><td>**[/color]Age:[color=#008000]**</td><td><input**[/color] [color=#7D9029]type=[/color][color=#BA2121]"text"[/color] [color=#7D9029]id=[/color][color=#BA2121]"age"[/color][color=#008000]**></td></tr>**[/color]
    [color=#008000]**<tr><td>**[/color]ID:[color=#008000]**</td><td><input**[/color] [color=#7D9029]type=[/color][color=#BA2121]"text"[/color] [color=#7D9029]id=[/color][color=#BA2121]"id"[/color][color=#008000]**></td></tr>**[/color]
    [color=#008000]**<tr><td**[/color] [color=#7D9029]colspan=[/color][color=#BA2121]"2"[/color][color=#008000]**><button**[/color] [color=#7D9029]id=[/color][color=#BA2121]"submit_user"[/color][color=#008000]**>**[/color]Submit user![color=#008000]**</button></td></tr>**[/color]
[color=#008000]**</table>**[/color]
[color=#008000]**<div**[/color] [color=#7D9029]id=[/color][color=#BA2121]"output"[/color] [color=#7D9029]style=[/color][color=#BA2121]"padding:8px; border: 1px solid black; margin-bottom:8px;"[/color][color=#008000]**></div>**[/color]
[color=#008000]**<p**[/color] [color=#7D9029]style=[/color][color=#BA2121]"text-align:center;"[/color][color=#008000]**>**[/color]
    For more programming challenges, visit
    [color=#008000]**<a**[/color] [color=#7D9029]href=[/color][color=#BA2121]"http://www.challenge-you.com"[/color][color=#008000]**>**[/color]Challenge-You![color=#008000]**</a>**[/color]
[color=#008000]**</p>**[/color]
[color=#008000]**</body>**[/color]
[color=#008000]**</html>**[/color]

```

---

### Post by LaRoza on 2008-08-06
> **Wybiral said:**
> HTML 4.01 Strict


Too many errors ;)

Not valid for the contest.

Remember, a single warning in the compilation phase disqualifies. You had show stopping errors.

---

### Post by ghostdog74 on 2008-08-06
> **arsenic23 said:**
> Thanks, the bash help I had been using never explained the need for "(( ))" when comparing ints.  In fact it had a chart that said that -lt and < where the same thing.  I had tried something like [ $((val < 9)) ] thinking it was something like that and having used $(( stuff )) to do simple math is bash before.  heheh

the advance bash guide is very useful. if you could finish it, it would benefit you alot.

> 
So is there a terribly good reason to use a while loop in this situation?  I really only did it like this because I was interested in seeing if bash would get angry if I had functions call themselves.  I put in incorrect input over and over again to see if it would raise a fuss, but it seemed to work alright.

An infinite loop has the effect of repetition. If input is not valid, you will do it again. recursion has the same effect, however, they have different consequences which i will not elaborate further.
here's my sketch, you can easily understand after reading the links i gave
```

while true
do
 read -p "Enter user name: " username
 username=${username:0:20}  #get 20 characters.
 [ -z "$username" ] && continue
 read -p "Enter age: " age
 [[ "$age" =~ [a-z]+ ]]|| (("$age" <= 0 ))  || (("$age" > 100 ))  && echo "Invalid age" && continue # age 1 onwards?
 read -p "Enter userid: " userid
 ....
 ....
 printf "You entered valid input"
done



```

---

### Post by Wybiral on 2008-08-06
> **LaRoza said:**
> Too many errors ;)

Not valid for the contest.

Remember, a single warning in the compilation phase disqualifies. You had show stopping errors.

It passes this: [http://validator.w3.org/#validate_by_input](http://validator.w3.org/#validate_by_input)

---

### Post by LaRoza on 2008-08-06
> **Wybiral said:**
> It passes this: [http://validator.w3.org/#validate_by_input](http://validator.w3.org/#validate_by_input)

It doesn't pass firebug.

---

### Post by Wybiral on 2008-08-06
> **LaRoza said:**
> It doesn't pass firebug.

It does for me... :(

---

### Post by arsenic23 on 2008-08-06
> **Wybiral said:**
> It does for me... :(

Me too, incase you started thinking you where crazy. 
Works in firefox 3.0.1 and Opera 9.5 on my box.  (64bit)

---

### Post by LaRoza on 2008-08-06
> **Wybiral said:**
> It does for me... :(

Firebug finds things in jquery.js to complain about.

---

### Post by Vishal Agarwal on 2008-08-06
Dear Laroza,
I want to write a shell script for this, But I need some help, regarding shell script commands. Can U pls guide some URL containing good treasure of shell scripting commands.

---

### Post by LaRoza on 2008-08-06
> **Vishal Agarwal said:**
> Dear Laroza,
I want to write a shell script for this, But I need some help, regarding shell script commands. Can U pls guide some URL containing good treasure of shell scripting commands.

The guide posted by ghostdog above, or my wiki.

---

### Post by mcsimon on 2008-08-06
My java version of this :)
```

/**
 * Input manipulation challenge
 * 
 * @author Simon McMahon
 * @version 1.0
 */

import java.util.Scanner;

public class InputChallenge
{
    private static Scanner scan = new Scanner(System.in);
    
    
    
    
    private static String getName() {
        
        String input = "";
        String name = "";
        
		boolean nameLegal = false;
		
		System.out.println("Please enter your username. No leading spaces please. type exit to quit");
		while(!nameLegal) {
		      try {
		          input = scan.nextLine();
		    
		          if(input.equals("") || input.charAt(0) == ' ') {
		               System.out.println("Invalid username. Please enter again. type exit to quit");
		          } else {
		              name = input;
		              nameLegal = true;
		          }
					
		      } catch(Exception e) {
		          System.out.println("Invalid username. Please enter again. type exit to quit");
		      }
		  }
		return name;
    }
    
    private static int getAge() {
		
		boolean ageLegal = false;
		int age = 0;
		String aInput = "";
		System.out.println("Please enter your age. type exit to quit");
		while(!ageLegal) {
		   try {
		          aInput = scan.nextLine();
			
		          if (aInput.toLowerCase().equals("exit")) {
		                  return -1;
		          }
		    
		   
		          if(aInput.equals("") || Integer.parseInt(aInput) < 1) {
		              System.out.println("Invalid age. Please enter again. type exit to quit");
		          } else {
		              age = Integer.parseInt(aInput);
		              ageLegal = true;
		    
		          }    
		    } catch (Exception n) {
		          System.out.println("Invalid age. Please enter again. type exit to quit");
		    }
					
		}
		return age;
    }
    
    
    private static int getID() {
		
		boolean IDLegal = false;
		int ID = 0;
		String dInput = "";
		System.out.println("Please enter your ID number. type exit to quit");
		while(!IDLegal) {
		    try {
		          dInput = scan.nextLine();
			
		          if (dInput.toLowerCase().equals("exit")) {
		              return -1;
		          }
		        
		          if(dInput.equals("") || Integer.parseInt(dInput) < 1) {
		              System.out.println("Invalid user ID. Please enter again. type exit to quit");
		          } else {
		              ID = Integer.parseInt(dInput);
		              IDLegal = true;
		    
		          }    
		    } catch (Exception n) {
		          System.out.println("Invalid user ID. Please enter again. type exit to quit");
		    }
					
		}
		return ID;
    }

    
    public static void main(String[] args) {
        String name = getName();
        if(!name.toLowerCase().equals("exit")) {
            int age = getAge();
            if (age != -1) {
                int ID = getID();
                if (ID != -1) {
                    System.out.print("You are " + name + ", aged " + age);
                    System.out.print(". Next year you will be " + (age + 1));
                    System.out.println(". Your user ID is " + ID + " and the next user will be " + (ID + 1) + ".");
                }
            }
        }
        System.out.println("Thank you for using this program.");
            
    }
}

```

---

### Post by nvteighen on 2008-08-06
I see nobody has tried C yet...

Question to our host, LaRoza:
Are we allowed to use external libs? Or would be too advanced for a "beginner"?

---

### Post by shae on 2008-08-06
My version in C/C++ (First time using C/C++):
[PHP]#include <iostream>
#include <string>
#include <cstring>

using namespace std;

bool no_character(string input)
{
    for (unsigned int i=0; i < input.size(); i++)
        {
            if(isalpha(input[i]))
                return false;
        }
    return true;
}

int main()
{
    string input;
    string name;
    int age;
    int usrid;

    cout << "Welcome to Shae's solution to Programming Challenge 2." << endl;
    cout << "Type exit and press enter to close this program." << endl;

    // While loop to take the input for the name
    while(1)
    {
        cout << "Please type your forum name and press enter: ";
        getline (cin, input, '\n');

        if (input == "exit")
            return 0;
        else if (input.size() == 0)
            cout << "Your forum name cannot be blank, please try again." << endl;
        else if (input[0] == ' ')
            cout << "Your forum name cannot start with a space, please try again." << endl;
        else if (no_character(input))
            cout << "Your forum name must contain a non-numerical character, please try again." << endl;
        else
        {
            name = input;
            break;
        }
    }

    // While loop to take the input for the age
    while(1)
    {
        cout << "Please type your age and press enter: ";
        getline (cin, input, '\n');
        age = atoi(input.c_str());

        if (input == "exit")
            return 0;
        else if (input.size() == 0)
            cout << "Your age cannot be blank, please try again." << endl;
        else if (input[0] == ' ')
            cout << "Your age cannot start with a space, please try again." << endl;
        else if (age < 1 || age > 120)
            cout << "Your age cannot be less than 1, greater than 120, and must be a number, please try again." << endl;
        else
            break;
    }

    // While loop to take the input for the user id
    while(1)
    {
        cout << "Please type your user id and press enter: ";
        getline (cin, input, '\n');
        usrid = atoi(input.c_str());

        if (input == "exit")
            return 0;
        else if (input.size() == 0)
            cout << "Your user id cannot be blank, please try again." << endl;
        else if (input[0] == ' ')
            cout << "Your user id cannot start with a space, please try again." << endl;
        else if (usrid < 1 || usrid > 999999)
            cout << "Your user id cannot be less than 1, greater than 999999, and must be a number, please try again." << endl;
        else
            break;
    }

    cout << "You are " << name << ", aged " << age << " next year you will be " << age + 1 << ", with user id " << usrid << ", the next user is " << usrid + 1 << "." << endl;
    return 0;
}[/PHP]

---

### Post by jimi_hendrix on 2008-08-06
> **LaRoza said:**
> 

You can have one made with a GUI. It has to be free, and let me know what I need to compile it though. Packages should be in Ubuntu repos.

are there any C++/C# IDE's in the repos that allow you to use a GUI to position the components then you just have to add your code to tell them what to do

---

### Post by lordhaworth on 2008-08-06
Ok found it - ignore my comment in the other thread!
Ill hopefully be posting a tested (this time) Fortran90 program soon

Good luck everyone 

Tom

---

### Post by nvteighen on 2008-08-06
**C / GTK+**

Ha, you didn't expect this. Actually, it's kinda cheating, because the high-level data types GLib offers like GString are designed to avoid the usual string problems that were the challenge's goal; so I wouldn't mind if I'm disqualified. But I hope it can be useful for someone, so I also GPL it and post it...

EDIT: Forgot to mention that, as a consequence of using GTK+, this one supports UTF-8.

You need the GTK+ libraries (for those using KDE. GNOME & Xfce users already have it installed) and the GTK+ development packages (libgtk2.0-0 and libgtk2.0-dev).

Compile with:
```

gcc -o challenge challenge.c -Wall `pkg-config --cflags --libs gtk+-2.0`

```

Here, the winner code:
**UPDATES**: 
1) I decided to comment the code so anyone who's curious can see what I'm doing and why.
2) Fixed parsing conditions. Previous version didn't handle negative values correctly.
3) Fixed bug in parsing. It accepted null input as username.
4) A cosmetic change that allows the main button to use the user's native locale.
[PHP]
/* challenge.c - UF Beginner Challenge #2
 *
 * Copyright (C) 2008 Eugenio M. Vigo (aka "nvteighen")
 *
 * This program is free software: you can redistribute it and/or modify it under
 * the terms of the GNU General Public License as published by the Free Software
 * Foundation, either version 3 of the License, or (at your option) any later
 * version.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT 
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS 
 * FOR A PARTICULAR PURPOSE. See the GNU General Public License for more 
 * details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program. If not, see <http://www.gnu.org/licenses/>. */

#include <string.h> /* For strlen() */
#include <stdlib.h> /* For atoi() */
#include <gtk/gtk.h>

#define MSG_STRING "You are %s aged %d you will be %d, with user id %d, the next user is %d."

/** FUNCTION PROTOTYPES:
 ** You should always do this! **/
 
GtkWidget *my_win(void);
GtkWidget *my_entry_with_label(const char *);
void send_cback(GtkWidget *, gpointer *);
void my_print(GtkWindow *, GString *, GString *, GString *);

int parse(const char *, const char *, const char *);

/** INTERFACE FUNCTIONS:
 ** These functions below are responsible of creating the user interface. 
 ** Nothing of the real implementation (data processing) is done here in order 
 ** to show how you can (and should) divide a program into the "stage" (what the 
 ** user sees) and the "backstage" (what the program does). Usually, this 
 ** division would imply to have more than one source file, but as this is a
 ** rather trivial program (compared to major projects like Nautilus), let's
 ** do all in the same file. **/

GtkWidget *my_win(void)
{
    /* Constructor for the main window. All settings for it are set here and 
     * nowhere else.
     *
     * RET: A pointer to the window widget. */

    GtkWidget *Window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_default_size(GTK_WINDOW(Window), 400, 300);
    gtk_window_set_title(GTK_WINDOW(Window), 
        "Beginner Programming Challenge 2");
    
    gtk_container_set_border_width(GTK_CONTAINER(Window), 23); 
    
    /* Assigning callback to the "delete_event" (user closing window). */
    g_signal_connect(G_OBJECT(Window), "delete_event", gtk_main_quit, NULL);
    
    return Window;
}

GtkWidget *my_entry_with_label(const char *label)
{
    /* Constructor for text entries; it takes a string as argument for label.
     *
     * RET: A pointer to the new text entry. */
    
    GtkWidget *NewEntry = gtk_entry_new();
    gtk_entry_set_text(GTK_ENTRY(NewEntry), label);
    
    return NewEntry;
}

void send_cback(GtkWidget *Send, gpointer *data)
{
    /* What's this? GTK+ works using callbacks, a sort of wrapper activated by
     * an event that prepares the data for further processing. All callbacks
     * have the same argument structure: first argument is the widget and then,
     * a gpointer to the data, in this case, a gpointer to a gpointer (i.e an 
     * array of gpointers... isn't C great?). 
     *
     * RET: (void). */

    /* We take advantage of GLib's GString data type to store the user's input.
     * The input is taken from the entries, whose addresses are stored in the
     * data array indices 0-2. */
    GString *ForumName = g_string_new(gtk_entry_get_text(GTK_ENTRY(data[0])));
    GString *Age = g_string_new(gtk_entry_get_text(GTK_ENTRY(data[1])));
    GString *ForumID = g_string_new(gtk_entry_get_text(GTK_ENTRY(data[2])));
    
    /* The GString data type allows direct access to the string from the 'str'
     * data member. */
    if(parse(ForumName->str, Age->str, ForumID->str) == 0)
    {
        /* If all data meets the criteria at parse(), then we can display the
         * sentence. */
        my_print(GTK_WINDOW(data[4]), ForumName, Age, ForumID);
    }
    else
    {
        /* If something failed, we display an error dialog box. */
        GtkWidget *Err = gtk_message_dialog_new(GTK_WINDOW(data[4]), 
            GTK_DIALOG_MODAL, GTK_MESSAGE_ERROR, GTK_BUTTONS_OK, 
            "Are you sure?");
        
        /* We have to give the "response" signal (when user presses the button)
         * a result: destroy the dialog box. */
        g_signal_connect(G_OBJECT(Err), "response", 
            G_CALLBACK(gtk_widget_destroy), NULL);
        
        /* Show the dialog. gtk_widget_show() could also be used. */
        gtk_dialog_run(GTK_DIALOG(Err));
    }
    
    /* Free memory allocated for the GStrings. The second argument queries to 
     * also free internal data too. */
    g_string_free(ForumName, TRUE);
    g_string_free(Age, TRUE);
    g_string_free(ForumID, TRUE);
}

void my_print(GtkWindow *parent, GString *ForumName, GString *Age, 
    GString *ForumID)
{
    /* The display function which outputs the final sentence. The first argument
     * is needed to give the resulting message box a parent window.
     *
     * RET: (void). */
    GtkWidget *MsgBox = gtk_message_dialog_new(parent, GTK_DIALOG_MODAL, 
        GTK_MESSAGE_INFO, GTK_BUTTONS_OK, MSG_STRING, ForumName->str, 
        atoi(Age->str), atoi(Age->str) + 1, atoi(ForumID->str), 
        atoi(ForumID->str) + 1);
    
    /* Define what happens when "response" signal is emitted (destroy the dialog
     * box). */
    g_signal_connect(G_OBJECT(MsgBox), "response", 
        G_CALLBACK(gtk_widget_destroy), MsgBox);
        
    /* Show the dialog. */    
    gtk_dialog_run(GTK_DIALOG(MsgBox));
}

int main(int argc, char **argv)
{
    /* Here we design the main window and give GTK+ the control of the 
     * interface. The command line arguments are needed for GTK+. 
     *
     * RET: always 0. */
    
    /* All GTK+ apps need this. */
    gtk_init(&argc, &argv);

    /* Creating array that will hold all widgets' memory address. */
    gpointer All[5];

    /* Create widgets and set them. */
    GtkWidget *Window = my_win();
    
    GtkWidget *ForumName = my_entry_with_label("Forum Name");
    GtkWidget *Age = my_entry_with_label("Age");
    GtkWidget *ForumID = my_entry_with_label("Forum ID");
    
    GtkWidget *Send = gtk_button_new_from_stock(GTK_STOCK_OK);
    /* Defining what happens if Send is clicked: send_cback() is called and 
     * 'All' serves as data container. */
    g_signal_connect(G_OBJECT(Send), "clicked", G_CALLBACK(send_cback), All);
    
    /* Assign the memory addresses into the array. */
    All[0] = ForumName;
    All[1] = Age;
    All[2] = ForumID;
    All[3] = Send; 
    All[4] = Window;
    
    /* Now, let's pack everything into a vertical box. A for-loop is used to 
     * take advantage of our 'All' array, but we have to stop at i = 3 so 
     * 'Window' is not packaged! */
    GtkWidget *Box = gtk_vbox_new(FALSE, 10); /* 10 pixels between widgets. */
    size_t i;
    for(i = 0; i < 4; i++)
        gtk_box_pack_start(GTK_BOX(Box), All[i], FALSE, FALSE, 0);
    
    /* Now, insert 'Box' into the window. */
    gtk_container_add(GTK_CONTAINER(Window), Box);
    
    /* And, show all children widgets recursively! */
    gtk_widget_show_all(Window);
    
    /* Finally, call the GTK+ main loop, which takes care for the signals and
     * all the stuff behind the scenes. This line is needed in all GTK+ apps. */
    gtk_main();
    
    return 0;
}

/** IMPLEMENTATION FUNCTION:
 ** This function is responsible of data crunching and processing and is
 ** absolutely independent from the interface. As you see, only standard types 
 ** are used, so in theory any possible C program should be able to call this, 
 ** no matter what interface it uses, whether GTK+, ncurses or just plain 
 ** command line. **/

int parse(const char *ForumName, const char *Age, const char *ForumID)
{
    /* This function processes the data according to the criteria given by the
     * challenge.
     *
     * RET: 0 on success. 1 on error. */
     
    int parsed_age = atoi(Age);
    int parsed_ID = atoi(ForumID);
    int error = 0;
    
    /* The C standard function atoi() returns 0 if input is not an integer, 
     * otherwise, it returns the converted integer. In this case, we need to 
     * avoid any negative and zero results. Forum ID also requires to be less 
     * than 99999. If one of these conditions fails, error is set to 1. */
    if(!((parsed_age > 0) && (parsed_ID > 0) && (parsed_ID < 99999)))
        error = 1;
    
    if(strlen(ForumName) == 0)
    	error = 1;
    
    return error;
}
[/PHP]

---

### Post by Reiger on 2008-08-06
Requires the CLI version of PHP (written in 5.x; may not work with older versions because of the shorthand for acquiring STDIN):

[PHP]
<?php

	echo "A short, mildly inquisitive program written for fun. To quit type 'quit' or 'exit' (without the apostrophes/single quotes).\n";
	
	/*
	All the questions & checks in 2 arrays...
	*/
	$questions=array(
			"Could you please give me your Username?",
			"I hope you don't mind, but could you also give me your age?",
			"May I further ask you to provide me your UID? I promise not to misuse it. ;)"
			);
	$checks	  =array(
			'/^\w[\w ]*$/', // This construction ensures no leading whitespace will be allowed, but whitespace itself within the name is...
			'/^[1-9]\d?$/', // This construction prevents you from typing ages <= 0
			'/^\d{1,6}$/' // This construction prevents anyone from entering negative values [the minus character isn't a digit ;)]
			);
	
	function askForInput ($question,$check) {
		$valid=false;
		while($valid==false) {
			echo "$question\n> ";
			$input=fgets(STDIN); // PHP shorthand
			$valid=preg_match($check,$input);
			if(preg_match('/^(qu|ex)it$/',$input))
				forceQuit("Okay, I'll quit now.");
		}
		
		return trim($input);
	}
	
	$data=array();
	foreach($questions as $num => $question) {
		$data[$num]=askForInput($question,$checks[$num]);
		if($num==2 && $data[$num]==0)
			$data[$num]=askForInput($question,$checks[2]);
	}
	
	function forceQuit ($exit) { die("$exit\n"); }
	
	$ouput = "You are '".$data[0]."', aged ".$data[1]." and next year you will be ".($data[1]+1).". Your UID is '".$data[2]."', the next user is '".($data[2]+1)."'.\n";
	
	forceQuit($ouput);
	
	
?>
[/PHP]

Also: does this forum have some kind of spoiler tags? Like [spoil][/spoil] ? For those who don't know: spoiler tags are used to hide, erhm well, 'spoilers'...

EDIT: @LaRoza: you may want to make the assignment a little more clear regarding the following few constraints:
1) Are UID's required to be 6 digits long? I assume not as you said they could be anything from 1 thru 99999, still ...
2) At one point you require people to be able to 'quit' the next time it's 'exit'. Which are the valid killer commands? Both, the former or the latter? (I assumed both.)

---

### Post by TreeFinger on 2008-08-06
can age be a float or only integers??

---

### Post by drubin on 2008-08-06
> **Wybiral said:**
> It does for me... :(

Firebugs version have been a bit off since the change from 2.* to 3.* at one point at work i had to down grade to 2.0.14 of firefox to get errors to show up on firebug. 

Give him a second chance. :)

---

### Post by drubin on 2008-08-06
> **Reiger said:**
> Requires the CLI version of PHP (written in 5.x; may not work with older versions because of the shorthand for acquiring STDIN):

1) Are UID's required to be 6 digits long? I assume not as you said they could be anything from 1 thru 99999, still ...

is 0000002 a valid forum Id? and is it different to 2

---

### Post by LaRoza on 2008-08-06
> **nvteighen said:**
> I see nobody has tried C yet...

Question to our host, LaRoza:
Are we allowed to use external libs? Or would be too advanced for a "beginner"?

You can, although I would appreciate having instructions on what I need to do to get it to work.

> **shae said:**
> My version in C/C++ (First time using C/C++):


That is C++, not C.

> **jimi_hendrix said:**
> are there any C++/C# IDE's in the repos that allow you to use a GUI to position the components then you just have to add your code to tell them what to do
This is new, C++/C#. See the sticky for GUI development. C# has Monodevelop.

> **Reiger said:**
> 
Also: does this forum have some kind of spoiler tags? Like [spoil][/spoil] ? For those who don't know: spoiler tags are used to hide, erhm well, 'spoilers'...

No.

> 
EDIT: @LaRoza: you may want to make the assignment a little more clear regarding the following few constraints:
1) Are UID's required to be 6 digits long? I assume not as you said they could be anything from 1 thru 99999, still ...
2) At one point you require people to be able to 'quit' the next time it's 'exit'. Which are the valid killer commands? Both, the former or the latter? (I assumed both.)

If I wanted leading zero's, I would have stated 000001 to 999999. Also, the forum doesn't use leading zero's (I am going by forum ID's when formulating the input)

It should be obvious what the command is when I run the program, so it doesn't matter.

> **TreeFinger said:**
> can age be a float or only integers??
Integer.

> **rubinboy said:**
> is 0000002 a valid forum Id? and is it different to 2
I just checked the forum, and leading zeros are ignored, so I guess it is valid.

---

### Post by TreeFinger on 2008-08-06
[php]

class ForumUser:

	def __init__(self):
		print "Welcome, new forum user! We must set up your account."
		print "To exit the setup at anytime, simply type 'exit' (excluding quotations)."

		self.name = ""
		self.age = -1
		self.user = -1

		self.__set_all()

		self.to_string()

	def __set_all(self):
		print "The first step is to set your user name.\n"
		self.set_name()

		print "Next, please enter your age.\n"
		self.set_age()

		print "Finally, enter your user ID.\n"
		self.set_user()

	def set_name(self):
		print "Forum Name must have at least 1 character, may not begin with a space and cannot be 'exit', 'Exit', etc.\n"
		name_ok = False
		while name_ok == False:
			self.name = raw_input("Enter Desired Name: ")
			self.__y_n_exit(self.name)

			if self.name == "":
				print "I told you, your name must be at least 1 character long!\n"
				continue
			if self.name[0] == " ":
				print "I told you, space as first character is not allowed!\n"
				continue
			else:
				name_ok = True
				print "Your user name is: %s \n " % self.name

	def set_age(self):
		print "Your age must be a number greater than 0, although I have a feeling you are much older than 1!\n"
		age_ok = False
		while age_ok == False:
			self.age = raw_input("Enter Your Age: ")
			self.__y_n_exit(self.age)

			self.age = self.__string_to_int(self.age)

			if self.age == 'error': 
				continue
			elif self.age < 1:
				print "You aren't that young! Enter your real age!\n"
				continue
			elif self.age > 199:
				print "I don't think anyone is that old! Enter your real age!\n"
				continue
			else:
				age_ok = True
				print "Your age is: %d" % self.age

	def set_user(self):
		print "Your user ID must be greater than 0 and less than 999999\n"
		userid_ok = False
		while userid_ok == False:
			self.user = raw_input("Enter Your ID: ")
			self.__y_n_exit(self.user)

			self.user = self.__string_to_int(self.user)

			if self.user == 'error':
				continue
			elif self.user < 1:
				print "ID Must be greater than 0!\n"
				continue
			elif self.user > 999999:
				print "ID Must be less than 1000000!\n"
				continue
			else:
				userid_ok = True
				print "Your ID is: %d" % self.user

	def to_string(self):
		if self.user != 999999:
			print "You are %s, aged %d, with user id %d. Next year you will be %d and the next user id is %d" % (self.name, self.age, self.user, self.age+1, self.user+1)
		else:
			print "You are %s, aged %d, with user id %d. Next year you will be %d and there can be no next user!" % (self.name, self.age, self.user, self.age+1)

	def __string_to_int(self, string):
		try:
			return int(string)
		except ValueError:
			print "I don't think you entered a normal number! Try Again."
			return 'error'

	def __y_n_exit(self, string):
		if string.lower() == 'exit':
			print "\nYou have decided to exit, come back soon!"
			quit()

user = ForumUser()
[/php]

---

### Post by Bachstelze on 2008-08-06
Quick Python version, I'll work on a C one after dinner :p

```
#!/usr/bin/env python
#coding: utf-8

import sys

class User(object) :

    def __init__(self) :
        self.__username = ""
        self.__uid = 0
        self.__age = 0

        print "Okay, I'm going to ask you a few details about yourself."
        print "Remember that at any prompt, you may type \"exit\" to quit."

    def testInputForExit(self, input) :
        if input == "exit" :
            print "Good bye!"
            sys.exit(0)


    def promptUsername(self) :
        print "\nPlease enter your username and press Enter."
        while True :
            username = raw_input()
            self.testInputForExit(username)
            username=username.strip()

            if username != "" :
                self.__username = username
                break

            print "Error. Your username must contain at least one non-space character."


    def promptAge(self) :
        print "\nNow, please enter your age."
        while True :
            age = raw_input()
            self.testInputForExit(age)

            try :
                age = int(age)
                assert age >= 0 and age <= 130
            except ValueError :
                print "Error. You must enter an integer."
            except AssertionError :
                print "Error. You must enter a stricly positive integer no greater than 130."
            else :
                self.__age = age
                break

    def promptUid(self) :
        print "\nAlmost there! Now, please enter your user ID."
        while True :
            uid = raw_input()
            self.testInputForExit(uid)

            try :
                uid = int(uid)
                assert uid > 0
            except ValueError :
                print "Error. You must enter an integer."
            except AssertionError :
                print "Error. You must enter a strictly positive integer."
            else :
                self.__uid = uid
                break

    def printString(self) :
        print "You are %s, aged %s next year you will be %s, with user id %s, the next user is %s." % \
                (self.__username, self.__age, self.__age + 1, self.__uid, self.__uid +1)

if __name__ == "__main__" :
    user = User()
    user.promptUsername()
    user.promptAge()
    user.promptUid()
    user.printString()
```

---

### Post by Titan8990 on 2008-08-06
Alright, starting off. I am aware that it better practice to use OPP instead of global variables but this is the way that I wanted to do it for my own personal learning experience. I'm happy with the end result:

[php]#!/usr/bin/python

import sys

name = 0
age = 0
uid = 0

def getname():
	global name
	name = raw_input(str("What is your name? "))
	if name == "exit":
		sys.exit()		
	if name[0] == " ":
		print "\nPlease do not start your name with a space.\n\nTry again.\n"
		getname()
	try:
		name = str(name)
	except:
		print "\nAre you sure thats your name?\n\nTry again.\n"
		getname()
	
def getage():
	global age
	age = raw_input("How old are you? ")
	
	if age == "exit":
		sys.exit()
	
	try:
		age = int(age)
	except:
		print "\nYour age needs to be an integer.\n\nTry again.\n"
		getage()
	if age > 100:
		print "\nThats too old.\n\n Try again.\n"
		getage()
	elif age <= 0:
		print "\nYou must be older than that.\n\nTry again.\n"
		getage()
		

def getuid():
	global uid
	uid = raw_input("What is your forum user id? ")

	if uid == "exit":
		sys.exit()
	
	try:
		uid = int(uid)
	except: 
		print "\nUser IDs should be in the form of integers\n"
		getuid()
	if uid < 1:
		print "\nThe user ID you have entered is invalid.\n\nTry again.\n"
		getuid()
	elif uid > 999999:
		print "\nThe user ID you have entered in invalid.\n\nTry again.\n"
		getuid()		


def main():

	print "\n\nPlease answer the following questions.\n\n You can type exit at any time to quit.\n"
	getname()
	getage()
	getuid()

	nextyear = age + 1
	nextuid = uid + 1

	print "\n\nYou are %s, aged %s next year you will be %s, with user id %s, the next user is %s.\n" % (name, age, nextyear, uid, nextuid)

	raw_input("Press the enter key to exit.\n")

main()[/php]

---

### Post by wtfnomorenames on 2008-08-06
After a few hours of me banging my head against anything that was in close proximity, reading through man page after man page, and wasting even a few more hours trying to figure out why fflush() wasn't working on stdin, I think I finally have some working code here.

It was compiled using gcc 4.2.3 on Linux 2.6.24-19.

[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <assert.h>
#include <ctype.h>

#define NAME_LEN 21
#define BUF_SIZE 21

#define AGE_MIN 10
#define AGE_MAX 100

#define ID_MIN 1
#define ID_MAX 999999

#define QUIT_STRING "exit"

void get_string(char* prompt, char* string, unsigned int string_length)
{
  char buffer[BUF_SIZE];
  char c;

  printf("%s", prompt);

  /* Read in BUF_SIZE characters from standard input and store it in buffer. */
  fgets(buffer, BUF_SIZE, stdin);

  /* If the user types "exit" at any point, then that's what we need to do. */
  if (strncmp(buffer, QUIT_STRING, strlen(QUIT_STRING)) == 0)
    exit(EXIT_SUCCESS);

  /* This code could use some explaining. What happens when you type in a
     string longer than the buffer is that it copies over the length of the
     buffer, but leaves the rest of what was entered still in the input queue.
     For most compilers, fflush() is only designed for output buffers, and
     using it on input buffers has an unknown effect. (However, I believe that
     MS VC++'s version of fflush may be used on stdin.) What this code does is
     (1) checks to see if our local buffer string is full, and (2) if this is
     the case, then that means we have some "overflow" still in the stdin
     queue. The while loop then reads in the rest of the unwanted characters
     from the queue and discards them, so we won't have problems when we try
     and read new user input in the future. */
  if (strlen(buffer) >= BUF_SIZE - 1)
    while ((c = fgetc(stdin)) && c != '\n');

  /* Copies our local copy to the string whose address was passed in. This
     only copies up to string_length characters. */
  strncpy(string, buffer, string_length);
}

void get_username(char* prompt, char* string, unsigned int string_length)
{
  char username[BUF_SIZE];
  int hasChars = 0;
  int i;

  do {
    get_string(prompt, username, BUF_SIZE);

    if (username[0] == ' ') {
      printf("Sorry, your username cannot begin with a space.\n");
      continue;
    }

    /* This scans the string to see if there is at least one character (as
       opposed to all numbers) in the string. In addition, it gets rid of the
       newline character which is kept on from the fgets() function called in
       the get_string function. */
    for (i = 0; i < BUF_SIZE; i++) {
      if (username[i] == '\n'){
	username[i] = '\0';
	break;
      }

      if (isalpha(username[i])) {
	hasChars = 1;
      }
    }

    if (! hasChars)
      printf("Sorry, your username must contain at least 1 character.\n");

  } while ((! hasChars) || username[0] == ' ');

  strncpy(string, username, string_length);
}

unsigned int get_number(char* prompt, unsigned int min, unsigned int max)
{
  char input_string[BUF_SIZE];

  unsigned int number = 0;

  do {
    printf("%s (%d-%d): ", prompt, min, max);
    get_string("", input_string, BUF_SIZE);
    
    /* Converts the string representation of the number to an actual integer
       stored value. */
    number = (unsigned int)atoi(input_string);

    /* atoi will return 0 if an error has occured, so we must check the first
       character to see if it is actually a 0, or if atoi just returned with an
       error. */
    if (number == 0 && input_string[0] != '0') {
      printf("That wasn't a number. Please try again.\n");
      continue;
    }
  } while (number < min || number > max);

  return number;
}

int main(int argc, char* argv[])
{
  char name[NAME_LEN]; name[0] = '\0';
  unsigned int age, id;

  /* We want to make sure that the quit string can actually fit inside the
     buffer. Otherwise, all hell may break lose. */
  assert(strlen(QUIT_STRING) < BUF_SIZE);

  printf("Type '%s' at any time to quit.\n\n", QUIT_STRING);

  /* Retrieve and validate all input */
  age = get_number("Please enter your age", AGE_MIN, AGE_MAX);
  id = get_number("Please enter your user id", ID_MIN, ID_MAX);
  get_username("Please enter your forum name: ", name, NAME_LEN);
  
  /* Output the final results */
  printf("You are %s, aged %d next year you will be %d, with user id %d, the next user is %d.\n", name, age, age+1, id, id+1);

  /* We are home at last! */
  return EXIT_SUCCESS;
}[/PHP]

EDIT: I changed the CODE tags to PHP tags, so the code is easier on your eyes, even though the OCD side of me is making me twitch because it's labeled something that it's not.

---

### Post by LaRoza on 2008-08-06
@wtfnomorenames

It prints "Sorry, your username must contain at least 1 character." every time. Please fix it, I'd hate to have your code disqualified for such a minor detail :-)

---

### Post by wtfnomorenames on 2008-08-06
> **LaRoza said:**
> @wtfnomorenames

It prints "Sorry, your username must contain at least 1 character." every time. Please fix it, I'd hate to have your code disqualified for such a minor detail :-)

Wow, thanks for that! I restructured some things, and didn't even notice that. I corrected it in my post above.

---

### Post by Bachstelze on 2008-08-06
@LaRoza : not sure if we may comment on other users' code here. If not, feel free to delete this.

@Titan8990 : okay, a few comments:

1) "Shebang" line. You should use [font="Courier New"]#!/usr/bin/env python[/font] instead of [font="Courier New"]#!/usr/bin/python[/font], because Python is not always intalled at [font="Courier New"]/usr/bin/python[/font]. For example, if I tried to execute your script on my FreeBSD system, it would not start, because Python is intalled at [font="Courier New"]/usr/local/bin/python[/font]. On the other hand, [font="Courier New"]#!/usr/bin/env python[/font] is a nice way to make sure your script runs on all platforms (see [here](http://www.velocityreviews.com/forums/showpost.php?p=1736854&postcount=2) if you want to know why).

2) Global variables. You really shouldn't use them, and you can avoid it without needing to use OOP, just pass the variables you need to be modified as arguments to your function, and use the return values, like :

[PHP]
age = 0
    
def getage(oldage):
    age = raw_input("How old are you? ")
    
    if age == "exit":
        sys.exit()
    
    try:
        age = int(age)
    except:
        print "\nYour age needs to be an integer.\n\nTry again.\n"
        getage()
    if age > 100:
        print "\nThats too old.\n\n Try again.\n"
        getage()
    elif age <= 0:
        print "\nYou must be older than that.\n\nTry again.\n"
        getage()

    return age

def main(age):

    print "\n\nPlease answer the following questions.\n\n You can type exit at any time to quit.\n"
    age = getage(age)
    nextyear = age + 1

    print "\n\nYou are aged %s next year you will be %s." % (age, nextyear)

    raw_input("Press the enter key to exit.\n")

main(age)[/PHP]

3) Recursivity. It is absolutely not needed here, as it doesn't make your code any more readable, and could lead to problems if you have some fool of a user who keeps entering invalid data, due to the enormous amount of function calls in your stack that would create. It would be better to use a [font="Courier New"]while[/font] loop to keep prompting until a valid value is entered without making additional function calls.

4) [font="Courier New"]str(x)[/font] when [font="Courier New"]x[/font] is a string (you're not the only one who've done that one, though). What the heck? If [font="Courier New"]x[/font] is a string, [font="Courier New"]str(x)[/font] will simply return [font="Courier New"]x[/font], there is absolutely no point in doing this (and even more so in trying to make it raise an exception) when you're certain it is the case.

5) [font="Courier New"]name = 0[/font]. Setting an initial value for a parameter that is not of the correct type for it (0 is an illegal name, as it is not a string) should be avoided, as it might confuse people who read your code and might want to reuse it.

---

### Post by linkmaster03 on 2008-08-06
Should we let usernames contain spaces as long as it does not begin with a space?

---

### Post by LaRoza on 2008-08-06
> **wtfnomorenames said:**
> Wow, thanks for that! I restructured some things, and didn't even notice that. I corrected it in my post above.

I'll test it out. It works well, definately one of the top ten assuming we don't get a bunch of C guru's here :-)

> **HymnToLife said:**
> @LaRoza : not sure if we may comment on other users' code here. If not, feel free to delete this.

Why not. It is all about learning.

> 
1) "Shebang" line.

Just to let others know, I copy and paste code to run it, but I will run it with the appropriate interpreter even if it isn't specified or specified correctly.


> **linkmaster03 said:**
> Should we let usernames contain spaces as long as it does not begin with a space?
User names can contain spaces, but as long as the program doesn't break when it is entered (even if it doesn't record the name in full) it is Ok. Using spaces will be a possible tie breaker if it comes down to that.

---

### Post by kk0sse54 on 2008-08-06
First program ever written with python :) these threads are an awesome idea
[PHP]#! /usr/bin/python

import sys
resp = raw_input("What is your forum name (Type quit to exit)? ")
if resp == "quit":
    print "Goodbye"
    sys.exit()
else:
    print "Thank You"

resp1 = raw_input("What is your age (Type quit to exit)? ")
if resp1 == "quit":
    print "Goodbye"
    exit()
else:
    resp1 = int(resp1)
    if resp1 < 1:
        print "That is not a valid age, Goodbye"
        exit()
    else:
        if resp1 > 999999:
            print "That is not a valid age,Goodbye"
            exit()
        else:
            print "Thank You"

resp2 = raw_input("What is your forum ID (Type quit to exit)? ")
if resp2 == "quit":
    print "Goodbye"
    exit()
else:
    resp2 = int(resp2)
    if resp2 < 1:
        print "That is not a valid forum ID, Goodbye"
        exit()
    else:
        if resp2 > 999999:
            print "That is not a valid forum ID, Goodbye"
            exit()
        else:
            print "Thank You"

print "You are %s, aged %s next year you will be %s, with user id %s, the next user is %s." % (resp, resp1,resp1 + 1, resp2, resp2 +1)[/PHP]

---

### Post by Bachstelze on 2008-08-06
C!oud, you trust users too much ;) As LaRoza wrote in the first post : **"No matter what you ask in a program, expect the user to give random input or nothing at all."**, and your program will crash if the users enters anything that is not an integer when prompted for his age or UID. So it is very important that your program can handle such cases. Read some of the programs above to get an idea of how this is done, and [this](http://docs.python.org/tut/node10.html) for an in-depth explanation.

---

### Post by kk0sse54 on 2008-08-06
Good point didn't see that coming ](*,) thanks HymnToLife :)

---

### Post by shae on 2008-08-06
> **LaRoza said:**
> 
That is C++, not C.


I figured I should specify that I used C also in my C++ application to convert string to integer (hence the #include <cstring> and use of atoi()).

---

### Post by LaRoza on 2008-08-06
> **shae said:**
> I figured I should specify that I used C also in my C++ application to convert string to integer (hence the #include <cstring> and use of atoi()).

That is still C++. It doesn't conform to any C standard, and no C compiler will compile it.

---

### Post by Bodsda on 2008-08-06
Do we get points for program layout/formatting? (the output not the code)

---

### Post by scourge on 2008-08-06
Started off great, but then I got really annoyed and just finished the thing code-monkey style so I could go on with my life.

It's in C.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>


static char *getline(void)
{
	char *str;
	int bufsize;
	int i;
	int c;
	
	bufsize = 4;
	str = malloc(bufsize);
	if (str == NULL) {
		fprintf(stderr, "Out of memory\n");
		exit(EXIT_FAILURE);
	}
	
	i = 0;
	while (1) {
		c = fgetc(stdin);
		if (i >= bufsize) {
			bufsize *= 2;
			str = realloc(str, bufsize);
			if (str == NULL) {
				fprintf(stderr, "Out of memory\n");
				exit(EXIT_FAILURE);
			}
		}
		if (c == '\n' || c == '\r' || c == EOF) {
			str[i] = '\0';
			break;
		}
		str[i] = (char)c;
		i++;
	}

	return str;
}

static int is_valid_name(char *name)
{
	if (name == NULL)
		return 0;
	if (strlen(name) <= 0)
		return 0;
	if (isspace(name[0]))
		return 0;
	
	return 1;
}

static char *get_forum_name(int *exit)
{
	char *input;

	while (1) {
		printf("Forum name: ");

		input = getline();
		if (strcmp(input, "exit") == 0) {
			*exit = 1;
			free(input);
			return NULL;
		}
		
		if (is_valid_name(input))
			break;
		free(input);
	}
	
	return input;
}

static int is_valid_age(int age)
{
	if (age <= 0)
		return 0;
	return 1;
}

static int get_age(int *exit)
{
	char *input;
	int age = 0;

	while (1) {
		printf("Age: ");

		input = getline();
		if (strcmp(input, "exit") == 0) {
			*exit = 1;
			free(input);
			return 0;
		}
		
		age = atoi(input);
		if (is_valid_age(age))
			break;
		free(input);
	}
	
	free(input);
	return age;
}

static int is_valid_user_id(int user_id)
{
	if (user_id <= 0 || user_id > 999999)
		return 0;
	return 1;
}

static int get_user_id(int *exit)
{
	char *input;
	int user_id = 0;

	while (1) {
		printf("User id: ");

		input = getline();
		if (strcmp(input, "exit") == 0) {
			*exit = 1;
			free(input);
			return 0;
		}
		
		user_id = atoi(input);
		if (is_valid_user_id(user_id))
			break;
		free(input);
	}
	
	free(input);
	return user_id;
}

int main(void)
{
	char *name;
	int age;
	int user_id = 0;
	int exit = 0;
	
	printf("Identify yourself! Or type 'exit' any time to exit the program\n\n");
	
	name = get_forum_name(&exit);
	if (exit)
		return 0;

	age = get_age(&exit);
	if (exit)
		return 0;
	
	user_id = get_user_id(&exit);
	if (exit)
		return 0;
	
	printf("You are %s, aged %d next year you will be %d, with user id %d, the next user is %d.\n",
	       name, age, age + 1, user_id, user_id + 1);
	free(name);
	
	return 0;
}

```

---

### Post by linkmaster03 on 2008-08-06
I really liked this one! I learned how to handle exceptions, and a lot of string testing. :) My version, in Python:

[php]#!/usr/bin/env python
# userinfo.py
#User Info Gatherer by LinkMaster03
import sys
name,age,id,valid,namestr,agestr,idstr="","","","Please enter a valid","username.\n(Only letters,\
 numbers, spaces, and underscores. Must have, and start and end with, atleast one letter or\
 number.)","age. (integer 5-130)","forum ID. Click on your Ubuntuforums profile, and the number\
 after the = is your forum ID. (integer 1-999999)"
print "\nType exit or quit at any prompt to leave!"
def getName():
    try:
        name=raw_input("What is your username? ")
        name=name.strip()
        if len(name)<1 or len(name)>20: 
            print "Invalid username length, please enter a name with 1-20 characters."
            name=""
        elif name=="exit" or name=="quit": 
            sys.exit()
        elif name[0]==("_"):
            print valid,namestr
            name=""
        elif not name.replace(" ","").replace("_","").isalnum():
            print valid,namestr
            name=""
        else:
            pass
        return name
    except (TypeError, ValueError, AttributeError):
        print valid,namestr
        name=""
def getAge():
    try:
        age=raw_input("Thanks! Can I have your age? ")
        age=age.strip(" _")
        age=age.replace(" ","")
        if age=="exit" or age=="quit": sys.exit()
        age=int(age)
        if age<5 or age>130:
            print valid,agestr
            age=""
        else: 
            pass
        return age
    except (TypeError, ValueError, AttributeError):
        print valid,agestr
        age=""
def getID():
    try:
        id=raw_input("Great! Will you tell me your forum ID? ")
        id=id.strip(" _")
        id=id.replace(" ","")
        if id=="exit" or id=="quit": sys.exit()
        id=int(id)
        if id<1 or id>999999:
            print valid,idstr
            id=""
        else: 
            pass
        return id
    except (TypeError, ValueError, AttributeError):
        print valid,idstr
        id=""
while not name:
    name=getName()
while not age:
    age=getAge()
while not id:
    id=getID()
print "Your username is %s. You are %s years old, and you will be turning %s on your next birthday!\
 Your Ubuntuforums user ID is %s, and the ID of the person who registered after you is %s. Your profile is at\
 http://ubuntuforums.org/member.php?u=%s." % (name,age,age+1,id,id+1,id)
[/php]

---

### Post by jimi_hendrix on 2008-08-06
time for my overly long C# version that i probably wasted way to much time on

i added a menu and i allow the user to load/save profiles

[PHP]using System;
using System.Collections.Generic;
using System.Text;
using System.IO;

namespace User_Input
{
    class Program
    {
        static void Main(string[] args)
        {
            //variables we will use
            bool keepGoing = true; //this keeps our while loop going
            string name = ""; //this is your name
            int age = 0; //your age
            int nextAge = age + 1; //the age you will be next year
            long uID = 0; //your id
            long nextUID = uID + 1; //the next person's id
            bool loaded = false;//we will use this at the start to make sure the user creates or loads a profile

            //asks if the user wants to load or make a new profile
            Console.WriteLine("Type load to load a profile or anything else to create a new one");
            string answer = Console.ReadLine();//set answer to the input by user
 
            if (answer.ToLower() == "load")//here is where we load the profile
            {                              //we use the ToLower method to make sure that if the user types Load, lOAD, LOAD or any combination of capitals and lower case will be valid
                
                while (loaded == false)//makes sure the person wants to load a file                   
                {
                    Console.WriteLine("what is the name of the profile you want to load?");

                    try//this will attempt to seach for a user file
                    {
                        StreamReader sr = new StreamReader(Console.ReadLine());//creates a Stream Reader to read the file
                        name = sr.ReadLine();//reads the first line of the file and sets name to it
                        age = Convert.ToInt32(sr.ReadLine());//reads the second line of the file sets age to it
                        uID = Convert.ToInt32(sr.ReadLine());//reads the third line of the file and sets uID to it
                        Console.WriteLine();//these lines print out the user info
                        Console.WriteLine(name);
                        Console.WriteLine(age);
                        Console.WriteLine(uID);
                        sr.Close();//closes the stream reader without this the program will still be accessing the stream even after its close
                        loaded = true;
                    }
                    catch (FileNotFoundException)//error handling
                    {   string reload;
                        Console.WriteLine("ERROR NO PROFILE WITH THAT NAME EXISTS!!!");
                        Console.WriteLine("do you want to load again? Type yes to try again or any thing else to create a new profile");
                        reload = Console.ReadLine();
                        if (reload.ToLower() != "load")
                        {
                            loaded = true;
                        }
                    }
                 }
             }

            

             while(loaded == false)//if the user chooses to load they create a new profile here
             {
                Console.WriteLine("What is your name?");//this is all basic question and answer with the user
                name = Console.ReadLine();
                Console.WriteLine("What is your age?");
                try
                {
                    age = Convert.ToInt32(Console.ReadLine());
                    nextAge = age + 1;
                }
                catch (FormatException)
                {
                    Console.WriteLine("you have entered invalid input please finish filling out the data and then re enter it");
                }
                Console.WriteLine("What is your user id?");
                try
                {
                    uID = Convert.ToInt32(Console.ReadLine());
                    nextUID = uID + 1;
                }
                catch (FormatException)
                {
                    Console.WriteLine("you have entered invalid input please finish filling out the data and then re enter it");
                }
                if (age <= 0 | uID <= 0)//error handling
                {
                    Console.WriteLine("you have entered invalid data for your age or id");
                }

                else//everything is created correctly so we can exit
                {
                    loaded = true;
                }
             }            

            while (keepGoing == true)//the guts of the program start here
            {
                Console.WriteLine("Your name is: {0}", name);//display user data
                Console.WriteLine("Your age is {0}, next year you will be {1} years old", age, nextAge);
                Console.WriteLine("Your user ID is {0}, next year you will be {1}", uID, nextUID);
                Console.WriteLine();
                Console.WriteLine();

                int choice = Menu();//display menu and get user choice
                
                switch (choice)//act depending on choice
                {
                    case 0://display info again
                        Console.WriteLine("Your name is: {0}", name);
                        Console.WriteLine("Your age is {0}, next year you will be {1} years old", age, nextAge);
                        Console.WriteLine("Your user ID is {0}, next year you will be {1}", uID, nextUID);
                        Console.WriteLine();
                        Console.WriteLine();
                        break;
                    case 1://change name
                        try
                        {
                            name = nameChange();
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 2://change age
                        try
                        {
                            age = ageChange();
                            nextAge = age + 1;
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 3://change id
                        try
                        {
                            uID = idChange();
                            uID = nextUID + 1;
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 4://save
                        try
                        {
                        StreamWriter sw = new StreamWriter(name);//here we save the user data to a file with the same name as the user
                        sw.WriteLine(name);
                        sw.WriteLine(Convert.ToString(age));
                        sw.WriteLine(Convert.ToString(uID));
                        sw.Close();
                        Console.WriteLine("saved");
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 5://load
                        Console.WriteLine("what is the name of the profile you want to load?");

                        try
                        {
                            StreamReader sr = new StreamReader(Console.ReadLine());//here we load the data line by line
                            name = sr.ReadLine();
                            age = Convert.ToInt32(sr.ReadLine());
                            uID = Convert.ToInt32(sr.ReadLine());
                            Console.WriteLine(name);
                            Console.WriteLine(age);
                            Console.WriteLine(uID);
                            nextAge = age + 1;
                            nextUID = uID + 1;
                            sr.Close();
                        }
                        catch (FileNotFoundException)//error handling for no files or invalid data
                        {
                            Console.WriteLine("ERROR NO PROFILE WITH THAT NAME EXISTS!!!");
                        }
                        
                        break;
                    case 6://exit
                        return;
                        
                }
            }
        }

        static int Menu()// method to display the menu and get the user choice
        {
            int input = 0;
           
            Console.WriteLine("What would you like to do now?");
            Console.WriteLine("[0]: Enter 0 to print your info to screen again");
            Console.WriteLine("[1]: Enter 1 to change your name");
            Console.WriteLine("[2]: Enter 2 to change your age");
            Console.WriteLine("[3]: Enter 3 to change your id");
            Console.WriteLine("[4]: Enter 4 to save your profile");
            Console.WriteLine("[5]: Enter 5 to load a profile");
            Console.WriteLine("[6]: Enter 6 to exit");
            try
            {
                input = Convert.ToInt32(Console.ReadLine());
            }
            catch(FormatException)//error handling
            {
                Console.WriteLine("INVALID INPUT");
            }
            return input;
        }

        static string nameChange()//method to change the user name
        {
            string newName;
            Console.WriteLine("What would you like to change it to?:");
            newName = Console.ReadLine();
            return newName;
        }

        static int ageChange()//method to change the age
        {
            int nAge;
            Console.WriteLine("What would you like to change it to?:");
            nAge = Convert.ToInt32(Console.ReadLine());
            return nAge;
        }
         
        static int idChange()//method to change the id
        {
            int nID;
            Console.WriteLine("What would you like to change it to?:");
            nID = Convert.ToInt32(Console.ReadLine());
            return nID;
        }
    }

}[/PHP]

also i am not sure if this is portable for i wrote it on my vista side (i was going to use mono but it did even compile the C# code it starts you with for me)

please tell me if this works on your linux side with your compiler or if it doesnt

i would appreciate it if someone would compile and test this before friday

---

### Post by shae on 2008-08-06
> **LaRoza said:**
> That is still C++. It doesn't conform to any C standard, and no C compiler will compile it.

I am sorry for the dragging this out further, but I was always under the impression that you should differentiate between C, C++, and C/C++.

Furthermore, I updated my code to include checking for characters in the name (because the first time I read it I thought you just meant that it was not empty ](*,))

Edit: After some digging, apparently C++ includes the C library so I suppose the differentiation is moot.

---

### Post by wtfnomorenames on 2008-08-06
I forgot to put in a message explaining how to exit, so I've added that line in.

LaRoza: Is ease of extensibility (i.e. being able to easily alter some parts of the program without having to go all over the place changing things) considered at all?

---

### Post by LaRoza on 2008-08-06
> **wtfnomorenames said:**
> I forgot to put in a message explaining how to exit, so I've added that line in.

LaRoza: Is ease of extensibility (i.e. being able to easily alter some parts of the program without having to go all over the place changing things) considered at all?

The first thing I test is it does what it is supposed to do.

Then I test various inputs to see if it can be broken (blank, non numerals, 0, negatives, etc)

This is all before looking at code.

In the last challenge, we had a lot of working code, and I looked at code to narrow it down, and I will do the same here.

In general, one should write clean and logical code. Use structured programming in general also.

---

### Post by LaRoza on 2008-08-06
**Thread will be closed and judged just like last time Friday (unless we have requests to wait). It will be reopened and it will still be active just like other one.**

---

### Post by Bachstelze on 2008-08-06
Are we allowed to make changes to our programs until Friday? I just realized that removing leading and trailing spaces separately is a bit nonsensical...

---

### Post by LaRoza on 2008-08-06
> **HymnToLife said:**
> Are we allowed to make changes to our programs until Friday? I just realized that removing leading and trailing spaces separately is a bit nonsensical...

Sure, you can edit as much as you want (I judge thread backwards, so if I see multiple entries, I assume last one (first one I see) is the final)

---

### Post by ibuclaw on 2008-08-06
Hello all.

Thought I might throw in a blast from the past.
[PHP]
000001 identification division.
000002 program-id. userinput.
000003 environment division.
000004 data division.
000005 working-storage section.
000006 01  forum-name   picture is X(20).
000007 01  your-age     picture is Z(2)9.
000008 01  num-age      picture is 9(3).
000009 01  next-age     picture is Z(3)9.
000010 01  forum-id     picture is 9(6).
000011 01  next-id      picture is Z9(6).
000012 01  user-input   picture is X(20).
000013 01  num-level    picture is 9 value is 0.
000014
000015 procedure division.
000016 input-name.
000017    display "What is your forum name?: " no advancing.
000018    accept user-input.
000019    perform check-input.
000020    move user-input to forum-name.
000021    add 1 to num-level.
000022    perform input-age.
000023
000024 input-age.
000025    display "What is your age?: " no advancing.
000026    accept user-input.
000027    move user-input to num-age.
000028    perform check-input.
000029    add 1 to num-level.
000030    perform input-id.
000031
000032 input-id.
000033    display "What is your forum ID?: " no advancing.
000034    accept user-input.
000035    move user-input to forum-id.
000036    perform check-input.
000037    perform compute-results.
000038
000039 compute-results.
000040    compute your-age = num-age.
000041    compute next-age = num-age + 1.
000042    compute next-id = forum-id + 1.
000043    inspect your-age replacing leading space by low-values.
000044    inspect next-age replacing leading space by low-values.
000045    inspect next-id replacing leading space by low-values.
000046    display "You are " forum-name ". Aged " your-age
000047            ", next year you will be " next-age
000048            ". With user ID #" forum-id
000049            ", the next user is #" next-id ".".
000050    stop run.
000051
000052 check-input.
000053    inspect user-input replacing leading space by low-values.
000054    inspect user-input replacing trailing space by low-values.
000055    if user-input(1:4) = "exit"
000056       stop run.
000057    if user-input = low-values
000058       perform back-a-level.
000059    if user-input(1:1) = "0"
000060       perform back-a-level.
000061 
000062 back-a-level.
000063    evaluate num-level
000064       when '0' go to input-name
000065       when '1' go to input-age
000066       when '2' go to input-id
000067    end-evaluate.

[/PHP]
This may work with hardy's compiler, but I use Intrepid's version myself.
```
sudo apt-get install open-cobol
```
or append the "**-t intrepid**" if you are tied to that repo.

And to compile, run:
```
cobc -x -o foo foo.cbl
```

Regards
Iain

---

### Post by OutOfReach on 2008-08-06
Ok here's mine written in Python, had a little trouble with it, but managed to get it working. Any feedback would be appreciated! :)

[PHP]#!/usr/bin/env python

import string

class userInfo(object):
    
    print "***At any time, you can type 'quit' (without the quotes) to exit the program.***"
    
    def UserName(self):
        self.supportedChars = list(string.letters+string.digits)
        try:
            self.userName = raw_input("Please enter your forum user name: ")
            #Check if the person typed in something invalid.
            if self.userName == "" or self.userName.isspace() or type(self.userName) != str or self.userName.startswith(" ") or self.userName.endswith(" "):
                print "ERROR: Invalid input."
                UserInfo.UserName()
            elif type(self.userName) == str:
                if self.userName.lower() == "quit":
                    print "Goodbye."
                    exit(1)
                else:
                    #Check the string for invalid entries, e.x. #$@__-=, stuff like that...
                    for chars in self.userName.lower():
                        if chars not in self.supportedChars:
                            print "ERROR: Invalid character/s."
                            UserInfo.UserName()
                            break
                    else:
                        #If we don't find anything wrong, goto the next prompt.
                        UserInfo.UserAge()
        except (ValueError, IndexError), e:
            print "ERROR: %s" % e
            UserInfo.UserName()
            
                    
    def UserAge(self):
        try:
            self.userAge = raw_input("Now enter your current age: ")
            if self.userAge.lower() == "quit":
                print "Goodbye."
                exit(1)
            self.userAge = int(self.userAge)
            if 5 < self.userAge < 100:
                UserInfo.UserID()
            else:
                print "ERROR: Your age seems too be unrealistic."
                UserInfo.UserAge()
        except (ValueError, IndexError), e:
            print "ERROR: %s" % e
            UserInfo.UserAge()
    def UserID(self):
        try:
            self.userID = raw_input("Enter your forum ID: ")
            if self.userID == "quit":
                print "Goodbye."
                exit(1)
            self.userID = int(self.userID)
            if 0 < self.userID < 999999:
                UserInfo.FinalOutput()
            else:
                print "ERROR: Invalid forum User ID."
                UserInfo.UserID()
        except (ValueError,IndexError), e:
            print "ERROR: %s" % e
            UserInfo.UserID()
    
    def FinalOutput(self):
        print "You are %s, aged %i next year you will be %i with the user id %i, the next user is %i." % (self.userName, self.userAge, self.userAge + 1, self.userID, self.userID + 1)
                    
                    
if __name__ == "__main__":
    UserInfo = userInfo()
    UserInfo.UserName()
[/PHP]

---

### Post by ghostdog74 on 2008-08-06
> **OutOfReach said:**
> 
    def UserName(self):
        self.supportedChars = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z','0','1','2','3','4','5','6','7','8','9']
        try:

you could use 
```

import string
supported=list(string.letters+string.digits)

```

---

### Post by schauerlich on 2008-08-06
> **ghostdog74 said:**
> you could use 
```

import string
supported=list(string.letters+string.digits)

```

Or $VAR_NAME.isalnum()

---

### Post by OutOfReach on 2008-08-06
Wow I knew about the string module but not string.letters/digits, :P I guess we learn something new everyday, eh? Thanks.

---

### Post by ghostdog74 on 2008-08-06
> **EDavidBurg said:**
> Or $VAR_NAME.isalnum()

???

---

### Post by schauerlich on 2008-08-06
> **ghostdog74 said:**
> ???

From the article LaRoza linked to in the first post:

[quote=Saving Users From Themselves]
It happens that all string objects in Python have built-in methods which make this quite painless. Type these lines in at the '>>>' prompt:

>>>input = '9'
>>>input.isdigit()
1

This will return a '1' (true), so you can easily use it in an 'if' statement as a condition. Some other handy attributes of this kind are:

s.isalnum() returns true if all characters in s are alphanumeric, false otherwise.
s.isalpha() returns true if all characters in s are alphabetic, false otherwise.
[/quote]

---

### Post by ghostdog74 on 2008-08-06
> **EDavidBurg said:**
> From the article LaRoza linked to in the first post:

I see. yes, isalnum, isalpha, isdigit all can be put to good use. Also the coder should take note that if characters such as # can be used in the username, then using isalnum() to check it will give you False.

---

### Post by Def13b on 2008-08-06
My attempt. Didn't want to use Try, Except though I think it might of been easier if I did. Didn't test it as thoroughly as I probably should of either but I think I covered all bases.
[PHP]#!/usr/bin/env python

import sys

def name(input):
    if not input or input[0] == ' ':
        return False
    return True

def num(input, info):
    if input.isdigit():
        if input[0] not in ('0', '-'):
            if info == 'age' and int(input) > 130:
                return False
            return True

def input_data(info):
    options = {'age': '\nPlease enter your age: ',
               'name': '\nPlease enter your forum name: ',
               'fuid': '\nPlease enter your forum user ID: '}
    result = ''
    while not result:
        result = raw_input(options[info])
        if result.lower() == 'quit':
            print '\nExiting Program, Goodbye'
            sys.exit()
        if (info == 'age' or info == 'fuid') and num(result, info):
            return result
        if info == 'name' and name(result):
            return result
        result = ''
        print 'Invalid entry, please try again'


print "Welcome to the info gatherer. \
Type 'quit' at any prompt to exit the program"

name = input_data('name').strip()
age = input_data('age').strip()
fuid = input_data('fuid').strip()

print '\nYou are %s, aged %s, next year you will be %s, with user id \
%s the next user is %s' % (name, age, int(age)+1, fuid, int(fuid)+1)[/PHP]

---

### Post by cprofitt on 2008-08-06
Here is my code... after much procrastination (read: several months) I am starting to take Python seriously... I have been told that this code is not very Pythonic... but I do believe it works properly.

```

#!/usr/bin/env python

#  challeng2.py
#       A program to handle text and numeric input
#  by PrivateVoid

import sys

sError = "there was an error in your entry please re-enter"
sBlank = "your entry was blank please re-enter"



def test(n):
        if n > 0 and n < 1000000 and n % 1 == 0:
                return True
        else:
                return False

def __exit__(s):
        if s == "exit":
                sys.exit(0)

def blank(r):
        if len(r) == 0:
                return True
        else:
                return False


def age():
        aInput = raw_input("how old are you? (must be an integer between 1 and 999999) ")
        try:
                __exit__(aInput)
                if blank(aInput):
                        print sBlank
                        return age()
                elif not test(int(aInput)):
                        print "your entry was not an integer between 1 and 999999 please re-enter"
                        return age()
                print aInput
                return int(aInput)
        except ValueError:
                print sError
                age()

def name():
        aName = raw_input("please enter your name (your name can not begin with a space) ")
        try:
                __exit__(aName)
                bName = aName.lstrip(' ')
                if len(aName) > len(bName):
                        print "your entry started with a space please re-enter"
                        return name()
                elif blank(aName):
                        print sBlank
                        return name()
                return aName                
        except ValueError:
                print sError
                name()

def forumid():
        aID = raw_input("please enter your forum ID (must be an integer between 1 and 999999) ")
        try:
                __exit__(aID)
                if not test(int(aID)):
                        print "your entry was not an integer between 1 and 999999 please re-enter"
                        return forumid()
                elif blank(aID):
                        print sBlank
                        return forumid()
                return int(aID)
        except ValueError:
               print sError
               forumid()

def main():
        print "To leave the program please just type 'exit' at any prompt"
        sName = name()
        sAge = age()
        sID = forumid()
        print "You are ", sName, " aged ", sAge, "next year you will be ", sAge+1, ", with user id ", sID, "the next user is ", sID+1, "."

main()

```

tools used - IDLE

can not wait for a critique and to see the other entries.

---

### Post by ghostdog74 on 2008-08-06
> **PrivateVoid said:**
> ```

def blank(r):
        if len(r) == 0:
                return True
        else:
                return False

```

to check for blank, there's no need to check for length
```

>>> s=""
>>> not s
True
>>> if not s:
...  print "null"
...
null

```
> **PrivateVoid said:**
> 
```

def name():
        aName = raw_input("please enter your name (your name can not begin with a space) ")
        try:
                __exit__(aName)
                bName = aName.lstrip(' ')
                if len(aName) > len(bName):
                        print "your entry started with a space please re-enter"
....
[code]

to check starting with space, you can use startswith()
[code]
>>> s=" username"
>>> s.startswith(" ")
True

```

---

### Post by Bachstelze on 2008-08-07
Okay, here's my C version. Though it might seem a bit overkill, I used a separate header file for the sake of good practice.

**challenge2.h**
[PHP]
#ifndef CHALLENGE_2
#define CHALLENGE_2

#define MAX_AGE 130
#define MAX_UID 9999999
#define MAX_USERNAME_LENGTH 20

void initUser       (void);
void promptName     (void);
void promptAge      (void);
void promptUid      (void);
void printString    (void);
void destroyUser    (void);

#endif
[/PHP]

**challenge2.c**
[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include "challenge2.h"

/* The macros below are a little preprocessor trick to allow usage of other macro
 * values as string constants.
 * For more information, see:  http://gcc.gnu.org/onlinedocs/cpp/Stringification.html
 */

#define xstr(s) str(s)
#define str(s) #s


static char*    name;
static int      age;
static int      uid;

void initUser(void)
{
    //First, we initialize the variables
    name = (char*) calloc(MAX_USERNAME_LENGTH + 1, sizeof(char));
    age = 0;
    uid = 0;

    //Nice greeting message...
    printf("Okay, I'm going to ask you a few details about yourself.\n");
    printf("Remember that at any prompt, you may type \"exit\" to quit.\n\n");

    //And we prompt for the values
    promptName();
    promptAge();
    promptUid();
}


void testInputForExit(char* input)
{
    if(!strcmp(input, "exit"))
    {
        printf("Good bye!\n");
        exit(0);
    }
}


void cleanBuffer(void)
{
    /*  This is used to clean the buffer after every input, in order to avoid
     *  potential buffer overflow issues, as well not to pollute further inputs.
     */
    int c;
    while(((c = getchar()) != '\n') && c != EOF)
    {;}
}


int toInt(char* input, int max_value)
{
    /*  This function is used to check whether or not the string given as input
     *  is "convertible" to an integer. Unlike atoi() and friends, this requires
     *  _all_ the characters in the string to be digits. Since the minus sign is
     *  not allowed, only positive integers are. Additionally, this function also
     *  checks whether the converted integer is smaller than max_value.
     *
     *  This functions returns the converted positive integer on success.
     *  On failure, it returns -1 if the input was not a positive integer, and
     *  -2 if it exceeded the limit.
     */

    unsigned i = 0;
    while(i < strlen(input))
    {
        if(!isdigit(input[i]))
            return -1;
        i++;
    }

    return (atoi(input) > max_value) ? -2 : atoi(input);
}

char* prompt(unsigned maxStringLength)
{
    char* buffer = calloc(maxStringLength + 1, sizeof(char));
    unsigned i;

    /*  This is where the xstr macro comes into play. It allows us to always have
     *  a maximum input length sufficient to contain all the values, but no more
     *  (for the sake of simplicity, we assume that MAX_USERNAME_LENGTH will always
     *  be the longest one. Who needs twenty-digits ages anyway?).
     */
    scanf(" %" xstr(MAX_USERNAME_LENGTH) "[^\n]", buffer);
    cleanBuffer();

    //Remove trailing spaces (if any)
    for(i = strlen(buffer) - 1; i >= 0; i--)
    {
        if(isspace(buffer[i]))
            buffer[i] = '\0';
        else if(isgraph(buffer[i]))
            break;
    }

    testInputForExit(buffer);
    return buffer;
}


void promptName(void)
{
    printf("Please enter your username and press Enter.\n");
    char* tmp = prompt(MAX_USERNAME_LENGTH);
    memccpy(name, tmp, '\0', MAX_USERNAME_LENGTH);
    free(tmp);
}


void promptAge(void)
{
    printf("Now, please enter your age.\n");
    while(1)
    {
        char* tmp = prompt(MAX_USERNAME_LENGTH);
        if((age = toInt(tmp, MAX_AGE)) < 1)
        {
            if(age >= -1)
                printf("Error. Please enter a strictly positive integer.\n");
            else
                printf("Error. Please enter an integer lower than %u.\n", MAX_AGE);
        }
        else
            break;
    }
    free(tmp);
}


void promptUid(void)
{
    printf("Almost there! Now, please enter your user ID.\n");
    while(1)
    {
        char* tmp = prompt(MAX_USERNAME_LENGTH);
        if((uid = toInt(tmp, MAX_UID)) < 1)
        {
            if(uid >= -1)
                printf("Error. Please enter a strictly positive integer.\n");
            else
                printf("Error. Please enter an integer lower than %u.\n", MAX_UID);
        }
        else
            break;
    }
    free(tmp);
}


void printString(void)
{
    printf("You are %s, aged %d next year you will be %d, with user id %u the next user is %u.\n",
            name, age, age+1, uid, uid+1);
}


void destroyUser(void)
{
    printf("Good bye, %s!\n", name);
    free(name);
}


int main(void)
{
    initUser();
    printString();
    destroyUser();
    return 0;
}


[/PHP]

Place in the same directory and compile with

```
cc -o challenge2 challenge2.c
```

---

### Post by PandaGoat on 2008-08-07
My first attempt at using (common? maybe?) lisp.  I tried it with scbl and clisp interpreters, and it worked.  By the way it messed up with php tags, so I used code.
```
 
(defun check-name-nil (name)
  (if (STRING-EQUAL name "") t nil))

(defun check-name-start-space (name)
  (if (STRING-EQUAL (subseq name 0 1) " ") t nil))

(defun check-name-not-contains-char (name)
  (loop for c across name
     do (if (alpha-char-p c) (return-from check-name-not-contains-char nil) ()))
  t)


(defun get-name ()
  (loop
     do (format t "Whats be yo tag yo: ") (finish-output)
       (let ((name (read-line t)))
	 (if (STRING-EQUAL name "exit") (quit)
	     (if (check-name-nil name) (format t "Yuz ain't nosbody~%")  
		 (if (check-name-start-space name) (format t "Yuz tag gotta start wit a character yo~%")
		     (if (check-name-not-contains-char name) (format t "Yo i didn' ask fo yuz digits~%") (return-from get-name name))))))))



(defun get-age ()
  (loop
       do (format t "How old bez yo: ") (finish-output)
       (let ((age (read)))
	 (if (typep age 'REAL)
	     (if (<= age 0) (format t "Howz yuz typin' from da womb?~%") 
		 (if (>= age 120) (format t "Howz yuz not dead?~%") (return-from get-age age))) 	 
	     (if (STRING-EQUAL age "exit") (quit) (format t "Yuz age needzta be a numba~%"))))))
  


(defun get-id ()
  (loop
     do (format t "Whats yuz forum numba: ") (finish-output)
       (let ((id (read)))
	 (if (typep id 'REAL)
	     (if (<= id 0) (format t "No onez got dis forum numba~%") 
		 (if (> id 999999) (format t "No onez got dis forum numba~%") (return-from get-id id)))
	     (if (STRING-EQUAL id "exit") (quit) (format t "Yuz forum numba needzta be a numba~%"))))))


(defun main ()
  (format t "Follow da prompts or enta exit anywhere to exit~2%")
  (let ((name (get-name)) (age (get-age)) (id (get-id)))
    (format t "You are ~A, aged ~A next year you will be ~A, with user id ~A, the next user is ~A." name age (+ age 1) id (+ id 1))))


(main)

```

---

### Post by artoj on 2008-08-07
C++ again. I tried to abstract the validation of things as much as possible. This was good practice for using templates too.

[PHP]
#include <vector>
#include <string>
#include <iterator>
#include <iostream>
#include <sstream>

class ValidatorPolicy
{
	public:
		ValidatorPolicy() { }
		virtual ~ValidatorPolicy() { }
		
		virtual bool validate(int value) const = 0;
		virtual bool validate(const std::string& value) const = 0;

};

class FullPolicy : public ValidatorPolicy
{
	public:
		FullPolicy() { }
		virtual ~FullPolicy() { }

		virtual bool validate(int value) const { return true; }
		virtual bool validate(const std::string& value) const { return true; }

};

class RangePolicy : public FullPolicy
{
	public:
		RangePolicy(int min, int max)
		{
			m_min = min;
			m_max = max;
		}
		~RangePolicy() { }

		bool validate(int value) const
		{
			if (value > m_min && value < m_max)
			{
				return true;
			}

			return false;
		}

	private:
		int m_min;
		int m_max;

};

class NamePolicy : public FullPolicy
{
	public:
		NamePolicy() { }
		~NamePolicy() { }

		bool validate(const std::string& value) const
		{
			if (value[0] == ' ' || value.empty())
				return false;

			return true;
		}

};

template <typename T> class Validator
{
	public:
		Validator() { }
		~Validator()
		{
			while (!m_policies.empty())
			{
				delete m_policies.back();
				m_policies.pop_back();
			}
		}

		void addPolicy(ValidatorPolicy* policy)
		{
			m_policies.push_back(policy);
		}

		bool validateAll(const T& value)
		{
			std::vector<ValidatorPolicy*>::iterator i;
			for (i = m_policies.begin(); i != m_policies.end(); ++i)
			{
				if (!isValid((*i), value))
					return false;
			}

			return true;
		}

		bool isValid(ValidatorPolicy* policy, const T& value)
		{
			return policy->validate(value);
		}
	
	private:
		std::vector<ValidatorPolicy*> m_policies;	
};

class Application
{
	public:
		Application() { }
		virtual ~Application() { }

		virtual int exec() = 0;

};

class ValidatorApplication : public Application
{
	public:
		ValidatorApplication()
		{
			m_nameValidator.addPolicy(new NamePolicy());
			m_ageValidator.addPolicy(new RangePolicy(5, 120));
			m_forumIdValidator.addPolicy(new RangePolicy(0, 99999));
		}

		~ValidatorApplication() { }

		int exec()
		{
			std::cout << "Type your info or \"exit\" to exit."
				<< std::endl << std::endl;

			std::string s;
			
			do
			{
				if (!input("Please input your name: ", s))
				{
					return 0;
				}
				else
				{
					m_name = s;
				}
			}
			while (!m_nameValidator.validateAll(m_name));

			do
			{
				if (!input("Plese input your age: ", s))
				{
					return 0;
				}
				else
				{
					std::istringstream stream(s);
					stream >> m_age;
				}
			}
			while (!m_ageValidator.validateAll(m_age));

			do
			{
				if (!input("Please input your forum id: ", s))
				{
					return 0;
				}
				else
				{
					std::istringstream stream(s);
					stream >> m_forumId;
				}
			}
			while (!m_forumIdValidator.validateAll(m_forumId));

			std::cout << "You're " << m_name << " aged " << m_age << " next ";
			std::cout << "near you'll be " << m_age + 1 << ", with user id ";
			std::cout << m_forumId << ", the next user is " << m_forumId + 1;
			std::cout << std::endl;

			return 0;
		}
	
	private:
		bool input(const std::string& prompt, std::string& command)
		{
			std::cout << prompt;
			getline(std::cin, command);

			if (command == "exit")
				return false;
			
			return true;
		}

		std::string m_name;
		int m_age;
		int m_forumId;
		Validator<std::string> m_nameValidator;
		Validator<int> m_ageValidator;
		Validator<int> m_forumIdValidator;

};

int main(int argc, char* argv[])
{
	ValidatorApplication app;
	return app.exec();
}
[/PHP]

---

### Post by Ed J on 2008-08-07
Now that I'm done I'll look at the other entries.
```
#!/usr/bin/env python

runiftrue = 1
while runiftrue: 
    while 1:    
        try:
            namein = raw_input('Enter your name, press "Enter" when complete. ')
            if len(namein) == 0:
                print 'Not enough characters.'
                continue
            if namein[0] == ' ':
                print "Don't start name with a space."
                continue
            if namein == "quit":
                print 'Goodbye' 
                runiftrue = 0
                break
            if len(namein) > 20:
	        namein = namein[0:19]  
                print 'name truncated'  
            break
        except:
	    print 'Input error, try again.'
            continue

    if runiftrue == 0:
        break

    while 1:    
        try:
            agein = raw_input('Enter your age, press "Enter" when complete. ')
            if len(agein) == 0:
                print 'Not enough characters.'
                continue
            if agein == "quit":
                print 'Goodbye'
	        runiftrue = 0
                break
            if not agein.isdigit():
                print 'Enter a number for your age.'
                continue
            if int(agein) < 1:
                print 'Too low, try again.'
                continue
            break
        except:
	    print 'Input error, try again.'
            continue

    if runiftrue == 0:
        break

    while 1:
        try:
            useridin = raw_input('Enter your Forum User ID, press "Enter" when complete. ')
            if useridin == "quit":
                print 'Goodbye'
	        runiftrue = 0
                break
            if len(useridin) == 0:
                print 'Not enough numbers.'
                continue
            if not useridin.isdigit():
                print 'Enter the number of your Forum User ID.'
                continue
            if int(useridin) > 999999:
                print 'Too high, try again.'
                continue
            if int(useridin) < 1:
                print 'Too low, try again.'
                continue
            if len(useridin) > 20:
	        useridin = useridin[0:19]  
                print 'name truncated'  
            break
        except:
            print 'Input error, try again.'
            continue

    if runiftrue == 0:
        break
    
    print '''You are %s, age %i, next year you will be %i, with user id %i,
        the next user is %i.''' % (namein, int(agein), int(agein)+1,                            
        int(useridin), int(useridin) + 1)
    break
```

---

### Post by Bachstelze on 2008-08-07
Wow, that's a lof of [FONT="Courier New"]if[/FONT]'s ;)

---

### Post by jimi_hendrix on 2008-08-07
just curious...could u compile C with a C++ compiler?

---

### Post by Bachstelze on 2008-08-07
> **jimi_hendrix said:**
> just curious...could u compile C with a C++ compiler?

Why not just try?

```
firas@nobue ~ % cat helloworld.c
#include <stdio.h>

int main(void)
{
    printf("Hello world!\n");
    return 0;
}

firas@nobue ~ % g++ -o helloworld helloworld.c
firas@nobue ~ % ./helloworld
Hello world!

```

---

### Post by Titan8990 on 2008-08-07
> 2) Global variables. You really shouldn't use them, and you can avoid it without needing to use OOP, just pass the variables you need to be modified as arguments to your function, and use the return values, like:

I can't get this to work like that at all. I foolled with code for an extended period of time before I finally got it work with globals. When I saw your post I made another unsuccessful attempt. I then tried to run your example code and it had the same problem as mine:

UnboundLocalError: local variable 'age' referenced before assignment

How do I get around this?

---

### Post by Bachstelze on 2008-08-07
> **Titan8990 said:**
> I then tried to run your example code and it had the same problem as mine:

UnboundLocalError: local variable 'age' referenced before assignment

How do I get around this?

Sorry, my mistake. The parameter [FONT="Courier New"]age[/FONT] should be passed to the [FONT="Courier New"]main[/FONT] function as well (basically, to any function that uses it). I edited my post.



EDIT : here's your whole script without the globals:

[PHP]#!/usr/bin/python            

import sys

name = 0
age = 0 
uid = 0 

def getname():
    name = raw_input(str("What is your name? "))
    if name == "exit":                          
        sys.exit()                              
    if name[0] == " ":                          
        print "\nPlease do not start your name with a space.\n\nTry again.\n"
        getname()                                                            
    try:                                                                     
        name = str(name)                                                     
    except:                                                                  
        print "\nAre you sure thats your name?\n\nTry again.\n"              
        getname()                                                            

    return name
               
def getage():  
    age = raw_input("How old are you? ")
                                        
    if age == "exit":                   
        sys.exit()                      
                                        
    try:                                
        age = int(age)                  
    except:                             
        print "\nYour age needs to be an integer.\n\nTry again.\n"
        getage()                                                  
    if age > 100:                                                 
        print "\nThats too old.\n\n Try again.\n"                 
        getage()                                                  
    elif age <= 0:                                                
        print "\nYou must be older than that.\n\nTry again.\n"    
        getage()                                                  

    return age
              

def getuid():
    uid = raw_input("What is your forum user id? ")

    if uid == "exit":
        sys.exit()   

    try:
        uid = int(uid)
    except:
        print "\nUser IDs should be in the form of integers\n"
        getuid()
    if uid < 1:
        print "\nThe user ID you have entered is invalid.\n\nTry again.\n"
        getuid()
    elif uid > 999999:
        print "\nThe user ID you have entered in invalid.\n\nTry again.\n"
        getuid()

    return uid


def main():

    print "\n\nPlease answer the following questions.\n\n You can type exit at any time to quit.\n"
    name = getname()
    age = getage()
    uid = getuid()

    nextyear = age + 1
    nextuid = uid + 1

    print "\n\nYou are %s, aged %s next year you will be %s, with user id %s, the next user is %s.\n" % (name, age, nextyear, uid, nextuid)

    raw_input("Press the enter key to exit.\n")

main()[/PHP]

As you can see, it is not even necessary to pass anything to the functions, since the old values are not used anyway. The important thing is to have the function return the new value, which will let you catch them when you call the function.

---

### Post by Ed J on 2008-08-07
> **HymnToLife said:**
> Sorry, my mistake. The parameter [FONT="Courier New"]age[/FONT] should be passed to the [FONT="Courier New"]main[/FONT] function as well (basically, to any function that uses it). I edited my post.



EDIT : here's your whole script without the globals:

[PHP#]!/usr/bin/python            

import sys

name = 0
age = 0 
uid = 0 
            

... code removed for the sake of brevity

I made this crash by entering ctrl+Z and enter at the input prompt, space at the name prompt and 565656 at the user id prompt.

---

### Post by Bachstelze on 2008-08-07
> **Ed J said:**
> I made this crash by entering ctrl+Z and enter at the input prompt, space at the name prompt and 565656 at the user id prompt.

I just removed the globals, I didn't correct the code altogether.

---

### Post by Jessehk on 2008-08-07
> **jimi_hendrix said:**
> just curious...could u compile C with a C++ compiler?

For the most part, yes.
There are a few things that C does differently than C++ (especially in the most recent standard: C99) that would not work on a C++ compiler.

A few examples are variable-length arrays, the **long long** type,
function definitions that mean different things:

```

/* A function taking no parameters in C++ */
int foo();

/* A function taking an unknown number of parameters in C */
int foo();

/* Same as the C++ version in C */
int foo( void );

```

Certain headers that are not relevant in C++ (like stdbool.h) and a few others that I don't think are available in most C++ compilers like tgmath.h, and stdint.h.

---

### Post by conehead77 on 2008-08-07
We need some Haskell in this thread:

[PHP]
import Data.Char (isDigit)

main = do
  name <- getName "Whats your name? [type 'quit' to exit] \n"
  if name == "quit" then return() else do
  age <- getNumber "Whats your age? [type 'quit' to exit] \n" 12 120
  if age == "quit" then return() else do
  userID <- getNumber "Whats your userID? [type 'quit' to exit] \n" 0 (2^1000)
  if userID == "quit" then return() else do
  putStrLn $ "You are " ++ name ++ " and your age is " ++ age ++
             ". You will be " ++ succString age ++ " next year.\n" ++
             "Your userID is " ++ userID ++ ". The next userID is " ++ 
             succString userID ++ ".\n"

succString :: String -> String
succString s = init s ++ [succ $ last s]

getName :: String -> IO String
getName s = do
  putStr s
  name <- getLine
  case name of
    "" -> getName "Please enter a name or type 'quit' to exit: \n"
    _  -> return name

getNumber :: String -> Integer -> Integer -> IO String
getNumber s min max = do 
  putStr s
  digits <- getLine
  if digits == "quit" then return "quit" else do
  if all isDigit digits && digits /= []
    then if read digits >= min && read digits <= max
           then return digits
           else getNumber "Please enter a reasonable number! [type 'quit' to exit] \n" min max
    else getNumber "Please enter a valid number! [type 'quit' to exit] \n" min max  
[/PHP]

You cant quit the program and with leading zeros it doesnt look so pretty. Also you can enter "" as name, so its far from perfect.

---

### Post by nvteighen on 2008-08-07
> **conehead77 said:**
> 
you cant quit the program...

:)

---

### Post by conehead77 on 2008-08-07
quit before you entered all data correct that is :)

---

### Post by Bachstelze on 2008-08-07
> **conehead77 said:**
> You cant quit the program

[img]http://icanhascheezburger.files.wordpress.com/2007/07/its-a-trap.jpg[/img]

---

### Post by LaRoza on 2008-08-07
> **HymnToLife said:**
> Wow, that's a lof of [FONT="Courier New"]if[/FONT]'s ;)
It is the most used keyword.

> **jimi_hendrix said:**
> just curious...could u compile C with a C++ compiler?
If the C code is valid C++ code, you can. C++ changes the meaning of a few keywords and C has things that aren't C++, so you shouldn't do that.

---

### Post by cprofitt on 2008-08-07
After some reading and advice from ghostdoq76... this is my second attempt.

```

#!/usr/bin/env python

#  challeng2.py
#       A program to handle text and numeric input
#       Version 2
#  by PrivateVoid

# variables for end statement

import sys

iAge = 0
iForumID = 0
sName = ""

print "To end this program please type 'exit' at any prompt"

def integertest(n):
    if n % 1 == 0:
        return True
    else:
        return False

while int(iAge) < 1:
    try:
        iAge = raw_input("enter your age (must be an integer between 1 and 130) ")
        if iAge == "exit":
            sys.exit(0)
        elif int(iAge) > 130:
            iAge = 0
        elif not integertest(int(iAge)):
            iAge = 0
    except ValueError:
        iAge = 0

while int(iForumID) < 1:
    try:
        iForumID = raw_input("enter your forum id (must be an integer between 1 and 999999) ")
        if iForumID == "exit":
            sys.exit(0)
        elif int(iForumID) > 999999:
            iForumID = 0
        elif not integertest(int(iForumID)):
            iForumID = 0
    except ValueError:
        iForumID = 0

while sName == "":
    try:
        sName = raw_input("enter your forum name (can not begin with a space) ")
        if sName.startswith(" "):
            sName = ""
        elif sName == "exit":
            sys.exit(0)
    except ValueError:
        sName = ""

print "You are ", sName, " aged ", iAge, "next year you will be ", int(iAge)+1, ", with user id ", iForumID, "the next user is ", int(iForumID)+1, "."

```

A little cleaner and much shorter. Thanks dog!

Revised this for some stuff I left out.

---

### Post by ibuclaw on 2008-08-07
> **LaRoza said:**
> It is the most used keyword.

Most useful?

I much prefer **case** or **unless** statements. :)

But that is just me coming from a very C/Perl-ish background...

---

### Post by cprofitt on 2008-08-07
> **tinivole said:**
> Most useful?

I much prefer **case** or **unless** statements. :)

But that is just me coming from a very C/Perl-ish background...

Perhaps I should look at this Perl you speak of.

---

### Post by LaRoza on 2008-08-07
> **tinivole said:**
> Most useful?

I much prefer **case** or **unless** statements. :)

But that is just me coming from a very C/Perl-ish background...
I said "used" and it is. Most code is full of "if"'s. There was a study on it, but I leave that up to google to find.

> **PrivateVoid said:**
> Perhaps I should look at this Perl you speak of.

Look at it? Don't. It is gibberish. However, you can learn to write it...

---

### Post by M_the_C on 2008-08-07
I am still very much a beginner.  I do not expect to win, but just thought it was about time I let other people view my code.  Despite the fact that it is probably very messy.  (All comments welcome.)

I think (hope) that is has met all the requirements.  I will happily *try* to correct it if not.  Enjoy.

Python
```
# Introduction.
print "Hello and Welcome to M_the_C's Fantabulous Forum Doohickey."
print "Type 'quit' or 'exit' to terminate the program at any time."

while True:

  # Ask the user for the required information.
  forumname = ""
  while forumname == "":
    forumname = raw_input("Please type your Forum User Name:  ")
    if forumname == "quit":
      print "Goodbye."
      exit()
    if forumname == "exit":
      print "Goodbye."
      exit()
    if forumname == "":
      "Please enter something."
    else:
      if forumname.startswith(" ") == 0:
        pass
      else:
        print "That is an incorrect answer, please try again."
        forumname = ""
    
  age = "0"
  while age == "0":
    age = raw_input("Please enter your age:  ")
    if age == "quit":
      print "Goodbye."
      exit()
    if age == "exit":
      print "Goodbye."
      exit()
    if age.isdigit() == 1:
      if int(age) < 150:
        if int(age) == 0:
          print "Sorry, you have to be 1 or older to use this program."
        else:
          pass
      else:
        print "Do you really expect me to believe that you are over 150 years old?"
        age = "0"
    else:
      print "That is an incorrect answer, please try again."
      age = "0"

  uid = "0"
  while uid == "0":  
    uid = raw_input("Please enter your User ID:  ")
    if uid == "quit":
      print "Why are you quitting?  You are so near the end."
      exit()
    if uid == "exit":
      print "Why are you quitting?  You are so near the end."
      exit()
    if uid.isdigit() == 1:
      if int(uid) == 0:
        print "There is no User 0, please try again."
      else:
        pass
    else:
      print "That is an incorrect answer, please try again."
      uid = "0"

  #  Create the extra information and format them as strings.
  age1 = int(age) + 1
  age1 = str(age1)
  uid1 = int(uid) + 1
  uid1 = str(uid1)

  #  Create and print the sentance.
  listA =  ["You are ", forumname, ", aged ", age, " next year you will be ", age1, ", with user id ", uid, ", the next user is ", uid1, "."]
  listB = "".join(listA)
  print listB

  b = "a"
  while b == "a":
    #  Ask what to do next.
    a = raw_input("Do you want to do another? y/n:  ") 
    if a == "y":
      print "Restart."
      b = "b"
      pass
    elif a == "n":
      print "Goodbye."
      exit()
    elif a == "quit":
      print "Goodbye."
      exit()
    elif a == "exit":
      print "Goodbye."
      exit()
    else:
      print "Pardon?"
```
EDIT:  Altered because of [this.](http://ubuntuforums.org/showpost.php?p=5549227&postcount=146)

---

### Post by mssever on 2008-08-07
> **tinivole said:**
> I much prefer **case** or **unless** statements.
Ruby has [FONT=Courier New]case[/FONT] and [FONT=Courier New]unless[/FONT] statements, and an [FONT=Courier New]until[/FONT] loop. However, unlike Perl, Ruby code is actually readable. I miss [FONT=Courier New]case[/FONT] and [FONT=Courier New]unless[/FONT] when I write Python (both contribute to code readability), even though Ruby's case statement annoyingly doesn't fall through like PHP's.

---

### Post by ibuclaw on 2008-08-07
Yeah, I was thinking about taking up Ruby as my next language.

And I don't find Perl **that** unreadable either.
Would a fairly indepth knowledge of sed and awk be a reason why? I don't know...

[QUOTE=LaRoza]I said "used" and it is.[/QUOTE]
Ah, sorry. I could sworn it said "useful" a few hours ago...
[QUOTE=LaRoza]Look at it? Don't. It is gibberish.[/QUOTE]
Haha, I see you are a Python Programmer then... :razz:

---

### Post by jimi_hendrix on 2008-08-07
is there a C# ide in the repos that i could use to test to see if my code is compatable?

---

### Post by bobbocanfly on 2008-08-07
> **jimi_hendrix said:**
> is there a C# ide in the repos that i could use to test to see if my code is compatable?

MonoDevelop is the Mono C# IDE. Sounds like it should do.

sudo apt-get install monodevelop

---

### Post by LaRoza on 2008-08-07
> **jimi_hendrix said:**
> is there a C# ide in the repos that i could use to test to see if my code is compatable?

You mean compiler. It doesn't matter what IDE one uses, but what compiler. 

gmcs is the compiler, see the sticky on how to use it.

---

### Post by jimi_hendrix on 2008-08-07
> **LaRoza said:**
> You mean compiler. It doesn't matter what IDE one uses, but what compiler. 

gmcs is the compiler, see the sticky on how to use it.

yes your right...compiler...

---

### Post by jimi_hendrix on 2008-08-07
what time will you close the thread tomarrow

---

### Post by xnevermore on 2008-08-07
Alright, here is my solution in ruby, which is a language I just started to learn, thanks to [why's (poignant) guide to ruby]("http://qa.poignantguide.net"), which is got to be one of the most entertaining programming resources around. It's really a shame that more open source projects don't use ruby, because it's a really powerful, fun, and elegant language. In fact, the reason I chose to learn it over python is that the code looks a hell of a lot more beautiful.

Anyway, here it is:
```

#!/usr/bin/ruby

class Person
  @name, @age, @id = nil
  def setName (name)
    if name.kind_of? String and not name.empty? and name[0] != ' '[0] and name.length < 20
      @name = name.rstrip
    else
      @name = nil
    end
  end
  def setAge (age)
    if age.kind_of? Fixnum and age>0
      @age = age
    else
      @age = nil
    end
  end
  def setId (id)
    if id.kind_of? Fixnum and (1..999999) === id
      @id = id
    else
      @id = nil
    end
  end
  def name
    @name
  end
  def id
    @id
  end
  def age
    @age
  end
end

def xgets
  result = gets.chomp
  if result.upcase == 'EXIT'
    puts "Program terminated"
    exit
  else
    return result
  end
end

person = Person.new
while person.name == nil
  print "Name: ";
  person.setName(xgets)
end
while person.age == nil
  print "Age: "
  person.setAge(xgets.to_i)
end
while person.id == nil
  print "ID: "
  person.setId(xgets.to_i)
end

print "You are #{ person.name }, "
print "aged #{ person.age } next year you will be #{ person.age + 1 }, "
puts "with user id #{ person.id }, the next user is #{ person.id + 1 }."
```

---

### Post by xnevermore on 2008-08-07
Sweet, after looking through this thread I've realized that I'm the only one with a Ruby version! That should earn me some points, right? :p

---

### Post by LaRoza on 2008-08-07
> **jimi_hendrix said:**
> what time will you close the thread tomarrow

Not sure. I'll wait until you are done if you want. If anyone wants me to wait, let me know as soon as possible (on this thread)

> **xnevermore said:**
> Sweet, after looking through this thread I've realized that I'm the only one with a Ruby version! That should earn me some points, right? :p

After finding all that work, I separate them by language, and try to get 10 total. If there are more than 10, I narrow down the language groups (like last time we had a lot of Python and C++, and only a few other languages. I culled the Python and C++ ones to get a top 10, although I think it ended up being only 9)

Being the only one in a language (and it works) means it won't be bumped unless it is really needed (and since I think we have less submissions this time, it will be unlikely to happen)

---

### Post by kk0sse54 on 2008-08-07
Fixed it so it won't crash when not typing in numbers. No award winner but it was still fun making it :grin: Last changes I will be making to it so if someone finds something wrong or a bug I would love to find out but I'll be too busy to re-do any parts
[PHP]#!/usr/bin/env python
#revised version, fixed bug that caused program to crash when user did not enter 
#a number when asked for their Age and Forum ID

import sys

resp1 = raw_input("What is your forum name (Type quit to exit)? ")
while resp1 == "":
        resp1 = raw_input("Please enter your forum name (Type quit to exit)? ")
        if resp1 == "quit":
                print "Goodbye"
                exit()
        else:
                if resp1 == " ":
                        print "Please do not use spaces"
                        exit()
                else:   
                    if resp1 != "":
                        print "That's better"
if resp1 == "quit":
    print "Goodbye"
    exit()
else:
    if resp1 == " ":
        print "Please do not use a space"
        exit()
    else:
        if resp1 != "":
            print "Thank You"

            
resp2 = raw_input("What is your age (Type quit to exit)? ")
while resp2 == "":
        resp2 = raw_input("Please enter either a number or quit in order to exit ")
        if resp2 == "quit":
                print "Goodbye"
                exit()       
if resp2 == "quit":
        print "Goodbye"
        exit()
while resp2:
        try:
            resp2 = int(resp2)
            if resp2 == int(resp2):
                break
        except:
            resp2 = raw_input("Please enter a valid number for your age (Type quit to exit)? ")
            if resp2 == "quit":
                print "Goodbye"
                exit()
            else:
                if resp2 == "":
                   resp2 = raw_input("Please enter a valid number for your age (Type quit to exit)? ")
                   if resp2 == "quit":
                           print "Goodbye"
                           exit() 
if resp2 < 1:
        print "That is not a valid age, Goodbye"
        exit()
else:
        if resp2 > 999999:
            print "That is not a valid age,Goodbye"
            exit()
        else:
            print "Thank You"


resp3 = raw_input("What is your forum ID (Type quit to exit)? ")
while resp3 == "":
        resp3 = raw_input("Please either enter your Forum ID or quit")
        if resp3 == "quit":
                print "Goodbye"
                exit()
if resp3 == "quit":
        print "Goodbye"
        exit()
while resp3:
        try:
            resp3 = int(resp3)
            if resp3 == int(resp3):
                break
        except:
            resp3 = raw_input("Please enter a valid number for your forum ID (Type quit to exit)? ")
            if resp3 == "quit":
                print "Goodbye"
                exit()
            else:
                    if resp3 == "":
                            resp3 = raw_input("Please enter a valid number for your forum ID (Type quit to exit? ")
                            if resp3 == "quit":
                                    print "Goodbye"
                                    exit()                  
if resp3 < 1:
        print "That is not a valid forum ID, Goodbye"
        exit()
else:
        if resp3 > 999999:
            print "That is not a valid forum ID, Goodbye"
            exit()
        else:
            print "Thank You"


print "You are %s, aged %s next year you will be %s, with user id %s, the next user is %s." % (resp1, resp2,resp2 + 1, resp3, resp3 +1)

[/PHP]

---

### Post by jimi_hendrix on 2008-08-07
> After finding all that work, I separate them by language, and try to get 10 total. If there are more than 10, I narrow down the language groups (like last time we had a lot of Python and C++, and only a few other languages. I culled the Python and C++ ones to get a top 10, although I think it ended up being only 9)

Being the only one in a language (and it works) means it won't be bumped unless it is really needed (and since I think we have less submissions this time, it will be unlikely to happen)

i assume that goes the same for my C#?

and thanks for waiting i should be done tomarrow afternoon

---

### Post by LaRoza on 2008-08-07
> **jimi_hendrix said:**
> i assume that goes the same for my C#?

and thanks for waiting i should be done tomarrow afternoon

Yes.

---

### Post by jimi_hendrix on 2008-08-07
ok on my ubuntu side now i followed the sticky instructions and got hello world to print to console using gmcs and mono

now i tried my program and got

```
Cannot open assembly UserInput.cs.

```

any idea?

---

### Post by LaRoza on 2008-08-07
> **jimi_hendrix said:**
> ok on my ubuntu side now i followed the sticky instructions and got hello world to print to console using gmcs and mono

now i tried my program and got

```
Cannot open assembly UserInput.cs.

```

any idea?

I compiled your code with gmcs.

```

gmcs p.cs

```
(File was p.cs) and ran it with:

```

mono p.exe

```

Bad news, it threw an uncaught exception, you might want to fix that.

---

### Post by mssever on 2008-08-07
> **xnevermore said:**
> Alright, here is my solution in ruby, which is a language I just started to learn, thanks to [why's (poignant) guide to ruby]("http://qa.poignantguide.net"), which is got to be one of the most entertaining programming resources around.
I'd rather call that book odd. Seriously, though, Ruby is my favorite language, so I took a special interest in your submission. Unfortunately, unless you fix it before LaRoza closes the contest, it will be disqualified. Here's what happened when I tried running it:
```
Name: mssever
./ruby.rb:6:in `setName': undefined method `start_with?' for "mssever":String (NoMethodError)
    from ./ruby.rb:50
```

EDIT: I have a number of suggestions for how to improve your code, but I'll wait to post them until the contest is finished.

---

### Post by Phenax on 2008-08-07
> **mssever said:**
> I'd rather call that book odd. Seriously, though, Ruby is my favorite language, so I took a special interest in your submission. Unfortunately, unless you fix it before LaRoza closes the contest, it will be disqualified. Here's what happened when I tried running it:
```
Name: mssever
./ruby.rb:6:in `setName': undefined method `start_with?' for "mssever":String (NoMethodError)
    from ./ruby.rb:50
```EDIT: I have a number of suggestions for how to improve your code, but I'll wait to post them until the contest is finished.

Your version just doesn't have an implementation of String.start_with?. Works fine here. But considering the majority of people probably don't have it either, he should probably find another way or make a quick implementation of it in the String class.

---

### Post by mssever on 2008-08-08
> **Phenax said:**
> Your version just doesn't have an implementation of String.start_with?. Works fine here. But considering the majority of people probably don't have it either, he should probably find another way or make a quick implementation of it in the String class.
If xnevermore is using some additional library, there should be an appropriate require statement. If he/she is using some version of Ruby other than the Ubuntu Hardy default (1.8.6), that should be stated, as well--especially since the most likely other version would be a development version.

I'm careful to maintain my Ruby installation in the default state so I can distribute my software without those kinds of problems. So, I use 1.8.6, which is what you get when installing the package [FONT=Courier New]ruby[/FONT].

EDIT: By the way, I assume you meant to say that I don't have [FONT=Courier New]String**#**start_with?[/FONT]. That's an important detail in Ruby. And, this issue can be avoided by something like: ```
if name =~ /^[\s]/ # or /^ / for a stricter interpretation of the rules
```

---

### Post by cacycleworks on 2008-08-08
Arrrrgh for work keeping me so busy! Seeing this got me to at least install nasm and do the requisite hello world program. :) But it's been too long since the last time I wrote assembly and that part of the brain is rusted over, not just rusty! I immediately saw a series of compares with jlt's and jgt's keeping the input within bounds.

Anyhow, thanks for the thread and the fun thoughts.
:D Chris

btw, I loved the bash entry!

---

### Post by xnevermore on 2008-08-08
> **mssever said:**
> If xnevermore is using some additional library, there should be an appropriate require statement. If he/she is using some version of Ruby other than the Ubuntu Hardy default (1.8.6), that should be stated, as well--especially since the most likely other version would be a development version.

Well you're wrong about the additional libraries. Just used the standard one. You're right about the ruby version though (i'm using 1.8.7), but you're wrong about it being a development version (1.8.7 is the latest stable, 1.9 is development).

However, I did adjust my code so it would work with those using OLDER versions of ruby. Not everyone can be a trail-blazer, I guess.

I didn't want people to think I was taking your ideas, though. Even though my first inclination was to use regular expressions, like you suggested, I decided to use another method instead... out of spite! :)

---

### Post by Reiger on 2008-08-08
> **conehead77 said:**
> quit before you entered all data correct that is :)

*But* you should be able (explicitly requested by the contest) to quit at *any* prompt... I guess having more than 1 function defined in your module may make that a bit easier to implement?

---

### Post by bobbocanfly on 2008-08-08
Ahh, didn't know this finished so soon. Was quite tempted to write a client<->server model version, to practise network programming. May quickly hack one together when I get home, just to see if I can do it.

---

### Post by chandru on 2008-08-08
I am only an amateur programmer, but probably not a beginner. Here is my version in mono. Little bit of cheating, since mono handles unicode automatically. Also I ignore leading spaces, but I think all other requirements are handled.


```
using System;

class ForumChallenge {
  static void Main() {
    Console.WriteLine("Type 'exit' at any prompt to exit");

    // Get the data
    // Most of the work is done in the AskandValidate function
    string forumName = AskandValidate("What is your forum name?\n(leading spaces are ignored, all other characters are valid)", 
        new NameValidator<string>());
    int age = AskandValidate("What is your age?\n(must be between 1 and 120 inclusive)", 
        new NumValidator<int>(1, 120));
    int userid = AskandValidate("What is your user id?\n(must be between 1 and 999999 inclusive)", 
        new NumValidator<int>(1, 999999));

    // Write the output
    Console.WriteLine("You are {0}, aged {1}; next year you will be {2}, with user id {3}; the next user is {4}", 
       forumName, age, age + 1, userid, userid + 1);
  }

  // Asks the question
  // Validates the answer using a validator
  static T AskandValidate<T>(string question, IValidator<T> validator) {
    bool validAnswer = false;   // remain in loop until valid answer or an exit request
    string errmsg;              // helpful error message if invalid answer
    T result;                   // the result

    while (!validAnswer) {
      // Ask the question and read the answer
      Console.Write("{0} ", question);
      string answer = Console.ReadLine();

      // do we want out
      if (answer.Trim().ToLower().Equals("exit")) {
        Console.WriteLine("bye");
        System.Environment.Exit(-1);
      }

      // validate the answer
      // if answer is invalid, print an error message
      // otherwise exit the loop and return the value
      validAnswer = validator.Validate(answer.Trim(), out result, out errmsg);
      Console.WriteLine(errmsg);
    }

    return result;
  }
}

// Validator interface
// makes code reusable (hopefully)
interface IValidator<T> {
  // allows use of different validator algorithms for different questions
  // returns true if answer is valid
  // result is the formatted answer
  // errmsg is error message
  bool Validate(string answer, out T result, out string errmsg);
}

// Validate the name
class NameValidator<T> : IValidator<string> {

  // Validation
  // Empty strings are invalid
  // Leading spaces are silently ignored (but can be checked for if necessary)
  public bool Validate(string answer, out string result, out string errmsg) {
    result = "";
    if (String.IsNullOrEmpty(answer)) {
      errmsg = "Name cannot be empty";
      return false;
    }

    errmsg = "";
    result = answer;
    return true;
  }
}

// Validator for numbers
// for now it checks only integers 
// (should be extendable to check floats,doubles etc 
// - probably needs reflection to call the right parse function)
class NumValidator<T> : IValidator<int> {
  private int min, max;

  // We know the value limits
  public NumValidator(int minValue, int maxValue) {
    min = minValue;
    max = maxValue;
  }

  // Validate
  public bool Validate(string answer, out int result, out string errmsg) {
    result = -1;

    // Convert the string to int
    // Handle all exceptions
    try {
      result = Int32.Parse(answer);
    } catch (ArgumentNullException) {
      errmsg = "Number is empty";
      return false;
    } catch (FormatException) {
      errmsg = "Answer is not a number";
      return false;
    } catch (OverflowException) {
      errmsg = "Number is too big to be a valid age";
      return false;
    }

    // Check if number is within limits
    if (result < min || result > max) {
      errmsg = "Number is beyond acceptable limits";
      return false;
    }

    errmsg = "";
    return true;
  }
}
```

---

### Post by jimi_hendrix on 2008-08-08
> Bad news, it threw an uncaught exception, you might want to fix that.

can u say where it was that threw an exception

---

### Post by jimi_hendrix on 2008-08-08
can u hold it till this afternoon so i can fix it (4:00 Eastern Standard Time if you can)

---

### Post by sharma2008 on 2008-08-08
I am also Looking Professional guidlines..

---

### Post by conehead77 on 2008-08-08
> **Reiger said:**
> *But* you should be able (explicitly requested by the contest) to quit at *any* prompt... 
Thats why i mentioned it :)
Anyways, i modified the code to meet this requirement:

[http://ubuntuforums.org/showthread.php?p=5542382#post5542382](http://ubuntuforums.org/showthread.php?p=5542382#post5542382)

---

### Post by LaRoza on 2008-08-08
> **jimi_hendrix said:**
> can u say where it was that threw an exception

I didn't read the code so I can't say where. But what it is the maximum size of the data type for the numerical input?

---

### Post by cprofitt on 2008-08-08
just noticed a lot of entries that made a simple mistake based on the requirements, but not sure if I should point it out... what is the protocol?

---

### Post by Reiger on 2008-08-08
> **conehead77 said:**
> Thats why i mentioned it :)
Anyways, i modified the code to meet this requirement:

[http://ubuntuforums.org/showthread.php?p=5542382#post5542382](http://ubuntuforums.org/showthread.php?p=5542382#post5542382)

Heh for fun and to see if I could do it; I tried a Haskell version as well:

```

module Main where
import Control.Exception
import Data.Char
import System.Exit
import System.IO
import System.IO.Unsafe

-- Print a line, and return subsequent user input.
prompt :: [Char] -> [Char]
prompt x = unsafePerformIO ( (putStr (x ++ "\n> ")) >> getLine )

-- Names aren't allowed to begin with whitespace, thereby removing invalid user input.
userConstraint :: [Char] -> Bool
userConstraint (' ':xs) = False
userConstraint ('\t':xs) = False
userConstraint _       = True

-- Numbers aren't allowed to begin with 0 or -, thereby removing invalid user input.
numericConstraint :: [Char] -> Bool
numericConstraint ('0':xs) = False
numericConstraint xs = all isDigit xs

-- For simple testing purposes: always accepts anything
genericConstraint :: a -> Bool
genericConstraint _  = True

-- Keep asking till valid input was given; special cases "quit" (valid) and "" (invalid) bypass the 'validator'
sanitize :: [Char] -> ([Char] -> Bool) -> [Char] -> [Char]
sanitize "" p m = sanitize (prompt m) p m
sanitize "quit" p m = "quit"
sanitize xx p m
    | p(xx)     = xx
    | otherwise = sanitize (prompt m) p m

-- Ask for input
get :: [Char] -> ([Char] -> Bool) -> [Char]
get ask constraint = sanitize (prompt m) constraint e
                     where
                     m = "Please enter your "++ask++" below:"
                     e = "You (must) have specified a wrong "++ask++"! "++m

-- Ask for input which is hopefully numeric, but maybe not
getMaybeNum :: [Char] -> Maybe Int
getMaybeNum ask = eval (get ask numericConstraint)
                  where
                  eval "quit" = Nothing
                  eval  str   = Just (read str)

-- Ask for a name
getName :: [Char]
getName = get "username" userConstraint

-- Ask for an age
getAge :: Maybe Int
getAge = getMaybeNum "age"

-- Ask for a UID
getUID :: Maybe Int
getUID = getMaybeNum "forum id"

-- Make the program executable; and catch any exception it may throw
main :: IO()
main = do
       hSetBuffering stdout NoBuffering
       x <- Control.Exception.catch run catch22
       putStrLn x
       return ()
       where
       catch22 _ = return "Okay I'll quit now."

-- The Real Main Method: does everything main can't. Such as throwing an exception and not invalidating my contest entry ;)
run :: IO String
run = do
      putStrLn "A simple, mildly inquisitive program. To quit at any time, type 'quit' at the prompt."
      n <- (check    getName )
      a <- (numcheck getAge  )
      u <- (numcheck getUID  )
      return ("You are '"++n++"', aged "++(show a)++" and next year you will be "++(show (1 + a))++". Your forum id is '"++(show u)++"' and the next user is '"++(show (1 + u))++"'.")
      where
      check    "quit"    = exitWith ExitSuccess
      check    str       = return str
      numcheck Nothing   = exitWith ExitSuccess
      numcheck (Just i)  = return i

```

Admittedly not the best Haskell there is; then again Haskell was never my strongest point. Learnt/recalled quite a bit there...

---

### Post by LaRoza on 2008-08-08
> **PrivateVoid said:**
> just noticed a lot of entries that made a simple mistake based on the requirements, but not sure if I should point it out... what is the protocol?

You can point out the mistake if you want. This is the last day/night until review.

---

### Post by mssever on 2008-08-08
> **xnevermore said:**
> Well you're wrong about the additional libraries. Just used the standard one. You're right about the ruby version though (i'm using 1.8.7), but you're wrong about it being a development version (1.8.7 is the latest stable, 1.9 is development).Ruby 1.8.7 is stable, but it's in a development version of Ubuntu (Intrepid). Hardy, the latest stable version of Ubuntu, has 1.8.6.

I think there's a general lesson here that applies to many languages, not just Ruby: Be careful of versions when distributing your code--especially if your development environment includes non-default software or development versions of something. Make sure you're aware of the implications and deal with them in a reasonable way (perhaps coding around the differences, perhaps simply documenting them). Version issues like this came up during the change from Dapper to Edgy. Edgy had done something different with Python (I don't know what it was), but a lot of the newer software suddenly wouldn't run on Dapper--even before Edgy's release.

---

### Post by cprofitt on 2008-08-08
> **LaRoza said:**
> You can point out the mistake if you want. This is the last day/night until review.

Thanks.

Many people are missing the specification:

> 
Typing "exit" should exit the program gracefully.


---

### Post by LaRoza on 2008-08-08
I should point out I will use the standard repos on the current version of Ubuntu (8.04). So make sure your code works on that.

---

### Post by nvteighen on 2008-08-08
> **PrivateVoid said:**
> Thanks.

Many people are missing the specification:
What!?

Mine is a GUI program: you can exit it by closing the window... so it technically always exits gracefully.

---

### Post by LaRoza on 2008-08-08
> **nvteighen said:**
> What!?

Mine is a GUI program: you can exit it by closing the window... so it technically always exits gracefully.

A GUI is different here. The important part is the program has to be exitable without killing it. I was assuming most would be CLI, so the keyword was specified. GUI's have their own methods.

It won't always exit gracefully if it is a GUI.

---

### Post by cprofitt on 2008-08-08
> **nvteighen said:**
> What!?

Mine is a GUI program: you can exit it by closing the window... so it technically always exits gracefully.

Technically the specification doesn't call for a GUI so not sure how that will affect the scoring... but the minor detail is valid for many entries.

---

### Post by conehead77 on 2008-08-08
> **Reiger said:**
> Heh for fun and to see if I could do it; I tried a Haskell version as well:

Admittedly not the best Haskell there is; then again Haskell was never my strongest point. Learnt/recalled quite a bit there...

Wow, i dont understand half of your code. Maybe because i dont know about System/Control (yet).

---

### Post by M_the_C on 2008-08-08
> **PrivateVoid said:**
> Many people are missing the specification:I used 'quit' as it was the first word used.  Should I go back and add exit as well?
> **LaRoza said:**
> The entry "quit" should exit the program at any question.EDIT:  I think I will just to be on the safe side.  Please say if that is incorrect.

---

### Post by LaRoza on 2008-08-08
> **PrivateVoid said:**
> Technically the specification doesn't call for a GUI so not sure how that will affect the scoring... but the minor detail is valid for many entries.

I wasn't expect GUI's (and this is aimed at beginners) so I didn't specify the real goal was to just not require force quitting.

> **M_the_C said:**
> I used 'quit' as it was the first word used.  Should I go back and add exit as well?
It doesn't matter. When I run the program, I should be able to tell.

---

### Post by linkmaster03 on 2008-08-08
I have exit and quit. :) I hope I pass this time and get into the voting.

---

### Post by mssever on 2008-08-08
> **linkmaster03 said:**
> I have exit and quit. :) I hope I pass this time and get into the voting.
The important thing is that the program should tell the user how to exit. (Unless it's a GUI where that's not necessary, provided the program works in a sane manner.)

---

### Post by nvteighen on 2008-08-08
> **LaRoza said:**
> A GUI is different here. The important part is the program has to be exitable without killing it. I was assuming most would be CLI, so the keyword was specified. GUI's have their own methods.

It won't always exit gracefully if it is a GUI.

Thank you. In summary: that the program doesn't get trapped in an infinite loop.

As far as I know, mine is the only GUI-designed... and I think it exits as it should, there's no way out except passing through gtk_main_quit(). Of course, you can kill it, reset the X server in the middle and who knows what can happen.

---

### Post by linkmaster03 on 2008-08-08
I added some comments to help aid my fellow beginners in reading the code:

[php]#!/usr/bin/env python
# userinfo.py
#User Info Gatherer by LinkMaster03
import sys
name,age,id,valid,namestr,agestr,idstr="","","","Please enter a valid","username.\n(Only letters,\
 numbers, spaces, and underscores. Must have, and start and end with, atleast one letter or\
 number.)","age. (integer 5-130)","forum ID. Click on your Ubuntuforums profile, and the number\
 after the = is your forum ID. (integer 1-999999)" #define error messages
print "\nType exit or quit at any prompt to leave!"
def getName():
    try:    #if an exception is thrown in here
        name=raw_input("What is your username? ") #get username
        name=name.strip()
        if len(name)<1 or len(name)>20: 
            print "Invalid username length, please enter a name with 1-20 characters."
            name=""
        elif name=="exit" or name=="quit": #if user wants to quit the program
            sys.exit()
        elif name[0]==("_"): #if name starts with underscore, print error
            print valid,namestr
            name=""
        elif not name.replace(" ","").replace("_","").isalnum(): #if the name is not alphanumeric with spaces and underscores removed
            print valid,namestr
            name=""
        else:
            pass
        return name
    except (TypeError, ValueError, AttributeError):     #handle it here
        print valid,namestr
        name=""
def getAge():
    try:    #if an exception is thrown in here
        age=raw_input("Thanks! Can I have your age? ")
        age=age.strip(" _")
        age=age.replace(" ","") #remove all spaces
        if age=="exit" or age=="quit": sys.exit()
        age=int(age)
        if age<5 or age>130:
            print valid,agestr
            age=""
        else: 
            pass
        return age
    except (TypeError, ValueError, AttributeError):     #handle it here
        print valid,agestr
        age=""
def getID():
    try:
        id=raw_input("Great! Will you tell me your forum ID? ")
        id=id.strip(" _")
        id=id.replace(" ","")
        if id=="exit" or id=="quit": sys.exit()
        id=int(id)
        if id<1 or id>999999:
            print valid,idstr
            id=""
        else: 
            pass
        return id
    except (TypeError, ValueError, AttributeError):
        print valid,idstr
        id=""
while not name:
    name=getName()
while not age:
    age=getAge()
while not id:
    id=getID()
print "Your username is %s. You are %s years old, and you will be turning %s on your next birthday!\
 Your Ubuntuforums user ID is %s, and the ID of the person who registered after you is %s. Your profile is at\
 http://ubuntuforums.org/member.php?u=%s." % (name,age,age+1,id,id+1,id)
[/php]

So this replaces my code on page 6 or 7, whichever it was on.

---

### Post by mssever on 2008-08-08
> **linkmaster03 said:**
> [php]
        elif name[0]==("_"): #if name starts with underscore, print error
            print valid,namestr
            name=""
        elif not name.replace(" ","").replace("_","").isalnum(): #if the name is not alphanumeric with spaces and underscores removed
            print valid,namestr
            name=""[/php]
Your code will reject valid usernames. It IS valid for a username to start with an underscore, and it's valid for it to contain non-alphanumeric characters. Furthermore, your code will silently change user input, which could make a correct, valid username incorrect.

---

### Post by Reiger on 2008-08-08
> **conehead77 said:**
> Wow, i dont understand half of your code. Maybe because i dont know about System/Control (yet).

I'll comment my code (almost line by line) as I wouldn't have understood most of it were it not for the fact I used the quite infallible **ghci** command:
```

:t expr

```

And **Hoogle**. Gotta love Hoogle!

```

module Main where
import Control.Exception -- imports the functions required to catch/try Exceptionable code
import Data.Char         -- imports the isDigit function
import System.Exit       -- imports the exitWith :: ExitCode -> IO a function
import System.IO         -- imports the functions/constants required to turn off buffering
import System.IO.Unsafe  {- imports a backdoor into the IO monad to be able to strip the unwiedly IO String down to the more handsome String, in the prompt function -}

-- Print a line, and return subsequent user input.
prompt :: [Char] -> [Char]
prompt x = unsafePerformIO ( (putStr (x ++ "\n> ")) >> getLine ) {- A compact notation for
unsafePerformIO ( foo )
where
foo = do
      putStr (x ++ "\n> ")
      str <- getLine
      return str
-}

-- Names aren't allowed to begin with whitespace, thereby removing invalid user input.
userConstraint :: [Char] -> Bool
userConstraint (' ':xs) = False -- simple pattern matching (space + rest); using the fact that String == [Char]
userConstraint ('\t':xs) = False -- simple pattern matching (tab + rest) ...
userConstraint _       = True {- using the fact pattern matching is evaluated top to bottom... I don't care about the pattern anymore... -}

-- Numbers aren't allowed to begin with 0 or -, thereby removing invalid user input.
numericConstraint :: [Char] -> Bool
numericConstraint ('0':xs) = False -- see the other constraint function for the idea
numericConstraint ('-':xs) = False -- ditto
numericConstraint xs = all isDigit xs {- major stylistic improvement compared to previous version; using the built in Prelude function all instead of writing out a lazy definition for it manually... <_< -}

-- For simple testing purposes: always accepts anything
genericConstraint :: a -> Bool
genericConstraint _  = True

-- Keep asking till valid input was given; special cases "quit" (valid) and "" (invalid) bypass the 'validator'
sanitize :: [Char] -> ([Char] -> Bool) -> [Char] -> [Char]
sanitize "" p m = sanitize (prompt m) p m -- if someone were to hit enter immediately at the prompts... call back
sanitize "quit" p m = "quit" -- let "quit" (my kill command) fall through any prompt
sanitize xx p m
    | p(xx)     = xx -- predicate p holds for xx; therefore the constraints were met; thus pass on the value!
    | otherwise = sanitize (prompt m) p m {- otherwise re-prompt; I use a different message to indicate that the value entered was wrong -}

-- Ask for input
get :: [Char] -> ([Char] -> Bool) -> [Char]
get ask constraint = sanitize (prompt m) constraint e -- invoke the 'true' get function
                     where
                     m = "Please enter your "++ask++" below:" -- the generic ask 'demand for input'
                     e = "You (must) have specified a wrong "++ask++"! "++m {- the version to use upon re-prompting after invalid input -}

-- Ask for input which is hopefully numeric, but maybe not
getMaybeNum :: [Char] -> Maybe Int
getMaybeNum ask = eval (get ask numericConstraint)
                  where
                  eval "quit" = Nothing {- because of Haskell's strict typing mechanism I need something which can also encapsulate some ambiguity regarding the meaning of the value: kill or actual value? The Maybe monad is perfect, it even makes syntactic sense on the code level: "quit" isn't an Int! -}
                  eval  str   = Just (read str) {- note how the function signature enforces this read to be of the type read :: Int -}

-- Ask for a name
getName :: [Char]
getName = get "username" userConstraint -- easy enough ;-)

-- Ask for an age
getAge :: Maybe Int
getAge = getMaybeNum "age"

-- Ask for a UID
getUID :: Maybe Int
getUID = getMaybeNum "forum id"

-- Make the program executable; and catch any exception it may throw
main :: IO()
main = do
       hSetBuffering stdout NoBuffering -- turn off buffering of stuff written to STDOUT
       x <- Control.Exception.catch run catch22 {- in case no exception occurs this will return the formatted string. The Control.Exception.catch is the imported Exception-catch function; bypassing the Prelude.catch (IOErrors only!!!) function. run is the exceptionable code; catch22 is the exception handler code. -}
       putStrLn x
       return ()
       where
       catch22 _ = return "Okay I'll quit now." -- in this case I simply return a 'catchy' (?!) string

-- The Real Main Method: does everything main can't. Such as throwing an exception and not invalidating my contest entry ;)
run :: IO String
run = do
      putStrLn "A simple, mildly inquisitive program. To quit at any time, type 'quit' at the prompt."
      n <- (check    getName ) {- n is assinged the value of getName; check is just a filter to avoid the program going on blissfully unaware of a "quit" command with ... -}
      a <- (numcheck getAge  ) {- ... assinging a; numcheck is the same as check but for the Maybe Int type... -}
      u <- (numcheck getUID  ) {- ... same idea as above ... -}
      return ("You are '"++n++"', aged "++(show a)++" and next year you will be "++(show (1 + a))++". Your forum id is '"++(show u)++"' and the next user is '"++(show (1 + u))++"'.") -- my nicely formatted string
      where
      check    "quit"    = exitWith ExitSuccess -- raise an ExitException; to be caught in main; to break free!
      check    str       = return str -- or just pass on the str
      numcheck Nothing   = exitWith ExitSuccess -- raise an ExitException; to be caught in main; to break free!
      numcheck (Just i)  = return i -- or just pass on the i

```

---

### Post by Reiger on 2008-08-08
> **PrivateVoid said:**
> Thanks.

Many people are missing the specification:

[omitted spec]

> **LaRoza said:**
> It should be obvious what the command [to kill it] is when I run the program, so it doesn't matter.

So I guess/hope that anything would be accepted if the valid code were to be made clear at a/the prompt. Even the good old AoE cheat:
```

die die die

```

Should be considered a valid exit-command.

---

### Post by Bachstelze on 2008-08-08
> **Reiger said:**
> So I guess/hope that anything would be accepted if the valid code were to be made clear at a/the prompt. Even the good old AoE cheat:
```

die die die

```

Should be considered a valid exit-command.

I also considered making the terminal flash in red a few times with "st00p1d us3r!!" figlet-printed in the center when some invalid data is entered. Maybe next time :p

---

### Post by LaRoza on 2008-08-08
This will be closed in a few hours, so speak now or [for a day] hold your peace.

---

### Post by badperson on 2008-08-08
just squeaked in under the wire...
written in java, challenge itself didn't feel too hard, but I'm sure my code could be a lot more elegant. 

Would be interested in seeing code that addressed the unicode issue after the challenge is over...
mine runs on the command line. 

```
/**
Ubuntu forum challenge #2, user input
http://ubuntuforums.org/showthread.php?t=881152
written in java
written by badperson 8/8/08

*/


import java.io.*;
import java.util.*;
public class UserInputChallenge {
                
	private String name; 
	private String truncatedName;
	private int age;
	private int forumId;    
	private	String input = "";



	// method to get user input
	public void getUserInput(){ 
	System.out.println("Welcome to the Ubuntu Forum User input challenge.\nThis submission by Badperson.\nPlease follow the prompts, type \"exit\" at any time to quit\n");
	System.out.println("please enter your forum name: ");
	convertUserInput(); 
	name = input; 
	truncateName(name);

	System.out.println("please enter your forum id: ");
	convertUserInput();    
	validateForumId(input);    

	System.out.println("please enter your age: ");
	convertUserInput();
	validateAge(input);
	System.out.println("You are " + name + ", aged " + age + ", next year you will be " + (age + 1) + ", \nwith user id " + forumId  + ", the next user is " + (forumId + 1));

	} // get user input method


	public void truncateName(String nameToTruncate){

		if(nameToTruncate.length() > 20){
			String temp="";
				for(int i=0;i<20;i++){
				temp += nameToTruncate.charAt(i);
				}
			truncatedName = temp;
		        System.out.println("truncated name is: " + truncatedName);
                
		} else {
                truncatedName = nameToTruncate;
		}
	
	}

        public void validateAge(String ageString){
        	if(isAllDigits(ageString)){
		age = Integer.parseInt(input);

			if(age < 7){
        	         System.out.println("you're awfully young to be writing code, please re-enter or quit: ");
			convertUserInput();
			validateAge(input);
			} else if (age > 120){
	                 System.out.println("you've entered an age that is way too old for you to be serious...pleae re-enter or type \"exit\"");
			convertUserInput();
			validateAge(input);
			}


		} else {
                System.out.println("your age must be a positive integer, and within the realm of human possibility, please re-enter: ");
		convertUserInput();
		validateAge(input);
		}

	}

	public void validateForumId(String id){
		
		if (id.length() > 6 ){
		System.out.println("your forum id must be an integer between 0 and 999999, please re-enter: ");
		convertUserInput();
		validateForumId(input);

		} else if(isAllDigits(id)){
			forumId = Integer.parseInt(input);
		} else {
		System.out.println("your forum id must be an integer between 0 and 999999, please re-enter: ");
		convertUserInput();
		validateForumId(input);
		}

	}

	public boolean isAllDigits(String digitString){
		for(int i=0;i<digitString.length();i++){
			boolean check=Character.isDigit(digitString.charAt(i));
			if(check==false){
			return false;
			}
		}  
	return true;

	}

	// method to get user input
	public void convertUserInput(){
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));  
                                 	

		try{
		input = br.readLine();
			if(input.equalsIgnoreCase("exit")){
        	         System.out.println("you have decided to exit the program, terminating...");
			 System.exit(0);
			} else if(input.equals("")){
			System.out.println("you have entered an empty value, please re-enter your value, or type \"exit\"");
			convertUserInput();                                                    	
			} else if(input.startsWith(" ")){
			System.out.println(" no value may begin with a space, please re-enter your value: ");
			convertUserInput();
			}

		} catch (IOException ioe){
		System.err.println("problem reading user input, program bombed...");
                 ioe.printStackTrace();

		}

	}


// main method
	public static void main(String[] args){

	new UserInputChallenge().getUserInput();

	} // end main


} // end class
```

---

### Post by LaRoza on 2008-08-08
> **badperson said:**
> 
Would be interested in seeing code that addressed the unicode issue after the challenge is over...
mine runs on the command line. 


The easiest way would be to use a language which supported it out of the box.

---

### Post by nvteighen on 2008-08-08
> **badperson said:**
> 
Would be interested in seeing code that addressed the unicode issue after the challenge is over...


Try mine and you'll see Unicode support ;) [http://ubuntuforums.org/showthread.php?p=5534421#post5534421](http://ubuntuforums.org/showthread.php?p=5534421#post5534421)

---

### Post by Ed J on 2008-08-08
In regards to "if"
> **LaRoza said:**
> It is the most used keyword.

"If" is the middle word in life.
BTW thats a movie quote.

---

### Post by jimi_hendrix on 2008-08-08
> **LaRoza said:**
> I didn't read the code so I can't say where. But what it is the maximum size of the data type for the numerical input?

i made them both longs so for extra exception handling (in case someone one is a couple billion years old)

---

### Post by Reiger on 2008-08-08
> **badperson said:**
> 
Would be interested in seeing code that addressed the unicode issue after the challenge is over...


Well, Java uses an implementation of Unicode by default...

---

### Post by badperson on 2008-08-08
been meaning to read [this]("http://www.joelonsoftware.com/articles/Unicode.html") for awhile...
bp

---

### Post by LaRoza on 2008-08-08
> **jimi_hendrix said:**
> i made them both longs so for extra exception handling (in case someone one is a couple billion years old)

Well, I entered a very long string of numbers and it threw an uncaught exception.

The lesson is to not assume the user will enter near valid data. The article I recommended people read says users will blissfully enter their name, lunch or nothing at any prompt.

Thread going to be closed soon.

---

### Post by jimi_hendrix on 2008-08-08
ok i believe i fixed the problem...the user will go in an infinite loop until he either loads a profile or creates a new one (wait do i need to fix this so that he can exit while he is making his profile???)

if so dont start judging for a bit...

---

### Post by jimi_hendrix on 2008-08-08
ok here is my revised code with what has hopefully no bugs

[PHP]using System;
using System.Collections.Generic;
using System.Text;
using System.IO;

namespace User_Input
{
    class Program
    {
        static void Main(string[] args)
        {
            //variables we will use
            bool keepGoing = true; //this keeps our while loop going
            string name = ""; //this is your name
            long age = 0; //your age
            long nextAge = age + 1; //the age you will be next year
            long uID = 0; //your id
            long nextUID = uID + 1; //the next person's id
            bool loaded = false;//we will use this at the start to make sure the user creates or loads a profile
            bool newProfile = false;

            //asks if the user wants to load or make a new profile
            Console.WriteLine("Type load to load a profile or \n anything else to create a new one. \n You can also type quit at any time \n during the creation process to quit");
            string answer = Console.ReadLine();//set answer to the input by user

            if (answer.ToLower() == "load")//here is where we load the profile
            {                              //we use the ToLower method to make sure that if the user types Load, lOAD, LOAD or any combination of capitals and lower case will be valid

                while (loaded == false)//makes sure the person wants to load a file                   
                {
                    Console.WriteLine("what is the name of the profile you want to load?");

                    try//this will attempt to seach for a user file
                    {
                        string quit = Console.ReadLine();
                        if (quit.ToLower() == "quit")
                        {
                            return;
                        }
                        StreamReader sr = new StreamReader(quit);//creates a Stream Reader to read the file
                        name = sr.ReadLine();//reads the first line of the file and sets name to it
                        age = Convert.ToInt32(sr.ReadLine());//reads the second line of the file sets age to it
                        uID = Convert.ToInt32(sr.ReadLine());//reads the third line of the file and sets uID to it
                        Console.WriteLine();//these lines print out the user info
                        Console.WriteLine(name);
                        Console.WriteLine(age);
                        Console.WriteLine(uID);
                        sr.Close();//closes the stream reader without this the program will still be accessing the stream even after its close
                        loaded = true;
                    }
                    catch (FileNotFoundException)//error handling
                    {
                        string reload;
                        Console.WriteLine("ERROR NO PROFILE WITH THAT NAME EXISTS!!!");
                        Console.WriteLine("do you want to load again? Type no to create a new profile or quit to exit \n (anything else will ask you to load again)");
                        reload = Console.ReadLine();
                        if (reload.ToLower() == "quit")
                        {
                            return;
                        }
                        if (reload.ToLower() == "no")
                        {
                            newProfile = true;
                            loaded = true;
                        }
                    }
                }
            }
            else
            {
                newProfile = true;
            }

            

             while(newProfile == true)//if the user chooses to load they create a new profile here
             {
                string quit;
                Console.WriteLine("What is your name?");//this is all basic question and answer with the user
                name = Console.ReadLine();
                if (name.ToLower() == "quit")
                {
                    return;
                }
                Console.WriteLine("What is your age?");
                try
                {
                    quit = Console.ReadLine();
                    if (quit.ToLower() == "quit")
                    {
                        return;
                    }
                    age = Convert.ToInt32(quit);
                    nextAge = age + 1;
                }
                catch (FormatException)
                {
                    Console.WriteLine("you have entered invalid input please finish filling out the data and then re enter it");
                }
                catch
                {
                    Console.WriteLine("i dont think your that old...");
                }
                Console.WriteLine("What is your user id?");
                try
                {
                    quit = Console.ReadLine();
                    if (quit.ToLower() == "quit")
                    {
                        return;
                    }
                    uID = Convert.ToInt32(quit);
                    nextUID = uID + 1;
                }
                catch (FormatException)
                {
                    Console.WriteLine("you have entered invalid input please finish filling out the data and then re enter it");
                }
                catch
                {
                    Console.WriteLine("i dont think your user ID is that long...");
                }
                if (age <= 0 | uID <= 0)//error handling
                {
                    Console.WriteLine("you have entered invalid data for your age and/or id");
                }

                else//everything is created correctly so we can exit
                {
                    newProfile = false;
                }
             }            

            while (keepGoing == true)//the guts of the program start here
            {
                Console.WriteLine("Your name is: {0}", name);//display user data
                Console.WriteLine("Your age is {0}, next year you will be {1} years old", age, nextAge);
                Console.WriteLine("Your user ID is {0}, next year you will be {1}", uID, nextUID);
                Console.WriteLine();
                Console.WriteLine();

                int choice = Menu();//display menu and get user choice
                
                switch (choice)//act depending on choice
                {
                    case 0://display info again
                        Console.WriteLine("Your name is: {0}", name);
                        Console.WriteLine("Your age is {0}, next year you will be {1} years old", age, nextAge);
                        Console.WriteLine("Your user ID is {0}, next year you will be {1}", uID, nextUID);
                        Console.WriteLine();
                        Console.WriteLine();
                        break;
                    case 1://change name
                        try
                        {
                            name = nameChange();
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 2://change age
                        try
                        {
                            age = ageChange();
                            nextAge = age + 1;
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 3://change id
                        try
                        {
                            uID = idChange();
                            uID = nextUID + 1;
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 4://save
                        try
                        {
                        StreamWriter sw = new StreamWriter(name);//here we save the user data to a file with the same name as the user
                        sw.WriteLine(name);
                        sw.WriteLine(Convert.ToString(age));
                        sw.WriteLine(Convert.ToString(uID));
                        sw.Close();
                        Console.WriteLine("saved");
                        }
                        catch
                        {
                            Console.WriteLine("Error please try again");
                        }
                        break;
                    case 5://load
                        Console.WriteLine("what is the name of the profile you want to load?");

                        try
                        {
                            StreamReader sr = new StreamReader(Console.ReadLine());//here we load the data line by line
                            name = sr.ReadLine();
                            age = Convert.ToInt32(sr.ReadLine());
                            uID = Convert.ToInt32(sr.ReadLine());
                            Console.WriteLine(name);
                            Console.WriteLine(age);
                            Console.WriteLine(uID);
                            nextAge = age + 1;
                            nextUID = uID + 1;
                            sr.Close();
                        }
                        catch (FileNotFoundException)//error handling for no files or invalid data
                        {
                            Console.WriteLine("ERROR NO PROFILE WITH THAT NAME EXISTS!!!");
                        }
                        
                        break;
                    case 6://exit
                        return;
                        
                }
            }
        }

        static int Menu()// method to display the menu and get the user choice
        {
            int input = 0;
           
            Console.WriteLine("What would you like to do now?");
            Console.WriteLine("[0]: Enter 0 to print your info to screen again");
            Console.WriteLine("[1]: Enter 1 to change your name");
            Console.WriteLine("[2]: Enter 2 to change your age");
            Console.WriteLine("[3]: Enter 3 to change your id");
            Console.WriteLine("[4]: Enter 4 to save your profile");
            Console.WriteLine("[5]: Enter 5 to load a profile");
            Console.WriteLine("[6]: Enter 6 to exit");
            try
            {
                input = Convert.ToInt32(Console.ReadLine());
            }
            catch(FormatException)//error handling
            {
                Console.WriteLine("INVALID INPUT");
            }
            return input;
        }

        static string nameChange()//method to change the user name
        {
            string newName;
            Console.WriteLine("What would you like to change it to?:");
            newName = Console.ReadLine();
            return newName;
        }

        static int ageChange()//method to change the age
        {
            int nAge;
            Console.WriteLine("What would you like to change it to?:");
            nAge = Convert.ToInt32(Console.ReadLine());
            return nAge;
        }
         
        static int idChange()//method to change the id
        {
            int nID;
            Console.WriteLine("What would you like to change it to?:");
            nID = Convert.ToInt32(Console.ReadLine());
            return nID;
        }
    }

}[/PHP]

---

### Post by linkmaster03 on 2008-08-08
I fixed it according to feedback:

[php]#!/usr/bin/env python
# userinfo.py
#User Info Gatherer by LinkMaster03
import sys
name,age,id,valid,namestr,agestr,idstr="","","","Please enter a valid","username.\n(Only letters,\
 numbers, spaces, and underscores. Must have, and start and end with, atleast one letter or\
 number.)","age. (integer 5-130)","forum ID. Click on your Ubuntuforums profile, and the number\
 after the = is your forum ID. (integer 1-999999)" #define error messages
print "\nType exit or quit at any prompt to leave!"
def getName():
    try:    #if an exception is thrown in here
        name=raw_input("What is your username? ") #get username
        if len(name.strip())<1 or len(name.strip())>20: 
            print "Invalid username length, please enter a name with 1-20 characters."
            name=""
        elif name=="exit" or name=="quit": #if user wants to quit the program
            sys.exit()
        else:
            if name.strip()!=name:
                print "Spaces have been stripped from beginning and end of name."
                name=name.strip()
        return name
    except (TypeError, ValueError, AttributeError):     #handle it here
        print valid,namestr
        name=""
def getAge():
    try:    #if an exception is thrown in here
        age=raw_input("Thanks! Can I have your age? ")
        age=age.strip(" _")
        age=age.replace(" ","") #remove all spaces
        if age=="exit" or age=="quit": sys.exit()
        age=int(age)
        if age<5 or age>130:
            print valid,agestr
            age=""
        else: 
            pass
        return age
    except (TypeError, ValueError, AttributeError):     #handle it here
        print valid,agestr
        age=""
def getID():
    try:
        id=raw_input("Great! Will you tell me your forum ID? ")
        id=id.strip(" _")
        id=id.replace(" ","")
        if id=="exit" or id=="quit": sys.exit()
        id=int(id)
        if id<1 or id>999999:
            print valid,idstr
            id=""
        else: 
            pass
        return id
    except (TypeError, ValueError, AttributeError):
        print valid,idstr
        id=""
while not name:
    name=getName()
while not age:
    age=getAge()
while not id:
    id=getID()
print "Your username is %s. You are %s years old, and you will be turning %s on your next birthday!\
 Your Ubuntuforums user ID is %s, and the ID of the person who registered after you is %s. Your profile is at\
 http://ubuntuforums.org/member.php?u=%s." % (name,age,age+1,id,id+1,id)  [/php]

It will now accept all valid usernames, and notify the user if their name has been stripped of spaces.

---

### Post by LaRoza on 2008-08-08
Closed for grading. Might take a day to finish. 

Stay tuned...

---

### Post by LaRoza on 2008-08-08
Opened for an hour. Going to grocery store.

---

### Post by Joeb454 on 2008-08-08
> **LaRoza said:**
> Opened for an hour. Going to grocery store.

I've still not done it :p I best get cracking!

---

### Post by ibuclaw on 2008-08-08
> **Joeb454 said:**
> I've still not done it :p I best get cracking!

Always fashionably late, you are The-Joe...

---

### Post by LaRoza on 2008-08-08
Possibles:
[list]
[*] linkmaster03 (python) [http://ubuntuforums.org/showpost.php?p=5551282&postcount=167](http://ubuntuforums.org/showpost.php?p=5551282&postcount=167)
[*] chandru (C#) [http://ubuntuforums.org/showpost.php?p=5547417&postcount=130](http://ubuntuforums.org/showpost.php?p=5547417&postcount=130)
[*] xnevermore (ruby) [http://ubuntuforums.org/showpost.php?p=5544919&postcount=115](http://ubuntuforums.org/showpost.php?p=5544919&postcount=115)
[*] M_the_C (python) [http://ubuntuforums.org/showpost.php?p=5543810&postcount=107](http://ubuntuforums.org/showpost.php?p=5543810&postcount=107)
[*] PrivateVoid (python) [http://ubuntuforums.org/showpost.php?p=5543207&postcount=103](http://ubuntuforums.org/showpost.php?p=5543207&postcount=103)
[*] Ed J (python) [http://ubuntuforums.org/showpost.php?p=5540624&postcount=89](http://ubuntuforums.org/showpost.php?p=5540624&postcount=89)
[*] artoj (c++) [http://ubuntuforums.org/showpost.php?p=5540398&postcount=88](http://ubuntuforums.org/showpost.php?p=5540398&postcount=88)
[*] TreFinger (python) [http://ubuntuforums.org/showpost.php?p=5535623&postcount=51](http://ubuntuforums.org/showpost.php?p=5535623&postcount=51)
[*] Reiger (php) [http://ubuntuforums.org/showpost.php?p=5534573&postcount=46](http://ubuntuforums.org/showpost.php?p=5534573&postcount=46)
[*] mcsimon (java) [http://ubuntuforums.org/showpost.php?p=5533325&postcount=40](http://ubuntuforums.org/showpost.php?p=5533325&postcount=40)
[*] bobbocanfly (python) [http://ubuntuforums.org/showpost.php?p=5531236&postcount=6](http://ubuntuforums.org/showpost.php?p=5531236&postcount=6)
[/list]

Sorry:
[list]
[*] jimi_hendrix (when given improper input, asked all questions over again and allowed an name with no characters in it)
[*] badperson (threw uncaught exception when given a very large number)
[*] Reiger (gave weird unanswers with large numbers, first version gave a negative number for my age!)
[*] C!oud (quit when entered a very large number, not according to specs)
[*] conehead77 (Infinate loop, nothing worked)
[*] HymnToLife (threw uncaught exception on empty string for name, first thing I tried...)
[*] PandaGoat (couldn't read prompts)
[*] HymnToLife (wouldn't compile, memory management issues)
[*] Def13b (syntax error)
[*] OutOfReach (error on name for "laroza o")
[*] tinivole (truncates long numbers)
[*] scourge (doesn't give errors for large numbers, invalid data and responses)
[*] wtfnomorenames (silently accepted 22-1 for an age)
[*] Titan8990 (threw uncaught exception on first try, empty input for name)
[*] nvteighen (long numbers cause logical errors)
[*] shae (accepted 233s as user id)
[*] arsenic23 (long numbers again)
[*] chris200x9 (infinite loop on error)
[/list]
Couldn't run:

---

### Post by Bachstelze on 2008-08-08
> **LaRoza said:**
> 
[*] HymnToLife (threw uncaught exception on empty string for name, first thing I tried...)

I'm sorry but it does not throw any exception here. Did you really try *my* code (post #52) and not some code from another user I copied?

The C one is just me being an idiot, though, I quickly modified something I thought was trivial without testing it first...

---

### Post by LaRoza on 2008-08-08
[list]
[*]  [artoj](http://ubuntuforums.org/showpost.php?p=5540398&postcount=88)
[*]  [bobbocanfly](http://ubuntuforums.org/showpost.php?p=5531236&postcount=6)
[*]  [chandru](http://ubuntuforums.org/showpost.php?p=5547417&postcount=130)
[*]  [Ed J](http://ubuntuforums.org/showpost.php?p=5540624&postcount=89)
[*]  [linkmaster03](http://ubuntuforums.org/showpost.php?p=5551282&postcount=167)
[*]  [mcsimon](http://ubuntuforums.org/showpost.php?p=5533325&postcount=40)
[*]  [PrivateVoid](http://ubuntuforums.org/showpost.php?p=5543207&postcount=103)
[*]  [Reiger](http://ubuntuforums.org/showpost.php?p=5534573&postcount=46)
[*]  [TreeFinger](http://ubuntuforums.org/showpost.php?p=5535623&postcount=51)
[*]  [xnevermore](http://ubuntuforums.org/showpost.php?p=5544919&postcount=115)
[/list]

Sorry, had to bump: [M_the_C](http://ubuntuforums.org/showpost.php?p=5543810&postcount=107) to get 10. Reason for bumping: lack of shebang.

---

### Post by LaRoza on 2008-08-08
> **HymnToLife said:**
> I'm sorry but it does not throw any exception here. Did you really try *my* code (post #52) and not some code from another user I copied?

The C one is just me being an idiot, though, I quickly modified something I thought was trivial without testing it first...

[http://ubuntuforums.org/showpost.php?p=5541062&postcount=94](http://ubuntuforums.org/showpost.php?p=5541062&postcount=94)

---

### Post by Bachstelze on 2008-08-08
As I say in the post, it was not my code, it was Titan8990's that I modified to show him how to get rid of the global variables...

---

### Post by LaRoza on 2008-08-08
> **HymnToLife said:**
> As I say in the post, it was not my code, it was Titan8990's that I modified to show him how to get rid of the global variables...

I see....

I am only now beginning to read anything (beyond prompts). Copy, paste, run, input, repeat.

I didn't test the prior ones (except the C one, because I thought you were doing two languages)

---

### Post by Bachstelze on 2008-08-08
> **LaRoza said:**
> I see....

I am only now beginning to read anything (beyond prompts). Copy, paste, run, input, repeat.

I didn't test the prior ones (except the C one, because I thought you were doing two languages)

No problem ;)

Well, I actually did a Python one and a C one. The Python (#52) I did mostly for fun, as I'm 99,999% sure it works. The C one was more of a challenge, and seems to work fine too, that'll teach me not to submit untested changes, however tiny they might seem :p

---

### Post by LaRoza on 2008-08-08
> **HymnToLife said:**
> No problem ;)

Well, I actually did a Python one and a C one. The Python (#52) I did mostly for fun, as I'm 99,999% sure it works. The C one was more of a challenge, and seems to work fine too, that'll teach me not to submit untested changes, however tiny they might seem :p

Well, as I tested it it worked fine, however, I had 11 working version and had to bump one of 6 Python versions. I didn't want to add another so I didn't even consider it. It did pass the tests though.

---

### Post by Def13b on 2008-08-08
Just for future reference, your not using P3K are you? :) Can't seem to get mine to throw up a syntax error in anything other then 3000.

---

### Post by arsenic23 on 2008-08-08
I love these challanges.  I had no idea you couldn't add long numbers in bash.  More importantly I don't know why I just assumed you could.  ( I had not noticed that I needed the next user's ID untill after the first time I'd posted it, so I just added it in without testing. ) 

I also had never head of *bc*, turns out I should have gotten the next user's ID like this:
```
nextid=`echo $forumid + 1 | bc`
```

---

### Post by linkmaster03 on 2008-08-08
How are you gonna stop everyone just voting for themselves?

---

### Post by arsenic23 on 2008-08-08
> **linkmaster03 said:**
> How are you gonna stop everyone just voting for themselves?

Does it matter?  Though, I voted *other* in the last poll just to not be tempted to vote for myself.

---

### Post by conehead77 on 2008-08-08
> **LaRoza said:**
> 
[*] conehead77 (Infinate loop, nothing worked)


Huh? I just copied my code from this thread and tested again without problems (see attachment).
It also worked with GHCI and HUGS on 8.04.

---

### Post by linkmaster03 on 2008-08-08
Still, the requirements were accepting user IDs 1-999999. :P

---

### Post by LaRoza on 2008-08-08
> **arsenic23 said:**
> I love these challanges.  I had no idea you couldn't add long numbers in bash.  More importantly I don't know why I just assumed you could.  ( I had not noticed that I needed the next user's ID untill after the first time I'd posted it, so I just added it in without testing. ) 


You assumed you could because it was illogical to do otherwise. Users are not logical. Users are evil (most people try to avoid them)

> **linkmaster03 said:**
> How are you gonna stop everyone just voting for themselves?

Voters are shown (click on numbers in poll). And it doesn't matter. A good programmer can determine when another's code is better than theirs, and when theirs is better than others. (And it doesn't matter in the long run)

> **conehead77 said:**
> Huh? I just copied my code from this thread and tested again without problems (see attachment).
It also worked with GHCI and HUGS on 8.04.

I compiled it, maybe that what caused the problem?

---

### Post by mssever on 2008-08-09
As promised, here are my suggested improvements to xnevermore's submission. xnevermore, I'm not picking on you. I promise! It just happens that Ruby is my favorite language and yours was the only Ruby submission.

I'm only suggesting code cleanup type issues. Other things would require a rewrite, and they'd touch on matters of personal style.
[php]#!/usr/bin/ruby

# Ruby style point: Ruby convention is to use underscores, not camelCase,
# to separate words in variable and method names. For example, use set_name,
# not setName. The reason this kind of consistency is important is that it's
# a lot easier to remember how to spell some method name if you know that you
# don't have to remember how to separate the words. And Ruby core and the
# standard library both use underscores. If you ever decide to mess with Rails,
# Rails will force you to follow that convention.

class Person
  
  # Instance variables should be initialized in the constructor,
  # though you don't need to initialize them in this situation.
  # Still, it can't hurt...
  def initialize
    @name, @age, @id = nil
  end

  def setName (name)
    # All input comes in as a string, so checking for a String is pointless.
    # Besides, the Ruby way is to use duck typing (call name.to_s rather than
    # explicitly checking for a string).
    # name.length <= 20 is better than not name.length > 20. But you don't need
    # to check that anyway. The limit is for the benefit of languages that have
    # difficulty with arbitrary-length input. Ruby is NOT one of those
    # languages, and a 19-character limit will reject some valid usernames.
    # I just saw a 24-character username: Yannick Le Saint kyncani (id: 20026)
    # 
    # Another thing: name[0] != ' '[0] is equivalent to name[0] != ' '

    # if name.kind_of? String and not name.empty? and name[0] != ' '[0] and not name.length > 20
    if name.empty? or name =~ /^[\s]/  # The forum is eating my backslash! It's supposed to be before the s
      @name = nil
    else
      @name = name # String#chomp is unnecessary because you're already calling it.
                   # On the other hand, calling it twice is better than not at all.
    end
  end

  def setAge (age)
    # See comments on setId
    @age = age
    @age = nil if @age <= 0
  end

  def setId (id)
    # You already ran to_i on id, so id is guaranteed to be an Integer.
    # No sense in differentiating between a Fixnum and a Bignum, though.

    #if id.kind_of? Fixnum and (1..999999) === id
    #  @id = id
    #else
    #  @id = nil
    #end
    @id = id
    @id = nil unless @id.between? 1, 999_999
  end

  #def name
  #  @name
  #end
  #def id
  #  @id
  #end
  #def age
  #  @age
  #end
  attr_reader :name, :id, :age # Let Ruby write your basic accessor methods for you!
end

def xgets
  result = gets.chomp
  if result.upcase == 'EXIT'
    puts "Program terminated"
    exit
  else
    return result
  end
end

# I added this for compliance with the rules:
puts "Type `exit' to quit."

person = Person.new
until person.name # Notice the until loop
  print "Name: ";
  person.setName(xgets)
end
until person.age
  print "Age: "
  person.setAge(xgets.to_i)
end
until person.id
  print "ID: "
  person.setId(xgets.to_i)
end

print "You are #{ person.name }, "
print "aged #{ person.age } next year you will be #{ person.age + 1 }, "
puts "with user id #{ person.id }, the next user is #{ person.id + 1 }."[/php]

---

### Post by conehead77 on 2008-08-09
> **LaRoza said:**
> I compiled it, maybe that what caused the problem?

Yes, you are right. After compiling it doesnt work for me either. Now i have something to think about...

---

### Post by mssever on 2008-08-09
> **linkmaster03 said:**
> [php]name,age,id,valid,namestr,agestr,idstr="","","","Please enter a valid","username.\n(Only letters,\
 numbers, spaces, and underscores. Must have, and start and end with, atleast one letter or\
 number.)","age. (integer 5-130)","forum ID. Click on your Ubuntuforums profile, and the number\
 after the = is your forum ID. (integer 1-999999)" #define error messages[/php]
This would be a lot easier to read (and readability counts, especially in Python):
[php]name = ""
age = ""
id = ""
#define error messages
valid = "Please enter a valid"
namestr = """username.\n(Only letters,
 numbers, spaces, and underscores. Must have, and start and end with, atleast one letter or
 number.)"""
agestr = "age. (integer 5-130)"
idstr = """forum ID. Click on your Ubuntuforums profile, and the number
 after the = is your forum ID. (integer 1-999999)"""[/php]

---

### Post by ghostdog74 on 2008-08-09
> **arsenic23 said:**
> I love these challanges.  I had no idea you couldn't add long numbers in bash.  More importantly I don't know why I just assumed you could.  ( I had not noticed that I needed the next user's ID untill after the first time I'd posted it, so I just added it in without testing. ) 

I also had never head of *bc*, turns out I should have gotten the next user's ID like this:
```
nextid=`echo $forumid + 1 | bc`
```

there are lots of ways to count up in bash. bc is one, expr is another, . Other ways to count
```
 
# a=1
# echo $(( a + 1 ))
2
# expr 1 + 3 
4

```

---

### Post by arsenic23 on 2008-08-09
> **ghostdog74 said:**
> there are lots of ways to count up in bash. bc is one, expr is another, . Other ways to count
```
 
# a=1
# echo $(( a + 1 ))
2
# expr 1 + 3 
4

```

Actually $(( a + 1 )) won't work with long number, and expr doesn't seem to either, though it may and I just didn't look at it long enough.  The problem was I didn't stop the user from entering long numbers because...  I dunno, on a whim.  All of my coded worked except that :

```
$ echo $(( 23138991037489701324781329804730192 + 1 ))
-8899521776612761775
```

Using bc fixes the problem though.

---

### Post by cprofitt on 2008-08-09
now that it is closed...

I put in a piece of code to ensure I got an integer -- 1, 2, 3, etc...

not a 1.5.

I thought that would be a requirement... was I incorrect in that? Was my test, given Python, not needed?

```

[FONT=monospace]def integertest(n):
    if n % 1 == 0:
        return True
    else:
        return False

```
[/FONT]

---

### Post by mssever on 2008-08-09
> **PrivateVoid said:**
> now that it is closed...

I put in a piece of code to ensure I got an integer -- 1, 2, 3, etc...

not a 1.5.

I thought that would be a requirement... was I incorrect in that? Was my test, given Python, not needed?

```

[FONT=monospace]def integertest(n):
    if n % 1 == 0:
        return True
    else:
        return False
[/FONT]
```[FONT=monospace]
[/FONT]Assuming you're testing your code while still a string, you could do something like:
[php]try:
    n = int(n)
except ValueError:
    # Handle invalid input
# Here, we know that we have a valid int (though there hasn't been any range checking yet.[/php]

---

### Post by ghostdog74 on 2008-08-09
> **arsenic23 said:**
> Actually $(( a + 1 )) won't work with long number, and expr doesn't seem to either, though it may and I just didn't look at it long enough.  The problem was I didn't stop the user from entering long numbers because...  I dunno, on a whim.  All of my coded worked except that :

```
$ echo $(( 23138991037489701324781329804730192 + 1 ))
-8899521776612761775
```

Using bc fixes the problem though.


if you look at the bash [FAQ](http://www.faqs.org/faqs/unix-faq/shell/bash/),
> 
   New features added to bash-2.05b since the release of bash-2.05a.  

    o.  The shell now performs arithmetic in the largest integer size the
        machine supports (intmax_t), instead of long. 


---

### Post by cprofitt on 2008-08-09
> **mssever said:**
> Assuming you're testing your code while still a string, you could do something like:
[php]try:
    n = int(n)
except ValueError:
    # Handle invalid input
# Here, we know that we have a valid int (though there hasn't been any range checking yet.[/php]

That method depends on an error...

I guess I like my code a bit better as it does not rely on an error... and it would work if the variable was already not a string.

---

### Post by conehead77 on 2008-08-09
> **LaRoza said:**
> I compiled it, maybe that what caused the problem?

Problem solved, buffering was the problem. I updated again (not for the challenge, just to have a working solution).

---

### Post by NovaAesa on 2008-08-09
> **PrivateVoid said:**
> I put in a piece of code to ensure I got an integer -- 1, 2, 3, etc...

not a 1.5.

```

[FONT=monospace]def integertest(n):
    if n % 1 == 0:
        return True
    else:
        return False

```
[/FONT]

I'm not sure how it works in Python, but I do know that in alot of other languages you get inconsistent results when using the modulo operator on floating point numbers.

---

### Post by Def13b on 2008-08-09
> **PrivateVoid said:**
> now that it is closed...

I put in a piece of code to ensure I got an integer -- 1, 2, 3, etc...

not a 1.5.

I thought that would be a requirement... was I incorrect in that? Was my test, given Python, not needed?


Assuming I'm reading the correct post (#103) wouldn't it never get to that anyway, the line before it,

```
while int(iAge) < 1:
    try:
        iAge = raw_input("enter your age (must be an integer between 1 and 130) ")
        if iAge == "exit":
            sys.exit(0)
        elif int(iAge) > 130:   <----- This bit
            iAge = 0
        elif not integertest(int(iAge)):
            iAge = 0
    except ValueError:
        iAge = 0
```

will throw a ValueError if it's given a float so the intergertest will never run.

---

### Post by xnevermore on 2008-08-09
mssever: Awesome. I appreciate the suggestions. I learned a lot. ?The attr_reader part was particularly enlightening. However, you missed updates I had made to the first version of the code.

For example, I'd already gotten ridden of the second chomp (which by the way, was chomp(' '), designed to get rid of extra spaces, but really didn't work like expected) and replaced it with name.rstrip, which worked much better. I'd also changed the not name.length > 20 with name.length < 20, because, you're right, was much more complicated than it should have been.

Also, you were wrong about one thing: name[0] != ' '[0] is not the same as name[0] != ' '. name[0] returns a Fixnum and ' ' returns a string. You can't compare them.

```

irb(main):001:0> ' '[0] == ' '
=> false

```

I orignally made the same mistake, btw. It works in C, after all.

---

### Post by Reiger on 2008-08-09
> **LaRoza said:**
> Possibles:
[list]Sorry:
[*] Reiger (gave weird unanswers with large numbers, first version gave a negative number for my age!)
[/list]


Gah! I should've encapsulated the no-more than six digits!...

---

### Post by cprofitt on 2008-08-09
> **Def13b said:**
> Assuming I'm reading the correct post (#103) wouldn't it never get to that anyway, the line before it,

```
while int(iAge) < 1:
    try:
        iAge = raw_input("enter your age (must be an integer between 1 and 130) ")
        if iAge == "exit":
            sys.exit(0)
        elif int(iAge) > 130:   <----- This bit
            iAge = 0
        elif not integertest(int(iAge)):
            iAge = 0
    except ValueError:
        iAge = 0
```will throw a ValueError if it's given a float so the intergertest will never run.

I just tested the code and putting in 1.5 or 2.5 does indeed throw an error when I did the comparison to > 130...

so the integertest was not necessary... cool... old C# knowledge dies hard. Thanks for that catch and tip.

---

### Post by nvteighen on 2008-08-09
> **LaRoza said:**
> 
Sorry:
nvteighen (long numbers cause logical errors)


Yup, bug confirmed: a somehow obscure integer overflow that is leading to funny results when numbers are too long. Changing to 'long int' doesn't work, either...

---

### Post by mssever on 2008-08-09
> **Def13b said:**
> [/code]will throw a ValueError if it's given a float so the intergertest will never run.Beware that you'll get a ValueError when calling int on a string which contains a float. But calling int on a float is not an error. ```
>>> int('2.5') > 130
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '2.5'
>>> int(2.5)
2
>>> int(2.5) > 130
False
```

> **xnevermore said:**
> The attr_reader part was particularly enlightening.
See attr_writer and attr_accessor for other delicious flavors.
> For example, I'd already gotten ridden of the second chomp (which by the way, was chomp(' '), designed to get rid of extra spaces, but really didn't work like expected)String#chomp is mainly useful for stripping the trailing newline off of your input. I don't use it for anything else, because as you discovered, String#strip and friends do a better job of stripping whitespace.
> Also, you were wrong about one thing: name[0] != ' '[0] is not the same as name[0] != ' '. name[0] returns a Fixnum and ' ' returns a string. You can't compare them.You're right. That's annoying. And it uses a dumb indexing scheme (it appears that it's indexed on the individual bytes in the string, instead of Unicode codepoints). If Ruby had been written by an American, I could understand the error, since all the characters on a US English keyboard are a part of ASCII. But Matz is Japanese, and Japanese has had many character set-related problems, that Matz should be aware of. Why perpetuate the myth that 1 character == 1 byte?

---

### Post by M_the_C on 2008-08-09
As I took part in this one, I would like to vote in it as well.

But as I said I am not a very good programmer, what should I look for to judge?  (Particularly in the non-python ones.)
I will be running them in a bit, but there will probably be at least two or three that are equal, if not all, and it will come down to the code.
> **LaRoza said:**
> Sorry, had to bump: [M_the_C](http://ubuntuforums.org/showpost.php?p=5543810&postcount=107) to get 10. Reason for bumping: lack of shebang.Nooooo.  ;)

---

### Post by jimi_hendrix on 2008-10-05
written in Lua...im learning it because im bored and for game modding purposes

comments are welcome especially about the io.read function because its the one thing my tutorial isnt telling me and im having trouble finding documentation on it
[PHP]print ("what is your name?")
name = io.read ("*line")
print ("what is your age?")
age = io.read ("*line")
print ("what is your user id?")
id = io.read ("*line")
nextAge = age + 1
nextId = id + 1
print ("your name is: "..name)
print ("your age is: "..age)
print ("and you will be "..nextAge .." next year")
print ("your user id is: "..id)
print ("the next person's id will be: ".. nextId)
[/PHP]

---

### Post by Canis familiaris on 2008-10-08
Written in [SIZE="6"]Python[/SIZE]

I have tried to handle few exceptions I found. But I am not sure all.
[SIZE="4"]Comments, tips and Feedback would be REALLY appreciated.[/SIZE] :)

```
[color=#408080]*#!/usr/bin/python*[/color]
[color=#408080]*#Author: Anurag Panda*[/color]

[color=#408080]*#Function cls*[/color]
[color=#008000]**def**[/color] [color=#0000FF]cls[/color](strng[color=#666666]=[/color][color=#BA2121]''[/color]):
	[color=#008000]**print**[/color] [color=#BA2121]'[/color][color=#BB6622]**\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n**[/color][color=#BA2121]'[/color]
	[color=#008000]**print**[/color] [color=#BA2121]'MESSAGE: '[/color], strng
	[color=#008000]**print**[/color] [color=#BA2121]'[/color][color=#BB6622]**\n**[/color][color=#BA2121]'[/color]
[color=#408080]*#end function*[/color]


[color=#408080]*#MAIN	*[/color]
name [color=#666666]=[/color] [color=#BA2121]""[/color]
age[color=#666666]=[/color][color=#666666]0[/color]
id_[color=#666666]=[/color][color=#666666]0[/color]

cls([color=#BA2121]"Welcome.[/color][color=#BB6622]**\n**[/color][color=#BA2121]Step1. Remember username cannot started with space or be empty."[/color])

[color=#008000]**while**[/color]([color=#008000]True[/color]):
	name[color=#666666]=[/color][color=#008000]raw_input[/color]([color=#BA2121]"Enter Name: "[/color])
	[color=#008000]**if**[/color]([color=#AA22FF]**not**[/color](([color=#008000]len[/color](name)[color=#666666]==[/color][color=#666666]0[/color]) [color=#AA22FF]**or**[/color] name[[color=#666666]0[/color]] [color=#666666]==[/color] [color=#BA2121]' '[/color])):
		[color=#008000]**break**[/color]
	[color=#008000]**elif**[/color](name[color=#666666]==[/color][color=#BA2121]"exit"[/color]):
		quit()
	[color=#008000]**else**[/color]:
		cls([color=#BA2121]"Name cannot begin with space or be empty"[/color])
		[color=#408080]*#continue looping till proper username is entered*[/color]


cls([color=#BA2121]"This is Step 2. Remember if you enter age in decimals, the decimal part would be truncated since the age in years is only needed. Please Enter Numeric Data, strings [/color][color=#BB6622][b]\
[/b][/color][color=#BA2121]wouldn't be accepted"[/color])

[color=#008000]**while**[/color]([color=#008000]True[/color]):
	[color=#008000]**try**[/color]: 
		
		age [color=#666666]=[/color] [color=#008000]int[/color]([color=#008000]input[/color]([color=#BA2121]"Enter Age: "[/color] ))
		[color=#008000]**if**[/color](age[color=#666666]>[/color][color=#666666]0[/color] [color=#AA22FF]**and**[/color] age[color=#666666]<[/color][color=#666666]140[/color]):
			[color=#008000]**break**[/color]
		[color=#008000]**else**[/color]:
			cls([color=#BA2121]"Illogical Age. Please Enter again"[/color])
			[color=#408080]*#continue looping till user enters a logical age*[/color]
	[color=#008000]**except**[/color] ([color=#D2413A]**NameError**[/color],[color=#D2413A]**SyntaxError**[/color]):
		cls([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]Incorrect Data Type Inserted. Please Retry.[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color])
		[color=#408080]*#The SyntaxError exception is added when user inputs something like 2dsds, 32dasd*[/color]
		[color=#408080]*#Enter Age: 22s*[/color]
		[color=#408080]*#Traceback (most recent call last):*[/color]
		[color=#408080]*#  File "laroza_c2.py", line 36, in <module>*[/color]
		[color=#408080]*#    age = int(input("Enter Age: " ))*[/color]
		[color=#408080]*#  File "<string>", line 1*[/color]
		[color=#408080]*#    22s*[/color]
		[color=#408080]*#     ^*[/color]
		[color=#408080]*#SyntaxError: unexpected EOF while parsing*[/color]

cls([color=#BA2121]"This is Step 3. Remember if you enter ID in decimals, the decimal part would be truncated since the ID is never in decimal. Please Enter Numeric Data, strings wouldn't[/color][color=#BB6622][b]\
[/b][/color][color=#BA2121]be accepted"[/color])

[color=#008000]**while**[/color]([color=#008000]True[/color]):
	[color=#008000]**try**[/color]:
		id_ [color=#666666]=[/color] [color=#008000]int[/color]([color=#008000]input[/color]([color=#BA2121]"Enter Forum ID: "[/color] ))
		[color=#008000]**if**[/color](id_[color=#666666]>[/color][color=#666666]0[/color] [color=#AA22FF]**and**[/color] id_[color=#666666]<[/color][color=#666666]1000000[/color]):
			[color=#008000]**break**[/color]	
		[color=#008000]**else**[/color]:
			cls([color=#BA2121]"The Forum ID you inserted is either out of range(above 999999, zero, or negative). Please Re-Enter"[/color])
	[color=#008000]**except**[/color] ([color=#D2413A]**NameError**[/color],[color=#D2413A]**SyntaxError**[/color]):
		cls([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]Incorrect Data Type Inserted. Please Retry.[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color])
		
cls([color=#BA2121]"Result[/color][color=#BB6622]**\n**[/color][color=#BA2121]------"[/color])


[color=#008000]**if**[/color] id_[color=#666666]==[/color][color=#666666]999999[/color]:
	[color=#008000]**print**[/color] [color=#BA2121]"You are"[/color], name,[color=#BA2121]", aged "[/color], age, [color=#BA2121]" next year you'll be "[/color], age[color=#666666]+[/color][color=#666666]1[/color], [color=#BA2121]", with user id "[/color], id_, [color=#BA2121]", you are the last user"[/color]	
[color=#008000]**else**[/color]:
	[color=#008000]**print**[/color] [color=#BA2121]"You are"[/color], name,[color=#BA2121]", aged "[/color], age, [color=#BA2121]" next year you'll be "[/color], age[color=#666666]+[/color][color=#666666]1[/color], [color=#BA2121]", with user id "[/color], id_, [color=#BA2121]",the next user is "[/color], (id_ [color=#666666]+[/color] [color=#666666]1[/color])

		

```

---

### Post by ghostdog74 on 2008-10-08
remove all your ( and ) from your while loops and if/else statements, try/catch statements too.

---

### Post by Canis familiaris on 2008-10-08
> **ghostdog74 said:**
> remove all your ( and ) from your while loops and if/else statements, try/catch statements too.

May I know why? Also if possible tell me how to handle the exceptions without try...except :)

---

### Post by ghostdog74 on 2008-10-08
because its not necessary in Python. Part of Python zen philosophy for readability

---

### Post by Canis familiaris on 2008-10-08
> **ghostdog74 said:**
> because its not necessary in Python. Part of Python zen philosophy for readability

But if I remove the try...except statement; then what happens is that if I enter a string instead of number when the program asks for id or age, then the program terminates and thus disqualifying it in this challenge.
If you know any simpler or better way, then please suggest. I would love to learn it. :)

---

### Post by ghostdog74 on 2008-10-08
i didn't ask you to remove try/exception. Anyway, i misread your try/catch block, so just leave it. remove all the ( and ) from you if/else and while loop

---

### Post by Canis familiaris on 2008-10-08
Updated Code
------------

**Changes**
Removed Repitation by usage of functions
Removed the unnessecary cls() function


```
[color=#408080]*#!/usr/bin/python*[/color]
[color=#408080]*#Author: Anurag Panda*[/color]
[color=#408080]*#Functions*[/color]

[color=#008000]**def**[/color] [color=#0000FF]getnumeric[/color](msg, l, u): 
	[color=#008000]**try**[/color]:
		isOK [color=#666666]=[/color] [color=#008000]False[/color]
		
		[color=#008000]**while**[/color](isOK[color=#666666]==[/color][color=#008000]False[/color]):
			val [color=#666666]=[/color] [color=#008000]input[/color](msg)
			[color=#008000]**if**[/color](val[color=#666666]>=[/color]l [color=#AA22FF]**and**[/color] val[color=#666666]<[/color]u):
				isOK[color=#666666]=[/color][color=#008000]True[/color]	
			[color=#008000]**else**[/color]:
				[color=#008000]**print**[/color] [color=#BA2121]"***Illogical Data Entered![/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
						
		[color=#008000]**return**[/color] val
		
			
	[color=#008000]**except**[/color] ([color=#D2413A]**NameError**[/color], [color=#D2413A]**SyntaxError**[/color]):
		[color=#008000]**print**[/color] [color=#BA2121]"***Text entered into Numerical Field[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
		[color=#008000]**return**[/color] getnumeric(msg, l, u)
		
		
[color=#008000]**def**[/color] [color=#0000FF]getname[/color]():
	name[color=#666666]=[/color][color=#008000]raw_input[/color]([color=#BA2121]"Enter Name: "[/color])
	[color=#008000]**while**[/color]([color=#008000]len[/color](name)[color=#666666]==[/color][color=#666666]0[/color] [color=#AA22FF]**or**[/color] name[[color=#666666]0[/color]] [color=#666666]==[/color] [color=#BA2121]' '[/color]):
		[color=#008000]**print**[/color] [color=#BA2121]"***Names can't begin with space or can be empty[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
		name[color=#666666]=[/color][color=#008000]raw_input[/color]([color=#BA2121]"Enter Name: "[/color])
	[color=#008000]**return**[/color] name
	
[color=#408080]*#MAIN*[/color]

name [color=#666666]=[/color] getname()
age [color=#666666]=[/color] getnumeric([color=#BA2121]"Enter Age: "[/color],[color=#666666]1[/color], [color=#666666]150[/color])
id_ [color=#666666]=[/color] getnumeric([color=#BA2121]"Enter ID: "[/color], [color=#666666]1[/color], [color=#666666]1000000[/color])



[color=#008000]**if**[/color] id_[color=#666666]==[/color][color=#666666]999999[/color]:
	[color=#008000]**print**[/color] [color=#BA2121]"You are"[/color], name,[color=#BA2121]", aged "[/color], age, [color=#BA2121]" next year you'll be "[/color], age[color=#666666]+[/color][color=#666666]1[/color], [color=#BA2121]", with user id "[/color], id_, [color=#BA2121]", you are the last user"[/color]	
[color=#008000]**else**[/color]:
	[color=#008000]**print**[/color] [color=#BA2121]"You are"[/color], name,[color=#BA2121]", aged "[/color], age, [color=#BA2121]" next year you'll be "[/color], age[color=#666666]+[/color][color=#666666]1[/color], [color=#BA2121]", with user id "[/color], id_, [color=#BA2121]",the next user is "[/color], (id_ [color=#666666]+[/color] [color=#666666]1[/color])

```

---

### Post by akvino on 2008-10-08
I am starting to find these very interesting. Is it to late to enter?:guitar:

---

### Post by snova on 2008-10-08
I don't think they have an end, so probably not.

---

### Post by tiachopvutru on 2008-10-18
^If that's the case, I want to see if there are anything to fix in my entries (aside from my horrible organization, format, and comments):

[PHP]import sys

def exit (userInput):
    if (userInput == "exit"):
        sys.exit(0)

print "If you want to exit any time, type exit"
name = raw_input("Enter name: ")
exit(name)

#remove all leading and trailing white spaces
name = name.strip()
while (len(name) == 0):
    name = raw_input("Enter name: ")
    name = name.strip()

#Truncate string name if over 20 characters
#If there's a space in an the last nth character where n <= 20, then only truncate
#until the last space.
if (len(name) > 20):
    for ii in xrange(19, -1, -1):
        if name[ii].isspace(): 
            name = name[0:ii]
            break
    else:
        name = name[:20]

age = raw_input("Enter age: ")
exit(age)

#Check if age is larger than 0 or is an integer. If not, then prompt the user to
#reinput the age.
while (type(age) == str):
    try:
        age = int(age)
        if (age < 1):
            age = raw_input ("Age has to be an integer larger than 0: ")
            exit(age)
    except (TypeError, ValueError):
        age = raw_input ("Age has to be an integer larger than 0: ")
        exit(age)

userID = raw_input("Enter User ID: ")
exit(userID)
#Check if User ID is between 1-999999 (inclusive)
while (type(userID) == str):
    try:
        userID = int(userID)
        if (userID < 1 or userID > 999999):
            userID = raw_input ("User ID has to be an integer between 1-999999 (inclusive): ")
            exit(userID)
    except (TypeError, ValueError):
        userID = raw_input ("User ID has to be an integer between 1-999999 (inclusive): ")
        exit(userID)

#check if userID is 999999. If so, nextUserID is none.
if (userID == 999999):
    nextUserID = "none"
else:
    nextUserID = str(userID + 1)

print "You are %s, aged %d next year you will be %d, with user id %d, the next user is %s" %\
        (name, age, age + 1, userID, nextUserID)
[/PHP]

I kinda took TypeError exception from the tutorial linked in the first page, but I'm not sure what it does. I could reproduce ValueError in the interactive mode, but how do I reproduce TypeError?

---

### Post by Nemooo on 2008-10-21
My C entry:

[php]/* Beginner Programming Challenge 2

   Write a program to take a person's forum name, age, forum user id (a
   postive integer equal to or between 1 and 999999). The program should ask
   for each datum individually, and not go to the next unless the previous
   was valid. If there is an error, it must prompt again until it is write
   or the program is halted. The entry "exit" should exit the program at any
   question.

   If all data is entered, it should print a sentence like:
      "You are LaRoza, aged 20 next year you will be 21, with user id
       266234, the next user is 266235." */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/* Clears the buffer. Used after fgets, because fgets appends a '\n' if it 
   doesn't exceed the length of the array (so there needs to be room for '\0').
   strchr returns a pointer to the occurence of '\n' and a NULL pointer if 
   there's no '\n'. If there's not room for a newline the buffer contains 
   letters we want erased. This is done by calling getchar until it reaches
   '\n'. If there is a '\n' it's replaced by a '\0', so the newline isn't
   printed later. */
void clear_buffer(char *input)
{
	char *i;

	i = strchr(input, '\n');

	if(i == NULL)
		while(getchar() != '\n')
			;
	else
		*i = '\0';
}

/* Get the input using fgets. If it's exit, quit the program. Is the string
   empty or is the first character a space return 1 (error) and otherwise 0
   (succes). */
int get_check(char *input, size_t len_arr)
{
	fgets(input, len_arr, stdin);
	clear_buffer(input);

	if(strcmp(input, "exit") == 0) {
		exit(0);
	} else if(input[0] == ' '
	       || input[0] == 10) {
		puts("Invalid input");
		return 1;
	}

	return 0;
}

/* Get name, then age and then ID by calling get_check. If it returns 0
   continue to the next input otherwise call get_check again. After
   succesfully acquiring name, age and ID display the message in the
   specified format. */
int main()
{
	char name[21];
	char age[4];
	char id[7];
	int check;
	int num_age, num_id;

	/* Get name. */
	do {
		printf("What's your name: ");
		check = get_check(name, sizeof(name));
	} while(check != 0);

	/* Get age. */
	do {
		printf("How old are you: ");
		check = get_check(age, sizeof(age));
		/* Convert the age string to a number, so it is easier to check
		   if the input is a valid age print. */
		num_age = atoi(age);

		if(num_age < 1
		|| num_age > 122) {
			puts("Come on. We both know that ain't possible.");
			check = 1;
		}
	} while(check != 0);

	/* Get ID. */
	do {
		printf("What's your user ID: ");
		check = get_check(id, sizeof(id));
		/* Convert the ID string to a number, so it is easier to check
		   if the input is a valid ID and print. */
		num_id = atoi(id);

		if(num_id < 1
		|| num_id > 999999) {
			puts("User IDs must be between 1 and 999999");
			check = 1;
		}
	} while(check != 0);

	/* Print desired output. */
	printf("\nYou are %s, ", name);
	printf("aged %d next year you will be %d, ", num_age, num_age + 1);
	printf("with user id %d, the next user is %d.\n", num_id, num_id + 1);

	return 0;
}[/php]

EDIT: New and better version. It now clears the buffer, if the input's too long and removes the newline character fgets appends.

---

