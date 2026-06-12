---
title: "Gambas/ubuntu help"
date: 2010-01-12
forum: Programming Talk
---

### Post by ve3tru on 2010-01-12
I'm new to programming and Gambas
I'm trying to write a simple one button program  that can open terminal and do things there. I can get it to open terminal but thats all; can someone help me plz...
Here's what I have.

' Gambas class file

PUBLIC SUB _new()

END

PUBLIC SUB Form_Open()

END

PUBLIC SUB Button1_Click()

EXEC ["/usr/bin/gnome-terminal"]


END

---

### Post by kalaharix on 2010-01-12
Hi,

erm... Why don't you just open terminal from the Ubuntu menu? Opening it by shelling from Gambas won't make it any different. 

There is a Gambas scripting language but documentation is minimal and I think it is fair to say it is still 'under development'. If you want to program from the terminal I would recommend Python. Gambas scores when programming a graphical interface (i.e. nothing to do with terminal).

If you want to do simple arithmetic calculations in Gambas, do a forum search on gambas and look at my reply in '[kde] gambas trouble' author coletsou.

rgds

---

### Post by ve3tru on 2010-01-14
"Why don't you just open terminal from the Ubuntu menu?"
The whole point of my program is so you don't have to open the terminal.
I wrote a script that id like to execute under Gambas, or write it into gambas some how.
Tnx

---

### Post by lavinog on 2010-01-15
If you are wanting to execute shell statements within a shell, you usually don't do it by executing a shell.

---

### Post by kalaharix on 2010-01-15
Hi

I am still unsure where you are trying to get to.
> 
I wrote a script....


If you are talking about a shell script then just make it executable and shell from Gambas to it.

e.g. if your script (saved as scrpt) is:
TERM=linux
export TERM
echo "This is a shell script"

Then make it executable with:
chmod 755 scrpt

and then from Gambas:
SHELL "./scrpt"

When you run the Gambas program, the output appears in the Gambas IDE console.

I will put money on this being a very inefficient way of doing what you are trying to achieve.

> 
or write it into gambas some how.


That sounds better! Show me the script and maybe I can help.

rgds

---

