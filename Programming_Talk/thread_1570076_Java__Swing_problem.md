---
title: "Java / Swing problem"
date: 2010-09-07
forum: Programming Talk
---

### Post by matty-guy on 2010-09-07
I've started doing my computing in 6th form (college) and it went okay, but once I got home I wanted to try the stuff I'd learnt. I installed all the Java packages I was told I'd need, installed NetBeans and Geany to see if much differed and gave it a go. 

The code we were given was something like this 
```
import javax.Swing.JOptionPane;
public class Numbers {
	public static void main (String args [])
{
int blah;
blah= 66;

JOptionPane.showMessageDialog (null, "My number is" + blah);

System.exit (0);
}
}

```

The problem I have is that in NetBeans, I get an error next to the first like and 'JOptionPane...' line, saying ' package javax.Swing does not exist'. Geany won't compile my program, I assume for the same reason. The code up there worked at school, unless I made a silly error copying it over. Anyone know what's up or how to fix it? I've tried this on my 9.04 Crunchbang and the new Linux Mint.

---

### Post by KdotJ on 2010-09-07
Your problem is a simple mistake in your import, "Swing" should have a lowercase s

```
import javax.swing.JOptionPane;
```

---

### Post by matty-guy on 2010-09-07
:oops: Thanks! I'm gonna have a tough time with the case sensitivity.

---

### Post by KdotJ on 2010-09-07
> **matty-guy said:**
> :oops: Thanks! I'm gonna have a tough time with the case sensitivity.

lol you'll get used to it. I'm sure your course will explain naming conventions, e.g. for variables and methods.

---

### Post by firefly2442 on 2010-09-07
You may want to try the Eclipse IDE.  If you are missing an "import" it's nice about telling you.

---

### Post by KdotJ on 2010-09-07
Netbeans has the same feature too, it's nice. If, for example the OP didn't import anything, but called the JOptionPane.showMessageDialog method in their code, netbeans will automatically add the needed import to the source file

---

