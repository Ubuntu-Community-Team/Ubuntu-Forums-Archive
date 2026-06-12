---
title: "LightDM and those white dots"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dmoconnell on 2011-10-08
Just upgraded to Oneiric Ocelot, And the first thing I noticed is that LightDM has those white dots. I thought that if I changed the picture it would remove the dots. Changed picture and it still shows those [censored] white dots. Does anyone know how I can remove the white dots from my Login
Don't know if this helps but I am using the unity-greeter session (I do know there is other greeter sessions just don't know how to get/use them)

Thanks 
Dm

---

### Post by hansdown on 2011-10-08
Hi dmoconnell.

Sorry if I'm misunderstanding.

Do you mean the four blinking dots, that show , that the system is loading?

---

### Post by fillmont on 2011-10-08
> **hansdown said:**
> Hi dmoconnell.

Sorry if I'm misunderstanding.

Do you mean the four blinking dots, that show , that the system is loading?

I think he means the white dot grid on the actual lightdm log in screen.

---

### Post by Spr0k3t on 2011-10-08
I'm with dmoconnell on this one... I wish there was a simple way to get rid of those [explicative goes here] dots.

---

### Post by hansdown on 2011-10-08
> **fillmont said:**
> I think he means the white dot grid on the actual lightdm log in screen. 

<snip huge image>

Wow... That is interesting.

Sadly, I haven't kept up to date.

Thanks, fillmont.

---

### Post by tista on 2011-10-08
> **dmoconnell said:**
> Just upgraded to Oneiric Ocelot, And the first thing I noticed is that LightDM has those white dots. I thought that if I changed the picture it would remove the dots. Changed picture and it still shows those [censored] white dots. Does anyone know how I can remove the white dots from my Login
Don't know if this helps but I am using the unity-greeter session (I do know there is other greeter sessions just don't know how to get/use them)

Thanks 
Dm

Hi dmoconnell,

Yeah that dots grid had been embedded into the codes especially user-list.vala.
so if you knew the vala codes, you could remove such grid. ;)
Getting the source codes, modify the codes, and rebuild package, that's all.
For example, my unity-greeter 0.1.0 featuring elementary, I did.

And today, that grid sometimes might have been keeping to desktop in case you guys run oneiric on virtualbox. :S

cheers.

---

### Post by Quackers on 2011-10-09
I like them :-)
I think it makes a nice change from that plain default Ubuntu background.
Mine are staying for sure ;)

---

### Post by dmoconnell on 2011-10-09
> **fillmont said:**
> I think he means the white dot grid on the actual lightdm log in screen.
[COLOR=Blue]Yes thats exactly what I mean [/COLOR]

> **Spr0k3t said:**
> I'm with dmoconnell on this one... I wish there was a simple way to get rid of those [explicative goes here] dots.
[COLOR=Blue]I'll choose my grandma's choice explicative "Oh banana's"[/COLOR]

> **tista said:**
> Hi dmoconnell,

Yeah that dots grid had been embedded into the codes especially user-list.vala.
so if you knew the vala codes, you could remove such grid. ;)
Getting the source codes, modify the codes, and rebuild package, that's all.
For example, my unity-greeter 0.1.0 featuring elementary, I did.

And today, that grid sometimes might have been keeping to desktop in case you guys run oneiric on virtualbox. :S

cheers.
[COLOR=Blue]So no easy way to do it.  It sounds like you do know how to do it. Think you could post a tutorial on how to edit the vala codes (I know nothing of vala)

[COLOR=Black]Thanks 
Dm
[/COLOR][/COLOR]

---

### Post by flipper T on 2011-10-09
> **Quackers said:**
> I like them :-)
I think it makes a nice change from that plain default Ubuntu background.
Mine are staying for sure ;)

if i want white dots sprawled across my desktop, i would put them there.

ugly / ridiculous / pointless. the dots, not you quackers :)

---

### Post by Quackers on 2011-10-09
:-) no offence taken :-)
It's not your desktop is it? Your login screen, maybe?
And I still like them! But I'm a duck and they look like breadcrumbs :-)

---

### Post by BigCityCat on 2011-10-09
> **Quackers said:**
> I like them :-)
I think it makes a nice change from that plain default Ubuntu background.
Mine are staying for sure ;)

Yup me too. Really like them a lot.

---

### Post by keithy on 2011-10-09
FWIW,

I like them too!

---

