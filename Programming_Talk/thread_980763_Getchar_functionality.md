---
title: "Getchar functionality"
date: 2008-11-13
forum: Programming Talk
---

### Post by pardeepluna on 2008-11-13
Hi all, 

please direct me if in case i have posted in wrong thread .. 

i am working with C on linux and i am facing small problem in the code .. Here it is.. 

int function(char *ptr, int MAX_LENGTH)
{
     char ptr_array[MAX_LENGTH];
for(i =0;((i<MAX_LENGTH)&& (ptr_array[i]=getchar())!='\n');i++)
                                ;
         if(i <= MAX_LENGTH+1)
                 {
                         ptr_array[i] ='\0';
                         ptr = ptr_array;
                         return 1;

                 }
         else
                 {
                       printf("This line won't get stored since its length is more");
                        return 0;
                 }
}

Here i am facing problem with the getchar() functionality .. Even after i am typing more than MAX_LENGTH (100) characters .. I am not getting out of for loop.It seems as if getchar is holding the string in the buffer Please clear me how can i use getchar here

---

### Post by Tony Flury on 2008-11-13
Under the C standard library (getchat etc), input is buffered per line.

You can change this behaviour (i think) by using things like the stty settings on the terminal.

I have asked this thread to be moved to the Programming Talk forum, where people more expert than me are able to assit.

---

### Post by dmizer on 2008-11-13
Moved to Programming talk.

---

### Post by pardeepluna on 2008-11-13
#include<stdio.h>
      2
      3 int main()
      4 {
      5         int i=0;
      6         char *str, str_second[10];
      7         str = "I am good boy";
      8         for(i=0;i<10;i++)
      9         {
     10                 if((str_second[i]= getchar())!='\n')
     11                         ;
     12         }
     13         printf(str_second);
     14         printf(str);
     15
     16         return 0;
     17 }


Here is another example .. the problem is .. getchar() is storing all the entered charaters in the buffer and once i am pressing enter or '\n' character .. Its executing the loop without further checking the condition in the for loop.

if i am placing printf() in the loop the getchar functionality is getting executed once and after that the loop is executing printf() only without further checking the getchar() condition.

Please let me know the solution for this.I am working on linux

---

### Post by Tony Flury on 2008-11-13
I am not sure what you are refering to when you talk about your printf, but as I said before - input is line buffered, so getchar will only read characters of a completed line - you can't use getchar to detect characters as they are typed.

Note : it would help when you post code in these forums that you use the CODE tags (click the # button) in order to maintain the idententation and other formatting.

You code will appear like this when you post it

```

#include<stdio.h>

int main()
{
    int i=0;
    char *str, str_second[10];
    str = "I am good boy";

    for(i=0;i<10;i++)
    {
        if((str_second[i]= getchar())!='\n')
        ;
    }

    printf(str_second);
    printf(str);
    return 0;
}

```

Your if ststement wont do anything, even if you do get a newline it just ignores it and the loop will continue - did you mean the loop to stop at that point ?

if you want your loop to stop - then this code should do that, however it will still need you to press return.

```

#include<stdio.h>

int main()
{
    int i=0;
    char *str, str_second[11];
    str = "I am good boy";

    for(i=0;i<10;i++)
    { 
        str_second[i] = getchar() ; 

        if(str_second[i]=='\n')
            break ;
    }

    str_second[i+1] = '\0' ; 

    printf(str_second);
    printf(str);
    return 0;
}

```
the changes i have made 
1) I have declared your string as char[11] (not 10) so that it can be made to include the '\0' (NULL terminating character).
2) I have seperated the call to getchar from your if statement - yes it means another line of code, but i think it makes it clearer.
3) used the break statement to come out of the loop if you get a '\n'
4) Made sure that when the loop exits it includes a '\0' to the end of the inputted string.

---

### Post by nvteighen on 2008-11-13
What you want, I'd I understand, is to give the user a limited prompt so he/she can't write more than MAX_LENGTH, right?

I'm almost sure there's no way to do this using the Standard Library because of how stdout/stdin work. Maybe some ncurses trick may be useful?

---

### Post by pardeepluna on 2008-11-14
Thanks Tony and others ... Next time i post any query i will try to make it more clean and understandable ..... 

Since as you said .. getchar() can't be used to get one character at a time and it read line buffer .Can you please suggest me what shall i used to read one character at a time so that i can terminate my loop as soon as i exceed the limit of counter.

