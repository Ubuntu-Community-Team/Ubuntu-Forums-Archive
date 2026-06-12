---
title: "OO Design question"
date: 2009-02-03
forum: Programming Talk
---

### Post by badperson on 2009-02-03
Hi,
I'm writing a simple app that will compare folders (2 or more) and report which files are more current, exist on one directory and not the other, etc. 

I have a "Job" class that will have a several methods. For example, I have a "process()" method which will launch all the other methods, such as "validateFolder()". I'm wondering if that method should be "validateFolder()" (singular), and I would validate all folders in a for loop from the process() method, or should it be "validateFolders()" (plural); and since an array of Folders is a field in the class, it could just loop through that array. 

The only downside to that is, in some future implementation if I wanted to use that code to validate just one folder...

thanks!
bp

---

### Post by mdurham on 2009-02-03
Why not make validateFolders() call validateFolder() for each folder?

---

### Post by badperson on 2009-02-03
Hi,

I thought of that...but it felt weird to me to have them both there; I suppose I could make the validateFolders() private...the idea being that if this application grew into an industry powerhouse to rival excel/photoshop/quicken...:lolflag: and then you had these two methods there it would be kind of ugly. 

But I suppose you're right, there isn't any reason not to set it up that way. 
thanks!
bp

---

### Post by maximinus_uk on 2009-02-03
IMHO: Always always make it work first. If it looks ugly you can always fix it later :D

---

### Post by nvteighen on 2009-02-03
What I fail to see is why you need OO in this. It sounds like a simple procedural task... (unless there's something else).

---

### Post by Sorivenul on 2009-02-03
> **nvteighen said:**
> What I fail to see is why you need OO in this. It sounds like a simple procedural task... (unless there's something else).
+1. Comparing the two folders and contents seems to be procedural. Generally I see something like: check if file1 is in folder1, check if file1 is in folder2, if in both compare dates and return more recent file1 and content differences. No need for object orientation.

---

