---
title: "New to Anjuta, which  Automake version ?"
date: 2005-11-20
forum: Programming Talk
---

### Post by Biased turkey on 2005-11-20
I'm a turncoat, just swithed from Kdevelop to Anjuta.
I have nothing againdt Kdevelop, but installing KDE ( bloated imho ) just for using Kdevelop is not worth it.
5 minutes ago, I just created my 1st Anjuta C++ project but it failed bacause Anjuta complains about a missing automake.
So I fired Synaptic to install automake, the problem is that I have the choice to install 5 different versions ( 1.4 1.6 1.7 1.8 1.9 )
Question: what automake version should I install ( I would guess the latest: 1.9 ) ?
Why so many versions of automake ?
tia for any advise

---

### Post by kperkins on 2005-11-20
Actually anjuta suggests automake1.4. (If you rightclick on things in synaptic, it shows recomended, and suggested programs.)  Reading the description of 1.9 it says that it doesn't work in some of the situations of previous versions.

---

### Post by Biased turkey on 2005-11-20
[QUOTE=kperkins]Actually anjuta suggests automake1.4. (If you rightclick on things in synaptic, it shows recomended, and suggested programs.)  Reading the description of 1.9 it says that it doesn't work in some of the situations of previous versions.[/QUOTE]

Thanks for your promt reply kperkins.
I installed 1.9, but according to your suggestion, I uninstalled it and went for 1.4 instead.
It looks like anjut = dependency hell.
First, before installing Anjuta I went to the Ubuntu wiki and as suggested I installed build-essential, then Anjuta.
I created a simple C++ project but got the missing automake message.
So  I installed automake, created a new project and the got the missing glib error.
So back to synaptic again I installed libglib2.0-dev.
I created a new project then got the missing libtool error message.
So, back to Synaptic again and installed libtool.
What kind of dependency problem shall I expect next ?
Is there any link that tells me what packages I need to install in order to compile a louzy " Hello world " program with Anjuta ?
I'm already starting to miss Kdevelop lol.

---

### Post by kperkins on 2005-11-20
Actually 1.9 doesn't have to be removed to install 1.4--I have both on my system.
As for dependencies, those libs, etc aren't needed to run anjuta (obviously) but are needed to actually do certain things.  What I'd do is open up Syaptic search for anjuta, select it, right click on it and mark everything in the mark recommended/suggested for installation, and you should be all set.

---

### Post by Biased turkey on 2005-11-20
[QUOTE=kperkins]Actually 1.9 doesn't have to be removed to install 1.4--I have both on my system.
As for dependencies, those libs, etc aren't needed to run anjuta (obviously) but are needed to actually do certain things.  What I'd do is open up Syaptic search for anjuta, select it, right click on it and mark everything in the mark recommended/suggested for installation, and you should be all set.[/QUOTE]

Right after installing libtool I didn't have any dependency problems.
But I learned a lot from your latest post, I didn't even know one could right-click on a package in Synaptic to get the suggested / recommended packages.
As they say: R.T.F.M.
Thanks a lot Kperkins , and "hello world"
Now, I'm ready for SDL ( I already found a post on this forum about how to configure Anjuta for including the SDL libs ).

---

### Post by Biased turkey on 2005-11-22
Just compiled my 1st SDL program, went smoothly.
Now I can really remove Kdevelop and KDE.
I really appreciate the simplicity of Gnome ( some would say the minimalisticity )

---

