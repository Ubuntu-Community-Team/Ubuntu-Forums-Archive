---
title: "c fgets function"
date: 2010-05-08
forum: Programming Talk
---

### Post by kartabosh on 2010-05-08
i used gets ever since i started learning programming which was not so long ago :lolflag:
but some people here suggested i used fgets and i realized that fgets adds \n\0 to whatever you write, the \0 is fine but whats with the \n? i remember ruby had a method something like gets.chomp if i remember right that removed the new line character automatically 
so is there such a thing here or is this the fastest way
[php]
    fgets(buffer, 1024, stdin);
    buffer[strlen(buffer)-1]=buffer[strlen(buffer)];
[/php]

---

### Post by nvteighen on 2010-05-08
> **kartabosh said:**
> i used gets ever since i started learning programming which was not so long ago :lolflag:
but some people here suggested i used fgets and i realized that fgets adds \n\0 to whatever you write, the \0 is fine but whats with the \n? i remember ruby had a method something like gets.chomp if i remember right that removed the new line character automatically 
so is there such a thing here or is this the fastest way
[php]
    fgets(buffer, 1024, stdin);
    buffer[strlen(buffer)-1]=buffer[strlen(buffer)];
[/php]

No, fgets doesn't add '\n'. The '\n' is added because you actually type in the enter key when entering something into stdin.

---

### Post by trent.josephsen on 2010-05-08
> **kartabosh said:**
> i used gets ever since i started learning programming which was not so long ago :lolflag:
but some people here suggested i used fgets and i realized that fgets adds \n\0 to whatever you write, the \0 is fine but whats with the \n? i remember ruby had a method something like gets.chomp if i remember right that removed the new line character automatically 
so is there such a thing here or is this the fastest way
[php]
    fgets(buffer, 1024, stdin);
    buffer[strlen(buffer)-1]=buffer[strlen(buffer)];
[/php]

fgets does not "add" a newline.  gets is unusual in that it explicitly removes the newline.  The newline is useful in that it allows you to determine (by examining the last character before the '\0') whether fgets stopped reading input because it reached the end of a line, or because it ran out of space in the buffer.

Your suggested solution will be very slow because each time you call strlen it has to traverse the entire array.  You can write a chomp function something like this (untested):
```
char *chomp(char *s)
{
    if (*s) {
        while (*++s);
        s[-1] = '\0';
    }
    return s;
}
```

