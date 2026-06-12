---
title: "Gambas simple Question"
date: 2010-01-20
forum: Programming Talk
---

### Post by ve3tru on 2010-01-20
I'm a newbe playing with gambas
My program is a simple GUI computer backup.
Anyway I can't figure out how to use jpeg.s. I tried picture box even tried to make a link to the jpeg. Nothing it won't show up when I run the program.
It's got to be simple but I'm stumped.
Tnx.

---

### Post by kalaharix on 2010-01-21
hi

PictureBox1.Picture = Picture.Load("/home/fred/Photos/SV400005.JPG")

also look at the imageviewer example supplied with gambas.

It is likely you will need to rescale the image to the size of your picturebox which you can do something like:

> 
INC Application.Busy

SHELL "convert /home/fred/Dropbox/Photos/SV400008.JPG -resize "   & PictureBox1.Height & "x" & PictureBox1.width & " smaller.jpg" WAIT

PictureBox1.Picture = Picture.Load("/home/fred/smaller.jpg")
DEC Application.Busy  


(depending on the width of your screen, the shell command might show as 2 lines: it is actually 1 line)

rgds

---

### Post by ve3tru on 2010-01-22
Thanks but no go
I used
PictureBox1.Picture = Picture.Load("/home/peter/Desktop/backup/tux.jpg")

comes back missing AS

Tnx

---

### Post by kalaharix on 2010-01-23
hi

What version Gambas?

Are you putting the statement inside a public sub {e.g. Form_open()}? Show me the full listing.

rgds

---

### Post by ve3tru on 2010-01-24
Ok got it  tnx had to resize and... I could only get it to work after the 1st line
PUBLIC SUB _new()
Couldn't get it working anywhere else in the program, (I guess your not suppose to) tried PUBLIC SUB whatever no go
anyway many thanks couldn't of done it without you.

---

### Post by ve3tru on 2010-01-24
Ok Ive got another question 4 u
This ones harder lol
As SHELL is running my backup program how do I know when its done ?
so i can let the user know.
Tnx.

---

### Post by kalaharix on 2010-01-25
Hi

From your post it sounds like you do not know why the line should be inside the Form_open() event. This is fundamental to event-driven programming (which includes Gambas and VB6) so I suggest you google 'event-driven programming' and brush up a bit.

Put wait at the end of your shell or exec command. e.g.
SHELL "mysqldump --add-drop-table -u root stock > /home/fred/stockDump.sql" WAIT 

This forces the Gambas interpreter to wait until the shell command is complete. Follow it with:
message.info("Backup Complete") 
to get the users acknowledgement of this.

rgds

---

