---
title: "help with null pointer exception"
date: 2011-04-05
forum: Programming Talk
---

### Post by edan3250 on 2011-04-05
hello guys :)
im using java-gnome and i have a problem about "image click event".

my code:
```
package game;

import org.gnome.gdk.EventButton;
import org.gnome.gtk.Fixed;
import org.gnome.gtk.Image;
import org.gnome.gtk.Widget;

public class Piece implements Widget.ButtonReleaseEvent
{
	private Point location;
	private Image image;
	private int player;
	private boolean legal;

	protected Piece(Point location, Image image, int player, boolean legal)
	{
		this.location = location;
		this.image = image;
		this.player = player;
		this.legal = legal;
		this.image.connect(this);
	}

	public Point getLocation()
	{
		return this.location;
	}

	public void setLocation(Point location)
	{
		this.location = location;
	}

	public Image getImage()
	{
		return this.image;
	}

	public void setImage(Image image)
	{
		this.image = image;
	}

	public int getPlayer()
	{
		return this.player;
	}

	public void setPlayer(int player)
	{
		this.player = player;
	}

	public boolean isLegal()
	{
		return this.legal;
	}

	public void setLegal(boolean legal)
	{
		this.legal = legal;
	}

	public boolean equals(Piece piece)
	{
		return this.player == piece.player;
	}

	public void draw(Fixed fixed)
	{
		fixed.put(this.image, this.location.getX(), this.location.getY());
	}

	public boolean onButtonReleaseEvent(Widget w, EventButton e)
	{
		// TODO Auto-generated method stub
		if (e.equals(this.image))
			System.out.println("e");
		if (w.equals(this.image))
			System.out.println("w");
		return false;
	}
}
```

my error:
```
Exception in thread "main" java.lang.NullPointerException
	at game.Piece.<init>(Piece.java:21)
	at game.Board.<init>(Board.java:31)
	at game.Hexxagon.<init>(Hexxagon.java:23)
	at game.Hexxagon.main(Hexxagon.java:40)
```

the error found at line:
```
this.image.connect(this);
```

java-gnome api:
[http://java-gnome.sourceforge.net/4.0/doc/api/index.html?overview-summary.html](http://java-gnome.sourceforge.net/4.0/doc/api/index.html?overview-summary.html)

thanks for help :)

---

### Post by simeon87 on 2011-04-05
Are you sure that you have passed an Image object? Based on what you've given us I think the Image object is null.

---

### Post by edan3250 on 2011-04-05
thanks for fast response!

yes on my "Board" class i do that...
```
this.board[x][y] = new Piece(new Point(xIndex, yIndex), new Image(Constants.PIECE_EMPTY), Constants.PLAYER_EMPTY, true);
```

on "Constants" this is the field (i dont using resources yet)
```
public static final String PIECE_EMPTY = "/home/edan3250/Documents/Hexagon/done/Piece.png";
```

any idea?

---

### Post by edan3250 on 2011-04-05
ok thanks very much simeon87!
you right, because the hexxagon is not fully map, i using null value as some places.

i use the connect function when i have true value on legal and its works!
but i have another problem, when i click on image (and release of course) nothing happens!

looks on the last function, is an event that should auto calling when i connect the image to widget button release...

i try equals the widget and the event to image and nothing :(

---

### Post by simeon87 on 2011-04-05
> **edan3250 said:**
> ok thanks very much simeon87!
you right, because the hexxagon is not fully map, i using null value as some places.

i use the connect function when i have true value on legal and its works!
but i have another problem, when i click on image (and release of course) nothing happens!

looks on the last function, is an event that should auto calling when i connect the image to widget button release...

i try equals the widget and the event to image and nothing :(

Why are you trying to equal a Widget or EventButton to an Image? They'll never be equal because a widget is not an image and an event is not an image either. When that function runs, you get the Widget from which the event originated and the EventButton with additional information about the event. Try putting a normal System.out.println("test"); to see if it runs at all and then think about what you want to do.

---

### Post by edan3250 on 2011-04-05
i try to print a message without any condition and its not called.
maybe i doing something wrong?
how can i catch the mouse click (press or release) on the image?

---

### Post by simeon87 on 2011-04-05
> **edan3250 said:**
> i try to print a message without any condition and its not called.
maybe i doing something wrong?
how can i catch the mouse click (press or release) on the image?

You can catch mouse events from gtk widgets so what is the widget on which you are listening for events? You can display an Image on a Widget and you should listen for events on that widget. So you're not really clicking on the image itself but on the widget that contains it.

In Gtk you have to listen for events, so for example you can do (in Python, I don't know about Java):

```
widget.connect("button_press_event", self.on_button_press_event)
```

which means all button press events on that widget will be given to the function on_button_press_event. It must be something similar in Java but I'm not familiar with the rest of your program and the details of GTK in Java.

---

### Post by edan3250 on 2011-04-05
yes i know that...
im using that and its works fine...
but when i try to catch the image clicked event its do nothing...
i also try using "Button.Clicked" event but its not supported on images.
well i can get it works when i catch the coordination of the fixed panel and then calculate them to know image who clicked, have a another way?

---

