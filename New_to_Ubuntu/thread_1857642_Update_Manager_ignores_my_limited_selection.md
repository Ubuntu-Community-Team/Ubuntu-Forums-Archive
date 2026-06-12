---
title: "Update Manager ignores my limited selection"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-10-10
Hi,   I'm travelling with my Natty on a netbook and my connection is via a 3G dongle with a limited Mbyte allocation,  so when Update Manager recently presented me with a menu of some 56MB of updates,  I decided to select only the small urgent updates and leave the heavy ones (Office Productivity Suite and Libre Office updates) till later when I'm on proper broadband again.  

OK,  so I unticked all the Office Productivity Suite and Libre Office  ones,  after which Update Manager said "5 updates selected,  202KB to be downloaded".     So far so good.

But then when I started to download my 202KB's worth of selected updates,  I could see all the original 56MB starting to be downloaded.    Not wishing to use up my dongle's allocation,  I stopped the download when it had reached 6MB.   

I closed Update Manager and Natty,  but the next day the same 56MB update menu was presented to me again,  so I thought I'd give it another try. I unticked all the heavy Office Productivity Suite and Libre Office updates,   leaving the same 202KB to be downloaded as I'd tried the day before.   Exactly the same happened as before,   and I had to stop the download when I saw it had reached 6MB.

How do I make Download Manager obey my selection and only download the updates that I've left ticked?

---

### Post by snowpine on 2011-10-10
I don't know the answer, but here's a tip:

"Installing" an application that is already installed will cause it to update (if updates are available).

So if you want to update Firefox (for example):

```
sudo apt-get update
sudo apt-get install firefox
```

I hope that helps! :)

---

### Post by Lisiano on 2011-10-10
^--- +1
Also if you have synaptic, you can manually check what can be updated and update only what you want.
Another good tip would be to go to a cafe, library, bookstore, airport, wherever and use the free WiFi to download everything.

---

### Post by Sleepy-zz-John on 2011-10-10
> **snowpine said:**
> I don't know the answer, but here's a tip: 
Thanks for the tip, snowpine,  but my problem is that I want to ***exclude*** items on Update manager's menu from being updated as opposed to ordering anything else to be updated.

---

### Post by thatguruguy on 2011-10-10
You can always update from synaptic.

However, update manager should honor your decisions on what to update, and what not to update.  I kept some packages back for months simply by deselecting them when I ran update manager.

---

### Post by Sleepy-zz-John on 2011-10-10
> **Lisiano said:**
> ^--- +1
Also if you have synaptic, you can manually check what can be updated and update only what you want.
Thanks Lisiano,  but I still don't know how to stop Update Manager from spending unnecessary update Mbytes on my limited 3G dongle when they aren't needed urgently. 
I feel as if I'm experiencing a bug or some kind of malfunction here;  surely Update Manager should be taking notice of which items are ticked and which are unticked and adjusting the download program accordingly,  shouldn't it?   
> Another good tip would be to go to a cafe, library, bookstore, airport, wherever and use the free WiFi to download everything.
Yes,  fair enough,  that's what I'm planning to do,  but in the meantime what's the point of having a menu with items that can be unticked if everything's going to be automatically downloaded anyway?   I'm sure I've used this unticking system successfully in the past and done restricted downloading of upodates.   Look to me as if some bug must have crept in just recently.

---

### Post by Lisiano on 2011-10-10
> **Sleepy-zz-John said:**
> Thanks for the tip, snowpine,  but my problem is that I want to ***exclude*** items on Update manager's menu from being updated as opposed to ordering anything else to be updated.

> **snowpine said:**
> I don't know the answer, but here's a tip:

"Installing" an application that is already installed will cause it _to **update** (**if** updates are **available**)_.

So if you want to update Firefox (for example):

```
sudo apt-get update
sudo apt-get install firefox
```

I hope that helps! :)

He meant that you can tell a certain package to update itself, say you notice there is a kernel upgrade, you tell apt-get to "install" the kernel, actually it will update it but if there is no update, it will just tell you that it is already installed.

---

### Post by Sleepy-zz-John on 2011-10-12
> **thatguruguy said:**
> You can always update from synaptic.

However, update manager should honor your decisions on what to update, and what not to update.  I kept some packages back for months simply by deselecting them when I ran update manager.
Thanks for your reply,  but so far nobody seems to have been able to address my basic query about the ticking and unticking system in Update Manager which is being ignored when I start an update download.   

Can anyone suggest how I could make Update Manager honour my deselections?  How can I prevent it downloading everything on the menu instead of limiting itself to those items that I've left ticked?  

This problem only arises when I'm on a 3G dialup connection with a restricted monthly allocation of Mbytes.   When I'm on ordinary broadband,  I normally leave everything on the menu ticked,  but just now when I'm travelling and limited to 3G,  I need to temporarily deselect heavy less urgent updates that are being offered by unticking them.  Although within Update Manager the deselection appears to be working and a reduced total download figure is displayed,  when I start the actual download,  everything,  including my deselected items are still being downloaded.

Hope I'm making myself a bit clearer now :)

---

### Post by Linux_junkie on 2011-10-12
> **Sleepy-zz-John said:**
> Thanks for your reply,  but so far nobody seems to have been able to address my basic query about the ticking and unticking system in Update Manager which is being ignored when I start an update download.   

Can anyone suggest how I could make Update Manager honour my deselections?  How can I prevent it downloading everything on the menu instead of limiting itself to those items that I've left ticked?  

