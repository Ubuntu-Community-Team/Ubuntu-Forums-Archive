---
title: "linking contents of cells in librecalc"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by jimimckay on 2013-02-27
Hi there, I'm an absolute beginner with librecalc and I'm trying to figure out what seems to be a really basic problem. I've created a spreadsheet for plants, and I have them in one column, with the following columns for additional information. Now, as I go adding to the spreadsheet, the order of the plant name column will change, but I don't know how to link the contents of the cells in the adjacent columns to the first cell!

If anyone can help me then I'd really appreciate it.
Cheers,
Jimi.

---

### Post by Zill on 2013-02-27
jimimckay:  Unless you are using formulae within your spreadsheet then there is no "linking" needed.  All the data you enter into any given row of cells will remain where you put it *unless* you sort column(s) into a different order.

You can, of course, select and then move, insert or delete rows (or columns!) as you wish but all the data in the particular row (or column) will move with the row (or column).

If you do wish to sort your data into a new order then you need to select the appropriate area first and then all that data will be affected by your desired function.

This probably sounds as clear as mud but if you experiment with some dummy data you will soon see how things work.  The [LibreOffice 3 Calc Guide]("https://wiki.documentfoundation.org/images/b/b7/CG34-CalcGuideLO.pdf") should help explain things.

---

### Post by audiomick on 2013-02-27
> **jimimckay said:**
> ... Now, as I go adding to the spreadsheet, the order of the plant name column will change, but I don't know how to link the contents of the cells in the adjacent columns to the first cell!

Do you mean something like you have an alphabetical list of plants, and you want to add a new plant in alphbetical order, and need the existing information to stay lined up with the existing plant names? 

If that is the case, what you need to do is right click in the left border and add a new row at the spot where the new plant goes in.

If your problem is different to that, then please explain a bit more exactly what you are doing. I'm sure there is a way to do it.

---

### Post by jimimckay on 2013-03-11
Hi Michael,

Sorry for not getting back to you sooner, I didn't actually know how this forum even worked.. real beginner.

You got it absolutely: I want to link all of the information in the columns to the right of the plant name to the cell where it's entered, so that the order doesn't change when I add new plants. I'll try what you suggested, hopefully it's as easy as that. I'm going to add a lot of new columns and I don't want to have to move all the information manually later!

Cheers,
Jimi.

---

### Post by jimimckay on 2013-03-11
Thanks a lot, I just don't really get how you add a new cell/ row for a new plant for example, and move everything accordingly. I see what you mean about 'linking', but that's really what I want, since no calculations are required at the moment. All I want is to sort an entire row based on the first cell (alphabetical). It's probably really easy, but I'm not convinced by my poor attempts!

---

### Post by Zill on 2013-03-11
jimimckay:  First, to avoid any confusion, a spreadsheet consists of horizontal **rows** (indicated by *numbers* on the left-hand side) and vertical **columns** (indicated by *letters* at the top).  Within the spreadsheet you will have **cells** containing your data.  You can enter your data into cells anywhere in the spreadsheet but traditionally we start at the top left hand corner and then work down or right entering new data into rows or columns as appropriate.

If you wish to add new data to existing data then you have two options.  One option is to create a new row in the desired location and this is easily done left-clicking on the appropriate row number to select the entire row.  Then right-click on the row number and select "insert rows" to produce a new row.  Note that this will move *all* the rows (including data in other columns) beneath to make room for the new row.

The other option is to add your new data to the bottom of the existing data.  If you then wish to sort all the data to move the new data to the "right" position (eg alphabetically) you can simply highlight *all* your data (with the mouse) and then use the sort buttons at the top of the spreadsheet application to sort to your desired order.

Both these techniques work for both rows and columns so just play around with some dummy data and all should become clear. :-)

---

### Post by jimimckay on 2013-03-13
Hi Zill,

Thanks a lot for taking the time to respond in detail to my query. I haven't used a spreadsheet for years and it's taking me a while to get used to it again. I've tried what you suggest, and it's no problem, the column sorts alphabetically fine. The problem I have is that when I add a new item to the list the data in the following column stays where it is, but the new plant name is moved into its corresponding position in the list. Adding a new row doesn't help me, because it moves everything down, but the data in the adjacent columns doesn't move to the appropriate position. I asked another user about 'linking' cells, but I was told that this isn't how spreadsheets work. Sorry I'm so slow on the upchuck, must be missing something!

Ciao,
Jimi.

---

### Post by jimimckay on 2013-03-13
Sorry Zill, just checked the thread and I saw it was you who told me that, hadn't noticed your username!

---

### Post by steeldriver on 2013-03-13
PMJI but I think what you're missing is that you need to select all the adjacent columns before performing the sort, then choose the plant name column as the one to sort with respect to

Here is a video I found that explains it pretty well - it is for a google docs spreadsheet but the principle is the same

[http://www.youtube.com/watch?v=2_LCvsk688k](http://www.youtube.com/watch?v=2_LCvsk688k)

---

### Post by jimimckay on 2013-03-13
Hi steeldriver,

Thanks a lot; that seems to be doing exactly what I want. In fairness, I think two other users were trying to tell me the same thing, but I reckon I was doing something wrong in the sort options!

A great help,
cheers,
Jimi.

---

### Post by Zill on 2013-03-13
jimimckay:  The important thing to know is that spreadsheet functions work *only* on the cells that are *highlighted*.  You can select an entire **row** by clicking on the **row number** at the left or you can select an entire **column** by clicking on the **column letter** at the top.

If you don't wish to select an entire row or column then just highlight the entire area you wish to change with the mouse.

Hopefully, you have now got things working but if not then please advise.

---

### Post by Zill on 2013-03-13
jimimckay:  Just for clarification, I attach some screendumps showing how to insert a new row of data to your desired position:
[LIST=1]
[*]Original sheet.png
[*]Highlight row.png
[*]Insert row.png
[*]New row appears.png
[*]New data added.png
[/LIST]

---

