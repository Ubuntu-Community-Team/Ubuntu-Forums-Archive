---
title: "Lost Unity option on Log in"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by makitso on 2011-09-09
I have both Unity and G3 installed in Virtualbox.  Today's update was a partial.  Went into synaptic and selected all for update.  Now, there is no Unity option on the login and when login to G3 get fallback mode.

---

### Post by go7Ul1ai on 2011-09-09
Well that's what you get for doing a partial upgrade?

---

### Post by coffeecat on 2011-09-09
> **makitso said:**
>   Today's update was a partial.

That could be the problem. You have read the sticky about not doing partial upgrades? 

It could be that the partial upgrade removed Unity. Have a look in Synaptic and re-install unity and unity-2d if they've been removed.

Recognise the voice of bitter experience in this? :wink:

---

### Post by sgage on 2011-09-09
> **makitso said:**
> I have both Unity and G3 installed in Virtualbox.  Today's update was a partial.  Went into synaptic and selected all for update.  Now, there is no Unity option on the login and when login to G3 get fallback mode.

The first thing Synaptic does after you mark all for upgrade is tell you exactly what it is going to do. With this morning's upgrades, a long "to be removed" list came up, including Unity, Unity 2D, etc. You really have to pay attention!

If you wait for a few hours for things to resolve, you can probably just do an apt-get install unity and get it back.

[Edit: Here it is 10 minutes later, and the dependencies are already resolved - nothing to be removed ]
[Edit 2: Now there's another large batch of upgrades, resulting in many removals. Busy day! ]

---

### Post by ventrical on 2011-09-09
> **sgage said:**
> The first thing Synaptic does after you mark all for upgrade is tell you exactly what it is going to do. With this morning's upgrades, a long "to be removed" list came up, including Unity, Unity 2D, etc. You really have to pay attention!

If you wait for a few hours for things to resolve, you can probably just do an apt-get install unity and get it back.

[Edit: Here it is 10 minutes later, and the dependencies are already resolved - nothing to be removed ]
[Edit 2: Now there's another large batch of upgrades, resulting in many removals. Busy day! ]


 Yep .. OK .. thanks sgage.Thats what happened to me.

---

