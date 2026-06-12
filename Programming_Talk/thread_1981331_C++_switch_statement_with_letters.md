---
title: "C++ switch statement with letters"
date: 2012-05-16
forum: Programming Talk
---

### Post by bobman321123 on 2012-05-16
I'm trying to make a program that accepts string input and outputs it as ASCII art.
In order to do this, I have to search for each letter and use the function for that letter.

I was thinking of doing it something like this: 
```
for(int cout=0; cout<exambleString.length();cout++){
  switch(exampleString.at(count){
  case 'a': LetterA();
  break;
  case 'b': LetterB();
  break;
 .............................
.........................
//you get the idea
}
}

```

---

### Post by bobman321123 on 2012-05-16
But every time I try compiling that, it ends up being something like this....
```
stringCompare.cpp:9:8: error: case label does not reduce to an integer constant

```

---

### Post by PaulM1985 on 2012-05-16
I am not sure if it is because you have posted an example of your code, but your switch line does not have enough ")".

Yours:
```

switch(exampleString.at(count){

```

Should be:
```

switch(exampleString.at(count)) {

```

May be something else, I just noticed that.

Paul

EDIT:
This works:
```

#include <stdio.h>

int main()
{
	printf("Started");

	char aChar = 'c';
	switch (aChar)
	{
	case 'c':
		printf("It is c");
		break;
	default:
		printf("Not c");
		break;
	}


return 0;
}

```

---

### Post by bobman321123 on 2012-05-16
Here's the complete code:
```


#include <iostream>
#include <string>
using namespace std;

int main(){
	string foo="able";
	cout << foo[1] << endl;
	switch(foo.at(1)){
		case "a": cout << "a";
		break;
		case "b": cout << "b";
		break;
		case "l": cout << "l";
		break;
		case "e": cout << "e";
		break;
		default: cout << "Something didn't work...." << endl;
		break;
	}
	return 0;
}

```

and the complete errors:

```
josh@Nero:~/Coding/C/C++/testing$ g++ -Wall -pedantic -o ./stringCompare.o stringCompare.cpp 
stringCompare.cpp: In function ‘int main()’:
stringCompare.cpp:9:8: error: case label does not reduce to an integer constant
stringCompare.cpp:11:8: error: case label does not reduce to an integer constant
stringCompare.cpp:13:8: error: case label does not reduce to an integer constant
stringCompare.cpp:15:8: error: case label does not reduce to an integer constant

```

---

### Post by PaulM1985 on 2012-05-16
You cases use " which indicate you want a string.  A ' means that it is a character.  Your case labels look like you want to compare the strings of a, b, l, e rather than the characters.

Paul

---

### Post by kingtaurus on 2012-05-16
> **bobman321123 said:**
> I'm trying to make a program that accepts string input and outputs it as ASCII art.
In order to do this, I have to search for each letter and use the function for that letter.

I was thinking of doing it something like this: 
```
for(int cout=0; cout<exambleString.length();cout++){*
  switch(exampleString.at(count){*
  case 'a': LetterA();
  break;
  case 'b': LetterB();
  break;
 .............................
.........................
//you get the idea
}
}

```

(1) Don't use cout; (it looks too similar to std::cout)
(2) I assume that you have a typos at lines marked with * (and are meaning to use count);
(3) What is the type of exampleString? (assuming std::string)
(4) Your editted first post contains a different error (using double quotes rather than single quotes when switching on char);

Below is what I'm guessing you might be after:
 
```

#include <string>
#include <iostream>
int LetterA()
{
  std::cout << "a" << std::endl;
  return 0;
}
int LetterB()
{
  std::cout << "b" << std::endl;
  return 1;
}

int main()
{
  std::string exampleString = "aaabbbcc";
  for(int pos=0; pos < exampleString.length(); ++pos){
    switch (exampleString.at(pos))
    {
      case 'a': LetterA();
      break;
      case 'b': LetterB();
      break;
      default:
      break;
    }
  }
  return 0;
}


```

---

### Post by bobman321123 on 2012-05-16
Ok, so how would I write a switch that would compare foo.at(1) with the letter a?

---

### Post by bobman321123 on 2012-05-16
Thanks, :)
"cout" was supposed to be "count" :P

btw, your example worked perfectly.
What was I doing wrong?

---

### Post by Simian Man on 2012-05-16
> **bobman321123 said:**
> Thanks, :)
"cout" was supposed to be "count" :P

btw, your example worked perfectly.
What was I doing wrong?

