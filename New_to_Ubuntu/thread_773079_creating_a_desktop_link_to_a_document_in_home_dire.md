---
title: "creating a desktop link to a document in home directory"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by socref on 2008-04-28
Hello.

This is probably incredibly easy in Ubuntu (it sure was easy in SuSE). But I just cannot figure how to create a link on my desktop that looks back to a document (e.g., a word-processor document) in my home directory such that changes I make when working in the "linked" document also appear in the original.

With SuSE I just dragged the original document to my desktop and dropped it there, and SuSE created a link. Then any changes I made in the linked document appeared in the original.

But I don't see that option to drop a link on the desktop in Ubuntu. I can drag the document to the desktop and drop it there, or I can copy the document to the desktop. And I can right click on the document in my home directory and select  "make link." But no matter where that link is, changes to it do not appear in the original.

Hope that explanation of what I'm trying to do is clear.

What silly thing am I missing here?

Thanks!
socref

---

### Post by tamoneya on 2008-04-28
I have never used suse so i am not exactly sure what you are talking about but when I make links i typically right click on the document or directory and select make link.  Then I drag the link to where I want it.

---

### Post by Oldsoldier2003 on 2008-04-28
> **tamoneya said:**
> I have never used suse so i am not exactly sure what you are talking about but when I make links i typically right click on the document or directory and select make link.  Then I drag the link to where I want it.

yes thats much easier than


```
ln -s /full/path/to/document ~/Desktop/linkname
```

---

### Post by KaliVoid on 2008-04-28
if i understand you right then you have to "save" the changes you
made to the document before checking the original

---

### Post by stchman on 2008-04-28
> **socref said:**
> Hello.

This is probably incredibly easy in Ubuntu (it sure was easy in SuSE). But I just cannot figure how to create a link on my desktop that looks back to a document (e.g., a word-processor document) in my home directory such that changes I make when working in the "linked" document also appear in the original.

With SuSE I just dragged the original document to my desktop and dropped it there, and SuSE created a link. Then any changes I made in the linked document appeared in the original.

But I don't see that option to drop a link on the desktop in Ubuntu. I can drag the document to the desktop and drop it there, or I can copy the document to the desktop. And I can right click on the document in my home directory and select  "make link." But no matter where that link is, changes to it do not appear in the original.

Hope that explanation of what I'm trying to do is clear.

What silly thing am I missing here?

Thanks!
socref

The way to create shortcuts or as Linux calls them "symbolic links" is to hightlight the file with the middle mouse button drag it onto the desktop and then click the menu "Link here".

Very easy.

Else you will have to so the CLI thing.

```
ln -s <location of file or folder you want to link to> ~/Desktop
```

---

### Post by brownknight on 2008-04-28
Right click on the document you want to have a link and choose make link. Then just drap the link or shortcut to where you want it to be.

---

### Post by socref on 2008-04-28
> **KaliVoid said:**
> if i understand you right then you have to "save" the changes you
made to the document before checking the original

Yes, saved the changes.
socref

---

### Post by socref on 2008-04-28
> **stchman said:**
> The way to create shortcuts or as Linux calls them "symbolic links" is to hightlight the file with the middle mouse button drag it onto the desktop and then click the menu "Link here".


No middle mouse button. Two only.
socref

---

### Post by socref on 2008-04-28
> **brownknight said:**
> Right click on the document you want to have a link and choose make link. Then just drap the link or shortcut to where you want it to be.

That's exactly what I was doing. Actually I was trying it with an Excel spreadsheet rather than a text document, but that should not have made any difference. However, here is something really fascinating.

I tried again, this time with a text document and it does work.

Now I typically use CrossOver Office to open Word, Excel, and Powerpoint documents. 

And creating a symbolic link using the obvious method does retain changes with Word (or Open Office Word Processor), and it works with Powerpoint (or Open Office Impress), and it works with Open Office Spreadsheet. But it does NOT work with Excel!

I have tried Excel sheet after sheet and not one of them will retain changes. Isn't that weird? Before I posted to the forum I had only tried to create the link and save using an Excel sheet. It never occured to me that it would make any difference what kind of document you were trying to link. Ubuntu should not care, right?

So I can successfully create the link and save changes back in the original document for any kind of document EXCEPT Excel.

Can someone who has CrossOver Office try this with an Excel document and see if you can save changes in a linked spreadsheet and have those changes also appear in the original document?

Thanks
socref

---

