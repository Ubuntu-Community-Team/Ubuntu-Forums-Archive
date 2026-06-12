---
title: "Cube with Compiz has issues on Ubuntu 12.04"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by desposti on 2012-06-04
Hello
I own a HP envy 17  and recently installed Ubuntu 12.04 in a small partition just for testing. My main OS so far is Ubuntu 11.04.
Ubuntu 12.04 is fine and I quickly solved a small wifi problem that was very slow. 
Still Cube with compiz has one annoying issue: When I use gnome the  fallback mode and  I switch desktop by clicking one of the desktops cube basically the rotation happens ok BUT in the new desktop there is an annoying quick flash of the applications opened on the previous desktop and if you click back you have another flash of the backaground image on the other desktop. if no programs are opened and desktops are empty switching desktops is smooth but whenever there is something on screen we have the annoying quick flash of the images of other desktops and disappearing very quickly. I hope you guy understand. It's just an annoying graphic problem that I do not have on Ubuntu 11.04.

---

### Post by Face-Ache on 2012-06-04
I'm interested in this too, as i have the same issue. I recently upgraded to 12.04 from 11.10, and i think i recall it also happening in 11.10.

---

### Post by desposti on 2012-06-04
> **Face-Ache said:**
> I'm interested in this too, as i have the same issue. I recently upgraded to 12.04 from 11.10, and i think i recall it also happening in 11.10.

Yes it also happened with 11.10 , that's why I was still using 11.04.

---

### Post by O2Blevel on 2012-06-04
There is a patch for that bug released a few days ago, but you have to apply to the source and recompile. Or else you can wait for 12.10 which is what I'm doing. I can't seem to find any of the links I had for it but google will get you there.

---

### Post by VE6EFR on 2012-06-04
Happening for me as well with a fresh install of 12.04 LTS. Looking forward to the fix in the next update.

---

