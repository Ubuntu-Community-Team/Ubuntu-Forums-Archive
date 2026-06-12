---
title: "How do I compile a GTK2-Perl program?"
date: 2009-11-29
forum: Programming Talk
---

### Post by Puzzled Guy on 2009-11-29
How do I compile a GTK2-Perl program and what will be the resulting file?

---

### Post by BenAshton24 on 2009-11-29
Perl is an interperative language meaning that you don't need to compile it... just save the script as script.pl, make it executable:
> chmod +x script.pl
and run it.

---

### Post by Puzzled Guy on 2009-11-29
Oh, so there is no way to make a standalone Perl program.

Another question then, how do I set the size of the window that is created?

---

### Post by loell on 2009-11-29
> **Puzzled Guy said:**
> 
Another question then, how do I set the size of the window that is created?

```
$window->set_default_size ($width, $height)
```

where **$width** and **$height** is the window's width and height.  ;)

---

### Post by BenAshton24 on 2009-11-29
you can compile standalone program with perlcc.

I don't program in perl myself, but I'm pretty sure that it's something like

```
$window->set_default_size (400, 300);
```

(when window is a reference to the window that you want to resize)

---

### Post by Puzzled Guy on 2009-11-29
> **loell said:**
> ```
$window->set_default_size ($width, $height)
```where **$width** and **$height** is the window's width and height.  ;)

Do I have to assign values to them and then use that exact line or do I replace the $width and $height with numbers?

And where do I insert the line? After the line that creates the window?

---

### Post by BenAshton24 on 2009-11-29
> **Puzzled Guy said:**
> Do I have to assign values to them and then use that exact line or do I replace the $width and $height with numbers?

you can do either.

---

### Post by Puzzled Guy on 2009-11-29
> **BenAshton24 said:**
> you can compile standalone program with perlcc.

I don't program in perl myself, but I'm pretty sure that it's something like

```
$window->set_default_size (400, 300);
```(when window is a reference to the window that you want to resize)

That worked, but whenever I start the program, or any program, it always starts maximized. How do I set it to start with the dimensions I set in the $window->set_default_size (400, 300);
line?

---

### Post by loell on 2009-11-29
> **Puzzled Guy said:**
> 
And where do I insert the line? After the line that creates the window?


consider this generic gtk2 hello world perl script,

tingnan mo yung high-lited entry, :)  

> 


# Use the TRUE and FALSE constants exported by the Glib module.
use Glib qw/TRUE FALSE/;
use Gtk2 '-init';

# This is a callback function. We simply say hello to the world, and destroy
# the window object in order to close the program.
sub hello
{
	my ($widget, $window) = @_;
	print "Hello, World\n";

	$window->destroy;
}

sub delete_event
{
	# If you return FALSE in the "delete_event" signal handler,
	# GTK will emit the "destroy" signal. Returning TRUE means
	# you don't want the window to be destroyed.
	# This is useful for popping up 'are you sure you want to quit?'
	# type dialogs.
	print "delete event occurred\n";

	# Change TRUE to FALSE and the main window will be destroyed with
	# a "delete_event".
	return TRUE;
}

# create a new window
$window = Gtk2::Window->new('toplevel');

# When the window is given the "delete_event" signal (this is given
# by the window manager, usually by the "close" option, or on the
# titlebar), we ask it to call the delete_event () functio
# as defined above. No data is passed to the callback function.
$window->signal_connect(delete_event => \&delete_event);

# Here we connect the "destroy" event to a signal handler.
# This event occurs when we call Gtk2::Widget::destroy on the window,
# or if we return FALSE in the "delete_event" callback. Perl supports
# anonymous subs, so we can use one of them for one line callbacks.
$window->signal_connect(destroy => sub { Gtk2->main_quit; });

# Sets the border width of the window.
$window->set_border_width(10);

[COLOR="Red"][B]#you can just put it here
$window->set_default_size (400, 300);[/B]
[/COLOR]
# Creates a new button with a label "Hello World".
$button = Gtk2::Button->new("Hello World");

# When the button receives the "clicked" signal, it will call the function
# hello() with the window reference passed to it.The hello() function is
# defined above.
$button->signal_connect(clicked => \&hello, $window);

# This packs the button into the window (a gtk container).
$window->add($button);

# The final step is to display this newly created widget.
$button->show;

# and the window
$window->show;

# All GTK applications must have a call to the main() method. Control ends here
# and waits for an event to occur (like a key press or a mouse event).
Gtk2->main;

0;



---

### Post by Puzzled Guy on 2009-11-29
Great! But I still want to know how to force the window to start with the dimensions I set

---

### Post by loell on 2009-11-29
do try, but i'm unsure of the result.

$window->unmaximize;

---

### Post by Puzzled Guy on 2009-11-29
Nope, that didn't work

---

### Post by loell on 2009-11-29
after showing the window, put,

 $window->resize ($width, $height);

if it still doesn't, skim through this reference

[http://gtk2-perl.sourceforge.net/doc/pod/Gtk2/Window.html]("http://gtk2-perl.sourceforge.net/doc/pod/Gtk2/Window.html")

I would advice that you learn the ins and outs of perl before doing UIs.  or first use Python before going to perl, just my 2 cents.

---

### Post by Puzzled Guy on 2009-11-29
> **loell said:**
> after showing the window, put,

 $window->resize ($width, $height);

if it still doesn't, skim through this reference

[http://gtk2-perl.sourceforge.net/doc/pod/Gtk2/Window.html](http://gtk2-perl.sourceforge.net/doc/pod/Gtk2/Window.html)

I would advice that you learn the ins and outs of perl before doing UIs.  or first use Python before going to perl, just my 2 cents.

None of the things in the reference worked. I even tried combining the maximize and unmaximize function, but, nothing!

Let me know if you find something

---

### Post by Puzzled Guy on 2009-11-29
Bump

---

### Post by Puzzled Guy on 2009-11-29
> **loell said:**
> 
I would advice that you learn the ins and outs of perl before doing UIs.
I already know the basics of Perl. I read "Perl 5 for Dummies"

---

### Post by Puzzled Guy on 2010-07-04
D'oh! I had Maximus running. Maximus maximizes windows on startup.

Sorry.

---

