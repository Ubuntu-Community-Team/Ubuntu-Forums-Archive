---
title: "user input and SPE"
date: 2007-08-08
forum: Programming Talk
---

### Post by BDNiner on 2007-08-08
I am trying to use SPE since IDLE has not window decorations on my computer for some reason. But when i run a program that requires the user to input some text the program just hangs. Where do i input the text to make the loop continue?

Maybe i am doing something wrong. i open the program and it appears in the source window. then i press F9 to run it. I get what the program is supposed to display in the output window, but nothing in the terminal window. I cannot enter text into the output window, so where do i enter the text?

Also what happened to the manual? has it been moved to a different site?

---

### Post by pmasiar on 2007-08-08
running code in terminal using F9 (and shift-F9 without arguments) works fine for me (Tools >> Run in terminal).

```

n = raw_input("test?")
print n
raw_input() # stop before terminal closes



```

Any simplified source code? What we are doing differently

---

### Post by BDNiner on 2007-08-08
I tried the code that you posted and it is the same thing. When i press F9 it displays "test?" in the output tab but nothing else happens. Where do i enter the text?? Oh and how do you display the code window in your post?

---

### Post by pmasiar on 2007-08-08
That terminal *is* the window you are looking for. Just enter some text after the "test?" prompt, and press enter.

use [ code ] .... [ / code ] tags for code :-)

---

### Post by BDNiner on 2007-08-08
Ok, that is the window that i am unable to enter anything into. At first i thought i was doing something but now it seems like it is broken.

This is the code i am trying to run.

```
def print_options():
    print "Options:"
    print " 'p' print options"
    print " 'c' convert from celsius"
    print " 'f' convert from fahrenheit"
    print " 'q' quit the program"

def celsius_to_fahrenheit(c_temp):
    return 9.0/5.0*c_temp+32

def fahrenheit_to_celsius(f_temp):
    return (f_temp - 32.0)*5.0/9.0

choice = "p"
while choice != "q":
    if choice == "c":
        temp = input("Celsius temperature:")
        print "Fahrenheit:",celsius_to_fahrenheit(temp)
    elif choice == "f":
        temp = input("Fahrenheit temperature:")
        print "Celsius:",fahrenheit_to_celsius(temp)
    elif choice != "q":
        print_options()
    choice = raw_input("option:")

```

---

### Post by pmasiar on 2007-08-08
that code works perfectly fine for me. :confused:

1) After F9 dialog box opens asking for arguments, i just click "run" (with no runtime arguments".
2) New (terminal) window opens, where program printed menu, and asks for "option": let's enter 'c' and press enter.
3) Program asks for celsius temp, I enter 0 and press enter. Program prints "Fahrenheit: 32" and asks new option.

What happens when you run it?

BTW you want to use "choice = raw_input("option:").lower()" so if anyone enters 'C' it will work like 'c'.

---

### Post by BDNiner on 2007-08-08
Oh ok, the terminal window is not opening up for me. It just sits there, the longest i waited was for about 20 mins this morning. This is on my computer at work. My computer at home is also doing the same thing. The program works perfectly in IDLE.

I installed SPE using add/remove. Is there a better way to install it?

---

### Post by BDNiner on 2007-08-08
I have figured it out. If i use Shift + F9 then the 2nd terminal window will open. I don't know why it wont work when i just use F9?? Thank you for your help. This was driving me crazy since IDLE doesn't have any window decorations when i use compiz fusion (but everything else does, even the dialogue boxes from IDLE do)

Thank you for your help.

---

### Post by pmasiar on 2007-08-08
If you run program using F9, dialog window should show. Looks like it did not  show under compiz. You may want to report it to Stani

---

### Post by BDNiner on 2007-08-08
How do i submit a bug report?? And what should i put in it?

---

