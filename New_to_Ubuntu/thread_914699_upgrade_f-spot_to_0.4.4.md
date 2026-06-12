---
title: "upgrade f-spot to 0.4.4?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by epidemiks on 2008-09-09
I'm using f-spot 0.4.3.1, but the latest version in 0.4.4.

I've got the tar ball, and  about to install it, but will it 'upgrade' the version I'm using or create a 'new' version?

Also, why doesn't this update appear in synaptic?

Cheers!

---

### Post by SunnyRabbiera on 2008-09-09
Usually the repositories update on more important matters like security updates, if this is a minor bug fix version then dont expect it in the repositories.
I would not worry about the new Fspot, if this is just a small bug fix version it wont matter much.

---

### Post by epidemiks on 2008-09-09
ah ok, the f-spot folk reckon they've done a bit of work though..

>     *  various FullScreen enhancements: fading widgets, snapped on screen edges, ...
    * rating with hotkeys: use Alt-0 to Alt-5 in browse or edit mode to rate
    * reduce startup time by ~40%, depending on your db size
    * push back the "sort tag by popularity" feature removed on 0.4.3.1
    * choose the theme you prefer for f-spot, even switch theme without restart with gtk-sharp 2.12.2
    * reduce the verbosity of the output log. use --debug for full debugging output
    * migrate CDExport to gio for gnome 2.22
    * an insane amount of other fixes, new capabilities, updated translations and refactoring 

so just as an excercise in knowing, what happens to the existing install if i install 0.4.4 from a tarball?

---

### Post by Archmage on 2008-09-09
The next Ubuntu-version will have 0.44. I would suggest to wait and upgrade the whole since this way you know that it is stable and tested.

---

### Post by SunnyRabbiera on 2008-09-09
Nothing really, if you are able to compile from source then install it then it should just replace the one you have.
But really I would just hold out until this is out of the development phase on launchpad before installing it. look here:
[https://launchpad.net/ubuntu/+source/f-spot](https://launchpad.net/ubuntu/+source/f-spot)

now you can get a binary here but I would just hold off, latest doesn't always mean greatest you know.
[http://packages.ubuntu.com/intrepid/f-spot](http://packages.ubuntu.com/intrepid/f-spot)

---

### Post by epidemiks on 2008-09-09
thanks for the info guys. I'll wait.

---

### Post by SunnyRabbiera on 2008-09-09
The thing is that if the package is in development phase its just better to avoid it till its officially out.
Besides this package will be in Ibex by next month anyway, ibex is the next ubuntu release.

---

