---
title: "frustration"
date: 2009-05-19
forum: Programming Talk
---

### Post by infinities on 2009-05-19
I'm new to *nix, and I just installed ubuntu on my laptop so that I can do some programming. 

So far I've gotten eclipse installed, but I'm a little annoyed by the IDE. I'm not a professional, and I never find the need to actually create projects. Maybe I should be getting in that habit? Let me know. Anyway, I'm working on something, and I don't know how you're supposed to run individual files. I'm always forced to create some sort of project which later I can't even find. IT'S ANNOYING.

I also installed java 1.6(I THINK) and I haven't been able to correctly update it from 1.5 on eclipse. The amount of configuration just overwhelms me. 

I've tried BlueJ and JEdit, and I can't even find the options for compiling the files. Why does this have to be difficult?  Does anyone know of a simple IDE that can compile java?

---

### Post by cl333r on 2009-05-19
The most user friendly ide for Java is NetBeans:

[http://www.netbeans.org/downloads/](http://www.netbeans.org/downloads/)

download NetBeans from the link above since the version from the repositories has been reported as glitchy by some users.

And I agree with you, Eclipse su* when it comes to ease of use.

If you have several Java JDKs installed choose the one you need to be the default:
sudo update-alternatives --config java

PS: a project to an IDE is what an object is to Java - you can't get along without it, if you think you can't get along with projects you most likely won't get along with IDEs and thus the only option is to use hand-made makefile scripts and text editors and alike.

---

### Post by infinities on 2009-05-19
I already downloaded netbeans, but being that I'm a newbie at *nix, I don't know how you're supposed to install the .sh

I was probably going to look it up now.


also, what is the difference between OpenJDK and the normal JDK?

---

### Post by Joeb454 on 2009-05-19
To install it (lets assume the .sh file is on your desktop).

Open a terminal, and run ```
sudo ~/Desktop/netbeans-file.sh
``` Of course, you'll need to use the correct file name ;)

---

### Post by cl333r on 2009-05-19
Don't use the OpenJDK, it is what Sun Microsystems managed to open source, but since some graphics (and other) stuff could not be open sourced it has been replaced by lower quality code which causes glitches, so don't use it for now.
By the way, to install the "normal" JDK:
sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin

You can also run the .sh file by just double-clicking it, but first you have to make it "executable", to do it right-click it->Properties->"Permissions" tab and make sure "Allow executing file as program" is checked.

---

### Post by monkeyking on 2009-05-19
I also hate this "project approach" that these gui ide forces down on me.

I would recommand just using an editor and compile by commmandline. Like a real man :)

---

### Post by cl333r on 2009-05-19
Since you're new you'll have many questions, you can use my ICQ to ask (as long as I'm online), if I know I'll help.

---

### Post by infinities on 2009-05-19
> **cl333r said:**
> Since you're new you'll have many questions, you can use my ICQ to ask (as long as I'm online), if I know I'll help.

hah, thanks for the offer

i've never used ICQ either, i'll try figuring it out

but first, how can you compile/ run java files from the terminal?

---

### Post by cl333r on 2009-05-19
Say App.java is in your home directory:

The file App.java:
```

public class App {
	public static void main(String[] args) {
		System.out.println( "hello world" );
	}
}

```
Open the terminal, to compile:
javac App.java

and now to run the App.class file:
java App

The terminal can be found at Applications->Accessories->Terminal

---

### Post by cl333r on 2009-05-19
How to clear the terminal:
In windows you used to issue the "cls" command to clear the terminal window.
Here you can use the Ctrl+L to "go down and keep the text up one screen" or type "tput reset" to actually clear the window and all the text. As you can see "tput reset" is a closer equivalent to the windows "cls".

---

### Post by infinities on 2009-05-19
well, I tried netbeans and I think that it checks for different things during compilation

It gave me a compilation error regarding an array, though I've ran the program fine before

it's wierd, but i do agree that it's more user friendly than eclipse


also, cl333r:
is ICQ like an instant messanging program, or what?

---

### Post by cl333r on 2009-05-19
My ICQ number is 212375036, yes, it's an instant messaging program. Afaik you have to register on their site and get a number like mine. After you register online [https://www.icq.com/register/](https://www.icq.com/register/) you can use pidgin (Applications->Internet->Pidgin) to login - it supports ICQ.

If you can't solve that problem with the array you need to post more details including the error message (along with the relevant code) here.
It's 4:25 AM here so I might go to sleep.

---

