---
title: "First C app please help"
date: 2006-01-31
forum: Programming Talk
---

### Post by zootreeves on 2006-01-31
I've been messing around trying to learn glade/C and I'm trying to make a very simple calculator - just with two forms and it adds one to the other.

So I've created the UI with glade (see screenshot), but the program just crashes when I click apply (Add). Here's my callbacks.c file:

```
#ifdef HAVE_CONFIG_H
#  include <config.h>
#endif

#include <gnome.h>

#include "callbacks.h"
#include "interface.h"
#include "support.h"


void on_OK_clicked(GtkButton *button, gpointer user_data){
int numbone;
int numbtwo;
int output;


GtkWidget * entryone = lookup_widget(GTK_WIDGET(button), "entry3");
GtkWidget * entrytwo = lookup_widget(GTK_WIDGET(button), "entry4");
GtkWidget * entryout = lookup_widget(GTK_WIDGET(button), "EqualBox");


numbone = gtk_entry_get_text(GTK_ENTRY(entryone));
numbtwo = gtk_entry_get_text(GTK_ENTRY(entrytwo));

output = numbone + numbtwo;

gtk_entry_set_text(GTK_ENTRY(entryout),output);

}


```

The propblem I think is in this line:

output = numbone + numbtwo;

I can use:

output = numbone;

and I shows the first number in the total box, but It is when I try and add the number it goes wrong. I can't even use output = numbone + 2;

---

### Post by zootreeves on 2006-01-31
This is really frustrating. How to you add stuff?

If I do:
output= "2+2";

then it just puts 2+2 in the box, if I do

output= 2 + 2;

It crashes [-(

---

### Post by sapo on 2006-01-31
I dont know anything about C, but arent you trying to put a integer value in a string var?

Try using a int var or maybe convert integer to string :p

---

### Post by zootreeves on 2006-01-31
I new to the difference between int, char, var, I mostly use php so have never bothered with setting variable types.

I tried to use sprintf(output, "%", total); to convert the int to string, but it just crashes again.

To help find the error I tried this:
```
     total = numbone + numbtwo;

	printf("Number one = %d\n", numbone);
	printf("Number two = %d\n", numbtwo);
	printf("Number = %d\n", total);

```

Say If I put 3 in one box and 4 in  the other I would expect it to say:
Number one = 3
Number two = 4
Number = 7

But whatever number I put in it outputs:
Number one = 135123592
Number two = 135131392
Number = 270254984

---

### Post by rock freak on 2006-01-31
are you getting any errors when you re make it / ciompile it

---

### Post by lnostdal on 2006-01-31
you're doing a lot of wierd things .. i'm not going to bother telling you the answers (knowledge != answers) 

instead, look for "The C Programming Language" at Amazon.com or your local library.. they can probably order the book from an external library if they do not have it

---

### Post by zootreeves on 2006-01-31
Thanks for your replies. There are no errors during compilation, I am completely stumped...

Has anyone got the solution - I find it much easier to learn by example...

---

### Post by David Marrs on 2006-01-31
Check the [stdlib](http://www.gnu.org/software/libc/) docs for atoi().

int i = atoi("5");

PS. atoi is deprecated, according to the manual. User strtol instead.

---

### Post by rock freak on 2006-01-31
well this sounds alot like my a level computing tasks for the coursework so yes i do no how to do it and i shall do a example for you if you wish so you still have to learn how to implement it into your own code!

I find that its a good elarnign way as long as you understand what does what!!!

tell me if you would like tht example ;)

---

### Post by zootreeves on 2006-01-31
Finally! I got it to work. Here's the code in case any beginners are after something similiar:

```
#ifdef HAVE_CONFIG_H
#  include <config.h>
#endif

#include <gtk/gtk.h>
#include <stdlib.h>
#include <stddef.h>
#include <stdio.h>
#include <string.h>

#include "callbacks.h"
#include "interface.h"
#include "support.h"



void
on_Apply_clicked                       (GtkButton       *button,
                                        gpointer         user_data)
{


int total;
int totaltxt;
char totalready[80];

 GtkWidget *entry = lookup_widget(GTK_WIDGET(button), "entry4");
 int *entry_text = gtk_entry_get_text(GTK_ENTRY(entry));

 GtkWidget *entry2 = lookup_widget(GTK_WIDGET(button), "entry5");
 int *entry2_text = gtk_entry_get_text(GTK_ENTRY(entry2));

 GtkWidget *totalb = lookup_widget(GTK_WIDGET(button), "entry3");

 long int number1 = strtol(entry_text, NULL,  16);
 long int number2 = strtol(entry2_text, NULL,  16);
 total =  number1 + number2;

	//print in terminal
	printf("%d", total);
	g_print(entry_text);
	g_print(entry2_text);

totaltxt = "Total Is:";

sprintf(totalready, "%i", total);




gtk_entry_set_text(GTK_ENTRY(totalb),totalready);
}


```
I have also attached the glade file...

But now  have a new problem, But i don't think it is to do with my code, I think ubuntu/gcc is setup wrong:

If I put: #include <iostream.h> in calbacks.c then i get:
callbacks.c:10:22: error: iostream.h: No such file or directory

I think this is the cause of why if i use cout is says it is not declared. Anyone have any ideas? Thanks

---

### Post by jerome bettis on 2006-01-31
iostream and cout are C++ things not C

you want to #include <stdio.h> and use printf() for output

---

### Post by lnostdal on 2006-01-31
if you want to use C++ compile your code with g++ instead of gcc, and remember that #include <iostream.h> is deprecated (old and non-standard).. you should use #include <iostream> instead

---

### Post by rock freak on 2006-01-31
i dont get what you need from

> <iostream.h>

all you need is

```
#include <stdio.h>
```

unless there is more c code???

---

### Post by zootreeves on 2006-01-31
I was just messing around using different functions - but I didn't realise the tutorial I was reading was for C++. 

The most annoying thing I have found about C so far is that when you try and look anything up on google there is no good documentation and because 'C' (It's not like 'C++' or 'Python') is such a broad term the documentation that is there is mixed up with other useless stuff.

---

### Post by lnostdal on 2006-01-31
I use the glibc manual and the man-pages for this: [http://www.gnu.org/software/libc/manual/](http://www.gnu.org/software/libc/manual/)

You can also access the glibc-manual from the console by typing info libc  (or from emacs too!)

Here:
[http://www.gnu.org/software/libc/manual/html_node/Formatted-Output-Functions.html#Formatted-Output-Functions](http://www.gnu.org/software/libc/manual/html_node/Formatted-Output-Functions.html#Formatted-Output-Functions)

then if you type man sprintf you get more details

---

### Post by rock freak on 2006-02-01
hey there if you need a nice C tht is a C reference libary not C++ or C# 

I use this link and my c book

[http://www.acm.uiuc.edu/webmonkeys/book/c_guide/](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/)

---

