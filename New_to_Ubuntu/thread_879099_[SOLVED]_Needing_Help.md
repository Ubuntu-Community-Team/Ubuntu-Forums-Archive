---
title: "[SOLVED] Needing Help"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Shooter44 on 2008-08-03
Ok so I'm a new user trying to get the hang of Ubuntu 8.04LTS. So go easy on me here. I'm born and bred Windows. Which I'm trying to get away from. 

I have been doing a lot of reading here for Noobs and such. I'm trying to install some programs. Been reading this link which I got from here

h**p://monkeyblog.org/ubuntu/installing/

But like all tutorials I'm trying to learn from when I go to system &#8594; Administration &#8594; Synaptic Package Manager. Its not there. Nor is the add/ remove. 

So is there a way to add the package manager to my bar? 

Also can any of the experienced users here recommend a good noob book for Ubuntu 8.04 that I will understand. I'm very good in Windows but sooo darn lost in this. I have a lot of work to do here.. Off to do more reading. 

This forum is great with a TON of wealty info, but for a noob like me there is just sooo much information to take in at once it makes my head spin..  :lolflag:  Off to read...

---

### Post by GreenN00b on 2008-08-03
What programs do you want to install? Do they have linux versions?

---

### Post by Shooter44 on 2008-08-03
right now I'm trying to install utorrent. 1.7.7. I was just reading and it seems I might need something called wine???

---

