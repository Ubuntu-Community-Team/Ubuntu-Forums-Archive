---
title: "Java game, how to distribute?"
date: 2009-12-18
forum: Programming Talk
---

### Post by chs1010 on 2009-12-18
Hey all,

ive been making a game for my university course using java (in netbeans) and i want to be able to send it to others to test out for me without getting netbeans themselves, however the way my game is programmed means it doesnt have a main class :S (unless i got the wrong meaning of main class, in which case could someone clear that up for me?), and from what ive been told and read about, everything gets put into the dist folder that netbeans makes but the thing in there doesnt run the game

ok im a little unsure of how im wording all this, i just wanna be able to give out like a simple file that lets people run my game, i know java doesnt use .exe's but something similar if someone understands that

thanks in advance for any replies :KS

---

### Post by baizon on 2009-12-18
I'm not sure that this is what you are searching.
> How to make a JAVA application - executable JAR archive
Links:
[http://www.captain.at/programming/java/executable-java-application.php]("http://www.captain.at/programming/java/executable-java-application.php")
[http://www.excelsior-usa.com/articles/java-to-exe.html]("http://www.excelsior-usa.com/articles/java-to-exe.html")

---

### Post by Penguin Guy on 2009-12-18
> **chs1010 said:**
> the way my game is programmed means it doesnt have a main class :S (unless i got the wrong meaning of main class, in which case could someone clear that up for me?)

Okay, I'm a newbie programmer, and never used Java before, so sorry if I've got the wrong end of the stick.

Can't you just stick your existing code into a class?

**Pseudocode:**
```

[I]<your>
<main>
<code>[/I]

```

```

class main (parameters)
{
    [I]<your>
    <main>
    <code>[/I]
}

```

---

### Post by dvlchd3 on 2009-12-18
A main class in Java simply means a class containing the following method:

```

public static void main(String[] args) {}

```

Every Java program must have this, otherwise, it wouldn't run...Typically Java applications would look like this

```

public class myCoolGui {

public myCoolGui() {
// construct the frame, etc

}

public static void main(String[] args) {
// Run the program on the Event dispatching thread.
[INDENT]SwingUtilities.invokeLater(new Runnable() {[/INDENT]
[INDENT][INDENT]public void run() {[/INDENT][/INDENT]
[INDENT][INDENT][INDENT]new myCoolGui();[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT]}[/INDENT][/INDENT]
[INDENT]});[/INDENT]
}

```

It is highly recommended that you run your GUI application on the event dispatching thread.

If you wrote a simple text-based Java program, the above is completely irrelevant, and just ignore it.

Therefore, you do not have to have a "Main Class" meaning a class named "MainClass" or a class just containing the main method, however, you MUST have some main method in some class within your project.  This is unless you are wrapping your program in some other sort of executable that knows what to do, however, I'm assuming this is not what you are doing.  Netbeans would not have allowed you to run the Java program unless the main method existed someplace.

With all that being said, to make it redistributable, you can make, as suggested above, an executable JAR file.  Executable JARs are supported from Java 1.2 or 1.3 (not sure which) on.  Also, the end-users will need to have Java installed on their computers.  If you experience issues, it is likely due to the fact that you used newer Java features then the end-user's JRE supports.  If you developed with 1.5, its a safe bet they will need 1.5 installed on their computer.

Didn't mean to write that much, but nonetheless, hope it answers your question fully.

---

### Post by Finalfantasykid on 2009-12-18
A Runnable Jar is the easiest way IMO.  Though I have never used Netbeans, I am sure there is a way to export your project as a Runnable Jar, that way you don't need to worry about the Manifest file or anything like that.

---

### Post by LKjell on 2009-12-18
Not possible to let them have the source code and test it from there?

---

### Post by chs1010 on 2009-12-19
thanks for all the replies

from what my tutor told me, we cant use a main class in a game, it runs in a big game loop which is a loop containing all the aspects of the games and such and a main class does someting wrong with it, and about it needing one or it wouldnt work, hey it works for me :P, i just wanna make it like an executable, so other people can play it with ease

---

### Post by sheazar on 2009-12-20
Executable JAR is definatly the way to go. You could make one in netbeans by pressing shift + F11. It places it in the dist folder. If your still unable to run it (try it in the terminal using java -jar yourprogram) it might be that you have another working directory than if you run it directly from netbeans. This might mess up things like finding images.

By the way, I think you and your tutor missunderstood each other. You always have a "main class" (class with public static void main(String[] arg)) otherwise you definatly wouldn't be able to run your app. (It might be a really short method though :P )

---

### Post by chs1010 on 2009-12-20
my game shouldnt run then (it does though), i looked through all the files and it doesnt have a main class rofl, it does extend the japplet and jpanel though, dunno if that has anything to do with it? :/

---

### Post by Some Penguin on 2009-12-20
That's because the main() is in the NetBeans framework that will invoke your specially-written code.  (That is, your code must have some method which NetBeans either assumes, can find, or be configured to use).

This does mean that your only options are 

(1) assume that your recipients already have NetBeans,
(2) tell them to download it separately, or
(3) distribute the NetBeans framework as well (which may or may not be legal -- some legally free-to-download material includes licensing that prohibits unauthorized redistribution by third parties, so check the NetBeans license)
(4) re-implement every part of NetBeans that you depend upon and distribute that (obviously, probably not what you want to do, and again, possibly legal issues involved)

---

### Post by chs1010 on 2009-12-21
ok thanks for all the help guys but ive found i can make it run in a html file and through the browser lol

thanks again ^_^

---

### Post by fiddler616 on 2009-12-21
Guys, let's not jump to conclusions about the main(String[] args) method.

Consider this:

```

public class Game extends Applet
{
    public void init()
    {
        ...
    }
    
    public void paint(Graphics g)
    //etcetera
}
```

In fact, considering the level of the class, I'd be willing to bet the game is an applet, and doesn't have fancy graphics and whatnot.

OP: If you know for a fact that the game is an applet, just make a folder with all the .class files and an HTML file that runs the applet*, distribute that folder, and tell people to double click on the HTML file. If it's not an applet, disregard this post.

*I would totally give you the code, but I can't remember it, am too lazy to look it up, and anyway--independent research is good for the soul.

---

