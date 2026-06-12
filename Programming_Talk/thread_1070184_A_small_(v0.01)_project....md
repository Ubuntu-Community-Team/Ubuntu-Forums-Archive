---
title: "A small (v0.01) project..."
date: 2009-02-14
forum: Programming Talk
---

### Post by tom66 on 2009-02-14
I've begun writing an alternative to OpenOffice.org Presentation/Impress and Microsoft PowerPoint. Frankly, I think that OO.org Presentation sucks (sorry to OO.org devs): There's little (or no) anti-aliasing (on text only as far as I can see), it's slow when doing simple things like changing properties of an object, it doesn't integrate with any know interface of mine (what is it... GNOME/GTK, maybe?) and it's been a bit unstable for me (crashing with animations happens sometimes with me). I've started writing ... *GtkPresentationProgram*, for lack of a better name (I'm open to suggestions.)

This program will use Cairo as it's a fantastic graphics library for rendering vector graphics. It handles antialiased alpha-channel PNG/PDF/SVG output, and can draw to a GTK window, which is swell. The program currently uses GTK to render the window, widgets, toolbar, and other elements, though that area is currently incomplete. 

Focus is on the rendering engine at the moment. I have ambitious plans for getting cool features integrated which are probably *not* compatible with other programs. These include strokes (or outlines, whatever you want to call them) with gradients, text with shadows, text having strokes, fill and highlighting (all supporting gradients, radial and linear, and full colors unlike the max 16/24(?) colors supported in some programs), smooth animation, a 'pre-render' feature, where the show can optionally be pre-rendered into a series of bitmap images before it is shown so it runs at the best performance level (sacrificing a minute or so while it renders everything) (although this will not work with triggered animations based on mouse clicks or user-input, unless all possibilities are pre-rendered which might be a bit of work), and animations which can do some more things that I've wanted before, which can be done by simply using cairo's mask feature (such as a fade in from left to right). More input trigger options (for animation) are also planned: instead of just a standard mouse click, what about the button pressed (left, right, middle, scroll wheel, etc.), or triggering on mouse movement. And instead of general key presses, why not 'specific' key presses, releases, or multiple key combinations? These features I've found lacking in other packages.

And, if graphs are added, then animation will be a possible feature which could be applied to the individual elements. So you could have a line graph moving along as a demonstration, or have bar chart bars fall from the top of the canvas. Tables and lists are currently not planned, until I can figure them out and how to implement them... sorry!

This is also a learning experience for me. You might have seen me asking a lot about C and how to do this and that. This is because I am still learning about C and really starting to appreciate it with my first real project. Oh, and this program was just an idea of what could be done with cairo: upon a quick consideration, I came to the conclusion on how powerful it is: GTK 2.10+ uses it, Firefox/Gecko uses it and Inkscape uses it, so I realised it would suit my needs perfectly. 

At the moment, I'm going to be developing it but when it gets to the point of a very beta release I will let people know. I can provide the code if anyone wants, but beware I will be doing heavy development on it and also a lot of it is hopeful prototypes, things which have not been implemented yet but have core functions to do things with their data structures. And my coding style is still not up to scratch and is my own style which not all people use. You'll find occasional use of tabs, which I'm trying to avoid, in favor of four or more spaces. 

Any suggestions, ideas, encouragement, and names welcome.
Tom. (I need t sleep now. My tping is getsing worser andworseq..,)

---

### Post by ch0d3 on 2009-02-14
> **tom66 said:**
> I've begun writing an alternative to OpenOffice.org ...

Sounds very cool. Have you thought about hosting on a distributed vcs like bazaar?

---

### Post by OutOfReach on 2009-02-15
I like your idea. :)
Anyways I hope to see this advance. (P.S. ch0d3 is right you should consider something like Bazaar or cvs)

---

### Post by timClicks on 2009-02-15
Great project!

If this got off the ground, it would be a great complement to GNOME Office. Personally, I *much* prefer using AbiWord to OO.o.

Its great to see the feature-full concept. It will be great to make this more than a PowerPoint clone.

---

### Post by tom66 on 2009-02-15
Thanks guys. I probably wouldn't know much about CVS, although my web host offers it so I'll consider them or consider using Launchpad/Sourceforge (whichever suits my needs). 

Any ideas or suggestions?

---

### Post by cb951303 on 2009-02-15
I hope you work it out. Community needs a GTK presentation application to go along with Abiword and Gnumeric

---

### Post by tom66 on 2009-02-15
Oh, and at the moment, my code is not very good. It compiles, but it has a ton of warnings about incompatible pointer types:

```

main.c:45: warning: passing argument 1 of &#8216;gtk_message_dialog_new&#8217; from incompatible pointer type
main.c:50: warning: passing argument 1 of &#8216;gtk_message_dialog_format_secondary_markup&#8217; from incompatible pointer type
main.c:72: warning: passing argument 1 of &#8216;gtk_widget_destroy&#8217; from incompatible pointer type

```

