---
title: "Trouble with loading Adobe flash"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by Michael_Dukeminier on 2014-03-30
I have an older computer that had XP on it and it crashed. Since this is gonna be for my kids I thought I'd try Linux OS.  I have never used this OS or even seen it.

Issue 1) 
I went to You-tube and tried to watch a video and it said I needed Flash Player and had a link to get it.  At the link it ID'ed my OS but told me to choose a Linux platform ( YUM and others) I had no idea which to choose.  I chose YUM for the heck of it and it did something but not what I expected and I still cannot see the video on You-tube. 

Issue 2)
I can't get on my wireless network and I am used to the computer telling me what WL networks it sees and then choosing mine...

I'm beginning to think I have made a mistake, that Linux is for the super computer savvy and that I should just buy MS 7.
Feeling frustrated and really stupid,,,,

Here is my system:

---

### Post by carl4926 on 2014-03-30
```
sudo apt-get install ubuntu-restricted-extras
```

post the result of
```
lspci -nnk
```

---

### Post by Impavidus on 2014-03-30
Just some clarification: carl4926's first terminal command will install flash, along with some other software with restrictive licences, like fonts and multimedia codecs. It will install some Windows fonts, for which you'll have to accept the licence. Hit tab to select the correct button, enter to proceed. It will also ask for your password, which you'll have to enter (type and hit the return key) without recieving any feedback, not even ****. Alternatively, if you only want the flash player, you can use```
sudo apt-get install flashplugin-installer
```There is also the software centre, where you have a graphical interface to install either of these packages (flashplugin-installer or ubuntu-restricted-extras).

I wouldn't say that Linux, or in any case Ubuntu, is for the super computer savvy people. Still, you sometimes have to get under the bonnet of your vehicle to fix it. Most of us see that as something good, as it allows us to tune or fix things without sending it to the garage (id est, the computer repair shop).

---

### Post by mörgæs on 2014-03-30
13.04 is out of support. Best is to begin with a fresh install of 13.10.
After that the two commands posted above should do the trick (or just install Chrome, in which Flash is installed by default).

---

### Post by Chessgeek2900 on 2014-03-30
Greetings.

My first (and currently only) thread is (in some ways) related to this issue: my computer kept crashing on Youtube.  It turned out it was overheating, in part due to the way Adobe Flash uses system resources.  Someone recommended trying Viewtube.  Viewtube requires getting Greasemonkey first (I believe both are available through the Ubuntu Software Center,) and it does not have that nice ability to go from one full-screen video to the next without going out of full-screen, but my computer has not crashed once since I switched over.  I think Viewtube and Greasemonkey are browser-specific add-ons (as in, they need a Mozilla base,) but I may be mistaken.

And no, Linux is not only for the computer programmers--otherwise I would have given up on it before I even had it downloaded!  There are some things that are annoyingly difficult to find, though (mainly because of my inexperience with Linux.)

Don't give up! (says the guy with only his king left against king, queen, bishop, and two rooks...)


Chessgeek2900

---

### Post by monkeybrain20122 on 2014-03-30
> **Chessgeek2900 said:**
> Greetings.
Viewtube requires getting Greasemonkey first (I believe both are available through the Ubuntu Software Center,) and it does not have that nice ability to go from one full-screen video to the next without going out of full-screen, but my computer has not crashed once since I switched over.  I think Viewtube and Greasemonkey are browser-specific add-ons (as in, they need a Mozilla base,) but I may be mistaken.


They are not in the software centre. Greasemonkey is a Firefox addon and Viewtube is from [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
 After installing GM in Firefox (go to Tools > Add-ons > get Add-ons and search for greasemonkey then install) , restart FF, go to Viewtube's website and click download it will install. To use it you can either use totem as the backend or gecko-mediaplayer (this needs to be installed from software centre), personally I prefer gecko-mediaplayer.

It also works in chrome, instead of greasemonkey there is a script manager called tampermonkey. But google will ban all Mozilla (NAAPI) pluggins in April so it will stop working soon.

---

