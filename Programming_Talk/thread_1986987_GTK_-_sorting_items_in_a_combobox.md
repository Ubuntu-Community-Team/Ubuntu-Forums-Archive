---
title: "GTK - sorting items in a combobox"
date: 2012-05-25
forum: Programming Talk
---

### Post by anewguy on 2012-05-25
Using [this]("http://www.lemoda.net/pango/list-fonts/index.html") link I was able to come up with a combobox of the font family names as I wanted.  However, this list is not sorted in alphabetical order.  I looked in the docs and on line and found something called a gtklistbox.  It appears it can have a sorted type.  Can someone tell me if this is sorted, so if I load the font family names into a listbox it will show as sorted?  Also, can someone point me to a simple tutorial with sample code for using a gtklistbox in C?  The Devhelp docs can be a little cryptic for someone like me.  I need to know how to define it, add text rows to it, set a default text row and know when a text row has been selected.  All of the docs show "iteration" as some form of data type and I would have thought I could just use an integer to access a row but apparently not.  So, I'm new AND confused!

Thanks in advance!

Dave ;)

---

### Post by roelforg on 2012-05-26
Instead of inserting directly in the combobox, put the fonts in an array.
Sort the array and insert the sorted array in the combobox.

---

### Post by StephenF on 2012-05-26
You want one of these I think.

[http://developer.gnome.org/pygtk/2.24/class-gtktreemodelsort.html](http://developer.gnome.org/pygtk/2.24/class-gtktreemodelsort.html)


Apply it to the liststore then apply the treemodelsort to the combobox widget instead using the liststore directly. As you append items (fonts?) to the liststore they will appear as sorted in the combobox.

You will need to write a simple compare function in order for the treemodelsort to do its magic.

---

### Post by anewguy on 2012-05-26
Didn't see the replies here until I got it working - and I did it as you suggested, roelforg.  I didn't know that to make an array of strings dynamic I had to use char **arrayname to define it - I don't even know what exactly that entails.  I think it means a pointer to a pointer, but I'm lost as to how the strings are actually stored and how the pointers are setup.  I did the malloc's as needed and got it loaded, then used qsort to sort it.  Don't get me wrong - I don't know what the heck I'm doing - I just found samples on the net that I was able to modify to make it work.

The end result is:

I load the available font names from Pango into a string array, then sort the array (Pango doesn't return them in any particular order that I can see), then load the combobox.  Now the users get a "normal" font name selection box.  I'll be adding the bold and italic check boxes, as well as font size and height.  That will give what is needed and make it easy for me to patch into the generated CSS file.


Thanks for the replies and help!!

Dave ;)

---

### Post by roelforg on 2012-05-27
> **anewguy said:**
> Didn't see the replies here until I got it working - and I did it as you suggested, roelforg.  I didn't know that to make an array of strings dynamic I had to use char **arrayname to define it - I don't even know what exactly that entails.  I think it means a pointer to a pointer, but I'm lost as to how the strings are actually stored and how the pointers are setup.  I did the malloc's as needed and got it loaded, then used qsort to sort it.  Don't get me wrong - I don't know what the heck I'm doing - I just found samples on the net that I was able to modify to make it work.



[http://cplusplus.com/doc/tutorial/pointers/](http://cplusplus.com/doc/tutorial/pointers/)
I know it's a c++ site, but they explain it very good.
I could go on for quite some time about how you (should/shouldn't) use memory and how to (and not to) (de)allocate it. But then again, i've made my own toy os kernel and several emulators, so i know the ins and outs of this stuff (and that's more than most programmers would ever need to know).

> **anewguy said:**
> 

The end result is:

I load the available font names from Pango into a string array, then sort the array (Pango doesn't return them in any particular order that I can see), then load the combobox.  Now the users get a "normal" font name selection box.  I'll be adding the bold and italic check boxes, as well as font size and height.  That will give what is needed and make it easy for me to patch into the generated CSS file.


Thanks for the replies and help!!

Dave ;)

Good luck

---

