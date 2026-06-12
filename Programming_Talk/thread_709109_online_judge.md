---
title: "online judge"
date: 2008-02-27
forum: Programming Talk
---

### Post by sys_alpha on 2008-02-27
hi ,
  I want to build an online C code judge for which i want to use java php and mysql .
  But i donot find any related topic on the web. Does anybody have a brief idea for this or any link/book(s) that gives the details ?

---

### Post by a9bejo on 2008-02-27
What does a "online C code judge" do? Is this meant to be a [code analysis tool](http://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis) like lint or checkstyle ?

---

### Post by sys_alpha on 2008-02-27
a c online judge basically gets the c code through net and gives the result too. This is useful in organising programming contest.

---

### Post by sys_alpha on 2008-02-27
does any body have  any idea /link about building a code online judge using java+php+mysql?

A code online judge simply takes code and displays the result over web.?

---

### Post by negge on 2008-02-27
What exactly do you mean? What kind of code should it "judge"?

---

### Post by PmDematagoda on 2008-02-27
This thread has been moved to the Programming Talk section.

---

### Post by pedro_orange on 2008-02-27
Why would you want to do this?

Surely it would make more sense to just compile and test it on your machine, than uploading it to a web server to compile and run.

Unless I'm missing the point here....

---

### Post by sys_alpha on 2008-02-27
actually i want to organise local programming contest based on intranet. for that i want the user to be able to see the results and to submit their code within a deadline.
 If you find any help for this using java+php+mysql please help me.

---

### Post by pedro_orange on 2008-02-27
I suppose you could write a web service that is called after the source is uploaded. It would compile the application, run it and pipe (say shell) output to a text file, which could be shown to the person who submitted the code.

---

### Post by pmasiar on 2008-02-27
> **sys_alpha said:**
>  If you find any help for this using java+php+mysql please help me.

Not sure why you selected java if you have php+mysql.

What is your other experience in programming? Any web apps?

---

