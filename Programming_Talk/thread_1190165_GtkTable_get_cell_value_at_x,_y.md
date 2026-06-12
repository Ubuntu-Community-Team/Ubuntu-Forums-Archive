---
title: "Gtk::Table get cell value at x, y"
date: 2009-06-17
forum: Programming Talk
---

### Post by froggyswamp on 2009-06-17
Folks,
in Java I had a JTable where to get the value of a given cell I just wrote:
Object value = jtable.getValueAt(x, y);
and that's it.
But there doesn't seem to be such a thing in Gtkmm..
Can anyone please show me a quick example?

---

### Post by Habbit on 2009-06-17
Well, a Gtk::Table is not comparable to a javax.swing.JTable. Its more like a JPanel with a GridLayout (or maybe GridBagLayout, I'm not that experienced). Maybe you should be using Gtk::TreeView?

---

### Post by froggyswamp on 2009-06-17
I'm sorry, I indeed have a Gtk::TreeView, I just called it "table" because I have to deal much with Java..
So how do I do it with a Gtk::TreeView?

---

### Post by simeon87 on 2009-06-17
Edit: nevermind, I had posted some Python code for x,y as mouse coordinates but you appear to be looking for row/column coordinates.

---

### Post by froggyswamp on 2009-06-17
uh... found out.. finally.. not as easy as in Java tough.

```

//DetailedTreeView extends Gtk::TreeView
bool DetailedTreeView::on_button_press_event(GdkEventButton* event) {

	Gtk::TreeModel::Path path;
	bool found = get_path_at_pos(event->x, event->y, path);

	if(!found) {
		return true;
	}

	Glib::RefPtr<Gtk::TreeModel> model = get_model();
	Gtk::TreeModel::iterator iter = model->get_iter(path);
	Gtk::TreeModel::Row row = *iter;
	Glib::ustring sValue = row[treeModelCR.colName];//that's it..
}

```

---

