---
title: "No &quot;Custom&quot; option for Preferred Browser/E-mail"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by Birchle on 2011-10-03
I noticed this a while ago, but it's becoming increasingly annoying the longer I work around it.

In Ubuntu 11.04, the Preferred Applications window does not offer the option to select/specify a custom application for a web browser or e-mail client.  All the other tabs retain the custom option, but for some reason, it seems to have been removed for those two in the first tab.

Is there some way to re-add the custom option?  Why was it removed in the first place?

---

### Post by zeroseven0183 on 2011-10-03
There have been a few bug reports and forum threads about this issue. This bug thread suggests that is a bug regression and users suggest some workarounds [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/708382](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/708382)

---

### Post by Birchle on 2011-10-03
I hadn't seen that, thanks.

I'm not entirely clear on what the suggested workarounds do, though.  It looks like comments #4 and #24 are the ones I want, for browser and email respectively, but are they setting specific applications already?  Or are those two comments giving instructions on how to add the Custom option back into Preferred Apps?  Or does some other file have to be changed after I make those comments' changes, and those comments just allow the potential third change to "stick"?  If I have to edit another file as well, which one, and where, and to what, so I can have the latest Seamonkey and the latest Thunderbird as the defaults?

---

### Post by Krytarik on 2011-10-03
Well, those workaround stated in the thread of the bug report doesn't seem too great, actually. I would rather change some GConf keys instead, via "gconf-editor". And no, those changes won't add back the options for setting custom apps to the "Preferred Applications" GUI, and they won't be necessarily reflected by those either.

As I've set Firefox and Thunderbird as my preferred apps, I've searched in "gconf-editor" yesterday for every occurrence of "firefox" and "thunderbird"; these are the keys to change:

Browser:

[LIST]
[*]/desktop/gnome/applications/browser/exec
[*]/desktop/gnome/url-handlers/unknown/command
[*]/desktop/gnome/url-handlers/http/command
[*]/desktop/gnome/url-handlers/https/command
[*]/desktop/gnome/url-handlers/about/command
[/LIST]
Mail Client:

[LIST]
[*]/desktop/gnome/url-handlers/mailto/command
[/LIST]
Greetings.

---

### Post by Birchle on 2011-10-03
I tried changing the browser parts (let's only break one thing at a time!), but it doesn't seem to have accomplished anything.  However, I'm not sure if I did it right, either, and I'm also not entirely sure what the right questions are that I should be asking, so I'll just start with the ones I have.

 I'm assuming the value it's looking for is the same as the Command part of main menu item.  Right?  So typing in the path to the program executable (for manually installed programs) should work.  Synaptic-installed programs all seem to be "<program_name> %u".

Going through your list, I noticed that the value of /desktop/gnome/applications/browser/exec was "firefox" while all the rest were "firefox %u"  -- what's the difference?  How am I supposed to change the path of manually-installed Seamonkey to do the equivalent of dropping the %u?

After changing all the browser keys to use /path/to/seamonkey, I restarted everything, tried clicking a link in Thunderbird, and it opened...  still in Firefox.  The Pref App Gui also still says Firefox, but you said that's to be expected, so I'm less concerned about that.

Related, and perhaps I should have started with this...  Synaptic-installed older Thunderbird integrates into the panel indicator envelope.  If I manage to set manually-installed newer Thunderbird as the default mail application, will that allow it to integrate into the envelope? (I had originally been assuming this would be the case, but by now, I'm not so sure that's a safe assumption.)  Or are only synaptic-installed programs allowed to integrate like that?

---

### Post by Krytarik on 2011-10-03
> **Birchle said:**
> Going through your list, I noticed that the value of /desktop/gnome/applications/browser/exec was "firefox" while all the rest were "firefox %u"  -- what's the difference?  How am I supposed to change the path of manually-installed Seamonkey to do the equivalent of dropping the %u?
Well, I, too, don't know what's exactly the difference between both of those parameters, but both are taking the respective input URL/path/values and are passing them to the respective apps. In fact, I have "%s" in all those latter keys, not "%u", like you apparently have.

Whatever is there as the default in your case, appended to "firefox" or "thunderbird", respectively; just replace "firefox", respectively "thunderbird" with the name of your app's executable. I've tested that with "chromium-browser", just for the "http" key, and the fitting URLs were opened in Chromium. Whether it was from the About dialog of Gedit or a link in a mail in Thunderbird.

> **Birchle said:**
> If I manage to set manually-installed newer Thunderbird as the default mail application, will that allow it to integrate into the envelope?
Nope, not by default, that isn't affected by this at all. But you can try creating a .desktop file for your manually installed version and link those to the mail envelope. This guide should help you with that (you'll notice that you know those already :P ):

