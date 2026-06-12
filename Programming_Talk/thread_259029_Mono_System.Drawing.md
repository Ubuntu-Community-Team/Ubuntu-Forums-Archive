---
title: "Mono System.Drawing"
date: 2006-09-16
forum: Programming Talk
---

### Post by grim918 on 2006-09-16
I am learing how to use mono and I am getting this error when I try to compile the program. I am using Gtk#. I got the program example from 
the mono-project.com website. [http://www.mono-project.com/GtkSharp:_Buttons](http://www.mono-project.com/GtkSharp:_Buttons)

here is the simple program that I am trying to compile:
> 
using Gtk;
using System;
using System.Drawing;

public class togglebuttons
{
        public static void Main(string[] args)
        {
                Application.Init();

                Window.window = new Window("Toggle Buttons");
                window.Resize(200,200);

                wndow.DeleteEvent += delete_event;

                /* Creating a new Toggle Button */
                ToggleButton togglebutton = new ToggleButton("button1");
                togglebutton.Clicked += clickedCallback;

                window.Add(togglebutton);
                window.ShowAll();

                Application.Run();
        }

        static void delete_event(object obj, DeleteEventArgs args)
        {
                Application.Quit();
        }

        static void clickedCallback(object obj, EventArgs args)
        {
                /* Check Active Property */
                if(((ToggleButton) obj).Active)
                        Console.WriteLine("ToggleButton clicked,I'm activating") ;
        }
}


I use this command to compile the program:
>  mcs -pkg:gtk-sharp-2.0 toggle.cs

And here is the compile error that I get:
> 
&#65279;toggle.cs(5,7): error CS0234: The type or namespace name `Drawing' does not exist in the namespace `System'. Are you missing an assembly reference?
toggle.cs(5,1): error CS0246: The type or namespace name `System.Drawing' could not be found. Are you missing a using directive or an assembly reference?
&#65279;    Try using -r:System.Drawing
toggle.cs(5,7): error CS0234: The type or namespace name `Drawing' does not exist in the namespace `System'. Are you missing an assembly reference?
toggle.cs(5,1): error CS0246: The type or namespace name `System.Drawing' could not be found. Are you missing a using directive or an assembly reference?
    Try using -r:System.Drawing
Compilation failed: 4 error(s), 0 warnings


Does anyone know How to make this work. I am using Dapper if thats any help. Thank you.

---

### Post by grim918 on 2006-09-16
Nevermind. I figured it out. If anyone comes across this problem just type the following in the command line:
> 
 mcs -pkg:gtk-sharp-2.0 -r:System.Drawing toggle.cs


---

### Post by solde9 on 2011-07-17
> **grim918 said:**
> Nevermind. I figured it out. If anyone comes across this problem just type the following in the command line:

Thank You! 

But, how it works?

---

### Post by cgroza on 2011-07-17
> **solde9 said:**
> Thank You! 

But, how it works?
It tells the compiler where to find the declarations it needs. Sort of like linking in C.

---

