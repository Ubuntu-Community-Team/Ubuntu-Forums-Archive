---
title: "[Beginner] Programming Challenge: 1"
date: 2008-07-31
forum: Programming Talk
---

### Post by LaRoza on 2008-07-31
We have at other times had weekly programming challenges. They, when I read them, seemed to get more advanced as they went because the winner got to choose the next challenge, each one was the idea of a somewhat experienced programmer and sometimes very experienced.

I am not sure how we will have someone choose the next challenge, but we'll figure it out when we get there :-)

There is no time limit either, but I am thinking any interest in this should be apparent within this week.

[size=+1]The Challenge:[/size]
Write a program, in any free language, that prints to the terminal the lyrics to [this song, 99 Bottles of Beer]("http://99-bottles-of-beer.net/lyrics.html").

If you copy anything from that site, it will be obvious, so don't try it, although you may find that site useful for seeing code of many different languages.

[size=+1]Rules:[/size]
Do not copy code, but you can obviously read it :-)

Try not to comment on other submissions. It will be hard to judge changing entries. If you edit your code, post the new version and make it clear there is a new code.

[size=+1]How it will be judged[/size]
Obviously, this is a task that is trivial (one big output statement would work) so the winner will be judged on the following:

[list]
[*] Clean code. Readable code is a must for being a programmer who wishes to possibly interact with others. Some languages can be more readable than others, so it will be judged on the effort of writing clean code, not which language is easier to read by design.
[*] Logical code. Be a programmer, not a code monkey :-)
[*] Commented code. If something is possibly unclear (like an obscure use of math), let the readers know. Do not over comment, and let the code speak for itself whenever you can. Have logical variable names and function names. (Excessive commenting is a minus factor)
[*] Working code. It has to work as it is posted. The codw will be read on the forum, so remember to use this guide to paste code if you don't know how: [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)
[/list]

[size=+1]Hints:[/size]
[list]
[*] When you get to 1 bottle, it is a singular "bottle", whereas all other instances are plural.
[*] Using this challenge to try out a new language brings you bonus points, so please state when you are using the language for the first time if you are.
[/list]

---

### Post by mssever on 2008-07-31
Another hint (or two):

[LIST]
[*]Don't rely too heavily on the programs on that site. Many are poorly-written and a surprising number are incorrect.
[*]The text to print contains another special case that LaRoza didn't mention and that many programs on that website miss. I'll leave you to figure that special case out on your own. :)
[/LIST]

---

### Post by Yuki_Nagato on 2008-07-31
Do criticize.  I probably could have just had one string and then modified it as I went.

[PHP]#!/usr/bin/python
#
# Throat Saver ver. 1
# Sings the song "99 Bottles of Beer" for you.

beers = 99

for x in range(beers + 1):
	
	# Grammatical Specifications
	if beers == 0:
		print "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.\n"
		
	elif beers == 1:
		print "1 bottle of beer on the wall, 1 bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n"
	
	elif beers == 2:
		print "2 bottles of beer on the wall, 2 bottles of beer.\nTake one down and pass it around, 1 bottle of beer on the wall.\n"
		
	# Normal Use
	else:
		print beers, " bottles of beer on the wall, ", beers, " bottles of beer.\nTake one down and pass it around, ", (beers - 1), " bottles of beer on the wall.\n"
	
	# Take it down
	beers = beers - 1[/PHP]

---

### Post by Joeb454 on 2008-07-31
I thought I'd include the C version :)

It's probably rubbish, it's been a while since I did any programming [PHP]#include <stdio.h>

main()
{
        int i = 99;

        for(i; i > 1; i--)
        {
                printf("%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottles of beer on the wall.\n\n", i, i, i-1);

                if(i == 2)
                {
                        printf("%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottle of beer on the wall.\n\n", i, i, i-1);
                }
        }

        printf("1 bottle of beer on the wall, 1 bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n\n");
        printf("No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.\n\n");

        //I was lazy with the last 2. Sorry :)

        return 0;
}[/PHP]

---

### Post by stevescripts on 2008-07-31
LaRoza,

Nice choice for a first beginner's challenge!

Steve

---

### Post by tuxerman on 2008-07-31
I'm new to this forum.. I saw this today morning.. and it was great to break the ice :)

[PHP]// Code done in C++
// Bottles of Beer :)

#include<iostream.h>

int main()
{
 
 int beers=99;                       //Thats the number of beer bottles on the wall

 for(beers=99;beers>=0;beers--)     //Keep decrememnting the number of beer bottles we have, till it equals zero
 {
  //number-specific corrections to be made:
  
  if(beers==1)
  {
   cout<<"1 bottle of beer on the wall, 1 bottle of beer.\n";
   cout<<"Take one down and pass it around, no more bottles of beer on the wall.\n\n";
  }
  
  else if(beers==2)
  {
   cout<<"2 bottles of beer on the wall, 2 bottles of beer.\n";
   cout<<"Take one down and pass it around, 1 more bottle of beer on the wall.\n\n";
  }
  
  else if(beers==0)
  {
   cout<<"No more bottles of beer on the wall, no more bottles of beer.\n";
   cout<<"Go to the store and buy some more, 99 bottles of beer on the wall.\n\n";
  }
  
  // for all other numbers:
  else
  {  
   cout<<beers<<" bottles of beer on the wall, "<<beers<<" bottles of beer.\n";
   cout<<"Take one down and pass it around, "<<(beers-1)<<" bottles of beer on the wall.\n\n";
  }
 }                                   // end of the 'for' loop
return 0;                           //Since main was declared 'int'
}
[/PHP]

---

### Post by TreeFinger on 2008-07-31
I'll submit my answer tomorrow. I am pretty sure I can do it :)

---

### Post by Alasdair on 2008-07-31
Here's my submission. It features gratuitous abuse of the format macro. There is a similar submission on the site that shows some really crazy use of the format macro which I don't understand.

```
(defun bottles ()
  (format t
	       "~:{~A bottl~
                es of beer ~
                on the wall~
                , ~A bottle~
               s of beer.~%~
              Take one down a~
            nd pass it around, ~
         ~A bottles of beer on the ~
       wall.~%~%~}2 bottles of beer o~
      n the wall, 2 bottles of beer.~%~
      Take one down and pass it around~
      , 1 bottle of beer on the wall.~
      ~%~%1 bottle of beer on the wall~
      , 1 bottle of beer.~%Take one do~
      wn and pass it around, no more b~
      ottles of beer on the wall.~%~%~
      No more bottles of beer on the w~
      all, no more bottles of beer.~%~
      Go to the store and buy some mor~
      e, 99 bottles of beer on the wall."
      ;-------------------------------;
      ;       __   __  __  __         ;
      ;      |__| |_  |_  |__|        ;
      ;      |__| |__ |__ |  \        ;
      ;                               ;
      ;-------------------------------;
      ;  +-------+---------+-------+  ;
      ;  |       |         |       |  ;
      ;  |       |         |       |  ;
      ;  |       |         |       |  ;
      ;  +-------+---------+-------+  ;
      ;_______________________________;
      (loop for i from 99 downto 3
	 collect (list i i (1- i)))))
```

---

### Post by Sinkingships7 on 2008-07-31
LaRoza, you're a wonderful person. You know that? I've hoped someone would do something like this. It's perfect for me, 'cause when the first challenges were posted on this forum, I wasn't good enough to do them. And now that I am, I don't want to because the competition is gone. So, here it goes:

[B]EDIT: Updated code to fix a formatting problem
EDIT2: Updated code to fix another formatting problem[/B]
[PHP]
/* Prints the lyrics to "99 Bottles of Beer on The Wall" */

#include <stdio.h>

/* FUNCTIONS PROTOTYPES */
void give_lyrics(int);

int main(){
    int bottles;

    for (bottles = 99; bottles >= 1; bottles--){
        give_lyrics(bottles);
    }

    printf("No more bottles of beer on the wall, no more bottles of beer.\n"
           "Go to the store and buy some more, 99 bottles of beer on the wall.\n");
    
    getchar();       
    return 0;
}

/* FUNCTIONS */
void give_lyrics(int bottles){
     char *arry = malloc(8);
     arry = "bottles";
     if (bottles == 2){
        arry = "bottle";
     }
     if (bottles > 1){
        printf("%i bottles of beer on the wall, %i bottles of beer.\n"
               "Take one down, pass it around, %i %s of beer on the wall\n\n", 
               bottles, bottles, bottles - 1, arry);
     }
     else{
        printf("%i bottle of beer on the wall, %i bottle of beer.\n"
               "Take one down, pass it around, no more bottles of beer on the wall\n\n", 
               bottles, bottles);
     }
}  
[/PHP]

---

### Post by skeeterbug on 2008-07-31
Compact version (with no comments) in ruby I did years ago (code that won had to be smallest in size).

```

b=" bottles of beer"
w=" on the wall"
99.downto 1 do|x|
puts"#{x}#{b}#{w}, #{x}#{b}."
b=b.delete"s"if x<3
print"Take one down and pass it around, #{x-1}#{b}#{w}.\n\n"if x>1
end 
puts"Go to the store and buy some more, 99 bottles of beer#{w}."

```

---

### Post by CptPicard on 2008-07-31
An infinite lazy list in Clojure:

```


(defn beer [n]
  
  (defn beerstring [x, initcap]
    (cond (= x 0) (str (if initcap "No" "no") " more bottles")
	  (= x 1) "1 bottle"
	  true (str x " bottles")))
  
  (defn beer-internal [y]
    (lazy-cons
     (str (beerstring y true) " of beer on the wall, " (beerstring y false) " of beer\n"
	  (if (= y 0)
	    (str "Go to the store and buy some more, " (beerstring n false) " of beer on the wall\n")
	    (str "Take one down and pass it around, " (beerstring (- y 1) false) " of beer on the wall\n")))
     (if (> y 0) 
       (beer-internal (- y 1))
       (beer-internal n))))

  (beer-internal n))

```

(The newlines don't work right but what the heck)

With this list you can (take) as many bottles as you like, pass around the lazy list, and there's as much beer as anybody can drink...

---

### Post by PandaGoat on 2008-08-01
[php]
#include <stdio.h>
#include <stdlib.h>

char* itoa(int n){char* _n = malloc(3); sprintf(_n, "%i", n); return _n;};
int main()
{
    int i;
    for(i = 99; i >= 0; i--)
    {
        printf("%s %s of beer on the wall, %s %s of beer. \n%s %s %s of beer on the wall.\n\n",
                i==0?"No more":itoa(i), i==1?"bottle":"bottles",
                i==0?"no more":itoa(i), i==1?"bottle":"bottles",
                i==0?"Go to the store and buy some more,":"Take one down and pass it around,",
                i==0?"99":i==1?"no more":itoa(i-1), i==2?"bottle":"bottles");
    }
    return 0;
}
[/php]

---

### Post by Exershio on 2008-08-01
First program using Python. :)

[php]#!/usr/bin/python

def main():
	bottles = 99
	
	# Let's keep singing forever!
	while 1:
	
		if bottles > 2:
			print str(bottles) + " bottles of beer on the wall, " + str(bottles) + " bottles of beer."
			bottles -= 1
			print "Take one down and pass it around, " + str(bottles) + " bottles of beer on the wall."
			
		elif bottles == 2:
			print str(bottles) + " bottles of beer on the wall, " + str(bottles) + " bottles of beer."
			bottles -= 1
			print "Take one down and pass it around, " + str(bottles) + " bottle of beer on the wall."
			
		elif bottles == 1:
			print str(bottles) + " bottle of beer on the wall, " + str(bottles) + " bottle of beer."
			bottles -= 1
			print "Take one down and pass it around, no more bottles of beer on the wall."
			
		elif bottles == 0:
			print "No more bottles of beer on the wall, no more bottles of beer."
			bottles = 99
			print "Go to the store and buy some more, " + str(bottles) + " bottles of beer on the wall."

if __name__ == '__main__':
	main()[/php]

---

### Post by Maveric3477 on 2008-08-01
Hi all, a really simple version done in Common Lisp. I tried to make it as clear as possible, which I think I achieved. However, It's probably not very Lisp like. 

It works on my computer (SBCL + Slime), so hopefully shouldn't be a problem on yours.

```

;;;Common Lisp version by Maveric
;;;;I've tried to make this as simple, and easy to follow as possible.
;;;;I decided to tac the last sentence (Go to the store...) in the main loop, 
;;;;As I think it looks slightly neater.

(defun beer-print (num)
  (if (>= num 2)
      (format t "~R bottles of beer on the wall,~
                 ~:*~r bottles of beer. ~1% Take one down and pass it around,~
                 ~r bottles of beer on the wall.~2% " num (- num 1))
      (format t "~r bottle of beer on the wall, ~:*~r bottle of beer.~
                 ~1% Take one down and pass it around,~
                 no bottles of beer on the wall ~2%" num)))

(defun main-loop ()
  (loop :for x :from 99 :downto 1 :do (beer-print x))
  (format t "No more bottles of beer on the wall, no more bottles of beer.~
             ~1%Go to the store and buy some more, 99 bottles of beer on the wall."))


```

---

### Post by aktiwers on 2008-08-01
I am just starting to learn python, thanks for a fun challenge.
(have no idea if this is the correct "style of writing python code, but it works) :)

[php]
#!/usr/bin/python
#
# Drink drink! ver. 0.1
# "99 Bottles of Beer". 

###################################
# This is the lyrics of the song #
#################################

# This is the general used lyrics
a = "bottles of beer on the wall, "
b = "bottles of beer."
c = "Take one down and pass it around," 
d = "bottles of beer on the wall."

# This is the lyrics used at the end of the song
# Note that a1 and b1 is == to a and b just that we are singing about 1 bottle
a1 = "bottle of beer on the wall, "
b1 = "bottle of beer."
e = "Take one down and pass it around, no more bottles of beer on the wall. \n"
f = "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.\n"

############################################
# This is the loop that produces the song #
##########################################
n = 99

while n >= 3:
    n = n-1
    print n, a, n, b, "\n" , c, n-1, d, "\n\n"
if n == 2:
    print n-1, a1, n-1, b1, "\n" , e
    print f
[/php]

---

### Post by schauerlich on 2008-08-01
for loops were about as far as I got at my last attempt learning to program, so this is a good first challenge for me.


[php]
#/usr/bin/python

for i in range(99,1,-1) :
	print i, "bottles of beer on the wall,\n", i, "bottles of beer,\nTake one down, pass it around,"
	i = i - 1
	if i > 1 :
		print i, "bottles of beer on the wall.\n"
	else :
		print i, "bottle of beer on the wall.\n"

# Kind of cheated here, but oh well. Assigning parts of the sentence to variables would have eliminated the verbosity of this last line as the cost of readability (to me, at least)
print "1 bottle of beer on the wall,\n1 bottle of beer,\nTake one down, pass it around,\nno more bottles of beer on the wall.\n"
print "No more bottles of beer on the wall,\nno more bottles of beer.\nGo to the store and buy some more,\n99 bottles of beer on the wall."
[/php]

---

### Post by lordhaworth on 2008-08-01
Here it is in Fortran90, though im not with my ubuntu comp at the mo (But cant wait either) so havnt compiled it, I really should have it working first time, but you never know there may be that annoying spelling error or something. 
I like this whole idea of programming challenges I've not come across (or have turned up too late) for any previous ones. I'll try and keep up with these

```
PROGRAM 99_Bottles_Of_Beer

	IMPLICIT NONE

	INTEGER	:: Bottles = 99


	!Do loop to print the bulk of lines where grammar is constant
	DO WHILE (Bottles > 2)
		PRINT *, Bottles, "Bottles Of Beer On The Wall", Bottles, "Bottles Of Beer"
		Bottles = Bottles - 1
		PRINT *, "Take One Down And Pass It Around", Bottles, "Bottles Of Beer On The Wall"
	END DO 

	!If statement to print the other grammatical cases
	IF (Bottles == 2) THEN
		PRINT *, Bottles, "Bottles Of Beer On The Wall", Bottles, "Bottles Of Beer"
		Bottles = Bottles - 1
		PRINT *, "Take One Down And Pass It Around", Bottles, "Bottle Of Beer On The Wall"

	ELSE IF ( Bottles == 1) THEN	
		PRINT *, Bottles, "Bottle Of Beer On The Wall", Bottles, "Bottle Of Beer"
		Bottles = Bottles - 1
		PRINT *, "Take One Down And Pass It Around No More Bottles Of Beer On The Wall"
	
	ELSE IF (Bottles == 0) THEN
		PRINT *, "No more bottles of beer on the wall, no more bottles of beer"
		Bottles = 99
		PRINT *, "Go To The Store And Buy Some More", Bottles, "Bottles Of Beer On The Wall"
	END IF

END PROGRAM

```

---

### Post by ghostdog74 on 2008-08-01
```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html | awk '/<p>/{gsub("<br>","\n");gsub(" *<[^>]+>","");print}'

```

---

### Post by lordhaworth on 2008-08-01
> wget -q -O - [http://99-bottles-of-beer.net/lyrics.html](http://99-bottles-of-beer.net/lyrics.html) | awk '/<p>/{gsub("<br>","\n");gsub(" *<[^>]+>","");print}'

Lols - Very Good!

---

### Post by schauerlich on 2008-08-01
> **ghostdog74 said:**
> ```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html | awk '/<p>/{gsub("<br>","\n");gsub(" *<[^>]+>","");print}'

```

+1 for cleverness, whether you're eligible in the competition or not. :D

---

### Post by nvteighen on 2008-08-01
My first Python program! (Yes, believe me despite the dictionary with a tuple inside...)

**Update**: As I'm a C guy, I felt forced to refactor the code a bit and make it even more structured as I could!

[PHP]
#!/usr/bin/python

def choose(i):
    special = {0 : ("no more", "bottles"), 1 : ("1", "bottle")}
    if i not in special:
        modulo = (i, "bottles")
    else:
        modulo = special[i]
    return "%s %s" % modulo
    
b = 99
for i in range(b, -1, -1):
    print "%s of beer on the wall, %s of beer." % (choose(i).capitalize(), 
    choose(i))
    if i > 0:
        print "Take one down and pass it around,", choose(i - 1),
    else:
        print "Go to the store and buy some more,", choose(b),
    print "of beer on the wall.\n"
[/PHP]

---

### Post by Reiger on 2008-08-01
I like the Haskell version they have... a lot.

---

### Post by Titan8990 on 2008-08-01
Thanks for the challenge. Here is what I got:

[PHP]#!/usr/bin/python

beerCount = 99

while beerCount > -1:
	if beerCount == 0:
		print "No more bottles of beer on the wall.\n" "No more bottles of beer.\n" "Go to the store and buy some more, 99 bottles of beer on the wall.\n"
	elif beerCount == 1:
		print beerCount, "bottle of beer on the wall.\n", beerCount, "bottle of beer.\n", "Take one down, pass it around,", beerCount, "bottle of beer on the wall.\n"
	else:	
		print beerCount, "bottles of beer on the wall.\n", beerCount, "bottles of beer.\n", "Take one down, pass it around,", beerCount, "bottles of beer on the wall.\n"
	beerCount = beerCount - 1[/PHP]

I took a a little formating advice from Reiger. I don't think I was missing any spaces, just capitalization and periods. Also, each verse did begin seperated by a blank line. 

> * You should decrement the beerCount before 'passing it around' 

I don't understand what you mean here so I am just going to post my output:

```
jordan@einstein:~$ ./UbuntuChallenge
99 bottles of beer on the wall.
99 bottles of beer.
Take one down, pass it around, 99 bottles of beer on the wall.

98 bottles of beer on the wall.
98 bottles of beer.
Take one down, pass it around, 98 bottles of beer on the wall.

97 bottles of beer on the wall.
97 bottles of beer.
Take one down, pass it around, 97 bottles of beer on the wall.

96 bottles of beer on the wall.
96 bottles of beer.
Take one down, pass it around, 96 bottles of beer on the wall.

95 bottles of beer on the wall.
95 bottles of beer.
Take one down, pass it around, 95 bottles of beer on the wall.

94 bottles of beer on the wall.
94 bottles of beer.
Take one down, pass it around, 94 bottles of beer on the wall.

93 bottles of beer on the wall.
93 bottles of beer.
Take one down, pass it around, 93 bottles of beer on the wall.

92 bottles of beer on the wall.
92 bottles of beer.
Take one down, pass it around, 92 bottles of beer on the wall.

91 bottles of beer on the wall.
91 bottles of beer.
Take one down, pass it around, 91 bottles of beer on the wall.

90 bottles of beer on the wall.
90 bottles of beer.
Take one down, pass it around, 90 bottles of beer on the wall.

89 bottles of beer on the wall.
89 bottles of beer.
Take one down, pass it around, 89 bottles of beer on the wall.

88 bottles of beer on the wall.
88 bottles of beer.
Take one down, pass it around, 88 bottles of beer on the wall.

87 bottles of beer on the wall.
87 bottles of beer.
Take one down, pass it around, 87 bottles of beer on the wall.

86 bottles of beer on the wall.
86 bottles of beer.
Take one down, pass it around, 86 bottles of beer on the wall.

85 bottles of beer on the wall.
85 bottles of beer.
Take one down, pass it around, 85 bottles of beer on the wall.

84 bottles of beer on the wall.
84 bottles of beer.
Take one down, pass it around, 84 bottles of beer on the wall.

83 bottles of beer on the wall.
83 bottles of beer.
Take one down, pass it around, 83 bottles of beer on the wall.

82 bottles of beer on the wall.
82 bottles of beer.
Take one down, pass it around, 82 bottles of beer on the wall.

81 bottles of beer on the wall.
81 bottles of beer.
Take one down, pass it around, 81 bottles of beer on the wall.

80 bottles of beer on the wall.
80 bottles of beer.
Take one down, pass it around, 80 bottles of beer on the wall.

79 bottles of beer on the wall.
79 bottles of beer.
Take one down, pass it around, 79 bottles of beer on the wall.

78 bottles of beer on the wall.
78 bottles of beer.
Take one down, pass it around, 78 bottles of beer on the wall.

77 bottles of beer on the wall.
77 bottles of beer.
Take one down, pass it around, 77 bottles of beer on the wall.

76 bottles of beer on the wall.
76 bottles of beer.
Take one down, pass it around, 76 bottles of beer on the wall.

75 bottles of beer on the wall.
75 bottles of beer.
Take one down, pass it around, 75 bottles of beer on the wall.

74 bottles of beer on the wall.
74 bottles of beer.
Take one down, pass it around, 74 bottles of beer on the wall.

73 bottles of beer on the wall.
73 bottles of beer.
Take one down, pass it around, 73 bottles of beer on the wall.

72 bottles of beer on the wall.
72 bottles of beer.
Take one down, pass it around, 72 bottles of beer on the wall.

71 bottles of beer on the wall.
71 bottles of beer.
Take one down, pass it around, 71 bottles of beer on the wall.

70 bottles of beer on the wall.
70 bottles of beer.
Take one down, pass it around, 70 bottles of beer on the wall.

69 bottles of beer on the wall.
69 bottles of beer.
Take one down, pass it around, 69 bottles of beer on the wall.

68 bottles of beer on the wall.
68 bottles of beer.
Take one down, pass it around, 68 bottles of beer on the wall.

67 bottles of beer on the wall.
67 bottles of beer.
Take one down, pass it around, 67 bottles of beer on the wall.

66 bottles of beer on the wall.
66 bottles of beer.
Take one down, pass it around, 66 bottles of beer on the wall.

65 bottles of beer on the wall.
65 bottles of beer.
Take one down, pass it around, 65 bottles of beer on the wall.

64 bottles of beer on the wall.
64 bottles of beer.
Take one down, pass it around, 64 bottles of beer on the wall.

63 bottles of beer on the wall.
63 bottles of beer.
Take one down, pass it around, 63 bottles of beer on the wall.

62 bottles of beer on the wall.
62 bottles of beer.
Take one down, pass it around, 62 bottles of beer on the wall.

61 bottles of beer on the wall.
61 bottles of beer.
Take one down, pass it around, 61 bottles of beer on the wall.

60 bottles of beer on the wall.
60 bottles of beer.
Take one down, pass it around, 60 bottles of beer on the wall.

59 bottles of beer on the wall.
59 bottles of beer.
Take one down, pass it around, 59 bottles of beer on the wall.

58 bottles of beer on the wall.
58 bottles of beer.
Take one down, pass it around, 58 bottles of beer on the wall.

57 bottles of beer on the wall.
57 bottles of beer.
Take one down, pass it around, 57 bottles of beer on the wall.

56 bottles of beer on the wall.
56 bottles of beer.
Take one down, pass it around, 56 bottles of beer on the wall.

55 bottles of beer on the wall.
55 bottles of beer.
Take one down, pass it around, 55 bottles of beer on the wall.

54 bottles of beer on the wall.
54 bottles of beer.
Take one down, pass it around, 54 bottles of beer on the wall.

53 bottles of beer on the wall.
53 bottles of beer.
Take one down, pass it around, 53 bottles of beer on the wall.

52 bottles of beer on the wall.
52 bottles of beer.
Take one down, pass it around, 52 bottles of beer on the wall.

51 bottles of beer on the wall.
51 bottles of beer.
Take one down, pass it around, 51 bottles of beer on the wall.

50 bottles of beer on the wall.
50 bottles of beer.
Take one down, pass it around, 50 bottles of beer on the wall.

49 bottles of beer on the wall.
49 bottles of beer.
Take one down, pass it around, 49 bottles of beer on the wall.

48 bottles of beer on the wall.
48 bottles of beer.
Take one down, pass it around, 48 bottles of beer on the wall.

47 bottles of beer on the wall.
47 bottles of beer.
Take one down, pass it around, 47 bottles of beer on the wall.

46 bottles of beer on the wall.
46 bottles of beer.
Take one down, pass it around, 46 bottles of beer on the wall.

45 bottles of beer on the wall.
45 bottles of beer.
Take one down, pass it around, 45 bottles of beer on the wall.

44 bottles of beer on the wall.
44 bottles of beer.
Take one down, pass it around, 44 bottles of beer on the wall.

43 bottles of beer on the wall.
43 bottles of beer.
Take one down, pass it around, 43 bottles of beer on the wall.

42 bottles of beer on the wall.
42 bottles of beer.
Take one down, pass it around, 42 bottles of beer on the wall.

41 bottles of beer on the wall.
41 bottles of beer.
Take one down, pass it around, 41 bottles of beer on the wall.

40 bottles of beer on the wall.
40 bottles of beer.
Take one down, pass it around, 40 bottles of beer on the wall.

39 bottles of beer on the wall.
39 bottles of beer.
Take one down, pass it around, 39 bottles of beer on the wall.

38 bottles of beer on the wall.
38 bottles of beer.
Take one down, pass it around, 38 bottles of beer on the wall.

37 bottles of beer on the wall.
37 bottles of beer.
Take one down, pass it around, 37 bottles of beer on the wall.

36 bottles of beer on the wall.
36 bottles of beer.
Take one down, pass it around, 36 bottles of beer on the wall.

35 bottles of beer on the wall.
35 bottles of beer.
Take one down, pass it around, 35 bottles of beer on the wall.

34 bottles of beer on the wall.
34 bottles of beer.
Take one down, pass it around, 34 bottles of beer on the wall.

33 bottles of beer on the wall.
33 bottles of beer.
Take one down, pass it around, 33 bottles of beer on the wall.

32 bottles of beer on the wall.
32 bottles of beer.
Take one down, pass it around, 32 bottles of beer on the wall.

31 bottles of beer on the wall.
31 bottles of beer.
Take one down, pass it around, 31 bottles of beer on the wall.

30 bottles of beer on the wall.
30 bottles of beer.
Take one down, pass it around, 30 bottles of beer on the wall.

29 bottles of beer on the wall.
29 bottles of beer.
Take one down, pass it around, 29 bottles of beer on the wall.

28 bottles of beer on the wall.
28 bottles of beer.
Take one down, pass it around, 28 bottles of beer on the wall.

27 bottles of beer on the wall.
27 bottles of beer.
Take one down, pass it around, 27 bottles of beer on the wall.

26 bottles of beer on the wall.
26 bottles of beer.
Take one down, pass it around, 26 bottles of beer on the wall.

25 bottles of beer on the wall.
25 bottles of beer.
Take one down, pass it around, 25 bottles of beer on the wall.

24 bottles of beer on the wall.
24 bottles of beer.
Take one down, pass it around, 24 bottles of beer on the wall.

23 bottles of beer on the wall.
23 bottles of beer.
Take one down, pass it around, 23 bottles of beer on the wall.

22 bottles of beer on the wall.
22 bottles of beer.
Take one down, pass it around, 22 bottles of beer on the wall.

21 bottles of beer on the wall.
21 bottles of beer.
Take one down, pass it around, 21 bottles of beer on the wall.

20 bottles of beer on the wall.
20 bottles of beer.
Take one down, pass it around, 20 bottles of beer on the wall.

19 bottles of beer on the wall.
19 bottles of beer.
Take one down, pass it around, 19 bottles of beer on the wall.

18 bottles of beer on the wall.
18 bottles of beer.
Take one down, pass it around, 18 bottles of beer on the wall.

17 bottles of beer on the wall.
17 bottles of beer.
Take one down, pass it around, 17 bottles of beer on the wall.

16 bottles of beer on the wall.
16 bottles of beer.
Take one down, pass it around, 16 bottles of beer on the wall.

15 bottles of beer on the wall.
15 bottles of beer.
Take one down, pass it around, 15 bottles of beer on the wall.

14 bottles of beer on the wall.
14 bottles of beer.
Take one down, pass it around, 14 bottles of beer on the wall.

13 bottles of beer on the wall.
13 bottles of beer.
Take one down, pass it around, 13 bottles of beer on the wall.

12 bottles of beer on the wall.
12 bottles of beer.
Take one down, pass it around, 12 bottles of beer on the wall.

11 bottles of beer on the wall.
11 bottles of beer.
Take one down, pass it around, 11 bottles of beer on the wall.

10 bottles of beer on the wall.
10 bottles of beer.
Take one down, pass it around, 10 bottles of beer on the wall.

9 bottles of beer on the wall.
9 bottles of beer.
Take one down, pass it around, 9 bottles of beer on the wall.

8 bottles of beer on the wall.
8 bottles of beer.
Take one down, pass it around, 8 bottles of beer on the wall.

7 bottles of beer on the wall.
7 bottles of beer.
Take one down, pass it around, 7 bottles of beer on the wall.

6 bottles of beer on the wall.
6 bottles of beer.
Take one down, pass it around, 6 bottles of beer on the wall.

5 bottles of beer on the wall.
5 bottles of beer.
Take one down, pass it around, 5 bottles of beer on the wall.

4 bottles of beer on the wall.
4 bottles of beer.
Take one down, pass it around, 4 bottles of beer on the wall.

3 bottles of beer on the wall.
3 bottles of beer.
Take one down, pass it around, 3 bottles of beer on the wall.

2 bottles of beer on the wall.
2 bottles of beer.
Take one down, pass it around, 2 bottles of beer on the wall.

1 bottle of beer on the wall.
1 bottle of beer.
Take one down, pass it around, 1 bottle of beer on the wall.

No more bottles of beer on the wall.
No more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall.
```

---

### Post by Reiger on 2008-08-01
I'm not sure; as I don't know Python but intuitively I'd say your program has a few subtle 'formatting' issues?

* Missing spaces (but that could be my lack of Python, as I see others with the same thing?)
* Missing dots (.) at the end of a setence
* Missing comma's and newlines instead of comma's
* 'take' should be 'Take'
* You should decrement the beerCount before 'passing it around' ;-)
* Each verse is separated by a blank line ;-)

---

### Post by Wybiral on 2008-08-01
Generates the song line-by-line

```

[color=#008000]**def**[/color] [color=#0000FF]song[/color](n):
    bob [color=#666666]=[/color] [color=#008000]**lambda**[/color] x: [color=#BA2121]"[/color][color=#BB6688]**%(x)s**[/color][color=#BA2121] [/color][color=#BB6688]**%(bottles)s**[/color][color=#BA2121] of beer"[/color] [color=#666666]%[/color] {
        [color=#BA2121]"x"[/color]: x [color=#008000]**if**[/color] x [color=#666666]>[/color] [color=#666666]0[/color] [color=#008000]**else**[/color] [color=#BA2121]"no more"[/color],
        [color=#BA2121]"bottles"[/color]: [color=#BA2121]"bottle"[/color] [color=#008000]**if**[/color] x [color=#666666]==[/color] [color=#666666]1[/color] [color=#008000]**else**[/color] [color=#BA2121]"bottles"[/color]}
    otw [color=#666666]=[/color] [color=#008000]**lambda**[/color] x: [color=#BA2121]"[/color][color=#BB6688]**%(b)s**[/color][color=#BA2121] on the wall, [/color][color=#BB6688]**%(b)s**[/color][color=#BA2121]."[/color] [color=#666666]%[/color] [color=#008000]dict[/color](b[color=#666666]=[/color]bob(x))
    tod [color=#666666]=[/color] [color=#008000]**lambda**[/color] x: [color=#BA2121]"Take one down, pass it around, [/color][color=#BB6688]**%s**[/color][color=#BA2121] on the wall."[/color] [color=#666666]%[/color] bob(x)
    [color=#008000]**for**[/color] i [color=#AA22FF]**in**[/color] [color=#008000]xrange[/color](n, [color=#666666]0[/color], [color=#666666]-[/color][color=#666666]1[/color]):
        [color=#008000]**yield**[/color] otw(i)
        [color=#008000]**yield**[/color] tod(i [color=#666666]-[/color] [color=#666666]1[/color])

[color=#008000]**for**[/color] line [color=#AA22FF]**in**[/color] song([color=#666666]99[/color]):
    [color=#008000]**print**[/color] line

```

The end of the song is really actually really sad though...

---

### Post by the7erm on 2008-08-01
```

for (b=99;b>0;b--) {
	word = 'bottle'
	if (b>1) {
		word += "s"
	}
	document.write(b+" "+word+" of beer on the wall, "+b+" "+word+" of beer.<br />Take one down and pass it around, "+(b-1)+" "+word+" of beer on the wall.<br /><br />");
}

document.write("No more bottles of beer on the wall, no more bottles of beer.<br />Go to the store and buy some more, 99 bottles of beer on the wall.")

```
EDIT
```

for (b=99;b>0;b--) {
	word = 'bottle'
	if (b>1) {
		word += "s"
		b2 = b-1
		if (b2>0) {
			phrase = b2 + " bottle"
			if (b2 > 1) {
				phrase += "s"
			}
		}
	} else {
		phrase = "no more bottles"
	}
	document.write(b+" "+word+" of beer on the wall, "+b+" "+word+" of beer.<br />Take one down and pass it around, "+phrase+" of beer on the wall.<br /><br />");
}

document.write("No more bottles of beer on the wall, no more bottles of beer.<br />Go to the store and buy some more, 99 bottles of beer on the wall.")

```

---

### Post by mvoncken on 2008-08-01
Extra self-imposed challenge: use generator-expressions ; no if/then ;no real loops. 

[php]
#!/usr/bin/python 
#extra self-imposed challenge: use generators ; no if/then ;no real loops.
#

def bottles(i):
    return {0:"No more bottles",1:"1 bottle",-1:"99 bottles"}.get(i,"%s bottles" % i)

template = """
%s of beer on the wall, %s of beer.
%s, %s of beer on the wall.
"""

print "".join((template %
    ( bottles(i), bottles(i).lower(),
     {0:"Go to the store and buy some more"}.get(i,"Take one down and pass it around"),
     bottles(i - 1).lower()
    ))
    for i in xrange(99,-1,-1))
[/php]
@aktiwers : Please give your variables real names, a,b,c is not very descriptive ,exception : i as the default counter is a convention.

Edit : bugfix for a special case I missed.

Edit 2: Special cases are hard..

This was my 1st version and it didn't need any bugfixes , much more readable, but i guess it's against the spirit of the challenge.
[php]
#!/usr/bin/python 

template = """
%(num)s bottles of beer on the wall, %(num)s bottles of beer.
Take one down and pass it around, %(nextnum)s bottles of beer on the wall.
"""

print "".join((template % {"num":i,"nextnum":i - 1}) for i in xrange(99,2,-1))

#special cases? easy:
print """2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around, 1 bottle of beer on the wall.

1 bottle of beer on the wall, 1 bottle of beer.
Take one down and pass it around, no more bottles of beer on the wall.

No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."""
[/php]

---

### Post by arsenic23 on 2008-08-01
**Hahaha -this doesn't work right!  What's wrong with me.  Fixed version on down the thread.**

```
#!/usr/bin/env python

beers=99
wall="on the wall"
while beers >= 0:
	if beers == 0:
		print "We ain't got no beer."
		break
	if beers > 1: bottles=str(beers)+" bottles of beer"
	elif beers <= 1: bottles=str(beers)+" bottle of beer"
	out= "%s %s. %s. Take one down pass it around, " %(bottles,wall,bottles)
	beers-=1
	out+= "%s bottles of beer %s." %(str(beers),wall)
	print out
```

---

### Post by Titan8990 on 2008-08-01
I thought yours looked interesting arsenic but I get a syntax error trying to run it.

Edit: mvoncken your forgot the "/" for root directory on line 1:

> #!usr/bin/python

---

### Post by bobbocanfly on 2008-08-01
Boring one in Python:

```
bottles = range(0, 99)
bottles.reverse() #Reverse it otherwise we will be counting up
buffer = "" #Where we store the song up until we print it

for count in bottles:
    if count > 2: #'Bottles' is plural
        buffer += "%s bottles of beer on the wall, %s bottles of beer\n" % (count, count)
        buffer += "Take one down and pass it around, %s bottles of beer on the wall.\n\n" % (count - 1)
    elif count == 2: #Last bottle is singular
        buffer += "%s bottles of beer on the wall, %s bottles of beer\n" % (count, count)
        buffer += "Take one down and pass it around, %s bottle of beer on the wall.\n\n" % (count - 1)
    elif count == 1: #'Bottle' is singular
        buffer += "%s bottle of beer on the wall, %s bottle of beer\n" % (count, count)
        buffer += "Take one down and pass it around, no more bottles of beer on the wall.\n\n"
    elif count == 0: #No bottles left
        buffer += "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall."

#Dump the buffer onto the screen
print buffer
```

---

### Post by arsenic23 on 2008-08-01
> **Titan8990 said:**
> I thought yours looked interesting arsenic but I get a syntax error trying to run it.

I changed the first line.  Looks like it wasn't trying to run as python code.  After trying to run it with just ./filename.py, I noticed that it wasn't working for me either.  I think it works now, or it does for me.

---

### Post by Titan8990 on 2008-08-01
Works for me now as well but I am curious as to what env is.

---

### Post by arsenic23 on 2008-08-01
> **Titan8990 said:**
> Works for me now as well but I am curious as to what env is.

[http://www.cyberciti.biz/tips/finding-bash-perl-python-portably-using-env.html](http://www.cyberciti.biz/tips/finding-bash-perl-python-portably-using-env.html)

---

### Post by bobbocanfly on 2008-08-01
Heres a different version, users classes, lambdas and map(). Just learnt about the functional programming features yesterday so have been trying them out as much as possible.

```
class Bottle:
    
    #Setup the Bottle instance
    def __init__(self, number):
        self.number = number
        
        #Work what to say when asked
        if self.number == 0:
            self.say = "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall."
        elif self.number == 1:
            self.say = "%s bottle of beer on the wall, %s bottle of beer\n" % (self.number, self.number)
            self.say += "Take one down and pass it around, no more bottles of beer on the wall.\n\n"
        elif self.number == 2: #Last bottle is singular
            self.say = "%s bottles of beer on the wall, %s bottles of beer\n" % (self.number, self.number)
            self.say += "Take one down and pass it around, %s bottle of beer on the wall.\n\n" % (self.number - 1)
        else:
            self.say = "%s bottles of beer on the wall, %s bottles of beer\n" % (self.number, self.number)
            self.say += "Take one down and pass it around, %s bottles of beer on the wall.\n\n" % (self.number - 1)
            
    #Print the lyric for this bottle
    def speak(self):
        print self.say
        
if __name__ == "__main__":
    #Create a bottle instance for each number from 99 to -1 and put it into 'bottles' list
    #We need to have -1 so the last line will show
    bottles = map(lambda x: Bottle(x), range(99, -1, -1)) 
    
    #Go through each of the bottle instances and run its speak() function
    map(lambda x: x.speak(), bottles)
```

---

### Post by mvoncken on 2008-08-01
I'm sorry for the bugfixes and the #!/usr/bin/python , i really think this is final now, but I thought that when I posted the 1st version....

---

### Post by Titan8990 on 2008-08-01
Alright, a co-worker made an attempt at writing it in the fewest lines as possible. Here is it is:

[PHP]#include <stdio.h>
int main(){int x;for(x=99;x>=1;printf("%i bottle%s of beer on the wall, %i bottle%s of beer, take one down, pass it around, %s%i%s bottle%s of beer on the wall\n", x, x > 1 ? "s" : "", x, x > 1 ? "s" : "", x==1 ? "n" : "", x-1, x == 1 ? " more": "", x==2 ? "" : "s"),x--); 
return 0;}[/PHP]

---

### Post by rickh57 on 2008-08-01
This is in [Forth]("http://en.wikipedia.org/wiki/Forth_(programming_language)"), a stack-oriented postfix language. It is definitely not my first program using the language, but I haven't done much with it in 20 years. I used it extensively one summer during graduate school to create a program used to control a kiln for drying lumber.

```

: showbottles ( n -- )
\ duplicate the value for future use
DUP
\ if greater than 2...
2 > IF
    DUP . ." bottles of beer on the wall, " DUP . ." bottles of beer." CR ." Take one down and pass it around, " 1 - . ." bottles of beer on the wall." CR
ELSE
    \ if equal to 2...
    DUP 2 = IF DUP . ." bottles of beer on the wall, " . ." bottles of beer." CR ." Take one down and pass it around, one bottle of beer on the wall." CR
ELSE
    \ if equal to 1
    DUP 1 = IF DUP . ." bottle of beer on the wall, " . ." bottle of beer." CR ." Take one down and pass it around, no more bottles of beer on the wall." CR
ELSE
    \ if equal to 0
    0 = IF ." No more bottles of beer on the wall, no more bottles of beer." CR ." Go to the store and buy some more, 99 bottles of beer on the wall." CR
THEN
THEN
THEN
THEN
CR
;

: beer ( -- )
\ loop 100 times... [0 to 99]
100 0 DO
    \ subtract loop counter from 99 and leave on stack
    99 I -
    showbottles
LOOP ;

```

---

### Post by arsenic23 on 2008-08-01
My first one was broken and I didn't notice because I was typing it while at work.  Oh distractions.

[PHP]#!/usr/bin/env python

beers=99
wall="on the wall"
S="s"
while beers >= 0:
	if beers == 0:
		print "We ain't got no beer."
		break
	bottles="%s bottle%s of beer" %(str(beers),S)
	out="%s %s. %s. Take one down pass it around, " %(bottles,wall,bottles)
	beers-=1
	if beers <= 1: S=''
	out+= "%s bottle%s of beer %s." %(str(beers),S,wall)
	print out[/PHP]

---

### Post by Lux Perpetua on 2008-08-01
> **LaRoza said:**
> We have at other times had weekly programming challenges. They, when I read them, seemed to get more advanced as they went because the winner got to choose the next challenge, each one was the idea of a somewhat experienced programmer and sometimes very experienced.Thank you. I am also guilty of that (my challenge being to draw Sierpinski's triangle), but I'm glad someone said it. 

That said, it can be hard to come up with challenges that are both easy and interesting. I like this one, though. It's totally trivial, and although the result isn't very interesting, there are many interesting possibilities for implementation.

---

### Post by aktiwers on 2008-08-01
Okay I made a new one..  I found out my other (slamcode) did not work 100% correct.
This one does though :)

[php]
#!/usr/bin/python
#
# Drink drink! ver. 0.2
# "99 Bottles of Beer". 

i = 99

for x in range(3, 99):
    i = i-1
    print i, " bottles of beer on the wall,",i ,"bottles of beer. \n"
    print "Take one down and pass it around,", i-1, "bottles of beer on the wall."
if i == 3:
    i = i-1
    print i-1, " bottle of beer on the wall,",i-1 ,"bottle of beer. \n\n",i-1, "bottle of beer on the wall,",i-1, "bottle of beer.\n","Take one down and pass it around, no more bottles of beer on the wall.\n\n","No more bottles of beer on the wall, no more bottles of beer.\n", "Go to the store and buy some more,", i+97," bottles of beer on the wall.\n"
[/php]Btw thanks for the comment mvoncken..  I will remember that 
Edit: Why does my first output line only show 98 and not the second verse? :(

---

### Post by samjh on 2008-08-01
A little messy, but here's mine.  (In Python, obviously.)

Illustrates function recursion, type casting to string, and the string.replace() method.  It should be fairly self-explanatory.  Also illustrates a form of if-else optimisation: ie. check for the most common and computationally least expensive occurrence first, and "else-if" the least common and computationally most expensive occurrence last.

[php]#! /usr/bin/python

# This function prints the constructed verse from form_verse(bottles) function.
def write_verse(verse):
	print verse

# This function constructs each verse (consisting of two lines) to be printed to screen.
def form_verse(bottles):
	# Cast the integer variable bottles, and integer result from bottles - 1, into strings.
	# This allows concatenation of these values with other strings, using the "+" operator.
	bwall = str(bottles)
	bleft = str(bottles - 1)
	
	# These two lines form the two lines of a verse.  If the bottles on the wall is greater
	#   than 2 and smaller than 100, theses can be printed to screen as is.
	line1 = bwall + " bottles of beer on the wall, " + bwall + " bottles of beer.\n"
	line2 = "Take one down and pass it around, " + bleft + " bottles of beer on the wall.\n"
	
	# Check for special cases! Notice how the most common and simplest occurrence is checked first.
	# The last case (bottles == 0) is the least common and involves the most complex action. It also
	#   results in the end of this program using the "return" keyword to exit the function.
	if bottles > 2:
		write_verse(line1 + line2)
	elif bottles == 2:
		line2 = line2.replace("bottles", "bottle")
		write_verse(line1 + line2)
	elif bottles == 1:
		line1 = line1.replace("bottles", "bottle")
		line2 = line2.replace("0", "no more")
		write_verse(line1 + line2)
	elif bottles == 0:
		# Something tricky with the next two lines. :)
		# If I use just the first line and not the second, then the sentence is
		#   grammatically wrong. Try it.
		line1 = line1.replace("0", "no more")
		line1 = line1.replace("no more", "No more", 1)
		line2 = "Go to the store and buy some more, 99 bottles of beer on the wall."
		write_verse(line1 + line2)
		return
	
	# Demonstrates recursion: a function invoking itself. Notice that the bottles parameter is
	#   is reduced by 1 each time this function runs, until it reaches 0.
	form_verse(bottles - 1)

# Calls form_verse(bottles) function, which will keep calling itself until bottles = 0.
form_verse(99)[/php]

---

### Post by LaRoza on 2008-08-01
Looking good everyone. Now, I know some of you aren't beginners and this challenge series will be aimed at those starting to learn programming ;) 

I will chose the winner soon (after it seems no one else is going to submit) but because this thread is aimed at beginners, it would be nice if people gave their input on other people's code at the end to help.

---

### Post by samjh on 2008-08-01
> **LaRoza said:**
> Looking good everyone. Now, I know some of you aren't beginners and this challenge series will be aimed at those starting to learn programming ;) 

I think those of us who are more experienced should try to produce code which demonstrates concepts or styles that beginners can learn from.  It's what I tried to do in my submission. :)

---

### Post by LaRoza on 2008-08-01
> **samjh said:**
> I think those of us who are more experienced should try to produce code which demonstrates concepts or styles that beginners can learn from.  It's what I tried to do in my submission. :)

Yes, I know. I just didn't want a new programmer coming in and seeing those tricks and getting depressed :-)

---

### Post by mssever on 2008-08-01
> **aktiwers said:**
> Edit: Why does my first output line only show 98 and not the second verse? :(
Hint: Where are you decrementing your counter, and/or where are you starting your range?

---

### Post by Def13b on 2008-08-01
First, I'm a huge fan of these challenges so thanks to LaRoza and everyone else that's made one. I've learnt alot from these, Project Euler, Challenge-You and Python Challenge that never quite stuck when read in a tutorial or book.

Here's my effort, as with life, if you give the drinking task to an object when it's all over you'll only be left with one thing :)

```
#!/usr/bin/env python

def drink(n):
    stock = zip(range(n, 0, -1), range(n-1, 0, -1) + ['no more'])
    case = {1: 'bottle'}
    for before, after in stock:
        print '%s %s of beer on the wall, %s %s of beer.' % (before, case.get(before, 'bottles'), before, case.get(before, 'bottles'))
        print 'Take one down and pass it around, %s %s of beer on the wall.\n' % (after, case.get(after, 'bottles'))
    print 'No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.'
    return 'Hangover'
    
drink(99)
```

---

### Post by descendency on 2008-08-02
Mono (basic, straightforward, sledgehammer method):

```
[COLOR="White"]using System;

class Program
{
    public static void Main(string[] args)
    {
        int beer;           // a counter variable to keep up with how much beer I have
        for (beer = 99; beer > -1; beer--) // make sure you decrement instead of increment, or else you'll have infinite imaginary beer. . . 
        {
            switch (beer) // an if alternative
            {
                case 0:
                    Console.WriteLine("No more bottles of beer on the wall, no more bottles of beer.");
                    Console.WriteLine("Go to the store and buy some more, 99 bottles of beer on the wall.");
                    Console.WriteLine("");
                    break;  // don't forget the breaks, it'll print too many extra sentences
                case 1:
                    Console.WriteLine(beer + " bottle of beer on the wall, " + beer + " bottle of beer.");
                    Console.WriteLine("Take one down and pass it around, no more bottles of beer on the wall.");
                    Console.WriteLine("");
                    break;
                case 2:
                    Console.WriteLine(beer + " bottles of beer on the wall, " + beer + " bottles of beer.");
                    Console.WriteLine("Take one down and pass it around, " + (beer - 1) + " bottle of beer on the wall.");      // don't forget parenthesis, it's a compile time syntax error
                    Console.WriteLine("");
                    break;
                default:
                    Console.WriteLine(beer + " bottles of beer on the wall, " + beer + " bottles of beer.");
                    Console.WriteLine("Take one down and pass it around, " + (beer - 1) + " bottles of beer on the wall.");
                    Console.WriteLine("");
                    break;
            }            
        } 
    }
}[/COLOR]
```

I considered a foreach loop, but I didn't want to have to hand type the array. ("99", "98", "97", "96", ..., "3", "2", "1", "No more")

edit: Hidden from those who might want to complete the challenge without reading my code.

---

### Post by mssever on 2008-08-02
> **descendency said:**
> edit: Hidden from those who might want to complete the challenge without reading my code.
For a minute, I thought you'd decided to write it in [Whitespace]("http://en.wikipedia.org/wiki/Whitespace_%28programming_language%29").

---

### Post by slavik on 2008-08-02
> **LaRoza said:**
> Clean code. Readable code is a must for being a programmer who wishes to possibly interact with others. Some languages can be more readable than others, so it will be judged on the effort of writing clean code, not which language is easier to read by design.

Why do you discriminate against me? :(

---

### Post by LaRoza on 2008-08-02
> **slavik said:**
> Why do you discriminate against me? :(

I specifically said the criteria would be based on effort, not structure of the language:
> 
so it will be judged on the **effort of writing clean code**, not which language is easier to read by design.

---

### Post by collinp on 2008-08-02
Whoops, found the answer to my question.

---

### Post by collinp on 2008-08-02
Here is a simple one done in Bash:
```
#/usr/bin/bash
#These are the lyrics to the rhyme "99 Bottles of Beer on the wall, coding 
#done in bash
echo 99 bottles of beer on the wall, 99 bottles of beer.
echo Take one down and pass it around, 98 bottles of beer on the wall.
sleep 4
echo 98 bottles of beer on the wall, 98 bottles of beer.
echo Take one down and pass it around, 97 bottles of beer on the wall.
sleep 4
echo 97 bottles of beer on the wall, 97 bottles of beer.
echo Take one down and pass it around, 96 bottles of beer on the wall.
sleep 4
echo 96 bottles of beer on the wall, 96 bottles of beer.
echo Take one down and pass it around, 95 bottles of beer on the wall.
sleep 4
echo 95 bottles of beer on the wall, 95 bottles of beer.
echo Take one down and pass it around, 94 bottles of beer on the wall.
sleep 4
echo 94 bottles of beer on the wall, 94 bottles of beer.
echo Take one down and pass it around, 93 bottles of beer on the wall.
sleep 4
echo 93 bottles of beer on the wall, 93 bottles of beer.
echo Take one down and pass it around, 92 bottles of beer on the wall.
sleep 4
echo 92 bottles of beer on the wall, 92 bottles of beer.
echo Take one down and pass it around, 91 bottles of beer on the wall.
sleep 4
echo 91 bottles of beer on the wall, 91 bottles of beer.
echo Take one down and pass it around, 90 bottles of beer on the wall.
sleep 4
echo 90 bottles of beer on the wall, 90 bottles of beer.
echo Take one down and pass it around, 89 bottles of beer on the wall.
sleep 4
echo 89 bottles of beer on the wall, 89 bottles of beer.
echo Take one down and pass it around, 88 bottles of beer on the wall.
sleep 4
echo 88 bottles of beer on the wall, 88 bottles of beer.
echo Take one down and pass it around, 87 bottles of beer on the wall.
sleep 4
echo 87 bottles of beer on the wall, 87 bottles of beer.
echo Take one down and pass it around, 86 bottles of beer on the wall.
sleep 4
echo 86 bottles of beer on the wall, 86 bottles of beer.
echo Take one down and pass it around, 85 bottles of beer on the wall.
sleep 4
echo 85 bottles of beer on the wall, 85 bottles of beer.
echo Take one down and pass it around, 84 bottles of beer on the wall.
sleep 4
echo 84 bottles of beer on the wall, 84 bottles of beer.
echo Take one down and pass it around, 83 bottles of beer on the wall.
sleep 4
echo 83 bottles of beer on the wall, 83 bottles of beer.
echo Take one down and pass it around, 82 bottles of beer on the wall.
sleep 4
echo 82 bottles of beer on the wall, 82 bottles of beer.
echo Take one down and pass it around, 81 bottles of beer on the wall.
sleep 4
echo 81 bottles of beer on the wall, 81 bottles of beer.
echo Take one down and pass it around, 80 bottles of beer on the wall.
sleep 4
echo 80 bottles of beer on the wall, 80 bottles of beer.
echo Take one down and pass it around, 79 bottles of beer on the wall.
sleep 4
echo 79 bottles of beer on the wall, 79 bottles of beer.
echo Take one down and pass it around, 78 bottles of beer on the wall.
sleep 4
echo 78 bottles of beer on the wall, 78 bottles of beer.
echo Take one down and pass it around, 77 bottles of beer on the wall.
sleep 4
echo 77 bottles of beer on the wall, 77 bottles of beer.
echo Take one down and pass it around, 76 bottles of beer on the wall.
sleep 4
echo 76 bottles of beer on the wall, 76 bottles of beer.
echo Take one down and pass it around, 75 bottles of beer on the wall.
sleep 4
echo 75 bottles of beer on the wall, 75 bottles of beer.
echo Take one down and pass it around, 74 bottles of beer on the wall.
sleep 4
echo 74 bottles of beer on the wall, 74 bottles of beer.
echo Take one down and pass it around, 73 bottles of beer on the wall.
sleep 4
echo 73 bottles of beer on the wall, 73 bottles of beer.
echo Take one down and pass it around, 72 bottles of beer on the wall.
sleep 4
echo 72 bottles of beer on the wall, 72 bottles of beer.
echo Take one down and pass it around, 71 bottles of beer on the wall.
sleep 4
echo 71 bottles of beer on the wall, 71 bottles of beer.
echo Take one down and pass it around, 70 bottles of beer on the wall.
sleep 4
echo 70 bottles of beer on the wall, 70 bottles of beer.
echo Take one down and pass it around, 69 bottles of beer on the wall.
sleep 4
echo 69 bottles of beer on the wall, 69 bottles of beer.
echo Take one down and pass it around, 68 bottles of beer on the wall.
sleep 4
echo 68 bottles of beer on the wall, 68 bottles of beer.
echo Take one down and pass it around, 67 bottles of beer on the wall.
sleep 4
echo 67 bottles of beer on the wall, 67 bottles of beer.
echo Take one down and pass it around, 66 bottles of beer on the wall.
sleep 4
echo 66 bottles of beer on the wall, 66 bottles of beer.
echo Take one down and pass it around, 65 bottles of beer on the wall.
sleep 4
echo 65 bottles of beer on the wall, 65 bottles of beer.
echo Take one down and pass it around, 64 bottles of beer on the wall.
sleep 4
echo 64 bottles of beer on the wall, 64 bottles of beer.
echo Take one down and pass it around, 63 bottles of beer on the wall.
sleep 4
echo 63 bottles of beer on the wall, 63 bottles of beer.
echo Take one down and pass it around, 62 bottles of beer on the wall.
sleep 4
echo 62 bottles of beer on the wall, 62 bottles of beer.
echo Take one down and pass it around, 61 bottles of beer on the wall.
sleep 4
echo 61 bottles of beer on the wall, 61 bottles of beer.
echo Take one down and pass it around, 60 bottles of beer on the wall.
sleep 4
echo 60 bottles of beer on the wall, 60 bottles of beer.
echo Take one down and pass it around, 59 bottles of beer on the wall.
sleep 4
echo 59 bottles of beer on the wall, 59 bottles of beer.
echo Take one down and pass it around, 58 bottles of beer on the wall.
sleep 4
echo 58 bottles of beer on the wall, 58 bottles of beer.
echo Take one down and pass it around, 57 bottles of beer on the wall.
sleep 4
echo 57 bottles of beer on the wall, 57 bottles of beer.
echo Take one down and pass it around, 56 bottles of beer on the wall.
sleep 4
echo 56 bottles of beer on the wall, 56 bottles of beer.
echo Take one down and pass it around, 55 bottles of beer on the wall.
sleep 4
echo 55 bottles of beer on the wall, 55 bottles of beer.
echo Take one down and pass it around, 54 bottles of beer on the wall.
sleep 4
echo 54 bottles of beer on the wall, 54 bottles of beer.
echo Take one down and pass it around, 53 bottles of beer on the wall.
sleep 4
echo 53 bottles of beer on the wall, 53 bottles of beer.
echo Take one down and pass it around, 52 bottles of beer on the wall.
sleep 4
echo 52 bottles of beer on the wall, 52 bottles of beer.
echo Take one down and pass it around, 51 bottles of beer on the wall.
sleep 4
echo 51 bottles of beer on the wall, 51 bottles of beer.
echo Take one down and pass it around, 50 bottles of beer on the wall.
sleep 4
echo 50 bottles of beer on the wall, 50 bottles of beer.
echo Take one down and pass it around, 49 bottles of beer on the wall.
sleep 4
echo 49 bottles of beer on the wall, 49 bottles of beer.
echo Take one down and pass it around, 48 bottles of beer on the wall.
sleep 4
echo 48 bottles of beer on the wall, 48 bottles of beer.
echo Take one down and pass it around, 47 bottles of beer on the wall.
sleep 4
echo 47 bottles of beer on the wall, 47 bottles of beer.
echo Take one down and pass it around, 46 bottles of beer on the wall.
sleep 4
echo 46 bottles of beer on the wall, 46 bottles of beer.
echo Take one down and pass it around, 45 bottles of beer on the wall.
sleep 4
echo 45 bottles of beer on the wall, 45 bottles of beer.
echo Take one down and pass it around, 44 bottles of beer on the wall.
sleep 4
echo 44 bottles of beer on the wall, 44 bottles of beer.
echo Take one down and pass it around, 43 bottles of beer on the wall.
sleep 4
echo 43 bottles of beer on the wall, 43 bottles of beer.
echo Take one down and pass it around, 42 bottles of beer on the wall.
sleep 4
echo 42 bottles of beer on the wall, 42 bottles of beer.
echo Take one down and pass it around, 41 bottles of beer on the wall.
sleep 4
echo 41 bottles of beer on the wall, 41 bottles of beer.
echo Take one down and pass it around, 40 bottles of beer on the wall.
sleep 4
echo 40 bottles of beer on the wall, 40 bottles of beer.
echo Take one down and pass it around, 39 bottles of beer on the wall.
sleep 4
echo 39 bottles of beer on the wall, 39 bottles of beer.
echo Take one down and pass it around, 38 bottles of beer on the wall.
sleep 4
echo 38 bottles of beer on the wall, 38 bottles of beer.
echo Take one down and pass it around, 37 bottles of beer on the wall.
sleep 4
echo 37 bottles of beer on the wall, 37 bottles of beer.
echo Take one down and pass it around, 36 bottles of beer on the wall.
sleep 4
echo 36 bottles of beer on the wall, 36 bottles of beer.
echo Take one down and pass it around, 35 bottles of beer on the wall.
sleep 4
echo 35 bottles of beer on the wall, 35 bottles of beer.
echo Take one down and pass it around, 34 bottles of beer on the wall.
sleep 4
echo 34 bottles of beer on the wall, 34 bottles of beer.
echo Take one down and pass it around, 33 bottles of beer on the wall.
sleep 4
echo 33 bottles of beer on the wall, 33 bottles of beer.
echo Take one down and pass it around, 32 bottles of beer on the wall.
sleep 4
echo 32 bottles of beer on the wall, 32 bottles of beer.
echo Take one down and pass it around, 31 bottles of beer on the wall.
sleep 4
echo 31 bottles of beer on the wall, 31 bottles of beer.
echo Take one down and pass it around, 30 bottles of beer on the wall.
sleep 4
echo 30 bottles of beer on the wall, 30 bottles of beer.
echo Take one down and pass it around, 29 bottles of beer on the wall.
sleep 4
echo 29 bottles of beer on the wall, 29 bottles of beer.
echo Take one down and pass it around, 28 bottles of beer on the wall.
sleep 4
echo 28 bottles of beer on the wall, 28 bottles of beer.
echo Take one down and pass it around, 27 bottles of beer on the wall.
sleep 4
echo 27 bottles of beer on the wall, 27 bottles of beer.
echo Take one down and pass it around, 26 bottles of beer on the wall.
sleep 4
echo 26 bottles of beer on the wall, 26 bottles of beer.
echo Take one down and pass it around, 25 bottles of beer on the wall.
sleep 4
echo 25 bottles of beer on the wall, 25 bottles of beer.
echo Take one down and pass it around, 24 bottles of beer on the wall.
sleep 4
echo 24 bottles of beer on the wall, 24 bottles of beer.
echo Take one down and pass it around, 23 bottles of beer on the wall.
sleep 4
echo 23 bottles of beer on the wall, 23 bottles of beer.
echo Take one down and pass it around, 22 bottles of beer on the wall.
sleep 4
echo 22 bottles of beer on the wall, 22 bottles of beer.
echo Take one down and pass it around, 21 bottles of beer on the wall.
sleep 4
echo 21 bottles of beer on the wall, 21 bottles of beer.
echo Take one down and pass it around, 20 bottles of beer on the wall.
sleep 4
echo 20 bottles of beer on the wall, 20 bottles of beer.
echo Take one down and pass it around, 19 bottles of beer on the wall.
sleep 4
echo 19 bottles of beer on the wall, 19 bottles of beer.
echo Take one down and pass it around, 18 bottles of beer on the wall.
sleep 4
echo 18 bottles of beer on the wall, 18 bottles of beer.
echo Take one down and pass it around, 17 bottles of beer on the wall.
sleep 4
echo 17 bottles of beer on the wall, 17 bottles of beer.
echo Take one down and pass it around, 16 bottles of beer on the wall.
sleep 4
echo 16 bottles of beer on the wall, 16 bottles of beer.
echo Take one down and pass it around, 15 bottles of beer on the wall.
sleep 4
echo 15 bottles of beer on the wall, 15 bottles of beer.
echo Take one down and pass it around, 14 bottles of beer on the wall.
sleep 4
echo 14 bottles of beer on the wall, 14 bottles of beer.
echo Take one down and pass it around, 13 bottles of beer on the wall.
sleep 4
echo 13 bottles of beer on the wall, 13 bottles of beer.
echo Take one down and pass it around, 12 bottles of beer on the wall.
sleep 4
echo 12 bottles of beer on the wall, 12 bottles of beer.
echo Take one down and pass it around, 11 bottles of beer on the wall.
sleep 4
echo 11 bottles of beer on the wall, 11 bottles of beer.
echo Take one down and pass it around, 10 bottles of beer on the wall.
sleep 4
echo 10 bottles of beer on the wall, 10 bottles of beer.
echo Take one down and pass it around, 9 bottles of beer on the wall.
sleep 4
echo 9 bottles of beer on the wall, 9 bottles of beer.
echo Take one down and pass it around, 8 bottles of beer on the wall.
sleep 4
echo 8 bottles of beer on the wall, 8 bottles of beer.
echo Take one down and pass it around, 7 bottles of beer on the wall.
sleep 4
echo 7 bottles of beer on the wall, 7 bottles of beer.
echo Take one down and pass it around, 6 bottles of beer on the wall.
sleep 4
echo 6 bottles of beer on the wall, 6 bottles of beer.
echo Take one down and pass it around, 5 bottles of beer on the wall.
sleep 4
echo 5 bottles of beer on the wall, 5 bottles of beer.
echo Take one down and pass it around, 4 bottles of beer on the wall.
sleep 4
echo 4 bottles of beer on the wall, 4 bottles of beer.
echo Take one down and pass it around, 3 bottles of beer on the wall.
sleep 4
echo 3 bottles of beer on the wall, 3 bottles of beer.
echo Take one down and pass it around, 2 bottles of beer on the wall.
sleep 4
echo 2 bottles of beer on the wall, 2 bottles of beer.
echo Take one down and pass it around, 1 bottle of beer on the wall.
sleep 4
echo 1 bottle of beer on the wall, 1 bottle of beer.
echo Take one down and pass it around, no more bottles of beer on the wall.
sleep 3
echo No beer, go buy more!
echo Add the beer to the wall, 99 bottles of beer on the wall.
```

And i didnt copy from the website, if you are wondering that.

---

### Post by Maveric3477 on 2008-08-02
> **LaRoza said:**
> ...it would be nice if people gave their input on other people's code at the end to help.

That would be really cool if people gave their input. I know I'd definitely benefit from having people critique my code. I'm not too horrible at writing working code, but it's generally not pretty :P

---

### Post by OutOfReach on 2008-08-02
Here's mine, remember that I'm just learning Python so don't eat me if I'm doing this all wrong :P.
[PHP]#!/usr/bin/env python


lineOne = "%i bottles of beer on the wall, %i bottles of beer."
lineTwo = "Take one down and pass it around, %i bottles of beer on the wall.\n\n"
numberOfBeers = 99

while numberOfBeers >= 0:

    print lineOne % (numberOfBeers, numberOfBeers)
    print lineTwo % int(numberOfBeers - 1)
    numberOfBeers -= 1

    #In the next three blocks, we change the output so the ending of the song makes sense.

    if numberOfBeers == 2:

        print lineOne % (numberOfBeers, numberOfBeers)
        print "Take one down and pass it around, %i bottle of beer on the wall.\n\n" % int(numberOfBeers - 1)
        numberOfBeers -= 1

    if numberOfBeers == 1:

        print "%i bottle of beer on the wall, %i bottle of beer." % (numberOfBeers, numberOfBeers)
        print "Take one down and pass it around, no more bottles of beer on the wall.\n\n"
        numberOfBeers = 0

    if numberOfBeers == 0:

        print "No more bottles of beer on the wall, no more bottles of beer."
        print "Go to the store and buy some more, 99 bottles of beer on the wall.\n\n"
        #Takes us out of the while loop
        break
[/PHP]

---

### Post by ghostdog74 on 2008-08-02
> **Hellow said:**
> Here is a simple one done in Bash:
```
#/usr/bin/bash
#These are the lyrics to the rhyme "99 Bottles of Beer on the wall, coding 
#done in bash
echo 99 bottles of beer on the wall, 99 bottles of beer.
echo Take one down and pass it around, 98 bottles of beer on the wall.
sleep 4
echo 98 bottles of beer on the wall, 98 bottles of beer.
echo Take one down and pass it around, 97 bottles of beer on the wall.
sleep 4
echo 97 bottles of beer on the wall, 97 bottles of beer.
echo Take one down and pass it around, 96 bottles of beer on the wall.
sleep 4
echo 96 bottles of beer on the wall, 96 bottles of beer.
echo Take one down and pass it around, 95 bottles of beer on the wall.
sleep 4
echo 95 bottles of beer on the wall, 95 bottles of beer.
echo Take one down and pass it around, 94 bottles of beer on the wall.
sleep 4
echo 94 bottles of beer on the wall, 94 bottles of beer.
echo Take one down and pass it around, 93 bottles of beer on the wall.
sleep 4
echo 93 bottles of beer on the wall, 93 bottles of beer.
echo Take one down and pass it around, 92 bottles of beer on the wall.
sleep 4
echo 92 bottles of beer on the wall, 92 bottles of beer.
echo Take one down and pass it around, 91 bottles of beer on the wall.
sleep 4
echo 91 bottles of beer on the wall, 91 bottles of beer.
echo Take one down and pass it around, 90 bottles of beer on the wall.
sleep 4
echo 90 bottles of beer on the wall, 90 bottles of beer.
echo Take one down and pass it around, 89 bottles of beer on the wall.
sleep 4
echo 89 bottles of beer on the wall, 89 bottles of beer.
echo Take one down and pass it around, 88 bottles of beer on the wall.
sleep 4
echo 88 bottles of beer on the wall, 88 bottles of beer.
echo Take one down and pass it around, 87 bottles of beer on the wall.
sleep 4
echo 87 bottles of beer on the wall, 87 bottles of beer.
echo Take one down and pass it around, 86 bottles of beer on the wall.
sleep 4
echo 86 bottles of beer on the wall, 86 bottles of beer.
echo Take one down and pass it around, 85 bottles of beer on the wall.
sleep 4
echo 85 bottles of beer on the wall, 85 bottles of beer.
echo Take one down and pass it around, 84 bottles of beer on the wall.
sleep 4
echo 84 bottles of beer on the wall, 84 bottles of beer.
echo Take one down and pass it around, 83 bottles of beer on the wall.
sleep 4
echo 83 bottles of beer on the wall, 83 bottles of beer.
echo Take one down and pass it around, 82 bottles of beer on the wall.
sleep 4
echo 82 bottles of beer on the wall, 82 bottles of beer.
echo Take one down and pass it around, 81 bottles of beer on the wall.
sleep 4
echo 81 bottles of beer on the wall, 81 bottles of beer.
echo Take one down and pass it around, 80 bottles of beer on the wall.
sleep 4
echo 80 bottles of beer on the wall, 80 bottles of beer.
echo Take one down and pass it around, 79 bottles of beer on the wall.
sleep 4
echo 79 bottles of beer on the wall, 79 bottles of beer.
echo Take one down and pass it around, 78 bottles of beer on the wall.
sleep 4
echo 78 bottles of beer on the wall, 78 bottles of beer.
echo Take one down and pass it around, 77 bottles of beer on the wall.
sleep 4
echo 77 bottles of beer on the wall, 77 bottles of beer.
echo Take one down and pass it around, 76 bottles of beer on the wall.
sleep 4
echo 76 bottles of beer on the wall, 76 bottles of beer.
echo Take one down and pass it around, 75 bottles of beer on the wall.
sleep 4
echo 75 bottles of beer on the wall, 75 bottles of beer.
echo Take one down and pass it around, 74 bottles of beer on the wall.
sleep 4
echo 74 bottles of beer on the wall, 74 bottles of beer.
echo Take one down and pass it around, 73 bottles of beer on the wall.
sleep 4
echo 73 bottles of beer on the wall, 73 bottles of beer.
echo Take one down and pass it around, 72 bottles of beer on the wall.
sleep 4
echo 72 bottles of beer on the wall, 72 bottles of beer.
echo Take one down and pass it around, 71 bottles of beer on the wall.
sleep 4
echo 71 bottles of beer on the wall, 71 bottles of beer.
echo Take one down and pass it around, 70 bottles of beer on the wall.
sleep 4
echo 70 bottles of beer on the wall, 70 bottles of beer.
echo Take one down and pass it around, 69 bottles of beer on the wall.
sleep 4
echo 69 bottles of beer on the wall, 69 bottles of beer.
echo Take one down and pass it around, 68 bottles of beer on the wall.
sleep 4
echo 68 bottles of beer on the wall, 68 bottles of beer.
echo Take one down and pass it around, 67 bottles of beer on the wall.
sleep 4
echo 67 bottles of beer on the wall, 67 bottles of beer.
echo Take one down and pass it around, 66 bottles of beer on the wall.
sleep 4
echo 66 bottles of beer on the wall, 66 bottles of beer.
echo Take one down and pass it around, 65 bottles of beer on the wall.
sleep 4
echo 65 bottles of beer on the wall, 65 bottles of beer.
echo Take one down and pass it around, 64 bottles of beer on the wall.
sleep 4
echo 64 bottles of beer on the wall, 64 bottles of beer.
echo Take one down and pass it around, 63 bottles of beer on the wall.
sleep 4
echo 63 bottles of beer on the wall, 63 bottles of beer.
echo Take one down and pass it around, 62 bottles of beer on the wall.
sleep 4
echo 62 bottles of beer on the wall, 62 bottles of beer.
echo Take one down and pass it around, 61 bottles of beer on the wall.
sleep 4
echo 61 bottles of beer on the wall, 61 bottles of beer.
echo Take one down and pass it around, 60 bottles of beer on the wall.
sleep 4
echo 60 bottles of beer on the wall, 60 bottles of beer.
echo Take one down and pass it around, 59 bottles of beer on the wall.
sleep 4
echo 59 bottles of beer on the wall, 59 bottles of beer.
echo Take one down and pass it around, 58 bottles of beer on the wall.
sleep 4
echo 58 bottles of beer on the wall, 58 bottles of beer.
echo Take one down and pass it around, 57 bottles of beer on the wall.
sleep 4
echo 57 bottles of beer on the wall, 57 bottles of beer.
echo Take one down and pass it around, 56 bottles of beer on the wall.
sleep 4
echo 56 bottles of beer on the wall, 56 bottles of beer.
echo Take one down and pass it around, 55 bottles of beer on the wall.
sleep 4
echo 55 bottles of beer on the wall, 55 bottles of beer.
echo Take one down and pass it around, 54 bottles of beer on the wall.
sleep 4
echo 54 bottles of beer on the wall, 54 bottles of beer.
echo Take one down and pass it around, 53 bottles of beer on the wall.
sleep 4
echo 53 bottles of beer on the wall, 53 bottles of beer.
echo Take one down and pass it around, 52 bottles of beer on the wall.
sleep 4
echo 52 bottles of beer on the wall, 52 bottles of beer.
echo Take one down and pass it around, 51 bottles of beer on the wall.
sleep 4
echo 51 bottles of beer on the wall, 51 bottles of beer.
echo Take one down and pass it around, 50 bottles of beer on the wall.
sleep 4
echo 50 bottles of beer on the wall, 50 bottles of beer.
echo Take one down and pass it around, 49 bottles of beer on the wall.
sleep 4
echo 49 bottles of beer on the wall, 49 bottles of beer.
echo Take one down and pass it around, 48 bottles of beer on the wall.
sleep 4
echo 48 bottles of beer on the wall, 48 bottles of beer.
echo Take one down and pass it around, 47 bottles of beer on the wall.
sleep 4
echo 47 bottles of beer on the wall, 47 bottles of beer.
echo Take one down and pass it around, 46 bottles of beer on the wall.
sleep 4
echo 46 bottles of beer on the wall, 46 bottles of beer.
echo Take one down and pass it around, 45 bottles of beer on the wall.
sleep 4
echo 45 bottles of beer on the wall, 45 bottles of beer.
echo Take one down and pass it around, 44 bottles of beer on the wall.
sleep 4
echo 44 bottles of beer on the wall, 44 bottles of beer.
echo Take one down and pass it around, 43 bottles of beer on the wall.
sleep 4
echo 43 bottles of beer on the wall, 43 bottles of beer.
echo Take one down and pass it around, 42 bottles of beer on the wall.
sleep 4
echo 42 bottles of beer on the wall, 42 bottles of beer.
echo Take one down and pass it around, 41 bottles of beer on the wall.
sleep 4
echo 41 bottles of beer on the wall, 41 bottles of beer.
echo Take one down and pass it around, 40 bottles of beer on the wall.
sleep 4
echo 40 bottles of beer on the wall, 40 bottles of beer.
echo Take one down and pass it around, 39 bottles of beer on the wall.
sleep 4
echo 39 bottles of beer on the wall, 39 bottles of beer.
echo Take one down and pass it around, 38 bottles of beer on the wall.
sleep 4
echo 38 bottles of beer on the wall, 38 bottles of beer.
echo Take one down and pass it around, 37 bottles of beer on the wall.
sleep 4
echo 37 bottles of beer on the wall, 37 bottles of beer.
echo Take one down and pass it around, 36 bottles of beer on the wall.
sleep 4
echo 36 bottles of beer on the wall, 36 bottles of beer.
echo Take one down and pass it around, 35 bottles of beer on the wall.
sleep 4
echo 35 bottles of beer on the wall, 35 bottles of beer.
echo Take one down and pass it around, 34 bottles of beer on the wall.
sleep 4
echo 34 bottles of beer on the wall, 34 bottles of beer.
echo Take one down and pass it around, 33 bottles of beer on the wall.
sleep 4
echo 33 bottles of beer on the wall, 33 bottles of beer.
echo Take one down and pass it around, 32 bottles of beer on the wall.
sleep 4
echo 32 bottles of beer on the wall, 32 bottles of beer.
echo Take one down and pass it around, 31 bottles of beer on the wall.
sleep 4
echo 31 bottles of beer on the wall, 31 bottles of beer.
echo Take one down and pass it around, 30 bottles of beer on the wall.
sleep 4
echo 30 bottles of beer on the wall, 30 bottles of beer.
echo Take one down and pass it around, 29 bottles of beer on the wall.
sleep 4
echo 29 bottles of beer on the wall, 29 bottles of beer.
echo Take one down and pass it around, 28 bottles of beer on the wall.
sleep 4
echo 28 bottles of beer on the wall, 28 bottles of beer.
echo Take one down and pass it around, 27 bottles of beer on the wall.
sleep 4
echo 27 bottles of beer on the wall, 27 bottles of beer.
echo Take one down and pass it around, 26 bottles of beer on the wall.
sleep 4
echo 26 bottles of beer on the wall, 26 bottles of beer.
echo Take one down and pass it around, 25 bottles of beer on the wall.
sleep 4
echo 25 bottles of beer on the wall, 25 bottles of beer.
echo Take one down and pass it around, 24 bottles of beer on the wall.
sleep 4
echo 24 bottles of beer on the wall, 24 bottles of beer.
echo Take one down and pass it around, 23 bottles of beer on the wall.
sleep 4
echo 23 bottles of beer on the wall, 23 bottles of beer.
echo Take one down and pass it around, 22 bottles of beer on the wall.
sleep 4
echo 22 bottles of beer on the wall, 22 bottles of beer.
echo Take one down and pass it around, 21 bottles of beer on the wall.
sleep 4
echo 21 bottles of beer on the wall, 21 bottles of beer.
echo Take one down and pass it around, 20 bottles of beer on the wall.
sleep 4
echo 20 bottles of beer on the wall, 20 bottles of beer.
echo Take one down and pass it around, 19 bottles of beer on the wall.
sleep 4
echo 19 bottles of beer on the wall, 19 bottles of beer.
echo Take one down and pass it around, 18 bottles of beer on the wall.
sleep 4
echo 18 bottles of beer on the wall, 18 bottles of beer.
echo Take one down and pass it around, 17 bottles of beer on the wall.
sleep 4
echo 17 bottles of beer on the wall, 17 bottles of beer.
echo Take one down and pass it around, 16 bottles of beer on the wall.
sleep 4
echo 16 bottles of beer on the wall, 16 bottles of beer.
echo Take one down and pass it around, 15 bottles of beer on the wall.
sleep 4
echo 15 bottles of beer on the wall, 15 bottles of beer.
echo Take one down and pass it around, 14 bottles of beer on the wall.
sleep 4
echo 14 bottles of beer on the wall, 14 bottles of beer.
echo Take one down and pass it around, 13 bottles of beer on the wall.
sleep 4
echo 13 bottles of beer on the wall, 13 bottles of beer.
echo Take one down and pass it around, 12 bottles of beer on the wall.
sleep 4
echo 12 bottles of beer on the wall, 12 bottles of beer.
echo Take one down and pass it around, 11 bottles of beer on the wall.
sleep 4
echo 11 bottles of beer on the wall, 11 bottles of beer.
echo Take one down and pass it around, 10 bottles of beer on the wall.
sleep 4
echo 10 bottles of beer on the wall, 10 bottles of beer.
echo Take one down and pass it around, 9 bottles of beer on the wall.
sleep 4
echo 9 bottles of beer on the wall, 9 bottles of beer.
echo Take one down and pass it around, 8 bottles of beer on the wall.
sleep 4
echo 8 bottles of beer on the wall, 8 bottles of beer.
echo Take one down and pass it around, 7 bottles of beer on the wall.
sleep 4
echo 7 bottles of beer on the wall, 7 bottles of beer.
echo Take one down and pass it around, 6 bottles of beer on the wall.
sleep 4
echo 6 bottles of beer on the wall, 6 bottles of beer.
echo Take one down and pass it around, 5 bottles of beer on the wall.
sleep 4
echo 5 bottles of beer on the wall, 5 bottles of beer.
echo Take one down and pass it around, 4 bottles of beer on the wall.
sleep 4
echo 4 bottles of beer on the wall, 4 bottles of beer.
echo Take one down and pass it around, 3 bottles of beer on the wall.
sleep 4
echo 3 bottles of beer on the wall, 3 bottles of beer.
echo Take one down and pass it around, 2 bottles of beer on the wall.
sleep 4
echo 2 bottles of beer on the wall, 2 bottles of beer.
echo Take one down and pass it around, 1 bottle of beer on the wall.
sleep 4
echo 1 bottle of beer on the wall, 1 bottle of beer.
echo Take one down and pass it around, no more bottles of beer on the wall.
sleep 3
echo No beer, go buy more!
echo Add the beer to the wall, 99 bottles of beer on the wall.
```

And i didnt copy from the website, if you are wondering that.

and if its not 99 but 9999, are you going to type that many echoes? Use functions, mathematics in bash for the tasks. Read the bash link in my sig for more bash.

---

### Post by collinp on 2008-08-02
> **OutOfReach said:**
> Here's mine, remember that I'm just learning Python so don't eat me if I'm doing this all wrong :P.
```
#!/usr/bin/env python


lineOne = "%i bottles of beer on the wall, %i bottles of beer."
lineTwo = "Take one down and pass it around, %i bottles of beer on the wall.\n\n"
numberOfBeers = 99

while numberOfBeers >= 0:

    print lineOne % (numberOfBeers, numberOfBeers)
    print lineTwo % int(numberOfBeers - 1)
    numberOfBeers -= 1

    #In the next three blocks, we change the output so the ending of the song makes sense.

    if numberOfBeers == 2:

        print lineOne % (numberOfBeers, numberOfBeers)
        print "Take one down and pass it around, %i bottle of beer on the wall.\n\n" % int(numberOfBeers - 1)
        numberOfBeers -= 1

    if numberOfBeers == 1:

        print "%i bottle of beer on the wall, %i bottle of beer." % (numberOfBeers, numberOfBeers)
        print "Take one down and pass it around, no more bottles of beer on the wall.\n\n"
        numberOfBeers = 0

    if numberOfBeers == 0:

        print "No more bottles of beer on the wall, no more bottles of beer."
        print "Go to the store and buy some more, 99 bottles of beer on the wall.\n\n"
        #Takes us out of the while loop
        break

```

I eat you :b. I am actually learning python myself, dont have enough knowledge to make anything workable tho.

---

### Post by OutOfReach on 2008-08-02
Don't eat me!! D:
:P
All you need is hope to make things work. :) :lolflag:

---

### Post by NovaAesa on 2008-08-02
Writtin in C++ (which seems to be a bad choice for this challenge, Python is much better suited to this kind of thing). I chose C++ because it is my newest language (only been learning properly for the last 2 weeks). PHP tags used for limited syntax highlighting.

[php]
//Written by Peter Stace
//Last modification Sat 2nd of August 2008

#include <iostream>
#include <string>
#include <assert.h>
using namespace std;

// Outputs the number of bottles and then the word
// bottles either plural or singular.
//
// Preconditions: numBottles is the current number of bottles on the wall. It
//                should be a positive integer.
// Postconditions: a message is printed to standard output.
void bottles(int numBottles) {

    assert (numBottles >= 0); //numBottles should not be negative
    
    if (numBottles >= 2) {
        cout << numBottles << " bottles";
    } else if (numBottles == 1) {
        cout << "1 bottle";
    } else {
        cout << "no bottles";
    }
    
}

//the mainline of the programme
int main() {

    for (int i = 99; i >= 1; i--) {
    
        //first line
        bottles(i);
        cout << " of beer on the wall, ";
        bottles(i);
        cout << " of beer." << endl;
        
        //second line
        cout << "Take one down and pass it around," << endl;
        
        //third line
        bottles(i - 1);
        cout << " of beer on the wall.\n" <<endl;
    }
    
    //displayed at the end of the song
    cout << "Go to the store, buy some more," << endl;
    cout << "99 bottles of beer on the wall.\n" << endl;
}
[/php]

---

### Post by collinp on 2008-08-02
> **OutOfReach said:**
> Don't eat me!! D:
:P
All you need is hope to make things work. :) :lolflag:
You script works great :). But i am still going to eat you :lolflag:.

---

### Post by mosty friedman on 2008-08-02
```


//using java
//i think its pretty easy to understand the code so i didnt add any comments
public class Lyrics {
public static void main(String[]args)
{
	for(int bottles=99;bottles>0;bottles--)
	{
		if(bottles==2)
		{
		System.out.println(bottles+" bottles of beer on the wall, "+bottles+" bottles of beer");
		System.out.println("Take one down and pass it around, "+(bottles-1)+" bottle of beer on the wall");
		}
		if(bottles==1)
		{
		System.out.println(bottles+" bottle of beer on the wall, "+bottles+" bottle of beer");
		System.out.println("Take one down and pass it around, no more bottles of beer on the wall");
		}
		if(bottles>=3)
		{
		System.out.println(bottles+" bottles of beer on the wall, "+bottles+" bottles of beer");
		System.out.println("Take one down and pass it around, "+(bottles-1)+" bottles of beer on the wall");
		}
	}
	    System.out.println("No more bottles of beer on the wall, no more bottles of beer");
	    System.out.println("Go to the store and buy some more, 99 bottles of beer on the wall");
}
}

```

---

### Post by z0mbie on 2008-08-02
Here you go, written in** C++**:

[PHP]
/* Prints the lyrics to the song "99 Bottles of Beer" */

#include <iostream>

using namespace std;

int main() {

    for ( int x=99; x>2; x-- ) {

            cout << x << " bottles of beer on the wall, " << x << " bottles of beer.\n"
                 << "Take one down pass it around, " << (x-1) << " bottles of beer on the wall.\n\n";
                        
    }

    //Last 3 stanzas of the song:

    cout << "2 bottles of beer on the wall, 2 bottles of beer.\n"
         << "Take one down and pass it around, 1 bottle of beer on the wall.\n\n";

    cout << "1 bottle of beer on the wall, 1 bottle of beer.\n"
         << "Take one down and pass it around, no more bottles of beer on the wall.\n\n";

    cout << "No more bottles of beer on the wall, no more bottles of beer.\n"
         << "Go to the store and buy some more, 99 bottles of beer on the wall.\n";

    return 0;
}
[/PHP]

---

### Post by albeano2004 on 2008-08-02
Another Java response
```
public class beer{
    private int bottles;
    public void printSong()
    {   for(bottles = 99; bottles > 0; bottles--)
        {   System.out.println(bottles + //First line
            (bottles > 1 ? " bottles" : " bottle") + //Formatting for when 1 bottle on wall
            " of beer on the wall, " + bottles + 
            (bottles > 1 ? " bottles" : " bottle") + //ditto
            " of beer.");
            
            System.out.println("Take one down, and pass it around, " + //Second line
            (bottles > 1 ? (bottles - 1) : " no more") +    //Formatting for when 0 bottles on wall
            ((bottles - 1) == 1 ? " bottle" : " bottles") + //Formatting for when 1 bottle on wall
            " of beer on the wall");
        }
        System.out.println("No beer, go buy some more!");   //No more beer! Oh noes! Print message
        System.out.println("Add the beer to the wall, 99 bottles of beer on the wall");
    }
}
```

---

### Post by albeano2004 on 2008-08-02
Another Java response
[PHP]public class beer{
    private int bottles;
    public void printSong()
    {   for(bottles = 99; bottles > 0; bottles--)
        {   System.out.println(bottles + //First line
            (bottles > 1 ? " bottles" : " bottle") + //Formatting for when 1 bottle on wall
            " of beer on the wall, " + bottles + 
            (bottles > 1 ? " bottles" : " bottle") + //ditto
            " of beer.");
            
            System.out.println("Take one down, and pass it around, " + //Second line
            (bottles > 1 ? (bottles - 1) : " no more") +    //Formatting for when 0 bottles on wall
            ((bottles - 1) == 1 ? " bottle" : " bottles") + //Formatting for when 1 bottle on wall
            " of beer on the wall");
        }
        System.out.println("No beer, go buy some more!");   //No more beer! Oh noes! Print message
        System.out.println("Add the beer to the wall, 99 bottles of beer on the wall");
    }
}[/PHP]

May not be the prettiest, but I'm not that flash with Java - I'm only just learning it really :)

---

### Post by mosty friedman on 2008-08-02
```


//using java
//i think its pretty easy to understand the code so i didnt add any comments
public class Lyrics {
public static void main(String[]args)
{
	for(int bottles=99;bottles>0;bottles--)
	{
		if(bottles==2)
		{
		System.out.println(bottles+" bottles of beer on the wall, "+bottles+" bottles of beer");
		System.out.println("Take one down and pass it around, "+(bottles-1)+" bottle of beer on the wall");
		}
		if(bottles==1)
		{
		System.out.println(bottles+" bottle of beer on the wall, "+bottles+" bottle of beer");
		System.out.println("Take one down and pass it around, no more bottles of beer on the wall");
		}
		if(bottles>=3)
		{
		System.out.println(bottles+" bottles of beer on the wall, "+bottles+" bottles of beer");
		System.out.println("Take one down and pass it around, "+(bottles-1)+" bottles of beer on the wall");
		}
	}
	    System.out.println("No more bottles of beer on the wall, no more bottles of beer");
	    System.out.println("Go to the store and buy some more, 99 bottles of beer on the wall");
}
}

```
i did very little modification, although i edited it in the previous post but i forgot that editing should be in a new post..sorry for that

---

### Post by Ed J on 2008-08-02
Python version, my first non-interactive mode python script. Tried to keep it readable and simple.  
Is it?

```
#!/usr/bin/env python

beerlist = range(99, -1, -1)    	#list of number of beers to iterate through
beerstring = " bottles of beer"
wallstring = " on the wall"
takestring = "Take one down and pass it around, "
for beernumber in beerlist:
	if beernumber > 1:		#change output for last verse
		#output normal beer verse, "s" in "bottles"
		print repr(beernumber) + beerstring + wallstring + ", " + \
			repr(beernumber) + beerstring + "."		
		if beernumber is 2:	
			#remove "s" from bottles when verse is"1 bottle..."
			print takestring + repr(beernumber-1) + beerstring[:7] + \
				 beerstring[8:] + wallstring + "\n"
		else:	
			print takestring + repr(beernumber-1) + beerstring + wallstring + "\n"

	elif beernumber == 1:
			#slice "s" from "bottles".
		print repr(beernumber) + beerstring[:7] + beerstring[8:] + wallstring + \
			". " + repr(beernumber) + beerstring[:7] + beerstring[8:] + "."
		print takestring + "no more" + beerstring + wallstring + ".\n"
	elif beernumber == 0:
		print "No more" + beerstring + wallstring + ", no more" + beerstring + "."
		print "Go to the store and buy some more, " + repr(beerlist[0]) + \
			beerstring + wallstring + "."

```[HTML][/HTML]

---

### Post by descendency on 2008-08-02
> **ghostdog74 said:**
> and if its not 99 but 9999, are you going to type that many echoes? Use functions, mathematics in bash for the tasks. Read the bash link in my sig for more bash.
I think he was trying to be funny.

I was tempted to do that too, but I'm too lazy.

> **mosty friedman said:**
> ```


//using java
//i think its pretty easy to understand the code so i didnt add any comments
public class Lyrics {
public static void main(String[]args)
{
	for(int bottles=99;bottles>0;bottles--)
	{
		if(bottles==2)
		{
		System.out.println(bottles+" bottles of beer on the wall, "+bottles+" bottles of beer");
		System.out.println("Take one down and pass it around, "+(bottles-1)+" bottle of beer on the wall");
		}
		if(bottles==1)
		{
		System.out.println(bottles+" bottle of beer on the wall, "+bottles+" bottle of beer");
		System.out.println("Take one down and pass it around, no more bottles of beer on the wall");
		}
		if(bottles>=3)
		{
		System.out.println(bottles+" bottles of beer on the wall, "+bottles+" bottles of beer");
		System.out.println("Take one down and pass it around, "+(bottles-1)+" bottles of beer on the wall");
		}
	}
	    System.out.println("No more bottles of beer on the wall, no more bottles of beer");
	    System.out.println("Go to the store and buy some more, 99 bottles of beer on the wall");
}
}

```
i did very little modification, although i edited it in the previous post but i forgot that editing should be in a new post..sorry for that
This is just a style comment, but you could also use an if/else structure. Like this (ignore the syntax, it's BASIC for readability):

```
if bottles == 2 
  print this line
else if bottles == 1
  print that line
else
  print the normal line
end if
```

---

### Post by LaRoza on 2008-08-02
> **ghostdog74 said:**
> and if its not 99 but 9999, are you going to type that many echoes? Use functions, mathematics in bash for the tasks. Read the bash link in my sig for more bash.

```

print "998 bottles of beer on the wall, 998 bottles of beer."
print "Take one down and pass it around, 997 bottles of beer on the wall.\n"
print "997 bottles of beer on the wall, 997 bottles of beer."
print "Take one down and pass it around, 996 bottles of beer on the wall.\n"
print "996 bottles of beer on the wall, 996 bottles of beer."
print "Take one down and pass it around, 995 bottles of beer on the wall.\n"
print "995 bottles of beer on the wall, 995 bottles of beer."
print "Take one down and pass it around, 994 bottles of beer on the wall.\n"
print "994 bottles of beer on the wall, 994 bottles of beer."
print "Take one down and pass it around, 993 bottles of beer on the wall.\n"
print "993 bottles of beer on the wall, 993 bottles of beer."
print "Take one down and pass it around, 992 bottles of beer on the wall.\n"
print "992 bottles of beer on the wall, 992 bottles of beer."
print "Take one down and pass it around, 991 bottles of beer on the wall.\n"
print "991 bottles of beer on the wall, 991 bottles of beer."
print "Take one down and pass it around, 990 bottles of beer on the wall.\n"
print "990 bottles of beer on the wall, 990 bottles of beer."
print "Take one down and pass it around, 989 bottles of beer on the wall.\n"
print "989 bottles of beer on the wall, 989 bottles of beer."
print "Take one down and pass it around, 988 bottles of beer on the wall.\n"
print "988 bottles of beer on the wall, 988 bottles of beer."
print "Take one down and pass it around, 987 bottles of beer on the wall.\n"
print "987 bottles of beer on the wall, 987 bottles of beer."
print "Take one down and pass it around, 986 bottles of beer on the wall.\n"
print "986 bottles of beer on the wall, 986 bottles of beer."
print "Take one down and pass it around, 985 bottles of beer on the wall.\n"
print "985 bottles of beer on the wall, 985 bottles of beer."
print "Take one down and pass it around, 984 bottles of beer on the wall.\n"
print "984 bottles of beer on the wall, 984 bottles of beer."
print "Take one down and pass it around, 983 bottles of beer on the wall.\n"
print "983 bottles of beer on the wall, 983 bottles of beer."
print "Take one down and pass it around, 982 bottles of beer on the wall.\n"
print "982 bottles of beer on the wall, 982 bottles of beer."
print "Take one down and pass it around, 981 bottles of beer on the wall.\n"
print "981 bottles of beer on the wall, 981 bottles of beer."
print "Take one down and pass it around, 980 bottles of beer on the wall.\n"
print "980 bottles of beer on the wall, 980 bottles of beer."
print "Take one down and pass it around, 979 bottles of beer on the wall.\n"
print "979 bottles of beer on the wall, 979 bottles of beer."
print "Take one down and pass it around, 978 bottles of beer on the wall.\n"
print "978 bottles of beer on the wall, 978 bottles of beer."
print "Take one down and pass it around, 977 bottles of beer on the wall.\n"
print "977 bottles of beer on the wall, 977 bottles of beer."
print "Take one down and pass it around, 976 bottles of beer on the wall.\n"
print "976 bottles of beer on the wall, 976 bottles of beer."
print "Take one down and pass it around, 975 bottles of beer on the wall.\n"
print "975 bottles of beer on the wall, 975 bottles of beer."
print "Take one down and pass it around, 974 bottles of beer on the wall.\n"
print "974 bottles of beer on the wall, 974 bottles of beer."
print "Take one down and pass it around, 973 bottles of beer on the wall.\n"
print "973 bottles of beer on the wall, 973 bottles of beer."
print "Take one down and pass it around, 972 bottles of beer on the wall.\n"
print "972 bottles of beer on the wall, 972 bottles of beer."
print "Take one down and pass it around, 971 bottles of beer on the wall.\n"
print "971 bottles of beer on the wall, 971 bottles of beer."
print "Take one down and pass it around, 970 bottles of beer on the wall.\n"
print "970 bottles of beer on the wall, 970 bottles of beer."
print "Take one down and pass it around, 969 bottles of beer on the wall.\n"
print "969 bottles of beer on the wall, 969 bottles of beer."
print "Take one down and pass it around, 968 bottles of beer on the wall.\n"
print "968 bottles of beer on the wall, 968 bottles of beer."
print "Take one down and pass it around, 967 bottles of beer on the wall.\n"
print "967 bottles of beer on the wall, 967 bottles of beer."
print "Take one down and pass it around, 966 bottles of beer on the wall.\n"
print "966 bottles of beer on the wall, 966 bottles of beer."
print "Take one down and pass it around, 965 bottles of beer on the wall.\n"
print "965 bottles of beer on the wall, 965 bottles of beer."
print "Take one down and pass it around, 964 bottles of beer on the wall.\n"
print "964 bottles of beer on the wall, 964 bottles of beer."
print "Take one down and pass it around, 963 bottles of beer on the wall.\n"
print "963 bottles of beer on the wall, 963 bottles of beer."
print "Take one down and pass it around, 962 bottles of beer on the wall.\n"
print "962 bottles of beer on the wall, 962 bottles of beer."
print "Take one down and pass it around, 961 bottles of beer on the wall.\n"
print "961 bottles of beer on the wall, 961 bottles of beer."
print "Take one down and pass it around, 960 bottles of beer on the wall.\n"
print "960 bottles of beer on the wall, 960 bottles of beer."
print "Take one down and pass it around, 959 bottles of beer on the wall.\n"
print "959 bottles of beer on the wall, 959 bottles of beer."
print "Take one down and pass it around, 958 bottles of beer on the wall.\n"
print "958 bottles of beer on the wall, 958 bottles of beer."
print "Take one down and pass it around, 957 bottles of beer on the wall.\n"
print "957 bottles of beer on the wall, 957 bottles of beer."
print "Take one down and pass it around, 956 bottles of beer on the wall.\n"
print "956 bottles of beer on the wall, 956 bottles of beer."
print "Take one down and pass it around, 955 bottles of beer on the wall.\n"
print "955 bottles of beer on the wall, 955 bottles of beer."
print "Take one down and pass it around, 954 bottles of beer on the wall.\n"
print "954 bottles of beer on the wall, 954 bottles of beer."
print "Take one down and pass it around, 953 bottles of beer on the wall.\n"
print "953 bottles of beer on the wall, 953 bottles of beer."
print "Take one down and pass it around, 952 bottles of beer on the wall.\n"
print "952 bottles of beer on the wall, 952 bottles of beer."
print "Take one down and pass it around, 951 bottles of beer on the wall.\n"
print "951 bottles of beer on the wall, 951 bottles of beer."
print "Take one down and pass it around, 950 bottles of beer on the wall.\n"
print "950 bottles of beer on the wall, 950 bottles of beer."
print "Take one down and pass it around, 949 bottles of beer on the wall.\n"
print "949 bottles of beer on the wall, 949 bottles of beer."
print "Take one down and pass it around, 948 bottles of beer on the wall.\n"
print "948 bottles of beer on the wall, 948 bottles of beer."
print "Take one down and pass it around, 947 bottles of beer on the wall.\n"
print "947 bottles of beer on the wall, 947 bottles of beer."
print "Take one down and pass it around, 946 bottles of beer on the wall.\n"
print "946 bottles of beer on the wall, 946 bottles of beer."
print "Take one down and pass it around, 945 bottles of beer on the wall.\n"
print "945 bottles of beer on the wall, 945 bottles of beer."
print "Take one down and pass it around, 944 bottles of beer on the wall.\n"
print "944 bottles of beer on the wall, 944 bottles of beer."
print "Take one down and pass it around, 943 bottles of beer on the wall.\n"
print "943 bottles of beer on the wall, 943 bottles of beer."
print "Take one down and pass it around, 942 bottles of beer on the wall.\n"
print "942 bottles of beer on the wall, 942 bottles of beer."
print "Take one down and pass it around, 941 bottles of beer on the wall.\n"
print "941 bottles of beer on the wall, 941 bottles of beer."
print "Take one down and pass it around, 940 bottles of beer on the wall.\n"
print "940 bottles of beer on the wall, 940 bottles of beer."
print "Take one down and pass it around, 939 bottles of beer on the wall.\n"
print "939 bottles of beer on the wall, 939 bottles of beer."
print "Take one down and pass it around, 938 bottles of beer on the wall.\n"
print "938 bottles of beer on the wall, 938 bottles of beer."
print "Take one down and pass it around, 937 bottles of beer on the wall.\n"
print "937 bottles of beer on the wall, 937 bottles of beer."
print "Take one down and pass it around, 936 bottles of beer on the wall.\n"
print "936 bottles of beer on the wall, 936 bottles of beer."
print "Take one down and pass it around, 935 bottles of beer on the wall.\n"
print "935 bottles of beer on the wall, 935 bottles of beer."
print "Take one down and pass it around, 934 bottles of beer on the wall.\n"
print "934 bottles of beer on the wall, 934 bottles of beer."
print "Take one down and pass it around, 933 bottles of beer on the wall.\n"
print "933 bottles of beer on the wall, 933 bottles of beer."
print "Take one down and pass it around, 932 bottles of beer on the wall.\n"
print "932 bottles of beer on the wall, 932 bottles of beer."
print "Take one down and pass it around, 931 bottles of beer on the wall.\n"
print "931 bottles of beer on the wall, 931 bottles of beer."
print "Take one down and pass it around, 930 bottles of beer on the wall.\n"
print "930 bottles of beer on the wall, 930 bottles of beer."
print "Take one down and pass it around, 929 bottles of beer on the wall.\n"
print "929 bottles of beer on the wall, 929 bottles of beer."
print "Take one down and pass it around, 928 bottles of beer on the wall.\n"
print "928 bottles of beer on the wall, 928 bottles of beer."
print "Take one down and pass it around, 927 bottles of beer on the wall.\n"
print "927 bottles of beer on the wall, 927 bottles of beer."
print "Take one down and pass it around, 926 bottles of beer on the wall.\n"
print "926 bottles of beer on the wall, 926 bottles of beer."
print "Take one down and pass it around, 925 bottles of beer on the wall.\n"
print "925 bottles of beer on the wall, 925 bottles of beer."
print "Take one down and pass it around, 924 bottles of beer on the wall.\n"
print "924 bottles of beer on the wall, 924 bottles of beer."
print "Take one down and pass it around, 923 bottles of beer on the wall.\n"
print "923 bottles of beer on the wall, 923 bottles of beer."
print "Take one down and pass it around, 922 bottles of beer on the wall.\n"
print "922 bottles of beer on the wall, 922 bottles of beer."
print "Take one down and pass it around, 921 bottles of beer on the wall.\n"
print "921 bottles of beer on the wall, 921 bottles of beer."
print "Take one down and pass it around, 920 bottles of beer on the wall.\n"
print "920 bottles of beer on the wall, 920 bottles of beer."
print "Take one down and pass it around, 919 bottles of beer on the wall.\n"
print "919 bottles of beer on the wall, 919 bottles of beer."
print "Take one down and pass it around, 918 bottles of beer on the wall.\n"
print "918 bottles of beer on the wall, 918 bottles of beer."
print "Take one down and pass it around, 917 bottles of beer on the wall.\n"
print "917 bottles of beer on the wall, 917 bottles of beer."
print "Take one down and pass it around, 916 bottles of beer on the wall.\n"
print "916 bottles of beer on the wall, 916 bottles of beer."
print "Take one down and pass it around, 915 bottles of beer on the wall.\n"
print "915 bottles of beer on the wall, 915 bottles of beer."
print "Take one down and pass it around, 914 bottles of beer on the wall.\n"
print "914 bottles of beer on the wall, 914 bottles of beer."
print "Take one down and pass it around, 913 bottles of beer on the wall.\n"
print "913 bottles of beer on the wall, 913 bottles of beer."
print "Take one down and pass it around, 912 bottles of beer on the wall.\n"
print "912 bottles of beer on the wall, 912 bottles of beer."
print "Take one down and pass it around, 911 bottles of beer on the wall.\n"
print "911 bottles of beer on the wall, 911 bottles of beer."
print "Take one down and pass it around, 910 bottles of beer on the wall.\n"
print "910 bottles of beer on the wall, 910 bottles of beer."
print "Take one down and pass it around, 909 bottles of beer on the wall.\n"
print "909 bottles of beer on the wall, 909 bottles of beer."
print "Take one down and pass it around, 908 bottles of beer on the wall.\n"
print "908 bottles of beer on the wall, 908 bottles of beer."
print "Take one down and pass it around, 907 bottles of beer on the wall.\n"
print "907 bottles of beer on the wall, 907 bottles of beer."
print "Take one down and pass it around, 906 bottles of beer on the wall.\n"
print "906 bottles of beer on the wall, 906 bottles of beer."
print "Take one down and pass it around, 905 bottles of beer on the wall.\n"
print "905 bottles of beer on the wall, 905 bottles of beer."
print "Take one down and pass it around, 904 bottles of beer on the wall.\n"
print "904 bottles of beer on the wall, 904 bottles of beer."
print "Take one down and pass it around, 903 bottles of beer on the wall.\n"
print "903 bottles of beer on the wall, 903 bottles of beer."
print "Take one down and pass it around, 902 bottles of beer on the wall.\n"
print "902 bottles of beer on the wall, 902 bottles of beer."
print "Take one down and pass it around, 901 bottles of beer on the wall.\n"
print "901 bottles of beer on the wall, 901 bottles of beer."
print "Take one down and pass it around, 900 bottles of beer on the wall.\n"
print "900 bottles of beer on the wall, 900 bottles of beer."
print "Take one down and pass it around, 899 bottles of beer on the wall.\n"
print "899 bottles of beer on the wall, 899 bottles of beer."
print "Take one down and pass it around, 898 bottles of beer on the wall.\n"
print "898 bottles of beer on the wall, 898 bottles of beer."
print "Take one down and pass it around, 897 bottles of beer on the wall.\n"
print "897 bottles of beer on the wall, 897 bottles of beer."
print "Take one down and pass it around, 896 bottles of beer on the wall.\n"
print "896 bottles of beer on the wall, 896 bottles of beer."
print "Take one down and pass it around, 895 bottles of beer on the wall.\n"
print "895 bottles of beer on the wall, 895 bottles of beer."
print "Take one down and pass it around, 894 bottles of beer on the wall.\n"
print "894 bottles of beer on the wall, 894 bottles of beer."
print "Take one down and pass it around, 893 bottles of beer on the wall.\n"
print "893 bottles of beer on the wall, 893 bottles of beer."
print "Take one down and pass it around, 892 bottles of beer on the wall.\n"
print "892 bottles of beer on the wall, 892 bottles of beer."
print "Take one down and pass it around, 891 bottles of beer on the wall.\n"
print "891 bottles of beer on the wall, 891 bottles of beer."
print "Take one down and pass it around, 890 bottles of beer on the wall.\n"
print "890 bottles of beer on the wall, 890 bottles of beer."
print "Take one down and pass it around, 889 bottles of beer on the wall.\n"
print "889 bottles of beer on the wall, 889 bottles of beer."
print "Take one down and pass it around, 888 bottles of beer on the wall.\n"
print "888 bottles of beer on the wall, 888 bottles of beer."
print "Take one down and pass it around, 887 bottles of beer on the wall.\n"
print "887 bottles of beer on the wall, 887 bottles of beer."
print "Take one down and pass it around, 886 bottles of beer on the wall.\n"
print "886 bottles of beer on the wall, 886 bottles of beer."
print "Take one down and pass it around, 885 bottles of beer on the wall.\n"
print "885 bottles of beer on the wall, 885 bottles of beer."
print "Take one down and pass it around, 884 bottles of beer on the wall.\n"
print "884 bottles of beer on the wall, 884 bottles of beer."
print "Take one down and pass it around, 883 bottles of beer on the wall.\n"
print "883 bottles of beer on the wall, 883 bottles of beer."
print "Take one down and pass it around, 882 bottles of beer on the wall.\n"
print "882 bottles of beer on the wall, 882 bottles of beer."
print "Take one down and pass it around, 881 bottles of beer on the wall.\n"
print "881 bottles of beer on the wall, 881 bottles of beer."
print "Take one down and pass it around, 880 bottles of beer on the wall.\n"
print "880 bottles of beer on the wall, 880 bottles of beer."
print "Take one down and pass it around, 879 bottles of beer on the wall.\n"
print "879 bottles of beer on the wall, 879 bottles of beer."
print "Take one down and pass it around, 878 bottles of beer on the wall.\n"
print "878 bottles of beer on the wall, 878 bottles of beer."
print "Take one down and pass it around, 877 bottles of beer on the wall.\n"
print "877 bottles of beer on the wall, 877 bottles of beer."
print "Take one down and pass it around, 876 bottles of beer on the wall.\n"
print "876 bottles of beer on the wall, 876 bottles of beer."
print "Take one down and pass it around, 875 bottles of beer on the wall.\n"
print "875 bottles of beer on the wall, 875 bottles of beer."
print "Take one down and pass it around, 874 bottles of beer on the wall.\n"
print "874 bottles of beer on the wall, 874 bottles of beer."
print "Take one down and pass it around, 873 bottles of beer on the wall.\n"
print "873 bottles of beer on the wall, 873 bottles of beer."
print "Take one down and pass it around, 872 bottles of beer on the wall.\n"
print "872 bottles of beer on the wall, 872 bottles of beer."
print "Take one down and pass it around, 871 bottles of beer on the wall.\n"
print "871 bottles of beer on the wall, 871 bottles of beer."
print "Take one down and pass it around, 870 bottles of beer on the wall.\n"
print "870 bottles of beer on the wall, 870 bottles of beer."
print "Take one down and pass it around, 869 bottles of beer on the wall.\n"
print "869 bottles of beer on the wall, 869 bottles of beer."
print "Take one down and pass it around, 868 bottles of beer on the wall.\n"
print "868 bottles of beer on the wall, 868 bottles of beer."
print "Take one down and pass it around, 867 bottles of beer on the wall.\n"
print "867 bottles of beer on the wall, 867 bottles of beer."
print "Take one down and pass it around, 866 bottles of beer on the wall.\n"
print "866 bottles of beer on the wall, 866 bottles of beer."
print "Take one down and pass it around, 865 bottles of beer on the wall.\n"
print "865 bottles of beer on the wall, 865 bottles of beer."
print "Take one down and pass it around, 864 bottles of beer on the wall.\n"
print "864 bottles of beer on the wall, 864 bottles of beer."
print "Take one down and pass it around, 863 bottles of beer on the wall.\n"
print "863 bottles of beer on the wall, 863 bottles of beer."
print "Take one down and pass it around, 862 bottles of beer on the wall.\n"
print "862 bottles of beer on the wall, 862 bottles of beer."
print "Take one down and pass it around, 861 bottles of beer on the wall.\n"
print "861 bottles of beer on the wall, 861 bottles of beer."
print "Take one down and pass it around, 860 bottles of beer on the wall.\n"
print "860 bottles of beer on the wall, 860 bottles of beer."
print "Take one down and pass it around, 859 bottles of beer on the wall.\n"
print "859 bottles of beer on the wall, 859 bottles of beer."
print "Take one down and pass it around, 858 bottles of beer on the wall.\n"
print "858 bottles of beer on the wall, 858 bottles of beer."
print "Take one down and pass it around, 857 bottles of beer on the wall.\n"
print "857 bottles of beer on the wall, 857 bottles of beer."
print "Take one down and pass it around, 856 bottles of beer on the wall.\n"
print "856 bottles of beer on the wall, 856 bottles of beer."
print "Take one down and pass it around, 855 bottles of beer on the wall.\n"
print "855 bottles of beer on the wall, 855 bottles of beer."
print "Take one down and pass it around, 854 bottles of beer on the wall.\n"
print "854 bottles of beer on the wall, 854 bottles of beer."
print "Take one down and pass it around, 853 bottles of beer on the wall.\n"
print "853 bottles of beer on the wall, 853 bottles of beer."
print "Take one down and pass it around, 852 bottles of beer on the wall.\n"
print "852 bottles of beer on the wall, 852 bottles of beer."
print "Take one down and pass it around, 851 bottles of beer on the wall.\n"
print "851 bottles of beer on the wall, 851 bottles of beer."
print "Take one down and pass it around, 850 bottles of beer on the wall.\n"
print "850 bottles of beer on the wall, 850 bottles of beer."
print "Take one down and pass it around, 849 bottles of beer on the wall.\n"
print "849 bottles of beer on the wall, 849 bottles of beer."
print "Take one down and pass it around, 848 bottles of beer on the wall.\n"
print "848 bottles of beer on the wall, 848 bottles of beer."
print "Take one down and pass it around, 847 bottles of beer on the wall.\n"
print "847 bottles of beer on the wall, 847 bottles of beer."
print "Take one down and pass it around, 846 bottles of beer on the wall.\n"
print "846 bottles of beer on the wall, 846 bottles of beer."
print "Take one down and pass it around, 845 bottles of beer on the wall.\n"
print "845 bottles of beer on the wall, 845 bottles of beer."
print "Take one down and pass it around, 844 bottles of beer on the wall.\n"
print "844 bottles of beer on the wall, 844 bottles of beer."
print "Take one down and pass it around, 843 bottles of beer on the wall.\n"
print "843 bottles of beer on the wall, 843 bottles of beer."
print "Take one down and pass it around, 842 bottles of beer on the wall.\n"
print "842 bottles of beer on the wall, 842 bottles of beer."
print "Take one down and pass it around, 841 bottles of beer on the wall.\n"
print "841 bottles of beer on the wall, 841 bottles of beer."
print "Take one down and pass it around, 840 bottles of beer on the wall.\n"
print "840 bottles of beer on the wall, 840 bottles of beer."
print "Take one down and pass it around, 839 bottles of beer on the wall.\n"
print "839 bottles of beer on the wall, 839 bottles of beer."
print "Take one down and pass it around, 838 bottles of beer on the wall.\n"
print "838 bottles of beer on the wall, 838 bottles of beer."
print "Take one down and pass it around, 837 bottles of beer on the wall.\n"
print "837 bottles of beer on the wall, 837 bottles of beer."
print "Take one down and pass it around, 836 bottles of beer on the wall.\n"
print "836 bottles of beer on the wall, 836 bottles of beer."
print "Take one down and pass it around, 835 bottles of beer on the wall.\n"
print "835 bottles of beer on the wall, 835 bottles of beer."
print "Take one down and pass it around, 834 bottles of beer on the wall.\n"
print "834 bottles of beer on the wall, 834 bottles of beer."
print "Take one down and pass it around, 833 bottles of beer on the wall.\n"
print "833 bottles of beer on the wall, 833 bottles of beer."
print "Take one down and pass it around, 832 bottles of beer on the wall.\n"
print "832 bottles of beer on the wall, 832 bottles of beer."
print "Take one down and pass it around, 831 bottles of beer on the wall.\n"
print "831 bottles of beer on the wall, 831 bottles of beer."
print "Take one down and pass it around, 830 bottles of beer on the wall.\n"
print "830 bottles of beer on the wall, 830 bottles of beer."
print "Take one down and pass it around, 829 bottles of beer on the wall.\n"
print "829 bottles of beer on the wall, 829 bottles of beer."
print "Take one down and pass it around, 828 bottles of beer on the wall.\n"
print "828 bottles of beer on the wall, 828 bottles of beer."
print "Take one down and pass it around, 827 bottles of beer on the wall.\n"
print "827 bottles of beer on the wall, 827 bottles of beer."
print "Take one down and pass it around, 826 bottles of beer on the wall.\n"
print "826 bottles of beer on the wall, 826 bottles of beer."
print "Take one down and pass it around, 825 bottles of beer on the wall.\n"
print "825 bottles of beer on the wall, 825 bottles of beer."
print "Take one down and pass it around, 824 bottles of beer on the wall.\n"
print "824 bottles of beer on the wall, 824 bottles of beer."
print "Take one down and pass it around, 823 bottles of beer on the wall.\n"
print "823 bottles of beer on the wall, 823 bottles of beer."
print "Take one down and pass it around, 822 bottles of beer on the wall.\n"
print "822 bottles of beer on the wall, 822 bottles of beer."
print "Take one down and pass it around, 821 bottles of beer on the wall.\n"
print "821 bottles of beer on the wall, 821 bottles of beer."
print "Take one down and pass it around, 820 bottles of beer on the wall.\n"
print "820 bottles of beer on the wall, 820 bottles of beer."
print "Take one down and pass it around, 819 bottles of beer on the wall.\n"
print "819 bottles of beer on the wall, 819 bottles of beer."
print "Take one down and pass it around, 818 bottles of beer on the wall.\n"
print "818 bottles of beer on the wall, 818 bottles of beer."
print "Take one down and pass it around, 817 bottles of beer on the wall.\n"
print "817 bottles of beer on the wall, 817 bottles of beer."
print "Take one down and pass it around, 816 bottles of beer on the wall.\n"
print "816 bottles of beer on the wall, 816 bottles of beer."
print "Take one down and pass it around, 815 bottles of beer on the wall.\n"
print "815 bottles of beer on the wall, 815 bottles of beer."
print "Take one down and pass it around, 814 bottles of beer on the wall.\n"
print "814 bottles of beer on the wall, 814 bottles of beer."
print "Take one down and pass it around, 813 bottles of beer on the wall.\n"
print "813 bottles of beer on the wall, 813 bottles of beer."
print "Take one down and pass it around, 812 bottles of beer on the wall.\n"
print "812 bottles of beer on the wall, 812 bottles of beer."
print "Take one down and pass it around, 811 bottles of beer on the wall.\n"
print "811 bottles of beer on the wall, 811 bottles of beer."
print "Take one down and pass it around, 810 bottles of beer on the wall.\n"
print "810 bottles of beer on the wall, 810 bottles of beer."
print "Take one down and pass it around, 809 bottles of beer on the wall.\n"
print "809 bottles of beer on the wall, 809 bottles of beer."
print "Take one down and pass it around, 808 bottles of beer on the wall.\n"
print "808 bottles of beer on the wall, 808 bottles of beer."
print "Take one down and pass it around, 807 bottles of beer on the wall.\n"
print "807 bottles of beer on the wall, 807 bottles of beer."
print "Take one down and pass it around, 806 bottles of beer on the wall.\n"
print "806 bottles of beer on the wall, 806 bottles of beer."
print "Take one down and pass it around, 805 bottles of beer on the wall.\n"
print "805 bottles of beer on the wall, 805 bottles of beer."
print "Take one down and pass it around, 804 bottles of beer on the wall.\n"
print "804 bottles of beer on the wall, 804 bottles of beer."
print "Take one down and pass it around, 803 bottles of beer on the wall.\n"
print "803 bottles of beer on the wall, 803 bottles of beer."
print "Take one down and pass it around, 802 bottles of beer on the wall.\n"
print "802 bottles of beer on the wall, 802 bottles of beer."
print "Take one down and pass it around, 801 bottles of beer on the wall.\n"
print "801 bottles of beer on the wall, 801 bottles of beer."
print "Take one down and pass it around, 800 bottles of beer on the wall.\n"
print "800 bottles of beer on the wall, 800 bottles of beer."
print "Take one down and pass it around, 799 bottles of beer on the wall.\n"
print "799 bottles of beer on the wall, 799 bottles of beer."
print "Take one down and pass it around, 798 bottles of beer on the wall.\n"
print "798 bottles of beer on the wall, 798 bottles of beer."
print "Take one down and pass it around, 797 bottles of beer on the wall.\n"
print "797 bottles of beer on the wall, 797 bottles of beer."
print "Take one down and pass it around, 796 bottles of beer on the wall.\n"
print "796 bottles of beer on the wall, 796 bottles of beer."
print "Take one down and pass it around, 795 bottles of beer on the wall.\n"
print "795 bottles of beer on the wall, 795 bottles of beer."
print "Take one down and pass it around, 794 bottles of beer on the wall.\n"
print "794 bottles of beer on the wall, 794 bottles of beer."
print "Take one down and pass it around, 793 bottles of beer on the wall.\n"
print "793 bottles of beer on the wall, 793 bottles of beer."
print "Take one down and pass it around, 792 bottles of beer on the wall.\n"
print "792 bottles of beer on the wall, 792 bottles of beer."
print "Take one down and pass it around, 791 bottles of beer on the wall.\n"
print "791 bottles of beer on the wall, 791 bottles of beer."
print "Take one down and pass it around, 790 bottles of beer on the wall.\n"
print "790 bottles of beer on the wall, 790 bottles of beer."
print "Take one down and pass it around, 789 bottles of beer on the wall.\n"
print "789 bottles of beer on the wall, 789 bottles of beer."
print "Take one down and pass it around, 788 bottles of beer on the wall.\n"
print "788 bottles of beer on the wall, 788 bottles of beer."
print "Take one down and pass it around, 787 bottles of beer on the wall.\n"
print "787 bottles of beer on the wall, 787 bottles of beer."
print "Take one down and pass it around, 786 bottles of beer on the wall.\n"
print "786 bottles of beer on the wall, 786 bottles of beer."
print "Take one down and pass it around, 785 bottles of beer on the wall.\n"
print "785 bottles of beer on the wall, 785 bottles of beer."
print "Take one down and pass it around, 784 bottles of beer on the wall.\n"
print "784 bottles of beer on the wall, 784 bottles of beer."
print "Take one down and pass it around, 783 bottles of beer on the wall.\n"
print "783 bottles of beer on the wall, 783 bottles of beer."
print "Take one down and pass it around, 782 bottles of beer on the wall.\n"
print "782 bottles of beer on the wall, 782 bottles of beer."
print "Take one down and pass it around, 781 bottles of beer on the wall.\n"
print "781 bottles of beer on the wall, 781 bottles of beer."
print "Take one down and pass it around, 780 bottles of beer on the wall.\n"
print "780 bottles of beer on the wall, 780 bottles of beer."
print "Take one down and pass it around, 779 bottles of beer on the wall.\n"
print "779 bottles of beer on the wall, 779 bottles of beer."
print "Take one down and pass it around, 778 bottles of beer on the wall.\n"
print "778 bottles of beer on the wall, 778 bottles of beer."
print "Take one down and pass it around, 777 bottles of beer on the wall.\n"
print "777 bottles of beer on the wall, 777 bottles of beer."
print "Take one down and pass it around, 776 bottles of beer on the wall.\n"
print "776 bottles of beer on the wall, 776 bottles of beer."
print "Take one down and pass it around, 775 bottles of beer on the wall.\n"
print "775 bottles of beer on the wall, 775 bottles of beer."
print "Take one down and pass it around, 774 bottles of beer on the wall.\n"
print "774 bottles of beer on the wall, 774 bottles of beer."
print "Take one down and pass it around, 773 bottles of beer on the wall.\n"
print "773 bottles of beer on the wall, 773 bottles of beer."
print "Take one down and pass it around, 772 bottles of beer on the wall.\n"
print "772 bottles of beer on the wall, 772 bottles of beer."
print "Take one down and pass it around, 771 bottles of beer on the wall.\n"
print "771 bottles of beer on the wall, 771 bottles of beer."
print "Take one down and pass it around, 770 bottles of beer on the wall.\n"
print "770 bottles of beer on the wall, 770 bottles of beer."
print "Take one down and pass it around, 769 bottles of beer on the wall.\n"
print "769 bottles of beer on the wall, 769 bottles of beer."
print "Take one down and pass it around, 768 bottles of beer on the wall.\n"
print "768 bottles of beer on the wall, 768 bottles of beer."
print "Take one down and pass it around, 767 bottles of beer on the wall.\n"
print "767 bottles of beer on the wall, 767 bottles of beer."
print "Take one down and pass it around, 766 bottles of beer on the wall.\n"
print "766 bottles of beer on the wall, 766 bottles of beer."
print "Take one down and pass it around, 765 bottles of beer on the wall.\n"
print "765 bottles of beer on the wall, 765 bottles of beer."
print "Take one down and pass it around, 764 bottles of beer on the wall.\n"
print "764 bottles of beer on the wall, 764 bottles of beer."
print "Take one down and pass it around, 763 bottles of beer on the wall.\n"
print "763 bottles of beer on the wall, 763 bottles of beer."
print "Take one down and pass it around, 762 bottles of beer on the wall.\n"
print "762 bottles of beer on the wall, 762 bottles of beer."
print "Take one down and pass it around, 761 bottles of beer on the wall.\n"
print "761 bottles of beer on the wall, 761 bottles of beer."
print "Take one down and pass it around, 760 bottles of beer on the wall.\n"
print "760 bottles of beer on the wall, 760 bottles of beer."
print "Take one down and pass it around, 759 bottles of beer on the wall.\n"
print "759 bottles of beer on the wall, 759 bottles of beer."
print "Take one down and pass it around, 758 bottles of beer on the wall.\n"
print "758 bottles of beer on the wall, 758 bottles of beer."
print "Take one down and pass it around, 757 bottles of beer on the wall.\n"
print "757 bottles of beer on the wall, 757 bottles of beer."
print "Take one down and pass it around, 756 bottles of beer on the wall.\n"
print "756 bottles of beer on the wall, 756 bottles of beer."
print "Take one down and pass it around, 755 bottles of beer on the wall.\n"
print "755 bottles of beer on the wall, 755 bottles of beer."
print "Take one down and pass it around, 754 bottles of beer on the wall.\n"
print "754 bottles of beer on the wall, 754 bottles of beer."
print "Take one down and pass it around, 753 bottles of beer on the wall.\n"
print "753 bottles of beer on the wall, 753 bottles of beer."
print "Take one down and pass it around, 752 bottles of beer on the wall.\n"
print "752 bottles of beer on the wall, 752 bottles of beer."
print "Take one down and pass it around, 751 bottles of beer on the wall.\n"
print "751 bottles of beer on the wall, 751 bottles of beer."
print "Take one down and pass it around, 750 bottles of beer on the wall.\n"
print "750 bottles of beer on the wall, 750 bottles of beer."
print "Take one down and pass it around, 749 bottles of beer on the wall.\n"
print "749 bottles of beer on the wall, 749 bottles of beer."
print "Take one down and pass it around, 748 bottles of beer on the wall.\n"
print "748 bottles of beer on the wall, 748 bottles of beer."
print "Take one down and pass it around, 747 bottles of beer on the wall.\n"
print "747 bottles of beer on the wall, 747 bottles of beer."
print "Take one down and pass it around, 746 bottles of beer on the wall.\n"
print "746 bottles of beer on the wall, 746 bottles of beer."
print "Take one down and pass it around, 745 bottles of beer on the wall.\n"
print "745 bottles of beer on the wall, 745 bottles of beer."
print "Take one down and pass it around, 744 bottles of beer on the wall.\n"
print "744 bottles of beer on the wall, 744 bottles of beer."
print "Take one down and pass it around, 743 bottles of beer on the wall.\n"
print "743 bottles of beer on the wall, 743 bottles of beer."
print "Take one down and pass it around, 742 bottles of beer on the wall.\n"
print "742 bottles of beer on the wall, 742 bottles of beer."
print "Take one down and pass it around, 741 bottles of beer on the wall.\n"
print "741 bottles of beer on the wall, 741 bottles of beer."
print "Take one down and pass it around, 740 bottles of beer on the wall.\n"
print "740 bottles of beer on the wall, 740 bottles of beer."
print "Take one down and pass it around, 739 bottles of beer on the wall.\n"
print "739 bottles of beer on the wall, 739 bottles of beer."
print "Take one down and pass it around, 738 bottles of beer on the wall.\n"
print "738 bottles of beer on the wall, 738 bottles of beer."
print "Take one down and pass it around, 737 bottles of beer on the wall.\n"
print "737 bottles of beer on the wall, 737 bottles of beer."
print "Take one down and pass it around, 736 bottles of beer on the wall.\n"
print "736 bottles of beer on the wall, 736 bottles of beer."
print "Take one down and pass it around, 735 bottles of beer on the wall.\n"
print "735 bottles of beer on the wall, 735 bottles of beer."
print "Take one down and pass it around, 734 bottles of beer on the wall.\n"
print "734 bottles of beer on the wall, 734 bottles of beer."
print "Take one down and pass it around, 733 bottles of beer on the wall.\n"
print "733 bottles of beer on the wall, 733 bottles of beer."
print "Take one down and pass it around, 732 bottles of beer on the wall.\n"
print "732 bottles of beer on the wall, 732 bottles of beer."
print "Take one down and pass it around, 731 bottles of beer on the wall.\n"
print "731 bottles of beer on the wall, 731 bottles of beer."
print "Take one down and pass it around, 730 bottles of beer on the wall.\n"
print "730 bottles of beer on the wall, 730 bottles of beer."
print "Take one down and pass it around, 729 bottles of beer on the wall.\n"
print "729 bottles of beer on the wall, 729 bottles of beer."
print "Take one down and pass it around, 728 bottles of beer on the wall.\n"
print "728 bottles of beer on the wall, 728 bottles of beer."
print "Take one down and pass it around, 727 bottles of beer on the wall.\n"
print "727 bottles of beer on the wall, 727 bottles of beer."
print "Take one down and pass it around, 726 bottles of beer on the wall.\n"
print "726 bottles of beer on the wall, 726 bottles of beer."
print "Take one down and pass it around, 725 bottles of beer on the wall.\n"
print "725 bottles of beer on the wall, 725 bottles of beer."
print "Take one down and pass it around, 724 bottles of beer on the wall.\n"
print "724 bottles of beer on the wall, 724 bottles of beer."
print "Take one down and pass it around, 723 bottles of beer on the wall.\n"
print "723 bottles of beer on the wall, 723 bottles of beer."
print "Take one down and pass it around, 722 bottles of beer on the wall.\n"
print "722 bottles of beer on the wall, 722 bottles of beer."
print "Take one down and pass it around, 721 bottles of beer on the wall.\n"
print "721 bottles of beer on the wall, 721 bottles of beer."
print "Take one down and pass it around, 720 bottles of beer on the wall.\n"
print "720 bottles of beer on the wall, 720 bottles of beer."
print "Take one down and pass it around, 719 bottles of beer on the wall.\n"
print "719 bottles of beer on the wall, 719 bottles of beer."
print "Take one down and pass it around, 718 bottles of beer on the wall.\n"
print "718 bottles of beer on the wall, 718 bottles of beer."
print "Take one down and pass it around, 717 bottles of beer on the wall.\n"
print "717 bottles of beer on the wall, 717 bottles of beer."
print "Take one down and pass it around, 716 bottles of beer on the wall.\n"
print "716 bottles of beer on the wall, 716 bottles of beer."
print "Take one down and pass it around, 715 bottles of beer on the wall.\n"
print "715 bottles of beer on the wall, 715 bottles of beer."
print "Take one down and pass it around, 714 bottles of beer on the wall.\n"
print "714 bottles of beer on the wall, 714 bottles of beer."
print "Take one down and pass it around, 713 bottles of beer on the wall.\n"
print "713 bottles of beer on the wall, 713 bottles of beer."
print "Take one down and pass it around, 712 bottles of beer on the wall.\n"
print "712 bottles of beer on the wall, 712 bottles of beer."
print "Take one down and pass it around, 711 bottles of beer on the wall.\n"
print "711 bottles of beer on the wall, 711 bottles of beer."
print "Take one down and pass it around, 710 bottles of beer on the wall.\n"
print "710 bottles of beer on the wall, 710 bottles of beer."
print "Take one down and pass it around, 709 bottles of beer on the wall.\n"
print "709 bottles of beer on the wall, 709 bottles of beer."
print "Take one down and pass it around, 708 bottles of beer on the wall.\n"
print "708 bottles of beer on the wall, 708 bottles of beer."
print "Take one down and pass it around, 707 bottles of beer on the wall.\n"
print "707 bottles of beer on the wall, 707 bottles of beer."
print "Take one down and pass it around, 706 bottles of beer on the wall.\n"
print "706 bottles of beer on the wall, 706 bottles of beer."
print "Take one down and pass it around, 705 bottles of beer on the wall.\n"
print "705 bottles of beer on the wall, 705 bottles of beer."
print "Take one down and pass it around, 704 bottles of beer on the wall.\n"
print "704 bottles of beer on the wall, 704 bottles of beer."
print "Take one down and pass it around, 703 bottles of beer on the wall.\n"
print "703 bottles of beer on the wall, 703 bottles of beer."
print "Take one down and pass it around, 702 bottles of beer on the wall.\n"
print "702 bottles of beer on the wall, 702 bottles of beer."
print "Take one down and pass it around, 701 bottles of beer on the wall.\n"
print "701 bottles of beer on the wall, 701 bottles of beer."
print "Take one down and pass it around, 700 bottles of beer on the wall.\n"
print "700 bottles of beer on the wall, 700 bottles of beer."
print "Take one down and pass it around, 699 bottles of beer on the wall.\n"
print "699 bottles of beer on the wall, 699 bottles of beer."
print "Take one down and pass it around, 698 bottles of beer on the wall.\n"
print "698 bottles of beer on the wall, 698 bottles of beer."
print "Take one down and pass it around, 697 bottles of beer on the wall.\n"
print "697 bottles of beer on the wall, 697 bottles of beer."
print "Take one down and pass it around, 696 bottles of beer on the wall.\n"
print "696 bottles of beer on the wall, 696 bottles of beer."
print "Take one down and pass it around, 695 bottles of beer on the wall.\n"
print "695 bottles of beer on the wall, 695 bottles of beer."
print "Take one down and pass it around, 694 bottles of beer on the wall.\n"
print "694 bottles of beer on the wall, 694 bottles of beer."
print "Take one down and pass it around, 693 bottles of beer on the wall.\n"
print "693 bottles of beer on the wall, 693 bottles of beer."
print "Take one down and pass it around, 692 bottles of beer on the wall.\n"
print "692 bottles of beer on the wall, 692 bottles of beer."
print "Take one down and pass it around, 691 bottles of beer on the wall.\n"
print "691 bottles of beer on the wall, 691 bottles of beer."
print "Take one down and pass it around, 690 bottles of beer on the wall.\n"
print "690 bottles of beer on the wall, 690 bottles of beer."
print "Take one down and pass it around, 689 bottles of beer on the wall.\n"
print "689 bottles of beer on the wall, 689 bottles of beer."
print "Take one down and pass it around, 688 bottles of beer on the wall.\n"
print "688 bottles of beer on the wall, 688 bottles of beer."
print "Take one down and pass it around, 687 bottles of beer on the wall.\n"
print "687 bottles of beer on the wall, 687 bottles of beer."
print "Take one down and pass it around, 686 bottles of beer on the wall.\n"
print "686 bottles of beer on the wall, 686 bottles of beer."
print "Take one down and pass it around, 685 bottles of beer on the wall.\n"
print "685 bottles of beer on the wall, 685 bottles of beer."
print "Take one down and pass it around, 684 bottles of beer on the wall.\n"
print "684 bottles of beer on the wall, 684 bottles of beer."
print "Take one down and pass it around, 683 bottles of beer on the wall.\n"
print "683 bottles of beer on the wall, 683 bottles of beer."
print "Take one down and pass it around, 682 bottles of beer on the wall.\n"
print "682 bottles of beer on the wall, 682 bottles of beer."
print "Take one down and pass it around, 681 bottles of beer on the wall.\n"
print "681 bottles of beer on the wall, 681 bottles of beer."
print "Take one down and pass it around, 680 bottles of beer on the wall.\n"
print "680 bottles of beer on the wall, 680 bottles of beer."
print "Take one down and pass it around, 679 bottles of beer on the wall.\n"
print "679 bottles of beer on the wall, 679 bottles of beer."
print "Take one down and pass it around, 678 bottles of beer on the wall.\n"
print "678 bottles of beer on the wall, 678 bottles of beer."
print "Take one down and pass it around, 677 bottles of beer on the wall.\n"
print "677 bottles of beer on the wall, 677 bottles of beer."
print "Take one down and pass it around, 676 bottles of beer on the wall.\n"
print "676 bottles of beer on the wall, 676 bottles of beer."
print "Take one down and pass it around, 675 bottles of beer on the wall.\n"
print "675 bottles of beer on the wall, 675 bottles of beer."
print "Take one down and pass it around, 674 bottles of beer on the wall.\n"
print "674 bottles of beer on the wall, 674 bottles of beer."
print "Take one down and pass it around, 673 bottles of beer on the wall.\n"
print "673 bottles of beer on the wall, 673 bottles of beer."
print "Take one down and pass it around, 672 bottles of beer on the wall.\n"
print "672 bottles of beer on the wall, 672 bottles of beer."
print "Take one down and pass it around, 671 bottles of beer on the wall.\n"
print "671 bottles of beer on the wall, 671 bottles of beer."
print "Take one down and pass it around, 670 bottles of beer on the wall.\n"
print "670 bottles of beer on the wall, 670 bottles of beer."
print "Take one down and pass it around, 669 bottles of beer on the wall.\n"
print "669 bottles of beer on the wall, 669 bottles of beer."
print "Take one down and pass it around, 668 bottles of beer on the wall.\n"
print "668 bottles of beer on the wall, 668 bottles of beer."
print "Take one down and pass it around, 667 bottles of beer on the wall.\n"
print "667 bottles of beer on the wall, 667 bottles of beer."
print "Take one down and pass it around, 666 bottles of beer on the wall.\n"
print "666 bottles of beer on the wall, 666 bottles of beer."
print "Take one down and pass it around, 665 bottles of beer on the wall.\n"
print "665 bottles of beer on the wall, 665 bottles of beer."
print "Take one down and pass it around, 664 bottles of beer on the wall.\n"
print "664 bottles of beer on the wall, 664 bottles of beer."
print "Take one down and pass it around, 663 bottles of beer on the wall.\n"
print "663 bottles of beer on the wall, 663 bottles of beer."
print "Take one down and pass it around, 662 bottles of beer on the wall.\n"
print "662 bottles of beer on the wall, 662 bottles of beer."
print "Take one down and pass it around, 661 bottles of beer on the wall.\n"
print "661 bottles of beer on the wall, 661 bottles of beer."
print "Take one down and pass it around, 660 bottles of beer on the wall.\n"
print "660 bottles of beer on the wall, 660 bottles of beer."
print "Take one down and pass it around, 659 bottles of beer on the wall.\n"
print "659 bottles of beer on the wall, 659 bottles of beer."
print "Take one down and pass it around, 658 bottles of beer on the wall.\n"
print "658 bottles of beer on the wall, 658 bottles of beer."
print "Take one down and pass it around, 657 bottles of beer on the wall.\n"
print "657 bottles of beer on the wall, 657 bottles of beer."
print "Take one down and pass it around, 656 bottles of beer on the wall.\n"
print "656 bottles of beer on the wall, 656 bottles of beer."
print "Take one down and pass it around, 655 bottles of beer on the wall.\n"
print "655 bottles of beer on the wall, 655 bottles of beer."
print "Take one down and pass it around, 654 bottles of beer on the wall.\n"
print "654 bottles of beer on the wall, 654 bottles of beer."
print "Take one down and pass it around, 653 bottles of beer on the wall.\n"
print "653 bottles of beer on the wall, 653 bottles of beer."
print "Take one down and pass it around, 652 bottles of beer on the wall.\n"
print "652 bottles of beer on the wall, 652 bottles of beer."
print "Take one down and pass it around, 651 bottles of beer on the wall.\n"
print "651 bottles of beer on the wall, 651 bottles of beer."
print "Take one down and pass it around, 650 bottles of beer on the wall.\n"
print "650 bottles of beer on the wall, 650 bottles of beer."
print "Take one down and pass it around, 649 bottles of beer on the wall.\n"
print "649 bottles of beer on the wall, 649 bottles of beer."
print "Take one down and pass it around, 648 bottles of beer on the wall.\n"
print "648 bottles of beer on the wall, 648 bottles of beer."
print "Take one down and pass it around, 647 bottles of beer on the wall.\n"
print "647 bottles of beer on the wall, 647 bottles of beer."
print "Take one down and pass it around, 646 bottles of beer on the wall.\n"
print "646 bottles of beer on the wall, 646 bottles of beer."
print "Take one down and pass it around, 645 bottles of beer on the wall.\n"
print "645 bottles of beer on the wall, 645 bottles of beer."
print "Take one down and pass it around, 644 bottles of beer on the wall.\n"
print "644 bottles of beer on the wall, 644 bottles of beer."
print "Take one down and pass it around, 643 bottles of beer on the wall.\n"
print "643 bottles of beer on the wall, 643 bottles of beer."
print "Take one down and pass it around, 642 bottles of beer on the wall.\n"
print "642 bottles of beer on the wall, 642 bottles of beer."
print "Take one down and pass it around, 641 bottles of beer on the wall.\n"
print "641 bottles of beer on the wall, 641 bottles of beer."
print "Take one down and pass it around, 640 bottles of beer on the wall.\n"
print "640 bottles of beer on the wall, 640 bottles of beer."
print "Take one down and pass it around, 639 bottles of beer on the wall.\n"
print "639 bottles of beer on the wall, 639 bottles of beer."
print "Take one down and pass it around, 638 bottles of beer on the wall.\n"
print "638 bottles of beer on the wall, 638 bottles of beer."
print "Take one down and pass it around, 637 bottles of beer on the wall.\n"
print "637 bottles of beer on the wall, 637 bottles of beer."
print "Take one down and pass it around, 636 bottles of beer on the wall.\n"
print "636 bottles of beer on the wall, 636 bottles of beer."
print "Take one down and pass it around, 635 bottles of beer on the wall.\n"
print "635 bottles of beer on the wall, 635 bottles of beer."
print "Take one down and pass it around, 634 bottles of beer on the wall.\n"
print "634 bottles of beer on the wall, 634 bottles of beer."
print "Take one down and pass it around, 633 bottles of beer on the wall.\n"
print "633 bottles of beer on the wall, 633 bottles of beer."
print "Take one down and pass it around, 632 bottles of beer on the wall.\n"
print "632 bottles of beer on the wall, 632 bottles of beer."
print "Take one down and pass it around, 631 bottles of beer on the wall.\n"
print "631 bottles of beer on the wall, 631 bottles of beer."
print "Take one down and pass it around, 630 bottles of beer on the wall.\n"
print "630 bottles of beer on the wall, 630 bottles of beer."
print "Take one down and pass it around, 629 bottles of beer on the wall.\n"
print "629 bottles of beer on the wall, 629 bottles of beer."
print "Take one down and pass it around, 628 bottles of beer on the wall.\n"
print "628 bottles of beer on the wall, 628 bottles of beer."
print "Take one down and pass it around, 627 bottles of beer on the wall.\n"
print "627 bottles of beer on the wall, 627 bottles of beer."
print "Take one down and pass it around, 626 bottles of beer on the wall.\n"
print "626 bottles of beer on the wall, 626 bottles of beer."
print "Take one down and pass it around, 625 bottles of beer on the wall.\n"
print "625 bottles of beer on the wall, 625 bottles of beer."
print "Take one down and pass it around, 624 bottles of beer on the wall.\n"
print "624 bottles of beer on the wall, 624 bottles of beer."
print "Take one down and pass it around, 623 bottles of beer on the wall.\n"
print "623 bottles of beer on the wall, 623 bottles of beer."
print "Take one down and pass it around, 622 bottles of beer on the wall.\n"
print "622 bottles of beer on the wall, 622 bottles of beer."
print "Take one down and pass it around, 621 bottles of beer on the wall.\n"
print "621 bottles of beer on the wall, 621 bottles of beer."
print "Take one down and pass it around, 620 bottles of beer on the wall.\n"
print "620 bottles of beer on the wall, 620 bottles of beer."
print "Take one down and pass it around, 619 bottles of beer on the wall.\n"
print "619 bottles of beer on the wall, 619 bottles of beer."
print "Take one down and pass it around, 618 bottles of beer on the wall.\n"
print "618 bottles of beer on the wall, 618 bottles of beer."
print "Take one down and pass it around, 617 bottles of beer on the wall.\n"
print "617 bottles of beer on the wall, 617 bottles of beer."
print "Take one down and pass it around, 616 bottles of beer on the wall.\n"
print "616 bottles of beer on the wall, 616 bottles of beer."
print "Take one down and pass it around, 615 bottles of beer on the wall.\n"
print "615 bottles of beer on the wall, 615 bottles of beer."
print "Take one down and pass it around, 614 bottles of beer on the wall.\n"
print "614 bottles of beer on the wall, 614 bottles of beer."
print "Take one down and pass it around, 613 bottles of beer on the wall.\n"
print "613 bottles of beer on the wall, 613 bottles of beer."
print "Take one down and pass it around, 612 bottles of beer on the wall.\n"
print "612 bottles of beer on the wall, 612 bottles of beer."
print "Take one down and pass it around, 611 bottles of beer on the wall.\n"
print "611 bottles of beer on the wall, 611 bottles of beer."
print "Take one down and pass it around, 610 bottles of beer on the wall.\n"
print "610 bottles of beer on the wall, 610 bottles of beer."
print "Take one down and pass it around, 609 bottles of beer on the wall.\n"
print "609 bottles of beer on the wall, 609 bottles of beer."
print "Take one down and pass it around, 608 bottles of beer on the wall.\n"
print "608 bottles of beer on the wall, 608 bottles of beer."
print "Take one down and pass it around, 607 bottles of beer on the wall.\n"
print "607 bottles of beer on the wall, 607 bottles of beer."
print "Take one down and pass it around, 606 bottles of beer on the wall.\n"
print "606 bottles of beer on the wall, 606 bottles of beer."
print "Take one down and pass it around, 605 bottles of beer on the wall.\n"
print "605 bottles of beer on the wall, 605 bottles of beer."
print "Take one down and pass it around, 604 bottles of beer on the wall.\n"
print "604 bottles of beer on the wall, 604 bottles of beer."
print "Take one down and pass it around, 603 bottles of beer on the wall.\n"
print "603 bottles of beer on the wall, 603 bottles of beer."
print "Take one down and pass it around, 602 bottles of beer on the wall.\n"
print "602 bottles of beer on the wall, 602 bottles of beer."
print "Take one down and pass it around, 601 bottles of beer on the wall.\n"
print "601 bottles of beer on the wall, 601 bottles of beer."
print "Take one down and pass it around, 600 bottles of beer on the wall.\n"
print "600 bottles of beer on the wall, 600 bottles of beer."
print "Take one down and pass it around, 599 bottles of beer on the wall.\n"
print "599 bottles of beer on the wall, 599 bottles of beer."
print "Take one down and pass it around, 598 bottles of beer on the wall.\n"
print "598 bottles of beer on the wall, 598 bottles of beer."
print "Take one down and pass it around, 597 bottles of beer on the wall.\n"
print "597 bottles of beer on the wall, 597 bottles of beer."
print "Take one down and pass it around, 596 bottles of beer on the wall.\n"
print "596 bottles of beer on the wall, 596 bottles of beer."
print "Take one down and pass it around, 595 bottles of beer on the wall.\n"
print "595 bottles of beer on the wall, 595 bottles of beer."
print "Take one down and pass it around, 594 bottles of beer on the wall.\n"
print "594 bottles of beer on the wall, 594 bottles of beer."
print "Take one down and pass it around, 593 bottles of beer on the wall.\n"
print "593 bottles of beer on the wall, 593 bottles of beer."
print "Take one down and pass it around, 592 bottles of beer on the wall.\n"
print "592 bottles of beer on the wall, 592 bottles of beer."
print "Take one down and pass it around, 591 bottles of beer on the wall.\n"
print "591 bottles of beer on the wall, 591 bottles of beer."
print "Take one down and pass it around, 590 bottles of beer on the wall.\n"
print "590 bottles of beer on the wall, 590 bottles of beer."
print "Take one down and pass it around, 589 bottles of beer on the wall.\n"
print "589 bottles of beer on the wall, 589 bottles of beer."
print "Take one down and pass it around, 588 bottles of beer on the wall.\n"
print "588 bottles of beer on the wall, 588 bottles of beer."
print "Take one down and pass it around, 587 bottles of beer on the wall.\n"
print "587 bottles of beer on the wall, 587 bottles of beer."
print "Take one down and pass it around, 586 bottles of beer on the wall.\n"
print "586 bottles of beer on the wall, 586 bottles of beer."
print "Take one down and pass it around, 585 bottles of beer on the wall.\n"
print "585 bottles of beer on the wall, 585 bottles of beer."
print "Take one down and pass it around, 584 bottles of beer on the wall.\n"
print "584 bottles of beer on the wall, 584 bottles of beer."
print "Take one down and pass it around, 583 bottles of beer on the wall.\n"
print "583 bottles of beer on the wall, 583 bottles of beer."
print "Take one down and pass it around, 582 bottles of beer on the wall.\n"
print "582 bottles of beer on the wall, 582 bottles of beer."
print "Take one down and pass it around, 581 bottles of beer on the wall.\n"
print "581 bottles of beer on the wall, 581 bottles of beer."
print "Take one down and pass it around, 580 bottles of beer on the wall.\n"
print "580 bottles of beer on the wall, 580 bottles of beer."
print "Take one down and pass it around, 579 bottles of beer on the wall.\n"
print "579 bottles of beer on the wall, 579 bottles of beer."
print "Take one down and pass it around, 578 bottles of beer on the wall.\n"
print "578 bottles of beer on the wall, 578 bottles of beer."
print "Take one down and pass it around, 577 bottles of beer on the wall.\n"
print "577 bottles of beer on the wall, 577 bottles of beer."
print "Take one down and pass it around, 576 bottles of beer on the wall.\n"
print "576 bottles of beer on the wall, 576 bottles of beer."
print "Take one down and pass it around, 575 bottles of beer on the wall.\n"
print "575 bottles of beer on the wall, 575 bottles of beer."
print "Take one down and pass it around, 574 bottles of beer on the wall.\n"
print "574 bottles of beer on the wall, 574 bottles of beer."
print "Take one down and pass it around, 573 bottles of beer on the wall.\n"
print "573 bottles of beer on the wall, 573 bottles of beer."
print "Take one down and pass it around, 572 bottles of beer on the wall.\n"
print "572 bottles of beer on the wall, 572 bottles of beer."
print "Take one down and pass it around, 571 bottles of beer on the wall.\n"
print "571 bottles of beer on the wall, 571 bottles of beer."
print "Take one down and pass it around, 570 bottles of beer on the wall.\n"
print "570 bottles of beer on the wall, 570 bottles of beer."
print "Take one down and pass it around, 569 bottles of beer on the wall.\n"
print "569 bottles of beer on the wall, 569 bottles of beer."
print "Take one down and pass it around, 568 bottles of beer on the wall.\n"
print "568 bottles of beer on the wall, 568 bottles of beer."
print "Take one down and pass it around, 567 bottles of beer on the wall.\n"
print "567 bottles of beer on the wall, 567 bottles of beer."
print "Take one down and pass it around, 566 bottles of beer on the wall.\n"
print "566 bottles of beer on the wall, 566 bottles of beer."
print "Take one down and pass it around, 565 bottles of beer on the wall.\n"
print "565 bottles of beer on the wall, 565 bottles of beer."
print "Take one down and pass it around, 564 bottles of beer on the wall.\n"
print "564 bottles of beer on the wall, 564 bottles of beer."
print "Take one down and pass it around, 563 bottles of beer on the wall.\n"
print "563 bottles of beer on the wall, 563 bottles of beer."
print "Take one down and pass it around, 562 bottles of beer on the wall.\n"
print "562 bottles of beer on the wall, 562 bottles of beer."
print "Take one down and pass it around, 561 bottles of beer on the wall.\n"
print "561 bottles of beer on the wall, 561 bottles of beer."
print "Take one down and pass it around, 560 bottles of beer on the wall.\n"
print "560 bottles of beer on the wall, 560 bottles of beer."
print "Take one down and pass it around, 559 bottles of beer on the wall.\n"
print "559 bottles of beer on the wall, 559 bottles of beer."
print "Take one down and pass it around, 558 bottles of beer on the wall.\n"
print "558 bottles of beer on the wall, 558 bottles of beer."
print "Take one down and pass it around, 557 bottles of beer on the wall.\n"
print "557 bottles of beer on the wall, 557 bottles of beer."
print "Take one down and pass it around, 556 bottles of beer on the wall.\n"
print "556 bottles of beer on the wall, 556 bottles of beer."
print "Take one down and pass it around, 555 bottles of beer on the wall.\n"
print "555 bottles of beer on the wall, 555 bottles of beer."
print "Take one down and pass it around, 554 bottles of beer on the wall.\n"
print "554 bottles of beer on the wall, 554 bottles of beer."
print "Take one down and pass it around, 553 bottles of beer on the wall.\n"
print "553 bottles of beer on the wall, 553 bottles of beer."
print "Take one down and pass it around, 552 bottles of beer on the wall.\n"
print "552 bottles of beer on the wall, 552 bottles of beer."
print "Take one down and pass it around, 551 bottles of beer on the wall.\n"
print "551 bottles of beer on the wall, 551 bottles of beer."
print "Take one down and pass it around, 550 bottles of beer on the wall.\n"
print "550 bottles of beer on the wall, 550 bottles of beer."
print "Take one down and pass it around, 549 bottles of beer on the wall.\n"
print "549 bottles of beer on the wall, 549 bottles of beer."
print "Take one down and pass it around, 548 bottles of beer on the wall.\n"
print "548 bottles of beer on the wall, 548 bottles of beer."
print "Take one down and pass it around, 547 bottles of beer on the wall.\n"
print "547 bottles of beer on the wall, 547 bottles of beer."
print "Take one down and pass it around, 546 bottles of beer on the wall.\n"
print "546 bottles of beer on the wall, 546 bottles of beer."
print "Take one down and pass it around, 545 bottles of beer on the wall.\n"
print "545 bottles of beer on the wall, 545 bottles of beer."
print "Take one down and pass it around, 544 bottles of beer on the wall.\n"
print "544 bottles of beer on the wall, 544 bottles of beer."
print "Take one down and pass it around, 543 bottles of beer on the wall.\n"
print "543 bottles of beer on the wall, 543 bottles of beer."
print "Take one down and pass it around, 542 bottles of beer on the wall.\n"
print "542 bottles of beer on the wall, 542 bottles of beer."
print "Take one down and pass it around, 541 bottles of beer on the wall.\n"
print "541 bottles of beer on the wall, 541 bottles of beer."
print "Take one down and pass it around, 540 bottles of beer on the wall.\n"
print "540 bottles of beer on the wall, 540 bottles of beer."
print "Take one down and pass it around, 539 bottles of beer on the wall.\n"
print "539 bottles of beer on the wall, 539 bottles of beer."
print "Take one down and pass it around, 538 bottles of beer on the wall.\n"
print "538 bottles of beer on the wall, 538 bottles of beer."
print "Take one down and pass it around, 537 bottles of beer on the wall.\n"
print "537 bottles of beer on the wall, 537 bottles of beer."
print "Take one down and pass it around, 536 bottles of beer on the wall.\n"
print "536 bottles of beer on the wall, 536 bottles of beer."
print "Take one down and pass it around, 535 bottles of beer on the wall.\n"
print "535 bottles of beer on the wall, 535 bottles of beer."
print "Take one down and pass it around, 534 bottles of beer on the wall.\n"
print "534 bottles of beer on the wall, 534 bottles of beer."
print "Take one down and pass it around, 533 bottles of beer on the wall.\n"
print "533 bottles of beer on the wall, 533 bottles of beer."
print "Take one down and pass it around, 532 bottles of beer on the wall.\n"
print "532 bottles of beer on the wall, 532 bottles of beer."
print "Take one down and pass it around, 531 bottles of beer on the wall.\n"
print "531 bottles of beer on the wall, 531 bottles of beer."
print "Take one down and pass it around, 530 bottles of beer on the wall.\n"
print "530 bottles of beer on the wall, 530 bottles of beer."
print "Take one down and pass it around, 529 bottles of beer on the wall.\n"
print "529 bottles of beer on the wall, 529 bottles of beer."
print "Take one down and pass it around, 528 bottles of beer on the wall.\n"
print "528 bottles of beer on the wall, 528 bottles of beer."
print "Take one down and pass it around, 527 bottles of beer on the wall.\n"
print "527 bottles of beer on the wall, 527 bottles of beer."
print "Take one down and pass it around, 526 bottles of beer on the wall.\n"
print "526 bottles of beer on the wall, 526 bottles of beer."
print "Take one down and pass it around, 525 bottles of beer on the wall.\n"
print "525 bottles of beer on the wall, 525 bottles of beer."
print "Take one down and pass it around, 524 bottles of beer on the wall.\n"
print "524 bottles of beer on the wall, 524 bottles of beer."
print "Take one down and pass it around, 523 bottles of beer on the wall.\n"
print "523 bottles of beer on the wall, 523 bottles of beer."
print "Take one down and pass it around, 522 bottles of beer on the wall.\n"
print "522 bottles of beer on the wall, 522 bottles of beer."
print "Take one down and pass it around, 521 bottles of beer on the wall.\n"
print "521 bottles of beer on the wall, 521 bottles of beer."
print "Take one down and pass it around, 520 bottles of beer on the wall.\n"
print "520 bottles of beer on the wall, 520 bottles of beer."
print "Take one down and pass it around, 519 bottles of beer on the wall.\n"
print "519 bottles of beer on the wall, 519 bottles of beer."
print "Take one down and pass it around, 518 bottles of beer on the wall.\n"
print "518 bottles of beer on the wall, 518 bottles of beer."
print "Take one down and pass it around, 517 bottles of beer on the wall.\n"
print "517 bottles of beer on the wall, 517 bottles of beer."
print "Take one down and pass it around, 516 bottles of beer on the wall.\n"
print "516 bottles of beer on the wall, 516 bottles of beer."
print "Take one down and pass it around, 515 bottles of beer on the wall.\n"
print "515 bottles of beer on the wall, 515 bottles of beer."
print "Take one down and pass it around, 514 bottles of beer on the wall.\n"
print "514 bottles of beer on the wall, 514 bottles of beer."
print "Take one down and pass it around, 513 bottles of beer on the wall.\n"
print "513 bottles of beer on the wall, 513 bottles of beer."
print "Take one down and pass it around, 512 bottles of beer on the wall.\n"
print "512 bottles of beer on the wall, 512 bottles of beer."
print "Take one down and pass it around, 511 bottles of beer on the wall.\n"
print "511 bottles of beer on the wall, 511 bottles of beer."
print "Take one down and pass it around, 510 bottles of beer on the wall.\n"
print "510 bottles of beer on the wall, 510 bottles of beer."
print "Take one down and pass it around, 509 bottles of beer on the wall.\n"
print "509 bottles of beer on the wall, 509 bottles of beer."
print "Take one down and pass it around, 508 bottles of beer on the wall.\n"
print "508 bottles of beer on the wall, 508 bottles of beer."
print "Take one down and pass it around, 507 bottles of beer on the wall.\n"
print "507 bottles of beer on the wall, 507 bottles of beer."
print "Take one down and pass it around, 506 bottles of beer on the wall.\n"
print "506 bottles of beer on the wall, 506 bottles of beer."
print "Take one down and pass it around, 505 bottles of beer on the wall.\n"
print "505 bottles of beer on the wall, 505 bottles of beer."
print "Take one down and pass it around, 504 bottles of beer on the wall.\n"
print "504 bottles of beer on the wall, 504 bottles of beer."
print "Take one down and pass it around, 503 bottles of beer on the wall.\n"
print "503 bottles of beer on the wall, 503 bottles of beer."
print "Take one down and pass it around, 502 bottles of beer on the wall.\n"
print "502 bottles of beer on the wall, 502 bottles of beer."
print "Take one down and pass it around, 501 bottles of beer on the wall.\n"
print "501 bottles of beer on the wall, 501 bottles of beer."
print "Take one down and pass it around, 500 bottles of beer on the wall.\n"
print "500 bottles of beer on the wall, 500 bottles of beer."
print "Take one down and pass it around, 499 bottles of beer on the wall.\n"
print "499 bottles of beer on the wall, 499 bottles of beer."
print "Take one down and pass it around, 498 bottles of beer on the wall.\n"
print "498 bottles of beer on the wall, 498 bottles of beer."
print "Take one down and pass it around, 497 bottles of beer on the wall.\n"
print "497 bottles of beer on the wall, 497 bottles of beer."
print "Take one down and pass it around, 496 bottles of beer on the wall.\n"
print "496 bottles of beer on the wall, 496 bottles of beer."
print "Take one down and pass it around, 495 bottles of beer on the wall.\n"
print "495 bottles of beer on the wall, 495 bottles of beer."
print "Take one down and pass it around, 494 bottles of beer on the wall.\n"
print "494 bottles of beer on the wall, 494 bottles of beer."
print "Take one down and pass it around, 493 bottles of beer on the wall.\n"
print "493 bottles of beer on the wall, 493 bottles of beer."
print "Take one down and pass it around, 492 bottles of beer on the wall.\n"
print "492 bottles of beer on the wall, 492 bottles of beer."
print "Take one down and pass it around, 491 bottles of beer on the wall.\n"
print "491 bottles of beer on the wall, 491 bottles of beer."
print "Take one down and pass it around, 490 bottles of beer on the wall.\n"
print "490 bottles of beer on the wall, 490 bottles of beer."
print "Take one down and pass it around, 489 bottles of beer on the wall.\n"
print "489 bottles of beer on the wall, 489 bottles of beer."
print "Take one down and pass it around, 488 bottles of beer on the wall.\n"
print "488 bottles of beer on the wall, 488 bottles of beer."
print "Take one down and pass it around, 487 bottles of beer on the wall.\n"
print "487 bottles of beer on the wall, 487 bottles of beer."
print "Take one down and pass it around, 486 bottles of beer on the wall.\n"
print "486 bottles of beer on the wall, 486 bottles of beer."
print "Take one down and pass it around, 485 bottles of beer on the wall.\n"
print "485 bottles of beer on the wall, 485 bottles of beer."
print "Take one down and pass it around, 484 bottles of beer on the wall.\n"
print "484 bottles of beer on the wall, 484 bottles of beer."
print "Take one down and pass it around, 483 bottles of beer on the wall.\n"
print "483 bottles of beer on the wall, 483 bottles of beer."
print "Take one down and pass it around, 482 bottles of beer on the wall.\n"
print "482 bottles of beer on the wall, 482 bottles of beer."
print "Take one down and pass it around, 481 bottles of beer on the wall.\n"
print "481 bottles of beer on the wall, 481 bottles of beer."
print "Take one down and pass it around, 480 bottles of beer on the wall.\n"
print "480 bottles of beer on the wall, 480 bottles of beer."
print "Take one down and pass it around, 479 bottles of beer on the wall.\n"
print "479 bottles of beer on the wall, 479 bottles of beer."
print "Take one down and pass it around, 478 bottles of beer on the wall.\n"
print "478 bottles of beer on the wall, 478 bottles of beer."
print "Take one down and pass it around, 477 bottles of beer on the wall.\n"
print "477 bottles of beer on the wall, 477 bottles of beer."
print "Take one down and pass it around, 476 bottles of beer on the wall.\n"
print "476 bottles of beer on the wall, 476 bottles of beer."
print "Take one down and pass it around, 475 bottles of beer on the wall.\n"
print "475 bottles of beer on the wall, 475 bottles of beer."
print "Take one down and pass it around, 474 bottles of beer on the wall.\n"
print "474 bottles of beer on the wall, 474 bottles of beer."
print "Take one down and pass it around, 473 bottles of beer on the wall.\n"
print "473 bottles of beer on the wall, 473 bottles of beer."
print "Take one down and pass it around, 472 bottles of beer on the wall.\n"
print "472 bottles of beer on the wall, 472 bottles of beer."
print "Take one down and pass it around, 471 bottles of beer on the wall.\n"
print "471 bottles of beer on the wall, 471 bottles of beer."
print "Take one down and pass it around, 470 bottles of beer on the wall.\n"
print "470 bottles of beer on the wall, 470 bottles of beer."
print "Take one down and pass it around, 469 bottles of beer on the wall.\n"
print "469 bottles of beer on the wall, 469 bottles of beer."
print "Take one down and pass it around, 468 bottles of beer on the wall.\n"
print "468 bottles of beer on the wall, 468 bottles of beer."
print "Take one down and pass it around, 467 bottles of beer on the wall.\n"
print "467 bottles of beer on the wall, 467 bottles of beer."
print "Take one down and pass it around, 466 bottles of beer on the wall.\n"
print "466 bottles of beer on the wall, 466 bottles of beer."
print "Take one down and pass it around, 465 bottles of beer on the wall.\n"
print "465 bottles of beer on the wall, 465 bottles of beer."
print "Take one down and pass it around, 464 bottles of beer on the wall.\n"
print "464 bottles of beer on the wall, 464 bottles of beer."
print "Take one down and pass it around, 463 bottles of beer on the wall.\n"
print "463 bottles of beer on the wall, 463 bottles of beer."
print "Take one down and pass it around, 462 bottles of beer on the wall.\n"
print "462 bottles of beer on the wall, 462 bottles of beer."
print "Take one down and pass it around, 461 bottles of beer on the wall.\n"
print "461 bottles of beer on the wall, 461 bottles of beer."
print "Take one down and pass it around, 460 bottles of beer on the wall.\n"
print "460 bottles of beer on the wall, 460 bottles of beer."
print "Take one down and pass it around, 459 bottles of beer on the wall.\n"
print "459 bottles of beer on the wall, 459 bottles of beer."
print "Take one down and pass it around, 458 bottles of beer on the wall.\n"
print "458 bottles of beer on the wall, 458 bottles of beer."
print "Take one down and pass it around, 457 bottles of beer on the wall.\n"
print "457 bottles of beer on the wall, 457 bottles of beer."
print "Take one down and pass it around, 456 bottles of beer on the wall.\n"
print "456 bottles of beer on the wall, 456 bottles of beer."
print "Take one down and pass it around, 455 bottles of beer on the wall.\n"
print "455 bottles of beer on the wall, 455 bottles of beer."
print "Take one down and pass it around, 454 bottles of beer on the wall.\n"
print "454 bottles of beer on the wall, 454 bottles of beer."
print "Take one down and pass it around, 453 bottles of beer on the wall.\n"
print "453 bottles of beer on the wall, 453 bottles of beer."
print "Take one down and pass it around, 452 bottles of beer on the wall.\n"
print "452 bottles of beer on the wall, 452 bottles of beer."
print "Take one down and pass it around, 451 bottles of beer on the wall.\n"
print "451 bottles of beer on the wall, 451 bottles of beer."
print "Take one down and pass it around, 450 bottles of beer on the wall.\n"
print "450 bottles of beer on the wall, 450 bottles of beer."
print "Take one down and pass it around, 449 bottles of beer on the wall.\n"
print "449 bottles of beer on the wall, 449 bottles of beer."
print "Take one down and pass it around, 448 bottles of beer on the wall.\n"
print "448 bottles of beer on the wall, 448 bottles of beer."
print "Take one down and pass it around, 447 bottles of beer on the wall.\n"
print "447 bottles of beer on the wall, 447 bottles of beer."
print "Take one down and pass it around, 446 bottles of beer on the wall.\n"
print "446 bottles of beer on the wall, 446 bottles of beer."
print "Take one down and pass it around, 445 bottles of beer on the wall.\n"
print "445 bottles of beer on the wall, 445 bottles of beer."
print "Take one down and pass it around, 444 bottles of beer on the wall.\n"
print "444 bottles of beer on the wall, 444 bottles of beer."
print "Take one down and pass it around, 443 bottles of beer on the wall.\n"
print "443 bottles of beer on the wall, 443 bottles of beer."
print "Take one down and pass it around, 442 bottles of beer on the wall.\n"
print "442 bottles of beer on the wall, 442 bottles of beer."
print "Take one down and pass it around, 441 bottles of beer on the wall.\n"
print "441 bottles of beer on the wall, 441 bottles of beer."
print "Take one down and pass it around, 440 bottles of beer on the wall.\n"
print "440 bottles of beer on the wall, 440 bottles of beer."
print "Take one down and pass it around, 439 bottles of beer on the wall.\n"
print "439 bottles of beer on the wall, 439 bottles of beer."
print "Take one down and pass it around, 438 bottles of beer on the wall.\n"
print "438 bottles of beer on the wall, 438 bottles of beer."
print "Take one down and pass it around, 437 bottles of beer on the wall.\n"
print "437 bottles of beer on the wall, 437 bottles of beer."
print "Take one down and pass it around, 436 bottles of beer on the wall.\n"
print "436 bottles of beer on the wall, 436 bottles of beer."
print "Take one down and pass it around, 435 bottles of beer on the wall.\n"
print "435 bottles of beer on the wall, 435 bottles of beer."
print "Take one down and pass it around, 434 bottles of beer on the wall.\n"
print "434 bottles of beer on the wall, 434 bottles of beer."
print "Take one down and pass it around, 433 bottles of beer on the wall.\n"
print "433 bottles of beer on the wall, 433 bottles of beer."
print "Take one down and pass it around, 432 bottles of beer on the wall.\n"
print "432 bottles of beer on the wall, 432 bottles of beer."
print "Take one down and pass it around, 431 bottles of beer on the wall.\n"
print "431 bottles of beer on the wall, 431 bottles of beer."
print "Take one down and pass it around, 430 bottles of beer on the wall.\n"
print "430 bottles of beer on the wall, 430 bottles of beer."
print "Take one down and pass it around, 429 bottles of beer on the wall.\n"
print "429 bottles of beer on the wall, 429 bottles of beer."
print "Take one down and pass it around, 428 bottles of beer on the wall.\n"
print "428 bottles of beer on the wall, 428 bottles of beer."
print "Take one down and pass it around, 427 bottles of beer on the wall.\n"
print "427 bottles of beer on the wall, 427 bottles of beer."
print "Take one down and pass it around, 426 bottles of beer on the wall.\n"
print "426 bottles of beer on the wall, 426 bottles of beer."
print "Take one down and pass it around, 425 bottles of beer on the wall.\n"
print "425 bottles of beer on the wall, 425 bottles of beer."
print "Take one down and pass it around, 424 bottles of beer on the wall.\n"
print "424 bottles of beer on the wall, 424 bottles of beer."
print "Take one down and pass it around, 423 bottles of beer on the wall.\n"
print "423 bottles of beer on the wall, 423 bottles of beer."
print "Take one down and pass it around, 422 bottles of beer on the wall.\n"
print "422 bottles of beer on the wall, 422 bottles of beer."
print "Take one down and pass it around, 421 bottles of beer on the wall.\n"
print "421 bottles of beer on the wall, 421 bottles of beer."
print "Take one down and pass it around, 420 bottles of beer on the wall.\n"
print "420 bottles of beer on the wall, 420 bottles of beer."
print "Take one down and pass it around, 419 bottles of beer on the wall.\n"
print "419 bottles of beer on the wall, 419 bottles of beer."
print "Take one down and pass it around, 418 bottles of beer on the wall.\n"
print "418 bottles of beer on the wall, 418 bottles of beer."
print "Take one down and pass it around, 417 bottles of beer on the wall.\n"
print "417 bottles of beer on the wall, 417 bottles of beer."
print "Take one down and pass it around, 416 bottles of beer on the wall.\n"
print "416 bottles of beer on the wall, 416 bottles of beer."
print "Take one down and pass it around, 415 bottles of beer on the wall.\n"
print "415 bottles of beer on the wall, 415 bottles of beer."
print "Take one down and pass it around, 414 bottles of beer on the wall.\n"
print "414 bottles of beer on the wall, 414 bottles of beer."
print "Take one down and pass it around, 413 bottles of beer on the wall.\n"
print "413 bottles of beer on the wall, 413 bottles of beer."
print "Take one down and pass it around, 412 bottles of beer on the wall.\n"
print "412 bottles of beer on the wall, 412 bottles of beer."
print "Take one down and pass it around, 411 bottles of beer on the wall.\n"
print "411 bottles of beer on the wall, 411 bottles of beer."
print "Take one down and pass it around, 410 bottles of beer on the wall.\n"
print "410 bottles of beer on the wall, 410 bottles of beer."
print "Take one down and pass it around, 409 bottles of beer on the wall.\n"
print "409 bottles of beer on the wall, 409 bottles of beer."
print "Take one down and pass it around, 408 bottles of beer on the wall.\n"
print "408 bottles of beer on the wall, 408 bottles of beer."
print "Take one down and pass it around, 407 bottles of beer on the wall.\n"
print "407 bottles of beer on the wall, 407 bottles of beer."
print "Take one down and pass it around, 406 bottles of beer on the wall.\n"
print "406 bottles of beer on the wall, 406 bottles of beer."
print "Take one down and pass it around, 405 bottles of beer on the wall.\n"
print "405 bottles of beer on the wall, 405 bottles of beer."
print "Take one down and pass it around, 404 bottles of beer on the wall.\n"
print "404 bottles of beer on the wall, 404 bottles of beer."
print "Take one down and pass it around, 403 bottles of beer on the wall.\n"
print "403 bottles of beer on the wall, 403 bottles of beer."
print "Take one down and pass it around, 402 bottles of beer on the wall.\n"
print "402 bottles of beer on the wall, 402 bottles of beer."
print "Take one down and pass it around, 401 bottles of beer on the wall.\n"
print "401 bottles of beer on the wall, 401 bottles of beer."
print "Take one down and pass it around, 400 bottles of beer on the wall.\n"
print "400 bottles of beer on the wall, 400 bottles of beer."
print "Take one down and pass it around, 399 bottles of beer on the wall.\n"
print "399 bottles of beer on the wall, 399 bottles of beer."
print "Take one down and pass it around, 398 bottles of beer on the wall.\n"
print "398 bottles of beer on the wall, 398 bottles of beer."
print "Take one down and pass it around, 397 bottles of beer on the wall.\n"
print "397 bottles of beer on the wall, 397 bottles of beer."
print "Take one down and pass it around, 396 bottles of beer on the wall.\n"
print "396 bottles of beer on the wall, 396 bottles of beer."
print "Take one down and pass it around, 395 bottles of beer on the wall.\n"
print "395 bottles of beer on the wall, 395 bottles of beer."
print "Take one down and pass it around, 394 bottles of beer on the wall.\n"
print "394 bottles of beer on the wall, 394 bottles of beer."
print "Take one down and pass it around, 393 bottles of beer on the wall.\n"
print "393 bottles of beer on the wall, 393 bottles of beer."
print "Take one down and pass it around, 392 bottles of beer on the wall.\n"
print "392 bottles of beer on the wall, 392 bottles of beer."
print "Take one down and pass it around, 391 bottles of beer on the wall.\n"
print "391 bottles of beer on the wall, 391 bottles of beer."
print "Take one down and pass it around, 390 bottles of beer on the wall.\n"
print "390 bottles of beer on the wall, 390 bottles of beer."
print "Take one down and pass it around, 389 bottles of beer on the wall.\n"
print "389 bottles of beer on the wall, 389 bottles of beer."
print "Take one down and pass it around, 388 bottles of beer on the wall.\n"
print "388 bottles of beer on the wall, 388 bottles of beer."
print "Take one down and pass it around, 387 bottles of beer on the wall.\n"
print "387 bottles of beer on the wall, 387 bottles of beer."
print "Take one down and pass it around, 386 bottles of beer on the wall.\n"
print "386 bottles of beer on the wall, 386 bottles of beer."
print "Take one down and pass it around, 385 bottles of beer on the wall.\n"
print "385 bottles of beer on the wall, 385 bottles of beer."
print "Take one down and pass it around, 384 bottles of beer on the wall.\n"
print "384 bottles of beer on the wall, 384 bottles of beer."
print "Take one down and pass it around, 383 bottles of beer on the wall.\n"
print "383 bottles of beer on the wall, 383 bottles of beer."
print "Take one down and pass it around, 382 bottles of beer on the wall.\n"
print "382 bottles of beer on the wall, 382 bottles of beer."
print "Take one down and pass it around, 381 bottles of beer on the wall.\n"
print "381 bottles of beer on the wall, 381 bottles of beer."
print "Take one down and pass it around, 380 bottles of beer on the wall.\n"
print "380 bottles of beer on the wall, 380 bottles of beer."
print "Take one down and pass it around, 379 bottles of beer on the wall.\n"
print "379 bottles of beer on the wall, 379 bottles of beer."
print "Take one down and pass it around, 378 bottles of beer on the wall.\n"
print "378 bottles of beer on the wall, 378 bottles of beer."
print "Take one down and pass it around, 377 bottles of beer on the wall.\n"
print "377 bottles of beer on the wall, 377 bottles of beer."
print "Take one down and pass it around, 376 bottles of beer on the wall.\n"
print "376 bottles of beer on the wall, 376 bottles of beer."
print "Take one down and pass it around, 375 bottles of beer on the wall.\n"
print "375 bottles of beer on the wall, 375 bottles of beer."
print "Take one down and pass it around, 374 bottles of beer on the wall.\n"
print "374 bottles of beer on the wall, 374 bottles of beer."
print "Take one down and pass it around, 373 bottles of beer on the wall.\n"
print "373 bottles of beer on the wall, 373 bottles of beer."
print "Take one down and pass it around, 372 bottles of beer on the wall.\n"
print "372 bottles of beer on the wall, 372 bottles of beer."
print "Take one down and pass it around, 371 bottles of beer on the wall.\n"
print "371 bottles of beer on the wall, 371 bottles of beer."
print "Take one down and pass it around, 370 bottles of beer on the wall.\n"
print "370 bottles of beer on the wall, 370 bottles of beer."
print "Take one down and pass it around, 369 bottles of beer on the wall.\n"
print "369 bottles of beer on the wall, 369 bottles of beer."
print "Take one down and pass it around, 368 bottles of beer on the wall.\n"
print "368 bottles of beer on the wall, 368 bottles of beer."
print "Take one down and pass it around, 367 bottles of beer on the wall.\n"
print "367 bottles of beer on the wall, 367 bottles of beer."
print "Take one down and pass it around, 366 bottles of beer on the wall.\n"
print "366 bottles of beer on the wall, 366 bottles of beer."
print "Take one down and pass it around, 365 bottles of beer on the wall.\n"
print "365 bottles of beer on the wall, 365 bottles of beer."
print "Take one down and pass it around, 364 bottles of beer on the wall.\n"
print "364 bottles of beer on the wall, 364 bottles of beer."
print "Take one down and pass it around, 363 bottles of beer on the wall.\n"
print "363 bottles of beer on the wall, 363 bottles of beer."
print "Take one down and pass it around, 362 bottles of beer on the wall.\n"
print "362 bottles of beer on the wall, 362 bottles of beer."
print "Take one down and pass it around, 361 bottles of beer on the wall.\n"
print "361 bottles of beer on the wall, 361 bottles of beer."
print "Take one down and pass it around, 360 bottles of beer on the wall.\n"
print "360 bottles of beer on the wall, 360 bottles of beer."
print "Take one down and pass it around, 359 bottles of beer on the wall.\n"
print "359 bottles of beer on the wall, 359 bottles of beer."
print "Take one down and pass it around, 358 bottles of beer on the wall.\n"
print "358 bottles of beer on the wall, 358 bottles of beer."
print "Take one down and pass it around, 357 bottles of beer on the wall.\n"
print "357 bottles of beer on the wall, 357 bottles of beer."
print "Take one down and pass it around, 356 bottles of beer on the wall.\n"
print "356 bottles of beer on the wall, 356 bottles of beer."
print "Take one down and pass it around, 355 bottles of beer on the wall.\n"
print "355 bottles of beer on the wall, 355 bottles of beer."
print "Take one down and pass it around, 354 bottles of beer on the wall.\n"
print "354 bottles of beer on the wall, 354 bottles of beer."
print "Take one down and pass it around, 353 bottles of beer on the wall.\n"
print "353 bottles of beer on the wall, 353 bottles of beer."
print "Take one down and pass it around, 352 bottles of beer on the wall.\n"
print "352 bottles of beer on the wall, 352 bottles of beer."
print "Take one down and pass it around, 351 bottles of beer on the wall.\n"
print "351 bottles of beer on the wall, 351 bottles of beer."
print "Take one down and pass it around, 350 bottles of beer on the wall.\n"
print "350 bottles of beer on the wall, 350 bottles of beer."
print "Take one down and pass it around, 349 bottles of beer on the wall.\n"
print "349 bottles of beer on the wall, 349 bottles of beer."
print "Take one down and pass it around, 348 bottles of beer on the wall.\n"
print "348 bottles of beer on the wall, 348 bottles of beer."
print "Take one down and pass it around, 347 bottles of beer on the wall.\n"
print "347 bottles of beer on the wall, 347 bottles of beer."
print "Take one down and pass it around, 346 bottles of beer on the wall.\n"
print "346 bottles of beer on the wall, 346 bottles of beer."
print "Take one down and pass it around, 345 bottles of beer on the wall.\n"
print "345 bottles of beer on the wall, 345 bottles of beer."
print "Take one down and pass it around, 344 bottles of beer on the wall.\n"
print "344 bottles of beer on the wall, 344 bottles of beer."
print "Take one down and pass it around, 343 bottles of beer on the wall.\n"
print "343 bottles of beer on the wall, 343 bottles of beer."
print "Take one down and pass it around, 342 bottles of beer on the wall.\n"
print "342 bottles of beer on the wall, 342 bottles of beer."
print "Take one down and pass it around, 341 bottles of beer on the wall.\n"
print "341 bottles of beer on the wall, 341 bottles of beer."
print "Take one down and pass it around, 340 bottles of beer on the wall.\n"
print "340 bottles of beer on the wall, 340 bottles of beer."
print "Take one down and pass it around, 339 bottles of beer on the wall.\n"
print "339 bottles of beer on the wall, 339 bottles of beer."
print "Take one down and pass it around, 338 bottles of beer on the wall.\n"
print "338 bottles of beer on the wall, 338 bottles of beer."
print "Take one down and pass it around, 337 bottles of beer on the wall.\n"
print "337 bottles of beer on the wall, 337 bottles of beer."
print "Take one down and pass it around, 336 bottles of beer on the wall.\n"
print "336 bottles of beer on the wall, 336 bottles of beer."
print "Take one down and pass it around, 335 bottles of beer on the wall.\n"
print "335 bottles of beer on the wall, 335 bottles of beer."
print "Take one down and pass it around, 334 bottles of beer on the wall.\n"
print "334 bottles of beer on the wall, 334 bottles of beer."
print "Take one down and pass it around, 333 bottles of beer on the wall.\n"
print "333 bottles of beer on the wall, 333 bottles of beer."
print "Take one down and pass it around, 332 bottles of beer on the wall.\n"
print "332 bottles of beer on the wall, 332 bottles of beer."
print "Take one down and pass it around, 331 bottles of beer on the wall.\n"
print "331 bottles of beer on the wall, 331 bottles of beer."
print "Take one down and pass it around, 330 bottles of beer on the wall.\n"
print "330 bottles of beer on the wall, 330 bottles of beer."
print "Take one down and pass it around, 329 bottles of beer on the wall.\n"
print "329 bottles of beer on the wall, 329 bottles of beer."
print "Take one down and pass it around, 328 bottles of beer on the wall.\n"
print "328 bottles of beer on the wall, 328 bottles of beer."
print "Take one down and pass it around, 327 bottles of beer on the wall.\n"
print "327 bottles of beer on the wall, 327 bottles of beer."
print "Take one down and pass it around, 326 bottles of beer on the wall.\n"
print "326 bottles of beer on the wall, 326 bottles of beer."
print "Take one down and pass it around, 325 bottles of beer on the wall.\n"
print "325 bottles of beer on the wall, 325 bottles of beer."
print "Take one down and pass it around, 324 bottles of beer on the wall.\n"
print "324 bottles of beer on the wall, 324 bottles of beer."
print "Take one down and pass it around, 323 bottles of beer on the wall.\n"
print "323 bottles of beer on the wall, 323 bottles of beer."
print "Take one down and pass it around, 322 bottles of beer on the wall.\n"
print "322 bottles of beer on the wall, 322 bottles of beer."
print "Take one down and pass it around, 321 bottles of beer on the wall.\n"
print "321 bottles of beer on the wall, 321 bottles of beer."
print "Take one down and pass it around, 320 bottles of beer on the wall.\n"
print "320 bottles of beer on the wall, 320 bottles of beer."
print "Take one down and pass it around, 319 bottles of beer on the wall.\n"
print "319 bottles of beer on the wall, 319 bottles of beer."
print "Take one down and pass it around, 318 bottles of beer on the wall.\n"
print "318 bottles of beer on the wall, 318 bottles of beer."
print "Take one down and pass it around, 317 bottles of beer on the wall.\n"
print "317 bottles of beer on the wall, 317 bottles of beer."
print "Take one down and pass it around, 316 bottles of beer on the wall.\n"
print "316 bottles of beer on the wall, 316 bottles of beer."
print "Take one down and pass it around, 315 bottles of beer on the wall.\n"
print "315 bottles of beer on the wall, 315 bottles of beer."
print "Take one down and pass it around, 314 bottles of beer on the wall.\n"
print "314 bottles of beer on the wall, 314 bottles of beer."
print "Take one down and pass it around, 313 bottles of beer on the wall.\n"
print "313 bottles of beer on the wall, 313 bottles of beer."
print "Take one down and pass it around, 312 bottles of beer on the wall.\n"
print "312 bottles of beer on the wall, 312 bottles of beer."
print "Take one down and pass it around, 311 bottles of beer on the wall.\n"
print "311 bottles of beer on the wall, 311 bottles of beer."
print "Take one down and pass it around, 310 bottles of beer on the wall.\n"
print "310 bottles of beer on the wall, 310 bottles of beer."
print "Take one down and pass it around, 309 bottles of beer on the wall.\n"
print "309 bottles of beer on the wall, 309 bottles of beer."
print "Take one down and pass it around, 308 bottles of beer on the wall.\n"
print "308 bottles of beer on the wall, 308 bottles of beer."
print "Take one down and pass it around, 307 bottles of beer on the wall.\n"
print "307 bottles of beer on the wall, 307 bottles of beer."
print "Take one down and pass it around, 306 bottles of beer on the wall.\n"
print "306 bottles of beer on the wall, 306 bottles of beer."
print "Take one down and pass it around, 305 bottles of beer on the wall.\n"
print "305 bottles of beer on the wall, 305 bottles of beer."
print "Take one down and pass it around, 304 bottles of beer on the wall.\n"
print "304 bottles of beer on the wall, 304 bottles of beer."
print "Take one down and pass it around, 303 bottles of beer on the wall.\n"
print "303 bottles of beer on the wall, 303 bottles of beer."
print "Take one down and pass it around, 302 bottles of beer on the wall.\n"
print "302 bottles of beer on the wall, 302 bottles of beer."
print "Take one down and pass it around, 301 bottles of beer on the wall.\n"
print "301 bottles of beer on the wall, 301 bottles of beer."
print "Take one down and pass it around, 300 bottles of beer on the wall.\n"
print "300 bottles of beer on the wall, 300 bottles of beer."
print "Take one down and pass it around, 299 bottles of beer on the wall.\n"
print "299 bottles of beer on the wall, 299 bottles of beer."
print "Take one down and pass it around, 298 bottles of beer on the wall.\n"
print "298 bottles of beer on the wall, 298 bottles of beer."
print "Take one down and pass it around, 297 bottles of beer on the wall.\n"
print "297 bottles of beer on the wall, 297 bottles of beer."
print "Take one down and pass it around, 296 bottles of beer on the wall.\n"
print "296 bottles of beer on the wall, 296 bottles of beer."
print "Take one down and pass it around, 295 bottles of beer on the wall.\n"
print "295 bottles of beer on the wall, 295 bottles of beer."
print "Take one down and pass it around, 294 bottles of beer on the wall.\n"
print "294 bottles of beer on the wall, 294 bottles of beer."
print "Take one down and pass it around, 293 bottles of beer on the wall.\n"
print "293 bottles of beer on the wall, 293 bottles of beer."
print "Take one down and pass it around, 292 bottles of beer on the wall.\n"
print "292 bottles of beer on the wall, 292 bottles of beer."
print "Take one down and pass it around, 291 bottles of beer on the wall.\n"
print "291 bottles of beer on the wall, 291 bottles of beer."
print "Take one down and pass it around, 290 bottles of beer on the wall.\n"
print "290 bottles of beer on the wall, 290 bottles of beer."
print "Take one down and pass it around, 289 bottles of beer on the wall.\n"
print "289 bottles of beer on the wall, 289 bottles of beer."
print "Take one down and pass it around, 288 bottles of beer on the wall.\n"
print "288 bottles of beer on the wall, 288 bottles of beer."
print "Take one down and pass it around, 287 bottles of beer on the wall.\n"
print "287 bottles of beer on the wall, 287 bottles of beer."
print "Take one down and pass it around, 286 bottles of beer on the wall.\n"
print "286 bottles of beer on the wall, 286 bottles of beer."
print "Take one down and pass it around, 285 bottles of beer on the wall.\n"
print "285 bottles of beer on the wall, 285 bottles of beer."
print "Take one down and pass it around, 284 bottles of beer on the wall.\n"
print "284 bottles of beer on the wall, 284 bottles of beer."
print "Take one down and pass it around, 283 bottles of beer on the wall.\n"
print "283 bottles of beer on the wall, 283 bottles of beer."
print "Take one down and pass it around, 282 bottles of beer on the wall.\n"
print "282 bottles of beer on the wall, 282 bottles of beer."
print "Take one down and pass it around, 281 bottles of beer on the wall.\n"
print "281 bottles of beer on the wall, 281 bottles of beer."
print "Take one down and pass it around, 280 bottles of beer on the wall.\n"
print "280 bottles of beer on the wall, 280 bottles of beer."
print "Take one down and pass it around, 279 bottles of beer on the wall.\n"
print "279 bottles of beer on the wall, 279 bottles of beer."
print "Take one down and pass it around, 278 bottles of beer on the wall.\n"
print "278 bottles of beer on the wall, 278 bottles of beer."
print "Take one down and pass it around, 277 bottles of beer on the wall.\n"
print "277 bottles of beer on the wall, 277 bottles of beer."
print "Take one down and pass it around, 276 bottles of beer on the wall.\n"
print "276 bottles of beer on the wall, 276 bottles of beer."
print "Take one down and pass it around, 275 bottles of beer on the wall.\n"
print "275 bottles of beer on the wall, 275 bottles of beer."
print "Take one down and pass it around, 274 bottles of beer on the wall.\n"
print "274 bottles of beer on the wall, 274 bottles of beer."
print "Take one down and pass it around, 273 bottles of beer on the wall.\n"
print "273 bottles of beer on the wall, 273 bottles of beer."
print "Take one down and pass it around, 272 bottles of beer on the wall.\n"
print "272 bottles of beer on the wall, 272 bottles of beer."
print "Take one down and pass it around, 271 bottles of beer on the wall.\n"
print "271 bottles of beer on the wall, 271 bottles of beer."
print "Take one down and pass it around, 270 bottles of beer on the wall.\n"
print "270 bottles of beer on the wall, 270 bottles of beer."
print "Take one down and pass it around, 269 bottles of beer on the wall.\n"
print "269 bottles of beer on the wall, 269 bottles of beer."
print "Take one down and pass it around, 268 bottles of beer on the wall.\n"
print "268 bottles of beer on the wall, 268 bottles of beer."
print "Take one down and pass it around, 267 bottles of beer on the wall.\n"
print "267 bottles of beer on the wall, 267 bottles of beer."
print "Take one down and pass it around, 266 bottles of beer on the wall.\n"
print "266 bottles of beer on the wall, 266 bottles of beer."
print "Take one down and pass it around, 265 bottles of beer on the wall.\n"
print "265 bottles of beer on the wall, 265 bottles of beer."
print "Take one down and pass it around, 264 bottles of beer on the wall.\n"
print "264 bottles of beer on the wall, 264 bottles of beer."
print "Take one down and pass it around, 263 bottles of beer on the wall.\n"
print "263 bottles of beer on the wall, 263 bottles of beer."
print "Take one down and pass it around, 262 bottles of beer on the wall.\n"
print "262 bottles of beer on the wall, 262 bottles of beer."
print "Take one down and pass it around, 261 bottles of beer on the wall.\n"
print "261 bottles of beer on the wall, 261 bottles of beer."
print "Take one down and pass it around, 260 bottles of beer on the wall.\n"
print "260 bottles of beer on the wall, 260 bottles of beer."
print "Take one down and pass it around, 259 bottles of beer on the wall.\n"
print "259 bottles of beer on the wall, 259 bottles of beer."
print "Take one down and pass it around, 258 bottles of beer on the wall.\n"
print "258 bottles of beer on the wall, 258 bottles of beer."
print "Take one down and pass it around, 257 bottles of beer on the wall.\n"
print "257 bottles of beer on the wall, 257 bottles of beer."
print "Take one down and pass it around, 256 bottles of beer on the wall.\n"
print "256 bottles of beer on the wall, 256 bottles of beer."
print "Take one down and pass it around, 255 bottles of beer on the wall.\n"
print "255 bottles of beer on the wall, 255 bottles of beer."
print "Take one down and pass it around, 254 bottles of beer on the wall.\n"
print "254 bottles of beer on the wall, 254 bottles of beer."
print "Take one down and pass it around, 253 bottles of beer on the wall.\n"
print "253 bottles of beer on the wall, 253 bottles of beer."
print "Take one down and pass it around, 252 bottles of beer on the wall.\n"
print "252 bottles of beer on the wall, 252 bottles of beer."
print "Take one down and pass it around, 251 bottles of beer on the wall.\n"
print "251 bottles of beer on the wall, 251 bottles of beer."
print "Take one down and pass it around, 250 bottles of beer on the wall.\n"
print "250 bottles of beer on the wall, 250 bottles of beer."
print "Take one down and pass it around, 249 bottles of beer on the wall.\n"
print "249 bottles of beer on the wall, 249 bottles of beer."
print "Take one down and pass it around, 248 bottles of beer on the wall.\n"
print "248 bottles of beer on the wall, 248 bottles of beer."
print "Take one down and pass it around, 247 bottles of beer on the wall.\n"
print "247 bottles of beer on the wall, 247 bottles of beer."
print "Take one down and pass it around, 246 bottles of beer on the wall.\n"
print "246 bottles of beer on the wall, 246 bottles of beer."
print "Take one down and pass it around, 245 bottles of beer on the wall.\n"
print "245 bottles of beer on the wall, 245 bottles of beer."
print "Take one down and pass it around, 244 bottles of beer on the wall.\n"
print "244 bottles of beer on the wall, 244 bottles of beer."
print "Take one down and pass it around, 243 bottles of beer on the wall.\n"
print "243 bottles of beer on the wall, 243 bottles of beer."
print "Take one down and pass it around, 242 bottles of beer on the wall.\n"
print "242 bottles of beer on the wall, 242 bottles of beer."
print "Take one down and pass it around, 241 bottles of beer on the wall.\n"
print "241 bottles of beer on the wall, 241 bottles of beer."
print "Take one down and pass it around, 240 bottles of beer on the wall.\n"
print "240 bottles of beer on the wall, 240 bottles of beer."
print "Take one down and pass it around, 239 bottles of beer on the wall.\n"
print "239 bottles of beer on the wall, 239 bottles of beer."
print "Take one down and pass it around, 238 bottles of beer on the wall.\n"
print "238 bottles of beer on the wall, 238 bottles of beer."
print "Take one down and pass it around, 237 bottles of beer on the wall.\n"
print "237 bottles of beer on the wall, 237 bottles of beer."
print "Take one down and pass it around, 236 bottles of beer on the wall.\n"
print "236 bottles of beer on the wall, 236 bottles of beer."
print "Take one down and pass it around, 235 bottles of beer on the wall.\n"
print "235 bottles of beer on the wall, 235 bottles of beer."
print "Take one down and pass it around, 234 bottles of beer on the wall.\n"
print "234 bottles of beer on the wall, 234 bottles of beer."
print "Take one down and pass it around, 233 bottles of beer on the wall.\n"
print "233 bottles of beer on the wall, 233 bottles of beer."
print "Take one down and pass it around, 232 bottles of beer on the wall.\n"
print "232 bottles of beer on the wall, 232 bottles of beer."
print "Take one down and pass it around, 231 bottles of beer on the wall.\n"
print "231 bottles of beer on the wall, 231 bottles of beer."
print "Take one down and pass it around, 230 bottles of beer on the wall.\n"
print "230 bottles of beer on the wall, 230 bottles of beer."
print "Take one down and pass it around, 229 bottles of beer on the wall.\n"
print "229 bottles of beer on the wall, 229 bottles of beer."
print "Take one down and pass it around, 228 bottles of beer on the wall.\n"
print "228 bottles of beer on the wall, 228 bottles of beer."
print "Take one down and pass it around, 227 bottles of beer on the wall.\n"
print "227 bottles of beer on the wall, 227 bottles of beer."
print "Take one down and pass it around, 226 bottles of beer on the wall.\n"
print "226 bottles of beer on the wall, 226 bottles of beer."
print "Take one down and pass it around, 225 bottles of beer on the wall.\n"
print "225 bottles of beer on the wall, 225 bottles of beer."
print "Take one down and pass it around, 224 bottles of beer on the wall.\n"
print "224 bottles of beer on the wall, 224 bottles of beer."
print "Take one down and pass it around, 223 bottles of beer on the wall.\n"
print "223 bottles of beer on the wall, 223 bottles of beer."
print "Take one down and pass it around, 222 bottles of beer on the wall.\n"
print "222 bottles of beer on the wall, 222 bottles of beer."
print "Take one down and pass it around, 221 bottles of beer on the wall.\n"
print "221 bottles of beer on the wall, 221 bottles of beer."
print "Take one down and pass it around, 220 bottles of beer on the wall.\n"
print "220 bottles of beer on the wall, 220 bottles of beer."
print "Take one down and pass it around, 219 bottles of beer on the wall.\n"
print "219 bottles of beer on the wall, 219 bottles of beer."
print "Take one down and pass it around, 218 bottles of beer on the wall.\n"
print "218 bottles of beer on the wall, 218 bottles of beer."
print "Take one down and pass it around, 217 bottles of beer on the wall.\n"
print "217 bottles of beer on the wall, 217 bottles of beer."
print "Take one down and pass it around, 216 bottles of beer on the wall.\n"
print "216 bottles of beer on the wall, 216 bottles of beer."
print "Take one down and pass it around, 215 bottles of beer on the wall.\n"
print "215 bottles of beer on the wall, 215 bottles of beer."
print "Take one down and pass it around, 214 bottles of beer on the wall.\n"
print "214 bottles of beer on the wall, 214 bottles of beer."
print "Take one down and pass it around, 213 bottles of beer on the wall.\n"
print "213 bottles of beer on the wall, 213 bottles of beer."
print "Take one down and pass it around, 212 bottles of beer on the wall.\n"
print "212 bottles of beer on the wall, 212 bottles of beer."
print "Take one down and pass it around, 211 bottles of beer on the wall.\n"
print "211 bottles of beer on the wall, 211 bottles of beer."
print "Take one down and pass it around, 210 bottles of beer on the wall.\n"
print "210 bottles of beer on the wall, 210 bottles of beer."
print "Take one down and pass it around, 209 bottles of beer on the wall.\n"
print "209 bottles of beer on the wall, 209 bottles of beer."
print "Take one down and pass it around, 208 bottles of beer on the wall.\n"
print "208 bottles of beer on the wall, 208 bottles of beer."
print "Take one down and pass it around, 207 bottles of beer on the wall.\n"
print "207 bottles of beer on the wall, 207 bottles of beer."
print "Take one down and pass it around, 206 bottles of beer on the wall.\n"
print "206 bottles of beer on the wall, 206 bottles of beer."
print "Take one down and pass it around, 205 bottles of beer on the wall.\n"
print "205 bottles of beer on the wall, 205 bottles of beer."
print "Take one down and pass it around, 204 bottles of beer on the wall.\n"
print "204 bottles of beer on the wall, 204 bottles of beer."
print "Take one down and pass it around, 203 bottles of beer on the wall.\n"
print "203 bottles of beer on the wall, 203 bottles of beer."
print "Take one down and pass it around, 202 bottles of beer on the wall.\n"
print "202 bottles of beer on the wall, 202 bottles of beer."
print "Take one down and pass it around, 201 bottles of beer on the wall.\n"
print "201 bottles of beer on the wall, 201 bottles of beer."
print "Take one down and pass it around, 200 bottles of beer on the wall.\n"
print "200 bottles of beer on the wall, 200 bottles of beer."
print "Take one down and pass it around, 199 bottles of beer on the wall.\n"
print "199 bottles of beer on the wall, 199 bottles of beer."
print "Take one down and pass it around, 198 bottles of beer on the wall.\n"
print "198 bottles of beer on the wall, 198 bottles of beer."
print "Take one down and pass it around, 197 bottles of beer on the wall.\n"
print "197 bottles of beer on the wall, 197 bottles of beer."
print "Take one down and pass it around, 196 bottles of beer on the wall.\n"
print "196 bottles of beer on the wall, 196 bottles of beer."
print "Take one down and pass it around, 195 bottles of beer on the wall.\n"
print "195 bottles of beer on the wall, 195 bottles of beer."
print "Take one down and pass it around, 194 bottles of beer on the wall.\n"
print "194 bottles of beer on the wall, 194 bottles of beer."
print "Take one down and pass it around, 193 bottles of beer on the wall.\n"
print "193 bottles of beer on the wall, 193 bottles of beer."
print "Take one down and pass it around, 192 bottles of beer on the wall.\n"
print "192 bottles of beer on the wall, 192 bottles of beer."
print "Take one down and pass it around, 191 bottles of beer on the wall.\n"
print "191 bottles of beer on the wall, 191 bottles of beer."
print "Take one down and pass it around, 190 bottles of beer on the wall.\n"
print "190 bottles of beer on the wall, 190 bottles of beer."
print "Take one down and pass it around, 189 bottles of beer on the wall.\n"
print "189 bottles of beer on the wall, 189 bottles of beer."
print "Take one down and pass it around, 188 bottles of beer on the wall.\n"
print "188 bottles of beer on the wall, 188 bottles of beer."
print "Take one down and pass it around, 187 bottles of beer on the wall.\n"
print "187 bottles of beer on the wall, 187 bottles of beer."
print "Take one down and pass it around, 186 bottles of beer on the wall.\n"
print "186 bottles of beer on the wall, 186 bottles of beer."
print "Take one down and pass it around, 185 bottles of beer on the wall.\n"
print "185 bottles of beer on the wall, 185 bottles of beer."
print "Take one down and pass it around, 184 bottles of beer on the wall.\n"
print "184 bottles of beer on the wall, 184 bottles of beer."
print "Take one down and pass it around, 183 bottles of beer on the wall.\n"
print "183 bottles of beer on the wall, 183 bottles of beer."
print "Take one down and pass it around, 182 bottles of beer on the wall.\n"
print "182 bottles of beer on the wall, 182 bottles of beer."
print "Take one down and pass it around, 181 bottles of beer on the wall.\n"
print "181 bottles of beer on the wall, 181 bottles of beer."
print "Take one down and pass it around, 180 bottles of beer on the wall.\n"
print "180 bottles of beer on the wall, 180 bottles of beer."
print "Take one down and pass it around, 179 bottles of beer on the wall.\n"
print "179 bottles of beer on the wall, 179 bottles of beer."
print "Take one down and pass it around, 178 bottles of beer on the wall.\n"
print "178 bottles of beer on the wall, 178 bottles of beer."
print "Take one down and pass it around, 177 bottles of beer on the wall.\n"
print "177 bottles of beer on the wall, 177 bottles of beer."
print "Take one down and pass it around, 176 bottles of beer on the wall.\n"
print "176 bottles of beer on the wall, 176 bottles of beer."
print "Take one down and pass it around, 175 bottles of beer on the wall.\n"
print "175 bottles of beer on the wall, 175 bottles of beer."
print "Take one down and pass it around, 174 bottles of beer on the wall.\n"
print "174 bottles of beer on the wall, 174 bottles of beer."
print "Take one down and pass it around, 173 bottles of beer on the wall.\n"
print "173 bottles of beer on the wall, 173 bottles of beer."
print "Take one down and pass it around, 172 bottles of beer on the wall.\n"
print "172 bottles of beer on the wall, 172 bottles of beer."
print "Take one down and pass it around, 171 bottles of beer on the wall.\n"
print "171 bottles of beer on the wall, 171 bottles of beer."
print "Take one down and pass it around, 170 bottles of beer on the wall.\n"
print "170 bottles of beer on the wall, 170 bottles of beer."
print "Take one down and pass it around, 169 bottles of beer on the wall.\n"
print "169 bottles of beer on the wall, 169 bottles of beer."
print "Take one down and pass it around, 168 bottles of beer on the wall.\n"
print "168 bottles of beer on the wall, 168 bottles of beer."
print "Take one down and pass it around, 167 bottles of beer on the wall.\n"
print "167 bottles of beer on the wall, 167 bottles of beer."
print "Take one down and pass it around, 166 bottles of beer on the wall.\n"
print "166 bottles of beer on the wall, 166 bottles of beer."
print "Take one down and pass it around, 165 bottles of beer on the wall.\n"
print "165 bottles of beer on the wall, 165 bottles of beer."
print "Take one down and pass it around, 164 bottles of beer on the wall.\n"
print "164 bottles of beer on the wall, 164 bottles of beer."
print "Take one down and pass it around, 163 bottles of beer on the wall.\n"
print "163 bottles of beer on the wall, 163 bottles of beer."
print "Take one down and pass it around, 162 bottles of beer on the wall.\n"
print "162 bottles of beer on the wall, 162 bottles of beer."
print "Take one down and pass it around, 161 bottles of beer on the wall.\n"
print "161 bottles of beer on the wall, 161 bottles of beer."
print "Take one down and pass it around, 160 bottles of beer on the wall.\n"
print "160 bottles of beer on the wall, 160 bottles of beer."
print "Take one down and pass it around, 159 bottles of beer on the wall.\n"
print "159 bottles of beer on the wall, 159 bottles of beer."
print "Take one down and pass it around, 158 bottles of beer on the wall.\n"
print "158 bottles of beer on the wall, 158 bottles of beer."
print "Take one down and pass it around, 157 bottles of beer on the wall.\n"
print "157 bottles of beer on the wall, 157 bottles of beer."
print "Take one down and pass it around, 156 bottles of beer on the wall.\n"
print "156 bottles of beer on the wall, 156 bottles of beer."
print "Take one down and pass it around, 155 bottles of beer on the wall.\n"
print "155 bottles of beer on the wall, 155 bottles of beer."
print "Take one down and pass it around, 154 bottles of beer on the wall.\n"
print "154 bottles of beer on the wall, 154 bottles of beer."
print "Take one down and pass it around, 153 bottles of beer on the wall.\n"
print "153 bottles of beer on the wall, 153 bottles of beer."
print "Take one down and pass it around, 152 bottles of beer on the wall.\n"
print "152 bottles of beer on the wall, 152 bottles of beer."
print "Take one down and pass it around, 151 bottles of beer on the wall.\n"
print "151 bottles of beer on the wall, 151 bottles of beer."
print "Take one down and pass it around, 150 bottles of beer on the wall.\n"
print "150 bottles of beer on the wall, 150 bottles of beer."
print "Take one down and pass it around, 149 bottles of beer on the wall.\n"
print "149 bottles of beer on the wall, 149 bottles of beer."
print "Take one down and pass it around, 148 bottles of beer on the wall.\n"
print "148 bottles of beer on the wall, 148 bottles of beer."
print "Take one down and pass it around, 147 bottles of beer on the wall.\n"
print "147 bottles of beer on the wall, 147 bottles of beer."
print "Take one down and pass it around, 146 bottles of beer on the wall.\n"
print "146 bottles of beer on the wall, 146 bottles of beer."
print "Take one down and pass it around, 145 bottles of beer on the wall.\n"
print "145 bottles of beer on the wall, 145 bottles of beer."
print "Take one down and pass it around, 144 bottles of beer on the wall.\n"
print "144 bottles of beer on the wall, 144 bottles of beer."
print "Take one down and pass it around, 143 bottles of beer on the wall.\n"
print "143 bottles of beer on the wall, 143 bottles of beer."
print "Take one down and pass it around, 142 bottles of beer on the wall.\n"
print "142 bottles of beer on the wall, 142 bottles of beer."
print "Take one down and pass it around, 141 bottles of beer on the wall.\n"
print "141 bottles of beer on the wall, 141 bottles of beer."
print "Take one down and pass it around, 140 bottles of beer on the wall.\n"
print "140 bottles of beer on the wall, 140 bottles of beer."
print "Take one down and pass it around, 139 bottles of beer on the wall.\n"
print "139 bottles of beer on the wall, 139 bottles of beer."
print "Take one down and pass it around, 138 bottles of beer on the wall.\n"
print "138 bottles of beer on the wall, 138 bottles of beer."
print "Take one down and pass it around, 137 bottles of beer on the wall.\n"
print "137 bottles of beer on the wall, 137 bottles of beer."
print "Take one down and pass it around, 136 bottles of beer on the wall.\n"
print "136 bottles of beer on the wall, 136 bottles of beer."
print "Take one down and pass it around, 135 bottles of beer on the wall.\n"
print "135 bottles of beer on the wall, 135 bottles of beer."
print "Take one down and pass it around, 134 bottles of beer on the wall.\n"
print "134 bottles of beer on the wall, 134 bottles of beer."
print "Take one down and pass it around, 133 bottles of beer on the wall.\n"
print "133 bottles of beer on the wall, 133 bottles of beer."
print "Take one down and pass it around, 132 bottles of beer on the wall.\n"
print "132 bottles of beer on the wall, 132 bottles of beer."
print "Take one down and pass it around, 131 bottles of beer on the wall.\n"
print "131 bottles of beer on the wall, 131 bottles of beer."
print "Take one down and pass it around, 130 bottles of beer on the wall.\n"
print "130 bottles of beer on the wall, 130 bottles of beer."
print "Take one down and pass it around, 129 bottles of beer on the wall.\n"
print "129 bottles of beer on the wall, 129 bottles of beer."
print "Take one down and pass it around, 128 bottles of beer on the wall.\n"
print "128 bottles of beer on the wall, 128 bottles of beer."
print "Take one down and pass it around, 127 bottles of beer on the wall.\n"
print "127 bottles of beer on the wall, 127 bottles of beer."
print "Take one down and pass it around, 126 bottles of beer on the wall.\n"
print "126 bottles of beer on the wall, 126 bottles of beer."
print "Take one down and pass it around, 125 bottles of beer on the wall.\n"
print "125 bottles of beer on the wall, 125 bottles of beer."
print "Take one down and pass it around, 124 bottles of beer on the wall.\n"
print "124 bottles of beer on the wall, 124 bottles of beer."
print "Take one down and pass it around, 123 bottles of beer on the wall.\n"
print "123 bottles of beer on the wall, 123 bottles of beer."
print "Take one down and pass it around, 122 bottles of beer on the wall.\n"
print "122 bottles of beer on the wall, 122 bottles of beer."
print "Take one down and pass it around, 121 bottles of beer on the wall.\n"
print "121 bottles of beer on the wall, 121 bottles of beer."
print "Take one down and pass it around, 120 bottles of beer on the wall.\n"
print "120 bottles of beer on the wall, 120 bottles of beer."
print "Take one down and pass it around, 119 bottles of beer on the wall.\n"
print "119 bottles of beer on the wall, 119 bottles of beer."
print "Take one down and pass it around, 118 bottles of beer on the wall.\n"
print "118 bottles of beer on the wall, 118 bottles of beer."
print "Take one down and pass it around, 117 bottles of beer on the wall.\n"
print "117 bottles of beer on the wall, 117 bottles of beer."
print "Take one down and pass it around, 116 bottles of beer on the wall.\n"
print "116 bottles of beer on the wall, 116 bottles of beer."
print "Take one down and pass it around, 115 bottles of beer on the wall.\n"
print "115 bottles of beer on the wall, 115 bottles of beer."
print "Take one down and pass it around, 114 bottles of beer on the wall.\n"
print "114 bottles of beer on the wall, 114 bottles of beer."
print "Take one down and pass it around, 113 bottles of beer on the wall.\n"
print "113 bottles of beer on the wall, 113 bottles of beer."
print "Take one down and pass it around, 112 bottles of beer on the wall.\n"
print "112 bottles of beer on the wall, 112 bottles of beer."
print "Take one down and pass it around, 111 bottles of beer on the wall.\n"
print "111 bottles of beer on the wall, 111 bottles of beer."
print "Take one down and pass it around, 110 bottles of beer on the wall.\n"
print "110 bottles of beer on the wall, 110 bottles of beer."
print "Take one down and pass it around, 109 bottles of beer on the wall.\n"
print "109 bottles of beer on the wall, 109 bottles of beer."
print "Take one down and pass it around, 108 bottles of beer on the wall.\n"
print "108 bottles of beer on the wall, 108 bottles of beer."
print "Take one down and pass it around, 107 bottles of beer on the wall.\n"
print "107 bottles of beer on the wall, 107 bottles of beer."
print "Take one down and pass it around, 106 bottles of beer on the wall.\n"
print "106 bottles of beer on the wall, 106 bottles of beer."
print "Take one down and pass it around, 105 bottles of beer on the wall.\n"
print "105 bottles of beer on the wall, 105 bottles of beer."
print "Take one down and pass it around, 104 bottles of beer on the wall.\n"
print "104 bottles of beer on the wall, 104 bottles of beer."
print "Take one down and pass it around, 103 bottles of beer on the wall.\n"
print "103 bottles of beer on the wall, 103 bottles of beer."
print "Take one down and pass it around, 102 bottles of beer on the wall.\n"
print "102 bottles of beer on the wall, 102 bottles of beer."
print "Take one down and pass it around, 101 bottles of beer on the wall.\n"
print "101 bottles of beer on the wall, 101 bottles of beer."
print "Take one down and pass it around, 100 bottles of beer on the wall.\n"
print "100 bottles of beer on the wall, 100 bottles of beer."
print "Take one down and pass it around, 99 bottles of beer on the wall.\n"
print "99 bottles of beer on the wall, 99 bottles of beer."
print "Take one down and pass it around, 98 bottles of beer on the wall.\n"
print "98 bottles of beer on the wall, 98 bottles of beer."
print "Take one down and pass it around, 97 bottles of beer on the wall.\n"
print "97 bottles of beer on the wall, 97 bottles of beer."
print "Take one down and pass it around, 96 bottles of beer on the wall.\n"
print "96 bottles of beer on the wall, 96 bottles of beer."
print "Take one down and pass it around, 95 bottles of beer on the wall.\n"
print "95 bottles of beer on the wall, 95 bottles of beer."
print "Take one down and pass it around, 94 bottles of beer on the wall.\n"
print "94 bottles of beer on the wall, 94 bottles of beer."
print "Take one down and pass it around, 93 bottles of beer on the wall.\n"
print "93 bottles of beer on the wall, 93 bottles of beer."
print "Take one down and pass it around, 92 bottles of beer on the wall.\n"
print "92 bottles of beer on the wall, 92 bottles of beer."
print "Take one down and pass it around, 91 bottles of beer on the wall.\n"
print "91 bottles of beer on the wall, 91 bottles of beer."
print "Take one down and pass it around, 90 bottles of beer on the wall.\n"
print "90 bottles of beer on the wall, 90 bottles of beer."
print "Take one down and pass it around, 89 bottles of beer on the wall.\n"
print "89 bottles of beer on the wall, 89 bottles of beer."
print "Take one down and pass it around, 88 bottles of beer on the wall.\n"
print "88 bottles of beer on the wall, 88 bottles of beer."
print "Take one down and pass it around, 87 bottles of beer on the wall.\n"
print "87 bottles of beer on the wall, 87 bottles of beer."
print "Take one down and pass it around, 86 bottles of beer on the wall.\n"
print "86 bottles of beer on the wall, 86 bottles of beer."
print "Take one down and pass it around, 85 bottles of beer on the wall.\n"
print "85 bottles of beer on the wall, 85 bottles of beer."
print "Take one down and pass it around, 84 bottles of beer on the wall.\n"
print "84 bottles of beer on the wall, 84 bottles of beer."
print "Take one down and pass it around, 83 bottles of beer on the wall.\n"
print "83 bottles of beer on the wall, 83 bottles of beer."
print "Take one down and pass it around, 82 bottles of beer on the wall.\n"
print "82 bottles of beer on the wall, 82 bottles of beer."
print "Take one down and pass it around, 81 bottles of beer on the wall.\n"
print "81 bottles of beer on the wall, 81 bottles of beer."
print "Take one down and pass it around, 80 bottles of beer on the wall.\n"
print "80 bottles of beer on the wall, 80 bottles of beer."
print "Take one down and pass it around, 79 bottles of beer on the wall.\n"
print "79 bottles of beer on the wall, 79 bottles of beer."
print "Take one down and pass it around, 78 bottles of beer on the wall.\n"
print "78 bottles of beer on the wall, 78 bottles of beer."
print "Take one down and pass it around, 77 bottles of beer on the wall.\n"
print "77 bottles of beer on the wall, 77 bottles of beer."
print "Take one down and pass it around, 76 bottles of beer on the wall.\n"
print "76 bottles of beer on the wall, 76 bottles of beer."
print "Take one down and pass it around, 75 bottles of beer on the wall.\n"
print "75 bottles of beer on the wall, 75 bottles of beer."
print "Take one down and pass it around, 74 bottles of beer on the wall.\n"
print "74 bottles of beer on the wall, 74 bottles of beer."
print "Take one down and pass it around, 73 bottles of beer on the wall.\n"
print "73 bottles of beer on the wall, 73 bottles of beer."
print "Take one down and pass it around, 72 bottles of beer on the wall.\n"
print "72 bottles of beer on the wall, 72 bottles of beer."
print "Take one down and pass it around, 71 bottles of beer on the wall.\n"
print "71 bottles of beer on the wall, 71 bottles of beer."
print "Take one down and pass it around, 70 bottles of beer on the wall.\n"
print "70 bottles of beer on the wall, 70 bottles of beer."
print "Take one down and pass it around, 69 bottles of beer on the wall.\n"
print "69 bottles of beer on the wall, 69 bottles of beer."
print "Take one down and pass it around, 68 bottles of beer on the wall.\n"
print "68 bottles of beer on the wall, 68 bottles of beer."
print "Take one down and pass it around, 67 bottles of beer on the wall.\n"
print "67 bottles of beer on the wall, 67 bottles of beer."
print "Take one down and pass it around, 66 bottles of beer on the wall.\n"
print "66 bottles of beer on the wall, 66 bottles of beer."
print "Take one down and pass it around, 65 bottles of beer on the wall.\n"
print "65 bottles of beer on the wall, 65 bottles of beer."
print "Take one down and pass it around, 64 bottles of beer on the wall.\n"
print "64 bottles of beer on the wall, 64 bottles of beer."
print "Take one down and pass it around, 63 bottles of beer on the wall.\n"
print "63 bottles of beer on the wall, 63 bottles of beer."
print "Take one down and pass it around, 62 bottles of beer on the wall.\n"
print "62 bottles of beer on the wall, 62 bottles of beer."
print "Take one down and pass it around, 61 bottles of beer on the wall.\n"
print "61 bottles of beer on the wall, 61 bottles of beer."
print "Take one down and pass it around, 60 bottles of beer on the wall.\n"
print "60 bottles of beer on the wall, 60 bottles of beer."
print "Take one down and pass it around, 59 bottles of beer on the wall.\n"
print "59 bottles of beer on the wall, 59 bottles of beer."
print "Take one down and pass it around, 58 bottles of beer on the wall.\n"
print "58 bottles of beer on the wall, 58 bottles of beer."
print "Take one down and pass it around, 57 bottles of beer on the wall.\n"
print "57 bottles of beer on the wall, 57 bottles of beer."
print "Take one down and pass it around, 56 bottles of beer on the wall.\n"
print "56 bottles of beer on the wall, 56 bottles of beer."
print "Take one down and pass it around, 55 bottles of beer on the wall.\n"
print "55 bottles of beer on the wall, 55 bottles of beer."
print "Take one down and pass it around, 54 bottles of beer on the wall.\n"
print "54 bottles of beer on the wall, 54 bottles of beer."
print "Take one down and pass it around, 53 bottles of beer on the wall.\n"
print "53 bottles of beer on the wall, 53 bottles of beer."
print "Take one down and pass it around, 52 bottles of beer on the wall.\n"
print "52 bottles of beer on the wall, 52 bottles of beer."
print "Take one down and pass it around, 51 bottles of beer on the wall.\n"
print "51 bottles of beer on the wall, 51 bottles of beer."
print "Take one down and pass it around, 50 bottles of beer on the wall.\n"
print "50 bottles of beer on the wall, 50 bottles of beer."
print "Take one down and pass it around, 49 bottles of beer on the wall.\n"
print "49 bottles of beer on the wall, 49 bottles of beer."
print "Take one down and pass it around, 48 bottles of beer on the wall.\n"
print "48 bottles of beer on the wall, 48 bottles of beer."
print "Take one down and pass it around, 47 bottles of beer on the wall.\n"
print "47 bottles of beer on the wall, 47 bottles of beer."
print "Take one down and pass it around, 46 bottles of beer on the wall.\n"
print "46 bottles of beer on the wall, 46 bottles of beer."
print "Take one down and pass it around, 45 bottles of beer on the wall.\n"
print "45 bottles of beer on the wall, 45 bottles of beer."
print "Take one down and pass it around, 44 bottles of beer on the wall.\n"
print "44 bottles of beer on the wall, 44 bottles of beer."
print "Take one down and pass it around, 43 bottles of beer on the wall.\n"
print "43 bottles of beer on the wall, 43 bottles of beer."
print "Take one down and pass it around, 42 bottles of beer on the wall.\n"
print "42 bottles of beer on the wall, 42 bottles of beer."
print "Take one down and pass it around, 41 bottles of beer on the wall.\n"
print "41 bottles of beer on the wall, 41 bottles of beer."
print "Take one down and pass it around, 40 bottles of beer on the wall.\n"
print "40 bottles of beer on the wall, 40 bottles of beer."
print "Take one down and pass it around, 39 bottles of beer on the wall.\n"
print "39 bottles of beer on the wall, 39 bottles of beer."
print "Take one down and pass it around, 38 bottles of beer on the wall.\n"
print "38 bottles of beer on the wall, 38 bottles of beer."
print "Take one down and pass it around, 37 bottles of beer on the wall.\n"
print "37 bottles of beer on the wall, 37 bottles of beer."
print "Take one down and pass it around, 36 bottles of beer on the wall.\n"
print "36 bottles of beer on the wall, 36 bottles of beer."
print "Take one down and pass it around, 35 bottles of beer on the wall.\n"
print "35 bottles of beer on the wall, 35 bottles of beer."
print "Take one down and pass it around, 34 bottles of beer on the wall.\n"
print "34 bottles of beer on the wall, 34 bottles of beer."
print "Take one down and pass it around, 33 bottles of beer on the wall.\n"
print "33 bottles of beer on the wall, 33 bottles of beer."
print "Take one down and pass it around, 32 bottles of beer on the wall.\n"
print "32 bottles of beer on the wall, 32 bottles of beer."
print "Take one down and pass it around, 31 bottles of beer on the wall.\n"
print "31 bottles of beer on the wall, 31 bottles of beer."
print "Take one down and pass it around, 30 bottles of beer on the wall.\n"
print "30 bottles of beer on the wall, 30 bottles of beer."
print "Take one down and pass it around, 29 bottles of beer on the wall.\n"
print "29 bottles of beer on the wall, 29 bottles of beer."
print "Take one down and pass it around, 28 bottles of beer on the wall.\n"
print "28 bottles of beer on the wall, 28 bottles of beer."
print "Take one down and pass it around, 27 bottles of beer on the wall.\n"
print "27 bottles of beer on the wall, 27 bottles of beer."
print "Take one down and pass it around, 26 bottles of beer on the wall.\n"
print "26 bottles of beer on the wall, 26 bottles of beer."
print "Take one down and pass it around, 25 bottles of beer on the wall.\n"
print "25 bottles of beer on the wall, 25 bottles of beer."
print "Take one down and pass it around, 24 bottles of beer on the wall.\n"
print "24 bottles of beer on the wall, 24 bottles of beer."
print "Take one down and pass it around, 23 bottles of beer on the wall.\n"
print "23 bottles of beer on the wall, 23 bottles of beer."
print "Take one down and pass it around, 22 bottles of beer on the wall.\n"
print "22 bottles of beer on the wall, 22 bottles of beer."
print "Take one down and pass it around, 21 bottles of beer on the wall.\n"
print "21 bottles of beer on the wall, 21 bottles of beer."
print "Take one down and pass it around, 20 bottles of beer on the wall.\n"
print "20 bottles of beer on the wall, 20 bottles of beer."
print "Take one down and pass it around, 19 bottles of beer on the wall.\n"
print "19 bottles of beer on the wall, 19 bottles of beer."
print "Take one down and pass it around, 18 bottles of beer on the wall.\n"
print "18 bottles of beer on the wall, 18 bottles of beer."
print "Take one down and pass it around, 17 bottles of beer on the wall.\n"
print "17 bottles of beer on the wall, 17 bottles of beer."
print "Take one down and pass it around, 16 bottles of beer on the wall.\n"
print "16 bottles of beer on the wall, 16 bottles of beer."
print "Take one down and pass it around, 15 bottles of beer on the wall.\n"
print "15 bottles of beer on the wall, 15 bottles of beer."
print "Take one down and pass it around, 14 bottles of beer on the wall.\n"
print "14 bottles of beer on the wall, 14 bottles of beer."
print "Take one down and pass it around, 13 bottles of beer on the wall.\n"
print "13 bottles of beer on the wall, 13 bottles of beer."
print "Take one down and pass it around, 12 bottles of beer on the wall.\n"
print "12 bottles of beer on the wall, 12 bottles of beer."
print "Take one down and pass it around, 11 bottles of beer on the wall.\n"
print "11 bottles of beer on the wall, 11 bottles of beer."
print "Take one down and pass it around, 10 bottles of beer on the wall.\n"
print "10 bottles of beer on the wall, 10 bottles of beer."
print "Take one down and pass it around, 9 bottles of beer on the wall.\n"
print "9 bottles of beer on the wall, 9 bottles of beer."
print "Take one down and pass it around, 8 bottles of beer on the wall.\n"
print "8 bottles of beer on the wall, 8 bottles of beer."
print "Take one down and pass it around, 7 bottles of beer on the wall.\n"
print "7 bottles of beer on the wall, 7 bottles of beer."
print "Take one down and pass it around, 6 bottles of beer on the wall.\n"
print "6 bottles of beer on the wall, 6 bottles of beer."
print "Take one down and pass it around, 5 bottles of beer on the wall.\n"
print "5 bottles of beer on the wall, 5 bottles of beer."
print "Take one down and pass it around, 4 bottles of beer on the wall.\n"
print "4 bottles of beer on the wall, 4 bottles of beer."
print "Take one down and pass it around, 3 bottles of beer on the wall.\n"
print "3 bottles of beer on the wall, 3 bottles of beer."
print "Take one down and pass it around, 2 bottles of beer on the wall.\n"
print "1 bottle of beer on the wall, 1 bottle of beer.\n\n1 bottle of beer on the wall, 1 bottle of beer.\n Take one down and pass it around, no more bottles of beer on the wall.\n"
print "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.\n";


```

> **descendency said:**
> I think he was trying to be funny.

I was tempted to do that too, but I'm too lazy.

I am trying to be funny, and I am lazy :-)

---

### Post by jacensolo on 2008-08-02
Python with a twist. I would have used string variables to make it easier on myself, but that made it less readable.

How did do i get my syntax highlighted in the code block?

[php]#bottles of beer
#Added the abillity to do it again and choose how many bottles are on the wall after the inital song
#No error handling since this is basic. ex: Don't put a string in the string function.

#The start is how many bottles you want to start from
def sing(start):
    #Start from the start varible, go to 0 in a step by -1
    for bottles in range(start,-1,-1):
        #If the number of bottles is above two...
        if bottles > 2:
            print bottles, "bottles of beer on the wall,", bottles, "bottles of beer.\n", \
                  "Take one down, pass it around,", (bottles-1), "bottles of beer on the wall\n\n"
        #From here one we know exactly how many bottles of beer are on the wall - no need to use the variable.
        elif bottles == 2:
            print "2 bottles of beer of beer on the wall, 2 bottles of beer. \nTake one down, pass it around, 1 bottle of beer one the wall.\n\n"
        elif bottles == 1:
            print "1 bottle of beer on the wall, 1 bottle of beer.\nTake one down, pass it around, no more bottles of beer on the wall\n\n"
        elif bottles == 0:
            print "No more bottles of beer on the wall, no bottles of beer. \nGo to the store and by some more, 99 bottles of beer on the wall."

#start from 99
sing(99)


#Ask to do it again indefinitely.
while True:
    if raw_input("\n\n\nType 'again' to do it again.") == "again":
        sing(int((raw_input("Start from how many bottles?\n"))))
[/php]

---

### Post by LaRoza on 2008-08-02
> **jacensolo said:**
> Python with a twist. I would have used string variables to make it easier on myself, but that made it less readable.

How did do i get my syntax highlighted in the code block?


By following the link in my first post about how to post code on the forum ;) [http://ubuntuforums.org/showpost.php?p=5499342&postcount=1](http://ubuntuforums.org/showpost.php?p=5499342&postcount=1)

---

### Post by Kadrus on 2008-08-02
or me telling you:p
use the PHP tags
[ PHP ] [ PHP ]
Dont use space

---

### Post by robertchahine on 2008-08-02
when is the last day of this challenge?

---

### Post by Kadrus on 2008-08-02
> when is the last day of this challenge?
I dont think there is.
You can always post your code at any time.

---

### Post by LaRoza on 2008-08-02
> **robertchahine said:**
> when is the last day of this challenge?

When it is over.

---

### Post by Ed J on 2008-08-02
> **LaRoza said:**
> Yes, I know. I just didn't want a new programmer coming in and seeing those tricks and getting depressed :-)

I saw the post by Def13b and I was blown away. I didn't get depressed but I did pick up my Python book shortly after.

---

### Post by collinp on 2008-08-02
> **LaRoza said:**
> Yes, I know. I just didn't want a new programmer coming in and seeing those tricks and getting depressed :-)

Im depressed :lolflag:.

---

### Post by robertchahine on 2008-08-02
[PHP]#include<stdio.h>
int main(void)
{
int i=99;
for(i;i>=3;i--)
{printf("%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottles of beer on the wall\n\n",i,i,i-1);}

printf("2 bottles of beer on the wall, 2 bottles of beer.\nTake one down and pass it around, 1 bottle of beer on the wall.\n\n");

printf("1 bottle of beer on the wall, 1 bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n\n");

printf("No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.\n\n");

return 0;
}[/PHP]

---

### Post by aktiwers on 2008-08-02
Finally I made a version without errors :) Sorry for spamming different versions, I am still learning.
And great thread by the way, I hope to see more.

[php]
#!/usr/bin/python
#
# Drink drink! ver. 0.3
# "99 Bottles of Beer". 

# This is the amount of beer, increase if you want more beer (remember 100 is actually == 99 in output)
numbersofbeer = 100

#This is the loop that makes the song. 
while numbersofbeer > 3:
    numbersofbeer = numbersofbeer -1
    print numbersofbeer, "bottles of beer on the wall,", numbersofbeer, "bottles of beer.\nTake one down and pass it around,", numbersofbeer-1, "bottles of beer on the wall.\n"
if numbersofbeer == 3:
    numbersofbeer = numbersofbeer-1
    print numbersofbeer, "bottles of beer on the wall,", numbersofbeer, "bottles of beer.\nTake one down and pass it around,", numbersofbeer-1, "bottle of beer on the wall.\n"
if numbersofbeer < 3:
    numbersofbeer = numbersofbeer-1
    print numbersofbeer,"bottle of beer on the wall,", numbersofbeer, "bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n"
    print "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more,",numbersofbeer+98 ,"bottles of beer on the wall.\n"
[/php]

---

### Post by CptPicard on 2008-08-02
+1 to Def13b from here, a nice solution without being so "clever" it becomes obfuscated.

---

### Post by robertchahine on 2008-08-02
> When it is over.
Good, and whem the challenge n:2 begin , because i like this thread

---

### Post by Kadrus on 2008-08-02
Maybe you should subscribe to the [RSS feeds of the programming talk sub forum]("http://ubuntuforums.org/external.php?type=RSS2&forumids=39") to say informed

---

### Post by LaRoza on 2008-08-02
I will chose the winner of this challenge on Wednesday.

Unlike the other challenges, each challenge will be open forever, so new forum members can always try it out without necromancing.

These will hopefully provide a chain of tasks that are good for those learning and more importantly will provide a way to get feedback from other programmers on a variety of topics.

---

### Post by CptPicard on 2008-08-02
May I suggest that you really choose the winner based on one being a good n00b, instead of some guru who demonstrates something interesting but creates a really out of this planet solution... I have a feeling that the programming challenges have a way of growing harder and harder simply by virtue of winner being more and more competent...

---

### Post by drubin on 2008-08-02
> **CptPicard said:**
> May I suggest that you really choose the winner based on one being a good n00b, instead of some guru who demonstrates something interesting but creates a really out of this planet solution... I have a feeling that the programming challenges have a way of growing harder and harder simply by virtue of winner being more and more competent...

Agreed!!! See how many other people have attempted  this challenge as apposed to the previous one.

---

### Post by paul_philp on 2008-08-02
Hello all, saw this on reddit and thought I'd give it a go. I'm no programmer but have been mucking around with python lately and crudely nailed this together over the past few hours using what I've learned recently. It's not perfect, as on the last verse it says "1 bottle**s** of beer", but I can live with that. (Not sure how to post the colour-highlighted syntax?) anyway -
[PHP]
from time import sleep

bottles1 = 99
bottles2 = 1
bottles3 = bottles1 - bottles2

print bottles1, "bottles of beer on the wall,", bottles1, "bottles of beer"
print "take one down, pass it around,"
print bottles3, "bottles of beer on the wall"
print
sleep(1)

while bottles3 > 1:
    print bottles3, "bottles of beer on the wall", bottles3, "bottles of beer"
    print "take one down, pass it around,"
    bottles3 = bottles3 - 1
    print bottles3, "bottles of beer on the wall"
    print
    sleep(1)

print "No bottles of beer on the wall, no bottles of beer"
print "go to the store, buy some more"
print "99 bottles of beer on the wall"
[/PHP]

---

### Post by LaRoza on 2008-08-02
> **CptPicard said:**
> May I suggest that you really choose the winner based on one being a good n00b, instead of some guru who demonstrates something interesting but creates a really out of this planet solution... I have a feeling that the programming challenges have a way of growing harder and harder simply by virtue of winner being more and more competent...

Yes, that is what I am going to do. I think having winners choose the topics leads to the harder ladder.

I will maintain the beginner challenges for now, but I hope people give suggestions on the Index thread on topics!

Maybe you or someone could have different series of challenges with harder topics?

---

### Post by drubin on 2008-08-02
> **paul_philp said:**
> Hello all, saw this on reddit and thought I'd give it a go. I'm no programmer but have been mucking around with python lately and crudely nailed this together over the past few hours using what I've learned recently. It's not perfect, as on the last verse it says "1 bottle**s** of beer", but I can live with that. (Not sure how to post the colour-highlighted syntax?) anyway -


Firstly I like the time delay!! Think it is pretty cool and hasn't been used before and makes it more like a program "singing" the song.

As for the colors use the PHP tags, they supposed to provide php syntax support but they mostly work for others as well.

[NOPARSE]
[PHP]Stuff you want to me highlighted  [/PHP][/NOPARSE]

---

### Post by drubin on 2008-08-02
> **LaRoza said:**
> I will maintain the beginner challenges for now, but I hope people give suggestions on the Index thread on topics!

You truly do so much for these forums. Do you work for them full time or have another job?  

Thanks

---

### Post by LaRoza on 2008-08-02
> **rubinboy said:**
> You truly do so much for these forums. Do you work for them full time or have another job?  

Thanks

We are all volunteers :-)

I at the moment am a part time student and don't have a full time job at the moment (soon I will I think)

---

### Post by paul_philp on 2008-08-02
> **rubinboy said:**
> Firstly I like the time delay!! Think it is pretty cool and hasn't been used before and makes it more like a program "singing" the song.

As for the colors use the PHP tags, they supposed to provide php syntax support but they mostly work for others as well.

[NOPARSE]
[PHP]Stuff you want to me highlighted  [/PHP][/NOPARSE]

Thanks! Have edited ;-)

---

### Post by drubin on 2008-08-02
> **LaRoza said:**
> We are all volunteers :-)

I at the moment am a part time student and don't have a full time job at the moment (soon I will I think)

That is what I thought, but I look at the time and effort you put into this place. (and the impressive post count) and wondered how you kept it up if you had a full time job. :)

---

### Post by LaRoza on 2008-08-02
> **rubinboy said:**
> That is what I thought, but I look at the time and effort you put into this place. (and the impressive post count) and wondered how you kept it up if you had a full time job. :)

Well, some people here post while at work a lot more than their bosses would like!

---

### Post by jimi_hendrix on 2008-08-02
My first working C++ program that isn't out of a tutorial


if you have a way to stop the program from exiting other then a line break at "return 0" please pm it to me


[PHP]
#include "stdafx.h"
#include <iostream>
#include <stdio.h>

using namespace std;

int _tmain(int argc, _TCHAR* argv[])
{
	int bottles = 99;
	while (bottles >2)
	{
		//prints verses 1-98
		cout << bottles << " bottles of beer on the wall," << endl << bottles << " bottles of beer. Take one down and pass it around," << endl;
		bottles--;
		cout << bottles << " bottles of beer on the wall." << endl << endl;
	}
	//prints the last 3 verses because i was to lazy to 
        //do ifs/else ifs
	cout << "2 bottles of beer on the wall, 2 bottles of beer." << endl << "Take one down and pass it around, 1 bottle of beer on the wall." << endl << endl << "1 bottle of beer on the wall, 1 bottle of beer." << endl << "Take one down and pass it around, no more bottles of beer on the wall." << endl << endl << "No more bottles of beer on the wall, no more bottles of beer." << endl << "Go to the store and buy some more, 99 bottles of beer on the wall."<<endl;
	/*put a line break next to return because i havn't      figured out how to put code to stop it from exiting yet...*/
	return 0;
}

[/PHP]

---

### Post by drubin on 2008-08-02
> **jimi_hendrix said:**
> 
if you have a way to stop the program from exiting other then a line break at "return 0" please pm it to me


Please do not PM any solutions/answers to questions posted on these forums post the solution! Encase other people would like the answers.

---

### Post by jimi_hendrix on 2008-08-02
> **rubinboy said:**
> Please do not PM any solutions/answers to questions posted on these forums encase other people would like the answers. Helps others

good point

---

### Post by Phoenix1701 on 2008-08-02
I'm not a beginner, though I am a novice at Python specifically, so please consider this an example and not an actual submission.  Nonetheless, I couldn't resist taking on this challenge with one minor tweak: instead of '99', '98', etc., my program prints 'ninety-nine', 'ninety-eight', etc. all the way down to zero.  Here it is:

[php]
#!/usr/bin/env python
# encoding: utf-8
"""
bottles-of-beer.py

Created by Brian Ellis on 2008-08-02.
The source of this program is hereby released to the public domain.
"""

"""
The number of beers we begin with.  Don't set this to higher than 99, since we
can't count that high.
"""
kInitialBeerSupply = 99

def main():
  """
  Main function.  This will be automatically executed when the script is run
  unless it is imported as a module.
  """
  beers_left = kInitialBeerSupply
  stop_drinking = False
  while not stop_drinking:
    how_many = cardinal_for_num_beers(beers_left)
    bottles = bottles_for_num_beers(beers_left)
    print "%s %s of beer on the wall, %s %s of beer." % (how_many.capitalize(),
                                                         bottles,
                                                         how_many,
                                                         bottles)
    (what_to_do, refill_stock) = action_for_num_beers(beers_left)
    if (refill_stock):
      beers_left = kInitialBeerSupply
      stop_drinking = True  # Guess it's time to call it a night...
    else:
      beers_left -= 1       # Chug! Chug! Chug!
    
    how_many = cardinal_for_num_beers(beers_left)
    bottles = bottles_for_num_beers(beers_left)
    print "%s, %s %s of beer on the wall.\n" % (what_to_do.capitalize(),
                                                how_many,
                                                bottles)

class TooManyBeers(Exception):
  """
  Exception raised when we have too much beer to count.  We can only count up
  to ninety-nine, because anything above that is complicated, and anyway we're
  going to get sloshed, so it soon won't matter.
  """
  def __init__(self, num):
    msg = "too many beers (%d). Please drink some, then try again." % (num)
    super(TooManyBeers, self).__init__(msg)

class InvalidBeers(Exception):
  """
  Exception raised when we claim to have an invalid number of beers.
  This could mean we have negative beers, a non-integer number of beers,
  a complex number of beers, or that the number of beers we got was not actually
  a number at all, but something else, such as a string, an actual collection of
  beer bottles, or an orangutan.  In Python, one never really knows.  In any
  case, this exception usually indicates that you are too drunk and should not
  drink any more beers.
  """
  def __init__(self, num):
    msg = ("invalid number of beers (%d). " % (num) +
           "Negative and imaginary beers are frowned upon.")
    super(InvalidBeers, self).__init__(msg)

def action_for_num_beers(num_beers):
  """
  Returns a tuple of (string, boolean) indicating what we should do given the
  number of beers we have, and whether doing this will replenish our beer
  supply.  Unsurprisingly, the answer to the first question is usually "drink
  more beer".
  """
  if num_beers > 0:                                  # Have beer?
    return ('take one down, pass it around', False)  # Drink beer!
  else:                                              # Don't have beer?
    return ('go to the store, buy some more', True)  # Buy more beer!

def bottles_for_num_beers(num_beers):
  """
  Returns the correct form of the word "bottle" to use when addressing the given
  number of beers.  In English, this will always be either 'bottle' or 'bottles'
  but in other languages (Arabic, Sami, and Scots Gaelic, to name a few) we will
  need special forms for two beers as well.
  """
  if num_beers == 1:
    return 'bottle'
  else:
    return 'bottles'

def cardinal_for_num_beers(num_beers):
  """
  Returns the 'cardinal' form of the given number of beers as a string.  The use
  of the word 'cardinal' here is to distinguish it from 'ordinal'; i.e.,
  cardinal_for_num_beers(1) will return 'one' in English, not 'first'.
  Since we know we're dealing with beers here, the cardinal form of 0 is not
  'zero', but rather 'no more', as when one runs out of beer one is typically
  not interested in talking about the beer one doesn't have, but rather in
  drawing attention to the problem and getting more beer.
  """
  # First, handle special cases for invalid or irregular numbers of beers.
  if num_beers >= 100:
    raise TooManyBeers(num_beers)
  elif num_beers == 0:
    return 'no more'
  elif num_beers == 10:
    return 'ten'
  elif num_beers == 11:
    return 'eleven'    # would be 'oneteen'
  elif num_beers == 12:
    return 'twelve'    # would be 'twoteen'
  elif num_beers == 13:
    return 'thirteen'  # would be 'threeteen'
  elif num_beers == 15:
    return 'fifteen'   # would be 'fiveteen'
  elif num_beers == 18:
    return 'eighteen'  # would be 'eightteen'
  
  # If the written form of the number is regular, we can use a fairly simple
  # algorithm to figure out what it ought to be.
  try:
    tens_place = int(num_beers / 10)
    ones_place = int(num_beers % 10)
  except(TypeError, e):
    # If we got here, num_beers was not a number.
    raise InvalidBeers(num_beers)
  
  tens_cardinal = None
  ones_cardinal = None
  if tens_place == 0:
    tens_cardinal = ''
  elif tens_place == 1:
    tens_cardinal = 'teen'
  elif tens_place == 2:
    tens_cardinal = 'twenty'
  elif tens_place == 3:
    tens_cardinal = 'thirty'
  elif tens_place == 4:
    tens_cardinal = 'forty'
  elif tens_place == 5:
    tens_cardinal = 'fifty'
  elif tens_place == 6:
    tens_cardinal = 'sixty'
  elif tens_place == 7:
    tens_cardinal = 'seventy'
  elif tens_place == 8:
    tens_cardinal = 'eighty'
  elif tens_place == 9:
    tens_cardinal = 'ninety'
  else:
    raise InvalidBeers(num_beers)
  
  if ones_place == 0:
    ones_cardinal = ''
  elif ones_place == 1:
    ones_cardinal = 'one'
  elif ones_place == 2:
    ones_cardinal = 'two'
  elif ones_place == 3:
    ones_cardinal = 'three'
  elif ones_place == 4:
    ones_cardinal = 'four'
  elif ones_place == 5:
    ones_cardinal = 'five'
  elif ones_place == 6:
    ones_cardinal = 'six'
  elif ones_place == 7:
    ones_cardinal = 'seven'
  elif ones_place == 8:
    ones_cardinal = 'eight'
  elif ones_place == 9:
    ones_cardinal = 'nine'
  else:
    raise InvalidBeers(num_beers)
  
  if tens_place <= 1 or ones_place == 0:
    return '%s%s' % (ones_cardinal, tens_cardinal)
  else:
    return '%s-%s' % (tens_cardinal, ones_cardinal)

if __name__ == '__main__':
  main()


[/php]

---

### Post by CptPicard on 2008-08-02
> **LaRoza said:**
> Well, some people here post while at work a lot more than their bosses would like!

I post here during work way more than boss (me) would like :oops:

I'll think about some interesting things to write a challenge of... my own participation to challenges has been limited because I actually prefer to sleep and live away from keyboard too, especially the last ones seemed more like work than anything else :)

---

### Post by grumbles79 on 2008-08-02
Here's my entry.  It's my first program written in Erlang. 

```
-module(bottles99).
-export([print/1]).

print(X) ->
    if
	X > 1 ->
	    io:format("~w bottles of beer on the wall. ~w bottles of beer.~n", [X, X]),
	    Temp = X-1,
	    if
		Temp > 1 ->
		    io:format("Take one down, pass it around, ~w bottles of beer on the wall.~n", [Temp]);
		Temp == 1 ->
		    io:format("Take one down, pass it around, ~w bottle of beer on the wall.~n", [Temp])
	    end,
	    %% Call the print method again with the decremented Temp counter
	    print(Temp);
	X == 1 ->
	    io:format("~w bottle of beer on the wall. ~w bottle of beer.~n", [X, X]),
	    Temp = X-1,
	    io:format("Take one down, pass it around, no more bottles of beer on the wall.~n", []),
	    %% Call the print method again with the decremented Temp counter
	    print(Temp);
	X == 0 ->
	    io:format("No more bottles of beer on the wall, no more bottles of beer.~n", []),
	    io:format("Go to the store and buy some more, 99 bottles of beer on the wall.~n",[])
    end.

```

To Run:

1. save the code in a file named 'bottes99.erl'
2. start the erlang interpreter in the folder 'bottles99.erl' is in
3. type 'c(bottles99).' to compile the code
3. to run, type 'bottles99:print(99).'

that's supposed to be a ':' then a 'p', not a smiley of some sort

---

### Post by mssever on 2008-08-02
> **Phoenix1701 said:**
> I'm not a beginner, though I am a novice at Python specifically, so please consider this an example and not an actual submission.  Nonetheless, I couldn't resist taking on this challenge with one minor tweak: instead of '99', '98', etc., my program prints 'ninety-nine', 'ninety-eight', etc. all the way down to zero.  Here it is:
Python style hint: It's a strong convention in the Python world to use four spaces for indentation, not two.

---

### Post by Phoenix1701 on 2008-08-02
> **mssever said:**
> Python style hint: It's a strong convention in the Python world to use four spaces for indentation, not two.

Ah, thanks for the tip.  My company has a style guide which includes two spaces for indentation, so I tend to follow that out of habit.

---

### Post by ghostdog74 on 2008-08-02
> **Phoenix1701 said:**
> Ah, thanks for the tip.  My company has a style guide which includes two spaces for indentation, so I tend to follow that out of habit.

it doesn't matter, as long as you do follow a convention.

---

### Post by LaRoza on 2008-08-02
Oh, for languages that are not executable directly (like the Python, Ruby, and other scripts) and isn't Ada, Java, C or C++, please tell how to compile/run it. I saw a Lispy one earlier that may have been scheme, and I don't want to play spin the interpeter. I never used Erlang so that one has to be given as well.

---

### Post by LaRoza on 2008-08-02
> **ghostdog74 said:**
> it doesn't matter, as long as you do follow a convention.

4 spaces is the convention though.

---

### Post by ghostdog74 on 2008-08-02
> **LaRoza said:**
> 4 spaces is the convention though.
It don't matter, as long as its consistent. Conventions are made by people. If I want to follow, i will. But if I don't, I will make my own, and be consistent throughout.

---

### Post by LaRoza on 2008-08-02
> **ghostdog74 said:**
> It don't matter, as long as its consistent. Conventions are made by people. If I want to follow, i will. But if I don't, I will make my own, and be consistent throughout.

Well, if only for me, 4 spaces are a good idea :-)

---

### Post by iofthemourning on 2008-08-03
good times. hope these continue.

beer.py
[PHP]
end="s"
for i in range(1,101):
	if i==100:
		print "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall." 
	else:
		print "%d bottle%s of beer on the wall, %d bottle%s of beer." %(100-i, end, 100-i, end)
		if i==99:
			print "Take one down and pass it around, no more bottles of beer on the wall." 
		else:
			if i==98:
				end=""
			print "Take one down and pass it around, %d bottle%s of beer on the wall." %(99-i, end)
[/PHP]

run: python beer.py

---

### Post by ghostdog74 on 2008-08-03
just bored on a sunday morning
```

awk 'BEGIN{ j=i=100}
NR<=98{
   i--;--j   
   print i " bottles of beer on the wall, " i" bottles of beer."
   print "Take one down and pass it around, " j " bottles of beer on the wall."
}
NR>98{ 
    print "1 bottle of beer on the wall, 1 bottle of beer."
    print "Take one down and pass it around, no more bottles of beer on the wall."
    print "No more bottles of beer on the wall, no more bottles of beer."
    print "Go to the store and buy some more, 99 bottles of beer on the wall." 
    exit
}' /var/log/messages

```

---

### Post by wsppan on 2008-08-03
[PHP]
#!/usr/bin/perl

use strict;
use warnings;

for(my $num = 99; $num > 0; $num--) {
    take_one($num);
}

print "No more bottles of beer on the wall, no more bottles of beer.\n";
print "Go to the store and buy some more, 99 bottles of beer on the wall.\n";

sub take_one {
    my $bottle_num = shift;

    # is next bottle 0
    my $next_bottle_num = $bottle_num == 1 ? "no more" : $bottle_num - 1;

    # is current bottle a single bottle
    my $bottles = $bottle_num == 1 ? "bottle" : "bottles";

    # is next bottle a single bottle
    my $next_bottles = $next_bottle_num eq "1" ? "bottle" : "bottles";

    # sing along!
    print "$bottle_num $bottles of beer on the wall, ";
    print "$bottle_num $bottles of beer.\n";
    print "Take one down and pass it around, ";
    print "$next_bottle_num $next_bottles of beer on the wall.\n";
    print "\n\n";
}[/PHP]

---

### Post by samjh on 2008-08-03
> **CptPicard said:**
> May I suggest that you really choose the winner based on one being a good n00b, instead of some guru who demonstrates something interesting but creates a really out of this planet solution... 

Agreed

---

### Post by Lux Perpetua on 2008-08-03
This is my first Haskell program, so I'm open to criticism.
```
import Char(toUpper)

main = putStrLn (e 99)

e :: Int -> String
e x = ((\(c : cs) -> (toUpper c : cs))(d x)) ++ ", " 
      ++ (c x) ++ ".\n" 
      ++ case x of 
           0         -> "Go to the store and buy some more, " ++ (d 99) ++ "."
           otherwise -> "Take one down and pass it around, " ++ (d (x-1)) ++ ".\n\n"
                        ++ (e (x-1))

d :: Int -> String
d x = (c x) ++ " on the wall"

c :: Int -> String
c x = case x of
        0         -> "no more"
        otherwise -> show x
      ++ " bottle" ++
      case x of 
        1         -> ""
        otherwise -> "s" 
      ++ " of beer"

```
**Edit:** okay, sorry, I think I'm done editing. 
**Edit:** I lied. [Updated version](http://ubuntuforums.org/showthread.php?t=876479&page=4#136)

To run this, you'll need a Haskell compiler, like ghc6 (in the repositories). Save the file to, say, "bottles.hs", and then run **runghc bottles**.

Also, and I think LaRoza knows this, but to be clear: I'm not a n00b programmer, just a Haskell n00b. :-)

---

### Post by runningwithscissors on 2008-08-03
[SIZE="3"]Erlang[/SIZE]

I don't really _know_ Erlang, but this seemed piss easy, so...
```
-module(beerwall).
-export([beer/1]).

beer(0) ->
    io:format("No more bottles of beer on the wall, no more bottles of beer.~nGo to the store and buy some more, 99 bottles of beer on the wall.~n", []);
beer(1) ->
    io:format("1 bottle of beer on the wall, 1 bottle of beer.~nTake one down and pass it around, no more bottles of beer on the wall.~n~n", []),
    beer(0);
beer(2) ->
    io:format("2 bottles of beer on the wall, 2 bottles of beer.~nTake one down and pass it around, 1 bottle of beer on the wall.~n~n", []),
    beer(1);
beer(N) ->
     io:format("~w bottles of beer on the wall, ~w bottles of beer.~nTake one down and pass it around, ~w bottles of beer on the wall.~n~n", [N, N, N-1]),
     beer(N - 1).
```

EDIT: I see Erlang's already been done, but, what the hell. :)

---

### Post by bobbocanfly on 2008-08-03
Very boring approach in C. Has some cool indentation when you run it though, but I cant work out what is causing it.

```
#define BOTTLES 99

int main(int argc, char **argv[])
{
    int i, minus;
        
    for (i = BOTTLES; i > -1; i--)
    {
        if (i == 0)
        {
            printf("No more bottles of beer on the wall, no more bottles of beer. \n\
                   Go to the store and buy some more, 99 bottles of beer on the wall.\n\n");
        }
        else if (i == 1)
        {
            printf("1 bottle of beer on the wall, 1 bottle of beer. \n\
                   Take one down and pass it around, no more bottles of beer on the wall.\n\n");
        }
        else if (i == 2)
        {
            printf("2 bottles of beer on the wall, 2 bottles of beer. \n\
                   Take one down and pass it around, 1 bottle of beer on the wall.\n\n");
        }
        else
        {
            minus = i - 1;
            printf("%i bottles of beer on the wall, %i bottles of beer. \n\
                   Take one down and pass it around, %i bottles of beer\n\n", i, i, minus);
        }
    }
    
    return 0;
}
```

---

### Post by schauerlich on 2008-08-03
> **bobbocanfly said:**
> Very boring approach in C. Has some cool indentation when you run it though, but I cant work out what is causing it.

You escape the line break, but not the tab.

---

### Post by nvteighen on 2008-08-03
> **CptPicard said:**
> May I suggest that you really choose the winner based on one being a good n00b, instead of some guru who demonstrates something interesting but creates a really out of this planet solution... I have a feeling that the programming challenges have a way of growing harder and harder simply by virtue of winner being more and more competent...

That's an interesting recursive function... Can someone model that in a program? ;)

---

### Post by NovaAesa on 2008-08-03
> **EDavidBurg said:**
> You escape the line break, but not the tab.

Wouldn't it be because s/he is escaping the "n" but then also escaping the "T" on the next line? /t would be a tab char.

---

### Post by unutbu on 2008-08-03
[PHP]#!/usr/bin/env python

class Beers(object):
    def __init__(self,bottles):
        self.max=bottles
        self.bottles=bottles

    def say_bottle(self):        
        if self.bottles>1:
            return "%s bottles"%self.bottles
        elif self.bottles==1:
            return "1 bottle"
        else:
            return "no more bottles"

    def check_wall(self):
        return "%s of beer on the wall"%self.say_bottle()

    def check_inventory(self):
        print ("%s, %s of beer."%(self.check_wall(),
                                  self.say_bottle())
               ).capitalize()

    def relax(self):
        self.bottles=self.bottles-1
        print "Take one down and pass it around, %s.\n"%self.check_wall()

    def refill(self):
        self.bottles=self.max
        print "Go to the store and buy some more, %s."%self.check_wall()

    def drink(self):
        while self.bottles:
            self.check_inventory()
            self.relax()
        self.check_inventory()
        self.refill()

if __name__ == "__main__":
    beer=Beers(99)
    beer.drink()
[/PHP]

---

### Post by CptPicard on 2008-08-03
> **nvteighen said:**
> That's an interesting recursive function... Can someone model that in a program? ;)

Genetic algorithms already are a major class of AI methods... :)

---

### Post by SteelDragon on 2008-08-03
Hello all,

I haven't read the other entries yet, so I'll go back and do that today, but I do have my own. This is my first attempt at a program in python (that isn't Hello World or the Fib sequence), so criticism/advice/mockery is welcome and even solicited. Well, not so much the mockery.

One issue I had is that I'm a rural type of guy, so I like me beer from cans :). I know not everybody shares my preference, so I have to ask the user what they drink from before starting. It's been tested with bottle(s), can(s), glass(es) and box(es).

Cheers.

```

#!/usr/bin/python

#################################################################
# Print the lyrics to the song "99 bottles of beer on the wall" #
# Ask the user what they want to drink from first, as it may    #
# not be bottles.                                               #
#################################################################

# Handle the pluralization and output of the container name
def container( beers, vessel = 'bottle', ends_in_ss = False ):
	if ends_in_ss:
		if beers != 1:
			vessel = vessel + 'es'
	else:
		if beers != 1:
			vessel = vessel + 's'

	return vessel

# Words that end in 'ss' (such as glass) or in x (box) need an 'es' to pluralize
def s_words( holder ):
	if (holder[ len( holder ) - 1 ] == 's' and holder[ len( holder ) - 2 ] == 's') or holder[ len( holder ) - 1 ] == 'x':
		return True
	else:
		return False

def main():
	bottles = 99

	vessel = raw_input("What do you like to drink from? ")
	length = len( vessel )
	
	# If the user entered their preferred format as a plural, strip the s
	if vessel[ length - 1 ] == 's' and vessel[ length - 2 ] != 'e' and vessel[ length - 2 ] != 's': # Non s-word entered as plural
		tempVessel = vessel[ 0 : length - 1 ]
		vessel = tempVessel
	elif ( vessel[ length - 1 ] == 's' and vessel[ length - 2 ] == 'e' ): # Ends in 'ss' or 'x' and is plural
		tempVessel = vessel[ 0 : length - 2 ]
		vessel = tempVessel

	print vessel[ length - 3 ]
	print 'vessel =', vessel
	sWord = s_words( vessel )
	print 'sWord =', sWord

	for beers in range( bottles, 0, -1 ):
		print  beers, container( beers, vessel, sWord ), 'of beer on the wall,', beers, container( beers, vessel, sWord ), 'of beer.' 
		print 'Take one down, pass it around,', beers - 1, container( beers - 1, vessel, sWord ), 'of beer on the wall.\n'

	print 'No more', container( 0, vessel, sWord ), 'of beer on the wall, no more', container( beers, vessel, sWord ), 'of beer,'
	print 'Go to the store, buy some more,', bottles, container( bottles, vessel, sWord ), 'of beer on the wall.'


if __name__ == "__main__":
	main()


```

---

### Post by jimi_hendrix on 2008-08-03
if you know how to stop a console app in C++ from closing like the one in my post, please tell me, because i need to do a line break to keep it from closing and that feels like cheating

---

### Post by jimi_hendrix on 2008-08-03
also when does the next challenge come out?

---

### Post by dwhitney67 on 2008-08-03
> **jimi_hendrix said:**
> 
[PHP]
#include "stdafx.h"
#include <iostream>
#include <stdio.h>

using namespace std;

int _tmain(int argc, _TCHAR* argv[])
{
	int bottles = 99;
	while (bottles >2)
	{
		//prints verses 1-98
		cout << bottles << " bottles of beer on the wall," << endl << bottles << " bottles of beer. Take one down and pass it around," << endl;
		bottles--;
		cout << bottles << " bottles of beer on the wall." << endl << endl;
	}
	//prints the last 3 verses because i was to lazy to 
        //do ifs/else ifs
	cout << "2 bottles of beer on the wall, 2 bottles of beer." << endl << "Take one down and pass it around, 1 bottle of beer on the wall." << endl << endl << "1 bottle of beer on the wall, 1 bottle of beer." << endl << "Take one down and pass it around, no more bottles of beer on the wall." << endl << endl << "No more bottles of beer on the wall, no more bottles of beer." << endl << "Go to the store and buy some more, 99 bottles of beer on the wall."<<endl;
	/*put a line break next to return because i havn't      figured out how to put code to stop it from exiting yet...*/
	return 0;
}
[/PHP]
Hopefully the next challenge will not be revealed until you fix this program.  _tmain() and _TCHAR??  Why are you not using the proper format for the main function.  On both windows and Linux it is:
[PHP]int main( int argc, char **argv )
// or
int main( int argc, char *argv[] )[/PHP]
What you have is a non-portable bastardization created by Gates & Co.

The part about you being "lazy" is also disturbing.  If you want to learn to program, then do it correctly and concisely.  Cutting corners is not the proper way!

---

### Post by drubin on 2008-08-03
> **dwhitney67 said:**
> 
What you have is a non-portable bastardization created by Gates & Co.

The part about you being "lazy" is also disturbing.  If you want to learn to program, then do it correctly and concisely.  Cutting corners is not the proper way!

Ha ha ha.. If you are "lazy" programming is probably not the right option for you.

---

### Post by jimi_hendrix on 2008-08-03
> **dwhitney67 said:**
> Hopefully the next challenge will not be revealed until you fix this program.  _tmain() and _TCHAR??  Why are you not using the proper format for the main function.  On both windows and Linux it is:
[PHP]int main( int argc, char **argv )
// or
int main( int argc, char *argv[] )[/PHP]
What you have is a non-portable bastardization created by Gates & Co.

The part about you being "lazy" is also disturbing.  If you want to learn to program, then do it correctly and concisely.  Cutting corners is not the proper way!

hehe that's what you get for using a microsoft IDE...ill fix that and i will add the loops and edit my post...i still would like to know how i will not need the line break at the end to keep the terminal from closing

---

### Post by drubin on 2008-08-03
> **jimi_hendrix said:**
> hehe that's what you get for using a microsoft IDE...ill fix that and i will add the loops and edit my post...i still would like to know how i will not need the line break at the end to keep the terminal from closing

System("PAUSE"); -> BUT this only works on windows, but clearly that is what you are working on and care about(But these are linux/ubuntu forums...). Maybe some one has a platform independent version?

Or you could just ask for some input at the end. ie a return char would do the trick.

---

### Post by jimi_hendrix on 2008-08-03
good point

and yes i am using windows because most programming books assume you are using it

---

### Post by drubin on 2008-08-03
> **jimi_hendrix said:**
> Most programming books assume you are using it

Time to get better books...

---

### Post by jimi_hendrix on 2008-08-03
heh

the System("PAUSE") didnt work for me so im using a "enter 1 to exit or any other number to continue"

---

### Post by Wybiral on 2008-08-03
> **ghostdog74 said:**
> It don't matter, as long as its consistent. Conventions are made by people. If I want to follow, i will. But if I don't, I will make my own, and be consistent throughout.

As far as your own project consistency, that's true. But the great thing about Python is that 90% of the recognizable 3rd party modules out there (I made that up, but it's based on experience), and 100% of the standard modules follow the [PEP8]("http://www.python.org/dev/peps/pep-0008/") convention. Sure, it doesn't matter if you're just writing your own stuff, but most Python programmers follow the "everything non-trivial should be written as a module" philosophy, instead of writing everything strictly for their own one-time-only use.

Take my site for example, the syntax highlighting module I'm using ([pygments]("http://pygments.org/")) lacked [Clojure]("http://clojure.org/") support, so I just wrote one into it which required me to both copy & paste their code and write my own code along with theirs in some places. If they used tabs and I used spaces, it would have been a mess (I ended up submitting that patch to them, so the next release will support clojure). I also ended up having to extend the PostMarkup module, the reCaptcha module, and have used small snippets from other code if I see an elegant function that does what I need.

BTW, I do use visible white-space and can convert between tabs and space, but it's so much simpler to just dive in, insert X code into Y and have it work, and be consistent... And the PEP8 ensures this, like it or not (I didn't at first). If everyone used 4-space tabs, the Python world would be a better place (and most people do anyway, but sometimes you find a well-written module or snippet that doesn't and then it sucks to work with).

---

### Post by ghostdog74 on 2008-08-03
> **Wybiral said:**
> As far as your own project consistency, that's true. But the great thing about Python is that 90% of the recognizable 3rd party modules out there (I made that up, but it's based on experience), and 100% of the standard modules follow the [PEP8]("http://www.python.org/dev/peps/pep-0008/") convention. Sure, it doesn't matter if you're just writing your own stuff, but most Python programmers follow the "everything non-trivial should be written as a module" philosophy, instead of writing everything strictly for their own one-time-only use.

Take my site for example, the syntax highlighting module I'm using ([pygments]("http://pygments.org/")) lacked [Clojure]("http://clojure.org/") support, so I just wrote one into it which required me to both copy & paste their code and write my own code along with theirs in some places. If they used tabs and I used spaces, it would have been a mess (I ended up submitting that patch to them, so the next release will support clojure). I also ended up having to extend the PostMarkup module, the reCaptcha module, and have used small snippets from other code if I see an elegant function that does what I need.

BTW, I do use visible white-space and can convert between tabs and space, but it's so much simpler to just dive in, insert X code into Y and have it work, and be consistent... And the PEP8 ensures this, like it or not (I didn't at first). If everyone used 4-space tabs, the Python world would be a better place (and most people do anyway, but sometimes you find a well-written module or snippet that doesn't and then it sucks to work with).
i agree with you. If there's a standard, everyone should follow. However, the world would be a better place if the Python interpreter will just stop  running the script if there isn't 4 spaces. I think this will end all  arguments. :)

---

### Post by artoj on 2008-08-03
*It's called C++, it's the only way to fly.*

```

#include <iostream>

class Counter
{
	public:
		Counter() { }
		virtual ~Counter() { }

		virtual void set(int amount) = 0;
		virtual void substract(int amount = 1) = 0;
		virtual int count() const = 0;

};

class BeerCounter : public Counter
{
	public:
		BeerCounter(int initial) { set(initial); }
		~BeerCounter() { }

		void set(int amount) { m_numberOfBeers = amount; }
		void substract(int amount = 1) { m_numberOfBeers -= amount; }
		int count() const { return m_numberOfBeers; }
	
	private:
		int m_numberOfBeers;

};

class Translator
{
	public:
		Translator() { }
		virtual ~Translator() { }

		virtual void translate(Counter* c) = 0;

};

class BeerTranslator : public Translator
{
	public:
		BeerTranslator() { }
		~BeerTranslator() { }

		void translate(Counter* c)
		{
			switch (c->count())
			{
				case 0:
					std::cout << "No more bottles of beer on the wall, ";
					std::cout << "no more bottles of beer." << std::endl;

					std::cout << "Go to the store and buy some more beer, ";
					std::cout << "99 bottles of beer on the wall."
						<< std::endl;
				break;

				case 1:
					std::cout << "1 bottle of beer on the wall, ";
					std::cout << "1 bottle of beer." << std::endl;

					std::cout << "Take one down and pass it around, ";
					std::cout << "no more bottles of beer on the wall"
						<< std::endl;
				break;

				case 2:
					std::cout << "2 bottles of beer on the wall, ";
					std::cout << "2 bottles of beer." << std::endl;

					std::cout << "Take one down and pass it around, ";
					std::cout << "1 more bottle of beer on the wall"
						<< std::endl;
				break;

				default:
					std::cout << c->count() <<
						" bottles of beer on the wall, ";
					std::cout << c->count() <<
						" bottles of beer." << std::endl;

					std::cout << "Take one down and pass it around, ";
					std::cout << c->count() - 1 <<
						" more bottle of beer on the wall" << std::endl;
				break;
			}
		}

};

class Application
{
	public:
		Application() { }
		virtual ~Application() { }

		virtual int exec() = 0;

};

class BeerApplication : public Application
{
	public:
		BeerApplication()
		{
			m_beerCounter = new BeerCounter(99);
			m_beerTranslator = new BeerTranslator();
		}

		~BeerApplication()
		{
			delete m_beerCounter;
			delete m_beerTranslator;
		}

		int exec()
		{
			while (m_beerCounter->count() >= 0)
			{
				m_beerTranslator->translate(m_beerCounter);
				m_beerCounter->substract();
			}

			return 0;
		}

	private:
		BeerCounter* m_beerCounter;
		BeerTranslator* m_beerTranslator;

};

int main(int argc, char* argv[])
{
	BeerApplication app;
	return app.exec();
}

```

---

### Post by Lux Perpetua on 2008-08-03
Edit: sorry, didn't see the part about not commenting on other entries.

---

### Post by dwhitney67 on 2008-08-03
> **jimi_hendrix said:**
> ...i still would like to know how i will not need the line break at the end to keep the terminal from closing
Here are two choices I sometimes use:
[PHP]#include <iostream>

int main()
{
  std::cout << "Press ctrl-d to continue... ";
  char dummy;
  std::cin >> dummy;


  // or

  std::cout << "Press <enter> to continue... ";
  getchar();

  return 0;
}[/PHP]

---

### Post by LaRoza on 2008-08-03
> **jimi_hendrix said:**
> if you know how to stop a console app in C++ from closing like the one in my post, please tell me, because i need to do a line break to keep it from closing and that feels like cheating

The program stays open while it is running. If you are running it from a terminal, that is good. If you are double clicking it, it is bad. The solution is don't double click! 

Using such getchar() things and pausing it just leads to wasted energy when it is run from the terminal, which it should be.

---

### Post by jimi_hendrix on 2008-08-03
i really wish vista had a terminal

---

### Post by Kadrus on 2008-08-03
It has command prompt,terminal is only under Unix oses,you should do your programming under Linux ;)

---

### Post by LaRoza on 2008-08-03
> **jimi_hendrix said:**
> i really wish vista had a terminal

Press start menu, type "cmd" press enter.

---

### Post by jimi_hendrix on 2008-08-03
i know but its not nearly as good ive never have had to use it

---

### Post by Lux Perpetua on 2008-08-03
Here's my updated code: ```
import Char(toUpper)

main = putStrLn (e 99)

e :: Int -> String
e x = ((\(c : cs) -> (toUpper c : cs))(d x)) ++ ", " 
      ++ (c x) ++ ".\n" 
      ++ if x == 0
         then "Go to the store and buy some more, " ++ (d 99) ++ "."
         else "Take one down and pass it around, " ++ (d (x-1)) ++ ".\n\n"
                  ++ (e (x-1))

d :: Int -> String
d x = (c x) ++ " on the wall"

c :: Int -> String
c x = (if x == 0 then "no more" else show x)
      ++ " bottle" ++
      (if x == 1 then "" else "s")
      ++ " of beer"
```I don't promise that it won't be updated again, since I'm still learning the ins and outs of Haskell. 

I chose this design in order to minimize the amount of repeated text in the source code. Every major word or phrase (e. g., "bottle(s)", "of beer", etc.) only appears once.

---

### Post by tafoo85 on 2008-08-03
```

#include <iostream>
using namespace std;

void printBottles(int);

int main(int argc, char** argv)
{
        int beer = 99;

        printBottles(beer);
        return 0;

}

void printBottles(int beer)
{
        switch(beer)
        {
      case 0:
          {
           cout <<  "No bottles of beer on the wall, no bottles of beer.\nGo to the store and buy some more. 99 bottles of beer on the wall.\n" << endl;
       return;
          }

          case 1:
          {
          cout << beer << " bottle of beer on the wall, " << beer << " bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n" << endl;
          printBottles(beer - 1);
          }
          break;

          case 2:
          {
         cout << beer << " bottles of beer on the wall, " << beer << " bottles of beer.\nTake one down and pass it around, " 
                      << beer - 1 << " bottle of beer on the wall.\n" << endl;
         printBottles(beer - 1);
          }
          break;
          default:
          {
                cout << beer << " bottles of beer on the wall, " << beer << " bottles of beer.\nTake one down and pass it around, "
                         << beer - 1 << " bottles of beer on the wall.\n" << endl;
                printBottles(beer - 1);  
          }
          break;
        };
}

```

First post.  It's been a long time since I've done any C++.

---

### Post by AaronMT on 2008-08-03
Hello,

Here is my submission in **Python**. I am not a new programmer, but I am a fairly new Python programmer. I thought I would keep this task fairly basic by letting the ```
range()
``` function take care of most of the work for me.

[php]#!/usr/bin/env python
#
#       99_Bottles.py
#       
#       Copyright 2008 Aaron <aaron@aaron-laptop>
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       

def drink_me(n):
	for i in range(n,0,-1):
		if i > 1:
			print i, "bottles of beer on the wall", i, " bottles of beer.\nTake one down, pass it around", (i-1), "bottles of beer on the wall.\n"
		else: 
			print "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more",n,"bottles of beer on the wall.\n"
    return 0
def main():
	drink_me(99)
	return 0

if __name__ == '__main__': main()
[/php]

---

### Post by geogur on 2008-08-03
can you do this again this is so cool for me to read all your ideas . i am self taught so seeing your answers are interseting . there really are more than one way to do this .

---

### Post by TheNatealator on 2008-08-03
I decided to go with this semi-recursive method, since the iterative method has been done before. I have some repeated code in there, which bothers me, but here it is anyways. Maybe I'll try another language next.

[PHP]#!usr/bin/perl
package Beer;
use strict;

# Can start with any number of beers, default is 99.
our $numBeers = ($ARGV[0] && $ARGV[0] =~ m|\d+|) ? $ARGV[0] : 99;

&sing($numBeers);
&getMore($numBeers);

# Print the first line of each verse.
sub sing {
	my $Beer = my $beer = shift; #Capitalized and uncapitalized version
	my $s = ($beer == 1) ? "" : "s";
	$Beer =~ s|n|N|;
	print "$Beer bottle$s of beer on the wall, $beer bottle$s of beer.\n";
	&takeOne(--$beer) if ($beer =~ m|\d+|);	
}

# Print the second line of each verse (except the last).
sub takeOne {
	my $beer = shift;
	my $s = ($beer == 1) ? "" : "s";
	$beer = ($beer == 0) ? "no more" : $beer;
	print "Take one down and pass it around, $beer bottle$s of beer on the wall.\n\n";
	&sing($beer);
}

# The last line.
sub getMore {
	my $s = ((my $beer = shift) == 1) ? "" : "s";
	print "Go to the store and buy some more, $beer bottle$s of beer on the wall.\n";
}[/PHP]

---

### Post by mvoncken on 2008-08-03
@aktiwers : I hereby give you my personal most-improved award ;).
I can read and understand your code now.

> **CptPicard said:**
> May I suggest that you really choose the winner based on one being a good n00b <SNIP>
Yea, experienced people should make it clear in their post that they are not a new

this thread is getting too long to read :( 
Someone else said experienced people should demonstrate a specific concept/pattern and i totally agree with that too. 
A bonus award for an expert would be fine though.

---

### Post by happysmileman on 2008-08-03
> **Titan8990 said:**
> Alright, a co-worker made an attempt at writing it in the fewest lines as possible. Here is it is:

[PHP]#include <stdio.h>
int main(){int x;for(x=99;x>=1;printf("%i bottle%s of beer on the wall, %i bottle%s of beer, take one down, pass it around, %s%i%s bottle%s of beer on the wall\n", x, x > 1 ? "s" : "", x, x > 1 ? "s" : "", x==1 ? "n" : "", x-1, x == 1 ? " more": "", x==2 ? "" : "s"),x--); 
return 0;}[/PHP]

```
#include"ios"
main(){char*f=" on the wall",a[]=" bottles",*d=" of beer";for(int i=99;i;){printf("%d%s%s%s, %d%s%s.\n",i,a,d,f,i,a,d);if(--i<2)a[7]=0;i?printf("Take one down and pass it around, %d%s%s%s.\n\n",i,a,d,f):printf("Go to the store and buy some more, 99%ss%s%s.",a,d,f);}}
```

That one is shorter but only because I took some shortcuts (main() instead of int main(), #include"ios", no whitespace), overall yours is shorter >:3

---

### Post by conehead77 on 2008-08-03
> **Lux Perpetua said:**
> Here's my updated code: ```
import Char(toUpper)

main = putStrLn (e 99)

e :: Int -> String
e x = ((\(c : cs) -> (toUpper c : cs))(d x)) ++ ", " 
      ++ (c x) ++ ".\n" 
      ++ if x == 0
         then "Go to the store and buy some more, " ++ (d 99) ++ "."
         else "Take one down and pass it around, " ++ (d (x-1)) ++ ".\n\n"
                  ++ (e (x-1))

d :: Int -> String
d x = (c x) ++ " on the wall"

c :: Int -> String
c x = (if x == 0 then "no more" else show x)
      ++ " bottle" ++
      (if x == 1 then "" else "s")
      ++ " of beer"
```I don't promise that it won't be updated again, since I'm still learning the ins and outs of Haskell. 

I chose this design in order to minimize the amount of repeated text in the source code. Every major word or phrase (e. g., "bottle(s)", "of beer", etc.) only appears once.

I think pattern matching and/or guards are more "haskellish" than if..then, so i did something like you but with slightly changed syntax (i also tried to give the functions meaningful names :) ) :

```
main = putStr $ text 99

text :: Int -> String
text 0 = "N" ++ tail (item 0) ++ location ',' ++ item 0 ++ ".\n" ++
         "Go to the store and buy some more, " ++ item 99 ++ location '.'
text x = item x ++ location ',' ++ item x ++ ".\n" ++
         "Take one down and pass it around, " ++ item (x-1) ++ location '.' ++ "\n" ++
         text (x-1)

item :: Int -> String
item x 
    | x == 0 = "no more" ++ b ++ "s" ++ o
    | x == 1 = "1" ++ b ++ o
    | otherwise = show(x) ++ b ++ "s" ++ o where
        b = " bottle"
        o = " of beer"

location :: Char -> String
location ' ' = " on the wall"
location '.' = location ' ' ++ ".\n"
location ',' = location ' ' ++ ", "
```

---

### Post by LaRoza on 2008-08-03
> **mvoncken said:**
> 
Yea, experienced people should make it clear in their post that they are not a new

It won't be hard to figure out for me. This chain of challenges are for people new to programming, and it isn't hard to determine who is new. 

> 

this thread is getting too long to read :( 

I have to soon test all of the entries...

---

### Post by LaRoza on 2008-08-03
**On this Tuesday, I will close this thread and make a new one for the new challenge. After looking at all the entries, I will choose a winner (probably) and reopen it for discussion. I just want to be able to look it over without modification.**

---

### Post by mssever on 2008-08-03
> **LaRoza said:**
> I have to soon test all of the entries...
Have fun... :)

---

### Post by LaRoza on 2008-08-03
> **mssever said:**
> Have fun... :)

Oh? A volunteer to help :-)

---

### Post by jimi_hendrix on 2008-08-03
> **LaRoza said:**
> It won't be hard to figure out for me. This chain of challenges are for people new to programming, and it isn't hard to determine who is new. 


I have to soon test all of the entries...

hopefully you have a windows partition to test mine in because i think its not going to be linux compatable (does that disqualify me?)

---

### Post by LaRoza on 2008-08-03
> **jimi_hendrix said:**
> hopefully you have a windows partition to test mine in because i think its not going to be linux compatable (does that disqualify me?)

The conditions for the competition said in "in any free language".

Looking at the code, it doesn't look at all standard, and I don't know of a free compiler for that language. If you can tell me of one if one exists, I'll be able to test it.

---

### Post by jimi_hendrix on 2008-08-03
microsoft visual C++ 2008 is what i used (the only thing they do right is their IDE's)

---

### Post by jimi_hendrix on 2008-08-03
it takes a while to download though

---

### Post by mssever on 2008-08-03
> **jimi_hendrix said:**
> it takes a while to download though
Can you even download it legally, or are you talking about piracy? (I have no use for Windows-only setups anyway, legal or otherwise, free or non-free.)

---

### Post by jimi_hendrix on 2008-08-03
yes its legal and free (at least the express adition is)

---

### Post by DaymItzJack on 2008-08-03
[php]def sing(bottles = 99):
    if bottles == 0:
        print 'No more bottles of beer on the wall, no more bottles of beer.'
        print 'Go to the store and buy some more, 99 bottles of beer on the wall.'
        return 
    
    
    print '%i bottle%s of beer on the wall, %i bottle%s of beer.' % (bottles, f(bottles), bottles, f(bottles))
    print 'Take one down and pass it around, %i bottle%s of beer on the wall.' % (bottles - 1, f(bottles - 1))
    print 
    
    sing(bottles - 1)

f = lambda x: x > 1 and 's' or ''
sing()[/php]

---

### Post by tjmage1 on 2008-08-03
UPDATE: This code is outdated, there's a bug in it. See my entry further down for my (hopefully final code.

Here's my python code. I'm a beginner programmer, but I'm best at python. My focus was on clean and easy code.
[PHP]
#Prints 99 Bottles of Beer Song
beers = 99
while beers > 2:
	print beers, " bottles of beer on the wall, ", beers, "bottles of beer."
	beers = beers-1
	print "Take one down and pass it around, ", beers, "on the wall."
	print ""
print "1 bottle of beer on the wall, 1 bottle of beer."
print "Take one down and pass it around, no more bottles of beer on the wall."
print ""
print "No more bottles of beer on the wall, no more bottles of beer."
print "Go to the store and buy some more, 99 bottles of beer on the wall."
[/PHP]

I had an awesome idea, then I did it. Why only print the lyrics? Why not get your PC to sing 'em too??!!
That's just what I did. I installed Festival and created a text file containing all the lyrics.

[https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech) is how. I used a 16 kilohertz American speaker. 
I've attached my text file, named beer_song.txt. Get it and put it in a directory of your choice, just remember where.

Open a terminal and cd to your directory.
Type: festival
A festival prompt will come up. Type: (tts "beer_song.txt" nil)

Assuming beer_song is in your current directory, you computer will starting singing (well, talking more like) the song to you!!!

Yippie!

Please let me know what you think, and any suggestions.
My python code is my entry, to be clear. The singing is just a nice extra.

---

### Post by LaRoza on 2008-08-04
> **jimi_hendrix said:**
> microsoft visual C++ 2008 is what i used (the only thing they do right is their IDE's)

> **jimi_hendrix said:**
> yes its legal and free (at least the express adition is)

Sorry. That isn't free. By free, I meant really free, not they release a crippled version to get students hooked and locked in.

---

### Post by emobrad on 2008-08-04
```
#include <iostream>
using namespace std;

int main()
{
	int bottles = 99;
	do
	{
		if (bottles == 2)
		{
			cout << bottles << " bottles of beer on the wall. " << bottles << " bottles of beer!" << endl;
			cout << "You take one down, pass it around. " << bottles - 1 << " bottle of beer on the wall" << endl;
			cout << " " << endl;
		}
		else
		{
			cout << bottles << " bottles of beer on the wall. " << bottles << " bottles of beer!" << endl;
			cout << "You take one down, pass it around. " << bottles - 1 << " bottles of beer on the wall" << endl;
			cout << " " << endl;
		}
			bottles --;
	}
	while (bottles >= 2);
	
	cout << "1 bottle of beer on the wall, one bottle of beer!" << endl;
	cout << "You take one down, pass it around, no more bottles of beer on the wall." << endl;
	cout << " " << endl;
	
	cout << "No more bottles of beer on the wall. No more bottles of beer!" << endl;
	cout << "Go to the store, buy some more. 99 bottles of beer on the wall. (And you may also want to look into AA)" << endl;
	
	return 0;
}
```


A little longer than I was going to write it at first, but I realized I had to use good grammar and bleh.

---

### Post by Xealot on 2008-08-04
> **rubinboy said:**
> Ha ha ha.. If you are "lazy" programming is probably not the right option for you.


Are you sure? I often find myself writing an app that automates a process I would otherwise do a lot. Isnt that lazy? :)

---

### Post by lordhaworth on 2008-08-04
Just for my future reference how often will these challenges be being set? I want to try and keep up to date with these, but would rather not have to be constantly checking!

Cheers

---

### Post by drubin on 2008-08-04
> **jimi_hendrix said:**
> microsoft visual C++ 2008 is what i used (the only thing they do right is their IDE's)

I disagree..... Do you know/understand the process of compiling an application, or do you just click the big green button?

---

### Post by Wybiral on 2008-08-04
You know, LaRoza, there is a [better platform]("http://www.challenge-you.com") for hosting challenges... Where the sourcecode is actually highlighted (not just for PHP) and users can vote on each-others solutions :)

---

### Post by Vishal Agarwal on 2008-08-04
I don't know it will solve the purpose or not, But it is working with php cli.
PHP Code:
[PHP]<?php
/*
 * Created on Aug 4, 2008
 *
 * To change the template for this generated file go to
 * Window - Preferences - PHPeclipse - PHP - Code Templates
 */
 for ($Count=99;$Count>=2;$Count--)
 	{
 		echo "$Count bottles of beer on the wall, $Count bottles of beer. \n";
// 		echo "<br>";
		echo "Take one down and pass it around, ".($Count-1)." bottles of beer on the wall.\n\n";
//		echo "<br><br>";
 	}
 		echo "1 bottles of beer on the wall, 1 bottles of beer. \n";
// 		echo "<br>";
		echo "Take one down and pass it around, no more bottles of beer on the wall.\n\n";
//		echo "<br><br>";
?>[/PHP]

---

### Post by drubin on 2008-08-04
> **Wybiral said:**
> You know, LaRoza, there is a [better platform]("http://www.challenge-you.com") for hosting challenges... Where the sourcecode is actually highlighted (not just for PHP) and users can vote on each-others solutions :)

Would be cool :) But does it have email reminders on updates and stuff?

That is what I like about these forums is that every time some one makes a change/comments i get a reminder to come back and check things out. Makes the challenge more viral.

---

### Post by LaRoza on 2008-08-04
> **Wybiral said:**
> You know, LaRoza, there is a [better platform]("http://www.challenge-you.com") for hosting challenges... Where the sourcecode is actually highlighted (not just for PHP) and users can vote on each-others solutions :)

"better" is relative. This entire forum is redundant. Wikipedia, google, documentation, man pages, various wiki's and mailing lists are often "better". ;)

I started the [http://ubuntuprogramming.wikidot.com](http://ubuntuprogramming.wikidot.com) wiki, yet it has barely grown, and the same old questions are asked on this forum.

---

### Post by Kadrus on 2008-08-04
> **Wybiral said:**
> You know, LaRoza, there is a [better platform]("http://www.challenge-you.com") for hosting challenges... Where the sourcecode is actually highlighted (not just for PHP) and users can vote on each-others solutions :)

I agree with Wybiral and maybe you should add a bulletin board to your website for users discussion.

EDIT:
> "better" is relative. This entire forum is redundant. Wikipedia, google, documentation, man pages, various wiki's and mailing lists are often "better"
I think Challenge-you is great for this type of situations,you can create a thread that redirects to challenge-you with the challenge,well that's my opinion,I'm sure many disagree with me.

---

### Post by LaRoza on 2008-08-04
> **Kadrus said:**
> 
EDIT:

I think Challenge-you is great for this type of situations,you can create a thread that redirects to challenge-you with the challenge,well that's my opinion,I'm sure many disagree with me.

There are many programming challenge sites and are linked to in sticky: [http://ubuntuforums.org/showthread.php?t=783387](http://ubuntuforums.org/showthread.php?t=783387)

If anyone wants to contribute to such sites, or link to them, that is fine.

---

### Post by Wybiral on 2008-08-04
Well, perhaps then, instead of one individual picking the winner, we open a poll when the challenge is over to let the entire community decide?

But seriously, PHP-only syntax highlighting is depressing...

We, at least, need a [ code = python ] on this forum (or lisp, haskell, etc)

---

### Post by schauerlich on 2008-08-04
> **Wybiral said:**
> We, at least, need a [ code = python ] on this forum (or lisp, haskell, etc)

The php highlighting works pretty well for other languages. But it would be good to have language specific highlighting so as to catch each language's nuances. Python would probably be the top priority to develop.

---

### Post by LaRoza on 2008-08-04
> **Wybiral said:**
> Well, perhaps then, instead of one individual picking the winner, we open a poll when the challenge is over to let the entire community decide?

But seriously, PHP-only syntax highlighting is depressing...

We, at least, need a [ code = python ] on this forum (or lisp, haskell, etc)

I was thinking of having no particular winners, just suggestions and praise when needed.

We could have people host their code remotely on various pastebins, but that wouldn't be required.

---

### Post by nvteighen on 2008-08-04
> **LaRoza said:**
> I was thinking of having no particular winners, just suggestions and praise when needed.

We could have people host their code remotely on various pastebins, but that wouldn't be required.
I'm sure I'm the winner. My code is a masterpiece. :D

---

### Post by Kadrus on 2008-08-04
> But seriously, PHP-only syntax highlighting is depressing...
The admins should add [GeSHi]("http://qbnz.com/highlighter/") to the forum,so we can highlight any language we want.

---

### Post by LaRoza on 2008-08-04
> **nvteighen said:**
> I'm sure I'm the winner. My code is a masterpiece. :D

No. Me. I have a 999 bottles of beer echoed line by line. That took forever to type.

> **Kadrus said:**
> The admins should add [GeSHi]("http://qbnz.com/highlighter/") to the forum,so we can highlight any language we want.

Does it work with vBulletin? This site is very large and not something they can fiddle with.

---

### Post by Kadrus on 2008-08-04
Well it works for PunBB,and I think if the admins mod the VBulletin code a bit,they can get it to work.
I found this googling:[http://www.vbulletin.org/forum/showthread.php?t=93071](http://www.vbulletin.org/forum/showthread.php?t=93071)

---

### Post by LaRoza on 2008-08-04
> **Kadrus said:**
> Well it works for PunBB,and I think if the admins mod the VBulletin code a bit,they can get it to work.
I found this googling:[http://www.vbulletin.org/forum/showthread.php?t=93071](http://www.vbulletin.org/forum/showthread.php?t=93071)

I found that also:
> 
Version: 3.5.0 RC1	Rating:  (8 votes - 4.75 average) 
Released: 28 Jul 2005	Last Update: Never
Obviously, this version of vBulletin is different and considering the plugins that didn't work for this upgrade, I doubt that one will.

Yes, if the mod it they probably could, however, they'd give up secure updates (things would break), uptime and time.

---

### Post by Kadrus on 2008-08-04
Ah well,I suppose the php tags will do fine for the moment:p

---

### Post by jimi_hendrix on 2008-08-04
> **LaRoza said:**
> Sorry. That isn't free. By free, I meant really free, not they release a crippled version to get students hooked and locked in.

so basically i cant do any of these challenges in my microsoft IDE?

---

### Post by LaRoza on 2008-08-04
> **jimi_hendrix said:**
> so basically i cant do any of these challenges in my microsoft IDE?

It doesn't matter what editor you use, just as long as you use a standardised and free language.

---

### Post by Vishal Agarwal on 2008-08-04
Dear LaRoza,

What is the time line for submitting the code and how the winner will be informed.

---

### Post by jimi_hendrix on 2008-08-04
[PHP]#include "stdafx.h"
#include <iostream>
#include <stdio.h>
int have_a_drink(int Bottles);


using namespace std;

int main(int argc, char** argv)
{
    int bottles = 99;
    have_a_drink(bottles);
    /*put a line break next to return because i havn't      figured out how to put code to stop it from exiting yet...*/
    return 0;
}  

int have_a_drink(int Bottles)
{
	while (Bottles >2)
    {
        //prints verses 1-98
        cout << Bottles << " bottles of beer on the wall, " << endl << Bottles << " bottles of beer. Take one down and pass it around, " << endl;
        Bottles--;
        cout << Bottles << " bottles of beer on the wall." << endl << endl;
    }
   		
   	if (Bottles == 2)
   	{
   		cout << Bottles << " bottles of beer on the wall, " << Bottles << " bottles of beer." << endl;
   		Bottles--; 
   		cout << "Take one down and pass it around, " << Bottles << " bottle of beer on the wall." << endl << endl;
	}
	
	if (Bottles == 1)
	{
		cout << "1 bottle of beer on the wall, 1 bottle of beer." << endl << "Take one down and pass it around, no more bottles of beer on the wall." << endl << endl;
		Bottles--;
	}
	
	if (Bottles == 0)
	{
		cout << "No more bottles of beer on the wall, no more bottles of beer." << endl << "Go to the store and buy some more, 99 bottles of beer on the wall."<<endl;
	}
	return Bottles;
}
[/PHP]

new version of my program that uses a function and some if loops at the end.

i tried to compile this in geany  but i get 

```
08:10:26: Process failed (Failed to execute child process (No such file or directory))
```

in messeges

---

### Post by hsweet on 2008-08-04
This is not mine, so I am not eligible for the contest, but there has been a running perl game trying to write as short (and hard to understand) version as possible.  Here is the winner

```
$n=pop||99;sub b{"$n bottle@{[$n!=1&&s=>]} of beer"}print$b=b,$w=' on 
+the wall'
,", $b!\nTake one down, pass it around,\n",b($n--),"$w!\n\n"while$n
```

The rest of this thread is at 
[http://perlmonks.org/?node=99+bottles](http://perlmonks.org/?node=99+bottles)

---

### Post by LaRoza on 2008-08-04
> **Vishal Agarwal said:**
> Dear LaRoza,

What is the time line for submitting the code and how the winner will be informed.

Well, I did announce it earlier (but it could have been easily missed) [http://ubuntuforums.org/showpost.php?p=5518375&postcount=145](http://ubuntuforums.org/showpost.php?p=5518375&postcount=145)

I will post the results on this thread, but I will have started another thread before doing it.

---

### Post by TreeFinger on 2008-08-04
[php]
class wall_of_beer:
	"""
	This object is meant to represent a wall of beer.
	Every wall of beer has an amount of beers it currently contains.
	When the wall runs out of beer. Someone goes to the store and buys some more!
	"""
	def __init__(self, beers):
		"""
		Constructor accepts one parameter, beers. Which is how many beers the user
		has on his wall of beers. This constructor calls the __print_line method
		until there are no beers left. When no beers are left, __print_end method
		is called to tell the user to remind the user to head to the store!
		"""
		self.amount = beers

		while self.amount > 0:	# Until no beers are left
			self.__print_line()
			self.amount -= 1

		self.__print_end(beers)

	def __print_line(self):
		"""
		This method prints the next lines of the song depending on the value of
		self.amount . 
		"""
		if self.amount > 1:
			print "%d bottles of beer on the wall, %d bottles of beer." % (self.amount, self.amount)
			if self.amount == 2:
				print "Take one down and pass it around, %d bottle of beer on the wall.\n" % (self.amount - 1)
			else:
				print "Take one down and pass it around, %d bottles of beer on the wall.\n" % (self.amount - 1)

		else:
			print "%d bottle of beer on the wall, %d bottle of beer." % (self.amount, self.amount)
			print "Take one down and pass it around, no more bottles of beer on the wall.\n"

	def __print_end(self, b):
		"""
		Prints the final line of the song.
		"""
		print "No more bottles of beer on the wall, no more bottles of beer."
		print "Go to the store and buy some more, %d bottles of beer on the wall.\n" % b



wall = wall_of_beer(99)
[/php]

---

### Post by tjmage1 on 2008-08-04
This is my new code. I don't think this has any bugs in it, but if you want to take points off for having a bug in the first one, I understand.
[php]
#Prints 99 Bottles of Beer Song
beers = 99
while beers > 2:
	print beers, "bottles of beer on the wall, ", beers, "bottles of beer."
	beers = beers-1
	print "Take one down and pass it around, ", beers, "bottles of beer on the wall."
	print ""
print "2 bottles of beer on the wall, 2 bottles of beer."
print "Take one down and pass it around, 1 bottle of beer on the wall."
print ""
print "1 bottle of beer on the wall, 1 bottle of beer."
print "Take one down and pass it around, no more bottles of beer on the wall."
print ""
print "No more bottles of beer on the wall, no more bottles of beer."
print "Go to the store and buy some more, 99 bottles of beer on the wall."
[/php]

I try to keep it basic; when some people see a problem, they think, let's use regular expressions. Then they have 2 problems.

My singing computer still works fine, that wasn't changed.

BTW, for anyone who was wondering, I was trying to program a version of this for my TI-83 calc, that's how I discovered the bug.

---

### Post by drubin on 2008-08-04
> **LaRoza said:**
> Well, I did announce it earlier (but it could have been easily missed) [http://ubuntuforums.org/showpost.php?p=5518375&postcount=145](http://ubuntuforums.org/showpost.php?p=5518375&postcount=145)

I will post the results on this thread, but I will have started another thread before doing it.

I think we need to have a minimum amount of time  before posting a new one, as to allow people to look  at the winning solution see how theirs differed and how to improve appon theirs for the next one :)

Also to give LaRoza a break... :popcorn:

---

### Post by MONODA on 2008-08-04
i am so proud of myself :P :

[PHP]#!/usr/bin/python

bottlecount = 99
while bottlecount >= 0:
	if bottlecount > 2:
		print "%d bottles of beer on the wall, %d bottles of beer. \nTake one down and pass it around, %d bottles of beer on the wall." % (bottlecount, bottlecount, bottlecount - 1)
		bottlecount -= 1
	elif bottlecount == 2:
		print "%d bottles of beer on the wall, %d bottles of beer. \nTake one down and pass it around, %d bottle of beer on the wall." % (bottlecount, bottlecount, bottlecount - 1)
		bottlecount -= 1
	elif bottlecount == 1:
		print "%d bottle of beer on the wall, %d bottle of beer. \nTake one down and pass it around, no more bottles of beer on the wall." % (bottlecount, bottlecount)
		bottlecount -= 1
	else:
		print "No more bottles of beer on the wall, no more bottles of beer. \nGo to the store and buy some more, 99 bottles of beer on the wall."
		break
[/PHP]
EDIT: thanks a lot for this LaRoza, I have been looking for something like this.
EDIT2: W00t! 700 posts! :P

---

### Post by Titan8990 on 2008-08-04
I'm not 100% but I don't think you need to import sys to use sys.exit. I believe that is something that is always available. Also, I don't think it is needed here at all as I have mostly seen it used in error catching.

---

### Post by MONODA on 2008-08-04
i am pretty sure the way i have done it is correct since I tried it without importing sys and it failed and if i dont have sys.exit() at the end it continiues to loop.

---

### Post by mssever on 2008-08-04
> **MONODA said:**
> i am pretty sure the way i have done it is correct since I tried it without importing sys and it failed and if i dont have sys.exit() at the end it continiues to loop.
sys.exit() will fail if you don't import sys. However, in your case, you could also use the break statement, which would be a little more idiomatic.

---

### Post by MONODA on 2008-08-04
> sys.exit() will fail if you don't import sys. However, in your case, you could also use the break statement, which would be a little more idiomatic.
ahh yes i forgot about the break statement, im just starting out with python and progamming as a whole.

---

### Post by DaymItzJack on 2008-08-04
> **MONODA said:**
> i am so proud of myself :P :

[PHP]#!/usr/bin/python

 .. snip ..
[/PHP]
EDIT: thanks a lot for this LaRoza, I have been looking for something like this.
EDIT2: W00t! 700 posts! :P

Instead of reassigning your variables in 3 different locations, do it only once after the `if` statement. You could also instead of using 'less_bottlecount' use 'bottlecount - 1' in anyplace that you would use 'less_bottlecount'.


```
For i = 99 To 1 Step -1
   MsgBox i & " bottles of beer on the wall, " & i & " bottles of beer."
   MsgBox "Take one down and pass it around, " & i - 1 & " bottles of beer on the wall."
Next

MsgBox "No more bottles of beer on the wall, no more bottles of beer."
MsgBox "Go to the store and buy some more, 99 bottles of beer on the wall."
```

Is this an anti-VBScript forum? :) (this is a joke, that's why I didn't bother with the 's' thing)

---

### Post by MONODA on 2008-08-04
if i assign my bottlecount variable after the while statement it will fail. thanks for the other tip

---

### Post by jimi_hendrix on 2008-08-04
> **tjmage1 said:**
> 

BTW, for anyone who was wondering, I was trying to program a version of this for my TI-83 calc, that's how I discovered the bug.

how do i program one of those

---

### Post by linkmaster03 on 2008-08-04
EDIT: SCROLL DOWN FOR MY FINAL VERSION

Just beginning to learn Python. My first Python program.

[php]#!/usr/bin/python
#  beer.py
# Beer Singer by LinkMaster03 in Python
b,p,a=99,"bottles",""
while b>0:
    print b,p,"of beer on the wall,",b,p,"of beer."
    if b==1: p,b,a="more bottles","n","o"
    elif b==2: p="bottle"; b=b-1
    else: b=b-1
    print "Take one down and pass it around, %s%s %s of beer on the wall.\n" % (b,a,p)
    if a=="o": break
p=b.upper()+a+" "+p
print p,"of beer on the wall,",p.lower(),"of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall."[/php]

I'm really proud of how compact this turned out for my first script! I love Python, I'm definitely going to keep learning. I'll be waiting for the next challenge.

---

### Post by cmay on 2008-08-04
this is the solution i found to make sure that the s in bottles
only shows in the lines whit more than one bootle.
also as i am a hobby songwriter i would always split things like songs into chorus intro break outro and so on.

```

/* 99 bottles on the wall song printed to terminal*/ 
#include <stdio.h>
#include <stdlib.h>

void beer_song_intro();
void beer_song();
void beer_song_outro();

int main(int argc, char** argv)
{

beer_song_intro();
beer_song();
beer_song_outro();
exit(0);

}

void beer_song_intro(){
printf("the beer song\n");
printf("press return to continue\n");
getchar();
system("clear");
}

void beer_song(){

int beer;
char s; 

for(beer=99;beer >=1 ;beer--){
// test to see if the s should be included in bottle
if(beer == 1)
s=' ';
else
s='s';
//unless there are more than one bottle it does include the s
printf("%d bottle%c of beer on the wall,\n",beer,s);
printf("%d bottle%c of beer.\n",beer,s);
printf("Take one down and pass it around,\n");
printf("%d bottle%c of beer on the wall.\n",beer,s);

}
// end of beer_song main lyrics
}

void beer_song_outro(){

printf("No more bottles of beer on the wall,\n");
printf("no more bottles of beer.\n");
printf("Go to the store and buy some more,\n");
printf("99 bottles of beer on the wall.\n");

}

```

---

### Post by LaRoza on 2008-08-04
> **DaymItzJack said:**
> 
Is this an anti-VBScript forum? :) (this is a joke, that's why I didn't bother with the 's' thing)
It is a Windows language, but I'll try to use Windows and test it, although as you said it doesn't do the "s", which is rather important.

---

### Post by linkmaster03 on 2008-08-04
EDITL SCROLL DOWN FOR MY FINAL VERSION

I optimized my script to remove a line. I also added comments. 9 lines now.

Minimal:

[php]b,p,a=99,"bottles",""
while b!="n":
    print b,p,"of beer on the wall,",b,p,"of beer."
    if b==1: p,b,a="more bottles","n","o"
    elif b==2: p="bottle"; b=b-1
    else: b=b-1
    print "Take one down and pass it around, %s%s %s of beer on the wall.\n" % (b,a,p)
p=b.upper()+a+" "+p
print p,"of beer on the wall,",p.lower(),"of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall."[/php]

Commented:

[php]#!/usr/bin/python
#  beer.py
# Beer Singer by LinkMaster03 in Python
b,p,a=99,"bottles","" #Set b, bottle count. p, the english bottle reference. Declare a for later.
while b!="n": #While b is a number, and it will be until b==1, do the following:
    print b,p,"of beer on the wall,",b,p,"of beer." #Tell how many bottles are on the wall
    if b==1: p,b,a="more bottles","n","o" #If you only have 1 bottle left, change the variables to show there are "no more bottles"
    elif b==2: p="bottle"; b=b-1 #But, if you have 2 bottles left, unpluralize 'bottles' and take away another bottle
    else: b=b-1 #And if you have more than 2 bottles, just take away a bottle
    print "Take one down and pass it around, %s%s %s of beer on the wall.\n" % (b,a,p) #Say that one was passed around, and how many are remaining on the wall
p=b.upper()+a+" "+p #Capitalize the 'n' and combine it all so p=="No more bottles"
print p,"of beer on the wall,",p.lower(),"of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall." #Tell them to head to the store. p.lower() decapitalizes 'No more bottles'[/php]

---

### Post by wilsonmuse on 2008-08-04
99 Beers on the Wall in Python

[PHP]
#!/usr/bin/env python

# 99 Bottles of Beer on the Wall

i = 99

while i > -1: # Loop through bottles until we get to 0
    if i == 0:
        print "Take one down and pass it around, no more bottles of beer on the wall."
        print
        print "No more bottles of beer on the wall, no more bottles of beer."
        print "Go to the store and buy some more, 99 bottles of beer on the wall."
    
    elif i == 1:
        print "Take one down and pass it around, 1 bottle of beer on the wall."
        print
        print "1 bottle of beer on the wall, 1 bottle of beer."
    
    elif i == 99:
        print "99 bottles of beer on the wall, 99 bottles of beer."
    
    else:
        print "Take one down and pass it around, " + str(i) + " bottles of beer on the wall."
        print
        print "" + str(i) + " bottles of beer on the wall, " + str(i) + " bottles of beer."
    
    i -= 1 # Subtract 1 beer *gulp*
[/PHP]

---

### Post by linkmaster03 on 2008-08-04
Last revision. I promise. :)

[php]#!/usr/bin/python
#  beer.py
# Beer Singer by LinkMaster03 in Python
b,p,w,a=99,"bottles","of beer on the wall",""
while b!="n":
    print b,p,w+",",b,p,"of beer."
    if b==1: p,b,a="more bottles","n","o"
    elif b==2: p="bottle"; b=b-1
    else: b=b-1
    print "Take one down and pass it around, %s%s %s %s.\n" % (b,a,p,w)
print b.upper()+a,p,w+",",b+a,p,"of beer.\nGo to the store and buy some more, 99 bottles",w+"."[/php]

---

### Post by DaymItzJack on 2008-08-04
> **MONODA said:**
> if i assign my bottlecount variable after the while statement it will fail. thanks for the other tip

I said after your 'if' statement.
Like so:
```
#!/usr/bin/python

bottlecount = 99
while bottlecount >= 0:
    if bottlecount > 2:
        print "..." % (bottlecount, bottlecount, bottlecount - 1)
                        #bottlecount -= 1    you can remove this
    elif bottlecount == 2:
        print "..." % (bottlecount, bottlecount, bottlecount - 1)
                        #bottlecount -= 1    you can remove this
    elif bottlecount == 1:
        print "..." % (bottlecount, bottlecount)
                        #bottlecount -= 1    you can remove this
    else:
        print "..."
        break
    bottlecount -= 1
```

> **LaRoza said:**
> It is a Windows language, but I'll try to use Windows and test it, although as you said it doesn't do the "s", which is rather important.
I already posted a Python version, that was just a joke and I'm advanced enough to be able to do this in my sleep anyways.

---

### Post by LaRoza on 2008-08-04
> **DaymItzJack said:**
> 
I already posted a Python version, that was just a joke and I'm advanced enough to be able to do this in my sleep anyways.

Ok. I haven't really looked at all the submissions yet. Way too many...

This thread will be closed tomorrow (or tonight, depending on where you are) and I will make a new thread. The new thread is less about writing code than writing useful code :-)

Stay tuned everyone.

---

### Post by Tim Sharitt on 2008-08-05
I just started learning scheme the day before this challenge was posted, so this is my first program in scheme.
```
(define beerstring
	(lambda (b)
		(cond ((= b 1) (display "1 bottle"))
		((= b 0) (display "no more bottles"))
		(else (display b) (display " bottles")))
	(display " of beer")))

(define beer
	(lambda (b)
		(cond ((> b 0)
			(beerstring b) (display " on the wall, ") (beerstring b) (display ".") (newline)
			(display "Take one down and pass it around, ")
			(beerstring (- b 1)) (display " on the wall.") (newline)
			(beer (- b 1))))))
(beer 99)
(display "No more bottles of beer on the wall, no more bottles of beer.") (newline)
(display "Go to the store and buy some more, 99 bottles of beer on the wall.") (newline)

```
I know it's probably crude, but I think it's okay for less than a week with a completely new language.
P.S. I'm using mzscheme if that matters.

---

### Post by LaRoza on 2008-08-05
Closed for grading :-)

See new challenge.

---

### Post by LaRoza on 2008-08-05
Grading here, so don't follow this until it is done! I am just keeping track of the ones I do and that work.

Possibles: 
[list]
[*] Tim Sharitt (scheme) [http://ubuntuforums.org/showpost.php?p=5525885&postcount=201](http://ubuntuforums.org/showpost.php?p=5525885&postcount=201)
[*]emobrad (c++) [http://ubuntuforums.org/showpost.php?p=5519960&postcount=157](http://ubuntuforums.org/showpost.php?p=5519960&postcount=157)
[*]tjmage1 (python) [http://ubuntuforums.org/showpost.php?p=5519031&postcount=155](http://ubuntuforums.org/showpost.php?p=5519031&postcount=155) 
[*] DaymItzJack (python) [http://ubuntuforums.org/showpost.php?p=5518782&postcount=154](http://ubuntuforums.org/showpost.php?p=5518782&postcount=154)
[*] AaronMT (python) [http://ubuntuforums.org/showpost.php?p=5517479&postcount=138](http://ubuntuforums.org/showpost.php?p=5517479&postcount=138)
[*] tafoo85 (c++) [http://ubuntuforums.org/showpost.php?p=5517391&postcount=137](http://ubuntuforums.org/showpost.php?p=5517391&postcount=137)
[*] Lux Perpetua (hasekell) [http://ubuntuforums.org/showpost.php?p=5517257&postcount=136](http://ubuntuforums.org/showpost.php?p=5517257&postcount=136)
[*] artoj (c++) [http://ubuntuforums.org/showpost.php?p=5516092&postcount=128](http://ubuntuforums.org/showpost.php?p=5516092&postcount=128)
[*] bobbocanfly (c) [http://ubuntuforums.org/showpost.php?p=5514605&postcount=110](http://ubuntuforums.org/showpost.php?p=5514605&postcount=110)
[*] wsppan (perl) [http://ubuntuforums.org/showpost.php?p=5513914&postcount=106](http://ubuntuforums.org/showpost.php?p=5513914&postcount=106)
[*] iofthemourning (python)[http://ubuntuforums.org/showpost.php?p=5513347&postcount=104](http://ubuntuforums.org/showpost.php?p=5513347&postcount=104)
[*] paul_philp (python) [http://ubuntuforums.org/showpost.php?p=5512195&postcount=83](http://ubuntuforums.org/showpost.php?p=5512195&postcount=83)
[*] aktiwers (python)[http://ubuntuforums.org/showpost.php?p=5510891&postcount=76](http://ubuntuforums.org/showpost.php?p=5510891&postcount=76)
[*] Ed J (python) [http://ubuntuforums.org/showpost.php?p=5509066&postcount=64](http://ubuntuforums.org/showpost.php?p=5509066&postcount=64)
[*] z0mbie (c++) [http://ubuntuforums.org/showpost.php?p=5507929&postcount=61](http://ubuntuforums.org/showpost.php?p=5507929&postcount=61)
[*] NovaAesa (c++) [http://ubuntuforums.org/showpost.php?p=5507853&postcount=58](http://ubuntuforums.org/showpost.php?p=5507853&postcount=58)
[*] OutOfReach (python) [http://ubuntuforums.org/showpost.php?p=5507726&postcount=54](http://ubuntuforums.org/showpost.php?p=5507726&postcount=54)
[*] Def13b (python) [http://ubuntuforums.org/showpost.php?p=5507005&postcount=46](http://ubuntuforums.org/showpost.php?p=5507005&postcount=46)
[*] arsenic23 (python) [http://ubuntuforums.org/showpost.php?p=5505044&postcount=38](http://ubuntuforums.org/showpost.php?p=5505044&postcount=38)
[*] mvoncken (python) [http://ubuntuforums.org/showpost.php?p=5503296&postcount=27](http://ubuntuforums.org/showpost.php?p=5503296&postcount=27)
[*] Titan8990 (python) [http://ubuntuforums.org/showpost.php?p=5502896&postcount=23](http://ubuntuforums.org/showpost.php?p=5502896&postcount=23)
[*] PandaGoat (c) [http://ubuntuforums.org/showpost.php?p=5500725&postcount=12](http://ubuntuforums.org/showpost.php?p=5500725&postcount=12)
[*] Yuki_Nagato (python) [http://ubuntuforums.org/showpost.php?p=5499608&postcount=3](http://ubuntuforums.org/showpost.php?p=5499608&postcount=3)
[/list]

Sorry:
[list]
[*] linkmaster03 (python) [http://ubuntuforums.org/showpost.php?p=5525361&postcount=198](http://ubuntuforums.org/showpost.php?p=5525361&postcount=198) 
[*] wilsonmuse (python)[http://ubuntuforums.org/showpost.php?p=5525230&postcount=197](http://ubuntuforums.org/showpost.php?p=5525230&postcount=197) 
[*] TreeFinger (python) [http://ubuntuforums.org/showpost.php?p=5521305&postcount=182](http://ubuntuforums.org/showpost.php?p=5521305&postcount=182) 
[*] jimi_hendrix (c++) [http://ubuntuforums.org/showpost.php?p=5521002&postcount=179](http://ubuntuforums.org/showpost.php?p=5521002&postcount=179) 
[*] Vishal Agarwal (php5-cli) [http://ubuntuforums.org/showpost.php?p=5520342&postcount=162](http://ubuntuforums.org/showpost.php?p=5520342&postcount=162) 
[*] TheNatealator (perl) [http://ubuntuforums.org/showpost.php?p=5517850&postcount=140](http://ubuntuforums.org/showpost.php?p=5517850&postcount=140)
[*] SteelDragon (python) [http://ubuntuforums.org/showpost.php?p=5515064&postcount=116](http://ubuntuforums.org/showpost.php?p=5515064&postcount=116)
[*] unutbu (python) [http://ubuntuforums.org/showpost.php?p=5514798&postcount=114](http://ubuntuforums.org/showpost.php?p=5514798&postcount=114)
[*] robertchahine (c) [http://ubuntuforums.org/showpost.php?p=5510881&postcount=75](http://ubuntuforums.org/showpost.php?p=5510881&postcount=75)
[*] jacensolo (python) [http://ubuntuforums.org/showpost.php?p=5510534&postcount=67](http://ubuntuforums.org/showpost.php?p=5510534&postcount=67)
[*] mosty friedman (java) [http://ubuntuforums.org/showpost.php?p=5508002&postcount=63](http://ubuntuforums.org/showpost.php?p=5508002&postcount=63)
[*] albeano2004 (java) [http://ubuntuforums.org/showpost.php?p=5507965&postcount=62](http://ubuntuforums.org/showpost.php?p=5507965&postcount=62)
[*] EDavidBurg (python) [http://ubuntuforums.org/showpost.php?p=5501514&postcount=16](http://ubuntuforums.org/showpost.php?p=5501514&postcount=16)
[*] Exershio (python) [http://ubuntuforums.org/showpost.php?p=5500860&postcount=13](http://ubuntuforums.org/showpost.php?p=5500860&postcount=13)
[*] Sinkingships7 (c) [http://ubuntuforums.org/showpost.php?p=5500091&postcount=9](http://ubuntuforums.org/showpost.php?p=5500091&postcount=9)
[*] tuxerman (c++) [http://ubuntuforums.org/showpost.php?p=5499755&postcount=6](http://ubuntuforums.org/showpost.php?p=5499755&postcount=6)
[*] Joeb454 (c) [http://ubuntuforums.org/showpost.php?p=5499651&postcount=4](http://ubuntuforums.org/showpost.php?p=5499651&postcount=4)
[/list]

Couldn't get it to work:
[list]
[*] grumbles79 (erlang) [http://ubuntuforums.org/showpost.php?p=5512707&postcount=96](http://ubuntuforums.org/showpost.php?p=5512707&postcount=96)
[*] lordhaworth (fortran90) [http://ubuntuforums.org/showpost.php?p=5501587&postcount=17](http://ubuntuforums.org/showpost.php?p=5501587&postcount=17)
[*] Maveric3477 (cl)[http://ubuntuforums.org/showpost.php?p=5501259&postcount=14](http://ubuntuforums.org/showpost.php?p=5501259&postcount=14) 
[/list]

---

### Post by jimi_hendrix on 2008-08-05
> **LaRoza said:**
> Closed for grading :-)

See new challenge.

i could be totally blind and if i am i am sorry but i dont see a new challenge

---

### Post by LaRoza on 2008-08-05
> **jimi_hendrix said:**
> i could be totally blind and if i am i am sorry but i dont see a new challenge

Yeah, it will be up soon.

---

### Post by LaRoza on 2008-08-05
Narrowed it to top ten:

[Def13b](http://ubuntuforums.org/showpost.php?p=5507005&postcount=46)
[arsenic23](http://ubuntuforums.org/showpost.php?p=5505044&postcount=38)
[mvoncken](http://ubuntuforums.org/showpost.php?p=5503296&postcount=27)
[DaymItzJack ](http://ubuntuforums.org/showpost.php?p=5518782&postcount=154)
[NovaAesa](http://ubuntuforums.org/showpost.php?p=5507853&postcount=58)
[wsppan](http://ubuntuforums.org/showpost.php?p=5513914&postcount=106)
[PandaGoat](http://ubuntuforums.org/showpost.php?p=5500725&postcount=12)
[Tim Sharitt](http://ubuntuforums.org/showpost.php?p=5525885&postcount=201)
[Lux Perpetua](http://ubuntuforums.org/showpost.php?p=5517257&postcount=136)

---

### Post by jimi_hendrix on 2008-08-05
ok thanks

---

### Post by LaRoza on 2008-08-05
Finished!

Method of judging:

[list]
[*] Find all entries of beginners that work (prints the song lyrics correctly)
[*] Remove all with obvious problems, formatting, readability, and non standard code (warnings are not to be ignored!)
[*] Separate all finalists into language. Anyone language with one representative is part of the poll. The large groups are reduced to the best of each (Python/C++ this time)
[*] Alphabetise and make poll
[/list]

You can all comment on code and give suggestions now. The "winner" will be whoever is the winner in the poll, which doesn't expire. 

This thread will not expire either, but the poll options won't change.

---

### Post by Kadrus on 2008-08-05
I voted for Tim Sharitt,I have little experience with Scheme,and as said above he has been learning it for a day,so he is considerably a beginner in scheme no matter what background he has in programming,and the code was clean,easy to understand,all i have to say is well done

---

### Post by schauerlich on 2008-08-05
Mine worked when I tested it, but now from OS X gives an error about non ascii characters. Redoing all of the whitespace fixed that. Weird.

---

### Post by LaRoza on 2008-08-05
> **EDavidBurg said:**
> Mine worked when I tested it, but now from OS X gives an error about non ascii characters. Redoing all of the whitespace fixed that. Weird.

What editor did you originally use?

---

### Post by schauerlich on 2008-08-05
> **LaRoza said:**
> What editor did you originally use?

I'm pretty sure it was Kate. If it wasn't that, then nano.

---

### Post by Maveric3477 on 2008-08-06
Hey, I'm not sure why mine didn't work, was there an error?

Testing it now on windows (Slime + Clisp), it works. Did you open it up in your CL implementation and run (main-loop)? 

If not, I probably should of added that in the comments. My bad.

---

### Post by -grubby on 2008-08-06
> **EDavidBurg said:**
> I'm pretty sure it was Kate. If it wasn't that, then nano.

Edavidburg: Did you set kate to use spaces for tabs instead of tabulator characters? 

Go into settings > Configure Kate > Editing > and select "Insert spaces instead of tabulators". Than, go into Settings > configure kate > identation and select "use spaces instead of tabs to indent".

---

### Post by schauerlich on 2008-08-06
> **nathangrubb said:**
> Edavidburg: Did you set kate to use spaces for tabs instead of tabulator characters? 

Go into settings > Configure Kate > Editing > and select "Insert spaces instead of tabulators". Than, go into Settings > configure kate > identation and select "use spaces instead of tabs to indent".

I did the second, not the first. Thanks.

---

### Post by LaRoza on 2008-08-06
> **Maveric3477 said:**
> Hey, I'm not sure why mine didn't work, was there an error?

Testing it now on windows (Slime + Clisp), it works. Did you open it up in your CL implementation and run (main-loop)? 

If not, I probably should of added that in the comments. My bad.

I couldn't run it, as I haven't used lisp outside the repl (Scheme I used) and I had a lot to try and didn't stop to check out the docs. I had clisp.

---

### Post by Maveric3477 on 2008-08-06
Ahhh, okie dokie :P

I was gonna use Scheme, but I didn't know if it had format in it, or if I could do something similar to ~r

If you want, I can give instructions on how to load it. But, it works and is too late for me to go on the poll (I wuold of won, totally :P)

P.S. ~r prints the word, not the number.. so it prints "ninety-nine".. etc

P.P.S If anyone reads this who has experience with CL, do you know how to make ~r capitalise? I couldn't find out

---

### Post by lordhaworth on 2008-08-06
out of curiosity for future reference could you not get mine to run because you havnt got a fortran90 compiler? or because i wrote it at work (w/out a fortran90 compiler) and didnt check it runs - i think ill wait and check anyway for the next one

will it be posted here when the next challenge is up?

---

### Post by Lux Perpetua on 2008-08-06
> **PandaGoat said:**
> [php]
#include <stdio.h>
#include <stdlib.h>

char* itoa(int n){char* _n = malloc(3); sprintf(_n, "%i", n); return _n;};
int main()
{
    int i;
    for(i = 99; i >= 0; i--)
    {
        printf("%s %s of beer on the wall, %s %s of beer. \n%s %s %s of beer on the wall.\n\n",
                i==0?"No more":itoa(i), i==1?"bottle":"bottles",
                i==0?"no more":itoa(i), i==1?"bottle":"bottles",
                i==0?"Go to the store and buy some more,":"Take one down and pass it around,",
                i==0?"99":i==1?"no more":itoa(i-1), i==2?"bottle":"bottles");
    }t
    return 0;
}
[/php]You've got a big memory leak here because your itoa allocates its own string, which your code promptly forgets about. This really isn't a job for dynamic allocation; you'd be better off writing to a static buffer.

---

### Post by LaRoza on 2008-08-06
> **lordhaworth said:**
> out of curiosity for future reference could you not get mine to run because you havnt got a fortran90 compiler? or because i wrote it at work (w/out a fortran90 compiler) and didnt check it runs - i think ill wait and check anyway for the next one

will it be posted here when the next challenge is up?
Oh, I had trouble compiling it, forgot to name the file (my home directory is full of practice code files, which are all named "p" with different extensions. My p.f90 was what I used.

I just ran it, and it didn't print the last verse, so it wasn't valid anyway.

---

### Post by TheNatealator on 2008-08-06
Out of curiosity, what went wrong with my script? Was it because I chose a non-straightforward implementation, or was my output wrong? I know you have a lot of entries, but it would be nice for us to learn from our mistakes.

---

### Post by LaRoza on 2008-08-06
> **TheNatealator said:**
> Out of curiosity, what went wrong with my script? Was it because I chose a non-straightforward implementation, or was my output wrong? I know you have a lot of entries, but it would be nice for us to learn from our mistakes.
It didn't print the last verse.

---

### Post by fluteflute on 2008-08-07
I know this is finished now but I wanted to do all the challenges starting from the beggining in Python (which I'm trying to learn). So I thought I might as well submit it here.
[PHP]#! /usr/bin/python 

ii = 99

while ii > 2:
	print "%s bottles of beer on the wall, %s bottles of beer." %(ii,ii)
	ii = ii - 1
	print "Take one down and pass it around, %s bottles of beer on the wall." %ii
	
while ii == 2:
	print "%s bottles of beer on the wall, %s bottles of beer." %(ii,ii)
	ii = ii - 1
	print "Take one down and pass it around, %s bottle of beer on the wall." %ii
	
while ii == 1:
	print "No more bottles of beer on the wall, no more bottles of beer. "
	ii = ii - 1
	ii = 99
	print "Go to the store and buy some more, %s bottles of beer on the wall." %ii[/PHP]

---

### Post by WitchCraft on 2008-08-09
> **ghostdog74 said:**
> ```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html | awk '/<p>/{gsub("<br>","\n");gsub(" *<[^>]+>","");print}'

```

Only two flaws.
First: you don't indirect the stderr, and if some errors occur during transmission, they will be in the output...

Second: you don't add newlines.

This way to add stderr-redirect in your example:
```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html 2> /dev/null | awk '/<p>/{gsub("<br>","\n");gsub(" *<[^>]+>","");print}'

```

And since nobody needs awk, here is a fully correct way,only using core-utils:
```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html 2> /dev/null | grep "be" | tr -d '\012' | sed ';s/<[^>]*>//g;s/^\s*//g;s/er\./er\.\n/g;s/ll\./ll\.\n\n/g;' | sed 's/^\s*//g'

```

---

### Post by ghostdog74 on 2008-08-09
> **WitchCraft said:**
> Only two flaws.
First: you don't indirect the stderr, and if some errors occur during transmission, they will be in the output...

good, then i will know what's going on and it will be a bigger part of the entire code, which is not what i intend to do.


> 
And since nobody needs awk, here is a fully correct way,only using core-utils:
```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html 2> /dev/null | grep "be" | tr -d '\012' | sed ';s/<[^>]*>//g;s/^\s*//g;s/er\./er\.\n/g;s/ll\./ll\.\n\n/g;' | sed 's/^\s*//g'

```
that's really messy, and no one needs that many seds/greps/tr. Awk can provide the functionality of all of these commands add together.

---

### Post by kaatil on 2008-08-09
Here my program.. it's recrusive in C. :)

[PHP]
#include <stdio.h>


void beers( int beers_count ){
	if (beers_count > 2) {
		printf("%d bottles of beer on the wall, %d bottles of beer.\n", beers_count, beers_count);
		printf("Take one down and pass it around, %d bottles of beer on the wall.\n\n", beers_count - 1);
		beers( beers_count - 1);
	}
		
	else if (beers_count == 2 ) {
		printf("2 bottles of beer on the wall, 2 bottles of beer.\n");
		printf("Take one down and pass it around, 1 bottle of beer on the wall.\n\n");
		beers( beers_count - 1 );
	}
		
	else if (beers_count == 1) {
		printf("1 bottle of beer on the wall, 1 bottle of beer.\n");
        printf("Take one down and pass it around, no more bottles of beer on the wall.\n\n");
		beers( beers_count - 1 );
		
	}
	else {
		printf("No more bottles of beer on the wall, no more bottles of beer\n.");
		printf("Go to the store and buy some more, 99 bottles of beer on the wall\n\n.");
	}
}

int main(){
	beers( 99 );
	return 0;
}

[/PHP]

---

### Post by furialis on 2008-08-10
I bought a couple of python books and I'm trying to teach myself programming. This is my first program ever. I know its a little late but please let me know how it is. Any mentors out there?

[PHP]
loop = 1
while loop == 1:
     a = 15
     b = "Bottles of beer on the wall,"
     c = "Bottles of beer!\n" 
     d = "Take one down, pass it around,"
     e = "Bottles of beer on the wall!\n"
     f = "Bottle of beer on the wall!"
     g = "Bottle of beer on the wall!\n"
     h = "Bottle of beer!\n"
     i = "WE HAVE NO MORE BEER!\n"
     while a > 2:
          print a, b, a, c, d, a - 1, e
          a = a - 1
     print a, b, a, c, d, a - 1, g
     print a - 1, f, a - 1, h, d, i
     z = raw_input("Do you want to go to the store to get more? Y/N? ")
quit
[/PHP]

---

### Post by lisati on 2008-08-10
> **furialis said:**
> I bought a couple of python books and I'm trying to teach myself programming. This is my first program ever. I know its a little late but please let me know how it is. Any mentors out there?

[PHP]
loop = 1
while loop == 1:
     a = 15
     b = "Bottles of beer on the wall,"
     c = "Bottles of beer!\n" 
     d = "Take one down, pass it around,"
     e = "Bottles of beer on the wall!\n"
     f = "Bottle of beer on the wall!"
     g = "Bottle of beer on the wall!\n"
     h = "Bottle of beer!\n"
     i = "WE HAVE NO MORE BEER!\n"
     while a > 2:
          print a, b, a, c, d, a - 1, e
          a = a - 1
     print a, b, a, c, d, a - 1, g
     print a - 1, f, a - 1, h, d, i
     z = raw_input("Do you want to go to the store to get more? Y/N? ")
[\PHP]
The \PHP tag should be /PHP and will help the formatting

---

### Post by mssever on 2008-08-10
Try using meaningful variable names instead of single letters. In larger programs, single letters can quickly become confusing.

---

### Post by LaRoza on 2008-08-10
> **mssever said:**
> Try using meaningful variable names instead of single letters. In larger programs, single letters can quickly become confusing.

One of the entries was booted from the list because of that.

---

### Post by mssever on 2008-08-10
> **LaRoza said:**
> One of the entries wasn't booted from the list because of that.
Wasn't? or was?

---

### Post by furialis on 2008-08-10
> **LaRoza said:**
> One of the entries wasn't booted from the list because of that.

What does that mean?

---

### Post by LaRoza on 2008-08-10
> **mssever said:**
> Wasn't? or was?

was, sorry.

> **furialis said:**
> What does that mean?

It means I can't spell.

---

### Post by cmay on 2008-08-11
```
#!/usr/bin/perl
#my_first_perl_program_and_i_think_that_is_sad_that_i_never_used_per_before#################################
printf("there was 99 bottles of beer on the wall \nthis is how we got rid of them all\n\n");#################
$bottles=99;for($takes_bottles_down=2;$takes_bottles_down => $bottles;$takes_bottles_down-1){###############
printf("%d bottles on the wall \ntake one down and pass it around %d on the wall\n\n",$bottles--,$bottles);#
if($bottles == 1){printf("%d bottle on the wall i take it down and pass it around\n\n",$bottles--);#########
printf(" now thee is no more bottles on the wall\nwe must have taken care of them all\n");}#################
}{printf("\n");}{printf("license GPL\n");}{printf("AUTHOR nevermind\n");}{##################################
printf("\ni can drive here i am the winnner \n quote :beck hansen\n");}#####################################
#or_some_would_say_it_would_be_sad_if_keep_learning_perl_:)#################################################
#cmay:2008.......................please dont tell anyone about this ok?#####################################

```
i am learning perl now. i started 24 hours ago  reading and is my very first perlscript. i am very proud of this.:)

---

### Post by Lux Perpetua on 2008-08-11
> **cmay said:**
> i am learning perl now. i started 24 hours ago  reading and is my very first perlscript. i am very proud of this.:)That wasn't after all 99 bottles, was it? If so, you have good reason to be proud!

---

### Post by cmay on 2008-08-11
> That wasn't after all 99 bottles, was it? If so, you have good reason to be proud!
actually i dident need that many bottles.:)

i wrote it as a tribute to beck hansens album mellow gold.

---

### Post by doas777 on 2008-08-17
sorry to chime in late. I'm learning python and this looked a good exercise. thanks for putting 'em up.

anyway, here's mine. it's short, static, and decidedly uncool, but I like the idea of O(n-3) and getting rid of all the little checks every iteration seemed worthwhile.

```

#! /usr/bin/env python
# ubuntuforums programming challenge 1
#99 bottles of beer

bot = 98
print "99 bottles of beer on the wall, 99 bottles of beer. "
print " Take one down, pass it arround, "
while(bot > 1):
    print str(bot) + " bottles of beer on the wall. \n"
    print str(bot) + " bottles of beer on the wall, " + str(bot) + " bottles of beer."
    print " Take one down, pass it arround, "
    bot -= 1
print "just 1 bottle of beer on the wall."
print "\n1 bottle of beer on the wall, just 1 bottle of beer. "
print "Take it down, pass it arround,"
print "No more bottles of beeeeeeeeer oooooooon the waaaaaaaaaaaaaaalllll" 

```


have fun, 
Franklin

---

### Post by sdennie on 2008-08-17
Someone just pointed me at this so, I'm a bit late.  Hopefully this is correct and LaRozas new rule of non-beginners is no longer in effect after things have been open for a while:

```

#!/usr/bin/perl

$b = $_ != 1 ? "bottles" : "bottle", $l = $_ ? $_ - 1 : 99, $l = $l ? $l : "no more", $_ = $_ ? $_ : "no", print ucfirst "$_ $b of beer on the wall, $_ $b of beer.\n".($l != 99 ? "Take one down, pass it around" : "Go to the store and buy some more").", $l ".($l == 1 ? "bottle" : "bottles")." of beer on the wall.\n\n" for reverse 0..99;
```

(No bonus points for me.  I've used perl before)

Edit:
Someone pointed out a few problems in the end cases.  Fixed in the general style of the original.

---

### Post by Retaliation on 2008-08-18
Just found this challenge on the forums, decided to give it a try. :)
I am just starting out on python, so I thought I would keep it simple. Ended up being pretty short too.

```
#!/usr/bin/python
#99 Bottles too many

for x in range(99,1,-1):
	print x, "bottles of beer on the wall,", x,"bottles of beer!"
	print "Take one down, pass it around,", x, "bottles of beer on the wall!"
	print " "
x = x - 1
print x, "bottle of beer on the wall,", x,"bottle of beer!"
print "Take one down, pass it around, no more bottles of beer on the wall!"
print " "
print "No more bottles of beer on the wall, no more bottles of beer!"
print "Go to the store and buy some more, 99 bottles of beer on the wall!"
```

Guess I'll check out the next challenge!

---

### Post by jinksys on 2008-08-19
I'm no beginner, but hacking something up in asm is always fun to me.

```

#99 Bottles by Steve Melvin <jinksys@gmail.com>
.data
int_beer:
	.int 99
msg_sing:
	.asciz "1 bottle of beer on the wall, 1 bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n\n"

msg_plur:
	.asciz "%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottles of beer on the wall.\n\n"

msg_end:
	.asciz "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.\n"

.text
.globl _start
_start:

beerloop:
decl int_beer
pushl int_beer
incl int_beer
pushl int_beer
pushl int_beer
pushl $msg_plur
call printf
add $8, %esp
decl int_beer
cmp $1, int_beer
jg beerloop

pushl $msg_sing
call printf
add $4, %esp

pushl $msg_end
call printf
add $4, %esp

movl $1, %eax
movl $0, %ebx
int $0x80

```

Compile:
```

as bottles.s -o bottles.o
ld bottles.o -o bottles -lc -dynamic-linker /lib/ld-linux.so.2

```

---

### Post by ogwilson on 2008-08-29
Took a shot at it. Heres my code.

```
//BottlesOfBeer.cpp

#include <iostream>
using namespace std;

class BottlesOfBeer
{
    private:
        int beerBottles;
        int OriginalBeerBottles;
    
    public:
        BottlesOfBeer(int bob = 99){ beerBottles = bob; OriginalBeerBottles = bob;}
        
        void playSong()
        {
            for(int i= OriginalBeerBottles; i > 0; i--)
            {
                if(i > 2)
                {
                    cout << endl << beerBottles << " Bottles of Beer on the wall, "
                    << beerBottles << " Bottles of Beer.\nTake one down and pass"
                    << " it around,";
                    
                    beerBottles--;
                    
                    cout << beerBottles << " Bottles of Beer on the wall.";
                }
                else if(beerBottles == 1)
                {
                    cout << endl << beerBottles << " Bottle of Beer on the wall, "
                    << beerBottles << " Bottle of Beer.\nTake one down and pass"
                    << " it around,";
                    
                    beerBottles--;
                    
                    cout << " No more Bottles of Beer on the wall.";
                }
                else if(beerBottles == 2)
                {
                    cout << endl << beerBottles << " Bottles of Beer on the wall, "
                    << beerBottles << " Bottle of Beer.\nTake one down and pass"
                    << " it around,";
                    
                    beerBottles--;
                    
                    cout << " 1 Bottle of Beer on the wall.";
                }
                else
                {
                    cout << endl << "No more bottles of beer on the wall, no more bottles of beer."
                    << "\n Go to the store and buy some more";
                    
                    beerBottles = OriginalBeerBottles;
                    
                    cout << beerBottles << " bottles of beer on the wall.";
                }
            }
        }
};

``````
//Main.cpp

#include "botsofbeer.cpp"

int main(int argc, char** argv)
{
    BottlesOfBeer bots;
    
    bots.playSong();
    
    return 0;
}

```

---

### Post by ogwilson on 2008-08-30
Improved encapsulation:

```
//BottlesOfBeer.cpp

#include <iostream>
using namespace std;

class BottlesOfBeer
{
    private:
        int beerBottles;
        int OriginalBeerBottles;
        void getLyrics(int bob)
        {
            if(bob > 2)
                {
                    cout << endl << endl << beerBottles << " Bottles of Beer on the wall, "    << beerBottles << " Bottles of Beer.\nTake one down and pass" << " it around,";
                    
                    beerBottles--;
                    
                    cout << beerBottles << " Bottles of Beer on the wall.";
                }
                else if(bob == 1)
                {
                    cout << endl << endl << beerBottles << " Bottle of Beer on the wall, " << beerBottles << " Bottle of Beer.\nTake one down and pass"    << " it around,";
                    
                    beerBottles--;
                    
                    cout << " No more Bottles of Beer on the wall.";

                }
                else if(bob == 2)
                {
                    cout << endl << endl << beerBottles << " Bottles of Beer on the wall, "<< beerBottles << " Bottle of Beer.\nTake one down and pass"    << " it around,";
                    
                    beerBottles--;
                    
                    cout <<  beerBottles << " Bottle of Beer on the wall.";
                }
                else
                {
                    cout << endl << endl << "No more bottles of beer on the wall, no more bottles of beer."<< "\n Go to the store and buy some more, ";
                    
                    beerBottles = OriginalBeerBottles;
                    
                    cout << beerBottles << " bottles of beer on the wall.";
                }
            }
            
    
    public:
        BottlesOfBeer(int bob = 99){ beerBottles = bob; OriginalBeerBottles = bob;}
        
        void playSong()
        {
            for(int i= OriginalBeerBottles; i >= 0; i--)
            {
                getLyrics(beerBottles);
            }
        }
};

```

Later I'll improve it some more by allowing the user to take down and pass around more than 1 beer bottles.

---

### Post by cmay on 2008-08-30
i created a small utility for picking up the bottles and put them back on the wall. just run this program when some one has taken all 99 bottles of the wall :)
[PHP]
program beer_back_on_the_wall;
uses crt,sysutils;
var 
i:integer;
begin
writeln(' this is puts back the 99 bottles of beer on the wall');
for i:= 1to 99 do begin
delay(100);
writeln('puts back',i,'');
writeln('bottles of beer on the wall');
end;
clrscr;
writeln(' now all the',i,' bottles are back on the wall ');
end.
[/PHP]
compile whit Free pascal in turbo pascal mode.

---

### Post by ifross on 2008-08-31
I have done the old python one liner, just to see if I could do it really. Not sure if anyone has posted one similar as it is a long thread:

[PHP]print  "".join(["%s bottle%s of beer on the wall,\nTake one down and pass it around, %s bottle%s of beer on the wall,\n\n" % (str(i), ("", "s")[bool(i-1)], ("no more", str(i-1))[bool(i-1)], ("", "s")[bool(i-2)]) for i in range(99,0,-1)] + ["No beer, go buy more!\nAdd the beer to the wall, 99 bottles of beer on the wall."])[/PHP]

I know it was supposed to be easy to read, but like I said, I was just seeing if I could do it on one line, so it is never going to be easy to read.

---

### Post by akbeancounter on 2008-09-09
I've been working on this the last couple of days, but meatspace obligations took precedence.  Here's my shot at 99 Bottles of Beer, written in C++.

[PHP]
/* Comments explaining program, purpose, 
   author, licensing, etc.  */

#include <iostream>
#include <time.h>
using namespace std;

int main()
{
 cout << "*************************************" << endl;
 cout << "*        99 Bottles of Beer         *" << endl;
 cout << "*************************************\n\n" << endl;

int bottles = 99;

while(bottles > 2)		// loop verses 99 - 3
{
    cout << bottles << " bottles of beer on the wall" << endl;
    cout << bottles << " bottles of beer" << endl;
    cout << "Take one down, pass it around," << endl;
    bottles--; 			// decrement bottles by 1, continue verse
    cout << bottles << " bottles of beer on the wall.\n\n" << endl;
    sleep(2);                   // Makes it a bit easier to watch, I think.
                                // If writing for Windows, change to Sleep(2000);
}			

if(bottles == 2)		// when we get down to two bottles, begin end sequence
{
    cout << bottles << " bottles of beer on the wall" << endl;
    cout << bottles << " bottles of beer" << endl;
    cout << "Take one down, pass it around," << endl;
    cout << "One bottle of beer on the wall.\n\n" << endl;

    cout << "One bottle of beer on the wall" << endl;
    cout << "One bottle of beer" << endl;
    cout << "Take it down, pass it around," << endl;
    cout << "No more bottles of beer on the wall.\n\n" << endl;

    cout << "No more bottles of beer on the wall" << endl;
    cout << "No more bottles of beer" << endl;
    cout << "Go to the store and buy some more," << endl;
    cout << "99 bottles of beer on the wall.\n" << endl;
} 
else  				// if I did my job correctly,
                                // this should never print
{cout << "There's something wrong with your loop, man." << endl;}

return 0;
}
[/PHP]

The comments should all align, but I'm not going to take it down over a little tab damage.  I can't actually try to run it until tonight, so I may come back later to fix it.

Update 9/9/08 17:30 GMT-9: I didn't have my books with me, so I wasn't sure whether "using namespace std" needed a semicolon.  I guessed wrong.  Fixed now, works great.  With the sleep statements, it takes about eight minutes to fully execute.

-- A.

---

### Post by WitchCraft on 2008-09-12
> **ghostdog74 said:**
> 
that's really messy, and no one needs that many seds/greps/tr. Awk can provide the functionality of all of these commands add together.

Now I made it even more professional: 
I found the reason why the newline removal didn't work.

So now tr -d '\012' can be replaced with
```

sed ':a;N;$!ba;s/\n//g'

```


l00ks far nic3r, now:
```

wget -q -O - http://99-bottles-of-beer.net/lyrics.html 2> /dev/null | grep "be" | sed ':a;N;$!ba;s/\n//g;s/<[^>]*>//g;s/^\s*//g;s/er\./er\.\n/g;s/ll\./ll\.\n\n/g;' | sed 's/^\s*//g'

```


~# wget -q -O - [http://99-bottles-of-beer.net/lyrics.html](http://99-bottles-of-beer.net/lyrics.html) 2> /dev/null | grep "be" | sed ':a;N;$!ba;s/\n//g;s/<[^>]*>//g;s/^\s*//g;s/er\./er\.\n/g;s/ll\./ll\.\n\n/g;' | sed 's/^\s*//g' >> 99bottles.txt

99bottles.txt:
```

99 bottles of beer on the wall, 99 bottles of beer.
Take one down and pass it around, 98 bottles of beer on the wall.

98 bottles of beer on the wall, 98 bottles of beer.
Take one down and pass it around, 97 bottles of beer on the wall.

97 bottles of beer on the wall, 97 bottles of beer.
Take one down and pass it around, 96 bottles of beer on the wall.

96 bottles of beer on the wall, 96 bottles of beer.
Take one down and pass it around, 95 bottles of beer on the wall.

95 bottles of beer on the wall, 95 bottles of beer.
Take one down and pass it around, 94 bottles of beer on the wall.

94 bottles of beer on the wall, 94 bottles of beer.
Take one down and pass it around, 93 bottles of beer on the wall.

93 bottles of beer on the wall, 93 bottles of beer.
Take one down and pass it around, 92 bottles of beer on the wall.

92 bottles of beer on the wall, 92 bottles of beer.
Take one down and pass it around, 91 bottles of beer on the wall.

91 bottles of beer on the wall, 91 bottles of beer.
Take one down and pass it around, 90 bottles of beer on the wall.

90 bottles of beer on the wall, 90 bottles of beer.
Take one down and pass it around, 89 bottles of beer on the wall.

89 bottles of beer on the wall, 89 bottles of beer.
Take one down and pass it around, 88 bottles of beer on the wall.

88 bottles of beer on the wall, 88 bottles of beer.
Take one down and pass it around, 87 bottles of beer on the wall.

87 bottles of beer on the wall, 87 bottles of beer.
Take one down and pass it around, 86 bottles of beer on the wall.

86 bottles of beer on the wall, 86 bottles of beer.
Take one down and pass it around, 85 bottles of beer on the wall.

85 bottles of beer on the wall, 85 bottles of beer.
Take one down and pass it around, 84 bottles of beer on the wall.

84 bottles of beer on the wall, 84 bottles of beer.
Take one down and pass it around, 83 bottles of beer on the wall.

83 bottles of beer on the wall, 83 bottles of beer.
Take one down and pass it around, 82 bottles of beer on the wall.

82 bottles of beer on the wall, 82 bottles of beer.
Take one down and pass it around, 81 bottles of beer on the wall.

81 bottles of beer on the wall, 81 bottles of beer.
Take one down and pass it around, 80 bottles of beer on the wall.

80 bottles of beer on the wall, 80 bottles of beer.
Take one down and pass it around, 79 bottles of beer on the wall.

79 bottles of beer on the wall, 79 bottles of beer.
Take one down and pass it around, 78 bottles of beer on the wall.

78 bottles of beer on the wall, 78 bottles of beer.
Take one down and pass it around, 77 bottles of beer on the wall.

77 bottles of beer on the wall, 77 bottles of beer.
Take one down and pass it around, 76 bottles of beer on the wall.

76 bottles of beer on the wall, 76 bottles of beer.
Take one down and pass it around, 75 bottles of beer on the wall.

75 bottles of beer on the wall, 75 bottles of beer.
Take one down and pass it around, 74 bottles of beer on the wall.

74 bottles of beer on the wall, 74 bottles of beer.
Take one down and pass it around, 73 bottles of beer on the wall.

73 bottles of beer on the wall, 73 bottles of beer.
Take one down and pass it around, 72 bottles of beer on the wall.

72 bottles of beer on the wall, 72 bottles of beer.
Take one down and pass it around, 71 bottles of beer on the wall.

71 bottles of beer on the wall, 71 bottles of beer.
Take one down and pass it around, 70 bottles of beer on the wall.

70 bottles of beer on the wall, 70 bottles of beer.
Take one down and pass it around, 69 bottles of beer on the wall.

69 bottles of beer on the wall, 69 bottles of beer.
Take one down and pass it around, 68 bottles of beer on the wall.

68 bottles of beer on the wall, 68 bottles of beer.
Take one down and pass it around, 67 bottles of beer on the wall.

67 bottles of beer on the wall, 67 bottles of beer.
Take one down and pass it around, 66 bottles of beer on the wall.

66 bottles of beer on the wall, 66 bottles of beer.
Take one down and pass it around, 65 bottles of beer on the wall.

65 bottles of beer on the wall, 65 bottles of beer.
Take one down and pass it around, 64 bottles of beer on the wall.

64 bottles of beer on the wall, 64 bottles of beer.
Take one down and pass it around, 63 bottles of beer on the wall.

63 bottles of beer on the wall, 63 bottles of beer.
Take one down and pass it around, 62 bottles of beer on the wall.

62 bottles of beer on the wall, 62 bottles of beer.
Take one down and pass it around, 61 bottles of beer on the wall.

61 bottles of beer on the wall, 61 bottles of beer.
Take one down and pass it around, 60 bottles of beer on the wall.

60 bottles of beer on the wall, 60 bottles of beer.
Take one down and pass it around, 59 bottles of beer on the wall.

59 bottles of beer on the wall, 59 bottles of beer.
Take one down and pass it around, 58 bottles of beer on the wall.

58 bottles of beer on the wall, 58 bottles of beer.
Take one down and pass it around, 57 bottles of beer on the wall.

57 bottles of beer on the wall, 57 bottles of beer.
Take one down and pass it around, 56 bottles of beer on the wall.

56 bottles of beer on the wall, 56 bottles of beer.
Take one down and pass it around, 55 bottles of beer on the wall.

55 bottles of beer on the wall, 55 bottles of beer.
Take one down and pass it around, 54 bottles of beer on the wall.

54 bottles of beer on the wall, 54 bottles of beer.
Take one down and pass it around, 53 bottles of beer on the wall.

53 bottles of beer on the wall, 53 bottles of beer.
Take one down and pass it around, 52 bottles of beer on the wall.

52 bottles of beer on the wall, 52 bottles of beer.
Take one down and pass it around, 51 bottles of beer on the wall.

51 bottles of beer on the wall, 51 bottles of beer.
Take one down and pass it around, 50 bottles of beer on the wall.

50 bottles of beer on the wall, 50 bottles of beer.
Take one down and pass it around, 49 bottles of beer on the wall.

49 bottles of beer on the wall, 49 bottles of beer.
Take one down and pass it around, 48 bottles of beer on the wall.

48 bottles of beer on the wall, 48 bottles of beer.
Take one down and pass it around, 47 bottles of beer on the wall.

47 bottles of beer on the wall, 47 bottles of beer.
Take one down and pass it around, 46 bottles of beer on the wall.

46 bottles of beer on the wall, 46 bottles of beer.
Take one down and pass it around, 45 bottles of beer on the wall.

45 bottles of beer on the wall, 45 bottles of beer.
Take one down and pass it around, 44 bottles of beer on the wall.

44 bottles of beer on the wall, 44 bottles of beer.
Take one down and pass it around, 43 bottles of beer on the wall.

43 bottles of beer on the wall, 43 bottles of beer.
Take one down and pass it around, 42 bottles of beer on the wall.

42 bottles of beer on the wall, 42 bottles of beer.
Take one down and pass it around, 41 bottles of beer on the wall.

41 bottles of beer on the wall, 41 bottles of beer.
Take one down and pass it around, 40 bottles of beer on the wall.

40 bottles of beer on the wall, 40 bottles of beer.
Take one down and pass it around, 39 bottles of beer on the wall.

39 bottles of beer on the wall, 39 bottles of beer.
Take one down and pass it around, 38 bottles of beer on the wall.

38 bottles of beer on the wall, 38 bottles of beer.
Take one down and pass it around, 37 bottles of beer on the wall.

37 bottles of beer on the wall, 37 bottles of beer.
Take one down and pass it around, 36 bottles of beer on the wall.

36 bottles of beer on the wall, 36 bottles of beer.
Take one down and pass it around, 35 bottles of beer on the wall.

35 bottles of beer on the wall, 35 bottles of beer.
Take one down and pass it around, 34 bottles of beer on the wall.

34 bottles of beer on the wall, 34 bottles of beer.
Take one down and pass it around, 33 bottles of beer on the wall.

33 bottles of beer on the wall, 33 bottles of beer.
Take one down and pass it around, 32 bottles of beer on the wall.

32 bottles of beer on the wall, 32 bottles of beer.
Take one down and pass it around, 31 bottles of beer on the wall.

31 bottles of beer on the wall, 31 bottles of beer.
Take one down and pass it around, 30 bottles of beer on the wall.

30 bottles of beer on the wall, 30 bottles of beer.
Take one down and pass it around, 29 bottles of beer on the wall.

29 bottles of beer on the wall, 29 bottles of beer.
Take one down and pass it around, 28 bottles of beer on the wall.

28 bottles of beer on the wall, 28 bottles of beer.
Take one down and pass it around, 27 bottles of beer on the wall.

27 bottles of beer on the wall, 27 bottles of beer.
Take one down and pass it around, 26 bottles of beer on the wall.

26 bottles of beer on the wall, 26 bottles of beer.
Take one down and pass it around, 25 bottles of beer on the wall.

25 bottles of beer on the wall, 25 bottles of beer.
Take one down and pass it around, 24 bottles of beer on the wall.

24 bottles of beer on the wall, 24 bottles of beer.
Take one down and pass it around, 23 bottles of beer on the wall.

23 bottles of beer on the wall, 23 bottles of beer.
Take one down and pass it around, 22 bottles of beer on the wall.

22 bottles of beer on the wall, 22 bottles of beer.
Take one down and pass it around, 21 bottles of beer on the wall.

21 bottles of beer on the wall, 21 bottles of beer.
Take one down and pass it around, 20 bottles of beer on the wall.

20 bottles of beer on the wall, 20 bottles of beer.
Take one down and pass it around, 19 bottles of beer on the wall.

19 bottles of beer on the wall, 19 bottles of beer.
Take one down and pass it around, 18 bottles of beer on the wall.

18 bottles of beer on the wall, 18 bottles of beer.
Take one down and pass it around, 17 bottles of beer on the wall.

17 bottles of beer on the wall, 17 bottles of beer.
Take one down and pass it around, 16 bottles of beer on the wall.

16 bottles of beer on the wall, 16 bottles of beer.
Take one down and pass it around, 15 bottles of beer on the wall.

15 bottles of beer on the wall, 15 bottles of beer.
Take one down and pass it around, 14 bottles of beer on the wall.

14 bottles of beer on the wall, 14 bottles of beer.
Take one down and pass it around, 13 bottles of beer on the wall.

13 bottles of beer on the wall, 13 bottles of beer.
Take one down and pass it around, 12 bottles of beer on the wall.

12 bottles of beer on the wall, 12 bottles of beer.
Take one down and pass it around, 11 bottles of beer on the wall.

11 bottles of beer on the wall, 11 bottles of beer.
Take one down and pass it around, 10 bottles of beer on the wall.

10 bottles of beer on the wall, 10 bottles of beer.
Take one down and pass it around, 9 bottles of beer on the wall.

9 bottles of beer on the wall, 9 bottles of beer.
Take one down and pass it around, 8 bottles of beer on the wall.

8 bottles of beer on the wall, 8 bottles of beer.
Take one down and pass it around, 7 bottles of beer on the wall.

7 bottles of beer on the wall, 7 bottles of beer.
Take one down and pass it around, 6 bottles of beer on the wall.

6 bottles of beer on the wall, 6 bottles of beer.
Take one down and pass it around, 5 bottles of beer on the wall.

5 bottles of beer on the wall, 5 bottles of beer.
Take one down and pass it around, 4 bottles of beer on the wall.

4 bottles of beer on the wall, 4 bottles of beer.
Take one down and pass it around, 3 bottles of beer on the wall.

3 bottles of beer on the wall, 3 bottles of beer.
Take one down and pass it around, 2 bottles of beer on the wall.

2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around, 1 bottle of beer on the wall.

1 bottle of beer on the wall, 1 bottle of beer.
Take one down and pass it around, no more bottles of beer on the wall.

No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall.

```

---

### Post by Nemooo on 2008-09-13
My first script using Arc:

```
; Prints the "99 bottles of beer" lyrics or
; any other desired number of bottles.
;
; Run with (99-bottles [number of bottles]).

(def 99-bottles (bottles)
    (let plural " bottles"
        (repeat bottles
            (prn bottles plural " of beer on the wall, " bottles plural " of beer.")
            (= bottles (- bottles 1))
            (if (< bottles 2) (= plural " bottle"))
            (if (< bottles 1) (and (= bottles "no more") (= plural " bottles")))
            (prn "Take one down and pass it around, " bottles plural " of beer on the wall.\n")))
    (prn "No more bottles of beer on the wall, no more bottles of beer.")
    (prn "Go to the store and buy some more, 99 bottles of beer on the wall.\n"))
```

---

### Post by NinjaKick on 2008-09-16
Hello, here is my version of "99 bottles of beer":)

[PHP]

// Java code - 99 Bottles of Beer

public class Beer {
    
    public static void beer(int bottles) { // This is an iterating method
    	if (bottles == 0) {
    		System.out.println("No more bottles of beer on the wall, no more bottles of beer. ");
    		System.out.print("Go to the store and buy some more, "); 
    		bottles = 99;
    		System.out.println(bottles + " bottles of beer on the wall.\n");
    	}
    	else if (bottles == 1) {
   	        System.out.println(bottles + " bottle of beer on the wall, " + bottles + " bottle of beer.");
   		System.out.print("Take one down and pass it around, ");
   		bottles--;
   		System.out.println("no more bottles of beer on the wall.\n");
   		beer(bottles);
    	}
    	else if (bottles == 2) {
    		System.out.println(bottles + " bottles of beer on the wall, " + bottles + " bottles of beer.");
    		System.out.print("Take one down and pass it around, ");
    		bottles--;
    		System.out.println(bottles + " bottle of beer on the wall.\n");
    		beer(bottles);
    	}
    	else { // all other numbers
    		System.out.println(bottles + " bottles of beer on the wall, " + bottles + " bottles of beer.");
    		System.out.print("Take one down and pass it around, ");
    		bottles--;
    		System.out.println(bottles + " bottles of beer on the wall.\n");
    		beer(bottles);
    	}
    }
    
    public static void main(String[] args) {
		beer(99);
    }
}
[/PHP]

---

### Post by hey_ram on 2008-09-24
hey!

just came across this thread...
its a nice challenge...

here is my attempt:
```

/*trying to do the same bottles of beer routine using a switch statement.*/

#include<stdio.h>

int main(int argc, char *argv[])
{
 int j = 99, i;
 i = j;

 while( j >= 0 )
 {
  printf("\n");
  switch(j)
  {
   case 0:
   	printf("\nNo more bottles of beer on the wall, no more bottles of beer.\n");
	break;

   case 1:
   	printf("\n%d bottle of beer on the wall, %d bottle of beer.\n", j, j);
	break;

   default:
   	printf("\n%d bottles of beer, %d bottles of beer.\n", j, j);
	break;
  }

  switch(j)
  {
   case 0:
   	printf("Go to the store and buy some more, %d bottles of beer on the wall.", i);
	break;

   case 1:
      	printf("Take one down and pass it around, no more bottles of beer.");
	break;

   default:
   	printf("Take one down and pass it around, %d bottles of beer on the wall.", (j - 1));
	break;
  }
  j--;
 }

 return 0;
}

```

---

### Post by hannseman on 2008-09-30
I know the challenge is over but I love the idea so I did this anyway.

[PHP]
public class Beer {
	public static void main(String[] args){
		for (int i = 99; i >= 2; i--){
			System.out.println(i + " bottles of beer on the wall, " + i + " bottles of beer." +
	    		"\nTake one down and pass it around, " + (i -1) +  " bottles of beer on the wall.\n");
		}

		System.out.println("2 bottles of beer on the wall, 2 bottles of beer." +
	    		"\nTake one down and pass it around, 1 bottle of beer on the wall.\n");

		System.out.println("1 bottle of beer on the wall, 1 bottle of beer." +
	  		"\nTake one down and pass it around, no bottle of beer on the wall.\n");

		System.out.println("No more bottles of beer on the wall, no more bottles of beer." +
			"\nGo to the store and buy some more, 99 bottles of beer on the wall.");
	}
}[/PHP]

---

### Post by JupiterV2 on 2008-10-01
Since I still consider myself to be a newbie, I thought I would post my own results. I've just started browsing the forums again, so I'm a bit behind.

I thought it important that the lyrics be true by using a string for the number of bottles rather than a number.

To compile and run the code, copy and paste the following to a text file and save as '99bottles.cpp':
```

g++ -Wall -Wextra -O2 99bottles.cpp -o 99bottles
./99bottles

```

[PHP]#include <iostream>
#include <sstream>

/* Convert an integer to a string. Does not handle numbers greater than
 * 999. */
std::string itos(unsigned int num)
{
	const char* single_d[10] = {"zero", "one", "two", "three", "four", "five", 
		"six", "seven", "eight", "nine"};	
	const char* teen_d[10] = {"ten", "eleven", "twelve", "thirteen", "fourteen", 
		"fifteen", "sixteen", "seventeen", "eighteen", "nineteen"};
	const char* double_d[8] = {"twenty", "thirty", "forty", "fifty", 
		"sixty", "seventy", "eighty", "ninety"};
	
	int prod, remainder;
	
	std::ostringstream os;
	
	if( num == 0 ) return "zero";
	if( num > 999 ) num = 999;
	
	for(int x = 100; x >= 0; x /= 10)
	{
	    /* find the product of num divided by x (power of 10) and 
	     * retain the remainder for next iteration */
	     
		prod = num / x;
		remainder = num - (prod * x);

		if( prod > 0 )
		{
			switch(x)
			{
				case 1: os << single_d[prod]; break;
				case 10: 
					if( num > 19 ) 
					{
						os << double_d[prod - 2];
						if( remainder ) os << "-";
					}
					else 
					{
						os << teen_d[remainder];
						if( prod ) os << " ";
						remainder = 0;
					}
					break;
				case 100: 
					os << single_d[prod] << " hundred"; 
					if( remainder ) os << " "; 
					break;
			}
		}
		if( !(num = remainder) ) break;
	}
	
	return os.str();
}

int main() {
    for(unsigned int x = 99; x > 0;) {
        std::ostringstream os;
        
        os << itos(x) << " bottle" << (x == 1 ? " " : "s ") <<
            "of beer on the wall," << std::endl;
        os << itos(x) << " bottle" << (x == 1 ? " " : "s ") <<
            "of beer!" << std::endl;
        os << "take one down, pass it around," << std::endl;
        
        x--;
        os << itos(x) << " bottle" << (x  == 1 ? " " : "s ") <<
            "of beer on the wall!" << std::endl;
            
        std::cout << os.str() << std::endl;
    }
    
    return EXIT_SUCCESS;
}[/PHP]

Excerpt:

```

ninety-nine bottles of beer on the wall,
ninety-nine bottles of beer!
take one down, pass it around,
ninety-eight bottles of beer on the wall!

...

two bottles of beer on the wall,
two bottles of beer!
take one down, pass it around,
one bottle of beer on the wall!

one bottle of beer on the wall,
one bottle of beer!
take one down, pass it around,
zero bottles of beer on the wall!

```

---

### Post by Canis familiaris on 2008-10-07
I know it's a bit late but I just started learning Python today, so here's my code... :)

```
[color=#408080]*#!/usr/bin/python*[/color]
[color=#008000]**for**[/color] i [color=#AA22FF]**in**[/color] [color=#008000]range[/color]([color=#666666]99[/color],[color=#666666]2[/color],[color=#666666]-[/color][color=#666666]1[/color]):
	[color=#008000]**print**[/color] i, [color=#BA2121]"bottles of beer on the wall"[/color], i,[color=#BA2121]"""  bottles of beer.
	Take one down and pass it around, """[/color], i[color=#666666]-[/color][color=#666666]1[/color], [color=#BA2121]"bottles of beer on the wall."[/color], [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]
[color=#008000]**else**[/color]:
	[color=#008000]**print**[/color] [color=#BA2121]"""2 bottles of beer on the wall, 2 bottle of beer.
	Take one down and pass it around, 1 bottle of beer on the wall."""[/color], [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]	

	[color=#008000]**print**[/color] [color=#BA2121]"""1 bottle of beer on the wall, 1 bottle of beer.
	Take one down and pass it around, no more bottles of beer on the wall."""[/color], [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]

	[color=#008000]**print**[/color] [color=#BA2121]"""No more bottles of beer on the wall, no more bottles of beer. 
	Go to the store and buy some more, 99 bottles of beer on the wall"""[/color], [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]

```

And my favourite way which describes the advantage of Python I found over C/C++ :D
```
[color=#408080]*#!/usr/bin/python*[/color]

[color=#008000]**print**[/color] [color=#BA2121]"""99 bottles of beer on the wall, 99 bottles of beer.
Take one down and pass it around, 98 bottles of beer on the wall.

98 bottles of beer on the wall, 98 bottles of beer.
Take one down and pass it around, 97 bottles of beer on the wall.

97 bottles of beer on the wall, 97 bottles of beer.
Take one down and pass it around, 96 bottles of beer on the wall.

96 bottles of beer on the wall, 96 bottles of beer.
Take one down and pass it around, 95 bottles of beer on the wall.

95 bottles of beer on the wall, 95 bottles of beer.
Take one down and pass it around, 94 bottles of beer on the wall.

94 bottles of beer on the wall, 94 bottles of beer.
Take one down and pass it around, 93 bottles of beer on the wall.

93 bottles of beer on the wall, 93 bottles of beer.
Take one down and pass it around, 92 bottles of beer on the wall.

92 bottles of beer on the wall, 92 bottles of beer.
Take one down and pass it around, 91 bottles of beer on the wall.

91 bottles of beer on the wall, 91 bottles of beer.
Take one down and pass it around, 90 bottles of beer on the wall.

90 bottles of beer on the wall, 90 bottles of beer.
Take one down and pass it around, 89 bottles of beer on the wall.

89 bottles of beer on the wall, 89 bottles of beer.
Take one down and pass it around, 88 bottles of beer on the wall.

88 bottles of beer on the wall, 88 bottles of beer.
Take one down and pass it around, 87 bottles of beer on the wall.

87 bottles of beer on the wall, 87 bottles of beer.
Take one down and pass it around, 86 bottles of beer on the wall.

86 bottles of beer on the wall, 86 bottles of beer.
Take one down and pass it around, 85 bottles of beer on the wall.

85 bottles of beer on the wall, 85 bottles of beer.
Take one down and pass it around, 84 bottles of beer on the wall.

84 bottles of beer on the wall, 84 bottles of beer.
Take one down and pass it around, 83 bottles of beer on the wall.

83 bottles of beer on the wall, 83 bottles of beer.
Take one down and pass it around, 82 bottles of beer on the wall.

82 bottles of beer on the wall, 82 bottles of beer.
Take one down and pass it around, 81 bottles of beer on the wall.

81 bottles of beer on the wall, 81 bottles of beer.
Take one down and pass it around, 80 bottles of beer on the wall.

80 bottles of beer on the wall, 80 bottles of beer.
Take one down and pass it around, 79 bottles of beer on the wall.

79 bottles of beer on the wall, 79 bottles of beer.
Take one down and pass it around, 78 bottles of beer on the wall.

78 bottles of beer on the wall, 78 bottles of beer.
Take one down and pass it around, 77 bottles of beer on the wall.

77 bottles of beer on the wall, 77 bottles of beer.
Take one down and pass it around, 76 bottles of beer on the wall.

76 bottles of beer on the wall, 76 bottles of beer.
Take one down and pass it around, 75 bottles of beer on the wall.

75 bottles of beer on the wall, 75 bottles of beer.
Take one down and pass it around, 74 bottles of beer on the wall.

74 bottles of beer on the wall, 74 bottles of beer.
Take one down and pass it around, 73 bottles of beer on the wall.

73 bottles of beer on the wall, 73 bottles of beer.
Take one down and pass it around, 72 bottles of beer on the wall.

72 bottles of beer on the wall, 72 bottles of beer.
Take one down and pass it around, 71 bottles of beer on the wall.

71 bottles of beer on the wall, 71 bottles of beer.
Take one down and pass it around, 70 bottles of beer on the wall.

70 bottles of beer on the wall, 70 bottles of beer.
Take one down and pass it around, 69 bottles of beer on the wall.

69 bottles of beer on the wall, 69 bottles of beer.
Take one down and pass it around, 68 bottles of beer on the wall.

68 bottles of beer on the wall, 68 bottles of beer.
Take one down and pass it around, 67 bottles of beer on the wall.

67 bottles of beer on the wall, 67 bottles of beer.
Take one down and pass it around, 66 bottles of beer on the wall.

66 bottles of beer on the wall, 66 bottles of beer.
Take one down and pass it around, 65 bottles of beer on the wall.

65 bottles of beer on the wall, 65 bottles of beer.
Take one down and pass it around, 64 bottles of beer on the wall.

64 bottles of beer on the wall, 64 bottles of beer.
Take one down and pass it around, 63 bottles of beer on the wall.

63 bottles of beer on the wall, 63 bottles of beer.
Take one down and pass it around, 62 bottles of beer on the wall.

62 bottles of beer on the wall, 62 bottles of beer.
Take one down and pass it around, 61 bottles of beer on the wall.

61 bottles of beer on the wall, 61 bottles of beer.
Take one down and pass it around, 60 bottles of beer on the wall.

60 bottles of beer on the wall, 60 bottles of beer.
Take one down and pass it around, 59 bottles of beer on the wall.

59 bottles of beer on the wall, 59 bottles of beer.
Take one down and pass it around, 58 bottles of beer on the wall.

58 bottles of beer on the wall, 58 bottles of beer.
Take one down and pass it around, 57 bottles of beer on the wall.

57 bottles of beer on the wall, 57 bottles of beer.
Take one down and pass it around, 56 bottles of beer on the wall.

56 bottles of beer on the wall, 56 bottles of beer.
Take one down and pass it around, 55 bottles of beer on the wall.

55 bottles of beer on the wall, 55 bottles of beer.
Take one down and pass it around, 54 bottles of beer on the wall.

54 bottles of beer on the wall, 54 bottles of beer.
Take one down and pass it around, 53 bottles of beer on the wall.

53 bottles of beer on the wall, 53 bottles of beer.
Take one down and pass it around, 52 bottles of beer on the wall.

52 bottles of beer on the wall, 52 bottles of beer.
Take one down and pass it around, 51 bottles of beer on the wall.

51 bottles of beer on the wall, 51 bottles of beer.
Take one down and pass it around, 50 bottles of beer on the wall.

50 bottles of beer on the wall, 50 bottles of beer.
Take one down and pass it around, 49 bottles of beer on the wall.

49 bottles of beer on the wall, 49 bottles of beer.
Take one down and pass it around, 48 bottles of beer on the wall.

48 bottles of beer on the wall, 48 bottles of beer.
Take one down and pass it around, 47 bottles of beer on the wall.

47 bottles of beer on the wall, 47 bottles of beer.
Take one down and pass it around, 46 bottles of beer on the wall.

46 bottles of beer on the wall, 46 bottles of beer.
Take one down and pass it around, 45 bottles of beer on the wall.

45 bottles of beer on the wall, 45 bottles of beer.
Take one down and pass it around, 44 bottles of beer on the wall.

44 bottles of beer on the wall, 44 bottles of beer.
Take one down and pass it around, 43 bottles of beer on the wall.

43 bottles of beer on the wall, 43 bottles of beer.
Take one down and pass it around, 42 bottles of beer on the wall.

42 bottles of beer on the wall, 42 bottles of beer.
Take one down and pass it around, 41 bottles of beer on the wall.

41 bottles of beer on the wall, 41 bottles of beer.
Take one down and pass it around, 40 bottles of beer on the wall.

40 bottles of beer on the wall, 40 bottles of beer.
Take one down and pass it around, 39 bottles of beer on the wall.

39 bottles of beer on the wall, 39 bottles of beer.
Take one down and pass it around, 38 bottles of beer on the wall.

38 bottles of beer on the wall, 38 bottles of beer.
Take one down and pass it around, 37 bottles of beer on the wall.

37 bottles of beer on the wall, 37 bottles of beer.
Take one down and pass it around, 36 bottles of beer on the wall.

36 bottles of beer on the wall, 36 bottles of beer.
Take one down and pass it around, 35 bottles of beer on the wall.

35 bottles of beer on the wall, 35 bottles of beer.
Take one down and pass it around, 34 bottles of beer on the wall.

34 bottles of beer on the wall, 34 bottles of beer.
Take one down and pass it around, 33 bottles of beer on the wall.

33 bottles of beer on the wall, 33 bottles of beer.
Take one down and pass it around, 32 bottles of beer on the wall.

32 bottles of beer on the wall, 32 bottles of beer.
Take one down and pass it around, 31 bottles of beer on the wall.

31 bottles of beer on the wall, 31 bottles of beer.
Take one down and pass it around, 30 bottles of beer on the wall.

30 bottles of beer on the wall, 30 bottles of beer.
Take one down and pass it around, 29 bottles of beer on the wall.

29 bottles of beer on the wall, 29 bottles of beer.
Take one down and pass it around, 28 bottles of beer on the wall.

28 bottles of beer on the wall, 28 bottles of beer.
Take one down and pass it around, 27 bottles of beer on the wall.

27 bottles of beer on the wall, 27 bottles of beer.
Take one down and pass it around, 26 bottles of beer on the wall.

26 bottles of beer on the wall, 26 bottles of beer.
Take one down and pass it around, 25 bottles of beer on the wall.

25 bottles of beer on the wall, 25 bottles of beer.
Take one down and pass it around, 24 bottles of beer on the wall.

24 bottles of beer on the wall, 24 bottles of beer.
Take one down and pass it around, 23 bottles of beer on the wall.

23 bottles of beer on the wall, 23 bottles of beer.
Take one down and pass it around, 22 bottles of beer on the wall.

22 bottles of beer on the wall, 22 bottles of beer.
Take one down and pass it around, 21 bottles of beer on the wall.

21 bottles of beer on the wall, 21 bottles of beer.
Take one down and pass it around, 20 bottles of beer on the wall.

20 bottles of beer on the wall, 20 bottles of beer.
Take one down and pass it around, 19 bottles of beer on the wall.

19 bottles of beer on the wall, 19 bottles of beer.
Take one down and pass it around, 18 bottles of beer on the wall.

18 bottles of beer on the wall, 18 bottles of beer.
Take one down and pass it around, 17 bottles of beer on the wall.

17 bottles of beer on the wall, 17 bottles of beer.
Take one down and pass it around, 16 bottles of beer on the wall.

16 bottles of beer on the wall, 16 bottles of beer.
Take one down and pass it around, 15 bottles of beer on the wall.

15 bottles of beer on the wall, 15 bottles of beer.
Take one down and pass it around, 14 bottles of beer on the wall.

14 bottles of beer on the wall, 14 bottles of beer.
Take one down and pass it around, 13 bottles of beer on the wall.

13 bottles of beer on the wall, 13 bottles of beer.
Take one down and pass it around, 12 bottles of beer on the wall.

12 bottles of beer on the wall, 12 bottles of beer.
Take one down and pass it around, 11 bottles of beer on the wall.

11 bottles of beer on the wall, 11 bottles of beer.
Take one down and pass it around, 10 bottles of beer on the wall.

10 bottles of beer on the wall, 10 bottles of beer.
Take one down and pass it around, 9 bottles of beer on the wall.

9 bottles of beer on the wall, 9 bottles of beer.
Take one down and pass it around, 8 bottles of beer on the wall.

8 bottles of beer on the wall, 8 bottles of beer.
Take one down and pass it around, 7 bottles of beer on the wall.

7 bottles of beer on the wall, 7 bottles of beer.
Take one down and pass it around, 6 bottles of beer on the wall.

6 bottles of beer on the wall, 6 bottles of beer.
Take one down and pass it around, 5 bottles of beer on the wall.

5 bottles of beer on the wall, 5 bottles of beer.
Take one down and pass it around, 4 bottles of beer on the wall.

4 bottles of beer on the wall, 4 bottles of beer.
Take one down and pass it around, 3 bottles of beer on the wall.

3 bottles of beer on the wall, 3 bottles of beer.
Take one down and pass it around, 2 bottles of beer on the wall.

2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around, 1 bottle of beer on the wall.

1 bottle of beer on the wall, 1 bottle of beer.
Take one down and pass it around, no more bottles of beer on the wall.

No more bottles of beer on the wall, no more bottles of beer. 
Go to the store and buy some more, 99 bottles of beer on the wall."""[/color]

```

---

### Post by Flynn555 on 2008-10-07
here is my solution...

```


/*Author:    Flynn555
 *Purpose:   As a part of the Ubuntuforums.org programming 
 *           contest, this program prints the lyrics to the 
 *           song "99 bottles of beer on the wall"
 *Language:  C++
 */

#include <iostream>
#include <string>
using namespace std;

//function prototypes
void sing();

int main()
{
   sing();

}//endmain

void sing(){
	for (int beers = 99; beers >= 0; beers--){
        switch(beers){
           case 0:  cout << "No more bottles of beer on the wall, "
                         << "no more bottles of beer.\n"
                         << "Go to the store and buy some more, "
                         << "99 bottles of beer on the wall!\n\n";
                         break;
           case 1:  cout << beers << " bottle of beer on the wall, " 
                         << beers << " bottle of beer.\n"
                         << "Take one down pass it around, "
                         << beers-1 << " bottles of beer on the wall!\n\n";
                         break;
           case 2:  cout << beers << " bottles of beer on the wall, " 
                         << beers << " bottles of beer.\n"
                         << "Take one down pass it around, "
                         << beers-1 << " bottle of beer on the wall!\n\n";
                         break;
           default: cout << beers << " bottles of beer on the wall, " 
                         << beers << " bottles of beer.\n"
                         << "Take one down pass it around, "
                         << beers-1 << " bottles of beer on the wall!\n\n";
                         break;
       }//endswitch
    }//endfor
}//endsing


```

edit: just realized i included string for some reason.

---

### Post by dodle on 2008-10-11
I'm a little late for this, but am a beginner programmer and wanted to do the challenges.  So here is my input in Python.[PHP]# 99 bottles of beer on the wall

bottles = 99

# Subtracts 1 from bottles for each verse
def take_one_down(bottles):
    bottles = bottles - 1
    return bottles

# Verse layout until only 1 bottle left
def verse(bottles):
    print "\n%s bottles of beer on the wall, %s bottles of beer.\n\
Take one down and pass it around, %s bottles of beer on the wall." % (bottles, bottles, bottles - 1)

# Verse layout for 1 bottle left
def verse_1bottle(bottles):
    print "\n%s bottle of beer on the wall, %s bottle of beer.\n\
Take one down and pass it around, no more bottles of beer on the wall." % (bottles, bottles)


beer_loop = True
while beer_loop == True:
    if bottles > 1:
        verse(bottles)
        bottles = take_one_down(bottles)
    
    elif bottles == 1:
        verse_1bottle(bottles)
        bottles = take_one_down(bottles)

    elif bottles == 0:
        print "\nNo more bottles of beer on the wall, no more bottles of beer.\n\
Go to the store and buy some more, 99 bottles of beer on the wall."    
        beer_loop = False[/PHP]

---

### Post by alberto ferreira on 2008-10-15
No one has done it in bash, so, here it is xD
This script has the advantage of replacing the variable "n" at the beginning of the script so that you can have a lyric with bazillions of bottles of beer! :D
[php]#! /bin/bash

n=99
quote_n=$n

bottles(){
case "$n" in
        1) bottles="1 bottle of beer";;
        0) bottles="no more bottles of beer";;
        *) bottles="$n bottles of beer";;
esac
}

clear
until [ "$n" = "0" ];do
bottles
echo "$bottles on the wall, $bottles."
n=$(( n -1 ))
bottles
echo "Take one down and pass it around, $bottles on the wall.
"
done
#Last paragraph
echo "No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, $quote_n bottles of beer on the wall."



[/php]
Please comment

---

### Post by ferty on 2008-10-17
Hi,I thought I`d like to have a go at the biginner challenges,starting with this one using C.



```


#include<stdio.h>

int main()


{
int botts=99;

for (;botts>1;)
	{
		printf("%d bottles of beer on the wall, %d bottles of beer.\n",botts,botts);
		if(botts==2)
		printf("Take one down and pass it around, %d bottle of beer on the wall.\n\n",--botts);
		else
		printf("Take one down and pass it around, %d bottles of beer on the wall.\n\n",--botts);
	}

	printf("%d bottle of beer on the wall, %d bottle of beer.\n",botts,botts);
	printf("Take one down and pass it around, no more bottles of beer on the wall.\n\n");
	printf("No more bottles of beer on the wall, no more bottles of beer.\n");
	printf("Go to the store and buy some more, 99 bottles of beer on the wall.\n");

	return(0);
```

---

### Post by panthius on 2008-10-20
I am another late comer to the party here.  Here is my C++ version of the program.  It was a lot smaller before the comments.  Not sure if this is any good or not, but it is what I thought of when reading the challenge.  

Enjoy!

[php]#include <iostream>
using namespace std;

// need to declare my function before it is called:
void startDrinking(int iBottleCount);

int main() {
    // Set the starting number of beers to drink:
    int bottleCount = 99;

    // Start drinking the bottles of beer, and only come back here when there are no more bottles of beer:
    startDrinking(bottleCount);

    // We must be out of beer, so what do we do now?
    cout << "No more bottles of beer on the wall, no more bottles of beer.\n";
    cout << "Go to the store and buy some more, " << bottleCount << " bottles of beer on the wall.\n";

    // We are done:
    return 0;
}

// This function will be called over and over.  Could have used a loop, but what fun is that?
void startDrinking(int iBottleCount) {
    // Save myself some typing by declaring astring:
    string onthewall=" of beer on the wall, ";

    // For the first line, there are only two cariations:
    if (iBottleCount > 1) {
        // More than 1, then we display plural bottles:
        cout << iBottleCount << " bottles" << onthewall << iBottleCount << " bottles";
    } else if (iBottleCount == 1) {
        // Equal 1 and we use singular bottles:
        cout << iBottleCount << " bottle" << onthewall << iBottleCount << " bottle";
    }

    // Always display the following at this point:
    cout << " of beer.\nYou take one down and pass it around, ";

    // Now determine what do for the rest of the 2nd line:
    if (--iBottleCount > 1) {
        // More than 1 then we use plural bottles:
        cout << iBottleCount << " bottles";
    } else if (iBottleCount == 1) {
        // Only 1 then we just have a single bottle:
        cout << iBottleCount << " bottle";
    } else {
        // Less than 1, then we took the last bottle and return out:
        cout << "no more bottles of beer on the wall.\n\n";
        return;
    }

    // Always display the following to finish the second line:
    cout << " of beer on the wall.\n\n";

    // Let's start drinking some more, passing in the new number of bottles:
    startDrinking(iBottleCount);
}
[/php]

---

### Post by ewproctor on 2008-10-29
I'm new too, so here is my python...

```

#!/usr/bin/env python
# ninety-nine
#

def sing(number):
    while(number >1):
        if(number>2):
            bottlestring = "%s bottles" % str(number)
            nextstring = "%s bottles" % str(number-1)
        elif(number >1):
            bottlestring = "%s bottles" % str(number)
            nextstring = "%s bottle" % str(number-1)
        print "%s of beer on the wall, %s of beer, if one of those bottles should happen to fall, %s of beer on the wall!" % (bottlestring, bottlestring, nextstring)
        number-=1
    print "1 bottle of beer on the wall, 1 bottle of beer, if this bottle should happen to fall, there are no more bottles of beer on the wall!  Go to the store, buy some more, 99 bottles of beer on the wall!"

sing(99)

```

---

### Post by Smygis on 2008-10-29
```

#!/usr/bin/env python
# coding: UTF-8

BottlesOfBeer = "\n\
    %s%s of beer on the wall, %s%s of beer. \n\
    %s, %s%s of beer on the wall."

PassOrBuy = ("Go to the store and buy some more", \
    "Take one down and pass it around")

bottles = lambda n: ((n, " bottles") if n != 1 else (n, " bottle")) \
  if n > 0 else (("","no more bottles") if n == 0 else (99, " bottles"))

print "\n".join([BottlesOfBeer % (bottles(i)*2 + (PassOrBuy[bool(i)],) \
         + bottles(i-1)) for i in xrange(99, -1, -1)])

```

That is **four** lines of actual code. But i dont think im a beginner.

---

### Post by JuhaK on 2008-11-01
Hello,
I have wanted for long time to be able to create small programs with C or C++ and now I decided to learn some with these challenges. I have earlier experience with PHP, so I am not total beginner in programming :) Anyways, this is my version in C and I learned a lot with it. For example how do I pass parameter for a program :) :)
[PHP]
#include <stdio.h>
int main(int argc, char *argv[])
{
    int num_bottles = (argc > 1)? atoi(argv[1]):99; // Has user passed a parameter? if yes then value of a parameter is the number of bottles
    int original_bottle_count = num_bottles;

    for (num_bottles; num_bottles >= 0; num_bottles--) {
        switch(num_bottles) {
            case 0:
                printf("No more bottles of beer on the wall, no more  bottles of beer.\nGo to the store and buy some more, %d bottles of beer on the wall.\n\n",original_bottle_count);
                break;
            case 1:
                printf("%d bottle of beer on the wall, %d bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n\n",num_bottles,num_bottles);
                break;
            case 2:
                printf("%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottle of beer on the wall.\n\n",num_bottles,num_bottles,num_bottles-1);
                break;
            default:
                printf("%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottles of beer on the wall.\n\n",num_bottles,num_bottles,num_bottles-1);
                break;
        }
    }
    return 0;
}[/PHP]

---

### Post by CLomax on 2008-12-31
[PHP]#include <stdio.h>

int main()
{
      int b, i;

   b = 99;
   i = 98;

 for(b=99;b>1;b--)
 {
   printf("%d bottles of beer on the wall %d bottles of beer.\nTake one down and pass it around, %d bottles of beer on the wall.\n\n",b,b,i--);
 }
 return(0);
}[/PHP]

Here's my C code... not really that good but it does the job and it weighs in at about 256 bytes.

---

### Post by pp. on 2008-12-31
> **CLomax said:**
> it does the job

Have you looked at the last two "verses" your program has to produce, i.e. at #bottles=1 and #bottles=0?

---

### Post by CLomax on 2008-12-31
> **pp. said:**
> Have you looked at the last two "verses" your program has to produce, i.e. at #bottles=1 and #bottles=0?

Woops :D
And I thought I manage to reduce it further than others did. I'll look into that. Thanks.

---

### Post by bgs100 on 2009-01-24
[PHP]#!/usr/bin/python
beer=99
#normal stuff, 99 to 3
while beer > 2: 
	print "%i bottles of beer on the wall, %i bottles of beer, take one down, pass it around, %i bottles of beer on the wall\n" % (beer,beer,beer-1)
	beer=beer-1
#Ending with correct grammar
print "2 bottles of beer on the wall, 2 bottles of beer.\nTake one down and pass it around, 1 bottle of beer on the wall.\n" 
print "1 bottle of beer on the wall, 1 bottle of beer.\nTake one down and pass it around, no more bottles of beer on the wall.\n"
print "No more bottles of beer on the wall, no more bottles of beer.  Go to the store and buy some more, 99 bottles of beer on the wall."
[/PHP]
I am a python noobie.  Edited beforehand for correct grammar on 1 and 2

---

### Post by eightmillion on 2009-01-24
Here's my python one liner:

```
python -c 'bo,be,ta,wa,no="bottle","of beer","Take one down and pass it around","on the wall",range(99,0,-1); print "".join([ "%s %s%s %s %s,\n%s %s%s %s.\n%s, %s %s%s %s %s.\n\n" % (num,bo,["s",""][num==1],be,wa,num,bo,["s",""][num==1],be,ta,[num-1,"no more"][num-1==0],bo,["s",""][num-1==1],be,wa) for num in no ] + ["No more %ss %s %s, no more %ss %s.  Go to the store and buy some more, 99 %ss %s %s." % (bo,be,wa,bo,be,bo,be,wa)] )'
```

Edit: Also, a version for bash:
```
bo="bottle";be="of beer";ta="Take one down and pass it around";wa="on the wall";i=99;while [ "$i" != 0 ]; do printf "$i $bo`[ $i != 1 ] && echo s` $be $wa,\n$i $bo`[ $i != 1 ] && echo s` $be.\n$ta, `[ $((i-1)) != 0 ] && echo $((i-1)) || echo "no more"` $bo`[ $i != 2 ] && echo s` $be.\n\n"  ;i=$((i-1));done;  printf "No more ${bo}s $be $wa,\nno more ${bo}s $be.\nGo to the store and buy some more, 99 ${bo}s $be $wa.\n"
```

---

### Post by baizon on 2009-05-09
Java:
```
public class NinetyNineBottles {

	private static void bottlesCounter(int bottles) {
		for (; bottles > 0; bottles--) {
			if (bottles == 1) {
				System.out.println(bottles + " bottle of beer on the wall, " + bottles + " bottle of beer.");
				System.out.println("Take one down and pass it around, no more bottles of beer on the wall.");
			} else {
				System.out.println(bottles + " bottles of beer on the wall, " + bottles + " bottles of beer.");
				System.out.println("Take one down and pass it around, " + (bottles - 1) + " bottles of beer on the wall.");
			}
		}
	}
	
	public static void main(String[] args) {
		bottlesCounter(99);
	}
}
```

---

### Post by xfice on 2013-05-25
Here is my answer in the first problem. any comments? I used C.

#include<stdio.h>

int qty;

main(){
  for(qty=99;qty!=1;qty--){
  printf("%d bottles of beer on the wall, %d bottles of beer.\n", qty,qty);
  printf("Take one down and pass it around, %d bottles of beer on the wall.\n", qty-1);
                }
    if(qty=1){
    printf("%d bottle of beer on the wall, %d bottle of beer.\n", qty, qty);
    printf("Take one down and pass it around, no more bottles of beer on the wall.\n");

    printf("No more bottles of beer on the wall, no more bottles of beer. \nGo to the store and buy some more, 99 bottles of beer on the wall.\n");
  
          }
      }

---

