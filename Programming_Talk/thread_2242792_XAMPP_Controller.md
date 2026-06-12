---
title: "XAMPP Controller"
date: 2014-09-04
forum: Programming Talk
---

### Post by dgriffiths on 2014-09-04
**[FONT=arial][SIZE=4][COLOR=#0000ff]Intro[/COLOR][/SIZE][/FONT]**

So I recently lost all of my non-Linux computers which means that ALL of my development work is now done on my primary Linux box! In the case of all my web development, I've chosen to use XAMPP... But I wanted a better control system than is available by default... something that had tighter OS integration. So... I wrote the first Python app I've written in a VERY long time in the form of an indicator applet for XAMPP. It's fairly simple, and has no real configuration... yet. Regardless, I intend to continue to build it out and improve it.


[LIST]
[*]Allows quick access to all major XAMPP commands 
[*]Includes quick access to phpMyAdmin, Webalizer, and localhost 
[*]Autodetects any installed sites (assuming you create them within the htdocs folder) 
[/LIST]

Hopefully someone other than me will find it useful, and I'll get some decent feedback on it!

If you have any thoughts, questions, comments, etc, speak up! Can't improve on a product without feedback!


[COLOR=#0000ff]**[FONT=arial][SIZE=4]Installation[/SIZE][/FONT]**[/COLOR]

```
sudo apt-add-repository ppa:dgriffiths/xampp-controller
sudo apt-get update
sudo apt-get install xampp-controller
```

Nice and simple!


[COLOR=#0000ff][SIZE=4][FONT=arial]**Usage**[/FONT][/SIZE][/COLOR]

Run xampp-controller (or add it to your Startup Applications). That's it!


**[COLOR=#0000ff][FONT=arial][SIZE=4]Screenshots[/SIZE][/FONT][/COLOR]**

[IMG]http://i2.wp.com/ghost1227.com/wp-content/uploads/2014/08/xampp-controller.png[/IMG]


**[COLOR=#0000ff][SIZE=4][FONT=arial]Support[/FONT][/SIZE][/COLOR]**

If you have questions or comments, feel free to post them here. If you want to contribute or open an issue, XAMPP Controller is [available on Github]("https://github.com/Section214/XAMPP-Controller")!


**[COLOR=#0000ff][SIZE=4][FONT=arial]Changelog[/FONT][/SIZE][/COLOR]**

**Version 1.0.5 (August 31, 2014)**
* Fixed about image reference
* Added option refresh menu

**Version 1.0.4 (August 30, 2014)**
* First stable release

---

