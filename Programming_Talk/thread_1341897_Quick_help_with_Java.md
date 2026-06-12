---
title: "Quick help with Java"
date: 2009-11-30
forum: Programming Talk
---

### Post by blazemore on 2009-11-30
Hello Java people.
I am a bit stuck on what should be a very simple problem.
I have to ask the user for a first name, and if the string is empty, I'm to print an error and ask for the name again. My current code is as follows:
```
    void setFirstName() {
        System.out.print("Enter First Name: ");
        firstname = UserInput.readString();
        if firstname.equals("") {
            System.out.println("ERROR, No first name was entered");
            
        }
    } // end setFirstName
```Obviously that just carries on if the string is empty, which isn't ideal.

Maybe some kind of do while loop? (While firstname is empty, do this...)

I'd appreciate your help.
nb yes this is an assignment, but it's a small part of a much larger program, most of which I can do; it's just this one stupid bit.

---

### Post by jespdj on 2009-11-30
Learn about 'while' loops here: [The while and do-while Statements](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/while.html)

Note: The code you posted does not compile because you forgot some parentheses on the if-statement. It should be:
```
if (firstname.equals("")) {
```

---

### Post by blazemore on 2009-11-30
> **jespdj said:**
> Learn about 'while' loops here: [The while and do-while Statements]("http://java.sun.com/docs/books/tutorial/java/nutsandbolts/while.html")

Note: The code you posted does not compile because you forgot some parentheses on the if-statement. It should be:
```
if (firstname.equals("")) {
```

Ugh yes. I previously learned Python, and its beautiful, clean code (almost like pseudocode) makes it VERY difficult for me to get my head round Java syntax, especially having to declare types for methods.

---

### Post by Zugzwang on 2009-11-30
Apparently, you want something like a "do ... while" loop:

```

 void setFirstName() {
        do {
           System.out.print("Enter First Name: ");
           firstname = UserInput.readString();
           if (firstname.equals("")) {
               System.out.println("ERROR, No first name was entered");
           }
        } while (firstname.equals(""));
    } // end setFirstName

```

---

### Post by blazemore on 2009-11-30
Thanks, that's excellent.
I don't know if you noticed but our university wrote us an excellent UserInput class. I can put a link up if anyone wants it, it saves a lot of code, if you haven't already written one yourself.

---

