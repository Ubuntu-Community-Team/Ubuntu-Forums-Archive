---
title: "Java: Writing a  program to take key words and make them links..."
date: 2008-08-05
forum: Programming Talk
---

### Post by tdrusk on 2008-08-05
I need to be able to enter a list of x amount of keywords. Then I need to write a paragraph. The program has to take those key words and replace them with <a href="http://website.com">keyword</a>. I can do everything but the first part. How can I type a list of keywords, preferably separated by commas, and make strings for each keyword? Is there an easier way to do this?

Thanks in advance!

---

### Post by issih on 2008-08-05
Easier than what?
What kind of interface are you using? console aplication, swing gui?
In essence assuming you can get hold of a string that is:
"keyworda, keywordb, keywordc" you just tokenise that string based on the ',' character. The dirt simple way would be to just use the split command, or alternatively the indexof and substring ones if you are targetting a jvm prior to regular expression support.

[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html)

---

### Post by descendency on 2008-08-05
as issih said, store them into a single string. When you need them, call the string, split it (based on your separator character [ie ","]), and loop through the resulting array creating your links.

---

### Post by tdrusk on 2008-08-05
I'm still really confused with this. 

I tried
```


[COLOR=#7f0055]**import **[/COLOR][COLOR=#000000]java.util.*;[/COLOR]

[COLOR=#7f0055]**public class **[/COLOR][COLOR=#000000]StringTokenizing[/COLOR][COLOR=#000000]{[/COLOR]
[COLOR=#ffffff]  [/COLOR][COLOR=#7f0055]**public static **[/COLOR][COLOR=#7f0055]**void **[/COLOR][COLOR=#000000]main[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]String[/COLOR][COLOR=#000000][] [/COLOR][COLOR=#000000]args[/COLOR][COLOR=#000000]) {[/COLOR]
[COLOR=#ffffff]    [/COLOR][COLOR=#000000]StringTokenizer stringTokenizer = [/COLOR][COLOR=#7f0055]**new **[/COLOR][COLOR=#000000]
     StringTokenizer[/COLOR][COLOR=#000000]([/COLOR][COLOR=#2a00ff]"You are tokenizing a string"[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#ffffff]    [/COLOR][COLOR=#000000]System.out.println[/COLOR][COLOR=#000000]([/COLOR][COLOR=#2a00ff]"The total no. of tokens 
   generated :  " [/COLOR][COLOR=#000000]+ stringTokenizer.countTokens[/COLOR][COLOR=#000000]())[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#ffffff]    [/COLOR][COLOR=#7f0055]**while**[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]stringTokenizer.hasMoreTokens[/COLOR][COLOR=#000000]()){[/COLOR]
[COLOR=#ffffff]      [/COLOR][COLOR=#000000]System.out.println[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]stringTokenizer.nextToken[/COLOR][COLOR=#000000]())[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#ffffff]    [/COLOR][COLOR=#000000]}[/COLOR]
[COLOR=#ffffff]  [/COLOR][COLOR=#000000]}[/COLOR]
[COLOR=#000000]}[/COLOR]

```

which works. But when I scan for a string(keywords), and replace "You are tokenizing a string" with (keywords) it only comes out as the first word in the string. What's wrong here?

---

### Post by lisati on 2008-08-05
> **tdrusk said:**
> I'm still really confused with this. 

