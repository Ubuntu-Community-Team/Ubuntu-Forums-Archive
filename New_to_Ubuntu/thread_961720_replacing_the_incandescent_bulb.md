---
title: "replacing the incandescent bulb"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-10-28
hi everyone.i know it may sound weird and trivial to you.the icon showing information appears as a light bulb,right.but i would like it to be a CFL instead of a traditional incandescent bulb.how can i do this?

---

### Post by aktiwers on 2008-10-28
Could you be more specific? Maybe post a screenshot?

Most your icons are in /home/yourusername/.icons
folder, you could look there and replace the image with one you like. 
But we need a little more info to be more helpfull.. at least I do :)

---

### Post by stonecoldjha on 2008-10-28
sadfully,no one evem viewing my thread.

---

### Post by aktiwers on 2008-10-28
34 people viewed your thread so fare, I think you need to be a little more clear about what you need help with.

---

### Post by scorchgeek on 2008-10-28
You would need to find a CFL icon on the Internet and then replace the information icon in the icons folder, as said above. We need a bit more information about exactly what you want, though.

---

### Post by Therion on 2008-10-28
> **aktiwers said:**
> 34 people viewed your thread so fare, I think you need to be a little more clear about what you need help with.
OP wants to change the system updates indicator-icon from an incandescent light bulb (icon) to a Compact Fluorescent Light bulb (icon).

---

### Post by aktiwers on 2008-10-28
Do you have a  Compact Fluorescent Light bulb icon already?

Then you need to replace the incandescent light bulb icon images. I think its a good idea to back them up first though. It should be located here
/home/USERNAME/.icons/YOURCURRENTICONTHEME/scalable/status/dialog-information.png

Where USERNAME is your ubuntu username and YOURCURRENTICONTHEME should be replaced with your current icon theme name. 
If you replace that .PNG file with another Icon it should do the trick.. 

I have not done this before, and never use the default human theme, but I found it is also located here:

> 
/usr/share/icons/Human/16x16/status/dialog-information.png
/usr/share/icons/Human/22x22/status/dialog-information.png
/usr/share/icons/Human/24x24/status/dialog-information.png
/usr/share/icons/Human/48x48/status/dialog-information.png
/usr/share/icons/gnome/16x16/status/dialog-information.png
/usr/share/icons/gnome/22x22/status/dialog-information.png
/usr/share/icons/gnome/24x24/status/dialog-information.png
/usr/share/icons/gnome/32x32/status/dialog-information.png
/usr/share/icons/gnome/scalable/status/dialog-information.svg
So I would try my first suggestion and then Restart X (CTRL+ALT+BACKSPACE) and see if it changed.
If yes, GOOD!

If not, I would change the other onces as well (first make a backup of them, and change them as root).

---

### Post by stonecoldjha on 2008-10-28
thanks,i could locate that icon in the location as u told.and,i have the CFL image,but i somehow ned to get rid of its background,or need an icon of the very same instead.do we even have an icon for that?

---

### Post by aktiwers on 2008-10-28
I don't know..  You want the background to be transparent?
If you know howto, you could fix it in Gimp, though I am not that strong in gimp.

Can you upload the picture/icon for us to see? :)

---

### Post by stonecoldjha on 2008-10-28
yeah,but even i have no experience with gimp.the icon is attached herewith.

---

### Post by DGortze380 on 2008-10-28
> **stonecoldjha said:**
> yeah,but even i have no experience with gimp.the icon is attached herewith.

done

---

### Post by aktiwers on 2008-10-28
> **DGortze380 said:**
> done
Nice! 

I tried doing the same...  what a big fail!   :D
I won't even post it here :P

---

### Post by Paqman on 2008-10-28
How's this? I've added some lighting and made it into a 48x48 png. Still not really an icon though, just a wee picture. So it might look a bit odd in your panel.

---

### Post by stonecoldjha on 2008-10-28
thanks,you took the trouble to get it done for me,thanks a lot.

---

### Post by stonecoldjha on 2008-11-02
can someone please make an icon using that image,i.e. make it in all the required formats,like 16x16,22x22,etc.thanks in advance.

---

### Post by Paqman on 2008-11-02
> **stonecoldjha said:**
> can someone please make an icon using that image,i.e. make it in all the required formats,like 16x16,22x22,etc.thanks in advance.

That's very easy to do yourself.

Open the image in GIMP, and select Image > Scale Image and change the size. Then File > Save As. Rinse and repeat.

---

### Post by farmer ck on 2008-11-02
here is a 16x16 and a 22x22. They ain't beautiful but I don't think they're too bad. If you need any other sizes let me know and I'll give it a shot.

---

### Post by diablo75 on 2008-11-02
How cool!  I'd love to seen a screenshot of this thing in action after you replace the old light bulb icon.

---

### Post by occams_beard on 2008-11-02
Nifty, I'm going to change my icon to one of a burning tire!

---

### Post by coldcoffee on 2008-11-02
Sweet! I want to change mine now too. And thanks for the footwork guys. I fail at gimp big time. But I will try out Paqman said.

The cfl bulb does make more sense in a way. A little more modern. Progressive.

---

### Post by stonecoldjha on 2008-11-02
can someone please make an icon using that image,i.e. make it in all the required formats,like 16x16,22x22,etc.thanks in advance.

---

### Post by rhcm123 on 2008-11-02
this is a really cool thread... i think i'll change my icon to the ubuntu logo!:guitar:

---

### Post by diablo75 on 2008-11-02
> **occams_beard said:**
> Nifty, I'm going to change my icon to one of a burning tire!

That is hilarious!

---

### Post by stonecoldjha on 2008-11-02
to create a usable icon we need the following formats of that image:
16x16
22x22
24x24
32x32
48x48
72x72
128x128

---

### Post by farmer ck on 2008-11-02
I went ahead and made the icons in the other sizes yall asked for. Hope yall like them. Let me know if I can help with anything else... maybe I should try the buring tire next. ha ha ha.

---

### Post by coolbrook on 2008-11-02
The CFL bulb is a good idea stonecold.  Maybe you can pitch the argument to Canonical or whoever designs the icons.  I've been meaning to replace the green logout man with a penguin and maybe I'll get around to it.

---

### Post by Hijinx on 2008-11-02
second the notion.  fantastic customization idea op'er.

---

### Post by justchange on 2008-11-03
Hey! Wait a minute!
I want to play, too!

Here's _my_ take on the CFL bulb... and Occam's burning tire, too.
Have fun!

(Part 1 of 3)

---

### Post by justchange on 2008-11-03
Here's more images and sizes... (part 2 of 3)

---

### Post by justchange on 2008-11-03
And here's the last of them... (part 3 of 3)

Note: the *tire.svg* was an afterthought and could have been much better if I'd thought it through, but it's late and I'm tired... maybe tomorrow, if I get a request for it.

Have fun!

---

### Post by occams_beard on 2008-11-03
Thanks! Now I can offset the CFL icon's carbon credits. Woohoo :) Down with Gaia!

---

### Post by HittingSmoke on 2008-11-03
> **occams_beard said:**
> Thanks! Now I can offset the CFL icon's carbon credits. Woohoo :) Down with Gaia!

Oh my, this thread has cracked me up since the burning tire comment. Lets build an entire theme based on destroying the planet. Call it F' Gore.

Or, "Springfield Tire Fire"

---

