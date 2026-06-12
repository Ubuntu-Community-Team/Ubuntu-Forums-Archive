---
title: "Is there a java program that checks indentation?"
date: 2009-09-14
forum: Programming Talk
---

### Post by todlangweilig on 2009-09-14
I am taking a Computer Science class. For our first lab project, we were to write a simple program that adds two numbers. Our instructor wants us to use a unix system for coding. This involves SSHing into the unix box, coding, and then SCPing the file back to the windows desktop so the source can be uploaded to Blackboard for grading. Somewhere between vim, scp and windows my file ended up like this:

[PHP]
<snip>
        {
            <snip>
            System.out.print("Enter an integer: ");
            // Prompt user for second number 
-->   int num2 = kbd.nextInt();
-->   // store second number
            System.out.println(num1+num2);
            //print out sum of num1 and num2
        }
<more snipping>
[/PHP]

Which in turn lead to this:
> 
Grade: 9/10 
Lacks Proper Indentation. 


leaving me feeling like :mad:

Which brings me to my question, is there a java program that will check the indention of another java program? I prefer java since this needs to run in windows and on a machine that I presumably cannot install software on.

---

### Post by myrtle1908 on 2009-09-14
What you want is a code "beautifier" or "formatter".  There are many.  Some web-based, some not.  Here is one you can download: [http://www.tiobe.com/index.php/content/products/jacobe/Jacobe.html](http://www.tiobe.com/index.php/content/products/jacobe/Jacobe.html)

---

### Post by todlangweilig on 2009-09-14
Thanks, this seems like it will do nicely if I can get it to work in [Allman style]("http://en.wikipedia.org/wiki/Indent_style#Allman_style_.28bsd_in_Emacs.29"). My professor wants the code to be in this style.

---

