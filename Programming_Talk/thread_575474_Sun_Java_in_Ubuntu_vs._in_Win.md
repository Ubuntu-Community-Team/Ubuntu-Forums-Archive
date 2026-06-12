---
title: "Sun Java in Ubuntu vs. in Win"
date: 2007-10-14
forum: Programming Talk
---

### Post by freetonik on 2007-10-14
Hello friends!

I'm taking Java Programming course in university. Now we using Sun Java 1.6 and JCreator LE for Windows.

Since I decided to switch to Ubuntu, I have no other questions but Java. So, my question is: will I have problems using Sun Java under Ubuntu? I mean problems with compatibility, because tutors are checking our assignments under Windows.. If I take .java file from my windows-friend and try to compile it under Ubuntu - will I have success? 

Thank you in forward

---

### Post by Ramses de Norre on 2007-10-14
Yes, that will go perfectly fine, I've distributed a lot of applications written and tested on linux to users using windows and haven't encountered any problems yet.

BTW: JCreator is a real pain to develop with, and as it doesn't have a linux port neither I suggest you to use eclipse on both linux and windows, you'll be twice as efficient with it ;)

---

### Post by Lord Illidan on 2007-10-14
Either Eclipse or Netbeans as well. I'm also doing a java course at Uni, btw :P

---

### Post by jespdj on 2007-10-14
> **freetonik said:**
> Since I decided to switch to Ubuntu, I have no other questions but Java. So, my question is: will I have problems using Sun Java under Ubuntu? I mean problems with compatibility, because tutors are checking our assignments under Windows.. If I take .java file from my windows-friend and try to compile it under Ubuntu - will I have success?
One of the main strengths of Java is that it is platform-independent; Java programs run on all OS'es for which there's a Java runtime environment available. You don't even need to recompile, Java class files compiled on Windows will run fine on Linux.

---

### Post by Lord Illidan on 2007-10-14
Though I guess that things can get hairy if you start mixing libraries which can't be found on Linux, right?

---

### Post by CptPicard on 2007-10-14
Where would you find libraries that aren't crossplatform, as they will be in Java too?

You use native code very, very rarely in Java...

---

### Post by Lord Illidan on 2007-10-14
> **CptPicard said:**
> Where would you find libraries that aren't crossplatform, as they will be in Java too?

You use native code very, very rarely in Java...

Like a GUI application using GTK java for example? I am just asking questions here, forgive me for my display of ignorance. So far my only java knowledge is related to terminal and some java applets.

---

### Post by motang on 2007-10-14
> **freetonik said:**
> Hello friends!

I'm taking Java Programming course in university. Now we using Sun Java 1.6 and JCreator LE for Windows.

Since I decided to switch to Ubuntu, I have no other questions but Java. So, my question is: will I have problems using Sun Java under Ubuntu? I mean problems with compatibility, because tutors are checking our assignments under Windows.. If I take .java file from my windows-friend and try to compile it under Ubuntu - will I have success? 

Thank you in forward
Well you will be fine as when I did a Java course(s) at my college I was able to move from Fedore to Windows XP to Ubuntu back to Fedore just fine.  Also we use Eclipse which is very good in my opinion.  I have never used JCreator LE so I can't say much about that.  Hope this helps you out.

---

### Post by CptPicard on 2007-10-14
> **Lord Illidan said:**
> Like a GUI application using GTK java for example? I am just asking questions here, forgive me for my display of ignorance.

Hmm. I'm not familiar with how Java bindings to native-code windowing toolkits work, but I would assume that if they are available for both platforms, you can also call them in that case.

However I do think that binding to any native code libraries pretty much defeats the primary purpose of using Java in the first place -- the language itself is not that wonderful that I'd use it if the crossplatform nature was not there.

If you're writing a Java app, use Java libraries, that way you avoid platform-specific dependencies. In the GUI case, use Swing, or SWT (which is more native than Swing but that's nitpicking..)

---

### Post by tenmillionmilesaway on 2007-10-14
naturally you do need to make sure that you are using the same java version

---

### Post by Mickeysofine1972 on 2007-10-14
The only problem I have come across is that Draggable <div>'s are slower under linux when using scriptaculous but thats just a performance th issue, they do work.

Also, that only JavaScript but I thought I might just mention it XD

Mike

---

### Post by CptPicard on 2007-10-14
> **Mickeysofine1972 said:**
> Also, that only JavaScript but I thought I might just mention it XD


Despite the name (which Javascript got because of marketing reasons), Javascript, Java and their implementations in your system are completely unrelated...

---

### Post by freetonik on 2007-10-14
Thank you, everyone, for the answers!

---

### Post by Mickeysofine1972 on 2007-10-14
> **CptPicard said:**
> Despite the name (which Javascript got because of marketing reasons), Javascript, Java and their implementations in your system are completely unrelated...

Mr Picard I am not a merry man ! XD

Mike

---

### Post by freetonik on 2007-10-14
> **Ramses de Norre said:**
> Yes, that will go perfectly fine, I've distributed a lot of applications written and tested on linux to users using windows and haven't encountered any problems yet.

BTW: JCreator is a real pain to develop with, and as it doesn't have a linux port neither I suggest you to use eclipse on both linux and windows, you'll be twice as efficient with it ;)

Well, it is, for big projects. But my course called "Introduction to Object-Oriented programming" For making two classes and four loops JCreator is pretty good. Isn't it silly to use Eclipse to calculate square root in Java? :confused:

---

