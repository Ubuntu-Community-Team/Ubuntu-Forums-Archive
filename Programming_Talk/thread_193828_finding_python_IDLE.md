---
title: "finding python IDLE"
date: 2006-06-10
forum: Programming Talk
---

### Post by Micik on 2006-06-10
Hello
I have installed ubuntu linux two days ago and before that I had Mandrake linux 10.1. I noticed that Mandrake had in "start menu"Development-->IDLE so I could start this pythons IDE. On the other hand, after I had installed ubuntu, python is also installed (I have checked with $python -V) but I cannot find IDLE anywhere. How Can I check if IDLE is installed at all and where to find it? I tried to searh for available packages on ubuntu cd but could not find IDLE and I have installed all that had something with python in its name.
Thanks

---

### Post by punchy on 2006-06-10
Hi Micik,

You can install the IDLE interface, by using 'synaptic', or with the command 

   sudo apt-get install idle

It may be that you should activate the repositories on the www.
I am not sure whether idle would be on the ubuntu install cd.

Check for 'repositories' in the forums. 

Or better yet..
Use the 'automatix' script and simply keep the repositories which it suggests. (search for automatix)

Let me know whether it worked out.
Punchy

---

### Post by pelago on 2006-06-10
You need to install the package called 'idle'.

---

### Post by Micik on 2006-06-10
Unfortunately the computer on which linux is installed is not connected to the internet. Can you post link where I can download idle and the somehow install it. Is it possible. IDLE is not on ubuntu installation cd, I have checked. Since it was on Mandrake cd, can I somehow use Mandrake installation cd to install IDLE?

---

### Post by punchy on 2006-06-10
Hmm.. if you're not on the net then thats a big drawback in general. I'm not sure whether the 'idle' package is on the install cd and i don't have one handy right now. I dont have much experience how to handle a ubuntu (or linux in general) install without the power of the www. 

Maybe somebody else ?

---

### Post by Micik on 2006-06-10
Hmm, I tried to execute apt -get install... command but I got error message apt not found. Is this because of lack of internet connection?
On Mandrake, IDLE is automatically installed, but here is not. When I run synaptic package manager and choose Search it cannot finde anything with name IDLE
Thanks for your effort anyway.

I have just downloaded idle-python 2.4.1.2 but couldn't installed because it depends pn 2.4 Tk also 2.4.1-2, but Tk depends on numrous other files so I think it's not possible to do it this way. I assume maybe each of these files depends on some other files and so on.
Is there any precompiled IDLE? Any ideas where I can find that?

---

### Post by Micik on 2006-06-10
Hello again, on python.org I have found information that IDLE is coming with each linux distribution. I continue to search and found info that python is usually in usr/lib directory. I used Places->Search for Files and choose to search in filesystem and search engine found nothing. Now I chose to search in /usr/lib/python2.4 directly and it found idle.py and idle.pyw. Now in terminal I typed
python idle.pyw and IDLE shell opened.
Now two questions:
1. Why search engine cannot find idle.py if I choose to search in filesystem (it is supposed to check all directories)?
2. Is there any way to make shortcut to idle.pyw on my Desktop to start it faster?

---

### Post by DirtDawg on 2006-06-10
Go here:
   [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/) (assuming you're using Dapper)

Go to the Python Section:
   [http://packages.ubuntu.com/dapper/python/](http://packages.ubuntu.com/dapper/python/)

Find and select "Idle":
   [http://packages.ubuntu.com/dapper/python/idle](http://packages.ubuntu.com/dapper/python/idle)

Download it.

In the terminal, go to directory which the package is stored:
   " cd /home/packages/idle.deb " [or whatever]

Install:
   " sudo dpkg -i idle.deb "

TaDaaa!

Of course, I'm assuming your attempt to reinstall Python had no gnarly side-effects.

Good Luck

---

### Post by Micik on 2006-06-11
Well, like I said, I found IDLE in /usr/lib/python2.4/idlelib and I can execute it by typing
python idle.pyw
Now I wonder is it possible to create some kind of shortcut on Desktop so when I double click that shortcut IDLE starts?
Thanks very valueable links.

---