(The if statement is necessary to make sure we don't write before the start of an empty string.)

Better is not to worry about the trailing newline at all.  Use strtok to pick apart the result of fgets, or roll your own with getchar and friends.  Don't use gets; there are plenty of other, more subtle ways to shoot yourself in the foot, and don't use scanf unless your input is actually formatted (e.g. CSV data or the output of ls -l).

---

### Post by kartabosh on 2010-05-08
well the thing is that now i have to use
strcmp(x,"something\n") because of that new line
it also gets in the way if i use a switch function unless i use a special case '\n':break;

---

### Post by kartabosh on 2010-05-08
also i see that it doesnt really work when it a loop 
[php]
while (1){
printf("> ");
    fgets(buffer, 1024, stdin);
    if (strcmp(buffer,"exit\n")== 0) break;
[/php]
it only reads it once...

---

### Post by Compyx on 2010-05-08
> **trent.josephsen said:**
> You can write a chomp function something like this (untested):
```
char *chomp(char *s)
{
    if (*s) {
        while (*++s);
        s[-1] = '\0';
    }
    return s;
}
```


That will remove any last character from a string, not just newlines. :)

This will remove a newline if it's the last character in the string (also untested):
```

char *chomp(char *s)
{
    if (s != NULL && *s ='\0') {
        size_t n = strlen(s);
        if (s[n - 1] == '\n') s[n - 1] = '\0;
    }
    return s;
}

```

---

### Post by kartabosh on 2010-05-08
thanks 
this is my output, very strange ...
[php]
> a+b-c
a b + c - 
a=2
b=4
c=5
1
> 
0
>[/php]

---

### Post by kartabosh on 2010-05-08
can someone please debug my code?
[php]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
typedef struct{
    char tip;
    short pri;
} semnbag;
typedef struct{
    char tip;
    int valoare;
} gigipai;
char buffer[1024],final[1024],x[1024],jupiter[1024];
int number,intel,pamela,fixel,pb,pri,igor,gicu,i,true=2,k[99],is,is2,w,si,temp1,temp2,dubios,nc,zero,neo;
int main(){
gigipai num[99];
semnbag semn[30];
while (1){
number=intel=pamela=fixel=pb=pri=igor=gicu=i=is=is2=w=si=temp1=temp2=dubios=nc=zero=neo=0;
final[0]='\0';
jupiter[0]='\0';
buffer[0]='\0';
x[0]='\0';
printf("> ");
printf("\naici\n");
    fgets(buffer, 1024, stdin);
    if (strcmp(buffer,"exit\n")== 0) break;
    buffer[strlen(buffer)-1]=buffer[strlen(buffer)];
    gicu=strlen(buffer)+1;
    for (intel=0;intel<gicu;++intel){
        switch(buffer[intel]){
            case '(':++pb;break;
            case ')':--pb;break;
            case 'a'...'z':
                final[fixel++]=buffer[intel];
                final[fixel++]=' ';
                break;
            case '+':
            case '-':
            case '*':
            case '/':
            case '\0':
                if (buffer[intel]=='+' || buffer[intel]=='-') pri=pb*10+1;
                else if (buffer[intel]=='\0') pri=-9999;
        else pri=pb*10+2;
                if  (igor>0){
                    while (pri<=semn[igor-1].pri){
                        final[fixel++]=semn[igor-1].tip;
                        final[fixel++]=' ';
                        semn[igor-1].tip='\0';
                        semn[igor-1].pri=0;
                        --igor;
                    }
                    semn[igor].tip=buffer[intel];
                    semn[igor++].pri=pri;
                }
                else{
                    semn[igor].tip=buffer[intel];
                    semn[igor++].pri=pri;
                }
            break;
            default:++pamela;break;
        }
    }
if (pamela) printf("eroare: caracter ilegal\n");
else{
if (igor > 0)
final[fixel] = semn[igor-1].tip;
printf("%s\n",final);
strcpy(x,final);
is=strlen(x);
        for (i=0;i<is;++i){
                switch(x[i]){
                    case 'a'...'z': num[nc].tip=x[i];
                            printf("%c=",num[nc].tip);
                            scanf("%d",&number);
                            num[nc++].valoare=number;
                            break;   
                    case  '+':   
                                    if(nc>1){
                                        num[nc-2].valoare=num[nc-2].valoare+num[nc-1].valoare;
                                        num[nc-1].valoare=num[nc].valoare;
                                       
                                        --nc;
                                    }
                                    //else ++neo;
                               
                    case  '-':   
                                    if(nc>1){
                                        num[nc-2].valoare=num[nc-2].valoare-num[nc-1].valoare;
                                        num[nc-1].valoare=num[nc].valoare;
                                        --nc;
                                    }
                                    //else ++neo;
                           
                    case  '/':   
                                    if(nc>1){
                                        if (num[nc-1].valoare!=0){
                                            num[nc-2].valoare=num[nc-2].valoare/num[nc-1].valoare;
                                            num[nc-1].valoare=num[nc].valoare;
                                            --nc;
                                        }
                                        else ++zero;
                                    } 
                                    //else ++neo;
                               
                    case  '*':   
                                    if(nc>1){
                                        num[nc-2].valoare=num[nc-2].valoare*num[nc-1].valoare;
                                        num[nc-1].valoare=num[nc].valoare;
                                        --nc;
                                    }
                                    //else ++neo;
                    case ' ':break;
                    default: ++dubios;break;
                   
                }
            }
//}
/*    if (dubios==0){
        if (zero!=0) printf("Divided by Zero\n");
        else if (neo>0) printf("Not enough operands\n");
        else if (neo==0 &&nc>1) printf("Too many operands\n");
        else if (nc==0);
        else {
            temp1=num[nc-1].valoare;
            if (temp1==num[nc-1].valoare)printf("%.0f\n",num[nc-1].valoare);
            else printf("%.10f\n",num[nc-1].valoare);
        }
        }
     else printf("Unrecognized token\n");
*/
printf("%d\n",num[nc-1].valoare);
}
}
return 0;
} 

[/php]

---

### Post by MadCow108 on 2010-05-08
better learn to debug it yourself.

a good tool to do that are, obviously, debuggers.
With these you can set your code line by line and see where it goes wrong.

gdb and the gui frontend ddd are good choices.

for memory related problems valgrind can quickly give the location of the problem.

---

### Post by kartabosh on 2010-05-08
> **MadCow108 said:**
> better learn to debug it yourself.

a good tool to do that are, obviously, debuggers.
With these you can set your code line by line and see where it goes wrong.

gdb and the gui frontend ddd are good choices.

for memory related problems valgrind can quickly give the location of the problem.
i did try to debug it but i found nothing 
it just passed the fgets line without asking for anything in the console

---

### Post by kartabosh on 2010-05-09
for some reason the second time it gets to fgets the buffer has \n in it probably from the last read where i pressed enter
anyway i solved that by adding a fgets at the end of the program that will empty the buffer

---

### Post by dwhitney67 on 2010-05-09
The following code works fine for me; perhaps you could use it too?
```

#include <stdio.h>
#include <string.h>

int main()
{
   char buffer[1024] = {0};

   while (1)
   {
      printf("Enter a word: ");

      fgets(buffer, sizeof(buffer), stdin);

      char* nl = strchr(buffer, '\n');
      if (nl) *nl = '\0';

      if (strcmp(buffer, "exit") == 0) break;

      printf("buffer contains: %s\n", buffer);

      // ...
   }

   return 0;
}

```

Btw, you should get into the habit for formatting your code with a little more newlines.  It is hard to read code that is "crushed" together such as the one you posted earlier.  Using proper indentation is also a bonus.

---

### Post by trent.josephsen on 2010-05-09
> **Compyx said:**
> That will remove any last character from a string, not just newlines. :)
Thanks for catching that.

