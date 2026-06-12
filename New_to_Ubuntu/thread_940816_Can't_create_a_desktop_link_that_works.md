---
title: "Can't create a desktop link that works"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by socref on 2008-10-07
Hello, everyone. I really apologize for this absurdly basic inquiry, but I think I'm doing everything right, yet without success.

Using Ubuntu 7.10.

I am trying to create a link on my desktop that points to a text file in my home directory (it's an MS Word doc). This would allow me quick access to work on the text file without having to go into my home directory. That should be simple enough, right? 

Well, no. :( 

I followed the directions in the Ubuntu Help directory ("Creating a symbolic link to a file or folder"). Specifically I grabbed the text file in my home directory, then pressed and held Ctrl+Shift, and I dragged and dropped the file on my desktop. That created a duplicate file with an arrow pointing upwards and to the right. 

I looked at the properties of this new file and it shows that it's a link pointing to the original file still sitting in my home directory. That should do it, right?

Well, no.  :(

When I make a change to the link document on the desktop and save it, the change does NOT happen in the original file. The change is saved only in the link. But here's where it really gets strange.

If I close and then reopen the link on the desktop the arrow that pointed up and to the right is gone. And when I look at the properties, that file on my desktop is no longer a link -- it does not point back to the file in my home directory. So it has morphed into a copy of the original, but it is no longer linked back to the original.

Equally interesting, if I create the link in the home directory (right click on the original and then click "make link") so the link file is physically inside the same folder with the original, the same things happen. Changes to the link do not appear in the original text file. And it morphs so that its properties no longer show as a link. 

What am I doing wrong? This should be so simple. 

In SuSE I just dragged the original file to the desktop, right clicked "create link," and it was there, ready for editing that always reflected back to the original.

Sheesh!! Thanks. 
socref

---

### Post by semitone36 on 2008-10-07
Hmm... when you save your file what is the path that the file is being saved to?

EDIT: Perhaps an easier method would be to just have the original file saved to your desktop?

---

### Post by cariboo on 2008-10-07
What application are you using to edit the document? I tried creating links on the desktop with two different files, then edited and saved them and they still remained links to the origional files.

I created the links by middle clicking the file and dragging it to the desktop. Nautilus asked If I wanted to move it, copy it or create a link, I chose link.

Note: I you don't have a wheel mouse you can use both mouse buttons at once to do the same thing.

Jim

---

### Post by socref on 2008-10-07
> **semitone36 said:**
> Hmm... when you save your file what is the path that the file is being saved to?

EDIT: Perhaps an easier method would be to just have the original file saved to your desktop?

1) Is that the same as the location?

2) Yes, but then I have to physically move it back into the home directory. And if, by chance, I do a backup of my home directory but forget to move the file beforehand, then it's not included in the backup. So having the file linked saves me from such oversight.

socref

---

### Post by socref on 2008-10-07
> **cariboo907 said:**
> What application are you using to edit the document? I tried creating links on the desktop with two different files, then edited and saved them and they still remained links to the origional files.

I created the links by middle clicking the file and dragging it to the desktop. Nautilus asked If I wanted to move it, copy it or create a link, I chose link.

Note: I you don't have a wheel mouse you can use both mouse buttons at once to do the same thing.

Jim

1) I'm using Crossover Office to run MS Word files.

2) I have a wheel mouse, but only two buttons. I tried your method (both mouse buttons at once) but result is the same. Exactly as described previously.

socref

---

### Post by semitone36 on 2008-10-07
> **socref said:**
> 1) Is that the same as the location?


Yes.  An example would be /home/documents/doc1.doc. I was thinking that perhaps somehow the document is overwriting the link on the deskotp every time you save.

---

### Post by rustutzman on 2008-10-07
How are you saving the document? Are you using the "File" menu? Does the same thing happen when just using "Control S"? Seems like it's doing a file save as instead of just file save.

Russ

---

### Post by socref on 2008-10-07
> **rustutzman said:**
> How are you saving the document? Are you using the "File" menu? Does the same thing happen when just using "Control S"? Seems like it's doing a file save as instead of just file save.

Russ

1) I click on the "save" icon at the top of the MS Word tool bar.

or

2) I click "file>save" from the top bar.

or

3) I click control S.

Doesn't matter. All three result in the same thing. The original document is not changed, and the link morphs into a copy. It is no longer a link.

socref

---

### Post by socref on 2008-10-07
> **semitone36 said:**
> Hmm... when you save your file what is the path that the file is being saved to?

EDIT: Perhaps an easier method would be to just have the original file saved to your desktop?

The location (path to the original document) is: /home/gil/work/fighting_back

The location of the link when first created is: /home/gil/Desktop

The link target (pointing to the document in my home directory) when first created is: /home/gil/work/fighting_back/Contract_Review_Template.doc

After I edit and save the linked file on the desktop the location remains /home/gil/Desktop, but the link target is no longer shown in the properties.

And, of course, the original document in my home directory still doesn't reflect the changes I made in the link document on my desktop.

Bizarre!
socref

---

### Post by fabricio.lemos on 2009-03-17
I have the same problem. Does anyone know how to solve this?

thanks in advance,
Fabricio Lemos

---

