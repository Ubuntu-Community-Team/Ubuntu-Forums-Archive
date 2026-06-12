---
title: "how do you name workspaces?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by al.adab on 2008-06-11
hello,

in Gutsy I named workspaces by right-clicking on *workspace switcher* (sitting on my deskbar), choosing "preferences", and using the window corresponding to the *gutsy.png* here attached. 

now on Hardy 8.04, if I right-click on workspace switcher>preferences, I get what you see on the *hardy.png* also attached. 

I'd like to be able to name workspaces. What shall I do?

thanks.

---

### Post by drascus on 2008-06-11
right click the workspaces area and choose preferences. click on a workspace name (this will highlight the line) then click on the name again (this will highlight only the word) then press the backspace button which will delete the word and type your own name. that should do it.

---

### Post by al.adab on 2008-06-11
drascus, that's what I used to do on Gutsy. Now, on Hardy, when I click on preferences I get the window whose screenshot I attached: no option (unless I can't see it) to give each workspace a name.

---

### Post by forestpixie on 2008-06-11
It's a bit odd - I have the normal preferences for the workplace switcher. Have you tried to remove the switcher and to replace it with a new one?

---

### Post by al.adab on 2008-06-11
it is, isn't it. I did try to replace it, but nothing changes. Mystery.

---

### Post by forestpixie on 2008-06-11
Can't find anything about it either - I would make a guess that there is something you can change in gconf-editor, but that's all it is.


Edit - you can do it in gconf-editor. ALt+F2 and run gconf-editor

navigate to apps/metacity/workspace_names

In the right panel you will see your existing names - double click and change to suit.

At least you can do what you want - but why the preferences won't work I have no idea - but I did learn something today.

---

### Post by drascus on 2008-06-11
I am also using hardy and I tried it before I replied to your response. It has been working for me so I am a bit confused as to why it wouldn't work for you.

---

### Post by saj0577 on 2008-06-11
In hardy I can only do columns and rows not names :S

Saj

---

### Post by forestpixie on 2008-06-11
Curiooser and curiouser then, I like drascus don't have that problem, still now we know another way to achieve the same end. 

Would like to know why though.

---

### Post by saj0577 on 2008-06-11
Very strange!

Workspace Switcher 2.22.2


what version do you have forestpixie.

Saj

---

### Post by forestpixie on 2008-06-11
Same - 2.22.2 and it's working in the virtual I have ready for intrepid as well.

---

### Post by al.adab on 2008-06-11
Tried the gconf-editor: I inserted names (at name_1 and name_2) but they don't appear on the switcher in the desktop bar. I went back to gconf-editor and the name I inserted are there. I don't know how to verify what version of switcher I have - anyway, it's the one I got with 8.04. Please get back to me on this if you've got a solution. Thanks.

---

### Post by forestpixie on 2008-06-11
To find out the version you have, I expect it to be the same though, right click the switcher and then About.

If you get nowhere might be worth reporting it as a bug. I had a look at launchpad but I can't see a similar one there.

If in the meantime I find a solution I will post it here.

---

### Post by al.adab on 2008-06-11
thanks forestpixie. I'll report it as a bug.

---

### Post by forestpixie on 2008-06-11
Yea - ccould you put any answer you get here I'd be interested in the outcome. Sorry I couldn't help.

---

### Post by al.adab on 2008-06-11
I was about to report it as a bug when I came across this
[https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152)

That's the issue: Appearance Preferences>Visual Effects>None. Now I can name my workspaces :)

I don't know/understand if setting the Visual Effects to "none" is going to affect what I do with the computer in any way. I don't deal with graphics or play video games, if that's relevant :) I do watch DVDs and use GIMP quite a lot, but the rest is pretty much word.docs and internet. 

Anyway, from [https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/129152) I couldn't understand if I can have both effects and workspace switcher...

---

### Post by Golem XIV on 2008-06-11
It's a Compiz problem.  See [this thread]("http://ubuntuforums.org/showthread.php?t=567344") for reference.

The workaround would be to turn off Compiz, change the workspace names and then turn Compiz on again (through System -> Preferences -> Appearance).  The changes should "stick".

---

### Post by forestpixie on 2008-06-11
Excellent - glad you found it. As far as having it set to none - it just means you don't have any eye-candy, I have mine set like that anyway now - all the cube stuff is good for a while :)

It might be worth reporting your error as the last was Novemeber last year on Gutsy , there's no mention of it still being a problem in Hardy, up to you.

Glad you're sorted.

---

### Post by al.adab on 2008-06-11
I'm afraid it doesn't stick. Tried three times. The workspaces' names disappear the moment I click on "Normal. Provide improved usability, etc".

---

### Post by al.adab on 2008-06-12
Bug reported at 
[https://bugs.launchpad.net/ubuntu/+bug/239231](https://bugs.launchpad.net/ubuntu/+bug/239231)
thanks everyone for trying to help.

---

### Post by AmpersUK on 2010-01-15
> **forestpixie said:**
> Can't find anything about it either - I would make a guess that there is something you can change in gconf-editor, but that's all it is.


Edit - you can do it in gconf-editor. ALt+F2 and run gconf-editor

navigate to apps/metacity/workspace_names

In the right panel you will see your existing names - double click and change to suit.

At least you can do what you want - but why the preferences won't work I have no idea - but I did learn something today.

I am working in 9.10 and when I first loaded up, I could name my workspaces.

Then all of a sudden they disappeared and all I get is "Current workspace is 'Workspace 1"' when I hover over the first workspace.

I went into the Configuration Editor and all the names I originally used are still there.

This happened once before and, as now, I gave up as I can remember where to open the programs.

I just put it down to bad software. I can live with it.

---

### Post by cscat on 2010-03-29
> **al.adab said:**
> I'm afraid it doesn't stick. Tried three times. The workspaces' names disappear the moment I click on "Normal. Provide improved usability, etc".
Thanks al.adab. Solved!

---

### Post by ragav31 on 2010-09-12
Hi,

I am using ubuntu 10.10 (beta).
I want to set name for workspaces i am unable to do it via 

1) ```
Right click on workspaces->Preferences->Workspaces switcher opens & shows workspaces columns and rows.
```

I am using ubuntu 9.10 in another system and as per step 1) i was able to do it.

2) ```
As per forestpixie (June 11th, 2008), 
Alt+F2->gconf-editor->apps/metacity/workspace_names
I can see workspace names as name_1 till name_16
when i double click on name_1 it opens a window with Edit a key.
Name: 
Type: 
Value:
Name and type are disabled. I can enter only value:
 
```

How do i get the options in preferences or via gconf-editor?

Any ideas? ):P

---

### Post by Elfy on 2010-09-12
Have you tried the instructions?

Could be that there's a bug in maverick - it's only beta at the moment.

Try a thread in the maverick forum - [http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by tropo on 2011-02-27
About to (change the) name workspaces: Ubuntu 10.10. This is an easy way to do it:
Clicks in: System/ preference/appearance/ visual effects/ select "none".  
Now you can right click in the workspace/preference and you can change  the names: double click in the name to change. (you can select in  "show  workspace name in switcher)

Para cambiar los nombres de los sitios de trabajo: Ubuntu 10.10. Este es un modo facil de hacerlo:
Presione: System/preferencias/apariencia/efectos visuales/ seleccione "ninguno"
Ahora con clic del botón derecho sobre los espacios de trabajo/  preferencia puede cambiar los nombre: presione doble clic en el nombre a  cambiar (puede seleccionar "muestre los nombres en el cambiador)

---

