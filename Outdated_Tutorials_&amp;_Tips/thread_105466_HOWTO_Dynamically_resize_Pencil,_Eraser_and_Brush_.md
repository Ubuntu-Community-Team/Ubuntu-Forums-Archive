---
title: "HOWTO: Dynamically resize Pencil, Eraser and Brush in The GIMP"
date: 2005-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by MetalMusicAddict on 2005-12-18
This is for the people who are used to this feature in Photoshop but everyone who uses The GIMP could find this usefull.

-This HOWTO involves using a wheelmouse. If you dont have one this still should help you to assign a keyboard action. Ill work on that and add it later.
So far Ive tried this on Windows, Ubuntu, a desktop and a laptop. All worked for me.


**1**. Create a new brush by going to **File**->**Dialogs**->**Brushes**. 
**2**. Once the **Brushes** dialog box is there at the bottom, click on the **New Brush** option.
**3**. Give the brush a name. _Dynamic_ is what I call mine.
Your settings should look something like the pic below to start.

[IMG]http://img416.imageshack.us/img416/6903/untitled7qc.png[/IMG]
As you learn, change 'em as suited. :)


**4**. Open the **File** menu then go to **Preferences**.
**5**. Select **Input Controllers**.
**6**. Select tab **Main Mouse Wheel**.
**7**. Make sure the **Enable this controller** box is checked.
**8**. Assign a preferred **Action** to your mouse **Event**. You will find the actions under **Context** in the popup dialogue when you click on **Edit** to edit your **Event**.

ie: I have assigned the **Scroll Up (Control)** event to **context-brush-radius-increase** action. Respective, **Scroll Down (Control)** is assigned to **context-brush-radius-decrease**.
So now by holding the **Control** button and scrolling the mouse wheel **Up** or **Down** I can dynamically change the size of the brush. :)

Now you can resize on-the-fly your brush, pencil and eraser. Funny how the answer to alot of peoples post was built in. :)
The 1 thing Ive seen is that you will only **see** the brush resize if you hover over your image but the window is not focused.

Not the same as PS does it but still very nice. And remember, The GIMP isnt PS.

---

### Post by stuporglue on 2005-12-30
Excelent. 

I have a feeling this is going to increase my effeciency quite a bit when using GIMP. 

Thank you!

---

### Post by MetalMusicAddict on 2005-12-30
This was 1 of a couple things that have slowed my move to The GIMP. Glad it helps someone.

(I gotta upload the pic to the 1st post again)

---

### Post by M7S on 2005-12-30
Is there any way to change the amount of increase or decrease per scroll? Right now the size goes up or down with 10 each time, which is way to much for my liking.

Thanks for the tip anyway,

M7S

---

### Post by MetalMusicAddict on 2005-12-30
Change:
**context-brush-radius-increase-skip** to **context-brush-radius-increase**
and
**context-brush-radius-decrease-skip** to **context-brush-radius-decrease**

Im gonna edit the guide to show this. Its actually how I have mine.

---

### Post by magnusbb on 2005-12-30
Thanks for this howto. I've really missed this!

---

### Post by M7S on 2005-12-30
> Change:
context-brush-radius-increase-skip to context-brush-radius-increase
and
context-brush-radius-decrease-skip to context-brush-radius-decrease

Im gonna edit the guide to show this. Its actually how I have mine.

Thanks

---

### Post by kperkins on 2005-12-31
Great stuff--Thanks!

---

### Post by Pretzal on 2006-01-01
nice tip! Could have used this the other day!

---

### Post by mztriz on 2006-01-01
Thank you so much, this is every helpful.

---

### Post by PhilOSparta on 2006-01-07
Nice work!

My wife and I have been using your new tool for over a week now.
It has more than doubled our productivity on a number of our routine tasks.

Thanks for your post.

Phil

