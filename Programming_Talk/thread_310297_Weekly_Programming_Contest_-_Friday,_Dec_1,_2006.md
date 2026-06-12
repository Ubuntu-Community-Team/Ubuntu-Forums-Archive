---
title: "Weekly Programming Contest - Friday, Dec 1, 2006"
date: 2006-12-01
forum: Programming Talk
---

### Post by po0f on 2006-12-01
Welcome to the first ever **_Weekly Programming Contest_**!

Ok, first the rules:
[list]
[*]Any language is allowed.  (No swearing though, please :))
[*]Extensive use of external libraries is frowned upon, and may be grounds for disqualification.
[*]Submissions must meet the requirements and must be programmed within any limitations imposed posted on the contest page.  
[*]All submissions for the contest must be submitted six (6) days after the initial posting of the contest.  (For example, this contest starts 1 Dec, submissions in by 6 Dec)  The final day will be for community review.
[*]A winner will be posted after community review; the winner gets to post the contest for the next week.  If the winner decides to not post a new contest, the previous winner may.  If the previous winner doesn't post a new contest in a timely fashion, then I'll post one.  :twisted: 
[*]All code will be considered [public domain](http://creativecommons.org/licenses/publicdomain/), unless the submitter chooses to release it under a different license.
[/list]
(Rules subject to change, since I kinda made them up on the spot.)

**Objective**:
Write a program that takes as input one string, and outputs the string backwards.

---

### Post by kthakore on 2006-12-01
yeehaw let the battle begin! I think we should have awards, I proposed:

-Most elegant
-Fastest program run time
-smallest space taken by program
-least line of codes
-and funniest!!!
-

---

### Post by coder_ on 2006-12-01
In Python.  Run as "python foo.py MYSTRING"
```
import sys;print sys.argv[1][::-1]
```

How do we determine a winner for this one?

---

### Post by po0f on 2006-12-01
coder_,

I meant a string like "hello world!", but I wasn't more specific.  :)

As for determining a winner, "points" will be awarded for creativity (I still don't understand how your's works :)), brevity, and other stuff.  Mainly creativity, I think this is more for getting people to code in ways that maybe others haven't seen before.

---

### Post by coder_ on 2006-12-01
It works if you pass quotes, like "hello world" as you said above that it had to do.
python foo.py "hello world"



Edit: Unless you mean without quotes, where each word is a different parameter.  It'd work like this (Yay for ugly scrunched up code! :P):
```

import sys;sys.argv.reverse()
for i in range(sys.argv.__len__()):
 if (sys.argv[-1]!=sys.argv[i]): sys.stdout.write(sys.argv[i][::-1]+' ')

```
python foo.py hello world



Sorry, I wasn't quite sure what you meant, if it had to be able to do it when passed "hello world" or when passed hello and then world.  So I just wrote the other one. :P

And wee!  To put it back to normal:  python foo.py $(python foo.py hello world) :p

---

### Post by crag277 on 2006-12-01
Here's my solution in C++.

make contest1
./contest1

---

### Post by ghostdog74 on 2006-12-01
```

#> echo "string" | python -c "import sys; print ''.join(reversed(sys.stdin.read()))"

```

or

```

#> echo "string"  | python -c "import sys; print sys.stdin.read()[::-1]"

```

---

### Post by imaiden22 on 2006-12-01
I'm liking the official look guys, and way to set the rules proof, this is gonna be fun times ahead!

Oh and this is just a suggestion, but what about accompanying a little written description of how your program exactly works, for all the newer programmers out there to pick up on the little ins and outs of languages like ruby, python, java, c++, etc.


**EDIT: Oh and po0f, where's my credit for starting this thing?? hahaha**

---

### Post by po0f on 2006-12-01
You guys have to stop, you're putting my (obviously meager) Python skills to shame.  :)

I think this will also be an excellent way to expose people to different programming languages.  I'm eagerly awaiting a Ruby or Common Lisp solution.

[EDIT]

And just to clarify, the input can be passed as arguments or be entered programmatically like crag277's solution.

---

### Post by emix on 2006-12-01
> **po0f said:**
> **Objective**:
Write a program that takes as input one string, and outputs the string backwards.

Here is my solution in C:
```
#include <stdio.h>

void reverse(char *c) {
	if (*c != '\0')
		reverse(c+1);
	printf("%c", *c);
}

int main(int argc, char **argv) {
	if (argc < 2) return 1;
	reverse(argv[1]);
	printf("\n");
	return 0;
}
```

Recursion is very elegant ;)

---

### Post by Arndt on 2006-12-01
> **po0f said:**
> Welcome to the first ever **_Weekly Programming Contest_**!


**Objective**:
Write a program that takes as input one string, and outputs the string backwards.

```
$ echo 'Hello world!' | sed 's/$/\t/;:a;s/\(.\)\t\(.*\)/\t\2\1/;t a;s/\t//'
!dlrow olleH
```

---

### Post by lnostdal on 2006-12-01
> **po0f said:**
> 
**Objective**:
Write a program that takes as input one string, and outputs the string backwards.

```

lars@blackbox:~/programming/lisp/ubuntu-contest$ cat reverese-string.lisp
#!/home/lars/programming/sbcl/bin/sbcl --noinform

(if (third *posix-argv*)
    (format t "Reverse of ~S is ~S~%" (third *posix-argv*) (reverse (third *posix-argv*)))
    (format t "Usage: ~A \"String to reverse\"~%" (second *posix-argv*)))

```

```

lars@blackbox:~/programming/lisp/ubuntu-contest$ ./reverese-string.lisp
Usage: ./reverese-string.lisp "String to reverse"

```

```

lars@blackbox:~/programming/lisp/ubuntu-contest$ ./reverese-string.lisp "Hello World"
Reverse of "Hello World" is "dlroW olleH"

```

edit:
here is a version that reads from STDIN:

```

#!/home/lars/programming/sbcl/bin/sbcl --noinform

(write-line "Enter a string so I can reverse it for you: ")
(write-line (reverse (read-line)))

```

```

lars@blackbox:~/programming/lisp/ubuntu-contest$ ./reverese-string.lisp
Enter a string so I can reverse it for you:
Hello there! What's up?
?pu s'tahW !ereht olleH

```

edit2:
but one usually develop software in the REPL when doing Lisp:
```

(defun readAndReverse ()
  (write-line "Enter a string so I can reverse it for you: ")
  (write-line (reverse (read-line))))

....

cl-user> (readAndReverse)
Enter a string so I can reverse it for you: 
Hello World!
!dlroW olleH

```

---

### Post by public_void on 2006-12-01
```
#define i if
#define d do
#define n int 
#define h char
#define m main
#define w while 
#define p printf 
#define r return
#include <stdio.h>
n m(n a,h*g[]){i
(a>1){h*c=g[1];w
(*c!='\0'){c++;}
d{c--;p("%c",*c)
;}w(c!=g[1]);r 
0;}r 1;}
```

The unobfuscated version
```
#include <stdio.h>

int main(int argc, char *argv[]) {
  if (argc > 1) {
    char *input = argv[1];
    while(*input != '\0') {
      input++;
    }
    do {
      input--;
      printf("%c", *input);
    } while (input != argv[1]);
    return 0;
  }
  return 1;
}
```

Its written in C, and could be smaller if I wrote a make file.

Works by incrementing a pointer until it points to the string terminator in the argument. Then it decrements the same pointer and prints the character at that pointer.

EDIT: Well spotted Arndt. In the second while loop I compared the value at the two pointers. I should have compared the pointers themselves. Fixed it now.

---

### Post by Arndt on 2006-12-01
> **public_void said:**
> ```
#define i if
#define d do
#define n int 
#define h char
#define m main
#define w while 
#define p printf 
#define r return
#include <stdio.h>
n m(n a,h*g[]){i
(a>1){h*c=g[1];w
(*c!='\0'){c++;}
d{c--;p("%c",*c)
;}w(*c!=*g[1]);r 
0;}r 1;}
```

