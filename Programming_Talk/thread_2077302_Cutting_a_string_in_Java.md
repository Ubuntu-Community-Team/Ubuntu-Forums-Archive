---
title: "Cutting a string in Java"
date: 2012-10-28
forum: Programming Talk
---

### Post by Drenriza on 2012-10-28
Hi guys.
 
I have the following 3 strings.
```

aaaaaaa <img class='avatar' alt='' src='http://path/x.png' /
bbbbbbbbbb </strong
cccc ccccc #6</li
```
 
How can i cut this to
```

aaaaaaa
bbbbbbbbbb
6

```
 
How can you say, print everything before the first < in the first two and print the first character after #
 
Thanks on advance.
Kind regards

---

### Post by bird1500 on 2012-10-28
You mean JavaScript

---

### Post by Drenriza on 2012-10-28
> **bird1500 said:**
> You mean JavaScript
 
I mean Java :)
 
The output above have i gotten from saying
```

url = new URL("[website]("http://cogdev.net/blink/?act=home")");
dis = new DataInputStream((new BufferedInputStream(is = url.openStream())));

```

---

### Post by Vaphell on 2012-10-28
string.split( regex ) and then take proper element from the returned array? #1, #2: "<", #3: "#|<"

---

### Post by lykeion on 2012-10-28
String.split() is fine for splitting strings, but for HTML it's better to use a proper parser like jsoup, see [http://jsoup.org](http://jsoup.org)

---

### Post by Drenriza on 2012-10-28
> **Vaphell said:**
> string.split( regex ) and then take proper element from the returned array? #1, #2: "<", #3: "#|<"
 
Yes i have tried the split command. But how do i get it to cut the characters infront of the delimiter and not after?

---

### Post by Vaphell on 2012-10-28
if you use regex '# OR <' result[1] will be the number alone

