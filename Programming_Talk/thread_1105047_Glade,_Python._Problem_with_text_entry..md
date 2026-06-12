---
title: "Glade, Python. Problem with text entry."
date: 2009-03-24
forum: Programming Talk
---

### Post by Chokkan on 2009-03-24
I want to have the text in a text entry box (entNewUserLogName) clear when the clear button (btnClear) is pressed. As you can see, I'm using glade and have set up the handler for the clicked signal on btnClear (on_btnClear_clicked). The python file is the problem (I think)
 
A simple request but one which I can't seem to do. I feel like I've tried everything and it is driving me crazy. Somebody please release me from this pain.
login.xml :
```
<?xml version="1.0"?>
<!--Generated with glade3 3.4.5 on Tue Mar 24 16:16:45 2009 -->
<interface>
  <object class="GtkWindow" id="LoginWindow">
    <property name="width_request">400</property>
    <property name="height_request">200</property>
    <property name="visible">True</property>
    <property name="title" translatable="yes">Login</property>
    <property name="window_position">GTK_WIN_POS_CENTER_ALWAYS</property>
    <signal handler="on_LoginWindow_destroy" name="destroy"/>
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <object class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <object class="GtkImage" id="image1">
                <property name="visible">True</property>
                <property name="stock">gtk-missing-image</property>
              </object>
            </child>
            <child>
              <object class="GtkLabel" id="label2">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Welcome</property>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
        </child>
        <child>
          <object class="GtkHBox" id="hbox2">
            <property name="visible">True</property>
            <child>
              <object class="GtkLabel" id="label1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Login Name</property>
              </object>
            </child>
            <child>
              <object class="GtkEntry" id="entry1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="max_length">40</property>
                <property name="width_chars">22</property>
              </object>
              <packing>
                <property name="padding">10</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <object class="GtkHBox" id="hbox3">
            <property name="visible">True</property>
            <child>
              <object class="GtkLabel" id="label4">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Password</property>
              </object>
            </child>
            <child>
              <object class="GtkEntry" id="entry2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="max_length">40</property>
                <property name="visibility">False</property>
                <property name="width_chars">20</property>
              </object>
              <packing>
                <property name="padding">10</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <object class="GtkHButtonBox" id="hbuttonbox1">
            <property name="visible">True</property>
            <property name="spacing">40</property>
            <property name="layout_style">GTK_BUTTONBOX_CENTER</property>
            <child>
              <object class="GtkButton" id="btnLoginCancel">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Cancel</property>
                <signal handler="on_btnLoginCancel_clicked" name="clicked"/>
              </object>
            </child>
            <child>
              <object class="GtkButton" id="btnLogin">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Login</property>
                <signal handler="on_btnLogin_clicked" name="clicked"/>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="btnNewUser">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">I'm new!</property>
                <signal handler="on_btnNewUser_clicked" name="clicked"/>
                <signal handler="gtk_widget_show" name="show"/>
              </object>
              <packing>
                <property name="position">2</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">3</property>
          </packing>
        </child>
        <child>
          <object class="GtkLabel" id="label3">
            <property name="sensitive">False</property>
            <property name="label" translatable="yes">Incorrect! Please try again.</property>
            <property name="use_markup">True</property>
          </object>
          <packing>
            <property name="fill">False</property>
            <property name="padding">9</property>
            <property name="position">4</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>
```
new-user.xml:
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Tue Mar 24 23:03:53 2009 -->
<glade-interface>
  <widget class="GtkWindow" id="NewUserWindow">
    <property name="width_request">400</property>
    <property name="height_request">400</property>
    <property name="visible">True</property>
    <property name="receives_default">True</property>
    <property name="title" translatable="yes">New User Registration</property>
    <property name="modal">True</property>
    <property name="window_position">GTK_WIN_POS_MOUSE</property>
    <property name="destroy_with_parent">True</property>
    <child>
      <widget class="GtkVBox" id="vbox2">
        <property name="visible">True</property>
        <child>
          <widget class="GtkLabel" id="lblNewUser">
            <property name="visible">True</property>
            <property name="label" translatable="yes">New User Registration</property>
          </widget>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox3">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="lblLoginName">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Login Name
e.g. HarukaMiyamoto</property>
                <property name="use_markup">True</property>
                <property name="justify">GTK_JUSTIFY_CENTER</property>
              </widget>
            </child>
            <child>
              <widget class="GtkEntry" id="entNewUserLogName">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="text" translatable="yes">Name</property>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="padding">50</property>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox7">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="lblName">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Name