The unobfuscated version
```
#include <stdio.h>

int main(int argc, char *argv[]) {
  if (argc > 1) {
    char *input = argv[1];
    while(*input != '\0') {
      input++;
    }
    do {
      input--;
      printf("%c", *input);
    } while (*input != *argv[1]);
    return 0;
  }
  return 1;
}
```

Its written in C, and could be smaller if I wrote a make file.

Works by incrementing a pointer until it points to the string terminator in the argument. Then it decrements the same pointer and prints the character at that pointer.

But,

$ make rev
cc     rev.c   -o rev
$ ./rev abcde
edcba
$ ./rev ababa
a
$ ./rev aetwtwtd
dtwtwtea
$ ./rev aetwtawtd
dtwa

---

### Post by Arndt on 2006-12-01
> **emix said:**
> Here is my solution in C:
```
#include <stdio.h>

void reverse(char *c) {
	if (*c != '\0')
		reverse(c+1);
	printf("%c", *c);
}

int main(int argc, char **argv) {
	if (argc < 2) return 1;
	reverse(argv[1]);
	printf("\n");
	return 0;
}
```

Recursion is very elegant ;)

The program will output a '\0' if called with an empty string as input.

Finding errors in others' programs is even more fun than writing my own...

---

### Post by daz4126 on 2006-12-01
in ruby:

> word = gets.chomp
puts work.reverse

---

### Post by emix on 2006-12-01
> **Arndt said:**
> The program will output a '\0' if called with an empty string as input.

Finding errors in others' programs is even more fun than writing my own...

And where is the error?

---

### Post by DeadEyes on 2006-12-01
> **daz4126 said:**
> in ruby:
word = gets.chomp
puts work.reverse

oops word/work :)

---

### Post by pichalsi on 2006-12-01
> **DeadEyes said:**
> oops word/work :)
wow ruby looks so easy :)

---

### Post by public_void on 2006-12-01
Fixed it now, with an explanation why it was wrong.

---

### Post by daz4126 on 2006-12-01
In ruby (with some explanation and, hopefully, no errors this time):

```
# comments start with a hash/pound symbol 
**puts "please enter a word"**
# puts outputs strings to the screen
**word = gets.chomp**
# gets will get a string from the user
# the chomp method gets rid of the carriage return that the user entered
# now we have a string held in the variable called 'word'
**puts word**
# this will output our word to the scren
**puts word.reverse**
# reverse is a string method and will write the word backwards

# run this program by saving the code as 'reverse.rb'
# then type ruby reverse.rb in a terminal window
```

DAZ

---

### Post by Tomosaur on 2006-12-01
In java:
```

class StringFlip{
        public static void main(String args[]){
                for(int i = args.length -1; i >= 0; i--){
                        char out[] = args[i].toCharArray();
                        for(int c = out.length - 1; c >= 0; c--){
                                System.out.print(out[c]);
                        }
                        System.out.print(" ");
                }
                System.out.println();
        }
}

```

How to use:
java StringFlip Hello there old chap!

No quotes required, string can be as long as you like :)

---

### Post by Ramses de Norre on 2006-12-01
```
import java.util.Scanner;
class ReverseDriver
{
	static String Reverse(String s)
	{
		String reverse="";
		for(int i=1;i<=s.length();i++)
		    reverse+=s.charAt(s.length()-i);
		return reverse;
	}
	public static void main(String[] args)
	{
		Scanner keys=new Scanner(System.in);
		System.out.print("Give string to reverse: ");
		String s=keys.nextLine();
		System.out.println("Reversed string: "+Reverse(s));
	}
}
```

---

### Post by Zdravko on 2006-12-01
```

#include <iostream>
#include <algorithm>
#include <sstream>
using namespace std;

int main(int c, char* v[]) {
    string s;
    c > 1 ? getline(istringstream(v[1]), s) : getline(cin, s);
    reverse(s.begin(), s.end());
    cout << s;
    return 0;
}

```
Now, do I win the contest? This is the most elegant way to solve the problem in C++.

---

### Post by whoismilan on 2006-12-01
Don't know if this should even qualify as a new entry in the contest, just showing that you can do it all in one line in Ruby also:

```
puts gets.chop.reverse
```

...although I think the way daz4126 did it would be better both when you show someone how to do stuff in Ruby, and if you want to expand our little program to actually do something.

Fun idea on the contest btw :)

---

### Post by lnostdal on 2006-12-01
well, if it's ok to do it without prompts of any kind:

```
(reverse (read-line))
```

---

### Post by public_void on 2006-12-01
Just to be fancy, I've written it in Prolog.
```
reverse_string(String):- 
    string_to_list(String, List),
    reverse(List, NewList),
    writef(NewList, '~c')
```
And the really short one liner.
```
r(S):-string_to_list(S,L),reverse(L,N),writef(N,'~c').
```

---

### Post by tomchuk on 2006-12-01
Perl
```

#!/usr/bin/perl
print scalar reverse "\n@ARGV"

```

---

### Post by ocertain on 2006-12-01
Sounds like a classic C stack program to me. Push the string (array of char) on the stack one char at a time, pop the char back off into another string and voila - it's reversed.

---

### Post by Tomosaur on 2006-12-01
> **ocertain said:**
> Sounds like a classic C stack program to me. Push the string (array of char) on the stack one char at a time, pop the char back off into another string and voila - it's reversed.

Do it then :P

---

### Post by lloyd mcclendon on 2006-12-01
1 statment

```
public class StringReverser {

	public static void main(String[] args) {
		System.out.println(
				(args.length > 1)
					? new StringBuilder(args[0]).reverse().toString()
					: "usage: java " + StringReverser.class.getSimpleName() + " string_to_reverse");
	}
}
```

---

### Post by lloyd mcclendon on 2006-12-01
> **Zdravko said:**
> ```

#include <iostream>
#include <algorithm>
#include <sstream>
using namespace std;

int main(int c, char* v[]) {
    string s;
    c > 1 ? getline(istringstream(v[1]), s) : getline(cin, s);
    reverse(s.begin(), s.end());
    cout << s;
    return 0;
}

```
Now, do I win the contest? This is the most elegant way to solve the problem in C++.


yeah that is pretty good, my solution is like that translated basically

but much respect for busting out the ternary operator and actually understanding the clusterfuck that is I/O in c++

---

### Post by po0f on 2006-12-01
I thought that since this was a fairly simple contest that it would be easier to pick a winner; it's only day two and I see a couple that have made me say "Ooh!" so far.

[EDIT]

Day *one*, really, getting a little ahead of myself.  :)

---

### Post by xtacocorex on 2006-12-01
Here is the solution in FORTRAN 90.

```

! UBUNTU PROGRAMMING CONTEST 1
! WRITTEN BY: ROBERT WOLTERMAN 12/1/2006

PROGRAM STRING_REVERSE

        IMPLICIT NONE
        ! VARIABLE DECLARATION
        CHARACTER(100) :: SINP, SOUTP
        INTEGER :: SLEN, I, J

        ! GET USER INPUT
        WRITE(*,*) "ENTER STRING TO REVERSE: "
        READ(*,*) SINP

        ! FIND THE LENGTH OF THE STRING
        SLEN = LEN_TRIM(SINP)

        ! REVERSE THE STRING
        DO I = SLEN, 1, -1
                J = SLEN - I + 1
                SOUTP(J:J) = SINP(I:I)
        END DO

        ! OUTPUT THE REVERSED STRING
        WRITE(*,5) SOUTP(1:SLEN)

        ! FORMAT STATEMENTS
        5 FORMAT (100(1A))

        ! END PROGRAM
        STOP

END PROGRAM STRING_REVERSE

```

---

### Post by rappo on 2006-12-01
```
public static void main(String[]args) {
 String phrase="ubuntu", end="";
 int l=phrase.length();

 for(int i=0; i<l; i++)
  end+=phrase.charAt((l-1)-i);

 System.out.println(end);
}
```

There's my version in Java (without using the pre-made reversals).

---

### Post by Peepsalot on 2006-12-01
I wrote mine in javascript
```
javascript:s=prompt();t='';i=s.length;while(i--)t+=s.charAt(i);alert(t);
```
Just paste the above into your browsers address bar and press enter.

