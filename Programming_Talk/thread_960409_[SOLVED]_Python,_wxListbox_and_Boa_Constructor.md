---
title: "[SOLVED] Python, wxListbox and Boa Constructor"
date: 2008-10-27
forum: Programming Talk
---

### Post by MaxVK on 2008-10-27
Hi there. I'm *very* new to both Python and Boa Constructor and I'm in the process of experimenting with various controls. I have had some success with the Listbox control, but now I am trying to loop through the contents of the listbox, and hitting a problem.

How do I return the number of items in the listbox?

I want to loop through them so I am doing this:

for c in range(0, self.listBox1.Number()):
    ....
    ....

However, although I have read several documents about the listbox and the Number() object, Boa Constructor returns an error saying "*ListBox' object has no attribute 'Number'*"

I can add items to the list, read the selected item, but now I need to find out how many items there are!

Can anyone help out please.

Regards

Max

---

### Post by MaxVK on 2008-10-27
Okay, answered my own question so I thought Id post here for others:

It seems that Number() is not available, but GetCount() is, so that -

for x in range(self.listBox1.GetCount()):

will work nicely.

Its all a little confusing though, because there seems to be at least four different descriptions of the listbox and its properties and methods (only *some* of which actually work), and yet  none of them show GetCount() - I found this by accident while searching and its the only mention of GetCount() that Iv found so far!

Anyway.... onward!

regards

Max

---

