---
title: "Passing information from one window to another"
date: 2009-05-14
forum: Programming Talk
---

### Post by PaulM1985 on 2009-05-14
Hi

I am trying to create a program using C# with a GUI but I am unsure on how to pass information from one window to another.

For example, I have a window with a select file button, and a label that displays the file name.

Clicking on the button opens another window where the user can choose the file name.

How do I make the select file button method update the label displaying the file name?  I need it to wait for something to be returned after calling the file chooser window.

I'm thinking threading somehow, but I am not sure what exactly I need to thread.

Any advice would be appreciated.  Thanks

Paul

---

### Post by galileon on 2009-05-14
Never used c~. if it's Object oriented, your FileChooserDialog could be an object that returns a string, when you click select.

---

### Post by PaulM1985 on 2009-05-14
Thats the thing.  I need to wait for the user to choose the file before the function returns a string of the path.  How do I wait?  That is why I thought of threading, but I am not sure where the thread should go exactly.

Paul

---

### Post by galileon on 2009-05-14
No, you won';t need threading for this, there should be a way to make the dialog "modal" or "application modal", ie make it take focus, and keep it until its closed.

when it's destroyed, it should return your string containing the path.. sorry i havent done any c#, so i can;t help more...

edit: google found this for me: [http://msdn.microsoft.com/en-us/library/bb383855.aspx](http://msdn.microsoft.com/en-us/library/bb383855.aspx)

edit2: [http://www.c-sharpcorner.com/UploadFile/DipalChoksi/PassingDataBetweenaWindowsFormandDialogBoxes11242005035025AM/PassingDataBetweenaWindowsFormandDialogBoxes.aspx](http://www.c-sharpcorner.com/UploadFile/DipalChoksi/PassingDataBetweenaWindowsFormandDialogBoxes11242005035025AM/PassingDataBetweenaWindowsFormandDialogBoxes.aspx)

edit3: [http://ww.functionx.com/vcsharp2003/Lesson06.htm](http://ww.functionx.com/vcsharp2003/Lesson06.htm)

---