[http://www.tuxgarage.com/2011/06/replace-evolution-with-thunderbird.html](http://www.tuxgarage.com/2011/06/replace-evolution-with-thunderbird.html)

Good luck!

---

### Post by Birchle on 2011-10-03
> **Krytarik said:**
> (you'll notice that you know those already :P )
Ah, right, I forgot I changed that part separately!  Apparently new system information overload is kicking in.

It just dawned on me, though -- should I be changing these settings with sudo/gksu, or without?

Also, is there a way to force the changed settings to *stay* changed?  It seems like opening the Pref App GUI, even if I don't do anything in it, resets all the browser options back to Firefox again.  Admittedly, I'm not likely to go in there very often, so it shouldn't be a huge problem...  But I still foresee it being very annoying, when I go to change an application in the future, and forget how I set the browser differently.

---

### Post by Krytarik on 2011-10-03
> **Birchle said:**
> should I be changing these settings with sudo/gksu, or without?No, definitely not as root! Otherwise, you are changing the settings of root, not yours! If not changed as root, does it work now?

> **Birchle said:**
> Also, is there a way to force the changed settings to *stay* changed?  It seems like opening the Pref App GUI, even if I don't do anything in it, resets all the browser options back to Firefox again.
Yeah, that's unfortunate, indeed. Apparently, it's behaving differently in my system, since I still have those GUI options to set custom apps. So, if it's in fact behaving like that in your system, you can try setting the values of those GConf keys as 'mandatory'. Therefore, right-click on the respective key, and choose "Set as Mandatory". This should work.

---

### Post by Birchle on 2011-10-03
> **Krytarik said:**
> No, definitely not as root! Otherwise, you are changing the settings of root, not yours!
In the "interesting notes" department, root only has the first, third, and fourth keys, and first still only says "firefox"...  But the other two have the %s you mentioned having, rather than the %u I have in my personal settings.  I would not have expected that to be different, whatever it means.

> If not changed as root, does it work now?Yup.  In hindsight, it might've worked the first time, except that I checked whether Pref Apps really would still say Firefox after changing gconf, and didn't realize until after we each posted again that Pref Apps had reset it.

> Yeah, that's unfortunate, indeed. Apparently, it's behaving differently in my system, since I still have those GUI options to set custom apps. So, if it's in fact behaving like that in your system, you can try setting the values of those GConf keys as 'mandatory'. Therefore, right-click on the respective key, and choose "Set as Mandatory". This should work.Well, it asked for a password to set as mandatory, which I've never had happen unless I'm doing something as root, and once set, there doesn't seem to be any indication that it's now mandatory instead of whatever it was before.  ...And after opening Pref Apps just to test, it's all set back to Firefox again anyhow.  So I guess it doesn't work. :(

This lack of a custom option is a nuisance.  What was it about the bug comments that made those workarounds not very good?  Were they suggested as a way to also prevent this Pref App resetting problem, perhaps?

---

### Post by Krytarik on 2011-10-03
> **Birchle said:**
> Well, it asked for a password to set as mandatory, which I've never had happen unless I'm doing something as root, and once set, there doesn't seem to be any indication that it's now mandatory instead of whatever it was before.  ...And after opening Pref Apps just to test, it's all set back to Firefox again anyhow.  So I guess it doesn't work.Yeah, of course does that action ask for a password, as the change is system-wide. I assumed you would expect that. Too bad that this doesn't work, eventually. Seems like "Mandatory" never works as expected. Dumb!

> **Birchle said:**
> What was it about the bug comments that made those workarounds not very good?  Were they suggested as a way to also prevent this Pref App resetting problem, perhaps?Actually, now that we seem to have an issue with making those changes stick, you could give the workaround indicated in comment #4 a try. Its point is to create a custom .desktop file (which you would need anyway, at least for the integration into the mail envelope), so that you don't need to set a "Custom" app, thus staying in the borders of the current capabilities of "Preferred Applications", which also answers your second question.

But instead of locating the .desktop files in your home directory, you should add them to the system-wide "/usr/share/applications". Do that for both, the browser and the mail client; for the latter, use the default .desktop file of Thunderbird as the template, instead of following the method indicated in comment #24.

---

### Post by Birchle on 2011-10-03
> **Krytarik said:**
> Yeah, of course does that action ask for a password, as the change is system-wide. I assumed you would expect that. Too bad that this doesn't work, eventually. Seems like "Mandatory" never works as expected. Dumb!
I didn't realize it was system-wide, since I was only working with my gconf, not root's.  But, now that you've pointed that out, I went back and checked root's settings (which, to be clear, I never actually changed) -- and *those* keys now say "seamonkey" and "seamonkey %u" where I set them in my gconf, instead of the "firefox" and "firefox %s" they said previously.  So the mandatory did stick...  Just not where it is needed.  Should I set them back to firefox to keep the defaults?  How do I undo the mandatory part?

I'm going to hold off on trying the rest until I hear back about gconf, so I don't wind up overlapping attempts and getting faulty results, since I don't know what the chances are of these various methods conflicting.

---

### Post by Krytarik on 2011-10-03
Upon checking out how exactly to 'unset' the 'mandatory' keys, I figured some things:

[LIST]
[*]You can only set keys *successfully* as 'mandatory' if you run "gconf-editor" as root, thus with "gksudo" prepended - at least in my 10.04, but it seems to work in your 11.04, given what you noticed in your root's GConf (btw., [here]("http://www.psychocats.net/ubuntu/graphicalsudo") is something to consider when running graphical apps as root; the bottom line: always use "gksudo" for those - or at least in Ubuntu also "gksu", if you want to spare typing the two additional letters).
[*]Setting of 'mandatory' keys only takes effect after relogin. Then, the - still set - user specific value will be overridden, and the key isn't changeable anymore, also in "gconf-editor". In that time, you won't see the user specific value in "gconf-editor", nor can you change it easily - meaning without editing XML files.
[*]To 'unset' 'mandatory' keys, open "gconf-editor" as root, choose "File -> New Mandatory Window", browse down the path to the concerning key, right-click it, and choose "Unset Key". You'll notice, however, that the folders will remain, but that doesn't hurt, of course. After relogin, the user specifc setting, which was hidden before, is re-activated, and the key is changeable again in "gconf-editor".
[/LIST]
So, knowing that now, you could try that way again, or opt for the .desktop file method, which I think now is the better, since more transparent, and more universal method, not at least with view on the Thunderbird integration into the mail envelope - I'm guessing that you've already created custom launchers for both apps on your desktop, which is another use case of those .desktop files, as well as integration into the classic Gnome menu, the Unity Dash, and all that.

---

### Post by Birchle on 2011-10-05
> **Krytarik said:**
> You can only set keys *successfully* as 'mandatory' if you run "gconf-editor" as root, thus with "gksudo" prepended - at least in my 10.04, but it seems to work in your 11.04, given what you noticed in your root's GConf
Either run it as root, or give the password when it's requested, apparently.

> Setting of 'mandatory' keys only takes effect after relogin. Then, the - still set - user specific value will be overridden, and the key isn't changeable anymore, also in "gconf-editor". In that time, you won't see the user specific value in "gconf-editor", nor can you change it easily - meaning without editing XML files.I hadn't been relogging after changing the settings, since so little seems to require that.  I have by now, however, and it does in fact look like the root mandatory has overridden the original user gconf settings, and both root gconf and user gconf tell me "This key is not writable" now.  The keys are all still visible, however.  And they stay set, how I wanted, even after opening Pref Apps, despite that Pref Apps still show the wrong programs.  That log out/in bit makes a big difference!

> So, knowing that now, you could try that way again, or opt for the .desktop file method...Since this first method seems to work after all, I think I'll leave it as-is, and see how it goes.  If other problems turn up later, I'll give the .desktop method a try.  I'll certainly keep the unset instructions handy, though, in case I need them at some point!

Unless...  If I unset the root mandatory keys, will the user keys still remain mandatory?  So I could set root back to default (firefox %s), but keep my own settings (seamonkey %u)?  Or is it an all-or-nothing deal?

---

### Post by Krytarik on 2011-10-05
> **Birchle said:**
> If I unset the root mandatory keys, will the user keys still remain mandatory?  So I could set root back to default (firefox %s), but keep my own settings (seamonkey %u)?  Or is it an all-or-nothing deal?
Yep, the latter. :P Look, the "Mandatory" and "Default" settings are stored in two additional GConf profiles, and have nothing to do with either the root or the user profiles. So, as I said in my previous post, as soon as you set keys as 'mandatory' and you relogged in, so that the override of your user's settings takes effect, you are effectively seeing the values of the 'mandatory' keys in the respective user's or root's GConf, not their own ones anymore. Btw., the latter was affected immediately because root isn't actually 'logged in', as soon as you closed all windows run as root, and re-open them or open different ones, GConf is reloaded.

---

### Post by arty.net on 2011-12-11
i also suggest this on gnome 3...it works ! ! !

[http://library.gnome.org/users/evolution/3.1/default-browser.html.en](http://library.gnome.org/users/evolution/3.1/default-browser.html.en)

---

