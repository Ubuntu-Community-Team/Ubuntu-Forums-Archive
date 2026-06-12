---
title: "MonoDevelop: Problem With Loop"
date: 2007-06-13
forum: Programming Talk
---

### Post by WastingBody on 2007-06-13
```
for (int i = 0; i < map.mapObjects.tagTypes.Count; i++)
 {
	Gtk.TreeIter iter = tagListStore.AppendValues (map.mapObjects.tagTypes[i]);
	for (int x = 0; x < map.mapIndex.objectCount; x++)
	{
		if (map.mapObjects.tagTypes[i] == map.mapObjects.tagClass[x])
		{
			tagListStore.AppendValues (iter, map.mapFiles.name[x]);
		}
	}
 }
```
I am fairly new to development so take it easy. ;) The first loop, loops through all of the tag types for the map. When the tagClass equals the tagType I want to add it to the treeview, but it only wants to find the first match and not continue through the rest of the tags.

---

### Post by kknd on 2007-06-13
Put a **break;** after that. After a break;, it will exit the inner for and go to the outer.

---

