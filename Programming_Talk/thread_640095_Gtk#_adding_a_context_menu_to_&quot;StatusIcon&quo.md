---
title: "Gtk# adding a context menu to &quot;StatusIcon&quot;"
date: 2007-12-13
forum: Programming Talk
---

### Post by sillv0r on 2007-12-13
I'm trying to have a menu pop-up from when the user right clicks on the status icon.  The icon shows up fine in gnome but the menu doesn't show.  The console write works, so i know the event is getting fired.  

Perhaps this has to do with the click event being perform async to the gui thread?  If so, anyone know a good solution?

```
namespace Tempo.Client
{	
	public class Program
	{		
		public static void Main()
		{			
			Gtk.Application.Init ();
			
			//
			//  Creating status icon.
			//
			Program.notification = Gtk.StatusIcon.NewFromStock(Gtk.Stock.Info);
			
			//
			//  Registering method for callback.
			//
			Program.notification.PopupMenu += Program.onRightClick;
			
			//
			//  Creating menu and adding items to it.
			//
			Program.contextMenu = new Gtk.Menu();
			Program.contextMenu.Add(new Gtk.MenuItem("option one"));
			Program.contextMenu.Add(new Gtk.MenuItem("option two"));
			
			Gtk.Application.Run ();
		}	
		
		private static void onRightClick(object sender, Gtk.PopupMenuArgs evt)
		{
			System.Console.WriteLine("testing");
			
			//
			//  Args[0] == button clicked &&   Args[1] == Active Time?
			//		
			Program.notification.PresentMenu(Program.contextMenu, (uint)evt.Args[0], (uint)evt.Args[1]);
		}
		
		private static Gtk.StatusIcon notification;
		private static Gtk.Menu contextMenu;
	}	
}
```

EDIT: Gtk# 2.10

---

### Post by sillv0r on 2007-12-14
Hrms, it doesn't look like it's the threading issue since the below didn't work either.

```
Gtk.Application.Invoke(
			    delegate(object sender2, System.EventArgs args)
			    {
				    System.Console.WriteLine("my delegate is being run.");
					//
					//  Args[0] == button clicked &&   Args[1] == Active Time?
					//		
					Program.notification.PresentMenu(Program.contextMenu, (uint)evt.Args[0], (uint)evt.Args[1]);
			     });
```

Note that the text was printed to the console and the menu still isn't showing. =[

---

### Post by drphrozen on 2009-11-25
I had the same problem as you but solved it by adding showAll before PresentMenu:
```

popupMenu.ShowAll();
trayIcon.PresentMenu(popupMenu, (uint)args.Args[0], (uint)args.Args[1]);

```

I know this is an old post, but maybe someone else has the same problem.

Cheers

---

