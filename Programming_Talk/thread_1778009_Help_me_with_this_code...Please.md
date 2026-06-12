---
title: "Help me with this code...Please"
date: 2011-06-08
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-06-08
Hi everybody i hope U are enjoying your day i have quite a newbie problem.

I'm trying to get a comparison between two char type variables here is my code:

```


int main()
{

const char ID[10] = "text";

char ID2[10];

cin >> ID2;

if (ID2 == ID) cout << "Yay!"; 
else cout << "Nooo!";

cin.get();
return 0;
}


```


But the result of this just gives me a "Nooo!", 
When I type "text"

(I type without comas btw.)

How to fix this to get a "Yay!" when typing "text" instead of "Nooo!" :guitar:

---

### Post by jwcalla on 2011-06-08
My C is rusty but the first thing that comes to mind is that you might be comparing the pointer values rather than the actual text.  I would feel more comfortable using one of the strcmp() methods for string comparisons.

I think in C++ the std::string object allows comparisons using "==".

---

### Post by Mr. Shannon on 2011-06-08
> ...the first thing that comes to mind is that you might be comparing the pointer values rather than the actual text. I would feel more comfortable using one of the strcmp() methods for string comparisons.

I just looked it up [[COLOR="Blue"]here[/COLOR]]("http://www.codeguru.com/forum/showthread.php?t=231162"), that seems to be what happens.  For instruction on using **strcmp** see the URL below.

