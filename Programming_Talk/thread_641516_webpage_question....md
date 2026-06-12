---
title: "webpage question..."
date: 2007-12-15
forum: Programming Talk
---

### Post by hockey97 on 2007-12-15
How can I  create  a boarder around a image to use my own art as the border??

I have seen some websites doing this. 

they also do it to video. 

I have seen one place have a picture if a tv but cut our the screen of the tv and on their website played the video file where the screen was cut out makes it look as if your watching tv.

Is this done in flash?? or can this be done with just code?

---

### Post by LaRoza on 2007-12-15
It was probably flash or an applet.

If you have artistic ability, or the image you want as the border, you can make the center colour transpartent, and use CSS to put your image there. 

Or you can put the image on top and align it right so the bottom image looks like a border.

---

### Post by Wybiral on 2007-12-15
You can either make the center transparent as LaRoza said, or you can split your image into four rectangles and use a table to align them all.

---

### Post by LaRoza on 2007-12-15
> **Wybiral said:**
> You can either make the center transparent as LaRoza said, or you can split your image into four rectangles and use a table to align them all.

The table idea would probably work best in all browsers. Make sure to use CSS to get rid of borders and other default browser behavior you don't want.

---

### Post by hockey97 on 2007-12-15
SO I can do something like that in css?

I plan to create a picture that inside the picture I created I want to display ads on it.

so it looks like that ads is part of the website.

an example  look on this website  [http://www.xgamestation.com/](http://www.xgamestation.com/)    their is a slideshow of pics on what looks like a computer chip.

Would I be able to create somthing like that??

---

### Post by LaRoza on 2007-12-15
They use the table method, I believe:


[img]http://www.xgamestation.com/gfx/welcome_top.gif[/img]

[img]http://www.xgamestation.com/gfx/welcome_bottom_v2.gif[/img]

[img]http://www.xgamestation.com/gfx/welcome_right.gif[/img]

[img]http://www.xgamestation.com/gfx/welcome_left.gif[/img]

They stick the contents in the middle cell.

```

<table>
<tr>
<td colspan="3"><img /></td>
</tr>

<tr>
<td><img /></td>
<td><object /></td>
<td><img /></td>
</tr>

<tr>
<td colspan="3"><img /></td>
</tr>
</table>

```

Use CSS to alter the height and width.

---

### Post by hockey97 on 2007-12-15
ok I now understand how I can do it.  Thanks.

---

### Post by Wybiral on 2007-12-15
There is no flash in that example. It's just an image inside the table (using the other images for the frame).

---

### Post by hockey97 on 2007-12-15
Is their any free paint program somthing like photoshop or somthing where I can create my art in?

I have blender 3d downloaded and plan to use that for my 3d art.

---

### Post by Majorix on 2007-12-15
Of course there is, it is called GIMP.

---

### Post by hockey97 on 2007-12-15
but isn't gimp just a image enhancer?? 

I looked at the site and seen only real photos being edited with special effects.

ps. Like your avatar stewie lol my fav.

---

### Post by Majorix on 2007-12-15
You can still use GIMP for simple tasks like drawing, painting etc. Though I have never used it in that way. But there are plenty of tutorials online that would help you get going with GIMP in no time.

And thanks about the compliment, he IS t3h ownage :D

---

### Post by LaRoza on 2007-12-15
[http://www.linfo.org/software_artists.html](http://www.linfo.org/software_artists.html)

---

