---
title: "Preferred applications in 12.04?"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by linux12 on 2012-05-27
I was looking at the community documentation on how to adjust the preferred mail application, and it said it would be under "personal". But it is not there, there is only 6 settings under personal and none of them are preferred applications. This leads me to believe that the process for changing preferred applications has change with the new Unity interface. So... how do I change the preferred apps in Ubuntu 12.04?

---

### Post by TheMTtakeover on 2012-05-27
system settings-details-default applications

---

### Post by linux12 on 2012-05-27
> **TheMTtakeover said:**
> system settings-details-default applications

 That did the trick.:guitar:

---

### Post by mfdc1969 on 2012-06-03
Thank you. It may seem so obvious but with the demise of gnome and the push of Unity these simple things can seem so daunting!

M.

---

### Post by linuxnutjob on 2012-08-25
What about adding an app to the preferred lists that is not already in the list?  How would someone go about doing that?

---

### Post by RodGer GR on 2012-09-03
Another minor problem is that there is no way to set preferred terminal application (I wanted to set terminator as default). In lucid there was a choice for the terminal app.

Anyway. You can always find a workaround  and so did I:
I just disabled the default terminal keyboard shortcut and created another with the same keys (Alt+Ctrl+T) for Terminator.

---

### Post by apollothethird on 2012-09-08
> **TheMTtakeover said:**
> system settings-details-default applications

> **linux12 said:**
> That did the trick.:guitar:

> **mfdc1969 said:**
> Thank you. It may seem so obvious but with the demise of gnome and the push of Unity these simple things can seem so daunting!

M.

Actually it's not obvious to me.  I can't find it.  Where is the "system" menu?  Clicking on Dash home gives me a filter option but I can't find out how to followup with the "steeings-details-default applications option.

I see a number places showing how to get to this place, but not of them work in my default 12.04 installation.

The first I tried was:

[https://help.ubuntu.com/community/OperaBrowser#Setting_Opera_as_default_browser_in_GNOME](https://help.ubuntu.com/community/OperaBrowser#Setting_Opera_as_default_browser_in_GNOME)

(Go to System -> Preferences -> Preferred Applications)  But I can't find it there either.

Thanks in advance if someone will give a clear set of steps of how to get the the Preferred Applications under a default installation of Ubuntu 12.04.

If I find a method I'll come back and bring it to the community for others that are stuck in this matter.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by jimberry on 2012-09-19
[QUOTE=apollothethird;12226892]Actually it's not obvious to me.  I can't find it.  Where is the "system" menu?  ... ... ... ... if someone will give a clear set of steps of how to get the the Preferred Applications under a default installation of Ubuntu 12.04.

It wasn't obvious to me either, but I was eventually able to check the default browser setting by right-clicking a html file and selecting "Properties". On the "Open with" tab there is an option to change the current default program.

---

### Post by apollothethird on 2012-09-19
> **jimberry said:**
> [QUOTE=apollothethird;12226892]Actually it's not obvious to me.  I can't find it.  Where is the "system" menu?  ... ... ... ... if someone will give a clear set of steps of how to get the the Preferred Applications under a default installation of Ubuntu 12.04.

It wasn't obvious to me either, but I was eventually able to check the default browser setting by right-clicking a html file and selecting "Properties". On the "Open with" tab there is an option to change the current default program.

Thanks, Jimberry.  I'm surprised I didn't think of that.  I have used it many times for other file extensions.  This worked great!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by jimberry on 2012-09-19
And I have now discovered the answer to the original question :D.

It seems the "Default Applications" has been moved a little deeper into the hierarchy.

Try
System Settings>System>Details>Default Applications

instead of 
system settings-details-default applications

---

### Post by dbyrd on 2012-09-19
To access "system settings-details-default applications" in Unity.

Load the dash, type "sys". Select "System Settings". A new list of icons will appear. Click the "Details" icon, then select "Default Applications" in the list box on the left side of the form.

---

### Post by apollothethird on 2012-09-19
> **dbyrd said:**
> To access "system settings-details-default applications" in Unity.

Load the dash, type "sys". Select "System Settings". A new list of icons will appear. Click the "Details" icon, then select "Default Applications" in the list box on the left side of the form.

I had read somewhere about typing a string into the dash.  I had been trying to recall what it was so that I could come back to share it here.  However I couldn't remember.

Since you know it's "sys"/"System Settings" it appears to be easy.  But when you don't know for sure where to start it's very complicated and confusing.  When I was trying to recall so that I could come back and share that, I was typing other variations such as default, preferred applications and other combinations.  I don't recall exactly what I had been typing, but I wasn't finding it.

Now since I know what to look for "details" is coming up promptly.  I believe that might be, because the system is remembering where I had went before.

Anyway, having to type things in to search for it rather than a seamless menu to navigate is making it harder and harder for a novice.  I hope they don't drop the pointer/dropdown altogether... but then again, making it complicated will keep IT professional such as myself employed when the Freee OS becomes more popular.

I guess people are going to have to apply money somewhere.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Servoguy on 2013-08-09
System Settings is always available from the drop down menu that appears when you click on the round spikey power button looking thingy in the top right corner of the screen. When I installed 12.04 I'm pretty sure it was also locked to the launcher by default.

---