[http://www.cplusplus.com/reference/clibrary/cstring/strcmp/]("http://www.cplusplus.com/reference/clibrary/cstring/strcmp/")

---

### Post by ThatCoolGuy220 on 2011-06-08
ill try brb....

---

### Post by ThatCoolGuy220 on 2011-06-08
Thank you everybody:

```

int main()
{

std::string ID = "text" , ID2;



cin >> ID2;

if (ID2 == ID)  cout << "Yay!"; 
else cout << "Nooo!";

cin.get();
return 0;
}


```

WORKED like a charm!.


I must add yes it was very weird, cause As a beginner I though on natural syntax.:popcorn:


strcmp has interesting uses.... hmmm

strcmp Version:

```

int main ()
{
char ID[] = "text";
char ID2[10];

do{
cin >> ID2;
}

while (strcmp (ID, ID2) != 0);
cout <<"Yay!";




cin.get();
return 0;
}

```


LOL I havent found a way to include an else there but if wouldnt be that hard...

---

### Post by Petrolea on 2011-06-08
> **ThatCoolGuy220 said:**
> Thank you everybody:

```

int main()
{

std::string ID = "text" , ID2;



cin >> ID2;

if (ID2 == ID)  cout << "Yay!"; 
else cout << "Nooo!";

cin.get();
return 0;
}


```

WORKED like a charm!.


I must add yes it was very weird, cause As a beginner I though on natural syntax.:popcorn:


strcmp has interesting uses.... hmmm

strcmp Version:

```

int main ()
{
char ID[] = "text";
char ID2[10];

do{
cin >> ID2;
}

while (strcmp (ID, ID2) != 0);
cout <<"Yay!";




cin.get();
return 0;
}

```


LOL I havent found a way to include an else there but if wouldnt be that hard...

What do you want to do with the 'else'?

---

### Post by ThatCoolGuy220 on 2011-06-08
add the "Nooo!"

if ID its not equal to ID2.

Im researching this but if you can Guide me I would be glad

---

### Post by ThatCoolGuy220 on 2011-06-08
Got it!

But its without the do, and while.

```

int main ()
{
char ID[] = "text";
char ID2[10];

cin >> ID2;

if (!strcmp(ID, ID2)){
	cout << "Yay!";
}
else
cout << "Nooo!";


cin.get();
return 0;
}



```

---

### Post by Petrolea on 2011-06-08
> **ThatCoolGuy220 said:**
> Got it!

But its without the do, and while.

```

int main ()
{
char ID[] = "text";
char ID2[10];

cin >> ID2;

if (!strcmp(ID, ID2)){
	cout << "Yay!";
}
else
cout << "Nooo!";


cin.get();
return 0;
}



```

That's correct, but you abandoned some functionality. You took the do-while loop out, so now it only repeats once. You can make a loop with ifs and just exit the loop on some word like "exit".

I won't write the whole program for you, but pseudocode might help:

```

while(1) //all the way to infinity
{
    read some input;

    if (the words are equal)
    {
        print "Yay!";
    } 
    else 
    {
        print "Nooooooooooooooooooooooooooooooooooooooo!";
    }

    if (word equals "exit")
    {
         break;
    }
}

```

You might also want to break the loop at some point (see the code). You can use "break;" for that. Google for more info. But don't ever use goto to break the loop, it just doesn't look nice and more gotos will make a mess.

---

### Post by ThatCoolGuy220 on 2011-06-10
Thanks bro.

Saved as reference....

And here is the Code well as usual it took me a while to catch it on but I finally understood it:

```


#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <string>

using namespace std;
int main()
{

string ID = "text", ID2, Exit = "exit";

while(1)
    {
     
    cin >> ID2;

    if (ID == ID2)
    {
    
    cout << "Yay! ";
    
    }


    else 
    
    {
	
    cout << "Nooooooooooooooooooooooooo! ";
    
    }	


    if (ID2 == Exit)
    {
     
    break;
    
    }

    }
		
cin.get();
return 0;

} ///:~



```

---

### Post by simeon87 on 2011-06-10
```
while(1) { }
```

always makes me a bit nervous, even when it always terminates. I prefer to write it as:

```
while (!done) { ... }
```

and then appropriately set done to true when needed.

---

### Post by ThatCoolGuy220 on 2011-06-10
Hmmm interesting.

Though as an extra IDK adding a whole program as a loop could be a good idea

But i can be wrong as well

---

### Post by ThatCoolGuy220 on 2011-06-10
Sorry for double posting but i have a doubt a very small one

Alright we have this code right:

```


while(1)
      {
   
       cin >> ID2;
	
	
       if (ID == ID2)
	
      {

       cout << "Yay! ";
      
       }


       else 
    
       {
	
       cout << "Nooooooooooooooooooooooooo! ";
    
       }	
}


```


Alright but I realized that if I suppress the "{}" on for example

```


while(1)
      {
   
       cin >> ID2;
	
	
       if (ID == ID2)
	
      

       cout << "Yay! ";
      
       


       else 
    
      
	
       cout << "Nooooooooooooooooooooooooo! ";
    

}       

```

I get the same effect but why?

Or there is something that I'm not seeing?


well thats all about this subject

---

### Post by Petrolea on 2011-06-10
> **ThatCoolGuy220 said:**
> Sorry for double posting but i have a doubt a very small one

Alright we have this code right:

```


while(1)
      {
   
       cin >> ID2;
	
	
       if (ID == ID2)
	
      {

       cout << "Yay! ";
      
       }


       else 
    
       {
	
       cout << "Nooooooooooooooooooooooooo! ";
    
       }	
}


```


Alright but I realized that if I suppress the "{}" on for example

```


while(1)
      {
   
       cin >> ID2;
	
	
       if (ID == ID2)
	
      

       cout << "Yay! ";
      
       


       else 
    
      
	
       cout << "Nooooooooooooooooooooooooo! ";
    

}       

```

I get the same effect but why?

Or there is something that I'm not seeing?


well thats all about this subject

If there is only one statement after if/else you don't need { }.

---

### Post by ThatCoolGuy220 on 2011-06-10
Statement could be another if, right if not? 

this bring me to next part of the code...

```


    if (ID2 == Exit)
    
    
    break;
    


```

Wich goes after the ```
else
```


but since i wanna make stuff right a have a good/clean code

I wanna know if its recommended to add or not add the "{}"

and if there are cases can somebody explain me if it is not much a problem....

---

### Post by Petrolea on 2011-06-11
> **ThatCoolGuy220 said:**
> Statement could be another if, right if not? 

this bring me to next part of the code...

```


    if (ID2 == Exit)
    
    
    break;
    


```

Wich goes after the ```
else
```


but since i wanna make stuff right a have a good/clean code

I wanna know if its recommended to add or not add the "{}"

and if there are cases can somebody explain me if it is not much a problem....

Your hundreds of new lines make code harder to read. Statements after if should be right after if.

And it doesn't matter whether you use {} or not if there's only one statement (but for me it is more readable if there are brackets after if, but that's just me :)). But with more than one statement you MUST use brackets.

---

### Post by nvteighen on 2011-06-11
The brackets make it possible to group several statements into one single unit. The syntax for C++'s *if* statement is the following: 

```

if (condition) consequence

```

If you just use one statement in the consequence, you get:

```

if (condition) a = 9;

```

The semicolon is required because it marks the ending of a single statement... The following, more widespread version is completely equivalent because C++ doesn't care about whitespace:

```

if (condition)
    a = 9;

```

But again, that's just a single statement and C++ actually treats it as if it were one single line of code.

So, you have to use brackets when more the condition consists in more than one statement, in order to group them into one "block". The semicolon can't be used because, although grouped, several statements are not equivalent to one...

```

if (condition)
{
    a = 9;
    do_something_very_important();
}

```

I hope you now realize why using brackets for a single-statement consequence does no harm. Some people prefer them because of clarity.

---

### Post by ThatCoolGuy220 on 2011-06-11
Thanks to all yop guys I Learned even more than that I was looking for

---

