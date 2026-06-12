---
title: "Getting a text from GtkTextView (Glade)"
date: 2009-06-15
forum: Programming Talk
---

### Post by OnlyOneOfUsWalksAway on 2009-06-15
Hi there,
I am trying to make a simple program that will get the text, which is
 written in the textview1 object. 
However, I can't find the right way to do it. I googled it and found 
no answer. 

The source code :
[php]try:
    import pygtk
    pygtk.require("2.0")
except:
    pass
try:
    import gtk
    import gtk.glade
except:
    sys.exit(1)
    
class myApp:
    
    def __init__(self):
        self.gladefile="test1.glade"
        self.wTree=gtk.glade.XML(self.gladefile)
        self.window=self.wTree.get_widget("window1")
        dic={ "on_window1_destroy":gtk.main_quit, "on_button1_clicked":self.on_button1_clicked }
        self.wTree.signal_autoconnect(dic)
    
    def on_button1_clicked(self,widget):
        self.textview1=self.wTree.get_widget("textview1").get_buffer()
        print self.textview1.get_text(self.enTexLog.get_start_iter,self.enTexLog.get_end_iter)

if __name__=="__main__":
    app=myApp()
    gtk.main()[/php]The glade interface :
[php]<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Mon Jun 15 23:52:35 2009 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <signal name="destroy" handler="on_window1_destroy"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkScrolledWindow" id="scrolledwindow1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="hscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <property name="vscrollbar_policy">GTK_POLICY_AUTOMATIC</property>
            <child>
              <widget class="GtkTextView" id="textview1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
            </child>
          </widget>
        </child>
        <child>
          <widget class="GtkButton" id="button1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="label" translatable="yes">button</property>
            <property name="response_id">0</property>
            <signal name="clicked" handler="on_button1_clicked"/>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>[/php]Thank you in advance.

---

### Post by Tony Flury on 2009-06-15
```

print self.textview1.get_text(self.enTexLog.get_start_iter,self.enTexLog.get_end_iter)

```

You are not setting self.enTexLog or any of the atrributes you are trying to use, at least not in the code sample  you have posted.

---

### Post by OnlyOneOfUsWalksAway on 2009-06-15
Wooow! That was faster than I thought. Anyway, you're right but it hasn't fixed the problem. I get this error :
[php]   print self.textview1.get_text(self.textview1.get_start_iter,self.textview1.get_end_iter)
TypeError: start should be a GtkTextIter[/php]The code :
[php]try:
    import pygtk
    pygtk.require("2.0")
except:
    pass
try:
    import gtk
    import gtk.glade
except:
    sys.exit(1)
    
class myApp:
    
    def __init__(self):
        self.gladefile="test1.glade"
        self.wTree=gtk.glade.XML(self.gladefile)
        self.window=self.wTree.get_widget("window1")
        dic={ "on_window1_destroy":gtk.main_quit, "on_button1_clicked":self.on_button1_clicked }
        self.wTree.signal_autoconnect(dic)
    
    def on_button1_clicked(self,widget):
        self.textview1=self.wTree.get_widget("textview1").get_buffer()
        print self.textview1.get_text(self.textview1.get_start_iter,self.textview1.get_end_iter)

if __name__=="__main__":
    app=myApp()
    gtk.main()  [/php]

---

### Post by Tony Flury on 2009-06-15
shouldn't you be using get_start_iter() - it is a method after all 

and similarly with get_end_iter()

---

### Post by OnlyOneOfUsWalksAway on 2009-06-16
Awesome! That works.
Thanks a lot!

---

