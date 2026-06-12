---
title: "can this  be read easy enough."
date: 2008-08-24
forum: Programming Talk
---

### Post by cmay on 2008-08-24
hi.
i just wanna ask if this is ok to read for others.
i have trouble whit my eyes so i can have hard time to
adjust the demands of others in terms of readability of my code fragments
also i have seen others use some highlighted text. how does one do that.
thanks for your time
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc,char **argv)
{   
	char name[100];
	printf("please enter your first and last name\n");
	fgets(name,sizeof(name),stdin);
	
	if(strcmp("bill gates\n",name - '\0') == 0 )
	{
	   puts("OHH MY GOD !!! are you using linux now\?");
        }
    
        if(strcmp("rambo\n",name -'\0') == 0 )
       {
         printf("sure you are  \"%s\"\n",getenv("USERNAME"));
       }
	
	else
	{
	printf("your name is %s\n",name);
	printf("your $USERNAME is %s\n",getenv("USERNAME"));
	printf("your $LOGNAME  is %s\n",getenv("LOGNAME"));
	printf("your $HOME  directory is %s\n",getenv("HOME")); 
        }
    
	puts("goodbye");  

        return 0;
 }

```

---

### Post by Reiger on 2008-08-24
Readable for sure. I guess what you meant with highlighted code is that people put their code inside the [PHP]PHP-code tags[/PHP]. Found under the little icon of a 'file' with PHP written over it, next to the code & html-code tags.

---

### Post by cmay on 2008-08-24
thanks i never seen that, i might as well get used to using it.
thanks for your time.
[PHP]test
test
test[/PHP]

---

### Post by monkeyking on 2008-08-24
[PHP]
int main(){return 0}
[/PHP]

Ahh that's nice

---

### Post by mssever on 2008-08-24
> **cmay said:**
> hi.
i just wanna ask if this is ok to read for others.
i have trouble whit my eyes so i can have hard time to
adjust the demands of others in terms of readability of my code fragments
I guess you'd have a hard time with Python, then. :) Your alignment is off by a space or two in a couple places, but nothing serious.

---

### Post by jinksys on 2008-08-24
> **cmay said:**
> hi.
i just wanna ask if this is ok to read for others.

Your code is clean and readable, however I do see potential SEGFAULTs.

---

### Post by NovaAesa on 2008-08-25
> **mssever said:**
> Your alignment is off by a space or two in a couple places,Agreed.


[quote=mssever] but nothing serious.[/QUOTE]
Disagreed.

The indenting is very inconsistent. For your first if statement, the { and } don't line up. You have indented by 3 spaces. Your next if statement is indented by one space compared to the rest in the main block. You then go back a space to put you { and }. Then what is in the block is only indented by 2 this time. On your else part, you have the { and } not lining up again. And also, there is no indentation at all for this block. And finally your return statement is one two many spaces in.



Now I understand that the OP has bad eyesight. The best solution to increasing readability would be to use and editor that converts the tab key to your choice of a number of spaces. And then don't press the space bar at all for indentation. Aso, you might want to bump up the font size on your editor, that way you would reduce the strain on your eye (I think this would help anyway :P)

Sorry if that was a bit harsh, but you did ask if it was okay for other readers :)

---

### Post by dribeas on 2008-08-25
> **NovaAesa said:**
> ... then don't press the space bar at all for indentation.

I agree in that you should only use TABs as indentation. Whether you use an editor that translates to spaces or not depends on what software you want to use to enhance your readability --yours, not other peoples. If at some point you use screen readers then 'tab, tab' is more readable for two levels of indentation than a sequence of 2 * sizeof(tab) 'space'.

@NovaAesa: I agree in that for most people, translating tabs into spaces helps as spaces are always seen exactly the same, while tabs can be configured to just about any size. On the other hand, tabs explicit the indentation level meaning better than spaces.

@all: I seems funny that the one person that has trouble reading is the one concerned on how the rest of us read his posts. Just think about it. I will.

   David

**UPDATE**: I've found tabinta firefox extension, which configured with Alt-I as the combination to enter tabs allows for tab insertion into multiline text areas. I'll try to remember to use it myself.

---

### Post by nvteighen on 2008-08-25
@OP: What text editor do you use?

---

### Post by cmay on 2008-08-25
> 
@OP: What text editor do you use? 

i use geany the most. and i use nano also.
i am glad that you all can read my code.
i have changed coding style since i seen many
use this a style  so i will try adapt it instead of 

[PHP]#include <stdio.h>
int main(int argc, char *argv[]){
        printf("i read too much k&r lately :)\n");
        return 0;
}[/PHP]

thanks for your time.

---

### Post by nvteighen on 2008-08-25
> **cmay said:**
> i use geany the most. and i use nano also.
i am glad that you all can read my code.
i have changed coding style since i seen many
use this a style  so i will try adapt it instead of 

[PHP]#include <stdio.h>
int main(int argc, char *argv[]){
        printf("i read too much k&r lately :)\n");
        return 0;
}[/PHP]

thanks for your time.

Geany should support basic indentation tools to help you not having to type spaces one by one and making <tab> insert spaces instead of tabs. Gedit supports that.

nano is very basic. I really don't code there and just use it for trivial text editing, for which is perfect.

What you need, with no doubt, is a text editor that allows you to customize it for your needs. In your position I'd sacrifice features like embedded terminal and things like that to the overmost important: that you be able to code without difficulties.

---

### Post by cmay on 2008-08-25
> nano is very basic. I really don't code there and just use it for trivial text editing, for which is perfect.
can i ask what editor you use ?. i have tried to use others like anjuta and
emacs and kdevelop but i like geany the most since the embedded terminal saves me time i just have to click compile and run .
its not so important yet since i am only learning but i sometimes paste code in these forums so i just want to make sure that its readable.:)

---

### Post by nvteighen on 2008-08-25
> **cmay said:**
> can i ask what editor you use ?. i have tried to use others like anjuta and
emacs and kdevelop but i like geany the most since the embedded terminal saves me time i just have to click compile and run .
its not so important yet since i am only learning but i sometimes paste code in these forums so i just want to make sure that its readable.:)
Sure. I use emacs; I love it, though I admit it's hard to use (and I'm not an expert on it): you do have embedded terminal and direct access to compiler and such things, but you'll have to customize it to get it the way you want.

But Gedit is also good and has those features. Have you looked at its plugins? Much of the best is disabled by default...

---

### Post by cmay on 2008-08-25
oh emacs is hard but its a fun editor as well.
i think i stick whit geany since i am getting used to it.
i will want a better one for larger project if i get so far. :)

---

