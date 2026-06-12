---
title: "How do you move min, max, close buttons to the right side?"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Melhisedek on 2011-09-05
The old way of ALT+F2 than gconf-editor doesn't work in 11.10

---

### Post by drs305 on 2011-09-05
I don't know what customizations I might have made, but for me the gconf-editor's setting for:
> /apps/metacity/general/button_layout
still moves the buttons to the left/right depending on whether the colon [noparse](:)[/noparse] starts or ends the setting.

---

### Post by Melhisedek on 2011-09-05
Thing is when I type gconf-editor nothing shows up :/

---

### Post by drs305 on 2011-09-05
If you type "which gconf-editor" does it return "/usr/bin/gconf-editor"? If not, you may have to install it.

I've been using gconf-editor and dconf tools, hoping that eventually the dconf editor will be as useful as gconf-editor has been over the years.

---

### Post by Melhisedek on 2011-09-05
Which command didn't return anything so I had to download it :) Thanks mate I would never think of it :)

---

### Post by drs305 on 2011-09-05
If you haven't installed it, dconf-tools provides the 'dconf-editor' app. Either it isn't fully developed yet or I just haven't learned how to use it, but it's another app that will be necessary for tweaking settings going forward.

You might want to leave the thread open for a while to see if others offer more information on the tweak integration in Oneiric, but once you are satisfied please mark the thread SOLVED with the "Thread Tools" link near the top right of the original post.

---

### Post by Melhisedek on 2011-09-05
Will do thanks. Just wish buttons would stay on the right side even when maximized :/ If anyone knows of a way please let me know.
Using Unity ofc

---

### Post by seattle vic on 2011-09-07
For some reason, today my buttons moved back to the left and making the changes I've made before in gconf-editor /apps/metacity/general/button layout have no effect.

---

### Post by jerrylamos on 2011-09-07
For previous Ubuntu's I would select ClearLooks.  
That put the buttons on the right where I expect.

For some reason never stated Ubuntu Development doesn't like ClearLooks.

For some reason never stated Ubuntu Development wants the close/min/max buttons on the left side.

So I use Ocelot the way "they" want it, looking for bugs as a tester.

I frequently use Narwhal, Meerkat, Lynx LTS the way "I" want it.

The "advertising" on Ubuntu still says customizable, but it's getting harder.

Jerry

---

### Post by cariboo on 2011-09-07
Isn't easier to just leave the buttons on the left? One of the complaints when Unity first came out was to much mouse movement. Moving the buttons to the right makes you move the mouse even more.

---

### Post by alexvy13 on 2011-09-07
Just use ubuntu tweak tool

---

### Post by seattle vic on 2011-09-07
I've been used to buttons on the right for probably 30 years and it's hard to change.

I just want to know if this is a recent bug (seems like they were on the right a day ago) or is it just no longer customizable.

---

### Post by seattle vic on 2011-09-08
> **alexvy13 said:**
> Just use ubuntu tweak tool

I just tried it and it has no effect on the button placement.  Right now nothing will either move the buttons or change their order, neither tweak or gconf-edit.

---

### Post by rturner on 2011-09-08
Mine didn't show up on the right until I rebooted.

---

### Post by seattle vic on 2011-09-08
> **rturner said:**
> Mine didn't show up on the right until I rebooted.

Yes, that worked for me also.

---

### Post by JonM33 on 2011-09-08
At first I didn't like them on the left side, I believed that to be too similar to Mac OS X location. But after time, given the way that Ubuntu Unity is on the left side I found it a lot quicker and easier to navigate when the close/min/max buttons on the left. 

Use it that way for a little bit and you will see. You move your mouse shorter distances because of that.

---

### Post by Longinus00 on 2011-09-08
> **JonM33 said:**
> At first I didn't like them on the left side, I believed that to be too similar to Mac OS X location. But after time, given the way that Ubuntu Unity is on the left side I found it a lot quicker and easier to navigate when the close/min/max buttons on the left. 

Use it that way for a little bit and you will see. You move your mouse shorter distances because of that.

