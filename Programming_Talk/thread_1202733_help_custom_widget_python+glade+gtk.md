---
title: "help: custom widget python+glade+gtk"
date: 2009-07-02
forum: Programming Talk
---

### Post by Tulth on 2009-07-02
I'm having a problem creating a custom drawable widget in glade and pygtk.  The specific problem is that my custom widget overwrites the toplevel window.  I have traced this problem to my widgets window attributes always being the toplevel window!  So when I create a graphics context, it writes straight to the toplevel window.

For example, I have a tree with a toplevel window, with some subwidgets, for example, my drawarea, a mainimagewidget that contains the drawarea, and a checkbox that shows up in a different container altogether.

Considering this code snippet:
```

        self.enableIRLEDsCheckbox = self.wTree.get_widget("enableIRLEDsCheckbox")
        self.mainImageWidget = self.wTree.get_widget("mainImage")
        self.drawarea = MyWidget()
        self.mainImageWidget.add(self.drawarea)
        print "mainImageWidget.window: ", self.mainImageWidget.window
        print "mainImageWidget.window.xid: ", "0x%x" % self.mainImageWidget.window.xid
        print "drawarea.window: ", self.drawarea.window
        print "drawarea.window.xid: ", "0x%x" % self.drawarea.window.xid
        print "enableRedLEDCheckbox.window: ", self.enableRedLEDCheckbox.window
        print "enableRedLEDCheckbox.window.xid: ", "0x%x" % self.enableRedLEDCheckbox.window.xid

```

This code produces the following output:

```

mainImageWidget.window:  <gtk.gdk.Window object at 0xb5b690 (GdkWindow at 0xc0a9b0)>
mainImageWidget.window.xid:  0x3200003
drawarea.window:  <gtk.gdk.Window object at 0xb5b690 (GdkWindow at 0xc0a9b0)>
drawarea.window.xid:  0x3200003
enableRedLEDCheckbox.window:  <gtk.gdk.Window object at 0xb5b690 (GdkWindow at 0xc0a9b0)>
enableRedLEDCheckbox.window.xid:  0x3200003

```

Running xwininfo, I see the following:
```

$ xwininfo -all -tree

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x3200003 "Linux TIR Driver Prototype"

  Root window id: 0x13b (the root window) (has no name)
  Parent window id: 0x1214280 (has no name)
     7 children:
     0x320002d (has no name): ()  508x20+206+624  +211+673
     0x320002b (has no name): ()  146x29+568+0  +573+49
     0x320002a (has no name): ()  142x29+426+0  +431+49
     0x3200029 (has no name): ()  142x29+284+0  +289+49
     0x3200028 (has no name): ()  142x29+142+0  +147+49
     0x3200023 (has no name): ()  142x29+0+0  +5+49
     0x3200004 (has no name): ()  1x1+-1+-1  +4+48

  Absolute upper-left X:  5
  Absolute upper-left Y:  49
  Relative upper-left X:  5
  Relative upper-left Y:  24
  Width: 714
  Height: 644
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +5+49  -881+49  -881-507  +5-507
  -geometry 714x644+5+49

  Bit gravity: NorthWestGravity
  Window gravity: NorthWestGravity
  Backing-store hint: NotUseful
  Backing-planes to be preserved: 0xffffffff
  Backing pixel: 0
  Save-unders: No

  Someone wants these events:
      KeyPress
      KeyRelease
      EnterWindow
      LeaveWindow
      Exposure
      StructureNotify
      SubstructureNotify
      FocusChange
      PropertyChange
      ColormapChange
  Do not propagate these events:
  Override redirection?: No

  Window manager hints:
      Client accepts input or input focus: Yes
      Initial state is Normal State

  Normal window size hints:
      Program supplied minimum size: 714 by 644
      Program supplied maximum size: 714 by 644
      Program supplied window gravity: CenterGravity
  No zoom window size hints defined

  No window shape defined
  No border shape defined

```

My glade file is the following, and you can see that there is a distinct widget tree. 

