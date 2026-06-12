---
title: "Eclipse auto-comment generation question..."
date: 2008-08-27
forum: Programming Talk
---

### Post by band-aid on 2008-08-27
According to my schools programming and commenting standards methods and classes have to be closed with a simple comment stating that this curly brace is the end of the class or method.

For Example:
```

public class helloworld
{
     public static void main(String args[])
     {
          System.out.println("Hello World!");
     }//end of main (this is the comment I am talking about)
}//end of helloworld     (this is another one of the comments)

```

I know that eclipse can auto generate comments, and I have poked around a bit in the .xml file a bit but I can't figure out how to get this comment generated. If possible, I'd like for it to be dropped in along with the ending curly brace as soon as I type the first line of the definition of the method. Currently eclipse automatically puts in the ending curly brace.

Thanks for the help
Band-aid

---

### Post by jespdj on 2008-08-27
Yuck, I hate that kind of comments and IMO they are not useful or necessary or good style at all. Just indent your code properly.

But, if you really want to do this, have a look at the Eclipse preferences (Window / Preferences). I don't know exactly how to do it, but look at Java / Code Style / Code Templates, or Java / Editor / Content Assist.

---

### Post by mike_g on 2008-08-27
I have used these types of comments before, but only in HTML. The only reason I see them being useful is if you have huge blocks of code and lots of indentation levels.

If you have that problem in Java then I would suggest restructuring you code. Generally its a good idea to make sure the code does not end up with more than 5 or so levels of indentation. Also, if a block of code is spanning more than a screen and a half it might be a good idea to break it down into a set of smaller functions. Not only does it improve the appearance of the code (to most people anyway), but i find that it makes it easier to locate problems within it.

---

### Post by Reiger on 2008-08-27
Hmm. It does sound vaguely familiar (the presumed feature of Eclipse I mean; never had to write such comments, luckily ;)) ...

Quick look: check out:

Project > Properties :

Java Code Style > Formatter :

Check the box at "Enable project specific settings":
Edit the profile or create a new one.
If you choose edit:
Click the "Comments" tab.

---

### Post by Shin_Gouki2501 on 2008-08-27
Maybe he should look for something like JavaDoc?

---

### Post by Tomosaur on 2008-08-27
> **Shin_Gouki2501 said:**
> Maybe he should look for something like JavaDoc?

Javadoc creates documentation (usually to take the pain out of creating an API, and things of that nature) - it is not generally for commenting specific parts of the code. It is more for use as a developer reference on a website, rather than making a developer's life easier when reading the actual code.

To the OP - I'm pretty sure Eclipse will allow you to do this - check out the Editor > Templates section in the main preferences window. There are default templates for different methods (public, static etc) which you can edit however you like. I think you can use them by hitting Ctrl+Space twice, but I never use this so you'll have to check yourself.

---

### Post by band-aid on 2008-08-27
Thanks for the replies, I'll let you know how it goes. As I said earlier, these are my schools coding standards and I don't have any say. It is a simple matter of do it their way, or fail the project.

---

