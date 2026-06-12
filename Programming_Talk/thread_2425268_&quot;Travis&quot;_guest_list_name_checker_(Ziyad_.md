---
title: "&quot;Travis&quot; guest list name checker (Ziyad Yehia Udemy course)"
date: 2019-08-22
forum: Programming Talk
---

### Post by Drone4four on 2019-08-22
I'm taking a Udemy course (not for credit, just for fun) but I would still like to treat this as a homework exercise so for experienced forum members, please do not solve the problem for me. All I am asking is for hints and tips.

The task involves verifying the contents of a list using conditionals. For a full explanation of the purpose of this program and for instructions from the teacher, you can read them in the [README on my GitHub repo](https://github.com/Angeles4four/travis_user_checker_Ziyad_Yehia_Udemy) (second paragraph from the bottom).

I kinda got the program to run. It used to meet the requirements set out by the instructor. But I am now taking the project in a new direction by consolidating the operations into two separate functions (one called ‘main’ and the other called ‘check’). It is extending this script that I am encountering a Name Error and a Type Error.

Here is my script so far:

```
#!/usr/bin/env python3
# This third iteration splits the code into two different functions

def main():
    """
    Initializes the two primary variables and returns them for future use
    """
    guest_list = ["Justin Trudeau", "Joseph Stalin", "Caesar", "Nero",]
    user_name = input("What is your name? Please spell it in full! >>  \n")
    return (guest_list, user_name)


def check(placeholder):
    """
    Verifies the user name input and determines if in guest list
    """
    if user_name in guest_list:
        print(f"Welcome, {user_name}!")
    if user_name not in guest_list:
        print(f"Hi {user_name}, but unfortunately you are not in the guest list.")
        include_proposition = input("Would you like to join us anyways? Please enter a Yes or a No >> \n")
        if include_proposition == ("Yes", "Y", "y"):
            guest_list.append(user_name)
            print(f"Thanks, {user_name}! You've been added. Please enter.")
        if include_proposition == ("No", "N", "n"):
            print("OK! Have a good night then, my friend!")
        else:
            print("Sorry, I didn't get that. Please enter your selection again")


if __name__ == "__main__":
    placeholder = main()
    check(placeholder)

```

Notice at line 13 I pass the `placeholder` variable (which I initialize at the end of the script) below the `if name` conditional.  Here is NameError the traceback:

> 
$ python script3.py
What is your name? Please spell it in full! >>  
Matt
Traceback (most recent call last):
  File "script3.py", line 33, in <module>
    check(placeholder)
  File "script3.py", line 17, in check
    if user_name in guest_list:
NameError: name 'user_name' is not defined


I figure the check() function requires `user_name` and `guest_list` so I tried replacing the `placeholder` as a parameter at line 13 with `guest_list, user_name` which returns a TypeError:

> 
$ python script3.py
What is your name? Please spell it in full! >>  
Matt
Traceback (most recent call last):
  File "script3.py", line 33, in <module>
    check(placeholder)
TypeError: check() missing 1 required positional argument: 'user_name'


Here are my two questions:
[list=1]
[*]How do I call both functions (`main()` and `check()`) properly so as to avoid these tracebacks?
[*]What do you call the Python convention with `if __name__ == "__main__":`? When I Google "if __name__ == "__main__"" there is [a very detailed and thorough Stack Overflow question and answer](https://stackoverflow.com/questions/419163/what-does-if-name-main-do) which explains very clearly how, why and when to use `if __name__ == "__main__":` however it doesn’t actually say what this Python convention is called. So what do you call this?
[/list]

For my future reference, this Udemy instructor Ziyad Yehia calls this the "Travis" application. This is the fourth project under the "Python Datastructures" section. The course is titled "[The Python Bible: Everything You Need to Program in Python](https://www.udemy.com/the-python-bible/)"

---

### Post by norobro on 2019-08-22
Hi Drone4Four


[LIST=1]
[*]guest_list and user_name are local variables in your function main(). You are pass ing a tuple consisting of a list and a string to check(). You need to extract those variables in check() by using assignment statements. Try putting print(placeholder)  as the first line in check().
[*]I do not know if there is a name for it. You've probably seen this page in the docs: [https://docs.python.org/3/library/__main__.html?highlight=__name__](https://docs.python.org/3/library/__main__.html?highlight=__name__)
[/LIST]

---

