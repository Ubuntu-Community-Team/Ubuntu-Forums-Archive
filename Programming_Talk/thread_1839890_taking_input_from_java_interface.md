---
title: "taking input from java interface"
date: 2011-09-06
forum: Programming Talk
---

### Post by vineeth v s on 2011-09-06
hi,

  i am now working on a project which uses java to make am applet interface
 and take inputs and updates a database.Leave the database part,can anyone tell me 
how to take inputs from java interface, both string and integer?? or it is enough top point me some
tutorials or links ....
it ll be a great help,

thanks in advance,....:popcorn:

---

### Post by PaulM1985 on 2011-09-06
Could you be a little clearer on what you are struggling with?  Have you created a user interface already?

To make it very simple, you could just have two JTextFields on your applet, one for the String, one for the Integer as well as a button that would say "Submit" or something similar.

In the code for the Submit button, you would get the text from the JTextField for the String and for the integer, you would get the text from the JTextField and then use Integer.parseInt(integerString) to parse it to an integer.  (Once you have done this you can add safety code to prevent people putting silly inputs).

Paul

---

### Post by vineeth v s on 2011-09-06
ooppss.. sory for my english... :D

yes, your answer will help...

but all i was trying to do is to take a string from JText field and 
store it to a variable in the program . is it possible?? is their some function for it??

---

### Post by ofnuts on 2011-09-06
> **PaulM1985 said:**
> Could you be a little clearer on what you are struggling with?  Have you created a user interface already?

To make it very simple, you could just have two JTextFields on your applet, one for the String, one for the Integer as well as a button that would say "Submit" or something similar.

In the code for the Submit button, you would get the text from the JTextField for the String and for the integer, you would get the text from the JTextField and then use Integer.parseInt(integerString) to parse it to an integer.  (Once you have done this you can add safety code to prevent people putting silly inputs).

PaulIt would be better to use a NumberFormat to parse the number. Does some of the sanity checks, and will handle necessary cultural variations (1000,000 and 1000.000 aren't the same across the Atlantic...)

---

### Post by myrtle1908 on 2011-09-06
> **vineeth v s said:**
> but all i was trying to do is to take a string from JText field and 
store it to a variable in the program . is it possible?? is their some function for it??

JTextField has a getText() method.

[http://download.oracle.com/javase/tutorial/uiswing/components/textfield.html](http://download.oracle.com/javase/tutorial/uiswing/components/textfield.html)

---

### Post by cgroza on 2011-09-06
> **myrtle1908 said:**
> JTextField has a getText() method.

[http://download.oracle.com/javase/tutorial/uiswing/components/textfield.html](http://download.oracle.com/javase/tutorial/uiswing/components/textfield.html)
Use that combined with Int.parseInt() and you get the result you want.

---

### Post by vineeth v s on 2011-09-07
oh!! man.. this is exactly wat i want.... thnku guyss....:popcorn::guitar:

---

