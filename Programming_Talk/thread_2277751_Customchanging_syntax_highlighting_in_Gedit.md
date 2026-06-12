---
title: "Custom/changing syntax highlighting in Gedit"
date: 2015-05-11
forum: Programming Talk
---

### Post by jim50 on 2015-05-11
Hi ladies and Gents,

I'm relatively new to programming and am at the hobby stage (Just completed the Python & Ruby codecademy courses) and have now signed up for an evening 'going beyond basics' python class. I really enjoy it, but the teacher of the course is very strict about not using IDE's at this stage. I have to use Gedit to write my code, which is fine, and we're encouraged to use syntax highlighting, but I really want to customise the colour scheme - too many things share the same few colours on all of the themes I've tried.

I know there are lots of python plug-ins for Gedit from googling the subject, but as I say we can't use those yet. It must be something simple I'm missing, but I just can't see it!

I suppose we can use another editor if you know one - the guys with macs use a different editor - but it can't help us any more than syntax highlighting?

Thanks all!

---

### Post by pavelexpertov on 2015-05-11
Well, I am afraid I can't find an option to change colours (unless I am wrong or you can download a custom theme from the web) in gedit. I started programming Java in simple featureless editors since your mind concentrates more on learning the syntax and from your stupid and silly mistakes. I can recommend one IDE I use for simple python development and it's Geany. Although it is an IDE, it is very lightweight and still works brilliantly as the editor. However, it does not have customisable colour schemes, you may like what it has got. Keep in mind about tab spacing, when you indent you have to have spaces rather than tab characters (coz geany doesn't do it by default, annoyingly) so you would have to change it in preferences. Other editors to try are either Atom (from github team) or Brackets (from Adobe). Also there is jedit based on java, although I can't remember if it does provide options for changing colour schemes or syntax highlighting.

P.S. syntax highlighting just provides convenient way to separate items in your code. As a programmer, you should be able to read and understand the code without the scheme in different situations.

---

### Post by steeldriver on 2015-05-11
You can change the overall gedit color *scheme*:

[https://help.gnome.org/users/gedit/stable/gedit-change-color-scheme.html.en](https://help.gnome.org/users/gedit/stable/gedit-change-color-scheme.html.en)

The 'Cobalt' scheme has a quite nice amount of contrast between the syntax elements imho. More themes / customization instructions here:

[https://wiki.gnome.org/Projects/GtkSourceView/StyleSchemes](https://wiki.gnome.org/Projects/GtkSourceView/StyleSchemes)

I am also a Geany fan btw

---

### Post by jim50 on 2015-05-11
Thanks steeldriver!

I followed the link and downloaded the IDLE theme. By the way, the path for themes in 15.04 is ```
/usr/share/gtksourceview-3.0/styles/
```

most of it was as I wanted, but I opened the xml file and it was pretty simple to declare extra colours and assign them.

Thanks both for recommending geany! before starting this course I'd been using geany idle and ninja. I think I liked geany the most too, but ninja looked like it'd be awesome once i knew enough python to utilise it!

---

### Post by user1397 on 2015-05-13
+1 to the cobalt theme, it's installed by default in gedit.  just gotta enable it in gedit's settings.

also +1 to geany.   Cool thing about geany is it is still simple enough that it's not a bloated IDE with a bunch of features, just barebones and you can compile/execute with console output right there.  Works with python and java and several other langs

---