to illustrate the idea using awk (i don't know java, i have no clue how to write even 'hello world')
```
echo "cccc ccccc #6</li" | awk '{ str=$0; n=split(str, a, "**<|#**"); for( i=1; i<=n; i++) print i ":" a[i]; }'
1:cccc ccccc 
**2:6**
3:/li
```

if you really have to get the the last char of the subpart, something like string[i].substr( string[i].length()-2, 1 )

---

### Post by Drenriza on 2012-10-28
> **lykeion said:**
> String.split() is fine for splitting strings, but for HTML it's better to use a proper parser like jsoup, see [http://jsoup.org](http://jsoup.org)
 
It sounds cleaver enough, but dunno how to proced with it.
 
The documentation (that i can find) is less then perfect :confused:

---

### Post by Drenriza on 2012-10-28
Anyone who can help me out?
 
Even tho vaphell comes with some suggestions, i cant seam to get it work as i want.

---

### Post by Vaphell on 2012-10-28
i don't even... o.O ;-)

my first java program ever
```
class test
{  
  public static void main(String args[])
  {
     String[] str = { "aaaaaaa <img class='avatar' alt='' src='http://path/x.png' /", "bbbbbbbbbb </strong", "cccc ccccc #6</li" };
     String[] parts;
     
     for( int n=0; n<str.length; n++ )
     {
       System.out.printf("string = %s\n", str[n] );
       parts = str[n].split("<|#");
       for( int i=0; i<parts.length; i++ )
         System.out.printf( "parts[%d] = '%s'\n", i, parts[i] );
// assuming next-to-last element
       System.out.printf( "result = '%s'\n", parts[parts.length-2] );
     }
  };
}
```

```
$ javac test.java
$ java test
string = aaaaaaa <img class='avatar' alt='' src='http://path/x.png' /
parts[0] = 'aaaaaaa '
parts[1] = 'img class='avatar' alt='' src='http://path/x.png' /'
result = 'aaaaaaa '
string = bbbbbbbbbb </strong
parts[0] = 'bbbbbbbbbb '
parts[1] = '/strong'
result = 'bbbbbbbbbb '
string = cccc ccccc #6</li
parts[0] = 'cccc ccccc '
parts[1] = '6'
parts[2] = '/li'
result = '6'

```

but i agree that this can work reliably only in simplest of cases and a proper parser may be required.

---

### Post by ofnuts on 2012-10-28
> **Drenriza said:**
> Hi guys.
 
I have the following 3 strings.
```

aaaaaaa <img class='avatar' alt='' src='http://path/x.png' /
bbbbbbbbbb </strong
cccc ccccc #6</li
```How can i cut this to
```

aaaaaaa
bbbbbbbbbb
6

```How can you say, print everything before the first < in the first two and print the first character after #
 
Thanks on advance.
Kind regards
String.split() is IMHO a bit simplistic here, you have better use a regular expression (in Java these are mostly covered by java.util.regex.Patten and java.util.regex.Matcher)[. ]("http://docs.oracle.com/javase/1.4.2/docs/api/java/util/regex/Pattern.html")

[LIST]
[*]Come up with a regular expression that describes your expected string and use grouping parentheses for the parts you want to extract. This is the hard part, and requires a specification much less ambiguous than your question above.
[*]Initialize a Pattern from it (this can be built once and reused for each match).
[*]For each string you want to analyze, ask the pattern to create a Matcher from it.
[*]Ask the matched if it matched, and if so, retrieve the groups from it.
[/LIST]

[]("http://docs.oracle.com/javase/1.4.2/docs/api/java/util/regex/Pattern.html")

---

### Post by Drenriza on 2012-10-28
> **Vaphell said:**
> i don't even... o.O ;-)
 
my first java program ever
```
class test
{  
  public static void main(String args[])
  {
     String[] str = { "aaaaaaa <img class='avatar' alt='' src='http://path/x.png' /", "bbbbbbbbbb </strong", "cccc ccccc #6</li" };
     String[] parts;
 
     for( int n=0; n<str.length; n++ )
     {
       System.out.printf("string = %s\n", str[n] );
       parts = str[n].split("<|#");
       for( int i=0; i<parts.length; i++ )
         System.out.printf( "parts[%d] = '%s'\n", i, parts[i] );
// assuming next-to-last element
       System.out.printf( "result = '%s'\n", parts[parts.length-2] );
     }
  };
}
```
 
```
$ javac test.java
$ java test
string = aaaaaaa <img class='avatar' alt='' src='http://path/x.png' /
parts[0] = 'aaaaaaa '
parts[1] = 'img class='avatar' alt='' src='http://path/x.png' /'
result = 'aaaaaaa '
string = bbbbbbbbbb </strong
parts[0] = 'bbbbbbbbbb '
parts[1] = '/strong'
result = 'bbbbbbbbbb '
string = cccc ccccc #6</li
parts[0] = 'cccc ccccc '
parts[1] = '6'
parts[2] = '/li'
result = '6'

```
 
but i agree that this can work reliably only in simplest of cases and a proper parser may be required.
 
Vaphell wouldn't you be kind enough to explain what your doing.
 
For example what does your %d and %s do.

---

### Post by Drenriza on 2012-10-28
> String.split() is IMHO a bit simplistic here, you have better use a regular expression
 
If you have a good guide / book. Please dont hold back :)

---

### Post by Vaphell on 2012-10-28
it's a run-of-the-mill printf() function that works the same in C, bash, awk and tons of other languages. I noticed java has printf so i used it instead of googling for a kosher way of doing things in the language.
First arg is the format string where %X are placeholders filled with the subsequent args. %d is for numbers, %s is for strings
```
System.out.printf( "parts[[COLOR="Blue"]%d[/COLOR]] = '[COLOR="DarkGreen"]%s[/COLOR]'\n", [COLOR="Blue"]i[/COLOR], [COLOR="DarkGreen"]parts[i][/COLOR] );
```

[http://en.wikipedia.org/wiki/Printf_format_string](http://en.wikipedia.org/wiki/Printf_format_string)

---

### Post by ofnuts on 2012-10-30
> **Drenriza said:**
> If you have a good guide / book. Please dont hold back :)

[http://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124/ref=sr_1_1](http://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124/ref=sr_1_1)

Accept no substitutes.

---

