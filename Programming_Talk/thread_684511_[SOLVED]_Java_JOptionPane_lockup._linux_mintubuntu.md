---
title: "[SOLVED] Java JOptionPane lockup. linux mint/ubuntu"
date: 2008-02-01
forum: Programming Talk
---

### Post by The Squig on 2008-02-01
Hi all, I hope im posting this at the right place.

Im doing a beginners course in Java programming (and later on c++).

I wrote a couple of programs last night on my laptop which is running feisty, they all ran (eventually) without any problems.

Today I tried writing some simple programs on my desktop. It is running a fresh install of Linux mint which is basically Gutsy with more stuff pre installed.

Unfortunately Ive run into a rather big problem.

It seems whenever I use the method JOptions.Pane my Java program locks up. It compiles without any problems.

ex (Im writing this from scratch and im not able to compile the code atm so if there are any compiling errors here they are incidental, I know that the original code works since ive copied it and tested it on another machine.)

```

import javax.swing.*;

public class test{
   public static void main (String[] arg) {
      System.out.println("lalala"); // program runs fine at this point

      JOptionPane.showMessageDialog(null, "Testing"); //this is the stage of the lockup, pop up shows but then the program hangs.

System.out.println("This wont show"); //Any code written after the JOption.pane popup wont run.      

      System.exit(0);
   } 
} 


```


any ideas?

---

### Post by a9bejo on 2008-02-01
Hi Squig, 

Maybe you are running the java-gcj machine on your desktop?

Try running the command 

```

sudo update-alternatives --config java

```

and make sure you got the latest sdk from sun installed (java-6-sun).

---

### Post by lnostdal on 2008-02-01
compiles and runs fine without problems here .. could you provide a backtrace - or some crash message?

---

### Post by The Squig on 2008-02-02
[COLOR="Navy"]Update: I tried compiling the program in eclipse. Then I opened up the terminal and executed the program from the torminal. In this case "java hw". It worked fine so I dunno why it still crashes when using exlipse.[/COLOR]
Update1: This did seem to help when compiling it myself in the terminal. However when Using my favorite coding program "Eclipse" it still generates the same crash. I can only assume that Eclipse uses the GCJ compiler.. Any ideas on that one?


Ty you both for the replies. Im sorry it took me  all day to get back to the post but i got really busy later on during the day.

edit: This didnt solve the problem. But indicates that ecplipse isnt using the java compiler since it compiles fine manually.


```
sudo update-alternatives --config java:
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
*+        3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/bin/gij-4.1

```

I choose (1), recompiled my program and it didnt crash. So ty for your help.

---

### Post by Lord Illidan on 2008-02-02
Do you have eclipse-gcj installed?

Personally, I took the path of just downloading eclipse, putting it in its own folder, and running it from there. It's more up to date.

---

### Post by The Squig on 2008-04-28
I know this topic is a couple of months old now but since Ive found this problem happening on many machines I thought Id post my solution here incase it may help someone.
-----------------------------
First id like to make it clear that im a noob on this and not certain at all if my explanation on why this is happening is actually true or not. Its just a hypothesis of mine which sounds plausible in my ears. Pls dont hesitate to correct me. Either way the solution below did solve my problems.
-----------------------------


The problem as far as I can tell lies in that eclipse seems to use the gcj compiler instead of suns official one. For some reason all my programs which calls on JOption crashes whenever the program reaches that stage.

On my latest install of eclipse on ubuntu 8.04 it wouldn't even recognize Scanner() until i changed the compiler.

this is what I did to make it all work:

install suns java compiler. (ex from repo: sun-java5-jdk)

In eclipse go to 

window -> preferences -> JAVA -> installed JREs

Click on search and add the installation folder of the installed package.
for me it was located here:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/

---

### Post by kleb74 on 2008-06-02
Sorry for reviving this thread. I must say it helped me a lot. 
I had the same problem The Squig had. 
The solution The Squig posted on his las post worked for me, but now I have another problem, even more strange.

When I use javax.swing.JOptionPane to draw an I/O window, a blank window appears instead of the window I set. But what's more irritating is the fact that sometimes the window appear allright, but sometimes blank. This unwanted "blank" effect seems to be random.
In other words, the program behaves different from run to run.

Any ideas? 
Thanks.

---

### Post by xlinuks on 2008-06-02
For people to help you, you need to post the source code.

---