@OP:  Indentation rules, perhaps?  This is the output of "indent -kr":
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
typedef struct {
    char tip;
    short pri;
} semnbag;
typedef struct {
    char tip;
    int valoare;
} gigipai;
char buffer[1024], final[1024], x[1024], jupiter[1024];
int number, intel, pamela, fixel, pb, pri, igor, gicu, i, true =
    2, k[99], is, is2, w, si, temp1, temp2, dubios, nc, zero, neo;
int main()
{
    gigipai num[99];
    semnbag semn[30];
    while (1) {
        number = intel = pamela = fixel = pb = pri = igor = gicu = i = is =
            is2 = w = si = temp1 = temp2 = dubios = nc = zero = neo = 0;
        final[0] = '\0';
        jupiter[0] = '\0';
        buffer[0] = '\0';
        x[0] = '\0';
        printf("> ");
        printf("\naici\n");
        fgets(buffer, 1024, stdin);
        if (strcmp(buffer, "exit\n") == 0)
            break;
        buffer[strlen(buffer) - 1] = buffer[strlen(buffer)];
        gicu = strlen(buffer) + 1;
        for (intel = 0; intel < gicu; ++intel) {
            switch (buffer[intel]) {
            case '(':
                ++pb;
                break;
            case ')':
                --pb;
                break;
            case 'a'...'z':
                final[fixel++] = buffer[intel];
                final[fixel++] = ' ';
                break;
            case '+':
            case '-':
            case '*':
            case '/':
            case '\0':
                if (buffer[intel] == '+' || buffer[intel] == '-')
                    pri = pb * 10 + 1;
                else if (buffer[intel] == '\0')
                    pri = -9999;
                else
                    pri = pb * 10 + 2;
                if (igor > 0) {
                    while (pri <= semn[igor - 1].pri) {
                        final[fixel++] = semn[igor - 1].tip;
                        final[fixel++] = ' ';
                        semn[igor - 1].tip = '\0';
                        semn[igor - 1].pri = 0;
                        --igor;
                    }
                    semn[igor].tip = buffer[intel];
                    semn[igor++].pri = pri;
                } else {
                    semn[igor].tip = buffer[intel];
                    semn[igor++].pri = pri;
                }
                break;
            default:
                ++pamela;
                break;
            }
        }
        if (pamela)
            printf("eroare: caracter ilegal\n");
        else {
            if (igor > 0)
                final[fixel] = semn[igor - 1].tip;
            printf("%s\n", final);
            strcpy(x, final);
            is = strlen(x);
            for (i = 0; i < is; ++i) {
                switch (x[i]) {
                case 'a'...'z':
                    num[nc].tip = x[i];
                    printf("%c=", num[nc].tip);
                    scanf("%d", &number);
                    num[nc++].valoare = number;
                    break;
                case '+':
                    if (nc > 1) {
                        num[nc - 2].valoare =
                            num[nc - 2].valoare + num[nc - 1].valoare;
                        num[nc - 1].valoare = num[nc].valoare;

                        --nc;
                    }
                    //else ++neo;

                case '-':
                    if (nc > 1) {
                        num[nc - 2].valoare =
                            num[nc - 2].valoare - num[nc - 1].valoare;
                        num[nc - 1].valoare = num[nc].valoare;
                        --nc;
                    }
                    //else ++neo;

                case '/':
                    if (nc > 1) {
                        if (num[nc - 1].valoare != 0) {
                            num[nc - 2].valoare =
                                num[nc - 2].valoare / num[nc - 1].valoare;
                            num[nc - 1].valoare = num[nc].valoare;
                            --nc;
                        } else
                            ++zero;
                    }
                    //else ++neo;

                case '*':
                    if (nc > 1) {
                        num[nc - 2].valoare =
                            num[nc - 2].valoare * num[nc - 1].valoare;
                        num[nc - 1].valoare = num[nc].valoare;
                        --nc;
                    }
                    //else ++neo;
                case ' ':
                    break;
                default:
                    ++dubios;
                    break;

                }
            }
//}
/*    if (dubios==0){
        if (zero!=0) printf("Divided by Zero\n");
        else if (neo>0) printf("Not enough operands\n");
        else if (neo==0 &&nc>1) printf("Too many operands\n");
        else if (nc==0);
        else {
            temp1=num[nc-1].valoare;
            if (temp1==num[nc-1].valoare)printf("%.0f\n",num[nc-1].valoare);
            else printf("%.10f\n",num[nc-1].valoare);
        }
        }
     else printf("Unrecognized token\n");
*/
            printf("%d\n", num[nc - 1].valoare);
        }
    }
    return 0;
}
```

Frankly, I'm still having a hard time understanding what it's supposed to do.  Do most of your identifiers actually mean something in some other language than English (Google Translate suggests Romanian), or are they mostly arbitrary?  Some of them (buffer, true, temp1 and temp2, for instance) seem to be reasonably named, but what about intel, pamela, x, num, and jupiter (this last of which I notice you don't even use)?

Consider breaking down the program into functions.  140 lines is a lot for main() and initializing 19 variables to 0 all at once is a good indication that they have greater scope than necessary (although I believe they're all initialized to 0 anyway because they have file scope -- someone correct me if I'm wrong).

I mean no offense.  Did you write this yourself?

---

### Post by kartabosh on 2010-05-09
yes, i'm a new programmer, just started few months ago
the language is indeed romanian
and i reset the variables because pamela and others are needed later on in the code, i know the code is horrible but doesnt trial and error apply in programming too?
and yes, i did write the code myself
i cant really break the code into functions because i dont know how to make an external function use a string, i think its something like blabla(char *) but i'm not good with pointers so i just keep everything in one main, pretty noobish right?
what's indent -kr ?

---

### Post by Bachstelze on 2010-05-09
> **kartabosh said:**
> 
what's indent -kr ?

[font=monospace]indent[/font] is a tool that automatically indents a piece of code according to a set of rules. The [font=monospace]-kr[/font] switch tells it to indent code using the so-called "K&R" coding style, used by Brian Kernighan and Dennis Ritchie in their book *The C Programming Language* (generally referred to as "The K&R book", or just "K&R").

---

### Post by soltanis on 2010-05-09
Here's how you make an external function use a string:

```

