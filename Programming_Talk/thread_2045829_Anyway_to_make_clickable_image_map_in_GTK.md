---
title: "Anyway to make clickable image map in GTK"
date: 2012-08-22
forum: Programming Talk
---

### Post by anewguy on 2012-08-22
I'd like to be able to have a clickable image map in GTK so the user can just click different places on the image to bring up different options to change.  Is a clickable image map possible in GTK?


EDIT:  I found something in the devhelp about something called the application tool kit and it mentions some id for a clickable image map, but I can't find anything to explain this to me and how to create the image map to begin with.  Completely new at this part.

---

### Post by mehaga on 2012-08-22
> **anewguy said:**
> I'd like to be able to have a clickable image map in GTK so the user can just click different places on the image to bring up different options to change.  Is a clickable image map possible in GTK?


EDIT:  I found something in the devhelp about something called the application tool kit and it mentions some id for a clickable image map, but I can't find anything to explain this to me and how to create the image map to begin with.  Completely new at this part.


What exactly do you mean by 'image map'? Do you want to use a single image and somehow recognize which part of it was clicked, or do you want to use multiple images and react to a click on one of them? If it's a single image, you'll want to handle a mouse click event, get the mouse position and translate that to position on the image, i.e. figure out which region was clicked. You'll have to code the mapping of 'places' somehow, maybe have a collection of rectangles and check which rectangle contains the point mouse was clicked at. 
If you can use multiple images, then it will be easier. Just use a bunch of image widgets (Gtk.Image, I guess) and handle click events on them. You can put them in a layout, e.g. HBox, so that they look like a single image...

This might not be terribly helpful, but any reply is better than no reply, right? :D

---

### Post by anewguy on 2012-08-22
Thanks for the reply!  I had given thought to the multiple image boxes, but thought that would be very difficult to setup considering some of the things I would like to try to do.  I saw that adk thing in devhelp where it lets an item be defined as a clickable image map, however I have found nothing in the devhelp or online for help/examples of using the application development kit.  It sounds as if you end up mapping this to a gtk object.  But without information and perhaps some samples, I have no clue how to use it or code for it.

Yep, I want an image (in my case a screen shot of the Ubuntu desktop) and need the program to react to which area in the image was clicked - like an image map on the net. I really would like to be able to show the image of the desktop, pop text up when the mouse is over certain places of the image and react to a mouse click on the same area.  I don't see any such thing in GTK, nor do I have any idea how I would "link" the image map to an image and detect mouse movements/clicks.  The coding, in terms of box definitions, image definitions, image actions such as mouse-over or click would be much smaller and easier to manage if there were some way to map the clickable areas of an image in GTK.

---

### Post by DarkAmbient on 2012-08-22
Such functionality doesn't seem to exist withing gtk, sadly enough.

But in case you use a single static screenshot of the Ubuntu-desktop, then perhaps you could retrieve mouseposition and check if the user is clicking in some essential location?

Check this tutorial on how to get coord. of mouse.
[http://developer.gnome.org/gtk-tutorial/stable/c2422.html](http://developer.gnome.org/gtk-tutorial/stable/c2422.html)

---

### Post by anewguy on 2012-08-22
Hummmm, that sounds promising.  I'm not that great with GTK yet and I didn't know there were attributes like x/y you could get when the mouse is clicked on an image.  I'll look into that!

I'm not really familiar with image maps anyway, so perhaps this will be easier for me.

Thanks again!

Dave ;)

---

### Post by alexfish on 2012-08-22
you need to place the image into an event box
something like:
```
	image = gtk_image_new_from_file("/path/to/file")
	ebox = gtk_event_box_new()
	gtk_container_add(ebox, image)

	gtk_widget_queue_draw(image)
	
	gtk_widget_set_events(ebox, GDK_POINTER_MOTION_MASK | GDK_KEY_PRESS_MASK | GDK_BUTTON_RELEASE_MASK | GDK_SCROLL_MASK)
    g_signal_connect_data(ebox, "button-press-event", <your routine>, 20, 0, 0)
    g_signal_connect_data(ebox, "button-release-event", <your routine>, 0, 0, 0)
    g_signal_connect_data(ebox, "motion-notify-event", <your routine>, 0, 0, 0)
    g_signal_connect_data(ebox, "leave-notify-event", <your routine>, 30, 0, 0)
```

then need the mouse routine "<your routine>" to return the mouse x and y , and the button events

gtk has a single pointer array , not much good for mapping

easier to make array in c , like "myarray[x][y]" , then use the mouse x y for pointer

regards

alexfish

---

### Post by anewguy on 2012-08-22
Thanks very much!  I've got some reading and experimenting to do now to try to do this.  I guess it's a good way to get my feet more wet!

BTW - love the 2 tin cans thing!

Thanks again!
Dave ;)

---

### Post by anewguy on 2012-08-22
I was just looking some more in devhelp to get some idea of what you are suggesting.  In and amongst that search I found some things on using a device, including gdk_device_get_position (), which returns the x/y of the mouse, if I understand it correctly.  Do you think I can display an image, wait on the gdk_device_get_position, then verify if it's location I want "clickable" via the returned x/y?  If so, do you think I can have the image as the 1st "tab" in a notebook, and automatically go to other pages depending on where in the image the click occurred?

Thanks so much for your help!

Dave ;)

---

