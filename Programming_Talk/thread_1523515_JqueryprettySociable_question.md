---
title: "Jquery/prettySociable question"
date: 2010-07-03
forum: Programming Talk
---

### Post by tlwstooge on 2010-07-03
'm currently using [prettySociable](http://www.no-margin-for-errors.com/projects/prettysociable-mashable-like-sharing/) on my website. I've edited the css to give it a bit of my own twist, but what I really want to do is change the way the tooltip (when dragging) defaults to the browser title. Instead, I'd sooner have an image in there. I *think* I've found the code I need to edit (the source can be downloaded from the above link. I use the uncompressed version) on line 265, which looks like this:

```
// If no defined title, take the page title
					desc = ($('meta[name=Description]').attr('content')) ? $('meta[name=Description]').attr('content') : "";
					if(attributes.length==1) {
						attributes[1] = ['title',document.title];
						attributes[2] = ['excerpt',desc];
					}
```

Is there any simple way to get it to show an image as the default, rather than the page title? 

Any help is gratefully received

---

### Post by tlwstooge on 2010-07-04
I had this suggested to me:

> Line 288 renders the content.

```

$(ps_tooltip).find('.ps_s').html("<p><strong>" + attributes[1][1] + "</strong><br />" + attributes[2][1]+"</p>");

```


Change out **attributes[1][1]** to an HTML image tag:

```

$(ps_tooltip).find('.ps_s').html("<p><strong>" + "<img src="images/someimage.gif" /> " + "</strong><br />" + attributes[2][1]+"</p>");

```

However, the bottom code gives me a syntax error on 288. Anybody know why that's doing that?

---

### Post by tlwstooge on 2010-07-04
Just incase anybody from the future is reading this, here is the working code

```
$(ps_tooltip).find('.ps_s').html("<p><strong>" + "<img src='http://url.com/image.png'> " + "</strong><br />" + attributes[2][1]+"</p>");
```

---

