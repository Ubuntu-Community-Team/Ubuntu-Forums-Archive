---
title: "newb question about pauseing program"
date: 2008-05-07
forum: Programming Talk
---

### Post by iansane on 2008-05-07
Hi, I have been learning from a book that uses system("pause") at the end of simple programs to keep the window open so I can look at the output.

Actually I don't think that came from the book, but somewhere I picked it up and it works for windows.

The book mentions one time, the following line.

cin.ignore(std::cin.rdbuf()->in_avail() + 1)

It doesn't explain the code at all. Just says use it to wait for the user to press enter.

The problem is, for it to work in Ubuntu terminal, I had to put cin.get() after every cin in my program to clear the cin stream.

I think my problem might be, not understanding the cin stream, because I wrote a program a few days ago where when a user inputs a name with spaces in it, the program uses everything after the first space in the cin to answer all of the other cin's in the program. Like "my app" would cause the program to take "my" as the name and then put " ", "a", "p", and "p" into the next 4 cin's in the program as input.

Someone told me not to use cin, but to use std::getline() instead. If std::getline() is the correct way, then why does the book I'm using teach to use cin?

Anyway, the questions I have are, is there a simpler way than the cin.ignore()? And can someone give me a newb like explaination of what's going on in cin stream and how to clear it up? BTW, I tried cin.clear() and it had no affect on the app.

Also, that cin.ignore, seems to not require a "+ 1" at the end of it in windows, but it does in linux terminal. Is terminal counting an extra space or something?

Sorry so long and Thanks for any replies.:-)

---

### Post by Zugzwang on 2008-05-07
It seems to be that the "cin.ignore..." line removes everything from the input buffer up to that point. 

So for example if you write a program that takes 100 seconds to compute something and you just type some lines into the terminal while it computes, these lines are removed from the buffer.

cin.getline() on the other hand will not empty the buffer so if you press enter during the 100 seconds or so, that key-press will count.

As you already noticed, "cin.getline()" seems to be more portable. Unless you explicitly want to remove all the key strokes in the meantime, it might be wise to stick with that.

---

### Post by iansane on 2008-05-07
Thanks Zugzwang,

In the case of waiting for the user to press enter, the cin.ignore only works if I count up the number of cin's  before it in the program and then put "+ the number" at the end of the statement. Or if I put cin.get() after cin lines. Is there something like system("pause") for linux or do I have to use the cin.ignore line? 

Just a thought... Is there a simple one line code that actually counts the number of characters still in the buffer?

---

