---
title: "Blender and Crystal Space"
date: 2009-01-15
forum: Programming Talk
---

### Post by thefiestysoldier on 2009-01-15
I am working on a small game, I want to use Blender for modeling and animation and crystal space as an engine, I have seen the Blender plugin to output Crystal Space models, the deb files appear to be outdated, will the still work?

---

### Post by meatpan on 2009-01-16
Both Blender and Crystal Space have complicated dependencies, and contain modules that are frequently updated.  Consider using the latest versions from their web-sites, and be prepared to check the forums for troubleshooting info (particularly with Crystal Space).

---

### Post by thefiestysoldier on 2009-01-16
Thanks for the response, I have Blender installed just fine, I went to the Crystal Space to Blender plugin site, installed the repository (it hasn't been updated since Edgy):confused: and installed the plugin. It did not work (probably since it was outdated):mad:. Is there any way you or anyone else can help me (or at least tell me whether the project is dead or not):confused:, or should I go to the Crystal Space forums (I guess I will either way...)

---

### Post by hessiess on 2009-01-16
Ask on blenderartists.org, im sure that someone there will know, as YoFrankie used cristalspace.

---

### Post by Cracauer on 2009-01-16
CS itself is a little on the back burner. You didn't mention why you picked CS so I don't know whether you have "hard" reasons. But if you don't you might want to look at Ogre, too.

Not they don't have difficulties keeping the Linux port up-to-date, too...

---

### Post by thefiestysoldier on 2009-01-16
My friend and I are just making a game or 2 on the side, he is doing most of the programming and I am doing most of the modeling, it was hids idea  to use crystal space so I just figured he could program it easier than the blender engine. can ogre use blender models?

---

### Post by hessiess on 2009-01-17
> **thefiestysoldier said:**
> My friend and I are just making a game or 2 on the side, he is doing most of the programming and I am doing most of the modeling, it was hids idea  to use crystal space so I just figured he could program it easier than the blender engine. can ogre use blender models?

*Anything* can use blender models as long as you can export to it, and as blender has a lot of exporters built in, and many more on the web this is unlickly to be a problem;).

---

### Post by Cracauer on 2009-01-17
> **thefiestysoldier said:**
> My friend and I are just making a game or 2 on the side, he is doing most of the programming and I am doing most of the modeling, it was hids idea  to use crystal space so I just figured he could program it easier than the blender engine. can ogre use blender models?

Yes.
[http://www.ogre3d.org/wiki/index.php/Tools:_Blender](http://www.ogre3d.org/wiki/index.php/Tools:_Blender)

But I haven't done it myself, so YMMV.

---

### Post by Kilon on 2009-01-17
> **thefiestysoldier said:**
> I am working on a small game, I want to use Blender for modeling and animation and crystal space as an engine, I have seen the Blender plugin to output Crystal Space models, the deb files appear to be outdated, will the still work?

you can use JmonkeyEngine with jython. (100% python , syntax , can call Java libraries , C/C++ python libraries cannot be used)

[http://www.jmonkeyengine.com/](http://www.jmonkeyengine.com/)

---

### Post by thefiestysoldier on 2009-01-18
> **Kilon said:**
> you can use JmonkeyEngine with jython. (100% python , syntax , can call Java libraries , C/C++ python libraries cannot be used)

[http://www.jmonkeyengine.com/](http://www.jmonkeyengine.com/)

Do you mean that as an alternative game engine?

---

### Post by Kilon on 2009-01-19
> **thefiestysoldier said:**
> Do you mean that as an alternative game engine?

Jython is actually a version of python that does not use python libraries which are usually made with C/C++ only python libraries using pure python , and mainly JAVA libraries. No need for extra coding you can use any JAVA library directly as you would do with JAVA.

jMonkeyEngine is an excellent JAVA 3d engine, which you can use , yes as you main game engine. It looks pretty impressive.

---