I tried
```


[COLOR=#7f0055]**import **[/COLOR][COLOR=#000000]java.util.*;[/COLOR]

[COLOR=#7f0055]**public class **[/COLOR][COLOR=#000000]StringTokenizing[/COLOR][COLOR=#000000]{[/COLOR]
[COLOR=#7f0055]**public static **[/COLOR][COLOR=#7f0055]**void **[/COLOR][COLOR=#000000]main[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]String[/COLOR][COLOR=#000000][] [/COLOR][COLOR=#000000]args[/COLOR][COLOR=#000000]) {[/COLOR]
[COLOR=#000000]StringTokenizer stringTokenizer = [/COLOR][COLOR=#7f0055]**new **[/COLOR][COLOR=#000000]
     StringTokenizer[/COLOR][COLOR=#000000]([/COLOR][COLOR=#2a00ff]"You are tokenizing a string"[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#000000]System.out.println[/COLOR][COLOR=#000000]([/COLOR][COLOR=#2a00ff]"The total no. of tokens 
   generated :  " [/COLOR][COLOR=#000000]+ stringTokenizer.countTokens[/COLOR][COLOR=#000000]())[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#7f0055]**while**[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]stringTokenizer.hasMoreTokens[/COLOR][COLOR=#000000]()){[/COLOR]
[COLOR=#000000]System.out.println[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]stringTokenizer.nextToken[/COLOR][COLOR=#000000]())[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]}[/COLOR]

```which works. But when I scan for a string(keywords), and replace "You are tokenizing a string" with (keywords) it only comes out as the first word in the string. What's wrong here?
Just one question from someone who isn't overly familiar with Java: Where are you storing the keywords?

---

### Post by issih on 2008-08-05
[http://java.sun.com/j2se/1.4.2/docs/api/java/util/StringTokenizer.html](http://java.sun.com/j2se/1.4.2/docs/api/java/util/StringTokenizer.html)

If you want to use that class you need to use the 2 parameter constructor and define your delimiter characters.

e.g.

```
import java.util.*;

public class StringTokenizing{
public static void main(String[] args) {
String input = "keyworda,keywordb,keywordc";
StringTokenizer stringTokenizer = new 
     StringTokenizer(input, ", ");
//N.B. each character in the second string acts as a delimiter, so this
//will split on spaces AND commas.
System.out.println("The total no. of tokens 
   generated :  " + stringTokenizer.countTokens());
while(stringTokenizer.hasMoreTokens()){
System.out.println(stringTokenizer.nextToken());
}
}
}
```

This method is the old way of doing things however, you'd be better off using the split method of the string class really, this will work though.

---

### Post by tdrusk on 2008-08-05
> **lisati said:**
> Just one question from someone who isn't overly familiar with Java: Where are you storing the keywords?
I am storing them as a string. It looks something like this:
```

import java.util.*;
import java.util.Scanner;
public class Casey {

    public static void main (String args[]) {    
        Scanner sc = new Scanner(System.in);
        String input = sc.next();
        StringTokenizer stringTokenizer = new 
         StringTokenizer(input, ", ");
        //N.B. each character in the second string acts as a delimiter, so this
        //will split on spaces AND commas.
        System.out.println("The total no. of tokens generated :  " + stringTokenizer.countTokens());
        while(stringTokenizer.hasMoreTokens()){
            System.out.println(stringTokenizer.nextToken());
}
}
}

```

---

### Post by tdrusk on 2008-08-05
*sigh* this is much harder than I thought it would be. 

I've gotten this far
```

import java.util.*;
import java.util.Scanner;
public class Casey {

    public static void main (String args[]) {    
        Scanner scan = new Scanner(System.in);
        String keywords = scan.next();
        
StringTokenizer stringTokenizer = new 
     StringTokenizer(keywords, ", ");
//N.B. each character in the second string acts as a delimiter, so this
//will split on spaces AND commas.
System.out.println("The total no. of tokens  generated :  " + stringTokenizer.countTokens());
while(stringTokenizer.hasMoreTokens()){
System.out.println(stringTokenizer.nextToken());
}


String paragraph = scan.next();

String p2= paragraph.replace("cat", "dog");
System.out.println(p2);
}
}
```

I enter "I like cat" but all that comes out is "i"

Is there a program out there that can do this for me with less hassle. I really just want to increase the speed of the work that I'm doing, and i've been working on this for 2 hours.

---

### Post by drubin on 2008-08-05
> **tdrusk said:**
> I am storing them as a string. It looks something like this:
```

import java.util.*;
import java.util.Scanner;
public class Casey {

    public static void main (String args[]) {    
        Scanner sc = new Scanner(System.in);
        String input = sc.next();
        StringTokenizer stringTokenizer = new 
         StringTokenizer(input, ", ");
        //N.B. each character in the second string acts as a delimiter, so this
        //will split on spaces AND commas.
        System.out.println("The total no. of tokens generated :  " + stringTokenizer.countTokens());
        while(stringTokenizer.hasMoreTokens()){
            System.out.println(stringTokenizer.nextToken());
}
}
}

```

[PHP]String x ="keyword,keyword,keyword";
String []keys=x.split(',');[/PHP]

That seems easier to do though :) split was added in JDK1.5

