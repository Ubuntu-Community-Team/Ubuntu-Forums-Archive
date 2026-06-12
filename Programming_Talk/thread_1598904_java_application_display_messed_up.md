---
title: "java application display messed up"
date: 2010-10-17
forum: Programming Talk
---

### Post by kanishkdudeja on 2010-10-17
hey guys..

i created an application that uses java and connects to mysql..

it anaylses a query, performs it on a mysql database and returns back the result..

i created in when i ws using windows..

it worked perfectly then..

but it ubuntu its display has messed up..

i have attached the java file..

please compile it..run it and tell me why its display has gone messy

---

### Post by kanishkdudeja on 2010-10-17
please help sumbody. i have to show its working in the college as it is a part of a project or else il hav to reinstall windows again..:(

---

### Post by spjackson on 2010-10-17
> **kanishkdudeja said:**
> 
please compile it..run it and tell me why its display has gone messy

> **kanishkdudeja said:**
> please help sumbody. i have to show its working in the college as it is a part of a project or else il hav to reinstall windows again..:(
There are smart ways to ask for help with your homework. [http://www.catb.org/esr/faqs/smart-questions.html](http://www.catb.org/esr/faqs/smart-questions.html) Be specific about what is going wrong, and reduce your code to a minimal amount that shows the problem.

I looked at your code: 840 lines without any indentation, and  for example, ~40 lines are occupied by 2 statements. I compiled it and ran it  (knowing that the database query would fail). I saw a window with controls in  it. I don't know what it is supposed to look like or where the display "has gone messy".

You might get help here, but I personally think that what you are expecting volunteers to do for you is unreasonable. Sorry I can't help you. Good luck.

[I now notice that you have posted this same question in General Help. [http://ubuntuforums.org/showthread.php?t=1598901](http://ubuntuforums.org/showthread.php?t=1598901) ] It could indeed be the jdk you are using, as gandaran suggests there, but you haven't given us much to go on.

---

### Post by Finalfantasykid on 2010-10-17
I don't know why it doesn't look right with the default look and feel.  But I ran it with this command:

```
java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel  query

```And using that look and feel made this look the way they should.  You can change the look and feel in your code as well:

```

        try {
            // Set System L&F
            UIManager.setLookAndFeel(
                UIManager.getSystemLookAndFeelClassName());
        } 
        catch (UnsupportedLookAndFeelException e) {
           // handle exception
        }
        catch (ClassNotFoundException e) {
           // handle exception
        }
        catch (InstantiationException e) {
           // handle exception
        }
        catch (IllegalAccessException e) {
           // handle exception
        }

```

---

### Post by kanishkdudeja on 2010-10-18
@finalfantasykid..

yes it is working fine with this command..thanks a lot..but i want to know why doesnt it look fine with jus java query ?

---

### Post by kanishkdudeja on 2010-10-18
@spjackson..

im sorry but i dont have d screenshots of what it should look like because i dont have windows installed nemore so i cannot compile it in windows and show u how it should look like..

wen i said display has gone messy i meant that controls were overlapping each other and i couldnt click on buttons..

btw i compiled it using sun's java

---

