---
title: "to use an ide or not to use one"
date: 2011-04-04
forum: Programming Talk
---

### Post by TinyXP on 2011-04-04
Hi,

I'm a php programmer and I usually develop on linux platforms using gedit. I've accomplished fairly complicated projects with gedit and little trouble at all. Never really needed anything beyond gedit with the syntax highlight, matching braces, support for file browsing etc.

I've never used an IDE extensively in my life, just because I've always believed that they tend to over complicate simple things. It makes the learning curve harder because you waste time trying to learn the IDE than doing any real coding.

But lately, I'm seeing all these jobs that expect you to be comfortable with an IDE like eclipse or netbeans. And now I might actually think about using an IDE.

What do you guys think about using IDE's ? Are they worth it or an overkill ?

---

### Post by Kirboosy on 2011-04-04
It all depends on the programmer.

I personally like using an IDE when I'm first learning the programming language. I find more of the tutorials use IDEs so I follow them by using the same IDE. IDEs help with finding errors too...

Once I get comfortable with the language though (like python) I will just open up a new file in gedit or vim and little scripts that way. 

IDEs do have a purpose and are very useful at times but they aren't always necessary. 


~Caboose

---

### Post by doas777 on 2011-04-04
an IDE is a tool, so like any tool, learning how to use it is critical. while it is a failing to not be able to perform many tasks manually (relying too much on tools) it is also an equal failing to not use them when they are called for. 

I knew a guy once, who believe all anyone needed was a copy of notepad and a jdk. he was probably a more skilled coder than I was, but i got all the praise from management because I got my stuff done on time, and could teach the junior developers how to use the tools. 

one of the things that throws many people when they first start working with large flagship IDEs, is that you have to figure out when to fight the defaults and when to take them. that is probably what is causing you to feel like they overcomplicated matters; usually means that you are fighting somthing you should just take as is.

---

### Post by Some Penguin on 2011-04-04
Depends on the scale and nature of the task.    I *could* write a Perl script to assist a refactoring by tracking down every class that imports or dynamically moved a moved class and to rewrite them, but actually doing so would be a lousy use of my time, and given that it wouldn't have access to the IDE's indices it'd also be slower than letting the IDE handle it.  It's a mechanical task, which is exactly what computers can be made expert in.

---

### Post by 102jon on 2011-04-04
For the most part, IDE's are good tools that can do a lot of things for you you wouldn't have to do manually with a text editor and terminal. You can configure the compiler, linker settings, etc., and IDE's typically have powerful debuggers that generally makes the developer's life easier. Having said that, I tend to go the text editor/terminal route (mostly because I usually develop in python), but also because it means I have control over everything. Sometimes an IDE can hide little things and you wouldn't have a clue. It's really up to the developer.

---

### Post by dazman19 on 2011-04-05
I started off using notepad/vi/gedit and kate. All text editors.

Once i learned the language I tried some IDE's but didnt like them.
One day i got a giant PHP project slammed in front of me, and i freaked. 

Thankfully netbeans for php was very forgiving and i learned fast.

When you only develop things from the ground up, you know all the ins and outs because you developed the entire package/app/website whatever then you dont really need an IDE. But once the project starts getting larger and a few people have worked on it, (either over the years or in conjunction) then using an IDE is very nice. Personally i prefer netbeans for PHP development, its quite cut down. I dont really like eclipse for PHP, but i Love it for java.

Netbeans will integrate with most SVN packages, and it colours the tabs different colors. (black = no change since last comit, blue = changed code, green= new file and doesnt exist in repos) 
and a exclamation mark for errors. The other advantage of the IDE is if you are working with larger files you can navigate easier and see an overview of what functions are in that file, and jump to the ones you want. 

All i know is that if i want to get the date function formatted for my region or something i just type Formatting:: ... and the IDE provides the list of static formatting functions i have overridden, once you start to rely on your IDE you will appreciate it more and start unlocking more power from it.

---

### Post by simeon87 on 2011-04-05
There's no need to look down upon an IDE as they can be very helpful with managing the project and refactoring your code automatically (as Eclipse can do).

For Python projects I just use gedit but for Java I do use Eclipse. It just depends, it certainly doesn't hurt to be familiar with an IDE but not every project needs an IDE.

For example, in Eclipse I use the built-in plugin for SVN but for Python I just use Mercurial from the command-line for versioning. It just depends on the project although I can imagine that companies like to use IDEs to speed up development time.

---

### Post by stchman on 2011-04-05
When I first started programming I used notepad on Windows and nano on *ix.  After I got used to using an IDE it is hard to go back to a text editor.

IDEs are good for keeping the project organized.

In Ubuntu if you're going to use just a text editor make it a good one like Geany.

---

### Post by Simian Man on 2011-04-05
I use an IDE for large projects when navigating the project as a whole is more important than navigating the individual files.  Also with large projects, the time used to setup the project is relatively insignificant.

For small projects, I just use a text editor.  I also think it's important to be comfortable with an editor and command line in case something goes wrong with your IDE setup, to allow others to compile your code easily and because many great languages have no good IDE support.

---

### Post by shawnhcorey on 2011-04-05
It depends on the language.  For the scripting languages, Perl, Python, Ruby, PHP, I find a text editor performs well but for compiled languages, C++, Java, I find an IDE is better.

---

### Post by cgroza on 2011-04-05
> **shawnhcorey said:**
> It depends on the language.  For the scripting languages, Perl, Python, Ruby, PHP, I find a text editor performs well but for compiled languages, C++, Java, I find an IDE is better.
+1, I just can't stand always switching between the editor and the command line. Errors are frequent and it is just simpler to hit compile and run.

---

### Post by shawnhcorey on 2011-04-05
> **cgroza said:**
> +1, I just can't stand always switching between the editor and the command line. Errors are frequent and it is just simpler to hit compile and run.

In that case, you'll l&#9829;ve emacs, the editor that thinks it's a kitchen sink.  :)

---

### Post by cgroza on 2011-04-05
> **shawnhcorey said:**
> In that case, you'll l&#9829;ve emacs, the editor that thinks it's a kitchen sink.  :)
Just googled a bit and it appears that thing is a whole OS! Stallman needed only the kernel after all, because he had EMACS!

---

### Post by LemursDontExist on 2011-04-05
I personally program without an IDE - often in gedit, though lately, I use Geany more than anything else.  For a small project, an IDE is actively counterproductive, and as the project gets larger there's not much an IDE can do that you can't do faster with the command line, shell scripting, and a good version control system (I use git).

Geany isn't a full featured IDE, but it does syntax highlighting and keeps track of variables and functions for me so I can quickly navigate a larger project.

For large projects with a complicated compilation process I write shell scripts.  This takes a little longer than doing the same thing in an IDE, but for these projects, the slightly higher one-time setup cost isn't a big deal, and I know exactly what everything is doing.  The time I save not being confused by the IDE doing clever things is well worth it!

---

