---
title: "Unity launcher is not showing any installed apps"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by soumoks on 2012-05-19
The unity launcher is not showing any installed apps,how do i launch apps now?,the home lens is not showing any apps,the applications lens does not seem to be working,what do i do?ubuntu sw centre also does not work,i recently changed the server location ,it was India initially,i changed it to the best server available,is that the problem?pls help me!!!

---

### Post by zombifier25 on 2012-05-19
Try launching the Dash and search (type the name) for the apps you want. The Launcher does not show installed apps, it shows apps you have locked in there.

---

### Post by soumoks on 2012-05-19
> **zombifier25 said:**
> Try launching the Dash and search (type the name) for the apps you want. The Launcher does not show installed apps, it shows apps you have locked in there.

tried that,it just doesn't show anything

---

### Post by Utkarsh Ray on 2012-05-19
> **zombifier25 said:**
> Try launching the Dash and search (type the name) for the apps you want. The Launcher does not show installed apps, it shows apps you have locked in there.

launch the dash, and look at the bottom of it.
There will be a home icon (which should be highlighted)
Select the icon next to it (looks like a comb, pen, brush), it is between home and a document icon.
The attachment will make it clear.

---

### Post by soumoks on 2012-05-19
> **Utkarsh Ray said:**
> launch the dash, and look at the bottom of it.
There will be a home icon (which should be highlighted)
Select the icon next to it (looks like a comb, pen, brush), it is between home and a document icon.
The attachment will make it clear.

i know what the lenses look like bro,but they are just not showing anything,i have been using unity from 11.10,this kind of thing never happened to me..even if i type the name of an app which i have installed,it shows no results found,what do i do?

---

### Post by wilee-nilee on 2012-05-19
Unity can be reset, I have had to do this myself hit crtl-f2 then type in unity --reset then hit enter.

---

### Post by soumoks on 2012-05-19
> **wilee-nilee said:**
> Unity can be reset, I have had to do this myself hit crtl-f2 then type in unity --reset then hit enter.

Ok will try this and report back,thanks:)

---

### Post by soumoks on 2012-05-20
> **wilee-nilee said:**
> Unity can be reset, I have had to do this myself hit crtl-f2 then type in unity --reset then hit enter.

sorry with my late reply,but this does not seem to be working,am i supposed to reboot after doing this?,i pressed ctrl+f2,but nothing happened,so i just typed unity --reset and it came up at the bottom of the screen,then i pressed enter,but nothin seems to be happening..:(,any other solutions?

---

### Post by Utkarsh Ray on 2012-05-21
> **soumoks said:**
> i know what the lenses look like bro,but they are just not showing anything,i have been using unity from 11.10,this kind of thing never happened to me..even if i type the name of an app which i have installed,it shows no results found,what do i do?

I misunderstood the problem.

> **wilee-nilee said:**
> Unity can be reset, I have had to do this  myself hit crtl-f2 then type in unity --reset then hit enter.

That's Alt+F2
Long-press Super (Windows) key for keyboard shortcuts.

---

### Post by wilee-nilee on 2012-05-21
> **Utkarsh Ray said:**
> I misunderstood the problem.



That's Alt+F2
Long-press Super (Windows) key for keyboard shortcuts.

alt-f2 is a command shell, the super key is the dash search, looks quite similar.

---

### Post by wilee-nilee on 2012-05-21
> **soumoks said:**
> sorry with my late reply,but this does not seem to be working,am i supposed to reboot after doing this?,i pressed ctrl+f2,but nothing happened,so i just typed unity --reset and it came up at the bottom of the screen,then i pressed enter,but nothin seems to be happening..:(,any other solutions?

Try it in a terminal it should restart the unity desktop.

---

### Post by soumoks on 2012-05-21
> **wilee-nilee said:**
> Try it in a terminal it should restart the unity desktop.

ok will try,am actually outside from the last two days,so not able to try these,will post back as soon as possible,and thank u all..:)

---

### Post by ravisghosh on 2012-05-21
> **soumoks said:**
> The unity launcher is not showing any installed apps,how do i launch apps now?,the home lens is not showing any apps,the applications lens does not seem to be working,what do i do?ubuntu sw centre also does not work,i recently changed the server location ,it was India initially,i changed it to the best server available,is that the problem?pls help me!!!

For me, some installed apps are not showing up such as GIMP.

In another case, icons of some apps such as Picasa via wine are showing up but they simply don't start the said application.

Also, some uninstalled apps still show in unity menu.

---

### Post by soumoks on 2012-05-23
ok guys tried everything mentioned above,i pressed alt+f2 and typed in unity --reset but nothin seemed to happen,then uninstalled and reinstalled the unity shell package using synaptic package manager but that also didn't work,currently am using gnome classic,what else can i do..:p,pls help me fix my unity,thanks again for the support.

---

### Post by goaliedude3919 on 2012-05-23
Have you tried just restarting your computer? Sometimes something gets messed up and restarating can let it reset. I had a similar problem once where searching the dash wouldn't find any apps, just files. I restarted my computer and it was working again.

---

### Post by soumoks on 2012-05-23
> **goaliedude3919 said:**
> Have you tried just restarting your computer? Sometimes something gets messed up and restarating can let it reset. I had a similar problem once where searching the dash wouldn't find any apps, just files. I restarted my computer and it was working again.

Its not a matter of restarting as i have done that a dozen of times since this happened,now currently am using gnome classic..

---

### Post by nic777 on 2012-05-25
I had the same issue this morning - applications would not show up in the Home lens when searching and applications lens would not show anything either.

From synaptic (run it from terminal) I completely removed the package unity-lens-applications and then re-installed it. I reset unity (as above) and rebooted and it started working again.

Bit concerning on why it happened. I can say that I had to do a hard reset last night because PC crashed so perhaps the config file for this lens got corrupt.

OP, please try the above and let us know if it works?

---

### Post by raja.genupula on 2012-05-25
hey have you gone through this ??[http://askubuntu.com/questions/125843/dash-search-gives-no-result](http://askubuntu.com/questions/125843/dash-search-gives-no-result)

---

### Post by soumoks on 2012-05-25
ok guys,i just tried about everything to make my application lens work again,but it doesn't seem to work no matter what i do,ok here is list of what all i did:
1.reinstalled unity application lens form synaptic
2.reset unity from terminal
3.i found one of these replies in the above mentioned link and ran this command```
rm -rf ~/.local/share/zeitgeist
```
nothin seems to work..

don't know what else to do..

---

### Post by soumoks on 2012-05-29
did a fresh install as nothin worked:(

---

