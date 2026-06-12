---
title: "java one interface leading to another"
date: 2011-09-08
forum: Programming Talk
---

### Post by vineeth v s on 2011-09-08
):P

hi,

can anyone tell me how i can connect two interfaces,
that is, for example first interface ask for username and password 
if it is wrong jst an error messege....., but if it is correct how can i lead the user to another interface...??
hope u understand what i mean...............

v

---

### Post by Zugzwang on 2011-09-08
> **vineeth v s said:**
> )
can anyone tell me how i can connect two interfaces,
that is, for example first interface ask for username and password 
if it is wrong jst an error messege....., but if it is correct how can i lead the user to another interface...??


Assuming that you want a non-browser GUI application:

Create a JFrame with two JPanels in it. Call setVisible(false) on the second one, make the first one contain your fields in which you ask for username/password, and make the second one contain the "other interface". When the correct password is entered, call setVisible(true) on the second panel and setVisible(false) on the first one. The content of the JFrame will be "replaced" by the other panel.

Depending on what you want to do, keep in mind that it is easy to decompile and modify a Java application.

Avoid the word "interface" withtout the word "User" if you are writing a post about Java, as people's first guess with the interface you know from deriving classes in Java.

---

### Post by vineeth v s on 2011-09-08
thnx that will help.......:popcorn:

but it will require the codes for both userinterfaces in the same program.....na??

for example if i have a GUI program for user.. and another for login..
 how can i connect these two GUIs?? 

sorry if it is a stupid one... :D

---

### Post by ofnuts on 2011-09-08
> **vineeth v s said:**
> thnx that will help.......:popcorn:

but it will require the codes for both userinterfaces in the same program.....na??

for example if i have a GUI program for user.. and another for login..
 how can i connect these two GUIs?? 

sorry if it is a stupid one... :DThey can't be different "programs", otherwise one would just start the "application" part directly... Typically for login you would create your main window but not make it visible, start the login dialog as modal window, and if everything OK when the dialog returns, show the main application window (otherwise reshow the modal login dialog).

---

### Post by vineeth v s on 2011-09-08
oh..!! i understand... ;)....

---

