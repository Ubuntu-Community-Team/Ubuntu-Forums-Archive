---
title: "(Mono/MonoDevelop) after upgrade to lucid: g* stack of assemblies not compatible with"
date: 2010-05-02
forum: Programming Talk
---

### Post by japsai on 2010-05-02
I use MonoDevelop, and after upgrading to Lucid (which is otherwise nice!) many (gnome related) references became invalid:

atk-sharp
gdk-sharp
glade-sharp
gtk-sharp
pango-sharp

With the error:

```
Assembly not available for Mono / .NET 2.0 (in Mono 2.4.4)
```

Anyone else have this problem? Is it a bug or something peculiar in my system?

---

### Post by CorporalMaxSterling on 2010-05-02
sorry for not being more help, but just wanted to add I'm having the exact same problem! :confused:

---

### Post by japsai on 2010-05-04
I would file a bug, but I have no clue to what package.

---

### Post by lexe-cc on 2010-05-04
I'm also experiencing this problem ..

---

### Post by japsai on 2010-05-05
[I filed a bug here.]("https://bugs.launchpad.net/ubuntu/+source/mono/+bug/575738")

Please go there and report that you "are also experiencing this bug.".

If possible one of you could even provide some extra information through the ubuntu-bug tool, I cannot get in my system right now due to another lucid-bug.

---

### Post by lexe-cc on 2010-05-05
I think I may have solved this:

just install gtk-sharp 

> sudo apt-get install gtk-sharp2

This solved my problem, so it wasn't a bug after all ..

Cheers

---

### Post by japsai on 2010-05-05
Yeah, this worked for me too. Still a bug though, if the new mono (2.4.4) is not compatible with gtk-sharp (old one) than some dependency or sth should be set accordingly.

---

### Post by gregarobinson on 2010-05-07
Not to steal your thread, but I am new to Linux and Ubuntu and need to know how to upgrade to the latest version of Mono on the Ubuntu box. Can anyone point me to a "how to" link or help me understand how to do this? 

Thanks

---

### Post by japsai on 2010-05-07
That depends, if you want the latest package for Ubuntu, you can do this through synaptic (application under system >administration) then search for mono, or through commandline:

```
sudo apt-get install mono
```

If you want the latest package by mono itself (this is even more cutting edge, but not supported by ubuntu) than you need to go through the mono website (probably have their own repository).

If you already have mono, use the update manager. You should upgrade to the latest Ubuntu version (Lucid Lynx, 10.04) first.

Let me know if you need more help.

---

### Post by gregarobinson on 2010-05-07
Thanks

The Ubuntu box already has Mono on it. It's missing 2 dlls that my ported app needs, and per the Mono site they are available now. I found one of them in the Synaptic Package manager this morning and "installed" it. But I still need the other one and it does not show up in the list. 

I thought about upgrading to the latest Ubuntu. I started to do this earlier today; I stopped when it said it could take many hours to complete the update.

---

### Post by japsai on 2010-05-07
What's the name of the DLL you're missing?

---

### Post by gregarobinson on 2010-05-07
System.ServiceModel

I started an Ubuntu upgrade hoping this would pull down the latest version of Mono...not a good idea.

All the files pulled down and the install started..I got a dialog box about overwriting a file but my mouse and keyboard were locked up. 

I tried everything possible to get my keyboard\mouse back with no luck so I powered the box down. I powered back up and I am unable to boot now.

---

### Post by japsai on 2010-05-10
How is it going now?

If you only installed Ubuntu recently I would suggest removing it and reinstalling the new version (10.04 Lucid Lynx).

If not, please give some more details, i.e. where does it stop to boot? Can you start in recovery modus? But the above option is easiest.

---

### Post by gregarobinson on 2010-05-10
We have been testing Ubuntu on an Artigo A1100 box with Version 9.01. I tried to do an upgrade and the box just died. I can get to BIOS. I tried to boot from disk, nothing, I tried to upgrade from disk, nothing. 

I got frustrated so I did a dula boot, installing 9.10. on a dev server. That went very well and I have our .NET 3.5 up and running partially on the dev server.

---

### Post by jqdennis on 2010-07-18
New MonoDevelop user:
References to gdk-sharp... in red, Assembly not available

reinstalled gtk-sharp2, but no change

---

### Post by Xavier962 on 2010-10-30
> **japsai said:**
> I use MonoDevelop, and after upgrading to Lucid (which is otherwise nice!) many (gnome related) references became invalid:

atk-sharp
gdk-sharp
glade-sharp
gtk-sharp
pango-sharp

With the error:

```
Assembly not available for Mono / .NET 2.0 (in Mono 2.4.4)
```Anyone else have this problem? Is it a bug or something peculiar in my system?

Hi,

I've got the exact same problem, that I could solve thanks to lexe-cc by running
```
sudo apt-get install gtk-sharp2 			 		
```.

However, there is still one reference that is said not to be available: notify-sharp.
It comes with package libnotify0.4-cil. I tried to reinstall it, but it does not fix the problem.

Does anyone have a clue?

Thanks,

Xavier

---

### Post by directhex on 2010-10-30
If you get a "not compatible" message, generally, it means you're missing the -dev package.

