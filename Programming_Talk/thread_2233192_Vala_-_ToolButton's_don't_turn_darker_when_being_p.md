---
title: "Vala - ToolButton's don't turn darker when being pressed"
date: 2014-07-07
forum: Programming Talk
---

### Post by slooksterpsv on 2014-07-07
EDIT: DELETE THIS POST - SOLVED!

It's the theme I'm using, ignore the rest!

--------------------------------------

It's me once again with yet another question.

When I click on my ToolButtons, they're not showing a darker grey like if I hold my mouse down on them. Here's a snippet of my code for creating the buttons. I have everything else set to just the connections for new, open, save, so any help would be awesome.

Thanks!

```

//Snippet

	var imgx = new Image.from_icon_name("document-new", IconSize.SMALL_TOOLBAR);

	var new_button = new ToolButton (imgx, null);
	//new_button.is_important = true;
	toolbar.add (new_button);
	new_button.clicked.connect (on_new_clicked);

	imgx = new Image.from_icon_name("document-open", IconSize.SMALL_TOOLBAR);

        var open_button = new ToolButton (imgx, null);
        //open_button.is_important = true;
        toolbar.add (open_button);
        open_button.clicked.connect (on_open_clicked);


```

The window is just a basic Window:

---

