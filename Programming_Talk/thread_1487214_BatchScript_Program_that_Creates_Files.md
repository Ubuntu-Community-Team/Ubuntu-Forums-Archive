---
title: "Batch/Script Program that Creates Files"
date: 2010-05-18
forum: Programming Talk
---

### Post by Hosmion on 2010-05-18
Hello everyone!  I was on a website looking up a couple things and I decided I could use some help real quick.  My mom asked me if she would make me a program to keep records of hours and stuff.  But, I am making it in a batch (or as I was informed, a "script" file) file.  I have the coding and everything like cd and md, but I don't know how to make a batch program actually create a text document.  Anyone help?

Or, if there is another programming language that will create text documents please specify it in your comment.

---

### Post by Sub101 on 2010-05-18
Text files are quite simple in a script.

Simply;

```
echo "Hello world" >> file_name
```

or

```
echo $my_var >> file_name
```

Note the double arrow means append. A single ">" would delete the current text.

---

### Post by Hosmion on 2010-05-18
EDIT::  Solved the question I asked here myself :).

But I have another, how do I make this text document automatically open up with NotePad or some other text editor?

---

### Post by Sub101 on 2010-05-18
Can I just confirm that we are talking about a program that runs from the terminal?

So long as that is the case then yes the text hello world would be written inside a file and saved to your current directory. This is the directory you are in at the time of running.

If you go to the terminal and type the command as above then you will create a text file in the current directory. (which would normally be your home directory)

---

### Post by Hosmion on 2010-05-18
Yes, this is being run in Terminal.  

I have hopefully 1 more question:  Is there a way I can make it make the text document made into a specific area?  Like...  A random file in the C:/ drive.

---

### Post by Sub101 on 2010-05-18
> **Hosmion said:**
> Yes, this is being run in Terminal.  

I have hopefully 1 more question:  Is there a way I can make it make the text document made into a specific area?  Like...  A random file in the C:/ drive.

Sorry are we not running this on Ubuntu/Linux?

I do not know if the above suggestion works in Windows. It may, but it may not.

To write to a specific file and folder on Ubuntu you can use;

```
echo "Hello world" >> /home/username/myfolder/filename
```

---

