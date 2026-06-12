---
title: "Working with C and code::blocks"
date: 2011-07-14
forum: Programming Talk
---

### Post by Avidanborisov on 2011-07-14
Hi, I am learning C with the book teach yourself C in 21 days. I work with code::blocks IDE. The book often provides some code to paste into the editor, but the problem is that commands that use quotes are formatted in the book as curly quotes, and when I paste them into code::blocks or any other editor, I need to manually change it so it could be compiled. Is there any way to convert this automatically while pasting into code::blocks?

---

### Post by sanguinoso on 2011-07-14
Most editors have a find and replace feature to facilitate the process.

---

### Post by Bachstelze on 2011-07-14
This is a very bad book if the code is not machine-readable.

---

### Post by Avidanborisov on 2011-07-14
> **Bachstelze said:**
> This is a very bad book if the code is not machine-readable.

Actually I have heard that the book is great, but this is just that tiny problem. In the book it doesn't even look curly. Anyway, I know I can replace it but can it be automatic for every time I copy? Or is there any way to modify the PDF?

---

### Post by cgroza on 2011-07-14
> **Avidanborisov said:**
> Actually I have heard that the book is great, but this is just that tiny problem. In the book it doesn't even look curly. Anyway, I know I can replace it but can it be automatic for every time I copy? Or is there any way to modify the PDF?
You are copying from a PDF? Maye it's because of the PDF because I tried to copy from a LaTeX generated PDF once and all the special characters were corrupted...

---

### Post by Avidanborisov on 2011-07-15
> **cgroza said:**
> You are copying from a PDF? Maye it's because of the PDF because I tried to copy from a LaTeX generated PDF once and all the special characters were corrupted...

Yes, the book is in PDF format.
So, does anyone have an idea? how can I automatically replace text when copied?

---

### Post by Vaphell on 2011-07-15
not trivial, replace (ctrl+r) in cb won't do? care to show an example of malformed code?

---

### Post by Avidanborisov on 2011-07-15
> **Vaphell said:**
> not trivial, replace (ctrl+r) in cb won't do? care to show an example of malformed code?

I know I can replace manually, I just asked if there is any way to do it automatically? is there any place for placing simple scripts in code blocks for text processing? 
example:

```
/* Program to calculate the product of two numbers. */
#include <stdio.h>
int val1, val2, val3;
int product(int x, int y);
int main( void )
{
/* Get the first number */
printf(“Enter a number between 1 and 100: “);
scanf(“%d”, &val1);
/* Get the second number */
printf(“Enter another number between 1 and 100: “);
scanf(“%d”, &val2);
/* Calculate and display the product */
val3 = product(val1, val2);
printf (“%d times %d = %d\n”, val1, val2, val3);
return 0;
}
/* Function returns the product of the two values provided */
int product(int x, int y)
{
return (x * y);
}
```

---

### Post by Vaphell on 2011-07-15
sudo apt-get install xsel

ctrl+c scanf(&#8220;%d&#8221;, &val1);
```
xsel -bo
scanf(&#8220;%d&#8221;, &val1);
```

now playing with contents of the clipboard
```
xsel -bo | sed -r 's/[&#8220;&#8221;]/"/g' | xsel -bi
```
in short: print content, replace &#8220;&#8221; with " and put into clipboard

```
xsel -bo
scanf("%d", &val1);
```
now ctrl+v will paste the good version

create a script with that 3 part line and add it to Tools menu in codeblocks or globally to system hotkey configuration with combination let's say ctrl+f12, so you can do ctrl+c, ctrl+f12 to modify clipboard, ctrl+v.

---

### Post by Avidanborisov on 2011-07-15
> **Vaphell said:**
> sudo apt-get install xsel

ctrl+c scanf(“%d”, &val1);
```
xsel -bo
scanf(“%d”, &val1);
```

now playing with contents of the clipboard
```
xsel -bo | sed -r 's/[“”]/"/g' | xsel -bi
```
in short: print content, replace “” with " and put into clipboard

```
xsel -bo
scanf("%d", &val1);
```
now ctrl+v will paste the good version

create a script with that 3 part line and add it to Tools menu in codeblocks or globally to system hotkey configuration with combination let's say ctrl+f12, so you can do ctrl+c, ctrl+f12 to modify clipboard, ctrl+v.

Wow! thank you very much! this is just what I needed!
I have just another little problem. When I copy the code from the books it also has line numbers for convenience, for example:

```
2:
#include <stdio.h>
3:
#include <stdlib.h>
4:
5:
void display_usage(void);
6:
int line;
7:
8:
int main( int argc, char *argv[] )
```

Although in the PDF they are before the actual code, when you copy it, It goes to another line. so using your example above, how can I use for example sed to remove them? they are always in a separate line and they are formed as a number and then an ":".

---

### Post by Vaphell on 2011-07-15
```
xsel -bo | sed -r '/^[0-9]*:/d; s/[&#8220;&#8221;]/"/g' | xsel -bi
```

you don't get empty lines which were there for readability purposes but whatever :-)

---

### Post by Avidanborisov on 2011-07-15
> **Vaphell said:**
> ```
xsel -bo | sed -r '/^[0-9]*:/d; s/[“”]/"/g' | xsel -bi
```

you don't get empty lines which were there for readability purposes but whatever :-)

Thank you!
do you know also how to automatically tab it? (maybe not by this script but some code::blocks option?)

---

### Post by Vaphell on 2011-07-15
what do you mean by 'tab it'? if you mean autoformatting of code then in Settings/Editor/Source formatter you can choose a style and apply it to your code with Plugins/Source code formatter

---

### Post by Avidanborisov on 2011-07-16
> **Vaphell said:**
> what do you mean by 'tab it'? if you mean autoformatting of code then in Settings/Editor/Source formatter you can choose a style and apply it to your code with Plugins/Source code formatter

Thank you again! didn't know that. by the way, is there any keyboard shortcut for the source formatter?
Another question, every time I want to create another program I need to click on "Create New Project" -> "Files" -> "C/C++ Source" -> "C" -> Enter filename + path. Is there anyway to to make it remember everything until the filename + path?

---

### Post by Vaphell on 2011-07-16
> Thank you again! didn't know that. by the way, is there any keyboard shortcut for the source formatter?

you don't click much around the menus on your own, do you? :-)
Settings/Editor/Keyboard shortcuts, find code formatter and assign something.

no idea about the second question.

---

### Post by Avidanborisov on 2011-07-17
> **Vaphell said:**
> you don't click much around the menus on your own, do you? :-)
Settings/Editor/Keyboard shortcuts, find code formatter and assign something.

no idea about the second question.

Well, I didn't have "Keyboard Shortcuts" in the menu.
Anyway, I searched for it and it is apparently a 3rd party plugin that has to be installed by installing the package codeblocks-contrib.
Any ideas about the second question?

---

### Post by Avidanborisov on 2011-07-20
So is there any way to create a shortcut for "Create New Project" -> "Files" -> "C/C++ Source" -> "C" -> Enter filename + path?

---

### Post by JupiterV2 on 2011-07-20
You know, in the amount of time you've spent looking for an answer to this problem you could have typed out the code yourself. I'm willing to bet that you'd have better retention too.

---

### Post by Avidanborisov on 2011-07-20
> **JupiterV2 said:**
> You know, in the amount of time you've spent looking for an answer to this problem you could have typed out the code yourself. I'm willing to bet that you'd have better retention too.

You think I didn't?
Of course I code, that's the reason I am asking that...

---

