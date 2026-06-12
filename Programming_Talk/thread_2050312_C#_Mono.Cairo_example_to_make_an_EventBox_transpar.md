---
title: "C# Mono.Cairo example to make an EventBox transparent - Needed"
date: 2012-08-30
forum: Programming Talk
---

### Post by OM55 on 2012-08-30
I need to create an image with transparency placed on top of another image, inside a regular Gtk# window. The first image should be able to respond to mouse clicks.

The simple way would usually be to put an Image inside an EventBox - and inside the window. However, EventBox is not transparent by default, so even if the png Image itself has transparent areas, when inside the EventBox it shows as a square opaque background around the image.

I'm aware that EventBox can be made transparent using **Cairo**, but so far was not able to do that.

**Can anyone provide a short C# example to make EventBox transparent?**

Thanks!

---

### Post by OM55 on 2012-09-09
Answering my own question...:

The solution is so simple, while I was looking for complex code to redraw the widget...
All that needs to be done is to set the EventBox.VisibleWindow member to 'false' (it is 'true' by default). Than the EventBox is not drawn and if the image inside the EventBox has transparent areas, they will show what ever is below.

In the example below, it is:
**mapBox.VisibleWindow = false;**
and
**pinBox.VisibleWindow = false;**

As far as I could see, the Z-Order (which Widget is on top of which) is determined by the order of drawing on the screen (when the EventBox is not drawn, the EventBox.GdkWindow.Lower() or Raised() members are not doing anything).

Example:


```
    // Showing a map in an invisible EventBox
    EventBox mapBox = new EventBox();
    mapBox.Visible = true;
    **mapBox.VisibleWindow = false;**
    fixed1.Add(mapBox);
    fixed1.Move (mapBox, 0, 0);
    
    Image mapImage = new Image("map.png");
    mapImage.Visible = true;
    mapBox.Add (mapImage);
    
    // Showing a pin image with transparent areas, in an invisible EventBox, on top of the map
    EventBox pinBox = new EventBox();
    pinBox.Visible = true;
    **pinBox.VisibleWindow = false;**
    fixed1.Add(pinBox);
    fixed1.Move (pinBox, 60, 60);
    
    Image pinImage = new Image("redpin.png");
    pinImage.Visible = true;
    pinBox.Add (pinImage);


```

---

