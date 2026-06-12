---
title: "How To Remove Unwanted Icons From DASH?"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by Wheel on 2012-06-08
I've recently installed, then subsequently uninstalled a couple of things.  All uninstalled cleanly and thoroughly, but some icons are left behind in DASH.  The icons don't do anything since there's no corresponding program.  They're just dead and occupying space.

Can I remove them from DASH?  If so, how?

---

### Post by Frogs Hair on 2012-06-08
First, try right clicking the icon and selecting unlock from launcher. If that does not work try the following command. Note: you will have to reset your favorite applications after using the command.```
unity --reset-icons
```

---

### Post by MG&amp;TL on 2012-06-08
Run:

```
gksu nautilus
```

then navigate to /usr/share/applications/ and *carefully* remove the ones you don't need. I recommend caution, root powers are not to be toyed with.

---

### Post by Wheel on 2012-06-08
> **Frogs Hair said:**
> First, try right clicking the icon and selecting unlock from launcher. If that does not work try the following command. Note: you will have to reset your favorite applications after using the command.```
unity --reset-icons
```

Thanks for your thoughts, Frogs Hair.  
You may have misunderstood my situation -- or perhaps I failed to explain it  clearly.

My Launcher is just fine.  I am comfortable making additions or deletions to it as needed.
The troublesome icons I referred to were those inside of DASH, not those in the Launcher itself.

Unfortunately, the icons inside of the DASH do not offer right click options which you do see when right clicking icons on the Launcher.  There *are* no right click options in the DASH;  a right click on a DASH icon simply launches that app.
Since the icons I'm trying to kill reference uninstalled apps (i.e. they point to **nothing**), nothing happens.

I have run the "reset icons" command in the past so I knew pretty much to expect, but I thought I'd give it a try anyway.  First I backed up my home folder, then I ran the code.
The Launcher reset itself to its default state (as I expected).  After checking the DASH, I saw that those zombie icons (those that won't die!) remained in the DASH!  Oh well.  I simply restored my home folder to return my customized Launcher to my preferred state.



> Run:

     Code:
     gksu nautilus 
then navigate to /usr/share/applications/ and *carefully* remove  the ones you don't need. I recommend caution, root powers are not to be  toyed with.     Thanks for your comment as well, MG&TL.

I tried this solution as well.  Unfortunately, since the blasted icons I'm trying to rid myself of point to apps which I either "autoremoved" from Terminal OR "completely removed" from Synaptic, they no longer exist in the applications folder and as such, offered nothing to remove.

I couldn't agree more about treading lightly while wielding root powers.
I've done some hasty and foolish things in the past--and suffered the consequences!

...On a different note.  As you can see, I haven't quite figured out how to properly take multiple quotes from different posts and incorporate them into a single reply.  The initial quote always looks fine, but the second one is simply a manual copy & paste job.

So how *DO *you do that?

---

### Post by MG&amp;TL on 2012-06-08
> **Wheel said:**
> 

...On a different note.  As you can see, I haven't quite figured out how to properly take multiple quotes from different posts and incorporate them into a single reply.  The initial quote always looks fine, but the second one is simply a manual copy & paste job.

So how *DO *you do that?

Can you see the little button next to the Quote button? Looks like a newspaper or a magazine. Click that on all the posts you want to quote, then open a new reply. :)

---

### Post by Wheel on 2012-06-08
> **MG&TL said:**
> Can you see the little button next to the Quote button? Looks like a newspaper or a magazine. Click that on all the posts you want to quote, then open a new reply. :)

Aahhh!  Very nice.   I didn't even notice that.   (See that--2 or 3 beers and my brain goes on holiday!)  The next time it comes up, I'll give it a test drive.  :cool:

---

### Post by diesch on 2012-06-08
> **Wheel said:**
>  
I tried this solution as well.  Unfortunately, since the blasted icons I'm trying to rid myself of point to apps which I either "autoremoved" from Terminal OR "completely removed" from Synaptic, they no longer exist in the applications folder and as such, offered nothing to remove.


Have  a look at *~/.local/share/appliactions/  *the Dash looks there for .desktop files, too.

---

### Post by Wheel on 2012-06-08
> **diesch said:**
> Have  a look at *~/.local/share/appliactions/  *the Dash looks there for .desktop files, too.

Excellent.  This has solved my (minor) problem.  Thank you.

---

