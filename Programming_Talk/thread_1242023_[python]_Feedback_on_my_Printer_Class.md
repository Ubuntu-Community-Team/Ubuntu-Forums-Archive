---
title: "[python] Feedback on my Printer Class"
date: 2009-08-16
forum: Programming Talk
---

### Post by Pyro.699 on 2009-08-16
Hello All,

I would like some help with anything that i can do to improve my code located in the file below.

I recently learned how to use threads in Python, and as such have been required to create an easy way to work with output for threads. I need help with redundant code, and possibly things i can add to make it run better.

Here is a brief explanation of each function and what it does.

> 
_up()_ - Move the tab level up one
_down()_ - Move the tab level down one
_set(x)_ - Set the current tab level to *x*
_ get()_ - Get the current tab level
_save(i)_ - Save the current tab level to backup index *i*
_rest(i)_ - Restore backup index *i* as the current tab level
_rint(string, nl, tb, st)_ - This is the main print function. It will print the current *string* (aslong as *st* == **True**), it will calculate the tabs and preppend them (aslong as *tb* == **True**), it will also add a new line to the end of the string (aslong as *nl* == **True**)
_notice(string, nl, timeout)_ - This will stop all output for *timeout* seconds giving time for the user to read the message as defined by *string*. If *nl* == **True** it will add a blank line after the message
_unpause()_ - Used by the *notice* function, just unpauses the script
_write_list()_ - Used by the *rint* function this will ensure that the messages are alway printed in sequence
In case your wondering why i called the main print function "rint" this started as a testing function and wasn't planning to be this big, but i used the code below
```

p = Printer()
p.rint("My String")

```Meaning i would only have to add a period to all of my **print**'s

Please let me know what you think and provide any information that you can. I'm new to class' so i know there are somethings i can improve on.

Thanks
~Cody Woolaver

---

