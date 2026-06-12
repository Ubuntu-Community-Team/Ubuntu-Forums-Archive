---
title: "Java Swing Layout Managers Question"
date: 2007-05-12
forum: Programming Talk
---

### Post by khughitt on 2007-05-12
Hi,

I'm new to Swing and to GUI development in general. I'm having some trouble laying things out as i would like. For instance- for one frame, I would like to display a panel, and inside the panel have mostly space, except for four Components in the center (2 JTextFields and 2 JLabels).

[ATTACH]32438[/ATTACH]

When I just use GridLayout directly however the text-fields expand to fill all of the space and look ridiculous. I was able to get what I wanted by using a larger grid and padding the top and bottom with dummy labels, but this is not the best way to program I am sure :P

If anyone has any advice on how to do this- or on GUI programming / Swing in general it would be greatly appreciated.

Thanks!

---

### Post by stuffradio on 2007-05-12
It's fairly simple to do. Using the Swing library everything textfields, labels, etc. has an x co-ordination and a y co-ordination. You can also specify how wide to make things, etc. 

I don't have a Java IDE installed in front of me, and haven't done it in a while, but basically just call the Library. Look through the library for the textfield and Labels.

If no one posts the code in a certain amount of time, I'll install an ide and post the code for you :)

EDIT: Not doing Java for a while makes it harder to write the code haha, I'm just playing around right  now. If I ever get around to making something like your picture I'll post the code, however if someone else can do it instead be my guest :P

---

### Post by khughitt on 2007-05-13
Thanks. It's okay if you don't get the chance to post the code. I'm gonna try checking out the [GridBagLayout]("http://java.sun.com/docs/books/tutorial/uiswing/layout/gridbag.html") layout manager and see if that will work for what i need. I tried setting the size also, but it didn't seem to take hold for some reason. I may have been going about it the wrong way however.

If only I could use CSS box model and floats to lay things out. Life would be much easier :)

---

### Post by samjh on 2007-05-13
GridBagLayout would indeed be your best choice.  It's a bit hard to use though.

If you don't feel like coding the GUI by hand, you can use the Netbeans IDE to design the GUI.  It has the best Swing GUI editor in the market so far.  Check out [www.netbeans.org](www.netbeans.org) if you are interested.

---

### Post by sphinx on 2007-05-13
I used to use GridBagLayout quite a bit before I settled on using mostly BorderLayout. I've found it actualy feels more elegant to nest BorderLayouts to atcheve the layout you want.

Take you desired layout for example.

I would create the outermost panel and give it a BorderLayout, then create another panel (the inner one) with perhaps a GridLayout if thats enough to satisfy you. Then add the inner panel to the outer one with the BorderLayout.CENTER constraint. To show some code it would look something like:
```

JPanel outerPanel = new JPanel();
outerPanel.setLayout(new BorderLayout());

JPanel innerPanel = new JPanel();
// do all the stuff to create your labels and text fields here
//something the same as what you've already done from what you've written.
outerPanel.add(innerPanel, BorderLayout.CENTER);

```

The center area of a border layout controled container respects the preferrred height of the added component.

Hope this helps.

---

### Post by khughitt on 2007-05-13
Thanks guys. It's funny, when i went to read up some more on GridBagLayout yesterday, the first thing on sun's ["How To Use GridBagLayout" Tutorial]("http://java.sun.com/docs/books/tutorial/uiswing/layout/gridbag.html") stated:

> 
Note: Due to the painstaking nature of writing layout code by hand, it is strongly recommended that you use the GroupLayout layout manager combined with a builder tool to lay out your GUI. One such tool is the NetBeans IDE 5.5 Matisse GUI builder. The information provided in this lesson is only useful if you absolutely must write your layout code by hand. In this case, and if you do not want to use GroupLayout, then GridBagLayout is recommended as the next most flexible and powerful layout manager.


I Still want to learn how to lay things manually using the different layout managers so that I at least have the option, but I'm going to give netbeans a shot for now. I Also tried Jingoo for Eclipse (another visual swing editor), and although it is nice to be able to work in eclipse, I think the netbeans interface is much nicer overall.

Hopefully later this summer I will have some free time and can come back and master the different layout managers.

Thanks everyone for your advice :)

---

### Post by thelinuxguy on 2007-05-13
> **pwnedd said:**
> I tried setting the size also, but it didn't seem to take hold for some reason. I may have been going about it the wrong way however.

Setting the size and location manually will have no effect on the layout if a layout manager is managing the GUI. If you want to position and size the components yourself, set the layout to null. But it is painful. And if you simply add the components to a container having null layout without setting the size and location, the components won't show up on screen.

And as sphinx has already mentioned, most applications nest layout managers with BorderLayout at the top.

I would suggest using an IDE. I use Netbeans most of the time.

---

### Post by khughitt on 2007-05-15
Cool thanks guys. I'm starting to get the hang of things (slowly)... Netbeans is pretty nice, and for the most part does the trick. I still like to do things manually though to get a better understanding, at least at first.

In case it helps anyone else, some of the tricks i found useful are:

1. Nest Layout Managers (mentioned above). By using border layout as the outer layout, or even grid layout with just 2 rows, you can split your main panel into smaller workable areas which can then be further divided with other layout managers.

2. FlowLayout manager as an option to have things alrign to the right. (Good for some buttons, etc).

3. BoxLayout is another simple and useful layout manager if you wanna stack components either vertically or horizontally.

Take care,

---

