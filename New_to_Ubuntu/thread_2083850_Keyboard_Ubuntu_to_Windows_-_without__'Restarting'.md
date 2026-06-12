---
title: "Keyboard Ubuntu to Windows - without  'Restarting' ?"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by BNZBKK on 2012-11-13
Is there a quick 'keyboard change' from Ubuntu to Windows -and back - without  'Restarting' ?


A search failed to provide an answer

---

### Post by Moose on 2012-11-13
Press CTRL+T then type sudo reboot.
 
A fail proof method to switching to windows with your keyboard. Technically it isn't restarting but instead "Rebooting". 
 
 
Your question has been answered.
...Your welcome

---

### Post by squakie on 2012-11-13
We could use a little more detail on exactly what you want.  Do you want to remove a keyboard from a Windows machine and plug it into a running Ubuntu machine?

---

### Post by ibjsb4 on 2012-11-13
It can be done with just a click of the mouse or keyboard

[https://www.virtualbox.org/wiki/Screenshots](https://www.virtualbox.org/wiki/Screenshots)

---

### Post by BNZBKK on 2012-11-13
> **AnarchyTech said:**
> Press CTRL+T then type sudo reboot.
 
A fail proof method to switching to windows with your keyboard. Technically it isn't restarting but instead "Rebooting". 
 
 
Your question has been answered.
...Your welcome



1. CTRL + T is terrific for bringing up a new 'Speed Dial' page.  I'm using an Acer PC.


2. Technically it is "Rebooting" you're correct but if one clicks on the 'Shut Down' button on the drop down you will see Shut Down then 'Restart'. 


3. Presumptuous, as my question has not been answered to satisfaction yet - but a valiant try, as a keyboard solution such as you offered is what I'm after, please don't be discouraged. Ahem


.

---

### Post by BNZBKK on 2012-11-13
> **squakie said:**
> We could use a little more detail on exactly what you want.  Do you want to remove a keyboard from a Windows machine and plug it into a running Ubuntu machine?


Please don't overthink - or underthink - this, a solution such as CTRL+T as previously suggested is what I'm after 

Thank you

---

### Post by BNZBKK on 2012-11-13
> **ibjsb4 said:**
> It can be done with just a click of the mouse or keyboard

[https://www.virtualbox.org/wiki/Screenshots](https://www.virtualbox.org/wiki/Screenshots)



Virtually impossible at this address but thanks for your reply anyway

---

### Post by audiomick on 2012-11-13
> **BNZBKK said:**
> 1. CTRL + T is terrific for bringing up a new 'Speed Dial' page.  I'm using an Acer PC.

I think he meant ctrl+alt+t. That should bring up a terminal, and then you can type in
```
sudo reboot
```

This
```
shutdown -r now
```
will also make it reboot, and this

```
sudo shutdown -P now
```

will make it shutdown and power off.

Look at 
```
man reboot
```
for more details on that command, and
```
man shutdown
```
for details on the shutdown command.

---

### Post by offgridguy on 2012-11-13
audiomick;  This is making more sense now, at least to me.

The url doesn't though, it brings up  Open Linux Forums- Index

---

### Post by audiomick on 2012-11-13
> **offgridguy said:**
> 
The url doesn't though, it brings up  Open Linux Forums- Index

Oh, that isn't part of the post. That is in my signature... ;)

---

### Post by squakie on 2012-11-13
> **BNZBKK said:**
> Please don't overthink - or underthink - this, a solution such as CTRL+T as previously suggested is what I'm after 

Thank you

Couldn't tell from your initial post what you were saying - you wanted a way to switch your keyboard from linux to windows and back.  That can a huge number of possibilities of what you want to do.

From reading what is in the thread now, it isn't a matter of keyboard or windows at all, it's a matter of doing a restart from the keyboard by pressing a single key or a single combination of keys.  If that isn't correct please explain exactly what you want to do.

I've seen mention in some of the replies about virtualbox, yet you don't mention virtualbox.  That's why it would be nice to know:  does this have ANYTHING to do with a virtual machine, and if so, what is the host and what is the guest?  Do you just want to switch between a virtual machine and the host OS?  OR do you just simply want a "quick" way to request ubuntu to reboot?  Where does Windows come in to this (given your initial post)? 

Forgive me for "overthinking", but you just haven't been specific enough to describe exactly what you want to do.  With that, we can perhaps give you THE answer.

---

### Post by BNZBKK on 2012-11-14
> **offgridguy said:**
> audiomick;  This is making more sense now, at least to me.

The url doesn't though, it brings up  Open Linux Forums- Index

> **audiomick said:**
> Oh, that isn't part of the post. That is in my signature... ;)


Heh heh you wacky tech heads

---

### Post by BNZBKK on 2012-11-14
> **audiomick said:**
> I think he meant ctrl+alt+t. That should bring up a terminal, and then you can type in
```
sudo reboot
```

This
```
shutdown -r now
```
will also make it reboot, and this...
 

Yes thank you 'audiomick' you've got the idea but it's just another way to restart into the other OS
 
I may be mistaken but I thought  ...wish there was a **quick** 'key-in' to go back and forth between the two OS's rapidly but probably impossible given the OS 'brain change' and power up required.

But I'm grateful to you all anyway - and keep up the good work


.

---

### Post by BNZBKK on 2012-11-14
> **squakie said:**
> Couldn't tell from your initial post what you were saying - you wanted a way to switch your keyboard from linux to windows and back.  That can a huge number of possibilities of what you want to do.

From reading what is in the thread now, it isn't a matter of keyboard or windows at all, it's a matter of doing a restart from the keyboard by pressing a single key or a single combination of keys.  If that isn't correct please explain exactly what you want to do.

I've seen mention in some of the replies about virtualbox, yet you don't mention virtualbox.  That's why it would be nice to know:  does this have ANYTHING to do with a virtual machine, and if so, what is the host and what is the guest?  Do you just want to switch between a virtual machine and the host OS?  OR do you just simply want a "quick" way to request ubuntu to reboot?  Where does Windows come in to this (given your initial post)? 

Forgive me for "overthinking", but you just haven't been specific enough to describe exactly what you want to do.  With that, we can perhaps give you THE answer.




Hey 'squakie' have a cup of tea and a good lie down ..or a long walk ..seriously

---

### Post by squakie on 2012-11-14
> **BNZBKK said:**
> Hey 'squakie' have a cup of tea and a good lie down ..or a long walk ..seriously

I'm asking a legitimate question based on your opening post.  So, what is it you want to do?  Seems like a SIMPLE question.

---

### Post by squakie on 2012-11-14
> **BNZBKK said:**
> Yes thank you 'audiomick' you've got the idea but it's just another way to restart into the other OS
 
I may be mistaken but I thought  ...wish there was a **quick** 'key-in' to go back and forth between the two OS's rapidly but probably impossible given the OS 'brain change' and power up required.

But I'm grateful to you all anyway - and keep up the good work


.
If you want a magic key to switch between a RUNNING ubuntu and a RUNNING Windows installation, there's no such animal unless you ARE using a virtual machine.  You can't have both OS's running at the same time on the same box without one of them being in a virtual machine.  There is also no way to rapidly switch OS's - you must restart.

That's THE answer.

Wasn't so hard providing that detail to someone ELSE, was it?

---

### Post by newb85 on 2012-11-14
> **squakie said:**
> If you want a magic key to switch between a RUNNING ubuntu and a RUNNING Windows installation, there's no such animal unless you ARE using a virtual machine.  You can't have both OS's running at the same time on the same box without one of them being in a virtual machine.  There is also no way to rapidly switch OS's - you must restart.


+1

Would have provided the same info myself, but thought surely the OP wasn't asking for a keyboard shortcut to switch between independent OSes.  The initial post seemed confusing, and everyone else seemed to be barking up different trees.  

For the record, it is possible to Hibernate one system and then boot into the other.  However, Hibernate functionality has been sketchy enough in the past that it's now disabled by default in Ubuntu.  It wouldn't really be faster, anyways, unless you had a lot of applications open that you didn't want to close.

If you want to quickly switch between OSes, you need to run one on a VM.

---

### Post by squakie on 2012-11-14
> **newb85 said:**
> +1

Would have provided the same info myself, but thought surely the OP wasn't asking for a keyboard shortcut to switch between independent OSes.  The initial post seemed confusing, and everyone else seemed to be barking up different trees.  

For the record, it is possible to Hibernate one system and then boot into the other.  However, Hibernate functionality has been sketchy enough in the past that it's now disabled by default in Ubuntu.  It wouldn't really be faster, anyways, unless you had a lot of applications open that you didn't want to close.

If you want to quickly switch between OSes, you need to run one on a VM.

Yep - finally someone who saw what I was talking about - thanks newb85!!  ;)  As you mention, you can hibernate one, but you still have to do a reboot to get to the other, and apparently the op is looking for a way around that.  But as you mention, hibernate, if you can get it working (I'm lucky on my old Dell Inspiron 1501 - the hibernate actually works!) does provide for a somewhat faster way to get back to where you were.  I'm so glad you saw this thread and posted - I thought maybe I was going nuts or something! ;) ;)

---

### Post by critin on 2012-11-14
> **squakie said:**
> If you want a magic key to switch between a RUNNING ubuntu and a RUNNING Windows installation, there's no such animal unless you ARE using a virtual machine.  You can't have both OS's running at the same time on the same box without one of them being in a virtual machine.  There is also no way to rapidly switch OS's - you must restart.

That's THE answer.

Wasn't so hard providing that detail to someone ELSE, was it?

+1  good job!

---

### Post by wildmanne39 on 2012-11-14
This has been asked and answered so I am closing the thread.
Thanks

---

