---
title: "Help me with actionscript 3"
date: 2008-03-07
forum: Programming Talk
---

### Post by kool_kat_os on 2008-03-07
Im am playing around with action script 3

here is the code: 
[PHP]import fl.events.*;
import flash.events.*;
import fl.data.DataProvider;

var dp1:DataProvider = new DataProvider();
dp1.addItem( { URLRequest:new URLRequest("http://www.mywebsite.com/") label: "Home Page" } );
dp1.addItem( { label: "page 1" } );
dp1.addItem( { label: "page 2" } );
dp1.addItem( { label: "page 3" } );
dp1.addItem( { label: "page 4" } );

List.dataProvider = dp1;

List.addEventListener(Event.CHANGE, Selected);
Button.addEventListener(MouseEvent.CLICK, Pressed);

function Selected(EVENT) :void {
	trace("You have selected: " + List.selectedItem.label);
}
function Pressed(MouseEvent) :void {
	trace("You have pressed: " + List.selectedItem.label);
	Button.addEventListener(MouseEvent.CLICK.label);
}
[/PHP]

how do i make it so that when you select an item in the menu (List) and press the button (Button) it goes to a specific link?

---

### Post by kool_kat_os on 2008-03-08
anyone?.....

---

### Post by Can+~ on 2008-03-08
I don't think there's a lot of AS3 developers around.

Maybe try at adobe's forum?

---

### Post by smartbei on 2008-03-08
Well, since there are not many AS3 developers around, as can+~ said, perhaps you could reduce your problem into something we can help you with - for example, if the problem is accessing the label of the currently selected item in the list, perhaps you could use a global variable that is update by the callback Selected, and acccessed by the callback Pressed.

Something I don't quite understand is why in the trace in Pressed you are printing the selected item in the list, rather than the button's label. Copy/Paste error?

---

### Post by monstrfolk on 2008-08-07
I know this thread is old but...

try navigateToURL or htmlText.

---