void chomp(char *str)
{
        int len = strlen(str);

        if (str[len - 1] == '\n') {
                str[len - 1] = '\0';
        }
}

```

Explanation:
strlen determines the length of the string, not including the terminating null. This means that str[len] would be where the null character is (because C arrays are zero indexed), and str[len - 1] is the character right before the end. This function checks if the last character is a newline, and if it is, it overwrites it with a null character, effectively chopping the terminating newline.

To invoke this function, pass an array of char to it. By virtue of the fact that you are using pointers, which you will come to understand later, this function will modify the string you give it.

```

/* in a function */
char string[1024];

fgets(string, sizeof(str), stdin);
chomp(string);

```

---

### Post by kartabosh on 2010-05-10
but no return line?
 i mean if i want to make a function that copies all the characters from one string into another in a specific order how will the function know? oh wait
i think i got it 
something(char *str1,char*str2){
//copy str1 to str2 in a certain order just as if it were a local string
}
no return no nothing and str2 will contain in main what i wanted?

---

### Post by lisati on 2010-05-10
> **kartabosh said:**
> but no return line?
 i mean if i want to make a function that copies all the characters from one string into another in a specific order how will the function know? oh wait
i think i got it 
something(char *str1,char*str2){
//copy str1 to str2 in a certain order just as if it were a local string
}
no return no nothing and str2 will contain in main what i wanted?

Some programming languages and some dialects of C that I've seen (bad pun not intended) let you do this. However, there will generally be an implied return. In my opinion, good programming style demands that you put a return in where appropriate, even if the compiler is smart enough to provide one for you when needed.

For copying strings, you might want to look into strcpy and strncpy.

---

### Post by soltanis on 2010-05-10
In functions which do not return values (void functions) the return is implied when the function reaches the end }. Depending on your opinion, having an explicit return may be good or bad style; either way the compiler will not care.

The reason my chomp function has no return value is because it modifies the string you give it in memory. Therefore, there is no particular reason for it to have a return value, unless for example you wanted to streamline its usage in a nested function call:

```

