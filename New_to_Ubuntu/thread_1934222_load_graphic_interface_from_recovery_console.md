---
title: "load graphic interface from recovery console ?"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by karlhutt on 2012-03-01
hello!
i'm new with ubuntu. 

i'm having a problem: 
i use ubuntu 11.04, 
i changed the option on the ACCESS screen, where you can choose from loading classic ubuntu, or the nicer ubuntu, or recovery console. 
i chose recovery console just to see what happens 

(i was having trouble loading the nicer ubunutu with effects, but i usually use the classic look, so it was not really a problem). 

now my computer turns on directly to the recovery console, and i CANNOT open the grapic mode! 
i turn on the computer, and what i get is the ubuntu logo on the background and a terminal on the top left corner.. 

i tried startx and it tells me 
'fatal IO error 11 (Resource temporarily unavailable) on X server'

i tried alt-shift-f7, and nothing happens..

how can i go back to my graphic mode?

thanks.

---

### Post by Krytarik on 2012-03-01
> **karlhutt said:**
> i turn on the computer, and what i get is the ubuntu logo on the background and a terminal on the top left corner..
Problem: You have auto-login enabled.

> **karlhutt said:**
> how can i go back to my graphic mode?
Solution: Simply enter "exit" into that terminal to get to the login screen. :P

Regards.

---

### Post by karlhutt on 2012-03-01
yes. i do that, but then on the LOGIN SCREEN i do log in, and it goes back there. 
no graphic interface.

---

### Post by Krytarik on 2012-03-01
> **karlhutt said:**
> yes. i do that, but then on the LOGIN SCREEN i do log in, and it goes back there.
Then you have additionally disabled the password query on login - very bad idea! ;-)

To re-enable it, open the file "/etc/group" with the CLI text editor "nano", and remove your user from the "nopasswdlogin" group:
```
sudo nano /etc/group
```
Addition: Although now I'm wondering how you were able to change the session option in the first place, if that's true; must have been a *very* bad timing then. :P

---

### Post by karlhutt on 2012-03-02
THANKS!!!!
it worked!!!
thank you SO very much!

---

