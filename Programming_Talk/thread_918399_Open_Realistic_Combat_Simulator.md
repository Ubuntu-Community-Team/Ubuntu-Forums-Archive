---
title: "Open Realistic Combat Simulator"
date: 2008-09-12
forum: Programming Talk
---

### Post by linuxguymarshall on 2008-09-12
I am looking for people to help create an open-source combat simulator. Something that would have a huge battlefield such as that of the battlefield 1942 games.  I would like it to have a lot of physics involved and forces acting on EVERYTHING. I want it to be created with entirely open-source software and everything must be released under the MIT license.

If you have questions or are interested in helping just ask. Obviously this will require the help of tons of people and nothing playable for a year or so.

---

### Post by Phristen on 2008-09-12
And I wanna fly to the moon.... On an open source rocket.

---

### Post by linuxguymarshall on 2008-09-12
> **Phristen said:**
> And I wanna fly to the moon.... On an open source rocket.

I like that idea.....

---

### Post by CptPicard on 2008-09-13
-1, [delusions of grandeur]("http://ubuntuforums.org/member.php?u=356998")

---

### Post by nvteighen on 2008-09-13
> **linuxguymarshall said:**
> I am looking for people to help create an open-source combat simulator. Something that would have a huge battlefield such as that of the battlefield 1942 games.  I would like it to have a lot of physics involved and forces acting on EVERYTHING. I want it to be created with entirely open-source software and everything must be released under the MIT license.

If you have questions or are interested in helping just ask. Obviously this will require the help of tons of people and nothing playable for a year or so.

Err... are you sure you can do such a thing??? Have you ever done something in an open source project (not yours, someone else's)? Look for a project that you like and start helping there so you see how things are done...

I don't want you to leave this project, but I really would like to see you starting it with some chance to really finish it.

---

### Post by crazyfuturamanoob on 2008-09-13
Sounds very utopian idea...

---

### Post by linuxguymarshall on 2008-09-13
> **crazyfuturamanoob said:**
> Sounds very utopian idea...

That's what software engineering is all about. Pushing the limits, creating perfection

---

### Post by Tomosaur on 2008-09-13
> **linuxguymarshall said:**
> That's what software engineering is all about. Pushing the limits, creating perfection

Such a project is a huge, huge task. Even the BF games struggle to achieve what you want to achieve (physics on **everything** would be very resource intensive).

You should start small. It is always best to get some solid ideas down rather than just a vague description. If you get a working prototype together, maybe people would be more interested in helping - but for now this is way too ambitious.

---

### Post by nvteighen on 2008-09-13
> **linuxguymarshall said:**
> That's what software engineering is all about. Pushing the limits, creating perfection
If you have the experience and knowledge... to create something that **nears** perfection.

Man, if creating a card game engine is taking me a lot of work and thought, tests, bad code, rewrite, hey! it works, no, it doesn't... wait, let's try this and hurra! (ask CptPicard), I just can't imagine how long it would take to have a physics engine. Unless you use an existing one, but I guarrantee all will have some kind of non-perfection that makes things unrealistic.

Tell us, what programming languages do you know? Can you show us some code by you? Any experience in any open source project? Any implementation design ideas for your game? Do you know if someone else has already started something like this? As 1942 is such a popular game, I'm sure you'll find someone... I really recommend you to join that project.

If you just want some piece of work (which is always a good thing), some members of these forums (including myself) are working on [https://launchpad.net/sysres](https://launchpad.net/sysres). I can give you a little, concrete and well-defined task that could help to speed things up, but you are required to have some well-established Python knowledge and patience.

---

### Post by hod139 on 2008-09-13
> **linuxguymarshall said:**
> I am looking for people to help create an open-source combat simulator.
If you are really interested you should perhaps consider building your game off of an existing open source engine.  For example,  [ODE]("http://www.ode.org/"), [bullet]("http://www.bulletphysics.com/Bullet/wordpress/"), and [OGRE]("http://www.ogre3d.org/") are popular solutions.  Starting one from scratch is a huge task that will take years.

As an aside, all these engines are designed with games in mind, and therefore sacrifice accuracy in the physics for speed.  Their goal is physical "believability", not accuracy.  So using these engines for a combat simulator is not something that say the DoD will use, but only gamers.

---

