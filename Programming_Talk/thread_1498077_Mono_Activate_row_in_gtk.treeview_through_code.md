---
title: "Mono: Activate row in gtk.treeview through code"
date: 2010-05-31
forum: Programming Talk
---

### Post by lexe-cc on 2010-05-31
Hi,

I'm having trouble selecting and activating a row in a treeview widget. I'm using GTK# with monodevelop.
This is the code i use, but nothing happens ..

```

oLib.sSearchFilter = dlgSearch.GetInput();
					
TreeIter iter;
tvwTree.Model.GetIterFirst(out iter);
for (int i = 0; i < tvwTree.Model.IterNChildren(); i++)
{
	if (tvwTree.Model.GetValue(iter, 0).ToString().Contains("Search"))
	{
		tvwTree.Model.SetValue(iter, 0, "[Search=''" + dlgSearch.GetInput() + "'']");
		break;
	}
	tvwTree.Model.IterNext(ref iter);
}
					
tvwTree.ActivateRow(tvwTree.Model.GetPath(iter), tvwTree.Columns[0]);

```

The last line is the method I need (at least I think so). I'm sure the TreeIter is correct and the column is correct as well. The model used for this treeview is a ListStore with only one column ..
Anyone any thoughts?

Thanks in advance!
Lexe

---

### Post by JwB Zoofware on 2010-06-01
Try something like:

```
tvwTree.Selection.SelectIter(iter)
```

---

