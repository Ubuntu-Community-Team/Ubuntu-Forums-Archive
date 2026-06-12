---
title: "Eclipse: Button size"
date: 2005-02-19
forum: Programming Talk
---

### Post by Jochen Skulj on 2005-02-19
Hello,

I installed Eclipse 3.0.1 on Ubuntu Warty. It works fine but all buttons in the IDE are displayed in a wrong size. They have not the correct height and so you can hardly read the buttons' labels.

Has anyone else had the same problem? Is there a fix or workaround?

Thanks, Jochen

---

### Post by defkewl on 2005-02-22
[QUOTE=Jochen Skulj]Hello,

I installed Eclipse 3.0.1 on Ubuntu Warty. It works fine but all buttons in the IDE are displayed in a wrong size. They have not the correct height and so you can hardly read the buttons' labels.

Has anyone else had the same problem? Is there a fix or workaround?

Thanks, Jochen[/QUOTE]
 Which one did you downloaded? Motif or GTK2?

---

### Post by zabilcm on 2005-02-22
This is a problem that I faced while using the Industrial and the Human theme.
You could probably try switching the theme to Mist from Preferences->Themes, doing that will resove the issue.

---

### Post by Jochen Skulj on 2005-02-22
[QUOTE=zabilcm]This is a problem that I faced while using the Industrial and the Human theme.
You could probably try switching the theme to Mist from Preferences->Themes, doing that will resove the issue.[/QUOTE]

Thanks, that's the solution. I used a Nuvola/Lush theme. If I use the Mist theme eclipse works fine.

Jochen

---

### Post by hantsy on 2005-03-02
[QUOTE=Jochen Skulj]Thanks, that's the solution. I used a Nuvola/Lush theme. If I use the Mist theme eclipse works fine.

Jochen[/QUOTE]
 The simple theme work well...
Some complex gtk engines cause java application display ugly...

---

### Post by theh0g on 2005-03-28
[QUOTE=hantsy]The simple theme work well...
Some complex gtk engines cause java application display ugly...[/QUOTE]
 I found this sollution and it works...I edited theme's gtkrc...quoting from another forum:
-----
Just add the following lines of text to a file listed in
ENV variable GTK2_RC_FILES, e.g.
to file $HOME/.kde/share/config/gtkrc :

############################################
style "eclipse-button" {
GtkButton::default_border = {0,0,0,0}
GtkButton::default_outside_border = {0,0,0,0}
}
class "*Button*" style : highest "eclipse-button"
widget_class "*Button*" style : highest "eclipse-button"

#############################################

Start Eclipse and the buttons will be readable :-) 
-----

---

