---
title: "Drop menu flicker error @ 768px - clears @ lower res. (bootstrap)"
date: 2015-10-30
forum: Programming Talk
---

### Post by Ace..... on 2015-10-30
[B].
The drop-menu error [[COLOR=#0000cd]can be seen here[/COLOR]]("https://w3layouts.com/preview/?l=/learn-a-educational-guidance-flat-bootstrap-responsive-web-template/").[/B]

Grab the right browser border, and drag it slowly to the left.
The menu remains a normal menu, until the browser window dimensions hit 768px, when the menu changes to an 'icon activated' drop menu.

It works, but with a major 'flicker' problem, as the mouse cursor passes over the menu, causing the sub-menus to drop.

The problem apparently (?) arises from the menu being @ hard right.

As the browser window is dragged further to the left, @ about 740px...... the menu moves central...... and then functions without a glitch.
(when [[COLOR=#0000cd]downloaded[/COLOR]]("https://w3layouts.com/learn-a-educational-guidance-flat-bootstrap-responsive-web-template/") the same behaviour exists).

With the code in my own website, this problem occurs until 640px is met.

**Note:**
I did notice that 'body display changes' seemed to be occurring outside of my style.css.
I dealt with this, using @media(max-width:XXXpx), countering whatever I presumed to be hardcoded into bootstrap.css.

I figured that, logically, my nav-bar code (below 640px) needed moving from 640 to 768px.

However, when this was done........ the drop menu remained at the right (glitching) at all resolutions, so I returned the code back to @media(max-width:640px).

**Template**
Clearly the template itself has faults....... fine...... it causes one to learn.
However, I am simply failing to get a handle on the fundamentals.

All the general body blocks, I was able to re-configure.
But so far, not the nav bar.

I checked out bootstrap, but there are just too many instances to grasp.

I really could do with some help.
I need to get the 'mobile menu' to activate correctly (centrally) @ 640px (without prior change).
OR
.... for it to activate correctly at 768px.

I'm stumped.
I'm sure that it's just lack of knowledge.
Hopefully a fellow forum member can bring me up to speed in this area
(it's my first attempt at responsive coding).

:)

---

### Post by Ace..... on 2015-10-31
Problem apparently solved!

This may not be ideal, or it may be ideal.
I simply modified the css code grouping [COLOR=#000000]@media(max-width:640px)
to [/COLOR][COLOR=#000000]@media(max-width:768px)

So it created two groups of [/COLOR][COLOR=#000000]@media(max-width:768px).

I still haven't gained a full grasp of these elements, but....... the drop menu now displays correctly.

:)[/COLOR]

---

