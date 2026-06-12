---
title: "VB.net"
date: 2008-04-28
forum: Programming Talk
---

### Post by cartisdm on 2008-04-28
I have a listbox with a set of data in it that I pulled in from a text file.  It's a basic list, one item per line.  On click of a button I'm trying to display a messagebox that gives the contents of the list box, also one item per line.  Any help?  

This is what I have so far (I know it's not much)

```
MessageBox.Show("All your sports are ", sportListBox.Items, MessageBoxButtons.OK)
```

---

### Post by Hyperkill on 2008-04-28
> **cartisdm said:**
> I have a listbox with a set of data in it that I pulled in from a text file.  It's a basic list, one item per line.  On click of a button I'm trying to display a messagebox that gives the contents of the list box, also one item per line.  Any help?  

This is what I have so far (I know it's not much)

```
MessageBox.Show("All your sports are ", sportListBox.Items, MessageBoxButtons.OK)
```

I haven't programmed in VB in years but if I'm not mistaken you have to provide an index in order to do this.  What you should probably do is use a for..next loop and grab each item.  Indexes start with 0 so the first item will have an index of that.  Sorry if I am no help but maybe it's a step in the right direction.

---

### Post by skeeterbug on 2008-04-28
Hyperkill is right. You will have to iterate over sportListBox.Items, and perhaps build a string from that?

in C# it would look like so:

```

ListBox sportListBox = new ListBox();
string allItems = "";
foreach (ListItem li in sportListBox)
{
    //Append each item here
}

//Display the "allItems" string in the messagebox

```

---

