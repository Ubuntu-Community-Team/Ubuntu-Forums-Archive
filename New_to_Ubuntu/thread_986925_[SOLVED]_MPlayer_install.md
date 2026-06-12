---
title: "[SOLVED] MPlayer install"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by mesmith on 2008-11-19
Another newbie question.

I wanted to listen to some BBC radio stuff and Firefox announced that I needed a plugin and gave me three choices.  I chose MPlayer which appears to work (no speakers til tomorrow, but I do get what appears to be streming data with no warnings about Real Player not being installed), so I'm assuming all is fine.  Now, when I look at the Multimedia menu it offers a Movie Player, which after choosing gives me Totem Movie Player.  I like it.  Just below that menu entry is MPlayer Movie Player, which appears to be a not so nifty dupe of the Totem Movie Player with detached controls.  I'd like to dump the Mplayer Movie entry but cannot find it listed in the add/remove program area under multimedia programs.  How can I get rid of it, and let me say that if I can't (though I doubt that, as xubuntu seems to be infinitely modifiable) it's no big deal.

Many thanks,

Mike

---

### Post by Zack McCool on 2008-11-19
Mplayer is the far more usable and configurable of the 2.  And from your post, it appears that firefox is using the mplayer plugin to play your media, so I wouldn't get rid of it.

I always use either mplayer or vlc.  I have never liked totem in the least.  You may wish to try vlc instead of totem...

---

### Post by mesmith on 2008-11-19
Okay, I appreciate that information, but how is it configurable?  It appears after launching to be nothing more than a playback window with some detached controls.  Where does configuration come into the picture?  I can't see any options or buttons for configuration.  Also, why doesn't it appear under the add/remove software listings?  And assuming you are correct, and I do, how do I get rid of the Totem Movie player?

Mike

---

### Post by sloggerkhan on 2008-11-19
open up synaptic package manager and search for mplayer. Then hit mark to removal and apply.

The official mplayer gui is really lame, I recomend trying smplayer as the front end if you don't mind a few kde/qt libs.

That said if DVD menus and Subtitle rendering aren't important to you, VLC might be the way to go.

If DVD menus are a big deal, best support is xine.

Overall I can't really recomend totem and the gstreamer framework as being the optimal playback solutions.

---

### Post by mesmith on 2008-11-19
Thank you for your help.  I think I may be overcomplicating things.  I will rarely, if ever, play a movie.  I installed MPlayer only to get a plugin for Real Player audio streams from the beeb.  I have over the course of time developed a strong dislike for all things from Real and wanted to avoid loading Real Player.  Mplayer seems to work for my needs.  I don't know to how get to its configuration options (and maybe don't care too much at this point), but thought I'd like to not have two Movie player options.  So, maybe I need how to get rid of the Totem movie player.  Or, perhaps, I should be a little less compulsive and just let the two happily coexist.

Mike

---

### Post by Zack McCool on 2008-11-19
You are overthinking things...   ;)

To configure mplayer, open it, then right-click on it and select preferences.

Also, not everything is in "Add/Remove".  It is just an over-simplified front-end for apt, and doesn't have everything.  Open the Synaptic package manager.  That will give you access to all of your packages.

There is no need to uninstall either.  The disk space used isn't that much, and totem is part of the base install, though it isn't that good, IMO.  You manually installed mplayer for a specific reason.  If you no longer need it, you can remove it, but that's completely up to you.

---

### Post by mesmith on 2008-11-19
Thanks.  You answered all my questions and now I can configure MPlayer.  Since I'm new, I took a look at the Synaptic pkg.  Looks like I can do a search for Totem, for example, then mark the modules as remove completely and Apply.  That seems pretty straightforward.

Been with Windows since day one, but I wouldn't go back now.  Linux is still a bit quirky (through Windows glasses), but the speed and versatility of this system is just great.

---

### Post by mesmith on 2008-11-19
One other quick question: if I do uninstall Totem, which is part of the base install, does it complicate anything like the auto updates?  Or would the system realize that Totem didn't exist and not offer updates?

Thanks.

---

### Post by o.besner on 2008-11-19
It's not gonna freak out, if you don't remove anything else than Totem. I know there is one package that if you remove it brasero will be removed too. Just avoid that one and delete the rest.

You might wanna try, if you're sticking with Mplayer, the package gnome-mplayer. It's a nice skin. To make it look better in firefox you can also try gecko mediaplayer. It's basically the integration of gnome-mplayer in firefox.

to remove ugly/unwanted shortcuts you don't want in the menu (which was your first question) just right-click on the "applications" button.

---

### Post by Scunnered on 2008-11-19
mesmith

You don't say where you are attempting to listen to the BBC from. I found that in the UK I could get the BBC iPlayer to view all videos but not let me listen to live Radio. 

By using totem, mplayer not only could I listen to the national programmes but I was able to listen to radio Scotland without the dreaded Realplayer.

Hope this is of assistance

---

### Post by mesmith on 2008-11-19
Thanks to all of you for your help and guidance.

How would I determine which Totem pkg is required by Brasero?  I did a search in Synaptic for Totem and read all the pkg descriptions but didn't see Brasero mentioned.

Thanks again.

---

### Post by Zack McCool on 2008-11-22
What would Brasero need a totem package for?  What are you trying to do?

---

### Post by mesmith on 2008-11-23
There's a library in Totem that Brasero uses.  Don't know what it's for.  When I attempted to delete Totem using Synaptic it warned me.  Then again, I'm a newbie so it could have been some sort of fear halucination.

Mike

---

### Post by Nepherte on 2008-11-23
You will always get a warning when you attempt to remove something (in this case a totem library) that another application (in this case brasero) depends on. Just pay attention when you use synaptic (install/remove something). The package in this case is libtotem-plparser12.

---