### Post by sammiev on 2011-10-09
WoWser and all over a few white dots. :(

---

### Post by sgage on 2011-10-09
> **BigCityCat said:**
> Yup me too. Really like them a lot.

You know, the white dots don't particularly bother me, and I hardly ever see the login screen anyway, but I really can't understand why anyone would "really like them a lot".  :???:

---

### Post by BigCityCat on 2011-10-09
> **sgage said:**
> You know, the white dots don't particularly bother me, and I hardly ever see the login screen anyway, but I really can't understand why anyone would "really like them a lot".  :???:

It was hard not to go with sexy. lol

---

### Post by sgage on 2011-10-09
> **BigCityCat said:**
> It was hard not to go with sexy. lol

Guess I just don't swing that way... :lolflag:

---

### Post by tista on 2011-10-09
Guys,

IMHO, White dots didn't really matter whether it showed or not... I suppose the lightdm problem for theming is that it was constructed by GtkMenubar routines...

Yeah it means the appearance of top panel on lightdm had to depend on gtk3's menubar color scheme... That's horrible!! :/

Because Ambiance has:
* Dark menubar background
* Light menubar foreground

But, other types of theme has:
* Light menubar background
* Dark menubar foreground

So we couldn't read the dark chars on black top panel... speechless... Devs seems to concern only Ambiance? Or they should fix this "issue" by override foreground color with #FFF or somehing like that, I hope. This is why I don't like lightdm.

Every time devs're only concerning Ambiane, Unity, and "their resources" by ignoring any ohters... :sad:

Regards.

---

### Post by PhantmKllr on 2011-10-10
> **sgage said:**
> You know, the white dots don't particularly bother me, and I hardly ever see the login screen anyway, but I really can't understand why anyone would "really like them a lot".  :???:

I suppose you could say that I (maybe, sort of) like the dots. They're aesthetically pleasing, and I don't see anything wrong with them. They stay for me.

> **tista said:**
> Guys,

IMHO, White dots didn't really matter whether it showed or not... I suppose the lightdm problem for theming is that it was constructed by GtkMenubar routines...

Yeah it means the appearance of top panel on lightdm had to depend on gtk3's menubar color scheme... That's horrible!! :/

Because Ambiance has:
* Dark menubar background
* Light menubar foreground

But, other types of theme has:
* Light menubar background
* Dark menubar foreground

So we couldn't read the dark chars on black top panel... speechless... Devs seems to concern only Ambiance? Or they should fix this "issue" by override foreground color with #FFF or somehing like that, I hope. This is why I don't like lightdm.

Every time devs're only concerning Ambiane, Unity, and "their resources" by ignoring any ohters... :sad:

Regards.

You see, this is a good example of the unfortunate side effect of rapid progress. The Devs are focusing on implementing new features, instead of working on/fixing what we have now.

I truly hope that they'll spend the next cycle improving Ubuntu, so that it can be the best it can be, and hopefully, the best operating system in existence. (And let us hope that they do it soon, instead of waiting until 12.04. :popcorn: )

---

### Post by Rasa1111 on 2011-10-10
> **Quackers said:**
> I like them :-)
I think it makes a nice change from that plain default Ubuntu background.
Mine are staying for sure ;)

I like them to!
I love the entire new login screen, really! :KS

> but I really can't understand why anyone would "really like them a lot".  :???:
I 'really' like them a lot, myself, actually. 
what is there to "not understand"? 
:D

---

### Post by jbicha on 2011-10-10
The LightDM developer is hoping that designers make their own greeters, not necessarily try to theme the Unity greeter.

This is the first significant release of LightDM & the Unity greeter and I think it is quite comparable to current GDM. LightDM has much more potential for theming whereas GDM is mostly locked down.

---

### Post by tista on 2011-10-10
> **jbicha said:**
> The LightDM developer is hoping that designers make their own greeters, not necessarily try to theme the Unity greeter.

This is the first significant release of LightDM & the Unity greeter and I think it is quite comparable to current GDM. LightDM has much more potential for theming whereas GDM is mostly locked down.

@jbicha,

No.. no.. please..

All of theme creators could code the greeter for lightdm from scratch?!
I know lightdm/unity-greeter are amazing, but I couldn't say them "seamless appearance". Since today's unity-greeter seems quite difference from both unity "Dash" and Gtk "Ambiance"... I couldn't see the goal of unity-greeter at all...

Especially for "Seamless Appearance", even gdm 3.2 has good possibility with gnome-shell. Yep, theme designers could make own favorite theming for both gs and gdm in same time by writing css. and gdm-greeter runs on gs engine, so most of gdm-greeter's stuff could share the resources of gs theming. For example, top panel, main dialog, color scheme, fonts, and much more!! ;) I think that's the "seamless appearance".

Finally I don't think all of users needs eye-candy 3D-CG greeter.

Regards.

---

