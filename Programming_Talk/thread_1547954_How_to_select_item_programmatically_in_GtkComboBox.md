---
title: "How to select item programmatically in GtkComboBox (Python)?"
date: 2010-08-07
forum: Programming Talk
---

### Post by estiedi on 2010-08-07
Hi, 

I'm working on a program using Quickly, Python & Glade. 

I made a **Master/Detail window**: 
The master part is a TreeView with a list of persons (ID, firstname, name).
The detail part a frame with several widgets (mostly entry, combobox).

When the user selects a person in the master list, I display the persons details in the details frame to view and/or edit.

In the details frame I have a combo box with zip codes. 
I need to *set the zip code of the selected person programmatically*, but couldn't find a function in gtk.ComboBox or gtk.TreeModel that lets me do this easily.

My solution is to keep a separate list of zip codes through which I loop to find  the index of the zip code I need and then use the combobox's set_active(index) function.

This is the treeview event handler when the user selects another person: 
```

    def on_treeview1_cursor_changed(self, widget):
        model, it, = widget.get_selection().get_selected()
        val = model.get_value(it, 0)
        self.show_member_detail(val)

```The function that fills the detail frame with the selected person's details:
```

    def show_member_detail(self, member_nr):
        mbr = get_store().find(Member, Member.member_nr == member_nr).one() 
        self.builder.get_object('entry_firstname').set_text(mbr.firstname)       
        self.builder.get_object('entry_name').set_text(mbr.name)       
        combo_pc = self.builder.get_object('combobox_zipcode')
        combo_pc.set_active(get_zipcode_index(mbr.place.zipcode))
        self.builder.get_object('entry_address').set_text(mbr.address)
        self.builder.get_object('entry_email').set_text(lid.email)       
        self.builder.get_object('entry_tel1').set_text(lid.tel1)       
        self.builder.get_object('entry_tel2').set_text(lid.tel2)       

```This is the function that tries to find the index of the zip code
```

def get_zipcode_index(zipcode):
    places = get_store().find(Places)
    for zc in places:
        idx = idx + 1
        if zc.zipcode == zipcode
            return idx

```Is there any better way to do this? I could not find any hint on Google about this, so maybe I heading in the complete wrong direction.

Thx.

---

### Post by StephenF on 2010-08-07
To implement the interface you describe I would create a gtk.TreeRowReference for each zip code in the ComboBox. These references will go as the values of a dictionary so that a simple dictionary lookup of the currently set zip code can be used to obtain the TreeRowReference that tracks the ComboBox zip code.

Then the code would look something like
```

my_combo_box.set_active(my_dict[zip_code].get_path()[0])

```

---

### Post by km0r3 on 2010-08-07
> **estiedi said:**
> 
```

def get_zipcode_index(zipcode):
    places = get_store().find(Places)
    for zc in places:
        idx = idx + 1
        if zc.zipcode == zipcode
            return idx

```Is there any better way to do this? I could not find any hint on Google about this, so maybe I heading in the complete wrong direction.

Thx.

I recently had to do some searching over a GtkListStore and the approach is similar to yours. I have also done a lot of research on Google, but, just like you, I haven't found a lot of useful sites on the topic.

Personally, I think you're code is "a good way to do this".

Though, there's [one blog talking about Quickly projects]("http://theravingrick.blogspot.com/") and I found a code snippet which you might consider useful:

```
  def __new_filter_row(self, widget, data=None):
   """
   new_filter row - hack to allow naming of columns
   in a grid filter.

   This code works around:
   https://bugs.edge.launchpad.net/quidgets/+bug/587558

   """

   row = self.filt.rows[len(self.filt.rows)-1]
   row.connect("add_row_requested",self.__new_filter_row)
   model = row.column_combo.get_model()

   for i, k in enumerate(model):
       itr = model.get_iter(i)
       title = model.get_value(itr,0)
       if title == "name":
           model.set_value(itr,0,_("Name"))
       elif title == "priority":
           model.set_value(itr,0,_("Priority"))
       elif title == "due":
           model.set_value(itr,0,_("Due"))
       elif title == "project":
           model.set_value(itr,0,_("Project"))
       if title == "complete?":
           model.set_value(itr,0,_("Completed"))
```

P.S.: The blog I've linked to earlier is a **really** useful resource in my humble opinion.

---

### Post by estiedi on 2010-08-08
Thanks a lot, StephenF and km0r3.

I somehow missed the TreeRowReference class and the blog really looks great. I'm going to dig those deeper.

@km0r3:
I want to avoid looping through all the zip codes. As you can imagine there are many zip codes and the user might switch between persons a lot, so this could be a potential performance bummer. :???:
Even thinking whether a combobox is a good idea for zip codes after all. 

Many thanks for helping me finding the way.

Estiedi

---

