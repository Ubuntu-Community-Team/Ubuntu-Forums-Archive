---
title: "Java Combobox to get drive mount points."
date: 2009-03-28
forum: Programming Talk
---

### Post by Joanofarc on 2009-03-28
Does anyone know how to take the results from 

```
File[] roots = File.listRoots();
```

That. And put the items into a java combo box? I'm using netbeans, and the newest JDK. I've googled up and down with no luck.

---

### Post by myrtle1908 on 2009-03-28
Off the top of my head (untested) ...

[PHP]
File[] roots = File.listRoots();
JComboBox cb = new JComboBox();
for (int i=0; i<roots.length; i++) {
  cb.addItem(roots[i].getName());
}
[/PHP]

---

### Post by HotCupOfJava on 2009-03-28
You can actually pass an array of type Object to the JComboBox constructor. Since File is a subclass of Object (pretty much everything is), you can pass it the File[] array.

[PHP]File[] roots = file.listRoots();
JComboBox cb = new JComboBox(roots);[/PHP]

In NetBeans you use the "custom creation code" option in the "code" section for the JComboBox you created to do this.

Or you can do like the above poster and load the items individually AFTER construction.

Note: the JComboBox uses any Object's toString() method to display it in the JComboBox. In the case of File, it will show the FULL pathname. If you want something shorter, you will have to subclass File and override the toString() method. Then use your subclass to create the array.

---

