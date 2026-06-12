---
title: "Web Development Issue"
date: 2007-10-02
forum: Programming Talk
---

### Post by RyanZec on 2007-10-02
I am trying to remove everything from i need to do on windows except windows programming(no way around that).  Besides gaming and C++ programming, I do a lot of web development.  The only issue with web development is IE(which along is a issues but i will not get into that).  it there a way i can test web tests in at least IE7(IE6 would be nice too) on ubuntu?

---

### Post by justinjacobs on 2007-10-02
For IE6, IE5.5, and IE5, there's [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").

If you want to run IE7, I think the only way as of now would be to run an installation of Windows XP in something such as VMWare or Virtualbox.

---

### Post by RyanZec on 2007-10-02
i can actually run the entire Window OS in some linux VM software?

---

### Post by aks44 on 2007-10-02
> **RyanZec said:**
> i can actually run the entire Window OS in some linux VM software?

With a few limitations, yes. It will be a bit slower than native Windows, you can't do 3D, and you need a decent RAM amount (your comp must be able to fit both Ubuntu and Windows in RAM at the same time... better have at least 1Go).

But VirtualBox's "Seamless mode" is a killer... :D


FWIW I have IE7, 6, 5.5 and 5 in my Windows VM (could have installed IE4 and 3 too but they are not worth the pain ;)). Plus Firefox, Opera and Konqueror in Ubuntu. Kinda neat for testing / debugging cross-browser issues.

---

### Post by Samhain13 on 2007-10-02
There's an IEs4Linux installer that allows you to include IE7 in the installation. It uses the IE6 GUI and settings though but I find it suitable for viewing how the page rendered in IE7.

---

### Post by MicahCarrick on 2007-10-02
I explain a lot of this in _[Web Development in Linux (GNOME)]("http://www.micahcarrick.com/09-28-2007/web-development-linux.html")_.

Linux is actually advantageous to web developers as you'll catch those problematic font and IE-hackery that you might otherwise not notice if programming just in Windows.

In linux, you can test using IE, Firefox, Konqueror (similar to Safari in terms of rendering CSS and JS), Opera, Netscape, Mozilla, and many more.

---

### Post by Jonne on 2007-10-02
for testing IE, virtualisation is the way to go. Either use vmware or virtualbox. If you're running Windows you need to run a virtual machine anyway to test for the other IE versions, as you can't have them on the same install reliably, so you might as well use Ubuntu as the host OS.

---

### Post by aks44 on 2007-10-02
> **Jonne said:**
> If you're running Windows you need to run a virtual machine anyway to test for the other IE versions, as you can't have them on the same install reliably

Strange then that I have 4 versions of IE on the same install, all working as expected including conditional comments etc...

---

### Post by mridkash on 2007-10-03
> With a few limitations, yes. It will be a bit slower than native Windows, you can't do 3D, and you need a decent RAM amount (your comp must be able to fit both Ubuntu and Windows in RAM at the same time... better have at least 1Go).

I'm learning to use 3ds max and keep windows for that, now I'm planning to shift to virtual box for windows.

Will 3ds max work there, I have ample RAM (1.5 gb)?

---

