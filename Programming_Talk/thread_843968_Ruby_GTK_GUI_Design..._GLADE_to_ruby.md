---
title: "Ruby GTK GUI Design... GLADE to ruby?"
date: 2008-06-29
forum: Programming Talk
---

### Post by Questioneer on 2008-06-29
Hello-
Here's my problem.

A. There is no WAY I can hand code the GUI for my Ruby GTK app.
B. GLADE Sucks! I HATE GLADE. Well, it is a nice UI designer, but there is NO WAY I'm going to use a freaking .glade file. Why, WHY can glade not just provide the raw code for the output in several languages???

So. I'm looking for some kind of GUI designer for Ruby and GTK.
The all important requirement, is, the GUI designer MUST BE ABLE TO OUTPUT THE CODE FOR THE DESIGN IN PURE RUBY.

I DO NOT WANT a .stupidxml file. I want a .rb output file.

What would be good is a way to convert a .glade to a .rb file.

If anyone knows anything, please help.

---

### Post by grigio on 2008-06-29
I manage the ruby/gtk GUIs in this way

@glade = GladeXML.new('data/gui.glade')
@glade.widget_names.each do |name|
      instance_variable_set("@#{name}".intern, @glade[name])
end

More on:
[http://grigio.org/sviluppare_un_programma_gnome_ruby_e_glade](http://grigio.org/sviluppare_un_programma_gnome_ruby_e_glade)

There is also Gladex, but I really don't need it
[https://help.ubuntu.com/community/Gladex#head-7e96fd09c298bd55b4263eae62e46d8350c2a96e](https://help.ubuntu.com/community/Gladex#head-7e96fd09c298bd55b4263eae62e46d8350c2a96e)

---

### Post by slavik on 2008-06-29
> **Questioneer said:**
> Hello-
Here's my problem.

A. There is no WAY I can hand code the GUI for my Ruby GTK app.
B. GLADE Sucks! I HATE GLADE. Well, it is a nice UI designer, but there is NO WAY I'm going to use a freaking .glade file. Why, WHY can glade not just provide the raw code for the output in several languages???

So. I'm looking for some kind of GUI designer for Ruby and GTK.
The all important requirement, is, the GUI designer MUST BE ABLE TO OUTPUT THE CODE FOR THE DESIGN IN PURE RUBY.

I DO NOT WANT a .stupidxml file. I want a .rb output file.

What would be good is a way to convert a .glade to a .rb file.

If anyone knows anything, please help.
if you don't like it, don't use it and stop bothering us.

---

### Post by napsy on 2008-06-29
Older versions of Glade had an option to generate C/C++ code from the XML data. But because code generation is bad practice this option was later removed. The main feature of glade is that you can modify your UI look without changing any code.

The latest Gtk+ library merged with the Glade XML parser so you don't need to use the Glade module in your program. Instead just find the apropriate Ruby functions to manipulate Glade XML data.

---

