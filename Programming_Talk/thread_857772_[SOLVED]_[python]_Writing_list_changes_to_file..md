---
title: "[SOLVED] [python] Writing list changes to file."
date: 2008-07-12
forum: Programming Talk
---

### Post by -grubby on 2008-07-12
I can't seem to get this, how would I write list items to file? Say for example, I have an existing file, and I want to keep adding stuff to it. How would I do this?

---

### Post by loell on 2008-07-12
isn't that just appending?

```
write_filehandle = file(filname,"a")

write_filehandle.writelines([yourlist])


```

---

### Post by -grubby on 2008-07-12
Yes it is just appending. However I was thinking of taking a different approach, because I need to remove items too

---

### Post by loell on 2008-07-12
how about two filehandles? for reading and writing,
then read the file by .readlines on to another list
manipulate the list then write it back?

---

### Post by -grubby on 2008-07-12
> **loell said:**
> how about two filehandles? for reading and writing,
then read the file by .readlines on to another list
manipulate the list then write it back?

Wait what? I'm pretty sure what you're basically saying is, make 2 files, one with the actual list and one with a different list.. and then I kind of get lost

---

### Post by ghostdog74 on 2008-07-12
> **nathangrubb said:**
> I can't seem to get this, how would I write list items to file? Say for example, I have an existing file, and I want to keep adding stuff to it. How would I do this?

its best to show examples of what you mean. However, by pure guessing
1) when you run the script on the command line, use > operator
2) o.write("".join(list))
3) Take a look at the pickle, shelve module for more information

---

### Post by loell on 2008-07-12
> **nathangrubb said:**
> Wait what? I'm pretty sure what you're basically saying is, make 2 files, one with the actual list and one with a different list.. and then I kind of get lost

no, i'm saying two filehandles pointing to the same file one for "a" and the other for "w". or is there some unified filehandle in python for reading and writing?

```

write_filehandle = file(filname,"w")
read_filehanlde = file(filename)
thelist = read_filehandle.readlines()

#manipulate  **thelist** by comparing, popping, or removing items
#then write it back

write_filehandle.writelines(thelist)


```

err, so this is not just simple append. :D

---

### Post by -grubby on 2008-07-12
OK guys, nevermind, I figured it out. It was too easy. If you care to see my solution :

[php]
# Note that "file"'s entire value is "list", so I basically overwrite the whole file
def write_new_list_value_to_file(new_list_value) :
    file = ("filename", "w")
    list.append(new_list_value)
    file.write(list)
def remove_list_value_from_file(removed_value) :
    file = ("filename", "w")
    list.remove(removed_value)
    file.write(list)
[/php]

---

### Post by ghostdog74 on 2008-07-12
either that, or try pickle/shelve.

---

### Post by boblemur on 2008-07-13
why do you need the list synced with the file???

shouldn't u write to the file when you close your program.... 

sorry if im missing the point...

---

### Post by -grubby on 2008-07-13
> **boblemur said:**
> why do you need the list synced with the file???

shouldn't u write to the file when you close your program.... 

sorry if im missing the point...

No, this method will be used in a web application. You can not 'close' a web app ;)

---

### Post by boblemur on 2008-07-13
ok, still it just seems like alot of io for no good reason... and io is very very slow

---

### Post by -grubby on 2008-07-13
> **boblemur said:**
> ok, still it just seems like alot of io for no good reason... and io is very very slow

I don't plan to be writing things that are unordinarily large

---

### Post by boblemur on 2008-07-13
hmmm ok, but still if it used oftern /update alot... you could concider some kind of threshold system... ie it updates after X number of changes to the list... this way you are not rewriting the file very time... and also you file will still stay upto date...

---

