---
title: "C++ &amp; Gnome"
date: 2007-12-07
forum: Programming Talk
---

### Post by clash on 2007-12-07
Hey guys, want to start writing a bit of code on gnome.

I haven't really being paying much attention to the whole linux development world for the last couple of years. 

Can anyone recommend a ide ? I used Anjuta before but sorry to say am not a fan. Is there a howto on how to use glade3 developed gui's with anjuta etc ? 

Thanks.

---

### Post by daou on 2007-12-07
Eclipse is nice. Besides C/C++ you can program in any  of the more popular languages with the right plugins. It also has countless other useful plugins (I find the SVN plugin invaluable to my work).
It is a bit heavier than the other IDE's because it's coded in Java. But I recommend the Eclipse Europa version which has just the C/C++ environment, it's much faster. As for Glade, I recommend you just use the Glade interface designer that spits out an XML file. It's quite easy to maintain. Then just load the XML file in your code. Good for small projects, but the bloat can be a problem for bigger ones.

---

### Post by Auria on 2007-12-07
There's also Code::Blocks (my favorite), KDevelop

---

### Post by MicahCarrick on 2007-12-07
There is also OpenLDev, a more light weight IDE. I prefer working in Gedit and Glade3 individually.

I have a pretty comprehensive glade 3 tutorial in the works which I should post on my blog once it's proof read and some fact checking is done.

---

### Post by subs on 2007-12-07
python would be a good choice

---

### Post by mannequin on 2007-12-07
As a friend of the developer of OpenLDev, I can say that it's not being developed anymore. :(

It would be cool if we could find someone that would be interested in picking it back up. :)

The current release (1.0) has a couple of bugs that tend to stop it from starting up. The SVN version fixes these, but there are still some bugs that need to be killed before it would be ready for any sort of 1.1 (or whatever) release.

@Auria: How does Code::Blocks work for C development? I'm in the game for a good IDE for C development now that OpenLDev has stopped being developed.

@subs: How does Python help with _**C++**_ and Gnome?

-M.

---

### Post by Auria on 2007-12-07
> **mannequin said:**
> 
@Auria: How does Code::Blocks work for C development? I'm in the game for a good IDE for C development now that OpenLDev has stopped being developed.
.

Fairly well i find. But you better try by yourself, of course. If you like very light IDEs you might in the end prefer a programmer's text editor

---

### Post by Geekkit on 2007-12-07
> **Auria said:**
> Fairly well i find. But you better try by yourself, of course. If you like very light IDEs you might in the end prefer a programmer's text editor

Hear, hear. I find that using Geany and Glade together work best for me. I like light and fast and I'm a bit of a control freak so I like to write the make files myself. :)

Geany reminds me of Editplus in Windows and that's what I used to use there.

Also, if you are okay with an extra library then use Glade 3 like you said. If however you want to keep it simple then you may wish to revert to Glade 2. The difference being is that Glade 2 generates the source code for you whereas Glade 3 requires you to use the glade library during runtime to read in your XML files.

---

### Post by mannequin on 2007-12-07
> **Auria said:**
> Fairly well i find. But you better try by yourself, of course. If you like very light IDEs you might in the end prefer a programmer's text editor
I like any IDE that works well with my tastes. Emacs, then OpenLDev did that for me. But I've now had to move back to Emacs. (To be honest, everything I start starts with Emacs. When it gets larger, I hate dealing with anything but the code. :) )

I've dealt some with Eclipse + C / C++ plugin. Not too happy with it. It seems to have a bit of a learning curve for me.

I might try Code::Blocks, though. Thanks. :)

-M.

---

### Post by daou on 2007-12-07
> **mannequin said:**
> I like any IDE that works well with my tastes. Emacs, then OpenLDev did that for me.
...
I've dealt some with Eclipse + C / C++ plugin. Not too happy with it. It seems to have a bit of a learning curve for me.


Someone who enjoys Emacs and finds a learning curve in Eclipse ;) ? Ok, considering that all keyboard shortcuts are different than in most popular GUI's today, I suppose it might be difficult to transition.

Jokes aside, I was going to recommend Emacs as well as another option. But seeing that the first post mentioned Anjuta, I assumed that the poster was looking for something that seemed more familiar from the Windows world.

---

### Post by Natr0n on 2007-12-07
> Is there a howto on how to use glade3 developed gui's with anjuta etc ?There sure is (uses glade2 though): [Tutorial: Simple Gnome Application Using libglade and C/GTK+]("http://www.micahcarrick.com/03-02-2006/gnome-programming-tutorial.html")

---