### Post by kleb74 on 2008-06-02
Ok, here it goes. It's just a test code, so it may have no sense.

```
package PackageNelson;
import javax.swing.JOptionPane;
public class Prueba {

	public static void main(String[] args) {
		String strMedidaEnt;
		float fltMedidaEnt;
		String strUnidadEnt;
		
		
		//String strMedidaSal;
		float fltMedidaSal = 0;
		String strUnidadSal;
		
		int intCodUnidadEnt = 0;
		int intCodUnidadSal = 0;
		
		String strNombreUnidadEnt = "";
		String strNombreUnidadSal = "";
		
		strUnidadEnt = JOptionPane.showInputDialog(null, "Ingrese  la unidad de medida de entrada: (m)etros - (y)ardas - (p)ulgadas - m(i)llas"); 
		strMedidaEnt = JOptionPane.showInputDialog(null, "Ingrese la medida de entrada"); 
		
		strUnidadSal = JOptionPane.showInputDialog(null, "Ingrese el código de la unidad de medida de salida: (m)etros - (y)ardas - (p)ulgadas - m(i)llas"); 
				
				
		JOptionPane.showMessageDialog("String");
		
		

	}

}
```

---

### Post by kleb74 on 2008-06-02
Here's how the problem looks:


[IMG]http://img229.imageshack.us/img229/92/pantallazosf9.png[/IMG]

---

### Post by kleb74 on 2008-06-02
The problem seems to be Eclipse's. I'm running the program from command line and it works without problems. 
I'm using Eclipse 3.2 Classic (it says "Eclipse Europa" on startup) on Ubuntu Hardy Heron x86-64.

---

### Post by Tarif Ezaz on 2008-07-20
I came into this link after googling about this same problem. And my problem is solved now :D

Thanks a9bejo!

---

### Post by Reiger on 2008-07-20
I guess it's that you installed Eclipse first and Sun's java (I take it you have at least one of the sun-java*-jdk pacakges installed?) second.

Eclipse is configured with a number of JRE's (and the default option is checked, which is used to execute your code with).

In this scenario only the GCJ one is found (which is installed out of the box with *buntu), so after installing one of Sun's, you must configure your Eclipse to use that one instead. (For obvious reasons GCJ isn't as good as those of Sun's.)

So here we go:
Window/Preferences 

Expand the Java item, find Installed JREs
Click Add

In the dialog box that pops up click browse; and navigate to your JRE of choice. Typically it will be located in /usr/share/libs/jvm/

Simply select the root directory & click open. You should now see a populated list of System Libraries as well as pre-entered name & other info in the dialog box.

Simply a matter of clicking OK, make sure that the JRE you want as default is in fact the default JRE by checking the checkbox in the list.

Result:
[[IMG]http://img29.picoodle.com/img/img29/4/7/20/t_snapshot1m_f1f0a2f.png[/IMG]](http://www.picoodle.com/view.php?img=/4/7/20/f_snapshot1m_f1f0a2f.png&srv=img29)

---

### Post by sanderd17 on 2009-01-06
Hi, I just want to add something to this explanation, 

when I configured the standard JRE in ubuntu with the following code

Code:
sudo update-alternatives --config java

I set it to the sun JRE but when I launched eclipse, there was a major problem: eclipse seemed not to find any JRE and it was constantly using so much CPU power I had to reset my computer.

To prevent this I have noticed that you need first change the JRE in eclipse (window -> preferences -> JAVA -> installed JREs), after that it's even not necessary to change the systems standard JRE (but maybe it's more correct)

I thank everyone who worked on this forum, it did really help me.

---

### Post by The Squig on 2009-01-06
Guys, i think we.re starting to get close to a bit of a repeat of whats already been said here. Please read through the thread again before you decide if its worth necroing this old post. Im very glad that this has seemed to help some people ^^.

> **The Squig said:**
> 
this is what I did to make it all work:

install suns java compiler. (ex from repo: sun-java5-jdk)

In eclipse go to 

window -> preferences -> JAVA -> installed JREs

Click on search and add the installation folder of the installed package.
for me it was located here:
/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/

---

### Post by ckmellin on 2009-04-16
I'm not sure this procedure solves the problem that kleb74 describes.   I am having the same issue.   The windows sometimes work and sometimes show up blank.   I am using JRE version java-6-sun-1.6.0.07 and still have the issue.  Any other suggestions??
thanks!

---