Can one user submit two entries if they are in different languages?

---

### Post by Peepsalot on 2006-12-02
Well, I'm going to submit my second program anyways, cause I think it's cool, and I learned a bit from trying it this way.  Programmed in the language of... the command line ;) (or bash script if you will)
```
#!/bin/bash
echo $1|grep -o .|tac|tr -d '\n' && echo
```

---

### Post by slimdog360 on 2006-12-02
> **po0f said:**
> I thought that since this was a fairly simple contest that it would be easier to pick a winner; it's only day two and I see a couple that have made me say "Ooh!" so far.

[EDIT]

Day *one*, really, getting a little ahead of myself.  :)

maybe set up a panel of judges. Maybe this panel can change from week to week and make it so that the judges for that week cant enter the comp. Also maybe setup a criteria for the judges.

---

### Post by emix on 2006-12-02
> **ocertain said:**
> Sounds like a classic C stack program to me. Push the string (array of char) on the stack one char at a time, pop the char back off into another string and voila - it's reversed.
That is what I [did](http://ubuntuforums.org/showpost.php?p=1830548&postcount=10) using the implicit recursion stack ;)

---

### Post by addicted68098 on 2006-12-02
Ehh, I could only get it to work for the word racecar!

I am not sure if python would be valid, I am using the len function, but I don't think that counts as a external library.
I did avoid the revrse function. 
```

def reverseatize(input):
  chars = len(input)
  output = ""
  for a in range(chars):
    output = output+input[chars-1-a]
  return output
print reverseatize('test')
print "tset?"
i = raw_input('Reverse a string?')
print reverseatize(i)

```

Its only 5 lines long? Do I win?

---

### Post by Jessehk on 2006-12-02
```

// By Jessehk on Dec 2, 2006

#include <iostream>
#include <string>
#include <vector>

std::string reverse( const std::string &str ) {
    std::string result( "" );
    std::string::const_reverse_iterator iter;

    for ( iter = str.rbegin(); iter != str.rend(); ++iter )
        result += *iter;

    return result;
}

std::string join( const std::vector<std::string> vs,
                  const std::string &joiner ) {
    
    std::string result( "" );
    std::vector<std::string>::const_iterator iter;

    for ( iter = vs.begin(); iter != vs.end(); ++iter )
        result += (*iter + (iter + 1 == vs.end() ? "" : joiner ) );

    return result;
}

int main( int argc, char *argv[] ) {
    std::vector<std::string> args( argv + 1, argv + argc );
    std::cout << reverse( join( args, " " ) ) << std::endl;
}
    

```

---

### Post by JmSchanck on 2006-12-02
```

## WPC_1.py
## Author: John Schanck
## Purpose: Reverse a string using a clever method.

import sys
text = [ord(i) for i in sys.argv[1]]
print "".join([chr(text[n] ^ text[-(n+1)] ^ text[n]) for n in range(len(text))])

```

Usage:
```
 python WPC_1.py "Reverse this string" 
```

Explanation:
```
 import sys 
```
import the sys module so I can get input from the command line via sys.argv

```
 text = [ord(i) for i in sys.argv[1]] 
```
Take the first string passed to the program and convert all the characters in it to their equivalent numerical values

```
 print "".join([chr(text[n] ^ text[-(n+1)] ^ text[n]) for n in range(len(text))]) 
```

For each character in the list, perform an [xor swap]("http://en.wikipedia.org/wiki/Xor_swap") between that character and the character opposite it (ie first with last, second with second to last...). Store each ASCII character corresponding to the value received from the xor swap in a list and print the result.

---

### Post by ghostdog74 on 2006-12-02
The easiest way to reverse a string in Python is using the [::-1] slice notation.
```

>>> s = "reverse this string"
>>> print s[::-1]
gnirts siht esrever

```

---

### Post by Dual Cortex on 2006-12-02
C++

```
#include "stdafx.h"
#include <iostream> 
using namespace std;char word[1024];void main(){cout << "Write something: ";cin.getline(word,1023);int i = int(strlen(word)-1);for(i;i>-1;i--)cout << word[i];}

```

or

```
#include "stdafx.h"
#include <iostream> 
using namespace std;
char word[1024];
void main(){
	cout << "Write something: ";
	cin.getline(word,1023);
	int i = int(strlen(word)-1);
	for(i;i>-1;i--)
		cout << word[i];
}
```

---

### Post by po0f on 2006-12-02
Who wants to be a judge?  I think 3 judges should be able to pick a winner.  You will have to be available on 7 Dec for "deliberation", because the winner has to post the next contest on 8 Dec.  Post back if you want to be a judge, and you'll be "randomly" picked.  ;)

---

### Post by eatpie75 on 2006-12-02
in ruby
```

class Main
    input=gets
    puts input.reverse
end
Main.new()

```or
```

input=gets
puts input.reverse

```or
```

puts ARGV[0].reverse

```ruby ftw

edit: oh snap first two (pretty much) submitted twice already... so i wrote a gui:D 
```

#!/usr/bin/ruby

require 'gtk2'

class Main
    window = Gtk::Window.new('Reversifier')
    window.set_default_size(200, 100)
    window.window_position=Gtk::Window::POS_CENTER
    window.signal_connect("delete_event") {false}
    window.signal_connect("destroy") {Gtk.main_quit}
    
    mainbox = Gtk::VBox.new(false, 0)
    window.add(mainbox)
    
    input = Gtk::Entry.new
    mainbox.pack_start(input, true, true, 0)
    
    input_button = Gtk::Button.new('Reversify')
    mainbox.pack_start(input_button, true, true, 0)
    input_button.signal_connect("clicked") do
        input.text=input.text.reverse
    end
    
    window.show_all
    
    Gtk.main
end
Main.new()

```requires libgtk2-ruby

---

### Post by MatthewMetzger on 2006-12-03
Hello eatpie75,

I get a whole bunch of errors when I try to run your program. I have libgtk2-ruby installed.

Here's the output (sorry for length and I didn't even post it all):

./reverse_string.rb: line 3

   Gtk-WARNING **:Screen for GtkWindow not set; you must always set

a screen for a GtkWindow before using the window

./reverse_string.rb: line 3

   Gtk-CRITICAL **:gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

./reverse_string.rb: line 3

   Gdk-CRITICAL **:gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

./reverse_string.rb: line 3

   Pango-CRITICAL **:pango_context_set_font_description: assertion `context != NULL' failed

./reverse_string.rb: line 3

   Pango-CRITICAL **:pango_context_set_base_dir: assertion `context != NULL' failed

./reverse_string.rb: line 3

   Pango-CRITICAL **:pango_context_set_language: assertion `context != NULL' failed

./reverse_string.rb: line 3

   Pango-CRITICAL **:pango_context_get_language: assertion `context != NULL' failed

./reverse_string.rb: line 3

   Pango-CRITICAL **:pango_context_get_metrics: assertion `PANGO_IS_CONTEXT (context)' failed

./reverse_string.rb: line 3

   Pango-CRITICAL **:pango_font_metrics_get_ascent: assertion `metrics != NULL' failed