Your problem as PaulM1985 said is that you used the double quote " instead of single quote '.  Double quotes are for strings of many characters while single quotes are for only one.  One character can be reduced to an integer (using the ASCII code), whereas a string cannot (not a small integer anyway).  Switches, as the error message informed you, need the case statements to be integers or something that can reduce to integers.

---

### Post by David Andersson on 2012-05-16
> **bobman321123 said:**
> 
What was I doing wrong?

1) You supplied source code and error messages in two posts. After each PaulM explained what was wrong.

[QUOTE=bobman321123]I'm trying to make a program that accepts string input and outputs it as ASCII art.[/QUOTE]

2) If the task is to produce fancy ascii-art text, and not to learn C++, then try Figlet. First install package *figlet*. Then try these commands:
```
figlet Hello World
figlet -k Hello World
figlet -f slant Hello World
figlet -f lean Hello World
```

3) If the task is to learn C++ programming using this problem as an example, then *also* try a solution where you look up in an *array* what to output for each character, instead of *switching* to different program statements. (Data driven programming.)

---

### Post by bobman321123 on 2012-05-16
> **David Andersson said:**
> 1) You supplied source code and error messages in two posts. After each PaulM explained what was wrong.



2) If the task is to produce fancy ascii-art text, and not to learn C++, then try Figlet. First install package *figlet*. Then try these commands:
```
figlet Hello World
figlet -k Hello World
figlet -f slant Hello World
figlet -f lean Hello World
```

3) If the task is to learn C++ programming using this problem as an example, then *also* try a solution where you look up in an *array* what to output for each character, instead of *switching* to different program statements. (Data driven programming.)

I haven't quite got that far in C++ yet, I'm not quite sure how I'd use an array to fit functions.

---

### Post by Lux Perpetua on 2012-05-17
> **bobman321123 said:**
> I haven't quite got that far in C++ yet, I'm not quite sure how I'd use an array to fit functions.That's possible with function pointers, but a cleaner approach is to abstract away the common logic from all those functions into a single function. Then you don't need to use the character to look up a function; you only need to look up some data (a string? A sequence of strings? I don't know what you're really after), which you feed into your one master function. Once you adopt that idea, you're also more flexible as to how that data gets into your array. When you're calling a different function for each letter, you're forced to modify the source code whenever you want to change the behavior for any letter. When you're just looking up data, the data can be compiled in, or you can store the data separately in a different file, and your program can load the data from the file when it starts. The second way is slightly more difficult to design and code, but it can save you time down the road if you find yourself tweaking the output a lot.

---

### Post by bobman321123 on 2012-05-17
> **Lux Perpetua said:**
> That's possible with function pointers, but a cleaner approach is to abstract away the common logic from all those functions into a single function. Then you don't need to use the character to look up a function; you only need to look up some data (a string? A sequence of strings? I don't know what you're really after), which you feed into your one master function. Once you adopt that idea, you're also more flexible as to how that data gets into your array. When you're calling a different function for each letter, you're forced to modify the source code whenever you want to change the behavior for any letter. When you're just looking up data, the data can be compiled in, or you can store the data separately in a different file, and your program can load the data from the file when it starts. The second way is slightly more difficult to design and code, but it can save you time down the road if you find yourself tweaking the output a lot.


Here's my final program I made, just so you can see what I was going for. 
If you have any suggestions for improvements, they'd be much appreciated. :)