---

### Post by pardeepluna on 2008-11-14
If getchar() can't be used to get one character at a time and it read line buffer .Can you please suggest me what shall i used to read one character at a time so that i can terminate my loop as soon as i exceed the limit of counter.

---

### Post by Tony Flury on 2008-11-14
I think you would have to look at nucrses - and use some of the routines there to do what you want - not for the faint hearted.

I think I would be tempted to ask yourself why you are doing this ?

---

### Post by pardeepluna on 2008-11-14
Hi Tony . 

Thanks for your reply .. Actually i have seen getchar() used in the books  the way i have used above. so i was wondering why it was not happening with me. 

anyways as i have got to know that the problem was becoz of buffer. I am not getting  what you mean by < nucrses >. I would be thankfull if you can provide me some links.

-Luna

---

### Post by Tony Flury on 2008-11-14
ncurses is a library that allows very detailed control of terminal type output - a quick google search : 

[http://www.google.co.uk/search?hl=en&q=ncurses+library+from+C&meta=](http://www.google.co.uk/search?hl=en&q=ncurses+library+from+C&meta=)

the top two links :

[http://invisible-island.net/ncurses/ncurses-intro.html](http://invisible-island.net/ncurses/ncurses-intro.html)

[http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Curses.pdf](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Curses.pdf) 


BTW : I do think that getchar has even worked like that on Unix based systems - it might do that on WIndows (but I have never programmed with C on MS Windows).

---

### Post by dwhitney67 on 2008-11-14
Here's a guide to Ncurses:  [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)

I've joined this thread late, and I apologize if the following question has been answered already...  Why are you trying to read one character at a time?  Are you writing a key-stroke logger?  If all you need to do is read an input string of length-N, then I suggest you use fgets().

---

### Post by Tony Flury on 2008-11-14
i think even fgets is line-buffered when reading from stdin - and probably all other files as well - so i don't think fgets would work either for what the OP asked for.

---

### Post by dwhitney67 on 2008-11-14
> **Tony Flury said:**
> i think even fgets is line-buffered when reading from stdin - and probably all other files as well - so i don't think fgets would work either for what the OP asked for.
It is indeed line buffered.  I was wondering why the OP wanted to read one character at a time.  I see many times that newbies attempt to read one character at a time from a file, when it would be easier (and faster) to read the data in larger blocks.

Anyhow, I would like to hear from the OP as to why he needs to read one character at a time.  Has this been answered already?

---

### Post by lisati on 2008-11-14
Suggestion:

getch() or getche()

(or have I been over-influenced by Turbo-C?)

---

### Post by Tony Flury on 2008-11-14
dwhitney67 : The OP has not explained why the application needs to read one character at a time 

lisati : getch & getche are not Unix/Posix standard functions - from what i can tell they are MS or Turbo-C specials.

---

### Post by pardeepluna on 2008-11-14
Hi All, 

I want to read a line in a way where i want to notify user as soon as they exceed the limit and for that i need to take his input char by char and check for the limit.

The moment i press some char on the keyboard i want that char to be recognized without pressing enter key. Please let me know whether its possible or not. If yes please provide me the solution

-Luna

---

### Post by Tony Flury on 2008-11-15
We have already tried to provide you with a solution in that you will have to use the ncurses library to do what you want.

the people in this forum will help you to help yourself (i.e. pointing you in the right direction) but you wont learn anything if someone just drops you a complete working solution. It is far better for you to try to solve it given the direction and hints we provide, and then come back for further specific help if you get stuck.

we are however interested is to why you want to do what you are trying to do - can you give us an explanation as to why you want your programm to do this ?

---

### Post by Zugzwang on 2008-11-16
Tony, I don't want to spoil your line of reasoning, but I just wanted to point out that apart from using ncurses, there's also the possibility to use some user-made getch() function instead. In fact, there's one at:

[http://forum.de.selfhtml.org/archiv/2006/10/t138258/]("http://forum.de.selfhtml.org/archiv/2006/10/t138258/")

**Warning**! The actual function is surrounded by german text. On that page it starts with "// Nachimplementierung der getch()-Funktion aus DOS-conio.h" and where it ends should be obvious. Note that the author seems to have declared it as being public domain. I tried it once and the implementation worked fine.

---

