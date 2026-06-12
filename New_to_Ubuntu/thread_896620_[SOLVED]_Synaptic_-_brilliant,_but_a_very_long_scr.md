---
title: "[SOLVED] Synaptic - brilliant, but a very long scroll!"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-08-21
I am enormously impressed with Synaptic Package Manager.

But I find it is a long, delicate & frustrating business to try to scroll to a particular package I know the name of.

Not surprising as the list is 25,000 items long!
So even if I get close, the slightest twitch sends me off into outer space again.

I know there is a pane which would allow me to cut the list into categories, but often I don't know which is the appropriate category.

I know there is a search function, but it takes forever to work it's way through the 25000 items (reminds me of searching before Google or even now in XP...).

I know there is a terminal command I could use, if I wanted to & if I could remember it or write it down somewhere.

But it would be SO MUCH BETTER if the Synaptic GUI window had the sort of search which is now very common (see Picasa, for instance) :
As soon as I enter, say "s", it takes me to the top of the "s" items.
If I then enter "c" I get to the top of the "sc" items.
If I then enter "r" I get to the "scr" items.
etc.

Being totally incompetent myself, I imagine it would be a no-brainer for somebody competent to add!

Or does it already exist & I just missed it?

Anybody else want it?

Is there somewhere else I should suggest it?

Thanks!

---

### Post by Troll_the_Great on 2008-08-21
If you know the name of the package, open a terminal and type
```
sudo apt-get install name_of_package
```
That's it.
Cheers!

---

### Post by kdorf on 2008-08-21
The search button works about as fast as you can expect for a 25000 item database, and on my machine it's very snappy.

Try changing the option to package name only.

EDIT:

Also, please don't post if you don't know what you're talking about. I'm running Ubuntu 8.04 and the feature you're asking for is already implemented.

---

### Post by tacutu on 2008-08-21
if you know the name (or part of the name) of the package, select "look in: Name" in the search dialogue. It speeds thungs up quite a lot.

---

### Post by philinux on 2008-08-21
Open synaptic and click once on any app.

Then type the first letters say nvidia and it will take you there. Once there click any app again and scroll your mouse. If you dont click an app for some reason the scroll is very slow.

---

### Post by tacutu on 2008-08-21
> **philinux said:**
> Open synaptic and click once on any app.

Then type the first letters say nvidia and it will take you there.

hei, this is brilliant! I had no idea it works like this!

---

### Post by 3rdalbum on 2008-08-21
I think most developers have faster machines, which can search a 25,000 item database in a few seconds.

Back in Ubuntu Breezy, it still only took maybe 20 seconds to search by description on a 333MHz computer with 128 mb RAM. And a couple of seconds to search by name only.

If you want to install a package that you know the first few letters of the name, you can do this:

```
sudo apt-get install apac
```
(or whatever the first four letters are) then press the tab key to autocomplete. If the computer beeps at you, press tab once or twice more and it will show you all the choices.

---

### Post by Cinnander on 2008-08-21
You may find Programs Menu (aka System Menu) > System > "Add/Remove" to be an easier to manage tool. Everything is categorised as in Synaptic but there isn't thousands of lib* entries, and searching for some things can be quicker (e.g. if you wanted to search for third-party-only games).
If you or anyone else who uses the computer is a Linux newbie, this is friendlier than synaptic (no 'scary' technical features like filters and repository management)

(If you don't have a menu entry for it, the command is /usr/bin/gnome-app-install - it works on Xubuntu so I guess Ubunto too. Not sure about Kubuntu though)

---

### Post by Elfy on 2008-08-21
Intrepid does have a quick search in synaptic - so it will turn up - but I don't know if it's quicker than using a letter to search.

---

### Post by 2CV67 on 2008-08-21
Thank you all for your various responses.

Thanks particularly to philinux for: 
> Open synaptic and click once on any app.

Then type the first letters say nvidia and it will take you there. ..... If you dont click an app for some reason the scroll is very slow.

That is exactly what I am looking for & it works perfectly.
But I never found it because I never clicked on one app before searching for another app - why would I?

I didn't particularly appreciate kdorf's comment:
> Also, please don't post if you don't know what you're talking about. I'm running Ubuntu 8.04 and the feature you're asking for is already implemented.
1. This is an absolute beginners forum, so I am allowed to not know what I am talking about.
2. I had searched extensively before asking this question, and never seen any mention of the function or of how to activate it.

As tacutu said:
> hei, this is brilliant! I had no idea it works like this!
Exactly!

So now I am happy because I know how to do what I wanted.
(as usual after asking a question here - thanks everybody).

I still think things could be improved if the search-by-letter feature was activated automatically or if there was an instruction somewhere, so everybody could benefit.

Of course, anybody Googling about it will find this thread, which is one good reason for posting dumb questions on forums!

Thanks again!

---

### Post by philinux on 2008-08-21
I only stumbled on this by pressing letters expecting it to go to say letter n. Then one day I click one app to see its description then pressed a letter and hey presto.

---

### Post by Elfy on 2008-08-21
> **philinux said:**
> I only stumbled on this by pressing letters expecting it to go to say letter n. Then one day I click one app to see its description then pressed a letter and hey presto.Exactly how I found out - and how I discovered the middle click paste - another gem hidden :)

> I didn't particularly appreciate kdorf's comment:Don't take any notice - and carry on asking questions, you can guarantee that someone else will want the answer. I posted a thread because I wanted to know how to bump a thread lol



> I still think things could be improved if the search-by-letter feature was activated automaticallyI'd guess that it would work once the 'name pane' had the focus whether you had clicked or not, but haven't checked.

---

### Post by 2CV67 on 2008-08-21
philinux:
Very glad you stumbled on it & even more glad you could be bothered to tell me (us)!

forestpixie:
Thanks for middle-click paste - I had never heard of that either.
But Synaptic Search (as I wanted & suggested it) does not seem to work just by selecting "look in :name". 
Looks like we have to remember to click on any app first!

Thanks guys!

---

### Post by kerry_s on 2008-08-21
that type of search works in a lot of places, nautilus for example, click on a folder and start typing the name your looking for.

---

### Post by mc4100 on 2008-08-21
It also works in Evolution (very useful if you have *loads* of folders, like me.)

Edit: Just tried Rhythmbox ... it works there, too!

---

### Post by Sealbhach on 2008-08-21
> **kdorf said:**
> 

EDIT:

Also, please don't post if you don't know what you're talking about.

I thought that was the whole point of the Absolute Beginners Forum? :confused:


.

---

### Post by 2CV67 on 2008-08-22
> **kerry_s said:**
> that type of search works in a lot of places, nautilus for example, click on a folder and start typing the name your looking for.

Well - I would never have found that either!

You have to wonder why these GUIs don't open with, say, a "Scroll to:...." box, open & highlighted for business so you would pretty much see that just typing letters would take you straight there, without having to click on anything.
Especially Synaptic, where the need is so great.
Good GUI should be obvious/instinctive, without having to remember what to do & above all without having to do something else!
If that is too difficult, then a toolbar button labelled "Scroll to:" would be better than having to click on some unrelated folder.

Next revision, maybe?

Thanks for those various examples, and I hope they may help others.

---

