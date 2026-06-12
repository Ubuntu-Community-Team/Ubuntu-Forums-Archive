---
title: "Accessing Global Variables under a Def in Python"
date: 2007-08-04
forum: Programming Talk
---

### Post by marcos.linux on 2007-08-04
Hi, I am a noob at python, I was thinkng of making this python script for my college's exam wich asks you the question and you type the answer and a score will be shown, but I have a problem, I do not know how to make a variable inside a def access a global variable, for example:


> a=100
def question():
     print "question 1"
     ques1=str(raw_input("What is 5+5"))
     if ques1=="10":
        print "Good!"
        print "Current score: " + a
     else:
        print "Wrong! Is 10."
        a=a-1
        print "Current score: " + a
question()

As you can see something is wrong there! Well I get:

UnboundLocalError: local variable 'a' referenced before assignment

Thats where all my doubts starts running, how do I manage to make this work?

Any help would be hugely appreciated!:confused:

EDIT: Yes, I have organized it well under the python file, but the forums seem to align allthe code to the left.

---

### Post by kebes on 2007-08-04
First off, when posting source code, you should use the "code" tags (not "quote") so that code retains indentation.


As for your question, you just use the "global" keyword inside the function that needs access to a variable outside its scope. (You do NOT use the keyword when declaring the variable.

So for instance:
```

a=100
def question():
    **global a**
    print "question 1"
    ques1=str(raw_input("What is 5+5"))
    if ques1=="10":
        print "Good!"
        print "Current score: " + str(a)
    else:
        print "Wrong! Is 10."
        a=a-1
        print "Current score: " + str(a)

question()

```


EDIT:
Note, however, that global variables are usually "bad style"... you should be using function variables wherever possible. For instance:
```


starting_score=100

def question( score ):

    print "question 1"
    ques1=str(raw_input("What is 5+5"))
    if ques1=="10":
        print "Good!"
        print "Current score: " + str(score)
    else:
        print "Wrong! Is 10."
        score=score-1
        print "Current score: " + str(score)

    return score


current_score = starting_score
current_score = question(current_score)

```

---

### Post by pmasiar on 2007-08-04
Why str(score)? use just: 

print  "Current score: ", score

or:

print  "Current score: %i points" % score

Possibly good idea could be to define data structure with questions and correct answers (and scoring program using that structure), so it will be easier to add new tests.

BTW "under a Def" means: "inside a function" :-)

---

### Post by marcos.linux on 2007-08-05
Thanks to all of u! :-D this is has helped me completely.

---

