---
title: "Two mice on the screen"
date: 2008-09-16
forum: Programming Talk
---

### Post by shantanu.nalawade on 2008-09-16
Hi everyone :),

I'm working on a project in which I've to display TWO CURSORS simultaneously on the screen.

I'm aware that the X-server handles the events of the mouse.

I wanted to ask How the X-server and GTK(tool kit which I might use to design the cursor) communicate?

Also is this possible using X-Lib?

If yes which one would be more feasible and easy?

If you guys have some examples which I can look into please do post them.

Thank you.

---

### Post by Quikee on 2008-09-16
You can't do that - not until [MPX]("http://wearables.unisa.edu.au/mpx/") is available in the xserver - which will be in xserver 1.6 or 1.7 (1.5 was released recently). You can merge MPX yourself if you want.

---

### Post by prshah on 2008-09-16
> **shantanu.nalawade said:**
> 
I'm working on a project in which I've to display TWO CURSORS simultaneously on the screen.
I'm aware that the X-server handles the events of the mouse.


You're looking for the [Multi Pointer X server]("http://wearables.unisa.edu.au/mpx/?q=mpx") Includes screenshots (18 mice !!)

Edit: Quikee was too quick.

---

### Post by shantanu.nalawade on 2008-09-16
Ya I've heard about MPX.

But I've an older x-server.

I wanted to develop a similar application.

I was searching for the source code for MPX but couldn't find it.

Could help me with this.

It would be really helpful.

Thank You.

Hoping for your reply.

---

### Post by brnetonboy on 2008-09-17
> **Quikee said:**
> You can't do that - not until [MPX]("http://wearables.unisa.edu.au/mpx/") is available in the xserver - which will be in xserver 1.6 or 1.7 (1.5 was released recently). You can merge MPX yourself if you want.

When will xserver 1.6 be out? I've been wanting MPX forever...

---

### Post by escapee on 2008-09-17
> **shantanu.nalawade said:**
> Ya I've heard about MPX.

I was searching for the source code for MPX but couldn't find it.

Could help me with this.

It would be really helpful.



It's on the MPX site that is linked in the post just above yours, check it out.

---

### Post by Quikee on 2008-09-19
> **brnetonboy said:**
> When will xserver 1.6 be out? I've been wanting MPX forever...

As far as I read - xserver 1.6 should be out at the end of the year and xserver 1.7 should be out in April 2009 - together with X.Org 7.5. MPX is otherwise already merged into the main trunk of xserver - but I think its release is dependent on Xinput2. If Xinput2 won't be ready before the release of xserver 1.6 - MPX will be disabled. 

Ideally 9.04 Jaunty will have X.Org 7.5 with all the new features - including MPX.

---

### Post by shantanu.nalawade on 2008-09-21
Hey quickee i suppose u are quite familiar with all this.

Would you please help me writing an application for displayin two cursors on the screen.

I'm interested in displaying only two.

Please this project is very important for me.

It would really be helpful.

Thanks.

---

### Post by Quikee on 2008-09-22
> **shantanu.nalawade said:**
> Hey quickee i suppose u are quite familiar with all this.

Would you please help me writing an application for displayin two cursors on the screen.

I'm interested in displaying only two.

Please this project is very important for me.

It would really be helpful.

Thanks.

As I said - this isn't possible without MPX (this is an extension for xserver itself). Even if you were were able to draw a second cursor you would still have the problem with mouse events. Xserver without MPX support sees several mouses as one mouse - which means if you plug 2 mouses and you move both, you will get coordinates from both as one mouse event and no way to distinguish where they came from.

With MPX on the other hand this should be pretty simple because you will get everything you need (n mouses, n cursors).

---

### Post by shantanu.nalawade on 2008-09-22
Ya you've said it earlier.

But is MPX-1.5 available with necessary features?

I'm asking because the project which I'm working on needs to be completed before end of this year.

If you could help me out with it's source code then it would be really great.

---

### Post by skullmunky on 2008-09-26
I think the conclusion is that you will not be able to do it in this time frame.  The new version of X that will allow this won't be out until next year or later.  If you are building an app for single-location deployment, like a kiosk, you can compile your own Xserver that includes the MPX extension.  However if you are trying ship an app to users of common linux distros, they will not be able to run it because their systems won't have the multi-pointer extension yet.

If you can share any more about the app, you might be able to get brainstorms on other appropriate input methods ... 

side note : that is AWESOME that this feature is coming to X, even if just in the near future!!

---

### Post by poopypants on 2008-10-13
my understanding is that if you compile xorg with mpx and (separately?) xinput2 you can then enable multiple mice using xinput2 (today/now, if you can figure out how to do it and there aren't any broken sources). I haven't been able to figure out the xinput2 compile and use yet so I'm stuck myself (I just don't have much experience with xorg yet). Here is a script and info on compiling xorg (with mpx):
[http://www.x.org/wiki/Development/git](http://www.x.org/wiki/Development/git)
[http://wearables.unisa.edu.au/mpx/?q=downloads](http://wearables.unisa.edu.au/mpx/?q=downloads)

xi2 (xinput2):
[http://wearables.unisa.edu.au/mpx/?q=xi2_sample](http://wearables.unisa.edu.au/mpx/?q=xi2_sample)
[http://wearables.unisa.edu.au/mpx/?q=tutorial](http://wearables.unisa.edu.au/mpx/?q=tutorial)

more info:
[http://who-t.blogspot.com/](http://who-t.blogspot.com/)
[http://smspillaz.wordpress.com/2008/10/07/308/](http://smspillaz.wordpress.com/2008/10/07/308/)

---

