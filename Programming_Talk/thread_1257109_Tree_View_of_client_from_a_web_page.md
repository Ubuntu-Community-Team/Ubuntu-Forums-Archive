---
title: "Tree View of client from a web page?"
date: 2009-09-03
forum: Programming Talk
---

### Post by tc101 on 2009-09-03
I have a web page that will save a file on a client.  We already have an activeX that does the saving.  I just need to do a tree view of the client hard drive so the user of the web page can select where on his computer the file will be saved.

I am working in the MS world with classic ASP and  javascript running in IE on XP boxes.  This is for a company use web site so I control all the boxes. 

Can anyone point me at some sample code to do this?

---

### Post by WitchCraft on 2009-09-03
> **tc101 said:**
> I have a web page that will save a file on a client.  We already have an activeX that does the saving.  I just need to do a tree view of the client hard drive so the user of the web page can select where on his computer the file will be saved.

I am working in the MS world with classic ASP and  javascript running in IE on XP boxes.  This is for a company use web site so I control all the boxes. 

Can anyone point me at some sample code to do this?

TreeView of the **CLIENT's **hard-drive from an ASP page? 
That's impossible for security reasons. If that would be possible...

You can do a recursive directory traversal and generate an XML file, which you can then databind to a treeview. But that only works for ASP.NET, and only serverside or for a database.

[http://bigbadcode.com/2005/09/12/recursive-file-and-folder-listing-vbnet/](http://bigbadcode.com/2005/09/12/recursive-file-and-folder-listing-vbnet/)
is how to travers a directory structure in .NET.

Is probably similar in old ASP.


Maybe you should write an email to the german intelligence service and ask them for the "Bundestrojaner", which should be able to do just that ;-))

---

### Post by tc101 on 2009-09-03
You can do a tree view from Yahoo Mail when it asks you where you want to upload a file from.

---

### Post by tc101 on 2009-09-04
Does anyone know how big sites like yahoo override the security on a computer and view the client hard drive?

---

### Post by tturrisi on 2009-09-04
File upload is differnt than File Save.  HTML provides a built in form object called "file".  <input type="file"> produces a text input and a Browse... button.

In IE 5 one could at one time use code to show the contents on the user's directories.  But that security hole got plugged back around 2003 or so.

To invoke a Save dialog you'd have to code it into the ActiveX control.

I used to use this code to display viewer's files:
```
<object id="browserIcons" classid="clsid:EAB22AC3-30C1-11CF-A7EB-0000C05BAE0B"
    align="baseline" border="0" width="400" height="200">
      <param name="ExtentX" value="10583">
      <param name="ExtentY" value="5292">
      <param name="ViewMode" value="3">
      <param name="Offline" value="0">
      <param name="Silent" value="0">
      <param name="RegisterAsBrowser" value="0">
      <param name="RegisterAsDropTarget" value="0">
      <param name="Height" value="200">
      <param name="Width" value="400">
      <param name="AutoArrange" value="1">
      <param name="NoClientEdge" value="0">
      <param name="AlignLeft" value="1">
      <param name="ViewID" value="{0057D0E0-3573-11CF-AE69-08002B2E1262}">
      <param name="Location" value="file:///C:/">
    </object></p>
```

---

