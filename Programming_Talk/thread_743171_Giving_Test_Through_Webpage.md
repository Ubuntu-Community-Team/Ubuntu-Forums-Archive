---
title: "Giving Test Through Webpage"
date: 2008-04-02
forum: Programming Talk
---

### Post by TreeFinger on 2008-04-02
I'm wondering if someone could give me some advice on implementing a little online quiz on a webpage. I'm looking for something quick and easy.. nothing to complicated. Doesn't need to save scores anywhere.. just display the score once for the user. Maybe an option to e-mail the score to an e-mail address.

What would be the best way to implement this in a quick and easy way?

---

### Post by mike_g on 2008-04-02
How about an HTML form?

---

### Post by joshdudeha on 2008-04-02
You could use javascript?

---

### Post by LaRoza on 2008-04-02
What are the specs? Perhaps I could whip something up.

Here are two self test quizes I wrote for someone studying for a test: [http://laroza.freehostia.com/home/apps/airlines/index.php](http://laroza.freehostia.com/home/apps/airlines/index.php)

(The answers are in that text file and there are two tests)

---

### Post by TreeFinger on 2008-04-02
Well, this is for part of a school project so I'd like to do it myself. Thank you for the responses so far.

How could an HTML form test if a user inputs a correct answer?

---

### Post by mssever on 2008-04-02
> **TreeFinger said:**
> Well, this is for part of a school project so I'd like to do it myself. Thank you for the responses so far.

How could an HTML form test if a user inputs a correct answer?

You need some kind of scripting. Since this is for a school project, I don't want to say too much. But if you look around, you might be able to find other examples and see how they work.

---

### Post by pmasiar on 2008-04-02
[http://www.quibblo.com/](http://www.quibblo.com/) - make your own quiz, 

Result of 2 minutes of my superior Google-fu skilzors!

Edit: you did not mentioned you want to do it yourself! Time to learn some programming...

---

### Post by lnostdal on 2008-04-02
you're not asking the right question .. you should be asking "how do i send data from html forms to a server?"

here is how i'd do something like that using Hunchentoot and CL-WHO:
[http://paste.lisp.org/display/58498](http://paste.lisp.org/display/58498) (note: i haven't tested this code .. i just wrote it now in a hurry)

..here is a video, if you like that sort of thing - of someone using Hunchentoot to create a simple web application:
[http://www.lispcast.com/2007/10/lispcast-writing-a-simple-reddit-clone-in-common-lisp/](http://www.lispcast.com/2007/10/lispcast-writing-a-simple-reddit-clone-in-common-lisp/)

---

### Post by mssever on 2008-04-02
Based on what the OP said, Javascript might be an option, as well; the results don't have to be persistant.

---

### Post by TreeFinger on 2008-04-02
Maybe I should look into javascript. I am familiar with Java.

The thing is that this test is not required to be on the internet. Our group could print out a test sheet and hand it to the test takers. But I find this approach to be more oriented at my IT related major.

In the beginning I was thinking of creating a java applet to conduct the test, but I have not become familiar enough with GUI programming to accomplish this. I'll look into the javascript suggestion.

---

### Post by mssever on 2008-04-02
> **TreeFinger said:**
> Maybe I should look into javascript. I am familiar with Java.

Despite the name, Java and Javascript are completely different.

---

### Post by LaRoza on 2008-04-02
> **TreeFinger said:**
> Maybe I should look into javascript. I am familiar with Java.

The thing is that this test is not required to be on the internet. Our group could print out a test sheet and hand it to the test takers. But I find this approach to be more oriented at my IT related major.

In the beginning I was thinking of creating a java applet to conduct the test, but I have not become familiar enough with GUI programming to accomplish this. I'll look into the javascript suggestion.

See my site I linked to. It may help. (One could also use cookies and a few other techniques, my tests were just a study aid)

ECMAScript is easy to use, its syntax is C like (Java like, etc).

The quiz, with source for download: [http://laroza.freehostia.com/home/apps/airlines/index.php](http://laroza.freehostia.com/home/apps/airlines/index.php)

The client side script: [http://laroza.freehostia.com/home/apps/airlines/script/](http://laroza.freehostia.com/home/apps/airlines/script/)

---

