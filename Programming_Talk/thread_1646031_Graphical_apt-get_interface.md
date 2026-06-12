---
title: "Graphical apt-get interface"
date: 2010-12-15
forum: Programming Talk
---

### Post by glilco on 2010-12-15
I want to make a script that installs a package in the user's system, and I don't want the installation runing in the shell but the graphical interface of installation that appears, for example, when you install the flash plugin in firefox.

Is there an easy way to do this?

---

### Post by shawnhcorey on 2010-12-15
Do you mean?

System -> Administration -> Synaptic Package Manager

---

### Post by glilco on 2010-12-15
no. I want a command that triggers some graphical installation of some especific package in the repository. For example, let's say I want to create a button to install flash player plugin. I don't want this button to open a console and launch apt-get install via command line, but do it in a graphical way.

If synaptics had a command "synaptics install package" that would be the command.

---

### Post by dwhitney67 on 2010-12-15
> **glilco said:**
> For example, let's say I want to create a button to install flash player plugin. I don't want this button to open a console and launch apt-get install via command line, but do it in a graphical way.


What's your plan?  Will you create a thousand buttons, one for each package that is available today, and then another thousand spare buttons for the yet-to-be-developed packages that will be available tomorrow?

If the "System->Administration->Synaptic Package Manager" is not what you want, then I suggest that you come up with a better set of requirements than what you have previously written.  Otherwise I doubt anyone will take you seriously.

---

### Post by Simian Man on 2010-12-15
Gdebi is closest to what you want, but I think it can only install local .deb files.  I guess you could "wget" the package from the repos manually and then install it with gdebi.

---

### Post by wojox on 2010-12-15
Also have a look a [Zenity]("http://live.gnome.org/Zenity"). But why reinvent the wheel?

---

### Post by glilco on 2010-12-16
dwhitney67, I don't want to create thousands of buttons, only a few buttons for some specific packages. I am working in an ubuntu based distribution for educational porpouses and the users are not experienced linux users. I want to put some menu buttons to install some specific packages, at the moment, java and flash plugin packages, but I don't want it to open a shell terminal.

Simian Man, gdebi would be great, but it haves the disvantage you pointed: the needing of download the packages.

wojox, my intention is not to reinvent the weel, but make something similar to what happens, for example, when you don't have the flash plugin installed in your computer and you try to access some flash content with firefox. Firefox does not opens a shell window running apt-get to install it but opens a graphical component to install the package.

---

### Post by wojox on 2010-12-16
> **glilco said:**
> 
wojox, my intention is not to reinvent the weel, but make something similar to what happens, for example, when you don't have the flash plugin installed in your computer and you try to access some flash content with firefox. Firefox does not opens a shell window running apt-get to install it but opens a graphical component to install the package.

Write a bash script and use zenity to do this. Here's a better link.

[http://library.gnome.org/users/zenity/stable/](http://library.gnome.org/users/zenity/stable/)

Open your terminal and run this:

```
zenity --info --text "glilco join us at http://www.fedoraforum.org/."
```

---

### Post by wojox on 2010-12-16
I forgot. Just remember to do all this installing you need Admin privileges for all, which isn't a good idea for  > users are not experienced linux users.

---

