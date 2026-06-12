---
title: "Test My Java Program!"
date: 2008-08-06
forum: Programming Talk
---

### Post by tdrusk on 2008-08-06
It's nothing special but...

I have been working on this for a few hours today and yesterday. Basically it is supposed to request a list of keywords, request a link, request a paragraph, search through the paragraph and replace the keywords with a linked keyword, then ask if the link is a video.

Anyway. I noticed one thing that needs to be ironed out. If the keyword is more than two words it will only capitalize the first word. I thought about separating the words, but if I did that it would make two separate links. I only want one.

Besides that I can't think of anything else that is wrong with it. Is it user friendly and easy to understand?

I am just going to share this with some of the people that I am working with. We have to write paragraphs with keywords in them and link back to a specific site. 

Attached is the program. Java must be installed. All you have to do is extract the directory, go to it, and run ```
java Linker
```Thanks in advance,

Tyler

P.S. I am new to Java. Please don't look down on me if I did something that was wasteful. I would however love to hear how to do it easier. I am here to learn :).

---

### Post by tinny on 2008-08-06
> **tdrusk said:**
> It's nothing special but...

I have been working on this for a few hours today and yesterday. Basically it is supposed to request a list of keywords, request a link, request a paragraph, search through the paragraph and replace the keywords with a linked keyword, then ask if the link is a video.

Anyway. I noticed one thing that needs to be ironed out. If the keyword is more than two words it will only capitalize the first word. I thought about separating the words, but if I did that it would make two separate links. I only want one.

Besides that I can't think of anything else that is wrong with it. Is it user friendly and easy to understand?

I am just going to share this with some of the people that I am working with. We have to write paragraphs with keywords in them and link back to a specific site. 

Attached is the program. Java must be installed. All you have to do is extract the directory, go to it, and run ```
java Linker
```Thanks in advance,

Tyler

P.S. I am new to Java. Please don't look down on me if I did something that was wasteful. I would however love to hear how to do it easier. I am here to learn :).

I ran your app. Output:

```

                                xXxXxXxXxXxXxXxXx
                                X    Linker            X
                                x By Tyler Rusk x
                                XxXxXxXxXxXxXxXxX


Enter the keywords that you want linked (lowercase only). Separate keywords with commas.
Example: dog,cat,big turtle,moose
sean


Enter the website you want each keyword to link to
google.com


Enter Paragraph. Start all sentences with lowercase letters. After each period put a space.
        Example: i like dogs. dogs are fun.
Do not press enter until you are ready to submit.
one day sean. two day sean.

 One day <a href="google.COm">Sean</a>. Two day <a href="google.COm">Sean</a>.


You want to use Linker again?(true or false)
false
BUILD SUCCESSFUL (total time: 1 minute 46 seconds)


```


Does some funny things with "google.com" E.g google.COm .

Also I think you should put a "> " before scanning for input (makes it clearer that you can input text).

Coding tip, I personally prefer to use String split instead of string tokenizer.

[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html#split(java.lang.String](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html#split(java.lang.String))

---

### Post by tinny on 2008-08-06
Also

[PHP]
import java.util.*;
[/PHP]

Wild card imports are not so good.

---

### Post by tdrusk on 2008-08-06
> **tinny said:**
> I ran your app. Output:

```

                                xXxXxXxXxXxXxXxXx
                                X    Linker            X
                                x By Tyler Rusk x
                                XxXxXxXxXxXxXxXxX


Enter the keywords that you want linked (lowercase only). Separate keywords with commas.
Example: dog,cat,big turtle,moose
sean


Enter the website you want each keyword to link to
google.com


Enter Paragraph. Start all sentences with lowercase letters. After each period put a space.
        Example: i like dogs. dogs are fun.
Do not press enter until you are ready to submit.
one day sean. two day sean.

 One day <a href="google.COm">Sean</a>. Two day <a href="google.COm">Sean</a>.


You want to use Linker again?(true or false)
false
BUILD SUCCESSFUL (total time: 1 minute 46 seconds)


```Does some funny things with "google.com" E.g google.COm .

Also I think you should put a "> " before scanning for input (makes it clearer that you can input text).

Coding tip, I personally prefer to use String split instead of string tokenizer.

[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html#split(java.lang.String]("http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html#split%28java.lang.String"))
Thanks. Would it matter since it's just html and capitalization doesn't matter with links does it?

I tried to use split as the code appears easier, but I can't get it to work. Someone suggested using
```
String x ="keyword,keyword,keyword"; 
String []keys=x.split(',');  
```but it returns "illegal start of expression"

> **tinny said:**
> Also

[php]
import java.util.*;
[/php]Wild card imports are not so good.
Good call. What would I have to import to make my program run correctly?

Also....
I am trying to make it so it saves the link and keywords so I don't have to enter them in again. I moved 
```
        //Scans for website that is being linked to.
        System.out.println("\n\nEnter the website you want each keyword to link to");
        String link = scan.nextLine();
        
        //Scans for keywords that need to be linked.            
        System.out.println("\n\nEnter the keywords that you want linked (lowercase only). Separate keywords with commas.");
        System.out.println("Example: dog,cat,big turtle,moose");
        String keywords = scan.nextLine();
```above the do loop and it compiles, but I get this error when I answer true at the end. 
```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: String index out of range: 2
        at java.lang.String.substring(String.java:1935)
        at Linker.main(Linker.java:61)
```To reproduce this error the code looks like the attached file.

Thanks for all your help so far and if you can answer any of my questions it would be greatly appreciated.

---

### Post by tinny on 2008-08-07
> 
Would it matter since it's just html and capitalization doesn't matter with links does it?


Yes, but not good form.

> 
Good call. What would I have to import to make my program run correctly?


[PHP]
import java.util.Scanner;
import java.util.StringTokenizer;
[/PHP]

Too use the string split: (your [] was in the wrong place)

[PHP]
String x ="keyword,keyword,keyword";
String[] keys = x.split(",");
[/PHP]

I dont really understand your other question (not with out doing it for you ;) )

---

### Post by tdrusk on 2008-08-07
> **tinny said:**
> Yes, but not good form.



[php]
import java.util.Scanner;
import java.util.StringTokenizer;
[/php]Too use the string split: (your [] was in the wrong place)

[php]
String x ="keyword,keyword,keyword";
String[] keys = x.split(",");
[/php]I dont really understand your other question (not with out doing it for you ;) )
Thanks. I will keep trying to work with it. I really appreciate your help.

---

### Post by tinny on 2008-08-07
Here is a basic guide to using files in Java. (you could write your result to a file).

[http://www.javacoffeebreak.com/java103/java103.html](http://www.javacoffeebreak.com/java103/java103.html)

---

### Post by tdrusk on 2008-08-07
> **tinny said:**
> Here is a basic guide to using files in Java. (you could write your result to a file).

[http://www.javacoffeebreak.com/java103/java103.html](http://www.javacoffeebreak.com/java103/java103.html)
Yes! i was wondering about this. We have to write the link to the page we are on along with the keyword. This should help. :guitar:

---

