---
title: "gedit Gtk-WARNING **:"
date: 2011-06-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-06-23
So I do something simple like
sudo gedit /etc/grub.d/40_custom
which works.  This is Ocelot updated to 22 June.

What are all these messages about?

```

(gedit:18626): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkBox's child GtkImage 0x8701c98. Allocation is 16x1, but minimum required size is 16x16.

(gedit:18626): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.0W1WXV': No such file or directory

(gedit:18626): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

Thanks, Jerry

---

### Post by dino99 on 2011-06-23
first error flood xsession-errors log on my end
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798626](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798626)

the second message is about rights (file locked), create it if it does not really exist (empty file) or delete it otherwise.

---

### Post by MacUntu on 2011-06-23
You don't use 'sudo' with GUI programs. [https://help.ubuntu.com/community/RootSudo#Graphical sudo](https://help.ubuntu.com/community/RootSudo#Graphical sudo)

> **dino99 said:**
> the second message is about rights (file locked)
Uhm, no. It wants to create a file at a directory that doesn't exist.

---

### Post by sparker256 on 2011-06-23
> **jerrylamos said:**
> So I do something simple like
sudo gedit /etc/grub.d/40_custom
which works.  This is Ocelot updated to 22 June.

What are all these messages about?

```

(gedit:18626): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkBox's child GtkImage 0x8701c98. Allocation is 16x1, but minimum required size is 16x16.

(gedit:18626): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.0W1WXV': No such file or directory

(gedit:18626): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

Thanks, Jerry
When I use sudo nautilus I get something very similar but never seemed to prevent it from working so I just ignored it. 

Bill
```

bill@billsim-1110-64:~$ sudo nautilus
[sudo] password for bill: 
Initializing nautilus-gdu extension

(nautilus:3170): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate NautilusPathBar's child GtkButton 0x23e9c60. Allocation is 24x36, but minimum required size is 27x27.

(nautilus:3170): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkButton's child GtkArrow 0x21f6b40. Allocation is 12x24, but minimum required size is 15x15.

(nautilus:3170): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate NautilusPathBar's child GtkButton 0x23e9c60. Allocation is 24x36, but minimum required size is 27x27.

(nautilus:3170): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkButton's child GtkArrow 0x21f6b40. Allocation is 12x24, but minimum required size is 15x15.

(nautilus:3170): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate NautilusPathBar's child GtkButton 0x23e9c60. Allocation is 24x36, but minimum required size is 27x27.

(nautilus:3170): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate GtkButton's child GtkArrow 0x21f6b40. Allocation is 12x24, but minimum required size is 15x15.

(nautilus:3170): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to underallocate NautilusPathBar's child GtkButton 0x23e9c60. Allocation is 24x36, but minimum required size is 27x27.

```

---

### Post by dino99 on 2011-06-23
[QUOTE=sparker256;10971592]When I use sudo nautilus I get something very similar but never seemed to prevent it from working so I just ignored it. 

Bill

yes, but log is growing, growing, .... not stop :(

---

### Post by dino99 on 2011-06-23
> **MacUntu said:**
> You don't use 'sudo' with GUI programs. [https://help.ubuntu.com/community/RootSudo#Graphical sudo](https://help.ubuntu.com/community/RootSudo#Graphical sudo)


Uhm, no. It wants to create a file at a directory that doesn't exist.

have one at ~/.local/share/recently-used.xbel (user/user)

which differ from #1: root/

---

### Post by sparker256 on 2011-06-23
> **dino99 said:**
> [QUOTE=sparker256;10971592]When I use sudo nautilus I get something very similar but never seemed to prevent it from working so I just ignored it. 

Bill

yes, but log is growing, growing, .... not stop :(

Ok I am still trying to learn every day. Which log? And the proper command should be gksudo nautilus?

Thanks Bill

---

### Post by dino99 on 2011-06-23
> **sparker256 said:**
> [QUOTE=dino99;10971606]

Ok I am still trying to learn every day. Which log? And the proper command should be gksudo nautilus?

Thanks Bill

its .xsession-errors in your /home (ctrl+h to unhide it)

i suppose we still get this issue since complete gtk3 transition.

---

### Post by jerrylamos on 2011-06-23
> **MacUntu said:**
> You don't use 'sudo' with GUI programs. [https://help.ubuntu.com/community/RootSudo#Graphical sudo](https://help.ubuntu.com/community/RootSudo#Graphical sudo)

Uhm, no. It wants to create a file at a directory that doesn't exist.

With Oneiric Ocelot AMD64:

gksudo gedit started to edit then vanished.

sudo gedit worked, with a couple page fulls of error warnings..,,

Oh, well, I got done what I wanted to do.

Jerry

---

### Post by jerrylamos on 2011-06-23
Just tried leafpad.  It doesn't get all the WARNING messages that gedit does.

Jerry

---

### Post by Hairy_Palms on 2011-06-24
im fairly sure i remember reading something about this as a known bug currently of the gtk3 gedit, ill see if i can find a bug report at some point.

---

