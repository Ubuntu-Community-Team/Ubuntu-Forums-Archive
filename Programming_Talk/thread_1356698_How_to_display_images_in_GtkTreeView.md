---
title: "How to display images in GtkTreeView"
date: 2009-12-16
forum: Programming Talk
---

### Post by bluedalmatian on 2009-12-16
Im using a GtkTreeView with a GtkListStore to display a list of rows with both text and a picture.

I can declare the model with just the text as follows:

```
lhs_store=gtk_list_store_new(1,G_TYPE_STRING,); //1 cols(string)
```

but how do I decalre it to have a picture as well e.g the following- which doesnt work. What type do I use for the second col?

```
lhs_store=gtk_list_store_new(2,G_TYPE_STRING,G_TYPE_PIXBUF); //2 cols, 1st is string, 2nd is icon
``` 

I can then add the text to the model easily with

```
gtk_list_store_set(lhs_store,&lhs_treeiter,0,"Subscribers",-1); //put string in col0
```

what I also want to do is put an image file in the other column

I know how to set up a pixbuf renderer in the view to display it but I cant find an example showing how to store images in the model.

---

