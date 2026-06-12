---
title: "Gnome-shell vs Unity (under the hood)"
date: 2011-10-19
forum: Recurring Discussions
---

### Post by screaminj3sus on 2011-10-19
Most of the gnome-shell vs unity discussions seem to focus on superficial aspects of the two shells.

What I've noticed is the underlying technologies play a big part as well.

IMO gnome-shell seems like it was really thought out and executed much better than unity from the ground up. Gnome-shell is far more customizable than unity being built with javascript and css. It has strong themeing and customization capabilities (extensions) compared to unity.

I like unity, but to me the way its built as a glorified compiz plugin seems more hacky, and it seems like they weren't thinking about the future when architecting it. I think gnome-shell has better long term prospects the way it was built.

---

### Post by sffvba[e0rt on 2011-10-19
*Thread moved to **Recurring Discussions**.*


404

---

### Post by mips on 2011-10-19
I don't like either but if you forced me to choose between the two I would pick Gnome.

---

### Post by irv on 2011-10-19
> **screaminj3sus said:**
> 

I like unity, but to me the way its built as a glorified compiz plugin seems more hacky, and it seems like they weren't thinking about the future when architecting it. I think gnome-shell has better long term prospects the way it was built.
You like unity, I don't, but we agree on the last part of your post. After trying the new release of Ubuntu 11.10, I keep breaking it. Re-installed it 5 times. Finely install Kubuntu 11.10 with KDE and then installed Unity Desktop from within KDE. This way I can switch between them. I still keep breaking it when I make any changes to Compiz. I like the special effects in Compiz, but Metafile Desktop was much more stable. 

I am going to stay with KDE until the release of 12.04 and see where Unity goes in this release. As of yet, I don't see myself using Unity until many of the bugs are fixed.

---

### Post by Copper Bezel on 2011-10-19
Now, to be fair, Gnome is a much larger developer base than Ubuntu has, isn't it?

Unity does seem to break easily as a result of Compiz configuration problems. I don't know that that's really a result of its being a plugin, though - more a result of a lot of old settings and old code lying around in the first place. In Shell's case, the compositor was extremely limited at the beginning and was written around the shell. In Unity's case, the shell was written to match the compositor. I think the latter leaves a lot more room for versatility.

I know that the first version of Unity that shipped with 10.10 used Clutter compositing (and I think 2D when it's running without Compiz does this as well) so it's not completely out of the question that another shell could be written against Clutter. I know, too, that lot of the other Compiz plugins are broken or irrelevant under Unity. Those are arguments for both the versatility that Clutter does have and its tight connection with the Shell interface as it's shipped. Extensions also seem a good bit simpler to write against it than whole new plugins for Compiz would be.

I don't like this dconf thing, but that's so tightly woven into Gnome 3 that Ubuntu's distribution of Gnome has the problem every bit as much as upstream Gnome does.

If we're looking at it in the light of, as you say, planning for the future, I think you're right. Shell will turn out to be the better base in the long run. For now, I think Ubuntu made the right choice in sticking with Compiz. But Ubuntu benefits either way. They'll wait it out with Compiz until Clutter gets broader video card support and more elaborate extensions are written against it, then rewrite Unity again as a Shell extension when it catches up.

Or, I guess, end up porting Compiz into Wayland by themselves. = /

---

