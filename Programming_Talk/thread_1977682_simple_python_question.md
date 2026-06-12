---
title: "simple python question"
date: 2012-05-10
forum: Programming Talk
---

### Post by jpg123 on 2012-05-10
hi, im just trying to understand how to run python programmes thru ubuntu

my programme consists of 

print("Game over")
input("\n\nPress the enter key to exit")

ive made it executable so when i double click on the icon, i get the options

run in terminal
display
cancel
run

when i click on run in terminal a window flashes up and disappears in an instant and when i click run nothing happens. There must be a program i can download to run this file so that a window pops up and displays the words game over and then prompts me to press enter as above. But i dont know where its is.

Any help would be much appreciated. cheers

---

### Post by codemaniac on 2012-05-10
Open a terminal , locate the script and make it executable .
```
chmod +x yourScript.py
./yourScript.py
```

Also include** #!/usr/bin/python** at the beginning of your script .

---

### Post by jpg123 on 2012-05-10
How is that different from from going into properties of the file and marking x in the 'allow executing file as program'?

if i type in the terminal python game_over.py it gives me
Game over


press the enter key to exit.

Im probably being stupid, but im not sure i understand.

---

### Post by 3Miro on 2012-05-10
Open a terminal and then manually run the program in it. This way you can see if you have any error messages.

---

### Post by wojox on 2012-05-10
My favorite ide:
```
sudo apt-get install geany geany-plugins
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217658&stc=1&d=1336672248[/IMG]

---

### Post by jpg123 on 2012-05-10
if i run python game_over.py in the terminal i get
game over


press the enter key to exit( i then press enter)

and this comes on the next line

Traceback (most recent call last):
  File "game_over.py", line 5, in <module>
    input("\n\nPress the enter key to exit.")
  File "<string>", line 0
    
    ^
SyntaxError: unexpected EOF while parsing

I must be getting something basic wrong lol.

---

### Post by codemaniac on 2012-05-10
> **jpg123 said:**
> How is that different from from going into properties of the file and marking x in the 'allow executing file as program'?

if i type in the terminal python game_over.py it gives me
Game over


press the enter key to exit.

Im probably being stupid, but im not sure i understand.

You can turn the execute permissions from GUI also with a few clicks as you did .
The output you are getting is what it should be .What part you did not understand jpg123 .

---

### Post by jpg123 on 2012-05-10
im working from a beginners python book, and i states that the window/terminal should open
then display game over and then prompt me to press enter and then the terminal should close.

Im confused.

---

### Post by codemaniac on 2012-05-10
> **jpg123 said:**
> if i run python game_over.py in the terminal i get
game over


press the enter key to exit( i then press enter)

and this comes on the next line

Traceback (most recent call last):
  File "game_over.py", line 5, in <module>
    input("\n\nPress the enter key to exit.")
  File "<string>", line 0
    
    ^
SyntaxError: unexpected EOF while parsing

I must be getting something basic wrong lol.

Change your source code, use **raw_input** instead of input and run it in the terminal .

---

### Post by jpg123 on 2012-05-10
aha, it worked, thanks guys, you help was in real time, its much appreciated. i had loads of windows open and got a  bit confused. cheers.

---

### Post by Bachstelze on 2012-05-10
The code was probably meant to be run in Python 3. No one uses input() in Python 2.

---

### Post by wojox on 2012-05-10
> **Bachstelze said:**
> The code was probably meant to be run in Python 3. No one uses input() in Python 2.

And print is being used as a function.

---

### Post by prismctg on 2012-05-11
add this code end of the line ```
input()
```

---