```
#include <iostream>
#include <string>
using namespace std;
void Lettera(){
    cout <<"   A" << endl;
    cout <<"  A A" << endl;
    cout <<" A A A" << endl;
    cout <<"A     A" << endl;
    cout << endl << endl;
}
void Letterb(){
    cout << "BBBB"<< endl;
    cout << "B   B"<< endl;
    cout << "BBBB"<< endl;
    cout << "B   B"<< endl;
    cout << "BBBB"<< endl;
    cout << endl << endl;
}
void Letterc(){
    cout << "  CCCC"<< endl;
    cout << " CC" <<endl;
    cout << "CC" << endl;
    cout << " CC" << endl;
    cout << "  CCCC"<< endl;
    cout << endl << endl;
}
void Letterd(){
    cout << "DDDDD" << endl;
    cout << "DD  DD"<< endl;
    cout << "DD   DD"<< endl;
    cout << "DD  DD"<< endl;
    cout << "DDDDD" << endl;
    cout << endl << endl;
}
void Lettere(){
    cout << "EEEEEEE" << endl;
    cout << "EE" << endl;
    cout << "EEEE"<< endl;
    cout << "EE" << endl;
    cout << "EEEEEEE" << endl;
    cout << endl << endl;
}
void Letterf(){
    cout << "FFFFFFF" << endl;
    cout << "FF" << endl;
    cout << "FFFF" << endl;
    cout << "FF" << endl;
    cout << "FF" << endl;
    cout << "FF" << endl;
    cout << endl << endl;
}
void Letterg(){
    cout << " GGGGGG" << endl;
    cout << "GG" << endl;
    cout << "GG   GG" << endl;
    cout << "GG    G" << endl;
    cout << " GGGGG" << endl;
    cout << endl << endl;
}
void Letterh(){
    cout << "HH   HH" << endl;
    cout << "HH   HH" << endl;
    cout << "HHHHHHH" << endl;
    cout << "HH   HH" << endl;
    cout << "HH   HH" << endl;
    cout << endl << endl;
}
void Letteri(){
    cout << "IIIIIIII" << endl;
    cout << "   II" << endl;
    cout << "   II" << endl;
    cout << "   II" << endl;
    cout << "IIIIIIII" << endl;
    cout << endl << endl;
}
void Letterj(){
    cout << "JJJJJJJJ" << endl;
    cout << "   JJ" << endl;
    cout << "   JJ" << endl;
    cout << "   JJ" << endl;
    cout << " JJJ" << endl;
    cout << endl << endl;
}
void Letterk(){
    cout << "KK   IK" << endl;
    cout << "KK  KK" << endl;
    cout << "KK KK" << endl;
    cout << "KK  KK" << endl;
    cout << "KK   KK" << endl;
    cout << endl << endl;
}
void Letterl(){
    cout << "LL" << endl;
    cout << "LL" << endl;
    cout << "LL" << endl;
    cout << "LL" << endl;
    cout << "LLLLLL" << endl;
    cout << endl << endl;
}
void Letterm(){
    cout << "MM MM MM" << endl;
    cout << "M M  M M" << endl;
    cout << "M M  M M" << endl;
    cout << "M M  M M" << endl;
    cout << endl << endl;
}
void Lettern(){
    cout << "NN   NN" << endl;
    cout << "NNN  NN" << endl;
    cout << "NN NNNN" << endl;
    cout << "NN  NNN" << endl;
    cout << "NN   NN" << endl;
    cout << endl << endl;
}
void Lettero(){
    cout << " 00000" << endl;
    cout << "00   00" << endl;
    cout << "00   00" << endl;
    cout << "00   00" << endl;
    cout << "00   00" << endl;
    cout << " 00000" << endl;
    cout << endl << endl;
}
void Letterp(){
    cout << "PPPPP" << endl;
    cout << "PP  PP" << endl;
    cout << "PP  PP" << endl;
    cout << "PPPPP" << endl;
    cout << "PP" << endl;
    cout << "PP" << endl;
    cout << "PP" << endl;
    cout << endl << endl;
}
void Letterq(){
    cout << " QQQQ" << endl;
    cout << "QQ  QQ" << endl;
    cout << "QQ QQQ" << endl;
    cout << "QQ  QQQ" << endl;
    cout << " QQQQ Q";
}
void Letterr(){
    cout << "RRRRR" << endl;
    cout << "RR  RR" << endl;
    cout << "RR  RR" << endl;
    cout << "RR RR" << endl;
    cout << "RRRR" << endl;
    cout << "RR RR" << endl;
    cout << "RR  RR" << endl;
    cout << endl << endl;
}
void Letters(){
    cout << " SSSS" << endl;
    cout << "SS   S" << endl;
    cout << " SS " << endl;
    cout << "  SS" << endl;
    cout << "   SS" << endl;
    cout << "S   SS" << endl;
    cout << " SSSS" << endl;
    cout << endl << endl;
}
void Lettert(){
    cout << "TTTTTTTT" << endl;
    cout << "   TT" << endl;
    cout << "   TT" << endl;
    cout << "   TT" << endl;
    cout << "   TT" << endl;
    cout << endl << endl;
}
void Letteru(){
    cout << "UU   UU" << endl;
    cout << "UU   UU" << endl;
    cout << "UU   UU" << endl;
    cout << "UU   UU" << endl;
    cout << " UUUUU" << endl;
    cout << endl << endl;
}
void Letterv(){
    cout << "VV   VV" << endl;
    cout << "VVV VVV" << endl;
    cout << " VV VV" << endl;
    cout << " VVVVV" << endl;
    cout << "  VVV" << endl;
    cout << "   v" << endl;
    cout << endl << endl;
}
void Letterw(){
    cout << "WW  WW  WW" << endl;
    cout << " WWWWWWWW" << endl;
    cout << "  WW  WW" << endl;
    cout << "   W  W" << endl;
    cout << endl << endl;
}
void Letterx(){
    cout << "XX    XX" << endl;
    cout << " XX  XX" << endl;
    cout << "  XXXX" << endl;
    cout << " XX  XX" << endl;
    cout << "XX    XX" << endl;
    cout << endl << endl;
}
void Lettery(){
    cout << "YY  yy" << endl;
    cout << " YYYY" << endl;
    cout << "  YY" << endl;
    cout << "  YY" << endl;
    cout << "  YY" << endl;
    cout << endl << endl;
}
void Letterz(){
    cout << "ZZZZZZ" << endl;
    cout << "   ZZ" << endl;
    cout << "  ZZ" << endl;
    cout << " ZZ" << endl;
    cout << "ZZZZZZ" << endl;
    cout << endl << endl;
}
void PrintLetters(string input){
    for(unsigned int count=0; count < input.length(); count++){

        switch(input.at(count)){
            case 'a': Lettera();
            break;
            case 'b': Letterb();
            break;
            case 'c': Letterc();
            break;
            case 'd': Letterd();
            break;
            case 'e': Lettere();
            break;
            case 'f': Letterf();
            break;
            case 'g': Letterg();
            break;
            case 'h': Letterh();
            break;
            case 'i': Letteri();
            break;
            case 'j': Letterj();
            break;
            case 'k': Letterk();
            break;
            case 'l': Letterl();
            break;
            case 'm': Letterm();
            break;
            case 'n': Lettern();
            break;
            case 'o': Lettero();
            break;
            case 'p': Letterp();
            break;
            case 'q': Letterq();
            break;
            case 'r': Letterr();
            break;
            case 's': Letters();
            break;
            case 't': Lettert();
            break;
            case 'u': Letteru();
            break;
            case 'v': Letterv();
            break;
            case 'w': Letterw();
            break;
            case 'x': Letterx();
            break;
            case 'y': Lettery();
            break;
            case 'z': Letterz();
            break;
            case ' ': cout << endl << endl << endl;
            break;
            default: cout << "Ya can't input numbers, capitals, or spaces, goof." << endl;
            break;
        }
}
}
int main(){
    string input;
    while (1){
    while(input.empty()){
        cout << "Please input a word(type 'lucky ducky' to stop): " << endl;
        getline(cin, input);
    }
    for (int num; num < input.length(); num++){

    }
    if (input=="lucky ducky"){
        break;
    }
    else{
        PrintLetters(input);
    }
    input.clear();
    }

    return 0;
}

```

