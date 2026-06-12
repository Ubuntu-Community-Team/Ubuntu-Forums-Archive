---
title: "C++ accesing terminal"
date: 2007-01-01
forum: Programming Talk
---

### Post by s_h_a_d_o_w_s on 2007-01-01
I'm writing a C++ program to add lyrics to a song using eyeD3. This is what I have so far:

```
#include <iostream>
#include <string>

using namespace std;

int main ()

{

string dir;
string lyr;

cout<< "music file directory: " ;
cin >> dir;
cout<< "lyrics: " ;
cin >> lyr;

```What I wanted to know is how to I tell the program to run a command to the terminal, say xterm? Any help would be appreciated.

---

### Post by Kiwinote on 2007-01-01
```
system("xterm");
```

---

### Post by s_h_a_d_o_w_s on 2007-01-01
Great! that opens up the xterm, thanks a lot! But how do I ad text to appear in the terminal? 

Becasue i want to run the command, so I oppened the xterm but how can I add text in the oppened xterm?

---

### Post by s_h_a_d_o_w_s on 2007-01-01
I just realised I could:

system("command")

But how could I add strings to that?

---

### Post by Wybiral on 2007-01-01
I dont get the question...

Doing something like...

system("ls")

is the same as entering it into the terminal manually.

In c++...

cout << "ls"

Will print the letters "ls" to the terminal the same way "echo" does.

So you can send commands to the terminal and print text to it, what else are you wanting to do?

---

