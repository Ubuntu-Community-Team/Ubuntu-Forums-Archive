---
title: "cannot find Firefox plugins folder"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by GMachine_24 on 2008-09-02
Hi:

I have been using Ubuntu for several years and have always managed to install Java as per instructions found on the Java Web site. Until now.

This page:

[http://www.java.com/en/download/help/5000010500.xml#enable](http://www.java.com/en/download/help/5000010500.xml#enable)

says to find the firefox/plugins (which it locates at /usr/lib/firefox/plugins)

however

In my 8.04 LTS installation there is no such location to create a symbolic link to my Java installation. I created a symbolic link at /usr/lib/mozilla/plugins but this does not solve the problem.

In past distributions, I was able to find the plugins folder for the Firefox browser, and this was different from the plugins folder for Mozilla - but I do not seem to be able to locate it in this distrbution. Can anyone tell me where it is or what I am doing wrong?

Thanks in advance.

---

### Post by lapubell on 2008-09-02
you can create the folder /usr/lib/firefox/plugins and try it.

---

### Post by tuxxy on 2008-09-02
You could also open a terminal and type

```
locate firefox/plugins
```

This may provide you with the current folder you are using.

---

### Post by GMachine_24 on 2008-09-02
OK, it's located at:

/usr/lib/firefox-3.0.1/plugins


Creating my own folder under /usr/lib/firefox did not work. I had already tried it.

GM

---

### Post by tuxxy on 2008-09-02
> **GMachine_24 said:**
> OK, it's located at:

/usr/lib/firefox-3.0.1/plugins


Creating my own folder under /usr/lib/firefox did not work. I had already tried it.

GM

Sounds like you found it, try and move the plugins there, you can also confirm this is the correct folder by typing this into your browser addess bar

```
about:plugins
```

Check the installed plugins in your broswer match the ones in the directory you found.

---

### Post by MentalNotes on 2008-09-02
Firefox in Hardy is built on top of xulrunner. Currently, as far as I can see, plugins live in /usr/lib/xulrunner-addons/plugins. A helpful option in Firefox is to go to about:config and set plugin.expose_full_path to true. This shows the full path of the plugin when you look at about:plugins.

---

### Post by kansasnoob on 2008-09-02
Did you know that sun-java6-**** is in synaptic? I always just go to synaptic and install all sun-java6-**** except -docs and -source.

---