e.g. libnotify-cil-dev or libgtk2.0-cil-dev

---

### Post by Xavier962 on 2010-11-03
Yup, that did the trick, thanks!
I'm a bit startled though, since I didn't install that package in 9.10 when I developped my app...

Well, all solved, that's what is important.

Thanks again :)

---

### Post by directhex on 2010-11-03
> **Xavier962 said:**
> Yup, that did the trick, thanks!
I'm a bit startled though, since I didn't install that package in 9.10 when I developped my app...

Well, all solved, that's what is important.

Thanks again :)

It's a change to packaging since Karmic. And in the upgrade scenario, you don't pick up on it - MonoDevelop's package Recommends: libgtk2.0-cil-dev now, but when you upgrade an existing package, new Recommends are not installed

---

### Post by pr0f on 2010-11-25
I have done all the thing you have told but my assembly error dose not solved :neutral:

---

### Post by directhex on 2010-11-25
> **pr0f said:**
> I have done all the thing you have told but my assembly error dose not solved :neutral:

Which assembly error?

---

### Post by pr0f on 2010-11-25
Assembly not available for Mono / .NET 2.0 (in Mono 2.4.4)

---

### Post by directhex on 2010-11-25
> **pr0f said:**
> Assembly not available for Mono / .NET 2.0 (in Mono 2.4.4)

... it might help if you said WHICH assembly.

---

### Post by pr0f on 2010-11-26
I have installed mono-gac-1.0 and mono-gac-2.0 but it didn't worked 
I had read some where else I should set the path by export command but it didn't worked too

---

### Post by directhex on 2010-11-26
> **pr0f said:**
> I have installed mono-gac-1.0 and mono-gac-2.0 but it didn't worked 
I had read some where else I should set the path by export command but it didn't worked too

1) that doesn't answer my question.

2) those packages don't exist.

It's exceedingly difficult to help you when you don't actually state clearly what the problem is. Every problem has a solution - but we have no idea what the problem is yet.

---

### Post by pr0f on 2010-11-27
do you mean something like "yasm" as assembly ?

---

### Post by directhex on 2010-11-27
> **pr0f said:**
> do you mean something like "yasm" as assembly ?

I think there's an impenetrable language barrier going on here.

"Assembly" is the name for a .NET library. "Assembly not available for Mono / .NET 2.0" means "I cannot find the library you're trying to use".

You STILL haven't said which library you're trying and failing to use, so you STILL have no answer on how to fix your problem.

---

### Post by pr0f on 2010-12-05
Dear Directhex now I found what you mean I so sorry my English language is too weak so now the library that error in my app is "system.Deployment"  and "Microsoft.ReportViewer.WinForms" 
I hope this time I got the right meaning of your answer 
thank you for your help  ;)

---

### Post by directhex on 2010-12-06
> **pr0f said:**
> Dear Directhex now I found what you mean I so sorry my English language is too weak so now the library that error in my app is "system.Deployment"  and "Microsoft.ReportViewer.WinForms" 
I hope this time I got the right meaning of your answer 
thank you for your help  ;)

Neither of those are available in Mono.

---

### Post by necrocapo on 2011-10-20
I have upgraded to 11.10 oneiric and have the same problem,
References are red in solution panel, and the error is :

"Assembly not available for Mono / .NET 2.0 (in Mono 2.10.5)"

for :

atk-sharp
gdk-sharp
glade-sharp
glib-sharp
pango-sharp

I already have gtk-sharp2 package :

sudo apt-get install gtk-sharp2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk-sharp2 is already the newest version.

---

### Post by japsai on 2011-10-20
Consider changing your project to .NET 3.5. This can be done in the solution/project settings.

---

### Post by directhex on 2011-10-20
> **japsai said:**
> Consider changing your project to .NET 3.5. This can be done in the solution/project settings.

He actually needs to set it to 4.0

Ubuntu no longer support 2.0-3.5 for apps using libraries provided with the OS (GTK# etc), and no longer supports 1.0 in any form

---

### Post by necrocapo on 2011-10-20
I can compile with runtime 4.0 , but my client computer has debian and does not have 4.0 packages like libmono-corlib4.0-cil :(

So that means, I never will able to compile using 2.0 on Ubuntu? Should I downgrade to 11.04 in order to achieve this ?

---

### Post by directhex on 2011-10-20
> **necrocapo said:**
> I can compile with runtime 4.0 , but my client computer has debian and does not have 4.0 packages like libmono-corlib4.0-cil :(

So that means, I never will able to compile using 2.0 on Ubuntu? Should I downgrade to 11.04 in order to achieve this ?

You could try installing GTK# from the addons menu in MonoDevelop - it can download an older GTK# release to compile against for compatibility

---

### Post by necrocapo on 2011-10-21
> **directhex said:**
> You could try installing GTK# from the addons menu in MonoDevelop - it can download an older GTK# release to compile against for compatibility

Thank you , I found this and those packages have fix my problem :
[https://launchpad.net/~keks9n/+archive/monodevelop-latest/+packages](https://launchpad.net/~keks9n/+archive/monodevelop-latest/+packages)

---

