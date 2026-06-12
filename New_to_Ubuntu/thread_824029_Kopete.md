---
title: "Kopete"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-09
Hi all.I have a problem with kopete.If someone sends me a link and I click it I get the message "KDEInit could not launch 'kfmclient'
Could not find 'kfmclient' executable".
I use Gnome desktop and for a while I tried KDE.I decided I didn't like it so I removed it, and now Kopete causes me problems.How can I fix this?

---

### Post by Xiong Chiamiov on 2008-06-10
AFAIK, kfmclient is used for launching things with Konqueror, so if you have that uninstalled, you'll get problems.  Theoretically, you should be able to change the default browser used by Kopete, by I don't see anything in the preferences; it seems that it's too tied into Konqueror.

---

### Post by lostlinuxkiwi on 2008-06-10
Kopete is really made for KDE. Try using pidgin or something eles made for gnome.

---

### Post by hyper_ch on 2008-06-10
> **lostlinuxkiwi said:**
> Kopete is really made for KDE. Try using pidgin or something eles made for gnome.

Why?

You could satisfy all the dependencies and then chanke in kcontrol default browser to somethign else.

---

### Post by lostlinuxkiwi on 2008-06-10
> **hyper_ch said:**
> Why?

You could satisfy all the dependencies and then chanke in kcontrol default browser to somethign else.

You would have to re install kcontrol.

---

### Post by Troll_the_Great on 2008-06-10
I re installed kcontrol.Now what?

---

### Post by hyper_ch on 2008-06-10
run it ;)
```

gksudo kcontrol

```

---

### Post by Troll_the_Great on 2008-06-10
I'm still lost :(:(:(

---

### Post by hyper_ch on 2008-06-10
run that command in a terminal

---

### Post by Troll_the_Great on 2008-06-10
No, I mean I'm lost because I don't know where to look for the option I need.I know I must run it in a terminal or with ALT F2.

---

### Post by hyper_ch on 2008-06-10
I'm not on a linux box right now so I can't really help...

---

### Post by Troll_the_Great on 2008-06-10
:( Thx anyway.

---

### Post by hyper_ch on 2008-06-10
have you're look around, it must be somewhere...

---

### Post by Troll_the_Great on 2008-06-10
I can't find anything about kopete there, and the only browser is Mozila, so it must be the default...If I install again conqueror do you think it will work?

---

### Post by hyper_ch on 2008-06-10
if you install konqueror (which is my preferred file manager anyway) it will then open the link in konqueror

---

### Post by lostlinuxkiwi on 2008-06-10
go kcontrol>KDE components>File Association>text>HTML 
then put firefox at the top of the list in the preference order.

I think that will work.

---

### Post by Troll_the_Great on 2008-06-10
Nope, I get the same result.:(

---

### Post by lostlinuxkiwi on 2008-06-10
how about KDE Components>default applications and switch the web browser option to firefox.

---

### Post by lostlinuxkiwi on 2008-06-10
Im using kubuntu at the moment and it worked for me.

---

### Post by Troll_the_Great on 2008-06-10
Under KDE components I don't have a "default applications" tab.Only "File Associations" "File Manager" "KDE Performance" "KDE Resources" "Service Manager" "Session Manager" and "Spell Checker"

---

### Post by lostlinuxkiwi on 2008-06-10
damn, it should have been above file associations. I duno then. Install Konqueror? is there something you particularly like about kopete? pidgins good.

---

### Post by Troll_the_Great on 2008-06-10
I like Kopete because it has a nicer interface then Pidgin and because I can use my built in webcam (I have a laptop).I will install konqueror and that's it.Thx to all for the replies.

---

### Post by philinux on 2008-06-10
Just use synaptic and mark Kopete for reinstall. I like Kopete the best and I only use the gnome desktop.

I have K3b as the only other KDE app on my system and both work fine.

---

### Post by lostlinuxkiwi on 2008-06-10
He's got kopete. he wants hyperlinks to open in firefox rather than trying to open in Konqueror, which he doesn't have.

---

### Post by philinux on 2008-06-10
> **lostlinuxkiwi said:**
> He's got kopete. he wants hyperlinks to open in firefox rather than trying to open in Konqueror, which he doesn't have.

I could never crack this it always opened epiphany.

---

