---
title: "Compiling Netbeans stuff JUST with javac"
date: 2010-12-09
forum: Programming Talk
---

### Post by blazemore on 2010-12-09
I have an assignment for a Java program which I did in Netbeans, so it set up the actionlisteners and stuff for me.

However, the coursework description says it needs to be compiled "just using javac"

How can I make sure all the packages imported by Netbeans are available so my lecturer can compile it himself?

---

### Post by blazemore on 2010-12-09
For example, a specific error is:
package org.jdesktop.application does not exist

Is there a way in netbeans to export the project code and all dependencies?

---

### Post by PaulM1985 on 2010-12-09
If there was/is (I don't know) an export I guess it would be defeating the purpose of your assignment.

Try removing all the import statements that are giving you compiler issues and then try to replace all of the classes that use those statements with classes that come as standard.

Paul

---

### Post by blazemore on 2010-12-09
The assignment is on UI design, not programming.

---

### Post by blazemore on 2010-12-09
If it helps, the libraries being used are the following:
appframework-1.0.3.jar
swing-worker-1.1.jar

both of which are available on my system
How can I get them into my source tree so javac won't fail?

---

### Post by PaulM1985 on 2010-12-09
If the assignment is on UI design, surely your teacher wants you to be manually defining positions for controls and manually defining your layouts/layout managers etc.

Its quite easy to drag and drop.  Its harder to manually program a ui, which sounds like what your teacher wants you to do.

Have a look into swing and see if you can actually do this task using just gedit and the javac and java commands to compile and run.

Paul

---

### Post by KdotJ on 2010-12-09
I agree with Paul, you should really just try and do it yourself manually. Netbeans isn't really going to teach you anything. I mean, you can look at the code and see what it's doing, but you're much better off typing it out yourself because this is how you learn. It will be good to lean about layout managers that java provide as well the components it has to offer. As Paul said it's harder to do it this way, but it will serve you much better in the long run. 

However, as for your problem, have you tried taking out the "package <name>;"
statement at the top of the source file?

---