e.g. Haruka</property>
                <property name="use_markup">True</property>
                <property name="justify">GTK_JUSTIFY_CENTER</property>
              </widget>
            </child>
            <child>
              <widget class="GtkEntry" id="entNewUserName">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="padding">50</property>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox4">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="lblPassword">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Password</property>
                <property name="use_markup">True</property>
              </widget>
            </child>
            <child>
              <widget class="GtkEntry" id="entNewUserPassword">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="padding">50</property>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">3</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox5">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="lblRePassword">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Re-type Password</property>
                <property name="use_markup">True</property>
              </widget>
            </child>
            <child>
              <widget class="GtkEntry" id="entNewUserRePassword">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="padding">50</property>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">4</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox6">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="label8">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Year</property>
              </widget>
            </child>
            <child>
              <widget class="GtkHButtonBox" id="hbuttonbox2">
                <property name="visible">True</property>
                <child>
                  <widget class="GtkRadioButton" id="radiobutton1">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="label" translatable="yes">1st Year</property>
                    <property name="response_id">0</property>
                    <property name="active">True</property>
                    <property name="draw_indicator">True</property>
                  </widget>
                </child>
                <child>
                  <widget class="GtkRadioButton" id="radiobutton2">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="label" translatable="yes">2nd Year</property>
                    <property name="response_id">0</property>
                    <property name="draw_indicator">True</property>
                    <property name="group">radiobutton1</property>
                  </widget>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
                <child>
                  <widget class="GtkRadioButton" id="radiobutton3">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="label" translatable="yes">3rd Year</property>
                    <property name="response_id">0</property>
                    <property name="draw_indicator">True</property>
                    <property name="group">radiobutton1</property>
                  </widget>
                  <packing>
                    <property name="position">2</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">5</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHButtonBox" id="hbuttonbox3">
            <property name="visible">True</property>
            <property name="spacing">20</property>
            <property name="layout_style">GTK_BUTTONBOX_CENTER</property>
            <child>
              <widget class="GtkButton" id="btnClear">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Clear</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_btnClear_clicked"/>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="btnCancel">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Cancel</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_btnCancel_clicked"/>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkButton" id="btnSubmit">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Submit</property>
                <property name="response_id">0</property>
              </widget>
              <packing>
                <property name="position">2</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">6</property>
          </packing>
        </child>
        <child>
          <widget class="GtkLabel" id="lblError">
            <property name="visible">True</property>
            <property name="label" translatable="yes">--</property>
            <property name="use_markup">True</property>
          </widget>
          <packing>
            <property name="position">7</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>
```login.py:
```
#! /usr/bin/ python

import sys, gtk, os

class StartUp:

     def on_LoginWindow_destroy(self, widget, data=None):
         gtk.main_quit()
 
     def on_btnLoginCancel_clicked(self, widget, data=None):
         gtk.main_quit()

     def on_btnCancel_clicked(self, event):
         self.NewUserWindow.destroy()

     def on_btnClear_clicked(self, widget):
         #what goes here!?!?

     def on_btnNewUser_clicked(self, widget, data=None):
         
         builder = gtk.Builder()
         builder.add_from_file("new-user.xml")

         self.NewUserWindow = builder.get_object("NewUserWindow")
         builder.connect_signals(self)

     def __init__(self):
         builder = gtk.Builder()
         builder.add_from_file("login.xml") 
        
         self.window = builder.get_object("LoginWindow")
         builder.connect_signals(self)

     def main(self):
         self.window.show()
         gtk.main()

if __name__ == "__main__":
    start = StartUp()
    start.main()
```

---

### Post by sujoy on 2009-03-24
```
def on_btnClear_clicked(self, widget):
         #what goes here!?!?
```

what you need to do is set the text in the text entry to "", ie , blank string.
now i dont know how to do it in python, but that google can help you with i am sure

---

### Post by Chokkan on 2009-03-24
You're right, thanks for taking time to reply. I had tried doing something like that. and right now I just added:

```
def on_btnClear_clicked(self, widget, data="None"):
         self.LogName.set_text("")
```

I then added the following to the initial call to bring up NewUserWindow:

```
self.LogName = builder.get_object("entNewUserLogName")
```

And it works. One step along the road. :) It would be better if I could clear all the text entry boxes in one click though.

---

### Post by sujoy on 2009-03-24
> **Chokkan said:**
> You're right, thanks for taking time to reply. I had tried doing something like that. and right now I just added:

```
def on_btnClear_clicked(self, widget, data="None"):
         self.LogName.set_text("")
```

I then added the following to the initial call to bring up NewUserWindow:

```
self.LogName = builder.get_object("entNewUserLogName")
```

And it works. One step along the road. :) It would be better if I could clear all the text entry boxes in one click though.

yea well to clear all the text entry boxes just keep adding more
self.____.set_text("")
in the on_btnClear_clicked function one after another

---

### Post by Chokkan on 2009-03-24
Great! Thank you. 4am and I'm off to bed a happy man :D

---

