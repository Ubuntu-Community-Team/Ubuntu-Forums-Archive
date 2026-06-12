---
title: "Comic Development Kit: looking for help"
date: 2006-09-23
forum: Programming Talk
---

### Post by HanZo on 2006-09-23
I started this thread in the art-talk section but moved it here thanks to Omnios suggestion.

I'm a comic artist and illustrator and I have this little idea I'd really like to put into practice, it's called Comic Development Kit and it's basically about combining the idea of open source software and comic making.
I'm posting this here because I'd need some help on the matter... but more about that later, first I'm going to explain a bit what this is all about.

I imagine it should work something like this: there is a client software you download from the website that is something like inkscape, a vector based software that has two main modes: comic creation and object editor.
in comic creation you have a page where you can put panels and assemble your comic strip using pre-made parts (heads, bodies, objects, backgrounds, balloons and stuff). The objects can be dragged on the page from a kind of gallery (the objects should be stored on a central server, not locally).
in the object editor you can create a new object (which will be saved on the above mentioned central server) or edit an already existing one (in this case the oject will be saved on the server with a higher revision number).
once you have made your comic you can save it, this stores it on the server. optionally you can save it locally export it in some common format or print it.
The software should be available at least for linux, windows and osx.
for the whole process no proprietary software or format should be used (I was thinking about svg as default format).

so as you see the whole thing is pretty much about collaborative comic creation, about refining objects and enlarging the available object pool (wiki style).

other ideas could be the possibility of making "creation packs", packs that contain a fair number of characters and objects for a certain genre. Somebody could make a pack so others could make stories with it.

Now... I'm not a developer... and I don't have a lot of experience on how things work in the oss world, that's why I'm looking for help here. Basically right now I'd like to find out about the following things:

    * is it feasable, generally speaking... or will it take ages to put something like this in to practice?
    * could it be possible to use the sourcecode of a vector drawing app like inkscape to develop the client for this?
    * or should I try to do this with a webbased app (java applet?)
    * how are things usually working on systems like sourceforge? how are things organized?
    * is there anybody interested in helping me out on the coding side for this?
    * would you use it?
    * do you like the idea?


any help on this is really appreciated!

---

### Post by Tomosaur on 2006-09-23
Well, most programmers try to avoid reinventing the wheel, so it's likely that for this project, the source of Inkscape will indeed be modified (if you were set on .svg format anyway.) What would the comics be used for? They would need to be exported to .png before being displayable in a web-browser, if that's what you're thinking, since (I think) only Safari and Amaya currently support the .svg format.

The project itself doesn't sound like it would be impossible, since a lot of the features it requires are basically all there for people to borrow and use, and I would think Python would be the language of choice for this, since there are only very minor problems with cross-platform compatability. A client program would probably be best - complex .svg files are pretty large due to their  nature, and it doesn't take a brain surgeon to foresee slow service if the whole frontend is web-based too. I would question the wisdom of saving to the server by default - and I would recommend you rethink this. Saving locally allows the user much more freedom, and time, to edit their images. 

The creation pack idea is good - but you'd have to be careful about packs with only minor differences - so perhaps a moderating team would be beneficial to compare packs and reject the ones which aren't so great. You don't want your server getting clogged up with packs nobody wants to download.

Sourceforge moderates which projects are allowed - but it's not too strict or anything. It basically just doesn't want morons wasting server space and bandwith. I think you also need to give them a decent specification of your project - I doubt this description here would suffice.

All in all, I do really like this idea. I'd probably use it to play around with, but I doubt I'd pay for it. I don't personally have the time, and probably not the skill (yet :P ) to help out with this, but I do hope you get it off the ground.

---

### Post by DarkN00b on 2006-09-23
[quote="Tomosaur"]Well, most programmers try to avoid reinventing the wheel, so it's likely that for this project, the source of Inkscape will indeed be modified (if you were set on .svg format anyway.) What would the comics be used for? They would need to be exported to .png before being displayable in a web-browser, if that's what you're thinking, since (I think) only Safari and Amaya currently support the .svg format.[/quote]

Firefox is displaying [the Ubuntu badge]("https://wiki.ubuntu.com/PoweredBy?action=AttachFile&do=get&target=poweredbyubuntu.svg") .svg just fine.  Of course I'm on my windows machine at the moment, and can't check if it works in Ubuntu.

---

### Post by Tomosaur on 2006-09-23
Well I never, last time I checked it didn't work.

Still, on my (Windows) machine here, the .svg is a little messed up. SVG support is still patchy at best I reckon.

---

### Post by DarkN00b on 2006-09-23
[quote="From the WIKI"]NOTE: I know that the Powered by Xubuntu SVG file looks goofy on the page, however it is actually a good file, it just renders incorrectly on the wiki.[/quote]

The WIKI page even says it renders funny in browsers. I would guess that this is because of lack of real support for .svg files.  The wiki is [here]("https://wiki.ubuntu.com/PoweredBy").

---

### Post by HanZo on 2006-09-23
thanks for the replies guys, and thanks especially to Tomosaur.
I'm not planning to make a program for commercial purposes, the idea is to take the way oss works apply it to comics, so basically I'd like all the software involved in the project to be opensource and the client itself should be opensource as well.
I think you are right with boh the server thing and the moderating team. maybe it's better to have the client download only what is needed, maybe every object should have a lighweight png tumbnail that gets downloaded automatically by the app when you open it.
Anyway I have a moderation team already, since this project should be made as part of our monipodio project ([www.monipodio.net)](www.monipodio.net)). monipodio is magazine so the editorial staff would probably be the moderation team (plus maybe some people who show great interest in the project and want to be part of it).
Anyway... the comics would not have a use, I'd like to have a website displaying a screen res png of every strip created. and I'd like to print a magazine with the best strips created with the CDK.

---

### Post by Ravenseye on 2006-09-28
I am not a programmer, but I have an idea you might be able to run with based on another project out there. :)

First of all, check this out: [http://www.diyplanner.com/](http://www.diyplanner.com/)

You can download the project here: [http://www.diyplanner.com/templates](http://www.diyplanner.com/templates)

What this project allows is for people to create their own organizer using recycleable elements created in OpenOffice. The site accepts user-created add-ons and has been fairly successful so far :)

I don't know how immediately useful this would be for you, but as a bit of inspiration for ya, I'd give it a shot :) One huge advantage is that the tools are already there for you to use, so no reinventing the wheel there.

-Mike

---

### Post by HanZo on 2006-09-30
tnx for the tip! this thing looks interesting... it's not exactly what I'm planning to do... but maybe I can find some inspiration for a less complicated version of my CDK... i.e. one where I don't need anybody doing any programming...

---

### Post by Knark on 2008-12-02
Nice to see other comic loving people using Linux. 
The idea itself, I'm not too happy about I must admit. If I got it right, you want to make a "do it yourself" package for people where everything is served for them? Sounds like a program for kids, I think we need something more serious for grown up people who want to make their OWN comics, unless it was targeted for kids in the first place then it is all fair :) 

A comic making kit where you are able to put in speech bubbles, make the right layout for your pages, fix the size of several pages at once so they all fit, spell checking system and so on. That kinda stuff, I personally think would be appreciated a lot more. But I'm glad to see someone suggest new things for Linux, where you can use your artistic skills, because that's a weak spot when it comes to this system. Sometimes Gimps just not enough :)

---

