---
title: "Command Prompter help"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Grymauch on 2008-08-23
Here's the deal...
I have a virus on my computer.  It has lodged itself in the System Volume Information folder which is unaccessible.  
No problem.  I know how to enable access to that folder.
Get into the Command Prompter and type: 
 cacls "System Volume Information" /E /P [I]username[I]:F
Simple enough.
The problem is when I access the Command Prompter it starts me here:
C:\Documents and Settings\[I]username[I]
I can't get to just the C drive.  I try typing C:,  but it just redirects me to the same as above.
I'm betting this is something stupid that I just don't know how to do, but I would appreciate some help more than you can know:([/I][/I] [/I][/I]

---

### Post by iaculallad on 2008-08-23
> **Grymauch said:**
> Here's the deal...
I have a virus on my computer.  It has lodged itself in the System Volume Information folder which is unaccessible.  
No problem.  I know how to enable access to that folder.
Get into the Command Prompter and type: 
 cacls "System Volume Information" /E /P [I]username[I]:F
Simple enough.
The problem is when I access the Command Prompter it starts me here:
C:\Documents and Settings\[I]username[I]
I can't get to just the C drive.  I try typing C:,  but it just redirects me to the same as above.
I'm betting this is something stupid that I just don't know how to do, but I would appreciate some help more than you can know:([/I][/I] [/I][/I]

Boot from an Ubuntu LiveCD and use NAUTILUS to deal with your windoze System Volume Information folder as this is not a windoze forum so I opt to offer an Ubuntu "style" solution.

---

### Post by Grymauch on 2008-08-23
Thank you for the reply...

What is the Ubuntu LIVE CD. :confused: Sorry if this is elementary stuff.

---

### Post by iaculallad on 2008-08-23
> **Grymauch said:**
> Thank you for the reply...

What is the Ubuntu LIVE CD. :confused: Sorry if this is elementary stuff.

LiveCD contains the full Ubuntu OS. You have the option of using/ it for testing purposes (as it "emulates" a complete installation) while being accessed on the CD/DVD media or you could choose to install it on your HDD for permanent installation.
You could download the latest ISO file from this [site]("http://cdimage.ubuntu.com/hardy/daily-live/20080823.1/") and try to [burn]("https://wiki.ubuntu.com/BurningIsoHowto") it on a CD/DVD media.

---

### Post by Gone fishing on 2008-08-23
Mmmm You do realise this is an Ubuntu Linux forum? 

If you go to [http://www.ubuntu.com/](http://www.ubuntu.com/) you will be able to download the Ubuntu CD this will run Ubuntu from the CD and install Ubuntu Linux if you wish. From Ubuntu you will be able to get into XP and delete your virus.

A more interesting solution would be to install Ubuntu from the live CD it can resize your XP partition to make space and in Ubuntu you wont have to worry about virues again - you could even install AVG antivirus and clean XP.

---

### Post by BillDozer on 2008-08-23
> **Grymauch said:**
> Here's the deal...
I have a virus on my computer.  It has lodged itself in the System Volume Information folder which is unaccessible.  
No problem.  I know how to enable access to that folder.
Get into the Command Prompter and type: 
 cacls "System Volume Information" /E /P [I]username[I]:F
Simple enough.
The problem is when I access the Command Prompter it starts me here:
C:\Documents and Settings\[I]username[I]
I can't get to just the C drive.  I try typing C:,  but it just redirects me to the same as above.
I'm betting this is something stupid that I just don't know how to do, but I would appreciate some help more than you can know:([/I][/I] [/I][/I]
try to write cd \
This will change to the root of the C: drive.

---

### Post by Grymauch on 2008-08-23
> **BillDozer said:**
> try to write cd \
This will change to the root of the C: drive.

Oh geez... thank you SO much.  I knew it was something stupid.  I even knew about the "cd" command but never thought of putting in the "\".  I don't know anything about programming or code, and I've been running around different sites trying to get some help.

Billdozer, THANK YOU! 
YOU ROCK! :guitar:

---