./reverse_string.rb: line 3

   Pango-CRITICAL **:pango_font_metrics_get_descent: assertion `metrics != NULL' failed

---

### Post by eatpie75 on 2006-12-03
are you using ruby 1.8?

---

### Post by Cyril on 2006-12-03
I think some guidelines are needed for the contest. What will the programs be judged on? Elegance? Efficiency? If the latter is one of the criteria then I think it needs to be said what the length of the input string should be. When the length of the string is long enough, the difference each program takes to complete the task could be significant.

Some of the programs submitted output the result one character at a time. I/O is an expensive operation so it is much better to output the entire result at once.

Try running java StringReverseOne < a.txt
and java StringReverseTwo < a.txt

You will see that StringReverseTwo is more efficient than StringReverseOne because it outputs the entire string at once instead of 1 character at a time.

However StringReverseTwo still is not a good solution because, it uses string concatenation to form up the result and as the string gets longer the cancatenation operation gets more expensive.

Try running java StringReverseOne < b.txt
and java StringReverseTwo < b.txt

In this case you quickly see a result from StringReverseOne but 
StringReverseTwo takes a painfully long time to complete.

Try running java StringReverseThree < b.txt

This solution is more efficient than StringReverseOne or StringReverseTwo because it outputs the entire string at once instead of one character at a time and it uses a string buffer to form up the result instead of string concatenation.

Of course, if efficiency is not a concern than none of this matters.

> import java.io.*;

class StringReverseOne {

    public static void main(String args[]) throws IOException{

        BufferedReader stdin = new BufferedReader(new InputStreamReader(System.in));
        String inputStr = stdin.readLine();
        int stringLen = inputStr.length();
        long startTime = System.currentTimeMillis();

        for(int i = stringLen-1 ; i >= 0 ; i--){
            System.out.print(inputStr.charAt(i));
        }

        long endTime = System.currentTimeMillis();
        System.out.println();
        System.out.println("Time taken in milliseconds :" + (endTime-startTime));

        
    }

}

> import java.io.*;

class StringReverseTwo {

    public static void main(String args[]) throws IOException{

        BufferedReader stdin = new BufferedReader(new InputStreamReader(System.in));
        String inputStr = stdin.readLine();
        String result = "";
        int stringLen = inputStr.length();
        long startTime = System.currentTimeMillis();

        for(int i = stringLen-1 ; i >= 0 ; i--){
            result += inputStr.charAt(i);
        }

        System.out.println(result);
        long endTime = System.currentTimeMillis();
        System.out.println("Time taken in milliseconds :" + (endTime-startTime));

        
    }

}


> import java.io.*;

class StringReverseThree {

    public static void main(String args[]) throws IOException{

        BufferedReader stdin = new BufferedReader(new InputStreamReader(System.in));
        String inputStr = stdin.readLine();
        StringBuffer sb = new StringBuffer();
        int stringLen = inputStr.length();
        long startTime = System.currentTimeMillis();

        for(int i = stringLen-1 ; i >= 0 ; i--){
            sb.append(inputStr.charAt(i));
        }
        System.out.println(sb);
        long endTime = System.currentTimeMillis();
        System.out.println("Time taken in milliseconds :" + (endTime-startTime));

        
    }

}


---

### Post by emix on 2006-12-03
> **Cyril said:**
> Some of the programs submitted output the result one character at a time. I/O is an expensive operation so it is much better to output the entire result at once.
This is not definitely true: if you pick [my solution]("http://ubuntuforums.org/showpost.php?p=1830548&postcount=10") and add a pause of 1 second between the printf of each char you'll see that after a pause of 'strlen' seconds the string will be written entirely. This happens because the output is buffered before it's sent to the screen.

---

### Post by lnostdal on 2006-12-03
ah; you want a GUI also? .. here:

```

(eval-when (:compile-toplevel :load-toplevel :execute) (require :SWGtk))

(defpackage :ReverseGUI
  (:use :cl :SWGtk)
  (:shadowing-import-from :SWGtk :remove))
(in-package :ReverseGUI)