This problem only arises when I'm on a 3G dialup connection with a restricted monthly allocation of Mbytes.   When I'm on ordinary broadband,  I normally leave everything on the menu ticked,  but just now when I'm travelling and limited to 3G,  I need to temporarily deselect heavy less urgent updates that are being offered by unticking them.  Although within Update Manager the deselection appears to be working and a reduced total download figure is displayed,  when I start the actual download,  everything,  including my deselected items are still being downloaded.

Hope I'm making myself a bit clearer now :)

From what you've said it appears to be a bug in update-manager, have you reported it as a bug?

---

### Post by Sleepy-zz-John on 2011-10-12
Thanks Linux_junkie.    Yes,  I agree it does looks like a bug,   but I haven't reported it yet because I was hoping I might find someone else on here with Natty who could confirm they're seeing the same problem.  There's a fair chance it could be a bug,   but it's also possible that it's my system that's suffering from some kind of corruption.   .If another Natty user could try and test if the same thingv happens on their system or not,  that would indicate whether we've got a real bug going here,  or I've got some unique problem peculiar to my system.

---

### Post by thatguruguy on 2011-10-12
> **Sleepy-zz-John said:**
> Thanks for your reply,  but so far nobody seems to have been able to address my basic query about the ticking and unticking system in Update Manager which is being ignored when I start an update download.   

Can anyone suggest how I could make Update Manager honour my deselections?  How can I prevent it downloading everything on the menu instead of limiting itself to those items that I've left ticked?  

This problem only arises when I'm on a 3G dialup connection with a restricted monthly allocation of Mbytes.   When I'm on ordinary broadband,  I normally leave everything on the menu ticked,  but just now when I'm travelling and limited to 3G,  I need to temporarily deselect heavy less urgent updates that are being offered by unticking them.  Although within Update Manager the deselection appears to be working and a reduced total download figure is displayed,  when I start the actual download,  everything,  including my deselected items are still being downloaded.

Hope I'm making myself a bit clearer now :)

... and as I mentioned, I had held back packages for months by unclicking them in Update Manager.  I just now did a test, and was able to unclick packages in Update Manager, and it honored my choices. I'm not sure why it isn't working on your system, but I can't recreate the problem here.

---

### Post by Lisiano on 2011-10-12
I'll setup a VM and test it in it, I'm too up-to-date to test it on my current machine.

---

### Post by Sleepy-zz-John on 2011-10-12
> **thatguruguy said:**
> ... and as I mentioned, I had held back packages for months by unclicking them in Update Manager.  I just now did a test, and was able to unclick packages in Update Manager, and it honored my choices. I'm not sure why it isn't working on your system, but I can't recreate the problem here.
Thanks,  OK,  but just to clarify,  I have also held back packages by unclicking them in the past,  too,  so the problem I'm seeing is something that has changed just recently.    To re-clarify further,  I can still unclick items in Update Manager and I can still see a commensurate reduction appear in the Mbytes that Update Manager says will be downloaded.   For example that figure drops from 55Mb to 800Kb.   The problem only arises after my download actually starts when I find the whole menu of 55Mb originally offered updates is being downloaded instead of the 800Kb I'd selected. 
So I would just like to double-check that in your test,  you did actually proceed to the download stage,  and to verify that only your selected items were downloaded.   In other words,  confirm that your deselected items were ***not*** downloaded.

---

### Post by Lisiano on 2011-10-12
Okay so it is offering me 1003 updates (11.04 dvd, freshly downloaded) totaling 567.0MB, Update Manager is version 1:0.500
I right-clicked and pressed Uncheck All, selected to update Gwibber, GVFS and Update Manager (7 Updates, 2mb). Result: Downloaded only those 7 and installed only them.

Repeating same but with updated version 1:0.500.3
Selecting only apt (2mb).
It proceeded to download and install only apt.

So probably OP has a faulty config somewhere.

---

### Post by Sleepy-zz-John on 2011-10-13
> **Lisiano said:**
> So probably OP has a faulty config somewhere.
Yes,  I have to agree.  Anyway I'm very grateful to you for doing those tests.  without which I wouldn't have known if this problem was me or a reportable bug.    As a matter of fact I have some other ongoing issues with my Natty,  so rather than try to diagnose them or start again with a fresh Natty,  I'm thinking that as soon as I can find some broadband,  I might just take the opportnity and upgrade to Ocelot.   
Thanks again.

---

### Post by Larkspur on 2011-10-13
> **Sleepy-zz-John said:**
> Yes,  I have to agree.  Anyway I'm very grateful to you for doing those tests.  without which I wouldn't have known if this problem was me or a reportable bug.    As a matter of fact I have some other ongoing issues with my Natty,  so rather than try to diagnose them or start again with a fresh Natty,  I'm thinking that as soon as I can find some broadband,  I might just take the opportnity and upgrade to Ocelot.   
Thanks again.


When you deselected the LibreOffice updates, did you also deselect the LibreOffice Python updates?  They are called UNO, I think.  I had the same problem as you, but when I made sure that nothing connected to LibreOffice was selected, it "honored" my choices.  I think that selecting one LO package drags the rest with them.

---

### Post by Lisiano on 2011-10-14
If you tell a package to not install which another update depends on. Say new apt-url depends on the new apt (This is a example so might not be the same as it actually is)
If tick apt-url, it will also tick apt. since it can't install itself if there isn't an updated apt, you don't like that so you untick apt, it also unticks apt-url.

---