---

### Post by PaulM1985 on 2012-05-17
What is 
```

    for (int num; num < input.length(); num++){

    }

```
for?

---

### Post by David Andersson on 2012-05-17
> **bobman321123 said:**
> 
If you have any suggestions for improvements


1) The *end flag* should be something more logical, like the empty string or "quit", not "lucky ducky".

2) The *error message* for unsupported chars is a) wrong and b) rude. a) It says space is not supported, but it seems it is. b) I'm not fluent in english, but the urban dictionary suggest calling a user "goof" would be impolite, especially as it is not the users fault that certain chars are not supported.

3) *Orientation*. One can enter a string of characters, like "Hello World". One writes them horizontally, left to right, but they will be output vertically, top to bottom.

---

### Post by David Andersson on 2012-05-17
> **bobman321123 said:**
> 
If you have any suggestions for improvements


(The comments 1-3 in previous post was about the programs behaviour. This post is about implementation details.)

4) *Indentation*. The content of the "while(1)"-loop is not indetet. (I know I have faild to indent code when I add an outer loop, but I wouldn't publish it in that state.)

5) *Variable initialization*. Let's talk about the final "input.clear()"-statement. Logically it belongs to the "while(input.empty())"-loop test. When entering that loop the input-variable must be empty, so the loop will actually ask the user at least once for a new string. So I would put the "input.clear()"-statement right before that loop. I can see why it wasn't placed there in the first place. The first round in the outer "while(1)"-loop the input-variable is already empty, it hasn't been used yet, so no need to clear it, it seems. At the beginning of the second round it must be empty again, so it must be cleared somewhere. Maybe clear it when its value is not needed anymore, that is, at the end of the loop. It works, but I think it is bad style. The reason the input-variable must be empty is for the "while(input.empty())"-loop to behave as we want, put the statement that assures the value close to that loop entrance, preferably right before it.

5b) If you move the "string input;"-declaration inside the "while(1)"-loop you would not need any "input.clear()"-statement anywhere.

6) And now *Data driven programming*. See the code below. It declares a variable *bigfont* that is an *array* of *strings*. Arrays in C/C++ is indexed with integers, but chars are like integers, so arrays can be indexed with chars. I can access one of the strings in the *bigfont* by indexing it like this: bigfont['a']. In the example below only three strings are initialized. Complete the code with only the "main()"-program from your previous post and it should work.

