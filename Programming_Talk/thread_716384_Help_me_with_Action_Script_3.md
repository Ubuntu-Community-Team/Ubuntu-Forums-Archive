---
title: "Help me with Action Script 3?"
date: 2008-03-05
forum: Programming Talk
---

### Post by kool_kat_os on 2008-03-05
I am playing around with Adobe Flash CS3 and i am writing a simple Action Script...

here is the code:

[PHP]import fl.events.*;
import flash.events.*;
import fl.data.DataProvider;

var dp1:DataProvider = new DataProvider();
dp1.addItem( { label: "test item 1" } );
dp1.addItem( { label: "test item 2" } );
dp1.addItem( { label: "test item 3" } );
dp1.addItem( { label: "test item 4" } );
dp1.addItem( { label: "test item 5" } );
dp1.addItem( { label: "test item 6" } );

List1.dataProvider = dp1;

List1.addEventListener(Event.CHANGE, announceSelect);
Button1.addEventListener(MouseEvent.CLICK, deleteItem);
Button2.addEventListener(MouseEvent.CLICK, duplicateItem);

function announceSelect(e:Event):void {
	trace("You have selected item: " + List1.selectedItem.label);
}
function deleteItem(e:MouseEvent):void {
	trace("You have removed item: " + List1.selectedItem.label);
	dp1.removeItem(List1.selectedItem);
}
function duplicateItem(e:MouseEvent):void {
	trace("You have duplicated item: " + List1.selectedItem.label);
	dp1.addItem(List1.selectedItem);
}[/PHP]

how do i make it so that a form can be used and you can add stuff from the form to the list???
(google didnt help)

i dont know if this question makes sense...

EDIT: should i devote my time to learning c++ or Action Script 3?

---

### Post by Acglaphotis on 2008-03-05
I'd say python, because the syntax is not too different from actionscripts and its a good start to programming : D.

---

### Post by kool_kat_os on 2008-03-05
> **Acglaphotis said:**
> I'd say python, because the syntax is not too different from actionscripts and its a good start to programming : D.

if programming is the way to go...then im sticking with c++

---

