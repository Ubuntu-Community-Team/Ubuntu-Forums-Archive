---
title: "Can anyone help with my program in BASH"
date: 2012-06-12
forum: Programming Talk
---

### Post by peethagoras on 2012-06-12
Hi there forum!

In my many poor attempts to make a little BASH program, it seems that I am very inexperienced, and thus not at all good at it, (to be polite). I wonder if someone might be kind enough to offer a pointer or two?

I want to enter  any word using the console, and that word is to be converted into a numerical sum according to this rule:

A = 1 B = 2 C = 3 ...... etc to Z = 26.

If anything other than a valid abc letter is entered, it is simply ignored.

If I enter say: ABC the BASH program should add up 1 + 2 + 3 then print on the console "ABC = " 6.

I am going mad just trying to get off the ground.

Is there a better programming language available in Ubuntu?

Many thanks for reading this.

---

### Post by c2tarun on 2012-06-12
> **peethagoras said:**
> Hi there forum!
 
In my many poor attempts to make a little BASH program, it seems that I am very inexperienced, and thus not at all good at it, (to be polite). I wonder if someone might be kind enough to offer a pointer or two?
 
I want to enter any word using the console, and that word is to be converted into a numerical sum according to this rule:
 
A = 1 B = 2 C = 3 ...... etc to Z = 26.
 
If anything other than a valid abc letter is entered, it is simply ignored.
 
If I enter say: ABC the BASH program should add up 1 + 2 + 3 then print on the console "ABC = " 6.
 
I am going mad just trying to get off the ground.
 
Is there a better programming language available in Ubuntu?
 
Many thanks for reading this.
 
 
Posting your code might help us in helping you ;)
 
And regarding programming languages, Ubuntu support many languages. :) if you want you can start with C

---

### Post by buzzingrobot on 2012-06-12
Have you tried the Bash tutorials available on the web?  Search "learning Bash".  And, there's one here on the Forums, too.

Whatever ever language you tackle, you will need to begin by learning the same basic concepts: variables, looping, branching, arrays, objects, etc.  For the purposes of your little program, you'll need to read a word and then parse and test individual characters from it.  Typically, you would find the length of a word, then loop through it, testing each character to see if it is alpha or not.

Those basic tasks are fundamentally the same in any language, but how each language approaches them will differ, and the syntax of the language will vary widely.

Many languages are available in Ubuntu and Linux, including C. C++, Java, Perl ,Python, Ruby, and on and on. It's impossible to pick one for you.  But, I would recommend searching on something like "learning Java" or "beginning C".  Look for sites that are obviously for beginners, not developers looking to adopt a new language. Take your time and see if you are reasonably comfortable with the syntax of the language.  They all take time to gain fluency in.  Pick the language whose syntax is easiest for you to read and understand. Don't pay much attention at all to developers touting their favorite languages. You're looking to learn the basics.

---

### Post by peethagoras on 2012-06-12
Thanks very much for such a speedy response.

I have read through the tutorials (at least those bits which deal with the basics).

I have no experience of running programs under Linux. I assumed Linux commands would perform what I require. Rather like Windows DOS commands. The problem is in getting off the ground. How to begin? Do I write a simple set of instructions in BASH, as a separate file, then use that filename when running the console? In other words, do I call the program by its filename, from within BASH?

If for example, I wanted to input a string of text from the keyboard, and have the program simply echo everything in upper case to the screen, is this easy to do? Will the thing keep waiting for new input when I hit return? Can I do such tasks just using Linuk commands?

I am sorry if I sound thick, and I hope this all makes sense!

Thanks again friend.

---

### Post by bencouve on 2012-06-12
"If for example, I wanted to input a string of text from the keyboard,  and have the program simply echo everything in upper case to the screen,  is this easy to do?"

The answer is yes, pretty easy to do. You need to get yourself a book on shell scripting. I use Unix shell programming (Stephen G Kochan and Patrick H. Wood). A contemporary book on the bash shell would help you loads. Do a search on amazon.com

---

### Post by Vaphell on 2012-06-12
if you want to get into programing, i'd try python if i were you. It's has tons of convenience features that do things for you and more.

in bash:
```
read -p "Enter word: " word
w="${word^^}" #all-caps
sum=0
while [ "$w" ]
do
  # ascii code of first char - 64 => 1-26 range
  i=$(( $( printf "%d" "'${w:0:1}" ) - 64 ))
  (( sum+=i ))
  echo "${w:0:1} ($i)"
  w="${w:1}" # discard first char
done
echo "sum: $sum"
```

```
enter word: diNoSaur
D (4)
I (9)
N (14)
O (15)
S (19)
A (1)
U (21)
R (18)
sum: 101

```

---

### Post by greenpeace on 2012-06-13
> **Vaphell said:**
> if you want to get into programing, i'd try python if i were you. 

+1 for Python... here's an example

```
#!/usr/bin/python

word=raw_input("type your word: ")
sum = 0

for letter in word:
	letter_value = ord(letter.lower())-96 
	if 0 < letter_value < 27: # ignores numbers and punctuation
		sum += letter_value

print "%s = %s" % (word, sum)
```

save as "word2num.py" then run it as:

```
python word2num.py
```

---

