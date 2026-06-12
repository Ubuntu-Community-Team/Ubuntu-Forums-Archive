---
title: "Segmentation fault (core dumped) Problem"
date: 2012-10-16
forum: Programming Talk
---

### Post by mhaggard on 2012-10-16
Ok, I am sure this has already been solved somewhere, but I haven't found it yet. Anyway, I am writing a program for class and I keep getting this 'error' when I run it. I am using kate/gedit as my text editor, coding in C++, and compiling with g++. when I run my program (which is very small, [hangman]) i get: 'Segmentation fault (core dumped)'. So,

1. What does that mean?
2. Where does it come from/ where is the core being 'dumped'?
3. How do I fix that problem? or can I even fix it?

Thank you in advance. I'm kind of a novice Linux user as I am still learning a lot of things.

---

### Post by lisati on 2012-10-16
*Thread moved to **Programming Talk**.*

Welcome to the forum.

Sometimes a segmentation fault can be a symptom of a rogue pointer.

---

### Post by drdos2006 on 2012-10-16
Install CodeBlocks from the package manager and run your program in debugging mode. Then when you get your "segmentation fault" you will be able to use the backtrace to find out which part of your program is causing the error.

regards

---

### Post by Bachstelze on 2012-10-16
1. Very basically, it means your program is trying to access a memory area it is not suposed to.

2. To the current directoy.

3. You need to make sure your program doesn't do 1..

---

### Post by spjackson on 2012-10-17
The default behaviour on Ubuntu is that no core file is actually written, despite the message. If you have a core, you can examine it with a debugger to find out where it crashed. You can enable core dumps for your current terminal session by
```

ulimit -c unlimited

```

---

### Post by jwbrase on 2012-10-17
> **mhaggard said:**
> 
1. What does that mean?

About the same thing that "XYZ has encountered a problem and needs to close" or "XYZ has stopped working" usually does on Windows.

A pointer in your program is pointing to memory that hasn't been malloc'ed yet, or you're trying to use a NULL pointer, or something of that sort.

> 
2. Where does it come from/ where is the core being 'dumped'?

A core file (or core dump) is a file containing the complete memory image of a process that has crashed. The name is a holdover from the days when most computers had [magnetic-core memory]("http://en.wikipedia.org/wiki/Magnetic-core_memory"). It's generally written, as Bachstelze said, to the current directory, although nowadays, since most computer users aren't programmers anymore, the default settings of modern OS's generally have to be changed for a core dump to actually be written after a crash (for non-programmers, core dumps just end up being extra files cluttering the filesystem that they don't know what to do with). 

> 
3. How do I fix that problem? or can I even fix it?

There's a bug somewhere in your code, most likely involving a pointer (the first order of business whenever you see "Segmentation fault" or "SIGSEGV" is to double-check all the pointers in your code). Without seeing your code, we can't say exactly what it is. To fix the segfault problem you have to find and fix the bug.

---

### Post by mhaggard on 2012-10-17
Thanks for the welcome. Everybody replied so fast. I appreciate y'alls input already. For what it's worth, here is my code. It works on my windows machine without a problem. It is unfinished btw, just a homework assignment for my c++ class. I can't find any bugs... anymore input would be amazing. You guys have been great so far. 

```

#include <iostream> //every program has this.
#include <cstdlib> //standard library.
#include <ctime> //for random.
#include <fstream> //for reading and writing to a file.
#include <string>

using namespace std;

int main(){
  ifstream infile;
  ofstream outfile;
  
  int x;
  int word_length;
  
  string word_selection;
  string words[100];
  
  char letter_bank[100]; // holds the letters of the selected word.
  char play; // for continuation of the game. 
  
  cout << "Would you like to play hangman? (Enter y or n): ";
  cin >> play;
  
  if(play == 'y' || play == 'Y'){
  
	infile.open("hangman_input.txt");
  
	while(infile){
		infile >> x; 
		for (int i = 0; i < x; i++){
			infile >> words[i];
			}
		}
	
	long  seed = time(NULL); // gets current time
	srand(seed);
	int random_num = rand() % x; // Computer's random selection
	
	cout << random_num << endl;	
	cout << random_num << endl;
	
	word_selection = words[random_num]; // This is the word we will play hangman with.
	
	word_length = word_selection.length();
	cout << word_selection << " is " << word_length << " letters long" << endl;
	
	
	
	
	
	// Below is the end of the YES option...
	}
	
	
	else{
		cout << "Good bye." << endl;
		}
	
	

	cout << "This is the value for x: " << x <<  endl; 
  return 0;
  }

```

---

### Post by spjackson on 2012-10-17
What happens if x > 100?

---

### Post by trent.josephsen on 2012-10-17
I was going to complain about your indentation, but then I noticed you're using [Banner style](http://en.wikipedia.org/wiki/Indent_style#Banner_style) pretty consistently. Props for consistency I guess, but it's still hard to read. At least line up the "else" with its corresponding "if".

---

### Post by mhaggard on 2012-10-17
> **spjackson said:**
> What happens if x > 100?

if x gets bigger than 100 hundred, it will just change to that number. In the instructions, we aren't supposed to have more than 100 words anyways. Nevertheless, that number just changes to what ever it needs to be. Can you declare an array without giving some number of items in that array?

>  Originally posted by **trent.josephsen**
 I was going to complain about your indentation, but then I noticed you're using [Banner style]("http://en.wikipedia.org/wiki/Indent_style#Banner_style")  pretty consistently. Props for consistency I guess, but it's still hard  to read. At least line up the "else" with its corresponding "if".     Yea I do need to correct the else indentation. I didn't notice it. Thanks. How would you suggest I write it? For readability I mean...  Thanks in advance.

