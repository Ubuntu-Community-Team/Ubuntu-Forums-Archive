---
title: "firefox terminal start error messages"
date: 2023-11-02
forum: New to Ubuntu
---

### Post by mikesebastianparucha on 2023-11-02
[B]firefox terminal start error messages

[/B]dear interested reader,

when i open the terminal with ctrl+alt+t, and enter "firefox", then there are messages i ***cannot understand***.

can somebody *translate* the cryptic meaning of these messages given in the attachment please to me, and tell me what options there are to *solve* this issue whenever it is solvable?

sincerely
the author

---

### Post by #&amp;thj^% on 2023-11-02
Those are just warnings, but will firefox start from the terminal for you?

---

### Post by ActionParsnip on 2023-11-02
This should help some
```

sudo apt install libcanberra-gtk-module libcanberra-gtk3-module -y

```

Source:
[https://www.tecmint.com/failed-to-load-module-canberra-gtk-module/](https://www.tecmint.com/failed-to-load-module-canberra-gtk-module/)

---

### Post by ActionParsnip on 2023-11-02
Possibly this for the atk stuff
[https://stackoverflow.com/questions/75406844/not-loading-module-atk-bridge-the-functionality-is-provided-by-gtk-natively](https://stackoverflow.com/questions/75406844/not-loading-module-atk-bridge-the-functionality-is-provided-by-gtk-natively)

I don't use Firefox so cannot verify what is posted here but the replies look positive

---

### Post by Holger_Gehrke on 2023-11-02
Shouldn't somebody explain to mikesebastianparucha what atk and libcanberra are ? 

'atk' is a toolkit for accessibility. This used to be a library of its own and you needed to include a separate 'bridge' module to talk to it. It became a part of GTK some time ago and since then the bridge isn't necessary anymore. It's not yet an error to use it, but some day soon the bridge will not be there. So the message is directed at the developers to tell them to fix their atk initialization.

'libcanberra' is a library that allows program that use it to play sounds when certain events happen. It supports system wide sound themes, so all programs will produce the same sound for the same kind of event. E.g. an error will make the same sound in all programs, a request for confirmation will make a different sound then the error-sound, but - again - it will be the same sound across programs that use libcanberra. Using sounds for events used to be the new hotness back 20 years ago. For some reason the firefox snap comes with GTK 2.0 modules which can't work. I don't know whether that's the developers fault or the packagers ...

As already mentioned, these are just warnings not errors. Firefox should work just fine even if you don't do anything about them. They are directed more at developers than at users. They basically say: "You're doing things in a way that's not quite the current way of doing them.

Holger

---

### Post by #&amp;thj^% on 2023-11-02
> **Holger_Gehrke said:**
> Shouldn't somebody explain to mikesebastianparucha what atk and libcanberra are ? 
Holger
You just did that. :P

---

### Post by MAFoElffen on 2023-11-03
+1 -- Usually GUI applications are started from the GUI menu. 

Lot's of GUI applications display 'warnings' in the Terminal session when started directly from the commandline, that have no bearing on how it is running. As long as those things run okay, I tend to just ignore those.

---

### Post by mikesebastianparucha on 2023-11-04
dear all who answered,

thank you very much for your answers, to begin with... Yes, firefox (ff) started, however... earlier in these days, it had not opened by clicking onto the ff symbol, and i was wondering, why this happened, and this is how i started to use the terminal for checking what it does.

i used the steps given in your answers, especially given in the unique resource locators (url) added in some of the answers, but now, ff opens a **full black window**, so i use chromium to have a browser i am able to write to you.

also, i want to particularly point out Holger's answer and attempt to give an explanation to enhance my understanding in these features. -
the given url enhanced it likewise. 
thank you very much for that.

now, i am going to update the current problem. perhaps you or any other interested person are able to help me further. :-k :-s

unfortunately, i do not see any option to upload screenshots, hence i stop here leaving the url of the continued forum thread: [https://ubuntuforums.org/showthread.php?t=2492225&p=14164043#post14164043](https://ubuntuforums.org/showthread.php?t=2492225&p=14164043#post14164043)
sincerely,
mikesebastianparucha

---

### Post by mikesebastianparucha on 2023-11-04
dear interested reader,

in continuation of the problem given in [https://ubuntuforums.org/showthread.php?t=2492186](https://ubuntuforums.org/showthread.php?t=2492186)

i upload screenshots of the current state of the problem.
the solutions given in the url above led to this state unfortunately, however nonetheless i am optimistic to find a way to let these warnings from the terminal when writing "firefox" to open the firefox (FF) web browser vanish.

thank you in advance.

sincerely,
mike

---

### Post by coffeecat on 2023-11-04
@mikesebastianparucha, your latest post was simply a continuation of your original thread. I have merged it with the original thread. Please do not open duplicate threads about the same problem. This causes confusion.

---

### Post by MAFoElffen on 2023-11-05
That is what it looks like if you start it from the terminal & from the Icon?

What happen if you start if from the terminal lie this
```

firefox -safe-mode

```
If it does start, then diagnose your profile, extensions or themes, hardware acceleration. If not, then do
```

sudo snap switch --channel=beta firefox
sudo snap switch --channel=stable firefox

```
That will refresh the code of itl it...

---

### Post by mikesebastianparucha on 2023-11-05
dear coffeecat and others,

thank you very much for doing what i originally wanted to do but could not.

unfortunately, i could not add new attachments to the original thread. this is why i opened a new thread with the updated problem.

in the meantime, ff opens without giving a black screen, so normally, whence the warning messages still appear when ff is opened via terminal.

sincerly

---

### Post by mikesebastianparucha on 2023-11-05
dear MAFoElffen,

thank you very much for your answer.
however, i do not really know what you mean with the words "diagnose your profile, extensions or themes, hardware acceleration". What kind of profile shall I diagnose, and how?
Do you mean the extensions and themes within the web browser?
Where do I find information about the hardware acceleration?

Sincerely

---

### Post by Holger_Gehrke on 2023-11-05
A profile in Firefox is the totality of all settings, themes, extensions, bookmarks, browser history, and probably a few more things. You can have multiple profiles. To create (additional) profiles, switch between profiles, or set the default profile you can start Firefox from the command line with the option '-ProfileManager'. I use this to separate work-related and recreational browsing (different bookmarks, different extensions, different theme). For a classical .deb based installation of Firefox the profiles are stored in subdirectories of ~/.mozilla/firefox. For a snap based install they are stored in ~/snap/mozilla/firefox.

Hardware acceleration can be toggled on and off from the general settings page in Firefox, somewhere in the last third of that page.

Holger

---

### Post by mikesebastianparucha on 2023-11-05
Dear Holger,

Thank You for Your efforts. I guess that there is no direct solution to the described problem.
I have no profile installed on my Firefox Web Browser. This part of the discussion actually totally confuses me.

Sincerely

---

### Post by MAFoElffen on 2023-11-05
Well actually, "there are" many solutions for your problem. 

Though... I have not heard from you whether you have tried anything to resolve them. 

For example:  Did you open a terminal session and do this:
```

firefox -safe-mode

```
Did that start any differently? If it did not, then remove firefox, and reinstall it
```

sudo systemctl stop var-snap-firefox-common-host\\x2dhunspell.mount
sudo systemctl disable var-snap-firefox-common-host\\x2dhunspell.mount 
sudo snap remove firefox
sudo snap install firefox

```
If it did start up okay, then it may be a profile problem. To quickly replace your profile, do as Holger explained
```

firefox -profilemanager

```
When the ForeFox Profile Manager dialog comes up, select "Create Profile" > Next > Give it a name > Next.... When it appears in the list box, select it, then check the box that says to use it on startup...

Go back to the command line and type
```

firefox

```
See it it comes up...

You have choices. If you are not willing to "try", then that is on you. In that case, then you are not part of your own solution... We cannot help you with that.

---

### Post by mikesebastianparucha on 2023-11-06
Dear MAFoElffen,

This is helpful. Thank You. I was assuming that my answers imply that I am doing the steps given by the community as indirectly can be seen in the update of the problem: I did the steps given before that and ended up with the problem given in the update.

Back then I did the "firefox -safe-mode" command and the refreshing of the code skipping the profile diagnostics since I did not know what is meant by that.

As soon as my Ubuntu system is going to work again, I will do the steps given by You in the last post.

Sincerely

---

### Post by mikesebastianparucha on 2023-11-07
> **MAFoElffen said:**
> For example:  Did you open a terminal session and do this:
```

firefox -safe-mode

```
Did that start any differently? If it did not, then remove firefox, and reinstall it
```

sudo systemctl stop var-snap-firefox-common-host\\x2dhunspell.mount
sudo systemctl disable var-snap-firefox-common-host\\x2dhunspell.mount 
sudo snap remove firefox
sudo snap install firefox

```
If it did start up okay, then it may be a profile problem. To quickly replace your profile, do as Holger explained
```

firefox -profilemanager

```
When the ForeFox Profile Manager dialog comes up, select "Create Profile" > Next > Give it a name > Next.... When it appears in the list box, select it, then check the box that says to use it on startup...

Go back to the command line and type
```

firefox

```
See it it comes up...

I did all those steps, and the terminal output now is:

> ~$ firefox
Gtk-Message: 07:23:17.630: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

(firefox:4569): Gtk-WARNING **: 07:23:17.811: GTK+ module /snap/firefox/3290/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 07:23:17.811: Failed to load module "canberra-gtk-module"

(firefox:4569): Gtk-WARNING **: 07:23:17.814: GTK+ module /snap/firefox/3290/gnome-platform/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so cannot be loaded.
GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported.
Gtk-Message: 07:23:17.814: Failed to load module "canberra-gtk-module"

where I am not able to continue using this terminal window since there is no "~$".

---

### Post by mikesebastianparucha on 2023-11-07
Furthermore, there are new Gtk-Messages that can be seen in the uploaded screenshot: "Gtk-CRITICAL", where this is the terminal window where I could not enter any terminal commands since the "~$" was missing.

---

### Post by MAFoElffen on 2023-11-07
Missing because FireFox should have been running... Did FireFox start in another Window?

All those commands involving Firefox should have spawned other Windows.

---