### Post by GreenN00b on 2008-08-03
Get wine from here [http://winehq.org](http://winehq.org)
You can find instruction on how to install it on ubuntu on the download page.

---

### Post by Elfy on 2008-08-03
Yes you would - but there are other torrent clients available, transmission is default now, I use ktorrent (which is a kde app), deluge is a gnome application. I've used them all but prefere ktorrent.

Firstly though if you are sure that synaptic is not in the menu - you can see if it is installed by trying with a terminal. Open one - in accessories and paste this command in to it and enter

```
gksudo synaptic
```

if you get an error please paste it all in a post.

---

### Post by Shooter44 on 2008-08-03
Thank you very much for the quick help... But can you give me any ideas why my package manager isn't listed under the Admin tab? Thank you for the help...

---

### Post by Shooter44 on 2008-08-03
forestpixie that worked. But is there a way to add that to the top bar so I don't have to open the terminal and remember that code? 

And what is that top bar called anyway? The one at the top of the desktop with applications Places System. 

I'm not used to getting such good fast help in a forum. This place rocks...

---

### Post by Jack M. on 2008-08-03
You can add the icons to the top bar (called the menu bar) by right-clicking on it and choosing "Edit Menus". Then, make sure "Add/Remove..." under Applications and "Synaptic Package Manager" under System > Administration are both checked.

---

### Post by Elfy on 2008-08-03
> **Shooter44 said:**
> And what is that top bar called anyway? The one at the top of the desktop with applications Places System. It's a panel - so is the one at the bottom, to differentiate one is the top panel and the other the bottom panel :lol: j/k

> **Jack M. said:**
>  by right-clicking on it and choosing "Edit Menus". Then, make sure "Add/Remove..." under Applications and "Synaptic Package Manager" under System > Administration are both checked.right click the existing menu to get edit

---

### Post by Shooter44 on 2008-08-03
Ok this is fun now.. I managed to get wine installed. So next I'll try to install utorrent. Do I use the manager for that like I did wine? 

Now don't laugh.. when I go to edit my TOP menu.. LOL I see the options and the boxes are unchecked. I checked them both and hit enter. The box closes. But they are still not showing in my top menu. So I go back into the edit menu and the boxes are unchecked. Now when I put a check mark in there after like 2 seconds they come unchecked? Any ideas..  I'm lost..LMAO.. What a noob...

---

### Post by Elfy on 2008-08-03
You should be able to double click th wine exe and it will start with wine - but not sure as I don't use wine I'm afraid.

The menu issue isn't right - try and do it through terminal - it will open the same editor

```
alacarte
```if there is an output in the terminal post it, in the meantime I'll have a look around see if I can find anything, might be tomorrow though.


Also - welcome to the forums :D

---

### Post by Shooter44 on 2008-08-03
> **forestpixie said:**
> You should be able to double click th wine exe and it will start with wine - but not sure as I don't use wine I'm afraid.

The menu issue isn't right - try and do it through terminal - it will open the same editor

```
alacarte
```if there is an output in the terminal post it, in the meantime I'll have a look around see if I can find anything, might be tomorrow though.


Also - welcome to the forums :D

I still get the same results doing it that way thru the terminal. I'm going to take your advice and try rtorrent. Off to download it now..  Thanks..

Ok update, I managed to get rtorrent. It did its thing I guess. But were is it installed? LMAO.. I thought it would be under applications. That is were wine went. Any program I install will go to Applications correct?

---

### Post by Elfy on 2008-08-03
Good luck with rtorrent - I've never got the hang of that myself which is why I use a gui torrent client. My advice was to try ktorrent - big difference. But have a go with it 

this is the page I used to start with rtorrent

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by kansasnoob on 2008-08-03
I guess I'm confused ............. hey I'm old! You say:
> when I go to system &#8594; Administration &#8594; Synaptic Package Manager. Its not there. 

Do you NOT even have synaptic?

If your Ubuntu does not have synaptic you have a huge problem.

Then the question is, "why do you have no synaptic"?

---

### Post by Liolikas on 2008-08-03
Transmission, Deluge also good and have nice GUI.

---

### Post by Elfy on 2008-08-03
> **kansasnoob said:**
> I guess I'm confused ............. hey I'm old! You say:


Do you NOT even have synaptic?

If your Ubuntu does not have synaptic you have a huge problem.

Then the question is, "why do you have no synaptic"?

It runs from a terminal it appears - it just won't appear in the menu same with add/remove. But it does seem a bit strange that alacarte won't let it enable...

---

### Post by Shooter44 on 2008-08-03
kanasanoob I have synaptic I just want it to show in the top menu... 

Then I'm off to get ktorrent.. LOL I would like whatever is easier as I'm used to utorrent...  BRB..

---

### Post by Liolikas on 2008-08-03
> **Shooter44 said:**
> kanasanoob I have synaptic I just want it to show in the top menu... 

Then I'm off to get ktorrent.. LOL I would like whatever is easier as I'm used to utorrent...  BRB..
Deluge.

---

### Post by Elfy on 2008-08-03
> Ok update, I managed to get rtorrent. It did its thing I guess. But were is it installed? LMAO.. I thought it would be under applications. That is were wine went. Any program I install will go to Applications correct?Glad you're amused anyway - so rtorrent doesn't have a menu item, nor will it have a gui - it works from the command line.

see post 13 - nice to see someone actually not complaining about it being different lol

---

### Post by kansasnoob on 2008-08-03
> **forestpixie said:**
> It runs from a terminal it appears - it just won't appear in the menu same with add/remove. But it does seem a bit strange that alacarte won't let it enable...

Perhaps a redundant question, but what version of Ubuntu are you running? I mean like 7.10 Gutsy, or 8.04 Hardy:confused:

---

### Post by Shooter44 on 2008-08-03
You won't see me get upset.. I love learning new stuff.. Ok I uninstalled rTorrent and installed ktorrent. So how do we start that sucker.. 

I really need a good book on this.. I hope to look back on this one day and be able to laugh at myself and say what a freakin noob... :)


Running 8.04LTS hardy..

---

### Post by kansasnoob on 2008-08-03
If this is truly 8.04 Synaptic should just be there.

Maybe try:

```
sudo apt-get install synaptic

```

or:

```
sudo apt-get install --reinstall synaptic

```

Transmission and Brasero work so well together I can't imagine wanting anything different.

---

### Post by Ingenue on 2008-08-03
> **Shooter44 said:**
> Also can any of the experienced users here recommend a good noob book for Ubuntu 8.04 that I will understand..

I bought *The Official Ubuntu Book, 3rd. ed.*, it is only offered at Barnes and Nobles though. It does come with a LiveCD with option to install. This book covers Hardy. Not having any Linux know-how when I got Ubuntu, this broke it down for me.

