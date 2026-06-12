---
title: "[ C++ ] How to distribute applications based on GTK framework ?"
date: 2009-10-28
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-28
Platform: Windows

When I create an application in C++, which is based on GTK ( UI ), I don't see any difference, but that's just because of the fact that I've installed it's runtime - once I remove it, I can no longer use my app. Now, what should I do to make my application distributable ( so the user could just double-click and use it, without installing any additional packages ) ? What files do I need to include to be able to achieve this ?

---

### Post by TheBuzzSaw on 2009-10-28
I am interested in the answer to this question. However, I am more interested in how I go about creating a Windows installer that checks and installs the necessary GTK packages as well.

---

### Post by dwhitney67 on 2009-10-28
> **OpenGuard said:**
> Platform: Windows

When I create an application in C++, which is based on GTK ( UI ), I don't see any difference, but that's just because of the fact that I've installed it's runtime - once I remove it, I can no longer use my app. Now, what should I do to make my application distributable ( so the user could just double-click and use it, without installing any additional packages ) ? What files do I need to include to be able to achieve this ?

You would have to statically link in the GTK libs that your app requires.  I am not at all familiar with how windows defines static libraries (note these are not DLLs).

Anyhow, if you statically link in the libraries, expect to find that your application's executable file size to increase substantially.

---

### Post by OpenGuard on 2009-10-28
> **dwhitney67 said:**
> You would have to statically link in the GTK libs that your app requires.  I am not at all familiar with how windows defines static libraries (note these are not DLLs).

Anyhow, if you statically link in the libraries, expect to find that your application's executable file size to increase substantially.

```
#include <gtk/gtk.h>

int main (int argc, char *argv[])
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show (window);
    
    gtk_main ();
    
    return 0;
}
```As an example ( to not to make it too complicated ), how would I compile this code to get a stand-alone executable ( which can be launched, no matter what runtimes and whatnot the user have previously installed ) ?
[COLOR=Gray]** Google said it doesn't know anything about it ( only questions with no real answers ) ..[/COLOR]

---

### Post by TheBuzzSaw on 2009-10-28
Wouldn't statically linking in this manner violate the license on GTK?

---

### Post by OpenGuard on 2009-10-28
> **TheBuzzSaw said:**
> Wouldn't statically linking in this manner violate the license on GTK?

Would it ?

---

### Post by SledgeHammer_999 on 2009-10-28
Why do you use C++ with GTK? If you didn't know, there is gtkmm. Gtkmm is C++ bindings for GTK. link-->[www.gtkmm.org](www.gtkmm.org)

---

### Post by OpenGuard on 2009-10-28
> **SledgeHammer_999 said:**
> Why do you use C++ with GTK? If you didn't know, there is gtkmm. Gtkmm is C++ bindings for GTK. link-->[www.gtkmm.org]("http://www.gtkmm.org")

gtkmm is a C++ wrapper for the GTK engine - would that make any difference in terms of portability and ease of use ( from the point of a *dumb teenager* who doesn't know what GTK means, not to talk about how to install it ) ?

---

### Post by mmix on 2009-10-28
[http://gtk-win.sourceforge.net/home/index.php/en/Home](http://gtk-win.sourceforge.net/home/index.php/en/Home)

[http://dropline.net/past-projects/gtk-runtime-environment-for-windows/](http://dropline.net/past-projects/gtk-runtime-environment-for-windows/)

---

### Post by OpenGuard on 2009-10-28
> **mmix said:**
> [http://gtk-win.sourceforge.net/home/index.php/en/Home](http://gtk-win.sourceforge.net/home/index.php/en/Home)

[http://dropline.net/past-projects/gtk-runtime-environment-for-windows/](http://dropline.net/past-projects/gtk-runtime-environment-for-windows/)

Brilliant! Thank you :)

---

### Post by SledgeHammer_999 on 2009-10-28
> **OpenGuard said:**
> gtkmm is a C++ wrapper for the GTK engine - would that make any difference in terms of portability and ease of use ( from the point of a *dumb teenager* who doesn't know what GTK means, not to talk about how to install it ) ?

In terms of portabiility I think it is the same.
In terms of ease of use IMHO I think gtkmm is easier. Everything is handle in C++ terms. Eg a GtkButton is class named Gtk::Button which has all the functions that you use with a GtkButton*. Eg let's say you have Gtk::Button called my_button and a GtkButton* called my_gtk_button. To show the widget in gtkmm you just do a my_button.show(). In Gtk you do something like this gtk_widget_show(GTK_WIDGET(my_gtk_button)) that's ugly and needs more typing. Also with Gtkmm you don't need to play around with pointers(in most cases) and so you don't need to worry that much about unrefing widgets.

---

