---
title: "[Java][Applet] Making a largeish game, in a group...advice?"
date: 2009-10-31
forum: Programming Talk
---

### Post by fiddler616 on 2009-10-31
Hello,

At school this year, I started a programming team. We've struggled to find competitions like there used to be, where they'd give you about six very thinking-oriented problems, and you had an hour or two to solve them in a group of two or three, clustered around a "workstation" with "standard UNIX tools."

But we have found a contest sponsored by Gannon, which gives us until March to write a (relatively) large, full documented, downright impressive application. I would be absolutely charmed to do it in Python, but everyone else knows Java, so that's what it's going to be in. For the actual application, we put forth a few ideas, and decided that a *simple* RPG would be good. I know it's going to have a huge linecount, but I feel like at a conceptual level it's less challenging than, say, a better-than-Notepad text editor. And we do have about ten people and five months.

Organizationally, I'm trying to bust out a blueprint and a main method (actually the paint(), update() and MouseEvent() methods since it's an applet, but whatever), and then delegate different classes to one or more people. I'm trying to get them to use Subversion, which I'm not a fan of, but it's less evil than either using FTP or emailing stuff back and forth.

However, I have yet to actually write a program that defined more than one meaningful class, and I think my largest line count is about 400 or so. So do you guys have any protips? I just have this feeling that I'm going to run into big problems...

Thanks in advance.


*Disclaimer: The [contest rules]("http://www.gannon.edu/departmental/ecs/cis/contest_rules.asp") say nothing about outside help, but I feel like what I've asked for (very general) should be OK.*

---

### Post by NovaAesa on 2009-10-31
If you have only ever used one class before, I'm going to assume that you know little to none Object Oriented Programming. If you are going to use more than one class in your RPG (and also the fact you are using Java - a language that basically forces OOP), I'm going to assume you are going to be using Object Oriented Programming.

Tip = learn OOP if not already done so.

---

### Post by fiddler616 on 2009-10-31
> **NovaAesa said:**
> If you have only ever used one class before, I'm going to assume that you know little to none Object Oriented Programming. If you are going to use more than one class in your RPG (and also the fact you are using Java - a language that basically forces OOP), I'm going to assume you are going to be using Object Oriented Programming.

Tip = learn OOP if not already done so.
Yes, I'm very familiar with the theory behind OOP, and I've written classes before, just not in a big project.

---

### Post by kavon89 on 2009-10-31
Use [Google Project Hosting]("http://code.google.com/projecthosting/") to organize everything. Don't jump right into the code, first design the game and designate some people to handle things like graphics/sound. Then use inheritance, interfaces, information hiding, and [javadoc comments]("http://java.sun.com/j2se/javadoc/writingdoccomments/#format") (which show up very nicely in NetBeans' code completion dialog) liberally so it becomes easier to handle, for example:

```
Item
    Weapon
        Melee
            Sword
                BlackSwordOfDoom
            Club
        Ranged
            Bow
            Crossbow            
        Magic
    Food
    Equipment
    Ammo
```

---

### Post by fiddler616 on 2009-10-31
> **kavon89 said:**
> Use [Google Project Hosting]("http://code.google.com/projecthosting/") to organize everything.

I thought about this (and also Launchpad, which I personally like better) and I do plan to release under the GPL or similar, but I didn't know if it was a good idea or even legal to have the code open to the public before I submitted it to the competition. Thoughts?
>  Don't jump right into the code, first design the game and designate some people to handle things like graphics/sound. Then use inheritance, interfaces, information hiding, and [javadoc comments]("http://java.sun.com/j2se/javadoc/writingdoccomments/#format") (which show up very nicely in NetBeans' code completion dialog) liberally so it becomes easier to handle,
Yes. I've been working on creating a sort of skeleton of classes, like so:
```
}
public class Player extends Creature
{
    public Player(String name, int hp, Item[] inventory, Position pos)
    {
        super(name, hp, inventory, pos);
    }
    public fight(Creature c)
    {
    }

    ...
}
```
Is this a good use of time, or too verbose?

---

### Post by kavon89 on 2009-10-31
> **fiddler616 said:**
> I've been working on creating a sort of skeleton of classes, like so:
```
}
public class Player extends Creature
{
    public Player(String name, int hp, Item[] inventory, Position pos)
    {
        super(name, hp, inventory, pos);
    }
    public fight(Creature c)
    {
    }

    ...
}
```
Is this a good use of time, or too verbose?

It's a good use of time if you've already planned how the game will work, otherwise you may be writing something that will be completely rewritten later.

Also, it's relatively cheap to my knowledge to get pay-for private project hosting.

---

### Post by fiddler616 on 2009-10-31
Everything's pretty well planned out (in my head, at least, I'm still typing it up), except the mechanics of stuff offscreen. Because I feel like it's an immense waste of resources do draw things as if the applet was HUGE, and we were just looking at a little portion of it, and my brain isn't coming up something more elegant than just having an ArrayList of stuff that shouldn't be forgotten, and drawing the pieces of it that correspond to the section of the map the player's in.

---

### Post by kavon89 on 2009-10-31
> **fiddler616 said:**
> an ArrayList of stuff that shouldn't be forgotten

Just an ArrayList sounds like a bad idea and doesn't employ OO.

I'd have a World which keeps track of everything that can move/change, and a Map which tells it the large area it wants to be updated on based on where the user is. A thread in World should then always tell Map about anything which moves into the area Map cares about. This way, you have the onscreen and some of the offscreen ready to go and you could easily implement zooming in and out of the area.

EDIT: Also, I guess World would be a server-side thing if you're going for multi-player.

---

