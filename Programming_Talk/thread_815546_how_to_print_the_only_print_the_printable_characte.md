---
title: "how to print the only print the printable characters in JAVA"
date: 2008-06-01
forum: Programming Talk
---

### Post by fyplinux on 2008-06-01
Hi, I was trying to read a file and print it out in JAVA, for some characters, it is just wired, like, "&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;&#65453;".

why these chars cannot be displayed properly? How to solve this problem?

If it cannot be solved easily, How can I just print the printable chars?

Many thanks.

---

### Post by mike_g on 2008-06-01
I don't know, maybe you could load it as a string an use a regex to replace all non-alphanumeric, non-punctuation characters? I guess there must be an easier way tho.

---

### Post by NormR2 on 2008-06-01
Could you give a little more info on your problem?
What was in the file? Was it a text file with ASCII characters? Cnn you read and display it in a text editor?
What java class did you use to read the file? 
What statement/method did you use to print out what your read?

---

### Post by fyplinux on 2008-06-02
> **NormR2 said:**
> Could you give a little more info on your problem?
What was in the file? Was it a text file with ASCII characters? Cnn you read and display it in a text editor?
What java class did you use to read the file? 
What statement/method did you use to print out what your read?

It is the index.dat file, which is the browser history of IE in Windows. I heard that it could be read, so I tried to read out it by the classes of File, FileReader of Java.

A typical string read by emacs of the file:
       * "^@^@\357\276\255\336:200805272008052"*

the readable information is currently printed by such a statement:

		  ```
  if (Character.isLetterOrDigit(ch) || (ch >= 32 && ch <= 126)) {	
//do the print work
}		


```

---

### Post by NormR2 on 2008-06-03
Why would you expect to be able to read the contents of a program's data file and understand it (ie have it appear as ASCII text)?
Most likely a lot of it is binary(raw bytes).

The doc for FileReader says:
> 
FileReader is meant for reading streams of characters. For reading streams of raw bytes, consider using a FileInputStream.

---

