---
title: "Opening Python Interpreter with Customised Terminal Profile"
date: 2009-05-27
forum: Programming Talk
---

### Post by navneeth on 2009-05-27
*This is not a programming question per se, but I though it was suited here more than anywhere else on the board.*

When we open the Python interpreter (from Applications->Programming->Python(v2.6)), a window similar to the Gnome-terminal appears with the same profile, but with the interpreter showing. Well, I created another profile so that I won't confuse the regular terminal for the interpreter or vice-versa. But what I want to know is how to make the interpreter open with the custom profile I created, rather than the default?

Any help will be appreciated.

---

### Post by unutbu on 2009-05-27
Make a custom launcher (or menu item) which this command:
```
gnome-terminal --window-with-profile=PROFILENAME
```

---

### Post by navneeth on 2009-05-28
> **unutbu said:**
> Make a custom launcher (or menu item) which this command:
```
gnome-terminal --window-with-profile=PROFILENAME
```

Thanks for your reply, but all that command will do is open a terminal with the Shell, whereas what I want is the Python interpreter. I should neither be typing python (as in the command) at the shell, nor should I be right-clicking to change the profile. 

Applications->Programming->Python and it should **automatically open the interpreter with the custom profile**.

---

### Post by unutbu on 2009-05-28
In gnome-terminal, click Edit>Profile. 
Select the name  of your "python" profile -- what I call the PROFILENAME below.
Click the "Edit" button. 
Click the "Title and Command" tab.
Enable to "Run a custom command instead of my shell" checkbox.
Type in /usr/bin/python as the "Custom command".
Click close, etc.
Then run```

gnome-terminal --window-with-profile=PROFILENAME
```

I assume you know how to make the command into a gnome panel menu item. If not, just ask.

---

### Post by navneeth on 2009-05-28
> **unutbu said:**
> In gnome-terminal, click Edit>Profile. 
Select the name  of your "python" profile -- what I call the PROFILENAME below.
Click the "Edit" button. 
Click the "Title and Command" tab.
Enable to "Run a custom command instead of my shell" checkbox.
Type in /usr/bin/python as the "Custom command".
Click close, etc.
Then run```

gnome-terminal --window-with-profile=PROFILENAME
```

I assume you know how to make the command into a gnome panel menu item. If not, just ask.

Wonderful! That is exactly what I needed. Thank you. (I edited the existing menu item for Python.)

---

