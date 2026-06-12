---
title: "gnome-terminal, xterm, overwrites and extraneous characters"
date: 2015-04-12
forum: New to Ubuntu
---

### Post by Malik_Rumi on 2015-04-12
I have Ubuntu 14.04 Unity on a Dell XPS 1820 amd64. I was going through the official Postgres tutorial when I started getting what I considered strange results:

1) the terminal started overwriting the command line instead of going to a new line:
her.datSELECT weather.city, weather.temp_lo, weather.temp_hi, weather.prcp, weat 

2) extraneous data from the command line starting showing up in my results: (note the duplicate WHERE clause in the first table and the extra semicolon and 'weather.city' inside the second table)
mydb=# SELECT * FROM weather, cities WHERE city = name;
WHERE city =name;
     city      | temp_lo | temp_hi | prcp |    date    | location  
---------------+---------+---------+------+------------+-----------
 San Francisco |      46 |      50 | 0.25 | 1994-11-27 | (-194,53)
 San Francisco |      43 |      57 |    0 | 1994-11-29 | (-194,53)
(2 rows)
                                                                               ;
     city      | temp_lo | temp_hi | prcp |    date    | location  weather.city; 
---------------+---------+---------+------+------------+-----------
 San Francisco |      46 |      50 | 0.25 | 1994-11-27 | (-194,53)
 San Francisco |      43 |      57 |    0 | 1994-11-29 | (-194,53)
(2 rows)

3) I started getting a long series of tildes at the end of my results, followed by END and no command prompt: 

                                   List of databases
   Name    |   Owner    | Encoding |   Collate   |    Ctype    |   Access privileges   
-----------+------------+----------+-------------+-------------+-----------------------
 baillee   | malikarumi | UTF8     | en_US.UTF-8 | en_US.UTF-8 | 
 greenblue | malikarumi | UTF8     | en_US.UTF-8 | en_US.UTF-8 | 
 mydb      | malikarumi | UTF8     | en_US.UTF-8 | en_US.UTF-8 | 
 postgres  | postgres   | UTF8     | en_US.UTF-8 | en_US.UTF-8 | 
 template0 | postgres   | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =c/postgres          +
           |            |          |             |             | postgres=CTc/postgres
 template1 | postgres   | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =c/postgres          +
           |            |          |             |             | postgres=CTc/postgres
(6 rows)

~
~
~
~
(END)

4) I was able to get back to a command prompt by entering \q, but when I did that my previous results vanished from the screen:

greenblue-# \list
greenblue-# 

I posted about this to the posgres list last night and the first guy said:

"What it looks like is that psql has the wrong idea about what sort of
terminal you're using (ie, which command language your terminal
window understands).  With no more info than that you're on Ubuntu,
it's hard to be more specific than that.  But try "echo $TERM" at the
shell command line to see what psql is being told about this, and then
see if that squares with the documentation about your terminal program."

So I did:

malikarumi@Tetouan2:~$ echo $TERM
xterm

Now that I knew there was such a thing as xterm, I googled it and learned that the default on Ubuntu is supposed to be gnome-desktop, (or at least it was until recently).

The second guy to respond on the postgres list said:

"Also if you have binary data that is output to the terminal as a result of one of your queries it might have messed up your terminal in which case you could choose one of the reset options from the menu to see if it helps."

I did reset but the problems resurfaced shortly thereafter. I don't know if any of this is binary data or not.

So, with that extensive background,

A) What is the default terminal on Unity 14.04 supposed to be?
B) If it is still gnome-terminal, how did I get xterm?
C) In Dash, if I start typing in 'ter...', a Terminal icon pops up right away, and that's what I have been using. When I right click on it in Dash, it says it is gnome-terminal. But if I go all the way and enter 'terminal' in Dash, I see there is uterm and xterm also.
D) If my default is gnome, why does echo $TERM give me xterm?
E) I am totally confused because coming from Windows, I had no idea there were so many different flavors of terminal. Are gnome-terminal, or xterm, the same as, or compatible with, BASH?
F) I opened both xterm and uterm from Dash. They look like each other, but the default window is smaller than the terminal I've been using and so is the font. Both echo xterm.
G) Most importantly, how do I fix all this so my terminal (whatever it is) works smoothly and consistently with all my programs? Thanks.

