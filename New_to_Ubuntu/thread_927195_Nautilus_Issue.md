---
title: "Nautilus Issue"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Unanimated on 2008-09-22
There is a problem with Nautilus on my machine. Running "gksu nautilus" in the terminal doesn't do anything, and "sudo nautilus" returns nothing, but "gksudo nautilus" returns Segmentation fault. I really like Nautilus, but I use root on my file browser a lot, so I've had to resort to Thunar. I don't really like Thunar. Any help would be greatly appreciated.

---

### Post by tuxxy on 2008-09-22
Whats the error you are receving in the terminal after running gksu nautilus

---

### Post by Unanimated on 2008-09-22
There isn't one. The only thing that comes up is this:

```
Initializing nautilus-share extension

```

---

### Post by Unanimated on 2008-09-25
bump

---

### Post by NewDisciple on 2008-09-25
Do you have the script for that installed.  There are numerous root privilege nautilus scripts available.  I use them frequently and find them a little more convenient for doing numerous small tasks.

---

### Post by NullHead on 2008-09-25
Try changing your user to root then running nautilus. ```
sudo -i
nautilus
```

---

### Post by Unanimated on 2008-09-26
Wait, I just updated Nautilus and I'm actually getting an error message:
```
Initializing nautilus-share extension

(nautilus:10962): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10962): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:10962): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10962): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
```

---

### Post by Unanimated on 2008-09-28
bump

---

### Post by Unanimated on 2008-09-29
bump...........

Am I just going to have to reinstall Nautilus?

Or where do I get the sudo script and how do I install it?

---

### Post by Unanimated on 2008-09-29
I installed the sudo script, and.... it doesn't work.

---

### Post by gandaran on 2008-09-30
usually you can fix these problems by just deleting the configuration files in you home folder
go to the hidden home .gconf/apps and delete the nautilus folder, now run gksu nautilus, should work
by deleting the nautilus folder, you are going to loose all your own nautilus settings, nautilus will now start with default settings

---

### Post by Unanimated on 2008-09-30
Nope, that didn't work. I got the same error as before.

---

### Post by EnGorDiaz on 2008-09-30
here you go a full script for your nautilus


```
#!/bin/bash

if [[ -x /usr/bin/gksu || -x /opt/gnome/bin/gksu ]]; then
	sudotool=gksu
elif [[ -x /usr/bin/gnomesu || -x /opt/gnome/bin/gnomesu ]]; then
	sudotool=gnomesu
fi

$sudotool "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
```\

save it as a .sh file

---

### Post by Unanimated on 2008-09-30
Nope, that didn't work.

---

### Post by NewDisciple on 2008-09-30
When you say that it didn't work could you elaborate a little bit.  How did you install the script?  How did you try to use it?  Without knowing exactly what you are doing it's hard to pinpoint the problem.  If there is something wrong with your nautilus why not reinstall?  Takes less than a minute in the repository.

---

### Post by Unanimated on 2008-10-01
What I did was copy his script, put it into a text file, saved the next file to ~/.gnome2/nautilus-scripts, then CD'd to that directory and ran chmod +x root-nautilus-here (what I saved it as). Then I opened my home folder and tried to run the script, and nothing happened except it asked for my password.

---

### Post by NewDisciple on 2008-10-02
Perplexing to say the least.  Just for the heck of it go into your home folder (hidden files)>.gnome2 >nautilus >nautilus scripts >your script.  Right click & choose properties.  Check permission status, also check the executable tag box.

---

### Post by Unanimated on 2008-10-04
Yeah, it's all checked. I'll just reinstall it through Synaptic.

---

### Post by Unanimated on 2008-10-04
I reinstalled Nautilus and got the same error. I also installed the nautilus-gksu package, and that didn't solve anything, either.

---

### Post by Unanimated on 2008-10-11
bump

---

### Post by NullHead on 2008-10-11
Have you tried doing ```
sudo -i
```*then* running nautilus?

---

### Post by Unanimated on 2008-10-11
Yes.

