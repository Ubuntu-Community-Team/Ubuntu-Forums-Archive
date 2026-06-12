---
title: "[Need Help]Table CELL select (jQuery or JavaScript)"
date: 2012-02-24
forum: Programming Talk
---

### Post by snowz on 2012-02-24
So i'm making something with the **HTML5/CSS3/jQuery/JavaScript **combination. A simple application which is including a table with many cells. 

I've been thinking about something like:

When you click a cell in the table, it gets added to selection of cells. The color of the cell border changes to lets say red. This means it is selected. So if you click multiple cells, they all get the red border color when being selected. Above the table there is a div, including buttons. Lets say we got 3 buttons. After you select the cells you want to edit, you press one of those buttons and the button adds a number/word in the html content of the cells that were selected. Example, button number one, adds the number 1 into every cell that was being selected.

Any idea how I would achieve that with either **jQuery or JavaScript**?

Appreciating every type of response ;)

---

### Post by snowz on 2012-02-24
Here is an explanation image, kind of :)

[IMG]http://shrani.si/f/1D/ZW/4Rw4Pjl1/buttonclick.png[/IMG]

And yeah, after you click the button, the selected cells would get deselected.

---

### Post by Dimarchi on 2012-02-25
You need to mess up with events (addEventListener, JQuery or plain Javascript way).

That event listener - click, I guess - is tied up to the table element (and its id, I suppose...could be class or some other way used to identify the needed table). Once you click a cell, or anything in that table, really, the event fires up the function tied to the event. The function should check whether the clicked piece is a table cell and then do stuff. Let's say this stuff is adding a class called "selected" to the clicked table cell. In your CSS that class .selected describes the border colour of red. Do note that there can be several class names, like:

```

<td class="selected someotherclassname andmore">

```But in the example case you described even one would suffice. There is no need to add these things into arrays or some other variable which you use to follow which items have been clicked and which have not been clicked.

Now, when you click one of the buttons of your example, that in turn executes another function. That function goes through every cell of the table and checks whether it has the class name of selected. If it has the desired class name, the function in that case copies the content of the cell (using innerHTML, or some of the other ways to copy the content of the cell) and adds in the example of button number one 1 to the contents of that cell, and follows it by writing the new content back to the cell's content, overwriting or replacing the old cell content...again using innerHTML and the like. After the content modification stuff is done, the function will remove the class name of selected from the cell's class name list (which can be just selected, in which case just remove class attribute completely).

---

### Post by snowz on 2012-02-25
Thank you :)

---

