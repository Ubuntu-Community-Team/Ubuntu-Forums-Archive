---
title: "Using Tokenizer on Java and having a couple problems"
date: 2011-03-07
forum: Programming Talk
---

### Post by kanazky on 2011-03-07
I am attempting to retrieve every 5th Element from a file using the Tokenizer


The hasNextToken appears to run about 30 times more then it should and when I use the token count function it returns a number half the size of the actual number of tokens.

StringTokenizer st = new StringTokenizer(line);
while(st.hasNextToken())
{
    if(counter % 5 == 0)
        aStringBuilderObject.append(st.nextToken);
    counter++;
}

is the method I am currently using. Seems to run like this when I add debug Script

Word1
Word2
-
-
-
-
Word3
Word4
-
-
-
-
Word5
Word6

and so forth. - being the % 5 = false case

---

### Post by Arndt on 2011-03-07
> **kanazky said:**
> I am attempting to retrieve every 5th Element from a file using the Tokenizer


The hasNextToken appears to run about 30 times more then it should and when I use the token count function it returns a number half the size of the actual number of tokens.

StringTokenizer st = new StringTokenizer(line);
while(st.hasNextToken())
{
    if(counter % 5 == 0)
        aStringBuilderObject.append(st.nextToken);
    counter++;
}

is the method I am currently using. Seems to run like this when I add debug Script

Word1
Word2
-
-
-
-
Word3
Word4
-
-
-
-
Word5
Word6

and so forth. - being the % 5 = false case

I can't explain your numbers, 30, half, etc. but shouldn't you read the next token each time in the loop? Now you read something only every fifth time.

---

### Post by lykeion on 2011-03-07
> **kanazky said:**
> I am attempting to retrieve every 5th Element from a file using the Tokenizer

Why don't you use String.split() method instead. This example splits a string by spaces and prints out every fifth result. You can change the regex argument of split to the delimiter you want. 
```
String test = "one two three four five six seven eight";
String[] result = test.split("\\s");
for (int x=0; x<result.length; x=x+5) {
    System.out.println(result[x]);
}
```

---

### Post by kanazky on 2011-03-07
I was thinking of string split, but my data file will prob use different delimitars for information. With StringTokenizer I can change the Delimitar between delimiters and still get good runtime. 

My only problem is the loop is running way to many times. Its running like 30x what it should without the extra delimitars. When I use token count it only returns 1/2 the actual number of delimitars in my data file. 

This is really hurting development -.- as its not logically explained error lol

---

### Post by stchman on 2011-03-07
> **kanazky said:**
> I was thinking of string split, but my data file will prob use different delimitars for information. With StringTokenizer I can change the Delimitar between delimiters and still get good runtime. 

My only problem is the loop is running way to many times. Its running like 30x what it should without the extra delimitars. When I use token count it only returns 1/2 the actual number of delimitars in my data file. 

This is really hurting development -.- as its not logically explained error lol

No problem, the delimiter is just a String.

```

String test = "one two three four five six seven eight";
String delim = "\\s";
String[] result = test.split( delim );
for ( int x = 0; x < result.length; x+=5 )
{
    System.out.println( result[x] );
}

```

You can even make delim a global type variable.

---

### Post by VernonA on 2011-03-10
Arndt correctly identified the bug in your code, but you didn't listen. The call to get the token needs to happen every iteration, not once every 5 iterations as you've written. The hasNextToken() call doesn't advance the tokeniser, so it is returning true for the same token five times in a row, not for 5 different tokens as you have assumed.

---

