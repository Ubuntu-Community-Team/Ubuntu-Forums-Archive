---
title: "Need advice for new project."
date: 2011-08-15
forum: Programming Talk
---

### Post by cgroza on 2011-08-15
Hello everyone.
I have started working on a new project. It is called LinSnap and it should be a tool for
taking and managing screenshots. Similar to LittleSnapper.
Linux lacks one and I though I could make one.

I need advice on how to keep information about the index files.
My first idea was to keep a file in every indexed directory with information about every file in it, such as tags, path, name and so on.

My second idea was to use a sqllite database to do that.

I don't have any experience with such tasks, and never worked with databases.
So I am asking you about new approaches and what would be the drawbacks and advantages of every approach.

Thank you.

---

### Post by PaulM1985 on 2011-08-16
Why not have a directory that stores all of the screenshots?  For each screenshot there could be a corresponding XML file containing information about the screenshot.  Something like:
screenshotdir\shot0001.jpg
screenshotdir\shot0001.xml

This could give you a basic start point for developing your application.  Once you have more of a base and more info on the sort of thing you want to store you can make more decisions on storage.  XML could either be your final approach or something for your prototype stage.

Paul

---

### Post by amauk on 2011-08-16
What information do you want to store? and more importantly why?

Storing the path is a really bad idea, as you'll never keep it consistent
Think hardlinks, symlinks, bind-mounts, disk images mounted via loopback devices, etc. etc.

Any other user-generated metadata is probably better delegated to a proper semantic tagging framework like zeitgeist (as used by Unity & Gnome 3, possibly others as well)

In essence, all a screenshot application should do is take screenshots

---

### Post by cgroza on 2011-08-16
Thank you for your tips.
I have finally decided that I will have a file in my config folder for each indexed folder.
I will read them at start-up and turn them into an internal data structure, update them in memory and write them back.
It will make it easy for me to handle the data.

---

### Post by ofnuts on 2011-08-16
> **cgroza said:**
> Thank you for your tips.
I have finally decided that I will have a file in my config folder for each indexed folder.
I will read them at start-up and turn them into an internal data structure, update them in memory and write them back.
It will make it easy for me to handle the data.Image formats support integrated metadata (IPTC fields or plain comments). That would be a good place to keep your file data.

---

### Post by cgroza on 2011-08-16
> **ofnuts said:**
> Image formats support integrated metadata (IPTC fields or plain comments). That would be a good place to keep your file data.
Yeah, I took a look at that first, but could not find anything relevant about PNG.
Edit, iptcinfo library seems to be what I need.
Thanks a lot.

---

### Post by jmartrican on 2011-08-17
For data persistence you can try a berkley DB file.  Its basically a persistent hashmap that you can access with the berkleydb library.  I have not used it in a long while but I remember thinking that it was better tthan a database for small stuff.

---

### Post by nvteighen on 2011-08-17
I'd go for a central directory. A filesystem is already a type of DB (one meant for storing files) and you already know the interface. Also, because I guess it could be interesting to leave the "database" easily accessable for other utilities, say backup programs or anything.

Not that a "proper" DB wouldn't work, but I prefer to go with the apparently simplest solution.

---

### Post by Tom Dignan on 2011-08-17
> **amauk said:**
> 
In essence, all a screenshot application should do is take screenshots

I'm going to second this. Your screenshot app has no business creating a database to store a list of screenshots. There are already image management tools in every desktop that do that. Just save the screenshot as the current date, or as a unique identifier unless the user picks a name for it. 

If you want to add features, maybe do something like automatic uploads to imgur? Do something people don't already have with something else...and something that is easy.

---

### Post by cgroza on 2011-08-17
> **Tom Dignan said:**
> I'm going to second this. Your screenshot app has no business creating a database to store a list of screenshots. There are already image management tools in every desktop that do that. Just save the screenshot as the current date, or as a unique identifier unless the user picks a name for it. 

If you want to add features, maybe do something like automatic uploads to imgur? Do something people don't already have with something else...and something that is easy.
I want a Linux alternative for the MacOS application LittleSnapper. The app will do much more than organizing screenshots, it will offer an interface to upload them to different services.

---

### Post by cgroza on 2011-08-17
> **nvteighen said:**
> I'd go for a central directory. A filesystem is already a type of DB (one meant for storing files) and you already know the interface. Also, because I guess it could be interesting to leave the "database" easily accessable for other utilities, say backup programs or anything.

Not that a "proper" DB wouldn't work, but I prefer to go with the apparently simplest solution.
This is one of the approaches I have in mind. I can't decide between storing my screen shot tags in the PNG images themselves, or storing them in a central collection file.

---

### Post by nvteighen on 2011-08-17
> **cgroza said:**
> This is one of the approaches I have in mind. I can't decide between storing my screen shot tags in the PNG images themselves, or storing them in a central collection file.

I'm not familiar with the PNG format specs, but as a general advice, use tags for what they are specified to be used and use a different metadata system for anything else that you might need. In other words, don't fall into the temptation of using PNG metadata store arbitrary data just because it happens to fit there! :P

I like the approach suggested by PaulM1985: to use an XML file named exactly as the PNG one. I like it for several reasons: 1) you'll avoid writing a parser, 2) you can write an XML spec in the form of a DTD protocol, so that you actually create a documented XML sublanguage for your own purposes, 3) it doesn't interfere with anything and you're using a tool that's actually meant for this kind of tasks and 4) specifically having the XML file be exactly where the screenshot is may make things much easier (though this should be tested!). Now, there's a drawback: someone could break the XML-PNG relation by e.g. renaming the PNG file but not the XML one. IMO, that's a reasonable risk, because it's essentially the user's fault not to respect the program's conventions... :P 

The alternative of using a unique XML file that stores all metadata for all PNG files may have the additional advantage of having to parse one single metadata file for the whole collection, but you may end up simultaneously holding all objects that represent all images at the same time.

---

### Post by cgroza on 2011-08-17
> **nvteighen said:**
> 

I like the approach suggested by PaulM1985: to use an XML file named exactly as the PNG one. I like it for several reasons: 1) you'll avoid writing a parser, 2) you can write an XML spec in the form of a DTD protocol, so that you actually create a documented XML sublanguage for your own purposes, 3) it doesn't interfere with anything and you're using a tool that's actually meant for this kind of tasks and 4) specifically having the XML file be exactly where the screenshot is may make things much easier (though this should be tested!). Now, there's a drawback: someone could break the XML-PNG relation by e.g. renaming the PNG file but not the XML one. IMO, that's a reasonable risk, because it's essentially the user's fault not to respect the program's conventions... :P 

The alternative of using a unique XML file that stores all metadata for all PNG files may have the additional advantage of having to parse one single metadata file for the whole collection, but you may end up simultaneously holding all objects that represent all images at the same time.

It seems I will do what you suggested me. An XML file for every collection.
I think I will also scan the collections at startup and remove the XML entries of non existent files. I will offer functionality to rename files via my program, since that is what the user will use to manage his files anyway.

Thanks.

---

