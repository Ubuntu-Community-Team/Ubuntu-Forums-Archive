---
title: "Can't find System Tools"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Littlehawk on 2008-05-13
I have been running 8.04 and 7.10 for about a week on two machine. I'm still trying to navigate around the menus.

I came across a thread that says
> Open Applications > System Tools > Configuration Editor 

I can't find System Tools on my 8.04 install, so I can't get to the configuration editor. I did find both on the 7.10 install.

On the 8.04 install, I selected Applications > Add/Remove, and clicked the System Tools Icon. It shows that the Configuration Editor is already installed. I'm assuming it also is telling me that it's on the Applications>System Tools Menu.

I've looked at all of the menus and I cant find System Tools or Configuration Editor anywhere.  Does someone have any ideas what I should do?

---

### Post by systemqa on 2008-05-13
first you must go to  systme >> preferences >> main menu

under applications you will see system tools click it then check configuration editor in right panel

Open Applications > System Tools > Configuration Editor 
and you will be able to see it again
thats it :)

---

### Post by HotShotDJ on 2008-05-13
> **Littlehawk said:**
> I've looked at all of the menus and I cant find System Tools or Configuration Editor anywhere.  Does someone have any ideas what I should do?Most users do not (and should not) use the Configuration Editor, so just like with Windows RegEdit, it is tucked away, out of sight and out of mind.  It is easily accessed from a terminal using the command "gconf-editor".

You can add it to your Applications menu by right clicking on Applications, then selecting "System Tools" in the left panel.  You'll notice "Configuration Editor" is in the right hand panel.  Check it off and then close.

---

### Post by Littlehawk on 2008-05-13
Thanks to both of you. It looks easy. now. Apparently, I've already used both ways use the configuration editor or edit the configuration file and I didn't know they were changing the same info. 

It works now!

---

