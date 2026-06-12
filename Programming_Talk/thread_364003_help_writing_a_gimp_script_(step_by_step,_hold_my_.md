---
title: "help writing a gimp script (step by step, hold my hand, I'm ignorant)"
date: 2007-02-17
forum: Programming Talk
---

### Post by towsonu2003 on 2007-02-17
As I use gimp more and more, I feel the need to write my own macros (called script-fu in gimp) for it. But as I found, it is almost impossible for a non-programmer to write a script-fu without learning how to program...

Can anyone help me write this script-fu? I'll release it under GPL if I somehow manage to write... I tried, but I can't even find the right way to duplicate the Background layer using the script-fu console :(

Here is what I want this script-fu to do:

After I open my image, it will:
1. Duplicate the "Background" layer three times (new layers will be called "WorkLayer", "White", "Black")
2. On the "WorkLayer", use Levels tool to set white to 12 and black to 240
3. On the "White" layer, use Threshold to put the left-hand slider almost all the way to the right (set the number on the left side to about 230) => the whitest point in this layer will then be used *by the user* as a reference point to set the white point of the picture using Levels
4. On the "Black" layer, use Threshold to put the left-hand slider almost all the way to the left (set the number on the left side to about 20) => the blackest pont in this layer will then be used *by the user* as a reference point to set the black point of the picture using Levels
5. On the "WorkLayer", increase saturation by 20
6. Stop, may be let the user know with a pop up that it's done. 

What I'm trying to do is to [implement this tutorial]("http://gimparoo.blogspot.com/2007/02/basic-photo-retouching.html") as a script-fu. It seems like a very good way to start touching any pictures... 

Of course, a better option would be to submit a patch to gimp for the ability to record macros, but I'm no programmer. If you feel brave enough for this, have a look at the following links:

[http://bugzilla.gnome.org/show_bug.cgi?id=51937](http://bugzilla.gnome.org/show_bug.cgi?id=51937) (upstream bug report for this)
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/85899](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/85899) (corresponding ubuntu bug)
[https://blueprints.launchpad.net/ubuntu/+spec/gimp-record-macro](https://blueprints.launchpad.net/ubuntu/+spec/gimp-record-macro) (feature request)
[https://launchpad.net/bounties/gimp-macro-recorder/](https://launchpad.net/bounties/gimp-macro-recorder/) (bounty for this)

Thanks a lot :)

---

### Post by carla on 2007-03-11
:popcorn: Found some good tutorials for you:

[LIST]
[*][http://www.gimp.org/docs/scheme_plugin/](http://www.gimp.org/docs/scheme_plugin/)
[*][http://developer.gimp.org/plug-ins.html](http://developer.gimp.org/plug-ins.html) (three-parter!)
[*][http://www.gimp.org/docs/plug-in/plug-in.html](http://www.gimp.org/docs/plug-in/plug-in.html)
[*][http://www.gimp.org/docs/python/pygimp.html](http://www.gimp.org/docs/python/pygimp.html)
[*]From the GUG (Gimp Users Group): [Scheme Basics]("http://gug.sunsite.dk/tutorials/tomcat3/"); [How to Create a Script-Fu]("http://gug.sunsite.dk/tutorials/titix1/");[Batch Gimp]("http://gug.sunsite.dk/tutorials/tomcat17/"); and [IF-WHILE]("http://gug.sunsite.dk/tutorials/thepeach1/")[/LIST]

---

### Post by towsonu2003 on 2007-03-12
> **carla said:**
> :popcorn: Found some good tutorials for you:

[LIST]
[*][http://www.gimp.org/docs/scheme_plugin/](http://www.gimp.org/docs/scheme_plugin/)
[*][http://developer.gimp.org/plug-ins.html](http://developer.gimp.org/plug-ins.html) (three-parter!)
[*][http://www.gimp.org/docs/plug-in/plug-in.html](http://www.gimp.org/docs/plug-in/plug-in.html)
[*][http://www.gimp.org/docs/python/pygimp.html](http://www.gimp.org/docs/python/pygimp.html)
[*]From the GUG (Gimp Users Group): [Scheme Basics]("http://gug.sunsite.dk/tutorials/tomcat3/"); [How to Create a Script-Fu]("http://gug.sunsite.dk/tutorials/titix1/");[Batch Gimp]("http://gug.sunsite.dk/tutorials/tomcat17/"); and [IF-WHILE]("http://gug.sunsite.dk/tutorials/thepeach1/")[/LIST]

thanks -I guess I'll have to learn a bit of programming... :)

---

### Post by carla on 2007-03-12
> **towsonu2003 said:**
> thanks -I guess I'll have to learn a bit of programming... :)

1. Don't be intimidated.
2. Almost every one of those links has an example plugin/script that they build with you.
3. I need to learn how to do this, too, so we could buddy up and learn via this thread. :)
4. forgot one resource: [Gimp Flickr Group's discussions]("http://flickr.com/groups/gimpusers/discuss/") -- esp. check [this thread]("http://flickr.com/groups/gimpusers/discuss/72157594521838760/") out :guitar:

---

