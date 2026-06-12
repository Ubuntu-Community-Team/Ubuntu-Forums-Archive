---
title: "Expertise request pertaining to OpenOffice Spreadsheet."
date: 2008-09-26
forum: New to Ubuntu
---

### Post by suomalainen on 2008-09-26
Ubunteros!

I would like to insert a "new line" within a spreadsheet cell. How is this done?

I.E. creating an address within a cell. For example:

Name
Street address
city, state zip
telephone

Thanks

P.S. I don't want to use the space bar to shift everything to a new line.

---

### Post by Calmor on 2008-09-26
> **suomalainen said:**
> Ubunteros!

I would like to insert a "new line" within a spreadsheet cell. How is this done?

I.E. creating an address within a cell. For example:

Name
Street address
city, state zip
telephone

Thanks

P.S. I don't want to use the space bar to shift everything to a new line.

CTRL-Enter does what I think you're talking about.  

Hope this helps!

---

### Post by Linux&amp;Gsus on 2008-09-26
Hit <ctrl> + <enter>

Edit: I'm too slow... :D

---

### Post by suomalainen on 2008-09-26
Nope! That doesn't work. It only opens up a new empty cell.

BTW, I'm using Gutsy with version 2.3

---

### Post by MrWES on 2008-09-26
I believe it's alt + enter

Bill

---

### Post by Calmor on 2008-09-26
I have Hardy with OOo 2.4, but it should be the same.  (I checked my Windows version but it's 2.4 also).  

Not to underestimate your knowledge, but is it opening a new cell or just putting text where another cell should be (as in, not resizing the cell)?

If I hit enter, shift-enter, or alt-enter, it "finalizes" (for lack of a better word) my previous cell's entry and moves down one, but ctrl-enter just moves down a line and temporarily looks like it's in another cell.  Then, it either resizes the row or just hides the other text if there's something below it to overlap.

---

### Post by Linux&amp;Gsus on 2008-09-26
I just quickly tried it. <alt> + <enter> highlights the cell I'm in. <ctrl> + <enter> adds a new line in a cell but it somewhat doesn't look like it.
Means, I write, hit <ctrl> + <enter>, continue writing in the new line but it seems to write in a new cell. When I hit <enter> the line numbering on the right adjust correctly according to what I did.

BTW, I have OOo 2.4, but as far as I remember it has always been like this. For me at least.
Hope that helps.

---

### Post by suomalainen on 2008-09-26
So far none of the advice and suggestions are working. But thanks none the less.................

Again, I want to create a spreadsheet that contains address information within a SINGLE cell.

Example:

Name
Street address
city, state zip
telephone

I can use the "space bar" to "push" the individual line items like street, city, telehone to a new line.... BUT I don't want to do that.

I'd like to use a command to do this instead.

ctrl= enter and alt=enter do not work. These commands only open up a new cell.

---

### Post by Calmor on 2008-09-26
I can try it on my girlfriend's computer this evening when I get home, if it's not already answered by then.  She's still running Gutsy, and most likely 2.3 (unless an update was pushed through backports).

---

### Post by suomalainen on 2008-09-26
Many apologies everyone!

The suggestions offered do work!!! I'm using a Logitech wireless keyboard model S510 and it was on my lap while I was working. By being in & out of "coverage" certain commands from the kepboard weren't making it to the sensor for processing. Thus, OpenOffice wasn't hearing them....

So that's the story on my end. Everything is working now and I appericate the  assistance offered...

Thank you!

---

### Post by MrWES on 2008-09-26
I found this thread:

> 
Re: How-to input multi-line data in a table cell?

Postby tcrabb on Fri Jul 18, 2008 11:27 am
It sounds like you are trying to enter an entire recipe within a single cell - is this right? If this is the case you need to use the Memo [LONGVARCHAR] type field rather than Text [VARCHAR] data or you will be limited to 255 chars. You cannot use return for newline directly within a normal table cell.

Instead enter new recipe data by creating a form based on this recipies table - use the wizard if you are a newbie and choose Columnar rather than DataSheet when arranging controls. Or you can choose DataSheet then add some text boxes to dispay the data of any one table record. New lines can be achieved just by pressing return as normal when using the text field.

NOTE : If you have used new lines for formatting of the recipe within the text box within the form you will only see the first line when viewing the table directly from the Tables tab on the left pane of the project window.


---

### Post by Linux&amp;Gsus on 2008-09-26
haha, well, can happen... :lolflag:
just bring the receiver a bit closer and continue to relax in your chair. just don't fall asleep.

Am happy that it works. :)

---

### Post by blobby on 2009-08-21
Hi, try pressing alt+enter or ctrl+enter while your cursor is in the cell - this worked for me

---

### Post by hunebku on 2011-06-23
greetings
i am a very very newbie to ubuntu 
and to spreadsheets for that matter 

i am working with Ubuntu 10.04 LTS- the Lucid Lynx

and open office 3.2.0 

this is an old thread
and maybe there is another similar one 
apologies if so . 

i had the same problem
and just to say the ctrl + enter only works if i activate wrap text automatically

right click on cell ( or on top left cell in corner to apply to all )
format cell
alignment
properties
and then wrap cells automatically  

still wondering what 'hyphenation active' means as extra possibility here
sounds cool :-)

greets
Benjy

---

