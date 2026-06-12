---
title: "Removing WINE/Configure WINE/Uninstall Wine Software"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by joelbitar1986 on 2013-12-29
Hello,  Supernoob here.  I believe I successfully uninstalled wine, which was giving me many problems. However, I have been left with residual files/apps that are cluttering my computer. In particular 'Configure Wine' and 'Uninstall Wine Software'. Why are these things still present if I've already uninstalled wine?  P.S. I've included attachment of what I'm talking about.

---

### Post by r3dd on 2013-12-29
When you uninstall a program try using
```
sudo apt-get autoremove --purge <package>
```
That will get rid of any unused dependencies and rid the computer of all of the files associated with it. There will still be some stragglers to remove on your own.

Also, VERY IMPORTANT, the autoremove and purge options can be dangerous, so pay attention to what is being removed to make sure you don't break your system.

---

### Post by deadflowr on 2013-12-29
It looks like legacy behavior.
When you click on the app(try the configure wine one) does anything actually open?

If not, then go to system settings > privacy and look for delete history.

---

### Post by monkeybrain20122 on 2013-12-30
Did you reboot/logout? 

If they are still there after reboot Go to /usr/share/applications to find the .desktop files and delete them.
```
cd /usr/share/applications
ls
```

If you see a whole bunch of wine stuffs like wine-winecfg.desktop, just delete them. e.g
```
sudo rm wine-winecfg.desktop
```

(I was tempted to do "sudo rm wine*", but on second thought you may have other desktop files starting with the letters wine that has nothing to do with wine)

Also there may be something in .local/share/applications in your home. It is hidden (ctrl + h to show them in file browser), inside there is a wine folder, delete that too.

---

### Post by whitesmith on 2013-12-30
> **joelbitar1986 said:**
> Hello,  Supernoob here.  I believe I successfully uninstalled wine, which was giving me many problems.Two suggestions and a solution:

(a) In the future, always be specific about the headaches you are experiencing. "Giving me many problems" just says "stay away" to someone who may have heard of Wine and wants to experiment. Also, some knowledgeable user might have helped you avoid the extreme measure of removing the program--provided they knew the precise issues you were having.

(b) If you installed Wine through the Software Center, you should have removed it the same way to avoid perpetuating grief. The same holds for Synaptic.

Of course, this is education, not help. I think your problem is best solved with```
sudo apt-get --purge remove Wine #Got an error? Maybe that W should be in lower case. I don't remember.

```Also see #alan.e.redding's answer. Best of luck to you!

---

### Post by joelbitar1986 on 2013-12-30
Thank you,  This worked for me very well. Marking as solved.

---

