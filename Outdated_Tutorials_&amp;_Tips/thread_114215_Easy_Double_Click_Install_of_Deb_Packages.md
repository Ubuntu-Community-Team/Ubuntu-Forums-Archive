---
title: "Easy Double Click Install of Deb Packages"
date: 2006-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Nate53085 on 2006-01-08
Below is sorta irrelavant due to the program called gdebi.  

packages available here: [http://people.ubuntu.com/~mvo/backports/breezy/](http://people.ubuntu.com/~mvo/backports/breezy/)


The original content may offer some insite for someone about something, so I left it.
------------------------------------------------------------------------------


This is nothing but a dirty hack, don't get to angry.

1) Open Applications>System Tools>Applications Menu Editor

2) Click System Tools then New Entry

3) Create the Entry as Follows

Name: dblclk123
Comment: (blank)
Command: sudo dpkg -i
Icon: No Icon
Check the box that says run in terminal

This created the necessary .desktop file we need

4) Right Click on a .deb file and select Properties.  (If you do not have one handy, feel free to grab this one: [http://www.natebourgoin.com/links/fcc.deb]("http://www.natebourgoin.com/links/fcc.deb") we will remove once we are finished)

5) Click Open With then Add.  Select dblclk123 from the menu and click add.

6) Make sure that "Open With" now has dblclk123 selected (select it if it hasn't) then click close

7) Open Applications>System Tools>Applications Menu Editor again.  Then System Tools.  Uncheck the checkmark near dblclk123 (this will remove it from the visible menu while keeping the necessary .desktop file)

8) Test by double clicking the .deb package.  A terminal will open, ask for your password, then install the package.

9) If you used the Firstclass .deb I linked to above and don't have any use for the program, open a terminal and type:
> sudo apt-get remove fcc
to remove it.

Assuming it all went smoothly, you should be all set.


And now onto the discussion on why this is such a bad idea.

---

### Post by Shin Natsume on 2006-01-15
very nice, thanks for the how to :D

ciao

---

### Post by benplaut on 2006-01-15
i'm still waiting for a nice app that makes a local repo to solve dependencies, but this is nice, in the meantime :)

---

### Post by cjm5229 on 2006-01-15
I would put this in my top ten handiest apps. Thank You

---

### Post by rado_london on 2006-01-15
Thanks a lot
I like it now

---

### Post by donmayor on 2006-01-15
Thanx, this is marvelous. It would save me a lot of time

---

### Post by beaNN on 2006-01-15
Thanks! This is really quick and easy.

---

### Post by betamax on 2006-01-15
Very Handy,

Cheers ;)

---

### Post by hen3rz on 2006-01-15
So smart and intuitive! thanks heaps.

---

### Post by penguinmaster on 2006-01-15
I followed the directions for this and when I double click on a .deb file, the terminal window pops up real quick and then disappears again.  Any suggestions??

---

### Post by Nate53085 on 2006-01-16
Did you check the checkbox that says "Run in terminal" when you created the entry in Application Menu editor?

---

### Post by Nate53085 on 2006-01-16
Variations:

instead of sudo dpkg -i put sudo alien -di and set for RPMS and you can doubleclick install RPMs (though they won't always work once installed, RPM->DEB is not extremely reliable, dependency stuff)

This technique will also allow you to run any code with any type of file, just substitute in the code you want to run and set it to the filetype (right-click on the file and all that jazz)

One thing I'm seeing this would be useful for is allowing textfiles with different extentions to be handled differently (using some if statements that test for extention).

---

### Post by quonsar on 2006-01-16
Or you could get [Debins]("http://programmer-art.org/debins").  Debins "aims to counter the difficulties of apt's commandline interface and the lack of obscure packages in Ubuntu's repositories while remaining integrated with apt."

---

### Post by lex on 2006-01-16
[QUOTE=penguinmaster]I followed the directions for this and when I double click on a .deb file, the terminal window pops up real quick and then disappears again.  Any suggestions??[/QUOTE]

Yeah me too. I tried to remove the file to see if it worked,
"[COLOR="#000000"][COLOR="Blue"]lex@ubuntu:~$ sudo apt-get remove fcc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fcc
lex@ubuntu:~$"
[/COLOR][/COLOR]
I tried it on another .dep file and the terminal window popped up and ask for password; when i tried to type nothing happened. I pressed enter and it disappeared.
Any ideas?
Thanks
Lex

---

### Post by Jessehk on 2006-01-16
KDE offers this by default.

*runs away quickly*

---

### Post by Nate53085 on 2006-01-16
[QUOTE=Jessehk]KDE offers this by default.

*runs away quickly*[/QUOTE]

lol



Again, was "Run in terminal" checked?  If it asked for your password, it probably did install the package (unless it ran into an error?) but if "Run in terminal" is checked it should open a terminal, ask for a password, install the package outputting to the open terminal and then return to a prompt.  If Run in Terminal isn't checked, the terminal will not open.

---

### Post by BLTicklemonster on 2006-01-30
Wow.



I like it. 


now how to do targzses? :-k

---

### Post by engla on 2006-01-30
Me and another guy both had one try each at making this, but even nicer with a wrapper app in another thread.
You can read about it here:
[http://ubuntuforums.org/showthread.php?p=691323#post691323](http://ubuntuforums.org/showthread.php?p=691323#post691323)

The script I wrote basically works, just double-click and go.

---

### Post by Nate53085 on 2006-02-01
I just prefer not downloading someone's script.  I would rather do it by hand, gives insite into how it works.

---

### Post by self0 on 2006-02-13
nice tip
thanks

---

### Post by Ghetto_Smurf on 2006-02-13
[QUOTE=Jessehk]KDE offers this by default.

*runs away quickly*[/QUOTE]

yeah you better

---

### Post by cutOff on 2006-02-13
What about [gdebi]("http://www.whiprush.org/2005/11/gdebi_arrives.html")? There are already [packages]("http://people.ubuntu.com/~mvo/backports/breezy/") for Breezy even.

---

### Post by mattheweast on 2006-02-14
[QUOTE=cutOff]What about [gdebi]("http://www.whiprush.org/2005/11/gdebi_arrives.html")? There are already [packages]("http://people.ubuntu.com/~mvo/backports/breezy/") for Breezy even.[/QUOTE]

Yes, that is a much better way. You could amend this guide to use that program?

Matt

---

### Post by cutOff on 2006-02-14
[QUOTE=mattheweast]Yes, that is a much better way. You could amend this guide to use that program?

Matt[/QUOTE]
No, of course. I only wanted to report the existence of that program. If anyone is interested, look at this [post]("http://www.ubuntuforums.org/showpost.php?p=723141&postcount=14").


Regards

---

### Post by mattheweast on 2006-02-14
No, I was serious, I think this howto should be amended to reflect gdebi. It's an excellent program.

M

---

### Post by Nate53085 on 2006-02-14
Updated, kept the old stuff there just in case someone was interested in it.

---

### Post by daredevil on 2006-03-01
Lemme me try out. This definitely saves a lot of time

---

### Post by taipan899 on 2006-05-18
Very nice. Thank you

---

