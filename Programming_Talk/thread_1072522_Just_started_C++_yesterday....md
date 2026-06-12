---
title: "Just started C++ yesterday..."
date: 2009-02-17
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-17
I have a slight problem I can not get the following to work. What is wrong? Please help. I made the file executable and it looks like the same thing as on the screen they told me to put in....so what is up? Thanx for any help...

---

### Post by Can+~ on 2009-02-17
Copy the command you're using to compile and execute it.

You should be using:

g++ -Wall "C++ Practice~1" -o executable
chmod u+x executable
./executable

---

### Post by StOoZ on 2009-02-17
next time paste the code here , and not supply images like that.

I can barely see something.

---

### Post by Leo Dragonheart on 2009-02-17
Well that may be what is wrong. I just click the build button and then click build and run....:( I am using Code Blocks.

---

### Post by Leo Dragonheart on 2009-02-17
> **StOoZ said:**
> next time paste the code here , and not supply images like that.

I can barely see something.

I am sorry. What do you mean past the code here? I was not using the terminal I was runing or trying to run it from code blocks...

---

### Post by Can+~ on 2009-02-17
You know what? completely drop the IDE. Open Gedit, add the bracket-matching, syntax highlighting and set the tabbing size to 4.

Grab gedit, write whatever you have to write, then open a terminal, go to the place where the file is and do

```
g++ -Wall "myfirstcode.cpp" -o executable
```
for compilation

```
chmod u+x executable
```
to make it executable

```
./executable 
```
and running it.

Learn how to code, compile and run. Don't waste time on a fancy IDE, when the main objective is to learn a language. Later you can explore IDEs.

If it doesn't compile, you're probably lacking the compiling tools, which are easily attainable with:

```
sudo apt-get install build-essential
```

---

### Post by leg on 2009-02-17
My first guess would be to remove that cin.get() statement and then try again. 
[edit] actually scrap that your errors are on line three and five and your first is can't find using. Make sure build-essentials is installed.

---

### Post by Leo Dragonheart on 2009-02-17
Ok I will try what you suggest CAN+~, but I did only start C++ yesterday...Oh I forgot, Where is gedit?

---

### Post by Leo Dragonheart on 2009-02-17
> **leg said:**
> My first guess would be to remove that cin.get() statement and then try again. 
[edit] actually scrap that your errors are on line three and five and your first is can't find using. Make sure build-essentials is installed.

I tried removing that like you said and I got permission denied this time.

---

### Post by Martin Witte on 2009-02-17
I think to read this (I added the return line, otherwise the program is not correct)
```
#include <iostream>

using namespace std;

int main()
{
    cout << "HEY, you I'm alive. Oh and Hello World!\n";
    cin.get();
    return 0; // main should always return an integer value
}

```

When I paste this in Code::Blocks it works, I guess either the build essentials package is not installed as Can + already suggested or Code::Blocks doesn point to GNU GCC compiler (in settings menu, compiler and debugger)

---

### Post by Leo Dragonheart on 2009-02-17
> **leg said:**
> My first guess would be to remove that cin.get() statement and then try again. 
[edit] actually scrap that your errors are on line three and five and your first is can't find using. Make sure build-essentials is installed.

Yes I have build essentials 11.4 latest version...

---

### Post by Leo Dragonheart on 2009-02-17
> **Martin Witte said:**
> I think to read this (I added the return line, otherwise the program is not correct)
```
#include <iostream>

using namespace std;

int main()
{
    cout << "HEY, you I'm alive. Oh and Hello World!\n";
    cin.get();
    return 0; // main should always return an integer value
}

```

When I paste this in Code::Blocks it works, I guess either the build essentials package is not installed as Can + already suggested or Code::Blocks doesn point to GNU GCC compiler (in settings menu, compiler and debugger)

I tried that same errors... Code Blocks does point to the GNU GCC compiler I think...

---

### Post by nvteighen on 2009-02-17
Believe us. You don't need an IDE till you get into a really complex project... It's usually much better to learn what the compiling process is by hand than clueless struggling against an IDE.

---

### Post by jimi_hendrix on 2009-02-17
> **nvteighen said:**
> Believe us. You don't need an IDE till you get into a really complex project... It's usually much better to learn what the compiling process is by hand than clueless struggling against an IDE.

vim is what i use

---

### Post by SledgeHammer_999 on 2009-02-17
How did you start the project in Code::Blocks? Maybe you chose "C project" instead of "C++ project" and codeblocks uses gcc instead of g++ to compile your source.

---

### Post by Leo Dragonheart on 2009-02-17
> **nvteighen said:**
> Believe us. You don't need an IDE till you get into a really complex project... It's usually much better to learn what the compiling process is by hand than clueless struggling against an IDE.

I totally agree with you all...I have completed 3 program tests and got them to work properly since this post a few hours ago. It is better to learn how to do it by hand first. I understand it way more now. Thx to everyone...;-)

---