if (strncmp(chomp(string), "string") == 0) { ... }

```

In the case above you should redefine the function like this:

```

char *chomp(char *string)
{
        /* code as before */
        return string;
}

```

But otherwise it's all the same.

And by the way, many library functions like strncpy behave like this; they store their return value in one of the arguments you pass them as well as return it in the function call.

If you want to know more about the magic behind how you can modify the string in place, and why doing something like this:

```

chomp("This is a constant string, which you cannot chomp\n");

```

Will result (more likely than not) an error, that's pointers.

---

### Post by kartabosh on 2010-05-10
my function cannot be broken into small bits because both part 1 and 2 of it work with structures so it will be a function that cannot actually be used for other purposes therefor why create a function for it

---

### Post by soltanis on 2010-05-10
Whatchu talkin bout?

That is no reason to not create a function. I doubt you'll be reusing any of this code in a year in any case; the reason for writing functions is to make your code modular so that when something doesn't work out and you end up rewriting it, you're rewriting at the most a few functions as opposed to random bits and pieces of your big, ugly program.

Also, if you use functions, you never know; I still use some functions I wrote 2 years ago for setting up TCP connections because when I get down to it, 90% of my connection code is the same boilerplate anyway.

As functions can both take structures as arguments and return them as values, I see no good reason not to forge ahead with writing functions.

---

