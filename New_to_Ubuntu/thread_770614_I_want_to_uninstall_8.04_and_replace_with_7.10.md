---
title: "I want to uninstall 8.04 and replace with 7.10"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by NOLU on 2008-04-27
I had everything working well on 7.10 but 8.04 has been a nightmare. I've asked questions about my problems and haven't had much in response so the easy option for me is yo go back to 7.10.

In simple terms, how do I remove 8.04? I'll use the space left for 7.10 or may even make the space larger for 7.10

Thanks.

---

### Post by dokdoom on 2008-04-27
In my opinion your best bet would just be to just reinstall. What problems were you having if you don't mind me asking?

---

### Post by Michael.Godawski on 2008-04-27
I would do a clean reinstall. Perhaps with a separate home partition.
(I also stick with gutsy because hardy is killing my wlan)

---

### Post by NOLU on 2008-04-27
Well before I had effects on and all was well. No issues at all. Now with 8.04, even with all the effects switched off, every thing is slow from the internet, to folders opening and sometimes freezing. 

I've checked to see if anything is running and besides Firefox at the time, not much else is running so I don't know why it's all very slow.

I've read that some have had no problems and others have had this slow problem but I haven't seen why this could be.

When you say reinstall, would I not have to remove 8.04 first or would it just delete automatically when installing  7.10?

---

### Post by dokdoom on 2008-04-27
Reinstalling will wipe everything so don't worry about having to delete anything form gutsy. Unless there is some issue specific to your particular machine. All of the problems you posted sound like driver issues. I only know how to check if rendering works by using

glxinfo |grep ren

You have to install (or I did at least) mesa-utils in order to run that command. But honestly all of your problems sound like video issues. If you don't feel like trying and going right back to gutsy that's to bad. But I know how it is to have certain issues and not finding any results by using google. 

If you do want to try to run that command, reply and let me know if rendering is working. If it isn't then you are most likely using the wrong driver. Of course there may be other issues involved and maybe even a reinstall of hardy might fix them.

---

### Post by NOLU on 2008-04-27
I'll certainly give it a go. Let me just get out of Vista and pop back.

---

### Post by coool on 2008-04-27
Sad to hear you are having problems with hardy.
You dont have to uninstall 8.04.Just insert the live cd of 7.10 and install it over the existing root partition (root will be formatted). If you have any important files, you can put them into the home directory (assuming you have a separate home partition). You dont have to format the home partition when reinstalling 7.10.

---

### Post by NOLU on 2008-04-27
> **dokdoom said:**
> Reinstalling will wipe everything so don't worry about having to delete anything form gutsy. Unless there is some issue specific to your particular machine. All of the problems you posted sound like driver issues. I only know how to check if rendering works by using

glxinfo |grep ren

You have to install (or I did at least) mesa-utils in order to run that command. But honestly all of your problems sound like video issues. If you don't feel like trying and going right back to gutsy that's to bad. But I know how it is to have certain issues and not finding any results by using google. 

If you do want to try to run that command, reply and let me know if rendering is working. If it isn't then you are most likely using the wrong driver. Of course there may be other issues involved and maybe even a reinstall of hardy might fix them.

I typed the command in terminal and got this:

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
OpenGL renderer string: Mesa GLX Indirect

---

### Post by NOLU on 2008-04-27
> **coool said:**
> Sad to hear you are having problems with hardy.
You dont have to uninstall 8.04.Just insert the live cd of 7.10 and install it over the existing root partition (root will be formatted). If you have any important files, you can put them into the home directory (assuming you have a separate home partition). You dont have to format the home partition when reinstalling 7.10.

If all fails then I will just re-install. I've saved all my important stuff on the External HD :)

---

### Post by dokdoom on 2008-04-27
that's good news actually, we now know what might be the problem.

run 

lspci |grep VGA 

to find out which video card you are using. Let me know and I can most likely tell you which driver you need.

Also in your /etc/X11/xorg.conf look for the "Device" section and tell me what this line looks like.

"Device"      blah video card
"Driver"      <??????>

---

### Post by NOLU on 2008-04-27
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)

That last line, where would I find that file?

Thanks for the help :)

---

### Post by NOLU on 2008-04-27
I found it :D

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"

---

### Post by dokdoom on 2008-04-27
Unfortunatley I am not very familiar with ATI cards, but if  you were to google that card like:

card name ubuntu rendering

I would like to think you would find some solutions and documentation. Also now that everyone knows what your problem is, and what card you are using you should be able to get some better help than I could provide. Good luck, and don't get frustrated.

---

### Post by dokdoom on 2008-04-27
Unfortunately I am not very familiar with ATI cards, but if  you were to google that card like:

card name ubuntu rendering

I would like to think you would find some solutions and documentation. Also now that everyone knows what your problem is, and what card you are using you should be able to get some better help than I could provide. Good luck, and don't get frustrated.

---

### Post by NOLU on 2008-04-27
No problem. Thanks for getting me this far anyway. I'll see if I can sort this out first.

Thanks.

---

### Post by bobafifi on 2008-04-27
I switched back to 7.10 -- too many issues with 8.04 (weird screen resolution and font colors, monitor flickering, Firefox frequently crashing, video plugins not working -- yikes).  I'll try again in a few months.

---

### Post by Pirschjaeger on 2008-04-28
I have all the same problems as bobafifi. 

It's a bit disappointing after all the hype. My fault though. I've been using puters long enough to know what fresh software is all about. 

I'm just one of many white mice.

Curious though; why 8.04 and not just continue tweaking and perfecting 7.10? It's almost there.

---

