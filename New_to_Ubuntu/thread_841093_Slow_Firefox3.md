---
title: "Slow Firefox3"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by philk949 on 2008-06-26
Hi,
I recently did a fresh install of Ubuntu Hardy 8.04 and found everything zipped along just fine, despite my humble 512MB RAM. Firefox3 beta5 was my default browser with Hardy and it was quick, but after I installed the available updates and lost 3beta5, everything slowed to a crawl. I get hang time, freezes and general dial-up type pain. So I have these questions:

1. Is this common with the updated FF3?
2. Is there a Windows-like way of deleting Temp files and folders and can the file system be defragmented?
3. Can I uninstall FF3 and re-install FF3 beta5 without doing a complete re-install of Hardy?

Thanks in advance
philk949

---

### Post by Sinkingships7 on 2008-06-26
> **philk949 said:**
> Hi,
I recently did a fresh install of Ubuntu Hardy 8.04 and found everything zipped along just fine, despite my humble 512MB RAM. Firefox3 beta5 was my default browser with Hardy and it was quick, but after I installed the available updates and lost 3beta5, everything slowed to a crawl. I get hang time, freezes and general dial-up type pain. So I have these questions:

1. Is this common with the updated FF3?
2. Is there a Windows-like way of deleting Temp files and folders and can the file system be defragmented?
3. Can I uninstall FF3 and re-install FF3 beta5 without doing a complete re-install of Hardy?

Thanks in advance
philk949

Because you say this is a fresh install, I'm assuming you have no other Mozilla products installed.

Go to Places->Home and press ctrl+h. This will show you your hidden files and folders. Most of the folders you now see are configuration folders. It is my guess that something with your configuration in beta5 isn't agreeing with the final release. Navigate to the .mozilla directory and click it once to highlight it. Press F2 and rename it to .mozilla-backup. Then start up Firefox (it will look brand new) and see if the speed problem is fixed. If not, go back to your file browser, as before, and delete the new .mozilla folder, and rename the other one back to .mozilla. That will undo any changes.

Let's see if that works. Post back.

---

### Post by pixel :-) on 2008-06-26
my humble 512MB RAM.
Do you have swap?

1. Is this common with the updated FF3?
Ok with me,1.5G

2. Is there a Windows-like way of deleting Temp files and folders and can the file system be defragmented?
ext3 doesn't need defragmantation.It could be a addon that misbahaves,flash mplayer...it could be a broken .mozilla,rename it and see what happens,revert by simply renaming it.Try as a new user.

3. Can I uninstall FF3 and re-install FF3 beta5 without doing a complete re-install of Hardy?
Go in synaptic,select firefox3 then "Pakages-->Force vercion"

---

### Post by billgoldberg on 2008-06-26
When you updated you got some new kernels also.

Those **could** be the culprite.

When the grub loads when you start up your pc, press esc to enter it and pick an older kernel.

Other than that, if your only problem is with firefox 3, completly remove it.

```
sudo apt-get autoremove firefox --purge
```

and then reinstall it.

Or use another browser, like the default gnome browser "epiphany".

```
sudo apt-get install epiphany epiphany-plugins
```

or the new Opera 9.5

---

### Post by philk949 on 2008-06-26
Thank you to all who responded.
Aquavitae, I took your advice re the renaming of the .mozilla file and took it for a run, but no great difference, so went back to the original. I have disabled Noscripts and Adblock and things are not as glacially slow as before.
With regard to the screen res problem, i.e. having to reconfigure x-server at restart, that one remains as yet un-addressed. Sometimes, one feels inclined to actually USE the computer rather than be constantly tweaking it, with its attendant potential for disaster, especially at the hands of an overly inquisitive newbie.
Talk soon
philk

---

