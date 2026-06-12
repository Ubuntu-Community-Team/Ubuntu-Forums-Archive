---
title: "[SOLVED] Synaptic downloaded files. Where do they go?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by jorgeguberte on 2008-08-31
Hello. I've converted my pc 100% to Linux today. Wiped out Windows, and bye bye Mr. Gates. lol
I use FTP clients a lot, to maintain my website. I downloaded a ftp client via Synaptic Package Manager, but i have no clue where the downloaded files are, or how i can open the ftp client, or any other program downloaded from Synaptic.

Can anyone gimme a hand? ^^

---

### Post by Rocket2DMn on 2008-08-31
/var/cache/apt/archives I believe.

Why do you need to know where they are?  The package managers do the installation for you.

---

### Post by oldsoundguy on 2008-08-31
if what you want is an FTP uploader (manager) .. FireFTP, an add on to Firefox, has proven to work well for me.  Very much the look and feel of WS_FTP_Pro.

---

### Post by BDNiner on 2008-08-31
you can normally run a program installed from synaptic by typing the name of the program into the terminal. since it is an ftp program i would also check in the internet sub menu to see if an icon was created for the program.

---

### Post by jorgeguberte on 2008-08-31
> **Rocket2DMn said:**
> /var/cache/apt/archives I believe.

Why do you need to know where they are?  The package managers do the installation for you.

well...synaptic installed it, but i cannot find out how i open up the program just installed.  a shortcut, an icon, anything like that. 
=\

---

### Post by jorgeguberte on 2008-08-31
> **BDNiner said:**
> you can normally run a program installed from synaptic by typing the name of the program into the terminal. since it is an ftp program i would also check in the internet sub menu to see if an icon was created for the program.

nope, no shortcut created. =\
i typed the name into the terminal, and the insertion point changed to the name of the program. i'm 100% clueless when it gets to doing things through the text command.

---

### Post by Rocket2DMn on 2008-08-31
OK, what program(s) did you install that you want to run?  Usually they are made available somewhere under the Applications menu (sometimes you have to re-login or restart the computer for them to appear, though not usually).

---

### Post by Gannon8 on 2008-08-31
What program did you install? Usually you just need to type in the name of the program.

Edit: Beaten

---

### Post by jorgeguberte on 2008-08-31
I just restarted the compy, and nothing changed under the Internet submenu. So, i attached a screenshot of the package. The program is "ncftp".

---

### Post by jakupl on 2008-08-31
Well some programs that you install in synaptic are not GUI programs (Graphical User Interface), and therefore have no link. you can only run these programs in the terminal.
Add/Remove is a more user friendly way of installing programs.

---

### Post by Rocket2DMn on 2008-08-31
I believe NcFTP is a command line program, so there is no GUI for it, which would be why there are no links under Applications.  I use gftp as my GUI FTP client in Ubuntu, you may want to check that out instead.

---

### Post by jorgeguberte on 2008-08-31
> **jakupl said:**
> Well some programs that you install in synaptic are not GUI programs (Graphical User Interface), and therefore have no link. you can only run these programs in the terminal.
Add/Remove is a more user friendly way of installing programs.


ooh, i think it explains everything. ^^
i'll find another client using Add/Remove.


EDIT:
Done! Downloaded gftp.
Thanks to everyone. Much appreciated. :)

---