PS - I see that there is a new book coming out on the GIMP soon.
[http://www.ubuntuforums.org/showthread.php?t=110392](http://www.ubuntuforums.org/showthread.php?t=110392)

---

### Post by Tab on 2006-01-09
What I want to know is why the hell some kind of feature like this isn't already in by default. :|

---

### Post by simplyw00x on 2006-01-09
Very good tutorial; simple, quick and startlingly effective. Thanks a lot.

---

### Post by MetalMusicAddict on 2006-01-09
[QUOTE=Tab]What I want to know is why the hell some kind of feature like this isn't already in by default. :|[/QUOTE]
I also wonder. I look into talking to the devs to see what they say.

---

### Post by allelopath on 2006-04-10
This is great. Thanks for posting this.  I am a Suse person, but a link to this was posted on [email]Gimp-user@lists.XCF.Berkeley.EDU[/email]

---

### Post by graigsmith on 2006-04-10
this is an awesome tip! thank you :) 

figured out how to do it on any key you want. just go to interface and keyboard shortcuts.

there are alot of cool functions in there ;)

---

### Post by enopepsoo on 2006-04-14
:D 
My girlfriend is a photographer.  When I tried to switch her computer slowly to open source she complained about resizing brushes in the GIMP.
problem solved.  Nice work metalmusicaddict, and your government is violent!

---

### Post by MacSlow on 2006-05-19
I want to add a tiny but helpful hint to this great tip. Make sure to also configure:

[LIST]
[*]Wheel-Up (Shift): context-brush-hardness-increase
[*]Wheel-Down (Shift): context-brush-hardness-decrease
[/LIST]

Thus my dynamic brush manipulation shortcuts look like:

[LIST]
[*]Wheel-Up (Shift): context-brush-hardness-increase
[*]Wheel-Down (Shift): context-brush-hardness-decrease
[*]Wheel-Up (Ctrl): context-brush-radius-increase
[*]Wheel-Down (Ctrl): context-brush-radius-decrease
[/LIST]

This makes several painting actions very fast and efficient imo. While I'm by far no professional gimp-user (or photoshop for that matter), actually I use gimp only now and then, I greatly welcome this time-saving feature a lot. 

Best regards...

MacSlow

---

### Post by Ubuntuud on 2006-06-02
When I press Ctrl the color picker shows itself, so that I can't see how big the brush is while resizing. Is there a way to turn this off?

And is there a way to make the "dynamic" brush the standard brush?

---

### Post by MetalMusicAddict on 2006-06-02
[QUOTE=Ubuntuud]When I press Ctrl the color picker shows itself, so that I can't see how big the brush is while resizing. Is there a way to turn this off?[/QUOTE]
From 1st post.
[QUOTE=MetalMusicAddict]The 1 thing Ive seen is that you will only **see** the brush resize if you hover over your image but the window is not focused.[/QUOTE]
[QUOTE=Ubuntuud]And is there a way to make the "dynamic" brush the standard brush?[/QUOTE]It should stay your brush as long as you dont pick another.

---

### Post by Ubuntuud on 2006-06-03
[QUOTE=MetalMusicAddict]From 1st post.

It should stay your brush as long as you dont pick another.[/QUOTE]

I have "focus follow mouse" turned on, so I guess I'll have to live with it.

And with standard I meant on startup, but I found out already. There is an option called "save tool preferences" (or something similar).

---

### Post by mustang on 2006-09-07
Great tip! Thanks!

---

### Post by kosmic on 2006-09-08
Excelent Tip, Thank you.

---

### Post by matysjan on 2006-10-08
> **Ubuntuud said:**
> When I press Ctrl the color picker shows itself, so that I can't see how big the brush is while resizing. Is there a way to turn this off?

And is there a way to make the "dynamic" brush the standard brush?

So it is simple - when color picker shows it self, U can NOT see how You brush grows or shrink but ... the way to solve this is to click on gimp window (somewhere in empty space) and return the mouse on the picture area (BUT NOT CLICK) - now U can see the  brush silhouette and press CTRL and scroll mouse button to resize it! Simple and effective - so when U need to resize and see it try this procedure

     Jack

---

