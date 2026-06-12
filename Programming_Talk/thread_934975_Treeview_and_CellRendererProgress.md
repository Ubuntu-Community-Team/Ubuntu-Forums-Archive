---
title: "Treeview and CellRendererProgress"
date: 2008-10-01
forum: Programming Talk
---

### Post by lviggiani on 2008-10-01
Hi,
I have a treeview where a column is a progressbar (CellRendererProgress).
Is there a way to not show the progress bar for some nodes only? (see attached image).

Thanks in advance!

---

### Post by Zugzwang on 2008-10-01
Dear OP (original poster),

[LIST]
[*] The context of your post is not given. For example, make sure that for all programming related questions, you mention the used programming language (if applicable), the type of processors assembly code is intended to run on (for example, x86, 64 bit) and the dialect of the language you used (for example, for the programming language C, C99). In this case it seems like you forgot: [...**Which GUI library are you actually using? Eventually also state which programming language bindings you are using**...]
[/LIST]

---

### Post by lviggiani on 2008-10-01
Hi,I apologize for the incomplete post.

I'm programming with c# mono and gtk# libraries.
Here is the piece of code used:

```
Gtk.TreeView tgt = (Gtk.TreeView)output;
tgt.HeadersVisible = true;	
for(int co=tgt.Columns.Length-1; co>=0; co--)
	tgt.RemoveColumn(tgt.Columns[co]);
	
TreeViewColumn tvc = new TreeViewColumn();
CellRendererPixbuf cr = new CellRendererPixbuf();
tvc.PackStart(cr,false);
tvc.SetAttributes(cr, "pixbuf", 0);
				
CellRendererText crt = new CellRendererText();
tvc.PackStart(crt, true);
tvc.SetAttributes(crt, "text", 1);
tvc.Title = columnHeaders[0];
tgt.AppendColumn(tvc);
				
for (int co=1; co<columnHeaders.Length-1; co++)
	tgt.AppendColumn(columnHeaders[co], new CellRendererText(), "text", co+1);

CellRendererProgress crp = new CellRendererProgress();

tgt.AppendColumn(columnHeaders[columnHeaders.Length-1], 
                 crp, "value", columnHeaders.Length);
				
TreeStore store = new TreeStore (typeof (Gdk.Pixbuf),
                                 typeof (string),
                                 typeof (string),
                                 typeof (string),
                                 typeof (string),
                                 typeof (double),
                                 typeof (ResourceLink));
				
Gtk.Image img = new Gtk.Image();
				
TreeIter SCORMNode = store.AppendValues(img.RenderIcon(Stock.Directory, IconSize.SmallToolbar,null), "SCORM 2004 Lessons");
TreeIter OtherNode = store.AppendValues(img.RenderIcon(Stock.DialogInfo, IconSize.SmallToolbar,null), "Other resources");
				
for (int i=0; i < archives.Length; i++)
{	
	TreeIter iter = store.AppendValues (SCORMNode,
	                                    img.RenderIcon(Stock.Execute, IconSize.SmallToolbar,null),
	                                    archives[i].Substring(0,10) + "...",
	                                    "1.00 (draft)",
	                                    DateTime.Now.ToString("yyyy-MM-dd"),
	                                    "en-GB",
	                                    50d,
	                                    new ResourceLink());
}
tgt.Model = store;
tgt.ShowAll();
```

---

### Post by Zugzwang on 2008-10-01
Don't know much about Gtk, but my best bet would be to implement a custom Renderer which can render both Progress Bars and "nothing".

---

### Post by mike_g on 2008-10-01
I'm not sure what the C# binding for it would be but the progress bar should inherit [gtk_widget_hide](http://library.gnome.org/devel/gtk/2.6/GtkWidget.html#gtk-widget-hide).

---

### Post by lviggiani on 2008-10-01
Hi,
basing on Zugzwang suggestion, basically I wrote the following code:
```

	public class myCellRendererProgress : CellRendererProgress
	{
		protected override void Render (Drawable window, Widget widget, Rectangle background_area, Rectangle cell_area, Rectangle expose_area, CellRendererState flags)
		{
			if (this.Value>0) 
				base.Render (window, widget, background_area, cell_area, expose_area, flags);
		}
	}
```

I extend the CellRendererProgress class and override the Render method.
Well it works as long as this.Value is 0 or less as the base.Render method is not invoked. As soon as Value > 0 and base.Render is called, the application crashes. I've searched the web a little bit and it seems a bug in gtk# wrapper... so perhaps the only I can do is rewrite a progress bar drawing method rather than calling base.Render method.
Any other suggestion?

---

### Post by mike_g on 2008-10-01
Is it not possible to simply hide the widget? I havent toggled view states in gtk, but I have used it lots in Swing and found it to work very well.

Edit: my bad, gtkcellrendererprograss does not inherit gtkwidget, but it does inherit gtkcellrenderer which has a read/write propety called 'visible' [http://library.gnome.org/devel/gtk/2.14/GtkCellRenderer.html#GtkCellRenderer--visible](http://library.gnome.org/devel/gtk/2.14/GtkCellRenderer.html#GtkCellRenderer--visible)  which you should be able to use to show/hide it.

---

### Post by lviggiani on 2008-10-01
mmmm... I'm not sure I understand what you mean...

My need is not to display the progressbar at all when the value in iter collection is for example below a certain value (0 for example).
Have you got a sample dummy code?
Thanks

if I set it unvisible...

```
CellRendererProgress crp = new CellRendererProgress();
crp.Visible = false;
```

...it will not be displayed in any row.

---

