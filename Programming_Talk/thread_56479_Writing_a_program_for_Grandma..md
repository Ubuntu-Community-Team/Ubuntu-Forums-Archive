---
title: "Writing a program for Grandma."
date: 2005-08-12
forum: Programming Talk
---

### Post by TreeFrog on 2005-08-12
[FONT=Arial]Hi can anyone suggest where I should begin in this?

Specifically which tools should I learn to use for which purpose. Bearing in mind the simplistic requirement of the final application.

I'm thinking of writing a simple front end to run on Ubuntu in Gnome. tabs, buttons, output and input boxes. 
At the back it will run some simple scripts. perhaps do a little opening and parsing/editing of files too I'm not sure yet. Perhaps later it will even connect to the net to get up-to-date scripts.

I want it to be easily used by everyone. In that I mean if I give it to you, you can use it straight off. no configuration or install of other packages. Though it may be able to make necessary configuration changes once it is running.
This is for Grandma... if you get what I mean!

I have some experience with Delphi and C so concepts are Ok with me. it is just the tools and considerations for this environment I'm worried about. 

Any suggestions are appreciated.

Thanks.

Treefrog.[/FONT]

---

### Post by Lord Illidan on 2005-08-12
A front end for what? Or just to use Ubuntu?

If you use Gnome ... Glade
If you use KDE .... Kdevelop

---

### Post by TreeFrog on 2005-08-12
Sorry, ya not really a front end of something. More of just a GUI. I'm getting ahead of myself there.
I supose it could be inturprited as a front end of Ubuntu. that is what it will help to manage.
Oh dear says you.. another GUI for control systems. 

Anyone know the pit falls of such things. This is for good old Grandma Frog.

Glade looks interesting. I'll have a swing at it. Thanks.

Treefrog.

---

### Post by Teren on 2005-08-12
[QUOTE=TreeFrog]Sorry, ya not really a front end of something. More of just a GUI. I'm getting ahead of myself there.
I supose it could be inturprited as a front end of Ubuntu. that is what it will help to manage.
Oh dear says you.. another GUI for control systems. 

Anyone know the pit falls of such things. This is for good old Grandma Frog.

Glade looks interesting. I'll have a swing at it. Thanks.

Treefrog.[/QUOTE]
 I think TreeFrog means something like a kiosk-mode... an application, that takes whole screen, with buttons and stuff like "Browse internet", "Read mail" and stuff....

...But I am sure that is not what he means :)

---

### Post by tread on 2005-08-12
> I think TreeFrog means something like a kiosk-mode... an application, that takes whole screen, with buttons and stuff like "Browse internet", "Read mail" and stuff.... 

If this is what he means, it would probably be easier to take a minimal wm (or write one) and use something to put launchers on the desktop (rox in pinboard mode maybe?)

---

### Post by TreeFrog on 2005-08-13
I'll fiddle with a few things and post up a proof of concept. Then I can get all the constructive suggestions from a more informed perspective.

All in the name of Grandma    :grin: 

Thanks

Treefrog.

---

### Post by Lord Illidan on 2005-08-13
You will need big icons then... or buttons..

I think you can do this in Gnome without any fiddling, just by putting a few well placed icons on the desktop and increasing their size for dear ol' grandma..

However if you're in it for the challenge of programming something, I say good luck, it is n't every feller who does something like you for the convenience of other users..

---

### Post by tread on 2005-08-13
Maybe you could whip up something in gimp, to show what you have in mind?

---

### Post by TreeFrog on 2005-08-13
Ok it is not really for Grandma. It is for me. It is for you. It is for the me and you that was before we knew what to do. And it is for the other Grandmas of the world that might never know what to do but still need it doing. They are Human beeings too... I supose big bold icons could be good now you mention it.

However Grandma is just a really good extreem perspective to keep in mind so that it won't get more complicated than absolutly necessary. There perhaps could be a complicated ADVANCED part but it is suposed to be good enough for "Grandma"
The Grandma Project. lol

I have a few days free to hack at it so I'll see what I can pull together. 
It wont be pritty I'm sure. lol ... But we will see if it is worth working on more after that.

Any simple tutorials and examples on Glade. ?
I think I'll start with Glade. It is generic enough.. at least for Gnome and Ubuntu. I dont have anything against KDE but I want it to sit well for Grandma when she starts off. And she will most probbably start with Gnome. It is easy for her to get her simple head around. She has a good sence of humor too has Grandma. So I'll try to keep it light and easy on the nerves. 

It has probably been done a hundread times. So one more wont hurt.  :grin: 

Later guys.

Trefrog.

---

### Post by TreeFrog on 2005-08-17
Ok the Grandma project is running aground. Manly because I have not got enough C programming skill/know how. I'm so frustrated with myself for not being able to do it you cant imagine. An itch that cant be scratched. 

I'll outline it and anyone who is interested can either suggest something to make it easy or have a go just for fun.. It seems to be very small.
So it's up for grabs. 
I think if it were polished up nicely though it would go down very well with all "Grandmas" of this world and perhaps even the Gnome people.

I noticed that the first thing making it awkward to move to Ubunto from Windows is the way things get installed. I honestly cant say to someone "It is easy" if I know they really are not up for opening a console to type....
[I]sudo apt-get install streamtuner
sudo apt-get install streamripper[/I]
or walk through "How to add extra repositories"

It's just fine for me I like it. But I cant say "Hey try this Ubuntu Linux" to most of the people I know. And I'm sure they would use it happily, for the limited PC use they want, if they could.
I'd love to say it but they are all Grandmas when it comes to IT, at least at this level. 
You cant hold it against them and you cant ask them to learn a whole lot either but they are not completely dumb and deserve a shot at Ubuntu too. Ubuntu deserves a shot at them.
On top of that I'm getting sick of just explaining how to sort out peoples spyware and virus problems. It is so sad when I know the PC in question will not run so well with half the protection on it.


**Outline:**
So I thought if there was a way to grab the scripts form the wonderful
[http://ubuntuguide.org/](http://ubuntuguide.org/)   (Just the applications to begin with)
A little bit of parsing and presenting in a GUI. An install button to fire up a selected script. 
The Grandma tool could open a console and just throw the scripts in. Then all the errors would show up clearly. 
The [http://ubuntuguide.org/](http://ubuntuguide.org/) is set out very clear and very easy to work from. The beauty would be that if something needed changing it would be active for everyone with an intent connection. 


I can see it is not the best way to install many applications, Synaptic is the way to go, but for Grandma it has to be easer. Even if it has to stay unofficial like [http://ubuntuguide.org/](http://ubuntuguide.org/) is now.

Many people have written personal install scripts. Some have been posted here. Most of us would probably use a simple press button and run tool if it was there. At least for the small things without big dependencies. 

I'm so frustrated that I cant do it. 

The Unofficial Grandma Install Tool or UGIT is yours. 

Treefrog.

---

### Post by tread on 2005-08-17
So that's what you wanted to do!
Look up this thread:
[http://ubuntuforums.org/showthread.php?t=42553](http://ubuntuforums.org/showthread.php?t=42553)

---

### Post by TreeFrog on 2005-08-17
That is so funny,
the idea in 
[http://ubuntuforums.org/showthread.php?t=42553&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=42553&page=1&pp=10)
is exactly what I was thinking of.

The result looks OK and sound ok but I still have not managed to download it and compile it. 
I'd try Breezy but that has its own problems.
Is it somewhat stalble at the moment? 
perhaps I will give it a go.

---