### Post by MetalMusicAddict on 2006-12-12
Killer! This guide got translated into Chinese. :) [http://my.opera.com/symbol/blog/show.dml/459828](http://my.opera.com/symbol/blog/show.dml/459828)

---

### Post by BLTicklemonster on 2006-12-26
!!! Finally, I can get past a radius of 19. (too lazy to figure it out in the first place)

Thanks, dude!!!

---

### Post by SuperMike on 2007-01-29
Is there a way that I can use Gimp and when I open it up it doesn't have pen, eraser, pencil, and brush sizes set to a huge size? How about 1 pixel x 1 pixel? That would be more suitable to me.

---

### Post by BLTicklemonster on 2007-01-29
Seeing's how I would want to use this quite a bit, and how gimp defaults to Circle (11), why can't I name it Circle (11 dynamic) so it will be a scroll away?

---

### Post by MetalMusicAddict on 2007-01-29
> **BLTicklemonster said:**
> Seeing's how I would want to use this quite a bit, and how gimp defaults to Circle (11), why can't I name it Circle (11 dynamic) so it will be a scroll away?

I think I'm missing what your trying to do. You can name the "dynamic" brush you create whatever you want. :)

Are you trying to do something beyond naming?

---

### Post by BLTicklemonster on 2007-01-29
Nah, just trying to keep it close at hand. Right now when I open gimp, it's at circle 11, if I had it named circle 11 dynamic, I guess I'd still have to scroll past the largest circle setting anyway, so it's a non starter from the git go. never mind. lol

---

### Post by MetalMusicAddict on 2007-01-29
> **BLTicklemonster said:**
> Nah, just trying to keep it close at hand. Right now when I open gimp, it's at circle 11, if I had it named circle 11 dynamic, I guess I'd still have to scroll past the largest circle setting anyway, so it's a non starter from the git go. never mind. lol

OOhhh... I see.

Google is our friend. While it didnt give me the direct answer it gave me a clue. ;)

In a Terminal:
```
sudo gedit /etc/gimp/2.0/gimprc
```

Find:
```
[SIZE="1"]
# Specify a default brush.  The brush is searched for in the specified brush
# path.  This is a string value.
# 
# (default-brush "Circle (11)")[/SIZE]
```
Change to:
```
[SIZE="1"]
# Specify a default brush.  The brush is searched for in the specified brush
# path.  This is a string value.
# 
(default-brush "Dynamic")[/SIZE]
```

That works! Who loves ya. ;)

---

### Post by BLTicklemonster on 2007-01-30
Thank you very much, Cory!

I'm on a windows machine right now, and set it up and it's fine.

The gimprc file is located in your documents and settings\yourname\gimp-version number

open in notepad (I guess) and here's what I have mine like:

```
# GIMP gimprc
# 
# This is your personal gimprc file.  Any variable defined in this file takes
# precedence over the value defined in the system-wide gimprc: C:\Program
# Files\GIMP-2.0\etc\gimp\2.0\gimprc
# Most values can be set within The GIMP by changing some options in the
# Preferences dialog.
(monitor-xresolution 96.000000)
(monitor-yresolution 96.000000)
(show-tips no)
#Specify a default brush.  The brush is searched for in the specified brush
# path.  This is a string value.
# 
#
(default-brush "Dynamic")
# end of gimprc

```


Thanks again!!!!

---

### Post by stalefries on 2007-01-31
Good news folks, the developer versions of the Gimp have scalable brushes now! gimp.org

---

### Post by BLTicklemonster on 2007-01-31
Aha! So the DO browse this forum! Stealers!


:)

Great news, though.

---

### Post by MetalMusicAddict on 2007-01-31
Ha! Killer. I guess Ill clean this up a little and freeze the guide. Maybe Ill dive into the things the gimprc file can do with a new thread. ;)

---

### Post by sparkguitar05 on 2008-06-05
Is there a way to use the [bracket] keys to increase and decrease brush sizes?  I'm so used to this in Photoshop and I'm having a really hard time switching over to GIMP.

---

