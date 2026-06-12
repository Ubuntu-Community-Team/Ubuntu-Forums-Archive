---
title: "How do I do this?"
date: 2009-03-29
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2009-03-29
Hi guys

I was wondering if anyone had any idea how flash integrates with browsers?

I have and idea in planning stage that couls be used as a replacement for flash you see but I dont really know how to intergrate the system with a browser.

For instance, with friefox, do I make a firefox plugin? and what would I make for other browsers?

Any help or information would be great.

Thanks in advance.

Mike

---

### Post by tturrisi on 2009-03-29
AFAIK, for FF you need a plugin and for IE you need an ActiveX control.

---

### Post by Tomosaur on 2009-03-29
I may be wrong here - but I would imagine that the Flash player is a program which can play flash movies, whilst the 'plugin' is just a wrapper around it to ensure the browser can make use of it. So if you unpacked the IE and Firefox versions of the flash plugin, you would end up with the same thing - just the outer shell is different depending on the browser. It seems like it would be way too ridiculous to develop different Flash players for different browsers.

So while you will have to do a bit of work to make the codec / player whatever available to different browsers through their plugin system, the actual player itself is just a one time thing.

---

### Post by Mickeysofine1972 on 2009-03-29
but wouldn't I have to compile the player for each platform?

I think thats a yes but I'm not really certain

Mike

---

### Post by Tomosaur on 2009-03-29
> **Mickeysofine1972 said:**
> but wouldn't I have to compile the player for each platform?

I think thats a yes but I'm not really certain

Mike

Maybe not - I suppose it depends on your implementation. Java applets don't need to be re-compiled to work on different platforms - the only requirement is that the user has Java installed. However, there aren't really that many platform independent environments that a user is likely to have installed except Java, and you probably don't want to go anywhere near Java for a Flash replacement :P

Is there a reason why you don't want to compile the player for different platforms?

---

### Post by Mickeysofine1972 on 2009-03-29
nope no reason I'm kind of brain storming really.

The idea I have is this:

CurvedInfinity has open sourced his excellent games plat for mirthkit which you can now get from launchpad.

Last year when he and I were talking about his platform I mentioned that it would also be a goo thing if you could get a basic player that would work in a browser.

Currently, it compiled for windows and linux as a standalone, but i recon I could have a good stab at making it into a browser player and in the process make an alternative to flash.

Its actualy not that far off flash really, it just needs to remove the opengl rendering and be replaced with 2d rendering instead, or maybe it could be opengl I'm not sure atm.

Mike

---

### Post by Tomosaur on 2009-03-29
> **Mickeysofine1972 said:**
> nope no reason I'm kind of brain storming really.

The idea I have is this:

CurvedInfinity has open sourced his excellent games plat for mirthkit which you can now get from launchpad.

Last year when he and I were talking about his platform I mentioned that it would also be a goo thing if you could get a basic player that would work in a browser.

Currently, it compiled for windows and linux as a standalone, but i recon I could have a good stab at making it into a browser player and in the process make an alternative to flash.

Its actualy not that far off flash really, it just needs to remove the opengl rendering and be replaced with 2d rendering instead, or maybe it could be opengl I'm not sure atm.

Mike

Good idea. With respect to the opengl - I think the only reason you may need to worry about this is the overhead. Although I may be completely wrong here - I'm pretty sure you could still use OpenGL rendering in a browser plugin.

---

### Post by Mickeysofine1972 on 2009-03-29
Ok 

Well thats the brainstorming done!

Now I better get some research done! Linux first i think!

If anyone wants to help out then feel free :D

Mike

---

### Post by haemulon on 2009-03-29
I've read a few things around the internet about OpenGL bindings/integration with Javascript.

Is this the sort of thing you have in mind?

---

### Post by Mickeysofine1972 on 2009-03-29
Not really, Mirthkit has its own language built in called Squirrel

Mike

---