---

### Post by mhaggard on 2012-10-17
> **drdos2006 said:**
> Install CodeBlocks from the package manager and run your program in debugging mode. Then when you get your "segmentation fault" you will be able to use the backtrace to find out which part of your program is causing the error.

regards

ok awesome. Thanks. I already had code blocks installed. I will try that now.

---

### Post by lisati on 2012-10-17
> **mhaggard said:**
> if x gets bigger than 100 hundred, it will just change to that number. In the instructions, we aren't supposed to have more than 100 words anyways. Nevertheless, that number just changes to what ever it needs to be. Can you declare an array without giving some number of items in that array?

What happens when someone sneaks in more than 100 words? What happens to the words that won't fit into the array?

---

### Post by MG&amp;TL on 2012-10-17
> **mhaggard said:**
> if x gets bigger than 100 hundred, it will just change to that number. In the instructions, we aren't supposed to have more than 100 words anyways. Nevertheless, that number just changes to what ever it needs to be. Can you declare an array without giving some number of items in that array?

Not really, no. I would recommend using something like std::vector however: [http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/)

Btw, this will happen a lot. Get used to it. :)

---

### Post by mhaggard on 2012-10-17
Never mind... :neutral: I figured out what I was doing wrong. I didn't have the input file in the same folder as the code. It was giving me the error because I was telling it to read from a file that didn't exist... Ha. I'm a smart one. thanks alot guys and/or gals. Sorry I wasted everyone's time. I will consider this thread officially solved.

---

### Post by muteXe on 2012-10-18
I don't think open() from ifstream causes a segfault if it can't find the file?

---

### Post by Tony Flury on 2012-10-18
The open might not segfault, but attempting to use infile without checking that the open worked might well cause it too.

---

### Post by Zugzwang on 2012-10-18
> **Tony Flury said:**
> The open might not segfault, but attempting to use infile without checking that the open worked might well cause it too.

Actually that would also not segfault. But after reading to the variable x in the program posted above, variable x contains uninitialised data, and then the reading loop can store data into array elements beyond its size as the loop condition might be satisfied for many many iterations.

---

### Post by mhaggard on 2012-10-18
Wow, I am a little surprised at how much everyone knows here (not trying to insult anyone's intelligence or underestimate anyone). 

The problem was that i didn't check to see if the open worked and it was trying to read into the variable x. There was no data to read into it, so I assume it just sent itself into an infinite loop. Right? I am not sure if I am explaining it correctly.

---

### Post by Tony Flury on 2012-10-19
> **mhaggard said:**
> Wow, I am a little surprised at how much everyone knows here (not trying to insult anyone's intelligence or underestimate anyone). 

The problem was that i didn't check to see if the open worked and it was trying to read into the variable x. There was no data to read into it, so I assume it just sent itself into an infinite loop. Right? I am not sure if I am explaining it correctly.

The infinite loop would not cause the segfault on its own. the Segfault was almost certaily caused by x being rubbish afte attempting to read and ending up being a number well outside the array - it is that will cause the segfault.

---

### Post by trent.josephsen on 2012-10-20
> **mhaggard said:**
> Yea I do need to correct the else indentation. I didn't notice it. Thanks. How would you suggest I write it? For readability I mean...  Thanks in advance.

K&R and Allman are both styles I've seen used in my experience with C, Java and Perl. The thing those all have that banner style doesn't is that the terminating brace is indented to the same level as the line containing the opening brace, which makes it easy to identify the controlling statement of a particular block simply by scanning upward from the terminating brace.

I prefer K&R style personally. People say it makes it easy to lose the opening brace against the controlling statement, but I find that when I'm reading code I more frequently want to find the controlling statement itself and not just the opening brace.

<digression, you may feel free to skip>

I like to think of control structures as statements that just happen to contain blocks. When I have to break a statement over multiple lines, I indent the first and last lines the same as the lines around them, and indent the lines in between relative to that.

```
while (condition) {
    ...
}
```

I do a similar thing with long function calls, or long lists in Perl:

```
@ary = qw(
    element-1
    element-2
    ...
    element-3
);
foo(
    arg_1,
    arg_2,
    ...
    arg_N
);
```

</digression>

Probably the strongest argument against using a style that doesn't line up the terminating brace with the line containing its partner is that *most*, maybe 99% or more of C or C-like code is written in one of [these four styles](http://www.catb.org/jargon/html/I/indent-style.html), which all use that convention. If you reject it you stand to frustrate that 99%, including potential contributors. And if you think people wouldn't refuse to work on a project just because of the indent style, think again... ;)

---

### Post by dwhitney67 on 2012-10-20
K&R style is ok, but it pisses me off to no end when I see programmers use it, and then insert a blank like before the first statement within the block.  For example:
```

if (condition == true) {

    /* do something here */
}

```
Another example, when performing a do-while loop:
```

do {
    /* do something here */

} while (condition == false);

```
Forget K&R... the coding style was probably dictated by book publishers that wanted to conserve line-space when printing books.  It really sucks!

IMO (or IMHO if you prefer), the Allman style really is the best.

But seriously, there's no need to fret about coding style.  One can always program in their preferred style, and then pass their code through some "beautifier" that converts it into the style preferred by the person that matters the most... that is, the person that pays one's paycheck.

---

### Post by trent.josephsen on 2012-10-20
The ugly thing I really hate about Allman is this thing:

```
}
else
{
```

I mean, seriously? It takes 3 lines just to end one block and start another? :-P

But it's really about personal preference.

Re:beautifiers, I've taken to running almost every bit of code found on this forum through `indent -kr` as a preemptive measure before trying to troubleshoot :)

---