---

### Post by Shooter44 on 2008-08-03
Don't know if this matters or not but this is on my dedicated server that I'm running Ubuntu 8.04. I'm logged on thru NX.. 

So after installing ktorrent were is that located so I can run the program?

Ingenue thanks for the advice on the book. Off to check it out now...

---

### Post by ace007 on 2008-08-03
It wont appear because you are not logged in as an administrator.  I created a non-admin user for my family and they cant access add/remove and synaptic.  The menu doesn't even show it for them.

---

### Post by Shooter44 on 2008-08-03
Can I log in as admin? It's a dedicated box with only me on it. If so I wonder how.. 

I only say this because how do all the Ubuntu users remember all those commands to put into the terminal?

Update i found ktorrent under apps internet.. Off to play..

---

### Post by Ingenue on 2008-08-03
> **Shooter44 said:**
> Ingenue thanks for the advice on the book. Off to check it out now...

No problem, us newbies got to stick together.):P

---

### Post by kalwisti on 2008-08-03
Hi, Shooter44,

Since you've said that you're new to Linux and would like to read some printed manuals/guidebooks, I'd like to suggest a few book titles for you. (I'm an old fogey who prefers printed guidebooks when I'm trying to learn something new). 

Grant, Rickford. *Ubuntu for Non-Geeks: A Pain-Free, Project-Based, Get-Things-Done Guidebook*. 3rd ed. No Starch Press, 2008. 360 p.
ISBN 1593271808. $34.95 (retail); $23.07 Amazon.com
Covers Ubuntu 8.04 Hardy Heron

I own a copy of the 2nd ed. of Mr. Grant's book (which covers 7.04 Feisty Fawn) and it is very nicely done. Practical and helpful without being as condescending as some of the "For Dummies" books are, and without their lame attempts at humor. Unless something went drastically wrong with the new edition, I'd assume that is of the same quality as the 2nd ed.

Thomas, Keir, and Jaime Sicam. *Beginning Ubuntu Linux*. 3rd ed. Apress, 2008. 768 p.
ISBN 1590599918. $39.99 (retail); $26.39 Amazon.com
Covers Ubuntu 8.04 Hardy Heron

I have used a library copy of the 2nd ed. of Mr. Thomas' book and he does a thorough job of covering just about everything you'd want to know about Ubuntu. (Due to its greater length, he does cover some topics which are not in Grant's book).  

Gagn'e, Marcel. *Moving to Ubuntu Linux*. Addison-Wesley Professional,
2006. 496 p.
ISBN 032142722X. $39.99 (retail); $30.39 Amazon.com
[Covers Ubuntu 6.06 Dapper Drake]

Although Marcel Gagne's book is now somewhat dated, I list it here because he writes clearly, in a fun style, and is especially good at explaining basic Linux concepts to new users. He too concentrates on practical, everyday activities/programs that average folks use on their computers. 

Although each of these books has their positives, if I were pressed to rank them in order of usefulness to newbies, I'd put Grant at #1, Thomas at #2 and Gagn'e at #3 (due only to its age). But before you spend your hard-earned money, I'd suggest you first try looking for them at your local library, and if they are not in the collection, ask to borrow a copy via interlibrary loan. Another option would be to browse through them at a local bookstore. 

HTH,
=david

---

### Post by Shooter44 on 2008-08-03
I'll be going to the bookstore tomorrow to purchase one. ;) I don't mind having one of my own....  Thanks everyone for the quick great help I received tonight. I'll be back tomorrow with somemore questions I'm sure....

---

### Post by Ingenue on 2008-08-03
Your welcome. If you feel this thread has answered your questions don't forget to mark it as solved with the thread tools. :)

---

### Post by Shooter44 on 2008-08-03
It has answered most of my questions but I'm not sure were the thread tools are.. Sorry..

Edit I seem to have found them...

---

### Post by Ingenue on 2008-08-03
I didn't either, they should be at the top of any of the thread pages. Just click on the link that says Thread Tools and select Solved. I was told to do this so people would not keep answering a question when it has already been answered satisfactorily.

---

