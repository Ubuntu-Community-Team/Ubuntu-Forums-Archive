---
title: "Gtk/Gtk# question"
date: 2005-10-16
forum: Programming Talk
---

### Post by mostwanted on 2005-10-16
The deal is, I'm trying to write a simple text-editor. When I use a TextView inside a ScrolledWindow, the ScrolledWindow doesn't automatically scroll down as new content is added at the end, which means you'll have to scroll down manually every time you write a new line.

I've tried hacking a solution together here like someone on #mono said I should do, but haven't had much luck. First of all, it scrolls to the bottom no matter what, doesn't matter if you're editing something 4 "pages" up... which sucks. Second of all, it doesn't count a single \n as changed content it seems so it's never completely scrolled down unless you write some characters.

I'm led to believe this way to go it completely wrong, does anyone know what to do? Doesn't matter if it's Gtk, Gtkmm or whatever you know.

```
using System;
using Gtk;

// A namespace with various classes to be used in a text-editing application
namespace TextEditing {
	
	// Main application, uses text-editing classes found in this namespace
	public class SmallTextEditor
	{	
		private Window app;
		private VBox mainBox;
		private ScrolledWindow scroll;
		private TextView textArea;
		private TextBuffer buffer;
		private Toolbar tools;
		private ToolButton newFileButton, openFileButton, saveFileButton;
		
		public SmallTextEditor(string[] args)
		{
			// Do useless stuff with the arguments (will be worked on later)
			foreach (string arg in args)
			{
				Console.WriteLine(arg);
			}
			
			Application.Init();
			
			// Window
			app = new Window("Small editor");
			app.DeleteEvent += new DeleteEventHandler(Exit);
			
			// Containers
			mainBox = new VBox(false, 0);
			scroll = new ScrolledWindow(null, null);
			scroll.SetPolicy(PolicyType.Automatic, PolicyType.Automatic);
			scroll.WindowPlacement = CornerType.BottomLeft;
			
			// Widgets
			textArea = new TextView();
			buffer = textArea.Buffer;
			buffer.Changed += new EventHandler(ScrollDown);
			//buffer.UserActionEnded += new EventHandler(ScrollDown);
			//buffer.UserActionBegun += new EventHandler(ScrollDown);
			tools = new Toolbar();
			
			newFileButton = new ToolButton(Stock.New);
			openFileButton = new ToolButton(Stock.Open);
			saveFileButton = new ToolButton(Stock.Save);
			
			
			// Adding to containers
			tools.Add(newFileButton);
			tools.Add(openFileButton);
			tools.Add(saveFileButton);
			
			scroll.AddWithViewport(textArea);
			
			mainBox.PackStart(tools, false, false, 0);
			mainBox.PackStart(scroll, true, true, 0);
			
			app.Add(mainBox);
			
			app.DefaultWidth = 400;
			app.DefaultHeight = 400;
			app.ShowAll();
			
			Application.Run();
		}
		
		public void ScrollDown(object obj, EventArgs args)
		{
			Console.WriteLine("adjusts");
			scroll.Vadjustment.Value = scroll.Vadjustment.Upper - scroll.Vadjustment.PageSize;
			
		}
		
		public void Exit(object obj, DeleteEventArgs args)
		{
			Application.Quit();
		}
	}
}

// Create an instance of the SmallTextEditor class
class UseTextEditing
{
	public static void Main(string[] args)
	{
		new TextEditing.SmallTextEditor(args);
	}
}

```

---

### Post by mostwanted on 2005-10-17
Come on, there has to be some Gtk+ programmers here who've dabbled with a simple text-editor at some point! :)

---

### Post by wmcbrine on 2005-10-17
There's an example editor mentioned in Devhelp, IIRC. Or you could grab the source for gedit. Sorry I can't be more help. I don't speak #, and I'm just starting in Gtk myself; so far I've only done a viewer, not an editor.

---

### Post by mostwanted on 2005-10-17
I actually tried looking at the gedit source, but it was waaay too big for me to be able to spot out where they did the basic graphics interface.

---

