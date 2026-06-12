---
title: "linux seems to have a crude way of starting progs at login"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by chickenPie4breakfast on 2012-03-09
In windows I can easily add progs to the startup folder and when the computer starts up they start up in the background minimized in the tray.
I have tried the same in ubuntu but it's hit or miss - some start up minimized eg. workrave. but some like Kupfer and Zim startup and become active and have to be minimized manually every time I startup the computer.

---

### Post by |{urse on 2012-03-09
If it really bothers you then install devilspie and create a rule for whatever program is bothering you.

sudo apt-get install devilspie 

mkdir ~/.devilspie

cd .devilspie 

gedit zim.ds 
 
then paste this into zim.ds

> (if  
(is (application_name) "zim")  
(begin (minimize) )  
)  

save and close gedit, or whatever text editor you like :)

---

### Post by |{urse on 2012-03-09
[http://askubuntu.com/questions/20989/how-do-i-tell-a-start-up-program-to-start-minimized](http://askubuntu.com/questions/20989/how-do-i-tell-a-start-up-program-to-start-minimized)

---

### Post by 3rdalbum on 2012-03-09
"Minimize to tray" is behaviour that Ubuntu wants to stamp out for consistency reasons.

Ubuntu and Windows do exactly the same thing - they start the program and the program decides how to display itself. The kinds of Windows programs that you might want started minimized usually have an option in their Settings panel.

Ubuntu can do the same (Update Manager does, for instance) but some programs just aren't written to do this, and they often have reason not to.

---

### Post by chickenPie4breakfast on 2012-03-09
thanks for the suggestions, I'll try the devilspie thingy
@ 3rdalbum - It's crazy of the programs to do this and not give an option to start minimized. If all progs did this then when you startup your computer you could have half a dozen apps to minimize by hand!!
Cant say I remember a single app on windows that gave me this problem.

---

### Post by Cheesemill on 2012-03-09
Windows and Ubuntu have exactly the same behaviour on my machine.

Several of the apps that I have put in my Windows startup folder open maximised, the only ones that don't are the ones that have a 'launch minimized' option somewhere in their preferences.

---

### Post by chickenPie4breakfast on 2012-03-10
Firstly I tried the devilspie solution and it didn't work.
I still cant remember a program doing this on windows if it did I must have quickly found a solution. So far on linux I have tried 2 things including installing a program and I still cant solve it.
The main one is ZIM so I am going to try and contact the writer next and ask him why why oh why?

---

### Post by |{urse on 2012-03-11
Sorry, I had the z in zim capitalized, changed it up there.

Found this in a quick google.

> 
I would like zim to hide in the system tray.

There is a Tray Icon plugin which can be enabled from the Preferences dialog.
I would like to start zim hidden in the system tray.

You can call the Tray Icon plugin with the command "zim --plugin trayicon"


From [http://zim-wiki.org/manual/FAQ.html](http://zim-wiki.org/manual/FAQ.html)

---