### Post by stinkeye on 2012-06-04
This bug started in 11.10 when they implemented the compiz Unity plugin and
I don't think this will be fixed 'til 12.10.
There is a testing ppa for compiz
[**_[COLOR="DarkRed"]https://launchpad.net/~vanvugt/+archive/compiz-preproposed[/COLOR]_**]("https://launchpad.net/~vanvugt/+archive/compiz-preproposed") 
I wouldn't recommend it though.
It fixes the flicker but brings in other bugs.
Unfocused windows turn white and the windows become jerky when moving like in 11.10.
See this [**_[COLOR="DarkRed"]BUG[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430")

---

### Post by nll on 2012-06-04
Those bugs with the compiz-proposed ppa only happen for Nvidia cards. For Intel and AMD it's working great. If someone doesn't have an Nvidia GPU there's no problem in using it.

---

### Post by Face-Ache on 2012-06-04
I'm running a Radeon HD5450 graphics card - will that fix work okay with this card?

Have to admit, i'm a bit torn; try to fix something that isn't really a major issue and run the risk of messing something else up? Or wait for it to be fixed in 12.10?

Hmmmmmm.

---

### Post by nll on 2012-06-04
I got an Intel GM965, and everything's great. No one has reported any issue with Radeon cards until this moment, so I think it's worth trying. You can always downgrade if something goes bad.

---

### Post by Face-Ache on 2012-06-04
I think i'll give it a try, see how it goes.

---

### Post by Face-Ache on 2012-06-04
Yep, that's worked a treat - thanks stinkeye and nll  :)

Been doing some thorough testing, before and after, and everything seems to be working fine. It's funny, i never realised how annoying that 'quick flash' thing was when switching desktops via the cube until it was actually gone.

desposti, if you're not running an Nvidia card, this might also work for you. 

I'm pleased it worked for me, as i really have no idea how to reverse it if it *didn't* work. I'd have been relying on you guys to help me with that! (stinkeye, i see you've been getting a few mentions in Full Circle magazine .... you're famous bro!).

---

### Post by nll on 2012-06-04
Not at all! Cheers!

---

### Post by desposti on 2012-06-05
Thank you Stinkeye and Nll. I have an HP Envy 17 without Nvidia , I added the PPA and is working fine now. I am glad I opened this Thread!!

---

### Post by stinkeye on 2012-06-05
> **desposti said:**
> Thank you Stinkeye and Nll. I have an HP Envy 17 without Nvidia , I added the PPA and is working fine now. I am glad I opened this Thread!!

No probs. Alas, I have an Nvidia card. :(

P.S If you need to to go back to the official ubuntu compiz packages
install **ppa-purge** and run...
```
sudo ppa-purge ppa:vanvugt/compiz-preproposed
```

---

### Post by desposti on 2012-06-05
Thanks again. By the way...all good now BUT : when I try to move one window to another desktop it does not work any more, basically it goes round like usual but then the windows cannot stay on the target desktop and just goes back.  So we have the cube effect but cannot move windows.

---

### Post by tekkisan on 2012-06-05
I noticed that it is hard to move windows. It can be done, but you have to move it right over. However I have a bigger concern. My cube does not always work, along with the multiple workspace view and multiple windows view. When I boot into 12.04 either these features work or they don't. If they don't work I usually just re-boot right away. It seems that every second boot would have the cube and multiple views working properly. However today, I rebooted 4 or 5 times and could not get the cube to work.
Actually, the cube does work with the keyboard shortcut. I have the the cube set to rotate with the mouse at the top middle (on the panel) and use the left or right mouse button (1 or 3). This does not work all time.

---

### Post by nll on 2012-06-05
If you are still experiencing problems after adding the compiz-proposed ppa, check [this bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430") and, if it's not being discussed there,  file a new bug adding to the title "[0.9.8 r3110 regression]" and mentioning in the description that you're using a PPA that contains the fix for bug 862430, along with which graphics driver you're using.

---

### Post by desposti on 2012-06-06
Yes thanks. I think I will file a bug. Cube works perfectly but cannot move windows from one workspace to another. Thank you

---

### Post by thefumigator on 2012-06-17
> **desposti said:**
> Yes thanks. I think I will file a bug. Cube works perfectly but cannot move windows from one workspace to another. Thank you

I have the same problem but I fixed it by disabling "lazy positioning" in CCSM, windows management, move windows.

Still have the flashing problem. Actually its a windows appearing and dissappearing very quickly. Think I'm going to try the PPA but there's no guide on how to apply it?

---

### Post by stinkeye on 2012-06-17
> **thefumigator said:**
> I have the same problem but I fixed it by disabling "lazy positioning" in CCSM, windows management, move windows.

Still have the flashing problem. Actually its a windows appearing and dissappearing very quickly. Think I'm going to try the PPA but there's no guide on how to apply it?
Add the ppa...
```
sudo add-apt-repository ppa:vanvugt/compiz-preproposed
```

Update available packages...
```
sudo apt-get update
```

Update manger may open now with updated packages where you can upgrade compiz to the  ppa:vanvugt/compiz-preproposed packages or 
run
```
sudo apt-get upgrade
```

---

### Post by thefumigator on 2012-06-17
> **stinkeye said:**
> Add the ppa...
```
sudo add-apt-repository ppa:vanvugt/compiz-preproposed
```Update available packages...
```
sudo apt-get update
```Update manger may open now with updated packages where you can upgrade compiz to the  ppa:vanvugt/compiz-preproposed packages or 
run
```
sudo apt-get upgrade
```

Thank you! it just worked. There are some minor problems but for the most of it, it works as I needed it to. Thank you again

---

### Post by stinkeye on 2012-06-17
> **thefumigator said:**
> Thank you! it just worked. There are some minor problems but for the most of it, it works as I needed it to. Thank you again
No problem.
If you find you want to revert to the official 12.04 compiz packages see post  [**_[COLOR="DarkRed"]#14[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12000563&postcount=14")

---

### Post by Face-Ache on 2012-08-30
This 'quick flash' bug just started up again for me, any ideas?

---

### Post by stinkeye on 2012-08-30
> **Face-Ache said:**
> This 'quick flash' bug just started up again for me, any ideas?
Compiz has probably been upgraded and you are not using the compiz-preproposed ppa version anymore.
There is a fix described [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12204928&postcount=15") to reinstall the compiz-preproposed ppa version
and pin the compiz packages.

---

### Post by Face-Ache on 2012-08-30
Thanks Stinkeye; that's sorted it out.

There were no compiz packages that had a (!) next to them in Synaptic, so i just selected all of them and locked them. Do you see any issues with doing that?

---

### Post by O2Blevel on 2012-08-30
> **stinkeye said:**
> Compiz has probably been upgraded and you are not using the compiz-preproposed ppa version anymore.
There is a fix described [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12204928&postcount=15") to reinstall the compiz-preproposed ppa version
and pin the compiz packages.

That worked great. Thanks!!!

---

### Post by pqwoerituytrueiwoq on 2012-08-31
awesome this works, so much easer than downgrading to compiz 0.8.4
i should point out running this will prevent a command line upgrade with apt-get from messing this fix up
```
echo "compiz hold" | sudo dpkg --set-selections
```if you are using mint you may have to change maya to precise in gtk-software-sources
edit:
mouse still looses position when dragging across desktops, unchecking lazy positioning in sscm under move helps but it is not perfect

---

### Post by ozviking on 2012-08-31
> **nll said:**
> Those bugs with the compiz-proposed ppa only happen for Nvidia cards. For Intel and AMD it's working great. If someone doesn't have an Nvidia GPU there's no problem in using it.



I have that on 2 laptops one running Nvidia Intel and one Amd and ATI, NO difference they do the same "flicker" when you change desktop....
Cheers

---

