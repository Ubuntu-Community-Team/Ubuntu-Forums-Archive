---
title: "Request for config help -- super-simple interface for limited user"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by spudchick on 2011-11-10
Please be patient with this long post--but I hope something useful for others may come of it. 

I've been trying to set up a very simple user interface on a touchscreen all-in-one for my elderly and technophobic mother-in-law. I tried putting Eldy on both natty and oneiric without success.  Both natty and oneiric installed beautifully after a bios update, so the OS is not the problem.  There were two issues:

1. Eldy is java based and required installing and forcing Sun Java, and doing so screwed up the Ubuntu installs as well as never actually getting Eldy to fully work.  

2. Eldy is buggy and not well-specified yet for US users, and I found that even after installing Eldy on Win7 (which it's  better supported for than Linux), not everything worked--although mail and web did. 

The point of Eldy is that it creates a _very_ simple user interface with just a few large buttons for email, web, and Skype (though this last plugin never worked on any install). Besides making it easy for a person terrified of computers to work with it, the large controls make it highly suitable for touchscreen use without a stylus--excellent for someone with diminished vision and motor control and with arthritic hands who would find learning and using a mouse very difficult.

So my request here is for step-by-step guidance to configuring Ubuntu (recent versions) for the following:

*  icons and text are large and easy to read

*  controls in all programs are large enough to use on a touchscreen WITH FINGERS

*  large, clearly labeled shortcuts on the desktop 

*  remove login prompts wherever possible

*  easy way to invite another user for remote assistance 

*  if Canonical programs exist to make mail and web even simpler, let me know 

I don't want to have to wrangle a lot of third-party stuff onto  it to get it to work, the hope is that this can be done within the parameters of the native Ubuntu installation and any programs known to work specifically with Ubuntu. 

I'd especially like to hear from those of you who have set Ubuntu up for a new elderly user with limited physical ability and a fundamental incompatibility with electronics devices. 

Yes yes yes, I've heard the stories of older users who thought they couldn't use a computer and took to Ubuntu without any modifications like ducks to water, and I'm quite sure there are plenty as I see elderly users texting away on smartphones all the time.  But I am telling you now that my mother in law is Not That Person.  The two things she does have going for her with the prospect of learning to use a computer is that she is reasonably intelligent and realizes that she must encounter this terrifying thing if she wants to be able to stay in touch with a family and a world that are moving into realms she currently has no access to.  

I'd buy her one of the pre-configured touchscreens (most of which are linux based) but so far they are either terribly overpriced, or (in the case of Telikin, which looks like a decent and fairly priced touchscreen product) are still quite buggy yet.  I'm hoping that an Ubuntu group will work on a flavor for users in this category, but until then, I'd really appreciate hearing from you experienced Ubuntu configurers/configurators/configuratrixes.

Thanks in advance,

spud

---

### Post by grahammechanical on 2011-11-10
Ok, here goes. Regarding Oneric.

1) icons and text are large and easy to read.

A lot of people complain that the icons in the Launcher are too large and want them reduced in size, which can be done.

2) blank

3) large, clearly labeled shortcuts on the desktop.

Right Click any Desktop icon and select Resize Icon. Then you can use the grab handles to increase the size of the icon.

4) remove login prompts wherever possible.

Go to System Settings>User Accounts and unlock the utility and if your mother-in-law is set up as a standard user and not administrator you can set her account to not require a password. Then at the login/Greeter screen she clicks on her user name and presses enter and the desktop loads. You can also use the same utility to set Automatic login.

5) blank.

Have you examined the Universal Access options in Ubuntu in System Settings?

It is a start. Regards.

---

### Post by spudchick on 2011-11-10
Thanks, Graham.  It is indeed a start.

---

### Post by Mark Phelps on 2011-11-10
Good luck with #2.  

While I'm generally the first in line (or nearly that) to bash designers for forcing "smart phone interfaces" onto desktops, in situations like these, I can see the value of just such an interface.

Even Windows 8, whose interface was (supposedly) DESIGNED with touch screens in mind, has received a LOT of bad press for the few provided applications NOT being designed for touch-screen use.

After all, what good is a touch screen that then launches an app, that then uses tiny menus and requires fine-grained mouse clicks, in order to function?

As to #5 -- remote access -- the only value I see to this is allowing a support person (you?) to grab control of their machine in order to diagnose and repair a problem.  If that's why you included this, I sympathize -- as I am stuck in a similar situation and often end up driving across town to fix a minor problem with a relative's PC.  But, I believe there are solutions available for this, although I personally don't know any (in the Linux world).

---

### Post by spudchick on 2011-11-11
Thanks, Mark.  I'd heard something about Win8 having more options for touchscreen but not surprised to hear it's not quite meeting the mark. I'm going to take her the Win7 with Eldy and at least see how she does with email and web.  Will look into customizing Ubuntu for her separately  on another computer and maybe "graduate" her to that later.

---