(mostly GTK things) which I don't understand or know how to fix. So if anyone knows how to fix these, please let me know.

Oh, and I submit to you a PNG output of the rendering engine so far. This is what it is able to do: (excessive overuse of gradients is only for testing!)

---

### Post by nvteighen on 2009-02-15
You're probably forgetting to cast something... All widgets are declared as GtkWidget *, but then you have to cast them to their "nature"... GTK_WINDOW(), GTK_BUTTON(), whatever.

Good luck!

(And yes, take a look at [https://launchpad.net](https://launchpad.net) or similar to host this project somewhere)

---

### Post by tom66 on 2009-02-15
Thanks, I eliminated most of the warnings by doing that. :D

---

### Post by nvteighen on 2009-02-15
> **tom66 said:**
> Thanks, I eliminated most of the warnings by doing that. :D
Which remain? Can you post them?

Another recommendation, install the GTK+ docs from the repos + DevHelper, the documentation browser...

```

sudo apt-get install libgtk2.0-doc devhelper

```

---

### Post by tom66 on 2009-02-15
When sorting by zOrder, which is used with the qsort function:

```


/**
 * Sort by zOrder callback. If unable to sort by zOrder, sorts by pointer address,
 * to ensure the sort produces (hopefully) similar results every time. 
 * @params    o1, o2
 * @returns   result similar to strcmp
 * @note      Currently throws a warning due to incompatible pointer types -- if anyone
 *            can fix it without breaking functionality it would be great. Works fine 
 *            at the moment even with the warning. (FIXME: The warning seems to stem from
 *            the fact that I'm using (struct P_Render_Item *) elements, when I should be
 *            using (void  *) elements. However, doing this breaks it. So I'll leave it
 *            as-is.)
 */
int zorder_sort(struct P_Render_Item *o1, struct P_Render_Item *o2)
{
    if(o1->zOrder < o2->zOrder)
        return -1;
    else if(o1->zOrder > o2->zOrder)
        return 1;
    else if(o1->zOrder == o2->zOrder)
    {
        /* If the zOrders are equal, then we sort by address. */
        sprintf(__buffer, "o1 (0x%X) and o2 (0x%X) have the same zOrder, sorting by address. ", 
            (int)&o1->zOrder, (int)&o2->zOrder);
        __DEBUG(__buffer);
        
        if(&o1->zOrder < &o2->zOrder)
            return -1;
        else if(&o1->zOrder > &o2->zOrder)
            return 1;
        else
        {
            sprintf(__buffer, "o1 (0x%X) and o2 (0x%X) have the same addresses, returning as equal. ", 
                (int)&o1->zOrder, (int)&o2->zOrder);
            __WARNING(__buffer);
            return 0;
        }
    }
}

```

This line:

```

    /* Use the qsort function to sort the objects by zOrder using our zorder_sort function. */
    qsort(to_render, iListSize, sizeof(struct P_Render_Item), zorder_sort);

```

produces a single warning:

```

In file included from main.c:16:
draw.c: In function &#8216;render_objects_in_slide&#8217;:
draw.c:417: warning: passing argument 4 of &#8216;qsort&#8217; from incompatible pointer type

```

It works fine with this warning.

Oh, and I have both of those packages, I use them when I have no internet connection.

---

### Post by Tibuda on 2009-02-15
There is a dead project called Agnubis, but I was never able to get the source code. See: [http://projects.gnome.org/agnubis/](http://projects.gnome.org/agnubis/)

---

### Post by nvteighen on 2009-02-15
Try using **&zorder_sort** instead of **zorder_sort** in the qsort() call. That should solve it...

---

### Post by PythonPower on 2009-02-15
[QUOTE=nvteighen]Try using &zorder_sort instead of zorder_sort in the qsort() call. That should solve it...[/QUOTE]

I don't think that will work... Also, try defining zorder_sort() as:

[PHP]int zorder_sort(const void *elem1, const void *elem2)[/PHP]

And casting the two arguments within the function. Perhaps like:

[PHP]struct P_Render_Item *o1 = (struct P_Render_Item *)elem1;
struct P_Render_Item *o2 = (struct P_Render_Item *)elem2;[/PHP]

---

### Post by Vadi on 2009-02-15
I heard of a clutter program that does slideshows: [http://www.gnome.org/~fherrera/blog/opttollina.html](http://www.gnome.org/~fherrera/blog/opttollina.html)

---

### Post by tom66 on 2009-02-15
Hey, it's in Bazaar/Launchpad!

[https://code.launchpad.net/~thomas-tgohome/gtkpresentationprogram/trunk](https://code.launchpad.net/~thomas-tgohome/gtkpresentationprogram/trunk)

Enjoy. You can now get all the source code. Beware it doesn't work too great at the moment.

---

### Post by ch0d3 on 2009-02-15
> **tom66 said:**
> Hey, it's in Bazaar/Launchpad!

Sweet. In my experience sourceforge is painfully slow.

---

### Post by Xcmd on 2009-02-16
I'd love to see something like this, especially if it has some sort of stand-alone export feature.

---

### Post by tom66 on 2009-02-17
I'm probably going to start from scratch and write it in Python. At least then, I don't need to worry so much about the nitpicks of C, like pointers and character strings. What's everyone's opinion on this? It might not be as fast, but many apps are written in Python, so would it be a worthy language for this?

---

### Post by ajackson on 2009-02-17
> **tom66 said:**
> I'm probably going to start from scratch and write it in Python. At least then, I don't need to worry so much about the nitpicks of C, like pointers and character strings. What's everyone's opinion on this? It might not be as fast, but many apps are written in Python, so would it be a worthy language for this?
While it might not have the raw processing speed that some people seem to think is the answer to everything, Python has a large base of users (in here at least) and generally a very quick development cycle. As you say it lets you concentrate of the awkward parts of the specification without have to do everything at a very low level. No doubt some will disagree (some just for the sake of disagreeing) but that is my opinion.

---

### Post by Tibuda on 2009-02-18
You could also help Criawips, or use any code they already have:
[http://www.nongnu.org/criawips/](http://www.nongnu.org/criawips/)
[http://live.gnome.org/Criawips/](http://live.gnome.org/Criawips/)

---

### Post by CarpKing on 2009-02-18
You probably aren't to this point yet, but it would be cool if the interface could share some conventions with AbiWord and Gnumeric in order to create a more cohesive experience (as your project seems likely to appeal to the same sort of audience).  It would also be handy if the vector drawing tools worked the same as or similar to Inkscape's so people familiar with that program don't have to relearn too much.  

Anyway, I applaud your efforts and look forward to testing your project at some point.

---

### Post by OutOfReach on 2009-02-18
> **tom66 said:**
> I'm probably going to start from scratch and write it in Python. At least then, I don't need to worry so much about the nitpicks of C, like pointers and character strings. What's everyone's opinion on this? It might not be as fast, but many apps are written in Python, so would it be a worthy language for this?

I don't think an application as big as a presentation program would perform well with Python. [My Opinion]

---

### Post by tom66 on 2009-02-18
Thanks guys for your support but it will take a while before it starts becoming usable, maybe a couple of months.

Here's some info on what's planned. Remember, this is only a plan:

 - All graphics will be vector, excluding images, which will be adjusted to work with this system (probably resized on demand when zooming or performing transformations). They will be represented in 64-bit floating point values. Might not give the best performance, but it produces good precision at high zoom levels.
 - Animations that are missing in some programs will be added. For example there will be a fade in which allows you to fade in from left to right, for example. And when the hue of an object is shifted as an emphasis animation, it will also work with gradients and possibly images. 
 - Text rendering with multiple formatting elements is planned, like most programs support.
 - Triggering animations with many different types of input, such as keyboard presses and mouse movement (maybe even add mouse gestures?) is planned.
 - PyCairo will be the backend to the rendering library, which is called Agamid Render, which is part of the program. Agamids are a species of lizards, and this is named after another rendering engine (any guesses?). The animation library will probably be Chameleon, another species of lizard. 

And:
 
 - The interface has not yet been written. I am getting the rendering engine and the animations engine working before I start working with PyGTK and other programs.

---

### Post by Vadi on 2009-02-18
I can assist you in designing the interface part - I'm experienced with Glade and know the Gnome HIG.

---

### Post by tom66 on 2009-02-19
If you want to make a prototype please do. The prototype should have either a GtkDrawingArea or a suitably sized widget for the editing area for now. Maybe you could give the various dialogs a shot as well, such as the fill style and stroke style dialogs. (The fill style dialog should contain options for: Solid colors, gradients, and *possibly* images, the stroke style should contain line width, style, dash offset (a slider will be fine for this), and an option to set the fill style through the fill style dialog.) 

Please PM me with the prototype or post it here.

Thanks.

---

### Post by Dawei87 on 2009-04-02
this would be great. i hate oo.o and having a presentation application to go alongside abiword and gnumeric would be wonderful. def keep us posted on the project

---

### Post by simeon87 on 2009-04-02
> **OutOfReach said:**
> I don't think an application as big as a presentation program would perform well with Python. [My Opinion]

[http://en.wikipedia.org/wiki/List_of_Python_software](http://en.wikipedia.org/wiki/List_of_Python_software)

This list contains enough big programs to support the idea that Python is fast enough for a presentation program.

---