(defun startGUI ()
  (withSWGtk
    (let* ((window (make-instance 'Window
                                  :title "ReverseGUI: Reverse a string!"
                                  :default-width 400
                                  :default-height 250))
           (vbox (make-instance 'VBox))
           (output (make-instance 'Label))
           (input  (make-instance 'Entry
                                  :changed-event (lambda (input)
                                                   (setf (label-of output)
                                                         (reverse (text-of input)))))))
      (packStart output vbox)
      (packStart input vbox)
      (add vbox window)     
      (setf (visible-p-of window) :show-all))))

```

edit: ouch; it seems the forum messes with my indentation - which is very important in lisp .. here is the thing with correct indentation:
[http://nostdal.org/~lars/programming/lisp/ubuntu-contest/reverse-gui.lisp](http://nostdal.org/~lars/programming/lisp/ubuntu-contest/reverse-gui.lisp) (it is also visible in the animation below)

check out a GIF-animation of the thing here:
  [http://nostdal.org/~lars/programming/lisp/ubuntu-contest/reverse-gui.gif](http://nostdal.org/~lars/programming/lisp/ubuntu-contest/reverse-gui.gif)

..pretty cool? :D

pressing ctrl-shift-r restarts the animation btw.

edit:
I'm using my home-made GTK+-bindings for GUI: [http://nostdal.org/~lars/programming/lisp/swgtk/swgtk.html](http://nostdal.org/~lars/programming/lisp/swgtk/swgtk.html)

---

### Post by MatthewMetzger on 2006-12-03
> **eatpie75 said:**
> are you using ruby 1.8?

ruby 1.8.4

---

### Post by jayemef on 2006-12-03
No PHP solutions yet?

```

<?php
echo strrev('Hello world!');
?> 

```

Also, to all those with Bash solutions -- the rev tool is installed in Ubuntu by default. So for a more clear Bash solution:
```

echo 'Hello World!' | rev

```

You guys should check out [Ruby Quiz]("http://rubyquiz.com/") if this thread interests you. Similar concept - week-long programming challenges, though the language is restricted to Ruby. Previous challenges and solutions are all posted. I'd recommend joining the mailing list.

---

### Post by po0f on 2006-12-04
jayemef,

As originally posted in [this thread](http://www.ubuntuforums.org/showthread.php?t=309539), Ruby Quiz is where inspiration is partly drawn from.  The original intent is to not limit the language though, but thanks for the suggestion.

I haven't yet browsed the Ruby Quiz website in depth yet, but maybe some of the quizzes there can be posted here.  I'm interested in seeing solutions to problems from a variety of languages.  Also (just in case you thought this week's quiz wasn't that difficult), I would like the difficulty progression to go up only slightly each week to hopefully draw people not familiar with programming in as well.

PS: I'm still trying to come up with a Bash solution myself, but using just the built-ins (no outside commands, pure Bash).  I don't think I know enough Bash to get it done though.  :)

---

### Post by jayemef on 2006-12-04
My bad -- missed that part.

Here is a solution in straight bash:
```

text='Hello World!'
reverse=''
tmp=$text
while [ -n "$tmp" ]
do
    reverse=${tmp::1}$reverse
    tmp=${tmp:1}
done
echo $reverse

```

---

### Post by &lt;mawe&gt; on 2006-12-04
Hi!

My solution in OCaml:
```
let rev s =
  let n = ref "" in
  String.iter (fun x -> n := (Char.escaped x) ^ !n) s;
  !n


let _ =
  let s = match Sys.argv with
    [|_; s|] -> s
  | _ -> invalid_arg "Usage: reverse.ml <string>" in
  print_endline (rev s)
```

EDIT: ... and a short Python version:
```
print raw_input()[::-1]
```
:)

Regards, mawe

---

### Post by shoagun on 2006-12-04
Should we be trying to do this in the smartest most efficient way? (ie a one liner in perl) 

Or are we going for something creative and unexpected (like a solution in machine language?)

---

### Post by Arndt on 2006-12-04
> **emix said:**
> And where is the error?

In the 'reverse' function.

---

### Post by ghostdog74 on 2006-12-04
I think we should not make this thread a contest. We should just sticky it  or something, with a title eg "String reversals" and then whoever wants to know about how string reversals are done in various languages can go to it. Just a thought.

---

### Post by emix on 2006-12-04
> **Arndt said:**
> In the 'reverse' function.
My question was an italian way to say that it's not an error! The '\0' (null) character is not printable, so if you reverse an empty string it doesn't output anything.

---

### Post by Arndt on 2006-12-04
> **emix said:**
> My question was an italian way to say that it's not an error! The '\0' (null) character is not printable, so if you reverse an empty string it doesn't output anything.

To be specific, in that case you do putchar('\0'). That does output something. You don't see it, but it's there. Redirect to a file, and count the number of characters in the file - it will be 1 and not 0.
(Or 2 instead of 1 - I forget if there's a newline there or not.)

---

### Post by emix on 2006-12-04
> **Arndt said:**
> To be specific, in that case you do putchar('\0'). That does output something. You don't see it, but it's there. Redirect to a file, and count the number of characters in the file - it will be 1 and not 0.
(Or 2 instead of 1 - I forget if there's a newline there or not.)
Uhm... and is a '\0' output a very time consuming operation?!? Remember that the task of the program is to printout a string, not to store it somewhere.

Moreover the task of the program is really stupid and of course the right way to solve it is with the use of two "while", the former to find the end of the string and the latter to recreate the reversed string (if we don't want to use any external function). I used this approach to show a creative use of recursion.

IMHO

---

### Post by Arndt on 2006-12-04
> **emix said:**
> Uhm... and is a '\0' output a very time consuming operation?!? Remember that the task of the program is to printout a string, not to store it somewhere.

Moreover the task of the program is really stupid and of course the right way to solve it is with the use of two "while", the former to find the end of the string and the latter to recreate the reversed string (if we don't want to use any external function). I used this approach to show a creative use of recursion.

IMHO

If you do your operation on a whole text file, like the command 'rev' does, you will have converted a text file into a binary file (containing nonprintable characters). Why would you want to do that? It's an error, regardless of how fast it is.

The way to fix your function is to let the putchar be included in the 'if' statement just above it.

Recursion is fine, and I wasn't criticizing recursion. Since you brought it up, I'd like to mention that if you use recursion in C, you should be sure that you don't recurse very far - the C standard has a limit of what is guaranteed to work, but I don't remember what it is. C++ is likely to have a similar limit.

---

### Post by emix on 2006-12-04
> **Arndt said:**
> Recursion is fine, and I wasn't criticizing recursion. Since you brought it up, I'd like to mention that if you use recursion in C, you should be sure that you don't recurse very far - the C standard has a limit of what is guaranteed to work, but I don't remember what it is. C++ is likely to have a similar limit.
Of course... this approach is not safe and should be more "controlled", but I chose to keep the code as simpler as possible.

```
#include <stdio.h>

int depth = 0;

void rec() {
	printf("%d\n", depth++);
	rec();
}

int main(int argc, char **argv) {
	rec();
	return 0;
}
```

Output:
> ...
523464
523465
523466
523467
523468
523469
Segmentation fault (core dumped)


---

### Post by jayemef on 2006-12-04
Haskell:
```

reverse "Hello World!"

```

---

### Post by lloyd mcclendon on 2006-12-04
i think any solutions that iterate through the string char by char should be ruled out because it is so naive.  recursive solutions, while very cool, are essentailly the same thing and are just as naive and will perform even slower.  yeah it's ok for a string like "Hello world" but what if it's 2 billion characters

---

### Post by Dual Cortex on 2006-12-04
Yay for recursion and down 2 million characters!

Another submission:
```
#include <iostream>
using namespace std;
char word[1024];
int re(int i, char *p){
    if (!i)
        return 0;
    cout << p[--i];
    re(i, p);
}
int main(){
    cin.getline(word,1023);
    re(strlen(word), &*word);
    return 0;
}
```

---

### Post by Peepsalot on 2006-12-04
> **lloyd mcclendon said:**
> i think any solutions that iterate through the string char by char should be ruled out because it is so naive.  recursive solutions, while very cool, are essentailly the same thing and are just as naive and will perform even slower.  yeah it's ok for a string like "Hello world" but what if it's 2 billion characters
Naive?  Seems logical to me.  Do you know an algorithm that has complexity of less than O(n) ?

---

### Post by Ramses de Norre on 2006-12-04
> **lloyd mcclendon said:**
> 1 statment

```
public class StringReverser {

	public static void main(String[] args) {
		System.out.println(
				(args.length > 1)
					? new StringBuilder(args[0]).reverse().toString()
					: "usage: java " + StringReverser.class.getSimpleName() + " string_to_reverse");
	}
}
```

It's easy to say that other people's algorithms are too complex if you use a build in one yourself.. 
And I doubt its complexity will be lower.

---

### Post by Tomosaur on 2006-12-04
> **lloyd mcclendon said:**
> i think any solutions that iterate through the string char by char should be ruled out because it is so naive.  recursive solutions, while very cool, are essentailly the same thing and are just as naive and will perform even slower.  yeah it's ok for a string like "Hello world" but what if it's 2 billion characters

Any reversing method will do this, it just may not be obvious depending on the language. There is no way for hardware to just 'do' something. One of the fundamental differences between computers and humans is that computers are fantastic at doing the same thing over and over again. Recursion is essentially what computers do for any task.

---

### Post by &lt;mawe&gt; on 2006-12-04
[quote="lloyd mcclendon"]i think any solutions that iterate through the string char by char should be ruled out because it is so naive.[/quote]
Ok, so only languages with a "reverse" keyword should be allowed? And how are these functions implemented? ;)

BTW: I also think this thread should not be a contest. It's nice to see how reversing a string can be coded in so many different languages, but for a contest it's far too easy. Will be fun with a more "complex" task.

---

### Post by supirman on 2006-12-04
No assembly submission yet?  Perhaps I'll have to whip something up later...

---

### Post by Arndt on 2006-12-04
> **supirman said:**
> No assembly submission yet?  Perhaps I'll have to whip something up later...

Snobol would be interesting, but I've completely forgotten the details of that weird language.

---

### Post by daz4126 on 2006-12-04
> **lloyd mcclendon said:**
> i think any solutions that iterate through the string char by char should be ruled out because it is so naive.  recursive solutions, while very cool, are essentailly the same thing and are just as naive and will perform even slower.  yeah it's ok for a string like "Hello world" but what if it's 2 billion characters

I don't see what you propose as a solution? Surely this is what reverse methods do 'in the background' anyway?

On the contrary, I felt a bit of a fraud witht the simple word.reverse ruby entry and am trying to work on a recursive/loop solution. This has already helped my relative basic programming skills improve and I have learnt some new methods in the process.

DAZ

---

### Post by shining on 2006-12-04
> **<mawe> said:**
> Ok, so only languages with a "reverse" keyword should be allowed? And how are these functions implemented? ;)

BTW: I also think this thread should not be a contest. It's nice to see how reversing a string can be coded in so many different languages, but for a contest it's far too easy. Will be fun with a more "complex" task.

I think that using a reverse keyword shouldn't be allowed.
It would be nicer to see the implementation of a task in several languages, rather than only the usage of something already implemented.
But the task is indeed not complex enough.

Btw, this site is so cool : [http://www.99-bottles-of-beer.net/](http://www.99-bottles-of-beer.net/)

---

### Post by daz4126 on 2006-12-04
> **shining said:**
> I think that using a reverse keyword shouldn't be allowed.

But the task is indeed not complex enough.


Personally I think everything should be allowed, it is interesting to see people's different solutions and basic solutions should also be accepted to encourage novice programmers (like myself).

The task is very basic but I felt this was good for a start as it got me to enter and hopefully I will be able to stay on board and improve in the future.

Surely nobody cares that much about 'winning' this contest, think of it more as a 'challenge'.

DAZ

---

### Post by Verminox on 2006-12-04
Probably the shortest in C++:

```
for(int i=strlen("String");i!=0;std::cout<<s[--i]);
```

As a full working program...

```
#include <iostream>
int main(int v, char* a[]){
    for(int i=strlen(a[1]);i!=0;std::cout<<a[1][--i]);    
    return 0;
}
```

Compile and run with string as first argument

eg. RevProgram ReverseThisString

---

### Post by jayemef on 2006-12-04
SQL! (only tested in MS SQL Server)
```

SELECT REVERSE('Hello World!');

```

Why disallow solutions that use built-in functionality? Programmers should always look for a built-in way of doing something before implementing it on their own, as those who worked on the language spent a lot of time optimizing the routine as much as possible. For something as trivial as reversing text it might not be an issue. But the principle still holds true.

[Good programmers are lazy and dumb.]("http://blog.outer-court.com/archive/2005-08-24-n14.html")

---

### Post by dwblas on 2006-12-04
Someone has probably submitted this in Pyton.  There aren't that many different ways to do it
```
len_str = len(the_string) + 1
for j in range( 1, len_str ) :
   print the_string[-j]
```Edit:  Add my vote to the anything goes, we can all maybe learn something tally.

---

### Post by po0f on 2006-12-04
Ok, so next week it will be a "Weekly Programming *Challenge*", how about that?

I like the idea of using language built-ins for solving the problem, because it shows people how easy a language can be to use.  I never would have thought that Ruby (or Lisp) could be so compact.  Compact code really isn't my thing (I'm stubborn, and need things to be verbose and explained pretty in-depth for me to understand it), but it is cool to know that it's there for other people.

Since there is never going to be a "winner", who wants to post next week's challenge?

---

### Post by Wybiral on 2006-12-04
Ok, I figure I'll start off the ASM with this one, it simply creates a series of characters "\nHello World", sets the register edi to the end of them and works its way to the start outputting the current one.

```

.section .data
	data: .long '\n', 'H','e','l','l','o',' ','W','o','r','l','d','!'
	size= .-data

.globl _start

_start:
	movl $size, %edi
	subl $4, %edi

	start_loop:
		movl $4,   %eax
		movl $data, %ecx
		addl %edi, %ecx
		movl $4,   %edx
		int $0x80
		subl $4, %edi
		cmpl $0, %edi
	jnl start_loop

	movl $1, %eax
	int $0x80

```

If you dont know how to compile ASM, save it as "hello.s" and compile it to an object with...

"as hello.s -o hello.o"

Then create an executable from that object with...

"ld hello.o -o hello"

And you should have your executable, run it in the command line with "./hello"

---

### Post by tribaal on 2006-12-04
If I can be a juge, I'd settle for the Prolog solution (I love prolog and weird languages in general), and the sed solution. I really must learn sed "programming", it's so powerfull!

And a special mention for the python [::1] hack, and the assembly one, of course :)

My programming skills aren't high enough to come up with anything that hasn't already been posted... but I'll make an effort for the next contest ;)

Cheers to you all

- trib'

EDIT: For the next challenge, how about something that calculates the square root of an arbitrary number to, say, 6 decimals? ;)

---

### Post by igknighted on 2006-12-05
Java w/ an array:

```
import javax.swing.JOptionPane;
public class Reverse
{
	public static void main(String[] args)
	{
		String phrase = JOptionPane.showInputDialog("Enter a phrase to be reversed");
		int length = phrase.length();
		char letter[] = new char[length+1];
		int i = 0;
		while (i < length)
		{
			letter[i] = phrase.charAt(i);
			i++;
		}
		while (i > 0)
		{
			System.out.print(letter[i]);
			i--;
		}
		System.out.println(letter[0]);
	}
}
```

---

### Post by &lt;mawe&gt; on 2006-12-05
Hi!

A suggestion for the next challenge:
Someone mentioned the Ruby Quiz. What about Quiz #84, [pp-Pascal](http://rubyquiz.com/quiz84.html), calculate and pretty-print Pascal's Triangle. I think this wouldn't be too hard and not too trivial.
So the task would be: Write a program, where
```
pascal_tri 10
```
pretty prints the whole triangle up to line number 10, and
```
pascal_tri -l 10
```
prints just the 10'th line of the triangle.
What do you think? :)

Regards, mawe

---

### Post by daz4126 on 2006-12-05
Here a some of my suggestions:


[LIST=1]
[*]simulate rolling a dice (easy, but can be made harder)
[*]A program to calculate the factorial of a number (which would probably be needed anyway for the pascal's triangle program)
[*]A program that asked you to solve an equation of the form ax + b = c (or harder) and gave feedback about your answer
[*]A game of rock, paper, scissors
[*]A game of noughts and crosses (tic-tac-toe)
[/LIST]

I like the idea of 1 and 3 as they can be extended, but are not too difficult to begin with.
Rock paper scissors could also be extended into a question about game theory also...

any thoughs?

DAZ

---

### Post by Dual Cortex on 2006-12-05
I like #2 and #3.
#1 & #4 seem too easy.
#5 would require me to read up on TicTacToe strategy :P.

---

### Post by whoismilan on 2006-12-05
> **po0f said:**
> Ok, so next week it will be a "Weekly Programming *Challenge*", how about that?
Personally I feel as though "the best" in a competition like this really comes down to personal preference, so the competition turns into to a popularity contest. For this reason I would feel that a "weekly challenge" would be more fun, and also that way one can always count on that there will be a new challenge posted on time (contest: contest submissions -> contest closes/submission review -> winner announcment -> winner notices that he/she won (is everyone even online every few days to notice they won?) -> winner comes up with, and posts a new challenge).

> **po0f said:**
> Since there is never going to be a "winner", who wants to post next week's challenge?
YOU! :D How about if people can post ideas in the thread, but there is a "board" of members who chooses (e.g. consisting of the person(s) who came up with the contest/challenge, or someone else who has been appointed as in charge of it)?

---

### Post by po0f on 2006-12-05
tribaal,

I myself was pretty partial to the sed solution myself, because I think sed is just an awesome program.  I knew that this problem could be solved using sed, but like you, I don't know too much sed.


daz4126 and Dual Cortex,

This first challenge was intentionally easy, and subsequent challenges should progress in difficulty only slightly.  Like I said previously, I would like to keep the challenges accessible to non-programmers.  Hopefully we can draw people into programming that think it is too hard; browsing the forums, they might stumble upon these threads and realize how easy it is to solve simple problems.

I do like the idea of Pascal's triangle though.  OTOH daz4126's suggestion #3 would require quite a bit more knowledge than what a newbie programmer has, and maybe even what some of the programmers here have.  You're treading dangerously close to writing a compiler compiler (having to parse statements and evaluate them according to certain rules).  :)

---

### Post by Lster on 2006-12-05
@Po0f, I too like the idea of the equation solver. I have implemented quite a few myself and they are not very difficult - even for quadratics (cubics, sine, tan etc...).

Anyhow... I look forward to watching this, and maybe even submitting :D!

---

### Post by daz4126 on 2006-12-05
I wasn't thinking #3 would be too difficult, just something along the lines of choosing a random value for a,b and c and the program asking,
'solve ax + b = c'
If you put the right answer it says 'well done' and if it is wrong it says, 'try a lower/higher number' or 'try subtracting b from both sides' etc.

This could then obviously be extended to harder equations if people wished.

Personally I would be keen for a shallow curve in difficulty of the task as I am not an accomplished programmer by any means and this thread is a great motivator, maybe it would turn people off if it was too hard.

Just thought that it could be worth having an easy and hard challenge each week to give the class swats something to get their teeth into?

DAZ

---

### Post by daz4126 on 2006-12-05
> **Dual Cortex said:**
> I like #2 and #3.
#1 & #4 seem too easy.
#5 would require me to read up on TicTacToe strategy :P.

#4 (rock, paper, scissors) would probably be easy to start with, so would be very accessible for beginners (a good thing imo). The computer would employ the best strategy, which is to randomly choose either rock paper or scissors. However it gets more complex by trying to make the computer 'learn' your habits and react to what it 'thinks' you might do.
You could also give weightings to the game by allocating points, for example rock still beats scissors, but scores 2 points, whereas paper beats rock and scores 3 points. Then you are moving into more complicated tripartite game theory....

so to summarise, I feel that #4 is easy enough as to be accessible, but can also be extended. 

DAZ

---

### Post by daneel_olivaw on 2006-12-05
> **public_void said:**
> Just to be fancy, I've written it in Prolog.
```
reverse_string(String):- 
    string_to_list(String, List),
    reverse(List, NewList),
    writef(NewList, '~c')
```
And the really short one liner.
```
r(S):-string_to_list(S,L),reverse(L,N),writef(N,'~c').
```

Evidently I'm not the only one who likes Prolog :D

Ehm.. forgot to add my contribute, for the sake of recursion:

```

reverse([],[]).
reverse([H|T], L):-
	reverse(T, L1),
	append(L1, [H], L).

```

just the definition of the predicate you used :P

cheers

---

### Post by Wybiral on 2006-12-05
Here's a few more ideas to choose from...

Idea #1) Some kind of simple AI like; like a chatbot, genetic algorithm, or a simple neural network

Idea #2) I liked the idea of a handwritten square-root solver, even other handwritten math solvers, like a handwritten adder (can't use actually addition commands to add)

Idea #3) A size competition, like, it must be under 20 lines or so (and maybe a max line width)

Idea #4) A text editor

Idea #5) Procedurally generate a bmp image file (the code creativity AND the procedural image could both be considered)

Idea #6) Any small program that demonstrates 2d collision detection

---

### Post by public_void on 2006-12-05
Or to really twist your head with recursion and backtracking.
```
my_reverse(List, NewList):-
	my_reverse(List, [], NewList).

my_reverse([], NewList, NewList).
my_reverse([Head|Tail], TempList, NewList):-
        my_reverse(Tail, [Head|TempList], NewList).
```

---

### Post by po0f on 2006-12-05
> **daz4126 said:**
> I wasn't thinking #3 would be too difficult, just something along the lines of choosing a random value for a,b and c and the program asking,
'solve ax + b = c'
If you put the right answer it says 'well done' and if it is wrong it says, 'try a lower/higher number' or 'try subtracting b from both sides' etc. ...
I had something else in mind entirely when I read that; I thought you were saying that the *program* should evaluate what the *user* put in, not vice versa.  (It would be easy for the program too, if you had a set equation.  I was thinking more along the lines of the user inputting some random equation and the program solving it.)  I guess that would be easy enough, but I don't think many people are too keen on math.

And to go along with daz4126's suggestion of maybe extending programs to do things not outlined in the challenge, bonus "points" for implementing extra functionality into the program will be awarded.  Of course, the points will be like _Whose Line Is It Anyways?_ points.  (Hint: the points don't matter on that show.)  :)

I guess I will post next week's challenge, but I don't want to get used to doing it every week.  I wasn't the idea man behind it, this "contest" was originally someone else's idea (and someone else's before their's).  ;)  I think that maybe other people would want to contribute to the running of the WPC besides me, and it would make me feel less like a dictator.  (I hate dictators.)  :)

---

### Post by daz4126 on 2006-12-05
A totally different ruby program that iterates through the word's letters. This shows a cool integer method that I have just found out - downto:

```
puts "Please enter a word" #ask the user for a word
word = gets.chomp #get the word from the user and chomp off the newline character
word_backwards = "" #set an empty string variable for the word backwards

#this is the cool integer method, it starts at the lenght of the word and goes down to 1. It then pushes each letter from the back of the string into the new empty string (word backwards)
word.length.downto(1) do |letter|
word_backwards << word[letter -1].chr
end 

puts "Your word was: #{word}" #tell the user their word
puts "Your word backwards is: #{word_backwards}" #write the word backwards
```

DAZ

---

### Post by dwblas on 2006-12-05
> Or to really twist your head with recursion and backtracking.I would like to see something along these lines, but would it be too abstract/mind-twisting for someone fairly new to programming?  Another idea that was found on the internet:
Given a group of itemsets (or strings), whose members are themselves in
ascending order (or not), eg
ABCD
ABDE
ABE
AE
how can one find all subsets which occur in two (or in general some
integer c) or more sets in the group?

---

### Post by hod139 on 2006-12-05
I've looked at many of the solutions and many use existing libraries to perform the actual work.  While it is very useful and good to know how to use standard libraries in practice, for academic programming exercises designed to teach programming (which I think is the point of these threads) you should maybe consider outlawing the use of standard libraries in the solutions.

For example:
> **Zdravko said:**
> ```

#include <iostream>
#include <algorithm>
#include <sstream>
using namespace std;

int main(int c, char* v[]) {
    string s;
    c > 1 ? getline(istringstream(v[1]), s) : getline(cin, s);
    reverse(s.begin(), s.end());
    cout << s;
    return 0;
}

```Now, do I win the contest? This is the most elegant way to solve the problem in C++.

This is in no way attacking Zdravko, it is just a good post at illustrating my point.  While using the C++ STL leads to a very short implementation (don't know if I would call it **most** elegant) it doesn't show if s/he actually knows how to solve the problem.  The task was to **write** the reverse function, not call it.  There are many other examples of this.

Maybe I'm just being impracticable coming from still being in academia, but I just wanted to put in my two cents.

---

### Post by duff on 2006-12-05
I haven't seen a single one of you so-called C++ programmers using reverse iterators :p

```
#include <iostream>
#include <string>
#include <iterator>

int main(int argc, char *argv[])
{
   std::string str;
   getline(std::cin, str);
   std::copy(str.rbegin(), str.rend(), std::ostream_iterator<char>(std::cout, ""));
}
```

---

### Post by mkppk on 2006-12-05
```
import sys

s=''
for i in xrange(len(sys.argv[1])-1,-1,-1):s+=sys.argv[1][i]
print s
```


mkp@mac:~/pytest$ python foo.py hello
olleh
mkp@mac:~/pytest$

---

### Post by jayemef on 2006-12-05
C#:
```

using System;

namespace ReverseText {

    class MainClass {

        public static void Main(string[] args) {
            Console.WriteLine(Reverse("Hello World!"));
        }

        public static String Reverse(String text) {
            if (1 == text.Length) {
                return text;
            }
            else {
                return Reverse(text.Substring(1)) + text.Substring(0, 1);
            }
        }

    }

}


```

---

### Post by Lster on 2006-12-06
Here is my small example in C:

```
#include <stdio.h>
#include <string.h>

int main(){
	printf("\n> ");
	
	char a[101];
	scanf("%100s", &a);
	
	printf("= ");
	
	int i;
	for(i = strlen(a) - 1; i >= 0; i--)
		putchar(a[i]);
	
	printf("\n\n");
	
	getchar();
	return 0;
}

```

---

### Post by yaaarrrgg on 2006-12-06
bash shell ;)

```

echo "hello there" | rev 

```

---

### Post by Peepsalot on 2006-12-06
> **yaaarrrgg said:**
> bash shell ;)

```

echo "hello there" | rev 

```
lol, I can't believe I didn't find that command.  I already knew my bash solution was incredibly inefficient and unecessary, but man, way to rub it in.  :)

---

### Post by bradleyd on 2006-12-06
here is my solution in perl

#!/usr/bin/perl

print "Enter String:\n";
my $input = <STDIN>;
$rv = reverse($input);
print "your string reversed is:"."$rv\n";


or my favorite:

#!/usr/bin/perl

my $input = "bob";
$rv = reverse($input);
print "$rv\n";

---

### Post by Ramses de Norre on 2006-12-06
> **yaaarrrgg said:**
> bash shell ;)

```

echo "hello there" | rev 

```

That's cool, you can run bash|rev and all output from commands will be reversed =)

---

### Post by hod139 on 2006-12-06
There is also tac, which is the inverse of cat.

---

### Post by dwblas on 2006-12-06
> When I invented the Web, I didn't have to ask anyone's permission.
--Tim Berners-Lee on Net NeutralityGreat quote.

---

### Post by dwblas on 2006-12-06
This is now on page 11.  I would suggest that a new page be started each week to keep it to a manageable size.

---

### Post by Peepsalot on 2006-12-06
> **hod139 said:**
> There is also tac, which is the inverse of cat.

Yeah, but that only reverses the order of the lines, not the content of them. 

That's what my crappy bash solution used.  I had to split each character onto it's own line, then use tac, then merge the lines back together.  Unfortunately my solution doesn't preserve newline characters.

Here's the code again, just for reference
```
#!/bin/bash
echo $1|grep -o .|tac|tr -d '\n' && echo
```

---

### Post by po0f on 2006-12-06
dwblas,

A new thread will be created for each WPC.  I will post it Friday 12:00AM EST.

---

### Post by hod139 on 2006-12-06
> **Peepsalot said:**
> Yeah, but that only reverses the order of the lines, not the content of them. 

That's what my crappy bash solution used.  I had to split each character onto it's own line, then use tac, then merge the lines back together.  Unfortunately my solution doesn't preserve newline characters.

Here's the code again, just for reference
```
#!/bin/bash
echo $1|grep -o .|tac|tr -d '\n' && echo
```
Sorry for causing confusion.  I was incomplete in my posting, and didn't take the time to read all the others.  I only meant to state the BASH has a cute sense of humor by having a tac command, which is the inverse of cat.  I hadn't realized that someone actually used it, nor did I mean for it to be considered for an entry.  Sorry for the confusion.

---

### Post by Zdravko on 2006-12-07
> **hod139 said:**
> This is in no way attacking Zdravko, it is just a good post at illustrating my point. While using the C++ STL leads to a very short implementation (don't know if I would call it **most** elegant) it doesn't show if s/he actually knows how to solve the problem. The task was to **write** the reverse function, not call it. There are many other examples of this.
No, I believe the task didn't have explicit rules where built-in functions shouldn't be used. Besides, my sollution meets the conditions in the task!
 
> **duff said:**
> I haven't seen a single one of you so-called C++ programmers using reverse iterators :p
 
```
#include <iostream>
#include <string>
#include <iterator>
 
int main(int argc, char *argv[])
{
   std::string str;
   getline(std::cin, str);
   std::copy(str.rbegin(), str.rend(), std::ostream_iterator<char>(std::cout, ""));
}
```
Ok, dude - you win! I didn't come up with this idea! Looks very elegant, IMHO! :KS

---

### Post by the.dark.lord on 2006-12-07
Ruby:
Code-

puts'enter a string'
str=puts gets.chomp
puts str.reverse

-End of code-

Now, where's the prize? ;)

---

### Post by the.dark.lord on 2006-12-07
Sorry for the double post.

---

### Post by daz4126 on 2006-12-07
> **the.dark.lord said:**
> Ruby:
Code-

puts'enter a string'
str=puts gets.chomp
puts str.reverse

-End of code-

Now, where's the prize? ;)

You'll have to get in line for prizes! This is almost the same as the solution I posted last week. ;) 

Ruby is very elegant though isn't it? It seems much more readable than many of the other postings.

DAZ

---

### Post by ghostdog74 on 2006-12-07
> **daz4126 said:**
> You'll have to get in line for prizes! This is almost the same as the solution I posted last week. ;) 

Ruby is very elegant though isn't it? It seems much more readable than many of the other postings.

DAZ

elegant and more readable as compared to this?:
```

#!/usr/bin/python
str = raw_input("Enter a string: ")
print str[::-1]

```
:-k

---

### Post by lnostdal on 2006-12-07
> **ghostdog74 said:**
> elegant and more readable as compared to this?:
```

#!/usr/bin/python
str = raw_input("Enter a string: ")
print str[::-1]

```
:-k

..or in Lisp, again:
```
(reverse (read-line))
```

ie; "The reverse of what `read-line' returns." .. and Lisp is supposed to be hard. :)

Weird how some people think the more cryptic and hard-to-maintain stuff that looks like REGEXPs is "the coolest". I don't get that and certainly try to avoid it whenever possible regardless of language.

---

### Post by hod139 on 2006-12-07
> **Zdravko said:**
> No, I believe the task didn't have explicit rules where built-in functions shouldn't be used. Besides, my sollution meets the conditions in the task!
 


Maybe I was unclear.  My point was that for **future** programming challenges, they might want to add a rule that you can't use built in functions.  Sorry if that was unclear.  As short as 
```

echo "string" | rev

```

is, it doesn't really show that I know how to write a reverse operations.  

This is just my two cents, and it all depends on the goals of the contest.

---

### Post by daz4126 on 2006-12-07
> **lnostdal said:**
> 
Weird how some people think the more cryptic and hard-to-maintain stuff that looks like REGEXPs is "the coolest". I don't get that and certainly try to avoid it whenever possible regardless of language.

I agree. One of the things I love about ruby is at times it is like you are reading english, methods like the wonderful:

```
10.downto(1)
```

that increments from "10 down to 1" - told you it sounds just like english!!

DAZ

---

### Post by dwblas on 2006-12-07
I vote that anyone who uses this thread to say "My language is better." be banned.  These are exercises in programming, not an opportunity to give a sales pitch.

---

### Post by Peepsalot on 2006-12-07
Anyone written an uber efficient example using Duff's device?  I might code one up later.

---

### Post by hod139 on 2006-12-07
> **Peepsalot said:**
> Anyone written an uber efficient example using Duff's device?  I might code one up later.
Do you think Duff's device is faster than a memcpy?  It could be an interesting experiment, but I would put my money on memcpy, which is likely more optimized.  Duff's device can only be as fast as what gcc does to optimize it.

---

### Post by Peepsalot on 2006-12-07
> **hod139 said:**
> Do you think Duff's device is faster than a memcpy?  It could be an interesting experiment, but I would put my money on memcpy, which is likely more optimized.  Duff's device can only be as fast as what gcc does to optimize it.
How would you use memcpy to reverse a string?

And who said Duff's device has to be implemented in C, I was gonna do it in javascript :p

---

### Post by Jessehk on 2006-12-07
```

(* I'm learning O'Caml!
 * by Jessehk on Dec. 7, 2006
 *)

let reverse string =
    let rec helper n =
        match n - 1 with
        | -1    -> ""
        | x     -> String.make 1 (string.[x]) ^ helper x in

    helper (String.length string);;

let main =
    let input = read_line () in
    Printf.printf "%s\n" (reverse input);;

```

---

### Post by neoflight on 2006-12-09
in matlab:

```
>>out=fliplr(input('enter a string: ','s'))
```

output:

[PHP]enter a string: I vote that anyone who uses this thread to say "My language is better." be banned. These are exercises in programming, not an opportunity to give a sales pitch.

out =
.hctip selas a evig ot ytinutroppo na ton ,gnimmargorp ni sesicrexe era esehT .dennab eb ".retteb si egaugnal yM" yas ot daerht siht sesu ohw enoyna taht etov I[/PHP]

i win:mrgreen:

---

### Post by dwblas on 2006-12-10
From Neoflight: > I winIn that case I get to add one more entry which proves that you didn't```
import string
from collections import deque

input_str = raw_input( "Enter string to reverse " )
d = deque( input_str )
len_str = len(input_str)
try :
   for j in range( 0, len_str ) :
      print d.pop(),
   print
except :
   print "deque error"
```The result =
tsetnoc eht fo yad tsal eht saw yadsruhT

---

### Post by dwblas on 2006-12-10
Sorry, double post

---

### Post by maddog39 on 2006-12-16
Here is my contribution with a PHP command line program, and also has an execution timer.

[PHP]
#!/usr/bin/php

<?php
function get_time() {
	$current_time = microtime();
	$current_time = explode(" ", $current_time);
	$current_time = $current_time[1] + $current_time[0];
	return $current_time;
}

$start_time = get_time();

if (($argc >= 1) && (isset($argv[1]))) {
	if ($argv[1] == "-h") {
		echo "usage: " . $argv[0] . " <string>\n";
	} elseif (strlen($argv[1]) > 1) {
		echo "Reversed String: " . strrev($argv[1]) . "\n";
	} else {
		echo "Use " . $argv[0] . " -h for more information.\n";
	}
} else {
	echo "Use " . $argv[0] . " -h for more information.\n";
}

$stop_time = get_time();
$total_time = round($stop_time-$start_time, 5);
echo "Execution Time: " . $total_time . "s\n\n";
?>
[/PHP]
I also made a PHP one-liner, using CLI interface.
```

php -r "echo strrev('Hello World!').\"\n\";"

```

**Results/Usage**
Usage of revstr.php
```

alec-husseys-Computer:/Applications/MAMP/htdocs alechussey$ ./revstr.php 

Use ./revstr.php -h for more information.
Execution Time: 0.05372s

alec-husseys-Computer:/Applications/MAMP/htdocs alechussey$ ./revstr.php -h

usage: ./revstr.php <string>
Execution Time: 0.0009s

alec-husseys-Computer:/Applications/MAMP/htdocs alechussey$ ./revstr.php "maddog39 is really cool, right?"
                             
Reversed String: ?thgir ,looc yllaer si 93goddam
Execution Time: 0.00095s

```

Usage of one-liner
```

alec-husseys-Computer:/Applications/MAMP/htdocs alechussey$ php -r "echo strrev('Hello World!').\"\n\";"
!dlroW olleH

```

---

