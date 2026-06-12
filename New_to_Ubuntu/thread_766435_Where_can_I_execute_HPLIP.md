---
title: "Where can I execute HPLIP?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by tropdoug on 2008-04-25
Hope I am using the right place to ask this. When you initially install gutsy, and then update all the repositories, it tells me that I am downloading 218 new or updated packages, and then installs them, so thats really cool. But I have a wireless HP all in one printer that requires hplip to be running to see and use. 

So I went to synaptic and searched for the package only to find that apparently it is already installed, but there are no menu entires for it, nor is there the expected hplip toolbox, that exists on my desktop setup under gutsy, so if it is installed where is it, and how do I actually register the printer with it, and get it all working?

If I am in the wrong area, please let me know. 

Thanks in advance.

---

### Post by PmDematagoda on 2008-04-25
Open Main Menu in System>Preferences>Main Menu, then go to the System>Preferences category and then select HPLIP Toolbox, you can then run HPLIP using the HPLIP Toolbox in System>Preferences>HPLIP Toolbox.

I realise that I used a lot of "System>Preferences" here:).

---

### Post by tropdoug on 2008-04-26
Thanks [I]PmDematagoda

Problem, HPLIP toolbox does not exist to be able to add it. 

[/I]When I do a *file find *I can see heaps* of hplip* files in lots of directories, so if the system has installed the correct files, does it just require setting up first in order for hplip toolbox to appear? I cannot remember what I did on my desktop but I am sure that my main confusion is understanding how Linux installs files on initial setup, and then how and where the various files ares stored. I must say, that at first look Linux appears a lot more complicated in this respect than c:\Program Files. But I am sure there is very good reasons for that. 

Further question, if I simply do a reinstall using synaptic, will that add a set of duplicate files to the system, or overwrite the existing ones?

Could it be that I have not yet been able to get this box to find the printer to start off with?

Thanks Doug

---

### Post by PmDematagoda on 2008-04-26
Did you see if you could start HPLIP by pressing Alt+F2 and entering:-
hplip

---

### Post by tropdoug on 2008-04-26
Just did that and no luck it cannot find the hplip file. So maybe it's not installed yet fully. 

But thanks to you, I just learned something else, I was wondering how you could get the equivalent of windows 'run' command. so I will file alt-f2 into my memory. LOL. 

I think I might try reinstalling it and see what happens. 

any other ideas please post, it all helps.

---

### Post by PmDematagoda on 2008-04-26
Can you just post the output of:-
```
sudo apt-get install hplip
```

---

### Post by FredB on 2008-04-26
If you want graphic user interface, you will have to install python-qt3 package too.

---

### Post by scorp123 on 2008-04-26
> **tropdoug said:**
>  So I went to synaptic and searched for the package only to find that apparently it is already installed, but there are no menu entires for it, nor is there the expected hplip toolbox  The shell command to launch the "HP Toolbox" is this one:
```
hp-toolbox
```

If you type this into a terminal it should fire up the HP ToolBox and let you configure your printer. And yes, I have the same here on Gutsy: per default you don't get an icon anywhere. Strange. So I made one myself: just create a new launcher and insert that command above (hp-toolbox) into the "Command" part, choose a nice icon, and voila, done.

---

### Post by tropdoug on 2008-04-26
You guys rock! 100% solved, and [COLOR=Blue]for others who may read this is what I did. 
[/COLOR]
I decided to do [COLOR=Blue]hp - toolbox[/COLOR] in a terminal first to see what happened and that confirmed that the installation could not take place because the package [COLOR=Blue]pyqt [/COLOR]was missing. So went to synaptic and then thought - hmmm what if hplip was installed but maybe not the gui so I searched for hplip, right clicked and looked at [COLOR=Blue]properties [COLOR=Black]finding that the gui was not in fact installed. So back to main page found [COLOR=Blue]hplip-gui [COLOR=Black](just a few entries below Doh!) and marked it for install, checked the dependencies and there was [COLOR=Blue]pyqt[/COLOR] so away I went and installed it. Result, [COLOR=Blue]HPLIP Toolbox[/COLOR] appeared under [COLOR=Blue]System>Preferences [/COLOR]and [COLOR=Blue]Fax address book and HPLIP Fax Utility [/COLOR]appeared under [COLOR=Blue]Applications>Office.

[COLOR=Black]IMPORTANT: before running the toolbox to install your printer, navigate to * [COLOR=Blue]/usr/share/ppd/hpijs/HP/HP-Fax-hplip.ppd.gz[/COLOR] *Open the [COLOR=Blue]gz [/COLOR]file and you have to re save it after a small edit. 

Scroll down the page until you find the entry [COLOR=Blue]Nickname [/COLOR]and remove the version number from the end of it, so that your new [COLOR=Blue]Nickname[/COLOR] will simply be HP -Fax then save the file as HP Fax.ppd  This is because during setup the fax requires this file in this format, and will not install correctly if you do not edit it. (I hope that makes sense, I am still learning how to pass on information) 

Having done the above, run HP Toolbox from the menu, a GUI comes up, and follow the prompts, in 2 minutes I had a working wireless HP all in one printer, fax, scanner. (PS you will have to browse to the location that you saved the edited ppd file to, when the fax setup looks for it, so remember where you saved it too)

Again thank you to all who helped. Much obliged indeed. :lolflag:

[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

