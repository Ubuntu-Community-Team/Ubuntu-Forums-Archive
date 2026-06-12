---
title: "Help a beginner,"
date: 2010-10-12
forum: Programming Talk
---

### Post by CaptainMark on 2010-10-12
Hi im teaching myself python just from books for a start (Python programming for the absolute beginner, third edition). I hit a wall and cant understand something, theres one piece of code in a demo program thats not explained in the text, i know its vital because if i remove it the demo script crashes, i just dont like not knowing why its not explained. I know its a lot to ask but let me explain the way i see it.
The next_block function will take the next 7 lines from a text file (trivia.txt) and use them to return values for the question and correct answer etc.
The next_block function will fetch from the text file a number between 1 and 4 which corresponds to the correct answer so correct is assigned a string of say '1', this is returned to the main function and compared to the user answer in line 65.
What i dont understand is why comparing two strings of the same value wont work unless line 34/35 run:
if correct:
       (indent)correct=correct[0]
What exactly does this line do that is so vital, without it the program always thinks the users answer is wrong, i thought it would still compare the strings '1' and '1' and equate to them being the same
Thanks to anyone who dedicated time to helping me out.
EDIT: *** It struck me that it must be something to remove the new-line character from the string but i dont know how it does this ***
Heres the code ```
# Trivia Challenge
# Trivia game that reads a plain text file

import sys

def open_file(file_name, mode):
    """Open a file."""
    try:
        the_file = open(file_name, mode)
    except IOError as e:
        print("Unable to open the file", file_name, "Ending program.\n", e)
        input("\n\nPress the enter key to exit.")
        sys.exit()
    else:
        return the_file

def next_line(the_file):
    """Return next line from the trivia file, formatted."""
    line = the_file.readline()
    line = line.replace("/", "\n")
    return line

def next_block(the_file):
    """Return the next block of data from the trivia file."""
    category = next_line(the_file)
    
    question = next_line(the_file)
    
    answers = []
    for i in range(4):
        answers.append(next_line(the_file))
        
    correct = next_line(the_file)
    if correct:
        correct = correct[0]
        
    explanation = next_line(the_file) 

    return category, question, answers, correct, explanation

def welcome(title):
    """Welcome the player and get his/her name."""
    print("\t\tWelcome to Trivia Challenge!\n")
    print("\t\t", title, "\n")
 
def main():
    trivia_file = open_file("trivia.txt", "r")
    title = next_line(trivia_file)
    welcome(title)
    score = 0

    # get first block
    category, question, answers, correct, explanation = next_block(trivia_file)
    while category:
        # ask a question
        print(category)
        print(question)
        for i in range(4):
            print("\t", i + 1, "-", answers[i])

        # get answer
        answer = input("What's your answer?: ")

        # check answer
        if answer == correct:
            print("\nRight!", end=" ")
            score += 1
        else:
            print("\nWrong.", end=" ")
        print(explanation)
        print("Score:", score, "\n\n")

        # get next block
        category, question, answers, correct, explanation = next_block(trivia_file)

    trivia_file.close()

    print("That was the last question!")
    print("You're final score is", score)
 
main()  
input("\n\nPress the enter key to exit.")

```and heres the text file to do with it```
An Episode You Can't Refuse 
On the Run With a Mammal 
Let's say you turn state's evidence and need to "get on the lamb." If you wait /too long, what will happen? 
You'll end up on the sheep 
You'll end up on the cow 
You'll end up on the goat 
You'll end up on the emu 
1 
A lamb is just a young sheep. 
The Godfather Will Get Down With You Now 
Let's say you have an audience with the Godfather of Soul. How would it be /smart to address him? 
Mr. Richard 
Mr. Domino 
Mr. Brown 
Mr. Checker 
3 
James Brown is the Godfather of Soul. 
That's Gonna Cost Ya 
If you paid the Mob protection money in rupees, what business would you most /likely be insuring? 
Your tulip farm in Holland 
Your curry powder factory in India 
Your vodka distillery in Russian  
Your army knife warehouse in Switzerland 
2 
The Rupee is the standard monetary unit of India. 
Keeping It the Family 
If your mother's father's sister's son was in "The Family," how are you /related to the mob? 
By your first cousin once removed 
By your first cousin twice removed 
By your second cousin once removed 
By your second cousin twice removed 
1 
Your mother's father's sister is her aunt -- and her son is your /mother's first cousin. Since you and your mother are exactly one generation /apart, her first cousin is your first cousin once removed. 
A Maid Man 
If you were to literally launder your money, but didn't want the green in your /bills to run, what temperature should you use? 
Hot 
Warm 
Tepid 
Cold   
4 
According to my detergent bottle, cold is best for colors that might run.
```

---

### Post by Barrucadu on 2010-10-12
```
    if correct:
        correct = correct[0]
```

If a line ('correct') was read successfully, get the first character on the line ('correct[0]').

---

### Post by CaptainMark on 2010-10-13
i see, thank you, its so simple with an explanation

---

