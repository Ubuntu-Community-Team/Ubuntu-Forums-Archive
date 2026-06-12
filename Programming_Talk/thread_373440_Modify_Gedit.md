---
title: "Modify Gedit"
date: 2007-03-01
forum: Programming Talk
---

### Post by tc101 on 2007-03-01
I would like to make some simple modifications to gedit.  These modifications are not very important but I will learn about programming linux apps by doing them.

The first thing I would like to do is copy the Find command, which is in the Search menu, to the Edit menu.  

There is a file called /usr/share/gedit-2/ui/gedit-ui.xml that looks like it would be the menu file, but it is confusing to me.  Here is some  code for the EditMenu

<menu name="EditMenu" action="Edit">
      <menuitem name="EditUndoMenu" action="EditUndo"/>
      <menuitem name="EditRedoMenu" action="EditRedo"/>
      <separator/>

I see the Undo and Redo name and action, but where are the actual titles "Undo" and "Redo" ?  I am not clear on what exactly I would add here to move the Find command to the edit menu.

I have been looking for some basic instructions about how to change this, but I can't find anything.

---

### Post by Tomosaur on 2007-03-01
You may need to dive into the source to find that. The implementations of the menu bar will vary between apps. It appears that gedit reads that xml file and then maps the hard-coded menu bar to it. You MAY be able to achieve what you're trying to do here, but I recommend browsing the source anyway. The important part is the 'action'. You can theoretically move the find menuitem into the EditMenu menu, through a simple copy and paste. Just back the xml file before you make any changes so you can revert back to the original if it doesn't work. The XML file is part of the gtk.UIManager class, but I can't remember exactly how it works - I think the actual menu appearance (titles and whatnot) is hard-coded however, the xml file just gives it it's structure.

---

### Post by tc101 on 2007-03-01
I will have to learn a lot to do this, but I would like to learn.  I am a retired programmer from the Microsoft VB and ASP.Net world, so I know how to write code but I know nothing about where the source code for gedit is found or how to change it or compile it.  I don't expect to learn that from asking questions in this forum.  Is there a site online somewhere that would take me through the steps of doing something like this?

---

### Post by lnostdal on 2007-03-01
> **tc101 said:**
> I would like to make some simple modifications to gedit.  These modifications are not very important but I will learn about programming linux apps by doing them.

The first thing I would like to do is copy the Find command, which is in the Search menu, to the Edit menu.  

There is a file called /usr/share/gedit-2/ui/gedit-ui.xml that looks like it would be the menu file, but it is confusing to me.  Here is some  code for the EditMenu

<menu name="EditMenu" action="Edit">
      <menuitem name="EditUndoMenu" action="EditUndo"/>
      <menuitem name="EditRedoMenu" action="EditRedo"/>
      <separator/>

I see the Undo and Redo name and action, but where are the actual titles "Undo" and "Redo" ? 

they are in a separate file and are loaded at run-time depending on what (human) language the end-user uses

move (edit: or copy) the line:

```
<menuitem name="SearchFindMenu" action="SearchFind"/>
```

..to the section denoted by:

```
    <menu name="EditMenu" action="Edit">

```

(append it after that line for instance)

not sure how this teaches you anything, but maybe you should take a look at Glade .. it generates XML-files that can be loaded by applications at runtime to generate GUIs

---

### Post by tc101 on 2007-03-01
Thanks.  I'll give that a try and also take a look at glade.

---

