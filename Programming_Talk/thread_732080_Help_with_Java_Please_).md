---
title: "Help with Java Please :)"
date: 2008-03-22
forum: Programming Talk
---

### Post by The3rdhero on 2008-03-22
I need to take a String which could be declared like:

String myString = "Ubuntu for teh win"

Then, I'm writing a method called Chop(), which will chop the string referenced by myString into its constituent words and return them as
an array of strings.

Any help please? :)

The closest I've got is toCharArray() - but it isn't quite what I need.

---

### Post by Wybiral on 2008-03-22
I think you're looking for the [split]("http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#split(java.lang.String)") method.

---

### Post by The3rdhero on 2008-03-22
Thank you bud, I've created it and it works like I wanted it to.

=D>


---------

Okay, I've come across yet another problem, I am new to Java so I'm still experimenting, but here goes...
My code below is meant to take the string in htmlPage - chop it up into an array called words, then i need to search the words array for the strings in links, if they exist, I need it to make a link of that word.  For example, if the word PageEnhancer is in both words[ ] and links[ ] then it should make the word PageEnhancer into a link.
The problem I'm having is below the code.

>    
   public String htmlPage = "<HTML> <TITLE> Page Enhancer </TITLE>"
                          + " <BODY> <H1> Hello </H1>"
                          + " <P> This page is the main page of PageEnhancer </P>"
                          + " <P> From here you will be able to click links </P>"
                          + " <P> that will take you to the index and"
                          + " contents pages </P> </BODY>";
   public String[ ][ ] links = {{"index", "index.html"}, {"contents", "contents.html"}, {"PageEnhancer", "description.html"}};



public StringBuilder addHyperLinks()
   {
      StringBuilder newPage = new StringBuilder();
      String[] words = htmlPage.split(" ");
      for(int k = 0; k < words.length; k++)
      {
         for(int i = 0; i < links.length; i++)
         {
            if(links[i][0] == words[k])
            {
               String pageLink = links[i][1];
               newPage.append("<a href=\"" + pageLink + "\">" + words[k] + "</a>");
            }
            if(links[i][0] != words[k])
            {
               newPage.append(words[k]);
               System.out.print(" ");
            }
         }
      }
      return newPage;
   }

> 
The code displays everything 3 times:

<HTML><HTML><HTML><TITLE><TITLE><TITLE>PagePagePageEnhancerEnhancerEnhancer</TITLE></TITLE></TITLE><BODY><BODY><BODY><H1><H1><H1>HelloHelloHello</H1></H1></H1><P><P><P>ThisThisThispagepagepageisisisthethethemainmainmainpagepagepageofofofPageEnhancerPageEnhancerPageEnhancer</P></P></P><P><P><P>FromFromFromhereherehereyouyouyouwillwillwillbebebeableableabletototoclickclickclicklinkslinkslinks</P></P></P><P><P><P>thatthatthatwillwillwilltaketaketakeyouyouyoutototothethetheindexindexindexandandandcontentscontentscontentspagespagespages</P></P></P></BODY></BODY></BODY>


Any help/solutions will be grately appreciated :)

---

### Post by nick_h on 2008-03-22
Yes - split is the method you need.  The following is an example from the java.sun.com documentation.  \s is the reqular expression for whitespace.
```
String[] result = "this is a test".split("\\s");
    for (int x=0; x<result.length; x++)
        System.out.println(result[x]);
```

EDIT: Too late! I just saw you got it working :)

---

### Post by The3rdhero on 2008-03-22
Sorry, but the quote thing removed my indenting >.<

---

### Post by imdano on 2008-03-22
Use code or php instead of quote.  It's really hard to read it as it is now.

---

### Post by Wybiral on 2008-03-22
Suppose we had three words that needed to be made into links: "why", "hello", "world" and our input string, for simplicity, was a single word, "xxx".

Your loop looks like it's doing this (a bit hard to tell without indentation, you should use "[ code ]" instead of "[ quote ]":

if "xxx" != "why": append("xxx");
if "xxx" != "hello": append("xxx");
if "xxx" != "world": append("xxx");

The result is "xxxxxxxxx".

Do you see what I mean?

---

### Post by ZylGadis on 2008-03-22
His trouble actually is incorrect comparison of Strings. String variables in Java contain references to String objects; so, if you compare the variables with the typical boolean equivalence operator, you'll get false nearly always, no matter what the objects contain. You need the equals method, like this:

```

String a = "something", b = "something";
if (a == b) //returns false, as the variables contain references to different objects
  System.out.println("a points to the same object as b");
if (a.equals(b)) //returns true, as the two objects contain the same String value
  System.out.println("String ref'd by a is same as String ref'd by b");

```

So, in your code, when you compare two String vars with == you never get into the block, and when you compare them with != you always get into the block. Use equals.

String is a very tricky thing in Java. It is a class, but at the same time special provisions have been made for it in the language, so that in some (most?) cases it behaves like a primitive type. Be careful with it.

---

### Post by The3rdhero on 2008-03-25
I'm Still having problems with this :(

I'll repost using code.
As I said above, for some reason, it's displaying each word 3 times when It should only do it once, and add links where it's needed.

```
   public String htmlPage = "<HTML> <TITLE> Page Enhancer </TITLE>"
                          + " <BODY> <H1> Hello </H1>"
                          + " <P> This page is the main page of PageEnhancer </P>"
                          + " <P> From here you will be able to click links </P>"
                          + " <P> that will take you to the index and"
                          + " contents pages </P> </BODY>";
   public String[][] links = {{"index", "index.html"}, {"contents", "contents.html"}, {"PageEnhancer", "description.html"}};

   public StringBuilder addHyperLinks()
   {
      StringBuilder newPage = new StringBuilder();
      String[] words = htmlPage.split(" ");
      for(int k = 0; k < words.length; k++)
      {
         for(int i = 0; i < links.length; i++)
         {
            if(links[i][0] == words[k])
            {
               String pageLink = links[i][1];
               newPage.append("<a href=\"" + pageLink + "\">" + words[k] + "</a>");
            }
            else
            {
               newPage.append(words[k]);
               System.out.print(" ");
            }
         }
      }
      return newPage;
   }

```

---

### Post by imdano on 2008-03-25
Trace out what happens.  You're checking if words[k] matches links[i][0] (and you're doing that incorrectly, see the post above yours for what you're doing wrong).

So first it checks words[k] against links[0][0], then links[1][0], then links[2][0].  Every time it checks and doesn't find a match, it's doing a newPage.append(words[k]).  Since you're checking for equality incorrectly, it never finds a match, and just appends words[k] three times.

Instead, you should be checking all of links for match, and if no match is found in the whole thing, then call newPage.append(words[k]), so that it only gets appended once.

---

### Post by The3rdhero on 2008-03-25
Am I right in having 2 **for** loops?

---

