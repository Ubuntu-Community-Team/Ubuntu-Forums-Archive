---
title: "GTK, C# question"
date: 2005-12-14
forum: Programming Talk
---

### Post by DaMasta on 2005-12-14
Teaching myself some GTK and C# using monodevelop. I created a button and would like to change a label's text when clicked. Here's what I have.

```

using System;
using Gtk;

class buMain {

	static void Main() 
	{
		Application.Init();
		Window mainWindow = new Window("Easy Backup");
        mainWindow.DeleteEvent += new DeleteEventHandler (delete_backuputil);
        mainWindow.SetDefaultSize (200, 150);
		VBox mbBox = new VBox(false,2);
//Creates a menubar		
		MenuBar mb = new MenuBar();
//Stars the file portion of the menubar
		Menu file_menu = new Menu();
//Creation of the open option and then appends the open option to the file portion
		MenuItem open_item = new MenuItem("Open...");
		file_menu.Append(open_item);
//Creation of the exit option and then appends the exit option to the file portion
		MenuItem exit_item = new MenuItem("Exit");
		file_menu.Append(exit_item);
		exit_item.Activated += new EventHandler (exit_backuputil);
		MenuItem file_item = new MenuItem("File");
		file_item.Submenu = file_menu;

//Stars the edit portion of the menubar
		Menu edit_menu = new Menu();
//Creation of the policy option and then appends the policy option to the edit portion
		MenuItem policy_item = new MenuItem("Policy...");
		edit_menu.Append(policy_item);
		MenuItem edit_item = new MenuItem("Edit");
		edit_item.Submenu = edit_menu;		
				
		mb.Append(file_item);
		mb.Append(edit_item);		
		mbBox.PackStart(mb, false, false, 0);
		Label testLabel = new Label("no");
		mbBox.PackStart(testLabel, false, false, 0);
		Button testButton1 = new Button("testing1");
		testButton1.Clicked += new EventHandler(change_label);
		mbBox.PackStart(testButton1, false, false, 0);
		Button testButton2 = new Button("testing2");
		mbBox.PackStart(testButton2, true, true, 0);		 
		mainWindow.Add(mbBox);
		mainWindow.ShowAll();
		Application.Run();
	}
     static void change_label (object obj, EventArgs args)
     {
           testLabel.Text = "Yes!";
     }	
     static void delete_backuputil (object o, DeleteEventArgs args)
     {
          Application.Quit ();
     }	
     static void exit_backuputil (object o, EventArgs args)
     {
          Application.Quit ();
     }	
} 

```
And here is the error:
backuputil.cs(53,11): error CS0246: The type or namespace name `testLabel' could not be found. Are you missing a using directive or an assembly reference?
backuputil.cs(53,11): error CS0103: The name `testLabel' does not exist in the context of `buMain'
Compilation failed: 2 error(s), 0 warnings

---

### Post by fct on 2005-12-14
Your problem is that "testLabel" is declared in the Main() function. But that means it's a local variable, that can't be seen from functions other than Main() (as is the case with "change_Label").

You have two different solutions:

- The best one would be to declare testLabel as a property of class buMain (that is, for example, before the declaration of the Main() method). That way it would be available to any function inside buMain.

- Use GTK# functions to check for the label by travelling through all the tree structure that defines the window and its contents (unnecessary here, and worksome).

---

### Post by dogen on 2005-12-14
Yes, as fct says, the function change_label has no idea what testLabel is because it doesn't exist within its scope when change_label attempts to reference it. 

It only exists within Main, which doesn't make it global to the class and doesn't make it visible to change_label.

---

### Post by DaMasta on 2005-12-14
Ok, so how would I go about doing this. I read there is no global variables in C#. I appreciate both of your help.

---

### Post by fct on 2005-12-15
```
using System;
using Gtk;

class buMain {
**	Label testLabel;**

	static void Main() 
	{
		Application.Init();
		Window mainWindow = new Window("Easy Backup");
        mainWindow.DeleteEvent += new DeleteEventHandler (delete_backuputil);
        mainWindow.SetDefaultSize (200, 150);
		VBox mbBox = new VBox(false,2);
//Creates a menubar		
		MenuBar mb = new MenuBar();
//Stars the file portion of the menubar
		Menu file_menu = new Menu();
//Creation of the open option and then appends the open option to the file portion
		MenuItem open_item = new MenuItem("Open...");
		file_menu.Append(open_item);
//Creation of the exit option and then appends the exit option to the file portion
		MenuItem exit_item = new MenuItem("Exit");
		file_menu.Append(exit_item);
		exit_item.Activated += new EventHandler (exit_backuputil);
		MenuItem file_item = new MenuItem("File");
		file_item.Submenu = file_menu;

//Stars the edit portion of the menubar
		Menu edit_menu = new Menu();
//Creation of the policy option and then appends the policy option to the edit portion
		MenuItem policy_item = new MenuItem("Policy...");
		edit_menu.Append(policy_item);
		MenuItem edit_item = new MenuItem("Edit");
		edit_item.Submenu = edit_menu;		
				
		mb.Append(file_item);
		mb.Append(edit_item);		
		mbBox.PackStart(mb, false, false, 0);
[B]		// Don't declare this here, do it in the class scope
		// Label testLabel = new Label("no");
		testLabel = new Label("no");
[/B]		mbBox.PackStart(testLabel, false, false, 0);
		Button testButton1 = new Button("testing1");
		testButton1.Clicked += new EventHandler(change_label);
		mbBox.PackStart(testButton1, false, false, 0);
		Button testButton2 = new Button("testing2");
		mbBox.PackStart(testButton2, true, true, 0);		 
		mainWindow.Add(mbBox);
		mainWindow.ShowAll();
		Application.Run();
	}
     static void change_label (object obj, EventArgs args)
     {
           testLabel.Text = "Yes!";
     }	
     static void delete_backuputil (object o, DeleteEventArgs args)
     {
          Application.Quit ();
     }	
     static void exit_backuputil (object o, EventArgs args)
     {
          Application.Quit ();
     }	
} 
```

---

### Post by DaMasta on 2005-12-15
Yeah, I tried it that way and it spits out:

burerun.cs(42,3): error CS0120: `testLabel': An object reference is required for the nonstatic field, method or property
burerun.cs(43,19): error CS0120: `testLabel': An object reference is required for the nonstatic field, method or property
burerun.cs(55,12): error CS0120: `testLabel': An object reference is required for the nonstatic field, method or property
Compilation failed: 3 error(s), 0 warnings

---

### Post by fct on 2005-12-15
try:

.......
class buMain {
	**static** Label testLabel;
.......

But the thing is that you should watch some more examples. Usually you don't init widget properties in Main(), but in the class constructor.

---

### Post by DaMasta on 2005-12-15
[QUOTE=fct]try:

.......
class buMain {
	**static** Label testLabel;
.......

But the thing is that you should watch some more examples. Usually you don't init widget properties in Main(), but in the class constructor.[/QUOTE]
Yep, that worked. Thanks fct. I'm learning as I go. I really appreciate your help.

---