---

### Post by issih on 2008-08-05
Your current problem is coming from the fact that you are using the Scanner class. This is actually designed to tokenise input much as you were trying to do with your keyword list.

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html)

by default it tokenises on whitespace, so the only thing returned when you ask for sc.next is the first token of (I like cats) which given it splits on whitespace is i.

if you use the nextLine method of Scanner repetitively, appending the result into the same string you avoid this:

String paragraph = "";
String line = sc.nextLine();
while(!line.equals(""))
{
    paragraph = paragraph + line;
    line = sc.nextLine();
}

something like that ought to grab a whole paragraph provided you entered an empty line at the end.

---

### Post by tdrusk on 2008-08-05
> **issih said:**
> Your current problem is coming from the fact that you are using the Scanner class. This is actually designed to tokenise input much as you were trying to do with your keyword list.

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html)

by default it tokenises on whitespace, so the only thing returned when you ask for sc.next is the first token of (I like cats) which given it splits on whitespace is i.

if you use the nextLine method of Scanner repetitively, appending the result into the same string you avoid this:

String paragraph = "";
String line = sc.nextLine();
while(!line.equals(""))
{
    paragraph = paragraph + line;
    line = sc.nextLine();
}

something like that ought to grab a whole paragraph provided you entered an empty line at the end.
Yep, just found that in my handy dandy java book. Thanks!

---

### Post by tdrusk on 2008-08-06
Okay guys I'm almost finished. I just need to make some final tweaks and I need your help!

```
import java.util.*;
import java.util.Scanner;
public class Casey {

    public static void main (String args[]) {    
        //Scans for keywords that need to be linked.
        System.out.println("Enter the keywords that you want linked. Only separate words with spaces");
        System.out.println("For example... dog,cat,big turtle,moose");
        Scanner scan = new Scanner(System.in);
        String keywords = scan.nextLine();
        
        //Scans for website that is being linked to.
        System.out.println("Enter the website you want each keyword to link to");
        String link = scan.nextLine();
        
        //Scans for paragraph that has keywords that need to be linked.        
        System.out.println ("Enter Paragraph. Do not press enter until you are ready to submit.");
        String paragraph = scan.nextLine();
        
        //Separates keywords by ","
        StringTokenizer keywordsTokenizer = new         
        StringTokenizer(keywords, ",");
        
        //Looks through the paragraph and replaces keyword with a linked and capitalized keyword.
        while(keywordsTokenizer.hasMoreTokens())
        {
            //
            String current = keywordsTokenizer.nextToken();
            String newCurrent = current.substring(0, 1).toUpperCase() + current.substring(1);
            paragraph = paragraph.replace(current, "<a href=\"" + link + "\">" + newCurrent + "</a>");
        }
        //Prints the paragraph complete with links
        System.out.println(paragraph);
        
        
}
}
```

Okay in the while loop
 ```
while(keywordsTokenizer.hasMoreTokens())
        {
            //
            String current = keywordsTokenizer.nextToken();
            String newCurrent = current.substring(0, 1).toUpperCase() + current.substring(1);
            paragraph = paragraph.replace(current, "<a href=\"" + link + "\">" + newCurrent + "</a>");
        }
```

It only accepts keywords that are exactly as they were submitted. Example: cat would not work for Cat, so Cat would not be linked. How can I fix this?

Also, I want it to capitalize all the keywords. For example keyword: big duck, I want it to come out as Big Duck, not Big duck as it is now. How can I do this?

Thanks for all the help so far.

---

