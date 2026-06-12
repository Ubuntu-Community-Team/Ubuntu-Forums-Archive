---
title: "BASH Why is my Echo command appending a special character to each new line?"
date: 2013-04-17
forum: Programming Talk
---

### Post by fr0s7y on 2013-04-17
This:

```
if [ "$answer" = "yes +" ] 
        then
                # Echo statement pulls the variables enters them into the filepath inside the $ADDRESSBOOK variable
                echo "$name, $firstname, $surname, $add1, $postcode, $num, $email" >>$ADDRESSBOOK
    elif [ "$answer" = "yes" ]
    then
                echo "$name, $firstname, $surname, $add1, $postcode, $num, $email" >>$ADDRESSBOOK
        exit=1

    elif [ "$answer" = "exit" ]
    then
        exit=1
        else
            # Give the user a message
            echo "$name NOT written to $ADDRESSBOOK"
        askEntry
        fi
```

Gives me in text file:

, Name, Surname, address etc.

^why is that comma there?

 :@ its been laughing at me all afternoon.

---

### Post by dargaud on 2013-04-17
> , Name, Surname, address etc.
Are you sure it's not giving you
, *FirstName*, Surname, etc ?
With an empty Name ?

---

### Post by fr0s7y on 2013-04-17
> **dargaud said:**
> Are you sure it's not giving you
, *FirstName*, Surname, etc ?
With an empty Name ?

Sorry I was in a rush, its giving me the right data was what I meant, its jus sticking an ',' at the start of every line.

I'm trying echo with -e and stuff, read the manual cant see anything giving me any hints there.

Read about printf too but I'm determined to make echo work now lol,

---

### Post by fr0s7y on 2013-04-17
> **dargaud said:**
> Are you sure it's not giving you
, *FirstName*, Surname, etc ?
With an empty Name ?

waaaaait, you're a genius, didnt even notice that $name variable, cheeky thing it is.

I think that should fix it, obviously the first variable will be empty. d'oh!

edit: Yeah that worked, thanks!!

---

