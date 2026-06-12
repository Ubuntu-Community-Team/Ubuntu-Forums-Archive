---
title: "Wrapping Scintilla into a C++ object"
date: 2009-03-12
forum: Programming Talk
---

### Post by NintenDave on 2009-03-12
I want to use Scintilla to manage highlighted text editing in a program I'm making with Gtkmm, and I'm investigating ways of integrating the two. Currently, I'm using a method something like this:

```
class MyScint
{
public:
    MyScint()
    {
        GtkWidget* cEditor = scintilla_new();
        sci = SCINTILLA(cEditor);
        scintilla_set_id(sci, 0);

        editor = Glib::wrap(cEditor);
    }

    Gtk::Widget& getWidget()
    {
        assert(editor);
        return *editor;
    }

    int _scintillaSendMessage(int message, int param1 = 0, int param2 = 0)
    {
        return scintilla_send_message(sci, message, param1, param2);
    }

    // void setMarginType(int, int) ...
    // ...

private:
    Gtk::Widget* editor;
    ScintillaObject* sci;
};
```

It works well enough, but I wonder if a more logical and convenient method might be to make a custom widget, with the widget returned by scintilla_new used as the underlying object. Unfortunately, I've been having a hard time understanding how to do this. Can anyone suggest what to do? Thanks.

---

### Post by cabalas on 2009-03-12
Out of interest why not use [gtksourceviewmm]("http://projects.gnome.org/gtksourceviewmm/")? it works pretty nicely.

If you are going to wrap the scintilla widget you might as well do it properly and get all the gtkmm niceties [this guide]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-wrapping-c-libraries.html") will show you how to do it.

---

### Post by NintenDave on 2009-03-12
Thankyou, I've looked at some GtkSourceView docs and it looks a lot simpler than Scintilla. As long as it's supported on at least Linux and Windows platforms I think I'll use it.

Thanks for the link about wrapping C Libraries also, that may come in useful.

---

### Post by cabalas on 2009-03-12
If you do go with gtksourceviewmm you might find this link useful, it was a blog post I did on how to set the highlighting.

[http://mlowen.com/2008/07/02/syntax-highlighting-with-gtksourceviewmm-20-and-giomm/]("http://mlowen.com/2008/07/02/syntax-highlighting-with-gtksourceviewmm-20-and-giomm/")

---

### Post by Vadi on 2009-03-12
Geany uses scintilla as it's editor, but I'm not sure if it's in C++. Check it out though.

(and scintilla better than gtksourceview from my experiences - in anjuta at least.)

---

