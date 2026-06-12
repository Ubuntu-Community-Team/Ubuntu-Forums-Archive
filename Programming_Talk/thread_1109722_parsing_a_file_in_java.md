---
title: "parsing a file in java"
date: 2009-03-29
forum: Programming Talk
---

### Post by Mia_tech on 2009-03-29
guys, using the Scanner for reading files how could I parse the question from the answer

Which of the following types are supertypes of Rectangle?
A) PrintStream
B) Shape
C) RectangularShape
D) Object
E) String
Select all that apply:
BCD
[PHP]
 FileReader file = new FileReader("quiz.txt");
Scanner in = new Scanner(file);
//calling the method that reads the file
q.read(in); [/PHP]


now the read method who parses questions from answers
[PHP]
public void read(Scanner in) throws IOException
    {
        boolean done = false;
        while(!done)
        {
            //code here
            addQuestions(new Question(question, answer);        
        }
    } 
[/PHP]
I'm having a bit of difficulty working with the scanner, so far I've always done it with a BufferedReader

---

### Post by simeon87 on 2009-03-29
Did you search for examples? Just Googling for 'java scanner example' gives me: [http://www.java-tips.org/java-se-tips/java.util/scanning-text-with-java.util.scanner-3.html](http://www.java-tips.org/java-se-tips/java.util/scanning-text-with-java.util.scanner-3.html)

---

### Post by Mia_tech on 2009-03-29
> **simeon87 said:**
> Did you search for examples? Just Googling for 'java scanner example' gives me: [http://www.java-tips.org/java-se-tips/java.util/scanning-text-with-java.util.scanner-3.html](http://www.java-tips.org/java-se-tips/java.util/scanning-text-with-java.util.scanner-3.html)

If I don't google is b/c sometimes either don't have the time or I'm involve in other project... so if all you going to do is post a link save your time... not interested

---

### Post by simeon87 on 2009-03-29
> **Mia_tech said:**
> If I don't google is b/c sometimes either don't have the time or I'm involve in other project... so if all you going to do is post a link save your time... not interested

If that's all you can say, why should we/I spend our/my time explaining how the Scanner class works?

Googling a few words takes zero effort and should be the first step because others have often tackled the same problem. In particular with something as common as the Scanner class.

Edit: to be clear: the link I mentioned fully answers your questions on how to do this - there's a wealth of information already on the web, so it's up to you if you're willing to use it.

---

### Post by Can+~ on 2009-03-29
> **Mia_tech said:**
> If I don't google is b/c sometimes either don't have the time or I'm involve in other project... so if all you going to do is post a link save your time... not interested

So you had the time to post in a forum, but not the time to do a google search?

Sheesh.

---