Too bad the scroll bars are on the right still. If you scroll a bit and want to close the window you'll be moving the mouse way more. Hopefully they'll move the scrollbar and the resize grabber to the left side as well! Then unity will be perfect.

---

### Post by freedomAboveAll on 2011-09-08
The 'New Wave' Theme moves buttons to the right side in 11.04.

super key >  Appearance

---

### Post by jerrylamos on 2011-09-08
> **alexvy13 said:**
> Just use ubuntu tweak tool

I'll bite, what is the CODE to get the "ubuntu tweak tool" to run?

I tried command line
it said tweak wasn't installed.
sudo apt-get install tweak
... did the install.  try to use it:

jerry@Compaq:~$ tweak
usage: tweak [-f] [-l] [-e] filename
    or tweak -D to write default tweak.rc to stdout

?  

Thanks, Jerry

---

### Post by drs305 on 2011-09-08
@ jerrylamos,

It's *ubuntu-tweak*. I have notes on how to install it in the "Rm_Kernel" link in my signature line.

---

### Post by 3rdalbum on 2011-09-09
> **seattle vic said:**
> I've been used to buttons on the right for probably 30 years and it's hard to change.

Since 1981? The Apple Lisa didn't have window buttons.

Try changing. It took me about five days and now I find I can deal with them on either side without even having to think.

---

### Post by JonM33 on 2011-09-09
> **Longinus00 said:**
> Too bad the scroll bars are on the right still. If you scroll a bit and want to close the window you'll be moving the mouse way more. Hopefully they'll move the scrollbar and the resize grabber to the left side as well! Then unity will be perfect.

I just use my middle mouse scroll. Works without a problem. Haven't used scroll bars in years.

---

### Post by Tekno.Statik on 2011-09-11
Ubuntu Tweak worked for me, every so often something would cause the buttons to go to the left again, in fact I noticed for the past week I've had them on the left. lol I must be getting somewhat used to them, but [Ubuntu Tweak]("http://ubuntu-tweak.com/") works on 10.04.

I just noticed when I went to their website; it specifies that Tweak is for 10.10 and older versions of Ubuntu.

You may have to get used to using purely the mouse scroll for everything, forget about the scroll bar.

But here's something I am following up on adjusting the mouse scroll to have more flexibility: 

[http://ubuntuforums.org/showthread.php?t=1179448&highlight=mouse+scroll]("http://ubuntuforums.org/showthread.php?t=1179448&highlight=mouse+scroll")

You must read the whole first page of comments to see where the conversation goes to Mouse scrolling control for Ubuntu.

---

### Post by VanR on 2011-09-11
May sound silly to some, but buttons on the left are a deal breaker for me. Got to have them on the right or I'll use another distro.

---

### Post by markseshop on 2011-09-11
Cant they just have a easy way to move them back this is total BS 
this is something ms would pull I love Ubuntu but my love is fading with this BS

---

### Post by Zeta-K on 2011-09-11
> **JonM33 said:**
> At first I didn't like them on the left side, I believed that to be too similar to Mac OS X location. But after time, given the way that Ubuntu Unity is on the left side I found it a lot quicker and easier to navigate when the close/min/max buttons on the left. 

Use it that way for a little bit and you will see. You move your mouse shorter distances because of that.

Every time I try to close a program, I open the unity bar!!!

---

### Post by Tekno.Statik on 2011-09-11
I recommend going back to 10.10 and using Ubuntu Tweak, it worked solid for me and it was easy to set up on the Windows options as displayed below:

[IMG]https://lh4.googleusercontent.com/-09MDXFXDNxI/Tm1ThT85YtI/AAAAAAAACaI/ENed5ptd9VY/s800/Screenshot.png[/IMG]

What's so good about the later versions? 10.04 is far more reliable in my opinion.

---

### Post by cariboo on 2011-09-11
> **Tekno.Statik said:**
> I recommend going back to 10.10 and using Ubuntu Tweak, it worked solid for me and it was easy to set up on the Windows options as displayed below:

<snip> image removed

What's so good about the later versions? 10.04 is far more reliable in my opinion.

Wait a couple of weeks after 12.04 is released, and it should be just as stable (as stable as ubuntu releases get) as 10.04 is.

---

