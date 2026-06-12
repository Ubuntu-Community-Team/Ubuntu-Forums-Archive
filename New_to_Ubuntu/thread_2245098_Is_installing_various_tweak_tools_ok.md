---
title: "Is installing various tweak tools ok?"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by czgirb on 2014-09-21
within my ubuntu 14.04, I installed
[B]* gnome-tweak-tool
* unity-tweak-tool
* Ubuntu Tweak
* CompizConfig Setting Manager
* dconf-editor[/B]
Sometimes I use GTT, but sometimes I use CCSM.
Is it right? Is it OK?

---

### Post by grahammechanical on 2014-09-21
Those tools are harmless until we, the user, starts using those tools to make changes.

There are system utilities that allow us to modify the user interface to a limited degree. These tools cover the same area as the system utilities but they go further into other areas. And in some areas they duplicate the work of each other. This is to be expected as these tools are developed independently.

Linux/Ubuntu is under constant development. These tools need constant development to keep up with the changes. 

Regards.

---

### Post by buzzingrobot on 2014-09-21
Unity is actually a Compiz plugin, so be careful making changes in CCSM. I use it to enable switching workspaces with the mouse wheel, but that's it.

The other tools, I believe, all make changes to the same configuration files, which may also be altered manually with the gsettings command.

---

### Post by czgirb on 2014-09-22
> **grahammechanical said:**
> 
... in some areas they duplicate the work of each other ...


So ... it is harmless to install it together ... OK.
How to factory-reset all tools below:
[B]* gnome-tweak-tool
* unity-tweak-tool
* Ubuntu Tweak
* CompizConfig Setting Manager
* dconf-editor
* Gnome Fallback DE
Thank you
[/B]

---

### Post by buzzingrobot on 2014-09-22
dconf-editor has a "Set to Default" option on each individual panel.

---

### Post by grahammechanical on 2014-09-22
The tools by themselves are harmless. They only become powerful when we load them. We can break our user interface if we are not careful. Some settings affect other settings. Changes we make in one tool can be overridden by another tool. If we do not keep a record of the actions that we have taken, then it becomes very difficult to revert the changes. And trying to revert the changes could cause other problems.

My advice would be to use with caution and make changes one at a time and confirm that everything is working before making another change.

I run the Ubuntu development release and there is always the possibility of an update breaking Compiz or Unity. So, I have installed gnome-session-flashback. That gives me a login option of loading Gnome Flashback (Metacity). So, If I break Compiz or Unity I can load to a UI using another window manager (Metacity) and then I can try to fix things.

If we are content with the limited modifications that a default install offers, then we do not need these Tweak tooks, in my opinion. And I am usually content with a default set up. If we want to do more, then I suggest that it would be wise to have an alternative desktop/UI installed for when things break.

Regards.

---

