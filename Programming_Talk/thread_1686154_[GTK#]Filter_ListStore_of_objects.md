---
title: "[GTK#]Filter ListStore of objects"
date: 2011-02-11
forum: Programming Talk
---

### Post by Moustacha on 2011-02-11
Hi, I'm having problems with filtering a ListStore of custom objects in c#/mono.

I've got it working to add and display the objects with their data in two columns (title and path).
What I would like to do is use a text entry field to filter the TreeView.
I've followed the logic from the [TreeView examples](http://www.mono-project.com/GtkSharp_TreeView_Tutorial#Filtering_Data) but it doesn't work for me.
I've got my objects in the ListStore. I then set up the filter with my ListStore as what is to be filtered. Now here is where the problems start. If I connect the ListStore to the TreeView as the model, the filter function works. I know this won't affect what is being displayed, but it shows that the function logic is correct.
When I connect the filter as the TreeView's model I start getting errors in the filter function.
```
: Gtk-CRITICAL **: gtk_list_store_get_value: assertion `VALID_ITER (iter, list_store)' failed

: GLib-GObject-CRITICAL **: g_value_unset: assertion `G_IS_VALUE (value)' failed
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
```

From what I understand when I try and get an object from the local reference to the model it goes crazy with NullReferenceExceptions. It doesn't give me a chance to catch them, it seems to be coming from GetValue().

So to the actual question, how can I filter my objects using a TreeModelFilter that is connected to a ListStore and TreeView?

Here are the relevant parts of code
```
movieList = new ListStore(typeof (Movie));

...

filter = new TreeModelFilter(movieList, null);
		filter.VisibleFunc = new TreeModelFilterVisibleFunc(FilterTitle);
		
		movieView.Model = movieList;

...

private bool FilterTitle (Gtk.TreeModel model, Gtk.TreeIter iter)
	{
		Movie tempMovie = (Movie)model.GetValue(iter, 0);
		if(tempMovie == null)
		{
			return false;
		}
		else
		{
			string title = tempMovie.Title;
			if(searchbar.Text == "")
			{
				movieList = (ListStore)model;
				return true;
			}
			if(title.IndexOf(searchbar.Text) > -1)
			{
				Console.WriteLine("{0} is in {1}", searchbar.Text, title);
				movieList = (ListStore)model;
				return true;
			}
			else
			{
				Console.WriteLine("{0} is NOT in {1}", searchbar.Text, title);
				movieList = (ListStore)model;
				return false;
			}
		}
	}
```

---

### Post by Moustacha on 2011-02-13
I figured out how to solve it.

Assign the ListStore as the model to the TreeView.
Then once the application has started, assign the filter to the model of the TreeView.
For some reason it stops throwing errors and works as expected.

---

