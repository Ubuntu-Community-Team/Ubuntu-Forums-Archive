---
title: "question about Google web kit tools"
date: 2012-12-31
forum: Programming Talk
---

### Post by oren tal on 2012-12-31
Hi,

I am using gwt and in the following library com.gwtext.client.widgets.grid.EditorGridPanel

I am using EditorGridPanel object.
Now, when I create the column model I use the following command:
```
CheckboxSelectionModel checkboxSelectionModel = new CheckboxSelectionModel();
CheckboxColumnConfig checkboxColumnConfig = new CheckboxColumnConfig( checkboxSelectionModel );
table.setSelectionModel( checkboxSelectionModel );
```

Now I do want to be able to click on a line without uncheck all the other lines, how can I do that?

---