---

### Post by egeezer on 2015-04-12
Do you have Synaptic Package Manager installed?  If so, you can get the Xfce terminal, which is highly configurable and much more readable than xterm.  You might even be able to install it from the Software Center. 

(I use the Xfce desktop rather than Unity, so I don't know what is easily available in Unity)

---

### Post by Holger_Gehrke on 2015-04-12
> **Malik_Rumi said:**
> A) What is the default terminal on Unity 14.04 supposed to be?

It's gnome-terminal.
> **Malik_Rumi said:**
> 
B) If it is still gnome-terminal, how did I get xterm?

Because they are compatible and the authors didn't want to confuse programs that check this variable. They all understand the codes meant for a VT100 or VT220 / VT320  (which were devices with a monitor and keyboard that connected to the serial port of a computer; you could send specific codes in your output to do things like move the cursor, clear the screen and so on; ancient history, but relevant since it's all still done as if that was what you have. That's why it's called a terminal **emulator**)
> **Malik_Rumi said:**
> 
C) In Dash, if I start typing in 'ter...', a Terminal icon pops up right away, and that's what I have been using. When I right click on it in Dash, it says it is gnome-terminal. But if I go all the way and enter 'terminal' in Dash, I see there is uterm and xterm also.

Which you use is largely a matter of taste, unless you need the emulation of a Tektronix graphics terminal. Then you don't have any choice but to use xterm which - in addtion to VT100 emulation - also has a mode for this type of terminal.
> **Malik_Rumi said:**
> 
D) If my default is gnome, why does echo $TERM give me xterm?

see B)
> **Malik_Rumi said:**
> 
E) I am totally confused because coming from Windows, I had no idea there were so many different flavors of terminal. Are gnome-terminal, or xterm, the same as, or compatible with, BASH?

The terminals just take your input and hand it to bash and takes the bash's (or whatever other program your running) output and shows it to you. 
> **Malik_Rumi said:**
> 
F) I opened both xterm and uterm from Dash. They look like each other, but the default window is smaller than the terminal I've been using and so is the font. Both echo xterm.

uxterm is xterm with **U**nicode support. In both you can hold control and the right mouse button to get a menu in which you can choose the font-size.
> **Malik_Rumi said:**
> 
G) Most importantly, how do I fix all this so my terminal (whatever it is) works smoothly and consistently with all my programs? Thanks.
gnome-terminal should have an entry "Terminal" with an option "Reset" in the menu. If the terminal starts misbehaving because of unwanted control characters in the output you can use that to get back to a useful state. In xterm the menu you get by holding ctrl and the middle mouse button has a similar option.

---

### Post by Malik_Rumi on 2015-04-12
Holger, thank you so much for a detailed response that actually answered my questions. I write my questions that way a lot to separate out the issues, but most of the time it gets ignored, so again, thank you for that. I do have one more question, however:

The Wikipedia article [http://en.wikipedia.org/wiki/GNOME_Terminal#cite_note-8](http://en.wikipedia.org/wiki/GNOME_Terminal#cite_note-8) makes it seem like what Ubuntu includes is actually a fork of gnome terminal. If so, where do I go for help in the future, besides posting here?

---

### Post by Holger_Gehrke on 2015-04-13
> **Malik_Rumi said:**
> 
The Wikipedia article [http://en.wikipedia.org/wiki/GNOME_Terminal#cite_note-8](http://en.wikipedia.org/wiki/GNOME_Terminal#cite_note-8) makes it seem like what Ubuntu includes is actually a fork of gnome terminal. If so, where do I go for help in the future, besides posting here?

No, it's not a fork; the distributors just put this one capability (transparent window background), which the gnome developers removed, back in by putting in code from an old version that had it. Gnome is rather well known for removing features like this or the split panel view in nautilus.

---

