---
title: "Custom Widgets in Glade"
date: 2013-09-30
forum: Programming Talk
---

### Post by Tony Flury on 2013-09-30
I have followed (as best I can) the tutorial here : 

[http://www.pygtk.org/articles/custom-widgets-glade/Custom_PyGTK_Widgets_in_Glade3.html](http://www.pygtk.org/articles/custom-widgets-glade/Custom_PyGTK_Widgets_in_Glade3.html)

To start writing a custom widget in Glade (I have Glade 3.67) but I can't even get the widget (or the new group) to even show up on the Glade palette. I know I must be doing something stupid - but there are no error messages from Glade which seem to be of any use.

Has anyone done this before who can help.

My catalog file is : 
```
<glade-catalog name="ToggleImage" library="ToggleImage"
domain="glade-3" depends="gtk+" language="Python">
 <init-function>glade_python_init</init-function>

 <glade-widget-classes>
   <glade-widget-class title="ToggleImage" name="ToggleImage" generic-name="Togg
leImage"/>
 </glade-widget-classes>

 <glade-widget-group name="python" title="Python">
   <glade-widget-class-ref name="ToggleImage"/>
 </glade-widget-group>
</glade-catalog>

```

---

### Post by Tony Flury on 2013-10-05
This is one of the first times I can remember a post of mine not getting a reply - I can't magine that has no-one tried to do this ?

---