```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Wed Jul  1 22:19:31 2009 -->
<glade-interface>
  <widget class="GtkWindow" id="mainWin">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Linux TIR Driver Prototype</property>
    <property name="resizable">False</property>
    <property name="gravity">GDK_GRAVITY_CENTER</property>
    <signal name="destroy" handler="on_window_destroy"/>
    <signal name="delete_event" handler="on_window_delete_event"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <property name="homogeneous">True</property>
            <child>
              <widget class="GtkToggleButton" id="captureVideoToggleButton">
                <property name="visible">True</property>
                <property name="sensitive">False</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Capture Video</property>
                <property name="response_id">0</property>
                <signal name="toggled" handler="on_captureVideoToggleButton_toggled"/>
              </widget>
            </child>
            <child>
              <widget class="GtkCheckButton" id="enableIRLEDsCheckbox">
                <property name="visible">True</property>
                <property name="sensitive">False</property>
                <property name="can_focus">True</property>
                <property name="label" translatable="yes">Enable IR LEDs</property>
                <property name="response_id">0</property>
                <property name="active">True</property>
                <property name="draw_indicator">True</property>
                <signal name="toggled" handler="on_enableIRLEDsCheckbox_toggled"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkCheckButton" id="enableGreenLEDCheckbox">
                <property name="visible">True</property>
                <property name="sensitive">False</property>
                <property name="can_focus">True</property>
                <property name="label" translatable="yes">Enable Green LED</property>
                <property name="response_id">0</property>
                <property name="active">True</property>
                <property name="draw_indicator">True</property>
                <signal name="toggled" handler="on_enableGreenLEDCheckbox_toggled"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="position">2</property>
              </packing>
            </child>
            <child>
              <widget class="GtkCheckButton" id="enableRedLEDCheckbox">
                <property name="visible">True</property>
                <property name="sensitive">False</property>
                <property name="can_focus">True</property>
                <property name="label" translatable="yes">Enable Red LED</property>
                <property name="response_id">0</property>
                <property name="draw_indicator">True</property>
                <signal name="toggled" handler="on_enableRedLEDCheckbox_toggled"/>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="position">3</property>
              </packing>
            </child>
            <child>
              <widget class="GtkCheckButton" id="enableBlueLEDCheckbox">
                <property name="visible">True</property>
                <property name="sensitive">False</property>
                <property name="can_focus">True</property>
                <property name="label" translatable="yes">Enable Blue LED</property>
                <property name="response_id">0</property>
                <property name="draw_indicator">True</property>
                <signal name="toggled" handler="on_enableBlueLEDCheckbox_toggled"/>
              </widget>
              <packing>
                <property name="position">4</property>
              </packing>
            </child>
          </widget>
        </child>
        <child>
          <widget class="GtkFrame" id="frame1">
            <property name="visible">True</property>
            <property name="label_xalign">0</property>
            <property name="shadow_type">GTK_SHADOW_NONE</property>
            <child>
              <widget class="GtkAlignment" id="mainImage">
                <property name="width_request">710</property>
                <property name="height_request">576</property>
                <property name="visible">True</property>
                <child>
                  <placeholder/>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkLabel" id="label1">
                <property name="visible">True</property>
                <property name="sensitive">False</property>
                <property name="label" translatable="yes">&lt;b&gt;Captured Video&lt;/b&gt;</property>
                <property name="use_markup">True</property>
              </widget>
              <packing>
                <property name="type">label_item</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox2">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="statusLabel">
                <property name="visible">True</property>
                <property name="label" translatable="yes">TrackIR 4 Pro hardware not detected</property>
                <property name="single_line_mode">True</property>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="padding">6</property>
              </packing>
            </child>
            <child>
              <widget class="GtkProgressBar" id="statusprogbar">
                <property name="visible">True</property>
                <property name="text" translatable="yes"></property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="position">3</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

My custom widget was based off this example, from [http://faq.pygtk.org/index.py?file=faq18.008.htp&req=edit:](http://faq.pygtk.org/index.py?file=faq18.008.htp&req=edit:)
```

 class MyWidget(gtk.DrawingArea):
        def __init__(self):
            gtk.DrawingArea.__init__(self)
            self.gc = None  # initialized in realize-event handler
            self.width  = 0 # updated in size-allocate handler
            self.height = 0 # idem
            self.connect('size-allocate', self.on_size_allocate)
            self.connect('expose-event',  self.on_expose_event)
            self.connect('realize',       self.on_realize)

        def on_realize(self, widget):
            self.gc = widget.window.new_gc()
            self.gc.set_line_attributes(3, gtk.gdk.LINE_ON_OFF_DASH,
                                        gtk.gdk.CAP_ROUND, gtk.gdk.JOIN_ROUND)

        def on_size_allocate(self, widget, allocation):
            self.width = allocation.width
            self.height = allocation.height

        def on_expose_event(self, widget, event):
            # This is where the drawing takes place

            widget.window.draw_rectangle(self.gc, False,
                                         1, 1, self.width - 2, self.height - 2)
            widget.window.draw_line(self.gc,
                                    0, 0, self.width - 1, self.height - 1)
            widget.window.draw_line(self.gc,
                                    self.width - 1, 0, 0, self.height - 1)

    win = gtk.Window()
    win.add(MyWidget())
    win.show_all()
    win.connect("destroy", lambda w: gtk.main_quit())
    gtk.main()

```

Whenever I do this line:
```
 self.gc = widget.window.new_gc()
```
this seems to get a GC relative to the toplevel app window, and subsequent draws will conflict with other widgets. Anyone know how to get/setup a proper GC so that my draws actually draw in the widget itself, not the toplevel window?

---

### Post by Tulth on 2009-07-02
Well, I rewrote my widget, and now its not doing it.  It seems like calling gtk.Entry() in the wrong place caused my problem.

---