---

### Post by NullHead on 2008-10-12
uh ... well .. I duno what to tell you, but thunar works :P

---

### Post by cyberfin on 2008-10-26
I'm seconding this problem. Exactly the same errors. Exactly the same futile attempts to fix.

Can someone pull me out of my perplexed state and tell me what's wrong here?

:confused::confused::confused::confused:

---

### Post by Unanimated on 2008-10-26
> **cyberfin said:**
> I'm seconding this problem. Exactly the same errors. Exactly the same futile attempts to fix.

Can someone pull me out of my perplexed state and tell me what's wrong here?

:confused::confused::confused::confused:
I wish I could fix it, but Intrepid is coming out in five days with Nautilus and X.Org updates, so what I would do is just use Thunar until Intrepid comes out.

---

### Post by cyberfin on 2008-10-26
> just use Thunar until Intrepid comes out.

I'm reluctant to just ram through the problem and not look back at something that is integrated it to a LTS OS... although I will probably upgrade to Intrepid anyway.

My problem at the moment is that I can't risk upgrading until I've finished a project I'm working on.

---

### Post by Scooby Doo on 2008-10-27
I take it that there was no solution for this.

I'm getting the same problem with gedit when I try to save a new file. Editing existing files doesn't appear to be a problem, just new ones.

```
(gedit:6908): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(gedit:6908): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
```When I try to **Save as...** gedit closes and the above error appears in the Terminal.

---

### Post by cyberfin on 2008-10-28
Indeed, it has not been solved and I would have thought that this is quite a real issue. I know I can do everything through the terminal (hail the terminal!) but when I have to move stuff (and we're not talking 2 files) I get kind of hacked off with term and want to do it GUI style. Anyway, just in case some geeky geek that is feeling generous today and decides to bless us with his awesomeness and raw heavenly powers... I thought I would paste my error msg:

```
gksudo nautilus
Initializing nautilus-share extension

(nautilus:9385): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:9385): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:9385): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:9385): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
```

I AM... thou humblest servant, milords.

Good day.

---

### Post by Scooby Doo on 2008-10-28
Well, I seem to have fixed it. Don't ask me how or why though.

This is what happened. I'd shutdown and restarted quite a few times and I was still getting the errors. At this time I had a CD in the drive that had an image of the Puppy linux .iso on. I ejected this CD and restarted. I'd done no other changes since the last restart and this time my system was back to normal. No more errors.  :confused:

I have absolutely no idea why this worked for me but I'm glad it did.

---

### Post by Buzzbait on 2008-10-28
I had the same error when running gksu nautilus. It turned out that I had a blank DVD in my DVD drive. The minute I ejected the blank DVD, gksu nautilus ran fine.

Strange days.

---

### Post by cyberfin on 2008-10-28
After reading your posts I thought that it just couldn't be that simple. I looked at my DVD drive. I pushed the button and... behold! A blank CD!

Un-effin-believable.

Go figure. Thanks guys.

---

### Post by lakitu on 2008-11-06
i 3rd this problem, & the fix. =/ thanks for the help
maybe someone should launchpad.net this.

---

### Post by getglenn on 2008-11-26
i too can confirm this...

after ejecting the blank cd "gksudo nautilus" works again!

i didnt have to reboot, restart or ANYTHING else, other than eject the blank cd!@#$%?

something is terribly wrong!

---

### Post by Jack005 on 2009-01-19
I confirm too...

I ejected the blank cd and then everything ("gksudo nautilus") was back to normal. I put back the blank CD in the drive and poof - "gksudo nautilus" does not work!!

---

### Post by Viperlin on 2009-02-04
same here, got nautilus running separately in openbox too so most of gnome is disabled.


guessing its a bug in the nautilus-cd-burner package then

or some other cd-drive extension to nautilus, very strange bug indeed heh

---

### Post by Francewhoa on 2009-07-31
I can confirm this bug too. I ejected a DVD. Run the same following command. And it worked. 
```
gksudo nautilus
```

---