Advantages of this solution: a) You don't have to declare a new function and invent a new function name for each new letter supported. b) Change the array to a dictionary and you can support thousands or millions of letters (needed when you go unicode). c) You can read the bigfont strings from a file instead of beeing constant values in the program, thus making it possible to add new letters or change how letters look without re-compiling the program.

```

#include <iostream>
#include <string>
using namespace std;

string bigfont[128];

void init() {
  bigfont['a'] = "\
    *     \n\
   ***    \n\
  ** **   \n\
 *******  \n\
**     ** \n\
";

  bigfont['b'] = "\
********  \n\
 **    ** \n\
 *******  \n\
 **    ** \n\
********  \n\
";

  bigfont['c'] = "\
 *******  \n\
**        \n\
**        \n\
**        \n\
 *******  \n\
";
}

void PrintLetters(string input) {
  for(int count=0; count < input.length(); ++count) {
    string bigletter = bigfont[input.at(count)];
    if (bigletter=="") {
      cerr << "I am terribly sorry but letter " << input.at(count) << " is not supported" << endl;
    } else {
      cout << bigfont[input.at(count)] << endl;
    }
  }
}

(add main() here)

```

---

### Post by 11jmb on 2012-05-18
If you can get the basics working for this, one fun "advanced" feature might be to print a bunch of characters in a single line. To do this, a variation of David Andersson's implementation would probably be your best bet. Instead of each character being represented as a single string with line breaks, each would be represented as an array of strings, one string for each line. 

then you could do something like:

```


void print_single_line(std::string text, 
                       std::map<char, std::vector<std::string>> font)
{
    //left as exercise to reader :P
}


```

---

### Post by bobman321123 on 2012-05-18
> **PaulM1985 said:**
> What is 
```

    for (int num; num < input.length(); num++){

    }

```for?
It's to go through the word and convert each letter.

---

### Post by bobman321123 on 2012-05-18
> **David Andersson said:**
> 1) The *end flag* should be something more logical, like the empty string or "quit", not "lucky ducky".

2) The *error message* for unsupported chars is a) wrong and b) rude. a) It says space is not supported, but it seems it is. b) I'm not fluent in english, but the urban dictionary suggest calling a user "goof" would be impolite, especially as it is not the users fault that certain chars are not supported.

3) *Orientation*. One can enter a string of characters, like "Hello World". One writes them horizontally, left to right, but they will be output vertically, top to bottom.
1) The program was originally intended to be just for me, to try to teach myself C++, and had no intention of publishing it, so I happened to feel like making the end phrase silly.
2) "Goof" isn't an insulting word. It's more of a "oh you silly" type of thing. It might be insulting in some circles (where words have different definitions), but not where I'm from.
3) Well, I'm not quite sure how I would make it output horizontally, so I didn't really try. This is more a proof of concept thing for me.

---

### Post by 11jmb on 2012-05-18
I will say that it may be in your best interest to cut back on the cheeky comments/variable names/debug printouts/etc. You never know which project might turn into something interesting that you keep adding to over months or years. It may turn into something that you would want to hand over to an employer as an example of your coding ability or a collaborative project. 

This is mostly advice from personal experience. Years ago, I had a few projects that I had pretty much done just for fun/learning that turned into pretty interesting applications. After talking about one of these projects in an interview, I was asked if I would want to pass the code along to the employer as an example of my abilities. This project was riddled with cheeky comments, insulting error messages, and swear words, because I thought it was funny as an undergrad. I spent weeks cleaning up the code. 

I'm not admonishing you or anything, but just advising that maintaining a professional style, even for personal projects, is a very good practice.

---

### Post by bobman321123 on 2012-05-18
> **11jmb said:**
> I will say that it may be in your best interest to cut back on the cheeky comments/variable names/debug printouts/etc. You never know which project might turn into something interesting that you keep adding to over months or years. It may turn into something that you would want to hand over to an employer as an example of your coding ability or a collaborative project. 

This is mostly advice from personal experience. Years ago, I had a few projects that I had pretty much done just for fun/learning that turned into pretty interesting applications. After talking about one of these projects in an interview, I was asked if I would want to pass the code along to the employer as an example of my abilities. This project was riddled with cheeky comments, insulting error messages, and swear words, because I thought it was funny as an undergrad. I spent weeks cleaning up the code. 

I'm not admonishing you or anything, but just advising that maintaining a professional style, even for personal projects, is a very good practice.

Yeah, that makes sense :)
I'll keep that in mind.
Professionalism, here I come.

---

