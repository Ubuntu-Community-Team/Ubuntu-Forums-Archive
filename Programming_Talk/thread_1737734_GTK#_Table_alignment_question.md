---
title: "GTK# Table alignment question?"
date: 2011-04-23
forum: Programming Talk
---

### Post by Adrienk on 2011-04-23
So with the follwoing code I am saying Create a Table of size 1x1 and place menu in the top and fram in the bottom, upon running neither menu nor frame are showing even though both have .show on them, and the console spite out:

[I](Asis:6610): Gtk-CRITICAL **: IA__gtk_table_attach: assertion `left_attach < right_attach' failed

(Asis:6610): Gtk-CRITICAL **: IA__gtk_table_attach: assertion `left_attach < right_attach' failed[/I]

Which I dont understand. Upon reading the documentation of the table class and its method attach:

[COLOR=#000000][FONT=sans-serif][COLOR=#333333][FONT=Lucida Grande]**Syntax**

public [void]("t:System.Void") **Attach** ([Widget]("t:Gtk.Widget") widget, [uint]("t:System.UInt32") left_attach, [uint]("t:System.UInt32") right_attach, [uint]("t:System.UInt32") top_attach, [uint]("t:System.UInt32") bottom_attach)

**Parameters**
[INDENT]*widget*The widget to be attached to the table
*left_attach*The column number to attach the left side of *child* to. 
*right_attach*The column number to attach the right side of *child* to.
*top_attach*The row number to attach the top of *child* to.
*bottom_attach*The row number to attach the bottom of *child* to.I assumed that if there is no left or right you place a 0, much like in java when placing objects into a gui window using the table layout method,
How ever I seem to be wrong.

The code is below, could some one help me out?

```

using Gtk;
using System;

namespace Asis
{
    public class Asis
    {
        public void asisMain ()
        {
            Application.Init();
            
            //Create new window.
            Window asis = new Window("Asis Application");
            asis.SetSizeRequest(300, 300);
            asis.BorderWidth = 10;
            asis.DeleteEvent += whenExit;
            
            //Create a frame.
            Frame f = new Frame("Asis");
            f.ShadowType = (ShadowType) 4;
            
            //Create a tabel 1X1
            Table t = new Table(1,1, true);
            
            MenuBar mb = new MenuBar();
            Menu m = new Menu();
            MenuItem exit = new MenuItem("Exit");
            MenuItem file = new MenuItem("File");
            exit.Activated += new EventHandler(exitApp);
            m.Append(exit);
            file.Submenu = m;
            mb.Append(file);
            
            //Add objects to the tabel.
            t.Attach(mb, 0, 0, 1, 0);
            t.Attach(f, 0, 0, 0, 2);
            
            //Add items to window.
            asis.Add(t);
            
            //Show frame and menu
            f.Show();
            mb.Show();
            
            //Start the application.
            asis.ShowAll();
            Application.Run();
        }
        
        /// <summary>
        /// Quit the Application when the user clicks 
        /// File -> exit.
        /// </summary>
        /// <param name="obj">
        /// A <see cref="Object"/>
        /// </param>
        /// <param name="args">
        /// A <see cref="EventArgs"/>
        /// </param>
        static void exitApp(object obj, EventArgs args)
        {
            Application.Quit();
        }
        
        /// <summary>
        /// This method will allow for the user to 
        /// exit the application cleanly with out leaving 
        /// any residue behind. 
        /// 
        /// Used when the user clicks the "X" at the 
        /// top right hand corner.
        /// 
        /// Note: Unlike clicking exit from the menu,
        /// this method does not use event arguments instead
        /// it uses delete event arguments to cleanly dispose
        /// of the window and the process.
        /// </summary>
        /// <param name="obj">
        /// A <see cref="System.Object"/>
        /// </param>
        /// <param name="args">
        /// A <see cref="DeleteEventArgs"/>
        /// </param>
        static void whenExit(object obj, DeleteEventArgs args)
        {
            Application.Quit();
        }
    }
}

```[/INDENT][/FONT][/COLOR][/FONT][/COLOR]

---

### Post by Adrienk on 2011-04-24
Bump

---

### Post by steeleyuk on 2011-04-24
Your table size is set to 1x1 so essentially you can only have one widget in the table.

```
Table t = new Table(1,1, true);
```

If you change the numbers to 2, 2, you have a 2x2 table. 3, 2 creates a 3x2 table, etc.

The second and cause of the problem is the Attach method. Your positioning of the widgets are messed up.

```
t.Attach(mb, 0, 0, 1, 0);
t.Attach(f, 0, 0, 0, 2);
```

If you have a 2x2 table, and would like to add a widget to the top-left cell of the table, your values would be 0, 1, 0, 1 (left, right, top, bottom).

Another example would be a 3x3 table and wanting to show a widget in the middle cell. This would mean that your numbers on the Attach method would be 1, 2, 1, 2.

Of the four numbers in .Attach, the second needs to be greater than the first, and the fourth needs to be greater than the third.

Hope that explanation helps, though explaining attaching to tables can be a little difficult.

---

