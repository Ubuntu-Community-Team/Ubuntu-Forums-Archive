---
title: "simple Java question about comboboxes"
date: 2011-08-02
forum: Programming Talk
---

### Post by WinterMadness on 2011-08-02
Hey there, I just want to know how to add an item from the combo box's text.

For example, lets say the program just has a combobox ad nothing more on the screen, the user types in the combobox, and then hits enter and then the text the user typed gets added into the combobox its self. The code for hitting enter is not important here.

It seems like the code should be this.jCombobox1.addItem(this.jCombobox1.getText);
but obviously it isnt.

How would I do this? I really dont want to have to have an editable combobox AND a textfield...

---

### Post by Reiger on 2011-08-02
You need to get the item through the editor of the JComboBox:
```

Object item = comboBox.getEditor().getItem();

```

---

### Post by Zugzwang on 2011-08-03
EDIT: Never mind.

---

